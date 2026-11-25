Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../BFILE.md)
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

## Uses of Class oracle.sql.BFILE

- **Packages that use [BFILE](../BFILE.md)**

  | Package     | Description                                                                                       |
  |-------------|---------------------------------------------------------------------------------------------------|
  | oracle.jdbc | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`. |
  | oracle.sql  | A package of classes that represent java SQL types and Oracle specific SQL types.                 |

- - ### Uses of [BFILE](../BFILE.md) in [oracle.jdbc](../../jdbc/package-summary.md)

    **Methods in [oracle.jdbc](../../jdbc/package-summary.md) that return [BFILE](../BFILE.md)**

    | Modifier and Type      | Method and Description                                                                                                                                                                           |
    |------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`BFILE`](../BFILE.md) | OracleCallableStatement.[`getBfile`](../../jdbc/OracleCallableStatement.md)`(int parameterIndex)`<br>Retrieves data into an `oracle.sql.BFILE` object.                                           |
    | [`BFILE`](../BFILE.md) | OracleResultSet.[`getBfile`](../../jdbc/OracleResultSet.md)`(int columnIndex)`<br>Oracle extension.                                                                                              |
    | [`BFILE`](../BFILE.md) | OracleResultSet.[`getBfile`](../../jdbc/OracleResultSet.md)`(int columnIndex)`<br>Oracle extension.                                                                                              |
    | [`BFILE`](../BFILE.md) | OracleCallableStatement.[`getBfile`](../../jdbc/OracleCallableStatement.md)`(int parameterIndex)`<br>Retrieves data into an `oracle.sql.BFILE` object.                                           |
    | [`BFILE`](../BFILE.md) | OracleCallableStatement.[`getBFILE`](../../jdbc/OracleCallableStatement.md)`(int parameterIndex)`<br>Retrieves data into an `oracle.sql.BFILE` object.                                           |
    | [`BFILE`](../BFILE.md) | OracleResultSet.[`getBFILE`](../../jdbc/OracleResultSet.md)`(int columnIndex)`<br>Oracle extension.                                                                                              |
    | [`BFILE`](../BFILE.md) | OracleResultSet.[`getBFILE`](../../jdbc/OracleResultSet.md)`(int columnIndex)`<br>Oracle extension.                                                                                              |
    | [`BFILE`](../BFILE.md) | OracleCallableStatement.[`getBFILE`](../../jdbc/OracleCallableStatement.md)`(int parameterIndex)`<br>Retrieves data into an `oracle.sql.BFILE` object.                                           |
    | [`BFILE`](../BFILE.md) | OracleResultSet.[`getBfile`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName)`<br>Oracle extension. |
    | [`BFILE`](../BFILE.md) | OracleResultSet.[`getBfile`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName)`<br>Oracle extension. |
    | [`BFILE`](../BFILE.md) | OracleResultSet.[`getBFILE`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName)`<br>Oracle extension. |
    | [`BFILE`](../BFILE.md) | OracleResultSet.[`getBFILE`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName)`<br>Oracle extension. |

    **Methods in [oracle.jdbc](../../jdbc/package-summary.md) with parameters of type [BFILE](../BFILE.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                              |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | OraclePreparedStatement.[`setBfile`](../../jdbc/OraclePreparedStatement.md)`(int parameterIndex, `[`BFILE`](../BFILE.md)` file)`<br>Binds the designated parameter to a `oracle.sql.BFILE` value.                                                                                                   |
    | `void`            | OraclePreparedStatement.[`setBfile`](../../jdbc/OraclePreparedStatement.md)`(int parameterIndex, `[`BFILE`](../BFILE.md)` file)`<br>Binds the designated parameter to a `oracle.sql.BFILE` value.                                                                                                   |
    | `void`            | OraclePreparedStatement.[`setBFILE`](../../jdbc/OraclePreparedStatement.md)`(int parameterIndex, `[`BFILE`](../BFILE.md)` file)`<br>Binds the designated parameter to a `oracle.sql.BFILE` value.                                                                                                   |
    | `void`            | OraclePreparedStatement.[`setBFILE`](../../jdbc/OraclePreparedStatement.md)`(int parameterIndex, `[`BFILE`](../BFILE.md)` file)`<br>Binds the designated parameter to a `oracle.sql.BFILE` value.                                                                                                   |
    | `void`            | OracleCallableStatement.[`setBfile`](../../jdbc/OracleCallableStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`BFILE`](../BFILE.md)` x)`<br>Sets the designated parameter to an `oracle.sql.BFILE`value.          |
    | `void`            | OracleCallableStatement.[`setBfile`](../../jdbc/OracleCallableStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`BFILE`](../BFILE.md)` x)`<br>Sets the designated parameter to an `oracle.sql.BFILE`value.          |
    | `void`            | OracleCallableStatement.[`setBFILE`](../../jdbc/OracleCallableStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`BFILE`](../BFILE.md)` x)`<br>Sets the designated parameter to an `oracle.sql.BFILE`value.          |
    | `void`            | OracleCallableStatement.[`setBFILE`](../../jdbc/OracleCallableStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`BFILE`](../BFILE.md)` x)`<br>Sets the designated parameter to an `oracle.sql.BFILE`value.          |
    | `void`            | OraclePreparedStatement.[`setBfileAtName`](../../jdbc/OraclePreparedStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`BFILE`](../BFILE.md)` value)`<br>Sets the designated parameter to a `oracle.sql.BFILE`value. |
    | `void`            | OraclePreparedStatement.[`setBfileAtName`](../../jdbc/OraclePreparedStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`BFILE`](../BFILE.md)` value)`<br>Sets the designated parameter to a `oracle.sql.BFILE`value. |
    | `void`            | OraclePreparedStatement.[`setBFILEAtName`](../../jdbc/OraclePreparedStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`BFILE`](../BFILE.md)` value)`<br>Sets the designated parameter to a `oracle.sql.BFILE`value. |
    | `void`            | OraclePreparedStatement.[`setBFILEAtName`](../../jdbc/OraclePreparedStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`BFILE`](../BFILE.md)` value)`<br>Sets the designated parameter to a `oracle.sql.BFILE`value. |
    | `void`            | OracleResultSet.[`updateBfile`](../../jdbc/OracleResultSet.md)`(int columnIndex, `[`BFILE`](../BFILE.md)` value)`<br>Oracle extension.                                                                                                                                                              |
    | `void`            | OracleResultSet.[`updateBfile`](../../jdbc/OracleResultSet.md)`(int columnIndex, `[`BFILE`](../BFILE.md)` value)`<br>Oracle extension.                                                                                                                                                              |
    | `void`            | OracleResultSet.[`updateBFILE`](../../jdbc/OracleResultSet.md)`(int columnIndex, `[`BFILE`](../BFILE.md)` value)`<br>Oracle extension.                                                                                                                                                              |
    | `void`            | OracleResultSet.[`updateBFILE`](../../jdbc/OracleResultSet.md)`(int columnIndex, `[`BFILE`](../BFILE.md)` value)`<br>Oracle extension.                                                                                                                                                              |
    | `void`            | OracleResultSet.[`updateBfile`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`BFILE`](../BFILE.md)` value)`<br>Oracle extension.                                                                 |
    | `void`            | OracleResultSet.[`updateBfile`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`BFILE`](../BFILE.md)` value)`<br>Oracle extension.                                                                 |
    | `void`            | OracleResultSet.[`updateBFILE`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`BFILE`](../BFILE.md)` value)`<br>Oracle extension.                                                                 |
    | `void`            | OracleResultSet.[`updateBFILE`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`BFILE`](../BFILE.md)` value)`<br>Oracle extension.                                                                 |

  - ### Uses of [BFILE](../BFILE.md) in [oracle.sql](../package-summary.md)

    **Methods in [oracle.sql](../package-summary.md) with parameters of type [BFILE](../BFILE.md)**

    | Modifier and Type | Method and Description                                                                                                                                    |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `long`            | BFILE.[`position`](../BFILE.md)`(`[`BFILE`](../BFILE.md)` pattern, long start)`<br>Deprecated. <br>Determine the byte position at which the given pattern |
    | `long`            | BFILE.[`position`](../BFILE.md)`(`[`BFILE`](../BFILE.md)` pattern, long start)`<br>Deprecated. <br>Determine the byte position at which the given pattern |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../BFILE.md)
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
