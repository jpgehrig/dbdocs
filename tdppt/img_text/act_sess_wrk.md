This screenshot shows the top portion of the Active Sessions Working: CPU + CPU Wait page.

In the top right corner of the screenshot is the following list: View Data. The value shown is Real Time: 15 Second Refresh.

A line chart labeled Active Sessions is shown. The units of the x-axis are times of day in 10-minute intervals. The x-coordinates shown range from 9:08 a.m. to 9:58. The units of the y-axis are: number of active sessions. The y-coordinates shown range from 0 to 2.4. A line at the 2.0 mark is labeled Maximum CPU. The following types of information are plotted in the chart: CPU + CPU Wait. The chart indicates that the highest spike in CPU usage was 2.2 at 9:59. A shaded box indicates the selected five minute interval, which is from 9:59 to 10:04.

Underneath the line chart is the Detailed for Selected 5 Minute Interval section. The Start Time is Jan 13, 2012 9:59:09.

The Detail section contains the following subsections: Top Working SQL, and Top Working Sessions.

The Top Working SQL section contains the Actions list, which shows Schedule SQL Tuning Advisor. Next to it is the Go button. Below the Actions list are the options Select All and Select None.

Underneath the options is a table. The table contains the following columns: Select, Activity (%), SQL ID, and SQL Type. The Select column contains check boxes. Values in the Activity column are displayed as a horizontal bar chart with an associated number. Values in the SQL ID column are links.

Seven rows are shown in the table. In each row, the check box in the Select column is clear. The remaining values of the rows are as follows:

Row 1: 60.00, 94fzm3jx1c1yp, PL/SQL EXECUTE.

Row 2: 15.40, ddthrb7j9a63f, SELECT.

Row 3: 11.50, 95adfchfv58a5, UPDATE.

Row 4: 10.63, 357p6hzg9gat, PL/SQL EXECUTE.

Row 5: 9.98, axabnfyfp4r3p, SELECT.

Row 6: 4.99, f8ybh6brs1uq2, SELECT.

Row 7: 4.12, dsv6nf68zgkuc, INSERT.

The Top Working Sessions section contains the View list, which shows Top Sessions. Underneath the list is a table. The table contains the following columns: Activity (%), Session ID, User Name, and Program. Values in the Activity column are displayed as a horizontal bar chart with an associated number. Values in the Session ID and User Name columns are links.

7 rows are shown in the table. The values of the row are as follows:

Row 1: 44.93, 31, HR, sqlplus@dbhost (TNS V1-V3).

Row2: 37.57, 32, HR, sqlplus@dbhost (TNS V1-V3).

Row 3: 4.17, 34, SYS, oracle@dbhost (M000).

Row 4: 1.19, 127, SYS, JDBC Thin Client.

Row 5: .80, 8, SYS, oracle@dbhost (LGO1).

Row 6: .40, 6, SYS, oracle@dbhost (LGWR).

Row 7: .40, 9, SYS, oracle@dbhost (LGO2).

End of description.
