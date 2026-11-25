If you use Oracle wallet with Transparent Data Encryption (TDE), then copy the `sqlnet.ora` and wallet file to the new Oracle home.

You must copy the `sqlnet.ora` and the wallet file manually before starting the upgrade.

1.  Log in as an authorized user.
2.  Manually copy the `sqlnet.ora` file, and the wallet file, `ewallet.p12`, to the new release Oracle home.
3.  Open the Oracle wallet in mount.
    For example:

        SQL> STARTUP MOUNT;
        SQL> ALTER SYSTEM SET ENCRYPTION WALLET OPEN

**Parent topic:** [Database Preparation Tasks to Complete Before Starting Oracle Database Upgrades](db-preparation-tasks-before-starting-db-upgrades.md)
