If your target Oracle Database release is 12.2 or later, then you can upgrade without disabling Oracle Database Vault.

If you have Oracle Database Vault enabled in your source Oracle Database release, then you can upgrade Oracle Database to Oracle Database 18c and later releases without first disabling Oracle Database Vault. After the upgrade, if your source Oracle Database release is Oracle Database 12c release 1 (12.1) or later, then Oracle Database Vault is enabled with the same enforcement settings that you had in place before the upgrade. For example, if your source database is Oracle Database release 12.1, and Oracle Database Vault was disabled in that release, then it remains disabled after you upgrade. If your source Oracle Database release 12.1 database had Oracle Database Vault enabled before the upgrade, then Oracle Database Vault is enabled after the upgrade.

If you manually disable Oracle Database Vault before the upgrade, then you must enable Oracle Database Vault manually after the upgrade.

If you did not have Oracle Database Vault enabled before the upgrade, then you can enable it manually after the upgrade.

Enable Oracle Database Vault in the upgraded database by using the procedure `dvsys.dbms_macadm.enable_dv()`. Run this procedure with a user account that is granted `DV_OWNER`. After you run the procedure, restart the database instance so that the procedure takes effect.

**Related Topics**

- [Oracle Database Vault Administrator’s Guide](../dvadm/disabling-and-enabling-oracle-database-vault.md)

**Parent topic:** [Enabling Oracle Database Vault After Upgrading Oracle Database](enabling-oracle-db-vault-after-upgrading-oracle-db.md)
