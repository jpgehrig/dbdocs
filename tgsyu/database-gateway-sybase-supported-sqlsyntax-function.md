The following topics describe supported SQL Syntax and Functions:

- Supported SQL Statements

- Oracle Functions

### B.1 Supported SQL Statements

With a few exceptions, the gateway provides full support for Oracle `DELETE`, `INSERT`, `SELECT`, and `UPDATE` statements.

The gateway does not support Oracle data definition language (DDL) statements. No form of the Oracle `ALTER`, `CREATE`, `DROP`, `GRANT`, or `TRUNCATE` statements can be used. Instead, for `ALTER`, `CREATE`, `DROP`, and `GRANT` statements, use the pass-through feature of the gateway if you need to use DDL statements against the Sybase database.

**Note:**

`TRUNCATE` cannot be used in a pass-through statement.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/index.md) for detailed descriptions of keywords, parameters, and options and the Sybase documentation for details of executing SQL statements in a transaction.

#### B.1.1 DELETE

The `DELETE` statement is fully supported. However, only Oracle functions supported by Sybase can be used.

**See Also:**

"Functions Supported by Sybase" for a list of supported functions.

#### B.1.2 INSERT

The `INSERT` statement is fully supported. However, only Oracle functions supported by Sybase can be used.

**See Also:**

"Functions Supported by Sybase" for a list of supported functions.

#### B.1.3 SELECT

The SELECT statement is fully supported, with these exceptions:

- `CONNECT BY` `condition`

- `NOWAIT`

- `START WITH` `condition`

- `WHERE CURRENT` OF

#### B.1.4 UPDATE

The `UPDATE` statement is fully supported. However, only Oracle functions supported by Sybase can be used. Also, you cannot have SQL statements in the subquery that refer to the same table name in the outer query. Subqueries are not supported in the SET clause.

**See Also:**

"Functions Supported by Sybase" for a list of supported functions.

### B.2 Oracle Functions

All functions are evaluated by the Sybase database after the gateway has converted them to Sybase SQL.

Topics:

- Functions Not Supported by Sybase

- Functions Supported by Sybase

#### B.2.1 Functions Not Supported by Sybase

Oracle SQL functions with no equivalent function in Sybase are not supported in `DELETE`, `INSERT`, or `UPDATE` statements, but are evaluated by the Oracle database if the statement is a `SELECT` statement. That is, the Oracle database performs post-processing of `SELECT` statements sent to the gateway.

If an unsupported function is used in a `DELETE`, `INSERT`, or `UPDATE`, statement, the following Oracle error occurs:

    ORA-02070: database db_link_name does not support function in this context

#### B.2.2 Functions Supported by Sybase

The gateway translates the following Oracle database functions in SQL statements to their equivalent Sybase functions:

- Arithmetic Operators

- Comparison Operators

- Group Functions

- String Functions

- Other Functions

##### B.2.2.1 Arithmetic Operators

| Oracle | Sybase |
|:-------|:-------|
| `+`    | `+`    |
| `-`    | `-`    |
| `*`    | `*`    |
| `/`    | `/`    |

##### B.2.2.2 Comparison Operators

| Oracle            | Sybase        |
|:------------------|:--------------|
| `=`               | `=`           |
| `>`               | `>`           |
| `<`               | `<`           |
| `>=`              | `>=`          |
| `<=`              | `<=`          |
| `<>`, `!=`, ` ^=` | `<>`,` !=`    |
| `IS NOT NULL`     | `IS NOT NULL` |
| `IS NULL`         | `IS NULL`     |

##### B.2.2.3 Group Functions

| Oracle  | Sybase  |
|:--------|:--------|
| `AVG`   | `AVG`   |
| `COUNT` | `COUNT` |
| `MAX`   | `MAX`   |
| `MIN`   | `MIN`   |
| `SUM`   | `SUM`   |

##### B.2.2.4 String Functions

| Oracle                                                 | Sybase                                    |
|:-------------------------------------------------------|:------------------------------------------|
| `||`                                                   | \+ ` (``expression1` `+` `expression2``)` |
| `ASCII`                                                | `ASCII`                                   |
| `CHR`                                                  | `CHAR`                                    |
| `INSTR`                                                | `CHARINDEX`                               |
| `LENGTH`                                               | `CHAR_LENGTH`                             |
| `LOWER`                                                | `LOWER`                                   |
| `SUBSTR` (second argument cannot be a negative number) | `SUBSTRING`                               |
| `UPPER`                                                | `UPPER`                                   |

##### B.2.2.5 Other Functions

| Oracle      | Sybase        |
|:------------|:--------------|
| `ABS`       | `ABS`         |
| `CEIL`      | `CEILING`     |
| `COS`       | `COS`         |
| `EXP`       | `EXP`         |
| `FLOOR`     | `FLOOR`       |
| `LN`        | `LOG`         |
| `LOG`       | `LOG10`       |
| `MOD`       | `%`           |
| `NOT` `NVL` | `IS NOT NULL` |
| `NVL`       | `IS NULL`     |
| `POWER`     | `POWER`       |
| `ROUND`     | `ROUND`       |
| `SIN`       | `SIN`         |
| `SQRT`      | `SQRT`        |
| `TAN`       | `TAN`         |
