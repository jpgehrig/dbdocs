## Standard Administration and Job Role Separation User Groups

Oracle Grid Infrastructure uses various operating system groups.

These operating system groups are designated with the logical role of granting operating system group authentication for administration system privilege for Oracle Clusterware and Oracle ASM.

- [About Job Role Separation Operating System Privileges Groups and Users](about-job-role-separation-operating-system-privileges-groups-and-users.md)
  Job role separation requires that you create different operating system groups for each set of system privileges that you grant through operating system authorization.
- [Oracle Software Owner for Each Oracle Software Product](oracle-software-owner-for-each-oracle-software-product.md)
  Oracle recommends that you use appropriate operating system groups and users for all installations where you specify separate Oracle Home Users:
- [Standard Oracle Database Groups for Database Administrators](standard-oracle-database-groups-for-database-administrators.md)
  The Oracle Database supports multiple operating system groups to provide operating system authentication for database administration system privileges.
- [Oracle ASM Groups for Job Role Separation](oracle-asm-groups-for-job-role-separation.md)
  The SYSASM, SYSOPER for ASM, and SYSDBA for ASM system privileges enables the separation of the Oracle ASM storage administration privileges from SYSDBA.
- [Extended Oracle Database Administration Groups for Job Role Separation](extended-oracle-database-administration-groups-for-job-role-separation.md)
  Oracle Database 12c Release 1 (12.1) and later releases provide an extended set of database groups to grant task-specific system privileges for database administration.
- [Operating System Groups Created During Installation](operating-system-groups-created-during-installation.md)
  When you install either Oracle Grid Infrastructure or Oracle RAC, the user groups listed in the following table are created, if they do not already exist.
- [Example of Using Role-Allocated Groups and Users](example-of-using-role-allocated-groups-and-users.md)
  You can use role-allocated groups and users that is compliant with an Optimal Flexible Architecture (OFA) deployment.

**Parent topic:** [Configuring Users, Groups and Environments for Oracle Grid Infrastructure and Oracle RAC](configuring-users-groups-and-environments-for-oracle-grid-infrastructure-and-oracle-rac.md)
