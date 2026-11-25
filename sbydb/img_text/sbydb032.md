This illustration shows a Data Guard configuration consisting of a primary database and a logical standby database.

From the primary database, redo data is archived to the standby database where log apply services transform the archived redo log files into SQL statements, which are then executed on the open logical standby database using SQL Apply technology.
