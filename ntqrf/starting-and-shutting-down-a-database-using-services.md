Learn how to start and shut down a database using services.

You can start or shut down Oracle Database by starting or stopping the service `OracleService``SID` in the Control Panel. Starting `OracleService``SID` is equivalent to using the `STARTUP` command or manually entering:

    C:\> oradim -STARTUP -SID SID [-STARTTYPE srvc | inst | srvc,inst] [-PFILE
    filename | -SPFILE]

Stopping `OracleService``SID` is equivalent to using the `SHUTDOWN` command or manually entering:

    C:\> oradim -SHUTDOWN -SID SID [-SHUTTYPE srvc | inst | srvc,inst] [-SHUTMODE
    normal | immediate | abort]

You can enable starting and stopping Oracle Database through `OracleService``SID` by setting registry parameters.

### Setting Registry Parameters

To start or stop Oracle Database through Oracle Database services, set the following registry parameters to the indicated values:

- `ORA_``SID``_AUTOSTART`

  When set to `true`, the default value, this parameter causes Oracle Database to start when `OracleService``SID` is started.

- `ORA_``SID``_PFILE`

  This parameter sets the full path to the initialization parameter file. If this entry is not present, then ORADIM tries to start the database with an `SPFILE` or `PFILE` from `ORACLE_HOME``\database`.

- `ORA_SHUTDOWN`

  When set to `true`, this parameter enables the selected instance of Oracle Database to be shut down when `OracleService``SID` is stopped. This includes any database in the current Oracle home. The default value is `false`.

- `ORA_``SID``_SHUTDOWN`

  When set to `true`, the default value, this parameter causes the instance of Oracle Database identified by the `SID` value to shut down when `OracleService``SID` is stopped manually—using either the Control Panel or Net stop command.

  **Note:**

  If `ORA_SHUTDOWN` or `ORA_SID_SHUTDOWN` is set to `false`, then manually shutting down `OracleService``SID` still shuts down Oracle Database. But it is an abnormal shutdown, and Oracle does not recommend it.

The following two registry parameters are optional:

- `ORA_``SID``_SHUTDOWNTYPE`

  This parameter controls database shutdown mode. Set it to `a` (`abort`), `i` (`immediate`), or `n` (`normal`). The default mode is `i` (`immediate`) if you do not set this parameter.

- `ORA_``SID``_SHUTDOWN_TIMEOUT`

  This parameter sets the maximum time to wait before the service for a particular `SID` stops.

The registry location of these required and optional parameters are determined by the number of Oracle home directories on your computer. If you have only one Oracle home directory, then these parameters belong in:

    HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\HOME0

If you have multiple Oracle home directories, then these parameters belong in:

    HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\HOMEID

The variable `ID` is incremented for each additional Oracle home directory on your computer.

**Note:**

If you use ORADIM to create or edit instances, then it automatically sets the relevant registry parameters to their appropriate values.

### Starting or Stopping OracleServiceSID from the Control Panel

1.  To start the database, start OracleService`SID`.
    This automatically starts ORADIM and enters the -`STARTUP` command using the initialization parameter file identified by `ORA_``SID``_PFILE`.
2.  To stop the database, stop OracleService`SID`.
    This automatically stops ORADIM, which enters the `-SHUTDOWN` command in the mode indicated by `ORA_``SID``_SHUTDOWNTYPE`, and shuts down Oracle Database.

    **See Also:**

    Your operating system documentation for instructions on starting and stopping services.

**Related Topics**

- [Configuration Parameters and the Registry](configuration-parameters-and-registry.md)

**Parent topic:** [Administering a Database on Windows](administering-database-on-windows.md)
