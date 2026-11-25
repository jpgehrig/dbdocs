## 129  DBMS_PERF

The DBMS_PERF package provides and interface to generate active reports for monitoring database performance

**See Also:**

Oracle Database PL/SQL Language Reference for more information about ["Avoiding SQL Injection in PL/SQL"](../lnpls/sql-injection.md)

This chapter contains the following topics:

- Overview

- Security Model

- Summary of DBMS_PERF Subprograms

### 129.1  DBMS_PERF Overview

The DBMS_PERF package provides an interface for generating database performance reports. All subprograms return an active report and these reports can be generated at the system level, session level or at SQL level.

### 129.2 DBMS_PERF Security Model

The DBMS_PERF package requires the DBA role.

### 129.3 Summary of DBMS_PERF Subprograms

This table lists the `DBMS_PERF` subprograms and briefly describes them.

Table 129-1 DBMS_PERF Package Subprograms

| Subprogram              | Description                                                                                                                         |
|:------------------------|:------------------------------------------------------------------------------------------------------------------------------------|
| REPORT_PERFHUB Function | Generates a composite active performance report of the entire database system for a specified time period                           |
| REPORT_SESSION Function | Generates a performance report for a specific database session where a session is identified by `inst_id`, `sid`, and `serial_num`. |
| REPORT_SQL Function     | Generates an active performance report for a particular SQL statement identified by its `sql_id`.                                   |

#### 129.3.1 REPORT_PERFHUB Function

This function generates a composite active performance report of the entire database system for a specified time period.

##### Syntax

    DBMS_PERF.REPORT_PERFHUB (
       is_realtime          IN NUMBER   DEFAULT NULL,
       outer_start_time     IN DATE     DEFAULT NULL,
       outer_end_time       IN DATE     DEFAULT NULL,
       selected_start_time  IN DATE     DEFAULT NULL,
       selected_end_time    IN DATE     DEFAULT NULL,
       inst_id              IN NUMBER   DEFAULT NULL,
       dbid                 IN NUMBER   DEFAULT NULL,
       monitor_list_detail  IN NUMBER   DEFAULT NULL,
       workload_sql_detail  IN NUMBER   DEFAULT NULL,
       addm_task_detail     IN NUMBER   DEFAULT NULL,
       report_reference     IN VARCHAR2 DEFAULT NULL,
       report_level         IN VARCHAR2 DEFAULT NULL,
       type                 IN VARCHAR2 DEFAULT 'ACTIVE',
       base_path            IN VARCHAR2 DEFAULT NULL);
     RETURN CLOB;

##### Parameters

Table 129-2 REPORT_PERFHUB Function Parameters

| Parameter             | Description                                                                                                                                                                                                                                                             |
|:----------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `is_realtime`         | If 1, then real-time. If `NULL` (default) or `0`, then historical mode.                                                                                                                                                                                                 |
| `outer_start_time`    | Start time of outer period shown in the time selector. If `NULL` (default):<br>• If `is_realtime`=`0` (historical), then 24 hours before `outer_end_time`.<br>• If `is_realtime`=`1` (realtime mode), then 1 hour before `outer_end_time`.                              |
| `outer_end_time`      | End time of outer period shown in the time selector. If `NULL` (default), then latest AWR snapshot.<br>• If `is_realtime`=`0` (historical), then the latest AWR snapshot<br>• If `is_realtime`=`1` (realtime mode), this is the current time (and any input is ignored) |
| `selected_start_time` | Start time period of selection. If `NULL` (default)<br>• If `is_realtime`=`0`, then 1 hour before `selected_end_time`<br>• If `is_realtime`=`1`, then 5 minutes before `selected_end_time`                                                                              |
| `selected_end_time`   | End time period of selection. If `NULL` (default)<br>• If `is_realtime`=`0`, then latest AWR snapshot<br>• `If is_realtime`=`1`, then current time                                                                                                                      |
| `inst_id`             | Instance ID to for which to retrieve data<br>• If `-1`, then current instance<br>• If number is specified, then for that instance<br>• If `NULL` (default), then all instances                                                                                          |
| `dbid`                | `DBID` to query.<br>• If `NULL`, then current `DBID`.<br>• If `is_realtime`=`1`, then `DBID` must be the local `DBID`.                                                                                                                                                  |
| `monitor_list_detail` | Top N in SQL monitor list for which to retrieve SQL monitor details.<br>• If `NULL` (default), then retrieves top 10<br>• If `0`, then retrieves no monitor list details                                                                                                |
| `workload_sql_detail` | Top N in Workload Top SQL list to retrieve monitor details,<br>• If `NULL` (default), then retrieves top 10<br>• If `0`, then retrieves no monitor list details                                                                                                         |
| `addm_task_detail`    | Maximum N latest ADDM tasks to retrieve<br>• If `NULL` (default), retrieves available data but no more than N<br>• If `0`, then retrieves no ADDM task details                                                                                                          |
| `report_reference`    | Must be `NULL` when used from SQL\*Plus.                                                                                                                                                                                                                                |
| `report_level`        | `'typical'` will get all tabs in performance hub                                                                                                                                                                                                                        |
| `type`                | Report type:<br>• `'ACTIVE'` (default)<br>• `'xml'` returns XML                                                                                                                                                                                                         |
| `base_path`           | URL path for HTML resources since flex HTML requires access to external files. This is only valid for type='`ACTIVE'` and is typically not used. Default value will retrieve the required files from OTN.                                                               |

##### Usage Notes

- Once a time period is selected, the performance information is collected and presented based on performance subject areas.

- The time period can be real-time or historical.

- When real-time data is selected, more granular data is presented because data points are available every minute.

- When historical data is selected, more detailed data (broken down by different metrics) is presented, but the data points are averaged out to the Automatic Workload Repository (AWR) interval (usually an hour).

- Different tabs are available in the Performance Hub, depending on whether is_real-time is 1 for real time mode or 0 for historical mode.

#### 129.3.2 REPORT_SESSION Function

This function produces a performance report for a specific database session where a session is identified by `inst_id`, `sid`, and`serial_num`.

If any of those parameters are missing, then the report is for the current session.

The session-level performance report contains the following tabs:

- Summary - This tab contains key identifiers and attributes of the session along with a summary of its activity data. It also contains a list of SQLs, PLSQL blocks and Database Operations (DBOP) executed by that session that were monitored by Real-time SQL Monitoring.

- Activity - This tab shows activity broken down by wait classes for this session. The data used for this chart is fetched from Active Session History (ASH).

- Metrics - This tab shows charts for certain key metrics for the selected session over time and is only available in historical mode. Some of the metrics shown are CPU usage, PGA usage, IO Throughput and IO Requests.

##### Syntax

    DBMS_PERF.REPORT_SESSION (
        inst_id              IN NUMBER   DEFAULT NULL,
        sid                  IN NUMBER   DEFAULT NULL,
        serial               IN NUMBER   DEFAULT NULL,
        is_realtime          IN NUMBER   DEFAULT NULL,
        outer_start_time     IN DATE     DEFAULT NULL,
        outer_end_time       IN DATE     DEFAULT NULL,
        selected_start_time  IN DATE     DEFAULT NULL,
        selected_end_time    IN DATE     DEFAULT NULL,
        dbid                 IN NUMBER   DEFAULT NULL,
        monitor_list_detail  IN NUMBER   DEFAULT NULL,
        report_reference     IN VARCHAR2 DEFAULT NULL,
        report_level         IN VARCHAR2 DEFAULT NULL,
        type                 IN VARCHAR2 DEFAULT 'ACTIVE',
        base_path            IN VARCHAR2 DEFAULT NULL)
      RETURN CLOB;

##### Parameters

Table 129-3 REPORT_SESSION Function Parameters

| Parameter             | Description                                                                                                                                                                                                                                                             |
|:----------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `inst_id`             | Instance ID to for which to retrieve data. If `NULL` (default), then instance of current session.                                                                                                                                                                       |
| `sid`                 | Session ID for which to retrieve performance. If `NULL`, uses current session.                                                                                                                                                                                          |
| `serial`              | Serial# of session. If `NULL`, then the serial# of the specified `sid` is used provided the session is connected.                                                                                                                                                       |
| `is_realtime`         | If 1, then real-time. If `NULL` (default) or `0`, then historical mode.                                                                                                                                                                                                 |
| `outer_start_time`    | Start time of outer period shown in the time selector. If `NULL` (default):<br>• If `is_realtime`=`0` (historical), then 24 hours before `outer_end_time`.<br>• If `is_realtime`=`1` (realtime mode), then 1 hour before `outer_end_time`.                              |
| `outer_end_time`      | End time of outer period shown in the time selector. If `NULL` (default), then latest AWR snapshot.<br>• If `is_realtime`=`0` (historical), then the latest AWR snapshot<br>• If `is_realtime`=`1` (realtime mode), this is the current time (and any input is ignored) |
| `selected_start_time` | Start time period of selection. If `NULL` (default)<br>• If `is_realtime`=`0`, then 1 hour before `selected_end_time`<br>• If `is_realtime`=`1`, then 5 minutes before `selected_end_time`                                                                              |
| `selected_end_time`   | End time period of selection. If `NULL` (default)<br>• If `is_realtime`=`0`, then latest AWR snapshot<br>• If `is_realtime`=`1`, then current time                                                                                                                      |
| `dbid`                | `DBID` to query.<br>• If `NULL`, then current `DBID`.<br>• If `is_realtime`=`1`, then `DBID` must be the local `DBID`.\\                                                                                                                                                |
| `monitor_list_detail` | Top N in SQL monitor list for which to retrieve SQL monitor details.<br>• If `NULL` (default), then retrieves top 10<br>• If `0`, then retrieves no monitor list details                                                                                                |
| `report_reference`    | Must be `NULL` when used from SQL\*Plus.                                                                                                                                                                                                                                |
| `report_level`        | `'typical'` will get all tabs in the session hub (or session details)                                                                                                                                                                                                   |
| `type`                | Report type:<br>• `'ACTIVE'` (default)<br>• `'xml'` returns XML                                                                                                                                                                                                         |
| `base_path`           | URL path for HTML resources since flex HTML requires access to external files                                                                                                                                                                                           |

#### 129.3.3 REPORT_SQL Function

This function generates an active performance report for a particular SQL statement identified by its `sql_id`.

The SQL-level performance report contains the following tabs:

- Summary - This tab contains an overview of the SQL statement with key attributes like the SQL text, user name, sessions executing it, and related information. It also contains a Plans tab which shows statistics and activity for each distinct plan for this SQL statement found in memory and in the AWR.

- Activity - This tab shows activity broken down by wait classes for this SQL statement. The data used for this chart is fetched from Active Session History (ASH).

- Execution Statistics - This tab shows statistics and activity for each distinct plan for this statement along with a graphical and tabular representation of the plan.

- Monitored SQL - All executions of this SQL statement that were monitored by Real-time SQL Monitoring are listed in this tab.

- Plan Control - This tab shows information about SQL Profiles and SQL Plan Baselines if they exist for this SQL statement.

- Historical Statistics - This tab is available only in Historical mode. It contains statistics, such as number of executions, number of I/Os, rows processed, and other information produced over time for different execution plans. This information is retrieved from AWR.

##### Syntax

    DBMS_PERF.REPORT_SQL (
        sql_id               IN varchar2 default null,
        is_realtime          IN number   default null,
        outer_start_time     IN date     default null,
        outer_end_time       IN date     default null,
        selected_start_time  IN date     default null,
        selected_end_time    IN date     default null,
        inst_id              IN number   default null,
        dbid                 IN number   default null,
        monitor_list_detail  IN number   default null,
        report_reference     IN varchar2 default null,
        report_level         IN varchar2 default null,    type                 IN varchar2 default 'ACTIVE',
        base_path            IN varchar2 default null);
      RETURN CLOB;

##### Parameters

Table 129-4 REPORT_SQL Function Parameters

| Parameter             | Description                                                                                                                                                                                                                                                             |
|:----------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `sql_id`              | `SQL_ID` for which to retrieve performance. If `NULL`, gets SQL details for the last executed SQL statement.                                                                                                                                                            |
| `is_realtime`         | If 1, then real-time. If `NULL` (default) or `0`, then historical mode.                                                                                                                                                                                                 |
| `outer_start_time`    | Start time of outer period shown in the time selector. If `NULL` (default):<br>• If `is_realtime`=`0` (historical), then 24 hours before `outer_end_time`.<br>• If `is_realtime`=`1` (realtime mode), then 1 hour before `outer_end_time`.                              |
| `outer_end_time`      | End time of outer period shown in the time selector. If `NULL` (default), then latest AWR snapshot.<br>• If `is_realtime`=`0` (historical), then the latest AWR snapshot<br>• If `is_realtime`=`1` (realtime mode), this is the current time (and any input is ignored) |
| `selected_start_time` | Start time period of selection. If `NULL` (default)<br>• If `is_realtime`=`0`, then 1 hour before `selected_end_time`<br>• If `is_realtime`=`1`, then 5 minutes before `selected_end_time`                                                                              |
| `selected_end_time`   | End time period of selection. If `NULL` (default)<br>• If `is_realtime`=`0`, then latest AWR snapshot<br>• If `is_realtime`=`1`, then current time                                                                                                                      |
| `inst_id`             | Instance ID to for which to retrieve data. If `NULL` (default), then instance of current session.                                                                                                                                                                       |
| `dbid`                | `DBID` to query.<br>• If `NULL`, then current `DBID`.<br>• If `is_realtime`=`1`, then `DBID` must be the local `DBID`.\\                                                                                                                                                |
| `monitor_list_detail` | Top N in SQL monitor list for which to retrieve SQL monitor details.<br>• If `NULL` (default), then retrieves top 10<br>• If `0`, then retrieves no monitor list details                                                                                                |
| `report_reference`    | Must be `NULL` when used from SQL\*Plus.                                                                                                                                                                                                                                |
| `report_level`        | `'typical'` will get all tabs in performance hub                                                                                                                                                                                                                        |
| `type`                | Report type:<br>• `'ACTIVE'` (default)<br>• `'xml'` returns XML                                                                                                                                                                                                         |
| `base_path`           | URL path for HTML resources since flex HTML requires access to external files                                                                                                                                                                                           |
