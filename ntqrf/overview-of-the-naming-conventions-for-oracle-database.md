All the mounted Oracle Database servers in a network must have unique database names.

When a database is created, a name is associated with it and stored in its control files. If you provide the database keyword, either in the `CREATE DATABASE` statement or when prompted by Database Configuration Assistant, then that value becomes the name for that database.

If you attempt to mount two Oracle Database servers with the same database name, then you receive the following error during mounting of the second server:

    ORA-01102: cannot mount database in EXCLUSIVE mode

If there are two or more Oracle Database servers on the same computer, but located in different Oracle homes, then the following rules apply:

- Each database name must be unique

- Each SID must be unique

To change the name of an existing database, you must use the `CREATE CONTROLFILE` statement to re-create your control files and specify a new database name.

**Parent topic:** [Postinstallation Database Creation on Windows](postinstallation-database-creation-on-windows.md)
