This chapter provides information about administering Oracle Database on UNIX-based operating systems. It contains the following sections:

- Overview

- Environment Variables

- Initialization Parameters

- Managing Diagnostic Data

**See Also:**

- The appropriate appendix in this guide for platform-specific information about administering Oracle Database

- [Oracle Database Administrator's Guide](../admin/getting-started-with-database-administration.md) and [Database 2 Day DBA](../admqs/getting-started-with-database-administration.md) for generic information about administering Oracle Database

### 1.1 Overview

You must set Oracle Database environment variables, parameters, and user settings for Oracle Database to work. This chapter describes the various settings for Oracle Database.

In Oracle Database files and programs, a question mark (?) represents the value of the `ORACLE_HOME` environment variable. For example, Oracle Database expands the question mark in the following SQL statement to the full path of the Oracle home directory:

    SQL> ALTER TABLESPACE TEMP ADD DATAFILE '?/dbs/temp02.dbf' SIZE 200M

Similarly, the at sign (@) represents the `ORACLE_SID` environment variable. For example, to indicate a file that belongs to the current instance, run the following command:

    SQL> ALTER TABLESPACE tablespace_name ADD DATAFILE tempfile@.dbf

### 1.2 Environment Variables

This section describes the most commonly used Oracle Database and operating system environment variables. You must define some environment variables before installing Oracle Database. This section covers the following topics:

- Oracle Database Environment Variables

- Linux and UNIX Environment Variables

- Setting a Common Environment

- Setting the System Time Zone

To display the current value of an environment variable, use the `env` command. For example, to display the value of the `ORACLE_SID` environment variable, run the following command:

    $ env | grep ORACLE_SID

To display the current value of all environment variables, run the `env` command as follows:

    $ env | more

#### 1.2.1 Oracle Database Environment Variables

The following table describes some environment variables used with Oracle Database.

Table 1-1 Oracle Database Environment Variables

| Variable         | Definition                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
|:-----------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `NLS_LANG`       | Function: Specifies the language, territory, and character set of the client environment. The client character set specified by `NLS_LANG` must match the character set of the terminal or terminal emulator. If required, `NLS_LANG` can be temporarily reset to another character set before starting a non-interactive batch program to match the character set of files and scripts processed by this program. The character set specified by `NLS_LANG` can be different from the database character set, in which case the character set is automatically converted.<br>Refer to [Oracle Database Globalization Support Guide](../nlspg/setting-up-globalization-support-environment.md) for a list of parameters for this variable.<br>Syntax:`language_territory.characterset`<br>Example:`french_france.we8iso8859p15` |
| `ORA_NLS10`      | Function: Specifies the directory where the language, territory, character set, and linguistic definition files are stored.<br>Syntax: `directory_path`<br>Example: `$ORACLE_HOME/nls/data`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `ORA_TZFILE`     | Function: Specifies the full path and file name of the time zone file. The Oracle Database Server always uses the large time zone file (`$ORACLE_HOME/oracore/zoneinfo/timezlrg_``number``.dat`). If you want to use the small time zone file on the client side, you must set this environment variable to the full path of the small time zone file (`$ORACLE_HOME/oracore/zoneinfo/timezone_``number``.dat`). If you use the small time zone file on the client side, you must ensure that the database you access contains data only in the time zone regions recognized by the small time zone file.<br>Syntax: `directory_path`<br>Example: `$ORACLE_HOME/oracore/zoneinfo/timezlrg_11.dat`                                                                                                                               |
| `ORACLE_BASE`    | Function: Specifies the base of the Oracle directory structure for Optimal Flexible Architecture compliant installations.<br>Syntax: `directory_path`<br>Example: `/u01/app/oracle`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `ORACLE_HOME`    | Function: Specifies the directory containing the Oracle software.<br>Syntax: `directory_path`<br>Example: `$ORACLE_BASE/product/19.0.0/dbhome_1`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `ORACLE_PATH`    | Function: Specifies the search path for files used by Oracle applications such as SQL\*Plus. If the full path to the file is not specified, or if the file is not in the current directory, then the Oracle application uses `ORACLE_PATH` to locate the file.<br>Syntax: Colon-separated list of directories:<br>`directory1:directory2:directory3`<br>Example: `/u01/app/oracle/product/19.0.0/dbhome_1/bin:`                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `ORACLE_SID`     | Function: Specifies the Oracle system identifier.<br>Syntax: A string of numbers and letters that must begin with a letter. Oracle recommends a maximum of 8 characters for system identifiers. For more information about this environment variable, refer to [Oracle Database Installation Guide](../install-and-upgrade.md).<br>Example: `SAL1`                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `ORACLE_TRACE`   | Function: Enables the tracing of shell scripts during an installation. If it is set to `T`, then many Oracle shell scripts use the `set -x` command, which prints commands and their arguments as they are run. If it is set to any other value, or no value, then the scripts do not use the `set -x` command.<br>Syntax: `T` or not `T`<br>Example: `T`                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `ORAENV_ASK`     | Function: Controls whether the `oraenv` or `coraenv` script prompts or does not prompt for the value of the `ORACLE_SID` environment variable. If it is set to `NO`, then the scripts do not prompt for the value of the `ORACLE_SID` environment variable. If it is set to any other value, or no value, then the scripts prompt for a value for the `ORACLE_SID` environment variable.<br>Syntax: `NO` or not `NO`<br>Example: `NO`                                                                                                                                                                                                                                                                                                                                                                                           |
| `SQLPATH`        | Function: Specifies the directory or list of directories that SQL\*Plus searches for a `login.sql` file.<br>Syntax: Colon-separated list of directories: `directory1:directory2:directory3`<br>Example: `/home:/home/oracle:/u01/oracle`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `TNS_ADMIN`      | Function: Specifies the directory containing the Oracle Net Services configuration files.<br>Syntax: `directory_path`<br>Example: `$ORACLE_HOME/network/admin`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `TWO_TASK`       | Function: Specifies the default connect identifier to use in the connect string. If this environment variable is set, then do not specify the connect identifier in the connect string. For example, if the `TWO_TASK` environment variable is set to `sales`, then you can connect to a database by using the following command:<br>`SQL> CONNECT username`<br>`Enter password: password`<br>Syntax: Any connect identifier.<br>Range of Values: Any valid connect identifier that can be resolved by using a naming method, such as a `tnsnames.ora` file or a directory server.<br>Example: `PRODDB_TCP`                                                                                                                                                                                                                     |
| `NLS_OS_CHARSET` | Function: Specifies the Oracle character set name corresponding to the UNIX locale character set in which the file names and user names are encoded by the operating system. You must set the environment variable `NLS_OS_CHARSET,` if the UNIX locale character set is different from the Oracle client character set. These two character sets may differ, for example, if `NLS_LANG` is set to a particular character set used to encode an SQL script, which is to be executed in an SQL\*Plus session. Usually, the Oracle client character set and the operating system character set are the same and `NLS_OS_CHARSET` must not be set.<br>Syntax: `characterset`<br>Example: `WE8ISO8859P1`                                                                                                                            |

**Note:**

- To prevent conflicts, do not define environment variables with names that are identical to the names of Oracle Database server processes. For example `ARCH`, `PMON`, and `DBWR`.

- If the Oracle installation owner (`oracle` user) environment variables are missing, or if they are set to incorrect paths, then you may encounter undefined errors during Oracle Database startup. Ensure that all the environment variables are correctly set before starting the database. Refer to My Oracle Support Note 373303.1 for more information:

  <https://support.oracle.com/epmos/faces/DocumentDisplay?id=373303.1>

**Caution:**

You must consult Oracle Support before you implement any changes as suggested in the My Oracle Support Note 373303.1.

#### 1.2.2 Linux and UNIX Environment Variables

Oracle Database uses operating system environment variables to define system resources and software locations.

Table 1-2 Environment Variables Used with Oracle Database

| Variable                                                    | Definition                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
|:------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ADA_PATH` (IBM AIX on POWER Systems (64-Bit) only)         | Function: Specifies the directory containing the Ada compiler<br>Syntax: `directory_path`<br>Example: `/usr/lpp/powerada`                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| `CLASSPATH`                                                 | Function: Used with Java applications. The required setting for this variable depends on the Java application. Refer to the product documentation for Java application for more information.<br>Syntax: Colon-separated list of directories or files:`directory1:directory2:file1:file1`<br>Example: There is no default setting. `CLASSPATH` must include the following directories:<br>`$ORACLE_HOME/jdk/jre/lib:$ORACLE_HOME/jlib`                                                                                                                                                     |
| `DISPLAY`                                                   | Function: Used by X-based tools. Specifies the display device used for input and output. Refer to the X Window System documentation for information.<br>Syntax: `hostname:server[.screen]`<br>where `hostname` is the system name (either IP address or alias), `server` is the sequential code number for the server, and `screen` is the sequential code number for the screen. If you use a single monitor, then use the value `0` for both server and screen (`0.0`).<br>Note: If you use a single monitor, then `screen` is optional.<br>Example:<br>`192.0.2.1:0.0`<br>`password:0` |
| `HOME`                                                      | Function: The home directory of the user.<br>Syntax: `directory_path`<br>Example: `/home/``example_home`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `LANG` or `LC_ALL`                                          | Function: Specifies the language and character set used by the operating system for messages and other output. Oracle tools that are programmed in Java, such as Oracle Universal Installer and Oracle Database Configuration Assistant, may also use this variable to determine the language of their user interface. Refer to the operating system documentation for more information.                                                                                                                                                                                                  |
| `LD_OPTIONS`                                                | Function: Specifies the default linker options. Refer to the `ld` man page for more information about this environment variable.                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `LPDEST` (Oracle Solaris only)                              | Function: Specifies the name of the default printer.<br>Syntax: `string`<br>Example: `docprinter`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `LD_LIBRARY_PATH`                                           | Function: Environment variable to specify the path used to search for libraries on UNIX and Linux. The environment variable may have a different name on some operating systems, such as `LIBPATH` on IBM AIX on POWER Systems (64-Bit), and `SHLIB_PATH` on HP-UX.<br>Syntax: Colon-separated list of directories: `directory1:directory2:directory3`<br>Example:`/usr/dt/lib:$ORACLE_HOME/lib`                                                                                                                                                                                          |
| `PATH`                                                      | Function: Used by the shell to locate executable programs; must include the `$ORACLE_HOME/bin` directory.<br>Syntax: Colon-separated list of directories: `directory1:directory2:directory3`<br>Example:` /bin:/usr/bin:/usr/local/bin:/usr/bin/X11:$ORACLE_HOME/bin:$HOME/bin:`                                                                                                                                                                                                                                                                                                          |
| `PRINTER`                                                   | Function: Specifies the name of the default printer.<br>Syntax: `string`<br>Example: `docprinter`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `TEMP`, `TMP`, and `TMPDIR`                                 | Function: Specifies the default directories for temporary files. If set, then the tools that create temporary files create them in one of these directories.<br>Syntax: `directory_path`<br>Example:`/u02/oracle/tmp`                                                                                                                                                                                                                                                                                                                                                                     |
| `USER` (when using SSH to connect on HP-UX Itanium systems) | Function: Specifies the name of the user logging in.<br>Syntax: `string`<br>Example: `oracle`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |

#### 1.2.3 Setting a Common Environment

This section describes how to set a common operating system environment by using the `oraenv` or `coraenv` scripts, depending on the default shell:

- For the Bourne, Bash, or Korn shell, use the `oraenv` command.

- For the C shell, use the `coraenv` command.

##### oraenv and coraenv Script Files

The `oraenv` and `coraenv` scripts are created during installation. These scripts set environment variables based on the contents of the `oratab` file and provide:

- A central means of updating all user accounts with database changes

- A mechanism for switching between databases specified in the `oratab` file

You may find yourself frequently adding and removing databases from the development system or your users may be switching between several different Oracle Databases installed on the same system. You can use the `oraenv` or `coraenv` script to ensure that user accounts are updated and to switch between databases.

**Note:**

Do not call the `oraenv` or `coraenv` script from the Oracle software owner (typically, `oracle`) user's shell startup script. Because these scripts prompt for values, they can prevent the `dbstart` script from starting a database automatically when the system starts.

The `oraenv` or `coraenv` script is usually called from the user's shell startup file (for example, `.profile` or`.login`). It sets the `ORACLE_SID` and `ORACLE_HOME` environment variables and includes the `$ORACLE_HOME/bin` directory in the `PATH` environment variable setting. When switching between databases, users can run the `oraenv` or `coraenv` script to set these environment variables.

**Note:**

To run one of these scripts, use the appropriate command:

- `coraenv` script:

      % source /usr/local/bin/coraenv

- `oraenv` script:

      $ . /usr/local/bin/oraenv

##### Local bin Directory

The directory that contains the `oraenv`, `coraenv`, and `dbhome` scripts is called the local `bin` directory. All database users must have read access to this directory. Include the path of the local bin directory `PATH` environment variable setting for the users. When you run the `root.sh` script after installation, the script prompts you for the path of the local `bin` directory and automatically copies the `oraenv`, `coraenv`, and `dbhome` scripts to the directory that you specify. The default local `bin` directory is `/usr/local/bin`. If you do not run the `root.sh` script, then you can manually copy the `oraenv` or `coraenv` and `dbhome` scripts from the `$ORACLE_HOME/bin` directory to the local `bin` directory.

#### 1.2.4 Setting the System Time Zone

The `TZ` environment variable sets the time zone. It enables you to adjust the clock for daylight saving time changes or different time zones.

**See Also:**

- "ORA_TZFILE" in "Table 1-1"

- [Oracle Database Globalization Support Guide](../nlspg/setting-up-globalization-support-environment.md) and [Oracle Database Administrator's Guide](../admin/creating-and-configuring-an-oracle-database.md) for more information about setting the database time zone

### 1.3 Initialization Parameters

These sections provide information about Oracle Database initialization parameters.

Topics:

- ASM_DISKSTRING Initialization Parameter

- DISK_ASYNCH_IO Initialization Parameter (HP-UX)

- PROCESSOR_GROUP_NAME Initialization Parameter

- Managing Diagnostic Data

#### 1.3.1 ASM_DISKSTRING Initialization Parameter

**Note:**

Only Automatic Storage Management instances support the `ASM_DISKSTRING` initialization parameter.

The syntax for assigning a value to the `ASM_DISKSTRING` initialization parameter is as follows:

    ASM_DISKSTRING = 'path1'[,'path2', . . .]

In this syntax, `pathn` is the path to a raw device. You can use wildcard characters when specifying the path.

Table 1-3 lists the platform-specific default values for the `ASM_DISKSTRING` initialization parameter.

Table 1-3 Default Values of the ASM_DISKSTRING Initialization Parameter

| Platform                          | Default Search String |
|:----------------------------------|:----------------------|
| Oracle Solaris                    | `/dev/rdsk/*`         |
| Linux                             | `/dev/sd*`            |
| IBM AIX on POWER Systems (64-Bit) | `/dev/rhdisk*`        |
| HP-UX                             | `/dev/rdisk*`         |

#### 1.3.2 DISK_ASYNCH_IO Initialization Parameter (HP-UX)

The `DISK_ASYNCH_IO` initialization parameter determines whether the database files reside on raw disks or file systems. Asynchronous I/O is available only with Automatic Storage Management disk group which uses raw partitions as the storage option for database files. The `DISK_ASYNCH_IO` parameter can be set to `TRUE` or `FALSE` depending on where the files reside. By default, the value is set to `TRUE`.

**Note:**

The `DISK_ASYNCH_IO` parameter must be set to `FALSE` when the database files reside on file system. This parameter must be set to `TRUE` only when the database files reside on raw partitions.

#### 1.3.3 PROCESSOR_GROUP_NAME Initialization Parameter

`PROCESSOR_GROUP_NAME` specifies the name of the processor group in which an instance is running. This parameter instructs Oracle databases to run only on processors which are a part of the specified operating system processor groups. For NUMA systems, all System Global Area (SGA) and Program Global Area (PGA) are allocated from the NUMA nodes associated with the CPUs in this processor group.

`PROCESSOR_GROUP_NAME` parameter is only supported on Linux x86-64 and Oracle Solaris 11 SRU 4 and later.

On Linux x86-64, the named subset of CPUs is created through a Linux feature called control groups (cgroups). Cgroups are introduced in Linux kernel version 2.6.24. It is created by specifying a name and a set of CPUs for the group. When a process is mapped to a cgroup, it uses only the CPUs associated with the cgroup.

On Oracle Solaris 11 SRU 4, the named subset of CPUs is created through a feature called resource pools. Each resource pool consists of a name and a set of CPUs. When a process is mapped to a resource pool, it uses the CPUs associated with the resource pool.

**Note:**

Oracle recommends that the `PROCESSOR_GROUP_NAME` parameter is set only for databases using a dedicated connection broker. The `USE_DEDICATED_BROKER` initialization parameter is used to configure the dedicated connection brokers.

**Related Topics**

- [Oracle Database Reference](../refrn/USE_DEDICATED_BROKER.md)
- [Oracle Database Reference](../refrn/PROCESSOR_GROUP_NAME.md)

#### 1.3.4 Managing Diagnostic Data

Diagnostic data includes the trace files, dumps, and core files to investigate, track, and resolve problems quickly and effectively.

**Related Topics**

- [Oracle Database Administrator’s Guide](../admin/diagnosing-and-resolving-problems.md)
