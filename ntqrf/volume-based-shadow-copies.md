The Oracle VSS writer supports volume-based shadow copies, which are snapshots of complete drive or volumes.

Oracle Database places the files that it manages in a state suitable to create shadow copies. For example, the data files are placed in hot backup mode and a new snapshot control file is created for a database in `ARCHIVELOG` mode. Oracle VSS writer excludes files such as the current control file and online redo logs from the shadow copies. The writer also returns an error if the snapshot cannot be taken. For example, if a `NOARCHIVELOG` database is open in read/write mode, then the writer returns an error indicating that the snapshot is not possible.

**Note:**

Oracle Automatic Storage Management files and raw files are not supported for Oracle VSS snapshots.

**Parent topic:** [Basic Concepts of Database Backup and Recovery with VSS](basic-concepts-of-database-backup-and-recovery-with-vss.md)
