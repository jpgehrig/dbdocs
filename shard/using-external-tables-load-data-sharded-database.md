## Using External Tables to Load Data into a Sharded Database

Using the examples and guidelines in the following topics, you can load data into a sharded database by creating external tables and then loading the data from the external tables into sharded or duplicated tables.

This data loading method is useful when the data to be loaded resides in external files, for example in CSV files.

External tables can be defined using the `ORGANIZATION EXTERNAL` keyword in the `CREATE TABLE` statement. This table must be local to each shard and not sharded or duplicated. Loading the data into the sharded or duplicated table involves a simple `INSERT … SELECT` statement from an external table, with a condition to filter only a subset of data for sharded tables.

You may choose to keep the files on different hosts based on the access time and size of the files. For example, copy the files for duplicated tables on the shard catalog host and keep files for sharded tables on a network share that is accessible to all of the shards. It is also possible to keep a copy of the sharded table files on each shard for faster loading.

For more information about external tables, see [External Tables](../sutil/oracle-external-tables.md) in Oracle Database Utilities.

### Loading Data into Duplicated Tables

Data for the duplicated tables resides on the shard catalog, so loading the data into the duplicated tables is also done on the shard catalog. The data is then automatically replicated to shards after loading is complete.

Consider the following table defined as a duplicated table.

    CREATE DUPLICATED TABLE StockItems (
     StockNo     NUMBER(4) PRIMARY KEY,
     Description VARCHAR2(20),
     Price       NUMBER(6,2)
    );

Loading data into the table StockItems involves the following steps.

1.  Create a directory object pointing to the directory containing the data file and grant access to the shard user on this directory.
        CREATE OR REPLACE DIRECTORY shard_dir AS '/path/to/datafile';
        GRANT ALL on DIRECTORY shard_dir TO uname;
2.  Create an external table that is local to the shard catalog, with the same columns as the duplicated table.
    On the shard catalog, run:

        ALTER SESSION DISABLE SHARD DDL;
        CREATE TABLE StockItems_Ext (
         StockNo     NUMBER(4) NOT NULL,
         Description VARCHAR2(20),
         Price       NUMBER(6,2)
        )
        ORGANIZATION EXTERNAL
        (TYPE ORACLE_LOADER DEFAULT DIRECTORY shard_dir
            ACCESS PARAMETERS
                (FIELDS TERMINATED BY ’|’ (
                  StockNo,
                  Description,
                  Price)
            )LOCATION (’StockItems.dat’)
         );

    In this example, the data file for the duplicated table is named `StockItems.dat` and column values are separated by the character ‘\|’.
3.  Insert data from the external table into the duplicated table.
        INSERT INTO StockItems  (SELECT * FROM StockItems_Ext);

    You can use also optimizer hints such as APPEND and PARALLEL (with degree of parallelism) for faster loading depending on your system resources. For example:

        ALTER SESSION ENABLE PARALLEL DML;
        INSERT /*+ APPEND PARALLEL */ INTO StockItems
          (SELECT * FROM StockItems_Ext);

    or

        ALTER SESSION ENABLE PARALLEL DML;
        INSERT /*+ APPEND PARALLEL(24) */ INTO StockItems
          (SELECT * FROM StockItems_Ext);
4.  Commit the insert operation.
        COMMIT;
5.  Drop the external table.
        DROP TABLE StockItems_Ext;

    Repeat these steps for each duplicated table.

### Loading Data into Sharded Tables

Loading data into a sharded table needs to be performed on individual shards because data for a sharded table is partitioned across shards. The load can be done concurrently on all the shards, even if the source data file is shared.

The process of loading is similar to the loading of duplicated tables, with an additional filter in the `INSERT … SELECT` statement to filter out the rows that do not belong to the current shard.

As an example, consider the sharded table created as follows.

    CREATE SHARDED TABLE Customers (
     CustNo     NUMBER(3) NOT NULL,
     CusName    VARCHAR2(30) NOT NULL,
     Street     VARCHAR2(20) NOT NULL,
     City       VARCHAR2(20) NOT NULL,
     State      CHAR(2) NOT NULL,
     Zip        VARCHAR2(10) NOT NULL,
     Phone      VARCHAR2(12),
     CONSTRAINT RootPK PRIMARY KEY (CustNo)
    )
    PARTITION BY CONSISTENT HASH (CustNo)
    PARTITIONS AUTO
    TABLESPACE SET ts1
    ;

Loading data into this table involves doing the following steps on each shard.

1.  Create the directory object in the same way as done for the duplicated tables.
2.  Create an external table for Customers table.
        ALTER SESSION DISABLE SHARD DDL;
        CREATE TABLE Customers_Ext (
         CustNo     NUMBER(3) NOT NULL,
         CusName    VARCHAR2(30) NOT NULL,
         Street     VARCHAR2(20) NOT NULL,
         City       VARCHAR2(20) NOT NULL,
         State      CHAR(2) NOT NULL,
         Zip        VARCHAR2(10) NOT NULL,
         Phone      VARCHAR2(12)
        )
        ORGANIZATION EXTERNAL
        (TYPE ORACLE_LOADER DEFAULT DIRECTORY shard_dir
            ACCESS PARAMETERS
            (FIELDS TERMINATED BY ’|’ (
              CustNo, CusName, Street, City, State, Zip, Phone)
            )LOCATION (’Customers.dat’)
         );
3.  Insert data from external table into sharded table.
        ALTER SESSION ENABLE PARALLEL DML;

        INSERT /*+ APPEND PARALLEL(24) */ INTO Customers
         (SELECT * FROM Customers_Ext WHERE
                SHARD_CHUNK_ID(’UNAME.CUSTOMERS’, CUSTNO) IS NOT NULL
          );

    The operator `SHARD_CHUNK_ID` is used to filter the rows that belong to the current shard. This operator returns a valid chunk number for the given sharding key value. The parameters for this operator are the root table name (in this case `UNAME.CUSTOMERS`) and values of the sharding key columns. When a value does not belong to the current shard, this operator returns `NULL`.

    Note that this operator is introduced in the current release (Oracle Database 21c). If this operator is not available in your version, you must modify the insert statement as follows for the case of system-managed sharding.

        INSERT /*+ APPEND PARALLEL(24) */ INTO Customers c
         (SELECT * FROM Customers_Ext WHERE
                EXISTS (SELECT chunk_number FROM gsmadmin_internal.chunks
                    WHERE ora_hash(c.CustNo)>= low_key
                      AND ora_hash c.CustNo)< high_key)
          );

    This query user internal sharding metadata to decide the eligibility for the row to be inserted.
4.  Commit the insert operation.
        COMMIT;
5.  Drop external tables.
        DROP TABLE Customers_Ext;

Repeat the above steps for each sharded table, starting with the root table and descending down the table family hierarchy to maintain any foreign key constraints.
