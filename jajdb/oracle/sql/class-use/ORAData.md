Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../ORAData.md)
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

## Uses of Interface oracle.sql.ORAData

- **Packages that use [ORAData](../ORAData.md)**

  | Package     | Description                                                                                       |
  |-------------|---------------------------------------------------------------------------------------------------|
  | oracle.jdbc | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`. |
  | oracle.sql  | A package of classes that represent java SQL types and Oracle specific SQL types.                 |

- - ### Uses of [ORAData](../ORAData.md) in [oracle.jdbc](../../jdbc/package-summary.md)

    **Methods in [oracle.jdbc](../../jdbc/package-summary.md) that return [ORAData](../ORAData.md)**

    | Modifier and Type          | Method and Description                                                                                                                                                                                                                                 |
    |----------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`ORAData`](../ORAData.md) | OracleResultSet.[`getORAData`](../../jdbc/OracleResultSet.md)`(int columnIndex, `[`ORADataFactory`](../ORADataFactory.md)` factory)`<br>Oracle extension.                                                                                              |
    | [`ORAData`](../ORAData.md) | OracleResultSet.[`getORAData`](../../jdbc/OracleResultSet.md)`(int columnIndex, `[`ORADataFactory`](../ORADataFactory.md)` factory)`<br>Oracle extension.                                                                                              |
    | [`ORAData`](../ORAData.md) | OracleResultSet.[`getORAData`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`ORADataFactory`](../ORADataFactory.md)` factory)`<br>Oracle extension. |
    | [`ORAData`](../ORAData.md) | OracleResultSet.[`getORAData`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`ORADataFactory`](../ORADataFactory.md)` factory)`<br>Oracle extension. |

    **Methods in [oracle.jdbc](../../jdbc/package-summary.md) with parameters of type [ORAData](../ORAData.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                                       |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | OraclePreparedStatement.[`setORAData`](../../jdbc/OraclePreparedStatement.md)`(int parameterIndex, `[`ORAData`](../ORAData.md)` x)`<br>Binds the designated parameter to a `oracle.sql.ORAData` value.                                                                                                       |
    | `void`            | OraclePreparedStatement.[`setORAData`](../../jdbc/OraclePreparedStatement.md)`(int parameterIndex, `[`ORAData`](../ORAData.md)` x)`<br>Binds the designated parameter to a `oracle.sql.ORAData` value.                                                                                                       |
    | `void`            | OracleCallableStatement.[`setORAData`](../../jdbc/OracleCallableStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`ORAData`](../ORAData.md)` x)`<br>Sets the designated parameter to an `oracle.sql.ORAData`value.           |
    | `void`            | OracleCallableStatement.[`setORAData`](../../jdbc/OracleCallableStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`ORAData`](../ORAData.md)` x)`<br>Sets the designated parameter to an `oracle.sql.ORAData`value.           |
    | `void`            | OraclePreparedStatement.[`setORADataAtName`](../../jdbc/OraclePreparedStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`ORAData`](../ORAData.md)` value)`<br>Sets the designated parameter to an `oracle.sql.ORAData`value. |
    | `void`            | OraclePreparedStatement.[`setORADataAtName`](../../jdbc/OraclePreparedStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`ORAData`](../ORAData.md)` value)`<br>Sets the designated parameter to an `oracle.sql.ORAData`value. |
    | `void`            | OracleResultSet.[`updateORAData`](../../jdbc/OracleResultSet.md)`(int columnIndex, `[`ORAData`](../ORAData.md)` value)`<br>Oracle extension.                                                                                                                                                                 |
    | `void`            | OracleResultSet.[`updateORAData`](../../jdbc/OracleResultSet.md)`(int columnIndex, `[`ORAData`](../ORAData.md)` value)`<br>Oracle extension.                                                                                                                                                                 |
    | `void`            | OracleResultSet.[`updateORAData`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`ORAData`](../ORAData.md)` value)`<br>Oracle extension.                                                                    |
    | `void`            | OracleResultSet.[`updateORAData`](../../jdbc/OracleResultSet.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` columnName, `[`ORAData`](../ORAData.md)` value)`<br>Oracle extension.                                                                    |

  - ### Uses of [ORAData](../ORAData.md) in [oracle.sql](../package-summary.md)

    **Classes in [oracle.sql](../package-summary.md) that implement [ORAData](../ORAData.md)**

    | Modifier and Type | Class and Description                                                                                                                                                 |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `class `          | [`ANYDATA`](../ANYDATA.md)<br>This class is the Java mapping of the SYS.ANYDATA SQL type.                                                                             |
    | `class `          | [`ArrayDescriptor`](../ArrayDescriptor.md)<br>Deprecated. <br>Use factory method OracleConnection.createOracleArray to create an instance of java.sql.Array directly. |
    | `class `          | [`OpaqueDescriptor`](../OpaqueDescriptor.md)<br>Deprecated. <br>OPAQUE types cannot be created on the client side.                                                    |
    | `class `          | [`StructDescriptor`](../StructDescriptor.md)<br>Deprecated. <br>Use factory method Connection.createStruct to create an instance of java.sql.Struct directly.         |
    | `class `          | [`TypeDescriptor`](../TypeDescriptor.md)<br>The descriptor of pre-defined types.                                                                                      |

    **Methods in [oracle.sql](../package-summary.md) that return [ORAData](../ORAData.md)**

    | Modifier and Type          | Method and Description                                                                                                                  |
    |----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
    | [`ORAData`](../ORAData.md) | ORADataFactory.[`create`](../ORADataFactory.md)`(`[`Datum`](../Datum.md)` d, int sqlType)`<br>Create an ORAData from a oracle.sql.Datum |
    | [`ORAData`](../ORAData.md) | ORADataFactory.[`create`](../ORADataFactory.md)`(`[`Datum`](../Datum.md)` d, int sqlType)`<br>Create an ORAData from a oracle.sql.Datum |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../ORAData.md)
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
