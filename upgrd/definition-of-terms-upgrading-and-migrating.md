## Definition of Terms Upgrading and Migrating

Upgrading and migrating are different types of database changes.

Upgrading transforms an existing Oracle Database environment (including installed components and associated applications) into a new release Oracle Database environment. The data dictionary for the database is upgraded to the new release. Upgrading does not directly affect user data; no data is touched, changed, or moved during an upgrade.

Migrating data refers to moving data from one Oracle Database into another database previously created for migrating or moving the data. You migrate data when you need to move your database environment to a new hardware or operating system platform, or to a new character set. Migrating does not include upgrading to the latest release. The upgrade process is handled separately after you migrate the data.

The upgrade steps in Oracle Database Upgrade Guide apply to all operating systems, unless otherwise specified. Some operating systems can require additional upgrade steps.

**Related Topics**

- [Oracle Database Installation Guide](../install-and-upgrade.md)
- [Oracle Database Utilities](../sutil/oracle-data-pump-export-utility.md)

**Parent topic:** [Overview of Oracle Database Upgrade Tools and Processes](overview-oracle-db-upgrade-tools-processes.md)
