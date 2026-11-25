## Locating Control Files

The preconfigured database contains two control files located in the `ORACLE_BASE\oradata``\DB_NAME` directory.

The preconfigured database contains two control files located in the `ORACLE_BASE\oradata``\DB_NAME` directory. Oracle recommends that you keep at least two control files (on separate physical drives) for each database, and set the `CONTROL_FILES` initialization parameter to list each control file.

A control file is an administrative file. Oracle Database requires a control file to start and run the database. The control file defines the physical structure of the database. For example, it defines the database name and the names and locations of the database data files and redo log files.

**See Also:**

[Oracle Database Administrator's Guide](../admin/creating-and-configuring-an-oracle-database.md)

For more information about using Oracle Enterprise Manager Database Express to perform various tasks related to tablespaces and data files, redo log files, and control files, click Help in the Oracle Enterprise Manager Database Express window.

**See Also:**

- [Oracle Database Administrator's Guide](../admin/creating-and-configuring-an-oracle-database.md)

- [Oracle Database 2 Day DBA](../admqs/managing-database-storage-structures.md) for information about “Viewing Control File”

**Parent topic:** [Getting Started with Oracle Database](getting-started-with-oracle-database.md)
