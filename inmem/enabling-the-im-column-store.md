To enable or disable the IM column store, specify a value for the `INMEMORY_SIZE` initialization parameter.

### 3.1 Overview of Enabling the IM Column Store

Enable the IM column store size by setting the `INMEMORY_SIZE` initialization parameter.

By default, `INMEMORY_SIZE` is set to `0`, which means the IM column store is disabled. To enable the IM column store, set the initialization parameter `INMEMORY_SIZE` to a value greater than zero before restarting the database instance. You can dynamically increase the `INMEMORY_SIZE` size setting by using an `ALTER SYSTEM` statement.

For the Database In-Memory Base Level only, you can allocate up to 16 GB on any CDB or any instance of an Oracle RAC database.

By default, you must specify candidates for population in the IM column store using the `INMEMORY` clause of a `CREATE` or `ALTER` statement for a table, tablespace, or materialized view.

**See Also:**

- "[In-Memory Initialization Parameters](init-parameters-for-im-column-store.md)"

- [Oracle Database Reference](../refrn/INMEMORY_SIZE.md) to learn more about the `INMEMORY_SIZE` initialization parameter

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-MATERIALIZED-ZONEMAP.md) for more information about the `INMEMORY` clause

- [Oracle Database Licensing Information User Manual](../dblic/Licensing-Information.md) for details on which features are supported for different editions and services

### 3.2 Estimating the Required Size of the IM Column Store

Estimate the size of the IM column store based on your requirements, and then resize the IM column store to meet those requirements. Applying compression can reduce memory size.

The amount of memory required by the IM column store depends on the database objects stored in it and the compression method applied on each object. When choosing a compression method for the `INMEMORY` objects, balance the performance benefits against the amount of available memory:

- To make the greatest reduction in memory size, choose the `FOR CAPACITY HIGH` or `FOR CAPACITY LOW` compression methods. However, these options require additional CPU during query execution to decompress the data.

- To get the best query performance, choose the `FOR QUERY HIGH` or `FOR QUERY LOW` compression methods. However, these options consume more memory.

When sizing the IM column store, consider the following guidelines:

1.  For every object to be populated into the IM column store, estimate the amount of memory it consumes.

    Oracle Compression Advisor estimates the compression ratio that you can realize using the `MEMCOMPRESS` clause. The advisor uses the `DBMS_COMPRESSION` interface.

2.  Add the individual amounts to together.

    **Note:**

    After population, `V$IM_SEGMENTS` shows the actual size of the objects on disk and their size in the IM column store. You can use this information to calculate the compression ratio for the populated objects. However, if the objects were compressed on disk, then this query does not show the correct compression ratio.

3.  If you configured In-Memory Optimized Arithmetic, and if In-Memory tables use `FOR QUERY LOW` compression, then add roughly 15% to account for the dual storage of `NUMBER` columns.

4.  Add space to account for the growth of database objects, and to store updated versions of rows after DML operations.

    The minimum amount for dynamic resizing is 128 MB.

**See Also:**

- "[IM Column Store Compression Methods](populating-objects-in-memory.md)"

- "Enabling the IM Column Store for a Database"

- "Increasing the Size of the IM Column Store Dynamically"

- "[About In-Memory Optimized Arithmetic](optimizing-in-memory-aggregation.md)"

- [Oracle Database Administrator’s Guide](../admin/managing-tables.md) to learn how to estimate compression ratio using Compression Advisor

- [Oracle Database Reference](../refrn/V-IM_SEGMENTS.md) to learn about `V$IM_SEGMENTS`

### 3.3 Enabling the IM Column Store for a Database

Before tables or materialized views can be populated into the IM column store, you must enable the IM column store for the database.

In this context, "database" is a non-CDB, CDB, or PDB. In a CDB, the `INMEMORY_SIZE` setting in the CDB root determines the overall size of the IM column store. By default, all PDBs have access to the IM column store.

Within an individual PDB, you can limit access to the shared In-Memory Area by setting `INMEMORY_SIZE` to a different value. For example, in a CDB with 100 PDBs, you could set `INMEMORY_SIZE` to `16G` at the CDB level, and then set `INMEMORY_SIZE` to `10G` in one PDB, to `6G` in a second PDB, and to `0` in the remaining PDBs.

#### Prerequisites

This task assumes that the following:

- The database is open.

- The `COMPATIBLE` initialization parameter is set to `12.1.0` or higher.

- The `INMEMORY_SIZE` initialization parameter is set to `0` (default).

- You want to use the Database In-Memory Base Level.

#### To enable the IM column store:

1.  In SQL\*Plus or SQL Developer, log in to the database as a user with administrative privileges.

2.  Set the `INMEMORY_SIZE` initialization parameter to a nonzero value.

    When you set this initialization parameter in a server parameter file (SPFILE) using the `ALTER SYSTEM` statement, you must specify `SCOPE=SPFILE`.

    For example, the following statement sets the In-Memory Area size to 16 GB:

        ALTER SYSTEM SET INMEMORY_SIZE = 16G SCOPE=SPFILE;

3.  For the Database In-Memory Base Level, set the `INMEMORY_FORCE` initialization parameter to `BASE_LEVEL`.

    For example, the following statement specifies the Base Level:

        ALTER SYSTEM SET INMEMORY_FORCE=BASE_LEVEL SCOPE=SPFILE;

    You cannot set `INMEMORY_FORCE=``BASE_LEVEL` at the PDB level. Also, you cannot set this parameter dynamically.

4.  Shut down the database, and then reopen it.

    You must reopen the database to initialize the IM column store in the SGA.

5.  Optionally, check the amount of memory currently allocated for the IM column store:

        SHOW PARAMETER INMEMORY_SIZE

    **Note:**

    After the IM column store is enabled, you can increase its size dynamically without reopening the database.

Example 3-1 Enabling the IM Column Store

Assume that the `INMEMORY_SIZE` initialization parameter is set to `0`. The following SQL\*Plus example sets `INMEMORY_SIZE` to 16 GB, shuts down the database instance, and then reopens the database so that the change can take effect:

    SQL> SHOW PARAMETER INMEMORY_SIZE

    NAME                                 TYPE        VALUE
    ------------------------------------ ----------- -----
    inmemory_size                        big integer 0

    SQL> ALTER SYSTEM SET INMEMORY_SIZE=16G SCOPE=SPFILE;

    System altered.

    SQL> SHUTDOWN IMMEDIATE
    Database closed.
    Database dismounted.
    ORACLE instance shut down.

    SQL> STARTUP
    ORACLE instance started.

    Total System Global Area   11525947392 bytes
    Fixed Size                     8213456 bytes
    Variable Size                754977840 bytes
    Database Buffers              16777216 bytes
    Redo Buffers                   8560640 bytes
    In-Memory Area             10737418240 bytes
    Database mounted.
    Database opened.

    SQL> SHOW PARAMETER INMEMORY_SIZE

    NAME                                 TYPE        VALUE
    ------------------------------------ ----------- -----
    inmemory_size                        big integer 16G

**See Also:**

- "[Multiple IM Column Stores](deploying-in-memory-in-oracle-rac.md)"

- [Oracle Database Upgrade Guide](../upgrd/what-is-oracle-database-compatibility.md) for information about setting the database compatibility level

- [Oracle Database Reference](../refrn/INMEMORY_SIZE.md) for more information about the `INMEMORY_SIZE` initialization parameter

### 3.4 Increasing the Size of the IM Column Store Dynamically

You can increase the size of IM column store at database run time by using SQL to reset `INMEMORY_SIZE`.

**Note:**

If ASMM is enabled, it automatically decreases or increases the IM column store size dynamically as needed. If you want to set `INMEMORY_SIZE` to a value smaller than its current setting, check the prerequisites listed here, then issue the `ALTER SYSTEM` statement with `SCOPE=SPFILE` as described below. Then restart the database to effect the change.

#### Prerequisites

To increase the size of the IM column store dynamically using `ALTER SYSTEM`, the instance must meet the following prerequisites:

- The IM column store must be enabled.

- The compatibility level must be `12.2.0` or higher.

- The database instances must be started with an SPFILE.

- The new size of the IM column store must be at least 1 granule.

Steps

1.  In SQL\*Plus or SQL Developer, log in to the database with administrative privileges.
2.  Optionally, check the amount of memory currently allocated for the IM column store:
        SHOW PARAMETER INMEMORY_SIZE
3.  Set the `INMEMORY_SIZE` initialization parameter to a value greater than the current size of the IM column store with an `ALTER SYSTEM` statement that specifies `SCOPE=BOTH` or `SCOPE=MEMORY`.
    When you set this parameter dynamically, you must set it to a value that is higher than its current value, and there must be enough memory available in the SGA to increase the size of the IM column store dynamically to the new value.

    For example, the following statement sets `INMEMORY_SIZE` to `500M` dynamically:
        ALTER SYSTEM SET INMEMORY_SIZE = 500M SCOPE=BOTH;

**See Also:**

- "Enabling the IM Column Store for a Database"

- [Oracle Database Reference](../refrn/INMEMORY_SIZE.md) for more information about the `INMEMORY_SIZE` initialization parameter

### 3.5 Disabling the IM Column Store

You can disable the IM column store by setting the `INMEMORY_SIZE` initialization parameter to zero, and then reopening the database.

#### Assumptions

This task assumes that the IM column store is enabled in an open database.

#### To disable the IM column store:

1.  Set the `INMEMORY_SIZE` initialization parameter to `0` in the server parameter file (SPFILE).

2.  Shut down the database.

3.  Start a database instance, and then open the database.

**See Also:**

[Oracle Database Reference](../refrn/INMEMORY_SIZE.md) for information about the `INMEMORY_SIZE` initialization parameter
