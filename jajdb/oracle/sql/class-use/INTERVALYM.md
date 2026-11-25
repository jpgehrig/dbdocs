Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../INTERVALYM.md)
- Use
- [Tree](../package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev
- Next

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

## Uses of Class oracle.sql.INTERVALYM

- **Packages that use [INTERVALYM](../INTERVALYM.md)**

  | Package     | Description                                                                                       |
  |-------------|---------------------------------------------------------------------------------------------------|
  | oracle.jdbc | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`. |

- - ### Uses of [INTERVALYM](../INTERVALYM.md) in [oracle.jdbc](../../jdbc/package-summary.md)

    **Methods in [oracle.jdbc](../../jdbc/package-summary.md) that return [INTERVALYM](../INTERVALYM.md)**

    | Modifier and Type                | Method and Description                                                                                                                                                                                                                            |
    |----------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`INTERVALYM`](../INTERVALYM.md) | OracleConnection.[`createINTERVALYM`](../../jdbc/OracleConnection.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` value)`<br>Creates an INTERVALYM that has the given value.               |
    | [`INTERVALYM`](../INTERVALYM.md) | OracleConnectionWrapper.[`createINTERVALYM`](../../jdbc/OracleConnectionWrapper.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` value)`<br>Creates an INTERVALYM that has the given value. |
    | [`INTERVALYM`](../INTERVALYM.md) | OracleConnectionWrapper.[`createINTERVALYM`](../../jdbc/OracleConnectionWrapper.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` value)`<br>Creates an INTERVALYM that has the given value. |
    | [`INTERVALYM`](../INTERVALYM.md) | OracleConnection.[`createINTERVALYM`](../../jdbc/OracleConnection.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` value)`<br>Creates an INTERVALYM that has the given value.               |
    | [`INTERVALYM`](../INTERVALYM.md) | OracleCallableStatement.[`getINTERVALYM`](../../jdbc/OracleCallableStatement.md)`(int parameterIndex)`<br>Retrieves data into an `oracle.sql.INTERVALYM` object.                                                                                  |
    | [`INTERVALYM`](../INTERVALYM.md) | OracleResultSet.[`getINTERVALYM`](../../jdbc/OracleResultSet.md)`(int columnIndex)`<br>Obtain an oracle.sql.INTERVALYM value from the ResultSet.                                                                                                  |
    | [`INTERVALYM`](../INTERVALYM.md) | OracleResultSet.[`getINTERVALYM`](../../jdbc/OracleResultSet.md)`(int columnIndex)`<br>Obtain an oracle.sql.INTERVALYM value from the ResultSet.                                                                                                  |
    | [`INTERVALYM`](../INTERVALYM.md) | OracleCallableStatement.[`getINTERVALYM`](../../jdbc/OracleCallableStatement.md)`(int parameterIndex)`<br>Retrieves data into an `oracle.sql.INTERVALYM` object.                                                                                  |
    | [`INTERVALYM`](../INTERVALYM.md) | OracleResultSet.[`getINTERVALYM`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName)`<br>Obtain an oracle.sql.INTERVALYM value from the ResultSet.     |
    | [`INTERVALYM`](../INTERVALYM.md) | OracleResultSet.[`getINTERVALYM`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName)`<br>Obtain an oracle.sql.INTERVALYM value from the ResultSet.     |

    **Methods in [oracle.jdbc](../../jdbc/package-summary.md) with parameters of type [INTERVALYM](../INTERVALYM.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                                                  |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | OraclePreparedStatement.[`setINTERVALYM`](../../jdbc/OraclePreparedStatement.md)`(int parameterIndex, `[`INTERVALYM`](../INTERVALYM.md)` x)`<br>Binds the designated parameter to an oracle.sql.INTERVALYM value.                                                                                                       |
    | `void`            | OraclePreparedStatement.[`setINTERVALYM`](../../jdbc/OraclePreparedStatement.md)`(int parameterIndex, `[`INTERVALYM`](../INTERVALYM.md)` x)`<br>Binds the designated parameter to an oracle.sql.INTERVALYM value.                                                                                                       |
    | `void`            | OracleCallableStatement.[`setINTERVALYM`](../../jdbc/OracleCallableStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`INTERVALYM`](../INTERVALYM.md)` x)`<br>Sets the designated parameter to an `oracle.sql.INTERVALYM`value.          |
    | `void`            | OracleCallableStatement.[`setINTERVALYM`](../../jdbc/OracleCallableStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`INTERVALYM`](../INTERVALYM.md)` x)`<br>Sets the designated parameter to an `oracle.sql.INTERVALYM`value.          |
    | `void`            | OraclePreparedStatement.[`setINTERVALYMAtName`](../../jdbc/OraclePreparedStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`INTERVALYM`](../INTERVALYM.md)` value)`<br>Sets the designated parameter to an oracle.sql.INTERVALYM value. |
    | `void`            | OraclePreparedStatement.[`setINTERVALYMAtName`](../../jdbc/OraclePreparedStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`INTERVALYM`](../INTERVALYM.md)` value)`<br>Sets the designated parameter to an oracle.sql.INTERVALYM value. |
    | `void`            | OracleResultSet.[`updateINTERVALYM`](../../jdbc/OracleResultSet.md)`(int columnIndex, `[`INTERVALYM`](../INTERVALYM.md)` value)`<br>Oracle extension.                                                                                                                                                                   |
    | `void`            | OracleResultSet.[`updateINTERVALYM`](../../jdbc/OracleResultSet.md)`(int columnIndex, `[`INTERVALYM`](../INTERVALYM.md)` value)`<br>Oracle extension.                                                                                                                                                                   |
    | `void`            | OracleResultSet.[`updateINTERVALYM`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`INTERVALYM`](../INTERVALYM.md)` value)`<br>Oracle extension.                                                                      |
    | `void`            | OracleResultSet.[`updateINTERVALYM`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`INTERVALYM`](../INTERVALYM.md)` value)`<br>Oracle extension.                                                                      |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../INTERVALYM.md)
- Use
- [Tree](../package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- Prev
- Next

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

Copyright © 2008, 2022, Oracle and/or its affiliates.
