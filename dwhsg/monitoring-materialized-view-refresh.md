This chapter describes how to use refresh statistics to monitor the performance of materialized view refresh operations.

This chapter contains the following topics:

- About Materialized View Refresh Statistics

- Overview of Managing Materialized View Refresh Statistics

- About Data Dictionary Views that Store Materialized View Refresh Statistics

- Collecting Materialized View Refresh Statistics

- Retaining Materialized View Refresh Statistics

- Viewing Materialized View Refresh Statistics Settings

- Purging Materialized View Refresh Statistics

- Viewing Materialized View Refresh Statistics

- Analyzing Materialized View Refresh Performance Using Refresh Statistics

### 9.1 About Materialized View Refresh Statistics

Oracle Database collects and stores statistics about materialized view refresh operations. These statistics are accessible using data dictionary views.

Statistics for both current and historical materialized view refresh operations are stored in the database. Historical materialized view refresh statistics enable you to understand and analyze materialized view refresh performance over time in your database. Refresh statistics can be collected at varying levels of granularity.

Maintaining materialized view refresh statistics provides the following:

- Reporting capabilities for materialized view refresh operations

  - Display both current and historical statistics for materialized view refresh operations

  - Display statistics on actual refresh execution times

  - Track the performance of materialized view refresh over time using statistics on actual refresh execution times

- Diagnostic capabilities for materialized view refresh performance

  Detailed current and historical statistics can be used to quickly analyze the performance of materialized view refresh operations. For example, if a materialized view takes a long time to refresh, you can use refresh statistics to determine if the slowdown is due to increased system load or vastly varying change data.

### 9.2 Overview of Managing Materialized View Refresh Statistics

Oracle Database manages the collection and retention of materialized view refresh statistics based on the defined database settings. By default, the database collects and stores basic statistics about materialized view refresh operations for the entire database.

Managing materialized view refresh statistics comprises of the defining policies that control the following:

- Level of details for materialized view refresh statistics

- Retention period of materialized view refresh statistics

Use the following techniques to define policies that manage materialized view refresh statistics:

- Define default settings that are applicable to the entire database

  The `DBMS_MVIEW_STATS.SET_SYSTEM_DEFAULT` procedure defines default settings that manage the collection and retention of materialized view refresh statistics for the entire database.

- Define collection and retention policies for individual materialized views

  The `DBMS_MVIEW_STATS.SET_MVREF_STATS_PARAMS` procedure provides more fine-grained control over materialized view refresh statistics by managing the collection and retention of statistics at the level in individual materialized views. Settings made at the materialized view level override the database-level settings.

**Note:**

- Collecting Materialized View Refresh Statistics

- Retaining Materialized View Refresh Statistics

### 9.3 About Data Dictionary Views that Store Materialized View Refresh Statistics

Oracle Database stores materialized view refresh statistics in the data dictionary. Setting the collection level for materialized view refresh controls the detail level of refresh statistics collected.

Each materialized view refresh operation is identified using a unique refresh ID. A single refresh operation could refresh multiple materialized views. For example, when the `REFRESH_DEPENDENT` procedure is used to refresh a single materialized view, all materialized views that are dependent on the specified materialized view are also refreshed as part of the same refresh operation. Thus, all the materialized views refreshed as part of this operation will have the same refresh ID.

Table 9-1 Data Dictionary Views that Store Materialized View Refresh Statistics

| View Name                | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|:-------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `DBA_MVREF_STATS`        | Stores basic statistics for a materialized view refresh such as the refresh ID and basic timing statistics for the refresh operation.<br>This view contains the following information about each materialized view for which refresh statistics are collected:<br>• name of the materialized view<br>• refresh method used<br>• number of rows in the materialized view at the beginning and end of the refresh operation<br>• number of steps used to refresh the materialized view<br>**Note:**<br>This is view populated for fast refresh of materialized views with aggregates or joins only. It is not populated for other types of materialized view refreshes. |
| `DBA_MVREF_RUN_STATS`    | Stores detailed information about each materialized view refresh operation including the following:<br>• parameters specified when running the refresh operation such as list of materialized views, refresh method, purge option, and so on.<br>• number of materialized views refreshed in the refresh operation.<br>• detailed timing statistics for the refresh operation including start time, end time, and elapsed time.                                                                                                                                                                                                                                       |
| `DBA_MVREF_CHANGE_STATS` | Contains change data load information for the base tables associated with a materialized view refresh operation.<br>The details include base table names, materialized view names, number of rows inserted, number of rows updated, number of rows deleted, number of direct-load inserts, PMOPs details, and number of rows at the beginning of the refresh operation.                                                                                                                                                                                                                                                                                               |
| `DBA_MVREF_STMT_STATS`   | Contains information related to each refresh statement that is part of a single materialized view refresh operation.<br>This includes information such as materialized view name, refresh ID, the refresh statement, SQLID of the refresh statement, and execution plan of the statement.                                                                                                                                                                                                                                                                                                                                                                             |

**See Also:**

[Oracle Database Reference](../refrn/index.md)

### 9.4 Collecting Materialized View Refresh Statistics

Oracle Database collects basic statistics about materialized view refresh operations. These statistics are stored in the data dictionary and can be used to analyze the performance of materialized view refresh operations.

**See Also:**

- About Collecting Materialized View Refresh Statistics

- Specifying Default Settings for Collecting Materialized View Refresh Statistics

- Modifying the Collection Level for Materialized View Refresh Statistics

#### 9.4.1 About Collecting Materialized View Refresh Statistics

By default, Oracle Database collects basic refresh statistics for all materialized views refresh operations.

Oracle Database enables you to control the granularity and level at which materialized view refresh statistics are collected. Statistics can be collected for all materialized views in the database or for a specific set of materialized views. If you are interested in monitoring only some materialized views in the database, then you can collect statistics at the materialized view level. Collecting refresh statistics for a selected set of materialized views is useful because refresh patterns of materialized views can vary widely.

The collection level defines the amount of statistics that the database collects for materialized view refresh operations. You can either collect basic statistics or more detailed information such as the parameters used and the SQL statements run during the materialized view refresh operation.

Use the procedures in the `DBMS_MVIEW_STATS` package to set the `COLLECTION_LEVEL` parameter, which specifies the collection level for materialized view refresh statistics. The values that can be set for the `COLLECTION_LEVEL` parameter are:

- NONE

  No statistics are collected for materialized view refresh operations.

- TYPICAL

  Only basic refresh statistics are collected for materialized view refresh operations. This is the default setting.

- ADVANCED

  Detailed statistics, including the parameters used in the refresh operation and the SQL statements that are run, are collected for materialized view refresh operations.

#### 9.4.2 Specifying Default Settings for Collecting Materialized View Refresh Statistics

The `DBMS_MVIEW_STATS.SET_SYSTEM_DEFAULT` procedure enables you to set defaults for managing the collection of materialized view refresh statistics at the database level.

You can override the system defaults by specifying different settings at the individual materialized view level. Materialized views for which the default settings are not overridden will use the system default settings.

By default, Oracle Database collects and stores basic statistics about materialized view refresh operations for the entire database. You can disable statistics collection or change the default setting by modifying the statistics collection level.

To set the default collection level for materialized view refresh statistics at the database level:

- Run the `DBMS_MVIEW_STATS.SET_SYSTEM_DEFAULT` procedure and set the `COLLECTION_LEVEL` parameter.

Example 9-1 Setting Materialized View Refresh Statistics Collection Level for the Database

This example sets the default collection level for materialized view refresh statistics to ADVANCED indicating that detailed statistics about materialized view refresh operations will be collected and stored.

    DBMS_MVIEW_STATS.SET_SYSTEM_DEFAULT ('COLLECTION_LEVEL','ADVANCED');

Example 9-2 Disabling Statistics Collection for Materialized View Refresh

This example sets the default collection level for materialized view refresh statistics to NONE thereby disabling statistics collection.

    DBMS_MVIEW_STATS.SET_SYSTEM_DEFAULT ('COLLECTION_LEVEL','NONE');

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_MVIEW_STATS.md)

#### 9.4.3 Modifying the Collection Level for Materialized View Refresh Statistics

You can modify the settings that manage the collection of materialized view refresh statistics by using the `DBMS_MVIEW_STATS.SET_MVREF_STATS_PARAMS` procedure.

You can modify the statistics collection behavior either for the entire database or for one or more materialized views. The new collection settings override the default settings made at the database level or previous settings made for the specified materialized views. For example, the system default for `COLLECTION_LEVEL` is set to TYPICAL for the database. You then use the `DBMS_MVIEW_STATS.SET_MVREF_STATS_PARAMS` procedure to modify the collection level for the materialized views `MV1` and `MV2` to ADVANCED. The remaining materialized views in the database will continue to use the TYPICAL collection level.

To modify the collection level for materialized view refresh statistics, either at the database level or materialized view level:

- Run the `DBMS_MVIEW_STATS.SET_MVREF_STATS_PARAMS` procedure and set the `COLLECTION_LEVEL` parameter to the required value

Example 9-3 Setting the Materialized View Statistics Collection Level for the Entire Database

The following example modifies the collection level for materialized view refresh statistics at the database level to TYPICAL. Specifying `NULL` instead of one or more materialized view names indicates that this setting is for the entire database.

    DBMS_MVIEW_STATS.SET_MVREF_STATS_PARAMS (NULL, 'TYPICAL');

Example 9-4 Setting the Materialized View Statistics Collection Level for Multiple Materialized Views

This example sets the collection level for the materialized views `SALES_2013_MV` and `SALES_2014_MV` in the `SH` schema to ADVANCED. The retention period is set to 60 days. This setting overrides any default settings that may have been specified at the database level.

    DBMS_MVIEW_STATS.SET_MVREF_STATS_PARAMS ('SH.SALES_2013_MV, SH.SALES_2014_MV','ADVANCED',60);

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_MVIEW_STATS.md)

### 9.5 Retaining Materialized View Refresh Statistics

Oracle Database stores the collected materialized view refresh statistics for a period of time specified by the retention period.

**See Also:**

- About Retaining Materialized View Refresh Statistics

- Specifying the Default Retention Period for Materialized View Refresh Statistics

- Modifying the Retention Period for Materialized View Refresh Statistics

#### 9.5.1 About Retaining Materialized View Refresh Statistics

The retention period defines the duration, in days, for which materialized view refresh statistics are stored in the data dictionary. Collected statistics are automatically purged after the retention period is reached.

The retention period for materialized view refresh statistics can be set either at the database level or the materialized view level. The `RETENTION_PERIOD` parameter in `DBMS_MVIEW_STATS.SET_SYSTEM_DEFAULT` or `DBMS_MVIEW_STATS.SET_MVREF_STATS_PARAMS` enables you to specify the duration for which materialized view refresh statistics must be retained in the data dictionary.

#### 9.5.2 Specifying the Default Retention Period for Materialized View Refresh Statistics

The `DBMS_MVIEW_STATS.SET_SYSTEM_DEFAULT` procedure sets defaults for managing the retention of materialized view refresh statistics at the database level.

By default, Oracle Database retains materialized view refresh statistics for 365 days from the date of collection. After the retention period is reached, the statistics are purged from the data dictionary. You can override the system default setting by specifying different settings at the individual materialized view level. Materialized views for which the default settings are not overridden will continue to use the system default settings.

You can specify that refresh statistics must never be purged from the database by setting the retention period to -1.

To specify a new default retention period for the entire database:

- Set the `RETENTION_PERIOD` parameter of the `DBMS_MVIEW_STATS.SET_SYSTEM_DEFAULT` procedure to the required number of days

Example 9-5 Setting the Retention Period for Materialized View Refresh Statistics

This example sets the default retention period for materialized view refresh statistics for the entire database to 60 days.

    DBMS_MVIEW_STATS.SET_SYSTEM_DEFAULT ('RETENTION_PERIOD',60);

Example 9-6 Preventing the Purging of Materialized View Refresh Statistics

This example sets the retention period for materialized view refresh statistics to -1 thereby ensuring that refresh statistics are not automatically purged when the default retention period is reached. When you use this setting, refresh statistics will need to be explicitly purged from the data dictionary using the `DBMS_MVIEW_STATS.PURGE_REFRESH_STATS` procedure.

    DBMS_MVIEW_STATS.SET_SYSTEM_DEFAULT ('RETENTION_PERIOD',–1);

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_MVIEW_STATS.md)

#### 9.5.3 Modifying the Retention Period for Materialized View Refresh Statistics

The `DBMS_MVIEW_STATS.SET_MVREF_STATS_PARAMS` procedure enables you to modify the retention period set for materialized view refresh statistics.

You can modify the retention period either for the entire database or for one or more materialized views. When you modify the retention period only for specific materialized views, the remaining materialized views in the database continue to use their existing retention period.

Suppose that your system default setting is to collect basic materialized view refresh statistics and retain them for 60 days. However, for a particular set of materialized views, you want to collect detailed statistics and retain these statistics for 45 days. In this case, for the specific set of materialized views, you set `COLLECTION_LEVEL` to ADVANCED and `RETENTION_PERIOD` to 45.

To modify the retention period for materialized view refresh statistics either at the database level to materialized view level:

- Run the `DBMS_MVIEW_STATS.SET_MVREF_STATS_PARAMS` procedure and set the` RETENTION_PERIOD` parameter to the required value

Example 9-7 Using Default Materialized View Refresh Statistics Settings for Retention Period

This example sets the collection level for the materialized view `SALES_MV` in the `SH` schema to TYPICAL. Since NULL is used for the retention period, the system-wide default setting for retention period is used for this materialized view.

    DBMS_MVIEW_STATS.SET_MVREF_STATS_PARAMS ('SH.SALES_MV','TYPICAL',NULL);

Example 9-8 Setting the Retention Period for a Materialized View

This example sets the collection level for the `SH.SALES_MV` to ADVANCED and the retention period to 45 days. This overrides the existing retention period set for this materialized view.

    DBMS_MVIEW_STATS.SET_MVREF_STATS_PARAMS ('SH.SALES_MV','ADVANCED',45);

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_MVIEW_STATS.md)

### 9.6 Viewing Materialized View Refresh Statistics Settings

Data dictionary views store both the default settings and materialized view-specific settings that manage materialized view refresh statistics.

To view the database-level default settings for collecting and retaining materialized view refresh statistics:

- Query the `parameter_name` and `value` columns in the `DBA_MVREF_STATS_SYS_DEFAULTS` view

To view the collection and retention settings for refresh statistics of one or more materialized views:

- Query the `parameter_name` and `value` columns in the `DBA_MVREF_STATS_PARAMS` view by filtering data using the `mv_owner` and `mv_name` columns

Example 9-9 Displaying the Database-level Default Settings for Managing Materialized View Refresh Statistics

The following query displays the database level default settings for managing materialized view refresh statistics:

    SELECT parameter_name, value from DBA_MVREF_STATS_SYS_DEFAULTS;

    PARAMETER_NAME          VALUE
    ---------------         --------
    COLLECTION_LEVEL        TYPICAL
    RETENTION_PERIOD        45

Example 9-10 Displaying the Refresh Statistics Settings for a Set of Materialized Views

The following query displays the refresh statistics settings for all the materialized view owned by the `SH` schema:

    SELECT mv_name,collection_level,retention_period
    FROM DBA_MVREF_STATS_PARAMS
    WHERE mv_owner = 'SH';

    MV_NAME         COLLECTION_LEVEL    RETENTION_PERIOD
    --------        ----------------    -----------------
    MY_RTMV                 ADVANCED                60
    NEW_SALES_RTMV          ADVANCED                45
    MY_SUM_SALES_RTMV       TYPICAL                 31
    SALES_RTMV              TYPICAL                 -1
    CAL_MONTH_SALES_MV      TYPICAL                 45

    5 rows selected.

### 9.7 Purging Materialized View Refresh Statistics

The `DBMS_MVIEW_STATS.PURGE_REFRESH_STATS` procedure enables you to explicitly purge materialized view refresh statistics that are older than a specified period from the data dictionary.

By default, materialized view refresh statistics are removed from the data dictionary after the specified retention period. Depending on your settings, the purging may be performed for the entire database or for a set of specified materialized views. You can use the `DBMS_MVIEW_STATS.PURGE_REFRESH_STATS` procedure to explicitly purge refresh statistics that are older than a specified time without altering the set retention period. Explicit purging of refresh statistics overrides the current setting for retention period but does not alter the setting.

To purge materialized view refresh statistics stored in the database:

- Run the `DBMS_MVIEW_STATS.PURGE_REFRESH_STATS` procedure.
  Specify the materialized views for which statistics must be purged and the duration beyond which statistics must be purged.

Example 9-11 Purging Refresh Statistics for a Materialized View

Assume that the retention period for refresh statistics of the materialized view `SALES_MV` is 60 days. At any given time, the refresh statistics for the previous 60 days are available. However, because of space constraints, you want to purge the statistics for the last 30 days. Use the `DBMS_MVIEW_STATS.PURGE_REFRESH_STATS` procedure to do this.

Note that the retention period set for `SALES_MV` remains unaltered. The purge is a one-time operation.

    DBMS_MVIEW_STATS.PURGE_REFRESH_STATS (’SH.SALES_MV’,30);

Example 9-12 Purging Refresh Statistics for All Materialized Views

This example purges materialized view refresh statistics that are older than 20 days for all materialized views in the database. Specifying `NULL` instead of one or more materialized views indicates that this setting is for the entire database.

    DBMS_MVIEW_STATS.PURGE_REFRESH_STATS (NULL,20);

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_MVIEW_STATS.md)

### 9.8 Viewing Materialized View Refresh Statistics

You can view both current and historical statistics for materialized view refresh operations by querying the data dictionary views that store refresh statistics.

Depending on the collection level setting, materialized view refresh statistics are stored in one or more of the following views: `DBA_MVREFS_STATS`, `DBA_MVREF_RUN_STATS`, `DBA_MVREF_CHANGE_STATS`, and `DBA_MVREF_STMT_STATS`. There are corresponding `USER_` versions for all these views. The views contain a `REFRESH_ID` column that can be used to join one or more views, when required.

**See Also:**

- Viewing Basic Refresh Statistics for a Materialized View

- Viewing Detailed Statistics for Each Materialized View Refresh Operation

- Viewing Change Data Statistics During Materialized View Refresh Operations

- Viewing the SQL Statements Associated with A Materialized View Refresh Operation

#### 9.8.1 Viewing Basic Refresh Statistics for a Materialized View

Use the `DBA_MVREF_STATS` view to display basic statistics about materialized view refresh operations.

Each materialized view refresh operation is identified using a unique refresh ID. The `DBA_MVREF_STATS` view stores the refresh ID, refresh method, names of materialized views refreshed, basic execution times, and the number of steps in the refresh operation.

To view basic refresh statistics for materialized view refresh operations:

- Query the `DBA_MVREF_STATS` view with list of required columns and use conditions to filter the required data

Example 9-13 Displaying Basic Statistics for a Materialized View Refresh Operation

The following query displays some refresh statistics for refresh operations on the `SH.NEW_SALES_RTMV` materialized view. Information includes the refresh method, refresh time, number of rows in the materialized view at the start of the refresh operation, and number of rows at the end of the refresh operation.

    SELECT refresh_id, refresh_method, elapsed_time, initial_num_rows, final_num_rows
    FROM dba_mvref_stats
    WHERE mv_name = 'NEW_SALES_RTMV' and mv_owner = 'SH';

    REFRESH_ID    REFRESH_METHOD    ELAPSED_TIME    INITIAL_NUM_ROWS    FINAL_NUM_ROWS
    ----------    --------------    -------------   ----------------    ----------------
    49            FAST              0               766                 788
    61            FAST              1               788                 788
    81            FAST              1               788                 798

    3 rows selected.

Example 9-14 Displaying Materialized Views Based on their Refresh Times

The following example displays the names of materialized views whose refresh operations took more than 10 minutes. Since `elapsed_time` is specified in seconds, we use 600 in the query.

    SELECT mv_owner, mv_name, refresh_method
    FROM dba_mvref_stats
    WHERE elapsed_time > 600;

#### 9.8.2 Viewing Detailed Statistics for Each Materialized View Refresh Operation

The `DBA_MVREF_RUN_STATS` view stores detailed statistics about materialized view refresh operation. When a refresh operation affects multiple materialized views, detailed statistics are available for all affected materialized views.

Materialized views can be refreshed using one of the following procedures in the `DBMS_MVIEW` package: `REFRESH`, `REFRESH_DEPENDENT`, or `REFRESH_ALL`. Each procedure contains different parameters that specify how the refresh must be performed. The` DBA_MVREF_RUN_STATS` view contains information about the parameters specified for the refresh operation, the number of materialized views refreshed, execution times, and log purge time.

To view detailed refresh statistics for materialized view refresh operations:

- Query the `DBA_MVREF_RUN_STATS` view with the list of required columns and use conditions to filter the required data

Example 9-15 Listing All Materialized Views Refreshed in a Single Refresh Operation

The following example displays the materialized views and refresh times for materialized views that were refreshed as part of the specified refresh ID.

    SELECT mviews, elapsed_time, complete_stats_available
    FROM dba_mvref_run_stats
    WHERE refresh_id = 100;

    MVIEWS              ELAPSED_TIME      COMPLETE_STATS_AVAIALBE
    --------            ------------      -------------------------
    "SH"."SALES_RTMV"   1                 Y

Example 9-16 Viewing the Parameters Specified During a Materialized View Refresh Operation

The following example displays the list of refreshed materialized views and some of the parameters specified during the refresh operation for refresh ID 81.

    SELECT mviews, refresh_after_errors, purge_option, parallelism, nested
    FROM dba_mvref_run_stats
    WHERE run_owner = 'SH' and refresh_id=81;

    MVIEWS                  R     PURGE_OPTION    PARALLELISM   NESTED
    ------                  -     ------------    ------------  -------
    "SH"."SALES_RTMV"   N   1       0   N

Example 9-17 Displaying Detailed Statistics for a Materialized View Refresh Operation

The following example displays detailed statistics for the refresh operation with refresh ID 156. The details include the number of materialized views refreshed, the owner and names of materialized views, and the time taken for the refresh.

    SELECT num_mvs, mv_owner, mv_name, r.elapsed_time
    FROM dba_mvref_stats s, dba_mvref_run_stats r
    WHERE s.refresh_id = r.refresh_id and refresh_id = 156;

    NUM_MVS     MV_OWNER    MV_NAME         ELAPSED_TIME
    --------    --------    --------        -----------
    1           SH          SALES_RTMV      5

**See Also:**

[Oracle Database Reference](../refrn/DBA_MVREF_RUN_STATS.md)

#### 9.8.3 Viewing Change Data Statistics During Materialized View Refresh Operations

The `DBA_MVREF_CHANGE_STATS` view stores detailed change data statistics for materialized view refresh operations. This includes the base tables that were refreshed, the number of rows inserted, number of rows updated, number of rows deleted, and partition maintenance operations (PMOPs) details.

You can join the `DBA_MVREF_CHANGE_STATS` view with other views that contain materialized view refresh statistics to provide more complete statistics.

To view detailed change data statistics for materialized view refresh operations:

- Query the `DBA_MVREF_CHANGE_STATS` view with the list of required columns and use conditions to filter the required data

Example 9-18 Determining if a Refresh Operation Resulted in PMOPs

The following example displays the base table names and PMOP details for the refresh operation with refresh ID 1876. The query output contains one record for each base table of the materialized view.

    SELECT tbl_name, mv_name, pmops_occurred, pmop_details
    FROM dba_mvref_change_stats
    WHERE refresh_id =1876;

    TBL_NAME      MV_NAME     PMOPS_OCCURRED    PMOP_DETAILS
    ---------     --------    --------------    ------------
    MY_SALES      SALES_RTMV    N

Example 9-19 Displaying the Number of Rows Modified During a Refresh Operation

This example displays the following details about each base table in a refresh operation on the `SH.MY_SALES` materialized view: number of rows in the tables, number of rows inserted, number of rows updates, number of rows deleted, number of direct load inserts, and details of PMOP operations.

    SELECT tbl_name, num_rows, num_rows_ins, num_rows_upd, num_rows_del, num_rows_dl_ins, pmops_occurred, pmop_details
    FROM dba_mvref_change_stats
    WHERE mv_name = 'MY_SALES' and mv_owner = 'SH';

**See Also:**

[Oracle Database Reference](../refrn/DBA_MVREF_CHANGE_STATS.md)

#### 9.8.4 Viewing the SQL Statements Associated with A Materialized View Refresh Operation

Query the `DBA_MVREF_STMT_STATS` view to display information about all the SQL statements used in a materialized view refresh operation.

Each refresh operation can consist of multiple steps, each of which is performed using a SQL statement. For each step in a refresh operation, you can view the step number and the SQL statement.

To view the SQL statements associated with materialized view refresh operations:

- Query the `DBA_MVREF_STMT_STATS` view with the list of required columns and use conditions to filter the required data

Example 9-20 Displaying SQL Statements for Each Step in a Refresh Operation

The following example displays the materialized view names, SQL statements used to refresh the materialized view, and execution time for the materialized view refresh operation with refresh ID is 1278.

    SELECT mv_name, step, stmt, execution_time
    FROM dba_mvref_stmt_stats
    WHERE refresh_id = 1278;

Example 9-21 Displaying Refresh Statements Used in the Current Refresh of an Materialized View

This example displays the individual SQL statements that are used to the refresh the `MY_SALES` materialized view. A single refresh operation may consist of multiple steps, each of which executes a SQL statement. The details displayed in this example include the step number, SQL ID of the SQL statement, the SQL statement that is executed, and the execution time for the SQL statement.

    SELECT step, sqlid, stmt, execution_time
    FROM DBA_MVREF_STATS M, DBA_MVREF_STMT_STATS S
    WHERE M.refresh_id = S.refresh_id and M.mv_name = 'MY_SALES'
    ORDER BY step;

**See Also:**

[Oracle Database Reference](../refrn/DBA_MVREF_STMT_STATS.md)

### 9.9 Analyzing Materialized View Refresh Performance Using Refresh Statistics

Materialized view refresh statistics that are stored in data dictionary views can be used to analyze the refresh performance of materialized views.

Refresh statistics provide detailed information that enables you to understand and analyze materialized view refresh operations and their performance. Typically, you analyze refresh statistics for critical or long running materialized view refresh operations. If a materialized view takes longer to refresh than it does normally, then you can analyze its past refresh times and change data to identify any differences that may account for the increased time (for example, 5 times more data that needs to be refreshed this time).

To analyze materialized view refresh performance:

1.  Set the collection level and retention period for the materialized view to collect refresh statistics over a period of time.
    You can set these at the database level or at the materialized view level.
2.  Identify the materialized views whose refresh performance needs to be analyzed.
    Typically, you would be interested in analyzing the refresh performance of a specific set of materialized views in the database. In this case, you can modify the refresh statistics settings for these materialized views as per your requirement.
3.  Where multiple refresh operations take place over a period of time (for the materialized views you want to analyze), Oracle Database collects the desired refresh statistics.
4.  Query the data dictionary views that store refresh statistics and analyze the refresh behavior of materialized views of interest over time to understand refresh behavior.
    The database stores both historical and current statistics which can be analyzed to understand refresh behavior.
