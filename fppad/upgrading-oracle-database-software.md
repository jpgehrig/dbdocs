## Upgrading Oracle Database

Fleet Patching and Provisioning provides two options for upgrading Oracle Database. Both options are performed with a single command.

The `rhpctl upgrade database` command performs a traditional upgrade incurring downtime. The `rhpctl zdtupgrade database` command performs an Oracle RAC or Oracle RAC One Node upgrade with minimal or no downtime.

You can use Fleet Patching and Provisioning to provision, scale, and patch Oracle Database 11g release 2 (11.2.0.4) and later releases. You can also upgrade Oracle Databases from 11g release 2 (11.2.0.4), 12c release 1 (12.1.0.2), 12c release 2 (12.2), and 18c to Oracle Database 19c. Refer to Oracle Database Upgrade Guide for information about Oracle Database direct upgrade paths.

**Note:**

The version of Oracle Grid Infrastructure on which the pre-upgrade database is running must be the same version or higher than the version of the database to which you are upgrading.

The destination for the upgrade can be a working copy already provisioned, or you can choose to create the working copy of gold image as part of this operation.

The pre-upgrade database can be running on a working copy (a managed home that was provisioned by Fleet Patching and Provisioning) or on an unmanaged home. In the first case, you can roll back the upgrade process with a single RHPCTL command.

**Note:**

You can delete the source working copy at any time after completing an upgrade. Once you delete the working copy, however, you cannot perform a rollback. Also, use the `rhpctl delete workingcopy` command (as opposed to `rm`, for example) to remove the source working copy to keep the Fleet Patching and Provisioning inventory correct.

### Oracle Database AutoUpgrade

The AutoUpgrade utility identifies issues before upgrades, performs pre- and post-upgrade actions, deploys upgrades, and starts the upgraded Oracle Database. AutoUpgrade is included with each release update (RU).

Oracle FPP runs the `autoupgrade.jar` file that exists in the Oracle home. However, before you create a gold image, Oracle strongly recommends that you download the latest AutoUpgrade version. The most recent AutoUpgrade version is always available from My Oracle Support Document 2485457.1.

**Note:**

A general Oracle Database upgrade requires you to run Oracle Database Upgrade Assistant (DBUA), but you can use the `autoupg` option with the `rhpctl upgrade database` command to automate the upgrade.

**Related Topics**

- [rhpctl upgrade database](database-commands.md)
- [rhpctl zdtupgrade database](database-commands.md)
- [Using AutoUpgade for Oracle Database Upgrades](../upgrd/using-autoupgrade-oracle-database-upgrades.md)

**Parent topic:** [Patching and Upgrading Oracle Database](patching-and-upgrading-oracle-database.md)
