## Extended Oracle Database Groups for Job Role Separation

In addition to the SYSOPER privilege to start up and shut down the database, you can create new administrative privileges that are more task-specific and less privileged than the `ORA_DBA`/SYSDBA system privileges to support specific administrative privileges tasks required for everyday database operation.

Users granted these system privileges are also authenticated through operating system group membership.

During installation, you are prompted to provide operating system groups whose members are granted access to these system privileges. You can assign the same group to provide authentication for these privileges (for example, `ORA_DBA`), but Oracle recommends that you provide a unique group to designate each privilege.

The OSDBA subset job role separation privileges and groups consist of the following:

- The OSBACKUPDBA group for Oracle Database (`ORA_``HOMENAME``_SYSBACKUP`)

  Use this group if you want a separate group of operating system users to have a limited set of database backup and recovery related administrative privileges (the SYSBACKUP privilege).

- The OSDGDBA group for Oracle Data Guard (`ORA_``HOMENAME``_SYSDG`)

  Use this group if you want a separate group of operating system users to have a limited set of privileges to administer and monitor Oracle Data Guard (the SYSDG privilege).

- The OSKMDBA group for encryption key management (`ORA_``HOMENAME``_SYSKM`)

  Use this group if you want a separate group of operating system users to have a limited set of privileges for encryption key management such as Oracle Wallet Manager management (the SYSKM privilege).

- The OSRACDBA group for Oracle Real Application Clusters Administration (`ORA_``HOMENAME``_SYSRAC`)

  Use this group if you want a separate group of operating system users to have a limited set of Oracle Real Application Clusters (RAC) administrative privileges (the SYSRAC privilege). To use this privilege:

  - Add the Oracle Database installation owners as members of this group.

**Note:**

All these groups, `ORA_``HOMENAME``_SYSBACKUP`, `ORA_``HOMENAME``_SYSDG`, `ORA_``HOMENAME``_SYSKM`, and `ORA_``HOMENAME``_SYSRAC `are applicable only to the database instances running from that particular Oracle home.

**Parent topic:** [Operating System Groups and Users for Job Role Separation](operating-system-groups-and-users-for-job-role-separation.md)
