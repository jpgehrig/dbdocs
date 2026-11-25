Heterogeneous Services supports callback links.

This enables SQL statements like the following to be executed:

    INSERT INTO table_name@dblink SELECT column_list FROM table_name;

Even though Heterogeneous Services supports the callback functionality, not all gateways have implemented it. If the gateway that you are using has not implemented this functionality, the preceding `INSERT` statement returns the following error message:

    ORA-02025: All tables in the SQL statement must be at the remote database

**See Also:**

Your gateway documentation for information about support for callback links

For gateways that do not support callback links, you can use the SQL\*Plus `COPY` command. The syntax is as follows:

    COPY FROM username@db_name-
       INSERT destination_table -
       USING query;

The following example selects all rows from the local Oracle `emp` table, inserts them into the `emp` table on the non-Oracle database, and commits the transaction:

    COPY FROM SCOTT@inst1 -
      INSERT EMP@remote_db -
      USING SELECT * FROM EMP;

The `COPY` command supports the `APPEND`, `CREATE`, `INSERT`, and `REPLACE` options. However, `INSERT` is the only option supported when copying to non-Oracle databases. The SQL\*Plus `COPY` command does not support copying to tables with lowercase table names. Use the following PL/SQL syntax with lowercase table names:

    DECLARE
        v1 oracle_table.column1%TYPE;
        v2 oracle_table.column2%TYPE;
        v3 oracle_table.column3%TYPE;
        .
        .
        .
        CURSOR cursor_name IS SELECT * FROM oracle_table;
    BEGIN
        OPEN cursor_name;
        LOOP
           FETCH cursor_name INTO v1, v2, v3, ... ;
           EXIT WHEN cursor_name%NOTFOUND;
           INSERT INTO destination_table VALUES (v1, v2, v3, ...);
        END LOOP;

        CLOSE cursor_name;
    END;

**See Also:**

[SQL\*Plus User's Guide and Reference ](../sqpug/SQL-Plus-COPY-command.md)for more information about the `COPY` command

**Parent topic:** [Using Heterogeneous Services Agents](using-heterogeneous-services-agents.md)
