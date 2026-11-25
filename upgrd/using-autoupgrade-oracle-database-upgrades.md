## 3 Using AutoUpgrade for Oracle Database Upgrades

Learn how to use AutoUpgrade to simplify your upgrade tasks.

- [About Oracle Database AutoUpgrade](about-oracle-database-autoupgrade.md)
  The AutoUpgrade utility is designed to automate the upgrade process, both before starting upgrades, during upgrade deployments, and during postupgrade checks and configuration migration
- [Examples of How to Use AutoUpgrade](examples-of-autoupgrade-workflows.md)
  To guide your upgrade, use the AutoUpgrade workflow example that matches your upgrade use case.
- [AutoUpgrade Messages and Process Description Terms](autoupgrade-messages-process-description-terms.md)
  To understand how your upgrade checks and operations are proceeding, learn about the AutoUpgrade utility messages that are generated as the utility runs.
- [About AutoUpgrade Processing Modes](about-autoupgrade-processing-modes.md)
  The four AutoUpgrade processing modes (Analyze, Fixup, Deploy, and Upgrade) characterize the actions that AutoUpgrade performs as it runs.
- [Understanding AutoUpgrade Workflows and Stages](understanding-autoupgrade-workflows-stages.md)
  The AutoUpgrade workflow automates each step of a typical upgrade process. The stages that run depend on the processing mode that you select.
- [Understanding Non-CDB to PDB Upgrades with AutoUpgrade](understanding-non-cdb-to-pdb-upgrades-autoupgrade.md)
  You can upgrade and convert a non-CDB to a PDB in a new CDB in a single operation, or upgrade and then convert a Non-CDB database to a PDB in a pre-existing CDB.
- [Understanding Unplug-Plug Upgrades with AutoUpgrade](understanding-pdb-unplug-plug-upgrades-autoupgrade.md)
  AutoUpgrade can perform an unplug of a pluggable database (PDB) from an earlier release source container database (CDB), plug it into a later release target CDB, and then complete all the steps required to upgrade the PDB to the target CDB release.
- [AutoUpgrade Command-Line Parameters and Options](autoupgrade-command-line-parameters.md)
  Review the AutoUpgrade parameters and select the parameters and options for your Oracle Database upgrade use case.
- [AutoUpgrade Utility Configuration Files Parameters and Options](autoupgrade-utility-configuration-files.md)
  AutoUpgrade configuration files contain all the information required to perform Oracle Database upgrades.
- [AutoUpgrade and Oracle Database Configuration Options](autoupgrade-oracle-database-config-options.md)
  When you run AutoUpgrade, it determines the type of database (Oracle Database, Oracle Database Standalone with Oracle ASM, or Oracle RAC), and performs an upgrade for that type of database
- [AutoUpgrade Patching](autoupgrade-patching.md)
  AutoUpgrade has enhanced capability that enables it to automate all of the necessary steps in the database patching process, including optional downloading of patches.
- [AutoUpgrade Configuration File Examples](autoupgrade-configuration-file-examples.md)
  Use these examples to understand how you can modify your own AutoUpgrade configuration files to perform a variety of configuration actions during the upgrade.
- [AutoUpgrade Internal Settings Configuration File](autoupgrade-internal-settings-config-file-parameters.md)
  Internal configuration settings control how AutoUpgrade runs.
- [AutoUpgrade Log File Structure](autoupgrade-log-file-structure.md)
  The AutoUpgrade utility produces a log file structure that includes job status and configuration files.
- [Enabling Full Deployments for AutoUpgrade](enabling-full-deployments-autoupgrade.md)
  To enable a guaranteed restore point (GRP) so that you can flashback an upgrade, you must set up archive logging, and you should complete other tasks to enable AutoUpgrade to complete the upgrade.
- [Examples of How to Use the AutoUpgrade Console](how-to-use-autoupgrade-console.md)
  The AutoUpgrade console provides a set of commands to monitor the progress of AutoUpgrade jobs. The console starts by default when you run the AutoUpgrade utility, and is enabled or disabled by the parameters `console` and `noconsole`.
- [Known Restrictions for AutoUpgrade](known-restrictions-autoupgrade.md)
  If you encounter issues with your upgrade, review the known restrictions to find solutions.
- [Proper Management of AutoUpgrade Database Changes](proper-management-autoupgrade-database-changes.md)
  AutoUpgrade is a powerful utility, which requires that you use it responsibly. Review and avoid using AutoUpgrade in ways that put the database at risk.
- [How to Override Default Fixups](how-to-override-default-fixups.md)
  You can use the `RUNFIX` column entry to disable automated fixups, except in cases where disabling the fixup violates security or Oracle policy.
- [Local Configuration File Parameter Fixups Checklist Example](config-file-parameter-fixups-checklist.md)
  To include or exclude specific fixups for individual databases during upgrades, use the local configuration file checklist.
- [AutoUpgrade and Microsoft Windows ACLs and CLIs](autoupgrade-microsoft-windows-access-cointrol-lists.md)
  When running AutoUpgrade on Microsoft Windows systems, Oracle recommends additional best practices with access control lists (ACLs) and command-line interfaces (CLIs).
