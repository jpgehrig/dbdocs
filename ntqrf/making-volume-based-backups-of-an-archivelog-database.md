To make volume-based shadow copies of Oracle database when the database is open in read/write mode, the archived redo logs must be physically located on a separate volume from the volume containing the Oracle data files, control files, server parameter file, and online redo logs.

To back up the database and archived redo logs by volume:

1.  Start a SQL\*Plus session on the target database and make sure the database is open `READ WRITE`.
2.  Use a third-party VSS requester to select the volumes where the data files, control files, and server parameter file are physically located.
3.  Create a snapshot of the database files.
    Oracle VSS writer includes the server parameter file, control file, and data files in the snapshot. The online redo logs are not included in the snapshot. Note that you can restore the server parameter file individually, but the control files and data files must be always restored together.
4.  Use a third-party VSS requester to select the volumes where all of the archived redo logs (or the fast recovery area) are physically located.
5.  Create a snapshot of the archived redo logs.

**Parent topic:** [About Backing Up a Database in ARCHIVELOG Mode](about-backing-up-a-database-in-archivelog-mode.md)
