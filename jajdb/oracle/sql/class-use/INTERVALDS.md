Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../INTERVALDS.md)
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

## Uses of Class oracle.sql.INTERVALDS

- **Packages that use [INTERVALDS](../INTERVALDS.md)**

  | Package     | Description                                                                                       |
  |-------------|---------------------------------------------------------------------------------------------------|
  | oracle.jdbc | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`. |

- - ### Uses of [INTERVALDS](../INTERVALDS.md) in [oracle.jdbc](../../jdbc/package-summary.md)

    **Methods in [oracle.jdbc](../../jdbc/package-summary.md) that return [INTERVALDS](../INTERVALDS.md)**

    | Modifier and Type                | Method and Description                                                                                                                                                                                                                            |
    |----------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`INTERVALDS`](../INTERVALDS.md) | OracleConnection.[`createINTERVALDS`](../../jdbc/OracleConnection.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` value)`<br>Creates an INTERVALDS that has the given value.               |
    | [`INTERVALDS`](../INTERVALDS.md) | OracleConnectionWrapper.[`createINTERVALDS`](../../jdbc/OracleConnectionWrapper.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` value)`<br>Creates an INTERVALDS that has the given value. |
    | [`INTERVALDS`](../INTERVALDS.md) | OracleConnectionWrapper.[`createINTERVALDS`](../../jdbc/OracleConnectionWrapper.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` value)`<br>Creates an INTERVALDS that has the given value. |
    | [`INTERVALDS`](../INTERVALDS.md) | OracleConnection.[`createINTERVALDS`](../../jdbc/OracleConnection.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` value)`<br>Creates an INTERVALDS that has the given value.               |
    | [`INTERVALDS`](../INTERVALDS.md) | OracleCallableStatement.[`getINTERVALDS`](../../jdbc/OracleCallableStatement.md)`(int parameterIndex)`<br>Retrieves data into an `oracle.sql.INTERVALDS` object.                                                                                  |
    | [`INTERVALDS`](../INTERVALDS.md) | OracleResultSet.[`getINTERVALDS`](../../jdbc/OracleResultSet.md)`(int columnIndex)`<br>Obtain an oracle.sql.INTERVALDS value from the ResultSet.                                                                                                  |
    | [`INTERVALDS`](../INTERVALDS.md) | OracleResultSet.[`getINTERVALDS`](../../jdbc/OracleResultSet.md)`(int columnIndex)`<br>Obtain an oracle.sql.INTERVALDS value from the ResultSet.                                                                                                  |
    | [`INTERVALDS`](../INTERVALDS.md) | OracleCallableStatement.[`getINTERVALDS`](../../jdbc/OracleCallableStatement.md)`(int parameterIndex)`<br>Retrieves data into an `oracle.sql.INTERVALDS` object.                                                                                  |
    | [`INTERVALDS`](../INTERVALDS.md) | OracleResultSet.[`getINTERVALDS`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName)`<br>Obtain an oracle.sql.INTERVALDS value from the ResultSet.     |
    | [`INTERVALDS`](../INTERVALDS.md) | OracleResultSet.[`getINTERVALDS`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName)`<br>Obtain an oracle.sql.INTERVALDS value from the ResultSet.     |

    **Methods in [oracle.jdbc](../../jdbc/package-summary.md) with parameters of type [INTERVALDS](../INTERVALDS.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                                                  |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | OraclePreparedStatement.[`setINTERVALDS`](../../jdbc/OraclePreparedStatement.md)`(int parameterIndex, `[`INTERVALDS`](../INTERVALDS.md)` x)`<br>Binds the designated parameter to an oracle.sql.INTERVALDS value.                                                                                                       |
    | `void`            | OraclePreparedStatement.[`setINTERVALDS`](../../jdbc/OraclePreparedStatement.md)`(int parameterIndex, `[`INTERVALDS`](../INTERVALDS.md)` x)`<br>Binds the designated parameter to an oracle.sql.INTERVALDS value.                                                                                                       |
    | `void`            | OracleCallableStatement.[`setINTERVALDS`](../../jdbc/OracleCallableStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`INTERVALDS`](../INTERVALDS.md)` x)`<br>Sets the designated parameter to an `oracle.sql.INTERVALDS`value.          |
    | `void`            | OracleCallableStatement.[`setINTERVALDS`](../../jdbc/OracleCallableStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`INTERVALDS`](../INTERVALDS.md)` x)`<br>Sets the designated parameter to an `oracle.sql.INTERVALDS`value.          |
    | `void`            | OraclePreparedStatement.[`setINTERVALDSAtName`](../../jdbc/OraclePreparedStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`INTERVALDS`](../INTERVALDS.md)` value)`<br>Sets the designated parameter to an oracle.sql.INTERVALDS value. |
    | `void`            | OraclePreparedStatement.[`setINTERVALDSAtName`](../../jdbc/OraclePreparedStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`INTERVALDS`](../INTERVALDS.md)` value)`<br>Sets the designated parameter to an oracle.sql.INTERVALDS value. |
    | `void`            | OracleResultSet.[`updateINTERVALDS`](../../jdbc/OracleResultSet.md)`(int columnIndex, `[`INTERVALDS`](../INTERVALDS.md)` value)`<br>Oracle extension.                                                                                                                                                                   |
    | `void`            | OracleResultSet.[`updateINTERVALDS`](../../jdbc/OracleResultSet.md)`(int columnIndex, `[`INTERVALDS`](../INTERVALDS.md)` value)`<br>Oracle extension.                                                                                                                                                                   |
    | `void`            | OracleResultSet.[`updateINTERVALDS`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`INTERVALDS`](../INTERVALDS.md)` value)`<br>Oracle extension.                                                                      |
    | `void`            | OracleResultSet.[`updateINTERVALDS`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`INTERVALDS`](../INTERVALDS.md)` value)`<br>Oracle extension.                                                                      |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../INTERVALDS.md)
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
