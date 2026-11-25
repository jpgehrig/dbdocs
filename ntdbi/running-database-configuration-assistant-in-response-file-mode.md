## Running Oracle Database Configuration Assistant in Response File Mode

Use this procedure to run Oracle Database Configuration Assistant (Oracle DBCA) in response file mode.

To create an Oracle DBCA response file:

1.  Copy the `dbca.rsp` response file template from the response file directory to a directory on your system.
    The `dbca.rsp` response file is located in the `database\response` directory on the Oracle Database installation media.
2.  Open the `dbca.rsp` response file in a text editor.
3.  Edit the `dbca.rsp` file, following the instructions in the file.
    Oracle DBCA fails if you do not correctly configure the `dbca.rsp` response file.

To run the Oracle DBCA using the response file you just created, run Oracle DBCA in a silent or a response file mode using the following syntax:

    C:\> %ORACLE_HOME%\bin\dbca [-silent] -createDatabase -responseFile local_dir/dbca.rsp

where:

- `-createDatabase` creates Oracle Database.

- `-silent` runs Oracle Database Configuration Assistant in the silent mode.

- `local_dir` is the full path of the directory where you copied the `dbca.rsp` response file template.

For example:

    C:\> %ORACLE_HOME%\bin\dbca -createDatabase -responseFile
    C:\oracle_response_files\mydbca.rsp

As an alternative to creating a database using a response file, you can run `dbca` at the command line by specifying all the required information as command line options. Database Configuration Assistant writes progress messages to `stdout`. For information about the list of options supported, enter the following command:

    C:\ORACLE_HOME\bin\dbca -help

**Parent topic:** [Running Oracle Database Configuration Assistant Using a Response File](running-oracle-database-configuration-assistant-using-a-response-file.md)
