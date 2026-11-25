Learn about how to start multiple database instances.

Perform the following steps to start service for multiple Oracle Database instance:

1.  Start the service for each instance using ORADIM or the Services dialog of the Control Panel.
2.  At the command prompt, set the `ORACLE_SID` configuration parameter to the `SID` for the first instance to run:
        C:\> SET ORACLE_SID=SID

    The variable `SID` is the name of the Oracle Database instance.
3.   Start SQL\*Plus:
        C:\> sqlplus /NOLOG
4.  Connect `AS` `SYSDBA`:
        SQL> CONNECT / AS SYSDBA
5.  Start up the first instance:
        SQL> STARTUP PFILE=ORACLE_BASE\admin\db_name\pfile\init.ora

    The variable `ORACLE_BASE` is `c:\app\``username` (unless you changed it during installation) and `db_name` is the name of the instance.
6.  Repeat Step 2 through Step 5 for the other instances to run.

**Parent topic:** [Administering a Database on Windows](administering-database-on-windows.md)
