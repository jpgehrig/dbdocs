Oracle Database provides an extended set of database groups to grant task-specific system privileges for database administration.

The extended set of Oracle Database system privileges groups are task-specific and less privileged than the OSDBA/SYSDBA system privileges. They are designed to provide privileges to carry out everyday database operations. Users granted these system privileges are also authorized through operating system group membership.

You do not have to create these specific group names, but during interactive and silent installation, you must assign operating system groups whose members are granted access to these system privileges. You can assign the same group to provide authorization for these privileges, but Oracle recommends that you provide a unique group to designate each privilege.

The subset of OSDBA job role separation privileges and groups consist of the following:

- OSBACKUPDBA group for Oracle Database (typically, `backupdba`)

  Create this group if you want a separate group of operating system users to have a limited set of database backup and recovery related administrative privileges (the SYSBACKUP privilege).

- OSDGDBA group for Oracle Data Guard (typically, `dgdba`)

  Create this group if you want a separate group of operating system users to have a limited set of privileges to administer and monitor Oracle Data Guard (the SYSDG privilege). To use this privilege, add the Oracle Database installation owners as members of this group.

- The OSKMDBA group for encryption key management (typically, `kmdba`)

  Create this group if you want a separate group of operating system users to have a limited set of privileges for encryption key management such as Oracle Wallet Manager management (the SYSKM privilege). To use this privilege, add the Oracle Database installation owners as members of this group.

- The OSRACDBA group for Oracle Real Application Clusters Administration (typically, `racdba`)

  Create this group if you want a separate group of operating system users to have a limited set of Oracle Real Application Clusters (RAC) administrative privileges (the SYSRAC privilege). To use this privilege:

  - Add the Oracle Database installation owners as members of this group.

  - For Oracle Restart configurations, if you have a separate Oracle Grid Infrastructure installation owner user (`grid`), then you must also add the `grid` user as a member of the OSRACDBA group of the database to enable Oracle Grid Infrastructure components to connect to the database.

**Related Topics**

- [Oracle Database Administrator’s Guide](../admin/managing-users-and-securing-the-database.md)
- [Oracle Database Security Guide](../dbseg/configuring-privilege-and-role-authorization.md)

**Parent topic:** [Oracle Installations with Standard and Job Role Separation Groups and Users](oracle-installations-with-standard-and-job-role-separation-groups-and-users.md)
