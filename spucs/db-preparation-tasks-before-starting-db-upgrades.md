Ensure that you have completed these database preparation tasks before starting an Oracle Database upgrade.

- [Release Updates and Requirements for Upgrading Oracle Database](https://docs.oracle.com/en/database/oracle/oracle-database/19/spucs/unresolvable-reference.html)
  Before starting upgrades, update your new release Oracle home to the latest Release Update (Update).
- [Recommendations for Oracle Net Services When Upgrading Oracle Database](https://docs.oracle.com/en/database/oracle/oracle-database/19/spucs/unresolvable-reference.html)
  You must ensure that the listener is running in your new release Oracle home.
- [Understanding Password Case Sensitivity and Upgrades](https://docs.oracle.com/en/database/oracle/oracle-database/19/spucs/unresolvable-reference.html)
  By default, Oracle Database 12c Release 2 (12.2) and later releases use Exclusive Mode authentication protocols. Exclusive Modes do not support case-insensitive password-based authentication.
- [Checking for Accounts Using Case-Insensitive Password Version](https://docs.oracle.com/en/database/oracle/oracle-database/19/spucs/unresolvable-reference.html)
  Use these procedures to identify if the Oracle Database that you want to upgrade has accounts or configuration parameters that are using a case-insensitive password version.
- [Running Upgrades with Read-Only Tablespaces](https://docs.oracle.com/en/database/oracle/oracle-database/19/spucs/unresolvable-reference.html)
  To take user schema-based tablespaces offline during upgrade, use AutoUpgrade with the `catctl_options` parameter `-T` option.

**Parent topic:** [Preparing to Upgrade Oracle Database](preparing-to-upgrade.md)

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

### Recommendations for Oracle Net Services When Upgrading Oracle Database

You must ensure that the listener is running in your new release Oracle home.

If the Oracle Database that you are upgrading does not have a listener configured, then before you start the upgrade, you must run Oracle Net Configuration Assistant (`NETCA`) to configure the listening protocol address and service information for the new release of Oracle Database, including a `listener.ora` file. The current listener is backward-compatible with earlier Oracle Database releases.

If you are upgrading Oracle Real Application Clusters Oracle Database, or a release older than Oracle Database 12c, then review the following additional information.

For Oracle RAC database upgrades, the listener normally is migrated during the Grid Infrastructure upgrade. You must administer the listener by using the `lsnrctl` command in the Oracle Grid Infrastructure home. Do not attempt to use the `lsnrctl` commands from Oracle home locations for earlier releases.

**Related Topics**

- [Oracle Database Net Services Reference](../netrf/parameters-for-the-sqlnet.ora.md)

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

### Checking for Accounts Using Case-Insensitive Password Version

Use these procedures to identify if the Oracle Database that you want to upgrade has accounts or configuration parameters that are using a case-insensitive password version.

By default, in Oracle Database 12c release 2 (12.2) and later releases, the `10G` password version is not generated or allowed.

If you do not set `SQLNET.ALLOWED_LOGON_VERSION_SERVER` to a permissive authentication protocol that permits case-insensitive versions, and you do not want user accounts authenticated with case-insensitive password versions to be locked out of the database, then you must identify affected accounts, and ensure that they are using case-sensitive password versions.

Example 2-2 Finding User Accounts That Use Case-Insensitive (10G) Version

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

Example 2-3 Fixing Accounts with Case-Insensitive Passwords

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

Example 2-4 Checking for the Presence of SEC_CASE_SENSITIVE_LOGON Set to FALSE

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

### Running Upgrades with Read-Only Tablespaces

To take user schema-based tablespaces offline during upgrade, use AutoUpgrade with the `catctl_options` parameter `-T` option.

For all Oracle Database releases that AutoUpgrade can upgrade, Autoupgrade can read file headers created in earlier releases. You are not required to do anything to them during the upgrade. The file headers of `READ ONLY` tablespaces are updated when they are changed to `READ WRITE`.

**Note:**

If you are performing a non-CDB to PDB conversion, then using read-only tablespaces is not a valid fallback option. During a non-CDB to PDB conversion, tablespaces must be online during conversion, because each data file header requires changes during the upgrade.

If the upgrade suffers a catastrophic error, so that the upgrade is unable to bring the tablespaces back online, then review the upgrade log files. The log files contain the actual SQL statements required to make the tablespaces available. To bring the tablespaces back online, you must run the SQL statements in the log files for the database, or run the log files for each PDB.

#### Viewing Tablespace Commands in Upgrade Log Files

If a catastrophic upgrade failure occurs, then you can navigate to the `dbupgrade` log directory, and run commands in the log files manually to bring up tablespaces. You can view tablespace commands in the following log files:

- Non-CDB Upgrade format: `catupgrd``YYYY``MM``DD``HH``MM``SC``0.log`, where:

  `YYYY` is the year, `MM` is the month, `DD` is the day, `HH` is the hour, `MM` is the minute in the hour, and `SC` is the seconds.

- PDB databases format: `catupgrd``YYYY``MM``DD``HH``SC``pdbname``0.log`, where:

  `YYYY` is the year, `MM` is the month, `DD` is the day, `HH` is the hour, `MM` is the minute in the hour, `SC` is the seconds, and `pdbname` is the name of the PDB that you are upgrading.

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
