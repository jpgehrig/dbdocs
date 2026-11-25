## About Read-Only Oracle Homes

Starting with Oracle Database 18c, you can configure an Oracle home in read-only mode.

A read-only Oracle home simplifies provisioning by implementing separation of installation and configuration.

In a read-only Oracle home, all the configuration data and log files reside outside of the read-only Oracle home.

Apart from the traditional ORACLE_BASE and ORACLE_HOME directories, the following directories contain files that used to be in ORACLE_HOME:

- ORACLE_BASE_HOME

- ORACLE_BASE_CONFIG

**Note:**

This feature does not affect how database administrators monitor, diagnose, and tune their system performance.

**Parent topic:** [Evolution of Oracle Homes](win-evolution-oracle-homes.md)
