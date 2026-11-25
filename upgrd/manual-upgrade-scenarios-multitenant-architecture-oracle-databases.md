## Manual Upgrade Scenarios for Multitenant Architecture Oracle Databases

To prepare for manual upgrades, review the manual upgrade scenarios and procedures for Oracle Database deployed with multitenant architecture.

Starting with Oracle Database 12c, multitenant architecture enables Oracle Database deployments using multitenant container databases (CDB) that contain pluggable databases (PDBs). All Oracle Database releases earlier than Oracle Database 12c Release 1 (12.1.0.1) use non-CDB architecture.

**Caution:**

You cannot downgrade a database after you have set the compatible initialization parameter to 12.1.0.2 or later releases. A downgrade is possible for a pluggable database (PDB) only if the compatibility is set to 12.1.0.1. There can still be restrictions on downgrading.

Before starting an upgrade, and before starting a downgrade, Oracle strongly recommends that you upgrade your source and target databases to the most recent release update or release update revision.

- About Oracle Multitenant Oracle Database Upgrades
  You can upgrade Oracle Databases installed on multitenant architecture either in parallel, or in sequence.
- Coordinate Upgrades of Proxy PDBs with Multitenant Upgrades
  Coordinate upgrades of the CDB so that proxy PDB and PDB targets are the same version.
- Manually Upgrading a Multitenant Container Oracle Database (CDB)
  The procedure in this section provides steps for upgrading a CDB manually using a command-line procedure.
- About Upgrading PDBs Using the Parallel Upgrade Utility with Priority Lists
  In Oracle Database 12.2 and later releases, you can upgrade PDBs using a priority list to upgrade a set of PDBs ahead of other PDBs, and you can modify that upgrade priority.
- About PDB Upgrades Using Priority Lists, Inclusion Lists, and Exclusion Lists
  To control how your pluggable databases (PDBs) are upgraded, you can use inclusion and exclusion lists with priority lists.
- Upgrading Multitenant Architecture In Parallel
  Use this technique to upgrade multitenant architecture Oracle Database releases (Oracle Database 12c Release 1 (12.1.0.1) and later by upgrading container databases (CDBs), and then upgrading multiple pluggable databases (PDBs) in parallel.
- Upgrading Multitenant Architecture Sequentially Using Unplug-Plug
  To upgrade pluggable databases (PDBs) that are in an earlier release multitenant container databases (CDBs), Oracle Database Release 12c (12.1.0.1) and later, you can unplug the PDBs from the earlier release CDB, and plug the PDBs into the later release CDB.

**Related Topics**

- [Oracle Multitenant Administrator's Guide](../multi/introduction-to-the-multitenant-architecture.md)

**Parent topic:** [Upgrading Oracle Database Manually Using Parallel Upgrade Utility](upgrading-oracle-database-parallel-upgrade-utiility-replay-upgrade.md)

### About Oracle Multitenant Oracle Database Upgrades

You can upgrade Oracle Databases installed on multitenant architecture either in parallel, or in sequence.

You can upgrade multitenant architecture systems by using AutoUpgrade, or Oracle Restart upgrade, or by using Parallel Upgrade Utility to carry out manual upgrades. Starting with Oracle Database 21c, Replay Upgrade is the default option for upgrading PDBs.

There are two techniques for upgrading Oracle Databases using the multitenant architecture:

- In parallel. With this technique, you carry out one upgrade operation that upgrades the CDB, and then upgrades the PDBs in parallel.

- Sequentially. With this technique, you install a new release CDB, prepare and unplug PDBs from the earlier release CDB, plug the PDBs into a later release CDB, and then complete the upgrade for each PDB.

The following sections provide a high-level summary of each upgrade technique.

#### Upgrading Oracle Multitenant In Parallel

With the In Parallel technique, you first upgrade `CDB$ROOT` using the Parallel Upgrade Utility (`catctl.pl`), using parameters to set the degree of parallel processing and availability:

- The `-n` parameter defines how many parallel processes run the upgrade, up to 8.

- The `-M` parameter determines if the `CDB$ROOT` stays in `UPGRADE` mode through the entire upgrade, or becomes available for access after the CDB upgrade is complete. If you do not run the upgrade with the `-M` parameter, then when the `CDB$ROOT` upgrade is complete, PDBs then become available for access as soon as each PDB completes its upgrade. If you run the upgrade with the `–M` parameter, then `CDB$ROOT` stays in `UPGRADE` mode, and PDBs do not become available until upgrade of all PDBs is complete.

#### Upgrading Oracle Multitenant In Sequence

With the In Sequence technique, you install the new release multitenant architecture CDB. Next, in the earlier release multitenant architecture CDB, you run AutoUpgrade preupgrade scripts to prepare one or more PDBs to upgrade, and shut them down. You then unplug PDBs, plug them into the new release multitenant architecture CDB, and complete the upgrade sequentially for each PDB.

**Parent topic:** Manual Upgrade Scenarios for Multitenant Architecture Oracle Databases

### Coordinate Upgrades of Proxy PDBs with Multitenant Upgrades

Coordinate upgrades of the CDB so that proxy PDB and PDB targets are the same version.

During upgrades, upgrade of a Proxy PDB does not upgrade its corresponding target PDB. Upgrade of the target PDB has to be done separately.

**Parent topic:** Manual Upgrade Scenarios for Multitenant Architecture Oracle Databases

### Manually Upgrading a Multitenant Container Oracle Database (CDB)

The procedure in this section provides steps for upgrading a CDB manually using a command-line procedure.

You must complete the following steps before using this procedure:

- Install the new release software for Oracle Database

- Prepare the new Oracle home

- Run the Pre-Upgrade Information Tool

Oracle Database 12c introduced multitenant architecture, which enables Oracle Database to function as a multitenant container database (CDB) with pluggable databases. You can upgrade the CDB using DBUA, and in the process, upgrade all the pluggable databases attached to the CDB at the same time. Or, after you install the software for Oracle Database and prepare the new Oracle home, you can proceed with a manual, command-line upgrade.

1.  If you have not done so, run the Pre-Upgrade Information Tool. Review the Pre-Upgrade Information tool output and correct all issues noted in the output before proceeding.

2.  Back up the source database.

3.  If you have not done so, prepare the new Oracle home.

4.  (Conditional) For Oracle RAC environments only, enter the following commands to set the initialization parameter value for CLUSTER_DATABASE to FALSE:

        ALTER SYSTEM SET CLUSTER_DATABASE=FALSE SCOPE=SPFILE;

    Restart the database after changing the CLUSTER_DATABASE parameter.

5.  Shut down the database. (The syntax is the same for a non-CDB and a CDB.)

        SQL> SHUTDOWN IMMEDIATE

    **Note:**

    To close a PDB, you can specify it from the CDB root: `alter pluggable database ``PDBname`` close`.

6.  If your operating system is Windows, then complete the following steps:

    1.  Stop the `OracleService ``SID` Oracle service of the database you are upgrading, where `SID` is the instance name. For example, if your `SID` is `ORCL`, then enter the following at a command prompt:

            C:\> NET STOP OracleServiceORCL

    2.  Delete the Oracle service at a command prompt using `ORADIM`.

        If your `SID` is `ORCL`, then enter the following command, substituting your SID for `SID`.

            C:\> ORADIM -DELETE -SID ORCL

    3.  Create the service for the new release Oracle Database at a command prompt using the `ORADIM` command of the new Oracle Database release.

        For example:

            C:\> ORADIM -NEW -SID SID -SYSPWD PASSWORD -MAXUSERS USERS
                 -STARTMODE AUTO -PFILE ORACLE_HOME\DATABASE\INITSID.ORA

        Most Oracle Database services log on to the system using the privileges of the Oracle Home User. The service runs with the privileges of this user. The `ORADIM` command prompts you for the password to this user account. You can specify other options using `ORADIM`.

        In this example, if your `SID`` value` is `ORCL`, your `password` (`SYSPWD`) value is `TWxy5791`, the maximum number of users (`MAXUSERS`) value is 10, and the Oracle home path is `C:\ORACLE\PRODUCT\19.1.0\DB`, then enter the following command:

            C:\> ORADIM -NEW -SID ORCL -SYSPWD TWxy5791 -MAXUSERS 10
            -STARTMODE AUTO -PFILE C:\ORACLE\PRODUCT\19.1.0\DB\DATABASE\INITORCL.ORA

        `ORADIM` writes a log file to the `ORACLE_HOME\database` directory. The log file contains the name of the PDB in the multitenant database.

7.  If your operating system is Linux or UNIX, then perform the following checks:

    1.  Your `ORACLE_SID` is set correctly

    2.  The `oratab` file points to the Oracle home for Oracle Database 12c

    3.  The following environment variables point to the Oracle Database 12c directories:

        - `ORACLE_HOME`

        - `PATH`

    4.  Any scripts that clients use to set `$ORACLE_HOME` environment variable must point to the new Oracle home.

    **Note:**

    If you are upgrading an Oracle Real Application Clusters database, then perform these checks on all nodes where the Oracle Real Application Clusters database has instances configured.

    **See Also:**

    Oracle Database and Oracle Clusterware installation guides for information about setting other important environment variables on your operating system

8.  Log in to the system as the owner of the Oracle home under the new Oracle Database release.

9.  Start SQL\*Plus in the new Oracle home from the path `Oracle_home``/rdbms/admin` directory.

    For example:

        $ cd $ORACLE_HOME/rdbms/admin
        $ pwd
        /u01/app/oracle/product/19.0.0/dbhome_1/rdbms/admin
        $ sqlplus

    On Windows platforms, to access SQL\*Plus, change directory to `%ORACLE_HOME%/bin`

10. Connect to the database that you want to upgrade using an account with SYSDBA privileges:

        SQL> CONNECT / AS SYSDBA

11. Start the CDB in upgrade mode:

        SQL> startup upgrade

12. Start the instance by issuing the following command in SQL\*Plus:

        SQL> alter pluggable database all open upgrade;

    If errors appear listing desupported initialization parameters, then make a note of the desupported initialization parameters and continue with the upgrade. Remove the desupported initialization parameters the next time you shut down the database.

    **Note:**

    Starting up the database in `UPGRADE` mode does the following:

    - Starts up the database with a new version of the Oracle Database instance

    - Restricts logins to SYSDBA

    - Disables system triggers

    - Performs additional operations that prepare the database for upgrades

13. Exit SQL\*Plus before proceeding to the next step.

    For example:

        SQL> EXIT

14. To upgrade an entire CDB, run the Parallel Upgrade Utility (`catctl.pl`) from the new Oracle home. The Parallel Upgrade Utility provides parallel upgrade options that reduce downtime. You can run the command by using the command-line script `dbupgrade` from the new Oracle home.

    For example:

    Linux:

        cd $ORACLE_HOME/bin
        ./dbupgrade

    Windows:

        cd %ORACLE_HOME%\bin
        dbupgrade

    **Note:**

    - Use the `-d` option to specify the directory that contains the files that you want to process. Use the `-l` option to specify the directory that you want to use for spool log files.

    - If you are upgrading an entire CDB, and there are errors in `CDB$ROOT`, then the upgrade aborts.

15. To upgrade a subset of PDBs within a CDB, specify either an inclusion list, or an exclusion list.

    - This example for a Linux or UNIX system uses an inclusion list to upgrade `PDB1` only:

          cd $ORACLE_HOME/bin
          ./dbupgrade -c 'PDB1'

    - This example for a Windows system uses an exclusion list to upgrade everything in the CDB except `PDB1`:

          cd $ORACLE_HOME\bin
          dbupgrade -C "PDB1"

    **Note:**

    You can upgrade an individual PDB by unplugging it from the earlier release CDB, and plugging it into a later release CDB.

    For Windows, when you run the `dbupgrade` command with the inclusion (`-c`) or the exclusion (`-C`) options, you must specify the option with quotes around the CDB root name and PDB seed name.

    For example:

    ... `-C "CDB$ROOT PDB$SEED"`

16. For CDBs, log in to the CDB as SYSDBA and run the command alter pluggable database all open to make databases available for recompiling code. For example:

        $ sqlplus / as sysdba

        SQL> alter pluggable database all open;

17. Run `catcon.pl`, using the log file base (`-b`) command to set the log file base to `utlrp`. This command starts `utlrp.sql` and recompiles any remaining stored PL/SQL and Java code.

    For example:

        $ORACLE_HOME/perl/bin/perl catcon.pl -n 1 -e -b utlrp -d '''.''' utlrp.sql

    Because the command specifies `-b utlrp`, recomplile results are stored in log file `utlrp0.log`.

18. Use the `catcon` utility to run `postupgrade_fixups.sql`, setting the log file base to `postupgrade_fixups`.

    For example:

        $ORACLE_HOME/perl/bin/perl catcon.pl -n 1 -e -b postupgrade_fixups -d '''.''' postupgrade_fixups.sql

19. Use the `catcon` utility to run `utlusts.sql`, setting the log file base to `utlu19s`. This command verifies that all issues are fixed.

    For example, in a CDB:

        $ORACLE_HOME/perl/bin/perl catcon.pl -n 1 -e -b utlu19s -d '''.''' utlusts.sql

    Because the command specifies `-b utlu19s`, upgrade results are stored in log file `utlu19s0.log`.

    To see information about the state of the database, run `utlusts.sql` as many times as you want, at any time after you complete the upgrade. If the `utlusts.sql` script returns errors, or if it shows components that are not marked as `VALID`, or if the SQL script you run is not from the most recent release, then refer to the troubleshooting section in this guide.

20. Ensure that the time zone data files are current by using the `DBMS_DST` PL/SQL package to upgrade the time zone file. You can also update the time zone after the upgrade. If you update the time zone, then you must update the time zone in both `CDB$ROOT` and the PDBs.

21. Exit SQL\*Plus.

    For example:

        SQL> EXIT

22. (Conditional) If you are upgrading an Oracle Real Application Clusters database, then use the following command syntax to upgrade the database configuration in Oracle Clusterware:

        $ srvctl upgrade database -db db-unique-name -oraclehome oraclehome

    In this example, `db-unique-name` is the assigned database name (not the instance name), and `oraclehome` is the Oracle home location in which the database is being upgraded. The `SRVCTL` utility supports long GNU-style options, in addition to the short CLI options used in earlier releases.

Your database is now upgraded. You are ready to complete post-upgrade procedures.

**Caution:**

If you retain the old Oracle software, then never start the upgraded database with the old software. Only start Oracle Database using the start command in the new Oracle Database home.

Before you remove the old Oracle environment, relocate any data files in that environment to the new Oracle Database environment.

**See Also:**

Oracle Database Administrator’s Guide for information about relocating data files

**Related Topics**

- [Oracle Database Administrator’s Guide](../admin/managing-data-files-and-temp-files.md)

**Parent topic:** Manual Upgrade Scenarios for Multitenant Architecture Oracle Databases

### About Upgrading PDBs Using the Parallel Upgrade Utility with Priority Lists

In Oracle Database 12.2 and later releases, you can upgrade PDBs using a priority list to upgrade a set of PDBs ahead of other PDBs, and you can modify that upgrade priority.

Priority lists enable you to group and upgrade PDBs according to their priority. A priority list is a text file with comma-delimited lists defining the order of upgrade priority, and the PDBs in each numeric priority group. You run the Parallel Upgrade Utility (`dbupgrade`, `dbupgrade.cmd`, or `catctl.pl`) using the `-L` option to run the upgrade using a priority list, and to call that list as the upgrade runs.

Create the list using the following format. In this format example, the variable numeral is a numeric value, and pdbx is the name of a PDB.

Number, Pdb
    numeral,pdb1,pdb2,pdb3
    numeral,pdb4
    numeral,pdb5,pdb6,pdb7,pdb8
    .
    .
    .

The numeral represents the priority for the PDB.

PDB priorities are as follows:

1.  CDB\$ROOT: Priority 1. Upgrading the container database first is a mandatory priority. You cannot change the priority for the container database upgrade. CDB\$ROOT is always processed first.

2.  PDB\$SEED: Priority 1. Upgrading the PDB seed database is a mandatory priority. You cannot change the priority for the PDB seed upgrade. PDB\$SEED always upgraded after CDB\$ROOT, and with the first batch of PDB upgrades.

3.  Priority List 1 PDBs: Priority 1 is the highest user-selected priority. These PDBs are upgraded second after CDB\$ROOT, in the batch where the PDB\$SEED PDB is upgraded.

4.  Priority List 2 PDBs: Priority 2 is the second-highest priority PDB set. These PDBs are upgraded after the Priority 1 PDBs.

5.  Priority List 3 PDBs: Priority 3 is the third-highest priority PDB set. These PDBS are upgraded after priority 2 PDBs.

6.  Priority List 4 PDBs: Priority 4 is the fourth-highest priority PDB set. These PDBS are upgraded after priority 3 PDBs.

7.  Priority List 5 PDBs: Priority 5 is the fifth-highest priority PDB set. These PDBS are upgraded after priority 4 PDBs.

8.  Priority List 6 PDBs: Priority 6 is the sixth-highest priority PDB set. These PDBS are upgraded after priority 5 PDBs.

When you run the Parallel Upgrade Utility, the following processing rules apply:

- CDB\$ROOT and PDB\$SEED are always processed first, even if they are not present in the priority list.

- All PDBs that are in priority lists are processed in order of priority

- Any PDBs that are not listed in priority lists are processed after the PDBs named in the priority list.

For example:

    Number,Pdb
    1,sales1,region2,receivables1
    2,sales2
    3,dss1,region3,region2,dss2,dss3

Use the following syntax to run the Parallel Upgrade utility using a priority list:

    dbupgrade -L priority_list_name

For example, to run the Parallel Upgrade Utility on a Windows system using the Parallel Upgrade Utility batch command and a priority list named `My122Upgrade`, enter the following command:

    C:>\u01\app\19.1.0\db_home1\rdbms\admin\dbupgrade -L MyUpgrade

After you complete an upgrade using a priority list to set upgrade priorities, these PDB priority states are maintained in the CDB for the PDBs. The next upgrade honors the priorities set for the PDBs in the previous upgrade.

Use the following SQL command syntax to change PDB upgrade priority states, where `PDBName` is the name of the PDB whose upgrade priority you want to change, and `PDBPriorityNumber` is the new priority value you want to assign:

    SQL> alter session set container = CDB$ROOT
    SQL> alter pluggable database PDBName upgrade priorityPDBPriorityNumber

For example:

    SQL> alter session set container = CDB$ROOT
    SQL> alter pluggable database region2 upgrade priority 2

In this example, the PDB named region 2 that was set to upgrade priority 1 in the previous example is changed to upgrade priority 2.

**Parent topic:** Manual Upgrade Scenarios for Multitenant Architecture Oracle Databases

### About PDB Upgrades Using Priority Lists, Inclusion Lists, and Exclusion Lists

To control how your pluggable databases (PDBs) are upgraded, you can use inclusion and exclusion lists with priority lists.

With Oracle Database 12c Release 1 (12.1.0.2) and later releases, the preferred method for specifying the order in which upgrades are applied to PDBs is to set the priority on the source Oracle Database using `alter pluggable database` with `upgrade priority`, where `pdbname` is the PDB, and `number` is the priority that you want to assign for upgrade:

    alter pluggable database pdbname upgrade priority number

For example:

    alter pluggable database CDB1_PDB3 upgrade priority 2

However, you can also specify priority lists at the time of upgrade by using the procedures described here.

#### Upgrade Processing and Lists

The following terms designate types of upgrade list processing:

- **Priority lists**: Comma-delimited lists that designate the upgrade priority of PDBs in the list.

- **Inclusion lists**: Comma-delimited lists that designate PDBs that you want to upgrade. PDBs in these lists are upgraded after the PDBs listed in priority lists.

- **Exclusion lists**: Comma-delimited lists that designate PDBs that you do not want to be upgraded.

You can use inclusion lists and exclusion lists in the following ways:

- On their own, to include or exclude a set of PDBs from an upgrade

- In conjunction with priority lists to provide detailed specifications for the order in which PDBs are upgraded, and which PDBs are excluded from an upgrade.

  When inclusion lists are used with priority lists, the PDBs listed in inclusion lists are upgraded according to the priority value they are assigned in the priority lists. PDBs listed in inclusion lists but not listed in priority lists are upgraded after all PDBs in the priority lists are upgraded.

  When exclusion lists are used with priority lists, the PDBs listed in exclusion lists are not upgraded.

**Note:**

Create priority lists using a plain text editor, such as `vi` on Linux and Unix, or Notepad on Microsoft Windows.

In the examples in this topic, the `cpu_count` value is equal to 2.

#### Upgrade Priority using Default Processing

**Default processing** is the upgrade processing that is carried out if you do not designate how you want to upgrade PDBs in your container databases (CDBs) using lists.

With default processing, `CDB$ROOT` is upgraded, and then `PDB$SEED`. Depending on the degree of parallelism you set, one or more PDBs may be updated in parallel with `PDB$SEED.` As upgrades complete, PDBs are upgraded as upgrade processors become available.

The examples that follow use the following multitenant configuration of CDB and PDBs:

    CDB$ROOT
    PDB$SEED
    CDB1_PDB1
    CDB1_PDB2
    CDB1_PDB3
    CDB1_PDB4
    CDB1_PDB5

In default processing, you specify no preference for which PDBs you want upgraded or excluded from upgrade. With default processing, `CDB$ROOT` is upgraded first, and `PDB$SEED` is updated in the first group of PDBs upgraded.

Example 4-3 Specifying Complete PDB Upgrade Priority

The following example of a priority list, where the priority setting for all PDBs is set by the list:

    1,CDB$ROOT
    1,PDB$SEED
    1,CDB1_PDB1
    1,CDB1_PDB2
    2,CDB1_PDB3
    2,CDB1_PDB4
    3,CDB1_PDB5

Here is another way of writing the same list, in which you group PDBs in priority order:

    1,CDB$ROOT
    1,PDB$SEED
    1,CDB1_PDB1,CDB1_PDB2
    2,CDB1_PDB3,CDB1_PDB4
    3,CDB1_PDB5

In the preceding example, the PDBs listed in priority 1 are `CDB1_PDB1` and `CDB1_PDB2`. These PDBs are upgraded before `CDB1_PDB3` and `CDB1_PDB4`.

Here is another way of writing the same list, using container ID values (`CON_ID`) to set the priority order:

    1,CDB$ROOT
    1,PDB$SEED
    1,3,4
    2,5,6
    3,7

In the preceding example, the PDBs listed in priority 1 are `CDB1_PDB1` (identified by `CON_ID 3`) and CDB1_PDB2 (identified by `CON_ID 4`). These PDBs are upgraded before `CDB1_PDB3` (`CON_ID 5`) and `CDB1_PDB4` (`CON_ID 6`).

When you use the `CON_ID` method to specify priority, the first number specifies the priority of the group of PDBs. The second value or number specifies the PDBs (by `CON_ID`) number that are in that priority grouping. `CDB$ROOT` is always updated first, and `PDB$SEED` is always updated in the first upgrade priority group.

These examples all show a priority list upgrade with the following characteristics:

- Exclusion processing: None

- Inclusion processing: None

- Default processing: None

The upgrade order is carried out in the following sequence:

1.  `CDB$ROOT`

2.  `PDB$SEED`, `CDB1_PDB1`

3.  `CDB1_PDB2`, `CDB1_PDB3`

4.  `CDB1_PDB4`, `CDB1_PDB5`

Example 4-4 Specifying a Priority Subset of PDBs, and Upgrading Other PDBs with Default Processing

The following example specifies a priority list called `priority.lst`, which specifies a subset of PDBs for upgrade:

    catctl -L priority.lst catupgrd.sql
    1,CDB$ROOT
    1,PDB$SEED
    1,CDB1_PDB1,CDB1_PDB2

This example shows a priority list upgrade with the following characteristics:

- Exclusion processing: None

- Inclusion processing: None

- Default processing: `CDB1_PDB3`, `CDB1_PDB4`, `CDB1_PDB5`

The upgrade order is carried out in the following sequence:

1.  `CDB$ROOT`

2.  `PDB$SEED`, `CDB1_PDB1`

3.  `CDB1_PDB2`, `CDB1_PDB3`

4.  `CDB1_PDB4`, `CDB1_PDB5`

Example 4-5 Specifying a Priority Subset of PDBs, and Upgrading Other PDBs with an Inclusion List

The following example specifies a priority list called `priority.lst`, which specifies a priority subset of PDBs for upgrade:

    catctl -L priority.lst -c 'CDB1_PDB2 CDB1_PDB4 CDB1_PDB5' catupgrd.sql

This command refers to the following priority list:

    1,CDB$ROOT
    1,PDB$SEED
    1,CDB1_PDB2,CDB1_PDB4
    2.CDB1_PDB5

This example shows a priority list upgrade with the following characteristics:

- Exclusion processing: None

- Inclusion processing: `CDB1_PDB2`, `CDB1_PDB4`, `CDB1_PDB5`

- Default processing: None

The upgrade order is carried out in the following sequence:

1.  `CDB1_PDB2`, `CDB1_PDB4`

2.  `CDB1_PDB5`

The Parallel Upgrade Utility processes only the PDBs that are in the inclusion list, and in the order of the priority list.

Example 4-6 Specifying a Priority Subset of PDBs, and Excluding CDB\$ROOT with an Exclusion List

The following example runs `catctl` using a priority list called `priority.lst`. Because this command runs with the `-C` option, it excludes CDB\$ROOT from the upgrade:

    catctl -L priority.lst -C 'CDB$ROOT' catupgrd.sql

This is the priority list:

    1,CDB$ROOT
    1,PDB$SEED
    1,CDB1_PDB1,CDB1_PDB2
    2,CDB1_PDB3,CDB1_PDB4
    3,CDB1_PDB5

The upgrades are processed using the priority list to specify upgrade priority.

- Inclusion processing: None

- Exclusion processing: `CDB$ROOT`

- Priority processing: `PDB$SEED`, `CDB1_PDB1`, `CDB1_PDB2`, `CDB1_PDB3`, `CDB1_PDB4`, `CDB1_PDB5`

Because `CDB$ROOT` is excluded, the priority processing shifts. The upgrade order is carried out in the following sequence:

1.  `PDB$SEED`, `CDB_PDB1`

2.  `CDB_PDB2`, `CDB_PDB3`

3.  `CDB1_PDB4`, `CDB1_PDB5`

Example 4-7 Specifying an Exclusion List using CATCTL_LISTONLY

The following example specifies a priority list called `priority.lst`, which specifies a subset of PDBs for upgrade. With the `CATCTL_LISTONLY` option, PDBs that are not in the priority list are excluded from the upgrade:

    catctl -L priority.lst -C 'CATCTL_LISTONLY' catupgrd.sql

Priority list:

    1,CDB$ROOT
    1,PDB$SEED
    1,CDB1_PDB1,CDB1_PDB2
    2,CDB1_PDB3
    3,CDB1_PDB5

- Exclusion processing: `CATCTL_LISTONLY` (Only process inclusion priority list)

- Inclusion processing: None

- Default processing: None

The upgrade order is carried out in the following sequence:

1.  `CDB$ROOT`

2.  `PDB$SEED`, `CDB1_PDB1`, `CDB1_PDB2`

3.  `CDB1_PDB3`, `CDB1_PDB5`

**Note:**

Specifying the keyword `CATCTL_LISTONLY` in the exclusion list turns the priority list into an inclusion priority list. Only PDBs in the list are processed. No default processing occurs in this scenario, so in this example, `CDB1_PDB4` is not processed.

Example 4-8 Specifying a Priority List using CON_ID Values

The following example specifies a priority list called `priority.lst`, which specifies a subset of PDBs for upgrade:

    catctl -L priority.lst -C 'CATCTL_LISTONLY' catupgrd.sql

The upgrade order is determined by the priority list priority number. In the list called by the `-L` parameter, `priority.lst`, the numbers following the upgrade priority number are the CON_ID values associated with PDB names:

    1,3,4
    2,5,CDB1_PDB4
    3,7

In the preceding list example, note that you can use a mix of CON_ID numbers and PDB names.

The PDBs listed in priority 1 are `CDB1_PDB1` (identified by `CON_ID 3`) and `CDB1_PDB2` (identified by `CON_ID 4)`. These PDBs are upgraded before `CDB1_PDB3` (`CON_ID 5`), `CDB1_PDB4`, which is identified by name, and `CDB1_PDB5` (`CON_ID 7`).

- Exclusion processing: `-C CATCTL_LISTONLY` (Only process PDBs in the inclusion priority list)

- Exclusion Processing: None

- Inclusion processing: Specified in `priority.lst`

- Default processing: `CDB$ROOT`, `PDB$SEED`

The upgrade order is determined by the priority list, which uses the `CON_ID` numbers associated with the PDB.

1.  `CDB$ROOT`

2.  `PDB$SEED`, `CDB1_PDB1`

3.  `CDB1_PDB2`, `CDB1_PDB3`

4.  `CDB1_PDB4`, `CDB1_PDB5`

**Note:**

This example demonstrates the use of the `CON_ID` method to specify the PDBs, and omits `CDB$ROOT` and `PDB$SEED` from the priority list. `CDB$ROOT` and `PDB$SEED` are processed using default processing.

**Parent topic:** Manual Upgrade Scenarios for Multitenant Architecture Oracle Databases

### Upgrading Multitenant Architecture In Parallel

Use this technique to upgrade multitenant architecture Oracle Database releases (Oracle Database 12c Release 1 (12.1.0.1) and later by upgrading container databases (CDBs), and then upgrading multiple pluggable databases (PDBs) in parallel.

- About Upgrading Pluggable Databases (PDBs) In Parallel
  Using the In-Parallel technique, you can upgrade the container database (CDB), and then immediately upgrade PDBs using parallel SQL processors.
- Upgrading Multitenant Container Databases In Parallel
  Use this technique to upgrade `CDB$ROOT`, `PDB$SEED`, and all PDBs in the CDB in one upgrade operation.

**Parent topic:** Manual Upgrade Scenarios for Multitenant Architecture Oracle Databases

#### About Upgrading Pluggable Databases (PDBs) In Parallel

Using the In-Parallel technique, you can upgrade the container database (CDB), and then immediately upgrade PDBs using parallel SQL processors.

CDBs can contain zero, one, or more PDBs. By default, the Parallel Upgrade Utility (`catctl.pl`) updates the CDB and all of its PDBs in the same upgrade window. The Parallel Upgrade Utility uses the number of computer processing units (CPUs) to determine the maximum number of PDBs that are upgraded simultaneously. For upgrades using Replay Upgrade (the default), the number of PDBs that are upgraded in parallel is determined by dividing the parallel SQL process count (`-n` option) by the parallel PDB SQL process count (`-N` option), divided by 2. For classic upgrade, the maximum PDB upgrades that run concurrently are the number of PDBs that are upgraded in parallel, dividing the parallel SQL process count (`-n` option) by the parallel PDB SQL process count (`-N` option).

**Note:**

You must plan your upgrade window to accommodate a common downtime for all of the database services that the PDBs on the CDB are providing.

##### Pluggable Database Upgrade Syntax

`dbupgrade [-M] -n ` \[-N\] \[-t\]

- `-M` Specifies if `CDB$ROOT` is kept in upgrade mode, or if it becomes available when it completes upgrade:

  - If you run the Parallel Upgrade Utility with the `-M` parameter, then the upgrade places `CDB$ROOT` and all of its PDBs in upgrade mode, which can reduce total upgrade time. However, you cannot bring up any of the PDBs until the CDB and all of its PDBs are upgraded.

  - If you do not run the Parallel Upgrade Utility with the `-M` parameter, then CDB\$ROOT is upgraded and restarted in normal mode, and the normal background processes are started. After a successful upgrade, only `CDB$ROOT` is opened in read/write mode. All the PDBs remain in `MOUNT` mode. As each PDB is upgraded, you can bring each PDB online while other PDBs are still being upgraded.

- `-n` Specifies the number of in-parallel PDB upgrade processors.

  If you do not specify a value for `-n`, then the default for `-n` is the `CPU_COUNT` value.

  If you do specify a value for `-n`, then that value is used to determine the number of parallel SQL processes. The maximum value is unlimited. The minimum value is 4.

- `-N` Specifies the number of SQL processors to use when upgrading PDBs. The maximum value is 8. The minimum value is 1. If you do not specify a value for `-N`, then the default value is 2.

  For classic upgrade, the maximum PDB upgrades running concurrently is the value of `-n` divided by the value of `-N` for classic upgrade, and for the Replay Upgrade default, the value of -n divided by -N, divided by 2.

- `-t` Specifies that you want to use classic upgrade, using AutoUpgrade, instead of using the Replay Upgrade default.

The following is a high-level list of actions during the In Parallel PDB upgrade technique:

1.  Make sure that your backup strategy is complete.

2.  Run AutoUpgrade using the `preupgrade` clause, to determine if there are any issues that you must correct before starting an upgrade. Fix any issue that is reported.

    For example:

        java -jar autoupgrade.jar -preupgrade "dir=/tmp,oh=/u01/app/product/12.2.0/dbhome_1,sid=db122,target_version=21" -mode analyze

3.  Run the AutoUpgrade utility. In sequence, the following upgrades are carried out:

    1.  Cycle 1: `CDB$ROOT` is upgraded to the new Oracle release

    2.  Cycle 2 to Cycle x: `PDB$SEED` and PDBs are upgraded in parallel, with the number of cycles of upgrades as determined by the parameter settings you specify with `-n`.

4.  Complete post-upgrade steps.

Example 4-9 Example of Multitenant Architecture Upgrade Using Defaults (No Parameters Set)

In this scenario, your `CPU_COUNT` value is equal to 24. If you do not specify a value for in-parallel PDB processors using the `-n` option, then the default value for in-parallel PDB processors (`-n`) is equal to 24. If you do not specify a value for `-N`, then the default value for the number of SQL processors (`-N`) is 2.

Result:

For Replay Upgrade, 6 PDBs are upgraded in parallel (\[`CPU_COUNT` divided by 2\], divided by 2, or 12 divided by 2). There are two parallel SQL processes allocated for each PDB.

For classic upgrade, 12 PDBs are upgraded in parallel (`CPU_COUNT` divided by 2, or 24 divided by 2.) There are 2 parallel SQL processes allocated for each PDB.

Example 4-10 Example of Multitenant Architecture Upgrade Using 64 In Parallel PDB Upgrade Processors and 4 Parallel SQL Processes

In this scenario you set the value of in-parallel PDB upgrade processors to 64 by specifying the option `-n 64`. You specify the value of parallel SQL processors to 4 by specifying the option `-N 4`.

Result:

For Replay Upgrade, 8 PDBs are upgraded in parallel (\[64 divided by 4\] divided by 2). There are 4 parallel SQL processes for each PDB.

For classic upgrade, 16 PDBs are upgraded in parallel ( 64 divided by 4). There are 4 parallel SQL processes for each PDB.

Example 4-11 Example of Multitenant Architecture Upgrade Using 20 In Parallel PDB Upgrade Processors and 2 Parallel SQL Processes

In this scenario you set the value of in-parallel PDB upgrade processors to 20 by specifying the option `-n 20`. You specify the value of parallel SQL processors to 2 by specifying the option `-N 2`.

Result:

For Replay Upgrade, 5 PDBs are upgraded in parallel (\[20 divided by 2\], divided by 2). There are 2 parallel SQL processes for each PDB.

For classic upgrade, 10 PDBs are upgraded in parallel (20 divided by 2) There are 2 parallel SQL processes for each PDB.

Example 4-12 Example of Multitenant Architecture Upgrade Using 10 In Parallel PDB Upgrade Processors and 4 Parallel SQL Processes

In this scenario you set the value of in-parallel PDB upgrade processors to 10 by specifying the option `-n 10`. You specify the value of parallel SQL processors to 2 by specifying the option `-N 4`.

Result:

For Replay Upgrade, 1 PDB is upgraded (\[10 divided by 4\], divided by 2). There are 4 parallel SQL processes for the PDB.

For classic upgrade, 2 PDBs are upgraded in parallel (10 divided by 4). There are 4 parallel SQL processes for each PDB.

**Parent topic:** Upgrading Multitenant Architecture In Parallel

#### Upgrading Multitenant Container Databases In Parallel

Use this technique to upgrade `CDB$ROOT`, `PDB$SEED`, and all PDBs in the CDB in one upgrade operation.

If you do not choose to use the AutoUpgrade utility to complete your upgrade, or to use Replay Upgrade, then Oracle recommends that you use this approach if you can schedule downtime. Using this procedure upgrades in parallel all the PDBs in the multitenant architecture container database, depending on your server’s available processors (CPUs). This is a direct procedure for upgrades that provides simplicity of maintenance.

**Note:**

When you upgrade the entire container using the In Parallel upgrade method, all the PDBs must be down. Perform the upgrade in a scheduled upgrade window so that you can bring all the PDBs down.

**Caution:**

- Always create a backup of existing databases before starting any configuration change.
- You cannot downgrade a database after you have set the compatible initialization parameter.
- Oracle strongly recommends that you upgrade your source and target databases to the most recent release update (RU) or release update revision (RUR) before starting an upgrade, and to the most recent release update before starting a downgrade.

1.  Ensure that you have a proper backup strategy in place.
2.  Open all PDBs.
    For example:

        SQL> alter pluggable database all open;
3.  To check readiness for upgrade, run AutoUpgrade using the `preupgrade` parameter, and use the `dir` option to specify an output log directory.
        java -jar autoupgrade.jar -preupgrade "dir=/tmp,oh=/u01/app/product/12.2.0/dbhome_1,sid=db122,target_version=21" -mode analyze
4.  Check the `upgrade.xml` file in the log directory.
    On multitenant architecture Oracle Databases, running AutoUpgrade using the `preupgrade` parameter with `fixups` mode runs fixups on every container that was open when you ran AutoUpgrade. The scripts resolve some issues that AutoUpgrade identifies.

    Complete any other preupgrade tasks identified in the `upgrade.xml` file.
5.  (Conditional) For Oracle RAC databases, use SQL\*Plus to set the cluster database initialization parameter to `FALSE`:
    For example;

        ALTER SYSTEM SET cluster_database=FALSE SCOPE=spfile;
6.  Shut down the database in the old Oracle home using `srvctl`.
    For example, where `db_unique_name` is your database name:

        cd $ORACLE_HOME
        pwd
        /u01/app/oracle/19.0.0/dbhome_1

        srvctl stop database -d db_unique_name
        srvctl disable database -d db_unique_name
7.  Copy the `PFILE` or `SPFILE` from the old Oracle home to the new Oracle home
8.  Connect with SQL\*Plus:
        sqlplus / as sysdba
9.  Bring the `CDB$ROOT` instance into upgrade mode:
        STARTUP UPGRADE
10. Bring all PDBs into upgrade mode:
        ALTER PLUGGABLE DATABASE ALL OPEN UPGRADE;
11. Check the status of PDBs to confirm that they are ready to upgrade:
        SHOW PDBS

    For all PDBs, ensure that the status is set to `MIGRATE`.
12. Exit from SQL\*Plus, and change directory to the new Oracle home `$ORACLE_HOME/rdbms/admin`:
        EXIT
        cd $ORACLE_HOME/rdbms/admin
13. Start the upgrade using the Parallel Upgrade Utility (`catctl.pl`, using the shell command `dbupgrade`), where `-d` specifies the location of the directory:
        dbupgrade -d $ORACLE_HOME/rdbms/admin

    Starting with Oracle Database 21c, by default the `dbupgrade` script calls a Replay Upgrade, which sets parallelism to the number of CPUs divided by four. The number of PDBs upgraded in parallel is always half of the value previously used with legacy upgrade. On a server with 64 CPUs, 64 divided by 4 equals 16 PDBs upgraded in parallel.

    **Note:**

    If you prefer to use classic upgrade to perform the upgrade, then start `dbupgrade` using the `-t` option. For example:

        dbupgrade -t -d $ORACLE_HOME/rdbms/admin

    If you prefer to use AutoUpgrade, then refer to the AutoUpgrade script instructions.
14. Confirm that the upgrade was successful by reviewing the `upg_summary.log` If necessary, review other logs.
15. Open all PDBs using SQL\*Plus, so that you can recompile the databases:
        ALTER PLUGGABLE DATABASE ALL OPEN;
16. Exit from SQL\*Plus, and change directory to the new Oracle home path `$ORACLE_HOME/rdbms/admin`:
        EXIT
        cd $ORACLE_HOME/rdbms/admin
17. Run AutoUpgrade with the `preupgrade` parameter, run in `postfixups` mode. AutoUpgrade runs all database checks, and on the basis of those results, runs fixups automatically.
    For example:

        java -jar autoupgrade.jar -preupgrade "dir=/tmp,oh=u01/app/product/12.2.0/dbhome_1,sid=db122,target_home=/databases/product/19c/dbhome_1" -mode postfixups
18. Run `utlusts.sql` to verify that there are no upgrade issues,
    For example, in a CDB, where you use the `catcon` utility to run utlusts.sql, using the flag `-b` to set the log file base for the upgrade to `utlu19s`:

        $ORACLE_HOME/perl/bin/perl catcon.pl -n 1 -e -b utlu19s -d '''.''' utlusts.sql

    Because the command specifies `-b utlu19s`, upgrade results are stored in log file `utlu19s0.log`.

    To see information about the state of the database, run `utlusts.sql` as many times as you want, at any time after the upgrade is completed. If the `utlusts.sql` script returns errors, or shows components that do not have the status `VALID`, or if the version listed for the component is not the most recent release, then perform troubleshooting.
19. (Conditional) For Oracle RAC environments only, enter the following commands to set the initialization parameter value for CLUSTER_DATABASE to `TRUE`:
        ALTER SYSTEM SET CLUSTER_DATABASE=TRUE SCOPE=SPFILE;
20. Start Oracle Database, where `dbname` is the name of the database.
        srvctl upgrade database -db db-unique-name -oraclehome oraclehome
        srvctl enable database -db db-unique-name
21. Use SQL\*Plus to shut down the database.
        SHUTDOWN IMMEDIATE
22. Use `srvctl` to start up the database.
        srvctl start database -db db-unique-name

Your database is now upgraded.

**Caution:**

If you retain the old Oracle software, then never start the upgraded database with the old software. Only start Oracle Database using the start command in the new Oracle Database home.

Before you remove the old Oracle environment, relocate any data files in that environment to the new Oracle Database environment.

**Related Topics**

- [Managing Data Files and Temp Files](../admin/managing-data-files-and-temp-files.md)

**Parent topic:** Upgrading Multitenant Architecture In Parallel

### Upgrading Multitenant Architecture Sequentially Using Unplug-Plug

To upgrade pluggable databases (PDBs) that are in an earlier release multitenant container databases (CDBs), Oracle Database Release 12c (12.1.0.1) and later, you can unplug the PDBs from the earlier release CDB, and plug the PDBs into the later release CDB.

- About Upgrading Pluggable Databases (PDBs) Sequentially
  You can upgrade PDBs manually with the Parallel Upgrade Utility by unplugging a PDB from an earlier release CDB, plugging it into a later release CDB, and then upgrading that PDB to the later release.
- Unplugging the Earlier Release PDB from the Earlier Release CDB
  To prepare for upgrading the PDB, use this procedure to unplug the PDB from the earlier release CDB.
- Plugging in the Earlier Release PDB to the Later Release CDB
  To Plug the PDB from the earlier release CDB to the later release CDB, use the `CREATE PLUGGABLE DATABASE` command.
- Upgrading the Earlier Release PDB to the Later Release
  Open PDBs in `UPGRADE` mode use the Parallel Upgrade Utility to carry out the upgrade of the earlier-release PDB to the release level of the CDB.
- Use Inclusion or Exclusion Lists for PDB Upgrades
  If you want to upgrade a subset of earlier release PDBs, then use inclusion or exclusion lists to avoid reupgrading the CDB or PDBs that are at the new release level.

**Parent topic:** Manual Upgrade Scenarios for Multitenant Architecture Oracle Databases

#### About Upgrading Pluggable Databases (PDBs) Sequentially

You can upgrade PDBs manually with the Parallel Upgrade Utility by unplugging a PDB from an earlier release CDB, plugging it into a later release CDB, and then upgrading that PDB to the later release.

You have multiple options available to you to upgrade PDBs. CDBs can contain zero, one, or more pluggable databases (PDBs). After you install a new Oracle Database release, or after you upgrade the CDB (`CDB$ROOT`), you can upgrade one or more PDBs without upgrading all of the PDBs on the CDB.

You can choose the upgrade plan that meets the needs for your service delivery. For example, you can use the AutoUpgrade utility to upgrade PDBs, or you can use the manual Parallel Upgrade Utility to upgrade PDBs individually, or with inclusion or exclusion lists. You can upgrade the CDB and all PDBs (an In Parallel manual upgrade), or you can upgrade the CDB, and then upgrade PDBs sequentially, either individually, or in sets using inclusion or exclusion lists. You can also continue to use Database Upgrade Utility (DBUA). However, the preferred option for upgrading Oracle Database is to use the AutoUpgrade utility.

If you choose to run upgrades using the Parallel Upgrade Utility to perform manual unplug-plug upgrades, then the following is a high-level list of the steps required for sequential PDB upgrades using the Parallel Upgrade Utility:

1.  Unplug the earlier release PDB from the earlier release CDB.
2.  Drop the PDB from the CDB.
3.  Plug the earlier release PDB into the later release CDB.
4.  Upgrade the earlier release PDB to a later release.

If you choose to upgrade manually using the Parallel Upgrade Utility, then you can manage PDB upgrades with lists:

- Priority lists, to set the order in which PDBs are upgraded

- Inclusion lists, which enable you to designate a set of PDBs to upgrade after the PDBs listed in the priority list are upgraded

- Exclusion lists, which enable you to designate a set of PDBs that are not upgraded

**Note:**

A PDB cannot be recovered unless it is backed up. After an upgrade using the method of creating a CDB and plugging in a PDB, be sure to back up the PDB.

**Related Topics**

- [Oracle Database Backup and Recovery User’s Guide](../bradv/backing-up-database.md)
- [Oracle Database Administrator’s Guide](../multi/removing-a-pdb.md)

**Parent topic:** Upgrading Multitenant Architecture Sequentially Using Unplug-Plug

#### Unplugging the Earlier Release PDB from the Earlier Release CDB

To prepare for upgrading the PDB, use this procedure to unplug the PDB from the earlier release CDB.

1.  To determine if the database is ready for upgrade, run AutoUpgrade with the preupgrade parameter, run in `analyze` mode. For example, with the database `salespdb` in the Oracle home `/u01/app/oracle/product/12.2.0/dbhome1`, checking for readiness to upgrade to Oracle Database 19c:

    1.  Run `setenv ORACLE_HOME /u01/app/oracle/product/12.2.0/dbhome1`.
    2.  Run `setenv ORACLE_SID salespdb`.
    3.  Run `java -jar autoupgrade.jar -preupgrade "target_version=19,dir=/autoupgrade/test/log" –mode fixups`.
    4.  Check `prefixups.xml` under the directory `/autoupgrade/test/log/salespdb/prefixups`.

2.  Fix any issues AutoUpgrade detected that could not be fixed automatically.

3.  Close the PDB you want to unplug.

    For example, use the following command to close the PDB `salespdb`:

        SQL> ALTER PLUGGABLE DATABASE salespdb CLOSE;

4.  Log back in to `CDB$ROOT`:
        CONNECT / AS SYSDBA
        SQL> ALTER SESSION SET CONTAINER=CDB$ROOT;

5.  Unplug the earlier release PDB using the following SQL command syntax, where `pdb` is the name of the PDB, and `path` is the location of the PDB XML file:

        ALTER PLUGGABLE DATABASE pdb UNPLUG INTO 'path/pdb.xml';

    For example, where the pdb name is `salespdb` and path is `/home/oracle/salespdb.xml`:

        SQL> ALTER PLUGGABLE DATABASE salespdb UNPLUG INTO '/home/oracle/salespdb.xml';

    The following response displays when the command is completed:

        Pluggable database altered

6.  Drop the pluggable database `salespdb`, but keep data files.

    Oracle recommends that you drop `salespdb` after this procedure to clean up leftover information in the CDB views, and to help to avoid future issues. As a best practice guideline, back up your PDB in the destination CDB first, and then issue the `DROP` command on the source.

    **Caution:**

    After you drop the PDB from its original CDB, you cannot revert to it using previously taken backup, because the `DROP` command removes backup files.

    To drop the pluggable database, enter the following command:

        SQL> DROP PLUGGABLE DATABASE salespdb KEEP DATAFILES;

7.  Exit.

**Parent topic:** Upgrading Multitenant Architecture Sequentially Using Unplug-Plug

#### Plugging in the Earlier Release PDB to the Later Release CDB

To Plug the PDB from the earlier release CDB to the later release CDB, use the `CREATE PLUGGABLE DATABASE` command.

This procedure example shows how to plug in a PDB when you are using Oracle-Managed Files. Refer to Oracle Database Administrator’s Guide for additional information about plugging in PDBs.

1.  Connect to the later release CDB.

2.  Plug in the earlier release PDB using the following SQL command, where `pdb` is the name of the PDB, and `path` is the path where the PDB XML file is located:

    CREATE PLUGGABLE DATABASE pdb USING 'path/pdb.xml';

    For example:

        SQL> CREATE PLUGGABLE DATABASE salespdb USING '/home/oracle/salespdb.xml';

    The following response displays when the command is completed:

        Pluggable database created.

**Note:**

When you plug in an earlier release PDB, the PDB is in restricted mode. You can only open the PDB for upgrade.

**Related Topics**

- [Oracle Database Administrator’s Guide](../multi/plugging-in-a-pdb.md)

**Parent topic:** Upgrading Multitenant Architecture Sequentially Using Unplug-Plug

#### Upgrading the Earlier Release PDB to the Later Release

Open PDBs in `UPGRADE` mode use the Parallel Upgrade Utility to carry out the upgrade of the earlier-release PDB to the release level of the CDB.

1.  If needed, switch to the PDB that you want to upgrade. For example, enter the following command to switch to the PDB `salespdb`:

        SQL> ALTER SESSION SET CONTAINER=salespdb;

2.  Open the PDB in UPGRADE mode.

        SQL> ALTER PLUGGABLE DATABASE OPEN UPGRADE;

3.  Upgrade the PDB using the Parallel Upgrade Utility command (`catctl.pl`, or the shell utility `dbupgrade`).

    When you upgrade a PDB, you use the commands you normally use with the Parallel Upgrade Utility. However, you also add the option `-c ``PDBname` to specify which PDB you are upgrading. Capitalize the name of your PDB as shown in the following example using the PDB named `salespdb`:

        $ORACLE_HOME/perl/bin/perl $ORACLE_HOME/rdbms/admin/catctl.pl -d  \
        $ORACLE_HOME/rdbms/admin -c 'salespdb' -l $ORACLE_BASE catupgrd.sql

4.  Review results.

    The default file path for the logs is in the path `Oracle_base``/cfgtoollogs/``dbname``/``upgradedatetime`, where `Oracle_base` is the Oracle base path, `dbname` is the database name, and `upgradedatetime` is the date and time for the upgrade. The date and time strings are in the character string format YYYYMMDDHHMMSC, in which YYYY designates the year, MM designates the month, DD designates the day, HH designates the hour, MM designates the minute, and SC designates the second.

    For example:

        $ORACLE_BASE/cfgtoollogs/salespdb/upgrade20181015120001/upg_summary.log

5.  To execute post-upgrade fixups, and to recompile the INVALID objects in the databaseUse the utility `catcon.pl` to run the script `postupgrade_fixups.sql`:

        $ORACLE_HOME/perl/bin/perl catcon.pl –c 'salespdb' -n 1 -e -b postfixups -d '''.''' /tmp/cfgtoollogs/salespdb/preupgrade/postupgrade_fixups.sql

6.  Use the utility `catcon.pl` to run `utlrp.sql` from the `$ORACLE_HOME/rdbms/admin` directory:

        $ORACLE_HOME/perl/bin/perl catcon.pl –c 'salespdb'-n 1 -e -b comp -d '''.''' utlrp.sql

    The script recompiles `INVALID` objects in the database, and places a log file in the current directory with the name `comp0.log`.

**Parent topic:** Upgrading Multitenant Architecture Sequentially Using Unplug-Plug

#### Use Inclusion or Exclusion Lists for PDB Upgrades

If you want to upgrade a subset of earlier release PDBs, then use inclusion or exclusion lists to avoid reupgrading the CDB or PDBs that are at the new release level.

Oracle recommends that you record the containers that you upgrade, and use inclusion or exclusion lists to exclude these containers from successive bulk upgrades. Excluding upgraded containers from successive bulk upgrades ensures that the upgrade only runs on PDBs that require the upgrade. Avoiding reupgrades minimizes the overall upgrade time, and avoids unnecessary unavailability.

For example: If you have installed Oracle Database using a multitenant architecture deployment, then the containers `CDB$ROOT`, `PDB$SEED`, and any other PDBs created when the CDB was created, are part of the new release multitenant architecture. If you upgraded a CDB, and at the same time upgraded a set of PDBs to the new release, then you do not need to upgrade either the CDB containers or the upgraded PDBs again.

In either case, when you plug in earlier release PDBs and then upgrade them, upgrade the PDBs with either an exclusion list, or an inclusion list:

- Use an inclusion list to specify only the set of PDBs that you want to upgrade.

- Use an exclusion list to exclude the CDB and PDB containers that are already upgraded.

If you do not use an inclusion list or an exclusion list to limit the upgrade scope, then the Parallel Upgrade Utility (`catctl.pl`) attempts to upgrade the entire CDB, not just the PDBs that require the upgrade. During that upgrade process, your system undergoes needless downtime. The inclusion list and the exclusion list options are mutually exclusive.

**Parent topic:** Upgrading Multitenant Architecture Sequentially Using Unplug-Plug
