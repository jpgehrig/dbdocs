## 6 Managing Keystores and TDE Master Encryption Keys in United Mode

United mode enables you to create a common keystore for the CDB and the PDBs for which the keystore is in united mode.

The keys for the CDB and the PDBs reside in the common keystore.

- About Managing Keystores and TDE Master Encryption Keys in United Mode
  In united mode, you create the keystore and TDE master encryption key for CDB and PDBs that reside in the same keystore.
- Operations That Are Allowed in United Mode
  Many `ADMINISTER KEY MANAGEMENT` operations performed in the CDB root apply to keystores and encryption keys in the united mode PDB.
- Operations That Are Not Allowed in a United Mode PDB
  `ADMINISTER KEY MANAGEMENT` operations that are not allowed in a united mode PDB can be performed in the CDB root.
- Configuring United Mode with the Initialization Parameter File and ALTER SYSTEM
  If your environment relies on server parameter files (`spfile`), then you can set `WALLET_ROOT` and `TDE_CONFIGURATION` using `ALTER SYSTEM SET` with `SCOPE`.
- Configuring a Software Keystore for Use in United Mode
  In united mode, the software keystore resides in the CDB root but the master keys from this keystore are available for the PDBs that have their keystore in united mode.
- Configuring a Container Database with United Mode PDBs for Oracle Key Vault
  The TDE master keys of all united mode PDBs and the CDB reside in the same virtual wallet in Oracle Key Vault.
- Administering Keystores and TDE Master Encryption Keys in United Mode
  After you configure a keystore and master encryption key for use in united mode, you can perform tasks such as rekeying TDE master encryption keys.
- Administering Transparent Data Encryption in United Mode
  You can perform general administrative tasks with Transparent Data Encryption in united mode.

**Parent topic:** [Using Transparent Data Encryption](asopart1.md)

### 6.1 About Managing Keystores and TDE Master Encryption Keys in United Mode

In united mode, you create the keystore and TDE master encryption key for CDB and PDBs that reside in the same keystore.

The keys for PDBs having keystore in united mode, can be created from CDB root or from the PDB.

This design enables you to have one keystore to manage the entire CDB environment, enabling the PDBs to share this keystore, but you can customize the behavior of this keystore in the individual united mode PDBs. For example, in a united mode PDB, you can configure a TDE master encryption key for the PDB in the united keystore that you created in the CDB root, open the keystore locally, and close the keystore locally. In order to perform these actions, the keystore in the CDB root must be open.

Before you configure your environment to use united mode or isolated mode, all the PDBs in the CDB environment are considered to be in united mode.

To use united mode, you must follow these general steps:

1.  In the CDB root, configure the database to use united mode by setting the `WALLET_ROOT` and `TDE_CONFIGURATION` parameters.

    The `WALLET_ROOT` parameter sets the location for the wallet directory and the `TDE_CONFIGURATION` parameter sets the type of keystore to use.

2.  Restart the database so that these settings take effect.

3.  In the CDB root, create the keystore, open the keystore, and then create the TDE master encryption key.

4.  In each united mode PDB, perform TDE master encryption key tasks as needed, such as opening the keystore locally in the united mode PDB and creating the TDE master encryption key for the PDB. Remember that the keystore is managed by the CDB root, but must contain a TDE master encryption key that is specific to the PDB for the PDB to be able to use TDE.

When you run `ADMINISTER KEY MANAGEMENT` statements in united mode from the CDB root, if the statement accepts the `CONTAINER` clause, and if you set it to `ALL`, then the statement applies only to the CDB root and its associated united mode PDBs. Any PDB that is in isolated mode is not affected.

**Parent topic:** Managing Keystores and TDE Master Encryption Keys in United Mode

### 6.2 Operations That Are Allowed in United Mode

Many `ADMINISTER KEY MANAGEMENT` operations performed in the CDB root apply to keystores and encryption keys in the united mode PDB.

#### Available United Mode-Related Operations in a CDB Root

Table 6-1 describes the `ADMINISTER KEY MANAGEMENT` operations that you can perform in the CDB root.

Table 6-1 ADMINISTER KEY MANAGEMENT United Mode Operations in a CDB Root

| Operation                                                                                       | Syntax                                                                                                                                                                                                                                                                                                                              | United Mode Notes                                                                                                                                                                                                                                                                                                                              |
|:------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Creating a keystore                                                                             | `ADMINISTER KEY MANAGEMENT`<br>`CREATE KEYSTORE `<br>`IDENTIFIED BY keystore_password;`                                                                                                                                                                                                                                             | After you create the keystore in the CDB root, by default it is available in the united mode PDBs. Do not include the `CONTAINER` clause.                                                                                                                                                                                                      |
| Opening a keystore                                                                              | `ADMINISTER KEY MANAGEMENT `<br>`SET KEYSTORE OPEN`<br>`IDENTIFIED BY`<br>`[EXTERNAL STORE | keystore_password]`<br>`[CONTAINER = ALL | CURRENT];`                                                                                                                                                                                  | In this operation, the `EXTERNAL STORE` clause fetches the keystore password from the SSO wallet located in the `WALLET_ROOT``/tde_seps` directory.                                                                                                                                                                                            |
| Changing a keystore password                                                                    | `ADMINISTER KEY MANAGEMENT `<br>`ALTER KEYSTORE PASSWORD`<br>`IDENTIFIED BY old_keystore_password`<br>`SET new_keystore_password WITH BACKUP `<br>`[USING 'backup_identifier'];`                                                                                                                                                    | Do not include the `CONTAINER` clause.                                                                                                                                                                                                                                                                                                         |
| Backing up a keystore                                                                           | `ADMINISTER KEY MANAGEMENT`<br>`BACKUP KEYSTORE `<br>`[USING 'backup_identifier']`<br>`[FORCE KEYSTORE]`<br>`IDENTIFIED BY [EXTERNAL STORE | keystore_password]`<br>`[TO 'keystore_location'];`                                                                                                                                     | Do not include the `CONTAINER` clause.                                                                                                                                                                                                                                                                                                         |
| Closing a keystore without force                                                                | `ADMINISTER KEY MANAGEMENT `<br>`SET KEYSTORE CLOSE`<br>`[IDENTIFIED BY [EXTERNAL STORE | keystore_password]]`<br>`[CONTAINER = ALL | CURRENT];`                                                                                                                                                                                    | \-                                                                                                                                                                                                                                                                                                                                             |
| Closing a keystore with force                                                                   | `ADMINISTER KEY MANAGEMENT `<br>`FORCE KEYSTORE CLOSE`<br>`[IDENTIFIED BY [EXTERNAL STORE | keystore_password]]`<br>`[CONTAINER = ALL | CURRENT];`                                                                                                                                                                                  | \-                                                                                                                                                                                                                                                                                                                                             |
| Creating and activating a new TDE master encryption key (rekeying)                              | `ADMINISTER KEY MANAGEMENT`<br>`SET [ENCRYPTION] KEY`<br>`[FORCE KEYSTORE]`<br>`[USING TAG 'tag_name']`<br>`IDENTIFIED BY [EXTERNAL STORE | keystore_password]`<br>`WITH BACKUP [USING 'backup_identifier']`<br>`[CONTAINER = ALL | CURRENT]`                                                                                       | \-                                                                                                                                                                                                                                                                                                                                             |
| Creating a user-defined TDE master encryption key for either now (`SET`) or later on (`CREATE`) | `ADMINISTER KEY MANAGEMENT [SET | CREATE] [ENCRYPTION] KEY`<br>`'mkid:mk | mk' `<br>`[USING ALGORITHM 'algorithm'] `<br>`[FORCE KEYSTORE]`<br>`[USING TAG 'tag_name']`<br>`IDENTIFIED BY [EXTERNAL STORE | keystore_password]`<br>`[WITH BACKUP [USING 'backup_identifier']]`<br>`[CONTAINER = CURRENT];`                           | \-                                                                                                                                                                                                                                                                                                                                             |
| Activating an existing TDE master encryption key                                                | `ADMINISTER KEY MANAGEMENT `<br>`USE [ENCRYPTION] KEY 'key_id' `<br>`IDENTIFIED BY [EXTERNAL STORE | keystore_password]`<br>`WITH BACKUP `<br>`[USING 'backup_identifier'];`                                                                                                                                                        | Do not include the `CONTAINER` clause.                                                                                                                                                                                                                                                                                                         |
| Tagging a TDE master encryption key                                                             | `ADMINISTER KEY MANAGEMENT `<br>`SET TAG 'tag' FOR 'key_id'`<br>`IDENTIFIED BY [EXTERNAL STORE | keystore_password ]`<br>`WITH BACKUP `<br>`[USING 'backup_identifier'];`                                                                                                                                                           | Do not include the `CONTAINER` clause.                                                                                                                                                                                                                                                                                                         |
| Moving a TDE master encryption key to a new keystore                                            | `ADMINISTER KEY MANAGEMENT `<br>`MOVE [ENCRYPTION] KEYS`<br>`TO NEW KEYSTORE 'keystore_location1'`<br>`IDENTIFIED BY keystore1_password`<br>`FROM [FORCE] KEYSTORE`<br>`IDENTIFIED BY keystore_password`<br>`[WITH IDENTIFIER IN`<br>`{ 'key_id' [, 'key_id' ]... | ( subquery ) } ]`<br>`WITH BACKUP [USING 'backup_identifier'];` | You can only move the master encryption key to a keystore that is within the same container (for example, between keystores in the CDB root or between keystores in the same PDB). You cannot move the master encryption key from a keystore in the CDB root to a keystore in a PDB, and vice versa.<br>Do not include the `CONTAINER` clause. |

#### Available Operations in a United Mode PDB

Table 6-2 describes the `ADMINISTER KEY MANAGEMENT` operations that you can perform in a united mode PDB.

Table 6-2 ADMINISTER KEY MANAGEMENT United Mode PDB Operations

| Operation                                                                                                                                                                                                                                                           | Syntax                                                                                                                                                                                                                                                                                                                                   | United Mode Notes                                                                                                                                                                            |
|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Opening a keystore                                                                                                                                                                                                                                                  | `ADMINISTER KEY MANAGEMENT`<br>`SET KEYSTORE CLOSE`<br>`[IDENTIFIED BY EXTERNAL STORE | keystore_password]`<br>`[CONTAINER = CURRENT];`                                                                                                                                                                                                  | In this operation, the `EXTERNAL_STORE` clause uses the password in the Secure Sockets Layer (SSL) wallet. This wallet is located in the `tde_seps` directory in the `WALLET_ROOT` location. |
| Closing a keystore without force                                                                                                                                                                                                                                    | `ADMINISTER KEY MANAGEMENT `<br>`SET KEYSTORE CLOSE`<br>`[IDENTIFIED BY keystore_password]`<br>`[CONTAINER = CURRENT];`                                                                                                                                                                                                                  | \-                                                                                                                                                                                           |
| Closing a keystore with force                                                                                                                                                                                                                                       | `ADMINISTER KEY MANAGEMENT `<br>`FORCE KEYSTORE CLOSE`<br>`IDENTIFIED BY`<br>`[EXTERNAL STORE | keystore_password]`<br>`[CONTAINER = CURRENT];`                                                                                                                                                                                          | \-                                                                                                                                                                                           |
| Creating and activating a new TDE master encryption key (rekeying or rotating)                                                                                                                                                                                      | `ADMINISTER KEY MANAGEMENT`<br>`SET [ENCRYPTION] KEY`<br>`[FORCE KEYSTORE]`<br>`[USING TAG 'tag_name']`<br>`IDENTIFIED BY EXTERNAL STORE | keystore_password`<br>`WITH BACKUP [USING 'backup_identifier']`<br>`[CONTAINER = CURRENT];`                                                                                                   | \-                                                                                                                                                                                           |
| Creating a user-defined TDE master encryption key for use either now (`SET`) or later on (`CREATE`)                                                                                                                                                                 | `ADMINISTER KEY MANAGEMENT SET | CREATE [ENCRYPTION] KEY`<br>`'mkid:mk | mk'`<br>`[USING ALGORITHM 'algorithm']`<br>`[FORCE KEYSTORE]`<br>`[USING TAG 'tag']`<br>`IDENTIFIED BY EXTERNAL STORE | keystore_password`<br>`WITH BACKUP [USING 'backup_identifier']`<br>`[CONTAINER = CURRENT];`                                             | \-                                                                                                                                                                                           |
| Activating an existing TDE master encryption key                                                                                                                                                                                                                    | `ADMINISTER KEY MANAGEMENT`<br>`USE [ENCRYPTION] KEY 'key_id'`<br>`IDENTIFIED BY`<br>`EXTERNAL STORE | keystore_password`<br>`WITH BACKUP`<br>`[USING 'backup_identifier'];`                                                                                                                                                             | Do not include the `CONTAINER` clause.                                                                                                                                                       |
| Tagging a TDE master encryption key                                                                                                                                                                                                                                 | `ADMINISTER KEY MANAGEMENT`<br>`SET TAG 'tag' FOR 'key_id'`<br>`[FORCE KEYSTORE]`<br>`IDENTIFIED BY EXTERNAL STORE | keystore_password`<br>`WITH BACKUP [USING 'backup_identifier'];`                                                                                                                                                    | Do not include the `CONTAINER` clause.                                                                                                                                                       |
| Moving an encryption key to a new keystore                                                                                                                                                                                                                          | `ADMINISTER KEY MANAGEMENT`<br>`MOVE [ENCRYPTION] KEYS`<br>`TO NEW KEYSTORE 'new_keystore_location'`<br>`IDENTIFIED BY new_keystore_password`<br>`FROM [FORCE] KEYSTORE`<br>`IDENTIFIED BY keystore_password`<br>`[WITH IDENTIFIER IN`<br>`{ 'key_id' [, 'key_id' ]... | ( subquery ) } ]`<br>`WITH BACKUP [USING 'backup_identifier'];` | Do not include the `CONTAINER` clause.                                                                                                                                                       |
| Moving a key from a united mode keystore in the CDB root to an isolated mode keystore in a PDB                                                                                                                                                                      | `ADMINISTER KEY MANAGEMENT`<br>`ISOLATE KEYSTORE`<br>`IDENTIFIED BY isolated_keystore_password`<br>`FROM ROOT KEYSTORE`<br>`[FORCE KEYSTORE]`<br>`IDENTIFIED BY`<br>`EXTERNAL STORE | united_keystore_password`<br>`WITH BACKUP [USING backup_id];`                                                                                      | Do not include the `CONTAINER` clause.                                                                                                                                                       |
| Using the `FORCE` clause when a clone of a PDB is using the TDE master encryption key that is being isolated; then copying (rather than moving) the TDE master encryption keys from the keystore that is in the CDB root into the isolated mode keystore of the PDB | `ADMINISTER KEY MANAGEMENT `<br>`FORCE ISOLATE KEYSTORE`<br>`IDENTIFIED BY isolated_keystore_password`<br>`FROM ROOT KEYSTORE`<br>`[FORCE KEYSTORE]`<br>`IDENTIFIED BY`<br>`[EXTERNAL STORE | united_keystore_password]`<br>`[WITH BACKUP [USING backup_id]];`                                                                           | \-                                                                                                                                                                                           |

**Parent topic:** Managing Keystores and TDE Master Encryption Keys in United Mode

### 6.3 Operations That Are Not Allowed in a United Mode PDB

`ADMINISTER KEY MANAGEMENT` operations that are not allowed in a united mode PDB can be performed in the CDB root.

These operations are as follows:

- Keystore operations:

  - Performing merge operations on keystores

  - Exporting a keystore

  - Importing a keystore

  - Migrating a keystore

  - Reverse-migrating a keystore

  - Moving the keys of a keystore that is in the CDB root into the keystores of a PDB

  - Moving the keys from a PDB into a united mode keystore that is in the CDB root

- Encryption key operations:

  - Using the `CONTAINER = ALL` clause to create a new TDE master encryption key for later user in each pluggable database (PDB)

- Client secret operations:

  - Adding client secrets

  - Updating client secrets

  - Deleting client secrets

**Parent topic:** Managing Keystores and TDE Master Encryption Keys in United Mode

### 6.4 Configuring United Mode with the Initialization Parameter File and ALTER SYSTEM

If your environment relies on server parameter files (`spfile`), then you can set `WALLET_ROOT` and `TDE_CONFIGURATION` using `ALTER SYSTEM SET` with `SCOPE`.

1.  Log in to the server where the CDB root of the Oracle database resides.
2.  If necessary, create a wallet directory.
    This directory cannot contain any wallets. Oracle recommends that you create a directory outside of` $ORACLE_HOME` or `$ORACLE_BASE`, to avoid backing up the keystore (wallet or Oracle Key Vault installation tree) with the encrypted database during an operating system-level backup.
3.  Edit the initialization parameter file to include the `WALLET_ROOT` static initialization parameter for the wallet directory.
    By default, the initialization parameter file is located in the `$ORACLE_HOME/dbs` directory.
    For example, for a database instance named `orcl`:
        wallet_root=$ORACLE_BASE/admin/orcl/wallet
4.  Log in to the CDB root as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
5.  Restart the database.
        SHUTDOWN IMMEDIATE
        STARTUP

    To start the database by pointing to the location of the initialization file where you added the `WALLET_ROOT` setting, issue a `STARTUP` command similar to the following:

        STARTUP PFILE = /u01/oracle/dbs/init.ora
6.  Check the `WALLET_ROOT` setting.
        SHOW PARAMETER WALLET_ROOT

    The `VALUE` column of the output should show the absolute path location of the `wallet` directory.

    For example:
        wallet_root string /etc/ORACLE/KEYSTORES/finance
7.  Set the `TDE_CONFIGURATION` dynamic initialization parameter to specify the keystore type, using the following syntax:
        ALTER SYSTEM SET TDE_CONFIGURATION="KEYSTORE_CONFIGURATION=keystore_type"
        SCOPE=scope_type;

    In this specification:

    - `keystore_type` can be one of the following settings:

      - `FILE` configures a TDE keystore.

      - `OKV` configures an Oracle Key Vault keystore.

    - `scope_type` sets the type of scope (for example, `both`, `memory`, `spfile`, `pfile`.

    For example, to configure a TDE keystore if the parameter file (`pfile`) is in use, set `scope` to `memory`:

        ALTER SYSTEM SET TDE_CONFIGURATION="KEYSTORE_CONFIGURATION=FILE"
        SCOPE=memory;

    To configure a TDE keystore if the server parameter file (`spfile`) is in use, set scope to `both`:

        ALTER SYSTEM SET TDE_CONFIGURATION="KEYSTORE_CONFIGURATION=FILE"
        SCOPE=both;
8.  Check the `TDE_CONFIGURATION` parameter setting.
        SHOW PARAMETER TDE_CONFIGURATION

    The `VALUE` column should show the keystore type, prepended with `KEYSTORE_CONFIGURATION=`.
9.  Confirm that the `TDE_CONFIGURATION` parameter was set correctly.
        SELECT CON_ID, KEYSTORE_MODE FROM V$ENCRYPTION_WALLET;

    The output should be similar to the following:
            CON_ID KEYSTORE
        ---------- --------
                 1 NONE
                 2 UNITED
                 3 UNITED
                 4 UNITED
                 5 UNITED

    The CDB root (`CON_ID 1`) will always be in the `NONE` state, and at this stage, the remaining `CON_ID`s should be set to `UNITED`. PDBs can be either `UNITED` or `ISOLATED`, depending on how you configure them. When you query the `V$ENCRYPTION_WALLET` view, if the `ORA-46691: The value of the KEYSTORE_CONFIGURATION attribute is invalid` error appears, then check the initialization parameter file where you added this setting.

After you configure united mode, you can create keystores and master encryption keys, and when these are configured, you can encrypt data.

**Parent topic:** Managing Keystores and TDE Master Encryption Keys in United Mode

### 6.5 Configuring a Software Keystore for Use in United Mode

In united mode, the software keystore resides in the CDB root but the master keys from this keystore are available for the PDBs that have their keystore in united mode.

- About Configuring a Software Keystore in United Mode
  In united mode, the keystore that you create in the CDB root will be accessible by the united mode PDBs.
- Creating a Password-Protected TDE Wallet
  In united mode, you must create the keystore in the CDB root.
- Step 2: Open the TDE Wallet in a United Mode PDB
  To open a TDE wallet in united mode, you must use the `ADMINISTER KEY MANAGEMENT` statement with the `SET KEYSTORE OPEN` clause.
- Step 3: Set the TDE Master Encryption Key in the TDE Wallet in United Mode
  To set the TDE master encryption key in the TDE wallet when the PDB is configured in united mode, use the `ADMINISTER KEY MANAGEMENT` statement with the `SET KEY` clause.

**Parent topic:** Managing Keystores and TDE Master Encryption Keys in United Mode

#### 6.5.1 About Configuring a Software Keystore in United Mode

In united mode, the keystore that you create in the CDB root will be accessible by the united mode PDBs.

In general, to configure a united mode software keystore after you have enabled united mode, you create and open the keystore in the CDB root, and then create a master encryption key for this keystore. Afterward, you can begin to encrypt data for tables and tablespaces that will be accessible throughout the CDB environment.

The `V$ENCRYPTION_WALLET` dynamic view describes the status and location of the keystore. For example, the following query shows the open-closed status and the keystore location of the CDB root keystore (`CON_ID 1`) and its associated united mode PDBs. The `WRL_PARAMETER` column shows the CDB root keystore location being in the `$ORACLE_BASE/wallet/tde` directory.

    SELECT CON_ID, STATUS, WRL_PARAMETER FROM V$ENCRYPTION_WALLET;

    CON_ID STATUS WRL_PARAMETER
    ------ ------ -----------------------------
         1 OPEN   /app/oracle/wallet/tde/
         2 CLOSED
         3 OPEN
         4 OPEN
         5 OPEN

In this output, there is no keystore path listed for the other PDBs in this CDB because these PDBs use the keystore in the CDB root. If any of these PDBs are isolated and you create a keystore in the isolated mode PDB, then when you perform this query, the `WRL_PARAMETER` column will show the keystore path for the isolated mode PDB.

You can create a secure external store for the software keystore. This feature enables you to hide the password from the operating system: it removes the need for storing clear-text keystore passwords in scripts or other tools that can access the database without user intervention, such as overnight batch scripts. The location for this keystore is set by the `EXTERNAL_KEYSTORE_CREDENTIAL_LOCATION` initialization parameter. In a multitenant environment, different PDBs can access this external store location when you run the `ADMINISTER KEY MANAGEMENT` statement using the `IDENTIFIED BY EXTERNAL STORE` clause. This way, you can centrally locate the password and then update it only once in the external store.

**Parent topic:** Configuring a Software Keystore for Use in United Mode

#### 6.5.2 Creating a Password-Protected TDE Wallet

In united mode, you must create the keystore in the CDB root.

After you create this TDE wallets in the CDB root, it becomes available in any united mode PDB, but not in any isolated mode PDBs.

1.  Connect to the CDB root as a common user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
    For example:
        CONNECT c##sec_admin AS SYSKM
        Enter password: password
2.  Use the `SHOW PARAMETER` command to confirm that `WALLET_ROOT` is set, and `TDE_CONFIGURATION` is set to `KEYSTORE_CONFIGURATION=FILE`.
3.  Run the `ADMINISTER KEY MANAGEMENT` SQL statement to create the keystore using the following syntax:
        ADMINISTER KEY MANAGEMENT CREATE KEYSTORE
        IDENTIFIED BY TDE_wallet_password;

    The `/tde` directory is automatically created under `WALLET_ROOT`, if it does not already exist. In Oracle Automatic Storage Management (Oracle ASM), for the `/tde` directory to be automatically created if it does not already exist, `WALLET_ROOT` must point to `+DATA/ORACLE_UNQNAME`.

    In this specification, `TDE_wallet_password` is the password of the TDe wallet that you, the security administrator, creates.

    For example, to create the TDE wallet in the `WALLET_ROOT``/tde` directory:

        ADMINISTER KEY MANAGEMENT CREATE KEYSTORE IDENTIFIED BY TDE_wallet_password;

        keystore altered.

    After you run this statement, the `ewallet.p12` file, which is the TDE wallet, appears in the wallet location.

After you complete these steps, the `ewallet.p12` file, which contains the keystore, appears in the designated keystore location. For example, if you had set the `WALLET_ROOT` parameter to `$ORACLE_BASE/wallet` and the `TDE_CONFIGURATION` parameter to `FILE` (for TDE, which creates a `tde` directory in the wallet root location), then the keystore will be created in the `/etc/ORACLE/KEYSTORES/${ORACLE_SID}/tde` directory. The name of the TDE wallet is `ewallet.p12`.

**Related Topics**

- [Configuring an External Store for a Keystore Password](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Configuring a Software Keystore for Use in United Mode

#### 6.5.3 Step 2: Open the TDE Wallet in a United Mode PDB

To open a TDE wallet in united mode, you must use the `ADMINISTER KEY MANAGEMENT` statement with the `SET KEYSTORE OPEN` clause.

1.  Connect to the CDB root as a common user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Open the TDE wallet in the CDB root.
    For example:
        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN
        IDENTIFIED BY password;

        keystore altered.

    If the CDB is configured with the TDE wallet password stored in `WALLET_ROOT``/tde_seps` and has a (local) auto-login TDE wallet in `WALLET_ROOT``/tde`, you must include the `FORCE KEYSTORE` clause and the `IDENTIFIED BY EXTERNAL STORE` clause in the `ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN` statement, as follows:

        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN
        FORCE KEYSTORE
        IDENTIFIED BY EXTERNAL STORE;

        keystore altered.

    If the `WALLET_ROOT` parameter has been set, then Oracle Database finds the external store in the `WALLET_ROOT``/tde_seps` directory.
3.  Ensure that the PDB in which you want to open the TDE wallet is in `READ WRITE` mode.
    For example:
        SHOW PDBS

        CON_ID CON_NAME   OPEN MODE    RESTRICTED
        ------ ---------- ------------ -----------
        2      PDB$SEED   READ ONLY    NO
        3      CDB1_PDB1  READ WRITE   NO

    If any PDB has an `OPEN MODE` value that is different from `READ WRITE`, then run the following statement to open the PDB, which will set it to `READ WRITE` mode:

        ALTER PLUGGABLE DATABASE CDB1_PDB1 OPEN;

    Now the TDE wallet can be opened in both the CDB root and the PDB.
4.  Connect to the PDB.
5.  Run the `ADMINISTER KEY MANAGEMENT` statement to open the TDE wallet.
        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN
        IDENTIFIED BY password | EXTERNAL STORE;
        keystore altered.

    To open a password-protected TDE wallet when a (local) auto-login TDE wallet is open, specify the `FORCE KEYSTORE` clause as follows.

        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN
        FORCE KEYSTORE
        IDENTIFIED BY TDE_wallet_password | EXTERNAL STORE;
        keystore altered.

    `FORCE KEYSTORE` is also useful for databases that are heavily loaded. The `IDENTIFIED BY EXTERNAL STORE` clause is included in the statement because the TDE wallet credentials exist in an external store. This enables the password-protected TDE wallet to be opened without specifying the TDE wallet password within the statement itself.

    If the `WALLET_ROOT` parameter has been set in the CDB, then united PDBs find the external store in the `WALLET_ROOT``/tde_seps` directory.
6.  Confirm that the TDE wallet is open.
        SELECT STATUS FROM V$ENCRYPTION_WALLET;

Note that if the TDE wallet is open but you have not created a TDE master encryption key yet, the `STATUS` column of the `V$ENCRYPTION_WALLET` view reminds you with an` OPEN_NO_MASTER_KEY` status.

**Parent topic:** Configuring a Software Keystore for Use in United Mode

#### 6.5.4 Step 3: Set the TDE Master Encryption Key in the TDE Wallet in United Mode

To set the TDE master encryption key in the TDE wallet when the PDB is configured in united mode, use the `ADMINISTER KEY MANAGEMENT` statement with the `SET KEY` clause.

1.  Log in to the CDB root or to the PDB that is configured for united mode as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Ensure that the database is open in `READ WRITE` mode.
    To find the status, run the `show pdbs` command.
3.  Run the `ADMINISTER KEY MANAGEMENT SET ENCRYPTION KEY` statement to create or rekey the TDE master encryption key in the TDE wallet.
    For example, if the TDE wallet is password-protected and open, and you want to create or rekey the TDE master encryption key in the current container:
        ADMINISTER KEY MANAGEMENT SET KEY
        IDENTIFIED BY keystore_password
        WITH BACKUP USING 'emp_key_backup';

        keystore altered.

    If the keystore is closed:

        ADMINISTER KEY MANAGEMENT SET KEY
        FORCE KEYSTORE
        IDENTIFIED BY keystore_password
        WITH BACKUP USING 'emp_key_backup';

        keystore altered.

    In this specification:

    - `FORCE KEYSTORE` should be included if the TDE wallet is closed. This automatically opens the keystore before setting the TDE master encryption key. The `FORCE KEYSTORE` clause also switches over to opening the password-protected TDE wallet when an auto-login keystore is configured and is currently open.

    - `IDENTIFIED BY` specifies the TDE wallet password. Alternatively, if the TDE wallet password is in an external store, you can use the `IDENTIFIED BY EXTERNAL STORE` clause.
4.  Confirm that the TDE master encryption key is set.
        SELECT MASTERKEY_ACTIVATED FROM V$DATABASE_KEY_INFO;

    The output should be `YES`.

**Related Topics**

- [About Setting the TDE Wallet TDE Master Encryption Key](configuring-transparent-data-encryption.md)

**Parent topic:** Configuring a Software Keystore for Use in United Mode

### 6.6 Configuring a Container Database with United Mode PDBs for Oracle Key Vault

The TDE master keys of all united mode PDBs and the CDB reside in the same virtual wallet in Oracle Key Vault.

- About Configuring a Container Database with United Mode PDBs for Oracle Key Vault
  In united mode, you can configure Oracle Key Vault by setting the `WALLET_ROOT` and `TDE_CONFIGURATION` parameters in the container database (CDB).
- Step 1: Configure Oracle Key Vault for United Mode
  You can configure Oracle Key Vault for united mode PDBs by setting the `WALLET_ROOT` and `TDE_CONFIGURATION` parameters in the container database (CDB).
- Step 2: Open the Connection to Oracle Key Vault
  After you have configured the database to use Oracle Key Vault for TDE key management, you must open the connection to Oracle Key Vault before you can use it.
- Step 3: Set the TDE Master Encryption Key in Oracle Key Vault
  After you have opened the connection to Oracle Key Vault, you are ready to set the TDE master encryption key.
- Step 4: Encrypt Your Data in United Mode
  Now that you have completed the configuration for an external keystore or for an Oracle Key Vault keystore, you can begin to encrypt data.

**Parent topic:** Managing Keystores and TDE Master Encryption Keys in United Mode

#### 6.6.1 About Configuring a Container Database with United Mode PDBs for Oracle Key Vault

In united mode, you can configure Oracle Key Vault by setting the `WALLET_ROOT` and `TDE_CONFIGURATION` parameters in the container database (CDB).

Oracle recommends that you set the parameters `WALLET_ROOT` and `TDE_CONFIGURATION` for new deployments. Alternatively, you can migrate from the old configuration in the `sqlnet.ora file` to the new configuration with `WALLET_ROOT` and `TDE_CONFIGURATION` at your earliest convenience (for example, the next time you apply a quarterly bundle patch).

United Mode is the default TDE setup that is used in Oracle Database release 12.1.0.2 and later with the TDE configuration in `sqlnet.ora`. In Oracle Database release 18c and later, TDE configuration in `sqlnet.ora` is deprecated. You must first set the static initialization parameter `WALLET_ROOT` to an existing directory; for this change to be picked up, a database restart is necessary. After the restart, set the `KEYSTORE_CONFIGURATION` attribute of the dynamic `TDE_CONFIGURATION` parameter to `OKV` (for a password-protected connection into Oracle Key Vault), or `OKV|FILE` for an auto-open connection into Oracle Key Vault, and then open the configured external keystore, and then set the TDE master encryption keys. After you complete these tasks, you can begin to encrypt data in your database.

**Parent topic:** Configuring a Container Database with United Mode PDBs for Oracle Key Vault

#### 6.6.2 Step 1: Configure Oracle Key Vault for United Mode

You can configure Oracle Key Vault for united mode PDBs by setting the `WALLET_ROOT` and `TDE_CONFIGURATION` parameters in the container database (CDB).

1.  If the `WALLET_ROOT` parameter is set, then install the Oracle Key Vault client software into the `WALLET_ROOT/okv` directory.
2.  Log in to the database instance as a user who has been granted the `ALTER SYSTEM` administrative privilege.
3.  Set the `TDE_CONFIGURATION` dynamic initialization parameter to specify the keystore type by using the following syntax:
        ALTER SYSTEM SET TDE_CONFIGURATION="KEYSTORE_CONFIGURATION=keystore_type" SCOPE=BOTH SID = '*';

    In this specification:

    - `keystore_type` is `OKV`, to configure an Oracle Key Vault keystore.

    For example, to configure your database to use Oracle Key Vault:

        ALTER SYSTEM SET TDE_CONFIGURATION="KEYSTORE_CONFIGURATION=OKV"
        SCOPE=BOTH SID = '*";

**Parent topic:** Configuring a Container Database with United Mode PDBs for Oracle Key Vault

#### 6.6.3 Step 2: Open the Connection to Oracle Key Vault

After you have configured the database to use Oracle Key Vault for TDE key management, you must open the connection to Oracle Key Vault before you can use it.

- About Opening the Connection to Oracle Key Vault
  You must open the connection to Oracle Key Vault so that it is accessible to the database before you can perform any encryption or decryption.
- Opening the Oracle Key Vault Connection in a United Mode PDB
  To open the Oracle Key Vault connection in united mode, you must use the `ADMINISTER KEY MANAGEMENT` statement with the `SET KEYSTORE OPEN` clause.

**Parent topic:** Configuring a Container Database with United Mode PDBs for Oracle Key Vault

##### 6.6.3.1 About Opening the Connection to Oracle Key Vault

You must open the connection to Oracle Key Vault so that it is accessible to the database before you can perform any encryption or decryption.

If a recovery operation is needed on your database (for example, if the database was not cleanly shut down, and has an encrypted tablespace that needs recovery), then you must open the connection to Oracle Key Vault before you can open the database itself.

There are two ways that you can open the Oracle Key Vault connection:

- Manually open the keystore by issuing the `ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN` statement. Afterward, you can perform the operation.

- Include the `FORCE KEYSTORE` clause in the `ADMINISTER KEY MANAGEMENT` statement. `FORCE KEYSTORE` temporarily opens the keystore for the duration of the operation, and when the operation completes, the keystore is closed again. `FORCE KEYSTORE` is useful for situations when the database is heavily loaded. In this scenario, because of concurrent access to encrypted objects in the database, the auto-login keystore continues to open immediately after it has been closed but before a user has had a chance to open the password-based keystore.

To check the status of the keystore, query the `STATUS` column of the `V$ENCRYPTION_WALLET` view. Keystores can be in the following states: `CLOSED`, `NOT_AVAILABLE` (that is, not present in the `WALLET_ROOT` location), `OPEN`, `OPEN_NO_MASTER_KEY`, `OPEN_UNKNOWN_MASTER_KEY_STATUS`.

Be aware that for external keystores, if the database is in the mounted state, then it cannot check if the master key is set because the data dictionary is not available. In this situation, the status will be `OPEN_UNKNOWN_MASTER_KEY_STATUS`.

**Related Topics**

- How Keystore Open and Close Operations Work in United Mode

**Parent topic:** Step 2: Open the Connection to Oracle Key Vault

##### 6.6.3.2 Opening the Oracle Key Vault Connection in a United Mode PDB

To open the Oracle Key Vault connection in united mode, you must use the `ADMINISTER KEY MANAGEMENT` statement with the `SET KEYSTORE OPEN` clause.

1.  Connect to the CDB root as a common user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Open the keystore in the CDB root by using the following syntax.
        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN
        IDENTIFIED BY EXTERNAL STORE | "Oracle_Key_Vault_password"
        [CONTAINER = ALL | CURRENT];

    In this specification:

    - `IDENTIFIED BY` can be one of the following settings:

      - `EXTERNAL STORE` uses the keystore password stored in the external store to perform the keystore operation.

      - `Oracle_Key_Vault_password` is the Oracle Key Vault password that was giving during the Oracle Key Vault client installation. If no password was given, then the password in the `ADMINISTER KEY MANAGEMENT` statement becomes `NULL`. Enclose this password in double quotation marks.

    - `CONTAINER` specifies the scope in which to open the Oracle Key Vault connection.

      - `ALL` opens the connection to Oracle Key Vault for the root container and all open united PDBs.
      - `CURRENT` opens the connection to Oracle Key Vault for the root container.

    If the password contains a semi-colon (`;`), then enclose the password in double quotation marks.

        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN
        IDENTIFIED BY "Oracle_Key_Vault_password";
3.  Ensure that the PDB in which you want to open the keystore is in `READ WRITE` mode.
4.  Connect to the PDB and run the `ADMINISTER KEY MANAGEMENT` statement to open the keystore.
    For example:
        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN
        IDENTIFIED BY "external_key_manager_password";
5.  Confirm that the keystore is open.
        SELECT STATUS FROM V$ENCRYPTION_WALLET;
6.  Repeat this procedure each time you restart the PDB.

**Parent topic:** Step 2: Open the Connection to Oracle Key Vault

#### 6.6.4 Step 3: Set the TDE Master Encryption Key in Oracle Key Vault

After you have opened the connection to Oracle Key Vault, you are ready to set the TDE master encryption key.

- About Setting the External Keystore TDE Master Encryption Key
  You must create a TDE master encryption key that is stored inside the external keystore.
- Heartbeat Batch Size for External Keystores
  You can control the size of the batch of heartbeats issued during each heartbeat period.
- Setting the TDE Master Encryption Key in the United Mode External Keystore
  To set the TDE master encryption key in the keystore when the PDB is configured in united mode, use the `ADMINISTER KEY MANAGEMENT` statement with the `SET KEY` clause.
- Migration of an Encrypted Database from a TDE Wallet to Oracle Key Vault or OCI KMS
  To switch from a TDE wallet to centralized key management with Oracle Key Vault or Oracle Cloud Infrastructure (OCI) Key Management Service (KMS), after you upload all current and retired TDE master keys you must migrate the database from the TDE wallet to Oracle Key Vault or OCI KMS.

**Parent topic:** Configuring a Container Database with United Mode PDBs for Oracle Key Vault

##### 6.6.4.1 About Setting the External Keystore TDE Master Encryption Key

You must create a TDE master encryption key that is stored inside the external keystore.

Oracle Database uses the master encryption key from Oracle Key Vault or Oracle Cloud Infrastructure (OCI) Key Management Service (KMS) to encrypt or decrypt TDE table keys or tablespace encryption keys (data encryption keys) inside the database.

If you have not previously configured TDE with a wallet, then you must set the master encryption key in Oracle Key Vault or OCI KMS. If you have already configured TDE with a wallet, then you must migrate the database to Oracle Key Vault or OCI KMS.

Along with the current master encryption key, all TDE keystores (TDE wallet, Oracle Key Vault, and OCI KMS) maintain historical master encryption keys that are generated after every re-key operation that rekeys the master encryption key. These historical master keys help to restore Oracle Database backups that were taken previously using one of the master encryption keys. Only Oracle Key Vault allows you to upload all historical key from a TDE wallet before migrating the database to use Oracle Key Vault. After migration to Oracle Key Vault, the TDE wallet can be deleted, which satisfies security regulation that mandate that encryption keys cannot reside on the encrypting server.

**Parent topic:** Step 3: Set the TDE Master Encryption Key in Oracle Key Vault

##### 6.6.4.2 Heartbeat Batch Size for External Keystores

You can control the size of the batch of heartbeats issued during each heartbeat period.

When a PDB is configured to use an external key manager, the `GEN0` background process must perform a heartbeat request on behalf of the PDB to the external key manager. This background process ensures that the external key manager is available and that the TDE master encryption key of the PDB is available from the external key manager and can be used for both encryption and decryption. The `GEN0` background process must complete this request within the heartbeat period (which defaults to three seconds).

When a very large number of PDBs (for example, 1000) are configured to use an external key manager, you can configure the `HEARTBEAT_BATCH_SIZE` database instance initialization parameter to batch heartbeats and thereby mitigate the possibility of the hang analyzer mistakenly flagging the `GEN0` process as being stalled when there was not enough time for it to perform a heartbeat for each PDB within the allotted heartbeat period.

By setting the heartbeat batch size, you can stagger the heartbeats across batches of PDBs to ensure that for each batch a heartbeat can be completed for each PDB within the batch during the heartbeat period, and also ensure that PDB master encryption keys can be reliably fetched from an Oracle Key Vault server and cached in the Oracle Key Vault persistent cache. The `HEARTBEAT_BATCH_SIZE` parameter configures the size of the batch of heartbeats sent per heartbeat period to the external key manager. The value must be between 2 and 100 and it defaults to 5. The default duration of the heartbeat period is three seconds.

For example, if 500 PDBs are configured and are using Oracle Key Vault, the usual time taken by `GEN0` to perform a heartbeat on behalf of a single PDB is less than half a second. In addition, assume that the `CDB$ROOT` has been configured to use an external key manager such as Oracle Key Vault (`OKV`). Therefore, it should generally be possible to send five heartbeats (one for the `CDB$ROOT` and four for a four-PDB batch) in a single batch within every three-second heartbeat period.

Even though the `HEARTBEAT_BATCH_SIZE` parameter configures the number of heartbeats sent in a batch, if the `CDB$ROOT` is configured to use an external key manager, then each heartbeat batch must include a heartbeat for the `CDB$ROOT`. The minimum value of the `HEARTBEAT_BATCH_SIZE` parameter is 2 and its maximum value is 100. When the `CDB$ROOT` is configured to use an external key manager, then each batch of heartbeats includes one heartbeat for the `CDB$ROOT`. This is why the minimum batch size is two: one must be reserved for the `CDB$ROOT`, because it might be configured to use an external key manager.

For example, suppose you set the `HEARTBEAT_BATCH_SIZE` parameter as follows:

    ALTER SYSTEM SET HEARTBEAT_BATCH_SIZE=3 SCOPE=BOTH SID='*';

Each iteration corresponds to one `GEN0` three-second heartbeat period.

Example 1: Setting the Heartbeat for Containers That Are Configured to Use Oracle Key Vault

Suppose the container list is 1 2 3 4 5 6 7 8 9 10, with all containers configured to use Oracle Key Vault (`OKV`). The iterations are as follows:

- Iteration 1: batch consists of containers: 1 2 3
- Iteration 2: batch consists of containers: 1 4 5
- Iteration 3: batch consists of containers: 1 6 7
- Iteration 4: batch consists of containers: 1 8 9
- Iteration 5: batch consists of containers: 1 10
- Repeat this cycle.

Example 2: Setting the Heartbeat for Isolated PDBs with Different Keystores (Root Container in Oracle Key Vault)

In this example, the container list is 1 2 3 4 5 6 7 8 9 10, with only odd-numbered PDBs configured to use OKV, and the even-numbered PDBs configured to use a TDE wallet (`FILE`).

- Iteration 1: batch consists of containers: 1 3 5
- Iteration 2: batch consists of containers: 1 7 9
- Iteration 3: batch consists of containers: 1
- Repeat this cycle.

Example 3: Setting the Heartbeat for Isolated PDBs with Different Keystores (Root Container in TDE Wallet)

Assume that the container list is 1 2 3 4 5 6 7 8 9 10, with only even-numbered container numbers configured to use Oracle Key Vault, and the odd-numbered containers configured to use `FILE`. In the following example, there is no heartbeat for the `CDB$ROOT`, because it is configured to use `FILE`.

- Iteration 1: batch consists of containers: 2 4 6
- Iteration 2: batch consists of containers: 8 10
- Repeat this cycle.

**Related Topics**

- Setting the TDE Master Encryption Key in the United Mode External Keystore
- [Setting the TDE Master Encryption Key in the Isolated Mode External Keystore](managing-keystores-encryption-keys-in-isolated-mode.md)

**Parent topic:** Step 3: Set the TDE Master Encryption Key in Oracle Key Vault

##### 6.6.4.3 Setting the TDE Master Encryption Key in the United Mode External Keystore

To set the TDE master encryption key in the keystore when the PDB is configured in united mode, use the `ADMINISTER KEY MANAGEMENT` statement with the `SET KEY` clause.

1.  Connect to the CDB root as a common user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
    For example:
        CONNECT c##sec_admin AS SYSKM
        Enter password: password
2.  Ensure that the database is open in `READ WRITE` mode.
    You can set the master encryption key if `OPEN_MODE` is set to `READ WRITE`. To find the status, for a non-multitenant environment, query the `OPEN_MODE` column of the `V$DATABASE` dynamic view. If you are in a multitenant environment, then run the `show_pdbs` command.
3.  Run the `ADMINISTER KEY MANAGEMENT SET ENCRYPTION KEY` statement to set the TDE master encryption key in the keystore.
        ADMINISTER KEY MANAGEMENT SET KEY
        [USING TAG 'tag']
        [FORCE KEYSTORE]
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
        IDENTIFIED BY "psmith:password";

        keystore altered.
4.  Confirm that the TDE master encryption key is set.
        SELECT MASTERKEY_ACTIVATED FROM V$DATABASE_KEY_INFO;

    The output should be `YES`.

**Parent topic:** Step 3: Set the TDE Master Encryption Key in Oracle Key Vault

##### 6.6.4.4 Migration of an Encrypted Database from a TDE Wallet to Oracle Key Vault or OCI KMS

To switch from a TDE wallet to centralized key management with Oracle Key Vault or Oracle Cloud Infrastructure (OCI) Key Management Service (KMS), after you upload all current and retired TDE master keys you must migrate the database from the TDE wallet to Oracle Key Vault or OCI KMS.

Tools such as Oracle Data Pump and Oracle Recovery Manager require access to the old TDE wallet to perform decryption and encryption operations on data exported or backed up using the TDE wallet. Along with the current master encryption key, Oracle keystores maintain historical master encryption keys that are generated after every re-key operation that rotates the master encryption key. These historical master encryption keys help to restore Oracle database backups that were taken previously using one of the historical master encryption keys.

**Related Topics**

- [Migrating from a TDE Wallet to Oracle Key Vault](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Step 3: Set the TDE Master Encryption Key in Oracle Key Vault

#### 6.6.5 Step 4: Encrypt Your Data in United Mode

Now that you have completed the configuration for an external keystore or for an Oracle Key Vault keystore, you can begin to encrypt data.

**Related Topics**

- [Encrypting Columns in Tables](configuring-transparent-data-encryption.md)
- [Encryption Conversions for Tablespaces and Databases](configuring-transparent-data-encryption.md)

**Parent topic:** Configuring a Container Database with United Mode PDBs for Oracle Key Vault

### 6.7 Administering Keystores and TDE Master Encryption Keys in United Mode

After you configure a keystore and master encryption key for use in united mode, you can perform tasks such as rekeying TDE master encryption keys.

- Changing the Keystore Password in United Mode
  You can change the password of either a TDE wallet or an external keystore only in the CDB root.
- Backing Up a Password-Protected TDE Wallet in United Mode
  The `BACKUP KEYSTORE` clause of the `ADMINISTER KEY MANAGEMENT` statement backs up a password-protected TDE wallet.
- Closing Keystores in United Mode
  You can close both TDE wallet and external keystores in united mode, unless the system tablespace is encrypted.
- Creating a User-Defined TDE Master Encryption Key in United Mode
  To create a user-defined TDE master encryption key, use the `ADMINISTER KEY MANAGEMENT` statement with the `SET | CREATE [ENCRYPTION] KEY` clause.
- Example: Creating a Master Encryption Key in All PDBs
  You can use the `ADMINISTER KEY MANAGEMENT CREATE KEY USING TAG` statement to create a TDE master encryption key in all PDBs.
- Creating a TDE Master Encryption Key for Later Use in United Mode
  A keystore must be opened before you can create a TDE master encryption key for use later on in united mode.
- Activating a TDE Master Encryption Key in United Mode
  To activate a TDE master encryption key in united mode, you must open the keystore and use `ADMINISTER KEY MANAGEMENT` with the `USE KEY` clause.
- Rekeying the TDE Master Encryption Key in United Mode
  You can use the `ADMINISTER KEY MANAGEMENT` statement with the `SET KEY` clause to rekey a TDE master encryption key.
- Finding the TDE Master Encryption Key That Is in Use in United Mode
  A TDE master encryption key that is in use is the key that was activated most recently for the database.
- Creating a Custom Attribute Tag in United Mode
  To create a custom attribute tag in united mode, you must use the `SET TAG` clause of the `ADMINISTER KEY MANAGEMENT` statement.
- Moving a TDE Master Encryption Key into a New Keystore in United Mode
  In united mode, you can move an existing TDE master encryption key into a new keystore from an existing software password keystore.
- Automatically Removing Inactive TDE Master Encryption Keys in United Mode
  In united mode, the `REMOVE_INACTIVE_STANDBY_TDE_MASTER_KEY` initialization parameter can configure the automatic removal of inactive TDE master encryption keys.
- Isolating a Pluggable Database Keystore
  Isolating a PDB keystore moves the master encryption key from the CDB root keystore into an isolated mode keystore in the a PDB.

**Parent topic:** Managing Keystores and TDE Master Encryption Keys in United Mode

#### 6.7.1 Changing the Keystore Password in United Mode

You can change the password of either a TDE wallet or an external keystore only in the CDB root.

- Changing the Password-Protected TDE Wallet Password in United Mode
  To change the password of a password-protected TDE wallet in united mode, you must use the `ADMINISTER KEY MANAGEMENT` statement in the CDB root.
- Changing the Password of an External Keystore in United Mode
  To change the password of an external keystore, you must close the external keystore and then change the password from the external keystore management interface.

**Parent topic:** Administering Keystores and TDE Master Encryption Keys in United Mode

##### 6.7.1.1 Changing the Password-Protected TDE Wallet Password in United Mode

To change the password of a password-protected TDE wallet in united mode, you must use the `ADMINISTER KEY MANAGEMENT` statement in the CDB root.

You can change this password at any time, as per the security policies, compliance guidelines, and other security requirements of your site. As part of the command to change the password, you will be forced to specify the `WITH BACKUP` clause, and thus forced to make a backup of the current TDE wallet. During the password change operation, Transparent Data Encryption operations such as encryption and decryption will continue to work normally. You can change this password at any time. You should change this password if you think it was compromised.

1.  Connect to the CDB root as a common user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Use the following syntax to change the password for the keystore:
        ADMINISTER KEY MANAGEMENT ALTER KEYSTORE PASSWORD
        [FORCE KEYSTORE]
        IDENTIFIED BY
        old_TDE_wallet_password SET new_TDE_wallet_password
        WITH BACKUP [USING 'backup_identifier'];

    In this specification:

    - `FORCE KEYSTORE` temporarily opens the password-protected TDE wallet for this operation if the TDE wallet is closed, if an auto-login TDE wallet is configured and is currently open, or if a password-protected TDE wallet is configured and is currently closed.

    - `old_TDE_wallet_password` is the current password that you want to change.

    - `new_TDE_wallet_password` is the new password.

    - You do not need to include the `CONTAINER` clause because the password can only be changed locally, in the CDB root.

    The following example creates a backup of the keystore and then changes the password:

        ADMINISTER KEY MANAGEMENT ALTER KEYSTORE PASSWORD
        IDENTIFIED BY old_password SET new_password
        WITH BACKUP USING 'before_password_change';

        keystore altered.

    This example performs the same operation but uses the `FORCE KEYSTORE` clause in case the auto-login TDE wallet is in use or the password-protected TDE wallet is closed.

        ADMINISTER KEY MANAGEMENT ALTER KEYSTORE PASSWORD
        FORCE KEYSTORE
        IDENTIFIED BY old_password SET new_password
        WITH BACKUP USING 'before_password_change';

        keystore altered.

**Related Topics**

- [Performing Operations That Require a Keystore Password](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Changing the Keystore Password in United Mode

##### 6.7.1.2 Changing the Password of an External Keystore in United Mode

To change the password of an external keystore, you must close the external keystore and then change the password from the external keystore management interface.

1.  Connect to the CDB root as a common user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Close the external keystore.
    - Close the connection to the external key manager:

          ADMINISTER KEY MANAGEMENT SET KEYSTORE CLOSE
          IDENTIFIED BY "external_key_manager_password"|EXTERNAL STORE
          CONTAINER = ALL;

    - If the keystore was auto-opened by the database, then close the connection to the external key manager as follows:

          ADMINISTER KEY MANAGEMENT SET KEYSTORE CLOSE
          CONTAINER = ALL;
3.  Change the Oracle Key Vault password.
        WALLET_ROOT/okv/bin/okvutil changepwd -t wallet -l WALLET_ROOT/okv/ssl
4.  Update the Oracle Key Vault password that enables an auto-open Oracle Key Vault keystore to use the new password that you set in step 3.
        ADMINISTER KEY MANAGEMENT UPDATE SECRET 'new_Oracle_Key_Vault_password'
        FOR CLIENT 'OKV-PASSWORD' TO [LOCAL] AUTO-LOGIN KEYSTORE 'WALLET_ROOT/tde';
5.  Update the Oracle Key Vault password that enables `IDENTIFIED BY EXTERNAL STORE (IBES)` to the new password that you set in step 3.
        ADMINISTER KEY MANAGEMENT UPDATE SECRET 'new_Oracle_Key_Vault_password'
        FOR CLIENT 'OKV-PASSWORD' TO [LOCAL] AUTO-LOGIN KEYSTORE 'WALLET_ROOT/tde_seps';
6.  Open the connection to Oracle Key Vault.
        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN
        IDENTIFIED BY EXTERNAL STORE;

**Related Topics**

- [Performing Operations That Require a Keystore Password](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Changing the Keystore Password in United Mode

#### 6.7.2 Backing Up a Password-Protected TDE Wallet in United Mode

The `BACKUP KEYSTORE` clause of the `ADMINISTER KEY MANAGEMENT` statement backs up a password-protected TDE wallet.

1.  Connect to the CDB root as a common user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Back up the keystore by using the following syntax:
        ADMINISTER KEY MANAGEMENT BACKUP KEYSTORE
        [USING 'backup_identifier']
        [FORCE KEYSTORE]
        IDENTIFIED BY [EXTERNAL STORE | TDE_wallet_password]
        [TO 'keystore_location'];

    In this specification:

    - `USING` `backup_identifier` is an optional string that you can provide to identify the backup. Enclose this identifier in single quotation marks (`' '`). This identifier is appended to the named keystore file (for example, `ewallet_``time-stamp``_emp_key_backup.p12`).

    - `FORCE KEYSTORE` temporarily opens the password-protected TDE wallet for this operation. You must open the TDE wallet for this operation.

    - `IDENTIFIED BY` is required for the `BACKUP KEYSTORE` operation on a password-protected keystore because although the backup is simply a copy of the existing keystore, the status of the TDE master encryption key in the password-protected keystore must be set to `BACKED UP` and for this change the keystore password is required.

    - `keystore_location` is the path at which the backup keystore is stored. This setting is restricted to the PDB when the PDB lockdown profile `EXTERNAL_FILE_ACCESS` setting is blocked in the PDB or when the `PATH_PREFIX` variable was not set when the PDB was created. If you do not specify the `keystore_location`, then the backup is created in the same directory as the original keystore. Enclose this location in single quotation marks (`' '`).

    - You do not need to include the `CONTAINER` clause because the keystore can only be backup up locally, in the CDB root.

    The following example backs up a TDE wallet in the same location as the source keystore.

        ADMINISTER KEY MANAGEMENT BACKUP KEYSTORE
        USING 'hr.emp_keystore'
        FORCE KEYSTORE
        IDENTIFIED BY
        TDE_wallet_password ;

        keystore altered.

    In the following version, the password for the keystore is external, so the `EXTERNAL STORE` clause is used.

        ADMINISTER KEY MANAGEMENT BACKUP KEYSTORE
        USING 'hr.emp_keystore'
        FORCE KEYSTORE
        IDENTIFIED BY EXTERNAL STORE;

    After you run this statement, an `ewallet_``identifier``.p12` file (for example, `ewallet_``time-stamp``_hr.emp_keystore.p12`) appears in the TDE wallet backup location.

**Related Topics**

- [Backing Up Password-Protected Software Keystores](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Administering Keystores and TDE Master Encryption Keys in United Mode

#### 6.7.3 Closing Keystores in United Mode

You can close both TDE wallet and external keystores in united mode, unless the system tablespace is encrypted.

- Closing a Software Keystore in United Mode
  You can close password-protected keystores, auto-login keystores, and local auto-login software keystores in united mode.
- Closing an External Keystore in United Mode
  To close an external keystore, you must use the `ADMINISTER KEY MANAGEMENT` statement with the `SET KEYSTORE CLOSE` clause.

**Parent topic:** Administering Keystores and TDE Master Encryption Keys in United Mode

##### 6.7.3.1 Closing a Software Keystore in United Mode

You can close password-protected keystores, auto-login keystores, and local auto-login software keystores in united mode.

In the case of an auto-login keystore, which opens automatically when it is accessed, you must first move it to a new location where it cannot be automatically opened, then you must manually close it. You must do this if you are changing your configuration from an auto-login keystore to a password-protected keystore: you change the configuration to stop using the auto-login keystore (by moving the auto-login keystore to another location where it cannot be automatically opened), and then closing the auto-login keystore.

1.  Log in to the CDB root or the united mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Close the software keystore.
    - For a password-protected software keystore, use the following syntax if you are in the CDB root:

          ADMINISTER KEY MANAGEMENT SET | FORCE KEYSTORE CLOSE
          [IDENTIFIED BY [EXTERNAL STORE | software_keystore_password]]
          [CONTAINER = ALL | CURRENT];

      Use the `SET` clause to close the keystore without force. If there is a dependent keystore that is open (for example, an isolated mode PDB keystore and you are trying to close the CDB root keystore), then an `ORA-46692 cannot close wallet` error appears. If this happens, then use the `FORCE` clause instead of `SET` to temporarily close the dependent keystore during the close operation. The `STATUS` column of the `V$ENCRYPTION_WALLET` view shows if a keystore is open.

      If you are in the united mode PDB, then either omit the `CONTAINER` clause or set it to `CURRENT`.

    - For an auto-login or local auto-login software keystore, use this syntax if you are in the CDB root:

          ADMINISTER KEY MANAGEMENT SET KEYSTORE CLOSE
          [CONTAINER =  ALL | CURRENT];

Closing a keystore disables all of the encryption and decryption operations. Any attempt to encrypt or decrypt data or access encrypted data results in an error.

**Related Topics**

- [About Closing Keystores](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Closing Keystores in United Mode

##### 6.7.3.2 Closing an External Keystore in United Mode

To close an external keystore, you must use the `ADMINISTER KEY MANAGEMENT` statement with the `SET KEYSTORE CLOSE` clause.

1.  Log in to the CDB root or the united mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Close the external keystore by using the following syntax:
        ADMINISTER KEY MANAGEMENT SET KEYSTORE CLOSE
        IDENTIFIED BY [EXTERNAL STORE | "external_key_manager_password"]
        [CONTAINER = ALL | CURRENT];

    For example, for an HSM:

        ADMINISTER KEY MANAGEMENT SET KEYSTORE CLOSE
        IDENTIFIED BY "external_key_manager_password"
        CONTAINER = ALL;

    If an `ORA-46692 cannot close wallet` error appears, then check if any isolated mode keystores are open. To find the status of a keystore, query the `STATUS` column of the `V$ENCRYPTION_WALLET` view.

Closing a keystore disables all of the encryption and decryption operations. Any attempt to encrypt or decrypt data or access encrypted data results in an error.

**Related Topics**

- [About Closing Keystores](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Closing Keystores in United Mode

#### 6.7.4 Creating a User-Defined TDE Master Encryption Key in United Mode

To create a user-defined TDE master encryption key, use the `ADMINISTER KEY MANAGEMENT` statement with the `SET | CREATE [ENCRYPTION] KEY` clause.

1.  Connect to the CDB root as a common user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Create the user-defined TDE master encryption key by using the following syntax:
        ADMINISTER KEY MANAGEMENT SET | CREATE [ENCRYPTION] KEY
        '[mkid:mk | mk]'
        [USING ALGORITHM 'algorithm']
        [FORCE KEYSTORE]
        IDENTIFIED BY [EXTERNAL STORE | keystore_password]
        [WITH BACKUP [USING 'backup_identifier']];

    In this specification:

    - `SET | CREATE` : Enter `SET` if you want to create the master and activate the TDE master encryption key now, or select `CREATE` if you want to create the key for later use, without activating it yet. For `SET KEY` and `USE KEY`, you must be connected to the database that is supposed to use that key (CDB root container, united or isolated PDB). For `CREATE KEY`, you can be connected any united PDB, or the CDB root container, or the specific isolated PDB that is supposed to use that key later.

    - `mkid` and `mk`:

      - `mkid`, the TDE master encryption key ID, is a 16–byte hex-encoded value that you can specify or have Oracle Database generate.

      - `mk`, the TDE master encryption key, is a hex-encoded value that you can specify or have Oracle Database generate, either 32 bytes (for the for `AES256`, `ARIA256`, and `GOST256` algorithms) or 16 bytes (for the `SEED128` algorithm).

      If you omit the `mkid``:``mk``|``mkid` clause but include the `mk` value, then Oracle Database generates the `mkid` for the `mk`.

      If you omit the entire `mkid``:``mk``|``mkid` clause, then Oracle Database generates these values for you.

    - `USING ALGORITHM`: Specify one of the following supported algorithms:

      - `AES256`

      - `ARIA256`

      - `SEED128`

      - `GOST256`

      If you omit the algorithm, then the default, `AES256`, is used.

    - `FORCE KEYSTORE` temporarily opens the password-protected TDE wallet for this operation. You must open the TDE wallet for this operation.

    The following example creates a TDE master encryption key without the key-ID is when a database administrator performs that operation:

    First, generate the TDE master encryption key. For example, using OpenSSL:

        $ openssl rand -hex 32
        f24ce8cdae39742b5da7293da206fbd05a28b1e44c4781f801768cfdc3dbb6e2

    Set (create and activate) this ARIA master key with the following `ADMINISTER KEY MANAGEMENT` statement:

        ADMINISTER KEY MANAGEMENT SET ENCRYPTION KEY
        'f24ce8cdae39742b5da7293da206fbd05a28b1e44c4781f801768cfdc3dbb6e2'
        USING ALGORITHM 'ARIA256'
        FORCE KEYSTORE
        IDENTIFIED BY EXTERNAL STORE
        WITH BACKUP USING 'backup_identifier';

    The next example, where TDE master encryption key and key-ID are generated outside of the database, shows how to support separation of duties. A key administrator inserts the key with a `key_ID` into the wallet by using the `ADMINISTER KEY MANAGEMENT CREATE [ENCRYPTION] KEY` statement. Then, the key administrator sends the `key_ID` to the database administrator, who then activates the key by using the `ADMINISTER KEY MANAGEMENT USE KEY` clause.

    1.  Create the `key-ID`, converting characters to upper case. For example, using OpenSSL:

            $ openssl rand 16 | xxd -u -p
            D20765EB721AF44D054B30FE87F8E49A

    2.  Create the TDE master encryption key. For example, using OpenSSL:

            $ openssl rand -hex 32
            5a089c8ea6ee21cba774f61e58d102665df4a979a34757836b3d066a3eb3db11

    3.  Create (but do not activate) a default AES256 master encryption key by inserting both the random `key-ID` and the key itself, separated by a `:`, into the wallet.

            ADMINISTER KEY MANAGEMENT CREATE ENCRYPTION KEY
            'D20765EB721AF44D054B30FE87F8E49A:5a089c8ea6ee21cba774f61e58d102665df4a979a34757836b3d066a3eb3db11'
            IDENTIFIED BY [EXTERNAL STORE | keystore_password]
            WITH BACKUP USING 'backup_identifier' WITH BACKUP;

    4.  The database administrator can retrieve the BASE64 key-ID from the database with the following `SELECT` statement:

            SELECT ' ADMINISTER KEY MANAGEMENT USE KEY '''||KEY_ID||'''
            USING TAG '''||SYS_CONTEXT('USERENV', 'CON_NAME')||' '||TO_CHAR (SYS_EXTRACT_UTC (SYSTIMESTAMP),
            'YYYY-MM-DD HH24:MI:SS"Z"')||'''
            FORCE KEYSTORE
            IDENTIFIED BY EXTERNAL STORE WITH BACKUP;
            ' AS "USE KEY COMMAND" FROM DUAL, V$ENCRYPTION_KEYS WHERE TAG IS NULL;

**Related Topics**

- [Supported Encryption and Integrity Algorithms](introduction-to-transparent-data-encryption.md)

**Parent topic:** Administering Keystores and TDE Master Encryption Keys in United Mode

#### 6.7.5 Example: Creating a Master Encryption Key in All PDBs

You can use the `ADMINISTER KEY MANAGEMENT CREATE KEY USING TAG` statement to create a TDE master encryption key in all PDBs.

Example 6-1 shows how to create a master encryption key in all of the PDBs in a multitenant environment. It uses the `FORCE KEYSTORE` clause in the event that the auto-login keystore in the CDB root is open. The password is stored externally, so the `EXTERNAL STORE` setting is used for the `IDENTIFIED BY` clause. After you execute this statement, a master encryption key is created in each PDB. You can find the identifiers for these keys as follows:

- Log in to the PDB and then query the `TAG` column of the `V$ENCRYPTION_KEYS` view.

- Log in to the CDB root and then query the `INST_ID` and `TAG` columns of the `GV$ENCRYPTION_KEYS` view.

You also can check the `CREATION_TIME` column of these views to find the most recently created key, which would be the key that you created from this statement. After you create the keys, you can individually activate the keys in each of the PDBs.

Example 6-1 Creating a Master Encryption Key in All of the PDBs

    ADMINISTER KEY MANAGEMENT CREATE KEY USING TAG
    'scope:all pdbs;description:Create Key for ALL PDBS'
    FORCE KEYSTORE IDENTIFIED BY EXTERNAL STORE
    WITH BACKUP
    CONTAINER = ALL;

    keystore altered.

**Parent topic:** Administering Keystores and TDE Master Encryption Keys in United Mode

#### 6.7.6 Creating a TDE Master Encryption Key for Later Use in United Mode

A keystore must be opened before you can create a TDE master encryption key for use later on in united mode.

1.  Log in to the CDB root or the united mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Create the TDE master encryption key by using the following syntax:
        ADMINISTER KEY MANAGEMENT CREATE [ENCRYPTION] KEY
        [FORCE KEYSTORE]
        [USING TAG 'tag_name']
        IDENTIFIED BY [EXTERNAL STORE | keystore_password]
        [WITH BACKUP [USING 'backup_identifier']]
        [CONTAINER = ALL | CURRENT];

    In this specification:

    - `FORCE KEYSTORE` temporarily opens the password-protected TDE wallet for this operation. You must open the TDE wallet for this operation.

    - `CONTAINER`: In the CDB root, set `CONTAINER` to either `ALL` or `CURRENT`. In a PDB, set it to `CURRENT`. In both cases, omitting `CONTAINER` defaults to `CURRENT`.

    For example:

        ADMINISTER KEY MANAGEMENT CREATE KEY
        FORCE KEYSTORE
        IDENTIFIED BY keystore_password
        WITH BACKUP
        CONTAINER = CURRENT;
3.  If necessary, activate the TDE master encryption key.
    1.  Find the key ID.
            SELECT KEY_ID FROM V$ENCRYPTION_KEYS;

            KEY_ID
            ----------------------------------------------------
            AWsHwVYC2U+Nv3RVphn/yAIAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
    2.  Use this key ID to activate the key.
            ADMINISTER KEY MANAGEMENT USE KEY
            'AWsHwVYC2U+Nv3RVphn/yAIAAAAAAAAAAAAAAAAAAAAAAAAAAAAA'
            USING TAG 'quarter:second;description:Activate Key on standby'
            IDENTIFIED BY password
            WITH BACKUP;

**Related Topics**

- [Creating TDE Master Encryption Keys for Later Use](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Administering Keystores and TDE Master Encryption Keys in United Mode

#### 6.7.7 Activating a TDE Master Encryption Key in United Mode

To activate a TDE master encryption key in united mode, you must open the keystore and use `ADMINISTER KEY MANAGEMENT` with the `USE KEY` clause.

1.  Connect to the CDB root as a common user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Query the `ORIGIN` and `KEY_ID` columns of the `V$ENCRYPTION_KEYS` view to find the key identifier.
    For example:

        SELECT ORIGIN, KEY_ID FROM V$ENCRYPTION_KEYS;

        ORIGIN  KEY_ID
        ------  ----------------------------------------------
        LOCAL   ARaHD762tUkkvyLgPzAi6hMAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
3.  Use this key identifier to activate the TDE master encryption key by using the following syntax:
        ADMINISTER KEY MANAGEMENT USE KEY 'key_identifier_from_V$ENCRYPTION_KEYS'
        [USING TAG 'tag']
        [FORCE KEYSTORE]
        IDENTIFIED BY [EXTERNAL STORE | keystore_password]
        WITH BACKUP [USING 'backup_identifier'];

    In this specification:

    - `FORCE KEYSTORE` temporarily opens the password-protected TDE wallet for this operation. You must open the TDE wallet for this operation.

    - `WITH BACKUP` backs up the wallet in the same location as original wallet, as identified by `WALLET_ROOT``/tde`. To find the key locations for all of the database instances, query the `V$ENCRYPTION_WALLET` or `GV$ENCRYPTION_WALLET` view.

      The `WITH BACKUP` clause is mandatory for all `ADMINISTER KEY MANAGEMENT` statements that modify the wallet. Optionally, include the `USING` `backup_identifier` clause to add a description of the backup. Enclose `backup_identifier` in single quotation marks (`' '`).

    For example:

        ADMINISTER KEY MANAGEMENT USE KEY 'ARaHD762tUkkvyLgPzAi6hMAAAAAAAAAAAAAAAAAAAAAAAAAAAAA'
        FORCE KEYSTORE
        IDENTIFIED BY EXTERNAL STORE
        WITH BACKUP;

**Parent topic:** Administering Keystores and TDE Master Encryption Keys in United Mode

#### 6.7.8 Rekeying the TDE Master Encryption Key in United Mode

You can use the `ADMINISTER KEY MANAGEMENT` statement with the `SET KEY` clause to rekey a TDE master encryption key.

1.  Log in to the CDB root or the united mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.

2.  If you are rekeying the TDE master encryption key for a keystore that has auto login enabled, then ensure that both the auto login keystore, identified by the `.sso` file, and the encryption keystore, identified by the `.p12` file, are present.

    You can find the location of these files by querying the `WRL_PARAMETER` column of the `V$ENCRYPTION_WALLET` view. To find the `WRL_PARAMETER` values for all of the database instances, query the `GV$ENCRYPTION_WALLET` view.

3.  Rekey the TDE master encryption key by using the following syntax:

        ADMINISTER KEY MANAGEMENT SET [ENCRYPTION] KEY
        [FORCE KEYSTORE]
        [USING TAG 'tag_name']
        IDENTIFIED BY [EXTERNAL STORE | keystore_password]
        [WITH BACKUP [USING 'backup_identifier']]
        [CONTAINER = ALL | CURRENT];

    In this specification:

    - `tag` is the associated attributes and information that you define. Enclose this setting in single quotation marks (`' '`).

    - `FORCE KEYSTORE` temporarily opens the password-protected TDE wallet for this operation. You must open the TDE wallet for this operation.

    - `IDENTIFIED BY` can be one of the following settings:

      - `EXTERNAL STORE` uses the keystore password stored in the external store to perform the keystore operation.

      - `keystore_password` is the password that was created for this keystore.

    - `CONTAINER`: In the CDB root, set `CONTAINER` to either `ALL` or `CURRENT`. In a PDB, set it to `CURRENT`. In both cases, omitting `CONTAINER` defaults to `CURRENT`.

    For example:

        ADMINISTER KEY MANAGEMENT SET KEY
        FORCE KEYSTORE
        IDENTIFIED BY keystore_password
        WITH BACKUP USING 'emp_key_backup'
        CONTAINER = CURRENT;

        keystore altered.

**Related Topics**

- [About Rekeying the TDE Master Encryption Key](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Administering Keystores and TDE Master Encryption Keys in United Mode

#### 6.7.9 Finding the TDE Master Encryption Key That Is in Use in United Mode

A TDE master encryption key that is in use is the key that was activated most recently for the database.

In united mode, the TDE master encryption key in use of the PDB is the one that was activated most recently for that PDB.

- To find the TDE master encryption key that is in use, query the `V$ENCRYPTION_KEYS` dynamic view.
  For example:
      SELECT KEY_ID
      FROM V$ENCRYPTION_KEYS
      WHERE ACTIVATION_TIME = (SELECT MAX(ACTIVATION_TIME)
             FROM V$ENCRYPTION_KEYS
             WHERE ACTIVATING_PDBID = SYS_CONTEXT('USERENV', 'CON_ID'));

**Parent topic:** Administering Keystores and TDE Master Encryption Keys in United Mode

#### 6.7.10 Creating a Custom Attribute Tag in United Mode

To create a custom attribute tag in united mode, you must use the `SET TAG` clause of the `ADMINISTER KEY MANAGEMENT` statement.

1.  Log in to the CDB root or the united mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.

2.  If necessary, query the `TAG` column of the `V$ENCRYPTION_KEY` dynamic view to find a listing of existing tags for the TDE master encryption keys.

    When you create a new tag for a TDE master encryption key, it overwrites the existing tag for that TDE master encryption key.

3.  Create the custom attribute tag by using the following syntax:

        ADMINISTER KEY MANAGEMENT SET TAG 'tag'
        FOR 'master_key_identifier'
        [FORCE KEYSTORE]
        IDENTIFIED BY [EXTERNAL STORE | keystore_password]
        WITH BACKUP [USING 'backup_identifier'];

    In this specification

    - `tag` is the associated attributes or information that you define. Enclose this information in single quotation marks (`' '`).

    - `master_key_identifier` identifies the TDE master encryption key for which the `tag` is set. To find a list of TDE master encryption key identifiers, query the `KEY_ID` column of the `V$ENCRYPTION_KEYS` dynamic view.

    - `FORCE KEYSTORE` temporarily opens the password-protected TDE wallet for this operation. You must open the TDE wallet for this operation.

    - `IDENTIFIED BY` can be one of the following settings:

      - `EXTERNAL STORE` uses the keystore password stored in the external store to perform the keystore operation.

      - `keystore_password` is the password that was created for this keystore.

    - `backup_identifier` defines the tag values. Enclose this setting in single quotation marks (`' ')` and separate each value with a colon.

    For example, to create a tag that uses two values, one to capture a specific session ID and the second to capture a specific terminal ID:

        ADMINISTER KEY MANAGEMENT SET ENCRYPTION KEY
        USING TAG 'sessionid=3205062574:terminal=xcvt'
        IDENTIFIED BY keystore_password
        WITH BACKUP;

        keystore altered.

    Both the session ID (`3205062574`) and terminal ID (`xcvt`) can derive their values by using either the `SYS_CONTEXT` function with the `USERENV` namespace, or by using the `USERENV` function.

**Related Topics**

- [About Creating Custom Attribute Tags](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Administering Keystores and TDE Master Encryption Keys in United Mode

#### 6.7.11 Moving a TDE Master Encryption Key into a New Keystore in United Mode

In united mode, you can move an existing TDE master encryption key into a new keystore from an existing software password keystore.

This feature enables you to delete unused keys. After you move the key to a new keystore, you then can delete the old keystore.

1.  Log in to the CDB root or the united mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Query the `KEY_ID` column of the `V$ENCRYPTION_KEYS` view to find the key identifier of the keystore to which you want to move the keys.
    For example:
        SELECT CREATION_TIME, KEY_ID FROM V$ENCRYPTION_KEYS;

        CREATION TIME
        ----------------------------------------------------
        22-SEP-17 08.55.12.956170 PM +00:00

        KEY_ID
        ----------------------------------------------------
        ARaHD762tUkkvyLgPzAi6hMAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
3.  Move the key into a new keystore by using the following syntax:
        ADMINISTER KEY MANAGEMENT
        MOVE [ENCRYPTION] KEYS
        TO NEW KEYSTORE 'keystore_location1'
        IDENTIFIED BY keystore1_password
        FROM [FORCE] KEYSTORE
        IDENTIFIED BY keystore_password
        [WITH IDENTIFIER IN
        { 'key_identififier' [, 'key_identifier' ]... | ( subquery ) } ]
        [WITH BACKUP [USING 'backup_identifier']];

    In this specification:

    - `keystore_location1` is the path to the `wallet` directory that will store the new keystore `.p12` file. By default, this directory is in `$ORACLE_BASE/admin/``db_unique_name``/wallet`.

    - `FORCE` temporarily opens the keystore for this operation.

    - `keystore_password` is the password for the keystore from which the key is moving.

    For example:

        ADMINISTER KEY MANAGEMENT MOVE KEYS
        TO NEW KEYSTORE '$ORACLE_BASE/admin/orcl/wallet'
        IDENTIFIED BY keystore_password
        FROM FORCE KEYSTORE
        IDENTIFIED BY keystore_password
        WITH IDENTIFIER IN
        (SELECT KEY_ID FROM V$ENCRYPTION_KEYS WHERE ROWNUM < 2)
        WITH BACKUP;
4.  To delete the old keystore, go to the `wallet` directory and then manually delete the `.p12` file containing the keystore.
    To find the location of the keystore, open the keystores, and then query the `WRL_PARAMETER` column of the `V$ENCRYPTION_WALLET` view.

**Related Topics**

- [Dangers of Deleting Keystores](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Administering Keystores and TDE Master Encryption Keys in United Mode

#### 6.7.12 Automatically Removing Inactive TDE Master Encryption Keys in United Mode

In united mode, the `REMOVE_INACTIVE_STANDBY_TDE_MASTER_KEY` initialization parameter can configure the automatic removal of inactive TDE master encryption keys.

1.  Log in to the server where the CDB root or the united mode PDB of the Oracle standby database resides.
2.  Locate the initialization parameter file for the database.
    By default, the initialization parameter fileis located in the `$ORACLE_HOME/dbs` directory.
3.  Edit the initialization parameter file to include the `REMOVE_INACTIVE_STANDBY_TDE_MASTER_KEY` initialization parameter.
    For example:
        remove_inactive_standby_tde_master_key = true

    Setting this parameter to `TRUE` enables the automatic removal of inactive TDE master encryption keys; setting it to `FALSE` disables the automatic removal.

**Parent topic:** Administering Keystores and TDE Master Encryption Keys in United Mode

#### 6.7.13 Isolating a Pluggable Database Keystore

Isolating a PDB keystore moves the master encryption key from the CDB root keystore into an isolated mode keystore in the a PDB.

This process enables the keystore to be managed as a separate keystore in isolated mode. This way, an administrator who has been locally granted the `ADMINISTER KEY MANAGEMENT` privilege for the PDB can manage the keystore.

1.  Connect to the CDB root as a common user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Move the keys from the keystore of the CDB root into the isolated mode keystore of the PDB by using the following syntax:
        ADMINISTER KEY MANAGEMENT [FORCE] ISOLATE KEYSTORE
        IDENTIFIED BY isolated_keystore_password
        FROM ROOT KEYSTORE
        [FORCE KEYSTORE]
        IDENTIFIED BY
        [EXTERNAL STORE | united_keystore_password]
        [WITH BACKUP [USING backup_id]];

    In this specification:

    - `FORCE` is used when a clone of the PDB is using the master encryption key that is being isolated. The `ADMINISTER KEY MANAGEMENT` statement then copies (rather than moves) the keys from the wallet of the CDB root into the isolated mode PDB.

    - `FORCE KEYSTORE` temporarily opens the password-protected TDE wallet for this operation if an auto-login TDE wallet is open (and in use) or if the TDE wallet is closed.

    - `united_keystore_password`: Knowledge of this password does not enable the user who performs the `ISOLATE KEYSTORE` operation privileges to perform `ADMINISTER KEY MANAGEMENT UNITE KEYSTORE` operations on the CDB root. This password is the same as the keystore password in the CDB root.

    <!-- -->

    After the keystore of a CDB root has been united with that of a PDB, all of the previously active (historical) master encryption keys that were associated with the CDB are moved to the keystore of the PDB.
3.  Confirm that the united mode PDB is now an isolated mode PDB.
        SELECT KEYSTORE_MODE FROM V$ENCRYPTION_WALLET;

    The output should be `ISOLATED`.

After the united mode PDB has been converted to an isolated mode PDB, you can change the password of the keystore.

**Parent topic:** Administering Keystores and TDE Master Encryption Keys in United Mode

### 6.8 Administering Transparent Data Encryption in United Mode

You can perform general administrative tasks with Transparent Data Encryption in united mode.

- Moving PDBs from One CDB to Another in United Mode
  You can clone or relocate encrypted PDBs within the same container database, or across container databases.
- Unplugging and Plugging a PDB with Encrypted Data in a CDB in United Mode
  In united mode, for a PDB that has encrypted data, you can plug it into a CDB. Conversely, you can unplug this PDB from the CDB.
- Managing Cloned PDBs with Encrypted Data in United Mode
  In united mode, you can clone a PDB that has encrypted data in a CDB.
- How Keystore Open and Close Operations Work in United Mode
  You should be aware of how keystore open and close operations work in united mode.
- Finding the Keystore Status for All of the PDBs in United Mode
  You can create a convenience function that uses the `V$ENCRYPTION_WALLET` view to find the status for keystores in all PDBs in a CDB.
- Unplugging a PDB That Has Encrypted Data in United Mode Without ENCRPYT Clause
  In united mode, you can unplug a PDB with encrypted data and export data into an XML file or an archive file and then export TDE master encryption keys separately into a file.
- Plugging a PDB That Has Encrypted Data into a CDB in United Mode Without DECRYPT Clause
  To plug a PDB that has encrypted data into a CDB, you first plug in the PDB, open the PDB, import the TDE master encryption keys, and then you create a master encryption key for the PDB

**Parent topic:** Managing Keystores and TDE Master Encryption Keys in United Mode

#### 6.8.1 Moving PDBs from One CDB to Another in United Mode

You can clone or relocate encrypted PDBs within the same container database, or across container databases.

If you are trying to move a non-CDB or a PDB in which the `SYSTEM`, `SYSAUX`, `UNDO`, or `TEMP` tablespace is encrypted, and using the manual export or import of keys, then you must first import the keys for the non-CDB or PDB in the target database's `CDB$ROOT` before you create the PDB. Import of the keys are again required inside the PDB to associate the keys to the PDB.

- Clone or relocate the non-CDB or PDB using the following syntax:
      CREATE|RELOCATE PLUGGABLE DATABASE database_name KEYSTORE
      IDENTIFIED BY EXTERNAL STORE|target_keystore_password [NO REKEY];

**Related Topics**

- [Oracle Multitenant Administrator's Guide](../multi/introduction-to-the-multitenant-architecture.md)

**Parent topic:** Administering Transparent Data Encryption in United Mode

#### 6.8.2 Unplugging and Plugging a PDB with Encrypted Data in a CDB in United Mode

In united mode, for a PDB that has encrypted data, you can plug it into a CDB. Conversely, you can unplug this PDB from the CDB.

- Unplugging a PDB That Has Encrypted Data in United Mode
  In united mode, you can unplug a PDB with encrypted data and export it into an XML file or an archive file.
- Plugging a PDB That Has Encrypted Data into a CDB in United Mode
  To plug a PDB that has encrypted data into a CDB, you first plug in the PDB and then you create a master encryption key for the PDB.
- Unplugging a PDB That Has Master Encryption Keys Stored in an External Keystore in United Mode
  You can unplug a PDB from one CDB that has been configured with an external keystore and then plug it into another CDB also configured with an external keystore.
- Plugging a PDB That Has Master Encryption Keys Stored in an External Keystore in United Mode
  The `ADMINISTER KEY MANAGEMENT` statement can import a TDE master encryption key from an external keystore to a PDB that has been moved to another CDB.

**Parent topic:** Administering Transparent Data Encryption in United Mode

##### 6.8.2.1 Unplugging a PDB That Has Encrypted Data in United Mode

In united mode, you can unplug a PDB with encrypted data and export it into an XML file or an archive file.

You can check if a PDB has been unplugged by querying the `STATUS` column of the `DBA_PDBS` data dictionary view.

1.  In the CDB root, query the `V$ENCRYPTION_WALLET` dynamic view to ensure that the keystore is open.
2.  Use the `ENCRYPT USING ``transport_secret` clause in the `ALTER PLUGGABLE DATABASE` statement when you unplug the PDB.
    This process extracts the master encryption keys that belong to that PDB from the open wallet, and encrypts those keys with the `transport_secret` clause.
    You must use this clause if the PDB has encrypted data. Otherwise, an `ORA-46680: master keys of the container database must be exported` error is returned.
    - For example, to export the PDB data into an XML file:

          ALTER PLUGGABLE DATABASE CDB1_PDB2
          UNPLUG INTO '/tmp/cdb1_pdb2.xml'
          ENCRYPT USING transport_secret;

    - To export the PDB data into an archive file:

          ALTER PLUGGABLE DATABASE CDB1_PDB2
          UNPLUG INTO '/tmp/cdb1_pdb2.pdb'
          ENCRYPT USING transport_secret;

**Related Topics**

- Step 2: Open the TDE Wallet in a United Mode PDB
- [Oracle Multitenant Administrator's Guide](../multi/removing-a-pdb.md)
- [Oracle Database SQL Language Reference](../sqlrf/ALTER-PLUGGABLE-DATABASE.md)

**Parent topic:** Unplugging and Plugging a PDB with Encrypted Data in a CDB in United Mode

##### 6.8.2.2 Plugging a PDB That Has Encrypted Data into a CDB in United Mode

To plug a PDB that has encrypted data into a CDB, you first plug in the PDB and then you create a master encryption key for the PDB.

After you plug the PDB into the target CDB, and you must create a master encryption key that is unique to this plugged-in PDB. This is because the plugged-in PDB initially uses the key that was extracted from the wallet of the source PDB. When you plug an unplugged PDB into another CDB, the key version is set to `0` because this operation invalidates the history of the previous keys. You can check the key version by querying the `KEY_VERSION` column of the `V$ENCRYPTED_TABLESPACES` dynamic view. Similarly, if a control file is lost and recreated, then the previous history of the keys is reset to `0`. You can check if a PDB has already been plugged in by querying the `STATUS` column of the `DBA_PDBS` data dictionary view.

1.  From the CDB root, create the PDB by plugging the unplugged PDB into the CDB.

    To perform this operation for united mode, include the `DECRYPT USING ``transport_secret` clause.

    You must use this clause if the XML or archive file for the PDB has encrypted data. Otherwise, an `ORA-46680: master keys of the container database must be exported` error is returned.

    - For example, if you had exported the PDB data into an XML file:

          CREATE PLUGGABLE DATABASE CDB1_PDB2
          USING '/tmp/cdb1_pdb2.xml'
          KEYSTORE IDENTIFIED BY EXTERNAL STORE|TDE_wallet_password
          DECRYPT USING transport_secret;

    - If you had exported the PDB into an archive file:

          CREATE PLUGGABLE DATABASE CDB1_PDB2
          USING '/tmp/cdb1_pdb2.pdb'
          KEYSTORE IDENTIFIED BY EXTERNAL STORE|TDE_wallet_password
          DECRYPT USING transport_secret;

    During the open operation of the PDB after the plug operation, Oracle Database determines if the PDB has encrypted data. If so, it opens the PDB in the `RESTRICTED` mode.

    If you want to create the PDB by cloning another PDB or from a non-CDB, and if the source database has encrypted data or a TDE master encryption key that has been set, then you must provide the keystore password of the target keystore by including the `KEYSTORE IDENTIFIED BY ``keystore_password` clause in the `CREATE PLUGGABLE DATABASE ... FROM` SQL statement. You must provide this password even if the target database is using an auto-login TDE wallet. You can find if the source database has encrypted data or a TDE master encryption key set in the TDE wallet by querying the `V$ENCRYPTION_KEYS` dynamic view

2.  Open the PDB.

    For example:

        ALTER PLUGGABLE DATABASE CDB1_PDB2 OPEN;

3.  Open the keystore in the CDB root by using one of the following methods:

    - If the TDE wallet of the CDB is not open, open it for the container and all open PDBs by using the following syntax:

          ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN [FORCE KEYSTORE]
          IDENTIFIED BY EXTERNAL STORE|KEYSTORE_PASSWORD CONTAINER = ALL;

    - If the TDE wallet of the CDB is open, connect to the plugged-in PDB and then open the keystore by using the following syntax:

          ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN [FORCE KEYSTORE]
          IDENTIFIED BY EXTERNAL STORE|KEYSTORE_PASSWORD [CONTAINER = CURRENT];

4.  In the plugged-in PDB, set the TDE master encryption key for the PDB by using the following syntax:

        ADMINISTER KEY MANAGEMENT SET KEY
        [FORCE KEYSTORE]
        IDENTIFIED BY EXTERNAL STORE|TDE_wallet_password
        WITH BACKUP [USING 'backup_identifier'];

**Related Topics**

- Step 2: Open the TDE Wallet in a United Mode PDB
- Step 3: Set the TDE Master Encryption Key in the TDE Wallet in United Mode

**Parent topic:** Unplugging and Plugging a PDB with Encrypted Data in a CDB in United Mode

##### 6.8.2.3 Unplugging a PDB That Has Master Encryption Keys Stored in an External Keystore in United Mode

You can unplug a PDB from one CDB that has been configured with an external keystore and then plug it into another CDB also configured with an external keystore.

1.  Unplug the PDB.
    You can check if a PDB has already been unplugged by querying the `STATUS` column of the `DBA_PDBS` data dictionary view.
2.  Move the master encryption keys of the unplugged PDB in the external keystore that was used at the source CDB to the external keystore that is in use at the destination CDB.
    Refer to the documentation for the external keystore for information about moving master encryption keys between external keystores.

**Related Topics**

- [Oracle Multitenant Administrator's Guide](../multi/index.md)

**Parent topic:** Unplugging and Plugging a PDB with Encrypted Data in a CDB in United Mode

##### 6.8.2.4 Plugging a PDB That Has Master Encryption Keys Stored in an External Keystore in United Mode

The `ADMINISTER KEY MANAGEMENT` statement can import a TDE master encryption key from an external keystore to a PDB that has been moved to another CDB.

1.  Plug the unplugged PDB into the destination CDB that has been configured with the external keystore.
    You can check if a PDB has already been plugged in by querying the `STATUS` column of the `DBA_PDBS` data dictionary view.
    After the plug-in operation, the PDB that has been plugged in will be in restricted mode.
2.  Ensure that the master encryption keys from the external keystore that has been configured with the source CDB are available in the external keystore of the destination CDB.
3.  Log in to the plugged PDB as a user who was granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
4.  Open the master encryption key of the plugged PDB.
    For example:

        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN
        IDENTIFIED BY keystore_passsword;
5.  Import the external keystore master encryption key into the PDB.
        ADMINISTER KEY MANAGEMENT IMPORT ENCRYPTION KEYS
        WITH SECRET "OKV" FROM 'OKV'
        IDENTIFIED BY keystore_password;
6.  Restart the PDB.
        ALTER PLUGGABLE DATABASE PDB1 CLOSE;
        ALTER PLUGGABLE DATABASE PDB1 OPEN;

**Related Topics**

- [Oracle Multitenant Administrator's Guide](../multi/plugging-in-a-pdb.md)

**Parent topic:** Unplugging and Plugging a PDB with Encrypted Data in a CDB in United Mode

#### 6.8.3 Managing Cloned PDBs with Encrypted Data in United Mode

In united mode, you can clone a PDB that has encrypted data in a CDB.

- About Managing Cloned PDBs That Have Encrypted Data in United Mode
  When you clone a PDB, you must make the master encryption key of the source PDB available to cloned PDB.
- Cloning a PDB with Encrypted Data in a CDB in United Mode
  The `CREATE PLUGGABLE DATABASE` statement with the `KEYSTORE IDENTIFIED BY` clause can clone a PDB that has encrypted data.
- Performing a Remote Clone of PDB with Encrypted Data Between Two CDBs in United Mode
  The `CREATE PLUGGABLE DATABASE` statement with the `KEYSTORE IDENTIFIED BY` clause can remotely clone a PDB that has encrypted data.
- TDE Academy Videos: Remotely Cloning and Upgrading Encrypted PDBs
  The Oracle TDE Academy provides videos on how to remotely clone and upgrade encrypted pluggable databases (PDBs).
- Relocating a PDB with Encrypted Data Across CDBs in United Mode
  The `CREATE PLUGGABLE DATABASE` statement with the `KEYSTORE IDENTIFIED BY` clause can relocate a PDB with encrypted data across CDBs.

**Parent topic:** Administering Transparent Data Encryption in United Mode

##### 6.8.3.1 About Managing Cloned PDBs That Have Encrypted Data in United Mode

When you clone a PDB, you must make the master encryption key of the source PDB available to cloned PDB.

This allows a cloned PDB to operate on the encrypted data. To perform the clone, you do not need to export and import the keys because Oracle Database transports the keys for you even if the cloned PDB is in a remote CDB. However, you will need to provide the keystore password of the CDB where you are creating the clone.

If the PDBs have encrypted data, then you can perform remote clone operations on PDBs between CDBs, and relocate PDBs across CDBs.

**Parent topic:** Managing Cloned PDBs with Encrypted Data in United Mode

##### 6.8.3.2 Cloning a PDB with Encrypted Data in a CDB in United Mode

The `CREATE PLUGGABLE DATABASE` statement with the `KEYSTORE IDENTIFIED BY` clause can clone a PDB that has encrypted data.

1.  In the CDB root, query the `STATUS` column of the `V$ENCRYPTION_WALLET` dynamic view to ensure that the keystore is open in the CDB root.
2.  Log in to the PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` and the `CREATE PLUGGABLE DATABASE` privileges.
3.  Use the `CREATE PLUGGABLE DATABASE` statement with the `KEYSTORE IDENTIFIED BY` clause to clone the PDB.
    For example:

        CREATE PLUGGABLE DATABASE cdb1_pdb3
        FROM cdb1_pdb1
        FILE_NAME_CONVERT=('cdb1_pdb1', 'pdb3/cdb1_pdb3') KEYSTORE
        IDENTIFIED BY EXTERNAL STORE|keystore_password [NO REKEY];

    Replace `keystore_password` with the password of the keystore of the CDB where the `cdb1_pdb3` clone is created.

    By default, during a PDB clone or relocate operation, the data encryption keys are rekeyed, which implies a re-encryption of all encrypted tablespaces. This rekey operation can increase the time it takes to clone or relocate a large PDB. With the optional `NO REKEY` clause, the data encryption keys are not renewed, and encrypted tablespaces are not re-encrypted.

    After you create the cloned PDB, encrypted data is still accessible by the clone using the master encryption key of the original PDB. After a PDB is cloned, there may be user data in the encrypted tablespaces. This encrypted data is still accessible because the master encryption key of the source PDB is copied over to the destination PDB. Because the clone is a copy of the source PDB but will eventually follow its own course and have its own data and security policies, you should rekey the master encrytion key of the cloned PDB.
4.  Rekey the master encryption key of the cloned PDB.
    For example:

        ADMINISTER KEY MANAGEMENT SET KEY
        FORCE KEYSTORE
        IDENTIFIED BY keystore_password
        WITH BACKUP USING 'emp_key_backup';

    In this example, `FORCE KEYSTORE` is included because the keystore must be open during the rekey operation.

    Before you rekey the master encryption key of the cloned PDB, the clone can still use master encryption keys that belong to the original PDB. However, these master encryption keys do not appear in the cloned PDB `V$` dynamic views. Rekeying the master encryption key ensures that the cloned PDB uses its own unique keys, which will be viewable in the `V$` views.

**Related Topics**

- Step 2: Open the TDE Wallet in a United Mode PDB

**Parent topic:** Managing Cloned PDBs with Encrypted Data in United Mode

##### 6.8.3.3 Performing a Remote Clone of PDB with Encrypted Data Between Two CDBs in United Mode

The `CREATE PLUGGABLE DATABASE` statement with the `KEYSTORE IDENTIFIED BY` clause can remotely clone a PDB that has encrypted data.

1.  In the CDB root, query the `STATUS` column of the `V$ENCRYPTION_WALLET` dynamic view to ensure that the keystore is open in the CDB root.
2.  In this root container of the target database, create a database link that connects to the root container of the source CDB.
        CREATE DATABASE LINK clone_link
        CONNECT TO C##REMOTE_CLONE_USER
        IDENTIFIED BY C##REMOTE_CLONE_USER_PASSWORD
        USING '//source_ip_address:port/DB_NAME';
3.  Use the `CREATE PLUGGABLE DATABASE` statement with the `KEYSTORE IDENTIFIED BY` clause to perform the clone of the PDB.
    For example:

        CREATE PLUGGABLE DATABASE cdb1_pdb3
        FROM cbd_1_pdb1@clone_link
        FILE_NAME_CONVERT=('cdb1_pdb1', 'pdb3/cdb1_pdb3') KEYSTORE
        KEYSTORE IDENTIFIED BY EXTERNAL STORE|keystore_password;

    Replace `keystore_password` with the password of the keystore of the CDB where the `cdb1_pdb3` clone is created.

    After you create the cloned PDB, encrypted data is still accessible by the clone using the master encryption key of the original PDB. After a PDB is cloned, there may be user data in the encrypted tablespaces. This encrypted data is still accessible because the master encryption key of the source PDB is copied over to the destination PDB. Because the clone is a copy of the source PDB but will eventually follow its own course and have its own data and security policies, you should rekey the master encrytion key of the cloned PDB.
4.  Connect as a user who has who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
5.  Rekey the master encryption key of the remotely cloned PDB.
    For example:

        ADMINISTER KEY MANAGEMENT SET KEY
        FORCE KEYSTORE
        IDENTIFIED BY keystore_password
        WITH BACKUP USING 'emp_key_backup';

    In this example, `FORCE KEYSTORE` is included because the keystore must be open during the rekey operation.

    Before you rekey the master encryption key of the cloned PDB, the clone can still use master encryption keys that belong to the original PDB. However, these master encryption keys do not appear in the cloned PDB `V$` dynamic views. Rekeying the master encryption key ensures that the cloned PDB uses its own unique keys, which will be viewable in the `V$` views.

**Related Topics**

- Step 2: Open the TDE Wallet in a United Mode PDB
- [Oracle Multitenant Administrator's Guide](../multi/cloning-a-pdb.md)
- [Oracle Multitenant Administrator's Guide](../multi/cloning-a-pdb.md)
- [Oracle Database SQL Language Reference](../sqlrf/CREATE-DATABASE-LINK.md)

**Parent topic:** Managing Cloned PDBs with Encrypted Data in United Mode

##### 6.8.3.4 TDE Academy Videos: Remotely Cloning and Upgrading Encrypted PDBs

The Oracle TDE Academy provides videos on how to remotely clone and upgrade encrypted pluggable databases (PDBs).

- [TDE Academy \#01: Remote clone and upgrade encrypted 18c PDBs to 19c](https://www.youtube.com/embed/onIQ3CDsjik)
- [TDE Academy \#02: Remote clone and upgrade encrypted 12.2.0.1 PDBs to 19c](https://www.youtube.com/embed/oJipexiHBXk)
- [TDE Academy \#03: Remote clone and upgrade encrypted 12.1.0.2 PDBs to 19c](https://www.youtube.com/embed/ql6352lmi24)

**Parent topic:** Managing Cloned PDBs with Encrypted Data in United Mode

##### 6.8.3.5 Relocating a PDB with Encrypted Data Across CDBs in United Mode

The `CREATE PLUGGABLE DATABASE` statement with the `KEYSTORE IDENTIFIED BY` clause can relocate a PDB with encrypted data across CDBs.

1.  In the CDB root, query the `STATUS` column of the `V$ENCRYPTION_WALLET` dynamic view to ensure that the keystore is open in the CDB root.
2.  Create a database link for the PDB that you want to clone.
    Use the `CREATE DATABASE LINK` SQL statement to create the database link. You must create the database link by following the database link prerequisites that are required for cloning a remote PDB or a non-CDB.
3.  Use the `CREATE PLUGGABLE DATABASE` statement with the `KEYSTORE IDENTIFIED BY` clause to relocate the PDB.
    For example:

        CREATE PLUGGABLE DATABASE cdb1_pdb3
        FROM cdb1_pdb1@clone_link RELOCATE [AVAILABILITY MAX]
        [FILE_NAME_CONVERT=('cdb1_pdb1', 'pdb3/cdb1_pdb3')]
        KEYSTORE IDENTIFIED BY EXTERNAL STORE|keystore_password;

    Replace `keystore_password` with the password of the keystore of the CDB where the `cdb1_pdb3` clone is created.

    After you have relocated the PDB, the encrypted data is still accessible because the master encryption key of the source PDB is copied over to the destination PDB; however, these master encryption keys do not appear in the cloned PDB `V$` dynamic views.
4.  Connect to the PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
5.  Rekey the master encryption key of the relocated PDB.
    For example:

        ADMINISTER KEY MANAGEMENT SET KEY
        [FORCE KEYSTORE]
        IDENTIFIED BY EXTERNAL STORE|keystore_password
        WITH BACKUP [USING 'emp_key_backup'];

**Related Topics**

- Step 2: Open the TDE Wallet in a United Mode PDB
- [Oracle Multitenant Administrator's Guide](../multi/cloning-a-pdb.md)
- [Oracle Multitenant Administrator's Guide](../multi/cloning-a-pdb.md)
- [Oracle Database SQL Language Reference](../sqlrf/CREATE-DATABASE-LINK.md)

**Parent topic:** Managing Cloned PDBs with Encrypted Data in United Mode

#### 6.8.4 How Keystore Open and Close Operations Work in United Mode

You should be aware of how keystore open and close operations work in united mode.

For each PDB in united mode, you must explicitly open the password-protected TDE wallet or external keystore in the PDB to enable the Transparent Data Encryption operations to proceed. (Auto-login and local auto-login TDE wallets open automatically.) Closing a keystore on a PDB blocks all of the Transparent Data Encryption operations on that PDB.

The open and close keystore operations in a PDB depend on the open and close status of the keystore in the CDB root.

Note the following:

- You can create a separate keystore password for each PDB in united mode.

- Before you can manually open a password-protected TDE wallet or an external keystore in an individual PDB, you must open the wallet or keystore in the CDB root.

- If an auto-login TDE wallet is in use, or if the keystore is closed, then include the `FORCE KEYSTORE` clause in the `ADMINISTER KEY MANAGEMENT` statement when you open the wallet.

- If the keystore is a password-protected TDE wallet that uses an external store for passwords, then replace the password in the `IDENTIFIED BY` clause with `EXTERNAL STORE`.

- Before you can set a TDE master encryption key in an individual PDB, you must set the key in the CDB root. Oracle highly recommends that you include the `USING TAG` clause when you set keys in PDBs. For example:

      SELECT ' ADMINISTER KEY MANAGEMENT SET KEY
      USING TAG '''||SYS_CONTEXT('USERENV', 'CON_NAME')||' '||TO_CHAR (SYSDATE, 'YYYY-MM-DD HH24:MI:SS')||'''
      FORCE KEYSTORE IDENTIFIED BY EXTERNAL STORE
      WITH BACKUP CONTAINER = CURRENT;' AS "SET KEY COMMAND" FROM DUAL;

  Including the `USING TAG` clause enables you to quickly and easily identify the keys that belong to a certain PDB, and when they were created.

- Auto-login and local auto-login TDE wallets open automatically. You do not need to manually open these from the CDB root first, or from the PDB.

- If you close the keystore in the CDB root, then the keystores in the dependent PDBs also close. A keystore close operation in the root is the equivalent of performing a keystore close operation with the `CONTAINER` clause set to `ALL`.

- If you perform an `ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN` statement in the CDB root and set the `CONTAINER` clause to `ALL`, then the keystore will only be opened in each open PDB that is configured in united mode. Keystores for any PDBs that are configured in isolated mode are not opened.

**Parent topic:** Administering Transparent Data Encryption in United Mode

#### 6.8.5 Finding the Keystore Status for All of the PDBs in United Mode

You can create a convenience function that uses the `V$ENCRYPTION_WALLET` view to find the status for keystores in all PDBs in a CDB.

The `V$ENCRYPTION_WALLET` view displays the status of the keystore in a PDB, whether it is open, closed, uses a software or an external keystore, and so on.

- To create a function that uses the`V$ENCRYPTION_WALLET` view to find the keystore status, use the `CREATE PROCEDURE` PL/SQL statement.

Example 6-2 shows how to create this function.

Example 6-2 Function to Find the Keystore Status of All of the PDBs in a CDB

    CREATE OR REPLACE PROCEDURE all_pdb_v$encryption_wallet
    IS
        err_occ            BOOLEAN;
        curr_pdb           VARCHAR2(30);
        pdb_name           VARCHAR2(30);
        wrl_type           VARCHAR2(20);
        status             VARCHAR2(30);
        wallet_type        VARCHAR2(20);
        wallet_order       VARCHAR2(12);
        fully_backed_up    VARCHAR2(15);
        wrl_parameter      VARCHAR2(4000);
        cursor sel_pdbs IS SELECT NAME FROM V$CONTAINERS
                           WHERE NAME <> 'PDB$SEED' order by con_id desc;
      BEGIN

        -- Store the original PDB name
        SELECT sys_context('userenv', 'con_name') INTO curr_pdb FROM DUAL;
        IF curr_pdb <> 'CDB$ROOT' THEN
          dbms_output.put_line('Operation valid in ROOT only');
        END IF;

        err_occ := FALSE;
        dbms_output.put_line('---');
        dbms_output.put_line('PDB_NAME                       WRL_TYPE STATUS                        ');
        dbms_output.put_line('------------------------------ -------- ------------------------------');
        dbms_output.put_line('WALLET_TYPE          WALLET_ORDER FULLY_BACKED_UP');
        dbms_output.put_line('-------------------- ------------ ---------------');
        dbms_output.put_line('WRL_PARAMETER');
        dbms_output.put_line('--------------------------------------------------------------------------');
        FOR pdbinfo IN sel_pdbs LOOP

          pdb_name := DBMS_ASSERT.ENQUOTE_NAME(pdbinfo.name, FALSE);
          EXECUTE IMMEDIATE 'ALTER SESSION SET CONTAINER = ' || pdb_name;

          BEGIN
            pdb_name := rpad(substr(pdb_name,1,30), 30, ' ');
            EXECUTE IMMEDIATE 'SELECT wrl_type from V$ENCRYPTION_WALLET' into wrl_type;
            wrl_type := rpad(substr(wrl_type,1,8), 8, ' ');
            EXECUTE IMMEDIATE 'SELECT status from V$ENCRYPTION_WALLET' into status;
            status := rpad(substr(status,1,30), 30, ' ');
            EXECUTE IMMEDIATE 'SELECT wallet_type from V$ENCRYPTION_WALLET' into wallet_type;
            wallet_type := rpad(substr(wallet_type,1,20), 20, ' ');
            EXECUTE IMMEDIATE 'SELECT wallet_order from V$ENCRYPTION_WALLET' into wallet_order;
            wallet_order := rpad(substr(wallet_order,1,9), 12, ' ');
            EXECUTE IMMEDIATE 'SELECT fully_backed_up from V$ENCRYPTION_WALLET' into fully_backed_up;
            fully_backed_up := rpad(substr(fully_backed_up,1,9), 15, ' ');
            EXECUTE IMMEDIATE 'SELECT wrl_parameter from V$ENCRYPTION_WALLET' into wrl_parameter;
            wrl_parameter := rpad(substr(wrl_parameter,1,79), 79, ' ');
            dbms_output.put_line(pdb_name || ' ' || wrl_type || ' ' || status);
            dbms_output.put_line(wallet_type || ' ' || wallet_order || ' ' || fully_backed_up);
            dbms_output.put_line(wrl_parameter);

          EXCEPTION
            WHEN OTHERS THEN
            err_occ := TRUE;
          END;
        END LOOP;

        IF err_occ = TRUE THEN
           dbms_output.put_line('One or more PDB resulted in an error');
        END IF;
      END;
    .
    /
    set serveroutput on
    exec all_pdb_v$encryption_wallet;

**Parent topic:** Administering Transparent Data Encryption in United Mode

#### 6.8.6 Unplugging a PDB That Has Encrypted Data in United Mode Without `ENCRPYT` Clause

In united mode, you can unplug a PDB with encrypted data and export data into an XML file or an archive file and then export TDE master encryption keys separately into a file.

1.  Export the keys.

    If the source is multitenant then export the keys from the PDB which needs to be unplugged. For example:

        alter session set container =<cdb1_pdb1>;
        administer key management export encryption keys with secret "transport_secret" to '/tmp/TDE/pdb_01.p12' identified by <TDE_wallet_password>;

    If the source is NON-CDB then export the keys from NON-CDB. For example,
        administer key management export encryption keys with secret "transport_secret" to '/tmp/TDE/pdb_01.p12' identified by <TDE_wallet_password>;

2.  After export unplug the PDB from source.
    1.  Close the PDB which needs to be unplugged:

            alter session set container=cdb$root;
            alter pluggable database <CDB1_PDB1> close;

    2.  Unplug the PDB:

            alter pluggable database <CDB1_PDB1> '/tmp/TDE/cdb1_pdb1.xml';

    3.  If the source is NON-CDB, generate an XML file named `ncdb.xml` in the `/tmp` directory, run the following procedure:

            BEGIN
            DBMS_PDB.DESCRIBE(
                pdb_descr_file => '/tmp/ncdb.xml'
                );
            END;
            /

**Parent topic:** Administering Transparent Data Encryption in United Mode

#### 6.8.7 Plugging a PDB That Has Encrypted Data into a CDB in United Mode Without `DECRYPT` Clause

To plug a PDB that has encrypted data into a CDB, you first plug in the PDB, open the PDB, import the TDE master encryption keys, and then you create a master encryption key for the PDB

1.  In the destination CDB, import the keys. This step can be skipped if there are no system and sysaux encrypted data in source.
    For example,
        administer key management import encryption keys with secret "transport_secret" from '/tmp/TDE/pdb_01.p12' identified by <TDE_wallet_password> with backup;
2.  Create the PDB using xml created in source.
    For example,
        create pluggable database <CDB1_PDB4_Plug> using '/tmp/TDE/cdb1_pdb1.xml' file_name_convert=('cdb1_pdb1','cdb1_pdb4_plug') keystore identified by <TDE_wallet_password>;
3.  Open the TDE keystore.
    For example,
        alter session set container =<CDB1_PDB4_Plug>;
        administer key management set Keystore open identified by <TDE_wallet_password>;
4.  Open the new created PDB.
    For example,
        alter session set container=cdb$root;
        alter pluggable database <CDB1_PDB4_Plug> open;
5.  Import the keys.
    For example,
        administer key management import encryption keys with secret "transport_secret" from '/tmp/TDE/pdb_01.p12' identified by <TDE_wallet_password> with backup;

**Parent topic:** Administering Transparent Data Encryption in United Mode
