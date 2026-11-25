## About Oracle Database AutoUpgrade

The AutoUpgrade utility is designed to automate the upgrade process, both before starting upgrades, during upgrade deployments, and during postupgrade checks and configuration migration

When you perform upgrades, Oracle recommends that you download the most recent version of the AutoUpgrade utility (`autoupgrade.jar`) to prepare for and to deploy your upgrade. You use AutoUpgrade after you have downloaded binaries for the new Oracle Database release, and set up new release Oracle homes. When you use AutoUpgrade, you can upgrade multiple Oracle Database deployments at the same time, using a single configuration file, customized as needed for each database deployment. You can now download the latest AutoUpgrade utility release directly from the [Database Upgrades and Migrations](https://www.oracle.com/database/upgrades/) page without having to log in to My Oracle Support: [Download the AutoUpgrade utility](https://download.oracle.com/otn-pub/otn_software/autoupgrade.jar)

The `autoupgrade.jar` file exists by default in the Oracle home (`Oracle_home``/rdbms/admin`). However, before you use AutoUpgrade, Oracle strongly recommends that you download the latest AutoUpgrade version. AutoUpgrade is included with each release update (RU), but the most recent AutoUpgrade version is always available from the Database Upgrades and Migrations page.

**Note:**

AutoUpgrade is available for Oracle Database Enterprise Edition, and Oracle Database Standard Edition. It is not available for other Oracle Database editions.

### Preventing Issues: Analyze and Fixup Modes

Before the upgrade, in Analyze mode, the AutoUpgrade utility performs read-only analysis of databases before upgrade, so that it can identify issues that require fixing. You can run the utility during normal database operations. In Fixup Mode, the AutoUpgrade utility detects and identifies both fixes that require manual intervention, and fixes that the AutoUpgrade utility can perform during the upgrade deployment phase.

### Simplifying Upgrades: Deploy and Upgrade Modes

In Deploy phase, the AutoUpgrade utility modifies the databases you indicate in your configuration file. It enables you to call your own custom scripts during the upgrade to configure databases. In many cases, the AutoUpgrade utility can perform automatic fixes to databases during the upgrade process without requiring manual intervention.

### Deploy and Upgrade Postupgrade Checks and Fixes

After an upgrade completes with either Deploy or Upgrade modes, AutoUpgrade performs postupgrade checks. It provides a process where you can enable your custom scripts to be run on each of the upgraded databases, in accordance with the configuration instructions you provide in the AutoUpgrade configuration file, and also can run automatic postupgrade fixups as part of the postupgrade process. In Deploy mode, AutoUpgrade also confirms that the upgrade has succeeded, and copies database files such as `sqlnet.ora`, `tnsname.ora`, and `listener.ora` from the source home to the target home. After these actions are complete, the upgraded Oracle Database release is started in the new Oracle home.

### Try AutoUpgrade using our Hands-On Lab on Oracle LiveLabs

Oracle LiveLabs provides you with an environment in which you can try out Oracle technology in a free lab environment. Daniel Overby Hansen provides you with a demonstration of how you can use Oracle LiveLabs to set up your own demonstration lab environment in an Oracle Cloud environment. Check it out!

[Try AutoUpgrade using our Hands-On Lab on Oracle LiveLabs](https://www.youtube.com/watch?v=KeaWiqCRnTg)

**Related Topics**

- [Download the AutoUpgrade Utility (latest release)](https://download.oracle.com/otn-pub/otn_software/autoupgrade.jar)
- [Database Upgrades and Migration](https://www.oracle.com/database/upgrades/)
- [AutoUpgrade Tool (Doc ID 2485457.1)](https://support.oracle.com/rs?type=doc&id=2485457.1)
- [Oracle LiveLabs](https://apexapps.oracle.com/pls/apex/f?p=133:1)

**Parent topic:** [Using AutoUpgrade for Oracle Database Upgrades](using-autoupgrade-oracle-database-upgrades.md)
