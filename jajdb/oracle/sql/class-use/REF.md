Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../REF.md)
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

## Uses of Class oracle.sql.REF

- **Packages that use [REF](../REF.md)**

  | Package     | Description                                                                                       |
  |-------------|---------------------------------------------------------------------------------------------------|
  | oracle.jdbc | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`. |

- - ### Uses of [REF](../REF.md) in [oracle.jdbc](../../jdbc/package-summary.md)

    **Methods in [oracle.jdbc](../../jdbc/package-summary.md) that return [REF](../REF.md)**

    | Modifier and Type  | Method and Description                                                                                                                                                                         |
    |--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`REF`](../REF.md) | OracleCallableStatement.[`getREF`](../../jdbc/OracleCallableStatement.md)`(int parameterIndex)`<br>Retrieves data into an `oracle.sql.REF` object.                                             |
    | [`REF`](../REF.md) | OracleResultSet.[`getREF`](../../jdbc/OracleResultSet.md)`(int columnIndex)`<br>Oracle extension.                                                                                              |
    | [`REF`](../REF.md) | OracleResultSet.[`getREF`](../../jdbc/OracleResultSet.md)`(int columnIndex)`<br>Oracle extension.                                                                                              |
    | [`REF`](../REF.md) | OracleCallableStatement.[`getREF`](../../jdbc/OracleCallableStatement.md)`(int parameterIndex)`<br>Retrieves data into an `oracle.sql.REF` object.                                             |
    | [`REF`](../REF.md) | OracleResultSet.[`getREF`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName)`<br>Oracle extension. |
    | [`REF`](../REF.md) | OracleResultSet.[`getREF`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName)`<br>Oracle extension. |

    **Methods in [oracle.jdbc](../../jdbc/package-summary.md) with parameters of type [REF](../REF.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                           |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | OraclePreparedStatement.[`setREF`](../../jdbc/OraclePreparedStatement.md)`(int parameterIndex, `[`REF`](../REF.md)` ref)`<br>Binds the designated parameter to a `oracle.sql.REF` value.                                                                                                         |
    | `void`            | OraclePreparedStatement.[`setREF`](../../jdbc/OraclePreparedStatement.md)`(int parameterIndex, `[`REF`](../REF.md)` ref)`<br>Binds the designated parameter to a `oracle.sql.REF` value.                                                                                                         |
    | `void`            | OracleCallableStatement.[`setREF`](../../jdbc/OracleCallableStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`REF`](../REF.md)` x)`<br>Sets the designated parameter to an `oracle.sql.REF`value.               |
    | `void`            | OracleCallableStatement.[`setREF`](../../jdbc/OracleCallableStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`REF`](../REF.md)` x)`<br>Sets the designated parameter to an `oracle.sql.REF`value.               |
    | `void`            | OraclePreparedStatement.[`setREFAtName`](../../jdbc/OraclePreparedStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`REF`](../REF.md)` value)`<br>Sets the designated parameter to an `oracle.sql.REF`value.     |
    | `void`            | OraclePreparedStatement.[`setREFAtName`](../../jdbc/OraclePreparedStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`REF`](../REF.md)` value)`<br>Sets the designated parameter to an `oracle.sql.REF`value.     |
    | `void`            | OraclePreparedStatement.[`setRefType`](../../jdbc/OraclePreparedStatement.md)`(int parameterIndex, `[`REF`](../REF.md)` ref)`<br>Binds the designated parameter to a `oracle.sql.REF` value.                                                                                                     |
    | `void`            | OraclePreparedStatement.[`setRefType`](../../jdbc/OraclePreparedStatement.md)`(int parameterIndex, `[`REF`](../REF.md)` ref)`<br>Binds the designated parameter to a `oracle.sql.REF` value.                                                                                                     |
    | `void`            | OracleCallableStatement.[`setRefType`](../../jdbc/OracleCallableStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`REF`](../REF.md)` x)`<br>Sets the designated parameter to an `oracle.sql.REF`value.           |
    | `void`            | OracleCallableStatement.[`setRefType`](../../jdbc/OracleCallableStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`REF`](../REF.md)` x)`<br>Sets the designated parameter to an `oracle.sql.REF`value.           |
    | `void`            | OraclePreparedStatement.[`setRefTypeAtName`](../../jdbc/OraclePreparedStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`REF`](../REF.md)` value)`<br>Sets the designated parameter to an `oracle.sql.REF`value. |
    | `void`            | OraclePreparedStatement.[`setRefTypeAtName`](../../jdbc/OraclePreparedStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`REF`](../REF.md)` value)`<br>Sets the designated parameter to an `oracle.sql.REF`value. |
    | `void`            | OracleResultSet.[`updateREF`](../../jdbc/OracleResultSet.md)`(int columnIndex, `[`REF`](../REF.md)` value)`<br>Oracle extension.                                                                                                                                                                 |
    | `void`            | OracleResultSet.[`updateREF`](../../jdbc/OracleResultSet.md)`(int columnIndex, `[`REF`](../REF.md)` value)`<br>Oracle extension.                                                                                                                                                                 |
    | `void`            | OracleResultSet.[`updateREF`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`REF`](../REF.md)` value)`<br>Oracle extension.                                                                    |
    | `void`            | OracleResultSet.[`updateREF`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`REF`](../REF.md)` value)`<br>Oracle extension.                                                                    |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../REF.md)
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
