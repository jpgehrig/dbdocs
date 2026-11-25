## 5 Managing the Keystore and the Master Encryption Key

You can modify settings for the keystore and TDE master encryption key, and store Oracle Database and store Oracle GoldenGate secrets in a keystore.

- Managing the Keystore
  You can perform maintenance activities on keystores such as changing passwords, and backing up, merging, and moving keystores.
- Managing the TDE Master Encryption Key
  You can manage the TDE master encryption key in several ways.
- Storing Oracle Database Secrets
  Secrets are data that support internal Oracle Database features that integrate external clients such as Oracle GoldenGate into the database.
- Storing Oracle GoldenGate Secrets in a Keystore
  You can store Oracle GoldenGate secrets in Transparent Data Encryption keystores.

**Parent topic:** [Using Transparent Data Encryption](asopart1.md)

### 5.1 Managing the Keystore

You can perform maintenance activities on keystores such as changing passwords, and backing up, merging, and moving keystores.

- Performing Operations That Require a Keystore Password
  Many `ADMINISTER KEY MANAGEMENT` operations require access to a keystore password, for both TDE wallets and external keystores.
- Changing the Password of a Software Keystore
  Oracle Database enables you to easily change password-protected software keystore passwords.
- Changing the Oracle Key Vault Password
  To change the password of Oracle Key Vault, you use `okvutil`, which is part of the Oracle Key Vault endpoint software on the database host.
- Configuring an External Store for a Keystore Password
  An external store for a keystore password stores the keystore password in a centrally accessed and managed location.
- Backing Up Password-Protected Software Keystores
  When you back up a password-protected software keystore, you can create a backup identifier string to describe the backup type.
- How the V\$ENCRYPTION_WALLET View Interprets Backup Operations
  The `BACKUP` column of the `V$ENCRYPTION_WALLET` view indicates a how a copy of the keystore was created.
- Backups of the External Keystore
  You cannot use Oracle Database to back up external keystores.
- Merging TDE Wallets
  You can merge TDE wallets in a variety of ways.
- Moving a TDE Wallet to a New Location
  You move a TDE wallet to a new location after you have updated the `WALLET_ROOT` parameter.
- Moving a TDE Wallet Out of Automatic Storage Management
  You can use the `ADMINISTER KEY MANAGEMENT` statement to move a TDE wallet out Automatic Storage Management.
- Migrating from a TDE Wallet to Oracle Key Vault
  You can migrate between password-protected TDE wallets and external keystores in Oracle Key Vault.
- Migration of Keystores to and from Oracle Key Vault
  You can use Oracle Key Vault to migrate both TDE wallets and external keystores to and from Oracle Key Vault.
- Configuring Keystores for Automatic Storage Management
  You can store a TDE wallet on an Automatic Storage Management (ASM) disk group.
- Closing a Keystore
  You can manually close software and external keystores.
- Backup and Recovery of Encrypted Data
  For TDE wallets, you cannot access encrypted data without the TDE master encryption key.
- Dangers of Deleting Keystores
  Oracle strongly recommends that you do not delete keystores.
- Features That Are Affected by Deleted Keystores
  Some features can be adversely affected if a keystore is deleted and a TDE master encryption key residing in that keystore is later needed.

**Parent topic:** Managing the Keystore and the Master Encryption Key

#### 5.1.1 Performing Operations That Require a Keystore Password

Many `ADMINISTER KEY MANAGEMENT` operations require access to a keystore password, for both TDE wallets and external keystores.

In some cases, a keystore depends on an auto-login TDE wallet before the operation can succeed. Auto-login TDE wallets open automatically when they are configured and a key is requested. They are generally used for operations where the TDE wallet could be closed but a database operation needs a key (for example, after the database is restarted). Because the auto-login TDE wallet opens automatically, it can be retrieved to perform a database operation without manual intervention. However, some keystore operations that require the keystore password cannot be performed when the auto-login keystore is open. The auto-login TDE wallet must be closed and the password-protected keystore must be opened for the keystore operations that require a password.

In a multitenant environment, the re-opening of keystores affects other PDBs. For example, an auto-login TDE wallet in the root must be accessible by the PDBs in the CDB for this root.

You can temporarily open the TDE wallet by including the `FORCE KEYSTORE` clause in the `ADMINISTER KEY MANAGEMENT` statement when you perform the following operations: rotating a TDE wallet password; creating, using, rekeying, tagging, importing, exporting, migrating, or reverse migrating encryption keys; opening or backing up TDE wallet; adding, updating, or deleting secret TDE wallets. In a multitenant environment, if no TDE wallet is open in the root, then `FORCE KEYSTORE` opens the password-protected TDE wallet in the root.

**Parent topic:** Managing the Keystore

#### 5.1.2 Changing the Password of a Software Keystore

Oracle Database enables you to easily change password-protected software keystore passwords.

- About Changing the Password of a Password-Protected Software Keystore
  You can only change the password for protected-protected software keystores.
- Changing the Password-Protected Software Keystore Password
  To change the password of a password-protected software keystore, you must use the `ADMINISTER KEY MANAGEMENT` statement.

**Parent topic:** Managing the Keystore

##### 5.1.2.1 About Changing the Password of a Password-Protected Software Keystore

You can only change the password for protected-protected software keystores.

You can change this password at any time, as per the security policies, compliance guidelines, and other security requirements of your site. As part of the command to change the password, you will be forced to specify the `WITH BACKUP` clause, and thus forced to make a backup of the current keystore. During the password change operation, Transparent Data Encryption operations such as encryption and decryption will continue to work normally.

You can change this password at any time. You may want to change this password if you think it was compromised.

**Parent topic:** Changing the Password of a Software Keystore

##### 5.1.2.2 Changing the Password-Protected Software Keystore Password

To change the password of a password-protected software keystore, you must use the `ADMINISTER KEY MANAGEMENT` statement.

1.  Log in to the database instance as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.

2.  Change the password of the password-protected software keystore by using the following syntax:

        ADMINISTER KEY MANAGEMENT ALTER KEYSTORE PASSWORD
        [FORCE KEYSTORE]
        IDENTIFIED BY
        old_password SET new_password
        WITH BACKUP [USING 'backup_identifier'];

    In this specification:

    - `FORCE KEYSTORE` temporarily opens the password-protected TDE wallet for this operation. You must open the TDE wallet for this operation.

    - `old_password` is the current keystore password that you want to change.

    - `new_password` is the new password that you will set for the keystore.

    - `WITH BACKUP` creates a backup of the current keystore before the password is changed. You must include this clause.

    - `backup_identifier` specifies an optional identifier string for the backup that is created. The `backup_identifier` is added to the name of the backup file. Enclose `backup_identifier` in single quotation marks (' '). This identifier is appended to the named keystore file (for example, `ewallet_``time_stamp``_emp_key_pwd_change.p12`).

    The following example backs up the current keystore and then changes the password for the keystore:

        ADMINISTER KEY MANAGEMENT ALTER KEYSTORE PASSWORD
        FORCE KEYSTORE
        IDENTIFIED BY
        old_password SET new_password
        WITH BACKUP USING 'pwd_change';

        keystore altered.

**Parent topic:** Changing the Password of a Software Keystore

#### 5.1.3 Changing the Oracle Key Vault Password

To change the password of Oracle Key Vault, you use `okvutil`, which is part of the Oracle Key Vault endpoint software on the database host.

1.  Log in to the database instance as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Close the external keystore.
    - Close the connection to the external key manager:

          ADMINISTER KEY MANAGEMENT SET KEYSTORE CLOSE
          IDENTIFIED BY Oracle_Key_Vault_password | EXTERNAL STORE CONTAINER = ALL;

      If the keystore was auto-opened by the database, then close the connection to Oracle Key Vault as follows:

          ADMINISTER KEY MANAGEMENT SET KEYSTORE CLOSE
          CONTAINER = ALL;
3.  Change the Oracle Key Vault password.
        WALLET_ROOT/okv/bin/okvutil changepwd -t wallet -l WALLET_ROOT/okv/ssl
4.  Open the external keystore.
    - For example, for Oracle Key Vault:

          ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN FORCE KEYSTORE
          IDENTIFIED BY new_Oracle_Key_Vault_pwd CONTAINER =ALL;

    - If the old Oracle Key Vault password was stored in a \[local\] auto-open wallet in the `WALLET_ROOT``/tde_seps` directory, then update the password using the following syntax:

          ADMINISTER KEY MANAGEMENT UPDATE SECRET 'new-Oracle_Key_Vault_password'
          FOR CLIENT 'Oracle_Key_Vault_password" TO [LOCAL] AUTO_LOGIN KEYSTORE 'WALLET_ROOT/tde_seps;

      Then you can open the connection to Oracle Key Vault as follows:

          ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN
          [FORCE KEYSTORE] IDENTIFIED BY EXTERNAL STORE CONTAINER = ALL;

**Parent topic:** Managing the Keystore

#### 5.1.4 Configuring an External Store for a Keystore Password

An external store for a keystore password stores the keystore password in a centrally accessed and managed location.

- About Configuring an External Store for a Keystore Password
  An external store for a keystore password allows you to easily remove that keystore password from the `ADMINISTER KEY MANAGEMENT` command line.
- Configuring the External Keystore Password Store with WALLET_ROOT
  When you configure TDE by using the `WALLET_ROOT` parameter, the external keystore password store is auto-discovered in the `WALLET_ROOT``/tde_seps` directory.
- When to Use the EXTERNAL STORE Clause After Configuration
  After you configure the external store for a keystore password, you can use the `EXTERNAL_STORE` clause in the `ADMINISTER KEY MANAGEMENT` statement.

**Parent topic:** Managing the Keystore

##### 5.1.4.1 About Configuring an External Store for a Keystore Password

An external store for a keystore password allows you to easily remove that keystore password from the `ADMINISTER KEY MANAGEMENT` command line.

This feature implements separation of duties between database administrators and key administrators. It is also useful for situations in which you use automated tools to perform Transparent Data Encryption operations that require a password, when the scripts that run the automated tools include hard-coded password. To avoid hard-coding the password in a script, you can store this password in an external store on the database server. In a multitenant environment, different PDBs can make use of the external store.

In a multitenant environment, all PDBs in united mode use the hidden password of the root container. In isolated mode, each PDB can have its own keystore password in its own external store.

**Related Topics**

- Storing Oracle Database Secrets

**Parent topic:** Configuring an External Store for a Keystore Password

##### 5.1.4.2 Configuring the External Keystore Password Store with WALLET_ROOT

When you configure TDE by using the `WALLET_ROOT` parameter, the external keystore password store is auto-discovered in the `WALLET_ROOT``/tde_seps` directory.

- Run the `ADMINISTER KEY MANAGEMENT` statement by using the following syntax:
      ADMINISTER KEY MANAGEMENT ADD SECRET 'keystore_password'
      FOR CLIENT 'TDE_WALLET|OKV_PASSWORD'
      TO [LOCAL] AUTO_LOGIN KEYSTORE 'WALLET_ROOT/tde_seps';

**Related Topics**

- When to Use the EXTERNAL STORE Clause After Configuration

**Parent topic:** Configuring an External Store for a Keystore Password

##### 5.1.4.3 When to Use the EXTERNAL STORE Clause After Configuration

After you configure the external store for a keystore password, you can use the `EXTERNAL_STORE` clause in the `ADMINISTER KEY MANAGEMENT` statement.

You must use the `EXTERNAL STORE` clause in the `ADMINISTER KEY MANAGEMENT` statement for the following operations: opening, closing, backing up the keystore; adding, updating, or deleting a secret keystore; creating, using, rekeying, tagging, importing, exporting encryption keys.

For example:

    ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN
    IDENTIFIED BY EXTERNAL STORE;

You can change or delete external keystore passwords by using the `ADMINISTER KEY MANAGEMENT UPDATE CLIENT SECRET` statement or the `ADMINISTER KEY MANAGEMENT DELETE CLIENT SECRET` statement.

**Parent topic:** Configuring an External Store for a Keystore Password

#### 5.1.5 Backing Up Password-Protected Software Keystores

When you back up a password-protected software keystore, you can create a backup identifier string to describe the backup type.

- About Backing Up Password-Protected TDE Wallets
  You must back up password-protected TDE wallets, as per the security policy and requirements of your site.
- Creating a Backup Identifier String for the Backup TDE Wallet
  The backup file name of a software password wallet is derived from the name of the password-protected TDE wallet.
- Backing Up a Password-Protected TDE Wallet
  The `BACKUP KEYSTORE` clause of the `ADMINISTER KEY MANAGEMENT` statement backs up a password-protected TDE wallet.

**Parent topic:** Managing the Keystore

##### 5.1.5.1 About Backing Up Password-Protected TDE Wallets

You must back up password-protected TDE wallets, as per the security policy and requirements of your site.

A backup of the TDE wallet contains all of the keys contained in the original TDE wallet. Oracle Database prefixes the backup TDE wallet with the creation time stamp (UTC). If you provide an identifier string, then this string is inserted between the time stamp and TDE wallet name.

After you complete the backup operation, the keys in the original TDE wallet are marked as "backed up". You can check the status of keys querying the `V$ENCRYPTION_WALLET` data dictionary view.

You cannot back up auto-login or local auto-login TDE wallets. No new keys can be added to them directly through the `ADMINISTER KEY MANAGEMENT` statement operations. The information in these TDE wallets is only read and hence there is no need for a backup.

You must include the `WITH BACKUP` clause in any `ADMINISTER KEY MANAGEMENT` statement that changes the wallet (for example, changing the wallet password, or setting the master encryption key).

**Parent topic:** Backing Up Password-Protected Software Keystores

##### 5.1.5.2 Creating a Backup Identifier String for the Backup TDE Wallet

The backup file name of a software password wallet is derived from the name of the password-protected TDE wallet.

- To create a backup identifier string for a backup TDE wallet, use the `ADMINISTER KEY MANAGEMENT` SQL statement with the `BACKUP KEYSTORE` clause, with the following syntax:
      ewallet_creation-time-stamp-in-UTC_user-defined-string.p12

  When you create the backup identifier (`user_defined_string`), use the operating system file naming convention. For example, in UNIX systems, you may want to ensure that this setting does not have spaces.

  The following example shows the creation of a backup TDE wallet that uses a user-identified string, and how the resultant TDE wallet appears in the file system. This example includes the `FORCE KEYSTORE` clause in the event the auto-login TDE wallet is in use or the TDE wallet is closed.

      ADMINISTER KEY MANAGEMENT BACKUP KEYSTORE USING 'Monthly-backup-2013-04'
      FORCE KEYSTORE
      IDENTIFIED BY TDE_wallet_password;

  This version is for a scenario in which the password is stored in an external store:

      ADMINISTER KEY MANAGEMENT BACKUP KEYSTORE USING 'Monthly-backup-2013-04'
      FORCE KEYSTORE
      IDENTIFIED BY EXTERNAL STORE;

  Resultant TDE wallet file:

      ewallet_2013041513244657_Monthly-backup-2013-04.p12

**Parent topic:** Backing Up Password-Protected Software Keystores

##### 5.1.5.3 Backing Up a Password-Protected TDE Wallet

The `BACKUP KEYSTORE` clause of the `ADMINISTER KEY MANAGEMENT` statement backs up a password-protected TDE wallet.

- Back up the keystore by using the following syntax:
      ADMINISTER KEY MANAGEMENT BACKUP KEYSTORE
      [USING 'backup_identifier']
      FORCE KEYSTORE]
      IDENTIFIED BY [EXTERNAL STORE | TDE_wallet_password]
      [TO 'keystore_location'];

  In this specification:

  - `USING` `backup_identifier` is an optional string that you can provide to identify the backup. Enclose this identifier in single quotation marks (`' '`). This identifier is appended to the named keystore file (for example, `ewallet_``time-stamp``_emp_key_backup.p12`).

  - `FORCE KEYSTORE` temporarily opens the password-protected TDE wallet for this operation. You must open the TDE wallet for this operation.

  - `IDENTIFIED BY` can be one of the following settings:

    - `EXTERNAL STORE` uses the keystore password stored in the external store to perform the keystore operation.

    - `TDE_wallet_password` is the password for the keystore.

  - `keystore_location` is the path at which the backup keystore is stored. If you do not specify the `keystore_location`, then the backup is created in the same directory as the original keystore. Enclose this location in single quotation marks (`' '`).

  The following example backs up a TDE wallet into another location.

      ADMINISTER KEY MANAGEMENT BACKUP KEYSTORE
      USING 'hr.emp_wallet'
      FORCE KEYSTORE
      IDENTIFIED BY TDE_wallet_password
      TO '/etc/ORACLE/KEYSTORE/DB1/';

      keystore altered.

  In the following version, the password for the TDE wallet is external, so the `EXTERNAL STORE` clause is used. The TDE wallet is backed up into the same directory as the current TDE wallet.

      ADMINISTER KEY MANAGEMENT BACKUP KEYSTORE
      USING 'hr.emp_wallet'
      FORCE KEYSTORE
      IDENTIFIED BY EXTERNAL STORE;

  After you run this statement, an `ewallet_``identifier``.p12` file (for example, `ewallet_``time-stamp``_hr.emp_wallet.p12`) appears in the keystore location.

**Parent topic:** Backing Up Password-Protected Software Keystores

#### 5.1.6 How the V\$ENCRYPTION_WALLET View Interprets Backup Operations

The `BACKUP` column of the `V$ENCRYPTION_WALLET` view indicates a how a copy of the keystore was created.

The column indicates if a copy of the keystore had been created with the `WITH BACKUP` clause of the `ADMINISTER KEY MANAGEMENT` statement or the `ADMINISTER KEY MANAGEMENT BACKUP KEYSTORE` statement.

When you modify a key or a secret, the modifications that you make do not exist in the previously backed-up copy, because you make a copy and then modify the key itself. Because there is no copy of the modification in the previous keystores, the `BACKUP` column is set to `NO`, even if the `BACKUP` had been set to `YES` previously. Hence, if the `BACKUP` column is `YES`, then after you perform an operation that requires a backup, such as adding a custom attribute tag, the `BACKUP` column value changes to `NO`.

**Parent topic:** Managing the Keystore

#### 5.1.7 Backups of the External Keystore

You cannot use Oracle Database to back up external keystores.

Uploading TDE wallets into Oracle Key Vault is another way of backing up the wallet and having it available immediately if the need arises (for example after accidental deletion of the wallet, or file corruption). If the database is not migrated to online key management with Oracle Key Vault, then it keeps relying on the TDE wallet, even if the wallet has been uploaded into Oracle Key Vault.

You can use the Oracle Key Vault `okvutil upload` and `okvutil download` commands to upload and download TDE wallets to and from Oracle Key Vault.

For example, to upload a TDE wallet to Oracle Key Vault:

    $ okvutil upload -l "/etc/oracle/wallets" -t wallet -g "HRWallet"
    Enter wallet password (<enter> for auto-login): password
    Enter Oracle Key Vault endpoint password: Key_Vault_endpoint_password

This example shows how to download a TDE wallet from Oracle Key Vault:

    $ okvutil download -l "/etc/oracle/wallets/orcl/" -t WALLET -g HRWallet
    Enter new wallet password(<enter> for auto-login): Oracle_wallet_password
    Confirm new wallet password: Oracle_wallet_password
    Enter Oracle Key Vault endpoint password: Key_Vault_endpoint_password

**Related Topics**

- [Oracle Key Vault Administrator's Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/asoag&id=OKVAG-GUID-A3E85D53-86C6-4B17-86E9-037AB61AFD40)

**Parent topic:** Managing the Keystore

#### 5.1.8 Merging TDE Wallets

You can merge TDE wallets in a variety of ways.

- About Merging TDE Wallets
  You can merge any combination of TDE wallets, but the merged keystore must be password-protected. It can have a password that is different from the constituent wallets.
- Merging One TDE Wallet into an Existing TDE Wallet
  You can use the `ADMINISTER KEY MANAGEMENT` statement with the `MERGE KEYSTORE` clause to merge one TDE wallet into another existing TDE wallet.
- Merging Two TDE Wallets into a Third New TDE Wallet
  You can merge two TDE wallets into a third new TDE wallet. The two existing source TDE wallets are not changed.
- Merging an Auto-Login TDE Wallet into an Existing Password-Protected TDE Wallet
  You can merge an auto-login TDE wallet into an existing password-protected TDE wallet.
- Reversing a TDE Wallet Merge Operation
  You cannot directly reverse a TDE wallet merge operation.

**Parent topic:** Managing the Keystore

##### 5.1.8.1 About Merging TDE Wallets

You can merge any combination of TDE wallets, but the merged keystore must be password-protected. It can have a password that is different from the constituent wallets.

To use the merged TDE wallet, you must explicitly open the merged TDE wallet after you create it, even if one of the constituent TDE wallets was already open before the merge.

Whether a common key from two source TDE wallets is added or overwritten to a merged TDE wallet depends on how you write the `ADMINISTER KEY MANAGEMENT` merge statement. For example, if you merge TDE wallet 1 and TDE wallet 2 to create TDE wallet 3, then the key in TDE wallet 1 is added to TDE wallet 3. If you merge TDE wallet 1 into TDE wallet 2, then the common key in TDE wallet 2 is not overwritten.

The `ADMINISTER KEY MANAGEMENT` merge statement has no bearing on the configured TDE wallet that is in use. However, the merged TDE wallet can be used as the new configured database TDE wallet if you want. Remember that you must reopen the TDE wallet if you are using the newly created TDE wallet as the TDE wallet for the database at the location configured by the `WALLET_ROOT` parameter.

**Related Topics**

- Migrating from a TDE Wallet to Oracle Key Vault

**Parent topic:** Merging TDE Wallets

##### 5.1.8.2 Merging One TDE Wallet into an Existing TDE Wallet

You can use the `ADMINISTER KEY MANAGEMENT` statement with the `MERGE KEYSTORE` clause to merge one TDE wallet into another existing TDE wallet.

- To perform this type of merge, use the following SQL statement:
      ADMINISTER KEY MANAGEMENT MERGE KEYSTORE 'TDE_wallet1_location'
      [IDENTIFIED BY TDE_wallet1_password]
      INTO EXISTING KEYSTORE 'TDE_wallet2_location'
      IDENTIFIED BY TDE_wallet2_password
      [WITH BACKUP [USING 'backup_identifier]];

  In this specification:

  - `TDE_wallet1_location` is the directory location of the first TDE wallet, which will be left unchanged after the merge. Enclose this path in single quotation marks (' ').

  - The `IDENTIFIED BY` clause is required for the first TDE wallet if it is a password-protected TDE wallet. `TDE_wallet1_password` is the password for the first TDE wallet.

  - `TDE_wallet2_location` is the directory location of the second TDE wallet into which the first TDE wallet is to be merged. Enclose this path in single quotation marks (' ').

  - `TDE_wallet2_password` is the password for the second keystore.

  - `WITH BACKUP` creates a backup of the TDE wallet. Optionally, you can use the `USING` clause to add a brief description of the backup. Enclose this description in single quotation marks (' '). This identifier is appended to the named TDE wallet file (for example, `ewallet_``time_stamp``_emp_key_backup``.p12`, with `emp_key_backup` being the backup identifier). Follow the file naming conventions that your operating system uses.

The resultant TDE wallet after the merge operation is always a password-protected TDE wallet.

**Parent topic:** Merging TDE Wallets

##### 5.1.8.3 Merging Two TDE Wallets into a Third New TDE Wallet

You can merge two TDE wallets into a third new TDE wallet. The two existing source TDE wallets are not changed.

- Merge the TDE wallets by using the following syntax:
      ADMINISTER KEY MANAGEMENT MERGE KEYSTORE 'TDE_wallet1_location'
      [IDENTIFIED BY TDE_wallet1_password]
      AND KEYSTORE 'TDE_wallet2_location'
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
      IDENTIFIED BY existing_password_for_keystore_2
      INTO NEW KEYSTORE '/etc/ORACLE/KEYSTORE/DB3'
      IDENTIFIED BY new_password_for_keystore_3;

      keystore altered.

**Parent topic:** Merging TDE Wallets

##### 5.1.8.4 Merging an Auto-Login TDE Wallet into an Existing Password-Protected TDE Wallet

You can merge an auto-login TDE wallet into an existing password-protected TDE wallet.

- Use the `ADMINISTER KEY MANAGEMENT MERGE KEYSTORE` SQL statement to merge an auto-login TDE wallet into an existing password-protected TDE wallet.
  The following example shows how to merge an auto-login TDE wallet into a password-protected TDE wallet. It also creates a backup of the second TDE wallet before creating the merged TDE wallet.
      ADMINISTER KEY MANAGEMENT MERGE KEYSTORE '/etc/ORACLE/KEYSTORE/DB1'
      INTO EXISTING KEYSTORE '/etc/ORACLE/KEYSTORE/DB2'
      IDENTIFIED BY keystore_password WITH BACKUP;

  In this specification:

  - `MERGE KEYSTORE` must specify the auto-login TDE wallet.

  - `EXISTING KEYSTORE` refers to the password TDE wallet.

**Parent topic:** Merging TDE Wallets

##### 5.1.8.5 Reversing a TDE Wallet Merge Operation

You cannot directly reverse a TDE wallet merge operation.

When you merge a TDE wallet into an existing TDE wallet (rather than creating a new one), you must include the `WITH BACKUP` clause in the `ADMINISTER KEY MANAGEMENT` statement to create a backup of this existing TDE wallet. Later on, if you decide that you must reverse the merge, you can replace the merged TDE wallet with the one that you backed up. In other words, suppose you want merge TDE wallet A into TDE wallet B. By using the `WITH BACKUP` clause, you create a backup for TDE wallet B before the merge operation begins. (The original TDE wallet A is still intact.) To reverse the merge operation, revert to the backup that you made of TDE wallet B.

- Use the `ADMINISTER KEY MANAGEMENT MERGE KEYSTORE` SQL statement to perform merge operations.
  - For example, to perform a merge operation into an existing TDE wallet:

        ADMINISTER KEY MANAGEMENT MERGE KEYSTORE '/etc/ORACLE/KEYSTORE/DB1'
        INTO EXISTING KEYSTORE '/etc/ORACLE/KEYSTORE/DB2'
        IDENTIFIED BY password WITH BACKUP USING "merge1";

    Replace the new TDE wallet with the backup TDE wallet, which in this case would be named `ewallet_``time-stamp``_merge1.p12`.

  - To merge an auto-login TDE wallet into a password-based TDE wallet, use the `ADMINISTER KEY MANAGEMENT MERGE KEYSTORE` SQL statement.

**Parent topic:** Merging TDE Wallets

#### 5.1.9 Moving a TDE Wallet to a New Location

You move a TDE wallet to a new location after you have updated the `WALLET_ROOT` parameter.

If you are using Oracle Key Vault, then you can configure a TDE direct connection where Key Vault directly manages the master encryption keys. In this case, you will never need to manually move the TDE wallet to a new location.

1.  Connect to the united mode CDB root or isolated mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.

2.  Back up the TDE wallet.

    For example:

        ADMINISTER KEY MANAGEMENT BACKUP KEYSTORE
        USING 'hr.emp_keystore'
        FORCE KEYSTORE
        IDENTIFIED BY
        TDE_wallet_password TO '/etc/ORACLE/KEYSTORE/DB1/';

3.  Close the TDE wallet.

    Examples of ways that you can close the TDE wallet are as follows.

    For an auto-login TDE wallet:

        ADMINISTER KEY MANAGEMENT SET KEYSTORE CLOSE;

    For a password-protected TDE wallet:

        ADMINISTER KEY MANAGEMENT SET KEYSTORE CLOSE
        IDENTIFIED BY TDE_wallet_password;

    For a TDE wallet for which the password is stored externally:

        ADMINISTER KEY MANAGEMENT SET KEYSTORE CLOSE
        IDENTIFIED BY EXTERNAL STORE;

4.  Exit the database session.

    For example, if you are logged in to SQL\*Plus:

        EXIT

5.  In the `init.ora` file for the database instance, update the `WALLET_ROOT` parameter to point to the new location where you want to move the TDE wallet.

6.  Use the operating system move command (such as `mv`) to move the TDE wallet with all of its keys to the new directory location.

**Related Topics**

- [Oracle Key Vault Administrator's Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/asoag&id=OKVAG10564)

**Parent topic:** Managing the Keystore

#### 5.1.10 Moving a TDE Wallet Out of Automatic Storage Management

You can use the `ADMINISTER KEY MANAGEMENT` statement to move a TDE wallet out Automatic Storage Management.

1.  Connect to the united mode CDB root or isolated mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Initialize a target TDE wallet on the file system by using the following syntax:
        ADMINISTER KEY MANAGEMENT CREATE KEYSTORE target_TDE_wallet_path
        IDENTIFIED BY target_TDE_wallet_password;

    In this specification:

    - `target_TDE_wallet_path` is the directory path to the target TDE wallet on the file system.

    - `target_TDE_wallet_password` is a password that you create for the TDE wallet.

    For example:

        ADMINISTER KEY MANAGEMENT CREATE KEYSTORE '/etc/ORACLE/KEYSTORE/DB1/' IDENTIFIED BY "target_TDE_wallet_password";
3.  Copy the TDE wallet from ASM to the target TDE wallet that you just created.
    This step requires that you merge the TDE wallet from ASM to the file system, as follows:

        ADMINISTER KEY MANAGEMENT MERGE KEYSTORE source_TDE_wallet_path
        IDENTIFIED BY source_TDE_wallet_password
        INTO EXISTING KEYSTORE target_TDE_wallet_path
        IDENTIFIED BY target_TDE_wallet_password
        WITH BACKUP USING backupIdentifier;

    In this specification:

    - `source_TDE_wallet_path` is the directory path to the source TDE wallet.

    - `source_TDE_wallet_password` is th source TDE wallet password.

    - `target_TDE_wallet_path` is the path to the target TDE wallet.

    - `target_TDE_wallet_password` is the target TDE wallet password.

    - `backupIdentifier` is the backup identifier to be added to the backup file name.

    For example:

        ADMINISTER KEY MANAGEMENT MERGE KEYSTORE '+DATAFILE'
        IDENTIFIED BY "source_TDE_wallet_password"
        INTO EXISTING KEYSTORE '/etc/ORACLE/KEYSTORE/DB1/'
        IDENTIFIED BY "target_TDE_wallet_password"
        WITH BACKUP USING "bkup";

**Parent topic:** Managing the Keystore

#### 5.1.11 Migrating from a TDE Wallet to Oracle Key Vault

You can migrate between password-protected TDE wallets and external keystores in Oracle Key Vault.

- Migrating from a Password-Protected TDE Wallet to an External Keystore
  You can migrate from a password-protected TDE wallet to an external keystore.
- Migrating from an External Keystore to a Password-Based TDE Wallet
  You can migrate an external keystore to a TDE wallet.
- Keystore Order After a Migration
  After you perform a migration, keystores can be either primary or secondary in their order.

**Parent topic:** Managing the Keystore

##### 5.1.11.1 Migrating from a Password-Protected TDE Wallet to an External Keystore

You can migrate from a password-protected TDE wallet to an external keystore.

- Step 1: Convert the TDE Wallet to Open with the External Keystore
  Some Oracle tools require access to the old TDE wallet to encrypt or decrypt data that was exported or backed up using the TDE wallet.
- Step 2: Configure the External Keystore Type
  You can use the `ALTER SYSTEM` statement to configure the external keystore type.
- Step 3: Perform the External Keystore Migration
  You can use the `ADMINISTER KEY MANAGEMENT` SQL statement to perform an external keystore migration.

**Parent topic:** Migrating from a TDE Wallet to Oracle Key Vault

###### 5.1.11.1.1 Step 1: Convert the TDE Wallet to Open with the External Keystore

Some Oracle tools require access to the old TDE wallet to encrypt or decrypt data that was exported or backed up using the TDE wallet.

Examples of these tools are Oracle Data Pump and Oracle Recovery Manager.

- Use the `ADMINISTER KEY MANAGEMENT` SQL statement to convert a TDE wallet to open with an external keystore.
  - To set the TDE wallet password as that of the external keystore, use the following syntax:

        ADMINISTER KEY MANAGEMENT ALTER KEYSTORE PASSWORD
        FORCE KEYSTORE
        IDENTIFIED BY TDE_wallet_password
        SET "external_key_manager_password" WITH BACKUP
        [USING 'backup_identifier'];

    In this specification:

    - `TDE_wallet_password` is the same password that you used when creating the TDE wallet.

    - `external_key_manager_password` is the new TDE wallet password which is the same as the password of the external keystore.

    - `WITH BACKUP` creates a backup of the TDE wallet. Optionally, you can use the `USING` clause to add a brief description of the backup. Enclose this description in single quotation marks (`' '`). This identifier is appended to the named TDE wallet file (for example, `ewallet_``time-stamp``_emp_key_backup``.p12`, with `emp_key_backup` being the backup identifier). Follow the file naming conventions that your operating system uses.

  - To create an auto-login TDE wallet for a TDE wallet, use the following syntax:

        ADMINISTER KEY MANAGEMENT CREATE [LOCAL] AUTO_LOGIN KEYSTORE
        FROM KEYSTORE 'keystore_location'
        IDENTIFIED BY TDE_wallet_password;

    In this specification:

    - `LOCAL` enables you to create a local auto-login TDE wallet. Otherwise, omit this clause if you want the TDE wallet to be accessible by other computers.

    - `TDE_wallet_location` is the path to the TDE wallet directory location of the wallet that is configured in the `sqlnet.ora` file.

    - `TDE_wallet_password` is the existing password of the configured TDE wallet.

**Parent topic:** Migrating from a Password-Protected TDE Wallet to an External Keystore

###### 5.1.11.1.2 Step 2: Configure the External Keystore Type

You can use the `ALTER SYSTEM` statement to configure the external keystore type.

For the TDE wallet to open with the external keystore, either the TDE wallet must have the same password as the external keystore, or alternatively, you can create an auto-login TDE wallet for the TDE wallet.

1.  Connect to the united mode CDB root or isolated mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Set the `TDE_CONFIGURATION` dynamic initialization parameter.
    This example migrates the database from a TDE wallet to Oracle Key Vault.

        ALTER SYSTEM SET TDE_CONFIGURATION="KEYSTORE_CONFIGURATION=OKV|FILE" SCOPE = "BOTH" SID = "*";

**Parent topic:** Migrating from a Password-Protected TDE Wallet to an External Keystore

###### 5.1.11.1.3 Step 3: Perform the External Keystore Migration

You can use the `ADMINISTER KEY MANAGEMENT` SQL statement to perform an external keystore migration.

To migrate from the TDE wallet to external keystore, you must use the `MIGRATE USING` `external_key_manager_password` clause in the `ADMINISTER KEY MANAGEMENT SET KEY` SQL statement to decrypt the existing TDE table keys and tablespace encryption keys with the TDE master encryption key in the TDE wallet and then reencrypt them with the newly created TDE master encryption key in the external keystore. After you complete the migration, you do not need to restart the database, nor do you need to manually re-open the external keystore. The migration process automatically reloads the keystore keys in memory.

- Migrate the external keystores by using the following syntax:
      ADMINISTER KEY MANAGEMENT SET ENCRYPTION KEY
      IDENTIFIED BY "external_key_manager_password"
      MIGRATE USING TDE_wallet_password
      [WITH BACKUP [USING 'backup_identifier']];

  In this specification:

  - `external_key_manager_password` is the password that was created when the external keystore was created. Enclose this setting in double quotation marks (`" "`).

  - `TDE_wallet_password` is the same password that you used when you created the TDE wallet or that you have changed to (when converting a TDE wallet to open with an external keystore).

  - `USING` enables you to add a brief description of the backup. Enclose this description in single quotation marks (`' '`). This identifier is appended to the named keystore file (for example, `ewallet_``time-stamp``_``emp_key_backup``.p12`, with `emp_key_backup` being the backup identifier). Follow the file naming conventions that your operating system uses.

**Parent topic:** Migrating from a Password-Protected TDE Wallet to an External Keystore

##### 5.1.11.2 Migrating from an External Keystore to a Password-Based TDE Wallet

You can migrate an external keystore to a TDE wallet.

- About Migrating Back from an External Keystore
  To switch from using an external keystore solution to a TDE wallet, you can use reverse migration of the TDE wallet.
- Step 1: Configure the External Keystore Type
  You can use the `ALTER SYSTEM` statement to configure the external keystore type.
- Step 2: Configure the Keystore for the Reverse Migration
  The `ADMINISTER KEY MANAGEMENT` statement with the `SET ENCRYPTION KEY` and `REVERSE MIGRATE` clauses can be used to reverse the migration of a keystore.
- Step 3: Configure the External Keystore to Open with the TDE Wallet
  After you complete the migration, the migration process automatically reloads the keystore keys in memory.

**Parent topic:** Migrating from a TDE Wallet to Oracle Key Vault

###### 5.1.11.2.1 About Migrating Back from an External Keystore

To switch from using an external keystore solution to a TDE wallet, you can use reverse migration of the TDE wallet.

After you complete the switch, keep the external keystore, in case earlier backup files rely on the TDE master encryption keys in the external key manager.

If you had originally migrated from the TDE wallet to the external keystore and reconfigured the TDE wallet, then you already have an existing TDE wallet with the same password as the external keystore password. Reverse migration configures this keystore to act as the new TDE wallet with a new password. If your existing TDE wallet is an auto-login TDE wallet and you have the password-based TDE wallet for this auto-login TDE wallet, then use the password-based TDE wallet. If the password-based TDE wallet is not available, then merge the auto-login TDE wallet into a newly created empty password-based TDE wallet, and use the newly created password-based TDE wallet.

If you do not have an existing TDE wallet, then you must specify a TDE wallet location using the `WALLET_ROOT` parameter in the `init.ora` file. When you perform the reverse migration, migrate to the previous TDE wallet so that you do not lose the keys.

**Related Topics**

- Merging TDE Wallets
- [Migration of an Encrypted Database from a TDE Wallet to Oracle Key Vault or OCI KMS](managing-keystores-encryption-keys-in-united-mode.md)

**Parent topic:** Migrating from an External Keystore to a Password-Based TDE Wallet

###### 5.1.11.2.2 Step 1: Configure the External Keystore Type

You can use the `ALTER SYSTEM` statement to configure the external keystore type.

1.  Connect to the united mode CDB root or isolated mode PDB as a user who has been granted the `ALTER SYSTEM ` privilege.
2.  Set the `TDE_CONFIGURATION` dynamic initialization parameter to specify the TDE keystore type.
    For example:
        ALTER SYSTEM SET TDE_CONFIGURATION="KEYSTORE_CONFIGURATION=OKV" SCOPE = BOTH SID = '*';

    Setting `KEYSTORE_CONFIGURATION` to `"OKV"` indicates a configuration where the connection into Oracle Key Vault must be opened by providing the Oracle Key Vault password. To use an auto-open Oracle Key Vault configuration, you set `KEYSTORE_CONFIGURATION` to `"OKV|FILE"`, where the Oracle Key Vault password is stored in an auto-open keystore in `WALLET_ROOT``/tde`.
3.  Restart the database (for the CDB root) or close and re-open the PDB.
    To restart from the CDB root:

        SHUTDOWN IMMEDIATE
        STARTUP

    To close and re-open a PDB:

        ALTER PLUGGABLE DATABASE pdb_name CLOSE IMMEDIATE;
        ALTER PLUGGABLE DATABASE pdb_name OPEN;

**Parent topic:** Migrating from an External Keystore to a Password-Based TDE Wallet

###### 5.1.11.2.3 Step 2: Configure the Keystore for the Reverse Migration

The `ADMINISTER KEY MANAGEMENT` statement with the `SET ENCRYPTION KEY` and `REVERSE MIGRATE` clauses can be used to reverse the migration of a keystore.

1.  Connect to the united mode CDB root or isolated mode PDB as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Reverse migrate the keystore by using the following syntax:
        ADMINISTER KEY MANAGEMENT SET ENCRYPTION KEY
        IDENTIFIED BY TDE_wallet_password
        REVERSE MIGRATE USING "external_key_manager_password"
        [WITH BACKUP [USING 'backup_identifier']];

    In this specification:

    - `TDE_wallet_password` is the password for the existing keystore or the new keystore.

    - `external_key_manager_password` is the password that was created when you first created the external keystore. If the pre-external TDE wallet is the new keystore, then you must ensure that it has the same password as the `external_key_manager_password` before issuing the reverse migration command. Enclose this setting in double quotation marks (`" "`).

    - `WITH BACKUP` creates a backup of the TDE wallet. Optionally, you can include the `USING` clause to add a brief description of the backup. Enclose this description in single quotation marks (`' '`). This identifier is appended to the named keystore file (for example, `ewallet_``time-stamp``_``emp_key_backup``.p12`, with `emp_key_backup` being the backup identifier). Follow the file naming conventions that your operating system uses.

    For example:

        ADMINISTER KEY MANAGEMENT SET ENCRYPTION KEY
        IDENTIFIED BY TDE_wallet_password
        REVERSE MIGRATE USING "external_key_manager_password" WITH BACKUP;

        keystore altered.
3.  Optionally, change the keystore password.
    For example:
        ADMINISTER KEY MANAGEMENT ALTER KEYSTORE PASSWORD
        IDENTIFIED BY old_TDE_wallet_password
        SET new_TDE_wallet_password
        WITH BACKUP USING 'before_password_was_changed';

**Parent topic:** Migrating from an External Keystore to a Password-Based TDE Wallet

###### 5.1.11.2.4 Step 3: Configure the External Keystore to Open with the TDE Wallet

After you complete the migration, the migration process automatically reloads the keystore keys in memory.

You do not need to restart the database, nor do you need to manually re-open the TDE wallet.

The external keystore may still be required after reverse migration because the old keys are likely to have been used for Oracle Data Pump Export and Oracle Recovery Manager (Oracle RMAN)-encrypted backups. You should add the external keystore credentials to the keystore so that the HSM can be opened with the TDE wallet.

**Related Topics**

- Configuring Auto-Open Connections into External Key Managers

**Parent topic:** Migrating from an External Keystore to a Password-Based TDE Wallet

##### 5.1.11.3 Keystore Order After a Migration

After you perform a migration, keystores can be either primary or secondary in their order.

The `WALLET_ORDER` column of the `V$ENCRYPTION_WALLET` dynamic view describes whether a TDE wallet is primary (that is, it holds the current TDE master encryption key) or if it is secondary (it holds the previous TDE master encryption key). The `WRL_TYPE` column describes the type of locator for the TDE wallet (for example, `FILE` for the `sqlnet.ora` file). The `WALLET_ORDER` column shows `SINGLE` if two TDE wallets are not configured together and no migration was ever performed previously.

Table 5-1 describes how the keystore order works after you perform a migration.

Table 5-1 Keystore Order After a Migration

| Type of Migration Done                                        | WRL_TYPE        | WALLET_ORDER             | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
|:--------------------------------------------------------------|:----------------|:-------------------------|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Migration of TDE wallet to external keystore                  | `OKV`<br>`FILE` | `PRIMARY`<br>`SECONDARY` | Both the external and TDE wallet are configured. The TDE master encryption key can be either in Oracle Key Vault or the TDE wallet.<br>The TDE master encryption key is first searched in Oracle Key Vault.<br>If the TDE master encryption key is not in the primary keystore (Oracle Key Vault), then it will be searched for in the TDE wallet.<br>All of the new TDE master encryption keys will be created in the primary keystore (in this case, Oracle Key Vault).                              |
| Reverse migration from Oracle Key Vault (`HSM`) to TDE wallet | `FILE`<br>`HSM` | `PRIMARY`<br>`SECONDARY` | Both the external and TDE wallet are configured. The TDE master encryption key can be either in the external keystore or the TDE wallet.<br>The TDE master encryption key is first searched for in the TDE wallet.<br>If the TDE master encryption key is not present in the primary (that is, software) TDE wallet, then it will be searched for in the HSM's external keystore.<br>All of the new TDE master encryption keys will be created in the primary keystore (in this case, the TDE wallet). |

**Parent topic:** Migrating from a TDE Wallet to Oracle Key Vault

#### 5.1.12 Migration of Keystores to and from Oracle Key Vault

You can use Oracle Key Vault to migrate both TDE wallets and external keystores to and from Oracle Key Vault.

This enables you to manage the keystores centrally, and then share the keystores as necessary with other TDE-enabled databases in your enterprise.

Oracle Key Vault enables you to upload a keystore to a container called a virtual wallet, and then create a new virtual wallet from the contents of previously uploaded keystore. For example, suppose you previously uploaded a keystore that contains 5 keys. You can create a new virtual wallet that consists of only 3 of these keys. You then can download this keystore to another TDE-enabled database. This process does not modify the original keystore.

In addition to Oracle keystores, Oracle Key Vault enables you to securely share other security objects, such as credential files and Java keystores, across the enterprise. It prevents the loss of keys and keystores due to forgotten passwords or accidentally deleted keystores. You can use Oracle Key Vault with products other than TDE: Oracle Real Application Security, Oracle Active Data Guard, and Oracle GoldenGate. Oracle Key Vault facilitates the movement of encrypted data using Oracle Data Pump and Oracle Transportable Tablespaces.

**Related Topics**

- [Oracle Key Vault Administrator's Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/asoag&id=OKVAG10693)

**Parent topic:** Managing the Keystore

#### 5.1.13 Configuring Keystores for Automatic Storage Management

You can store a TDE wallet on an Automatic Storage Management (ASM) disk group.

- About Configuring Keystores for Automatic Storage Management
  You can configure a TDE wallet for Automatic Storage Management (ASM) for a standalone database or a multitenant environment. The `WALLET_ROOT` location can be compliant or non-compliant with Oracle Managed File (OMF) systems.
- Configuring a Keystore on a Standalone Database to Point to an ASM Location
  On a standalone database system, you can set the `WALLET_ROOT` parameter to point to an ASM location.
- Configuring a Keystore to Point to an ASM Location
  You can set `WALLET_ROOT` to point to an ASM directory within which the TDE wallet of the CDB root (which all united mode PDBs share) and the TDE wallets of all isolated mode PDBs are located.
- Configuring a Keystore to Point to an ASM Location When the WALLET_ROOT Location Does Not Follow OMF Guidelines
  If the chosen `WALLET_ROOT` location does not comply with the Oracle Managed File (OMF) guidelines, then the Oracle database cannot perform automation of the directory creation.

**Parent topic:** Managing the Keystore

##### 5.1.13.1 About Configuring Keystores for Automatic Storage Management

You can configure a TDE wallet for Automatic Storage Management (ASM) for a standalone database or a multitenant environment. The `WALLET_ROOT` location can be compliant or non-compliant with Oracle Managed File (OMF) systems.

You should use the `WALLET_ROOT` and `TDE_CONFIGURATION` initialization parameters to configure the TDE wallet location in an ASM system. The `TDE_CONFIGURATION` parameter must be set with the attribute `KEYSTORE_CONFIGURATION=FILE` in order for the `WALLET_ROOT` parameter to work. Note that starting with Oracle Database release 19c, the `ENCRYPTION_WALLET_LOCATION`, set in the `sqlnet.ora` file, is deprecated in favor of `WALLET_ROOT` and `TDE_CONFIGURATION`.

To perform the configuration, you must specify a `+` sign, followed by the ASM disk group and path where the TDE wallet will be located. For example:

    WALLET_ROOT=+disk_group/path

Note the following:

- When you open a local TDE wallet, it opens only on the ASM node on which it was created.
- When you designate the path for the `WALLET_ROOT` for databases in standalone or multitenant environments, or environments where the `WALLET_ROOT` location either complies or does not comply with the Oracle Managed File (OMF) directory naming convention, be aware that this path must follow certain conventions so that the database can automate the creation of the directory components of the TDE wallet locations for you. Otherwise, you must manually create the directories under the `WALLET_ROOT` location.
- If you must move or merge TDE wallets between a regular file system and an ASM file system, then you can use the same TDE wallet merge statements that are used to merge TDE wallets.
- To run commands to manage TDE wallets in an ASM environment, you can use the `ASMCMD` utility.

**Related Topics**

- Merging TDE Wallets
- [Oracle Automatic Storage Management Administrator's Guide](../ostmg/manage-asm-asmcmd.md)

**Parent topic:** Configuring Keystores for Automatic Storage Management

##### 5.1.13.2 Configuring a Keystore on a Standalone Database to Point to an ASM Location

On a standalone database system, you can set the `WALLET_ROOT` parameter to point to an ASM location.

1.  Ensure that the `KEYSTORE_CONFIGURATION` attribute of the `TDE_CONFIGURATION` dynamic initialization parameter is set to `FILE`.
    For example, in SQL\*Plus:
        ALTER SYSTEM SET TDE_CONFIGURATION="KEYSTORE_CONFIGURATION=FILE";
2.  In the `init.ora` file, set the `WALLET_ROOT` static initialization parameter to the ASM disk group location.
    Optionally, include `OMF` (in upper case) to provide Oracle Managed File (OMF) compliance and to facilitate automation of the directory creation.
    For example:
        WALLET_ROOT=+disk_group_name/OMF

    This setting places the TDE keystore of the standalone database system in the` ``WALLET_ROOT``/tde` directory (that is, `+``disk_group_name``/OMF/tde` with the `tde` component of the path being automatically created by the database server).

**Parent topic:** Configuring Keystores for Automatic Storage Management

##### 5.1.13.3 Configuring a Keystore to Point to an ASM Location

You can set `WALLET_ROOT` to point to an ASM directory within which the TDE wallet of the CDB root (which all united mode PDBs share) and the TDE wallets of all isolated mode PDBs are located.

1.  Ensure that the `KEYSTORE_CONFIGURATION` attribute of the `TDE_CONFIGURATION` dynamic initialization parameter is set to `FILE`.
    For a CDB, set `TDE_CONFIGURATION` in the CDB root; for an isolated PDB, set it in the PDB.
    For example, in SQL\*Plus:
        ALTER SYSTEM SET TDE_CONFIGURATION="KEYSTORE_CONFIGURATION=FILE";
2.  Set the `WALLET_ROOT` static initialization parameter to the ASM disk group location followed by the `DB_UNIQUE_NAME` initialization parameter value.
    The inclusion of the value of `DB_UNIQUE_NAME` is necessary to allow the database server to automate the creation of the necessary directories under this location.
    You must not use `OMF` as a directory component of the `WALLET_ROOT` location (unlike in the standalone database configuration section).
    For example:
        WALLET_ROOT=+disk_group_name/db_unique_name

    This setting locates the TDE wallet that is used by the root and by all of the united mode PDBs in the `WALLET_ROOT``/``db_unique_name``/tde` directory (that is, in `+``disk_group_name``/``db_unique_name``/tde`).

    This setting locates the TDE wallet which is used by each isolated mode PDB in the `WALLET_ROOT``/``db_unique_name``/``pdb_guid``/tde` directory (that is, in `+``disk_group_name``/``db_unique_name``/``pdb_guid``/tde`).

**Parent topic:** Configuring Keystores for Automatic Storage Management

##### 5.1.13.4 Configuring a Keystore to Point to an ASM Location When the WALLET_ROOT Location Does Not Follow OMF Guidelines

If the chosen `WALLET_ROOT` location does not comply with the Oracle Managed File (OMF) guidelines, then the Oracle database cannot perform automation of the directory creation.

In this case, you must use the `ALTER DISKGROUP` command to manually create the necessary directories under the `WALLET_ROOT` location. You must use the `ALTER DISKGROUP` ... `ADD DIRECTORY` statement to manually create the necessary directories, because no automation of the directory creation is possible when the `WALLET_ROOT` parameter is not using an OMF-compliant value.

1.  Ensure that the `KEYSTORE_CONFIGURATION` attribute of the `TDE_CONFIGURATION` dynamic initialization parameter is set to `FILE`.
    For example, in SQL\*Plus:
        ALTER SYSTEM SET TDE_CONFIGURATION="KEYSTORE_CONFIGURATION=FILE";
2.  In the `init.ora` file, set the `WALLET_ROOT` static initialization parameter to the ASM disk group location.
    For example, the following path after `disk_group_name` contains no uppercase OMF directory elements:
        WALLET_ROOT="+disk_group_name/mydir/wallets"
3.  Connect to the database instance using the `SYSASM` administrative privilege.
        connect / as sysasm
4.  Execute the `ALTER DISKGROUP` statements to create the necessary directories.
    You must perform this step because the database server cannot automate the creation of these directories, since the location chosen for `WALLET_ROOT` is not compliant with the Oracle Managed Files guideline (that is, it does not have the `OMF` component included in it in uppercase letters).
    For example:

        ALTER DISKGROUP "disk_group_name" ADD DIRECTORY
            '+disk_group_name/mydir/wallets/tde';

    For a multitenant environment, find the PDB GUID of the PDB that will store the keystore, as follows:

        SELECT GUID FROM DBA_PDBS WHERE PDB_NAME = 'pdb name';

    Next, include the PDB GUID in the following `ALTER DISKGROUP` statements to create the necessary directories for the isolated mode PDB within the `WALLET_ROOT` location. For example, assuming the GUID is `4756C705E52A8768E053F82DC40A5329`:

        ALTER DISKGROUP "disk_group_name" ADD DIRECTORY
            '+disk_group_name/mydir/wallets/4756C705E52A8768E053F82DC40A5329'

        ALTER DISKGROUP "disk_group_name" ADD DIRECTORY
            '+disk_group_name/mydir/wallets/4756C705E52A8768E053F82DC40A5329/tde';

**Parent topic:** Configuring Keystores for Automatic Storage Management

#### 5.1.14 Closing a Keystore

You can manually close software and external keystores.

- About Closing Keystores
  After you open a keystore, it remains open until you shut down the database instance.
- Closing a TDE Wallet
  You can manually close password-based TDE wallets, auto-login TDE wallets, and local auto-login TDE wallets.
- Closing an External Keystore
  To close an external keystore, you must use the `ADMINISTER KEY MANAGEMENT` statement with the `SET KEYSTORE CLOSE` clause.

**Parent topic:** Managing the Keystore

##### 5.1.14.1 About Closing Keystores

After you open a keystore, it remains open until you shut down the database instance.

When you restart the database instance, then auto-login and local auto-login TDE wallets automatically open when required (that is, when the TDE master encryption key must be accessed). However, TDE wallet password-based and external keystores do not automatically open. You must manually open them again before you can use them.

When you close a TDE wallet or an external keystore, you disable all of the encryption and decryption operations on the database. Hence, a database user or application cannot perform any operation involving encrypted data until the TDE wallet or keystore is reopened.

When you re-open a TDE wallet or keystore after closing it, its contents are reloaded back into the database. Thus, if the contents had been modified (such as during a migration), the database will have the latest contents.

You can check if a TDE wallet or keystore is closed by querying the `STATUS` column of the `V$ENCRYPTION_WALLET` view.

The following data operations will fail if the TDE wallet or keystore is not accessible:

- `SELECT` data from an encrypted column

- `INSERT` data into on an encrypted column

- `CREATE` a table with encrypted columns

- `CREATE` an encrypted tablespace

**Parent topic:** Closing a Keystore

##### 5.1.14.2 Closing a TDE Wallet

You can manually close password-based TDE wallets, auto-login TDE wallets, and local auto-login TDE wallets.

In the case of an auto-login TDE wallet, which opens automatically when it is accessed, manually close it if you moved it to a new location. You do this if you are changing your configuration from an auto-login TDE wallet to a password-based TDE wallet: you move out the auto-login TDE wallet, and then close the auto-login TDE wallet.

- Run the `ADMINISTER KEY MANAGEMENT` SQL statement.
  - For a password-based TDE wallet, use the following syntax:

        ADMINISTER KEY MANAGEMENT SET KEYSTORE CLOSE
        [IDENTIFIED BY [EXTERNAL STORE | TDE_wallet_password]];

    In this specification:

    - `IDENTIFIED BY` can be one of the following:

      - `EXTERNAL STORE` uses the TDE wallet password stored in the external store to perform the TDE wallet operation.

      - `TDE_wallet_password` is the password of the user who created the TDE wallet.

  - For an auto-login or local auto-login TDE wallet, use the following SQL statement:

        ADMINISTER KEY MANAGEMENT SET KEYSTORE CLOSE;

    You do not need to specify a password for this statement.

  Closing a TDE wallet disables all of the encryption and decryption operations. Any attempt to encrypt or decrypt data or access encrypted data results in an error.

**Parent topic:** Closing a Keystore

##### 5.1.14.3 Closing an External Keystore

To close an external keystore, you must use the `ADMINISTER KEY MANAGEMENT` statement with the `SET KEYSTORE CLOSE` clause.

1.  Log into the database instance as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Close the external keystore by using this syntax:
        ADMINISTER KEY MANAGEMENT SET KEYSTORE CLOSE
        IDENTIFIED BY [EXTERNAL STORE | "external_key_manager_password"];

    In this specification:

    - `IDENTIFIED BY` can be one of the following settings:

      - `EXTERNAL STORE` uses the keystore password stored in the external store to perform the keystore operation.

      - `external_key_manager_password` is for an external keystore manager, which can be Oracle Key Vault or OCI Vault - Key Management. Enclose this password in double quotation marks. For Oracle Key Vault, enter the password that was given during the Oracle Key Vault client installation. If at that time no password was given, then the password in the `ADMINISTER KEY MANAGEMENT` statement becomes `NULL`.

    For example:

        ADMINISTER KEY MANAGEMENT SET KEYSTORE CLOSE
        IDENTIFIED BY "external_key_manager_password";

**Parent topic:** Closing a Keystore

#### 5.1.15 Backup and Recovery of Encrypted Data

For TDE wallets, you cannot access encrypted data without the TDE master encryption key.

Because the TDE master encryption key is stored in the TDE wallet, you should periodically back up the TDE wallet in a secure location. You must back up a copy of the TDE wallet whenever you set a new TDE master encryption key or perform any operation that writes to the TDE wallet.

Do not back up the TDE wallet in the same location as the encrypted data. Back up the TDE wallet separately. This is especially true when you use the auto-login TDE wallet, which does not require a password to open. In case the backup tape is lost, a malicious user should not be able to get both the encrypted data and the TDE wallet.

Oracle Recovery Manager (Oracle RMAN) does not back up the TDE wallet as part of the database backup. When using a media manager such as Oracle Secure Backup with Oracle RMAN, Oracle Secure Backup automatically excludes auto-open TDE wallets (the `cwallet.sso` files). However, it does not automatically exclude encryption TDE wallets (the `ewallet.p12` files). It is a good practice to add the following `exclude` data set statement to your Oracle Secure Backup configuration:

    exclude name *.p12

This setting instructs Oracle Secure Backup to exclude the encryption TDE wallet from the backup set.

If you lose the TDE wallet that stores the TDE master encryption key, then you can restore access to encrypted data by copying the backed-up version of the TDE wallet to the appropriate location. If you archived the restored TDE wallet after the last time that you reset the TDE master encryption key, then you do not need to take any additional action.

If the restored TDE wallet does not contain the most recent TDE master encryption key, then you can recover old data up to the point when the TDE master encryption key was reset by rolling back the state of the database to that point in time. All of the modifications to encrypted columns after the TDE master encryption key was reset are lost.

**Related Topics**

- [Oracle Database Backup and Recovery User’s Guide](../bradv/rman-complete-database-recovery.md)

**Parent topic:** Managing the Keystore

#### 5.1.16 Dangers of Deleting Keystores

Oracle strongly recommends that you do not delete keystores.

If a keystore becomes overly full, any TDE master encryption key other than the currently active TDE master encryption key can be moved to a new keystore to reduce the overall size of the keystore, but it is important to keep a backup of the old and new keystores because even though the keys have been moved out of the currently active keystore, they may still be needed by other Oracle features, such as Oracle Recovery Manager backup operations. (See Related Topics at the end of this topic for a listing of features that are affected by deleted keystores.)

Deleting a keystore that still contains keys is particularly dangerous if you have configured Transparent Data Encryption and the keystore is in use. You can find if a keystore is in use by querying the `STATUS` column of the `V$ENCRYPTION_WALLET` view after you open the keystore. How you should proceed depends on whether you are using united mode or isolated mode.

- In isolated mode, if the `STATUS` column of the `V$ENCRYPTION_WALLET` is `OPEN_NO_MASTER_KEY`, then it is safe to archive and later delete the this keystore, because there are no keys in it.
- In united mode, you must execute the query of `V$ENCRYPTION_WALLET` from the `CDB$ROOT`, not the PDB. If you execute the query in a PDB that does not yet have a key set, then the `STATUS` is `OPEN_NO_MASTER_KEY`. However, this can be misleading, because a key could have been set in the `CDB$ROOT`. After you execute the query in the root and if the `STATUS` is `OPEN_NO_MASTER_KEY`, then you can safely archive and later delete the keystore.

The reason that you should be cautious when moving keys out of the currently-active TDE keystore is that this keystore may contain keys that are still needed by the database (even though the TDE master encryption key has been rekeyed). Deleting the keystore deletes these keys, and could result in the loss of encrypted data. Even if you decrypted all of the data in your database, you still should not delete the keystore, because doing so could still hamper the normal functioning of the Oracle database. This is because a TDE master encryption key in the keystore can also be required for other Oracle Database features. (See Related Topics at the end of this topic for a listing of features that are affected by deleted keystores.)

Even after you performed TDE keystore migration (which rekeys in such a way that the location of your currently-active TDE master encryption key changes place between your software keystore and your external keystore), you still should not delete your original keystore. The keys in the original keystore may be needed at a later time (for example, when you must recover an offline encrypted tablespace). Even if all online tablespaces are not encrypted, the key may still be in use.

The exception is in the case of software auto-login (or local auto-login) keystores. If you do not want to use this type of keystore, then ideally you should move it to a secure directory. Only delete an auto-login keystore if you are sure that it was created from a specific password-based keystore because an auto-login keystore is always based on an ordinary software keystore. The keystore should be available and known.

If you must delete a keystore, then do so with great caution. You must first move the keys within the keystore to a new keystore by using the `ADMINISTER KEY MANAGEMENT MOVE KEYS TO NEW KEYSTORE` statement.

**Related Topics**

- Features That Are Affected by Deleted Keystores
- Moving a TDE Master Encryption Key into a New Keystore
- [Moving a TDE Master Encryption Key into a New Keystore in United Mode](managing-keystores-encryption-keys-in-united-mode.md)
- [Moving a TDE Master Encryption Key into a New Keystore in Isolated Mode](managing-keystores-encryption-keys-in-isolated-mode.md)

**Parent topic:** Managing the Keystore

#### 5.1.17 Features That Are Affected by Deleted Keystores

Some features can be adversely affected if a keystore is deleted and a TDE master encryption key residing in that keystore is later needed.

Before you delete a keystore, consider the impact that the deletion will have in the event that you need the any TDE master encryption key in the TDE keystore at a later time. The following features and activities are affected:

- Offlined tablespace operations
- Oracle Secure Backup operations
- Media recovery and block media recovery operations
- Point-in-time recovery operations
- Physical and logical Oracle Data Guard standby operations
- Golden Gate operations
- Oracle Streams operations
- Oracle Recovery Manager operations, including restoring Oracle Recovery Manager backups
- Applying archived redo logs to a database during database crash recovery operations
- Database online block recovery. (Online block recovery implies that the database is still open. Deleting a wallet in an open database with encrypted tablespaces will cause additional problems other than those associated with online block recovery.) These problems can include the following:
  - Encrypted online data in encrypted tablespaces would no longer be decrypted. Encrypted metadata in the `SYSTEM`, `UNDO`, and `TEMP` tablespaces would no longer be decrypted. You will no longer have control over what metadata is encrypted or where that metadata can reside.
  - Buffered data or metadata needs to be encrypted before it can be written back to the disk, but if the wallet is deleted, then the buffered data or metadata would no longer be encrypted. This could cause redo generation to fail, and the DBWR background process would not be able to write the data, which would possibly lead to a database instance hang or crash.
  - After a database instance crash, the database instance recovery and database crash recovery would fail, leading to the database not being able to be restarted.

**Related Topics**

- Dangers of Deleting Keystores

**Parent topic:** Managing the Keystore

### 5.2 Managing the TDE Master Encryption Key

You can manage the TDE master encryption key in several ways.

- Creating User-Defined TDE Master Encryption Keys
  You can create a user-defined TDE master encryption key outside the database by generating a TDE master encryption key ID.
- Creating TDE Master Encryption Keys for Later Use
  You can create a TDE master encryption key that can be activated at a later date.
- Activating TDE Master Encryption Keys
  After you activate a TDE master encryption key, it can be used.
- TDE Master Encryption Key Attribute Management
  TDE master encryption key attributes store information about the TDE master encryption key.
- Creating Custom TDE Master Encryption Key Attributes for Reports
  Custom TDE master encryption key attributes enable you to defined attributes that are specific to your needs.
- Setting or Rekeying the TDE Master Encryption Key in the Keystore
  You can set or rekey the TDE master encryption key for both TDE wallets and external keystores.
- Exporting and Importing the TDE Master Encryption Key
  You can export and import the TDE master encryption key in different ways.
- Moving TDE Master Encryption Keys into a New Keystore
  You can move an existing TDE master encryption key into a new keystore from an existing password-protected keystore.
- Converting from ENCRYPTION_WALLET_LOCATION to WALLET_ROOT and TDE_CONFIGURATION
  You can convert the wallet location from using the `sqlnet.ora` `ENCRYPTION_WALLET_LOCATION` parameter to using the `WALLET_ROOT` and `TDE_CONFIGURATION` parameters instead.
- Management of TDE Master Encryption Keys Using Oracle Key Vault
  You can use Oracle Key Vault to manage and share TDE master encryption keys across an enterprise.

**Parent topic:** Managing the Keystore and the Master Encryption Key

#### 5.2.1 Creating User-Defined TDE Master Encryption Keys

You can create a user-defined TDE master encryption key outside the database by generating a TDE master encryption key ID.

- About User-Defined TDE Master Encryption Keys
  A TDE master encryption key that is outside the database has its own user-generated ID, which tracks the use of the TDE master encryption key.
- Creating a User-Defined TDE Master Encryption Key
  To create a user-defined TDE master encryption key, use the `ADMINISTER KEY MANAGEMENT` statement with the `SET | CREATE [ENCRYPTION] KEY` clause.

**Parent topic:** Managing the TDE Master Encryption Key

##### 5.2.1.1 About User-Defined TDE Master Encryption Keys

A TDE master encryption key that is outside the database has its own user-generated ID, which tracks the use of the TDE master encryption key.

You can use the `ADMINISTER KEY MANAGEMENT` to create and set user-defined TDE master encryption key IDs. After you generate the TDE master encryption key, you can bring this key into the database. Optionally, you can specify the TDE master encryption key ID in various `ADMINISTER KEY MANAGEMENT` statements.

This type of configuration benefits Oracle Fusion SaaS Cloud environments in that it enables you to generate a TDE master encryption key this complies with your site’s requirements. This key that you generate supports the current encryption algorithms and can be used for TDE wallets.

After you generate the TDE master encryption key ID, you can encrypt your data as you normally would.

The TDE master encryption key and its corresponding ID will not be captured by any auditing logs.

**Parent topic:** Creating User-Defined TDE Master Encryption Keys

##### 5.2.1.2 Creating a User-Defined TDE Master Encryption Key

To create a user-defined TDE master encryption key, use the `ADMINISTER KEY MANAGEMENT` statement with the `SET | CREATE [ENCRYPTION] KEY` clause.

1.  Log in to the database instance as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Create the user-defined TDE master encryption key by using the following syntax:
        ADMINISTER KEY MANAGEMENT SET | CREATE [ENCRYPTION] KEY
        '[mkid:mk | mk]'
        [USING ALGORITHM 'algorithm']
        [FORCE KEYSTORE]
        IDENTIFIED BY [EXTERNAL STORE | keystore_password]
        [WITH BACKUP [USING 'backup_identifier']];

    In this specification:

    - `SET | CREATE` : Enter `SET` if you want to create the master and activate the TDE master encryption key now, or select `CREATE` if you want to create the key for later use, without activating it yet.

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

    Set (create and use) this ARIA master key with the following `ADMINISTER KEY MANAGEMENT` statement.

    For example:

        ADMINISTER KEY MANAGEMENT SET ENCRYPTION KEY
        'f24ce8cdae39742b5da7293da206fbd05a28b1e44c4781f801768cfdc3dbb6e2'
        USING ALGORITHM 'ARIA256'
        FORCE KEYSTORE
        IIDENTIFIED BY EXTERNAL STORE | keystore_password
        WITH BACKUP [USING 'backup_identifier'];

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
            IDENTIFIED BY EXTERNAL STORE | software_keystore_password WITH BACKUP;

    4.  The database administrator can retrieve the BASE64 key-ID from the database with the following `SELECT` statement that creates the proper SQL command to activate the key and add a tag to it:

            SELECT ' ADMINISTER KEY MANAGEMENT USE KEY '''||KEY_ID||'''
            USING TAG '''||SYS_CONTEXT('USERENV', 'CON_NAME')||' '||TO_CHAR (SYS_EXTRACT_UTC (SYSTIMESTAMP),
            'YYYY-MM-DD HH24:MI:SS"Z"')||'''
            FORCE KEYSTORE
            DENTIFIED BY EXTERNAL STORE|software_keystore_password WITH BACKUP;

**Related Topics**

- [Supported Encryption and Integrity Algorithms](introduction-to-transparent-data-encryption.md)

**Parent topic:** Creating User-Defined TDE Master Encryption Keys

#### 5.2.2 Creating TDE Master Encryption Keys for Later Use

You can create a TDE master encryption key that can be activated at a later date.

- About Creating a TDE Master Encryption Key for Later Use
  The `CREATE KEY` clause of the `ADMINISTER KEY MANAGEMENT` statement can create a TDE master encryption key to be activated at a later date.
- Creating a TDE Master Encryption Key for Later Use
  A keystore must be opened before you can create a TDE master encryption key for use later on.
- Example: Creating a TDE Master Encryption Key in a Single Database
  You can use the `ADMINISTER KEY MANAGEMENT CREATE KEY USING TAG` statement to create a TDE master encryption key in a single database.

**Parent topic:** Managing the TDE Master Encryption Key

##### 5.2.2.1 About Creating a TDE Master Encryption Key for Later Use

The `CREATE KEY` clause of the `ADMINISTER KEY MANAGEMENT` statement can create a TDE master encryption key to be activated at a later date.

You then can activate this key on the same database or export it to another database and activate it there.

This method of TDE master encryption key creation is useful in a multitenant environment when you must re-create the TDE master encryption keys. The `CREATE KEY` clause enables you to use a single SQL statement to generate a new TDE master encryption key for all of the PDBs within a multitenant environment. The creation time of the new TDE master encryption key is later than the activation of the TDE master encryption key that is currently in use. Hence, the creation time can serve as a reminder to all of the PDBs to activate the most recently created TDE master encryption key as soon as possible.

**Parent topic:** Creating TDE Master Encryption Keys for Later Use

##### 5.2.2.2 Creating a TDE Master Encryption Key for Later Use

A keystore must be opened before you can create a TDE master encryption key for use later on.

1.  Log in to the database instance as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.

2.  Create the TDE master encryption key by using this syntax:

        ADMINISTER KEY MANAGEMENT CREATE KEY [USING TAG 'tag']
        [FORCE KEYSTORE]
        IDENTIFIED BY EXTERNAL STORE | keystore_password
        WITH BACKUP [USING 'backup_identifier'];

    In this specification:

    - `tag` is the associated attribute and information that you define. Enclose this setting in single quotation marks (' ').

    - `FORCE KEYSTORE` temporarily opens the password-protected TDE wallet for this operation. You must open the TDE wallet for this operation.

    - `IDENTIFIED BY` can be one of the following settings:

      - `EXTERNAL STORE` uses the keystore password stored in the external store to perform the keystore operation.

      - `keystore_password` is the mandatory keystore password that you used when you created the original keystore. It is case sensitive.

    - `WITH BACKUP` backs up the TDE master encryption key in the same location as the key, as identified by the `WRL_PARAMETER` column of the `V$ENCRYPTION_WALLET` view. To find the key locations for all of the database instances, query the `GV$ENCRYPTION_WALLET` view.

      You must back up password-based software keystores. You do not need to back up auto-login or local auto-login software keystores. Optionally, include the `USING` `backup_identifier` clause to add a description of the backup. Enclose `backup_identifier` in single quotation marks (`' '`).

3.  If necessary, activate the TDE master encryption key.

    1.  Fin the key ID.

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

- [Step 3: Open the TDE Wallet](configuring-transparent-data-encryption.md)
- [Opening an External Keystore](configuring-transparent-data-encryption.md)
- Activating TDE Master Encryption Keys

**Parent topic:** Creating TDE Master Encryption Keys for Later Use

##### 5.2.2.3 Example: Creating a TDE Master Encryption Key in a Single Database

You can use the `ADMINISTER KEY MANAGEMENT CREATE KEY USING TAG` statement to create a TDE master encryption key in a single database.

Example 5-1 shows how to create a TDE master encryption key in a single database. After you run this statement, a TDE master encryption key with the tag definition is created in the keystore for that database. You can query the `TAG` column of the `V$ENCRYPTION_KEYS` view for the identifier of the newly created key. You can query the `CREATION_TIME` column to find the most recently created key, which would be the key that you created from this statement. You can export this key to another database if you want or activate it locally later on, as described in Activating TDE Master Encryption Keys.

Example 5-1 Creating a TDE Master Encryption Key in a Single Database

    ADMINISTER KEY MANAGEMENT CREATE KEY USING TAG
    'source:admin@source;target:db1@target'
    IDENTIFIED BY password WITH BACKUP;

    keystore altered.

**Parent topic:** Creating TDE Master Encryption Keys for Later Use

#### 5.2.3 Activating TDE Master Encryption Keys

After you activate a TDE master encryption key, it can be used.

- About Activating TDE Master Encryption Keys
  You can activate a previously created or imported TDE master encryption key by using the `USE KEY` clause of `ADMINISTER KEY MANAGEMENT`.
- Activating a TDE Master Encryption Key
  To activate a TDE master encryption key, you must open the keystore and use `ADMINISTER KEY MANAGEMENT` with the `USE KEY` clause.
- Example: Activating a TDE Master Encryption Key
  You can use the ADMINISTER KEY MANAGEMENT SQL statement to activate a TDE master encryption key.

**Parent topic:** Managing the TDE Master Encryption Key

##### 5.2.3.1 About Activating TDE Master Encryption Keys

You can activate a previously created or imported TDE master encryption key by using the `USE KEY` clause of `ADMINISTER KEY MANAGEMENT`.

After you activate the master encryption key, it is used to encrypt all data encryption keys in your database. The key will be used to protect all of the column keys and all of the [tablespace encryption key](glossary.md)s. If you have deployed a logical standby database, then you must export the TDE master encryption keys after recreating them, and then import them into the standby database. You can have the TDE master encryption key in use on both the primary and the standby databases. To do so, you must activate the TDE master encryption key after you import it to the logical standby database.

**Parent topic:** Activating TDE Master Encryption Keys

##### 5.2.3.2 Activating a TDE Master Encryption Key

To activate a TDE master encryption key, you must open the keystore and use `ADMINISTER KEY MANAGEMENT` with the `USE KEY` clause.

1.  Log in to the database instance as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.

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

    - `key_identifier_from_V$ENCRYPTION_KEYS` is the key identifie. Enclose this setting in single quotation marks (`' '`).

    - `tag` is the associated attributes and information that you define. Enclose this setting in single quotation marks (`' '`).

    - `FORCE KEYSTORE` temporarily opens the password-protected TDE wallet for this operation. You must open the TDE wallet for this operation.

    - `IDENTIFIED BY` can be one of the following settings:

      - `EXTERNAL STORE` uses the keystore password stored in the external store to perform the keystore operation.

      - `keystore_password` is the mandatory keystore password that you used when you created the original keystore.

    - `WITH BACKUP` backs up the TDE master encryption key in the same location as the key, as identified by the `WRL_PARAMETER` column of the `V$ENCRYPTION_WALLET` view. To find the key locations for all of the database instances, query the `GV$ENCRYPTION_WALLET` view.

      You must back up password-based software keystores. You do not need to back up auto-login or local auto-login software keystores. Optionally, include the `USING` `backup_identifier` clause to add a description of the backup. Enclose `backup_identifier` in single quotation marks (`' '`).

**Related Topics**

- [Opening a TDE Wallet](configuring-transparent-data-encryption.md)
- [Opening an External Keystore](configuring-transparent-data-encryption.md)

**Parent topic:** Activating TDE Master Encryption Keys

##### 5.2.3.3 Example: Activating a TDE Master Encryption Key

You can use the ADMINISTER KEY MANAGEMENT SQL statement to activate a TDE master encryption key.

Example 5-2 shows how to activate a previously imported TDE master encryption key and then update its tag. This key is activated with the current database time stamp and time zone.

Example 5-2 Activating a TDE Master Encryption Key

    ADMINISTER KEY MANAGEMENT USE KEY
    'ARaHD762tUkkvyLgPzAi6hMAAAAAAAAAAAAAAAAAAAAAAAAAAAAA'
    USING TAG 'quarter:second;description:Activate Key on standby'
    IDENTIFIED BY password WITH BACKUP;

    keystore altered.

In this version of the same operation, the `FORCE KEYSTORE` clause is added in the event that the auto-login keystore is in use, or if the keystore is closed. The password of the keystore is stored externally, so the `EXTERNAL STORE` setting is used for the `IDENTIFIED BY` clause.

    ADMINISTER KEY MANAGEMENT USE KEY
    'ARaHD762tUkkvyLgPzAi6hMAAAAAAAAAAAAAAAAAAAAAAAAAAAAA'
    USING TAG 'quarter:second;description:Activate Key on standby'
    FORCE KEYSTORE IDENTIFIED BY EXTERNAL STORE WITH BACKUP;

    keystore altered.

**Parent topic:** Activating TDE Master Encryption Keys

#### 5.2.4 TDE Master Encryption Key Attribute Management

TDE master encryption key attributes store information about the TDE master encryption key.

- TDE Master Encryption Key Attributes
  TDE master encryption key attributes include detailed information about the TDE master encryption key.
- Finding the TDE Master Encryption Key That Is in Use
  A TDE master encryption key that is in use is the encryption key that was activated most recently for the database.

**Parent topic:** Managing the TDE Master Encryption Key

##### 5.2.4.1 TDE Master Encryption Key Attributes

TDE master encryption key attributes include detailed information about the TDE master encryption key.

The information contains the following types:

- Key time stamp information: Internal security policies and compliance policies usually determine the key rekeying frequency. You should expire keys when they reach the end of their lifetimes and then generate new keys. Time stamp attributes such as key creation time and activation time help you to determine the key age accurately, and automate key generation.

  The `V$ENCRYPTION_KEYS` view includes columns such as `CREATION_TIME` and `ACTIVATION_TIME.` See [Oracle Database Reference](../refrn/V-ENCRYPTION_KEYS.md) for a complete description of the `V$ENCRYPTION_KEYS` view.

- Key owner information: Key owner attributes help you to determine the user who created or activated the key. These attributes can be important for security, auditing, and tracking purposes. Key owner attributes also include key use information, such as whether the key is used for standalone TDE operations or used in a multitenant environment.

  The `V$ENCRYPTION_KEYS` view includes columns such as `CREATOR, CREATOR_ID, USER, USER_ID,` and `KEY_USE.`

- Key source information: Keys often must be moved between databases for operations such as import-export operations and Data Guard-related operations. Key source attributes enable you to track the origin of each key. You can track whether a key was created locally or imported, and the database name and instance number of the database that created the key. In a multitenant environment, you can track the PDB where the key was created.

  The `V$ENCRYPTION_KEYS` view includes columns such as `CREATOR_DBNAME, CREATOR_DBID, CREATOR_INSTANCE_NAME, CREATOR_INSTANCE_NUMBER, CREATOR_PDBNAME,` and so on.

- Key usage information: Key usage information determines the database or PDB where the key is being used. It also helps determine whether a key is in active use or not.

  The `V$ENCRYPTION_KEYS` view includes columns such as `ACTIVATING_DBNAME, ACTIVATING_DBID, ACTIVATING_INSTANCE_NAME, ACTIVATING_PDBNAME,` and so on.

- User-defined information and other information: When creating a key, you can tag it with information using the `TAG` option. Each key contains important information such as whether or not it has been backed up.

  The `V$ENCRYPTION_KEYS` view includes columns such as `KEY_ID, TAG,` and other miscellaneous columns, for example `BACKED_UP`.

**Note:**

TDE Master Key Attributes and Tag are only supported with Oracle Key Vault and Oracle Cloud Infrastructure (OCI) Key Management Service (KMS).

**Parent topic:** TDE Master Encryption Key Attribute Management

##### 5.2.4.2 Finding the TDE Master Encryption Key That Is in Use

A TDE master encryption key that is in use is the encryption key that was activated most recently for the database.

- To find the TDE master encryption key, query the `V$ENCRYPTION_KEYS` dynamic view.
  For example:
      SELECT KEY_ID
      FROM V$ENCRYPTION_KEYS
      WHERE ACTIVATION_TIME = (SELECT MAX(ACTIVATION_TIME)
                               FROM V$ENCRYPTION_KEYS
                               WHERE ACTIVATING_DBID = (SELECT DBID FROM V$DATABASE));

**Parent topic:** TDE Master Encryption Key Attribute Management

#### 5.2.5 Creating Custom TDE Master Encryption Key Attributes for Reports

Custom TDE master encryption key attributes enable you to defined attributes that are specific to your needs.

- About Creating Custom Attribute Tags
  Attribute tags enable you to monitor specific activities users perform, such as accessing a particular terminal ID.
- Creating a Custom Attribute Tag
  To create a custom attribute tag, you must use the `SET TAG` clause of the `ADMINISTER KEY MANAGEMENT` statement.

**Parent topic:** Managing the TDE Master Encryption Key

##### 5.2.5.1 About Creating Custom Attribute Tags

Attribute tags enable you to monitor specific activities users perform, such as accessing a particular terminal ID.

By default, Oracle Database defines a set of attributes that describe various characteristics of the TDE master encryption keys that you create, such as the creation time, database in which the TDE master encryption key is used, and so on. These attributes are captured by the `V$ENCRYPTION_KEY` dynamic view.

You can create custom attributes that can be captured by the `TAG` column of the `V$ENCRYPTION_KEYS` dynamic view. This enables you to define behaviors that you may want to monitor, such as users who perform activities on encryption keys. The tag can encompass multiple attributes, such as session IDs from a specific terminal.

After you create the tag for a TDE master encryption key, its name should appear in the `TAG` column of the `V$ENCRYPTION_KEYS` view for that TDE master encryption key. If you create a tag for the secret, then the tag appears in the `SECRET_TAG` column of the `V$CLIENT_SECRETS` view. If you create a secret with a tag, then the tag appears in the `SECRET_TAG` column of the `V$CLIENT_SECRETS` view.

**Parent topic:** Creating Custom TDE Master Encryption Key Attributes for Reports

##### 5.2.5.2 Creating a Custom Attribute Tag

To create a custom attribute tag, you must use the `SET TAG` clause of the `ADMINISTER KEY MANAGEMENT` statement.

1.  Log in to the database instance as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.

2.  If necessary, query the `TAG` column of the `V$ENCRYPTION_KEY` dynamic view to find a listing of existing tags for the TDE master encryption keys.

    When you create a new tag for a TDE master encryption key, it overwrites the existing tag for that TDE master encryption key.

3.  Create the custom attribute tag by using the following syntax:

        ADMINISTER KEY MANAGEMENT SET TAG 'tag'
        FOR 'master_key_identifier'
        [FORCE KEYSTORE]
        IDENTIFIED BY [EXTERNAL STORE | keystore_password]
        [WITH BACKUP [USING 'backup_identifier']];

    In this specification

    - `tag` is the associated attributes or information that you define. Enclose this information in single quotation marks (' ').

    - `master_key_identifier` identifies the TDE master encryption key for which the `tag` is set. To find a list of TDE master encryption key identifiers, query the `KEY_ID` column of the `V$ENCRYPTION_KEYS` dynamic view.

    - `FORCE KEYSTORE` temporarily opens the password-protected TDE wallet for this operation. You must open the TDE wallet for this operation.

    - `IDENTIFIED BY` can be one of the following settings:

      - `EXTERNAL STORE` uses the keystore password stored in the external store to perform the keystore operation.

      - `keystore_password` is the password that was used to create the keystore.

    - `backup_identifier` defines the tag values. Enclose this setting in single quotation marks (`' '`) and separate each value with a colon.

    For example, to create a tag that uses two values, one to capture a specific session ID and the second to capture a specific terminal ID:

        ADMINISTER KEY MANAGEMENT SET ENCRYPTION KEY
        USING TAG 'sessionid=3205062574:terminal=xcvt'
        IDENTIFIED BY keystore_password
        WITH BACKUP;

        keystore altered.

    Both the session ID (`3205062574`) and terminal ID (`xcvt`) can derive their values by using either the `SYS_CONTEXT` function with the `USERENV` namespace, or by using the `USERENV` function.

**Parent topic:** Creating Custom TDE Master Encryption Key Attributes for Reports

#### 5.2.6 Setting or Rekeying the TDE Master Encryption Key in the Keystore

You can set or rekey the TDE master encryption key for both TDE wallets and external keystores.

- About Setting or Rekeying the TDE Master Encryption Key in the Keystore
  You can set or rekey the TDE master encryption key for both software password-based and external keystores.
- Creating, Tagging, and Backing Up a TDE Master Encryption Key
  The `ADMINISTER KEY MANAGEMENT` statement enables you to create, tag, and back up a TDE master encryption key.
- About Rekeying the TDE Master Encryption Key
  Oracle Database uses a unified TDE Master Encryption Key for both TDE column encryption and TDE tablespace encryption.
- Rekeying the TDE Master Encryption Key
  You can use the `ADMINISTER KEY MANAGEMENT` statement to rekey a TDE master encryption key.
- Changing the TDE Master Encryption Key for a Tablespace
  You can use the `ENCRYPT` and `REKEY` clauses of the `ALTER TABLESPACE` statement to encrypt a tablespace.

**Parent topic:** Managing the TDE Master Encryption Key

##### 5.2.6.1 About Setting or Rekeying the TDE Master Encryption Key in the Keystore

You can set or rekey the TDE master encryption key for both software password-based and external keystores.

The TDE master encryption key is stored in an external security module (keystore), and it is used to protect the [TDE table key](glossary.md)s and [tablespace encryption key](glossary.md)s. By default, the TDE master encryption key is a system-generated random value created by Transparent Data Encryption (TDE).

Use the `ADMINISTER KEY MANAGEMENT` statement to set or reset (`REKEY`) the TDE master encryption key. When the master encryption key is set, then TDE is considered enabled and cannot be disabled.

Before you can encrypt or decrypt database columns or tablespaces, you must generate a TDE master encryption key. Oracle Database uses the same TDE master encryption key for both TDE column encryption and TDE tablespace encryption. The instructions for setting a software or hardware TDE master encryption key explain how to generate a tDE master encryption key.

**Related Topics**

- [Step 4: Set the TDE Master Encryption Key in the TDE Wallet](configuring-transparent-data-encryption.md)
- [Step 3: Set the TDE Master Encryption Key in Oracle Key Vault](managing-keystores-encryption-keys-in-united-mode.md)

**Parent topic:** Setting or Rekeying the TDE Master Encryption Key in the Keystore

##### 5.2.6.2 Creating, Tagging, and Backing Up a TDE Master Encryption Key

The `ADMINISTER KEY MANAGEMENT` statement enables you to create, tag, and back up a TDE master encryption key.

Oracle Database uses the keystore in the keystore location specified by the `WALLET_ROOT` parameter in the initialization parameter file to store the TDE master encryption key.

1.  Log in to the database instance as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
2.  Create and back up the TDE master encryption key, and apply a tag, by using the following syntax:
        ADMINISTER KEY MANAGEMENT SET ENCRYPTION KEY
        [USING TAG 'tag']
        [FORCE KEYSTORE]
        IDENTIFIED BY [EXTERNAL STORE | keystore_password]
        WITH BACKUP [USING 'backup_identifier'];

    In this specification:

    - `tag` is the tag that you want to create. Enclose this tag in single quotation marks (`' '`).

    - `FORCE KEYSTORE` temporarily opens the password-protected TDE wallet for this operation. You must open the TDE wallet for this operation.

    - `IDENTIFIED BY` can be one of the following settings:

      - `EXTERNAL STORE` uses the keystore password stored in the external store to perform the keystore operation.

      - `keystore_password` is either `software_keystore_password` or `external_key_manager_password`. As with software passwords, it is case sensitive. You must enclose the password string in double quotation marks (`" "`). Separate `user_name` and `password` with a colon (`:`).

    - `WITH BACKUP` backs the TDE master encryption key up in the same location as the key, as identified by the `WRL_PARAMETER` column of the `V$ENCRYPTION_WALLET` view. To find the `WRL_PARAMETER` values for all of the database instances, query the `GV$ENCRYPTION_WALLET` view.

      You must back up password-based TDE wallets. You do not need to use it for auto-login or local auto-login TDE wallets. Optionally, include the `USING` `backup_identifier` clause to add a description of the backup. Enclose this identifier in single quotation marks (`' '`).

    For example:

        ADMINISTER KEY MANAGEMENT SET ENCRYPTION KEY
        USING TAG 'backups"
        IDENTIFIED BY password
        WITH BACKUP USING 'hr.emp_key_backup';

        keystore altered.

**Related Topics**

- Creating Custom TDE Master Encryption Key Attributes for Reports

**Parent topic:** Setting or Rekeying the TDE Master Encryption Key in the Keystore

##### 5.2.6.3 About Rekeying the TDE Master Encryption Key

Oracle Database uses a unified TDE Master Encryption Key for both TDE column encryption and TDE tablespace encryption.

When you rekey the TDE master encryption key for TDE column encryption, the TDE Master Encryption Key for TDE tablespace encryption also is rekeyed. Rekey the TDE Master Encryption Key only if it was compromised or as per the security policies of the organization. This process deactivates the previous TDE master encryption key.

For better security and to meet compliance regulations, periodically rekey the TDE master encryption key. This process deactivates the previous TDE master encryption key, creates a new TDE master encryption key, and then activates it. You can check the keys that were created recently by querying the `CREATION_TIME` column in the `V$ENCRYPTION_KEYS` view. To find the keys that were activated recently, query the `ACTIVATION_TIME` column in the `V$ENCRYPTION_KEYS` view.

You cannot change the TDE master encryption key or rekey a TDE master encryption key for an auto-login keystore. Because auto-login keystores do not have a password, an administrator or a privileged user can change the keys without the knowledge of the security officer. However, if both the auto-login and the password-based keystores are present in the configured location (as set in the `sqlnet.ora` file), then when you rekey the TDE master encryption key, a TDE master encryption key is added to both the auto-login and password-based keystores. If the auto-login keystore is in use in a location that is different from that of the password-based keystore, then you must re-create the auto-login keystore.

Do not perform a rekey operation of the master key concurrently with an online tablespace rekey operation. You can find if an online tablespace is in the process of being TDE Master Encryption Keyed by issuing the following query:

    SELECT TS#,ENCRYPTIONALG,STATUS FROM V$ENCRYPTED_TABLESPACES;

A status of `REKEYING` means that the corresponding tablespace is still being rekeyed.

**Note:**

You cannot add new information to auto-login keystores separately.

**Parent topic:** Setting or Rekeying the TDE Master Encryption Key in the Keystore

##### 5.2.6.4 Rekeying the TDE Master Encryption Key

You can use the `ADMINISTER KEY MANAGEMENT` statement to rekey a TDE master encryption key.

1.  Log in to the database instance as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
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

      - `keystore_password` is the mandatory keystore password that you created when you created the keystore in [Step 2: Create the TDE Wallet](configuring-transparent-data-encryption.md).

    - `WITH BACKUP` creates a backup of the keystore. You must use this option for password-based and external keystores. Optionally, you can use the `USING` clause to add a brief description of the backup. Enclose this description in single quotation marks (`' '`). This identifier is appended to the named keystore file (for example, `ewallet_``time-stamp``_emp_key_backup.p12`). Follow the file naming conventions that your operating system uses.

    For example:

        ADMINISTER KEY MANAGEMENT SET KEY
        FORCE KEYSTORE
        IDENTIFIED BY keystore_password
        WITH BACKUP USING 'emp_key_backup';

        keystore altered.

**Related Topics**

- [Step 3: Open the TDE Wallet](configuring-transparent-data-encryption.md)
- [Step 2: Open the Connection to Oracle Key Vault](managing-keystores-encryption-keys-in-united-mode.md)

**Parent topic:** Setting or Rekeying the TDE Master Encryption Key in the Keystore

##### 5.2.6.5 Changing the TDE Master Encryption Key for a Tablespace

You can use the `ENCRYPT` and `REKEY` clauses of the `ALTER TABLESPACE` statement to encrypt a tablespace.

1.  Ensure that the tablespace open in read-write mode.
    You can query the `STATUS` column of the `V$INSTANCE` dynamic view to find if a database is open and the `OPEN_MODE` column of the `V$DATABASE` view to find if it in read-write mode.
2.  If necessary, open the database in read-write mode.
        ALTER DATABASE OPEN READ WRITE;
3.  Run the `ALTER TABLESPACE` SQL statement to encrypt the tablespace.
    If the tablespace has not yet been encrypted, then use the `ENCRYPT` clause:

        ALTER TABLESPACE encrypt_ts ENCRYPTION USING 'AES256' ENCRYPT;

    To change the encryption of the `SYSTEM`, `SYSAUX`, or `UNDO` tablespace, you must rekey the tablespace online. Use the `ONLINE` and `REKEY` clauses. For example, to change the encryption algorithm of the `SYSTEM` tablespace:

        ALTER TABLESPACE SYSTEM ENCRYPTION ONLINE USING 'AES256' REKEY;

**Related Topics**

- [About Encryption Conversions for Existing Online Tablespaces](configuring-transparent-data-encryption.md)

**Parent topic:** Setting or Rekeying the TDE Master Encryption Key in the Keystore

#### 5.2.7 Exporting and Importing the TDE Master Encryption Key

You can export and import the TDE master encryption key in different ways.

- About Exporting and Importing the TDE Master Encryption Key
  Oracle Database features such as transportable tablespaces and Oracle Data Pump move data that is possibly encrypted between databases.
- About Exporting TDE Master Encryption Keys
  You can use `ADMINISTER KEY MANAGEMENT EXPORT` to export TDE master encryption keys from a keystore, and then import them into another keystore.
- Exporting a TDE Master Encryption Key
  The `ADMINISTER KEY MANAGEMENT` statement with the `EXPORT [ENCRYPTION] KEYS WITH SECRET` clause exports a TDE master encryption key.
- Example: Exporting a TDE Master Encryption Key by Using a Subquery
  The `ADMINISTER KEY MANAGEMENT EXPORT ENCRYPTION KEYS` statement can export a TDE master encryption key by using a subquery.
- Example: Exporting a List of TDE Master Encryption Key Identifiers to a File
  The `ADMINISTER KEY MANAGEMENT EXPORT ENCRYPTION KEYS WITH SECRET` statement can export a list of TDE master encryption key identifiers to a file.
- Example: Exporting All TDE Master Encryption Keys of the Database
  The `ADMINISTER KEY MANAGEMENT EXPORT ENCRYPTION KEYS` SQL statement can export all TDE master encryption keys of a database.
- About Importing TDE Master Encryption Keys
  The `ADMINISTER KEY MANAGEMENT IMPORT` statement can import exported TDE master encryption keys from a key export file into a target keystore.
- Importing a TDE Master Encryption Key
  The `ADMINISTER KEY MANAGEMENT` statement with the `IMPORT [ENCRYPTION] KEYS WITH SECRET` clause can import a TDE master encryption key.
- Example: Importing a TDE Master Encryption Key
  You can use the ADMINISTER KEY MANAGEMENT IMPORT KEYS SQL statement to import a TDE master encryption key.
- How Keystore Merge Differs from TDE Master Encryption Key Export or Import
  The keystore merge operation differs from the TDE master encryption key export and import operations.

**Parent topic:** Managing the TDE Master Encryption Key

##### 5.2.7.1 About Exporting and Importing the TDE Master Encryption Key

Oracle Database features such as transportable tablespaces and Oracle Data Pump move data that is possibly encrypted between databases.

These are some common scenarios in which you can choose to export and import TDE master encryption keys to move them between source and target keystores. For Data Guard (Logical Standby), you must copy the keystore that is in the primary database to the standby database. Instead of merging the primary database keystore with the standby database, you can export the TDE master encryption key that is in use and then import it to the standby database. Moving transportable tablespaces that are encrypted between databases requires that you export the TDE master encryption key at the source database and then import it into the target database.

**Parent topic:** Exporting and Importing the TDE Master Encryption Key

##### 5.2.7.2 About Exporting TDE Master Encryption Keys

You can use `ADMINISTER KEY MANAGEMENT EXPORT` to export TDE master encryption keys from a keystore, and then import them into another keystore.

A TDE master encryption key is exported together with its key identifier and key attributes. The exported keys are protected with a password (secret) in the export file.

You can specify the TDE master encryption keys to be exported by using the `WITH IDENTIFIER` clause of the `ADMINSITER KEY MANAGENT EXPORT` statement. To export the TDE master encryption keys, you can either specify their key identifiers as a comma-separated list, or you can specify a query that enumerates their key identifiers. Be aware that Oracle Database executes the query determining the key identifiers within the current user's rights and not with definer's rights.

If you omit the `WITH IDENTIFER` clause, then all of the TDE master encryption keys of the database are exported.

**Related Topics**

- [Exporting and Importing Master Encryption Keys for a PDB in Isolated Mode](managing-keystores-encryption-keys-in-isolated-mode.md)

**Parent topic:** Exporting and Importing the TDE Master Encryption Key

##### 5.2.7.3 Exporting a TDE Master Encryption Key

The `ADMINISTER KEY MANAGEMENT` statement with the `EXPORT [ENCRYPTION] KEYS WITH SECRET` clause exports a TDE master encryption key.

1.  Log in to the database instance as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.

2.  Export the TDE master encryption keys by using the following syntax:

        ADMINISTER KEY MANAGEMENT EXPORT [ENCRYPTION] KEYS
        WITH SECRET "export_secret"
        TO 'file_path'
        [FORCE KEYSTORE]
        IDENTIFIED BY [EXTERNAL STORE | keystore_password]
        [WITH IDENTIFIER IN 'key_id1', 'key_id2', 'key_idn' | (SQL_query)];

    In this specification:

    - `export_secret` is a password that you can specify to encrypt the export the file that contains the exported keys. Enclose this secret in double quotation marks (" "), or you can omit the quotation marks if the secret has no spaces.

    - `file_path` is the complete path and name of the file to which the keys must be exported. Enclose this path in single quotation marks (`' ')`. You can export to regular file systems only.

    - `FORCE KEYSTORE` temporarily opens the password-protected TDE wallet for this operation. You must open the TDE wallet for this operation.

    - `IDENTIFIED BY` can be one of the following settings:

      - `EXTERNAL STORE` uses the keystore password stored in the external store to perform the keystore operation.

      - `TDE_wallet_password` is the password of the keystore containing the keys.

    - `key_id1`, `key_id2`, `key_idn` is a string of one or more TDE master encryption key identifiers for the TDE master encryption key being exported. Separate each key identifier with a comma and enclose each of these key identifiers in single quotation marks (`' '`). To find a list of TDE master encryption key identifiers, query the `KEY_ID` column of the `V$ENCRYPTION_KEYS` dynamic view.

    - `SQL_query` is a query that fetches a list of the TDE master encryption key identifiers. It should return only one column which contains the TDE master encryption key identifiers. This query is executed with current user rights.

**Related Topics**

- [Step 3: Open the TDE Wallet](configuring-transparent-data-encryption.md)

**Parent topic:** Exporting and Importing the TDE Master Encryption Key

##### 5.2.7.4 Example: Exporting a TDE Master Encryption Key by Using a Subquery

The `ADMINISTER KEY MANAGEMENT EXPORT ENCRYPTION KEYS` statement can export a TDE master encryption key by using a subquery.

Example 5-4 shows how to export TDE master encryption keys whose identifiers are fetched by a query to a file called `export.exp`. The TDE master encryption keys in the file are encrypted using the secret `my_secret`. The `SELECT` statement finds the identifiers for the TDE master encryption keys to be exported.

Example 5-3 Exporting a List of TDE Master Encryption Key Identifiers to a File

    ADMINISTER KEY MANAGEMENT EXPORT ENCRYPTION KEYS
    WITH SECRET "my_secret"
    TO '/TDE/export.exp'
    FORCE KEYSTORE
    IDENTIFIED BY password
    WITH IDENTIFIER IN 'AdoxnJ0uH08cv7xkz83ovwsAAAAAAAAAAAAAAAAAAAAAAAAAAAAA',
    'AW5z3CoyKE/yv3cNT5CWCXUAAAAAAAAAAAAAAAAAAAAAAAAAAAAA';

    keystore altered.

**Parent topic:** Exporting and Importing the TDE Master Encryption Key

##### 5.2.7.5 Example: Exporting a List of TDE Master Encryption Key Identifiers to a File

The `ADMINISTER KEY MANAGEMENT EXPORT ENCRYPTION KEYS WITH SECRET` statement can export a list of TDE master encryption key identifiers to a file.

Example 5-3 shows how to export TDE master encryption keys by specifying their identifiers as a list, to a file called `export.exp`. TDE master encryption keys in the file are encrypted using the secret `my_secret`. The identifiers of the TDE master encryption key to be exported are provided as a comma-separated list.

Example 5-4 Exporting TDE Master Encryption Key Identifiers by Using a Subquery

    ADMINISTER KEY MANAGEMENT EXPORT ENCRYPTION KEYS
    WITH SECRET "my_secret" TO '/etc/TDE/export.exp'
    FORCE KEYSTORE
    IDENTIFIED BY password
    WITH IDENTIFIER IN (SELECT KEY_ID FROM V$ENCRYPTION_KEYS WHERE ROWNUM <3);

    keystore altered.

**Parent topic:** Exporting and Importing the TDE Master Encryption Key

##### 5.2.7.6 Example: Exporting All TDE Master Encryption Keys of the Database

The `ADMINISTER KEY MANAGEMENT EXPORT ENCRYPTION KEYS` SQL statement can export all TDE master encryption keys of a database.

Example 5-5 shows how to export all of the TDE master encryption keys of the database to a file called `export.exp`. The TDE master encryption keys in the file are encrypted using the secret `my_secret`.

Example 5-5 Exporting All of the TDE Master Encryption Keys of the Database

    ADMINISTER KEY MANAGEMENT EXPORT ENCRYPTION KEYS
    WITH SECRET "my_secret" TO '/etc/TDE/export.exp'
    FORCE KEYSTORE
    IDENTIFIED BY password;

    keystore altered.

**Parent topic:** Exporting and Importing the TDE Master Encryption Key

##### 5.2.7.7 About Importing TDE Master Encryption Keys

The `ADMINISTER KEY MANAGEMENT IMPORT` statement can import exported TDE master encryption keys from a key export file into a target keystore.

You cannot re-import TDE master encryption keys that have already been imported.

**Related Topics**

- [Exporting and Importing Master Encryption Keys for a PDB in Isolated Mode](managing-keystores-encryption-keys-in-isolated-mode.md)

**Parent topic:** Exporting and Importing the TDE Master Encryption Key

##### 5.2.7.8 Importing a TDE Master Encryption Key

The `ADMINISTER KEY MANAGEMENT` statement with the `IMPORT [ENCRYPTION] KEYS WITH SECRET` clause can import a TDE master encryption key.

- Use the following syntax to import a TDE master encryption key:
      ADMINISTER KEY MANAGEMENT IMPORT [ENCRYPTION] KEYS
      WITH SECRET "import_secret"
      FROM 'file_name'
      [FORCE KEYSTORE]
      IDENTIFIED BY [EXTERNAL STORE | keystore_password]
      [WITH BACKUP [USING 'backup_identifier']];

  In this specification:

  - `import_secret` is the same password that was used to encrypt the keys during the export operation. Enclose this secret in double quotation marks (" "), or you can omit the quotation marks if the secret has no spaces.

  - `file_name` is the complete path and name of the file from which the keys need to be imported. Enclose this setting in single quotation marks (`' '`).

  - `FORCE KEYSTORE` temporarily opens the password-protected TDE wallet for this operation. You must open the TDE wallet for this operation.

  - `IDENTIFIED BY` can be one of the following settings:

    - `EXTERNAL STORE` uses the keystore password stored in the external store to perform the keystore operation.

    - `TDE_wallet_password` is the password of the TDE wallet where the keys are being imported.

  - `WITH BACKUP` must be used in case the target keystore was not backed up before the import operation. `backup_identifier` is an optional string that you can provide to identify the keystore backup. Enclose this setting in single quotation marks (`' '`).

**Parent topic:** Exporting and Importing the TDE Master Encryption Key

##### 5.2.7.9 Example: Importing a TDE Master Encryption Key

You can use the ADMINISTER KEY MANAGEMENT IMPORT KEYS SQL statement to import a TDE master encryption key.

Example 5-6 shows how to import the TDE master encryption key identifiers that are stored in the file `export.exp` and encrypted with the secret `my_secret`.

Example 5-6 Importing TDE Master Encryption Key Identifiers from an Export File

    ADMINISTER KEY MANAGEMENT IMPORT KEYS
    WITH SECRET "my_secret"
    FROM '/etc/TDE/export.exp'
    FORCE KEYSTORE
    IDENTIFIED BY password WITH BACKUP;

    keystore altered.

**Parent topic:** Exporting and Importing the TDE Master Encryption Key

##### 5.2.7.10 How Keystore Merge Differs from TDE Master Encryption Key Export or Import

The keystore merge operation differs from the TDE master encryption key export and import operations.

Even though both the `ADMINISTER KEY MANAGEMENT MERGE` statement and the `ADMINISTER KEY MANAGEMENT EXPORT` and `IMPORT` statements eventually move the TDE master encryption keys from one keystore to the next, there are differences in how these two statements function.

- The `MERGE` statement merges two keystores whereas the `EXPORT` and `IMPORT` statements export the keys to a file or import the keys from a file. The keystore is different from the export file, and the two cannot be used interchangeably. The export file is not a keystore and cannot be configured to be used with a database as a keystore. Similarly, the `IMPORT` statement cannot extract the TDE master encryption keys from the keystore.

- The `MERGE` statement merges all of the TDE master encryption keys of the specified keystores where as the `EXPORT` and `IMPORT` statements can be selective.

- The `EXPORT` and `IMPORT` statements require the user to provide both a location (`filepath`) and the file name of the export file, whereas the `MERGE` statement only takes in the location of the keystores.

- The file name of the keystores is fixed and is determined by the `MERGE` operation and can be either `ewallet.p12` or `cwallet.sso`. The file names for the export files used in the `EXPORT` the `IMPORT` statements are specified by the user.

- The keystores on Automatic Storage Management (ASM) disk groups or regular file systems can be merged with `MERGE` statements. The export files used in the `EXPORT` and the `IMPORT` statements can only be a regular operating system file and cannot be located on an ASM disk group.

- The keystores merged using the `MERGE` statement do not need to be configured or in use with the database. The `EXPORT` statement can only export the keys from a keystore that is configured and in use with the database and is also open when the export is done. The `IMPORT` statement can only import the keys into a keystore that is open, configured, and in use with the database.

- The `MERGE` statement never modifies the metadata associated with the TDE master encryption keys. The `EXPORT` and `IMPORT` operations can modify the metadata of the TDE master encryption keys when required, such as during a PDB plug operation.

**Parent topic:** Exporting and Importing the TDE Master Encryption Key

#### 5.2.8 Moving TDE Master Encryption Keys into a New Keystore

You can move an existing TDE master encryption key into a new keystore from an existing password-protected keystore.

- About Moving TDE Master Encryption Keys into a New Keystore
  You can move an unused (and safely archived) TDE master encryption key into a new keystore.
- Moving a TDE Master Encryption Key into a New Keystore
  The `ADMINISTER KEY MANAGEMENT MOVE KEYS` moves an existing TDE master encryption key into a new keystore from an existing keystore.

**Parent topic:** Managing the TDE Master Encryption Key

##### 5.2.8.1 About Moving TDE Master Encryption Keys into a New Keystore

You can move an unused (and safely archived) TDE master encryption key into a new keystore.

Use great caution when you decide to run `ADMINISTER KEY MANAGEMENT MOVE KEYS`. Even though this statement will not move an active master encryption key, it can still affect keys that are necessary for a range of database features. If you have deleted a key, then the data that was encrypted by that key is rendered permanently inaccessible (equivalent to deleting the data) for these features to be used. See Related Topics at the end of this topic for more information about features that are affected by deleted keystores.

Therefore, before you move the keystore, it is very important that you safely archive it. Delete the keystore only after a period of time has passed, to ensure that the keystore is no longer really useful.

To move a TDE master encryption key into a new keystore, you use the `ADMINISTER KEY MANAGEMENT MOVE KEYS` statement. This statement does not move the active TDE master encryption key (that is, the key that is currently in use at the time that `ADMINISTER KEY MANAGEMENT MOVE KEYS` is issued) because the database is currently using it.

If you mistakenly use the `ADMINISTER KEY MANAGEMENT MOVE KEYS` statement instead of `ADMINISTER KEY MANAGEMENT MERGE KEYSTORE` when you are configuring a new TDE keystore (for example, when you are changing the TDE keystore configuration from one where the TDE wallet is located in the operating system's file system to one where the TDE wallet is located in Oracle Automatic Storage Management (Oracle ASM)), then the following symptoms may help you to identify the TDE misconfiguration that was introduced by the use of the wrong key management command:

- When you open the TDE keystore that was the target of the earlier `ADMINISTER KEY MANAGEMENT MOVE KEYS` operation, an `ORA-28374: typed master key not found in wallet` error is seen, because the active TDE master encryption key was not moved to that keystore.
- The value shown in the `STATUS` column of the `V$ENCRYPTION_WALLET` view is `OPEN_NO_MASTER_KEY` after you open the new keystore. The `OPEN_NO_MASTER_KEY` status is expected, because the new TDE keystore that was mistakenly populated by means of the `ADMINISTER KEY MANAGEMENT MOVE KEYS` statement does not contain the active TDE master encryption key.

**Related Topics**

- Dangers of Deleting Keystores
- Features That Are Affected by Deleted Keystores

**Parent topic:** Moving TDE Master Encryption Keys into a New Keystore

##### 5.2.8.2 Moving a TDE Master Encryption Key into a New Keystore

The `ADMINISTER KEY MANAGEMENT MOVE KEYS` moves an existing TDE master encryption key into a new keystore from an existing keystore.

This feature enables you to delete unused keystores. Before you move the keystore, ensure that it is safely archived. After you move the encryption key to a new keystore, and when you are sure that the old keystore is no longer needed, you then can delete the old keystore.

1.  Log in to the database instance as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
    For example:
        sqlplus sec_admin as syskm
        Enter password: password
        Connected.
2.  Query the `KEY_ID` column of the `V$ENCRYPTION_KEYS` view to find the key identifier of the keys you want to move to the "key archival" keystore.
    For example:
        SELECT KEY_ID FROM V$ENCRYPTION_KEYS;

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
        { 'key_identifier' [, 'key_identifier' ]... | ( subquery ) } ]
        [WITH BACKUP [USING 'backup_identifier'] ];

    In this specification:

    - `keystore_location1` is the path to the `wallet` directory that will store the new keystore `.p12` file. By default, this directory is in `$ORACLE_BASE/admin/``db_unique_name``/wallet`.

    - `keystore1_password` is the password for the keystore from which the new keystore is moved.

    - `keystore_password` is the password for the keystore from which the key is moving.

    - `key_identifier` is the key identifier that you find from querying the `KEY_ID` column of the `V$ENCRYPTION_KEYS` view. Enclose this setting in single quotation marks (`' '`).

    - `subquery` can be used to find the exact key identifier that you want.

    - `backup_identifier` is an optional description of the backup. Enclose `backup_identifier` in single quotation marks (`' '`).

    For example:

        ADMINISTER KEY MANAGEMENT MOVE KEYS
        TO NEW KEYSTORE $ORACLE_BASE/admin/orcl/wallet
        IDENTIFIED BY keystore_password
        FROM FORCE KEYSTORE
        IDENTIFIED BY keystore_password
        WITH IDENTIFIER IN
        (SELECT KEY_ID FROM V$ENCRYPTION_KEYS WHERE ROWNUM < 2);
4.  To delete the old keystore, go to the `wallet` directory and then manually delete the `.p12` file containing the keystore.
    To find the location of the keystore, open the keystore, and then query the `WRL_PARAMETER` column of the `V$ENCRYPTION_WALLET` view.

**Related Topics**

- Dangers of Deleting Keystores
- Features That Are Affected by Deleted Keystores

**Parent topic:** Moving TDE Master Encryption Keys into a New Keystore

#### 5.2.9 Converting from ENCRYPTION_WALLET_LOCATION to WALLET_ROOT and TDE_CONFIGURATION

You can convert the wallet location from using the `sqlnet.ora` `ENCRYPTION_WALLET_LOCATION` parameter to using the `WALLET_ROOT` and `TDE_CONFIGURATION` parameters instead.

The conversion applies to either file systems or Oracle Automatic Storage Management (Oracle ASM) configurations. This procedure assumes that you have already set the `WALLET_ROOT` static initialization parameter and created a `WALLET_ROOT``/tde` directory.

1.  Copy all the wallets to the `WALLET_ROOT``/tde` directory.
2.  Restart the database.
3.  Back up the database.
4.  Connect to the CDB root as a user who has been granted the `ADMINISTER KEY MANAGEMENT` or `SYSKM` privilege.
5.  Set the `TDE_CONFIGURATION` dynamic initialization parameter to `FILE`.
        ALTER SYSTEM SET TDE_CONFIGURATION="KEYSTORE_CONFIGURATION=FILE" SCOPE = "BOTH" SID = "*";
6.  Rename the wallets from where you copied them.
7.  Remove the old `ENCRYPTION_WALLET_LOCATION` configuration setting from the `sqlnet.ora` file.

**Parent topic:** Managing the TDE Master Encryption Key

#### 5.2.10 Management of TDE Master Encryption Keys Using Oracle Key Vault

You can use Oracle Key Vault to manage and share TDE master encryption keys across an enterprise.

Oracle Key Vault securely stores the keys in a central repository, along with other security objects such as credential files and Java keystores, and enables you to share these objects with other TDE-enabled databases.

**Related Topics**

- Migration of Keystores to and from Oracle Key Vault
- [Oracle Key Vault Administrator's Guide](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/asoag&id=OKVAG10693)

**Parent topic:** Managing the TDE Master Encryption Key

### 5.3 Storing Oracle Database Secrets

Secrets are data that support internal Oracle Database features that integrate external clients such as Oracle GoldenGate into the database.

- About Storing Oracle Database Secrets in a Keystore
  Keystores can store secrets that support internal Oracle Database features and integrate external clients such as Oracle GoldenGate.
- Storage of Oracle Database Secrets in a Software Keystore
  The `ADMINISTER KEY MANAGEMENT ADD SECRET|UPDATE SECRET|DELETE SECRET` statements can add secrets, update secrets, and delete secrets from a keystore.
- Example: Adding an Oracle Key Vault Password to a Software Keystore
  The `ADMINISTER KEY MANAGEMENT ADD SECRET` statement can add an Oracle Key Vault password to a software keystore.
- Example: Changing an Oracle Key Vault Password Stored as a Secret in a Software Keystore
  The `ADMINISTER KEY MANAGEMENT UPDATE SECRET` statement can change an Oracle Key Vault password that is stored as a secret in a software keystore.
- Example: Deleting an Oracle Key Vault Password Stored as a Secret in a Software Keystore
  The `ADMINISTER KEY MANAGEMENT DELETE SECRET` statement can delete Oracle Key Vault passwords that are stored as secrets in a software keystore.
- Storage of Oracle Database Secrets in an External Keystore
  The `ADMINISTER KEY MANAGEMENT ADD SECRET|UPDATE SECRET|DELETE SECRET` statements can add, update, and delete secrets.
- Example: Adding an Oracle Database Secret to an External Keystore
  The `ADMINISTER KEY MANAGEMENT ADD SECRET` statement can add an Oracle Database secret to an external keystore.
- Example: Changing an Oracle Database Secret in an External Keystore
  The `ADMINISTER KEY MANAGEMENT MANAGEMENT UPDATE SECRET` statement can change an Oracle Database secret in an external keystore.
- Example: Deleting an Oracle Database Secret in an External Keystore
  The `ADMINISTER KEY MANAGEMENT DELETE SECRET FOR CLIENT` statement can delete an Oracle Database secret that is in an external keystore.
- Configuring Auto-Open Connections into External Key Managers
  An external key manager can be configured to use the auto-login capability.

**Parent topic:** Managing the Keystore and the Master Encryption Key

#### 5.3.1 About Storing Oracle Database Secrets in a Keystore

Keystores can store secrets that support internal Oracle Database features and integrate external clients such as Oracle GoldenGate.

The secret key must be a string adhering to Oracle identifier rules. You can add, update, or delete a client secret in an existing keystore. The Oracle GoldenGate Extract process must have data encryption keys to decrypt the data that is in data files and in `REDO` or `UNDO` logs. Keys are encrypted with shared secrets when you share the keys between an Oracle database and an Oracle GoldenGate client. The software keystore stores the shared secrets.

Depending on your site's requirements, you may require automated open keystore operations even when an external keystore is configured. For this reason, the external key manager password can be stored in a software auto-login keystore, which enables the auto-login capability for the external keystore. The Oracle Database side can also store the credentials for the database to log in to an external storage server in the software keystore.

You can store Oracle Database secrets in both software keystores and external keystores:

- Software keystores: You can store secrets in software password-based, auto-login, and local auto-login software keystores. If you want to store secrets in an auto-login (or auto-login local) keystore, then note the following:

  - If the software auto-login keystore is in the same location as its corresponding password-based software keystore, then the secrets are added automatically.

  - If the software auto-login keystore is in a different location from its corresponding password-based software keystore, then you must create the auto-login keystore again from the password-based keystore, and keep the two keystores in synchronization.

- External keystores: You can store secrets in standard external key managers.

**Related Topics**

- Storage of Oracle Database Secrets in an External Keystore
- Configuring Auto-Open Connections into External Key Managers

**Parent topic:** Storing Oracle Database Secrets

#### 5.3.2 Storage of Oracle Database Secrets in a Software Keystore

The `ADMINISTER KEY MANAGEMENT ADD SECRET|UPDATE SECRET|DELETE SECRET` statements can add secrets, update secrets, and delete secrets from a keystore.

As with all of the `ADMINISTER KEY MANAGEMENT` statements, you must have the `ADMINISTER KEY MANAGEMENT` or the `SYSKM` administrative privilege. To find information about existing secrets, you can query the `V$CLIENT_SECRETS` dynamic view.

- Adding a secret: Use the following syntax:

      ADMINISTER KEY MANAGEMENT
      ADD SECRET 'secret' FOR CLIENT 'client_identifier'
      [USING TAG 'tag']
      [TO [[LOCAL] AUTO_LOGIN] KEYSTORE keystore_location
      [FORCE KEYSTORE]
      IDENTIFIED BY [EXTERNAL STORE | keystore_password]
      [WITH BACKUP [USING backup_id];

- Updating a secret: Use the following syntax:

      ADMINISTER KEY MANAGEMENT
      UPDATE SECRET 'secret' FOR CLIENT 'client_identifier'
      [USING TAG 'tag']
       [TO [[LOCAL] AUTO_LOGIN] KEYSTORE keystore_location
      [FORCE KEYSTORE]
      IDENTIFIED BY [EXTERNAL STORE | keystore_password]
      [WITH BACKUP [USING backup_id];

- Deleting a secret: Use the following syntax:

      ADMINISTER KEY MANAGEMENT
      DELETE SECRET FOR CLIENT 'client_identifier'
      [FROM [[LOCAL] AUTO_LOGIN] KEYSTORE keystore_location
      [FORCE KEYSTORE]
      IDENTIFIED BY [EXTERNAL STORE | keystore_password]
      [WITH BACKUP [USING backup_id];

In all of these statements, the specification is as follows:

- `secret` is the client secret key to be stored, updated, or deleted. Enclose this setting in single quotation marks (`' '`) or omit the quotation marks if the secret has no spaces. To find information about existing secrets and their client identifiers, query the `V$CLIENT_SECRETS` dynamic view.

- `client_identifier` is an alphanumeric string used to identify the secret key. `client_identifier` does not have a default value. Enclose this setting in single quotation marks (`' '`).

- `TO [[LOCAL] AUTO_LOGIN] KEYSTORE` refers to the location of an auto-login keystore, which is specified in the `sqlnet.ora` file.

- `tag` is an optional, user-defined description for the secret key to be stored. You can use `tag` with the `ADD` and `UPDATE` operations. Enclose this setting in single quotation marks (`' '`). This tag appears in the `SECRET_TAG` column of the `V$CLIENT_SECRETS` view.

  `WITH BACKUP` is required in case the keystore was not backed up before the `ADD`, `UPDATE`, or `DELETE` operation. `backup_identifier` is an optional user-defined description for the backup. Enclose `backup_identifier` in single quotation marks (`' '`).

- `[TO | FROM [[LOCAL] AUTOLLOGIN] KEYSTORE` specifies the location of the auto-login or password keystore, which is set in the s`qlnet.ora` file.

- `FORCE KEYSTORE` temporarily opens the password-protected TDE wallet for this operation if an auto-login TDE wallet is open (and in use) or if the TDE wallet is closed.

- `IDENTIFIED BY` can be one of the following settings:

  - `EXTERNAL STORE` uses the keystore password stored in the external store to perform the keystore operation.

  - `keystore_password` is the password for the keystore.

**Related Topics**

- Creating Custom TDE Master Encryption Key Attributes for Reports

**Parent topic:** Storing Oracle Database Secrets

#### 5.3.3 Example: Adding an Oracle Key Vault Password to a Software Keystore

The `ADMINISTER KEY MANAGEMENT ADD SECRET` statement can add an Oracle Key Vault password to a software keystore.

Example 5-7 shows how to add an Oracle Key Vault password as a secret into an existing software keystore (for example, after migrating to Oracle Key Vault, the Oracle Key Vault password can be added to the old TDE software keystore to set up an auto-open connection into Oracle Key Vault.

Example 5-7 Adding an Oracle Database Secret to a Software Keystore

    ADMINISTER KEY MANAGEMENT
    ADD SECRET 'external_key_manager_password' FOR CLIENT 'OKV_PASSWORD'
    IDENTIFIED BY software_keystore_password WITH BACKUP;

Before migrating from a software keystore to Oracle Key Vault, you can upload the software keystore into the virtual wallet of that endpoint in Oracle Key Vault. After migrating, you now can delete the old TDE wallet, because its key is in Oracle Key Vault. In order to configure auto-open Oracle Key Vault without a wallet being already present, execute the following statement:

    ADMINISTER KEY MANAGEMENT ADD SECRET 'external_keystore_password'
    FOR CLIENT 'OKV_PASSWORD' INTO [LOCAL] AUTO_LOGIN KEYSTORE 'WALLET_ROOT/tde';

Note that the setting `TDE_CONFIGURATION='KEYSTORE_CONFIGUARTION=OKV'` is for a password-protected connection into Oracle Key Vault. After the Oracle Key Vault password has been inserted into an existing or newly created wallet, change the `TDE_CONFIGURATION` setting to `'KEYSTORE_CONFIGURATION=OKV|FILE'`.

**Parent topic:** Storing Oracle Database Secrets

#### 5.3.4 Example: Changing an Oracle Key Vault Password Stored as a Secret in a Software Keystore

The `ADMINISTER KEY MANAGEMENT UPDATE SECRET` statement can change an Oracle Key Vault password that is stored as a secret in a software keystore.

Example 5-8 shows how to change an Oracle Key Vault password that is stored as a secret in a software keystore.

Example 5-8 Changing an Oracle Key Vault Password Secret to a Software Keystore

    ADMINISTER KEY MANAGEMENT
    UPDATE SECRET admin_password FOR CLIENT 'admin@myhost'
    USING TAG 'new_host_credentials' FORCE KEYSTORE
    IDENTIFIED BY software_keytore_password;

In this version, the password for the keystore is in an external store:

    DMINISTER KEY MANAGEMENT
    UPDATE SECRET admin_password FOR CLIENT 'admin@myhost'
    USING TAG 'new_host_credentials' FORCE KEYSTORE
    IDENTIFIED BY EXTERNAL STORE;

**Parent topic:** Storing Oracle Database Secrets

#### 5.3.5 Example: Deleting an Oracle Key Vault Password Stored as a Secret in a Software Keystore

The `ADMINISTER KEY MANAGEMENT DELETE SECRET` statement can delete Oracle Key Vault passwords that are stored as secrets in a software keystore.

Example 5-9 shows how to delete an Oracle Key Vault password that is stored as a secret in the software keystore.

Example 5-9 Deleting an Oracle Key Vault Password Secret in a Software Keystore

    ADMINISTER KEY MANAGEMENT
    DELETE SECRET FOR CLIENT 'OKV_PASSWORD'
    FORCE KEYSTORE
    IDENTIFIED BY password WITH BACKUP;

In this version, the password for the keystore is in an external store:

    ADMINISTER KEY MANAGEMENT
    DELETE SECRET FOR CLIENT 'OKV_PASSWORD'
    FORCE KEYSTORE
    IDENTIFIED BY EXTERNAL STORE WITH BACKUP;

**Parent topic:** Storing Oracle Database Secrets

#### 5.3.6 Storage of Oracle Database Secrets in an External Keystore

The `ADMINISTER KEY MANAGEMENT ADD SECRET|UPDATE SECRET|DELETE SECRET` statements can add, update, and delete secrets.

As with all `ADMINISTER KEY MANAGEMENT` statements, you must have the `ADMINISTER KEY MANAGEMENT` or the `SYSKM` administrative privilege. When you add, update, or delete secrets from a keystore that is in use or presently open, then you must run `ADMINISTER KEY MANAGEMENT` in the root.

You can store Oracle Database secrets in both HSM and Oracle Key Vault external keystores, but be aware that automatic logins do not work if you store the `HSM_PASSWORD` in a Key Vault keystore.

- Adding a secret: Use the following syntax:

      ADMINISTER KEY MANAGEMENT ADD SECRET 'secret'
      FOR CLIENT 'client_identifier' [USING TAG 'tag']
      [TO [[LOCAL] AUTO_LOGIN] KEYSTORE keystore_location
      [FORCE KEYSTORE]
      IDENTIFIED BY "external_key_manager_password"
      [WITH BACKUP [USING backup_id]];

- Updating a secret: Use the following syntax:

      ADMINISTER KEY MANAGEMENT UPDATE SECRET 'secret'
      FOR CLIENT 'client_identifier' [USING TAG 'tag']
      [TO [[LOCAL] AUTO_LOGIN] KEYSTORE keystore_location
      [FORCE KEYSTORE]
      IDENTIFIED BY "external_key_manager_password"
      [WITH BACKUP [USING backup_id]];

- Deleting a secret: Use the following syntax:

      ADMINISTER KEY MANAGEMENT DELETE SECRET
      FOR CLIENT 'client_identifier'
      [FROM [[LOCAL] AUTO_LOGIN] KEYSTORE keystore_location
      [FORCE KEYSTORE]
      IDENTIFIED BY "external_key_manager_password"
      [WITH BACKUP [USING backup_id]];

In all of these statements, the specification as follows:

- `secret` is the client secret key to be stored, updated, or deleted. Enclose this setting in double quotation marks (`' '`) or omit the quotation marks if the secret has no spaces. To find information about existing secrets and their client identifiers, query the `V$CLIENT_SECRETS` dynamic view.

- `client_identifier` is an alphanumeric string used to identify the secret key. `client_identifier` does not have a default value. Enclose this setting in single quotation marks (' ').

- `tag` is an optional, user-defined description for the secret key to be stored. You can use `tag` with the `ADD` and `UPDATE` operations. Enclose this setting in single quotation marks (`' '`). This tag appears in the `SECRET_TAG` column of the `V$CLIENT_SECRETS` view.

- `[TO | FROM [[LOCAL] AUTO_LOGIN] KEYSTORE` specifies the location of the keystore used for the external keystore.

- `external_key_manager_password` is for an external keystore manager, which can be Oracle Key Vault or OCI Vault - Key Management. Enclose this password in double quotation marks. For Oracle Key Vault, enter the password that was given during the Oracle Key Vault client installation. If at that time no password was given, then the password in the `ADMINISTER KEY MANAGEMENT` statement becomes `NULL`.

**Related Topics**

- Creating Custom TDE Master Encryption Key Attributes for Reports

**Parent topic:** Storing Oracle Database Secrets

#### 5.3.7 Example: Adding an Oracle Database Secret to an External Keystore

The `ADMINISTER KEY MANAGEMENT ADD SECRET` statement can add an Oracle Database secret to an external keystore.

Example 5-10 shows how to add a password for a user to an external keystore.

Example 5-10 Adding an Oracle Database Secret to an External Keystore

    ADMINISTER KEY MANAGEMENT ADD SECRET 'password'
    FOR CLIENT 'admin@myhost' USING TAG 'myhost admin credentials'
    IDENTIFIED BY "external_key_manager_password";

In this version, the keystore password is in an external store, so the `EXTERNAL STORE` setting is used for `IDENTIFIED BY`:

    ADMINISTER KEY MANAGEMENT ADD SECRET 'password'
    FOR CLIENT 'admin@myhost' USING TAG 'myhost admin credentials'
    IDENTIFIED BY EXTERNAL STORE;

**Parent topic:** Storing Oracle Database Secrets

#### 5.3.8 Example: Changing an Oracle Database Secret in an External Keystore

The `ADMINISTER KEY MANAGEMENT MANAGEMENT UPDATE SECRET` statement can change an Oracle Database secret in an external keystore.

Example 5-11 shows how to change a password that is stored as a secret in an external keystore.

Example 5-11 Changing an Oracle Database Secret in an External Keystore

    ADMINISTER KEY MANAGEMENT MANAGEMENT UPDATE SECRET 'password2'
    FOR CLIENT 'admin@myhost' USING TAG 'New host credentials'
    IDENTIFIED BY "external_key_manager_password";

In this version, the password for the keystore is in an external store:

    ADMINISTER KEY MANAGEMENT MANAGEMENT UPDATE SECRET 'password2'
    FOR CLIENT 'admin@myhost' USING TAG 'New host credentials'
    IDENTIFIED BY EXTERNAL STORE;

**Parent topic:** Storing Oracle Database Secrets

#### 5.3.9 Example: Deleting an Oracle Database Secret in an External Keystore

The `ADMINISTER KEY MANAGEMENT DELETE SECRET FOR CLIENT` statement can delete an Oracle Database secret that is in an external keystore.

Example 5-12 shows how to delete an external key manager password that is stored as a secret in the external keystore.

Example 5-12 Deleting an Oracle Database Secret in an External Keystore

    ADMINISTER KEY MANAGEMENT DELETE SECRET FOR CLIENT 'admin@myhost'
    IDENTIFIED BY "external_key_manager_password";

In this version, the password for the keystore is in an external store:

    ADMINISTER KEY MANAGEMENT DELETE SECRET FOR CLIENT 'admin@myhost'
    IDENTIFIED BY EXTERNAL STORE;

**Parent topic:** Storing Oracle Database Secrets

#### 5.3.10 Configuring Auto-Open Connections into External Key Managers

An external key manager can be configured to use the auto-login capability.

- About Auto-Open Connections into External Key Managers
  An auto-open connection into an external key manager stores the external keystore credentials in an auto-login keystore.
- Configuring an Auto-Open Connection into an External Key Manager
  To configure the auto-open connection, you must use the `ADMINISTER KEY MANAGEMENT` statement to add or update a client secret to authenticate to the external key manager.

**Parent topic:** Storing Oracle Database Secrets

##### 5.3.10.1 About Auto-Open Connections into External Key Managers

An auto-open connection into an external key manager stores the external keystore credentials in an auto-login keystore.

You can configure a connection to an external key manager so that the database can open the keystore without prompting for the keystore password. This configuration is essential in Oracle Real Application Clusters (Oracle RAC) environments, and is highly recommended for Oracle Data Guard standby databases. Be aware that this configuration reduces the security of the system as a whole. However, this configuration does support unmanned or automated operations, and is useful in deployments where TDE-enabled databases that are enrolled into an external keystore for key management can start automatically.

Be aware that executing the query `SELECT * FROM V$ENCRYPTION_WALLET` will automatically open an auto-login external keystore. For example, suppose you have an auto-login external keystore configured. If you close the keystore and query the `V$ENCRYPTION_WALLET` view, then the output will indicate that a keystore is open. This is because `V$ENCRYPTION_WALLET` opened up the auto-login external keystore and then displayed the status of the auto-login keystore.

To enable the auto-login capability for an external keystore, you must store the external keystore's credentials in an auto-login wallet.

When you use the `ADMINISTER KEY MANAGEMENT` statement, there are conceptually two sets of commands that act on client secrets:

- `ADMINISTER KEY MANAGEMENT` commands that act on the wallet that is currently in use (in other words, a wallet that contains an active TDE master encryption key).
- `ADMINISTER KEY MANAGEMENT` commands that act on a wallet that is not currently being used to hold the active TDE master encryption key. Oracle recommends that you use this approach when you configure an auto-login external keystore.

**Related Topics**

- Configuring an Auto-Open Connection into an External Key Manager

**Parent topic:** Configuring Auto-Open Connections into External Key Managers

##### 5.3.10.2 Configuring an Auto-Open Connection into an External Key Manager

To configure the auto-open connection, you must use the `ADMINISTER KEY MANAGEMENT` statement to add or update a client secret to authenticate to the external key manager.

Before you begin this procedure, ensure that you have configured the external keystore.

In this procedure, the wallet that is created does not contain any keys. It only holds the client secret. So, when you query the `V$ENCRYPTION_WALLET` dynamic view for this wallet, the `STATUS` column shows `OPEN_NO_MASTER_KEY` rather than `OPEN`, because the wallet only contains the client secret.

1.  Reconfigure the `WALLET_ROOT` parameter in the `init.ora` file to include the location of the TDE wallet, if it is not already present.

    The TDE wallet location may already be present if you had previously migrated to using the external key manager.

    For example:

        WALLET_ROOT=/etc/ORACLE/WALLETS/orcl

2.  Add or update the secret in the TDE wallet.

    The secret is the external keystore password and the client is the `OKV_PASSWORD`. `OKV_PASSWORD` is an Oracle-defined client name that is used to represent the external key manager password as a secret in the TDE wallet.

    For example:

        ADMINISTER KEY MANAGEMENT ADD SECRET 'external_key_manager_password'
        FOR CLIENT 'OKV_PASSWORD'
        TO LOCAL AUTO_LOGIN KEYSTORE TDE_wallet_location
        WITH BACKUP;

    In this example:

    - `TDE_wallet_location` is the location of the TDE wallet within the `WALLET_ROOT` location that you just defined in Step 1.

      For the CDB root and for any PDB that is configured in united mode, the value to use for the `TDE_wallet_location` location is `WALLET_ROOT``/tde`.

      For any PDB that is configured in isolated mode, the value to use for the `TDE_wallet_location` location is `WALLET_ROOT``/``pdb_guid``/tde`. When you are in the PDB, run the following query to find this GUID: `SELECT GUID FROM V$PDBS;`

    - `LOCAL` creates a local auto-login wallet file, `cwallet.sso`, to hold the credentials for the external key manager. This wallet is tied to the host on which it was created.

      For an Oracle Real Application Clusters environment, omit the `LOCAL` keyword, because each Oracle RAC node has a different host name, yet they all use the same external key manager. If you configure a local auto-login wallet for the Oracle RAC instance, then only the first Oracle RAC node, where the `cwallet.sso` file was created, would be able to access the external key manager credentials. If you try to open the TDE wallet from another node instead of from that first node, there would be a problem auto-opening `cwallet.sso`, and so it would result in a failure to auto-open the auto-login external keystore. This restriction applies if you are using a shared location to hold the `cwallet.sso` file for the Oracle RAC cluster, because using `LOCAL` only works if you have a separate `cwallet.sso` file (containing the same credentials) on each node of the Oracle RAC environment.

At this stage, the next time a TDE operation runs, the external key manager auto-login TDE wallet opens automatically. An example of a TDE operation is to query the `V$ENCRYPTION_WALLET` view, for example:

    SELECT * FROM V$ENCRYPTION_WALLET;

**Parent topic:** Configuring Auto-Open Connections into External Key Managers

### 5.4 Storing Oracle GoldenGate Secrets in a Keystore

You can store Oracle GoldenGate secrets in Transparent Data Encryption keystores.

- About Storing Oracle GoldenGate Secrets in Keystores
  You can use a keystore to store secret keys for tools and external clients such as Oracle GoldenGate.
- Oracle GoldenGate Extract Classic Capture Mode TDE Requirements
  Ensure that you meet the requirements for Oracle GoldenGate Extract to support Transparent Data Encryption capture.
- Configuring Keystore Support for Oracle GoldenGate
  You can configure Transparent Data Encryption keystore support for Oracle GoldenGate by using a shared secret for the keystore.

**Parent topic:** Managing the Keystore and the Master Encryption Key

#### 5.4.1 About Storing Oracle GoldenGate Secrets in Keystores

You can use a keystore to store secret keys for tools and external clients such as Oracle GoldenGate.

The secret key must be a string adhering to Oracle identifier rules. You can add, update, or delete a client secret in an existing keystore. This section describes how to capture Transparent Data Encryption encrypted data in the Oracle GoldenGate Extract (Extract) process using classic capture mode.

TDE support when Extract is in classic capture mode requires the exchange of the following keys:

- TDE support for Oracle GoldenGate in the classic capture mode of the Extract process requires that an Oracle database and the Extract process share the secret to encrypt sensitive information being exchanged. The shared secret is stored securely in the Oracle database and Oracle GoldenGate domains. The shared secret is stored in the software keystore or the external keystore as the database secret.

- The decryption key is a password known as the shared secret that is stored securely in the Oracle database and Oracle GoldenGate domains. Only a party that has possession of the shared secret can decrypt the table and redo log keys.

After you configure the shared secret, Oracle GoldenGate Extract uses the shared secret to decrypt the data. Oracle GoldenGate Extract does not handle the TDE master encryption key itself, nor is it aware of the keystore password. The TDE master encryption key and password remain within the Oracle database configuration.

Oracle GoldenGate Extract only writes the decrypted data to the Oracle GoldenGate trail file, which Oracle GoldenGate persists during transit. You can protect this file using your site's operating system standard security protocols, as well as the Oracle GoldenGate AES encryption options. Oracle GoldenGate does not write the encrypted data to a discard file (specified with the `DISCARDFILE` parameter). The word `ENCRYPTED` will be written to any discard file that is in use.

Oracle GoldenGate does require that the keystore be open when processing encrypted data. There is no performance effect of Oracle GoldenGate feature on the TDE operations.

**Parent topic:** Storing Oracle GoldenGate Secrets in a Keystore

#### 5.4.2 Oracle GoldenGate Extract Classic Capture Mode TDE Requirements

Ensure that you meet the requirements for Oracle GoldenGate Extract to support Transparent Data Encryption capture.

The requirements are as follows:

- To maintain high security standards, ensure that the Oracle GoldenGate Extract process runs as part of the Oracle user (the user that runs the Oracle database). That way, the keys are protected in memory by the same privileges as the Oracle user.

- Run the Oracle GoldenGate Extract process on the same computer as the Oracle database installation.

**Parent topic:** Storing Oracle GoldenGate Secrets in a Keystore

#### 5.4.3 Configuring Keystore Support for Oracle GoldenGate

You can configure Transparent Data Encryption keystore support for Oracle GoldenGate by using a shared secret for the keystore.

- Step 1: Decide on a Shared Secret for the Keystore
  A shared secret for a keystore is a password.
- Step 2: Configure Oracle Database for TDE Support for Oracle GoldenGate
  The `DBMS_INTERNAL_CLKM` PL/SQL package enables you to configure TDE support for Oracle GoldenGate.
- Step 3: Store the TDE GoldenGate Shared Secret in the Keystore
  The `ADMINISTER KEY MANAGEMENT` statement can store a TDE GoldenGate shared secret in a keystore.
- Step 4: Set the TDE Oracle GoldenGate Shared Secret in the Extract Process
  The GoldenGate Software Command Interface (GGSCI) utility sets the TDE Oracle GoldenGate shared secret in the extract process.

**Parent topic:** Storing Oracle GoldenGate Secrets in a Keystore

##### 5.4.3.1 Step 1: Decide on a Shared Secret for the Keystore

A shared secret for a keystore is a password.

- Decide on a shared secret that meets or exceeds Oracle Database password standards.

Do not share this password with any user other than trusted administrators who are responsible for configuring Transparent Data Encryption to work with Oracle GoldenGate Extract.

**Related Topics**

- [Oracle Database Security Guide](../dbseg/keeping-your-oracle-database-secure.md)

**Parent topic:** Configuring Keystore Support for Oracle GoldenGate

##### 5.4.3.2 Step 2: Configure Oracle Database for TDE Support for Oracle GoldenGate

The `DBMS_INTERNAL_CLKM` PL/SQL package enables you to configure TDE support for Oracle GoldenGate.

1.  Log in to the database instance as user `SYS` with the `SYSDBA` administrative privilege.

    For example

        sqlplus sys as sysdba
        Enter password: password
        Connected.

2.  Load the Oracle Database-supplied `DBMS_INTERNAL_CLKM` PL/SQL package.

    For example:

        @?/app/oracle/product/12.2/rdbms/admin/prvtclkm.plb

    The `prvtclkm.plb` file also enables Oracle GoldenGate to extract encrypted data from an Oracle database.

3.  Grant the `EXECUTE` privilege on the `DBMS_INTERNAL_CLKM` PL/SQL package to the Oracle GoldenGate Extract database user.

    For example:

        GRANT EXECUTE ON DBMS_INTERNAL_CLKM TO psmith;

    This procedure enables the Oracle database and Oracle GoldenGate Extract to exchange information.

4.  Exit SQL\*Plus.

**Parent topic:** Configuring Keystore Support for Oracle GoldenGate

##### 5.4.3.3 Step 3: Store the TDE GoldenGate Shared Secret in the Keystore

The `ADMINISTER KEY MANAGEMENT` statement can store a TDE GoldenGate shared secret in a keystore.

Before you begin this procedure, ensure that you have configured the TDE software or external keystore, based on [Configuring a TDE Wallet](configuring-transparent-data-encryption.md) and [Configuring an External Keystore](configuring-transparent-data-encryption.md).

1.  Set the Oracle GoldenGate-TDE key in the keystore by using the following syntax.

        ADMINISTER KEY MANAGEMENT ADD|UPDATE|DELETE SECRET 'secret'
        FOR CLIENT 'secret_identifier' [USING TAG 'tag']
        IDENTIFIED BY keystore_password [WITH BACKUP [USING 'backup_identifier']];

    In this specification:

    - `secret` is the client secret key to be stored, updated, or deleted. Enclose this setting in single quotation marks (`' '`).

    - `secret_identifier` is an alphanumeric string used to identify the secret key. `secret_identifier` does not have a default value. Enclose this setting in single quotation marks (`' '`).

    - `tag` is an optional, user-defined description for the secret key to be stored. `tag` can be used with the `ADD` and `UPDATE` operations. Enclose this setting in single quotation marks (`' '`). This tag appears in the `SECRET_TAG` column of the `V$CLIENT_SECRETS` view. Creating Custom TDE Master Encryption Key Attributes for Reports

    - `keystore_password` is the password for the keystore that is configured.

    - `WITH BACKUP` is required in case the keystore was not backed up before the `ADD`, `UPDATE` or `DELETE` operation. `backup_identifier` is an optional user-defined description for the backup. Enclose `backup_identifier` in single quotation marks (`' '`).

    The following example adds a secret key to the keystore and creates a backup in the same directory as the keystore:

        ADMINISTER KEY MANAGEMENT ADD SECRET 'some_secret'
        FOR CLIENT 'ORACLE_GG' USING TAG 'GoldenGate Secret'
        IDENTIFIED BY password WITH BACKUP USING 'GG backup';

2.  Verify the entry that you just created.

    For example:

        SELECT CLIENT, SECRET_TAG FROM V$CLIENT_SECRETS WHERE CLIENT = 'ORACLEGG';

        CLIENT   SECRET_TAG
        -------- ------------------------------------------
        ORACLEGG some_secret

3.  Switch the log files.

        CONNECT / AS SYSDBA

        ALTER SYSTEM SWITCH LOGFILE;

**See Also:**

- Creating Custom TDE Master Encryption Key Attributes for Reports for more information about tags

- [Oracle Database Administrator’s Guide](../admin/managing-the-redo-log.md) for more information about switching log files

- [How Transparent Data Encryption Works with Oracle Real Application Clusters](using-transparent-data-encryption-with-other-oracle-features.md) if you are having problems using this procedure in an Oracle Real Application Clusters environment

**Parent topic:** Configuring Keystore Support for Oracle GoldenGate

##### 5.4.3.4 Step 4: Set the TDE Oracle GoldenGate Shared Secret in the Extract Process

The GoldenGate Software Command Interface (GGSCI) utility sets the TDE Oracle GoldenGate shared secret in the extract process.

1.  Start the GGSCI utility.

    For example:

        ggsci

2.  In the GGSCI utility, run the `ENCRYPT PASSWORD` command to encrypt the shared secret within the Oracle GoldenGate Extract parameter file.

        ENCRYPT PASSWORD shared_secret algorithm ENCRYPTKEY keyname

    In this specification:

    - `shared_secret` is the clear-text shared secret that you created when you decided on a shared secret for the keystore. This setting is case sensitive.

    - `algorithm` is one of the following values to specify AES encryption:

      - `AES128`

      - `AES192`

      - `AES256`

    - `keyname` is the logical name of the encryption key in the `ENCKEYS` lookup file. Oracle GoldenGate uses this name to look up the actual key in the `ENCKEYS` file.

    For example:

        ENCRYPT PASSWORD password AES256 ENCRYPTKEY mykey1

3.  In the Oracle GoldenGate Extract parameter file, set the `DBOPTIONS` parameter with the `DECRYPTPASSWORD` option.

    As input, supply the encrypted shared secret and the Oracle GoldenGate-generated or user-defined decryption key.

        DBOPTIONS DECRYPTPASSWORD shared_secret algorithm ENCRYPTKEY keyname

    In this specification:

    - `shared_secret` is the clear-text shared secret that you created when you decided on a shared secret for the keystore. This setting is case sensitive.

    - `algorithm` is one of the following values to specify AES encryption:

      - `AES128`

      - `AES192`

      - `AES256`

    - `keyname` is the logical name of the encryption key in the `ENCKEYS` lookup file.

      For example:

          DBOPTIONS DECRYPTPASSWORD AACAAAAAAAAAAAIALCKDZIRHOJBHOJUH AES256 ENCRYPTKEY mykey1

**Related Topics**

- Step 1: Decide on a Shared Secret for the Keystore

**Parent topic:** Configuring Keystore Support for Oracle GoldenGate
