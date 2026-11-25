## Creating Operating System Privileges Groups

The following sections describe how to create operating system groups for Oracle Grid Infrastructure and Oracle Database:

- Creating the OSDBA for ASM Group
  You must designate a group as the OSDBA for ASM (`asmdba`) group during installation. Members of this group are also allowed to access the Oracle Automatic Storage Management (Oracle ASM) disk devices.
- Creating the OSOPER for ASM Group
  You can choose to designate a group as the OSOPER for ASM group (`asmoper`) during installation. Members of this group are granted startup and shutdown privileges to Oracle Automatic Storage Management.
- Creating the OSDBA Group for Database Installations
  Each Oracle Database requires an operating system group to be designated as the OSDBA group. Members of this group are granted the SYSDBA system privileges to administer the database.
- Creating an OSOPER Group for Database Installations
  Create an OSOPER group only if you want to identify a group of operating system users with a limited set of database administrative privileges (SYSOPER operator privileges).
- Creating the OSBACKUPDBA Group for Database Installations
  You must designate a group as the OSBACKUPDBA group during installation. Members of this group are granted the SYSBACKUP privileges to perform backup and recovery operations using RMAN or SQL\*Plus.
- Creating the OSDGDBA Group for Database Installations
  You must designate a group as the OSDGDBA group during installation. Members of this group are granted the SYSDG privileges to perform Data Guard operations.
- Creating the OSKMDBA Group for Database Installations
  You must designate a group as the OSKMDBA group during installation. Members of this group are granted the SYSKM privileges to perform Transparent Data Encryption keystore operations.
- Creating the OSRACDBA Group for Database Installations
  You must designate a group as the OSRACDBA group during database installation. Members of this group are granted the SYSRAC privileges to perform day–to–day administration of Oracle databases on an Oracle RAC cluster.

**Parent topic:** [Configuring Users, Groups and Environments for Oracle Grid Infrastructure and Oracle Database](configuring-users-groups-and-environments-for-oracle-grid-infrastructure-and-oracle-database.md)

### Creating the OSDBA for ASM Group

You must designate a group as the OSDBA for ASM (`asmdba`) group during installation. Members of this group are also allowed to access the Oracle Automatic Storage Management (Oracle ASM) disk devices.

The Oracle ASM disk devices should be owned by this group.

Create an OSDBA for ASM group using the group name `asmdba` unless a group with that name already exists:

    # /usr/sbin/groupadd -g 54327 asmdba

**Parent topic:** Creating Operating System Privileges Groups

### Creating the OSOPER for ASM Group

You can choose to designate a group as the OSOPER for ASM group (`asmoper`) during installation. Members of this group are granted startup and shutdown privileges to Oracle Automatic Storage Management.

If you want to create an OSOPER for ASM group, use the group name `asmoper` unless a group with that name already exists:

    # /usr/sbin/groupadd -g 54328 asmoper

**Parent topic:** Creating Operating System Privileges Groups

### Creating the OSDBA Group for Database Installations

Each Oracle Database requires an operating system group to be designated as the OSDBA group. Members of this group are granted the SYSDBA system privileges to administer the database.

You must create an OSDBA group in the following circumstances:

- An OSDBA group does not exist, for example, if this is the first installation of Oracle Database software on the system

- An OSDBA group exists, but you want to give a different group of operating system users database administrative privileges for a new Oracle Database installation

Create the OSDBA group using the group name `dba`, unless a group with that name already exists:

    # /usr/sbin/groupadd -g 54322 dba

**Parent topic:** Creating Operating System Privileges Groups

### Creating an OSOPER Group for Database Installations

Create an OSOPER group only if you want to identify a group of operating system users with a limited set of database administrative privileges (SYSOPER operator privileges).

For most installations, it is sufficient to create only the OSDBA group. However, to use an OSOPER group, create it in the following circumstances:

- If an OSOPER group does not exist; for example, if this is the first installation of Oracle Database software on the system

- If an OSOPER group exists, but you want to give a different group of operating system users database operator privileges in a new Oracle installation

If the OSOPER group does not exist, or if you require a new OSOPER group, then create it. Use the group name `oper` unless a group with that name already exists. For example:

    # groupadd -g 54323 oper

**Parent topic:** Creating Operating System Privileges Groups

### Creating the OSBACKUPDBA Group for Database Installations

You must designate a group as the OSBACKUPDBA group during installation. Members of this group are granted the SYSBACKUP privileges to perform backup and recovery operations using RMAN or SQL\*Plus.

Create the OSBACKUPDBA group using the group name `backupdba`, unless a group with that name already exists:

    # /usr/sbin/groupadd -g 54324 backupdba

**Parent topic:** Creating Operating System Privileges Groups

### Creating the OSDGDBA Group for Database Installations

You must designate a group as the OSDGDBA group during installation. Members of this group are granted the SYSDG privileges to perform Data Guard operations.

Create the OSDGDBA group using the group name `dgdba,` unless a group with that name already exists:

    # /usr/sbin/groupadd -g 54325 dgdba

**Parent topic:** Creating Operating System Privileges Groups

### Creating the OSKMDBA Group for Database Installations

You must designate a group as the OSKMDBA group during installation. Members of this group are granted the SYSKM privileges to perform Transparent Data Encryption keystore operations.

If you want a separate group for Transparent Data Encryption, then create the OSKMDBA group using the group name `kmdba` unless a group with that name already exists:

    # /usr/sbin/groupadd -g 54326 kmdba

**Parent topic:** Creating Operating System Privileges Groups

### Creating the OSRACDBA Group for Database Installations

You must designate a group as the OSRACDBA group during database installation. Members of this group are granted the SYSRAC privileges to perform day–to–day administration of Oracle databases on an Oracle RAC cluster.

Create the OSRACDBA group using the groups name `racdba` unless a group with that name already exists:

    # /usr/sbin/groupadd -g 54330 racdba

**Parent topic:** Creating Operating System Privileges Groups
