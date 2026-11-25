This chapter describes how to upgrade your existing database to Oracle Database 19c on Fujitsu BS2000. It gives you an overview about the steps required for the upgrade of a database and informs about actions, which are specific to the Fujitsu BS2000 platform.

Before you perform an upgrade, you must be familiar about upgrade preparation, space and backup requirements, release differences, handling `TIMESTAMP WITH TIME ZONE` data type, and other database upgrade concepts.

It is assumed that you have correctly installed Oracle Database 19c as explained in [“Oracle Database Installation and Deinstallation.”](oracle-database-installation-and-deinstallation.md)This chapter describes upgrading a database from Oracle Database 12c Release 2 (12.2) to Oracle Database 19c. The upgrade is done both in the normal BS2000 environment and in the POSIX shell. Oracle recommends that you be familiar with both these environments.

This chapter includes the following topics:

- Performing Preupgrade Procedures

- Performing Upgrade Procedures

- Performing Postupgrade Procedures

**Related Topics**

- [Oracle Database Upgrade Guide](../upgrd/intro-to-upgrading-oracle-database.md)

### 4.1 Performing Preupgrade Procedures

You must analyze your database before upgrading it to the new release. To analyze, run the `preupgrade.jar` Pre-Upgrade Information Tool from the environment of the database that you want to upgrade. Running the Pre-Upgrade Information Tool provides information about any issues that need to be fixed.

You must run the `preupgrade.jar` tool in the environment of the source database, for example, in the Oracle Database 12c Release 2 (12.2) environment. The database must be up and running.

The Pre-Upgrade Information Tool generates log files and fixup scripts that you can run, to resolve issues that are flagged in the source database. These log files and fixup scripts are generated in the POSIX file system. If `ORACLE_BASE` is defined, then the generated scripts and log files are created in the `$ORACLE_BASE/cfgtoollogs` directory. If `ORACLE_BASE` is not defined, then the generated scripts and log files are created in the `$ORACLE_HOME/cfgtoollogs` directory.

Perform the following steps in the environment of the source database:

1.  Log in to the DBA user ID of the source database.
2.  To avoid being prompted for many overflow acknowledgements on your screen, enter:
    `/MODIFY-TERMINAL-OPTIONS OVERFLOW-CONTROL=*NO-CONTROL`
3.  Change to the POSIX shell:
    `/START-POSIX-SHELL`
4.  Before you run the Pre-upgrade Information Tool, `preupgrade.jar` in the POSIX shell, set the Oracle environment variables `ORACLE_HOME` and `ORACLE_BASE` by executing the `.profile.oracle `file:
    `$ . ``oracle_home_path_12c_R2``/.profile.oracle`

    You must also set the `ORACLE_SID` environment variable to the `sid` of your Oracle Database instance. Use the following commands:

        $ ORACLE_SID=sid
        $ export ORACLE_SID

    **Note:**

    You must remember that the variable `BGJPAR` might not be defined. Oracle recommends to set the variable `BGJPAR` according to the value you find in the corresponding `ORAENV` file , `sid``.P.ORAENV`.
5.  Run the `preupgrade.jar` Pre-Upgrade Information Tool:
        $ $ORACLE_HOME/jdk/bin/java -jar oracle_home_path_19c/rdbms/admin/preupgrade.jar
6.  View and read through the resulting generated fixup scripts and log file, which are located in:
    - `$ORACLE_BASE/cfgtoollogs/``db_unique_name``/preupgrade` directory if` ORACLE_BASE` is defined.

    - `$ORACLE_HOME/cfgtoollogs/``db_unique_name``/preupgrade` directory if `ORACLE_BASE` is not defined.
7.  After you have reviewed the scripts, Oracle recommends that you execute `preupgrade_fixups.sql` on the source database. The `preupgrade_fixups.sql` script attempts to resolve issues reported by the preupgrade process. You must manually resolve the issues that cannot be resolved automatically by a fixup script.
8.  Shutdown the database and exit SQL\*Plus. Use the following commands:
        $ sqlplus /nolog
        SQL> connect / as sysdba
        SQL> shutdown immediate;
        SQL> exit
9.  Exit the POSIX shell:
    `$ exit`

    **Note:**

    Oracle recommends that you back up your Oracle database after running the Pre-Upgrade Information Tool and shutting down the database.

    You can find regular updates of the Pre-Upgrade Information tool on the My Oracle Support website. Refer to the [My Oracle Support Note 884522.1](https://support.oracle.com/epmos/faces/DocumentDisplay?id=884522.1) if you want to download and install a new release of the Pre-Upgrade information tool. The steps described in this note are valid for Fujitsu BS2000, too. The only difference is the procedure for unzipping the zip file.

    Transfer the zip file (with binary mode) to the POSIX file system of your BS2000 machine. Then unzip the zip file into the `$ORACLE_HOME/rdbms/admin` directory of Oracle Database 19c as follows:

        $ cd $ORACLE_HOME/rdbms/admin
        $ unzip -aa preupgrade_19_cbuild_nn_lf.zip -x preupgrade.jar
        $ unzip preupgrade_19_cbuild_nn_lf.zip preupgrade.jar

### 4.2 Performing Upgrade Procedures

Use the upgrade utility, `dbupgrade` to upgrade Oracle Database. As shell scripts and Perl scripts are supported only in the POSIX environment, you must change to the POSIX shell for performing some of the procedure.

The shell script `dbupgrade` is a wrapper for the parallel upgrade utility `catctl.pl`, which is based on Perl.

All the steps in this phase must be performed in the new Oracle Database 19c environment. For some steps you have to change to the POSIX shell.

Perform the following upgrade steps:

1.  Log in to the DBA user ID of the database to be upgraded.
2.  To avoid being prompted for many overflow acknowledgements on your screen, enter:
    `/MODIFY-TERMINAL-OPTIONS OVERFLOW-CONTROL=*NO-CONTROL`
3.  Enter the following command to create an Oracle Database 19c `INIT.ORA` file and an Oracle Database 19c` ORAENV` file. The original files will be saved by the `$ORACINST.INSTALL.P.DBA` procedure with the suffix `.OLD`. Use the following commands:
        /CALL-PROCEDURE $ORACINST.INSTALL.P.DBA,(sid,jobclass,UPDATE=YES)
4.  Modify the newly created files according to your requirements. For example, change the values of `PROCESSES` or `DB_CACHE_SIZE` in the `INIT.ORA` file.
5.  Set the parameters in the `INIT.ORA` file as recommended by the Pre-Upgrade Information Tool. Ensure that the `COMPATIBLE` initialization parameter is explicitly set to 12.2.0 or higher.
6.  Change to the POSIX shell. Use the following command:
    `/START-POSIX-SHELL`
7.  Before you run SQL\*Plus in the POSIX shell you must set some environment variables. For example, `ORACLE_HOME` and `ORACLE_BASE`. To set these variables, run the `.profile.oracle` file that is located in the `ORACLE_HOME` directory of the Oracle Database 19c software installation:
    `$ . ``oracle_home_path_19c``/.profile.oracle`
8.  Set the `ORACLE_SID` environment variable to the `sid` of your Oracle Database instance:
        $ ORACLE_SID=sid
        $ export ORACLE_SID

    **Note:**

    Ensure that you define the `BGJPAR` variable. Oracle recommends to set the `BGJPAR` variable to the corresponding value in the `ORAENV` file, `sid``.P.ORAENV`.
9.  Start up the instance in upgrade mode as follows:
        $ sqlplus /nolog
        SQL> connect / as sysdba
        SQL> startup upgrade
        SQL> exit
10. Run the shell script for upgrade as follows:
        $ $ORACLE_HOME/bin/dbupgrade -l $HOME/logs

    The `–l` option allows you to specify the directory where you want to write the upgrade log files.
    **See Also:**

    [Oracle Database Upgrade Guide](../upgrd/intro-to-upgrading-oracle-database.md) for other options of the upgrade utility, `dbupgrade`.
    The upgraded database is shut down after running `dbupgrade`.
11. Restart the instance to reinitialize the system parameters for normal operation:
        $ sqlplus /nolog
        SQL> connect / as sysdba
        SQL> startup
12. Run the `catcon.pl` script to start `utlrp.sql`, and to recompile any remaining stored PL/SQL and Java code. For example:
    `$ORACLE_HOME/perl/bin/perl catcon.pl -n 1 -e -b utlrp -l $HOME/logs -d '''.''' utlrp.sql`
    When you run the command using `-b utlrp`, the log file `utlrp0.log` is generated as the script is run. The log file provides the recompilation results.
13. Run the `postupgrade_fixups.sql` script. For example:
    `SQL> @postupgrade_fixups.sql`
14. Run `utlusts.sql`, the Post-Upgrade Status Tool to display a summary of the upgrade results:
    `SQL> @$ORACLE_HOME/rdbms/admin/utlusts.sql TEXT`

    If the `utlusts.sql` script returns errors, or shows components that do not contain the most recent release, or do not have the `VALID` status, then refer to [Oracle Database Upgrade Guide](../upgrd/troubleshooting-oracle-database-upgrade.md) for troubleshooting.
15. To query invalid objects, execute SQL queries similar to:
        SQL> SELECT count(*) FROM dba_objects WHERE status='INVALID';
        SQL> SELECT distinct object_name FROM dba_objects WHERE status='INVALID';

Your database is now upgraded to Oracle Database 19c.

### 4.3 Performing Postupgrade Procedures

You must complete the following tasks after upgrading to Oracle Database 19c:

- Gathering Statistics

- Migrating to Unified Auditing

#### Gathering Statistics

Oracle recommends to gather dictionary statistics after upgrading the database. Execute the following SQL statement:

    SQL> execute dbms_stats.gather_dictionary_stats;

After an upgrade Oracle strongly recommends that you regather fixed object statistics after you have run representative workloads. Execute the following SQL statement:

    SQL> execute dbms_stats.gather_fixed_objects_stats;

#### Migrating to Unified Auditing

Oracle Database 19c supports Unified Auditing. After upgrading to Oracle Database 19c, the Unified Auditing option is not enabled.

**See Also:**

- [“About Unified Auditing”](unified-auditing.md) for more information about enabling Unified Auditing

- [Oracle Database Upgrade Guide](../spucs/recommended-and-best-practices-complete-upgrading-oracle-database.md) for more information about migrating to Unified Auditing
