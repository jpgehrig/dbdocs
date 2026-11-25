You can use Automatic Data Optimization (ADO) and Automatic In-Memory to manage objects in the IM column store dynamically.

ADO uses [Heat Map](glossary.md), which tracks data access patterns for blocks and segments. ADO and Heat Map are a part of [Information Lifecycle Management (ILM)](glossary.md), which is a set of processes and policies for managing data from creation to archival or deletion. This chapter assumes that you are familiar with ILM, ADO, and Heat Map.

This chapter contains the following topics:

**See Also:**

[Oracle Database VLDB and Partitioning Guide](../vldbg/ilm-strategy-heatmap-ado.md) for background about ILM, ADO, and Heat Map

### 6.1 Enabling ADO for the IM Column Store

**Automatic Data Optimization (ADO)** creates policies, and automates actions based on those policies, to implement your ILM strategy.

This section contains the following topics:

#### 6.1.1 About ADO Policies and the IM Column Store

ADO manages the IM column store through **ADO policies**. You can only create an ADO policy with an `INMEMORY` clause at the segment level.

The database treats an ADO policy like an attribute of an object. ADO policies are at the database level, not the instance level. Oracle Database supports the following types of ADO policies for Database In-Memory:

- `INMEMORY` policy

  This policy marks objects with the `INMEMORY` attribute, enabling them for population in the IM column store. When set at the table level, the `INMEMORY` attribute applies only to internal partitions; therefore, external partitions of a hybrid partitioned table are not managed by the policy.

- Recompression policy

  This policy changes the compression level on an `INMEMORY` object.

- `NO INMEMORY` policy

  This policy removes an object from the IM column store and removes its `INMEMORY` attribute.

Oracle Database supports the following criteria to determine when policies apply:

- A specified number of days since the object was modified

  Obtain this value from the column `SEGMENT_WRITE_TIME` in the `DBA_HEAT_MAP_SEGMENT` view.

- A specified number of days since the object was accessed

  This value is the greater value in the columns `SEGMENT_WRITE_TIME`, `FULL_SCAN`, and `LOOKUP_SCAN` in the `DBA_HEAT_MAP_SEGMENT` view.

- A specified number of days since the object was created

  Obtain this value from the `CREATED` column in `DBA_OBJECTS`.

- A user-defined function returns a Boolean value

**See Also:**

- [Oracle Database Reference](../refrn/DBA_HEAT_MAP_SEGMENT.md) to learn about the `DBA_HEAT_MAP_SEGMENT` view

- [Oracle Database SQL Language Reference](../sqlrf/ALTER-TABLE.md) to learn about the `INMEMORY` clause

#### 6.1.2 Purpose of ADO and the IM Column Store

ADO manages the IM column store as a new data tier.

You can create policies to evict objects from the IM column store when they are being accessed less often, and populate objects when they are being accessed more often and would improve query performance. ADO manages the IM column store using Heat Map statistics.

##### Purpose of INMEMORY Policies

In many databases, segments undergo heavy modification after creation. To maximize performance, ADO can populate these segments in the IM column store when write activity subsides. For example, if you add a partition to a table every day, then you can create a policy that populates the `sales_2016_d100` partition one day after creation:

    ALTER TABLE sales MODIFY PARTITION sales_2016_d100
      ILM ADD POLICY SET INMEMORY MEMCOMPRESS FOR QUERY
        PRIORITY HIGH
      AFTER 1 DAYS OF CREATION

Similarly, you may know that write activity on a table subsides two months after creation, and want to populate this object when this time condition is met:

    ALTER TABLE 2016_ski_sales
      ILM ADD POLICY SET INMEMORY MEMCOMPRESS FOR QUERY
        PRIORITY CRITICAL
      AFTER 60 DAYS OF CREATION

The preceding policy causes all existing and new partitions of the `2016_ski_sales` table to inherit the policy. When the segment qualifies for the policy, the database marks every partition independently with the specified `INMEMORY` clause. If the segment already has an `INMEMORY` policy, then the database ignores the new policy.

##### Purpose of Recompression Policies

You may want to compress data in the IM column store based on access patterns. For example, you may want to change a segment from DML compression to query compression 2 days after DML activity on the segment has ceased:

    ALTER TABLE lineorders
      ILM ADD POLICY MODIFY INMEMORY MEMCOMPRESS FOR QUERY HIGH
      AFTER 2 DAYS OF NO MODIFICATION

If the object is not populated in IM column store, then this policy only changes the compression attribute. If the object is populated in the IM column store, then ADO repopulates the object using the new compression level. The database ignores the policy if the segment does not already have the `INMEMORY` attribute.

##### Purpose of NO INMEMORY Policies

To optimize space in the IM column store, you may want to evict inactive segments using a `NO INMEMORY` policy. This policy is also useful for preventing population of inactive segments by infrequent queries. For example, if reports on a specific sales partition run frequently during the year, but typically not every week, then you may want to may want to evict this partition after a week of no access:

    ALTER TABLE sales MODIFY PARTITION sales_2015_q1
      ILM ADD POLICY NO INMEMORY AFTER 7 DAYS OF NO ACCESS;

If the sales table for 1998 is rarely queried, then you may want to evict after 1 day of no access:

    ALTER TABLE sales_1998
      ILM ADD POLICY NO INMEMORY AFTER 1 DAYS OF NO ACCESS;

Queries of an evicted segment are never blocked. The database can always access the data through the traditional buffer cache mechanism.

**See Also:**

- "[Row Data in the Database Buffer Cache](in-memory-column-store-architecture.md)"

- [Oracle Database VLDB and Partitioning Guide](../vldbg/manage-data-db-ilm.md)

#### 6.1.3 How ADO Works with Columnar Data

From the ADO perspective, the IM column store is another storage tier.

##### 6.1.3.1 How Heat Map Works

When enabled, Heat Map automatically discovers data access patterns. ADO uses the Heat Map data to implement user-defined policies at the database level.

Heat Map automatically tracks usage information at the row and segment levels. At the row level, Heat Map tracks data modification times, and then aggregates these times to the block level. At the segment level, Heat Map tracks times for modifications, full table scans, and index lookups.

When an IM column store is enabled, Heat Map tracks access patterns for columnar data. For example, the `sales` table may be “hot,” whereas the `locations` table may be “cold.” The ADO algorithms work the same way for columnar data as for row-based data.

The database periodically writes Heat Map data to the data dictionary. The database exposes Heat Map data in data dictionary views. For example, to obtain the read and write time for In-Memory objects, query the `ALL_HEAT_MAP_SEGMENT` view.

**See Also:**

- [Oracle Database VLDB and Partitioning Guide](../vldbg/ilm-strategy-heatmap-ado.md) to learn more about Heat Map

- [Oracle Database Reference](../refrn/ALL_HEAT_MAP_SEGMENT.md) to learn about the `ALL_HEAT_MAP_SEGMENT` view

##### 6.1.3.2 How Policy Evaluation Works

The policy evaluation for IM column store policies uses the same infrastructure as the evaluation of other ADO policies. The database evaluates and executes policies automatically during the maintenance window.

The database evaluates policies using Heat Map statistics, which are stored in the data dictionary. Setting `INMEMORY` attributes is mostly a metadata operation, and thus minimally affects performance.

ADO uses the Job Scheduler to perform population. The In-Memory Coordinator Process (IMCO) performs the population.

**Related Topics**

- [In-Memory Coordinator Process (IMCO)](in-memory-column-store-architecture.md)

#### 6.1.4 Controls for ADO and the IM Column Store

Enable Heat Map using the `HEAT_MAP` initialization parameter. Control ADO through a SQL and PL/SQL interface.

##### ILM Clause in DDL Statements

No new SQL statements are required to create In-Memory policies, but the ILM clause has new options. The following table describes SQL options for ADO and the IM column store.

**Note:**

The `INMEMORY` attribute only applies to internal partitions of a hybrid partitioned table.

Table 6-1 ILM Clause for ADO and the IM Column Store

| Clause            | Description                                     | Examples                                                                                                                                                                                           |
|:------------------|:------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `SET INMEMORY`    | Sets the `INMEMORY` attribute for the object    | `ALTER TABLE sh.sales `<br>`  ILM ADD POLICY `<br>`    SET INMEMORY `<br>`    MEMCOMPRESS FOR QUERY LOW`<br>`    PRIORITY HIGH `<br>`    SEGMENT `<br>`    AFTER 30 DAYS OF CREATION;`             |
| `MODIFY INMEMORY` | Modifies the compression level for the object   | `ALTER TABLE sh.customers `<br>`  ILM ADD POLICY `<br>`    MODIFY INMEMORY `<br>`    MEMCOMPRESS FOR QUERY HIGH`<br>`    PRIORITY CRITICAL `<br>`    SEGMENT `<br>`    AFTER 30 DAYS OF CREATION;` |
| `NO INMEMORY`     | Sets the `NO INMEMORY` attribute for the object | `ALTER TABLE sh.products `<br>`  ILM ADD POLICY `<br>`    NO INMEMORY `<br>`    SEGMENT `<br>`    AFTER 30 DAYS OF CREATION;`                                                                      |

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md) to learn more about the ilm_policy_clause of `CREATE TABLE`

##### Initialization Parameters

The following table describes initialization parameters that are relevant for ADO and the IM column store.

Table 6-2 Initialization Parameters for ADO and the IM Column Store

| Initialization Parameter | Description                                                                                                                                                 |
|:-------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `COMPATIBLE`             | Specifies the release with which the database must maintain compatibility. For ADO to manage the IM column store, set this parameter to `12.2.0` or higher. |
| `HEAT_MAP`               | Enables both the Heat Map and ADO features. For ADO to manage the IM column store, set this parameter to `ON`.                                              |
| `INMEMORY_SIZE`          | Enables the IM column store. This parameter must be set to a nonzero value.                                                                                 |

##### PL/SQL Packages

The following table describes PL/SQL packages that are relevant for ADO and the IM column store.

Table 6-3 PL/SQL Packages for ADO and the IM Column Store

| Package          | Description                                                                                   |
|:-----------------|:----------------------------------------------------------------------------------------------|
| `DBMS_HEAT_MAP`  | Displays detailed Heat Map data at the tablespace, segment, object, extent, and block levels. |
| `DBMS_ILM`       | Implements ILM strategies using ADO policies.                                                 |
| `DBMS_ILM_ADMIN` | Customizes ADO policy execution.                                                              |

**See Also:**

Oracle Database PL/SQL Packages and Types Reference to learn more about [`DBMS_HEAT_MAP`](../arpls/DBMS_HEAT_MAP.md), [`DBMS_ILM`](../arpls/DBMS_ILM.md), and [`DBMS_ILM_ADMIN`](../arpls/DBMS_ILM_ADMIN.md) packages

##### V\$ and Data Dictionary Views

The following table describes views that are relevant for ADO and the IM column store.

Table 6-4 Views for ADO and the IM Column Store

| View                          | Description                                                                                                                                                                                                                                          |
|:------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `DBA_HEAT_MAP_SEG_HISTOGRAM`  | Displays segment access information for all segments visible to the user.                                                                                                                                                                            |
| `DBA_HEAT_MAP_SEGMENT`        | Displays the latest segment access time for all segments visible to the user.                                                                                                                                                                        |
| `DBA_HEATMAP_TOP_OBJECTS`     | Displays heat map information for the top 10000 objects by default.                                                                                                                                                                                  |
| `DBA_HEATMAP_TOP_TABLESPACES` | Displays heat map information for the top 10000 tablespaces.                                                                                                                                                                                         |
| `DBA_ILMDATAMOVEMENTPOLICIES` | Displays information specific to data movement-related attributes of an ADO policy in a database. The `action_type` column describes policies related to the IM column store. Possible values are `COMPRESSION`, `STORAGE`, `EVICT`, and `ANNOTATE`. |
| `V$HEAT_MAP_SEGMENT`          | Displays real-time segment access information.                                                                                                                                                                                                       |

**See Also:**

[Oracle Database Reference](../refrn/about-static-data-dictionary-views.md) to learn more about views

#### 6.1.5 Creating an ADO Policy for the IM Column Store

You can use ADO policies to set, modify, or remove the `INMEMORY` clause for objects based on Heat Map statistics.

To create an ADO IM column store policy, specify the `ILM ADD POLICY` clause in an `ALTER TABLE` statement, followed by one of the following subclauses:

- `SET INMEMORY ... SEGMENT`

  This option is useful when you want to mark segments with the `INMEMORY` attribute only when DML activity subsides.

- `MODIFY INMEMORY ... MEMCOMPRESS ... SEGMENT`

  Storing data uncompressed or at the `MEMCOMPRESS FOR DML` level is appropriate when it is frequently modified. The alternative compression levels are more suited for queries. If the activity on a segment transitions from mostly writes to mostly reads, then you can use the `MODIFY` clause to apply a different compression method.

- `NO INMEMORY ... SEGMENT`

  This option is useful when access to a segment decreases with time (it becomes “cold”), and to prevent population of this segment as a result of random access.

##### Prerequisites

Before you can use an ADO IM column store policy, you must meet the following prerequisites:

- Enable the IM column store for the database by setting the `INMEMORY_SIZE` initialization parameter to a nonzero value and restarting the database.

- The `HEAT_MAP` initialization parameter must be set to `ON`.

  Heat Map provides data access tracking at the segment-level and data modification tracking at the segment and row level.

- The `COMPATIBLE` initialization parameter must be set to `12.2.0` or higher.

##### To create an ADO policy:

1.  In SQL\*Plus or SQL Developer, log in to the database as a user with the necessary privileges.

2.  Use an `ALTER TABLE` statement with the `ILM ADD POLICY ... INMEMORY` clause.

Example 6-1 Creating an Eviction Policy

In this example, you create a policy specifying that `oe.order_items` table is evicted from the IM column store if it has not been accessed in three days. An ADO IM column store policy must be a segment-level policy.

    ALTER TABLE oe.order_items ILM ADD POLICY
       NO INMEMORY SEGMENT
       AFTER 3 DAYS OF NO ACCESS;

Example 6-2 Executing an ILM Policy Using DBMS_ILM

You can also evaluate and executes policies manually. Thus, you can programmatically decide when you want an object compressed or tiered. The following example manually executes an ADO task for `sh.sales`:

    DECLARE
      v_executonid NUMBER;
    BEGIN
      DBMS_ILM.EXECUTE_ILM ( owner           => 'SH',
                             object_name     => 'SALES',
                             execution_mode  => DBMS_ILM.ILM_EXECUTION_OFFLINE,
                             task_id         => v_executionid);
    END;
    /

**See Also:**

- [Oracle Database SQL Language Reference](../sqlrf/CREATE-TABLE.md) for `CREATE TABLE` syntax and semantics

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_ILM.md) to learn more about the `DBMS_ILM` package

### 6.2 Configuring Automatic In-Memory

Automatic In-Memory uses access tracking and column statistics to manage objects in the IM column store.

If the IM column store is full, and if other more frequently accessed segments would benefit from population in the IM column store, then the IM column store evicts inactive segments. If the IM column store is configured to hold all `INMEMORY` segments, however, then Automatic In-Memory takes no action.

**Note:**

If the `INMEMORY_FORCE` initialization parameter is set to `BASE_LEVEL`, then Automatic In-Memory is disabled even if `INMEMORY_AUTOMATIC_LEVEL` is set. Even if tables have a compression level of `AUTO`, Automatic In-Memory background operations do not run.

This chapter contains the following topics:

#### 6.2.1 Purpose of Automatic In-Memory

To ensure that the working data set is always populated, Automatic In-Memory automatically evicts cold (infrequently accessed) segments.

The IM column store only removes a populated segment if it is dropped or moved, the `INMEMORY` option is removed, or an IM ADO policy acts on it. Memory pressure occurs when the size of the `INMEMORY` data set exceeds the available memory for the IM column store, and some populated segments become inactive. For optimal performance, the IM column store should contain the most frequently queried segments, known as the [working data set](glossary.md).

Typically, the working data set changes with time for many applications. Therefore, optimization requires regular monitoring and manual intervention from the DBA to evict IM store elements or create ADO IM policies. Both tasks require a good understanding of the workload.

By automatically evicting cold segments, Automatic In-Memory provides the following benefits:

- Improved performance

  By mitigating memory pressure through eviction of cold segments, Automatic In-Memory improves the performance of workloads because the working data set resides in the IM column store.

- Ease of management

  Management of the IM column store for mitigating memory pressure by eviction of cold segments involves significant user intervention. Automatic In-Memory addresses these issues with minimal user intervention.

#### 6.2.2 How Automatic In-Memory Works

The unit of data eviction is an `INMEMORY` segment.

An `INMEMORY` segment is only eligible for eviction when its priority is `NONE`. The basic process is as follows:

1.  A population job fails, which means that IM column store space has been exhausted.

2.  The database uses internal statistics of eligible populated segments to define the set of objects to evict. The statistics are similar to those used by Heat Map, but do not require Heat Map to be enabled.

3.  For each segment in the set, the database checks whether an ADO policy is enabled for the segment:

    - If an enabled policy requires that the segment remain populated, then the ADO policy overrides Automatic In-Memory. The database does nothing.

    - If no policy prevents eviction, then Automatic In-Memory submits tasks to evict the segments.

4.  Wnnn processes evict any segments that pass the preceding checks, freeing up space in the IM column store.

    The `INMEMORY` attribute is retained for evicted segments.

For example, a nightly batch job loads a `sales` partition (with priority `NONE`), and then queries the partition to trigger population. Because the IM column store is almost at its maximum capacity, only half the rows of the partition are populated. The failure to completely populate the new partition triggers Automatic In-Memory, which evicts a cold segment. A subsequent on-demand populate job for the new partition completely populates the new `sales` partition.

**See Also:**

"[Space Management Worker Processes (Wnnn)](in-memory-column-store-architecture.md)"

#### 6.2.3 User Interface for Automatic In-Memory

Enable and disable Automatic In-Memory using the initialization parameter `INMEMORY_AUTOMATIC_LEVEL`.

##### Initialization Parameters

The system-level initialization parameter `INMEMORY_AUTOMATIC_LEVEL` has the following possible values:

- `OFF` (default)

  This option disables Automatic In-Memory, returning the IM column store to its Oracle Database 12c Release 2 (12.2.0.1) behavior.

- `LOW`

  When under memory pressure, the database evicts cold segments from the IM column store.

- `MEDIUM`

  This level includes an additional optimization that ensures that any hot segment that was not populated because of memory pressure is populated first.

**Note:**

Automatic In-Memory does not require the `HEAT_MAP` initialization parameter to be enabled.

Oracle recommends that you provision enough memory for the working data set to fit in the IM column store. As a rule of thumb for sizing the additional Automatic In-Memory shared pool requirement, multiply 5 KB by the number of `INMEMORY` segments of SGA memory. For example, if 10,000 segments have the `INMEMORY` attribute, then reserve 50 MB of the shared pool for Automatic In-Memory.

**See Also:**

[Oracle Database Reference](../refrn/INMEMORY_AUTOMATIC_LEVEL.md) to learn more about `INMEMORY_AUTOMATIC_LEVEL`

##### DBMS_INMEMORY_ADMIN

Use the `DBMS_INMEMORY_ADMIN` package to control the time window in which Automatic In-Memory considers statistics. For example, you can specify that Automatic In-Memory only consider the past month or the past week.

Use the `DBMS_INMEMORY_ADMIN.AIM_SET_PARAMETER` procedure to set the `AIM_STATWINDOW_DAYS` constant. For example, to set the sliding statistics window to 7 days, execute the following program:

    EXEC DBMS_INMEMORY_ADMIN.AIM_SET_PARAMETER ( DBMS_INMEMORY_ADMIN.AIM_STATWINDOW_DAYS, 7 );

The default value for `AIM_STATWINDOW_DAYS` is `31` days.

The corresponding `DBMS_INMEMORY_ADMIN.AIM_GET_PARAMETER` procedure obtains the current setting for `AIM_STATWINDOW_DAYS`.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_INMEMORY.md) to learn more about `DBMS_INMEMORY_ADMIN.AIM_SET_PARAMETER` and `DBMS_INMEMORY_ADMIN.AIM_GET_PARAMETER`

##### V\$ VIEWS

The `V$IM_ADOTASKS` and `DBA_INMEMORY_AIMTASKS` views enable you to track decisions made by Automatic In-Memory tasks. The `V$IM_ADOTASKDETAILS` and `DBA_INMEMORY_AIMTASKDETAILS` views describe details relating to the tasks.

**See Also:**

[Oracle Database Reference](../refrn/dynamic-performance-v-views-2.md) to learn more about `V$IM_ADOTASKS`

#### 6.2.4 Controlling Automatic In-Memory

Use the `INMEMORY_AUTOMATIC_LEVEL` initialization parameter to control Automatic In-Memory.

By default, Automatic In-Memory is set to `OFF`. Enable it by setting `INMEMORY_AUTOMATIC_LEVEL` to either `MEDIUM` or `LOW`.

##### Prerequisites

To set this parameter with `ALTER SYSTEM`, you must have the `ALTER SYSTEM` privilege.

##### To change the `INMEMORY_AUTOMATIC_LEVEL` setting:

1.  In SQL\*Plus or SQL Developer, log in to the database as a user with the necessary privileges.

2.  Specify `INMEMORY_AUTOMATIC_LEVEL` using the `ALTER SYSTEM` statement.

    The following example disables Automatic In-Memory:

        ALTER SYSTEM SET INMEMORY_AUTOMATIC_LEVEL = 'OFF' SCOPE=BOTH;

**See Also:**

[Oracle Database Reference](../refrn/INMEMORY_AUTOMATIC_LEVEL.md) to learn more about `INMEMORY_AUTOMATIC_LEVEL`

#### 6.2.5 Setting the Time Interval for Automatic In-Memory

Use the `DBMS_INMEMORY_ADMIN` package to set the time interval for the usage statistics checked by Automatic In-Memory.

By default, Automatic In-Memory checks usage statistics for the past 31 days. You can change the current setting by supplying the `AIM_STATWINDOW_DAYS` parameter to `DBMS_INMEMORY_ADMIN.AIM_SET_PARAMETER`.

##### Prerequisites

You must have administrator privileges to execute the `DBMS_INMEMORY_ADMIN.AIM_SET_PARAMETER` and `DBMS_INMEMORY_ADMIN.AIM_GET_PARAMETER` procedures.

##### Assumptions

You want to set the interval to 7 days.

##### To change the Automatic In-Memory interval setting:

1.  In SQL\*Plus or SQL Developer, log in to the database as a user with administrative privileges.

2.  Optionally, check the current setting of the `aim_statwindow_days` parameter.

    The following example calls the `DBMS_INMEMORY_ADMIN.AIM_GET_PARAMETER` procedure:

        VARIABLE b_interval NUMBER

        BEGIN
          DBMS_INMEMORY_ADMIN.AIM_GET_PARAMETER(
            DBMS_INMEMORY_ADMIN.AIM_STATWINDOW_DAYS, :b_interval);
        END;
        /

        PRINT b_interval

        B_INTERVAL
        -----------------------------
        31

3.  Change the `aim_statwindow_days` setting with the `DBMS_INMEMORY_ADMIN.AIM_SET_PARAMETER` procedure.

    The following code changes the setting to 7 days:

        BEGIN
          DBMS_INMEMORY_ADMIN.AIM_SET_PARAMETER(
            DBMS_INMEMORY_ADMIN.AIM_STATWINDOW_DAYS, 7);
        END;
        /

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_INMEMORY.md) to learn more about the `DBMS_INMEMORY_ADMIN.AIM_SET_PARAMETER` and `DBMS_INMEMORY_ADMIN.AIM_GET_PARAMETER` procedures
