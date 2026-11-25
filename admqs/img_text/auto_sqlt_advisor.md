This is a screen shot of the SQL Tuning Advisor page with the Automatic tab showing. At the top of the page, Show All is the selected value in the Automatic Runs field. To the right of the Automatic Runs field is the Configuration button. At the top right of the page, the Page Refreshed field shows the time that the page was last refreshed, and the Auto Refresh field shows the refresh interval currently set for this page. The table shows information about the Automatic SQL Tuning Advisor task named SYS_AUTO_SQL_TUNING_TASK, which runs daily.

On the left below the page name is the Status section. This includes the following fields and values:

- Task Name: SYS_AUTO_SQL_TUNING_TASK

- Task Owner: SYS

- Started: Fri Oct 19, 2012 12:29:45 PM

- Completed: Fri Oct 19, 2012 12:40:34 PM

- Automatic SQL Tuning: Enabled

- Profiles Implementation: Manual

To the right of the Status section is the Findings Overview section, which includes these three charts from right to left:

- SQL Examined Count: This chart shows the number of SQL statements without findings (which has a value of 4), and SQL statements with findings (which has a value of 11)

- Breakdown by Finding Type: This chart shows five categories named (from left to right) SQL Profile, Index, Restructure SQL, Statistics, and Alternative Plan). SQL Profile has a value of 9, Index has a value of 11, Restructure SQL has a value of 2, and Statistics and Alternative Plan have no values.

- SQL Profile Potential DB Time Benefit (sec): This chart shows two categories named Implemented and Recommended. There is a Before value of 00:13:12 seconds, and After value of 00:03:13 seconds, and a Benefit value of 00:09:59 seconds, which is a 75.63% improvement.

The Top SQL Statements table appears at the bottom of the page. On the left, just above the table, the View Details and Implement All SQL Profiles buttons appear. On the right, just above the table, the SQL Profile Verified check box and the Search field for the table appear.

The columns in the table (from left to right) are SQL Text, Id, Schema, Cumulative DB Time Benefit, Per-Execution Benefit, Statistics, SQL Profile, Index, Restructure SQL, Alternative Plan, Miscellaneous, and Timeout.
