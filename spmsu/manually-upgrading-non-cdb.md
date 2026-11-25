This procedure provides steps for upgrading non-CDB architecture Oracle Databases.

**Note:**

Starting with Oracle Database 12c Release 1 (12.1), non-CDB architecture is deprecated. It can be desupported in a future release.

Before using this procedure, complete the following steps:

- Install the Oracle Database software

- Prepare the new Oracle home

- Run the Pre-Upgrade Information Tool

Steps:

1.  If you have not done so, run the Pre-Upgrade Information Tool. Review the Pre-Upgrade Information Tool output and correct all issues noted in the output before proceeding.

    For example, on Linux or Unix systems:

         $ORACLE_HOME/jdk/bin/java -jar /opt/oracle/product/19.0.0/rdbms/admin/preupgrade.jar FILE TEXT

2.  Ensure that you have a proper backup strategy in place.

3.  If you have not done so, prepare the new Oracle home.

4.  (Conditional) For Oracle RAC environments only, enter the following commands to set the initialization parameter value for CLUSTER_DATABASE to FALSE:

        ALTER SYSTEM SET CLUSTER_DATABASE=FALSE SCOPE=SPFILE;

5.  Shut down the database. For example:
        SQL> SHUTDOWN IMMEDIATE

6.  If your operating system is Windows, then complete the following steps:

    1.  Stop the `OracleService``SID` Oracle service of the database you are upgrading, where `SID` is the instance name. For example, if your `SID` is `ORCL`, then enter the following at a command prompt:

            C:\> NET STOP OracleServiceORCL

    2.  Delete the Oracle service at a command prompt using `ORADIM`. Refer to your platform guide for a complete list of the `ORADIM` syntax and commands.

        For example, if your `SID` is `ORCL`, then enter the following command.

            C:\> ORADIM -DELETE -SID ORCL

    3.  Create the service for the new release Oracle Database at a command prompt using the `ORADIM` command of the new Oracle Database release.

        Use the following syntax, where `SID` is your database SID, `PASSWORD` is your system password, `USERS` is the value you want to set for maximum number of users, and `ORACLE_HOME` is your Oracle home:

            C:\> ORADIM -NEW -SID SID -SYSPWD PASSWORD -MAXUSERS USERS
                 -STARTMODE AUTO -PFILE ORACLE_HOME\DATABASE\INITSID.ORA

        Most Oracle Database services log on to the system using the privileges of the Oracle software installation owner. The service runs with the privileges of this user. The `ORADIM` command prompts you to provide the password to this user account. You can specify other options using `ORADIM`.

        In the following example, if your `SID` is `ORCL`, your `password` (`SYSPWD`) is `TWxy5791`, the maximum number of users (`MAXUSERS`) is 10, and the Oracle home path is `C:\ORACLE\PRODUCT\19.0.0\DB`, then enter the following command:

            C:\> ORADIM -NEW -SID ORCL -SYSPWD TWxy5791 -MAXUSERS 10
            -STARTMODE AUTO -PFILE C:\ORACLE\PRODUCT\19.0.0\DB\DATABASE\INITORCL.ORA

        `ORADIM` writes a log file to the `ORACLE_HOME\database` directory.

        **Note:**

        If you use an Oracle Home User account to own the Oracle home, then the ORADIM command prompts you for that user name and password.

7.  If your operating system is Linux or UNIX, then perform the following checks:

    1.  Your `ORACLE_SID` is set correctly

    2.  The `oratab` file points to the new Oracle home

    3.  The following environment variables point to the new Oracle Database directories:

        - `ORACLE_HOME`

        - `PATH`

    4.  Any scripts that clients use to set the `$ORACLE_HOME` environment variable must point to the new Oracle home.

    **Note:**

    If you are upgrading an Oracle Real Application Clusters database, then perform these checks on all Oracle Grid Infrastructure nodes where the Oracle Real Application Clusters database has instances configured.

8.  Log in to the system as the Oracle installation owner for the new Oracle Database release.

9.  Start SQL\*Plus in the new Oracle home from the admin directory in the new Oracle home directory.

    For example:

        $ cd $ORACLE_HOME/rdbms/admin
        $ pwd
        /u01/app/oracle/product/19.0.0/dbhome_1/rdbms/admin
        $ sqlplus

10. Copy the SPFILE.ORA or INIT.ORA file from the old Oracle home to the new Oracle home.

11. Connect to the database that you want to upgrade using an account with SYSDBA privileges:
        SQL> connect / as sysdba

12. Start the non-CDB Oracle Database in upgrade mode:

        SQL> startup upgrade

    If errors appear listing desupported initialization parameters, then make a note of the desupported initialization parameters and continue with the upgrade. Remove the desupported initialization parameters the next time you shut down the database.

    **Note:**

    Starting up the database in `UPGRADE` mode enables you to open a database based on an earlier Oracle Database release. It also restricts log-ins to `AS SYSDBA` sessions, disables system triggers, and performs additional operations that prepare the environment for the upgrade.

13. Exit SQL\*Plus.

    For example:

        SQL> EXIT

14. Run the Parallel Upgrade Utility (`catctl.pl`) script, using the upgrade options that you require for your upgrade.

    You can run the Parallel Upgrade Utility as a command-line shell command by using the `dbupgrade` shell command, which is located in `Oracle_home``/bin`. If you set the PATH environment variable to include `Oracle_home/bin`, then you can run the command directly from your command line. For example:

        $ dbupgrade -d /u01/app/oracle/19.1.0/dbhome_1

    **Note:**

    - When you run the Parallel Upgrade Utility command, use the `-d` option to specify the filepath for the target Oracle home. Use the` -l` option to specify the directory that you want to use for spool log files.

15. The database is shut down after a successful upgrade. Restart the instance so that you reinitialize the system parameters for normal operation. For example:

        SQL> STARTUP

    This restart, following the database shutdown, flushes all caches, clears buffers, and performs other housekeeping activities. These measures are an important final step to ensure the integrity and consistency of the upgraded Oracle Database software.

    **Note:**

    If you encountered a message listing desupported initialization parameters when you started the database, then remove the desupported initialization parameters from the parameter file before restarting it. If necessary, convert the `SPFILE` to a `PFILE`, so that you can edit the file to delete parameters.

16. Run `catcon.pl` to start `utlrp.sql`, and to recompile any remaining invalid objects.

    For example:

        $ORACLE_HOME/perl/bin/perl catcon.pl -n 1 -e -b utlrp -d '''.''' utlrp.sql

    Because you run the command using `-b utlrp`, the log file `utlrp0.log` is generated as the script is run. The log file provides results of the recompile.

17. Run `postupgrade_fixups.sql`. For example:

        SQL> @postupgrade_fixups.sql

    **Note:**

    If you did not specify to place the script in a different location, then it is in the default path `Oracle_base``/cfgtoollogs/``SID``/preupgrade`, where `Oracle_base` is your Oracle base home path, and `SID` is your unique database name.

18. Run `utlusts.sql`. The script verifies that all issues are fixed.

    For example:

        SQL> @$ORACLE_HOME/rdbms/admin/utlusts.sql

    The log file `utlrp0.log` is generated as the script is run, which provides the upgrade results. You can also review the upgrade report in `upg_summary.log`.

    To see information about the state of the database, run `utlusts.sql` as many times as you want, at any time after the upgrade is completed. If the `utlusts.sql` script returns errors, or shows components that do not have the status `VALID`, or if the version listed for the component is not the most recent release, then refer to the troubleshooting section in this guide.

19. Ensure that the time zone data files are current by using the `DBMS_DST PL/SQL` package to upgrade the time zone file. You can also adjust the time zone data files after the upgrade.

20. Exit from SQL\*Plus

    For example:

        SQL> EXIT

21. (Conditional) If you are upgrading an Oracle Real Application Clusters database, then use the following command syntax to upgrade the database configuration in Oracle Clusterware:

        srvctl upgrade database -db db-unique-name -oraclehome oraclehome

    In this syntax example, `db-unique-name` is the database name (not the instance name), and `oraclehome` is the Oracle home location in which the database is being upgraded. The `SRVCTL` utility supports long GNU-style options, in addition to short command-line interface (CLI) options used in earlier releases.

22. (Conditional) For Oracle RAC environments only, after you have upgraded all nodes, enter the following commands to set the initialization parameter value for CLUSTER_DATABASE to TRUE, and start the database, where `db_unique_name` is the name of the Oracle RAC database:

        ALTER SYSTEM SET CLUSTER_DATABASE=TRUE SCOPE=SPFILE;
        srvctl start database -db db_unique_name

Your database is now upgraded. You are ready to complete post-upgrade procedures.

**Caution:**

If you retain the old Oracle software, then never start the upgraded database with the old software. Only start Oracle Database using the start command in the new Oracle Database home.

Before you remove the old Oracle environment, relocate any data files in that environment to the new Oracle Database environment.

**See Also:**

[Oracle Database Administrator’s Guide](../admin/managing-data-files-and-temp-files.md) for information about relocating data files

**Parent topic:** [Upgrading Oracle Database](upgrading-db.md)
