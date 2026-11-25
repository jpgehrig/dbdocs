Before you upgrade Oracle Database, review new features, and carry out procedures to prepare your database for upgrade.

**Note:**

Oracle strongly recommends that you test the upgrade process and prepare a backup strategy.

- [Installing Oracle Software in a New Oracle Home](installing-oracle-software-in-a-new-oracle-home.md)
  Choose a new location for the target Oracle home, and then install the new Oracle Database release software for single-instance.
- About Oracle Database AutoUpgrade
  The AutoUpgrade utility identifies issues before upgrades, performs pre- and postupgrade actions, deploys upgrades, performs postupgrade actions, and starts the upgraded Oracle Database.
- [Prepare a Backup Strategy Before Upgrading Oracle Database](prepare-a-backup-strategy-before-upgrading-db.md)
  You must design and carry out an appropriate backup strategy to ensure a successful upgrade.
- [Database Preparation Tasks to Complete Before Starting Oracle Database Upgrades](db-preparation-tasks-before-starting-db-upgrades.md)
  Ensure that you have completed these database preparation tasks before starting an Oracle Database upgrade.
- About the AutoUpgrade Analyze Processing Mode
  The AutoUpgrade Analyze (`analyze`) processing mode checks your database to see if it is ready for upgrade.
- AutoUpgrade with Source and Target Database Homes on Same Server (Typical)
  When your Oracle Database Source and Target Oracle homes are installed on the same physical server, use this example.
- [Enabling Oracle Database Vault After Upgrading Oracle Database](enabling-oracle-db-vault-after-upgrading-oracle-db.md)
  Depending on your target database release, you can be required to disable Oracle Database Vault to complete an Oracle Database upgrade.

### About Oracle Database AutoUpgrade

The AutoUpgrade utility identifies issues before upgrades, performs pre- and postupgrade actions, deploys upgrades, performs postupgrade actions, and starts the upgraded Oracle Database.

In place of `preupgrade.jar`, Oracle recommends that you download the most recent version of the AutoUpgrade Utility from My Oracle Support Document 2485457.1, and use `autoupgrade.jar -mode analyze`. The AutoUpgrade utility is designed to automate the upgrade process, both before starting upgrades with preupgrade checks, during upgrade deployments, and during postupgrade checks and configuration migration. You use AutoUpgrade after you have downloaded binaries for the new Oracle Database release, and set up new release Oracle homes. When you use AutoUpgrade, you can upgrade multiple Oracle Database deployments at the same time, using a single configuration file, customized as needed for each database deployment.

With the January 2019 Release Updates (`DBJAN2019RU`) and later updates, AutoUpgrade support is available for Oracle Database 12c Release 2 (12.2) and Oracle Database 18c (18.5) target homes. For both Oracle Database 12c Release 2 (12.2) and Oracle Database 18c (18.5) target homes, you must download the AutoUpgrade kit from My Oracle Support Document 2485457.1.

In Oracle Database 19c (19.3) and later target Oracle homes, the `autoupgrade.jar` file exists by default. However, before you use AutoUpgrade, Oracle strongly recommends that you download the latest AutoUpgrade version. AutoUpgrade is included with each release update (RU), but the most recent AutoUpgrade version is always available from My Oracle Support Document 2485457.1.

**Note:**

AutoUpgrade is available for Oracle Database Enterprise Edition, and Oracle Database Standard Edition. It is not available for Oracle Database Express Edition.

#### Preventing Issues: Analyze and Fixup Modes

Before the upgrade, in Analyze mode, the AutoUpgrade utility performs read-only analysis of databases before upgrade, so that it can identify issues that require fixing. You can run the utility during normal database operations. In Fixup Mode, the AutoUpgrade utility detects and identifies both fixes that require manual intervention, and fixes that the AutoUpgrade utility can perform during the upgrade deployment phase.

#### Simplifying Upgrades: Deploy and Upgrade Modes

In Deploy phase, the AutoUpgrade utility modifies the databases you indicate in your configuration file. It enables you to call your own custom scripts during the upgrade to configure databases. In many cases, the AutoUpgrade utility can perform automatic fixes to databases during the upgrade process without requiring manual intervention.

#### Deploy and Upgrade Postupgrade Checks and Fixes

After an upgrade completes with either Deploy or Upgrade modes, AutoUpgrade performs postupgrade checks. It provides a process where you can enable your custom scripts to be run on each of the upgraded databases, in accordance with the configuration instructions you provide in the AutoUpgrade configuration file, and also can run automatic postupgrade fixups as part of the postupgrade process. In Deploy mode, AutoUpgrade also confirms that the upgrade has succeeded, and copies database files such as `sqlnet.ora`, `tnsname.ora`, and `listener.ora` from the source home to the target home. After these actions are complete, the upgraded Oracle Database release is started in the new Oracle home.

**Related Topics**

- [My Oracle Support Document 2485457.1](https://support.oracle.com/rs?type=doc&id=2485457.1)

**Parent topic:** Preparing to Upgrade Oracle Database

### About the AutoUpgrade Analyze Processing Mode

The AutoUpgrade Analyze (`analyze`) processing mode checks your database to see if it is ready for upgrade.

When you run AutoUpgrade in Analyze mode, AutoUpgrade only reads data from the database, and does not perform any updates to the database. You can run AutoUpgrade using the Analyze mode during normal business hours. You can run AutoUpgrade in Analyze mode on your source Oracle Database home before you have set up your target release Oracle Database home.

You start AutoUpgrade in Analyze mode using the following syntax, where `Java-8-home` is the location of your Java 8 distribution, or the environment variable set for the Java 8 home:

    Java-8-home/bin/java -jar autoupgrade.jar -config yourconfig.txt -mode analyze

Oracle Database Release 12.2 (12.2.0.1) or newer Oracle homes have a valid java version by default. Start AutoUpgrade in Analyze mode using the following syntax, where `Oracle_home` is the Oracle home directory, or the environment variable set for the Oracle home, and `yourconfig.txt` is your configuration file:

    Oracle_home/jdk/bin/java -jar autoupgrade.jar -config yourconfig.txt -mode analyze

![Description of autoupgrade-analyze-flow.eps follows](img/autoupgrade-analyze-flow.png)
[Description of the illustration autoupgrade-analyze-flow.eps](img_text/autoupgrade-analyze-flow.md)

The AutoUpgrade Analyze mode produces two output files, which are given the name of the system identifier (`SID`) of the database that you check:

- `SID``.html`: View this file using a web browser.

<!-- -->

- `SID``_preupgrade.log`: View this file using a text editor.

Each report identifies upgrade errors that would occur if you do not correct them, either by running an automatic fixup script, or by manual correction. If errors occur, then they are reported in the user log file, and also in the `status.json` file.

The Analyze mode also generates a status directory in the path `cfgtoollogs/upgrade/auto/status`. This directory contains files that indicate if the analysis was successful or failed. This directory has two JSON files, `status.json` and `progress.json`:

- `status.json `: A high-level status JSON file that contains the final status of the upgrade.
- `progress.json`: A JSON file that contains the current progress of all upgrades being performed on behalf of the configuration file. If errors occur, then they are reported in the log file of the user running AutoUpgrade, and also in the `status.json` file.

If your target database Oracle home is not available on the server, then in your configuration file, you must set the source Oracle home parameters to the same path, so that the AutoUpgrade analyze processing mode can run. For example:

    #
    # Source Home
    #
    sales3.source_home=d:\app\oracle\product\12.1.0\dbhome_1
    #
    # Target Oracle Home
    #
    sales3.target_home=d:\app\oracle\product\19.1.0\dbhome_1

Earlier releases of AutoUpgrade required you to set `target_home` and `target_version`. In later releases of AutoUpgrade, this restriction has been lifted for both Analyze and Fixups modes.

**Parent topic:** Preparing to Upgrade Oracle Database

### AutoUpgrade with Source and Target Database Homes on Same Server (Typical)

When your Oracle Database Source and Target Oracle homes are installed on the same physical server, use this example.

Context: Source and Target homes are on the same server.

To start the analysis, enter the following command.

    java -jar autoupgrade.jar -config config.txt -mode analyze

The command produces a report that indicates any error conditions that the command finds. Review the error conditions.

To start the deployment of the upgrade, enter the following command:

    java -jar autoupgrade.jar -config config.txt -mode deploy

**Parent topic:** Preparing to Upgrade Oracle Database
