## About ORATAB Configuration for Oracle RAC

Oracle creates an entry for each Oracle RAC database in the `oratab` configuration file.

The `oratab` file is created by the `root.sh` script during installation, and it is updated by the Database Configuration Assistant when creating or deleting a database.

Oracle ASM Agent creates Oracle ASM `oratab` entries if the node is pinned in the CSS. The `oratab` file entry is also created automatically by the Database Agent when a database is first started on a node where it has not run previously, if your system meets any of the following conditions:

- The database release is Oracle Database 12c Release 1 (12.1) or earlier
- The database is a single instance Oracle Database
- The database is an admin-managed Oracle RAC database

Oracle Enterprise Manager uses the `oratab` file during service discovery to determine the name of the Oracle RAC database, and to determine if the database must be started automatically when the system is restarted.

The database entry has the following syntax:

    $DB_UNIQUE_NAME:$ORACLE_HOME:N

A colon (:) is used as the field terminator. A new line terminates the entry. Lines beginning with a pound sign (#) are comments. Because all the instances of an Oracle RAC database have the same `DB_UNIQUE_NAME`, but each instance has its own `ORACLE_SID`, use the `$DB_UNIQUE_NAME` environment variable in the `oratab` file as the database entry.

The `$DB_UNIQUE_NAME` identifier for your Oracle RAC database must be unique across your enterprise. `$ORACLE_HOME` is the directory path to the database, and `N` indicates that the database should not be started at restart time. The following is an example entry for a database named `sales`:

    sales:/u01/app/oracle/sales:N

**Parent topic:** [Understanding the Oracle RAC Installed Configuration](understanding-the-oracle-rac-installed-configuration.md)
