You can upgrade your operating system by installing a new operating system on a server, and then migrating your database either manually, or by using Export/Import method.

**Note:**

Confirm that the server operating system is supported, and that kernel and package requirements for the operating system meet or exceed the minimum requirements for the Oracle Database release to which you want to migrate.

### Manual, Command-Line Copy for Migrating Data and Upgrading Oracle Database

You can copy files to the new server and upgrade it manually. If you use this procedure, then you cannot use Oracle Database Upgrade Assistant. However, you can revert to your existing database if you encounter upgrade issues.

1.  Copy the database files from the computer running the previous operating system to the one running the new operating system.

2.  Re-create the control files on the computer running the new operating system.

3.  Manually upgrade the database using command-line scripts and utilities.

**See Also:**

[Oracle Database Upgrade Guide](../upgrd/manual-upgrade-scenarios-multitenant-architecture-oracle-databases.md) to review the procedure for upgrading the database manually, and to evaluate the risks and benefits of this option

### Export/Import Method for Migrating Data and Upgrading Oracle Database

You can install the operating system on the new server, install the new Oracle Database release on the new server, and then use Oracle Data Pump Export and Import utilities to migrate a copy of data from your current database to a new database in the new release. Data Pump Export and Import are recommended for higher performance and to ensure support for new data types.

**See Also:**

[Oracle Database Upgrade Guide](../upgrd/choose-an-upgrade-method-for-oracle-database.md) to review the Export/Import method for migrating data and upgrading Oracle Database

**Parent topic:** [Reviewing Operating System and Software Upgrade Best Practices](reviewing-operating-system-and-software-upgrade-best-practices.md)
