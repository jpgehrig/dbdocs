## Extended Oracle Database Administration Groups for Job Role Separation

Oracle Database 12c Release 1 (12.1) and later releases provide an extended set of database groups to grant task-specific system privileges for database administration.

The extended set of Oracle Database system privileges groups are task-specific and less privileged than the ORA_DBA/SYSDBA system privileges. They are designed to provide privileges to carry out everyday database operations. Users granted these system privileges are also authorized through operating system group membership.

The installer automatically creates operating system groups whose members are granted these system privileges. The subset of OSDBA job role separation privileges and groups consist of the following:

- OSBACKUPDBA group for Oracle Database (`ORA_``HOMENAME``_SYSBACKUP`)

  Assign users to this group if you want a separate group of operating system users to have a limited set of database backup- and recovery-related administrative privileges (the SYSBACKUP privilege).

- OSDGDBA group for Oracle Data Guard (`ORA_``HOMENAME``_SYSDG`)

  Assign users to this group if you want a separate group of operating system users to have a limited set of privileges to administer and monitor Oracle Data Guard (the SYSDG privilege). To use this privilege, add the Oracle Database installation owners as members of this group.

- OSKMDBA group for encryption key management (`ORA_``HOMENAME``_SYSKM`)

  Assign users to this group if you want a separate group of operating system users to have a limited set of privileges for encryption key management such as Oracle Wallet Manager management (the SYSKM privilege). To use this privilege, add the Oracle Database installation owners as members of this group.

- OSRACDBA group for Oracle Real Application Clusters Administration (typically, `ORA_``HOMENAME``_SYSRAC`)

  Assign users to this group if you want a separate group of operating system users to have a limited set of Oracle Real Application Clusters (RAC) administrative privileges (the SYSRAC privilege). To use this privilege, add the Oracle Database installation owners as members of this group.

You cannot change the name of these operating system groups. These groups do not have any members after database creation, but an Administrator user can assign users to these groups after installation. Each operating system group identifies a group of operating system users that are granted the associated set of database privileges.

**See Also:**

- [Oracle Database Administrator’s Guide](../admin/getting-started-with-database-administration.md) for more information about the OSDBA, OSASM, OSOPER, OSBACKUPDBA, OSDGDBA, OSKMDBA, and OSRACDBA groups, and the SYSDBA, SYSASM, SYSOPER, SYSBACKUP, SYSDG, SYSKM, and SYSRAC privileges

- The "Managing Administrative Privileges" section in [Oracle Database Security Guide](../dbseg/configuring-privilege-and-role-authorization.md)

**Parent topic:** [Standard Administration and Job Role Separation User Groups](standard-administration-and-job-role-separation-user-groups.md)
