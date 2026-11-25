## 8  Downgrading Oracle Database to an Earlier Release

For supported releases of Oracle Database, you can downgrade a database to the release from which you last upgraded.

For example, if you recently upgraded your Oracle Database 12c release 1 (12.1.0.2( to release 19c, and you did not change the compatible initialization parameter to 19.1.0, then you can downgrade to release 12.1.0.2.

- Supported Releases for Downgrading Oracle Database
  You can downgrade both major releases and release update or patchset releases, based on the original Oracle Database release from which the database was upgraded.
- Prepare to Downgrade a Standby Database with the Primary
  If you are using an Oracle Data Guard Standby database, then review the procedure you can use to downgrade the standby database with the primary database
- Check COMPATIBLE Parameter when Downgrading Oracle Database
  If `COMPATIBLE` has been changed after the upgrade, then it is no longer possible to downgrade an Oracle Database.
- Perform a Full Backup Before Downgrading Oracle Database
  Oracle strongly recommends that you perform a full backup of your new Oracle Database release before you downgrade to a supported earlier release.
- Performing Required Predowngrade Steps for Oracle Database
  Complete the required preparation steps described here before you downgrade Oracle Database to the earlier release from which you upgraded.
- Using Scripts to Downgrade a CDB or Non-CDB Oracle Database
  To automate downgrades, starting in Oracle Database 19c, Oracle provides the `dbdowngrade` utility script. When necessary, you can also continue to run `catdwgrd.sql` manually, as in previous releases.
- Downgrading a Single Pluggable Oracle Database (PDB)
  If you are downgrading Oracle Database, then you can downgrade one PDB without downgrading the whole CDB.
- Downgrading PDBs That Contain Oracle Application Express
  Use this procedure to avoid INVALID OBJECTS OWNED BY APEX_050000 errors when you downgrade PDBs that contain Oracle Application Express.
- Post-Downgrade Tasks for Oracle Database Downgrades
  After you downgrade your Oracle Database release, you can be required to complete additional tasks, due to changes that affect compatibility, components, and supported protocols.
- Troubleshooting the Downgrade of Oracle Database
  Use this troubleshooting information to address issues that may occur when downgrading Oracle Database.

### Supported Releases for Downgrading Oracle Database

You can downgrade both major releases and release update or patchset releases, based on the original Oracle Database release from which the database was upgraded.

#### Releases Supported for Downgrades

You can downgrade a non-CDB Oracle Database from Oracle Database 19c to Oracle Database 18c, Oracle Database 12c, and to Oracle Database 11g release 11.2.0.4.

You can downgrade a PDB or CDB to Oracle Database 18c, Oracle Database 12c Release 12.2, and Oracle Database 12c Release 12.1.0.2.

**Note:**

Starting with Oracle Database 12c, Release 1 (12.1), non-CDB architecture is deprecated. It can be desupported in a future release.

The following table provides additional information about releases supported for downgrading. When using this table, also read about compatibility in "Checking for Incompatibilities When Downgrading Oracle Database."

Table 8-1 Supported Releases and Editions for Downgrading

| Oracle Database Release or Edition | Downgradable (Yes/No) | Notes                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|:-----------------------------------|:----------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 18                                 | Yes                   | No additional information at this time.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| 12.2.0.1 and 12.1.0.2              | Yes                   | You cannot downgrade a database after you set the compatible initialization parameter to 12.1.0.2.<br>You can downgrade a non-CDB from 19 to 18, or 12.2 to 12.1.0.2, or 11.2.0.4 (all supported upgrade releases).<br>Install the latest Release Update, Release Revision, bundle patch or patch set update (BP or PSU) before you downgrade a CDB, or before you unplug and downgrade a PDB. Patches are available for download on My Oracle Support. Refer to My Oracle Support note 756671.1 to obtain the latest patch set.<br>You cannot downgrade to releases earlier than the minimum compatibility setting for the new Oracle Database release. |
| Oracle Enterprise Manager          | No                    | If you downgrade to an earlier supported release, then you must reconfigure Oracle Enterprise Manager controls.<br>Before you start your upgrade, you must use the `emdwgrd` utility to save DB Control files and data, so that you can restore Oracle Enterprise Manager Database Control (DB Control) after a downgrade.                                                                                                                                                                                                                                                                                                                               |
| Oracle Database Express Edition    | No                    | You cannot downgrade a database that is upgraded from Oracle Database Express Edition.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

#### Recommendations to Review Before Downgrading

The following recommendations for earlier supported releases affect downgrading for Oracle Database:

- Multitenant architecture provides architecture features for a multitenant container database (CDB), and pluggable databases (PDBs). If you are upgrading to multitenant architecture, and you set the compatible initialization parameter to the highest level after upgrading to this release, then you cannot downgrade the database after an upgrade.

- This release contains a new object privilege, `READ`, in addition to `SELECT`. After you downgrade, note the following implications of this object privilege:

  - If you have the `SELECT` and `READ` object privileges, then the `READ` privilege is removed.

  - If you previously only had the `READ` object privilege, then the `READ` object privilege is transformed into the `SELECT` object privilege.

  Refer to Oracle Database Security Guide for more information about the READ and SELECT object privileges.

- If Oracle XML DB is not installed in the database that you upgrade, then during a downgrade, Oracle XML DB is uninstalled. For example, if you did not install Oracle XML DB with Oracle Database 11g Release 2 (11.2), then Oracle XML DB is installed with Oracle Database 12c. If you downgrade the database, then Oracle XML DB is uninstalled as part of the downgrade. Oracle XML DB is included by default with Oracle Database 12c release 1 (12.1), and later releases.

- During upgrade to Oracle Database 12c, the Database (DB) Control repository is removed. If you downgrade to an earlier release, then you must reconfigure the Database (DB) Control to use it after the downgrade.

- Downgrade is not supported for Oracle Enterprise Manager. If you downgrade to an earlier supported release, then you must reconfigure Oracle Enterprise Manager controls.

**Related Topics**

- <https://support.oracle.com/rs?type=doc&id=756671.1>
- [Oracle Database Security Guide](../dbseg/configuring-privilege-and-role-authorization.md)

**Parent topic:** Downgrading Oracle Database to an Earlier Release

### Prepare to Downgrade a Standby Database with the Primary

If you are using an Oracle Data Guard Standby database, then review the procedure you can use to downgrade the standby database with the primary database

You can downgrade a database without breaking the standby database. To downgrade Oracle Database when a physical or logical standby database is present in the Oracle Data Guard configuration, use the procedure for your downgrade scenario as described in " Patching, Upgrading, and Downgrading Databases in an Oracle Data Guard Configuration" in Oracle Data Guard Concepts and Administration

**Related Topics**

- [Patching, Upgrading, and Downgrading Databases in an Oracle Data Guard Configuration](../sbydb/upgrading-patching-downgrading-oracle-data-guard-configuration.md)

**Parent topic:** Downgrading Oracle Database to an Earlier Release

### Check COMPATIBLE Parameter when Downgrading Oracle Database

If `COMPATIBLE` has been changed after the upgrade, then it is no longer possible to downgrade an Oracle Database.

If you have updated the `COMPATIBLE` parameter to set the compatibility level of your Oracle Database release to the current release, then you are not able to downgrade to an earlier release. This issue occurs because new releases have changes to the Data Dictionary, and can have other feature changes that prevent downgrades.

To check the `COMPATIBLE` parameter setting for your database before you downgrade, enter the following command:

    SQL> SELECT name, value, description FROM v$parameter WHERE name =
        ‘compatible’;

**Note:**

For Oracle ASM disk groups, if you changed the `compatible.asm` parameter after the upgrade to the upgraded release value, then when you downgrade to the earlier release, you cannot mount your Oracle ASM disk groups. The value for `compatible.asm` sets the minimum Oracle ASM release that can mount a disk group.

As part of your downgrade, you must create a new disk group to your downgraded release level, and restore data to that downgraded compatibility ASM disk group.

**Parent topic:** Downgrading Oracle Database to an Earlier Release

### Perform a Full Backup Before Downgrading Oracle Database

Oracle strongly recommends that you perform a full backup of your new Oracle Database release before you downgrade to a supported earlier release.

If time does not allow for you to complete a full level 0 backup, then at least complete a level 1 backup.

**Related Topics**

- [Backing Up the Database in Oracle Database Backup and Recovery User’s Guide](../bradv/backing-up-database.md)

**Parent topic:** Downgrading Oracle Database to an Earlier Release

### Performing Required Predowngrade Steps for Oracle Database

Complete the required preparation steps described here before you downgrade Oracle Database to the earlier release from which you upgraded.

Before you start a downgrade, you must resolve incompatibilities between database releases. For example, determine if you must disable components in the database before you start the downgrade.

1.  If you have enabled Oracle Database Vault on your database, then disable Oracle Database Vault before downgrading the database.

    Use DBA_DV_STATUS to find out if Oracle Database Vault is enabled:

        SQL> SELECT * FROM DBA_DV_STATUS;

    If the output is `TRUE`, then Oracle Database Vault is enabled, so you must disable it.

    On multitenant architecture Oracle Database systems, use `CDB_DV_STATUS` on `CDB$ROOT` to find out the Oracle Database Vault status on all PDBs plugged in to the CDB:

        SQL> SELECT * FROM CDB_DV_STATUS;

2.  If you have enabled Unified Auditing, then you can choose to back up and purge the unified audit trail:

    1.  Find if unified audit records exist.

            SQL> SELECT COUNT(*) FROM UNIFIED_AUDIT_TRAIL;

    2.  Back up the existing audit data to a table. For example:

            SQL> CREATE TABLE UA_DATA AS (SELECT * FROM UNIFIED_AUDIT_TRAIL);

    3.  Clean up the audit trail.

            EXEC DBMS_AUDIT_MGMT.CLEAN_AUDIT_TRAIL(audit_trail_type => DBMS_AUDIT_MGMT.AUDIT_TRAIL_UNIFIED, use_last_arch_timestamp => FALSE);

3.  Before downgrade, ensure that the target Oracle home for the downgraded database contains the version of the time zone file that your database is using.

    To find which time zone file version your database is currently using, query `V$TIMEZONE_FILE` using the following command:

        SQL> select * from  V$TIMEZONE_FILE;

    For example:

    If the query returns `timezlrg_20.dat` in the column `V$TIMEZONE_FILE.FILENAME`, then check if the file is present in the target Oracle Home:

    Linux and Unix

        $ORACLE_HOME/oracore/zoneinfo/timezlrg_20.dat

    Windows

        %ORACLE_HOME%\oracore\zoneinfo\timezlrg_20.dat

    If the required time zone file is missing from the target Oracle home, then do one of the following:

    - If you installed the current version of the time zone file as a patch, and you still know the patch number, then use the same patch number to download the corresponding time zone file for the target release from the My Oracle Support website.

    - Locate the correct patch by using the My Oracle Support website patch search function. Enter the following search criteria: "Product is 'Oracle Database'", "Release is 'target release'", and "Description contains 'DST'".

    - If you cannot locate the patch on the My Oracle Support website, then log a service request with Oracle Support.

    After you find and download the required patch, install it in the target Oracle home.

4.  If you created objects based on fixed objects, then drop these objects to avoid possible `ORA-00600` errors. You can recreate these objects after the downgrade.

5.  If you have Oracle Enterprise Manager configured in your database, then drop the Enterprise Manager user:

        DROP USER sysman CASCADE;

    **Note:**

    After you drop the Enterprise Manager user, you can find that `MGMT*` synonyms are invalid. You must reconfigure Oracle Enterprise Manager to use any Oracle Enterprise Manager controls in the downgraded database.

**Related Topics**

- [Oracle Database Globalization Support Guide](../nlspg/datetime-data-types-and-time-zone-support.md)

**Parent topic:** Downgrading Oracle Database to an Earlier Release

### Using Scripts to Downgrade a CDB or Non-CDB Oracle Database

To automate downgrades, starting in Oracle Database 19c, Oracle provides the `dbdowngrade` utility script. When necessary, you can also continue to run `catdwgrd.sql` manually, as in previous releases.

- Using Dbdowngrade to Downgrade CDB and Non-CDB Oracle Databases
  To downgrade to a previous database release, Oracle recommends that you run the downgrade script `dbdowngrade`.
- Downgrading a CDB or Non-CDB Oracle Database Manually with catdwgrd.sql
  You can run the manual `catdwgrd.sql` script for downgrades of Oracle Database to an earlier supported major release, or an earlier release update, where you either prefer to run a manual script, or you want to avoid excessive thread issues.

**Parent topic:** Downgrading Oracle Database to an Earlier Release

#### Using Dbdowngrade to Downgrade CDB and Non-CDB Oracle Databases

To downgrade to a previous database release, Oracle recommends that you run the downgrade script `dbdowngrade`.

Starting with Oracle Database 19c, Oracle provides the Downgrade Utility script `dbdowngrade`. When you use the dbdowngrade utility, it sets appropriate values for the downgrade, and simplifies how you start a downgrade. Specifically, it ensures that the underlying calls to `catcon.pl` use recommended values, so that potential errors due to excessive threads being spawned are reduced. This feature is especially of value for downgrades of multitenant architecture (CDB) databases. If you prefer to be in control of the number of resources used for a downgrade, then you can run the `catdwgrd.sql` script manually, as in previous releases. After you downgrade to the earlier database release, you can then appy any release update to that earlier release.

The `dbdowngrade` shell command is located in the file path `$ORACLE_HOME/bin` on Linux and Unix, and `%ORACLE_HOME%\bin` on Microsoft Windows based systems. If you are downgrading a CDB, then you can provide the inclusion list as argument to the script.

When you downgrade multitenant architecture databases (CDBs), the `dbdowngrade` script has two behaviors, depending on whether you use an inclusion list.

- Without an inclusion list. The downgrade runs on all the containers that are open in the CDB (PDB and CDB).

  Run the downgrade without an inclusion list when you want to downgrade the entire CDB. In this scenario, all open containers are downgraded. You must open all the PDBs in the CDB manually before you start the `dbdowngrade` script.

- With an inclusion list. The downgrade runs only on the PDBs within the inclusion list, and CDB\$ROOT is not downgraded during the downgrade operation.

  Run the downgrade with an inclusion list when you want to downgrade only the set of PDBs listed in the inclusion list. In this scenario, where you want to use unplug and plug upgrades, only the set of PDBs that you list in the inclusion list are downgraded. The CDB and the PDBs that are not on the inclusion list remain upgraded to the later release.

Prerequisites:

- If you are downgrading from Oracle Database 19c to Oracle Database 18c, Oracle Database 12.2, or Oracle Database 12.1, then you can downgrade all databases in a multitenant container database (CDB), or one pluggable database (PDB) within a CDB. Oracle Database releases earlier than Oracle Database 12c did not use multitenant architecture.

- If you are downgrading without an inclusion list, then you must open all PDB containers before you run the `dbdowngrade` script.

1.  Log in to the system as the owner of the Oracle Database Oracle home directory.
2.  Set the `ORACLE_HOME` environment variable to the Oracle home of the upgraded Oracle Database release that you want to downgrade.
3.  Set the `ORACLE_SID` environment variable to the system identifier (SID) of the Oracle Database that you want to downgrade.
    **Note:**

    If you are downgrading a cluster database, then shut down the database completely, and change the value for the initialization parameter `CLUSTER_DATABASE` to `FALSE`. After the downgrade, set this parameter back to `TRUE`.
4.  Using SQL\*Plus, connect to the database instance that you want to downgrade as a user with `SYSDBA` privileges:
        sqlplus sys as sysdba
        Enter password: password
5.  Start the instance in downgrade mode by issuing the following SQL\*Plus command for your Oracle Database instance type. In case of errors during startup, you can be required to use the `PFILE` option to specify the location of your initialization parameter file.
    - Non-CDB instances:

          SQL> startup downgrade pfile=pfile_name

    - CDB instances:

          SQL> startup downgrade pfile=pfile_name
          SQL> alter pluggable database all open downgrade;

    Specify the location of your initialization parameter file `PFILE`.

    **See Also:**

    [Oracle Database Administrator’s Guide](../admin/starting-up-and-shutting-down.md) for information about specifying initialization parameters at startup and the initialization parameter file
6.  Start the `dbdowngrade` script, either with default values, or with an inclusion list.
    If you use an inclusion list, then `CDB$ROOT` must not be on your inclusion list.

    For example:

    `Running with default values`
    Linux and Unix

        $cd $ORACLE_HOME/bin
        $./dbdowngrade

    Microsoft Windows

        $cd %ORACLE_HOME%\bin
        $dbdowngrade.cmd

    `Running with inclusion list for CDB`
    Linux and Unix

        $cd $ORACLE_HOME/bin
        $./dbdowngrade –c 'PDB1 PDB2 PDBN'

    Microsoft Windows

        $cd %ORACLE_HOME%\bin
        $dbdowngrade.cmd –c "PDB1 PDB2 PDBN"

    After the `dbdowngrade` script (which starts `catdwgrd.sql`) finishes running, shut down the database in the higher version Oracle home.
7.  Change the following environment variables to point to the directories of the release to which you are downgrading:
    - `ORACLE_HOME`
    - `PATH`

    Also check that your `oratab` file, and any client scripts that set the value of `ORACLE_HOME`, point to the downgraded Oracle home.

    To finish the downgrade, you run downgrade reload in the lower version Oracle home.
8.  Start up the database in the lower version Oracle home in Upgrade mode. Run `catrelod.sql` on non-CDB databases, or use `catcon.pl` to run `catrelod.sql` on CDB databases.
    - For a non-CDB:

          SQL> $ORACLE_HOME/rdbms/admin/catrelod.sql

    - For a CDB:

          $ORACLE_HOME/perl/bin/perl $ORACLE_HOME/rdbms/admin/catcon.pl -e -n 1 -b catrelod -d $ORACLE_HOME/rdbms/admin catrelod.sql

    This command reloads the appropriate version for each of the database components in the downgraded database.

As a result of running the `dbdowngrade` script, the utility runs `catdwgrd` and `catcon.pl`. These scripts perform the downgrade, using the recommended values for the release to which you are downgrading. The log files produced by the downgrade scripts are placed under the first directory found of one of these three options, in order:

- The Oracle base home identified by the `orabasehome` command

- The Oracle base home identified by the `orabase` command

- The Oracle home identified by the `oracle_home` command

For example:

    $ $ORACLE_HOME/bin/orabasehome
    /u01/app/oracle/product/19.0.0/dbhome_1

In this example, the \$ORACLE_BASE directory is ` /u01/app/oracle/product/19.0.0/dbhome_1`, and the logs are located in `/u01/app/oracle/product/19.0.0/dbhome_1/cfgtoollogs/downgrade`. In the directory, the log files are prefixed with the string `catdwgrd`.

**Note:**

- Read-write Oracle homes: the commands `orabaseconfig` and `orabasehome` both return the environment setting for ORACLE_HOME.

- Read-only Oracle homes: the command `orabaseconfig` returns the read-only path configuration for the Oracle base in the path `$ORACLE_BASE/homes`.

**Parent topic:** Using Scripts to Downgrade a CDB or Non-CDB Oracle Database

#### Downgrading a CDB or Non-CDB Oracle Database Manually with catdwgrd.sql

You can run the manual `catdwgrd.sql` script for downgrades of Oracle Database to an earlier supported major release, or an earlier release update, where you either prefer to run a manual script, or you want to avoid excessive thread issues.

If you are downgrading from Oracle Database 19c to Oracle Database 18c, Oracle Database 12.2, or Oracle Database 12.1, then you can downgrade all databases in a multitenant container database (CDB), or one pluggable database (PDB) within a CDB. Oracle Database releases earlier than Oracle Database 12c did not use multitenant architecture.

**Note:**

Starting with Oracle Database 12c release 1 (12.1), non-CDB architecture was deprecated. It is desupported in releases after Oracle Database 19c.

1.  Log in to the system as the owner of the Oracle Database Oracle home directory.
2.  Set the `ORACLE_HOME` environment variable to the Oracle home of the upgraded Oracle Database release.
3.  Set the `ORACLE_SID` environment variable to the system identifier (SID) of the Oracle Database that you want to downgrade.
4.  At a system prompt, change to the directory `ORACLE_HOME``/rdbms/admin`, where `ORACLE_HOME` is the Oracle home on your system.
    **Note:**

    If you are downgrading a cluster database, then shut down the database completely, and change the value for the initialization parameter `CLUSTER_DATABASE` to `FALSE`. After the downgrade, set this parameter back to `TRUE`.
5.  Using SQL\*Plus, connect to the database instance that you want to downgrade as a user with `SYSDBA` privileges:
        sqlplus sys as sysdba
        Enter password: password
6.  Start the instance in downgrade mode by issuing the following SQL\*Plus command for your Oracle Database instance type. In case of errors during startup, you can be required to use the `PFILE` option to specify the location of your initialization parameter file.
    - Non-CDB instances:

          SQL> startup downgrade pfile=pfile_name

    - CDB instances:

          SQL> startup downgrade pfile=pfile_name
          SQL> alter pluggable database all open downgrade;

    Specify the location of your initialization parameter file `PFILE`.

    **See Also:**

    [Oracle Database Administrator’s Guide](../admin/starting-up-and-shutting-down.md) for information about specifying initialization parameters at startup and the initialization parameter file
7.  (Recommended) If you are downgrading a non-CDB, then Oracle recommends that you set the system to spool results to a log file, so that you can track the changes and issues.
    If you are downgrading a CDB, then you do not need to perform this step. CDBs automatically spool output to the `catcon_logs`.

    On a non-CDB, enter the following command to spool results to a log file, where `downgrade.log` is the name of the log file:

        set echo on termout on serveroutput on timing on
        SQL> SPOOL downgrade.log
8.  Use the following command to start the downgrade, depending on your configuration:
    - Non-CDB:

          SQL> @catdwgrd.sql

    - CDB:

          $ORACLE_HOME/perl/bin/perl $ORACLE_HOME/rdbms/admin/catcon.pl -d $ORACLE_HOME/rdbms/admin -e -b catdwgrd -l output directory -r catdwgrd.sql

    In the CDB example, `catdwgrd.sql` is run on containers using `catcon.pl`. To run commands with the `catcon.pl` utility, you first start Perl. The `-d` parameter tells `catcon.pl` where to find `catdwgrd`. The `-l` parameter specifies the output directory for log files (instead of writing to the `rdbms/admin` directory). Specifying the `-r` parameter causes `catdwgrd` to run first on the PDBs, and second on CDB_ROOT.

    Run `catdwgrd` using the `-r` parameter when you downgrade a CDB. The `–r` parameter changes the default order that scripts are run, so that scripts run in all PDBs, and then in CDB_ROOT.

    **Note:**

    - Use the version of the `catdwgrd.sql` script included with your new Oracle Database release.
    - Run `catdwgrd` using the `-r` parameter when downgrading a CDB.
    - Run `catdwgrd.sql` in the new Oracle Database release environment.
    - The `catdwgrd.sql` script downgrades all Oracle Database components in the database to the release from which you upgraded. The downgrade is either to the supported major release from which you upgraded, or to the patch release from which you upgraded.

    If you are downgrading a multitenant environment database, and the `catdwgrd.sql` command encounters a failure, then review the error message. Check to see what issues are present in the `CDB$ROOT` or PDBs before proceeding. Check the section "Troubleshooting the Downgrade of Oracle Database." Fix the issues as stated in the errors. After you resolve the errors, rerun `catdgwrd.sq` with the `catcon.pl` utility, using the syntax `catcon.pl -c 'cdb,pdb' -r`.

    **Caution:**

    If the downgrade for a component fails, then an `ORA-39709` error is displayed. The SQL\*Plus session terminates without downgrading the Oracle Database data dictionary. All components must be successfully downgraded before the Oracle Database data dictionary is downgraded. Identify and fix the problem before rerunning the `catdwgrd.sql` script.
9.  For Non-CDB only, if you turned the spool on, then turn off the spooling of script results to the log file:
        SQL> SPOOL OFF

    Check the spool file, and verify that no errors occurred during the downgrade. You named the spool file in Step 8, and the suggested name was `downgrade.log`. Correct any problems that you find in this file. If necessary, rerun the downgrade script.

    **Note:**

    Save the results from the first time you ran the downgrade script. Before you rerun the downgrade script, rename the file `downgrade.log` to a different name, so that it is not overwritten when you rerun the script.
10. Shut down the instance:
        SQL> SHUTDOWN IMMEDIATE
11. Exit SQL\*Plus.
12. If your operating system is Linux or Unix, then change the following environment variables to point to the directories of the release to which you are downgrading:
    - Linux and UNIX systems

      Change the following environment variables to point to the directories of the release to which you are downgrading:

      - `ORACLE_HOME`

      - `PATH`

      Also check that your `oratab` file, and any client scripts that set the value of `ORACLE_HOME`, point to the downgraded Oracle home.

      **See Also:**

      [Oracle Database Installation Guide](../install-and-upgrade.md) for your operating system for information about setting other important environment variables on your operating system

    - Microsoft Windows systems

      1.  Stop all Oracle services, including the `OracleService``SID` Oracle service of the Oracle Database 12c database, where `SID` is the instance name.

          For example, if your SID is `ORCL`, then enter the following at a command prompt:

              C:\> NET STOP OracleServiceORCL

          **See Also:**

          [Oracle Database Administrator’s Reference for Microsoft Windows](../ntqrf/stopping-oracle-database-services.md) for more information about stopping Oracle services on Windows

      2.  Delete the Oracle service at a command prompt by issuing the command `ORADIM`.

          For example, if your SID is `ORCL`, then enter the following command:

              C:\> ORADIM -DELETE -SID ORCL

          Create the Oracle service of the database that you are downgrading at a command prompt using the command `ORADIM`:

              C:\> ORADIM -NEW -SID SID -INTPWD PASSWORD -MAXUSERS USERS
              -STARTMODE MANUAL -PFILE ORACLE_HOME\DATABASE\INITSID.ORA

          The syntax for `ORADIM` includes the following variables:

          | Variable    | Description                                                                                                                                                                                                                                                                                                                                                                                      |
          |:------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
          | SID         | Same system identifier (SID) name as the SID of the database being downgraded.                                                                                                                                                                                                                                                                                                                   |
          | PASSWORD    | Password for the database instance. This password is the password for the user connected with `SYSDBA` privileges. The `-INTPWD` option is not required. If you are prompted for a password, then use the password for the standard user account for this Windows platform.                                                                                                                      |
          | USERS       | Maximum number of users that can be granted `SYSDBA` and `SYSOPER` privileges.                                                                                                                                                                                                                                                                                                                   |
          | ORACLE_HOME | Oracle home directory of the database to which you are downgrading. Ensure that you specify the full path name with the option `-PFILE`, including the drive letter where the Oracle home directory is mounted.<br>See Oracle Database Administrator’s Guide for information about specifying initialization parameters at startup, and for information about the initialization parameter file. |

          For example, if your SID is `ORCL`, your PASSWORD is `TWxy5791`, the maximum number of USERS is `10`, and the ORACLE_HOME directory is `C:\ORANT`, then enter the following command:

              C:\> ORADIM -NEW -SID ORCL -INTPWD TWxy5791 -MAXUSERS 10
                   -STARTMODE AUTO -PFILE C:\ORANT\DATABASE\INITORCL.ORA

          **Note:**

          The `ORADIM` command prompts you for the password for the Oracle home user account. You can specify other options using `ORADIM`.

          You are not required to change any Windows Registry settings when downgrading a database. The `ORADIM` utility makes all necessary changes automatically.

          **See Also:**

          [Oracle Database Administrator’s Reference for Microsoft Windows](../ntqrf/about-administering-an-oracle-database-instance-using-oradim.md) for information about administering an Oracle Database instance using `ORADIM`
13. Restore the configuration files (for example, parameter files, password files, and so on) of the release to which you are downgrading.
    If the database is an Oracle RAC database, then run the following command to return the database to single instance mode:

        SET CLUSTER_DATABASE=FALSE

    **Note:**

    If you are downgrading a cluster database, then perform this step on all nodes on which this cluster database has instances configured. Set the value for the initialization parameter `CLUSTER_DATABASE` to `FALSE`. After the downgrade, set this initialization parameter back to `TRUE`.

    **See Also:**

    [Oracle Real Application Clusters Administration and Deployment Guide](../racad/administering-database-instances-and-cluster-databases.md) for information about initialization parameter use in Oracle RAC
14. At a system prompt, change to the `admin` directory in the Oracle home directory of the earlier release to which you are downgrading. (`ORACLE_HOME``/rdbms/admin`, where `ORACLE_HOME` is the path to the earlier release Oracle home.)
15. Start SQL\*Plus, and connect to the database instance as a user with SYSDBA privileges.
    - For a non-CDB:

          SQL> CONNECT / AS SYSDBA
          SQL> STARTUP UPGRADE

    - For a CDB:

          connect / as sysdba
          startup upgrade;
          alter pluggable database all open upgrade;
16. (Optional) For a non-CDB, set the system to spool results to a log file to track changes and issues. This step is not needed for a CDB.
        SQL> SPOOL reload.log
17. Run `catrelod.sql` on non-CDB databases, or use `catcon.pl` to run `catrelod.sql` on CDB databases.
    - For a non-CDB:

          SQL> $ORACLE_HOME/rdbms/admin/catrelod.sql

    - For a CDB:

           $ORACLE_HOME/perl/bin/perl $ORACLE_HOME/rdbms/admin/catcon.pl -n 1 -e -b catrelod -d $ORACLE_HOME/rdbms/admin catrelod.sql

    This command reloads the appropriate version for each of the database components in the downgraded database.
18. If you turned on spooling for a non-CDB, then turn off the spooling of script results to the log file:
        SQL> SPOOL OFF

    Check the spool file, and verify that the packages and procedures compiled successfully. Correct any problems that you find in this log file, and rerun the appropriate script, if necessary.
19. Shut down and restart the instance for normal operation:
        SQL> SHUTDOWN IMMEDIATE
        SQL> STARTUP

    You can be required to use the option`PFILE` to specify the location of your initialization parameter file.

    **See Also:**

    [Oracle Database Administrator’s Guide](../admin/starting-up-and-shutting-down.md) for information about specifying initialization parameters at startup, and in the initialization parameter file
20. If you configured your database to use Oracle Label Security, then complete this step. If you did not configure your database to use Oracle Label Security, then proceed to the next step.
    1.  Copy the script `olstrig.sql` from the Oracle home under Oracle Database 12c to the Oracle home of the release number to which you are downgrading the database.
    2.  From the Oracle home of the downgrade release, run `olstrig.sql` to recreate DML triggers on tables with Oracle Label Security policies:
            SQL> @olstrig.sql
21. (Optional) For a non-CDB, set the system to spool results to a log file to track changes and issues. This step is not needed for a CDB.
    Example:

        SQL> SPOOL utlrp.log
22. Run the `utlrp.sql` script to recompile any remaining stored PL/SQL and Java code. Use the procedure for your configuration:
    - non-CDB:

          SQL> $ORACLE_HOME/rdbms/admin/utlrp.sql

    - CDB:

          $ORACLE_HOME/perl/bin/perl $ORACLE_HOME/rdbms/admin/catcon.pl -n 1 -e -b utlrp -d $ORACLE_HOME/rdbms/admin utlrp.sql

      The `utlrp.sql` script recompiles all existing PL/SQL modules previously in `INVALID` state, such as packages, procedures, types, and so on. The log file `utlrp0.log` is generated. That log file lists the recompilation results.
23. If you turn on spooling for a non-CDB when you run `utlrp.sql`, then turn off the spooling of script results to the log file:
        SQL> SPOOL OFF

    Check the spool file, and verify that the packages and procedures compiled successfully. Correct any problems that you find in this log file. If necessary, rerun the appropriate script.
24. Exit SQL\*Plus.

At the completion of this procedure, your database is downgraded.

**Related Topics**

- Troubleshooting the Downgrade of Oracle Database
- [Oracle Database Administrator’s Guide](../admin/starting-up-and-shutting-down.md)

**Parent topic:** Using Scripts to Downgrade a CDB or Non-CDB Oracle Database

### Downgrading a Single Pluggable Oracle Database (PDB)

If you are downgrading Oracle Database, then you can downgrade one PDB without downgrading the whole CDB.

In Oracle Database releases later than Oracle Database 12c release 2 (12.2), you can downgrade individual PDBs. For example, you can unplug a PDB from an upgraded CDB, downgrade the PDB, and then plug it in to an earlier release CDB, or you can convert the PDB database to a standalone database.

#### Downgrade the PDB

In this procedure example, you downgrade the PDB to release 12.1.0.2:

1.  Start up the PDB in DOWNGRADE mode. The CDB can be in normal mode when you do this.

        SQL> alter pluggable database CDB1_PDB1 open downgrade;

2.  Downgrade the PDB, either by using the `dbdowngrade` utility, or by running `catdwgrd` manually, using `catcon.pl`.

    In each of these options, the PDB that you are downgrading is `PDB1`.

    - Downgrading with `dbdowngrade` utility.

      Downgrade the PDB using the dbdowngrade script as follows:

          cd $ORACLE_HOME/bin
          ./dbdowngrade -c 'PDB1'

    - Manually downgrading with `catdwgrd`, using `catcon.p.`

      Run `catdwgrd` as follows:

          $ORACLE_HOME/perl/bin/perl $ORACLE_HOME/rdbms/admin/catcon.pl -d
           $ORACLE_HOME/rdbms/admin -n 1 -l <output directory> -e -b catdwgrd -c 'PDB1'
           catdwgrd.sql

      In the example, `catdwgrd` is run with `catcon.pl`. The `-d` parameter tells `catcon.pl` where to find `catdwgrd`. The `-l` parameter specifies the output directory for log files, instead of writing to the `rdbms/admin` directory). You must use the `-r` parameter to run the two scripts together at the same time.

      The log files for the downgrade are placed in the Oracle base home (the Oracle base identified by the commands `orabasehome`, or `orabase`, or the Oracle home identified by the command `oracle_home`, in that order.

3.  Close the PDB.

#### Unplug the PDB from the CDB

In this step you unplug the downgraded PDB from the release 12.2.0.1 CDB:

1.  Connect to the upgraded CDB.

2.  Close the PDB that you want to unplug.

        SQL> alter pluggable database PDB1 close;

3.  Unplug the downgraded 12.1.0.2 PDB, replacing the variable `path` with the path on your system:

        SQL> alter pluggable database PDB1 unplug into 'path/pdb1.xml';

    You receive the following response when the unplug is completed:

        Pluggable database altered

#### Plug in the Downgraded 12.1.0.2 PDB

In this step you plug the downgraded 12.1.0.2 PDB into the 12.1.0.2 CDB. To do this, you must create the PDB in this CDB. The following example shows how to create a pluggable database called PDB1:

1.  Connect to the 12.1.0.2 CDB.

2.  Plug in the 12.1.0.2 PDB.

        SQL> create pluggable database PDB1 using 'path/pdb1.xml';

    This command returns `Pluggable database created`.

3.  Open the PDB in upgrade mode:

        SQL> alter pluggable database PDB1 open upgrade;

4.  Connect to the PDB:

        SQL> alter session set container=PDB1;

5.  Run `catrelod` in the PDB:

        SQL> @$ORACLE_HOME/rdbms/admin/catrelod.sql

    The `catrelod.sql` script reloads the appropriate version for each of the database components in the downgraded database.

6.  Run `utlrp` in the PDB:

        SQL> @$ORACLE_HOME/rdbms/admin/utlrp.sql

    The `utlrp.sql` script recompiles all existing PL/SQL modules that were previously in an `INVALID` state, such as packages, procedures, types, and so on.

**Parent topic:** Downgrading Oracle Database to an Earlier Release

### Downgrading PDBs That Contain Oracle Application Express

Use this procedure to avoid INVALID OBJECTS OWNED BY APEX_050000 errors when you downgrade PDBs that contain Oracle Application Express.

After you downgrade the PDB to an earlier release, enter a SQL statement similar to the following to drop the Oracle Application Express user:

    $ORACLE_HOME/perl/bin/perl $ORACLE_HOME/rdbms/admin/catcon.pl -b drop_apex5
    -c 'PDB1' -- --x'drop user apex_050000 cascade'

In this example, the PDB name is `'PDB1'`.

**Parent topic:** Downgrading Oracle Database to an Earlier Release

### Post-Downgrade Tasks for Oracle Database Downgrades

After you downgrade your Oracle Database release, you can be required to complete additional tasks, due to changes that affect compatibility, components, and supported protocols.

- Reapply Release Update and Other Patches After Downgrade
  After the downgrade is run, and `catrelod.sql` completes successfully, if you installed new patches in your original Oracle home after the upgrade, but before the downgrade, then ensure that you apply any patches that you installed.
- Reenabling Oracle RAC After Downgrading Oracle Database
  After the downgrade, you can re-enable Oracle Real Application Clusters (Oracle RAC).
- Reenabling Oracle Database Vault after Downgrading Oracle Database
  You must do this if you are instructed during the downgrade to disable Oracle Database Vault.
- Downgrade the Oracle Grid Infrastructure Configuration for the Database
  \After a downgrade you must change the Oracle Grid Infrastructure registration to start the database release in the earlier release Oracle Database home.
- Restoring Oracle Enterprise Manager after Downgrading Oracle Database
  The restore task described in this section is required only if you are performing a downgrade, and Oracle Enterprise Manager is configured on the host.
- Restoring Oracle APEX to the Earlier Release
  After a downgrade, if you upgraded Oracle APEX (formerly Oracle Application Express) at the same time as you upgraded Oracle Database, then you must complete steps to revert to the earlier release.
- Gathering Dictionary Statistics After Downgrading
  To help to assure good performance after you downgrade, use this procedure to gather dictionary statistics.
- Regathering Fixed Object Statistics After Downgrading
  After the downgrade, run representative workloads on Oracle Database, and regather fixed object statistics.
- Regathering Stale CBO Statistics After Downgrade
  Oracle recommends that you regather Oracle Cost-Based Optimizer (CBO) statistics after completing an Oracle Database downgrade.
- Checking Validity of Registry Components After Downgrade
  Check the validity of registry components and identify any invalid components.

**Parent topic:** Downgrading Oracle Database to an Earlier Release

#### Reapply Release Update and Other Patches After Downgrade

After the downgrade is run, and `catrelod.sql` completes successfully, if you installed new patches in your original Oracle home after the upgrade, but before the downgrade, then ensure that you apply any patches that you installed.

If you installed new patches, then run the `datapatch` tool to apply those patches to the downgraded database. If you did not change the binaries and files in your Oracle Home after the upgrade, then there is no need to run `datapatch` after running `catrelod.sql`. However, if you are in any doubt about whether new patches are installed, then run `datapatch`. There is no safety concern that prevents you from running `datapatch` as many times as you require to be certain that patches are applied to the database.

**Parent topic:** Post-Downgrade Tasks for Oracle Database Downgrades

#### Reenabling Oracle RAC After Downgrading Oracle Database

After the downgrade, you can re-enable Oracle Real Application Clusters (Oracle RAC).

For downgrades with Oracle RAC databases, where you set `CLUSTER_DATABASE=FALSE` for the downgrade, you can now set `CLUSTER_DATABASE=TRUE` again and start with all instances in the RAC cluster.

**Parent topic:** Post-Downgrade Tasks for Oracle Database Downgrades

#### Reenabling Oracle Database Vault after Downgrading Oracle Database

You must do this if you are instructed during the downgrade to disable Oracle Database Vault.

If you use Oracle Database Vault, then you may have been instructed to disable it before downgrading your databaseTo use Oracle Database Vault after downgrading, you must register it to reenable it.

**Related Topics**

- [Registering Oracle Database Vault](../dvadm/getting-started-with-oracle-database-vault.md)

**Parent topic:** Post-Downgrade Tasks for Oracle Database Downgrades

#### Downgrade the Oracle Grid Infrastructure Configuration for the Database

\After a downgrade you must change the Oracle Grid Infrastructure registration to start the database release in the earlier release Oracle Database home.

Later release Oracle Grid Infrastructure can run earlier Oracle Database releases. Oracle does not recommend that you downgrade Oracle Grid Infrastructure, unless you encounter an issue related specifically to Oracle Grid Infrastructure. However, after you downgrade your Oracle Databaes release, you must use the command `srvctl downgrade database` to configure Oracle Clusterware to start the database in the earlier release Oracle home.

To configure Oracle Clusterware to start the database in the earlier release Oracle home, use the following command syntax, where `$LATER_RELEASE_ORACLE_HOME` is the path (or environment variable) to the later release Oracle home, `old_release_oracle_home` is the path to the earlier release Oracle home, and `old-release` is the earlier release Oracle Database release:

    $LATER_RELEASE_ORACLE_HOME/bin/srvctl downgrade database -d $ORACLE_UNQNAME -o old_release_oracle_home -t old-release

For example:

    $ORACLE_HOME/bin/srvctl downgrade database -d $ORACLE_UNQNAME -o /u02/app/oracle/product/12.2/db_1/ -t 12.2.0.4

**Parent topic:** Post-Downgrade Tasks for Oracle Database Downgrades

#### Restoring Oracle Enterprise Manager after Downgrading Oracle Database

The restore task described in this section is required only if you are performing a downgrade, and Oracle Enterprise Manager is configured on the host.

To restore Oracle Enterprise Manager, you first run Oracle Enterprise Manager configuration assistant (EMCA), and then you run the `emdwgrd` utility.

- Requirements for Restoring Oracle Enterprise Manager After Downgrading
  You must complete these requirements before you upgrade to be able to restore Oracle Enterprise Manager after a downgrade to a release earlier than 12.1
- Running EMCA to Restore Oracle Enterprise Manager After Downgrading
  Review these topics and select your restoration scenario to restore Oracle Enterprise Manager after a downgrade.
- Running the emdwgrd utility to restore Enterprise Manager Database Control
  You can restore the Oracle Enterprise Manager Database Control and data by using the `emdwgrd` utility after you run `emca -restore`.

**Parent topic:** Post-Downgrade Tasks for Oracle Database Downgrades

##### Requirements for Restoring Oracle Enterprise Manager After Downgrading

You must complete these requirements before you upgrade to be able to restore Oracle Enterprise Manager after a downgrade to a release earlier than 12.1

The following must be true to use `emca -restore` to restore Oracle Enterprise Manager to its previous state:

- Before the upgrade, you saved a backup of your Oracle Enterprise Manager configuration files and data

- You run the `emca` binary located in the new Oracle Database release home for this procedure

On Oracle Clusterware systems, to restore Oracle Enterprise Manager on an Oracle RAC database, you must have the database registered using `srvctl` before you run `emca -restore`. You must run `emca -restore` from the `ORACLE_HOME``/bin` directory of the earlier Oracle Database release to which the database is being downgraded.

Run the `emca -restore` command with the appropriate options to restore Oracle Enterprise Manager Database Control or Grid Control to the old Oracle home.

Specify different `emca` options, depending on whether the database you want to downgrade is a single-instance database, an Oracle RAC database, or an Oracle ASM database.

**Related Topics**

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/server-control-command-reference.md)

**Parent topic:** Restoring Oracle Enterprise Manager after Downgrading Oracle Database

##### Running EMCA to Restore Oracle Enterprise Manager After Downgrading

Review these topics and select your restoration scenario to restore Oracle Enterprise Manager after a downgrade.

- Running emca on a Single-Instance Oracle Database Without Oracle ASM
  Use Enterprise Manager Configuration Assistant (`emca`) to manage your database.
- Running EMCA on an Oracle RAC Database Without Oracle ASM
  Use Enterprise Manager Configuration Assistant (`emca`) to manage your database:
- Running EMCA on a Single-Instance Oracle ASM Instance
  Use Enterprise Manager Configuration Assistant (`emca`) to manage your database and storage.
- Running emca on an Oracle ASM on Oracle RAC Instance
  Use Enterprise Manager Configuration Assistant (`emca`) to manage your database and storage.
- Running emca on a Single-Instance Oracle Database With Oracle ASM
  Use Enterprise Manager Configuration Assistant (`emca`) to manage your database and storage.
- Running emca on an Oracle RAC Database and Oracle ASM Instance
  Use Enterprise Manager Configuration Assistant (`emca`) to manage your database and storage.

**Parent topic:** Restoring Oracle Enterprise Manager after Downgrading Oracle Database

###### Running emca on a Single-Instance Oracle Database Without Oracle ASM

Use Enterprise Manager Configuration Assistant (`emca`) to manage your database.

Use this command to run Enterprise Manager Configuration Assistant.

    ORACLE_HOME/bin/emca -restore db

You are prompted to enter the following information:

- Oracle home for the database that you want to restore

- Database SID

- Listener port number

**Parent topic:** Running EMCA to Restore Oracle Enterprise Manager After Downgrading

###### Running EMCA on an Oracle RAC Database Without Oracle ASM

Use Enterprise Manager Configuration Assistant (`emca`) to manage your database:

Use this procedure to run Enterprise Manager Configuration Assistant:

    ORACLE_HOME/bin/emca -restore db -cluster

You are prompted to enter the following information:

- Oracle home for the database that you want to restore

- Database unique name

- Listener port number

**Parent topic:** Running EMCA to Restore Oracle Enterprise Manager After Downgrading

###### Running EMCA on a Single-Instance Oracle ASM Instance

Use Enterprise Manager Configuration Assistant (`emca`) to manage your database and storage.

Use this command to run Enterprise Manager Configuration Assistant.

    ORACLE_HOME/bin/emca -restore asm

You are prompted to enter the following information:

- Oracle home for the database that you want to restore

- Oracle ASM port

- Oracle ASM SID

**Parent topic:** Running EMCA to Restore Oracle Enterprise Manager After Downgrading

###### Running emca on an Oracle ASM on Oracle RAC Instance

Use Enterprise Manager Configuration Assistant (`emca`) to manage your database and storage.

Use this command to run Enterprise Manager Configuration Assistant.

    ORACLE_HOME/bin/emca -restore asm -cluster

You are prompted to enter the following information:

- Oracle home for the database that you want to restore

- Oracle ASM port

**Parent topic:** Running EMCA to Restore Oracle Enterprise Manager After Downgrading

###### Running emca on a Single-Instance Oracle Database With Oracle ASM

Use Enterprise Manager Configuration Assistant (`emca`) to manage your database and storage.

Use this command to run Enterprise Manager Configuration Assistant.

    ORACLE_HOME/bin/emca -restore db_asm

You are prompted to enter the following information:

- Oracle home for the Oracle Database that you want to restore

- Database SID

- Listener port number

- Oracle ASM port

- Oracle ASM home

- Oracle ASM SID \[+ASM\]

**Parent topic:** Running EMCA to Restore Oracle Enterprise Manager After Downgrading

###### Running emca on an Oracle RAC Database and Oracle ASM Instance

Use Enterprise Manager Configuration Assistant (`emca`) to manage your database and storage.

Use this command to run Enterprise Manager Configuration Assistant:

    ORACLE_HOME/bin/emca -restore db_asm -cluster

You are prompted to enter the following information:

- Oracle home for the database that you want to restore

- Database unique name

- Listener port number

- Oracle ASM port

- Oracle ASM Oracle home

- Oracle ASM SID \[+ASM\]

The output of `emca` varies according to the options that you specify and the values that you enter at the prompts. In Oracle RAC environments, you must repeat this step on all Oracle RAC cluster member nodes.

You must now run the `emdwgrd` utility to restore Oracle Enterprise Manager Database Control and data.

**Parent topic:** Running EMCA to Restore Oracle Enterprise Manager After Downgrading

##### Running the emdwgrd utility to restore Enterprise Manager Database Control

You can restore the Oracle Enterprise Manager Database Control and data by using the `emdwgrd` utility after you run `emca -restore`.

To use `emdwgrd`, you must do the following:

- Set ORACLE_HOME and other environment variables to point to the Oracle home from which the upgrade originally took place.

- Run the `emdwgrd` utility from the new release Oracle Database Oracle home.

The following procedure is for Linux and Unix. To run it on Windows, substitute `emdwgrd.bat` for `emdwgrd`.

1.  Set ORACLE_HOME to the Oracle home from which the database upgrade originally took place.

2.  Set ORACLE_SID to the SID of the database that was upgraded and then downgraded.

3.  Set PATH, LD_LIBRARY_PATH and SHLIB_PATH to point to the Oracle home from which the database upgrade originally took place.

4.  Go to the new Oracle Database release Oracle home:

        cd $ORACLE_HOME/bin

5.  Run `emdwgrd` using one of the following procedures:

    1.  For a single-instance database, run the following command, where `SID` is the SID of the database that was upgraded and then downgraded and `save_directory` is the path to the storage location you chose when saving your database control files and data:

            emdwgrd -restore -sid SID -path save_directory -tempTablespace TEMP

    2.  For an Oracle RAC database, remote copy is required across the cluster nodes. Define an environment variable to indicate which remote copy is configured. For example:

            setenv EM_REMCP /usr/bin/scp

        Then, run emdwgrd —restore with the following options:

            emdwgrd -restore -tempTablespace TEMP -cluster -sid SID_OldHome -path save_directory

        If the Oracle home is on a shared device, then add -shared to the `emdwgrd` command options.

6.  Enter the SYS and SYSMAN passwords when prompted by `emdwgrd`.

7.  When `emdwgrd` completes, Oracle Enterprise Manager Database Control is downgraded to the old Oracle home.

**Parent topic:** Restoring Oracle Enterprise Manager after Downgrading Oracle Database

#### Restoring Oracle APEX to the Earlier Release

After a downgrade, if you upgraded Oracle APEX (formerly Oracle Application Express) at the same time as you upgraded Oracle Database, then you must complete steps to revert to the earlier release.

To complete the downgrade of Oracle APEX after a database downgrade, complete all the steps listed in Oracle APEX Installation Guide to revert your Oracle APEX release to the earlier release. The steps to revert are different, depending on whether your architecture is a Non-CDB or a multitenant architecture (CDB) Oracle Database.

**Note:**

You only need to complete these steps if you upgraded Oracle APEX at the same time that you upgraded the database.

**Related Topics**

- [Oracle APEX Installation Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/upgrd&id=HTMIG-GUID-802A767F-2528-4B98-AC4F-B683DF4E572B)

**Parent topic:** Post-Downgrade Tasks for Oracle Database Downgrades

#### Gathering Dictionary Statistics After Downgrading

To help to assure good performance after you downgrade, use this procedure to gather dictionary statistics.

Oracle recommends that you gather dictionary statistics after downgrading the database, so that the statistics are collected for the downgraded release Data Dictionary tables.

**Note:**

After a downgrade process, be aware that the the data dictionary can have changes that persist in the downgraded dictionary. These changes are insignificant. The downgraded data dictionary is functionally equivalent to an earlier release data dictionary.

- Non-CDB Oracle Database: Oracle recommends that you use the `DBMS_STATS.GATHER_DICTIONARY_STATS` procedure to gather these statistics. For example, enter the following SQL statement:

      SQL> EXEC DBMS_STATS.GATHER_DICTIONARY_STATS;

- CDB (multitenant architecture) Oracle Database: Oracle recommends that you use `catcon` to gather Data Dictionary statistics across the entire multitenant architecture.

  To gather dictionary statistics for all PDBs in a container database, use the following syntax:

  `$ORACLE_HOME/perl/bin/perl $ORACLE_HOME/rdbms/admin/catcon.pl -l /tmp -b gatherstats -- --x"exec dbms_stats.gather_dictionary_stats"`

  To gather dictionary statistics on a particular PDB, use syntax similar to the following:

      $ORACLE_HOME/perl/bin/perl $ORACLE_HOME/rdbms/admin/catcon.pl -l /tmp -c
      'SALES1' -b gatherstats -- --x"exec dbms_stats.gather_dictionary_stats"

  In the preceding example the `-c SALES1` option specifies a PDB inclusion list for the command that you run, specifying the database named `SALES1`. The option ` -b gatherstats`specifies the base name for the logs. The option `--x` specifies the SQL command that you want to execute. The SQL command itself is inside the quotation marks.

**Related Topics**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_STATS.md)

**Parent topic:** Post-Downgrade Tasks for Oracle Database Downgrades

#### Regathering Fixed Object Statistics After Downgrading

After the downgrade, run representative workloads on Oracle Database, and regather fixed object statistics.

Fixed objects are the X\$ tables and their indexes. V\$ performance views are defined through X\$ tables. After you downgrade, regather fixed object statistics to ensure that the optimizer for the restored database can generate good execution plans. These execution plans can improve database performance. Failing to obtain representative statistics can lead to suboptimal execution plans, which can cause performance problems

Gather fixed objects statistics by using the `DBMS_STATS.GATHER_FIXED_OBJECTS_STATS` PL/SQL procedure. `DBMS_STATS.GATHER_FIXED_OBJECTS_STATS` also displays recommendations for removing all hidden or underscore parameters and events from `init.ora` and `SPFILE`.

To gather statistics for fixed objects, run the following PL/SQL procedure:

    SQL> execute dbms_stats.gather_fixed_objects_stats;

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_STATS.md) for more information about using the `GATHER_FIXED_OBJECTS_STATS` procedure

**Parent topic:** Post-Downgrade Tasks for Oracle Database Downgrades

#### Regathering Stale CBO Statistics After Downgrade

Oracle recommends that you regather Oracle Cost-Based Optimizer (CBO) statistics after completing an Oracle Database downgrade.

When you upgrade Oracle Database and gather new CBO statistics, the upgraded database has new database statistics. The upgraded database also can include new histogram types. For this reason, when you downgrade the database, the statistics that you collected for the new release can be different from the previous release. This issue is applicable both to data dictionary tables, and to regular user tables.

Regather stale statistics either by using GATHER_DATABASE_STATS, or by using gather commands that you typically use to update stale statistics in the dictionary and application schemas.

For example:

- Non-CDB Oracle Database: To regather statistics, Oracle recommends that you use the `GATHER_DATABASE_STATS` procedure, with the option `'GATHER STALE'`. For example:

      SQL> execute dbms_stats.gather_database_stats(options=>'GATHER STALE');

- CDB (multitenant architecture) Oracle Database: to regather Data Dictionary statistics across the entire multitenant architecture, Oracle recommends that you use `catcon`.

  To regather stale dictionary statistics for all PDBs in a container database, use the following syntax:

  `$ORACLE_HOME/perl/bin/perl $ORACLE_HOME/rdbms/admin/catcon.pl -l /tmp -b gatherstats -- --x"exec dbms_stats.gather_database_stats(options=>'GATHER STALE')"`

  To gather dictionary statistics on a particular PDB, use syntax similar to the following:

      $ORACLE_HOME/perl/bin/perl $ORACLE_HOME/rdbms/admin/catcon.pl -l /tmp -c
      'SALES1' -b gatherstats -- --x"exec dbms_stats.gather_database_stats(options=>'GATHER STALE')"

  In the preceding example, the `-c SALES1` option specifies a PDB inclusion list for the command that you run, specifying the database named `SALES1`. The option ` -b gatherstats`specifies the base name for the logs. The option `--x` specifies the SQL command that you want to execute. The SQL command itself is inside the quotation marks.

**Related Topics**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_STATS.md)

**Parent topic:** Post-Downgrade Tasks for Oracle Database Downgrades

#### Checking Validity of Registry Components After Downgrade

Check the validity of registry components and identify any invalid components.

After the downgrade, check the state of the components in the database. If you downgrade a complete CDB, then you can use the `CDB_REGISTRY` view. You can also check an individual PDB using `DBA_REGISTRY`. Ensure that all components are either `VALID` or `OPTION OFF`.

Example 8-1 Check Registry on a CDB with CDB_REGISTRY View

    set line 200
    set pages 1000
    col COMP_ID format a8
    col COMP_NAME format a34
    col SCHEMA format a12
    col STATUS format a10
    col VERSION format a12
    col CON_ID format 99

    select CON_ID, COMP_ID, comp_name, schema, status, version from CDB_REGISTRY order by 1,2;

Example 8-2 Check Registry on a Non-CDB or PDB with DBA_REGISTRY View

    set line 200
    set pages 1000
    col COMP_ID format a8
    col COMP_NAME format a34
    col SCHEMA format a12
    col STATUS format a10
    col VERSION format a12
    col CON_ID format 99

    select CON_ID, COMP_ID, comp_name, schema, status, version from DBA_REGISTRY order by 1,2;

**Related Topics**

- [Upgrade Your Database Now! Database Migration from non-CDB to PDB – The Component Pitfall](https://mikedietrichde.com/2019/07/31/database-migration-from-non-cdb-to-pdb-the-component-pitfall/)
- [CHECK_COMPONENTS.SQL Script - Displays installed components from DBA_REGISTRY](https://github.com/MikeDietrichDE/scripts/blob/main/check_components.sql)

**Parent topic:** Post-Downgrade Tasks for Oracle Database Downgrades

### Troubleshooting the Downgrade of Oracle Database

Use this troubleshooting information to address issues that may occur when downgrading Oracle Database.

This section contains known errors that may occur during downgrades, and workarounds to address those errors.

- Errors Downgrading Oracle Database Components with catdwgrd.sql Script
  Use this section to troubleshoot errors when you run the `catdwgrd.sql` script during a downgrade, such as `ORA-20001`: Downgrade cannot proceed.
- Downgrading Oracle Grid Infrastructure (Oracle Restart) After Successful or Failed Upgrade
  To downgrade Oracle Restart, you must deconfigure and then reinstall Oracle Grid Infrastructure. You can then add back the databases and services.
- Errors Downgrading Databases with Oracle Messaging Gateway
  If you downgrade a database configured with Oracle Messaging Gateway , then you can encounter `ORA-02303` errors.

**Parent topic:** Downgrading Oracle Database to an Earlier Release

#### Errors Downgrading Oracle Database Components with catdwgrd.sql Script

Use this section to troubleshoot errors when you run the `catdwgrd.sql` script during a downgrade, such as `ORA-20001`: Downgrade cannot proceed.

The `catdwgrd.sql` script downgrades all Oracle Database components in the database to the major release from which you originally upgraded. This script must run before the Data Dictionary can be downgraded. If you encounter any problems when you run the script, then correct the causes of the problems, and rerun the script.

Errors you can see include `ORA-39709` and `ORA-06512`. When these errors occur, downgrades cannot proceed.

- Cause: One or more components that must be downgraded before proceeding with the Data Dictionary downgrade did not downgrade.

- Action: Review the log files to determine what errors occurred before the `catdwgrd.sql` script halted, and the downgrade was stopped.

Review these examples to understand how to correct this issue.

Errors typically describe what you must do to fix the issue that is preventing the downgrade to complete. Follow the instructions in the error message. After you have fixed the cause of the error, rerun the `catdwgrd.sql` script.

For example, If the CDB downgrade fails during the downgrade of CDB\$ROOT due to a check, then follow the instructions in the error message to fix the condition error. After you fix the error, rerun `catdwgrd.sql` with `catcon.pl`. Use the `-c` option to run the command with the inclusion list `'CDB$ROOT PDB1'`. Use the `-r` option to run the command first on the PDB, and then on CDB\$ROOT. For example:

    $ORACLE_HOME/perl/bin/perl $ORACLE_HOME/rdbms/admin/catcon.pl -d $ORACLE_HOME/rdbms/admin -e -b catdwgrd -l /scratch/rac/downgradeLogs -c 'CDB$ROOT, PDB1, PDB2' -r catdwgrd.sql

Example 8-3 ORA-20001 Error Due To ORA-06512

Your downgrade stops. When you review the log files, you find that `catdwgrd.sql` terminates on this error:

    DECLARE * ERROR at line 1: ORA-20001: Downgrade cannot proceed -
    Unified Audit Trail data exists. Please clean up the data first
    using DBMS_AUDIT_MGMT.CLEAN_AUDIT_TRAIL. ORA-06512: at line 65
    ORA-06512: at line 42

You must purge the unified audit trial on ` CDB$ROOT` and on all PDBs.

For example:

1.  Look for the presence of unified audit trails:

        SQL> SELECT COUNT(*) FROM UNIFIED_AUDIT_TRAIL;
        COUNT(*)
        ----------
              4538

2.  Purge the audit trail. on the CDB.

    For example, where the audit trail type is `DBMS_AUDIT.MGMT.AUDIT`:

        EXEC DBMS_AUDIT_MGMT.CLEAN_AUDIT_TRAIL DBMS_AUDIT_MGMT.AUDIT

3.  Run `catdwngrd.sql `on `CDB$ROOT`. If PDBs still have unified audit data, then the script fails with ORA20001:

         62        execute immediate
         63        'select count(*) from audsys.'||'"'||tab_name||'"' into no_rows;
         64
         65        -- If audit trail has some data, raise the application error
         66        IF no_rows > 0 THEN
         67          RAISE_APPLICATION_ERROR(-20001, ErrMsg);
         68        END IF;
         69      END IF;
         70    END IF;
         71  EXCEPTION
         72    WHEN NO_DATA_FOUND THEN
         73     NULL;
         74    WHEN OTHERS THEN
         75     RAISE;
         76  END;
         77  /
        DECLARE
        *
        ERROR at line 1:
        ORA-20001: Downgrade cannot proceed - Unified Audit Trail data exists.Please
        clean up the data first using DBMS_AUDIT_MGMT.CLEAN_AUDIT_TRAIL.
        ORA-06512: at line 75

4.  Connect to individual PDBs, and find if they have unified audit trails. Clear the unified audit trail for all PDBs. For example, The PDB named PDB1 has unified audit trails:

        ALTER SESSION SET container = PDB1;

        SQL> SELECT COUNT(*) FROM UNIFIED_AUDIT_TRAIL;
         COUNT(*)
        ----------
              1330

5.  Identify the unified audit trails:

        SQL> CREATE TABLE UA_DATA AS (SELECT * FROM UNIFIED_AUDIT_TRAIL);

6.  Purge the audit trails.

    In this example, the audit trail type is `DBMS_AUDIT_MGMT.AAUDIT_TRAIL_UNIFIED`, the `USE_LAST_ARCH_TIMESTAMP` value is set to `FALSE`, so that all audit records are deleted, without considering last archive timestamp, and the `CONTAINER` value is set to `DBMS_AUDIT_MGMT.CONTAINER_ALL`, so that audit records on all PDBs are purged.

        BEGIN
          DBMS_AUDIT_MGMT.CLEAN_AUDIT_TRAIL(
           AUDIT_TRAIL_TYPE           =>  DBMS_AUDIT_MGMT.AUDIT_TRAIL_UNIFIED,
           USE_LAST_ARCH_TIMESTAMP    =>  FALSE,
           CONTAINER                  =>  DBMS_AUDIT_MGMT.CONTAINER_ALL
        END;
        /

7.  Rerun `catdwngrd.sql` at the PDB and CDB level. For example:

        $ORACLE_HOME/perl/bin/perl $ORACLE_HOME/rdbms/admin/catcon.pl -c 'CDB$ROOT,PDB1' -d $ORACLE_HOME/rdbms/admin -e -b catdwgrd -l /u01/oracle/product/19.0.0/downgrade_logs -r catdwgrd.sql

8.  Repeat the process of finding and purging audit trails and run `catdwgrd.sql` until the script completes successfully on the CDB and PDBs, and you no longer see `ORA-20001` errors in logs

**Related Topics**

- [Oracle Database Security Guide](../dbseg/administering-the-audit-trail.md)

**Parent topic:** Troubleshooting the Downgrade of Oracle Database

#### Downgrading Oracle Grid Infrastructure (Oracle Restart) After Successful or Failed Upgrade

To downgrade Oracle Restart, you must deconfigure and then reinstall Oracle Grid Infrastructure. You can then add back the databases and services.

**Related Topics**

- <https://support.oracle.com/rs?type=doc&id=1364412.1>
- [Oracle Grid Infrastructure Installation and Upgrade Guide](../install-and-upgrade.md)

**Parent topic:** Troubleshooting the Downgrade of Oracle Database

#### Errors Downgrading Databases with Oracle Messaging Gateway

If you downgrade a database configured with Oracle Messaging Gateway , then you can encounter `ORA-02303` errors.

If you downgrade an Oracle Database that contains Oracle Messaging Gateway objects, then you can encounter the following error:

    ORA-02303: cannot drop or replace a type with type or table dependents

- Cause The `catrelod.sql` script is attempting to reload Oracle Messaging Gateway objects of a different type than the earlier Oracle Database release.
- Action No action. You can ignore this error.

**Parent topic:** Troubleshooting the Downgrade of Oracle Database
