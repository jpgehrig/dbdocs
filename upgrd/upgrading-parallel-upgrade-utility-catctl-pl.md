## Upgrading Manually with Parallel Upgrade Utility

To run upgrades with scripts that you run and manage manually, you can use the Parallel Upgrade Utility (`catctl.pl`).

- About the Parallel Upgrade Utility for Oracle Database (CATCTL.PL and DBUPGRADE)
  The Parallel Upgrade Utility (`catctl.pl`, and the `dbupgrade` script) enable you to upgrade simultaneously components that do not require upgrades to occur in a specific order.
- General Steps for Running the Parallel Upgrade Utility
  Review to obtain an overview of how to use the Parallel Upgrade Utility for Oracle Database.
- Parallel Upgrade Utility (catctl.pl) Parameters
  Control how the Parallel Upgrade Utility (`catctl.pl`) runs. You can also use these arguments to run the `dbupgrade` shell command.
- Example of Using the Parallel Upgrade Utility
  Use this example to understand how you can run the parallel upgrade utility manually to perform upgrades.

**Parent topic:** [Upgrading Oracle Database Manually Using Parallel Upgrade Utility](upgrading-oracle-database-parallel-upgrade-utiility-replay-upgrade.md)

### About the Parallel Upgrade Utility for Oracle Database (CATCTL.PL and DBUPGRADE)

The Parallel Upgrade Utility (`catctl.pl`, and the `dbupgrade` script) enable you to upgrade simultaneously components that do not require upgrades to occur in a specific order.

Oracle Database 12c release 1 (12.1) introduced the Parallel Upgrade Utility, `catctl.pl`. This utility reduces the total amount of time it takes to perform an upgrade by loading the database dictionary in parallel, and by using multiple SQL processes to upgrade the database. Performing parallel upgrades of components enables you to take advantage of your CPU capacity. Oracle continues to make improvements to the upgrade process to simplify both manual upgrades, and upgrades performed with the Database Upgrade Assistant (DBUA). DBUA and the manual upgrade procedures take advantage of the new Parallel Upgrade Utility.

You can run a shell command, `dbupgrade`, which starts up `catctl.pl` from the command line, instead of requiring you to run it from Perl.

The `dbupgrade` shell command is located in the file path `$ORACLE_HOME/bin` on Linux and UNIX, and `%ORACLE_HOME%\bin` on Windows. You can provide any command arguments that are valid for `catctl.pl` to the shell command. Either run the command directly from the new Oracle home path, or set a user environment variable to point to the file path.

For example:

Running with default values:

    $ ./dbupgrade

Running to specify a log directory placed in `/tmp`:

    $ ./dbupgrade -l /tmp

You can also run the Parallel Upgrade Utility using priority lists. For example:

    $ ./dbupgrade -L priority_list_name

When you use a priority list, you can include or exclude a specific list of PDBs in your upgrade.

You can also run the Parallel Upgrade Utility using priority emulation, so that you can see how the priority list is read and carried out, without actually performing the upgrade. For example:

    $ ./dbupgrade -E

**Related Topics**

- [Example of Testing Upgrades Using Priority List Emulation](testing-upgraded-production-oracle-database.md)

**Parent topic:** Upgrading Manually with Parallel Upgrade Utility

### General Steps for Running the Parallel Upgrade Utility

Review to obtain an overview of how to use the Parallel Upgrade Utility for Oracle Database.

The Parallel Upgrade Utility (`catctl.pl`, which you can start with the shell command `dbupgrade`) loads the data dictionary and components in parallel. Loading in parallel reduces the overall upgrade time. Before running the Parallel Upgrade Utility, follow the procedures for backing up your database that you normally do before upgrading. Also, as a prerequisite, you must run AutoUpgrade using the `preupgrade` clause to identify any problems that a database administrator must address before the upgrade proceeds.

The general steps for upgrading your database with the Parallel Upgrade Utility are as follows:

1.  Back up your current database.

2.  Install the Oracle Database software for the new release.

3.  Run AutoUpgrade with the `preupgrade` parameter on the source database, and correct any issues that AutoUpgrade does not fix.

4.  Shut down your current database.

5.  Set up the new Oracle home environment to access the new release database software, and then start SQL\*Plus from the directory `ORACLE_HOME``/rdbms/admin`.

6.  Log in to a user account with `SYSDBA` system privileges, and connect to the database that you want to upgrade:

        CONNECT / AS SYSDBA

7.  Start the database in upgrade mode. Use the command for your configuration type.

        SQL> startup upgrade;
        SQL> alter pluggable database all open upgrade;

    **Note:**

    The `UPGRADE` keyword performs operations that prepare the environment for the upgrade.

    You can be required to use the `PFILE` option in your startup command to specify the location of your initialization parameter file.

    When you start the database in upgrade mode, only queries on fixed views execute without errors until after the `catctl.pl` script is run. Before you run `catctl.pl`, you receive an error if you try to use PL/SQL, or if you try to run queries on any other view.

    If errors appear listing desupported initialization parameters, then make a note of the desupported initialization parameters, and continue with the upgrade. Remove the desupported initialization parameters the next time you shut down the database.

8.  Exit SQL\*Plus.

9.  Run the Parallel Upgrade Utility from the new Oracle home.

    You can run the utility as a shell command (`dbupgrade` on Linux and Unix, and` dbupgrade.cmd` on Microsoft Windows) or you can run it as a Perl command (`catctl.pl`).

    For example, on Linux and Unix:

        cd $ORACLE_HOME/bin
        ./dbupgrade

    For example, on Microsoft Windows:

        cd %ORACLE_HOME%\bin
        dbupgrade

    The Parallel Upgrade Utility starts the upgrade process.

    **Note:**

    The Parallel Upgrade Utility uses other files to carry out the upgrade. On Linux and Unix systems, these files include `catconst.pm`, `catcom.pm`, `sqlpatch`, `sqlpatch.pl` or `sqlpatch.pm`, and `orahome` on Linux/UNIX systems. On Windows systems, these files include `orahome.exe`. Do not change or remove these files.

**Related Topics**

- [Specifying Initialization Parameters at Startup](../admin/starting-up-and-shutting-down.md)

**Parent topic:** Upgrading Manually with Parallel Upgrade Utility

### Parallel Upgrade Utility (catctl.pl) Parameters

Control how the Parallel Upgrade Utility (`catctl.pl`) runs. You can also use these arguments to run the `dbupgrade` shell command.

**Note:**

The shell command utility `dbupgrade` starts `catctl.pl`. The dbupgrade utility resides in the `ORACLE_HOME/bin` directory. You can use the shell command utility to start the Parallel Upgrade Utility at the command prompt. You can either run the utility using default values, or you can use `catctl.pl` input parameters to specify Parallel Upgrade Utility arguments.

Table 4-1 Parallel Upgrade Utility (catctl.pl) Parameters

| Parameter | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|:----------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `-c`      | Specifies a space-delimited inclusion list for PDBs that you want to upgrade. For example, in an Oracle Multitenant deployment with PDB1, PDB2, PDB3, and PDB4, include PDB1 and PDB2, but exclude the PDBs not named. PDB 1 and PDB 2 are upgraded, but PDB 3 and PDB4 are not upgraded.<br>Linux and UNIX (use single quotes):<br>`-c 'PDB1 PDB2'`<br>Windows (use double quotes):<br>`-c "PDB1 PDB2"`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-C`      | Specifies a space-delimited exclusion list for PDBs that you want to upgrade. For example, in an Oracle Multitenant deployment with PDB1, PDB2, PDB3, and PDB4, you can use an exclusion list to exclude PDB1 and PDB2, but include the PDBs not named. PDB1 and PDB2 are not upgraded, but PDB3 and PDB4 are upgraded.<br>Linux and UNIX (use single quotes):<br>`-C 'PDB1 PDB2'`<br>Windows (use double quotes):<br>`-C "PDB1 PDB2"`<br>Note: `-c` and `-C` are mutually exclusive.<br>`-C 'CATCTL_LISTONLY'` is an option that specifies that the Parallel Upgrade Utility processes only the PDBs in a priority list. Use this option with the `-L` parameter, specifying a list.                                                                                                                                                                                                                                                                                                        |
| `-d`      | Specifies the location of the directory containing the files that you want processed.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-e`      | Sets echo OFF while running the scripts. The default is echo ON.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `-E`      | Enables you to run an upgrade emulation.<br>You can use the `-E` parameter to run the Parallel Upgrade Utility in emulation mode to test how priority lists run, or to test how other upgrade parameter selections are carried out during an upgrade. For example, you can run an upgrade emulation to obtain more information about how the resource allocation choices you make using the `-n` and `-N` parameters are carried out.<br>To carry out an upgrade emulation, complete all upgrade preparations before you run the Parallel Upgrade Utility, and then run the command using `-E`.<br>When you run the Parallel Upgrade Utility with the `-E` parameter, and call a priority list as part of the command using the `-L` parameter, the utility writes the upgrade order to the file `catctl_priority_run.lst`. This list is placed in the file path that you specify by the `-l` parameter, or in the default log file area if you do not specify a different output file path. |
| `-F`      | Forces a cleanup of previous upgrade errors.<br>Non-CDB databases require only the `-F` parameter. For CDBs, use this option with a space-delimited inclusion list, which you specify with `-c`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `-i`      | Specifies an identifier to use when creating spool log files.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `-l`      | Specifies the location for the directory to use for spool log files.<br>The default location is `Oracle_base``/cfgtoollogs/dbname/upgrade``date``time`. The `date` and `time` strings are in the character string format YYYYMMDDHHMMSC, in which YYYY designates the year, MM designates the month, DD designates the day, HH designates the hour, MM designates the minute, and SC designates the second.<br>Oracle strongly recommends that you do not write log files to the `/admin` directory.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `-L`      | Upgrades PDBs using a priority list during an Oracle Database upgrade, and specifies the priority list name. The priority list updates priority status in the database during upgrade. This priority listing is maintained in future upgrades.<br>By default the CDB\$ROOT and PDB\$SEED databases are always processed first. They are processed first even if they are not added to a priority list. All PDBs in the priority list are processed before PDBs not in the priority list.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `-M`      | Keeps CDB\$ROOT in UPGRADE mode while the PDBs are upgraded.<br>For non-CDBs, this parameter is ignored.<br>During CDB upgrades, using this parameter setting places the CDB and all its PDBs in upgrade mode, which can reduce total upgrade time. However, you cannot bring up any of the PDBs until the CDB and all its PDBs are upgraded.<br>By default, if you do not use the `-M` parameter setting, then CDB\$ROOT is upgraded and restarted in normal mode, and the normal background processes are started. As each PDB is upgraded, you can bring the PDB online while other PDBs are still being upgraded.                                                                                                                                                                                                                                                                                                                                                                        |
| `-n`      | Specifies the number of processes to use for parallel operations.<br>Non-CDBs: The `-n` parameter specifies the number of SQL processes to use when upgrading the database.<br>Multitenant architecture databases (CDBs): The number of PDBs upgraded concurrently is controlled by the value of the `-n` parameter. Multiple PDB upgrades are processed together. Starting in Oracle Database 12c, the default value for multitenant architecture databases is the number of CPUs on your system. A cpu_count equal to 24 equates to a default value of 24 for `-n`.<br>Values for the `-n` parameter:<br>Non-CDBs: The maximum value for `-n` is 8. The minimum value is 1. The default value is 4.<br>Multitenant architecture databases (CDBs): The maximum value for `-n` is unlimited. The minimum value is 4. The maximum PDB upgrades running concurrently is the value of `-n` divided by the value of `-N`.                                                                        |
| `-N`      | Specifies the number of SQL processors to use when upgrading PDBs.<br>For non-CDBs, this parameter is ignored.<br>For CDBs, the maximum value is 8. The minimum value is 1. The default value is 2.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
| `-p`      | Restarts from the specified phase. When you re-run an upgrade, it does not restart phases already completed successfully.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
| `-P`      | Stops from the specified phase.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-R`      | Resumes the upgrade from a failed phase. Using the `-R` parameter enables the upgrade to resume at the point of failure, so that only the missing upgrade phases are rerun.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `-s`      | Names the SQL script that initializes sessions.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `-S`      | Specifies serial upgrade instead of parallel.<br>Starting with Oracle Database 12.2, `catupgrd.sql` is no longer supported using the `-S` option.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| `-T`      | Takes offline user schema-based table spaces.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
| `-u`      | Specifies user name, and prompts for password.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| `-y`      | Displays phases only.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
| `-z`      | Turns on production debugging information for `catcon.pm`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| `-Z`      | Turns on debug tracing information for `catctl.pl`.<br>For example, to set the number to 1, enter -Z 1.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

**Parent topic:** Upgrading Manually with Parallel Upgrade Utility

### Example of Using the Parallel Upgrade Utility

Use this example to understand how you can run the parallel upgrade utility manually to perform upgrades.

The Parallel Upgrade Utility (`catctl.pl`) is integrated with AutoUpgrade and DBUA. The `catctl.pl` Perl script uses classic upgrade to upgrade `CDB$ROOT`. You can also run the Parallel Upgrade Utility manually by using the command-line script `dbupgrade`. Run the Parallel Upgrade Utility using the command-line parameters to specify how you want the upgrade to run. For example, to run the utility in serial mode instead of using parallel operations, specify the `-n 1` option.

Example 4-1 Running Parallel Upgrade Utility with Parameters for CDB and Non-CDB Databases

If you use the option `-n 4` when you run the Parallel Upgrade Utility, then the upgrade process creates `catupgrd0.log`, `catupgrd1.log`, `catupgrd2.log`, and `catupgrd3.log`. Check all of the `catupgrd`\#`.log` files to confirm that the upgrade succeeded. If the upgrade failed, and you fix issues and run the Parallel Upgrade Utility again, then the previous log files are overwritten, unless you specify a different log directory by using the `-l` parameter.

For example:

    cd $ORACLE_HOME/bin
    dbupgrade -n 4 -l $ORACLE_HOME/diagnostics

Example 4-2 Running Parallel Upgrades on Multiple Pluggable Databases (PDBs) Using Parallel Upgrade Utility

These examples show how parameter settings change the way that the Parallel Upgrade Utility performs the upgrade on multiple PDBs.

**Note:**

In your upgrade plans, be aware of the following:

- The `CDB$ROOT` defaults to a minimum value of 4 SQL processes, and to a maximum value of 8

- The default value for `-N` is 2.

- `PDB$SEED` always counts as one (1) PDB in the upgrade cycles

- The default for the Parallel Upgrade Utility parameter `-n` is the value of the `CPU_COUNT` parameter

In the following examples, the system is an Oracle Multitenant Oracle Database system that has a `CPU_COUNT` value of 24.

Run the Parallel Upgrade Utility without specifying values for the parameters `-n` and `-N` (that is, accept the default value of -N, which is 2, and accept the default value of `-n` as the `CPU_COUNT` parameter value, which is 24). The following parallel processing occurs:

- 12 PDBs are upgraded in parallel (`CPU_COUNT` divided by 2)

- 2 parallel processes run for each PDB

Specify the value of `-n` as 64, and `-N` as 4. The following parallel processing occurs:

- 16 PDBs are upgraded together (64 divided by 4)

- 4 parallel processes run for each PDB

Specify the value of `-n` as 20, and `-N` as 2. The following parallel processing occurs:

- 10 PDBs are upgraded together (20 divided by 2)

- 2 parallel processes run for each PDB

Specify the value of `-n` as 10, and `-N` as 4. The following parallel processing occurs:

- 2 PDBs are upgraded together (10 divided by 4), rounded down.

- 4 parallel processes run for each PDB

Do not specify the value of `-n` (that is, accept the default value of `-n`, which is the value of the `CPU_COUNT` parameter), and specify the value of `-N` as 1. The following parallel processing occurs:

- 24 PDBs are upgraded together (`CPU_COUNT` value divided by 1)

- 1 process runs for each PDB

Specify a value for `-n` as 20, and do not specify the value for `-N` (that is, accept the default value of `-N`, which is 2). The following parallel processing occurs:

- 10 PDBs are upgraded together (20 divided by 2)

- 2 parallel processes run for each PDB

**Parent topic:** Upgrading Manually with Parallel Upgrade Utility
