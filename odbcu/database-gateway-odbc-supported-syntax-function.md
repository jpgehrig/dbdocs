The following topics describe SQL syntax and functions supported by Oracle Database Gateway for ODBC.

### Supported SQL Statements

Oracle Database Gateway for ODBC supports the `DELETE`, `INSERT`, `SELECT`, and `UPDATE` statements, but only if the ODBC driver and non-Oracle system can execute them and if the statements contain supported Oracle SQL functions.

With a few exceptions, the gateway provides full support for Oracle `DELETE`, `INSERT`, `SELECT`, and `UPDATE` statements.

The gateway does not support Oracle data definition language (DDL) statements. No form of the Oracle `ALTER`, `CREATE`, `DROP`, `GRANT`, or `TRUNCATE` statements can be used. Instead, for `ALTER`, `CREATE`, `DROP`, and `GRANT` statements, use the pass-through feature of the gateway if you need to use DDL statements against the non-Oracle system database.

**Note:**

`TRUNCATE` cannot be used in a pass-through statement.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/index.md) for detailed descriptions of keywords, parameters, and options.

#### DELETE

The `DELETE` statement is fully supported. However, only Oracle functions supported by the non-Oracle system can be used.

#### INSERT

The `INSERT` statement is fully supported. However, only Oracle functions supported by the non-Oracle system can be used.

#### SELECT

The `SELECT` statement is fully supported, with these exceptions:

- `CONNECT BY` `condition`

- `NOWAIT`

- `START WITH` `condition`

- `WHERE CURRENT` `OF`

- `FOR UPDATE`

#### UPDATE

The `UPDATE` statement is fully supported. However, only Oracle functions supported by the non-Oracle system can be used. Also, you cannot have SQL statements in the subquery that refer to the same table name in the outer query. Subqueries are not supported in the SET clause.

### Oracle Functions

All functions are evaluated by the non-Oracle system after the gateway has converted them to the native SQL. Only a limited set of functions are assumed to be supported by the non-Oracle system. Most Oracle functions have no equivalent function in this limited set. Consequently, although post-processing is performed by the Oracle database, Oracle Database Gateway for ODBC does not support many Oracle functions, possibly impacting performance.

If an Oracle SQL function is not supported by Oracle Database Gateway for ODBC, this function is not supported in `DELETE`, `INSERT`, or `UPDATE` statements. In `SELECT` statements, these functions are evaluated by the Oracle database and processed after they are returned from the non-Oracle system.

If an unsupported function is used in a `DELETE`, `INSERT`, or `UPDATE` statement, it generates the following Oracle error:

    ORA-02070: database db_link_name does not support function in this context

Oracle Database Gateway for ODBC assumes that ODBC driver provider that is being used supports the following minimum set of SQL functions:

- `AVG(``exp``)`

- `LIKE(``exp``)`

- `COUNT(*)`

- `MAX(``exp``)`

- `MIN(``exp``)`

- `NOT`
