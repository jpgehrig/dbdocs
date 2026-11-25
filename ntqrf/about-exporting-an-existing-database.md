You are required to export an existing database only if you intend to copy its contents to a new database.

If you are working with data from an earlier Oracle release, then you can use Export for this task. If you are using Oracle Database 10g Release 1 (10.1) or later data, then Oracle recommends that you use Data Pump Export because it supports new Oracle Database 10g Release 1 (10.1) or later features, such as floating points.

Although you can start Data Pump Export or Export in either the parameter mode or an interactive mode, Oracle recommends parameter mode. Interactive mode provides less functionality than the parameter mode and exists for backward compatibility only.

The syntax for Data Pump Export parameter mode is:

    C:\> expdp SYSTEM DUMPFILE=myexp.dmp FULL=y LOGFILE=myexp.log
    Password: password

The syntax for Data Pump Export interactive mode is:

    C:\> expdp SYSTEM
    Password: password

Enter only the command `expdp` `SYSTEM`to begin an interactive session and let Data Pump Export prompt you for information it needs.

**Note:**

If you use the parameter mode, then Data Pump Export considers the file names and the directory names to be invalid if they contain one or more blank spaces. The workaround is to enclose the full path in the `DUMPFILE=` parameter in triple quotation marks. For example:

`DUMPFILE="""C:\program files\export.dmp"""`

If Data Pump Export is used in an interactive mode, then the file name or the directory name can contain a space without quotation marks.

The syntax for Export parameter mode is:

    C:\> exp SYSTEM FILE=myexp.dmp FULL=y LOG=myexp.log
    Password: password

The syntax for the Export interactive mode is:

    C:\> exp SYSTEM
    Password: password

Enter only the command `exp` `SYSTEM`to begin an interactive session and let Export prompt you for information it needs.

**Note:**

If you use the parameter mode, then Export considers the file names and the directory names to be invalid if they contain one or more blank spaces. The workaround is to enclose the full path in the `FILE=` parameter in triple quotation marks. For example:

`FILE="""C:\program files\export.dmp"""`

If Export is used in an interactive mode, then the file name or the directory name can contain a space without quotation marks.

- [Exporting All Data from an Existing Database](exporting-all-data-from-an-existing-database.md)
  Describes how to export all data from an existing database to a new database.

**See Also:**

[Oracle Database Utilities](../sutil/oracle-data-pump-export-utility.md) for more information about using Data Pump Export or Export

**Parent topic:** [Overview of Database Creation Tasks on Windows Using Command-Line Tools](overview-of-database-creation-tasks-on-windows-using-command-line-tools.md)
