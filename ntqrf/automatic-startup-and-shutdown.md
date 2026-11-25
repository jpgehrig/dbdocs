On UNIX, several files and scripts in different directories are used to start an instance automatically.

Other scripts are run on computer shutdown, allowing applications such as Oracle Database to shut down cleanly.

For automatic startup on Windows, set registry parameter `ORA_``SID``_AUTOSTART` to `true` using an Oracle Database tool such as ORADIM. Enter the following with parameters at the command prompt:

    C:\> oradim options

To start the listener automatically, set services startup type to automatic.

For automatic shutdown on Windows, set registry parameters `ORA_SHUTDOWN` and `ORA_``SID``_SHUTDOWN` to stop the relevant `OracleService``SID` and shut down. Set registry parameter `ORA_``SID``_SHUTDOWNTYPE` to control shutdown mode (default is `i`, or `immediate`).

**See Also:**

- [Administering a Database on Windows](administering-database-on-windows.md)

- [Oracle Database 2 Day DBA](../admqs/managing-the-oracle-instance.md)

**Parent topic:** [Oracle Database Differences on Windows and UNIX](oracle-database-differences-on-windows-and-unix.md)
