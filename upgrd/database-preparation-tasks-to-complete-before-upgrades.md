## Database Preparation Tasks to Complete Before Starting Oracle Database Upgrades

Ensure that you have completed these database preparation tasks before starting an Oracle Database upgrade.

- Release Updates and Requirements for Upgrading Oracle Database
  Before starting upgrades, update your new release Oracle home to the latest Release Update (Update).
- Upgrades and Transparent Data Encryption
  To upgrade databases using TDE, provide AutoUpgrade with TDE passwords either by using the `–load_password` command line option, or by specifying an external password store.
- Recommendations for Oracle Net Services When Upgrading Oracle Database
  You must ensure that the listener is running in your new release Oracle home.
- Create or Migrate Your Password File with ORAPWD
  Review if you have REMOTE_LOGIN_PASSWORDFILE set.
- Understanding Password Case Sensitivity and Upgrades
  By default, Oracle Database 12c Release 2 (12.2) and later releases use Exclusive Mode authentication protocols. Exclusive Modes do not support case-insensitive password-based authentication.
- Checking for Accounts Using Case-Insensitive Password Version
  Use these procedures to identify if the Oracle Database that you want to upgrade has accounts or configuration parameters that are using a case-insensitive password version.
- Resource and Password Parameter Updates for STIG and CIS Profiles
  Starting with Oracle Database 21c, the upgrade configures Oracle Recommended Profiles, which includes updating an already existing STIG profile, and installing a CIS profile as part of the upgrade.
- Check for Profile Scripts (glogin.sql and login.sql)
  For all upgrade methods, Oracle recommends that you run upgrades without the use of profile scripts.
- Running Upgrades with Read-Only Tablespaces
  Use the Parallel Upgrade Utility with the `-T` option to take schema-based tablespaces offline during upgrade.
- High Availability Options for Oracle Database
  Review the high availability options available to you for Oracle Database using Standard Edition High Availability, Oracle Restart, Oracle Real Application Clusters (Oracle RAC), and Oracle RAC One Node.
- Options for High Availability with Oracle Database Standard Edition
  To enable high availability for Oracle Database Standard Edition in releases after Oracle Database 19c, learn how you can use Standard Edition High Availability.
- Moving Operating System Audit Records into the Unified Audit Trail
  Audit records that have been written to the spillover audit files can be moved to the unified audit trail database table.
- Non-CDB Upgrades and Oracle GoldenGate
  If you are upgrading a Non-CDB Oracle Database where Oracle GoldenGate is deployed, then you must shut down Oracle GoldenGate, and reconfigure it after conversion and upgrade for the multitenant architecture.
- Back Up Very Large Databases Before Using AutoUpgrade
  If you use partial offline backups with very large databases, then to minimize downtime in the event you need to downgrade your database, check your tablespaces and ensure that all tablespaces required for recovery are backed up.

**Parent topic:** [Preparing to Upgrade Oracle Database](tasks-prepare-upgrade-oracle-database.md)

### Release Updates and Requirements for Upgrading Oracle Database

Before starting upgrades, update your new release Oracle home to the latest Release Update (Update).

The software for new Oracle Database releases contains a full release that includes all the latest updates for Oracle Database at the time of the release.

Before you start an upgrade, Oracle strongly recommends that you update your new release Oracle home to the latest quarterly Release Update (Update).

My Oracle Support provides detailed notes about how you can obtain the updates, as well as tools for lifecycle management.. For example:

- My Oracle Support note 555.1 Oracle Database 19c Important Recommended One-off Patches contains a list of patches of particular importance for Oracle Database 19c.

- My Oracle Support note 2118136.2 contains a download assistant to help you select the updates, revisions, Patch Set Updates (PSU), SPU (CPU), Bundle Patches, Patchsets, and Base Releases that you need for your environment. Oracle highly recommends that you start here.

- My Oracle Support note 1227443.1 contains a list of Oracle Database PSU/BP/Update/Revision known issues. This note provides information about all known issues notes for Oracle Database, Oracle Grid Infrastructure, and the Oracle JavaVM Component (OJVM).

**Related Topics**

- [Oracle Database 19c Important Recommended One-off Patches (Doc ID 555.1)](https://support.oracle.com/rs?type=doc&id=555.1)
- [My Oracle Support Note 2118136.2](https://support.oracle.com/rs?type=doc&amp;id=2118136.2)
- [My Oracle Support Note 1227443.1](https://support.oracle.com/rs?type=doc&id=1227443.1)

**Parent topic:** Database Preparation Tasks to Complete Before Starting Oracle Database Upgrades

### Upgrades and Transparent Data Encryption

To upgrade databases using TDE, provide AutoUpgrade with TDE passwords either by using the `–load_password` command line option, or by specifying an external password store.

Starting with AutoUpgrade version 22.1, you can choose either to provide Transparent Data Encryption (TDE) passwords at the command line during the upgrade to access the source keystores, and have AutoUpgrade create new external keystore on the target system in a location that you choose, or you can specify that AutoUpgrade should access an existing secure external password store (SEPS) that contains the TDE passwords.

#### Provide TDE Passwords At the Command Line Using Password Initialization and Storage

If you have the TDE passwords for the databases that you want to upgrade, then you can provide those passwords to AutoUpgrade at the command line. AutoUpgrade creates an external key manager generated and maintained by AutoUpgrade. With this configuration, AutoUpgrade supports unmanned or automated operations of TDE-enabled databases. As the upgrade runs, AutoUpgrade can open each source database keystore without prompting for the keystore password, and enroll the target database into the TDE external keystore for key management, so that the target database can start automatically.

1.  Before running AutoUpgrade, you add the global parameter `global.keystore` to the configuration file that you use with a database that uses TDE, and specify a secure path to the location of the keystore that you want created for the upgraded database. This path should be different from any other file path you specify in AutoUpgrade, so that the keystore is not in any log file location.
2.  When you run AutoUpgrade in Deploy mode, you must run it using the `-config` command line parameter, and with the `-load_password` parameter.
3.  Before AutoUpgrade starts the database upgrades, AutoUpgrade prompts you to provide the TDE passwords for each database specified in the configuration file that uses TDE. These passwords are used only to access the source release TDE keystores, and to write the TDE passwords to the new target external keystore. No passwords are written to SQL\*Plus execution plans during the upgrade. After AutoUpgrade no longer requires the TDE passwords, these passwords are purged from memory. No log records are kept of the passwords.

Note the following security features of the password initialization and storage option:

- You specify the TDE passwords as AutoUpgrade starts to deploy; they are not included in the configuration file.
- AutoUpgrade prompts you to provide the TDE password for each source database specified in your configuration file that contains a TDE keystore.
- AutoUpgrade performs no password logging in any files written by AutoUpgrade during the upgrade. Instead, AutoUpgrade records that the `load_password` command line option was used during the Deploy.
- As AutoUpgrade runs, it places TDE passwords entered at the command line into secure Java KeyStore objects.
- After the TDE password for an Oracle Database keystore is used for access, and the target database is enrolled into the TDE external keystore for key management, AutoUpgrade clears the Java KeyStore objects containing the password, so that these passwords are no longer in memory.
- AutoUpgrade does not include the keystore file in the zip file that AutoUpgrade generates during the upgrade.
- If the upgrade is a non-CDB or an Unplug-Plug PDB upgrade, then the XML manifest file created by AutoUpgrade for databases undergoing a Non-CDB to PDB or Unplug/Plug upgrade contains TDE encryption keys. This file is also excluded in the zip file generated by AutoUpgrade.

#### Provide TDE Passwords Using an AUTO LOGIN keystore

If you choose to use an existing external keystore to provide AutoUpgrade with passwords for TDE, then you must perform a one-time setup of an `AUTO LOGIN` keystore, so that the database can be shut down and restarted without requiring DBA intervention.

To review your existing have an Oracle Wallet value specified, enter the following command:

    SQL> show parameter WALLET_ROOT;

With AutoUpgrade 22.1 and later, copying the `sqlnet.ora file` to the new Oracle release is no longer required. If you choose to use a secure external password keystore, then Oracle recommends that you use the `WALLET_ROOT` static initialization parameter and `TDE_CONFIGURATION` dynamic initialization parameter.

You can specify in your AutoUpgrade configuration file to have the keystore location changed during the upgrade. Alternatively, you can complete this task manually after the upgrade. In either case, ensure that a recent backup has been made of the keystore before you start the upgrade.

If you complete this task manually, then after the upgrade, before you can configure keystores and begin to encrypt data, you must perform a one-time configuration using the `WALLET_ROOT` and `TDE_CONFIGURATION` parameters to designate the location and type of keystores that you plan to create.

The `WALLET_ROOT` parameter specifies the keystore directory location. Before you set `WALLET_ROOT`, ensure that you have an existing directory that you can use to store keystores. (Typically, this directory is called `wallet`.)

The `TDE_CONFIGURATION` parameter specifies the type of keystore (software keystore, hardware keystore, or Oracle Key Vault keystore). If you omit the `TDE_CONFIGURATION` parameter, then Oracle Database uses the `sqlnet.ora` file settings. After you set the type of keystore using `TDE_CONFIGURATION`, when you create the keystore, Oracle Database creates a directory within the `WALLET_ROOT` location for the keystore type. For example, if you set `TDE_CONFIGURATION` to `FILE`, for Transparent Data Encryption keystores, then Oracle Database creates a directory named `tde` (lower case) within the wallet directory. If you want to migrate from one keystore type to another, then you must first set `TDE_CONFIGURATION` parameter to the keystore type that you want to use, and then use the `ADMINISTER KEY MANAGEMENT` statement to perform the migration. For example, you can migrate from a hardware security module (HSM) keystore to a TDE keystore.

The `KEYSTORE_MODE` column of the `V$ENCRYPTION_WALLET` dynamic view shows whether united mode or isolated mode has been configured.

**Note:**

In previous releases, the `SQLNET.ENCRYPTION_WALLET_LOCATION` parameter was used to define the keystore directory location. This parameter has been deprecated. Oracle recommends that you use the `WALLET_ROOT` static initialization parameter and `TDE_CONFIGURATION` dynamic initialization parameter instead. You can use the AutoUpgrade utility to perform this update for you during the upgrade.

**Related Topics**

- [Databases are Fun: AutoUpgrade and Transparent Data Encryption (TDE)](https://dohdatabase.com/2022/03/29/autoupgrade-tde/)
- [Managing the Keystore and the Primary Encryption Key](../asoag/managing-keystore-and-tde-master-encryption-key.md)
- [Updating the TDE Wallet Store Location During Upgrade Using AutoUpgrade](autoupgrade-configuration-file-examples.md)

**Parent topic:** Database Preparation Tasks to Complete Before Starting Oracle Database Upgrades

### Recommendations for Oracle Net Services When Upgrading Oracle Database

You must ensure that the listener is running in your new release Oracle home.

If the Oracle Database that you are upgrading does not have a listener configured, then before you start the upgrade, you must run Oracle Net Configuration Assistant (`NETCA`) to configure the listening protocol address and service information for the new release of Oracle Database, including a `listener.ora` file. The current listener is backward-compatible with earlier Oracle Database releases.

If you are upgrading Oracle Real Application Clusters Oracle Database, or a release older than Oracle Database 12c, then review the following additional information.

When you upgrade an Oracle RAC database with DBUA, it automatically migrates the listener from your old Oracle home to the new Oracle Grid Infrastructure home. You must administer the listener by using the `lsnrctl` command in the Oracle Grid Infrastructure home. Do not attempt to use the `lsnrctl` commands from Oracle home locations for earlier releases.

In Oracle Database, underlying net services parameters enable data compression, which reduces the size of the session data unit that is transmitted over a SQL TCP connection.

The following new parameters for the `sqlnet.ora` file specify compression, and the preferred compression scheme:

- `SQLNET.COMPRESSION`

- `SQLNET.COMPRESSION_LEVELS`

- `SQLNET.COMPRESSION_THRESHOLD`

These parameters, which were introduced with Oracle Database 12c, are not supported in earlier releases.

**Related Topics**

- [Oracle Database Net Services Reference](../netrf/parameters-for-the-sqlnet.ora.md)

**Parent topic:** Database Preparation Tasks to Complete Before Starting Oracle Database Upgrades

### Create or Migrate Your Password File with ORAPWD

Review if you have REMOTE_LOGIN_PASSWORDFILE set.

If the REMOTE_LOGIN_PASSWORDFILE initialization parameter is set to `EXCLUSIVE`, then create or migrate the password file with `ORAPWD`. Oracle Database 12c and later releases provide a new option to `ORAPWD` for migrating the password file from your existing database.

With Oracle Database 12c release 2 (12.2) and later releases, if REMOTE_LOGIN_PASSWORDFILE is set to `SHARED`, then you receive a pre-upgrade check validation warning. You can choose one of the following options to correct this issue:

- Disable the password file-based authentication entirely by setting `REMOTE_LOGIN_PASSWORDFILE = NONE`

- Limit the password file-based authentication by setting `REMOTE_LOGIN_PASSWORDFILE = EXCLUSIVE`

**See Also:**

[Oracle Database Administrator’s Guide](../admin/getting-started-with-database-administration.md) for more information about creating or migrating password files

**Parent topic:** Database Preparation Tasks to Complete Before Starting Oracle Database Upgrades

### Understanding Password Case Sensitivity and Upgrades

By default, Oracle Database 12c Release 2 (12.2) and later releases use Exclusive Mode authentication protocols. Exclusive Modes do not support case-insensitive password-based authentication.

Accounts that have only the `10G` password version become inaccessible when the server runs in an Exclusive Mode.

In previous Oracle Database releases, you can configure the authentication protocol so that it allows case-insensitive password-based authentication by setting `SEC_CASE_SENSITIVE_LOGON=FALSE`. Starting with Oracle Database 12c release 2 (12.2), the default password-based authentication protocol configuration excludes the use of the case-insensitive `10G` password version. By default, the `SQLNET.ORA` parameter `SQLNET.ALLOWED_LOGON_VERSION_SERVER` is set to `12`, which is an Exclusive Mode. When the database is configured in Exclusive Mode, the password-based authentication protocol requires that one of the case-sensitive password versions (`11G` or `12C`) is present for the account being authenticated. This mode excludes the use of the `10G` password version used in earlier releases. After upgrading to Oracle Database 12c release 2 and later releases, accounts that have only the case-insensitive `10G` password version become inaccessible. This change occurs because the server runs in an Exclusive Mode by default. When Oracle Database is configured in Exclusive Mode, it cannot use the old `10G` password version to authenticate the client. The server is left with no password version with which to authenticate the client.

For greater security, Oracle recommends that you leave case-sensitive password-based authentication enabled. This setting is the default. However, you can temporarily disable case-sensitive authentication during the upgrade to new Oracle Database releases. After the upgrade, you can then decide if you want to enable the case-sensitive password-based authentication feature as part of your implementation plan to manage your password versions.

Before upgrading, Oracle recommends that you determine if this change to the default password-based authentication protocol configuration affects you. Perform the following checks:

- Identify if you have accounts that use only `10G` case-insensitive password authentication versions.

- Identify if you have Oracle Database 11g release 2 (11.2.0.3) database or earlier clients that have not applied critical patch update `CPUOct2012`, or a later patch update, and have any account that does not have the case-insensitive `10G` password version.

- Ensure that you do not have the deprecated parameter SEC_CASE_SENSITIVE_LOGON set to FALSE. Setting this parameter to FALSE prevents the use of the case-sensitive password versions (the `11G` and `12C` password versions) for authentication.

#### Options for Accounts Using Case-Insensitive Versions

If you have user accounts that have only the case-insensitive `10G` password version, then you must choose one of the following alternatives:

- Before upgrade, update the password versions for each account that has only the `10G` password version. You can update the password versions by expiring user passwords using the `10G` password version, and requesting that these users log in to their account. When they attempt to log in, the server automatically updates the list of password versions, which includes the case-sensitive password versions.

- Change the setting of the SQLNET.ORA parameter `SQLNET.ALLOWED_LOGON_VERSION_SERVER` to any of the settings that are not Exclusive Mode. For example: `SQLNET.ALLOWED_LOGON_VERSION_SERVER=11`

**Related Topics**

- [Oracle Database 2 Day DBA](../admqs/administering-user-accounts-and-security.md)
- [Oracle Database Net Services Reference](../netrf/parameters-for-the-sqlnet.ora.md)
- [Oracle Database Security Guide](../dbseg/configuring-authentication.md)

**Parent topic:** Database Preparation Tasks to Complete Before Starting Oracle Database Upgrades

### Checking for Accounts Using Case-Insensitive Password Version

Use these procedures to identify if the Oracle Database that you want to upgrade has accounts or configuration parameters that are using a case-insensitive password version.

By default, in Oracle Database 12c release 2 (12.2) and later releases, the `10G` password version is not generated or allowed.

If you do not set `SQLNET.ALLOWED_LOGON_VERSION_SERVER` to a permissive authentication protocol that permits case-insensitive versions, and you do not want user accounts authenticated with case-insensitive password versions to be locked out of the database, then you must identify affected accounts, and ensure that they are using case-sensitive password versions.

Example 2-1 Finding User Accounts That Use Case-Insensitive (10G) Version

Log in to SQL\*Plus as an administrative user, and enter the following SQL query:

    SELECT USERNAME,PASSWORD_VERSIONS FROM DBA_USERS;

The following result shows password versions for the accounts:

    USERNAME                       PASSWORD_VERSIONS
    ------------------------------ -----------------
    JONES                          10G 11G 12C
    ADAMS                          10G 11G
    CLARK                          10G 11G
    PRESTON                        11G
    BLAKE                          10G

In this example, the backgrounds for each user account password verification version in use are different:

- `JONES` was created in Oracle Database `10G`, and the password for `JONES` was reset in Oracle Database `12C` when the setting for the `SQLNET.ALLOWED_LOGON_VERSION_SERVER` parameter was set to `8`. As a result, this password reset created all three versions. `11G` and `12C` use case-sensitive passwords.

- `ADAMS` and `CLARK` were originally created with the `10G` version, and then `11G`, after they were imported from an earlier release. These account passwords were then reset in `11G`, with the deprecated parameter SEC_CASE_SENSITIVE_LOGON set to TRUE.

- The password for `BLAKE` was created with the `10G` version, and the password has not been reset. As a result, user BLAKE continues to use the `10G` password version, which uses a case-insensitive password.

The user `BLAKE` has only the `10G` password version before upgrade:

    SQL> SELECT USERNAME,PASSWORD_VERSIONS FROM DBA_USERS;

    USERNAME PASSWORD_VERSIONS
    ------------------------------ -----------------
    BLAKE 10G

If you upgrade to a new Oracle Database release without taking any further action, then this account becomes inaccessible. Ensure that the system is not configured in Exclusive Mode (by setting the `SQLNET.ORA` parameter `SQLNET.ALLOWED_LOGON_VERSION_SERVER` to a more permissive authentication mode) before the upgrade.

Example 2-2 Fixing Accounts with Case-Insensitive Passwords

Complete the following procedure:

1.  Use the following SQL query to find the accounts that only have the `10G` password version:

              select USERNAME
                 from DBA_USERS
                where ( PASSWORD_VERSIONS = '10G '
                       or PASSWORD_VERSIONS = '10G HTTP ')
                  and USERNAME <> 'ANONYMOUS';

2.  Configure the system so that it is not running in Exclusive Mode by editing the setting of the `SQLNET.ORA` parameter `SQLNET.ALLOWED_LOGON_VERSION_SERVER` to a level appropriate for affected accounts. For example:

        SQLNET.ALLOWED_LOGON_VERSION_SERVER=11

    After you make this change, proceed with the upgrade.

3.  After the upgrade completes, use the following command syntax to expire the accounts you found in step 1, where `username` is the name of a user returned from the query in step 1:

    `ALTER USER ``username`` PASSWORD EXPIRE;`

4.  Ask the users for whom you have expired the passwords to log in.

5.  When these users log in, they are prompted to reset their passwords. The system internally generates the missing `11G` and `12C` password versions for their account, in addition to the `10G` password version. The `10G` password version is still present, because the system is running in the permissive mode.

6.  Ensure that the client software with which users are connecting has the `O5L_NP` capability flag.

    **Note:**

    All Oracle Database release 11.2.0.4 and later clients, and all Oracle Database release 12.1 and later clients have the `O5L_NP` capability. Other clients require the `CPUOct2012` patch to acquire the `O5L_NP` capability.

    The `O5L_NP` capability flag is documented in Oracle Database Net Services Reference, in the section on the parameter `SQLNET.ALLOWED_LOGON_VERSION_SERVER`.

7.  After all clients have the `O5L_NP` capability, raise the server security back to Exclusive Mode by using the following procedure:

    1.  Remove the `SEC_CASE_SENSITIVE_LOGON` setting from the instance initialization file, or set the `SEC_CASE_SENSITIVE_LOGON` instance initialization parameter to `TRUE`. For example:

        `SEC_CASE_SENSITIVE_LOGON = TRUE`

    2.  Remove the `SQLNET.ALLOWED_LOGON_VERSION_SERVER` parameter from the server `SQLNET.ORA` file, or set it back to Exclusive Mode by changing the value of `SQLNET.ALLOWED_LOGON_VERSION_SERVER` in the server `SQLNET.ORA` file back to `12`. For example:

        `SQLNET.ALLOWED_LOGON_VERSION_SERVER = 12`

8.  Use the following SQL query to find the accounts that still have the `10G` password version:

               select USERNAME
                 from DBA_USERS
                where PASSWORD_VERSIONS like '%10G%'
                  and USERNAME <> 'ANONYMOUS';

9.  Use the list of accounts returned from the query in step 8 to expire all the accounts that still have the `10G` password version. Expire the accounts using the following syntax, where `username` is a name on the list returned by the query:

    `ALTER USER ``username`` PASSWORD EXPIRE;`

10. Request the users whose accounts you expired to log in to their accounts.

    When the users log in, they are prompted to reset their password. The system internally generates only the `11G` and `12C` password versions for their account. Because the system is running in Exclusive Mode, the `10G` password version is no longer generated.

11. Check that the system is running in a secure mode by rerunning the query from step 1. Ensure that no users are found. When the query finds no users, this result means that no `10G` password version remains present in the system.

Example 2-3 Checking for the Presence of SEC_CASE_SENSITIVE_LOGON Set to FALSE

Oracle Database does not prevent the use of the `FALSE` setting for `SEC_CASE_SENSITIVE_LOGON` when the `SQLNET.ALLOWED_LOGON_VERSION_SERVER` parameter is set to `12` or `12a`. This setting can result in all accounts in the upgraded database becoming inaccessible.

    SQL> SHOW PARAMETER SEC_CASE_SENSITIVE_LOGON

    NAME                                 TYPE        VALUE
    ------------------------------------ ----------- ------------------------------
    sec_case_sensitive_logon             boolean     FALSE

You can change this parameter by using the following command:

    SQL> ALTER SYSTEM SET SEC_CASE_SENSITIVE_LOGON = TRUE;

    System altered.

**Note:**

Unless the value for the parameter `SQLNET.ALLOWED_LOGON_VERSION_SERVER` is changed to a version that is more permissive than `12`, such as `11`, do not set the `SEC_CASE_SENSITIVE_LOGON` parameter to FALSE.

**Related Topics**

- [Oracle Database Net Services Reference](../netrf/parameters-for-the-sqlnet.ora.md)
- [Oracle Database Security Guide](../dbseg/configuring-authentication.md)

**Parent topic:** Database Preparation Tasks to Complete Before Starting Oracle Database Upgrades

### Resource and Password Parameter Updates for STIG and CIS Profiles

Starting with Oracle Database 21c, the upgrade configures Oracle Recommended Profiles, which includes updating an already existing STIG profile, and installing a CIS profile as part of the upgrade.

A **profile** is a collection of attributes that apply to a user. It enables a single point of reference for any of multiple users that share those exact attributes.

During Oracle Database upgrades, the Oracle Supplied Profile `ORA_STIG_PROFILE` user profile is updated in accordance with the most recent system configuration baselines specified by the US Department of Defense Systems Agency (DISA) Security Technical Implementation Guides (STIG) baselines. This update overwrites any password and resource limits that you may have set previously in the `ORA_STIG_PROFILE` user profile. In addition, a new profile is added, `ORA_CIS_PROFILE`, which complies with the most recent Center of Internet Security (CIS) baseline updates available to Oracle at the time of the software release. These two profiles are designated **Oracle Recommended Profiles**. These profiles differ from a standard `DEFAULT` profile, because they are based on the STIG and CIS baselines.

The profiles `ORA_STIG_PROFILE` and `ORA_CIS_PROFILE` are created as `LOCAL` profiles, and the clause `CONTAINER=CURRENT` clause is used. However, to enhance the security of the profiles that Oracle provides, only the `SYS` user has permissions to modify these files.

If there are users associated to `ORA_STIG_PROFILE`, then the following parameters for these users are made stricter after the upgrade:

- `PASSWORD_LIFE_TIME`, which is changed to `35`.
- `PASSWORD_REUSE_TIME`, which is changed to `175`.
- `PASSWORD_GRACE_TIME`, which is changed to `0`.

For more information about using Oracle Recommended Profiles, refer to Oracle Database Security Guide.

**Related Topics**

- [Managing Resources with Profiles](../dbseg/managing-security-for-oracle-database-users.md)

**Parent topic:** Database Preparation Tasks to Complete Before Starting Oracle Database Upgrades

### Check for Profile Scripts (glogin.sql and login.sql)

For all upgrade methods, Oracle recommends that you run upgrades without the use of profile scripts.

Depending on the content of profile scripts (`glogin.sql` and `login.sql`), there is a risk that these scripts can interfere with the upgrade of Oracle Database, and that you can encounter an `UPG-1400 UPGRADE FAILED` error, or `Unexpected error encountered in catcon`, or `ORA-04023: Object SYS.STANDARD could not be validated or authorized`. Oracle recommends that you remove the site profile script (`glogin.sql`) from the target Oracle home (located in the Oracle home under `/sqlplus/admin` ) before starting the upgrade. Also ensure that no user profile script is defined, either in the current directory, or specified using the environment variable `SQLPATH`.

**Related Topics**

- [Upgrade and Profile Scripts](https://dohdatabase.com/2020/08/04/upgrade-and-profile-scripts/)

**Parent topic:** Database Preparation Tasks to Complete Before Starting Oracle Database Upgrades

### Running Upgrades with Read-Only Tablespaces

Use the Parallel Upgrade Utility with the `-T` option to take schema-based tablespaces offline during upgrade.

Oracle Database can read file headers created in earlier releases, so you are not required to do anything to them during the upgrade. The file headers of `READ ONLY` tablespaces are updated when they are changed to `READ WRITE`.

If the upgrade suffers a catastrophic error, so that the upgrade is unable to bring the tablespaces back online, then review the upgrade log files. The log files contain the actual SQL statements required to make the tablespaces available. To bring the tablespaces back online, you must run the SQL statements in the log files for the database, or run the log files for each PDB.

#### Viewing Tablespace Commands in Upgrade Log Files

If a catastrophic upgrade failure occurs, then you can navigate to the log directory (`Oracle_base``/cfgtoologs/dbua`), and run commands in the log files manually to bring up tablespaces. You can view tablespace commands in the following log files:

- Non-CDB Upgrades: `catupgrd0.log`

- PDB databases: `catupgrd``pdbname``0.log`, where `pdbname` is the name of the PDB that you are upgrading.

At the beginning of each log file, you find SQL statements such as the following, which sets tables to `READ ONLY`:

    SQL> ALTER TABLESPACE ARGROTBLSPA6 READ ONLY;

    Tablespace altered.

    SQL> ALTER TABLESPACE ARGROTBLSPB6 READ ONLY;

    Tablespace altered.

Near the end of each log file, you find SQL statements to reset tables to `READ WRITE`:

    SQL> ALTER TABLESPACE ARGROTBLSPA6 READ WRITE;

    Tablespace altered.

    SQL> ALTER TABLESPACE ARGROTBLSPB6 READ WRITE;

    Tablespace altered.

**See Also:**

[Oracle Database Administrator’s Guide](../admin/transporting-data.md) for information about transporting tablespaces between databases

**Parent topic:** Database Preparation Tasks to Complete Before Starting Oracle Database Upgrades

### High Availability Options for Oracle Database

Review the high availability options available to you for Oracle Database using Standard Edition High Availability, Oracle Restart, Oracle Real Application Clusters (Oracle RAC), and Oracle RAC One Node.

The following is an overview of the high availability options available to you for Oracle Database.

#### Standard Edition High Availability

- Cluster-based active/passive Oracle Database failover solution
- Designed for single instance Standard Edition Oracle Databases
- Available with Oracle Database 19c release update (RU) 19.7 and later
- Requires Oracle Grid Infrastructure 19c RU 19.7 and later, installed as a Standalone Cluster

#### Oracle Restart

- Oracle Database instance restart only feature and basis for Oracle Automatic Storage Management (Oracle ASM) for standalone server deployments
- For single instance Oracle Databases
- Requires Oracle Grid Infrastructure for a standalone server (no cluster)

#### Oracle Real Application Clusters (Oracle RAC) One Node

- Provides a cluster-based active/passive Oracle Database failover and online database relocation solution
- Available for Oracle RAC-enabled Oracle Databases
- Only one instance of an Oracle RAC-enabled Oracle Database is running under normal operations
- Enables relocation of the active instance to another server in the cluster in an online fashion. To relocate the active instance, you can temporarily start a second instance on the destination server, and relocate the workload
- Supports Rolling Upgrades - patch set, database, and operating system
- Supports Application Continuity
- Requires Oracle Grid Infrastructure to be installed as a Standalone Cluster

#### Oracle Real Application Clusters (Oracle RAC)

- Provides active / active Oracle Database high availability and scalability solution
- Enables multiple servers to perform concurrent transactions on the same Oracle Database
- Provides high availability: a failure of a database instance or server does not interrupt the database service as a whole, because other instances and their servers remain operational
- Supports Rolling Upgrades - patch set, database, and operating system
- Supports Application Continuity
- Requires Oracle Grid Infrastructure to be installed as a Standalone Cluster

<!-- -->

- Audit Table Preupgrade and Archive Requirements
  For Oracle Database releases earlier than 12.1 using Oracle Label Security and Oracle Database Vault, you must run the OLS preprocess script before you upgrade.

**Parent topic:** Database Preparation Tasks to Complete Before Starting Oracle Database Upgrades

#### Audit Table Preupgrade and Archive Requirements

For Oracle Database releases earlier than 12.1 using Oracle Label Security and Oracle Database Vault, you must run the OLS preprocess script before you upgrade.

If you are upgrading from a database earlier than Oracle Database release 12.1 that uses Oracle Label Security (OLS) and Oracle Database Vault, then you must first run the OLS preprocess script, `olspreupgrade.sql`, to process the `aud$` table contents. The OLS upgrade moves the `aud$` table from the `SYSTEM` schema to the `SYS` schema. The `olspreupgrade.sql` script is a preprocessing script required for this move.

**Caution:**

Running the `olspreupgrade.sql` script before upgrading is mandatory for upgrading databases earlier than Oracle Database release 12.1 that use Oracle Label Security and Oracle Database Vault. Once you have upgraded to Oracle Database release 12.1, you do not have to perform the OLS preprocessing procedure going forward to patch or upgrade the database.

The `olspreupgrade.sql` script creates a temporary table `PREUPG_AUD$` in the `SYS` schema and moves the `SYSTEM.aud$` records to `SYS.PREUPG_AUD$`. As a safety measure, Oracle recommends that you archive your audit trail before running the `olspreupgrade.sql` script. If Oracle Label Security is installed on your database, and you are upgrading from an earlier release, then you must run the OLS preprocess script before upgrading.

**See Also:**

[Oracle Database Security Guide](../dbseg/administering-the-audit-trail.md) for information about archiving audit trails

[Oracle Label Security Administrator's Guide](../olsag/performing-dba-functions-under-oracle-label-security.md) for information about the OLS preprocess script

**Parent topic:** High Availability Options for Oracle Database

### Options for High Availability with Oracle Database Standard Edition

To enable high availability for Oracle Database Standard Edition in releases after Oracle Database 19c, learn how you can use Standard Edition High Availability.

- Preparing to Upgrade Standard Edition Oracle RAC or Oracle RAC One Node
  To maintain high availability after migrating from Standard Edition Oracle Real Application Clusters (Oracle RAC), you can use Standard Edition High Availability.
- Requirements for Using Standard Edition High Availability With Oracle Databases
  To use Standard Edition High Availability, deploy Oracle Database Standard Edition 2 in accordance with these configuration requirements.

**Parent topic:** Database Preparation Tasks to Complete Before Starting Oracle Database Upgrades

#### Preparing to Upgrade Standard Edition Oracle RAC or Oracle RAC One Node

To maintain high availability after migrating from Standard Edition Oracle Real Application Clusters (Oracle RAC), you can use Standard Edition High Availability.

Starting with the Oracle Database 19c release, Oracle Database Standard Edition 2 does not support Oracle RAC. To continue to meet high availability needs for Oracle Database Standard Edition, Oracle is introducing Standard Edition High Availability.

**Parent topic:** Options for High Availability with Oracle Database Standard Edition

#### Requirements for Using Standard Edition High Availability With Oracle Databases

To use Standard Edition High Availability, deploy Oracle Database Standard Edition 2 in accordance with these configuration requirements.

- The database is created in a cluster running Oracle Grid Infrastructure for a Standalone Cluster, with its database files placed in Oracle Automatic Storage Management (Oracle ASM) or Oracle Automatic Storage Management Cluster File System (Oracle ACFS).
- When using the Database Configuration Assistant, do not create a listener when creating an Oracle Database Standard Edition 2 database that you want to configure for Standard Edition High Availability.
- Register the database with Single Client Access Name (SCAN) listeners as remote listeners, and node listeners as the local listener.
- Create a database service. Use this service, instead of the default database service, when you connect applications or database clients to the database.
- Ensure that the server parameter file (`spfile`) and password file are on Oracle ASM or Oracle ACFS. If the `spfile` and password file were placed on a local file system when the database was created or configured, then move these files to Oracle ASM or Oracle ACFS.

Refer to the database installation documentation for additional requirements that must be met.

**Related Topics**

- [Oracle Database Installation Guide for Linux](../ladbi/guidelines-for-seha.md)

**Parent topic:** Options for High Availability with Oracle Database Standard Edition

### Moving Operating System Audit Records into the Unified Audit Trail

Audit records that have been written to the spillover audit files can be moved to the unified audit trail database table.

When the database is not writable (such as during database mounts), if the database is closed, or if it is read-only, then Oracle Database writes the audit records to these external files. The default location for these external files is the `$ORACLE_BASE/audit/$ORACLE_SID` directory.

You can load the files into the database by running the `DBMS_AUDIT_MGMT.LOAD_UNIFIED_AUDIT_FILES` procedure. Be aware that if you are moving a large number of operating system audit records in the external files, performance may be affected.

To move the audit records in these files to the `AUDSYS` schema audit table when the database is writable:

1.  Log into the CDB root as a user who has been granted the `AUDIT_ADMIN` role.
    Before you can upgrade to the current release or Oracle Database, you must execute the `DBMS_AUDIT_MGMT.LOAD_UNIFIED_AUDIT_FILES` procedure from the CDB root to avoid losing operating system spillover files during the upgrade process.
    For example:
        CONNECT c##aud_admin
        Enter password: password
        Connected.
2.  Ensure that the database is open and writable.
    To find if the database is open and writable, query the `V$DATABASE` view.

        SELECT NAME, OPEN_MODE FROM V$DATABASE;

        NAME            OPEN_MODE
        --------------- ----------
        HRPDB           READ WRITE

    You can run the `show pdbs` command to find information about PDBs associated with the current instance.
3.  Run the `DBMS_AUDIT_MGMT.LOAD_UNIFIED_AUDIT_FILES` procedure.
        EXEC DBMS_AUDIT_MGMT.LOAD_UNIFIED_AUDIT_FILES;
4.  If you want to load individual PDB audit records, then log in to each PDB and run the `DBMS_AUDIT_MGMT.LOAD_UNIFIED_AUDIT_FILES` procedure again.

The audit records are loaded into the `AUDSYS` schema audit table immediately, and then deleted from the `$ORACLE_BASE/audit/$ORACLE_SID` directory.

**Parent topic:** Database Preparation Tasks to Complete Before Starting Oracle Database Upgrades

### Non-CDB Upgrades and Oracle GoldenGate

If you are upgrading a Non-CDB Oracle Database where Oracle GoldenGate is deployed, then you must shut down Oracle GoldenGate, and reconfigure it after conversion and upgrade for the multitenant architecture.

If you are using Oracle GoldenGate with the non-CDB Oracle Database that you want to upgrade, then before you convert and upgrade the source non-CDB Oracle Database to the multitenant architecture, you must shut down and remove the Oracle GoldenGate processes, and then reconfigure them after conversion and upgrade for the multitenant architecture. The following is a high level overview of the processes required:

1.  Drop Oracle GoldenGate users on the source Oracle Database.
2.  Wait until the Oracle GoldenGate processes finish processing all current DML and DDL data in the Oracle GoldenGate trails, and processes are at End of File (EOF).
3.  Stop all Oracle GoldenGate processes on the source database.
4.  Complete the conversion and upgrade of the source non-CDB Oracle Database to the target Oracle Database on the target release CDB.
5.  Restart the database.
6.  If you are also upgrading the database from an earlier release to a later major release family (for example, from Oracle Database 12.1 to Oracle Database 19c, which is the terminal patch set of the Oracle Database 12.2 family), then you must install a new version of Oracle GoldenGate that is supported for Oracle Database 19c. If you are upgrading both Oracle Database and Oracle GoldenGate simultaneously, then you must upgrade the database first.

After the database conversion and upgrade is complete, you can create new credentials for the Oracle GoldenGate extract user. With the new credentials you can then create a new Extract process and Extract pump and distribution service for the upgraded Oracle Database PDB on the target CDB, and start up the newly created processes. For more information about completing those procedures after the upgrade, refer to the Oracle GoldenGate documentation.

**Related Topics**

- [Establishing Oracle GoldenGate Credentials](https://docs.oracle.com/en/middleware/goldengate/core/19.1/oracle-db/establishing-oracle-goldengate-credentials.html#GUID-E40B375A-5042-4195-B563-BE7EDC251880)
- [Configuring Oracle GoldenGate in a Multitenant Container Database](https://docs.oracle.com/en/middleware/goldengate/core/19.1/oracle-db/configuring-oracle-goldengate-multitenant-container-database-1.html#GUID-0B0CEB35-51C6-4319-BEE1-FA208FF4DE05)

**Parent topic:** Database Preparation Tasks to Complete Before Starting Oracle Database Upgrades

### Back Up Very Large Databases Before Using AutoUpgrade

If you use partial offline backups with very large databases, then to minimize downtime in the event you need to downgrade your database, check your tablespaces and ensure that all tablespaces required for recovery are backed up.

If you are using the AutoUpgrade utility for upgrading databases where you have selected partial offline backups as your backup option, then check that all tablespaces that are required for upgrade are in `READ WRITE` mode, and only after you are sure you have identified all required tablespaces for backup, change the status of all required tables before you take an `OFFLINE` backup of the tablespaces you require for recovery before you run AutoUpgrade.

The reasons for this guideline are as follows:

During an AutoUpgrade operation, other tablespaces besides `SYSTEM`, `SYSAUX` and `UNDO` may need to be maintained in `READ WRITE` status for the upgrade. Some of the reasons for this requirement during an upgrade can include:

- Tablespaces that contain dictionary objects
- Tablespaces that are the default tablespace for Oracle-maintained users
- Tablespaces that are the default tablespace for the database

AutoUpgrade detects if all tablespaces needed for the upgrade are in `READ WRITE` status.

When there are tablespaces that must be changed to `READ WRITE` mode for the upgrade, then:

- During the `PRECHECKS` processing mode, AutoUpgrade detects tables in `READ ONLY` status as an issue.
- During the `FIXUP` processing mode, AutoUpgrade performs an automatic fixup to update to `READ WRITE` mode any tablespaces that it detects in `READ ONLY` mode that must be in `READ WRITE` mode.

If there are any tablespaces required for upgrade that AutoUpgrade changes from `READ ONLY` mode to `READ WRITE` mode, and these tablespaces were not included in your backup before starting AutoUpgrade, then your recovery strategy is at risk. To ensure that your backup is valid for recovery, you must take your `OFFLINE` backup only after you are sure which tablespaces must be backed up.

To ensure that your partial offline backup contains backups for all tablespaces modified during the upgrade, complete this procedure:

1.  Put all tablespaces in `READ ONLY` mode, except for `SYSTEM`, `SYSUX` and `UNDO` and those tablespaces that you know must be in `READ WRITE`.

2.  Run the this query for pivot users:

        (SELECT username
        FROM dba_users
        WHERE user_id in (
          SELECT schema# FROM sys.registry$
            WHERE namespace = 'SERVER'
            UNION
            SELECT schema# FROM sys.registry$schemas
            WHERE namespace = 'SERVER'
            UNION
            SELECT user# FROM sys.user$
            WHERE type#=1 AND bitand(spare1,256)=256))
          SELECT tablespace_name
          FROM dba_tablespaces
          WHERE status <>'ONLINE' and tablespace_name IN
          (
          SELECT property_value
          FROM database_properties
            WHERE property_name = 'DEFAULT_PERMANENT_TABLESPACE'
            UNION
            SELECT default_tablespace
            FROM dba_users
            WHERE username IN (SELECT username FROM pivot_users)
            UNION
            SELECT tablespace_name
            FROM dba_segments
            WHERE owner IN (SELECT username FROM pivot_users)
            UNION
            SELECT t.name
            FROM modeltab$ m,  ts$ t, sys_objects s
            WHERE m.obj#=s.object_id and s.ts_number=t.ts#
            )'

    The next step you take depends on the result of the query:

    - If the query returns no rows, then it means that backing up `SYSTEM`, `SYSAUX` and `UNDO`, as well as those tables you specifically know must be in `READ WRITE`, is sufficient to complete a partial offline backup.
    - If the query return rows in tablespaces, then to complete a partial offline backup, you must place these additional tablespaces in `READ WRITE` mode.

3.  When you have completed identifying and placing all required tablespaces in `READ WRITE` mode, take your partial offline backup of those tablespaces. Also back up `SYSTEM`, `SYSAUX` and `UNDO`.redo logs, control files and any other files that you consider relevant for the restore/recovery procedure in case they are needed.

4.  Run AutoUpgrade in `ANALYZE` mode. Review the output, and ensure that AutoUpgrade identifies no additional tablespaces reported as `READ ONLY` that must be put in `READ WRITE`.

(Optional) Enter the result of the procedure here.

**Parent topic:** Database Preparation Tasks to Complete Before Starting Oracle Database Upgrades
