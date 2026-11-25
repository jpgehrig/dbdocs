## Testing the Upgrade Process for Oracle Database

Your test plan for Oracle Database upgrades should include these test procedures.

Oracle recommends that you create a full working copy of your database environment in which to test all the pre-upgrade, upgrade, and post-upgrade processes.

You can create a test environment that does not interfere with the current production Oracle database. Oracle Data Guard, for example, enables you to create physical and snapshot standby databases.

Your test environment depends on the upgrade method you choose:

- If you plan to use DBUA or perform a manual upgrade, then create a test version of the current production database.

- If you plan to use Data Pump Export/Import, then export and import in stages, using subsets of the current production database.

Practice upgrading the database using the test environment. The best practice is to perform testing of the upgrade process on an exact copy of the database that you want to upgrade, rather than on a downsized copy or test data. If an exact copy is impractical, then carefully chose a representative subset of your data to move over to your test environment and test the upgrade on that data.

- Example of Testing Upgrades Using Priority List Emulation
  You can use the Parallel Upgrade Utility on multitenant architecture Oracle Databases to run upgrade emulations to test your priority list or other parameter settings before you run your upgrade.
- Upgrade Oracle Call Interface (OCI) and Precompiler Applications
  Upgrade any Oracle Call Interface (OCI) and precompiler applications that you plan to use with the new release of Oracle Database.

**See Also:**

- [Oracle Database Testing Guide](../ratug/testing-a-database-upgrade.md) for information about testing a database upgrade

- [Oracle Database Utilities](../sutil/oracle-data-pump-overview.md) for information on Data Pump Export and Import utilities

- [Oracle Data Guard Concepts and Administration](../sbydb/managing-oracle-data-guard-physical-standby-databases.md) for information on physical and snapshot standby databases

**Parent topic:** [Preparing to Upgrade Oracle Database](tasks-prepare-upgrade-oracle-database.md)

### Example of Testing Upgrades Using Priority List Emulation

You can use the Parallel Upgrade Utility on multitenant architecture Oracle Databases to run upgrade emulations to test your priority list or other parameter settings before you run your upgrade.

On multitenant architecture Oracle Database systems, starting with Oracle Database 12c release 2 (12.2), you can use priority lists to upgrade or exclude specific PDBs, or to set a specific upgrade priority order. Running the Parallel Upgrade Utility using priority emulation is a way to test your priority list without actually running the upgrade. Use the Parallel Upgrade Utility emulation feature to test your upgrade plan using priority lists.

#### Preparing for Upgrade Emulation Tests

Before you run the emulation, you must set up your source and target upgrade locations, and prepare your database in the same way you prepare for an actual upgrade. No upgrade actually occurs, but the Parallel Upgrade Utility generates log files that show how an actual upgrade is carried out.

**Note:**

You can use the `-E` parameter to run the Parallel Upgrade Utility in emulation mode to test how priority lists run, or to test how other upgrade parameter selections are carried out during an upgrade. For example, you can run an upgrade emulation to obtain more information about how the resource allocation choices you make using the `-n` and `-N` parameters are carried out.

#### Syntax for Running Priority List Emulation

You can use any of the parameter settings that you normally use with the Parallel Upgrade Utility, However, you must create a priority list, and you must use the `-L` parameter to call the list when you run the Parallel Upgrade Utility with the `-E` parameter to set it to perform an upgrade emulation.

The following is an example of the minimum required syntax for running the Parallel Upgrade Utility using priority list emulation, where `priority_list_name` is the name of your priority list file:

    catctl -E -L priority_list_name catupgrd.sql

Example 2-6 Example of Running the Parallel Upgrade Utility using Priority List Emulation

The following example uses this priority list, which is named `plist.txt`:

    1,CDB$ROOT
    2,PDB$SEED
    3,CDB1_PDB2
    4,CDB1_PDB4
    4,CDB1_PDB3
    5,CDB1_PDB5
    5,CDB1_PDB1

The following command runs a parallel emulation, calling this priority list:

    $ORACLE_HOME/perl/bin/perl catctl.pl -L plist.txt -E -n 4 -N 2 catupgrd.sql

This command uses the following parameter settings:

- `-E `specifies that Parallel Upgrade Utility runs the upgrade procedures in emulation mode.

- `-n 4` specifies that the upgrade allocates four processes to perform parallel upgrade operations.

- `-N 2` specifies that the upgrade runs two SQL processors to upgrade the PDBs. The maximum PDB upgrades running concurrently is the value of `-n` divided by the value of `-N`, so the upgrade runs no more than two concurrent PDB upgrades.

- `-L` specifies the priority list that the command reads to set upgrade priority.

As the Parallel Upgrade Utility carries out the emulated upgrade, it displays on screen the same output that you see during an actual upgrade.

When the upgrade emulation completes, it generates a log file, `catctl_prority_run.list`, which is stored either in the default logging directory, or in a logging directory location that you specify with the `-l` parameter. Because in this example we did not specify a different log directory, and we are running the upgrade on the container database named `CDB1`, the output is place in the path `Oracle_base``/cfgtoollogs/CDB1/run`, where `Oracle_base` is the Oracle base of the user running the upgrade, and `CDB1` is the name of the container database (CDB) on which you are running the upgrade.

The log file `catctl_priority_run.lst` displays the list of how the upgrade priority was carried out during the upgrade emulation. It shows how the Parallel Upgrade Utility grouped PDB upgrades. You can see a priority run that contains the groupings and priorities before you actually carry out the upgrade. The log file generated by the upgrade is also displayed on the screen after the upgrade completes.

At the conclusion of the upgrade log, the log will show that `CDB$ROOT` is upgraded first. After the CDB\$ROOT upgrade is completed, the Parallel Upgrade Utility carries out the following concurrent upgrades of PDBs, in accordance with the priority settings in the priority list:

1.  `PDB$SEED` and `CDB1_PDB2`. Output logs are generated with log ldentifiers (Log IDs) specified as `pdb_seed` for `PDB$SEED`, and log ID `mayapdb2` for `CDB_1PDB2`)

2.  `CDB1_PDB3` and `CDB1_PDB4`. Log IDs are specified `mayapdb3` and `mayapdb4`

3.  `CDB1_PDB5` and `CDB1_PDB6`. Log IDs are specified `mayapdb5` and `mayapdb6`

4.  `CDB1_PDB1`. The log ID is specified as `mayapdb1`.

**Related Topics**

- [About the Parallel Upgrade Utility for Oracle Database (CATCTL.PL and DBUPGRADE)](upgrading-parallel-upgrade-utility-catctl-pl.md)
- [Parallel Upgrade Utility (catctl.pl) Parameters](upgrading-parallel-upgrade-utility-catctl-pl.md)

**Parent topic:** Testing the Upgrade Process for Oracle Database

### Upgrade Oracle Call Interface (OCI) and Precompiler Applications

Upgrade any Oracle Call Interface (OCI) and precompiler applications that you plan to use with the new release of Oracle Database.

Oracle recommends that you test these applications on a test database before you upgrade your current production database.

**Related Topics**

- [About Upgrading Precompiler and OCI Applications in Oracle Database](-upgrade-precompiler-oci-apps-oracle-database.md)

**Parent topic:** Testing the Upgrade Process for Oracle Database
