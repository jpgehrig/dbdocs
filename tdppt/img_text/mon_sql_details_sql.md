This screenshot shows the Monitored SQL Execution Details page for the SQL statement 75g0d6c4dh7r8. Next to the title of the page is a Completed symbol. At the top right of the page is the label-value pair Page Refreshed: 10:12:35 a.m GMT-0500.

The page has the Overview group and the Details group. In the Overview group are the General, Time & Wait Statistics, and IO Statistics groups.

The General group has the following label-value pairs:

SQL Text: SELECT MAX(asld) FROM(SLECT MAX(amo

Execution Started: Tue Sep 20, 2012 10:11:06 a.m.

Last Refresh Time: Tue Sep 20, 2012 10:11:48 a.m.

Execution ID: 16777216

User: SH

Fetch Calls: 1

The Time & Wait Statistics group has the following label-value pairs:

Duration: bar and 42.0s

Database Time: bar and 42.1s

PL/SQL & Java: 0us

Wait Activity %: 100

The IO Statistics group has the following label-value pairs:

Buffer Gets: bar and 4,760

IO Requests: bar and 1,490

IO Bytes: bar and 81MB

The Details group has the Plan Statistics, Plan, Activity, and Metrics subpages. The Plan Statistics subpage is showing. The subpage has the label-value pair Plan Hash Value: 984733633. Below that is a table with the following columns: Operation, Name, Line ID, Estimated Rows, Cost, Timeline(3s), Executions, Actual Rows, Temp (Max), Other, IO Requests, IO Bytes, Activity %. The value in the Timeline column is a bar that indicates the duration of the operation and when it was first active. The value in the Activity column is a bar that indicates the type of activity and the number of samples.

Six rows are shown in the table. The values in the rows are the following:

Row 1: SELECT statement, null, 0, null, null, very small bar, 1, 1, null, null, null, null, null, null.

Row 2: SORT AGGREGATE, null, 1, 1, null, very small bar, 1, 1, null, null, null, null, null, null.

Row 3: VIEW, null, 2, 7,059, 17M, very small bar, 1, 7,059, null, null, null, null, null, null.

Row 4: HASH GROUP BY, null, 3, 7,059, 17M, very small bar, 1, 7,059, 1MB, null, null, null, null, null.

Row 5: VIEW, VW_NWVW, 4, 4,113k, 17M, very small bar, 1, 919K, null, null, null, null, null, null.

Row 6: FILTER, null, 5, null, null, very small bar, 1, 919K, null, null, null, null, null, null.
