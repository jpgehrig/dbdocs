## Configure Shared Storage for the Oracle RAC Database

Before starting Oracle Database Configuration Assistant (DBCA) to configure an Oracle RAC database, you must install Oracle Grid Infrastructure for a cluster, and configure shared storage areas for Oracle RAC files.

1.  Log in as a user with SYSASM system privileges.
    Storage administration tasks require the SYSASM system privileges, which are granted to members of the OSASM operating system group. This group may not be the same as the OSDBA group, whose members are granted the SYSDBA system privileges.
2.  On Windows-based systems, if you plan to use Oracle ASM storage, then before you use DBCA to create a database, you must perform the following steps:
    1.  Create logical drives either on extended partitions or primary partitions.
    2.  Delete the drive letters for these partitions on all nodes.
    3.  Stamp these partitions with `asmtoolg`.
    4.  After you have configured the disks to be used by Oracle ASM, you must create the disk groups that will be used by the database.
        You can create disk groups by using Oracle Automatic Storage Management Configuration Assistant (ASMCA), SQL\*Plus, or Oracle Enterprise Manager.

**See Also:**

- [Oracle Database Installation Guide for Microsoft Windows](../ntdbi/configuring-storage-for-oracle-automatic-storage-management.md) for more information about `asmtoolg`

- [Oracle Grid Infrastructure Installation Guide](../install-and-upgrade.md) for your platform more information on shared storage configuration requirements

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/create-diskgroups.md) for more information about creating disk groups

**Parent topic:** [Tasks to Complete Before Using DBCA to Create an Oracle RAC Database](tasks-to-complete-before-using-dbca-to-create-a-rac-database.md)
