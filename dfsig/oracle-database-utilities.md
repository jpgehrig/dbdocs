The various Oracle Database utilities and how to use them with Fujitsu BS2000 are discussed in the following topics:

- Basics of Oracle Database Utilities

- SQL\*Plus

- The SQL\*Loader

- The Export Utility

- The Import Utility

- The Data Pump Export Utility

- The Data Pump Import Utility

- Recovery Manager on BS2000

- Checking the Integrity of the Physical Data Structure

- Workload Replay Client

- The Oracle Text Loader

**See Also:**

[Oracle Database Utilities](../sutil/oracle-data-pump-overview.md)

### 7.1 Basics of Oracle Database Utilities

The BS2000-specific information about Oracle Database utilities that you must use with Oracle Database 19c for Fujitsu BS2000 are discussed in the following sections:

- The Oracle Database Environment-Definition File

- Oracle Runtime Libraries

- Starting Oracle Utilities in the BS2000 Program Environment

- Starting Oracle Utilities in the POSIX Program Environment

- Connecting to an Oracle Database Instance

- Using BS2000 Files for Input and Output

#### 7.1.1 The Oracle Database Environment-Definition File

Every Oracle Database utility and product under BS2000 uses an Oracle Database environment definition file, named `ORAENV`.

The `ORAENV` file is divided into the following parts:

- An executable part for BS2000 commands

- A static part for the definition of the environment variables

When processing the environment-definition file, a file link with the name `ORAENV` is created to the file itself. Oracle programs use the link name `ORAENV` to open this file. When reading this file, all lines with BS2000 commands (‘`/`’ in column one) and comments (‘`*`’ in column one) will be ignored. Only the variable settings starting in column one will be accepted.

You must generate this file before you use the Oracle Database programs as it contains several Oracle Database environment variables. These Oracle Database environment variables describe the operating environment for the Oracle database and utilities.

If you do not generate the `ORAENV` file, then the default values are used for all environment variables. In some cases, there are no default values for environment variables, such as for `ORASID`. If you start an Oracle Database program or utility without generating the `ORAENV` file first, then you cannot connect to the Oracle Database.

This section includes the following topics:

- Generating the Environment-Definition File

- Calling the Environment Definition File

- Specifying the Environment Variables

##### 7.1.1.1 Generating the Environment-Definition File

To generate an `ORAENV` file, perform the following steps:

1.  Call the `INSTALL.P.USER` procedure by entering the following command:
        /CALL-PROCEDURE $ORACINST.INSTALL.P.USER

    You are prompted to enter the database system identifier, `SID`.
2.  Enter the `SID`. If you do not know the `SID`, then contact your database administrator.

##### 7.1.1.2 Calling the Environment Definition File

Use the BS2000 command `CALL-PROCEDURE` to process the `ORAENV` file. For example:

    /CALL-PROCEDURE DEMO.P.ORAENV

##### 7.1.1.3 Specifying the Environment Variables

To specify the environment variables, call the `ORAENV` file containing the environment variables for the database you want to use.

If required, you can change the Oracle Database 19c working environment by editing the user variables in the `ORAENV` file.

**Note:**

The values that you assign to user variables are specific to your task and the database with which you work. The database administrator can also set other variables that may affect the whole database instance. If you try to set values for the DBA-specific variables in the `ORAENV` file, then they are ignored.

**See Also:**

[Oracle Environment Variables](oracle-environment-variables.md) for a list of the variables that you can specify in the `ORAENV` file

#### 7.1.2 Oracle Runtime Libraries

The executables of Oracle Database 19c are stored in a library called `ORALOAD.LIB`. Before running an Oracle program you must assign this library to the link name `ORALOAD`. This link is created when the `ORAENV` procedure is called. If the link `ORALOAD` is not defined properly, then a BLS (BS2000 loader) error message is displayed.

The `ORAMESG` library, `$ORACINST.ORAMESG.LIB` is required for Oracle messages. This library is assigned the link name `ORAMESG` in the `ORAENV` procedure.

#### 7.1.3 Starting Oracle Utilities in the BS2000 Program Environment

Before you start Oracle Database programs, you must call the environment definition file.

**See Also:**

"Calling the Environment Definition File" for more information

Use the SDF command `START-EXECUTABLE-PROGRAM` or the shorter form `START-EXECUTABLE` to start a program or a utility. Specify the options and operands as the first data input line when the data prompt (\*) is displayed, as shown in the following example:

    /START-EXECUTABLE (*LINK(ORALOAD),program_name)
    CCM0001 enter options:
    * [option_switch] [arguments]

where:

`program_name` is the name of the program or the utility that you want to start

`option_switch` is one or more of the program-dependent optional switches. If this is used, then the switch is preceded by a dash (-).

`arguments` are one or more operands of the program (or utility), or the user name and password combination, or both.

As soon as the program is loaded, the `CCM0001` prompt is displayed and enables you to enter the command line options. As shown in the preceding examples, you can enter the `option_switch` or `arguments` for the program. Then the prompt of the program is displayed. If the program is SQL\*Plus, then the prompt is `SQL>`. You can now enter one of the commands of the program. See the generic documentation for the utility for a description of the valid commands.

For example, to start SQL\*Plus, enter the following command:

    /START-EXECUTABLE (*LINK(ORALOAD),SQLPLUS)
    * userid/password


To start a utility in UNIX-Style, the Oracle syntax file `$ORACINST.SYSSDF.ORACLE.USER` must be activated. This is done by the `MOD-SDF (MODIFY-SDF-OPTIONS)` command in the `ORAENV` file. Remove the comment marker `'&*'` and call the `sid``.P.ORAENV` file again. The following commands to start an Oracle utility are available:

    /START-ORACLE-CM-CONTROL        or     /CMCTL
    /START-ORACLE-CMMIGR            or     /CMMIGR
    /START-ORACLE-EXPORT            or     /OEXP
    /START-ORACLE-EXPDP             or     /EXPDP
    /START-ORACLE-IMPORT            or     /OIMP
    /START-ORACLE-IMPDP             or     /IMPDP
    /START-ORACLE-LISTENER-CONTROL  or     /LSNRCTL
    /START-ORACLE-ORAPWD            or     /ORAPWD
    /START-ORACLE-SQLLOADER         or     /SQLLDR
    /START-ORACLE-SQLPLUS           or     /SQLPLUS
    /START-ORACLE-TNSPING           or     /TNSPING
    /START-ORACLE-RECOVERY-MANAGER  or     /RMAN

Specify the parameters after the start command. Enclose the parameters within single quotation marks, if they contain a white space or an equal sign (=) . The following examples show how to start an utility in UNIX Style in the BS2000 program environment:

`/lsnrctl `

`/sqlplus /nolog`

`/oimp 'system/manager file=iea buffer=210000 ignore=y grants=y rows=y full=y commit=y'`

#### 7.1.4 Starting Oracle Utilities in the POSIX Program Environment

You can run utilities like SQL\*Plus both in the normal BS2000 environment and the POSIX environment.

During Oracle Database installation, the utilities are installed within the POSIX file system in the `oracle_home_path``/bin` directory.

Before you start Oracle utilities in the POSIX shell, you must set the `ORACLE_HOME` environment variable and extend the `PATH` environment variable by the path name of the Oracle directory, `oracle_home_path``/bin` as follows:

    $ ORACLE_HOME=/u01/app/oracbase/product/19.3.0/dbhome_1
    $ export ORACLE_HOME
    $ PATH=$ORACLE_HOME/bin:$PATH
    $ export PATH

Alternatively, you can execute the `oracle_home_path``/.profile.oracle` profile, which is created during Oracle Database installation under POSIX. This profile sets and expands the most important variables like `ORACLE_HOME` and `PATH`.

To execute the profile, enter the following command:

    $ . /u01/app/oracbase/product/19.3.0/dbhome_1/.profile.oracle

Set the variable `ORACLE_SID` before you start an Oracle utility for a specific Oracle Database instance. Check the related `ORAENV` file in the BS2000 file system for instance specific environment variables. Set these variables in the POSIX shell before you start the utility.

Utilities running in the POSIX shell provide the opportunity to read instance-specific variables from the `ORAENV` file in the BS2000 file system. To provide access to the BS2000 `ORAENV` file, you must create a file with the name, `oraenv``sid` in the `ORACLE_HOME/dbs` directory or `ORACLE_BASE_CONFIG/dbs` directory in a read-only Oracle home environment. This file contains the fully qualified BS2000 file name of the BS2000 `ORAENV` file. It acts as a link to the `ORAENV` file in the BS2000 file system.

For example, to access the `ORAENV` file, `$ORADATA.ORCL.P.ORAENV`, you must create an `oraenvORCL` file in the `ORACLE_HOME/dbs` directory, as follows:

    $ ORACLE_HOME=/u01/app/oracbase/product/19.3.0/dbhome_1
    $ export ORACLE_HOME
    $ echo '$ORADATA.ORCL.P.ORAENV' > $ORACLE_HOME/dbs/oraenvORCL
    $ chmod 664 $ORACLE_HOME/dbs/oraenvORCL

**Note:**

- Utilities running in the POSIX shell handle the variables of the BS2000 `ORAENV` file as subordinate variables. Environment variables in the POSIX shell take precedence over settings in the BS2000 `ORAENV` file.

- The `sid` in the file name `oraenv``sid` is case sensitive and must match the `sid` specified in `ORACLE_SID`.

- You must grant access to the user using the BS2000 `ORAENV` file, if the POSIX user that runs the Oracle utility in the POSIX shell is different from the BS2000 user ID where the `ORAENV` file is located.

If an Oracle utility uses the BEQ protocol to connect to a database, then Oracle Net Services gets the job parameters to start a dedicated server in the BS2000 environment from the `BGJPAR` variable. If you do not specify this variable, then Oracle Net Services uses default values.

**Note:**

The `BGJPAR` variable might not be set after the `oracle_home_path``/.profile.oracle` profile is run.

When using the BEQ protocol, Oracle recommends that you define the particular BS2000 job parameters for BS2000 jobs that are started by Oracle Net Services. The `BGJPAR` variable provides the option to define these parameters. You can define this variable either in the related BS2000 `ORAENV` file or by explicitly setting it in the POSIX environment to the appropriate value.

For example, to assign a bequeathed server task to a special `JOB-CLASS`, set the `BGJPAR` variable in the POSIX environment as follows:

    $ ORACLE_SID=orcl
    $ export ORACLE_SID
    $ BGJPAR='START=SOON,CPU-LIMIT=NO,JOB-CLASS=JCBORA,LOGGING=*NO'
    $ export BGJPAR

You can start the utilities in a similar way as on other UNIX systems. For example, to start SQL\*Plus, use the following commands:

    $ sqlplus /nolog
    $ SQL> connect / as sysdba

#### 7.1.5 Connecting to an Oracle Database Instance

You can connect to an Oracle Database instance using one of the following methods:

- Oracle Net Services with the Bequeath adapter.

- Oracle Net Services over TCP/IP or IPC.

Check with your database administrator if you can connect to the Oracle database using the listed methods, as the possibilities available are dependent on how the system has been configured. Usually, you specify the way you connect to an Oracle Database instance as part of the logon string appended to the userid/password, and separated from it by an at sign (@), as described in the following sections:

Default Connections

Accessing an Oracle Database Instance

##### 7.1.5.1 Default Connections

If you do not specify a connection string, then use the `DEFAULT_CONNECTION` or `TWO_TASK` environment variables to specify an Oracle Database Net Services connect descriptor.

**See Also:**

[“Oracle Environment Variables”](oracle-environment-variables.md) for more information about the `ORAENV` file, and the `DEFAULT_CONNECTION` and `TWO_TASK` environment variables.

##### 7.1.5.2 Accessing an Oracle Database Instance

Use Oracle Net Services to access a local or a remote database instance. Use the Oracle Net Services logon string to identify the following connection attributes for accessing a local or a remote database:

- Protocol to be used.

- Database that you want to access.

- Type of server (whether dedicated or shared) that you want to use.

The Oracle Net Services logon string has the following structure:

    /START-EXECUTABLE (*LINK(ORALOAD),SQLPLUS)
    * userid/password@net_service_name

where:

`net_service_name` specifies a service name stored in the `TNSNAMES.ORA` file that identifies the TNS connect descriptor for the desired database. If you are not sure of what you should enter, then contact your database administrator.

The following example shows a logon string to connect to a database defined in the `TNSNAMES.ORA` file as `SERVERX`:

    username-for-HR/password-for-HR@SERVERX

**See Also:**

[“Oracle Net Services”](oracle-net-services.md) for information about connecting to an Oracle Database using the Bequeath adapter

#### 7.1.6 Using BS2000 Files for Input and Output

In most cases, Oracle Database for BS2000 programs use the functions of the C-BS2000 run-time system to access their input and output files. Oracle Database programs can read and write `SAM`, `ISAM`, and `PAM` files.

This section includes the following topics:

- Text Files

- Binary Files

- Default File Name Extensions

- Using Link Names

- Fixed Link Names

##### 7.1.6.1 Text Files

`SAM` or `ISAM` files store textual data. Each record is considered as a single text line. For example, the SQL script files used by SQL\*Plus and spool output files.

SQL\*Loader input data is provided as `SAM` or `ISAM` files. These files may also contain non-printable data, such as packed decimal or binary integer values. For `ISAM` files, the key at the beginning of the record is generally ignored.

##### 7.1.6.2 Binary Files

Binary data is usually stored in PAM files.

##### 7.1.6.3 Default File Name Extensions

Under BS2000, the Oracle Database utilities add default extensions to file names only if the last component of the specified file name is longer than three characters, or if only one component is specified, as shown in the following table:

| Original File Name | Extended File Name |
|:-------------------|:-------------------|
| `TEST.TEST`        | `TEST.TEST.EXT`    |
| `TST`              | `TST.EXT`          |
| `T.T`              | `T.T`              |
| `TEST.TST`         | `TEST.TST`         |

This is similar to the file naming conventions used with Oracle Database on a UNIX system.

##### 7.1.6.4 Using Link Names

In special cases, instead of specifying a file name, you can also specify the link name of a previously issued `BS2000 /SET-FILE-LINK` command. Use the syntax `link=``linkname` in places where a file name is requested. In this way, you can override default file attributes, preallocate file space, and so on. There are a few exceptions where you cannot use the `link=``linkname` notation.

When using the `link=``linkname` notation, the default file name extensions do not work. As a result, file name defaults derived from such notation are not valid, and you must provide explicit names in such cases.

For example, when working with SQL\*Loader, if you specify `link=``linkname` for the SQL\*Loader control file, then you must provide explicit names for the `BAD`, `LOG`, and `DISCARD` file names.

Some programs may report a syntax error when the `link=``linkname` notation is used on the command (options) line. In such cases, omit the parameter on the command line and specify it instead, when you are prompted for the missing parameter.

##### 7.1.6.5 Fixed Link Names

Oracle Database for BS2000 uses fixed link names for specific files.

The most important link names are as follows:

| Type    | Meaning/Usage                                                                                                                  |
|:--------|:-------------------------------------------------------------------------------------------------------------------------------|
| ORAENV  | Oracle Database environment definition file.                                                                                   |
| ORALOAD | The link name is mandatory and specifies the load library from which the Oracle Database modules are loaded during processing. |
| ORAMESG | The link name is mandatory and specifies the message library from which Oracle message modules are loaded during execution.    |

Typically, you can set these link names by running the `ORAENV` procedure.

### 7.2  SQL\*Plus

SQL\*Plus is an interactive and a batch query tool that is installed with every Oracle Database installation. It has a command-line user interface. SQL\*Plus has its own commands and environment, and provides access to the Oracle Database. It enables you to enter and execute SQL, PL/SQL, SQL\*Plus, and operating system commands to perform the following:

- Format, perform calculations on, store, and print from query results

- Examine table and object definitions

- Develop and run batch scripts

- Perform database administration

This section describes how to use SQL\*Plus in the BS2000 environment and in the POSIX environment. It supplements the [SQL\*Plus User's Guide and Reference](../sqpug/SQL-Plus-quick-start.md). It contains the following topics:

- Using SQL\*Plus in the BS2000 Environment

- Using SQL\*Plus in the POSIX environment

- SQL\*Plus User Profiles

- Using SQL\*Plus Symbols

- Sample Schemas and SQL\*Plus

- SQL\*Plus Limits

#### 7.2.1 Using SQL\*Plus in the BS2000 Environment

This section describes how to use SQL\*Plus in the BS2000 environment. It contains the following topics:

- Starting SQL\*Plus in the BS2000 Environment

- Interrupting a SQL\*Plus Command in the BS2000 Environment

- Running BS2000 Commands from SQL\*Plus

- Starting the BS2000 Editor

- Spooling SQL\*Plus Output

- Specifying the Search Path for SQL Scripts in the BS2000 Environment

- Starting SQL\*Plus in a BS2000 command procedure

##### 7.2.1.1 Starting SQL\*Plus in the BS2000 Environment

1.  To start SQL\*Plus, enter:
    `/START-EXECUTABLE (*LINK(ORALOAD),SQLPLUS)`

    `*username/password`

    **Note:**

    If you omit user name and password, then you will be prompted to enter these values.

    If you enter the user name only, then you will be prompted for the password.

    SQL\*Plus displays the following command prompt:
    `SQL>`

    The SQL\*Plus command prompt indicates that SQL\*Plus is ready to accept your commands.
2.  To start SQL\*Plus without connecting to a database, enter the following command:
        /START-EXECUTABLE (*LINK(ORALOAD),SQLPLUS)
        */NOLOG
3.  After SQL\*Plus has started, you can connect to the database with the `CONNECT` command as follows:
    `SQL> CONNECT ``username/password`

##### 7.2.1.2 Interrupting a SQL\*Plus Command in the BS2000 Environment

Use the INTERRUPT key \[K2\] to interrupt the execution of a command in SQL\*Plus. For example, you can interrupt SQL\*Plus if you receive a long report that you do not want to be completely displayed on the screen. When you press the INTERRUPT key \[K2\], the display of the report is stopped and the SQL\*Plus command prompt is displayed.

**Note:**

If you issue an INTERRUPT key when an input is requested, then you must answer this request before interrupting the process. However, this answer will be ignored.

##### 7.2.1.3 Running BS2000 Commands from SQL\*Plus

The SQL\*Plus `HOST` command and the `$` command enables you to run a BS2000 command without exiting from SQL\*Plus.

Some examples of how you can use the `HOST` command:

- If you enter the `HOST` command without any BS2000 command, then it takes you to the BS2000 command level:

      SQL> HOST
      /SHOW-USER-STATUS

  To return to SQL\*Plus, use the BS2000 command `RESUME` .

- If you enter the `HOST` command with a BS2000 command, then the command executes and the control returns to the SQL\*Plus command level:

      SQL> HOST SHOW-USER-STATUS
      SQL>

The following BS2000 commands, if used with the `HOST` or `$` command, do not return to SQL\*Plus when they have finished running:

- `START-EXECUTABLE-PROGRAM`

- `LOAD-EXECUTABLE-PROGRAM`

- `START-PROGRAM`

- `LOAD-PROGRAM`

- `CALL-PROCEDURE`

- `HELP-SDF`

- `LOGOFF`

##### 7.2.1.4 Starting the BS2000 Editor

You can use the SQL\*Plus `EDIT` command to start the BS2000 editor:

    SQL> EDIT

This command:

- Writes the SQL buffer, which contains the current SQL statement, to a file called `SQLEDT.BUF` in the current BS2000 user ID.

- Starts the editor EDT, which reads the `SQLEDT.BUF` file into the work area.

You can then edit and write to the file using the `@write` command. Use the `@halt` command to exit the editor and return to SQL\*Plus. SQL\*Plus then reads the current contents of `SQLEDT.BUF` back into its command buffer, from which you can execute the SQL statement by entering a forward slash (/) at the SQL\*Plus command prompt.

**Note:**

If you use the SQL\*Plus `DEFINE _EDITOR` command to define a name for the editor, then SQL\*Plus ignores it when running in the BS2000 environment. It always starts the EDT editor.

You can also use the `EDIT` command to edit a SQL file by specifying the SQL file. For example, if you enter the following command, then the editor EDT is called to edit the `LOGIN.SQL` file:

`SQL> EDIT LOGIN[.SQL]`

Note that you can omit the default file name extension `.SQL`.

**See Also:**

[SQL\*Plus User's Guide and Reference](../sqpug/EDIT.md) for more details about the `EDIT` command

##### 7.2.1.5 Spooling SQL\*Plus Output

When you use the SQL\*Plus `SPOOL` command, SQL\*Plus uses the default output-file suffix, `.LST`.

**Note:**

The output generated by BS2000 operating system commands are not spooled.

When you issue a `SPOOL OUT` command, SQL\*Plus executes the BS2000 `/PRINT` command:

`/PRINT ``tempfile``,ERASE`

where `tempfile` is a temporary copy of the spool file. This routes the file to the central printer. To specify any `/PRINT` command options, such as character sets, or routing to a remote printer, add the following line to the `ORAENV` file:

`PRINTPAR=``options`

where `options` is any sequence of `/PRINT` command options. SQL\*Plus then executes a `/PRINT` command, which includes these options.

**See Also:**

BS2000 manual User Commands (ISP Format) for more information about these options

##### 7.2.1.6 Specifying the Search Path for SQL Scripts in the BS2000 Environment

You can run SQL script with SQL\*Plus by using the `START` command or the `@` (at symbol).

If SQL\*Plus is executed in the BS2000 environment, it searches the SQL script in the current BS2000 user ID. If the script is not found, then SQL\*Plus searches the paths specified by the `SQLPATH` environment variable. This variable is used to specify one or more file name prefixes separated by a semicolon (;), which should be applied when searching for the SQL script file.

For example, if `SQLPATH` is set as follows:

`SQLPATH=PRIVATE;$GLOBAL;``/guest/scripts/``;`

then, when you enter the following command:

`SQL> @``filename`` `

SQL\*Plus searches for the SQL script file in the following sequence, until a matching file name is found:

1.  `filename``.SQL` in the current BS2000 user ID in the BS2000 DMS.
2.  `PRIVATE.``filename``.SQL` with the prefix `PRIVATE` in the current user ID in the BS2000 DMS.
3.  `$GLOBAL.``filename``.SQL` in the BS2000 user ID `$GLOBAL` in the BS2000 DMS.
4.  `/guest/scripts/filename.sql` in the directory `/guest/scripts/` in the POSIX file system.

##### 7.2.1.7 Starting SQL\*Plus in a BS2000 command procedure

If you execute SQL\*Plus within a BS2000 SDF command procedure, add the following command to the procedure before the `/START-EXECUTE` command for SQL\*Plus:

`/ASSIGN-SYSDTA *SYSCMD`

This forces SQL\*Plus to read data from the procedure, instead of prompting at the terminal.

#### 7.2.2 Using SQL\*Plus in the POSIX environment

You can run SQL\*Plus not only in the normal BS2000 environment, but also in the POSIX environment.

This section describes the following:

- Starting SQL\*Plus in the POSIX Environment

- Interrupting a SQL\*Plus Command in the POSIX Environment

- Running Shell Commands From SQL\*Plus

- Using an Editor in SQL\*Plus

- Spooling SQL\*Plus Output in the POSIX Environment

- Specifying the Search Path for SQL Scripts in the POSIX Environment

##### 7.2.2.1 Starting SQL\*Plus in the POSIX Environment

Set the required environment variables and run SQL\*Plus as described in "Starting Oracle Utilities in the POSIX Program Environment." To connect to a database immediately, specify the user name and password as an argument as follows:

`$ sqlplus ``username``/``password[@net_service_name]`

If you do not want to connect to a database, then specify /nolog as an argument:

`$ sqlplus /nolog`

If you start SQL\*Plus without any arguments, then you will be prompted for the user name and password.

##### 7.2.2.2 Interrupting a SQL\*Plus Command in the POSIX Environment

Interrupting a SQL statement when you run SQL\*Plus in the POSIX environment depends on the terminal connected with your POSIX session.

To interrupt a SQL statement in the POSIX environment:

- Enter @@c and then press the Enter key if the POSIX shell is started on a blockmode terminal.

- Press the Ctrl + C key combination if the POSIX shell is started by a remote X-client through rlogin or ssh using an xterm terminal.

##### 7.2.2.3 Running Shell Commands From SQL\*Plus

The SQL\*Plus `HOST` command and the `$` command enables you to enter a POSIX shell command, without exiting SQL\*Plus.

When using the `HOST` command, remember the following points:

- If you enter the `HOST` command without any shell command, then a POSIX subshell is started and the POSIX command prompt is displayed. To return to SQL\*Plus, you must use the `exit` command or the `return` command in the POSIX subshell.

- If you enter the `HOST` command with a POSIX shell command, then the command is executed in a subshell and then control returns to SQL\*Plus.

- Use the `bs2cmd` POSIX shell command to execute BS2000 commands.

##### 7.2.2.4 Using an Editor in SQL\*Plus

Start a text editor in SQL\*Plus with the `EDIT` command, to edit an SQL statement.

The default editor depends on the terminal connected with your POSIX session:

- If the POSIX shell is started on a blockmode terminal, then `edtu` is set as the default editor in SQL\*Plus.

- If the POSIX shell is started by a remote X-client through `rlogin` or `ssh` using an xterm terminal, then `vi` is set as the default editor in SQL\*Plus.

SQL\*Plus provides the opportunity to define a preferred text editor with the `DEFINE _EDITOR` command. In the POSIX environment you can define a preferred editor. For example, to define the editor used by the `EDIT` command to be the POSIX editor `edtu`, enter the following command in SQL\*Plus:

    DEFINE _EDITOR = edtu

**Note:**

- The editor `vi` does not work on blockmode terminals.

- The editor `edtu` does not work on xterm terminals.

The command `EDIT`:

- Writes the SQL buffer, which contains the current SQL statement to a file called `SQLEDT.BUF` in the current working directory in the POSIX file system.

- Starts the editor, which reads the file `SQLEDT.BUF` into the work area.

You can then edit and write this file using `@write` with `edtu` editor and using `:w` with `vi` editor.

To exit the editor and return to SQL\*Plus, use the `@halt` command with `edtu` and `:q` with `vi`. SQL\*Plus then reads the current contents of `SQLEDT.BUF` back into its command buffer, from which the SQL statement can be run by entering slash “`/`” at the SQL\*Plus command prompt.

You can also use the `EDIT` command to edit a SQL file by specifying the name of the SQL file. For example, if you enter the following command, then the editor is called to edit the `login.sql` file:

`SQL> EDIT login[.sql]`

Note that you can omit the default file name extension, `.sql`.

##### 7.2.2.5 Spooling SQL\*Plus Output in the POSIX Environment

When using the SQL\*Plus `SPOOL` command, SQL\*Plus uses the default output-file suffix, `.lst `.

The command `SPOOL OUT` is not supported, when you use SQL\*Plus in the POSIX environment.

##### 7.2.2.6 Specifying the Search Path for SQL Scripts in the POSIX Environment

You can run a SQL script with SQL\*Plus by using the `START` command or the `@` (at symbol).

If SQL\*Plus is executed in the POSIX environment, it searches the SQL script in the current working directory. If the script is not found, then SQL\*Plus searches the paths specified by the `SQLPATH` environment variable. This variable specifies one or more file name prefixes separated by a semicolon (;), which should be applied when searching for the SQL script file.

For example, if `SQLPATH` is set as follows:

    SQLPATH=’private;/BS2/$GLOBAL;/guest/scripts/;’
    export SQLPATH

then, when you enter the following command:

`SQL> @``filename`` `

SQL\*Plus searches for the SQL script file in the following sequence, until a matching file name is found:

1.  `filename``.SQL` in the current working directory in the POSIX file system.
2.  `private/``filename``.SQL` in the subdirectory `private` of the current working directory in the POSIX file system.
3.  `/BS2/$GLOBAL.``filename``.SQL` in the BS2000 user ID `$GLOBAL` in the BS2000 DMS.
4.  `/guest/scripts/filename.sql` in the directory `/guest/scripts/` in the POSIX file system.

#### 7.2.3 SQL\*Plus User Profiles

You can set up your SQL\*Plus environment to use the same settings with each session. There are two operating system files to do this:

- The Site Profile file, `glogin.sql` for site wide settings.

- The User Profile file, `login.sql` for user specific settings.

When a user starts SQL\*Plus, the `glogin.sql` file is executed first followed by the user's `login.sql` file. These profiles are discussed in detail in the following topics:

- The glogin.sql Global Setup File

- The login.sql User Setup File

##### 7.2.3.1 The glogin.sql Global Setup File

The Site Profile file, `glogin.sql` is executed when you start SQL\*Plus. This file contains SQL statements and SQL\*Plus commands that must be run at the beginning of a SQL\*Plus session. The `glogin.sql` file is located in the POSIX file system, `$ORACLE_HOME/sqlplus/admin`. The database administrator may customize the `glogin.sql` file if required.

##### 7.2.3.2 The login.sql User Setup File

Every time you start SQL\*Plus, the user profile script `login.sql` is executed after the `glogin.sql` script. Similar to `glogin.sql`, this file also contains SQL statements and SQL\*Plus commands that a user wants to run at the beginning of every SQL\*Plus session.

When you start SQL\*Plus in the BS2000 environment, SQL\*Plus searches along the path that is specified by the `ORACLE_PATH` environment variable. If there are more than one `login.sql` file, then SQL\*Plus executes the first `login.sql` file that is found. If you specify a list of `login.sql` files, they must be separated by a semicolon (`;`). For a customized SQL\*Plus environment, each BS2000 user ID can have its own `login.sql` file.

When you start SQL\*Plus in the POSIX environment, SQL\*Plus searches along the path that is specified by the `ORACLE_PATH` environment variable . If there are more than one `login.sql` file, then SQL\*Plus executes the first `login.sql` file that is found. For a customized SQL\*Plus environment, each POSIX user can have its own `login.sql` file.

**See Also:**

- "[Oracle Environment Variables](oracle-environment-variables.md)" for a description of the SQLPATH environment variable

- [SQL\*Plus User's Guide and Reference](../sqpug/configuring-SQL-Plus.md) for more information about `login.sql`

The following is a sample profile file:

    set echo off
    set feedback 4
    set pause on
    set pause  PLEASE ACKNOWLEDGE TO CONTINUE
    set echo on

#### 7.2.4 Using SQL\*Plus Symbols

The SQL\*Plus symbol used for concatenation is the vertical bar, "\|" (X'4F'). For users with German keyboards and using a 7–bit terminal character set, any key that transmits a X'4F' (for example, "ö"), can be used.

#### 7.2.5 Sample Schemas and SQL\*Plus

The sample schemas provide a common platform for examples.

**See Also:**

- [SQL\*Plus User's Guide and Reference](../sqpug/SQL-Plus-quick-start.md) for more information about the sample schemas and SQL\*Plus

- "[Creating a Database](about-creating-a-database.md)" for information about how to install the sample schemas

#### 7.2.6 SQL\*Plus Limits

The limits of several SQL\*Plus elements are specified in [SQL\*Plus User's Guide and Reference](../sqpug/SQL-Plus-limits.md). The following table defines BS2000 specific limits:

| Item                                   | Limit                                                                                     |
|:---------------------------------------|:------------------------------------------------------------------------------------------|
| File name length                       | 54 in the BS2000 DMS (including CATID and BS2000 user ID)<br>512 in the POSIX file system |
| LINESIZE                               | 32767                                                                                     |
| MAXDATA                                | 32767                                                                                     |
| Maximum number of nested command files | 12                                                                                        |

### 7.3 The SQL\*Loader

SQL\*Loader is a tool used for moving data from an external file (or files) into the tables of an Oracle database. SQL\*Loader can load data in several formats and can even load several tables simultaneously. You can also use it to load only records that match a particular data value.

This section includes the following topics:

- Starting the SQL\*Loader Utility

- Using the SQL\*Loader Demonstration Files

**See Also:**

[Oracle Database Utilities](../sutil/oracle-sql-loader-concepts.md) for a detailed description of SQL\*Loader and its demonstration files

#### 7.3.1 Starting the SQL\*Loader Utility

You can start SQL\*Loader either in the BS2000 environment or the POSIX environment.

**Related Topics**

- Starting Oracle Utilities in the BS2000 Program Environment
- Starting Oracle Utilities in the POSIX Program Environment

#### 7.3.2 Using the SQL\*Loader Demonstration Files

The demonstration files are shipped under:

    $ORACINST.RDBMS.DEMO.ULCASE*.CTL
    $ORACINST.RDBMS.DEMO.ULCASE*.SQL
    $ORACINST.RDBMS.DEMO.ULCASE*.DAT

To run the ULCASE1 demo, perform the following steps:

1.  Run SQL\*Plus and set up the table to be used in the demonstration by entering the following commands:
        /START-EXECUTABLE (*LINK(ORALOAD),SQLPLUS)
        * SCOTT/password
        SQL> START $ORACINST.RDBMS.DEMO.ULCASE1

    **Note:**

    This example sets up the table for the user `SCOTT` to run the demonstrations.
2.  Start SQL\*Loader to run the demonstration by entering the following command:
        /START-EXECUTABLE (*LINK(ORALOAD),SQLLDR)
        * SCOTT/password $ORACINST.RDBMS.DEMO.ULCASE1 ULCASE1 ULCASE1

### 7.4 The Export Utility

The Export utility is used to write data from an Oracle database into the BS2000 files. Use this utility with the Import utility to back up your data and to move data between Oracle databases.

This section includes the following topics:

- Starting the Export Utility

- Exporting to Foreign Systems

#### 7.4.1 Starting the Export Utility

You can start the Export utility, `exp` either in the BS2000 environment or the POSIX environment.

**See Also:**

- Starting Oracle Utilities in the BS2000 Program Environment

- Starting Oracle Utilities in the POSIX Program Environment

Export dump files, which are created in the BS2000 DMS by `EXP` usually have the file structure, `SAM`. You can override default output file specifications by running a `SET-FILE-LINK` command such as:

`/SET-FILE-LINK LINK-NAME=``explink``,FILE-NAME=``expfile``,ACCESS-METHOD=*SAM,RECORD-FORMAT=*FIXED,RECORD-SIZE=2048,BUFFER-LENGTH=*STD(1)`

Then, call the `EXP` utility by specifying the following in response to the output file name prompt:

    LINK=explink

On a nonkey public volume set, you may need to adjust the `BLKSIZE` and `RECSIZE` values for efficient disk-space usage (note that `RECSIZE` must be 16 bytes less than the `BLKSIZE` on nonkey disks). Specify the `RECSIZE` value to match the export record size.

For example:

`/SET-FILE-LINK LINK-NAME=``explink``,FILE-NAME=``expfile``,ACCESS-METHOD=*SAM,RECORD-FORMAT=*FIXED,RECORD-SIZE=2032,BUFFER-LENGTH=2048`

**Note:**

Do not use variable record size with `SAM` files.

When using a block size (`PAM`) or record size (`SAM`) other than 2048, you must also specify a corresponding `RECORDLENGTH` parameter to `EXP` on the options line.

When exporting large volumes of data, the default disk-space allocation for the output file is inappropriate, and the program spends a significant amount of time allocating secondary extents of disk space. If the maximum number of extents exceeds the number that the BS2000 catalog entry can hold, then an output-file error occurs.

You can preallocate the `EXP` output file with the BS2000 `CREATE-FILE` command, before starting the Export utility. When allocating the file, you must use a realistic estimate for both the primary and secondary space allocations.

For example:

    /CREATE-FILE LARGE.EXPORT.DMP,SPACE=(30000,30000)
    /ADD-FILE-LINK LINK-NAME=EXPOUT,FILE-NAME=LARGE.EXPORT.DMP
    /START-EXECUTABLE (*LINK(ORALOAD),EXP)
    * system/manager
    ...
    Export file: EXPDAT.DMP >link=expout
    ...

#### 7.4.2 Exporting to Foreign Systems

You can export to foreign systems using the following methods:

- Exporting Data to Tape

- Transferring Data by File Transfer

##### 7.4.2.1 Exporting Data to Tape

To export directly to tape:

1.  Create a catalog entry for a file using the `CREATE-FILE` command.

2.  Create a link using the `ADD-FILE-LINK` command. For example:

        /CREATE-FILE tapefile,SUPPORT=*TAPE(VOLUME=vsn,DEVICE-TYPE=device)
        /ADD-FILE-LINK LINK-NAME=tapelink,FILE-NAME=tapefile,ACCESS-METHOD=*SAM,RECORD-FORMAT=*FIXED,RECORD-SIZE=2048,BUFFER-LENGTH=*STD(1)

3.  Set the environment variable `EXP_CLIB_FILE_IO` to `FALSE`.

4.  Execute `EXP` by specifying the following value in response to the output file name prompt:
        LINK=tapelink

The export utility writes the output as `SAM` files, which simplifies export to an Oracle database on foreign systems.

##### 7.4.2.2 Transferring Data by File Transfer

If you use FTP, then ensure that you specify binary mode. This is to avoid automatic EBCDIC-ASCII conversion.

You must use FTP on BS2000 when you want to use an export file from BS2000 as an import file on an ASCII platform. To avoid new line (NL) insertion at block boundaries, ensure that you provide the `binary` and the `ftyp binary` parameters.

### 7.5 The Import Utility

The Import utility is used to write data from the files created by the Export utility to an Oracle database.

This section includes the following topics:

- Starting the Import Utility

- Importing from Foreign Systems

**See Also:**

[“Known Problems, Restrictions and Workarounds”](../dfsrn/index.md) in Oracle Database Release Notes for Fujitsu BS2000 for restrictions when using the Import utility

#### 7.5.1 Starting the Import Utility

You can start the Import utility, `imp` either in the BS2000 environment or the POSIX environment.

**See Also:**

- Starting Oracle Utilities in the BS2000 Program Environment

- Starting Oracle Utilities in the POSIX Program Environment

#### 7.5.2 Importing from Foreign Systems

Follow the guidelines listed in this section when you import data from non-BS2000 systems:

- Importing File with Non-Standard Block Size

- Importing Data from Tape

- Transferring Data by File Transfer

##### 7.5.2.1 Importing File with Non-Standard Block Size

If the import file on the BS2000 operating system has a block size (`BLKSIZE`) not equal to 2 KB, then you must specify the block size during import with the Import parameter `RECORDLENGTH`.

##### 7.5.2.2 Importing Data from Tape

The Import utility can read directly from tape, provided the file can be processed as a `SAM` file, which is usually the case even for `EXP` files created on foreign systems (for example, as a sequence of fixed 2 KB blocks).

To read a foreign export file directly:

1.  Create a catalog entry for a file using the `IMPORT-FILE` command.

2.  Create a link using the `ADD-FILE-LINK` command. For example:

        /IMPORT-FILE SUPPORT=*TAPE(VOLUME=vsn,DEVICE-TYPE=device,FILE-NAME=tapefile)
        /ADD-FILE-LINK LINK-NAME=tapelink,FILE-NAME=tapefile

3.  Set the environment variable `IMP_CLIB_FILE_IO` to `FALSE`.

4.  Execute `IMP` by specifying the following value in response to the input file name prompt:
        LINK=tapelink

##### 7.5.2.3 Transferring Data by File Transfer

If you use FTP, then ensure that you specify binary mode. This is to avoid automatic ASCII-EBCDIC conversion. The received file is stored as a `PAM` file by the BS2000 FTP utility and can immediately be used as an input file to `IMP`.

### 7.6 The Data Pump Export Utility

The Data Pump Export and Import are functionally similar to Export and Import discussed in the preceding sections. However, the I/O processing for dump files is done in the Oracle database server rather than in the client utility session.

This utility is used to write data from an Oracle database into the BS2000 files. Use this utility with the Data Pump Import utility to back up your data and to move data between Oracle databases.

#### 7.6.1  Starting the Data Pump Export Utility

You can start the Data Pump Export utility, `expdp` either in the BS2000 environment or the POSIX environment.

**See Also:**

- “Starting Oracle Utilities in the BS2000 Program Environment”

- “Starting Oracle Utilities in the POSIX Program Environment”

The Data Pump Export dump files are always created in the BS2000 DMS as `PAM` files with `BLKSIZE=(STD,2)`.

To use an export file from BS2000 as an import file on an ASCII platform, use FTP as the transfer utility on BS2000 side and indicate the `binary` parameter .

**Note:**

If you start `EXPDP` in UNIX-style and use the interactive-command mode \[K2\] key, then the parameters must be specified when you are prompted for them, and not on the command line.

Data Pump Export to tape is not supported.

### 7.7 The Data Pump Import Utility

The Data Pump Import utility is used to write data from the files created by the Data Pump Export utility to an Oracle database.

#### 7.7.1 Starting the Data Pump Import Utility

You can start the Data Pump Import utility `impdp` either in the BS2000 environment or the POSIX environment.

The following example shows how to use the command-line mode of `impdp` in the BS2000 environment:

    START-EXECUTABLE (*LINK(ORALOAD),IMPDP)
    * username/password [options]

If you use an export file from an ASCII platform as an import file on BS2000, then use FTP as the transfer utility on BS2000 side and indicate the `binary` parameter.

Before you get the file, issue the FTP command:

    file dmp-file,fcbtype=pam,blksize=(std,2),blkctrl=no

**Note:**

If you start `IMPDP` in UNIX-style and use interactive-command mode \[K2\] key, then the parameters must be specified when you are prompted for them, and not on the command line.

Data Pump Import by tape is not supported.

**Related Topics**

- Starting Oracle Utilities in the BS2000 Program Environment
- Starting Oracle Utilities in the POSIX Program Environment

### 7.8 Recovery Manager on BS2000

On BS2000, Recovery Manager does not support tapes. Disks are the only backup media.

As a workaround, use the Recovery Manager output as a first level storage to be migrated by BS2000 subsystem HSMS (Hierarchical Storage Management System) to tapes. However, it is the administrator's responsibility to ensure the cooperation of the two systems.

The following is an example of a Recovery Manager command in the BS2000 environment:

    /START-EXECUTABLE (*LINK(ORALOAD),RMAN)
    *target "dba1/dba1@i1" catalog "dba2/dba2@i2" cmdfile "b.dat" log "b.log"

### 7.9 Checking the Integrity of the Physical Data Structure

To check the physical data structure integrity of offline databases, use the `DBVERIFY` command-line utility. You can start the `DBVERIFY` utility `dbv`, either in the BS2000 environment or the POSIX environment.

The following examples shows how to use `dbv` in the BS2000 environment:

    /START-EXECUTABLE (*LINK(ORALOAD),DBV)
    file=orcl.dbs.database1.dbf blocksize=4096 feedback=100

The following example shows how to use `dbv` in the POSIX environment:

    $ dbv file=/BS2/orcl.dbs.database1.dbf blocksize=4096 feedback=100

**See Also:**

- "Starting Oracle Utilities in the BS2000 Program Environment"

- "Starting Oracle Utilities in the POSIX Program Environment"

- [Oracle Database Utilities](../sutil/oracle-dbverify-utility.md) for more information about the `DBVERIFY` program

### 7.10 Workload Replay Client

The Workload Replay Client (WRC) is a multithreaded program where each thread submits a workload from a captured session.

An executable program, `wrc` is located in the `$ORACLE_HOME/bin` directory. The specific characteristics of the Workload Replay Client (WRC) on BS2000 is discussed in the following topics:

- About Running Workload Replay Client

- About Troubleshooting Workload Replay Client

**Related Topics**

- [Oracle DatabaseTesting Guide](../ratug/introduction-to-database-replay.md)

#### 7.10.1 About Running Workload Replay Client

On BS2000 the WRC is built as a PTHREADS application with default options which enable the application to run out of the box. The user can modify these options for its own needs. The PTHREADS options are stored in the `WRC.OPTFILE` file, which is created by the installation procedure with the most important options in the installation user ID.

For a proper execution of the WRC, the `WRC.OPTFILE` file must reside in the BS2000 filesystem of the user ID where you run the WRC. Oracle recommends that you copy the `WRC.OPTFILE` file to the BS2000 filesystem of the desired user ID. The WRC itself can only be started in the POSIX shell.

    /COPY-FILE $ORACINST.WRC.OPTFILE,WRC.OPTFILE,SAME

Before you can run the WRC you must prepare your database for testing as described in the Oracle Database Testing Guide. The captured data must be stored in the POSIX file system. If your database is ready for a workload replay, then you can run the WRC.

Start a POSIX shell, run the profile `oracle_home_path/.profile.oracle`, set an `ORACLE_SID` and start the WRC as described in the Oracle Database Testing Guide.

For example:

    /START-POSIX-SHELL
    $ ./u01/app/oracle/product/19.3.0/dbhome_1/.profile.oracle
    $ ORACLE_SID=orcl
    $ export ORACLE_SID
    $ wrc system/password@test mode=replay replaydir=./replay

**See Also:**

- [Oracle Database Testing Guide](../ratug/introduction-to-database-replay.md) to prepare your database for testing

- [Oracle Database Testing Guide](../ratug/replaying-a-database-workload.md) for more information about starting WRC

#### 7.10.2 About Troubleshooting Workload Replay Client

You need not modify the parameters of the `WRC.OPTFILE` except when there are problems with the WRC application. The following table shows the parameters defined in the `WRC.OPTFILE`. Modify the parameter values carefully:

| Parameter | Value                                   | Description                                                                         |
|:----------|:----------------------------------------|:------------------------------------------------------------------------------------|
| `APPLL`   | `$ORACINST.ORALOAD.LIB`                 | Application Load Library                                                            |
| `SCHPO`   | `*STD|FIFO|RR`<br>Default: `*STD`       | Defines the thread scheduling policy: Standard, First In First Out, or Round Robin. |
| `BUSYC`   | Integer 1…2147483647<br>Default: 100    | Number of retries to get a lock.                                                    |
| `MINRT`   | Integer 0…59<br>Default: 1              | Minimum number of resource tasks.                                                   |
| `MAXRT`   | Integer 0…59<br>Default: 1              | Maximum number of resource tasks.                                                   |
| `MSESZ`   | Integer 1…2147483647<br>Default: 262144 | Number of bytes reserved for the main stack.                                        |
| `ILCS7`   | Integer 1…2147483647<br>Default: 262144 | Default size of a stack for a thread.                                               |
| `SHAMS`   | Integer 1…2147483647<br>Default: 131072 | Number of memory pages reserved for the application memory pool.                    |

To get information about the running WRC, call the procedure `ITH-SHOW` from the `SYSPRC` library of the `PTHREADS` installation:

`/CALL-PROCEDURE $TSOS.SYSPRC.PTHREADS.014(ITH-SHOW)`

This utility produces an output similar to the following:

    /CALL-PROCEDURE $TSOS.SYSPRC.PTHREADS.014(ITH-SHOW)
    %  BLS0523 ELEMENT 'ITHSHOW', VERSION 'V01.4A10', TYPE 'L' FROM LIBRARY
    ':BUG2:$
    TSOS.SYSLNK.PTHREADS.014' IN PROCESS
    %  BLS0524 LLM 'ITHSHOW', VERSION 'V01.4A10' OF '2013-11-30 03:17:44' LOADED
    %  BLS0551 COPYRIGHT (C) 2013 Fujitsu Technology Solutions. ALL RIGHTS RESERVED
    STARTED AT 2016-04-20-145816 BY POSIX  (running)
    LLM     = WRC  (prelinked)
    MAIN    = IC@#MAIN
    APPLL   = :POR5:$ORA12102.ORALOAD.LIB
    RUNTL   = :BUG2:$TSOS.SYSLNK.PTHREADS.014
    PTHvers = 01.4A21 2016-02-10 18:55:31
    FDs     = 5 (3 ORIG FDs, 2 RESO FDs)
    Threads = 5 (1 user threads, 4 system threads)
    TYPE  TSN   PID     JOB-TYPE           PRI      CPU-USED CPU-MAX ACCOUNT#
    ORIG  1D4U  2902 (X'0B56')  3 DIALOG  *0 240     3.0365   32767    FSC
                        waiting for new requests
    RESO  1D48  2917 (X'0B65')  3 DIALOG  *0 240     0.0450   32767    FSC
                         executing request
    THRE  1D49  2918 (X'0B66')  3 DIALOG  *0 240     0.2478   32767    FSC

Here you find the TSNs of the tasks involved in the `WRC` application. You can connect to the `WRC` application when you choose the TSN of the `ORIG` task as the input for the parameter TSN of the `ITH-START` procedure in the following format:

`/CALL-PROCEDURE $TSOS.SYSPRC.PTHREADS.014(ITH-START),(TSN=1D4U)`

When you see the double slash prompt you can type `SHOW-PTHREADS-STATUS` to show the status of the running `WRC` application or `CANCEL-THREADED-PROGRAM` to cancel the application. If the `ORIG` task is already terminated, then you can terminate all other tasks of the `WRC` application. In the BS2000 environment, use the following system command:

`/CANCEL-JOB JOB-IDENTIFICATION=``tsn`

In the POSIX environment use the shell command `kill` to abort pending processes. You must use the signal `SIGABRT (6)` or `SIGTERM (15)` to notify the target process:

`$ kill -6 ``pid`

### 7.11 The Oracle Text Loader

This utility imports and exports text data. .

You can start the Oracle Text Loader utility `ctxldr` either in the BS2000 environment or the POSIX environment.

**See Also:**

[Oracle Text](oracle-text.md) for installing Oracle Text

The following examples show how to use `ctxldr` in the BS2000 environment:

    /START-EXECUTABLE (*LINK(ORALOAD),CTXLDR)
    *-USER username/password [options]

The following example shows how to use `ctxldr` in the POSIX environment:

    $ ctxldr -USER username/password [options]

**Related Topics**

- [Oracle Text Reference](../ccref/oracle-text-utilities.md)
- Starting Oracle Utilities in the BS2000 Program Environment
- Starting Oracle Utilities in the POSIX Program Environment
