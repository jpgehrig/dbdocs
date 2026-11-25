Ensure that you have completed these database preparation tasks before starting an Oracle Database upgrade.

- [Release Updates and Requirements for Upgrading Oracle Database](patch-set-updates-and-requirements.md)
  Before starting upgrades, update your new release Oracle home to the latest Release Update (Update).
- [Copying Transparent Encryption Oracle Wallets](copying-transparent-encryption-oracle-wallets.md)
  If your database uses Transparent Data Encryption (TDE) and a software keystore, and you rely on the `sqlnet.ora` parameter `ENCRYPTION_WALLET_LOCATION` to locate the TDE software keystore, then ensure that the new release `sqlnet.ora` has a proper configuration.
- [Recommendations for Oracle Net Services When Upgrading Oracle Database](recommendations-for-oracle-net-services.md)
  You must ensure that the listener is running in your new release Oracle home.
- [Understanding Password Case Sensitivity and Upgrades](understanding-password-case-sensitivity-and-upgrades.md)
  By default, Oracle Database 12c Release 2 (12.2) and later releases use Exclusive Mode authentication protocols. Exclusive Modes do not support case-insensitive password-based authentication.
- [Checking for Accounts Using Case-Insensitive Password Version](checking-for-accounts-using-case-insensitive-password.md)
  Use these procedures to identify if the Oracle Database that you want to upgrade has accounts or configuration parameters that are using a case-insensitive password version.

**Parent topic:** [Preparing to Upgrade Oracle Database](preparing-to-upgrade.md)
