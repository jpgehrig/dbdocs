In the Details section of the SQL Details page. The section has four tabs: Statistics (selected), Activity, Plan, Plan Control, Tuning History, and SQL Monitoring (grayed out). The Statistics subpage is shown.

In the Summary section, the Active Sessions chart is shown. The y-axis values are active sessions with a range from 0 to 1. The x-axis values are times of day. The times begin with 2:41, the next time is 2:45, then the times are in 5-minute increments until 3:30. Under the x-axis is the date Dec 30, 2011. Session activity occurs from 2:41 to 2:49, with four spikes to .5 between 2:44 and 2:48. Session activity is then 0 until 3:21 when activity begins again. The activity is above .5 several times between 3:22 and 3:32, when it spikes at .75.

The General section has the following label-value pairs: Module is SQL\*Plus, Action is EMP_DML, Parsing Schema is HR, PL/SQL Source is Not Applicable, SQL Profile is n/a, and SQL Plan Baseline is n/a. The Activity By Waits pie chart has a legend of CPU 80%, Remaining Waits (12.9%), and Concurrency Waits (7.1%)

The Activity By Time section has the following label-value pairs: Elapsed Time (sec) is 706.46, CPU Time (sec) is 564.97, and Wait Time (sec) is 141.50.

The Elapsed Time Breakdown section has the following label-value pairs: SQLTime (sec) is 706.46, PL/SQL Time (sec) is 0, Java Time (sec) is 0.

The Shared Cursors Statistics section has the following label-value pairs: Total Parses is 2, Hard Parses is 1, Child Cursors is 1, Loaded Plans is 1, Invalidations is 0, Largest Cursor Size (KB) is 54.66, All Cursor Size (KB) is 54.66, First Load Time is Dec 30, 2011 2:30:16 PM GMT -06:00, Last Load Time is Dec 30, 2011 2:30:16 PM GMT -06:00.

The Execution Statistics table has the following columns: null, Total, Per Execution, and Per Row. The table has six rows. The values in the rows are the following:

Row 1: Executions, 773,938, 1, .11.

Row 2: Elapsed Time (sec), 706.46, \<0.01, \< 0.01.

Row 3: CPU Time (sec), 564.97, \< 0.01, \< 0.01.

Row 4: Buffer Gets, 30,869,398, 39.89, 4.43.

Row 5: Disk Reads, 0, 0, 0.

Row 6: Direct Writes, 0, 0, 0.

The Other Statistics section has the following label-value pairs: Executions that Fetched All Rows (%) is 100, Average Persistent Mem (KB) is 14.37, Average Runtime Mem (KB) is 13.12, Serializable Aborts is 0, Remote is No, Obsolete is No, and Child Latch Number is 0.

End of description.
