The following topics describe supported SQL Syntax and Functions:

- Supported SQL Statements

- Oracle Functions

### B.1 Supported SQL Statements

With a few exceptions, the gateway provides full support for Oracle `DELETE`, `INSERT`, `SELECT`, and `UPDATE` statements.

The gateway does not support Oracle data definition language (DDL) statements. No form of the Oracle `ALTER`, `CREATE`, `DROP`, `GRANT`, or `TRUNCATE` statements can be used. Instead, use the pass-through feature of the gateway if you need to use DDL statements against the SQL Server database.

**Note:**

`TRUNCATE` cannot be used in a pass-through statement.

**See Also:**

[Oracle Database Reference](../refrn/index.md) for detailed descriptions of keywords, parameters, and options.

#### B.1.1 DELETE

The `DELETE` statement is fully supported. However, only Oracle functions supported by SQL Server can be used.

**See Also:**

"Functions Supported by SQL Server" for a list of supported functions.

#### B.1.2 INSERT

The `INSERT` statement is fully supported. However, only Oracle functions supported by SQL Server can be used.

**See Also:**

"Functions Supported by SQL Server" for a list of supported functions.

#### B.1.3 SELECT

The `SELECT` statement is fully supported, with these exceptions:

- `CONNECT BY` `condition`

- `NOWAIT`

- `START WITH` `condition`

- `WHERE CURRENT` `OF`

#### B.1.4 UPDATE

The `UPDATE` statement is fully supported. However, only Oracle functions supported by SQL Server can be used.

**See Also:**

"Functions Supported by SQL Server" for a list of supported functions.

### B.2 Oracle Functions

All functions are evaluated by the SQL Server database after the gateway has converted them to SQL Server SQL equivalents. The exception is the `TO_DATE` function, which is evaluated by the gateway.

#### B.2.1 Functions Not Supported by SQL Server

Oracle SQL functions with no equivalent function in SQL Server are not supported in `DELETE`, `INSERT`, or `UPDATE` statements, but are evaluated by the Oracle database if the statement is a `SELECT` statement. That is, the Oracle database performs post-processing of `SELECT` statements sent to the gateway.

If an unsupported function is used in a `DELETE`, `INSERT`, or `UPDATE`, statement, the following Oracle error occurs:

    ORA-02070: database db_link_name does not support function in this context

#### B.2.2 Functions Supported by SQL Server

The gateway translates the following Oracle database functions in SQL statements to their equivalent SQL Server functions:

- Arithmetic Operators

- Comparison Operators

- Pattern Matching

- Group Functions

- String Functions

- Other Functions

##### B.2.2.1 Arithmetic Operators

| Oracle | SQL Server |
|:-------|:-----------|
| `+`    | `+`        |
| `-`    | `-`        |
| `*`    | `*`        |
| `/`    | `/`        |

##### B.2.2.2 Comparison Operators

| Oracle        | SQL Server    |
|:--------------|:--------------|
| `=`           | `=`           |
| `>`           | `>`           |
| `<`           | `<`           |
| `>=`          | `>=`          |
| `<=`          | `<=`          |
| `<>, !=, ^=`  | `<>`          |
| `IS NOT NULL` | `IS NOT NULL` |
| `IS NULL`     | `IS NULL`     |

##### B.2.2.3 Pattern Matching

| Oracle     | SQL Server |
|:-----------|:-----------|
| `LIKE`     | `LIKE`     |
| `NOT LIKE` | `NOT LIKE` |

##### B.2.2.4 Group Functions

| Oracle  | SQL Server |
|:--------|:-----------|
| `AVG`   | `AVG`      |
| `COUNT` | `COUNT`    |
| `MAX`   | `MAX`      |
| `MIN`   | `MIN`      |
| `SUM`   | `SUM`      |

##### B.2.2.5 String Functions

| Oracle                                                 | SQL Server                                |
|:-------------------------------------------------------|:------------------------------------------|
| `||, CONCAT`                                           | `+` `(``expression1` `+` `expression2``)` |
| `ASCII`                                                | `ASCII`                                   |
| `CHR`                                                  | `CHAR`                                    |
| `INSTR` (with two arguments)                           | `CHARINDEX`                               |
| `LENGTH ()`                                            | `LEN ()`                                  |
| `LENGTHB ()`                                           | `DATALENGTH ()`                           |
| `LENGTHC ()`                                           | `LEN ()`                                  |
| `LOWER`                                                | `LOWER`                                   |
| `LTRIM`                                                | `LTRIM`                                   |
| `RTRIM`                                                | `RTRIM`                                   |
| `SUBSTR` (second argument cannot be a negative number) | `SUBSTRING`                               |
| `UPPER`                                                | `UPPER`                                   |

##### B.2.2.6 Other Functions

| Oracle    | SQL Server    |
|:----------|:--------------|
| `ABS`     | `ABS`         |
| `CEIL`    | `CEILING`     |
| `COS`     | `COS`         |
| `EXP`     | `EXP`         |
| `FLOOR`   | `FLOOR`       |
| `LN`      | `LOG`         |
| `LOG`     | `LOG10`       |
| `MOD`     | `%`           |
| `NOT NVL` | `IS NOT NULL` |
| `NVL`     | `IS NULL`     |
| `POWER`   | `POWER`       |
| `ROUND`   | `ROUND`       |
| `SIN`     | `SIN`         |
| `SQRT`    | `SQRT`        |
| `TAN`     | `TAN`         |

#### B.2.3 Functions Supported by the Gateway

If an Oracle function has no equivalent function in SQL Server, the Oracle function is not translated into the SQL statement and must be post-processed if the SQL statement is a `SELECT`.

The gateway, however, does support the `TO_DATE` function equivalent in SQL Server, as follows:

    TO_DATE(date_string | date_column)

where:

- `date_string` is converted to a string with the following format:

      yyyy-mm-dd hh:mi:ss.fff

  **Note:**

  Supply the date string with the same format as the result (that is, `y``yyyy``-``mm``-``dd`` ``hh``:``mi``:``ss``.``fff`).

- `date_column` is a column with a date data type. It is converted to a parameter with a timestamp data type.
