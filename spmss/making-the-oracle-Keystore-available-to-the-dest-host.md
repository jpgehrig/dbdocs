If transparent encryption is configured on the source database, then you must ensure that the Oracle software keystore from the source database is available to the auxiliary instance. Manually copy the keystore from the source database to the destination host.

The Oracle software keystore contains the TDE master key used to:

- decrypt encrypted backups when performing backup-based duplication.

- decrypt database or tablespace data when performing active database duplication of TDE-encrypted databases or tablespaces.

The following are the requirements for the keystore at the duplicate database:

- The keystore must be in the default location, or in the location indicated by the `sqlnet.ora` file.

- Permissions on the Oracle keystore file must be set so that the database can access the file.

- During duplication, the auxiliary instance is restarted thereby causing the Oracle software keystore to become unavailable. To ensure that the auxiliary instance has access to the keystore, set the `ENCRYPTION_WALLET_LOCATION` parameter in the `sqlnet.ora` file such that it points to the keystore location.

  The `ENCRYPTION_WALLET_LOCATION` `sqlnet.ora` parameter is deprecated in Oracle Database Release 19c. Use the `WALLET_ROOT` initialization parameter with the `TDE_CONFIGURATION` initialization parameter to configure the software keystore location.

- With Oracle Real Application Clusters (Oracle RAC), register the auxiliary instance statically with an Oracle Grid Infrastructure listener and use the `ENVS` parameter in the `sqlnet.ora` file of the Oracle Grid home to specify environment variables that set the keystore location and the unique name of the database.

  The following example sets the `ENVS` parameter in `sqlnet.ora` to specify the keystore location and unique database name:

       (ENVS="ORACLE_UNQNAME=cdbrptl, ENCRYPTION_WALLET_LOCATION=(SOURCE=(METHOD=FILE)(METHOD_DATA=(DIRECTORY=/etc/ORACLE/WALLETS/cdbrpt1)))")

- If the source database uses a password-based software keystore (not an auto-login software keystore), then you must provide the keystore password before you begin the duplication.

  Use the `SET` command with the `DECRYPTION WALLET OPEN IDENTIFIED BY` clause to specify the password that must be used to open the keystore.

  The following command specifies the password used to open the keystore (where `password` is a placeholder for the actual password that you enter):
      SET DECRYPTION WALLET OPEN IDENTIFIED BY password;

**See Also:**

- [Oracle Database Advanced Security Guide](../asoag/using-sqlnet-ora-to-configure-tde-keystores.md) for information about specifying the Oracle keystore location in `sqlnet.ora`

- [Oracle Database Advanced Security Guide](../asoag/configuring-transparent-data-encryption.md) for information about the default Oracle keystore location

- [Oracle Database Advanced Security Guide](../asoag/configuring-transparent-data-encryption.md) for information about converting a standard Oracle keystore to an auto-login keystore

- [Oracle Database Backup and Recovery Reference](../rcmrf/SET.md) for information about the `SET` command

**Parent topic:** [Preparing the Auxiliary Instance on the Destination Host](preparing-the-auxiliary-instance-destination-host.md)
