Heterogeneous Services and the gateway rewrite SQL statements when the statements need to be translated or postprocessed.

For the following examples, assume the `INITCAP` function is not supported in the non-Oracle database. Consider a program that requests the following from the non-Oracle database. For example:

    SELECT "COLUMN_A" FROM "test"@remote_db
        WHERE "COLUMN_A" = INITCAP("COLUMN_B");

The non-Oracle database does not recognize the `INITCAP` function, so the Oracle database server fetches the data from the table `test` in the remote database and filters the results locally. The gateway rewrites the `SELECT` statement as follows:

    SELECT "COLUMN_A", "COLUMN_B" FROM "test"@remote_db;

The results of the query are sent from the gateway to Oracle and are filtered by the Oracle database server.

If a string literal or bind variable is supplied in place of `"COLUMN_B"` as shown in the previous example, the Heterogeneous Services component of the Oracle server would apply the `INITCAP` function before sending the SQL command to the gateway. For example, if the following SQL command is issued:

    SELECT "COLUMN_A" FROM "test"@remote_db WHERE "COLUMN_A" = INITCAP('jones');

The following SQL command would be sent to the gateway:

    SELECT "COLUMN_A" FROM "test"@remote_db WHERE "COLUMN_A" = 'Jones';

Consider the following `UPDATE` request:

    UPDATE "test"@remote_db SET "COLUMN_A" = 'new_value'
        WHERE "COLUMN_A" = INITCAP("COLUMN_B");

In this case, the Oracle database server and the gateway cannot compensate for the lack of support at the non-Oracle side, so an error is issued.

If a string literal or bind variable is supplied in place of `"COLUMN_B"` as shown in the preceding example, the Heterogeneous Services component of the Oracle server would apply the `INITCAP` function before sending the SQL command to the gateway. For example, if the following SQL command is issued:

    UPDATE "test"@remote_db SET "COLUMN_A" = 'new_value'
        WHERE "COLUMN_A" = INITCAP('jones');

The following SQL command would be sent to the gateway:

    UPDATE  "test"@remote_db SET "COLUMN_A" = 'new_value'
        WHERE "COLUMN_A" = 'Jones';

In previous releases, the preceding `UPDATE` statement would have raised an error due to the lack of `INITCAP` function support in the non-Oracle database.

- Data Type Checking Support for a Remote-Mapped Statement
  There is data type checking support for remote-mapped statements in a heterogeneous environment.

**Parent topic:** [Using Heterogeneous Services Agents](using-heterogeneous-services-agents.md)

### Data Type Checking Support for a Remote-Mapped Statement

There is data type checking support for remote-mapped statements in a heterogeneous environment.

The Oracle database has always performed data type checking and data type coercion in a homogeneous environment. For example, `SELECT * FROM EMP WHERE EMPNO='7934'` would return the same result as `SELECT * FROM EMPNO WHERE EMPNO=7934`. There is also full data type checking support for remote-mapped statements in a heterogeneous environment. In general, the operands in SQL statements whether its a column, literal, or bind variable would be processed internally for data type checking. Consider the following examples:

    SELECT * FROM EMP@LINK WHERE NUMBER_COLUMN='123'
    SELECT * FROM EMP@LINK WHERE NUMBER_COLUMN=CHAR_COLUMN;
    SELECT * FROM EMP@LINK WHERE NUMBER_COLUMN=CHAR_BIND_VARIABLE;

Most non-Oracle databases do not support data type coercion, and the previous statements fail if they are sent to a non-Oracle database as is. The Heterogeneous Services component for the Oracle database performs data type checking and the necessary data type coercion before sending an acceptable statement to a non-Oracle database.

Data type checking provides consistent behavior on post-processed or remote-mapped statements. Consider the following two statements:

    SELECT * FROM EMP@LINK WHERE TO_CHAR(EMPNO)='7933' + '1';

And:

    SELECT * FROM EMP@LINK WHERE EMPNO='7933' + '1';

Both of the previous statements provide the same result and coercion regardless if the `TO_CHAR` function is supported in the non-Oracle database or not. Now, consider the following statement:

    SELECT * FROM EMP@LINK WHERE EMPNO='123abc' + '1';

As data type checking is enforced, the coercion attempt within Oracle generates an error and returns it without sending any statements to a non-Oracle database.

In summary, there is consistent data type checking and coercion behavior regardless of post-processed or remote-mapped statements.

**Parent topic:** Oracle Database Server SQL Construct Processing
