Use this technique to upgrade CDB\$ROOT, PDB\$SEED, and all PDBS in the CDB in one upgrade operation.

Oracle recommends that you use this approach if you can schedule downtime, because it provides a direct procedure for upgrades and simplicity of maintenance. Using this procedure upgrades in parallel all the PDBs in the multitenant architecture container database, depending on your server’s available processors (CPUs).

**Note:**

When you upgrade the entire container using the In Parallel upgrade method, all the PDBs must be down. Perform the upgrade in a scheduled upgrade window so that you can bring all the PDBs down.

**Caution:**

- Always create a backup of existing databases before starting any configuration change.

- You cannot downgrade a database after you have set the compatible initialization parameter.

- Oracle strongly recommends that you upgrade your source and target databases to the most recent bundle patch or patch set update (BP or PSU) before starting an upgrade, and to the most recent release update before starting a downgrade.

1.  Ensure that you have a proper backup strategy in place.
2.  Open all PDBs.
    For example:

        SQL> alter pluggable database all open;
3.  Run the Pre-Upgrade Information Tool (`preupgrade.jar`), using the following syntax:
    `/java -jar ``$New_release_Oracle_home``/rdbms/admin/preupgrade.jar [TERMINAL|FILE|DIR outputdir] [TEXT|XML] [-c ``InclusionListOfPDBs``] [-C ``ExclusionListOfPDBs``]`
    Use space-delimitation for lists. On Linux and UNIX, define the list by placing the list inside single quotes:` '`. On Windows systems, define the list by placing the list inside double quotes` "`.

    For example, run the following command to run the Pre-Upgrade Information tool on PDBs PDB1 through PDB25, where you have set up an environment variable `$ORACLE_HOME_12.2` for your Oracle Database Oracle home in` /u01/app/ oracle/product/12.2.0/dbhome_1/`, and you have set up an environment variable `$ORACLE_HOME_19.1` for your new Oracle Database Oracle home in `/u01/app/oracle/product/19.1.0/dbhome_1/`:
    Linux and UNIX:

        java -jar $ORACLE_HOME_19.1/rdbms/admin/preupgrade.jar \
        -c 'pdb1 pdb2 pdb3 pdb4 pdb5 pdb6 pdb7 pdb8 pdb9 pdb10 pdb11 pdb12 pdb13\
        pdb14 pdb15 pdb16 pdb17 pdb18 pdb19 pdb20 pdb21 pdb22 pdb23 pdb24 pdb25'

    Windows:

        java -jar %ORACLE_HOME_19.1%/rdbms/admin/preupgrade.jar \
        -c "pdb1 pdb2 pdb3 pdb4 pdb5 pdb6 pdb7 pdb8 pdb9 pdb10 pdb11 pdb12 pdb13\
        pdb14 pdb15 pdb16 pdb17 pdb18 pdb19 pdb20 pdb21 pdb22 pdb23 pdb24 pdb25"

    **Note:**

    You must use Java 1.5 or later to run the Pre-Upgrade Information tool. By default, the Java releases in Oracle Database releases that you can upgrade directly support the tool.
4.  Review any generated fixup scripts and log files.
    By default, if ORACLE_BASE is defined, then the fixup files are placed in one of the following paths:

    - Linux and UNIX:

      `$ORACLE_BASE/cfgtoollogs/``db_unique_name``/preupgrade`

    - Windows

      `%ORACLE_BASE%\cfgtoollogs\``db_unique_name``\preupgrade`

    If ORACLE_BASE is not defined, then fixup files are placed in one of the following paths:

    - Linux and UNIX:

      `$ORACLE_HOME/cfgtoollogs/``db_unique_name``/preupgrade`

    - Windows:

      `%ORACLE_HOME\cfgtoollogs\``db_unique_name``\preupgrade`

    On multitenant architecture Oracle Databases, the Pre-Upgrade Information Tool also creates a consolidated `preupgrade_fixups.sql` script. You can run the consolidated fixup script by using `catcon.pl`. The consolidated fixup script runs on every container that was open at the time that you ran the `preupgrade.jar` command.
5.  Run the `preupgrade_fixups` script, or individual PDB scripts. The `preupgrade_fixups` SQL scripts resolve some of the issues reported by the `preupgrade` script.
    On multitenant environment Oracle Database deployments, you can run `preupgrade_fixups``pdb-name``.sql` scripts on the source database, where `pdb-name` is the PDB name. If you generate fixup scripts for PDBs, then the PDB name is added to the fixup filename.

    In addition to the individual PDB fixup scripts, you can use `catcon.pl` to run the consolidated `preupgrade_fixups.sql` script. The consolidated script runs on every container that was open at the time that you ran `preupgrade.jar`.

    **Note:**

    Because \$ is a reserved symbol on operating systems, the fixup script for PDB\$SEED is `preupgrade_fixups_pdb_seed.sql`.

    Complete any other preupgrade tasks that the Pre-Upgrade Information Tool identifies.
6.  (Conditional) for Oracle RAC databases, set the cluster database initialization parameter to false:
    For example;

        ALTER SYSTEM SET cluster_database=FALSE SCOPE=spfile;
7.  Shut down the database in the old Oracle home.
    For example, where `db_unique_name` is your database name:

    `$ srvctl stop database -d ``db_unique_name`
8.  Copy the `PFILE` or `SPFILE` from the old Oracle home to the new Oracle home
9.  Connect with SQL\*Plus:
        sqlplus / as sysdba
10. Bring the CDB\$ROOT instance into upgrade mode:
        STARTUP UPGRADE
11. Bring all PDBs into upgrade mode:
        ALTER PLUGGABLE DATABASE ALL OPEN UPGRADE;
12. Check the status of PDBs to confirm that they are ready to upgrade:
        SHOW PDBS

    For all PDBs, ensure that the status is set to MIGRATE.
13. Exit from SQL\*Plus, and change directory to the new Oracle home `$ORACLE_HOME/rdbms/admin`:
        SQL> EXIT
        $ ORACLE_HOME/bin
14. Start the upgrade using the Parallel Upgrade Utility (`catctl.pl`, using the shell command `dbupgrade`), where `-d` specifies the location of the directory:
        dbupgrade -d $ORACLE_HOME/rdbms/admin

    If you do not specify any parameters, then the Parallel Upgrade Utility runs the upgrade in parallel on the number of PDBs equivalent to the number of CPUs divided by 2. On a server with 64 CPUs, 64 divided by 2 equals 32 PDBs upgraded in parallel, carried out with two SQL processors for each PDB. CDB\$ROOT remains in NORMAL mode for the duration of the upgrade.
15. Confirm that the upgrade was successful by reviewing the `upg_summary.log` If necessary, review other logs.
16. Open all PDBs, so that you can recompile the databases:
        ALTER PLUGGABLE DATABASE ALL OPEN;
17. Exit from SQL\*Plus, and change directory to the new Oracle home path `$ORACLE_HOME/rdbms/admin`:
        SQL> EXIT
        cd $ORACLE_HOME/rdbms/admin
18. Run the `catcon.pl` script and the `postupgrade_fixups.sql` script that is supplied with the new release Oracle Database.
    The following example shows the command strings for running `catcon.pl`, using the `-n` parameter to specify one parallel processor for each PDB, using the `-d` parameter to specify the path where the preupgrade script that you want to run is located, using the `-l` parameter to specify the location where you want the scripts to place log files, and using the `-b` flag to specify the log file prefixes for the `postupgrade_fixups.sql` script:

        $ORACLE_HOME/perl/bin/perl $ORACLE_HOME/rdbms/admin/catcon.pl -n 1 -d \
        $ORACLE_HOME/cfgtoollogs/cdbupgr/preupgrade -l /home/oracle/upgrdDBA -b \
        postupgrade_fixups postupgrade_fixups.sql
19. Run `postupgrade_fixups.sql`.
    Non- CDB:

        SQL> @rdbms/admin/postupgrade_fixups.sql

    CDB:

        $ORACLE_HOME/perl/bin/perl catcon.pl -n 1 -e -b postupgradefixups -d '''.''' postupgradefixups.sql
20. Run `utlusts.sql` to verify that there are no upgrade issues.
    Non-CDB:

        SQL> @rdbms/admin/utlusts.sql

    CDB:

        $ORACLE_HOME/perl/bin/perl catcon.pl -n 1 -e -b utlu122s -d '''.''' utlusts.sql

    When you use `catcon.pl` to run `utlusts.sql`, the log file `utlu122s0.log` is generated. The log file provides the upgrade results. You can also review the upgrade report, `upg_summary.log`.

    To see information about the state of the database, run `utlusts.sql` as many times as you want, at any time after the upgrade is completed. If the `utlusts.sql` script returns errors, or shows components that do not have the status `VALID`, or if the version listed for the component is not the most recent release, then perform troubleshooting.
21. (Conditional) For Oracle RAC environments only, enter the following commands to set the initialization parameter value for CLUSTER_DATABASE to `TRUE`, and to start the Oracle RAC database, where `dbname` is the name of the Oracle RAC database:
        ALTER SYSTEM SET CLUSTER_DATABASE=TRUE SCOPE=SPFILE;
        srvctl start database -db db_unique_name

    Your database is now upgraded.

    **Caution:**

    If you retain the old Oracle software, then never start the upgraded database with the old software. Only start Oracle Database using the start command in the new Oracle Database home.

    Before you remove the old Oracle environment, relocate any data files in that environment to the new Oracle Database environment.

    **See Also:**

    [Oracle Database Administrator’s Guide](../admin/managing-data-files-and-temp-files.md) for information about relocating data files

**Parent topic:** [Upgrading Multitenant Architecture In Parallel](upgrading-multitenant-architecture-in-parallel.md)
