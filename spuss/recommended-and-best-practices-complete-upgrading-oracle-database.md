Oracle recommends that you complete these good practices guidelines for updating Oracle Database. Except where noted, these practices are recommended for all types of upgrades.

- [Back Up the Database](back-up-the-db.md)
  Oracle strongly recommends that you at least perform a level 1 backup, or if time allows, perform a level 0 backup.
- [Upgrading Statistics Tables Created by the DBMS_STATS Package After Upgrading Oracle Database](upgrading-statistics-tables-created-by-dbms-stats-package.md)
  If you created statistics tables using the `DBMS_STATS.CREATE_STAT_TABLE` procedure, then upgrade these tables by running `DBMS_STATS.UPGRADE_STAT_TABLE`.
- [Regathering Fixed Objects Statistics with DBMS_STATS](regathering-fixed-objects-statistics.md)
  After an upgrade, or after other database configuration changes, Oracle strongly recommends that you regather fixed object statistics after you have run representative workloads on Oracle Database.
- Dropping and Recreating DBMS_SCHEDULER Jobs
  If DBMS_SCHEDULER jobs do not function after upgrading from an earlier release, drop and recreate the jobs.
- Transfer Unified Audit Records After the Upgrade
  Review these topics to understand how you can obtain better performance after you upgrade and migrate to unified auditing
- Enabling Disabled Release Update Bug Fixes in the Upgraded Database
  Because bug fixes in Release Updates that can cause execution plan changes are disabled, Oracle recommends that you enable the disabled bug fixes that you want to use.
- [Reset Passwords to Enforce Case-Sensitivity](reset-passwords-to-enforce-case-sensitivity.md)
  For upgraded databases, improve security by using case-sensitive passwords for default user accounts and user accounts.
- [Configuring the FTP and HTTP Ports and HTTP Authentication for Oracle XML DB](configuring-ftp-and-http-ports-andhttp-authentication.md)
  Oracle Database Configuration Assistant (DBCA) does not configure ports for Oracle XML DB on Oracle Database 12c and later releases. Upgrades use digest authentication.
- [Add New Features as Appropriate](add-new-features-as-appropriate.md)
  Review new features as part of your database upgrade plan.
- [Develop New Administrative Procedures as Needed](develop-new-administrative-procedures-as-needed.md)
  Plan a review of your scripts and procedures, and change as needed.
- Migrate Your Upgraded Oracle Databases to Use Unified Auditing
  Traditional auditing is deprecated. To use the full facilities of unified auditing, you must manually migrate to unified auditing.
- [Migrating From Rollback Segments To Automatic Undo Mode](migrating-from-rollback-segments-to-automatic-undo-mode.md)
  If your database release is earlier than Oracle Database 11g, then you must migrate the database that is being upgraded from using rollback segments (manual undo management) to automatic undo management.
- [Migrating Tables from the LONG Data Type to the LOB Data Type](migrating-tables-from-long-data-type-to-lob-data-type.md)
  You can use the `ALTER TABLE` statement to change the data type of a `LONG` column to `CLOB` and that of a `LONG RAW` column to `BLOB`.
- [Identify Oracle Text Indexes for Rebuilds](identify-oracle-text-indexes-for-rebuilds.md)
  You can run a script that helps you to identify Oracle Text index indexes with token tables that can benefit by being rebuilt after upgrading to the new Oracle Database release..
- [About Testing the Upgraded Production Oracle Database](about-testing-the-upgraded-production-oracle-db.md)
  Repeat tests on your production database that you carried out on your test database to ensure applications operate as expected.
- [Upgrading the Time Zone File Version After Upgrading Oracle Database](upgrading-time-zone-file-version-after-upgrading-oracle-db.md)
  If the AutoUpgrade preupgrade report instructs you to upgrade the time zone files after completing the database upgrade, and you do not set AutoUpgrade to complete this task for you, then use the `DBMS_DST` PL/SQL package to upgrade the time zone file.

**Parent topic:** [Post-Upgrade Tasks for Oracle Database](post-upgrde-tasks.md)

### Dropping and Recreating DBMS_SCHEDULER Jobs

If DBMS_SCHEDULER jobs do not function after upgrading from an earlier release, drop and recreate the jobs.

If you find that DBMS_SCHEDULER jobs are not functioning after an upgrade. drop and recreate those jobs. This issue can occur even if the upgrade process does not report issues, and system objects are valid.

**Parent topic:** Recommended and Best Practices to Complete After Upgrading Oracle Database

### Transfer Unified Audit Records After the Upgrade

Review these topics to understand how you can obtain better performance after you upgrade and migrate to unified auditing

**Parent topic:** Recommended and Best Practices to Complete After Upgrading Oracle Database

### Enabling Disabled Release Update Bug Fixes in the Upgraded Database

Because bug fixes in Release Updates that can cause execution plan changes are disabled, Oracle recommends that you enable the disabled bug fixes that you want to use.

After you upgrade your database, the bug fix patches that can cause execution plan changes included in the Release Updates are installed disabled by default. These bug fixes will not be activated until you enable the fixes. You can either enable these fixes manually, with `PFILE` or `ALTER SYSTEM` commands, or you can use the `DBMS_OPTIM_BUNDLE` package. Starting with AutoUpgrade 19.12, the `DBMS_OPTIM_BUNDLE` package includes 58 standard fixes. You can now add additional fixes using `DBMS_OPTIM_BUNDLE`. If you add fixes, then the fixes that you add are run in addition to the default fixes.

Oracle strongly recommends that you enable these disabled patches that you want to use in your production system, and run complete workload performance tests using these patches as part of your upgrade test plan.

For more information about using `DBMS_OPTIM_BUNDLE` to enable patches that were disabled because they can change execution plans, see Oracle Database PL/SQL Packages and Types Reference, and My Oracle Support note 2147007.1.

**Related Topics**

- [DBMS_OPTIM_BUNDLE](../arpls/dbms_optim_bundle.md)
- [My Oracle Support Doc ID 2147007.1 Managing "installed but disabled" bug fixes in Database Release Updates using DBMS_OPTIM_BUNDLE](https://support.oracle.com/rs?type=doc&id=2147007.1)

**Parent topic:** Recommended and Best Practices to Complete After Upgrading Oracle Database

### Migrate Your Upgraded Oracle Databases to Use Unified Auditing

Traditional auditing is deprecated. To use the full facilities of unified auditing, you must manually migrate to unified auditing.

Unified Auditing and Traditional Auditing (mixed mode) has been the default auditing mode from Oracle Database 12c onward. Mixed mode auditing was offered to enable you to become familiar with Unified Auditing, and to transition from Traditional Auditing. With the deprecation of Traditional Auditing in Oracle Database 21c, Oracle recommends that you migrate to Unified Auditing. Refer to the migration procedure in Oracle Database Security Guide.

**Related Topics**

- [How the Unified Auditing Migration Affects Individual Audit Features](../dbseg/how-unified-auditing-migration-affects-individual-audit-features.md)

**Parent topic:** Recommended and Best Practices to Complete After Upgrading Oracle Database
