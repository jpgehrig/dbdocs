This procedure explains how to recover from the loss of all tablespaces.

To recover all data files:

1.  Ensure that the database is mounted.
2.  If the archived redo logs are required for recovery of the data files or tablespaces, then restore the archived redo logs.
3.  Select the component named `All Tablespaces` from a VSS snapshot.
4.  Restore the tablespaces.
    The Oracle VSS writer automatically recovers the restored data files. If some archived logs are missing, then you can restore the logs and recover the data files with SQL\*Plus or RMAN.
5.  Open the database.

**Parent topic:** [About Restoring and Recovering a Database in ARCHIVELOG Mode](about-restoring-and-recovering-a-database-in-archivelog-mode.md)
