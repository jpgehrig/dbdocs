Oracle recommends that you complete these good practices guidelines for updating Oracle Database. These practices are recommended for both manual and DBUA upgrades.

- [Back Up the Database](back-up-the-db.md)
  Perform a full backup of the production database.
- [Scenario Non-CDB Running the postupgrade_fixups.sql Script](scenario-non-cdb-running-the-postupgrade-fixups-script.md)
  Review this procedure to understand how to use the `postupgrade_fixups.sql` scripts for Non-CDB databases.
- [Gathering Dictionary Statistics After Upgrading](gathering-dictionary-statistics-after-upgrading.md)
  To help to assure good performance, use this procedure to gather dictionary statistics after completing your upgrade.
- [Regathering Fixed Objects Statistics with DBMS_STATS](regathering-fixed-objects-statistics.md)
  After an upgrade, or after other database configuration changes, Oracle strongly recommends that you regather fixed object statistics after you have run representative workloads on Oracle Database.
- [Reset Passwords to Enforce Case-Sensitivity](reset-passwords-to-enforce-case-sensitivity.md)
  For upgraded databases, improve security by using case-sensitive passwords for default user accounts and user accounts.
- [Add New Features as Appropriate](add-new-features-as-appropriate.md)
  Review new features as part of your database upgrade plan.
- [Develop New Administrative Procedures as Needed](develop-new-administrative-procedures-as-needed.md)
  Plan a review of your scripts and procedures, and change as needed.
- [Set Threshold Values for Tablespace Alerts](set-threshold-values-for-tablespace-alerts.md)
  After an upgrade, thresholds for the upgraded Oracle Database Tablespace Alerts are set to null, disabling the alerts.
- [Migrating From Rollback Segments To Automatic Undo Mode](migrating-from-rollback-segments-to-automatic-undo-mode.md)
  If your database release is earlier than Oracle Database 11g, then you must migrate the database that is being upgraded from using rollback segments (manual undo management) to automatic undo management.
- [Configure Oracle Data Guard Broker](configure-oracle-data-guard-broker.md)
  InitialConnectIdentifier is replaced by DGConnectIdentifier, which affects upgrades from Oracle Database 10g.
- [Migrating Tables from the LONG Data Type to the LOB Data Type](migrating-tables-from-long-data-type-to-lob-data-type.md)
  You can use the `ALTER TABLE` statement to change the data type of a `LONG` column to `CLOB` and that of a `LONG RAW` column to `BLOB`.
- [Identify Oracle Text Indexes for Rebuilds](identify-oracle-text-indexes-for-rebuilds.md)
  You can run a script that helps you to identify Oracle Text index indexes with token tables that can benefit by being rebuilt after upgrading to the new Oracle Database release..
- [About Testing the Upgraded Production Oracle Database](about-testing-the-upgraded-production-oracle-db.md)
  Repeat tests on your production database that you carried out on your test database to ensure applications operate as expected.

**Parent topic:** [Post-Upgrade Tasks for Oracle Database](post-upgrde-tasks.md)
