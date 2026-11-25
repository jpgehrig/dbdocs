After the gateway is installed and configured, you can use the gateway to access Informix data, pass Informix commands from applications to the Informix database, perform distributed queries, and copy data.

### Remote Insert Rowsource

A remote insert rowsource feature allows remote insert requiring local Oracle data to work through the Oracle database and Oracle Database Gateway. This functionality requires that the Oracle database and the Oracle Database Gateway to be version 12.2 or later.

By Oracle Database design, some distributed statement must be executed at the database link site. But in certain circumstances, there is data needed to execute these queries that must be fetched from the originating Oracle Database. Under homogeneous connections, the remote Oracle database would call back the source Oracle database for such data. But in heterogeneous connections, this is not viable, because this means that the Foreign Data Store would have to query call back functions, or data, that can only be provided by the Oracle instance that issued the query. In general, these kinds of statements are not something that can be supported through the Oracle Database Gateway.

The following categories of SQL statements results in a callback:

- Any DML with a sub-select, which refers to a table in Oracle database.

- Any `DELETE`, `INSERT`, `UPDATE` or "`SELECT... FOR UPDATE..."` SQL statement containing SQL functions or statements that needs to be executed at the originating Oracle database.

  These SQL functions include `USER`, `USERENV`, and `SYSDATE`; and involve the selection of data from the originating Oracle database.

- Any SQL statement that involves a table in Oracle database, and a `LONG` or `LOB` column in a remote table.

An example of a remote `INSERT` statement that can work through the remote insert rowsource feature is as follows:

    INSERT INTO gateway_table@gateway_link select * from local_table;

### Using the Pass-Through Feature

The gateway can pass Informix commands or statements from the application to the Informix database using the `DBMS_HS_PASSTHROUGH` package.

Use the `DBMS_HS_PASSTHROUGH` package in a PL/SQL block to specify the statement to be passed to the Informix database, as follows:

    DECLARE
        num_rows INTEGER;
    BEGIN
        num_rows := DBMS_HS_PASSTHROUGH.EXECUTE_IMMEDIATE@IFMX('command');
    END;
    /

Where command cannot be one of the following:

- `COMMIT`

- `CREATE DATABASE`

- `DROP DATABASE`

- `ROLLBACK`

- `ROLLFORWARD DATABASE`

- Informix tool commands

The `DBMS_HS_PASSTHROUGH` package supports passing bind values and executing `SELECT` statements.

**Note:**

It is recommended that you `COMMIT` after each DDL statement in the pass-through.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_HS_PASSTHROUGH.md) and [Chapter 3, Features of Oracle Database Gateways,](../heter/oracle-database-gateways-features.md) of Oracle Database Heterogeneous Connectivity User's Guide for more information about the `DBMS_HS_PASSTHROUGH` package.

### CHAR Semantics

This feature allows the gateway to optionally run in `CHAR` semantics mode.

Rather than always describing Informix `CHAR` columns as `CHAR(n BYTE)`, this feature describes them as `CHAR(n CHAR)` and `VARCHAR(n CHAR)`. The concept is similar to Oracle database `CHAR` semantics. You need to specify `HS_NLS_LENGTH_SEMANTICS=CHAR` gateway parameter to activate this option.

**See Also:**

[Initialization Parameters](database-gateway-for-informix-initialization-parameters.md)

### Multi-byte Character Sets Ratio Suppression

This feature optionally suppresses the ratio expansion from Informix database to Oracle database involving multi-byte character set.

By default, Oracle gateways assume the worst ratio to prevent data being truncated or insufficient buffer size situation. However, if you have specific knowledge of your Informix database and do not want the expansion to occur, you can specify `HS_KEEP_REMOTE_COLUMN_SIZE` parameter to suppress the expansion.

**See Also:**

[Initialization Parameters](database-gateway-for-informix-initialization-parameters.md)

### IPv6 Support

Besides full IPv6 support between Oracle databases and the gateway, IPv6 is also supported between this gateway and Informix database.

**See Also:**

[Initialization Parameters](database-gateway-for-informix-initialization-parameters.md) for more detail about the `HS_FDS_CONNECT_INFO` parameter.

### Gateway Session IDLE Timeout

You can optionally choose to terminate long idle gateway sessions automatically with the gateway parameter `HS_IDLE_TIMEOUT`. Specifically, when a gateway session is idle for more than the specified time limit, the gateway session is terminated with any pending update rolled back. Refer to the `HS_IDLE_TIMEOUT` parameter in [Initialization Parameters](database-gateway-for-informix-initialization-parameters.md) for more detail.

### Database Compatibility Issues for Informix

Informix and Oracle databases function differently in some areas, causing compatibility problems. The compatibility issues are described in the following links:

- ANSI SQL Standard

- Naming Rules

- Data Types

- Queries

- Locking

#### ANSI SQL Standard

The American National Standards Institute (ANSI) has established a set of industry standards for SQL. The gateway supports only Informix databases that comply with the ANSI standard. For more information about how to create or start up an ANSI-compliant Informix database, refer to your Informix documentation.

#### Naming Rules

Naming rule issues include the following:

- Rules for Naming Objects

- Object Names

- Case Sensitivity

##### Rules for Naming Objects

Oracle and Informix use different database object naming rules. For example, the maximum number of characters allowed for each object name can be different. Also, the use of single and double quotation marks, case sensitivity, and the use of alphanumeric characters can all be different.

**See Also:**

[Oracle Database Reference](../refrn/index.md) and Informix documentation.

##### Object Names

Names of Informix database objects are limited to a maximum of 18 characters. An object name can be composed of these characters:

- Numbers 0 to 9

- Lowercase letters a to z

- Uppercase letters A to Z

- Underscore character (\_)

##### Case Sensitivity

Informix handles letter case differently from Oracle. Informix uses these rules:

- Table owner names default to uppercase letters, unless the name is surrounded by double quote characters

- Column names, table names, view names, and so on, are always treated as lowercase letters

The Oracle database defaults to uppercase unless you surround identifiers with double quote characters. For example, to refer to the Informix table called `emp`, enter the name with double quote characters, as follows:

    SQL> SELECT * FROM "emp"@IFMX;

However, to refer to the Informix table called `emp` owned by `SCOTT` from an Oracle application, enter the following:

    SQL> SELECT * FROM "Scott"."emp"@IFMX;

If the Informix table called `emp` is owned by `SCOTT`, a table owner name in uppercase letters, you can enter the owner name without double quote characters, as follows:

    SQL> SELECT * FROM SCOTT."emp"@IFMX;

Or

    SQL> SELECT * FROM scott."emp"@IFMX;

Oracle recommends that you surround all Informix object names with double quote characters and use the exact letter case for the object names as they appear in the Informix data dictionary. This convention is not required when referring to the supported Oracle data dictionary tables or views listed in [Data Dictionary](database-gateway-for-informix-data-dictionary.md).

If existing applications cannot be changed according to these conventions, create views in Oracle to associate Informix names to the correct letter case. For example, to refer to the Informix table `emp` from an existing Oracle application by using only uppercase names, define the following view:

    SQL> CREATE VIEW EMP (EMPNO, ENAME, SAL, HIREDATE)
          AS SELECT "empno", "ename", "sal", "hiredate"
          FROM "emp"@IFMX;

With this view, the application can issue statements such as the following:

    SQL> SELECT EMPNO, ENAME FROM EMP;

Using views is a workaround solution that duplicates data dictionary information originating in the Informix data dictionary. You must be prepared to update the Oracle view definitions whenever the data definitions for the corresponding tables are changed in the Informix database.

#### Data Types

Data type issues include the following:

- Binary\_ Byte and Text Literal Notation

- Data Type Conversion

##### Binary, Byte and Text Literal Notation

Oracle SQL uses hexadecimal digits surrounded by single quotes to express literal values being compared or inserted into columns defined as data type `RAW`.

This notation is not converted to syntax compatible with Informix `BINARY`, `BYTE` and `TEXT` data types (a 0x followed by hexadecimal digits, surrounded by single quotes).

For example, the following statement is not supported:

    SQL> INSERT INTO BYTE_TAB@IFMX VALUES ('Oxff');

Where `BYTE_TAB` contains a column of data type `BINARY`, `BYTE` or `TEXT`. Use bind variables when inserting into or updating `BINARY`, `BYTE` or `TEXT` data types.

##### Data Type Conversion

Informix does not support implicit date conversions. Such conversions must be explicit.

For example, the gateway issues an error for the following `SELECT` statement:

    SQL> SELECT DATE_COL FROM TEST@IFMX
         WHERE DATE_COL = "1-JAN-2001";

To avoid problems with implicit conversions, add explicit conversions, as in the following:

    SQL> SELECT DATE_COL FROM TEST@IFMX
         WHERE DATE_COL = TO_DATE("1-JAN-2001");

**See Also:**

[Data Type Conversion](database-gateway-for-informix-data-type-conversion.md) for more information about restrictions on data types.

#### Queries

Query issues include the following:

- Row Selection

- Empty Strings

- Empty Bind Variables

##### Row Selection

Informix evaluates a query condition for all selected rows before returning any of the rows. If there is an error in the evaluation process for one or more rows, no rows are returned even though the remaining rows satisfy the condition.

Oracle evaluates the query condition row-by-row and returns a row when the evaluation is successful. Rows are returned until a row fails the evaluation.

##### Empty Strings

Oracle processes an empty string in a SQL statement as a null value. Informix processes an empty string as an empty string.

Comparing to an empty string

The gateway passes literal empty strings to the Informix database without any conversion. If you intended an empty string to represent a null value, Informix does not process the statement that way; it uses the empty string.

You can avoid this problem by using `NULL` or `IS NULL` in the SQL statement instead of the empty string syntax, as in the following example:

    SELECT * from "emp"@IFMX where "ename" IS NULL;

Selecting an empty string

For `VARCHAR` columns, the gateway returns an empty string to the Oracle database as `NULL` value.

For `CHAR` columns, the gateway returns the full size of the column with each character as empty space (' ').

##### Empty Bind Variables

For `VARCHAR` bind variables, the gateway passes empty bind variables to the Informix database as a `NULL` value.

#### Locking

The locking model for an Informix database differs significantly from the Oracle model. The gateway depends on the underlying Informix behavior, so the following possible scenarios can affect Oracle applications that access Informix through the gateway:

- Read access might block write access

- Write access might block read access

- Statement-level read consistency is not guaranteed

  **See Also:**

  Informix documentation for information about the Informix locking model.

### Known Restrictions

If you encounter incompatibility problems not listed in this section or in "Known Problems", contact Oracle Support Services. The following topics describe the known restrictions and includes suggestions for dealing with them when possible:

- Transactional Integrity

- Transaction Capability

- COMMIT or ROLLBACK in PL/SQL Cursor Loops Closes Open Cursors

- Pass-Through Feature

- Informix SMALLFLOAT and REAL Data Types

- SQL Syntax

- SQL\*Plus

- Database Links

- Gateway Data Dictionary Views

- Stored Procedures

**Note:**

If you have any questions or concerns about the restrictions, contact Oracle Support Services.

#### Transactional Integrity

The gateway cannot guarantee transactional integrity in the following cases:

- When a statement that is processed by the gateway causes an implicit commit in the target database

- When the target database is configured to work in autocommit mode

  **Note:**

  Oracle strongly recommends the following:

  - If you know that executing a particular statement causes an implicit commit in the target database, then ensure that this statement is executed in its own transaction.

  - Do not configure the target database to work in autocommit mode.

#### Transaction Capability

The gateway does not support savepoints. If a distributed update transaction is under way involving the gateway and a user attempts to create a savepoint, the following error occurs:

    ORA-02070: database dblink does not support savepoint in this context

By default, the gateway is configured as `COMMIT_CONFIRM` and in this transaction mode it is always the commit point site when the Informix database is updated by the transaction.

If your Informix system does not use logging, then you cannot use the default transaction capability. It is strongly recommended that you enable logging in your Informix system. If you are not using logging, and have read only requirement, then set `HS_TRANSACTION_MODEL=READ_ONLY_AUTOCOMMIT` in the gateway initialization parameter file. If you are not using logging, and you require to update the Informix database, then set `HS_TRANSACTION_MODEL=SINGLE_SITE_AUTOCOMMIT` in the gateway initialization parameter file.

**See Also:**

[Initialization Parameters](database-gateway-for-informix-initialization-parameters.md) and the [Oracle Database Heterogeneous Connectivity User's Guide](../heter/index.md) for more information about customizing the initialization parameter file.

#### COMMIT or ROLLBACK in PL/SQL Cursor Loops Closes Open Cursors

Any `COMMIT` or `ROLLBACK` issued in a PL/SQL cursor loop closes all open cursors, which can result in the following error:

    ORA-1002:  fetch out of sequence

To prevent this error, move the `COMMIT` or `ROLLBACK` statement outside the cursor loop.

#### Pass-Through Feature

If the SQL statements being passed through the gateway result in an implicit commit at the Informix database, the Oracle transaction manager is unaware of the commit and an Oracle `ROLLBACK` command cannot be used to roll back the transaction.

#### Informix SMALLFLOAT and REAL Data Types

Informix `SMALLFLOAT` and `REAL` data types have a precision of `6`.

#### SQL Syntax

Restrictions on SQL syntax are listed as follows:

- WHERE CURRENT OF Clause

- CONNECT BY Clause

- Use of NULL Keyword in SELECT Statement

- Subqueries in INSERT Statement

- Subqueries in DELETE\_ INSERT\_ and UPDATE Statements

- ROWID

- EXPLAIN PLAN Statement

**See Also:**

[Supported SQL Syntax and Functions](database-gateway-for-informix-supported-sqlsyntax-functions.md) for more information about restrictions on SQL syntax.

##### WHERE CURRENT OF Clause

`UPDATE` and `DELETE` statements with the `WHERE` `CURRENT` `OF` clause are not supported by the gateway because they rely on the Oracle `ROWID` implementation. To update or delete a specific row through the gateway, a condition style `WHERE` clause must be used.

##### CONNECT BY Clause

The gateway does not support the `CONNECT BY` clause in a `SELECT` statement.

##### Use of NULL Keyword in SELECT Statement

The `NULL` keyword cannot be used in the select list of a `SELECT` statement because that syntax is not `ANSI SQL`.

For example, the following statement cannot be used:

    SQL> SELECT NULL FROM . . .

##### Subqueries in INSERT Statement

Subqueries of `INSERT` statements cannot use multiple aliases for the same table. For example, the following statement is not supported:

    SQL> INSERT INTO "emp_target"@IFMX
             SELECT a."empno" FROM "emp_source"@IFMX a,
                "emp_source"@IFMX b WHERE b."empno"=9999

##### Subqueries in DELETE, INSERT, and UPDATE Statements

SQL statements in subqueries of `DELETE`, `INSERT`, and `UPDATE` statements cannot refer to the same table as specified in the outer query. This is because of the locking mechanism in Informix.

##### ROWID

The Oracle `ROWID` implementation is not supported.

##### EXPLAIN PLAN Statement

The `EXPLAIN PLAN` statement is not supported.

#### SQL\*Plus

In SQL\*Plus, the gateway does not support using a `SELECT` statement to retrieve data from an Informix column defined as data type `BYTE`.

You need to use double quotes to wrap around lowercase table names, for example:

    copy from tkhouser/tkhouser@inst1 insert loc_tkhodept using select* from "tkhodept"@holink2;

#### Database Links

The gateway is not multithreaded and cannot support shared database links. Each gateway session spawns a separate gateway process and connections cannot be shared.

#### Gateway Data Dictionary Views

Only the first 64 characters of the view definition are returned when querying `ALL_VIEWS` and `USER_VIEWS` in the gateway data dictionary.

#### Stored Procedures

The gateway does not support the procedure feature that allows the execution of stored procedures in a non-Oracle database.

### Known Problems

This section lists known problems and includes suggestions for correcting them when possible. If you have any questions or concerns about the problems, contact Oracle Support Services. A current list of problems is available online. Contact your local Oracle office for information about accessing the list.

The known problems are as follows:

- Encrypted Format Login

- Informix BYTE and TEXT Data Types

- Schema Names and PL/SQL

- Data Dictionary Views and PL/SQL

#### Encrypted Format Login

Oracle database no longer supports the initialization parameter `DBLINK_ENCRYPT_LOGIN`. Up to version 7.3, this parameter's default `TRUE` value prevented the password for the login user ID from being sent over the network (in the clear). Later versions automatically encrypt the password.

#### Informix BYTE and TEXT Data Types

The following restrictions apply when using `BYTE` and `TEXT` data types:

- An unsupported SQL function cannot be used in a SQL statement that accesses a column defined as Informix data type `TEXT`.

- You cannot use SQL\*Plus to select data from a column defined as Informix data type `TEXT` when the data is greater than 80 characters in length. Oracle recommends using Pro\*C or Oracle Call Interface to access such data in a Informix database.

- `BYTE` and `TEXT` data types must be `NULLABLE` for `INSERT` or `UPDATE` to work.

- A table including a `BYTE` or `TEXT` column must have a unique index defined on the table or the table must have a separate column that serves as a primary key.

- `BYTE` and `TEXT` data in a view cannot be accessed.

- `BYTE` and `TEXT` data cannot be read through pass-through queries.

- Data less than 32,739 bytes cannot be inserted into `BYTE` and `TEXT` columns using bind variables.

The gateway does not support the PL/SQL function `COLUMN_VALUE_LONG` of the `DBMS_SQL` package.

**See Also:**

[Supported SQL Syntax and Functions](database-gateway-for-informix-supported-sqlsyntax-functions.md).

#### Schema Names and PL/SQL

If you do not prefix an Informix database object with its schema name in a SQL statement within a PL/SQL block, the following error message occurs:

    ORA-6550 PLS-201 Identifier table_name must be declared.

Change the SQL statement to include the schema name of the object.

#### Data Dictionary Views and PL/SQL

You cannot refer to data dictionary views in SQL statements that are inside a PL/SQL block.
