The title is WORKLOAD REPOSITORY COMPARE PERIOD REPORT.

The first table has the following columns: Snapshot Set, DB Name, DB Id, Instance, Inst num, Release, Cluster, Host, Std Block Size. The table has two rows. The values of the rows are the following:

Row 1: First (1st), EMPDB, 647168497, empdb, 1, 12.1.0.0.1, NO, dbhost, 8192.

Row 2 has the following values: Second (2nd), EMPDB, 647168497, empdb, 1, 12.1.0.0.1, NO, dbhost, 8192.

The second table has the following columns: Snapshot Set, Begin Snap Id, Begin Snap Time, End Snap Id, End Snap Time, Avg Active Users, Elapsed Time (min), DB time (min). The table has three rows. The values of the rows are the following:

Row 1: 1st, 1488, 07-Feb-12 10:50:03 (Tue), 1491, 07-Feb-12 11:20:13 (Tue), 1.1, 30.2, 33

Row 2: 2nd, 1500, 07-Feb-12 12:50:34 (Tue), 1501, 07-Feb-12 11:20:13 (Tue), 0, 10, 0.

Row 3: %Diff, null, null, null, null, -100, -66.7, -100.

The Host Configuration Comparison section follows.

The section contains a table with the following columns: null, 1st, 2nd, Diff, %Diff. The table has 10 rows. The values of the rows are the following:

Row 1: Number of CPUs, 2, 2, 0, 0.

Row 2: Number of CPU Cores: 2, 2, 0, 0.

Row 3: Number of CPU Sockets: 2, 2, 0, 0.

Row 4: Physical Memory, 4000M, 4000M, 0M, 0.

Row 5: Load at Start Snapshot, 1.69, .17, -1.52, -88.9.

Row 6: Load at End Snapshot, 1.52, .73, -.79, -52.

Row 7: %User Time, 53.11, 6.01, -47.09, -88.7.

Row 8: %System Time 2.93, 1.48, --1.45, -49.5.

Row 9: %Idle Time, 43.92, 92.46, 48.56, 110.6.

Row 10: %IO Wait Time, 7.78, 3.08, -4.68, -60.3.

The Cache Sizes section follows.

The section contains a table with the following columns: null, 1st (M), 2nd (M), Diff (M), %Diff. The table has 7 rows. The values of the rows are the following:

Row 1: Memory Target, 1,024, 1,024, 0, 0.

Row 2: (indented under Memory Target) SGA Target, 748, 748, 0, 0.

Row 3: (indented under SGA Target) Buffer Cache, 152, 152, 0, 0.

Row 4: (indented under SGA Target) Shared Pool, 396, 396, 0, 0.

Row 5: (indented under SGA Target) Large Pool, 4, 4, 0, 0.

Row 6: (indented under SGA Target) Java Pool, 180, 180, 0, 0.

Row 5: (indented under SGA Target) Streams Pool, 4, 4, 0, 0.

Row 6: (indented under Memory Target) PGA Target, 276, 276, 0, 0.

Row 7: Log Buffer, 5.4, 5.4, 0, 0.

The Load Profile section follows.

The section contains a table with the following columns: null, 1st per sec, 2nd per sec, %Diff, 1st per txn, 2nd per txn, %Diff. The table has 3 rows showing. The values of the rows are the following:

Row 1: DB time, 1.1, 0, -100, 18.5, .1, -99.7.

Row 2: CPU time, 1, 0, -100, 16.6, .1, -99.7.

Row 3: Redo size, 3,990.2, 3,740.6, 67,475.6, 173,212.3, 156.7.

End of description.
