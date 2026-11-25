This procedure explains how to recover from the loss of the server parameter file, control file, and all data files.

To perform disaster recovery:

1.  Ensure that the instance is not started.
2.  If the archived redo logs are required for recovery of the data files or tablespaces, then restore the archived redo logs.
3.  Select the component named `Oracle Database` from a VSS snapshot.
4.  Restore the database.
    The Oracle VSS writer automatically starts the instance, mount the database, and recovers the restored data files. If some archived logs are missing, then you can restore the logs and recover the data files with SQL\*Plus or RMAN.
5.  Open the database with the `RESETLOGS` option.

**Parent topic:** [About Restoring and Recovering a Database in ARCHIVELOG Mode](about-restoring-and-recovering-a-database-in-archivelog-mode.md)
