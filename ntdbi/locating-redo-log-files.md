## Locating Redo Log Files

The preconfigured database uses three redo log files. Redo log files record all changes made to data in the database buffer cache.

If an instance fails, then Oracle Database uses the redo log files to recover the modified data in memory.

Oracle Database uses redo log files in a cyclical fashion. For example, if three files constitute the online redo log, Oracle Database fills the first file, then the second file, and then the third file. In the next cycle, it reuses and fills the first file, the second file, and so on.

**See Also:**

- [Oracle Database 2 Day DBA](../admqs/managing-database-storage-structures.md) about Viewing Online Redo Log File Information

- [Oracle Database 2 Day DBA](../admqs/managing-database-storage-structures.md) about Viewing Archived Redo Log File Information

- [Oracle Database 2 Day DBA](../admqs/managing-database-storage-structures.md)

- [Oracle Database Backup and Recovery User's Guide](../bradv/backing-up-database.md)

**Parent topic:** [Getting Started with Oracle Database](getting-started-with-oracle-database.md)
