## Configure Shared Storage for the Oracle RAC Database

Before starting DBCA to configure an Oracle RAC database, you must have installed Oracle Grid Infrastructure for a cluster, and you must have configured shared storage areas for Oracle RAC files.

Storage administration tasks require the `SYSASM` system privileges, which are granted to members of the `OSASM` operating system group. This group may not be the same as the `OSDBA` group, whose members are granted the `SYSDBA` system privileges.

See [Oracle Grid Infrastructure Installation Guide](../install-and-upgrade.md) for your platform for more information about shared storage configuration requirements.

**Parent topic:** [Tasks to Complete Before Using DBCA to Create any Oracle RAC Database](tasks-to-complete-before-using-dbca-to-create-any-oracle-rac-database.md)
