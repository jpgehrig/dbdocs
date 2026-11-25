Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../ARRAY.md)
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

## Uses of Class oracle.sql.ARRAY

- **Packages that use [ARRAY](../ARRAY.md)**

  | Package     | Description                                                                                       |
  |-------------|---------------------------------------------------------------------------------------------------|
  | oracle.jdbc | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`. |
  | oracle.sql  | A package of classes that represent java SQL types and Oracle specific SQL types.                 |

- - ### Uses of [ARRAY](../ARRAY.md) in [oracle.jdbc](../../jdbc/package-summary.md)

    **Methods in [oracle.jdbc](../../jdbc/package-summary.md) that return [ARRAY](../ARRAY.md)**

    | Modifier and Type      | Method and Description                                                                                                                                                                                                                                                                                                                                                     |
    |------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`ARRAY`](../ARRAY.md) | OracleConnection.[`createARRAY`](../../jdbc/OracleConnection.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` typeName, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` elements)`<br>Creates an ARRAY object with the given type name and elements.               |
    | [`ARRAY`](../ARRAY.md) | OracleConnectionWrapper.[`createARRAY`](../../jdbc/OracleConnectionWrapper.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` typeName, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` elements)`<br>Creates an ARRAY object with the given type name and elements. |
    | [`ARRAY`](../ARRAY.md) | OracleConnectionWrapper.[`createARRAY`](../../jdbc/OracleConnectionWrapper.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` typeName, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` elements)`<br>Creates an ARRAY object with the given type name and elements. |
    | [`ARRAY`](../ARRAY.md) | OracleConnection.[`createARRAY`](../../jdbc/OracleConnection.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` typeName, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` elements)`<br>Creates an ARRAY object with the given type name and elements.               |
    | [`ARRAY`](../ARRAY.md) | OracleCallableStatement.[`getARRAY`](../../jdbc/OracleCallableStatement.md)`(int parameterIndex)`<br>Retrieves data into an `oracle.sql.ARRAY` object.                                                                                                                                                                                                                     |
    | [`ARRAY`](../ARRAY.md) | OracleResultSet.[`getARRAY`](../../jdbc/OracleResultSet.md)`(int columnIndex)`<br>Oracle extension.                                                                                                                                                                                                                                                                        |
    | [`ARRAY`](../ARRAY.md) | OracleResultSet.[`getARRAY`](../../jdbc/OracleResultSet.md)`(int columnIndex)`<br>Oracle extension.                                                                                                                                                                                                                                                                        |
    | [`ARRAY`](../ARRAY.md) | OracleCallableStatement.[`getARRAY`](../../jdbc/OracleCallableStatement.md)`(int parameterIndex)`<br>Retrieves data into an `oracle.sql.ARRAY` object.                                                                                                                                                                                                                     |
    | [`ARRAY`](../ARRAY.md) | OracleResultSet.[`getARRAY`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName)`<br>Oracle extension.                                                                                                                                                                           |
    | [`ARRAY`](../ARRAY.md) | OracleResultSet.[`getARRAY`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName)`<br>Oracle extension.                                                                                                                                                                           |

    **Methods in [oracle.jdbc](../../jdbc/package-summary.md) with parameters of type [ARRAY](../ARRAY.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                               |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | OraclePreparedStatement.[`setARRAY`](../../jdbc/OraclePreparedStatement.md)`(int parameterIndex, `[`ARRAY`](../ARRAY.md)` arr)`<br>Binds the designated parameter to a `oracle.sql.ARRAY`.                                                                                                           |
    | `void`            | OraclePreparedStatement.[`setARRAY`](../../jdbc/OraclePreparedStatement.md)`(int parameterIndex, `[`ARRAY`](../ARRAY.md)` arr)`<br>Binds the designated parameter to a `oracle.sql.ARRAY`.                                                                                                           |
    | `void`            | OracleCallableStatement.[`setARRAY`](../../jdbc/OracleCallableStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`ARRAY`](../ARRAY.md)` x)`<br>Sets the designated parameter to an `oracle.sql.ARRAY`value.           |
    | `void`            | OracleCallableStatement.[`setARRAY`](../../jdbc/OracleCallableStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`ARRAY`](../ARRAY.md)` x)`<br>Sets the designated parameter to an `oracle.sql.ARRAY`value.           |
    | `void`            | OraclePreparedStatement.[`setARRAYAtName`](../../jdbc/OraclePreparedStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`ARRAY`](../ARRAY.md)` value)`<br>Sets the designated parameter to a `oracle.sql.ARRAY` value. |
    | `void`            | OraclePreparedStatement.[`setARRAYAtName`](../../jdbc/OraclePreparedStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`ARRAY`](../ARRAY.md)` value)`<br>Sets the designated parameter to a `oracle.sql.ARRAY` value. |
    | `void`            | OracleResultSet.[`updateARRAY`](../../jdbc/OracleResultSet.md)`(int columnIndex, `[`ARRAY`](../ARRAY.md)` value)`<br>Oracle extension.                                                                                                                                                               |
    | `void`            | OracleResultSet.[`updateARRAY`](../../jdbc/OracleResultSet.md)`(int columnIndex, `[`ARRAY`](../ARRAY.md)` value)`<br>Oracle extension.                                                                                                                                                               |
    | `void`            | OracleResultSet.[`updateARRAY`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`ARRAY`](../ARRAY.md)` value)`<br>Oracle extension.                                                                  |
    | `void`            | OracleResultSet.[`updateARRAY`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`ARRAY`](../ARRAY.md)` value)`<br>Oracle extension.                                                                  |

  - ### Uses of [ARRAY](../ARRAY.md) in [oracle.sql](../package-summary.md)

    **Methods in [oracle.sql](../package-summary.md) with parameters of type [ARRAY](../ARRAY.md)**

    | Modifier and Type                                                                                    | Method and Description                                                                                                                                                                                                                                       |
    |------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true) | ArrayDescriptor.[`toResultSet`](../ArrayDescriptor.md)`(`[`ARRAY`](../ARRAY.md)` array, long index, int count, `[`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)` map, boolean saveLocalCopy)`<br>Deprecated. <br>  |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true) | ArrayDescriptor.[`toResultSet`](../ArrayDescriptor.md)`(`[`ARRAY`](../ARRAY.md)` array, long index, int count, `[`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)` map, boolean saveLocalCopy)`<br>Deprecated. <br>  |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../ARRAY.md)
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
