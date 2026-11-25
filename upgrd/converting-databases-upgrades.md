## About Converting Databases During Upgrades

Review these topics to determine which is the best path for you to select to upgrade Oracle Databases.

- [Overview of Converting Databases During Upgrades](overview-conveting-databases-during-upgrade.md)
  There are two methods to convert non-CDBs to multitenant architecture Oracle Databases during upgrades, and several different technologies you can use.
- [About Upgrading Using Standby Databases](upgrading-using-standby-databases.md)
  You can perform rolling upgrades of databases by using Active Oracle Data Guard, or by using Oracle Enterprise Manager Cloud Control.
- Overview of Steps for Upgrading Oracle Database Using Oracle GoldenGate
  Review these steps to obtain a high-level overview of how to upgrade Oracle Database using Oracle GoldenGate.
- [Migrating From Standard Edition to Enterprise Edition of Oracle Database](migrating-from-standard-to-enterprise--database.md)
  Review these options to migrate to Oracle Database Enterprise Edition from Oracle Database Standard Edition
- [Migrating from Enterprise Edition to Standard Edition of Oracle Database](migrating-from-enterprise-to-standard-database.md)
  Converting from Enterprise Edition to Standard Edition requires exporting and importing data, using the Export utility.
- [Migrating from Oracle Database Express Edition (Oracle Database XE) to Oracle Database](migrating-from-express-to-standard-database.md)
  You must upgrade from Oracle Database Express Edition to Oracle Database Enterprise Edition, and then upgrade to the current Oracle Database release.

**Parent topic:** [Introduction to Upgrading Oracle Database](intro-to-upgrading-oracle-database.md)

### Overview of Steps for Upgrading Oracle Database Using Oracle GoldenGate

Review these steps to obtain a high-level overview of how to upgrade Oracle Database using Oracle GoldenGate.

Upgrading to the new Oracle Database release using Oracle GoldenGate consists of the following steps.

1.  Set up a target database running the earlier Oracle Database software release, using an existing database backup.
2.  Upgrade the target database to the new Oracle Database release.
3.  Synchronize the target database with the production database.
4.  Test your environment in active/live mode.
5.  Switch over the application to the target database.
6.  Perform comprehensive testing of the new release on the target database, including enabling any features that were installed disabled by default that you plan to use in the new Oracle Database release.
7.  Upgrade the production database to the new Oracle Database release.

**Note:**

For complete details of this procedure, refer to the Oracle GoldenGate documentation.

**Related Topics**

- [Oracle GoldenGate documentation](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/upgrd&id=ogg)
- [Testing a Database Upgrade](../ratug/testing-a-database-upgrade.md)

**Parent topic:** About Converting Databases During Upgrades
