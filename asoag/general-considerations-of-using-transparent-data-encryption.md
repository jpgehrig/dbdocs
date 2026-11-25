## 8 General Considerations of Using Transparent Data Encryption

When you use Transparent Data Encryption, you should consider factors such as security, performance, and storage overheads.

- Migrating Encrypted TDE Columns or Tablespaces after a Database Upgrade from Release 11g
  If you are upgrading from Oracle Database release 11g, then you must manually convert the typed master encryption keys to united mode master encryption keys.
- Compression and Data Deduplication of Encrypted Data
  When you use Oracle's compression products and options with Transparent Data Encryption (TDE) tablespace encryption, Oracle Database automatically applies compression before performing the encryption.
- Security Considerations for Transparent Data Encryption
  As with all Oracle Database features, you should consider security when you create TDE policies.
- Performance and Storage Overhead of Transparent Data Encryption
  The performance of Transparent Data Encryption can vary.
- Modifying Your Applications for Use with Transparent Data Encryption
  You can modify your applications to use Transparent Data Encryption.
- How ALTER SYSTEM and orapki Map to ADMINISTER KEY MANAGEMENT
  Many of the clauses from the `ALTER SYSTEM` statement correspond to the `ADMINISTER KEY MANAGEMENT` statement.
- Data Loads from External Files to Tables with Encrypted Columns
  You can use SQL\*Loader to perform data loads from files to tables that have encrypted columns.
- Transparent Data Encryption and Database Close Operations
  You should ensure that the software or external keystore is open before you close the database.

**Parent topic:** [Using Transparent Data Encryption](asopart1.md)

### 8.1 Migrating Encrypted TDE Columns or Tablespaces after a Database Upgrade from Release 11g

If you are upgrading from Oracle Database release 11g, then you must manually convert the typed master encryption keys to united mode master encryption keys.

You must perform this task for master encryption keys in both column encryption and tablespace encryption configurations.

1.  Navigate to directory that has the TDE password-based keystore `ewallet.p12`.
2.  Check the keystore contents and look for typed keys (that is, identifiers starting with `ORACLE.SECURITY.TS.ENCRYPTION.B` as follows).
        mkstore -wrl ewallet.p12 -list
        Enter wallet password: wallet_password

    Output similar to the following appears. The entries with TS are the typed keys that must be converted.

        Oracle Secret Store entries:
        ORACLE.SECURITY.DB.ENCRYPTION.AYTGHzMNxU9kv77shWptsxkAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
        ORACLE.SECURITY.DB.ENCRYPTION.ARjWMYe05E9Bv4KULq1no8UAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
        ORACLE.SECURITY.DB.ENCRYPTION.ASoO2D5jtk/jv9FPW6rhhGcAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
        ORACLE.SECURITY.DB.ENCRYPTION.MASTERKEY
        ORACLE.SECURITY.TS.ENCRYPTION.BW8QuLUTgOpV0PtEt/lR028CAwAAAAAAAAAAAAAAAAAAAAAAAAAA
        ORACLE.SECURITY.TS.ENCRYPTION.BWNFXbAc38AZMdFdi2kuWV0CAwAAAAAAAAAAAAAAAAAAAAAAAAAA
3.  Back up the keystore.
    For example:
        cp ewallet.p12 ewallet_ddddmmyy.p12
4.  Create a united key for each typed key that you found in the keystore.
    To accomplish this, you must modify the identifier name (Key ID) to have DB instead of TS and the first letter from B to A. For this you must add a new entry to the keystore. The following example shows how to convert the first typed key in the list that was shown in the preceding steps.
    1.  List the value for identifier to double-check it. The bold text indicates the two changes to be made.
        For example:
            ORACLE.SECURITY.TS.ENCRYPTION.BW8QuLUTgOpV0PtEt/lR028CAwAAAAAAAAAAAAAAAAA

        This example must be changed as follows:

            ORACLE.SECURITY.DB.ENCRYPTION.AW8QuLUTgOpV0PtEt/lR028CAwAAAAAAAAAAAAAAAAA
    2.  Using this updated entry, add a new entry to the keystore.
        For example:
            mkstore -wrl wallet_location -viewEntry
            ORACLE.SECURITY.TS.ENCRYPTION.BW8QuLUTgOpV0PtEt/lR028CAwAAAAAAAAAAAAAAAAAAAAAAAAAA

        The `-viewEntry` option of this command displays the identifier value for the TS encryption, which you must include in the next command when you create the keystore entry:

            mkstore -wrl wallet_location -
            createEntry ORACLE.SECURITY.DB.ENCRYPTION.AW8QuLUTgOpV0PtEt/lR028CAwAAAAAAAAAAAAAAAA
            AAAAAAAAAA value_for_ts_encryption_identifier
    3.  For an auto-login keystore, rename the old auto-login keystore and then create a new one.
        1.  Back up the master encryption key. For example:

                mv cwallet.sso cwallet_ddddmmyy.sso

        2.  Use the `ADMINISTER KEY MANAGEMENT` command to create the auto-login keystore.

**Related Topics**

- [Creating an Auto-Login or a Local Auto-Login Software Keystore](configuring-transparent-data-encryption.md)

**Parent topic:** General Considerations of Using Transparent Data Encryption

### 8.2 Compression and Data Deduplication of Encrypted Data

When you use Oracle's compression products and options with Transparent Data Encryption (TDE) tablespace encryption, Oracle Database automatically applies compression before performing the encryption.

The compression products include the following: Oracle Recovery Manager (Oracle RMAN) compression, Oracle Advanced Compression, Exadata Hybrid Columnar Compression (EHCC), and so on.

This ensures that you receive the maximum space and performance benefits from compression, while also receiving the security of encryption at rest. In the `CREATE TABLESPACE` SQL statement, include both the `COMPRESS` and `ENCRYPT` clauses.

With column encryption, Oracle Database compresses the data after it encrypts the column. This means that compression will have minimal effectiveness on encrypted columns. There is one notable exception: if the column is a SecureFiles LOB, and the encryption is implemented with SecureFiles LOB Encryption, and the compression (and possibly deduplication) are implemented with SecureFiles LOB Compression & Deduplication, then compression is performed before encryption. Similar to the `CREATE TABLESPACE` statement for tablespace encryption, include both the `COMPRESS` and `ENCRYPT` clauses.

**Note:**

The type of compression that you can use depends on the licensing that you have for Advanced Compression. See [Oracle Database Licensing Information User Manual](../dblic/Licensing-Information.md).

**Related Topics**

- [Oracle Database Backup and Recovery User’s Guide](../bradv/configuring-rman-client-advanced.md)

**Parent topic:** General Considerations of Using Transparent Data Encryption

### 8.3 Security Considerations for Transparent Data Encryption

As with all Oracle Database features, you should consider security when you create TDE policies.

- Transparent Data Encryption General Security Advice
  Security considerations for Transparent Data Encryption (TDE) operate within the broader area of total system security.
- Transparent Data Encryption Column Encryption-Specific Advice
  Additional security considerations apply to normal database and network operations when using TDE.
- Managing Security for Plaintext Fragments
  You should remove old plaintext fragments that can appear over time.

**Parent topic:** General Considerations of Using Transparent Data Encryption

#### 8.3.1 Transparent Data Encryption General Security Advice

Security considerations for Transparent Data Encryption (TDE) operate within the broader area of total system security.

Follow these general guidelines:

- Identify the degrees of sensitivity of data in your database, the protection that they need, and the levels of risk to be addressed. For example, highly sensitive data requiring stronger protection can be encrypted with the AES256 algorithm. A database that is not as sensitive can be protected with no [salt](glossary.md) or the `nomac` option to enable performance benefits.

- Evaluate the costs and benefits that are acceptable to data and keystore protection. Protection of keys determines the type of keystore to be used: auto-login TDE wallets, password-based TDE wallets, or external keystores.

- Consider having separate security administrators for TDE and for the database.

- Consider having a separate and exclusive keystore for TDE.

- Implement protected back-up procedures for your encrypted data.

**Parent topic:** Security Considerations for Transparent Data Encryption

#### 8.3.2 Transparent Data Encryption Column Encryption-Specific Advice

Additional security considerations apply to normal database and network operations when using TDE.

Encrypted column data stays encrypted in the data files, undo logs, redo logs, and the buffer cache of the system global area (SGA). However, data is decrypted during expression evaluation, making it possible for decrypted data to appear in the swap file on the disk. Privileged operating system users can potentially view this data.

Column values encrypted using TDE are stored in the data files in encrypted form. However, these data files may still contain some [plaintext](glossary.md) fragments, called ghost copies, left over by past data operations on the table. This is similar to finding data on the disk after a file was deleted by the operating system.

**Parent topic:** Security Considerations for Transparent Data Encryption

#### 8.3.3 Managing Security for Plaintext Fragments

You should remove old plaintext fragments that can appear over time.

Old [plaintext](glossary.md) fragments may be present for some time until the database overwrites the blocks containing such values. If privileged operating system users bypass the access controls of the database, then they might be able to directly access these values in the data file holding the tablespace.

To minimize this risk:

1.  Create a new tablespace in a new data file.

    You can use the `CREATE TABLESPACE` statement to create this tablespace.

2.  Move the table containing encrypted columns to the new tablespace. You can use the `ALTER TABLE.....MOVE` statement.

    Repeat this step for all of the objects in the original tablespace.

3.  Drop the original tablespace.

    You can use the `DROP TABLESPACE ``tablespace` `INCLUDING CONTENTS KEEP DATAFILES` statement. Oracle recommends that you securely delete data files using platform-specific utilities.

4.  Use platform-specific and file system-specific utilities to securely delete the old data file. Examples of such utilities include `shred` (on Linux) and `sdelete` (on Windows).

**Parent topic:** Security Considerations for Transparent Data Encryption

### 8.4 Performance and Storage Overhead of Transparent Data Encryption

The performance of Transparent Data Encryption can vary.

- Performance Overhead of Transparent Data Encryption
  Transparent Data Encryption tablespace encryption has small associated performance overhead.
- Storage Overhead of Transparent Data Encryption
  TDE tablespace encryption has no storage overhead, but TDE column encryption has some associated storage overhead.

**Parent topic:** General Considerations of Using Transparent Data Encryption

#### 8.4.1 Performance Overhead of Transparent Data Encryption

Transparent Data Encryption tablespace encryption has small associated performance overhead.

The actual performance impact on applications can vary. TDE column encryption affects performance only when data is retrieved from or inserted into an encrypted column. No reduction in performance occurs for operations involving unencrypted columns, even if these columns are in a table containing encrypted columns. Accessing data in encrypted columns involves small performance overhead, and the exact overhead you observe can vary.

The total performance overhead depends on the number of encrypted columns and their frequency of access. The columns most appropriate for encryption are those containing the most sensitive data.

Enabling encryption on an existing table results in a full table update like any other `ALTER TABLE` operation that modifies table characteristics. Keep in mind the potential performance and redo log impact on the database server before enabling encryption on a large existing table.

A table can temporarily become inaccessible for write operations while encryption is being enabled, [TDE table key](glossary.md)s are being rekeyed, or the encryption algorithm is being changed. You can use online table redefinition to ensure that the table is available for write operations during such procedures.

If you enable TDE column encryption on a very large table, then you may need to increase the redo log size to accommodate the operation.

Encrypting an indexed column takes more time than encrypting a column without indexes. If you must encrypt a column that has an index built on it, you can try dropping the index, encrypting the column with `NO SALT`, and then re-creating the index.

If you index an encrypted column, then the index is created on the encrypted values. When you query for a value in the encrypted column, Oracle Database transparently encrypts the value used in the SQL query. It then performs an index lookup using the encrypted value.

**Note:**

If you must perform range scans over indexed, encrypted columns, then use TDE tablespace encryption in place of TDE column encryption.

**See Also:**

- [Creating an Encrypted Column in an External Table](configuring-transparent-data-encryption.md)

- [Oracle Database Administrator’s Guide](../admin/managing-tables.md) for information about redefining tables online

**Parent topic:** Performance and Storage Overhead of Transparent Data Encryption

#### 8.4.2 Storage Overhead of Transparent Data Encryption

TDE tablespace encryption has no storage overhead, but TDE column encryption has some associated storage overhead.

Encrypted column data must have more storage space than [plaintext](glossary.md) data. In addition, TDE pads out encrypted values to multiples of 16 bytes. This means that if a credit card number requires nine bytes for storage, then an encrypted credit card value will require an additional seven bytes.

Each encrypted value is also associated with a 20-byte integrity check. This does not apply if you have encrypted columns using the `NOMAC` parameter. If data was encrypted with [salt](glossary.md), then each encrypted value requires an additional 16 bytes of storage.

The maximum storage overhead for each encrypted value is from one to 52 bytes.

**Related Topics**

- [Creating an Encrypted Column in an External Table](configuring-transparent-data-encryption.md)

**Parent topic:** Performance and Storage Overhead of Transparent Data Encryption

### 8.5 Modifying Your Applications for Use with Transparent Data Encryption

You can modify your applications to use Transparent Data Encryption.

1.  Configure the software or external keystore for TDE, and then set the master encryption key.

    See the following sections for more information:

    - [Configuring a TDE Wallet](configuring-transparent-data-encryption.md)

    - [Configuring an External Keystore](configuring-transparent-data-encryption.md)

2.  Verify that the master encryption key was created by querying the `KEY_ID` column of the `V$ENCRYPTION_KEYS` view.

3.  Identify the sensitive columns (such as those containing credit card data) that require Transparent Data Encryption protection.

4.  Decide whether to use TDE column encryption or TDE tablespace encryption.

    See the following sections for more information:

    - [How Transparent Data Encryption Column Encryption Works](introduction-to-transparent-data-encryption.md)

    - [How Transparent Data Encryption Tablespace Encryption Works](introduction-to-transparent-data-encryption.md)

5.  Open the keystore.

    See the following sections for more information:

    - [Step 3: Open the TDE Wallet](configuring-transparent-data-encryption.md)

    - [Step 2: Open the Connection to Oracle Key Vault](managing-keystores-encryption-keys-in-united-mode.md)

6.  Encrypt the columns or tablespaces.

    See the following sections for more information:

    - [Encrypting Columns in Tables](configuring-transparent-data-encryption.md)

    - [Encryption Conversions for Tablespaces and Databases](configuring-transparent-data-encryption.md)

**Parent topic:** General Considerations of Using Transparent Data Encryption

### 8.6 How ALTER SYSTEM and orapki Map to ADMINISTER KEY MANAGEMENT

Many of the clauses from the `ALTER SYSTEM` statement correspond to the `ADMINISTER KEY MANAGEMENT` statement.

[Table 9-1](using-transparent-data-encryption-with-other-oracle-features.md) compares the Transparent Data Encryption usage of the `ALTER SYSTEM` statement and the `orapki` utility from previous releases with the `ADMINISTER KEY MANAGEMENT` statement.

Table 8-1 How ALTER SYSTEM and orapki Map to ADMINISTER KEY MANAGEMENT

| Behavior                                                                                                     | ALTER SYSTEM or orapki                                                                                                                                                                                                      | ADMINISTER KEY MANAGEMENT                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
|:-------------------------------------------------------------------------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Creating a keystore                                                                                          | For TDE wallets:<br>`ALTER SYSTEM SET ENCRYPTION KEY`<br>`["certificate_ID"] IDENTIFIED`<br>`BY keystore_password;`<br>For external keystores, the keystore is available after you configure the external keystore.         | For TDE wallets:<br>`ADMINISTER KEY MANAGEMENT CREATE KEYSTORE`<br>`IDENTIFIED BY TDE_wallet_password`<br>For external keystores, the keystore is available after you configure the external keystore.                                                                                                                                                                                                                                                                                |
| Creating an auto-login keystore                                                                              | `orapki wallet create -wallet`<br>`wallet_location `<br>`-auto_login [-pwd password]`                                                                                                                                       | For TDE wallets:<br>`ADMINISTER KEY MANAGEMENT CREATE [LOCAL]`<br>`AUTO_LOGIN KEYSTORE FROM KEYSTORE`<br>`IDENTIFIED BY TDE_wallet_password;`<br>This type of keystore applies to TDE wallets only.                                                                                                                                                                                                                                                                                   |
| Opening a keystore                                                                                           | `ALTER SYSTEM SET [ENCRYPTION]`<br>`WALLET OPEN IDENTIFIED BY`<br>`keystore_password;`                                                                                                                                      | `ADMINISTER KEY MANAGEMENT SET KEYSTORE `<br>`OPEN [FORCE KEYSTORE] `<br>`IDENTIFIED BY keystore_password | EXTERNAL STORE`<br>`[CONTAINER = ALL | CURRENT];`                                                                                                                                                                                                                                                                                                                         |
| Closing a keystore                                                                                           | `ALTER SYSTEM SET [ENCRYPTION]`<br>`WALLET CLOSE IDENTIFIED BY`<br>`keystore_password;`                                                                                                                                     | For both software and external keystores:<br>`ADMINISTER KEY MANAGEMENT SET KEYSTORE `<br>`CLOSE [IDENTIFIED BY keystore_password]`<br>`[CONTAINER = ALL | CURRENT];`                                                                                                                                                                                                                                                                                                                 |
| Migrating from an external keystore to a TDE wallet                                                          | `ALTER SYSTEM SET [ENCRYPTION] KEY `<br>`IDENTIFIED BY wallet_password `<br>`REVERSE MIGRATE USING "external_key_manager_password" `<br>`WITH BACKUP;`                                                                      | `ADMINISTER KEY MANAGEMENT SET [ENCRYPTION]`<br>`KEY IDENTIFIED BY`<br>`keystore_password`<br>`REVERSE MIGRATE USING "external_key_manager_password"`<br>`WITH BACKUP [USING 'backup_identifier'];`                                                                                                                                                                                                                                                                                   |
| Migrating from a TDE wallet to Oracle Key Vault or Oracle Cloud Interface (OCI) Key Management Service (KMS) | `ALTER SYSTEM SET [ENCRYPTION] KEY`<br>`IDENTIFIED BY "Oracle_Key_Vault_password" `<br>`MIGRATE USING wallet_password;`                                                                                                     | `ADMINISTER KEY MANAGEMENT SET [ENCRYPTION]`<br>`KEY IDENTIFIED BY "Oracle_Key_Vault_password"`<br>`MIGRATE USING wallet_password;`                                                                                                                                                                                                                                                                                                                                                   |
| Changing a keystore password                                                                                 | `orapki wallet change_pwd`<br>`-wallet wallet_location`<br>`[-oldpwd password ] `<br>`[-newpwd password]`                                                                                                                   | For password-based TDE wallets:<br>`ADMINISTER KEY MANAGEMENT ALTER KEYSTORE`<br>`PASSWORD IDENTIFIED BY`<br>`TDE_wallet_old_password `<br>`SET TDE_wallet_new_password`<br>`[WITH BACKUP [USING 'backup_identifier']];`<br>For external keystores, you close the keystore, change it in the external key manager interface, and then reopen the keystore.                                                                                                                            |
| Backing up a password-based TDE wallet                                                                       | No `ALTER SYSTEM` or `orapki` equivalent for this functionality                                                                                                                                                             | `ADMINISTER KEY MANAGEMENT BACKUP KEYSTORE`<br>`[USING 'backup_identifier'] IDENTIFIED BY`<br>`TDE_wallet_password `<br>`[TO 'TDE_wallet_location'];`                                                                                                                                                                                                                                                                                                                                 |
| Merging two TDE wallets into a third new keystore                                                            | No `ALTER SYSTEM` or `orapki` equivalent for this functionality                                                                                                                                                             | `ADMINISTER KEY MANAGEMENT MERGE KEYSTORE`<br>`'TDE_wallet1_location' [IDENTIFIED BY`<br>`TDE_wallet1_password] `<br>`AND KEYSTORE 'TDE_wallet2_location'`<br>`[IDENTIFIED BY TDE_wallet2_password]`<br>`INTO NEW KEYSTORE 'TDE_wallet3_location'`<br>`IDENTIFIED BY TDE_wallet3_password;`                                                                                                                                                                                           |
| Merging one TDE wallet into another existing keystore                                                        | No `ALTER SYSTEM` or `orapki` equivalent for this functionality                                                                                                                                                             | `ADMINISTER KEY MANAGEMENT MERGE KEYSTORE`<br>`'TDE_wallet1_location' [IDENTIFIED BY`<br>`TDE_wallet1_password] `<br>`INTO EXISTNG KEYSTORE 'TDE_wallet2_location'`<br>`IDENTIFIED BY TDE_wallet2_password`<br>`[WITH BACKUP [USING 'backup_identifier']];`                                                                                                                                                                                                                           |
| Setting or rekeying the master encryption key                                                                | `ALTER SYSTEM SET [ENCRYPTION] KEY`<br>`IDENTIFIED BY keystore_password;`<br>Note: The `ALTER SYSTEM SET ENCRYPTION KEY` statement does not update the `V$ENCRYPTION_KEYS` dynamic view after you rekey the encryption key. | `ADMINISTER KEY MANAGEMENT `<br>`SET ENCRYPTION KEY [USING TAG 'tag']`<br>`IDENTIFIED BY keystore_password `<br>`WITH BACKUP [USING 'backup_identifier'] `<br>`[CONTAINER = ALL | CURRENT];`<br>After you rekey the encryption key, the `V$ENCRYPTION_KEYS` dynamic view is updated.                                                                                                                                                                                                  |
| Creating a master encryption key for later user                                                              | No `ALTER SYSTEM` or `orapki` equivalent for this functionality                                                                                                                                                             | `ADMINISTER KEY MANAGEMENT CREATE KEY `<br>`[USING TAG 'tag'] `<br>`IDENTIFIED BY keystore_password `<br>`[WITH BACKUP [USING 'backup_identifier']]`<br>`[CONTAINER = (ALL|CURRENT)];`                                                                                                                                                                                                                                                                                                |
| Activating a master encryption key                                                                           | No `ALTER SYSTEM` or `orapki` equivalent for this functionality                                                                                                                                                             | `ADMINISTER KEY MANAGEMENT USE KEY`<br>`'key_identifier' [USING TAG 'tag'] `<br>`IDENTIFIED BY keystore_password `<br>`[WITH BACKUP [USING 'backup_identifier']];`                                                                                                                                                                                                                                                                                                                    |
| Creating custom tags for master encryption keys                                                              | No `ALTER SYSTEM` or `orapki` equivalent for this functionality                                                                                                                                                             | `ADMINISTER KEY MANAGEMENT SET TAG 'tag' `<br>`FOR 'master_key_identifier' `<br>`IDENTIFIED BY keystore_password `<br>`[WITH BACKUP [USING 'backup_identifier']];`                                                                                                                                                                                                                                                                                                                    |
| Exporting a master encryption key                                                                            | No `ALTER SYSTEM` or `orapki` equivalent for this functionality                                                                                                                                                             | `ADMINISTER KEY MANAGEMENT `<br>`EXPORT [ENCRYPTION] KEYS `<br>`WITH SECRET "export_secret" `<br>`TO 'file_path' `<br>`IDENTIFIED BY keystoe_password`<br>`[WITH IDENTIFIER IN `<br>`'key_id1', 'key_id2', 'key_idn' | `<br>`(SQL_query)]`                                                                                                                                                                                                                                            |
| Importing a master encryption key                                                                            | No `ALTER SYSTEM` or `orapki` equivalent for this functionality                                                                                                                                                             | `ADMINISTER KEY MANAGEMENT `<br>`IMPORT [ENCRYPTION] KEYS `<br>`WITH SECRET "import_secret" |  `<br>`FROM 'file_name' `<br>`IDENTIFIED BY keystore_password`<br>`[WITH BACKUP [USING 'backup_identifier']];`                                                                                                                                                                                                                                                                          |
| Storing Oracle Database secrets in a keystore                                                                | No `ALTER SYSTEM` or `orapki` equivalent for this functionality                                                                                                                                                             | For TDE wallets:<br>`ADMINISTER KEY MANAGEMENT`<br>`ADD SECRET|UPDATE SECRET|DELETE SECRET`<br>`"secret" FOR CLIENT 'client_identifier' `<br>`[USING TAG'tag'] `<br>`IDENTIFIED BY keystore_password `<br>`[WITH BACKUP [USING 'backup_identifier'];`<br>For external keystores:<br>`ADMINISTER KEY MANAGEMENT`<br>`ADD SECRET|UPDATE SECRET|DELETE SECRET`<br>`"secret" FOR CLIENT 'client_identifier' `<br>`[USING TAG 'tag'] `<br>`IDENTIFIED BY "external_key_manager_password";` |

**Parent topic:** General Considerations of Using Transparent Data Encryption

### 8.7 Data Loads from External Files to Tables with Encrypted Columns

You can use SQL\*Loader to perform data loads from files to tables that have encrypted columns.

Be aware that with SQL\*Loader, you cannot include the `ENCRYPT` clause in the column definition of an external table of the type `ORACLE_LOADER`, but you can include it in the column definitions of external tables of type `ORACLE_DATAPUMP`.

- External tables of type `ORACLE_LOADER`

  The reason that you cannot include the `ENCRYPT` clause in the column definitions of external tables of the type `ORACLE_LOADER` is because the contents of an external table with the `ORACLE_LOADER` type must come from a user-specified plaintext "backing file," and such plaintext files cannot contain any TDE encrypted data.

  If you use the `ENCRYPT` clause in the definition of an external table of type `ORACLE_LOADER`, then when you query the TDE-encrypted column in this external table, the query fails. This is because TDE expects the external data to have been encrypted, and automatically tries to decrypt it on load. This action fails because the "backing file" only contains plaintext.

- External tables of type `ORACLE_DATAPUMP`

  You can use TDE column encryption with external tables of type `ORACLE_DATAPUMP`. This is because for external tables of `ORACLE_DATAPUMP` type, the "backing file" is always created by Oracle Database(during an unload operation) and thus does have support for being populated with encrypted data.

**Parent topic:** General Considerations of Using Transparent Data Encryption

### 8.8 Transparent Data Encryption and Database Close Operations

You should ensure that the software or external keystore is open before you close the database.

The master encryption keys may be required during the database close operation. The database close operation automatically closes the software or external keystore.

**Related Topics**

- [Step 3: Open the TDE Wallet](configuring-transparent-data-encryption.md)
- [Step 2: Open the Connection to Oracle Key Vault](managing-keystores-encryption-keys-in-united-mode.md)

**Parent topic:** General Considerations of Using Transparent Data Encryption
