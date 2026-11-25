## About Changes in Default SGA Permissions for Oracle Database

Starting with Oracle Database 12c Release 2 (12.2.0.1), by default, permissions to read and write to the System Global Area (SGA) are limited to the Oracle software installation owner.

In previous releases, both the Oracle installation owner account and members of the OSDBA group had access to shared memory. The change in Oracle Database 12c Release 2 (12.2) and later releases to restrict access by default to the Oracle installation owner account provides greater security than previous configurations. However, this change may prevent DBAs who do not have access to the Oracle installation owner account from administering the database.

The Oracle Database initialization parameter ALLOW_GROUP_ACCESS_TO_SGA determines if the Oracle Database installation owner account (`oracle` in Oracle documentation examples) is the only user who can read and write to the database System Global Area (SGA), or if members of the OSDBA group can read the SGA. In Oracle Database 12c Release 2 (12.2) and later releases, the default value for this parameter is FALSE, so that only the Oracle Database installation owner has read and write permissions to the SGA. Group access to the SGA is removed by default. This change affects all Linux and UNIX platforms.

If members of the OSDBA group require read access to the SGA, then you can change the initialization parameter ALLOW_GROUP_ACCESS_TO_SGA setting from FALSE to TRUE. Oracle strongly recommends that you accept the default permissions that limit access to the SGA to the `oracle` user account.

**Related Topics**

- [Oracle Database Reference](../refrn/ALLOW_GROUP_ACCESS_TO_SGA.md)

**Parent topic:** [Oracle Grid Infrastructure Postinstallation Tasks](oracle-grid-infrastructure-postinstallation-tasks.md)
