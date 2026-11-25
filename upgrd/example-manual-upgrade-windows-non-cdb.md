## Example of Manual Upgrade of Windows Non-CDB Oracle Database

These examples show the steps to complete preupgrade checks, upgrade, and postupgrade checks for an Oracle Database 11g Release 2 (11.2.0.4) upgrade to Oracle Database 19c.

The specific examples in these topics show an upgrade on the Microsoft Windows platform. They use tools specific to the Windows environment. However, these example provide an overview of a manual installation experience.

- Preparing to Upgrade Windows Non-CDB Using Command-Line Utilities
  Complete the required preupgrade steps before upgrading Non-CDB Oracle Database 11g release 2 (11.2.0.4) databases to a Non-CDB Oracle Database 12c and later releases.
- Manually Upgrading Windows Non-CDB Using Command-Line Utilities
  These examples show upgrade steps to upgrade a Non-CDB Oracle Database 11g release 2 (11.2.0.4) to a Non-CDB Oracle Database

**Parent topic:** [Upgrading Oracle Database Manually Using Parallel Upgrade Utility](upgrading-oracle-database-parallel-upgrade-utiility-replay-upgrade.md)

### Preparing to Upgrade Windows Non-CDB Using Command-Line Utilities

Complete the required preupgrade steps before upgrading Non-CDB Oracle Database 11g release 2 (11.2.0.4) databases to a Non-CDB Oracle Database 12c and later releases.

This procedure provides an example of how to use command-line utilities to prepare your system to carry out a manual upgrade of a Non-CDB Oracle Database to a current release Non-CDB Oracle Database on Microsoft Windows. In this example, the Oracle Database that you are upgrading is Oracle Database 11g release 2 (11.2.0.4).

Log in as a user that is a member of the `ORA_DBA` group. Oracle recommends that you install the new release Oracle Database binaries on the server. Refer to the Oracle Database installation guide for Windows to complete that procedure.

The Preupgrade consists of the following steps:

1.  Reset the user environment variables from the new release Oracle home to the 11.2.0.4 Oracle home for the Oracle Installation Owner User Account (Oracle user).

2.  Test the connection to the 11.2.0.4 Oracle Database.

3.  Run the following command:

        autoupgrade.jar -mode analyze

4.  Review `autoupgrade.jar` reports.

5.  Back up your database.

These examples use the following systems, paths, and users:

Oracle Database 11g release 2 (11.2.0.4)

- Oracle Installation Owner user account: `oracle1`, which is a member of the ORA_DBA group.

- Oracle home: `C:\app\oracle\product\11.2.0\dbhome_1`

Oracle Database 19c

- Oracle Installation Owner user account: `oracle2`, which is a member of the ORA_DBA group.

- Oracle home: `C:\app\oracle1\product\19\dbhome_1`

Example 4-13 Resetting the User Environment Variables

This example shows how to change the environment variables from values set for the Oracle Database 19c installation:

    C:\app\oracle1\product\19\dbhome_1\rdbms\admin>set ORACLE_HOME=C:\app\oracle2\product\11.2.0\dbhome_1
    C:\app\oracle1\product\19\dbhome_1\rdbms\admin>set ORACLE_SID=orcl11

Example 4-14 Testing the Connection to the Database

This example shows how to test the connection to the database, and ensure that you are connecting to the release 11.2.0.4 database that you want to upgrade.

    C:\app\oracle1\product\19\dbhome_1\rdbms\admin>sqlplus / as sysdba

        SQL*Plus: Release 11.2.0.4.0 Production on Tue Dec 11 12:14:49 2018

        Copyright (c) 1982, 2011, Oracle.  All rights reserved.

        Connected to:
        Oracle Database 11g Enterprise Edition Release 11.2.0.4.0 - 64bit Production
        With the Partitioning, OLAP, Data Mining and Real Application Testing options

        SQL> select version from v$instance;

        VERSION
        -----------------
        11.2.0.4.0

        SQL>

Example 4-15 Manually Removing Oracle Enterprise Manager (em_present)

The `autoupgrade.jar -mode analyze` log file provides you with instructions to remove Oracle Enterprise Manager manually (`em_present`):

    + Remove the EM repository.

             - Copy the rdbms/admin/emremove.sql script from the target 19.0.0.0.0
             ORACLE_HOME into the source 11.2.0.4.0 ORACLE_HOME.

             Step 1: If database control is configured, stop EM Database Control,
             using the following command

               $> emctl stop dbconsole

             Step 2: Connect to the database using the SYS account AS SYSDBA

               SET ECHO ON;
               SET SERVEROUTPUT ON;

              @emremove.sql
            ...
            ...
            ...

            Execution:

            Step 1 - Stop dbconsole:

                C:\app\oracle1\product\19\dbhome_1\rdbms\admin> emctl stop dbconsole

                Oracle Enterprise Manager 11g Database Control Release 11.2.0.4.0
                Copyright (c) 1996, 2011 Oracle Corporation.  All rights reserved.
                https://db01.example.com:1158/em/console/aboutApplication
                The OracleDBConsoleorcl11 service is stopping...........
                The OracleDBConsoleorcl11 service was stopped successfully.

            Step 2 - Remove em (provide credentials if needed)

                ...
                ...
                ...

                Dropping synonym : SETEMVIEWUSERCONTEXT ...
                Dropping synonym : SMP_EMD_AVAIL_OBJ ...
                Dropping synonym : SMP_EMD_DELETE_REC_ARRAY ...
                Dropping synonym : SMP_EMD_INTEGER_ARRAY ...
                Dropping synonym : SMP_EMD_INTEGER_ARRAY_ARRAY ...
                Dropping synonym : SMP_EMD_NVPAIR ...
                Dropping synonym : SMP_EMD_NVPAIR_ARRAY ...
                Dropping synonym : SMP_EMD_STRING_ARRAY ...
                Dropping synonym : SMP_EMD_STRING_ARRAY_ARRAY ...
                Dropping synonym : SMP_EMD_TARGET_OBJ ...
                Dropping synonym : SMP_EMD_TARGET_OBJ_ARRAY ...
                Finished phase 5
                Starting phase 6 : Dropping Oracle Enterprise Manager related other roles ...
                Finished phase 6
                The Oracle Enterprise Manager related schemas and objects are dropped.
                Do the manual steps to studown the DB Control if not done before running this
                script and then delete the DB Control configuration files

                PL/SQL procedure successfully completed.

                SQL>

Example 4-16 Manually Removing the OLAP Catalog (amd_exists)

The `preupgrade_fixups.sql` log file provides you with instructions to remove the OLAP catalog manually (`amd_exists`):

     + Remove OLAP Catalog by running the 11.2.0.4.0 SQL script
         $ORACLE_HOME/olap/admin/catnoamd.sql script.

         The OLAP Catalog component, AMD, exists in the database.

         sqlplus / as sysdba @%ORACLE_HOME%\olap\admin\catnoamd.sql
            ...
            ...
            ...

            Synonym dropped.

            User dropped.

            Role dropped.

            SQL>

Example 4-17 Granting the ADMINISTER DATABASE TRIGGER privilege (trgowner_no_admndbtrg)

The `autoupgrade.jar -mode analyze` report provides you with instructions to grant the `ADMINISTER DATABASE TRIGGER` privilege (`trgowner_no_admndbtrg`):

    + Directly grant ADMINISTER DATABASE TRIGGER privilege to the owner of the
             trigger or drop and re-create the trigger with a user that was granted
             directly with such. You can list those triggers using "SELECT OWNER,
             TRIGGER_NAME FROM DBA_TRIGGERS WHERE BASE_OBJECT_TYPE='DATABASE' AND
             OWNER NOT IN (SELECT GRANTEE FROM DBA_SYS_PRIVS WHERE
             PRIVILEGE='ADMINISTER DATABASE TRIGGER')"

                SQL> SELECT OWNER,
                  2       TRIGGER_NAME FROM DBA_TRIGGERS WHERE BASE_OBJECT_TYPE='DATABASE' AND
                  3       OWNER NOT IN (SELECT GRANTEE FROM DBA_SYS_PRIVS WHERE
                  4       PRIVILEGE='ADMINISTER DATABASE TRIGGER');

                OWNER                          TRIGGER_NAME
                ------------------------------ ------------------------------
                MDSYS                          SDO_DROP_USER
                MDSYS                          SDO_ST_SYN_CREATE
                MDSYS                          SDO_TOPO_DROP_FTBL
                MDSYS                          SDO_GEOR_BDDL_TRIGGER
                MDSYS                          SDO_GEOR_ADDL_TRIGGER
                MDSYS                          SDO_NETWORK_DROP_USER

                6 rows selected.

                SQL> grant ADMINISTER DATABASE TRIGGER to MDSYS;

                Grant succeeded.

Example 4-18 Refreshing Materialized Views (mv_refresh)

The `autoupgrade.jar -mode analyze` log file provides you with instructions to refresh materialized views (`mv_refresh`):

    + Please make sure that all the MVs are refreshed and sys.sumdelta$
             becomes empty before doing upgrade, unless you have strong business
             reasons not to do so. You can use dbms_mview.refresh() to refresh the
             MVs except those stale ones  to be kept due to business need. If there
             are any stale MVs depending on changes in sys.sumdelta$, do not truncate
             it, because doing so will cause wrong results after refresh.

                SQL> declare
                  2  num_failures integer(3) :=0;
                  3  begin
                  4  DBMS_MVIEW.REFRESH_ALL_MVIEWS(num_failures,'C','', TRUE, FALSE);
                  5  end;
                  6  /

                PL/SQL procedure successfully completed.

                SQL> select count(1) from sumdelta$;

                  COUNT(1)
                ----------
                         0

                SQL>

Example 4-19 Upgrading Oracle Application Express (apex_upgrade_msg)

The `autoupgrade.jar -mode analyze` report recommends to you that you can upgrade Oracle Application Express (`apex_upgrade_msg`). Running this upgrade can reduce the downtime required for the Oracle Database upgrades. The log file provides you with information about how to complete that upgrade:

    + Consider upgrading APEX manually, before the database upgrade.

             The database contains APEX version 3.2.1.00.12 and will need to be
             upgraded to at least version 5.0.4.00.11.

             To reduce database upgrade time, you can upgrade APEX manually before
             the database upgrade.  Refer to My Oracle Support Note 1088970.1 for
             information on APEX installation upgrades.

            Download: http://www.oracle.com/technetwork/developer-tools/apex/downloads/index.html provide credentials.

            Then go to: http://www.oracle.com/technetwork/developer-tools/apex/application-express/upgrade-apex-for-xe-154969.html and
                        https://docs.oracle.com/cd/E59726_01/install.50/e39144/toc.htm to guide you to do the upgrade.

            Once downloaded, please go to the directory and unzip the files, run the apex upgrade from there.

            ...
            ...
                Completing registration process. 12:07:41
                Validating installation.  12:07:41
                ...Starting validation 12:07:41
                ...Database user "SYS", database schema "APEX_050000", user# "90" 12:07:41
                ...272 packages
                ...265 package bodies
                ...465 tables
                ...8 functions
                ...16 procedures
                ...4 sequences
                ...497 triggers
                ...1582 indexes
                ...255 views
                ...0 libraries
                ...14 types
                ...5 type bodies
                ...0 operators
                ...0 index types
                ...Begin key object existence check 12:07:53
                ...Completed key object existence check 12:07:54
                ...Setting DBMS Registry 12:07:54
                ...Setting DBMS Registry Complete 12:07:54
                ...Exiting validate 12:07:54

                PL/SQL procedure successfully completed.

                timing for: Validate Installation
                Elapsed: 00:00:13.00

                Session altered.

                timing for: Complete Installation
                Elapsed: 00:18:40.49

            ...
            ...

**Caution:**

After you complete preupgrade steps, Oracle recommends that you back up your database before proceeding with the upgrade.

**Related Topics**

- [Back Up Oracle Database Before Upgrading](backing-up-oracle-db-for-upgrading.md)

**Parent topic:** Example of Manual Upgrade of Windows Non-CDB Oracle Database

### Manually Upgrading Windows Non-CDB Using Command-Line Utilities

These examples show upgrade steps to upgrade a Non-CDB Oracle Database 11g release 2 (11.2.0.4) to a Non-CDB Oracle Database

After you complete running preupgrade steps, you can upgrade the Non-CDB Oracle Database to the new release Non-CDB Oracle Database. Before starting the upgrade, you must stop the database services. You can stop database services either by using command-line commands, or by using Microsoft Windows PowerShell scripting.

The sequence of steps to complete the upgrade is as follows:

1.  Stop the database service, using either command-line commands, or PowerShell.

2.  Delete the database service from the earlier release Oracle home.

3.  Stop the listener from the earlier release Oracle home

4.  Set the environment variables to the new Oracle home.

5.  Copy database files, such as `tnsnames.ora`, `listener.ora`, password files, wallets, and other similar files to the new Oracle home.

6.  Copy the PFILE to the new Oracle Database Oracle home, and create a new service using the Oracle Database binary in the new Oracle home. (In this example, we assume that the PFILE is compatible. It is possible that your PFILE is not compatible with the new release.)

7.  Start the database upgrade.

8.  Complete the post-upgrade steps.

Example 4-20 Stopping the Database Service Using Command-Line Commands

1.  If you do not know the service name, then identify the service name.

        c:\apex\apex>sc query type= service | find /i "orcl11"
                        SERVICE_NAME: OracleServiceORCL11
                        DISPLAY_NAME: OracleServiceORCL11

2.  Using the service name, find out what the status is of the service.

        c:\apex\apex>sc query  OracleServiceORCL11

                        SERVICE_NAME: OracleServiceORCL11
                            TYPE               : 10  WIN32_OWN_PROCESS
                            STATE              : 4  RUNNING
                                                    (STOPPABLE, PAUSABLE, ACCEPTS_SHUTDOWN)
                            WIN32_EXIT_CODE    : 0  (0x0)
                            SERVICE_EXIT_CODE  : 0  (0x0)
                            CHECKPOINT         : 0x0
                            WAIT_HINT          : 0x0

3.  Stop the service

        c:\apex\apex>sc stop  OracleServiceORCL11

                        SERVICE_NAME: OracleServiceORCL11
                            TYPE               : 10  WIN32_OWN_PROCESS
                            STATE              : 3  STOP_PENDING
                                                    (STOPPABLE, PAUSABLE, ACCEPTS_SHUTDOWN)
                            WIN32_EXIT_CODE    : 0  (0x0)
                            SERVICE_EXIT_CODE  : 0  (0x0)
                            CHECKPOINT         : 0x5
                            WAIT_HINT          : 0x15f90

4.  Wait for a few minutes, and then check the status.

        c:\apex\apex>sc query  OracleServiceORCL11

                        SERVICE_NAME: OracleServiceORCL11
                            TYPE               : 10  WIN32_OWN_PROCESS
                            STATE              : 1  STOPPED
                            WIN32_EXIT_CODE    : 0  (0x0)
                            SERVICE_EXIT_CODE  : 0  (0x0)
                            CHECKPOINT         : 0x0
                            WAIT_HINT          : 0x0

    After the services are stopped, you can proceed to delete the services.

Example 4-21 Stopping the Database Service Using Microsoft Windows PowerShell Scripting

1.  Check the status of the service.

        PS C:\app\oraclbm\cfgtoollogs\orcl\preupgrade> Get-Service | Where-Object {$_.displayName.Contains("ORCL11")}

                        Status   Name               DisplayName
                        ------   ----               -----------
                        Stopped  OracleJobSchedu... OracleJobSchedulerORCL11
                        Running  OracleServiceOR... OracleServiceORCL11
                        Running  OracleVssWriter... Oracle ORCL11 VSS Writer Service

2.  Stop the service.

        PS C:\app\oraclbm\cfgtoollogs\orcl\preupgrade> Get-Service | Where-Object {$_.displayName.Contains("ORCL11")} | Stop-Ser
                        vice
                        WARNING: Waiting for service 'OracleServiceORCL11 (OracleServiceORCL11)' to stop...
                        WARNING: Waiting for service 'OracleServiceORCL11 (OracleServiceORCL11)' to stop...
                        WARNING: Waiting for service 'OracleServiceORCL11 (OracleServiceORCL11)' to stop...
                        WARNING: Waiting for service 'OracleServiceORCL11 (OracleServiceORCL11)' to stop...
                        WARNING: Waiting for service 'OracleServiceORCL11 (OracleServiceORCL11)' to stop...
                        WARNING: Waiting for service 'OracleServiceORCL11 (OracleServiceORCL11)' to stop...
                        WARNING: Waiting for service 'OracleServiceORCL11 (OracleServiceORCL11)' to stop...
                        WARNING: Waiting for service 'OracleServiceORCL11 (OracleServiceORCL11)' to stop...
                        WARNING: Waiting for service 'OracleServiceORCL11 (OracleServiceORCL11)' to stop...
                        WARNING: Waiting for service 'OracleServiceORCL11 (OracleServiceORCL11)' to stop...
                        WARNING: Waiting for service 'OracleServiceORCL11 (OracleServiceORCL11)' to stop...


    After the services are stopped, you can proceed to delete the database service.

Example 4-22 Deleting the Database Service from the Earlier Release Oracle Home

For Oracle Database 11g release 2 (11.2.0.4) on Windows, use ORADIM from the earlier release Oracle home. ORADIM is a Windows-specific utility that you can use to administer the Windows service.

    c:\apex\apex>oradim -delete -sid orcl11
                Unable to stop service, OS Error = 1062
                Instance deleted.

Example 4-23 Stopping the Listener for the Earlier Release Oracle Home

    c:\apex\apex>lsnrctl status

                LSNRCTL for 64-bit Windows: Version 11.2.0.4.0 - Production on 13-JUL-2016 13:58:52

                Copyright (c) 1991, 2012, Oracle.  All rights reserved.

                Connecting to (DESCRIPTION=(ADDRESS=(PROTOCOL=IPC)(KEY=EXTPROC1522)))
                STATUS of the LISTENER
                ------------------------
                Alias                     LISTENER
                Version                   TNSLSNR for 64-bit Windows: Version 11.2.0.4.0 - Production
                Start Date                05-JUL-2018 10:01:30
                Uptime                    8 days 3 hr. 57 min. 23 sec
                Trace Level               off
                Security                  ON: Local OS Authentication
                SNMP                      OFF
                Listener Parameter File   C:\app\oracle2\product\11.2.0\dbhome_1\network\admin\listener.ora
                Listener Log File         C:\app\oracle2\diag\tnslsnr\slc01auu\listener\alert\log.xml
                Listening Endpoints Summary...
                  (DESCRIPTION=(ADDRESS=(PROTOCOL=ipc)(PIPENAME=\\.\pipe\EXTPROC1522ipc)))
                  (DESCRIPTION=(ADDRESS=(PROTOCOL=tcp)(HOST=db01.example.com)(PORT=1522)))
                Services Summary...
                Service "CLRExtProc" has 1 instance(s).
                  Instance "CLRExtProc", status UNKNOWN, has 1 handler(s) for this service...
                The command completed successfully

    c:\apex\apex>lsnrctl stop

                LSNRCTL for 64-bit Windows: Version 11.2.0.4.0 - Production on 13-JUL-2018 13:59:00

                Copyright (c) 1991, 2012, Oracle.  All rights reserved.

                Connecting to (DESCRIPTION=(ADDRESS=(PROTOCOL=IPC)(KEY=EXTPROC1522)))
                The command completed successfully

Example 4-24 Setting the environment variables to the new Oracle home

    c:\apex\apex>set ORACLE_HOME=C:\app\oracle1\product\18.1.0\dbhome_1

    c:\apex\apex>SET PATH=%ORACLE_HOME%\BIN;%PATH%

    c:\apex\apex>SET ORACLE_SID=ORCL11

Example 4-25 Copying the PFILE to the New Oracle home, and Creating a New Service Using the New Oracle Database binary

This example shows how to use the Windows-specific ORADIM utility to create a new database service. In this example, the PFILE from the earlier release is compatible with the new release.

    c:\apex\apex>C:\app\oracle1\product\18.1.0\dbhome_1\bin\oradim -new -sid orcl11 -syspwd
    My-sys-password -maxusers 1000 -startmode auto -pfile  C:\app\oracle1\product\18.1.0\dbhome_1\database\initorcl11.ora

                Enter password for Oracle service user:
                Instance created.

Example 4-26 Starting the Database Upgrade

Start the upgrade using the Parallel Upgrade Utility.

**Note:**

You can find that you have to change the folder symbolic links on the PFILE for paths such as DIAGNOSTIC_DEST. If this is the case, then you see errors such as the following examples:

    ORA-48173: error checking directory existence during ADR initialization [C:\app\oracle2\diag\rdbms\orcl11]
    ORA-00205: error in identifying control file, check alert log for more info

If you see these errors, then grant permissions to the user on the earlier release Oracle home, and on all the related folders with inheritance. Make this change also on any access control list (ACL) that the database accesses, such as wallet files. This step is particularly necessary if you are using the earlier release Oracle home as an ORADATA location.

If you are using the built-in account, then the service runs as `LocalSystem`. If you are using a virtual account, then services run using the Windows virtual accounts, with names derived from the service name. If the Oracle Database 19c binaries owner is a virtual account, then you must add that virtual account to the group `ORA_``Homename``_SVCAACCTS`, instead of adding the Oracle Home User.

Oracle Database 19c includes a shell script, `dbupgrade`. The shell script calls the Parallel Upgrade Utility (`catctl.pl`), so that you can run the upgrade as a command. This example shows the upgrade of Oracle Database from release 11.2.0.4 to release 19c. The upgrade time for your system can vary from the results in this example.

    C:\app\oracle1\product\19.1.0\dbhome_1\bin>dbupgrade
                ...
                ...
                ...
                    C:\app\oracle1\product\19.1.0\dbhome_1\bin>REM Batch file to execute catctl.pl

                    Argument list for [C:\app\oracle1\product\19\dbhome_1\rdbms\admin\catctl.pl]
                    Run in                c = 0
                    Do not run in         C = 0
                    Input Directory       d = 0
                    Echo OFF              e = 1
                    Simulate              E = 0
                    Forced cleanup        F = 0
                    Log Id                i = 0
                    Child Process         I = 0
                    Log Dir               l = c:\temp2
                    Priority List Name    L = 0
                    Upgrade Mode active   M = 0
                    SQL Process Count     n = 4
                    SQL PDB Process Count N = 0
                    Open Mode Normal      o = 0
                    Start Phase           p = 0
                    End Phase             P = 0
                    Reverse Order         r = 0
                    AutoUpgrade Resume    R = 0
                    Script                s = 0
                    Serial Run            S = 0
                    RO User Tablespaces   T = 0
                    Display Phases        y = 0
                    Debug catcon.pm       z = 0
                    Debug catctl.pl       Z = 0

                    catctl.pl VERSION: [19.0.0.0.0]
                        STATUS: [production]
                        BUILD: [RDBMS_MAIN_WINDOWS.X64_160624]

                    C:\app\oracle1\product\19.1.0\dbhome_1\rdbms\admin\orahome.exe = [C:\app\oracle1\product\19.1.0\dbhome_1]
                    C:\app\oracle1\product\19.1.0\dbhome_1\bin\orabasehome.exe = [C:\app\oracle1\product\189.1.0\dbhome_1]
                    catctlGetOrabase = [C:\app\oracle1\product\19.1.0\dbhome_1]

                    Analyzing file C:\app\oracle1\product\19.1.0\dbhome_1\rdbms\admin\catupgrd.sql

                    Log file directory = [c:\temp2]

                    catcon: ALL catcon-related output will be written to [c:\temp2/catupgrd_catcon_3252.lst]
                    catcon: See [c:\temp2/catupgrd*.log] files for output generated by scripts
                    catcon: See [c:\temp2/catupgrd_*.lst] files for spool files, if any

                    Number of Cpus        = 2
                    Database Name         = orcl11
                    DataBase Version      = 11.2.0.4.0
                    Parallel SQL Process Count            = 4
                    Components in [orcl11]
                        Installed [APEX APS CATALOG CATJAVA CATPROC CONTEXT JAVAVM ORDIM OWM SDO XDB XML XOQ]
                    Not Installed [DV EM MGW ODM OLS RAC WK]

                    ------------------------------------------------------
                    Phases [0-109]         Start Time:[2018_12_13 15:49:40]
                    ------------------------------------------------------
                    ***********   Executing Change Scripts   ***********
                    Serial   Phase #:0    [orcl11] Files:1

                ...
                ...
                ...
                    ------------------------------------------------------
                    Phases [0-109]         End Time:[2018_12_13 16:53:27]
                    ------------------------------------------------------

                    Grand Total Time: 3830s

                     LOG FILES: (c:\temp2\catupgrd*.log)

                    Upgrade Summary Report Located in:
                    c:\temp2\upg_summary.log

                    Grand Total Upgrade Time:    [0d:1h:3m:50s]

Example 4-27 Completing the Post-Upgrade Checks

Start the upgraded Oracle Database, and check the version and status.

    C:\app\oracle1\product\19.1.0\dbhome_1\bin>sqlplus / as sysdba

                    SQL*Plus: Release 19.1.0 Production on Thu Dec 13 09:38:50 201

                    Copyright (c) 1982, 2019, Oracle.  All rights reserved.

                    Connected to an idle instance.

                    SQL> startup
                    ORACLE instance started.

                    Total System Global Area 1828716544 bytes
                    Fixed Size                  8740096 bytes
                    Variable Size             503317248 bytes
                    Database Buffers         1308622848 bytes
                    Redo Buffers                8036352 bytes
                    Database mounted.
                    Database opened.
                    SQL> select open_mode from v$database;

                    OPEN_MODE
                    --------------------
                    READ WRITE

                    SQL> select version from v$instance;

                    VERSION
                    -----------------
                    19.0.0.0.0

                    SQL>

After the upgrade is complete, carry out post-upgrade checks to ensure that objects are valid, and that there are no remaining issues.

**Parent topic:** Example of Manual Upgrade of Windows Non-CDB Oracle Database
