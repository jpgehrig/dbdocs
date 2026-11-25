Explains how to back up the entire database. You can back up only `Oracle Database,` `ArchiveLogDest_``n`, and `Fast Recovery Area`, listed in Components Backed Up by the Oracle VSS Writer.

To back up the entire database:

1.  Start a SQL\*Plus session on the target database and make sure the database is open `READ WRITE`.
2.  Use a third-party VSS requester to select the `Oracle Database` component.
3.  Create a snapshot of the database.
    Oracle VSS writer includes the server parameter file, control file, and data files in the snapshot. The online redo logs are not included in the snapshot.

**Parent topic:** [About Backing Up a Database in ARCHIVELOG Mode](about-backing-up-a-database-in-archivelog-mode.md)
