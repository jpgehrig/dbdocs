If this is the first database on your computer or if you intend to make the new database the default database, then you must make a change in the registry.

Perform the following steps:

1.  Start Registry Editor at the command prompt:
        C:\> regedit

    The Registry Editor window appears.
2.  Select the subkey `\HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\HOME0` for the first Oracle home on your computer. For subsequent installations to different Oracle homes on the same computer, the path is `\HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\HOME``ID` where ID is the unique number identifying the Oracle home.
3.  Locate the parameter `ORACLE_SID` on the right side of the Registry Editor window.
4.  Double-click the parameter name and change the data to the new `SID`, which is `prod` in this example.

**Related Topics**

- [Configuration Parameters and the Registry](configuration-parameters-and-registry.md)

**Parent topic:** [Overview of Database Creation Tasks on Windows Using Command-Line Tools](overview-of-database-creation-tasks-on-windows-using-command-line-tools.md)
