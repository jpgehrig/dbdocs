The following topics describe supported SQL Syntax and Functions:

- Supported SQL Statements

- Oracle Functions

### Supported SQL Statements

With a few exceptions, the gateway provides full support for Oracle `DELETE`, `INSERT`, `SELECT`, and `UPDATE` statements.

The gateway does not support Oracle data definition language (DDL) statements. No form of the Oracle `ALTER`, `CREATE`, `DROP`, `GRANT`, or `TRUNCATE` statements can be used. Instead, use the pass-through feature of the gateway if you need to use DDL statements against the Teradata database.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/index.md) for detailed descriptions of keywords, parameters, and options.

#### DELETE

The `DELETE` statement is fully supported. However, only Oracle functions supported by Teradata can be used.

**See Also:**

"Functions Supported by Teradata" for a list of supported functions.

#### INSERT

The `INSERT` statement is fully supported. However, only Oracle functions supported by Teradata can be used.

**See Also:**

"Functions Supported by Teradata" for a list of supported functions.

#### SELECT

The `SELECT` statement is fully supported, with these exceptions:

- `CONNECT BY` `condition`

- `NOWAIT`

- `START WITH` `condition`

- `WHERE` `CURRENT` `OF`

#### UPDATE

The `UPDATE` statement is fully supported. However, only Oracle functions supported by Teradata can be used. Also, you cannot have SQL statements in the subquery that refer to the same table name in the outer query. Subqueries are not supported in the `SET` clause.

**See Also:**

"Functions Supported by Teradata" for a list of supported functions.

### Oracle Functions

All functions are evaluated by the Teradata database after the gateway has converted them to Teradata SQL.

#### Functions Not Supported by Teradata

Oracle SQL functions with no equivalent function in Teradata are not supported in `DELETE`, `INSERT`, or `UPDATE` statements, but are evaluated by the Oracle database if the statement is a `SELECT` statement. That is, the Oracle database performs post-processing of `SELECT` statements sent to the gateway.

If an unsupported function is used in a `DELETE`, `INSERT`, or `UPDATE`, statement, the following Oracle error occurs:

    ORA-02070: database db_link_name does not support function in this context

#### Functions Supported by Teradata

The gateway translates the following Oracle database functions in SQL statements to their equivalent Teradata functions:

- Arithmetic Operators

- Comparison Operators

- Group Functions

- String Functions

- Other Functions

##### Arithmetic Operators

| Oracle | Teradata |
|:-------|:---------|
| `+`    | `+`      |
| `-`    | `-`      |
| `*`    | `*`      |
| `/`    | `/`      |

##### Comparison Operators

| Oracle           | Teradata      |
|:-----------------|:--------------|
| `=`              | `=`           |
| `>`              | `>`           |
| `<`              | `<`           |
| `>=`             | `>=`          |
| `<=`             | `<=`          |
| `<>`, `!=`, `^=` | `<>`, `!=`    |
| `IS NOT NULL`    | `IS NOT NULL` |
| `IS NULL`        | `IS NULL`     |

##### Group Functions

| Oracle  | Teradata |
|:--------|:---------|
| `AVG`   | `AVG`    |
| `COUNT` | `COUNT`  |
| `MAX`   | `MAX`    |
| `MIN`   | `MIN`    |
| `SUM`   | `SUM`    |

##### String Functions

| Oracle  | Teradata   |
|:--------|:-----------|
| `INSTR` | `POSITION` |

##### Other Functions

| Oracle      | Teradata              |
|:------------|:----------------------|
| `ABS`       | `ABS`                 |
| `EXP`       | `EXP`                 |
| `LOG(a, b)` | `LOG10(b) / LOG10(a)` |
| `POWER`     | `**`                  |
| `SQRT`      | `SQRT`                |
