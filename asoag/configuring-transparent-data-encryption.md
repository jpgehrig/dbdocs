## 4 Configuring Transparent Data Encryption

You can configure software or external keystores, for use on both individual table columns or entire tablespaces.

- About Configuring Transparent Data Encryption
  To configure Transparent Data Encryption, you must perform a one-time setup before you create keystores and encrypt data.
- Transparent Data Encryption Keystore Search Order
  The search order for the TDE keystore depends on how you have set either the instance initialization parameters, the `sqlnet.ora` parameters, or the environment variables.
- Configuring a TDE Wallet
  A TDE wallet is a container for the master encryption key, and it resides in the software file system.
- Configuring an External Keystore
  There are two types of external keystores that Oracle Database supports: Oracle Key Vault keystores and OCI Vault - Key Management keystores.
- Encrypting Columns in Tables
  You can use Transparent Data Encryption to encrypt individual columns in database tables.
- Encryption Conversions for Tablespaces and Databases
  You can perform encryption operations on both offline and online tablespaces and databases.
- Transparent Data Encryption Data Dynamic and Data Dictionary Views
  You can query a set of dynamic and data dictionary views to find more information about Transparent Data Encryption (TDE) data.

**Parent topic:** [Using Transparent Data Encryption](asopart1.md)

### 4.1 About Configuring Transparent Data Encryption

To configure Transparent Data Encryption, you must perform a one-time setup before you create keystores and encrypt data.

Before you can begin to encrypt data, you must perform a one-time configuration using the static `WALLET_ROOT` parameter and the dynamic `TDE_CONFIGURATION` parameter to designate the location and type of keystores that you plan to use.

The `WALLET_ROOT` parameter specifies the top directory for many different software keystores (such as TDE, Oracle Enterprise User Security (EUS), TLS). For TDE, the directory for automated discovery is `WALLET_ROOT/tde`.

The `TDE_CONFIGURATION` parameter specifies the type of keystore (software keystore or Oracle Key Vault). After you set the type of keystore using `TDE_CONFIGURATION`, when you create the keystore, Oracle Database creates a directory within the `WALLET_ROOT` location for the keystore type. For example, if you set `TDE_CONFIGURATION` to `FILE`, then Oracle Database creates a TDE wallet in `WALLET_ROOT/tde`. To use Oracle Key Vault, install the Oracle Key Vault client software into `WALLET_ROOT/okv` and set `TDE_CONFIGURATION` to `OKV`. To establish an auto-open Oracle Key Vault configuration, add the Oracle Key Vault password into an auto-open wallet in `WALLET_ROOT/tde`, and set `TDE_CONFIGURATION` to `OKV|FILE`. If you want to migrate from one keystore type to another, then you must first set `TDE_CONFIGURATION` parameter to the keystore type that you want to use, and then use the `ADMINISTER KEY MANAGEMENT` statement to perform the migration. For example, you can migrate from a TDE keystore to `OKV` by setting it to `OKV|FILE`.

The `KEYSTORE_MODE` column of the `V$ENCRYPTION_WALLET` dynamic view shows whether united mode or isolated mode has been configured. If you want to change the database default encryption algorithm from AES128, then after you apply patch 30398099, you can set a dynamic initialization parameter by executing the following statement:

    ALTER SYSTEM SET "_TABLESPACE_ENCRYPTION_DEFAULT_ALGORITHM" = 'AES256' SCOPE = BOTH SID = '*';

**Note:**

In previous releases, the `SQLNET.ENCRYPTION_WALLET_LOCATION` parameter was used to define the keystore directory location. This parameter has been deprecated. Oracle recommends that you use the `WALLET_ROOT` static initialization parameter and `TDE_CONFIGURATION` dynamic initialization parameter instead.

**Related Topics**

- Transparent Data Encryption Keystore Search Order

**Parent topic:** Configuring Transparent Data Encryption

### 4.2 Transparent Data Encryption Keystore Search Order

The search order for the TDE keystore depends on how you have set either the instance initialization parameters, the `sqlnet.ora` parameters, or the environment variables.

Oracle Database retrieves the keystore by searching in these locations, in the following order:

1.  The location set by the `WALLET_ROOT` instance initialization parameter, when the `KEYSTORE_CONFIGURATION` attribute of the `TDE_CONFIGURATION` initialization parameter is set to `FILE`. Oracle recommends that you use this parameter to configure the keystore location.

2.  If the `KEYSTORE_CONFIGURATION` attribute of the `TDE_CONFIGURATION` initialization parameter is not set to `FILE` or `WALLET_ROOT` is not set, then the location specified by the `WALLET_LOCATION` setting in the `sqlnet.ora` file. (Note that you cannot have multiple `WALLET_LOCATION` settings in this file.)

3.  If `WALLET_ROOT` and `WALLET_LOCATION` are not set, then the location specified by the `ENCRYPTION_WALLET_LOCATION` parameter (now deprecated in favor of `WALLET_ROOT`) in the `sqlnet.ora` file.

4.  If none of these parameters are set, and if the `ORACLE_BASE` environment variable is set, then the `$ORACLE_BASE/admin/``db_unique_name``/wallet` directory. If `ORACLE_BASE` is not set, then `$ORACLE_HOME/admin/``db_unique_name``/wallet`.

**Parent topic:** Configuring Transparent Data Encryption

### 4.3 Configuring a TDE Wallet

A TDE wallet is a container for the master encryption key, and it resides in the software file system.

- About Configuring a TDE Wallet
  A software keystore is a container that stores the TDE master encryption key.
- Step 1: Configure the TDE Wallet Location and Type
  You must configure the TDE wallet location and type by setting `WALLET_ROOT` in `init.ora` and `TDE_CONFIGURATION` in the database instance.
- Step 2: Create the TDE Wallet
  After you have specified a directory location for the software keystore, you can create the TDE wallet.
- Step 3: Open the TDE Wallet
  Depending on the type of keystore you create, you must manually open the TDE wallet before you can use it.
- Step 4: Set the TDE Master Encryption Key in the TDE Wallet
  Once the TDE wallet is open, you can set a TDE master encryption key for it.
- Step 5: Encrypt Your Data
  Now that you have completed the configuration, you can begin to encrypt data in the PDB.

**Parent topic:** Configuring Transparent Data Encryption

#### 4.3.1 About Configuring a TDE Wallet

A software keystore is a container that stores the TDE master encryption key.

Before you can configure the TDE wallet, you first must define a location for it by setting the static initialization parameter `WALLET_ROOT`. Then, after a database restart, you must set the dynamic initialization parameter `TDE_CONFIGURATION` to instruct the database to retrieve the master encryption key from a TDE wallet, Oracle Key Vault, or Oracle Cloud Interface (OCI) Key Management Service (KMS), according to their documentation. The database locates this TDE wallet by first checking the `WALLET_ROOT` setting. If this setting has not been created, then the database checks the `sqlnet.ora` file. You can create other TDE wallets, such as copies of the wallet and export files that contain keys, depending on your needs. If you must remove or delete the TDE wallet that you configured in the `WALLET_ROOT` location, then you must do so only after you copied all TDE wallets (including backups and auto-login wallets) in the old to the new location. Then you must reset `WALLET_ROOT` to point to the new location of the TDE wallet.

After you configure the TDE wallet location by using the `WALLET_ROOT` and `TDE_CONFIGURATION` parameters, you can log in to the CDB to create and open the keystore, and then set the TDE master encryption key. After you complete these steps, you can begin to encrypt data.

**Parent topic:** Configuring a TDE Wallet

#### 4.3.2 Step 1: Configure the TDE Wallet Location and Type

You must configure the TDE wallet location and type by setting `WALLET_ROOT` in `init.ora` and `TDE_CONFIGURATION` in the database instance.

1.  Log in to the server where the Oracle database resides.
2.  If necessary, create a wallet directory.
    Typically, the wallet directory is located in the `$ORACLE_BASE/admin/``db_unique_name` directory, and it is named `wallet`. Preferably, this directory should be empty.
3.  Log in to the database instance as a user who has been granted the `SYSDBA` administrative privilege.
    For example:
        sqlplus sec_admin as sysdba
        Enter password: password
4.  Set the `WALLET_ROOT` static initialization parameter for the wallet directory.
    The TDE wallets will be created in `WALLET_ROOT``/tde`. For example, for a database instance named `orcl`:
        ALTER SYSTEM SET WALLET_ROOT = '$ORACLE_BASE/ADMIN/ORCL/WALLET' SCOPE = SPFILE SID = '*';
5.  Set the `TDE_CONFIGURATION` parameter to specify the TDE wallet type.
    For example:
        ALTER SYSTEM SET TDE_CONFIGURATION="KEYSTORE_CONFIGURATION=keystore_type" SCOPE=BOTH SID = '*';

    In this specification, `keystore_type` must be set to `FILE` to configure a TDE wallet.

    To configure a TDE keystore if the server parameter file (`spfile`) is in use, set `scope` to `both`:

        ALTER SYSTEM SET TDE_CONFIGURATION="KEYSTORE_CONFIGURATION=FILE" SCOPE = BOTH SID = '*';

**Parent topic:** Configuring a TDE Wallet

#### 4.3.3 Step 2: Create the TDE Wallet

After you have specified a directory location for the software keystore, you can create the TDE wallet.

- About Creating TDE Wallets
  There are three different types of TDE wallets.
- Creating a Password-Protected Software Keystore
  A password-protected software keystore requires a password, which is used to protect the TDE master keys.
- Creating an Auto-Login or a Local Auto-Login Software Keystore
  As an alternative to password-protected keystores, you can create either an auto-login or local auto-login software keystore.

**Parent topic:** Configuring a TDE Wallet

##### 4.3.3.1 About Creating TDE Wallets

There are three different types of TDE wallets.

You can create password-protected TDE wallets, auto-login TDE wallets, and local auto-login TDE wallets.

Be aware that running the query `SELECT * FROM V$ENCRYPTION_WALLET` will automatically open an auto-login TDE wallet. For example, suppose you have a password-protected TDE wallet and an auto-login TDE wallet. If the password-protected TDE wallet is open and you close the password-protected TDE wallet and then query the `V$ENCRYPTION_WALLET` view, then the output will indicate that a TDE wallet is open. However, this is because `V$ENCRYPTION_WALLET` opened up the auto-login TDE wallet and then displayed the status of the auto-login wallet.

**Related Topics**

- [Types of Keystores](introduction-to-transparent-data-encryption.md)

**Parent topic:** Step 2: Create the TDE Wallet

##### 4.3.3.2 Creating a Password-Protected Software Keystore

A password-protected software keystore requires a password, which is used to protect the TDE master keys.

A TDE wallet can only contain TDE-related security objects, and no security objects used by other database or application components. In addition, do not use orapki or mkstore to create password-protected or (local) auto-open TDE wallets. Instead, use the `ADMINISTER KEY MANAGEMENT statement`.

1.  Log in to the database instance as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Use the `SHOW PARAMETER` command to confirm that `WALLET_ROOT` is set, and `TDE_CONFIGURATION` is set to `KEYSTORE_CONFIGURATION=FILE`.
3.  Run the `ADMINISTER KEY MANAGEMENT` SQL statement to create the keystore using the following syntax:
        ADMINISTER KEY MANAGEMENT CREATE KEYSTORE IDENTIFIED BY software_keystore_password;

    The `/tde` directory is automatically created under `WALLET_ROOT`, if it does not already exist. In Oracle Automatic Storage Management (Oracle ASM), for the `/tde` directory to be automatically created if it does not already exist, `WALLET_ROOT` must point to `+DATA/ORACLE_UNQNAME`.

    In this specification, `software_keystore_password` is the password of the keystore that you, the security administrator, creates.

    For example, to create the keystore in the `WALLET_ROOT/tde` directory:

        ADMINISTER KEY MANAGEMENT CREATE KEYSTORE IDENTIFIED BY password;

        keystore altered.

    After you run this statement, the `ewallet.p12` file, which is the keystore, appears in the keystore location.

**Parent topic:** Step 2: Create the TDE Wallet

##### 4.3.3.3 Creating an Auto-Login or a Local Auto-Login Software Keystore

As an alternative to password-protected keystores, you can create either an auto-login or local auto-login software keystore.

Both of these keystores have system-generated passwords. They are also PKCS#12-based files. The auto-login software keystore can be opened from different computers from the computer where this keystore resides, but the local auto-login software keystore can only be opened from the computer on which it was created. Both the auto-login and local auto-login keystores are created from the password-protected software keystores. Creating any of them does not require database downtime.

1.  Log in to the database instance as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.

    Confirm that `WALLET_ROOT` is set, and `TDE_CONFIGURATION` is set to `KEYSTORE_CONFIGURATION=FILE`.

2.  Create the auto-login or local auto-login keystore by using the following syntax:

        ADMINISTER KEY MANAGEMENT CREATE [LOCAL] AUTO_LOGIN KEYSTORE
        FROM KEYSTORE IDENTIFIED BY software_keystore_password;

    In this specification:

    - `LOCAL` enables you to create a local auto-login software keystore. Otherwise, omit this clause if you want the keystore to be accessible by other computers. `LOCAL` creates a local auto-login wallet file, `cwallet.sso`, and this wallet will be tied to the host on which it was created. For an Oracle Real Application Clusters (Oracle RAC) environment, omit the `LOCAL` keyword, because each Oracle RAC node has a different host name. If you configure a local auto-login wallet for the Oracle RAC instance, then only the first Oracle RAC node, where the `cwallet.sso` file was created, would be able to access the software keystore. If you try to open the keystore from another node instead of from that first node, there would be a problem auto-opening `cwallet.sso`, and so it would result in a failure to auto-open the software keystore. This restriction applies if you are using a shared location to hold the `cwallet.sso` file for the Oracle RAC cluster, because using `LOCAL` only works if you have a separate `cwallet.sso` file (containing the same credentials) on each node of the Oracle RAC environment.

    - `software_keystore_password` is the password of the keystore from which you want to create.

    For example, to create an auto-login software keystore of the password-protected keystore that is located in the`/etc/ORACLE/WALLETS/tde` directory:

        ADMINISTER KEY MANAGEMENT CREATE AUTO_LOGIN KEYSTORE
        FROM KEYSTORE IDENTIFIED BY password;

        keystore altered.

    After you run this statement, the `cwallet.sso` file appears in the keystore location. The `ewallet.p12` file is the password-protected wallet.

Follow these guidelines:

- Do not remove the `PKCS#12` wallet (`ewallet.p12` file) after you create the auto-login keystore (`.sso` file). You must have the `PKCS#12` wallet to regenerate or rekey the TDE master encryption key in the future.
- Remember that Transparent Data Encryption uses an auto login keystore only if it is available at the correct location (`WALLET_ROOT/tde`), `ENCRYPTION_WALLET_LOCATION`, or the default keystore location), and the SQL statement to open an encrypted keystore has not already been executed. If you have the `ENCRYPTION_WALLET_LOCATION` parameter set, then be aware this parameter is deprecated. Oracle recommends that you use the `WALLET_ROOT` static initialization parameter and `TDE_CONFIGURATION` dynamic initialization parameter instead.

**Related Topics**

- Creating a Password-Protected Software Keystore

**Parent topic:** Step 2: Create the TDE Wallet

#### 4.3.4 Step 3: Open the TDE Wallet

Depending on the type of keystore you create, you must manually open the TDE wallet before you can use it.

- About Opening TDE Wallets
  A password-protected TDE wallet must be open before any TDE master encryption keys can be created or accessed in the TDE wallet.
- Opening a TDE Wallet
  To open a TDE wallet, you must use the `ADMINISTER KEY MANAGEMENT` statement with the `SET KEYSTORE OPEN` clause.

**Parent topic:** Configuring a TDE Wallet

##### 4.3.4.1 About Opening TDE Wallets

A password-protected TDE wallet must be open before any TDE master encryption keys can be created or accessed in the TDE wallet.

Many Transparent Data Encryption operations require the TDE wallet to be open. There are two ways that you can open the TDE wallet:

- Manually open the TDE wallet by issuing the `ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN` statement. Afterward, you can perform the operation.

- Include the `FORCE KEYSTORE` clause in the `ADMINISTER KEY MANAGEMENT` statement that is used to perform the operation. `FORCE KEYSTORE` temporarily opens the TDE wallet for the duration of the operation, and when the operation completes, the TDE wallet is closed again. `FORCE KEYSTORE` is useful for situations when the database is heavily loaded. In this scenario, because of concurrent access to encrypted objects in the database, the auto-login TDE wallet continues to open immediately after it has been closed but before a user has had chance to open the password-based TDE wallet.

TDE wallets can be in the following states: open, closed, open but with no master encryption key, open but with an unknown master encryption key, undefined, or not available (that is, not present in the `WALLET_ROOT/tde` location).

After you manually open a TDE wallet, it remains open until you manually close it. Each time you restart a database instance, you must manually open the password TDE wallet to reenable encryption and decryption operations.

You can check the status of whether a TDE wallet is open or not by querying the `STATUS` column of the `V$ENCRYPTION_WALLET` view.

**Related Topics**

- [Performing Operations That Require a Keystore Password](managing-keystore-and-tde-master-encryption-key.md)
- [How Keystore Open and Close Operations Work in United Mode](managing-keystores-encryption-keys-in-united-mode.md)

**Parent topic:** Step 3: Open the TDE Wallet

##### 4.3.4.2 Opening a TDE Wallet

To open a TDE wallet, you must use the `ADMINISTER KEY MANAGEMENT` statement with the `SET KEYSTORE OPEN` clause.

1.  Log in to the database instance as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Run the `ADMINISTER KEY MANAGEMENT` statement to open the TDE wallet.
        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN
        IDENTIFIED BY TDE_wallet_password;
        keystore altered.

    To switch over to opening the password-protected TDE wallet when an auto-login keystore is configured and is currently open, specify the `FORCE KEYSTORE` clause as follows.

        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN
        FORCE KEYSTORE
        IDENTIFIED BY EXTERNAL STORE;
        keystore altered.

    Here, the `IDENTIFIED BY EXTERNAL STORE` clause is included in the statement because the TDE wallet credentials exist in an external store. This enables the password-protected TDE wallet to be opened without specifying the TDE wallet password within the statement itself.

    If the `WALLET_ROOT` parameter has been set, then Oracle Database finds the external store by searching in this path: `WALLET_ROOT``/``PDB_GUID``/tde_seps`.
3.  Confirm that the TDE wallet is open.
        SELECT STATUS FROM V$ENCRYPTION_WALLET;

Note that if the TDE wallet is open but you have not created a TDE master encryption key yet, the `STATUS` column of the `V$ENCRYPTION_WALLET` view reminds you with an `OPEN_NO_MASTER_KEY` status.

**Parent topic:** Step 3: Open the TDE Wallet

#### 4.3.5 Step 4: Set the TDE Master Encryption Key in the TDE Wallet

Once the TDE wallet is open, you can set a TDE master encryption key for it.

- About Setting the TDE Wallet TDE Master Encryption Key
  The TDE master encryption key is stored in the TDE wallet.
- Setting the TDE Master Encryption Key in the TDE Wallet
  To set the TDE master encryption key in a TDE wallet, use the `ADMINISTER KEY MANAGEMENT` statement with the `SET KEY` clause.

**Parent topic:** Configuring a TDE Wallet

##### 4.3.5.1 About Setting the TDE Wallet TDE Master Encryption Key

The TDE master encryption key is stored in the TDE wallet.

The TDE master encryption key protects the TDE table keys and tablespace encryption keys. By default, the TDE master encryption key is a key that TDE generates. You can find if a TDE wallet has no TDE master encryption key set or an unknown TDE master encryption key by querying the `STATUS` column of the `V$ENCRYPTION_WALLET` view.

You can import a master encryption key (bring your own key (BYOK)), that was created outside of the database, into the TDE wallet. You can set a key for immediate use, using `ADMINISTER KEY MANAGEMENT SET`, or create a key for later use, by activating it with the `ADMINISTER KEY MANAGEMENT USE KEY` statement.

**Related Topics**

- [Creating User-Defined TDE Master Encryption Keys](managing-keystore-and-tde-master-encryption-key.md)
- [Creating TDE Master Encryption Keys for Later Use](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Step 4: Set the TDE Master Encryption Key in the TDE Wallet

##### 4.3.5.2 Setting the TDE Master Encryption Key in the TDE Wallet

To set the TDE master encryption key in a TDE wallet, use the `ADMINISTER KEY MANAGEMENT` statement with the `SET KEY` clause.

1.  Log in to the database instance as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.

2.  Ensure that the database is open in `READ WRITE` mode.

    You can set the TDE master encryption key if `OPEN_MODE` is set to `READ WRITE`. To find the status, query the `OPEN_MODE` column of the `V$DATABASE` dynamic view. (If you cannot access this view, then connect as `SYSDBA` and try the query again. In order to connect as `SYSKM` for this type of query, you must create a password file for it.)

3.  Set the TDE master encryption key in the software by using the following syntax:

        ADMINISTER KEY MANAGEMENT SET KEY
        [USING TAG 'tag']
        [FORCE KEYSTORE]
        IDENTIFIED BY EXTERNAL STORE | software_keystore_password
        WITH BACKUP [USING 'backup_identifier'];

    In this specification:

    - `tag` is the associated attributes and information that you define. Enclose this setting in single quotation marks (`' '`).

    - `FORCE KEYSTORE` temporarily opens the password-protected TDE wallet for this operation. You must open the TDE wallet for this operation.

    - `FORCE KEYSTORE` should be included if the keystore is closed. This automatically opens the keystore before setting the TDE master encryption key. The `FORCE KEYSTORE` clause also switches over to opening the password-protected TDE wallet when an auto-login TDE wallet is configured and is currently open.

    - `IDENTIFIED BY` specifies the TDE wallet password. Alternatively, if the TDE wallet password is in an external store, you can use the `IDENTIFIED BY EXTERNAL STORE` clause.

    - `WITH BACKUP` creates a backup of the TDE wallet. You must use this option for password-protected TDE wallets. Optionally, you can use the `USING` clause to add a brief description of the backup. Enclose this description in single quotation marks (`' '`). This identifier is appended to the named TDE wallet file (for example, `ewallet_``time_stamp``_emp_key_backup.p12`, with `emp_key_backup` being the backup identifier). Follow the file naming conventions that your operating system uses.

    For example:

        ADMINISTER KEY MANAGEMENT SET KEY
        FORCE KEYSTORE
        IDENTIFIED BY EXTERNAL STORE | TDE_wallet_password
        WITH BACKUP USING 'emp_key_backup';

**Parent topic:** Step 4: Set the TDE Master Encryption Key in the TDE Wallet

#### 4.3.6 Step 5: Encrypt Your Data

Now that you have completed the configuration, you can begin to encrypt data in the PDB.

You can encrypt data in individual table columns or in entire tablespaces or databases.

**Related Topics**

- Encrypting Columns in Tables
- Encryption Conversions for Tablespaces and Databases

**Parent topic:** Configuring a TDE Wallet

### 4.4 Configuring an External Keystore

There are two types of external keystores that Oracle Database supports: Oracle Key Vault keystores and OCI Vault - Key Management keystores.

- About Configuring an External Keystore
  An external keystore is a separate server or device that provides security storage for encryption keys.
- Step 1: Configure the External Keystore
  You can configure the external keystore by setting the `TDE_CONFIGURATION` parameter.
- Step 2: Open the Connection to Oracle Key Vault
  After you have configured the database to use Oracle Key Vault for TDE key management, you must open the connection to Oracle Key Vault before you can use it.
- Step 3: Set the TDE Master Encryption Key in Oracle Key Vault
  After you have opened the connection to Oracle Key Vault, you are ready to set the TDE master encryption key.
- Step 4: Encrypt Your Data in United Mode
  Now that you have completed the configuration for an external keystore or for an Oracle Key Vault keystore, you can begin to encrypt data.

**Parent topic:** Configuring Transparent Data Encryption

#### 4.4.1 About Configuring an External Keystore

An external keystore is a separate server or device that provides security storage for encryption keys.

External keystores are external to an Oracle database. Oracle Database can interface with external keystores but cannot manipulate them outside of the Oracle interface. The Oracle database can request the external keystore to create a key but it cannot define how this key is stored in an external database. (Conversely, for software keystores that are created using TDE, Oracle Database has full control: that is, you can use SQL statements to manipulate this type of keystore.) Examples of external keystores are Oracle Key Vault keystores. Supported external keystores are Oracle Key Vault and the Oracle Cloud Infrastructure Vault.

To configure an external keystore, you must first include the keystore type in the `sqlnet.ora` file, open the external keystore, and then set the external keystore TDE master encryption key.

For Oracle Key Vault:

    IDENTIFIED BY "Oracle_Key_Vault_password"

After you configure the external keystore, you are ready to begin encrypting your data.

**Parent topic:** Configuring an External Keystore

#### 4.4.2 Step 1: Configure the External Keystore

You can configure the external keystore by setting the `TDE_CONFIGURATION` parameter.

1.  If the `WALLET_ROOT` parameter is set, then install the Oracle Key Vault client software into the `WALLET_ROOT/okv` directory.
2.  Log in to the database instance as a user who has been granted the `ALTER SYSTEM` administrative privilege.
3.  Set the `TDE_CONFIGURATION` dynamic initialization parameter to specify the keystore type by using the following syntax:
        ALTER SYSTEM SET TDE_CONFIGURATION="KEYSTORE_CONFIGURATION=keystore_type" SCOPE=BOTH SID = '*';

    In this specification:

    - `keystore_type` can be one of the following types:

      - `OKV` to configure an Oracle Key Vault keystore

      - `HSM` to configure a hardware security module (HSM) keystore

    For example, to configure your database to use Oracle Key Vault:

        ALTER SYSTEM SET TDE_CONFIGURATION="KEYSTORE_CONFIGURATION=OKV"
        SCOPE=BOTH SID = '*";

**Parent topic:** Configuring an External Keystore

#### 4.4.3 Step 2: Open the Connection to Oracle Key Vault

After you have configured the database to use Oracle Key Vault for TDE key management, you must open the connection to Oracle Key Vault before you can use it.

- About Opening the Connection to Oracle Key Vault
  You must open the connection to Oracle Key Vault so that it is accessible to the database before you can perform any encryption or decryption.
- Opening an External Keystore
  To open an external keystore, use the `ADMINISTER KEY MANAGEMENT` statement with the `SET KEYSTORE OPEN` clause.

**Parent topic:** Configuring an External Keystore

##### 4.4.3.1 About Opening the Connection to Oracle Key Vault

You must open the connection to Oracle Key Vault so that it is accessible to the database before you can perform any encryption or decryption.

If a recovery operation is needed on your database (for example, if the database was not cleanly shut down, and has an encrypted tablespace that needs recovery), then you must open the connection to Oracle Key Vault before you can open the database itself.

There are two ways that you can open the Oracle Key Vault connection:

- Manually open the keystore by issuing the `ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN` statement. Afterward, you can perform the operation.

- Include the `FORCE KEYSTORE` clause in the `ADMINISTER KEY MANAGEMENT` statement. `FORCE KEYSTORE` temporarily opens the keystore for the duration of the operation, and when the operation completes, the keystore is closed again. `FORCE KEYSTORE` is useful for situations when the database is heavily loaded. In this scenario, because of concurrent access to encrypted objects in the database, the auto-login keystore continues to open immediately after it has been closed but before a user has had a chance to open the password-based keystore.

To check the status of the keystore, query the `STATUS` column of the `V$ENCRYPTION_WALLET` view. Keystores can be in the following states: `CLOSED`, `NOT_AVAILABLE` (that is, not present in the `WALLET_ROOT` location), `OPEN`, `OPEN_NO_MASTER_KEY`, `OPEN_UNKNOWN_MASTER_KEY_STATUS`.

Be aware that for external keystores, if the database is in the mounted state, then it cannot check if the master key is set because the data dictionary is not available. In this situation, the status will be `OPEN_UNKNOWN_MASTER_KEY_STATUS`.

**Related Topics**

- [How Keystore Open and Close Operations Work in United Mode](managing-keystores-encryption-keys-in-united-mode.md)

**Parent topic:** Step 2: Open the Connection to Oracle Key Vault

##### 4.4.3.2 Opening an External Keystore

To open an external keystore, use the `ADMINISTER KEY MANAGEMENT` statement with the `SET KEYSTORE OPEN` clause.

1.  Log in to the database instance as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Open the external keystore by using the following syntax:
        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN
        [FORCE KEYSTORE]
        IDENTIFIED BY EXTERNAL STORE | "external_key_manager_password"
        [CONTAINER = ALL | CURRENT];

    In this specification:

    - `FORCE KEYSTORE` enables the keystore operation if the keystore is closed.

    - `IDENTIFIED BY` can be one of the following settings:

      - `EXTERNAL STORE` uses the keystore password stored in the external store to perform the keystore operation.

      - `external_key_manager_password` is for an external keystore manager, which can be Oracle Key Vault or OCI Vault - Key Management. Enclose this password in double quotation marks. For Oracle Key Vault, enter the password that was given during the Oracle Key Vault client installation. If at that time no password was given, then the password in the `ADMINISTER KEY MANAGEMENT` statement becomes `NULL`.

    For Oracle Key Vault in a multitenant environment, to open the connection into Oracle KeyVault for the `CDB$ROOT` and all open PDBs:

        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN [FORCE KEYSTORE]
        IDENTIFIED BY Oracle_Key_Vault_password
        CONTAINER = ALL;
3.  Repeat this procedure each time you restart the database instance.

**Parent topic:** Step 2: Open the Connection to Oracle Key Vault

#### 4.4.4 Step 3: Set the TDE Master Encryption Key in Oracle Key Vault

After you have opened the connection to Oracle Key Vault, you are ready to set the TDE master encryption key.

- About Setting the External Keystore TDE Master Encryption Key
  You must create a TDE master encryption key that is stored inside the external keystore.
- Setting a New TDE Master Encryption Key
  You should complete this procedure if you have not previously configured an external keystore for Transparent Data Encryption.
- Migration of an Encrypted Database from a TDE Wallet to Oracle Key Vault or OCI KMS
  To switch from a TDE wallet to centralized key management with Oracle Key Vault or Oracle Cloud Infrastructure (OCI) Key Management Service (KMS), after you upload all current and retired TDE master keys you must migrate the database from the TDE wallet to Oracle Key Vault or OCI KMS.

**Parent topic:** Configuring an External Keystore

##### 4.4.4.1 About Setting the External Keystore TDE Master Encryption Key

You must create a TDE master encryption key that is stored inside the external keystore.

Oracle Database uses the master encryption key from Oracle Key Vault or Oracle Cloud Infrastructure (OCI) Key Management Service (KMS) to encrypt or decrypt TDE table keys or tablespace encryption keys (data encryption keys) inside the database.

If you have not previously configured TDE with a wallet, then you must set the master encryption key in Oracle Key Vault or OCI KMS. If you have already configured TDE with a wallet, then you must migrate the database to Oracle Key Vault or OCI KMS.

Along with the current master encryption key, all TDE keystores (TDE wallet, Oracle Key Vault, and OCI KMS) maintain historical master encryption keys that are generated after every re-key operation that rekeys the master encryption key. These historical master keys help to restore Oracle Database backups that were taken previously using one of the master encryption keys. Only Oracle Key Vault allows you to upload all historical key from a TDE wallet before migrating the database to use Oracle Key Vault. After migration to Oracle Key Vault, the TDE wallet can be deleted, which satisfies security regulation that mandate that encryption keys cannot reside on the encrypting server.

**Parent topic:** Step 3: Set the TDE Master Encryption Key in Oracle Key Vault

##### 4.4.4.2 Setting a New TDE Master Encryption Key

You should complete this procedure if you have not previously configured an external keystore for Transparent Data Encryption.

1.  Log in to the database instance as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Ensure that the database is open in `READ WRITE` mode.
    You can set the master encryption key if `OPEN_MODE` is set to `READ WRITE`. To find the status, for a non-multitenant environment, query the `OPEN_MODE` column of the `V$DATABASE` dynamic view. If you are in a multitenant environment, then run the `show_pdbs` command.
3.  Set the new master encryption key by using the following syntax:
        ADMINISTER KEY MANAGEMENT SET KEY
        [USING TAG 'tag'] [FORCE KEYSTORE]
        IDENTIFIED BY [EXTERNAL STORE | "external_key_manager_password"];

    In this specification:

    - `tag` is the associated attributes and information that you define. Enclose this setting in single quotation marks (`' '`).

    - `FORCE KEYSTORE` temporarily opens the password-protected TDE wallet for this operation. You must open the TDE wallet for this operation.

    - `IDENTIFIED BY` can be one of the following settings:

      - `EXTERNAL STORE` uses the keystore password stored in the external store to perform the keystore operation.

      - `external_key_manager_password` is for an external keystore manager, which can be Oracle Key Vault or OCI Vault - Key Management. Enclose this password in double quotation marks. For Oracle Key Vault, enter the password that was given during the Oracle Key Vault client installation. If at that time no password was given, then the password in the `ADMINISTER KEY MANAGEMENT` statement becomes `NULL`.

    For example:

        ADMINISTER KEY MANAGEMENT SET KEY
        FORCE KEYSTORE
        IDENTIFIED BY "external_key_manager_password";

        keystore altered.

**Related Topics**

- [Creating a TDE Master Encryption Key for Later Use](managing-keystore-and-tde-master-encryption-key.md)
- [Oracle Database Administrator’s Guide](../admin/getting-started-with-database-administration.md)

**Parent topic:** Step 3: Set the TDE Master Encryption Key in Oracle Key Vault

##### 4.4.4.3 Migration of an Encrypted Database from a TDE Wallet to Oracle Key Vault or OCI KMS

To switch from a TDE wallet to centralized key management with Oracle Key Vault or Oracle Cloud Infrastructure (OCI) Key Management Service (KMS), after you upload all current and retired TDE master keys you must migrate the database from the TDE wallet to Oracle Key Vault or OCI KMS.

Tools such as Oracle Data Pump and Oracle Recovery Manager require access to the old TDE wallet to perform decryption and encryption operations on data exported or backed up using the TDE wallet. Along with the current master encryption key, Oracle keystores maintain historical master encryption keys that are generated after every re-key operation that rotates the master encryption key. These historical master encryption keys help to restore Oracle database backups that were taken previously using one of the historical master encryption keys.

**Related Topics**

- [Migrating from a TDE Wallet to Oracle Key Vault](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Step 3: Set the TDE Master Encryption Key in Oracle Key Vault

#### 4.4.5 Step 4: Encrypt Your Data in United Mode

Now that you have completed the configuration for an external keystore or for an Oracle Key Vault keystore, you can begin to encrypt data.

**Related Topics**

- Encrypting Columns in Tables
- Encryption Conversions for Tablespaces and Databases
- [Oracle Key Vault Administrator's Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/asoag&id=OKVAG-GUID-0D169EB8-C355-459A-9ABD-325CA5B46DD0)

**Parent topic:** Configuring an External Keystore

### 4.5 Encrypting Columns in Tables

You can use Transparent Data Encryption to encrypt individual columns in database tables.

- About Encrypting Columns in Tables
  You can encrypt individual columns in tables.
- Data Types That Can Be Encrypted with TDE Column Encryption
  Oracle Database supports a specific set of data types that can be used with TDE column encryption.
- Restrictions on Using TDE Column Encryption
  TDE column encryption is performed at the SQL layer. Oracle Database utilities that bypass the SQL layer cannot use TDE column encryption services.
- Creating Tables with Encrypted Columns
  Oracle Database provides a selection of different algorithms that you can use to define the encryption used in encrypted columns.
- Encrypting Columns in Existing Tables
  You can encrypt columns in existing tables. As with new tables, you have a choice of different algorithms to use to definite the encryption.
- Creating an Index on an Encrypted Column
  You can create an index on an encrypted column.
- Adding Salt to an Encrypted Column
  Salt, which is a random string added to data before encryption, is a way to strengthen the security of encrypted data. .
- Removing Salt from an Encrypted Column
  You can use the ALTER TABLE SQL statement to remove salt from an encrypted column.
- Changing the Encryption Key or Algorithm for Tables with Encrypted Columns
  You can use the `ALTER TABLE` SQL statement to change the encryption key or algorithm used in encrypted columns.

**Parent topic:** Configuring Transparent Data Encryption

#### 4.5.1 About Encrypting Columns in Tables

You can encrypt individual columns in tables.

Whether you choose to encrypt individual columns or entire tablespaces depends on the data types that the table has. There are also several features that do not support TDE column encryption.

**Related Topics**

- Data Types That Can Be Encrypted with TDE Column Encryption
- Restrictions on Using TDE Column Encryption

**Parent topic:** Encrypting Columns in Tables

#### 4.5.2 Data Types That Can Be Encrypted with TDE Column Encryption

Oracle Database supports a specific set of data types that can be used with TDE column encryption.

You can encrypt data columns that use a variety of different data types.

Supported data types are as follows:

- `BINARY_DOUBLE`

- `BINARY_FLOAT`

- `CHAR`

- `DATE`

- `INTERVAL DAY TO SECOND`

- `INTERVAL YEAR TO MONTH`

- `NCHAR`

- `NUMBER`

- `NVARCHAR2`

- `RAW` (legacy or extended)

- `TIMESTAMP` (includes `TIMESTAMP WITH TIME ZONE` and `TIMESTAMP WITH LOCAL TIME ZONE`)

- `VARCHAR2` (legacy or extended)

If you want to encrypt large binary objects (LOBs), then you can use Oracle SecureFiles. Oracle SecureFiles enables you to store LOB data securely. To encrypt a LOB using SecureFiles, you use the `CREATE TABLE` or `ALTER TABLE` statements.

You cannot encrypt a column if the encrypted column size is greater than the size allowed by the data type of the column.

Table 4-1 shows the maximum allowable sizes for various data types.

Table 4-1 Maximum Allowable Size for Data Types

| Data Type              | Maximum Size |
|:-----------------------|:-------------|
| `CHAR`                 | 1932 bytes   |
| `VARCHAR2` (legacy)    | 3932 bytes   |
| `VARCHAR2` (extended)  | 32,699 bytes |
| `NVARCHAR2` (legacy)   | 1966 bytes   |
| `NVARCHAR2` (extended) | 16,315 bytes |
| `NCHAR`                | 966 bytes    |
| `RAW` (extended)       | 32,699 bytes |

**Note:**

TDE tablespace encryption does not have these data type restrictions.

**Related Topics**

- Restrictions on Using Transparent Data Encryption Tablespace Encryption
- [Oracle Database SecureFiles and Large Objects Developer's Guide](../adlob/using-oracle-LOBs-storage.md)

**Parent topic:** Encrypting Columns in Tables

#### 4.5.3 Restrictions on Using TDE Column Encryption

TDE column encryption is performed at the SQL layer. Oracle Database utilities that bypass the SQL layer cannot use TDE column encryption services.

Do not use TDE column encryption with the following database features:

- Index types other than B-tree

- Range scan search through an index

- Synchronous change data capture

- Transportable tablespaces

- Columns that have been created as identity columns

In addition, you cannot use TDE column encryption to encrypt columns used in foreign key constraints.

Applications that must use these unsupported features can use the `DBMS_CRYPTO` PL/SQL package for their encryption needs.

Transparent Data Encryption protects data stored on a disk or other media. It does not protect data in transit. Use the network encryption solutions discussed in [Oracle Database Security Guide](../dbseg/stong-authentication-administration-tools.md) to encrypt data over the network.

**Related Topics**

- [How Transparent Data Encryption Works with Export and Import Operations](using-transparent-data-encryption-with-other-oracle-features.md)
- Data Types That Can Be Encrypted with TDE Column Encryption

**Parent topic:** Encrypting Columns in Tables

#### 4.5.4 Creating Tables with Encrypted Columns

Oracle Database provides a selection of different algorithms that you can use to define the encryption used in encrypted columns.

- About Creating Tables with Encrypted Columns
  You can use the `CREATE TABLE` SQL statement to create a table with an encrypted column.
- Creating a Table with an Encrypted Column Using the Default Algorithm
  By default, TDE uses the `AES` encryption algorithm with a 192-bit key length (`AES192`).
- Creating a Table with an Encrypted Column Using No Algorithm or a Non-Default Algorithm
  You an use the `CREATE TABLE` SQL statement to create a table with an encrypted column.
- Using the NOMAC Parameter to Save Disk Space and Improve Performance
  You can bypass checks that TDE performs. This can save up to 20 bytes of disk space per encrypted value.
- Example: Using the NOMAC Parameter in a CREATE TABLE Statement
  You can use the CREATE TABLE SQL statement to encrypt a table column using the NOMAC parameter.
- Example: Changing the Integrity Algorithm for a Table
  You can use the ALTER TABLE SQL statement in different foregrounds to convert different offline tablespaces in parallel.
- Creating an Encrypted Column in an External Table
  The external table feature enables you to access data in external sources as if the data were in a database table.

**Parent topic:** Encrypting Columns in Tables

##### 4.5.4.1 About Creating Tables with Encrypted Columns

You can use the `CREATE TABLE` SQL statement to create a table with an encrypted column.

To create relational tables with encrypted columns, you can specify the SQL `ENCRYPT` clause when you define database columns with the `CREATE TABLE` SQL statement.

**Parent topic:** Creating Tables with Encrypted Columns

##### 4.5.4.2 Creating a Table with an Encrypted Column Using the Default Algorithm

By default, TDE uses the `AES` encryption algorithm with a 192-bit key length (`AES192`).

If you encrypt a table column without specifying an algorithm, then the column is encrypted using the `AES192` algorithm.

TDE adds [salt](glossary.md) to plaintext before encrypting it. Adding salt makes it harder for attackers to steal data through a brute force attack. TDE also adds a Message Authentication Code (MAC) to the data for integrity checking. The `SHA-1` integrity algorithm is used by default.

- To create a table that encrypts a column, use the `CREATE TABLE` SQL statement with the `ENCRYPT` clause.

  For example, to encrypt a table column using the default algorithm:

      CREATE TABLE employee (
           first_name VARCHAR2(128),
           last_name VARCHAR2(128),
           empID NUMBER,
           salary NUMBER(6) ENCRYPT);

  This example creates a new table with an encrypted column (`salary`). The column is encrypted using the default encryption algorithm (`AES192`). Salt and MAC are added by default. This example assumes that the keystore is open and a master encryption key is set.

**Note:**

If there are multiple encrypted columns in a table, then all of these columns must use the same pair of encryption and integrity algorithms.

Salt is specified at the column level. This means that an encrypted column in a table can choose not to use salt irrespective of whether or not other encrypted columns in the table use salt.

**Parent topic:** Creating Tables with Encrypted Columns

##### 4.5.4.3 Creating a Table with an Encrypted Column Using No Algorithm or a Non-Default Algorithm

You an use the `CREATE TABLE` SQL statement to create a table with an encrypted column.

By default, TDE adds [salt](glossary.md) to plaintext before encrypting it. Adding salt makes it harder for attackers to steal data through a brute force attack. However, if you plan to index the encrypted column, then you must use the `NO SALT` parameter.

- To create a table that uses an encrypted column that is a non-default algorithm or no algorithm, run the `CREATE TABLE` SQL statement as follows:

  - If you do not want to use any algorithm, then include the `ENCRYPT NO SALT` clause.

  - If you want to use a non-default algorithm, then use the `ENCRYPT USING` clause, followed by one of the following algorithms enclosed in single quotation marks:

    - `3DES168`

    - `AES128`

    - `AES192` (default)

    - `AES256`

The following example shows how to specify encryption settings for the `empID` and `salary` columns.

    CREATE TABLE employee (
         first_name VARCHAR2(128),
         last_name VARCHAR2(128),
         empID NUMBER ENCRYPT NO SALT,
         salary NUMBER(6) ENCRYPT USING '3DES168');

In this example:

- The `empID` column is encrypted and does not use salt. Both the `empID` and `salary` columns will use the `3DES168` encryption algorithm, because all of the encrypted columns in a table must use the same encryption algorithm.

- The `salary` column is encrypted using the `3DES168` encryption algorithm. Note that the string that specifies the algorithm must be enclosed in single quotation marks (' '). The `salary` column uses salt by default.

**Parent topic:** Creating Tables with Encrypted Columns

##### 4.5.4.4 Using the NOMAC Parameter to Save Disk Space and Improve Performance

You can bypass checks that TDE performs. This can save up to 20 bytes of disk space per encrypted value.

If the number of rows and encrypted columns in the table is large, then bypassing TDE checks can add up to a significant amount of disk space. In addition, this saves processing cycles and reduces the performance overhead associated with TDE.

TDE uses the `SHA-1` integrity algorithm by default. All of the encrypted columns in a table must use the same integrity algorithm. If you already have a table column using the `SHA-1` algorithm, then you cannot use the `NOMAC` parameter to encrypt another column in the same table.

- To bypass the integrity check during encryption and decryption operations, use the `NOMAC` parameter in the `CREATE TABLE` and `ALTER TABLE` statements.

**Related Topics**

- [Performance and Storage Overhead of Transparent Data Encryption](general-considerations-of-using-transparent-data-encryption.md)

**Parent topic:** Creating Tables with Encrypted Columns

##### 4.5.4.5 Example: Using the NOMAC Parameter in a CREATE TABLE Statement

You can use the CREATE TABLE SQL statement to encrypt a table column using the NOMAC parameter.

Example 4-1 creates a table with an encrypted column. The `empID` column is encrypted using the `NOMAC` parameter.

Example 4-1 Using the NOMAC parameter in a CREATE TABLE statement

    CREATE TABLE employee (
         first_name VARCHAR2(128),
         last_name VARCHAR2(128),
         empID NUMBER ENCRYPT 'NOMAC' ,
         salary NUMBER(6));

**Parent topic:** Creating Tables with Encrypted Columns

##### 4.5.4.6 Example: Changing the Integrity Algorithm for a Table

You can use the ALTER TABLE SQL statement in different foregrounds to convert different offline tablespaces in parallel.

Example 4-2 shows how to change the integrity algorithm for encrypted columns in a table. The encryption algorithm is set to `3DES168` and the integrity algorithm is set to `SHA-1`. The second `ALTER TABLE` statement sets the integrity algorithm to `NOMAC`.

Example 4-2 Changing the Integrity Algorithm for a Table

    ALTER TABLE EMPLOYEE REKEY USING '3DES168' 'SHA-1';

    ALTER TABLE EMPLOYEE REKEY USING '3DES168' 'NOMAC';

**Parent topic:** Creating Tables with Encrypted Columns

##### 4.5.4.7 Creating an Encrypted Column in an External Table

The external table feature enables you to access data in external sources as if the data were in a database table.

External tables can be updated using the `ORACLE_DATAPUMP` access driver.

- To encrypt specific columns in an external table, use the `ENCRYPT` clause when you define those columns:

  A system-generated key encrypts the columns. For example, the following `CREATE TABLE` SQL statement encrypts the `ssn` column using the `3DES168` algorithm:

      CREATE TABLE emp_ext (
          first_name,
          ....
          ssn ENCRYPT USING '3DES168',
          ....

If you plan to move an external table to a new location, then you cannot use a randomly generated key to encrypt the columns. This is because the randomly generated key will not be available at the new location.

For such scenarios, you should specify a password while you encrypt the columns. After you move the data, you can use the same password to regenerate the key required to access the encrypted column data at the new location.

Table partition exchange also requires a password-protected [TDE table key](glossary.md).

Example 4-3 creates an external table using a password to create the [TDE table key](glossary.md).

Example 4-3 Creating a New External Table with a Password-Generated TDE Table Key

    CREATE TABLE emp_ext (
         first_name,
         last_name,
         empID,
         salary,
         ssn ENCRYPT IDENTIFIED BY password
    )  ORGANIZATION EXTERNAL
       (
        TYPE ORACLE_DATAPUMP
        DEFAULT DIRECTORY "D_DIR"
        LOCATION('emp_ext.dat')
        )
        REJECT LIMIT UNLIMITED
    AS SELECT * FROM EMPLOYEE;

**Parent topic:** Creating Tables with Encrypted Columns

#### 4.5.5 Encrypting Columns in Existing Tables

You can encrypt columns in existing tables. As with new tables, you have a choice of different algorithms to use to definite the encryption.

- About Encrypting Columns in Existing Tables
  The `ALTER TABLE` SQL statement enables you to encrypt columns in an existing table.
- Adding an Encrypted Column to an Existing Table
  You can encrypt columns in existing tables, use a different algorithm, and use `NO SALT` to index the column.
- Encrypting an Unencrypted Column
  You can use the `ALTER TABLE MODIFY` statement to encrypt an existing unencrypted column.
- Disabling Encryption on a Column
  You may want to disable encryption for reasons of compatibility or performance.

**Parent topic:** Encrypting Columns in Tables

##### 4.5.5.1 About Encrypting Columns in Existing Tables

The `ALTER TABLE` SQL statement enables you to encrypt columns in an existing table.

To add an encrypted column to an existing table, or to encrypt or decrypt an existing column, you use the `ALTER TABLE` SQL statement with the `ADD` or `MODIFY` clause.

**Parent topic:** Encrypting Columns in Existing Tables

##### 4.5.5.2 Adding an Encrypted Column to an Existing Table

You can encrypt columns in existing tables, use a different algorithm, and use `NO SALT` to index the column.

- To add an encrypted column to an existing table, use the `ALTER TABLE ADD` statement, specifying the new column with the `ENCRYPT` clause.

Example 4-4 adds an encrypted column, `ssn`, to an existing table, called `employee`. The `ssn` column is encrypted with the default `AES192` algorithm. Salt and MAC are added by default.

Example 4-4 Adding an Encrypted Column to an Existing Table

    ALTER TABLE employee ADD (ssn VARCHAR2(11) ENCRYPT);

**Parent topic:** Encrypting Columns in Existing Tables

##### 4.5.5.3 Encrypting an Unencrypted Column

You can use the `ALTER TABLE MODIFY` statement to encrypt an existing unencrypted column.

- To encrypt an existing unencrypted column, use the `ALTER TABLE MODIFY` statement, specifying the unencrypted column with the `ENCRYPT` clause.

The following example encrypts the `first_name` column in the `employee` table. The `first_name` column is encrypted with the default `AES192` algorithm. Salt is added to the data, by default. You can encrypt the column using a different algorithm. If you want to index a column, then you must specify `NO SALT`. You can also bypass integrity checks by using the `NOMAC` parameter.

    ALTER TABLE employee MODIFY (first_name ENCRYPT);

The following example encrypts the `first_name` column in the employee table using the `NOMAC` parameter.

    ALTER TABLE employee MODIFY (first_name ENCRYPT 'NOMAC');

**Parent topic:** Encrypting Columns in Existing Tables

##### 4.5.5.4 Disabling Encryption on a Column

You may want to disable encryption for reasons of compatibility or performance.

- To disable column encryption, use the `ALTER TABLE MODIFY` command with the `DECRYPT` clause.

Example 4-5 decrypts the `first_name` column in the `employee` table.

Example 4-5 Turning Off Column Encryption

    ALTER TABLE employee MODIFY (first_name DECRYPT);

**Parent topic:** Encrypting Columns in Existing Tables

#### 4.5.6 Creating an Index on an Encrypted Column

You can create an index on an encrypted column.

The column being indexed must be encrypted without [salt](glossary.md). If the column is encrypted with salt, then the `ORA-28338: cannot encrypt indexed column(s) with salt` error is raised.

- To create an index on an encrypted column, use the `CREATE INDEX` statement with the `ENCRYPT NO SALT` clause.

Example 4-6 shows how to create an index on a column that has been encrypted without salt.

Example 4-6 Creating Index on a Column Encrypted Without Salt

    CREATE TABLE employee (
       first_name VARCHAR2(128),
       last_name VARCHAR2(128),
       empID NUMBER ENCRYPT NO SALT,
       salary NUMBER(6) ENCRYPT USING '3DES168');

    CREATE INDEX employee_idx on employee (empID);

**Parent topic:** Encrypting Columns in Tables

#### 4.5.7 Adding Salt to an Encrypted Column

Salt, which is a random string added to data before encryption, is a way to strengthen the security of encrypted data. .

Salt ensures that the same plaintext data does not always translate to the same encrypted text. Salt removes the one common method that intruders use to steal data, namely, matching patterns of encrypted text. Adding [salt](glossary.md) requires an additional 16 bytes of storage per encrypted data value.

- To add or remove salt from encrypted columns, use the `ALTER TABLE MODIFY` SQL statement.

For example, suppose you want to encrypt the `first_name` column using salt. If the `first_name` column was encrypted without salt earlier, then the `ALTER TABLE MODIFY` statement reencrypts it using salt.

    ALTER TABLE employee MODIFY (first_name ENCRYPT SALT);

**Parent topic:** Encrypting Columns in Tables

#### 4.5.8 Removing Salt from an Encrypted Column

You can use the ALTER TABLE SQL statement to remove salt from an encrypted column.

- To remove salt from an encrypted column, use the `ENCRYPT NO SALT` clause in the ALTER TABLE SQL statement.

For example, suppose you wanted to remove salt from the `first_name` column. If you must index a column that was encrypted using salt, then you can use this statement to remove the salt before indexing

    ALTER TABLE employee MODIFY (first_name ENCRYPT NO SALT);

**Parent topic:** Encrypting Columns in Tables

#### 4.5.9 Changing the Encryption Key or Algorithm for Tables with Encrypted Columns

You can use the `ALTER TABLE` SQL statement to change the encryption key or algorithm used in encrypted columns.

Each table can have only one [TDE table key](glossary.md) for its columns. You can regenerate the TDE table key with the `ALTER TABLE` statement. This process generates a new key, decrypts the data in the table using the previous key, reencrypts the data using the new key, and then updates the table metadata with the new key information. You can also use a different encryption algorithm for the new TDE table key.

- To change the encryption key or algorithm for tables that contain encrypted columns, use the `ALTER TABLE` SQL statement with the `REKEY` or `REKEY USING` clause.

For example:

    ALTER TABLE employee REKEY;

Example 4-7 regenerates the TDE table key for the `employee` table by using the `3DES168` algorithm.

Example 4-7 Changing an Encrypted Table Column Encryption Key and Algorithm

    ALTER TABLE employee REKEY USING '3DES168';

**Parent topic:** Encrypting Columns in Tables

### 4.6 Encryption Conversions for Tablespaces and Databases

You can perform encryption operations on both offline and online tablespaces and databases.

- About Encryption Conversion for Tablespaces and Databases
  The `CREATE TABLESPACE` SQL statement can be used to encrypt new tablespaces. `ALTER TABLESPACE` can encrypt existing tablespaces.
- Impact of a Closed TDE Keystore on Encrypted Tablespaces
  A TDE keystore can be closed or migrated when an Oracle-managed tablespace is encrypted, and the database system itself must be shut down to disallow operations on an Oracle-managed tablespace.
- Restrictions on Using Transparent Data Encryption Tablespace Encryption
  You should be aware of restrictions on using Transparent Data Encryption when you encrypt a tablespace.
- Creating an Encrypted New Tablespace
  When you create a new tablespace, you can configure its encryption settings during the creation process.
- Setting the Tablespace Encryption Default Algorithm
  The `TABLESPACE_ENCRYPTION_DEFAULT_ALGORITHM` applies to specific encryption scenarios.
- Encrypting Future Tablespaces
  You can configure Oracle Database to automatically encrypt future tablespaces that you will create.
- Encrypted Sensitive Credential Data in the Data Dictionary
  You can encrypt sensitive credential data in the `SYS.LINK$` and `SYS.SCHEDULER$_CREDENTIAL` system tables.
- Encryption Conversions for Existing Offline Tablespaces
  You can perform offline encryption conversions by using the `ALTER TABLESPACE` SQL statement `OFFLINE`, `ENCRYPT`, and `DECRYPT` clauses.
- Encryption Conversions for Existing Online Tablespaces
  You can encrypt and decrypt an online existing tablespace by using the `ALTER TABLESPACE` SQL statement with the `ONLINE` and `ENCRYPT` or `DECRYPT` clauses.
- Encryption Conversions for Existing Databases
  You can encrypt both offline and online databases.

**Parent topic:** Configuring Transparent Data Encryption

#### 4.6.1 About Encryption Conversion for Tablespaces and Databases

The `CREATE TABLESPACE` SQL statement can be used to encrypt new tablespaces. `ALTER TABLESPACE` can encrypt existing tablespaces.

In addition to encrypting new and existing tablespaces, you can encrypt full databases, which entails the encryption of the [Oracle-managed tablespace](glossary.md)s (in this release, the `SYSTEM`, `SYSAUX`, `TEMP`, and `UNDO` tablespaces). To encrypt a full database, you use the `ALTER TABLESPACE` statement, not `ALTER DATABASE`, to encrypt the Oracle-managed tablespaces.

The following table compares the differences between an offline and an online encryption conversion of tablespaces and databases.

Table 4-2 Offline and Online Tablespace and Database Encryption Conversions

| Functionality                                                                | Offline Conversion                                                                                                                                                                                                                  | Online Conversion                                                                                                                                                                                                                 |
|:-----------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Release with minimum conversion capability                                   | Oracle Database 11g release 2 (11.2)                                                                                                                                                                                                | Oracle Database 12c release 2 (12.2) and later                                                                                                                                                                                    |
| What can be backported?                                                      | The ability to encrypt or decrypt a data file with the `AES128` algorithm (using `ALTER DATABASE DATAFILE ``data_file`` ENCRYPT` or `DECRYPT`) can be used in Oracle Database releases 12.1.0.2 and 11.2.0.4.                       | No                                                                                                                                                                                                                                |
| Algorithms supported                                                         | All symmetric encryption algorithms that TDE supports. See [Supported Encryption and Integrity Algorithms](introduction-to-transparent-data-encryption.md). See also About Encryption Conversions for Existing Offline Tablespaces. | All symmetric encryption algorithm that TDE supports. See [Supported Encryption and Integrity Algorithms](introduction-to-transparent-data-encryption.md). See also About Encryption Conversions for Existing Online Tablespaces. |
| When can the conversion be run?                                              | When the tablespace is offline or the database is in the mount stage.                                                                                                                                                               | When the tablespace is online and database is open in read/write mode.                                                                                                                                                            |
| Is auxiliary space required for the conversion?                              | No                                                                                                                                                                                                                                  | Yes. See Encrypting an Existing Tablespace with Online Conversion for guidelines.                                                                                                                                                 |
| Oracle Data Guard conversion guidelines                                      | Convert both the primary and standby manually. Convert the standby first and then switch over to minimum downtime                                                                                                                   | After you convert the primary, the standby conversion takes place automatically. You cannot perform an online conversion directly on the standby.                                                                                 |
| Encrypt the `SYSTEM`, `SYSAUX`, and `UNDO` tablespaces (database conversion) | Oracle Database 12c release 2 (12.2) and later only. You must set `COMPATIBILITY` to `12.2.0.0`. Only auto-login keystores are supported.                                                                                           | Oracle Database 12c release 2 (12.2) and later only. You must set `COMPATIBILITY` to `12.2.0.0`.                                                                                                                                  |
| Can an existing `TEMP` tablespace be converted?                              | No, but you can create an encrypted `TEMP` tablespace in Oracle Database 12c release 2 (12.2) and later, make it the default temporary tablespace, and then drop the original `TEMP` tablespace.                                    | No, but you can create an encrypted `TEMP` tablespace in Oracle Database 12c release 2 (12.2) and later, make it the default temporary tablespace, and then drop the original `TEMP` tablespace.                                  |
| Can an existing tablespace be decrypted?                                     | You only can decrypt a tablespace or data file that was previously encrypted by an offline encrypt operation. Oracle does not recommend that you decrypt the `UNDO` tablespace once it is encrypted.                                | Yes, but Oracle does not recommend that you decrypt the `UNDO` tablespace once it is encrypted.                                                                                                                                   |
| Can encryption keys be rekeyed?                                              | No, but after the tablespace is encrypted, you can then use online conversion to rekey in Oracle Database 12c release 2 (12.2) compatibility.                                                                                       | Yes                                                                                                                                                                                                                               |
| Can encryption operations be run in parallel?                                | You can run parallel encryption conversions at the data file level with multiple user sessions running.                                                                                                                             | You can run parallel encryption conversions at the tablespace level with multiple user sessions running.                                                                                                                          |
| What to do if an encryption conversion SQL statement fails to complete?      | Re-issue the encryption or decryption SQL statement to ensure that all the data files within the tablespace are consistently either encrypted or decrypted.                                                                         | Rerun the SQL statement but use the `FINISH` clause.                                                                                                                                                                              |

**Parent topic:** Encryption Conversions for Tablespaces and Databases

#### 4.6.2 Impact of a Closed TDE Keystore on Encrypted Tablespaces

A TDE keystore can be closed or migrated when an Oracle-managed tablespace is encrypted, and the database system itself must be shut down to disallow operations on an Oracle-managed tablespace.

A closed TDE keystore has no impact on operations that involve an encrypted [Oracle-managed tablespace](glossary.md) (in this release, the `SYSTEM`, `SYSAUX`, `TEMP`, and `UNDO` tablespaces). This enables operations that are performed by background processes (for example, the log writer) to continue to work on these tablespaces while the TDE keystore is closed. If you want to disallow operations on an encrypted Oracle-managed tablespace, then you must shut down the database.

With regard to user-created tablespaces, a closed TDE keystore causes operations such as rotating a key or decrypting the tablespace to fail with an `ORA-28365 wallet is not open` error, just as it did in earlier releases. If you want to disallow operations on the user-created tablespace, then close the TDE keystore (or shut down the database).

User-created data can be copied into an encrypted Oracle-managed tablespace (for example, by an internal process such as `DBMS_STATS` statistics gathering) from a user-created tablespace while the TDE keystore is open. Closing the keystore does not prevent a user from viewing this data afterward, when the TDE keystore is in the `CLOSED` state at the time that you query the `V$ENCRYPTION_WALLET` view. Access to the original data by attempting to query an encrypted user-created tablespace will fail, resulting in an `ORA-28365 wallet is not open` error.

Table 4-3 describes the operations that are necessary to disallow or allow operations on encrypted data in user-created tablespaces and Oracle-managed tablespaces. For example, in the first scenario, both the user-created tablespaces and the Oracle-managed tablespaces are encrypted. In this case, for the encrypted data in the encrypted user-created tablespace, an administrator can close or open keystores, and shut down and open a database with an encrypted user-created tablespace. When an encrypted Oracle-managed tablespace is configured, the administrator can disallow operations by shutting down the database, and can allow operations by starting up in mount mode, opening the TDE keystore, and then opening the database. (It is necessary to open the TDE keystore before opening the database because the system may need the TDE master encryption key to decrypt the bootstrap dictionary tables, which are located in the encrypted Oracle-managed tablespace.) The N/A flags in this table refer to non-encrypted data, which you can always operate on, unless the instance is shut down.

Table 4-3 Necessary Commands to Disallow or Allow Operations on Encrypted Data

| Tablespace Encryption Scenarios                                    | Commands to Disallow Operations on Encrypted User-Created Tablespace Data                    | Commands to Disallow Operations on Encrypted Oracle-Managed Tablespace Data | Commands to Allow Operations on Encrypted User-Created Tablespace Data                                                       | Commands to Allow Operations on Encrypted Oracle-Managed Tablespace Data                                                     |
|:-------------------------------------------------------------------|:---------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------|
| Both user-created and Oracle-managed tablespaces encrypted         | • `ADMINISTER KEY MANAGEMENT SET KEYSTORE CLOSE IDENTIFIED BY ``password``;`<br>• `SHUTDOWN` | `SHUTDOWN`                                                                  | • `STARTUP MOUNT;`<br>• `ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN IDENTIFIED BY ``password``;`<br>• `ALTER DATABASE OPEN` | • `STARTUP MOUNT;`<br>• `ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN IDENTIFIED BY ``password``;`<br>• `ALTER DATABASE OPEN` |
| User tablespace encrypted; Oracle-managed tablespace not encrypted | • `ADMINISTER KEY MANAGEMENT SET KEYSTORE CLOSE IDENTIFIED BY ``password``;`<br>• `SHUTDOWN` | N/A                                                                         | • `STARTUP MOUNT;`<br>• `ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN IDENTIFIED BY ``password``;`<br>• `ALTER DATABASE OPEN` | N/A                                                                                                                          |
| User tablespace not encrypted; Oracle-managed tablespace encrypted | N/A                                                                                          | `SHUTDOWN`                                                                  | N/A                                                                                                                          | • `STARTUP MOUNT;`<br>• `ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN IDENTIFIED BY ``password``;`<br>• `ALTER DATABASE OPEN` |
| Neither user nor Oracle-managed tablespaces encrypted              | N/A                                                                                          | N/A                                                                         | N/A                                                                                                                          | N/A                                                                                                                          |

**Parent topic:** Encryption Conversions for Tablespaces and Databases

#### 4.6.3 Restrictions on Using Transparent Data Encryption Tablespace Encryption

You should be aware of restrictions on using Transparent Data Encryption when you encrypt a tablespace.

Note the following restrictions:

- Transparent Data Encryption (TDE) tablespace encryption encrypts or decrypts data during read and write operations, as opposed to TDE column encryption, which encrypts and decrypts data at the SQL layer. This means that most restrictions that apply to TDE column encryption, such as data type restrictions and index type restrictions, do not apply to TDE tablespace encryption.

- To perform import and export operations, use Oracle Data Pump.

**Related Topics**

- Encrypting an Unencrypted Column
- Data Types That Can Be Encrypted with TDE Column Encryption
- [Oracle Database Utilities](../sutil/oracle-data-pump-overview.md)

**Parent topic:** Encryption Conversions for Tablespaces and Databases

#### 4.6.4 Creating an Encrypted New Tablespace

When you create a new tablespace, you can configure its encryption settings during the creation process.

- Step 1: Set the COMPATIBLE Initialization Parameter for Tablespace Encryption
  You must set the `COMPATIBLE` initialization parameter before creating an encrypted tablespace.
- Step 2: Set the Tablespace TDE Master Encryption Key
  You should ensure that you have configured the TDE master encryption key.
- Step 3: Create the Encrypted Tablespace
  After you have set the `COMPATIBLE` initialization parameter, you are ready to create the encrypted tablespace.

**Parent topic:** Encryption Conversions for Tablespaces and Databases

##### 4.6.4.1 Step 1: Set the COMPATIBLE Initialization Parameter for Tablespace Encryption

You must set the `COMPATIBLE` initialization parameter before creating an encrypted tablespace.

- About Setting the COMPATIBLE Initialization Parameter for Tablespace Encryption
  A minimum `COMPATIBLE` initialization parameter setting of `11.2.0.0` enables the full set of tablespace encryption features.
- Setting the COMPATIBLE Initialization Parameter for Tablespace Encryption
  To set the `COMPATIBLE` initialization parameter, you must edit the initialization parameter file for the database instance.

**Parent topic:** Creating an Encrypted New Tablespace

###### 4.6.4.1.1 About Setting the COMPATIBLE Initialization Parameter for Tablespace Encryption

A minimum `COMPATIBLE` initialization parameter setting of `11.2.0.0` enables the full set of tablespace encryption features.

Setting the compatibility to `11.2.0.0` enables the following functionality:

- The `11.2.0.0` setting enables the database to use any of the four supported algorithms for data encryption (`3DES168`, `AES128`, `AES192`, and `AES256`).

- The `11.2.0.0` setting enables the migration of a key from a TDE wallet to an external keystore (ensure that the TDE master encryption key was configured for the external keystore)

- The `11.2.0.0` setting enables rekeying the TDE master encryption key

Be aware that once you set the `COMPATIBLE` parameter to `11.2.0.0`, the change is irreversible. To use tablespace encryption, ensure that the compatibility setting is at the minimum, which is `11.2.0.0`.

**Related Topics**

- [Oracle Database SQL Language Reference](../refrn/COMPATIBLE.md)
- [Oracle Database Administrator’s Guide](../admin/creating-and-configuring-an-oracle-database.md)

**Parent topic:** Step 1: Set the COMPATIBLE Initialization Parameter for Tablespace Encryption

###### 4.6.4.1.2 Setting the COMPATIBLE Initialization Parameter for Tablespace Encryption

To set the `COMPATIBLE` initialization parameter, you must edit the initialization parameter file for the database instance.

1.  Log in to the database instance.

2.  Check the current setting of the `COMPATIBLE` parameter.

    For example:

        SHOW PARAMETER COMPATIBLE

        NAME                                 TYPE        VALUE
        ------------------------------------ ----------- ------------------------------
        compatible                           string      11.2.0.0
        noncdbcompatible                     BOOLEAN     FALSE

3.  If you must change the `COMPATIBLE` parameter, then complete the remaining steps in this procedure.

    The value should be 12.2.0.0 or later.

4.  From the command line, locate the initialization parameter file for the database instance.

    - UNIX systems: This file is in the `ORACLE_HOME``/dbs` directory and is named `init``ORACLE_SID``.ora` (for example, `initmydb.ora`).

    - Windows systems: This file is in the `ORACLE_HOME``\database` directory and is named `init``ORACLE_SID``.ora` (for example, `initmydb.ora`).

5.  Edit the initialization parameter file to use the new `COMPATIBLE` setting.

    For example:

        COMPATIBLE=12.2.0.0

6.  In SQL\*Plus, connect as a user who has the `SYSDBA` administrative privilege, and then restart the database.

    For example:

        CONNECT /AS SYSDBA
        SHUTDOWN
        STARTUP

    If tablespace encryption is in use, then open the keystore at the database mount. The keystore must be open before you can access data in an encrypted tablespace.

    For example:

        STARTUP MOUNT;
        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN IDENTIFIED BY keystore_password;
        ALTER DATABASE OPEN;

**Parent topic:** Step 1: Set the COMPATIBLE Initialization Parameter for Tablespace Encryption

##### 4.6.4.2 Step 2: Set the Tablespace TDE Master Encryption Key

You should ensure that you have configured the TDE master encryption key.

- Set the TDE master encryption key as follows:

  - For software TDE master encryption keys, see Step 4: Set the TDE Master Encryption Key in the TDE Wallet.

  - For hardware TDE master encryption keys, see [Step 3: Set the TDE Master Encryption Key in Oracle Key Vault](managing-keystores-encryption-keys-in-united-mode.md).

**Parent topic:** Creating an Encrypted New Tablespace

##### 4.6.4.3 Step 3: Create the Encrypted Tablespace

After you have set the `COMPATIBLE` initialization parameter, you are ready to create the encrypted tablespace.

- About Creating Encrypted Tablespaces
  To create an encrypted tablespace, you can use the `CREATE TABLESPACE` SQL statement.
- Creating an Encrypted Tablespace
  To create an encrypted tablespace, you must use the `CREATE TABLESPACE` statement with the `ENCRYPTION USING` clause.
- Example: Creating an Encrypted Tablespace That Uses AES192
  You can use the `CREATE TABLESPACE` SQL statement to create an encrypted tablespace.
- Example: Creating an Encrypted Tablespace That Uses the Default Algorithm
  You can use the `CREATE TABLESPACE` SQL statement to create an encrypted tablespace that uses the default algorithm.

**Parent topic:** Creating an Encrypted New Tablespace

###### 4.6.4.3.1 About Creating Encrypted Tablespaces

To create an encrypted tablespace, you can use the `CREATE TABLESPACE` SQL statement.

You must have the `CREATE TABLESPACE` system privilege to create an encrypted tablespace.

You can import data into an encrypted tablespace by using Oracle Data Pump. You can also use a SQL statement such as `CREATE TABLE...AS SELECT...` or `ALTER TABLE...MOVE...` to move data into an encrypted tablespace. The `CREATE TABLE...AS SELECT...` statement creates a table from an existing table. The `ALTER TABLE...MOVE...` statement moves a table into the encrypted tablespace.

For security reasons, you cannot encrypt a tablespace with the `NO SALT` option.

You can query the `ENCRYPTED` column of the `DBA_TABLESPACES` and `USER_TABLESPACES` data dictionary views to verify if a tablespace was encrypted.

**See Also:**

Oracle Database Reference for more information about the [`DBA_TABLESPACES`](../refrn/DBA_TABLESPACES.md) and [`USER_TABLESPACES`](../refrn/USER_TABLESPACES.md) data dictionary views

**Parent topic:** Step 3: Create the Encrypted Tablespace

###### 4.6.4.3.2 Creating an Encrypted Tablespace

To create an encrypted tablespace, you must use the `CREATE TABLESPACE` statement with the `ENCRYPTION USING` clause.

- Run the `CREATE TABLESPACE` statement, using its encryption clauses.
  For example:

      CREATE TABLESPACE encrypt_ts
        DATAFILE '$ORACLE_HOME/dbs/encrypt_df.dbf' SIZE 1M
        ENCRYPTION USING 'AES256' ENCRYPT;

  In this specification:

  - `ENCRYPTION USING 'AES256' ENCRYPT` specifies the encryption algorithm and the key length for the encryption. The `ENCRYPT` clause encrypts the tablespace. Enclose this setting in single quotation marks (`' '`). The key lengths are included in the names of the algorithms. If you do not specify an encryption algorithm, then the default encryption algorithm, `AES128`, is used.

**Related Topics**

- [Supported Encryption and Integrity Algorithms](introduction-to-transparent-data-encryption.md)

**Parent topic:** Step 3: Create the Encrypted Tablespace

###### 4.6.4.3.3 Example: Creating an Encrypted Tablespace That Uses AES192

You can use the `CREATE TABLESPACE` SQL statement to create an encrypted tablespace.

Example 4-8 creates a tablespace called `securespace_1` that is encrypted using the `AES192` algorithm.

Example 4-8 Creating an Encrypted Tablespace That Uses AES192

    CREATE TABLESPACE securespace_1
    DATAFILE '/home/user/oradata/secure01.dbf'
    SIZE 150M
    ENCRYPTION USING 'AES192' ENCRYPT;

**Parent topic:** Step 3: Create the Encrypted Tablespace

###### 4.6.4.3.4 Example: Creating an Encrypted Tablespace That Uses the Default Algorithm

You can use the `CREATE TABLESPACE` SQL statement to create an encrypted tablespace that uses the default algorithm.

Example 4-9 creates a tablespace called `securespace_2`. Because no encryption algorithm is specified, the default encryption algorithm (`AES128`) is used. The key length is 128 bits.

Example 4-9 Creating an Encrypted Tablespace That Uses the Default Algorithm

    CREATE TABLESPACE securespace_2
    DATAFILE '/home/user/oradata/secure01.dbf'
    SIZE 150M
    ENCRYPTION ENCRYPT;

**Parent topic:** Step 3: Create the Encrypted Tablespace

#### 4.6.5 Setting the Tablespace Encryption Default Algorithm

The `TABLESPACE_ENCRYPTION_DEFAULT_ALGORITHM` applies to specific encryption scenarios.

These scenarios are as follows:

- Encryption commands that do not allow to specify the encryption algorithm
- New tablespaces that are created without the encryption syntax
- The encryption algorithm for the `SYSTEM` tablespace

`_TABLESPACE_ENCRYPTION_DEFAULT_ALGORITHM` only becomes effective if it is set before the first `SET KEY` operation with Oracle Key Vault, or the `CREATE KEYSTORE` command for software keystore-based TDE configuration.

`_TABLESPACE_ENCRYPTION_DEFAULT_ALGORITHM` applies to both offline and online tablespace encryption operations. It also applies to future encrypted tablespaces, if `TABLESPACE_ENCRYPTION` has been set appropriately.

- Enter the following `ALTER SYSTEM` statement:
      ALTER SYSTEM SET "_TABLESPACE_ENCRYPTION_DEFAULT_ALGORITHM" = value SCOPE=BOTH;

  In this specification, `value` can be one of the following encryption algorithms: `AES128`, `AES192`, `AES256`, `3DES168`, `ARIA128`, `ARIA192`, or `ARIA256`. The default encryption algorithm is `AES128`.
- You can also add the following statement to the `dbca create database` or `dbaascli create database` command:
      -initparams "_TABLESPACE_ENCRYPTION_DEFAULT_ALGORITHM" = AES256

**Parent topic:** Encryption Conversions for Tablespaces and Databases

#### 4.6.6 Encrypting Future Tablespaces

You can configure Oracle Database to automatically encrypt future tablespaces that you will create.

- About Encrypting Future Tablespaces
  The `ENCRYPT_NEW_TABLESPACES` dynamic database initialization parameter controls if future tablespaces are encrypted.
- Setting Future Tablespaces to be Encrypted
  You can set the `ENCRYPT_NEW_TABLESPACES` database initialization parameter to automatically encrypt future tablespaces that you create.

**Parent topic:** Encryption Conversions for Tablespaces and Databases

##### 4.6.6.1 About Encrypting Future Tablespaces

The `ENCRYPT_NEW_TABLESPACES` dynamic database initialization parameter controls if future tablespaces are encrypted.

By default, all Oracle Cloud databases are encrypted. If you install an off-the-shelf application into such a database, its installation scripts most likely do not have the encryption syntax. In this case, because `ENCRYPT_NEW_TABLESPACES` is set to `CLOUD_ONLY`, those tablespaces would be created encrypted regardless.

In an Oracle Cloud environment, the following scenarios may occur when you create encrypted tablespaces in Oracle Cloud and on-premises environments:

- You create a database in Oracle Cloud; the tablespaces are encrypted because the `TABLESPACE_ENCRYPTION` parameter is set to `AUTO_ENABLE`. However, you may not have the intention or even an Advanced Security Option license to bring the encrypted database back on premises. For this use case, Oracle Recovery Manager (Oracle RMAN) provides the option to duplicate or restore `AS DECRYPTED`.

- You create a hybrid environment where the primary database is on premises and the standby database is on Oracle Cloud. If a switchover operation takes place, then the new primary is on Oracle Cloud. For example, suppose you do not have an Advanced Security Option (ASO) license, and you have an automatically encrypted tablespace in the Oracle Cloud. The standby database on premises is also automatically encrypted. In this case, you either need an Advanced Security license (which includes Transparent Data Encryption and Data Redaction) for the on-premises standby database, or you cannot use the standby database.

**Parent topic:** Encrypting Future Tablespaces

##### 4.6.6.2 Setting Future Tablespaces to be Encrypted

You can set the `ENCRYPT_NEW_TABLESPACES` database initialization parameter to automatically encrypt future tablespaces that you create.

**Note:**

Starting with Oracle Database 19.16, the `ENCRYPT_NEW_TABLESPACES` is deprecated.

- In SQL\*Plus, enter the following `ALTER SYSTEM` statement:
      ALTER SYSTEM SET ENCRYPT_NEW_TABLESPACES = value;

  In this specification, `value` can be:

  - `CLOUD_ONLY` transparently encrypts the tablespace in the Cloud using the tablespace encryption default algorithm if you do not specify the `ENCRYPTION` clause of the `CREATE TABLESPACE` SQL statement. In Oracle Cloud Infrastructure (OCI) databases, this value cannot be changed, to comply with Oracle's encryption mandate. If you create the tablespace on premises, then it will follow the `CREATE TABLESPACE` statement specification that you enter. For example, if you omit the `ENCRYPTION` clause, then the tablespace is created unencrypted. If you include this clause and use a different algorithm, then the tablespace will use that algorithm. `CLOUD_ONLY` is the default.

  - `AUTO_ENABLE` automatically encrypts the tablespace using the tablespace encryption default algorithm and cipher mode if you do not specify the `ENCRYPTION` clause of the `CREATE TABLESPACE` SQL statement, or to the algorithm specified by the `TABLESPACE_ENCRYPTION_DEFAULT_ALGORITHM` dynamic parameter.

  - `ALWAYS` automatically encrypts the tablespace using the tablespace encryption default algorithm if you omit the `ENCRYPTION` clause of `CREATE TABLESPACE`, for both the Cloud and premises scenarios.

    If you do provide the `ENCRYPTION` clause, however, the algorithm that you specify takes precedence over the tablespace encryption default algorithm.

  - `DDL` encrypts the tablespace using the specified setting of the `ENCRYPTION` clause of `CREATE TABLESPACE`, for both Oracle Cloud and on-premises environments.

**Related Topics**

- [ENCRYPT_NEW_TABLESPACES](../refrn/ENCRYPT_NEW_TABLESPACES.md)

**Parent topic:** Encrypting Future Tablespaces

#### 4.6.7 Encrypted Sensitive Credential Data in the Data Dictionary

You can encrypt sensitive credential data in the `SYS.LINK$` and `SYS.SCHEDULER$_CREDENTIAL` system tables.

By default, the credential data in the `SYS.LINK$` and `SYS.SCHEDULER$_CREDENTIAL` system tables is obfuscated. However, because of the availability of many types of de-obfuscation algorithms, Oracle recommends that you encrypt this sensitive credential data. To check the status the data dictionary credentials, you can query the `DICTIONARY_CREDENTIALS_ENCRYPT` data dictionary view.

The encryption of sensitive credential data in these two system tables uses Transparent Data Encryption. Encryption of credential data uses the AES256 algorithm. To encrypt credential data, you do not need an Oracle Advanced Security Option license, but you must be granted the `SYSKM` administrative privilege and the database must have an open keystore.

**Related Topics**

- [Oracle Database Security Guide](../dbseg/encrypt-sensitive-data.md)

**Parent topic:** Encryption Conversions for Tablespaces and Databases

#### 4.6.8 Encryption Conversions for Existing Offline Tablespaces

You can perform offline encryption conversions by using the `ALTER TABLESPACE` SQL statement `OFFLINE`, `ENCRYPT`, and `DECRYPT` clauses.

- About Encryption Conversions for Existing Offline Tablespaces
  You can encrypt or decrypt an existing data file of a user tablespace when the tablespace is offline or when the database is not open.
- Encrypting an Existing User-Defined Tablespace with Offline Conversion
  To encrypt an existing tablespace with offline conversion, you can use the `ALTER TABLESPACE` SQL statement with the `OFFLINE` and `ENCRYPT` clauses.
- Decrypting an Existing Tablespace with Offline Conversion
  To decrypt an existing tablespace with offline conversion, you can use the `ALTER TABLESPACE` SQL statement with the `OFFLINE` and `DECRYPT` clauses.

**Parent topic:** Encryption Conversions for Tablespaces and Databases

##### 4.6.8.1 About Encryption Conversions for Existing Offline Tablespaces

You can encrypt or decrypt an existing data file of a user tablespace when the tablespace is offline or when the database is not open.

Use the offline encryption method if you do not plan to change the compatibility of your databases from Oracle Database 11c release 2 (11.2) or Oracle Database 12c release 1 (12.1) to release 19c, which is irreversible. The offline encryption method is also useful if you want to quickly make use of Transparent Data Encryption before you upgrade this database to release 18c. You can both encrypt and decrypt offline tablespaces.

Note the following:

- If you want to encrypt the Oracle Database-supplied tablespaces (`SYSTEM`, `SYSAUX`, and `UNDO`) using the offline conversion method, then you must use the method that is recommended when you encrypt an existing database with offline conversion.

- You can use the online method to rekey, change the encryption algorithm, or decrypt a tablespace that was previously encrypted with the offline method.

- If you have configured Oracle Data Guard, then you can minimize downtime by encrypting the tablespaces on the standby first, switching over to the primary, and then performing an offline encryption the tablespaces on the new standby database. Offline encryption (both on the data file and tablespace level) are is performed on the standby first. Online encryption is an Oracle Data Guard transaction, and as such, it is replayed on the standby database.

- You can use the `USING ... ENCRYPT` clause to specify an encryption algorithm. Supported algorithms include `AES128`, `AES192`, `AES256`, and others, such as `ARIA` and `GOST`. To check the encryption key, query the `ENCRYPTIONALG` column in the `V$DATABASE_KEY_INFO` view.

- To set the default encryption algorithm for future offline tablespace encryption operations, set the `TABLESPACE_ENCRYPTION_DEFAULT_ALGORITHM` dynamic parameter.

- You can use the `ALTER TABLESPACE` statement to convert offline tablespaces in parallel by using multiple foreground sessions to encrypt different data files.

- If you are using Oracle Data Guard, you can minimize the downtime by encrypting the tablespaces on the standby first, switching over, and then encrypting the tablespaces on the original primary next.

- For Oracle Database 11g release 2 (11.2.0.4) and Oracle Database 12c release 1 (12.1.0.2), you cannot perform an offline encryption of the `SYSTEM` and `SYSAUX` tablespaces. Also, Oracle does not recommend encrypting offline the `UNDO` tablespace in these releases. Doing so prevents the keystore from being closed, and this prevents the database from functioning. In addition, encrypting the `UNDO` tablespace while the database is offline is not necessary because all undo records that are associated with any encrypted tablespaces are already automatically encrypted in the `UNDO` tablespace. If you want to encrypt the `TEMP` tablespace, you must drop and then recreate it as encrypted.

**Related Topics**

- Encrypting an Existing Database with Offline Conversion
- [Supported Encryption and Integrity Algorithms](introduction-to-transparent-data-encryption.md)
- Setting the Tablespace Encryption Default Algorithm

**Parent topic:** Encryption Conversions for Existing Offline Tablespaces

##### 4.6.8.2 Encrypting an Existing User-Defined Tablespace with Offline Conversion

To encrypt an existing tablespace with offline conversion, you can use the `ALTER TABLESPACE` SQL statement with the `OFFLINE` and `ENCRYPT` clauses.

The procedure that is described in this section applies to the case where you want to encrypt individual user-created tablespaces within a database. These tablespaces can be encrypted offline. However, the Oracle Database-supplied `SYSTEM` and `UNDO` tablespaces cannot be brought offline. If you want to encrypt the tablespaces offline, then you must use the method that is described in Encrypting an Existing Database with Offline Conversion.

1.  Connect to the united mode CDB root or isolated mode PDB as a user who has been granted administrative privileges.
    You must have the `SYSDBA` administrative privilege to work with the `SYSTEM` and `SYSAUX` tablespaces. Otherwise, connect with the `SYSKM` administrative privilege.
2.  Bring the tablespace offline.
        ALTER TABLESPACE users OFFLINE NORMAL;
3.  Back up the tablespace.
    The offline conversion method does not use auxiliary disk space or files, and it operates directly in-place to the data files. Therefore, you should perform a full backup of the user tablespace before converting it offline.
4.  As a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege, open the TDE wallet.
    For example:
        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN IDENTIFIED BY TDEk_wallet_password;
5.  Encrypt the tablespace.
    For example, to encrypt an entire tablespace, include its data files:
        ALTER TABLESPACE users1 ENCRYPTION OFFLINE ENCRYPT;

    This example encrypts the tablespace with the default encryption algorithm, `AES128`. (`AES256` is the default.) To use a different encryption algorithm, enter a statement similar to the following:

        ALTER TABLESPACE users2 ENCRYPTION OFFLINE USING 'AES128' ENCRYPT;

    To encrypt individual data files within a tablespace, use the `ALTER DATABASE DATAFILE` SQL statement. For example, to encrypt the data files `user_01.dbf` and `user_02.dbf`:
        ALTER DATABASE DATAFILE 'user_01.dbf' ENCRYPT;
        ALTER DATABASE DATAFILE 'user_02.dbf' ENCRYPT;

    In the same database session, these statements encrypt each of the data files in sequence, one after another. If you run each statement in its own database session, then they will be run in parallel.

    If the encryption process is interrupted, then rerun the `ALTER TABLESPACE` statement. The kinds of errors that you can expect in an interruption are general errors, such as file system or storage file system errors. The data files within the tablespace should be consistently encrypted. For example, suppose you offline a tablespace that has 10 files but for some reason, the encryption only completes for nine of the files, leaving one decrypted. Although it is possible to bring the tablespace back online with such inconsistent encryption if the `COMPATIBLE` parameter is set to `12.2.0.0` or later, then it is not recommended to leave the tablespace in this state. If `COMPATIBLE` is less than `12.2.0.0`, then it is not possible to bring the tablespace online if the encryption property is inconsistent across the data files.
6.  Bring the tablespace back online or open the database.
    - To bring the tablespace back online:

          ALTER TABLESPACE users ONLINE;

    - To open a database in a non-multitenant environment:

          ALTER DATABASE OPEN

    - In a multitenant environment, you can encrypt a data file or tablespace with the offline method if the root is open and the PDB is not open. For example, for a PDB named `hr_pdb`:

          ALTER PLUGGABLE DATABASE hr_pdb OPEN
7.  Perform a full backup of the converted tablespace.

**Related Topics**

- [Supported Encryption and Integrity Algorithms](introduction-to-transparent-data-encryption.md)

**Parent topic:** Encryption Conversions for Existing Offline Tablespaces

##### 4.6.8.3 Decrypting an Existing Tablespace with Offline Conversion

To decrypt an existing tablespace with offline conversion, you can use the `ALTER TABLESPACE` SQL statement with the `OFFLINE` and `DECRYPT` clauses.

1.  Connect as a user who has the `SYSDBA` administrative privilege.
    You must have the `SYSDBA` administrative privilege if you plan to decrypt the `SYSTEM` and `SYSAUX` tablespaces. Otherwise, connect with the `SYSKM` administrative privilege.
2.  Bring the tablespace offline.
        ALTER TABLESPACE users OFFLINE NORMAL;
3.  As a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege, open the keystore.
    For example:
        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN IDENTIFIED BY TDE_wallet_password;
4.  Run the `ALTER TABLESPACE` SQL statement to perform the decryption.
    For example, for a tablespace called `users`:
        ALTER TABLESPACE users ENCRYPTION OFFLINE DECRYPT;

    If the decryption process is interrupted, then rerun the `ALTER TABLESPACE` statement. The kinds of errors that you can expect in an interruption are general errors, such as file system or storage file system errors. The data files within the tablespace should be consistently decrypted. For example, suppose you offline a tablespace that has 10 files but for some reason, the decryption only completes for nine of the files, leaving one encrypted. Although it is possible to bring the tablespace back online with such inconsistent decryption if the `COMPATIBLE` parameter is set to `12.2.0.0` or later, then it is not recommended to leave the tablespace in this state. If `COMPATIBLE` is less than `12.2.0.0`, then it is not possible to bring the tablespace online if the encryption property is inconsistent across the data files.
5.  Bring the tablespace online.
        ALTER TABLESPACE users ONLINE;

**Related Topics**

- Opening a TDE Wallet

**Parent topic:** Encryption Conversions for Existing Offline Tablespaces

#### 4.6.9 Encryption Conversions for Existing Online Tablespaces

You can encrypt and decrypt an online existing tablespace by using the `ALTER TABLESPACE` SQL statement with the `ONLINE` and `ENCRYPT` or `DECRYPT` clauses.

- About Encryption Conversions for Existing Online Tablespaces
  You can encrypt, decrypt, or rekey existing user tablespaces, and the `SYSTEM`, `SYSAUX`, and `UNDO` tablespace when they are online.
- Encrypting an Existing Tablespace with Online Conversion
  To encrypt an existing tablespace with online conversion, use `ALTER TABLESPACE` with the `ONLINE` and `ENCRYPT` clauses.
- Rekeying an Existing Tablespace with Online Conversion
  To rekey an existing tablespace that is online, you can use the `REKEY` clause of the `ALTER TABLESPACE` SQL statement.
- Decrypting an Existing Tablespace with Online Conversion
  To decrypt an existing tablespace with online conversion, you can use the `ALTER TABLESPACE` SQL statement with `DECRYPT` clause.
- Finishing an Interrupted Online Encryption Conversion
  If an online encryption process is interrupted, then you can complete the conversion by rerunning the `ALTER TABLESPACE` statement using the `FINISH` clause.

**Parent topic:** Encryption Conversions for Tablespaces and Databases

##### 4.6.9.1 About Encryption Conversions for Existing Online Tablespaces

You can encrypt, decrypt, or rekey existing user tablespaces, and the `SYSTEM`, `SYSAUX`, and `UNDO` tablespace when they are online.

However, you cannot encrypt, decrypt, or rekey a temporary tablespace online.

An online tablespace can be created by using the `ONLINE` clause of the `CREATE TABLESPACE` SQL statement. When you encrypt or rekey a tablespace online, the tablespace will have its own independent encryption keys and algorithms.

Note the following:

- If an offline tablespace has been encrypted, then you can rekey it online to use a different algorithm.

- You can encrypt multiple tablespaces online in parallel by using multiple foreground sessions to encrypt different tablespaces. Within each tablespace, the data files are encrypted sequentially.

- If the conversion is interrupted, then you can resume the process by issuing the `FINISH` clause of the `ALTER TABLESPACE` SQL statement.

- A redo log is generated for each online tablespace conversion.

- Do not encrypt the `SYSTEM` and `UNDO` tablespaces concurrently with other tablespaces.

- You cannot use the transportable tablespace feature with Oracle Data Pump while you are encrypting a tablespace.

- You cannot run the `ALTER TABLESPACE` statement concurrently with the following features:
  - `ADMINISTER KEY MANAGEMENT SET KEY` SQL statement

  - `FLASHBACK DATABASE` SQL statement

- If you are using Oracle-managed files for the data files, then the encryption process rekeys the data files that are associated with the tablespace and then copies or moves them to the default Oracle-managed files location.

- You can add new files to the tablespace after you have encrypted it. Oracle Database reformats the new file with the new encryption key. Blocks will be encrypted using the new key.

- Previous operations that took place in the root or the PDB may require the control files to be cross-checked against the data dictionary before you can begin the online conversion process. An `ORA-241 operation disallowed: control file is not yet checked against data dictionary` error may occur. To resolve this problem, restart the root or PDB, and then try issuing the online conversion commands again.

- For security reasons, once online conversion processes a data file, Oracle will zero out the original data file before deletion. This prevents the database from leaving ghost data on disk sectors. However, there is a known limitation that can occur if you are performing an online tablespace conversion at the same time that Oracle Recovery Manager (Oracle RMAN) is validating files. The online tablespace conversion processes each file one at a time. If Oracle RMAN is validating a file at the same time that it is being processed by the online tablespace conversion, then Oracle RMAN could report a corruption problem (`ORA-01578: ORACLE data block corrupted (file # , block # )`). It does this because it sees the blocks that comprise the file as zero. This is a false alarm and you can ignore the error. If this occurs, then try running the Oracle RMAN validation process again.

**Related Topics**

- [Supported Encryption and Integrity Algorithms](introduction-to-transparent-data-encryption.md)

**Parent topic:** Encryption Conversions for Existing Online Tablespaces

##### 4.6.9.2 Encrypting an Existing Tablespace with Online Conversion

To encrypt an existing tablespace with online conversion, use `ALTER TABLESPACE` with the `ONLINE` and `ENCRYPT` clauses.

1.  Connect as a user who has the `SYSDBA` administrative privilege.
    You must have the `SYSDBA` administrative privilege if you plan to encrypt the `SYSTEM` and `SYSAUX` tablespaces. Otherwise, connect with the `SYSKM` administrative privilege.
2.  Ensure that the `COMPATIBLE` initialization parameter is set to 12.2.0.0 or later.
    You can use the `SHOW PARAMETER` command to check the current setting of a parameter.
3.  Ensure that the database is open in read-write mode.
    You can query the `STATUS` column of the `V$INSTANCE` dynamic view to find if a database is open and the `OPEN_MODE` column of the `V$DATABASE` view to find if it in read-write mode.
4.  If necessary, open the database in read-write mode.
        ALTER DATABASE OPEN READ WRITE;
5.  Ensure that the auxiliary space is at least the same size as the largest data file of this tablespace.
    This size requirement is because Oracle Database performs the conversion one file at a time. For example, if the largest data file of the tablespace is 32 GB, then ensure that you have 32 GB of auxiliary space. To find the space used by a data file, query the `BYTES` or `BLOCKS` column of the `V$DATAFILE` dynamic performance view.
6.  Create and open a master encryption key.
    For example:

        ADMINISTER KEY MANAGEMENT CREATE KEYSTORE 'TDE_wallet_location' IDENTIFIED BY TDE_wallet_password;
        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN IDENTIFIED BY TDE_wallet_password;
        ADMINISTER KEY MANAGEMENT SET KEY IDENTIFIED BY TDE_wallet_password WITH BACKUP;
7.  Run the `ALTER TABLESPACE` statement using the `ENCRYPTION` and `ENCRYPT` clauses to perform the encryption.
    **Note:**

    For the `SYSTEM` tablespace, you can use the `ENCRYPT` clause to encrypt the tablespace, but you cannot specify an encryption algorithm because it is encrypted with the existing database key the first time. After encrypting the `SYSTEM` tablespace, use the `REKEY` clause to specify the algorithm. See Rekeying an Existing Tablespace with Online Conversion for more information.
    For example, for a non-Oracle managed files tablespace named `users`:

        ALTER TABLESPACE users ENCRYPTION ONLINE USING 'AES192' ENCRYPT FILE_NAME_CONVERT = ('users.dbf', 'users_enc.dbf');

    In this example:

    - `ENCRYPTION ONLINE USING ‘AES192’ ENCRYPT` sets the statement to encrypt the tablespace `users` while it is online and assigns it the `AES192` encryption algorithm. If you omit the `USING ``algorithm` clause, then the default algorithm, `AES128`, is used.

    - `FILE_NAME_CONVERT` specifies one or more pairs of data files that are associated with the tablespace. The first name in the pair is an existing data file, and the second name is for the encrypted version of this data file, which will be created after the `ALTER TABLESPACE` statement successfully executes. If the tablespace has more than one data file, then you must process them all in this statement. Note the following:

      - Separate each file name with a comma, including multiple pairs of files. For example:

            FILE_NAME_CONVERT = ('users1.dbf', 'users1_enc.dbf', 'users2.dbf', 'users2_enc.dbf')

      - You can specify directory paths in the `FILE_NAME_CONVERT` clause. For example, the following clause converts and moves the matching files of the tablespace from the `dbs` directory to the `dbs/enc` directory:

            FILE_NAME_CONVERT = ('dbs', 'dbs/enc')

      - The `FILE_NAME_CONVERT` clause recognizes patterns. The following example converts the data files `users_1.dbf` and `users_2.dbf` to `users_enc1.dbf` and `users_enc2.dbf`:

            FILE_NAME_CONVERT = ('users', 'users_enc')

      - In an Oracle Data Guard environment, include the name of the standby database data file in the `FILE_NAME_CONVERT` settings.

      - If you are using Oracle-managed file mode, then the new file name is internally assigned, so this file name should not affect your site's file-naming standards. If you are using non-Oracle-managed file mode and if you omit the `FILE_NAME_CONVERT` clause, then Oracle Database internally assigns an auxiliary file name, and then later renames it back to the original name. This enables the encryption process to use the name that you had originally given the file to be encrypted. The renaming operation is effectively creating another copy of the file, hence it is slower than explicitly including the `FILE_NAME_CONVERT` clause. For better performance, include the `FILE_NAME_CONVERT` clause.

      - You can find the data files for a tablespace by querying the `V$DATAFILE` or `V$DATAFILE_HEADER` dynamic views.

      By default, data files are in the `$ORACLE_HOME/dbs` directory. If the data files are located there, then you do not have to specify a path.

After you complete the conversion, you can check the encryption status by querying the `STATUS` column of the `V$ENCRYPTED_TABLESPACES` dynamic view. The `ENCRYPTIONALG` column of this view shows the encryption algorithm that is used. If the conversion process was interrupted, then you can resume it by running `ALTER TABLESPACE` with the `FINISH` clause. For example, if the primary data file converts but the standby data file does not, then you can run `ALTER TABLESPACE ... FINISH` on the standby database for the standby data files.

**Related Topics**

- Setting the COMPATIBLE Initialization Parameter for Tablespace Encryption
- Finishing an Interrupted Online Encryption Conversion

**Parent topic:** Encryption Conversions for Existing Online Tablespaces

##### 4.6.9.3 Rekeying an Existing Tablespace with Online Conversion

To rekey an existing tablespace that is online, you can use the `REKEY` clause of the `ALTER TABLESPACE` SQL statement.

Before you perform a rekey operation, be aware of the following:

- You cannot rekey the `TEMP` tablespace. If you want to assign a different encryption algorithm to a `TEMP` tablespace, then drop `TEMP` and recreate it with the correct encryption algorithm.

- Do not perform an online tablespace rekey operation with a master key operation concurrently. To find if any tablespaces are currently being rekeyed, issue the following query to find the rekey status of encrypted tablespaces:

      SELECT TS#,ENCRYPTIONALG,STATUS FROM V$ENCRYPTED_TABLESPACES;

  A status of `REKEYING` means that the corresponding tablespace is still being rekeyed. Do not rekey the master key while this status is in effect.

To rekey an existing tablespace with online conversion:

1.  Connect as a user who has the `SYSDBA` administrative privilege.
    For example:

        sqlplus sec_admin as sysdba
        Enter password: password

    You must have the `SYSDBA` administrative privilege if you plan to rekey the `SYSTEM` and `SYSAUX` tablespaces. Otherwise, connect with the `SYSKM` administrative privilege.
2.  Ensure that the following requirements are met:
    - The `COMPATIBLE` initialization parameter is set to 12.2.0.0 or later.
    - The database is open and in read-write mode.
    - A master encryption key has been created and is open.
3.  Query the `KEY_VERSION` and `STATUS` columns of the `V$ENCRYPTED_TABLESPACES` dynamic view to find the current status of the encryption algorithm used by the master encryption key.
4.  Perform the rekey operation, based on the status returned by the `V$ENCRYPTED_TABLESPACES` dynamic view:
    - If the key version status of the tablespace is `NORMAL`, then specify the new algorithm of the online tablespace rekey.

      For example:

          ALTER TABLESPACE users ENCRYPTION USING 'AES192' REKEY FILE_NAME_CONVERT = ('users.dbf', 'users_enc.dbf');

    - If the key version status is `ENCRYPTING`, `DECRYPTING`, or `REKEYING`, then use the `FINISH` clause.

      For example:

          ALTER TABLESPACE users ENCRYPTION ONLINE FINISH REKEY FILE_NAME_CONVERT = ('users.dbf', 'users_enc.dbf');
5.  If the `ORA-00241 operation disallowed: control file inconsistent with data dictionary` error appears, then restart the database.
    In a multitenant environment, restart the CDB root database and then retry Step 4.

If the conversion process was interrupted, then you can resume it by running `ALTER TABLESPACE` with the `FINISH` clause.

**Related Topics**

- Encrypting an Existing Tablespace with Online Conversion
- About Encryption Conversions for Existing Online Tablespaces
- Finishing an Interrupted Online Encryption Conversion

**Parent topic:** Encryption Conversions for Existing Online Tablespaces

##### 4.6.9.4 Decrypting an Existing Tablespace with Online Conversion

To decrypt an existing tablespace with online conversion, you can use the `ALTER TABLESPACE` SQL statement with `DECRYPT` clause.

1.  Connect as a user who has the `SYSDBA` administrative privilege.
    You must have the `SYSDBA` administrative privilege if you plan to decrypt the `SYSTEM` and `SYSAUX` tablespaces. Otherwise, connect with the `SYSKM` administrative privilege.
2.  Ensure that the following requirements are met:
    - The `COMPATIBLE` initialization parameter is set to 12.2.0.0 or later.
    - The database is open and in read-write mode.
    - A master encryption key has been created and is open.
    - There is enough auxiliary space to complete the decryption.
3.  Run the `ALTER TABLESPACE` SQL statement with the `DECRYPT` clause.
    For example:

        ALTER TABLESPACE users ENCRYPTION ONLINE DECRYPT FILE_NAME_CONVERT = ('users_enc.dbf', 'users.dbf');

    In this specification:

    - When you specify the files to decrypt, enter them in the reverse order in which they were originally encrypted. That is, first enter the name of the encrypted file (`users_enc.dbf`), followed by the data file (`users.dbf`).

    - Do not provide an algorithm key for the decryption.

If the conversion process was interrupted, then you can resume it by running `ALTER TABLESPACE` with the `FINISH` clause.

**Related Topics**

- Encrypting an Existing Tablespace with Online Conversion
- Finishing an Interrupted Online Encryption Conversion

**Parent topic:** Encryption Conversions for Existing Online Tablespaces

##### 4.6.9.5 Finishing an Interrupted Online Encryption Conversion

If an online encryption process is interrupted, then you can complete the conversion by rerunning the `ALTER TABLESPACE` statement using the `FINISH` clause.

An interrupted encryption process (encryption, rekey, or decryption) can be, for example, an `ORA-28425: missing a valid FILE_NAME_CONVERT clause` error in the `FILE_NAME_CONVERT` clause of the `ALTER TABLESPACE` SQL statement. Other examples of interrupted processes are if the conversion skips a data file, which can happen if there is an error when an Oracle DataBase WRiter (DBWR) process offlines a data file, or if there is not enough space for the auxiliary file. The tablespace should be operational even if you do not rerun the `ALTER TABLESPACE` statement with the `FINISH` clause.

In addition to interrupted encryption processes, the tablespace encryption process can fail during the period when the status is `ENCRYPTING`. In this case, you can either decrypt the tablespace back to its original state, or you can resume the encryption by using the `ENCRYPTION ONLINE FINISH ENCRYPT` clause of `ALTER TABLEPSPACE`.

1.  Query the `V$ENCRYPTED_TABLESPACES` to check the `STATUS` column for the tablespace.
    If the `STATUS` column reports `ENCRYPTING`, `DECRYPTING`, or `REKEYING`, then re-run the `ALTER TABLESPACE` statement with the `FINISH` clause, as described in this procedure. If the `STATUS` reports `NORMAL`, then you can rerun `ALTER TABLESPACE` without the `FINISH` clause.

    You can find the tablespace name that matches the `TS#` and `TABLESPACE_NAME` columns by querying the `V$DATAFILE_HEADER` view.
2.  If necessary query the following additional views to find information about the tablespace whose online conversion was interrupted:
    - `DBA_TABLESPACES` to find if the `STATUS` of the tablespace indicates if it is online or offline.
    - `V$ENCRYPTED_TABLESPACES` to find if the `STATUS` of the tablespace indicates if it is encrypted, and what the `KEY_VERSION` of the encryption key is.
    - `V$DATAFILE` and `V$DATAFILE_HEADER` to find the data files that are associated with a tablespace.
3.  Run the `ALTER TABLESPACE` statement using the `FINISH` clause.
    Examples are as follows:
    - For an encryption operation:
          ALTER TABLESPACE users ENCRYPTION ONLINE FINISH ENCRYPT FILE_NAME_CONVERT = ('users.dbf', 'users_enc.dbf');
    - For a decryption operation:
          ALTER TABLESPACE users ENCRYPTION ONLINE FINISH DECRYPT FILE_NAME_CONVERT = ('users_enc.dbf', 'users.dbf');

      Note the order in which the files are specified: first, the name of the encrypted file, and then the name of the data file. (In the encryption operation, the name of the data file is specified first, followed by the name of the encrypted file.)
    - For a rekey operation:
          ALTER TABLESPACE users ENCRYPTION ONLINE FINISH REKEY FILE_NAME_CONVERT = ('users.dbf', 'users_enc.dbf');

      You cannot specify an algorithm when you use the `FINISH` clause in an `ALTER TABLESPACE` statement.
4.  To check the conversion, query the `STATUS` column of the `V$ENCRYPTED_TABLESPACES` view.
    The status should be `NORMAL`. In an Oracle Data Guard environment, if the database does not have `NORMAL` as the `STATUS`, then run the `ALTER TABLESPACE ... FINISH` statement on the primary or the standby data file that did not successfully convert.

**Parent topic:** Encryption Conversions for Existing Online Tablespaces

#### 4.6.10 Encryption Conversions for Existing Databases

You can encrypt both offline and online databases.

- About Encryption Conversions for Existing Databases
  The encryption conversion of an entire database encrypts all tablespaces, including the Oracle-supplied `SYSTEM`, `SYSAUX`, `UNDO`, and `TEMP` tablespaces.
- Encrypting an Existing Database with Offline Conversion
  When you encrypt an existing database with offline conversion, for the Oracle-managed tablespaces, you do not specify an encryption algorithm.
- Encrypting an Existing Database with Online Conversion
  When you encrypt an existing database with online conversion, you do not specify an encryption algorithm.

**Parent topic:** Encryption Conversions for Tablespaces and Databases

##### 4.6.10.1 About Encryption Conversions for Existing Databases

The encryption conversion of an entire database encrypts all tablespaces, including the Oracle-supplied `SYSTEM`, `SYSAUX`, `UNDO`, and `TEMP` tablespaces.

Note the following:

- If you are using Database Configuration Assistant (DBCA) to create or configure a database, then you can create a TDE wallet in the database as part of the creation or configuration process. When you drop a database by using DBCA, any TDE wallets that are in this database are also removed. Important: Before you drop a database by using DBCA, and if it has any local TDE wallets, then back these wallets up to a secure location. If the database has been migrated to use Oracle Key Vault, then be aware that its TDE encryption keys reside in the Oracle Key Vault server. It is the responsibility of the Oracle Key Vault administrator to back up Oracle Key Vault.

- To perform the encryption, you can use the offline and online functionality of the tablespace encryption conversions.

- You can encrypt any or all of the Oracle-supplied tablespaces, and in any order. The encryption of the Oracle-supplied tablespaces has no impact on the encryption of user-created tablespaces.

- When you encrypt the Oracle-supplied tablespaces, Oracle Database prevents the keystore from being closed.

- You cannot encrypt an existing temporary tablespace, but you can create an encrypted temporary tablespace, configure the database to use that new encrypted temporary tablespace as the default temporary tablespace, and then drop the old clear-text temporary tablespace.

- The `UNDO` and `TEMP` metadata that is generated from sensitive data in an encrypted tablespace is already automatically encrypted. Therefore, encrypting `UNDO` and `TEMP` is optional.

- The performance effect of encrypting all the tablespaces in a database depends on the workload and platform. Many modern CPUs provide built-in hardware acceleration, which results in a minimal performance impact.

- In a multitenant environment, you can encrypt any tablespaces in any pluggable databases (PDBs), including the Oracle-supplied tablespaces. However, the keystore in the CDB root must be open at all times so that a PDB can open its keystore. You can check the status of whether a keystore is open by querying the `STATUS` column of the `V$ENCRYPTION_WALLET` view

**Parent topic:** Encryption Conversions for Existing Databases

##### 4.6.10.2 Encrypting an Existing Database with Offline Conversion

When you encrypt an existing database with offline conversion, for the Oracle-managed tablespaces, you do not specify an encryption algorithm.

1.  Connect as a user who has the `SYSDBA` administrative privilege.
    You must have the `SYSDBA` administrative privilege to encrypt the `SYSTEM` and `SYSAUX` tablespaces.
2.  Mount the database.
        STARTUP MOUNT
3.  Open the keystore.
        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN IDENTIFIED BY keystore_password;
4.  Run the `ALTER TABLESPACE` SQL statement to encrypt the `SYSTEM`, `SYSAUX`, and `UNDO` tablespaces. Do not encrypt the `SYSTEM` tablespace concurrently with the encryption of other tablespaces.
    For example, to encrypt the `SYSTEM` tablespace:

        ALTER TABLESPACE SYSTEM ENCRYPTION OFFLINE ENCRYPT;
5.  Open the database.
    For example, to open the database in read/write mode:
        ALTER DATABASE OPEN READ WRITE;
6.  Run the `ALTER TABLESPACE` SQL statement to encrypt other user tablespaces.
    Alternatively, you can proceed to the next step and open the database first, and then perform the steps described in Encrypting an Existing User-Defined Tablespace with Offline Conversion.
7.  Open the database.
        ALTER DATABASE OPEN;

After you have encrypted the tablespace, if you want to use a different encryption algorithm (change the TDE master encryption key) for the `SYSTEM`, `SYSAUX`, and `UNDO` tablespaces, then you must use online conversion. In addition to `AES128`, supported encryption algorithms are `AES192` and `AES256`, in addition to other algorithms such as `ARIA` and `GOST`.

**Related Topics**

- [Changing the TDE Master Encryption Key for a Tablespace](managing-keystore-and-tde-master-encryption-key.md)
- [Supported Encryption and Integrity Algorithms](introduction-to-transparent-data-encryption.md)

**Parent topic:** Encryption Conversions for Existing Databases

##### 4.6.10.3 Encrypting an Existing Database with Online Conversion

When you encrypt an existing database with online conversion, you do not specify an encryption algorithm.

The reason that you do not need to specify an encryption algorithm the first time you perform the encryption is that the tablespaces that you must use to encrypt the database are automatically encrypted with the database key. If you want to change the algorithm, then you can issue the `ALTER TABLESPACE ENCRYPTION REKEY` SQL statement after the initial encryption.

1.  Perform the following tasks, which are described in Encrypting an Existing Tablespace with Online Conversion:
    1.  Connect as a user who has been granted the `SYSDBA` administrative privilege.
    2.  Ensure that the `COMPATIBLE` parameter is set to `12.2.0.0` or later.
    3.  Ensure that the database is open in read-write mode.
    4.  Ensure that you have enough auxiliary space to complete the encryption.
    5.  Back up the tablespaces that you must encrypt.
    6.  Open the keystore.
2.  Run the `ALTER TABLESPACE` SQL statement to encrypt the `SYSTEM`, `SYSAUX`, and `UNDO` tablespaces. Do not specify an algorithm, and do not encrypt the `SYSTEM` tablespace concurrently with the encryption of other tablespaces.
    For example, to encrypt the `SYSTEM` tablespace:

        ALTER TABLESPACE SYSTEM ENCRYPTION ONLINE ENCRYPT
        FILE_NAME_CONVERT=('system01.dbf','system01_enc.dbf');
3.  Create a temporary tablespace.
    1.  Create a new (encrypted) `TEMP` tablespace with the identical characteristics as the original `TEMP` tablespace, as follows:
            SELECT ' CREATE TEMPORARY TABLESPACE '
            ||tablespace_name||'_ENC tempfile '''
            ||substr(file_name,1,length(file_name)-4)
            ||'_enc.dbf'' size '
            ||bytes||' ENCRYPTION USING ''AES256'' ENCRYPT;'
            AS " Create new encrypted TEMP tablespace"
            FROM DBA_TEMP_FILES;

        Alternatively, you could extract the original parameters by running `DBMS_METADATA.GET_DDL`. If you omit the `USING ``algorithm` clause, then Oracle Database applies the default algorithm.
    2.  Run the command (that is, the output of the `SELECT` statement).
    3.  Change the database default temporary tablespace to the new encrypted `TEMP` tablespace.
            ALTER DATABASE DEFAULT TEMPORARY TABLESPACE temp_enc;
    4.  Drop the original `TEMP` tablespace.
            DROP TABLESPACE TEMP INCLUDING CONTENTS AND DATAFILES;

        Optionally, you can rename `temp_enc` to `TEMP`.

**Related Topics**

- [Changing the TDE Master Encryption Key for a Tablespace](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Encryption Conversions for Existing Databases

### 4.7 Transparent Data Encryption Data Dynamic and Data Dictionary Views

You can query a set of dynamic and data dictionary views to find more information about Transparent Data Encryption (TDE) data.

Table 4-4 describes these dynamic and data dictionary views.

Table 4-4 Transparent Data Encryption Related Views

| View                             | Description                                                                                                                                                                                                                                                                                                                                                                                                       |
|:---------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `ALL_ENCRYPTED_COLUMNS`          | Displays encryption information about encrypted columns in the tables accessible to the current user                                                                                                                                                                                                                                                                                                              |
| `DICTIONARY_CREDENTIALS_ENCRYPT` | Indicates if credential data in the `SYS.LINK$` and `SYS.SCHEDULER$_CREDENTIAL` system tables is encrypted                                                                                                                                                                                                                                                                                                        |
| `DBA_ENCRYPTED_COLUMNS`          | Displays encryption information for all of the encrypted columns in the database                                                                                                                                                                                                                                                                                                                                  |
| `USER_ENCRYPTED_COLUMNS`         | Displays encryption information for encrypted table columns in the current user's schema                                                                                                                                                                                                                                                                                                                          |
| `DBA_TABLESPACE_USAGE_METRICS`   | Describes tablespace usage metrics for all types of tablespaces, including permanent, temporary, and undo tablespaces                                                                                                                                                                                                                                                                                             |
| `V$CLIENT_SECRETS`               | Lists the properties of the strings (secrets) that were stored in the keystore for various features (clients).<br>In a multitenant environment, when you query this view in a PDB, then it displays information about keys that were created or activated for the current PDB. If you query this view in the root, then it displays this information about keys for all of the PDBs.                              |
| `V$DATABASE_KEY_INFO`            | Displays information about the default encryption key that is used for the current database. The default is `AES128`.                                                                                                                                                                                                                                                                                             |
| `V$ENCRYPTED_TABLESPACES`        | Displays information about the tablespaces that are encrypted                                                                                                                                                                                                                                                                                                                                                     |
| `V$ENCRYPTION_KEYS`              | When used with keys that have been rekeyed with the `ADMINISTER KEY MANAGEMENT` statement, displays information about the TDE master encryption keys.<br>In a multitenant environment, when you query this view in a PDB, it displays information about keys that were created or activated for the current PDB. If you query this view in the root, it displays this information about keys for all of the PDBs. |
| `V$ENCRYPTION_WALLET`            | Displays information on the status of the keystore and the keystore location for TDE                                                                                                                                                                                                                                                                                                                              |
| `V$RMAN_ENCRYPTION_ALGORITHMS`   | Displays supported encryption algorithms in the current PDB and is used by Oracle Recovery Manager (Oracle RMAN) to validate user-requested algorithms                                                                                                                                                                                                                                                            |

**See Also:**

[Oracle Database Reference](../refrn/index.md) for detailed information about these views

**Parent topic:** Configuring Transparent Data Encryption
