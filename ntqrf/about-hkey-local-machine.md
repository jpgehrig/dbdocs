Each time you install Oracle products into a new Oracle home on your computer, `HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\KEY_``HOMENAME` is created.

This subkey contains parameter values for most Oracle products.

`HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\KEY_``HOMENAME` includes the following parameters for an Oracle home directory. Depending on products you install, additional parameters can also be created. See your Windows development manuals.

- [MSHELP_TOOLS](mshelp-tools.md)
  Specifies the location of Windows help files.
- [NLS_LANG and Other Globalization Parameters](nls-lang-and-other-globalization-parameters.md)
  Specifies supported language, territory, and character set.
- [ORA_CWD](ora-cwd.md)
  Specifies current working directory.
- [ORA_SID_AUTOSTART](ora-sid-autostart.md)
  Starts Oracle Database when `OracleService``SID` service is started.
- [ORA_SID_PFILE](ora-sid-pfile.md)
  Specifies full path to initialization parameter file.
- [ORA_SID_SHUTDOWN](ora-sid-shutdown.md)
  When set to `true`, the default value, this parameter shuts down the instance of Oracle Database identified by `SID` when `OracleService``SID` is stopped manually—using either the Control Panel or Net stop command.
- [ORA_SID_SHUTDOWN_TIMEOUT](ora-sid-shutdown-timeout.md)
  Sets maximum time (in seconds) to wait for shutdown to complete before the service for a particular `SID` stops.
- [ORA_SID_SHUTDOWNTYPE](ora-sid-shutdowntype.md)
  Specifies mode in which Oracle Database is shut down when you stop `OracleService``SID`.
- [ORA_TZFILE](ora-tzfile.md)
  Specifies the location of time zone file.
- [ORACLE_AFFINITY](oracle-affinity.md)
  Enables the scheduling of class threads on more than one processor group for systems with more than 64 CPUs.
- [ORACLE_BASE](oraclebase.md)
  Specifies the top-level Oracle directory (for example, `C:\app\username\product\12.2.0`) that contains `ORACLE_HOME`, `admin`, and `oradata`.
- [ORACLE_GROUP_NAME](oracle-group-name.md)
  Specifies the name of the group containing icons of the Oracle products installed.
- [ORACLE_HOME](oraclehome.md)
  Specifies Oracle home directory in which Oracle products are installed.
- [ORACLE_HOME_KEY](oracle-home-key.md)
  The `HKEY_LOCAL_MACHINE` location of Oracle parameters.
- [ORACLE_HOME_USER](oracle-home-user.md)
  A string type entry that holds the Oracle Home User value.
- [ORACLE_HOMENAME](oracle-homename.md)
  Specifies home name of Oracle home directory in which Oracle products are installed.
- [ORACLE_PRRITY](oracle-prrity.md)
  Determines Windows scheduling priorities of the threads within the Oracle Database management system process.
- [ORACLE_SID](oracle-sid.md)
  Specifies the name of the Oracle Database instance on the host computer.
- [OSAUTH_PREFIX_DOMAIN](osauth-prefix-domain.md)
  Enables user authentication.
- [RDBMS_ARCHIVE](rdbms-archive.md)
  Specifies the location of backup database files.
- [RDBMS_CONTROL](rdbms-control.md)
  Specifies the location of backup database control files.
- [SQLPATH](sqlpath.md)
  Specifies the location of SQL scripts.

**See Also:**

[Oracle Database Installation Guide for Microsoft Windows](../ntdbi/index.md) Appendix B, "Optimal Flexible Architecture" for details on the PATH variable and registry values when you are working with multiple Oracle homes.

**Parent topic:** [Registry Parameters Overview](registry-parameters--overview.md)
