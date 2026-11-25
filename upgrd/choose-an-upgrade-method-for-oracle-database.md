## Choose an Upgrade Method for Oracle Database

Oracle offers several methods to upgrade your database, which support the complexities of your enterprise.

- The AutoUpgrade Utility Method for Upgrading Oracle Database
  The AutoUpgrade utility identifies issues before upgrades, performs pre- and postupgrade actions, deploys upgrades, performs postupgrade actions, and starts the upgraded Oracle Database.
- The Graphical User Interface Method for Upgrading Oracle Database
  Database Upgrade Assistant (DBUA) interactively steps you through the upgrade process and configures the database for the new Oracle Database release.
- The Manual, Command-Line Method for Upgrading Oracle Database
  Manual upgrades give you finer control over the upgrade process.
- The Export/Import Method for Migrating Data When Upgrading Oracle Database
  You can use Oracle Data Pump to carry out data exports and imports.
- The Graphical User Interface Method for Upgrading Oracle Database
  Database Upgrade Assistant (DBUA) interactively steps you through the upgrade process and configures the database for the new Oracle Database release.

**Parent topic:** [Tasks to Prepare for Oracle Database Upgrades](tasks-to-prepare-for-oracle-database-upgrades.md)

### The AutoUpgrade Utility Method for Upgrading Oracle Database

The AutoUpgrade utility identifies issues before upgrades, performs pre- and postupgrade actions, deploys upgrades, performs postupgrade actions, and starts the upgraded Oracle Database.

Oracle recommends that you download the most recent version of the AutoUpgrade Utility from My Oracle Support Document 2485457.1, and use `autoupgrade.jar` to prepare for and to deploy your upgrade. The AutoUpgrade utility is designed to automate the upgrade process, both before starting upgrades, during upgrade deployments, and during postupgrade checks and configuration migration. You use AutoUpgrade after you have downloaded binaries for the new Oracle Database release, and set up new release Oracle homes. When you use AutoUpgrade, you can upgrade multiple Oracle Database deployments at the same time, using a single configuration file, customized as needed for each database deployment. Starting with Oracle Database 21c, when you have an existing target release CDB, you can use AutoUpgrade to convert a non-CDB Oracle Database to a PDB on the target release CDB during the upgrade.

With AutoUpgrade, when you have an existing target release CDB, you can use AutoUpgrade to convert a non-CDB Oracle Database to a PDB on the target release CDB during the upgrade.

Starting with AutoUpgrade version 22.1, Oracle provides REST APIs that enable you to perform upgrades remotely over SSH using Oracle REST Data Services (ORDS) or Oracle Cloud Infrastructure (OCI) REST API. The ORDS database API is a database management and monitoring REST API embedded into Oracle REST Data Services. The OCI REST API is enabled by configuring the REST Adapter connection to use the OCI Signature Version 1 security policy. You can now use these features to run AutoUpgrade upgrades remotely over HTTPS or HTTP.

The minimum `COMPATIBLE` parameter setting for the source database must be at least 12.2.0. If the `COMPATIBLE` setting is a lower version, then during the conversion and upgrade process, `COMPATIBLE` is set to 12.2.0. During the conversion, the original datafiles are retained. They are not copied to create the new PDB. To enable AutoUpgrade to perform the upgrade, edit the AutoUpgrade configuration file to set the AutoUpgrade parameters `target_version `to the target CDB release, and identify the CDB to which the upgraded database is placed using `target_cdb`. During the conversion and upgrade process, AutoUpgrade uses that information to complete the upgrade to the target CDB.

**Caution:**

Before you run AutoUpgrade to complete the conversion and upgrade. Oracle strongly recommends that you create a full backup of your source database, and complete thorough testing of the upgrade. There is no option to roll back to the non-CDB Oracle Database state after AutoUpgrade starts this procedure.

**Parent topic:** Choose an Upgrade Method for Oracle Database

### The Graphical User Interface Method for Upgrading Oracle Database

Database Upgrade Assistant (DBUA) interactively steps you through the upgrade process and configures the database for the new Oracle Database release.

The preferred option for upgrading Oracle Database is to use the AutoUpgrade utility. However, in Oracle Database 19c, you can still use DBUA to upgrade multitenant architecture container databases (CDB), and pluggable databases (PDBs).

DBUA starts AutoUpgrrade using the preupgrade parameter (autoupgrade.jar -preupgrade -mode), which fixes some configuration settings to the values required for the upgrade. For example, the tool can change initialization parameters to values required for the upgrade. The tool also provides you with a list of items that you can fix manually before you continue with the upgrade.

**Parent topic:** Choose an Upgrade Method for Oracle Database

### The Manual, Command-Line Method for Upgrading Oracle Database

Manual upgrades give you finer control over the upgrade process.

A manual upgrade consists of running SQL scripts and utilities from a command line to upgrade a database to the new Oracle Database release.

#### Before the Upgrade

- Analyze the database using AutoUpgrade (`autoupgrade.jar -mode analyze`)

  The AutoUpgrade Analyze (analyze) processing mode checks your database to see if it is ready for upgrade. When you run AutoUpgrade in Analyze mode, AutoUpgrade only reads data from the database, and does not perform any updates to the database. You can run AutoUpgrade using the Analyze mode during normal business hours. You can run AutoUpgrade in Analyze mode on your source Oracle Database home before you have set up your target release Oracle Database home.

- Prepare the new Oracle home.

- Perform a backup of the database.

**Parent topic:** Choose an Upgrade Method for Oracle Database

### The Export/Import Method for Migrating Data When Upgrading Oracle Database

You can use Oracle Data Pump to carry out data exports and imports.

Topics:

- The Effects of Export/Import on Upgraded Oracle Databases
  Review this topic to understand the benefits of Export/Import data migration.
- Export/Import Benefits for Migrating Data for Oracle Database
  Migrating data when upgrading Oracle Database using Export/Import provides benefits that can increase performance.
- Time Requirements for Migrating Data with Export/Import
  Understand the time it takes for data migration using Oracle Data Pump.

**Parent topic:** Choose an Upgrade Method for Oracle Database

#### The Effects of Export/Import on Upgraded Oracle Databases

Review this topic to understand the benefits of Export/Import data migration.

The Export/Import data migration method does not change the current database, which enables the database to remain available throughout the upgrade process. However, if a consistent snapshot of the database is required (for data integrity or other purposes), then the database must run in restricted mode or must otherwise be protected from changes during the export procedure. Because the current database can remain available, you can, for example, keep an existing production database running while the newly upgraded Oracle Database database is being built at the same time by Export/Import. During the upgrade, to maintain complete database consistency, changes to the data in the database cannot be permitted without the same changes to the data in the newly upgraded Oracle database.

Most importantly, the Export/Import operation results in a completely new database. Although the current target database ultimately contains a copy of the specified data that you migrated, the upgraded database can perform differently from the original source database. Although Export/Import creates an identical copy of the database, other factors can cause unexpected performance issues. (For example: disk placement of data, and unset tuning parameters).

**Parent topic:** The Export/Import Method for Migrating Data When Upgrading Oracle Database

#### Export/Import Benefits for Migrating Data for Oracle Database

Migrating data when upgrading Oracle Database using Export/Import provides benefits that can increase performance.

Using Export/Import to migrate data provides the following benefits:

- Defragments the data. You can compress the imported data to improve performance.

- Restructures the database. You can create new tablespaces or modify existing tables, tablespaces, or partitions that you want to populate with imported data.

- Facilitates side-by-side testing of the old and new releases of Oracle Database because an entirely new database is created.

- Enables the copying of specified database objects or users. Importing only the objects, users, and other items you need is useful for establishing a test environment for the new software on only a subset of the production data. Data Pump Export/Import provides flexible data-subsetting capabilities.

- Serves as a backup archive. You can use a full database export as an archive of the current database.

- Enables you to establish the upgraded database on a different operating system or hardware platform than the platform on which your earlier release database is placed.

- Network-based Data Pump Import enables you to load the new release Oracle Database directly across the network for your earlier release Oracle Database. By using network-based Data Pump import, you are not required to use intervening dump files.

**Parent topic:** The Export/Import Method for Migrating Data When Upgrading Oracle Database

#### Time Requirements for Migrating Data with Export/Import

Understand the time it takes for data migration using Oracle Data Pump.

Migrating an entire Oracle Database by using Oracle Data Pump using Export/Import can take a long time, especially compared to using DBUA or performing a manual upgrade. If you use Oracle Data Pump to migrate data, then schedule the migration during non-peak hours or make provisions for propagating to the new database any changes that are made to the current database during the upgrade.

**Parent topic:** The Export/Import Method for Migrating Data When Upgrading Oracle Database

### The Graphical User Interface Method for Upgrading Oracle Database

Database Upgrade Assistant (DBUA) interactively steps you through the upgrade process and configures the database for the new Oracle Database release.

The preferred option for upgrading Oracle Database is to use the AutoUpgrade utility. However, in Oracle Database 19c, you can still use DBUA to upgrade multitenant architecture container databases (CDB), and pluggable databases (PDBs).

DBUA starts AutoUpgrrade using the preupgrade parameter (autoupgrade.jar -preupgrade -mode), which fixes some configuration settings to the values required for the upgrade. For example, the tool can change initialization parameters to values required for the upgrade. The tool also provides you with a list of items that you can fix manually before you continue with the upgrade.

**Parent topic:** Choose an Upgrade Method for Oracle Database
