## Standard Oracle Database Groups for Database Administrators

The Oracle Database supports multiple operating system groups to provide operating system authentication for database administration system privileges.

### OSDBA group (`ORA_DBA`)

When you install Oracle Database, a special Windows local group called `ORA_DBA` is created (if it does not already exist from an earlier Oracle Database installation), and the Oracle Installation user is automatically added to this group. Members of the `ORA_DBA` group automatically receive the SYSDBA privilege. Membership in the `ORA_DBA` group allows a user to:

- Connect to Oracle Database instances without a password

- Perform database administration procedures such as starting and shutting down local databases

- Add additional Windows users to `ORA_DBA`, enabling them to have the SYSDBA privilege

Membership in the `ORA_DBA` group grants full access to all databases on the server.

### OSDBA group for a particular Oracle home (`ORA_``HOMENAME``_DBA`)

This group is created the first time you install Oracle Database software into a new Oracle home. Membership in the `ORA_``HOMENAME``_DBA` group grants full access (SYSDBA privileges) for all databases that run from the specific Oracle home.

Belonging to either the `ORA_DBA` or `ORA_``HOMENAME``_DBA` group does not grant any special privileges for the user with respect to the Oracle ASM instance. Members of these groups will not be able to connect to the Oracle ASM instance.

### OSOPER group for Oracle Database (`ORA_OPER`)

This group is created the first time you install Oracle Database software into a new Oracle home. This optional group identifies operating system user accounts that have database administrative privileges (the SYSOPER system privilege) for the database instances that run from any Oracle home. Assign users to this group if you want a separate group of operating system users to have a limited set of database administrative privileges for starting up and shutting down any Oracle database.

### OSOPER group for a particular Oracle home (`ORA_``HOMENAME``_OPER`)

This group is created the first time you install Oracle Database software into a new Oracle home. This optional group identifies operating system user accounts that have database administrative privileges (the SYSOPER system privilege) for the database instances that run from a specific Oracle home. Assign users to this group if you want a separate group of operating system users to have a limited set of database administrative privileges for starting up and shutting down any Oracle database located in a specific Oracle home.

**Parent topic:** [Standard Administration and Job Role Separation User Groups](standard-administration-and-job-role-separation-user-groups.md)
