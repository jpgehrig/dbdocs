Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OracleTypeMetaData.md)
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

## Uses of Interface oracle.jdbc.OracleTypeMetaData

- **Packages that use [OracleTypeMetaData](../OracleTypeMetaData.md)**

  | Package     | Description                                                                                       |
  |-------------|---------------------------------------------------------------------------------------------------|
  | oracle.jdbc | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`. |
  | oracle.sql  | A package of classes that represent java SQL types and Oracle specific SQL types.                 |

- - ### Uses of [OracleTypeMetaData](../OracleTypeMetaData.md) in [oracle.jdbc](../package-summary.md)

    **Subinterfaces of [OracleTypeMetaData](../OracleTypeMetaData.md) in [oracle.jdbc](../package-summary.md)**

    | Modifier and Type   | Interface and Description                                                                                                           |
    |---------------------|-------------------------------------------------------------------------------------------------------------------------------------|
    | `static interface ` | [`OracleTypeMetaData.Array`](../OracleTypeMetaData.Array.md)<br>This nested interfacet defines additional methods for array types   |
    | `static interface ` | [`OracleTypeMetaData.Opaque`](../OracleTypeMetaData.Opaque.md)<br>This nested interface defines additional methods for opaque types |
    | `static interface ` | [`OracleTypeMetaData.Struct`](../OracleTypeMetaData.Struct.md)<br>This nested interface defines additional methods for struct types |

    **Methods in [oracle.jdbc](../package-summary.md) that return [OracleTypeMetaData](../OracleTypeMetaData.md)**

    | Modifier and Type                                | Method and Description                                                                                                                                                                                                                                |
    |--------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OracleTypeMetaData`](../OracleTypeMetaData.md) | OracleArray.[`getOracleMetaData`](../OracleArray.md)`()`<br>Oracle extension.                                                                                                                                                                         |
    | [`OracleTypeMetaData`](../OracleTypeMetaData.md) | OracleOpaque.[`getOracleMetaData`](../OracleOpaque.md)`()`<br>Oracle extension.                                                                                                                                                                       |
    | [`OracleTypeMetaData`](../OracleTypeMetaData.md) | OracleRef.[`getOracleMetaData`](../OracleRef.md)`()`<br>Oracle extension.                                                                                                                                                                             |
    | [`OracleTypeMetaData`](../OracleTypeMetaData.md) | OracleStruct.[`getOracleMetaData`](../OracleStruct.md)`()`<br>Oracle extension.                                                                                                                                                                       |
    | [`OracleTypeMetaData`](../OracleTypeMetaData.md) | OracleStruct.[`getOracleMetaData`](../OracleStruct.md)`()`<br>Oracle extension.                                                                                                                                                                       |
    | [`OracleTypeMetaData`](../OracleTypeMetaData.md) | OracleRef.[`getOracleMetaData`](../OracleRef.md)`()`<br>Oracle extension.                                                                                                                                                                             |
    | [`OracleTypeMetaData`](../OracleTypeMetaData.md) | OracleOpaque.[`getOracleMetaData`](../OracleOpaque.md)`()`<br>Oracle extension.                                                                                                                                                                       |
    | [`OracleTypeMetaData`](../OracleTypeMetaData.md) | OracleArray.[`getOracleMetaData`](../OracleArray.md)`()`<br>Oracle extension.                                                                                                                                                                         |
    | [`OracleTypeMetaData`](../OracleTypeMetaData.md) | AdditionalDatabaseMetaData.[`getOracleTypeMetaData`](../AdditionalDatabaseMetaData.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sqlTypeName)`<br>Return the type metadata for a named type. |
    | [`OracleTypeMetaData`](../OracleTypeMetaData.md) | OracleDatabaseMetaData.[`getOracleTypeMetaData`](../OracleDatabaseMetaData.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sqlTypeName)`                                                       |
    | [`OracleTypeMetaData`](../OracleTypeMetaData.md) | OracleDatabaseMetaData.[`getOracleTypeMetaData`](../OracleDatabaseMetaData.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sqlTypeName)`                                                       |
    | [`OracleTypeMetaData`](../OracleTypeMetaData.md) | AdditionalDatabaseMetaData.[`getOracleTypeMetaData`](../AdditionalDatabaseMetaData.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sqlTypeName)`<br>Return the type metadata for a named type. |

  - ### Uses of [OracleTypeMetaData](../OracleTypeMetaData.md) in [oracle.sql](../../sql/package-summary.md)

    **Classes in [oracle.sql](../../sql/package-summary.md) that implement [OracleTypeMetaData](../OracleTypeMetaData.md)**

    | Modifier and Type | Class and Description                                                                                                                                                        |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `class `          | [`ArrayDescriptor`](../../sql/ArrayDescriptor.md)<br>Deprecated. <br>Use factory method OracleConnection.createOracleArray to create an instance of java.sql.Array directly. |
    | `class `          | [`OpaqueDescriptor`](../../sql/OpaqueDescriptor.md)<br>Deprecated. <br>OPAQUE types cannot be created on the client side.                                                    |
    | `class `          | [`StructDescriptor`](../../sql/StructDescriptor.md)<br>Deprecated. <br>Use factory method Connection.createStruct to create an instance of java.sql.Struct directly.         |
    | `class `          | [`TypeDescriptor`](../../sql/TypeDescriptor.md)<br>The descriptor of pre-defined types.                                                                                      |

    **Methods in [oracle.sql](../../sql/package-summary.md) that return [OracleTypeMetaData](../OracleTypeMetaData.md)**

    | Modifier and Type                                | Method and Description                                                                                        |
    |--------------------------------------------------|---------------------------------------------------------------------------------------------------------------|
    | [`OracleTypeMetaData`](../OracleTypeMetaData.md) | ARRAY.[`getOracleMetaData`](../../sql/ARRAY.md)`()`<br>Deprecated. <br>Return the type data for this object   |
    | [`OracleTypeMetaData`](../OracleTypeMetaData.md) | OPAQUE.[`getOracleMetaData`](../../sql/OPAQUE.md)`()`<br>Deprecated. <br>Return the type data for this object |
    | [`OracleTypeMetaData`](../OracleTypeMetaData.md) | REF.[`getOracleMetaData`](../../sql/REF.md)`()`<br>Deprecated. <br>Return the type data for this object       |
    | [`OracleTypeMetaData`](../OracleTypeMetaData.md) | STRUCT.[`getOracleMetaData`](../../sql/STRUCT.md)`()`<br>Deprecated. <br>Return the type data for this object |
    | [`OracleTypeMetaData`](../OracleTypeMetaData.md) | STRUCT.[`getOracleMetaData`](../../sql/STRUCT.md)`()`<br>Deprecated. <br>Return the type data for this object |
    | [`OracleTypeMetaData`](../OracleTypeMetaData.md) | REF.[`getOracleMetaData`](../../sql/REF.md)`()`<br>Deprecated. <br>Return the type data for this object       |
    | [`OracleTypeMetaData`](../OracleTypeMetaData.md) | OPAQUE.[`getOracleMetaData`](../../sql/OPAQUE.md)`()`<br>Deprecated. <br>Return the type data for this object |
    | [`OracleTypeMetaData`](../OracleTypeMetaData.md) | ARRAY.[`getOracleMetaData`](../../sql/ARRAY.md)`()`<br>Deprecated. <br>Return the type data for this object   |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../OracleTypeMetaData.md)
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
