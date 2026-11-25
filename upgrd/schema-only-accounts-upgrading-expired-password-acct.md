## Schema-Only Accounts and Upgrading EXPIRED Password Accounts

Before starting your upgrade, determine if you want to use password authentication to default Oracle Database accounts where their passwords are in `EXPIRED` status, and their account is in `LOCKED` status

During upgrades to Oracle Database 19c and later releases, default Oracle accounts that have not had their passwords reset before upgrade (and are set to `EXPIRED` status), and that are also set to `LOCKED` status, are set to `NO AUTHENTICATION` after the upgrade is complete.

Because of this new feature, default accounts that are changed to schema-only accounts become unavailable for password authentication. The benefit of this feature is that administrators no longer have to periodically rotate the passwords for these Oracle Database-provided schemas. This feature also reduces the security risk of attackers using default passwords to hack into these accounts.

If you want to prevent these Oracle accounts from being set to schema-only accounts during the upgrade, then you must either set a valid strong password for the account before you start the upgrade, or set a valid strong password for these accounts after upgrade, or unlock the accounts before you log in to the upgraded Oracle Database.

After the upgrade, an administrator can also enable password authentication for schema-only accounts. However, for better security, Oracle recommends that you keep these accounts as schema only accounts.

**Related Topics**

- [Oracle Database Security Guide](../dbseg/managing-security-for-oracle-database-users.md)

**Parent topic:** [Upgrading Applications After Upgrading Oracle Database](upgrading-apps-after-oracle-db-upgrade.md)
