Manual upgrades give you finer control over the upgrade process.

A manual upgrade consists of running SQL scripts and utilities from a command line to upgrade a database to the new Oracle Database release.

### Before the Upgrade

- Analyze the database using the Pre-Upgrade Information Tool.

  The Pre-Upgrade Information Tool is a Java JAR file that is supplied with Oracle Database. When you start the tool, it self-extracts, and then executes SQL scripts.

  The Pre-Upgrade Information Tool displays warnings about possible upgrade issues with the database, and generates fixup scripts for you to use to address some issues. It also displays information about required initialization parameters for the new release of Oracle Database.

- Prepare the new Oracle home.

- Perform a backup of the database.

Depending on the Oracle Database release you upgrade, you can be required to perform more pre-upgrade steps. These steps can include adjusting the parameter file for the upgrade, removing desupported initialization parameters, or adjusting initialization parameters that can cause upgrade problems.

**Parent topic:** [Preparing to Upgrade Oracle Database](preparing-to-upgrade.md)
