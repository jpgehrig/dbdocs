## Server Minimum Storage Requirements

Each system must meet certain minimum storage requirements.

- 1 GB of space in the `%TEMP%` directory.

  If the free space available in the `%TEMP%` directory is less than what is required, then complete one of the following steps:

  - Delete unnecessary files from the `%TEMP%` directory to make available the space required.

  - Extend the file system that contains the `%TEMP%` directory. If necessary, contact your system administrator for information about extending file systems.

- At least 12 GB of space for the Oracle Grid Infrastructure for a cluster home (Grid home). Oracle recommends that you allocate 100 GB to allow additional space for patches.

- At least 3.5 GB of space for the Oracle base of the Oracle Grid Infrastructure Installation user. The Oracle base includes Oracle Clusterware and Oracle ASM log files.

- If you intend to install Oracle Database, then allocate 7.5 GB of disk space for the Oracle home (the location for the Oracle Database software binaries).

  If you plan to configure automated database backups for your Oracle Database, then you require additional space either in a file system or in an Oracle Automatic Storage Management disk group for the Fast Recovery Area.

**Note:**

The base directory for Oracle Grid Infrastructure 12c and the base directory for Oracle RAC 12c must be different from the directories used by any Oracle RAC 11g Release 2 installations.

**Parent topic:** [Configuring Servers for Oracle Grid Infrastructure and Oracle RAC](configuring-servers-for-oracle-grid-infrastructure-and-oracle-rac.md)
