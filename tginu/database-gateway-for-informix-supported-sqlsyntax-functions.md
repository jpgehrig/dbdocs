The following topics describe supported SQL Syntax and Functions:

- Supported SQL Statements

- Oracle Functions

### Supported SQL Statements

With a few exceptions, the gateway provides full support for Oracle `DELETE`, `INSERT`, `SELECT`, and `UPDATE` statements.

The gateway does not support Oracle data definition language (DDL) statements. No form of the Oracle `ALTER`, `CREATE`, `DROP`, `GRANT`, or `TRUNCATE` statements can be used. Instead, use the pass-through feature of the gateway if you need to use DDL statements against the Informix database.

**See Also:**

[Oracle Database SQL Language Reference](../sqlrf/index.md) for detailed descriptions of keywords, parameters, and options.

#### DELETE

The `DELETE` statement is fully supported. However, only Oracle functions supported by Informix can be used. Also, you cannot have SQL statements in the subquery that refer to the same table name in the outer query.

**See Also:**

"Functions Supported by Informix" for a list of supported functions.

#### INSERT

The `INSERT` statement is fully supported. However, only Oracle functions supported by Informix can be used. Also, you cannot have SQL statements in the subquery that refer to the same table name in the outer query.

**See Also:**

"Functions Supported by Informix" for a list of supported functions.

#### SELECT

The `SELECT` statement is fully supported, with these exceptions:

- `CONNECT BY` `condition`

- `NOWAIT`

- `START` `WITH` `condition`

- Subquery in `HAVING` clause

#### UPDATE

The `UPDATE` statement is fully supported. However, only Oracle functions supported by Informix can be used. Also, you cannot have SQL statements in the subquery that refer to the same table name in the outer query. Subqueries are not supported in the `SET` clause. Informix does not support table aliases in `UPDATE`.

**See Also:**

"Functions Supported by Informix" for a list of supported functions.

### Oracle Functions

All functions are evaluated by the Informix database after the gateway has converted them to Informix SQL.

#### Functions Not Supported by Informix

Oracle SQL functions with no equivalent function in Informix are not supported in `DELETE`, `INSERT`, or `UPDATE` statements, but are evaluated by the Oracle database if the statement is a `SELECT` statement. That is, the Oracle database performs post-processing of `SELECT` statements sent to the gateway.

If an unsupported function is used in a `DELETE`, `INSERT`, or `UPDATE`, statement, the following Oracle error occurs:

    ORA-02070: database db_link_name does not support function in this context

#### Functions Supported by Informix

The gateway translates the following Oracle database functions in SQL statements to their equivalent Informix functions:

- Arithmetic Operators

- Comparison Operators

- Group Functions

- String Functions

- Pattern Matches

- Date Functions

- Other Functions

##### Arithmetic Operators

| Oracle | Informix |
|:-------|:---------|
| `+`    | `+`      |
| `-`    | `-`      |
| `*`    | `*`      |
| `/`    | `/`      |

##### Comparison Operators

| Oracle            | Informix      |
|:------------------|:--------------|
| `=`               | `=`           |
| `>`               | `>`           |
| `<`               | `<`           |
| `>=`              | `>=`          |
| `<=`              | `<=`          |
| `<>`, `!=`, ` ^=` | `<>`          |
| `IS NOT NULL`     | `IS NOT NULL` |
| `IS NUL`L         | `IS NULL`     |

##### Group Functions

| Oracle  | Informix |
|:--------|:---------|
| `AVG`   | `AVG`    |
| `COUNT` | `COUNT`  |
| `MAX`   | `MAX`    |
| `MIN`   | `MIN`    |
| `SUM`   | `SUM`    |

##### String Functions

| Oracle         | Informix |
|:---------------|:---------|
| `||`, `CONCAT` | `||`     |
| `ASCII`        | `ASCII`  |
| `CHR`          | `CHR`    |
| `LENGTH`       | `LENGTH` |

##### Pattern Matches

| Oracle                  | Informix                |
|:------------------------|:------------------------|
| `LIKE 'a%'`             | `LIKE "a%"`             |
| `LIKE 'a_'`             | `LIKE "a_"`             |
| `LIKE 'a\%' ESCAPE '\'` | `LIKE "a\%" ESCAPE "\"` |
| `NOT LIKE`              | `NOT LIKE`              |

##### Date Functions

| Oracle          | Informix        |
|:----------------|:----------------|
| `date + number` | `date + number` |
| `date - number` | `date - number` |
| `date + date`   | `date + date`   |
| `date - date`   | `date - date`   |

##### Other Functions

| Oracle                    | Informix                         |
|:--------------------------|:---------------------------------|
| `ABS`                     | `ABS`                            |
| `COS`                     | `COS`                            |
| `EXP`                     | `EXP`                            |
| `LOG10`                   | `LOG10`                          |
| `LN`                      | `LOGN`                           |
| `LTRIM(``char``)`         | `TRIM(LEADING FROM` `char``)`    |
| `MOD`                     | `MOD`                            |
| `POWER (``m,n``)`         | `POW(``m,n``)`                   |
| `RTRIM(``char``)`         | `TRIM(TRAILING` `FROM` `char``)` |
| `ROUND` (with 1 argument) | `ROUND`                          |
| `SIN`                     | `SIN`                            |
| `SQRT`                    | `SQRT`                           |
| `TAN`                     | `TAN`                            |
| `TRUNC` (with 1 argument) | `TRUNC`                          |

#### Functions Supported by the Gateway

If the Oracle function has no equivalent function in Informix, the Oracle function is not translated into the SQL statement and must be post-processed if the SQL statement is a `SELECT`.

The gateway, however, does support one function even though there is no equivalent in Informix. This function is the `TO_DATE` function:

    TO_DATE(date_string | date_column)

Where:

`date_string` is converted to a string with the following format:

    yyyy-mm-dd hh:mi:ss.fff

**Note:**

Supply the date string with the same format as the result (that is, `yyyy-mm-dd hh:mi:ss.fff`).

`date_column` is a column with a date data type. It is converted to a parameter with a `timestamp` data type.
