## Operating System Groups and Users for Job Role Separation

A job role separation configuration of Oracle Database and Oracle ASM is a configuration with groups and users to provide separate groups for operating system authentication.

- [About Job Role Separation Operating System Privileges Groups and Users](about-job-role-separaation-operating-system-privileges-groups-and-users.md)
  During the Oracle Database installation, the `ORA_DBA`, ` ORA_OPER`, ` ORA_HOMENAME_DBA`, ` ORA_HOMENAME_OPER`, `ORA_HOMENAME_SYSBACKUP`, `ORA_HOMENAME_SYSDG`, `ORA_HOMENAME_SYSKM`, and `ORA_HOMENAME_SYSRAC` groups are created and users assigned to these groups.
- [Oracle Software Owner for Each Oracle Software Product](oracle-softwaare-owner-for-each-oracle-software-product.md)
  You can create a single user (for example, `oracle`) to own both Oracle Database, and Oracle Restart installations.
- [Standard Oracle Database Groups for Job Role Separation](standard-oracle-db-grouos-for-job-separation-oracledb.md)
  Review the standard Oracle Database groups.
- [Extended Oracle Database Groups for Job Role Separation](extended-oracledb-groups-for-job-separation.md)
  In addition to the SYSOPER privilege to start up and shut down the database, you can create new administrative privileges that are more task-specific and less privileged than the `ORA_DBA`/SYSDBA system privileges to support specific administrative privileges tasks required for everyday database operation.
- [Oracle Automatic Storage Management Groups for Job Role Separation](oracle-automatic-storage-management-groups-for-job-role-separation.md)
  Review the operating system groups.
- [Windows Group Managed Service Accounts and Virtual Accounts](windows-managed-service-accounts-and-virtual-accounts.md)
  Group Managed Services Account (gMSA) and Virtual Accounts are now supported and enable you to create and manage Database services without passwords.
- [Microsoft Hyper-V Requirements](microsoft-hyperv-requirements.md)
  Microsoft Hyper-V enables you to create and manage a virtualized computing environment by running multiple operating systems simultaneously on a single computer and isolate operating systems from each other.

**Parent topic:** [Creating Required Operating System Groups and Users](creating-required-operating-system-groups-and-users.md)
