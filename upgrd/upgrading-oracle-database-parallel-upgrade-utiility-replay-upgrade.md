## 4 Upgrading Oracle Database Manually Using Parallel Upgrade Utility

You can upgrade manually by using the Parallel Upgrade Utility command-line option.

Starting with Oracle Database 19c, Database Upgrade Assistant (DBUA) is replaced by the AutoUpgrade utility.

**Caution:**

If you retain the old Oracle Database software, then never start the upgraded database with the old Oracle Database software. Only start the database with the executables in the new Oracle Database installation.

- [Upgrading Manually with Parallel Upgrade Utility](upgrading-parallel-upgrade-utility-catctl-pl.md)
  To run upgrades with scripts that you run and manage manually, you can use the Parallel Upgrade Utility (`catctl.pl`).
- [Manual Upgrade Scenarios for Multitenant Architecture Oracle Databases](manual-upgrade-scenarios-multitenant-architecture-oracle-databases.md)
  To prepare for manual upgrades, review the manual upgrade scenarios and procedures for Oracle Database deployed with multitenant architecture.
- [Example of Manual Upgrade of Windows Non-CDB Oracle Database](example-manual-upgrade-windows-non-cdb.md)
  These examples show the steps to complete preupgrade checks, upgrade, and postupgrade checks for an Oracle Database 11g Release 2 (11.2.0.4) upgrade to Oracle Database 19c.
- [About Dbupgrade Scripts and catupgrd.sql in Earlier Releases of Oracle Database](dbupgrade-scripts-catupgrd.sql-earlier-release.md)
  The function of the `catupgrd.sql` script is replaced by the Parallel Upgrade Utility, `catctl.pl`, and the `dbupgrade` and `dbupgrade.cmd` scripts.
- [About Transporting and Upgrading a Database (Full Transportable Export/Import)](transporting-upgrading-database-full-transportable-export-import.md)
  You can use file-based or nonfile-based modes for transporting data.
- [Upgrade Scenarios for Non-CDB Oracle Databases](upgrade-scenarios-non-cdb-oracle-databases.md)
  Review these topics to understand the upgrade scenarios and procedures for non-CDB Oracle Databases
- [Rerunning Upgrades for Oracle Database](rerunning-upgrades-oracle-database.md)
  Use these options to rerun upgrades.
