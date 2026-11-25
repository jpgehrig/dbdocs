UNIX uses the concept of a DBA group. The `root` account cannot be used to install Oracle Database.

A separate Oracle Database account must be created manually.

On Windows, Oracle Database must be installed by a Windows username in the Administrators group. The user name is automatically added to the Windows local group `ORA_DBA`, which receives the SYSDBA privilege. This allows the user to log in to the database using `CONNECT` `/` `AS SYSDBA` and not be prompted for a password.

You can also create an `ORA_OPER` group to grant `SYSOPER` privileges to the other Windows users.

Password files are located in the `ORACLE_HOME``\database` directory and are named `pwd``SID``.ora`, where `SID` identifies the Oracle Database instance.

**Related Topics**

- [Administering a Database on Windows](administering-database-on-windows.md)

**See Also:**

[Oracle Database Installation Guide for Microsoft Windows](../ntdbi/creating-required-operating-system-groups-and-users.md) about "Operating System Groups Created During Oracle Database Installation"

**Parent topic:** [Oracle Database Differences on Windows and UNIX](oracle-database-differences-on-windows-and-unix.md)
