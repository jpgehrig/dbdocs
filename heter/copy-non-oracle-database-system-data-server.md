The `CREATE TABLE` statement lets you copy data from a non-Oracle database to the Oracle database.

To create a table on the local database and insert rows from the non-Oracle table, use the following syntax:

    CREATE TABLE table_name AS query;

The following example creates the table `emp` in the local Oracle database and inserts the rows from the `EMP` table of the non-Oracle database:

    CREATE TABLE table1 AS SELECT * FROM "EMP"@remote_db;

Alternatively, you can use the SQL\*Plus `COPY` command to copy data from the non-Oracle database to the Oracle database server.

**See Also:**

[SQL\*Plus User's Guide and Reference](../sqpug/SQL-Plus-COPY-command.md) for more information about the `COPY` command

**Parent topic:** [Using Heterogeneous Services Agents](using-heterogeneous-services-agents.md)
