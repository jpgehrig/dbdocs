## 2 New Features in 19c Release Updates

This chapter describes the features that are new in Oracle Database 19c Release Updates (RUs).

- Release Update 19.4 Features
- Release Update 19.5 Features
- Release Update 19.6 Features
- Release Update 19.7 Features
- Release Update 19.8 Features
- Release Update 19.9 Features
- Release Update 19.10 Features
- Release Update 19.11 Features
- Release Update 19.12 Features
- Release Update 19.13 Features
- Release Update 19.14 Features
- Release Update 19.15 Features
- Release Update 19.16 Features
- Release Update 19.17 Features
- Release Update 19.18 Features
- Release Update 19.19 Features
- Release Update 19.20 Features
- Release Update 19.21 Features
- Release Update 19.22.0.0 Features
- Release Update 19.23.0.0 Features
- Release Update 19.24 Features
- Release Update 19.25 Features
- Release Update 19.26 Features
- Release Update 19.27 Features
- Release Update 19.28 Features

### Release Update 19.4 Features

There are no new features for the 19.4 release update.

**Parent topic:** New Features in 19c Release Updates

### Release Update 19.5 Features

There are no new features for the 19.5 release update.

**Parent topic:** New Features in 19c Release Updates

### Release Update 19.6 Features

There are no new features for the 19.6 release update.

**Parent topic:** New Features in 19c Release Updates

### Release Update 19.7 Features

- SQL Macros (SQM)

**Parent topic:** New Features in 19c Release Updates

#### SQL Macros (SQM)

You can create SQL Macros (SQM) to factor out common SQL expressions and statements into reusable, parameterized constructs that can be used in other SQL statements. Starting with Oracle Database release 19c, version 19.7, SQL table macros are supported. SQL table macros are expressions, typically used in a `FROM` clause, to act as a sort of polymorphic (parameterized) view.

SQL macros increase developer productivity, simplify collaborative development, and improve code quality.

**Related Topics**

- [Oracle® Database PL/SQL Language Reference ](../lnpls/release-changes.md)

**Parent topic:** Release Update 19.7 Features

### Release Update 19.8 Features

- Database In-Memory Base Level
- CellMemory Level

**Parent topic:** New Features in 19c Release Updates

#### Database In-Memory Base Level

Database In-Memory is an option to Enterprise Edition. Database In-Memory now has a new Base Level feature. This allows the use of Database In-Memory with up to a 16GB column store without triggering any license tracking.

This feature allows you to use Database In-Memory without having to license the option. The column store is limited to 16GB when using the Base Level. This helps to show the value of Database In-Memory without having to worry about licensing issues.

**Related Topics**

- [Oracle® Database In-Memory Guide](../inmem/init-parameters-for-im-column-store.md)

**Parent topic:** Release Update 19.8 Features

#### CellMemory Level

You can use the CellMemory feature without enabling the IM column store by setting` INMEMORY_FORCE=CELLMEMORY_LEVEL` and `INMEMORY_SIZE=0`.

This feature allows you to use CellMemory without incurring the overhead of enabling the IM column store.

**Related Topics**

- [Oracle® Database In-Memory Guide](../inmem/init-parameters-for-im-column-store.md)

**Parent topic:** Release Update 19.8 Features

### Release Update 19.9 Features

- Oracle Grid Infrastructure SwitchHome
- Support for DBMS_CRYPTO Asymmetric Key Operations

**Parent topic:** New Features in 19c Release Updates

#### Oracle Grid Infrastructure SwitchHome

You can use the `-switchGridHome` option with `gridSetup.sh` to switch from one Oracle Grid Infrastructure home to another.

You can use the `-switchGridHome` option for patching and upgrading Oracle Grid Infrastructure. Use the `-switchGridHome` option to switch from the source Oracle Grid Infrastructure home to the patched Oracle Grid Infrastructure home. All Oracle Clusterware and Oracle Restart services start from the patched Oracle Grid Infrastructure home automatically.

**Related Topics**

- [Oracle® Grid Infrastructure Installation and Upgrade Guide for Linux](../cwaix/switching-oracle-grid-infrastructure-home-after-patching.md)

**Parent topic:** Release Update 19.9 Features

#### Support for DBMS_CRYPTO Asymmetric Key Operations

Starting with this release, the `DBMS_CRYPTO` PL/SQL package supports asymmetric key operations, in addition to the existing support for symmetric key operations.

To implement the support for asymmetric key operations, the following procedures have been added to the `DBMS_CRYPTO` package:

- `PKENCRYPT`
- `PKDECRYPT`
- `SIGN`
- `VERIFY`

**Related Topics**

- [Oracle® Database Security Guide](../dbseg/manually-encrypting-data.md)

**Parent topic:** Release Update 19.9 Features

### Release Update 19.10 Features

- Ability to Use Multiple Kerberos Principals with a Single Database Client
- DBMS_CLOUD Package
- New Database Initialization Parameters for Database Resident Connection Pooling (DRCP)
- Oracle Blockchain Table
- Oracle Instant Client Support for Linux for ARM
- Support Per-PDB Capture for Oracle Autonomous Database
- Updated Support for Micro Edition Suite (MES) for FIPS 140.2

**Parent topic:** New Features in 19c Release Updates

#### Ability to Use Multiple Kerberos Principals with a Single Database Client

Starting with this release, when you configure Kerberos authentication for an Oracle Database client, you can specify multiple Kerberos principals with a single Oracle Database client.

To enable this functionality, you will need to create a separate credential cache for each user in the client and then use the connect string to specify the user.

In previous releases, you were restricted to one Kerberos principal for each Oracle Database client.

**Related Topics**

- [Oracle® Database Security Guide](../dbseg/configuring-kerberos-authentication.md)

**Parent topic:** Release Update 19.10 Features

#### DBMS_CLOUD Package

Oracle provides two core mechanisms to work with data in object stores, as part of the new `DBMS_CLOUD` package or manually defining external tables.

Using `DBMS_CLOUD` provides benefits and additional functionality that goes beyond DDL and is fully compatible with Oracle Autonomous Database. Oracle strongly recommends leveraging the new `DBMS_CLOUD` package over manual external table creation.

**Related Topics**

- [Oracle® Database PL/SQL Packages and Types Reference ](../arpls/DBMS_CLOUD.md)

**Parent topic:** Release Update 19.10 Features

#### New Database Initialization Parameters for Database Resident Connection Pooling (DRCP)

New database initialization parameters, `MIN_AUTH_SERVERS` and `MAX_AUTH_SERVERS`, have been added to configure Database Resident Connection Pooling (DRCP).

`MIN_AUTH_SERVERS` and `MAX_AUTH_SERVERS` allow the number of processes used to handle session authentication for DRCP to be configured for optimal usage.

**Related Topics**

- [Oracle® Database Administrator's Guide](../admin/managing-processes.md)

**Parent topic:** Release Update 19.10 Features

#### Oracle Blockchain Table

Blockchain tables are append-only tables in which only insert operations are allowed. Deleting rows is either prohibited or restricted based on time. Rows in a blockchain table are made tamper-resistant by special sequencing and chaining algorithms. Users can verify that rows have not been tampered. A hash value that is part of the row metadata is used to chain and validate rows.

Blockchain tables can be used to implement blockchain applications where the participants trust the Oracle Database provider, but want means to verify that their data hasn’t been tampered with. The participants are different database users who trust the Oracle Database provider to maintain a verifiable, tamper-resistant blockchain of transactions. All participants must have privileges to insert data into the blockchain table. The contents of the blockchain table are defined and managed by the application, with a few added metadata fields maintained by Oracle Database. By leveraging a trusted provider with verifiable crypto-secure data management practices, such applications can avoid the distributed consensus requirements. This provides most of the protection of the distributed peer-to-peer blockchains, but with much higher throughput and lower transaction latency compared to peer-to-peer blockchains using distributed consensus.

**Related Topics**

- [Oracle® Database Administrator's Guide](../admin/managing-tables.md)

**Parent topic:** Release Update 19.10 Features

#### Oracle Instant Client Support for Linux for ARM

Starting with Oracle Database 19c Release Update (19.10), Oracle Instant Client is available on Linux for ARM (aarch64).

You can install Oracle Instant Client by downloading either the zip files or RPMs from the Oracle Instant Client download page on Oracle Technology Network (OTN).

**Related Topics**

- [Oracle® Database Client Installation Guide for Linux](../lacli/installing-instant-client.md)

**Parent topic:** Release Update 19.10 Features

#### Support Per-PDB Capture for Oracle Autonomous Database

To securely capture and replicate individual PDB changes to Oracle Autonomous Database, you can now use Oracle GoldenGate to provide per-PDB capture.

You can now provide local user credentials to connect to an individual PDB in a multitenant architecture Oracle Database, and replicate the data from just that PDB to an Oracle Autonomous Database. You no longer need to create a common user with access to all PDBs on the multitenant container database (CDB) to replicate a PDB to an Oracle Autonomous Database. Instead, you can now provision a local user with a predefined set of privileges to the source PDB that you want to capture. All LogMiner and Capture processing takes place only in this PDB, and only data from this specific PDB is captured and written to the Oracle GoldenGate trail. As part of this feature, the behavior for `V$LOGMNR_CONTENTS` changes, depending on whether you connect to a PDB, or connect to the `CDB$ROOT`.

**Related Topics**

- [Oracle® Database Utilities](../sutil/oracle-logminer-utility.md)

**Parent topic:** Release Update 19.10 Features

#### Updated Support for Micro Edition Suite (MES) for FIPS 140.2

Starting with this release, Oracle Database supports Micro Edition Suite (MES) version 4.5 for FIPS 140.2.

The Micro Edition Suite (MES) version 4.5 updates include four new CVEs in the RSA BSAFE MES library, support for the rules that FIPS 140.2 requires, and access to the updated NZ/ZT library from the Crypto Foundation.

This enhancement enables the Oracle Database FIPS 140.2 configuration to benefit from new features and security improvements available from the latest RSA BSAFE MES library.

**Related Topics**

- [Oracle® Database Security Guide](../dbseg/oracle-database-fips-140-settings.md)

**Parent topic:** Release Update 19.10 Features

### Release Update 19.11 Features

- Application Continuity Protection Check
- Immutable Tables
- New Database Initialization Parameter for Database Resident Connection Pooling (DRCP)
- Oracle Fleet Patching and Provisioning Zip Copy Image Transfer

**Parent topic:** New Features in 19c Release Updates

#### Application Continuity Protection Check

Application Continuity Protection Check (ACCHK) provides guidance on the level of protection for each application that uses Application Continuity and assists you to increase protection, if required.

ACCHK identifies which application configuration is protected to help you make an informed decision about which configuration to use for maximum protection or how to increase protection level for an application configuration. ACCHK also provides diagnostics for an unsuccessful failover.

**Related Topics**

- [Oracle® Real Application Clusters Administration and Deployment Guide](../racad/ensuring-application-continuity.md)

**Parent topic:** Release Update 19.11 Features

#### Immutable Tables

Immutable tables are insert-only tables in which existing data cannot be modified. Deleting rows is either prohibited or restricted based on the insertion time of the rows.

Immutable tables protect data against unauthorized modification by insiders. This includes database administrators or compromised users who have access to insider credentials. Immutable tables also prevent accidental data modification that may be caused by human error.

**Related Topics**

- [Oracle® Database Administrator's Guide](../admin/managing-tables.md)

**Parent topic:** Release Update 19.11 Features

#### New Database Initialization Parameter for Database Resident Connection Pooling (DRCP)

A new database initialization parameter, `DRCP_DEDICATED_OPT`, has been added to configure Database Resident Connection Pooling (DRCP).

With DRCP, when the number of application connections to the broker is less than the maximum pool size, a "dedicated optimization" makes DRCP behave like dedicated servers. With this optimization, DRCP tends towards a one-to-one correspondence between application connections and DRCP server processes even if those processes are not currently doing database work. Setting `DRCP_DEDICATED_OPT` to `NO` turns off the optimization and reduces the tendency of the pool to grow towards its maximum size until necessary. This helps keep the number of DRCP server processes small when statement execution concurrency is low, therefore reducing memory usage on the database host.

**Related Topics**

- [Oracle® Database Administrator's Guide](../admin/managing-processes.md)

**Parent topic:** Release Update 19.11 Features

#### Oracle Fleet Patching and Provisioning Zip Copy Image Transfer

Starting with Oracle Grid Infrastructure 19c Release Update (19.11), Oracle FPP enables you to install the gold images without transferring them to the target host. You can make the gold images available as zip files, either on a shared file system (NFS) or target hosts.

The Zip copy image transfer feature avoids errors and timeout for deployments with low bandwidth or high latency networks between the Oracle FPP Server and targets. This enables deployments in different data centers.

Related Topics

- [Oracle Fleet Patching and Provisioning Administrator's Guide](../fppad/provisioning-oracle-database-using-zip-copy.md)

**Parent topic:** Release Update 19.11 Features

### Release Update 19.12 Features

- Gradual Database Password Rollover for Applications
- Oracle Memory Speed Support for PMEM Devices

**Parent topic:** New Features in 19c Release Updates

#### Gradual Database Password Rollover for Applications

Starting with this release update, an application can change its database passwords without an administrator having to schedule downtime.

To accomplish this, a database administrator can associate a profile having a non-zero limit for the `PASSWORD_ROLLOVER_TIME` password profile parameter, new with this release, with an application schema. This allows the database password of the application user to be altered while allowing the older password to remain valid for the time specified by the `PASSWORD_ROLLOVER_TIME` limit. During the rollover period of time, the application instance can use either the old password or the new password to connect to the database server. When the rollover time expires, only the new password is allowed.

Before this enhancement, an administrator normally took the application down when the application database password was being rotated. This is because the password update requires changes on both the database and the application side. With the gradual database password rollover enhancement, the application can continue to use the older password until the new password is configured in the application.

In addition to the new clause `PASSWORD_ROLLOVER_TIME` in the `CREATE PROFILE` and `ALTER PROFILE` statements, the `ALTER USER` statement has a new clause, `EXPIRE PASSWORD ROLLOVER PERIOD`. The `ACCOUNT_STATUS` column of the `DBA_USERS` and `USER_USERS` data dictionary views have several new statuses indicating values to indicate rollover status.

**Related Topics**

- [Oracle® Database Security Guide](../dbseg/configuring-authentication.md)

**Parent topic:** Release Update 19.12 Features

#### Oracle Memory Speed Support for PMEM Devices

Oracle recommends that you use Oracle Database with the Oracle Memory Speed (OMS) file system to fully utilize the potential of persistent memory (PMEM) devices safely in data centers.

With PMEM as the backing device, OMS utilizes a memory-mapped file hosted on an XFS-based, DAX-enabled file system to perform I/O operations. You must export the PMEM device as a file using a DAX-enabled file system, such as XFS.

**Related Topics**

- [Oracle® Database Installation Guide for Linux](../ladbi/deploying_oms.md)

**Parent topic:** Release Update 19.12 Features

### Release Update 19.13 Features

There are no new features for the 19.13 release update.

**Parent topic:** New Features in 19c Release Updates

### Release Update 19.14 Features

There are no new features for the 19.14 release update.

**Parent topic:** New Features in 19c Release Updates

### Release Update 19.15 Features

There are no new features for the 19.15 release update.

**Parent topic:** New Features in 19c Release Updates

### Release Update 19.16 Features

- Enhancements for Identity and Access Management Integration with Oracle Database Environments
- Oracle Data Guard Redo Decryption for Hybrid Disaster Recovery Configurations

**Parent topic:** New Features in 19c Release Updates

#### Enhancements for Identity and Access Management Integration with Oracle Database Environments

Available for Oracle Database release 19.16 are enhancements to the integration of Identity and Access Management (IAM) users with Oracle Database Environments.

- Additional Oracle Database environments: The full list of supported Oracle Database environments is as follows:
  - Oracle Autonomous Database on Dedicated Exadata Infrastructure
  - Oracle Autonomous Database on Shared Exadata Infrastructure
  - Oracle Base Database Service
- Ability to use the IAM user name and password to retrieve an IAM token: Retrieving a token using an IAM user name and password or secure external password store (SEPS) is more secure than using the password verifier method of database access.

Related Topics

- [Oracle® Database Security Guide](../dbseg/authenticating-and-authorizing-iam-users-oracle-dbaas-databases.md)

**Parent topic:** Release Update 19.16 Features

#### Oracle Data Guard Redo Decryption for Hybrid Disaster Recovery Configurations

Available for Oracle Database release 19.16, Oracle Data Guard enables you to decrypt redo operations in hybrid cloud disaster recovery configurations where the Cloud database is encrypted with TDE and the on-premises database is not.

Hybrid disaster recovery is often considered a quick-stepping stone to cloud adoption. By enabling the ability to quickly configure disaster recovery even in cases where on-premises databases might not already be encrypted with TDE, the steps required to configure hybrid disaster recovery environments are reduced while still ensuring that redo data is still encrypted during the transportation process.

To enable this feature, Oracle Database introduces the `TABLESPACE_ENCRYPTION` initialization parameter, which enables you to control the automatic encryption of tablespaces in both the primary and standby databases, for on-premises and Oracle Cloud Infrastructure (OCI) environments. For example, an on-premises database can be unencrypted and an OCI database can be encrypted.

Related Topics

- [Oracle® Database Advanced Security Guide](../asoag/using-transparent-data-encryption-with-other-oracle-features.md)

**Parent topic:** Release Update 19.16 Features

### Release Update 19.17 Features

There are no new features for the 19.17 release update.

**Parent topic:** New Features in 19c Release Updates

### Release Update 19.18 Features

- All Time Zone Files (DST) Included in Release Updates (RUs)

**Parent topic:** New Features in 19c Release Updates

#### All Time Zone Files (DST) Included in Release Updates (RUs)

Starting with Oracle Database 19c RU 19.18.0, all available DST patches are installed with the RU, and deployed into the `Oracle_home/oracore/zoneinfo` directory. Installing DST patches does not affect database operation. However, installing the patches with the RU makes it easier for you to adjust the timezone version of your database, if you have a requirement to do so. For example, if you are using Transportable Tablespaces, or Full Transportable Export/Import, then you must ensure that your source and target databases are using identical character sets and identical time zone settings. With this change, you can more easily choose to change your destination database to use a different time zone file version than the default.

By default, AutoUpgrade changes the database time zone to the latest available level. If you don’t want the time zone to be upgraded, then you must explicitly set the local parameter `timezone_upg` in your AutoUpgrade configuration file to `no`. For example:

    upg1.timezone_upg=no

If you choose to use an older database time zone file, then set the database environment variable `ORA_TZFILE` to the older time zone file. The time zone files are located in `Oracle_home/oracore/zoneinfo`. By using the environment variable `ORA_TZFILE`, you can override the default of using the highest-numbered time zone file.

Related Topics

- [Choosing a Time Zone File](https://docs.oracle.com/en/database/oracle/oracle-database/21/nlspg/datetime-data-types-and-time-zone-support.html#GUID-805AB986-DE12-4FEA-AF56-5AABCD2132DF)
- [RUs contain now all available DST patches](https://mikedietrichde.com/2023/01/19/rus-contain-now-all-available-dst-patches/#:~:text=When%20you%20create%20a%20new%20database%2C%20regardless%20whether,be%20created%20with%20the%20newest%20available%20DST%20file)
- [Create a database with NON-DEFAULT Time Zone](https://mikedietrichde.com/2016/12/08/create-a-database-with-non-default-time-zone/)

**Parent topic:** Release Update 19.18 Features

### Release Update 19.19 Features

There are no new features for the 19.19 release update.

**Parent topic:** New Features in 19c Release Updates

### Release Update 19.20 Features

- In-Memory Eligibility Test

**Parent topic:** New Features in 19c Release Updates

#### In-Memory Eligibility Test

Many workloads benefit from Database In-Memory, however some may not. The In-Memory Eligibility Tool determines if a given workload would benefit or not benefit from Database In-Memory and assesses its eligibility for use of this feature. Eligibility is gauged by the percentage of analytical activity in the workload. If you are planning to implement Database In-Memory, you can use this tool to quickly identify and filter out databases that are ineligible - those where analytic activity is low and where you would see no substantive gain from the use of Database In-Memory. You can then focus your Database In-Memory deployment on databases whose workload includes more intense analytic activity and could therefore benefit substantially. The higher the percentage of analytical activity in the workload, the more benefit you gain from Database In-Memory.

Related Topics

- [Database In-Memory Guide](../inmem/intro-to-in-memory-column-store.md)

**Parent topic:** Release Update 19.20 Features

### Release Update 19.21 Features

- AutoUpgrade Automates Data Guard Operations During Database Upgrade
- AutoUpgrade Automates Steps Required for Oracle RAC Database Upgrade
- AutoUpgrade Automates Upgrade and Conversion of Non-CDB to PDB
- AutoUpgrade Automates Upgrade of a PDB via Unplug-Plug-Upgrade
- AutoUpgrade Release Update (RU) Upgrades
- AutoUpgrade Sets Parallelism Based on System Resources
- AutoUpgrade Supports Upgrades with Keystore Access to Databases Using TDE
- AutoUpgrade Unplug-Plugin Upgrades to Different Systems
- FPP Integration with AutoUpgrade
- Oracle Database Automates Database Upgrades with AutoUpgrade
- REST APIs for AutoUpgrade

**Parent topic:** New Features in 19c Release Updates

#### AutoUpgrade Automates Data Guard Operations During Database Upgrade

AutoUpgrade automates the steps necessary to upgrade a database in an Oracle Data Guard configuration. Note that in Oracle Database 19c, Data Guard operations are not fully automated. Oracle only supports upgrading a primary database and shutting down of redo apply to a standby database.

Steps that AutoUpgrade automates includes disabling and re-enabling the Data Guard Broker (if present), and deferring log file transport while the upgrade takes place. Automation of these Oracle Data Guard operations in the context of a database upgrade eliminates the need for manual or scripted steps that you otherwise would have to perform yourself. This in turn makes it easier to automate upgrades of databases in Oracle Data Guard configurations. This feature particularly helps to automate upgrades in high-end environments, where there can be many hundreds of such databases that you upgrade as part of your upgrade project.

Related Topics

- [Oracle® Database Database Upgrade Guide](https://docs.oracle.com/en/database/oracle/oracle-database/21/upgrd/autoupgrade-oracle-database-config-options.html#GUID-7985739B-B33B-4BA6-A9FE-FEFC7721FFE8)

**Parent topic:** Release Update 19.21 Features

#### AutoUpgrade Automates Steps Required for Oracle RAC Database Upgrade

AutoUpgrade automates all the steps needed to upgrade an Oracle Real Application Clusters (Oracle RAC) database.

AutoUpgrade automates steps that previously had to be performed manually or scripted. Steps that AutoUpgrade automates include the `SRVCTL` commands to stop and restart instances on multiple nodes, handling of `CLUSTER_DATABASE`, updating initialization parameter files, and restarting services, where appropriate.

This feature reduces the possibility of manual errors and decreases the work needed for DBAs to perform routine maintenance and upgrade activities.

Related Topics

[Oracle® Database Database Upgrade Guide](https://docs.oracle.com/en/database/oracle/oracle-database/21/upgrd/autoupgrade-oracle-database-config-options.html#GUID-746B7BAA-C9FF-4CDE-AF9E-154589714A56)

**Parent topic:** Release Update 19.21 Features

#### AutoUpgrade Automates Upgrade and Conversion of Non-CDB to PDB

To simplify upgrades to Oracle Database 21c, AutoUpgrade automates steps to convert a database from a non-CDB to a PDB as part of a database upgrade.

Oracle Database 21c requires multitenant architecture. With this release, you can use AutoUpgrade for non-CDB to PDB upgrades from Oracle Database 12c Release 2 (12.2) and later releases. Using the automation features of AutoUpgrade reduces both the effort required of DBAs for upgrades, and the risk associated with typographical errors in a manual process.

Related Topics

-  [Oracle® Database Database Upgrade Guide](https://docs.oracle.com/en/database/oracle/oracle-database/21/upgrd/understanding-non-cdb-to-pdb-upgrades-autoupgrade.html#GUID-D739E4A4-F1B9-45BE-B0E2-F213FE70F665)

**Parent topic:** Release Update 19.21 Features

#### AutoUpgrade Automates Upgrade of a PDB via Unplug-Plug-Upgrade

AutoUpgrade automates unplugging a PDB from a CDB, plugging it into a higher version CDB, and upgrading the PDB to that new target version.

As part of the process to simplify upgrade, you can upgrade pluggable databases (PDBs) using an unplug/plug, where the upgrade occurs when you plug the PDB into the target release container database (CDB). This feature adds another scenario in which AutoUpgrade can automate the entire database upgrade process.

Related Topics

- [Oracle® Database Database Upgrade Guide](https://docs.oracle.com/en/database/oracle/oracle-database/21/upgrd/understanding-pdb-unplug-plug-upgrades-autoupgrade.html#GUID-F03BAE5B-DFB7-40AF-8109-670DDD42589A)

**Parent topic:** Release Update 19.21 Features

#### AutoUpgrade Release Update (RU) Upgrades

AutoUpgrade supports the option of using AutoUpgrade to perform out-of-place Oracle home Release Update patching.

For an out-of-place patch of Oracle Database using AutoUpgrade, AutoUpgrade moves the source database that you want to patch to a new Oracle Database Oracle home, and then patches the database binaries in that target Oracle home with the Release Update that you select. With this option, you can use AutoUpgrade at any time that you want to move the database to a new Oracle home, either as part of a planned upgrade or as part of a patch plan. In a patch operation, AutoUpgrade performs the patch using the following workflow:

1.  AutoUpgrade recognizes that the source database and the target Oracle Database are the same base release.
2.  AutoUpgrade skips the upgrade steps.
3.  AutoUpgrade patches the target database using the Release Update.

Related Topics

- [AutoUpgrade Patching](https://docs.oracle.com/pls/topic/lookup?ctx=db23&id=UPGRD-GUID-20D02F58-2A55-4FC6-B726-113AB44FDCB7)

**Parent topic:** Release Update 19.21 Features

#### AutoUpgrade Sets Parallelism Based on System Resources

AutoUpgrade automatically evaluates system resources and makes an intelligent decision as to how many upgrade jobs can run simultaneously.

AutoUpgrade uses the `CPU_COUNT` value and system process parameters to determine available system resources, and calibrates both the number of upgrades that can run at a time and the number of parallel threads for each upgrade. Upgrades that exceed a safe threshold are put in a queue so that they can be run as system resources become available.

Related Topics

- [tune_setting](https://docs.oracle.com/pls/topic/lookup?ctx=db23&id=UPGRD-GUID-649B150D-3364-44A0-A432-58CCD693A41A)

**Parent topic:** Release Update 19.21 Features

#### AutoUpgrade Supports Upgrades with Keystore Access to Databases Using TDE

AutoUpgrade enhances support for databases that use transparent data encryption (TDE) by enabling keystore generation.

AutoUpgrade now enables you to provide passwords to an external key manager generated and maintained by AutoUpgrade. With this configuration, AutoUpgrade supports unmanned or automated operations of TDE-enabled databases. AutoUpgrade can open the source database keystore without prompting for the keystore password, and enroll the target database into the TDE external keystore for key management, so that the target database can start automatically.

Related Topics

- [Upgrades and Transparent Data Encryption](https://docs.oracle.com/pls/topic/lookup?ctx=db23&id=UPGRD-GUID-CA0377B3-5566-4CCF-8455-566F42440776)

**Parent topic:** Release Update 19.21 Features

#### AutoUpgrade Unplug-Plugin Upgrades to Different Systems

You can now use the Oracle Database AutoUpgrade Unplug/Plug method to unplug a PDB from one system and plug into a different system and upgrade.

In earlier releases, AutoUpgrade supported unplug/plug/upgrades on the same server, but it was not possible to unplug a PDB from one server, plug it into a different system, and then upgrade the PDB. With this feature, you can now migrate and upgrade the PDB in a single operation, including migrations to the cloud.

Related Topics

- [Unplug-Plug Relocate Upgrades With AutoUpgrade](https://docs.oracle.com/pls/topic/lookup?ctx=db23&id=UPGRD-GUID-BBDA588D-2CCD-4551-BDE2-CA7821A1A54D)

**Parent topic:** Release Update 19.21 Features

#### FPP Integration with AutoUpgrade

Fleet Patching and Provisioning (FPP) integration with AutoUpgrade provides a new tool for automating and simplifying Oracle Database Upgrade.

This feature makes Oracle Database AutoUpgrade more flexible, provides better control over the upgrade flow mechanism, and provides better usability by showing progress bar and additional elements. You can upgrade multiple databases in parallel.

Related Topics

-  [Oracle® Fleet Patching and Provisioning Administrator's Guide](https://docs.oracle.com/en/database/oracle/oracle-database/21/fppad/fleet-patching-provisioning.html#GUID-CCEC5960-EDA4-4A3F-9643-0CA308EA49AA)

**Parent topic:** Release Update 19.21 Features

#### Oracle Database Automates Database Upgrades with AutoUpgrade

Oracle Database AutoUpgrade enables you to upgrade one or many databases without human intervention, all with one command, and with a single configuration file.

AutoUpgrade enables you to upgrade one or many Oracle Database instances at the command-line, using a single command and a single configuration file. AutoUpgrade runs the preupgrade tasks, performs automated fix-ups where needed, runs the database upgrade, and finishes by completing post-upgrade tasks. It includes automatic retry and fallback, the option to schedule upgrades for future points in time, and the ability to set, change, or remove initialization parameters as desired. Using AutoUpgrade can save you time and money by enabling you to upgrade hundreds of databases with one command, and avoid the need for high-maintenance upgrade solutions.

Related Topics

-  [Oracle® Database Database Upgrade Guide](https://docs.oracle.com/en/database/oracle/oracle-database/21/upgrd/using-autoupgrade-oracle-database-upgrades.html)
- [Hitchhiker's Guide for Upgrading to Oracle Database 19c Workshop](https://apexapps.oracle.com/pls/apex/dbpm/r/livelabs/view-workshop?wid=606)

**Parent topic:** Release Update 19.21 Features

#### REST APIs for AutoUpgrade

To facilitate safe and secure remote use of the AutoUpgrade for Oracle Database upgrades, AutoUpgrade now provides REST APIs (ORDS and OCI).

The Oracle REST Data Services (ORDS) database API is a database management and monitoring REST API embedded into Oracle REST Data Services. The Oracle Cloud Infrastructure (OCI) REST API is enabled by configuring the REST Adapter connection to use the OCI Signature Version 1 security policy. You can now use these features to run AutoUpgrade upgrades remotely over SSH.

Related Topics

- [C AutoUpgrade REST APIs](https://docs.oracle.com/pls/topic/lookup?ctx=db23&id=UPGRD-GUID-757E7473-3FDB-4AE8-978A-1E762630BCA2)

**Parent topic:** Release Update 19.21 Features

### Release Update 19.22.0.0 Features

- Enabling Scrambled Dequeues and Dequeue Flow Control
- Enhanced Online DDL Capabilities in the Presence of Supplemental Logging

**Parent topic:** New Features in 19c Release Updates

#### Enabling Scrambled Dequeues and Dequeue Flow Control

You can enable or disable the scrambling and flow control feature using the queue level parameter:

- To spread the concurrent dequeuers across different blocks or buffers, enable scrambled dequeues using the following queue parameter:

      DBMS_AQADM.SET_QUEUE_PARAMETER('<schema_name>.<queue_name>', 'CQ_SCRAMBLED_DEQ', 1);

  To disable scrambled dequeues, use the following queue parameter:

      DBMS_AQADM.UNSET_QUEUE_PARAMETER('<schema_name>.<queue_name>', 'CQ_SCRAMBLED_DEQ');

- To internally restrict the number of concurrent sessions that execute the dequeue select for update on a queue, enable dequeue flow control using the following queue parameter:

      DBMS_AQADM.SET_QUEUE_PARAMETER('<schema_name>.<queue_name>', 'CQ_DEQ_FLOWCONTROL', N);

  Where N is the number of internal dequeue sessions allowed to do the core dequeue work concurrently, which causes waits and contentions. Note that N must be less than the number of actual external dequeue sessions.

  To disable dequeue flow control, use the following queue parameter:

      DBMS_AQADM.UNSET_QUEUE_PARAMETER('MY_QUEUE', 'CQ_DEQ_FLOWCONTROL');

Using these new parameters, you can now spread concurrent dequeuers across different blocks or buffers to reduce buffer busy waits contention and to avoid row lock contention and buffer busy waits contention.

**Parent topic:** Release Update 19.22.0.0 Features

#### Enhanced Online DDL Capabilities in the Presence of Supplemental Logging

Numerous DDL operations were blocking operations when supplemental logging was enabled. You can use the `OGG_ONLINE_DDL` initialization parameter to lift this restriction for several previously blocking DDL operations when minimal supplemental logging is enabled. Those commands are namely:

- `ALTER TABLE ADD COLUMN`
- `ALTER TABLE SET COLUMN UNUSED`
- `ALTER TABLE ADD CONSTRAINT ENABLE NOVALIDATE`
- `ALTER TABLE DROP CONSTRAINT`

Non-blocking DDL operations are crucial for mission-critical environments where it is hard to impossible to guarantee an idle time window for blocking DDL operations to succeed. Supplemental logging is a key requirement for GoldenGate replication support, which creates a dilemma for customers to choose between non-blocking DDL or using GoldenGate. Enabling more non-blocking DDL operations in the presence of supplemental logging make such a decision void. Customers benefit from non-blocking DDL operations and GoldenGate.

Related Topics

- [Database Reference](../refrn/OGG_ONLINE_DDL.md)

**Parent topic:** Release Update 19.22.0.0 Features

### Release Update 19.23.0.0 Features

- Session Exit on Invalidation

**Parent topic:** New Features in 19c Release Updates

#### Session Exit on Invalidation

Set `SESSION_EXIT_ON_PACKAGE_STATE_ERROR` to true to force a hard session exit when a session's state has been invalidated.

Exiting sessions after state invalidation avoids errors that can occur when applications mishandle invalid state.

Related Topics

- [Package State](../lnpls/package-state.md)

**Parent topic:** Release Update 19.23.0.0 Features

### Release Update 19.24 Features

There are no new features for the 19.24 release update.

**Parent topic:** New Features in 19c Release Updates

### Release Update 19.25 Features

There are no new features for the 19.25 release update.

**Parent topic:** New Features in 19c Release Updates

### Release Update 19.26 Features

There are no new features for the 19.26 release update.

**Parent topic:** New Features in 19c Release Updates

### Release Update 19.27 Features

There are no new features for the 19.27 release update.

**Parent topic:** New Features in 19c Release Updates

### Release Update 19.28 Features

- DBMS_DEVELOPER PL/SQL Package
- Enhancements to RADIUS Configuration
- IF \[NOT\] EXISTS Syntax Support
- Multi-Factor Authentication for Database Authentication
- Oracle Database Cloud Backup Module for Azure Blob Storage
- Oracle Update Advisor Support with Oracle FPP
- Schema Annotations
- SQL Diagnostic Report

**Parent topic:** New Features in 19c Release Updates

#### DBMS_DEVELOPER PL/SQL Package

The `DBMS_DEVELOPER` PL/SQL package provides an efficient way for developers to retrieve metadata for database objects, such as tables, views, and indexes. In previous releases, object metadata had to be retrieved using the `DBMS_METADATA` package, which returned metadata in XML format or by performing queries on various data dictionary tables and views.

The `DBMS_DEVELOPER` package returns metadata as a CLOB containing JSON formatted text, which can be easily integrated with applications and services, such as developer tools. You can adjust the level of detail to control the amount of metadata returned, tailoring it to your application's needs. Additionally, metadata retrieval time is significantly improved, enhancing integration with applications and services.

Related Topics

- [DBMS_DEVELOPER](../arpls/dbms_developer1.md)

**Parent topic:** Release Update 19.28 Features

#### Enhancements to RADIUS Configuration

RADIUS is frequently used to provide multi-factor authentication (MFA) for Oracle Database. Oracle Database 19c now supports the RFC 6613 and 6614 guidelines for RADIUS and implements TCP over Transport Layer Security (TLS) by default. This enhancement introduces new RADIUS-related `sqlnet.ora` parameters to support the new standards. The enhancement also deprecates several RADIUS-related `sqlnet.ora` parameters that are no longer needed to support the new standards.

This update to RADIUS standards support improves security for customers using RADIUS-based authentication.

Related Topics

- [About Configuring RADIUS Authentication](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23&id=DBSEG-GUID-7FE4DC4F-2E1B-4CEC-928C-39D8A953ED73)

**Parent topic:** Release Update 19.28 Features

#### IF \[NOT\] EXISTS Syntax Support

DDL object creation, modification, and deletion now support the c and `IF NOT EXISTS` syntax modifiers. This enables you to control whether an error should be raised if a given object exists or does not exist.

The `IF [NOT] EXISTS` syntax can simplify error handling in scripts and by applications.

Related Topics

- [Using IF EXISTS and IF NOT EXISTS](../adfns/sql-processing-for-application-developers.md)

**Parent topic:** Release Update 19.28 Features

#### Multi-Factor Authentication for Database Authentication

You can enhance Oracle Database security by enabling multi-factor authentication for users. You can use push notifications through the Cisco Duo or Oracle Mobile Authenticator app or combine a username and password with PKI (Public Key Infrastructure) certificate-based authentication.

Multi-factor authentication is a required security requirement for many databases, especially if the database holds sensitive data.

Related Topics

- [Configuring Multi-Factor Authentication](../dbseg/configuring-authentication.md)

**Parent topic:** Release Update 19.28 Features

#### Oracle Database Cloud Backup Module for Azure Blob Storage

The Oracle Database Cloud Backup Module for Azure Blob Storage enables Oracle Database to send backups to and recover from Microsoft Azure Blob Storage. This backup module is compatible with Oracle Databases deployed on-premises or on Azure cloud. Support for writing backups to Azure Blob Storage for Oracle-managed database services is not available. Database administrators can use RMAN commands, RMAN scripts, and Oracle Enterprise Manager to perform backup and recovery operations with Azure Blob Storage.

You can run Oracle Databases in many different locations, and the backup module for Azure Blob Storage provides on-premises and Azure virtual machine users with more flexibility for backup storage locations.

Related Topics

- [Oracle Database Cloud Backup Module for Azure](../bradv/azure-sbt-module.md)

**Parent topic:** Release Update 19.28 Features

#### Oracle Update Advisor Support with Oracle FPP

You can leverage Oracle Update Advisor with Oracle Fleet Patching and Provisioning (Oracle FPP). Oracle Update Advisor is a software recommendation framework that analyzes the health of Oracle Database and Oracle Grid Infrastructure, provides patch recommendations, and creates fully functional gold images based on your patch maintenance policy. These gold images are downloaded automatically into the Oracle FPP Gold Image repository.

Using Oracle Fleet Patching and Provisioning in conjunction with Oracle Update Advisor greatly simplifies and streamlines the update experience. You can use the Oracle Update Advisor for both Oracle FPP Local Mode and Oracle FPP Central Server Mode.

Related Topics

- [About Oracle Update Advisor](../fppad/about-oracle-update-advisor.md)

**Parent topic:** Release Update 19.28 Features

#### Schema Annotations

Schema annotations enable you to store and retrieve metadata about database objects. These are name-value pairs or simply a name. These are free-form text fields applications can use to customize business logic or user interfaces.

Annotations help you use database objects in the same way across all applications. This simplifies development and improves data quality.

Related Topics

- [Schema Annotations](../cncpt/application-data-usage.md)

**Parent topic:** Release Update 19.28 Features

#### SQL Diagnostic Report

The SQL diagnostic package (`DBMS_SQLDIAG`) includes a new function called `REPORT_SQL` which generates a zip archive containing a deep-level HTML diagnostic report for a specified SQL statement. The report includes important diagnostic information such as a plan history, non-default database parameters, optimizer statistics history, statistics status, index details, and more. The archive will also include, where available, captured SQL Monitor reports for the SQL.

This feature makes it easier to diagnose SQL performance issues.

Related Topics

- [REPORT_SQL Function](../arpls/DBMS_SQLDIAG.md)

**Parent topic:** Release Update 19.28 Features
