For better security, find and reset passwords for user accounts that use the `10G` password version so that they use later, more secure password versions.

### Finding All Password Versions of Current Users

You can query the `DBA_USERS` data dictionary view to find a list of all the password versions configured for user accounts.

For example:

    SELECT USERNAME,PASSWORD_VERSIONS FROM DBA_USERS;

    USERNAME                       PASSWORD_VERSIONS
    ------------------------------ -----------------
    JONES                          10G 11G 12C
    ADAMS                          10G 11G
    CLARK                          10G 11G
    PRESTON                        11G
    BLAKE                          10G

The `PASSWORD_VERSIONS` column shows the list of password versions that exist for the account. `10G` refers to the earlier case-insensitive Oracle password version, `11G` refers to the SHA-1-based password version, and `12C` refers to the SHA-2-based SHA-512 password version.

- User `jones`: The password for this user was reset in Oracle Database 12c Release 12.1 when the `SQLNET.ALLOWED_LOGON_VERSION_SERVER` parameter setting was `8`. This enabled all three password versions to be created.

- Users `adams` and `clark`: The passwords for these accounts were originally created in Oracle Database 10g and then reset in Oracle Database 11g. The Oracle Database 11g software was using the default `SQLNET.ALLOWED_LOGON_VERSION` setting of `8` at that time. Because case insensitivity is enabled by default, their passwords are now case sensitive, as is the password for `preston`.

- User `preston`: This account was imported from an Oracle Database 11g database that was running in Exclusive Mode (`SQLNET.ALLOWED_LOGON_VERSION = 12`).

- User `blake`: This account still uses the Oracle Database 10g password version. At this stage, user `blake` is prevented from logging in.

### Resetting User Passwords That Use the 10G Password Version

For better security, remove the `10G` password version from the accounts of all users. In the following procedure, to reset the passwords of users who have the `10G` password version, you must temporarily relax the `SQLNET.ALLOWED_LOGON_VERSION_SERVER` setting, which controls the ability level required of clients before login can be allowed. Relaxing the setting enables these users to log in and change their passwords, and hence generate the newer password versions in addition to the `10G` password version. Afterward, you can set the database to use Exclusive Mode and ensure that the clients have the `O5L_NP` capability. Then the users can reset their passwords again, so that their password versions no longer include `10G`, but only have the more secure `11G` and `12C` password versions.

1.  Query the `DBA_USERS` view to find users who only use the `10G` password version.
        SELECT USERNAME FROM DBA_USERS
        WHERE ( PASSWORD_VERSIONS = '10G '
        OR PASSWORD_VERSIONS = '10G HTTP ')
        AND USERNAME <> 'ANONYMOUS';
2.  Configure the database so that it does not run in Exclusive Mode, as follows:
    1.  Edit the `SQLNET.ALLOWED_LOGON_VERSION_SERVER` setting in the `sqlnet.ora` file so that it is more permissive than the default. For example:
            SQLNET.ALLOWED_LOGON_VERSION_SERVER=11
    2.  Restart the database.
3.  Expire the users that you found when you queried the `DBA_USERS` view to find users who only use the `10G` password version.
    You must expire the users who have only the `10G` password version, and do not have one or both of the `11G` or `12C` password versions.

    For example:

        ALTER USER username PASSWORD EXPIRE;
4.  Ask the users whose passwords you expired to log in.
    When the users log in, they are prompted to change their passwords. The database generates the missing `11G` and `12C` password versions for their account, in addition to the `10G` password version. The `10G` password version continues to be present, because the database is running in the permissive mode.
5.  Ensure that the client software with which the users are connecting has the `O5L_NP` ability.
    All Oracle Database release 11.2.0.3 and later clients have the `O5L_NP` ability. If you have an earlier Oracle Database client, then you must install the CPUOct2012 patch.
6.  After all clients have the `O5L_NP` capability, set the security for the server back to Exclusive Mode, as follows:
    1.  Remove the `SEC_CASE_SENSITIVE_LOGON` parameter setting from the instance initialization file, or set `SEC_CASE_SENSITIVE_LOGON` to `TRUE`.
            SEC_CASE_SENSITIVE_LOGON = TRUE
    2.  Remove the `SQLNET.ALLOWED_LOGON_VERSION_SERVER` parameter from the server `sqlnet.ora` file, or set the value of `SQLNET.ALLOWED_LOGON_VERSION_SERVER` in the server `sqlnet.ora` file back to `12`, to set it to an Exclusive Mode.
            SQLNET.ALLOWED_LOGON_VERSION_SERVER = 12
    3.  Restart the database.
7.  Find the accounts that still have the `10G` password version.
        SELECT USERNAME FROM DBA_USERS
        WHERE PASSWORD_VERSIONS LIKE '%10G%'
        AND USERNAME <> 'ANONYMOUS';
8.  Expire the accounts that still have the `10G` password version.
        ALTER USER username PASSWORD EXPIRE;
9.  Ask these users to log in to their accounts.
    When the users log in, they are prompted to reset their passwords. The database then generates only the `11G` and `12C` password versions for their accounts. Because the database is running in Exclusive Mode, the `10G` password version is no longer generated.
10. Rerun the following query:
        SELECT USERNAME FROM DBA_USERS
        WHERE PASSWORD_VERSIONS LIKE '%10G%'
        AND USERNAME <> 'ANONYMOUS';

    If this query does not return any results, then it means that no user accounts have the `10G` password version. Hence, the database is running in a more secure mode than in previous releases.

**Parent topic:** [Reset Passwords to Enforce Case-Sensitivity](reset-passwords-to-enforce-case-sensitivity.md)
