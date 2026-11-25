Using the In-Parallel technique, you can upgrade the CDB, and then immediately upgrade PDBs using parallel SQL processors.

Container databases (CDBs) can contain zero, one, or more pluggable databases (PDBs). By default, the Parallel Upgrade Utility (`catctl.pl`) updates the CDB and all of its PDBs in the same upgrade window. The Parallel Upgrade Utility uses the number of computer processing units (CPUs) to determine the maximum number of PDBs that are upgraded simultaneously. The number of PDBs that are upgraded in parallel is determined by dividing the parallel SQL process count (`-n` option) by the parallel PDB SQL process count (`-N` option).

**Note:**

You must plan your upgrade window to accommodate a common downtime for all of the database services that the PDBs on the CDB are providing.

### Pluggable Database Upgrade Syntax

`dbupgrade [-M] -n ` \[-N\]

- `-M` Specifies if CDB\$ROOT is kept in upgrade mode, or if it becomes available when it completes upgrade:

  - If you run the Parallel Upgrade Utility with the `-M` parameter, then the upgrade places CDB\$ROOT and all of its PDBs in upgrade mode, which can reduce total upgrade time. However, you cannot bring up any of the PDBs until the CDB and all of its PDBs are upgraded.

  - If you do not run the Parallel Upgrade Utility with the `-M` parameter, then CDB\$ROOT is upgraded and restarted in normal mode, and the normal background processes are started. After a successful upgrade, only CDB\$ROOT is opened in read/write mode. All the PDBs remain in MOUNT mode. As each PDB is upgraded, you can bring each PDB online while other PDBs are still being upgraded.

- `-n` Specifies the number of in-parallel PDB upgrade processors.

  If you do not specify a value for `-n`, then the default for `-n` is the `CPU_COUNT` value.

  If you do specify a value for `-n`, then that value is used to determine the number of parallel SQL processes. The maximum value is unlimited. The minimum value is 4.

- `-N` Specifies the number of SQL processors to use when upgrading PDBs. The maximum value is 8. The minimum value is 1. If you do not specify a value for `-N`, then the default value is 2.

- The maximum PDB upgrades running concurrently is the value of `-n` divided by the value of `-N`.

The following is a high-level list of actions during the In Parallel PDB upgrade technique:

1.  Make sure that your backup strategy is complete.

2.  Run the Pre-Upgrade tool. Fix any issue that is reported.. The Pre-Upgrade Tool (`preupgrade.jar`) is shipped with the new Oracle database release.

3.  Run the Parallel Upgrade Utility. In sequence, the following upgrades are carried out:

    1.  Cycle 1: CDB\$ROOT is upgraded to the new Oracle release

    2.  Cycle 2 to Cycle x: PDB\$SEED and PDBs are upgraded in parallel, with the number of cycles of upgrades as determined by the parameter settings you specify with `-n`.

4.  Complete post-upgrade steps.

Example 1-1 Example of Multitenant Architecture Upgrade Using Defaults (No Parameters Set)

In this scenario, your `CPU_COUNT` value is equal to 24. If you do not specify a value for in-parallel PDB processors using the `-n` option, then the default value for in-parallel PDB processors (`-n`) is equal to 24. If you do not specify a value for `-N`, then the default value for the number of SQL processors (`-N`) is 2.

Result:

12 PDBs are upgraded in parallel (`CPU_COUNT` divided by 2, or 24 divided by 2.) There are 2 parallel SQL processes allocated for each PDB.

Example 1-2 Example of Multitenant Architecture Upgrade Using 64 In Parallel PDB Upgrade Processors and 4 Parallel SQL Processes

In this scenario you set the value of in-parallel PDB upgrade processors to 64 by specifying the option `-n 64`. You specify the value of parallel SQL processors to 4 by specifying the option `-N 4`.

Result:

16 PDBs are upgraded in parallel ( 64 divided by 4). There are 4 parallel SQL processes for each PDB.

Example 1-3 Example of Multitenant Architecture Upgrade Using 20 In Parallel PDB Upgrade Processors and 2 Parallel SQL Processes

In this scenario you se the value of in-parallel PDB upgrade processors to 20 by specifying the option `-n 20`. You specify the value of parallel SQL processors to 2 by specifying the option `-N 2`.

Result:

10 PDBs are upgraded in parallel (20 divided by 2). There are 2 parallel SQL processes for each PDB.

Example 1-4 Example of Multitenant Architecture Upgrade Using 10 In Parallel PDB Upgrade Processors and 4 Parallel SQL Processes

In this scenario you se the value of in-parallel PDB upgrade processors to 10 by specifying the option `-n 10`. You specify the value of parallel SQL processors to 2 by specifying the option `-N 4`.

Result:

2 PDBs are upgraded in parallel (10 divided by 4). There are 4 parallel SQL processes for each PDB.

**Parent topic:** [Upgrading Multitenant Architecture In Parallel](upgrading-multitenant-architecture-in-parallel.md)
