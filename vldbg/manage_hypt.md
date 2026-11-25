The following topics are discussed in this section:

- Creating Hybrid Partitioned Tables

- Converting to Hybrid Partitioned Tables

- Converting Hybrid Partitioned Tables to Internal Partitioned Tables

- Using ADO With Hybrid Partitioned Tables

- Splitting Partitions in a Hybrid Partitioned Table

**See Also:**

- [Hybrid Partitioned Tables](partition-concepts.md) for an overview of hybrid partitioned tables, including information about limitations

### 4.7.1 Creating Hybrid Partitioned Tables

You can use the `EXTERNAL PARTITION ATTRIBUTES` clause of the `CREATE TABLE` statement to determine hybrid partitioning for a table. The partitions of the table can be external and or internal.

A hybrid partitioned table enables partitions to reside both in database data files (internal partitions) and in external files and sources (external partitions). You can create and query a hybrid partitioned table to utilize the benefits of partitioning with classic partitioned tables, such as pruning, on data that is contained in both internal and external partitions.

The `EXTERNAL PARTITION ATTRIBUTES` clause of the `CREATE TABLE` statement is defined at the table level for specifying table level external parameters in the hybrid partitioned table, such as:

- The access driver type, such as `ORACLE_LOADER, ORACLE_DATAPUMP, ORACLE_HDFS, ORACLE_HIVE`

- The default directory for all external partitions files

- The access parameters

The `EXTERNAL` clause of the `PARTITION` clause defines the partition as an external partition. When there is no `EXTERNAL` clause, the partition is an internal partition. You can specify for each external partition different attributes than the default attributes defined at the table level, such the directory. For example, in Example 4-43 the `DEFAULT DIRECTORY` value for partitions `sales_data2`, `sales_data3`, and `sales_data_acfs` is different than the `DEFAULT DIRECTORY` value defined in the `EXTERNAL PARTITION ATTRIBUTES` clause.

When there is no external file defined for an external partition, the external partition is empty. It can be populated with an external file by using an `ALTER TABLE MODIFY PARTITION` statement. Note that at least one partition must be an internal partition.

In Example 4-43, a hybrid range-partitioned table is a created with four external partitions and two internal partitions. The external comma-separated (CSV) data files are stored in the `sales_data` , `sales_data2`, `sales_data3`, and `sales_data_acfs` directories defined by the `DEFAULT DIRECTORY` clauses. `sales_data` is defined as the overall `DEFAULT DIRECTORY` in the `EXTERNAL PARTITION ATTRIBUTES` clause. The other directories are defined at the partition level. `sales_2014` and `sales_2015` are internal partitions. Data directory `sales_data_acfs` is stored on an Oracle ACFS file system to illustrate the use of that storage option.

In Example 4-44, an additional external partition is added to the hybrid range-partitioned table.

Example 4-43 Creating a Hybrid Range-Partitioned Table

    REM Connect as a user with appropriate privileges,
    REM then run the following to set up data directories that contain the data files
    CREATE DIRECTORY sales_data AS '/u01/my_data/sales_data1';
    GRANT READ,WRITE ON DIRECTORY sales_data TO hr;

    CREATE DIRECTORY sales_data2 AS '/u01/my_data/sales_data2';
    GRANT READ,WRITE ON DIRECTORY sales_data2 TO hr;

    CREATE DIRECTORY sales_data3 AS '/u01/my_data/sales_data3';
    GRANT READ,WRITE ON DIRECTORY sales_data3 TO hr;

    REM set up a data directory on an Oracle ACFS mount point (file system)
    CREATE DIRECTORY sales_data_acfs AS '/u01/acfsmounts/acfs1';
    GRANT READ,WRITE ON DIRECTORY sales_data_acfs TO hr;

    CONNECT AS hr, run the following
    CREATE TABLE hybrid_partition_table
      ( prod_id       NUMBER        NOT NULL,
        cust_id       NUMBER        NOT NULL,
        time_id       DATE          NOT NULL,
        channel_id    NUMBER        NOT NULL,
        promo_id      NUMBER        NOT NULL,
        quantity_sold NUMBER(10,2)  NOT NULL,
        amount_sold   NUMBER(10,2)  NOT NULL
      )
        EXTERNAL PARTITION ATTRIBUTES (
          TYPE ORACLE_LOADER
          DEFAULT DIRECTORY sales_data
           ACCESS PARAMETERS(
             FIELDS TERMINATED BY ','
             (prod_id,cust_id,time_id DATE 'dd-mm-yyyy',channel_id,promo_id,quantity_sold,amount_sold)
           )
          REJECT LIMIT UNLIMITED
         )
        PARTITION BY RANGE (time_id)
        (PARTITION sales_2014 VALUES LESS THAN (TO_DATE('01-01-2015','dd-mm-yyyy')),
         PARTITION sales_2015 VALUES LESS THAN (TO_DATE('01-01-2016','dd-mm-yyyy')),
         PARTITION sales_2016 VALUES LESS THAN (TO_DATE('01-01-2017','dd-mm-yyyy')) EXTERNAL
              LOCATION ('sales2016_data.txt'),
         PARTITION sales_2017 VALUES LESS THAN (TO_DATE('01-01-2018','dd-mm-yyyy')) EXTERNAL
              DEFAULT DIRECTORY sales_data2 LOCATION ('sales2017_data.txt'),
         PARTITION sales_2018 VALUES LESS THAN (TO_DATE('01-01-2019','dd-mm-yyyy')) EXTERNAL
              DEFAULT DIRECTORY sales_data3 LOCATION ('sales2018_data.txt'),
         PARTITION sales_2019 VALUES LESS THAN (TO_DATE('01-01-2020','dd-mm-yyyy')) EXTERNAL
              DEFAULT DIRECTORY sales_data_acfs LOCATION ('sales2019_data.txt')
     );

Example 4-44 Adding an External Partition to a Hybrid Range-artitioned Table

    ALTER TABLE hybrid_partition_table
          ADD PARTITION sales_2020 VALUES LESS THAN (TO_DATE('01-01-2021','dd-mm-yyyy'))
              EXTERNAL DEFAULT DIRECTORY sales_data_acfs  LOCATION ('sales2020_data.txt');

**See Also:**

- [Hybrid Partitioned Tables](partition-concepts.md)

### 4.7.2 Converting to Hybrid Partitioned Tables

You can convert a table with only internal partitions to a hybrid partitioned table.

In Example 4-45, an internal range partitioned table is converted to a hybrid partitioned table. You must add external partition attributes to an existing table first, then add external partitions. Note that at least one partition must be an internal partition.

Example 4-45 Converting to a Hybrid Range-Partitioned Table

    CREATE TABLE internal_to_hypt_table (
        prod_id       NUMBER        NOT NULL,
        cust_id       NUMBER        NOT NULL,
        time_id       DATE          NOT NULL,
        channel_id    NUMBER        NOT NULL,
        promo_id      NUMBER        NOT NULL,
        quantity_sold NUMBER(10,2)  NOT NULL,
        amount_sold   NUMBER(10,2)  NOT NULL
      )
       PARTITION by range (time_id)
       (PARTITION sales_2014 VALUES LESS THAN (TO_DATE('01-01-2015','dd-mm-yyyy'))
      );

    SELECT HYBRID FROM USER_TABLES WHERE TABLE_NAME = 'INTERNAL_TO_HYPT_TABLE';
    HYB
    ---
    NO

    ALTER TABLE internal_to_hypt_table
      ADD EXTERNAL PARTITION ATTRIBUTES
       (TYPE ORACLE_LOADER
         DEFAULT DIRECTORY sales_data
         ACCESS PARAMETERS (
           FIELDS TERMINATED BY ','
           (prod_id,cust_id,time_id DATE 'dd-mm-yyyy',channel_id,promo_id,quantity_sold,amount_sold)
         )
       )
    ;

    ALTER TABLE internal_to_hypt_table
          ADD PARTITION sales_2015 VALUES LESS THAN (TO_DATE('01-01-2016','dd-mm-yyyy'))
              EXTERNAL LOCATION ('sales2015_data.txt');

    ALTER TABLE internal_to_hypt_table
          ADD PARTITION sales_2016 VALUES LESS THAN (TO_DATE('01-01-2017','dd-mm-yyyy'))
              EXTERNAL LOCATION ('sales2016_data.txt');

    SELECT HYBRID FROM USER_TABLES WHERE TABLE_NAME = 'INTERNAL_TO_HYPT_TABLE';
    HYB
    ---
    YES

    SELECT DEFAULT_DIRECTORY_NAME FROM USER_EXTERNAL_TABLES WHERE TABLE_NAME = 'INTERNAL_TO_HYPT_TABLE';
    DEFAULT_DIRECTORY_NAME
    ---------------------------------------------------------------------------------------------
    SALES_DATA

**See Also:**

- [Hybrid Partitioned Tables](partition-concepts.md)

### 4.7.3 Converting Hybrid Partitioned Tables to Internal Partitioned Tables

You can convert a hybrid partitioned table to a table with only internal partitions.

In Example 4-46, a hybrid partitioned table is converted to an internal range partitioned table. First, you must drop the external partitions and then you can drop the external partition attributes.

Example 4-46 Converting from a Hybrid Partitioned Table to an Internal Table

    CREATE TABLE hypt_to_int_table
      ( prod_id       NUMBER        NOT NULL,
        cust_id       NUMBER        NOT NULL,
        time_id       DATE          NOT NULL,
        channel_id    NUMBER        NOT NULL,
        promo_id      NUMBER        NOT NULL,
        quantity_sold NUMBER(10,2)  NOT NULL,
        amount_sold   NUMBER(10,2)  NOT NULL
      )
        EXTERNAL PARTITION ATTRIBUTES (
         TYPE ORACLE_LOADER
         DEFAULT DIRECTORY sales_data
           ACCESS PARAMETERS(
            FIELDS TERMINATED BY ','
            (prod_id,cust_id,time_id DATE 'dd-mm-yyyy',channel_id,promo_id,quantity_sold,amount_sold)
           )
          REJECT LIMIT UNLIMITED
         )
        PARTITION BY RANGE (time_id)
        (PARTITION sales_2014 VALUES LESS THAN (TO_DATE('01-01-2015','dd-mm-yyyy')),
         PARTITION sales_2015 VALUES LESS THAN (TO_DATE('01-01-2016','dd-mm-yyyy')),
         PARTITION sales_2016 VALUES LESS THAN (TO_DATE('01-01-2017','dd-mm-yyyy'))
              EXTERNAL LOCATION ('sales2016_data.txt'),
         PARTITION sales_2017 VALUES LESS THAN (TO_DATE('01-01-2018','dd-mm-yyyy'))
              EXTERNAL DEFAULT DIRECTORY sales_data2 LOCATION ('sales2017_data.txt'),
         PARTITION sales_2018 VALUES LESS THAN (TO_DATE('01-01-2019','dd-mm-yyyy'))
              EXTERNAL DEFAULT DIRECTORY sales_data3 LOCATION ('sales2018_data.txt'),
         PARTITION sales_2019 VALUES LESS THAN (TO_DATE('01-01-2020','dd-mm-yyyy'))
              EXTERNAL DEFAULT DIRECTORY sales_data_acfs LOCATION ('sales2019_data.txt')
     );

    SELECT HYBRID FROM USER_TABLES WHERE TABLE_NAME = 'HYPT_TO_INT_TABLE';
    HYB
    ---
    YES

    ALTER TABLE hypt_to_int_table DROP PARTITION sales_2016;
    ALTER TABLE hypt_to_int_table DROP PARTITION sales_2017;
    ALTER TABLE hypt_to_int_table DROP PARTITION sales_2018;
    ALTER TABLE hypt_to_int_table DROP PARTITION sales_2019;

    ALTER TABLE hypt_to_int_table DROP EXTERNAL PARTITION ATTRIBUTES();

    SELECT HYBRID FROM USER_TABLES WHERE TABLE_NAME = 'HYPT_TO_INT_TABLE';
    HYB
    ---
    NO

**See Also:**

- [Hybrid Partitioned Tables](partition-concepts.md)

### 4.7.4 Using ADO With Hybrid Partitioned Tables

You can use Automatic Data Optimization (ADO) policies with hybrid partitioned tables under some conditions.

In Example 4-47, note that ADO policies are only defined on the internal partitions of the table.

Example 4-47 Using ADO with a Hybrid Partitioned Table

    SQL> CREATE TABLE hypt_ado_table
      ( prod_id       NUMBER        NOT NULL,
        cust_id       NUMBER        NOT NULL,
        time_id       DATE          NOT NULL,
        channel_id    NUMBER        NOT NULL,
        promo_id      NUMBER        NOT NULL,
        quantity_sold NUMBER(10,2)  NOT NULL,
        amount_sold   NUMBER(10,2)  NOT NULL
      )
        EXTERNAL PARTITION ATTRIBUTES (
         TYPE ORACLE_LOADER
         DEFAULT DIRECTORY sales_data
           ACCESS PARAMETERS(
            FIELDS TERMINATED BY ','
            (prod_id,cust_id,time_id DATE 'dd-mm-yyyy',channel_id,promo_id,quantity_sold,amount_sold)
           )
          REJECT LIMIT UNLIMITED
         )
        PARTITION BY RANGE (time_id)
        (PARTITION sales_2014 VALUES LESS THAN (TO_DATE('01-01-2015','dd-mm-yyyy')),
         PARTITION sales_2015 VALUES LESS THAN (TO_DATE('01-01-2016','dd-mm-yyyy')),
         PARTITION sales_2016 VALUES LESS THAN (TO_DATE('01-01-2017','dd-mm-yyyy'))
              EXTERNAL LOCATION ('sales2016_data.txt'),
         PARTITION sales_2017 VALUES LESS THAN (TO_DATE('01-01-2018','dd-mm-yyyy'))
              EXTERNAL DEFAULT DIRECTORY sales_data2 LOCATION ('sales2017_data.txt'),
         PARTITION sales_2018 VALUES LESS THAN (TO_DATE('01-01-2019','dd-mm-yyyy'))
              EXTERNAL DEFAULT DIRECTORY sales_data3 LOCATION ('sales2018_data.txt'),
         PARTITION sales_2019 VALUES LESS THAN (TO_DATE('01-01-2020','dd-mm-yyyy'))
              EXTERNAL DEFAULT DIRECTORY sales_data4 LOCATION ('sales2019_data.txt')
     );
    Table created.

    SQL> SELECT HYBRID FROM USER_TABLES WHERE TABLE_NAME = 'HYPT_ADO_TABLE';
    HYB
    ---
    YES

    SQL> ALTER TABLE hypt_ado_table MODIFY PARTITION sales_2014 ILM ADD POLICY ROW STORE COMPRESS ADVANCED ROW AFTER 6 MONTHS OF NO MODIFICATION;
    Table altered.

    SQL> ALTER TABLE hypt_ado_table MODIFY PARTITION sales_2015 ILM ADD POLICY ROW STORE COMPRESS ADVANCED ROW AFTER 6 MONTHS OF NO MODIFICATION;
    Table altered.

    SQL> SELECT POLICY_NAME, POLICY_TYPE, ENABLED FROM USER_ILMPOLICIES;
    POLICY_NAME    POLICY_TYPE     ENA
    -------------  --------------- -----
    P1             DATA MOVEMENT   YES
    P2             DATA MOVEMENT   YES

**See Also:**

- [Using Automatic Data Optimization](ilm-strategy-heatmap-ado.md) for information about ADO policies

### 4.7.5 Splitting Partitions in a Hybrid Partitioned Table

In Example 4-48, the default (MAXVALUE) partition is split into a two partitions: a new partition and the existing default position. You can split a default partition similar to splitting any other partition.

Example 4-48 Splitting the Default Partition in a Hybrid Partitioned Table

    CREATE TABLE hybrid_split_table
      ( prod_id       NUMBER        NOT NULL,
        cust_id       NUMBER        NOT NULL,
        time_id       DATE          NOT NULL,
        channel_id    NUMBER        NOT NULL,
        promo_id      NUMBER        NOT NULL,
        quantity_sold NUMBER(10,2)  NOT NULL,
        amount_sold   NUMBER(10,2)  NOT NULL
      )
        EXTERNAL PARTITION ATTRIBUTES (
         TYPE ORACLE_LOADER
         DEFAULT DIRECTORY sales_data
           ACCESS PARAMETERS(
            FIELDS TERMINATED BY ','
            (prod_id,cust_id,time_id DATE 'dd-mm-yyyy',channel_id,promo_id,quantity_sold,amount_sold)
           )
          REJECT LIMIT UNLIMITED
         )
        PARTITION BY RANGE (time_id)
         (PARTITION sales_2016 VALUES LESS THAN (TO_DATE('01-01-2017','dd-mm-yyyy'))
              EXTERNAL LOCATION ('sales2016_data.txt'),
          PARTITION sales_2017 VALUES LESS THAN (TO_DATE('01-01-2018','dd-mm-yyyy'))
              EXTERNAL LOCATION ('sales2017_data.txt'),
         PARTITION sales_2018 VALUES LESS THAN (TO_DATE('01-01-2019','dd-mm-yyyy')),
         PARTITION sales_2019 VALUES LESS THAN (TO_DATE('01-01-2020','dd-mm-yyyy')),
         PARTITION sales_future VALUES LESS THAN (MAXVALUE)
     );

    SELECT HYBRID FROM USER_TABLES WHERE TABLE_NAME = 'HYBRID_SPLIT_TABLE';
    HYB
    ---
    YES

    SELECT DEFAULT_DIRECTORY_NAME FROM USER_EXTERNAL_TABLES WHERE TABLE_NAME = 'HYBRID_SPLIT_TABLE';
    DEFAULT_DIRECTORY_NAME
    --------------------------------------------------------------------------------
    SALES_DATA

    INSERT INTO hybrid_split_table VALUES (1001,100,TO_DATE('10-02-2018','dd-mm-yyyy'),10,15,500,7500);
    INSERT INTO hybrid_split_table VALUES (1002,110,TO_DATE('15-06-2018','dd-mm-yyyy'),12,18,100,3200);
    ...
    INSERT INTO hybrid_split_table VALUES (1002,110,TO_DATE('12-01-2019','dd-mm-yyyy'),12,18,150,4800);
    INSERT INTO hybrid_split_table VALUES (1001,100,TO_DATE('16-02-2019','dd-mm-yyyy'),10,15,400,6500);
    ...
    INSERT INTO hybrid_split_table VALUES (1002,110,TO_DATE('19-02-2020','dd-mm-yyyy'),12,18,150,4800);
    INSERT INTO hybrid_split_table VALUES (1001,100,TO_DATE('12-03-2020','dd-mm-yyyy'),10,15,400,6500);
    ...

    SELECT * FROM hybrid_split_table PARTITION(sales_2016);
       PROD_ID    CUST_ID TIME_ID   CHANNEL_ID   PROMO_ID QUANTITY_SOLD AMOUNT_SOLD
    ---------- ---------- --------- ---------- ---------- ------------- -----------
          1001        100 10-JAN-16         10         15           500        7500
          1002        110 25-JAN-16         12         18           100        3200
    ...

    SELECT * FROM hybrid_split_table PARTITION(sales_2017);
       PROD_ID    CUST_ID TIME_ID   CHANNEL_ID   PROMO_ID QUANTITY_SOLD AMOUNT_SOLD
    ---------- ---------- --------- ---------- ---------- ------------- -----------
          1002        110 15-JAN-17         12         18           100        3200
          1001        100 10-FEB-17         10         15           500        7500
    ...

    SELECT * FROM hybrid_split_table PARTITION(sales_2018);
       PROD_ID    CUST_ID TIME_ID   CHANNEL_ID   PROMO_ID QUANTITY_SOLD AMOUNT_SOLD
    ---------- ---------- --------- ---------- ---------- ------------- -----------
          1001        100 10-FEB-18         10         15           500        7500
          1002        110 15-JUN-18         12         18           100        3200
    ...

    SELECT * FROM hybrid_split_table PARTITION(sales_2019);
       PROD_ID    CUST_ID TIME_ID   CHANNEL_ID   PROMO_ID QUANTITY_SOLD AMOUNT_SOLD
    ---------- ---------- --------- ---------- ---------- ------------- -----------
          1002        110 12-JAN-19         12         18           150        4800
          1001        100 16-FEB-19         10         15           400        6500
    ...

    SELECT * FROM hybrid_split_table PARTITION(sales_future);
       PROD_ID    CUST_ID TIME_ID   CHANNEL_ID   PROMO_ID QUANTITY_SOLD AMOUNT_SOLD
    ---------- ---------- --------- ---------- ---------- ------------- -----------
          1002        110 19-FEB-20         12         18           150        4800
          1001        100 12-MAR-20         10         15           400        6500
          1001        100 31-MAR-20         10         15           600        8000
          2105        101 25-APR-20         12         19           100        3000

    ALTER TABLE hybrid_split_table
      SPLIT PARTITION sales_future INTO
      (PARTITION sales_2020 VALUES LESS THAN (TO_DATE('01-01-2021','dd-mm-yyyy')),
       PARTITION sales_future
       );

    SELECT * FROM hybrid_split_table PARTITION(sales_2020);
       PROD_ID    CUST_ID TIME_ID   CHANNEL_ID   PROMO_ID QUANTITY_SOLD AMOUNT_SOLD
    ---------- ---------- --------- ---------- ---------- ------------- -----------
          1002        110 19-FEB-20         12         18           150        4800
          1001        100 12-MAR-20         10         15           400        6500
          1001        100 31-MAR-20         10         15           600        8000
          2105        101 25-APR-20         12         19           100        3000

    SELECT * FROM hybrid_split_table PARTITION(sales_future);
    no rows selected

### 4.7.6 Exchanging Data in Hybrid Partitioned Tables

You can exchange data of an internal partition in a hybrid partitioned table with an external nonpartitioned table, and exchange data of external nonpartitioned table with an internal partition in a hybrid partitioned table. Oracle supports exchange between internal and external storage but does not support a move operation between these tiers. Moving data between internal and external storage is a separate operation prior to exchange.

Example 4-49 Exchanging data of an internal partition of a hybrid partitioned table with an external nonpartioned table

In this example, data of an internal partition of an hybrid partitioned table is "moved" to external storage using exchange partition with a nonpartitioned external table containing the exact same data.

Create a hybrid partitioned table of TYPE ORACLE_DATAPUMP.

    CREATE TABLE hybrid_datapump_sales
      ( prod_id  NUMBER     NOT NULL,
        cust_id       NUMBER        NOT NULL,
        time_id       DATE          NOT NULL,
        channel_id    NUMBER        NOT NULL,
        promo_id      NUMBER        NOT NULL,
        quantity_sold NUMBER(10,2)  NOT NULL,
        amount_sold   NUMBER(10,2)  NOT NULL
      )
      EXTERNAL PARTITION ATTRIBUTES
      (TYPE ORACLE_DATAPUMP
       DEFAULT DIRECTORY sales_data
       ACCESS PARAMETERS (NOLOGFILE)
      )
      PARTITION by range (time_id)
      (
       PARTITION sales_old VALUES LESS THAN (TO_DATE('01-01-2018', 'DD-MM-YYYY'))
         EXTERNAL LOCATION ('sales_old.dmp'),
       PARTITION sales_2018 VALUES LESS THAN (TO_DATE('01-01-2019','dd-mm-yyyy')),
       PARTITION sales_2019 VALUES LESS THAN (TO_DATE('01-01-2020','dd-mm-yyyy')),
       PARTITION sales_2020 VALUES LESS THAN (TO_DATE('01-01-2021','dd-mm-yyyy')),
       PARTITION sales_future VALUES LESS THAN (MAXVALUE)
    );

Populate the hybrid partitioned table `hybrid_datapump_sales` with some data for this example.

    SELECT * FROM hybrid_datapump_sales PARTITION(sales_2018);

       PROD_ID    CUST_ID TIME_ID   CHANNEL_ID   PROMO_ID QUANTITY_SOLD AMOUNT_SOLD
    ---------- ---------- --------- ---------- ---------- ------------- -----------
          1001        100 10-FEB-18         10         15           500        7500
          1002        110 15-JUN-18         12         18           100        3200
          1002        110 30-MAR-18         10         15           500        6500
          2105        102 21-APR-18         18         12           100        2000
          1200        155 30-APR-18         20         20           300        3600

Create an external table with the same structure as the `sales_2018` partition. The `SELECT` clause completes data movement. The data movement operation needs to be done prior to exchange.

    CREATE TABLE year_2018_datapump
       ORGANIZATION EXTERNAL
       ( TYPE ORACLE_DATAPUMP DEFAULT DIRECTORY sales_data
         ACCESS PARAMETERS (NOLOGFILE) LOCATION ('sales_2018.dmp')
        )
       AS SELECT * FROM hybrid_datapump_sales PARTITION(sales_2018);

Exchange the data in `sales_2018` partition with the data in the external table.

    ALTER TABLE hybrid_datapump_sales
          EXCHANGE PARTITION(sales_2018) WITH TABLE year_2018_datapump;

    SELECT * FROM year_2018_datapump;

       PROD_ID    CUST_ID TIME_ID   CHANNEL_ID   PROMO_ID QUANTITY_SOLD AMOUNT_SOLD
    ---------- ---------- --------- ---------- ---------- ------------- -----------
          1001        100 10-FEB-18         10         15           500        7500
          1002        110 15-JUN-18         12         18           100        3200
          1002        110 30-MAR-18         10         15           500        6500
          2105        102 21-APR-18         18         12           100        2000
          1200        155 30-APR-18         20         20           300        3600

Example 4-50 Exchanging data of an external nonpartitioned table with an internal partition of a hybrid partitioned table

In this example, data of an external table is exchanged with an internal partition of a hybrid partitioned table to add new data to a partition of the hybrid partitioned table. The text data that has been loaded into the external table is first copied to a temporary nonpartitioned internal table. Then the nonpartitioned internal table is exchanged with an internal partition of a hybrid partitioned table.

Create a hybrid partitioned table of TYPE ORACLE_DATAPUMP.

    CREATE TABLE hybrid_datapump_sales
        ( prod_id  NUMBER     NOT NULL,
          cust_id       NUMBER        NOT NULL,
          time_id       DATE          NOT NULL,
          channel_id    NUMBER        NOT NULL,
          promo_id      NUMBER        NOT NULL,
          quantity_sold NUMBER(10,2)  NOT NULL,
          amount_sold   NUMBER(10,2)  NOT NULL
         )
         EXTERNAL PARTITION ATTRIBUTES
          (TYPE ORACLE_DATAPUMP
           DEFAULT DIRECTORY sales_data
           ACCESS PARAMETERS (NOLOGFILE)
          )
         PARTITION by range (time_id)
         (
          PARTITION sales_old VALUES LESS THAN (TO_DATE('01-01-2018', 'dd-mm-yyyy'))
           EXTERNAL LOCATION ('sales_old.dmp'),
          PARTITION sales_2018 VALUES LESS THAN (TO_DATE('01-01-2019','dd-mm-yyyy')),
          PARTITION sales_2019 VALUES LESS THAN (TO_DATE('01-01-2020','dd-mm-yyyy')),
          PARTITION sales_2020 VALUES LESS THAN (TO_DATE('01-01-2021','dd-mm-yyyy')),
          PARTITION sales_future VALUES LESS THAN (MAXVALUE)
      );

Note that the `sales_2020` partition has no records.

    SELECT * FROM hybrid_datapump_sales PARTITION(sales_2020);

    no rows selected

For this example, create an external table and load it with a text file that has been generated by some application.

    CREATE TABLE ext_sales_year_2020
            ( prod_id       NUMBER        NOT NULL,
              cust_id       NUMBER        NOT NULL,
              time_id       DATE          NOT NULL,
              channel_id    NUMBER        NOT NULL,
              promo_id      NUMBER        NOT NULL,
              quantity_sold NUMBER(10,2)  NOT NULL,
              amount_sold   NUMBER(10,2)  NOT NULL
             )
            ORGANIZATION EXTERNAL
            (
             TYPE ORACLE_LOADER DEFAULT DIRECTORY sales_data
             ACCESS PARAMETERS (
             FIELDS TERMINATED BY ','
             (prod_id,cust_id,time_id DATE 'dd-mm-yyyy',channel_id,promo_id,quantity_sold,amount_sold)
             )
             LOCATION ('sales2020_data.txt')
     );

    SELECT * FROM ext_sales_year_2020;

       PROD_ID    CUST_ID TIME_ID   CHANNEL_ID   PROMO_ID QUANTITY_SOLD AMOUNT_SOLD
    ---------- ---------- --------- ---------- ---------- ------------- -----------
          1001        100 10-JAN-20         10         15           500        7500
          1002        110 15-JAN-20         12         18           100        3200
          1001        100 20-JAN-20         10         15           500        7500
          2105        101 15-FEB-20         12         19            10         300
          2105        102 21-MAR-20         18         12           100        2000
          1200        155 30-MAR-20         20         20           300        3600
          1400        165 05-JUN-20         22         15           100        4000
          2105        125 05-JUN-20         12         16            40        8500
          2105        302 15-SEP-20         10         11            75        4350
          2108        305 18-NOV-20         10         11            70        4250

    10 rows selected.

Create a temporary internal table for the exchanging of data with the hybrid partitioned table.

    CREATE TABLE sales_year_2020 AS SELECT * FROM ext_sales_year_2020;

    SELECT * FROM sales_year_2020;

       PROD_ID    CUST_ID TIME_ID   CHANNEL_ID   PROMO_ID QUANTITY_SOLD AMOUNT_SOLD
    ---------- ---------- --------- ---------- ---------- ------------- -----------
          1001        100 10-JAN-20         10         15           500        7500
          1002        110 15-JAN-20         12         18           100        3200
          1001        100 20-JAN-20         10         15           500        7500
          2105        101 15-FEB-20         12         19            10         300
          2105        102 21-MAR-20         18         12           100        2000
          1200        155 30-MAR-20         20         20           300        3600
          1400        165 05-JUN-20         22         15           100        4000
          2105        125 05-JUN-20         12         16            40        8500
          2105        302 15-SEP-20         10         11            75        4350
          2108        305 18-NOV-20         10         11            70        4250

    10 rows selected.

Exchange data in the temporary internal table with the `sales_2020` partition to load the data into the hybrid partitioned table.

    ALTER TABLE hybrid_datapump_sales
           EXCHANGE PARTITION(sales_2020) WITH TABLE sales_year_2020;

    SELECT * FROM hybrid_datapump_sales PARTITION(sales_2020);

       PROD_ID    CUST_ID TIME_ID   CHANNEL_ID   PROMO_ID QUANTITY_SOLD AMOUNT_SOLD
    ---------- ---------- --------- ---------- ---------- ------------- -----------
          1001        100 10-JAN-20         10         15           500        7500
          1002        110 15-JAN-20         12         18           100        3200
          1001        100 20-JAN-20         10         15           500        7500
          2105        101 15-FEB-20         12         19            10         300
          2105        102 21-MAR-20         18         12           100        2000
          1200        155 30-MAR-20         20         20           300        3600
          1400        165 05-JUN-20         22         15           100        4000
          2105        125 05-JUN-20         12         16            40        8500
          2105        302 15-SEP-20         10         11            75        4350
          2108        305 18-NOV-20         10         11            70        4250

    10 rows selected.
