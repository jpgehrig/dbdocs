Learn how to use Data Pump Import or Import.

You can use Data Pump Import (for Oracle Database 10g Release 1 (10.1) or later data) or Import (for earlier data) to import the full export created into the new database. Although you can start Data Pump Import or Import using either the parameter mode or the interactive mode, Oracle recommends the parameter mode because it provides more functionality. Interactive mode exists solely for backward compatibility.

The syntax for Data Pump Import parameter mode is:

    C:\> impdp SYSTEM DUMPFILE=myexp.dmp FULL=y LOG=myexp.log
    Password: password

The syntax for Data Pump Import interactive mode is:

    C:\> impdp SYSTEM
    Password: password

Enter only `impdp` `SYSTEM` to begin an interactive session and let Data Pump Import prompt you for information it needs.

**Note:**

- If you use the parameter mode, then Data Pump Import considers the file names and the directory names to be invalid if they contain one or more blank spaces. The workaround is to enclose the full path in the `DUMPFILE=` parameter in triple quotation marks. For example:

  `DUMPFILE="""C:\program files\export.dmp"""`

  If you use Data Pump Import in an interactive mode, then the file name or the directory name can contain a space without the quotation marks.

- If the original database from which the export file was generated contains a tablespace that is not in the new database, then Import tries to create that tablespace with associated data files.

  The easy solution is to ensure that both the databases contain the same tablespaces. Data files are not required to be identical. Only the tablespace names are important.

**Related Topics**

- [About Exporting an Existing Database](about-exporting-an-existing-database.md)

**See Also:**

[Oracle Database Utilities](../sutil/datapump-import-utility.md) for more information about using Data Pump Import or Import

**Parent topic:** [Overview of Database Creation Tasks on Windows Using Command-Line Tools](overview-of-database-creation-tasks-on-windows-using-command-line-tools.md)
