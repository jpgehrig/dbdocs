Learn about the differences between Oracle Database on Windows and UNIX. For Oracle Database developers and database administrators moving from a UNIX platform to Windows, this information can be helpful in understanding Windows features that are relevant to Oracle Database.

- [Automatic Startup and Shutdown](automatic-startup-and-shutdown.md)
  On UNIX, several files and scripts in different directories are used to start an instance automatically.
- [Background Processing and Batch Jobs](background-processing-and-batch-jobs.md)
  UNIX provides sophisticated control mechanisms for background processing and batch jobs.
- [Diagnostic and Tuning Utilities](diagnostic-and-tuning-utilities.md)
  On UNIX, utilities such as `sar` and `vmstat` are used to monitor Oracle Database background and shadow processes.
- [Direct Writes to Disk](direct-writes-to-disk.md)
  On both UNIX and Windows platforms, bypassing the file system buffer cache ensures data is written to disk.
- [Dynamic Link Libraries (DLLs)](dynamic-link-libraries.md)
  Shared libraries on UNIX are similar to shared DLLs on Windows.
- [Hot Backups](hot-backups.md)
  A (manual) hot backup is equivalent to backing up a tablespace that is in an offline backup mode.
- [Initialization Parameters: Multiple Database Writers](multiple-database-writers.md)
  On UNIX, you can specify many database writer process with initialization parameter `DB_WRITERS`.
- [Installation Accounts and Groups](installation-accounts-and-groups.md)
  UNIX uses the concept of a DBA group. The `root` account cannot be used to install Oracle Database.
- [Oracle Database Installation](installation.md)
  The following manual setup tasks, all required on UNIX, are not required on Windows:
- [Memory Resources](memory-resources.md)
  The resources provided by the UNIX default kernels are often inadequate for a medium or large instance of Oracle Database.
- [Microsoft Transaction Server](transaction-server.md)
  Windows coordinates distributed transactions through the Microsoft Distributed Transaction Coordinator (DTC), one of the components of Microsoft Transaction Server.
- [Multiple Oracle Homes and OFA](multiple-oracle-homes-and-ofa.md)
  The goal of OFA is to place all Oracle Database software under one `ORACLE_HOME` directory and to spread database files across different physical drives as databases increase in size.
- [Oracle Home User and Oracle User](oracle-home-user-and-oracle-user.md)
  On Linux and UNIX systems, you must create and use a software owner user account (`oracle`), and this user must belong to the Oracle Inventory group (`oinstall`) and also must be a member of the appropriate OSDBA, OSOPER, OSBACKUPDBA, OSDGDBA, and OSKMDBA groups.
- [Raw Partitions](raw-partitions.md)
  Data files for tablespaces may be stored on a file system or on raw partitions.
- [Windows Services](services.md)
  Windows services are similar to UNIX daemons.
