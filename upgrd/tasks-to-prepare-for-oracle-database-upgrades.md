## Tasks to Prepare for Oracle Database Upgrades

Carry out these tasks to prepare your upgrade.

Before you upgrade your database, Oracle recommends that you review the new features and determine the best upgrade path and method to use, and carry out procedures to prepare your database for upgrade. Oracle strongly recommends that you test the upgrade process and prepare a backup strategy.

- [Become Familiar with New Oracle Database Features](become-familiar-with-new-database-features.md)
  Before you plan the upgrade process, become familiar with the features of the new Oracle Database release.
- [Pre-Upgrade Information Check with AutoUpgrade](pre-upgrade-check-autoupgrade.md)
  To obtain a checklist of tasks you must complete before upgrading an Oracle Database, run the AutoUpgrade utility (`autoupgrade.jar`) in `analyze` mode.
- [Review Deprecated and Desupported Features](review-deprecated-desupported-features.md)
  Before you upgrade, check to see if deprecated or desupported features require attention in your upgrade plan.
- [Choose an Upgrade Method for Oracle Database](choose-an-upgrade-method-for-oracle-database.md)
  Oracle offers several methods to upgrade your database, which support the complexities of your enterprise.
- [Choose a New Location for Oracle Home when Upgrading](choose-a-new-location-for-oracle-home-when-upgrading.md)
  When you upgrade or patch the database, you must install the new Oracle home in a new location (an out-of-place upgrade or patch).
- [Develop a Test Plan for Upgrading Oracle Database](develop-a-test-plan-for-upgrading-database.md)
  Review these topics to understand how to create a series of carefully designed tests to validate all stages of the upgrade process.
- [Schema-Only Accounts and Upgrading EXPIRED Password Accounts](schema-only-accounts-upgraded-expired-password-accounts.md)
  Before starting your upgrade, determine if you want to use password authentication to default Oracle Database accounts where their passwords are in `EXPIRED` status, and their account is in `LOCKED` status
- [Back Up Files to Preserve Downgrade and Recovery Options](back-up-files-to-preserve-downgrade.md)
  To ensure that you can recover from upgrade issues, and downgrade to an earlier release if necessary, Oracle recommends that you implement a backup strategy for your database, and for some specific files.

**Parent topic:** [Preparing to Upgrade Oracle Database](tasks-prepare-upgrade-oracle-database.md)
