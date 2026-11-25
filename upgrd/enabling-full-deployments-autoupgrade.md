## Enabling Full Deployments for AutoUpgrade

To enable a guaranteed restore point (GRP) so that you can flashback an upgrade, you must set up archive logging, and you should complete other tasks to enable AutoUpgrade to complete the upgrade.

For AutoUpgrade to be able to perform a full deployment of the new release Oracle Database, the following must be true:

- The database must have a proper configuration of the fast recovery area (FRA). Specifically, `DB_RECOVERY_FILE_DEST` and `DB_RECOVERY_FILE_DEST_SIZE` must be set, and be properly sized.
- Your source Oracle Database must be running in `ARCHIVELOG` mode.

**Note:**

AutoUpgrade creates a guaranteed restore point (GRP) during Deploy processing mode. You do not need to have a previously defined guaranteed restore point.

Example 3-21 Setting up Archive Logging and Fast Recovery Area (FRA) Before Using AutoUpgrade

In the following example, `your-directory-or-diskgroup` is the directory path or disk group where your recovery area is placed. The value for `DB_RECOVERY_FILE_DEST_SIZE` is specified as 50GB, but you should use the value that you require for your recovery area.

    sqlplus / as sysdba
    shutdown immediate;
    startup mount;
    alter system set db_recovery_file_dest_size = 50g scope=both sid='*';
    alter system set db_recovery_file_dest ='your-directory-or-diskgroup' scope=both sid='*';
    alter database archivelog;
    alter database open;
    alter pluggable database all open;

Example 3-22 Password Files and Security Password File Updates

During the upgrade, the AutoUpgrade utility copies the password file from the source Oracle Database Oracle home to the target Oracle Database Oracle home. However, the copied password file retains the earlier release password file version. Oracle recommends that you regenerate the password file to update it to the new release password file version.

Example 3-23 Transparent Data Encryption and AutoUpgrade

To enable the AutoUpgrade utility to obtain the privileges required for copying transparent data encryption keystores, you must enable auto-login for these keystores so that AutoUpgrade can copy them to the target release Oracle home. If you do not enable auto-login, then AutoUpgrade cannot complete the upgrade.

In addition, AutoUpgrade looks for the location of the Oracle Net administration directory using the `TNS_ADMIN` environment variable. If your `TNS_ADMIN` environment variable is not defined, then the path to the network administration directory defaults to the path `Oracle_home``/network/admin`. If you need to specify a different path, then specify the path in your configuration file using the local configuration parameter `source_tns_admin_dir`, and if necessary, the target path with `target_tns_admin_dir`.

Enable an Auto-Login or a Local Auto-Login Software Keystore by using the `ADMINISTRATOR KEY MANAGEMENT` or `SYSKM` privilege on your existing keystore. For example, to create an auto-login software keystore of the password-protected keystore that is located in the `/etc/ORACLE/WALLETS/orcl` directory:

    ADMINISTER KEY MANAGEMENT CREATE AUTO_LOGIN KEYSTORE
    FROM KEYSTORE '/etc/ORACLE/WALLETS/tde'
    IDENTIFIED BY password;

    keystore altered.

**Note:**

After AutoUpgrade completes copying the transparent data encryption keystores, disable auto login, so that your previous release security is restored.

**Related Topics**

- [Creating an Auto-Login or a Local Auto-Login Software Keystore](../asoag/configuring-transparent-data-encryption.md)
- [Overview of Local Naming Parameters](../netrf/local-naming-parameters-in-tns-ora-file.md)
- [Oracle Database Enterprise User Security Administrator's Guide](../dbimi/using-oracle-wallet-manager.md)
- [DB_RECOVERY_FILE_DEST](../refrn/DB_RECOVERY_FILE_DEST.md)

**Parent topic:** [Using AutoUpgrade for Oracle Database Upgrades](using-autoupgrade-oracle-database-upgrades.md)
