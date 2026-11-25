## 9 Using Transparent Data Encryption with Other Oracle Features

You can use Oracle Data Encryption with other Oracle features, such as Oracle Data Guard or Oracle Real Application Clusters.

- How Transparent Data Encryption Works with Export and Import Operations
  Oracle Data Pump can export and import tables that contain encrypted columns, as well as encrypt entire dump sets.
- How Transparent Data Encryption Works with Oracle Data Guard
  An Oracle Data Guard primary database and secondary secondary database can share both a TDE wallet and an external keystore.
- How Transparent Data Encryption Works with Oracle Real Application Clusters
  Oracle Real Application Clusters (Oracle RAC) nodes can share both a TDE wallets and an external keystore.
- How Transparent Data Encryption Works with SecureFiles
  SecureFiles, which stores LOBS, has three features: compression, deduplication, and encryption.
- How Transparent Data Encryption Works with Oracle Call Interface
  Transparent Data Encryption does not have any effect on the operation of Oracle Call Interface (OCI).
- How Transparent Data Encryption Works with Editions
  Transparent Data Encryption does not have any effect on the Editions feature of Oracle Database.
- Configuring Transparent Data Encryption to Work in a Multidatabase Environment
  Each Oracle database on the same server (such as databases sharing the same Oracle binary but using different data files) must access its own TDE keystore.

**Parent topic:** [Using Transparent Data Encryption](asopart1.md)

### 9.1 How Transparent Data Encryption Works with Export and Import Operations

Oracle Data Pump can export and import tables that contain encrypted columns, as well as encrypt entire dump sets.

- About Exporting and Importing Encrypted Data
  You can use Oracle Data Pump to export and import tables that have encrypted columns.
- Exporting and Importing Tables with Encrypted Columns
  You can export and import tables with encrypted columns using the `ENCRYPTION=ENCRYPTED_COLUMNS_ONLY` setting.
- Using Oracle Data Pump to Encrypt Entire Dump Sets
  Oracle Data Pump can encrypt entire dump sets, not just Transparent Data Encryption columns.
- Using Oracle Data Pump with Encrypted Data Dictionary Data
  Oracle Data Pump operations provide protections for encrypted passwords and other encrypted data.

**Parent topic:** Using Transparent Data Encryption with Other Oracle Features

#### 9.1.1 About Exporting and Importing Encrypted Data

You can use Oracle Data Pump to export and import tables that have encrypted columns.

For both software and external keystores, the following points are important when you must export tables containing encrypted columns:

- Sensitive data should remain unintelligible during transport.

- Authorized users should be able to decrypt the data after it is imported at the destination.

When you use Oracle Data Pump to export and import tables containing encrypted columns, it uses the `ENCRYPTION` parameter to enable encryption of data in dump file sets. The `ENCRYPTION` parameter allows the following values:

- `ENCRYPTED_COLUMNS_ONLY`: Writes encrypted columns to the dump file set in encrypted format

- `DATA_ONLY`: Writes all of the data to the dump file set in encrypted format

- `METADATA_ONLY`: Writes all of the metadata to the dump file set in encrypted format

- `ALL`: Writes all of the data and metadata to the dump file set in encrypted format

- `NONE`: Does not use encryption for dump file sets

**Parent topic:** How Transparent Data Encryption Works with Export and Import Operations

#### 9.1.2 Exporting and Importing Tables with Encrypted Columns

You can export and import tables with encrypted columns using the `ENCRYPTION=ENCRYPTED_COLUMNS_ONLY` setting.

1.  Ensure that the keystore is open before you attempt to export tables containing encrypted columns.

    In a multitenant environment, if you are exporting data in a pluggable database (PDB), then ensure that the wallet is open in the PDB. If you are exporting into the root, then ensure that the wallet is open in the root.

    To find if the keystore is open, query the `STATUS` column of the `V$ENCRYPTION_WALLET` view. If you must open the keystore, then run the following SQL statement:

        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN
        IDENTIFIED BY software_keystore_password
        [CONTAINER = ALL | CURRENT];

    The `software_keystore_password` setting is the password for the keystore. The keystore must be open because the encrypted columns must be decrypted using the [TDE table key](glossary.md)s, which requires access to the TDE master encryption key. The columns are reencrypted using a password, before they are exported.

2.  Run the `EXPDP` command, using the `ENCRYPTION_PASSWORD` parameter to specify a password that is used to encrypt column data in the export dump file set.

    The following example exports the `employee_data` table. The `ENCRYPTION_PWD_PROMPT = YES` setting enables you to prompt for the password interactively, which is a recommended security practice.

        expdp hr TABLES=employee_data DIRECTORY=dpump_dir
        DUMPFILE=dpcd2be1.dmp ENCRYPTION=ENCRYPTED_COLUMNS_ONLY
        ENCRYPTION_PWD_PROMPT = YES

        Password: password_for_hr

3.  To import the exported data into the target database, ensure that you specify the same password that you used for the export operation, as set by the `ENCRYPTION_PASSWORD` parameter.

    The password is used to decrypt the data. Data is reencrypted with the new TDE table keys generated in the target database. The target database must have the keystore open to access the TDE master encryption key. The following example imports the `employee_data` table:

        impdp hr TABLES=employee_data DIRECTORY=dpump_dir
        DUMPFILE=dpcd2be1.dmp
        ENCRYPTION_PWD_PROMPT = YES

        Password: password_for_hr

**Parent topic:** How Transparent Data Encryption Works with Export and Import Operations

#### 9.1.3 Using Oracle Data Pump to Encrypt Entire Dump Sets

Oracle Data Pump can encrypt entire dump sets, not just Transparent Data Encryption columns.

While importing, you can use either the password or the keystore TDE master encryption key to decrypt the data. If the password is not supplied, then the TDE master encryption key in the keystore is used to decrypt the data. The keystore must be present and open at the target database. The open keystore is also required to reencrypt column encryption data at the target database.

You can use the `ENCRYPTION_MODE=TRANSPARENT` setting to transparently encrypt the dump file set with the TDE master encryption key stored in the keystore. A password is not required in this case. The keystore must be present and open at the target database, and it must contain the TDE master encryption key from the source database for a successful decryption of column encryption metadata during an import operation.

The open keystore is also required to reencrypt column encryption metadata at the target database. If a keystore already exists on the target database, then you can export the current TDE master encryption key from the keystore of the source database and import it into the keystore of the target database.

- Use the `ENCRYPTION_MODE` parameter to specify the encryption mode. `ENCRYPTION_MODE=DUAL` encrypts the dump set using the TDE master encryption key stored in the keystore and the password provided.

For example, to use dual encryption mode to export encrypted data:

    expdp hr DIRECTORY=dpump_dir1
    DUMPFILE=hr_enc.dmp
    ENCRYPTION=all
    ENCRYPTION_PASSWORD=encryption_password
    ENCRYPTION_PWD_PROMPT=yes
    ENCRYPTION_ALGORITHM=AES256
    ENCRYPTION_MODE=dual

    Password: password_for_hr
    Encryption Password: password_for_encryption

**Related Topics**

- [Exporting and Importing the TDE Master Encryption Key](managing-keystore-and-tde-master-encryption-key.md)
- [Oracle Database Utilities](../sutil/oracle-data-pump-overview.md)
- [Creating an Encrypted Column in an External Table](configuring-transparent-data-encryption.md)

**Parent topic:** How Transparent Data Encryption Works with Export and Import Operations

#### 9.1.4 Using Oracle Data Pump with Encrypted Data Dictionary Data

Oracle Data Pump operations provide protections for encrypted passwords and other encrypted data.

When you enable the encryption of fixed-user database passwords in a source database, then an Oracle Data Pump export operation dump stores a known invalid password for the database link password. This password is in place instead of the encrypted password that the export operation extracts from the database. An `ORA-39395: Warning: object <database link name> requires password reset after import` warning message is displayed as a result. If you import data into an Oracle Database 18c or later database, then this same warning appears when the database link object with its invalid password is created in the target database. When this happens, you must reset the database link password, as follows:

    ALTER DATABASE LINK database_link_name CONNECT TO schema_name IDENTIFIED BY password;

To find information about the database link, you can query the `V$DBLINK` dynamic view.

When the encryption of fixed-user database passwords has been disabled in a source database, then there are no changes to Data Pump. The obfuscated database link passwords are exported and imported as in previous releases.

In this case, Oracle recommends the following:

- Set the `ENCRYPTION_PASSWORD` parameter on the `expdp` command so that you can further protect the obfuscated database link passwords.

- Set the `ENCRYPTION_PWD_PROMPT` parameter to `YES` so that the password can be entered interactively from a prompt, instead of being echoed on the screen.

Both the `ENCRYPTION_PASSWORD` and the `ENCRYPTION_PWD_PROMPT` parameters are available in import operations. `ENCRYPTION_PWD_PROMPT` is only available with the `expdp` and `impdp` command-line clients, whereas `ENCRYPTION_PASSWORD` is available in both the command-line clients and the `DBMS_DATAPUMP` PL/SQL package.

During an import operation, whether the keystore is open or closed affects the behavior of whether or not an encryption password must be provided. If the keystore was open during the export operation and you provided an encryption password, then you do not need to provide the password during the import operation. If the keystore is closed during the export operation, then you must provide the password during the import operation.

**Related Topics**

- [Oracle Database Reference](../refrn/V-DBLINK.md)
- [Oracle Database Utilities](../sutil/oracle-data-pump-export-utility.md)

**Parent topic:** How Transparent Data Encryption Works with Export and Import Operations

### 9.2 How Transparent Data Encryption Works with Oracle Data Guard

An Oracle Data Guard primary database and secondary secondary database can share both a TDE wallet and an external keystore.

- About Using Transparent Data Encryption with Oracle Data Guard
  For both TDE wallets and external keystores, Oracle Data Guard supports Transparent Data Encryption (TDE).
- Encryption of Tablespaces in an Oracle Data Guard Environment
  You can control tablespace encryption in the primary and standby databases in an Oracle Data Guard environment.
- Configuring TDE and Oracle Key Vault in an Oracle Data Guard Environment
  You can configure Oracle Data Guard in a multitenant environment so that it can work with TDE wallets and Oracle Key Vault.
- Configuring Wallet-Based Transparent Data Encryption in Oracle Data Guard
  You can configure wallet-based Transparent Data Encryption (TDE) in an Oracle Data Guard environment.
- Migrating a TDE Wallet in an Oracle Data Guard Environment to Oracle Key Vault
  After you have configured TDE wallet-based Transparent Data Encryption (TDE) in an Oracle Data Guard environment, you can migrate primary and standby databases to Oracle Key Vault, without downtime.
- Isolating an Encrypted PDB in an Oracle Data Guard Environment
  To isolated PDB's in an Oracle Data Guard environment, you must manually perform the configuration.

**Parent topic:** Using Transparent Data Encryption with Other Oracle Features

#### 9.2.1 About Using Transparent Data Encryption with Oracle Data Guard

For both TDE wallets and external keystores, Oracle Data Guard supports Transparent Data Encryption (TDE).

If the primary database uses TDE, then each standby database in a Data Guard configuration must have a copy of the encryption keystore from the primary database. If you reset the TDE master encryption key in the primary database, then you must copy the keystore from the primary database that contains the TDE master encryption key to each standby database.

Note the following:

- Re-key operations with wallet-based TDE will cause the Managed Recovery Process (MRP) on the standby databases to fail because the new TDE master encryption key is not yet available. In order to circumvent this problem, you can split the `set key` command into the `create key` and `use key` commands. After each command, copy the wallets to the standby database and 'force open' the keystore.

- Encrypted data in log files remains encrypted when data is transferred to the standby database. Encrypted data also stays encrypted during transit.

**Related Topics**

- [Merging TDE Wallets](managing-keystore-and-tde-master-encryption-key.md)
- Configuring Wallet-Based Transparent Data Encryption in Oracle Data Guard

**Parent topic:** How Transparent Data Encryption Works with Oracle Data Guard

#### 9.2.2 Encryption of Tablespaces in an Oracle Data Guard Environment

You can control tablespace encryption in the primary and standby databases in an Oracle Data Guard environment.

- About the Encryption of Tablespace in an Oracle Data Guard Environment
  In an Oracle Data Guard environment, you can control the automatic encryption of tablespaces in both the primary and standby databases, for on-premises and Oracle Cloud Infrastructure (OCI) environments.
- Configuring the Encryption of Tablespaces in an Oracle Data Guard Environment
  To configure the hybrid encryption of tablespaces, you must set the `TABLESPACE_ENCRYPTION` initialization parameter.

**Parent topic:** How Transparent Data Encryption Works with Oracle Data Guard

##### 9.2.2.1 About the Encryption of Tablespace in an Oracle Data Guard Environment

In an Oracle Data Guard environment, you can control the automatic encryption of tablespaces in both the primary and standby databases, for on-premises and Oracle Cloud Infrastructure (OCI) environments.

To control the encryption of new tablespaces, you set the `TABLESPACE_ENCRYPTION` initialization parameter.

Oracle recommends that you encrypt primary databases. However, because encryption requirements may vary depending on the site, you can use the `TABLESPACE_ENCRYPTION` parameter to configure a mixed encryption environment for on-premises and in-Cloud environments.

Note the following about using the `TABLESPACE_ENCRYPTION` parameter:

- Redo decryption takes place at the redo transport level.

- For Oracle Database 19.16 and later, if you do not have an Advanced Security Option (ASO) license, which includes Transparent Data Encryption, then you can configure an un-encrypted on-premises primary database to have an encrypted standby database in Oracle Cloud Infrastructure (OCI). Even after a role transition (planned or unplanned), the new on-premises standby database remains un-encrypted, while the primary database in OCI is encrypted. See the Oracle Database Product Management YouTube video [Hybrid Oracle Data Guard without Transparent Data Encryption (TDE) License](https://www.youtube.com/watch?v=HsnOtef87mM).

  For releases earlier than 19.16, "split-TDE" deployments are complicated to implement, require constant manual intervention on primary and standby databases, and require an ASO license for the un-encrypted on-premises database.

- If the `ENCRYPT_NEW_TABLESPACES` setting that you choose conflicts with the `TABLESPACE_ENCRYPTION` setting, then `TABLESPACE_ENCRYPTION` takes precedence.

- You must set `TABLESPACE_ENCRYPTION` in the CDB root, not in any PDBs.

- The default `TABLESPACE_ENCRYPTION` setting for OCI databases is `AUTO_ENABLE`. The setting is mandatory, and any changes to it are ignored.

- The default `TABLESPACE_ENCRYPTION` setting for on-premises databases is `MANUAL_ENABLE`.

In an Oracle Data Guard environment that uses on-premises databases and Oracle Database in the Cloud (ODBC) or Oracle Exadata Cloud (ExaCS), you can configure tablespace encryption in either of the following scenarios:

- Encrypt the tablespace in the Cloud standby database but not in the on-premises primary database: When an unencrypted on-premises primary database creates an unencrypted tablespace, adds a data file, or updates a table, then the redo is not encrypted. However, when the encrypted Cloud standby database applies the redo, it ensures that the tablespace or data file is created, or that the block is updated, and are all encrypted in the Cloud. After the switchover operation, if the encrypted Cloud primary database adds an implicitly encrypted tablespace or data file, or updates a table, then the tablespace is encrypted. The unencrypted on-premises standby database must decrypt the redo, create an unencrypted tablespace or data file, and then ensure that the block is not encrypted on-premises.
- Encrypt the tablespace in the Cloud primary database but not in the on-premises standby database: When an encrypted Cloud primary database creates an implicitly encrypted tablespace, adds a data file, or updates a table, then the redo is also encrypted. The unencrypted on-premises standby database must decrypt the redo and ensure that the tablespace and data file are created, or the updated files are all unencrypted. After the switchover operation, if the unencrypted on-premises primary database adds an unencrypted tablespace or data file, or updates a table, then the redo is not encrypted. The encrypted Cloud standby database adds an encrypted tablespace or data file, and then ensures that the block is encrypted in the Cloud.

For example, if you want to use `TABLESPACE_ENCRYPTION` in a configuration that followed the best practice of having both on-premises and OCI databases encrypted, then you would set `TABLESPACE_ENCRYPTION` to `AUTO_ENABLE` for both the on-premises and OCI databases. Alternatively, if the on-premises database is not encrypted in a hybrid disaster recovery configuration with ODBC or Oracle ExaCS, for example, you could set `TABLESPACE_ENCRYPTION` to `DECRYPT_ONLY`. The OCI database is set to `AUTO_ENABLE` by default.

See also the video [Hybrid Oracle Data Guard without Transparent Data Encryption (TDE) License](https://www.youtube.com/watch?v=HsnOtef87mM).

**Parent topic:** Encryption of Tablespaces in an Oracle Data Guard Environment

##### 9.2.2.2 Configuring the Encryption of Tablespaces in an Oracle Data Guard Environment

To configure the hybrid encryption of tablespaces, you must set the `TABLESPACE_ENCRYPTION` initialization parameter.

1.  Log in to the primary or the standby database instance by using SQL\*Plus with the `SYSDBA` administrative privilege.
    In a multitenant environment, this command logs you in to the CDB root. You cannot set this parameter in a pluggable database (PDB).
2.  Set the `TABLESPACE_ENCRYPTION` initialization parameter as follows:
        ALTER SYSTEM SET TABLESPACE_ENCRYPTION = 'value' SCOPE = SPFILE SID = '*';

    In this specification, replace `value` with one of the following settings:

    - `AUTO_ENABLE` encrypts all new tablespaces if the database is licensed for Oracle Advanced Security. This is the default setting for Cloud databases.

      Note the following:

      - If an existing tablespace is not encrypted, then the database writes a warning to the alert log.
      - Encrypted tablespaces cannot be converted to unencrypted tablespaces. For Oracle Database 19.16, in all Oracle Cloud Infrastructure (OCI) databases (including BaseDB, ExaDB-D, ExaDB-D@Azure, ExaDB-C@C, and ADB-C@C), encrypted tablespaces cannot be converted to unencrypted tablespaces.
      - Because all tablespaces must be encrypted in the Cloud, setting this parameter to `DECRYPT_ONLY` or `MANUAL_ENABLE` on a Cloud database will be ignored and the Cloud database will behave as if the setting is `AUTO_ENABLE`.
      - In the primary database, this setting encrypts the new tablespace with an encryption key.
      - In a standby database, this setting adds a key to the new tablespace and encrypts all blocks.

    - `DECRYPT_ONLY` prevents new tablespaces from being encrypted. Use this setting if you do not have a TDE license for your on-premises primary database that you want to protect with an encrypted standby database in OCI. See the Hybrid Oracle Data Guard without Transparent Data Encryption (TDE) License video. This setting is designed for sites that do not have the Advanced Security Option.

      Note the following:

      - If an existing tablespace is encrypted, then the database writes a warning to the alert log.
      - Unencrypted tablespaces cannot be changed to encrypted tablespaces.

    - `MANUAL_ENABLE` enables you to selectively encrypt tablespaces if the database is licensed for Oracle Advanced Security. This is the default for both on-premises primary and standby databases and it uses the same behavior as in previous Oracle Database releases.

    In an Oracle Real Application Clusters (Oracle RAC) environment, set `TABLESPACE_ENCRYPTION` to the same value for all instances of the primary database, and for all instances of the standby database. Because the default value is `MANUAL_ENABLE`, Oracle recommends that during an upgrade to the current release of Oracle Database, until all database instances are rolled over and upgraded, to not change `TABLESPACE_ENCRYPTION` for any of these database instances. When all the database instances are upgraded, then you can modify the `TABLESPACE_ENCRYPTION` parameter.
3.  Depending on how you set `TABLESPACE_ENCRYPTION`, do the following:
    - `TABLESPACE_ENCRYPTION=AUTO_ENABLE`:
      - Set the master encryption key on the primary database for the root, if you have not done so already.
      - Set master encryption keys on all the PDBs associated with this root, if you have not done so already.
      - Copy the wallet from the primary database to the standby database.
    - `TABLESPACE_ENCRYPTION=DECRYPT`: Set the master encryption keys on the primary database for the root and all the PDBs, and then copy the wallet to the standby database before creating any new tablespaces.

When both databases are on-premises, you can have primary and standby settings in pairings of the `MANUAL_ENABLE` and `DECRYPT_ONLY` settings. For example, you could set `MANUAL_ENABLE` on the standby database and `DECRYPT_ONLY` on the primary database. In a `DECRYPT_ONLY` (primary) and `MANUAL_ENABLE` (standby) pairing, you must manually encrypt the database on the standby by using TDE offline conversion.

Note the following with regard to rekey operations:

- Modifying the `TABLESPACE_ENCRYPTION` parameter does not affect master key rotation operations.

  When a tablespace key rotation is performed on the primary database, then the standby database will attempt to rotate the key for the tablespace as well. However, if the standby tablespace is unencrypted and does not have a key, then it will generate an error because there is no key to regenerate. If the standby tablespace is unencrypted but it has inherited a key from primary because of the `DECRYPT_ONLY` setting, then the key will be rotated. In either case, it does not affect the unencrypted tablespace.

- Both the master encryption key and the tablespace key rotation can only be performed on the primary database.

**Related Topics**

- [Encryption Conversions for Existing Offline Tablespaces](configuring-transparent-data-encryption.md)
- [Configuring a Software Keystore for Use in United Mode](managing-keystores-encryption-keys-in-united-mode.md)
- [Configuring a TDE Wallet and TDE Master Encryption Key in Isolated Mode](managing-keystores-encryption-keys-in-isolated-mode.md)

**Parent topic:** Encryption of Tablespaces in an Oracle Data Guard Environment

#### 9.2.3 Configuring TDE and Oracle Key Vault in an Oracle Data Guard Environment

You can configure Oracle Data Guard in a multitenant environment so that it can work with TDE wallets and Oracle Key Vault.

The following scenario shows the configuration with Oracle Key Vault in a single-instance, multitenant Oracle Data Guard environment with one physical standby database. The version for the primary and standby databases must be release 19.6 or later. To complete this procedure, you must perform each step in the sequence shown. After you complete the procedure, Oracle Data Guard will use Oracle Key Vault for TDE key management exclusively, and there will be no TDE wallet on your database servers. Oracle recommends that you monitor the alert logs of both primary and standby databases.

1.  On both the primary and standby databases, execute the `opatch lspatches` command to check the patch release.
        $ORACLE_HOME/OPatch/opatch lspatches

    Output similar to the following appears:

        31281355;Database Release Update : 19.7.0.0.200414 (30869156)
        29585399;OCW RELEASE UPDATE 19.3.0.0.0 (29585399)
2.  Download the Oracle Key Vault deployment script that the Oracle Key Vault administrators prepared to enable database administrators to automatically register their Oracle databases with Oracle Key Vault.
    [Oracle Key Vault RESTful Services Administrator's Guide ](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/asoag&id=OKVRF-GUID-578494A8-CF4A-41E8-9614-C54433E3BE55) has an example of how to create a script to automatically enroll Oracle databases as endpoints. The deployment scripts reside on a shared file system from which database administrators can download. There are two different versions of these deployment scripts. The `primary.zip` file is for the primary database, and the `secondary.zip` file is for all standby databases. You can use these scripts for an Oracle Data Guard or an Oracle RAC environment.
    Another component that the Oracle Key Vault administrators prepare and add to the deployment script is a configuration file that contains all details for the deployment scripts to connect to Oracle Key Vault.
3.  Copy the two deployment scripts (`primary.zip` and `secondary.zip`) that an Oracle Key Vault administrator created for database administrators to download from a shared location.
    1.  Copy the `primary.zip` file to the primary database.
            $ scp user@ip_address:/path/to/file/primary.zip .
    2.  Copy the `secondary.zip` file to the standby database.
            $ scp user@ip_address:/path/to/file/secondary.zip .
4.  On their respective servers, extract the zip files.
        $ unzip primary.zip

        $ unzip secondary.zip
5.  Execute the `primary-run-me.sh` and `secondary-run-me.sh` scripts, which contain the commands for the RESTful API to execute in Oracle Key Vault.
    The Oracle Key Vault RESTful services will execute these commands in order to register this database in Oracle Key Vault with unique wallet and endpoint names.
    1.  Primary database: For example:
            $ more primary-run-me.sh

            #!/bin/bash
            export EP_NAME=${ORACLE_SID^^}_on_$(hostname -s)
            export WALLET_NAME=${ORACLE_SID^^}
            curl -Ok --tlsv1.2 https://Oracle_Key_Vault_IP_address:5695/okvrestclipackage.zipp
            unzip -oj okvrestclipackage.zip lib/okvrestcli.jar -d ./lib
            cat > /home/oracle/deploy-primary.sh  << EOF
            #!/bin/bash
            mkdir -pv ${ORACLE_BASE}/product/okv
            okv manage-access wallet create --wallet ${WALLET_NAME} --unique FALSE
            okv admin endpoint create --endpoint ${EP_NAME} --description "$(hostname -f), $(hostname -i)"
                --type ORACLE_DB --platform LINUX64 --subgroup "USE CREATOR SUBGROUP" --unique FALSE --strict-ip-check TRUE
            okv manage-access wallet set-default --wallet ${WALLET_NAME} --endpoint ${EP_NAME}
            expect << _EOF
                set timeout 120
                spawn okv admin endpoint provision --endpoint ${EP_NAME} --location ${ORACLE_BASE}/product/okv --auto-login FALSE
                expect "Enter Oracle Key Vault endpoint password: "
                send "change-on-install\r"
                expect eof
            _EOF
            EOF
    2.  Standby database: For example:
            $ more secondary-run-me.sh

            $ more run-me.sh
            #!/bin/bash
            export EP_NAME=${ORACLE_SID^^}_on_$(hostname -s)
            export WALLET_NAME=${ORACLE_SID^^}
            curl -Ok --tlsv1.2 https://Oracle_Key_Vault_IP_address:5695/okvrestclipackage.zip
            unzip -oj okvrestclipackage.zip lib/okvrestcli.jar -d ./lib
            cat > /home/oracle/deploy-standby.sh << EOF
            #!/bin/bash
            okv admin endpoint create --endpoint ${EP_NAME} --description "$(hostname -f) $(hostname -i)" --subgroup "USE CREATOR SUBGROUP" --unique FALSE
            okv admin endpoint update --endpoint ${EP_NAME} --strict-ip-check TRUE
            okv manage-access wallet set-default --wallet ${WALLET_NAME} --endpoint ${EP_NAME}
            expect << _EOF
                set timeout 120
                spawn okv admin endpoint provision --endpoint ${EP_NAME} --location /etc/ORACLE/KEYSTORES/${ORACLE_UNQNAME^^}/okv --auto-login FALSE
                expect "Enter Oracle Key Vault endpoint password: "
                send "change-on-install\r"
                expect eof
            _EOF
            EOF
6.  Create the following directories on the primary database and the standby database.
    For example:
        $ mkdir -pv /u01/opt/oracle/product/okv
        $ mkdir -pv /u01/opt/oracle/product/tde
        $ mkdir -pv /u01/opt/oracle/product/tde_seps

    In this specification:

    - The `/u01/opt/oracle/product` directory will be defined as `WALLET_ROOT` in a later step.
    - `/u01/opt/oracle/product/okv` is the installation directory for the Oracle Key Vault client software. Depending on how the `TDE_CONFIGURATION` parameter is set, the Oracle Database will look for the Oracle Key Vault client software in `wallet_root/okv`.
    - `/u01/opt/oracle/product/tde` will store an auto-login wallet, which only contains the future Oracle Key Vault password, enabling an auto-login Oracle Key Vault configuration. Depending on how `TDE_CONFIGURATION` is set, the Oracle Database will look for the TDE wallet or an auto-open wallet for Oracle Key Vault, in `wallet_root/tde`.
    - `/u01/opt/oracle/product/tde_seps` will store an auto-login wallet, which only contains the future Oracle Key Vault password. This will hide the Oracle Key Vault password from the SQL\*Plus command line and potentially from the database administrator to enforce separation of duties between Oracle database administrators and Oracle Key Vault administrators.
7.  Execute the RESTful API on the primary database first, because the deployment script on the standby databases depends on the presence of the shared virtual wallet in Oracle Key Vault that the script on the primary database creates.
    - Primary database:

          $ ./deploy-primary.sh

    - Standby databases:

          $ ./deploy-standby.sh
8.  On the primary and standby databases, execute the `root.sh` script to deploy the PKCS#11 library.
        # /u01/opt/oracle/product/okv/bin/root.sh

    The following output should appear:

        Creating directory: /opt/oracle/extapi/64/hsm/oracle/1.0.0/
        Copying PKCS library to /opt/oracle/extapi/64/hsm/oracle/1.0.0/
        Setting PKCS library file permissions
9.  Execute the `okvutil changepwd` command to change the password for the wallet that you installed, starting from the primary database and then to the standby.
    Because all database administrators downloaded the same deployment script, all databases have the same password into Oracle Key Vault. This step enables each database to have a unique password.
        $ /u01/opt/oracle/product/okv/bin/okvutil changepwd -t wallet -l /u01/opt/oracle/product/okv/ssl/

        Enter wallet password: default_password
        Enter new wallet password: Oracle_Key_Vault_password
        Confirm new wallet password: Oracle_Key_Vault_password
        Wallet password changed successfully
10. On the primary and standby databases, execute the following statements.
    1.  Execute the following statement to add the Oracle Key Vault password as a secret into an auto-open wallet to replace the Oracle Key Vault password in the SQL\*Plus command line with `EXTERNAL STORE`.
            ADMINISTER KEY MANAGEMENT ADD SECRET 'Oracle_Key_Vault_password'
            FOR CLIENT 'OKV_PASSWORD'
            TO LOCAL AUTO_LOGIN KEYSTORE '/u01/opt/oracle/product/tde_seps';
    2.  Execute the following statement to add the Oracle Key Vault password as a secret into an auto-open wallet to enable auto-open Oracle Key Vault.
            ADMINISTER KEY MANAGEMENT ADD SECRET 'Oracle_Key_Vault_password'
            FOR CLIENT 'OKV_PASSWORD'
            TO LOCAL AUTO_LOGIN KEYSTORE '/u01/opt/oracle/product/tde';

        If you are using a release earlier than Oracle Database release 19.13, then use `HSM_PASSWORD`, not `OKV_PASSWORD`.
    3.  Optionally, if patch 30398099 is installed, then change the database default algorithm from `AES128` to either `AES192` or `AES256`.
        Patch 30398099 has been integrated into the April 2021 RU for Oracle Database release 19c (19.11), so that this functionality is available without extra patches. Note that the following parameter is preceded by an underscore.
            ALTER SYSTEM SET "_tablespace_encryption_default_algorithm" = 'AES256' SCOPE = BOTH;
    4.  Configure the primary and standby databases to always encrypt new tablespaces, depending on which release of Oracle Database 19c that you are using:
        - For Oracle Database 19.16 and later, run the following `ALTER SYSTEM` statement:

              ALTER SYSTEM SET TABLESPACE_ENCRYPTION = 'value' SCOPE = SPFILE SID = '*';

        - For Oracle Database 19.15 and earlier, run this `ALTER SYSTEM` statement:

              ALTER SYSTEM SET ENCRYPT_NEW_TABLESPACES = ALWAYS SCOPE = BOTH SID = '*';
    5.  In the primary and standby databases, define the `WALLET_ROOT` static initialization parameter:
            ALTER SYSTEM SET WALLET_ROOT = '/u01/opt/oracle/product' SCOPE = SPFILE;
    6.  Restart the primary and standby databases so that the preceding `ALTER SYSTEM SET WALLET_ROOT` and `ALTER SYSTEM SET TABLESPACE_ENCRYPTION` statements take effect.
    7.  After the database restarts, configure TDE to use Oracle Key Vault as the first keystore and the auto-open TDE wallet in `WALLET_ROOT/tde` as the secondary TDE wallet.
        Execute the following statement in both the primary and standby databases:
            ALTER SYSTEM SET TDE_CONFIGURATION = "KEYSTORE_CONFIGURATION=OKV|FILE" SCOPE = BOTH;
11. In the primary database, create your first TDE master encryption keys in Oracle Key Vault.
    Check the `alert.log` of the standby database. The managed recovery process (MRP) should not be stopped, since the standby database finds the correct master key in the shared virtual wallet in Oracle Key Vault.
    1.  Primary root container: Set the first master encryption key.
        For all `ADMINISTER KEY MANAGEMENT` statements that do not change the TDE configuration, the password will be replaced by `EXTERNAL STORE`. This enables separation of duties between the database administrators and the Oracle Key Vault administrators because the Oracle Key Vault administrators do not need to share the Oracle Key Vault password with the database administrators.

            sqlplus sys as syskm
            Enter password: password

            ADMINISTER KEY MANAGEMENT SET KEY FORCE KEYSTORE IDENTIFIED BY EXTERNAL STORE CONTAINER = CURRENT;
    2.  All primary PDBs: Set the first, tagged, master key for each open PDB. The benefit of tagging the PDB keys is that they can later be easily identified to belong to a certain PDB.
            SELECT ' ADMINISTER KEY MANAGEMENT SET KEY
            USING TAG '''||UPPER(SYS_CONTEXT('USERENV', 'CON_NAME'))||' '||TO_CHAR (SYS_EXTRACT_UTC (SYSTIMESTAMP),
            'YYYY-MM-DD HH24:MI:SS"Z"')||''' FORCE KEYSTORE IDENTIFIED BY EXTERNAL STORE;'
            AS "SET KEY COMMAND" FROM DUAL;
    3.  Execute the generated output of this `SELECT` statement.
        For example:
            ADMINISTER KEY MANAGEMENT SET KEY
            USING TAG 'pdb_name date time'
            FORCE KEYSTORE IDENTIFIED BY EXTERNAL STORE;
12. Perform the following steps in the root container.
    1.  Encrypt the `USERS`, `SYSTEM`, and `SYSAUX` tablespaces in `CDB$ROOT`.
        For example:
            ALTER TABLESPACE USERS ENCRYPTION ONLINE [USING 'AES256'] ENCRYPT;
            ALTER TABLESPACE SYSAUX ENCRYPTION ONLINE [USING 'AES256'] ENCRYPT;
            ALTER TABLESPACE SYSTEM ENCRYPTION ONLINE ENCRYPT;

        The `SYSTEM` tablespace can only be encrypted with the default algorithm (AES128 if not changed in step 10c).
    2.  Observe the `alert.log` of the standby database to confirm that the `USERS` tablespace there is also encrypted.
13. Encrypt the PDB tablespaces:
    1.  Encrypt the `USERS`, `SYSTEM`, `SYSAUX` and all application tablespaces in the PDBs.
        Encrypting the `TEMP` and `UNDO` tablespaces is optional because data from encrypted tablespaces is tracked and automatically encrypted before being written into `TEMP` or `UNDO`.
            ALTER TABLESPACE USERS ENCRYPTION ONLINE [USING 'algorithm'] ENCRYPT;
            ALTER TABLESPACE SYSTEM ENCRYPTION ONLINE ENCRYPT;
            ALTER TABLESPACE SYSAUX ENCRYPTION ONLINE [USING 'algorithm'] ENCRYPT;

        The `SYSTEM` tablespace can only be encrypted with the database default algorithm, which is `AES128` unless it has been changed in the previous step that you performed on the primary and standby databases. If you want to encrypt the `SYSTEM` tablespace with another algorithm, then you can rekey the `SYSTEM` tablespace, for example: For example:

            ALTER TABLESPACE SYSTEM ENCRYPTION ONLINE USING 'any_supported_algorithm' REKEY;

        Observe the `alert.log` of the standby database to confirm the encryption and rekey operations are applied there as well.
    2.  Optionally, encrypt the `UNDO` and `TEMP` tablespaces.
        For example, to encrypt an `UNDO` tablespace named `UNDOTBS1`:
            ALTER TABLESPACE UNDOTBS1 ENCRYPTION ONLINE [USING 'algorithm'] ENCRYPT;

        You cannot use the `ALTER TABLESPACE` statement to encrypt an existing `TEMP` tablespac. To encrypt a `TEMP` tablespace, you must create a new one and encrypt it. First, extract the DDL that was used to create the original `TEMP` tablespace.

            SELECT DBMS_METADATA.GET_DDL ('TABLESPACE', 'TEMP') FROM DBA_TEMP_FILES;

        Modify the output so that tempfile and tablespace name are different. For example:

            CREATE TEMPORARY TABLESPACE "TEMP_ENC"
            TEMPFILE '/u01/opt/oracle/oradata/${ORACLE_SID}/${PDB-NAME}/temp01_enc.dbf'
            SIZE 146800640 AUTOEXTEND ON NEXT 655360
            MAXSIZE 32767M EXTENT MANAGEMENT LOCAL UNIFORM SIZE 1048576
            ENCRYPTION [USING 'algorithm'] ENCRYPT;

        You only need to add the `ENCRYPTION [USING '``algorithm``'] ENCRYPT` clause if you need to apply an algorithm other than the default. Omitting the `ENCRYPTION [USING '``algorithm``'] ENCRYPT` clause will automatically encrypt the `TEMP` tablespace with the default algorithm.

        Next, make this new encrypted `TEMP` tablespace the default temp tablespace of this PDB, and then drop the old clear-text `TEMP` tablespace.

            ALTER DATABASE DEFAULT TEMPORARY TABLESPACE TEMP_ENC;
            DROP TABLESPACE TEMP INCLUDING CONTENTS AND DATAFILES;
14. Optionally, create a tablespace and table in the primary database PDB.
    When you create the tablespace in the primary database without encryption keywords in that statement. It will be encrypted with `AES128` by default unless the database default algorithm has been changed in an earlier step, when you changed the database default algorithm from `AES128` to either `AES192` or `AES256`.
        CREATE TABLESPACE protected DATAFILE SIZE 50M;

        CREATE TABLE SYSTEM.TEST TABLESPACE protected
        AS SELECT * FROM DBA_OBJECTS;
15. Confirm that you can select from the table that is stored in an encrypted tablespace.
        SELECT COUNT(*), OWNER FROM SYSTEM.TEST
        GROUP BY OWNER
        ORDER BY 1 DESC;
16. On the primary and standby databases, run the following statements in the root:
        SELECT c.name AS PDB_NAME, t.name
        AS TBS_NAME, e.ENCRYPTIONALG
        AS ALG, e.STATUS from v$tablespace t, v$encrypted_tablespaces e, v$containers c
        WHERE e.ts# = t.ts# AND e.con_id = t.con_id and e.con_id = c.con_id order by e.con_id, t.name;

        PDB_NAME        TBS_NAME        ALG     STATUS
        --------------- --------------- ------- -------------------------
        CDB$ROOT        SYSAUX          AES256  NORMAL
        CDB$ROOT        SYSTEM          AES256  NORMAL
        CDB$ROOT        USERS           AES256  NORMAL
        FINPDB19C       PROTECTED01     AES256  NORMAL
        FINPDB19C       SYSAUX          AES256  NORMAL
        FINPDB19C       SYSTEM          AES256  NORMAL
        FINPDB19C       USERS           AES256  NORMAL

    Note that the `TEMP` tablespace is not listed in the output of the standby databases.
17. Optionally, validate the configuration.
    1.  Perform an Oracle Data Guard switchover between the primary and standby databases.
        See [Oracle Data Guard Concepts and Administration](../sbydb/managing-oracle-data-guard-role-transitions.md).
        Perform the following steps in the new primary database.
    2.  Select from the encrypted table in your PDB.
        Because there is an auto-open connection into Oracle Key Vault, the following query does not require that you enter the Oracle Key Vault password.
            SELECT COUNT(*), OWNER FROM SYSTEM.TEST
            GROUP BY OWNER
            ORDER BY 1 DESC;

            24 rows selected.
    3.  Rekey the PDB.
            SELECT ' ADMINISTER KEY MANAGEMENT SET KEY
            USING TAG '''||UPPER(SYS_CONTEXT('USERENV', 'CON_NAME'))||' '||TO_CHAR (SYS_EXTRACT_UTC (SYSTIMESTAMP),
            'YYYY-MM-DD HH24:MI:SS"Z"')||'''
            FORCE KEYSTORE
            IDENTIFIED BY EXTERNAL STORE;'
            AS "RE-KEY COMMAND" FROM DUAL;
    4.  Execute the generated output of this `SELECT` statement.
        For example:
            ADMINISTER KEY MANAGEMENT SET KEY
            USING TAG 'pdb_name date time'
            FORCE KEYSTORE IDENTIFIED BY EXTERNAL STORE;
    5.  Perform another Oracle Data Guard switchover.
        See [Oracle Data Guard Concepts and Administration](../sbydb/managing-oracle-data-guard-role-transitions.md).
    6.  Select from the encrypted table in your PDB.
        Because there is an auto-open connection into Oracle Key Vault, the following query does not require that you enter the Oracle Key Vault password.
            SELECT COUNT(*), OWNER FROM SYSTEM.TEST
            GROUP BY OWNER
            ORDER BY 1 DESC;

            24 rows selected.
    7.  Rekey the PDB.
            SELECT ' ADMINISTER KEY MANAGEMENT SET KEY
            USING TAG '''||UPPER(SYS_CONTEXT('USERENV', 'CON_NAME'))||' '||TO_CHAR (SYS_EXTRACT_UTC (SYSTIMESTAMP),
            'YYYY-MM-DD HH24:MI:SS"Z"')||'''
            FORCE KEYSTORE
            IDENTIFIED BY EXTERNAL STORE;'
            AS "RE-KEY COMMAND" FROM DUAL;
    8.  Execute the generated output of this `SELECT` statement.
        For example:
            ADMINISTER KEY MANAGEMENT SET KEY
            USING TAG 'pdb_name date time'
            FORCE KEYSTORE IDENTIFIED BY EXTERNAL STORE;

**Parent topic:** How Transparent Data Encryption Works with Oracle Data Guard

#### 9.2.4 Configuring Wallet-Based Transparent Data Encryption in Oracle Data Guard

You can configure wallet-based Transparent Data Encryption (TDE) in an Oracle Data Guard environment.

The following scenario shows how to configure software keystore-based TDE in a single-instance, multitenant Oracle Data Guard environment with one physical standby database. The version for the primary and standby databases must be release 19.6 or later. To complete this procedure, you must perform each step in the sequence shown. After you complete this configuration, you can migrate the primary and standby databases from the software keystore to Oracle Key Vault. Oracle recommends that you monitor the alert logs of both primary and standby databases.

1.  In the primary and standby databases, create the directories that are needed for a software keystore-based TDE configuration.
    For example:
        # mkdir -pv /etc/ORACLE/KEYSTORES/finance/tde_seps
        # cd /etc
        # chown -Rv oracle:oinstall ./ORACLE
        # chmod -Rv 700 ./ORACLE
2.  In the CDB root of the primary and standby databases, as a user who has the `ALTER SYSTEM` privilege, run the following statements in SQL\*Plus to set the appropriate parameters.
        ALTER SYSTEM SET TABLESPACE_ENCRYPTION = AUTO_ENABLE SCOPE = SPFILE; --Oracle Database 19.16 or later
        ALTER SYSTEM SET ENCRYPT_NEW_TABLESPACE = ALWAYS SCOPE = BOTH; --Before release 19.16
        ALTER SYSTEM SET WALLET_ROOT = '/etc/ORACLE/KEYSTORES/$ORACLE_SID' SCOPE = SPFILE;
3.  Restart the primary and standby databases.
4.  Set the following parameters in the primary and standby databases:
        ALTER SYSTEM SET "_TABLESPACE_ENCRYPTION_DEFAULT_ALGORITHM" = 'AES256' SCOPE = BOTH;
        ALTER SYSTEM SET TDE_CONFIGURATION = "KEYSTORE_CONFIGURATION=FILE" SCOPE = BOTH;
5.  Configure tablespace encryption.
    1.  On the primary database, as a user with the `SYSKM` privilege, create a password-protected and a (local) auto-open software keystore.
        When you create this keystore, Oracle Database automatically creates the `WALLET_ROOT``/tde` directory.
            ADMINISTER KEY MANAGEMENT CREATE KEYSTORE IDENTIFIED BY tde_software_keystore_password;
            ADMINISTER KEY MANAGEMENT CREATE LOCAL AUTO_LOGIN KEYSTORE FROM KEYSTORE IDENTIFIED BY tde_software_keystore_password;
    2.  Enable separation of duties by hiding the TDE wallet password in another (local) auto-open wallet to replace the keystore password with `EXTERNAL STORE` for those `ADMINISTER KEY MANAGEMENT` commands that do not change the TDE configuration in the primary and all standby databases:
            ADMINISTER KEY MANAGEMENT ADD SECRET 'tde_software_keystore_password'
            FOR CLIENT 'TDE_WALLET'
            TO LOCAL AUTO_LOGIN KEYSTORE '/etc/ORACLE/KEYSTORES/finance/tde_seps';
6.  Set the first key in the `CDB$ROOT` container of the primary database.
        ADMINISTER KEY MANAGEMENT SET KEY FORCE KEYSTORE IDENTIFIED BY EXTERNAL STORE WITH BACKUP CONTAINER = CURRENT;
7.  Log in to each open primary PDB and set the first, tagged key by executing the output of this command:
        SELECT 'ADMINISTER KEY MANAGEMENT SET KEY USING TAG
        '''||UPPER(SYS_CONTEXT('USERENV', 'CON_NAME'))||' '||TO_CHAR
        (SYS_EXTRACT_UTC (SYSTIMESTAMP), 'YYYY-MM-DD HH24:MI:SS"Z"')||'''
        FORCE KEYSTORE IDENTIFIED BY EXTERNAL STORE
        WITH BACKUP;' AS "SET KEY COMMAND";
8.  Copy the software keystores from primary to standby databases.
    The local auto-open software keystore of the primary cannot be opened on the standby, so it is excluded from the copy process. For example:
        $ rsync -rvpt --exclude '*.sso' /etc/ORACLE/KEYSTORES/finance/tde/ standby_host:/etc/ORACLE/KEYSTORES/finance/tde/
9.  On the CDB root of the standby, as a user who has the `SYSKM` administrative privilege, create a local auto-login software keystore:
        ADMINISTER KEY MANAGEMENT CREATE LOCAL AUTO_LOGIN KEYSTORE
        FROM KEYSTORE IDENTIFIED BY tde_keystore_password;
10. As a user with the `ALTER TABLESPACE` privilege, encrypt the `SYSTEM`, `SYSAUX`, and `USERS` tablespaces in the root container database:
        ALTER TABLESPACE USERS ENCRYPTION ONLINE ENCRYPT;
        ALTER TABLESPACE SYSTEM ENCRYPTION ONLINE ENCRYPT;
        ALTER TABLESPACE SYSAUX ENCRYPTION ONLINE ENCRYPT;
11. As a user with the `ALTER TABLESPACE` privilege, encrypt the `SYSTEM`, `SYSAUX`, `USERS`, and all sensitive application tablespaces in the PDB.
        ALTER TABLESPACE USERS ENCRYPTION ONLINE ENCRYPT;
        ALTER TABLESPACE SYSTEM ENCRYPTION ONLINE ENCRYPT;
        ALTER TABLESPACE SYSAUX ENCRYPTION ONLINE ENCRYPT;
12. Optionally, encrypt the `UNDO` and `TEMP` tablespaces in the primary PDBs.
    1.  Perform the following `ALTER TABLESPACE` statement:
            ALTER TABLESPACE UNDOTBS1 ENCRYPTION ONLINE ENCRYPT;
    2.  Create a new encrypted `TEMP` tablespace with the same parameters that were applied to the original `TEMP` tablespace.
        You cannot use the `ALTER TABLESPACE` statement to encrypt an existing `TEMP` tablespace, so you must create a new one.
        First, extract the DDL that was used to create the original `TEMP` tablespace.

            SELECT DBMS_METADATA.GET_DDL ('TABLESPACE', 'TEMP') FROM DBA_TEMP_FILES;

        Second, modify the output so that the tempfile and tablespace names are different. For example:

            CREATE TEMPORARY TABLESPACE "TEMP_ENC"
            TEMPFILE '/u01/opt/oracle/oradata/${ORACLE_SID}/${PDB-NAME}/temp01_enc.dbf'
            SIZE 146800640 AUTOEXTEND ON NEXT 655360
            MAXSIZE 32767M EXTENT MANAGEMENT LOCAL UNIFORM SIZE 1048576
    3.  Make the new encrypted `TEMP` tablespace the default `TEMP` tablespace:
            ALTER DATABASE DEFAULT TEMPORARY TABLESPACE TEMP_ENC;
    4.  Drop the old clear-text `TEMP` tablespace:
            DROP TABLESPACE TEMP INCLUDING CONTENTS AND DATAFILES;
    5.  Rename the new `TEMP` tablesplace.
            ALTER TABLESPACE TEMP_ENC RENAME TO TEMP;
13. Optionally, create a small sample tablespace (which will be encrypted with AES256 even if no `ENCRYPTION` syntax is given), and create a copy of the `DBA_OBJECTS` table in this encrypted sample tablespace.
        CREATE TABLESPACE PROTECTED DATAFILE SIZE 50M;
        CREATE TABLE SYSTEM.TEST TABLESPACE PROTECTED AS SELECT * FROM DBA_OBJECTS;
14. Optionally, select from the encrypted copy of the `DBA_OBJECTS` table.
    For example:
        SELECT OWNER, COUNT(*) FROM SYSTEM.test GROUP BY OWNER ORDER BY 2 DESC;

        24 rows selected.
15. Connect to the CDB root of the primary and standby databases and confirm.
        SELECT C.NAME AS PDB_NAME, T.NAME AS TBS_NAME, E.ENCRYPTIONALG AS ALG, E.STATUS
        FROM V$TABLESPACE T, V$ENCRYPTED_TABLESPACES E, V$CONTAINERS C
        WHERE E.TS# = T.TS# AND E.CON_ID = T.CON_ID AND E.CON_ID = C.CON_ID ORDER BY E.CON_ID, T.NAME;

    Output similar to the following should appear:

        PDB_NAME        TBS_NAME        ALG     STATUS
        --------------- --------------- ------- -------------------------
        CDB$ROOT        SYSAUX          AES256  NORMAL
        CDB$ROOT        SYSTEM          AES256  NORMAL
        CDB$ROOT        USERS           AES256  NORMAL
        FINPDB19C       PROTECTED01     AES256  NORMAL
        FINPDB19C       SYSAUX          AES256  NORMAL
        FINPDB19C       SYSTEM          AES256  NORMAL
        FINPDB19C       USERS           AES256  NORMAL

    The standby does not have a `TEMP` tablespace, so it will not be listed here.
16. Connect to the `dgmgrl` utility on the standby as a user who has the `SYSDG` administrative privilege.
17. Perform a switchover operation.
        DGMGRL> switchover to '<standby_db_name>' wait 5;
18. To confirm the auto-open software keystore functionality, select from encrypted data (for example, the copy of the `DBA_OBJECTS` table in the PDB) of the new primary database after the role switch.
    For example:
        SELECT OWNER, COUNT(*) FROM SYSTEM.test GROUP BY OWNER ORDER BY 2 DESC;

        24 rows selected.
19. Oracle recommends that you create and then use the key. This way, the managed recovery process on the standby database is not interrupted due to unknown TDE master encryption keys. In the new primary PDB, run the following statement:
        ADMINISTER KEY MANAGEMENT CREATE KEY FORCE KEYSTORE IDENTIFIED BY EXTERNAL STORE WITH BACKUP;
20. Copy the software keystore to the standby, excluding the local auto-open keystores, and automatically deleting the obsolete local auto-open keystore on the standby side.
    For example:
        $ rsync -rvpt --exclude '*.sso' --delete-excluded /etc/ORACLE/KEYSTORES/finance/tde/ standby-host:/etc/ORACLE/KEYSTORES/finance/tde/
21. On the standby, re-create a local auto-open software keystore from the updated password-protected keystore so that the new key is immediately available to the standby database when needed.
        ADMINISTER KEY MANAGEMENT CREATE LOCAL AUTO_LOGIN KEYSTORE
        FROM KEYSTORE IDENTIFIED BY tde_keystore_password;
22. Execute the output of the following command:
        SELECT ' ADMINISTER KEY MANAGEMENT
        USE KEY '''||KEY_ID||'''
        USING TAG '''||SYS_CONTEXT('USERENV', 'CON_NAME')||' '||
        TO_CHAR (SYS_EXTRACT_UTC (SYSTIMESTAMP), 'YYYY-MM-DD HH24:MI:SS"Z"')||'''
        FORCE KEYSTORE IDENTIFIED BY EXTERNAL STORE
        WITH BACKUP;' AS "USE KEY COMMAND"
        FROM V$ENCRYPTION_KEYS
        WHERE TAG IS NULL;

    The `USE KEY` clause updates the associations in the software keystore, so the updated password-protected wallet is copied to the standby, again excluding the local auto-open software keystore and deleting the obsolete local auto-open keystore on the receiving standby side, for example, with the following command:

        $ rsync -rvpt --exclude '*.sso' --delete-excluded /etc/ORACLE/KEYSTORES/finance/tde/ standby-host:/etc/ORACLE/KEYSTORES/finance/tde/
23. On the CDB root of the primary, recreate the local auto-login software keystore.
        ADMINISTER KEY MANAGEMENT CREATE LOCAL AUTO_LOGIN KEYSTORE FROM KEYSTORE IDENTIFIED BY tde_keystore_password;
24. Using the `dgmgrl` utility, perform a switchover operation to the standby.
    For example:
        DGMGRL> switchover to '<standby_db_name>' wait 5;
25. Optionally, to confirm the auto-open functionality, select from an encrypted table (for example, the copy of the `DBA_OBJECTS` table).
        SELECT OWNER, COUNT(*) FROM SYSTEM.test GROUP BY OWNER ORDER BY 2 DESC;

        24 rows selected.

**Parent topic:** How Transparent Data Encryption Works with Oracle Data Guard

#### 9.2.5 Migrating a TDE Wallet in an Oracle Data Guard Environment to Oracle Key Vault

After you have configured TDE wallet-based Transparent Data Encryption (TDE) in an Oracle Data Guard environment, you can migrate primary and standby databases to Oracle Key Vault, without downtime.

The following scenario shows how to configure one endpoint for each of the primary and standby databases, and then migrate the primary and standby databases from a TDE wallet to Oracle Key Vault. This scenario uses a single-instance, multitenant Oracle Data Guard environment with one physical standby database. The version for the primary and standby databases must be release 19.6 or later. To complete this procedure, you must perform each step in the sequence shown. See [Oracle Key Vault RESTful Services Administrator's Guide ](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/23&id=OKVRF-GUID-578494A8-CF4A-41E8-9614-C54433E3BE55) for how an Oracle Key Vault administrator can create these files, which are later used by database administrators to automatically onboard their databases into Oracle Key Vault.

1.  Copy the primary deployment script to the primary database host.
    For example:
        $ rsync -v 192.168.1.29:/directory_on_shared_server/OKVdeploy-DG-primary.tgz .
2.  Copy the secondary deployment script to all standby database hosts.
    For example:
        $ rsync -v 192.168.1.29:/directory_on_shared_server/OKVdeploy-DG-standby.tgz .
3.  On the primary and standby database hosts, extract the archive.
        $ tar -xzvf OKVdeploy-DG*
4.  On the primary database, run the `primary-run-me.sh` script.
    This script creates the deployment script (`okv-ep.sh`), which contains unique names for the wallet and endpoint that it creates in Oracle Key Vault for the primary database.
        $ /primary-run-me.sh

          % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                         Dload  Upload   Total   Spent    Left  Speed
        100 3750k  100 3750k    0     0  13.5M      0 --:--:-- --:--:-- --:--:-- 13.5M
        Archive:  okvrestclipackage.zip
          inflating: ./lib/okvrestcli.jar
        #!/bin/bash
        mkdir -pv /etc/ORACLE/KEYSTORES/finance/okv
        okv manage-access wallet create --wallet FINANCE --unique FALSE
        okv admin endpoint create --endpoint FINANCE_on_SanDiego --description "SanDiego.us.oracle.com, 192.168.56.193"
          --subgroup "USE CREATOR SUBGROUP" --unique FALSE --strict-ip-check TRUE
        okv manage-access wallet set-default --wallet FINANCE --endpoint FINANCE_on_SanDiego
        expect << _EOF
            set timeout 120
            spawn okv admin endpoint provision --endpoint FINANCE_on_SanDiego --location /etc/ORACLE/KEYSTORES/finance/okv --auto-login FALSE
            expect "Enter Oracle Key Vault endpoint password: "
            send "change-on-install\r"
            expect eof
        _EOF
5.  On the standby databases, run the `secondary-run-me.sh` script.
    This script creates the deployment script (`okv-ep.sh`), which contains unique names for the endpoint that it creates in Oracle Key Vault for the standby databases. Note that the standby endpoint uses the primary wallet as its default wallet, so that primary and standby databases have access to same key material.
        $ ./secondary-run-me.sh

          % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                         Dload  Upload   Total   Spent    Left  Speed
        100 3750k  100 3750k    0     0  16.0M      0 --:--:-- --:--:-- --:--:-- 16.1M
        Archive:  okvrestclipackage.zip
          inflating: ./lib/okvrestcli.jar
        #!/bin/bash
        mkdir -pv /etc/ORACLE/KEYSTORES/finance/okv
        okv admin endpoint create --endpoint FINANCE_on_Phoenix
          --description "Phoenix.us.oracle.com, 192.168.56.194"
          --subgroup "USE CREATOR SUBGROUP"
          --unique FALSE
          --strict-ip-check TRUE
        okv manage-access wallet set-default --wallet FINANCE --endpoint FINANCE_on_Phoenix
        expect << _EOF
            set timeout 120
            spawn okv admin endpoint provision --endpoint FINANCE_on_Phoenix --location /etc/ORACLE/KEYSTORES/finance/okv --auto-login FALSE
            expect "Enter Oracle Key Vault endpoint password: "
            send "change-on-install\r"
            expect eof
        _EOF
6.  On the primary database host, run the `okv-ep.sh` script.
    This script creates a wallet and endpoint for the primary database in Oracle Key Vault. It makes the wallet the default wallet of that endpoint. The following `okv admin endpoint provision` command downloads and installs the Oracle Key Vault endpoint software into the existing directory, `WALLET_ROOT``/okv`.
        $ ./deploy-OKV.sh

        {
          "result" : "Success",
          "value" : {
            "status" : "PENDING",
            "locatorID" : "87E59AAD-0AAA-4AE8-ADCE-01D283ECE9C4"
          }
        }
        {
          "result" : "Success",
          "value" : {
            "status" : "PENDING",
            "locatorID" : "D13CC460-7BFB-451D-9998-DA387FC45783"
          }
        }
        {
          "result" : "Success"
        }
        spawn okv admin endpoint provision --endpoint finance_on_SanDiego --location /etc/ORACLE/KEYSTORES/finance/okv --auto-login FALSE
        Enter Oracle Key Vault endpoint password:
        {
          "result" : "Success"
        }
7.  On the standby database hosts, run the `okv-ep.sh` script.
    This script creates an endpoint for the standby database in Oracle Key Vault. It makes the primary wallet the default wallet of that endpoint. The following `okv admin endpoint provision` command downloads and installs the Oracle Key Vault endpoint software into the existing directory `WALLET_ROOT``/okv`.
        $ ./deploy-OKV.sh

        {
          "result" : "Success",
          "value" : {
            "status" : "PENDING",
            "locatorID" : "4208FBB5-5FD4-47EE-B3DB-FA8277BAFB84"
          }
        }
        {
          "result" : "Success"
        }
        spawn okv admin endpoint provision --endpoint finance_on_Phoenix --location /etc/ORACLE/KEYSTORES/finance/okv --auto-login FALSE
        Enter Oracle Key Vault endpoint password:
        {
          "result" : "Success"
        }
8.  On the primary and standby database hosts, run the `root.sh` script in the `WALLET_ROOT``/okv/bin`.
    This script deploys the PKCS#11 library into the correct destination directory.
        $ sudo /etc/ORACLE/KEYSTORES/finance/okv/bin/root.sh
9.  On the primary and standby databases, change the default password to a strong password that the database administrator should not know.
    This password is the same for all databases that used the deployment script.
        $ /etc/ORACLE/KEYSTORES/finance/okv/bin/okvutil changepwd -l /etc/ORACLE/KEYSTORES/finance/okv/ssl/ -t wallet

        Enter wallet password: current_endpoint_password
        Enter new wallet password: new_endpoint_password
        Confirm new wallet password: new_endpoint_password
        Wallet password changed successfully
10. Optionally, update the endpoint parameters.
    This step and the next two steps are optional. By default, the persistent cache is a password-protected wallet that is protected with the endpoint password from the preceding step. With the change in steps 10, 11, and 12, the persistent cache will be protected with a random password, which implies that the persistent cache will expire after database shutdown, and needs to be rebuilt after each database restart. Additionally, the persistent cache expiration time is changed to 4 hours, but the persistent cache refresh window is extended to 21 days.
        $ okv admin endpoint update --generate-json-input | jq '.service.options
        |= ({endpoint} | .endpointConfiguration
        |= (.expirePkcs11PersistentCacheOnDatabaseShutdown = "TRUE" | .pkcs11PersistentCacheRefreshWindow = "P21D" | .pkcs11PersistentCacheTimeout = "PT4H"))'
        > ./update-endpoint.json; more ./update-endpoint.json

        {
          "service": {
            "category": "admin",
            "resource": "endpoint",
            "action": "update",
            "options": {
              "endpoint": "#VALUE",
              "endpointConfiguration": {
                "expirePkcs11PersistentCacheOnDatabaseShutdown": "TRUE",
                "pkcs11PersistentCacheRefreshWindow": "P21D",
                "pkcs11PersistentCacheTimeout": "PT4H"
              }
            }
          }
        }
11. Optionally, on the primary, check the status of the endpoints on both the primary and standby databases.
    For example, for a primary with an endpoint called `finance_on_SanDiego` and a standby with an endpoint called `finance_on_Phoenix`:
        $ okv admin endpoint check-status --endpoint finance_on_SanDiego
        $ okv admin endpoint check-status --endpoint finance_on_Phoenix
12. After both endpoints are active, apply and re-use the `update-endpoint.json` file to update all endpoints of the primary and standby databases.:
        $ okv admin endpoint update --from-json ./update-endpoint.json --endpoint finance_on_SanDiego
        $ okv admin endpoint update --from-json ./update-endpoint.json --endpoint finance_on_Phoenix
13. On the primary database host, upload the current and retired master encryption keys from the TDE wallet into the virtual wallet in Oracle Key Vault.
    For example:
        $ /etc/ORACLE/KEYSTORES/finance/okv/bin/okvutil upload -l /etc/ORACLE/KEYSTORES/finance/tde/ -t wallet -g FINANCE -v 3
14. In the root of the primary, using SQL\*Plus, add the Oracle Key Vault password from step 9 into the TDE wallet to enable an auto-open Oracle Key Vault connection.
        ADMINISTER KEY MANAGEMENT ADD SECRET 'Oracle_Key_Vault_password' FOR CLIENT 'OKV_PASSWORD'
        FORCE KEYSTORE IDENTIFIED BY EXTERNAL STORE WITH BACKUP;
15. Copy the updated TDE wallet from the primary database host to the standby database hosts, excluding the local auto-login TDE wallet and deleting the obsolete local auto-login TDE wallet on the standby side.
    For example:
        $ rsync -rvpt --exclude '*.sso' --delete-excluded /etc/ORACLE/KEYSTORES/finance/tde/ standby-host:/etc/ORACLE/KEYSTORES/finance/tde/
16. On the CDB root of the standby, using SQL\*Plus, recreate the local auto-login TDE wallet, and then close it.
        ADMINISTER KEY MANAGEMENT CREATE LOCAL AUTO_LOGIN KEYSTORE
        FROM KEYSTORE IDENTIFIED BY TDE_wallet_password;
        ADMINISTER KEY MANAGEMENT SET KEYSTORE CLOSE CONTAINER = ALL;

    At this stage, the primary and standby databases are ready to be migrated into Oracle Key Vault.
17. In the primary and standby databases, change the `TDE_CONFIGURATION` dynamic parameter to `OKV|FILE`.
        ALTER SYSTEM SET TDE_CONFIGURATION = "KEYSTORE_CONFIGURATION=OKV|FILE" SCOPE = BOTH;
18. Run the `ADMINISTER KEY MANAGEMENT…MIGRATE` command.
    This command decrypts the data encryption keys with the most recent key from the TDE wallet, and re-encrypts them with a new TDE master encryption key that is created in Oracle Key Vault. If this is a container database, then each open PDB will go through these steps. This entails no downtime; the operation takes approximately 10 to 15 seconds for each PDB.
        ADMINISTER KEY MANAGEMENT SET KEY
        IDENTIFIED BY "Oracle_Key_Vault_password"
        FORCE KEYSTORE MIGRATE USING "TDE_wallet_password";
19. Add the Oracle Key Vault password, and remove the old TDE wallet password, from the local auto-login wallet that enables to replace the TDE wallet password on the SQL\*plus command line with `EXTERNAL STORE`.
        ADMINISTER KEY MANAGEMENT ADD SECRET 'Oracle_Key_Vault_password'
        FOR CLIENT "OKV_PASSWORD"
        TO LOCAL AUTO_LOGIN KEYSTORE '/etc/ORACLE/KEYSTORES/finance/tde_seps';

        ADMINISTER KEY MANAGEMENT DELETE SECRET FOR CLIENT 'TDE_WALLET'
        FROM LOCAL AUTO_LOGIN KEYSTORE '/etc/ORACLE/KEYSTORES/finance/tde_seps';
20. Now that primary and standby databases have been migrated to Oracle Key Vault, delete the old wallets (only because you have uploaded the keys into Oracle Key Vault in step 13.
        $ rm -v /etc/ORACLE/KEYSTORES/finance/tde/*
21. On the primary and standby databases, create a local auto-login TDE wallet in `WALLET_ROOT``/tde` that only contains the Oracle Key Vault password to enable an auto-login Oracle Key Vault configuration.
    For example:
        ADMINISTER KEY MANAGEMENT ADD SECRET 'Oracle_Key_Vault_password'
        FOR CLIENT 'OKV_PASSWORD' TO LOCAL AUTO_LOGIN KEYSTORE '/etc/ORACLE/KEYSTORES/finance/tde';
22. Create a tag for each key that is associated with each PDB.
    During migration, Oracle Key Vault created a new key for each PDB, but without a tag. The tag that you create makes it easier to find which key belongs to which PDB. You should give each key a tag that matches the PDB name, and a time stamp.
        SELECT ' ADMINISTER KEY MANAGEMENT SET TAG '''||SYS_CONTEXT('USERENV', 'CON_NAME')||' '||TO_CHAR (SYS_EXTRACT_UTC (ACTIVATION_TIME),
        'YYYY-MM-DD HH24:MI:SS"Z"')||''' FOR '''||KEY_ID||'''
        FORCE KEYSTORE IDENTIFIED BY EXTERNAL STORE;' AS "SET TAG COMMAND"
        FROM V$ENCRYPTION_KEYS
        WHERE CREATOR_PDBNAME = SYS_CONTEXT('USERENV', 'CON_NAME')
        ORDER BY CREATION_TIME DESC FETCH FIRST 1 ROWS ONLY;

**Parent topic:** How Transparent Data Encryption Works with Oracle Data Guard

#### 9.2.6 Isolating an Encrypted PDB in an Oracle Data Guard Environment

To isolated PDB's in an Oracle Data Guard environment, you must manually perform the configuration.

This is because the `ADMINISTER KEY MANAGEMENT` command that is run on the primary does not affect the standby. First, you isolate the PDB in the primary database. The `ADMINISTER KEY MANAGEMENT ISOLATE KEYSTORE` command performs the necessary isolation tasks, such as changing the PDB's `TDE_CONFIGURATION` parameter to `FILE` and moving the key from the united mode wallet to the newly created isolated mode wallet. Next, you must perform these same tasks manually on the standby to complete the isolation process.

1.  If you have not done so you, log in to the CDB root of the primary database, and then isolate the PDB.
        ADMINISTER KEY MANAGEMENT ISOLATE KEYSTORE
        IDENTIFIED BY "new_isolated_pdb_keystore_password"
        FROM ROOT KEYSTORE
        IDENTIFIED BY "root_keystore_password"
        EXTERNAL STORE WITH BACKUP;
2.  Log in to the server where the standby database is configured.
3.  Ensure that there is a directory for the PDB (for example, `$WALLET_ROOT/``pdb_guid``/tde/`).
4.  Connect to the PDB as a user who has the `ALTER SYSTEM` privilege.
5.  Set the `KEYSTORE_CONFIGURATION` parameter for this PDB.
        ALTER SYSTEM SET TDE_CONFIGURATION="KEYSTORE_CONFIGURATION=FILE" SCOPE=BOTH;
6.  At the command line, from the CDB root, copy the wallet (`.p12` and `.sso`) from the primary database to the standby; place this wallet in the `$WALLET_ROOT/``pdb_guid``/tde/` directory.
7.  Close and then re-open the CDB root's wallet.
        ADMINISTER KEY MANAGEMENT SET KEYSTORE CLOSE
        FORCE KEYSTORE IDENTIFIED BY root_wallet_password;

        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN
        FORCE KEYSTORE IDENTIFIED BY root_wallet_password;
8.  Connect to the PDB.
9.  Open the wallet in the PDB.
        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN
        FORCE KEYSTORE IDENTIFIED BY pdb_wallet_password;

**Parent topic:** How Transparent Data Encryption Works with Oracle Data Guard

### 9.3 How Transparent Data Encryption Works with Oracle Real Application Clusters

Oracle Real Application Clusters (Oracle RAC) nodes can share both a TDE wallets and an external keystore.

- About Using Transparent Data Encryption with Oracle Real Application Clusters
  Oracle requires a shared TDE wallet for Oracle Real Application Clusters (Oracle RAC), or a shared common virtual wallet in Oracle Key Vault among cluster instances.
- Configuring TDE in Oracle Real Application Clusters for Oracle Key Vault
  You can migrate encrypted Oracle Real Application Cluster (Oracle RAC) database instances to centralized key management provided by Oracle Key Vault. The migration process has been automated and is integrated with the provisioning workflow in Oracle Exadata Database Service on Cloud@Customer and Oracle Autonomous Database on Dedicated Exadata Infrastructure.

**Parent topic:** Using Transparent Data Encryption with Other Oracle Features

#### 9.3.1 About Using Transparent Data Encryption with Oracle Real Application Clusters

Oracle requires a shared TDE wallet for Oracle Real Application Clusters (Oracle RAC), or a shared common virtual wallet in Oracle Key Vault among cluster instances.

A TDE configuration with Oracle Key Vault uses a network connection from each instance of the database to the external key manager. In Oracle Key Vault, you must create one endpoint for each instance of the Oracle RAC-enabled database, and one virtual wallet for each Oracle RAC-enabled database. Then, make that virtual wallet the default wallet of all endpoints that belong to that database. In an Oracle RAC-enabled Data Guard configuration, all instances (primary and all standby databases) share that one virtual wallet. With this configuration, set key and re-key operations are completely transparent because all participating instances are automatically synchronized. This eliminates the need to manually copy the TDE wallet to each of the other nodes in the cluster.

Oracle does not support the use of individual TDE wallets for each Oracle RAC node. Instead, use shared wallets for TDE in the Oracle RAC environment. This enables all of the instances to access the same shared TDE wallet. If your site uses Oracle Automatic Storage Management Cluster File System (Oracle ACFS), then this is the preferred location for a shared wallet. Directly sharing the wallet in Oracle Automatic Storage Management (Oracle ASM) (for example, `+DATA/$ORACLE_UNQNAME/WALLETS`) is an alternative if Oracle ACFS is not available.

Keystore operations (such as opening or closing the keystore, or rekeying the TDE master encryption key) can be issued on any one Oracle RAC instance. Internally, the Oracle database takes care of synchronizing the keystore context on each Oracle RAC node, so that the effect of the keystore operation is visible to all of the other Oracle RAC instances in the cluster. Similarly, when a TDE master encryption key rekey operation takes place, the new key becomes available to each of the Oracle RAC instances. You can perform other keystore operations, such as exporting TDE master encryption keys, rotating the keystore password, merging keystores, or backing up keystores, from a single instance only.

When using a shared file system, ensure that the `WALLET_ROOT` static system parameter for all of the Oracle RAC instances point to the same shared TDE wallet location, as follows:

    ALTER SYSTEM SET WALLET_ROOT = '+DATA/$ORACLE_UNQNAME' SCOPE = SPFILE SID ='*';

    ALTER SYSTEM SET TDE_CONFIGURATION = "KEYSTORE_CONFIGURATION=FILE" SCOPE = BOTH SID = '*';

**Note:**

- If you have the `ENCRYPTION_WALLET_LOCATION` parameter set, then be aware this parameter is deprecated. Oracle recommends that you use the `WALLET_ROOT` static initialization parameter and `TDE_CONFIGURATION` dynamic initialization parameter instead.
- Storing TDE master encryption keys in individual wallets per Oracle Real Application Clusters (Oracle RAC) instance is not supported. As an alternative, use Oracle Key Vault for centralized key management across your on-premises or Cloud-based database deployments, or Oracle Automatic Storage Management (Oracle ASM), or Oracle ASM Cluster File System (Oracle ACFS) to provide local shared wallets.

**Parent topic:** How Transparent Data Encryption Works with Oracle Real Application Clusters

#### 9.3.2 Configuring TDE in Oracle Real Application Clusters for Oracle Key Vault

You can migrate encrypted Oracle Real Application Cluster (Oracle RAC) database instances to centralized key management provided by Oracle Key Vault. The migration process has been automated and is integrated with the provisioning workflow in Oracle Exadata Database Service on Cloud@Customer and Oracle Autonomous Database on Dedicated Exadata Infrastructure.

The following scenario assumes that you have a multitenant two-node Oracle RAC configuration. In this procedure, you must complete the following steps in the order shown. After you have completed this procedure, the Oracle RAC environment will exclusively use Oracle Key Vault for key management for Transparent Data Encryption. This procedure assumes that you have installed the January 2020 (19.6) or later upgrade for Oracle Database release 19c.

Before you begin, monitor the alert logs of your running Oracle RAC database. The Java version that is included in the default Oracle Database release 19c installation can be used to install the Oracle Key Vault client with the RESTful services.

1.  Download the Oracle Key Vault deployment script that the Oracle Key Vault administrators prepared to enable database administrators to automatically register their Oracle databases with Oracle Key Vault.
    [Oracle Key Vault RESTful Services Administrator's Guide ](https://docs.oracle.com/pls/topic/lookup?ctx=en/database/oracle/oracle-database/19/asoag&id=OKVRF-GUID-578494A8-CF4A-41E8-9614-C54433E3BE55) has an example of how to create a script to automatically enroll Oracle databases as endpoints. The deployment scripts reside on a shared file system from with database administrators can download. There are two different versions of these deployment scripts. One script is for only the first node (which is called lead node in this procedure) and the other script is for all other nodes (which are called secondary nodes in this procedure). You can use these scripts for an Oracle RAC or an Oracle Data Guard environment.
    Another component that the Oracle Key Vault administrators prepare and add to the deployment script is a configuration file that contains all details for the deployment scripts to connect to Oracle Key Vault.
2.  Copy the two deployment scripts (`primary.zip` and `secondary.zip`) that an Oracle Key Vault administrator created for database administrators to download from a shared location.
    1.  Copy the `primary.zip` file to the lead node.
            $ scp user@ip_address:/path/to/file/primary.zip .
    2.  Copy the `secondary.zip` file to each secondary node.
            $ scp user@ip_address:/path/to/file/secondary.zip .
3.  Extract the zip files.
    1.  On the lead node: Extract the `primary.zip` file.
            $ unzip primary.zip
    2.  On the secondary nodes: Extract the `secondary.zip` file.
            $ unzip secondary.zip
4.  Create the following directories on all nodes:
    For example:
        $ mkdir -pv /u01/opt/oracle/product/okv
        $ mkdir -pv /u01/opt/oracle/product/tde
        $ mkdir -pv /u01/opt/oracle/product/tde_seps

    In this specification:

    - The `/u01/opt/oracle/product` directory will be defined as `WALLET_ROOT` in a later step.
    - `/u01/opt/oracle/product/okv` is the installation directory for the Oracle Key Vault client software. Depending on how the `TDE_CONFIGURATION` parameter is set, the Oracle Database will look for the Oracle Key Vault client software in `wallet_root/okv`.
    - `/u01/opt/oracle/product/tde` will store an auto-login wallet, which only contains the future Oracle Key Vault password, enabling an auto-login Oracle Key Vault configuration. Depending on how `TDE_CONFIGURATION` is set, the Oracle Database will look for the TDE wallet or an auto-open wallet for Oracle Key Vault, in `wallet_root/tde`.
    - `/u01/opt/oracle/product/tde_seps` will store an auto-login wallet, which only contains the future Oracle Key Vault password. This will hide the Oracle Key Vault password from the SQL\*Plus command line and potentially from the database administrator to enforce separation of duties between Oracle database administrators and Oracle Key Vault administrators.
5.  Execute the `primary-run-me.sh` and `secondary-run-me.sh` scripts, which contain the commands for the RESTful API to execute in Oracle Key Vault.
    The Oracle Key Vault RESTful services will execute these commands in order to register this database in Oracle Key Vault with unique wallet and endpoint names.
    1.  On the lead node: This script creates a shared wallet (for the lead and all secondary nodes) and an endpoint in Oracle Key Vault, associates this endpoint for the lead node with the shared wallet, and downloads and installs the Oracle Key Vault client into an existing installation directory. With the `WALLET_ROOT` configuration, this directory is `wallet_root``/okv`.
            $ more primary-run-me.sh

            #!/bin/bash
            export EP_NAME=${ORACLE_SID^^}_on_$(hostname -s)
            export WALLET_NAME=${ORACLE_UNQNAME^^}${HOSTNAME//[!0-9]/}
            curl -Ok https://192.168.1.181:5695/okvrestclipackage.zip --tlsv1.2
            unzip -Voj okvrestclipackage.zip lib/okvrestcli.jar -d ./lib
            cat > /home/oracle/deploy-OKV.sh << EOF
            #!/bin/bash
            okv manage-access wallet create --wallet ${WALLET_NAME} --unique FALSE
            okv admin endpoint create --endpoint ${EP_NAME} --description "$(hostname -f) $(hostname -i)" --subgroup "USE CREATOR SUBGROUP" --unique FALSE
            okv admin endpoint update --endpoint ${EP_NAME} --strict-ip-check TRUE
            okv manage-access wallet set-default --wallet ${WALLET_NAME} --endpoint ${EP_NAME}
            expect << _EOF
                set timeout 120
                spawn okv admin endpoint provision --endpoint ${EP_NAME} --location /etc/ORACLE/KEYSTORES/${ORACLE_UNQNAME^^}/okv --auto-login FALSE
                expect "Enter Oracle Key Vault endpoint password: "
                send "change-on-install\r"
                expect eof
            _EOF
            EOF
    2.  Secondary nodes: This script only creates an endpoint for the secondary nodes, associates the endpoint of the secondary nodes with the shared wallet, and downloads and installs the Oracle Key Vault client into the existing installation directory on each secondary node.
            $ more run-me.sh

            #!/bin/bash
            export EP_NAME=${ORACLE_SID^^}_on_$(hostname -s)
            export WALLET_NAME=${ORACLE_UNQNAME^^}${HOSTNAME//[!0-9]/}
            curl -Ok --tlsv1.2 https://<OKV-IP-addr>:5695/okvrestclipackage.zip
            unzip -Voj okvrestclipackage.zip lib/okvrestcli.jar -d ./lib
            cat > /home/oracle/deploy-OKV.sh << EOF
            #!/bin/bash
            okv admin endpoint create --endpoint ${EP_NAME} --description "$(hostname -f) $(hostname -i)" --subgroup "USE CREATOR SUBGROUP" --unique FALSE
            okv admin endpoint update --endpoint ${EP_NAME} --strict-ip-check TRUE
            okv manage-access wallet set-default --wallet ${WALLET_NAME} --endpoint ${EP_NAME}
            expect << _EOF
                set timeout 120
                spawn okv admin endpoint provision --endpoint ${EP_NAME} --location /etc/ORACLE/KEYSTORES/${ORACLE_UNQNAME^^}/okv --auto-login FALSE
                expect "Enter Oracle Key Vault endpoint password: "
                send "change-on-install\r"
                expect eof
            _EOF
            EOF
6.  After successful installation of the Oracle Key Vault client, execute the `root.sh` script to install the PKCS library on all nodes.
        # Oracle_Key_Vault_installation_directory/bin/root.sh

    The following output should appear:

        Creating directory: /opt/oracle/extapi/64/hsm/oracle/1.0.0/
        Copying PKCS library to /opt/oracle/extapi/64/hsm/oracle/1.0.0/
        Setting PKCS library file permissions
7.  Execute the Oracle Key Vault `okvutil changepwd` command on all nodes to change the password for the Oracle Key Vault client that you installed.
    Because all database administrators downloaded the same deployment script, all databases have the same password into Oracle Key Vault. This step enables each database to have a unique password.
        $ /u01/opt/oracle/product/okv/bin/okvutil changepwd -t wallet -l /u01/opt/oracle/product/okv/ssl/

        Enter wallet password: default_password
        Enter new wallet password: Oracle_Key_Vault_password
        Confirm new wallet password: Oracle_Key_Vault_password
        Wallet password changed successfully
8.  On all nodes, add the Oracle Key Vault password into a local auto-login wallet to hide the newly changed password from database administrators.
        sqlplus c##sec_admin as syskm
        Enter password: password

        ADMINISTER KEY MANAGEMENT ADD SECRET 'Oracle_Key_Vault_password'
        FOR CLIENT 'OKV_PASSWORD'
        TO LOCAL AUTO_LOGIN KEYSTORE '/u01/opt/oracle/product/tde_seps';
9.  In the root container, execute the `ALTER SYSTEM` statement to set the static `WALLET_ROOT` parameter to configure the encryption wallet location for all instances:
    1.  Set the `WALLET_ROOT` parameter.
            ALTER SYSTEM SET WALLET_ROOT='/u01/opt/oracle/product' SCOPE = SPFILE;
    2.  Depending on the version of Oracle Database 19c that you have, set either the `TABLESPACE_ENCRYPTION` or `ENCRYPT_NEW_TABLESPACES` parameter.
        - For Oracle Database 19.16 and later, run the following `ALTER SYSTEM` statement:

              ALTER SYSTEM SET TABLESPACE_ENCRYPTION = 'value' SCOPE = SPFILE SID = '*';

        - For Oracle Database 19.15 and earlier, run this `ALTER SYSTEM` statement:

              ALTER SYSTEM SET ENCRYPT_NEW_TABLESPACES = ALWAYS SCOPE = BOTH SID = '*';
10. Restart the database.
11. In the root container, use the `ALTER SYSTEM` statement to set the dynamic `TDE_CONFIGURATION` parameter.
    For example:
        ALTER SYSTEM SET TDE_CONFIGURATION = "KEYSTORE_CONFIGURATION=OKV"
        SCOPE = BOTH SID = '*';
12. Optionally, define the database default encryption algorithm after applying Oracle patch 30398099.
    By default, Oracle Database applies the `AES128` algorithm to encryption clauses that do not specify an encryption algorithm. Patch 30398099 allows you to choose from the `AES128`, `AES192`, and `AES256` encryption algorithms. Patch 30398099 has been integrated into the April 2021 RU for Oracle Database release 19c (19.11), so this functionality is available without extra patches. Note that the following parameter is preceded by an underscore.
        ALTER SYSTEM SET "_TABLESPACE_ENCRYPTION_DEFAULT_ALGORITHM" = 'encryption_algorithm'
        SCOPE = BOTH SID = '*';
13. In the root container, open the keystore, which opens the connection to Oracle Key Vault for the root container and all open PDBs.
    Note that the Oracle Key Vault password has been replaced in all subsequent `ADMINISTER KEY MANAGEMENT` commands with `EXTERNAL STORE`, because the database automatically retrieves the Oracle Key Vault password from the local auto-login wallet that you created in Step 8.
        ADMINISTER KEY MANAGEMENT SET KEYSTORE OPEN
        IDENTIFIED BY EXTERNAL STORE
        CONTAINER = ALL;
14. In the root container, set the master encryption key.
        ADMINISTER KEY MANAGEMENT SET KEY
        IDENTIFIED BY EXTERNAL STORE
        CONTAINER = CURRENT;
15. Create and activate a tagged master encryption key in all PDBs in this container.
    The benefit of adding tagged master encryption keys to PDBs is that it enables you to easily identify keys that belong to a certain PDB.
    1.  Connect to each PDB and execute the following `SELECT` statement to create an `ADMINISTER KEY MANAGEMENT` command that contains the PDB name and time stamp as a tag for the PDB's master encryption key.
            CONNECT sec_admin@pdb_name AS SYSKM
            Enter password: password

            SELECT ' ADMINISTER KEY MANAGEMENT SET KEY
            USING TAG '''||SYS_CONTEXT('USERENV', 'CON_NAME')||' '||
            TO_CHAR (SYSDATE, 'YYYY-MM-DD HH24:MI:SS')||'''
            IDENTIFIED BY EXTERNAL STORE;' "SET KEY COMMAND" FROM DUAL;
    2.  Execute the generated output of this `SELECT` statement.
        For example:
            ADMINISTER KEY MANAGEMENT SET KEY
            USING TAG 'pdb_name date time'
            IDENTIFIED BY EXTERNAL STORE;
16. On all nodes, add the Oracle Key Vault password into an auto-login wallet to enable auto-login connection into Oracle Key Vault.
    This step is mandatory in Oracle RAC. Having an auto-login connection into Oracle Key Vault is especially important when Oracle RAC nodes are automatically restarted (for example, while applying quarterly release upgrades using the `opatchauto` patch tool).
        ADMINISTER KEY MANAGEMENT ADD SECRET 'Oracle_Key_Vault_password'
        FOR CLIENT 'OKV_PASSWORD'
        TO LOCAL AUTO_LOGIN KEYSTORE '/u01/opt/oracle/product/tde';

    If you are using a release earlier than Oracle Database release 19.13, then use for client `'HSM_PASSWORD'`, not `FOR CLIENT 'OKV_PASSWORD'`.
17. In the root container, execute the `ALTER SYSTEM` statement to change the `TDE_CONFIGURATION` parameter.
    For example:
        ALTER SYSTEM SET TDE_CONFIGURATION = "KEYSTORE_CONFIGURATION=OKV|FILE"
        SCOPE = BOTH SID = '*';
18. For versions of Oracle Database earlier than release 19.16, change the default behavior of the database to always encrypt new tablespaces with the `AES128` algorithm (or the algorithm that you specified in Step 12), even if the `CREATE TABLESPACE` command does not contain the encryption clauses.
    Execute this statement once on any node:
        ALTER SYSTEM SET ENCRYPT_NEW_TABLESPACES = ALWAYS SCOPE = BOTH SID = '*';
19. From the root, encrypt sensitive credential data with `AES256` for database links in the `SYS.LINK$` and `SYS.SCHEDULER$_CREDENTIAL` system tables.
    This command requires the `SYSKM` administrative privilege:
        sqlplus c##sec_admin as syskm
        Enter password: password

        ALTER DATABASE DICTIONARY ENCRYPT CREDENTIALS;
20. Log in to the PDB and create a tablespace.
    For example, to create a tablespace named `protected`:
        CREATE TABLESPACE protected DATAFILE SIZE 50M;
21. Confirm that the tablespace is encrypted even though the encryption clauses were omitted.
        SELECT C.NAME AS pdb_name, T.NAME AS tablespace_name, E.ENCRYPTIONALG AS ALG
        FROM V$TABLESPACE T, V$ENCRYPTED_TABLESPACES E, V$CONTAINERS C
        WHERE E.TS# = T.TS# AND E.CON_ID = T.CON_ID AND E.CON_ID = C.CON_ID
        ORDER BY E.CON_ID, T.NAME;
22. Create a table in the encrypted tablespace that you just created.
    For example:
        CREATE TABLE SYSTEM.test TABLESPACE protected
        AS SELECT * FROM DBA_OBJECTS;
23. Select from this table to confirm that you can read encrypted data:
        SELECT COUNT(*), OWNER FROM SYSTEM.test
        GROUP BY OWNER
        ORDER BY 1 DESC;
24. In the PDBs, encrypt the existing tablespaces.
    Optionally, encrypt the `SYSTEM`, `SYSAUX`, and `USERS` tablespaces. If you omit the encryption algorithm, then the default algorithm (`AES128`, or the algorithm that you specified in Step 12) is applied.
        ALTER TABLESPACE tablespace_name ENCRYPTION ONLINE ENCRYPT;
25. Optionally, validate the configuration.
    1.  Confirm that the auto-login for Oracle Key Vault is working.
        You can test this by restarting the database, logging into the PDB, and then selecting from the encrypted table. To restart the database:
            $ srvctl stop database -db database_name -o immediate
            $ srvctl start database -db database_name

        After logging in to the PDB, select from the `SYSTEM.test` table.

            SELECT COUNT(*), OWNER FROM SYSTEM.test
            GROUP BY OWNER
            ORDER BY 1 DESC;
    2.  Confirm that the master encryption key re-key operations in all open PDBs are successful.
        First, as a user who has the `SYSKM` administrative privilege, execute the following `SELECT` statement to create an `ADMINISTER KEY MANAGEMENT` command that contains the PDB name and time stamp.
            SELECT ' ADMINISTER KEY MANAGEMENT SET KEY
            USING TAG '''||SYS_CONTEXT('USERENV', 'CON_NAME')||' '||
            TO_CHAR (SYSDATE, 'YYYY-MM-DD HH24:MI:SS')||'''
            FORCE KEYSTORE IDENTIFIED BY EXTERNAL STORE;' "RE-KEY COMMAND" FROM DUAL;

        Next, execute the generated output of this `SELECT` statement.

            ADMINISTER KEY MANAGEMENT SET KEY
            USING TAG 'pdb_name date time'
            FORCE KEYSTORE IDENTIFIED BY EXTERNAL STORE;
    3.  From the root container, re-key previously encrypted sensitive credential data in the `SYS.LINK$` and `SYS.SCHEDULER$_CREDENTIAL` system tables.
        This command requires the `SYSKM` administrative privilege:
            ALTER DATABASE DICTIONARY REKEY CREDENTIALS;
    4.  Drop the `protected` tablespace and its table, `test`.
            DROP TABLESPACE protected
            INCLUDING CONTENTS AND DATAFILES;

**Related Topics**

- [Supported Encryption and Integrity Algorithms](introduction-to-transparent-data-encryption.md)
- [Oracle Exadata Database Service on Cloud@Customer: Manage Encryption Keys](https://docs.oracle.com/en/engineered-systems/exadata-cloud-at-customer/ecccm/manage-encryption-keys-on-external-devices.html)
- [Oracle Autonomous Database on Dedicated Exadata Infrastructure: Manage Encryption Keys](https://docs.oracle.com/en/engineered-systems/exadata-cloud-at-customer/ecccm/adb-manage-keys-on-ext-dev.html)
- [MOS Note: Migration of File based TDE to Oracle Key Vault for Oracle Exadata Database Service on Cloud@Customer Using Automation via REST](https://support.oracle.com/epmos/faces/DocumentDisplay?id=2924192.1)

**Parent topic:** How Transparent Data Encryption Works with Oracle Real Application Clusters

### 9.4 How Transparent Data Encryption Works with SecureFiles

SecureFiles, which stores LOBS, has three features: compression, deduplication, and encryption.

- About Transparent Data Encryption and SecureFiles
  SecureFiles encryption uses TDE to provide the encryption facility for LOBs.
- Example: Creating a SecureFiles LOB with a Specific Encryption Algorithm
  The `CREATE TABLE` statement can create a SecureFiles LOB with encryption specified.
- Example: Creating a SecureFiles LOB with a Column Password Specified
  The `CREATE TABLE` statement can create a SecureFiles LOB with a column password.

**Parent topic:** Using Transparent Data Encryption with Other Oracle Features

#### 9.4.1 About Transparent Data Encryption and SecureFiles

SecureFiles encryption uses TDE to provide the encryption facility for LOBs.

When you create or alter tables, you can specify the SecureFiles encryption or LOB columns that must use the SecureFiles storage. You can enable the encryption for a LOB column by either using the current Transparent Data Encryption (TDE) syntax or by using the `ENCRYPT` clause as part of the LOB parameters for the LOB column. The `DECRYPT` option in the current syntax or the LOB parameters turn off encryption.

**Parent topic:** How Transparent Data Encryption Works with SecureFiles

#### 9.4.2 Example: Creating a SecureFiles LOB with a Specific Encryption Algorithm

The `CREATE TABLE` statement can create a SecureFiles LOB with encryption specified.

Example 9-1 shows how to create a SecureFiles LOB in a `CREATE TABLE` statement.

Example 9-1 Creating a SecureFiles LOB with a Specific Encryption Algorithm

    CREATE TABLE table1 ( a BLOB ENCRYPT USING 'AES256')
        LOB(a) STORE AS SECUREFILE (
        CACHE
        );

**Parent topic:** How Transparent Data Encryption Works with SecureFiles

#### 9.4.3 Example: Creating a SecureFiles LOB with a Column Password Specified

The `CREATE TABLE` statement can create a SecureFiles LOB with a column password.

Example 9-2 shows an example of creating a SecureFiles LOB that uses password protections for the encrypted column.

All of the LOBS in the LOB column are encrypted with the same encryption specification.

Example 9-2 Creating a SecureFiles LOB with a Column Password Specified

    CREATE TABLE table1 (a VARCHAR2(20), b BLOB)
        LOB(b) STORE AS SECUREFILE (
            CACHE
            ENCRYPT USING 'AES192' IDENTIFIED BY password
        );

**Parent topic:** How Transparent Data Encryption Works with SecureFiles

### 9.5 How Transparent Data Encryption Works with Oracle Call Interface

Transparent Data Encryption does not have any effect on the operation of Oracle Call Interface (OCI).

For most practical purposes, TDE is transparent to OCI except for the row shipping feature. You cannot use the OCI row shipping feature with TDE because the key to make the row usable is not available at the receipt-point.

**Parent topic:** Using Transparent Data Encryption with Other Oracle Features

### 9.6 How Transparent Data Encryption Works with Editions

Transparent Data Encryption does not have any effect on the Editions feature of Oracle Database.

For most practical purposes, TDE is transparent to Editions. Tables are always noneditioned objects. TDE Column Encryption encrypts columns of the table. Editions are not affected by TDE tablespace encryption.

- How ALTER SYSTEM and orapki Map to ADMINISTER KEY MANAGEMENT
  Many of the clauses from the `ALTER SYSTEM` statement correspond to the `ADMINISTER KEY MANAGEMENT` statement.

**Parent topic:** Using Transparent Data Encryption with Other Oracle Features

#### 9.6.1 How ALTER SYSTEM and orapki Map to ADMINISTER KEY MANAGEMENT

Many of the clauses from the `ALTER SYSTEM` statement correspond to the `ADMINISTER KEY MANAGEMENT` statement.

Table 9-1 compares the Transparent Data Encryption usage of the `ALTER SYSTEM` statement and the `orapki` utility from previous releases with the `ADMINISTER KEY MANAGEMENT` statement.

Table 9-1 How ALTER SYSTEM and orapki Map to ADMINISTER KEY MANAGEMENT

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

**Parent topic:** How Transparent Data Encryption Works with Editions

### 9.7 Configuring Transparent Data Encryption to Work in a Multidatabase Environment

Each Oracle database on the same server (such as databases sharing the same Oracle binary but using different data files) must access its own TDE keystore.

Keystores are not designed to be shared among databases. By design, there must be one keystore per database. You cannot use the same keystore for more than one database.

- To configure the use of keystores in a multidatabase environment, use one of the following options:

  - Option 1: Specify the keystore location by individually setting the `WALLET_ROOT` static initialization parameter and the `TDE_CONFIGURATION` dynamic initialization parameter (its `KEYSTORE_CONFIGURATION` attribute set to `FILE`) for each CDB (or standalone database). You must set the `KEYSTORE_CONFIGURATION` attribute to `FILE` in order for the `WALLET_ROOT` parameter to work.

    For example:

        WALLET_ROOT = $ORACLE_BASE/admin/db_unique_name
        TDE_CONFIGURATION="KEYSTORE_CONFIGURATION=FILE"

  - Option 2: If `WALLET_ROOT` and `TDE_CONFIGURATION` are not set, and if the databases share the same Oracle home, then ensure that the `WALLET_LOCATION` and `ENCRYPTION_WALLET_LOCATION` parameters in `sqlnet.ora` are not set. By default, `sqlnet.ora` is located in the `$ORACLE_BASE/network/admin` directory (if `$ORACLE_BASE` is set) or in the `$ORACLE_HOME/network/admin` directory.

    This enables Oracle Database to use the keystore that is located in either the `$ORACLE_BASE/admin/db_unique_name/wallet` (assuming `$ORACLE_BASE` is set) or the `$ORACLE_HOME/admin/db_unique_name/wallet` directory.

  - Option 3: If options 1 and 2 are not feasible, then use separate `sqlnet.ora` files, one for each database. Ensure that you correctly set the `TNS_ADMIN` environment variable to point to the correct database configuration. However, be aware that the `ENCRYPTION_WALLET_LOCATION` parameter in `sqlnet.ora` is deprecated, starting with release 19c, in favor of the `WALLET_ROOT` and `TDE_CONFIGURATION` initialization parameters.

**Caution:**

Using a keystore from another database can cause partial or complete data loss.

**Related Topics**

- [Transparent Data Encryption Keystore Search Order](configuring-transparent-data-encryption.md)
- [SQL\*Plus User's Guide and Reference](../sqpug/SQL-Plus-quick-start.md)

**Parent topic:** Using Transparent Data Encryption with Other Oracle Features
