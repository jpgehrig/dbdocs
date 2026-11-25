Learn how to start an instance and services using ORADIM.

To use ORADIM to start an instance and services, enter:

    oradim -STARTUP -SID SID | -ASMSID SID [-SYSPWD password] [-STARTTYPE srvc |
    inst | srvc,inst] [-PFILE filename | -SPFILE]

For this command, note the following:

- `-STARTUP` indicates that you are starting an instance that already exists. This is a mandatory parameter.

- `-SID` `SID` is the name of the instance to start.

- `-ASMSID ``SID` is the name of the Oracle Automatic Storage Management instance to start.

- `-STARTTYPE` `srvc`, `inst` indicates whether to start the service or the instance. One or both values can be specified. If it is not specified, then the registry is checked for the current setting.

  `-STARTTYPE srvc` is the equivalent of running `net start oracleservice``sid` from the command line.

  `-STARTTYPE inst` is the equivalent of running `startup` within SQL\*Plus.

- `-PFILE` `filename` is the initialization parameter file to be used with this instance. Ensure that you specify the complete path name of this file, including drive letter.

- `-SPFILE` indicates that a server parameter file (SPFILE) be used during startup instead of a PFILE.

To start an instance called `puma`, for example, enter:

    C:\> oradim -STARTUP -SID puma -STARTTYPE inst -PFILE C:\app\username\admin\prod\pfile\init.ora

**Parent topic:** [About Administering an Oracle Database Instance Using ORADIM](about-administering-an-oracle-database-instance-using-oradim.md)
