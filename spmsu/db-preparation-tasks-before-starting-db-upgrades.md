Ensure that you have completed these database preparation tasks before starting an Oracle Database upgrade.

- [Patch Set Updates and Requirements for Upgrading Oracle Database](patch-set-updates-and-requirements.md)
  Before starting upgrades, update your new release Oracle Database to the latest Oracle bundle patch, patch set update (BP or PSU), or Release Update (Update), or Release Update Revision (Revision).
- [Copying Transparent Encryption Oracle Wallets](copying-transparent-encryption-oracle-wallets.md)
  If you use Oracle wallet with Transparent Data Encryption (TDE), then copy the `sqlnet.ora` and wallet file to the new Oracle home.
- [Recommendations for Oracle Net Services When Upgrading Oracle Database](recommendations-for-oracle-net-services.md)
  Review these procedures and parameter changes for Oracle Net Services before you upgrade.
- [Understanding Password Case Sensitivity and Upgrades](understanding-password-case-sensitivity-and-upgrades.md)
  By default, Oracle Database 12c Release 2 (12.2) and later releases are upgraded to an Exclusive Mode. Exclusive Modes do not support case-insensitive password-based authentication.
- [Checking for Accounts Using Case-Insensitive Password Version](checking-for-accounts-using-case-insensitive-password.md)
  Use these procedures to identify if the Oracle Database that you want to upgrade has accounts or configuration parameters that are using a case-insensitive password version.
- [Running Upgrades with Read-Only Tablespaces](running-upgrades-with-read-only-tablespaces.md)
  Use the Parallel Upgrade Utility with the `-T` option to take schema-based tablespaces offline during upgrade.

**Parent topic:** [Preparing to Upgrade Oracle Database](preparing-to-upgrade.md)
