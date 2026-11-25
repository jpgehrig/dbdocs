The Top Timed Events section of the AWR Compare Periods report is shown. The section has a table that has two top-level columns. Before the table is a sentence that says the following: Events with a "-" did not make the Top list in this set of snapshots, but are displayed for comparison purposes.

The names of the columns of the table are 1st and 2nd. Each column has six columns. Those column names are Event, Wait Class, Waits, Time(s), %DB time. There are seven rows of events, in descending order of the percentage of database time used.

The values for the rows of the 1st column are the following:

Row 1: CPU time, null, null, 1,772.85, null, 89.54.

Row 2: resmgr:cpu quantum, Scheduler, 14,105, 108.51, 7.69, 5.48.

Row 3: db file sequential read, User I/O, 2,470,197, 65.48, .03, 3.31

Row 4: db file async I/O submit, System I/O, 831, 10.10, 12.15, .51.

Row 5: oracle thread bootstrap, Other, 51, 6.64, 130.28, .34.

Row 6: -LGWR slave barrier, Other, 1,518, 4.2, 2.77, .21.

Row 7: -log file parallel write, System I/O, 659, 3.20, 4.86, .18

The values for the rows of the 2nd column are the following:

Row 1: oracle thread bootstrap, Other, 15, 2.07, 137.74, 250.26.

Row 2: CPU time, null, null, .68, null, 82.37.

Row 3: db file sequential read, User I/O, 103, .64, 6.25, 77.03.

Row 4: LGWR slave barrier, Other, 231, .31, 1.32, 36.9.7

Row 5: log file parallel write, System I/O, 97, .27, 2.8, 32.96.

Row 6: -db file async I/O submit, System I/O, 445, .09, .19, 10.32.

-, null, null, null, null, null.

End of description.
