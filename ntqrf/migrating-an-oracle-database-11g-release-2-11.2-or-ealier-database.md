To migrate Oracle Database 11g Release 2 (11.2) or earlier database for 32-bit Windows to Oracle Database 19c for 64-bit Windows, perform the following steps:

1.  Install Oracle Database 19c for 64-bit Windows.

2.  Create the new Oracle Database 19c service at the command prompt:

        C:\> ORADIM -NEW -SID SID [-INTPWD PASSWORD ] -MAXUSERS USERS
        -STARTMODE AUTO -PFILE ORACLE_HOME\DATABASE\INITSID.ORA

    The following table provides more information about the values you must supply.

    | Parameter     | Description                                                                                                                                                                                                                                                                                |
    |:--------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `SID`         | `SID` of the database you are migrating.                                                                                                                                                                                                                                                   |
    | `PASSWORD`    | Password for the new Oracle Database 19c for 64-bit Windows database. This is the password for the user connected with the `SYSDBA` privileges. The `-INTPWD` option is not required. If you do not specify it, then operating system authentication is used, and no password is required. |
    | `USERS`       | Maximum number of users who can be granted `SYSDBA` and `SYSOPER` privileges.                                                                                                                                                                                                              |
    | `ORACLE_HOME` | Oracle home directory. Ensure that you specify the full path name with the `-PFILE` option, including the drive letter of the Oracle home directory.                                                                                                                                       |

3.  Copy the 32-bit data files to the new 64-bit Oracle home.

4.  Copy the 32-bit configuration files to the 64-bit Oracle home.

    1.  If your 32-bit initialization parameter file has an `IFILE` (include file) entry, then copy the file specified by the `IFILE` entry to the 64-bit Oracle home and edit the `IFILE` entry in the initialization parameter file to point to its new location.

    2.  If you have a password file that resides in the 32-bit Oracle home, then copy the password file to the 64-bit Oracle home. The default 32-bit password file is located in `ORACLE_HOME``\database\pwd``SID``.ora`, where `SID` is your Oracle instance ID.

5.  If 19c Oracle home uses a Windows User Account as the Oracle Home User, then add this Oracle Home User to the list of users and grant file permissions or directory permissions for all the database files, `init.ora` files, oracle password files and so on.

6.  Add the `_SYSTEM_TRIG_ENABLED = false` parameter to the `ORACLE_HOME``\database\ORACLE_``SID` `\init.ora` file in the 64-bit Oracle home before changing the word size.

7.  Remove this parameter from the initialization file after the word size change is complete.

8.  Go to the 64-bit `ORACLE_HOME``\rdbms\admin` directory from the command prompt.

9.  Start SQL\*Plus:

        C:\> sqlplus /NOLOG

10. Connect to the database instance as `SYSDBA`:

        SQL> CONNECT / AS SYSDBA;

11. Re-create the 64-bit control files using the `CREATE CONTROLFILE` command. This creates the new control file in the `ORACLE_HOME``\database` directory.

    Here is an example of a database named `orcl32` on a 32-bit computer migrating to `orcl64` on a 64-bit computer:

        CREATE CONTROLFILE REUSE DATABASE "T1" NORESETLOGS NOARCHIVELOG
            MAXLOGFILES 32
            MAXLOGMEMBERS 2
            MAXDATAFILES 32
            MAXINSTANCES 16
            MAXLOGHISTORY 1815
        LOGFILE
            GROUP 1 'C:\app\username\oradata\orcl64\REDO03.LOG'  SIZE 1M,
            # was   'C:\app\username\oradata\orcl32\...LOG'
            # on the 32-bit computer
            GROUP 2 'C:\app\username\oradata\orcl64\REDO02.LOG'  SIZE 1M,
            GROUP 3 'C:\app\username\oradata\orcl64\REDO01.LOG'  SIZE 1M
        DATAFILE
           'C:\app\username\oradata\orcl64\SYSTEM01.DBF',
            # was 'C:\app\username\oradata\orcl32\...DBF'
            # on the 32-bit computer
           'C:\app\username\oradata\orcl64\RBS01.DBF',
           'C:\app\username\oradata\orcl64\USERS01.DBF',
           'C:\app\username\oradata\orcl64\TEMP01.DBF',
           'C:\app\username\oradata\orcl64\TOOLS01.DBF',
           'C:\app\username\oradata\orcl64\INDX01.DBF',
           'C:\app\username\oradata\orcl64\DR01.DBF'
        CHARACTER SET AL32UTF8;

12. Alter the `init` file from the 32-bit computer to include the new control file generated in the preceding step.

13. Shut down the database on the 64-bit computer:

        SQL> SHUTDOWN IMMEDIATE;

14. Start the database migration:

        SQL> STARTUP MIGRATE;

15. Migrate the database.

    **Note:**

    Upgrading to Oracle Database 19c is supported only when the same Windows User Account is used as the Oracle Home User in both the source and destination Oracle homes, or when the home from which the database is being upgraded uses a Windows built-in account.

16. Shut down the database:

        SQL> SHUTDOWN IMMEDIATE;

17. Restart the database:

        SQL> STARTUP OPEN;

**See Also:**

- [Oracle Database Installation Guide for Microsoft Windows](../ntdbi/index.md)

- [Tasks to Complete Only After Manually Upgrading Oracle Database](../upgrd/tasks-complete-only-manually-upgrading-oracle-database.md) for more information about changing word size, [Upgrading Oracle Database](../upgrd/upgrading-oracle-database-parallel-upgrade-utiility-replay-upgrade.md) about migrating the database, and [Prerequisites for Preparing Oracle Home on Windows](../upgrd/prerequisites-for-preparing-oracle-home-on-windows.md) for information about prerequisites for preparing a new Oracle home on Windows in Oracle Database Upgrade Guide

**Related Topics**

- [Backing Up a 32-Bit Oracle Database](backing-up-a-32-bit-oracle-database.md)

**Parent topic:** [Overview of Database Migration from a 32-Bit Windows Computer](overview-of-database-migration-from-a-32-bit-windows-computer.md)
