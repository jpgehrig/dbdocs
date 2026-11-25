## 10 Oracle Database Changes, Desupports, and Deprecations

To assist you with developing a long-term plan for your database patching and upgrades, Oracle provides this list of changes, deprecations and desupports across multiple releases.

This document is updated regularly to reflect information Oracle can provide about releases as they happen, so that you can plan for changes in releases that you plan to move to at a later date. For example, if you are upgrading to Oracle Database 19c, it can be helpful for your long-term planning to be aware of features that have been desupported in a later release, or for which there is a deprecation notice in a later release. In addition, it can be helpful to be aware that security protocols or default parameter settings have changed in a later release, so that you can begin your preparations for that change in your current release well before you want to upgrade to a release where those deprecations or desupports are in effect.

- About Deprecated and Desupported Status
  In addition to new features, Oracle Database releases can modify, deprecate or desupport features, and introduce upgrade behavior changes for your database
- Desupported and Deprecated Release Notice Dates
  You can identify the date that a desupport or deprecation notice has been published by using the datestamp on the topic.
- Using the ORADiff Tool to Find Release Changes
  To help you to find changes in parameter defaults, users, roles, and other changes between database releases, Oracle recommends that you use Oracle Database Release Diff Utility (ORADiff).
- Oracle Database 23ai Behavior Changes, Desupports, and Deprecations
  Review for descriptions of Oracle Database 23ai release changes.
- Oracle Database 21c Behavior Changes, Desupports, and Deprecations
  Review for descriptions of Oracle Database 21c release changes.
- Oracle Database 19c Behavior Changes, Desupports, and Deprecations
  Review for descriptions of Oracle Database 19c release changes.
- Oracle Database 18c Behavior Changes, Desupports, and Deprecations
  Review for descriptions of Oracle Database 18c release changes.
- Oracle Database 12c Release 2 (12.2) Behavior Changes, Desupports, and Deprecations
  Review for descriptions of Oracle Database 12c Release 2 (12.2) changes.
- Oracle Database 12c Release 1 (12.1) Behavior Changes, Desupports, and Deprecations
  Review for descriptions of Oracle Database 12c Release 1 (12.1) changes.

### About Deprecated and Desupported Status

In addition to new features, Oracle Database releases can modify, deprecate or desupport features, and introduce upgrade behavior changes for your database

Be aware of the implications of deprecated and desupported:

- **Deprecated** features are features that are no longer being enhanced, but are still supported for the full life of the Oracle Database release for which the deprecation notice is published.

- **Desupported** features are features that are no longer supported by fixing bugs related to that feature in the Oracle Database release for which the desupport notice is published. Often, Oracle can choose to remove the code required to use the feature. A deprecated feature can be desupported in the next Oracle Database release.

**Parent topic:** Oracle Database Changes, Desupports, and Deprecations

### Desupported and Deprecated Release Notice Dates

You can identify the date that a desupport or deprecation notice has been published by using the datestamp on the topic.

September 2023

The text above this sentence is a datestamp. It indicates that this topic was added with the September 2023 update to upgrade guides. Starting with August 2023, Oracle is adding this timestamp to the desupport and deprecation topics.

**Parent topic:** Oracle Database Changes, Desupports, and Deprecations

### Using the ORADiff Tool to Find Release Changes

To help you to find changes in parameter defaults, users, roles, and other changes between database releases, Oracle recommends that you use Oracle Database Release Diff Utility (ORADiff).

August 2023

The Oracle Database Release Diff Utility (ORADiff) is an Oracle tool that allows you to compare two Oracle Database releases, or between release updates. It reports differences in parameters, privileges, users and roles, reserved words, patch fixes, database homes, objects, and more. It can also be used to obtain an inventory of these items for a particular release. ORAdiff data is refreshed when a new Release Update is released, which is every quarter. You can also generate a report that you can use to identify items that have been removed or changed from your source database release to the target database release. Check it out!

To use ORADiff, you must log in with your Oracle account Single Sign-On (SSO) user.

**Related Topics**

- [ORADiff](https://oradiff.oracle.com/)
- [ORAdiff is live – compare two Oracle Database and Patch releases](https://mikedietrichde.com/2023/08/08/oradiff-is-live-compare-two-oracle-database-and-patch-releases/)
- [ORAdiff - Find the differences between two Oracle Database releases](https://www.dbarj.com.br/en/2023/08/oradiff-find-the-differences-between-two-oracle-database-releases/)

**Parent topic:** Oracle Database Changes, Desupports, and Deprecations

### Oracle Database 23ai Behavior Changes, Desupports, and Deprecations

Review for descriptions of Oracle Database 23ai release changes.

- Behavior Changes for Oracle Database 23ai Upgrade Planning
  Review these selected behavior changes to help plan for upgrades to Oracle Database 23ai.
- Desupported Features in Oracle Database 23ai
  As part of your upgrade plan, review the desupported features in this Oracle Database release.
- Desupported Parameters in Oracle Database 23ai
  As part of your upgrade plan, review the initialization parameters that are not supported starting with this Oracle Database release.
- Deprecated Features in Oracle Database 23ai
  As part of your upgrade plan, review the features that are deprecated in this Oracle Database release, and review alternatives for your application strategies.
- Deprecated Views in Oracle Database 23ai
  As part of your upgrade plan, review the views that are deprecated starting with this Oracle Database release.
- Deprecated Parameters in Oracle Database 23ai
  As part of your upgrade plan, review the initialization parameters listed here that are deprecated starting with this Oracle Database release.

**Parent topic:** Oracle Database Changes, Desupports, and Deprecations

#### Behavior Changes for Oracle Database 23ai Upgrade Planning

Review these selected behavior changes to help plan for upgrades to Oracle Database 23ai.

Behavior changes can include default changes for parameters or features, product name changes, and other changes to the database configuration that may require your attention.

- Oracle Database Release Number Changes
  The data provided in `VERSION`, `VERSION_LEGACY` and `VERSION_FULL` release number values are updated in Oracle Database 23ai.
- Oracle Spatial and Obsolete Objects
  If you previously used Oracle Multimedia or Oracle Locator for media objects, then Oracle Spatial is installed during the upgrade to Oracle Database 23ai if `MDSYS`-owned Locator objects exist in the database.
- REST APIs for AutoUpgrade
  To facilitate safe and secure remote use of the AutoUpgrade utility for Oracle Database upgrades, AutoUpgrade now provides REST APIs (ORDS and OCI).
- XML JSON Search Index Enhancements
  Starting with Oracle Database 23ai, enhancements to JSON search can be a factor in your upgrade planning.
- SQL/JSON Function JSON_VALUE With a Boolean JSON Value
  Starting with Oracle Database 23ai, the data type `BOOLEAN` is added to Oracle SQL. This feature extends SQL/JSON operators to allow returning a `BOOLEAN` value or accepting one as input.
- Migrate from Non-AES Algorithms in FIPS Before Upgrade
  If you use Transparent Data Encryption (TDE), then you must migrate your source database to AES encryption before starting your upgrade to Oracle Database 23ai.
- Oracle OLAP Deprecation Extended
  Analytic workspaces, the OLAP DML programming language, financial reporting, and the OLAP Java API continue to be deprecated in Oracle Database 23ai.
- About Read-Only Oracle Homes
  With Oracle Database 23ai, an Oracle home is available in read/write mode by default. However, you can choose to configure an Oracle home in read-only mode after you have performed a software-only Oracle Database installation.
- SYSDATE and SYSTIMESTAMP Reflect PDB Time Zone
  Starting with Oracle Database 23ai, `SYSDATE` and `SYSTIMESTAMP` can be managed separately for each database, following the individual database time zone setting.
- Oracle Spatial GeoRaster JPEG Compression on 4-band Raster Blocks
  Starting with Oracle Database 23ai, JPEG compression on Oracle Spatial GeoRaster object can only be applied on 1-band and 3-band raster blocks.
- Document-Identifier Field Names for Duality Views Requirements
  Starting with Oracle Database 23ai, release update 23.4, when you are using duality views, the document-identifier field name must be `_id`.
- BIGFILE Is the Default for SYSAUX, SYSTEM, and USER Tablespaces
  Starting with Oracle Database 23ai, newly created databases use BIGFILE as the default for the `SYSTEM`, `SYSAUX`, and `USER` tablespaces.
- Terminal Release of Stored Outlines
  Oracle Database 23ai is the terminal release of stored outlines. Migrate all stored outlines to SQL plan baselines.

**Parent topic:** Oracle Database 23ai Behavior Changes, Desupports, and Deprecations

##### Oracle Database Release Number Changes

The data provided in `VERSION`, `VERSION_LEGACY` and `VERSION_FULL` release number values are updated in Oracle Database 23ai.

##### Base Version release

The `VERSION` release is designated in the form `major release version``.0.0.0.0`. The major release version is based on the last two digits of the year in which an Oracle Database version is released for the first time. For example, the Oracle Database version released for the first time in the year 2023 has the major release version of 23, and thus its version release is 23.0.0.0.0. This base version release number is not updated over the course of the release. You can identify the base release by logging in to SQL\*Plus and entering `SELECT BANNER FROM V$VERSION` to see the release displayed. This is the value associated with the `COMPATIBLE` initialization parameter.

##### Version Full release

The `version_full` releases are categorized by five numeric segments separated by periods, which designate the base database release, the release update, the refresh of the release update, the release month, and the release year. This value is visible in trace files. You can see the difference in the following example, comparing the same SQL command output between Oracle Database 23ai and 19c. In the Oracle Database 23ai output, the `VERSION_FULL` value provides the base release (23), the release update (4), the refresh of the release update (0), and the year and month (24.03), while the Oracle Database 19c output for `VERSION_FULL` indicates only the base release and the release update (19.8):

    SQL> select INSTANCE_NAME,VERSION,VERSION_LEGACY,VERSION_FULL from v$instance;

    INSTANCE_NAME    VERSION           VERSION_LEGACY    VERSION_FULL
    ---------------- ----------------- ----------------- -----------------
    orcl             23.0.0.0.0        23.0.0.0.0        23.4.0.24.03

    19c
    -----
    SQL> select INSTANCE_NAME,VERSION,VERSION_LEGACY,VERSION_FULL from v$instance;

    INSTANCE_NAME    VERSION           VERSION_LEGACY    VERSION_FULL
    ---------------- ----------------- ----------------- -----------------
    orcl19800        19.0.0.0.0        19.0.0.0.0        19.8.0.0.0

**Related Topics**

- [About Oracle Database Release Numbers](oracle-database-release-numbers.md)

**Parent topic:** Behavior Changes for Oracle Database 23ai Upgrade Planning

##### Oracle Spatial and Obsolete Objects

If you previously used Oracle Multimedia or Oracle Locator for media objects, then Oracle Spatial is installed during the upgrade to Oracle Database 23ai if `MDSYS`-owned Locator objects exist in the database.

If Oracle Spatial is not needed, then to avoid triggering a Spatial installation during upgrade, remove Locator objects before you start the upgrade. To remove Oracle Spatial, run `$ORACLE_HOME/md/admin/deinssdo.sql` in the earlier release Oracle home.

If Oracle Spatial is needed, then to reduce downtime, install Oracle Spatial manually before starting the upgrade. To install Oracle Spatial, run `$ORACLE_HOME/md/admin/mdinst.sql` in the earlier release Oracle home.

- For upgrades to Oracle Database 21c, if the `MDSYS` schema existed in the database, but Oracle Spatial (SDO) did not, then Oracle Locator (LCTR) was installed into the database registry.
- During upgrades to Oracle Database 23ai, Oracle Multimedia (`ORDIM`) is removed. LCTR is also removed if it exists in the database registry. If Locator objects in the MDSYS schema exist in the database, and SDO does not, then SDO is installed.
- If you downgrade from Oracle Database 23ai, then `ORDIM` is not restored as part of the downgrade.
- If you downgrade from Oracle Database 23ai to Oracle Database 21c, then LCTR is reinstalled.
- If you are plugging in a lower version non-CDB or PDB with `ORDIM`, or `LCTR`, or both in its database registry into a target 23ai CDB where SDO is not installed, then install SDO in the Oracle Database 23ai `CDB$ROOT` before the plugin.

**Related Topics**

- [Changes in This Release for Oracle Spatial and Graph Developer's Guide](../spatl/changes-this-release-oracle-spatial-developers-guide.md)
- [Pitfall: Upgrade to 21c fails when ORDIM is Present but no SDO](https://mikedietrichde.com/2021/08/25/upgrade-to-21c-fails-when-ordim-is-present-but-no-sdo/)
- [My Oracle Support Doc ID 2555923.1](https://support.oracle.com/rs?type=doc&id=2555923.1)

**Parent topic:** Behavior Changes for Oracle Database 23ai Upgrade Planning

##### REST APIs for AutoUpgrade

To facilitate safe and secure remote use of the AutoUpgrade utility for Oracle Database upgrades, AutoUpgrade now provides REST APIs (ORDS and OCI).

The Oracle REST Data Services (ORDS) database API is a database management and monitoring REST API embedded into Oracle REST Data Services. The Oracle Cloud Infrastructure (OCI) REST API is enabled by configuring the REST Adapter connection to use the OCI Signature Version 1 security policy. You can now use these features to run AutoUpgrade upgrades remotely over SSH. AutoUpgrade 22 and later versions support the use of the AutoUpgrade REST APIs.

**Related Topics**

- [https://docs.oracle.com/en/database/oracle/oracle-database/19/dbrst/](../dbrst)

**Parent topic:** Behavior Changes for Oracle Database 23ai Upgrade Planning

##### XML JSON Search Index Enhancements

Starting with Oracle Database 23ai, enhancements to JSON search can be a factor in your upgrade planning.

After you complete upgrade testing, to take advantage of the XML Search Index enhancements introduced in Oracle Database 23ai, you may want to plan to recreate your Oracle Text indexes and JSON Search Indexes after you update the `COMPATIBLE` parameter to `23.0.0.0`. However, there are no functionality changes to existing XQuery Full Text Indexes. These indexes will remain usable even after updating your `COMPATIBLE` setting.

After updating your `COMPATIBLE` parameter setting, existing JSON Search Indexes will be treated as including all available paths. Existing JSON Search Indexes that you do not recreate will remain usable. Path-aware JSON Search Indexes were introduced in Oracle Database 21c, so upgrade changes to JSON Search Indexes to enable path awareness are already handled as part of the upgrade to Oracle Database 21c. The XML Search Index and `INCLUDE` path clause features introduced with Oracle Database 23ai will require the database compatible setting to be set to `23.0.0.0.0`.

The indexing syntax you used in previous releases continues to be usable. However, syntax introduced with Oracle Database 23ai for existing indexing features will also become available, even with no compatibility setting change. However, for JSON Search Indexes, the `VALUE` mode and path-subsetting features will only be available after you create the index on a JSON type column.

After you upgrade `COMPATIBLE` to `23.0.0.0.0`, downgrade of the database is prevented in the following scenarios:

- In the presence of XML Search Indexes
- In the presence of XML or JSON Search Indexes using path-subsetting.

**Parent topic:** Behavior Changes for Oracle Database 23ai Upgrade Planning

##### SQL/JSON Function JSON_VALUE With a Boolean JSON Value

Starting with Oracle Database 23ai, the data type `BOOLEAN` is added to Oracle SQL. This feature extends SQL/JSON operators to allow returning a `BOOLEAN` value or accepting one as input.

After you update the `COMPATIBLE` parameter to `23.0.0.0`, SQL/JSON path-expression item methods `boolean()` and `booleanOnly()` now return a `SQL BOOLEAN` value. This means that, in a query that has `json_value` semantics, a value produced by the item method is of type `BOOLEAN` by default: the value is handled as if it were controlled by a `json_value` `RETURNING` clause of type `BOOLEAN`.

In earlier releases, these methods returned a `VARCHAR2(20)` value `'true'` or `'false'`. If you need to obtain a `VARCHAR2` value (for compatibility reasons, for example), then you can wrap the value with SQL function `to_char`.

**Related Topics**

- [Oracle Database JSON Developer’s GuideUsing SQL/JSON Function JSON_VALUE With a Boolean JSON Value](../adjsn/function-JSON_VALUE.md)

**Parent topic:** Behavior Changes for Oracle Database 23ai Upgrade Planning

##### Migrate from Non-AES Algorithms in FIPS Before Upgrade

If you use Transparent Data Encryption (TDE), then you must migrate your source database to AES encryption before starting your upgrade to Oracle Database 23ai.

In Oracle Database 23ai, when you use Transparent Data Encryption (TDE) configured for the Federal Information Processing Standard (FIPS), only Advanced Encryption Standard (AES) ciphers AES-128, AES-192, and AES-256 are allowed. If your source Oracle Database is configured for the FIPS mode, and it is using any other algorithms to encrypt a column or a tablespace, then the column and tablespace must be rekeyed using AES before upgrade.

If you upgrade your source database and it is using desupported algorithms for encryption, then the upgraded database will either fail to start up, or encrypted tablespaces will not be available, because the database cannot decrypt tablespace keys. In that case, Oracle recommends that you downgrade your database, upgrade your encryption keys to the supported AES ciphers, and then restart the upgrade.

**Parent topic:** Behavior Changes for Oracle Database 23ai Upgrade Planning

##### Oracle OLAP Deprecation Extended

Analytic workspaces, the OLAP DML programming language, financial reporting, and the OLAP Java API continue to be deprecated in Oracle Database 23ai.

Date: July 2024

Be aware that OLAP will not be supported beyond the term of the current release (Oracle Database 23ai) premier support. Oracle strongly recommends that you do not start new projects using OLAP and begin migrating applications using OLAP to alternatives now. If your application requires an in-database dimensional model, then consider using Oracle Analytic Views. Analytic views provide a dimensional semantic model, calculations, and query semantics using data in Oracle Database. When used with columnar tables, analytic views provide query performance similar to the OLAP Option. If your application requires support for advanced dimensional analytics, what-if analysis, or forecasting, then consider Oracle Essbase. Oracle Essbase is a multidimensional database management system with support for complex dimensional business analytics.

**Parent topic:** Behavior Changes for Oracle Database 23ai Upgrade Planning

##### About Read-Only Oracle Homes

With Oracle Database 23ai, an Oracle home is available in read/write mode by default. However, you can choose to configure an Oracle home in read-only mode after you have performed a software-only Oracle Database installation.

A read-only Oracle Home simplifies provisioning by implementing separation of installation and configuration.

In a read-only Oracle home, all the configuration data and log files reside outside of the read-only Oracle home.

Apart from the traditional `ORACLE_BASE` and `ORACLE_HOME` directories, the following directories contain files that used to be in `ORACLE_HOME`:

- `ORACLE_BASE_HOME`

- `ORACLE_BASE_CONFIG`

**Note:**

This feature does not affect how database administrators monitor, diagnose, and tune their system performance.

**Parent topic:** Behavior Changes for Oracle Database 23ai Upgrade Planning

##### SYSDATE and SYSTIMESTAMP Reflect PDB Time Zone

Starting with Oracle Database 23ai, `SYSDATE` and `SYSTIMESTAMP` can be managed separately for each database, following the individual database time zone setting.

To increase the applicability and transparency of multitenant for even more consolidations of independent databases, pluggable databases (PDBs) can now be managed individually for databases in container databases (CDBs). All user-visible operations and internal functions (for example, Oracle Scheduler or Oracle Flashback technology) adhere to this setting.

In previous releases, the `SYSDATE` and `SYSTIMESTAMP` settings were centrally managed, following the operating system level of the database host. With this update, Oracle Multitenant enables an Oracle Database to consolidate multiple pluggable databases as self-contained databases, improving resource utilization and database management. If you do not change your initialization parameters after the upgrade, then the default remains, and all pluggable databases inherit the system time from the operating system.

**Related Topics**

- [TIME_AT_DBTIMEZONE](../refrn/index.md)

**Parent topic:** Behavior Changes for Oracle Database 23ai Upgrade Planning

##### Oracle Spatial GeoRaster JPEG Compression on 4-band Raster Blocks

Starting with Oracle Database 23ai, JPEG compression on Oracle Spatial GeoRaster object can only be applied on 1-band and 3-band raster blocks.

If you have any GeoRaster objects that have 4-band raster blocks, then you must reblock the objects to 1-band or 3-band raster blocks before applying the JPEG compression. If you have any GeoRaster objects that have JPEG compression on 4-band raster blocks in previous releases, then you must reblock them to 1-band or 3-band raster blocks before upgrading to Oracle Database 23ai.

**Related Topics**

- [My Oracle Support Doc ID 2960620.1](https://support.oracle.com/rs?type=doc&id=2960620.1)

**Parent topic:** Behavior Changes for Oracle Database 23ai Upgrade Planning

##### Document-Identifier Field Names for Duality Views Requirements

Starting with Oracle Database 23ai, release update 23.4, when you are using duality views, the document-identifier field name must be `_id`.

The name `_id` is the required (and only) document identifier that you can use for duality views. Duality views that do not use the `_id` identifier field will fail. This restriction applies with Oracle Database 23ai (23.4) and later updates.

**Related Topics**

- ["Document-Identifier Fields for Duality Views" in JSON-Relational Duality Developer's Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/upgrd&id=JSNVU-GUID-A1445407-623E-4898-BE32-5789A11E2EBD)

**Parent topic:** Behavior Changes for Oracle Database 23ai Upgrade Planning

##### BIGFILE Is the Default for SYSAUX, SYSTEM, and USER Tablespaces

Starting with Oracle Database 23ai, newly created databases use BIGFILE as the default for the `SYSTEM`, `SYSAUX`, and `USER` tablespaces.

A **bigfile** tablespace is a tablespace with a single, but large datafile. Traditional small file tablespaces (`smallfile`), in contrast, typically contain multiple datafiles, but the files cannot be as large. Making `SYSAUX`, `SYSTEM` and `USER` tablespaces bigfile tablespaces by default will benefit large databases by reducing the number of datafiles, thereby simplifying datafile, tablespace and overall global database management for users.

**Parent topic:** Behavior Changes for Oracle Database 23ai Upgrade Planning

##### Terminal Release of Stored Outlines

Oracle Database 23ai is the terminal release of stored outlines. Migrate all stored outlines to SQL plan baselines.

Stored outlines were deprecated in Oracle Database 11g. Oracle is preparing to discontinue further support for stored outlines. Alternative functionality is provided using SQL Plan Management baselines, which provide numerous enhancements.

**Parent topic:** Behavior Changes for Oracle Database 23ai Upgrade Planning

#### Desupported Features in Oracle Database 23ai

As part of your upgrade plan, review the desupported features in this Oracle Database release.

- ODP.NET OracleConfiguration.DirectoryType Property and .NET Configuration File DIRECTORY_TYPE Setting Desupported
  The Oracle Data Provider for .NET `DirectoryType` property that is part of the `OracleConfiguration` class is desupported in Oracle Database 23ai.
- Original Export Utility (EXP) Desupported
  The original Oracle Database Export (`exp`) utility is desupported in Oracle Database 23ai.
- MySQL Client Library Driver for Oracle Desupported
  The MySQL Client Library Driver for Oracle is desupported in Oracle Database 23ai.
- ACFSUTIL REPL REVERSE Desupported
  The `acfsutil repl reverse` command is desupported in Oracle Database 23ai. Use `repl failover` or `repl switchover` instead.
- Cluster Domain - Domain Services Cluster Desupported
  Starting with Oracle Grid Infrastructure 23ai, Domain Services Clusters (DSC), which is part of the Oracle Cluster Domain architecture, are desupported.
- DBSNMP Packages for Adaptive Thresholds Feature Desupported
  DBSNMP PL/SQL packages associated with the Adaptive Thresholds feature are desupported in Oracle Database 23ai.
- Policy-Managed Database Deployment Desupported
  The policy-managed database deployment option is desupported in Oracle Database 23ai.
- Enterprise User Security User Migration Utility Desupport
  Starting with Database 23ai, the User Migration Utility (UMU) part of Enterprise User Security (EUS) is desupported.
- Oracle Enterprise Manager Database Express Desupported
  Oracle Enterprise Manager Database Express (EM Express) is desupported in Oracle Database Release 23ai.
- Oracle Wallet Manager (OWM) Desupported
  Starting with Oracle Database 23ai, the Oracle Wallet Manager (OWM) is desupported.
- RASADM Desupported
  The Real Application Security GUI administration tool (RASADM) is desupported with Oracle Database 23ai.
- Oracle Label Security Parameters and Functions Desupported
  Oracle Label Security (OLS) parameters and functions that were deprecated in Oracle Database 12c are desupported in Oracle Database 23ai.
- Oracle Internet Directory with Oracle Label Security Desupported
  The integration of Oracle Internet Directory (OID) with Oracle Label Security (OLS) is desupported with Oracle Database 23ai.
- Granting Administrative Privilege to RADIUS Users Desupported
  Starting with Oracle Database 23ai, users authenticating to the database using the legacy RADIUS API no longer are granted administrative privileges.
- Transparent Data Encryption PKI Keys Desupported
  Transparent Data Encryption (TDE) public key infrastructure (PKI) keys are desupported with Oracle Database 23ai
- GOST and SEED TDE Cryptographic Encryption Algorithms Desupported
  Starting with Oracle Database 23ai, the Transparent Data Encryption (TDE) encryption libraries for the GOST and SEED algorithms are desupported and removed. The GOST and SEED decryption libraries are deprecated. Both are removed on HP Itanium platforms.
- Oracle Database 10G Password Verifier Desupported
  Starting with Oracle Database 23ai, the 10G database password verifier is desupported.
- Transport Layer Security versions 1.0 and 1.1 Desupported
  Starting with Database 23ai, the use of Transport Layer Security protocol versions 1.0 and 1.1 are desupported.
- Unix Crypt (MD5crypt) Password Verifier Desupported
  The Unix Crypt (`MD5crypt`) password verifier algorithm is desupported in Oracle Database 23ai server and clients.
- FIPS Strength 80 Encryption Desupported
  FIPS encryption strength 80 is desupported with the release of Oracle Database 23ai. Use FIPS encryption strength 112 instead.
- Diffie-Hellman Anonymous Ciphers Desupported
  The use of Diffie-Hellman anonymous ciphers (DH anon) is desupported with Oracle Database 23ai for both outbound connections and for database client/server connections.
- Oracle Database Extensions for .NET Desupported
  Oracle Database Extensions for .NET is desupported. Oracle recommends that you either place .NET code in the middle tier, or use the External Procedures feature, or rewrite the code using PL/SQL or Java.
- Quality of Service Management Desupported
  Starting with Oracle Database Release 23ai, Oracle Quality of Service Management (QoSM, or QoS Management) is desupported.
- Traditional Auditing Desupported
  Traditional auditing is desupported in Oracle Database 23ai. Oracle recommends that you use unified auditing.
- Desupport of config.sh
  Starting with Oracle Database 23ai, the Oracle Grid Infrastructure Configuration Wizard tool (`config.sh`) is desupported. Use `gridSetup.sh` instead.
- OLS Table LABELS Column Desupport
  The `LABELS` column in the `ALL_SA_USER_LABELS` and `DBA_SA_USER_LABELS `OLS tables is desupported in Oracle Database 23ai.
- Desupport of 32-Bit Oracle Database Clients
  32-bit Oracle Database clients are desupported in Oracle Database 23ai.
- Desupport of Oracle GoldenGate Replication for Oracle Globally Distributed Database High Availability
  The use of Oracle GoldenGate Replication for Shard-Level High Availability in Oracle Globally Distributed Database (formerly known as Oracle Sharding) is desupported in Oracle Database 23ai.
- Grid Infrastructure Management Repository (GIMR) Desupported
  Starting with Oracle Database 23ai, the use of Grid Infrastructure Management Repository (GIMR) is desupported.
- Data Recovery Advisor (DRA) Desupport
  Starting in Oracle Database 23ai, the Data Recovery Advisor (DRA) feature is desupported.
- DBUA and Manual Upgrade Methods Desupported
  AutoUpgrade and Replay Upgrade are the only supported method for upgrading to Oracle Database 23ai. All other methods, including Database Upgrade Assistant (DBUA), are desupported.
- Desupport of Oracle Data Masking and Subsetting with Oracle Real Application Testing
  The integration of data masking with Oracle Real Application Testing is desupported in Oracle Database 23ai.
- Desupport of Shared Grid Naming Service Option for Addresses
  The Shared GNS option of Grid Naming Service for name resolution in a cluster is desupported in Oracle Grid Infrastructure 23ai.
- DBMS_AUDIT_MGMT.FLUSH_UNIFIED_AUDIT_TRAIL Procedure Desupported
  The `DBMS_AUDIT_MGMT` procedure `DBMS_AUDIT_MGMT.FLUSH_UNIFIED_AUDIT` feature is desupported in Oracle Database 23ai.
- AUDIT_TRAIL_WRITE Mode of the AUDIT_TRAIL_PROPERTY Parameter Desupported
  The DBMS_AUDIT_MGMT AUDIT_TRAIL_WRITE Mode of the AUDIT_TRAIL_PROPERTY feature is desupported in Oracle Database 23ai.
- Cluster Time Synchronization Service Desupported
  Cluster Time Synchronization Service (CTSS) is desupported in Oracle Database 23ai.
- Oracle Connection Manager Parameter (CMAN) Password Access Desupported
  The use of password access to Oracle Connection Manager parameters is desupported in Oracle Database 23ai.
- Desupport of EUS Current User Database Links
  Current user database links for Enterprise User Security (EUS) are not supported in Oracle Database 23ai
- Desupport of oracle.jdbc.rowset Package
  The Java `oracle.jdbc.rowset` package is desupported in Oracle Database 23ai.
- Desupport of ACFS on IBM AIX
  Oracle Advanced Cluster File System (ACFS) on IBM AIX is desupported in Oracle Database 23ai
- RECOVER…SNAPSHOT TIME Desupported
  The `RECOVER…SNAPSHOT TIME` method of recovering a database to a point in time using a particular snapshot is desupported in Oracle Database 23ai.

**Parent topic:** Oracle Database 23ai Behavior Changes, Desupports, and Deprecations

##### ODP.NET OracleConfiguration.DirectoryType Property and .NET Configuration File DIRECTORY_TYPE Setting Desupported

The Oracle Data Provider for .NET `DirectoryType` property that is part of the `OracleConfiguration` class is desupported in Oracle Database 23ai.

Date: April 2023

The .NET configuration file `DIRECTORY_SERVER_TYPE` setting replaces the `DIRECTORY_TYPE` setting. The `OracleConfiguration DirectoryServerType` property replaces the `DirectoryType` property. All of these properties have identical functionality. Oracle recommends to developers to use and migrate to the `DirectoryServerType` property. The `DirectoryServerType` name better aligns with the `ldap.ora` parameter, `DIRECTORY_SERVER_TYPE`, which provides equivalent functionality.

**Parent topic:** Desupported Features in Oracle Database 23ai

##### Original Export Utility (EXP) Desupported

The original Oracle Database Export (`exp`) utility is desupported in Oracle Database 23ai.

Date: April 2023

Oracle recommends that you use Oracle Data Pump Export (`expdp`).

**Parent topic:** Desupported Features in Oracle Database 23ai

##### MySQL Client Library Driver for Oracle Desupported

The MySQL Client Library Driver for Oracle is desupported in Oracle Database 23ai.

Date: April 2023

The MySQL Client library driver, `liboramysql`, was deprecated in Oracle Database 21c. It is now desupported. There is no replacement. This desupport does not affect the ability of older Oracle Database Client releases that use `liboramysql` to connect to the database. However, the features available to use through these clients eventually can be limited.

**Parent topic:** Desupported Features in Oracle Database 23ai

##### ACFSUTIL REPL REVERSE Desupported

The `acfsutil repl reverse` command is desupported in Oracle Database 23ai. Use `repl failover` or `repl switchover` instead.

Date: April 2023

The Oracle Automatic Cluster File System (ACFS) command utility `acfsutil` includes the commands `repl failover` and `repl switchover`. These commands provide more functionality, including all the functions of `acfsutil repl reverse`. For this reason, Oracle is desupporting the `acfsutil repl reverse` command.

**Parent topic:** Desupported Features in Oracle Database 23ai

##### Cluster Domain - Domain Services Cluster Desupported

Starting with Oracle Grid Infrastructure 23ai, Domain Services Clusters (DSC), which is part of the Oracle Cluster Domain architecture, are desupported.

Date: April 2023

Oracle Cluster Domains consist of a Domain Services Cluster (DSC) and Member Clusters. Member Clusters were deprecated in Oracle Grid Infrastructure 19c. The DSC continues to be available to provide services to production clusters. However, with most of those services no longer requiring the DSC for hosting, installation of DSCs are desupported in Oracle Database 23ai. Oracle recommends that you use any cluster or system of your choice for services previously hosted on the DSC, if applicable. Oracle will continue to support the DSC for hosting shared services, until each service can be used on alternative systems.

**Parent topic:** Desupported Features in Oracle Database 23ai

##### DBSNMP Packages for Adaptive Thresholds Feature Desupported

DBSNMP PL/SQL packages associated with the Adaptive Thresholds feature are desupported in Oracle Database 23ai.

Date: April 2023

Beginning with Oracle Enterprise Manager Cloud Control 13.5, all features of Database Server Adaptive Thresholds and Baseline Metric Thresholds are removed for all Oracle Database targets. The following database server side packages that support this feature are longer available: DBSNMP.BSLN, DBSNMP.BSLN_INTERNAL. DBSNMP.MGMT_RESPONSE continues to be supported.

For more information about this deprecation and desupport, refer to My Oracle Support 2697846.1

**Parent topic:** Desupported Features in Oracle Database 23ai

##### Policy-Managed Database Deployment Desupported

The policy-managed database deployment option is desupported in Oracle Database 23ai.

Date: April 2023

Policy-managed databases were deprecated in Oracle Database 21c, and admin-managed database deployment was enhanced with functions similar to policy managed databases. By converging the automation provided by policy-managed database with the consistency of an admin-managed database, Oracle seeks to simplify database management tasks for database administrators. This converged database deployment provides the best of both options, such as providing the options to rank and define the order of database startup, without requiring you to choose a specific style during deployment.

**Parent topic:** Desupported Features in Oracle Database 23ai

##### Enterprise User Security User Migration Utility Desupport

Starting with Database 23ai, the User Migration Utility (UMU) part of Enterprise User Security (EUS) is desupported.

Date: April 2023

There is no workaround.

**Parent topic:** Desupported Features in Oracle Database 23ai

##### Oracle Enterprise Manager Database Express Desupported

Oracle Enterprise Manager Database Express (EM Express) is desupported in Oracle Database Release 23ai.

Date: April 2023

EM Express is a web-based database management tool that is built inside Oracle Database. It supports key performance management and basic database administration functions. EM Express was deprecated in Oracle Database 21c. Many of EM Express's capabilities are now available in Oracle Cloud Infrastructure (OCI) Database Management service, Oracle Enterprise Manager Cloud Control, or Oracle SQL Developer.

Instead of EM Express, Oracle recommends that you choose a tool that fits the requirements and deployment type (cloud, on-premises, or hybrid) from OCI Database Management service, Oracle Enterprise Manager Cloud Control or Oracle SQL Developer Web or Oracle SQL Developer desktop products.

**Parent topic:** Desupported Features in Oracle Database 23ai

##### Oracle Wallet Manager (OWM) Desupported

Starting with Oracle Database 23ai, the Oracle Wallet Manager (OWM) is desupported.

Date: April 2023

Oracle recommends using the `orapki` command line tool to replace OWM.

**Parent topic:** Desupported Features in Oracle Database 23ai

##### RASADM Desupported

The Real Application Security GUI administration tool (RASADM) is desupported with Oracle Database 23ai.

Date: April 2023

RASADM is no longer supported for use with Oracle Database 23ai. Oracle recommends that you use the RAS PL/SQL API which includes all the functionality of RASADM.

**Parent topic:** Desupported Features in Oracle Database 23ai

##### Oracle Label Security Parameters and Functions Desupported

Oracle Label Security (OLS) parameters and functions that were deprecated in Oracle Database 12c are desupported in Oracle Database 23ai.

Date: April 2023

These previously deprecated OLS parameters and functions have alternate parameters that can be used.

The following OLS functions and parameters are desupported:

`Least_UBOUND`. Use `OLS_GREATEST_LBOUND` instead.
`LUBD`. Use `OLS_GLBD` instead.
`DOMINATES`. Use the `OLS_DOMINATES` standalone function instead.
`DOM`. Use the `OLS_STRICTLY_DOMINATES` standalone function instead.
`STRICTLY_DOMINATES`. Use the `OLS_STRICTLY_DOMINATES` standalone function instead.
`S_DOM`. Use the `OLS_STRICTLY_DOMINATES` standalone function instead.
`DOMINATED_BY`. Use the `OLS_DOMINATED_BY` standalone function instead.
`DOM_BY`. Use the `OLS_DOMINATED_BY` standalone function instead.
`STRICTLY_DOMINATED_BY`. Use the OLS_STRICTLY_DOMINATED_BY standalone function instead.
`S_DOM_BY`. Use the `OLS_STRICTLY_DOMINATED_BY` standalone function instead.

Also, the OLS standalone function `SA_UTL.DOMINATES` boolean datatype is desupported. The `SA_UTL.DOMINATES` function that uses the `NUMBER` datatype is not deprecated.

For reference about alternatives see: [Oracle Label Security Administrator's Guide Deprecated Features](https://docs.oracle.com/database/121/OLSAG/release_changes.htm#GUID-8772D3A3-E733-42A4-9E1B-DD9408352CE4)

**Parent topic:** Desupported Features in Oracle Database 23ai

##### Oracle Internet Directory with Oracle Label Security Desupported

The integration of Oracle Internet Directory (OID) with Oracle Label Security (OLS) is desupported with Oracle Database 23ai.

Date: April 2023

The use of OID to store OLS policies and labels is desupported with Oracle Database 23ai. No replacement for this feature is planned. If you are using this feature, then you must create a custom method to copy and store this information.

**Parent topic:** Desupported Features in Oracle Database 23ai

##### Granting Administrative Privilege to RADIUS Users Desupported

Starting with Oracle Database 23ai, users authenticating to the database using the legacy RADIUS API no longer are granted administrative privileges.

Date: April 2023

In previous releases, users authenticating with RADIUS API could be granted administrative privileges such as `SYSDBA` or `SYSBACKUP`. In Oracle Database 23ai, Oracle introduces a new RADIUS API that uses the latest standards. To grant administrative privileges to users, ensure the database connection to the database uses the new RADIUS API, and that you are using the Oracle Database 23ai client to connect to the Oracle Database 23ai server.

**Parent topic:** Desupported Features in Oracle Database 23ai

##### Transparent Data Encryption PKI Keys Desupported

Transparent Data Encryption (TDE) public key infrastructure (PKI) keys are desupported with Oracle Database 23ai

Date: April 2023

The deprecation of TDE PKI keys was announced with Oracle Database 12c. Oracle recommends using one of the current TDE keys instead. Follow the documentation to rekey your database with a new TDE key before upgrading the Oracle Database 23ai. If the upgrade script detects PKI keys used with TDE, then the script will stop and notify you to rekey the TDE Master Key before upgrade.

**Related Topics**

- [Setting or Rekeying the TDE Master Encryption Key in the Keystore](../asoag/managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Desupported Features in Oracle Database 23ai

##### GOST and SEED TDE Cryptographic Encryption Algorithms Desupported

Starting with Oracle Database 23ai, the Transparent Data Encryption (TDE) encryption libraries for the GOST and SEED algorithms are desupported and removed. The GOST and SEED decryption libraries are deprecated. Both are removed on HP Itanium platforms.

Date: April 2023

GOST 28147-89 has been deprecated by the Russian government, and SEED has been deprecated by the South Korean government. If you need South Korean government-approved TDE cryptography, then use ARIA instead. If you are using GOST 28147-89, then you must decrypt and encrypt with another supported TDE algorithm. The decryption algorithms for GOST 28147-89 and SEED are included with Oracle Database 23ai, but are deprecated, and the GOST encryption algorithm is desupported with Oracle Database 23ai. If you are using GOST or SEED for TDE encryption, then Oracle recommends that you perform an online rekey operation before upgrading to Oracle Database 23ai. However, with the exception of the HP Itanium platform, the GOST and SEED decryption libraries are available with Oracle Database 23ai, so you can also decrypt after upgrading.

**Parent topic:** Desupported Features in Oracle Database 23ai

##### Oracle Database 10G Password Verifier Desupported

Starting with Oracle Database 23ai, the 10G database password verifier is desupported.

Date: April 2023

The database password verifier for Oracle Database 10g, `10G` is no longer supported or available on Oracle Database 23ai. Refer to the database upgrade guide preinstallation chapters for information about how to identify the Oracle Database 10G database password verifiers, and how to update the database user to use the latest and most secure database password verifier cryptography.

Parameters associated with the 10G verifiers were desupported with Oracle Database 21c:

- `IGNORECASE `
- `SEC_CASE_SENSITIVE_LOGON`

The 11G and 12C verifiers were the default password verifiers starting with Oracle Database 12c Release 2 (12.2). The following related parameter values are also desupported:

- `SQLNET.ALLOWED_LOGON_VERSION_SERVER` values of 8, 9, 10 and 11 are now removed (12 and 12a remain).
- `SQLNET.ALLOWED_LOGON_VERSION_CLIENT` value of 11 is now removed (12 and 12a remain).

In addition, note the following:

- Patched 10g and 11g clients using the 12c verifier will continue to work.
- Client capabilities listed in the Database Net Services Reference are modified.
- `O3L`, `O4L`, and `O5L` client capabilities are removed from the client capabilities table.

**Parent topic:** Desupported Features in Oracle Database 23ai

##### Transport Layer Security versions 1.0 and 1.1 Desupported

Starting with Database 23ai, the use of Transport Layer Security protocol versions 1.0 and 1.1 are desupported.

Date: April 2023

In most cases, this change will not have any impact, because the database client and server will negotiate the use of the most secure protocol and cipher algorithm. However, if TLS 1.0 or 1.1 has been specified, then you must either remove it to allow the database server and client to pick the most secure protocol, or you must specify either TLS 1.2, or TLS 1.3, or both, for the protocol. Oracle recommends using the latest, most secure protocol. That protocol is TLS 1.3, which is introduced with Oracle Database 23ai.

**Parent topic:** Desupported Features in Oracle Database 23ai

##### Unix Crypt (MD5crypt) Password Verifier Desupported

The Unix Crypt (`MD5crypt`) password verifier algorithm is desupported in Oracle Database 23ai server and clients.

Date: April 2023

Enterprise User Security (EUS) customers with users in Oracle Internet Directory (OID) potentially can be using older, less secure password verifiers generated by Unix Crypt, either by OID, or by the operating system, before they were migrated to OID. Compared to current methods to hash the password, Unix Crypt is a less secure algorithm. Oracle Database can no longer authenticate EUS or OID users with the older password verifiers. Oracle recommends that you reset passwords in OID now, using newer, more secure hashing algorithms.

**Parent topic:** Desupported Features in Oracle Database 23ai

##### FIPS Strength 80 Encryption Desupported

FIPS encryption strength 80 is desupported with the release of Oracle Database 23ai. Use FIPS encryption strength 112 instead.

Date: April 2023

FIPS encryption strength 80 is equivalent to the 1024 key lengths for RSA, Diffie-Hellman (DH), and Digital Signature Algorithm (DSA). The lower strength 0 (RSA/DH/DSA 512 key length) was desupported for FIPS use with Oracle Database 21c. The only remaining FIPS encryption strength supported for Oracle Database 23ai is 112 (RSA/DH/DSA 2048 key length). The encryption strength of 80 and 0 are still available for non-FIPS use. Oracle recommends that you use FIPS 112, because FIPS encryption strength 112 is much stronger than FIPS encryption strength 80, and the longer key lengths are used with Oracle Database 23ai.

**Parent topic:** Desupported Features in Oracle Database 23ai

##### Diffie-Hellman Anonymous Ciphers Desupported

The use of Diffie-Hellman anonymous ciphers (DH anon) is desupported with Oracle Database 23ai for both outbound connections and for database client/server connections.

Date: April 2023

Removing the DH anon ciphers improves the security for Oracle Database connections.

The following 3 ciphers are desupported with Oracle Database 23ai:

- TLS_DH_ANON_WITH_AES_256_GCM_SHA384

- TLS_DH_ANON_WITH_AES_128_GCM_SHA256

- SSL_DH_ANON_WITH_3DES_EDE_CBC_SHA

If you are an Enterprise User Security (EUS) customer, then you must confirm that you are using server-based TLS authentication in your OID connections. For database client/server connections, you should allow the server and client to negotiate for the strongest possible connection. If a DH anon cipher was specified, then you must remove that cipher, and the database server must be authenticated for a 1-way TLS connection.

**Parent topic:** Desupported Features in Oracle Database 23ai

##### Oracle Database Extensions for .NET Desupported

Oracle Database Extensions for .NET is desupported. Oracle recommends that you either place .NET code in the middle tier, or use the External Procedures feature, or rewrite the code using PL/SQL or Java.

Date: April 2023

Oracle Database Extensions for .NET is a feature of Oracle Database on Microsoft Windows that enables you to use stored procedures and functions written in a language managed by .NET, such as C#.

Oracle Database hosts the Microsoft Common Language Runtime (CLR) in an external process, outside of the Oracle Database process. Application developers can write stored procedures and functions using any .NET compliant language, such as C# and VB.NET, and use these .NET stored procedures in the database, in the same manner as other PL/SQL or Java stored procedures. .NET stored procedures can be called from PL/SQL packages, procedures, functions, and triggers; from SQL statements; or from anywhere a PL/SQL procedure or function can be called.

Migration options include:

- Moving the .NET code (assemblies) into a middle tier
- Using the External Procedures feature to have the external process load and execute the .NET assembly
- Rewriting the stored procedures using PL/SQL or Java

**Parent topic:** Desupported Features in Oracle Database 23ai

##### Quality of Service Management Desupported

Starting with Oracle Database Release 23ai, Oracle Quality of Service Management (QoSM, or QoS Management) is desupported.

Date: April 2023

Oracle QoSM automates the workload management for an entire system by adjusting the system configuration based on predefined policies to keep applications running at the performance levels needed. Applications and databases are increasingly deployed in systems that provide some of the resource management capabilities of QoSM. At the same time, Oracle’s Autonomous Health Framework has been enhanced to adjust and provide recommendations to mitigate events and conditions that impact the health and operational capability of a system and its associated components. For those reasons, QoSM and its Memory Guard feature are desupported with Oracle Database 23ai.

**Parent topic:** Desupported Features in Oracle Database 23ai

##### Traditional Auditing Desupported

Traditional auditing is desupported in Oracle Database 23ai. Oracle recommends that you use unified auditing.

Date: April 2023

Starting with Oracle Database 23ai, unified auditing is the way forward to perform Oracle Database auditing. Unified auditing offers more flexibility to perform selective and effective auditing, which helps you focus on activities that really matter to your enterprise. Unified auditing has one single and secure unified trail, conditional policy for audit selectivity, and default preconfigured policies for simplicity. To improve security and compliance, Oracle strongly recommends that you use unified auditing.

**Related Topics**

- [Handling the Desupport of Traditional Auditing](../dbseg/index.md)

**Parent topic:** Desupported Features in Oracle Database 23ai

##### Desupport of config.sh

Starting with Oracle Database 23ai, the Oracle Grid Infrastructure Configuration Wizard tool (`config.sh`) is desupported. Use `gridSetup.sh` instead.

Date: April 2023

With the introduction of image-based Oracle Grid Infrastructure installation, the `config.sh` functionality has become obsolete. The `gridSetup.sh` script supports the response file functionality previously used with config.sh.

**Parent topic:** Desupported Features in Oracle Database 23ai

##### OLS Table LABELS Column Desupport

The `LABELS` column in the `ALL_SA_USER_LABELS` and `DBA_SA_USER_LABELS `OLS tables is desupported in Oracle Database 23ai.

Date: April 2023

The `LABELS` column was previously deprecated for Oracle Label Security (OLS), because it duplicates information available in the other columns. This change improves the usability of these tables, because you no longer need to choose which column you should reference.

**Parent topic:** Desupported Features in Oracle Database 23ai

##### Desupport of 32-Bit Oracle Database Clients

32-bit Oracle Database clients are desupported in Oracle Database 23ai.

Date: April 2023

Oracle has discontinued developing 32-bit Oracle Database clients. Oracle recommends that you use 64-bit Oracle Database clients. If you are using 32-bit applications, then you can continue to use older 32-bit Oracle Database clients, subject to “Client / Server Interoperability Support Matrix for Different Oracle Versions (Doc ID 207303.1)," and the release support lifecycle (My Oracle Support 742060.1).

**Related Topics**

- [Client / Server Interoperability Support Matrix for Different Oracle Versions (Doc ID 207303.1)](https://support.oracle.com/rs?type=doc&id=207303.1)
- [Release Schedule of Current Database Releases (Doc ID 742060.1)](https://support.oracle.com/rs?type=doc&id=742060.1)

**Parent topic:** Desupported Features in Oracle Database 23ai

##### Desupport of Oracle GoldenGate Replication for Oracle Globally Distributed Database High Availability

The use of Oracle GoldenGate Replication for Shard-Level High Availability in Oracle Globally Distributed Database (formerly known as Oracle Sharding) is desupported in Oracle Database 23ai.

Date: April 2023

**Parent topic:** Desupported Features in Oracle Database 23ai

##### Grid Infrastructure Management Repository (GIMR) Desupported

Starting with Oracle Database 23ai, the use of Grid Infrastructure Management Repository (GIMR) is desupported.

Date: July 2023

Oracle is using another repository to store metadata. The use of GIMR is desupported in Oracle Database 23ai. This transition is planned so that there will be no effect on features using GIMR (GIMR clients), such as Oracle Autonomous Health Framework (AHF), Cluster Health Monitor (CHM), Oracle Cluster Health Advisor (CHA), or Oracle Fleet Patching and Provisioning (FPP).

**Parent topic:** Desupported Features in Oracle Database 23ai

##### Data Recovery Advisor (DRA) Desupport

Starting in Oracle Database 23ai, the Data Recovery Advisor (DRA) feature is desupported.

Date: July 2023

The desupport of DRA includes desupporting the following Oracle Recovery Manager (RMAN) commands: `LIST FAILURE`, `ADVISE FAILURE`, `REPAIR FAILURE`, and `CHANGE FAILURE`. Database administrators will no longer have access to these commands. There is no replacement feature for DRA.

**Parent topic:** Desupported Features in Oracle Database 23ai

##### DBUA and Manual Upgrade Methods Desupported

AutoUpgrade and Replay Upgrade are the only supported method for upgrading to Oracle Database 23ai. All other methods, including Database Upgrade Assistant (DBUA), are desupported.

Date: July 2023

Except for AutoUpgrade and Replay Upgrade, all other methods for upgrading are desupported for upgrades and migrations to Oracle Database 23ai, including Database Upgrade Assistant (DBUA) and the Parallel Upgrade Utility (`dbupgrade` or `catctl.pl`). This desupport notice applies to upgrades whether they are done on-premises, in any cloud, or in a hybrid approach. Oracle AutoUpgrade or Replay Upgrade are the only supported tools to upgrade Oracle Database, with or without a migration to the multitenant (CDB) architecture.

**Related Topics**

- [AutoUpgrade Tool (Doc ID 2485457.1)](https://support.oracle.com/rs?type=doc&id=2485457.1)

**Parent topic:** Desupported Features in Oracle Database 23ai

##### Desupport of Oracle Data Masking and Subsetting with Oracle Real Application Testing

The integration of data masking with Oracle Real Application Testing is desupported in Oracle Database 23ai.

Date: November 2023

For testing, Oracle recommends that you keep the test database in the production realm for security, but create user accounts for testing that cannot access your data to run both SQL Performance Analyzer (SPA) trials and Database Replay.

**Parent topic:** Desupported Features in Oracle Database 23ai

##### Desupport of Shared Grid Naming Service Option for Addresses

The Shared GNS option of Grid Naming Service for name resolution in a cluster is desupported in Oracle Grid Infrastructure 23ai.

Date: December 2023

The Shared GNS name resolution option is a daemon running on one cluster that is configured to provide name resolution for all clusters in domains that are delegated to GNS for resolution, which can be centrally managed using SRVCTL commands. Starting with Oracle Database 23ai, both the option of using role to specify a primary or secondary role for GNS and the option of using Shared GNS are discontinued as deployment options. Existing configurations using these features will still work after upgrade, but they will not be available for new GNS deployments. Oracle recommends that you use your own DNS to configure client connections to Oracle Grid Infrastructure.

**Parent topic:** Desupported Features in Oracle Database 23ai

##### DBMS_AUDIT_MGMT.FLUSH_UNIFIED_AUDIT_TRAIL Procedure Desupported

The `DBMS_AUDIT_MGMT` procedure `DBMS_AUDIT_MGMT.FLUSH_UNIFIED_AUDIT` feature is desupported in Oracle Database 23ai.

Date: December 2023

This procedure is no longer necessary because audit records now bypass the common logging infrastructure queues and are directly written to a new internal relational table.

**Parent topic:** Desupported Features in Oracle Database 23ai

##### AUDIT_TRAIL_WRITE Mode of the AUDIT_TRAIL_PROPERTY Parameter Desupported

The DBMS_AUDIT_MGMT AUDIT_TRAIL_WRITE Mode of the AUDIT_TRAIL_PROPERTY feature is desupported in Oracle Database 23ai.

Date: December 2023

This procedure is no longer necessary because audit records now bypass the common logging infrastructure queues and are directly written to a new internal relational table.

**Parent topic:** Desupported Features in Oracle Database 23ai

##### Cluster Time Synchronization Service Desupported

Cluster Time Synchronization Service (CTSS) is desupported in Oracle Database 23ai.

Date: January 2024

To synchronize time between cluster member nodes, use either an operating system configured network time protocol such as `ntp` or `chrony`, or Microsoft Windows Time service. To verify that you have network time synchronization configured, you can use the `cluvfy comp clocksync -n allnodes` command.

**Parent topic:** Desupported Features in Oracle Database 23ai

##### Oracle Connection Manager Parameter (CMAN) Password Access Desupported

The use of password access to Oracle Connection Manager parameters is desupported in Oracle Database 23ai.

Date: March 2024

Oracle provides an enhanced connection method, Local Operating System Authentication" (LOSA), which permits only the user who started CMAN to perform admin operations. This method is consistent with other operating system authentication methods used with Oracle Database. If you are currently using password access to CMAN, then Oracle recommends that you remove the CMAN password, and instead rely on LOSA.

**Parent topic:** Desupported Features in Oracle Database 23ai

##### Desupport of EUS Current User Database Links

Current user database links for Enterprise User Security (EUS) are not supported in Oracle Database 23ai

Date: April 2024

Because Oracle Database releases after Oracle Database 19c only use the multitenant architecture, the use of EUS current user database links (`CREATE DATABASE LINK…TO CURRENT_USER` ) is not supported in releases after Oracle Database 19c. Oracle recommends that you use fixed user or connected user database links with EUS.

**Parent topic:** Desupported Features in Oracle Database 23ai

##### Desupport of oracle.jdbc.rowset Package

The Java `oracle.jdbc.rowset` package is desupported in Oracle Database 23ai.

Date: May 2024

Oracle recommends that you use the Standard JDBC Rowset package to replace this feature.

**Parent topic:** Desupported Features in Oracle Database 23ai

##### Desupport of ACFS on IBM AIX

Oracle Advanced Cluster File System (ACFS) on IBM AIX is desupported in Oracle Database 23ai

Date: December 2024

To align the support for the IBM AIX platform, Oracle Advanced Cluster File System (ACFS) on IBM AIX is desupported in Oracle Database 23ai. For data or files currently stored on an ACFS file system that cannot be stored in Oracle Database, you can use the IBM General Parallel File System (GPFS).

**Parent topic:** Desupported Features in Oracle Database 23ai

##### RECOVER…SNAPSHOT TIME Desupported

The `RECOVER…SNAPSHOT TIME` method of recovering a database to a point in time using a particular snapshot is desupported in Oracle Database 23ai.

Date: February 2025

Instead of `RECOVER…SNAPSHOT TIME`, Oracle recommends that you use `ALTER DATABASE BEGIN/END BACKUP` before and after creating the storage snapshot of the data files and then use `RECOVER .. UNTIL TIME` to a specific timestamp or system change number (SCN) after the `END BACKUP` completion time. Oracle recommends that `ALTER DATABASE BEGIN/END BACKUP` always be used when performing snapshots on a running database to ensure data recovery integrity. Archived log redo logs must be separately backed up and restored for recovery operations.

Note that Oracle’s best practice for database backup and recovery is to use Recovery Manager (RMAN) only, not storage snapshots, and is integrated with Zero Data Loss Recovery Appliance (ZDLRA) to offer the highest levels of database protection.

**Related Topics**

- [IT Infrastructure Engineered Systems Zero Data Loss Recovery Appliance](https://www.oracle.com/engineered-systems/zero-data-loss-recovery-appliance/)

**Parent topic:** Desupported Features in Oracle Database 23ai

#### Desupported Parameters in Oracle Database 23ai

As part of your upgrade plan, review the initialization parameters that are not supported starting with this Oracle Database release.

- EXTERNAL_NAME Parameter in SYS_CONTEXT USERENV Desupported
  The `EXTERNAL_NAME` parameter in `SYS_CONTEXT USERENV` is desupported in Oracle Database 23ai
- Service Attribute Value SESSION_STATE_CONSISTENCY = STATIC Desupported
  The service attribute values `FAILOVER_TYPE = TRANSACTION` with `SESSION_STATE_CONSISTENCY = STATIC` are no longer a supported service attribute combination.
- Oracle Label Security Parameters and Functions Desupported
  Oracle Label Security (OLS) parameters and functions that were deprecated in Oracle Database 12c are desupported in Oracle Database 23ai.
- ENCRYPTION_WALLET_LOCATION Parameter Desupported
  Starting with Oracle Database 23ai, the parameter `ENCRYPTION_WALLET_LOCATION` is desupported.
- ADD_SSLV3_TO_DEFAULT SQLNET.ORA Parameter (and SSLv3) Desupported
  Starting with Oracle Database 23ai, the Secure Socket Layer v3 protocol (SSLv3) is no longer supported for database server-client connections, and the `sqlnet.ora` parameter `ADD_SSLV3_TO_DEFAULT` has been removed.
- Desupport of OPTIMIZER_SECURE_VIEW_MERGING Parameter
  Oracle is desupporting the initialization parameter `OPTIMIZER_SECURE_VIEW_MERGING` in Oracle Database 23ai

**Parent topic:** Oracle Database 23ai Behavior Changes, Desupports, and Deprecations

##### EXTERNAL_NAME Parameter in SYS_CONTEXT USERENV Desupported

The `EXTERNAL_NAME` parameter in `SYS_CONTEXT USERENV` is desupported in Oracle Database 23ai

Date: April 2023

The `EXTERNAL_NAME` parameter was deprecated in Oracle Database 10g. Two newer parameters, `AUTHENTICATED_IDENTITY` and `ENTERPRISE_IDENTITY`, offer more information. `EXTERNAL_NAME` is removed in Oracle Database 23ai.

**Parent topic:** Desupported Parameters in Oracle Database 23ai

##### Service Attribute Value SESSION_STATE_CONSISTENCY = STATIC Desupported

The service attribute values `FAILOVER_TYPE = TRANSACTION` with `SESSION_STATE_CONSISTENCY = STATIC` are no longer a supported service attribute combination.

Date: April 2023

In previous releases, you could use the service parameter `SESSION_STATE_CONSISTENCY` to manage session state automatically using Application Continuity by setting `SESSION_STATE_CONSISTENCY` to `DYNAMIC` or `STATIC`. However, starting with Oracle Database 23ai, you can no longer use the `STATIC` option. Instead, use one of the following failover options:

- `FAILOVER_TYPE = AUTO` with `SESSION_STATE_CONSISTENCY = AUTO`
- `FAILOVER_TYPE = TRANSACTION` with `SESSION_STATE_CONSISTENCY = DYNAMIC`

These configurations enforce session state tracking in Oracle Database, ensuring that session state is preserved at session migration and session failover.

Note that starting with Oracle Database 21c, you may also wish to set the `RESET_STATE` attribute to clear your session state set by applications in request at the end of the request. For more information, see `RESET_STATE`. For planned maintenance, Oracle recommends that you drain requests from Oracle Database connection pools in combination with Application Continuity for those requests that do not complete.

**Related Topics**

- [Session State Consistency](../racad/ensuring-application-continuity.md)

**Parent topic:** Desupported Parameters in Oracle Database 23ai

##### Oracle Label Security Parameters and Functions Desupported

Oracle Label Security (OLS) parameters and functions that were deprecated in Oracle Database 12c are desupported in Oracle Database 23ai.

Date: April 2023

These previously deprecated OLS parameters and functions have alternate parameters that can be used.

The following OLS functions and parameters are desupported:

`Least_UBOUND`. Use `OLS_GREATEST_LBOUND` instead.
`LUBD`. Use `OLS_GLBD` instead.
`DOMINATES`. Use the `OLS_DOMINATES` standalone function instead.
`DOM`. Use the `OLS_STRICTLY_DOMINATES` standalone function instead.
`STRICTLY_DOMINATES`. Use the `OLS_STRICTLY_DOMINATES` standalone function instead.
`S_DOM`. Use the `OLS_STRICTLY_DOMINATES` standalone function instead.
`DOMINATED_BY`. Use the `OLS_DOMINATED_BY` standalone function instead.
`DOM_BY`. Use the `OLS_DOMINATED_BY` standalone function instead.
`STRICTLY_DOMINATED_BY`. Use the OLS_STRICTLY_DOMINATED_BY standalone function instead.
`S_DOM_BY`. Use the `OLS_STRICTLY_DOMINATED_BY` standalone function instead.

Also, the OLS standalone function `SA_UTL.DOMINATES` boolean datatype is desupported. The `SA_UTL.DOMINATES` function that uses the `NUMBER` datatype is not deprecated.

For reference about alternatives see: [Oracle Label Security Administrator's Guide Deprecated Features](https://docs.oracle.com/database/121/OLSAG/release_changes.htm#GUID-8772D3A3-E733-42A4-9E1B-DD9408352CE4)

**Parent topic:** Desupported Parameters in Oracle Database 23ai

##### ENCRYPTION_WALLET_LOCATION Parameter Desupported

Starting with Oracle Database 23ai, the parameter `ENCRYPTION_WALLET_LOCATION` is desupported.

Date: April 2023

To store and retrieve the TDE wallet, use the `WALLET_ROOT` structure (introduced with Oracle Database 18c).

**Note:**

If Transparent Data Encryption (TDE) is enabled, but WALLET_ROOT is not configured, then you will be blocked from upgrading to Oracle Database 23ai. This block for upgrades of databases using TDE is to prevent the possibility of not being able to open the database after the upgrade.

**Parent topic:** Desupported Parameters in Oracle Database 23ai

##### ADD_SSLV3_TO_DEFAULT SQLNET.ORA Parameter (and SSLv3) Desupported

Starting with Oracle Database 23ai, the Secure Socket Layer v3 protocol (SSLv3) is no longer supported for database server-client connections, and the `sqlnet.ora` parameter `ADD_SSLV3_TO_DEFAULT` has been removed.

Date: April 2023

SSLv3 is a much less secure protocol to secure the database server-to-client connection. Instead of using SSLv3, allow the database server and client to negotiate the most secure protocol that is common between the server and the client. Oracle Database 23ai provides TLS 1.2 and TLS 1.3 protocols for certificate-based network encryption.

**Parent topic:** Desupported Parameters in Oracle Database 23ai

##### Desupport of OPTIMIZER_SECURE_VIEW_MERGING Parameter

Oracle is desupporting the initialization parameter `OPTIMIZER_SECURE_VIEW_MERGING` in Oracle Database 23ai

April 2024

The `init.ora` parameter `OPTIMIZER_SECURE_VIEW_MERGING` enabled the optimizer to use view merging without performing the checks that would otherwise be performed to ensure that view merging does not violate any security intentions of the view creator. There is no replacement for this parameter. If you need to use this parameter, then contact Oracle Support.

**Parent topic:** Desupported Parameters in Oracle Database 23ai

#### Deprecated Features in Oracle Database 23ai

As part of your upgrade plan, review the features that are deprecated in this Oracle Database release, and review alternatives for your application strategies.

- PROXY_ONLY_CONNECT Deprecation
  The ability to set a schema to `PROXY_ONLY_CONNECT` is deprecated in Oracle Database 23ai.
- Oracle Database 11g SHA-1 Verifier Deprecated
  Starting with Oracle Database 23ai, the SHA-1 verifier introduced with Oracle Database 11g is deprecated.
- RADIUS API Based on RFC-2138 is Deprecated
  Starting with Oracle Database 23ai, the older RADIUS API that is based on Request for Comments (RFC) 2138 is deprecated.
- Enterprise User Security (EUS) Deprecated
  Enterprise User Security (EUS) is deprecated with Oracle Database 23ai.
- Auto-Login Wallet Version 6 Deprecated
  Oracle has introduced a new auto-login wallet version (7) with Oracle Database 23ai. Version 6 of the Oracle local auto-login wallet is deprecated.
- WALLET_LOCATION Parameter Deprecated
  The parameter `WALLET_LOCATION` is deprecated for use with Oracle Database 23ai for the Oracle Database server. It is not deprecated for use with the Oracle Database client or listener.
- RAS Mid-Tier Session Support for Fusion Middleware Deprecated
  Oracle Real Application Security (RAS) mid-tier master session support for Fusion Middleware application session service is deprecated with Oracle Database 23ai
- Oracle Data Provider for .NET, Unmanaged Driver Deprecation
  Oracle Data Provider for .NET (ODP.NET), Unmanaged Driver is deprecated in Oracle Database 23ai.
- GOST and SEED Algorithms Deprecation
  Starting with Oracle Database 23ai, the Transparent Data Encryption (TDE) decryption libraries for the GOST and SEED algorithms are deprecated, and encryption to GOST and SEED are desupported.
- Oracle Persistent Memory Deprecation
  Oracle Persistent Memory Database (PMEM) is deprecated as of Oracle Database 23ai due to Intel discontinuing Optane Persistent Memory hardware.
- PMEM Support in Oracle Memory Speed File System Deprecation
  Oracle Memory Speed (OMS) File System is deprecated in Oracle Database 23ai for use with Intel Optane Persistent Memory.
- Service Name with Partial DN Matching and Server-only Certificate Check Deprecation
  Starting with Oracle Database 23ai, matching (partial and full) is not limited to the database server certificate. The listener certificate is also checked, and the `SERVICE_NAME` parameter is ignored for partial DN matching.
- Deprecation of the mkstore Command-Line Utility
  The `mkstore` wallet management command line tool is deprecated with Oracle Database 23ai, and can be removed in a future release.
- Network Data Model (NDM) XML API Deprecation
  The Network Data Model (NDM) XML API used by the NDM feature of Oracle Spatial is deprecated in Oracle Database Release 23ai.
- Two Subprograms in SDO_GEOR_ADMIN Package Deprecation
  The GeoRaster subprograms `SDO_GEOR_ADMIN.isUpgradeNeeded` and `SDO_GEOR_ADMIN.upgradeGeoRaster` in `SDO_GEOR_ADMIN` package, which are used to maintain the GeoRaster objects in the database, are deprecated in Oracle Database Release 23ai.
- SDO_GEOR.importFrom and SDO_GEOR.exportTo subprograms in SDO_GEOR Package Deprecations
  The GeoRaster subprograms `SDO_GEOR.importFrom` and `SDO_GEOR.exportTo` in the `SDO_GEOR` package are deprecated in Oracle Database Release 23ai.
- WAIT Option of Oracle Data Guard SWITCHOVER Command
  Starting with Oracle Database 23ai, the `WAIT` option of the Oracle Data Guard `SWITCHOVER` command is deprecated.
- DBMS_RESULT_CACHE Function Name Deprecations
  Oracle is changing the names of several DBMS_RESULT_CACHE function names in Oracle Database 23ai.
- Oracle ACFS Snapshot Remastering Deprecation
  Starting with Oracle Database Release 23ai, the Snapshot Remastering feature of Oracle Advanced Cluster File System (ACFS) is deprecated.
- Oracle ACFS Compression Deprecation
  The ACFS compression feature of Oracle Advanced Cluster File System (ACFS) is deprecated in Oracle Database 23ai.
- Oracle Virtual Directory with Real Application Security Deprecation
  The use of Oracle Virtual Directory with Oracle Real Application Security is deprecated with Oracle Database 23ai.
- BIG_IO Attribute in Oracle Text Deprecation
  The `BIG_IO` attribute of the `CONTEXT` indextype is deprecated with Oracle Database 23ai, and can be disabled or removed in a future release.
- ASYNCHRONOUS_UPDATE in Oracle Text Deprecation
  The `ASYNCHRONOUS_UPDATE` setting of the `CONTEXT` indextype is deprecated in Oracle Database 23ai, and can be ignored or removed in a future release.
- Oracle Text CTXCAT Indextype Deprecation
  The Oracle Text indextype `CTXCAT` is deprecated with Oracle Database 23ai. The indextype itself, and it's operator `CTXCAT`, can be removed in a future release.
- Oracle XML DB Repository Deprecation
  The Oracle XML DB Repository is deprecated with Oracle Database 23ai.
- DBMS_XMLGEN Deprecation
  The PL/SQL package `DBMS_XMLGEN` is deprecated in Oracle Database 23ai.
- DBMS_XMLSTORE Deprecation
  The PL/SQL package `DBMS_XMLSTORE` is deprecated in Oracle Database 23ai.
- Deprecation of Unstructured XML Indexes
  Unstructured XML indexes are deprecated in Oracle Database 23ai.
- DBMS_HANG_MANAGER Package Deprecation
  The `DBMS_HANG_MANAGER` package is deprecated in Oracle Database 23ai. Use `DBMS_BLOCKER_RESOLVER` instead.
- Zero Downtime Upgrade (ZDU) Deprecation
  The Zero Downtime Upgrade (ZDU) feature of Oracle Fleet Patching and Provisioning (FPP) is deprecated in Oracle Database 23ai. 
- Highly Available Grid Naming Service (GNS) Deprecation
  The Highly Available Grid Naming Service feature of Grid Naming Service (GNS) in Oracle Grid Infrastructure is deprecated in Oracle Database 23ai. 
- Traditional Auditing Packages and Functions Deprecated
  Traditional auditing packages and functions are deprecated in Oracle Database 23ai. 
- MDSYS-Owned RDF Graph Networks Deprecated
  Creation of RDF graph networks in the MDSYS schema is deprecated.  Oracle recommends that you create RDF graph networks in a user schema, which was enabled in Oracle Database 19c.
- TREAT (expr AS JSON) Deprecated
  The operator `TREAT (expr AS JSON)` is deprecated, because SQL data type JSON is now available. 
- Deprecation of Out-of-Place Patching with Opatch and OPatchAuto
  The use of OPatch and OPatchAuto for out-of-place patching continues to be deprecated. 
- RCONFIG Utility Deprecation
  Starting with Oracle Database 23ai, the `RCONFIG` utility is deprecated.
- UPDATE_SDATA API Deprecation
  The `UPDATE_SDATA` API in Oracle Text is deprecated in Oracle Database 23ai.
- Oracle JDBC-OCI Thick Driver Deprecation
  The Oracle JDBC Oracle Call Interface (OCI) Type 2 client driver (also known as a "thick" driver) is deprecated in Oracle Database 23ai.
- Deprecation of SQLJ
  Starting with Oracle Database 23ai, the SQLJ method of embedding SQL statements in Java code is deprecated.
- Oracle JDBC Proprietary BLOB/CLOB Open and Close Methods Deprecation
  The Oracle JDBC methods `open()`, `close()`, and `isClosed()` in `OracleBlob,` `OracleClob`, and `OracleBfile` are deprecated for removal in Oracle Database 23ai.
- Autonomous Heath Framework Scope (AHF Scope) Deprecated
  The Autonomous Health Framework Scope (AHF Scope) feature of Cluster Health Advisor (CHA) is deprecated in Oracle Database 23ai. 
- Oracle RAC Cross-Instance Deprecation
  The Oracle Real Application Clusters (Oracle RAC) cross-instance archival feature is deprecated.

**Parent topic:** Oracle Database 23ai Behavior Changes, Desupports, and Deprecations

##### PROXY_ONLY_CONNECT Deprecation

The ability to set a schema to `PROXY_ONLY_CONNECT` is deprecated in Oracle Database 23ai.

Date: April 2023

Setting a schema to be `PROXY_ONLY_CONNECT` is deprecated in this release, and can be desupported in a future release. Oracle recommends that you use `SCHEMA ONLY` user accounts instead of `PROXY_ONLY_CONNECT`. Schema-Only Accounts don't have passwords associated with the schema, so you can't directly log in to the schema, and passwords don't need to be rotated.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### Oracle Database 11g SHA-1 Verifier Deprecated

Starting with Oracle Database 23ai, the SHA-1 verifier introduced with Oracle Database 11g is deprecated.

Date: April 2023

The salted multi-round SHA-512 password hash (also known as "verifier") introduced with Oracle Database 12c provides enhanced security for your password. If 11g verifiers (`11G`) are still being used in your database, then Oracle recommends resetting them so they can be upgraded to the 12c (`12C`) de-optimized `PBKDF2`-based verifier.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### RADIUS API Based on RFC-2138 is Deprecated

Starting with Oracle Database 23ai, the older RADIUS API that is based on Request for Comments (RFC) 2138 is deprecated.

Oracle Database 23ai introduces an updated RADIUS API based on RFC 6613 and RFC 6614. Oracle recommends that you start planning on migrating to use the new RADIUS API as soon as possible. The new API is enabled by default. These parameters associated with the older RADIUS API are also deprecated: `SQLNET.RADIUS_ALTERNATE`, `SQLNET.RADIUS_ALTERNATE_PORT`, `SQLNET.RADIUS_AUTHENTICATION`, and `SQLNET.RADIUS_AUTHENTICATION_PORT`. Refer to the Radius API documentation for information on changing the default to use the older RADIUS API.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### Enterprise User Security (EUS) Deprecated

Enterprise User Security (EUS) is deprecated with Oracle Database 23ai.

Oracle recommends that you migrate to using Centrally Managed Users (CMU). This feature enables you to directly connect with Microsoft Active Directory without an intervening directory service for enterprise user authentication and authorization to the database. If your Oracle Database is in the cloud, you can also choose to move to one of the newer integrations with a cloud identity provider.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### Auto-Login Wallet Version 6 Deprecated

Oracle has introduced a new auto-login wallet version (7) with Oracle Database 23ai. Version 6 of the Oracle local auto-login wallet is deprecated.

Date: April 2023

You can update your local auto-login wallet by modifying it with `orapki`.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### WALLET_LOCATION Parameter Deprecated

The parameter `WALLET_LOCATION` is deprecated for use with Oracle Database 23ai for the Oracle Database server. It is not deprecated for use with the Oracle Database client or listener.

Date: April 2023

For Oracle Database server, Oracle recommends that you use the `WALLET_ROOT` system parameter instead of using `WALLET_LOCATION`.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### RAS Mid-Tier Session Support for Fusion Middleware Deprecated

Oracle Real Application Security (RAS) mid-tier master session support for Fusion Middleware application session service is deprecated with Oracle Database 23ai

Date: April 2023

This filter created the RAS session automatically for the FMW application server. Starting with Oracle Database 23ai, you now need to write the code to create the RAS session in the future, just as you would be required to do for any other application server.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### Oracle Data Provider for .NET, Unmanaged Driver Deprecation

Oracle Data Provider for .NET (ODP.NET), Unmanaged Driver is deprecated in Oracle Database 23ai.

Date: April 2023

ODP.NET provides ADO.NET-based data access to Oracle Database. There are two primary Oracle data access drivers for Microsoft .NET Framework: ODP.NET, Managed Driver and ODP.NET, Unmanaged Driver. In Oracle Database 23ai, ODP.NET, Managed Driver supports all major features available in ODP.NET, Unmanaged Driver with the same application programming interfaces and configuration settings. Code migration from unmanaged ODP.NET to managed ODP.NET is straightforward for the vast majority of existing .NET applications. Oracle recommends that you migrate existing unmanaged ODP.NET applications to ODP.NET, Managed Driver. The ODP.NET, Unmanaged Driver can be desupported in a future release.

ODP.NET, Managed Driver is a more compact and simpler install that can be consumed via NuGet packaging. Unmanaged ODP.NET is not available as a NuGet package. It is easier to manage multiple managed ODP.NET deployments on the same machine than multiple unmanaged ODP.NET deployments. These advantages make managed ODP.NET preferable for customer use over unmanaged ODP.NET. Because unmanaged ODP.NET no longer has any advantages over managed ODP.NET, Oracle has chosen to deprecate unmanaged ODP.NET.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### GOST and SEED Algorithms Deprecation

Starting with Oracle Database 23ai, the Transparent Data Encryption (TDE) decryption libraries for the GOST and SEED algorithms are deprecated, and encryption to GOST and SEED are desupported.

Date: April 2023

GOST 28147-89 has been deprecated by the Russian government, and SEED has been deprecated by the South Korean government. If you need South Korean government-approved TDE cryptography, then use ARIA instead. If you are using GOST 28147-89, then you must decrypt and encrypt with another supported TDE algorithm. The decryption algorithms for GOST 28147-89 and SEED are included in Oracle Database 23ai, but are deprecated, and the GOST encryption algorithm is desupported with Oracle Database 23ai. If you are using GOST or SEED for TDE encryption, then Oracle recommends that you online re-key to another algorithm before upgrading to Oracle Database 23ai. However, with the exception of the HP Itanium platform, the GOST and SEED decryption libraries are available with Oracle Database 23ai, so you can also decrypt after upgrading.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### Oracle Persistent Memory Deprecation

Oracle Persistent Memory Database (PMEM) is deprecated as of Oracle Database 23ai due to Intel discontinuing Optane Persistent Memory hardware.

Date: April 2023

Intel has announced they will discontinue the Optane Persistent Memory product. Therefore, Oracle Persistent Memory Database is being deprecated.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### PMEM Support in Oracle Memory Speed File System Deprecation

Oracle Memory Speed (OMS) File System is deprecated in Oracle Database 23ai for use with Intel Optane Persistent Memory.

Date: April 2023

Intel has announced they will discontinue the Optane Persistent Memory product. Therefore, use of Oracle Memory Speed (OMS) File System is being deprecated.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### Service Name with Partial DN Matching and Server-only Certificate Check Deprecation

Starting with Oracle Database 23ai, matching (partial and full) is not limited to the database server certificate. The listener certificate is also checked, and the `SERVICE_NAME` parameter is ignored for partial DN matching.

Date: April 2023

Server-side certificate verification through distinguished name (DN) is changed as follows: Both the listener certificate and the database server certificate are checked. In earlier Oracle Database releases, only the database server certificate was checked. In most production cases, the same certificate is used by the listener and the database. In cases where different certificates are used, DN matching can require new certificates to allow partial DN matching on SAN or hostname certificate information. In addition to checking the listener certificate, when using partial DN matching is used, the `SERVICE_NAME` parameter will be ignored Only the hostname connect string parameter will be checked against the certificate common name (CN) and subject alternate name (SAN) fields. To revert to the behavior in earlier releases (using the service name in addition to hostname, and only checking the database server certificate), set the new parameter: `SSL_ALLOW_WEAK_DN_MATCH=TRUE`. The default is `FALSE`.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### Deprecation of the mkstore Command-Line Utility

The `mkstore` wallet management command line tool is deprecated with Oracle Database 23ai, and can be removed in a future release.

Date: April 2023

To manage wallets, Oracle recommends that you use the `orapki` command line tool.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### Network Data Model (NDM) XML API Deprecation

The Network Data Model (NDM) XML API used by the NDM feature of Oracle Spatial is deprecated in Oracle Database Release 23ai.

Date: April 2023

To efficiently and securely implement your customized network analysis, Oracle Spatial is deprecating the NDM XML API. Instead, use the Load On Demand (LOD) API. The LOD API provides customization interfaces that allow you to easily and securely implement your customization. In addition, you can also use the NDM Contraction Hierarchies REST API for high performance network analysis.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### Two Subprograms in SDO_GEOR_ADMIN Package Deprecation

The GeoRaster subprograms `SDO_GEOR_ADMIN.isUpgradeNeeded` and `SDO_GEOR_ADMIN.upgradeGeoRaster` in `SDO_GEOR_ADMIN` package, which are used to maintain the GeoRaster objects in the database, are deprecated in Oracle Database Release 23ai.

Date: April 2023

As the size of the GeoRaster database increases, the performance of the `SDO_GEOR_ADMIN.isUpgradeNeeded` and `SDO_GEOR_ADMIN.upgradeGeoRaster` subprograms are not efficient. Instead, Oracle recommends that you use alternative subprograms, such as `SDO_GEOR_ADMIN.checkSysdataEntries`, `SDO_GEOR_ADMIN.maintainSysdataEntries` and a few other subprograms to maintain the GeoRaster objects and their system data in Oracle Database.

Detailed instructions on how to run the alternative subprograms to maintain GeoRaster databases are available in Oracle Spatial Spatial GeoRaster Developer's Guide.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### SDO_GEOR.importFrom and SDO_GEOR.exportTo subprograms in SDO_GEOR Package Deprecations

The GeoRaster subprograms `SDO_GEOR.importFrom` and `SDO_GEOR.exportTo` in the `SDO_GEOR` package are deprecated in Oracle Database Release 23ai.

Date: April 2023

The `SDO_GEOR.importFrom` and `SDO_GEOR.exportTo` subprograms support very small images stored in a few general image file formats. They are limited by many usage restrictions, by low performance, and they are not supported in Oracle Autonomous Database. To load and export image and raster files, Oracle recommends that you replace these deprecated subprograms with alternative options, such as the SDO_GEOR_GDAL.translate subprogram, GDAL, or the GDAL-Based GeoRaster ETL . These options support various geospatial images in more than 100 formats without many restrictions, and have much greater performance and scalability.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### WAIT Option of Oracle Data Guard SWITCHOVER Command

Starting with Oracle Database 23ai, the `WAIT` option of the Oracle Data Guard `SWITCHOVER` command is deprecated.

Date: April 2023

In Oracle Database 21c, Oracle introduced a new Oracle Data Guard property, `DrainTimeout`, which overrides the default for `drain_timeout` of database services registered in Oracle Clusterware when a `SWITCHOVER` is issued. The Oracle Data Guard `WAIT` option in the `SWITCHOVER` command is now redundant. Oracle recommends the new `DrainTimeout` property.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### DBMS_RESULT_CACHE Function Name Deprecations

Oracle is changing the names of several DBMS_RESULT_CACHE function names in Oracle Database 23ai.

Date: April 2023

The following functions and procedures are deprecated:

- `BLACK_LIST` function. Use `BLOCK_LIST` function.
- BLACK_LIST_ADD procedure. Use BLOCK_LIST_ADD procedure.
- BLACK_LIST_CLEAR procedure. Use BLOCK_LIST_CLEAR procedure
- BLACK_LIST_REMOVE procedure. Use BLOCK_LIST_REMOVE procedure
- OBJECT_BLACK_LIST function. Use OBJECT_BLOCK_LIST function
- OBJECT_BLACK_LIST_ADD procedure. Use OBJECT_BLOCK_LIST_ADD procedure.
- OBJECT_BLACK_LIST_CLEAR procedure. Use OBJECT BLOCK LIST_CLEAR procedure.
- OBJECT_BLACK_LIST_REMOVE procedure. Use OBJECT_BLOCK_LIST_REMOVE procedure.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### Oracle ACFS Snapshot Remastering Deprecation

Starting with Oracle Database Release 23ai, the Snapshot Remastering feature of Oracle Advanced Cluster File System (ACFS) is deprecated.

Date: April 2023

This feature can be desupported in a future release without replacement. Desupporting features with limited adoption enables Oracle to focus on improving core scaling, availability, and manageability.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### Oracle ACFS Compression Deprecation

The ACFS compression feature of Oracle Advanced Cluster File System (ACFS) is deprecated in Oracle Database 23ai.

Date: April 2023

This feature can be desupported in a future release without replacement. Desupporting features with limited adoption enables Oracle to focus on improving core scaling, availability, and manageability.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### Oracle Virtual Directory with Real Application Security Deprecation

The use of Oracle Virtual Directory with Oracle Real Application Security is deprecated with Oracle Database 23ai.

Date: July 2023

Using OVD with Oracle Real Application Security is deprecated, because OVD is no longer updated as a separate product

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### BIG_IO Attribute in Oracle Text Deprecation

The `BIG_IO` attribute of the `CONTEXT` indextype is deprecated with Oracle Database 23ai, and can be disabled or removed in a future release.

Date: July 2023

Oracle recommends that you allow this value to be set to its default value of `N`. `BIG_IO` was introduced to reduce the cost of seeks when index postings exceeded 4KB in length. However, the internal code is relatively inefficient, and the attribute cannot be combined with newer index options. Seek cost is much less relevant for solid state disks or non-volatile memory devices (NVMe), and seek cost is irrelevant when postings are cached. This setting is therefore of little benefit for most indexes.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### ASYNCHRONOUS_UPDATE in Oracle Text Deprecation

The `ASYNCHRONOUS_UPDATE` setting of the `CONTEXT` indextype is deprecated in Oracle Database 23ai, and can be ignored or removed in a future release.

Date: July 2023

Oracle can ignore or remove this attribute in a future release. Oracle recommends that you allow this value to be set to its default value, `SYNCHRONOUS_UPDATE`. To avoid unexpected loss of results during updates, use `SYNC (ON COMMIT)` or `SYNC(EVERY [``time-period``])` with a short time period.

The `ASYNCHRONOUS_UPDATE` setting was introduced as a workaround for the fact that updates are implemented as "delete followed by insert," and that deletes are immediate (on commit), while inserts are only performed during an index sync. However, this setting is incompatible with several other index options. Oracle recommends that you discontinue its use.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### Oracle Text CTXCAT Indextype Deprecation

The Oracle Text indextype `CTXCAT` is deprecated with Oracle Database 23ai. The indextype itself, and it's operator `CTXCAT`, can be removed in a future release.

Date: July 2023

Both `CTXCAT` and the use of `CTXCAT` grammar as an alternative grammar for `CONTEXT` queries is deprecated. Instead, Oracle recommends that you use the `CONTEXT` indextype, which can provide all the same functionality, except that it is not transactional. Near-transactional behavior in `CONTEXT` can be achieved by using `SYNC(ON COMMIT)` or, preferably, `SYNC(EVERY [``time-period``])` with a short time period.

`CTXCAT` was introduced when indexes were typically a few megabytes in size. Modern, large indexes, can be difficult to manage with `CTXCAT`. The addition of index sets to `CTXCAT` can be achieved more effectively by the use of `FILTER BY` and `ORDER BY` columns, or `SDATA`, or both, in the `CONTEXT` indextype. `CTXCAT` is therefore rarely an appropriate choice. Oracle recommends that you choose the more efficient `CONTEXT` indextype.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### Oracle XML DB Repository Deprecation

The Oracle XML DB Repository is deprecated with Oracle Database 23ai.

Date: July 2023

Oracle recommends that you replace any functionality used in XML DB Repository with alternative technologies. As a result of this deprecation, all XML DB Repository interfaces (for example Repository-specific Java classes `oracle.xdb.servlet`,` oracle.xdb.event`, and `oracle.xdb.spi`) are consequently deprecated as well.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### DBMS_XMLGEN Deprecation

The PL/SQL package `DBMS_XMLGEN` is deprecated in Oracle Database 23ai.

Date: July 2023

`DBMS_XMLGEN` is a non-standard Oracle-proprietary package that is provided to generate and convert XML documents from SQL queries or with PL/SQL. This package is deprecated, and can be desupported in a future release. Oracle recommends that you use SQL/XML operators to generate XML from relational columns instead. Using ANSI SQL/XML operators for any generation and modification of XML documents provides a standardized and future-proof way to work with XML documents.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### DBMS_XMLSTORE Deprecation

The PL/SQL package `DBMS_XMLSTORE` is deprecated in Oracle Database 23ai.

Date: July 2023

`DBMS_XMLSTORE` is a non-standard Oracle-proprietary package that enables you to store and manipulate XML data in Oracle Database. This package is deprecated, and can be desupported in a future release. Oracle recommends that you use regular SQL DML and with standard XQuery and SQL/XML to store and manage XML data. Using standard functionality provides future-proof way to store and manipulate XML data.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### Deprecation of Unstructured XML Indexes

Unstructured XML indexes are deprecated in Oracle Database 23ai.

Date: July 2023

Unstructured XML indexes are deprecated and superseded by XML search indexes. Oracle recommends that you use XML search indexes or structured XML indexes.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### DBMS_HANG_MANAGER Package Deprecation

The `DBMS_HANG_MANAGER` package is deprecated in Oracle Database 23ai. Use `DBMS_BLOCKER_RESOLVER` instead.

Date: July 2023

The `DBMS_HANG_MANAGER` package provides a method of changing some configuration parameters and constraints to address session issues. This package is being replaced with `DBMS_BLOCKER_RESOLVER`. `DBMS_HANG_MANAGER` can be removed in a future release.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### Zero Downtime Upgrade (ZDU) Deprecation

The Zero Downtime Upgrade (ZDU) feature of Oracle Fleet Patching and Provisioning (FPP) is deprecated in Oracle Database 23ai. 

Date: July 2023

ZDU uses either Transient Logical Standby or Oracle GoldenGate classic. However, Transient Logical Standby does not support the latest data types, and the Oracle GoldenGate classic implementation is deprecated. Instead of ZDU, Oracle recommends that you use FPP in combination with the `DBMS_ROLLING` PL/SQL package: You can use FPP for the provisioning and deployment of new Oracle homes, and you can use `DBMS_ROLLING` as a streamlined method of performing rolling upgrades.

The `DBMS_ROLLING` package is closely integrated with Application Continuity to help to minimize disruptions in the database tier, and mask rolling patching activities.

**Related Topics**

- [Using DBMS_ROLLING to Perform a Rolling Upgrade](../sbydb/using-DBMS_ROLLING-to-perform-rolling-upgrade.md)

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### Highly Available Grid Naming Service (GNS) Deprecation

The Highly Available Grid Naming Service feature of Grid Naming Service (GNS) in Oracle Grid Infrastructure is deprecated in Oracle Database 23ai. 

Date: December 2023

The highly-available GNS provides the ability to run multiple GNS instances in a multi-cluster environment with different roles. This feature is being deprecated. There is no replacement.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### Traditional Auditing Packages and Functions Deprecated

Traditional auditing packages and functions are deprecated in Oracle Database 23ai. 

Date: September 2023

With the desupport of traditional auditing, the PL/SQL packages and functions associated with traditional auditing are deprecated, This deprecation includes the packages and functions `INIT_CLEANUP`, `DEINIT_CLEANUP`, and `IS_CLEANUP_INITIALIZED`. While these packages or functions continue to operate in Oracle Database 23ai, you can neither add to or modify traditional auditing configurations.  

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### MDSYS-Owned RDF Graph Networks Deprecated

Creation of RDF graph networks in the MDSYS schema is deprecated.  Oracle recommends that you create RDF graph networks in a user schema, which was enabled in Oracle Database 19c.

Date: November 2023

An RDF graph network is a logical structure a developer creates to contain multiple RDF graphs. Starting with Oracle Database 19c, RDF graph networks can be created in a user schema. It is simpler for developers to create RDF graph networks in a user schema, and this method makes it easier to share graphs with other user schemas.  Creating RDF graph networks in user schemas is also more secure, as developers can create RDF graph networks without requiring DBA privileges.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### TREAT (expr AS JSON) Deprecated

The operator `TREAT (expr AS JSON)` is deprecated, because SQL data type JSON is now available. 

Date: November 2023

The `TREAT(expr as JSON)` functionality is no longer needed, as this function is replaced with the JSON constructor. For this reason, Oracle is deprecating the `TREAT AS JSON` operator in Oracle Database 23ai. 

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### Deprecation of Out-of-Place Patching with Opatch and OPatchAuto

The use of OPatch and OPatchAuto for out-of-place patching continues to be deprecated. 

Date: December 2023

For patching in Oracle Database 23ai, Oracle recommends that you use out-of-place patching using Gold images to apply quarterly release updates (RUs). This deprecation does not affect in-place patching. If you want to perform in-place patching, then OPatch and OPatchAuto continue to be available for this purpose. The Oracle Database 23ai Free release is not supported for patching with RUs.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### RCONFIG Utility Deprecation

Starting with Oracle Database 23ai, the `RCONFIG` utility is deprecated.

Date: January 2024

Oracle recommends that you use Database Configuration Assistant (DBCA). Beginning with Oracle Enterprise Manager 13c Release 5 Update 23 (13.5.0.23), converting a single-instance database to Oracle RAC through Oracle Enterprise Manager using the `RCONFIG` utility is no longer supported.

**Related Topics**

- [Converting Single-Instance Oracle Databases to Oracle RAC and Oracle RAC One Node](../racad/converting-single-instance-oracle-databases-to-oracle-rac-and-oracle-rac-one-node.md)

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### UPDATE_SDATA API Deprecation

The `UPDATE_SDATA` API in Oracle Text is deprecated in Oracle Database 23ai.

Date: February 2024

Instead of modifying the index, Oracle recommends that you update the underlying data.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### Oracle JDBC-OCI Thick Driver Deprecation

The Oracle JDBC Oracle Call Interface (OCI) Type 2 client driver (also known as a "thick" driver) is deprecated in Oracle Database 23ai.

Date: May 2024

Most Java applications that use Open Database Connectivity (ODBC) with Oracle JDBC drivers use the Thin driver. To enable Oracle to allocate resources to better address customer requirements, Oracle is deprecating the JDBC-OCI driver.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### Deprecation of SQLJ

Starting with Oracle Database 23ai, the SQLJ method of embedding SQL statements in Java code is deprecated.

Date: May 2024

In place of SQLJ, Oracle recommends that you directly use the Java Database Connectivity (JDBC) APIs (dynamic SQL, prepared statements or PL/SQL blocks).

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### Oracle JDBC Proprietary BLOB/CLOB Open and Close Methods Deprecation

The Oracle JDBC methods `open()`, `close()`, and `isClosed()` in `OracleBlob,` `OracleClob`, and `OracleBfile` are deprecated for removal in Oracle Database 23ai.

Date: July 2024

Oracle is deprecating these methods, which are replaced with `openLob()`, `closeLob()` and `isClosedLob()`. The method `close()` conflicts with the interface type `java.lang.Autocloseable`. Removing the proprietary method `close()` makes it possible for `java.lang OracleBlob`, `java.lang.OracleClob`, and `java.lang.OracleBfile` to extend the Autocloseable interface at some future time. The `open()` and `isClosed()` methods will be removed and replaced in a future release to maintain rational names for these methods.

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### Autonomous Heath Framework Scope (AHF Scope) Deprecated

The Autonomous Health Framework Scope (AHF Scope) feature of Cluster Health Advisor (CHA) is deprecated in Oracle Database 23ai. 

Date: April 2025

To enable Oracle to allocate resources to better address customer requirements, Oracle is discontinuing AHF Scope. In its place, Oracle recommends that you use Autonomous Health Framework Insights (AHF Insights).

**Parent topic:** Deprecated Features in Oracle Database 23ai

##### Oracle RAC Cross-Instance Deprecation

The Oracle Real Application Clusters (Oracle RAC) cross-instance archival feature is deprecated.

Date: April 2025

Cross-instance archival allowed archive logs to be shipped between instances of the same database in configurations without shared storage for the recovery area. Local archive log destinations in Oracle RAC are only supported on shared storage. Therefore, there will be no replacement for this feature.

**Parent topic:** Deprecated Features in Oracle Database 23ai

#### Deprecated Views in Oracle Database 23ai

As part of your upgrade plan, review the views that are deprecated starting with this Oracle Database release.

- V\$DATABASE.FS_FAILOVER Columns in V\$DATABASE View Deprecated
  Starting with Oracle Database 23ai, all `V$DATABASE.FS_FAILOVER` columns in the `V$DATABASE` view are deprecated. Use the `V$FAST_START_FAILOVER_CONFIG` view.
- V\$PQ_SLAVE View Deprecation
  Oracle is replacing the view `V$PQ_SLAVE` with `V$PX_SERVER` in Oracle Database 23ai.
- V\$FS_FAILOVER_STATS View Deprecation
  The view `V$FS_FAILOVER_STATS` is deprecated and replaced by the view `V$DG_BROKER_ROLE_CHANGE` in Oracle Database 23ai.
- DBA_HANG_MANAGER_PARAMETERS Data Dictionary View Deprecation
  The `DBA_HANG_MANAGER_PARAMETERS` static Data Dictionary view is deprecated with Oracle Database 23ai. Use `DBA_BLOCKER_RESOLVER_PARAMETERS` instead.
- V\$RECOVERY_SLAVE View Deprecation
  Oracle is replacing the view `V$RECOVERY_SLAVE` with `V$RECOVERY_WORKER` in Oracle Database 23ai.

**Parent topic:** Oracle Database 23ai Behavior Changes, Desupports, and Deprecations

##### V\$DATABASE.FS_FAILOVER Columns in V\$DATABASE View Deprecated

Starting with Oracle Database 23ai, all `V$DATABASE.FS_FAILOVER` columns in the `V$DATABASE` view are deprecated. Use the `V$FAST_START_FAILOVER_CONFIG` view.

Date: April 2023

Oracle is introducing the `V$FAST_START_FAILOVER_CONFIG` view, which contains configuration details about the Oracle Data Guard fast-start failover feature. As a result, the `FS_FAILOVER_*` columns in the `V$DATABASE` view are deprecated. Instead, use the corresponding columns in the `V$FAST_START_FAILOVER_CONFIG` view.

The column replacements are as follows:

- `V$DATABASE.FS_FAILOVER_MODE`: Replace with `V$FAST_START_FAILOVER_CONFIG.FAST_START_FAILOVER_MODE`
- `V$DATABASE.FS_FAILOVER_STATUS`: Replace with `V$FAST_START_FAILOVER_CONFIG.STATUS`
- `V$DATABASE.FS_FAILOVER_CURRENT_TARGET`: Replace with `V$FAST_START_FAILOVER_CONFIG.CURRENT_TARGET `
- `V$DATABASE.FS_FAILOVER_THRESHOLD`: Replace with `V$FAST_START_FAILOVER_CONFIG.THRESHOLD`
- `V$DATABASE.FS_FAILOVER_OBSERVER_PRESENT`: Replace with `V$FAST_START_FAILOVER_CONFIG.OBSERVER_PRESENT`
- `V$DATABASE.FS_FAILOVER_OBSERVER_HOST`: Replace with `V$FAST_START_FAILOVER_CONFIG.OBSERVER_HOST `

**Parent topic:** Deprecated Views in Oracle Database 23ai

##### V\$PQ_SLAVE View Deprecation

Oracle is replacing the view `V$PQ_SLAVE` with `V$PX_SERVER` in Oracle Database 23ai.

Date: April 2023

Use `V$PX_SERVER` in place of `V$PQ_SLAVE`.

**Parent topic:** Deprecated Views in Oracle Database 23ai

##### V\$FS_FAILOVER_STATS View Deprecation

The view `V$FS_FAILOVER_STATS` is deprecated and replaced by the view `V$DG_BROKER_ROLE_CHANGE` in Oracle Database 23ai.

Date: April 2023

The view `V$FS_FAILOVER_STATS` displayed one row with limited information about the last fast-start failover that occurred. The data was available in the primary database only, and was not persisted across database restarts. The new view `V$DG_BROKER_ROLE_CHANGE` contains detailed information about the last ten role changes, including switchover, failover, and reinstate, across the Data Guard broker configuration, and provides richer information than the deprecated view `V$FS_FAILOVER_STATS`.

**Parent topic:** Deprecated Views in Oracle Database 23ai

##### DBA_HANG_MANAGER_PARAMETERS Data Dictionary View Deprecation

The `DBA_HANG_MANAGER_PARAMETERS` static Data Dictionary view is deprecated with Oracle Database 23ai. Use `DBA_BLOCKER_RESOLVER_PARAMETERS` instead.

Date: July 2023

The `DBA_HANG_MANAGER_PARAMETERS` static Data Dictionary view shows the available user-tunable `DBMS_BLOCKER_RESOLVER` parameters and values, formerly available as `DBA_HANG_MANAGER_PARAMETERS`. This view is being replaced with `DBA_BLOCKER_RESOLVER_PARAMETERS`. `DBA_HANG_MANAGER_PARAMETERS` can be removed in a future release.

**Parent topic:** Deprecated Views in Oracle Database 23ai

##### V\$RECOVERY_SLAVE View Deprecation

Oracle is replacing the view `V$RECOVERY_SLAVE` with `V$RECOVERY_WORKER` in Oracle Database 23ai.

Date: August 2023

Use `V$RECOVERY_WORKER` in place of `V$RECOVERY_SLAVE`.

**Parent topic:** Deprecated Views in Oracle Database 23ai

#### Deprecated Parameters in Oracle Database 23ai

As part of your upgrade plan, review the initialization parameters listed here that are deprecated starting with this Oracle Database release.

To obtain the current list of all deprecated parameters in your database release, run the following query in SQL\*Plus:

    SELECT name from v$parameter
             WHERE isdeprecated = 'TRUE' ORDER BY name;

- ENCRYPT_NEW_TABLESPACES Deprecation
  Starting with Oracle Database 23ai, the `ENCRYPT_NEW_TABLESPACES` initialization parameter is deprecated.
- ALLOW_MD5_CERTS and ALLOW_SHA1_CERTS sqlnet.ora Parameter Deprecation
  Starting in Oracle Database 23ai, the `ALLOW_MD5_CERTS` and `ALLOW_SHA1_CERTS` `sqlnet.ora` parameters are deprecated.
- MY_WALLET_DIRECTORY Connect String Deprecated
  The connect string parameter `MY_WALLET_DIRECTORY` has been deprecated with Oracle Database 23ai.
- FIPS Parameters Deprecated
  Starting with Oracle Database 23ai, several parameters associated with `FIPS_140` are deprecated.
- ONE_STEP_PLUGIN_FOR_PDB_WITH_TDE Initialization Parameter Deprecated
  The parameter `ONE_STEP_PLUGIN_FOR_PDB_WITH_TDE` is deprecated with Oracle Database 23ai.
- Traditional Audit Initialization Parameters Deprecated
  With the desupport of creating and modifying traditional audit policies with Oracle Database 23, the traditional audit parameters are deprecated.
- PRE_PAGE_SGA Initialization Parameter Deprecated
  Oracle is deprecating `PRE_PAGE_SGA` because it is obsolete. Setting the parameter typically provides little or no potential performance benefits, and can create problems.
- REMOTE_OS_ROLES Initialization Parameter Deprecated
  The `REMOTE_OS_ROLES` initialization parameter is deprecated in Oracle Database 23ai

**Parent topic:** Oracle Database 23ai Behavior Changes, Desupports, and Deprecations

##### ENCRYPT_NEW_TABLESPACES Deprecation

Starting with Oracle Database 23ai, the `ENCRYPT_NEW_TABLESPACES` initialization parameter is deprecated.

Date: April 2023

Oracle recommends that you use the initialization parameter `TABLESPACE_ENCRYPTION`, which is new for Oracle Database 23ai.

**Parent topic:** Deprecated Parameters in Oracle Database 23ai

##### ALLOW_MD5_CERTS and ALLOW_SHA1_CERTS sqlnet.ora Parameter Deprecation

Starting in Oracle Database 23ai, the `ALLOW_MD5_CERTS` and `ALLOW_SHA1_CERTS` `sqlnet.ora` parameters are deprecated.

Date: April 2023

Instead of these parameters, use the `ALLOWED_WEAK_CERT_ALGORITHMS` `sqlnet.ora` parameter, which is new with Oracle Database 23ai.

**Parent topic:** Deprecated Parameters in Oracle Database 23ai

##### MY_WALLET_DIRECTORY Connect String Deprecated

The connect string parameter `MY_WALLET_DIRECTORY` has been deprecated with Oracle Database 23ai.

Date: April 2023

Oracle recommends that you use `WALLET_LOCATION` in the connect string to override the `sqlnet.ora` `WALLET_LOCATION` setting. `WALLET_LOCATION` has been updated for connect strings so that the same parameter can be used in `sqlnet.ora` and in `tnsnames.ora` This change simplifies the parameters that you need to remember. Oracle recommends that you change your client connect strings to use `WALLET_LOCATION` instead of `MY_WALLET_DIRECTORY`.

**Parent topic:** Deprecated Parameters in Oracle Database 23ai

##### FIPS Parameters Deprecated

Starting with Oracle Database 23ai, several parameters associated with `FIPS_140` are deprecated.

Date: April 2023

`FIPS_140` in `FIPS.ORA` can be used to enable `FIPS` for all features starting with Oracle Database 23ai. The following FIPS parameters are deprecated:

- SQLNET.ORA: `FIPS_140` to enable FIPS for native network encryption
- FIPS.ORA: `SSLFIPS_140` to enable FIPS for TLS
- Initialization parameter: `DBFIPS_140` to enable FIPS for TDE and `DBMS_CRYPTO`

**Parent topic:** Deprecated Parameters in Oracle Database 23ai

##### ONE_STEP_PLUGIN_FOR_PDB_WITH_TDE Initialization Parameter Deprecated

The parameter `ONE_STEP_PLUGIN_FOR_PDB_WITH_TDE` is deprecated with Oracle Database 23ai.

Date: July 2023

`ONE_STEP_PLUGIN_FOR_PDB_WITH_TDE` enables you to clone remotely or to relocate encrypted PDBs without providing the Transparent Data Encryption (TDE) keystore password. However, `EXTERNAL STORE` provides the same functionality, and is universally applicable to all `ADMINISTER KEY MANAGEMENT` statements that do not change the TDE configuration. Instead of using `ONE_STEP_PLUGIN_FOR_PDB_WITH_TDE`, Oracle recommends that you use the `IDENTIFIED BY EXTERNAL STORE` clause for the `ADMINISTER KEY MANAGEMENT` statement.

**Parent topic:** Deprecated Parameters in Oracle Database 23ai

##### Traditional Audit Initialization Parameters Deprecated

With the desupport of creating and modifying traditional audit policies with Oracle Database 23, the traditional audit parameters are deprecated.

Date: July 2023

Traditional audit policies are available after upgrading, but the initialization parameters associated with those policies are deprecated. These deprecated parameters include the following:

- `AUDIT_TRAIL`
- `AUDIT_SYS_OPERATIONS`
- `AUDIT_FILE_DEST`
- `AUDIT_SYSLOG_LEVEL`

Oracle recommends that you migrate to unified auditing as soon as possible, because these traditional audit parameters can be removed in a future database release.

**Parent topic:** Deprecated Parameters in Oracle Database 23ai

##### PRE_PAGE_SGA Initialization Parameter Deprecated

Oracle is deprecating `PRE_PAGE_SGA` because it is obsolete. Setting the parameter typically provides little or no potential performance benefits, and can create problems.

Date: August 2023

The Oracle Database design for SGA packaging has evolved over time, so that process start-up effects on the SGA are initiated after instance startup, and there is little to no benefit in changing the value for `PRE_PAGE_SGA`. The only use case for this parameter is on Oracle Exadata systems, which should have `PRE_PAGE_SGA` set to `TRUE`.

**Parent topic:** Deprecated Parameters in Oracle Database 23ai

##### REMOTE_OS_ROLES Initialization Parameter Deprecated

The `REMOTE_OS_ROLES` initialization parameter is deprecated in Oracle Database 23ai

Date: January 2025

The `REMOTE_OS_ROLES` instructed the database to grant database roles based on the user’s operating system group information in the database client. This feature was particularly for use with the initialization parameter `REMOTE_OS_AUTHENT`, which was deprecated, and desupported with Oracle Database 21c. The Oracle Database client can no longer authenticate a user within Oracle Database. This initialization parameter accordingly no longer has a supported use case, and is now deprecated.

**Parent topic:** Deprecated Parameters in Oracle Database 23ai

### Oracle Database 21c Behavior Changes, Desupports, and Deprecations

Review for descriptions of Oracle Database 21c release changes.

- Behavior Changes for Oracle Database 21c Upgrade Planning
  Review these behavior changes to help plan for upgrades to Oracle Database 21c.
- Desupported Features in Oracle Database 21c
  As part of your upgrade plan, review the desupported features in this Oracle Database release.
- Desupported Views in Oracle Database 21c
  Review this list of desupported views for changes and replacements in view settings in this release.
- Desupported Initialization Parameters in Oracle Database 21c
  Review this list of desupported initialization parameters for changes and replacements in parameter settings in this release.
- Deprecated Features in Oracle Database 21c
  As part of your upgrade plan, review the features that are deprecated in this Oracle Database release, and review alternatives for your application strategies.
- Deprecated Views in Oracle Database 21c
  As part of your upgrade plan, review the views that are deprecated starting with this Oracle Database release.
- Deprecated Parameters in Oracle Database 21c
  As part of your upgrade plan, review the initialization parameters that are deprecated starting with this Oracle Database release.

**Parent topic:** Oracle Database Changes, Desupports, and Deprecations

#### Behavior Changes for Oracle Database 21c Upgrade Planning

Review these behavior changes to help plan for upgrades to Oracle Database 21c.

Behavior changes can include default changes for parameters or features, product name changes, and other changes to the database configuration that may require your attention.

- About Read-Only Oracle Homes in Oracle Database 21c
  Starting with Oracle Database 21c, an Oracle Database installation configures all Oracle Database homes in read-only mode by default.
- Multitenant Upgrades Only in Oracle Database 21c
  Starting with Oracle Database 21c, Oracle Database is only supported using the multitenant architecture.
- Logical Standby and New Data Types
  If you use logical standby (when not used as part of `DBMS_ROLLING`), then you can use only data types added before Oracle Database 12c Release 2 (12.2)
- Relocation of HR Sample Schema
  Starting with Oracle Database 21c, the HR sample schema no longer ships as part of Oracle Database.
- Manage DRCP on PDBs
  Starting with Oracle Database 21c, Database Resident Connection Pool (DRCP) can be configured and managed for individual PDBs.
- Oracle Advanced Cluster File System (Oracle ACFS) Name Change
  Starting with Oracle Database 21c, the name of Oracle Automatic Storage Management Cluster File System (Oracle ACFS) is changed to Oracle Advanced Cluster File System (Oracle ACFS).
- Windows Authentication No Longer Uses NTLM by Default
  For Microsoft Windows installations with `AUTHENTICATION_SERVICES=NTS`, in this Oracle Database release, the `SQLNET.NO_NTLM` parameter setting in the `sqlnet.ora` file defaults to `TRUE`, which can cause ORA-12638 errors.

**Parent topic:** Oracle Database 21c Behavior Changes, Desupports, and Deprecations

##### About Read-Only Oracle Homes in Oracle Database 21c

Starting with Oracle Database 21c, an Oracle Database installation configures all Oracle Database homes in read-only mode by default.

**Note:**

This description of read-only Oracle home installation describes the default in Oracle Database 21c, where the only available configuration was a read-only Oracle home, and a software-only Oracle Database installation was not an option.

A read-only Oracle Home simplifies provisioning by implementing separation of installation and configuration.

Before Oracle Database 21c, the default `ORACLE_HOME` layout combined `ORACLE_HOME`, `ORACLE_BASE_HOME` and `ORACLE_BASE_CONFIG` into a single location. Starting with Oracle Database 21c, the only available configuration is a read-only `ORACLE_HOME` where `ORACLE_BASE_HOME` and `ORACLE_BASE_CONFIG` are located separately from `ORACLE_HOME`.

In a read-only Oracle home, all the configuration data and log files reside outside of the read-only Oracle home.

Apart from the traditional `ORACLE_BASE` and `ORACLE_HOME` directories, the following directories contain files that used to be in `ORACLE_HOME`:

- `ORACLE_BASE_HOME`

- `ORACLE_BASE_CONFIG`

**Note:**

This feature does not affect how database administrators monitor, diagnose, and tune their system performance.

**Parent topic:** Behavior Changes for Oracle Database 21c Upgrade Planning

##### Multitenant Upgrades Only in Oracle Database 21c

Starting with Oracle Database 21c, Oracle Database is only supported using the multitenant architecture.

**Note:**

A multitenant container database is the only supported architecture in Oracle Database 21c and later releases. While the documentation is being revised, legacy terminology may persist. In most cases, "database" and "non-CDB" refer to a CDB or PDB, depending on context. In some contexts, such as upgrades, "non-CDB" refers to a non-CDB from a previous release.

**Parent topic:** Behavior Changes for Oracle Database 21c Upgrade Planning

##### Logical Standby and New Data Types

If you use logical standby (when not used as part of `DBMS_ROLLING`), then you can use only data types added before Oracle Database 12c Release 2 (12.2)

Date: May 2021

New data types added after Oracle Database 12c Release 1 (12.1) are not supported with Oracle Data Guard logical standby. For example, Oracle Data Guard logical standby does not support long identifiers, complex Abstract Data Types (ADTs), and spatial data types. Note that this limitation does not exist with an Oracle Data Guard physical standby database, `DBMS_ROLLING`, or Oracle GoldenGate. To obtain the benefits of a standby database with more recent data types, Oracle recommends that you consider using either a physical standby database, a snapshot standby database, or that you use the logical replication features of Oracle GoldenGate.

**Parent topic:** Behavior Changes for Oracle Database 21c Upgrade Planning

##### Relocation of HR Sample Schema

Starting with Oracle Database 21c, the HR sample schema no longer ships as part of Oracle Database.

To install the HR schema, refer to the section "Installing Sample Schemas" in Oracle Database Database Sample Schemas

**Related Topics**

- [Installation of Sample Schemas](../comsc/installing-sample-schemas.md)

**Parent topic:** Behavior Changes for Oracle Database 21c Upgrade Planning

##### Manage DRCP on PDBs

Starting with Oracle Database 21c, Database Resident Connection Pool (DRCP) can be configured and managed for individual PDBs.

When you choose to configure DRCP so that it is managed from individual PDBs, you can configure, manage, and monitor pools on individual pluggable databases (PDBs).

In previous releases, the DRCP pool was used by the entire container database (CDB). This feature eases the management of DRCP pool by changing the granularity of the DRCP pool from the entire CDB to a DRCP pool for individual PDBs. This change enables tenant administrators to configure and manage independent tenant-specific DRCP pools.

This feature is enabled by a new database parameter, `ENABLE_PER_PDB_DRCP`. By default the parameter is set to `ENABLE_PER_PDB_DRCP=FALSE`. If you set `ENABLE_PER_PDB_DRCP=TRUE`, then this feature is enabled.

When you upgrade a PDB to Oracle Database 21c, the default connection pool for the PDB is created in the PDB. If you then enable this feature with the initialization parameter, then instead of managing connection pooling at the CDB, the connection pool is managed locally by the PDB.

**Parent topic:** Behavior Changes for Oracle Database 21c Upgrade Planning

##### Oracle Advanced Cluster File System (Oracle ACFS) Name Change

Starting with Oracle Database 21c, the name of Oracle Automatic Storage Management Cluster File System (Oracle ACFS) is changed to Oracle Advanced Cluster File System (Oracle ACFS).

This change is only a change of the name. The basic function of Oracle's cluster file system continues to be the same. Oracle continues to develop and enhance Oracle ACFS.

**Parent topic:** Behavior Changes for Oracle Database 21c Upgrade Planning

##### Windows Authentication No Longer Uses NTLM by Default

For Microsoft Windows installations with `AUTHENTICATION_SERVICES=NTS`, in this Oracle Database release, the `SQLNET.NO_NTLM` parameter setting in the `sqlnet.ora` file defaults to `TRUE`, which can cause ORA-12638 errors.

In previous releases, the default for `SQLNET.NO_NTLM` was `FALSE`. `SQLNET.NO_NTLM` controls whether `NTLM` can be used with NTS authentication (`AUTHENTICATION_SERVICES=NTS`). A `TRUE` setting means that NTLM cannot be used in NTS authentication. Because NTLM does not normally provide mutual authentication and is hence less secure, a `TRUE` setting for `SQLNET.NO_NTLM` makes the database and client more secure.

The `SQLNET.NO_NTLM` parameter is used on both the server and the client. If you have upgraded a Microsoft Windows installation of Oracle Database, or upgraded a client in which `SQLNET.NO_NTLM` had not been set, then its default will be `TRUE`. In that case, when you have `SQLNET.AUTHENTICATION_SERVICES=NTS` in your `sqlnet.ora`, clients can encounter the error `ORA-12638: Credential retrieval failed`.

If you prefer to use NTLM authentication for certain clients, then set this parameter as required in client-side `sqlnet.ora` files:

    SQLNET.NO_NTLM=FALSE

You must include this setting on both the server and client, and this setting should be the same on both. Ideally, you should ensure that `SQLNET.NO_NTLM` is set to `TRUE`. However, if there is an authentication failure in `extproc`, a virtual account, or a local account on Windows, set the client `SQLNET.NO_NTLM` to `FALSE`, and then retry the login. If you change `SQLNET.NO_NTLM` on the server, then you must restart the database.

**Related Topics**

- [Guideline for Securing Authentication for Oracle Database Microsoft Windows Installations](../dbseg/index.md)
- [Upgrade Your Database Now - ORA-12638 on Windows only from Oracle 19.10.0 onwards](https://mikedietrichde.com/2021/03/10/ora-12638-on-windows-only-from-oracle-19-10-0-onwards/)
- [Windows : While Connect to Database Getting ORA-12638 After Applying Jan 2021 WINDBBP 19.10.0.0.210119 On Windows 64/32 Bit Database Client (Doc ID 2757734.1)](https://support.oracle.com/rs?type=doc&id=2757734.1)

**Parent topic:** Behavior Changes for Oracle Database 21c Upgrade Planning

#### Desupported Features in Oracle Database 21c

As part of your upgrade plan, review the desupported features in this Oracle Database release.

- Desupport of DBMS_OBFUSCATION_TOOLKIT Package
  Starting in Oracle Database 21c, the package `DBMS_OBFUSCATION_TOOLKIT` is desupported, and replaced with `DBMS_CRYPTO`.
- Desupport of Several XML Database (XDB) features
  Starting with Oracle Database 21c, several XML Database features are desupported.
- Desupport of DBMS_LOB.LOADFROMFILE and LOB Buffering
  Starting in Oracle Database 21c, the Large Object (LOB) features `DBMS_LOB.LOADFROMFILE` and LOB buffering are desupported.
- Desupport of Oracle Data Guard Broker Properties and Logical Standby
  Oracle Data Guard broker properties and logical standby properties whose functionality is replaced with the new EDIT … SET PARAMETER command in DGMGRL are now desupported.
- Desupport of DBMS_CRYPTO_TOOLKIT_TYPES and DBMS_CRYPTO_TOOLKIT
  Starting with Oracle Database 21c, the data types `DBMS_CRYPTO_TOOLKIT_TYPES` and package `DBMS_CRYPTO_TOOLKIT` are desupported.
- Desupport of Non-CDB Oracle Databases
  Starting with Oracle Database 21c, installation of non-CDB Oracle Database architecture is no longer supported.
- Desupport of Cluster Domain Member Clusters
  Effective with Oracle Grid Infrastructure 21c, Member Clusters, which are part of the Oracle Cluster Domain architecture, are desupported.
- Desupport of Unicode Collation Algorithm (UCA) 6.1 Collations
  Starting with Oracle Database 21c, the Unicode Collation Algorithm (UCA) 6.1 collations (`UCA0610_*`) are desupported. Use UCA 12.1 instead.
- Desupport of ACFS on Microsoft Windows
  Starting with Oracle Database 21c, the Oracle Grid Infrastructure feature Oracle Advanced Cluster File System (Oracle ACFS) is desupported with Microsoft Windows
- Desupport of Oracle ACFS Security (Vault) and ACFS Auditing
  Starting with Oracle Grid Infrastructure 21c, Oracle Advanced Cluster File System (ACFS) Security (Vault) and ACFS Auditing are desupported.
- Desupport of Oracle ACFS on Member Clusters (ACFS Remote)
  Starting with Oracle Grid Infrastructure 21c, Oracle Advanced Cluster File System (ACFS) on Member Clusters (ACFS Remote) is desupported.
- Desupport of ACFS Encryption on Solaris and Windows
  Starting with Oracle Database 21c, Oracle ACFS Encryption is desupported with no replacement on Oracle Solaris and Microsoft Windows.
- Desupport of ACFS Replication REPV1
  Starting with Oracle Database 21c, the Oracle ACFS replication protocol `repv1` is desupported.
- Desupport of Vendor Clusterware Integration with Oracle Clusterware
  Starting with Oracle Clusterware 21c, the integration of vendor or third party clusterware with Oracle Clusterware is desupported.
- Desupport of VERIFY_FUNCTION and VERIFY_FUNCTION_11G
  The `VERIFY_FUNCTION` and `VERIFY_FUNCTION_11G` password verify functions are desupported in Oracle Database 21c.
- Desupport of Deprecated Oracle Database Vault Roles
  The Oracle Database Vault roles `DV_PUBLIC`, `DV_REALM_OWNER`, and `DV_REALM_RESOURCE` are desupported in Oracle Database 21c.
- Desupport of Anonymous RC4 Cipher Suite
  The use of the anonymous RC4 cipher suite for non-authenticated TLS connections is desupported in Oracle Database 21c (`SSL_DH_anon_WITH_RC4_128_MD5`)
- Desupport of Adobe Flash-Based Oracle Enterprise Manager Express
  Flash-based Oracle EM Express is desupported in Oracle 21c. Use the JET-based Oracle EM Express, which is the default.
- Desupport of Intelligent Data Placement (IDP)
  Intelligent Data Placement (IDP) is desupported in Oracle Database 21c.
- Desupport of XML DB Content Connector
  Oracle XML DB Content Connector was deprecated in Oracle Database 12c Release 2. It is desupported and removed in Oracle Database 21c.
- Desupport of DBMS_XMLSAVE
  The PL/SQL package `DBMS_XMLSAVE` is desupported in Oracle Database 21c. Use `DBMS_XMLSTORE` instead.
- Desupport of DBMS_XMLQUERY
  The PL/SQL package `DBMS_XMLQUERY` is desupported in Oracle Database 21c. Use `DBMS_XMLGEN` instead.
- Desupport of FIPS Protect and Process Strength 0
  The protect and process strength 0 (RSA key length 512) equivalent is desupported for FIPS. This strength is still available for the non-FIPS mode.
- Desupport of PDB Flat File Dictionary Dumps
  The ability to create flat file dictionary dumps of pluggable databases (PDBs) is desupported in Oracle Database 21c.
- Desupport of Oracle Fail Safe
  Starting with Oracle Database 21c, Oracle Fail Safe is desupported for Oracle Database releases.
- Desupport of EUS Current User Database Links
  Current user database links for Enterprise User Security (EUS) are not supported in Oracle Database 21c.

**Parent topic:** Oracle Database 21c Behavior Changes, Desupports, and Deprecations

##### Desupport of DBMS_OBFUSCATION_TOOLKIT Package

Starting in Oracle Database 21c, the package `DBMS_OBFUSCATION_TOOLKIT` is desupported, and replaced with `DBMS_CRYPTO`.

Date: May 2021

`DBMS_OBFUSCATION_TOOLKIT` was deprecated in Oracle Database 10g Release 2. It is now removed in Oracle Database 21c. `DBMS_CRYPTO` replaces the functionality that `DBMS_OBFUSCATION_TOOLKIT` provided previously. `DBMS_CRYPTO` includes more modern and secure encryption technologies for your security requirements.

**Parent topic:** Desupported Features in Oracle Database 21c

##### Desupport of Several XML Database (XDB) features

Starting with Oracle Database 21c, several XML Database features are desupported.

Date: May 2021

The following features are desupported:

- Package `DBMS_XDBT`. There is no replacement.
- Oracle XQuery function `ora:contains`. Use XQuery Full Text instead.
- Oracle SQL function `XMLRoot`. Use SQL/XML function `XMLSerialize()` with a version number instead.
- Nested tables stored as index-ordered tables (IOTs). This includes both the use of option `DBMS_XMLSCHEMA.REGISTER_NT_AS_IOT`, and the use of clause `NESTED TABLE ``N`` STORE AS ... (ORGANIZATION INDEX)` when creating a table with nested-table column `N`. Instead, store nested-table columns using heap storage (the default behavior for PL/SQL procedure `DBMS_XMLSCHEMA.registerSchema`).
- PL/SQL procedure `DBMS_XSLPROCESSOR.CLOB2FILE`. Use `DBMS_LOB.CLOB2FILE` instead.
- PL/SQL function `DBMS_XSLPROCESSOR.READ2CLOB`. Use `DBMS_LOB.LOADCLOBFROMFILE` instead.
- Oracle XML DB Content Connector.

**Parent topic:** Desupported Features in Oracle Database 21c

##### Desupport of DBMS_LOB.LOADFROMFILE and LOB Buffering

Starting in Oracle Database 21c, the Large Object (LOB) features `DBMS_LOB.LOADFROMFILE` and LOB buffering are desupported.

Date: May 2021

The following features are desupported:

- `DBMS_LOB.LOADFROMFILE` Procedure. Use `DBMS_LOB.LoadClobFromFile` or `DBMS_LOB.LoadBlobFromFile` instead.

- The LOB buffering subsystem APIs:

  - `OCILobEnableBuffering()`
  - `OCILobDisableBuffering()`
  - `OCILobFlushBuffer()`

  In place of using these LOB buffering functions, use the LOB prefetch feature.

**Parent topic:** Desupported Features in Oracle Database 21c

##### Desupport of Oracle Data Guard Broker Properties and Logical Standby

Oracle Data Guard broker properties and logical standby properties whose functionality is replaced with the new EDIT … SET PARAMETER command in DGMGRL are now desupported.

Date: May 2021

The following Oracle Data Guard broker properties are desupported in Oracle Database 21c:

- `ArchiveLagTarget`
- `DataGuardSyncLatency`
- `LogArchiveMaxProcesses`
- `LogArchiveMinSucceedDest`
- `LogArchiveTrace`
- `StandbyFileManagement`
- `DbFileNameConvert`
- `LogArchiveFormat`
- `LogFileNameConvert`

The following Oracle Data Guard broker Properties that affect Logical Standby are desupported in Oracle Database 21c:

- `LsbyMaxEventsRecorded`
- `LsbyMaxServers`
- `LsbyMaxSga`
- `LsbyPreserveCommitOrder`
- `LsbyRecordAppliedDdl`
- `LsbyRecordSkippedDdl`
- `LsbyRecordSkipErrors`
- `LsbyParameter`

**Parent topic:** Desupported Features in Oracle Database 21c

##### Desupport of DBMS_CRYPTO_TOOLKIT_TYPES and DBMS_CRYPTO_TOOLKIT

Starting with Oracle Database 21c, the data types `DBMS_CRYPTO_TOOLKIT_TYPES` and package `DBMS_CRYPTO_TOOLKIT` are desupported.

Date: May 2021

The data types `DBMS_CRYPTO_TOOLKIT_TYPES` and the `DBMS_CRYPTO_TOOLKIT` package were deprecated in Oracle9i Database. These data types and package are now removed from Oracle Database 21c.

**Parent topic:** Desupported Features in Oracle Database 21c

##### Desupport of Non-CDB Oracle Databases

Starting with Oracle Database 21c, installation of non-CDB Oracle Database architecture is no longer supported.

Date: May 2021

The non-CDB architecture was deprecated in Oracle Database 12c. It is desupported in Oracle Database 21c. Oracle Universal Installer can no longer be used to create non-CDB Oracle Database instances.

**Parent topic:** Desupported Features in Oracle Database 21c

##### Desupport of Cluster Domain Member Clusters

Effective with Oracle Grid Infrastructure 21c, Member Clusters, which are part of the Oracle Cluster Domain architecture, are desupported.

Date: May 2021

Desupporting certain clustering features with limited adoption allows Oracle to focus on improving core scaling, availability, and manageability across all features and functionality. Oracle Cluster Domains consist of a Domain Services Cluster (DSC) and Member Clusters. It also includes Remote Oracle Advanced Cluster File System (Remote ACFS). Member Clusters were first introduced to simplify the management of larger cluster estates, and to minimize outage times for certain failures and configurations. However, additional enhancements in Standalone Clusters provide the same benefits. These enhancements make the use of Member Clusters unnecessary. Consequently, if you are currently using Member Clusters, then Oracle recommends that you use Standalone Clusters going forward.

**Parent topic:** Desupported Features in Oracle Database 21c

##### Desupport of Unicode Collation Algorithm (UCA) 6.1 Collations

Starting with Oracle Database 21c, the Unicode Collation Algorithm (UCA) 6.1 collations (`UCA0610_*`) are desupported. Use UCA 12.1 instead.

Date: May 2021

Oracle recommends that you use the latest supported version of Unicode Collation Algorithm (UCA) collations, which in Oracle Database 21c is UCA 12.1. UCA 6.1 collations were deprecated in Oracle Database 12c Release 2. UCA 12.1 incorporates all of the UCA enhancements since version 6.1, as well as proper collation weight assignments for all new characters introduced since Unicode 6.1.

**Parent topic:** Desupported Features in Oracle Database 21c

##### Desupport of ACFS on Microsoft Windows

Starting with Oracle Database 21c, the Oracle Grid Infrastructure feature Oracle Advanced Cluster File System (Oracle ACFS) is desupported with Microsoft Windows

Date: May 2021

Oracle ACFS is used for two major use cases:

- Oracle Database Files for Oracle Real Application Clusters (Oracle RAC)
- Generic files (unstructured data) that need to be shared across multiple hosts.

For Oracle Real Application Clusters files, Oracle recommends that you use Oracle ASM. For generic files, depending on your use case, Oracle recommends that you either move files to Oracle Database File System (DBFS), or move files to Microsoft Windows shared files.

**Parent topic:** Desupported Features in Oracle Database 21c

##### Desupport of Oracle ACFS Security (Vault) and ACFS Auditing

Starting with Oracle Grid Infrastructure 21c, Oracle Advanced Cluster File System (ACFS) Security (Vault) and ACFS Auditing are desupported.

Date: May 2021

To manage security and auditing, Oracle recommends that you use your operating system access controls and auditing systems. For example, with Linux, you can use the Linux Auditing System. As part of this desupport, the following views are removed:

    V$ASM_ACFS_SEC_ADMIN
    V$ASM_ACFS_SEC_CMDRULE
    V$ASM_ACFS_SEC_REALM
    V$ASM_ACFS_SEC_REALM_FILTER
    V$ASM_ACFS_SEC_REALM_GROUP
    V$ASM_ACFS_SEC_REALM_USER
    V$ASM_ACFS_SEC_RULE
    V$ASM_ACFS_SEC_RULESET
    V$ASM_ACFS_SEC_RULESET_RULE
    V$ASM_ACFS_SECURITY_INFO

**Parent topic:** Desupported Features in Oracle Database 21c

##### Desupport of Oracle ACFS on Member Clusters (ACFS Remote)

Starting with Oracle Grid Infrastructure 21c, Oracle Advanced Cluster File System (ACFS) on Member Clusters (ACFS Remote) is desupported.

Date: May 2021

Oracle Advanced Cluster File System (ACFS) on Member Clusters (ACFS Remote) is desupported. Desupporting certain clustering features with limited adoption allows Oracle to focus on improving core scaling, availability, and manageability across all features and functionality.

**Parent topic:** Desupported Features in Oracle Database 21c

##### Desupport of ACFS Encryption on Solaris and Windows

Starting with Oracle Database 21c, Oracle ACFS Encryption is desupported with no replacement on Oracle Solaris and Microsoft Windows.

Date: May 2021

Oracle ACFS Encryption on Oracle Solaris and Microsoft Windows is based on RSA technology. Retirement of RSA technology has been announced. Oracle ACFS Encryption continues to be supported on Linux, and is unaffected by this deprecation, because Linux uses an alternative technology.

**Parent topic:** Desupported Features in Oracle Database 21c

##### Desupport of ACFS Replication REPV1

Starting with Oracle Database 21c, the Oracle ACFS replication protocol `repv1` is desupported.

Date: May 2021

The initial ACFS replication protocol `repv1` was released with Oracle Database 11g Release 2 (11.2).The `replv2` protocol has been required since Oracle Database 12c Release 2 (12.2). The `replv1` protocol was available only during the required upgrade to `replv2` in 12.2 and later releases. The` replv1` protocol was deprecated in Oracle Database 19c. It is desupported in Oracle Database 21c.

**Parent topic:** Desupported Features in Oracle Database 21c

##### Desupport of Vendor Clusterware Integration with Oracle Clusterware

Starting with Oracle Clusterware 21c, the integration of vendor or third party clusterware with Oracle Clusterware is desupported.

Date: May 2021

The integration of vendor clusterware with Oracle Clusterware is desupported in Oracle Database 21c. Desupporting certain clustering features with limited adoption allows Oracle to focus on improving core scaling, availability, and manageability across all features and functionality. In the absence of an integration between different cluster solutions, the system is subject to the dueling cluster solutions issue: Independent cluster solutions can make individual decisions about which corrective actions must be taken in case of certain failures. To avoid conflicts, only one cluster solution should be active at any point in time. For this reason, Oracle recommends that you align your next software or hardware upgrade with the transition off of vendor cluster solutions. This desupport applies to clustered deployments, including Oracle Real Application Clusters and Oracle RAC One Node.

**Related Topics**

- [About vendor clusterware support for Oracle Clusterware (Doc ID 3044222.1)](https://support.oracle.com/rs?type=doc&id=3044222.1)

**Parent topic:** Desupported Features in Oracle Database 21c

##### Desupport of VERIFY_FUNCTION and VERIFY_FUNCTION_11G

The `VERIFY_FUNCTION` and `VERIFY_FUNCTION_11G` password verify functions are desupported in Oracle Database 21c.

Date: May 2021

These older functions are desupported because they enforce the weaker password restrictions from earlier releases. Instead, use the functions `ORA12C_VERIFY_FUNCTION`, `ORA12C_STRONG_VERIFY_FUNCTION`, or `ORA12C_STIG_VERIFY_FUNCTIONS`. These functions enforce stronger, more up-to-date password verification restrictions.

**Parent topic:** Desupported Features in Oracle Database 21c

##### Desupport of Deprecated Oracle Database Vault Roles

The Oracle Database Vault roles `DV_PUBLIC`, `DV_REALM_OWNER`, and `DV_REALM_RESOURCE` are desupported in Oracle Database 21c.

Date: May 2021

Oracle deprecated these Oracle Database Vault roles in Oracle Database 19c. The roles are granted powerful privileges,but were seldom used. During upgrades to Oracle Database 21c, these roles are removed, and are not available in new Oracle Database installations. If you are using these roles, and you are upgrading your database, then note the roles and privileges granted to them and then create roles for these privileges after the upgrade is complete.

**Parent topic:** Desupported Features in Oracle Database 21c

##### Desupport of Anonymous RC4 Cipher Suite

The use of the anonymous RC4 cipher suite for non-authenticated TLS connections is desupported in Oracle Database 21c (`SSL_DH_anon_WITH_RC4_128_MD5`)

Date: May 2021

Oracle recommends that you use the more secure authenticated connections available with Oracle Database. If you use anonymous Diffie-Hellman with RC4 for connecting to Oracle Internet Directory for Enterprise User Security, then you must migrate to use a different algorithm connection. Oracle recommends that you use either TLS one-way, or mutual authentication using certificates.

**Parent topic:** Desupported Features in Oracle Database 21c

##### Desupport of Adobe Flash-Based Oracle Enterprise Manager Express

Flash-based Oracle EM Express is desupported in Oracle 21c. Use the JET-based Oracle EM Express, which is the default.

Date: May 2021

Adobe Flash is desupported by all major browsers starting in January 2021. Oracle Database 19c and later releases of Oracle Enterprise Manager Express (Oracle EM Express) use Oracle JavaScript Extension Toolkit (JET) technology as a replacement for Flash.

**Parent topic:** Desupported Features in Oracle Database 21c

##### Desupport of Intelligent Data Placement (IDP)

Intelligent Data Placement (IDP) is desupported in Oracle Database 21c.

Date: May 2021

Intelligent Data Placement helped to place data on physical storage disks to reduce latency. This feature was deprecated in Oracle Database 12c release 2 (12.2). There is no replacement. Views and ASM disk group attributes associated with this feature are also desupported.

**Parent topic:** Desupported Features in Oracle Database 21c

##### Desupport of XML DB Content Connector

Oracle XML DB Content Connector was deprecated in Oracle Database 12c Release 2. It is desupported and removed in Oracle Database 21c.

Date: May 2021

XML DB Content Connector implemented the Java standard JSR-170 API. This standard has been replaced by Java standard JSR-283.

**Parent topic:** Desupported Features in Oracle Database 21c

##### Desupport of DBMS_XMLSAVE

The PL/SQL package `DBMS_XMLSAVE` is desupported in Oracle Database 21c. Use `DBMS_XMLSTORE` instead.

Date: May 2021

Replace `DBMS_XMLSAVE` calls with `DBMS_XMLSTORE`.

**Parent topic:** Desupported Features in Oracle Database 21c

##### Desupport of DBMS_XMLQUERY

The PL/SQL package `DBMS_XMLQUERY` is desupported in Oracle Database 21c. Use `DBMS_XMLGEN` instead.

Date: May 2021

Replace calls to `DBMS_XMLQUERY` with `DBMS_XMLGEN`.

**Parent topic:** Desupported Features in Oracle Database 21c

##### Desupport of FIPS Protect and Process Strength 0

The protect and process strength 0 (RSA key length 512) equivalent is desupported for FIPS. This strength is still available for the non-FIPS mode.

Date: May 2021

The default protect and process strength for Federal Information Processing Standard (FIPS) mode is currently 80. The equivalent RSA key strength is 1024. The equivalent ECC key strength is curves with minimum ECC curve key length 160, ECC named curves P192, K163 and B163 and above. The equivalent DH/DSA (Diffie Hellman, Digital Signature Algorithm) key length is 1024. Oracle recommends that you use FIPS protect strength 112, because the default FIPS protect strength, 80, is deprecated.

**Parent topic:** Desupported Features in Oracle Database 21c

##### Desupport of PDB Flat File Dictionary Dumps

The ability to create flat file dictionary dumps of pluggable databases (PDBs) is desupported in Oracle Database 21c.

Date: May 2021

In previous releases, using a flat file dictionary was one means of mining the redo logs for the changes associated with a specific PDB whose data dictionary was contained within the flat file. This feature is now desupported. Starting with Oracle Database 21c, Oracle recommends that you call `DBMS_LOGMNR.START_LOGMNR`, and supply the system change number (SCN) or time range that you want to mine. The SCN or time range options of `START_LOGMNR` are enhanced to support mining of individual PDBs.

**Parent topic:** Desupported Features in Oracle Database 21c

##### Desupport of Oracle Fail Safe

Starting with Oracle Database 21c, Oracle Fail Safe is desupported for Oracle Database releases.

Date: June 2021

This desupport notice does not apply to earlier releases of Oracle Database. Oracle Fail Safe will continue to be supported for the lifetime of Oracle Database 19c. For Oracle Database releases starting with Oracle Database 21c, if you are running Oracle Database on Microsoft Windows, then Oracle recommends that you investigate other failover solutions, such as Oracle RAC One Node, or Oracle Database Standard Edition High Availability.

**Parent topic:** Desupported Features in Oracle Database 21c

##### Desupport of EUS Current User Database Links

Current user database links for Enterprise User Security (EUS) are not supported in Oracle Database 21c.

Date: April 2024

Because Oracle Database releases after Oracle Database 19c only use the multitenant architecture, the use of EUS current user database links (`CREATE DATABASE LINK…TO CURRENT_USER` ) is not supported in releases after Oracle Database 19c. Oracle recommends that you use fixed user or connected user database links with EUS.

**Parent topic:** Desupported Features in Oracle Database 21c

#### Desupported Views in Oracle Database 21c

Review this list of desupported views for changes and replacements in view settings in this release.

- Desupport of V\$OBJECT_USAGE View
  The view V\$OBJECT_USAGE is desupported in Oracle Database 21c. Use USER_OBJECT_USAGE instead.

**Parent topic:** Oracle Database 21c Behavior Changes, Desupports, and Deprecations

##### Desupport of V\$OBJECT_USAGE View

The view V\$OBJECT_USAGE is desupported in Oracle Database 21c. Use USER_OBJECT_USAGE instead.

Date: October 2021

The V\$OBJECT_USAGE view displayed statistics about index usage gathered from the database for the indexes owned by the current user. This view was deprecated in Oracle Database 12c Release 1. It is now desupported. To obtain statistics about index usage owned by a user, use the USER_OBJECT_USAGE view instead of the V\$OBJECT_USAGE view.

**Parent topic:** Desupported Views in Oracle Database 21c

#### Desupported Initialization Parameters in Oracle Database 21c

Review this list of desupported initialization parameters for changes and replacements in parameter settings in this release.

- Desupport of UNIFIED_AUDIT_SGA_QUEUE_SIZE
  Starting in Oracle Database 21c, the initialization parameter `UNIFIED_AUDIT_SGA_QUEUE_SIZE` is desupported.
- Desupport of IGNORECASE Parameter for Passwords
  Starting in Oracle Database 21c, the `IGNORECASE` parameter for the `orapwd` file is desupported. All newly created password files are case-sensitive.
- Desupport of DISABLE_DIRECTORY_LINK_CHECK
  Starting in Oracle Database 21c, the `DISABLE_DIRECTORY_LINK_CHECK` parameter is desupported, with no replacement.
- Desupport of REMOTE_OS_AUTHENT Parameter
  The Oracle Database initialization parameter `REMOTE_OS_AUTHENT` has been removed from Oracle Database 21c.
- Desupport of SEC_CASE_SENSITIVE_LOGON
  The `SEC_CASE_SENSITIVE_LOGON` parameter is desupported in Oracle Database 21c.
- Desupport of CLUSTER_DATABASE_INSTANCES Parameter
  The `CLUSTER_DATABASE_INSTANCES` parameter is desupported in 21c. There is no replacement.

**Parent topic:** Oracle Database 21c Behavior Changes, Desupports, and Deprecations

##### Desupport of UNIFIED_AUDIT_SGA_QUEUE_SIZE

Starting in Oracle Database 21c, the initialization parameter `UNIFIED_AUDIT_SGA_QUEUE_SIZE` is desupported.

May 2021

The `UNIFIED_AUDIT_SGA_QUEUE_SIZE` parameter was deprecated in Oracle Database 12c Release 2 (12.2), and the value for the parameter was no longer was honored. It is now removed.

**Parent topic:** Desupported Initialization Parameters in Oracle Database 21c

##### Desupport of IGNORECASE Parameter for Passwords

Starting in Oracle Database 21c, the `IGNORECASE` parameter for the `orapwd` file is desupported. All newly created password files are case-sensitive.

May 2021

Case-sensitive password files provide more security than older non-case sensitive password files. To enhance security, Oracle recommends that you use case-sensitive passwords. However, upgraded password files from earlier Oracle Database releases can retain original case-insensitive passwords. To ensure that password files are case-sensitive, Oracle recommends that you force case sensitivity by migrating password files from one format to another, using the following syntax: `orapwd input_file=``input_password _file`` file=``output_password_file`

**Parent topic:** Desupported Initialization Parameters in Oracle Database 21c

##### Desupport of DISABLE_DIRECTORY_LINK_CHECK

Starting in Oracle Database 21c, the `DISABLE_DIRECTORY_LINK_CHECK` parameter is desupported, with no replacement.

May 2021

The `DISABLE_DIRECTORY_LINK_CHECK` parameter is disabled. Symbolic links managed previously with this parameter fail in the new Oracle Database release. If you attempt to use an affected feature after upgrade, where that feature used symbolic links, then you encounter `ORA-29283: invalid file operation: path traverses a symlink`.

**Parent topic:** Desupported Initialization Parameters in Oracle Database 21c

##### Desupport of REMOTE_OS_AUTHENT Parameter

The Oracle Database initialization parameter `REMOTE_OS_AUTHENT` has been removed from Oracle Database 21c.

May 2021

`REMOTE_OS_AUTHENT` was deprecated in Oracle Database 11g. To prevent potentially insecure connections to the database, Oracle is removing this authentication option in Oracle Database 21c.

**Parent topic:** Desupported Initialization Parameters in Oracle Database 21c

##### Desupport of SEC_CASE_SENSITIVE_LOGON

The `SEC_CASE_SENSITIVE_LOGON` parameter is desupported in Oracle Database 21c.

May 2021

The SEC_CASE_SENSITIVE_LOGON parameter was deprecated in Oracle Database 12c Release 1 (12.1). To ensure that new passwords are case-sensitive, Oracle is removing this parameter from Oracle Database 21c.

**Related Topics**

- [Checking for Accounts Using Case-Insensitive Password Version](database-preparation-tasks-to-complete-before-upgrades.md)

**Parent topic:** Desupported Initialization Parameters in Oracle Database 21c

##### Desupport of CLUSTER_DATABASE_INSTANCES Parameter

The `CLUSTER_DATABASE_INSTANCES` parameter is desupported in 21c. There is no replacement.

October 2021

The `init.ora` parameter `CLUSTER_DATABASE_INSTANCES` specified the number of configured Oracle Real Application Clusters (Oracle RAC) instances. This parameter was deprecated in Oracle Database 19c, because the number of configurable Oracle RAC instances is derived automatically from the Oracle Clusterware resource definitions. There is no replacement for this parameter, because there is no longer a reason to have this parameter.

**Parent topic:** Desupported Initialization Parameters in Oracle Database 21c

#### Deprecated Features in Oracle Database 21c

As part of your upgrade plan, review the features that are deprecated in this Oracle Database release, and review alternatives for your application strategies.

- Deprecation of AUTO OPTIMIZE Framework
  In Oracle Database Release 21c, the procedures `ADD_AUTO_OPTIMIZE` and `REMOVE_AUTO_OPTIMIZE`, and the views `CTX_AUTO_OPTIMIZE_INDEXES`, `CTX_USER_AUTO_OPTIMIZE_INDEXES` and `CTX_AUTO_OPTIMIZE_STATUS` are deprecated.
- Deprecation of CTXFILTERCACHE Query Operator
  Starting in Oracle Database Release 21c, `CTXFILTERCACHE` is deprecated, and also `CTX_FILTER_CACHE_STATISTICS` and `QUERY_FILTER_CACHE_SIZE`.
- Deprecation of Policy-Managed Databases
  Starting with Oracle Grid Infrastructure 21c, policy-managed databases are deprecated.
- Deprecation of Traditional Auditing
  Traditional auditing is deprecated in Oracle Database 21c. Oracle recommends that you use unified auditing, which enables selective and more effective auditing inside Oracle Database.
- Deprecation of Older Encryption Algorithms
  Starting with Oracle Database 21c, older encryption and hashing algorithms are deprecated.
- Deprecation of Cluster Domain - Domain Services Cluster
  Starting with Oracle Grid Infrastructure 21c, Domain Services Clusters (DSC), which is part of the Oracle Cluster Domain architecture, are deprecated.
- Deprecation of Enterprise User Security (EUS) User Migration Utility
  Enterprise User Security (EUS) User Migration Utility (UMU) is deprecated in Oracle Database 21c. Use EUS Manager (EUSM) features instead.
- Logical Standby and New Data Types
  If you use logical standby (when not used as part of `DBMS_ROLLING`), then you can use only data types added before Oracle Database 12c Release 2 (12.2)
- Deprecation of Sharded Queues
  AQ sharded queues are deprecated in Oracle Database 21c. Use Transactional Event Queues (TEQ) instead.
- Deprecation of MySQL Client Library Driver for Oracle
  The MySQL Client Library Driver for Oracle is deprecated in Oracle Database 21c.
- Deprecation of TLS 1.0 and 1.1 Transport Layer Security
  Starting with Oracle Database 21c, Transport Layer Security protocol versions 1.0 and 1.1 (TLS 1.0 and TLS 1.1) are deprecated.
- Deprecation of Unix Crypt (or MD5crypt) Password Verifier
  The Unix Crypt (`MD5crypt`) password verifier algorithm is deprecated in Oracle Database 21c server and clients, and passwords using this algorithm will stop working in a future release.
- Deprecation of ODP.NET OracleConfiguration.DirectoryType Property
  The Oracle Data Provider for .NET `OracleConfiguration DirectoryType` property and .NET configuration file `DIRECTORY_TYPE` setting are deprecated in Oracle Database 21c, and can be desupported in a future release.
- Deprecation of Weaker Encryption Key Strengths
  The use of weaker encryption keys is deprecated in Oracle Database 21c.
- Deprecation of DBSNMP Packages for Adaptive Thresholds Feature
  DBSNMP PL/SQL packages associated with the Adaptive Thresholds feature are deprecated in Oracle Database 21c.
- Deprecation of Oracle GoldenGate Replication for Oracle Sharding High Availability
  Oracle GoldenGate replication support for Oracle Sharding High Availability is deprecated in Oracle Database 21c.
- Deprecation of Anonymous Cipher Suites with Outbound TLS Connections
  Anonymous cipher suites for outbound TLS connections (Database to other services) are deprecated with Oracle Database 21c.
- Deprecation of the KERBEROS5PRE Adapter
  The use of the `KERBEROS5PRE` adapter is deprecated with Oracle Database 21c. Oracle recommends that you use the `KERBEROS5` adapter instead.
- Deprecation of Oracle Wallet Manager
  Oracle Wallet Manager (OWM) is deprecated with Oracle Database 21c.
- Deprecation of Oracle Enterprise Manager Database Express
  Oracle Enterprise Manager Database Express (EM Express) is deprecated, and will be removed in a future Oracle Database release.
- Deprecation of Service Attribute Value SESSION_STATE_CONSISTENCY = STATIC
  The combination of session attribute values `FAILOVER_TYPE = TRANSACTION` with `SESSION_STATE_CONSISTENCY = STATIC` is deprecated in Oracle Database 21c.
- Deprecation of SHA-1 use for SQLNET and DBMS_CRYPTO
  The use of SHA-1 with `DBMS_CRYPTO`, `SQLNET.CRYPTO_CHECKSUM_TYPES_CLIENT` and `SQLNET.CRYPTO_CHECKSUM_TYPES_SERVER` is deprecated.
- Deprecation of ACFSUTIL REPL REVERSE
  The `acfsutil repl reverse` command is deprecated in Oracle Database 21c. Use `repl failover` or `repl switchover` instead.
- Deprecation of Oracle OLAP
  Analytic workspaces, the OLAP DML programming language, and the OLAP Java API are deprecated in Oracle Database 21c.
- Deprecation of Oracle Database Extensions for .NET
  Oracle Database Extensions for .NET is deprecated in Oracle Database 21c. Oracle recommends that you either place .NET code in the middle tier, or use the External Procedures feature, or rewrite the code using PL/SQL or Java.
- Deprecation of Repository Events
  The use of repository events to trigger application actions is deprecated in Oracle Database 21c (21.3). There is no replacement.
- Deprecation of Quality of Service Management
  Starting with Oracle Database Release 21c, Oracle Quality of Service Management (QoSM, or QOS Management) is deprecated.
- Grid Infrastructure Management Repository Deprecation
  The Grid Infrastructure Management Repository (GIMR), or Management Database (`MGMTDB`), is deprecated in Oracle Database 21c.

**Parent topic:** Oracle Database 21c Behavior Changes, Desupports, and Deprecations

##### Deprecation of AUTO OPTIMIZE Framework

In Oracle Database Release 21c, the procedures `ADD_AUTO_OPTIMIZE` and `REMOVE_AUTO_OPTIMIZE`, and the views `CTX_AUTO_OPTIMIZE_INDEXES`, `CTX_USER_AUTO_OPTIMIZE_INDEXES` and `CTX_AUTO_OPTIMIZE_STATUS` are deprecated.

Date: May 2021

Basic optimization is now automatic for all indexes. You can also schedule additional optimization declaratively in the `CREATE INDEX` statement. Because of this enhancement, the `AUTO_OPTIMIZE` framework (procedures and views) is no longer necessary. Two procedures are deprecated in the `CTX_DDL` package: `ADD_AUTO_OPTIMIZE`, and `REMOVE_AUTO_OPTIMIZE`. In addition, the following views are deprecated: `CTX_AUTO_OPTIMIZE_INDEXES`, `CTX_USER_AUTO_OPTIMIZE_INDEXES` and `CTX_AUTO_OPTIMIZE_STATUS`.

**Parent topic:** Deprecated Features in Oracle Database 21c

##### Deprecation of CTXFILTERCACHE Query Operator

Starting in Oracle Database Release 21c, `CTXFILTERCACHE` is deprecated, and also `CTX_FILTER_CACHE_STATISTICS` and `QUERY_FILTER_CACHE_SIZE`.

Date: May 2021

The `CTXFILTERCACHE` query operator was designed to speed up commonly-used expressions in queries. In Oracle Database Release 21c, this function is replaced by other internal improvements. The` CTXFILTERCACHE` operator is deprecated (and will pass through its operands to be run as a normal query). Because they no longer have a function, the view `CTX_FILTER_CACHE_STATISTICS` is also deprecated, and also the storage attribute `QUERY_FILTER_CACHE_SIZE`.

**Parent topic:** Deprecated Features in Oracle Database 21c

##### Deprecation of Policy-Managed Databases

Starting with Oracle Grid Infrastructure 21c, policy-managed databases are deprecated.

Date: May 2021

You can continue to use existing server pools, and create new pools and policies. Resources using existing server pools can continue to use them transparently.

The use of CRS configuration policies and the CRS policy set can be desupported in a future release. In place of server pools and policy-managed databases, Oracle recommends that you use the new "Merged" management style.

**Parent topic:** Deprecated Features in Oracle Database 21c

##### Deprecation of Traditional Auditing

Traditional auditing is deprecated in Oracle Database 21c. Oracle recommends that you use unified auditing, which enables selective and more effective auditing inside Oracle Database.

Date: May 2021

Standard traditional auditing in Oracle Database has been provided for more than two decades. Traditional auditing provided built-in support for auditing statements, privileges and objects. Over the years, as data auditing became a key factor to ensuring the success of data strategy, Oracle recognized that there was a need to provide selective and effective auditing inside Oracle Database. To address this need, Oracle introduced unified auditing with Oracle Database 12c. In addition to providing built-in audit operation support, Unified Auditing simplifies management of auditing within the database, provides the ability to accelerate auditing based on conditions, and increases the security of audit data generated by the database. Unified Auditing and Traditional Auditing (mixed mode) has been the default auditing mode from Oracle Database 12c onward. Mixed mode auditing was offered as to enable you to become familiar with Unified Auditing, and to transition from Traditional Auditing. With the deprecation of Traditional Auditing in this release, Oracle recommends that you migrate to Unified Auditing. Refer to the migration procedure in Oracle Database Security Guide.

**Parent topic:** Deprecated Features in Oracle Database 21c

##### Deprecation of Older Encryption Algorithms

Starting with Oracle Database 21c, older encryption and hashing algorithms are deprecated.

Date: May 2021

The deprecated algorithms for `DBMS_CRYPTO` and native network encryption include MD4, MD5, DES, 3DES, and RC4-related algorithms as well as 3DES for Transparent Data Encryption (TDE). Removing older, less secure cryptography algorithms prevents accidental use of these algorithms. To meet your security requirements, Oracle recommends that you use more modern cryptography algorithms, such as the Advanced Encryption Standard (AES).

As a consequence of this deprecation, Oracle recommends that you review your network encryption configuration to see if you have specified use of any of the deprecated algorithms. If any are found, then switch to using a more modern cipher, such as AES. Also, if you are currently using 3DES encryption for your TDE deployment, then you should plan to migrate to a more modern algorithm such as AES. For more information, refer to Oracle Database Security Guide

**Parent topic:** Deprecated Features in Oracle Database 21c

##### Deprecation of Cluster Domain - Domain Services Cluster

Starting with Oracle Grid Infrastructure 21c, Domain Services Clusters (DSC), which is part of the Oracle Cluster Domain architecture, are deprecated.

Date: May 2021

Deprecating certain clustering features with limited adoption enables Oracle to focus on improving core scaling, availability, and manageability across all features and functionality. Oracle Cluster Domains consist of a Domain Services Cluster (DSC) and Member Clusters. Member Clusters were deprecated in Oracle Grid Infrastructure 19c. The DSC continues to be available to provide services to production clusters. However, with most of those services no longer requiring the DSC for hosting, installation of DSCs are deprecated, and can be desupported in a future release. Oracle recommends that you use any cluster or system of your choice for services previously hosted on the DSC, if applicable. Oracle will continue to support the DSC for hosting shared services, until each service can be used on alternative systems.

**Parent topic:** Deprecated Features in Oracle Database 21c

##### Deprecation of Enterprise User Security (EUS) User Migration Utility

Enterprise User Security (EUS) User Migration Utility (UMU) is deprecated in Oracle Database 21c. Use EUS Manager (EUSM) features instead.

Date: May 2021

Because organizational directory services already have records of all employees, there is no need to bulk-migrate database users to directory services. EUS Manager (EUSM) has many of the same functions as the EUS UMU. Oracle recommends that you use it place of EUS UMU.

**Parent topic:** Deprecated Features in Oracle Database 21c

##### Logical Standby and New Data Types

If you use logical standby (when not used as part of `DBMS_ROLLING`), then you can use only data types added before Oracle Database 12c Release 2 (12.2)

Date: May 2021

New data types added after Oracle Database 12c Release 1 (12.1) are not supported with Oracle Data Guard logical standby. For example, Oracle Data Guard logical standby does not support long identifiers, complex Abstract Data Types (ADTs), and spatial data types. Note that this limitation does not exist with an Oracle Data Guard physical standby database, `DBMS_ROLLING`, or Oracle GoldenGate. To obtain the benefits of a standby database with more recent data types, Oracle recommends that you consider using either a physical standby database, a snapshot standby database, or that you use the logical replication features of Oracle GoldenGate.

**Parent topic:** Deprecated Features in Oracle Database 21c

##### Deprecation of Sharded Queues

AQ sharded queues are deprecated in Oracle Database 21c. Use Transactional Event Queues (TEQ) instead.

Date: May 2021

Starting with Oracle Database 21c, AQ sharded queues are being repackaged as Transactional Event Queues (TEQ). In the Oracle Database 21c release, TEQs coexist with AQ sharded queues. However, AQ sharded queues will be desupported in a future release and will be replaced by TEQ. Oracle recommends that you move to TEQs for higher throughput and better performance on Oracle Real Application Clusters (Oracle RAC).

**Parent topic:** Deprecated Features in Oracle Database 21c

##### Deprecation of MySQL Client Library Driver for Oracle

The MySQL Client Library Driver for Oracle is deprecated in Oracle Database 21c.

Date: May 2021

The MySQL Client library driver, `liboramysql`, is deprecated. Oracle may desupport `liboramysql` in a future release. There is no replacement. This deprecation does not affect the ability of older Oracle Database Client releases that use `liboramysql` to connect to the database. However, it is possible that the features available to use through these clients eventually can be limited.

**Parent topic:** Deprecated Features in Oracle Database 21c

##### Deprecation of TLS 1.0 and 1.1 Transport Layer Security

Starting with Oracle Database 21c, Transport Layer Security protocol versions 1.0 and 1.1 (TLS 1.0 and TLS 1.1) are deprecated.

Date: May 2021

In accordance with security best practices, Oracle has deprecated the use of TLS 1.0 and TLS 1.1. To meet your security requirements, Oracle strongly recommends that you use TLS 1.2 instead.

**Parent topic:** Deprecated Features in Oracle Database 21c

##### Deprecation of Unix Crypt (or MD5crypt) Password Verifier

The Unix Crypt (`MD5crypt`) password verifier algorithm is deprecated in Oracle Database 21c server and clients, and passwords using this algorithm will stop working in a future release.

Date: May 2021

Enterprise User Security (EUS) customers with enterprise users in Oracle Internet Directory (OID) potentially can be using older, less secure password verifiers generated by Unix Crypt, either by OID, or by the operating system, before they were migrated to OID. Unix Crypt is a less secure algorithm to hash passwords. When `MD5crypt` is removed, Oracle Database can no longer authenticate EUS or OID users with the Unix Crypt passwrod verifier type. Oracle recommends that you reset passwords in OID now, using newer, more secure hashing algorithms.

**Parent topic:** Deprecated Features in Oracle Database 21c

##### Deprecation of ODP.NET OracleConfiguration.DirectoryType Property

The Oracle Data Provider for .NET `OracleConfiguration DirectoryType` property and .NET configuration file `DIRECTORY_TYPE` setting are deprecated in Oracle Database 21c, and can be desupported in a future release.

Date: May 2021

The `OracleConfiguration DirectoryServerType` property replaces the `DirectoryType` property. The .NET configuration file `DIRECTORY_SERVER_TYPE` setting replaces the `DIRECTORY_TYPE` setting. All these properties have identical functionality. Oracle recommends to developers that you use and migrate to the new properties. The `DirectoryServerType` and `DIRECTORY_SERVER_TYPE` names better align with the `ldap.ora` parameter,` DIRECTORY_SERVER_TYPE`, which provides equivalent functionality.

**Parent topic:** Deprecated Features in Oracle Database 21c

##### Deprecation of Weaker Encryption Key Strengths

The use of weaker encryption keys is deprecated in Oracle Database 21c.

Date: May 2021

The security strength of the cipher algorithms have been changed in Oracle Database 21c with the introduction of the newest RSA BSAFE Micro Edition Suite (MES) v 4.5. The following cipher algorithms are deprecated:

- For FIPS mode
  - The FIPS default protect strength of 80 has been deprecated. This strength is still available, but will not be the default protect strength in the future. The new default protect strength for FIPS mode will be 112.
    - When the default FIPS protect strength changes from 80 to 112 with a later release, you can still revert to using the older, less secure FIPS protect strength 80 by setting a parameter.
  - Diffie Hellman and Digital Signature Algorithm (DH/DSA) with 1024 key size is deprecated. The new minimum supported key size will be 2048. The 1024 key size support will remain available when the default protect strength will be changed to 112 bits of security strength (equivalent to 2048 key size), the process strength remains at 80 bits of security strength (equivalent to 1024 key size).
- For non-FIPS mode
  - Both protect and process strength 0 (RSA key length 512) are deprecated. By default, both protect and process strength are now 80. Protect and process strength 0 (RSA key 512 and equivalent) is still available, but not recommended for use.

**Related Topics**

- [Managing Deprecated Weaker Algorithm Keys](../dbseg/index.md)

**Parent topic:** Deprecated Features in Oracle Database 21c

##### Deprecation of DBSNMP Packages for Adaptive Thresholds Feature

DBSNMP PL/SQL packages associated with the Adaptive Thresholds feature are deprecated in Oracle Database 21c.

Date: May 2021

Beginning with Oracle Enterprise Manager Cloud Control 13.5, all features of Database Server Adaptive Thresholds and Baseline Metric Thresholds will be removed for all Oracle Database targets. The following database server side packages that support this feature will no longer be available: `DBSNMP.BSLN`, `DBSNMP.BSLN_INTERNAL` and `DBSNMP.MGMT_RESPONSE`.

For more information about this deprecation, refer to My Oracle Support 2697846.1

**Related Topics**

- [My Oracle Support Note 2697846.1](https://support.oracle.com/rs?type=doc&id=2697846.1)

**Parent topic:** Deprecated Features in Oracle Database 21c

##### Deprecation of Oracle GoldenGate Replication for Oracle Sharding High Availability

Oracle GoldenGate replication support for Oracle Sharding High Availability is deprecated in Oracle Database 21c.

Date: May 2021

**Parent topic:** Deprecated Features in Oracle Database 21c

##### Deprecation of Anonymous Cipher Suites with Outbound TLS Connections

Anonymous cipher suites for outbound TLS connections (Database to other services) are deprecated with Oracle Database 21c.

Date: May 2021

Anonymous cipher suites only encrypt the connection between client and server without authenticating either party leaving it vulnerable to a person-in-the-middle attack. The following three anonymous cipher suites are deprecated with this release:

- `NZTLS_DH_ANON_WITH_AES_256_GCM_SHA384`
- `NZTLS_DH_ANON_WITH_AES_128_GCM_SHA256`
- `NZSSL_DH_ANON_WITH_3DES_EDE_CBC_SHA`

To provide better protection for your connections, Oracle recommends using the strongest possible non-anonymous TLS cipher suites.

**Parent topic:** Deprecated Features in Oracle Database 21c

##### Deprecation of the KERBEROS5PRE Adapter

The use of the `KERBEROS5PRE` adapter is deprecated with Oracle Database 21c. Oracle recommends that you use the `KERBEROS5` adapter instead.

Date: May 2021

The `KERBEROS5` adapter is the primary adapter supported by Oracle for Kerberos authentication. `KERBEROS5PRE` is not needed anymore, and will be desupported in a future release. This change simplifies Kerberos configuration.

**Parent topic:** Deprecated Features in Oracle Database 21c

##### Deprecation of Oracle Wallet Manager

Oracle Wallet Manager (OWM) is deprecated with Oracle Database 21c.

Date: May 2021

Instead of using Oracle Wallet Manager, Oracle recommends that you use the command line tool `orapki` .

**Parent topic:** Deprecated Features in Oracle Database 21c

##### Deprecation of Oracle Enterprise Manager Database Express

Oracle Enterprise Manager Database Express (EM Express) is deprecated, and will be removed in a future Oracle Database release.

Date: May 2021

EM Express is a web-based database management tool that is built inside the Oracle Database. It supports key performance management and basic database administration functions. Many of EM Express's capabilities are also available in Oracle SQL Developer, which is included in all Oracle Database editions. Oracle recommends that you replace your use of EM Express with Oracle SQL Developer.

**Parent topic:** Deprecated Features in Oracle Database 21c

##### Deprecation of Service Attribute Value SESSION_STATE_CONSISTENCY = STATIC

The combination of session attribute values `FAILOVER_TYPE = TRANSACTION` with `SESSION_STATE_CONSISTENCY = STATIC` is deprecated in Oracle Database 21c.

Date: May 2023

The use of session attribute values `FAILOVER_TYPE = TRANSACTION` with `SESSION_STATE_CONSISTENCY = STATIC` is no longer a supported service attribute combination.

Instead use one of the following combinations in the service configuration:

- `FAILOVER_TYPE = AUTO` with `SESSION_STATE_CONSISTENCY = AUTO`
- `FAILOVER_TYPE = TRANSACTION` with `SESSION_STATE_CONSISTENCY = DYNAMIC`

These configurations enforce session state tracking in Oracle Database, ensuring that session state is preserved at session migration and session failover. Note that starting with Oracle Database 21c, you may also wish to set the `RESET_STATE` attribute to clear your session state set by applications in request at the end of the request. For more information, see `RESET_STATE`.

**Parent topic:** Deprecated Features in Oracle Database 21c

##### Deprecation of SHA-1 use for SQLNET and DBMS_CRYPTO

The use of SHA-1 with `DBMS_CRYPTO`, `SQLNET.CRYPTO_CHECKSUM_TYPES_CLIENT` and `SQLNET.CRYPTO_CHECKSUM_TYPES_SERVER` is deprecated.

May 2021

Using SHA-1 (Secure Hash Algorithm 1) with the parameters `SQLNET.CRYPTO_CHECKSUM_TYPES_CLIENT` and `SQLNET.CRYPTO_CHECKSUM_TYPES_SERVER` is deprecated in this release, and can be desupported in a future release. Using SHA-1 ciphers with `DBMS_CRYPTO` is also deprecated (`HASH_SH1`, `HMAC_SH1`). Instead of using SHA1, Oracle recommends that you start using a stronger SHA-2 cipher in place of the SHA-1 cipher.

**Parent topic:** Deprecated Features in Oracle Database 21c

##### Deprecation of ACFSUTIL REPL REVERSE

The `acfsutil repl reverse` command is deprecated in Oracle Database 21c. Use `repl failover` or `repl switchover` instead.

Date: August 2021

The Oracle Advanced Cluster File System (ACFS) command utility `acfsutil` includes the commands `repl failover` and `repl switchover`. These commands provide more functionality, including all the functions of `acfsutil repl reverse`. For this reason, Oracle is deprecating the `acfsutil repl reverse` command.

**Parent topic:** Deprecated Features in Oracle Database 21c

##### Deprecation of Oracle OLAP

Analytic workspaces, the OLAP DML programming language, and the OLAP Java API are deprecated in Oracle Database 21c.

Date: August 2021

For new applications requiring advanced analytic capabilities, Oracle recommends that you consider analytic views (a feature of Oracle Database), or Oracle Essbase. Oracle analytic views are a feature of every Oracle Database edition. If your application uses OLAP for dimensional query and reporting applications, then Oracle recommends that you consider Oracle analytic views as a replacement for OLAP. Analytic views provide a fast and efficient way to create analytic queries of data stored in existing database tables and views. With Oracle analytic views, you obtain a dimensional query model and supporting metadata without requiring a "cube build/update" process. The elimination of the cube build/update process relieves scalability constraints (model complexity and data volume), simplifies the data preparation pipeline, and reduces or eliminates data latency. In addition, you can use analytic views with OLTP applications, external tables, and non-relational data types (for example, JSON) when these non-relational data types are wrapped by relational views.

**Parent topic:** Deprecated Features in Oracle Database 21c

##### Deprecation of Oracle Database Extensions for .NET

Oracle Database Extensions for .NET is deprecated in Oracle Database 21c. Oracle recommends that you either place .NET code in the middle tier, or use the External Procedures feature, or rewrite the code using PL/SQL or Java.

Date: September 2021

Oracle Database Extensions for .NET is a feature of Oracle Database on Microsoft Windows that enables you to use stored procedures and functions written in a language managed by .NET, such as C#.

Oracle Database hosts the Microsoft Common Language Runtime (CLR) in an external process, outside of the Oracle Database process. Application developers can write stored procedures and functions using any .NET compliant language, such as C# and VB.NET, and use these .NET stored procedures in the database, in the same manner as other PL/SQL or Java stored procedures. .NET stored procedures can be called from PL/SQL packages, procedures, functions, and triggers; from SQL statements; or from anywhere a PL/SQL procedure or function can be called.

Migration options include:

- Moving the .NET code (assemblies) into a middle tier
- Using the External Procedures feature to have the external process load and execute the .NET assembly
- Rewriting the stored procedures using PL/SQL or Java

**Parent topic:** Deprecated Features in Oracle Database 21c

##### Deprecation of Repository Events

The use of repository events to trigger application actions is deprecated in Oracle Database 21c (21.3). There is no replacement.

October 2021

Repository events are events that can be used to trigger application actions. Repository events include repository changes, such as creating, deleting, locking, unlocking, rendering, linking, unlinking, placing under version control, checking in, checking out, unchecking out (reverting a checked out version), opening, and updating a resource. The deprecation of the use of repository events includes deprecation of the `DBMS_XEVENT` package, and the following subprogram groups:

- `XDBevent`
- `XDBRepositoryEvent`
- `XDBHandler`
- `XDBHandlerList`
- `XDBPath`
- `XDBLink`

**Parent topic:** Deprecated Features in Oracle Database 21c

##### Deprecation of Quality of Service Management

Starting with Oracle Database Release 21c, Oracle Quality of Service Management (QoSM, or QOS Management) is deprecated.

Date: November 2022

Oracle QoSM automates the workload management for an entire system by adjusting the system configuration based on predefined policies to keep applications running at the performance levels needed. Applications and databases are increasingly deployed in systems that provide some of the resource management capabilities of QoSM. At the same time, Oracle’s Autonomous Health Framework has been enhanced to adjust and provide recommendations to mitigate events and conditions that impact the health and operational capability of a system and its associated components. For those reasons, QoSM is deprecated with Oracle Database 21c.

**Parent topic:** Deprecated Features in Oracle Database 21c

##### Grid Infrastructure Management Repository Deprecation

The Grid Infrastructure Management Repository (GIMR), or Management Database (`MGMTDB`), is deprecated in Oracle Database 21c.

Date: May 2023

Solutions using the GIMR (GIMR clients) such as Oracle Autonomous Health Framework (AHF), Cluster Health Monitor (CHM), Oracle Cluster Health Advisor (CHA), or Oracle Fleet Patching and Provisioning (FPP), will automatically transition to alternative repositories as needed. As a purpose-built database used exclusively by GIMR clients, the deprecation and potential removal of the GIMR in future releases will be seamless for Oracle Grid Infrastructure and related services.

**Parent topic:** Deprecated Features in Oracle Database 21c

#### Deprecated Views in Oracle Database 21c

As part of your upgrade plan, review the views that are deprecated starting with this Oracle Database release.

- Deprecation of Traditional Auditing Views
  As a result of deprecating traditional auditing, the views associated with traditional auditing are also deprecated.

**Parent topic:** Oracle Database 21c Behavior Changes, Desupports, and Deprecations

##### Deprecation of Traditional Auditing Views

As a result of deprecating traditional auditing, the views associated with traditional auditing are also deprecated.

Date: May 2021

- Static data dictionary views:

  - ALL_DEF_AUDIT_OPTS

  - AUDIT_ACTIONS

  - DBA_AUDIT_EXISTS

  - DBA_AUDIT_OBJECT

  - DBA_AUDIT_SESSION

  - DBA_AUDIT_STATEMENT

  - DBA_AUDIT_TRAIL

  - DBA_COMMON_AUDIT_TRAIL

  - DBA_FGA_AUDIT_TRAIL

  - DBA_OBJ_AUDIT_OPTS

  - DBA_PRIV_AUDIT_OPTS

  - DBA_STMT_AUDIT_OPTS

  - USER_AUDIT_OBJECT

  - USER_AUDIT_SESSION

  - USER_AUDIT_STATEMENT

  - USER_AUDIT_TRAIL

  - USER_OBJ_AUDIT_OPTS

- Dynamic performance view:

  - V$XML_AUDIT_TRAIL

**Parent topic:** Deprecated Views in Oracle Database 21c

#### Deprecated Parameters in Oracle Database 21c

As part of your upgrade plan, review the initialization parameters that are deprecated starting with this Oracle Database release.

- Deprecation of Traditional Auditing Initialization Parameters
  As a result of deprecating traditional auditing, the initialization parameters associated with traditional auditing are also deprecated.

**Parent topic:** Oracle Database 21c Behavior Changes, Desupports, and Deprecations

##### Deprecation of Traditional Auditing Initialization Parameters

As a result of deprecating traditional auditing, the initialization parameters associated with traditional auditing are also deprecated.

Date: May 2021

- Initialization parameters:

  - AUDIT_FILE_DEST

  - AUDIT_SYS_OPERATIONS

  - AUDIT_SYSLOG_LEVEL

  - AUDIT_TRAIL

**Parent topic:** Deprecated Parameters in Oracle Database 21c

### Oracle Database 19c Behavior Changes, Desupports, and Deprecations

Review for descriptions of Oracle Database 19c release changes.

- Behavior Changes for Oracle Database 19c Upgrade Planning
  Review these behavior changes to help plan for upgrades to Oracle Database 19c.
- Desupported Features in Oracle Database 19c
  As part of your upgrade plan, review the features that are desupported in Oracle Database 19c.
- Desupported Parameters in Oracle Database 19c
  As part of your upgrade plan, review the initialization parameters that are not supported starting with Oracle Database 19c.
- Deprecated Features in Oracle Database 19c
  As part of your upgrade plan, review the features that are deprecated in Oracle Database 19, and review alternatives for your application strategies.
- Deprecated Initialization Parameters in Oracle Database 19c
  As part of your upgrade plan, review the initialization parameters that are deprecated in Oracle Database 19c.

**Parent topic:** Oracle Database Changes, Desupports, and Deprecations

#### Behavior Changes for Oracle Database 19c Upgrade Planning

Review these behavior changes to help plan for upgrades to Oracle Database 19c.

Behavior changes can include default changes for parameters or features, product name changes, and other changes to the database configuration that may require your attention.

- All Time Zone Files (DST) Included in Release Updates (RUs)
  Starting with Oracle Database 19c RU 19.18.0, all available DST patches are installed with the RU, and deployed into the `Oracle_home``/oracore/zoneinfo` directory.
- Changes to Oracle Data Guard Properties Management
  Starting with Oracle Database 19c, properties for Oracle Data Guard configuration are stored in Oracle Database, instead of an external configuration file.
- Rapid Home Provisioning (RHP) Name Change
  Starting with Oracle Database 19c and Oracle Grid Infrastructure 19c, Rapid Home Provisioning is renamed to Fleet Patching and Provisioning (FPP).
- Resupport of Direct File Placement for OCR and Voting Disks
  Starting with Oracle Grid Infrastructure 19c, the desupport for direct placement of OCR and voting files on shared file systems is rescinded for Oracle Standalone Clusters.
- Optional Install for the Grid Infrastructure Management Repository
  Starting with Oracle Grid Infrastructure 19c, the Grid Infrastructure Management Repository (GIMR) is optional for new installations of Oracle Standalone Cluster. Oracle Domain Services Clusters still require the installation of a GIMR as a service component.
- Support for DBMS_JOB
  Oracle continues to support the `DBMS_JOB` package. However, you must grant the `CREATE JOB` privilege to the database schemas that submit `DBMS_JOB` jobs.
- About Standard Edition High Availability
  Starting with Oracle Database 19c, you can install Oracle Database Standard Edition 2 in high availability mode.
- Manage "Installed but Disabled" Module Bug Fixes with DBMS_OPTIM_BUNDLE
  To manage the implementation of Oracle Database bug fixes that cause a SQL execution plan change, use `DBMS_OPTIM_BUNDLE`.
- Windows Authentication No Longer Uses NTLM by Default
  For Microsoft Windows installations with `AUTHENTICATION_SERVICES=NTS`, in this Oracle Database release, the `SQLNET.NO_NTLM` parameter setting in the `sqlnet.ora` file defaults to `TRUE`, which can cause ORA-12638 errors.

**Parent topic:** Oracle Database 19c Behavior Changes, Desupports, and Deprecations

##### All Time Zone Files (DST) Included in Release Updates (RUs)

Starting with Oracle Database 19c RU 19.18.0, all available DST patches are installed with the RU, and deployed into the `Oracle_home``/oracore/zoneinfo` directory.

Installing DST patches does not affect current database operation. However, installing the patches with the RU makes it easier for you to adjust the timezone version of your database, if you have a requirement to do so. For example, if you are using Transportable Tablespaces, or Full Transportable Export/Import, then you must ensure that your source and target databases are using identical character sets and identical time zone settings. With this change, you can more easily choose to change your destination database to use a different time zone file version than the default.

**Note:**

By default, AutoUpgrade changes the database time zone to the latest available level. If you don’t want the time zone to be upgraded, then you must explicitly set the local parameter `timezone_upg` in your AutoUpgrade configuration file to `no`. For example:

`upg1.timezone_upg=no`

When you patch a database with RU 19.18 or later, a new database created with Database Configuration Assistant (DBCA) in that patched Oracle home will be created with the latest time zone files.

**Related Topics**

- [Choosing a Time Zone File](../nlspg/datetime-data-types-and-time-zone-support.md)
- [RUs contain now all available DST patches](https://mikedietrichde.com/2023/01/19/rus-contain-now-all-available-dst-patches/)
- [Primary Note DST FAQ : Updated DST Transitions and New Time Zones in Oracle RDBMS and OJVM Time Zone File Patches (Doc ID 412160.1)](https://support.oracle.com/rs?type=doc&id=412160.1)

**Parent topic:** Behavior Changes for Oracle Database 19c Upgrade Planning

##### Changes to Oracle Data Guard Properties Management

Starting with Oracle Database 19c, properties for Oracle Data Guard configuration are stored in Oracle Database, instead of an external configuration file.

Oracle Data Guard property names, storage locations, and behaviors are changed in Oracle Database 19c.

##### Property Name Changes

Table 10-1 Oracle Data Guard Property Name Changes

| Property                   | Oracle Database 18c and earlier releases | Oracle Database 19c and later releases |
|:---------------------------|:-----------------------------------------|:---------------------------------------|
| Archive location           | `OnlineArchiveLocation`                  | `ArchiveLocation`                      |
| Alternate location         | `OnlineAlternateLocation`                | `AlternateLocation`                    |
| Standby archive location   | `StandbyArchiveLocation`                 | `StandbyArchiveLocation`               |
| Standby alternate location | `StandbyAlternateLocation`               | `StandbyAlternateLocation`             |

##### Property Behavior Changes

- When `StandbyArchiveLocation` and `StandbyAlternateLocation` have empty strings, `ArchiveLocation` and `AlternateLocation` are locations for both online and standby log files

- When `StandbyArchiveLocation` and `StandbyAlternateLocation` have non-empty strings, `ArchiveLocation` and `AlternateLocation` are locations only for online log files

- The behavior of `StandbyArchiveLocation` and `StandbyAlternateLocation` are not changed. These properties are only used for standby log file locations.

##### Scope Changes

Starting with Oracle Database 19c, all four of the Oracle Data Guard properties have the scope `Database`. In earlier releases, they had the scope `Instance`.

##### Imports and Upgrades

Starting with Oracle Database 19c, note the following changes to the way Oracle Data Guard manages property imports and upgrades:

- Oracle Data Guard broker no longer automatically imports local archiving location properties.

- Oracle Data Guard broker no longer automatically upgrades the earlier release property settings from metadata files created from Oracle Database 18c and earlier release Data Guard broker exports.

**Parent topic:** Behavior Changes for Oracle Database 19c Upgrade Planning

##### Rapid Home Provisioning (RHP) Name Change

Starting with Oracle Database 19c and Oracle Grid Infrastructure 19c, Rapid Home Provisioning is renamed to Fleet Patching and Provisioning (FPP).

**Parent topic:** Behavior Changes for Oracle Database 19c Upgrade Planning

##### Resupport of Direct File Placement for OCR and Voting Disks

Starting with Oracle Grid Infrastructure 19c, the desupport for direct placement of OCR and voting files on shared file systems is rescinded for Oracle Standalone Clusters.

In Oracle Grid Infrastructure 12c Release 2 (12.2), Oracle announced that it would no longer support the placement of the Oracle Grid Infrastructure Oracle Cluster Registry (OCR) and voting files directly on a shared file system. This desupport is now rescinded. Starting with Oracle Grid Infrastructure 19c (19.3), with Oracle Standalone Clusters, you can again place OCR and voting disk files directly on shared file systems. However, for Oracle Domain Services Clusters, you must continue to place OCR and voting files in quorum failure groups managed by Oracle Automatic Storage Management (Oracle ASM).

**Parent topic:** Behavior Changes for Oracle Database 19c Upgrade Planning

##### Optional Install for the Grid Infrastructure Management Repository

Starting with Oracle Grid Infrastructure 19c, the Grid Infrastructure Management Repository (GIMR) is optional for new installations of Oracle Standalone Cluster. Oracle Domain Services Clusters still require the installation of a GIMR as a service component.

The Oracle Standalone Cluster locally hosts the GIMR on an Oracle ASM disk group or a shared file system; this GIMR is a multitenant database with a single pluggable database (PDB). The global GIMR runs in an Oracle Domain Services Cluster. Oracle Domain Services Cluster locally hosts the GIMR in a separate Oracle ASM disk group. Client clusters, such as Oracle Member Cluster for Database, use the remote GIMR located on the Oracle Domain Services Cluster. For two-node or four-node clusters, hosting the GIMR for a cluster on a remote cluster reduces the overhead of running an extra infrastructure repository on a cluster. The GIMR for an Oracle Domain Services Cluster is a multitenant database with one PDB, and additional PDB for each member cluster that is added.

**Parent topic:** Behavior Changes for Oracle Database 19c Upgrade Planning

##### Support for DBMS_JOB

Oracle continues to support the `DBMS_JOB` package. However, you must grant the `CREATE JOB` privilege to the database schemas that submit `DBMS_JOB` jobs.

Oracle Scheduler replaces the `DBMS_JOB` package. Although `DBMS_JOB` is still supported for backward compatibility, Oracle strongly recommends that you switch from `DBMS_JOB` to Oracle Scheduler.

In upgrades of Oracle Database 19c and later releases, if the upgrade can recreate existing `DBMS_JOB` jobs using `DBMS_SCHEDULER`, then for backward compatibility, after the upgrade, `DBMS_JOB` continues to act as a legacy interface to the `DBMS_SCHEDULER` job. If existing jobs cannot be recreated using `DBMS_SCHEDULER` because of issues with the metadata, then you receive a `JOB_TABLE_INTEGRITY` warning when you run upgrade prechecks. In that case, you have three options:

- Fix the metadata. After the upgrade continue to run after the upgrade using `DBMS_JOBS` as an interface, and run as `DBMS_SCHEDULER` jobs.
- Drop the jobs, if no longer required.
- Drop `DBMS_JOBS` jobs, and recreate the jobs manually using `DBMS_SCHEDULER`.

For existing jobs created with `DBMS_JOB` that are recreated during the upgrade, the legacy `DBMS_JOB` job is still present as an interface, but using it always creates a `DBMS_SCHEDULER` entry. Apart from the interface, the job is run as a `DBMS_SCHEDULER` job. If you subsequently disable the `DBMS_JOB` job created before the upgrade, then the `DBMS_SCHEDULER` job is also disabled. To avoid this behavior,drop the legacy job, and replace it with a `DBMS_SCHEDULER` job.

For all new jobs, use `DBMS_SCHEDULER`.

**Parent topic:** Behavior Changes for Oracle Database 19c Upgrade Planning

##### About Standard Edition High Availability

Starting with Oracle Database 19c, you can install Oracle Database Standard Edition 2 in high availability mode.

**Note:**

The ACFS storage option on IBM AIX is deprecated in Oracle Database 19c.

Standard Edition High Availability provides cluster-based failover for single-instance Standard Edition Oracle Databases using Oracle Clusterware.

Oracle Standard Edition High Availability benefits from the cluster capabilities and storage solutions that are already part of Oracle Grid Infrastructure, such as Oracle Clusterware, Oracle Automatic Storage Management (Oracle ASM) and Oracle ASM Cluster File System (Oracle ACFS).

Using integrated, shared, and concurrently mounted storage, such as Oracle ASM and Oracle ACFS for database files as well as for unstructured data, enables Oracle Grid Infrastructure to restart an Oracle Database on a failover node much faster than any cluster solution that relies on failing over and remounting volumes and file systems.

Starting with Oracle Database 19c Release Update (19.7), Standard Edition High Availability is supported on Linux x86-64, Oracle Solaris on SPARC (64-bit), and Microsoft Windows.

Starting with Oracle Database 19c Release Update (19.13), Standard Edition High Availability is supported on IBM AIX on POWER Systems (64-bit) and HP-UX Itanium.

**Note:**

This section is specific to Standard Edition High Availability, which provides cluster-based database failover for Standard Edition Oracle Databases 19c. For more information about high availability options for Oracle Database, see [Oracle Clusterware Administration and Deployment Guide](../cwadd/introduction-to-oracle-clusterware.md).

**Parent topic:** Behavior Changes for Oracle Database 19c Upgrade Planning

##### Manage "Installed but Disabled" Module Bug Fixes with DBMS_OPTIM_BUNDLE

To manage the implementation of Oracle Database bug fixes that cause a SQL execution plan change, use `DBMS_OPTIM_BUNDLE`.

After you upgrade your database, the bug fix patches that can cause execution plan changes included in the Release Updates are installed disabled by default. These bug fixes will not be activated until you enable the fixes. You can either enable these fixes manually, or use the `DBMS_OPTIM_BUNDLE` package.

Oracle strongly recommends that you enable these disabled patches that you want to use in your production system, and run complete workload performance tests using these patches as part of your upgrade test plan.

For more information about using `DBMS_OPTIM_BUNDLE` to enable patches that were disabled because they can change execution plans, see Oracle Database PL/SQL Packages and Types Reference, and My Oracle Support note 2147007.1.

**Related Topics**

- [DBMS_OPTIM_BUNDLE](../arpls/dbms_optim_bundle.md)
- [My Oracle Support Doc ID 2147007.1 Managing "installed but disabled" bug fixes in Database Release Updates using DBMS_OPTIM_BUNDLE](https://support.oracle.com/rs?type=doc&id=2147007.1)

**Parent topic:** Behavior Changes for Oracle Database 19c Upgrade Planning

##### Windows Authentication No Longer Uses NTLM by Default

For Microsoft Windows installations with `AUTHENTICATION_SERVICES=NTS`, in this Oracle Database release, the `SQLNET.NO_NTLM` parameter setting in the `sqlnet.ora` file defaults to `TRUE`, which can cause ORA-12638 errors.

Date: August 2023

In previous releases, the default for `SQLNET.NO_NTLM` was `FALSE`. `SQLNET.NO_NTLM` controls whether `NTLM` can be used with NTS authentication (`AUTHENTICATION_SERVICES=NTS`). A `TRUE` setting means that NTLM cannot be used in NTS authentication. Because NTLM does not normally provide mutual authentication and is hence less secure, a `TRUE` setting for `SQLNET.NO_NTLM` makes the database and client more secure.

The `SQLNET.NO_NTLM` parameter is used on both the server and the client. If you have upgraded a Microsoft Windows installation of Oracle Database, or upgraded a client in which `SQLNET.NO_NTLM` had not been set, then its default will be `TRUE`. In that case, when you have `SQLNET.AUTHENTICATION_SERVICES=NTS` in your `sqlnet.ora`, clients can encounter the error `ORA-12638: Credential retrieval failed`.

If you prefer to use NTLM authentication for certain clients, then set this parameter as required in client-side `sqlnet.ora` files:

    SQLNET.NO_NTLM=FALSE

You must include this setting on both the server and client, and this setting should be the same on both. Ideally, you should ensure that `SQLNET.NO_NTLM` is set to `TRUE`. However, if there is an authentication failure in `extproc`, a virtual account, or a local account on Windows, set the client `SQLNET.NO_NTLM` to `FALSE`, and then retry the login. If you change `SQLNET.NO_NTLM` on the server, then you must restart the database.

**Related Topics**

- [Upgrade Your Database Now - ORA-12638 on Windows only from Oracle 19.10.0 onwards](https://mikedietrichde.com/2021/03/10/ora-12638-on-windows-only-from-oracle-19-10-0-onwards/)
- [Windows : While Connect to Database Getting ORA-12638 After Applying Jan 2021 WINDBBP 19.10.0.0.210119 On Windows 64/32 Bit Database Client (Doc ID 2757734.1)](https://support.oracle.com/rs?type=doc&id=2757734.1)

**Parent topic:** Behavior Changes for Oracle Database 19c Upgrade Planning

#### Desupported Features in Oracle Database 19c

As part of your upgrade plan, review the features that are desupported in Oracle Database 19c.

- Desupport of Oracle Data Provider for .NET Promotable Transaction Setting
  The Oracle Data Provider for .NET `PromotableTransaction` setting is desupported because it is no longer necessary. All compatible database server versions support transaction promotion.
- Desupport of Oracle Multimedia
  Oracle Multimedia is desupported in Oracle Database 19c, and the implementation is removed.
- Desupport of the CONTINUOUS_MINE feature of LogMiner
  The `continuous_mine` option for the `dbms_logmnr.start_logmnr` package is desupported in Oracle Database 19c, and is no longer available.
- Desupport of Extended Datatype Support (EDS)
  The Extended Datatype Support (EDS) feature is desupported in Oracle Database 19c. All Data types that the EDS feature supported are now supported natively by both Logical Standby and Oracle GoldenGate.
- Data Guard Broker MaxConnections Property Desupported
  Starting in Oracle Database 19c, the Oracle Data Guard broker `MAX_CONNECTIONS` attribute is desupported.
- Desupport of Leaf Nodes in Flex Cluster Architecture
  Leaf nodes are no longer supported in the Oracle Flex Cluster Architecture in Oracle Grid Infrastructure 19c.
- Desupport of Oracle Streams
  Starting in Oracle Database 19c (19.1), Oracle Streams is desupported. Oracle GoldenGate is the replication solution for Oracle Database.
- Desupport of PRODUCT_USER_PROFILE Table
  Starting in Oracle Database 19c, the SQL\*Plus table `PRODUCT_USER_PROFILE` (PUP table) is desupported.
- Desupport of Oracle Real Application Clusters for Standard Edition 2 (SE2) Database Edition
  Starting with Oracle Database 19c, Oracle Real Application Clusters (Oracle RAC) is not supported in Oracle Database Standard Edition 2 (SE2).

**Parent topic:** Oracle Database 19c Behavior Changes, Desupports, and Deprecations

##### Desupport of Oracle Data Provider for .NET Promotable Transaction Setting

The Oracle Data Provider for .NET `PromotableTransaction` setting is desupported because it is no longer necessary. All compatible database server versions support transaction promotion.

Date: April 2019

The Oracle Data Provider for .NET registry, configuration, and property setting `PromotableTransaction` indicates whether the application must keep transactions as local, or if it can begin all single connection transactions as local, and then promote the transaction to distributed when a second connection enlists. This is the concept of promotable transactions.

The `PromotableTransaction` setting is desupported in Oracle Data Provider for .NET 18c, because all database versions compatible with this provider version support promotable transactions. Developers no longer need to use this setting if they employ promotable transactions. Existing applications remain unaffected, whether they use promotable transactions or not.

**Parent topic:** Desupported Features in Oracle Database 19c

##### Desupport of Oracle Multimedia

Oracle Multimedia is desupported in Oracle Database 19c, and the implementation is removed.

Date: April 2019

As an alternative for image processing and conversion, Oracle recommends that you store multimedia content in SecureFiles LOBs, and use third party products, such as APEX Media Extension (AME). The `ORDIM` component remains in the registry and still has a `VALID` status. Oracle Multimedia objects and packages remain in the database. However, these objects and packages no longer function, and raise exceptions if there is an attempt made to use them. Oracle Locator is not affected by the desupport of Oracle Multimedia.

**Related Topics**

- <https://www.apexmediaextension.com>

**Parent topic:** Desupported Features in Oracle Database 19c

##### Desupport of the CONTINUOUS_MINE feature of LogMiner

The `continuous_mine` option for the `dbms_logmnr.start_logmnr` package is desupported in Oracle Database 19c, and is no longer available.

Date: April 2019

The `continuous_mine` functionality of the LogMiner package is obsolete. It was deprecated in Oracle Database 12c Release 2 (12.2). There is no replacement functionality.

**Parent topic:** Desupported Features in Oracle Database 19c

##### Desupport of Extended Datatype Support (EDS)

The Extended Datatype Support (EDS) feature is desupported in Oracle Database 19c. All Data types that the EDS feature supported are now supported natively by both Logical Standby and Oracle GoldenGate.

Date: April 2019

The Extended Datatype Support (EDS) feature provides a mechanism for logical standbys to support certain Oracle data types that lack native redo-based support. For example, EDS was used to replicate tables with a `SDO_GEOMETRY` column. However, starting with Oracle Database 12c Release 2 (12.2), there are no EDS-supported Oracle data types that are not supported natively, either by Logical standby, or by Oracle GoldenGate. This feature is desupported with Oracle Database 19c (19.1).

**Parent topic:** Desupported Features in Oracle Database 19c

##### Data Guard Broker MaxConnections Property Desupported

Starting in Oracle Database 19c, the Oracle Data Guard broker `MAX_CONNECTIONS` attribute is desupported.

Date: April 2019

The Oracle Data Guard broker `MaxConnections` property ( pertaining to the `MAX_CONNECTIONS` attribute of the `LOG_ARCHIVE_DEST_``n` parameter) is desupported in Oracle Database 19c. It is removed. Using commands to set this property from DGMGRL returns errors.

**Parent topic:** Desupported Features in Oracle Database 19c

##### Desupport of Leaf Nodes in Flex Cluster Architecture

Leaf nodes are no longer supported in the Oracle Flex Cluster Architecture in Oracle Grid Infrastructure 19c.

Date: April 2019

In Oracle Grid Infrastructure 19c (19.1) and later releases, all nodes in an Oracle Flex Cluster function as hub nodes. The capabilities offered by Leaf nodes in the original implementation of the Oracle Flex Cluster architecture can as easily be served by hub nodes. Therefore, leaf nodes are no longer supported.

**Parent topic:** Desupported Features in Oracle Database 19c

##### Desupport of Oracle Streams

Starting in Oracle Database 19c (19.1), Oracle Streams is desupported. Oracle GoldenGate is the replication solution for Oracle Database.

Date: April 2019

Note that Oracle Database Advanced Queuing is not deprecated, and is fully supported in Oracle Database 19c. Oracle Streams did not support features added in Oracle Database 12c (12.1) and later releases, including the multitenant architecture, `LONG VARCHAR`, and other new features. Oracle Streams replication functionality is superseded by GoldenGate.

**Parent topic:** Desupported Features in Oracle Database 19c

##### Desupport of PRODUCT_USER_PROFILE Table

Starting in Oracle Database 19c, the SQL\*Plus table `PRODUCT_USER_PROFILE` (PUP table) is desupported.

Date: April 2019

The SQL\*Plus product-level security feature is unavailable in Oracle Database 19c. Oracle recommends that you protect data by using Oracle Database settings, so that you ensure consistent security across all client applications.

**Parent topic:** Desupported Features in Oracle Database 19c

##### Desupport of Oracle Real Application Clusters for Standard Edition 2 (SE2) Database Edition

Starting with Oracle Database 19c, Oracle Real Application Clusters (Oracle RAC) is not supported in Oracle Database Standard Edition 2 (SE2).

Date: April 2019

Upgrading Oracle Database Standard Edition databases that use Oracle Real Application Clusters (Oracle RAC) functionality from earlier releases to Oracle Database 19c is not possible. To upgrade those databases to Oracle Database 19c, either remove the Oracle RAC functionality before starting the upgrade, or upgrade from Oracle Database Standard Edition to Oracle Database Enterprise Edition. For more information about each step, including how to reconfigure your system after an upgrade, see My Oracle Support Note 2504078.1: "Desupport of Oracle Real Application Clusters (RAC) with Oracle Database Standard Edition 19c."

**Related Topics**

- [My Oracle Support Document 2504078.1](https://support.oracle.com/rs?type=doc&id=2504078.1)

**Parent topic:** Desupported Features in Oracle Database 19c

#### Desupported Parameters in Oracle Database 19c

As part of your upgrade plan, review the initialization parameters that are not supported starting with Oracle Database 19c.

- EXAFUSION_ENABLED Initialization Parameter Desupported
  The Oracle Exadata Database Machine initialization parameter `EXAFUSION_ENABLED` is desupported in Oracle Database 19c.
- MAX_CONNECTIONS attribute of LOG_ARCHIVE_DEST_n Desupported
  The `MAX_CONNECTIONS` attribute of the `LOG_ARCHIVE_DEST_``n` parameters for Oracle Data Guard Redo Transport is obsolete. It is desupported in Oracle Database 19c.
- Desupport of O7_DICTIONARY_ACCESS
  The initialization parameter `O7_DICTIONARY_ACCESSIBILITY` is desupported in Oracle Database 19c.
- Desupport of OPTIMIZE_PROGRESS_TABLE Parameter
  `OPTIMIZE_PROGRESS_TABLE` for Oracle GoldenGate Integrated Replicat, XStream In, and Logical Standby, is desupported in Oracle Database 19c.

**Parent topic:** Oracle Database 19c Behavior Changes, Desupports, and Deprecations

##### EXAFUSION_ENABLED Initialization Parameter Desupported

The Oracle Exadata Database Machine initialization parameter `EXAFUSION_ENABLED` is desupported in Oracle Database 19c.

Date: April 2019

The Exafusion feature was introduced for Oracle Database 12c Release 1 (12.1.0.2), but disabled by default. It was only available for the Linux operating system, and only available with Oracle Exadata Database Machine. You could enable this feature by setting the `EXAFUSION_ENABLED` initialization parameter to `1`. With Oracle Database 12c Release 2 (12.2), the feature became enabled by default on Oracle Exadata Database Machine running on Oracle Linux. You could disable this feature by changing the `EXAFUSION_ENABLED` parameter setting to `0`. However, with Oracle Database 18c and later releases, the Exafusion feature cannot be disabled. For this reason, the `EXAFUSION_ENABLED` parameter is desupported in Oracle Database 19c, because the parameter no longer serves a function.

**Parent topic:** Desupported Parameters in Oracle Database 19c

##### MAX_CONNECTIONS attribute of LOG_ARCHIVE_DEST\_n Desupported

The `MAX_CONNECTIONS` attribute of the `LOG_ARCHIVE_DEST_``n` parameters for Oracle Data Guard Redo Transport is obsolete. It is desupported in Oracle Database 19c.

Date: April 2019

The `MAX_CONNECTIONS` attribute can interfere with the new Redo Transport Streaming mechanism introduced in Oracle Database 11g, and increase the time necessary to resolve gaps. To prevent these types of errors, Oracle has desupported and removed this attribute.

**Parent topic:** Desupported Parameters in Oracle Database 19c

##### Desupport of O7_DICTIONARY_ACCESS

The initialization parameter `O7_DICTIONARY_ACCESSIBILITY` is desupported in Oracle Database 19c.

Date: November 2019

The `O7_DICTIONARY_ACCESSIBILITY` parameter controlled restrictions on System Privileges from accessing SYS owned objects. It was retained to enable certain backward compatibility for earlier release applications. Desupporting obsolete features enables Oracle to focus on security across all features and functionality. Oracle recommends that you manage system privileges in accordance with standard security best practices.

**Parent topic:** Desupported Parameters in Oracle Database 19c

##### Desupport of OPTIMIZE_PROGRESS_TABLE Parameter

`OPTIMIZE_PROGRESS_TABLE` for Oracle GoldenGate Integrated Replicat, XStream In, and Logical Standby, is desupported in Oracle Database 19c.

Date: September 2020

The apply parameter `OPTIMIZE_PROGRESS_TABLE` for Oracle GoldenGate Integrated Replicat, XStream In, and Logical Standby, is desupported in Oracle Database 19c. Before you upgrade to Oracle Database 19, you must turn off this parameter. If `OPTIMIZE_PROGRESS_TABLE` is set to ON, then stop apply gracefully, turn off the parameter, and restart apply. For GoldenGate Apply and XStream, this parameter is set to `OFF` by default.

**Parent topic:** Desupported Parameters in Oracle Database 19c

#### Deprecated Features in Oracle Database 19c

As part of your upgrade plan, review the features that are deprecated in Oracle Database 19, and review alternatives for your application strategies.

- Deprecation of URL_DATASTORE Text Type
  Starting with Oracle Database 19c, the Oracle Text type `URL_DATASTORE` is deprecated. Use `NETWORK_DATASTORE` instead.
- Deprecation of FILE_DATASTORE Type
  Starting with Oracle Database 19c, the Oracle Text type `FILE_DATASTORE` is deprecated. Use `DIRECTORY_DATASTORE` instead.
- Oracle Data Guard Broker Deprecated Properties
  Starting in Oracle Database 19c, several Oracle Data Guard broker properties associated with initialization parameters are deprecated. Their functionality is replaced with the new `EDIT … SET PARAMETER `command in `DGMGRL`.
- Oracle Data Guard Logical Standby Properties Deprecated
  Starting in Oracle Database 19c, Logical Standby properties of Oracle Data Guard broker are deprecated.
- Deprecation of ASMCMD PWCREATE On Command Line
  Using the Oracle ASM command-line utility `ASMCMD` command option `pwcreate ``password` to create ASM passwords is deprecated in Oracle Grid Infrastructure 19c (19.1).
- Deprecation of Addnode Script
  The `addnode` script is deprecated in Oracle Grid Infrastructure 19c. The functionality of adding nodes to clusters is available in the installer wizard.
- Deprecation of clone.pl Script
  The `clone.pl` script is deprecated in Oracle Database 19c. The functionality of performing a software-only installation, using the gold image, is available in the installer wizard.
- Deprecation of Oracle Fail Safe
  Oracle Fail Safe is deprecated as of Oracle Database 19c. It can be desupported and unavailable in a future release.
- Deprecation of GDSCTL Operating System Command-Line Password Resets
  To enhance security, starting with Oracle Database 19c, the ability to specify passwords from the Global Data Services Control Utility (GDSCTL) command-line when called from the operating system prompt is deprecated.
- Deprecation of Oracle Enterprise Manager Express
  Flash-based Enterprise Manager Express is deprecated in Oracle Database 19c. Starting with Oracle Database 19c, Enterprise Manager Express uses Java JET technology for the user interface.
- Deprecation of DV_REALM_OWNER Role
  The Oracle Database Vault role `DV_REALM_OWNER` role is deprecated with no replacement.
- Deprecation of DV_REALM_RESOURCE Role
  The Oracle Database Vault role `DV_REALM_RESOURCE` is deprecated with no replacement.
- Deprecation of DV_PUBLIC Role
  The Oracle Database Vault role `DV_PUBLIC` role is deprecated with no replacement.
- Deprecation of Oracle ACFS Replication Protocol REPV1
  Starting with Oracle Database 19c (19.3), the Oracle ACFS replication protocol repv1 is deprecated.
- Deprecation of Oracle OLAP
  Analytic workspaces, the OLAP DML programming language, and the OLAP Java API are deprecated in Oracle Database 19c.
- Deprecation of Oracle ACFS Encryption on Solaris and Windows
  Starting with Oracle Database 19c (19.3), Oracle ACFS Encryption is deprecated with no replacement on Oracle Solaris and Microsoft Windows.
- Deprecation of Oracle ACFS on Windows
  Starting with Oracle Grid Infrastructure 19c (19.5), Oracle ASM Cluster File System (ACFS) is deprecated on Microsoft Windows.
- Deprecation of Oracle ACFS Security (Vault) and ACFS Auditing
  Starting with Oracle Grid Infrastructure 19c (19.5), Oracle ASM Cluster File System (ACFS) Security (Vault) and ACFS Auditing are deprecated
- Deprecation of Oracle ACFS on Member Clusters (ACFS Remote)
  Starting with Oracle Grid Infrastructure 19c (19.5), Oracle ASM Cluster File System (ACFS) on Member Clusters (ACFS Remote) is deprecated.
- Deprecation of Cluster Domain - Member Clusters
  Starting with Oracle Grid Infrastructure 19c (19.5), Member Clusters, which are part of the Oracle Cluster Domain architecture, are deprecated.
- Deprecation of Vendor Clusterware Integration with Oracle Clusterware
  Starting with Oracle Clusterware 19c (19.5), the integration of vendor or third party clusterware with Oracle Clusterware is deprecated.
- Deprecation of Black Box Virtual Machine Management Using Oracle Clusterware
  Direct management of virtual machine (VM) resources using Oracle Clusterware is deprecated in Oracle Grid Infrastructure 19c, and can be removed in a future release.
- Deprecation of OPatch and OPatchAuto for Out-of-Place Patching
  Oracle recommended out-of-place patching using Opatch and OPatchAuto, but Oracle is transitioning to a simpler and easier Gold image process for out-of-place patching starting with Oracle Database 23ai On Premises.
- Data Recovery Advisor (DRA) Deprecation
  Starting in Oracle Database 19c, the Data Recovery Advisor (DRA) feature is deprecated.
- DBUA and Manual Upgrade Deprecated
  Oracle recommends using AutoUpgrade for database upgrades.
- Cluster Time Synchronization Service Deprecation
  Cluster Time Synchronization Service (CTSS) is deprecated in Oracle Database 19c. 
- ACFS Deprecation on IBM AIX
  The ACFS storage option on IBM AIX is deprecated in Oracle Database 19c.
- RECOVER…SNAPSHOT TIME Deprecated
  The `RECOVER…SNAPSHOT TIME` method of recovering a database to a point in time using a particular snapshot is deprecated in Oracle Database 19c.
- Oracle Data Masking and Subsetting with Oracle Real Application Testing Deprecated
  The integration of data masking with Oracle Real Application Testing is deprecated in Oracle Database 19c.
- Oracle ASM Filter Driver (ASMFD) Deprecated
  Oracle ASM Filter Driver (ASMFD) is deprecated on both Linux and Oracle Solaris beginning with Oracle Database 19c. It will be desupported in a future release.

**Parent topic:** Oracle Database 19c Behavior Changes, Desupports, and Deprecations

##### Deprecation of URL_DATASTORE Text Type

Starting with Oracle Database 19c, the Oracle Text type `URL_DATASTORE` is deprecated. Use `NETWORK_DATASTORE` instead.

Date: April 2019

The `URL_DATASTORE` type is used for text stored in files on the internet (accessed through HTTP or FTP), and for text stored in local file system files (accessed through the file protocol). It is replaced with `NETWORK_DATASTORE`, which uses ACLs to allow access to specific servers. This change aligns Oracle Text more closely with the standard operating and security model for accessing URLs from the database.

**Parent topic:** Deprecated Features in Oracle Database 19c

##### Deprecation of FILE_DATASTORE Type

Starting with Oracle Database 19c, the Oracle Text type `FILE_DATASTORE` is deprecated. Use `DIRECTORY_DATASTORE` instead.

Date: April 2019

Oracle recommends that you replace `FILE_DATASTORE` text indexes with the `DIRECTORY_DATASTORE` index type, which is available starting with Oracle Database 19c. `DIRECTORY_DATASTORE` provides greater security because it enables file access to be based on directory objects.

**Parent topic:** Deprecated Features in Oracle Database 19c

##### Oracle Data Guard Broker Deprecated Properties

Starting in Oracle Database 19c, several Oracle Data Guard broker properties associated with initialization parameters are deprecated. Their functionality is replaced with the new `EDIT … SET PARAMETER `command in `DGMGRL`.

Date: April 2019

The following Oracle Data Guard broker properties are deprecated in Oracle Database 19c:

- `ArchiveLagTarget`

- `DataGuardSyncLatency`

- `LogArchiveMaxProcesses`

- `LogArchiveMinSucceedDest`

- `LogArchiveTrace`

- `StandbyFileManagement`

- `DbFileNameConvert`

- `LogArchiveFormat`

- `LogFileNameConvert`

Using the current `EDIT ... SET PROPERTY` command with these properties continues to work. However, the update is automatically made with the new command, and the parameter data is now no longer be stored in the broker metadata file.

The `InconsistentProperties` property is also deprecated. This parameter now always has no value, because there can no longer be inconsistent values.

Using the new `EDIT ... SET PARAMETER` commands removes the possibility of inconsistent configuration data between the broker and a database. When you use the new `EDIT...SET PARAMETER` commands, you can change these parameters either by using either the new broker command, or by using the standard SQL\*Plus `ALTER SYSTEM` command. However, when you use the broker command, you can be attached to any database in the configuration, and perform parameter changes to any other database in the configuration.

**Parent topic:** Deprecated Features in Oracle Database 19c

##### Oracle Data Guard Logical Standby Properties Deprecated

Starting in Oracle Database 19c, Logical Standby properties of Oracle Data Guard broker are deprecated.

Date: April 2019

The following Oracle Data Guard broker Properties that affect Logical Standby are deprecated:

- `LsbyMaxEventsRecorded`

- `LsbyMaxServers`

- `LsbyMaxSga`

- `LsbyPreserveCommitOrder`

- `LsbyRecordAppliedDdl`

- `LsbyRecordSkippedDdl`

- `LsbyRecordSkipErrors`

- `LsbyParameter`

Using the `EDIT ... SET PROPERTY` command continues to work. However, the data about the setting is no longer stored in the broker metadata file.  Instead, Oracle recommends that you use the SQL\*Plus package `DBMS_LOGSTDBY` to change the Logical Standby properties. The Logical Standby properties for Oracle Data Guard broker can be desupported in a future release.

Directly using the SQL\*Plus package `DBMS_LOGSTDBY` removes the possibility of inconsistent configuration data between the broker and a Logical Standby database, and provides one interface to manage a Logical Standby.

**Parent topic:** Deprecated Features in Oracle Database 19c

##### Deprecation of ASMCMD PWCREATE On Command Line

Using the Oracle ASM command-line utility `ASMCMD` command option `pwcreate ``password` to create ASM passwords is deprecated in Oracle Grid Infrastructure 19c (19.1).

Date: April 2019

The option to supply the password on the command line is still enabled in Oracle Database 19c. However, to enhance security, Oracle is deprecating this method of creating a new Oracle ASM password. It can be desupported in a future release. The `pwcreate` option of `ASMCMD` enables you to specify a password on the command line. However, if you run the command `asmcmd pwcreate`, and you do not provide the password on the command line, then you are now prompted for the password.

**Parent topic:** Deprecated Features in Oracle Database 19c

##### Deprecation of Addnode Script

The `addnode` script is deprecated in Oracle Grid Infrastructure 19c. The functionality of adding nodes to clusters is available in the installer wizard.

Date: April 2019

The `addnode` script can be removed in a future release. Instead of using the `addnode` script (`addnode.sh` or `addnode.bat`), add nodes by using the installer wizard. The installer wizard provides many enhancements over the `addnode` script. Using the installer wizard simplifies management by consolidating all software lifecycle operations into a single tool.

**Parent topic:** Deprecated Features in Oracle Database 19c

##### Deprecation of clone.pl Script

The `clone.pl` script is deprecated in Oracle Database 19c. The functionality of performing a software-only installation, using the gold image, is available in the installer wizard.

Date: April 2019

The `clone.pl` script can be removed in a future release. Instead of using the `clone.pl` script, Oracle recommends that you install the extracted gold image as a home, using the installer wizard.

**Parent topic:** Deprecated Features in Oracle Database 19c

##### Deprecation of Oracle Fail Safe

Oracle Fail Safe is deprecated as of Oracle Database 19c. It can be desupported and unavailable in a future release.

Date: April 2019

Oracle recommends that you evaluate other single-node failover options, such as Oracle RAC One Node.

**Parent topic:** Deprecated Features in Oracle Database 19c

##### Deprecation of GDSCTL Operating System Command-Line Password Resets

To enhance security, starting with Oracle Database 19c, the ability to specify passwords from the Global Data Services Control Utility (GDSCTL) command-line when called from the operating system prompt is deprecated.

Date: April 2019

This deprecation applies only to password changes where GDSCTL is called from a user command-line prompt. For example, the following command is deprecated.

`$ gdsctl add database -connect inst1 -pwd ``gsm_password`

Specifying the password from the `GDSCTL` utility itself is still valid. For example, the following command is valid:

`GDSCTL> add database -connect inst1 -pwd ``gsm_password`

This deprecation addresses the security vulnerability when specifying passwords in GDSCTL commands called from the operating system prompt. Only enter the Global Data Services password only when GDSCTL prompts for it.

**Parent topic:** Deprecated Features in Oracle Database 19c

##### Deprecation of Oracle Enterprise Manager Express

Flash-based Enterprise Manager Express is deprecated in Oracle Database 19c. Starting with Oracle Database 19c, Enterprise Manager Express uses Java JET technology for the user interface.

Date: April 2019

In accordance with industry standards, Oracle is deprecating Flash-based Oracle Enterprise Manager Express (Oracle EM Express). Starting with Oracle Database 19c, Oracle EM Express, the default management option for Oracle Database, is based on Java JET technology. In this initial release, there are some options available in Flash-based Oracle EM Express that are not available in the JET version. If necessary, use the following command to revert to Flash Oracle EM Express:

    SQL> @?/rdbms/admin/execemx emx

To return to JET Oracle EM Express, use the following command:

    SQL> @?/rdbms/admin/execemx omx

**Parent topic:** Deprecated Features in Oracle Database 19c

##### Deprecation of DV_REALM_OWNER Role

The Oracle Database Vault role `DV_REALM_OWNER` role is deprecated with no replacement.

Date: April 2019

The `DV_REALM_OWNER` role is used for realm management to manage database objects in multiple schemas that define a realm. Oracle has deprecated the use of this role. It can be removed in a future release.

In addition, the following DV_REALM_OWNER privileges are revoked from the `DV_REALM_OWNER` role: `CREATE ROLE`, `ALTER ANY ROLE`, `DROP ANY ROLE`, `GRANT ANY ROLE`, `GRANT ANY PRIVILEGE`, and `GRANT ANY OBJECT PRIVILEGE`. If needed, you can choose to grant these privileges to the `DV_REALM_OWNER` role. For example:

    SQL> GRANT CREATE ROLE ON tablename TO DV_REALM_OWNER;

**Parent topic:** Deprecated Features in Oracle Database 19c

##### Deprecation of DV_REALM_RESOURCE Role

The Oracle Database Vault role `DV_REALM_RESOURCE` is deprecated with no replacement.

Date: April 2019

The `DV_REALM_RESOURCE` role is used for the management of realm resources. Oracle has deprecated the use of this role. It can be removed in a future release.

**Parent topic:** Deprecated Features in Oracle Database 19c

##### Deprecation of DV_PUBLIC Role

The Oracle Database Vault role `DV_PUBLIC` role is deprecated with no replacement.

Date: April 2019

The DV_PUBLIC role is still created during installation, but it is not granted any roles or privileges. All privileges that were granted to DV_PUBLIC in previous releases are now granted directly to the PUBLIC role. This role is obsolete, and can be removed in a future release.

**Parent topic:** Deprecated Features in Oracle Database 19c

##### Deprecation of Oracle ACFS Replication Protocol REPV1

Starting with Oracle Database 19c (19.3), the Oracle ACFS replication protocol repv1 is deprecated.

Date: April 2019

The initial ACFS replication protocol `repv1` was released with Oracle Database 11g Release 2 (11.2). Oracle Database 12c Release 2 introduced a new ACFS replication protocol, Oracle ACFS snapshot-based replication (`repv2`). Oracle continued to use the same management interface. Starting with Oracle Database 19c, the earlier ACFS replication protocol (`repv1`) is deprecated. Update to snapshot-based replication.

**Parent topic:** Deprecated Features in Oracle Database 19c

##### Deprecation of Oracle OLAP

Analytic workspaces, the OLAP DML programming language, and the OLAP Java API are deprecated in Oracle Database 19c.

Date: April 2019

This deprecation is announced in Oracle Database 19c and Oracle Database 21c. For new applications requiring advanced analytic capabilities, Oracle recommends that you consider analytic views (a feature of Oracle Database), or Oracle Essbase. Oracle analytic views are a feature of every Oracle Database edition. If your application uses OLAP for dimensional query and reporting applications, then Oracle recommends that you consider Oracle analytic views as a replacement for OLAP. Analytic views provide a fast and efficient way to create analytic queries of data stored in existing database tables and views. With Oracle analytic views, you obtain a dimensional query model and supporting metadata without requiring a "cube build/update" process. The elimination of the cube build/update process relieves scalability constraints (model complexity and data volume), simplifies the data preparation pipeline, and reduces or eliminates data latency. In addition, you can use analytic views with OLTP applications, external tables, and non-relational data types (for example, JSON) when these non-relational data types are wrapped by relational views.

**Parent topic:** Deprecated Features in Oracle Database 19c

##### Deprecation of Oracle ACFS Encryption on Solaris and Windows

Starting with Oracle Database 19c (19.3), Oracle ACFS Encryption is deprecated with no replacement on Oracle Solaris and Microsoft Windows.

Date: April 2019

Oracle ACFS Encryption on Oracle Solaris and Microsoft Windows is based on RSA technology. Retirement of RSA technology has been announced. Oracle ACFS Encryption continues to be supported on Linux, and is unaffected by this deprecation, because Linux uses an alternative technology.

**Parent topic:** Deprecated Features in Oracle Database 19c

##### Deprecation of Oracle ACFS on Windows

Starting with Oracle Grid Infrastructure 19c (19.5), Oracle ASM Cluster File System (ACFS) is deprecated on Microsoft Windows.

Date: October 2019

Deprecating certain clustering features with limited adoption allows Oracle to focus on improving core scaling, availability, and manageability across all features and functionality. ACFS file systems on Microsoft Windows are deprecated, and can be desupported in a future release. Depending on the use case, to replace current ACFS file systems, Oracle recommends that you move to Oracle Automatic Storage Management (Oracle ASM), Oracle Database File System (DBFS), or Microsoft Windows shares.

**Parent topic:** Deprecated Features in Oracle Database 19c

##### Deprecation of Oracle ACFS Security (Vault) and ACFS Auditing

Starting with Oracle Grid Infrastructure 19c (19.5), Oracle ASM Cluster File System (ACFS) Security (Vault) and ACFS Auditing are deprecated

Date: October 2019

Deprecating certain clustering features with limited adoption allows Oracle to focus on improving core scaling, availability, and manageability across all features and functionality. Oracle ACFS Security (Vault) and ACFS Auditing are deprecated, and can be desupported in a future release.

**Parent topic:** Deprecated Features in Oracle Database 19c

##### Deprecation of Oracle ACFS on Member Clusters (ACFS Remote)

Starting with Oracle Grid Infrastructure 19c (19.5), Oracle ASM Cluster File System (ACFS) on Member Clusters (ACFS Remote) is deprecated.

Date: October 2019

Oracle ASM Cluster File System (ACFS) on Member Clusters (ACFS Remote) is deprecated, and can be removed in a future release. Deprecating certain clustering features with limited adoption allows Oracle to focus on improving core scaling, availability, and manageability across all features and functionality.

**Parent topic:** Deprecated Features in Oracle Database 19c

##### Deprecation of Cluster Domain - Member Clusters

Starting with Oracle Grid Infrastructure 19c (19.5), Member Clusters, which are part of the Oracle Cluster Domain architecture, are deprecated.

Date: October 2019

Deprecating certain clustering features with limited adoption allows Oracle to focus on improving core scaling, availability, and manageability across all features and functionality. Oracle Cluster Domains consist of a Domain Services Cluster (DSC) and Member Clusters. The deprecation of Member Clusters affects the clustering used with the DSC, but not its ability to host services for other production clusters. Oracle recommends that you align your next software or hardware upgrade with the transition off Cluster Domain - Member Clusters.

**Parent topic:** Deprecated Features in Oracle Database 19c

##### Deprecation of Vendor Clusterware Integration with Oracle Clusterware

Starting with Oracle Clusterware 19c (19.5), the integration of vendor or third party clusterware with Oracle Clusterware is deprecated.

Date: October 2019

The integration of vendor clusterware with Oracle Clusterware is deprecated, and can be desupported in a future release. Deprecating certain clustering features with limited adoption allows Oracle to focus on improving core scaling, availability, and manageability across all features and functionality. In the absence of an integration between different cluster solutions, the system is subject to the dueling cluster solutions issue: Independent cluster solutions can make individual decisions about which corrective actions must be taken in case of certain failures. To avoid conflicts, only one cluster solution should be active at any point in time. For this reason, Oracle recommends that you align your next software or hardware upgrade with the transition off of vendor cluster solutions. This deprecation applies to clustered deployments, including Oracle Real Application Clusters and Oracle RAC One Node.

**Parent topic:** Deprecated Features in Oracle Database 19c

##### Deprecation of Black Box Virtual Machine Management Using Oracle Clusterware

Direct management of virtual machine (VM) resources using Oracle Clusterware is deprecated in Oracle Grid Infrastructure 19c, and can be removed in a future release.

Date: May 2020

Oracle continues to support the use of Oracle Clusterware to monitor and manage the availability of remotely deployed Oracle VMs. However, this support will be removed in an upcoming release.

**Parent topic:** Deprecated Features in Oracle Database 19c

##### Deprecation of OPatch and OPatchAuto for Out-of-Place Patching

Oracle recommended out-of-place patching using Opatch and OPatchAuto, but Oracle is transitioning to a simpler and easier Gold image process for out-of-place patching starting with Oracle Database 23ai On Premises.

Date: May 2023

Oracle continues to recommend out-of-place patching for the Oracle Database and Oracle Grid Infrastructure homes for Oracle Database 19c and 21c. However, Oracle is transitioning to a streamlined process that uses Gold Images for out-of-place patching of Oracle Database. In addition, Oracle also provides the fully automated Fleet Patching and Provisioning solution for patching your software. Accordingly, Oracle is announcing the deprecation of using Opatch and OpatchAuto for out-of-place patching. This deprecation does not affect in-place patching.

For Oracle Grid Infrastructure, Oracle recommends that you use `gridSetup.sh` with the `switchGridHomes` option. For standalone database homes, Oracle recommends that you use a fresh installation, and perform an out-of-place patch using Oracle Universal Installer with the `applyRU` and `applyOneOffs` options. You can then patch your databases either with AutoUpgrade, or with Fleet Patching and Provisioning, which automates the entire patch process for you.

**Parent topic:** Deprecated Features in Oracle Database 19c

##### Data Recovery Advisor (DRA) Deprecation

Starting in Oracle Database 19c, the Data Recovery Advisor (DRA) feature is deprecated.

Date: July 2023

The deprecation of DRA includes deprecation of the following Oracle Recovery Manager (RMAN) commands: `LIST FAILURE`, `ADVISE FAILURE`, `REPAIR FAILURE`, and `CHANGE FAILURE`. Database administrators will no longer have access to these commands. There is no replacement feature for DRA.

**Parent topic:** Deprecated Features in Oracle Database 19c

##### DBUA and Manual Upgrade Deprecated

Oracle recommends using AutoUpgrade for database upgrades.

Date: July 2023

To improve the reliability and support for Oracle Database upgrades, Oracle is deprecating Database Upgrade Assistant (DBUA), and manual upgrades using the Parallel Upgrade Utility (`catctl.pl`) , and the database upgrade scripts `dbupgrade` and `dbupgrade.cmd` in Oracle Database 19c. Use AutoUpgrade for Oracle Database upgrades. These obsolete upgrade methods can be removed in a future release update. Deprecating obsolete upgrade methods enables Oracle to focus on improving and extending the features and manageability of the AutoUpgrade utility.

**Parent topic:** Deprecated Features in Oracle Database 19c

##### Cluster Time Synchronization Service Deprecation

Cluster Time Synchronization Service (CTSS) is deprecated in Oracle Database 19c. 

Date: January 2024

To synchronize time between cluster member nodes, use either an operating system configured network time protocol such as `ntp` or `chrony`, or Microsoft Windows Time service. To verify that you have network time synchronization configured, you can use the `cluvfy comp clocksync -n all` command.

**Parent topic:** Deprecated Features in Oracle Database 19c

##### ACFS Deprecation on IBM AIX

The ACFS storage option on IBM AIX is deprecated in Oracle Database 19c.

Date: December 2024

To align the support for the IBM AIX platform, Oracle Automatic Storage Management Cluster File System (ACFS) on IBM AIX (called Oracle Advanced Cluster File System starting with Oracle Database 21c) is deprecated in Oracle Database 19c. For data or files currently stored on an ACFS file system that cannot be stored in the Oracle database, the IBM General Parallel File System (GPFS) can be used.

**Parent topic:** Deprecated Features in Oracle Database 19c

##### RECOVER…SNAPSHOT TIME Deprecated

The `RECOVER…SNAPSHOT TIME` method of recovering a database to a point in time using a particular snapshot is deprecated in Oracle Database 19c.

Date: February 2024

Instead of `RECOVER…SNAPSHOT TIME`, Oracle recommends that you use `ALTER DATABASE BEGIN/END BACKUP` before and after creating the storage snapshot of the data files and then use `RECOVER .. UNTIL TIME` to a specific timestamp or system change number (SCN) after the `END BACKUP` completion time. Oracle recommends that `ALTER DATABASE BEGIN/END BACKUP` always be used when performing snapshots on a running database to ensure data recovery integrity. Archived log redo logs must be separately backed up and restored for recovery operations.

Note that Oracle’s best practice for database backup and recovery is to use Recovery Manager (RMAN) only, not storage snapshots, and is integrated with Zero Data Loss Recovery Appliance (ZDLRA) to offer the highest levels of database protection.

**Related Topics**

- [IT Infrastructure Engineered Systems Zero Data Loss Recovery Appliance](https://www.oracle.com/engineered-systems/zero-data-loss-recovery-appliance/)

**Parent topic:** Deprecated Features in Oracle Database 19c

##### Oracle Data Masking and Subsetting with Oracle Real Application Testing Deprecated

The integration of data masking with Oracle Real Application Testing is deprecated in Oracle Database 19c.

Date: February 2024

For testing, Oracle recommends that you keep the test database in the production realm for security, but create user accounts for testing that cannot access your data to run both SQL Performance Analyzer (SPA) trials and Database Replay.

**Parent topic:** Deprecated Features in Oracle Database 19c

##### Oracle ASM Filter Driver (ASMFD) Deprecated

Oracle ASM Filter Driver (ASMFD) is deprecated on both Linux and Oracle Solaris beginning with Oracle Database 19c. It will be desupported in a future release.

Date: March 2025

On Linux systems running kernel 5.14 or higher (including Oracle Linux, RedHat Enterprise Linux, and SUSE Linux Enterprise Server), ASMFD filtering is already disabled and will not be supported going forward. Oracle recommends moving to ASMlib v3 for those environments, as it provides equivalent functionality. For details, see My Oracle Support Note Document 2806979.1. Migration steps are available. On Oracle Solaris, ASMFD is deprecated, but remains fully supported. No immediate action is required until a formal desupport notice is issued.

**Related Topics**

- [Oracle Automatic Storage Management Filter Driver (ASMFD) (Doc ID 2806979.1)](https://support.oracle.com/rs?type=doc&id=2806979.1)

**Parent topic:** Deprecated Features in Oracle Database 19c

#### Deprecated Initialization Parameters in Oracle Database 19c

As part of your upgrade plan, review the initialization parameters that are deprecated in Oracle Database 19c.

- CLUSTER_DATABASE_INSTANCES Initialization Parameter Deprecated
  The Oracle Database initialization parameter `CLUSTER_DATABASE_INSTANCES` is deprecated in Oracle Database 19c (19.1)
- Deprecation of SQLNET.ENCRYPTION_WALLET_LOCATION Parameter
  The SQLNET.ENCRYPTION_WALLET_LOCATION `sqlnet.ora` parameter is deprecated in Oracle Database 19c.
- Deprecation of the SERVICE_NAMES Initialization Parameter
  Starting with Oracle Database 19c, customer use of the `SERVICE_NAMES` parameter is deprecated. It can be desupported in a future release.

**Parent topic:** Oracle Database 19c Behavior Changes, Desupports, and Deprecations

##### CLUSTER_DATABASE_INSTANCES Initialization Parameter Deprecated

The Oracle Database initialization parameter `CLUSTER_DATABASE_INSTANCES` is deprecated in Oracle Database 19c (19.1)

Date: April 2019

The `init.ora` parameter `CLUSTER_DATABASE_INSTANCES` specifies the number of configured Oracle Real Application Clusters (Oracle RAC) instances. Starting with Oracle Database 19c and later releases, the number of configurable Oracle RAC instances is derived automatically from the Oracle Clusterware resource definitions. There is no replacement for this parameter, because there is no longer a reason to have this parameter.

**Parent topic:** Deprecated Initialization Parameters in Oracle Database 19c

##### Deprecation of SQLNET.ENCRYPTION_WALLET_LOCATION Parameter

The SQLNET.ENCRYPTION_WALLET_LOCATION `sqlnet.ora` parameter is deprecated in Oracle Database 19c.

Date: April 2019

The `SQLNET.ENCRYPTION_WALLET_LOCATION` parameter defines the location of the software keystores for Transparent Data Encryption (TDE). To configure the software keystore location, instead of setting `SQLNET.ENCRYPTION_WALLET_LOCATION`, Oracle recommends that you set the `WALLET_ROOT` initialization parameter, and the `TDE_CONFIGURATION` dynamic initialization parameter.

Oracle recommends that you use the WALLET_ROOT instance initialization parameter as soon as possible, because the value is read once at instance startup time, so all sessions and server background processes share the same path after startup. If the `SQLNET.ENCRYPTION_WALLET_LOCATION` parameter is used, then it can lead to confusing misconfigurations, because different sessions can have different SQLNET parameter values. Another reason to use `WALLET_ROOT` is that it is the directory within which you can locate the wallets of other features, such as Oracle Enterprise User Security, and Transport Layer Security. This location can become the principal location for all server-side wallets.

**Related Topics**

- [Oracle Database Advanced Security Guide](../asoag/configuring-transparent-data-encryption.md)

**Parent topic:** Deprecated Initialization Parameters in Oracle Database 19c

##### Deprecation of the SERVICE_NAMES Initialization Parameter

Starting with Oracle Database 19c, customer use of the `SERVICE_NAMES` parameter is deprecated. It can be desupported in a future release.

Date: November 2019

The use of the `SERVICE_NAMES` parameter is no longer actively supported. It must not be used for high availability (HA) deployments. It is not supported to use service names parameter for any HA operations. This restriction includes FAN, load balancing, `FAILOVER_TYPE`, `FAILOVER_RESTORE`, `SESSION_STATE_CONSISTENCY`, and any other uses.

To manage your services, Oracle recommends that you use the `SRVCTL` or `GDSCTL` command line utilities, or the `DBMS_SERVICE` package.

**Parent topic:** Deprecated Initialization Parameters in Oracle Database 19c

### Oracle Database 18c Behavior Changes, Desupports, and Deprecations

Review for descriptions of Oracle Database 18c release changes.

- Behavior Changes for Oracle Database 18c Upgrade Planning
  Review these behavior changes to help plan for upgrades to Oracle Database 18c
- Desupported Features in Oracle Database 18c
  Review this list of desupported features as part of your upgrade planning.
- Desupported Initialization Parameters in Oracle Database 18c
  Review this list of desupported initialization parameters for changes and replacements in parameter settings in this release.
- Terminal Release of Oracle Streams
  Oracle Database 18c is the terminal release for Oracle Streams support. Oracle Streams will be desupported from Oracle Database 19c onwards.
- Deprecated Features in Oracle Database 18c
  Review the deprecated features listed in this section to prepare to use alternatives after you upgrade.

**Parent topic:** Oracle Database Changes, Desupports, and Deprecations

#### Behavior Changes for Oracle Database 18c Upgrade Planning

Review these behavior changes to help plan for upgrades to Oracle Database 18c

- Simplified Image-Based Oracle Database Installation
  Starting with Oracle Database 18c, installation and configuration of Oracle Database software is simplified with image-based installation.
- Support Indexing of JSON Key Names Longer Than 64 Characters
  If you use JSON keys, then you can take advantage of increased efficiency of searching JSON documents generated from HASH MAP-like structures by using longer key names.
- Upgrading Existing Databases is Replaced With Image Installations
  Starting with Oracle Database 18c, existing services are no longer migrated by the installation. Use Database Upgrade Assistant (DBUA) to migrate services.
- About RPM-Based Oracle Database Installation
  Starting with Oracle Database 18c, you can install a single-instance Oracle Database or an Oracle Database Instant Client software using RPM packages.
- Token Limitations for Oracle Text Indexes
  Starting with Oracle Database Release 18c, the indexed token maximum size is increased to 255 characters for single-byte character sets.
- Changes to /ALL/USER/DBA User View and PL/SQL External Libraries
  Starting in Oracle Database 18c, there are changes to the `/USER/ALL/DBA_ARGUMENTS` and `/USER/ALL/DBA_IDENTIFIERS` views, and to `LIBRARY` object creation in PDBs.
- Symbolic Links and UTL_FILE
  You cannot use `UTL_FILE` with symbolic links. Use directory objects instead.
- Deprecation of Direct Registration of Listeners with DBCA
  Using Database Configuration Assistant (DBCA) to register Oracle Database to Oracle Internet Directory (OID) is deprecated in Oracle Database 18c.
- UNIFORM_LOG_TIMESTAMP_FORMAT Changes in INIT.ORA
  By default, the format of timestamps is different in Oracle Database 12c release 2 (12.2) and later releases. To view alert logs, use the Oracle Database utility Automatic Diagnostic Repository Command Interpreter (ADRCI) utility.

**Parent topic:** Oracle Database 18c Behavior Changes, Desupports, and Deprecations

##### Simplified Image-Based Oracle Database Installation

Starting with Oracle Database 18c, installation and configuration of Oracle Database software is simplified with image-based installation.

Starting with Oracle Database 18c, the Oracle Database software is available as an image file for download and installation. You must extract the image software into the directory where you want your Oracle home to be located, and then run the `runInstaller` script to start the Oracle Database installation. For details, refer to your operating system platform Oracle Database Installation Guide.

**Note:**

You must extract the image software (`db_home.zip`) into the directory where you want your Oracle Database home to be located, and then run the `runInstaller` script to start the Oracle Database installation and configuration. Oracle recommends that the Oracle home directory path you create is in compliance with the Oracle Optimal Flexible Architecture recommendations.

**Related Topics**

- [Oracle Database Installation Guide](../install-and-upgrade.md)

**Parent topic:** Behavior Changes for Oracle Database 18c Upgrade Planning

##### Support Indexing of JSON Key Names Longer Than 64 Characters

If you use JSON keys, then you can take advantage of increased efficiency of searching JSON documents generated from HASH MAP-like structures by using longer key names.

The upper limit is increased for JSON key names that can be indexed by the JSON Search index. The JSON key name upper limit in Oracle Database 12c Release 2 (12.2.0.2) and later releases is 255 bytes. In previous releases, JSON search indexes that were created did not index key names greater than 64 bytes.

**Parent topic:** Behavior Changes for Oracle Database 18c Upgrade Planning

##### Upgrading Existing Databases is Replaced With Image Installations

Starting with Oracle Database 18c, existing services are no longer migrated by the installation. Use Database Upgrade Assistant (DBUA) to migrate services.

If you have an existing Oracle Database with services that you want to migrate, then to migrate those services, you must install the new release Oracle Database software in the Oracle home, and then start DBUA.

On Windows, to migrate the Microsoft Transaction Service to the new Oracle home, you must also run the command `%ORACLE_HOME%\bin\oramtsctl.exe -new`

**Parent topic:** Behavior Changes for Oracle Database 18c Upgrade Planning

##### About RPM-Based Oracle Database Installation

Starting with Oracle Database 18c, you can install a single-instance Oracle Database or an Oracle Database Instant Client software using RPM packages.

An RPM-based installation performs preinstallation checks, extracts the database software, reassigns ownership of the extracted software to the preconfigured user and groups, maintains the Oracle inventory, and runs all root operations required to configure the Oracle Database software for a single-instance Oracle Database creation and configuration.

The RPM–based installation process detects when the minimum requirements for an installation are not met and prompts you to finish these minimum preinstallation requirements.

An RPM-based installation performs a software-only Oracle Database installation and creates an Oracle home. After the Oracle home is created, you can then use Oracle Database Configuration Assistant (Oracle DBCA) to create an Oracle Database.

The RPM-based installation process provides you with the option to create a database with the default settings using the `/etc/init.d/oracledb_ORCLCDB-19c` service configuration script.

**Parent topic:** Behavior Changes for Oracle Database 18c Upgrade Planning

##### Token Limitations for Oracle Text Indexes

Starting with Oracle Database Release 18c, the indexed token maximum size is increased to 255 characters for single-byte character sets.

Before Oracle Database Release 18c, all Oracle Text index types except `SDATA` sections stored tokens in a table column of type `VARCHAR2` (64 BYTE). Starting with Oracle Database Release 18c, all Oracle Text index types except `CTXCAT` and `CTXRULE` indexes store tokens in `VARCHAR2` (255 BYTE) table column types. This change is an increase for the maximum size of an indexed token to 255 characters for single-byte character sets. The size increase is less with multibyte or variable-length character sets. Tokens longer than 255 bytes are truncated. Truncated tokens do not prevent searches on the whole token string. However, the system cannot distinguish between two tokens that have the same first 255 bytes.

**Note:**

Before Oracle Database Release 18c, tokens that were greater than 64 bytes were truncated to 64 bytes. After upgrading to Oracle Database Release 18c, the token tables are increased to 255 bytes from 64 bytes. Searches with more than 64 bytes in the search token (that is, any single word in search string) cannot find any tokens which were truncated to 64 bytes. To avoid this problem, rebuild the index. If you never use search tokens longer than 64 bytes, it is not necessary to rebuild the index.

`SDATA` sections store tokens in a table column of type `VARCHAR2` (249 BYTE). `CTXCAT` and `CTXRULE` indexes store tokens in a table column of type `VARCHAR2` (64 BYTE).

**Parent topic:** Behavior Changes for Oracle Database 18c Upgrade Planning

##### Changes to /ALL/USER/DBA User View and PL/SQL External Libraries

Starting in Oracle Database 18c, there are changes to the `/USER/ALL/DBA_ARGUMENTS` and `/USER/ALL/DBA_IDENTIFIERS` views, and to `LIBRARY` object creation in PDBs.

Review the changes that can affect your work.

##### ALL/USER/DBA_ARGUMENTS User Views Changes

`ARGUMENTS` views contain fewer rows. In particular, only top-level (`DATA_LEVEL=0`) items are stored in the `ARGUMENTS` views.

In earlier Oracle Database releases, the PL/SQL compiler collected metadata for all nested types in a PL/SQL datatype. `DATA_LEVEL` represented the nesting level of the type. Starting in Oracle Database 18c, only top-level type metadata (`DATA_LEVEL=0`) is stored in the `ARGUMENTS` views.

For instance: Note the changes in the create-or-replace package `NestedTypesExample`:

    Type Level2Record is RECORD (Field1 NUMBER);
    Type Level1Collection is TABLE of Level2Record index by binary_integer;
    Type Level0Record is RECORD (Field1 Level1Collection);
    Procedure NestedTypesProc (Param1 Level0Record);

In previous Oracle Database releases, the top-level type of the `NestedTypeProc` procedure, `parameter Param1, Level0Record`, is returned, and also an expanded description of all the nested types within `Level0Record`. For example:

    SQL> select argument_name,type_subname,position,sequence,data_level from user_arguments where object_name='NESTEDTYPESPROC';
    ARGUMENT_NAME   TYPE_SUBNAME      POSITION   SEQUENCE  DATA_LEVEL
    --------------- ----------------- ---------- ---------- ---------
    PARAM1          LEVEL0RECORD             1          1           0
    FIELD1          LEVEL1COLLECTION         1          2           1
                    LEVEL2RECORD             1          3           2
    FIELD1                                   1          4           3

In contrast, the same query in an 18.1 database returns the following:

    ARGUMENT_NAME   TYPE_SUBNAME      POSITION   SEQUENCE  DATA_LEVEL
    --------------- ----------------- ---------- ---------- ---------
    PARAM1          LEVEL0RECORD             1          1           0

In releases earlier than Oracle Database 12c (12.1), PL/SQL package type descriptive metadata was not accessible in the way that metadata is accessible for top-level object types. With Top-level object types and collections, you can query `ALL_TYPES` and the associated user views, `ALL_TYPE_ATTRS`, and `ALL_COLL_TYPES`, to obtain type metadata. However, before Oracle Database 12.1, there was no way to obtain type metadata for PL/SQL package types, such as records and packaged collections. Function or procedure parameters that referenced those PL/SQL package types resulted in publishing all metadata about these types in the ARGUMENTS views, including any nested types.

The problem with this approach is that deeply nested types can consume extensive memory in the SYS tablespace. Also, because there is no way to share the type metadata in the ARGUMENTS views, each parameter with deeply nested types required its own redundant copy of the type metadata. The amount of metadata in the `ARGUMENTS` views and `SYS` tablespace, can lead to various issues, including PL/SQL compiler performance degradation. The degradation is caused because of the time it takes PL/SQL to update rows in the underlying dictionary tables.

In the Oracle Database 12.1 release, PL/SQL introduced enhanced support for package types, including the new user views, `ALL_PLSQL_TYPES`, `ALL_PLSQL_TYPE_ATTRS`, and `ALL_PLSQL_COLL_TYPES`. As the names imply, these views are similar to the `ALL_TYPES` view family. However, you can use the enhanced PL/SQL type views to query metadata about PL/SQL package types, instead of top-level object and collection types.

Because of the package types added with Oracle Database 12.1, there is no longer a need to insert large amounts of descriptive metadata into the ARGUMENTS views. A single row of metadata that includes the type name is all that is required in the ARGUMENTS views for each parameter type. You can obtain a full description of the type name in a query against the PL/SQL type views, and any nested types.

`OCIDescribeAny()` is based on the same metadata used by the `ARGUMENTS` views. `OCIDescribeAny()` also returns a single row for each parameter type, instead of the multiple rows commonly returned before the change in Oracle Database 12.1.

`ALL/DBA/USER_ARGUMENTS` contains a new column type, `TYPE_OBJECT_TYPE`. To determine the type of the type described by `TYPE_OWNER`, `TYPE_NAME` and `TYPE_SUBNAME`, you use the `TYPE_OBJECT_TYPE` column. The possible values include `TABLE`, `VIEW`, `PACKAGE`, and `TYPE`.

If you prefer to continue to collect the `ALL_TYPES` and the associated user views, `ALL_TYPE_ATTRS` and ALL_COLL_TYPES in ARGUMENTS views, then you can set events to `events='10946, level 65536'`. Setting this event reverts the `ARGUMENTS` views back to the behavior in Oracle Database releases earlier than 12.1, in which DATA_LEVEL can be greater than `0`, and descriptive metadata for the type and any nested types is included in the view. If you make this change, then you must recompile affected packages after you set the event. When you recompile the affected packages, the compiler recollects the additional metadata. This event also reverts `OCIDescribeAny()` to the behavior in Oracle Database releases earlier than 12.1.

Starting in Oracle Database 12c release 1 (12.1.0.2), if you enter a procedure with no arguments, then the `ARGUMENTS` views do not have any rows. This change is an additional change that is separate from the row reduction change to `ARGUMENTS` views. Before Oracle Database 12.1.0.2, a procedure with no arguments was presented as a single row in the `ARGUMENTS` views.

##### USER/ALL/DBA_IDENTIFIERS User View Changes

Starting with Oracle Database 18c, PL/Scope is enhanced to capture additional information about user identifiers in PL/SQL code. The additional information includes constraints placed on the identifiers, and an indicator that notes when a function is a SQL builtin in PL/SQL.

The following columns are new in the USER/ALL/DBA_IDENTIFIERS views in Oracle Database 18c:

- `CHARACTER_SET`: This column contains the value of the character set clause, when the column is used in a variable identifier declaration. The possible values are `CHAR_CS`, `NCHAR_CS`, and `IDENTIFIER`, when the character set is derived from another variable identifier.

- `ATTRIBUTE`: This column contains the attribute value when `%``attribute` is used in a variable declaration. The possible values are `ROWTYPE`, `TYPE`, and `CHARSET`.

- `CHAR_USED`: This column contains the type of the length constraint when a constraint is used in a string length constraint declaration. The possible values are `CHAR` and `BYTE`.

- `LENGTH`: This column contains the numeric length constraint value for a string length constraint declaration.

- `PRECISION`: This column contains the numeric precision when it is used in a variable declaration.

- `PRECISION2`: This column contains the numeric second precision value (for instance, interval types) used in a variable declaration.

- `SCALE`: This column contains the numeric scale value used in a variable declaration.

- `LOWER_RANGE`: This column contains the numeric lower range value used by a variable declaration with a range constraint.

- `UPPER_RANGE`: This column contains the numeric upper range value used by a variable declaration with a range constraint.

- `NULL_CONSTRAINT`: When a `NULL` constraint is used by a variable declaration, this column is set. The possible values are `NULL`, or `NOT NULL`.

- `SQL_BUILTIN`: When an identifier is a SQL builtin used in a SQL statement issued from PL/SQL, this column is set to `YES`. If the identifier is not a SQL builtin, then the column is set to `NO`.

##### PL/SQL EXTERNAL LIBRARY Changes

Starting with Oracle Database 18c, the methods change for how to create LIBRARY objects in an Oracle Database 18c PDB with a pre-defined `PATH_PREFIX`.

- When you create a new `LIBRARY` object in a PDB that has a predefined `PATH_PREFIX`, the `LIBRARY` must use a `DIRECTORY` object. The `DIRECTORY` object enforces the rules of `PATH_PREFIX` for the `LIBRARY` object. Failure to use a `DIRECTORY` object in the `LIBRARY` object results in a `PLS-1919` compile-time error.

- If a database is plugged into a CDB as a PDB with a predefined `PATH_PREFIX`, then attempts to use a `LIBRARY` object that does not use a DIRECTORY object result in an `ORA-65394` runtime error. The `LIBRARY` object is not invalidated. However, to make the `LIBRARY` useful (as opposed to always issuing a runtime error), you must recreate the `LIBRARY` object so that it uses a `DIRECTORY` object.

These changes enhance the security and manageability of `LIBRARY` objects in a PDB by accounting for the value of the `PATH_PREFIX`, which describes where the `LIBRARY` dynamic link library (DLL) can appear in the file system. The use of a DIRECTORY object also allows administrators to determine which users can access the DLL directory.

**Parent topic:** Behavior Changes for Oracle Database 18c Upgrade Planning

##### Symbolic Links and UTL_FILE

You cannot use `UTL_FILE` with symbolic links. Use directory objects instead.

The `UTL_FILE_DIR` symbolic link path is desupported in Oracle Database 18c and later releases. After an upgrade if applications address the database using symbolic links through `UTL_FILE`, then these links fail. Oracle recommends that you use directory objects. If necessary, you can create real files that are the targets of file names in `UTL_FILE`.

This desupport can affect any feature from an earlier release using symbolic links, including (but not restricted to) Oracle Data Pump, `BFILE`s, and External Tables. If you attempt to use an affected feature after upgrade, where that feature used symbolic links, you encounter `ORA-29283: invalid file operation: path traverses a symlink`. Before upgrade, to help you to identify symbolic link that you need to correct, run AutoUpgrade in `analyze` mode. Oracle recommends that you instead use directory objects in place of symbolic links.

Example 10-1 Example of Error Messages with UTL_FILE And Symbolic Links

Applications that use symbolic links that address UTL_FILE encounter an error. For example. suppose you attempt to create a symbolic link, where `Ia.c` is a symbolic link file:

    create or replace directory TEMP as '/home/PLSQL/TEMP';

    declare
    f utl_file.file_type;
    begin
    f := utl_file.fopen('TEMP','la.c','r');
    end;
    /

This command fails with the following errors:

    ERROR at line 1:
    ORA-29283: invalid file operation
    ORA-06512: at "SYS.UTL_FILE", line 536
    ORA-29283: invalid file operation
    ORA-06512: at line 4

**Parent topic:** Behavior Changes for Oracle Database 18c Upgrade Planning

##### Deprecation of Direct Registration of Listeners with DBCA

Using Database Configuration Assistant (DBCA) to register Oracle Database to Oracle Internet Directory (OID) is deprecated in Oracle Database 18c.

Instead of using DBCA to migrate or register listeners to a database home during an upgrade, use Net Configuration Assistant or Net Manager to create a LISTENER.ORA file for the new release Oracle home, and then start this listener. You can also use DBCA to de-register and register listeners again to OID.

**Parent topic:** Behavior Changes for Oracle Database 18c Upgrade Planning

##### UNIFORM_LOG_TIMESTAMP_FORMAT Changes in INIT.ORA

By default, the format of timestamps is different in Oracle Database 12c release 2 (12.2) and later releases. To view alert logs, use the Oracle Database utility Automatic Diagnostic Repository Command Interpreter (ADRCI) utility.

If you use scripts to parse the alert log for timestamp dates, then be aware that the default value for timestamp formats is set by the `init.ora` parameter UNIFORM_LOG_TIMESTAMP_FORMAT. The default value for this parameter is TRUE. When TRUE, the timestamp format changes from a day-month-year-time format to a year-month-day-time format. For example: `2017-05-17T10:00:54.799968+00:00`.

You can change to the timestamp format used in previous releases by changing the value of UNIFORM_LOG_TIMESTAMP_FORMAT to FALSE. You can also use scripts to parse `log.xml` instead of the alert log.

Oracle provides a dedicated command-line utility to find and analyze Oracle errors and tracefiles, called Automatic Diagnostic Repository Command Interpreter (ADRCI) Oracle recommends that you use the ADRCI utility for error management.

For example, you can use the ADRCI command `show alert` to view the alert log:

    $ oracle@user> adrci
    adrci> show alert -tail -f

ADRCI also enables you to use the `show log` command to pass predicates for a query. For example:

    adrci> show log -p "message_text like '%tablespace%'"

Refer to Oracle Database Utilities for more information about how to use the ADRCI utility.

**Related Topics**

- [Oracle Database Utilities](../sutil/oracle-adr-command-interpreter-adrci.md)

**Parent topic:** Behavior Changes for Oracle Database 18c Upgrade Planning

#### Desupported Features in Oracle Database 18c

Review this list of desupported features as part of your upgrade planning.

- Oracle Administration Assistant for Windows is Desupported
  The Oracle Administration Assistant tool for Windows is desupported in Oracle Database 18c.
- Oracle Multimedia DICOM Desupported Features
  Several Oracle Multimedia DICOM features are desupported in Oracle Database 18c. Replace DICOM with Oracle SecureFiles and third-party DICOM products.
- Oracle Multimedia Java Client Classes Desupported
  Oracle Multimedia proxy classes and Oracle Multimedia servlet and JSP classes are desupported.
- Oracle XML DB Desupported Features
  Starting withOracle Database 18c, schema subprograms in `DBMS_XMLSCHEMA`, many `DBMS_XDB` subprograms, and many other Oracle XML DB schema features are desupported.
- ODP.NET, Managed Driver - Distributed Transaction DLL Desupported
  Oracle is desupporting the `Oracle.ManagedDataAccessDTC.dll` file in Oracle Database 18c.
- Data Guard Broker DGMGRL ALTER Syntax is Desupported
  Starting with Oracle Database 18c, the Oracle Data Guard broker ALTER command in DGMGRL is desupported.
- Desupport of CRSUSER on Microsoft Windows Systems
  The `crsuser` utility and the `CRSToken` method to change the Windows service user is desupported in Oracle Database 18c.

**Parent topic:** Oracle Database 18c Behavior Changes, Desupports, and Deprecations

##### Oracle Administration Assistant for Windows is Desupported

The Oracle Administration Assistant tool for Windows is desupported in Oracle Database 18c.

Oracle Administration Assistant for Windows is desupported in the current database release. Oracle Administration Assistant for Windows was a tool for creating database administrators, operators, users, and roles in Windows. Oracle Administration Assistant also enabled database services, startup and shutdown configurations, and Windows Registry parameter management. There is no replacement.

**Parent topic:** Desupported Features in Oracle Database 18c

##### Oracle Multimedia DICOM Desupported Features

Several Oracle Multimedia DICOM features are desupported in Oracle Database 18c. Replace DICOM with Oracle SecureFiles and third-party DICOM products.

Digital Imaging and Communications in Medicine (DICOM) is a medical imaging technology that supports the connectivity of radiological devices. Oracle’s native DICOM feature is deprecated, and parts of it are desupported in this release. The desupport of Oracle Multimedia DICOM includes the following features:

- Oracle Multimedia DICOM protocol

- Oracle Multimedia DICOM mid-tier support

- Oracle Multimedia Oracle DICOM Component for WebCenter integration (DICOM/UCM)

The following Oracle Multimedia DICOM features continue to be deprecated:

- DICOM support in Oracle Multimedia ORDImage object

- Oracle Multimedia DICOM objects and packages

There is no replacement for Oracle Multimedia DICOM. Oracle recommends that you replace Oracle Multimedia DICOM by using Oracle SecureFiles with third-party products for DICOM functionality. For example: Use third-party DICOM features to carry out metadata management, DICOM image conversion, and so on.

**Parent topic:** Desupported Features in Oracle Database 18c

##### Oracle Multimedia Java Client Classes Desupported

Oracle Multimedia proxy classes and Oracle Multimedia servlet and JSP classes are desupported.

Oracle Multimedia Java client is desupported in Oracle Database 18c for the following classes:

- Oracle Multimedia proxy classes, including DICOM proxy classes

- Oracle Multimedia servlet/jsp classes

To develop Java applications that manage multimedia content within Oracle Databases, Oracle recommends that you embed PL/SQL blocks in Java.

**Parent topic:** Desupported Features in Oracle Database 18c

##### Oracle XML DB Desupported Features

Starting withOracle Database 18c, schema subprograms in `DBMS_XMLSCHEMA`, many `DBMS_XDB` subprograms, and many other Oracle XML DB schema features are desupported.

In Oracle Database 12c release 1 (12.1), the PL/SQL package `DBMS_XDB_CONFIG` was introduced. At the same time, all Oracle XML DB configuration functions, procedures, and constants that were moved from package `DBMS_XDB` to `DBMS_XDB_CONFIG`. were deprecated, and a series of other `DBMS_XMLSCHEMA`, `DBMS_XDB` subprograms, and other schema features were deprecated. These components are now desupported.

##### Desupported PL/SQL subprograms in package DBMS_XMLSCHEMA

The following PL/SQL subprograms in package DBMS_XMLSCHEMA are desupported:

- `generateSchema`

- `generateSchemas`

There are no replacements for these constructs. There is no workaround for this change.

##### Desupported Oracle XML DB Configuration Functions, Procedures, and Constants

All Oracle XML DB configuration functions, procedures, and constants that were moved from package `DBMS_XDB` to `DBMS_XDB_CONFIG` are desupported. Use `DBMS_XDB_CONFIG`.

The following list of subprograms are desupported in package DBMS_XDB:

- `ADDHTTPEXPIREMAPPING`

- `ADDMIMEMAPPING`

- `ADDSCHEMALOCMAPPING`

- `ADDSERVLET`

- `ADDSERVLETMAPPING`

- `ADDSERVLETSECROLE`

- `ADDXMLEXTENSION`

- `CFG_GET`

- `CFG_REFRESH`

- `CFG_UPDATE`

- `DELETEHTTPEXPIREMAPPING`

- `DELETEMIMEMAPPING`

- `DELETESCHEMALOCMAPPING`

- `DELETESERVLET`

- `DELETESERVLETMAPPING`

- `DELETESERVLETSECROLE`

- `DELETEXMLEXTENSION`

- `GETFTPPORT`

- `GETHTTPPORT`

- `GETLISTENERENDPOINT`

- `SETFTPPORT`

- `SETHTTPPORT`

- `SETLISTENERENDPOINT`

- `SETLISTENERLOCALACCESS`

The following constants are desupported in package `DBMS_XDB`:

- `XDB_ENDPOINT_HTTP`

- `XDB_ENDPOINT_HTTP2`

- `XDB_PROTOCOL_TCP`

- `XDB_PROTOCOL_TCPS`

##### Desupported Oracle XQuery Functions

The following Oracle XQuery functions are desupported. Use the corresponding standard XQuery functions instead. Corresponding functions are the functions that have the same names, but that use the namespace prefix `fn`.

- `ora:matches` . Use `fn:matches` instead

- `ora:replace`. Use `fn:replace` instead

**Parent topic:** Desupported Features in Oracle Database 18c

##### ODP.NET, Managed Driver - Distributed Transaction DLL Desupported

Oracle is desupporting the `Oracle.ManagedDataAccessDTC.dll` file in Oracle Database 18c.

Oracle provided a native managed distributed transaction support for Oracle Data Provider for .NET (`ODP.NET`), Managed Driver using `Oracle.ManagedDataAccessDTC.dll`. In .NET Framework 4.5.2, Microsoft introduced its own native managed distributed transaction implementation, which managed `ODP.NET` used. The new .NET Framework made the `Oracle.ManagedDataAccessDTC.dll` unnecessary. Moreover, Microsoft has desupported all .NET Framework 4 versions earlier than 4.5.2. In accordance with Microsoft policy, Oracle is desupporting the `Oracle.ManagedDataAccessDTC.dll` file.

The desupport includes removing the `UseManagedDTC .NET` configuration file parameter, and `Oracle.ManagedDataAccessDTC.dll`.

**Parent topic:** Desupported Features in Oracle Database 18c

##### Data Guard Broker DGMGRL ALTER Syntax is Desupported

Starting with Oracle Database 18c, the Oracle Data Guard broker ALTER command in DGMGRL is desupported.

The ALTER command syntax in the Data Guard broker DGMGRL command-line interface was deprecated in Oracle Database 10g Release 1 and replaced with the EDIT CONFIGURATION, EDIT DATABASE, and EDIT INSTANCE syntax.

**Parent topic:** Desupported Features in Oracle Database 18c

##### Desupport of CRSUSER on Microsoft Windows Systems

The `crsuser` utility and the `CRSToken` method to change the Windows service user is desupported in Oracle Database 18c.

In Oracle Grid Infrastructure releases before Release 12c (12.1), it was supported to use the `crsuser` utility with Oracle Real Application Clusters (Oracle RAC) to modify the database logon properties of the Oracle Database service from `LocalSystem` to a user ID.

Oracle introduced the Oracle Home User system privileges role for the DB home in Oracle Grid Infrastructure 12c Release 1 (12.1). This role makes the need for the `crsuser` functionality unnecessary. The `crsuser` facility was also previously used to create user-defined CRS resources that ran as a Windows user other than `LocalSystem`. However, Oracle Grid Infrastructure 12c Release 1 (12.1) and later releases provide that same functionality with `crsctl add wallet -type OSUSER` The `crsuser` feature no longer works. It is no longer developed or supported.

For more information about the `crsctl add wallet -type OSUSER` command, refer to Oracle Clusterware Administration and Deployment.

**Related Topics**

- [Oracle Clusterware Administration and Deployment Guide](../cwadd/oracle-clusterware-control-crsctl-utility-reference.md)

**Parent topic:** Desupported Features in Oracle Database 18c

#### Desupported Initialization Parameters in Oracle Database 18c

Review this list of desupported initialization parameters for changes and replacements in parameter settings in this release.

- Desupport of STANDBY_ARCHIVE_DEST Initialization Parameter
  Support for the initialization parameter `STANDBY_ARCHIVE_DEST` is removed in Oracle Database 18c.
- Desupport of UTL_FILE_DIR Initialization Parameter
  Starting in Oracle Database 18c, the `UTL_FILE_DIR` parameter is no longer supported. Instead, specify the name of a directory object.

**Parent topic:** Oracle Database 18c Behavior Changes, Desupports, and Deprecations

##### Desupport of STANDBY_ARCHIVE_DEST Initialization Parameter

Support for the initialization parameter `STANDBY_ARCHIVE_DEST` is removed in Oracle Database 18c.

Oracle Database 11g Release 2 (11.2) included an increase to 31 of the parameters `LOCAL` and `REMOTE` archiving `LOG_ARCHIVE_DEST_``n`. This increase, and the `ALTERNATE` attribute enhancements to provide high availability for local and remote archiving, provides you with more control over the results after an archiving destination fails. Because of these enhancements, `STANDBY_ARCHIVE_DEST` is not required or practical to use.

**Parent topic:** Desupported Initialization Parameters in Oracle Database 18c

##### Desupport of UTL_FILE_DIR Initialization Parameter

Starting in Oracle Database 18c, the `UTL_FILE_DIR` parameter is no longer supported. Instead, specify the name of a directory object.

The `UTL_FILE_DIR` initialization parameter is no longer listed in `V$SYSTEM_PARAMETER` and related views. If you attempt to set this parameter, then the attempt fails. If you attempt to specify an operating system file directly by using the `LOCATION` parameter of `UTL_FILE.FOPEN`, or by using the `LOCATION` parameter of `FOPEN_NCHAR`, then those attempts also fail. Specify the name of a directory object instead.

The security model for the use of a directory object for `UTL_FILE` and other Oracle Database subsystems is secure, because there is a clear privilege model. However, the use of an explicit operating system directory is insecure, because there is no associated privilege model. The notice of deprecation for the `UTL_FILE_DIR` initialization parameter was given in Oracle Database 12c Release 2 (12.2). With Oracle Database 18c, the parameter is now desupported.

##### UTL_FILE Package Symbolic Link in Directory Paths Not Supported

Using the `UTL_FILE` package to access a symbolic link fails in the new Oracle Database release. To avoid the issue, you must change the directory object and the file name, so that neither contains a symbolic link. This desupport can affect any feature from an earlier release using symbolic links, including (but not restricted to) Oracle Data Pump, `BFILE`s, and External Tables. If you attempt to use an affected feature after upgrade, where that feature used symbolic links, you encounter `ORA-29283: invalid file operation: path traverses a symlink`.

**Parent topic:** Desupported Initialization Parameters in Oracle Database 18c

#### Terminal Release of Oracle Streams

Oracle Database 18c is the terminal release for Oracle Streams support. Oracle Streams will be desupported from Oracle Database 19c onwards.

Oracle Streams was deprecated in Oracle Database 12c Release 1 (12.1). It does not support features introduced in Oracle Database 12c and later releases, including the multitenant architecture, the LONG VARCHAR data type, long identifiers, and other features. Oracle GoldenGate is the replication solution for Oracle Database.

**Parent topic:** Oracle Database 18c Behavior Changes, Desupports, and Deprecations

#### Deprecated Features in Oracle Database 18c

Review the deprecated features listed in this section to prepare to use alternatives after you upgrade.

**Note:**

The non-CDB architecture was deprecated in Oracle Database 12c. It can be desupported and unavailable in a release after Oracle Database 19c .

- Data Guard MAX_CONNECTIONS Attribute is Deprecated
  The `MAX_CONNECTIONS` attribute of the `LOG_ARCHIVE_DEST_``n` parameter for Data Guard redo transport is deprecated in Oracle Database 18c.
- Extended Datatype Support (EDS) is Deprecated
  Extended Datatype Support (EDS) is deprecated in Oracle Database 18c .
- GET\_\* Functions Deprecated in the DBMS_DATA_MINING Package
  Starting in Oracle Database 18c, the `GET_*` functions in `DBMS_DATA_MINING` are deprecated. Use the Oracle Data Mining (ODM) Model Details views instead.
- Package DBMS_XMLQUERY is deprecated
  The PL/SQL package `DBMS_XMLQUERY` is deprecated in Oracle Database 18c. Use `DBMS_XMLGEN` instead.
- Package DBMS_XMLSAVE is Deprecated
  The PL/SQL package `DBMS_XMLSAVE` is deprecated in Oracle Database 18c. Use `DBMS_XMLSTORE` instead.
- Deprecated Columns in Oracle Label Security Views
  Starting in Oracle Database 18c, The LABELS column is deprecated in the ALL_SA_USER_LABELS and DBA_SA_USER_LABELS views.
- Returning JSON True or False Values using NUMBER is Deprecated
  Starting with Oracle Database 18c , the option to specify a SQL NUMBER value (1 or 0) as the return value of a JSON value of true or false is deprecated.
- Deprecation of MAIL_FILTER in Oracle Text
  Starting with Oracle Database 18c, the use of `MAIL_FILTER` in Oracle Text is deprecated. Before adding email to the database, filter e-mails to indexable plain text, or to HTML.
- Deprecation of asmcmd showversion Option
  Starting with Oracle Database 18c, the command options for `asmcmd showversion` are replaced with new `asmcmd` options.
- Deprecation of NEWS_SECTION_GROUP in Oracle Text
  Starting with Oracle Database 18c, use of `NEWS_SECTION_GROUP` is deprecated in Oracle Text. Use external processing instead.
- Oracle Net Services Support for SDP is Deprecated
  Starting with Oracle Database 18c, the Oracle Net Services support for Sockets Direct Protocol (SDP) is deprecated.
- Deprecation of Flex Cluster (Hub/Leaf) Architecture
  Starting with Oracle Database 18c, Leaf nodes are deprecated as part of Oracle Flex Cluster architecture.
- Deprecation of PRODUCT_USER_PROFILE Table
  Starting in Oracle Database 18c, the  SQL\*Plus table `PRODUCT_USER_PROFILE` (PUP) table is deprecated.
- Deprecation of Oracle Multimedia
  Starting in Oracle Database 18c, Oracle Multimedia is deprecated. Oracle Multimedia will be desupported in Oracle Database 19c.

**Parent topic:** Oracle Database 18c Behavior Changes, Desupports, and Deprecations

##### Data Guard MAX_CONNECTIONS Attribute is Deprecated

The `MAX_CONNECTIONS` attribute of the `LOG_ARCHIVE_DEST_``n` parameter for Data Guard redo transport is deprecated in Oracle Database 18c.

Oracle Database 11g Release 1 (11.1) introduced the new streaming asynchronous model for redo transport. Using the `MAX_CONNECTIONS` attribute setting no longer provides any benefit when Oracle Data Guard is resolving gaps in the archive log files.

**Parent topic:** Deprecated Features in Oracle Database 18c

##### Extended Datatype Support (EDS) is Deprecated

Extended Datatype Support (EDS) is deprecated in Oracle Database 18c .

The Extended Datatype Support (EDS) feature provides a mechanism for logical standbys to support certain Oracle data types that lack native redo-based support. For example, EDS was used to replicate tables with SDO_GEOMETRY column. However, starting with Oracle Database 12c Release 2 (12.2), there are no EDS-supported Oracle data types that are not supported natively by Logical data or GoldenGate. This feature is now obsolete.

**Parent topic:** Deprecated Features in Oracle Database 18c

##### GET\_\* Functions Deprecated in the DBMS_DATA_MINING Package

Starting in Oracle Database 18c, the `GET_*` functions in `DBMS_DATA_MINING` are deprecated. Use the Oracle Data Mining (ODM) Model Details views instead.

In Oracle Database 12c Release 1, and earlier releases, the `DBMS_DATA_MINING` package supports a separate `GET_MODEL_DETAILS` function for each data mining algorithm. Global details are also available for Generalized Linear Models, Expectation Maximization, Singular Value Decomposition, and Association Rules. There are many `DBMS_DATA_MINING` `Get_*` functions. For example:

- `GET_MODEL_DETAILS`

- `DBMS_DATA_MINING.GET_MODEL_TRANSFORMATIONS`

For example, the Model detail view for Decision Tree describes the split information view, node statistics view, node description view, and the cost matrix view.

Starting with Oracle Database 18c, Oracle recommends that you replace the `GET_MODEL_DETAILS_XML` functions with the Oracle Data Mining Model Details views. The split information view `DM$VP``model_name` describes the decision tree hierarchy, in which you append the name of the Oracle Data Mining model to the view prefix.

**Parent topic:** Deprecated Features in Oracle Database 18c

##### Package DBMS_XMLQUERY is deprecated

The PL/SQL package `DBMS_XMLQUERY` is deprecated in Oracle Database 18c. Use `DBMS_XMLGEN` instead.

DBMS_XMLQUERY provides database-to-XMLType functionality. Oracle recommends that you replace calls to `DBMS_XMLQUERY` with `DBMS_XMLGEN`. `DBMS_XMLGEN` is written in C, and compiled into the kernel, so it provides higher performance.

**Parent topic:** Deprecated Features in Oracle Database 18c

##### Package DBMS_XMLSAVE is Deprecated

The PL/SQL package `DBMS_XMLSAVE` is deprecated in Oracle Database 18c. Use `DBMS_XMLSTORE` instead.

The `DBMS_XMLSAVE` package is part of the Oracle XML SQL Utility. It is used to insert, update, and delete data from XML documents in object-relational tables. Oracle recommends that you replace `DBMS_XMLSAVE` calls with `DBMS_XMLSTORE`. `DBMS_XMLSTORE` is written in C, and compiled into the kernel, so it provides higher performance.

For example: to replace `DBMS_XMLSAVE`, you can create a wrapper function or procedure that you used to call `DBMS_XMLSAVE` on an earlier release Oracle Database, and change the call to `DBMS_XMLSTORE`. Or you can create a synonym:

For example: to replace `DBMS_XMLSAVE`, you can create a wrapper function or procedure that you used to call `DBMS_XMLSAVE` on an earlier release Oracle Database, and change the call to `DBMS_XMLSTORE`. Or you can create a synonym:

    CREATE OR REPLACE PUBLIC SYNONYM DBMS_XMLSAVE FOR DBMS_XMLSTORE;
    GRANT EXECUTE ON DBMS_XMLSAVE TO PUBLIC;

**Parent topic:** Deprecated Features in Oracle Database 18c

##### Deprecated Columns in Oracle Label Security Views

Starting in Oracle Database 18c, The LABELS column is deprecated in the ALL_SA_USER_LABELS and DBA_SA_USER_LABELS views.

Table 10-2 Deprecated columns in Oracle Label Security Views

| Data Dictionary View | Deprecated Column |
|:---------------------|:------------------|
| `ALL_SA_USER_LABELS` | `LABELS`          |
| `ALL_SA_USERS`       | `USER_LABELS`     |
| `DBA_SA_USER_LABELS` | `LABELS`          |
| `DBA_SA_USERS`       | `USER_LABELS`     |

The information in the `LABELS` and `USER_LABELS` columns is redundant. This information is displayed in other columns in these data dictionary views.

**Parent topic:** Deprecated Features in Oracle Database 18c

##### Returning JSON True or False Values using NUMBER is Deprecated

Starting with Oracle Database 18c , the option to specify a SQL NUMBER value (1 or 0) as the return value of a JSON value of true or false is deprecated.

Oracle Database 12c release 1 (12.1) provided support for JSON data, including the function of specifying NUMBER as the type of a column that is returned. The option to specify NUMBER is deprecated. Instead of specifying NUMBER as the output for JSON data for true/false queries, you can use the default SQL value returned for a JSON Boolean value, and specify the string as  'true' or 'false'. If you have an application that requires a numeric value, then you can return the Boolean JSON value as a SQL VARCHAR2 value, and then test that value and return a SQL NUMBER value as the result of that test.

**Parent topic:** Deprecated Features in Oracle Database 18c

##### Deprecation of MAIL_FILTER in Oracle Text

Starting with Oracle Database 18c, the use of `MAIL_FILTER` in Oracle Text is deprecated. Before adding email to the database, filter e-mails to indexable plain text, or to HTML.

`MAIL_FILTER` is based on an obsolete email protocol, RFC-822. Modern email systems do not support RFC-822. There is no replacement.

**Parent topic:** Deprecated Features in Oracle Database 18c

##### Deprecation of asmcmd showversion Option

Starting with Oracle Database 18c, the command options for `asmcmd showversion` are replaced with new `asmcmd` options.

In place of the command `asmcmd showversion --softwarepatch`, use the new option `asmcmd showpatches -l`. In place of the command `asmcmd showversion --releasepatch`, use the new option `asmcmd showversion --active`.

**Parent topic:** Deprecated Features in Oracle Database 18c

##### Deprecation of NEWS_SECTION_GROUP in Oracle Text

Starting with Oracle Database 18c, use of `NEWS_SECTION_GROUP` is deprecated in Oracle Text. Use external processing instead.

If you want to index USENET posts, then preprocess the posts to use `BASIC_SECTION_GROUP` or `HTML_SECTION_GROUP` within Oracle Text. USENET is rarely used commercially.

USENET currently is rarely used for serious purpose. Performing index processing using this section group type is obsolete.

**Parent topic:** Deprecated Features in Oracle Database 18c

##### Oracle Net Services Support for SDP is Deprecated

Starting with Oracle Database 18c, the Oracle Net Services support for Sockets Direct Protocol (SDP) is deprecated.

Oracle recommends that you use TCP as an alternative.

**Parent topic:** Deprecated Features in Oracle Database 18c

##### Deprecation of Flex Cluster (Hub/Leaf) Architecture

Starting with Oracle Database 18c, Leaf nodes are deprecated as part of Oracle Flex Cluster architecture.

With continuous improvements in the Oracle Clusterware stack towards providing shorter reconfiguration times in case of a failure, Leaf nodes are no longer necessary for implementing clusters that meet customer needs, either for on-premises, or in the Cloud.

**Parent topic:** Deprecated Features in Oracle Database 18c

##### Deprecation of PRODUCT_USER_PROFILE Table

Starting in Oracle Database 18c, the  SQL\*Plus table `PRODUCT_USER_PROFILE` (PUP) table is deprecated.

The only use for the `PRODUCT_USER_PROFILE` (PUP) table is to provide a mechanism to control product-level security for SQL\*Plus. Starting with Oracle Database 18c, this mechanism is no longer relevant. This SQL\*Plus product-level security feature will be unavailable in Oracle Database 19c. Oracle recommends that you protect data by using Oracle Database settings, so that you ensure consistent security across all client applications.

**Parent topic:** Deprecated Features in Oracle Database 18c

##### Deprecation of Oracle Multimedia

Starting in Oracle Database 18c, Oracle Multimedia is deprecated. Oracle Multimedia will be desupported in Oracle Database 19c.

Oracle recommends that you store multimedia content in SecureFiles LOBs, and use open source or third-party products such as Piction for image processing and conversion. Oracle Locator is not affected by the deprecation of Oracle Multimedia.

**Parent topic:** Deprecated Features in Oracle Database 18c

### Oracle Database 12c Release 2 (12.2) Behavior Changes, Desupports, and Deprecations

Review for descriptions of Oracle Database 12c Release 2 (12.2) changes.

- Behavior Changes in Oracle Database 12c Release 2 (12.2)
  Review these behavior changes to help plan for upgrades to Oracle Database 12c release 2 (12.2)
- Desupported Features in Oracle Database 12c Release 2 (12.2)
  Review this list of desupported features as part of your upgrade planning.
- Desupported Initialization Parameters in Oracle Database 12c Release 2 (12.2)
  Review this list of desupported initialization parameters for changes and replacements in parameter settings in this release.
- Deprecated Features in Oracle Database 12c Release 2 (12.2)
  Review the deprecated features listed in this section to prepare to use alternatives after you upgrade.
- Deprecated Initialization Parameters in Oracle Database 12c Release 2 (12.2)
  To understand changes and replacements in parameter settings, review the parameters deprecated in the 12.2 release. These parameters can be removed in a later release.

**Parent topic:** Oracle Database Changes, Desupports, and Deprecations

#### Behavior Changes in Oracle Database 12c Release 2 (12.2)

Review these behavior changes to help plan for upgrades to Oracle Database 12c release 2 (12.2)

- Initialization Parameter Default Changes in Oracle Database 12c Release 2 (12.2)
  Review this list of initialization parameter default setting changes for Oracle Database 12c release 2 (12.2).
- Database Upgrade Assistant (DBUA) Enhancements and Changes
  Oracle Database 12c release 2 (12.2) includes several enhancements to DBUA, and some features have been removed or modified.
- Enhancements to Oracle Data Guard Broker and Rolling Upgrades
  Starting with Oracle Database 12c release 2 (12.2), Oracle Data Guard Broker has more features to assist rolling upgrades.
- About Changes in Default SGA Permissions for Oracle Database
  Starting with Oracle Database 12c Release 2 (12.2.0.1), by default, permissions to read and write to the System Global Area (SGA) are limited to the Oracle software installation owner.
- Network Access Control Lists and Upgrade to Oracle Database 12c
  Network access control lists (ACLs) are implemented as Real Application Security ACLs in 12c, and existing ACLs are migrated from XML DB ACLs and renamed during upgrade.
- Parallel Upgrade Utility Batch Scripts
  In Oracle Database 12c Release 2 and later releases, you can run the Parallel Upgrade Utility using command-line batch scripts. `catupgrd.sql` is no longer distributed.
- Unified Auditing AUDIT_ADMIN and AUDIT_VIEWER Roles Changes
  You can find it necessary to rename or drop `AUDIT_ADMIN` and `AUDIT_VIEWER` roles before upgrading.
- Oracle Update Batching Batch Size Settings Disabled
  Oracle update batching settings are disabled in Oracle Database 12c release 2 (12.2). Use JDBC batching instead.
- About Upgrading Tables Dependent on Oracle-Maintained Types
  Starting with Oracle Database 12c release 2 (12.2), you can run the Parallel Upgrade Utility with the `-T` option to set tables to READ ONLY.
- Case-Insensitive Passwords and ORA-1017 Invalid Username or Password
  The Oracle Database 12c release 2 (12.2) default authentication protocol is `12` (Exclusive Mode). This protocol requires case-sensitive passwords for authentication. Review your options if you have earlier release password versions.
- About Deploying Oracle Grid Infrastructure Using Oracle Fleet Patching and Provisioning
  Oracle Fleet Patching and Provisioning (Oracle FPP) is a software lifecycle management method for provisioning and maintaining Oracle homes. Oracle Fleet Patching and Provisioning enables mass deployment and maintenance of standard operating environments for databases, clusters, and user-defined software types.
- Restrictions Using Zero Data Loss Recovery Appliance Release 12.1 Backups
  Zero Data Loss Recovery Appliance release 12.1 does not support backups from protected database clients using Oracle Database 12c release 2 (12.2).
- Client and Foreground Server Process Memory Changes
  To increase optimization and performance, the Oracle Database Client and server process memory requirements are greater than in previous releases.

**Parent topic:** Oracle Database 12c Release 2 (12.2) Behavior Changes, Desupports, and Deprecations

##### Initialization Parameter Default Changes in Oracle Database 12c Release 2 (12.2)

Review this list of initialization parameter default setting changes for Oracle Database 12c release 2 (12.2).

##### OPTIMIZER_ADAPTIVE_PLANS and OPTIMIZER_ADAPTIVE_STATISTICS

OPTIMIZER_ADAPTIVE_FEATURE functions are replaced by two new parameters: OPTIMIZER_ADAPTIVE_PLANS, and OPTIMIZER_ADAPTIVE_STATISTICS.

OPTIMIZER_ADAPTIVE_PLANS controls adaptive plans. It is set by default to TRUE. When set to TRUE, this parameter determines alternate execution plans built with alternative choices that are based on statistics collected as a query executes.

OPTIMIZER_ADAPTIVE_STATISTICS controls adaptive statistics. It is set by default to FALSE. When set to TRUE, the optimizer augments the statistics gathered in the database with adaptive statistics gathered at SQL statement parse time to improve the quality of SQL execution plans. Some query shapes are too complex to rely upon base table statistics alone. The optimizer augments them with adaptive statistics to determine more accurately the best SQL execution plan.

##### SQL92_SECURITY Initialization Parameter Default is TRUE

The SQL standard specifies that security administrators should be able to require that users have SELECT privilege on a table when running an UPDATE or DELETE statement that references table column values in a WHERE or SET clause. SQL92_SECURITY specifies whether users must have been granted the SELECT object privilege to execute such UPDATE or DELETE statements.

Starting in Oracle Database 12c release 2 (12.2), the default setting for this parameter changes from FALSE to TRUE.

When this parameter is set to TRUE, users must have SELECT privilege on the object being deleted or updated.

**Related Topics**

- [Oracle Database Reference](../refrn/SQL92_SECURITY.md)

**Parent topic:** Behavior Changes in Oracle Database 12c Release 2 (12.2)

##### Database Upgrade Assistant (DBUA) Enhancements and Changes

Oracle Database 12c release 2 (12.2) includes several enhancements to DBUA, and some features have been removed or modified.

In response to customer requests, and to improve functionality, Database Upgrade Assistant (DBUA) includes new features and code enhancements. Also, some features in previous releases have been removed.

##### DBUA New Features

DBUA includes the following new features for Oracle Database 12c release 2 (12.2):

- Selective PDB Plug-In Upgrades: You can plug in a PDB created in a previous release into a release 12.2 multitenant architecture CDB environment, and upgrade the PDB using DBUA started from the release 12.2 CDB home

  You can unplug PDBs from a CDB, upgrade the CDB and any PDBs plugged in to the CDB, and then plug in earlier release PDBs and upgrade them using DBCA.

- Priority-Based PDB Upgrades: You can set priority for PDB upgrades, so that higher priority PDBs are upgraded first.

- Retry and Ignore Functionality: You can fix errors and retry upgrades, or select to ignore certain errors and continue upgrades.

- Pause and Continue Functionality: You can stop the upgrade, and continue the upgrade at a later time.

- Standalone Prerequisite Checks: You can run DBUA with the new `-executePrereqs` option to check prerequisites for upgrades at any time.

- Listener Configuration During Database Moves: You can configure the database with a new listener during a database move operation.

- Improved Logging Mechanism: DBUA now has time-stamped logs.

- Performance Enhancements: DBUA includes code enhancements that reduce the number of instance restarts during the upgrade process.

- Enhanced Error Reporting: All DBUA errors are reported using the error code prefix `DBT`, and all errors are reported as a list on a progress page, instead of being presented in message windows.

##### DBUA Removed Features

The following DBUA features available in previous releases are removed in Oracle Database 12c release 2 (12.2):

- Data Files Move: Data files can no longer be moved during upgrades.

- Database Renames During Upgrades: It is no longer supported to rename Oracle Database names during the upgrade.

- Degree of Parallelism Selection Removed from DBUA: The default parallelism is calculated depending on the use case.

  - Upgrade: The default parallelism using DBUA is the same value used by the Parallel Upgrade Utility for manual upgrades. However, in an upgrade operation, you can override the default by specifying the number of cores that you want to use.

  - Recompile: The default parallelism for object recompilation is determined by the `utlrp` script used in manual upgrade.

- Recompile parallelism is the same value as the upgrade parallelism by default.

- Changing Diagnostic and Audit Dest No Longer Available: You can only change the Diagnostic and Audit destination by using the DBUA command-line option `-initParam`.

- Remote DBUA Desupported: In previous releases, DBUA had an option on Windows platforms for supporting Oracle Database remote upgrades. This feature is desupported.

**Parent topic:** Behavior Changes in Oracle Database 12c Release 2 (12.2)

##### Enhancements to Oracle Data Guard Broker and Rolling Upgrades

Starting with Oracle Database 12c release 2 (12.2), Oracle Data Guard Broker has more features to assist rolling upgrades.

Oracle Data Guard Broker now supports Oracle Active Data Guard rolling upgrade. Oracle Active Data Guard rolling upgrade was introduced in Oracle Database 12c release 1 (12.1). It simplifies the execution of the transient logical database rolling upgrade process by automating many manual steps in a simple PL/SQL package (DBMS_ROLLING). In addition to making database rolling upgrades simpler, the automated process is much more reliable. Oracle Data Guard broker can now direct Oracle Active Data Guard rolling upgrades from the DGMGRL command-line interface. Broker support also adds substantial simplification to the rolling upgrade process by transparently handling redo transport destination settings and other tasks.

In Oracle Database 12c release 2 (12.2) and later releases, when you perform a rolling upgrade using the DBMS_ROLLING PL/SQL package, you no longer have to disable the broker. In addition, the broker now reports when a rolling upgrade is in place, and tracks its status. The status information is displayed in the output of the DGMGRL commands SHOW CONFIGURATION and SHOW DATABASE.

Using Oracle Data Guard Broker to manage database rolling upgrades can simplify the upgrade process by minimizing your downtime and risk when introducing change to production environments.

**Related Topics**

- [Oracle Data Guard Broker](../sbydb/using-DBMS_ROLLING-to-perform-rolling-upgrade.md)

**Parent topic:** Behavior Changes in Oracle Database 12c Release 2 (12.2)

##### About Changes in Default SGA Permissions for Oracle Database

Starting with Oracle Database 12c Release 2 (12.2.0.1), by default, permissions to read and write to the System Global Area (SGA) are limited to the Oracle software installation owner.

In previous releases, both the Oracle installation owner account and members of the OSDBA group had access to shared memory. The change in Oracle Database 12c Release 2 (12.2) and later releases to restrict access by default to the Oracle installation owner account provides greater security than previous configurations. However, this change may prevent DBAs who do not have access to the Oracle installation owner account from administering the database.

The Oracle Database initialization parameter ALLOW_GROUP_ACCESS_TO_SGA determines if the Oracle Database installation owner account (`oracle` in Oracle documentation examples) is the only user that can read and write to the database System Global Area (SGA), or if members of the OSDBA group can read the SGA. In Oracle Database 12c Release 2 (12.2) and later releases, the default value for this parameter is FALSE, so that only the Oracle Database installation owner has read and write permissions to the SGA. Group access to the SGA is removed by default. This change affects all Linux and UNIX platforms.

If members of the OSDBA group require read access to the SGA, then you can change the initialization parameter ALLOW_GROUP_ACCESS_TO_SGA setting from FALSE to TRUE. Oracle strongly recommends that you accept the default permissions that limit access to the SGA to the `oracle` user account.

**Related Topics**

- [Oracle Database Reference](../refrn/ALLOW_GROUP_ACCESS_TO_SGA.md)

**Parent topic:** Behavior Changes in Oracle Database 12c Release 2 (12.2)

##### Network Access Control Lists and Upgrade to Oracle Database 12c

Network access control lists (ACLs) are implemented as Real Application Security ACLs in 12c, and existing ACLs are migrated from XML DB ACLs and renamed during upgrade.

During Oracle Database upgrades to 12c Release 1 (12.1) and later releases, network access control in Oracle Database is implemented using Real Application Security access control lists (ACLs). Existing ACLs in XDB are migrated during upgrade. Existing APIs in the `DBMS_NETWORK_ACL_ADMIN` PL/SQL package and catalog views are deprecated. These deprecated views are replaced with new equivalents in Oracle Database 12c.

Starting with Oracle Database 12c Release 1 (12.1), you can grant network privileges by appending an access control entry (ACE) to a host ACL using `DBMS_NETWORK_ACL_ADMIN.APPEND_HOST_ACE`. If you append an ACE to a host that has no existing host ACL, then a new host ACL is created implicitly. If the host ACL exists, then the ACEs are appended to the existing ACL.

##### How Changing to Real Application Security ACLS Affects You

During upgrades, the following changes are made:

- Existing network ACLs are migrated from Oracle Database 11g XML DB to Oracle Database 12c Real Application Security. All privileges of the existing ACLs are preserved during this migration.

- Existing ACLs are renamed.

##### What You Need To Do Before Upgrades

- Check for existing Network ACLs before the upgrade.

- Preserve existing network ACLs and privileges (`DBA_NETWORK_ACLS` and `DBA_NETWORK_ACL_PRIVILEGES`) in an intermediate staging table. Preserving the existing privileges in a table enables you to restore them if the automatic migration fails, or if you want to roll back an upgrade.

**Related Topics**

- [Oracle Database Security Guide](../dbseg/managing-fine-grained-access-in-pl-sql-packages-and-types.md)
- [Oracle Database Reference](../refrn/DBA_ACL_NAME_MAP.md)

**Parent topic:** Behavior Changes in Oracle Database 12c Release 2 (12.2)

##### Parallel Upgrade Utility Batch Scripts

In Oracle Database 12c Release 2 and later releases, you can run the Parallel Upgrade Utility using command-line batch scripts. `catupgrd.sql` is no longer distributed.

In Oracle Database 12c Release 2 (12.2) and later releases, you can run the Parallel Upgrade Utility (`catctl.pl`) from the command line by entering the shell commands `dbupgrade` for Linux and Unix, and `dbupgrade.com` for Microsoft Windows. These shell scripts call the `catctl.pl` script from the upgrade binary home. You can either run these scripts with default values, or you can run them with the same input parameters that you use to run `catctl.pl` from the Perl prompt.

**Note:**

The information in this notice as published for Oracle Database Release 2 (12.2) is obsolete. All manual script methods for upgrading Oracle Database were deprecated starting with Oracle Database 19c, and desupported in Oracle Database 23c. For all releases, Oracle recommends that you perform upgrades using the AutoUpgrade utility. Listen to Roy Swonger tell you about this change, read Mike Dietrich's page about the history behind the development of AutoUpgrade, view Daniel Overby Hanson's video that shows you how you can test your own upgrade using AutoUpgrade, and have a look at the "Hitchhiker's Guide for Upgrading to Oracle Database 19c."

**Related Topics**

- [Upgrade Your Database Now: DBUA Deprecation and future Desupport in Oracle Database 23c](https://mikedietrichde.com/2023/06/21/dbua-deprecation-and-future-desupport-in-oracle-database-23c/)
- [Hitchhiker's Guide for Upgrading to Oracle Database 19c](https://apexapps.oracle.com/pls/apex/dbpm/r/livelabs/view-workshop?wid=606)

**Parent topic:** Behavior Changes in Oracle Database 12c Release 2 (12.2)

##### Unified Auditing AUDIT_ADMIN and AUDIT_VIEWER Roles Changes

You can find it necessary to rename or drop `AUDIT_ADMIN` and `AUDIT_VIEWER` roles before upgrading.

In Oracle Database 12c, if you use Unified Auditing, then you can have two AUDSYS roles in your Oracle Database 11g release 2 (11.2.0.4) and earlier releases that affect upgrading: `AUDIT_ADMIN` and `AUDIT_VIEWER`. Because of changes in these roles, you must drop these earlier release users or user roles before you can upgrade to Oracle Database 12c release 1 (12.1) or later.

If you have created `AUDIT_ADMIN` and `AUDIT_VIEWER` users or roles with Oracle Database 12c release 1 (12.1), then you do not need to drop these users or roles.

Only drop the `AUDSYS` schema and the `AUDIT_ADMIN` and `AUDIT_VIEWER` roles if both of the following conditions are true:

- The version from which you are upgrading is earlier than Oracle Database 12c release 1 (12.1)

- You have created a custom schema with the name `AUDSYS`

If you are affected by this requirement, and you cannot drop these `AUDSYS` roles, then select the `UNIFIED_AUDIT_TRAIL` view, create your own table, using similar definitions, and use this table to take a backup of the Unified Audit data. Oracle recommends that you also perform this procedure if you want to preserve your ability to downgrade to your earlier release database.

Oracle recommends that you do not use these names in your databases. If these users or roles exist, then you should rename or drop them as appropriate before upgrading to Oracle Database 12.

**See Also:**

[Oracle Database Security Guide](../dbseg/configuring-privilege-and-role-authorization.md) for information on configuring privilege and role authorization for database security

**Parent topic:** Behavior Changes in Oracle Database 12c Release 2 (12.2)

##### Oracle Update Batching Batch Size Settings Disabled

Oracle update batching settings are disabled in Oracle Database 12c release 2 (12.2). Use JDBC batching instead.

Oracle update batching was deprecated in Oracle Database 12c Release 1 (12.1). Starting in Oracle Database 12c Release 2 (12.2), Oracle update batching is a no operation code (no-op). This means that if you implement Oracle update batching in your application using the Oracle Database 12c Release 2 (12.2) JDBC driver, then the specified batch size is not set, and results in a batch size of 1. With this batch setting, your application processes one row at a time. Oracle strongly recommends that you use the standard JDBC batching if you are using the Oracle Database 12c Release 2 (12.2) JDBC driver.

**Parent topic:** Behavior Changes in Oracle Database 12c Release 2 (12.2)

##### About Upgrading Tables Dependent on Oracle-Maintained Types

Starting with Oracle Database 12c release 2 (12.2), you can run the Parallel Upgrade Utility with the `-T` option to set tables to READ ONLY.

When you run the Parallel Upgrade Utility with the `-T` option, any tablespaces that do not contain Oracle Maintained objects are set to READ ONLY. Setting these tables to READ ONLY can reduce the amount of data that you need to back up before upgrading the database.

If your database has user tables that depend on Oracle Maintained types (for example, AQ queue tables), then you must upgrade these tables manually after upgrade.

After the upgrade is complete, to upgrade tables dependent on Oracle-Maintained types, run the script `utluptabdata.sql` to carry out ALTER TABLE UPGRADE commands on tables in tablespaces set to READ ONLY during the upgrade.

Starting with Oracle Database 12c release 2, the ALTER TYPE statement behavior is also changed. If a dependent table is in an accessible tablespace, then it is automatically upgraded to the new version of the type. If the dependent table is in a READ ONLY tablespace, then it is not automatically upgraded. Run the `utluptabdata.sql` script to upgrade those tables set to READ ONLY tablespace states during the upgrade. You only need to run the `utluptabdata.sql` script when you run the Parallel Upgrade Utility with the `-T` option to run the upgrade.

**Note:**

When tablespaces are set to `READ ONLY`, this setting prevents updates on all tables in the tablespace, regardless of a user‘s update privilege level. For example, users connecting as SYSDBA are prevented from changing their application data.

**Related Topics**

- [Upgrading Tables Dependent on Oracle-Maintained Types](required-tasks-complete-upgrading-oracle-database.md)
- [Running Upgrades with Read-Only and Offline Tablespaces](database-preparation-tasks-to-complete-before-upgrades.md)

**Parent topic:** Behavior Changes in Oracle Database 12c Release 2 (12.2)

##### Case-Insensitive Passwords and ORA-1017 Invalid Username or Password

The Oracle Database 12c release 2 (12.2) default authentication protocol is `12` (Exclusive Mode). This protocol requires case-sensitive passwords for authentication. Review your options if you have earlier release password versions.

Starting with Oracle Database 12c release 2 (12.2), the default value for the SQLNET.ORA parameter ALLOWED_LOGON_VERSION_SERVER is changed to `12`. This parameter refers to the logon authentication protocol used for the server, not the Oracle Database release.

By default, Oracle no longer supports case-insensitive password-based authentication; only the new password versions (`11G` and `12C`) are allowed. The case-insensitive `10G` password version is no longer generated.

If the following conditions are true, then you may have accounts that are prevented from logging into the database after upgrading to 12.2:

- You are upgrading a server that has user accounts created in an earlier Oracle Database release.

- User accounts created in the earlier release use a case-insensitive password version from an earlier release authentication protocol, such as the `10G` password version.

- Earlier release user accounts have not reset passwords.

- The server has been configured with SEC_CASE_SENSITIVE_LOGON set to FALSE, so that it can only authenticate users who have a `10G` case-insensitive password version.

If you have accounts that require `10G` password versions, then to prevent accounts using that password version from being locked out of the database, you can change from an Exclusive Mode to a more permissive authentication protocol.

**Note:**

Oracle does not support case-insensitive password-based authentication while running in an Exclusive Mode. The default authentication protocol in Oracle Database 12c release 2 (12.2) is an Exclusive Mode. Oracle only supports case-insensitive authentication with the following conditions:

- The server is running in a mode other than an Exclusive Mode

- The `10G` password version is present

##### Option for Servers with Accounts Using Only 10G Password Version

After you upgrade to Oracle Database 12c release 2 (12.2), complete the following procedure to enable accounts using the `10G` password version:

1.  Log in as an administrator.

2.  Edit the SQLNET.ORA file to change the SQLNET.ALLOWED_LOGON_VERSION_SERVER setting from the default, `12`, to `11` or lower. For example:

    `SQLNET.ALLOWED_LOGON_VERSION_SERVER=11`

After you change to a more permissive SQLNET.ALLOWED_LOGON_VERSION_SERVER setting, expire users’ passwords to require them to change their passwords. For detailed information, refer to Oracle Database Security Guide.

**Parent topic:** Behavior Changes in Oracle Database 12c Release 2 (12.2)

##### About Deploying Oracle Grid Infrastructure Using Oracle Fleet Patching and Provisioning

Oracle Fleet Patching and Provisioning (Oracle FPP) is a software lifecycle management method for provisioning and maintaining Oracle homes. Oracle Fleet Patching and Provisioning enables mass deployment and maintenance of standard operating environments for databases, clusters, and user-defined software types.

**Note:**

Starting with Oracle Grid Infrastructure 19c, the feature formerly known as Rapid Home Provisioning (RHP) is now Oracle Fleet Patching and Provisioning (Oracle FPP).

Oracle Fleet Patching and Provisioning enables you to install clusters, and provision, patch, scale, and upgrade Oracle Grid Infrastructure, Oracle Restart, and Oracle Database homes. The supported versions are 11.2, 12.1, 12.2, 18c, and 19c. You can also provision applications and middleware using Oracle Fleet Patching and Provisioning.

Oracle Fleet Patching and Provisioning is a service in Oracle Grid Infrastructure that you can use in either of the following modes:

- Central Oracle Fleet Patching and Provisioning Server

  The Oracle Fleet Patching and Provisioning Server stores and manages standardized images, called gold images. Gold images can be deployed to any number of nodes across the data center. You can create new clusters and databases on the deployed homes and can use them to patch, upgrade, and scale existing installations.

  The Oracle Fleet Patching and Provisioning Server can manage the following types of installations:
  - Software homes on the cluster hosting the Oracle Fleet Patching and Provisioning Server itself.

  - Oracle Fleet Patching and Provisioning Clients running Oracle Grid Infrastructure 12c Release 2 (12.2), 18c, and 19c.

  - Installations running Oracle Grid Infrastructure 11g Release 2 (11.2) and 12c Release 1 (12.1).

  - Installations running without Oracle Grid Infrastructure.

  The Oracle Fleet Patching and Provisioning Server can provision new installations and can manage existing installations without requiring any changes to the existing installations. The Oracle Fleet Patching and Provisioning Server can automatically share gold images among peer servers to support enterprises with geographically distributed data centers.

- Oracle Fleet Patching and Provisioning Client

  The Oracle Fleet Patching and Provisioning Client can be managed from the Oracle Fleet Patching and Provisioning Server, or directly by executing commands on the client itself. The Oracle Fleet Patching and Provisioning Client is a service built into the Oracle Grid Infrastructure and is available in Oracle Grid Infrastructure 12c Release 2 (12.2) and later releases. The Oracle Fleet Patching and Provisioning Client can retrieve gold images from the Oracle Fleet Patching and Provisioning Server, upload new images based on the policy, and apply maintenance operations to itself.

##### Oracle Fleet Patching and Provisioning

Deploying Oracle software using Oracle Fleet Patching and Provisioning has the following advantages:

- Ensures standardization and enables high degrees of automation with gold images and managed lineage of deployed software.

- Minimizes downtime by deploying new homes as images (called gold images) out-of-place, without disrupting active databases or clusters.

- Simplifies maintenance by providing automatons which are invoked with a simple, consistent API across database versions and deployment models.

- Reduces maintenance risk with built-in validations and a “dry run” mode to test the operations.

- Enables you to resume or restart the commands in the event of an unforeseen issue, reducing the risk of maintenance operations.

- Minimizes and often eliminates the impact of patching and upgrades, with features that include:

  - Zero-downtime database upgrade with fully automated upgrade, executed entirely within the deployment without requiring any extra nodes or external storage.

  - Adaptive management of database sessions and OJVM during rolling patching.

  - Options for management of consolidated deployments.

- The deployment and maintenance operations enable customizations to include environment-specific actions into the automated workflow.

**Related Topics**

- [Oracle Clusterware Administration and Deployment Guide](../fppad/patching-and-upgrading-oracle-grid-infrastructure.md)

**See Also:**

Oracle Clusterware Administration and Deployment Guide for information about setting up the Oracle Fleet Patching and Provisioning Server and Client, and for creating and using gold images for provisioning and patching Oracle Grid Infrastructure and Oracle Database homes.

**Parent topic:** Behavior Changes in Oracle Database 12c Release 2 (12.2)

##### Restrictions Using Zero Data Loss Recovery Appliance Release 12.1 Backups

Zero Data Loss Recovery Appliance release 12.1 does not support backups from protected database clients using Oracle Database 12c release 2 (12.2).

Zero Data Loss Recovery Appliance release 12.2 (Recovery Appliance) does support backups from protected release 12.2 database clients.

If you back up your database to Recovery Appliance, then Oracle recommends that you do not not upgrade your database to release 12.2 until your Recovery Appliance is upgraded to release 12.2.

**Parent topic:** Behavior Changes in Oracle Database 12c Release 2 (12.2)

##### Client and Foreground Server Process Memory Changes

To increase optimization and performance, the Oracle Database Client and server process memory requirements are greater than in previous releases.

Every release of Oracle Database includes new features and capabilities. To provide optimal performance for the increased capability of the database, there can be an increase in the Oracle Database Client and Oracle Database Server can increase from one release to the next. The memory requirement increase can vary from platform to platform.

As part of your upgrade plan, check to determine the memory requirements increase that can be present in a new Oracle Database release. For example, in comparison to Oracle Database 11g Release 2 (11.2), Oracle Database 12c on some platforms can have as much as a 5 MB memory increase for each client, and a 10 MB increase for each server.

**Parent topic:** Behavior Changes in Oracle Database 12c Release 2 (12.2)

#### Desupported Features in Oracle Database 12c Release 2 (12.2)

Review this list of desupported features as part of your upgrade planning.

- Desupport of Advanced Replication
  Starting in Oracle Database 12c release 2 (12.2), the Advanced Replication feature of Oracle Database is desupported.
- Desupport of Direct File System Placement for OCR and Voting Files
  Placing OCR and Voting Disk files on shared file systems is desupported in favor of placing the files on Oracle ASM.
- Desupport of JPublisher
  All Oracle JPublisher features are desupported and unavailable in Oracle Database 12c Release 2 (12.2.0.1).
- Desupport of preupgrd.sql and utluppkg.sql
  The `preupgrd.sql` and `utluppkg.sql` scripts are replaced by the Preupgrade Information Tool (`preupgrade.jar`).
- Desupported Oracle Data Provider for .NET APIs for Transaction Guard
  Application programming interfaces (APIs) for Transaction Guard listed here are desupported in Oracle Database 12c release 2 (12.2).
- Desupported Views in Oracle Database 12c Release 2 (12.2)
  The views listed in this topic are desupported in Oracle Database 12c release 2 (12.2).
- SQLJ Support Inside Oracle Database
  Starting with Oracle Database 12c release 2 (12.2), Oracle does not support running server-side SQLJ code.
- Desupport of Some XML DB Features
  Starting in Oracle Database 12c release 2 (12.2), the XML DB features listed here are desupported.

**Parent topic:** Oracle Database 12c Release 2 (12.2) Behavior Changes, Desupports, and Deprecations

##### Desupport of Advanced Replication

Starting in Oracle Database 12c release 2 (12.2), the Advanced Replication feature of Oracle Database is desupported.

The Oracle Database Advanced Replication feature is desupported in its entirety. The desupport of this feature includes all functionality associated with this feature: multimaster replication, updateable materialized views, and deployment templates. Read-only materialized views are still supported with basic replication.

Oracle recommends that you replace your use of Advanced Replication with Oracle GoldenGate.

**Parent topic:** Desupported Features in Oracle Database 12c Release 2 (12.2)

##### Desupport of Direct File System Placement for OCR and Voting Files

Placing OCR and Voting Disk files on shared file systems is desupported in favor of placing the files on Oracle ASM.

Starting with Oracle Grid Infrastructure 12c Release 2 (12.2), the placement of Oracle Clusterware files: the Oracle Cluster Registry (OCR), and the Voting Files, directly on a shared file system is desupported in favor of having Oracle Clusterware files managed by Oracle Automatic Storage Management (Oracle ASM). You cannot place Oracle Clusterware files directly on a shared file system. If you need to use a supported shared file system, either a Network File System, or a shared cluster file system instead of native disks devices, then you must create Oracle ASM disks on supported network file systems that you plan to use for hosting Oracle Clusterware files before installing Oracle Grid Infrastructure. You can then use the Oracle ASM disks in an Oracle ASM disk group to manage Oracle Clusterware files.

If your Oracle Database files are stored on a shared file system, then you can continue to use the same for database files, instead of moving them to Oracle ASM storage.

**Parent topic:** Desupported Features in Oracle Database 12c Release 2 (12.2)

##### Desupport of JPublisher

All Oracle JPublisher features are desupported and unavailable in Oracle Database 12c Release 2 (12.2.0.1).

Oracle recommends that you use the following alternatives:

- To continue to use Web service callouts, Oracle recommends that you use the Oracle JVM Web Services Callout utility, which is a replacement for the Web Services Callout utility.

- To replace other JPublisher automation capabilities, including mapping user-defined SQL types or SQL types, wrapping PL/SQL packages and similar capabilities, Oracle recommends that developers use explicit steps, such as precompiling code with SQLJ precompiler, building Java STRUCT classes, or using other prestructured options.

**Related Topics**

- <https://support.oracle.com/rs?type=doc&id=1937939.1>

**See Also:**

My Oracle Support Note 1937939.1 for more information about JDeveloper deprecation and desupport

**Parent topic:** Desupported Features in Oracle Database 12c Release 2 (12.2)

##### Desupport of preupgrd.sql and utluppkg.sql

The `preupgrd.sql` and `utluppkg.sql` scripts are replaced by the Preupgrade Information Tool (`preupgrade.jar`).

Beginning with Oracle Database 12c release 2 (12.2), the Pre-Upgrade Information Tool scripts `preupgrd.sql` and `utluppkg.sql` are no longer supplied as part of the Oracle Database release. The Pre-Upgrade Information Tool `preupgrade.jar` replaces both of these files.

The `preupgrade.jar` Pre-Upgrade Information Tool is supplied with Oracle Database 12c release 2 (12.2). This script has the same capabilities as the scripts it replaces. It can run using the Java Development Kits (JDKs) installed with Oracle Database releases supported for direct upgrade to Oracle Database 12c release 2 (12.2).

**Note:**

The Pre-Upgrade Information Tool is now replaced with the AutoUpgrade Utility, which can assist you with upgrades from Oracle Database 11.2.0.4 and later releases. Download the latest available version.

**Related Topics**

- [My Oracle Support note 2485457.1](https://support.oracle.com/rs?type=doc&id=2485457.1)

**Parent topic:** Desupported Features in Oracle Database 12c Release 2 (12.2)

##### Desupported Oracle Data Provider for .NET APIs for Transaction Guard

Application programming interfaces (APIs) for Transaction Guard listed here are desupported in Oracle Database 12c release 2 (12.2).

The following Oracle Data Provider for .NET application programming interfaces for Transaction Guard are desupported in Oracle Database 12c Release 2 (12.2):

- `OracleLogicalTransactionStatus` class

- `OracleConnection.GetLogicalTransactionStatus` method

- `OracleConnection.LogicalTransactionId` property

- `OracleConnection.OracleLogicalTransaction` property

- `OracleLogicalTransaction.DataSource` property

- `OracleLogicalTransaction.GetOutcome()` method

- `OracleLogicalTransaction.GetOutcome(``string``, ``string``, ``string``)` method

- `OracleLogicalTransaction.UserId` property

**Parent topic:** Desupported Features in Oracle Database 12c Release 2 (12.2)

##### Desupported Views in Oracle Database 12c Release 2 (12.2)

The views listed in this topic are desupported in Oracle Database 12c release 2 (12.2).

Revise any of your SQL statements that use these views.

##### DBA_REGISTERED_MVIEW_GROUPS View

##### V\$REPLPROP View

##### V\$REPLQUEUE View

**Parent topic:** Desupported Features in Oracle Database 12c Release 2 (12.2)

##### SQLJ Support Inside Oracle Database

Starting with Oracle Database 12c release 2 (12.2), Oracle does not support running server-side SQLJ code.

Oracle supports using client-side SQLJ. However, Oracle does not support the use of server-side SQLJ, including running stored procedures, functions, and triggers in the database environment.

**Parent topic:** Desupported Features in Oracle Database 12c Release 2 (12.2)

##### Desupport of Some XML DB Features

Starting in Oracle Database 12c release 2 (12.2), the XML DB features listed here are desupported.

The following features are desupported:

- Java classes in package `oracle.xdb.dom`

- Oracle XPath function `ora:instanceof`. Use XQuery operator `instance of` instead.

- Oracle XPath function `ora:instanceof-only`. Use XML Schema attribute `xsi:type` instead.

- Function-based indexes on XMLType. Use XMLIndex with a structured component instead.

- Oracle XQuery function `ora:view`. Use XQuery functions `fn:collection` instead.

- PL/SQL procedure `DBMS_XDB_ADMIN.CreateRepositoryXMLIndex`

- PL/SQL procedure `DBMS_XDB_ADMIN.XMLIndexAddPath`

- PL/SQL procedure `DBMS_XDB_ADMIN.XMLIndexRemovePath `

- PL/SQL procedure `DBMS_XDB_ADMIN.DropRepositoryXMLIndex`

- XML schema annotation (attribute) `csx:encodingType `

- XMLIndex index on CLOB portions of hybrid XMLType storage (index on CLOB data that is embedded within object-relational storage)

**Parent topic:** Desupported Features in Oracle Database 12c Release 2 (12.2)

#### Desupported Initialization Parameters in Oracle Database 12c Release 2 (12.2)

Review this list of desupported initialization parameters for changes and replacements in parameter settings in this release.

##### GLOBAL_CONTEXT_POOL_SIZE Initialization Parameter

The `GLOBAL_CONTEXT_POOL_SIZE` initialization parameter is removed and desupported in this release.

`GLOBAL_CONTEXT_POOL_SIZE` specified the amount of memory to allocate in the SGA for storing and managing global application context. The default value of this parameter was null. The parameter was deprecated in Oracle Database 10g release 2 (10.2).

##### MAX_ENABLED_ROLES Initialization Parameter

The `MAX_ENABLED_ROLES` initialization parameter is removed and desupported in this release.

There is no replacement for this parameter. Oracle Database has not used this parameter since Oracle Database 10g release 2 (10.2).

##### OPTIMIZER_ADAPTIVE_FEATURES Initialization Parameter

The `OPTIMIZER_ADAPTIVE_FEATURES` initialization parameter is removed and desupported in this release.

The functions of this parameter are replaced by two new parameters. The default value for `OPTIMIZER_ADAPTIVE_PLANS` is `TRUE`. When set to `TRUE`, this parameter determines alternate execution plans that are based on statistics collected as a query executes. `OPTIMIZER_ADAPTIVE_STATISTICS` is set by default to `FALSE`. When set to `TRUE`, the optimizer augments the statistics gathered in the database with adaptive statistics gathered at SQL statement parse time to improve the quality of SQL execution plans.

##### PARALLEL_AUTOMATIC_TUNING Initialization Parameter

The `PARALLEL_AUTOMATIC_TUNING` initialization parameter is removed and desupported in this release.

The `PARALLEL_AUTOMATIC_TUNING` initialization parameter determined the default values for parameters that controlled parallel processing. It was deprecated in Oracle Database 10g release 2 (10.2).

##### PARALLEL_IO_CAP_ENABLED Initialization Parameter

The `PARALLEL_IO_CAP_ENABLED` initialization parameter determined if Oracle Database set a limit to the default degree of parallelism to a level no greater than the I/O system supported. This parameter was deprecated in Oracle Database release 11.2. The function of this parameter was replaced by the `PARALLEL_DEGREE_LIMIT` parameter, when that parameter is set to `IO`.

##### PARALLEL_SERVER Initialization Parameter

The `PARALLEL_SERVER` initialization parameter is removed and desupported in this release.

The `PARALLEL_SERVER` initialization parameter was used to start a database in Oracle Parallel Server mode. This parameter was deprecated in Oracle9i Database Release 1 (9.0.1). Oracle Parallel Server was replaced with Oracle Real Application Clusters, which uses the `CLUSTER_DATABASE`initialization parameter.

##### PARALLEL_SERVER_INSTANCES Initialization Parameter

The `PARALLEL_SERVER_INSTANCES` initialization parameter is removed and desupported in this release.

The `PARALLEL_SERVER_INSTANCES` initialization parameter specified the number of configured instances in Oracle Parallel Server mode. This parameter was deprecated in Oracle9i Database Release 1 (9.0.1). Oracle Parallel Server was replaced with Oracle Real Application Clusters, which uses the CLUSTER_DATABASE_INSTANCES initialization parameter.

##### USE_INDIRECT_DATA_BUFFERS Initialization Parameter

The initialization parameter `USE_INDIRECT_DATA_BUFFERS` is removed and desupported in this release.

The parameter was used to enable the Very Large Memory feature for 32-bit platforms. These platforms are no longer supported.

**Related Topics**

- [Oracle Database Reference](../refrn/initialization-parameters-2.md)

**Parent topic:** Oracle Database 12c Release 2 (12.2) Behavior Changes, Desupports, and Deprecations

#### Deprecated Features in Oracle Database 12c Release 2 (12.2)

Review the deprecated features listed in this section to prepare to use alternatives after you upgrade.

- Deprecation of ALTER TYPE REPLACE
  Starting with Oracle Database 12c release 2 (12.2.0.1), the REPLACE clause of ALTER TYPE is deprecated.
- Deprecation of configToolAllCommands Script
  The postinstallation check script configToolAllCommands is deprecated in Oracle Database 12c release 1 (12.1).
- Deprecation of DBMS_DEBUG Package
  The DBMS_DEBUG package is deprecated in Oracle Database 12c release 2 (12.2). Oracle recommends that you use DBMS_DEBUG_JDWP.
- Deprecation of Intelligent Data Placement (IDC)
  Intelligent Data Placement is deprecated in Oracle Database 12c release 2 (12.2).
- Deprecation of CONTINUOUS_MINE Option
  Starting with Oracle Database 12c Release 2 (12.2.0.1), the LogMiner CONTINUOUS_MINE option is deprecated.
- Deprecation of Non-CDB Architecture
  The non-CDB architecture was deprecated in Oracle Database 12c. It can be desupported and unavailable in a release after Oracle Database 19c .
- Deprecation of Oracle Administration Assistant for Windows
  Oracle Administration Assistant for Windows is deprecated in Oracle Database 12c release 2 (12.2).
- Deprecation of Oracle Data Provider for .NET PromotableTransaction Setting
  The Oracle Data Provider for .NET `PromotableTransaction` setting is deprecated, because it is no longer necessary.
- Deprecation of oracle.jdbc.OracleConnection.unwrap()
  Starting in Oracle Database 12c release 2 (12.2), the Java package `oracle.jdbc.OracleConnection.unwrap()` is deprecated.
- Deprecation of oracle.jdbc.rowset Package
  Starting in Oracle Database 12c release 2 (12.2), the Java `oracle.jdbc.rowset` package is deprecated
- Deprecation of oracle.sql.DatumWithConnection Classes
  `oracle.sql` classes that extend `oracle.sql.DatumWithConnection` are deprecated in Oracle Database 12c release 2 (12.2), in favor of `oracle.jdbc` extension types.
- Deprecation of Oracle Multimedia Java APIs
  The Oracle Multimedia Java APIs are deprecated in Oracle Database 12c release 2.
- Deprecation of Oracle Multimedia Support for DICOM
  Starting in Oracle Database 12c release 2 (12.2), the Oracle Multimedia DICOM feature is deprecated.
- Deprecation of Multimedia SQL/MM Still Image Standard Support
  Starting in Oracle Database 12c release 2 (12.2), Oracle Multimedia SQL/MM Still Image standard support is deprecated.
- Deprecation of Unicode Collation Algorithm (UCA) 6.1 Collations
  Starting in Oracle Database 12c release 2, the Unicode Collation Algorithm (UCA) 6.1 collations are deprecated.
- Deprecation of UNIFIED_AUDIT_SGA_QUEUE_SIZE
  Starting in Oracle Database 12c release 2, the initialization parameter UNIFIED_AUDIT_SGA_QUEUE_SIZE is deprecated.
- Deprecation of VERIFY_FUNCTION and VERIFY_FUNCTION_11G
  The `VERIFY_FUNCTION` and `VERIFY_FUNCTION_11G` password verify functions are deprecated in this release, because they enforce the weaker password restrictions from earlier releases.
- Deprecation of V\$MANAGED_STANDBY
  The V\$MANAGED_STANDBY view is deprecated in Oracle Database 12c release 2 (12.2.0.1). Oracle recommends that you use the new view V\$DATAGUARD_PROCESS.
- Deprecation of Some XML DB Functions
  Starting with Oracle Database 12c release 2 (12.2) the options listed in this topic are deprecated.
- Deprecated Features for Oracle XML Database
  These features are deprecated in Oracle Database 12c Release 1, and can be desupported in a future release.

**Parent topic:** Oracle Database 12c Release 2 (12.2) Behavior Changes, Desupports, and Deprecations

##### Deprecation of ALTER TYPE REPLACE

Starting with Oracle Database 12c release 2 (12.2.0.1), the REPLACE clause of ALTER TYPE is deprecated.

As an alternative, Oracle recommends that you use the ALTER TYPE methods ADD and DROP, or use ALTER TYPE `method` ADD .

**Related Topics**

- [Oracle Database PL/SQL Language Reference](../lnpls/ALTER-TYPE-statement.md)

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecation of configToolAllCommands Script

The postinstallation check script configToolAllCommands is deprecated in Oracle Database 12c release 1 (12.1).

The script `configToolAllCommands` runs in the response file mode to configure Oracle products after installation. It uses a separate password response file. Starting with Oracle Database 12c release 2 (12.2), `configToolAllCommands` is deprecated. It may be desupported in a future release.

You can now obtain postinstallation checks as part of the installation process. Oracle recommends that you run the Oracle Database or Oracle Grid Infrastructure installer with the option `-executeConfigTools`. You can use the same response file created during installation to complete postinstallation configuration.

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecation of DBMS_DEBUG Package

The DBMS_DEBUG package is deprecated in Oracle Database 12c release 2 (12.2). Oracle recommends that you use DBMS_DEBUG_JDWP.

In earlier releases, PL/SQL included the DBMS_DEBUG package to enable internal and third-party tools to debug PL/SQL programs. The DBMS_DEBUG package provides APIs to set breakpoints, obtain values of variables, and so on. This functionality has been provided by the DBMS_DEBUG_JDWP package for several releases. DBMS_DEBUG_JDWP provides the equivalent PL/SQL debugging capabilities, and it enables seamless debugging of PL/SQL routines when it calls into or is called from server-side Java (OJVM) with Java stored procedures.

**Related Topics**

- [Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_DEBUG_JDWP.md)

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecation of Intelligent Data Placement (IDC)

Intelligent Data Placement is deprecated in Oracle Database 12c release 2 (12.2).

Intelligent Data Placement enables you to specify disk regions on Oracle ASM disks for best performance. Using the disk region settings, you can ensure that frequently accessed data is placed on the outermost (hot) tracks which have greater speed and higher bandwidth. In addition, files with similar access patterns are located physically close, reducing latency. Intelligent Data Placement also enables the placement of primary and mirror extents into different hot or cold regions

This feature is deprecated in Oracle Database 12c release 2 (12.2).

**Related Topics**

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/index.md)

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecation of CONTINUOUS_MINE Option

Starting with Oracle Database 12c Release 2 (12.2.0.1), the LogMiner CONTINUOUS_MINE option is deprecated.

The LogMiner `CONTINUOUS_MINE` option is still supported for backward compatibility reasons. However, Oracle recommends that you discontinue using it. There is no replacement functionality.

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecation of Non-CDB Architecture

The non-CDB architecture was deprecated in Oracle Database 12c. It can be desupported and unavailable in a release after Oracle Database 19c .

Oracle recommends use of the CDB architecture.

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecation of Oracle Administration Assistant for Windows

Oracle Administration Assistant for Windows is deprecated in Oracle Database 12c release 2 (12.2).

Oracle Administration Assistant for Windows is a tool for creating database administrators, operators, users, and roles in Windows. It also allows database service, startup and shutdown configuration, and Windows Registry parameter management.

Instead of using Oracle Administration Assistant for Windows, use native Windows administration tools.

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecation of Oracle Data Provider for .NET PromotableTransaction Setting

The Oracle Data Provider for .NET `PromotableTransaction` setting is deprecated, because it is no longer necessary.

Promotable transactions themselves are not being deprecated. Only this specific setting is deprecated.

The Oracle Data Provider for .NET registry setting `PromotableTransaction` indicates whether the application must keep transactions as local, or if it can begin all single connection transactions as local, and then promote the transaction to distributed when a second connection enlists. This is the concept of promotable transactions.

The Promotable Transaction setting is deprecated in Oracle Database 12c release 2 (12.2). There is no reason not to use promotable transactions. Oracle recommends you accept the default value `promotable`.

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecation of oracle.jdbc.OracleConnection.unwrap()

Starting in Oracle Database 12c release 2 (12.2), the Java package `oracle.jdbc.OracleConnection.unwrap()` is deprecated.

The Java package `oracle.jdbc.OracleConnection.unwrap()` is deprecated in Oracle Database 12c release 2, and later releases. There is no replacement for this package.

Oracle recommends that you replace this JDBC method in your applications with standard Java methods.

**Related Topics**

- <https://support.oracle.com/rs?type=doc&id=2024500.1>

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecation of oracle.jdbc.rowset Package

Starting in Oracle Database 12c release 2 (12.2), the Java `oracle.jdbc.rowset` package is deprecated

Oracle recommends that you use the Standard JDBC RowSet package to replace this feature.

**Related Topics**

- [Oracle Database JDBC Developer’s Guide](../jjdbc/JDBC-Rowsets.md)
- <https://support.oracle.com/rs?type=doc&id=2024500.1>

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecation of oracle.sql.DatumWithConnection Classes

`oracle.sql` classes that extend `oracle.sql.DatumWithConnection` are deprecated in Oracle Database 12c release 2 (12.2), in favor of `oracle.jdbc` extension types.

In previous releases, Oracle Database included Oracle JDBC drivers that provided specific type extensions and performance extensions in both `oracle.sql` and `oracle.jdbc` Java packages. Starting with Oracle Database 12c release 2 (12.2), the `oracle.sql` classes that extend `oracle.sql.DatumWithConnection` are deprecated. The `oracle.jdbc` extensions continue to be supported.

For example, here is a partial list of deprecated `oracle.sql` classes:

- ARRAY

- BFILE

- BLOB

- CLOB

- OPAQUE

- REF

- STRUCT

Oracle recommends that you replace `oracle.sql` classes that extend `oracle.sql.DatumWithConnection` in your applications with standard Java types, or with `oracle.jdbc` extensions.

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecation of Oracle Multimedia Java APIs

The Oracle Multimedia Java APIs are deprecated in Oracle Database 12c release 2.

The following Java APIs are deprecated in Oracle Database 12c Release 2 (12.2), and can be desupported in a future release:

- Oracle Multimedia Java API

- Oracle Multimedia Servlets and JSP Java API

- Oracle Multimedia DICOM Java API

- Oracle Multimedia Mid-Tier Java API

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecation of Oracle Multimedia Support for DICOM

Starting in Oracle Database 12c release 2 (12.2), the Oracle Multimedia DICOM feature is deprecated.

There is no replacement for DICOM support in Oracle Database.

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecation of Multimedia SQL/MM Still Image Standard Support

Starting in Oracle Database 12c release 2 (12.2), Oracle Multimedia SQL/MM Still Image standard support is deprecated.

For image processing operations, Oracle Multimedia developers can call the new ORD_IMAGE PL/SQL package, or call the ORDImage methods.

For image matching, Oracle Database developers can use open source packages, such as OpenCV.

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecation of Unicode Collation Algorithm (UCA) 6.1 Collations

Starting in Oracle Database 12c release 2, the Unicode Collation Algorithm (UCA) 6.1 collations are deprecated.

The Unicode Collation Algorithm (UCA) 6.1 collations (UCA0610\_\*) are deprecated. They can be desupported and unavailable in a future release. Oracle recommends that you use the latest supported version of UCA collations for sorting multilingual data.

**Related Topics**

- [Oracle Database Globalization Support Guide](../nlspg/appendix-A-locale-data.md)

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecation of UNIFIED_AUDIT_SGA_QUEUE_SIZE

Starting in Oracle Database 12c release 2, the initialization parameter UNIFIED_AUDIT_SGA_QUEUE_SIZE is deprecated.

The UNIFIED_AUDIT_SGA_QUEUE_SIZE parameter is deprecated, and the value for this parameter is no longer honored. However, the parameter is currently retained for backward compatibility.

See Oracle Database Security Guide for additional information about Unified Audit records.

**Related Topics**

- [Oracle Database Security Guide](../dbseg/index.md)

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecation of VERIFY_FUNCTION and VERIFY_FUNCTION_11G

The `VERIFY_FUNCTION` and `VERIFY_FUNCTION_11G` password verify functions are deprecated in this release, because they enforce the weaker password restrictions from earlier releases.

Oracle recommends that you use the functions `ORA12C_VERIFY_FUNCTION` and `ORA12C_STRONG_VERIFY_FUNCTION`. These functions enforce stronger, more up-to-date password verification restrictions.

**See Also:**

[Oracle Database Security Guide](../dbseg/configuring-authentication.md)

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecation of V\$MANAGED_STANDBY

The V\$MANAGED_STANDBY view is deprecated in Oracle Database 12c release 2 (12.2.0.1). Oracle recommends that you use the new view V\$DATAGUARD_PROCESS.

The V\$DATAGUARD_PROCESS view includes much more information about processes used by Oracle Data Guard.

**Related Topics**

- [Oracle Database Reference](../refrn/V-MANAGED_STANDBY.md)

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecation of Some XML DB Functions

Starting with Oracle Database 12c release 2 (12.2) the options listed in this topic are deprecated.

The following options are deprecated:

- Oracle XQuery function `ora:contains`. Use XQuery Full Text instead.

- Oracle SQL function XMLRoot. Use SQL/XML function `XMLSerialize()` with a version number instead.

- Nested tables stored as index-ordered tables (IOTs). This includes both the use of option `DBMS_XMLSCHEMA.REGISTER_NT_AS_IOT`, and the use of clause `NESTED TABLE ``N`` STORE AS ... (ORGANIZATION INDEX)` when creating a table with nested-table column `N`. Instead, store nested-table columns using heap storage (the default behavior for PL/SQL procedure `DBMS_XMLSCHEMA.registerSchema`).

- PL/SQL procedure `DBMS_XSLPROCESSOR.CLOB2FILE`. Use `DBMS_LOB.CLOB2FILE` instead.

- PL/SQL function `DBMS_XSLPROCESSOR.READ2CLOB`. Use `DBMS_LOB.LOADCLOBFROMFILE` instead.

- Use of XLink with Oracle XML DB.

- Oracle XML DB Content Connector.

For more information, refer to Oracle XML DB Developer’s Guide.

**Related Topics**

- [Oracle XML DB Developer’s Guide](../adxdb/index.md)

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecated Features for Oracle XML Database

These features are deprecated in Oracle Database 12c Release 1, and can be desupported in a future release.

- `CLOB` storage of `XMLType`, also known as unstructured storage, is deprecated. Use binary XML storage of `XMLType` instead.

  To preserve whitespace in an XML file, store two copies of your original XML document. Use one file as an `XMLType` instance for database use and XML processing, and use the other file as a `CLOB` instance to provide document fidelity.

- Creating an `XMLIndex` index over an XML fragment stored as a `CLOB` instance embedded in object-relational `XMLType` data is deprecated. If you must index the data in such a fragment, then store the document using binary XML storage, instead of object-relational storage.

- The following PL/SQL subprograms in package `DBMS_XMLSCHEMA` are deprecated:

  - `generateSchema`

  - `generateSchemas`

  There are no replacements for these constructs, and there is no workaround for this change.

- PL/SQL package `DBMS_XDB_CONFIG` is new. All Oracle XML((nbsp))DB configuration functions, procedures, and constants are moved from package `DBMS_XDB` to `DBMS_XDB_CONFIG`. These functions, procedures and constants are now deprecated for package `DBMS_XDB`. Use them in package `DBMS_XDB_CONFIG` instead.

  The following is a list of subprograms deprecated in package `DBMS_XDB`:

  - `ADDHTTPEXPIREMAPPING`

  - `ADDMIMEMAPPING`

  - `ADDSCHEMALOCMAPPING`

  - `ADDSERVLET`

  - `ADDSERVLETMAPPING`

  - `ADDSERVLETSECROLE`

  - `ADDXMLEXTENSION`

  - `CFG_GET`

  - `CFG_REFRESH`

  - `CFG_UPDATE`

  - `DELETEHTTPEXPIREMAPPING`

  - `DELETEMIMEMAPPING`

  - `DELETESCHEMALOCMAPPING`

  - `DELETESERVLET`

  - `DELETESERVLETMAPPING`

  - `DELETESERVLETSECROLE`

  - `DELETEXMLEXTENSION`

  - `GETFTPPORT`

  - `GETHTTPPORT`

  - `GETLISTENERENDPOINT`

  - `SETFTPPORT`

  - `SETHTTPPORT`

  - `SETLISTENERENDPOINT`

  - `SETLISTENERLOCALACCESS`

  The following is a list of constants that are deprecated in package `DBMS_XDB`:

  - `XDB_ENDPOINT_HTTP`

  - `XDB_ENDPOINT_HTTP2`

  - `XDB_PROTOCOL_TCP`

  - `XDB_PROTOCOL_TCPS`

- All Oracle SQL functions for updating XML data are deprecated. Use XQuery Update instead for these functions . The following is a list of deprecated XML updating functions:

  - `updateXML`

  - `insertChildXML`

  - `insertChildXMLbefore`

  - `insertChildXMLafter`

  - `insertXMLbefore`

  - `insertXMLafter`

  - `appendChildXML`

  - `deleteXML`

- Oracle SQL function `sys_xmlgen` is deprecated. Use the SQL/XML generation functions instead.

- The following Oracle XQuery functions are deprecated. Use the corresponding standard XQuery functions instead, that is, the functions with the same names but with namespace prefix `fn`.

  - `ora:matches` – use `fn:matches` instead

  - `ora:replace` – use `fn:replace` instead

- The following Oracle constructs that provide support for XML translations are deprecated.

  - PL/SQL package `DBMS_XMLTRANSLATIONS`

  - Oracle XPath function `ora:translate`

  - XML Schema annotations `xdb:maxOccurs`, `xdb:srclang`, and `xdb:translate`

  There are no replacements for these constructs, and there is no workaround for this change.

- The following XML Schema annotations are deprecated:

  - `xdb:defaultTableSchema`

  - `xdb:maintainOrder`

  - `xdb:mapUnboundedStringToLob`

  - `xdb:maxOccurs`

  - `xdb:SQLCollSchema`

  - `xdb:SQLSchema`

  - `xdb:srclang`

  - `xdb:storeVarrayAsTable`

  - `xdb:translate`

  There are no replacements for these constructs, and there is no workaround for this change.

- The value `xml_clobs` for export parameter data_options is deprecated starting with Oracle Database 12c.

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

#### Deprecated Initialization Parameters in Oracle Database 12c Release 2 (12.2)

To understand changes and replacements in parameter settings, review the parameters deprecated in the 12.2 release. These parameters can be removed in a later release.

##### O7_DICTIONARY_ACCESSIBILITY Initialization parameter

The initialization parameter `O7_DICTIONARY_ACCESSIBILITY` controls restrictions on `SYSTEM` privileges. If the parameter is set to `TRUE`, then access to objects in the SYS schema is allowed. The default setting is FALSE. This default setting prevents system privileges that allow access to objects in any schema from allowing access to objects in the SYS schema. The `O7_DICTIONARY_ACCESSIBILITY` parameter is deprecated.

##### ASM_PREFERRED_READ_FAILURE_GROUPS Initialization Parameter

The `ASM_PREFERRED_READ_FAILURE_GROUPS` initialization parameter is deprecated in Oracle Automatic Storage Management 12c release 2 (12.2.0.1). Starting with Oracle Automatic Storage Management (Oracle ASM) 12c release 2 (12.2.0.1), specifying the preferred read failure groups is done automatically, so the use of the `ASM_PREFERRED_READ_FAILURE_GROUPS` initialization parameter is no longer required. Use the PREFERRED_READ.ENABLED disk group attribute to control the preferred read functionality.

##### PARALLEL_ADAPTIVE_MULTI_USER Initialization Parameter

The initialization parameter `PARALLEL_ADAPTIVE_MULTI_USER` specifies if you want to use an adaptive algorithm to improve performance in multi-user environments that use parallel execution. This parameter is deprecated, and the default value is now `FALSE`. There is no replacement for this parameter. Oracle recommends that you use the Oracle Database feature Parallel Statement Queuing to obtain parallel execution performance gains.

##### UTL_FILE_DIR Initialization Parameter

The initialization parameter `UTL_FILE_DIR` specifies accessible directories for PL/SQL file I/O. This parameter is deprecated, and Oracle recommends that you do not provide `UTL_FILE_DIR` access. Oracle recommends that you instead use the directory object feature, which replaces `UTL_FILE_DIR`. Directory objects provide the following benefits:

- They offer more flexibility and granular control to the `UTL_FILE` application administrator

- They can be maintained dynamically, without shutting down the database

- They are consistent with other Oracle tools.

**Related Topics**

- [Oracle Database Reference](../refrn/initialization-parameters-2.md)

**Parent topic:** Oracle Database 12c Release 2 (12.2) Behavior Changes, Desupports, and Deprecations

### Oracle Database 12c Release 1 (12.1) Behavior Changes, Desupports, and Deprecations

Review for descriptions of Oracle Database 12c Release 1 (12.1) changes.

- Behavior Changes for Oracle Database 12c Release 1 (12.1)
  Review these behavior changes to help plan for upgrades to Oracle Database 12c release 1 (12.1)
- Desupported Features in Oracle Database 12c Release 1 (12.1)
  Review this list of desupported features as part of your upgrade planning.
- Deprecated Features in Oracle Database 12c Release 2 (12.2)
  Review the deprecated features listed in this section to prepare to use alternatives after you upgrade.
- Deprecated Initialization Parameters in Oracle Database 12c Release 1 (12.1)
  As part of your upgrade plan, review the initialization parameters that are deprecated in Oracle Database 12c Release 1 (12.1).
- Deprecated Views in Oracle Database 12c Release 1 (12.1)
  Review the deprecated features listed in this section to prepare to use alternatives after you upgrade. Features deprecated in an earlier release can be desupported in a later release.

**Parent topic:** Oracle Database Changes, Desupports, and Deprecations

#### Behavior Changes for Oracle Database 12c Release 1 (12.1)

Review these behavior changes to help plan for upgrades to Oracle Database 12c release 1 (12.1)

- Error Associated with catupgrd.sql Run Without PARALLEL=NO
  If you choose to run the `catupgrd.sql` script instead of running `catctl.pl`), then you now must provide information for an additional input parameter, PARALLEL.
- Change for Standalone Deinstallation Tool
  Starting with Oracle Database 12c, the deinstallation standalone utility is replaced with a deinstall option using Oracle Universal Installer (OUI).
- Changes to Security Auditing Features
  The full set of auditing features are available automatically in Oracle Database 12c release 1 (12.1) and later releases.
- Upgrading a System that Did Not Have SQLNET.ALLOWED_LOGON_VERSION Parameter Setting
  Review the parameter setting for SQLNET.ALLOWED_LOGON_VERSION_SERVER to determine its implications for security and client connections to the upgraded database.
- Oracle Warehouse Builder (OWB) Not Installed with Oracle Database
  Oracle Warehouse Builder must be installed separately.
- About Upgrading Oracle Database Release 10.2 or 11.1 and OCFS and RAW Devices
  If you are upgrading an Oracle Database release 10.2.0.5 or release 11.1.0.7 environment that stores Oracle Clusterware files on OCFS on Windows or RAW devices, then you cannot directly upgrade to Oracle Database 12c release 1 (12.1).
- Change to VARCHAR2, NVARCHAR2, and RAW Datatypes
  You can increase the MAX_STRING_SIZE value for these datatypes to 32767 bytes in Oracle Database 12c Release 1 (12.1) and later releases.
- Changed Default for RESOURCE_LIMIT Parameter
  RESOURCE_LIMIT is set to TRUE by default.
- Oracle XML DB is Mandatory and Cannot Be Uninstalled
  Starting with Oracle Database 12c, Oracle XML DB is a mandatory component of Oracle Database.
- Direct NFS Enabled By Default for Oracle RAC
  In Oracle Database 12c release 1 (12.1) and later releases, Direct NFS (DNFS) is enabled by default with Oracle Real Application Clusters (Oracle RAC) installations.

**Parent topic:** Oracle Database 12c Release 1 (12.1) Behavior Changes, Desupports, and Deprecations

##### Error Associated with catupgrd.sql Run Without PARALLEL=NO

If you choose to run the `catupgrd.sql` script instead of running `catctl.pl`), then you now must provide information for an additional input parameter, PARALLEL.

For example:

    SQL> catupgrd.sql PARALLEL=NO

If you run `catupgrd.sql` without the parameter, then Oracle displays the following error message:

    NOTE

    The catupgrd.sql script is being deprecated in the 12.1 release of
    Oracle Database. Customers are encouraged to use catctl.pl as
    the replacement for catupgrd.sql when upgrading the database dictionary.

                    cd $ORACLE_HOME/rdbms/admin
                    $ORACLE_HOME/perl/bin/perl catctl.pl -n 4 catupgrd.sql

    Refer to the Oracle Database Upgrade Guide for more information.

    This database upgrade procedure must be called with the following
    argument when invoking from the SQL prompt:

                    @catupgrd.sql PARALLEL=NO

**Parent topic:** Behavior Changes for Oracle Database 12c Release 1 (12.1)

##### Change for Standalone Deinstallation Tool

Starting with Oracle Database 12c, the deinstallation standalone utility is replaced with a deinstall option using Oracle Universal Installer (OUI).

You can also run the deinstallation tool from the base directory of the installation media for Oracle Database, Oracle Database Client, or Oracle Grid Infrastructure.

Run the deinstallation tool by using the `runInstaller` command on Linux and UNIX, or `setup.exe` on Windows, with the `-deinstall` and `-home` options.

**See Also:**

- [Oracle Database Installation Guide](../install-and-upgrade.md) for your operating system for information about using OUI and `runInstaller`

- [Oracle Grid Infrastructure Installation Guide](../install-and-upgrade.md) for your operating system

**Parent topic:** Behavior Changes for Oracle Database 12c Release 1 (12.1)

##### Changes to Security Auditing Features

The full set of auditing features are available automatically in Oracle Database 12c release 1 (12.1) and later releases.

The auditing functionality is redesigned in Oracle Database 12c. When you create a new database with Oracle Database 12c, the full set of auditing enhancement features are automatically available. If you upgrade from an earlier release, then you are given the option of using some of the new audit features and the audit functionality from the release from which you upgraded. Oracle strongly recommends that you migrate to the full set of the latest audit features.

**See Also:**

[Oracle Database Security Guide](../dbseg/release-changes.md) for information about new auditing features and changes for security

**Parent topic:** Behavior Changes for Oracle Database 12c Release 1 (12.1)

##### Upgrading a System that Did Not Have SQLNET.ALLOWED_LOGON_VERSION Parameter Setting

Review the parameter setting for SQLNET.ALLOWED_LOGON_VERSION_SERVER to determine its implications for security and client connections to the upgraded database.

If you are upgrading a system that did not have a SQLNET.ALLOWED_LOGON_VERSION parameter setting (that is, it was using the default SQLNet setting `8`), then the new default value for the login verifier is set to `11`, which sets the 11g password verifier (`11G`) in Oracle Database 18c. This value permits Oracle Database 10g, 11g, 12c, and 18c clients to connect to the database, as well as Oracle Database 19c clients.

If you do not provide a parameter setting for SQLNET.ALLOWED_LOGON_VERSION_SERVER (or the deprecated SQLNET.ALLOWED_LOGON_VERSION) in the upgraded Oracle Database server, then the Oracle Database 19c default is `11`. This value enables connections from clients using releases earlier than Oracle Database release 11.2.0.3 that have not applied critical patch update CPU Oct 2012, or later patches, and that must use the Oracle Database 10g verifier (`10G`) to connect.

The higher the setting, the more restrictive the use of verifiers. A setting of `8` permits the most verifiers. For example, the `10G`, `11G`, and `12C` verifiers are all permitted with this setting. A setting of `12a` only permits the 12C verifier. For greater security, consider setting SQLNET.ALLOWED_LOGON_VERSION_SERVER to 12a. A setting of 12 permits both the 11G and 12C verifier to be used for authentication.

**See Also:**

[Oracle Database Security Guide](../dbseg/configuring-authentication.md) for additional information about verifier settings and client access

**Parent topic:** Behavior Changes for Oracle Database 12c Release 1 (12.1)

##### Oracle Warehouse Builder (OWB) Not Installed with Oracle Database

Oracle Warehouse Builder must be installed separately.

Starting with Oracle Database 12c, Oracle Warehouse Builder (OWB) is not installed as part of the software for Oracle Database. An installer for Oracle Warehouse Builder is available on Oracle Technology Network. OWB components that may exist from earlier releases are not upgraded as part of the Oracle Database upgrade process.

**Parent topic:** Behavior Changes for Oracle Database 12c Release 1 (12.1)

##### About Upgrading Oracle Database Release 10.2 or 11.1 and OCFS and RAW Devices

If you are upgrading an Oracle Database release 10.2.0.5 or release 11.1.0.7 environment that stores Oracle Clusterware files on OCFS on Windows or RAW devices, then you cannot directly upgrade to Oracle Database 12c release 1 (12.1).

You must first perform an interim upgrade to Oracle Database release 11.2, and then migrate Oracle Clusterware files to Oracle Automatic Storage Management (Oracle ASM). Then you can upgrade from release 11.2 to Oracle Database 12c release 1 (12.1).

**See Also:**

- <http://www.oracle.com/technetwork/documentation/index.html> to obtain Oracle Database Upgrade Guide for Oracle Database 11g Release 2 (11.2)

- [Oracle Database Installation Guide](../install-and-upgrade.md) for your operating system for procedures on installing the Oracle Database software

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/migrate-db-to-asm.md) for information about migrating a database to use Oracle Automatic Storage Management (Oracle ASM)

**Parent topic:** Behavior Changes for Oracle Database 12c Release 1 (12.1)

##### Change to VARCHAR2, NVARCHAR2, and RAW Datatypes

You can increase the MAX_STRING_SIZE value for these datatypes to 32767 bytes in Oracle Database 12c Release 1 (12.1) and later releases.

Starting with Oracle Database 12c Release 1 (12.1), you can increase the maximum size of the VARCHAR2, NVARCHAR2, and RAW datatypes to 32767 bytes. This size increase is possible if you set the COMPATIBLE initialization parameter to 12.0 or higher, and you set the MAX_STRING_SIZE initialization parameter to EXTENDED. This size increase is available for non-CDB Oracle Database instances, and for PDBs in multitenant architecture.

If you want to make this change, then you must run the `utl32k.sql` script in UPGRADE mode. After you run the script, you can set MAX_STRING_SIZE to EXTENDED.

**Caution:**

When you increase the COMPATIBLE initialization to 12.0 or higher, you cannot reverse this change.

**Parent topic:** Behavior Changes for Oracle Database 12c Release 1 (12.1)

##### Changed Default for RESOURCE_LIMIT Parameter

RESOURCE_LIMIT is set to TRUE by default.

The Oracle Database `RESOURCE_LIMIT` parameter determines if resource limits are enforced in database profiles. In this release, the `RESOURCE_LIMIT` parameter is set to `TRUE` by default. If Oracle resource limits are disabled, then any defined profile limits are ignored. This behavior does not apply to password resources.

Check the resource_limit parameter setting by entering the following SQL\*Plus command:

    SQL> select value from v$parameter where name = 'resource_limit';

**Parent topic:** Behavior Changes for Oracle Database 12c Release 1 (12.1)

##### Oracle XML DB is Mandatory and Cannot Be Uninstalled

Starting with Oracle Database 12c, Oracle XML DB is a mandatory component of Oracle Database.

You cannot uninstall Oracle XML DB, and there is no option to exclude it when you create an Oracle Database. Oracle XML DB is automatically installed or upgraded when you upgrade an existing Oracle Database to Oracle Database 12c.

**Parent topic:** Behavior Changes for Oracle Database 12c Release 1 (12.1)

##### Direct NFS Enabled By Default for Oracle RAC

In Oracle Database 12c release 1 (12.1) and later releases, Direct NFS (DNFS) is enabled by default with Oracle Real Application Clusters (Oracle RAC) installations.

By default, Direct NFS Client is installed in an enabled state for Oracle RAC installations. This is different from Oracle Database single-instance installations, in which you have to enable Direct NFS, and the Direct NFS Client is disabled by default as part of installation. If you upgrade an Oracle RAC Oracle Database release to Release 12.1 or later releases, and you do not have Direct NFS enabled on your source database, then you encounter the error message `ORA-17500: ODM err:Operation not permitted`.

For more information about this change, and to review options in preparation for your upgrade, refer to My Oracle Support notes 954425.1, and 1966267.1

**Related Topics**

- [My Oracle Support Doc ID 954425.1](https://support.oracle.com/rs?type=doc&id=954425.1)
- [My Oracle Support Doc ID 1966267.1](https://support.oracle.com/rs?type=doc&id=1966267.1)

**Parent topic:** Behavior Changes for Oracle Database 12c Release 1 (12.1)

#### Desupported Features in Oracle Database 12c Release 1 (12.1)

Review this list of desupported features as part of your upgrade planning.

- Desupport for Raw Storage Devices
  Starting with Oracle Database 12c release 1 (12.1), block file storage on raw devices is not supported.
- Desupport of ALTER INDEX OPTIMIZE for Text Indexes
  The ALTER INDEX OPTIMIZE `[token index_token | fast | full [maxtime (time | unlimited)]` operation is not supported for Oracle Database 12c.
- Desupport of CLEANUP_ORACLE_BASE Property
  In Oracle Database 12c, the `CLEANUP_ORACLE_BASE` property is removed for response file (silent) deinstalls.
- Desupport of Oracle Enterprise Manager Database Control
  Starting with Oracle Database 12c, Oracle Enterprise Manager Database Control is desupported and is no longer available.
- Desupported Cipher Suites for Secure Sockets Layer (SSL)
  Review this list of desupported cipher suites if you use Oracle Advanced Security.
- Desupport of Database Rules Manager (RUL) and Expression Filter (EXF)
  Starting with Oracle Database 12c release 1, the Expression Filter (EXF) and Database Rules Manager (RUL) features are desupported.
- Desupport of cluvfy comp cfs for OCFS
  The `cluvfy comp cfs` component verification command option is removed from Oracle Database 12c release 1 (12.1).
- Desupport of Change Data Capture
  Oracle Change Data Capture is not included in Oracle Database 12c and is replaced with Oracle GoldenGate.
- Desupported Features in Oracle Data Mining
  These Oracle Data Mining features are desupported in Oracle Database 12c.
- Desupported Implicit Connection Caching
  Implicit Connection Caching is desupported in Oracle Database 12c.
- Desupport of ABN Models for Oracle Data Mining Upgrades
  Starting with Oracle Database 12c, Oracle is desupporting the Data Mining Java API and the Adaptive Bayes Network (ABN) algorithm.
- Desupport of OLAP Catalog (AMD)
  Starting with Oracle Database 12c, the Common Warehouse Metamodel (CWM) standard is desupported for the OLAP catalog (AMD).
- Desupport of CSSCAN and CSALTER for Oracle Globalization
  Oracle Database 12c includes Oracle Database Migration Assistant for Unicode (DMU), and Oracle is desupporting the legacy database tools CSSCAN and CSALTER.
- Desupport of Oracle Net Connection Pooling
  In Oracle Database 12c, Oracle Net connection pooling is no longer supported.
- Desupport of Oracle Net Listener Password
  In Oracle Database 12c, the Oracle Net Listener password feature is no longer supported.
- Desupport of Oracle Names
  Oracle Names was desupported as a naming method in Oracle Database 11g. You must migrate to directory naming.
- Desupport of Oracle Names Control Utility for Oracle Net Services
  The Oracle Names Control Utility is desupported. Starting with Oracle Database 10g, it is not available.
- Desupport of CTXXPATH in Oracle Text and Oracle XML DB
  The `CTXSYS.CTXXPATH` index is desupported, starting with Oracle Database 12c Release 1 (12.1).
- Desupport of SQLNET.KERBEROS5_CONF_MIT Parameter for Oracle Net Services
  The SQLNET.KERBEROS5_CONF_MIT networking parameter is no longer needed and is not supported in `sqlnet.ora`.
- Desupport of ALTER INDEX OPTIMIZE for Text Indexes
  The ALTER INDEX OPTIMIZE `[token index_token | fast | full [maxtime (time | unlimited)]` operation is not supported for Oracle Database 12c.
- Desupport of SYNC \[MEMORY memsize\] for Text Indexes
  The `SYNC [MEMORY memsize]` operation is not supported for Oracle Database 12c
- Desupported Features on Microsoft Windows Platforms
  Review these topics to learn which features are deprecated or desupported with Oracle Database 12c for Microsoft Windows.

**Parent topic:** Oracle Database 12c Release 1 (12.1) Behavior Changes, Desupports, and Deprecations

##### Desupport for Raw Storage Devices

Starting with Oracle Database 12c release 1 (12.1), block file storage on raw devices is not supported.

You must migrate any data files stored on raw devices to Oracle ASM, to a cluster file system, or to a Network File System (NFS).

This desupport guideline also applies to OCR and voting disk files for Oracle Clusterware. You cannot store OCR or voting disk files on raw devices. Before you start the upgrade, you must move Oracle Clusterware files from raw devices to a supported storage option.

**Parent topic:** Desupported Features in Oracle Database 12c Release 1 (12.1)

##### Desupport of ALTER INDEX OPTIMIZE for Text Indexes

The ALTER INDEX OPTIMIZE `[token index_token | fast | full [maxtime (time | unlimited)]` operation is not supported for Oracle Database 12c.

To optimize your index, use CTX_DDL.OPTIMIZE_INDEX.

**See Also:**

[Oracle Text Reference](../ccref/CTX_DDL-package.md) for information about OPTIMIZE_INDEX

**Parent topic:** Desupported Features in Oracle Database 12c Release 1 (12.1)

##### Desupport of CLEANUP_ORACLE_BASE Property

In Oracle Database 12c, the `CLEANUP_ORACLE_BASE` property is removed for response file (silent) deinstalls.

It is no longer supported to use CLEANUP_ORACLE_BASE to remove an Oracle base during silent or response file mode deinstalls.

**Parent topic:** Desupported Features in Oracle Database 12c Release 1 (12.1)

##### Desupport of Oracle Enterprise Manager Database Control

Starting with Oracle Database 12c, Oracle Enterprise Manager Database Control is desupported and is no longer available.

Oracle introduces Oracle Enterprise Manager Database Express (Oracle EM Express) as a replacement. Oracle EM Express is installed when you upgrade to Oracle Database 12c.

You can carry out a manual configuration of the HTTP port for Oracle EM Express:

1.  Look in the `init.ora/spfile` (default setting) for the following string:

        dispatchers=(PROTOCOL=TCP)(SERVICE=sample XDB)

    Check the Oracle EM Express port configuration:

        SQL> select DBMS_XDB_CONFIG.getHTTPport() from dual;
        SQL> select DBMS_XDB_CONFIG.getHTTPSport() from dual;

2.  Set new ports. For example:

        SQL> exec DBMS_XDB_CONFIG.setHTTPport(5500);
        SQL> exec DBMS_XDB_CONFIG.setHTTPSport(8080);

3.  Access the Oracle EM Express home page in the browser. For example, using the settings you have provided, check the following path, where `database` is your SID, `hostname` is your fully qualified domain name, and `port` is the port you assigned:

        http://database-hostname:port/em

    For example:

        http://localhost:5500/em

4.  Repeat this configuration step for the CDB, and for every PDB, using different port numbers.

**See Also:**

- [Oracle Database Concepts](../cncpt/concepts-for-database-administrators.md) for an overview of Oracle EM Express

- [Oracle Database 2 Day DBA](../admqs/getting-started-with-database-administration.md) for information about using Oracle EM Express

- [Oracle Database Concepts](../cncpt/concepts-for-database-administrators.md) for an introduction to Oracle Enterprise Manager Cloud Control

**Parent topic:** Desupported Features in Oracle Database 12c Release 1 (12.1)

##### Desupported Cipher Suites for Secure Sockets Layer (SSL)

Review this list of desupported cipher suites if you use Oracle Advanced Security.

Oracle Advanced Security has desupported the following cipher suites in Oracle Database 12c:

- `SSL_DH_anon_WITH_DES_CBC_SHA`

- `SSL_RSA_EXPORT_WITH_DES40_CBC_SHA`

- `SSL_RSA_EXPORT_WITH_RC4_40_MD5`

- `SSL_RSA_WITH_DES_CBC_SHA`

**See Also:**

[Oracle Database Security Guide](../dbseg/configuring-authentication.md) for information about supported SSL cipher suites

**Parent topic:** Desupported Features in Oracle Database 12c Release 1 (12.1)

##### Desupport of Database Rules Manager (RUL) and Expression Filter (EXF)

Starting with Oracle Database 12c release 1, the Expression Filter (EXF) and Database Rules Manager (RUL) features are desupported.

If you are using Rules Manager, then Oracle recommends that you migrate to Oracle Business Rules, which is a component of Oracle Fusion Middleware. The Continuous Query Notification feature of Oracle Database replaces Expression Filter.

This script is executed by the upgrade process. To remove these components before upgrading, run the `catnoexf.sql` script before the upgrade. The `catnoexf.sql` script is located under `ORACLE_HOME``/rdbms/admin/`.

**See Also:**

<https://support.oracle.com/CSP/main/article?cmd=show&type=NOT&id=1244535.1>

**Parent topic:** Desupported Features in Oracle Database 12c Release 1 (12.1)

##### Desupport of cluvfy comp cfs for OCFS

The `cluvfy comp cfs` component verification command option is removed from Oracle Database 12c release 1 (12.1).

The Cluster Verification Utility (`cluvfy`) option `comp cfs` is removed in Oracle Database 12.1, because Oracle Cluster File System (OCFS) is no longer supported.

**See Also:**

[Oracle Clusterware Administration and Deployment Guide](../cwadd/oracle-clusterware-administration.md) for more information about cluster administration

**Parent topic:** Desupported Features in Oracle Database 12c Release 1 (12.1)

##### Desupport of Change Data Capture

Oracle Change Data Capture is not included in Oracle Database 12c and is replaced with Oracle GoldenGate.

**See Also:**

[Oracle GoldenGate documentation](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/upgrd&id=ogg) for information

**Parent topic:** Desupported Features in Oracle Database 12c Release 1 (12.1)

##### Desupported Features in Oracle Data Mining

These Oracle Data Mining features are desupported in Oracle Database 12c.

- The Oracle Data Mining Java API is no longer available. The programmatic interfaces to Oracle Data Mining 12c consist of two PL/SQL packages, `DBMS_DATA_MINING` and `DBMS_DATA_MINING_TRANSFORM`, and a family of SQL language functions for scoring data.

  **See Also:**

  [Oracle Data Mining User's Guide](../dmapi/data-mining-PL-SQL-packages.md) for information about the Data Mining PL/SQL packages

- The Adaptive Bayes Network (ABN) algorithm is no longer available. The Decision Tree algorithm replaces ABN in Oracle Data Mining 12c.

  **See Also:**

  [Oracle Data Mining Concepts](../dmapi/decision-tree.md) for information about the Decision Tree algorithm

**Parent topic:** Desupported Features in Oracle Database 12c Release 1 (12.1)

##### Desupported Implicit Connection Caching

Implicit Connection Caching is desupported in Oracle Database 12c.

Use Universal Connection Pool instead.

**See Also:**

[Oracle Universal Connection Pool for JDBC Developer's Guide](../jjucp/index.md) for information

**Parent topic:** Desupported Features in Oracle Database 12c Release 1 (12.1)

##### Desupport of ABN Models for Oracle Data Mining Upgrades

Starting with Oracle Database 12c, Oracle is desupporting the Data Mining Java API and the Adaptive Bayes Network (ABN) algorithm.

Because Oracle is desupporting these features, you cannot upgrade models created by the Oracle Data Mining Java API from Oracle Database release 11g to Oracle Database 12c. All other models and metadata are upgraded automatically during the upgrade from Oracle Database 11g to Oracle Database 12c. ABN models can be upgraded, but you cannot use them in an Oracle Database 12c database. You must drop ABN models either before the upgrade or afterward. You can replace ABN models by building new classification models in the Oracle Database 12c database.

**See Also:**

[Oracle Data Mining User's Guide](../dmapi/data-mining-API.md) for information about the Data Mining API and data mining models

**Parent topic:** Desupported Features in Oracle Database 12c Release 1 (12.1)

##### Desupport of OLAP Catalog (AMD)

Starting with Oracle Database 12c, the Common Warehouse Metamodel (CWM) standard is desupported for the OLAP catalog (AMD).

CWM standard support was deprecated in Oracle Database 11g Release 2 (11.2). If your existing database has CWM metadata in the OLAP catalog, and you upgrade to Oracle Database 12c, then the upgraded database has the AMD component. If the database you upgrade does not have the AMD component, then the upgraded Oracle Database 12c database also does not have the AMD component, because new installations for Oracle Database 12c do not include AMD. If your database has the AMD component, and you want to remove it, then run the `catnoamd.sql` script that is located in the path`ORACLE_HOME``/olap/admin/catnoamd.sql`. You can run this script either before or after you complete your upgrade.

**Note:**

If the OLAP catalog exists in the database you are upgrading, then you can see `AMD OLAP Catalog OPTION OFF` and invalid CWM OLAP objects. You can safely ignore the invalid OLAP objects, because they are not needed.

**See Also:**

- Oracle OLAP Java API Developer’s Guide for information about OLAP Java API metadata

- Oracle OLAP User’s Guide for more information about the OLAP option of Oracle Database and online analytic processing

**Parent topic:** Desupported Features in Oracle Database 12c Release 1 (12.1)

##### Desupport of CSSCAN and CSALTER for Oracle Globalization

Oracle Database 12c includes Oracle Database Migration Assistant for Unicode (DMU), and Oracle is desupporting the legacy database tools CSSCAN and CSALTER.

DMU provides a complete end-to-end Unicode migration solution for database administrators. Starting with Oracle Database 12c, DMU is included with Oracle Database. The CSSCAN and CSALTER tools are no longer included or supported.

**Parent topic:** Desupported Features in Oracle Database 12c Release 1 (12.1)

##### Desupport of Oracle Net Connection Pooling

In Oracle Database 12c, Oracle Net connection pooling is no longer supported.

Oracle Net connection pooling was deprecated in Oracle Database 11g. This deprecation included the `DISPATCHERS` attributes `TICKS`, `SESSIONS`, and `CONNECTIONS`.

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/configuring-shared-server-architecture.md) for information about configuring dispatchers

[Oracle Database Net Services Administrator's Guide](../netrf/index.md) for information about Oracle Connection Manager Parameters (cman.ora)

**Parent topic:** Desupported Features in Oracle Database 12c Release 1 (12.1)

##### Desupport of Oracle Net Listener Password

In Oracle Database 12c, the Oracle Net Listener password feature is no longer supported.

This change does not cause a loss of security, because Oracle Database enforces authentication through local operating system authentication.

**Related Topics**

- [Oracle Database Net Services Reference](../netrf/listener-control-utility.md)

**Parent topic:** Desupported Features in Oracle Database 12c Release 1 (12.1)

##### Desupport of Oracle Names

Oracle Names was desupported as a naming method in Oracle Database 11g. You must migrate to directory naming.

**See Also:**

[Oracle Database Net Services Administrator's Guide](../netag/configuring-naming-methods.md) for additional information about migrating to directory naming

**Parent topic:** Desupported Features in Oracle Database 12c Release 1 (12.1)

##### Desupport of Oracle Names Control Utility for Oracle Net Services

The Oracle Names Control Utility is desupported. Starting with Oracle Database 10g, it is not available.

Desupport of the Oracle Names Control Utility includes desupporting all the related control utility commands. Oracle Database clients cannot use a Names Server to resolve connect strings. Migrate your applications to Oracle Internet Directory with LDAP directory naming.

**See Also:**

[Oracle Database Net Services Reference](../netag/configuring-naming-methods.md) for information about configuring the directory naming method

**Parent topic:** Desupported Features in Oracle Database 12c Release 1 (12.1)

##### Desupport of CTXXPATH in Oracle Text and Oracle XML DB

The `CTXSYS.CTXXPATH` index is desupported, starting with Oracle Database 12c Release 1 (12.1).

The desupport of `CTXSYS.CTXXPATH` does not affect `CTXCAT`. Use `XMLIndex` indexes instead.

**Parent topic:** Desupported Features in Oracle Database 12c Release 1 (12.1)

##### Desupport of SQLNET.KERBEROS5_CONF_MIT Parameter for Oracle Net Services

The SQLNET.KERBEROS5_CONF_MIT networking parameter is no longer needed and is not supported in `sqlnet.ora`.

By default, the value of SQLNET.KERBEROS5_CONF_MIT is set to `FALSE`. This parameter setting has no affect on the Kerberos configuration. In previous releases, when SQLNET.KERBEROS5_CONF_MIT is set to TRUE, the parameter set parsing in a format as specified by MIT Kerberos 5. However, this parameter setting is no longer required. Starting with Oracle Database 12c, only MIT Kerberos 5 configuration is supported.

**See Also:**

[Oracle Database Net Services Reference](../netrf/index.md) for information about Kerberos parameters for the `sqlnet.ora` file

**Parent topic:** Desupported Features in Oracle Database 12c Release 1 (12.1)

##### Desupport of ALTER INDEX OPTIMIZE for Text Indexes

The ALTER INDEX OPTIMIZE `[token index_token | fast | full [maxtime (time | unlimited)]` operation is not supported for Oracle Database 12c.

To optimize your index, use CTX_DDL.OPTIMIZE_INDEX.

**See Also:**

[Oracle Text Reference](../ccref/CTX_DDL-package.md) for information about OPTIMIZE_INDEX

**Parent topic:** Desupported Features in Oracle Database 12c Release 1 (12.1)

##### Desupport of SYNC \[MEMORY memsize\] for Text Indexes

The `SYNC [MEMORY memsize]` operation is not supported for Oracle Database 12c

To synchronize your index, use `CTX_DDL.SYNC_INDEX`.

**Related Topics**

- [Oracle Text Reference](../ccref/CTX_DDL-package.md)

**Parent topic:** Desupported Features in Oracle Database 12c Release 1 (12.1)

##### Desupported Features on Microsoft Windows Platforms

Review these topics to learn which features are deprecated or desupported with Oracle Database 12c for Microsoft Windows.

- Desupport of Oracle COM Automation on Windows
  Oracle Database 12c does not contain Oracle COM Automation.
- Desupport of Oracle Objects for OLE
  Oracle Database 12c does not contain Oracle Objects for OLE on Microsoft Windows systems.
- Desupport of Oracle Counters for Windows Performance Monitor
  Oracle Database 12c does not contain Oracle Counters for Windows Performance Monitor.
- Desupport of Oracle Cluster File System (OCFS) on Windows
  Starting with Oracle Database 12c, Oracle Cluster File System (OCFS) is desupported on Windows. Support and distribution of OCFS on Linux (OCFS and OCFS2) remains unaffected by this desupport notice.

**Parent topic:** Desupported Features in Oracle Database 12c Release 1 (12.1)

###### Desupport of Oracle COM Automation on Windows

Oracle Database 12c does not contain Oracle COM Automation.

This feature was deprecated in Oracle Database 11g, which is the last database release that contains the database component Oracle COM Automation. Oracle recommends that you migrate your Oracle COM applications to current technology, such as the .NET Framework.

**See Also:**

<https://support.oracle.com/CSP/main/article?cmd=show&type=NOT&id=1175293.1>

**Parent topic:** Desupported Features on Microsoft Windows Platforms

###### Desupport of Oracle Objects for OLE

Oracle Database 12c does not contain Oracle Objects for OLE on Microsoft Windows systems.

Oracle Objects for OLE is deprecated in Oracle Database 11g. You can migrate your code to the OLE DB data access standard and ActiveX Data Objects (ADO), or you can migrate your applications to .NET (or Java or another application architecture) and use another driver.

**See Also:**

<https://support.oracle.com/CSP/main/article?cmd=show&type=NOT&id=1175303.1>

**Parent topic:** Desupported Features on Microsoft Windows Platforms

###### Desupport of Oracle Counters for Windows Performance Monitor

Oracle Database 12c does not contain Oracle Counters for Windows Performance Monitor.

Oracle Counters for Windows Performance Monitor was deprecated in Oracle Database 11g. The counters are not installed by default in earlier releases, and the counters only work on Windows. For monitoring, Oracle recommends that you use Oracle Enterprise Manager Cloud Control.

**See Also:**

<https://support.oracle.com/CSP/main/article?cmd=show&type=NOT&id=1175297.1>

**Parent topic:** Desupported Features on Microsoft Windows Platforms

###### Desupport of Oracle Cluster File System (OCFS) on Windows

Starting with Oracle Database 12c, Oracle Cluster File System (OCFS) is desupported on Windows. Support and distribution of OCFS on Linux (OCFS and OCFS2) remains unaffected by this desupport notice.

Databases currently using OCFS on Windows to host either the Oracle cluster files (Oracle Cluster Registry and voting files) or database files or both need to have these files migrated off OCFS before upgrading to Oracle Database 12c.

**See Also:**

- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/migrate-db-to-asm.md) for information about migrating a database to use Oracle Automatic Storage Management (Oracle ASM)

- <https://support.oracle.com/CSP/main/article?cmd=show&type=NOT&id=1392280.1>

**Parent topic:** Desupported Features on Microsoft Windows Platforms

#### Deprecated Features in Oracle Database 12c Release 2 (12.2)

Review the deprecated features listed in this section to prepare to use alternatives after you upgrade.

- Deprecation of Non-CDB Architecture
  The non-CDB architecture is deprecated in Oracle Database 12c. It can be desupported and unavailable in a release after Oracle Database 19c.
- Deprecation of catupgrd.sql Script and Introduction of Parallel Upgrade Utility
  In Oracle Database 12c release 1 (12.1), Oracle recommends that you use the Parallel Upgrade Utility (`catctl.pl`instead of `catupgrd.sql` to enable parallel upgrades.
- DELETE_CATALOG_ROLE Deprecated
  The `DELETE_CATALOG_ROLE` database role is deprecated in Oracle Database 12c.
- Deprecated Functions and Parameters in Oracle Label Security
  Nine Oracle Label Security features are deprecated in Oracle Database 12c release 1.
- Deprecated API for Oracle Database Vault
  The DVSYS.DBMS_MACADM.SYNC_RULES procedure is deprecated, because its functionality is built into the rule creation functionality.
- Deprecated Default Realms for Oracle Database Vault
  The Oracle Data Dictionary realm and Oracle Enterprise Manager realm are deprecated in this release.
- Deprecated Default Rule Sets for Oracle Database Vault
  Rule sets listed here are deprecated with Oracle Database 12c Release 1.
- Deprecation of Windows NTS Authentication Using the NTLM Protocol
  Because of security vulnerabilities, NTLM is deprecated as of Oracle Database 12c.
- Deprecation of Public Key Infrastructure for Transparent Data Encryption
  Public Key Infrastructure (PKI) is deprecated for Transparent Data Encryption (TDE) in Oracle Database 12c.
- Oracle Data Guard Broker Deprecated Features
  Review these deprecations if you use Oracle Data Guard Broker.
- Deprecated EndToEndMetrics-related APIs
  EndToEndMetrics -related APIs are deprecated in Oracle Database 12c. Use Universal Connection Pool instead.
- Deprecation of Oracle Restart
  Oracle Restart, also known as Oracle Grid Infrastructure for a Standalone Server, is deprecated in Oracle Database 12c.
- Deprecation of -checkpasswd for QOSCTL Quality of Service (QoS) Command
  The syntax `qosctl -checkpasswd username password` is deprecated.
- Deprecated NT LAN Manager (NTLM) Protocol for Oracle Net Services
  The NT LAN Manager (NTLM) protocol for domain authentication is deprecated in the Oracle Windows adapter.
- Deprecated Features for Oracle Call Interface
  Oracle Call Interface (OCI) features listed here are deprecated in Oracle Database 12c. They can be desupported in a future release
- Deprecation of Oracle Streams
  Oracle Streams is deprecated in Oracle Database 12c. It can be desupported and unavailable in a later Oracle Database release.
- Oracle Data Provider for .NET Deprecated Programming Interfaces
  Oracle Data Provider for .NET application programming interfaces for Transaction Guard are deprecated in Oracle Database 12c (12.1.0.2), and can be desupported in a future release.
- VPD Support in Oracle Database Semantic Technologies is Deprecated
  The Virtual Private Database (VPD) is deprecated for Oracle Database Semantic Technologies in Oracle Database 12c (12.1).
- Version-Enabled Models Support In Oracle Database Semantic Technologies
  The version-enabled models feature is deprecated for Oracle Database Semantic Technologies in Oracle Database 12c (12.1).
- Deprecation of Advanced Replication
  Oracle Database Advanced Replication is deprecated in Oracle Database 12c.
- Deprecation of Single-Character SRVCTL CLI Options
  Starting with Oracle Database 12c, single-character options are deprecated. They can be desupported in a later release.
- Deprecation of Stored List of Administrative Users for Cluster Administration
  Cluster administration is managed differently starting with Oracle Database 12c.
- Deprecation of SQLJ Inside the Server
  SQLJ usage inside the database server is deprecated in this release.
- Deprecated Oracle Update Batching
  Oracle Update Batching APIs are deprecated in Oracle Database 12c.
- Deprecated EndToEndMetrics-related APIs
  EndToEndMetrics -related APIs are deprecated in Oracle Database 12c. Use Universal Connection Pool instead.
- Deprecated Stored Outlines
  Stored outlines are deprecated in Oracle Database 12c.
- Deprecated Concrete Classes in oracle.sql Package
  The concrete classes in the `oracle.sql` package are deprecated in Oracle Database 12c.
- Deprecated defineColumnType Method
  The JDBC method `defineColumnType` is deprecated in Oracle Database 12c Release 1.
- Deprecated CONNECTION_PROPERTY_STREAM_CHUNK_SIZE Property
  The JDBC property CONNECTION_PROPERTY_STREAM_CHUNK_SIZE is deprecated in this release.
- Oracle Data Pump Export Utility Features
  The `XML_CLOBS` option of the Oracle Data Pump Export DATA_OPTIONS parameter is deprecated.
- Version-Enabled Models Support In Oracle Database Semantic Technologies
  The version-enabled models feature is deprecated for Oracle Database Semantic Technologies in Oracle Database 12c (12.1).
- Deprecated defineColumnType Method
  The JDBC method `defineColumnType` is deprecated in Oracle Database 12c Release 1.
- Deprecated NT LAN Manager (NTLM) Protocol for Oracle Net Services
  The NT LAN Manager (NTLM) protocol for domain authentication is deprecated in the Oracle Windows adapter.
- Deprecated Features for Oracle Call Interface
  Oracle Call Interface (OCI) features listed here are deprecated in Oracle Database 12c. They can be desupported in a future release
- Deprecation of Stored List of Administrative Users for Cluster Administration
  Cluster administration is managed differently starting with Oracle Database 12c.
- Deprecation of -cleanupOBase
  The `-cleanupOBase` flag of the deinstallation tool is deprecated in Oracle Database 12c Release 1 (12.1).
- Deprecated Features for Oracle XML Database
  These features are deprecated in Oracle Database 12c Release 1, and can be desupported in a future release.
- Deprecation of Advanced Replication
  Oracle Database Advanced Replication is deprecated in Oracle Database 12c.
- DICOM in Oracle Multimedia Deprecated in Oracle Database 12c Release 1 (12.1)
  In Oracle Database 12c, ORDImage support for Oracle Multimedia DICOM is deprecated.
- Deprecation of JPublisher

**Parent topic:** Oracle Database 12c Release 1 (12.1) Behavior Changes, Desupports, and Deprecations

##### Deprecation of Non-CDB Architecture

The non-CDB architecture is deprecated in Oracle Database 12c. It can be desupported and unavailable in a release after Oracle Database 19c.

Oracle recommends use of the CDB architecture.

**Note:**

There remain a small number of features that do not work with the CDB architecture (see README, section 2.2.1 "Features Restricted or Not Available for a Multitenant Container Database"). If you need these features, then continue to use the non-CDB architecture until your required feature works with the CDB architecture.

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecation of catupgrd.sql Script and Introduction of Parallel Upgrade Utility

In Oracle Database 12c release 1 (12.1), Oracle recommends that you use the Parallel Upgrade Utility (`catctl.pl`instead of `catupgrd.sql` to enable parallel upgrades.

Oracle Database 12c release 1 (12.1) introduces the new Parallel Upgrade Utility, `catctl.pl`. This utility replaces the `catupgrd.sql` script that was used in earlier releases. Although you can still use the `catupgrd.sql` script, it is deprecated starting with Oracle Database 12c. It will be removed in future releases. Oracle recommends that you perform database upgrades by using the new Parallel Upgrade Utility.

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### DELETE_CATALOG_ROLE Deprecated

The `DELETE_CATALOG_ROLE` database role is deprecated in Oracle Database 12c.

**See Also:**

[Oracle Database Reference](../refrn/index.md) for information about this role and dictionary objects

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecated Functions and Parameters in Oracle Label Security

Nine Oracle Label Security features are deprecated in Oracle Database 12c release 1.

The Oracle Label Security features listed here are deprecated in Oracle Database 12c release 1. They can be desupported in a future release. Oracle recommends that you use the alternative features listed here.

- LEAST_UBOUND. Use OLS_GREATEST_LBOUND instead.

- LUBD. Use OLS_GLBD instead.

- DOMINATES. Use OLS_DOMINATES instead.

- DOM. Use OLS_STRICTLY_DOMINATES instead.

- STRICTLY_DOMINATES. Use OLS_STRICTLY_DOMINATES instead.

- S_DOM. Use OLS_STRICTLY_DOMINATES instead.

- DOMINATED_BY. Use OLS_DOMINATED_BY instead.

- DOM_BY. Use OLS_DOMINATED_BY instead.

- STRICTLY_DOMINATED_BY. Use OLS_STRICTLY_DOMINATED_BY instead.

- S_DOM_BY. Use OLS_STRICTLY_DOMINATED_BY instead.

**See Also:**

- [Oracle Label Security Administrator’s Guide](../olsag/working-with-labeled-data.md) for information about finding greatest lower bound with GREATEST_LBOUND

- [Oracle Label Security Administrator’s Guide](../olsag/working-with-labeled-data.md) for information about OLS_GLBD

- [Oracle Label Security Administrator’s Guide](../olsag/working-with-labeled-data.md) for information about the OLS_DOMINATES standalone function

- [Oracle Label Security Administrator’s Guide](../olsag/advanced-topics-in-oracle-label-security.md) for information about OLS_STRICTLY_DOMINATES standalone function

- [Oracle Label Security Administrator’s Guide](../olsag/advanced-topics-in-oracle-label-security.md) for information about OLS_DOMINATED_BY standalone function

- [Oracle Label Security Administrator’s Guide](../olsag/advanced-topics-in-oracle-label-security.md) for information about OLS_STRICTLY_DOMINATED_BY standalone function

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecated API for Oracle Database Vault

The DVSYS.DBMS_MACADM.SYNC_RULES procedure is deprecated, because its functionality is built into the rule creation functionality.

**See Also:**

[Oracle Database Vault Administrator's Guide](../dvadm/configuring-rule-sets.md) for information on rule creation

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecated Default Realms for Oracle Database Vault

The Oracle Data Dictionary realm and Oracle Enterprise Manager realm are deprecated in this release.

The objects formerly protected by the Oracle Data Dictionary realm have been migrated to new realms.

**See Also:**

[Oracle Database Vault Administrator's Guide](../dvadm/configuring-realms.md) for information about new realms and default realms

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecated Default Rule Sets for Oracle Database Vault

Rule sets listed here are deprecated with Oracle Database 12c Release 1.

The following rule sets are deprecated in this release:

- Allow Oracle Data Pump Operation rule set

- Allow Scheduler Job rule set

**Related Topics**

- [Oracle Database Vault Administrator’s Guide](../dvadm/configuring-rule-sets.md)

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecation of Windows NTS Authentication Using the NTLM Protocol

Because of security vulnerabilities, NTLM is deprecated as of Oracle Database 12c.

Windows users can no longer authenticate using the NTS adaptor on Windows clients and servers that require the NT Lan Manager (NTLM) protocol. Windows users can still use Kerberos. NTLM is still used for local user authentication, and in cases in which the database service runs as a local user.

A new client side `sqlnet.ora` boolean parameter NO_NTLM (defaulting to false) allows you to control when NTLM is used in NTS authentication. When you set NO_NTLM to true, this parameter value prevents NTLM from being used in Windows NTS authentication.

**See Also:**

[Oracle Database Platform Guide for Microsoft Windows](../ntqrf/index.md) for information on changes that affect the Windows platform in this release

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecation of Public Key Infrastructure for Transparent Data Encryption

Public Key Infrastructure (PKI) is deprecated for Transparent Data Encryption (TDE) in Oracle Database 12c.

To configure TDE, use the ADMINISTER KEY MANAGEMENT SQL statement. Other implementations of PKI are not affected.

**See Also:**

[Oracle Database Advanced Security Administrator's Guide](../asoag/asopart1.md) for information about configuring TDE

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Oracle Data Guard Broker Deprecated Features

Review these deprecations if you use Oracle Data Guard Broker.

As part of Oracle Data Guard Broker's support for Separation of Duty features, the following broker properties are deprecated in Oracle Database 12c :

- `LsbyASkipCfgPr`

- `LsbyASkipErrorCfgPr`

- `LsbyASkipTxnCfgPr`

- `LsbyDSkipCfgPr`

- `LsbyDSkipErrorCfgPr`

- `LsbyDSkipTxnCfgPr`

- `LsbySkipTable`

- `LsbySkipTxnTable`

There are no replacements.

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecated EndToEndMetrics-related APIs

EndToEndMetrics -related APIs are deprecated in Oracle Database 12c. Use Universal Connection Pool instead.

The following APIs are deprecated and marked deprecated in the JDBC Javadoc:

- getEndToEndMetrics

- getEndToEndECIDSequenceNumber

- setEndToEndMetrics

- setApplicationContext

- clearAllApplicationContext

**See Also:**

[Oracle Database JDBC Developer's Guide](../jjdbc/JDBC-standards-support.md) and the JDBC Javadoc for information about Universal Connection Pool

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecation of Oracle Restart

Oracle Restart, also known as Oracle Grid Infrastructure for a Standalone Server, is deprecated in Oracle Database 12c.

Oracle Restart is restricted to manage single-instance Oracle databases and Oracle ASM instances only, and is subject to desupport in future releases. Oracle continues to provide Oracle ASM as part of the Oracle Grid Infrastructure installation for Standalone and Cluster deployments, and Oracle continues to provide Oracle RAC One Node.

**See Also:**

- My Oracle Support Note 1584742.1 for more information about Oracle Restart deprecation announcement and its replacement:

  <https://support.oracle.com/epmos/faces/DocumentDisplay?id=1584742.1&displayIndex=1>

- [Oracle Database Administrator's Guide](../admin/configuring-automatic-restart-of-an-oracle-database.md)

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecation of -checkpasswd for QOSCTL Quality of Service (QoS) Command

The syntax `qosctl -checkpasswd username password` is deprecated.

**See Also:**

[Oracle Database Quality of Service Management User's Guide](../atnms/creating-administrative-users-qos-management.md) for information about QOSCTL syntax and commands

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecated NT LAN Manager (NTLM) Protocol for Oracle Net Services

The NT LAN Manager (NTLM) protocol for domain authentication is deprecated in the Oracle Windows adapter.

Only Kerberos authentication is used for the NTS adapter.

**See Also:**

[Oracle Database Net Services Reference](../netrf/index.md) for information on Kerberos parameters for the `sqlnet.ora` file

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecated Features for Oracle Call Interface

Oracle Call Interface (OCI) features listed here are deprecated in Oracle Database 12c. They can be desupported in a future release

- OCI deployment parameters in sqlnet.ora are deprecated. These include the following parameters:

  - OCI client result cache parameters: `OCI_RESULT_CACHE_MAX_SIZE`, `OCI_RESULT_CACHE_MAX_RSET_SIZE`, and `OCI_RESULT_CACHE_MAX_RSET_ROWS`

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecation of Oracle Streams

Oracle Streams is deprecated in Oracle Database 12c. It can be desupported and unavailable in a later Oracle Database release.

Use Oracle GoldenGate to replace all replication features of Oracle Streams.

**Note:**

Oracle Database Advanced Queuing is independent of Oracle Streams, and continues to be enhanced.

**See Also:**

[Oracle GoldenGate documentation](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/upgrd&id=ogg) for information

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Oracle Data Provider for .NET Deprecated Programming Interfaces

Oracle Data Provider for .NET application programming interfaces for Transaction Guard are deprecated in Oracle Database 12c (12.1.0.2), and can be desupported in a future release.

The following application programming interfaces are deprecated:

- `OracleLogicalTransactionStatus` class

- `OracleConnection.LogicalTransactionId` property

- `OracleConnection.GetLogicalTransactionStatus` method

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### VPD Support in Oracle Database Semantic Technologies is Deprecated

The Virtual Private Database (VPD) is deprecated for Oracle Database Semantic Technologies in Oracle Database 12c (12.1).

Transition existing Semantic Technologies applications that depend on Virtual Private Database (VPD) to use Oracle Label Security (OLS) instead.

**See Also:**

[Oracle Database Semantic Technologies Developer's Guide](../rdfrm/fine-grained-access-control-rdf.md) for information about fine-grained access control for RDF data

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Version-Enabled Models Support In Oracle Database Semantic Technologies

The version-enabled models feature is deprecated for Oracle Database Semantic Technologies in Oracle Database 12c (12.1).

The specific alternative to using Workspace Manager with semantic data depends on the purpose of the application.

**See Also:**

[Oracle Database Semantic Technologies Developer's Guide](../rdfrm/fine-grained-access-control-rdf.md) for information about Workspace Manager support for RDF data

<https://support.oracle.com/CSP/main/article?cmd=show&type=NOT&id=1468273.1> for more information about use cases and recommended alternatives

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecation of Advanced Replication

Oracle Database Advanced Replication is deprecated in Oracle Database 12c.

Read-only materialized views are still supported with basic replication.

Use Oracle GoldenGate to replace all features of Advanced Replication. This guidance includes multimaster replication, updateable materialized views, and deployment templates.

**See Also:**

[Oracle GoldenGate documentation](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/upgrd&id=ogg)

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecation of Single-Character SRVCTL CLI Options

Starting with Oracle Database 12c, single-character options are deprecated. They can be desupported in a later release.

The Server Control Utility (SRVCTL) command line interface (CLI) supports long GNU-style options in addition to short CLI options used in earlier releases.

**See Also:**

[Oracle Real Application Clusters Administration and Deployment Guide](../racad/server-control-utility-reference.md) for information about SRVCTL

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecation of Stored List of Administrative Users for Cluster Administration

Cluster administration is managed differently starting with Oracle Database 12c.

Starting with Oracle Database 12c, the method of cluster administration using a stored list of administrative users is being replaced with more comprehensive management of administrative user roles by configuring the access control list of the policy set.

**See Also:**

[Oracle Clusterware Administration and Deployment Guide](../cwadd/oracle-clusterware-administration.md) for more information about cluster administration

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecation of SQLJ Inside the Server

SQLJ usage inside the database server is deprecated in this release.

The capability of translating and running SQLJ applications inside the database will not be available in later releases. SQLJ can only be used as a client tool to translate the applications that can connect to Oracle Database and run as a client. SQLJ cannot be used inside stored procedures, functions, or triggers.

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecated Oracle Update Batching

Oracle Update Batching APIs are deprecated in Oracle Database 12c.

The following APIs are deprecated and marked deprecated in the JDBC Javadoc:

- `OraclePreparedStatement.setExecuteBatch()`

- `OraclePreparedStatement.getExecuteBatch()`

- `OracleCallableStatement.setExecuteBatch()`

Use Standard Update Batching instead.

**Related Topics**

- [Oracle Database JDBC Developer’s Guide](../jjdbc/performance-extensions.md)

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecated EndToEndMetrics-related APIs

EndToEndMetrics -related APIs are deprecated in Oracle Database 12c. Use Universal Connection Pool instead.

The following APIs are deprecated and marked deprecated in the JDBC Javadoc:

- getEndToEndMetrics

- getEndToEndECIDSequenceNumber

- setEndToEndMetrics

- setApplicationContext

- clearAllApplicationContext

**See Also:**

[Oracle Database JDBC Developer's Guide](../jjdbc/JDBC-standards-support.md) and the JDBC Javadoc for information about Universal Connection Pool

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecated Stored Outlines

Stored outlines are deprecated in Oracle Database 12c.

Use plan baselines instead.

**See Also:**

[Oracle Database SQL Tuning Guide](../jsqlj/advanced-language-features.md) for information about migrating stored outlines to plan baselines

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecated Concrete Classes in oracle.sql Package

The concrete classes in the `oracle.sql` package are deprecated in Oracle Database 12c.

These classes are replaced with new interfaces in the `oracle.jdbc` package.

**See Also:**

[Oracle Database JDBC Developer's Guide](../jjdbc/Oracle-extensions.md) for information about the new interfaces for `oracle.jdbc`

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecated defineColumnType Method

The JDBC method `defineColumnType` is deprecated in Oracle Database 12c Release 1.

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecated CONNECTION_PROPERTY_STREAM_CHUNK_SIZE Property

The JDBC property CONNECTION_PROPERTY_STREAM_CHUNK_SIZE is deprecated in this release.

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Oracle Data Pump Export Utility Features

The `XML_CLOBS` option of the Oracle Data Pump Export DATA_OPTIONS parameter is deprecated.

**See Also:**

[Oracle Database Utilities](../sutil/oracle-data-pump-export-utility.md) for information about the Export DATA_OPTIONS parameter

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Version-Enabled Models Support In Oracle Database Semantic Technologies

The version-enabled models feature is deprecated for Oracle Database Semantic Technologies in Oracle Database 12c (12.1).

The specific alternative to using Workspace Manager with semantic data depends on the purpose of the application.

**See Also:**

[Oracle Database Semantic Technologies Developer's Guide](../rdfrm/fine-grained-access-control-rdf.md) for information about Workspace Manager support for RDF data

<https://support.oracle.com/CSP/main/article?cmd=show&type=NOT&id=1468273.1> for more information about use cases and recommended alternatives

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecated defineColumnType Method

The JDBC method `defineColumnType` is deprecated in Oracle Database 12c Release 1.

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecated NT LAN Manager (NTLM) Protocol for Oracle Net Services

The NT LAN Manager (NTLM) protocol for domain authentication is deprecated in the Oracle Windows adapter.

Only Kerberos authentication is used for the NTS adapter.

**See Also:**

[Oracle Database Net Services Reference](../netrf/index.md) for information on Kerberos parameters for the `sqlnet.ora` file

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecated Features for Oracle Call Interface

Oracle Call Interface (OCI) features listed here are deprecated in Oracle Database 12c. They can be desupported in a future release

- OCI deployment parameters in sqlnet.ora are deprecated. These include the following parameters:

  - OCI client result cache parameters: `OCI_RESULT_CACHE_MAX_SIZE`, `OCI_RESULT_CACHE_MAX_RSET_SIZE`, and `OCI_RESULT_CACHE_MAX_RSET_ROWS`

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecation of Stored List of Administrative Users for Cluster Administration

Cluster administration is managed differently starting with Oracle Database 12c.

Starting with Oracle Database 12c, the method of cluster administration using a stored list of administrative users is being replaced with more comprehensive management of administrative user roles by configuring the access control list of the policy set.

**See Also:**

[Oracle Clusterware Administration and Deployment Guide](../cwadd/oracle-clusterware-administration.md) for more information about cluster administration

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecation of -cleanupOBase

The `-cleanupOBase` flag of the deinstallation tool is deprecated in Oracle Database 12c Release 1 (12.1).

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecated Features for Oracle XML Database

These features are deprecated in Oracle Database 12c Release 1, and can be desupported in a future release.

- `CLOB` storage of `XMLType`, also known as unstructured storage, is deprecated. Use binary XML storage of `XMLType` instead.

  To preserve whitespace in an XML file, store two copies of your original XML document. Use one file as an `XMLType` instance for database use and XML processing, and use the other file as a `CLOB` instance to provide document fidelity.

- Creating an `XMLIndex` index over an XML fragment stored as a `CLOB` instance embedded in object-relational `XMLType` data is deprecated. If you must index the data in such a fragment, then store the document using binary XML storage, instead of object-relational storage.

- The following PL/SQL subprograms in package `DBMS_XMLSCHEMA` are deprecated:

  - `generateSchema`

  - `generateSchemas`

  There are no replacements for these constructs, and there is no workaround for this change.

- PL/SQL package `DBMS_XDB_CONFIG` is new. All Oracle XML((nbsp))DB configuration functions, procedures, and constants are moved from package `DBMS_XDB` to `DBMS_XDB_CONFIG`. These functions, procedures and constants are now deprecated for package `DBMS_XDB`. Use them in package `DBMS_XDB_CONFIG` instead.

  The following is a list of subprograms deprecated in package `DBMS_XDB`:

  - `ADDHTTPEXPIREMAPPING`

  - `ADDMIMEMAPPING`

  - `ADDSCHEMALOCMAPPING`

  - `ADDSERVLET`

  - `ADDSERVLETMAPPING`

  - `ADDSERVLETSECROLE`

  - `ADDXMLEXTENSION`

  - `CFG_GET`

  - `CFG_REFRESH`

  - `CFG_UPDATE`

  - `DELETEHTTPEXPIREMAPPING`

  - `DELETEMIMEMAPPING`

  - `DELETESCHEMALOCMAPPING`

  - `DELETESERVLET`

  - `DELETESERVLETMAPPING`

  - `DELETESERVLETSECROLE`

  - `DELETEXMLEXTENSION`

  - `GETFTPPORT`

  - `GETHTTPPORT`

  - `GETLISTENERENDPOINT`

  - `SETFTPPORT`

  - `SETHTTPPORT`

  - `SETLISTENERENDPOINT`

  - `SETLISTENERLOCALACCESS`

  The following is a list of constants that are deprecated in package `DBMS_XDB`:

  - `XDB_ENDPOINT_HTTP`

  - `XDB_ENDPOINT_HTTP2`

  - `XDB_PROTOCOL_TCP`

  - `XDB_PROTOCOL_TCPS`

- All Oracle SQL functions for updating XML data are deprecated. Use XQuery Update instead for these functions . The following is a list of deprecated XML updating functions:

  - `updateXML`

  - `insertChildXML`

  - `insertChildXMLbefore`

  - `insertChildXMLafter`

  - `insertXMLbefore`

  - `insertXMLafter`

  - `appendChildXML`

  - `deleteXML`

- Oracle SQL function `sys_xmlgen` is deprecated. Use the SQL/XML generation functions instead.

- The following Oracle XQuery functions are deprecated. Use the corresponding standard XQuery functions instead, that is, the functions with the same names but with namespace prefix `fn`.

  - `ora:matches` – use `fn:matches` instead

  - `ora:replace` – use `fn:replace` instead

- The following Oracle constructs that provide support for XML translations are deprecated.

  - PL/SQL package `DBMS_XMLTRANSLATIONS`

  - Oracle XPath function `ora:translate`

  - XML Schema annotations `xdb:maxOccurs`, `xdb:srclang`, and `xdb:translate`

  There are no replacements for these constructs, and there is no workaround for this change.

- The following XML Schema annotations are deprecated:

  - `xdb:defaultTableSchema`

  - `xdb:maintainOrder`

  - `xdb:mapUnboundedStringToLob`

  - `xdb:maxOccurs`

  - `xdb:SQLCollSchema`

  - `xdb:SQLSchema`

  - `xdb:srclang`

  - `xdb:storeVarrayAsTable`

  - `xdb:translate`

  There are no replacements for these constructs, and there is no workaround for this change.

- The value `xml_clobs` for export parameter data_options is deprecated starting with Oracle Database 12c.

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecation of Advanced Replication

Oracle Database Advanced Replication is deprecated in Oracle Database 12c.

Read-only materialized views are still supported with basic replication.

Use Oracle GoldenGate to replace all features of Advanced Replication. This guidance includes multimaster replication, updateable materialized views, and deployment templates.

**See Also:**

[Oracle GoldenGate documentation](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/upgrd&id=ogg)

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### DICOM in Oracle Multimedia Deprecated in Oracle Database 12c Release 1 (12.1)

In Oracle Database 12c, ORDImage support for Oracle Multimedia DICOM is deprecated.

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

##### Deprecation of JPublisher

Oracle JPublisher is deprecated in Oracle Database 12c Release 1, as of October 2014, and all JPublisher features are desupported and unavailable in Oracle Database 12c Release 2. Oracle recommends that you use the alternatives listed here:

- To continue to use Web service callouts, Oracle recommends that you use the OJVM Web Services Callout utility, which is a replacement for the Web Services Callout utility.

- To create Java client applications for PL/SQL programs and SQL objects, Oracle recommends that developers use other JDK development tools that assist you to create java `STRUCT` classes, and other prestructured options.

**See Also:**

My Oracle Support Note 1937939.1 for more information about JPublisher deprecation and desupport:

https://support.oracle.com/CSP/main/article?cmd=show&type=NOT&id=1937939.1

Also, see JDK Tools and Utilities on Oracle Technology Network:

http://docs.oracle.com/javase/8/docs/technotes/tools/

**Parent topic:** Deprecated Features in Oracle Database 12c Release 2 (12.2)

#### Deprecated Initialization Parameters in Oracle Database 12c Release 1 (12.1)

As part of your upgrade plan, review the initialization parameters that are deprecated in Oracle Database 12c Release 1 (12.1).

- FILE_MAPPING Initialization Parameter Deprecated
  The FILE_MAPPING initialization parameter is deprecated. It is still supported for backward compatibility.
- RDBMS_SERVER_DN Initialization Parameter Deprecated
  The initialization parameter RDBMS_SERVER_DN is deprecated in Oracle Database release 12.1.0.2.
- Deprecation of IGNORECASE and SEC_CASE_SENSITIVE_LOGON
  The `IGNORECASE` argument of `ORAPWD` and the `SEC_CASE_SENSITIVE_LOGON` system parameter are deprecated in Oracle Database 12c.
- Deprecation of SQLNET.ALLOWED_LOGON_VERSION Parameter
  The SQLNET.ALLOWED_LOGON_VERSION parameter is deprecated in Oracle Database 12c.
- LOG_ARCHIVE_LOCAL_FIRST Initialization Parameter Desupported
  The LOG_ARCHIVE_LOCAL_FIRST initialization parameter is removed and desupported in Oracle Database 12c.

**Parent topic:** Oracle Database 12c Release 1 (12.1) Behavior Changes, Desupports, and Deprecations

##### FILE_MAPPING Initialization Parameter Deprecated

The FILE_MAPPING initialization parameter is deprecated. It is still supported for backward compatibility.

**See Also:**

[Oracle Database Reference](../refrn/FILE_MAPPING.md) for information about the FILE_MAPPING initialization parameter

**Parent topic:** Deprecated Initialization Parameters in Oracle Database 12c Release 1 (12.1)

##### RDBMS_SERVER_DN Initialization Parameter Deprecated

The initialization parameter RDBMS_SERVER_DN is deprecated in Oracle Database release 12.1.0.2.

Use LDAP_DIRECTORY_ACCESS instead of RDBMS_SERVER_DN.

**See Also:**

[Oracle Database Reference](../refrn/RDBMS_SERVER_DN.md) for information about this parameter

**Parent topic:** Deprecated Initialization Parameters in Oracle Database 12c Release 1 (12.1)

##### Deprecation of IGNORECASE and SEC_CASE_SENSITIVE_LOGON

The `IGNORECASE` argument of `ORAPWD` and the `SEC_CASE_SENSITIVE_LOGON` system parameter are deprecated in Oracle Database 12c.

By default, passwords in Oracle Database 12c are case-sensitive.

**See Also:**

[Oracle Database Security Guide](../dbseg/configuring-authentication.md) for more information about configuring authentication and password protection

**Parent topic:** Deprecated Initialization Parameters in Oracle Database 12c Release 1 (12.1)

##### Deprecation of SQLNET.ALLOWED_LOGON_VERSION Parameter

The SQLNET.ALLOWED_LOGON_VERSION parameter is deprecated in Oracle Database 12c.

SQLNET.ALLOWED_LOGON_VERSION is replaced with two new Oracle Net Services parameters:

- SQLNET.ALLOWED_LOGON_VERSION_SERVER

- SQLNET.ALLOWED_LOGON_VERSION_CLIENT

**Related Topics**

- Upgrading a System that Did Not Have SQLNET.ALLOWED_LOGON_VERSION Parameter Setting
- [Check for the SQLNET.ALLOWED_LOGON_VERSION Parameter Behavior](required-tasks-complete-upgrading-oracle-database.md)

**See Also:**

[Oracle Database Net Services Reference](../netrf/parameters-for-the-sqlnet.ora.md) for information about SQLNET.ALLOWED_LOGON_VERSION_SERVER

[Oracle Database Net Services Reference](../netrf/parameters-for-the-sqlnet.ora.md) for information about SQLNET.ALLOWED_LOGON_VERSION_CLIENT

[Oracle Database Security Guide](../dbseg/index.md) for information about this deprecation

**Parent topic:** Deprecated Initialization Parameters in Oracle Database 12c Release 1 (12.1)

##### LOG_ARCHIVE_LOCAL_FIRST Initialization Parameter Desupported

The LOG_ARCHIVE_LOCAL_FIRST initialization parameter is removed and desupported in Oracle Database 12c.

LOG_ARCHIVE_LOCAL_FIRST specified when the archiver processes (`ARC``n`) transmit redo data to remote standby database destinations. It was deprecated in Oracle Database 11g.

Oracle recommends that you use `LOG_ARCHIVE_DEST_`n. Set the attributes for the LOG_ARCHIVE_DEST\_n initialization parameter to control different aspects of how redo transport services transfer redo data from a production or primary database destination to another (standby) database destination.

**Parent topic:** Deprecated Initialization Parameters in Oracle Database 12c Release 1 (12.1)

#### Deprecated Views in Oracle Database 12c Release 1 (12.1)

Review the deprecated features listed in this section to prepare to use alternatives after you upgrade. Features deprecated in an earlier release can be desupported in a later release.

The following views are deprecated:

- `ALL_SCHEDULER_CREDENTIALS` view. See [Oracle Database Reference](../refrn/ALL_SCHEDULER_CREDENTIALS.md) for more information.

- `DBA_NETWORK_ACL_PRIVILEGES` view. See [Oracle Database Reference](../refrn/DBA_NETWORK_ACL_PRIVILEGES.md) for more information.

- `DBA_NETWORK_ACLS` view. See [Oracle Database Reference](../refrn/DBA_NETWORK_ACLS.md) for more information.

- `DBA_SCHEDULER_CREDENTIALS` view. See [Oracle Database Reference](../refrn/DBA_SCHEDULER_CREDENTIALS.md) for more information.

- `USER_NETWORK_ACL_PRIVILEGES` view. See [Oracle Database Reference](../refrn/USER_NETWORK_ACL_PRIVILEGES.md) for more information.

- `USER_SCHEDULER_CREDENTIALS` view. See [Oracle Database Reference](../refrn/DBA_NETWORK_ACL_PRIVILEGES.md) for more information.

- `V$OBJECT_USAGE` view. Use the `USER_OBJECT_USAGE` view instead. See [Oracle Database Reference](../refrn/USER_OBJECT_USAGE.md) for more information.

**See Also:**

[Oracle Database Administrator's Guide](../admin/scheduling-jobs-with-oracle-scheduler.md) for information about specifying Scheduler job credentials

**Parent topic:** Oracle Database 12c Release 1 (12.1) Behavior Changes, Desupports, and Deprecations
