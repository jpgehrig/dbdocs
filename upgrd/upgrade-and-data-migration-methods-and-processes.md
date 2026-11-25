## Upgrade and Data Migration Methods and Processes

Oracle provides features and products to automate the upgrade process, and to assist you with completing upgrades efficiently.

Oracle Database supports the following methods for upgrading or migrating a database to the new release:

- AutoUpgrade Utility

  Identifies issues before upgrades, deploys upgrades, performs postupgrade actions, and starts the upgraded Oracle Database.

- Database Upgrade Assistant (DBUA)

  Provides a graphical user interface that guides you through the upgrade of a database. DBUA can be launched during installation with the Oracle Universal Installer, or you can launch DBUA as a standalone tool at any time in the future.

- Manual upgrade using the Parallel Upgrade Utility, and other command-line utilities

  Enables upgrades to be performed using shell scripts.

- Migrating data using Oracle Data Pump

  Provides export and import utilities. Oracle Data Pump can perform a full or partial export from your database, followed by a full, or partial import into the new release of Oracle Database. Export/Import in Oracle Data Pump can copy a subset of the data, leaving the database unchanged.

- `CREATE TABLE AS` SQL statement

  Migrates data from a database into a new Oracle Database release. By using this method, you can copy a subset of the data, leaving the database unchanged.

- Upgrading CDBs and PDBs using a priority list to group and upgrade PDBs according to their priority.

  Run the Parallel Upgrade Utility (`dbupgrade`, or `catctl.pl`) using the `-L` option to run the upgrade using a priority list, and to call that list as the upgrade runs.

- Synchronizing a standby database, upgrading, and using Oracle GoldenGate to synchronize the upgraded database (a zero downtime option)

- Using Fleet Patching and Provisioning (FPP) to upgrade databases.

  In a Fleet Patching and Provisioning (FPP) upgrade (formerly known as Rapid Home Provisioning), you complete a new Oracle Database installation. After testing the database, and modifying it in accordance with the standard operating environment (SOE) that you want to use for your databases, you create an FPP gold image. A DBA deploys instances of that gold image to servers that have earlier release databases that you want to upgrade. After deployment of these gold images, a DBA can run a single `rhpctl` command to move files, perform configuration changes, and perform other steps required to use the new binaries. Refer to Oracle Clusterware Administration and Deployment Guide for more information about Rapid Home Provisioning.

**Related Topics**

- [Oracle Clusterware Administration and Deployment Guide](../fppad/upgrading-oracle-database-software.md)

**Parent topic:** [Overview of Oracle Database Upgrade Tools and Processes](overview-oracle-db-upgrade-tools-processes.md)
