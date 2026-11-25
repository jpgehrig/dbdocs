## Understanding Operating System Privileges Groups

As an administrator, you often perform special operations such as shutting down or starting up a database, or configuring storage.

Only an administrator, responsible for these administration decisions, should perform these operations. System privileges for Oracle Database or Oracle Automatic Storage Management (Oracle ASM) administration require a secure authentication scheme.

Membership in special operating system groups enables administrators to authenticate to Oracle Database or Oracle ASM through the operating system rather than with a user name and password. This is known as operating system authentication. Each Oracle Database in a cluster can have its own operating system privileges groups, so that operating system authentication can be separated for each Oracle Database on a cluster. Because there can be only one Oracle Grid Infrastructure installation on a cluster, there can be only one set of operating system privileges groups for Oracle ASM.

During installation of Oracle Grid Infrastructure and Oracle Database, the installer creates operating system groups. These operating system groups are designated with the logical role of granting operating system authentication for administration system privileges for Oracle Database and Oracle ASM. Oracle Grid Infrastructure uses operating system authentication to manage Oracle Database. To enable this access, you must set the `AUTHENTICATION_SERVICES` parameter in the `sqlnet.ora` file to contain the value NTS.

You can use a single operating system group as the logical group whose members are granted all system privileges for Oracle Database and Oracle ASM, or you can delegate system privileges to two or more operating system groups. Oracle recommends that you designate separate operating system groups for each logical system privilege. Using separate operating system groups enables you to grant one or more subsets of administrator system privileges to database administrators. These database administrators can then perform standard database administration tasks without requiring the SYSDBA system privileges.

**See Also:**

- "[Net Services Profile File (sqlnet.ora)](net-services-profile-file-sqlnet-ora.md)" for more information on how to set the `AUTHENTICATION_SERVICES` parameter.

- [Oracle Grid Infrastructure Installation and Upgrade Guide for Microsoft Windows](../cwwin/operating-system-groups-created-during-installation.md) for more information about operating system groups and Oracle Database system privileges.

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/authenticate-access-asm-instance.md) for more information about operating system groups and Oracle ASM system privileges.

**Parent topic:** [Understanding the Oracle RAC Installed Configuration](understanding-the-oracle-rac-installed-configuration.md)
