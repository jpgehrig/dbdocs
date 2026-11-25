Learn how to start and shut down a database with SQL \*Plus.

These instructions assume that a database instance has been created.

**Note:**

Directory path examples in this chapter follow Optimal Flexible Architecture (OFA) guidelines. If you specified directories during installation that do not comply with OFA guidelines, then your directory paths differ.

To start or shut down Oracle Database:

1.  Go to your Oracle Database server.
2.  Start SQL\*Plus at the command prompt:
        C:\> sqlplus /NOLOG
3.  Connect to Oracle Database with username SYSDBA:
        SQL> CONNECT / AS SYSDBA
4.  To start a database, enter:
        SQL> STARTUP [PFILE=path\filename]

    This command uses the initialization parameter file specified in `path``\``filename`. To start a database using a file named `init2.ora` located in `C:\app\username\product\11.2.0\admin\orcl\pfile, `enter:

        SQL> STARTUP PFILE=C:\app\username\product\11.2.0\admin\orcl\pfile\init2.ora

    If no `PFILE` is specified, then the command looks for an `SPFILE` in `ORACLE_HOME``\database`. If the command finds one, then the command uses it to start the database. If it does not find an `SPFILE`, then it uses the default initialization parameter file located in `ORACLE_BASE``\ADMIN\db_name\pfile`.
5.  To stop a database, enter:
        SQL> SHUTDOWN [mode]

    The mode is `normal`, `immediate`, or `abort`.

    In a `normal` shutdown, Oracle Database waits for all currently connected users to disconnect and disallows any new connections before shutting down. This is the default mode.

    In an `immediate` shutdown, Oracle Database terminates and rolls back active transactions, disconnects clients, and shuts down.

    In an `abort` shutdown, Oracle Database terminates active transactions and disconnects users; it does not roll back transactions. The database performs automatic recovery and rollback the next time it is started. Use this mode only in emergencies.

**See Also:**

[Oracle Database Installation Guide for Microsoft Windows](../ntdbi/index.md) for more information about "Optimal Flexible Architecture"

**Parent topic:** [Administering a Database on Windows](administering-database-on-windows.md)
