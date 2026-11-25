Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../CLOB.md)
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

## Uses of Class oracle.sql.CLOB

- **Packages that use [CLOB](../CLOB.md)**

  | Package     | Description                                                                                       |
  |-------------|---------------------------------------------------------------------------------------------------|
  | oracle.jdbc | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`. |
  | oracle.sql  | A package of classes that represent java SQL types and Oracle specific SQL types.                 |

- - ### Uses of [CLOB](../CLOB.md) in [oracle.jdbc](../../jdbc/package-summary.md)

    **Methods in [oracle.jdbc](../../jdbc/package-summary.md) that return [CLOB](../CLOB.md)**

    | Modifier and Type    | Method and Description                                                                                                                                                                          |
    |----------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`CLOB`](../CLOB.md) | OracleCallableStatement.[`getCLOB`](../../jdbc/OracleCallableStatement.md)`(int parameterIndex)`<br>Retrieves data into an `oracle.sql.CLOB` object.                                            |
    | [`CLOB`](../CLOB.md) | OracleResultSet.[`getCLOB`](../../jdbc/OracleResultSet.md)`(int columnIndex)`<br>Oracle extension.                                                                                              |
    | [`CLOB`](../CLOB.md) | OracleResultSet.[`getCLOB`](../../jdbc/OracleResultSet.md)`(int columnIndex)`<br>Oracle extension.                                                                                              |
    | [`CLOB`](../CLOB.md) | OracleCallableStatement.[`getCLOB`](../../jdbc/OracleCallableStatement.md)`(int parameterIndex)`<br>Retrieves data into an `oracle.sql.CLOB` object.                                            |
    | [`CLOB`](../CLOB.md) | OracleResultSet.[`getCLOB`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName)`<br>Oracle extension. |
    | [`CLOB`](../CLOB.md) | OracleResultSet.[`getCLOB`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName)`<br>Oracle extension. |

    **Methods in [oracle.jdbc](../../jdbc/package-summary.md) with parameters of type [CLOB](../CLOB.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                          |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | OraclePreparedStatement.[`setCLOB`](../../jdbc/OraclePreparedStatement.md)`(int parameterIndex, `[`CLOB`](../CLOB.md)` lob)`<br>Binds the designated parameter to a `oracle.sql.CLOB` value.                                                                                                    |
    | `void`            | OraclePreparedStatement.[`setCLOB`](../../jdbc/OraclePreparedStatement.md)`(int parameterIndex, `[`CLOB`](../CLOB.md)` lob)`<br>Binds the designated parameter to a `oracle.sql.CLOB` value.                                                                                                    |
    | `void`            | OracleCallableStatement.[`setCLOB`](../../jdbc/OracleCallableStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`CLOB`](../CLOB.md)` x)`<br>Sets the designated parameter to an `oracle.sql.CLOB`value.          |
    | `void`            | OracleCallableStatement.[`setCLOB`](../../jdbc/OracleCallableStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`CLOB`](../CLOB.md)` x)`<br>Sets the designated parameter to an `oracle.sql.CLOB`value.          |
    | `void`            | OraclePreparedStatement.[`setCLOBAtName`](../../jdbc/OraclePreparedStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`CLOB`](../CLOB.md)` value)`<br>Sets the designated parameter to an oracle.sql.CLOB value. |
    | `void`            | OraclePreparedStatement.[`setCLOBAtName`](../../jdbc/OraclePreparedStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`CLOB`](../CLOB.md)` value)`<br>Sets the designated parameter to an oracle.sql.CLOB value. |
    | `void`            | OracleResultSet.[`updateCLOB`](../../jdbc/OracleResultSet.md)`(int columnIndex, `[`CLOB`](../CLOB.md)` value)`<br>Oracle extension.                                                                                                                                                             |
    | `void`            | OracleResultSet.[`updateCLOB`](../../jdbc/OracleResultSet.md)`(int columnIndex, `[`CLOB`](../CLOB.md)` value)`<br>Oracle extension.                                                                                                                                                             |
    | `void`            | OracleResultSet.[`updateCLOB`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`CLOB`](../CLOB.md)` value)`<br>Oracle extension.                                                                |
    | `void`            | OracleResultSet.[`updateCLOB`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`CLOB`](../CLOB.md)` value)`<br>Oracle extension.                                                                |

  - ### Uses of [CLOB](../CLOB.md) in [oracle.sql](../package-summary.md)

    **Subclasses of [CLOB](../CLOB.md) in [oracle.sql](../package-summary.md)**

    | Modifier and Type | Class and Description                                                                                                                    |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------|
    | `class `          | [`NCLOB`](../NCLOB.md)<br>Deprecated. <br>Use java.sql.NClob interface for declaration instead of using concrete class oracle.sql.NCLOB. |

    **Methods in [oracle.sql](../package-summary.md) that return [CLOB](../CLOB.md)**

    | Modifier and Type             | Method and Description                                                                                                                                                                                                                                      |
    |-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`CLOB`](../CLOB.md) | CLOB.[`createTemporary`](../CLOB.md)`(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, boolean cache, int _duration)`<br>Deprecated. <br>Create a temporary clob.                             |
    | `static `[`CLOB`](../CLOB.md) | CLOB.[`createTemporary`](../CLOB.md)`(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, boolean cache, int _duration)`<br>Deprecated. <br>Create a temporary clob.                             |
    | `static `[`CLOB`](../CLOB.md) | CLOB.[`createTemporary`](../CLOB.md)`(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, boolean cache, int _duration, short form_of_use)`<br>Deprecated. <br>Create a temporary clob or nclob. |
    | `static `[`CLOB`](../CLOB.md) | CLOB.[`createTemporary`](../CLOB.md)`(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, boolean cache, int _duration, short form_of_use)`<br>Deprecated. <br>Create a temporary clob or nclob. |
    | `static `[`CLOB`](../CLOB.md) | CLOB.[`empty_lob`](../CLOB.md)`()`<br>Deprecated. <br>use getEmptyCLOB instead                                                                                                                                                                              |
    | `static `[`CLOB`](../CLOB.md) | CLOB.[`empty_lob`](../CLOB.md)`()`<br>Deprecated. <br>use getEmptyCLOB instead                                                                                                                                                                              |
    | `static `[`CLOB`](../CLOB.md) | CLOB.[`getEmptyCLOB`](../CLOB.md)`()`<br>Deprecated. <br>Return a empty lob.                                                                                                                                                                                |
    | `static `[`CLOB`](../CLOB.md) | CLOB.[`getEmptyCLOB`](../CLOB.md)`()`<br>Deprecated. <br>Return a empty lob.                                                                                                                                                                                |

    **Methods in [oracle.sql](../package-summary.md) with parameters of type [CLOB](../CLOB.md)**

    | Modifier and Type | Method and Description                                                                                                                            |
    |-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static void`     | CLOB.[`freeTemporary`](../CLOB.md)`(`[`CLOB`](../CLOB.md)` temp_lob)`<br>Deprecated. <br>Free the contents and the locator of the temporary clob. |
    | `static void`     | CLOB.[`freeTemporary`](../CLOB.md)`(`[`CLOB`](../CLOB.md)` temp_lob)`<br>Deprecated. <br>Free the contents and the locator of the temporary clob. |
    | `static short`    | CLOB.[`getDuration`](../CLOB.md)`(`[`CLOB`](../CLOB.md)` lob)`<br>Deprecated. <br>return the duration of a temporary LOB                          |
    | `static short`    | CLOB.[`getDuration`](../CLOB.md)`(`[`CLOB`](../CLOB.md)` lob)`<br>Deprecated. <br>return the duration of a temporary LOB                          |
    | `static boolean`  | CLOB.[`isTemporary`](../CLOB.md)`(`[`CLOB`](../CLOB.md)` lob)`<br>Deprecated. <br>Return true if the lob locator points to a temporary clob.      |
    | `static boolean`  | CLOB.[`isTemporary`](../CLOB.md)`(`[`CLOB`](../CLOB.md)` lob)`<br>Deprecated. <br>Return true if the lob locator points to a temporary clob.      |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../CLOB.md)
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
