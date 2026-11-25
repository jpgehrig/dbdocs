## Configuring Oracle Database Vault Using DBCA

You can configure Oracle Database Vault after installation using Oracle Database Configuration Assistant (DBCA), or choose not to configure Oracle Database Vault.

To install Oracle Database Vault using DBCA:

1.  After installing Oracle RAC, create the database.
2.  Start DBCA and select the option Configure Database.
3.  In the component list, select Oracle Label Security and Oracle Database Vault.
4.  Provide the required Oracle Database Vault user IDs and passwords to proceed with configuration. To enable a separate Oracle Database Vault administrator, choose to configure the `DV_ACCTMGR` user.
5.  After you have finished, restart each database instance to finish the software configuration.

**See Also:**

[Oracle Database Vault Administrator's Guide](../dvadm/index.md) for information about using Oracle Data Guard with Oracle Database Vault

**Parent topic:** [Installing the Oracle Database Vault Option](installing-the-oracle-database-vault-option.md)
