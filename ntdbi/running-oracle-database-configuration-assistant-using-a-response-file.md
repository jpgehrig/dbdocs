## Running Oracle Database Configuration Assistant Using a Response File

You can run Oracle Database Configuration Assistant (Oracle DBCA) in a silent or a response file mode to configure and start an Oracle database on your system.

To run Oracle Database Configuration Assistant in silent or response file mode, use the `dbca.rsp` response file in the `ORACLE_BASE\ORACLE_HOME``\assistants\netca` directory, and the `response` directory in the `database\response` directory on the DVD.

**Note:**

If you copied the software to a hard disk, the response files are located in the `stage_area``\database\response` directory.

To run Oracle DBCA in a response file mode, you must use the `-responseFile` flag with the `-silent` flag. To run Oracle DBCA in response file mode, you must use a graphical display and set the `DISPLAY` environment variable.

On Windows, you must open the command prompt with Administrator privileges.

**See Also:**

- [Oracle Database Administrator's Guide](../admin/creating-and-configuring-an-oracle-database.md)

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/manage-asm-asmca.md)

<!-- -->

- [Silent Mode of Database Configuration Assistant](silent-mode-of-database-configuration-assistant.md)
  Use the `-silent` flag in combination with the `-responseFile` flag to set the mode to silent.
- [Running Oracle Database Configuration Assistant in Response File Mode](running-database-configuration-assistant-in-response-file-mode.md)
  Use this procedure to run Oracle Database Configuration Assistant (Oracle DBCA) in response file mode.

**Parent topic:** [Installing and Configuring Oracle Database Using Response Files](advance.md)
