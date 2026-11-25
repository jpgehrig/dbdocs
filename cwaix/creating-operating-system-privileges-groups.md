The following sections describe how to create operating system groups for Oracle Grid Infrastructure and Oracle Database:

- [Creating the OSASM Group](creating-the-osasm-group.md)
  If the OSASM group does not exist, or if you require a new OSASM group, then create it.
- [Creating the OSDBA for ASM Group](creating-the-osdba-for-asm-group.md)
  You must designate a group as the OSDBA for ASM (`asmdba`) group during installation. Members of this group are granted access privileges to Oracle Automatic Storage Management.
- [Creating the OSOPER for ASM Group](creating-the-osoper-for-asm-group.md)
  You can choose to designate a group as the OSOPER for ASM group (`asmoper`) during installation. Members of this group are granted startup and shutdown privileges to Oracle Automatic Storage Management.
- [Creating the OSDBA Group for Database Installations](creating-the-osdba-group-for-database-installations.md)
  Each Oracle Database requires an operating system group to be designated as the OSDBA group. Members of this group are granted the SYSDBA system privileges to administer the database.
- [Creating an OSOPER Group for Database Installations](creating-an-osoper-group-for-database-installations.md)
  Create an OSOPER group only if you want to identify a group of operating system users with a limited set of database administrative privileges (SYSOPER operator privileges).
- [Creating the OSBACKUPDBA Group for Database Installations](creating-the-osbackupdba-group-for-database-installations.md)
  You must designate a group as the OSBACKUPDBA group during installation. Members of this group are granted the SYSBACKUP privileges to perform backup and recovery operations using RMAN or SQL Plus.
- [Creating the OSDGDBA Group for Database Installations](creating-the-osdgdba-group-for-database-installations.md)
  You must designate a group as the OSDGDBA group during installation. Members of this group are granted the SYSDG privileges to perform Data Guard operations.
- [Creating the OSKMDBA Group for Database Installations](creating-the-oskmdba-group-for-database-installations.md)
  You must designate a group as the OSKMDBA group during installation. Members of this group are granted the SYSKM privileges to perform Transparent Data Encryption keystore operations.
- [Creating the OSRACDBA Group for Database Installations](creating-the-osracdba-group.md)
  You must designate a group as the OSRACDBA group during installation. Members of this group are granted the SYSRAC privileges to perform day to day administration of Oracle databases on a RAC cluster.

**Parent topic:** [Configuring Users, Groups and Environments for Oracle Grid Infrastructure and Oracle Database](configuring-users-groups-and-environments-for-oracle-grid-infrastructure-and-oracle-database.md)
