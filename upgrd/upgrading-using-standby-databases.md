## About Upgrading Using Standby Databases

You can perform rolling upgrades of databases by using Active Oracle Data Guard, or by using Oracle Enterprise Manager Cloud Control.

The `DBMS_ROLLING` PL/SQL package enables you to upgrade the database software in an Oracle Data Guard configuration in a rolling fashion. Rolling upgrades using Active Data Guard uses an Oracle Data Guard physical standby database and the SQL Apply process. Using Data Guard for rolling upgrades is supported for Oracle Database 12c release 1 (12.1) and later Oracle Database releases.

With Oracle Database 12c release 2 (12.2) and later releases, when you perform a rolling upgrade using the DBMS_ROLLING PL/SQL package, you no longer need to disable the broker. In addition, the broker now reports when a rolling upgrade is in place, and tracks its status. The status information is displayed in the output of the DGMGRL commands SHOW CONFIGURATION and SHOW DATABASE.

Oracle Enterprise Manager Cloud Control provides options to perform a rolling upgrade of databases in a Data Guard configuration. The procedures are described in online help within Cloud Control.

**See Also:**

- [Oracle Data Guard Broker](../dgbkr/upgrading-downgrading-in-data-guard-broker-configuration.md) for information about upgrading and downgrading in an Oracle Data Guard broker configuration

- [Oracle Data Guard Concepts and Administration](../sbydb/using-DBMS_ROLLING-to-perform-rolling-upgrade.md) for information about using `DBMS_ROLLING` to perform a rolling upgrade.

**Parent topic:** [About Converting Databases During Upgrades](converting-databases-upgrades.md)
