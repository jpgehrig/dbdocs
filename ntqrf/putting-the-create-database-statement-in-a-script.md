The `CREATE DATABASE` statement is a SQL statement that creates the database.

A script containing this statement can be used anytime you create a database.

The `CREATE DATABASE` statement has the following parameters:

- `MAXDATAFILES` - default value: 32, maximum value: 65534

- `MAXLOGFILES` - default value: 32, maximum value: 255

The `CHARACTER SET` parameter determines the database character set of the new database. The default value is US7ASCII, however the recommended value is AL32UTF8. AL32UTF8 is the Oracle implementation of the Unicode Standard character set in UTF-8 encoding form. Unicode is suitable for storing text in practically any written language of the world.

When you run the `CREATE DATABASE` statement, Oracle Database performs several operations depending upon the clauses that you specified in the `CREATE DATABASE` statement or the initialization parameters that you have set.

**Note:**

Oracle Managed Files is a feature that works with the `CREATE DATABASE` statement to simplify administration of Oracle Database. Oracle Managed Files eliminates the requirement to directly manage operating system files comprising an Oracle Database server, because you specify operations in terms of database objects rather than file names.

To create the database `prod`, copy and save the following statement in a file named `script_name``.sql`:

    CREATE DATABASE prod
    USER SYS IDENTIFIED BY sys_password
    USER SYSTEM IDENTIFIED BY system_password
    MAXLOGFILES 5
    MAXDATAFILES 100
    DATAFILE 'C:\app\username\oradata\prod\system01.dbf' SIZE 325M REUSE
    AUTOEXTEND ON NEXT 10240K MAXSIZE UNLIMITED
    UNDO TABLESPACE "UNDOTBS" DATAFILE 'app\username\oradata\prod\undotbs01.dbf'
    SIZE 200M REUSE AUTOEXTEND ON NEXT 5120K MAXSIZE UNLIMITED
    CHARACTER SET AL32UTF8
    logfile 'C:\app\username\oradata\prod\redo01.log' size 100M reuse,
            'C:\app\username\oradata\prod\redo02.log' size 100M reuse,
            'C:\app\username\oradata\prod\redo03.log' size 100M reuse
    Oracle Database Installation Guide for Microsoft WindowsEXTENT MANAGEMENT LOCAL;

**See Also:**

- [Oracle Database Administrator's Guide](../admin/using-oracle-managed-files.md) for more information about using Oracle Managed Files

- [Oracle Database Installation Guide for Microsoft Windows](../ntdbi/about-character-set-selection-during-installation.md) for more information about recommended database character sets

**Parent topic:** [Overview of Database Creation Tasks on Windows Using Command-Line Tools](overview-of-database-creation-tasks-on-windows-using-command-line-tools.md)
