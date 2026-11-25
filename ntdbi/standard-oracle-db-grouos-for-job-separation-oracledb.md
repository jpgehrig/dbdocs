## Standard Oracle Database Groups for Job Role Separation

Review the standard Oracle Database groups.

The following is a list of standard Oracle Database groups. These groups provide operating system authentication for database administration system privileges:

**Note:**

All these groups are automatically created as a part of Oracle Database installation on Windows.

- The OSDBA group (`ORA_DBA`)

  Use this group the first time you install Oracle Database software on the system. This group identifies operating system user accounts that have database administrative privileges (the SYSDBA privilege) for all database instances running on the server.

  Members of the `ORA_DBA` group do not have SYSASM privileges on Oracle ASM instances, which are needed for mounting and dismounting disk groups.

- The OSOPER group for Oracle Database (`ORA_OPER`)

  Use this group if you want a separate group of operating system users to have a limited set of database administrative privileges for starting up and shutting down the database (the SYSOPER privilege).

- The OSDBA group for a particular Oracle home (`ORA_``HOMENAME``_DBA`)

  This group is created the first time you install Oracle Database software into a new Oracle home. This group identifies operating system user accounts that have database administrative privileges (the SYSDBA privilege) for the database instances that run from that Oracle home.

- The OSOPER group for a particular Oracle home (`ORA_``HOMENAME``_OPER`)

  Use this group if you want a separate group of operating system users to have a limited set of database administrative privileges for starting up and shutting down the database instances that run from a particular Oracle home (the SYSOPER privilege).

**Parent topic:** [Operating System Groups and Users for Job Role Separation](operating-system-groups-and-users-for-job-role-separation.md)
