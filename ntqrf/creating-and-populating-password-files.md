Use Password Utility to create password files. Password Utility is automatically installed with Oracle Database utilities.

Password files are located in the directory `ORACLE_HOME``\database` and are named `PWD``sid``.ora`, where `SID` identifies the Oracle Database instance. Password files can be used for local or remote connections to Oracle Database.

To create and populate a password file:

1.  Create a password file with Password Utility:
        C:\> orapwd FILE=PWDsid.ora ENTRIES=max_users

    - `FILE` specifies the password file name.

    - `SID` identifies the database instance.

    - `ENTRIES` sets the maximum number of entries in the password file. This corresponds to maximum number of distinct users allowed to connect to the database simultaneously with either the SYSDBA or the SYSOPER DBA privilege.
2.  Set the initialization parameter file parameter `REMOTE_LOGIN_PASSWORDFILE` to `exclusive`, `shared`, or `none`.
    The value `exclusive` specifies that only one instance can use the password file and that the password file contains names other than `SYS`. In search of the password file, Oracle Database looks in the registry for the value of the parameter `ORA_SID_PWFILE`. If no value is specified, then Oracle Database looks in the registry for the value of the parameter `ORA_PWFILE`, which points to a file containing user names, passwords, and privileges. If that is not set, then Oracle Database uses the default:

        ORACLE_HOME\DATABASE\PWDsid.ORA.

    The default value is `shared`. It specifies that multiple instances (for example, an Oracle RAC environment) can use the password file. However, the only user recognized by the password file is `SYS`. Other users cannot log in with `SYSOPER` or `SYSDBA` privileges even if those privileges are granted in the password file. The `shared` value of this parameter affords backward compatibility with earlier Oracle releases. Oracle Database looks for the same files as it does when the value is `exclusive`.

    The value `none` specifies that Oracle Database ignores the password file and that authentication of privileged users is handled by the Windows operating system.
3.  Start SQL\*Plus:
        C:\> sqlplus /NOLOG
4.  Connect `AS SYSDBA`:
        SQL> CONNECT / AS SYSDBA

    For an Oracle ASM instance, connect `AS SYSASM`:

        SQL> CONNECT / AS SYSASM
5.  Start Oracle Database:
        SQL> STARTUP
6.  Grant appropriate privileges to each user. Users who must perform database administration, for example, are granted the `SYSDBA` privilege:
        SQL> GRANT SYSDBA TO db_administrator;

    For an Oracle ASM instance:

        SQL> GRANT SYSASM TO SYS;

    If the grant is successful, then the following message is displayed:

        Statement Processed.

    This adds `smith` to the password file and enables `smith` to connect to the database with `SYSDBA` privileges. Use SQL\*Plus to add or delete user names, user passwords, and user privileges in password files.

    **Note:**

    Copying or manually moving password files might result in ORADIM being unable to find a password to start an instance.

- [Viewing and Hiding the Password File](viewing-and-hiding-the-password-file.md)
  Use this procedure to make the password file visible or invisible from different locations.

**Parent topic:** [Administering a Database on Windows](administering-database-on-windows.md)
