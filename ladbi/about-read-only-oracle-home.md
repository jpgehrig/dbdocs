## About Read-Only Oracle Homes

Starting with Oracle Database 18c, you can configure an Oracle home in read-only mode. A read-only Oracle home does not imply that the file system and the Oracle home is in read-only mode. The file system and mount point should always be in read/write mode.

A read-only Oracle home simplifies provisioning by implementing separation of installation and configuration.

In a read-only Oracle home, all the configuration data and log files reside outside of the read-only Oracle home. See, [File Path and Directory Changes in Read-Only Oracle Homes](file-path-directory-changes-read-only-oracle-home.md).

Apart from the traditional ORACLE_BASE and ORACLE_HOME directories, the following directories contain files that used to be in ORACLE_HOME:

- ORACLE_BASE_HOME

- ORACLE_BASE_CONFIG

Ensure that you enable read-only Oracle home before you create the database or listener.

When you run the `roohctl` script to enable a read-only Oracle home, the Oracle home file system will continue to be a read/write file system.

**Note:**

This feature does not affect how database administrators monitor, diagnose, and tune their system performance.

**Parent topic:** [Evolution of Oracle Homes](understanding-read-only-oracle-homes.md)
