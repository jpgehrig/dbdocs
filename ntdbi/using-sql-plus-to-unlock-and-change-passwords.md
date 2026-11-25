## Using SQL\*Plus to Unlock and Change Passwords

Use this SQL\*Plus procedure to unlock and reset user account passwords.

To change a password after installation:

1.  Start SQL\*Plus:
        C:\> sqlplus /nolog
2.  Connect as `SYSDBA`:
        SQL> CONNECT SYS AS SYSDBA
        Enter password: SYS_password
3.  Enter a command similar to the following, where `account` is the user account to unlock and `password` is the new password:
        SQL> ALTER USER account IDENTIFIED BY password ACCOUNT UNLOCK;

**See Also:**

- [Oracle Database Security Guide](../dbseg/managing-security-for-oracle-database-users.md)

- [Oracle Database SQL Language Reference](../sqlrf/Introduction-to-Oracle-SQL.md)

- [Oracle Database Administrator's Guide](../admin/getting-started-with-database-administration.md)

**Parent topic:** [Reviewing User Accounts and Passwords](reviewing-user-accounts-and-passwords.md)
