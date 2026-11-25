## Running Oracle DBCA Using Response Files

You can run Oracle DBCA in response file mode to configure and start an Oracle database on the system.

To run Oracle DBCA in response file mode, you must copy and edit a response file template.

1.  Oracle provides a response file template named `dbca.rsp` in the response directory with the installation. Copy the `dbca.rsp` response file template from the response file directory to a directory on your system.
    If you have copied the software to a hard drive, then the response files are located in the `\response` directory.
    **Note:**

    As an alternative to editing the response file template, you can also create a database by specifying all required information as command-line options when you run Oracle DBCA. For information about the list of options supported, enter the following command:
        C:\> %ORACLE_HOME%\bin\dbca -help
2.  Log in as the Oracle Home user. Set the `%ORACLE_HOME%` environment variable to the correct Oracle home directory.
3.  Open the response file in a text editor.
4.  Edit the file, following the instructions in the file.
    In response file mode, Oracle DBCA uses values that you specify in the response file or as command-line options, to create a database.
    **Note:**

    Oracle DBCA fails if you do not correctly configure the response file.
5.  Open a command-line window. Change directories to the location of the Oracle home directory.
6.  Use a command similar to the following example to run Oracle DBCA in silent or response file mode using a response file:
        C:\> %ORACLE_HOME%\bin\dbca [-silent] -createDatabase -responseFile \local_dir\dbca.rsp

    In this example:

    - The `-silent` option runs Oracle DBCA in silent mode, suppressing user prompts.

    - `-createDatabase` creates the database.

    - local_dir is the full path of the directory where the `dbca.rsp` response file is located.

As Oracle DBCA configures and starts the database, it displays a window that contains status messages and a progress bar. The window that Oracle DBCA displays is the same window that is displayed when you choose to create a preconfigured database during an Oracle Database Enterprise Edition, Standard Edition, or Standard Edition 2 (SE2) installation.

**See Also:**

- "[Multiple Oracle Home Directories on Windows](multiple-oracle-home-directories-on-windows.md)" for more information about changing the current setting for Oracle Home.

- [Oracle Database Administrator's Guide](../admin/creating-and-configuring-an-oracle-database.md) for information about using Oracle DBCA in noninteractive, or silent mode, to create a database

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/manage-asm-asmca.md) for information about running Oracle Automatic Storage Management Configuration Assistant (ASMCA) in noninteractive mode

**Parent topic:** [Running Configuration Assistants Using Response Files](running-configuration-assistants-using-response-files.md)
