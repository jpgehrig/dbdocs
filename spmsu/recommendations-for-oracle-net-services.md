Review these procedures and parameter changes for Oracle Net Services before you upgrade.

In Oracle Database 12c, new underlying net services parameters enable data compression, which reduces the size of the session data unit that is transmitted over a SQL TCP connection.

The following new parameters for the `sqlnet.ora` file specify compression, and the preferred compression scheme:

- `SQLNET.COMPRESSION`

- `SQLNET.COMPRESSION_LEVELS`

- `SQLNET.COMPRESSION_THRESHOLD`

These parameters introduced with Oracle Database 12c are not supported in earlier releases. They are only available in Oracle Database 12c, and later releases For more information about these `sqlnet.ora` compression parameters, refer to Oracle Net Services Reference.

If the Oracle Database that you are upgrading does not have a listener configured, then before you run DBUA, you must run Oracle Net Configuration Assistant (NETCA) to configure the listening protocol address and service information for the new release of Oracle Database, including a `listener.ora` file. You must create a new version of the listener for releases of Oracle Database earlier than release 11.2. The current listener is backward-compatible with earlier Oracle Database releases.

When you upgrade an Oracle RAC database with DBUA, it automatically migrates the listener from your old Oracle home to the new Oracle Grid Infrastructure home. You must administer the listener by using the `lsnrctl` command in the Oracle Grid Infrastructure home. Do not attempt to use the `lsnrctl` commands from Oracle home locations for earlier releases.

**Related Topics**

- [Oracle Database Net Services Reference](../netrf/parameters-for-the-sqlnet.ora.md)

**Parent topic:** [Database Preparation Tasks to Complete Before Starting Oracle Database Upgrades](db-preparation-tasks-before-starting-db-upgrades.md)
