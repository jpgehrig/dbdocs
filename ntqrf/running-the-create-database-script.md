Use this procedure to run the CREATE DATABASE script.

To use the SQL script to create a database:

1.  Verify that the service is started in the Control Panel. In this example, the service name is `OracleServicePROD`, and its status column must display `Started`. If not, then select the service name and select Start.
    You can also check the status of the service by entering the following at the command prompt:

        C:\> net START

    A list of all the Windows services currently running on the system appears. If `OracleServicePROD` is missing from the list, then enter:

        C:\> net START OracleServicePROD
2.  Make `PROD` the current `SID`:
        C:\> set ORACLE_SID=PROD
3.  Add `ORACLE_HOME``\bin` to your `PATH` environment variable:
        set PATH=ORACLE_BASE\ORACLE_HOME\bin;%PATH%
4.  Start SQL\*Plus from the command prompt, and connect to the database as SYSDBA:
        C:\> sqlplus /NOLOG
        SQL> CONNECT / AS SYSDBA

    The message `connected` appears.
5.  Turn on spooling to save messages:
        SQL> SPOOL script_name.log
6.  Run the script `script_name``.sql` that you created in Adding the CREATE DATABASE Statement in a Script.
        SQL> C:\app\username\product\12.2.0\dbhome_1\rdbms\admin\script_name.sql;

    If the database is successfully created, then the instance is started and the following message appears numerous times: `Statement` `processed`

**Related Topics**

- [Adding the CREATE DATABASE Statement in a Script](putting-the-create-database-statement-in-a-script.md)

**Parent topic:** [Overview of Database Creation Tasks on Windows Using Command-Line Tools](overview-of-database-creation-tasks-on-windows-using-command-line-tools.md)
