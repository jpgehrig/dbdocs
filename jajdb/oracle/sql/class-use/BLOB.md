Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../BLOB.md)
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

## Uses of Class oracle.sql.BLOB

- **Packages that use [BLOB](../BLOB.md)**

  | Package     | Description                                                                                       |
  |-------------|---------------------------------------------------------------------------------------------------|
  | oracle.jdbc | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`. |
  | oracle.sql  | A package of classes that represent java SQL types and Oracle specific SQL types.                 |

- - ### Uses of [BLOB](../BLOB.md) in [oracle.jdbc](../../jdbc/package-summary.md)

    **Methods in [oracle.jdbc](../../jdbc/package-summary.md) that return [BLOB](../BLOB.md)**

    | Modifier and Type    | Method and Description                                                                                                                                                                          |
    |----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`BLOB`](../BLOB.md) | OracleCallableStatement.[`getBLOB`](../../jdbc/OracleCallableStatement.md)`(int parameterIndex)`<br>Retrieves data into an `oracle.sql.BLOB` object.                                            |
    | [`BLOB`](../BLOB.md) | OracleResultSet.[`getBLOB`](../../jdbc/OracleResultSet.md)`(int columnIndex)`<br>Oracle extension.                                                                                              |
    | [`BLOB`](../BLOB.md) | OracleResultSet.[`getBLOB`](../../jdbc/OracleResultSet.md)`(int columnIndex)`<br>Oracle extension.                                                                                              |
    | [`BLOB`](../BLOB.md) | OracleCallableStatement.[`getBLOB`](../../jdbc/OracleCallableStatement.md)`(int parameterIndex)`<br>Retrieves data into an `oracle.sql.BLOB` object.                                            |
    | [`BLOB`](../BLOB.md) | OracleResultSet.[`getBLOB`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName)`<br>Oracle extension. |
    | [`BLOB`](../BLOB.md) | OracleResultSet.[`getBLOB`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName)`<br>Oracle extension. |

    **Methods in [oracle.jdbc](../../jdbc/package-summary.md) with parameters of type [BLOB](../BLOB.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                          |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | OraclePreparedStatement.[`setBLOB`](../../jdbc/OraclePreparedStatement.md)`(int parameterIndex, `[`BLOB`](../BLOB.md)` lob)`<br>Binds the designated parameter to a `oracle.sql.BLOB` value.                                                                                                    |
    | `void`            | OraclePreparedStatement.[`setBLOB`](../../jdbc/OraclePreparedStatement.md)`(int parameterIndex, `[`BLOB`](../BLOB.md)` lob)`<br>Binds the designated parameter to a `oracle.sql.BLOB` value.                                                                                                    |
    | `void`            | OracleCallableStatement.[`setBLOB`](../../jdbc/OracleCallableStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`BLOB`](../BLOB.md)` x)`<br>Sets the designated parameter to an `oracle.sql.BLOB`value.          |
    | `void`            | OracleCallableStatement.[`setBLOB`](../../jdbc/OracleCallableStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`BLOB`](../BLOB.md)` x)`<br>Sets the designated parameter to an `oracle.sql.BLOB`value.          |
    | `void`            | OraclePreparedStatement.[`setBLOBAtName`](../../jdbc/OraclePreparedStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`BLOB`](../BLOB.md)` value)`<br>Sets the designated parameter to an oracle.sql.BLOB value. |
    | `void`            | OraclePreparedStatement.[`setBLOBAtName`](../../jdbc/OraclePreparedStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`BLOB`](../BLOB.md)` value)`<br>Sets the designated parameter to an oracle.sql.BLOB value. |
    | `void`            | OracleResultSet.[`updateBLOB`](../../jdbc/OracleResultSet.md)`(int columnIndex, `[`BLOB`](../BLOB.md)` value)`<br>Oracle extension.                                                                                                                                                             |
    | `void`            | OracleResultSet.[`updateBLOB`](../../jdbc/OracleResultSet.md)`(int columnIndex, `[`BLOB`](../BLOB.md)` value)`<br>Oracle extension.                                                                                                                                                             |
    | `void`            | OracleResultSet.[`updateBLOB`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`BLOB`](../BLOB.md)` value)`<br>Oracle extension.                                                                |
    | `void`            | OracleResultSet.[`updateBLOB`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`BLOB`](../BLOB.md)` value)`<br>Oracle extension.                                                                |

  - ### Uses of [BLOB](../BLOB.md) in [oracle.sql](../package-summary.md)

    **Methods in [oracle.sql](../package-summary.md) that return [BLOB](../BLOB.md)**

    | Modifier and Type             | Method and Description                                                                                                                                                                                                          |
    |-------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`BLOB`](../BLOB.md) | BLOB.[`createTemporary`](../BLOB.md)`(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, boolean cache, int _duration)`<br>Deprecated. <br>Create a temporary blob. |
    | `static `[`BLOB`](../BLOB.md) | BLOB.[`createTemporary`](../BLOB.md)`(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, boolean cache, int _duration)`<br>Deprecated. <br>Create a temporary blob. |
    | `static `[`BLOB`](../BLOB.md) | BLOB.[`empty_lob`](../BLOB.md)`()`<br>Deprecated. <br>use getEmptyBLOB instead                                                                                                                                                  |
    | `static `[`BLOB`](../BLOB.md) | BLOB.[`empty_lob`](../BLOB.md)`()`<br>Deprecated. <br>use getEmptyBLOB instead                                                                                                                                                  |
    | `static `[`BLOB`](../BLOB.md) | BLOB.[`getEmptyBLOB`](../BLOB.md)`()`<br>Deprecated. <br>Return a empty lob.                                                                                                                                                    |
    | `static `[`BLOB`](../BLOB.md) | BLOB.[`getEmptyBLOB`](../BLOB.md)`()`<br>Deprecated. <br>Return a empty lob.                                                                                                                                                    |

    **Methods in [oracle.sql](../package-summary.md) with parameters of type [BLOB](../BLOB.md)**

    | Modifier and Type | Method and Description                                                                                                                            |
    |-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static void`     | BLOB.[`freeTemporary`](../BLOB.md)`(`[`BLOB`](../BLOB.md)` temp_lob)`<br>Deprecated. <br>Free the contents and the locator of the temporary blob. |
    | `static void`     | BLOB.[`freeTemporary`](../BLOB.md)`(`[`BLOB`](../BLOB.md)` temp_lob)`<br>Deprecated. <br>Free the contents and the locator of the temporary blob. |
    | `static short`    | BLOB.[`getDuration`](../BLOB.md)`(`[`BLOB`](../BLOB.md)` lob)`<br>Deprecated. <br>return the duration of a temporary LOB                          |
    | `static short`    | BLOB.[`getDuration`](../BLOB.md)`(`[`BLOB`](../BLOB.md)` lob)`<br>Deprecated. <br>return the duration of a temporary LOB                          |
    | `static boolean`  | BLOB.[`isTemporary`](../BLOB.md)`(`[`BLOB`](../BLOB.md)` lob)`<br>Deprecated. <br>Return true if the lob locator points to a temporary blob.      |
    | `static boolean`  | BLOB.[`isTemporary`](../BLOB.md)`(`[`BLOB`](../BLOB.md)` lob)`<br>Deprecated. <br>Return true if the lob locator points to a temporary blob.      |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../BLOB.md)
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
