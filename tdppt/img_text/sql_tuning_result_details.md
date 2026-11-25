The Automatic SQL Tuning Result Details: All Analyzed SQLs section is shown.

The Begin Date is Feb 19, 2012 7:00:02 PM (UTC-08:00). The End Date is Feb 23, 2012 12:16:57 PM (UTC-08:00).

The Recommendations section is shown. Below the title is the sentence: Only profiles that significantly improve SQL performance were implemented. Below the sentence are the View Recommendations and Implement All SQL Profiles buttons.

The section has a table that has the following columns: Select, SQL Text, Parsing Schema, SQL ID, Weekly DB Time Benefit (sec), Per-Execution % Benefit, Statistics, SQL Profile, Index, Restructure SQL, Miscellaneous, Timed Out, Error, Date. The column values are options. The SQL ID values are links.

The table has six rows. The values of the rows are the following:

Row 1: (selected), SELECT sum(quantity_sold) FROM sales s..., SH, fudq5z56q642p, 60.38, 96, null, (96%) (check mark), (62%) (check mark), null, null, null, null, 2/20/12 10:00:02 AM.

Row 2: (not selected), SELECT \* FROM sales where amount_sold=..., SH, bzmnj0nbvmz8t, 3.97, 60, null, null, (60%) (check mark), null, null, null, null, 2/20/12 10:00:02 AM.

Row 3: (not selected), /\* Oracle OEM \*/ SELECT /\*+ INDEX(ts) \*/..., DBSNMP, ab7ktcdksu27j, 2.36, 87, (check mark), (87%) (check mark), null, null, (check mark), null, null, 2/20/12 7:00:00 PM.

Row 4: (not selected), SELECT TASK_LIST.TASK_ID FROM (SELECT /\*..., DBSNMP, bqfx5q2jas08u, .95, 98, (check mark), (98%) (check mark), null, null, (check mark), null, null, 2/23/12 10:00:02 AM.

Row 5: (not selected), SELECT NVL(SUM(e.non_exempt_violations_l..., SYSMAN, b4m9s8bfrr8x7, .40, 67, (check mark), (67%) (check mark), null, null, null, null, null, 2/19/12 7:00:02 PM.

Row 6: (not selected), SELECT :B1 TASK_ID, F.FINDING_ID FINDING..., DBSNMP, a8j39qb13tqkr, .23, 24, null, (24%) (check mark), null, (check mark), (check mark), null, null, 2/20/12 2:00:02 PM.

End of description.
