You can manage Heat Map and Automatic Data Optimization with Oracle Enterprise Manager Cloud Control.

This section contains the following topics:

- Accessing the Database Administration Menu

- Viewing Automatic Data Optimization Activity at the Tablespace Level

- Viewing the Segment Activity Details of Any Tablespace

- Viewing the Segment Activity Details of Any Object

- Viewing the Segment Activity History of Any Object

- Searching Segment Activity in Automatic Data Optimization

- Viewing Policies for a Segment

- Disabling Background Activity

- Changing Execution Frequency of Background Automatic Data Optimization

- Viewing Policy Executions In the Last 24 Hours

- Viewing Objects Moved In Last 24 Hours

- Viewing Policy Details

- Viewing Objects Associated With a Policy

- Evaluating a Policy Before Execution

- Executing a Single Policy

- Stopping a Policy Execution

- Viewing Policy Execution History

**See Also:**

- [Displaying Heat Map Tracking Data With Views](ilm-strategy-heatmap-ado.md) and [Using Views to Monitor Policies for ADO](ilm-strategy-heatmap-ado.md) for information about views available for displaying Heat Map and ADO policy details

- [Oracle Enterprise Manager Cloud Control Administrator's Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/vldbg&id=EMADM-GUID-5BA58E51-3D84-4591-B8CD-AA91B3C00373) for information about managing Oracle Enterprise Manager Cloud Control

### 5.5.1 Accessing the Database Administration Menu

To access the Administration menu for a database:

1.  Log in to Oracle Enterprise Manager Cloud Control.

2.  Select Databases under the Targets menu.

3.  Click the database name in the list.

4.  The Administration menu appears on the database home page.

### 5.5.2 Viewing Automatic Data Optimization Activity at the Tablespace Level

To monitor the activity of the top 100 tablespaces selected by size in the database, follow these steps:

1.  From the Administration menu, choose Storage, then select Information Lifecycle Management.

    Enterprise Manager displays the Information Lifecycle Management page.

2.  On the Information Lifecycle Management page, you can view the Top 100 Tablespace Activity Heat Map based on the last access time, last write time, last full scan time, and last look up scan time.

    By default, the size of each box in the heat map represents a tablespace within a heat map and is determined by tablespace size. You can then use Information Lifecycle Management to drill down from tablespace to object to segment level heat maps.

### 5.5.3 Viewing the Segment Activity Details of Any Tablespace

To view segment activity details of any tablespace, follow these steps:

1.  From the Administration menu, choose Storage, then select Information Lifecycle Management.

    Enterprise Manager displays the Information Lifecycle Management page.

2.  On the Information Lifecycle Management page, click the Show Additional button.

    Enterprise Manager displays a dialog box that you can use to search for the segment activity details of any tablespace.

3.  On the dialog box, enter the Tablespace Name and click the Search button.

    Enterprise Manager displays the Segment Activity details for the tablespace.

4.  Click the Edit Tablespace Policy button to display the Edit Tablespace page with the ADO tab selected. You can create a policy for the tablespace that allows it to be compressed or moved.

### 5.5.4 Viewing the Segment Activity Details of Any Object

To view segment activity details of any object, follow these steps:

1.  From the Administration menu, choose Storage, then select Information Lifecycle Management.

    Enterprise Manager displays the Information Lifecycle Management page.

2.  Move the cursor over any of the boxes within the Database level heat map where each box represents a tablespace. Click the Tablespace to which the object you want to view belongs.

    Enterprise Manager displays the Tablespace level heat map for the 100 largest objects belonging to the tablespace. The Segment Activity tables displays the Segment Activity details for the 100 largest objects.

3.  On the Information Lifecycle Management page, click the Show Additional button.

    Enterprise Manager displays a dialog box that you can use to search for the segment activity details of any object belonging to the tablespace.

4.  On the dialog box, enter the Schema Name and Object Name and click Search.

    Enterprise Manager displays the Segment Activity details for the object.

5.  Click the Edit Object Policy button to display the Edit Object page with the ADO tab selected. You can create a policy for the object that allows it to be compressed or moved.

### 5.5.5 Viewing the Segment Activity History of Any Object

To view the segment activity history of any object, follow these steps:

1.  From the Administration menu, choose Storage, then select Information Lifecycle Management.

    Enterprise Manager displays the Information Lifecycle Management page.

2.  Move the cursor over any of the boxes within the Database level heat map where each box represents a tablespace. Click the Tablespace to which the object you want to view belongs.

    Enterprise Manager displays the Tablespace level heat map for the 100 largest objects belonging to the tablespace. The Segment Activity tables displays the Segment Activity details for the 100 largest objects.

3.  Select the object in the Segment Activity details table and click the Activity History button.

    Enterprise Manager displays the Edit Object page with the ADO tab selected. The ADO tab displays a list of policies and the Segment Access history.

4.  You can select a segment, change the date range to be the last 60 days, select the Daily option, and clicks the Refresh button to display the Segment Access History for the object for the last 60 days.

### 5.5.6 Searching Segment Activity in Automatic Data Optimization

To search for segment activities during different time durations in Automatic Data Optimization, follow these steps:

1.  From the Administration menu, choose Storage, then select Information Lifecycle Management.

    Enterprise Manager displays the Information Lifecycle Management page.

2.  On the Information Lifecycle Management page, click any of the boxes in a heat map. From the initial display which is the database level, click a box in the heat map to display the 100 largest objects in that tablespace. You can then click a heat map box to see the heat map of the 100 largest segments in that object.

3.  Enter a timestamp that is one year ago for the Last Access Time and then click Go. A list of segments that have not been accessed or modified in the last year are displayed. The segments are sorted in descending order by segment size.

    On the object level heat map, you can search for a specific segment based on Tablespace, Name, Partition, Type, Last Access Time, Last Write Time, Last Full Scan Time, and Last Look Up Scan Time.

    You can select a row (segment) and view the row activity for that segment clicking the Policies column to view the policies associated with the segment.

### 5.5.7 Viewing Policies for a Segment

To view the policies associated with a segment, follow these steps:

1.  From the Administration menu, choose Storage, then select Information Lifecycle Management.

    Enterprise Manager displays the Information Lifecycle Management page.

2.  On the Information Lifecycle Management page, click Go. If the segments in the search results have policies associated with them, the count is displayed in the Policies column and is non-zero. Move your mouse over the count to view the associated policies with the segment, including inherited policies. If the count is zero then no policies are associated with the segment.

    From the Database level heat map drill down to Tablespace level heat map. On the Tablespace level heat map Enterprise Manager displays the top 100 Objects belonging to the Tablespace. For each object, Enterprise Manager displays the count of policies in the column.

    From Tablespace level heat map select an object and drill down to the object level heat map. Enterprise Manager displays the Top 100 largest Segments belonging to the Object. For each segment, Enterprise Manager displays a count of policies in the Policies column.

### 5.5.8 Disabling Background Activity

To disable the Automatic Data Optimization background evaluation and scheduler, follow these steps:

For more information about the ILM ADO `ENABLED` parameter, refer to [Managing ILM ADO Parameters](ilm-strategy-heatmap-ado.md).

1.  From the Administration menu, choose Storage, then select Information Lifecycle Management.

    Enterprise Manager displays the Information Lifecycle Management page.

2.  On the Information Lifecycle Management page, click the Policy tab.

3.  Click Configure in the Policy Execution Settings section.

    The Configure Policy Execution Settings dialog box is displayed.

4.  Change the Status drop-down to Disabled and click OK.

    Enterprise Manager displays the Information Lifecycle Management page where the Status now shows Disabled on the Policy tab in the Policy Execution Settings section.

### 5.5.9 Changing Execution Frequency of Background Automatic Data Optimization

To change the execution frequency of the Information Lifecycle Management background evaluation and scheduler, follow these steps:

For more information about the ILM ADO `EXECUTION` `INTERVAL` parameter, refer to [Managing ILM ADO Parameters](ilm-strategy-heatmap-ado.md).

1.  From the Administration menu, choose Storage, then select Information Lifecycle Management.

    Enterprise Manager displays the Information Lifecycle Management page.

2.  On the Information Lifecycle Management page, click the Policy tab.

3.  Click Configure in the Policy Execution Settings section.

    The Configure Policy Execution Settings dialog box is displayed.

4.  Change the value of the Execution Interval (mins) to a lower or higher number than what is currently displayed and then click OK.

    Enterprise Manager displays the Information Lifecycle Management page where the Execution Interval now shows the new value on the Policy tab under Policy Execution Settings.

### 5.5.10 Viewing Policy Executions In the Last 24 Hours

To view policies that were executed in the last 24 hours and to view what objects were moved or compressed with the execution of the policies, follow these steps:

1.  From the Administration menu, choose Storage, then select Information Lifecycle Management.

    Enterprise Manager displays the Information Lifecycle Management page.

2.  On the Information Lifecycle Management page, click the Policy tab.

3.  Click the Policies Completed or the Policies Failed link on the Policy execution summary for last 24 hours row. Clicking either displays the execution history for the past 24 hours.

    The Policy Execution Details dialog box display, showing the execution details for the policies in the last 24 hours.

### 5.5.11 Viewing Objects Moved In Last 24 Hours

To view which objects were moved in the last 24 hours and which policies/jobs moved those objects, follow these steps:

1.  From the Administration menu, choose Storage, then select Information Lifecycle Management.

    Enterprise Manager displays the Information Lifecycle Management page.

2.  On the Information Lifecycle Management page, click the Policy tab.

3.  On the Policies execution summary for last 24 hours row, click the Objects Moved link.

    The Policy Execution History dialog box displays, showing the execution history for the jobs and policies executed and the objects moved in the last 24 hours.

### 5.5.12 Viewing Policy Details

To view the details of a specific ADO policy, follow these steps:

1.  From the Administration menu, choose Storage, then select Information Lifecycle Management.

    Enterprise Manager displays the Information Lifecycle Management page.

2.  On the Information Lifecycle Management page, click the Policy tab.

3.  To view policy details, click the policy name link in the policy table, or select any row in the policies table and then click the View Policy Details button.

### 5.5.13 Viewing Objects Associated With a Policy

To view the objects associated with a specific policy, follow these steps:

1.  From the Administration menu, choose Storage, then select Information Lifecycle Management.

    Enterprise Manager displays the Information Lifecycle Management page.

2.  On the Information Lifecycle Management page, click the Policy tab.

3.  Click the count in the Objects column.

    The Objects associated with the Policy are displayed

### 5.5.14 Evaluating a Policy Before Execution

To evaluate a policy before executing the policy, follow these steps:

1.  From the Administration menu, choose Storage, then select Information Lifecycle Management.

    Enterprise Manager displays the Information Lifecycle Management page.

2.  On the Information Lifecycle Management page, click the Policy tab.

3.  In the Evaluations region, click Evaluate.

    A dialog box displays giving you the choice of evaluating all policies in the database, or all policies affecting objects in a particular schema.

4.  Enter a Schema Name and click OK to initiate the evaluation.

    The evaluation dialog box closes and the evaluation is submitted. You can refresh the page or perform other Enterprise Manager tasks and then revisit the Policy Tab later. When you do, the Completed count in the Evaluations region is increased by 1.

5.  When you click the Completed count link in the Evaluations region, a dialog box is displayed that lists all completed evaluations.

6.  When you click the Task ID of the most recent evaluation, the Evaluation Details dialog box is displayed listing all objects currently included in the evaluation task that will either be compressed or moved if this evaluation is executed.

7.  Click OK to include the list of objects in the execution. The Evaluation Details dialog box closes.

8.  Select the row in the Evaluations table containing the most recent evaluation (top most row), then click Execute.

    The Execute Evaluation dialog box is displayed, again listing the objects that will be affected during execution.

9.  Click OK to begin the execution.

    The Execute Evaluation dialog box closes. Eventually, execution results can be seen by clicking the Completed or Failed links in the Jobs or Policies regions under Policy Execution Summary for Last 24 Hours. Also, eventually the Evaluations Completed count is decreased by 1, as the task changes state from INACTIVE to ACTIVE to COMPLETED.

### 5.5.15 Executing a Single Policy

To execute a policy immediately on the objects associated with the Policy, follow these steps:

1.  From the Administration menu, choose Storage, then select Information Lifecycle Management.

    Enterprise Manager displays the Information Lifecycle Management page.

2.  On the Information Lifecycle Management page, click the Policy tab.

3.  Select the policy and click Execute Policy.

    The Execute Policy dialog box is displayed, listing all objects that are evaluated by the selected policy. The dialog box also includes a Hide/Show button to display the `EXECUTE_ILM` commands to be executed. Only objects with this policy enabled are included.

### 5.5.16 Stopping a Policy Execution

To stop a policy execution, follow these steps:

1.  From the Administration menu, choose Storage, then select Information Lifecycle Management.

    Enterprise Manager displays the Information Lifecycle Management page.

2.  On the Information Lifecycle Management page, click the Policy tab.

3.  In the Jobs region under Policy Execution Summary for Last 24 Hours, click the In Progress link. This step assumes there is at least one task or job in progress.

    A dialog box displays listing all currently executing tasks.

4.  Click the Jobs link for one of the tasks listed in the table.

    A dialog box displays listing details about the job(s) running as part of the task.

5.  Clicks OK.

    The Jobs Details dialog box closes.

6.  Select a row in the table and click Stop Execution.

    A dialog box displays confirmation of the stop execution process.

7.  Click OK.

    The confirmation dialog box is dismissed.

### 5.5.17 Viewing Policy Execution History

To view the execution history for a specific policy, follow these steps:

1.  From the Administration menu, choose Storage, then select Information Lifecycle Management.

    Enterprise Manager displays the Information Lifecycle Management page.

2.  On the Information Lifecycle Management page, click the Policy tab.

3.  Select the policy and click Execution History.

    The Policy Execution History dialog box displays, showing the execution history for the selected policy. The details include the job information and the objects that were moved or compressed.
