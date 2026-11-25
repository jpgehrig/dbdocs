ORADIM is a command-line tool that is available with Oracle Database.

Use ORADIM only if you are manually creating, deleting, or modifying databases. Oracle Database Configuration Assistant is an easier tool to use for this purpose.

ORADIM creates Oracle Database service, Oracle VSS Writer service, and Oracle Scheduler service to run under the Oracle Home User account. If this account is a Windows Local User Account or a Windows Domain User Account, then ORADIM prompts for a password for that account and accepts the same through `stdin`.

Specify both the Oracle Home User and its password using the `-RUNAS osusr[/ospass]` option to `oradim`. If the given `osusr` is different from the Oracle Home User, then use the Oracle Home User instead of `osusr` along with the given `ospass`.

The following sections describe ORADIM commands and parameters. Note that each command is preceded by a dash (`-`). To get a list of the ORADIM parameters, enter:

    oradim -? | -h | -help

**Note:**

Specifying `oradim` without any options also returns a list of ORADIM parameters and descriptions.

When you use ORADIM, a log file called `oradim.log` opens in `ORACLE_HOME``\database`, or in the directory specified by registry parameter `ORA_CWD`. All operations, whether successful or failed, are logged in this file. You mustcheck this file to verify success of an operation.

If you have installed an Oracle Database service on Windows, then when logging in as the SYSTEM user (LocalSystem), with the startup mode set to Automatic, it is possible that the Oracle Database service starts but the database does not start automatically. The following error message is written to the file `ORADIM.LOG` in the directory `ORACLE_HOME``\database`:

    ORA-12640: Authentication adapter initialization failed

Oracle Enterprise Management Agent, Oracle Enterprise Manager Management Server, and Oracle Internet Directory fails, because they cannot connect to the database for the same reason.

To work around this issue, perform the following tasks:

1.  Modify `SQLNET.ORA`

    You can modify `SQLNET.ORA`, by doing either of the following:

    - Remove the line `sqlnet.authentication_services=(NTS)`

    - Change the line `sqlnet.authentication_services=(NONE)`

2.  Start the database after the service starts.

    You can start the database manually after the Oracle Database service has started, using SQL\*Plus and connecting as `SYSDBA`.

3.  Start the service as a specific user.

    **See Also:**

    Your operating system documentation for instructions on starting the services

- [Creating an Instance Using ORADIM](creating-an-instance-using-oradim.md)
  Learn how to create an Oracle Database instance using ORADIM.
- [Starting an Instance and Services Using ORADIM](starting-an-instance-and-services-using-oradim.md)
  Learn how to start an instance and services using ORADIM.
- [Stopping an Instance and Services Using ORADIM](stopping-an-instance-and-services-using-oradim.md)
  Learn how to stop an instance and services using ORADIM.
- [Editing an Instance Using ORADIM](editing-an-instance-using-oradim.md)
  Learn how to edit an instance to change such values as instance name, startup mode, shutdown mode, and shutdown type using ORADIM.
- [Deleting an Instance Using ORADIM](deleting-an-instance-using-oradim.md)
  Learn how to delete an instance using ORADIM.
- [Manipulating ACLs Using ORADIM](manipulating-an-instance-using-oradim.md)
  Learn how to manipulate ACLs using ORADIM.
- [Manipulating Family Settings to Initialization Parameters using ORADIM](manipulating-family-settings-using-oradim.md)
  Learn how to manipulate family settings to initializing parameters.

**Parent topic:** [Postinstallation Database Creation on Windows](postinstallation-database-creation-on-windows.md)
