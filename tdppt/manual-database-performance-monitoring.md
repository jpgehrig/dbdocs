You can run the Automatic Database Diagnostic Monitor (ADDM) manually to monitor current and historical database performance. Typically, you use the automatic diagnostic feature of ADDM to identify performance problems with the database. As described in [Automatic Database Performance Monitoring](automatic-database-performance-monitoring.md), ADDM runs once every hour by default. You can configure ADDM to run at a different time interval. However, in some cases you may want to run ADDM manually.

You can run ADDM manually to analyze a time period that is longer than one ADDM analysis period. For example, you may want to analyze database performance in a workday by analyzing 8 consecutive hours. You could analyze each of the individual ADDM periods within the workday, but this approach may become complicated if performance problems appear in only some ADDM periods. Alternatively, you can run ADDM manually with a pair of Automatic Workload Repository (AWR) snapshots that encompass the 8-hour period. In this case, ADDM identifies the most critical performance problems in the entire time period.

This chapter contains the following sections:

- Manually Running ADDM to Analyze Current Database Performance

- Manually Running ADDM to Analyze Historical Database Performance

- Accessing Previous ADDM Results

### 7.1 Manually Running ADDM to Analyze Current Database Performance

By default, ADDM runs every hour to analyze snapshots taken by AWR during this period. In some cases you may notice performance degradation that did not exist in the previous ADDM analysis period, or a sudden spike in database activity on the Performance page, as described in [Monitoring Real-Time Database Performance](monitoring-real-time-database-performance.md) . If the next ADDM analysis is not scheduled to run for 30 minutes, then you can run ADDM manually to identify and resolve the performance problem.

When you run ADDM manually, a manual AWR snapshot is created automatically. This manual run may affect the ADDM run cycle. For example, if you scheduled ADDM to run hourly at the start of each hour and the last ADDM run was at 8:00 p.m., running ADDM manually at 8:30 p.m. causes the next scheduled run to start at 9:30 p.m., not 9:00 p.m. Subsequent ADDM runs continue on the new run cycle, occurring hourly at the half-hour instead of the start of each hour.

#### To analyze current database performance by manually running ADDM:

1.  Access the Database Home page.

    See "[Accessing the Database Home Page](introduction.md)" for more information.

2.  From the Performance menu, select Advisors Home.

    If the Database Login page appears, then log in as a user with administrator privileges. The Advisor Central page appears.

3.  Under Advisors, select ADDM. The Run ADDM page appears.

    ![Description of run_addm_now.gif follows](img/run_addm_now.gif)
    [Description of the illustration run_addm_now.gif](img_text/run_addm_now.md)
    In this example, the average active sessions with wait events rose at 10:00 a.m., peaking at 10:50 a.m. The number dipped at 11:00 a.m. and then started to rise again at 11:10 a.m.

4.  Select Run ADDM to analyze current performance and click OK.

    The Confirmation page appears.

5.  Click Yes.

    The Processing: Run ADDM Now page appears while the database takes a new AWR snapshot.

    An ADDM run occurs for the time period between the new and the previous snapshot. After ADDM completes the analysis, the Automatic Database Diagnostic Monitor (ADDM) page appears with the results.

    ![Description of run_addm_now_results.gif follows](img/run_addm_now_results.gif)
    [Description of the illustration run_addm_now_results.gif](img_text/run_addm_now_results.md)

6.  Click View Report.

    The View Report page appears.

7.  Optionally, click Save to File to save the results of the ADDM task in a report for later access.

**See Also:**

- "[Reviewing the Automatic Database Diagnostic Monitor Analysis](automatic-database-performance-monitoring.md)"

### 7.2 Manually Running ADDM to Analyze Historical Database Performance

You can run ADDM manually to analyze historical database performance by selecting a pair or range of AWR snapshots as the analysis period. This technique is useful when you have identified a previous time period when database performance was poor.

In the Performance page, you can monitor historical performance by selecting Historical from the View Data list. In the Historical view, you can monitor database performance in the past, up to the duration defined by the AWR retention period. If you notice performance degradation, then you can drill down from the Performance page to identify historical performance problems with the database, as described in [Monitoring Real-Time Database Performance](monitoring-real-time-database-performance.md) . If you identify a problem, then you can run ADDM manually to analyze a particular time period.

#### To analyze historical database performance by manually running ADDM:

1.  Access the Database Home page.

    See "[Accessing the Database Home Page](introduction.md)" for more information.

2.  From the Performance menu, select Advisors Home.

    If the Database Login page appears, then log in as a user with administrator privileges. The Advisor Central page appears.

3.  Under Advisors, select ADDM. The Run ADDM page appears.

4.  Select Run ADDM to analyze past performance.

5.  Specify a time period for analysis by selecting a pair of AWR snapshots. Complete the following steps:

    1.  Select Period Start Time.

    2.  Below the chart for the starting snapshot, click the snapshot you want to use for the start time.

        A play icon (displayed as an arrow) appears over the snapshot icon.

        In this example, database activity peaked from 10 a.m. to 11 a.m., so the snapshot taken at 10 a.m. is selected for the start time.

    3.  Select Period End Time.

    4.  Below the chart for the ending snapshot, click the snapshot you want to use for the end time.

        A stop icon (displayed as a square) appears over the snapshot icon.

        In this example, the ending snapshot is at 11:00 a.m.

    ![Description of run_addm_past.gif follows](img/run_addm_past.gif)
    [Description of the illustration run_addm_past.gif](img_text/run_addm_past.md)

6.  Click OK.

    After ADDM completes the analysis, the Automatic Database Diagnostic Monitor (ADDM) page appears with the results of the ADDM run.

    Figure 7-1 Analyzing Historical Database Performance

    ![Description of Figure 7-1 follows](img/run_addm_past_results.gif)
    [Description of "Figure 7-1 Analyzing Historical Database Performance"](img_text/run_addm_past_results.md)

7.  Click View Report.

    The View Report page appears.

8.  Optionally, click Save to File.

**See Also:**

- "[Reviewing the Automatic Database Diagnostic Monitor Analysis](automatic-database-performance-monitoring.md)"

### 7.3 Accessing Previous ADDM Results

If you ran ADDM manually to analyze current or historical database performance, the results are displayed on the Automatic Database Diagnostic Monitor (ADDM) page after the ADDM run has completed.

You can access the ADDM results at a later time, or access the ADDM results from previous run cycles.

#### To access the ADDM results:

1.  Access the Database Home page.

    See "[Accessing the Database Home Page](introduction.md)" for more information.

2.  From the Performance menu, select Advisors Home.

    If the Database Login page appears, then log in as a user with administrator privileges. The Advisor Central page appears.

3.  Complete the following steps:

    1.  Under Advisor Tasks, select ADDM from the Advisory Type list.

    2.  Select the appropriate search criteria.

        For example, you can select All in the Advisor Runs list to view all ADDM tasks.

    3.  Click Go.

    ![Description of advisor_tasks_addm.gif follows](img/advisor_tasks_addm.gif)
    [Description of the illustration advisor_tasks_addm.gif](img_text/advisor_tasks_addm.md)
    The ADDM tasks are displayed under Results.

4.  To view an ADDM result, select the desired ADDM task and click View Result.

    The results from the selected ADDM task are shown in the Automatic Database Diagnostic Monitor (ADDM) page.

    **See Also:**

    - "[Reviewing the Automatic Database Diagnostic Monitor Analysis](automatic-database-performance-monitoring.md)"
