This chapter describes how to administer Oracle Database 19c for BS2000.

Common administration tasks are described in the following sections:

- Using the SQL\*Plus Utility

- Startup and Parameter Files

- Preparing a Remote Startup of a Database Instance Using SQL\*Plus

- Automatic Diagnostic Repository

### 6.1 Using the SQL\*Plus Utility

SQL\*Plus is the primary command-line interface to administer your Oracle database. You can use SQL\*Plus to start up and shut down the database, set database initialization parameters, create and manage users, create and alter database objects, and so on.

**See Also:**

[“SQL\*Plus”](oracle-database-utilities.md) for more information about how to use SQL\*Plus on Fujitsu BS2000

### 6.2 Startup and Parameter Files

Oracle uses the following parameter files when starting the database:

1.  The environment definition file `ORAENV`, which contains BS2000-specific information. In the `ORAENV` file, identify the database that has to be started or shut down. You can use this file to set the required environment variables.

2.  The initialization file `INIT.ORA` or the server parameter file `SPFILE`, which exists in all Oracle Database implementations and contains database-specific parameters.

This section describes the following:

- The Environment Definition File ORAENV

- The Initialization File INIT.ORA

- The Server Parameter File SPFILE

- About Using the Initialization File

#### 6.2.1 The Environment Definition File ORAENV

The `ORAENV` file is identified by `sid``.P.ORAENV`, where `sid` is the system identifier. The same `ORAENV` file must be used by SQL\*Plus in BS2000 and by all background jobs.

If you use SQL\*Plus in the POSIX shell, then you must specify the requested BS2000 parameters that are set in the `ORAENV` file. You can set the variables in the POSIX environment or use the facility to access the BS2000 `ORAENV` file as described in [“Setting Variable in the POSIX Program Environment.”](concepts-and-architecture.md)

Ensure that the value for `sid` in the POSIX file name `oraenv``sid` matches the value of the environment variable `ORACLE_SID`. For example, if you created a POSIX file `oraenv``sid` with `sid` in uppercase, then you must set the environment variable `ORACLE_SID` to exactly the same value.

    $ echo '$ORADATA.ORCL.P.ORAENV' > $ORACLE_HOME/dbs/oraenvORCL
    $ ORACLE_SID=ORCL
    $ export ORACLE_SID
    $ sqlplus /nolog
    $ SQL> connect / as sysdba

**See Also:**

- [“Oracle Environment Variables”](oracle-environment-variables.md) for information about required and optional `ORAENV` variables

- [“Starting Oracle Utilities in the POSIX Program Environment”](oracle-database-utilities.md) for more information about how to set POSIX environment variables

#### 6.2.2 The Initialization File INIT.ORA

To start up a database, you require the `INIT.ORA` parameter file. This file contains a list of specifications for the Oracle database. The platform independent parameters set up the instance and the database.

**Related Topics**

- [Oracle Database Administrator’s Guide](../admin/creating-and-configuring-an-oracle-database.md)
- [Oracle Database Reference](../refrn/initialization-parameters-2.md)

#### 6.2.3 The Server Parameter File SPFILE

You can choose to maintain initialization parameters in a binary server parameter file. A server parameter file is initially built from a traditional text initialization parameter file using the `CREATE SPFILE` command. If you enter the following command:

    CREATE SPFILE FROM PFILE;

where neither `SPFILE` name nor `PFILE` name is specified, then Oracle looks for a text initialization file `sid``.DBS.INIT.ORA` and creates a server parameter file `sid``.DBS.SPFILE.ORA`.

#### 6.2.4 About Using the Initialization File

A default initialization file, called `$ORACINST.DEMO.DBS.INIT.ORA`, is distributed with Oracle Database. During database creation, this file is copied to the DBA user ID and renamed to `sid``.DBS.INIT.ORA`, where `sid` is the 1 to 4 character system ID you specified at the beginning of the database creation procedure.

Oracle determines the value of `sid` by retrieving the `ORASID` environment variable defined in the `ORAENV` file for the database. When you issue the `STARTUP` command without specifying the `PFILE`, Oracle locates the initialization parameter file by examining file names in the following order:

1.  `sid``.DBS.SPFILE.ORA`

2.  `DBS.SPFILE.ORA`

3.  `sid``.DBS.INIT.ORA`

If you want to use a different initialization file, then use the argument `PFILE`. For example, to bring up a previously created database using an initialization file called `TEST.INIT.ORA`, enter the following:

    /START-EXECUTABLE (*LINK(ORALOAD),SQLPLUS)
    * /NOLOG

At the SQL\*Plus prompt, enter:

    SQL> CONNECT / AS SYSDBA
    SQL> STARTUP PFILE=TEST.INIT.ORA

### 6.3 Preparing a Remote Startup of a Database Instance Using SQL\*Plus

This section describes the preparations that are required to start up a database instance remotely using SQL\*Plus:

1.  Usually, the listener parameter file, `LISTENER.ORA` does not contain a static service registration section (`SID_LIST`) for a database service. In case of a remote startup, you must define this section for the desired database. For example:
        SID_LIST_LISTENER = (SID_LIST =
                             (SID_DESC =
                              (SID_NAME = ORCL)))

    The listener must be running on the computer where you want to start the instance. The listener must statically register the instance. If the listener does not run under the same user ID as the instance that you want to start, then you must do one of the following:

    - Use the Oracle environment variables `sid``_USER`, `user``_ACCOUNT`, and `user``_PASSWORD` to specify the required `LOGON` authorization parameters in the `ORAENV` file of the listener.

    - Use SECOS, Fujitsu's Security Control System for BS2000.

    **See Also:**

    "[Configuring the Network](oracle-net-services.md)" for more information
2.  Create a password file with the Oracle utility, `ORAPWD` under the user ID of the instance that you want to administer. To run the `ORAPWD` utility on BS2000, use the following command:
        /START-EXECUTABLE (*LINK(ORALOAD),ORAPWD)
        *file=password_file password=my_password entries=10

    **See Also:**

    [Oracle Database Administrator’s Guide](../admin/getting-started-with-database-administration.md) for more information about how to use the `ORAPWD` utility
3.  The name of the password file is derived from the `SSSIDPWF` environment variable. Ensure that you add this environment variable to the `ORAENV` file of the instance that you want to start:
        SSSIDPWF = password_file
4.  The parameter `REMOTE_LOGIN_PASSWORDFILE` must be set to `EXCLUSIVE` in the initialization file of the instance:
        REMOTE_LOGIN_PASSWORDFILE = EXCLUSIVE
5.  Execute SQL\*Plus on the remote computer and connect as user `sys` to a server task of the instance that you want to start. The following example shows the commands for SQL\*Plus on a UNIX client. The net service name orcl_on_bs2000 is used to address the remote instance on the BS2000 computer:
        sqlplus /nolog
        SQL> connect sys@orcl_on_bs2000 as sysdba
        Enter password:
        password
        Connected
        SQL> startup
        ...

### 6.4 Automatic Diagnostic Repository

Automatic Diagnostic Repository (ADR) is a file-based hierarchical data store for depositing diagnostic information produced by diagnostic framework clients. The repository contains data describing incidents, traces, dumps, alert logs, health check records, SQL Trace information, and other information essential for problem diagnosis.

**See Also:**

[Oracle Database Administrator’s Guide](../admin/diagnosing-and-resolving-problems.md) for more information about Automatic Diagnostic Repository

This section describes the following:

- Automatic Diagnostic Repository Directories and Files

- ADR Command Interpreter Utility

#### 6.4.1 Automatic Diagnostic Repository Directories and Files

Automatic Diagnostic Repository (ADR) is a directory structure that is stored outside of the database. It is therefore available for problem diagnosis when the database is down.

The directories and files of the Automatic Diagnostic Repository are stored in the POSIX file system.

**See Also:**

[Oracle Database Administrator’s Guide](../admin/diagnosing-and-resolving-problems.md) for information about the directory structure

The ADR root directory is known as ADR base. Its location is set by the `DIAGNOSTIC_DEST` initialization parameter. For example:

    DIAGNOSTIC_DEST=/u01/app/oracbase/oradata/adr

If this parameter is omitted or left null, then the database sets the `DIAGNOSTIC_DEST` parameter upon startup as follows:

- If the environment variable `ORACLE_BASE` is set, then the `DIAGNOSTIC_DEST` parameter is set to the directory designated by `ORACLE_BASE`.

- If the environment variable `ORACLE_BASE` is not set, then the `DIAGNOSTIC_DEST` parameter is set to `ORACLE_HOME/log`.

Within ADR base, there can be multiple ADR homes, where each ADR home is the `root` directory for all diagnostic data, such as, traces, dumps, alert log, and so on, for a particular instance of a particular Oracle product or component.

Oracle Net Services also stores diagnostic data in the ADR. The location for diagnostic information for Oracle Net Services is set by the `ADR_BASE` and `ADR_BASE_``listener_name` parameters. These are set in the `sqlnet.ora` and `listener.ora` Oracle Net Services parameter files.

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/troubleshooting-oracle-net-services.md) for more information about diagnostic information for Oracle Net Services

You can read the text files of the Automatic Diagnostic Repository with text editors such as `vi` or `edtu`, or with POSIX shell commands such as `cat` or `more`.

You can investigate ADR with the ADRCI utility.

#### 6.4.2 ADR Command Interpreter Utility

ADR Command Interpreter (ADRCI) utility enables you to investigate problems, view health check reports, and package first-failure diagnostic data within a command-line environment. You can then upload the package to Oracle Support. ADRCI also enables you to view the following:

- Names of the trace files in the ADR.

- Alert log with XML tags stripped, with and without content filtering.

You must execute the ADRCI command-line utility in the POSIX shell. Before you start the ADRCI utility, you must set the `ORACLE_HOME` environment variable. The system variable `PATH` must be extended by the path name of the Oracle bin directory, `$ORACLE_HOME/bin`. You can set the environment variables by executing the `.profile.oracle` profile in the appropriate Oracle home directory. Additional environment variables, such as `ORACLE_SID`, are not required.

**See Also:**

- [Oracle Database Utilities](../sutil/oracle-adr-command-interpreter-adrci.md) for more information about ADRCI

- [“Starting Oracle Utilities in the POSIX Program Environment”](oracle-database-utilities.md) for more information about Oracle Database utilities

After setting these environment variables, start the ADRCI utility in the POSIX shell by entering `adrci` after the POSIX shell command prompt.

**Note:**

You cannot start the ADRCI utility in the BS2000 program environment. ADRCI utility must be started in the POSIX shell.

Display the current ADR base with the ADRCI `show base` command. The current ADR home can be displayed with the `show homes` command.

Set ADR base with the `set base` command. You can set ADR home with the `set home` command.

The `show alert` command shows the contents of the alert log in a text editor.

If you use a blockmode terminal, then the default editor for ADRCI on Fujitsu BS2000 is` edtu`. If you use an xterm terminal, after having logged in to POSIX through `rlogin` or `ssh`, then the default editor for ADRCI is `vi`.

You can either select the preferred text editor by setting the environment variable `EDITOR` before starting the ADRCI utility or specify your preferred text editor within ADRCI with the ADRCI `set editor` command.

**Note:**

The editor `vi` does not work on blockmode terminals and the editor `edtu `does not work on xterm terminals.

With ADRCI, you can invoke Incident Packaging Service (IPS) to create packages for incidents with the following commands:

    ips create package
    ips generate package

Upload the resulting zip file to Oracle Support.
