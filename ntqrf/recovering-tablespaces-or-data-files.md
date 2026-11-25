This procedure explains how to recover from the loss of one or more tablespaces or data files. This procedure assumes that not all data files are lost.

To recover from the loss of all tablespaces or data files:

1.  Ensure that the database is either mounted or open. If the database is open, then take the data files or tablespaces needing recovery offline with the `ALTER DATABASE ... OFFLINE` statement.
2.  If the archived redo logs are required for recovery of the data files or tablespaces, then restore the archived redo logs.
3.  Select the components from the VSS snapshot that contains the lost data files, or all data files in the lost tablespaces.
4.  Restore the component containing the lost data files.
    The Oracle VSS writer automatically recovers the restored data files. If some archived logs are missing, then you can restore the logs and recover the data files with SQL\*Plus or RMAN.
5.  Bring the offline data files or tablespaces back online.

**Parent topic:** [About Restoring and Recovering a Database in ARCHIVELOG Mode](about-restoring-and-recovering-a-database-in-archivelog-mode.md)
