The database does not automatically populate In-Memory objects whose `PRIORITY` setting is `NONE`. To populate these objects, you must execute SQL or PL/SQL.

This chapter contains the following topics:

### 5.1 About Manual Population of In-Memory Objects

Populate objects manually using either a full table scan, `DBMS_INMEMORY` program units, or `DBMS_INMEMORY_ADMIN.POPULATE_WAIT`.

If you enabled an object with `PRIORITY` set to `NONE`, and if you want to populate it immediately, then you have the options described in the following sections:

#### 5.1.1 Population Using SELECT

You can initiate population by issuing a `SELECT` statement that forces a full table scan.

In this case, the database reads each row in the object and converts it to columnar format. Note that the following statement does not guarantee a full table scan:

    SELECT COUNT(*) FROM object

The reason is that the optimizer may choose to scan an index. Therefore, Oracle recommends forcing a full table scan by using the `FULL` hint for `SELECT COUNT(*)` queries, as in the following example:

    SELECT /*+ FULL(customers) NO_PARALLEL(customers) */ COUNT(*) FROM customers;

**See Also:**

- "Populating an In-Memory Table Using a Full Table Scan: Example"

- [Oracle Database SQL Language Reference](../sqlrf/Comments.md) to learn more about the `FULL` hint

#### 5.1.2 Population Using DBMS_INMEMORY.POPULATE

The `DBMS_INMEMORY.POPULATE` procedure achieves the same goal as a full scan.

The database reads every row in the specified object, converts it from row format to columnar format, and then populates it in the IM column store. The following PL/SQL block initiates population of the `customer` table:

    BEGIN
      DBMS_INMEMORY.POPULATE( schema_name => 'SH', table_name => 'CUSTOMERS');
    END;
    /

**See Also:**

- "Populating a Table Using the POPULATE Procedure: Example"

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_INMEMORY.md) to learn about the `DBMS_INMEMORY` package

#### 5.1.3 Population Using DBMS_INMEMORY_ADMIN.POPULATE_WAIT

The `DBMS_INMEMORY_ADMIN.POPULATE_WAIT` function initiates population of all `INMEMORY` objects that have a priority greater than or equal to the specified priority, and returns a status value for the population. A user-specified interval specifies the maximum time that the function waits before returning the value to the caller.

Sample use cases for ensuring that objects are populated include:

- When the database is closed, open the database with `STARTUP RESTRICT` so that only administrators can access the database, and then execute `POPULATE_WAIT` with the desired timeout setting. If `POPULATE_WAIT` returns `-1`, indicating a timeout, then reexecute `POPULATE_WAIT`. When the function returns `0`, disable the restricted session so that non-administrative users can query the database.

- Block database connections by using services or an application tier technique. When no analytic indexes exists, and when the application depends on the IM column store to provide reasonable performance, these techniques prevent runaway queries.

The `POPULATE_WAIT` function does not accept a table name as input. Rather, the function submits population tasks for all `INMEMORY` objects with a `PRIORITY` setting greater than or equal to the `priority` specified (the default is `LOW`). If priority is `NONE`, then the function initiates population for all `INMEMORY` objects. `POPULATE_WAIT` does not apply to external tables, which have no priority setting.

The function accepts a population percentage as input, which defaults to `100`, and a timeout interval, which defaults to `99999999` seconds (115.74 days). When you execute the function, the database attempts to populate the objects that meet the specified `PRIORITY` criteria within the timeout interval, and then returns a value indicating the population status.

The following table describes the possible return values for `POPULATE_WAIT`. The function returns the values `0`, `1`, `2`, and `3` only if the condition is met before the end of the interval specified by `timeout`. For example, if `timeout` is `600`, then the function returns `1` only if an out-of-memory error occurs before 600 seconds pass. The function returns `-1` only if the end of the timeout interval occurs before the database completes the requested operation.

Table 5-1 Return Values for POPULATE_WAIT

| Constant                       | Value | Description                                                                                                                                                                                                                                                                              |
|:-------------------------------|:------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `POPULATE_TIMEOUT`             | `-1`  | The function timed out while waiting for population to complete.<br>Existing population jobs continue running in the background after `-1` is returned. Reissuing `POPULATE_TIMEOUT` after `-1` is returned reinitiates population; segments that are already populated are not dropped. |
| `POPULATE_SUCCESS`             | `0`   | All objects that met the `priority` criteria were populated to the specified `percentage` of completion.                                                                                                                                                                                 |
| `POPULATE_OUT_OF_MEMORY`       | `1`   | The In-Memory pool had insufficient memory to populate the objects that met the `priority` criteria to the specified `percentage` of completion.                                                                                                                                         |
| `POPULATE_NO_INMEMORY_OBJECTS` | `2`   | No `INMEMORY` objects met the specified `priority` criteria.                                                                                                                                                                                                                             |
| `POPULATE_INMEMORY_SIZE_ZERO`  | `3`   | The In-Memory column store is not enabled.                                                                                                                                                                                                                                               |

**See Also:**

- "Setting a Timeout Using the POPULATE_WAIT Function: Example"

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_INMEMORY_ADMIN.md) to learn about the `DBMS_INMEMORY_ADMIN` package

#### 5.1.4 Population Using DBMS_INMEMORY.REPOPULATE

`DBMS_INMEMORY.REPOPULATE` forces repopulation of a table, partition, or subpartition that is currently populated in the IM column store.

If you use this procedure on an In-Memory object that is not currently populated, then this procedure is functionally equivalent to `DBMS_INMEMORY.POPULATE`.

**See Also:**

- "Refreshing an In-Memory External Table Using the REPOPULATE Procedure: Example"

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_INMEMORY.md) to learn about the `DBMS_INMEMORY` package

- [Oracle Database SQL Language Reference](../sqlrf/Comments.md) to learn more about the `FULL` hint

### 5.2 Forcing Initial Population of an In-Memory Object

You can force population of an object using a full table scan, the `POPULATE` procedure, the `POPULATE_WAIT` function, or the `REPOPULATE` procedure.

#### Assumptions

This task assumes the following:

- The IM column store is enabled.

- You want to enable a table for In-Memory population.

- You want to force the immediate population of the table into the IM column store.

#### To force population of an INMEMORY table:

1.  In SQL\*Plus or SQL Developer, log in to the database as a user with administrative privileges.

2.  Apply the `INMEMORY` attribute to the table.

    For example, enable `sh.customers` for IM population as follows:

        ALTER TABLE sh.customers INMEMORY;

    In the preceding example, the default priority is `NONE`.

3.  Optionally, check the population status by querying `V$IM_SEGMENTS`.

    For example, use the following statement (sample output included):

        COL OWNER FORMAT a10;
        COL NAME FORMAT a25;
        COL STATUS FORMAT a10;

        SELECT OWNER, SEGMENT_NAME NAME,
               POPULATE_STATUS STATUS
        FROM   V$IM_SEGMENTS
        WHERE  SEGMENT_NAME = 'CUSTOMERS';

        no rows selected

    The preceding output shows that the object is not yet populated in the IM column store.

4.  Initiate population using one of the following techniques:

    - Query all rows in the table using `SELECT` with the `FULL` hint.

      For example, issue the following statement:

          SELECT /*+ FULL(customers) NO_PARALLEL(customers) */ COUNT(*) FROM sh.customers;

    - Execute the `DBMS_INMEMORY.POPULATE` procedure.

      For example, execute this procedure for `sh.customers` as follows:

          EXEC DBMS_INMEMORY.POPULATE('SH', 'CUSTOMERS');

    - Execute the `DBMS_INMEMORY.REPOPULATE` procedure.

      For unpopulated tables, this procedure is functionally equivalent to `POPULATE`. For example, execute this procedure for `sh.customers` as follows:

          EXEC DBMS_INMEMORY.REPOPULATE('SH', 'CUSTOMERS');

    - Execute the `DBMS_INMEMORY_ADMIN.POPULATE_WAIT` function.

      The following code example populates all `INMEMORY` objects, regardless of `PRIORITY` setting. The example specifies that the function should wait until all objects are 100% populated, and it should time out with an error if success is not achieved within 1800 seconds (30 minutes).

          VARIABLE b_pop_status NUMBER
          BEGIN
             SELECT DBMS_INMEMORY_ADMIN.POPULATE_WAIT(
                      priority   => 'NONE' ,
                      percentage => 100    ,
                      timeout    => 1800   ,
                      force      => FALSE  )
               INTO :b_pop_status
             FROM   dual;
          END;
          /
          PRINT b_pop_status

5.  Optionally, to check the population status, query `V$IM_SEGMENTS`.

    For example, use the following statement (sample output included):

        SELECT OWNER, SEGMENT_NAME NAME,
               POPULATE_STATUS STATUS
        FROM   V$IM_SEGMENTS
        WHERE  SEGMENT_NAME = 'CUSTOMERS';

        OWN NAME       STATUS
        --- ---------- --------------------
        SH  CUSTOMERS  COMPLETED

    The table is now populated in the IM column store.

**See Also:**

- [Oracle Database Reference](../refrn/V-IM_SEGMENTS.md) to learn about `V$IM_SEGMENTS`

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_INMEMORY.md) to learn about `DBMS_INMEMORY` subprograms

### 5.3 Populating In-Memory Tables Manually: Examples

The following examples illustrate how to populate In-Memory tables manually.

**See Also:**

"[Enabling and Disabling Tables for the IM Column Store](populating-objects-in-memory.md)"

#### 5.3.1 Populating an In-Memory Table Using a Full Table Scan: Example

This example using a full table scan to populate the `sh.sales` table into the IM column store.

Assume that you are logged in to the database as an administrator, and that you have issued the following DDL statement to add the `INMEMORY` clause to the `sh.sales` table:

    ALTER TABLE sh.sales INMEMORY;

The preceding statement uses the defaults for the `INMEMORY` clause: `MEMCOMPRESS FOR QUERY` and `PRIORITY NONE`. Because `PRIORITY` is `NONE`, the database will not automatically populate the table into the IM column store. The following query confirms that the `sh.sales` table is not currently populated:

    COL OWNER FORMAT a10;
    COL NAME FORMAT a25;
    COL STATUS FORMAT a10;

    SELECT OWNER, SEGMENT_NAME NAME,
           POPULATE_STATUS STATUS
    FROM   V$IM_SEGMENTS
    WHERE  SEGMENT_NAME = 'SALES';

    no rows selected

The following query uses the `FULL` hint to force a full table scan of `sales`, thereby initiating population (sample output included):

    SELECT /*+ FULL(sales) NO_PARALLEL(sales) */ COUNT(*) FROM sh.sales;

      COUNT(*)
    ----------
        918843

The following query shows the population status of `sales` (sample output included):

    SET PAGESIZE 50000
    COL OWNER FORMAT a3
    COL NAME FORMAT a10
    COL STATUS FORMAT a20

    SELECT OWNER, SEGMENT_NAME NAME,
           POPULATE_STATUS STATUS
    FROM   V$IM_SEGMENTS
    WHERE  SEGMENT_NAME = 'SALES';

    OWN NAME       STATUS
    --- ---------- --------------------
    SH  SALES      COMPLETED
    SH  SALES      COMPLETED
    SH  SALES      COMPLETED
    SH  SALES      COMPLETED
    SH  SALES      COMPLETED
    SH  SALES      COMPLETED
    SH  SALES      COMPLETED
    SH  SALES      COMPLETED
    SH  SALES      COMPLETED
    SH  SALES      COMPLETED
    SH  SALES      COMPLETED
    SH  SALES      COMPLETED
    SH  SALES      COMPLETED
    SH  SALES      COMPLETED
    SH  SALES      COMPLETED
    SH  SALES      COMPLETED

    16 rows selected.

The following query calculates the compression ratio of the table. The query assumes that the tables are not further compressed on disk.

    COL OWNER FORMAT a5
    COL SEGMENT_NAME FORMAT a5
    SET PAGESIZE 50000

    SELECT v.OWNER, v.SEGMENT_NAME, v.BYTES ORIG_SIZE,
           v.INMEMORY_SIZE IN_MEM_SIZE,
           ROUND(v.BYTES / v.INMEMORY_SIZE, 2) COMP_RATIO
    FROM   V$IM_SEGMENTS v
    ORDER BY 4;

    OWNER SEGME  ORIG_SIZE IN_MEM_SIZE COMP_RATIO
    ----- ----- ---------- ----------- ----------
    SH    SALES     851968     1310720        .65
    SH    SALES     835584     1310720        .64
    SH    SALES     925696     1310720        .71
    SH    SALES     958464     1310720        .73
    SH    SALES     950272     1310720        .73
    SH    SALES     786432     1310720         .6
    SH    SALES     876544     1310720        .67
    SH    SALES     753664     1310720        .58
    SH    SALES    1081344     1310720        .83
    SH    SALES     901120     1310720        .69
    SH    SALES     925696     1310720        .71
    SH    SALES     933888     1310720        .71
    SH    SALES     843776     1310720        .64
    SH    SALES     999424     1310720        .76
    SH    SALES     581632     1507328        .39
    SH    SALES     696320     1507328        .46

    16 rows selected.

#### 5.3.2 Populating a Table Using the POPULATE Procedure: Example

This example uses `DBMS_INMEMORY.POPULATE` to initiate population of the `sh.customers` table into the IM column store.

Assume that you are logged in to the database as an administrator, and that you have issued the following DDL statement to add the `INMEMORY` clause to the `sh.customers` table:

    ALTER TABLE sh.customers INMEMORY;

The preceding statement uses the defaults for the `INMEMORY` clause: `MEMCOMPRESS FOR QUERY` and `PRIORITY NONE`. Because `PRIORITY` is `NONE`, the database will not automatically populate the table into the IM column store. The following query confirms that the `sh.customers` table is not currently populated:

    COL OWNER FORMAT a10;
    COL NAME FORMAT a25;
    COL STATUS FORMAT a10;

    SELECT OWNER, SEGMENT_NAME NAME,
           POPULATE_STATUS STATUS
    FROM   V$IM_SEGMENTS
    WHERE  SEGMENT_NAME = 'CUSTOMERS';

    no rows selected

The following PL/SQL code uses the `POPULATE` procedure to initiative population:

    EXEC DBMS_INMEMORY.POPULATE('SH', 'CUSTOMERS');

The following query shows the population status of `customers` (sample output included):

    SELECT OWNER, SEGMENT_NAME NAME,
           POPULATE_STATUS STATUS
    FROM   V$IM_SEGMENTS
    WHERE  SEGMENT_NAME = 'CUSTOMERS';

    OWN NAME       STATUS
    --- ---------- --------------------
    SH  CUSTOMERS  COMPLETED

#### 5.3.3 Setting a Timeout Using the POPULATE_WAIT Function: Example

This example uses `DBMS_INMEMORY_ADMIN.POPULATE_WAIT` to populate all In-Memory tables, regardless of priority setting.

Example 5-1 Specifying a Timeout Interval for In-Memory Population

In this example, the database contains a number of In-Memory tables with a variety of priority settings. Your goal is to populate every In-Memory table to 100% completion in a restricted database session, and then disable the restricted session so that the application can be guaranteed of querying only the In-Memory representations.

Assume that the database is shut down. In SQL\*Plus, you connect to an idle instance as `SYSDBA`, and then execute the following command (sample output included):

    SQL> STARTUP RESTRICT
    ORACLE instance started.

    Total System Global Area 1157624280 bytes
    Fixed Size                  8839640 bytes
    Variable Size             754974720 bytes
    Database Buffers           16777216 bytes
    Redo Buffers                7933952 bytes
    In-Memory Area            369098752 bytes
    Database mounted.
    Database opened.

The database is open, but is accessible only to administrative users. You execute the following statements in SQL\*Plus (sample output shown in bold):

    VARIABLE b_pop_status NUMBER

    SELECT DBMS_INMEMORY_ADMIN.POPULATE_WAIT(
             priority   => 'NONE' ,
             percentage => 100    ,
             timeout    => 300    )
      INTO b_pop_status
    FROM   DUAL;

    PRINT b_pop_status
    -1

After 5 minutes, the function returns the number `–1`. This code indicates that the function timed out while waiting for population to complete. 5 minutes is not long enough to populate all `INMEMORY` tables. You re-execute the `SELECT` statement, specifying a 30-minute timeout:

    SELECT DBMS_INMEMORY_ADMIN.POPULATE_WAIT(
             priority   => 'NONE' ,
             percentage => 100    ,
             timeout    => 1800   )
      INTO b_pop_status
    FROM   DUAL;

    PRINT b_pop_status
    0

After 8 minutes, the function returns the number `0`. This code indicates that all tables are completely populated. You now disable the restricted session so that the application can start query In-Memory objects with full confidence that only In-Memory representations will be accessed:

    ALTER SYSTEM DISABLE RESTRICTED SESSION;

#### 5.3.4 Populating an In-Memory External Table Using DBMS_INMEMORY.POPULATE: Example

This example populates an external table that has the `INMEMORY` option.

This example assumes that you created the external table `sh.admin_ext_sales` with the `INMEMORY` option using the `sh_sales.csv` file.

The `admin_ext_sales` table is not yet populated. Starting in Oracle Database 19c, a full table scan populates an external table just as it populates a standard table. However, in this scenario, you choose to initiate population by using the `DBMS_INMEMORY` package.

**Note:**

Sessions that query In-Memory external tables must have the initialization parameter `QUERY_REWRITE_INTEGRITY` set to `stale_tolerated`.

It is important to keep in mind that if an external table is modified, then the results from the IM column store are undefined. Results are also undefined if a partition is altered (by dropping or adding values). This may lead to differences in results between IM and non-IM based scans. You can run `DBMS_INMEMORY.REPOPULATE` to refresh the IM store so that it is resynchronized with the table data.

To populate the table, you perform the following steps:

1.  Log in as user `sh`.

2.  Set `QUERY_REWRITE_INTEGRITY` in the database session:

        ALTER SESSION SET QUERY_REWRITE_INTEGRITY=stale_tolerated;

3.  Execute the following PL/SQL program:

        EXEC DBMS_INMEMORY.POPULATE('SH', 'ADMIN_EXT_SALES');

4.  Check the population status by querying `V$IM_SEGMENTS`:

        COL OWNER FORMAT a3
        COL NAME FORMAT a15
        COL STATUS FORMAT a9

        SELECT OWNER, SEGMENT_NAME NAME,
               POPULATE_STATUS STATUS
        FROM   V$IM_SEGMENTS;

        OWN NAME            STATUS
        --- --------------- ---------
        SH  ADMIN_EXT_SALES COMPLETED

    The preceding output shows that the `admin_ext_sales` table has been populated

**See Also:**

- "[In-Memory Views](views-related-to-im-column-store.md)"

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_INMEMORY.md) to learn more about `DBMS_INMEMORY.POPULATE`

- [Oracle Database Reference](../refrn/QUERY_REWRITE_INTEGRITY.md) to learn about the `QUERY_REWRITE_INTEGRITY` initialization parameter

#### 5.3.5 Refreshing an In-Memory External Table Using the REPOPULATE Procedure: Example

This example repopulates a currently populated In-Memory external table.

This example assumes that you used the comma-delimited flat file `/tmp/data/sh_sales.csv` to create the `sh.admin_ext_sales` table with the `INMEMORY` option, and that you populated this table into the IM column store.

Assume you add a record to `/tmp/data/sh_sales.csv` as follows:

    echo "148,8787,23-NOV-01,2,999,1,23.43" >> /tmp/data/sh_sales.csv

Unlike internal tables, external tables do not use the automatic repopulation mechanism. To refresh external tables, you must use one of the following techniques:

- Call the `DBMS_INMEMORY.REPOPULATE` procedure

- Specify the table as `NO INMEMORY`, specify it as `INMEMORY`, and then perform a full table scan

The following example uses the `REPOPULATE` procedure to force the IM column store to refresh `admin_ext_sales`:

    EXEC DBMS_INMEMORY.REPOPULATE('SH', 'ADMIN_EXT_SALES');

**See Also:**

- "[Creating an In-Memory External Table: Example](populating-objects-in-memory.md)"

- "[Controls for Repopulation of the IM Column Store](repopulation-and-dml.md)"

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_INMEMORY.md) to learn more about `DBMS_INMEMORY.REPOPULATE`
