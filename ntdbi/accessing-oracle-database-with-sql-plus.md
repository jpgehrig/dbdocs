## Accessing Oracle Database with SQL\*Plus

You can use SQL\*Plus to issue SQL and PL/SQL statements to the Oracle Database.

This tool enables you to perform the same database management operations, and query, insert, update, or delete data directly in the database.

To start SQL\*Plus, from the Start menu, select All Programs, then Oracle - HOMENAME, then Application Development, and then SQL Plus.

Alternatively, at the command line, you can enter the following command at a Windows command prompt:

    C:\> sqlplus /nolog
    SQL> CONNECT user_name
    Enter password: password

For example, to log on as SYSTEM using the password `password`, you enter:

    C:\> sqlplus /nolog
    SQL> CONNECT SYSTEM
    Enter password: password

If you are logging on as `SYS`, you must connect as `SYSDBA`:

    C:\> sqlplus /nolog
    SQL> CONNECT SYS AS SYSDBA
    Enter password: password

**See Also:**

- [SQL\*Plus User's Guide and Reference](../sqpug/SQL-Plus-user-interface.md)

- [SQL\*Plus Quick Reference](../sqpqr/index.md)

- [Oracle Database Administrator's Guide](../admin/getting-started-with-database-administration.md)

**Parent topic:** [Getting Started with Oracle Database](getting-started-with-oracle-database.md)
