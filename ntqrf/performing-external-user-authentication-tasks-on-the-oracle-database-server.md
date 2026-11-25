Use this procedure to perform external user authentication tasks.

Perform the following external user authentication tasks on the Oracle Database server:

1.  Add parameter `OS_AUTHENT_PREFIX` to your `init.ora` file.
    The `OS_AUTHENT_PREFIX` value is prefixed to local or domain user names attempting to connect to the server with the user's operating system name and password. The prefixed user name is compared with Oracle Database user names in the database when a connection request is attempted. Using parameter `OS_AUTHENT_PREFIX` with Windows native authentication methods is the recommended method for performing secure, trusted client connections to your server.
2.  Set a value for `OS_AUTHENT_PREFIX`. Your choices are:
    - Any character string

      If you specify `xyz`, as in this procedure's example, then `xyz` is prefixed to the beginning of the Windows user name (for example, `xyzjones` for local user `jones` or `xyzsales\jones` for domain user `jones` on domain `sales`).` `String values are case insensitive.

    - `""` (two double quotes with no space between)

      This option is recommended, because it eliminates the need for any prefix to Windows user names (for example, `jones` for local user `jones` or `sales\jones` for domain user `jones` on domain `sales`).

    - No value specified

      If you do not specify a value for `OS_AUTHENT_PREFIX`, it defaults to `OPS$` (for example, `OPS$jones` for local user `jones` or `OPS$sales\jones` for domain user `jones` on domain `sales`).

    **Note:**

    On Windows and Linux, create a database user name with characters in upper case for successful authentication. Authentication fails when you use characters with lower case. For example, authentication fails when creating a database user name with characters in lower case `ops$sales\jones`, but is successful when creating a database user name with upper case characters such as `OPS$SALES\JONES`.
3.  Create a Windows local user name for `jones` with the Computer Management tool, or create a Windows domain user name for `jones` with Active Directory Users and Computers (if the appropriate name does not currently exist). See your operating system documentation for detailed instructions.
4.  Ensure that parameter `SQLNET.AUTHENTICATN_SERVICES` in file `sqlnet.ora` contains `nts`.
5.  Start SQL\*Plus:
        C:\> sqlplus /NOLOG
6.  Connect to the database with the SYSTEM database administrator (DBA) name:
        SQL> CONNECT SYSTEM
        Enter password: system_password

    Unless you have changed it, the `SYSTEM` password is `MANAGER` by default.
7.  Create a local external user by entering:
        SQL> CREATE USER xyzjones IDENTIFIED EXTERNALLY;

    where `xyz` is the value you chose for initialization parameter `OS_AUTHENT_PREFIX`, and `jones` is the Windows local user name.
8.  Grant a local external user database roles by entering:
        SQL> GRANT DBA TO xyzjones;

    **Note:**

    External authentication of Windows Local users is supported from the same computer only. While external authentication of Windows Domain user is supported from the same computer or a different computer.
9.  Create a domain external user by entering:
        SQL> CREATE USER "XYZSALES\JONES" IDENTIFIED EXTERNALLY;

    where `XYZ` is the value you chose for initialization parameter `OS_AUTHENT_PREFIX`, and `SALES\JONES` is the domain name and Windows domain user name. Double quotes are required and the entire syntax must be in uppercase.
10. Grant a domain external user database roles by entering:
        SQL> GRANT DBA TO "XYZSALES\JONES";

    Double quotes are required and the entire syntax must be in uppercase.
11. Log on to the Windows system using the Windows local user `jones` or domain user `SALES\JONES`.
12. Connect to the database with the `SYSDBA` name:
        SQL> CONNECT / AS SYSDBA
13. Shut down the database:
        SQL> SHUTDOWN
14. Restart the database:
        SQL> STARTUP

    This causes the change to parameter `OS_AUTHENT_PREFIX` to take effect.

**Parent topic:** [About Manually Creating an External Operating System User](about-manually-creating-an-external-operating-system-user.md)
