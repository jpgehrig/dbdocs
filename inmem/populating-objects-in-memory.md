This chapter explains how to enable and disable objects for population in the IM column store, including setting compression and priority options.

This chapter contains the following topics:

### 4.1 About Manually Enabling Objects for In-Memory Population

Only objects with the `INMEMORY` clause are eligible for population into the IM column store. To apply this clause manually, you must use DDL statements such as `CREATE TABLE` or `ALTER TABLE`.

#### 4.1.1 Purpose of Enabling Objects for In-Memory Population

By default, objects implicitly have the `NO INMEMORY` attribute, which means they are ineligible for population into the IM column store.

Only when you use DDL to specify objects as `INMEMORY` are they eligible for population. Enabling an object as `INMEMORY` is specifying that an object can potentially reside in the IM column store. In-Memory population is a separate step that occurs when the database reads existing row-format data from disk, transforms it into columnar format, and then stores it in the IM column store.

Population, which transforms existing data on disk into columnar format, is different from [repopulation](glossary.md), which transforms new data into columnar format. Because IMCUs are read-only structures, Oracle Database does not populate them when rows change. Rather, the database records the row changes in a [transaction journal](glossary.md), and then creates new IMCUs as part of repopulation.

**Related Topics**

- [Optimizing Repopulation of the IM Column Store](repopulation-and-dml.md)
- [In-Memory Compression Units (IMCUs)](in-memory-column-store-architecture.md)

#### 4.1.2 How In-Memory Population Works

You can specify that the database populates objects in the IM column store either at database instance startup or when `INMEMORY` objects are accessed.

The population algorithm also varies depending on whether you use single-instance or Oracle RAC.

This section contains the following topics:

##### 4.1.2.1 Prioritization of In-Memory Population

DDL statements include an `INMEMORY PRIORITY` subclause that provides more control over the population queue.

**Note:**

The `INMEMORY PRIORITY` subclause controls the priority of population, but not the speed of population.

The priority level setting applies to an entire table, partition, or subpartition, not to different column subsets. Setting the `INMEMORY` attribute on an object means that this object is a candidate for population in the IM column store. It does not mean that the database immediately populates the object.

**Note:**

If a segment on disk is 64 KB or less, then it is not populated in the IM column store. Therefore, some small database objects that were enabled for the IM column store might not be populated.

Oracle Database manages prioritization as follows:

- On-demand population

  By default, the `INMEMORY PRIORITY` parameter is set to `NONE`. In this case, the database only populates the object when it is accessed through a full table scan. If the object is never accessed, or if it is accessed only through an index scan or fetch by rowid, then population never occurs.

- Priority-based population

  When `PRIORITY` is set to a value other than `NONE`, Oracle database automatically populates the objects using an internally managed priority queue. In this case, a full scan is not a necessary condition for population. The database does the following:

  - Populates columnar data in the IM column store automatically after the database instance restarts

  - Queues population of `INMEMORY` objects based on the specified priority level

    For example, a table altered with `INMEMORY PRIORITY CRITICAL` takes precedence over a table altered with `INMEMORY PRIORITY HIGH`, which in turn takes precedence over a table altered with `INMEMORY PRIORITY LOW`. If the IM column store has insufficient space, then Oracle Database does not populate additional objects until space is available.

  - Waits to return from `ALTER TABLE` or `ALTER MATERIALIZED VIEW` statements until the changes to the object are recorded in the IM column store

After a segment is populated in the IM column store, the database only evicts it when the segment is dropped or moved, or the segment is updated with the `NO INMEMORY` attribute. You can evict a segment manually or by means of an [ADO policy](glossary.md).

Example 4-1 Population of an Object in the IM Column Store

Before completing this example, the IM column store must be enabled for the database.

1.  Log in to the database as an administrator, and then query the `customers` table as follows:

        SELECT cust_id, cust_last_name, cust_first_name
        FROM   sh.customers
        WHERE  cust_city = 'Hyderabad'
        AND    cust_income_level LIKE 'C%'
        AND    cust_year_of_birth > 1960;

2.  Display the execution plan for the query:

        SQL> SELECT * FROM TABLE(DBMS_XPLAN.DISPLAY_CURSOR(FORMAT=>'+ALLSTATS'));
        SQL_ID  frgk9dbaftmm9, child number 0
        -------------------------------------
        SELECT cust_id, cust_last_name, cust_first_name FROM   sh.customers
        WHERE  cust_city = 'Hyderabad' AND    cust_income_level LIKE 'C%' AND
         cust_year_of_birth > 1960

        Plan hash value: 2008213504

        -------------------------------------------------------------------------------
        | Id| Operation         | Name      |Starts|E-Rows|A-Rows|   A-Time   |Buffers|
        -------------------------------------------------------------------------------
        |  0| SELECT STATEMENT  |           |     1|      |    6 |00:00:00.01 |   1523|
        |* 1|  TABLE ACCESS FULL| CUSTOMERS |     1|    6 |    6 |00:00:00.01 |   1523|
        -------------------------------------------------------------------------------

        Predicate Information (identified by operation id):
        ---------------------------------------------------

           1 - filter(("CUST_CITY"='Hyderabad' AND "CUST_YEAR_OF_BIRTH">1960 AND
                      "CUST_INCOME_LEVEL" LIKE 'C%'))

3.  Enable the `sh.customers` table for population in the IM column store:

        ALTER TABLE sh.customers INMEMORY;

    The preceding statement uses the default priority of `NONE`. A full scan is required to populate objects with no priority.

4.  To determine whether data from the `sh.customers` table has been populated in the IM column store, execute the following query (sample output included):

        SELECT SEGMENT_NAME, POPULATE_STATUS
        FROM   V$IM_SEGMENTS
        WHERE  SEGMENT_NAME = 'CUSTOMERS';

        no rows selected

    In this case, no segments are populated in the IM column store because the `sh.customers` table has not yet been scanned.

5.  Query `sh.customers` using the same statement as in Step 1:

        SELECT cust_id, cust_last_name, cust_first_name
        FROM   sh.customers
        WHERE  cust_city = 'Hyderabad'
        AND    cust_income_level LIKE 'C%'
        AND    cust_year_of_birth > 1960;

6.  Querying the cursor shows that the database performed a full scan and accessed the IM column store:

        SQL> SELECT * FROM TABLE(DBMS_XPLAN.DISPLAY_CURSOR(FORMAT=>'+ALLSTATS'));
        SQL_ID  frgk9dbaftmm9, child number 0
        -------------------------------------
        SELECT cust_id, cust_last_name, cust_first_name FROM   sh.customers
        WHERE  cust_city = 'Hyderabad' AND    cust_income_level LIKE 'C%' AND
         cust_year_of_birth > 1960

        Plan hash value: 2008213504

        ---------------------------------------------------------------------------------
        | Id| Operation           | Name            |Starts|E-Rows|A-Rows|A-Time|Buffers|
        ---------------------------------------------------------------------------------
        |  0| SELECT STATEMENT           |           |    1|     | 6 |00:00:00.02| 1523 |
        |* 1|  TABLE ACCESS INMEMORY FULL| CUSTOMERS |    1|    6| 6 |00:00:00.02| 1523 |
        ---------------------------------------------------------------------------------

        Predicate Information (identified by operation id):
        ---------------------------------------------------

           1 - inmemory(("CUST_CITY"='Hyderabad' AND "CUST_YEAR_OF_BIRTH">1960 AND
                      "CUST_INCOME_LEVEL" LIKE 'C%'))
               filter(("CUST_CITY"='Hyderabad' AND "CUST_YEAR_OF_BIRTH">1960 AND
                      "CUST_INCOME_LEVEL" LIKE 'C%'))

7.  Query `V$IM_SEGMENTS` again (sample output included):

        COL SEGMENT_NAME FORMAT a20

        SELECT SEGMENT_NAME, POPULATE_STATUS
        FROM   V$IM_SEGMENTS
        WHERE  SEGMENT_NAME = 'CUSTOMERS';

        SEGMENT_NAME         POPULATE_STATUS
        -------------------- ---------------
        CUSTOMERS            COMPLETED

    The value `COMPLETED` in `POPULATE_STATUS` means that the table is populated in the IM column store.

8.  The `DBA_FEATURE_USAGE_STATISTICS` view confirms that the database used the IM column store to retrieve the results:
        COL NAME FORMAT a25
        SELECT ul.NAME, ul.DETECTED_USAGES
        FROM   DBA_FEATURE_USAGE_STATISTICS ul
        WHERE  ul.VERSION= (SELECT MAX(u2.VERSION)
                            FROM   DBA_FEATURE_USAGE_STATISTICS u2
                            WHERE  u2.NAME = ul.NAME
                            AND    ul.NAME LIKE '%Column Store%');

        NAME                      DETECTED_USAGES
        ------------------------- ---------------
        In-Memory Column Store    1

**See Also:**

"Priority Options for the Population of In-Memory Objects"

[Oracle Database SQL Language Reference](../sqlrf/ALTER-TABLE.md) to learn about the `INMEMORY PRIORITY` clause

##### 4.1.2.2 How Background Processes Populate IMCUs

During population, the database reads data from disk in its row format, pivots the rows to create columns, and then compresses the data into In-Memory Compression Units (IMCUs).

Worker processes (Wnnn) populate the data in the IM column store. Each worker process operates on a subset of database blocks from the object. Population is a streaming mechanism, simultaneously compressing the data and converting it into columnar format.

The `INMEMORY_MAX_POPULATE_SERVERS` initialization parameter specifies the maximum number of worker processes to use for IM column store population. By default, the setting is one half of `CPU_COUNT`. Set this parameter to an appropriate value for your environment. More worker processes result in faster population, but they use more CPU resources. Fewer worker processes result in slower population, which reduces CPU overhead.

**Note:**

If `INMEMORY_MAX_POPULATE_SERVERS` is set to `0`, then population is disabled.

**See Also:**

[Oracle Database Reference](../refrn/INMEMORY_MAX_POPULATE_SERVERS.md) for more information about the `INMEMORY_MAX_POPULATE_SERVERS` initialization parameter

#### 4.1.3 Controls for In-Memory Objects

Use the `INMEMORY` clause in DDL statements to specify which objects are eligible for population into the IM column store. You can enable tablespaces, tables (internal and external), partitions, and materialized views.

This section contains the following topics:

##### 4.1.3.1 The INMEMORY Subclause

`INMEMORY` is a segment-level attribute, not a column-level attribute. However, you can apply the `INMEMORY` attribute to a subset of columns within a specific object.

To enable or disable an object for the IM column store, specify the `INMEMORY` clause in DDL statements for tablespaces, tables, and materialized views. The `INMEMORY` column in the `DBA_TABLES` view indicates which tables have the `INMEMORY` attribute set (`ENABLED`) or not set (`DISABLED`).

The following objects are not eligible for population in the IM column store:

- Indexes

- Index-organized tables

- Hash clusters

- Objects owned by the `SYS` user and stored in the `SYSTEM` or `SYSAUX` tablespace

###### 4.1.3.1.1 In-Memory Tables

To make heap-organized tables eligible for population, specify `INMEMORY` on the `CREATE TABLE` or `ALTER TABLE` statements.

By default, the IM column store populates all nonvirtual columns in the table. You can specify all or some columns of an internal table. For example, you might exclude the `weight_class` and `catalog_url` columns in `oe.product_information` from eligibility.

For a partitioned table, you can populate all or some partitions in the IM column store. By default, all partitions in a partitioned table inherit the `INMEMORY` attribute. For hybrid partitioned tables, which contain both internal and external partitions, only internal partitions inherit the `INMEMORY` attribute.

On Oracle Exadata Storage Server, the `CELLMEMORY` keyword (default) enables the flash cache to store data in the In-Memory format. You can use `ALTER TABLE` to choose `FOR QUERY` or `FOR CAPACITY` compression. Specifying `NO CELLMEMORY` disables columnar storage in the flash cache.

If you enable a table for the IM column store and it contains any of the following types of columns, then they will not be populated in the IM column store:

- Out-of-line columns (varrays, nested table columns, and out-of-line LOBs)

  **Note:**

  For inline LOB columns, the IM column store allocates up to 4 KB of contiguous buffer storage, and up to 32 KB when the inline LOBs contain OSON (binary JSON) data. For out-of-line LOBs, the IM column store allocates up to 40 bytes for the locator, but does not store the LOB itself.

- Columns that use the `LONG` or `LONG RAW` data types

- Extended data type columns

Example 4-2 Specifying a Table as INMEMORY

Assume that you are connected to the database as user `sh`. You enable the `customers` table for population in the IM column store, using the default compression level of `FOR QUERY LOW`:

    SQL> SELECT TABLE_NAME, INMEMORY FROM USER_TABLES WHERE TABLE_NAME = 'CUSTOMERS';

    TABLE_NAME INMEMORY
    ---------- --------
    CUSTOMERS  DISABLED

    SQL> ALTER TABLE customers INMEMORY;

    Table altered.

    SQL> SELECT TABLE_NAME, INMEMORY, INMEMORY_COMPRESSION FROM USER_TABLES WHERE TABLE_NAME='CUSTOMERS';

    TABLE_NAME INMEMORY INMEMORY_COMPRESS
    ---------- -------- -----------------
    CUSTOMERS  ENABLED  FOR QUERY LOW

**See Also:**

- "[In-Memory Compression](in-memory-column-store-architecture.md)"

- "[Enabling the IM Column Store for a Database](enabling-the-im-column-store.md)"

- [Oracle Exadata System Software User's Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/inmem&id=SAGUG-GUID-76E92D13-C65B-4B74-B92D-2AA01D923902) to learn more about `ALTER TABLE ... CELLMEMORY`

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md) for information about `INMEMORY` clause of the `CREATE TABLE` statement

###### 4.1.3.1.2 In-Memory External Tables

To make external tables eligible for population, specify the `EXTERNAL ... INMEMORY` clause in `CREATE TABLE` or `ALTER TABLE`.

##### Purpose of In-Memory External Tables

In-Memory external tables are useful in the following cases:

- Short-term data that must be scanned repeatedly in a short time span and does not require retention in Oracle Database

- External data that must be joined to relational data for fast analytic processing

- Data that is accessed by analytic queries in both Oracle Database and external tools, and which does not need to be materialized in database storage

##### Restrictions for In-Memory External Tables

The IM column store manages the data for external tables in the same way as for heap-organized tables. For example, a full table scan populates both internal tables and external tables into the IM column store. The same drivers supported for external tables are supported for In-Memory external tables. However, note the following differences:

- Some `INMEMORY` subclauses for external tables are not valid, including the column clause, distribute clause, and priority clause.

- In-Memory Optimized Arithmetic does not support external tables.

- Partitioning is not supported for In-Memory external tables. For hybrid partitioned tables, which contain both internal and external partitions, only internal partitions—not external partitions—support the `INMEMORY` attribute.

- Join groups are not supported for In-Memory external tables.

- IM expressions are not supported for In-Memory external tables.

- In-Memory external tables do not support the `DISTRIBUTE ... FOR SERVICE` clause for Oracle Active Data Guard instances.

**Note:**

Sessions that query In-Memory external tables must have the initialization parameter `QUERY_REWRITE_INTEGRITY` set to `stale_tolerated`.

It is important to keep in mind that if an external table is modified, then the results from the IM column store are undefined. Results are also undefined if a partition is altered (by dropping or adding values). This may lead to differences in results between IM and non-IM based scans. You can run `DBMS_INMEMORY.REPOPULATE` to refresh the IM store so that it is resynchronized with the table data.

**See Also:**

- "[Populating an In-Memory External Table Using DBMS_INMEMORY.POPULATE: Example](populating-the-imcs-manually.md)"

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md) for information about `INMEMORY` clause of the `CREATE TABLE ... EXTERNAL` statement

- [Oracle Database Licensing Information User Manual](../dblic/Licensing-Information.md) for details on which features are supported for different editions and services

###### 4.1.3.1.3 In-Memory Materialized Views

You can make materialized views eligible for population by specifying `INMEMORY` on the `CREATE MATERIALIZED VIEW` or `ALTER MATERIALIZED VIEW` statements.

For a partitioned materialized view, you can populate all or a subset of the partitions in the IM column store.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/ALTER-MATERIALIZED-VIEW.md) for `ALTER MATERIALIZED VIEW` syntax and semantics

###### 4.1.3.1.4 In-Memory Tablespaces

You can make permanent tablespaces eligible for population by specifying `INMEMORY` on the `CREATE TABLESPACE` or `ALTER TABLESPACE` statements.

By default, all tables and materialized views in the tablespace are enabled for the IM column store. Individual tables and materialized views in the tablespace may have different `INMEMORY` attributes. The attributes for individual database objects override the attributes for the tablespace.

**Note:**

Temporary tablespaces are not eligible for In-Memory population.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/ALTER-TABLESPACE.md) for `ALTER TABLESPACE` syntax and semantics

##### 4.1.3.2 Priority Options for the Population of In-Memory Objects

When you enable an object for the IM column store, you can either let Oracle Database control when the object is populated (default), or you can specify a level that determines the priority of the object in the population queue.

Oracle SQL includes an `INMEMORY PRIORITY` clause that provides more control over the queue for population. For example, it might be more important or less important to populate a database object's data before populating the data for other database objects.

**Video:**

The following table describes the supported priority levels.

Table 4-1 Priority Levels for Populating a Database Object in the IM Column Store

| CREATE/ALTER Syntax | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
|:--------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `PRIORITY NONE`     | The database populates the object on demand only. A full scan of the database object triggers the population of the object into the IM column store.<br>This is the default level when `PRIORITY` is not included in the `INMEMORY` clause.                                                                                                                                                                                                                                     |
| `PRIORITY LOW`      | The database assigns the object a low priority and populates it after startup based on its position in the queue. Population does not depend on whether the object is accessed.<br>The object is populated in the IM column store before database objects with the following priority level: `NONE`. The database object's data is populated in the IM column store after database objects with the following priority levels: `MEDIUM`, `HIGH`, or `CRITICAL`.                 |
| `PRIORITY MEDIUM`   | The database assigns the object a medium priority and populates it after startup based on its position in the queue. Population does not depend on whether the object is accessed.<br>The database object is populated in the IM column store before database objects with the following priority levels: `NONE` or `LOW`. The database object's data is populated in the IM column store after database objects with the following priority levels: `HIGH` or `CRITICAL`.      |
| `PRIORITY HIGH`     | The database assigns the object a high priority and populates it after startup based on its position in the queue. Population does not depend on whether the object is accessed.<br>The database object's data is populated in the IM column store before database objects with the following priority levels: `NONE`, `LOW`, or `MEDIUM`. The database object's data is populated in the IM column store after database objects with the following priority level: `CRITICAL`. |
| `PRIORITY CRITICAL` | The database assigns the object a low priority and populates it after startup based on its position in the queue. Population does not depend on whether the object is accessed.<br>The database object's data is populated in the IM column store before database objects with the following priority levels: `NONE`, `LOW`, `MEDIUM`, or `HIGH`.                                                                                                                               |

When more than one database object has a priority level other than `NONE`, Oracle Database queues the data for objects to be populated based on priority level. Database objects with the `CRITICAL` priority level are populated first; database objects with the `HIGH` priority level are populated next, and so on. If no space remains in the IM column store, then no additional objects are populated in it until space becomes available.

**Note:**

If you specify all objects as `CRITICAL`, then the database does not consider any object as more critical than any other.

When a database is restarted, all of the data for database objects with a priority level other than `NONE` are populated in the IM column store during startup. For a database object with a priority level other than `NONE`, an `ALTER` `TABLE` or `ALTER MATERIALIZED VIEW` DDL statement involving the database object does not return until the DDL changes are recorded in the IM column store.

**Note:**

- The priority level setting must apply to an entire table or to a table partition. Specifying different IM column store priority levels for different subsets of columns in a table is not permitted.

- If a segment on disk is 64 KB or less, then it is not populated in the IM column store. Therefore, some small database objects that were enabled for the IM column store might not be populated.

**See Also:**

- "Prioritization of In-Memory Population"

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md) for `CREATE TABLE ... INMEMORY PRIORITY` syntax and semantics

##### 4.1.3.3 IM Column Store Compression Methods

Depending on your requirement, you can compress In-Memory objects at different levels.

Typically, compression is a space-saving mechanism. However, the IM column store can compress data using a new set of algorithms that also improve query performance. If the columnar data is compressed using the `FOR DML` or `FOR QUERY` options, then SQL queries execute directly on the compressed data. Thus, scanning and filtering operations execute on a much smaller amount of data. The database only decompresses data when it is required for the result set.

**Video:**

The `V$IM_SEGMENTS` and `V$IM_COLUMN_LEVEL` views indicate the current compression level. You can change compression levels by using the appropriate `ALTER` command. If a table is currently populated in the IM column store, and if you change any `INMEMORY` attribute of the table other than `PRIORITY`, then the database evicts the table from the IM column store. The repopulation behavior depends on the `PRIORITY` setting.

The following table summarizes the data compression methods supported in the IM column store.

Table 4-2 IM Column Store Compression Methods

| CREATE/ALTER Syntax             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|:--------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `NO MEMCOMPRESS`                | The data is not compressed.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `MEMCOMPRESS FOR DML`           | This method results in the best DML performance.<br>This method compresses IM column store data the least, with the exception of `NO MEMCOMPRESS`.<br>**Note:**<br>This compression method is not supported for `CELLMEMORY` storage on Exadata flash cache.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `MEMCOMPRESS FOR QUERY LOW`     | This method results in the best query performance.<br>This method compresses IM column store data more than `MEMCOMPRESS FOR DML` but less than `MEMCOMPRESS FOR QUERY HIGH`.<br>This method is the default when the `INMEMORY` clause is specified without a compression method in a `CREATE` or `ALTER` SQL statement or when `MEMCOMPRESS FOR QUERY` is specified without including either `LOW` or `HIGH`.<br>Note: If the `INMEMORY_FORCE` initialization parameter is set to `BASE_LEVEL`, then `INMEMORY` objects and columns automatically use `QUERY LOW` compression. The data dictionary views may continue to show pre-existing compression settings, but the Base Level always transparently compresses objects and columns at the `QUERY LOW` level. |
| `MEMCOMPRESS FOR QUERY HIGH`    | This method results in good query performance, and saves space.<br>This method compresses IM column store data more than `MEMCOMPRESS FOR QUERY LOW` but less than `MEMCOMPRESS FOR CAPACITY LOW`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `MEMCOMPRESS FOR CAPACITY LOW`  | This method balances space saving and query performance, with a bias toward space saving.<br>This method compresses IM column store data more than `MEMCOMPRESS FOR QUERY HIGH` but less than `MEMCOMPRESS FOR CAPACITY HIGH`. This method applies a proprietary compression technique called Oracle Zip (OZIP) that offers extremely fast decompression that is tuned specifically for Oracle Database. That data must be decompressed before it can be scanned.<br>This method is the default when `MEMCOMPRESS FOR CAPACITY` is specified without including either `LOW` or `HIGH`.                                                                                                                                                                             |
| `MEMCOMPRESS FOR CAPACITY HIGH` | This method results in the best space saving.<br>This method compresses IM column store data the most.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |

In a SQL statement, the `MEMCOMPRESS` keyword must be preceded by the `INMEMORY` keyword.

**See Also:**

- "[About Repopulation of the IM Column Store](repopulation-and-dml.md)"

- [Oracle Exadata System Software User's Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/inmem&id=SAGUG-GUID-76E92D13-C65B-4B74-B92D-2AA01D923902) to learn more about `ALTER TABLE ... CELLMEMORY`

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md) for `CREATE TABLE ... INMEMORY PRIORITY` syntax and semantics

##### 4.1.3.4 Oracle Compression Advisor

Oracle Compression Advisor estimates the compression ratio that you can realize using the `MEMCOMPRESS` clause. The advisor uses the `DBMS_COMPRESSION` interface.

When you run `DBMS_COMPRESSION.GET_COMPRESSION_RATIO` for a table, Oracle Database analyzes a sample of the rows. For this reason, Oracle Compression Advisor provides a good estimate of the compression results that a table achieves after it is populated into the IM column store.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_COMPRESSION.md) to learn about `DBMS_COMPRESSION.GET_COMPRESSION_RATIO`

### 4.2 Enabling and Disabling Tables for the IM Column Store

Enable a table for the IM column store by including an `INMEMORY` clause in a `CREATE TABLE` or `ALTER TABLE` statement. Disable a table for the IM column store by including a `NO INMEMORY` clause in a `CREATE TABLE` or `ALTER TABLE` statement.

#### 4.2.1 Enabling New Tables for the In-Memory Column Store

You enable a new table for the IM column store by including an `INMEMORY` clause in a `CREATE TABLE` statement.

You can enable either internal or external tables for the IM column store. Some `INMEMORY` subclauses, including the columns and priority subclauses, are not valid for external tables.

##### Prerequisites

Ensure that the IM column store is enabled for the database. See "[Enabling the IM Column Store for a Database](enabling-the-im-column-store.md)".

##### To enable a new table for the IM column store:

1.  Log in to the database as a user with the necessary privileges to create the table.

2.  Run a `CREATE TABLE` statement with an `INMEMORY` clause.

**See Also:**

- "Enabling and Disabling Tables for the IM Column Store"

- "Enabling a Subset of Columns for the IM Column Store: Example"

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md) for information about `INMEMORY` clause of the `CREATE TABLE` statement

#### 4.2.2 Enabling and Disabling Existing Tables for the IM Column Store

Enable or disable an existing table for the IM column store by including an `INMEMORY` or `NO INMEMORY` clause in an `ALTER TABLE` statement.

##### Prerequisites

Ensure that the IM column store is enabled for the database. See "[Enabling the IM Column Store for a Database](enabling-the-im-column-store.md)".

##### To enable or disable an existing table for the IM column store:

1.  Log in to the database as a user with `ALTER TABLE` privileges.

2.  Run an `ALTER TABLE` statement with an `INMEMORY` clause or a `NO INMEMORY` clause.

3.  Optionally, to view metadata (size, priority, compression level) about the In-Memory segment, query `V$IM_SEGMENTS`.

**See Also:**

- "Enabling and Disabling Tables for the IM Column Store"

- "Enabling a Subset of Columns for the IM Column Store: Example"

- [Oracle Database SQL Language Reference](../sqlrf/ALTER-TABLE.md) for information about the `ALTER TABLE` statement

- [Oracle Database Reference](../refrn/V-IM_SEGMENTS.md) for information about the `V$IM_SEGMENTS` view

#### 4.2.3 Enabling and Disabling Tables for the IM Column Store

The following examples illustrate how to enable or disable tables for the IM column store.

##### 4.2.3.1 Creating an In-Memory Table: Example

This example creates the `test_inmem` table and enables it for the IM column store.

This example creates the test_inmem table and enables it for the IM column store. In SQL\*Plus, log in to the database as the user who will own the table, and then execute the following SQL statement:

    CREATE TABLE test_inmem ( id NUMBER(5) PRIMARY KEY, test_col VARCHAR2(15)) INMEMORY;

The preceding statement uses the defaults for the `INMEMORY` clause: `MEMCOMPRESS FOR QUERY` and `PRIORITY NONE`. Because `PRIORITY` is `NONE`, the database will not automatically populate the table.

You can prepopulate a new table by creating it with a CTAS (`CREATE TABLE AS SELECT`) statement and at the same time enable In-Memory on the new table with this statement, which pulls data from the sh sample schema provided by Oracle:

    CREATE TABLE test_inmem INMEMORY AS SELECT * FROM sh.sales;

You can also include `INMEMORY `subclauses:

    CREATE TABLE test_inmem INMEMORY MEMCOMPRESS for capacity high AS SELECT * FROM sh.sales;

Note that the following statement format is not correct. The `INMEMORY `clause and related subclauses must precede the `SELECT`. Here it it added after the `SELECT`:

    CREATE TABLE test_inmem AS SELECT * from sh.sales INMEMORY MEMCOMPRESS for capacity high;

In this incorrect usage, INMEMORY is interpreted as keyword, not a reserved word. It is silently ignored and INMEMORY remains disabled. Although `MEMCOMPRESS`, which is also interpreted as a keyword, raises an error.

##### 4.2.3.2 Creating a Table with In-Memory Partitions: Example

This example creates a partitioned table named `range_sales`, specifying a subset of the partitions as `INMEMORY`.

Log in to SQL\*Plus as the user that will own the new table, and then execute the following DDL statement:

    CREATE TABLE range_sales
        ( prod_id        NUMBER(6)
        , cust_id        NUMBER
        , time_id        DATE
        , channel_id     CHAR(1)
        , promo_id       NUMBER(6)
        , quantity_sold  NUMBER(3)
        , amount_sold    NUMBER(10,2)
        )
    PARTITION BY RANGE (time_id)
      (PARTITION SALES_Q4_1999
          VALUES LESS THAN (TO_DATE('01-JAN-2015','DD-MON-YYYY'))
          INMEMORY MEMCOMPRESS FOR DML,
       PARTITION SALES_Q1_2000
          VALUES LESS THAN (TO_DATE('01-APR-2015','DD-MON-YYYY'))
          INMEMORY MEMCOMPRESS FOR QUERY,
       PARTITION SALES_Q2_2000
          VALUES LESS THAN (TO_DATE('01-JUL-2015','DD-MON-YYYY'))
          INMEMORY MEMCOMPRESS FOR CAPACITY,
       PARTITION SALES_Q3_2000
          VALUES LESS THAN (TO_DATE('01-OCT-2015','DD-MON-YYYY'))
          NO INMEMORY,
       PARTITION SALES_Q4_2000
          VALUES LESS THAN (MAXVALUE));

The preceding SQL specifies a different compression level for the first three partitions in the IM column store. The last two partitions are not eligible for population in the IM column store.

##### 4.2.3.3 Creating an In-Memory External Table: Example

This example creates an external table with the `INMEMORY` option.

This example assumes that the host has the directories `/tmp/data/`, `/tmp/log/`, and `/tmp/bad/`.

The following SQL script creates the comma-delimited flat file `/tmp/data/sh_sales.csv` from the `sh.sales` table. Execute the script as user `sh`.

    SET HEAD OFF
    SET TRIMSPOOL ON
    SET PAGES 0
    SET FEEDBACK OFF
    SET TERMOUT OFF
    SPOOL /tmp/data/sh_sales.csv
    SELECT prod_id       || ',' || cust_id  || ',' || time_id || ',' ||
           channel_id    || ',' || promo_id || ',' ||
           quantity_sold || ',' || amount_sold
    FROM   sales;
    SPOOL OFF

Using the `sh_sales.csv` file, the following SQL script creates the external table `sh.admin_ext_sales` with the `INMEMORY` option:

    CONNECT  /  AS SYSDBA;
    -- Set up directories and grant access to sh
    CREATE OR REPLACE DIRECTORY admin_dat_dir
        AS '/tmp/data';
    CREATE OR REPLACE DIRECTORY admin_log_dir
        AS '/tmp/log';
    CREATE OR REPLACE DIRECTORY admin_bad_dir
        AS '/tmp/bad';
    GRANT READ ON DIRECTORY admin_dat_dir TO sh;
    GRANT WRITE ON DIRECTORY admin_log_dir TO sh;
    GRANT WRITE ON DIRECTORY admin_bad_dir TO sh;
    -- sh connects. Provide the user password (sh) when prompted.
    CONNECT sh
    -- create the external table
    DROP TABLE admin_ext_sales;
    CREATE TABLE admin_ext_sales
         (  prod_id           NUMBER,
            cust_id           NUMBER,
            time_id           DATE,
            channel_id        NUMBER,
            promo_id          NUMBER,
            quantity_sold     NUMBER(10,2),
            amount_sold       NUMBER(10,2)
         )
         ORGANIZATION EXTERNAL
         ( TYPE ORACLE_LOADER
           DEFAULT DIRECTORY admin_dat_dir
           ACCESS PARAMETERS
           ( records delimited by newline
             badfile admin_bad_dir:'empxt%a_%p.bad'
             logfile admin_log_dir:'empxt%a_%p.log'
             fields terminated by ','
             missing field values are null
             ( prod_id, cust_id,
               time_id char date_format date mask "dd-mon-yy",
               channel_id, promo_id, quantity_sold, amount_sold
             )
           )
           LOCATION ('sh_sales.csv')
         )
         REJECT LIMIT UNLIMITED
         INMEMORY;

The following query of `ALL_EXTERNAL_TABLES` shows that the `admin_ext_sales` table is enabled for `INMEMORY`:

    COL OWNER FORMAT A10
    COL TABLE_NAME FORMAT A15

    SELECT OWNER, TABLE_NAME,
           INMEMORY, INMEMORY_COMPRESSION
    FROM   ALL_EXTERNAL_TABLES
    WHERE  TABLE_NAME = 'ADMIN_EXT_SALES';

    OWNER      TABLE_NAME      INMEMORY INMEMORY_COMPRESS
    ---------- --------------- -------- -----------------
    SH         ADMIN_EXT_SALES ENABLED  FOR QUERY LOW

Related views include `ALL_XTERNAL_PART_TABLES`, `ALL_XTERNAL_TAB_PARTITIONS`, and `ALL_XTERNAL_TAB_SUBPARTITIONS`.

**See Also:**

- "[Populating an In-Memory External Table Using DBMS_INMEMORY.POPULATE: Example](populating-the-imcs-manually.md)"

- [Oracle Database Reference](../refrn/QUERY_REWRITE_INTEGRITY.md) to learn about `ALL_EXTERNAL_TABLES` and the related external table views

##### 4.2.3.4 Creating and Populating a Hybrid External Table: Example

This example creates a hybrid external table with the `INMEMORY` option, and then populates both the internal and external partitions.

This example assumes the existence of the `sh.sales` table. The goal is to create a hybrid partitioned table `sales_hpt` with two internal partitions, one of which uses the data from `sh.sales`, and then add one external partition. When you apply the `INMEMORY` attribute to `sales_hpt`, this attribute applies to all partitions.

1.  In Linux, create a temporary directory, and then create a text file with one row of sales data.

        rm -rf /tmp/sales_data
        mkdir /tmp/sales_data
        echo "1002,110,19-MAR-2016,12,18,150,4800" > /tmp/sales_data/sales2016_data.txt

2.  In SQL\*Plus, log is with administrator privileges, and then create a directory object for the sales data:

        CONNECT / AS SYSDBA
        CREATE DIRECTORY sales_data AS '/tmp/sales_data';
        GRANT READ,WRITE ON DIRECTORY sales_data TO sh;

3.  Log in as user `sh`, and then create the `sales_hpt` table:

        CONNECT sh

        DROP TABLE sales_hpt;
        CREATE TABLE sales_hpt
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
            (
             PARTITION sales_2014 VALUES LESS THAN (TO_DATE('01-01-2015','dd-mm-yyyy')),
             PARTITION sales_2015 VALUES LESS THAN (TO_DATE('01-01-2016','dd-mm-yyyy')),
             PARTITION sales_2016 VALUES LESS THAN (TO_DATE('01-01-2017','dd-mm-yyyy'))
               EXTERNAL LOCATION ('sales2016_data.txt')
        );

    The preceding statement shows that the table has three partitions: `sales_2014`, `sales_2015`, and `sales_2016`. Only `sales_2016` is designated as external.

4.  Query the data dictionary to confirm that the table is a hybrid (sample output included):

        COL TABLE_NAME FORMAT a25
        SELECT TABLE_NAME, HYBRID FROM USER_TABLES WHERE HYBRID = 'YES';

        TABLE_NAME                HYB
        ------------------------- ---
        SALES_HPT                 YES

5.  Insert rows into the internal partitions `sales_2014` and `sales_2015`:

        INSERT INTO sh.sales_hpt (SELECT * FROM sales);
        INSERT INTO sh.sales_hpt
          VALUES (30, 21086, TO_DATE('2015-12-30','SYYYY-MM-DD'), 2, 999, 1, 10.19);
        COMMIT;

    The first of the preceding statements inserts all rows from the `sales` table. All dates in `sales` are before 2002, so all rows from `sales` are inserted into the `sales_2014` partition. The second statement inserts a single row into the `sales_2015` partition.

6.  Query the partitions to confirm that the correct data exists:

        SQL> SELECT COUNT(*) FROM sales_hpt PARTITION(sales_2014);

          COUNT(*)
        ----------
            918843

        SQL> SELECT COUNT(*) FROM sales_hpt PARTITION(sales_2015);

          COUNT(*)
        ----------
                 1

        SQL> SELECT COUNT(*) FROM sales_hpt PARTITION(sales_2016);

          COUNT(*)
        ----------
                 1

7.  Apply the `INMEMORY` attribute at the table level, and then force the database to populate the table into the IM column store:

        ALTER TABLE sales_hpt INMEMORY;
        EXEC DBMS_INMEMORY.POPULATE('SH', 'SALES_HPT');

8.  Query the population status of the `sales_hpt` partitions:

        COL OWNER FORMAT a3
        COL SEGMENT FORMAT a18
        COL PARTITION FORMAT a13
        COL STATUS FORMAT a9
        COL BNP FORMAT 99999

        SELECT OWNER, SEGMENT_NAME SEGMENT, PARTITION_NAME PARTITION,
               IS_EXTERNAL AS EXT, POPULATE_STATUS STATUS,
               BYTES_NOT_POPULATED AS "BNP"
        FROM   V$IM_SEGMENTS
        WHERE  SEGMENT_NAME = 'SALES_HPT'
        ORDER BY PARTITION;

        OWN SEGMENT            PARTITION     EXT   STATUS       BNP
        --- ------------------ ------------- ----- --------- ------
        SH  SALES_HPT          SALES_2014    FALSE COMPLETED      0
        SH  SALES_HPT          SALES_2015    FALSE COMPLETED      0
        SH  SALES_HPT          SALES_2016    TRUE  COMPLETED      0

    The query shows that all partitions, both internal and external, were populated.

##### 4.2.3.5 Enabling an Existing Table for the IM Column Store: Example

This example enables the existing `sh.sales` table for the IM column store.

In SQL\*Plus, log in to the database as the `sh` user, and then execute the following DDL statement:

    ALTER TABLE sales INMEMORY;

The preceding statement uses the defaults for the `INMEMORY` clause: `MEMCOMPRESS FOR QUERY` and `PRIORITY NONE`.

##### 4.2.3.6 Setting In-Memory Compression to FOR CAPACITY LOW: Example

This example enables the existing `oe.product_information` table for the IM column store and specifies the compression method `FOR CAPACITY LOW`.

In SQL\*Plus, log in to the database as the `oe` user, and then execute the following DDL statement:

    ALTER TABLE product_information
      INMEMORY
      MEMCOMPRESS FOR CAPACITY LOW;

The preceding statement uses the default for the `PRIORITY` clause of `NONE`. Populate the table by forcing a full table scan as follows (sample output included):

    SELECT /*+ FULL(p) NO_PARALLEL(p) */ COUNT(*)
    FROM   product_information p;

      COUNT(*)
    ----------
           288

In a separate session, log in as a user with administrative privileges, and then calculate the compression ratio by executing the following query (sample output included):

    COL OWNER FORMAT a5
    COL SEGMENT_NAME FORMAT a19
    SET PAGESIZE 50000

    SELECT OWNER, SEGMENT_NAME, BYTES ORIG_SIZE,
           INMEMORY_SIZE IN_MEM_SIZE,
           ROUND (BYTES / INMEMORY_SIZE, 2) COMP_RATIO
    FROM   V$IM_SEGMENTS
    WHERE  SEGMENT_NAME LIKE 'P%'
    ORDER BY 4;

    OWNER SEGMENT_NAME         ORIG_SIZE IN_MEM_SIZE COMP_RATIO
    ----- ------------------- ---------- ----------- ----------
    OE    PRODUCT_INFORMATION      98304     1310720        .08

##### 4.2.3.7 Setting In-Memory Priority to HIGH: Example

This example enables the `oe.product_information` table for the IM column store and specifies `PRIORITY HIGH` for populating the table data in the IM column store.

In SQL\*Plus, log in to the database as the `oe` user, and then execute the following DDL statement:

    ALTER TABLE
      product_information
      INMEMORY
      PRIORITY HIGH;

##### 4.2.3.8 Changing the Compression and Priority Settings for an In-Memory Table: Example

This example alters the `oe.product_information` table to use `FOR CAPACITY HIGH` table compression and a `LOW` priority setting.

In SQL\*Plus, log in to the database as an administrative user, and then execute the following query to show the current priority and compression setting for the `oe.product_information` table:

    COL OWNER FORMAT a5
    COL SEGMENT_NAME FORMAT a19
    SET PAGESIZE 50000

    SELECT v.OWNER, v.SEGMENT_NAME, v.INMEMORY_PRIORITY,
           v.INMEMORY_COMPRESSION
    FROM   V$IM_SEGMENTS v
    WHERE  SEGMENT_NAME LIKE 'P%';

    OWNER SEGMENT_NAME        INMEMORY INMEMORY_COMPRESS
    ----- ------------------- -------- -----------------
    OE    PRODUCT_INFORMATION HIGH     FOR CAPACITY LOW

The following DDL statement alters `oe.product_information` to use `FOR CAPACITY HIGH` table compression and `PRIORITY LOW`:

    ALTER TABLE oe.product_information
      INMEMORY
      MEMCOMPRESS FOR CAPACITY HIGH
      PRIORITY LOW;

##### 4.2.3.9 Disabling a Table for the IM Column Store: Example

To disable a table for the IM column store, specify the `NO INMEMORY` clause.

Log in to the database as the user `oe`, and then execute the following statement to disable the `product_information` table for the IM column store:

    ALTER TABLE oe.product_information NO INMEMORY;

The `V$IM_SEGMENTS` view lists the database objects that are populated in the IM column store.

##### 4.2.3.10 Disabling Columnar Format on Exadata Smart Flash Cache: Example

This example disables the columnar format for `oe.product_information` on Exadata Smart Flash Cache storage.

By default, Exadata Smart Flash Cache compresses data using the level `MEMCOMPRESS FOR CAPACITY LOW`. To change the compression level or disable the columnar format altogether, use the `ALTER TABLE ... NO CELLMEMORY` statement.

Log in to the database as user `oe`, and execute the following DDL statement:

    ALTER TABLE product_information NO CELLMEMORY;

### 4.3 Enabling and Disabling Columns for In-Memory Tables

You can specify the `INMEMORY` clause for individual columns in an internal table. External tables do not support specifying `INMEMORY` at the column level.

#### 4.3.1 About Enabling INMEMORY Columns

For internal tables, both In-Memory virtual columns (IM virtual columns) and nonvirtual columns are eligible for IM population. For external tables, only nonvirtual columns are eligible.

##### NO INMEMORY Columns in INMEMORY Objects

**Note:**

Excluded columns can be specified at the table level only. You cannot specify them for partitions or sub-partitions

By default, if an internal object has the `INMEMORY` attribute, then all columns in this object are eligible for population into the IM column store. However, you can specify that some columns in an `INMEMORY` table should have the `NO INMEMORY` attribute, in which case only the `INMEMORY` columns are eligible for population.

To apply the `INMEMORY` attribute to a subset of columns, specify `ALTER TABLE ``table_name`` INMEMORY ... NO INMEMORY ``excluded_columns`, where excluded_columns lists the columns to be specified as `NO INMEMORY`. Only the columns that are not specified as `NO INMEMORY`, that is, the columns that are not in the excluded columns list, inherit the segment-level `INMEMORY` attribute.

Specifying `NO INMEMORY` columns in an `INMEMORY` table has an important consequence. A query that references a `NO INMEMORY` column uses the row store exclusively. For example, if `sales` is an `INMEMORY` table with 7 columns, and if only the `promo_id` column has the `NO INMEMORY` attribute, then any query whose `SELECT` list includes `promo_id` retrieves data from the row store rather than the IM column store. Likewise, any query whose predicate references `promo_id`, regardless of whether `promo_id` is in the `SELECT` list, retrieves data exclusively from the row store.

##### Virtual Columns

An IM virtual column is like any other column, except that its value is derived by evaluating an expression. Storing the precalculated IM virtual column values in the IM column store can improve query performance. The expression can include columns from the same table, constants, SQL functions, and user-defined PL/SQL functions (`DETERMINISTIC` only). You cannot explicitly write to an IM virtual column.

**Note:**

A virtual column or [IM expression](glossary.md) counts toward the limit of 1000 columns per populated object.

To populate IM virtual columns in the IM column store, set the `INMEMORY_VIRTUAL_COLUMNS` initialization parameter to one of the following values:

- `MANUAL` (default): If a table is enabled for the IM column store, then no IM virtual columns defined on this table are eligible for population, unless they are explicitly set as `INMEMORY`.

- `ENABLE`: If a table is enabled for the IM column store, then all IM virtual columns defined on this table are eligible for population, unless they are explicitly set as `NO INMEMORY`.

  By default, the compression level of the column in the IM column store is the same as the table or partition in which it is stored. However, when a different compression level is specified for the IM virtual column, it is populated at the specified compression level.

To specify that no IM virtual columns are populated in the IM column store, set this initialization parameter to `DISABLE`.

The underlying storage structures for IM virtual columns and IM expressions are the same. However, different mechanisms control IM expressions and IM virtual columns.

**Note:**

- The IM column store only populates virtual columns for tables marked `INMEMORY`.

- To populate IM virtual columns in the IM column store, the value for the initialization parameter `COMPATIBLE` must be set to 12.1.0 or higher.

**See Also:**

- "Enabling and Disabling Tables for the IM Column Store"

- "[IM Expressions Infrastructure](optimizing-in-memory-expressions.md)"

- "[In-Memory Initialization Parameters](init-parameters-for-im-column-store.md)"

- [Oracle Database SQL Language Reference](../sqlrf/Expressions.md) for the syntax and semantics of the `INMEMORY` clause

- <https://blogs.oracle.com/in-memory/what-happens-if-a-column-is-not-populated> for a blog entry on accessing columns that are not populated

#### 4.3.2 Enabling IM Virtual Columns

IM virtual columns improve query performance by avoiding repeated calculations. Also, the database can scan and filter IM virtual columns using techniques such as SIMD vector processing.

##### Prerequisites

To enable IM virtual columns, the following conditions must be true:

- The IM column store is enabled for the database.

  See "[Enabling the IM Column Store for a Database](enabling-the-im-column-store.md)".

- The table that contains the virtual columns is internal and has the `INMEMORY` attribute.

  See "Enabling and Disabling Tables for the IM Column Store".

- The `INMEMORY_VIRTUAL_COLUMNS` initialization parameter is not set to `DISABLE`.

- The value for the initialization parameter `COMPATIBLE` is set to `12.1.0` or higher.

##### To enable IM virtual columns:

1.  In SQL\*Plus or SQL Developer, log in to the database as a user with the necessary privileges.

2.  Either set the `INMEMORY_VIRTUAL_COLUMNS` initialization parameter to `ENABLE`, or enable specific virtual columns for the IM column store.

Example 4-3 Enabling Virtual Columns for the IM Column Store

In this example, you are logged in to the database as `SYSTEM`. The IM column store is enabled, but population of virtual columns is currently disabled:

    SQL> SHOW PARAMETER INMEMORY_SIZE

    NAME                                 TYPE        VALUE
    ------------------------------------ ----------- -----
    inmemory_size                        big integer 200M

    SQL> SHOW PARAMETER INMEMORY_VIRTUAL_COLUMNS

    NAME                                 TYPE        VALUE
    ------------------------------------ ----------- -------
    inmemory_virtual_columns             string      DISABLE

You add a virtual column to the `hr.employees` table, and then specify that the table is `INMEMORY`:

    SQL> ALTER TABLE hr.employees ADD (weekly_sal AS (ROUND(salary*12/52,2)));

    Table altered.

    SQL> ALTER TABLE hr.employees INMEMORY;

    Table altered.

At this stage, `weekly_sal` is not eligible for population, although the non-virtual columns in `hr.employees` are eligible for population. The following statement enables `weekly_sal`, and any other virtual columns in `hr.employees`, to be populated:

    SQL> ALTER SYSTEM SET INMEMORY_VIRTUAL_COLUMNS=ENABLE SCOPE=BOTH;

    System altered.

Note that you could also use `SCOPE=SPFILE`, but in that case the change will not take effect until the next database restart. When `SCOPE=BOTH` is used, the alteration takes place immediately and a restart is not required.

Example 4-4 Enabling a Specific IM Virtual Column for the IM Column Store

This example assumes that the `INMEMORY_VIRTUAL_COLUMNS` initialization parameter is set to `MANUAL`, which means that IM virtual columns must be added to the IM column store explicitly. This example first creates the `hr.admin_emp` table:

    CREATE TABLE hr.admin_emp (
          empno      NUMBER(5) PRIMARY KEY,
          ename      VARCHAR2(15) NOT NULL,
          job        VARCHAR2(10),
          sal        NUMBER(7,2),
          hrly_rate  NUMBER(7,2) GENERATED ALWAYS AS (sal/2080),
          deptno     NUMBER(3) NOT NULL)
       INMEMORY;

At this stage, the `hrly_rate` virtual column is not eligible for population. The following statement explicitly specifies the virtual column as `INMEMORY`:

    ALTER TABLE hr.admin_emp INMEMORY(hrly_rate);

#### 4.3.3 Enabling a Subset of Columns for the IM Column Store: Example

This example enables all columns in the `oe.product_information` table for the IM column store except `weight_class` and `catalog_url`.

The following statement also specifies different IM column store compression methods for the columns enabled for the IM column store:

    ALTER TABLE oe.product_information
       INMEMORY MEMCOMPRESS FOR QUERY (
          product_id, product_name, category_id, supplier_id, min_price)
       INMEMORY MEMCOMPRESS FOR CAPACITY HIGH (
          product_description, warranty_period, product_status, list_price)
       NO INMEMORY (
          weight_class, catalog_url);

Note the following:

- The columns `product_id`, `product_name`, `category_id`, `supplier_id`, and `min_price` are enabled for the IM column store with the `MEMCOMPRESS FOR QUERY` compression method.

- The columns `product_description`, `warranty_period`, `product_status`, and `list_price` are enabled for the IM column store with the `MEMCOMPRESS FOR CAPACITY HIGH` compression method.

- The `weight_class` and `catalog_url` columns are not enabled for the IM column store. Consequently, any query that references these two columns, either in the `SELECT` list or in the predicate, must use the row store rather than the IM column store.

- The table uses the default for the `PRIORITY` clause, which is `PRIORITY NONE`.

**Note:**

The priority level setting must apply to an entire table or partition. Specifying different IM column store priority levels for different subsets of columns in a table is not allowed.

To determine the selective column compression levels defined for a database object, query the `V$IM_COLUMN_LEVEL` view, as shown in the following example:

    COL TABLE_NAME FORMAT a20
    COL COLUMN_NAME FORMAT a20

    SELECT TABLE_NAME, COLUMN_NAME, INMEMORY_COMPRESSION
    FROM   V$IM_COLUMN_LEVEL
    WHERE  TABLE_NAME = 'PRODUCT_INFORMATION'
    ORDER BY COLUMN_NAME;

    TABLE_NAME           COLUMN_NAME          INMEMORY_COMPRESSION
    -------------------- -------------------- --------------------------
    PRODUCT_INFORMATION  CATALOG_URL          NO INMEMORY
    PRODUCT_INFORMATION  CATEGORY_ID          FOR QUERY LOW
    PRODUCT_INFORMATION  LIST_PRICE           FOR CAPACITY HIGH
    PRODUCT_INFORMATION  MIN_PRICE            FOR QUERY LOW
    PRODUCT_INFORMATION  PRODUCT_DESCRIPTION  FOR CAPACITY HIGH
    PRODUCT_INFORMATION  PRODUCT_ID           FOR QUERY LOW
    PRODUCT_INFORMATION  PRODUCT_NAME         FOR QUERY LOW
    PRODUCT_INFORMATION  PRODUCT_STATUS       FOR CAPACITY HIGH
    PRODUCT_INFORMATION  SUPPLIER_ID          FOR QUERY LOW
    PRODUCT_INFORMATION  WARRANTY_PERIOD      FOR CAPACITY HIGH
    PRODUCT_INFORMATION  WEIGHT_CLASS         NO INMEMORY

**See Also:**

- "[In-Memory Compression](in-memory-column-store-architecture.md)"

- [Oracle Database Reference](../refrn/V-IM_COLUMN_LEVEL.md) for more information about the `V$IM_COLUMN_LEVEL` view

#### 4.3.4 Specifying INMEMORY Column Attributes on a NO INMEMORY Table: Example

Starting in Oracle Database 12c Release 2 (12.2), you can specify the `INMEMORY` clause at the column level on an object that is not yet specified as `INMEMORY`.

In previous releases, the column-level `INMEMORY` clause was only valid when specified on an `INMEMORY` table or partition. This restriction meant that a column could not be associated with an `INMEMORY` clause before the table or partition was associated with an `INMEMORY` clause.

Starting in Oracle Database 12c Release 2 (12.2), if you specify the `INMEMORY` clause at the column level, then the database records the attributes of the specified column. If the table is `NO INMEMORY` (default), then the column-level attributes do not affect how the table is queried until the table or partition is specified as `INMEMORY`. If you mark the table itself as `NO INMEMORY`, then the database drops any existing column-level attributes.

In this example, your goal is to ensure that column `c3` in a partitioned table is never populated in the IM column store. You perform the following steps:

1.  Create a partitioned table `t` as follows:

        CREATE TABLE t (c1 NUMBER, c2 NUMBER, c3 NUMBER)
          NO INMEMORY -- this clause specifies the table itself as NO INMEMORY
          PARTITION BY LIST (c1)
            ( PARTITION p1 VALUES (0),
              PARTITION p2 VALUES (1),
              PARTITION p3 VALUES (2) );

    Table `t` is `NO INMEMORY`. The table is partitioned by list on column `c1`, and has three partitions: `p1`, `p2`, and `p3`.

2.  Query the compression of the columns in the table (sample output included):

        COL TABLE_NAME FORMAT a20
        COL COLUMN_NAME FORMAT a20

        SELECT TABLE_NAME, COLUMN_NAME, INMEMORY_COMPRESSION
        FROM   V$IM_COLUMN_LEVEL
        WHERE  TABLE_NAME = 'T'
        ORDER BY COLUMN_NAME;

        no rows selected

    As shown by the output, no column-level `INMEMORY` attributes are set.

3.  To ensure that column `c3` is never populated, apply the `NO INMEMORY` attribute to column `c3`:

        ALTER TABLE t NO INMEMORY (c3);

4.  Query the compression of the columns in the table (sample output included):

        SELECT TABLE_NAME, COLUMN_NAME, INMEMORY_COMPRESSION
        FROM   V$IM_COLUMN_LEVEL
        WHERE  TABLE_NAME = 'T'
        ORDER BY COLUMN_NAME;

        TABLE_NAME           COLUMN_NAME          INMEMORY_COMPRESSION
        -------------------- -------------------- --------------------
        T                    C1                   DEFAULT
        T                    C2                   DEFAULT
        T                    C3                   NO INMEMORY

    The database has recorded the `NO INMEMORY` attribute for `c3`. The other columns use the default compression.

5.  Specify partition `p3` as `INMEMORY`:

        ALTER TABLE t
          MODIFY PARTITION p3
            INMEMORY PRIORITY CRITICAL;

    Because column `c3` was previously specified as `NO INMEMORY`, initial population of partition `p3` will not include column `c3`.

6.  Specify the entire table as `INMEMORY`:

        ALTER TABLE t INMEMORY;

7.  Query the compression of the columns in the table (sample output included):

        SELECT TABLE_NAME, COLUMN_NAME, INMEMORY_COMPRESSION
        FROM   V$IM_COLUMN_LEVEL
        WHERE  TABLE_NAME = 'T'
        ORDER BY COLUMN_NAME;

        TABLE_NAME           COLUMN_NAME          INMEMORY_COMPRESSION
        -------------------- -------------------- --------------------------
        T                    C1                   DEFAULT
        T                    C2                   DEFAULT
        T                    C3                   NO INMEMORY

    The database has retained the `NO INMEMORY` setting for column `c3`. The other columns use the default compression.

8.  Apply different compression levels to columns `c1` and `c2`:

        ALTER TABLE t
          INMEMORY MEMCOMPRESS FOR CAPACITY HIGH (c1)
          INMEMORY MEMCOMPRESS FOR CAPACITY LOW (c2);

9.  Query the compression of the columns in the table (sample output included):

        SELECT TABLE_NAME, COLUMN_NAME, INMEMORY_COMPRESSION
        FROM   V$IM_COLUMN_LEVEL
        WHERE  TABLE_NAME = 'T'
        ORDER BY COLUMN_NAME;

        TABLE_NAME           COLUMN_NAME          INMEMORY_COMPRESSION
        -------------------- -------------------- --------------------------
        T                    C1                   FOR CAPACITY HIGH
        T                    C2                   FOR CAPACITY LOW
        T                    C3                   NO INMEMORY

    Each column now has a different compression level.

10. Specify the entire table as `NO INMEMORY`:

        ALTER TABLE t NO INMEMORY;

11. Query the compression of the columns in the table (sample output included):

        SELECT TABLE_NAME, COLUMN_NAME, INMEMORY_COMPRESSION
        FROM   V$IM_COLUMN_LEVEL
        WHERE  TABLE_NAME = 'T'
        ORDER BY COLUMN_NAME;

        no rows selected

    Because the entire table was specified as `NO INMEMORY`, the database dropped all column-level `INMEMORY` attributes.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/ALTER-TABLE.md) for `ALTER TABLE` syntax and semantics

### 4.4 Enabling and Disabling Tablespaces for the IM Column Store

You can enable or disable tablespaces for the IM column store.

Enable a tablespace for the IM column store during tablespace creation with a `CREATE TABLESPACE` statement that includes the `INMEMORY` clause. You can also alter a tablespace to enable it for the IM column store with an `ALTER TABLESPACE` statement that includes the `INMEMORY` clause.

Disable a tablespace for the IM column store by including a `NO INMEMORY` clause in a `CREATE TABLESPACE` or `ALTER TABLESPACE` statement.

When a tablespace is enabled for the IM column store, all tables and materialized views in the tablespace are enabled for the IM column store by default. The `INMEMORY` clause is the same for tables, materialized views, and tablespaces. The `DEFAULT` storage clause is required before the `INMEMORY` clause when enabling a tablespace for the IM column store and before the `NO INMEMORY` clause when disabling a tablespace for the IM column store.

When a tablespace is enabled for the IM column store, individual tables and materialized views in the tablespace can have different in-memory settings, and the settings for individual database objects override the settings for the tablespace. For example, if the tablespace is set to `PRIORITY LOW` for populating data in memory, and if a table in the tablespace is set to `PRIORITY HIGH`, then the table uses `PRIORITY HIGH`.

#### Prerequisites

Ensure that the IM column store is enabled for the database. See "[Enabling the IM Column Store for a Database](enabling-the-im-column-store.md)".

#### To enable or disable tablespaces for the IM column store:

1.  In SQL\*Plus or SQL Developer, log in to the database as a user with the necessary privileges.

2.  Run a `CREATE TABLESPACE` or `ALTER TABLESPACE` statement with an `INMEMORY` clause or a `NO INMEMORY` clause.

Example 4-5 Creating a Tablespace and Enabling It for the IM Column Store

The following example creates the `users01` tablespace and enables it for the IM column store:

    CREATE TABLESPACE users01
       DATAFILE 'users01.dbf' SIZE 40M
       ONLINE
       DEFAULT INMEMORY;

This example uses the defaults for the `INMEMORY` clause. Therefore, `MEMCOMPRESS FOR QUERY` is used, and `PRIORITY NONE` is used.

Example 4-6 Altering a Tablespace to Enable It for the IM Column Store

The following example alters the `users01` tablespace to enable it for the IM column store and specifies `FOR CAPACITY HIGH` compression for the database objects in the tablespace and `PRIORITY LOW` for populating data in memory:

    ALTER TABLESPACE users01 DEFAULT INMEMORY
       MEMCOMPRESS FOR CAPACITY HIGH
       PRIORITY LOW;

### 4.5 Enabling and Disabling Materialized Views for the IM Column Store

You can enable and disable materialized views for the IM column store.

Enable a materialized view for the IM column store by including an `INMEMORY` clause in a `CREATE MATERIALIZED VIEW` or `ALTER MATERIALIZED VIEW` statement. Disable a materialized view for the IM column store by including a `NO INMEMORY` clause in a `CREATE MATERIALIZED VIEW` or `ALTER MATERIALIZED VIEW` statement.

#### Prerequisites

Ensure that the IM column store is enabled for the database. See "[Enabling the IM Column Store for a Database](enabling-the-im-column-store.md)".

#### To enable or disable a materialized view for the IM column store:

1.  In SQL\*Plus or SQL Developer, log in to the database as a user with the necessary privileges.

2.  Run a `CREATE MATERIALIZED VIEW` or `ALTER MATERIALIZED VIEW` statement with either an `INMEMORY` clause or a `NO INMEMORY` clause.

Example 4-7 Creating a Materialized View and Enabling It for the IM Column Store

The following statement creates the `oe.prod_info_mv` materialized view and enables it for the IM column store:

    CREATE MATERIALIZED VIEW oe.prod_info_mv INMEMORY
      AS SELECT * FROM oe.product_information;

This example uses the defaults for the `INMEMORY` clause: `MEMCOMPRESS FOR QUERY LOW` and `PRIORITY` `NONE`.

Example 4-8 Enabling a Materialized View for the IM Column Store with HIGH Data Population Priority

The following statement enables the `oe.prod_info_mv` materialized view for the IM column store:

    ALTER MATERIALIZED VIEW oe.prod_info_mv INMEMORY PRIORITY HIGH;

This example uses the default compression: `MEMCOMPRESS FOR QUERY LOW`.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/CREATE-MATERIALIZED-VIEW.md) to learn more about the `CREATE` or `ALTER MATERIALIZED VIEW` statements
