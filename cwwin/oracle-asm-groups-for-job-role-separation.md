## Oracle ASM Groups for Job Role Separation

The SYSASM, SYSOPER for ASM, and SYSDBA for ASM system privileges enables the separation of the Oracle ASM storage administration privileges from SYSDBA.

During installation, the following groups are created for Oracle ASM:

- OSASM Group for Oracle ASM Administration (`ORA_ASMADMIN`)

  Use this separate group to have separate administration privilege groups for Oracle ASM and Oracle Database administrators. Members of this group are granted the SYSASM system privilege to administer Oracle ASM. In Oracle documentation, the operating system group whose members are granted privileges is called the OSASM group. During installation, the Oracle Installation User for Oracle Grid Infrastructure and Oracle Database Service IDs are configured as members of this group. Membership in this group also grants database access to the ASM disks.

  Members of the OSASM group can use SQL to connect to an Oracle ASM instance as SYSASM using operating system authentication. The SYSASM system privilege permits mounting and dismounting disk groups, and other storage administration tasks. SYSASM system privileges do not grant access privileges on an Oracle Database instance.

- OSDBA for ASM Database Administrator group (`ORA_ASMDBA`)

  This group grants access for the database to connect to Oracle ASM. During installation, the Oracle Installation Users are configured as members of this group. After you create an Oracle Database, this groups contains the Oracle Home Users of those database homes.

- OSOPER for ASM Group for ASM Operators (`ORA_ASMOPER`)

  This is an optional group. Use this group if you want a separate group of operating system users to have a limited set of Oracle ASM instance administrative privileges (the SYSOPER for ASM system privilege), including starting up and stopping the Oracle ASM instance. By default, members of the OSASM group also have all privileges granted by the SYSOPER for ASM system privilege.

  To use the Oracle ASM Operator group to create an Oracle ASM administrator with fewer privileges than those granted by the SYSASM system privilege you must assign the user to this group after installation.

**Parent topic:** [Standard Administration and Job Role Separation User Groups](standard-administration-and-job-role-separation-user-groups.md)
