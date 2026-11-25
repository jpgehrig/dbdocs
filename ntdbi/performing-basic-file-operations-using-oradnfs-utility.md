## Performing Basic File Operations Using the ORADNFS Utility

ORADNFS is a utility which enables the database administrators to perform basic file operations over Direct NFS Client on Microsoft Windows platforms.

ORADNFS is a multi-call binary, a single binary that acts like several utilities. This allows ORADNFS to be smaller since all the built-in commands can leverage DNFS code for many common operations. ORADNFS is run by issuing a command as an argument on the command line.

For example, `C:\> ORADNFS help` causes ORADNFS to print a list of built-in commands, and `C:\> ORADNFS ls C:\ORACLE\ORADATA\ORCL` causes ORADNFS to behave as an `ls` command of `C:\ORACLE\ORADATA\ORCL` remote directory, where `C:\ORACLE\ORADATA` is a DNFS virtual mount point specified in the `oranfstab` configuration file.

**Note:**

- A valid copy of the `oranfstab` configuration file must be present in `ORACLE_HOME``\dbs` directory for ORADNFS to operate.

- The user must be a member of the local `ORA_DBA` group to execute ORADNFS.

**Parent topic:** [Configuring File System Storage for Oracle Database](configuring-file-system-storage-oracle-database.md)
