To implement an Information Lifecycle Management (ILM) strategy for data movement in your database, you can use Heat Map and Automatic Data Optimization (ADO) features.

**Note:**

Heat Map and ADO are supported in Oracle Database 12c Release 2 multitenant environments.

This section contains the following topics:

- Using Heat Map

- Using Automatic Data Optimization

- Limitations and Restrictions With ADO and Heat Map

**See Also:**

- [Managing ILM Heat Map and ADO with Oracle Enterprise Manager](heatmap-ado-em.md) for information about using Oracle Enterprise Manager Cloud Control with Heat Map and ADO

- [Oracle Database Vault Administrator’s Guide](../dvadm/dba-operations-in-an-oracle-database-vault-environment.md) for information about using Information Lifecycle Management (ILM) with Oracle Database Vault realms and command rules, including granting the authorization that enables an ADO administrative user to perform ILM operations on Database Vault-protected objects.

### 5.2.1 Using Heat Map

To implement your ILM strategy, you can use Heat Map in Oracle Database to track data access and modification.

Heat Map provides data access tracking at the segment-level and data modification tracking at the segment and row level. You can enable this functionality with the `HEAT_MAP` initialization parameter.

Heat Map data can assist Automatic Data Optimization (ADO) to manage the contents of the In-Memory column store (IM column store) using ADO policies. Using Heat Map data, which includes column statistics and other relevant statistics, the IM column store can determine when it is almost full (under memory pressure). If the determination is almost full, then inactive segments can be evicted if there are more frequently accessed segments that would benefit from population in the IM column store.

This section contains the following topics:

- Enabling and Disabling Heat Map

- Displaying Heat Map Tracking Data With Views

- Managing Heat Map Data With DBMS_HEAT_MAP Subprograms

**See Also:**

- [Oracle Database In-Memory Guide](../inmem/enabling-the-im-column-store.md) for information about enabling and sizing the In-Memory Column Store

#### 5.2.1.1 Enabling and Disabling Heat Map

You can enable and disable heat map tracking at the system or session level with the `ALTER` `SYSTEM` or `ALTER` `SESSION` statement using the `HEAT_MAP` clause.

For example, the following SQL statement enables Heat Map tracking for the database instance.

    ALTER SYSTEM SET HEAT_MAP = ON;

When Heat Map is enabled, all accesses are tracked by the in-memory activity tracking module. Objects in the `SYSTEM` and `SYSAUX` tablespaces are not tracked.

The following SQL statement disables heat map tracking.

    ALTER SYSTEM SET HEAT_MAP = OFF;

When Heat Map is disabled, accesses are not tracked by the in-memory activity tracking module. The default value for the `HEAT_MAP` initialization parameter is `OFF`.

The `HEAT_MAP` initialization parameter also enables and disables Automatic Data Optimization (ADO). For ADO, Heat Map must be enabled at the system level.

**See Also:**

- Using Automatic Data Optimization for more information about ADO

- [Oracle Database Reference](../refrn/HEAT_MAP.md) for information about the `HEAT_MAP` initialization parameter

#### 5.2.1.2 Displaying Heat Map Tracking Data With Views

Heat map tracking data is viewed with `V$*`, `ALL*`, `DBA*`, and `USER*` heat map views.

Example 5-1 shows examples of information provided by heat map views. The `V$HEAT_MAP_SEGMENT` view displays real-time segment access information. The `ALL_`, `DBA_`, and `USER_HEAT_MAP_SEGMENT` views display the latest segment access time for all segments visible to the user. The `ALL_`, `DBA_`, and `USER_HEAT_MAP_SEG_HISTOGRAM` views display segment access information for all segments visible to the user. The `DBA_HEATMAP_TOP_OBJECTS` view displays heat map information for the top most active objects. The `DBA_HEATMAP_TOP_TABLESPACES` view displays heat map information for the top most active tablespaces.

**See Also:**

[Oracle Database Reference](../refrn/about-static-data-dictionary-views.md) for information about Heat Map views

Example 5-1 Heat map views

    /* enable heat map tracking if necessary*/

    SELECT SUBSTR(OBJECT_NAME,1,20), SUBSTR(SUBOBJECT_NAME,1,20), TRACK_TIME, SEGMENT_WRITE,
      FULL_SCAN, LOOKUP_SCAN FROM V$HEAT_MAP_SEGMENT;

    SUBSTR(OBJECT_NAME,1 SUBSTR(SUBOBJECT_NAM TRACK_TIM SEG FUL LOO
    -------------------- -------------------- --------- --- --- ---
    SALES                SALES_Q1_1998        01-NOV-12 NO  NO  NO
    SALES                SALES_Q3_1998        01-NOV-12 NO  NO  NO
    SALES                SALES_Q2_2000        01-NOV-12 NO  NO  NO
    SALES                SALES_Q3_1999        01-NOV-12 NO  NO  NO
    SALES                SALES_Q2_1998        01-NOV-12 NO  NO  NO
    SALES                SALES_Q2_1999        01-NOV-12 NO  NO  NO
    SALES                SALES_Q4_2001        01-NOV-12 NO  NO  NO
    SALES                SALES_Q1_1999        01-NOV-12 NO  NO  NO
    SALES                SALES_Q4_1998        01-NOV-12 NO  NO  NO
    SALES                SALES_Q1_2000        01-NOV-12 NO  NO  NO
    SALES                SALES_Q1_2001        01-NOV-12 NO  NO  NO
    SALES                SALES_Q2_2001        01-NOV-12 NO  NO  NO
    SALES                SALES_Q3_2000        01-NOV-12 NO  NO  NO
    SALES                SALES_Q4_2000        01-NOV-12 NO  NO  NO
    EMPLOYEES                                 01-NOV-12 NO  NO  NO
    ...

    SELECT SUBSTR(OBJECT_NAME,1,20), SUBSTR(SUBOBJECT_NAME,1,20), SEGMENT_WRITE_TIME,
      SEGMENT_READ_TIME, FULL_SCAN, LOOKUP_SCAN FROM USER_HEAT_MAP_SEGMENT;

    SUBSTR(OBJECT_NAME,1 SUBSTR(SUBOBJECT_NAM SEGMENT_W SEGMENT_R FULL_SCAN LOOKUP_SC
    -------------------- -------------------- --------- --------- --------- ---------
    SALES                SALES_Q1_1998                            30-OCT-12 01-NOV-12
    SALES                SALES_Q1_1998                            30-OCT-12 01-NOV-12
    SALES                SALES_Q1_1998                            30-OCT-12 01-NOV-12
    SALES                SALES_Q1_1998                            30-OCT-12 01-NOV-12
    SALES                SALES_Q1_1998                            30-OCT-12 01-NOV-12
    SALES                SALES_Q1_1998                            30-OCT-12 01-NOV-12
    ...

    SELECT SUBSTR(OBJECT_NAME,1,20), SUBSTR(SUBOBJECT_NAME,1,20), TRACK_TIME, SEGMENT_WRITE, FULL_SCAN,
      LOOKUP_SCAN FROM USER_HEAT_MAP_SEG_HISTOGRAM;

    SUBSTR(OBJECT_NAME,1 SUBSTR(SUBOBJECT_NAM TRACK_TIM SEG FUL LOO
    -------------------- -------------------- --------- --- --- ---
    SALES                SALES_Q1_1998        31-OCT-12 NO  NO  YES
    SALES                SALES_Q1_1998        01-NOV-12 NO  NO  YES
    SALES                SALES_Q1_1998        30-OCT-12 NO  YES YES
    SALES                SALES_Q2_1998        01-NOV-12 NO  NO  YES
    SALES                SALES_Q2_1998        31-OCT-12 NO  NO  YES
    SALES                SALES_Q2_1998        30-OCT-12 NO  YES YES
    SALES                SALES_Q3_1998        01-NOV-12 NO  NO  YES
    SALES                SALES_Q3_1998        30-OCT-12 NO  YES YES
    SALES                SALES_Q3_1998        31-OCT-12 NO  NO  YES
    SALES                SALES_Q4_1998        01-NOV-12 NO  NO  YES
    SALES                SALES_Q4_1998        31-OCT-12 NO  NO  YES
    SALES                SALES_Q4_1998        30-OCT-12 NO  YES YES
    SALES                SALES_Q1_1999        01-NOV-12 NO  NO  YES
    SALES                SALES_Q1_1999        31-OCT-12 NO  NO  YES
    ...

    SELECT SUBSTR(OWNER,1,20), SUBSTR(OBJECT_NAME,1,20), OBJECT_TYPE, SUBSTR(TABLESPACE_NAME,1,20),
        SEGMENT_COUNT FROM DBA_HEATMAP_TOP_OBJECTS ORDER BY SEGMENT_COUNT DESC;

    SUBSTR(OWNER,1,20)   SUBSTR(OBJECT_NAME,1 OBJECT_TYPE        SUBSTR(TABLESPACE_NA SEGMENT_COUNT
    -------------------- -------------------- ------------------ -------------------- -------------
    SH                   SALES                TABLE              EXAMPLE                         96
    SH                   COSTS                TABLE              EXAMPLE                         48
    PM                   ONLINE_MEDIA         TABLE              EXAMPLE                         22
    OE                   PURCHASEORDER        TABLE              EXAMPLE                         18
    PM                   PRINT_MEDIA          TABLE              EXAMPLE                         15
    OE                   CUSTOMERS            TABLE              EXAMPLE                         10
    OE                   WAREHOUSES           TABLE              EXAMPLE                          9
    HR                   EMPLOYEES            TABLE              EXAMPLE                          7
    OE                   LINEITEM_TABLE       TABLE              EXAMPLE                          6
    IX                   STREAMS_QUEUE_TABLE  TABLE              EXAMPLE                          6
    SH                   FWEEK_PSCAT_SALES_MV TABLE              EXAMPLE                          5
    SH                   CUSTOMERS            TABLE              EXAMPLE                          5
    HR                   LOCATIONS            TABLE              EXAMPLE                          5
    HR                   JOB_HISTORY          TABLE              EXAMPLE                          5
    SH                   PRODUCTS             TABLE              EXAMPLE                          5
    ...

    SELECT SUBSTR(TABLESPACE_NAME,1,20), SEGMENT_COUNT
        FROM DBA_HEATMAP_TOP_TABLESPACES ORDER BY SEGMENT_COUNT DESC;

    SUBSTR(TABLESPACE_NA SEGMENT_COUNT
    -------------------- -------------
    EXAMPLE                        351
    USERS                           11

    SELECT COUNT(*) FROM DBA_HEATMAP_TOP_OBJECTS;

      COUNT(*)
    ----------
            64

    SELECT COUNT(*) FROM DBA_HEATMAP_TOP_TABLESPACES;

      COUNT(*)
    ----------
             2

#### 5.2.1.3 Managing Heat Map Data With DBMS_HEAT_MAP Subprograms

The `DBMS_HEAT_MAP` package provides additional flexibility for displaying heat map data using `DBMS_HEAT_MAP` subprograms.

`DBMS_HEAT_MAP` includes one set of APIs that externalize heat maps at various levels of storage such as block, extent, segment, object, and tablespace; and a second set of APIs that externalize the heat maps materialized by the background process for the top tablespaces.

Example 5-2 shows examples of the use of `DBMS_HEAT_MAP` package subprograms.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_HEAT_MAP.md) for information about the `DBMS_HEAT_MAP` package

Example 5-2 Using DBMS_HEAT_MAP package subprograms

    SELECT SUBSTR(segment_name,1,10) Segment, min_writetime, min_ftstime
      FROM TABLE(DBMS_HEAT_MAP.OBJECT_HEAT_MAP('SH','SALES'));

    SELECT SUBSTR(tablespace_name,1,16) Tblspace, min_writetime, min_ftstime
      FROM  TABLE(DBMS_HEAT_MAP.TABLESPACE_HEAT_MAP('EXAMPLE'));

    SELECT relative_fno, block_id, blocks, TO_CHAR(min_writetime, 'mm-dd-yy hh-mi-ss') Mintime,
       TO_CHAR(max_writetime, 'mm-dd-yy hh-mi-ss') Maxtime,
       TO_CHAR(avg_writetime, 'mm-dd-yy hh-mi-ss') Avgtime
       FROM TABLE(DBMS_HEAT_MAP.EXTENT_HEAT_MAP('SH','SALES')) WHERE ROWNUM < 10;

    SELECT SUBSTR(owner,1,10) Owner, SUBSTR(segment_name,1,10) Segment,
      SUBSTR(partition_name,1,16) Partition, SUBSTR(tablespace_name,1,16) Tblspace,
      segment_type, segment_size FROM TABLE(DBMS_HEAT_MAP.OBJECT_HEAT_MAP('SH','SALES'));

    OWNER      SEGMENT    PARTITION        TBLSPACE         SEGMENT_TYPE         SEGMENT_SIZE
    ---------- ---------- ---------------- ---------------- -------------------- ------------
    SH         SALES      SALES_Q1_1998    EXAMPLE          TABLE PARTITION           8388608
    SH         SALES      SALES_Q2_1998    EXAMPLE          TABLE PARTITION           8388608
    SH         SALES      SALES_Q3_1998    EXAMPLE          TABLE PARTITION           8388608
    SH         SALES      SALES_Q4_1998    EXAMPLE          TABLE PARTITION           8388608
    SH         SALES      SALES_Q1_1999    EXAMPLE          TABLE PARTITION           8388608
    ...

### 5.2.2 Using Automatic Data Optimization

To implement your ILM strategy, you can use Automatic Data Optimization (ADO) to automate the compression and movement of data between different tiers of storage within the database.

The functionality includes the ability to create policies that specify different compression levels for each tier, and to control when the data movement takes place.

This section contains the following topics:

- Managing Policies for Automatic Data Optimization

- Creating a Table With an ILM ADO Policy

- Adding ILM ADO Policies

- Disabling and Deleting ILM ADO Policies

- Specifying Segment-Level Compression and Storage Tiering With ADO

- Specifying Row-Level Compression Tiering With ADO

- Managing ILM ADO Parameters

- Using PL/SQL Functions for Policy Management

- Using Views to Monitor Policies for ADO

To use Automatic Data Optimization, you must enable Heat Map at the system level. You enable this functionality with the `HEAT_MAP` initialization parameter. For information about setting the `HEAT_MAP` initialization parameter, refer to Enabling and Disabling Heat Map.

#### 5.2.2.1 Managing Policies for Automatic Data Optimization

You can specify policies for ADO at the row, segment, and tablespace granularity level when creating and altering tables with SQL statements. In addition, ADO policies can perform action on indexes.

By specifying policies for ADO, you can automate data movement between different tiers of storage within the database. These policies also enable you to specify different compression levels for each tier, and to control when the data movement takes place.

##### ADO Policies for Tables

The ILM clauses of the SQL `CREATE` and `ALTER` `TABLE` statements enable you to create, delete, enable or disable a policy for ADO. An ILM policy clause determines the compression or storage tiering policy and contains additional clauses, such as the `AFTER` and `ON` clauses to specify the condition when a policy action should occur. When you create a table, you can add a new policy for ADO. You can alter the table to add more policies or to enable, disable, or delete existing policies. You can add policies to an entire table or a partition of a table. You can specify only one condition type for an `AFTER` clause when adding an ADO policies to a table or partition of a table. ILM ADO policies are given a system-generated name, such `P1`, `P2`, and so on to `P``n`.

A segment level policy executes only one time. After the policy executes successfully, it is disabled and is not evaluated again. However, you can explicitly enable the policy again. A row level policy continues to execute and is not disabled after a successful execution.

The scope of an ADO policy can be specified for a group of related objects or at the level of a segment or row, using the keywords `GROUP`, `ROW`, or `SEGMENT`.

The default mappings for compression that can be applied to group policies are:

- `COMPRESS` `ADVANCED` on a heap table maps to standard compression for indexes and `LOW` for LOB segments.

- `COMPRESS` `FOR` `QUERY` `LOW`/`QUERY` `HIGH` on a heap table maps to standard compression for indexes and `MEDIUM` for LOB segments.

- `COMPRESS` `FOR` `ARCHIVE` `LOW`/`ARCHIVE` `HIGH` on a heap table maps to standard compression for indexes and `HIGH` for LOB segments.

The compression mapping cannot be changed. `GROUP` can only be applied to segment level policies. The storage tiering policies are applicable only at the segment level and cannot be specified at the row level.

##### ADO Policies for In-Memory Column Store

Automatic Data Optimization (ADO) supports the In-Memory Column Store (IM column store) with the `INMEMORY`, `INMEMORY` `MECOMPRESS`, and `NO` `INMEMORY` policy types.

- To enable objects for population in the In-Memory Column Store, include `INMEMORY` in the `ADD` `POLICY` clause.

- To increase the compression level on objects in an IM column store, include `INMEMORY` `MEMCOMPRESS` in the `ADD` `POLICY` clause.

- To explicitly evict objects that benefit the least from the IM column store, include `NO` `INMEMORY` in the `ADD` `POLICY` clause. For example:

The following is an example of the use the `NO` `INMEMORY` clause to evict objects from the IM column store.

    ALTER TABLE sales_2015 ILM ADD POLICY NO INMEMORY
          AFTER 7 DAYS OF NO ACCESS;

An ADO policy with an In-Memory Column Store clause can only be a segment level policy. The `USER/DBA_ILMDATAMOVEMENTPOLICIES` and `V$HEAT_MAP_SEGMENT` views include information about ADO policies for the In-Memory Column Store.

##### Customizing ADO Policies

You can customize policies with the `ON` `PL/SQL_function` option which provides the ability to determine when the policy should be executed. The `ON` `PL/SQL_function` option is available only with segment level policies. For example:

    CREATE OR REPLACE FUNCTION my_custom_ado_rules (objn IN NUMBER) RETURN BOOLEAN;

    ALTER TABLE sales_custom ILM ADD POLICY COMPRESS ADVANCED SEGMENT
          ON my_custom_ado_rules;

**See Also:**

- [Oracle Database In-Memory Guide](../inmem/configuring-memory-management.md) for information about In-Memory Column Store and ADO support

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md) for information about the syntax of the ILM clauses in SQL statements

#### 5.2.2.2 Creating a Table With an ILM ADO Policy

Use the `ILM` `ADD` `POLICY` clause with the `CREATE` `TABLE` statement to create a table with ILM ADO policy.

The SQL statement in Example 5-3 creates a table and adds an ILM policy.

Example 5-3 Creating a table with an ILM ADO policy

    /* Create an example table with an ILM ADO policy */
    CREATE TABLE sales_ado
     (PROD_ID NUMBER NOT NULL,
      CUST_ID NUMBER NOT NULL,
      TIME_ID DATE NOT NULL,
      CHANNEL_ID NUMBER NOT NULL,
      PROMO_ID NUMBER NOT NULL,
      QUANTITY_SOLD NUMBER(10,2) NOT NULL,
      AMOUNT_SOLD NUMBER(10,2) NOT NULL )
     PARTITION BY RANGE (time_id)
     ( PARTITION sales_q1_2012 VALUES LESS THAN (TO_DATE('01-APR-2012','dd-MON-yyyy')),
       PARTITION sales_q2_2012 VALUES LESS THAN (TO_DATE('01-JUL-2012','dd-MON-yyyy')),
       PARTITION sales_q3_2012 VALUES LESS THAN (TO_DATE('01-OCT-2012','dd-MON-yyyy')),
       PARTITION sales_q4_2012 VALUES LESS THAN (TO_DATE('01-JAN-2013','dd-MON-yyyy')) )
      ILM ADD POLICY COMPRESS FOR ARCHIVE HIGH SEGMENT
          AFTER 12 MONTHS OF NO ACCESS;

    /* View the existing ILM ADO polices */
    SELECT SUBSTR(policy_name,1,24) POLICY_NAME, policy_type, enabled
           FROM USER_ILMPOLICIES;

    POLICY_NAME              POLICY_TYPE   ENABLE
    ------------------------ ------------- ------
    P1                       DATA MOVEMENT YES

#### 5.2.2.3 Adding ILM ADO Policies

Use the `ILM` `ADD` `POLICY` clause with the `ALTER` `TABLE` statement to add an ILM ADO policy to a table.

The SQL statements in Example 5-4 provide examples of adding ILM policies to a partition of the `sales` table.

Example 5-4 Adding ILM ADO policies

    /* Add a row-level compression policy after 30 days of no modifications */
    ALTER TABLE sales MODIFY PARTITION sales_q1_2002
      ILM ADD POLICY ROW STORE COMPRESS ADVANCED ROW
      AFTER 30 DAYS OF NO MODIFICATION;

    /* Add a segment level compression policy for data after 6 months of no modifications */
    ALTER TABLE sales MODIFY PARTITION sales_q1_2001
      ILM ADD POLICY COMPRESS FOR ARCHIVE HIGH SEGMENT
      AFTER 6 MONTHS OF NO MODIFICATION;

    /* Add a segment level compression policy for data after 12 months of no access */
    ALTER TABLE sales MODIFY PARTITION sales_q1_2000
          ILM ADD POLICY COMPRESS FOR ARCHIVE HIGH SEGMENT
          AFTER 12 MONTHS OF NO ACCESS;

    /* Add storage tier policy to move old data to a different tablespace */
    /* that is on low cost storage media */
    ALTER TABLE sales MODIFY PARTITION sales_q1_1999
      ILM ADD POLICY
      TIER TO my_low_cost_sales_tablespace;

    /* View the existing polices */
    SELECT SUBSTR(policy_name,1,24) POLICY_NAME, policy_type, enabled
       FROM USER_ILMPOLICIES;

    POLICY_NAME              POLICY_TYPE   ENABLE
    ------------------------ ------------- ------
    P1                       DATA MOVEMENT YES
    P2                       DATA MOVEMENT YES
    P3                       DATA MOVEMENT YES
    P4                       DATA MOVEMENT YES
    P5                       DATA MOVEMENT YES

#### 5.2.2.4 Disabling and Deleting ILM ADO Policies

Use the `ILM` `DISABLE` `POLICY` or `ILM` `DELETE` `POLICY` clauses with the `ALTER` `TABLE` statement to disable or delete an ILM ADO policy.

You can disable or delete ILM policies for ADO as shown in the SQL statements in Example 5-5. At times you may need to remove existing ILM policies if those policies conflict with a new policy that you want to add.

Example 5-5 Disabling and deleting ILM ADO policies

    /* You can disable or delete an ADO policy in a table with the following */
    ALTER TABLE sales_ado ILM DISABLE POLICY P1;
    ALTER TABLE sales_ado ILM DELETE POLICY P1;

    /* You can disable or delete all ADO policies in a table with the following */
    ALTER TABLE sales_ado ILM DISABLE_ALL;
    ALTER TABLE sales_ado ILM DELETE_ALL;

    /* You can disable or delete an ADO policy in a partition with the following */
    ALTER TABLE sales MODIFY PARTITION sales_q1_2002 ILM DISABLE POLICY P2;
    ALTER TABLE sales MODIFY PARTITION sales_q1_2002 ILM DELETE POLICY P2;

    /* You can disable or delete all ADO policies in a partition with the following */
    ALTER TABLE sales MODIFY PARTITION sales_q1_2000 ILM DISABLE_all;
    ALTER TABLE sales MODIFY PARTITION sales_q1_2000 ILM DELETE_ALL;

#### 5.2.2.5 Specifying Segment-Level Compression and Storage Tiering With ADO

You can specify compression at the segment-level within a table using a segment-level compression tiering policy.

In combination with the row-level compression tiering policy, you have fine-grained control over how the data in your database is stored and managed.

Example 5-6 illustrates how to create policies for ADO to enforce a compression and storage tiering policy on the `sales_ado` table, reflecting the following business requirements:

1.  Bulk Load Data

2.  Run OLTP workloads

3.  After six months with no updates, compress for Archive High

4.  Move to low cost storage

Example 5-6 Using segment-level compression and storage tiering

    /* Add a segment level compression policy after 6 months of no changes */
    ALTER TABLE sales_ado ILM ADD POLICY
      COMPRESS FOR ARCHIVE HIGH SEGMENT
      AFTER 6 MONTHS OF NO MODIFICATION;

    Table altered.

    /* Add storage tier policy */
    ALTER TABLE sales_ado ILM ADD POLICY
      TIER TO my_low_cost_tablespace;

    SELECT SUBSTR(policy_name,1,24) POLICY_NAME, policy_type, enabled
      FROM USER_ILMPOLICIES;

    POLICY_NAME              POLICY_TYPE   ENABLED
    ------------------------ ------------- -------
    ...
    P6                       DATA MOVEMENT  YES
    P7                       DATA MOVEMENT  YES

#### 5.2.2.6 Specifying Row-Level Compression Tiering With ADO

Automatic Data Optimization (ADO) policies support Hybrid Columnar Compression (HCC) in addition to basic and advanced compression.

An HCC row level policy can be defined on any table regardless of the compression type of the table. Rows from cold blocks can be compressed with HCC when there is DML activity on other parts of the segment.

With HCC policies on non-HCC tables, there may be row movement during updates if the row is in a HCC compression unit (CU). Also, similar to other use cases of row movement, index maintenance is necessary to update index entries that referenced the moved row.

Row-level policies are supported in Oracle Database 12c Release 1 (12.1): however, the database must be at 12.2 compatibility or greater to use HCC row-level compression policies.

**See Also:**

[Oracle Database Administrator’s Guide](../admin/managing-tables.md) for information about table compression

Example 5-7 Creating an ADO policy using row-level Hybrid Columnar Compression

The SQL statement in Example 5-7 creates a policy using HCC on the rows of the table `employees_ilm`.

    ALTER TABLE employees_ilm
       ILM ADD POLICY COLUMN STORE COMPRESS FOR QUERY ROW
       AFTER 30 DAYS OF NO MODIFICATION;

Example 5-8 Creating an ADO policy using row-level advanced compression

The SQL statement in Example 5-8 creates a policy using advanced compression on the rows of the table `sales_ado`.

    ALTER TABLE sales_ado
      ILM ADD POLICY ROW STORE COMPRESS ADVANCED ROW
      AFTER 60 DAYS OF NO MODIFICATION;

    SELECT policy_name, policy_type, enabled
       FROM USER_ILMPOLICIES;

    POLICY_NAME              POLICY_TYPE   ENABLE
    ------------------------ ------------- -------
    ...
    P8                       DATA MOVEMENT YES

#### 5.2.2.7 Managing ILM ADO Parameters

You can customize your ADO environment with ILM ADO parameters that you set with the `CUSTOMIZE_ILM` procedure in the `DBMS_ILM_ADMIN` PL/SQL package.

Various ILM ADO parameters are described in Table 5-2.

Table 5-2 ILM ADO Parameters

| Name                       | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
|:---------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ABSOLUTE``JOB` `LIMIT`    | The value for `ABSOLUTE``JOB` `LIMIT` limits the absolute number of concurrent ADO jobs.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `DEGREE``OF` `PARALLELISM` | The value for `DEGREE``OF` `PARALLELISM` determines the degree of parallelism in which the ADO policy jobs are run.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `ENABLED`                  | The `ENABLED` parameter controls ADO background evaluation and execution. The default is enabled on (`TRUE` or `1`).<br>The settings of `ENABLED` and the `HEAT_MAP` initialization parameters interact as follows:<br>• If the `HEAT_MAP` initialization parameter is set to `ON` and the `ENABLED` parameter is set to `FALSE` (`0`), then heat map statistics are collected, but ADO does not act on the statistics automatically.<br>• If the `HEAT_MAP` initialization parameter is set to `OFF` and the `ENABLED` parameter is set to `TRUE` (`1`), then heat map statistics are not collected and because ADO cannot rely on the heat map statistics, ADO does nothing. ADO behaves as if `ENABLED` is set to `FALSE`. |
| `EXECUTION` `MODE`         | The value of `EXECUTION` `MODE` controls whether ADO executes in online or offline mode. The default is online (`2`).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `EXECUTION` `INTERVAL`     | The value of `EXECUTION` `INTERVAL` determines the frequency that ADO initiates background evaluation. The default is `15` minutes.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| `JOB` `LIMIT`              | The value for `JOB` `LIMIT` controls the maximum number of ADO jobs at any time. The maximum number of concurrent ADO jobs is calculated as (`JOB` `LIMIT`)\*(number of instances)\*(number of CPUs for each instance). The default is `2`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `POLICY` `TIME`            | The value for `POLICY` `TIME` determines if ADO policies are specified in seconds or days. Values are `1` for seconds or `0` for days (default).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `RETENTION` `TIME`         | The value for `RETENTION` `TIME` specifies the length of time that data of completed ADO tasks is kept before that data is purged. The default is `30` days.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `TBS` `PERCENT` `USED`     | The value for `TBS_PERCENT_USED` parameter specifies the percentage of the tablespace quota when a tablespace is considered full. The default is `85` percent.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `TBS` `PERCENT` `FREE`     | The value for `TBS_PERCENT_FREE` parameter specifies the targeted free percentage for the tablespace. The default is `25` percent.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |

For the values of the `TBS_PERCENT`\* parameters, ADO makes a best effort, but not a guarantee. When the percentage of the tablespace quota reaches the value of `TBS_PERCENT_USED`, ADO begins to move data so that percent free of the tablespace quota approaches the value of `TBS_PERCENT_FREE`. As an example, assume that `TBS_PERCENT_USED` is set to 85 and `TBS_PERCENT_FREE` is set to `25`, and that a tablespace becomes `90` percent full. ADO then initiates actions to move data so that the tablespace quota has at least `25` percent free, which can also be interpreted as less than `75` percent used of the tablespace quota.

You can display the parameters with the `DBA_ILMPARAMETERS` view. For example, the following query displays the values of the ADO-related parameters.

    SQL> SELECT NAME, VALUE FROM DBA_ILMPARAMETERS;

    ---------------------------------------------------------------- ----------
    ENABLED                                                                   1
    RETENTION TIME                                                           30
    JOB LIMIT                                                                 2
    EXECUTION MODE                                                            2
    EXECUTION INTERVAL                                                       15
    TBS PERCENT USED                                                         85
    TBS PERCENT FREE                                                         25
    POLICY TIME                                                               0
    ABSOLUTE JOB LIMIT                                                       10
    DEGREE OF PARALLELISM                                                     4
    ...

**See Also:**

- Example 5-9 for an example showing how to set ILM ADO parameters with the `CUSTOMIZE_ILM` procedure in the `DBMS_ILM_ADMIN` PL/SQL package

- [Managing ILM Heat Map and ADO with Oracle Enterprise Manager](heatmap-ado-em.md) for information about setting ILM ADO parameters with Oracle Enterprise Manager Cloud Control

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_ILM_ADMIN.md) for a complete list of ILM ADO parameters

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_ILM_ADMIN.md) for information about the `DBMS_ILM_ADMIN` package

#### 5.2.2.8 Using PL/SQL Functions for Policy Management

You can use the PL/SQL `DBMS_ILM` and `DBMS_ILM_ADMIN` packages for advanced policy management and customization to implement more complex ADO scenarios and control when policies are actively moving and compressing data.

With the PL/SQL `DBMS_ILM` and `DBMS_ILM_ADMIN` packages, you can manage ILM activities for ADO so that they do not negatively impact important production workloads. Database compatibility must be set to a minimum of 12.0 to use these packages.

The `EXECUTE_ILM` procedure of the `DBMS_ILM` package creates and schedules jobs to enforce policies for ADO. The `EXECUTE_ILM()` procedure provides this functionality, regardless of any previously-scheduled ILM jobs. All jobs are created and scheduled to run immediately; however, whether they are run immediately depends on the number of jobs queued with the scheduler.

You can use the `EXECUTE_ILM` procedure if you want more control when ILM jobs are performed, and do not want to wait until the next maintenance window.

The `STOP_ILM` procedure of the `DBMS_ILM` package stops all jobs, all running jobs, jobs based on a task Id, or a specific job.

The `CUSTOMIZE_ILM` procedure in the `DBMS_ILM_ADMIN` PL/SQL package enables you to customize settings for ADO, as shown in Example 5-9.

For example, you can set the values for the `TBS_PERCENT_USED` and `TBS_PERCENT_FREE` ILM parameters or set the `ABS_JOBLIMIT` ILM parameter. `TBS_PERCENT_USED` and `TBS_PERCENT_FREE` determine when data is moved based on tablespace quotas and `ABS_JOBLIMIT` sets the absolute number of concurrent ADO jobs.

You can also recreate objects with policies using the `DBMS_METADATA` PL/SQL package.

**See Also:**

- Managing ILM ADO Parameters for information about ILM ADO parameters

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_ILM.md) for information about the `DBMS_ILM`, `DBMS_ILM_ADMIN`, and `DBMS_METADATA` packages

Example 5-9 Using CUSTOMIZE_ILM to customize ADO settings

    SQL> BEGIN
      2  DBMS_ILM_ADMIN.CUSTOMIZE_ILM(DBMS_ILM_ADMIN.TBS_PERCENT_USED, 85);
      3  DBMS_ILM_ADMIN.CUSTOMIZE_ILM(DBMS_ILM_ADMIN.TBS_PERCENT_FREE, 25);
      4  END;
      5  /

    SQL> BEGIN
      2  DBMS_ILM_ADMIN.CUSTOMIZE_ILM(DBMS_ILM_ADMIN.ABS_JOBLIMIT, 10);
      3  END;
      4  /

#### 5.2.2.9 Using Views to Monitor Policies for ADO

You can view and monitor the policies for ADO that are associated with your database objects using the `DBA_ILM*` and `USER_ILM*` views, making it easier to change policies as needed.

- The `DBA/USER_ILMDATAMOVEMENTPOLICIES` view displays information specific to data movement related attributes of an ILM policy for ADO.

- The `DBA/USER_ILMTASKS` view displays the task Ids of the procedure `EXECUTE_ILM`. Every time a user invokes the procedure `EXECUTE_ILM`, a task Id is returned to track this particular invocation. A task Id is also generated to track periodic internal ILM tasks by the database. This view contains information about all ILM tasks for ADO.

- The `DBA/USER_ILMEVALUATIONDETAILS` view displays details on policies considered for a particular task. It also shows the name of the job that executes the policy in case the policy was selected for evaluation. In case the policy was not executed, this view also provides a reason.

- The `DBA/USER_ILMOBJECTS` view displays all the objects and policies for ADO in the database. Many objects inherit policies through their parent objects or because they were created in a particular tablespace. This view provides a mapping between the policies and objects. In the case of an inherited policy, this view also indicates the level from which policy is inherited.

- The `DBA/USER_ILMPOLICIES` view displays details about all the policies for ADO in the database.

- The `DBA/USER_ILMRESULTS` view displays information about data movement-related jobs for ADO in the database.

- The `DBA_ILMPARAMETERS` view displays information about ADO-related parameters.

**See Also:**

[Oracle Database Reference](../refrn/about-static-data-dictionary-views.md) for information about the `ILM` views

### 5.2.3 Limitations and Restrictions With ADO and Heat Map

The limitations and restrictions associated with ADO and Heat Map are discussed in this topic.

Limitations and restrictions associated with ADO and Heat Map include:

- Partition-level ADO and compression are supported for Temporal Validity except for row-level ADO policies that would compress rows that are past their valid time (access or modification).

- Partition-level ADO and compression are supported for in-database archiving if partitioned on the `ORA_ARCHIVE_STATE` column.

- Custom policies (user-defined functions) for ADO are not supported if the policies default at the tablespace level.

- ADO Row-level policies support the `OF NO MODIFICATION` condition type only.

- ADO does not perform checks for storage space in a target tablespace when using storage tiering.

- ADO is not supported on tables with object types or materialized views.

- ADO is not supported with index-organized tables or clusters.

- ADO concurrency (the number of simultaneous policy jobs for ADO) depends on the concurrency of the Oracle scheduler. If a policy job for ADO fails more than two times, then the job is marked disabled and the job must be manually enabled later.

- ADO has restrictions related to moving tables and table partitions.

  **See Also:**

  - [Oracle Database SQL Language Reference](../sqlrf/ALTER-TABLE.md) for information about restrictions on moving tables

  - [Oracle Database SQL Language Reference](../sqlrf/ALTER-TABLE.md) for information about restrictions on moving table partitions
