Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OracleData.md)
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

## Uses of Interface oracle.jdbc.OracleData

- **Packages that use [OracleData](../OracleData.md)**

  | Package     | Description                                                                                       |
  |-------------|---------------------------------------------------------------------------------------------------|
  | oracle.jdbc | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`. |
  | oracle.sql  | A package of classes that represent java SQL types and Oracle specific SQL types.                 |

- - ### Uses of [OracleData](../OracleData.md) in [oracle.jdbc](../package-summary.md)

    **Methods in [oracle.jdbc](../package-summary.md) that return [OracleData](../OracleData.md)**

    | Modifier and Type                | Method and Description                                                                                                                                                                                                       |
    |----------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OracleData`](../OracleData.md) | OracleDataFactory.[`create`](../OracleDataFactory.md)`(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` jdbcValue, int sqlType)`<br>Create an OracleData from a jdbc Object |
    | [`OracleData`](../OracleData.md) | OracleDataFactory.[`create`](../OracleDataFactory.md)`(`[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` jdbcValue, int sqlType)`<br>Create an OracleData from a jdbc Object |

  - ### Uses of [OracleData](../OracleData.md) in [oracle.sql](../../sql/package-summary.md)

    **Classes in [oracle.sql](../../sql/package-summary.md) that implement [OracleData](../OracleData.md)**

    | Modifier and Type | Class and Description                                                                                                                                                        |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `class `          | [`ANYDATA`](../../sql/ANYDATA.md)<br>This class is the Java mapping of the SYS.ANYDATA SQL type.                                                                             |
    | `class `          | [`ArrayDescriptor`](../../sql/ArrayDescriptor.md)<br>Deprecated. <br>Use factory method OracleConnection.createOracleArray to create an instance of java.sql.Array directly. |
    | `class `          | [`OpaqueDescriptor`](../../sql/OpaqueDescriptor.md)<br>Deprecated. <br>OPAQUE types cannot be created on the client side.                                                    |
    | `class `          | [`StructDescriptor`](../../sql/StructDescriptor.md)<br>Deprecated. <br>Use factory method Connection.createStruct to create an instance of java.sql.Struct directly.         |
    | `class `          | [`TypeDescriptor`](../../sql/TypeDescriptor.md)<br>The descriptor of pre-defined types.                                                                                      |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OracleData.md)
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
