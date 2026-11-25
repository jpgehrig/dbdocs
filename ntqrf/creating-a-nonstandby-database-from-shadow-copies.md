Use this procedure to create a nonstandby database from shadow copies.

This section assumes that you are duplicating the database on a host with the same file system structure as the primary database.

To create a nonstandby database from shadow copies:

1.  Restore the database on the new host.
2.  Start a SQL\*Plus session on the duplicate database and obtain the DBID. You can query the DBID as follows:
        SELECT DBID FROM V$DATABASE;
3.  Shut down the database consistently. You can shut down the database as follows:
        SHUTDOWN;
4.  Use the DBNEWID utility to change the DBID.
5.  Open the database.
6.  Start a SQL\*Plus session on the duplicate database and query the DBID. You can query the DBID as follows:
        SELECT DBID FROM V$DATABASE;

    **See Also:**

    [Oracle Database Utilities](../sutil/oracle-dbnewid-utility.md) for information about how to use DBNEWID

**Related Topics**

- [Performing Disaster Recovery](performing-disaster-recovery.md)

**Parent topic:** [About Duplicating a Database](about-duplicating-a-database.md)
