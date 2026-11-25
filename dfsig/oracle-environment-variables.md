This appendix describes variables that can be specified in the `ORAENV` file, the structured system variable `SYSPOSIX`, or the POSIX shell. Oracle parameters, such as `ORACLE_SID` and `NLS_LANG`, may be specified in the `ORAENV` file, system variable `SYSPOSIX`, or POSIX shell. If you use a `ORAENV` file, then you must follow the `ORAENV` rules for specifying environment variables as described in the following sections. If you use the system variable `SYSPOSIX`, then you must follow the rules to set a `SDF-P` variable. For example, if the variable name contains an underscore '\_' , then you must use a hyphen '-' instead of the underscore. In the POSIX shell, you must follow the UNIX rules to set and export the environment variables.

This appendix contains the following topics:

- ORAENV Rules

- Built-in Variables

- General Variables

- DBA Startup Variables

- Oracle Net Services Variables

**See Also:**

"[Oracle Envrionment Variables](concepts-and-architecture.md)" for more details

### B.1 ORAENV Rules

Consider the following general rules when you create or modify `ORAENV` files:

- All lines which begin with a slash or asterisk (/ or \*) are ignored.

- All variable names must be written in uppercase.

- Spaces must not be included immediately before and after the equals sign (=).

- Do not enclose values in quotation marks unless you want the quotation marks to be part of the value.

- Errors in variable names are not recognized. This means that the value of any variable whose name is typed incorrectly is not modified.

- There is only limited checking of variable assignments. An incorrect value may generate an error message, but may also be interpreted as a null value.

- When variable assignments refer to other variables, BS2000 command file substitution syntax applies. Substitution takes place when the variable is stored in the local environment.

  For example:

      ORAUID=$ORACINST
      SQLPATH=&ORAUID..RDBMS.ADMIN

  assigns the value `$ORACINST`.`RDBMS`.`ADMIN` to the variable `SQLPATH`. If `ORAUID` is changed, then `SQLPATH` automatically reflects the new value.

- The sequence of items in the `ORAENV` file is not generally significant. If an item occurs more than once, then the first occurrence is used.

- If a value is not specified for a variable, then the default value is used, if it exists.

### B.2 Built-in Variables

The following variables are always defined, and may be referenced in other variable assignments:

- LOGNAME

- ORAUID

- PGM

- TERM

- TSN

#### B.2.1 LOGNAME

The `LOGNAME` variable always contains the current BS2000 user ID. Do not alter the value of this variable by assigning a different value to it in the `ORAENV` file.

#### B.2.2 ORAUID

This variable specifies the BS2000 user ID where the Oracle Database programs, installation, and demonstration files are installed. The initial value is derived from the `ORALOAD` link name (the user ID part of the `ORALOAD` library name). This value is usually correct, but if necessary, you can override it by assigning a different value to it in the `ORAENV` file.

Format: `ORAUID`=`$userid` or `ORAUID`=`/BS2/``$userid`

#### B.2.3 PGM

The `PGM` variable contains the program name specified in the BS2000 command `START-EXECUTABLE`. You cannot alter the value of this variable by assigning a different value to it in the `ORAENV` file.

#### B.2.4 TERM

The `TERM` variable contains the terminal type. The default value is SNI9750. This default value is usually correct, but if necessary, you can override it by assigning a different value to it in the `ORAENV` file.

#### B.2.5 TSN

The `TSN` variable contains the task sequence number of the current task. You cannot alter the value of this variable by assigning a different value to it in the `ORAENV` file.

### B.3 General Variables

The following variables are for general use by Oracle DBAs and users:

- CLN_BASE

- CLN_MPID

- CLN_SCOPE

- EXP_CLIB_FILE_IO

- IMP_CLIB_FILE_IO

- NLS_LANG

- OPS_JID

- ORASID

- PRINTPAR

- SQLPATH

- SSSIDPWF

#### B.3.1 CLN_BASE

This variable specifies the address of the shared memory pool for the client-side shared code of Oracle Database, which is used by customer written database applications.

##### Format:

    CLN_BASE=address

##### Default:

200M

#### B.3.2 CLN_MPID

This variable specifies the identification of the shared memory pool for the client-side shared code of Oracle Database, which is used by customer written database applications.

##### Format:

    CLN_MPID=sid

##### Default:

    CLN_MPID=&ORASID

#### B.3.3 CLN_SCOPE

#####

This variable specifies the scope of the shared memory pool for the client-side shared code of Oracle Database, which is used by customer written database applications. The valid values are:

| Value | Description                                                                                                                     |
|:------|:--------------------------------------------------------------------------------------------------------------------------------|
| T     | The use of the memory pool is limited to the calling task.                                                                      |
| U     | All Oracle Database client tasks within the same BS2000 user ID as the calling task are participants of the shared memory pool. |
| G     | All Oracle Database client tasks in the system are participants.                                                                |

##### Format:

`CLN_SCOPE={T|U|G}`

##### Default:

`CLN_SCOPE=G`

#### B.3.4 EXP_CLIB_FILE_IO

This variable should be set to `FALSE` when you use the `Export` utility to overcome a problem with the C library functions, when an export file is written to tape.

Format: `EXP_CLIB_FILE_IO`=`FALSE`

Default: `EXP_CLIB_FILE_IO`=`TRUE`

#### B.3.5 IMP_CLIB_FILE_IO

This variable should be set to `FALSE` when you use the `Import` utility to overcome a problem with the C library functions, when an import file is read from tape.

Format: `IMP_CLIB_FILE_IO`=`FALSE`

Default: `IMP_CLIB_FILE_IO`=`TRUE`

#### B.3.6 NLS_LANG

This variable specifies the language, territory, and character set. For example:

    NLS_LANG=GERMAN_GERMANY.D8BS2000

Format: `NLS_LANG`=`language_territory.character-set`

Default: `NLS_LANG`=`AMERICAN_AMERICA.WE8BS2000`

#### B.3.7 OPS_JID

This variable is used for concatenation with the `OS_AUTHENT_PREFIX`, refer to the initialization parameter. The default value concatenates the value of the parameter `OS_AUTHENT_PREFIX` with the BS2000 user ID. Using `OPS_JID`, you can specify that the BS2000 jobname is used instead. This is useful when many users are sharing a single BS2000 user ID.

Format: `OPS_JID`=`userid/jobname`

Default: `userid`

#### B.3.8 ORASID

This variable defines the database that is used if no database identification is given at connect time.This variable is a synonym of the `ORACLE_SID` variable.

Format: `ORASID`=`sid` (`sid` is a characterstring where 1 \<= length \<= 4)

**Note:**

Oracle recommends that you use the `ORACLE_SID` variable.

#### B.3.9 PRINTPAR

This variable specifies optional variables for the` /PRINT` command internally issued by the `SPOOL OUT` statement in SQL\*Plus. Using this variable, the user can modify the spooled job, and, for example, route the job to a remote printer, add print options for laser printers, and so on. The BS2000 `/PRINT` command for spool files is issued as follows:

`/PRINT ``temporary_spoolfile``,&PRINTPAR `

Format: `PRINTPAR`=`print-options`

#### B.3.10 SQLPATH

This variable specifies a path where SQL\*Plus looks for SQL scripts. Elements of the path are separated by semicolons (;). For example:

    SQLPATH=PRIVATE;$ORACINST

This assignment causes SQL\*Plus to look for filename.SQL, then for `PRIVATE`.`filename`.`SQL`, and finally for `$ORACINST`.`filename`.`SQL`.

Format: `SQLPATH`=`search-path`

Default: `SQLPATH=&ORACLE_HOME/rdbms/admin;&ORAUID..RDBMS.DEMO`

#### B.3.11 SSSIDPWF

This variable specifies the password file.

Format: `SSSIDPWF`=`password-file`

**See Also:**

"[Administering Oracle Database](administering-oracle-database.md)" for more information

### B.4 DBA Startup Variables

The following variables are used during database and network startup. They supplement (and in some cases provide defaults for) variables specified in the initialization file.

To ensure that the variables are consistent, Oracle recommends that database startup and shutdown, background tasks, and server tasks refer to the same `ORAENV` file.

**Note:**

The default values listed in the following sections are built-in defaults, some of them are overridden by settings in the shipped `DEMO`.`P`.`ORAENV`.

The following DBA startup variables include:

- Address and Size Specification

- BGJPAR

- BGJ_PROCEDURE

- BGJPRC_UID / BGJPRC_SID

- BGJ_LOG_JOBSTART

- sid_BGJPAR

- sid_USER

- user_ACCOUNT/ user_PASSWORD

- COM_MPID

- COM_BASE

- COM_SCOPE

- JOBID

- KNL_BASE

- ORACLE_HOME

- PGA_BASE

- PGA_SIZE

- SF_PBLKSIZE

- SGA_BASE

#### B.4.1 Address and Size Specification

Several variables described in this section define memory addresses and sizes. The notations used to specify these items are as follows:

- A number with no modifiers is interpreted as a decimal number

- A number followed by K or M is interpreted as a decimal number multiplied by 1024 or 1048576 (1024\*1024) respectively

- A number enclosed in single quotation marks and preceded by the letter X is interpreted as a hexadecimal number

For example, the following example sets the `KNL_BASE` variable to 8 MB:

    KNL_BASE=8M
    KNL_BASE=8388608
    KNL_BASE=X'800000'

#### B.4.2 BGJPAR

This variable specifies the parameters for the BS2000 command `ENTER-PROCEDURE`, which is used for starting BS2000 jobs for the Oracle Database background and server processes. You can specify most of the parameters that are allowed for the BS2000 command `ENTER-PROCEDURE` in this variable. The `ENTER-PROCEDURE` command is used to submit jobs as follows:

`.``jobname`` ENTER-PROCEDURE ``jobfile``,&BGJPAR `

Format: `BGJPAR`=`parameters`

**Note:**

The `BGJPAR` variable is set up by the installation procedure.

#### B.4.3 BGJ_PROCEDURE

This variable specifies the name of the `ENTER-PROCEDURE` command for starting background jobs.

Format: `BGJ_PROCEDURE=``filename`

Default: `BGJ_PROCEDURE=(&ORAUID..ORALOAD.LIB,ENTER.PRC)`

#### B.4.4 BGJPRC_UID / BGJPRC_SID

These variables specify the user ID and `sid` of the file for the background enter jobs. If you want to use a special enter job file, then the parameters must be set to the desired `userid` and `sid`.

Format:

    BGJPRC_UID=$userid
    BGJPRC_SID=sid

#### B.4.5 BGJ_LOG_JOBSTART

This variable specifies whether the operating system message that a new job was accepted should be logged on `SYSOUT` or not.

Format: `BGJ_LOG_JOBSTART`=`Y/N`

Default: `BGJ_LOG_JOBSTART`=`N`

#### B.4.6 sid_BGJPAR

This variable specifies the parameters, which are used by the `ENTER-PROCEDURE` command to start a server process for the instance specified by `SID`.

Format: `sid`\_`BGJPAR`=`parameters`

Syntax: `sid` is a string of a maximum of 4 alphanumeric characters

`parameters` are the parameters for the `ENTER-PROCEDURE` command as described in the BS2000 Commands manual.

#### B.4.7 sid_USER

This variable specifies the BS2000 user ID where the instance identified by `sid `resides.

Format: `sid`\_`USER`=`userid`

Syntax: `sid` is a string of a maximum of 4 alphanumeric characters

`userid` is a string of a maximum of 8 alphanumeric characters, which follows the naming rules of a BS2000 user ID.

#### B.4.8 user_ACCOUNT/ user_PASSWORD

`user``_ACCOUNT` or `user`\_`PASSWORD` define credentials of a BS2000 user ID, which is used by the `ENTER-PROCEDURE` command to start a process.

Format: `user`\_`ACCOUNT`=`account`

`user`\_`PASSWORD`=`password`

Syntax: `user` is a string of a maximum of 8 alphanumeric characters, which follows the rules of a BS2000 user ID and must match a BS2000 user ID defined by the parameter `sid`\_`USER`.

`account` is a string of a maximum of 8 alphanumeric characters, which follows the naming rules for a BS2000 account number.

`password` is a string of a maximum of 8 alphanumeric characters, which follows the naming rules for a BS2000 password.

#### B.4.9 COM_MPID

This parameter specifies the identification of the shared code pool of the Oracle database instance for some common Oracle Database software components.

Format: `COM_MPID`=`sid`

Default: `COM_MPID`=`&ORASID`

#### B.4.10 COM_BASE

This parameter specifies the address of the shared code pool of the Oracle database instance for some common Oracle Database software components.

Format: `COM_BASE`=`address`

Default: Release Dependent

#### B.4.11 COM_SCOPE

This variable specifies the scope of the shared memory pool for the server-side shared code of Oracle Database

The valid values are:

T - The use of the memory pool is limited to the calling task.

U - All Oracle Database tasks within the same BS2000 user ID as the calling task are participants of the shared memory pool.

G - All Oracle Database tasks in the system are participants.

Format: `COM_SCOPE={T|U|G}`

Default: `COM_SCOPE=G`

#### B.4.12 JOBID

This variable is used internally in identifying the background tasks and generating task-specific names. You must never specify values for this variable.

#### B.4.13 KNL_BASE

This variable specifies the base address of the shared memory pool for the Oracle Database kernel module. This must be an integral number of megabytes.

Format: `KNL_BASE`=`address`

Default: Release Dependent

#### B.4.14 ORACLE_HOME

The Oracle home directory is the directory in the POSIX file system, which contains the installation of the software for a particular Oracle product.

Format: `ORACLE_HOME`=`/path-name`

#### B.4.15 PGA_BASE

This variable specifies the base address of the fixed part of the PGA. The PGA is task-specific, but must be located at a fixed memory address so that the kernel can access it. The base address must lie on a 64 KB boundary.

Format: `PGA_BASE`=`address`

Default: Release Dependent

#### B.4.16 PGA_SIZE

This variable specifies the size of the fixed part of the PGA. This variable must not be changed from its default value.

Format: `PGA_SIZE`=`size`

Default: Release Dependent

#### B.4.17 SF_PBLKSIZE

This variable specifies the physical blocksize of redo log files.

Format: `SF_PBLKSIZE`=`2K|4K`

Default: `2 KB`

**Note:**

This variable cannot be changed after database creation.

#### B.4.18 SGA_BASE

This variable specifies the base address of the shared memory pool for the SGA of an Oracle Database instance. The base address must lie on a megabyte boundary.

Format: `SGA_BASE`=`address`

Default: Release Dependent

**Note:**

There is no corresponding `SGA_SIZE` variable; the size of the SGA memory pool is calculated when the database is started.

### B.5 Oracle Net Services Variables

The following are the Oracle Net Services variables:

- DEFAULT_CONNECTION

- BREAK_HANDLING

- TNS_ADMIN

- TNS_BEQ_TIMEOUT

- TNS_UPDATE_IPNODE

- TNS_DH_TIMEOUT

- NT_IPC_PROTOCOL_UNIX

#### B.5.1 DEFAULT_CONNECTION

This variable provides a default host string for connect requests where no host string is specified. If you connect to the same database always, then it may be convenient to specify this variable. This value must contain everything you would otherwise specify after the "`@`" character. This variable is a synonym of the `TWO_TASK` variable.

Format: `DEFAULT_CONNECTION`=`host-string`

Example:

    DEFAULT_CONNECTION=TNS:
    (DESCRIPTION=
    (ADDRESS=
    (PROTOCOL=TCP)
    (HOST=MADRID)
    (PORT=1521))
    (CONNECT_DATA=
    (SERVICE_NAME=PROD)))

#### B.5.2 BREAK_HANDLING

This variable deactivates the signal routine for user interrupts, which sends a break over the network. An interrupt can be released by pressing the \[K2\] key.

##### Format:

    BREAK_HANDLING=ON|OFF

##### Default:

    BREAK_HANDLING=ON

#### B.5.3 TNS_ADMIN

This variable specifies the path to the Oracle Net Services configuration files, for example, `LISTENER.ORA`, `TNSNAMES.ORA`, and `SQLNET.ORA`. The configuration files can be stored in the BS2000 DMS or POSIX file system. Depending on the target file system, the path can be a BS2000 user ID or a POSIX directory.

If `TNS_ADMIN` is not defined, then the default search path is `NETWORK.ADMIN`, when the program runs in the BS2000 environment.

When the program runs in the POSIX program environment, the default search path for `TNS_ADMIN` is `$ORACLE_HOME/network/admin`.

Format: `TNS_ADMIN`=`$``userid``|/``posix_path`

#### B.5.4 TNS_BEQ_TIMEOUT

This variable specifies the time a parent process waits until it establishes a connection to a child process.

Format: `TNS_BEQ_TIMEOUT`=`lifetime` (in seconds)

Default: `TNS_BEQ_TIMEOUT`=`180`

#### B.5.5 TNS_UPDATE_IPNODE

This variable forces the Oracle Net software to change the server's IP-Node name to an IP-Node address.

Format: `TNS_UPDATE_IPNODE`=`TRUE/FALSE`

Default: `TNS_UPDATE_IPNODE`=`FALSE`

#### B.5.6 TNS_DH_TIMEOUT

If a listener has accepted a connection request which must be handed off to a server, then this variable specifies the time the listener waits for a response from the server.

Format: `TNS_DH_TIMEOUT=sec`

Default: `TNS_DH_TIMEOUT=10`

#### B.5.7 NT_IPC_PROTOCOL_UNIX

Specifies whether to use the POSIX sockets protocol `PF_UNIX` for local IPC communication or the BS2000 sockets protocol `PF_ISO.`

Format: `NT_IPC_PROTOCOL_UNIX={TRUE|FALSE}`

Default: `NT_IPC_PROTOCOL_UNIX=FALSE`

**Note:**

There are some differences in the BEQ adapter when using POSIX sockets. A client using BS2000 sockets with `PF_ISO` for IPC cannot connect through IPC or BEQ adapter to a server that uses the `PF_UNIX` protocol.
