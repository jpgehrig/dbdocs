## 7 Managing Keystores and TDE Master Encryption Keys in Isolated Mode

Isolated mode enables you to create a keystore for each pluggable database (PDB).

- About Configuring Isolated Mode
  In isolated mode, where a pluggable database (PDB) has its own keystore and keystore password, you manage the keystore and its TDE master encryption keys from the PDB only.
- Operations That Are Allowed in Isolated Mode
  You can perform many `ADMINISTER KEY MANAGEMENT` operations in isolated mode.
- Operations That Are Not Allowed in an Isolated Mode PDB
  There are several `ADMINISTER KEY MANAGEMENT` operations that you cannot perform in an isolated mode PDB.
- Configuring the Keystore Location and Type for Isolated Mode
  For isolated mode, you can configure the keystore location and type by using only parameters or a combination of parameters and the `ALTER SYSTEM` statement.
- Configuring a TDE Wallet and TDE Master Encryption Key in Isolated Mode
  In isolated mode, the TDE wallet is associated with a PDB.
- Configuring a Container Database with Isolated Mode PDBs for Oracle Key Vault
  Isolated PDBs have their own virtual wallet, with their own password, in Oracle Key Vault.
- Administering Keystores and TDE Master Encryption Keys in Isolated Mode
  After you create a keystore and a TDE master encryption key in isolated mode, you can perform administration tasks such as rekeying or tagging encryption keys.
- Administering Transparent Data Encryption in Isolated Mode
  You can perform a number of general administrative tasks with Transparent Data Encryption in isolated mode.

**Parent topic:** [Using Transparent Data Encryption](asopart1.md)

### 7.1 About Configuring Isolated Mode

In isolated mode, where a pluggable database (PDB) has its own keystore and keystore password, you manage the keystore and its TDE master encryption keys from the PDB only.

Isolated PDBs have been made available for all on-premises deployments starting with Oracle Database release 19.11 with patch [32235513](https://updates.oracle.com/download/32235513.html). (No patch is necessary for release 19.14 and later.)

Similar to united mode, you must first configure a PDB to use isolated mode by setting the `WALLET_ROOT` and `TDE_CONFIGURATION` parameters. After you set these parameters, you can create and manage the keystore from the PDB. In this way, you can have the following scenario:

- United mode PDBs inherit the TDE configuration from the root container. For example, the keystore that you create in the CDB root will be used by the root’s associated united mode PDBs.

- The PDBs that are configured in isolated mode are allowed to independently create and manage their own keystore. An isolated mode PDB can have its own keystore, independent of the keystore of the CDB root.

This scenario is useful in cases where you have many PDBs that must use one type of keystore, but you have a few PDBs that must use a different type. By different types of keystores, this refers to either TDE wallet or to one of the external keystores that Oracle supports (for example, Oracle Key Vault or Cloud Key Management Service). You cannot have a mixture of different external keystore types in one CDB environment because the Oracle server can load only one PKCS#11 vendor library. If necessary, you can configure these PDBs in isolated mode so that each PDB can use its own keystore.

**Note:**

Oracle Cloud Infrastructure (OCI) cloud tooling does not support isolated PDBs. This non-support applies to Oracle Base Database Service (BaseDB), ExaDB-D, ExaDB-D@Azure, ExaDB-C@C, ADB-C@C, even when Oracle Key Vault provides key management for those database deployments.

**Parent topic:** Managing Keystores and TDE Master Encryption Keys in Isolated Mode

### 7.2 Operations That Are Allowed in Isolated Mode

You can perform many `ADMINISTER KEY MANAGEMENT` operations in isolated mode.

These operations include creating, backing up, opening keystores; changing keystore passwords, merging keystores, closing keystores; creating, activating, tagging, moving, exporting, importing, and migrating encryption keys; and adding, updating, and deleting client secrets.

Table 7-1 describes the `ADMINISTER KEY MANAGEMENT` operations that you can perform in an isolated mode PDB.

Table 7-1 ADMINISTER KEY MANAGEMENT Isolated Mode Operations

| Operation                                                                                       | Syntax                                                                                                                                                                                                                                                                                                 | Isolated Mode Notes                                                                                                                                                                                                                                                                                                                                                                 |
|:------------------------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Creating a keystore                                                                             | `ADMINISTER KEY MANAGEMENT CREATE KEYSTORE `<br>`IDENTIFIED BY isolated_PDB_keystore_password;`                                                                                                                                                                                                        | You can create password-protected, local auto-login, and auto-login keystores in an isolated mode PDB.                                                                                                                                                                                                                                                                              |
| Creating an auto-login keystore                                                                 | `ADMINISTER KEY MANAGEMENT`<br>`CREATE [LOCAL] AUTO_LOGIN KEYSTORE`<br>`FROM KEYSTORE IDENTIFIED BY isolated_PDB_keystore_password;`                                                                                                                                                                   | The isolated PDB knows the keystore location of both password protected and (local) auto-open wallet from `WALLET_ROOT/pdb_guid``/tde`.                                                                                                                                                                                                                                             |
| Opening a keystore                                                                              | `ADMINISTER KEY MANAGEMENT`<br>`SET KEYSTORE OPEN`<br>`[FORCE KEYSTORE]`<br>`IDENTIFIED BY EXTERNAL STORE | isolated_PDB_keystore_password;`                                                                                                                                                           | The `EXTERNAL_STORE` clause retrieves the isolated mode PDB keystore password from a wallet in the `tde_seps` directory in the `WALLET_ROOT``/``PDB-GUID``/location`.                                                                                                                                                                                                               |
| Changing a keystore password                                                                    | `ADMINISTER KEY MANAGEMENT `<br>`ALTER KEYSTORE PASSWORD`<br>`IDENTIFIED BY old_isolated_PDB_keystore_password`<br>`SET new_isolated_PDB_keystore_password  `<br>`WITH BACKUP [USING 'backup_identifier'];`                                                                                            | \-                                                                                                                                                                                                                                                                                                                                                                                  |
| Backing up a TDE wallet                                                                         | `ADMINISTER KEY MANAGEMENT `<br>`BACKUP KEYSTORE `<br>`[USING 'backup_identifier']`<br>`IDENTIFIED BY EXTERNAL STORE | TDE_wallet_password]`<br>`[TO 'TDE_wallet_backup_location'];`                                                                                                                   | \-                                                                                                                                                                                                                                                                                                                                                                                  |
| Merging the contents of one keystore into an existing keystore                                  | `ADMINISTER KEY MANAGEMENT `<br>`MERGE KEYSTORE 'keystore1_location'`<br>`[IDENTIFIED BY TDE_wallet1_password]`<br>`INTO EXISTING KEYSTORE 'keystore2_location'`<br>`IDENTIFIED BY TDE_wallet2_password`<br>`WITH BACKUP [USING 'backup_identifier'];`                                                 | \-                                                                                                                                                                                                                                                                                                                                                                                  |
| Merging the contents of two keystores to create a third keystore                                | `ADMINISTER KEY MANAGEMENT`<br>`MERGE KEYSTORE 'keystore1_location'`<br>`[IDENTIFIED BY TDE_wallet1_password]`<br>`AND KEYSTORE 'keystore2_password'`<br>`[IDENTIFIED BY TDE_wallet2_password]`<br>`INTO NEW KEYSTORE 'keystore3_location'`<br>`IDENTIFIED BY TDE_wallet3_password;`                   | \-                                                                                                                                                                                                                                                                                                                                                                                  |
| Closing a keystore                                                                              | `ADMINISTER KEY MANAGEMENT `<br>`SET KEYSTORE CLOSE`<br>`[IDENTIFIED BY [EXTERNAL STORE | keystore_password]];`                                                                                                                                                                                        | \-                                                                                                                                                                                                                                                                                                                                                                                  |
| Closing the keystore of the CDB root when a PDB in isolated mode has its keystore open          | `ADMINISTER KEY MANAGEMENT `<br>`FORCE KEYSTORE CLOSE`<br>`[IDENTIFIED BY [EXTERNAL STORE | keystore_password]];`                                                                                                                                                                                      | The `FORCE` clause allows the keystore to be closed in the CDB root even when a PDB in isolated mode still has its keystore open                                                                                                                                                                                                                                                    |
| Creating and activating a new TDE master encryption key (rekeying)                              | `ADMINISTER KEY MANAGEMENT `<br>`SET [ENCRYPTION] KEY `<br>`[USING TAG 'tag_name']`<br>`[FORCE KEYSTORE]`<br>`IDENTIFIED BY [EXTERNAL STORE | keystore_password`<br>`]WITH BACKUP [USING 'backup_identifier'];`                                                                                        | \-                                                                                                                                                                                                                                                                                                                                                                                  |
| Creating a user-defined TDE master encryption key for either now (`SET`) or later on (`CREATE`) | `ADMINISTER KEY MANAGEMENT SET | CREATE [ENCRYPTION] KEY`<br>`'mkid:mk | mk' `<br>`[USING ALGORITHM 'algorithm'] `<br>`[FORCE KEYSTORE]`<br>`[USING TAG 'tag_name']`<br>`IDENTIFIED BY EXTERNAL STORE | TDE_wallet_password `<br>`WITH BACKUP [USING 'backup_identifier']`<br>`[CONTAINER = CURRENT];` | \-                                                                                                                                                                                                                                                                                                                                                                                  |
| Activating an existing TDE master encryption key                                                | `ADMINISTER KEY MANAGEMENT `<br>`USE [ENCRYPTION] KEY 'key_id' `<br>`[USING TAG 'tag']`<br>`IDENTIFIED BY`<br>`[EXTERNAL STORE | keystore_password] `<br>`WITH BACKUP [USING 'backup_identifier'];`                                                                                                    | \-                                                                                                                                                                                                                                                                                                                                                                                  |
| Tagging a TDE master encryption key                                                             | `ADMINISTER KEY MANAGEMENT `<br>`SET TAG 'tag' FOR 'key_id'`<br>`IDENTIFIED BY`<br>`[EXTERNAL STORE | keystore_password]`<br>`WITH BACKUP [USING 'backup_identifier'];`                                                                                                                                | \-                                                                                                                                                                                                                                                                                                                                                                                  |
| Exporting a TDE master encryption key                                                           | `ADMINISTER KEY MANAGEMENT `<br>`EXPORT [ENCRYPTION] KEYS `<br>`WITH SECRET secret TO 'filename'`<br>`IDENTIFIED BY TDE_wallet_password`<br>`[WITH IDENTIFIER IN `<br>`{ 'key_id' [, 'key_id' ]... | `<br>`( subquery ) }];`                                                                           | \-                                                                                                                                                                                                                                                                                                                                                                                  |
| Importing a TDE master encryption key                                                           | `ADMINISTER KEY MANAGEMENT `<br>`IMPORT [ENCRYPTION] KEYS `<br>`WITH SECRET secret FROM 'filename'`<br>`IDENTIFIED BY TDE_wallet_password`<br>`WITH BACKUP [USING 'backup_identifier'];`                                                                                                               | \-                                                                                                                                                                                                                                                                                                                                                                                  |
| Migrating an encrypted database from a TDE wallet to Oracle Key Vault                           | `ADMINISTER KEY MANAGEMENT`<br>`SET [ENCRYPTION] KEY`<br>`IDENTIFIED BY Oracle_Key_Vault_password`<br>`[FORCE KEYSTORE]`<br>`MIGRATE USING TDE_wallet_password;`                                                                                                                                       | \-                                                                                                                                                                                                                                                                                                                                                                                  |
| Reverse-migrating an encrypted database from an external keystore to a TDE wallet               | `ADMINISTER KEY MANAGEMENT `<br>`SET [ENCRYPTION] KEY`<br>`IDENTIFIED BY TDE_wallet_password`<br>`REVERSE MIGRATE USING Oracle_Key_Vault_password;`                                                                                                                                                    | \-                                                                                                                                                                                                                                                                                                                                                                                  |
| Adding a client secret                                                                          | `ADMINISTER KEY MANAGEMENT `<br>`ADD SECRET 'secret' FOR CLIENT 'client_identifier'`<br>`[USING TAG 'tag_name' ]`<br>`IDENTIFIED BY [EXTERNAL STORE | isolated_PDB_keystore_password]`<br>`WITH BACKUP [USING 'backup_identifier'];`                                                                   | \-                                                                                                                                                                                                                                                                                                                                                                                  |
| Updating a client secret                                                                        | `ADMINISTER KEY MANAGEMENT `<br>`UPDATE SECRET 'secret'`<br>`FOR CLIENT 'client_identifier'`<br>`[USING TAG 'tag_name' ]`<br>`IDENTIFIED BY [EXTERNAL STORE | keystore_password]`<br>`WITH BACKUP [USING 'backup_identifier'];`                                                                        | \-                                                                                                                                                                                                                                                                                                                                                                                  |
| Deleting a client secret                                                                        | `ADMINISTER KEY MANAGEMENT `<br>`DELETE SECRET`<br>`FOR CLIENT 'client_identifier'`<br>`IDENTIFIED BY [EXTERNAL STORE | keystore_password]`<br>`WITH BACKUP [USING 'backup_identifier'];`                                                                                                              | \-                                                                                                                                                                                                                                                                                                                                                                                  |
| Isolating a PDB                                                                                 | `ADMINISTER KEY MANAGEMENT `<br>`ISOLATE KEYSTORE`<br>`IDENTIFIED BY isolated_keystore_password`<br>`FROM ROOT KEYSTORE`<br>`[FORCE KEYSTORE]`<br>`IDENTIFIED BY [EXTERNAL STORE | united_keystore_password]`<br>`WITH BACKUP [USING backup_id];`                                                      | This operation performs two actions. First, it changes the `TDE_CONFIGURATION` of the PDB so that it is in isolated mode. Second, it moves the PDB's current and previously active TDE master encryption keys from the root keystore to a newly-created isolated keystore of the PDB, having its own isolated keystore password, where the PDB will be able to manage its own keys. |

**Parent topic:** Managing Keystores and TDE Master Encryption Keys in Isolated Mode

### 7.3 Operations That Are Not Allowed in an Isolated Mode PDB

There are several `ADMINISTER KEY MANAGEMENT` operations that you cannot perform in an isolated mode PDB.

These operations include the following:

- Using the `CONTAINER = ALL` clause to create a new TDE master encryption key for later use in each pluggable database (PDB)

- Moving encryption keys from the keystore of the CDB root into a keystore of a PDB that is configured in isolated mode

**Parent topic:** Managing Keystores and TDE Master Encryption Keys in Isolated Mode

### 7.4 Configuring the Keystore Location and Type for Isolated Mode

For isolated mode, you can configure the keystore location and type by using only parameters or a combination of parameters and the `ALTER SYSTEM` statement.

- Configuring the Keystore Location and Keystore Type for an Isolated Mode CDB
  You can configure isolated mode by setting `WALLET_ROOT` in the initialization parameter file in the CDB root and `TDE_CONFIGURATION` in the PDB you want to isolate.
- Example: Restoring an Older Version of a Control File
  You can set `TDE_CONFIGURATION` if you have an older version of a control file that must be restored and only a few PDBs were configured in isolated mode.
- Example: Addressing the Problem of a Lost Control File
  You can address the problem of a lost control file by using the `ALTER SYSTEM` statement.
- Example: Configuring Isolated Mode in an Oracle Real Application Clusters Environment
  You can use `ALTER SYSTEM` to configure isolated mode in an Oracle Real Application Clusters (Oracle RAC) environment.

**Parent topic:** Managing Keystores and TDE Master Encryption Keys in Isolated Mode

#### 7.4.1 Configuring the Keystore Location and Keystore Type for an Isolated Mode CDB

You can configure isolated mode by setting `WALLET_ROOT` in the initialization parameter file in the CDB root and `TDE_CONFIGURATION` in the PDB you want to isolate.

1.  In the root, ensure that the `WALLET_ROOT` parameter is set correctly.
    For example:
        SHOW PARAMETER WALLET_ROOT
2.  Connect to the isolated mode PDB as a user who has been granted the `ALTER SYSTEM` privilege.
    For example:
        CONNECT sec_admin@pdb_name
3.  As a user who has the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege, run the following statement in the PDB:
        ADMINISTER KEY MANAGEMENT CREATE KEYSTORE IDENTIFIED BY "iso_PDB_TDE_wallet_password";

    This statement does the following:
    - Sets the `TDE_CONFIGURATION` in the isolated PDB to `FILE`.
    - Creates the directories `pdb_guid``/tde` under `WALLET_ROOT`.
    - Creates a new TDE wallet with its own password (which might be not known to the CDB administrator).
4.  Check the configuration.
    - To check the `TDE_CONFIGURATION` parameter setting:

          SHOW PARAMETER TDE_CONFIGURATION

      The output should reflect the keystore configuration that you set for the current PDB. If it shows a different keystore configuration (for example, `FILE` if you had set it to `OKV`), then the setting may be showing the keystore configuration that was set for the CDB root, in united mode.

    - To check the keystore mode:

          SELECT KEYSTORE_MODE FROM V$ENCRYPTION_WALLET;

      The output should be `ISOLATED`.

After you configure isolated mode, the CDB root keystore that was available to the PDB when it was in united mode is no longer available to this PDB. At this stage, the PDB is configured to use its own keystore. If the `KEYSTORE_CONFIGURATION` parameter was `FILE` (meaning that the PDB is configured to use a TDE wallet), then the keystore location configured for the PDB is `WALLET_ROOT/PDB-GUID/tde`. If a keystore exists at that location and contains a TDE master encryption key, then that key is only available to this PDB, not to any other PDB. If no keystore exists at that location, you now can now proceed to create a TDE wallet and set a TDE master encryption key. If you later decide that you want the isolated mode PDB to become a united mode PDB again, then you can use the `ADMINISTER KEY MANAGEMENT UNITE KEYSTORE` statement. When you run `ADMINISTER KEY MANAGEMENT UNITE KEYSTORE`, it moves the keys from the PDB's keystore to the keystore of the CDB root, but it leaves any client secrets behind. So if there were no client secrets in the first place, then it would leave the PDB's keystore essentially "empty". It can now be backed up, and removed. Always back up keystores before you remove them, even empty keystores.

**Related Topics**

- [Configuring United Mode with the Initialization Parameter File and ALTER SYSTEM](managing-keystores-encryption-keys-in-united-mode.md)
- Uniting a Pluggable Database Keystore

**Parent topic:** Configuring the Keystore Location and Type for Isolated Mode

#### 7.4.2 Example: Restoring an Older Version of a Control File

You can set `TDE_CONFIGURATION` if you have an older version of a control file that must be restored and only a few PDBs were configured in isolated mode.

When the CDB root and the PDB are both in the mount state, then you can only change the PDB’s keystore configuration from the CDB root.

1.  Log in to the CDB root as a user who was granted the `SYSDBA` administrative privilege.

2.  For each PDB that you want to change, use the following syntax:

        ALTER SYSTEM SET TDE_CONFIGURATION="CONTAINER=pdb_name;KEYSTORE_CONFIGURATION=keystore_type" SCOPE=memory;

    For example, for the `hrpdb` and `salespdb` PDBs using `FILE` (for TDE wallets) as the keystore type:

        ALTER SYSTEM SET TDE_CONFIGURATION="CONTAINER=hrpdb;KEYSTORE_CONFIGURATION=FILE" SCOPE=memory;
        ALTER SYSTEM SET TDE_CONFIGURATION="CONTAINER=salespdb;KEYSTORE_CONFIGURATION=FILE" SCOPE=memory;

3.  After you set the `TDE_CONFIGURATION` parameter for each PDB, log in to the CDB root and then set `TDE_CONFIGURATION` for the CDB root itself.

        ALTER SYSTEM SET TDE_CONFIGURATION="KEYSTORE_CONFIGURATION=FILE";

    At this stage, CDB root is in the mounted state. The value of the `TDE_CONFIGURATION` parameter that was set using `ALTER SYSTEM` with the `CONTAINER` attribute is only present in the memory of the CDB root. To ensure that the configuration is properly applied to each PDB, you must close and then reopen the PDB. When an isolated mode PDB is opened, the configuration set by the `ALTER SYSTEM` statement that was issued in the CDB root is read from the control file and then is automatically applied to the PDB.

4.  Connect to each PDB and then close and reopen the PDB.

        ALTER PLUGGABLE DATABASE pdb_name CLOSE IMMEDIATE;
        ALTER PLUGGABLE DATABASE pdb_name OPEN;

**Parent topic:** Configuring the Keystore Location and Type for Isolated Mode

#### 7.4.3 Example: Addressing the Problem of a Lost Control File

You can address the problem of a lost control file by using the `ALTER SYSTEM` statement.

Running these statements with `SCOPE` set to memory will store the `CONTAINER` value in memory. When you open the isolated PDB, this configuration will automatically be updated for the PDB.

If you are using an Oracle Data Guard environment, then to correct the control file, run these statements on both the primary and the standby databases.

1.  Log in to the CDB root as a user who was granted the `SYSDBA` administrative privilege.

2.  If you are unsure of the exact state of the system, then you should run `ALTER SYSTEM` with `RESET`.

    For example:

        ALTER SYSTEM RESET TDE_CONFIGURATION SCOPE=memory;

3.  For each PDB that you want to change, use the following syntax:

        ALTER SYSTEM SET TDE_CONFIGURATION="CONTAINER=pdb_name;KEYSTORE_CONFIGURATION=FILE" SCOPE=memory;

    For example, for the `hrpdb` and `salespdb` PDBs with `FILE` (for TDE wallets) as the keystore type:

        ALTER SYSTEM SET TDE_CONFIGURATION="CONTAINER=hrpdb;KEYSTORE_CONFIGURATION=FILE" SCOPE=memory;
        ALTER SYSTEM SET TDE_CONFIGURATION="CONTAINER=salespdb;KEYSTORE_CONFIGURATION=FILE" SCOPE=memory;

4.  After you set the `TDE_CONFIGURATION` parameter for each PDB, log in to the CDB root and then set `TDE_CONFIGURATION` for the CDB root itself.

        ALTER SYSTEM SET TDE_CONFIGURATION="KEYSTORE_CONFIGURATION=FILE";

    At this stage, CDB root is in the mounted state. The value of the `TDE_CONFIGURATION` parameter that was set using `ALTER SYSTEM` with the `CONTAINER` attribute is only present in the memory of the CDB root. To ensure that the configuration is properly applied to each PDB, you must close and then reopen the PDB. When an isolated mode PDB is opened, the configuration set by the `ALTER SYSTEM` statement that was issued in the CDB root is read from the control file and then is automatically applied to the PDB.

5.  Connect to each PDB and then close and reopen the PDB.

        ALTER PLUGGABLE DATABASE pdb_name CLOSE IMMEDIATE;
        ALTER PLUGGABLE DATABASE pdb_name OPEN;

**Parent topic:** Configuring the Keystore Location and Type for Isolated Mode

#### 7.4.4 Example: Configuring Isolated Mode in an Oracle Real Application Clusters Environment

You can use `ALTER SYSTEM` to configure isolated mode in an Oracle Real Application Clusters (Oracle RAC) environment.

- To ensure that the effect of the `ALTER SYSTEM` statement is applied on each Oracle RAC node, specify the wildcard (`*`) in the `SID` clause of the `ALTER SYSTEM` statement, as follows. You can run this statement from either the CDB root or a PDB.

      ALTER SYSTEM SET TDE_CONFIGURATION="KEYSTORE_CONFIGURATION=keystore_type" SID='*';

**Parent topic:** Configuring the Keystore Location and Type for Isolated Mode

### 7.5 Configuring a TDE Wallet and TDE Master Encryption Key in Isolated Mode

In isolated mode, the TDE wallet is associated with a PDB.

- About Configuring a TDE Wallet in Isolated Mode
  You can create all types of TDE wallets in isolated mode: password-protected, password protected with the credential provided from an external store, auto-login, local auto-login.
- Step 1: Create a TDE Wallet in a PDB Configured in Isolated Mode
  A password-protected TDE wallet requires a password to protect the keystore keys and credentials.
- Step 2: Open the TDE Wallet in an Isolated Mode PDB
  To open a TDE wallet in isolated mode, you must use the `ADMINISTER KEY MANAGEMENT` statement with the `SET KEYSTORE OPEN` clause.
- Step 3: Set the TDE Master Encryption Key in the TDE Wallet of the Isolated Mode PDB
  To set the TDE master encryption key in a TDE wallet in an isolated mode PDB, use the `ADMINISTER KEY MANAGEMENT` statement with the `SET KEY` clause.
- Step 4: Encrypt Your Data in Isolated Mode
  Now that you have completed the configuration, you can begin to encrypt data in the PDB.

**Parent topic:** Managing Keystores and TDE Master Encryption Keys in Isolated Mode

#### 7.5.1 About Configuring a TDE Wallet in Isolated Mode

You can create all types of TDE wallets in isolated mode: password-protected, password protected with the credential provided from an external store, auto-login, local auto-login.

To enable encryption in the PDB after it is configured in isolated mode with the `KEYSTORE_CONFIGURATION` attribute set to `FILE` (that is, to use a TDE wallet), you must create a TDE wallet, open the TDE wallet, and then set a TDE master encryption key in the TDE wallet. Afterward, you can begin to encrypt data for tables and tablespaces that will be accessible in the PDB.

In a multitenant environment, you can create a secure external store to hold the credentials of the TDE wallet. This feature enables you to hide the keystore password: it removes the need for storing the wallet password in any script or tool that accesses the database without user intervention, such as an overnight batch script. When the `WALLET_ROOT` parameter is specified, the location of the external store for the CDB root is `WALLET_ROOT``/tde_seps` and for the PDB it is `WALLET_ROOT``/``pdb_guid``/tde_seps`. When the `WALLET_ROOT` parameter is set, there is no longer a single central external store, so when a keystore password is updated, the corresponding external store must be updated as well. When the `WALLET_ROOT` parameter is not specified, then the location of the external store is the same for both the CDB root and for every PDB. The external store location must then be set by the `EXTERNAL_KEYSTORE_CREDENTIAL_LOCATION` initialization parameter. When the `WALLET_ROOT` parameter is not specified, then there is a single central external store, so when you update the keystore password, only the central external store at the `EXTERNAL_KEYSTORE_CREDENTIAL_LOCATION` must be updated.

In a multitenant environment, different PDBs can access this external store location when you run the `ADMINISTER KEY MANAGEMENT` statement using the `IDENTIFIED BY EXTERNAL STORE` clause. This way, you can centrally locate the password and then update it only once in the external store.

**Related Topics**

- [Configuring an External Store for a Keystore Password](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Configuring a TDE Wallet and TDE Master Encryption Key in Isolated Mode

#### 7.5.2 Step 1: Create a TDE Wallet in a PDB Configured in Isolated Mode

A password-protected TDE wallet requires a password to protect the keystore keys and credentials.

1.  Connect to the isolated mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Use the `SHOW PARAMETER` command to confirm that `WALLET_ROOT` is set, and `TDE_CONFIGURATION` is set to `KEYSTORE_CONFIGURATION=FILE`.
3.  Run the `ADMINISTER KEY MANAGEMENT` SQL statement to create the keystore using the following syntax:
        ADMINISTER KEY MANAGEMENT CREATE KEYSTORE IDENTIFIED BY TDE_wallet_password;

    This command creates the `/tde` directory under `WALLET_ROOT/``pdb_guid` (unless it already exists), and creates a password-protected TDE wallet in this directory. If `WALLET_ROOT` points to a shared directory in ASM (`+DATA/DB_UNIQUE_NAME`), then the `pdb_guid``/tde` subdirectory and the TDE wallet is auto-created by the `CREATE KEYSTORE` statement.

    In this specification, `TDE_wallet_password` is the password of the keystore that you, the security administrator, creates.

    For example, to create the TDE wallet in the `WALLET_ROOT/``pdb_guid``/tde` directory:

        ADMINISTER KEY MANAGEMENT CREATE KEYSTORE IDENTIFIED BY password;

        keystore altered.

After you complete these steps, the `ewallet.p12` file, which is the TDE wallet, appears in the wallet location.

**Related Topics**

- [Creating an Auto-Login or a Local Auto-Login Software Keystore](configuring-transparent-data-encryption.md)

**Parent topic:** Configuring a TDE Wallet and TDE Master Encryption Key in Isolated Mode

#### 7.5.3 Step 2: Open the TDE Wallet in an Isolated Mode PDB

To open a TDE wallet in isolated mode, you must use the `ADMINISTER KEY MANAGEMENT` statement with the `SET KEYSTORE OPEN` clause.

1.  Connect to the isolated mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Run the `ADMINISTER KEY MANAGEMENT` statement to open the TDE wallet.
        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN
        IDENTIFIED BY TDE_wallet_password | EXTERNAL STORE;

        Keystore altered.

    To switch over to opening the password-protected TDE wallet when an auto-login wallet is configured and is currently open, specify the `FORCE KEYSTORE` clause as follows.

        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN
        FORCE KEYSTORE
        IDENTIFIED BY TDE_wallet_password | EXTERNAL STORE;

        Keystore altered.

    Here, the `IDENTIFIED BY EXTERNAL STORE` clause is included in the statement because the wallet credentials exist in an external store. This enables the password-protected TDE wallet to be opened without specifying the TDE wallet password within the statement itself.

    If the `WALLET_ROOT` parameter has been set, then Oracle Database finds the external store by searching in this path: `WALLET_ROOT``/``pdb_guid``/tde_seps`.
3.  Confirm that the TDE wallet is open.
        SELECT STATUS FROM V$ENCRYPTION_WALLET;

**Related Topics**

- [About Opening TDE Wallets](configuring-transparent-data-encryption.md)

**Parent topic:** Configuring a TDE Wallet and TDE Master Encryption Key in Isolated Mode

#### 7.5.4 Step 3: Set the TDE Master Encryption Key in the TDE Wallet of the Isolated Mode PDB

To set the TDE master encryption key in a TDE wallet in an isolated mode PDB, use the `ADMINISTER KEY MANAGEMENT` statement with the `SET KEY` clause.

1.  Log in to the isolated mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Ensure that the database is open in `READ WRITE` mode.
    To find the status, run the `show pdbs` command.
3.  Run the `ADMINISTER KEY MANAGEMENT` SQL statement to set the key in the TDE wallet.
    For example, if the wallet of the PDB is password-protected, the PDB is open, and the wallet of the PDB is open:
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

    - `FORCE KEYSTORE` should be included if the keystore is closed. This automatically opens the keystore before setting the TDE master encryption key. The `FORCE KEYSTORE` clause also switches over to opening the password-protected TDE wallet when an auto-login keystore is configured and is currently open.

    - `IDENTIFIED BY` specifies the keystore password. Alternatively, if the wallet password is in an external store, you can use the `IDENTIFIED BY EXTERNAL STORE` clause.
4.  Confirm that the TDE master encryption key is set.
        SELECT MASTERKEY_ACTIVATED FROM V$DATABASE_KEY_INFO;

    The output should be `YES`.

**Related Topics**

- [About Setting the TDE Wallet TDE Master Encryption Key](configuring-transparent-data-encryption.md)

**Parent topic:** Configuring a TDE Wallet and TDE Master Encryption Key in Isolated Mode

#### 7.5.5 Step 4: Encrypt Your Data in Isolated Mode

Now that you have completed the configuration, you can begin to encrypt data in the PDB.

**Related Topics**

- [Encrypting Columns in Tables](configuring-transparent-data-encryption.md)
- [Encryption Conversions for Tablespaces and Databases](configuring-transparent-data-encryption.md)

**Parent topic:** Configuring a TDE Wallet and TDE Master Encryption Key in Isolated Mode

### 7.6 Configuring a Container Database with Isolated Mode PDBs for Oracle Key Vault

Isolated PDBs have their own virtual wallet, with their own password, in Oracle Key Vault.

- About Configuring an External Keystore in Isolated Mode
  You can configure an external keystore for a PDB when the PDB is configured in isolated mode.
- Step 1: Configure Isolated PDBs for Oracle Key Vault
  You can configure isolated mode PDBs for Oracle Key Vault by setting the `TDE_CONFIGURATION` parameter.
- Step 2: Open the External Keystore in an Isolated Mode PDB
  If the isolated PDB does not have an auto-open connection into the external keystore, then you must open it manually before your open the PDB.
- Step 3: Set the First TDE Master Encryption Key in the External Keystore
  After you have opened the external keystore in an isolated mode PDB, you are ready to set the TDE master encryption key for the PDB.
- Step 4: Encrypt Your Data in Isolated Mode
  Now that you have completed the configuration, you can begin to encrypt data in the PDB.

**Parent topic:** Managing Keystores and TDE Master Encryption Keys in Isolated Mode

#### 7.6.1 About Configuring an External Keystore in Isolated Mode

You can configure an external keystore for a PDB when the PDB is configured in isolated mode.

To configure an external keystore for a PDB in isolated mode, you first must set the `WALLET_ROOT` parameter. This is necessary for two reasons: first, to have support for migrating to a TDE wallet in the future, and second, because the configuration file for Oracle Key Vault is retrieved from a location under `WALLET_ROOT`. Afterwards, you must set the `KEYSTORE_CONFIGURATION` attribute of the `TDE_CONFIGURATION` parameter to `OKV`, open the configured external keystore, and then set the TDE master encryption key for the PDB. After you complete these tasks, you can begin to encrypt data in your database.

How you specify the `IDENTIFIED BY` clause when you run the `ADMINISTER KEY MANAGEMENT` statement depends on the type of external keystore. Use the following syntax:

    IDENTIFIED BY EXTERNAL STORE|Oracle_Key_Vault_password

Enter the Oracle Key Vault password that was given during the Oracle Key Vault client installation. If at that time no password was given, then the password in the `ADMINISTER KEY MANAGEMENT` statement becomes `NULL`.

**Parent topic:** Configuring a Container Database with Isolated Mode PDBs for Oracle Key Vault

#### 7.6.2 Step 1: Configure Isolated PDBs for Oracle Key Vault

You can configure isolated mode PDBs for Oracle Key Vault by setting the `TDE_CONFIGURATION` parameter.

1.  If the `WALLET_ROOT` parameter is set, then install the Oracle Key Vault client software into the `WALLET_ROOT/``pdb_guid``/okv` directory.
2.  Log in to the database instance as a user who has been granted the `ALTER SYSTEM` administrative privilege.
3.  Set the `TDE_CONFIGURATION` dynamic initialization parameter to specify the keystore type by using the following syntax:
        ALTER SYSTEM SET TDE_CONFIGURATION="KEYSTORE_CONFIGURATION=keystore_type" SCOPE=BOTH SID = '*';

    In this specification:

    - `keystore_type` can be `OKV`, to configure an Oracle Key Vault keystore.

    For example, to configure your database to use Oracle Key Vault:

        ALTER SYSTEM SET TDE_CONFIGURATION="KEYSTORE_CONFIGURATION=OKV" SCOPE=BOTH SID = '*';

**Parent topic:** Configuring a Container Database with Isolated Mode PDBs for Oracle Key Vault

#### 7.6.3 Step 2: Open the External Keystore in an Isolated Mode PDB

If the isolated PDB does not have an auto-open connection into the external keystore, then you must open it manually before your open the PDB.

1.  Log in to the isolated mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Open the external keystore as follows, by enclosing the password in double quotation marks:
    For example:
        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN
        IDENTIFIED BY Oracle_Key_Vault_password;
3.  Repeat this procedure each time you restart the database instance.
    You must open the keystore of the CDB root first.

**Related Topics**

- [About Opening the Connection to Oracle Key Vault](managing-keystores-encryption-keys-in-united-mode.md)

**Parent topic:** Configuring a Container Database with Isolated Mode PDBs for Oracle Key Vault

#### 7.6.4 Step 3: Set the First TDE Master Encryption Key in the External Keystore

After you have opened the external keystore in an isolated mode PDB, you are ready to set the TDE master encryption key for the PDB.

- Setting the TDE Master Encryption Key in the Isolated Mode External Keystore
  You should complete this procedure if you have not previously configured an external keystore for Transparent Data Encryption.
- Migration of a Previously Configured Encryption Key in Isolated Mode
  You must migrate the previously configured master encryption key if you previously configured a TDE wallet.

**Parent topic:** Configuring a Container Database with Isolated Mode PDBs for Oracle Key Vault

##### 7.6.4.1 Setting the TDE Master Encryption Key in the Isolated Mode External Keystore

You should complete this procedure if you have not previously configured an external keystore for Transparent Data Encryption.

1.  Log in to the isolated mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Ensure that the database is open in `READ WRITE` mode.
    You can set the TDE master encryption key if `OPEN_MODE` is set to `READ WRITE`. To find the status, run the `show pdbs` command.
3.  Set the new TDE master encryption key by using the following syntax:
        ADMINISTER KEY MANAGEMENT SET KEY
        [USING TAG 'tag']
        [FORCE KEYSTORE]
        IDENTIFIED BY EXTERNAL STORE|Oracle_Key_Vault_password;

    In this specification:

    - `FORCE KEYSTORE` temporarily opens the password-protected TDE wallet for this operation if the TDE wallet is closed, if an auto-login TDE wallet is configured and is currently open, or if a password-protected TDE wallet is configured and is currently closed.

    - `IDENTIFIED BY` can be one of the following settings:

      - `EXTERNAL STORE` uses the keystore password stored in the external store to perform the keystore operation.

      - `Oracle_Key_Vault_password` is the the password that was given during the Oracle Key Vault client installation. If at that time no password was given, then the password in the `ADMINISTER KEY MANAGEMENT` statement becomes `NULL`.

    For example:

        ADMINISTER KEY MANAGEMENT SET KEY
        USING TAG 'sessionid=3205062574:terminal=xcvt'
        FORCE KEYSTORE
        IDENTIFIED BY EXTERNAL STORE;

        keystore altered.
4.  Confirm that the TDE master encryption key is set.
        SELECT MASTERKEY_ACTIVATED FROM V$DATABASE_KEY_INFO;

    The output should be `YES`.

**Related Topics**

- [About Setting the External Keystore TDE Master Encryption Key](managing-keystores-encryption-keys-in-united-mode.md)

**Parent topic:** Step 3: Set the First TDE Master Encryption Key in the External Keystore

##### 7.6.4.2 Migration of a Previously Configured Encryption Key in Isolated Mode

You must migrate the previously configured master encryption key if you previously configured a TDE wallet.

**Related Topics**

- [Migration of an Encrypted Database from a TDE Wallet to Oracle Key Vault or OCI KMS](managing-keystores-encryption-keys-in-united-mode.md)

**Parent topic:** Step 3: Set the First TDE Master Encryption Key in the External Keystore

#### 7.6.5 Step 4: Encrypt Your Data in Isolated Mode

Now that you have completed the configuration, you can begin to encrypt data in the PDB.

**Related Topics**

- [Encrypting Columns in Tables](configuring-transparent-data-encryption.md)
- [Encryption Conversions for Tablespaces and Databases](configuring-transparent-data-encryption.md)

**Parent topic:** Configuring a Container Database with Isolated Mode PDBs for Oracle Key Vault

### 7.7 Administering Keystores and TDE Master Encryption Keys in Isolated Mode

After you create a keystore and a TDE master encryption key in isolated mode, you can perform administration tasks such as rekeying or tagging encryption keys.

To change the password of an external keystore, you must use the administrative interface of the external keystore. You cannot perform this operation by using the `ADMINISTER KEY MANAGEMENT` statement.

- Changing the Keystore Password in Isolated Mode
  You can change the password of a TDE wallet when the PDB is in isolated mode.
- Backing Up a Password-Protected TDE Wallet in Isolated Mode
  The `BACKUP KEYSTORE` clause of the `ADMINISTER KEY MANAGEMENT` statement backs up a password-protected TDE wallet.
- Merging TDE Wallets in Isolated Mode
  In isolated mode, you can merge TDE wallets.
- Closing Keystores in Isolated Mode
  You can close both software and external keystores in isolated mode, unless the system tablespace is encrypted.
- Creating a User-Defined TDE Master Encryption Key in Isolated Mode
  To create a user-defined TDE master encryption key, use the `ADMINISTER KEY MANAGEMENT` statement with the `SET | CREATE [ENCRYPTION] KEY` clause.
- Creating a TDE Master Encryption Key for Later Use in Isolated Mode
  A keystore must be open before you can create a TDE master encryption key for use later on in isolated mode.
- Activating a TDE Master Encryption Key in Isolated Mode
  To activate a TDE master encryption key in isolated mode, you must open the keystore and use `ADMINISTER KEY MANAGEMENT` with the `USE KEY` clause.
- Rekeying the TDE Master Encryption Key in Isolated Mode
  You can use the `ADMINISTER KEY MANAGEMENT` statement with the `SET KEY` clause to rekey a TDE master encryption key.
- Moving a TDE Master Encryption Key into a New Keystore in Isolated Mode
  In isolated mode, you can move an existing TDE master encryption key into a new TDE wallet from an existing password TDE wallet.
- Creating a Custom Attribute Tag in Isolated Mode
  To create a custom attribute tag in isolated mode, you must use the `SET TAG` clause of the `ADMINISTER KEY MANAGEMENT` statement.
- Exporting and Importing the TDE Master Encryption Key in Isolated Mode
  You can export and import the TDE master encryption key in different ways in isolated mode.
- Storing Oracle Database Secrets in Isolated Mode
  Secrets are data that support internal Oracle Database features that integrate external clients such as Oracle GoldenGate into the database.
- Migrating Keystores in Isolated Mode
  You can perform migration and reverse migration operations between software keystores and external keystores in isolated mode.
- Uniting a Pluggable Database Keystore
  Uniting a PDB keystore moves the TDE master encryption keys from the PDB keystore into the keystore of the CDB root. This enables the administrator of the keystore of the CDB root to manage the keys.
- Creating a Keystore When the PDB Is Closed
  When you create a keystore in a PDB that is closed, the new keystore is empty and the PDB is converted to isolated mode.

**Parent topic:** Managing Keystores and TDE Master Encryption Keys in Isolated Mode

#### 7.7.1 Changing the Keystore Password in Isolated Mode

You can change the password of a TDE wallet when the PDB is in isolated mode.

To change the password of an external keystore, you must use the administrative interface of the external keystore. You cannot perform this operation by using the `ADMINISTER KEY MANAGEMENT` statement.

- Changing the Password-Protected TDE Wallet Password in Isolated Mode
  To change the password of a password-protected TDE wallet in isolated mode, you must use the `ADMINISTER KEY MANAGEMENT` statement.
- Changing the Password of an External Keystore in Isolated Mode
  To change the password of an external keystore, you must close the external keystore and then change the password from the external keystore’s management interface.

**Parent topic:** Administering Keystores and TDE Master Encryption Keys in Isolated Mode

##### 7.7.1.1 Changing the Password-Protected TDE Wallet Password in Isolated Mode

To change the password of a password-protected TDE wallet in isolated mode, you must use the `ADMINISTER KEY MANAGEMENT` statement.

You can change this password at any time, as per the security policies, compliance guidelines, and other security requirements of your site. As part of the command to change the password, you will be forced to specify the `WITH BACKUP` clause, and thus forced to make a backup of the current TDE wallet. During the password change operation, Transparent Data Encryption operations such as encryption and decryption will continue to work normally. You can change this password at any time. You may want to change this password if you think it was compromised.

1.  Connect to the isolated mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Change the password for the TDE wallet by using the following syntax:
        ADMINISTER KEY MANAGEMENT ALTER KEYSTORE PASSWORD
        [FORCE KEYSTORE]
        IDENTIFIED BY
        old_password SET new_password
        [WITH BACKUP [USING 'backup_identifier']];

    In this specification:

    - `FORCE KEYSTORE` temporarily opens the password-protected TDE wallet for this operation if the TDE wallet is closed, if an auto-login TDE wallet is configured and is currently open, or if a password-protected TDE wallet is configured and is currently closed.

    - `old_password` is the current TDE wallet password that you want to change.

    - `new_password` is the new password that you set for the TDE wallet.

    The following example creates a backup of the TDE wallet and then changes the TDE wallet password:

        ADMINISTER KEY MANAGEMENT ALTER KEYSTORE PASSWORD
        IDENTIFIED BY
        old_password SET new_password
        WITH BACKUP USING 'pwd_change';

        keystore altered.

    This example performs the same operation but uses the `FORCE KEYSTORE` clause in case the auto-login TDE wallet is in use or the password-protected TDE wallet is closed.

        ADMINISTER KEY MANAGEMENT ALTER KEYSTORE PASSWORD
        FORCE KEYSTORE
        IDENTIFIED BY
        old_password SET new_password
        WITH BACKUP USING 'pwd_change';

        keystore altered.

**Related Topics**

- [Performing Operations That Require a Keystore Password](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Changing the Keystore Password in Isolated Mode

##### 7.7.1.2 Changing the Password of an External Keystore in Isolated Mode

To change the password of an external keystore, you must close the external keystore and then change the password from the external keystore’s management interface.

1.  Connect to the isolated mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Close the external keystore.
    - For example:

          ADMINISTER KEY MANAGEMENT SET KEYSTORE CLOSE
          IDENTIFIED BY "external_key_manager_password";

    - For an external keystore whose password is stored externally:

          ADMINISTER KEY MANAGEMENT SET KEYSTORE CLOSE
          IDENTIFIED BY EXTERNAL STORE;
3.  Update the credentials of the external store to use "`new_external_key_manager_password``"`.
    Currently, the external store contains the old credentials, which would no longer work.

    For example:

        ADMINISTER KEY MANAGEMENT
        UPDATE SECRET 'new_external_key_manager_password'
        FOR CLIENT 'TDE_WALLET'
        TO LOCAL AUTO_LOGIN KEYSTORE '/etc/ORACLE/WALLETS/orcl/external_store';
4.  Open the external keystore.
    For example:

        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN
        IDENTIFIED BY "new_external_key_manager_password";

    For an external keystore whose password is stored externally:

        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN
        IDENTIFIED BY EXTERNAL STORE;

**Related Topics**

- [Performing Operations That Require a Keystore Password](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Changing the Keystore Password in Isolated Mode

#### 7.7.2 Backing Up a Password-Protected TDE Wallet in Isolated Mode

The `BACKUP KEYSTORE` clause of the `ADMINISTER KEY MANAGEMENT` statement backs up a password-protected TDE wallet.

1.  Connect to the isolated mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Back up the keystore by using the following syntax:
        ADMINISTER KEY MANAGEMENT BACKUP KEYSTORE
        [USING 'backup_identifier']
        [FORCE KEYSTORE]
        IDENTIFIED BY [EXTERNAL STORE | TDE_wallet_password]
        [TO 'TDE_wallet_location'];

    In this specification:

    - `USING` `backup_identifier` is an optional string that you can provide to identify the backup. Enclose this identifier in single quotation marks (`' '`). This identifier is appended to the named keystore file (for example, `ewallet_``time-stamp``_emp_key_backup.p12`).

    - `FORCE KEYSTORE` temporarily opens the password-protected TDE wallet for this operation. You must open the TDE wallet for this operation.

    - `IDENTIFIED BY` is required for the `BACKUP KEYSTORE` operation on a password-protected keystore because although the backup is simply a copy of the existing keystore, the status of the TDE master encryption key in the password-protected keystore must be set to `BACKED UP` and for this change the keystore password is required.

    - `TDE_wallet_location` is the path at which the backup TDE wallet is stored. This setting is restricted to the PDB when the PDB lockdown profile `EXTERNAL_FILE_ACCESS` setting is blocked in the PDB or when the `PATH_PREFIX` variable was set when the PDB was created. If you do not specify the `TDE_wallet_location`, then the backup is created in the same directory as the original TDE wallet. Enclose this location in single quotation marks (`' '`).

    The following example backs up a TDE wallet in the same location as the source TDE wallet.

        ADMINISTER KEY MANAGEMENT BACKUP KEYSTORE
        USING 'hr.emp_keystore'
        FORCE KEYSTORE
        IDENTIFIED BY
        'TDE_wallet_password';

        keystore altered.

    In the following version, the password for the TDE wallet is stored externally, so the `EXTERNAL STORE` clause is used.

        ADMINISTER KEY MANAGEMENT BACKUP KEYSTORE
        USING 'hr.emp_keystore'
        FORCE KEYSTORE
        IDENTIFIED BY EXTERNAL STORE;

    After you run this statement, an `ewallet_``identifier``.p12` file (for example, `ewallet_``time-stamp``_hr.emp_keystore.p12`) appears in the TDE wallet backup location.

**Related Topics**

- [Backing Up Password-Protected Software Keystores](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Administering Keystores and TDE Master Encryption Keys in Isolated Mode

#### 7.7.3 Merging TDE Wallets in Isolated Mode

In isolated mode, you can merge TDE wallets.

- Merging One TDE Wallet into an Existing TDE Wallet in Isolated Mode
  In isolated mode, you can use the `ADMINISTER KEY MANAGEMENT` statement with the `MERGE KEYSTORE` clause to merge one TDE wallet into another existing TDE wallet.
- Merging Two TDE Wallets into a Third New TDE Wallet in Isolated Mode
  In isolated mode, you can merge two TDE wallets into a third new TDE wallet, so that the two existing TDE wallets are not changed and the new TDE wallet contains the keys of both source TDE wallets.

**Parent topic:** Administering Keystores and TDE Master Encryption Keys in Isolated Mode

##### 7.7.3.1 Merging One TDE Wallet into an Existing TDE Wallet in Isolated Mode

In isolated mode, you can use the `ADMINISTER KEY MANAGEMENT` statement with the `MERGE KEYSTORE` clause to merge one TDE wallet into another existing TDE wallet.

1.  Connect to the isolated mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Merge the TDE wallets by using the following syntax:
        ADMINISTER KEY MANAGEMENT MERGE KEYSTORE 'TDE_wallet1_location'
        [IDENTIFIED BY TDE_wallet1_password]
        INTO EXISTING KEYSTORE 'TDE_wallet2_location'
        IDENTIFIED BY TDe_wallet2_password
        [WITH BACKUP [USING 'backup_identifier]];

    In this specification:

    - `TDE_wallet1_location` is the directory location of the first TDE wallet, which will be left unchanged after the merge. Enclose this path in single quotation marks (`' '`).

    - The `IDENTIFIED BY` clause is required for the first TDE wallet if it is a password-protected TDE wallet. `TDE_wallet1_password` is the password for the first TDE wallet.

    - `TDE_wallet2_location` is the directory location of the second TDE wallet into which the first TDE wallet is to be merged. Enclose this path in single quotation marks (`' '`).

    - `TDE_wallet2_password` is the password for the second TDE wallet.

The target TDE wallet (`TDE_wallet2`) remains a password-protected TDE wallet after the TDE wallet merge operation.

**Related Topics**

- [About Merging TDE Wallets](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Merging TDE Wallets in Isolated Mode

##### 7.7.3.2 Merging Two TDE Wallets into a Third New TDE Wallet in Isolated Mode

In isolated mode, you can merge two TDE wallets into a third new TDE wallet, so that the two existing TDE wallets are not changed and the new TDE wallet contains the keys of both source TDE wallets.

1.  Connect to the isolated mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Merge the TDE wallets by using the following syntax:
        ADMINISTER KEY MANAGEMENT MERGE KEYSTORE 'TDE_wallet1_location'
        [IDENTIFIED BY TDE_wallet1_password] AND TDE_wallet 'TDE_wallet2_location'
        [IDENTIFIED BY TDE_wallet2_password]
        INTO NEW KEYSTORE 'TDE_wallet3_location'
        IDENTIFIED BY TDE_wallet3_password;

    In this specification:

    - `TDE_wallet1_location` is the directory location of the first TDE wallet, which will be left unchanged after the merge. Enclose this path in single quotation marks (`' '`).

    - The `IDENTIFIED BY` clause is required for the first TDE wallet if it is a password-protected TDE wallet. `TDE_wallet1_password` is the current password for the first TDE wallet.

    - `TDE_wallet2_location` is the directory location of the second TDE wallet. Enclose this path in single quotation marks (`' '`).

    - The `IDENTIFIED BY` clause is required for the second TDE wallet if it is a password-protected TDE wallet. `TDE_wallet2_password` is the current password for the second TDE wallet.

    - `TDE_wallet3_location` specifies the directory location of the new, merged TDE wallet. Enclose this path in single quotation marks (`' '`). If there is already an existing TDE wallet at this location, the command exits with an error.

    - `TDE_wallet3_password` is the new password for the merged TDE wallet.

    The following example merges an auto-login TDE wallet with a password-protected TDE wallet to create a merged password-protected TDE wallet at a new location:

        ADMINISTER KEY MANAGEMENT MERGE KEYSTORE '/etc/ORACLE/KEYSTORE/DB1'
        AND KEYSTORE '/etc/ORACLE/KEYSTORE/DB2'
        IDENTIFIED BY existing_password_for_TDE_wallet_2
        INTO NEW KEYSTORE '/etc/ORACLE/KEYSTORE/DB3'
        IDENTIFIED BY new_password_for_TDE_wallet_3;

        keystore altered.

**Related Topics**

- [About Merging TDE Wallets](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Merging TDE Wallets in Isolated Mode

#### 7.7.4 Closing Keystores in Isolated Mode

You can close both software and external keystores in isolated mode, unless the system tablespace is encrypted.

- Closing a TDE Wallet in Isolated Mode
  You can close password-protected TDE wallets, auto-login TDE wallets, and local auto-login TDE wallets in isolated mode.
- Closing an External Keystore in Isolated Mode
  To close an external keystore, you must use the `ADMINISTER KEY MANAGEMENT` statement with the `SET KEYSTORE CLOSE` clause.

**Parent topic:** Administering Keystores and TDE Master Encryption Keys in Isolated Mode

##### 7.7.4.1 Closing a TDE Wallet in Isolated Mode

You can close password-protected TDE wallets, auto-login TDE wallets, and local auto-login TDE wallets in isolated mode.

In the case of an auto-login TDE wallet, which opens automatically when it is accessed, you must first move it to a new location where it cannot be automatically opened, then you must manually close it. You must do this if you are changing your configuration from an auto-login TDE wallet to a password-protected TDE wallet: you change the configuration to stop using the auto-login TDE wallet (by moving the auto-login TDE wallet to another location where it cannot be automatically opened), and then closing the auto-login TDE wallet.

1.  Connect to the isolated mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Close the TDE wallet by using the following syntax.
    Note that the only difference between the following two `ADMINISTER KEY MANAGEMENT SET KEYSTORE CLOSE` statements is that a password must be provided for a password-protected TDE wallet.
    - For a password-protected TDE wallet:

          ADMINISTER KEY MANAGEMENT SET KEYSTORE CLOSE
          IDENTIFIED BY [EXTERNAL STORE | TDE_wallet_password];

      Closing a password-protected TDE wallet disables all encryption and decryption operations. Any attempt to encrypt or decrypt data or access encrypted data results in an error.

    - For an auto-login or local auto-login TDE wallet:

          ADMINISTER KEY MANAGEMENT SET KEYSTORE CLOSE;

      The result of this statement will not necessarily be that the TDE wallet status will change to `CLOSED`, because unless you also moved the `cwallet.sso` file to a location that Oracle Database cannot find, then a background job or background process could automatically re-open the auto-login TDE wallet. This can cause the status to potentially always appear to be `OPEN` even after the `ADMINISTER KEY MANAGEMENT SET KEYSTORE CLOSE` statement completed successfully.

**Related Topics**

- [About Closing Keystores](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Closing Keystores in Isolated Mode

##### 7.7.4.2 Closing an External Keystore in Isolated Mode

To close an external keystore, you must use the `ADMINISTER KEY MANAGEMENT` statement with the `SET KEYSTORE CLOSE` clause.

For an Oracle Key Vault keystore, you can only provide the password. No user name is allowed in the `IDENTIFIED BY` clause. Enclose the password in double quotation marks.

1.  Connect to the isolated mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Close the external keystore by using the following syntax:
        ADMINISTER KEY MANAGEMENT SET KEYSTORE CLOSE
        IDENTIFIED BY [EXTERNAL STORE | "external_key_manager_password"];

Closing a keystore disables all encryption and decryption operations. Any attempt to encrypt or decrypt data or access encrypted data results in an error.

**Related Topics**

- [About Closing Keystores](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Closing Keystores in Isolated Mode

#### 7.7.5 Creating a User-Defined TDE Master Encryption Key in Isolated Mode

To create a user-defined TDE master encryption key, use the `ADMINISTER KEY MANAGEMENT` statement with the `SET | CREATE [ENCRYPTION] KEY` clause.

1.  Log in to the isolated mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Create the user-defined TDE master encryption key by using the following syntax:
        ADMINISTER KEY MANAGEMENT SET | CREATE [ENCRYPTION] KEY
        'mkid:mk | mk'
        [USING ALGORITHM 'algorithm']
        [FORCE KEYSTORE]
        IDENTIFIED BY [EXTERNAL STORE | keystore_password]
        [WITH BACKUP [USING 'backup_identifier']];

    In this specification:

    - `SET | CREATE` : Enter `SET` if you want to create the master and activate the TDE master encryption key now, or enter `CREATE` if you want to create the key for later use, without activating it yet.

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

    The following example includes a user-created TDE master encryption key but no TDE master encryption key ID, so that the TDE master encryption key ID is generated:

        ADMINISTER KEY MANAGEMENT SET ENCRYPTION KEY
        '3D432109DF88967A541967062A6F4E460E892318E307F017BA048707B402493C'
        USING ALGORITHM 'GOST256'
        FORCE KEYSTORE
        IDENTIFIED BY keystore_password WITH BACKUP;

    The next example creates user-defined keys for both the master encryption ID and the TDE master encryption key. It omits the algorithm specification, so the default algorithm `AES256` is used.

        ADMINISTER KEY MANAGEMENT CREATE ENCRYPTION KEY
        '10203040506070801112131415161718:3D432109DF88967A541967062A6F4E460E892318E307F017BA048707B402493C'
        IDENTIFIED BY keystore_password WITH BACKUP;

**Related Topics**

- [Supported Encryption and Integrity Algorithms](introduction-to-transparent-data-encryption.md)

**Parent topic:** Administering Keystores and TDE Master Encryption Keys in Isolated Mode

#### 7.7.6 Creating a TDE Master Encryption Key for Later Use in Isolated Mode

A keystore must be open before you can create a TDE master encryption key for use later on in isolated mode.

1.  Connect to the isolated mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Create the TDE master encryption key by using the following syntax:
        ADMINISTER KEY MANAGEMENT CREATE KEY [USING TAG 'tag']
        [FORCE KEYSTORE]
        IDENTIFIED BY EXTERNAL STORE | keystore_password
        WITH BACKUP [USING 'backup_identifier'];

    In this specification:

    - `FORCE KEYSTORE` temporarily opens the password-protected TDE wallet for this operation. You must open the TDE wallet for this operation.

    - `IDENTIFIED BY` is required for the `BACKUP KEYSTORE` operation on a password-protected keystore because although the backup is simply a copy of the existing keystore, the status of the TDE master encryption key in the password-protected keystore must be set to `BACKED UP` and for this change the keystore password is required.

    - `keystore_location` is the path at which the backup keystore is stored. This setting is restricted to the PDB when the PDB lockdown profile `EXTERNAL_FILE_ACCESS` setting is blocked in the PDB or when the `PATH_PREFIX` variable was not set when the PDB was created. If you do not specify the `keystore_location`, then the backup is created in the same directory as the original keystore. Enclose this location in single quotation marks (`' '`).

    For example:

        ADMINISTER KEY MANAGEMENT CREATE KEY
        FORCE KEYSTORE
        IDENTIFIED BY keystore_password
        WITH BACKUP;
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

- [About Creating a TDE Master Encryption Key for Later Use](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Administering Keystores and TDE Master Encryption Keys in Isolated Mode

#### 7.7.7 Activating a TDE Master Encryption Key in Isolated Mode

To activate a TDE master encryption key in isolated mode, you must open the keystore and use `ADMINISTER KEY MANAGEMENT` with the `USE KEY` clause.

1.  Log in to the isolated mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.

2.  Query the `KEY_ID` column of the `V$ENCRYPTION_KEYS` view to find the key identifier.

    For example:

        SELECT KEY_ID FROM V$ENCRYPTION_KEYS;

        KEY_ID
        ----------------------------------------------------
        ARaHD762tUkkvyLgPzAi6hMAAAAAAAAAAAAAAAAAAAAAAAAAAAAA

3.  Use this key identifier to activate the TDE master encryption key by using the following syntax:

        ADMINISTER KEY MANAGEMENT USE KEY 'key_identifier_from_V$ENCRYPTION_KEYS'
        [USING TAG 'tag']
        [FORCE KEYSTORE]
        IDENTIFIED BY [EXTERNAL STORE | keystore_password]
        [WITH BACKUP [USING 'backup_identifier']];

    In this specification:

    - `FORCE KEYSTORE` temporarily opens the password-protected TDE wallet for this operation. You must open the TDE wallet for this operation.

    For example:

        ADMINISTER KEY MANAGEMENT USE KEY 'ARaHD762tUkkvyLgPzAi6hMAAAAAAAAAAAAAAAAAAAAAAAAAAAAA'
        FORCE KEYSTORE
        IDENTIFIED BY keystore_password
        WITH BACKUP;

**Related Topics**

- [About Activating TDE Master Encryption Keys](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Administering Keystores and TDE Master Encryption Keys in Isolated Mode

#### 7.7.8 Rekeying the TDE Master Encryption Key in Isolated Mode

You can use the `ADMINISTER KEY MANAGEMENT` statement with the `SET KEY` clause to rekey a TDE master encryption key.

1.  Connect to the isolated mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  If you are rekeying the TDE master encryption key for a keystore that has auto login enabled, then ensure that both the auto login keystore, identified by the `.sso` file, and the encryption keystore, identified by the `.p12` file, are present.
    You can find the location of these files by querying the `WRL_PARAMETER` column of the `V$ENCRYPTION_WALLET` view. To find the `WRL_PARAMETER` values for all of the database instances, query the `GV$ENCRYPTION_WALLET` view.
3.  Rekey the TDE master encryption key by using the following syntax:
        ADMINISTER KEY MANAGEMENT SET [ENCRYPTION] KEY
        [FORCE KEYSTORE]
        [USING TAG 'tag_name']
        IDENTIFIED BY [EXTERNAL STORE | keystore_password]
        [WITH BACKUP [USING 'backup_identifier']];

    In this specification:

    - `tag` is the associated attributes and information that you define. Enclose this setting in single quotation marks (`' '`).

    - `FORCE KEYSTORE` temporarily opens the password-protected TDE wallet for this operation. You must open the TDE wallet for this operation.

    - `IDENTIFIED BY` can be one of the following settings:

      - `EXTERNAL STORE` uses the keystore password stored in the external store to perform the keystore operation.

      - `keystore_password` is the password that was created for this keystore.

    For example:

        ADMINISTER KEY MANAGEMENT SET KEY
        FORCE KEYSTORE
        IDENTIFIED BY keystore_password
        WITH BACKUP USING 'emp_key_backup';

        keystore altered.

**Related Topics**

- [About Rekeying the TDE Master Encryption Key](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Administering Keystores and TDE Master Encryption Keys in Isolated Mode

#### 7.7.9 Moving a TDE Master Encryption Key into a New Keystore in Isolated Mode

In isolated mode, you can move an existing TDE master encryption key into a new TDE wallet from an existing password TDE wallet.

This feature enables you to move a subset, or all, of a TDE wallet’s keys into a new TDE wallet. After you move the key or keys to the new TDE wallet and then back up the old TDE wallet, optionally you then can delete this old TDE wallet.

1.  Connect to the isolated mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Query the `CREATION_TIME` and `KEY_ID` columns of the `V$ENCRYPTION_KEYS` view to find the key identifier of the key that you want to move.
    For example:
        SELECT CREATION_TIME, KEY_ID FROM V$ENCRYPTION_KEYS;

        CREATION TIME
        ----------------------------------------------------
        22-SEP-19 08.55.12.956170 PM +00:00

        KEY_ID
        ----------------------------------------------------
        ARaHD762tUkkvyLgPzAi6hMAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
3.  Move the key into a new TDE wallet by using the following syntax:
        ADMINISTER KEY MANAGEMENT
        MOVE [ENCRYPTION] KEYS
        TO NEW KEYSTORE 'TDE_wallet_location1'
        IDENTIFIED BY TDE_wallet1_password
        FROM [FORCE] KEYSTORE
        IDENTIFIED BY TDE_wallet2_password
        [WITH IDENTIFIER IN
        { 'key_identifier' [, 'key_identifier' ]... | ( subquery ) }]
        [WITH BACKUP [USING 'backup_identifier'] ];

    In this specification:

    - `TDE_wallet_location1` is the path to the `wallet` directory that will store the new TDE wallet `.p12` file. By default, this directory is in `$ORACLE_BASE/admin/``db_unique_name``/wallet`.

    - `TDE_wallet1_password` is the password for the TDE wallet from which the new TDE wallet is moved.

    - `FORCE` temporarily opens the TDE wallet for this operation.

    - `TDE_wallet2_password` is the password for the TDE wallet from which the key is moving.

    - `subquery` can be used to find the exact key identifier that you want.

    - `backup_identifier` is an optional description of the backup. Enclose `backup_identifier` in single quotation marks (`' '`).

    For example:

        ADMINISTER KEY MANAGEMENT MOVE KEYS
        TO NEW KEYSTORE '$ORACLE_BASE/admin/orcl/wallet'
        IDENTIFIED BY TDE_wallet1_password
        FROM FORCE KEYSTORE
        IDENTIFIED BY TDE_wallet2_password
        WITH IDENTIFIER IN
        (SELECT KEY_ID FROM V$ENCRYPTION_KEYS WHERE ROWNUM < 2)
        WITH BACKUP;

    After the keys are moved to the new TDE wallet, they no longer exist in the old TDE wallet.
4.   To delete the old TDE wallet, go to the `wallet` directory and do the following:
    1.  Back up the `.p12` file containing the TDE wallet that you want to delete.
    2.  Manually delete the `.p12` file containing the TDE wallet.

    To find the location of the TDE wallet, open the TDE wallet, and then query the `WRL_PARAMETER` column of the `V$ENCRYPTION_WALLET` view.

**Related Topics**

- [About Moving TDE Master Encryption Keys into a New Keystore](managing-keystore-and-tde-master-encryption-key.md)
- [Dangers of Deleting Keystores](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Administering Keystores and TDE Master Encryption Keys in Isolated Mode

#### 7.7.10 Creating a Custom Attribute Tag in Isolated Mode

To create a custom attribute tag in isolated mode, you must use the `SET TAG` clause of the `ADMINISTER KEY MANAGEMENT` statement.

1.  Log in to the isolated mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.

2.  If necessary, query the `TAG` column of the `V$ENCRYPTION_KEY` dynamic view to find a listing of existing tags for the TDE master encryption keys.

    When you create a new tag for a TDE master encryption key, it overwrites the existing tag for that TDE master encryption key.

3.  Create the custom attribute tag by using the following syntax:

        ADMINISTER KEY MANAGEMENT SET TAG 'tag'
        FOR 'master_key_identifier'
        [FORCE KEYSTORE]
        IDENTIFIED BY [EXTERNAL STORE | keystore_password]
        [WITH BACKUP [USING 'backup_identifier']];

    In this specification:

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

**Parent topic:** Administering Keystores and TDE Master Encryption Keys in Isolated Mode

#### 7.7.11 Exporting and Importing the TDE Master Encryption Key in Isolated Mode

You can export and import the TDE master encryption key in different ways in isolated mode.

- Exporting a TDE Master Encryption Key in Isolated Mode
  In isolated mode, you can use the `ADMINISTER KEY MANAGEMENT` statement to export a TDE master encryption key.
- Importing a TDE Master Encryption Key in Isolated Mode
  The `ADMINISTER KEY MANAGEMENT` statement with the `IMPORT [ENCRYPTION] KEYS WITH SECRET` clause can import a TDE master encryption key.

**Parent topic:** Administering Keystores and TDE Master Encryption Keys in Isolated Mode

##### 7.7.11.1 Exporting a TDE Master Encryption Key in Isolated Mode

In isolated mode, you can use the `ADMINISTER KEY MANAGEMENT` statement to export a TDE master encryption key.

1.  Log in to the isolated mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.

2.  Export the TDE master encryption keystore by using the following syntax:

        ADMINISTER KEY MANAGEMENT EXPORT [ENCRYPTION] KEYS
        WITH SECRET "export_secret"
        TO 'file_path'
        [FORCE KEYSTORE]
        IDENTIFIED BY [EXTERNAL STORE | keystore_password]
        [WITH IDENTIFIER IN 'key_id1', 'key_id2', 'key_idn' | (SQL_query)];

    In this specification:

    - `export_secret` is a password that you can specify to encrypt the export the file that contains the exported keys. Enclose this secret in double quotation marks (`" "`), or you can omit the quotation marks if the secret has no spaces.

    - `file_path` is the complete path and name of the file to which the keys must be exported. Enclose this path in single quotation marks (`' '`). You can export to regular file systems only.

    - `FORCE KEYSTORE` temporarily opens the password-protected TDE wallet for this operation. You must open the TDE wallet for this operation.

    - `key_id1`, `key_id2`, `key_idn` is a string of one or more TDE master encryption key identifiers for the TDE master encryption key being exported. Separate each key identifier with a comma and enclose each of these key identifiers in single quotation marks (`' '`). To find TDE master encryption key identifiers, query the `KEY_ID` column of the `V$ENCRYPTION_KEYS` dynamic view.

    - `SQL_query` is a query that fetches a list of the TDE master encryption key identifiers. It should return only one column that contains the TDE master encryption key identifiers. This query is executed with current user rights.

**Related Topics**

- [Exporting and Importing the TDE Master Encryption Key](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Exporting and Importing the TDE Master Encryption Key in Isolated Mode

##### 7.7.11.2 Importing a TDE Master Encryption Key in Isolated Mode

The `ADMINISTER KEY MANAGEMENT` statement with the `IMPORT [ENCRYPTION] KEYS WITH SECRET` clause can import a TDE master encryption key.

1.  Connect to the isolated mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Import the TDE master encryption keystore by using the following syntax:
        ADMINISTER KEY MANAGEMENT IMPORT [ENCRYPTION] KEYS
        WITH SECRET "import_secret"
        FROM 'file_name'
        [FORCE KEYSTORE]
        IDENTIFIED BY [EXTERNAL STORE | keystore_password]
        [WITH BACKUP [USING 'backup_identifier']];

    In this specification:

    - `import_secret` is the same password that was used to encrypt the keys during the export operation. Enclose this secret in double quotation marks (`" "`), or you can omit the quotation marks if the secret has no spaces.

    - `file_name` is the complete path and name of the file from which the keys need to be imported. Enclose this setting in single quotation marks (`' '`).

    - `FORCE KEYSTORE` temporarily opens the password-protected TDE wallet for this operation. You must open the TDE wallet for this operation.

**Related Topics**

- [Exporting and Importing the TDE Master Encryption Key](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Exporting and Importing the TDE Master Encryption Key in Isolated Mode

#### 7.7.12 Storing Oracle Database Secrets in Isolated Mode

Secrets are data that support internal Oracle Database features that integrate external clients such as Oracle GoldenGate into the database.

- Storing Oracle Database Secrets in a TDE Wallet in Isolated Mode
  The `ADMINISTER KEY MANAGEMENT ADD SECRET|UPDATE SECRET|DELETE SECRET` statements can add secrets, update secrets, and delete secrets in a TDE wallet.
- Storing Oracle Database Secrets in an External Keystore in Isolated Mode
  The `ADMINISTER KEY MANAGEMENT ADD SECRET|UPDATE SECRET|DELETE SECRET` statements can add secrets, update secrets, and delete secrets in a keystore.

**Parent topic:** Administering Keystores and TDE Master Encryption Keys in Isolated Mode

##### 7.7.12.1 Storing Oracle Database Secrets in a TDE Wallet in Isolated Mode

The `ADMINISTER KEY MANAGEMENT ADD SECRET|UPDATE SECRET|DELETE SECRET` statements can add secrets, update secrets, and delete secrets in a TDE wallet.

1.  Connect to the isolated mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Add, update, or delete a database secret in a TDE wallet by using the following syntax:
    - To add a secret:

          ADMINISTER KEY MANAGEMENT
          ADD SECRET 'secret' FOR CLIENT 'client_identifier'
          [USING TAG 'tag']
          [TO [[LOCAL] AUTO_LOGIN] KEYSTORE TDE_wallet_location
          [WITH BACKUP [USING backup_id]]
          | [FORCE KEYSTORE]
          IDENTIFIED BY [EXTERNAL STORE | TDE_wallet_password]
          [WITH BACKUP [USING backup_id]]];

    - To update a secret:

          ADMINISTER KEY MANAGEMENT
          UPDATE SECRET 'secret' FOR CLIENT 'client_identifier'
          [USING TAG 'tag']
          [TO [[LOCAL] AUTO_LOGIN] KEYSTORE TDE_wallet_location
          [WITH BACKUP [USING backup_id]]
          | [FORCE KEYSTORE]
          IDENTIFIED BY [EXTERNAL STORE | TDE_wallet_password]
          [WITH BACKUP [USING backup_id]]];

    - To delete a secret:

          ADMINISTER KEY MANAGEMENT
          DELETE SECRET FOR CLIENT 'client_identifier'
          [FROM [[LOCAL] AUTO_LOGIN] KEYSTORE TDE_wallet_location
          [FORCE KEYSTORE]
          IDENTIFIED BY [EXTERNAL STORE | TDE_wallet_password]
          [WITH BACKUP [USING backup_id]]];

    The specification is as follows:

    - `secret` is the client secret key to be stored, updated, or deleted. To find information about existing secrets and their client identifiers, query the `V$CLIENT_SECRETS` dynamic view.

    - `client_identifier` is an alphanumeric string used to identify the secret key.

    - `FORCE KEYSTORE` temporarily opens the password-protected TDE wallet for this operation. You must open the TDE wallet for this operation.

**Related Topics**

- [Storing Oracle Database Secrets](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Storing Oracle Database Secrets in Isolated Mode

##### 7.7.12.2 Storing Oracle Database Secrets in an External Keystore in Isolated Mode

The `ADMINISTER KEY MANAGEMENT ADD SECRET|UPDATE SECRET|DELETE SECRET` statements can add secrets, update secrets, and delete secrets in a keystore.

1.  Log in to the isolated mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Add, update, or delete a database secret in an external keystore by using the following syntax:
    - To add a secret:

          ADMINISTER KEY MANAGEMENT
          ADD SECRET 'secret' FOR CLIENT 'client_identifier'
          [USING TAG 'tag']
          [TO [[LOCAL] AUTO_LOGIN] KEYSTORE keystore_location
          [FORCE KEYSTORE]
          IDENTIFIED BY "external_key_manager_password"]
          [WITH BACKUP [USING backup_id]];

    - To update a secret:

          ADMINISTER KEY MANAGEMENT
          UPDATE SECRET 'secret' FOR CLIENT 'client_identifier'
          [USING TAG 'tag']
           [TO [[LOCAL] AUTO_LOGIN] KEYSTORE keystore_location
          [FORCE KEYSTORE]
          IDENTIFIED BY "external_key_manager_password"
          [WITH BACKUP [USING backup_id]];

    - To delete a secret:

          ADMINISTER KEY MANAGEMENT
          DELETE SECRET FOR CLIENT 'client_identifier'
          [FROM [[LOCAL] AUTO_LOGIN] KEYSTORE keystore_location
          [FORCE KEYSTORE]
          IDENTIFIED BY "external_key_manager_password";

    The specification is as follows:

    - `secret` is the client secret key to be stored, updated, or deleted. To find information about existing secrets and their client identifiers, query the `V$CLIENT_SECRETS` dynamic view.

    - `client_identifier` is an alphanumeric string used to identify the secret key.

    - `FORCE KEYSTORE` temporarily opens the password-protected TDE wallet for this operation. You must open the TDE wallet for this operation.

    - `external_key_manager_password` is for an external keystore manager, which can be Oracle Key Vault or OCI Vault - Key Management. Enclose this password in double quotation marks. For Oracle Key Vault, enter the password that was given during the Oracle Key Vault client installation. If at that time no password was given, then the password in the `ADMINISTER KEY MANAGEMENT` statement becomes `NULL`.

**Related Topics**

- [Storing Oracle Database Secrets](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Storing Oracle Database Secrets in Isolated Mode

#### 7.7.13 Migrating Keystores in Isolated Mode

You can perform migration and reverse migration operations between software keystores and external keystores in isolated mode.

- Reverse Migrating an Isolated PDB from Oracle Key Vault to a TDE Wallet
  Isolated PDBs have individual keystores (TDE wallets or Oracle Key Vault external keystores), and can individually be migrated from the TDE wallet to Oracle Key Vault, and individually reverse migrated from Oracle Key Vault back to the TDE wallet.
- Migrating from an External Keystore to a Password-Protected TDE Wallet in Isolated Mode
  In isolated mode, you can migrate from an external keystore to a password-protected TDE wallet.

**Parent topic:** Administering Keystores and TDE Master Encryption Keys in Isolated Mode

##### 7.7.13.1 Reverse Migrating an Isolated PDB from Oracle Key Vault to a TDE Wallet

Isolated PDBs have individual keystores (TDE wallets or Oracle Key Vault external keystores), and can individually be migrated from the TDE wallet to Oracle Key Vault, and individually reverse migrated from Oracle Key Vault back to the TDE wallet.

For both the TDE wallet and the external keystore to open at the same time, either the TDE wallet must have the same password as the external keystore, or alternatively, after the migration has completed you can create an auto-login keystore for the TDE wallet.

1.  Before migrating any database from wallet to Oracle Key Vault, upload the contents of the wallet (the current and retired TDE master encryption keys) into the virtual wallet that you created in Oracle Key Vault for that database.
    In the following example, the static initialization parameter `WALLET_ROOT` is set to `/etc/ORACLE/KEYSTORES/${ORACLE_SID}`:
        /etc/ORACLE/KEYSTORES/${ORACLE_SID}/pdb-guid/okv/bin/okvutil upload -l
        /etc/ORACLE/KEYSTORES/${ORACLE_SID}/pdb-guid/tde/ -t wallet -g
        virtual_wallet_name_in_Oracle_Key_Vault -v 2
2.  Connect to the isolated mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
3.  Set the password of the external keystore so that it matches that of the TDE wallet.
    Some Oracle tools, such as Oracle Data Pump and Oracle Recovery Manager, require access to the old TDE wallet to decrypt data that was exported or backed up using the TDE master encryption key from the old TDE wallet.
    - To set the TDE wallet password so that it is the same as that of the external keystore, use the following syntax:

          ADMINISTER KEY MANAGEMENT ALTER KEYSTORE PASSWORD
          [FORCE KEYSTORE]
          IDENTIFIED BY TDE_wallet_password
          SET "external_key_manager_password"
          WITH BACKUP [USING 'backup_identifier'];

      In this specification:

      - `TDE_wallet_password` is the password that was assigned to this wallet when it was created.

      - `external_key_manager_password` is for an external keystore manager, which can be Oracle Key Vault or OCI Vault - Key Management. Enclose this password in double quotation marks. For Oracle Key Vault, enter the password that was given during the Oracle Key Vault client installation. If at that time no password was given, then the password in the `ADMINISTER KEY MANAGEMENT` statement becomes `NULL`.

    - Alternatively, to create an auto-login keystore for a TDE wallet, use the following syntax:

          ADMINISTER KEY MANAGEMENT CREATE [LOCAL] AUTO_LOGIN KEYSTORE
          FROM KEYSTORE 'keystore_location'
          IDENTIFIED BY TDE_wallet_password;
4.  Provision Oracle Key Vault for the isolated mode PDB by following the instructions in [Oracle Key Vault Administrator's Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/asoag&id=OKVAG-GUID-59436B34-58FC-469B-8C3F-B6ABAC283627)Oracle Key Vault Administrator's Guide to install the Oracle Key Vault software onto the endpoint.
5.  Set the configuration of the keystore so that the external keystore becomes the new primary, and the password-protected TDE wallet becomes the secondary, as follows:
        ALTER SYSTEM SET TDE_CONFIGURATION="KEYSTORE_CONFIGURATION=OKV|FILE";
6.  Migrate the external keystore by using the following syntax:
        ADMINISTER KEY MANAGEMENT SET ENCRYPTION KEY
        IDENTIFIED BY "external_key_manager_password"
        [FORCE KEYSTORE]
        MIGRATE USING TDE_wallet_password;

    After you complete the migration, you do not need to restart the database, nor do you need to manually re-open the external keystore.

**Related Topics**

- [Keystore Order After a Migration](managing-keystore-and-tde-master-encryption-key.md)
- [Migration of Keystores to and from Oracle Key Vault](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Migrating Keystores in Isolated Mode

##### 7.7.13.2 Migrating from an External Keystore to a Password-Protected TDE Wallet in Isolated Mode

In isolated mode, you can migrate from an external keystore to a password-protected TDE wallet.

1.  Log in to the isolated mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Ensure that you have enrolled the PDB endpoint and that the Oracle Key Vault configuration is present at the `$``WALLET_ROOT``/``pdb_guid``/okv` location.
    For both the TDE wallet and the external keystore to open at the same time, either the TDE wallet must have the same password as the external keystore, or alternatively, after the reverse migration has completed, you can create an auto-login TDE wallet for the TDE wallet.
3.  Set the `TDE_CONFIGURATION` parameter as follows, so that `FILE` becomes the new primary keystore, and `OKV` becomes the secondary keystore.
        ALTER SYSTEM SET TDE_CONFIGURATION="KEYSTORE_CONFIGURATION=FILE|OKV";
4.  Now that the keystore configuration has been completed, issue the following statement to reverse migrate from the external keystore to the password-protected TDE wallet:
        ADMINISTER KEY MANAGEMENT SET ENCRYPTION KEY
        IDENTIFIED BY TDE_wallet_password
        REVERSE MIGRATE USING "external_key_manager_password"
        [WITH BACKUP [USING 'backup_identifier']];
5.  Optionally, change the password of the newly migrated TDE wallet.
    For example:
        ADMINISTER KEY MANAGEMENT ALTER KEYSTORE PASSWORD
        IDENTIFIED BY
        old_password SET new_password
        WITH BACKUP USING 'pwd_change';

After you complete these steps, the migration process automatically reloads the keystore keys in memory. You do not need to restart the database, nor do you need to manually re-open the TDE wallet. The external keystore may still be required after reverse migration because the old keys are likely to have been used for encrypted backups or by tools such as Oracle Data Pump and Oracle Recovery Manager. You should create an auto-login keystore and put the `HSM_PASSWORD` client secret into it. For example:

    ADMINISTER KEY MANAGEMENT ADD SECRET 'external_key_manager_password'
    FOR CLIENT 'EXTERNAL_PASSWORD'
    TO LOCAL AUTO_LOGIN KEYSTORE TDE_wallet_location
    WITH BACKUP;

**Related Topics**

- [About Migrating Back from an External Keystore](managing-keystore-and-tde-master-encryption-key.md)
- [Keystore Order After a Migration](managing-keystore-and-tde-master-encryption-key.md)
- [Migration of Keystores to and from Oracle Key Vault](managing-keystore-and-tde-master-encryption-key.md)

**Parent topic:** Migrating Keystores in Isolated Mode

#### 7.7.14 Uniting a Pluggable Database Keystore

Uniting a PDB keystore moves the TDE master encryption keys from the PDB keystore into the keystore of the CDB root. This enables the administrator of the keystore of the CDB root to manage the keys.

The client secrets are not moved. Instead, they are left behind in the keystore that the PDB used while it was configured in isolated mode. Oracle recommends that you delete client secrets from that keystore before you unite the PDB keystore. Similarly, when a PDB becomes isolated, no client secret contained in the keystore of the CDB root is moved.

1.  Connect to the isolated mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Unite the PDB keystore, which moves the TDE master encryption keys from the PDB keystore into the keystore of the CDB root, by using the following syntax:
        ADMINISTER KEY MANAGEMENT UNITE KEYSTORE
        IDENTIFIED BY isolated_keystore_password
        WITH ROOT KEYSTORE [FORCE KEYSTORE]
        IDENTIFIED BY
        [EXTERNAL STORE | keystore_password_of_cdb_root]
        [WITH BACKUP [USING backup_id]];

    In this specification:

    - `FORCE KEYSTORE` temporarily opens the password-protected TDE wallet for this operation if an auto-login TDE wallet is open (and in use) or if the TDE wallet is closed.

    - `united_keystore_password`: Knowledge of this password does not enable the user who performs the `UNITE KEYSTORE` operation privileges to perform `ADMINISTER KEY MANAGEMENT UNITE KEYSTORE` operations on the PDB.

    When the keystore of a PDB is united with a keystore in the CDB root, all of the previously active (historical) TDE master encryption keys that were associated with the PDB are moved to the keystore of the CDB root. (If an `ORA-46694: The keys are already in the root keystore` error appears, see below.)
3.  Confirm that the isolated mode PDB is now a united mode PDB.
        SELECT KEYSTORE_MODE FROM V$ENCRYPTION_WALLET;

    The output should be `UNITED`.

The keystore no longer exists but its master encryption key is now in the keystore in the CDB root. If you later decide that you want the united mode PDB to be an isolated mode PDB again, then you can use the `ADMINISTER KEY MANAGEMENT ISOLATE KEYSTORE` statement.

ORA-46694 error: If a wallet is created in the in a PDB context, then it changes the keystore type of the PDB to isolated, and unless a key is set for the PDB, the wallet status will be `OPEN_NO_MASTER_KEY`. Uniting this type of PDB using the `ADMINISTER KEY MANAGEMENT UNITE KEYSTORE` statement will result in an `ORA-46694: The keys are already in the root keystore` error. To change the `KEYSTORE_MODE` to `UNITED` for this PDB, you must change the TDE configuration for the PDB. In the PDB, run the following statement:

    ALTER SYSTEM RESET TDE_CONFIGURATION;

**Related Topics**

- [Isolating a Pluggable Database Keystore](managing-keystores-encryption-keys-in-united-mode.md)

**Parent topic:** Administering Keystores and TDE Master Encryption Keys in Isolated Mode

#### 7.7.15 Creating a Keystore When the PDB Is Closed

When you create a keystore in a PDB that is closed, the new keystore is empty and the PDB is converted to isolated mode.

- About Creating a Keystore When the PDB Is Closed
  Creating a keystore in a PDB that is closed could inadvertently cause problems in rekey operations, but the keystore creation can be reverted.
- Reverting a Keystore Creation Operation When a PDB Is Closed
  If you have inadvertently created a keystore in a PDB (and thereby caused it to become configured in isolated mode), then you should reverse the keystore creation operation.

**Parent topic:** Administering Keystores and TDE Master Encryption Keys in Isolated Mode

##### 7.7.15.1 About Creating a Keystore When the PDB Is Closed

Creating a keystore in a PDB that is closed could inadvertently cause problems in rekey operations, but the keystore creation can be reverted.

In previous releases, if you tried to create a keystore in a closed PDB, you were prevented and an `ORA-65040: operation not allowed from within a pluggable database` error would appear. Starting in Oracle Database release 18c, for convenience, when the keystore of the PDB is closed and if you run the `ADMINISTER KEY MANAGEMENT CREATE KEYSTORE` statement in the PDB, Oracle Database allows the operation.

If the closed PDB has not been configured to use encryption (that is, it has never had an `ADMINISTER KEY MANAGEMENT SET KEY` statement performed in it), after you execute `ADMINISTER KEY MANAGEMENT CREATE KEYSTORE`, resulting in an empty keystore and the configuration of the PDB being changed to isolated mode, then you can create a TDE master encryption key in this empty keystore.

If, however, the PDB was already configured to use encryption, then the PDB may be configured in united mode (and thus have its TDE master encryption key being managed in the keystore of the CDB root).

Mistakenly running an `ADMINISTER KEY MANAGEMENT CREATE KEYSTORE` statement on such a closed PDB will create an additional keystore (which will be empty), and will then configure the PDB to be in isolated mode. This effectively misconfigures the PDB, because the PDB is now in isolated mode (whereas it should be in united mode), yet its TDE master encryption key is still in the keystore of the CDB root. This misconfiguration can cause problems later on, if you try to rekey the TDE master encryption key by using the `ADMINISTER KEY MANAGEMENT SET ENCRYPTION KEY` statement . An `ORA-28362: master key not found` error will appear, because when encryption has already been enabled and a key has been set, Oracle Database treats the `ADMINISTER KEY MANAGEMENT SET ENCRYPTION KEY` statement as a rekey operation. In order to perform a rekey operation, Oracle Database must locate the currently active TDE master encryption key of the PDB. But in this misconfigured PDB, Oracle Database cannot locate the TDE master encryption key, because the PDB is now in isolated mode and the necessary key is in the keystore of the CDB root. Hence, the PDB is no longer configured to search in the keystore of the PDB, and the rekey operation fails.

To remedy the misconfiguration of the PDB, you must reconfigure the PDB to united mode and you must remove the empty keystore. (Always make a backup before removing any keystore.) When the PDB is configured back to united mode, then the currently active TDE master encryption key is once again available for rekey and other TDE master encryption key operations.

If later on you want to configure the PDB to be in isolated mode, then you can open the PDB and run the `ADMINISTER KEY MANAGEMENT ISOLATE KEYSTORE` statement, which isolates the PDB and moves its TDE master encryption key and previously-active (historical) keys from the keystore of the CDB root to a newly-created keystore for the isolated PDB.

**Related Topics**

- Reverting a Keystore Creation Operation When a PDB Is Closed

**Parent topic:** Creating a Keystore When the PDB Is Closed

##### 7.7.15.2 Reverting a Keystore Creation Operation When a PDB Is Closed

If you have inadvertently created a keystore in a PDB (and thereby caused it to become configured in isolated mode), then you should reverse the keystore creation operation.

Use this procedure if you created a keystore in a closed PDB that already had encryption enabled (that is, it already had a TDE master encryption key).

1.  Log in to the isolated mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Confirm the mode of the PDB by querying the `KEYSTORE_MODE` column of the `V$ENCRYPTION_WALLET` dynamic view.
3.  If the `V$ENCRYPTION_WALLET` output is `ISOLATED`, then execute the `ALTER SYSTEM` statement to reconfigure the PDB to united mode.
    - When pfile is in use, clear the `TDE_CONFIGURATION` parameter by using the following statement:

          ALTER SYSTEM RESET TDE_CONFIGURATION SCOPE=MEMORY;

      In an Oracle Real Application Clusters environment, include the `SID` parameter:

          ALTER SYSTEM RESET TDE_CONFIGURATION SCOPE=MEMORY SID='*';

    - When spfile is in use, clear the `TDE_CONFIGURATION` parameter by using this statement:

          ALTER SYSTEM RESET TDE_CONFIGURATION SCOPE=BOTH;

      In an Oracle Real Application Clusters environment, include the `SID` parameter:

          ALTER SYSTEM RESET TDE_CONFIGURATION SCOPE=BOTH SID='*';
4.  In the `WALLET_ROOT``/``PDB_GUID``/tde` directory, find and back up the `ewallet.p12` keystore file that was mistakenly created.
5.  Delete the mistakenly-created empty keystore file.

At this stage, the PDB will be in united mode and the correct keystore and TDE master encryption key will be available for any future rekey operations.

**Parent topic:** Creating a Keystore When the PDB Is Closed

### 7.8 Administering Transparent Data Encryption in Isolated Mode

You can perform a number of general administrative tasks with Transparent Data Encryption in isolated mode.

- Cloning or Relocating Encrypted PDBs in Isolated Mode
  You can clone or relocate encrypted PDBs within the same container database, or across container databases.
- Unplugging and Plugging a PDB with Encrypted Data in a CDB in Isolated Mode
  In isolated mode, for a PDB that has encrypted data, you can plug it into a CDB. Conversely, you can unplug this PDB from the CDB.
- Cloning a PDB with Encrypted Data in a CDB in Isolated Mode
  The `CREATE PLUGGABLE DATABASE` statement with the `KEYSTORE IDENTIFIED BY` clause can clone a PDB that has encrypted data.
- Performing a Remote Clone of PDB with Encrypted Data Between Two CDBs in Isolated Mode
  The `CREATE PLUGGABLE DATABASE` statement with the `KEYSTORE IDENTIFIED BY` clause can remotely clone a PDB that has encrypted data.
- Relocating an Encrypted PDB in Isolated Mode
  The `CREATE PLUGGABLE DATABASE` statement with the `KEYSTORE IDENTIFIED BY` clause can relocate across CDBs a cloned PDB that has encrypted data.
- How Keystore Open and Close Operations Work in Isolated Mode
  You should be aware of how keystore (TDE wallets or external keystores) open and close operations work in isolated mode.
- Exporting and Importing Master Encryption Keys for a PDB in Isolated Mode
  In isolated mode, the `EXPORT` and `IMPORT` clauses of `ADMINISTER KEY MANAGEMENT EXPORT` can export or import master encryption keys for a PDB.

**Parent topic:** Managing Keystores and TDE Master Encryption Keys in Isolated Mode

#### 7.8.1 Cloning or Relocating Encrypted PDBs in Isolated Mode

You can clone or relocate encrypted PDBs within the same container database, or across container databases.

If you are trying to move a PDB in which the `SYSTEM`, `SYSAUX`, `UNDO`, or `TEMP` tablespace is encrypted, and using the manual export or import of keys, then you must first import the keys for the PDB in the target database's `CDB$ROOT` before you create the PDB. Import of the keys are again required inside the PDB to associate the keys to the PDB.

- Clone or relocate the PDB using the following syntax:
      CREATE|RELOCATE PLUGGABLE DATABASE database_name KEYSTORE
      IDENTIFIED BY EXTERNAL STORE|target_keystore_password [NO REKEY];

**Related Topics**

- [Oracle Multitenant Administrator's Guide](../multi/introduction-to-the-multitenant-architecture.md)

**Parent topic:** Administering Transparent Data Encryption in Isolated Mode

#### 7.8.2 Unplugging and Plugging a PDB with Encrypted Data in a CDB in Isolated Mode

In isolated mode, for a PDB that has encrypted data, you can plug it into a CDB. Conversely, you can unplug this PDB from the CDB.

- Unplugging a PDB That Has Encrypted Data in Isolated Mode
  You can unplug a PDB (that has encrypted data) from one CDB and then optionally plug it into another CDB.
- Plugging a PDB That Has Encrypted Data into a CDB in Isolated Mode
  After you plug a PDB that has encrypted data into a CDB, you can set the encryption key in the PDB.
- Unplugging a PDB That Has Master Encryption Keys Stored in an External Keystore in Isolated Mode
  You can unplug a PDB from one CDB that has been configured with an external keystore and then plug it into another CDB also configured with an external keystore.
- Plugging a PDB That Has Master Encryption Keys Stored in an External Keystore in Isolated Mode
  The `ADMINISTER KEY MANAGEMENT` statement can import an external keystore master encryption key to a PDB that has been moved to another CDB.

**Parent topic:** Administering Transparent Data Encryption in Isolated Mode

##### 7.8.2.1 Unplugging a PDB That Has Encrypted Data in Isolated Mode

You can unplug a PDB (that has encrypted data) from one CDB and then optionally plug it into another CDB.

Unlike united mode, you do not need to specify the `ENCRYPT` clause in the `ALTER PLUGGABLE DATABASE` statement. The database that is unplugged contains data files and other associated files. Because each PDB can have its own unique keystore, you do not need to export the TDE master encryption key of the PDB that you want to unplug. You can check if a PDB has already been unplugged by querying the `STATUS` column of the `DBA_PDBS` data dictionary view.

- Unplug the isolated mode PDB as you normally unplug PDBs.
  For example:
      ALTER PLUGGABLE DATABASE pdb1
        UNPLUG INTO '/oracle/data/pdb1.xml';

**Related Topics**

- [Oracle Multitenant Administrator's Guide](../multi/removing-a-pdb.md)
- [Oracle Database SQL Language Reference](../sqlrf/ALTER-PLUGGABLE-DATABASE.md)

**Parent topic:** Unplugging and Plugging a PDB with Encrypted Data in a CDB in Isolated Mode

##### 7.8.2.2 Plugging a PDB That Has Encrypted Data into a CDB in Isolated Mode

After you plug a PDB that has encrypted data into a CDB, you can set the encryption key in the PDB.

Unlike united mode, you do not need to specify the `DECRYPT` clause in the `CREATE PLUGGABLE DATABASE` statement. When you plug an unplugged PDB into another CDB, the key version is set to `0` because this operation invalidates the history of the previous keys. You can check the key version by querying the `KEY_VERSION` column of the `V$ENCRYPTED_TABLESPACES` dynamic view. Similarly, if a control file is lost and recreated, then the previous history of the keys is reset to `0`. You can check if a PDB has already been plugged in by querying the `STATUS` column of the `DBA_PDBS` data dictionary view.

1.  Create the PDB by plugging the unplugged PDB into the CDB.

    - For example, if you had exported the PDB data into a metadata XML file:

          CREATE PLUGGABLE DATABASE CDB1_PDB2
          USING '/tmp/cdb1_pdb2.xml'
          NOCOPY KEYSTORE
          IDENTIFIED BY password;

    - If you had exported the PDB into an archive file:

          CREATE PLUGGABLE DATABASE CDB1_PDB2
          USING '/tmp/cdb1_pdb2.pdb';

    During the open operation of the PDB after the plug operation, Oracle Database determines if the PDB has encrypted data. If so, it opens the PDB in the `RESTRICTED` mode.

    You can find if the source database has encrypted data or a TDE master encryption key set in the keystore by querying the `V$ENCRYPTION_KEYS` dynamic view.

2.  Open the PDB.

    For example:

        ALTER PLUGGABLE DATABASE CDB1_PDB2 OPEN;

3.  Open the keystore in the CDB root.

    For example:

        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN
        IDENTIFIED BY password;

    Optionally, open the keystore in the PDB.

4.  In the PDB, open the keystore and set the TDE master encryption key for the PDB.

    For example:

        ADMINISTER KEY MANAGEMENT SET KEY
        IDENTIFIED BY keystore_password
        WITH BACKUP USING 'emp_key_backup';

**Parent topic:** Unplugging and Plugging a PDB with Encrypted Data in a CDB in Isolated Mode

##### 7.8.2.3 Unplugging a PDB That Has Master Encryption Keys Stored in an External Keystore in Isolated Mode

You can unplug a PDB from one CDB that has been configured with an external keystore and then plug it into another CDB also configured with an external keystore.

1.  Unplug the PDB.
    You can check if a PDB has already been unplugged by querying the `STATUS` column of the `DBA_PDBS` data dictionary view.
2.  Move the master encryption keys of the unplugged PDB from the hardware that was used at the source CDB to the hardware that is in use at the destination CDB.
    Refer to the documentation for the external keystore for information about moving master keys between external keystores.

**Related Topics**

- [Oracle Multitenant Administrator's Guide](../multi/index.md)

**Parent topic:** Unplugging and Plugging a PDB with Encrypted Data in a CDB in Isolated Mode

##### 7.8.2.4 Plugging a PDB That Has Master Encryption Keys Stored in an External Keystore in Isolated Mode

The `ADMINISTER KEY MANAGEMENT` statement can import an external keystore master encryption key to a PDB that has been moved to another CDB.

1.  Plug the unplugged isolated mode PDB into the destination CDB that has been configured with the external keystore.
    You can check if a PDB has already been plugged in by querying the `STATUS` column of the `DBA_PDBS` data dictionary view.
    After the plug-in operation, the PDB that has been plugged in will be in restricted mode.
2.  Ensure that the master keys from the external keystore that has been configured with the source CDB are available in the external keystore of the destination CDB.
3.  Log in to the plugged PDB as a user who was granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
4.  Open the keystore of the plugged PDB.
    For example, for a PDB called `PDB1`:

        ALTER SESSION SET CONTAINER = PDB1;
        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN
        IDENTIFIED BY "external_key_manager_password";
5.  Import the external keystore master encryption key into the PDB.
        ADMINISTER KEY MANAGEMENT IMPORT ENCRYPTION KEYS
        WITH SECRET "external_keystore" FROM 'external_keystore'
        IDENTIFIED BY "external_key_manager_password";
6.  Close and re-open the PDB.
        ALTER PLUGGABLE DATABASE PDB1 CLOSE;
        ALTER PLUGGABLE DATABASE PDB1 OPEN;

**Related Topics**

- [Oracle Multitenant Administrator's Guide](../multi/plugging-in-a-pdb.md)

**Parent topic:** Unplugging and Plugging a PDB with Encrypted Data in a CDB in Isolated Mode

#### 7.8.3 Cloning a PDB with Encrypted Data in a CDB in Isolated Mode

The `CREATE PLUGGABLE DATABASE` statement with the `KEYSTORE IDENTIFIED BY` clause can clone a PDB that has encrypted data.

1.  Connect to the isolated mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Ensure that the TDE wallet of the PDB that you plan to clone is open.
    You can query the `STATUS` column of the `V$ENCRYPTION_WALLET` view to find if the TDE wallet is open.

    For example:

        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN FORCE KEYSTORE IDENTIFIED BY TDE_wallet_password;
3.  Clone the PDB.
    For example:

        CREATE PLUGGABLE DATABASE cdb1_pdb3 FROM cdb1_pdb1
        FILE_NAME_CONVERT=('cdb1_pdb1', 'pdb3/cdb1_pdb3') KEYSTORE
        IDENTIFIED BY TDE_wallet_password;

    Replace `TDE_wallet_password` with the password of the TDE wallet of the CDB where the `cdb1_pdb3` clone is created.

    After you create the cloned PDB, encrypted data is still accessible by the clone using the master encryption key of the original PDB. After a PDB is cloned, there may be user data in the encrypted tablespaces. This encrypted data is still accessible because the master encryption key of the source PDB is copied over to the destination PDB. Because the clone is a copy of the source PDB but will eventually follow its own course and have its own data and security policies, you should rekey the master encryption key of the cloned PDB.
4.  Rekey the master encryption key of the cloned PDB.
    For example:

        ADMINISTER KEY MANAGEMENT SET KEY
        IDENTIFIED BY TDE_wallet_password
        WITH BACKUP USING 'emp_key_backup';

    Before you rekey the master encryption key of the cloned PDB, the clone can still use master encryption keys that belong to the original PDB. However, these master encryption keys do not appear in the cloned PDB `V$` dynamic views. Rekeying the master encryption key ensures that the cloned PDB uses its own unique keys, which will be viewable in the `V$` views.

**Related Topics**

- [About Managing Cloned PDBs That Have Encrypted Data in United Mode](managing-keystores-encryption-keys-in-united-mode.md)

**Parent topic:** Administering Transparent Data Encryption in Isolated Mode

#### 7.8.4 Performing a Remote Clone of PDB with Encrypted Data Between Two CDBs in Isolated Mode

The `CREATE PLUGGABLE DATABASE` statement with the `KEYSTORE IDENTIFIED BY` clause can remotely clone a PDB that has encrypted data.

1.  Log in to the isolated mode PDB as a user who was granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Query the `STATUS` column of the `V$ENCRYPTION_WALLET` view to ensure that the TDE wallet of the PDB that you plan to clone is open.
3.  Create a database link for the PDB that you want to clone remotely.
    Use the `CREATE DATABASE LINK` SQL statement to create the database link. You must create the database link by following the database link prerequisites that are required for cloning a remote PDB or a non-CDB.
4.  Use the `CREATE PLUGGABLE DATABASE` statement with the `KEYSTORE IDENTIFIED BY` clause to perform the clone of the PDB.
    For example:

        CREATE PLUGGABLE DATABASE cdb1_pdb3
        FROM cdb1_pdb1
        FILE_NAME_CONVERT=('cdb1_pdb1', 'pdb3/cdb1_pdb3') KEYSTORE
        IDENTIFIED BY TDE_wallet_password;

    Replace `TDE_wallet_password` with the password of the TDE wallet of the CDB where the `cdb1_pdb3` clone is created.

    After you create the cloned PDB, encrypted data is still accessible by the clone using the master encryption key of the original PDB. After a PDB is cloned, there may be user data in the encrypted tablespaces. This encrypted data is still accessible because the master encryption key of the source PDB is copied over to the destination PDB. Because the clone is a copy of the source PDB but will eventually follow its own course and have its own data and security policies, you should rekey the master encrytion key of the cloned PDB.
5.  Rekey the master encryption key of the remotely cloned PDB.
    For example:

        ADMINISTER KEY MANAGEMENT SET KEY
        FORCE KEYSTORE
        IDENTIFIED BY TDE_wallet_password
        WITH BACKUP USING 'emp_key_backup';

    In this example, `FORCE KEYSTORE` is included because the TDE wallet must be open during the rekey operation.

    Before you rekey the master encryption key of the cloned PDB, the clone can still use master encryption keys that belong to the original PDB. However, these master encryption keys do not appear in the cloned PDB `V$` dynamic views. Rekeying the master encryption key ensures that the cloned PDB uses its own unique keys, which will be viewable in the `V$` views.

**Related Topics**

- [About Managing Cloned PDBs That Have Encrypted Data in United Mode](managing-keystores-encryption-keys-in-united-mode.md)
- [Step 2: Open the TDE Wallet in a United Mode PDB](managing-keystores-encryption-keys-in-united-mode.md)
- [Oracle Multitenant Administrator's Guide](../multi/cloning-a-pdb.md)
- [Oracle Multitenant Administrator's Guide](../multi/cloning-a-pdb.md)
- [Oracle Database SQL Language Reference](../sqlrf/CREATE-DATABASE-LINK.md)

**Parent topic:** Administering Transparent Data Encryption in Isolated Mode

#### 7.8.5 Relocating an Encrypted PDB in Isolated Mode

The `CREATE PLUGGABLE DATABASE` statement with the `KEYSTORE IDENTIFIED BY` clause can relocate across CDBs a cloned PDB that has encrypted data.

1.  Connect to the isolated mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Query the `STATUS` column of the `V$ENCRYPTION_WALLET` view to ensure that the TDE wallet of the PDB that you want to relocate is open.
3.  Create a database link for the PDB that you want to relocate.
    Use the `CREATE DATABASE LINK` SQL statement to create the database link. You must create the database link by following the database link prerequisites that are required for relocating a remote PDB or a non-CDB.
4.  Use the `CREATE PLUGGABLE DATABASE` statement with the `KEYSTORE IDENTIFIED BY` clause to relocate the PDB.
    For example:

        CREATE PLUGGABLE DATABASE target_pdb_name
        FROM src_pdb_name@dblink RELOCATE
        KEYSTORE IDENTIFIED BY TDE_wallet_password;

    Replace `TDE_wallet_password` with the password of the TDE wallet of the CDB where the `cdb1_pdb3` clone is created.

    After you create the cloned PDB, encrypted data is still accessible by the clone using the master encryption key of the original PDB. After a PDB is cloned, there may be user data in the encrypted tablespaces. This encrypted data is still accessible because the master encryption key of the source PDB is copied over to the destination PDB. Because the clone is a copy of the source PDB but will eventually follow its own course and have its own data and security policies, you should rekey the master encrytion key of the cloned PDB.
5.  Rekey the master encryption key of the remotely cloned PDB.
    For example:

        ADMINISTER KEY MANAGEMENT SET KEY
        FORCE KEYSTORE
        IDENTIFIED BY TDE_wallet_password
        WITH BACKUP USING 'emp_key_backup';

    In this example, `FORCE KEYSTORE` is included because the TDE wallet must be open during the rekey operation.

    Before you rekey the master encryption key of the cloned PDB, the clone can still use master encryption keys that belong to the original PDB. However, these master encryption keys do not appear in the cloned PDB `V$` dynamic views. Rekeying the master encryption key ensures that the cloned PDB uses its own unique keys, which will be viewable in the `V$` views.

**Related Topics**

- [About Managing Cloned PDBs That Have Encrypted Data in United Mode](managing-keystores-encryption-keys-in-united-mode.md)
- [Step 2: Open the TDE Wallet in a United Mode PDB](managing-keystores-encryption-keys-in-united-mode.md)
- [Oracle Multitenant Administrator's Guide](../multi/cloning-a-pdb.md)
- [Oracle Multitenant Administrator's Guide](../multi/cloning-a-pdb.md)
- [Oracle Database SQL Language Reference](../sqlrf/CREATE-DATABASE-LINK.md)

**Parent topic:** Administering Transparent Data Encryption in Isolated Mode

#### 7.8.6 How Keystore Open and Close Operations Work in Isolated Mode

You should be aware of how keystore (TDE wallets or external keystores) open and close operations work in isolated mode.

For each PDB in isolated mode, you must explicitly open the password-protected TDE wallet or external keystore in the PDB to enable the Transparent Data Encryption operations to proceed. (Auto-login and local auto-login TDE wallets open automatically.) Closing a keystore on a PDB blocks all of the Transparent Data Encryption operations on that PDB.

The open and close keystore operations in a PDB depend on the open and close status of the keystore in the PDB.

Note the following:

- You can create a separate keystore password for each PDB in the multitenant environment.

- Before you can manually open a password-protected software or an external keystore in an individual PDB, you must open the keystore in the CDB root.

- If an auto-login TDE wallet is in use, or if the TDE wallet is closed, then include the `FORCE KEYSTORE` clause in the `ADMINISTER KEY MANAGEMENT` statement when you open the TDE wallet.

- If the keystore is a password-protected TDE wallet that uses an external store for passwords, then replace the password in the `IDENTIFIED BY` clause with `EXTERNAL STORE`.

- Before you can set a TDE master encryption key in an individual PDB, you must set the key in the CDB root. Oracle highly recommends that you include the `USING TAG` clause when you set keys in PDBs. For example:

      SELECT ' ADMINISTER KEY MANAGEMENT SET KEY
      USING TAG '''||SYS_CONTEXT('USERENV', 'CON_NAME')||' '||TO_CHAR (SYSDATE, 'YYYY-MM-DD HH24:MI:SS')||'''
      FORCE KEYSTORE IDENTIFIED BY EXTERNAL STORE
      WITH BACKUP CONTAINER = CURRENT;' AS "SET KEY COMMAND" FROM DUAL;

  Including the `USING TAG` clause enables you to quickly and easily identify the keys that belong to a certain PDB, and when they were created.

- Auto-login and local auto-login TDE wallets open automatically. You do not need to manually open these from the root first, or from the PDB.

- If there is any PDB configured in isolated mode that has its keystore open, then an attempt to close the keystore in the CDB root would fail with an `ORA-46692 cannot close wallet` error. Use the `FORCE CLOSE` clause in the `ADMINISTER KEY MANAGEMENT` statement to override this behavior.

- If you perform an `ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN` statement in the CDB root and set the `CONTAINER` clause to `ALL`, then the keystore will only be opened in each open PDB that is configured in united mode. Keystores for any PDBs that are configured in isolated mode are not opened.

**Parent topic:** Administering Transparent Data Encryption in Isolated Mode

#### 7.8.7 Exporting and Importing Master Encryption Keys for a PDB in Isolated Mode

In isolated mode, the `EXPORT` and `IMPORT` clauses of `ADMINISTER KEY MANAGEMENT EXPORT` can export or import master encryption keys for a PDB.

- About Exporting and Importing Master Encryption Keys for a PDB in Isolated Mode
  In isolated mode, you can export and import master encryption keys from the CDB root in the same way that you export and import this key for a non-CDB database.
- Exporting or Importing a Master Encryption Key for a PDB in Isolated Mode
  In isolated mode, the `ADMINISTER KEY MANAGEMENT` statement can export or import a master encryption key for a PDB.
- Example: Exporting a Master Encryption Key from a PDB in Isolated Mode
  The `ADMINISTER KEY MANAGEMENT EXPORT ENCRYPTION KEYS` statement can export master encryption keys for a PDB.
- Example: Importing a Master Encryption Key into a PDB in Isolated Mode
  The `ADMINISTER KEY MANAGEMENT IMPORT ENCRYPTION KEYS` statement can import a master encryption key into a PDB.

**Parent topic:** Administering Transparent Data Encryption in Isolated Mode

##### 7.8.7.1 About Exporting and Importing Master Encryption Keys for a PDB in Isolated Mode

In isolated mode, you can export and import master encryption keys from the CDB root in the same way that you export and import this key for a non-CDB database.

You can export and import all of the master encryption keys that belong to the PDB by exporting and importing the master encryption keys from within a PDB. Export and import operations of master encryption keys in a PDB supports the PDB unplug and plug operations. During a PDB unplug and plug operations, all the master encryption keys that belong to a PDB, as well as the metadata, are involved. Therefore, the `WITH IDENTIFIER` clause of the `ADMINISTER KEY MANAGEMENT EXPORT` statement is not allowed when you export keys from within a PDB. The `WITH IDENTIFIER` clause is only permitted in the CDB root.

You should include the `FORCE KEYSTORE` clause if the CDB root has an auto-login keystore or if the keystore is closed. If the keystore has been configured to use an external store for the password, then use the `IDENTIFIED BY EXTERNAL STORE` clause. For example, to perform an export operation for this scenario:

    ADMINISTER KEY MANAGEMENT EXPORT KEYS
    WITH SECRET "my_secret"
    TO '/etc/TDE/export.exp'
    FORCE KEYSTORE
    IDENTIFIED BY EXTERNAL STORE;

This `ADMINISTER KEY MANAGEMENT EXPORT` operation exports not only the keys but creates metadata that is necessary for PDB environments (as well as for cloning operations).

Inside a PDB, the export operation of master encryption keys exports the keys that were created or activated by a PDB with the same GUID as the PDB where the keys are being exported. Essentially, all of the keys that belong to a PDB where the export is being performed will be exported.

The importing of master encryption keys from an export file within a PDB takes place only if the master encryption key was exported from another PDB with the same GUID. To support the plug-in of a PDB into a CDB, the import will also import the master encryption keys from an export file that contains the master encryption keys of a non-CDB exported without the `WITH IDENTIFIER` clause. Because the PDB-specific details, such as the PDB name and database ID, can change from one CDB to the next, the PDB-specific information is modified during the import to reflect the updated PDB information.

**Note:**

Within a PDB, you can only export the keys of a PDB as a whole. The ability to export them selectively based on a query or an identifier is restricted to the root.

**Parent topic:** Exporting and Importing Master Encryption Keys for a PDB in Isolated Mode

##### 7.8.7.2 Exporting or Importing a Master Encryption Key for a PDB in Isolated Mode

In isolated mode, the `ADMINISTER KEY MANAGEMENT` statement can export or import a master encryption key for a PDB.

1.  Log in to the isolated mode PDB as a user who was granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.

2.  Perform the export or import operation.

    For example:

        ADMINISTER KEY MANAGEMENT EXPORT ENCRYPTION KEYS
        WITH SECRET "hr_secret" TO '/tmp/export.p12'
        FORCE KEYSTORE
        IDENTIFIED BY password;

    Ensure that you include the `FORCE KEYSTORE` clause because the keystore must be open for this operation.

**Related Topics**

- Example: Exporting a Master Encryption Key from a PDB in Isolated Mode

**Parent topic:** Exporting and Importing Master Encryption Keys for a PDB in Isolated Mode

##### 7.8.7.3 Example: Exporting a Master Encryption Key from a PDB in Isolated Mode

The `ADMINISTER KEY MANAGEMENT EXPORT ENCRYPTION KEYS` statement can export master encryption keys for a PDB.

Example 7-1 shows how to export a master encryption key from the PDB `hrpdb`. In this example, the `FORCE KEYSTORE` clause is included in case the auto-login keystore is in use, or if the keystore is closed.

Example 7-1 Exporting a Master Encryption Key from a PDB

    ADMINISTER KEY MANAGEMENT EXPORT ENCRYPTION KEYS
    WITH SECRET "my_secret" TO '/tmp/export.p12'
    FORCE KEYSTORE
    IDENTIFIED BY password;

**Parent topic:** Exporting and Importing Master Encryption Keys for a PDB in Isolated Mode

##### 7.8.7.4  Example: Importing a Master Encryption Key into a PDB in Isolated Mode

The `ADMINISTER KEY MANAGEMENT IMPORT ENCRYPTION KEYS` statement can import a master encryption key into a PDB.

Example 7-2 shows how to import a master encryption key into the PDB `hrpdb`.

Example 7-2 Importing a Master Encryption Key into a PDB

    ADMINISTER KEY MANAGEMENT IMPORT ENCRYPTION KEYS
    WITH SECRET "my_secret"
    FROM '/tmp/export.p12'
    FORCE KEYSTORE
    IDENTIFIED BY password
    WITH BACKUP;

**Parent topic:** Exporting and Importing Master Encryption Keys for a PDB in Isolated Mode
