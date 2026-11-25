Learn about backing up a database in ARCHIVELOG mode.

The procedures assume that the database is open read/write. You can also make closed and consistent backups.

- [Making Component-Based Backups of an ARCHIVELOG Database](making-component-based-backups-of-an-archivelog-database.md)
  Explains how to back up the entire database. You can back up only `Oracle Database,` `ArchiveLogDest_``n`, and `Fast Recovery Area`, listed in Components Backed Up by the Oracle VSS Writer.
- [Making Volume-Based Backups of an ARCHIVELOG Database](making-volume-based-backups-of-an-archivelog-database.md)
  To make volume-based shadow copies of Oracle database when the database is open in read/write mode, the archived redo logs must be physically located on a separate volume from the volume containing the Oracle data files, control files, server parameter file, and online redo logs.

**Related Topics**

- [About Backing Up a Database in NOARCHIVELOG Mode](about-backing-up-a-database-in-noarchivelog-mode.md)

**Parent topic:** [About Backing Up a Database](about-backing-up-a-database.md)
