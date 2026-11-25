After the gateway is installed and configured, you can use the gateway to access data in non-Oracle systems, pass native commands from applications to the non-Oracle system, perform distributed queries, and copy data.

### Using the Pass-Through Feature

The gateway can pass native commands or statements from the application to the non-Oracle system using the `DBMS_HS_PASSTHROUGH` package.

Use the `DBMS_HS_PASSTHROUGH` package in a PL/SQL block to specify the statement to be passed to the non-Oracle system, as follows:

    DECLARE
        num_rows INTEGER;
    BEGIN
        num_rows := DBMS_HS_PASSTHROUGH.EXECUTE_IMMEDIATE@SYBS('command');
    END;
    /

Where command cannot be one of the following:

- `BEGIN TRANSACTION`

- `COMMIT`

- `ROLLBACK`

- `SAVE`

- `SHUTDOWN`

The `DBMS_HS_PASSTHROUGH` package supports passing bind values and executing `SELECT` statements.

**Note:**

`TRUNCATE` cannot be used in a pass-through statement.

As a general rule it is recommended that you `COMMIT` after each DDL statement in the pass-through especially when going to a Sybase database.

**See Also:**

[Oracle Database PL/SQL Packages and Types Reference](../arpls/DBMS_HS_PASSTHROUGH.md) and [Oracle Database Heterogeneous Connectivity User's Guide](../heter/oracle-database-gateways-features.md) for more information about the `DBMS_HS_PASSTHROUGH` package.

### Using AUTO COMMIT

Some non-Oracle databases operate without logging. If read-only capability is desired under such environment, you need to set the `HS_TRANSACTION_MODEL` gateway parameter.

The `HS_TRANSACTION_MODEL` parameter can be set as follows:

`HS_TRANSACTION_MODEL=READ_ONLY_AUTOCOMMIT`

However, if you still need to have update capability, then set `HS_TRANSACTION_MODEL=SINGLE_SITE_AUTOCOMMIT` in the gateway initialization parameter file. Any update is committed immediately. Commit-confirm is not allowed for the targets operating without logging.

### Known Restrictions

If you encounter incompatibility problems not listed in this section or in "Known Problems", contact Oracle Support Services.

The following are the known restrictions:

- Pass-through queries cannot read `BLOB` and `CLOB` data

- Updates or deletes that include unsupported functions within a `WHERE` clause are not allowed

- Oracle Database Gateway for ODBC does not support stored procedures

- Cannot participate in distributed transactions; only single-site transactions supported

- Does not support multithreaded agents

- Does not support updating `LONG` columns with bind variables

- Does not support rowids

#### COMMIT or ROLLBACK in PL/SQL Cursor Loops Closes Open Cursors

Any `COMMIT` or `ROLLBACK` issued in a PL/SQL cursor loop closes all open cursors, which can result in an error.

The following error can occur:

    ORA-1002:  fetch out of sequence

To prevent this error, move the `COMMIT` or `ROLLBACK` statement outside the cursor loop.

#### SQL Syntax Restrictions

Oracle Database Gateway for ODBC has the following restrictions on SQL syntax.

##### WHERE CURRENT OF Clause

`UPDATE` and `DELETE` statements with the `WHERE CURRENT OF` clause are not supported by the gateway because they rely on the Oracle `ROWID` implementation. To update or delete a specific row through the gateway, a condition style `WHERE` clause must be used.

##### CONNECT BY Clause

The gateway does not support the `CONNECT BY `clause in a `SELECT` statement.

##### ROWID

The Oracle `ROWID` implementation is not supported.

##### EXPLAIN PLAN Statement

The `EXPLAIN PLAN` statement is not supported.

- SQL\*Plus `COPY` Command with Lowercase Table Names

  Wrap lower case table name in double quotes.

  For example:

      copy from tkhouser/tkhouser@inst1 insert loc_tkhodept using select * from "tkhodept"@holink2;

- Database Links

  The gateway is not multithreaded and cannot support shared database links. Each gateway session spawns a separate gateway process and connections cannot be shared.

**See Also:**

[Supported SQL Syntax and Functions](database-gateway-odbc-supported-syntax-function.md) for more information about restrictions on SQL syntax.

#### CALLBACK Links Support

Oracle Database Gateway for ODBC does not support `CALLBACK` links.

Trying a `CALLBACK` link with the gateway will return the following error message:

    ORA-02025: All tables in the SQL statement must be at the remote database

### Known Problems

This section describes known problems and includes suggestions for correcting them when possible. If you have any questions or concerns about the problems, contact Oracle Support Services.

#### Encrypted Format Login

Oracle database automatically encrypts the password.

Oracle database no longer supports the initialization parameter `DBLINK_ENCRYPT_LOGIN`. Up to version 7.3, this parameter's default `TRUE` value prevented the password for the login user ID from being sent over the network (in the clear). Later versions automatically encrypt the password.

#### Date Arithmetic

This topic describes SQL expressions that do not function correctly with the gateway.

    date + number
    number + date
    date - number
    date1 - date2

Statements with the preceding expressions are sent to the non-Oracle system without any translation. If the non-Oracle system does not support these date arithmetic functions, then the statements return an error.
