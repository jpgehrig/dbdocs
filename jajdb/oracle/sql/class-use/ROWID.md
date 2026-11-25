Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../ROWID.md)
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

## Uses of Class oracle.sql.ROWID

- **Packages that use [ROWID](../ROWID.md)**

  | Package         | Description                                                                                                                     |
  |-----------------|---------------------------------------------------------------------------------------------------------------------------------|
  | oracle.jdbc     | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`.                               |
  | oracle.jdbc.dcn | This package is an Oracle JDBC extension that provides interfaces to access the Database Change Notification feature of Oracle. |

- - ### Uses of [ROWID](../ROWID.md) in [oracle.jdbc](../../jdbc/package-summary.md)

    **Methods in [oracle.jdbc](../../jdbc/package-summary.md) that return [ROWID](../ROWID.md)**

    | Modifier and Type      | Method and Description                                                                                                                                                                           |
    |------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`ROWID`](../ROWID.md) | OracleCallableStatement.[`getROWID`](../../jdbc/OracleCallableStatement.md)`(int parameterIndex)`<br>Retrieves data into an `oracle.sql.ROWID` object.                                           |
    | [`ROWID`](../ROWID.md) | OracleResultSet.[`getROWID`](../../jdbc/OracleResultSet.md)`(int columnIndex)`<br>Oracle extension.                                                                                              |
    | [`ROWID`](../ROWID.md) | OracleResultSet.[`getROWID`](../../jdbc/OracleResultSet.md)`(int columnIndex)`<br>Oracle extension.                                                                                              |
    | [`ROWID`](../ROWID.md) | OracleCallableStatement.[`getROWID`](../../jdbc/OracleCallableStatement.md)`(int parameterIndex)`<br>Retrieves data into an `oracle.sql.ROWID` object.                                           |
    | [`ROWID`](../ROWID.md) | OracleResultSet.[`getROWID`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName)`<br>Oracle extension. |
    | [`ROWID`](../ROWID.md) | OracleResultSet.[`getROWID`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName)`<br>Oracle extension. |

    **Methods in [oracle.jdbc](../../jdbc/package-summary.md) with parameters of type [ROWID](../ROWID.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                               |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | OraclePreparedStatement.[`setROWID`](../../jdbc/OraclePreparedStatement.md)`(int parameterIndex, `[`ROWID`](../ROWID.md)` rowid)`<br>Binds the designated parameter to a `oracle.sql.ROWID` value.                                                                                                   |
    | `void`            | OraclePreparedStatement.[`setROWID`](../../jdbc/OraclePreparedStatement.md)`(int parameterIndex, `[`ROWID`](../ROWID.md)` rowid)`<br>Binds the designated parameter to a `oracle.sql.ROWID` value.                                                                                                   |
    | `void`            | OracleCallableStatement.[`setROWID`](../../jdbc/OracleCallableStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`ROWID`](../ROWID.md)` x)`<br>Sets the designated parameter to an `oracle.sql.ROWID`value.           |
    | `void`            | OracleCallableStatement.[`setROWID`](../../jdbc/OracleCallableStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`ROWID`](../ROWID.md)` x)`<br>Sets the designated parameter to an `oracle.sql.ROWID`value.           |
    | `void`            | OraclePreparedStatement.[`setROWIDAtName`](../../jdbc/OraclePreparedStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`ROWID`](../ROWID.md)` value)`<br>Sets the designated parameter to an `oracle.sql.ROWID`value. |
    | `void`            | OraclePreparedStatement.[`setROWIDAtName`](../../jdbc/OraclePreparedStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`ROWID`](../ROWID.md)` value)`<br>Sets the designated parameter to an `oracle.sql.ROWID`value. |
    | `void`            | OracleResultSet.[`updateROWID`](../../jdbc/OracleResultSet.md)`(int columnIndex, `[`ROWID`](../ROWID.md)` value)`<br>Oracle extension.                                                                                                                                                               |
    | `void`            | OracleResultSet.[`updateROWID`](../../jdbc/OracleResultSet.md)`(int columnIndex, `[`ROWID`](../ROWID.md)` value)`<br>Oracle extension.                                                                                                                                                               |
    | `void`            | OracleResultSet.[`updateROWID`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`ROWID`](../ROWID.md)` value)`<br>Oracle extension.                                                                  |
    | `void`            | OracleResultSet.[`updateROWID`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`ROWID`](../ROWID.md)` value)`<br>Oracle extension.                                                                  |

  - ### Uses of [ROWID](../ROWID.md) in [oracle.jdbc.dcn](../../jdbc/dcn/package-summary.md)

    **Methods in [oracle.jdbc.dcn](../../jdbc/dcn/package-summary.md) that return [ROWID](../ROWID.md)**

    | Modifier and Type      | Method and Description                                                                                          |
    |------------------------|-----------------------------------------------------------------------------------------------------------------|
    | [`ROWID`](../ROWID.md) | RowChangeDescription.[`getRowid`](../../jdbc/dcn/RowChangeDescription.md)`()`<br>Returns the row id of the row. |
    | [`ROWID`](../ROWID.md) | RowChangeDescription.[`getRowid`](../../jdbc/dcn/RowChangeDescription.md)`()`<br>Returns the row id of the row. |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../ROWID.md)
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
