Use this procedure to create a standby database from shadow copies.

This section assumes that you have created a standby database on a host with the same file system structure as the primary database. This section also assumes that you have read Oracle Data Guard Concepts and Administration and are familiar with standby database creation and maintenance.

To create a standby database from shadow copies:

1.  Restore the database on the standby host.
2.  Start a SQL\*Plus session on the new database and a new standby control file must be obtained from primary database. You can create the control file with the SQL statement `ALTER DATABASE CREATE STANDBY CONTROLFILE`.
3.  Start the instance and mount the standby control file.

**See Also:**

[Oracle Data Guard Concepts and Administration](../sbydb/creating-oracle-data-guard-physical-standby.md)

**Related Topics**

- [Performing Disaster Recovery](performing-disaster-recovery.md)

**Parent topic:** [About Duplicating a Database](about-duplicating-a-database.md)
