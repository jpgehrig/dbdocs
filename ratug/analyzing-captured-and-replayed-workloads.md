This chapter describes how to analyze captured and replayed workloads using various Database Replay reports. This chapter contains the following sections:

- Using Workload Capture Reports

- Using Workload Replay Reports

- Using Replay Compare Period Reports

- Using SQL Performance Analyzer Reports

**Note:**

After the replay analysis is complete, you can restore the database to its original state at the time of workload capture and repeat workload replay to test other changes to the system once the workload directory object is backed up to another physical location.

### Using Workload Capture Reports

Workload capture reports contain captured workload statistics, information about the top session activities that were captured, and any workload filters used during the capture process.

The following sections describe how to generate and utilize workload capture reports:

- Accessing Workload Capture Reports Using Enterprise Manager

- Generating Workload Capture Reports Using APIs

- Reviewing Workload Capture Reports

#### Accessing Workload Capture Reports Using Enterprise Manager

This section describes how to generate a workload capture report using Oracle Enterprise Manager.

The primary tool for generating workload capture reports is Oracle Enterprise Manager. If for some reason Oracle Enterprise Manager is unavailable, you can generate workload capture reports using APIs, as described in "Generating Workload Capture Reports Using APIs".

##### To access workload capture reports using Enterprise Manager:

1.  From the Enterprise menu of the Enterprise Manager Cloud Control console, select Quality Management, then Database Replay.
    If the Database Login page appears, log in as a user with administrator privileges.

    The Database Replay page appears.
2.  From the Captured Workloads tab of the Database Replay page for a capture that has a Status other than Completed, click the name of the desired capture from the Capture table.
    The Summary tab of the Database Replay page appears.
3.  Click the Reports tab for access to controls for the Workload Capture report and Workload Capture ASH Analytics report.
    - The Workload Capture report contains detailed output showing the type of data components that were captured and not captured.

    - The Capture ASH Analytics report shows which sessions are consuming the most database time. This report provides a stacked chart to help you visualize the active session activity for several dimensions, such as Event, Activity Class, Module/Action, Session, Instance ID, and PL/SQL function.

      The "Other Activity" list choice for the report means that the activity has not been captured.
4.  After you access a report, you can save it by clicking Save.
    **See Also:**

    - "Reviewing Workload Capture Reports" for information about how to interpret the workload capture report

    - [Oracle Database Performance Tuning Guide](../tgdba/analyzing-sampled-data.md) for information about ASH (Active Session History)

#### Generating Workload Capture Reports Using APIs

You can generate a workload capture report using the `DBMS_WORKLOAD_CAPTURE` package. You can also use Oracle Enterprise Manager to generate a workload capture report, as described in "Accessing Workload Capture Reports Using Enterprise Manager".

##### To generate a report on the latest workload capture:

1.  Use the `DBMS_WORKLOAD_CAPTURE`.`GET_CAPTURE_INFO` procedure.

    The `GET_CAPTURE_INFO` procedure retrieves all information regarding the workload capture and returns the `cap_id` for the workload capture. This function uses the `dir` required parameter, which specifies the name of the workload capture directory object.

2.  Call the `DBMS_WORKLOAD_CAPTURE.REPORT` function.

    The `REPORT` function generates a report using the `cap_id` that was returned by the `GET_CAPTURE_INFO` procedure. This function uses the following parameters:

    - The `capture_id` required parameter relates to the directory that contains the workload capture for which the report will be generated. The directory should be a valid directory in the host system containing the workload capture. The value of this parameter should match the `cap_id` returned by the `GET_CAPTURE_INFO` procedure.

    - The `format` required parameter specifies the report format. Valid values include `DBMS_WORKLOAD_CAPTURE`.`TYPE_TEXT` and `DBMS_WORKLOAD_REPLAY`.`TYPE_HTML`.

In this example, the `GET_CAPTURE_INFO` procedure retrieves all information regarding the workload capture in the `jul14` directory and returns the `cap_id` for the workload capture. The `REPORT` function then generates a text report using the `cap_id` that was returned by the `GET_CAPTURE_INFO` procedure.

    DECLARE
      cap_id         NUMBER;
      cap_rpt        CLOB;
    BEGIN
      cap_id  := DBMS_WORKLOAD_CAPTURE.GET_CAPTURE_INFO(dir => 'jul14');
      cap_rpt := DBMS_WORKLOAD_CAPTURE.REPORT(capture_id => cap_id,
                               format => DBMS_WORKLOAD_CAPTURE.TYPE_TEXT);
    END;
    /

**See Also:**

- "Reviewing Workload Capture Reports" for information about how to interpret the workload capture report

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_WORKLOAD_CAPTURE.md) for information about the `DBMS_WORKLOAD_CAPTURE` package

#### Reviewing Workload Capture Reports

The workload capture report contains various types of information that can be used to assess the validity of the workload capture. Using the information provided in this report, you can determine if the captured workload:

- Represents the actual workload you want to replay

- Does not contain any workload you want to exclude

- Can be replayed

The information contained in the workload capture report is divided into the following categories:

- Details about the workload capture (such as the name of the workload capture, defined filters, date, time, and SCN of capture)

- Overall statistics about the workload capture (such as the total DB time captured, and the number of logins and transactions captured) and the corresponding percentages with respect to total system activity

- Profile of the captured workload

- Profile of the uncaptured workload due to version limitations

- Profile of the uncaptured workload that was excluded using defined filters

- Profile of the uncaptured workload that consists of background process or scheduled jobs

### Using Workload Replay Reports

Workload replay reports contain information that can be used to measure performance differences between the capture system and the replay system.

The following sections describe how to generate and review workload replay reports:

- Accessing Workload Replay Reports Using Enterprise Manager

- Generating Workload Replay Reports Using APIs

- Reviewing Workload Replay Reports

#### Accessing Workload Replay Reports Using Enterprise Manager

This section describes how to generate a workload replay report using Oracle Enterprise Manager.

The primary tool for generating workload replay reports is Oracle Enterprise Manager. If for some reason Oracle Enterprise Manager is unavailable, you can generate workload replay reports using APIs, as described in "Generating Workload Replay Reports Using APIs"

##### To access workload replay reports using Enterprise Manager:

1.  From the Enterprise menu of the Enterprise Manager Cloud Control console, select Quality Management, then Database Replay.
    If the Database Login page appears, log in as a user with administrator privileges.

    The Database Replay page appears.
2.  Click the Replay Tasks tab, then select a replay for which you want to access reports.
3.  Click the Reports tab to gain access to individual reports.
    There are several types of reports you can view for a completed workload replay:

    - Database Replay

      Use this report to view complete replay statistics in a tabular format, including replay divergence and the workload profile.

      ![Description of dbr_replay_replay_rep.gif follows](img/dbr_replay_replay_rep.gif)
      [Description of the illustration dbr_replay_replay_rep.gif](img_text/dbr_replay_replay_rep.md)

    - Compare Period ADDM

      Use this report to perform a high-level comparison of one workload replay to its capture or to another replay of the same capture. Only workload replays that contain at least 5 minutes of database time can be compared using this report.

      ![Description of dbr_replay_addm_rep.gif follows](img/dbr_replay_addm_rep.gif)
      [Description of the illustration dbr_replay_addm_rep.gif](img_text/dbr_replay_addm_rep.md)
      Examine the following sections of the report to understand the performance change between the two periods and the cause of the change:

      - Overview

        This portion of the report shows SQL commonality, which is the comparability between the base and comparison periods based on the average resource consumption of the SQL statements common to both periods.

        A commonality value of 100% means that the workload "signature" in both time periods is identical. A commonality of 100% is expected for this use case, because the workload being replayed is the same (assuming that you are not using replay filters). A value of 0% means that the two time periods have no items in common for the specific workload dimension.

        Commonality is based on the type of input (that is, which SQL is executing) as well as the load of the executing SQL statements. Consequently, SQL statements running in only one time period, but not consuming significant time, do not affect commonality. Therefore, two workloads could have a commonality of 100% even if some SQL statements are running only in one of the two periods, provided that these SQL statements do not consume significant resources.

      - Configuration

        The information displayed shows base period and comparison period values for various parameters categorized by instance, host, and database.

      - Findings

        The findings can show performance improvements and identify the major performance differences caused by system changes. For negative outcomes, if you understand and remove the cause, the negative outcome can be eliminated.

        The values shown for the Base Period and Comparison Period represent performance with regard to database time.

        The Change Impact value represents a measurement of the scale of a change in performance from one time period to another. It is applicable to issues or items measured by the total database time they consumed in each time period. The absolute values are sorted in descending order.

        If the value is positive, an improvement has occurred, and if the value is negative, a regression has occurred. For instance, a change impact of -200% means that period 2 is three times as slow as period 1.

        You can run performance tuning tools, such as ADDM and the SQL Tuning Advisor, to fix issues in the comparison period to improve general system performance.

      - Resources

        The information shown provides a summary of the division of database time for both time periods, and shows the resource usage for CPU, memory, I/O, and interconnect (Oracle RAC only).

    - SQL Performance Analyzer

      Use this report to compare a SQL tuning set from a workload capture to another SQL tuning set from a workload replay, or two SQL tuning sets from two workload replays. Comparing SQL tuning sets with Database Replay provides more information than SQL Performance Analyzer test-execute, because it considers and shows all execution plans for each SQL statement, while SQL Performance Analyzer test-execute generates only one execution plan per SQL statement for each SQL trial.

    - Replay Compare Period

      Use this report to compare the AWR data from one workload replay to its capture or to another replay of the same capture. Before running this report, AWR data for the captured or replayed workload must have been previously exported.

      ![Description of dbr_replay_compare_per_rep.gif follows](img/dbr_replay_compare_per_rep.gif)
      [Description of the illustration dbr_replay_compare_per_rep.gif](img_text/dbr_replay_compare_per_rep.md)
      For information about using this report, see "Reviewing Replay Compare Period Reports".

    - Replay ASH Analytics

      The Replay ASH Analytics report contains active session history (ASH) information for a specified duration of a workload that was replayed for the category you selected in the drop-down menu. Before running this report, AWR data must have been previously exported from the captured or replayed workload.

      ![Description of dbr_replay_ash_anal_rep.gif follows](img/dbr_replay_ash_anal_rep.gif)
      [Description of the illustration dbr_replay_ash_anal_rep.gif](img_text/dbr_replay_ash_anal_rep.md)
      The chart shows workload activity breakdown values for wait classes, and provides detailed statistics for the top activity sessions that are adversely affecting the system.

      You can optionally use the Load Map for a graphical view of system activity. The Load Map is useful for viewing activity in a single- or multi-dimensional layout when you are not interested in seeing how activity has changed over time within the selected period.

    **See Also:**

    [Oracle Database 2 Day + Performance Tuning Guide](../tdppt/resolving-performance-degradation-over-time.md) for information about how to interpret replay compare period reports

#### Generating Workload Replay Reports Using APIs

You can generate a workload replay report using the `DBMS_WORKLOAD_REPLAY` package. You can also use Oracle Enterprise Manager to generate a workload replay report, as described in "Accessing Workload Replay Reports Using Enterprise Manager".

##### To generate a report on the latest workload replay for a workload capture using APIs:

1.  Retrieve information about the workload captures and the history of the workload replay attempts from the replay directory object by calling the `DBMS_WORKLOAD_REPLAY`.`GET_REPLAY_INFO` function, as described in "[Retrieving Information About Workload Replays](replaying-a-database-workload.md)".

    The `GET_REPLAY_INFO` function returns the `cap_id` of a single capture directory (for a consolidated capture directory, the `cap_id` returned is 0).

2.  Using the `cap_id` that was returned by the `GET_REPLAY_INFO` function, run a query to return the appropriate `rep_id` for the latest replay of the workload.

3.  Call the `DBMS_WORKLOAD_REPLAY.REPORT` function.

    The `REPORT` function generates a report using the `rep_id` that was returned by the `SELECT` statement.

    The `REPORT` function uses the following parameters:

    - The `replay_id` required parameter specifies the directory that contains the workload replay for which the report will be generated. The directory should be a valid directory in the host system containing the workload replay. The value of this parameter should match the `rep_id` returned by the previous query.

    - The `format` parameter required parameter specifies the report format. Valid values include `DBMS_WORKLOAD_REPLAY`.`TYPE_TEXT`, `DBMS_WORKLOAD_REPLAY`.`TYPE_HTML`, and `DBMS_WORKLOAD_REPLAY`.`TYPE_XML`.

In this example, the `GET_REPLAY_INFO` function retrieves all information about the workload captures and the history of all the workload replay attempts from the `jul14` replay directory object. The function returns the `cap_id` of the capture directory, which can be associated with the `CAPTURE_ID` column in the `DBA_WORKLOAD_REPLAYS` view to access the information retrieved.The `SELECT` statement returns the appropriate `rep_id` for the latest replay of the workload. The `REPORT` function then generates a HTML report using the `rep_id` that was returned by the `SELECT` statement.

    DECLARE
      cap_id         NUMBER;
      rep_id         NUMBER;
      rep_rpt        CLOB;
    BEGIN
      cap_id := DBMS_WORKLOAD_REPLAY.GET_REPLAY_INFO(replay_dir => 'jul14');
      /* Get the latest replay for that capture */
      SELECT max(id)
      INTO   rep_id
      FROM   dba_workload_replays
      WHERE  capture_id = cap_id;

      rep_rpt := DBMS_WORKLOAD_REPLAY.REPORT(replay_id => rep_id,
                               format => DBMS_WORKLOAD_REPLAY.TYPE_HTML);
    END;
    /

**See Also:**

- "Reviewing Workload Replay Reports" for information about how to interpret the workload replay report

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_WORKLOAD_REPLAY.md) for information about the `DBMS_WORKLOAD_REPLAY` package

#### Reviewing Workload Replay Reports

After the workload is replayed on a test system, there may be some divergence in what is replayed compared to what was captured. There are numerous factors that can cause replay divergence, which can be analyzed using the workload replay report. The information contained in the workload replay report consists of performance and replay divergence.

Performance divergence may result when new algorithms are introduced in the replay system that affect the overall performance of the database. For example, if the workload is replayed on a newer version of Oracle Database, a new algorithm may cause specific requests to run faster, and the divergence will appear as a faster execution. In this case, this is a desirable divergence.

Data divergence occurs when the results of DML or SQL queries do not match results that were originally captured in the workload. For example, a SQL statement may return fewer rows during replay than those returned during capture.

Error divergence occurs when a replayed database call:

- Encounters a new error that was not captured

- Does not encounter an error that was captured

- Encounters a different error from what was captured

The information contained in the workload replay report is divided into the following categories:

- Details about the workload replay and the workload capture, such as job name, status, database information, duration and time of each process, and the directory object and path

- Replay options selected for the workload replay and the number of replay clients that were started

- Overall statistics about the workload replay and the workload capture (such as the total DB time captured and replayed, and the number of logins and transactions captured and replayed) and the corresponding percentages with respect to total system activity

- Profile of the replayed workload

- Replay divergence

- Error divergence

- DML and SQL query data divergence

Starting with Oracle Database Release 19c, the workload replay report provides information that is required to diagnose a slow workload replay. The information contained in the workload replay report has the following additional sections:

- Replay Sessions

- Synchronization

- Tracked Commits

- Session Failures

##### Replay Sessions

The Replay Sessions section includes statistics about the ongoing and completed replay sessions, such as top events, top slowest replay sessions, and top fastest replay sessions. The statistics related to the ongoing replay sessions are shown only when the replay is in progress. Use the information in this section to understand the top events for the ongoing and completed replay sessions, the replay sessions that were slower than the capture, and a comparison of the session elapsed time between the capture and replay.

##### Synchronization

During a workload replay, the execution order of the captured SQL statements is preserved. When a SQL statement’s execution is delayed or blocked during the replay, the result is a slower workload replay.

The Synchronization section contains information about the sessions that are blocking the execution of one of the synchronized SQL statements. This information is shown only when a SQL statement’s execution is blocked. Use the information in this section to understand why a workload replay is blocked or is slower than the workload capture. This section also includes the top events and the top SQL statements with top events related to sessions that are running synchronized SQL statements.

##### Tracked Commits

The commits executed during a workload capture and the time consumed between their executions are tracked by the Database Replay. It can detect slow commits and identify the parts of the captured workload that slowed down the workload replay.

The Tracked Commits section includes information about the number of captured commits and the time at which a commit was executed. Use this information to find whether the workload replay is moving slower than the workload capture.

##### Session Failures

When the workload replay of a user session fails, the replay of the remaining calls in the session are skipped. The Session Failures section includes information about the SQL statement that was executed during a session failure, the file ID and the call counter of the failed session, and the total number of calls that were not executed.

### Using Replay Compare Period Reports

Replay compare period reports can be used for several purposes. For example, you can use replay compare period reports to compare the performance of:

- A workload replay to its workload capture

- A workload replay to another replay of the same workload capture

- Multiple workload captures to a consolidated replay

The following sections describe how to generate and review replay compare period reports:

- Generating Replay Compare Period Reports Using APIs

- Reviewing Replay Compare Period Reports

**See Also:**

- [Using Consolidated Database Replay](using-consolidated-database-replay.md) for information about Consolidated Database Replay

#### Generating Replay Compare Period Reports Using APIs

This section describes how to generate replay compare period reports using the `DBMS_WORKLOAD_REPLAY` package. This report only compares workload replays that contain at least 5 minutes of database time.

To generate replay compare period reports, use the `DBMS_WORKLOAD_REPLAY`.`COMPARE_PERIOD_REPORT` procedure:

    BEGIN
      DBMS_WORKLOAD_REPLAY.COMPARE_PERIOD_REPORT (
                               replay_id1 => 12,
                               replay_id2 => 17,
                               format => DBMS_WORKLOAD_CAPTURE.TYPE_HTML,
                               result => :report_bind);
    END;
    /

In this example, the `COMPARE_PERIOD_REPORT` procedure generates a replay compare period report in HTML format that compares a workload replay with a replay ID of 12 with another replay with an ID of 17.

The `COMPARE_PERIOD_REPORT` procedure in this example uses the following parameters:

- The `replay_id1` parameter specifies the numerical identifier of the workload replay after change for which the reported will be generated. This parameter is required.

- The `replay_id2` parameter specifies the numerical identifier of the workload replay before change for which the reported will be generated. If unspecified, the comparison will be performed with the workload capture.

- The `format` parameter specifies the report format. Valid values include `DBMS_WORKLOAD_CAPTURE`.`TYPE_HTML` for HTML and `DBMS_WORKLOAD_CAPTURE`.`TYPE_XML` for XML. This parameter is required.

- The result parameter specifies the output of the report.

**See Also:**

- "Reviewing Replay Compare Period Reports" for information about how to interpret the replay compare period report

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_WORKLOAD_REPLAY.md) for information about the `DBMS_WORKLOAD_REPLAY` package

#### Reviewing Replay Compare Period Reports

Reviewing replay compare period reports enables you to determine if any replay divergence occurred and whether there were any significant performance changes.

Depending on the type of comparison that is being made, one of three types of replay compare period reports is generated:

- Capture vs. Replay

  This report type compares the performance of a workload replay to its workload capture.

- Replay vs. Replay

  This report type compares the performance of two workload replays of the same workload capture.

- Consolidated Replay

  This report type compares the performance of multiple workload captures to a consolidated replay. Only the ASH Data Comparison section is available for this report type. For more information about this report type, see "[Reporting and Analysis for Consolidated Database Replay](using-consolidated-database-replay.md)".

All replay compare period report types contain information about the most important changes between the two runs that are being compared. Use this information to determine the appropriate action to take. For example, if a new concurrency issue is found, review Automatic Database Diagnostic Monitor (ADDM) reports to diagnose the issue. If a new SQL performance problem is found, run SQL Tuning Advisor to fix the problem.

The information in the replay compare period report is divided into the following sections:

- General Information

- Replay Divergence

- Main Performance Statistics

- Top SQL/Call

- Hardware Usage Comparison

- ADDM Comparison

- ASH Data Comparison

##### General Information

This section contains metadata about the two runs being compared in the report. Any `init.ora` parameter changes between the two runs are also shown here. Review this section to verify if the system change being tested was performed.

##### Replay Divergence

This section contains the divergence analysis of the second run relative to the first. If the analysis shows significant divergence, review the full divergence report.

##### Main Performance Statistics

This section contains a high-level performance statistic comparison across the two runs (such as change in database time). If the comparison shows an insignificant change in database time, then the performance between the two runs are generally similar. If there is a significant change in database time, review the statistics to determine the component (CPU or user I/O) that is causing the greatest change.

##### Top SQL/Call

This section compares the performance change of individual SQL statements from one run to the next. The SQL statements are ordered by the total change in database time. Top SQL statements that regressed by the most database time are best candidates for SQL tuning.

##### Hardware Usage Comparison

This section compares CPU and I/O usage across the two runs. The number of CPUs is summed for all instances and CPU usage is averaged over instances.

I/O statistics are shown for data and temp files. A high value for the single block read time (much higher than 10 milliseconds) suggests that the system is I/O bound. If this is the case, then review the total read and write times to determine if the latency is caused by excessive I/O requests or poor I/O throughput.

##### ADDM Comparison

This section contains a comparison of ADDM analyses across the two runs ordered by the absolute difference in impact. Compare the ADDM results for the two runs to identify possible problems that only existed in one run. If the system change being tested is intended to improve database performance, then verify if the expected improvement is reflected in the ADDM findings.

**See Also:**

- [Oracle Database Performance Tuning Guide](../tgdba/automatic-performance-diagnostics.md) for information about ADDM analysis

##### ASH Data Comparison

This section compares the ASH data across the two runs. The begin time and end time of the comparison period are displayed in a table. These times may not match the capture and replay times of the two runs being compared. Instead, these times represent the times when the ASH samples were taken.

The ASH Data Comparison section contains the following subsections:

- Compare Summary

- Top SQL

- Long Running SQL

- Common SQL

- Top Objects

**See Also:**

- [Oracle Database Performance Tuning Guide](../tgdba/analyzing-sampled-data.md) for information about ASH

###### Compare Summary

This section summarizes the activity during the two runs based on database time and wait time distribution. For example:

- DB Time Distribution indicates how the total database time is distributed across CPU usage, wait times, and I/O requests.

  Figure 13-1 shows the DB Time Distribution subsection of a sample report.

  Figure 13-1 DB Time Distribution

  ![Description of Figure 13-1 follows](img/dbr_rep_db_time_dist.gif)
  [Description of "Figure 13-1 DB Time Distribution"](img_text/dbr_rep_db_time_dist.md)

- Wait Time Distribution indicates how the total wait time is distributed across wait events. The top wait event class, event name, and event count are listed for both runs.

  Figure 13-2 shows the Wait Time Distribution subsection of a sample report.

  Figure 13-2 Wait Time Distribution

  ![Description of Figure 13-2 follows](img/dbr_rep_wait_time_dist.gif)
  [Description of "Figure 13-2 Wait Time Distribution"](img_text/dbr_rep_wait_time_dist.md)

###### Top SQL

This section displays the top SQL statements for both runs by total database time, CPU time, and wait time.

###### Long Running SQL

This section displays the top long-running SQL statements for both runs. Each long-running SQL statement contains details about the query, such as the maximum, minimum, and average response times.

###### Common SQL

This section extracts the SQL statements that are common in both runs and displays the top common SQL statements by variance in average response time and total database time.

###### Top Objects

This section contains details about the top objects for both runs by total wait time.

Figure 13-3 shows the Top Objects section of a sample report.

Figure 13-3 Top Objects

![Description of Figure 13-3 follows](img/dbr_rep_top_objects.gif)
[Description of "Figure 13-3 Top Objects"](img_text/dbr_rep_top_objects.md)

### Using SQL Performance Analyzer Reports

Use the SQL Performance Analyzer report to compare a SQL tuning set from a workload replay to another SQL tuning set from a workload capture, or two SQL tuning sets from two workload replays.

Comparing SQL tuning sets with Database Replay provides more information than SQL Performance Analyzer test-execute because it considers and shows all execution plans for each SQL statement, while SQL Performance Analyzer test-execute generates only one execution plan per SQL statement for each SQL trial.

#### Generating SQL Performance Analyzer Reports Using APIs

This section describes how to generate a SQL Performance Analyzer report using the `DBMS_WORKLOAD_REPLAY` package.

To generate a SQL Performance Analyzer report, use the `DBMS_WORKLOAD_REPLAY`.`COMPARE_SQLSET_REPORT` procedure:

    BEGIN
      DBMS_WORKLOAD_REPLAY.COMPARE_SQLSET_REPORT (
                               replay_id1 => 12,
                               replay_id2 => 17,
                               format => DBMS_WORKLOAD_CAPTURE.TYPE_HTML,
                               result => :report_bind);
    END;
    /

In this example, the `COMPARE_SQLSET_REPORT` procedure generates a SQL Performance Analyzer report in HTML format that compares a SQL tuning set captured during the workload replay with a replay ID of 12 to a SQL tuning set captured during workload replay with an ID of 17.

The `COMPARE_SQLSET_REPORT` procedure in this example uses the following parameters:

- The `replay_id1` parameter specifies the numerical identifier of the workload replay after change for which the reported will be generated. This parameter is required.

- The `replay_id2` parameter specifies the numerical identifier of the workload replay after change for which the reported will be generated. If unspecified, the comparison will be performed with the workload capture.

- The `format` parameter specifies the report format. Valid values include `DBMS_WORKLOAD_CAPTURE`.`TYPE_HTML` for HTML, `DBMS_WORKLOAD_CAPTURE`.`TYPE_XML` for XML, and `DBMS_WORKLOAD_CAPTURE`.`TYPE_TEXT` for text. This parameter is required.

- The result parameter specifies the output of the report.

**See Also:**

- "[Reviewing the SQL Performance Analyzer Report in Command-Line](comparing-sql-trials.md)" for information about how to interpret the SQL Performance Analyzer report

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_WORKLOAD_REPLAY.md) for information about the `DBMS_WORKLOAD_REPLAY` package
