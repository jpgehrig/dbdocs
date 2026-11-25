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

**Parent topic:** [Database Preparation Tasks to Complete Before Starting Oracle Database Upgrades](db-preparation-tasks-before-starting-db-upgrades.md)
