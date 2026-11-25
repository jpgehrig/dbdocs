Starting with Oracle Database 12c Release 1, you can use the Oracle Multitenant option to configure and manage a multitenant environment. The multitenant architecture enables an Oracle Database to function as a multitenant container database (CDB) that includes zero, one, or many customer-created pluggable databases (PDBs). A PDB is a portable collection of schemas, schema objects, and nonschema objects.

This chapter describes the following:

- Prerequisites for Database Creation

- About Creating a Non-CDB

- About Creating a Multitenant Container Database

### 3.1 Prerequisites for Database Creation

Before you can create a database, the following prerequisites must be met:

1.  Oracle Database 19c must be installed under the installation user ID.
2.  The BS2000 system administrator must create a DBA user ID with the required attributes.
    **See Also:**

    - [“Oracle Database Installation and Deinstallation”](oracle-database-installation-and-deinstallation.md) for details on how to install Oracle Database

    - [“About Creating Users and Groups for Oracle Databases”](oracle-database-installation-and-deinstallation.md) for details about the attributes

### 3.2 About Creating a Non-CDB

A non-CDB is the traditional type of an Oracle database, which was supported in Oracle Database releases before 12c.

Oracle Database 19c supports a non-CDB.

You can create a non-CDB either automatically or manually. Oracle recommends that you use the automatic creation procedure outlined in the “Creating a Database Automatically” section. Instructions on how to create a traditional database manually are given in the “Creating a Database Manually” section.

This section describes the following topics:

- Creating a Database Automatically

- Creating a Database Manually

#### 3.2.1 Creating a Database Automatically

Complete the following steps to create a database automatically:

1.  Log in to the DBA user ID.
2.  To start the automatic creation procedure, `INSTALL.P.SUPER`, enter the following command:
        /CALL-PROCEDURE $ORACINST.INSTALL.P.SUPER

    When you run the `INSTALL.P.SUPER` procedure, you must specify the value of the following keyword parameters (the default values are used if you choose not to modify the values):

    | Parameter  | Value                                                                                                                                 |
    |:-----------|:--------------------------------------------------------------------------------------------------------------------------------------|
    | `BATCH`    | Enter YES to run the procedure in the batch mode. The default is set to `YES`. So, by default the procedure is run in the batch mode. |
    | `CPULIMIT` | Sets the CPU time limit for batch jobs. The default is 2000.                                                                          |
    | `PLSQL`    | Enter NO to suppress automatic installation of the basic PL/SQL package. The default is `YES`.                                        |
    | `VIEWS`    | Enter NO to suppress automatic installation of the basic views (catalog, import/export, and so on). The default is `YES`.             |
3.  Answer the prompts for the following information. If you do not enter any value, then the default values shown on the screen are used:
    | Parameter  | Value                                                                                                                                                                                                                                                            |
    |:-----------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `DBASID`   | Enter the 1 - 4 character system ID of the database you are installing. This is a mandatory parameter.                                                                                                                                                           |
    | `JOBCLASS` | Enter the jobclass to be used for Oracle Database 19c background jobs. This is mandatory.<br>**Note:**<br>The jobclass must be defined with the characteristics `TP-ALLOWED=YES` and `NO-CPU-LIMIT=YES`.                                                         |
    | `UPDATE`   | Enter YES if you have existing files for this `SID` and if you want to update them.                                                                                                                                                                              |
    | `SYSPW`    | Enter the desired password for the Oracle Database user `SYS`.                                                                                                                                                                                                   |
    | `SYSTEMPW` | Enter the desired password for the Oracle Database user `SYSTEM`.<br>Note: By default the `SYSTEM` user has the password `MANAGER`. For security reasons, Oracle recommends that you change this password immediately after installation.                        |
    | `JAVA`     | Enter NO if you do not need a Java enabled database (thus saving memory, CPU, and disk space resources). For more information refer to [“Java in the Database”](java-in-the-database.md) section.                                                                |
    | `DBSIZE`   | Enter the size of the `system` tablespace files in bytes, kilobytes, or megabytes. The value you enter can have one of the following forms:<br>• 44M for 44 megabytes<br>• 44000K for 44000 kilobytes<br>• 10000000 for 10000000 bytes<br>The default is 400 MB. |
    | `AUXSIZE`  | Enter the size of the `sysaux` tablespace file in bytes, kilobytes, or megabytes. The value you enter can have one of the following forms:<br>• 44M for 44megabytes<br>• 44000K for 44000 kilobytes<br>• 10000000 for 10000000 bytes<br>The default is 300 MB.   |
    | `LOGSIZE`  | Enter the size of the log files in bytes, kilobytes, or megabytes. The value you enter can have one of the following forms:<br>• 1M for 1 megabytes<br>• 1000K for 1000 kilobytes<br>• 100000 for 100000 bytes<br>The default is 20000 KB.                       |
    | `UNDOSIZE` | Enter the size of the undo tablespace file in bytes, kilobytes, or megabytes. The value you enter can have one of the following forms:<br>• 44M for 44 megabytes<br>• 44000K for 44000 kilobytes<br>• 10000000 for 10000000 bytes<br>The default is 100 MB.      |
    | `LOCAL`    | Enter NO if you do not require a locally managed system tablespace. The default is `YES`. If you choose a locally managed system tablespace, then Oracle automatically creates a default temporary tablespace.                                                   |
    | `DEFTS`    | Enter NO if you do not want to create a default permanent tablespace. The default is `YES`.                                                                                                                                                                      |
    | `TEMPTS`   | This prompt only appears if you do not want a locally managed system tablespace. Enter NO if you do not want a default temporary tablespace. The default is `YES`.                                                                                               |
    | `CHARSET`  | Enter the character set with which you want the database to be created (the default is `WE8BS2000`).<br>For more information refer to [“Globalization Support”](globalization-support.md).                                                                       |
    | `NCHARSET` | Enter the national character set used to store data in columns specifically defined as `NCHAR`, `NCLOB`, or `NVARCHAR2`. Valid values are `AL16UTF16` and `UTF8`. The default is `AL16UTF16`.                                                                    |

Unless specified otherwise, `$ORACINST.INSTALL.P.SUPER` generates and enters a batch job which:

- Calls `INSTALL.P.DBA`.

- Creates the `system` and `sysaux` tablespace.

- Creates the default permanent tablespace, temporary tablespace, and undo tablespace.

- Creates the log files.

- Initializes the database.

- Runs `CATALOG.SQL`.

- Runs `CATPROC.SQL` .

- Installs the tables for online help messages.

- Installs the `DEMO` tables.

- Changes the system passwords if necessary.

- Calls the verification procedure.

When `$ORACINST.INSTALL.P.SUPER` has completed, you should have an initialized, ready-to-use database, and a running Oracle Database instance. The results of the job are listed in the file, `L.``sid``.INSSUP.SYSOUT`, where `sid` is the system ID of the database that you just installed.

#### 3.2.2 Creating a Database Manually

Oracle recommends that you use the automatic creation procedure outlined in "Creating a Database Automatically". The manual creation procedure performs the same steps as the automatic creation procedure. However, when you create a database manually, you can perform the steps at your own pace, and also choose which of the optional steps to perform, omit, or perform later.

This section describes the following topics:

- Creating Parameter Files for a Non-CDB

- Creating the Database

- About Installing Data Dictionary Views

- About Installing Online Help Messages

- About Installing Demo Tables

- About Installing Sample Schemas

- About Verifying Database Creation

- About Installing Oracle Text

- About Installing Java

##### 3.2.2.1 Creating Parameter Files for a Non-CDB

Create the parameter files for the new database as follows:

1.  Log in to the DBA user ID.
2.  Call the BS2000 command procedure `INSTALL.P.DBA`. This procedure generates parameter files for the database in the DBA user ID. When the procedure begins you are prompted to supply a 1 to 4 character system ID for the database you are creating.
    To install the DBA files, enter the following command:

        /CALL-PROCEDURE $ORACINST.INSTALL.P.DBA

    This procedure prompts you for the following information:

    | Parameter  | Value                                                                                                                                                                   |
    |:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `DBASID`   | Enter the 1 - 4 character system ID of the database you are creating.                                                                                                   |
    | `JOBCLASS` | Enter the BS2000 jobclass to be used for background and server tasks.<br>The jobclass must be defined with the characteristics `TP-ALLOWED=YES` and `NO-CPU-LIMIT=YES`. |

    You can also modify the following keyword parameters when invoking this procedure:

    | Parameter | Value                                                                                  |
    |:----------|:---------------------------------------------------------------------------------------|
    | `LOG`     | Enter WRITE-TEXT (the BS2000 command name) if you want to have install actions listed. |
    | `UPDATE`  | Enter YES/NO to indicate whether existing files are to be updated. The default is NO.  |

    The `$ORACINST.INSTALL.P.DBA` procedure generates the following files into the DBA user ID:

    - `sid``.P.ORAENV`: Oracle Database environment definition file

    - `sid``.DBS.INIT.ORA`: Oracle Database initialization file

    where `sid` is the system ID for the database being created.

    These files are generated by using the two corresponding files `DEMO.P.ORAENV` and `DEMO.DBS.INIT.ORA` in the installation user ID as templates.

##### 3.2.2.2 Creating the Database

After generating the DBA files, you must create the database. This section describes the procedure for creating the database:

- About Modifying the Initialization File for a Non-CDB

- About Modifying the ORAENV File for a Non-CDB

- About Using SQL\*Plus to Create the Database

###### 3.2.2.2.1 About Modifying the Initialization File for a Non-CDB

Determine if you want to make any changes to parameters in the distributed initialization file, `sid``.DBS.INIT.ORA` (where `sid` is the system ID for the database). The SGA parameters may need to be adjusted to reflect memory limitations and the maximum number of users who can access the Oracle Database instance concurrently. Use a BS2000 editor to make the modifications.

**See Also:**

[Oracle Database Reference](../refrn/parameter-files.md) for more information about the initialization parameters

###### 3.2.2.2.2 About Modifying the ORAENV File for a Non-CDB

Modify the environment definition file, `sid``.P.ORAENV`, according to your specific requirements. Remember that a number of variables are evaluated during startup only. If you modify such a variable in the `ORAENV` file later on, then you may have to wait for the next startup for the changes to take effect.

Do not explicitly set the environment variable `NLS_LANG` when you run Oracle supplied SQL scripts.

###### 3.2.2.2.3 About Using SQL\*Plus to Create the Database

Remember that you must call the applicable `sid``.P.ORAENV` procedure before calling SQL\*Plus. To execute SQL\*Plus, enter the following commands:

    /START-EXECUTABLE (*LINK(ORALOAD),SQLPLUS)
    * /NOLOG
    SQL> CONNECT / AS SYSDBA
    SQL> STARTUP NOMOUNT [PFILE=filename]

- `/NOLOG` omits being prompted for user name and password.

- `CONNECT` gives you a connection to an idle instance.

- The last statement starts the Oracle Database instance.

If you want to use your own copy of the initialization file (`sid``.DBS.INIT.ORA`), then use the `PFILE=``filename` option, as illustrated in the previous command.

The following statement creates database and log files:

    SQL> CREATE DATABASE...;

**Note:**

If you get an error before the first `SQL>` prompt, then it may be caused by either a missing `ORAENV` file (or `ORASID` not set in the `ORAENV` file), or sometimes by an address space conflict. For example, the address range you assigned to the kernel memory pool (`KNL_BASE`) could be occupied by a subsystem.

##### 3.2.2.3 About Installing Data Dictionary Views

Run the scripts necessary to build data dictionary views, synonyms, and PL/SQL packages. Run the following commands:

    SQL> SPOOL filename
    SQL> SET TERMOUT OFF
    SQL> $ORACLE_HOME/rdbms/admin/catalog.sql
    SQL> $ORACLE_HOME/rdbms/admin/catproc.sql

##### 3.2.2.4 About Installing Online Help Messages

To install the Online Help facility, enter the following command:

`/CALL-PROCEDURE $ORACINST.INSTALL.P.HELP,(``sid``[,SYSTEMPW=systempw])`

##### 3.2.2.5 About Installing Demo Tables

To install demo tables, enter the following:

`/CALL-PROCEDURE $ORACINST.INSTALL.P.DEMO,(``sid` `[,SYSTEMPW=systempw])`

##### 3.2.2.6 About Installing Sample Schemas

To install sample schemas, enter the following:

`/CALL-PROCEDURE $ORACINST.INSTALL.P.SAMPLES,(``sid` `[,SYSTEMPW=systempw] [,SYSPW=syspw])`

The procedure `INSTALL.P.SAMPLES` installs the human resources (HR), order entry (OE), info exchange (IX), and sales history (SH) sample schemas with the default passwords. Product media (PM) is not supported.

##### 3.2.2.7  About Verifying Database Creation

To verify if the demonstration database was correctly created, enter the following:

`/CALL-PROCEDURE $ORACINST.INSTALL.P.VERIFY,(``sid` `[,SYSTEMPW=systempw])`

If the demonstration database was correctly created, then you see messages like the following displayed on the screen:

`*SCOTT'S TABLE EMP IS INSTALLED`

##### 3.2.2.8 About Installing Oracle Text

Installing Oracle Text is summarized in the "[Oracle Text](oracle-text.md)" chapter of this book.

##### 3.2.2.9 About Installing Java

Installing Java is summarized in the "[Java in the Database](java-in-the-database.md)" chapter of this book.

### 3.3 About Creating a Multitenant Container Database

A multitenant container database (CDB) is a single physical database that contains zero, one, or many user-created pluggable databases. A pluggable database (PDB) is a portable collection of schemas, schema objects, and nonschema objects that appears to an Oracle Net client as a non-CDB. A non-CDB is a traditional Oracle database that cannot contain PDBs.

Starting with Oracle Database 12c Release 1, you can create a multitenant container database (CDB).

The topics in this section describe how to create a CDB manually on Fujitsu BS2000. As creating a CDB involves Perl scripts, you must perform some steps in the POSIX environment. Perl is supported only in the POSIX environment of BS2000.

The following topics are discussed:

- Creating Parameter Files for a CDB

- About Creating a CDB

**See Also:**

[Oracle Database Administrator’s Guide](../multi/creating-and-configuring-a-cdb.md) for more information about creating a CDB

#### 3.3.1 Creating Parameter Files for a CDB

Create the parameter files for the new database as follows:

1.  Log in to the DBA user ID.
2.  Call the BS2000 command procedure `INSTALL.P.DBA`. This procedure generates parameter files for the database in the DBA user ID. When the procedure begins you are prompted to supply a 1 to 4 character system ID for the database you are creating.
    To install the DBA files, enter the following command:

        /CALL-PROCEDURE $ORACINST.INSTALL.P.DBA

    This procedure prompts you for the following information:

    | Parameter  | Value                                                                                                                                                                   |
    |:-----------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `DBASID`   | Enter the 1 - 4 character system ID of the database you are creating.                                                                                                   |
    | `JOBCLASS` | Enter the BS2000 jobclass to be used for background and server tasks.<br>The jobclass must be defined with the characteristics `TP-ALLOWED=YES` and `NO-CPU-LIMIT=YES`. |

    You can also modify the following keyword parameters when invoking this procedure:

    | Parameter | Value                                                                                  |
    |:----------|:---------------------------------------------------------------------------------------|
    | `LOG`     | Enter WRITE-TEXT (the BS2000 command name) if you want to have install actions listed. |
    | `UPDATE`  | Enter YES/NO to indicate whether existing files are to be updated. The default is NO.  |

    The `$ORACINST.INSTALL.P.DBA` procedure generates the following files into the DBA user ID:

    - `sid``.P.ORAENV`: Oracle Database environment definition file

    - `sid``.DBS.INIT.ORA`: Oracle Database initialization file

    where `sid` is the system ID for the database being created.

    These files are generated by using the two corresponding files `DEMO.P.ORAENV` and `DEMO.DBS.INIT.ORA` in the installation user ID as templates.

#### 3.3.2 About Creating a CDB

The procedure to create a multitenant container database (CDB) is discussed in the following topics:

- About Modifying the Initialization File for a CDB

- About Modifying the ORAENV File for a CDB

- Using SQL\*Plus to Create a CDB

##### 3.3.2.1 About Modifying the Initialization File for a CDB

Determine if you want to make any changes to the parameters in the initialization file, `sid``.DBS.INIT.ORA` (where `sid` is the system ID for the database). The SGA parameters may need to be adjusted to reflect memory limitations and the maximum number of users who can access the Oracle Database instance concurrently. Use a BS2000 editor to make the modifications.

To create a CDB, set the value for the `ENABLE_PLUGGABLE_DATABASE` initialization parameter in the `sid``.DBS.INIT.ORA` file as follows:

`ENABLE_PLUGGABLE_DATABASE=TRUE`

**See Also:**

[Oracle Database Reference](../refrn/parameter-files.md) for an explanation of initialization parameters

##### 3.3.2.2 About Modifying the ORAENV File for a CDB

Modify the environment definition file,` sid``.P.ORAENV`, according to your specific requirements. Remember that a number of variables are evaluated during startup only. If you modify such a variable in the `ORAENV` file later on, then you may have to wait for the next startup for the changes to take effect.

Do not explicitly set the environment variable `NLS_LANG` when you run Oracle supplied SQL scripts.

##### 3.3.2.3 Using SQL\*Plus to Create a CDB

Complete the following steps to create a CDB using the SQL\*Plus utility:

1.  In the DBA user ID, change to the POSIX shell by executing the BS2000 SDF command:
    `/START-POSIX-SHELL`
2.  Start SQL\*Plus in the POSIX shell and start up the instance with the `NOMOUNT` option:
        $ . oracle_home_path/.profile.oracle
        $ ORACLE_SID=sid
        $ export ORACLE_SID
        $ sqlplus /nolog
        SQL> connect / as sysdba
        SQL> startup nomount;
3.  Execute a SQL statement similar to the following to create `CDB$ROOT` and `PDB$SEED` of the CDB. In the following example, a CDB with the name `CDB1` is created:
        SQL> CREATE DATABASE CDB1
        USER SYS IDENTIFIED BY sys_password
        USER SYSTEM IDENTIFIED system_password
        LOGFILE 'CDB1.DBS.LOG1.DBF' SIZE 20M, 'CDB1.DBS.LOG2.DBF' SIZE 20M
        DATAFILE 'CDB1.DBS.DATABASE1.DBF' SIZE 400M
        SYSAUX DATAFILE 'CDB1.DBS.SYSAUX.DBF' SIZE 200M
        DEFAULT TABLESPACE USERS
        DATAFILE 'CDB1.DBS.USERS1.DBF' SIZE 100M AUTOEXTEND ON
        DEFAULT TEMPORARY TABLESPACE TEMP
        TEMPFILE 'CDB1.DBS.TEMP1.DBF' SIZE 100M AUTOEXTEND ON
        UNDO TABLESPACE UNDOTBS1
        DATAFILE 'CDB1.DBS.UNDO1.DBF' SIZE 100M AUTOEXTEND ON
        CHARACTER SET WE8BS2000
        NATIONAL CHARACTER SET AL16UTF16
        EXTENT MANAGEMENT LOCAL
        ENABLE PLUGGABLE DATABASE
        SEED FILE_NAME_CONVERT = ('DBS','SEED');
4.  The next statement installs all of the components required by a CDB. For example, it runs the SQL scripts `catalog.sql` and `catproc.sql` in `CDB$ROOT` and `PDB$SEED` of the CDB:
    `SQL> @$ORACLE_HOME/rdbms/admin/catcdb.sql`
5.  Exit SQL\*Plus and check the spool files for error messages.
