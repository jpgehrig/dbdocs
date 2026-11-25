## Rerunning Upgrades for Oracle Database

Use these options to rerun upgrades.

- About Rerunning Upgrades for Oracle Database
  Oracle provides the features listed here to rerun or restart Oracle Database upgrades, including after failed phases.
- Rerunning Upgrades with the Upgrade (catctl.pl) Script
  You can fix upgrade issues and then rerun the upgrade with the `catctl.pl` script, or the `dbupgrade` shell command.
- Options for Rerunning the Upgrade for Multitenant Databases (CDBs)
  If you want to rerun upgrades on Oracle Database using multitenant database architecture, then you have four options.
- [Restarting the Upgrade from a Specific Phase that Failed Using -p](restarting-upgrade-specific-phase-that-failed-using-p.md)
  Use this option to complete an upgrade after fixing errors.

**Parent topic:** [Upgrading Oracle Database Manually Using Parallel Upgrade Utility](upgrading-oracle-database-parallel-upgrade-utiility-replay-upgrade.md)

### About Rerunning Upgrades for Oracle Database

Oracle provides the features listed here to rerun or restart Oracle Database upgrades, including after failed phases.

#### Parallel Upgrade Utility and Restarts or Reruns

You can re-run or restart Oracle Database upgrade phases by using the Parallel Upgrade Utility (`catctl.pl`) script . You can also run commands on PDBs that failed to upgrade in an initial attempt, so that you can complete the upgrade.

#### Parallel Upgrade Utility Resume Option

With the Resume option for Parallel Upgrade Utility, you are not required to identify failed or incomplete phases when you rerun or restart the upgrade. When you use the Parallel Upgrade Utility using the resume option (`-R`), the utility automatically detects phases from the previous upgrade that are not completed successfully. The Parallel Upgrade Utility then reruns or restarts just these phases that did not complete successfully, so that the upgrade is completed. Bypassing steps that already completed successfully reduces the amount of time it takes to rerun the upgrade.

To use the Resume option, run the Parallel Upgrade Utility using the `-R` parameter. For example:

    $ORACLE_HOME/perl/bin/perl catctl.pl -L plist.txt -n 4 -N 2 -R -l $ORACLE_HOME/cfgtoollogs catupgrd.sql

You can rerun the entire upgrade at any time, regardless of which phase you encountered a failure in your upgrade. If you plan to rerun the entire upgrade, instead of rerunning only failed phases, then run the Parallel Upgrade Utility without using the Resume (`-R`) option.

**Parent topic:** Rerunning Upgrades for Oracle Database

### Rerunning Upgrades with the Upgrade (catctl.pl) Script

You can fix upgrade issues and then rerun the upgrade with the `catctl.pl` script, or the `dbupgrade` shell command.

**Note:**

Starting with Oracle Database 12c, Release 1 (12.1), non-CDB architecture is deprecated. It can be desupported in a future release.

1.  Shut down the database. For a non-CDB and a CDB, the syntax is the same.

        SQL> SHUTDOWN IMMEDIATE

2.  Restart the database in `UPGRADE` mode.

    For a non-CDB:

        SQL> STARTUP UPGRADE

    For a CDB:

        SQL> STARTUP UPGRADE
        SQL> alter pluggable database all open upgrade;

3.  Rerun the Parallel Upgrade utility (`catctl.pl`, or `dbupgrade` shell command).

    You can rerun the Parallel Upgrade Utility as many times as necessary.

    With CDBs, you can use the Resume option (`-R`) to rerun the Parallel Upgrade Utility. The script resumes the upgrades from failed phases.

    For example:

        $ORACLE_HOME/perl/bin/perl catctl.pl -n 4 -R -l $ORACLE_HOME/cfgtoollogs catupgrd.sql

    You can also provide the name of one or more specific PDBs on which you want to rerun the upgrade.

    For example, this command reruns the upgrade on the PDB named `cdb1_pdb1`:

        $ORACLE_HOME/perl/bin/perl catctl.pl -n 4 -R -l $ORACLE_HOME/cfgtoollogs -c 'cdb1_pdb1' catupgrd.sql

    You can use the `dbupgrade` shell command to run the same commands:

        dbupgrade -n 4 -R -l $ORACLE_HOME/diagnostics
        dbupgrade -n 4 -R -l $ORACLE_HOME/diagnostics -c 'cdb1_pdb1'

4.  Run `utlusts.sql`, the Post-Upgrade Status Tool, which provides a summary of the status of the upgrade in the spool log. You can run `utlusts.sql` any time before or after you complete the upgrade, but not during the upgrade.

    In a non-CDB:

        SQL> @$ORACLE_HOME/rdbms/admin/utlusts.sql

    In a CDB:

        $ORACLE_HOME/perl/bin/perl catcon.pl -n 1 -e -b utlu122s -d '''.''' utlusts.sql

    If the `utlusts.sql` script returns errors or shows components that are not `VALID` or not the most recent release, then follow troubleshooting procedures for more information.

5.  Run `utlrp.sql` to recompile any remaining stored PL/SQL and Java code.

        $ORACLE_HOME/perl/bin/perl catcon.pl -n 1 -e -b utlrp -d '''.''' utlrp.sql

    The script generates the log file `utlrp0.log` , which shows the results of the re-compilations.

    Use the following SQL commands to verify that all expected packages and classes are valid,

    In a single PDB (`cdb1_pdb1` in this example), open the PDB in normal mode as follows:

        alter pluggable database cdb1_pdb1 open;

    Run `catcon.pl` to start` utlrp.sql` in the PDB to recompile any remaining stored PL/SQL and Java code. Use the following syntax:

        $ORACLE_HOME/perl/bin/perl catcon.pl -n 1 -e -b utlrp -d '''.''' -c 'cdb1_pdb1'
         utlrp.sql

    In a non-CDB:

        SQL> SELECT count(*) FROM dba_invalid_objects;
        SQL> SELECT distinct object_name FROM dba_invalid_objects;

    In an entire CDB:

        SQL> ALTER SESSION SET CONTAINER = "CDB$ROOT"
        SQL> SELECT count(*) FROM dba_invalid_objects;
        SQL> SELECT distinct object_name FROM dba_invalid_objects;
        SQL> ALTER SESSION SET CONTAINER = "PDB$SEED"
        SQL> SELECT count(*) FROM dba_invalid_objects;
        SQL> SELECT distinct object_name FROM dba_invalid_objects;
        SQL> ALTER SESSION SET CONTAINER = "cdb1_pdb1"
        SQL> SELECT count(*) FROM dba_invalid_objects;
        SQL> SELECT distinct object_name FROM dba_invalid_objects;

6.  Run `utlusts.sql` again to verify that all issues have been fixed.

    In a non-CDB:

        SQL> @$ORACLE_HOME/rdbms/admin/utlusts.sql

    In a CDB:

        $ORACLE_HOME/perl/bin/perl catcon.pl -n 1 -e -b utlu122s -d '''.''' utlusts.sql

7.  Exit SQL\*Plus.

8.  If you are upgrading a cluster database from Release 11.2, then upgrade the database configuration in Oracle Clusterware using the following command syntax, where `db-unique-name` is the database name assigned to it (not the instance name), and `Oracle_home` is the Oracle home location in which the database is being upgraded.

        $ srvctl upgrade database -d db-unique-name -o Oracle_home

Your database is now upgraded. You are ready to complete post-upgrade tasks for Oracle Database.

**Related Topics**

- Options for Rerunning the Upgrade for a Multitenant Database (CDB)
- [Troubleshooting the Upgrade for Oracle Database](troubleshooting-oracle-database-upgrade.md)
- [Post-Upgrade Tasks for Oracle Database](post-upgrade-tasks-oracle-database.md)

**Parent topic:** Rerunning Upgrades for Oracle Database

### Options for Rerunning the Upgrade for Multitenant Databases (CDBs)

If you want to rerun upgrades on Oracle Database using multitenant database architecture, then you have four options.

- Rerun the Entire Upgrade for the CDB
  If several different issues occur during the first upgrade attempt, then use this procedure to re-run the entire upgrade.
- Rerun the Upgrade Only on Specified PDBs
  You can rerun upgrades on specified multitenant containers by running the Parallel Upgrade Utility with either the Resume option (`-R`), or with the exclusion list option (`-C`).
- Rerun the Upgrade While Other PDBs Are Online
  You can rerun PDB upgrades by using the Parallel Upgrade Utility Resume option, or by explicitly including or excluding online PDBs using with inclusion or exclusion lists.
- Rerun the Upgrade Using an Inclusion List to Specify a CDB or PDBs
  Use this example as a model for rerunning an upgrade on a PDB by using an inclusion list.

**Parent topic:** Rerunning Upgrades for Oracle Database

#### Rerun the Entire Upgrade for the CDB

If several different issues occur during the first upgrade attempt, then use this procedure to re-run the entire upgrade.

This example demonstrates running the upgrade again on the `CDB$ROOT`, `PDB$SEED` and all PDBs after correcting for a problem occurring during the initial upgrade attempt, such as running out of shared pool.

1.  Start the upgrade again. For example:

        SQL> startup upgrade;
        alter pluggable database all open upgrade;

2.  Run the Parallel Upgrade Utility (`catctl.pl`, or the `dbupgrade` shell script. For example:

        cd $ORACLE_HOME/bin/
        ./dbupgrade -d $ORACLE_HOME/rdbms/admin -l $ORACLE_HOME/rdbms/log

    The upgrade runs again on all the containers, including `CDB$ROOT` , `PDB$SEED`, and all PDBs in the CDB.

**Parent topic:** Options for Rerunning the Upgrade for Multitenant Databases (CDBs)

#### Rerun the Upgrade Only on Specified PDBs

You can rerun upgrades on specified multitenant containers by running the Parallel Upgrade Utility with either the Resume option (`-R`), or with the exclusion list option (`-C`).

In both the examples that follow, the multitenant container database contains five PDBs. All upgrades ran successfully except for `CDB1_PDB1` and `CDB1_PDB2`, which failed with an upgrade error. To run the upgrade on these two containers, you shut down the entire multitenant database and restart only the PDBs you want to upgrade.

**Note:**

Parallel Upgrade Utility parameters are case-sensitive.

Example 4-28 Rerunning Upgrades With the Resume Option

You can use the Parallel Upgrade Utility Resume parameter option `-R` to rerun the upgrade only on one or more multitenant containers (CDBs).

In the following example, the upgrade script detects that it should run on `CDB1_PDB1` and `CDB1_PDB2` containers only.

1.  Shut down the multitenant database, start up the database in upgrade mode, and then start up the PDBs on which the upgrade did not complete. For example:

        SQL> shutdown immediate;
              startup upgrade;
              alter pluggable database CDB1_PDB1 open upgrade;
              alter pluggable database CDB1_PDB2 open upgrade;

2.  Show the CDB and PDB status:

         SQL> show pdbs

               CON_ID CON_NAME                       OPEN MODE  RESTRICTED
               ---------- ------------------------------ ---------- ----------
                   2 PDB$SEED                       MIGRATE    YES
                   3 CDB1_PDB1                      MIGRATE    YES
                   4 CDB1_PDB2                      MIGRATE    YES
                   5 CDB1_PDB3                      MOUNTED
                   6 CDB1_PDB4                      MOUNTED
                   7 CDB1_PDB5                      MOUNTED

3.  Rerun the upgrade. The upgrade automatically detects from the previous upgrade logs that CDB\$ROOT and PDB\$SEED are upgraded successfully. The upgrade bypasses CDB\$ROOT and PDB\$SEED, and only runs on CDB1_PDB1 and CDB_PDB2. The command example here is for Linux/UNIX systems:

        cd $ORACLE_HOME/bin
        ./dbupgrade -d $ORACLE_HOME/rdbms/admin -l $ORACLE_HOME/cfgtoollogs -R

The Parallel Upgrade Utility completes the upgrade on `CDB1_PDB1` and `CDB1_PDB2`.

Example 4-29 Rerunning Upgrades With an Exclusion List

An exclusion list contains containers that you do not want to upgrade. An exclusion list uses the Parallel Upgrade Utility `-C` parameter option. Run the Parallel Upgrade utility by changing directory to `Oracle_home``/rdbms/admin/` and running the utility in Perl using `catctl.pl`, or by changing directory to `Oracle_home``/bin` and running the command-line script, `dbupgrade -C`. This method is useful when you have many PDBs on which you want to rerun the upgrade.

In this following example, you provide an exclusion list to exclude the upgrade script from running on containers where you do not require it to run.

1.  Shut down the multitenant database, start up the database in upgrade mode, and then start up the PDBs on which the upgrade did not complete. For example:

        SQL> shutdown immediate;
              startup upgrade;
              alter pluggable database CDB1_PDB1 open upgrade;
              alter pluggable database CDB1_PDB2 open upgrade;

2.  Show the CDB and PDB status:

         SQL> show pdbs

               CON_ID CON_NAME                       OPEN MODE  RESTRICTED
               ---------- ------------------------------ ---------- ----------
                   2 PDB$SEED                       MIGRATE    YES
                   3 CDB1_PDB1                      MIGRATE    YES
                   4 CDB1_PDB2                      MIGRATE    YES
                   5 CDB1_PDB3                      MOUNTED
                   6 CDB1_PDB4                      MOUNTED
                   7 CDB1_PDB5                      MOUNTED

3.  Rerun the upgrade, excluding `CDB$ROOT` and `PDB$SEED` from the upgrade in a space-delimited exclusion list that you specify with single quote marks. The command example here is for Linux/UNIX systems:

        $ORACLE_HOME/bin/dbupgrade -d $ORACLE_HOME/rdbms/admin -l $ORACLE_HOME/rdbms/log -C 'CDB$ROOT PDB$SEED'

The upgrade reruns, and completes on `CDB1_PDB1` and `CDB1_PDB2`.

**Note:**

For Windows, you must specify the `-C` option exclusion list by using with double quote marks to specify the exclusion list. For example:

    ... -C "CDB$ROOT PDB$SEED"

**Parent topic:** Options for Rerunning the Upgrade for Multitenant Databases (CDBs)

#### Rerun the Upgrade While Other PDBs Are Online

You can rerun PDB upgrades by using the Parallel Upgrade Utility Resume option, or by explicitly including or excluding online PDBs using with inclusion or exclusion lists.

Use these examples as a model for running upgrades on PDBs, where you want to rerun upgrades on some PDBs while other PDBs are open.

In the examples, the upgrade failed in containers `CDB1_PDB1` and `CDB1_PDB2`, but succeeded in containers `CDB1_PDB3`, `CDB1_PDB4`, and `CDB1_PDB5`.

You start up `CDB$ROOT` in normal mode. You find that the following containers are online: `CDB1_PDB3`, `CDB1_PDB4`, and `CDB1_PDB5` . You review the upgrade logs for `CDB1_PDB3`, `CDB1_PDB4`, and `CDB1_PDB5` and bring these containers online.

Example 4-30 Rerunning Upgrades on PDBs Using the Resume Option

The following example shows how to complete the upgrade for `CDB1_PDB1` and `CDB1_PDB2` by using the Parallel Upgrade Utility Resume option. The Resume option excludes PDBs that are already upgraded:

1.  Bring up `CDB$ROOT` in normal mode, and open `CDB1_PDB1` and `CDB1_PDB2` in upgrade mode. `CDB1_PDB3`, `CDB1_PDB4`, `CDB1_PDB5` are in normal mode. For example:

        SQL> startup;
              alter pluggable database CDB1_PDB1 open upgrade;
              alter pluggable database CDB1_PDB2 open upgrade;
              alter pluggable database cdb1_pdb3 open;
              alter pluggable database cdb1_pdb4 open;
              alter pluggable database cdb1_pdb5 open;

2.  Use the SQL command `show pdbs` to show the status of PDBs. For example:

        SQL> show pdbs

                CON_ID CON_NAME                       OPEN MODE  RESTRICTED
                ---------- ------------------------------ ---------- ----------
                     2 PDB$SEED                       READ ONLY  NO
                     3 CDB1_PDB1                      MIGRATE    YES
                     4 CDB1_PDB2                      MIGRATE    YES
                     5 CDB1_PDB3                      READ WRITE NO
                     6 CDB1_PDB4                      READ WRITE NO
                     7 CDB1_PDB5                      READ WRITE NO

3.  Rerun the upgrade, excluding `CDB$ROOT` from the upgrade, using the Parallel Upgrade Utility command-line script `dbupgrade`.

        cd $ORACLE_HOME/bin
        ./dbupgrade -d $ORACLE_HOME/rdbms/admin/ -l $ORACLE_HOME/cfgtoollogs -R

    Because you run the upgrade using the Resume option, the Parallel Upgrade Utility checks the logs and identifies that `CDB1_PDB1` and `CDB1_PDB2` are the only two containers in `CDB1` that are not upgraded. The upgrade script runs on just those two PDBs. The upgrade does not rerun on `PDB$SEED`, `CDB$ROOT`, `CDB_PDB3`, `CDB_PDB4`, and `CDB_PDB5`.

Example 4-31 Rerunning Upgrades on PDBs Using Exclusion Lists

The following example shows how to complete the upgrade for `CDB1_PDB1` and `CDB1_PDB2` by using an exclusion list to exclude the PDBs on which you do not want the upgrade script to run:

1.  Bring up `CDB$ROOT` in normal mode, and open `CDB1_PDB1` and `CDB1_PDB2` in upgrade mode. `CDB1_PDB3`, `CDB1_PDB4`, `CDB1_PDB5` are in normal mode. For example:

        SQL> startup;
              alter pluggable database CDB1_PDB1 open upgrade;
              alter pluggable database CDB1_PDB2 open upgrade;
              alter pluggable database cdb1_pdb3 open;
              alter pluggable database cdb1_pdb4 open;
              alter pluggable database cdb1_pdb5 open;

2.  Use the SQL command `show pdbs` to show the status of PDBs. For example:

        SQL> show pdbs

                CON_ID CON_NAME                       OPEN MODE  RESTRICTED
                ---------- ------------------------------ ---------- ----------
                     2 PDB$SEED                       READ ONLY  NO
                     3 CDB1_PDB1                      MIGRATE    YES
                     4 CDB1_PDB2                      MIGRATE    YES
                     5 CDB1_PDB3                      READ WRITE NO
                     6 CDB1_PDB4                      READ WRITE NO
                     7 CDB1_PDB5                      READ WRITE NO

3.  Rerun the upgrade, excluding `CDB$ROOT` from the upgrade, using the Parallel Upgrade Utility command-line script `dbupgrade`:

        cd $ORACLE_HOME/bin
        ./dbupgrade -d $ORACLE_HOME/rdbms/admin -l $ORACLE_HOME/cfgtoollogs -R -C 'CDB$ROOT'

    The Parallel Upgrade Utility runs with the Resume option (`-R`), and identifies from the logs that CDB1_PDB1 and

    CDB1_PDB2 have not completed the upgrade. Because the Parallel Upgrade Utility runs with the Exclude option (-C), and you specify that `CDB$ROOT` is excluded, the upgrade script is also explicitly excluded from running on `CDB$ROOT`.

    For Windows, when you run the Parallel Upgrade Utility with the Exclude option (`-C`), you must specify the targets `-C` option using double quotes around the CDB root name and PDB seed name. For example:

        . . . -C "CDB$ROOT PDB$SEED"

4.  The upgrade reruns and completes on `CDB1_PDB1` and `CDB1_PDB2`.

**Parent topic:** Options for Rerunning the Upgrade for Multitenant Databases (CDBs)

#### Rerun the Upgrade Using an Inclusion List to Specify a CDB or PDBs

Use this example as a model for rerunning an upgrade on a PDB by using an inclusion list.

You can use an inclusion list to specify a list of CDBs and PDBs where you want to re-run an upgrade, and exclude nodes not on the inclusion list. Specify the inclusion list by running the Parallel Upgrade Utility with the inclusion option (`-c`), followed by a space-delimited list designated by single quotes of the containers that you want to upgrade.

In the examples, the upgrade failed in containers CDB1_PDB1 and CDB1_PDB2, but succeeded in containers CDB1_PDB3, CDB1_PDB4, and CDB1_PDB5. You start up CDB\$ROOT in normal mode. You find that the following containers are online: CDB1_PDB3, CDB1_PDB4, and CDB1_PDB5 . You review the upgrade logs for CDB1_PDB3, CDB1_PDB4, and CDB1_PDB5 and bring these containers online.

Example 4-32 Rerunning Upgrades on PDBs Using an Inclusion List

For example:

1.  Bring up `CDB$ROOT` in normal mode, and open `CDB1_PDB1` and `CDB1_PDB2` in upgrade mode. `CDB1_PDB3`, `CDB1_PDB4`, `CDB1_PDB5` are in normal mode. For example:

        SQL> startup;
              alter pluggable database CDB1_PDB1 open upgrade;
              alter pluggable database CDB1_PDB2 open upgrade;
              alter pluggable database cdb1_pdb3 open;
              alter pluggable database cdb1_pdb4 open;
              alter pluggable database cdb1_pdb5 open;

2.  Use the SQL command `show pdbs` to show the status of PDBs. For example:

        SQL> show pdbs

                CON_ID CON_NAME                       OPEN MODE  RESTRICTED
                ---------- ------------------------------ ---------- ----------
                     2 PDB$SEED                       READ ONLY  NO
                     3 CDB1_PDB1                      MIGRATE    YES
                     4 CDB1_PDB2                      MIGRATE    YES
                     5 CDB1_PDB3                      READ WRITE NO
                     6 CDB1_PDB4                      READ WRITE NO
                     7 CDB1_PDB5                      READ WRITE NO

3.  Rerun the Parallel Upgrade Utility with the inclusion (-c) option, followed by a space-delimited inclusion list that you specify with single quote marks. This option runs the upgrade only on the PDBs that you list in the inclusion list.

    For example:

        cd $ORACLE_HOME/bin
        ./dbupgrade -d $ORACLE_HOME/rdbms/admin -l ORACLE_HOME/cfgtoollogs -R -c 'CDB1_PDB1 CDB1_PDB2'

    For Windows, when you run the Parallel Upgrade Utility with the inclusion option, you must specify the `-c` option targets by using double quotes around the inclusion list. For example:

        . . . -C "CDB1_PDB1 CDB1_PDB2"

4.  The upgrade reruns and completes on `CDB1_PDB1` and `CDB1_PDB2`.

**Parent topic:** Options for Rerunning the Upgrade for Multitenant Databases (CDBs)
