## Performing Basic File Operations Using the ORADNFS Utility

ORADNFS is a utility which enables the database administrators to perform basic file operations over Direct NFS Client on Microsoft Windows platforms.

ORADNFS is a multi-call binary, which is a single binary that acts like many utilities.

You must be a member of the local `ORA_DBA` group to use ORADNFS. A valid copy of the `oranfstab` configuration file must be present in `Oracle_home``\dbs` for ORADNFS to operate.

- To execute commands using ORADNFS you issue the command as an argument on the command line.
  The following command prints a list of commands available with ORADNFS:
      C:\> oradnfs help

  To display the list of files in the NFS directory mounted as `C:\ORACLE\ORADATA`, use the following command:
      C:\> oradnfs ls C:\ORACLE\ORADATA\ORCL

**Parent topic:** [Configuring Direct NFS Client for Oracle RAC Data Files](configuring-direct-nfs-client-for-oracle-rac-data-files.md)
