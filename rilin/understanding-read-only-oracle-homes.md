## Evolution of Oracle Homes

Learn about read-only Oracle home concepts like Oracle base home, Oracle base config, and orabasetab.

- [About Read-Only Oracle Homes](about-read-only-oracle-home.md)
  Starting with Oracle Database 18c, you can configure an Oracle home in read-only mode. A read-only Oracle home does not imply that the file system and the Oracle home is in read-only mode. The file system and mount point should always be in read/write mode.
- [About Oracle Base Homes](about-oracle-base-home.md)
  Both, in a read-only ORACLE_HOME and read/write ORACLE_HOME, the user-specific files, instance-specific files, and log files reside in a location known as the ORACLE_BASE_HOME.
- [About Oracle Base Config](about-oracle-base-config.md)
  Both, in a read-only ORACLE_HOME and read/write ORACLE_HOME, the configuration files reside in a location known as ORACLE_BASE_CONFIG.
- [About orabasetab](about-orabasetab.md)
  The `orabasetab` file is used to define fundamental directories based on \$ORACLE_HOME, ORACLE_BASE, ORACLE_BASE_HOME and ORACLE_BASE_CONFIG.

**Parent topic:** [Configuring Read-Only Oracle Homes](configuring-read-only-oracle-homes.md)
