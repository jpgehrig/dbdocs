## Oracle Automatic Storage Management Groups for Job Role Separation

Review the operating system groups.

Create the following operating system groups if you are installing Oracle Grid Infrastructure:

- The OSDBA group for Oracle ASM (`ORA_ASMDBA)`

  This group grants access for the database to connect to Oracle ASM. During installation, the Oracle Installation Users are configured as members of this group. After you create an Oracle Database, this group contains the Oracle Home Users of those database homes. Any client of Oracle ASM that needs to access storage managed by Oracle ASM needs to be in this group.

- The OSASM group for Oracle ASM Administration (`ORA_ASMADMIN`)

  Use this separate group to have separate administration privilege groups for Oracle ASM and Oracle Database administrators. Members of this group are granted the SYSASM system privilege to administer Oracle ASM. In Oracle documentation, the operating system group whose members are granted privileges is called the OSASM group. During installation, the Oracle Installation User for Oracle Grid Infrastructure and Oracle Database Service IDs are configured as members of this group. Membership in this group also grants database access to the Oracle ASM disks.

  Members of the OSASM group can use SQL to connect to an Oracle ASM instance as SYSASM using operating system authentication. The SYSASM privilege permits mounting and dismounting disk groups, and other storage administration tasks. SYSASM system privileges do not grant access privileges on an Oracle Database instance.

- The OSOPER group for Oracle ASM (`ORA_ASMOPER`)

  This is an optional group. Create this group if you want a separate group of operating system users to have a limited set of Oracle ASM instance administrative privileges (the SYSOPER for ASM privilege), including starting up and stopping the Oracle ASM instance. By default, members of the OSASM group also have all privileges granted by the SYSOPER for ASM privilege.

  To use the Oracle ASM Operator group to create an Oracle ASM administrator with fewer privileges than those granted by the SYSASM system privilege you must assign the user to this group after installation.

  **See Also:**

  - [Oracle Database Administrator’s Guide](../admin/getting-started-with-database-administration.md)

  - [Oracle Database Security Guide](../dbseg/configuring-privilege-and-role-authorization.md)

**Parent topic:** [Operating System Groups and Users for Job Role Separation](operating-system-groups-and-users-for-job-role-separation.md)
