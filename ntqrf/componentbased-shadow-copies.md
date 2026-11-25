The Oracle VSS writer supports component-based shadow copies, which are sets of database files.

The recommended technique for backing up an Oracle Database with VSS writer is to create shadow copies of components. During a backup, the Oracle VSS writer saves the redo generated during snapshot creation in a metadata document. During a restore operation, the writer automatically extracts the redo from the metadata document and applies it to files restored from a snapshot.

**Parent topic:** [Basic Concepts of Database Backup and Recovery with VSS](basic-concepts-of-database-backup-and-recovery-with-vss.md)
