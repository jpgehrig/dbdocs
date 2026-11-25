## 3 Security in an Oracle Sharding Environment

### Using Transparent Data Encryption with Oracle Sharding

Oracle Sharding supports Transparent Data Encryption (TDE), but in order to successfully move chunks in a sharded database with TDE enabled, all of the shards must share and use the same encryption key for the encrypted tablespaces.

A sharded database consists of multiple independent databases and a catalog database. For TDE to work properly, especially when data is moved between shards, certain restrictions apply. In order for chunk movement between shards to work when data is encrypted, you must ensure that all of the shards use the same encryption key.

There are two ways to accomplish this:

- Create and export an encryption key from the shard catalog, and then import and activate the key on all of the shards individually.

- Store the wallet in a shared location and have the shard catalog and all of the shards use the same wallet.

The following TDE statements are automatically propagated to shards when executed on the shard catalog with shard DDL enabled:

- alter system set encryption wallet open/close identified by password

- alter system set encryption key

- administer key management set keystore \[open\|close\] identified by password

- administer key management set key identified by password

- administer key management use key identified by password

- administer key management create key store identified by password

#### Limitations

The following limitations apply to using TDE with Oracle Sharding.

- For `MOVE CHUNK` to work, all shard database hosts must be on the same platform.

- `MOVE CHUNK` cannot use compression during data transfer, which may impact performance.

- Only encryption on the tablespace level is supported. Encryption on specific columns is not supported.

**See Also:**

[Oracle Database Advanced Security Guide](../asoag/asopart1.md) for more information about TDE

#### Creating a Single Encryption Key on All Shards

To propagate a single encryption key to all of the databases in the sharded database configuration, you must create a master encryption key on the shard catalog, then use wallet export, followed by wallet import onto the shards, and activate the keys.

**Note:**

This procedure assumes that the keystore password and wallet directory path are the same for the shard catalog and all of the shards. If you require different passwords and directory paths, all of the commands should be issued individually on each shard and the shard catalog with shard DDL disabled using the shard’s own password and path.

These steps should be done before any data encryption is performed.

1.  Create an encryption key on the shard catalog.
    With shard DDL enabled, issue the following statements.

        ADMINISTER KEY MANAGEMENT CREATE KEYSTORE wallet_directory_path IDENTIFIED BY
         keystore_password;
        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN IDENTIFIED BY keystore_password;

    The keystore_password should be the same if you prefer to issue wallet open and close commands centrally from the catalog.

    **Note:**

    The wallet directory path should match the `ENCRYPTION_WALLET_LOCATION` in the corresponding sqlnet.ora.

    `ENCRYPTION_WALLET_LOCATION` parameter is being deprecated. You are advised to use the `WALLET_ROOT` static initialization and `TDE_CONFIGURATION` dynamic initialization parameter instead.

    With shard DDL disabled, issue the following statement.

        ADMINISTER KEY MANAGEMENT SET KEY IDENTIFIED BY keystore_password WITH BACKUP;

    An encryption key is created and activated in the shard catalog database’s wallet.

    If you issue this statement with DDL enabled, it will also create encryption keys in each of the shards’ wallets, which are different keys from that of the catalog. In order for data movement to work, you cannot use different encryption keys on each shard.
2.  Get the master key ID from the shard catalog keystore.
        SELECT KEY_ID  FROM V$ENCRYPTION_KEYS
        WHERE ACTIVATION_TIME =
         (SELECT MAX(ACTIVATION_TIME) FROM V$ENCRYPTION_KEYS
          WHERE ACTIVATING_DBID = (SELECT DBID FROM V$DATABASE));
3.  With shard DDL disabled, export the catalog wallet containing the encryption key.
        ADMINISTER KEY MANAGEMENT EXPORT ENCRYPTION KEYS WITH SECRET secret_phrase TO
         wallet_export_file IDENTIFIED BY keystore_password;

    (Optional) Enter the result of the step here.
4.  Physically copy the wallet file to each of the shard hosts, into their corresponding wallet export file location, or put the wallet file on a shared disk to which all of the shards have access.
5.  With shard DDL disabled, log on to each shard and import the wallet containing the key.
        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN IDENTIFIED BY keystore_password;
        ADMINISTER KEY MANAGEMENT IMPORT ENCRYPTION KEYS WITH SECRET secret_phrase FROM
         wallet_export_file IDENTIFIED BY keystore_password WITH BACKUP;
6.  Restart the shard databases.
7.  Activate the key on all of the shards.
    On the catalog with shard DDL enabled

        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN IDENTIFIED BY keystore_password;
        ADMINISTER KEY MANAGEMENT USE KEY master_key_id IDENTIFIED BY keystore_password
         WITH BACKUP;

All of the shards and the shard catalog database now have the same encryption key activated and ready to use for data encryption. On the shard catalog, you can issue TDE DDLs (with shard DDL enabled) such as:

- Create encrypted tablespaces and tablespace sets.

- Create sharded tables using encrypted tablespaces.

- Create sharded tables containing encrypted columns (with limitations).

Validate that the key IDs on all of the shards match the ID on the shard catalog.

    SELECT KEY_ID  FROM V$ENCRYPTION_KEYS
    WHERE ACTIVATION_TIME =
     (SELECT MAX(ACTIVATION_TIME) FROM V$ENCRYPTION_KEYS
      WHERE ACTIVATING_DBID = (SELECT DBID FROM V$DATABASE));

### Configuring TCP/IP with SSL/TLS for Oracle Sharding

Configuring TCP/IP with SSL/TLS for Oracle Sharding has different steps depending on the type of databases you plan to run shards on.

For information about configuring this security feature, see the documents based on the types of database you plan to run shards on.

- Autonomous Database

  For Oracle Autonomous Database, TLS is already enabled by default, and you only need to create the remaining security infrastructure, such as vaults, keys, and certificate resources on OCI.

- Base Database Service

  For Base Database Service on OCI you will need to enable TLS using the information in [Configure TCP/IP with SSL/TLS for Sharding – GSM OCI Mode (Doc ID 2881390.1)](https://support.oracle.com/rs?type=doc&id=2881390.1)

- On-Premises

  For on-premises databases, see [Configure TCP/IP with SSL/TLS for Sharding – GSM JDBC THIN MODE (Doc ID 2881420.1)](https://support.oracle.com/rs?type=doc&id=2881420.1)

More information is also available in [Configuring Oracle Database Native Network Encryption and Data Integrity](../dbseg/configuring-network-data-encryption-and-integrity.md) and [Configuring Secure Sockets Layer Authentication](../dbseg/configuring-secure-sockets-layer-authentication.md)

### Oracle Database Vault

Do not enable Oracle Database Vault (Data Vault) on your sharded databases. Oracle Sharding does not support Oracle Database Vault.
