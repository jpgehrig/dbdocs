If your database uses Transparent Data Encryption (TDE) and a software keystore, and you rely on the `sqlnet.ora` parameter `ENCRYPTION_WALLET_LOCATION` to locate the TDE software keystore, then ensure that the new release `sqlnet.ora` has a proper configuration.

**Note:**

This procedure using `sqlnet.ora` to configure keystores is deprecated. Oracle recommends that you use the instance initialization file-based approach using the `WALLET_ROOT` and `TDE_CONFIGURATION` initialization parameters. After the upgrade, review and configure the `WALLET_ROOT` initialization parameter.

If you use the `sqlnet.ora` file to configure keystores, then you must copy `sqlnet.ora` and the keystore file manually to a keystore location outside of the Oracle home. Wallets should be stored in a location outside of an Oracle Home. If you move the wallet, then you must update `sqlnet.ora` before starting the upgrade. For auto-login wallets, you must also copy the `cwallet.sso` file manually to the new keystore location.

1.  Log in as the user owning the Oracle home software, typically `oracle`.
2.  Manually copy the `sqlnet.ora` file, and the keystore file, `ewallet.p12`, to the new release Oracle home.
3.  If you have enabled an auto-login wallet, then also copy the `cwallet.sso` file to the new release Oracle home. There is no need to complete the next step. If you have not enabled an auto-login wallet, then proceed to the next step.
4.  If you have not enabled an auto-login wallet, then open the Oracle wallet in mount.
    For example:

        SQL> STARTUP MOUNT;
        SQL> ALTER SYSTEM SET ENCRYPTION WALLET OPEN

    To create a local auto-login keystore for a software keystore, use the following syntax:

        ADMINISTER KEY MANAGEMENT CREATE LOCAL AUTO_LOGIN KEYSTORE
        FROM KEYSTORE 'keystore_location'
        IDENTIFIED BY software_keystore_password;

    In this specification:

    - `LOCAL` enables you to create a local auto-login software keystore. Otherwise, omit this clause if you want the keystore to be accessible by other computers.

    - `keystore_location` is the path to the keystore directory location of the keystore that is configured in the `sqlnet.ora` file.

    - `software_keystore_password` is the existing password of the configured software keystore.

**Related Topics**

- [About the Keystore Location in the sqlnet.ora File](../asoag/using-sqlnet-ora-to-configure-tde-keystores.md)

**Parent topic:** [Database Preparation Tasks to Complete Before Starting Oracle Database Upgrades](db-preparation-tasks-before-starting-db-upgrades.md)
