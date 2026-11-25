Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../TypeDescriptor.md)
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

## Uses of Class oracle.sql.TypeDescriptor

- **Packages that use [TypeDescriptor](../TypeDescriptor.md)**

  | Package     | Description                                                                                       |
  |-------------|---------------------------------------------------------------------------------------------------|
  | oracle.jdbc | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`. |
  | oracle.sql  | A package of classes that represent java SQL types and Oracle specific SQL types.                 |

- - ### Uses of [TypeDescriptor](../TypeDescriptor.md) in [oracle.jdbc](../../jdbc/package-summary.md)

    **Methods in [oracle.jdbc](../../jdbc/package-summary.md) that return [TypeDescriptor](../TypeDescriptor.md)**

    | Modifier and Type                            | Method and Description                                                                                                                                                                                                                                                                                                         |
    |----------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`TypeDescriptor`](../TypeDescriptor.md)`[]` | OracleConnection.[`getAllTypeDescriptorsInCurrentSchema`](../../jdbc/OracleConnection.md)`()`<br>Obtain all the type descriptors associated with object types or array in the schema of this connection.                                                                                                                       |
    | [`TypeDescriptor`](../TypeDescriptor.md)`[]` | OracleConnectionWrapper.[`getAllTypeDescriptorsInCurrentSchema`](../../jdbc/OracleConnectionWrapper.md)`()`                                                                                                                                                                                                                    |
    | [`TypeDescriptor`](../TypeDescriptor.md)`[]` | OracleConnectionWrapper.[`getAllTypeDescriptorsInCurrentSchema`](../../jdbc/OracleConnectionWrapper.md)`()`                                                                                                                                                                                                                    |
    | [`TypeDescriptor`](../TypeDescriptor.md)`[]` | OracleConnection.[`getAllTypeDescriptorsInCurrentSchema`](../../jdbc/OracleConnection.md)`()`<br>Obtain all the type descriptors associated with object types or array in the schema of this connection.                                                                                                                       |
    | [`TypeDescriptor`](../TypeDescriptor.md)`[]` | OracleConnection.[`getTypeDescriptorsFromList`](../../jdbc/OracleConnection.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[][] schemaAndTypeNamePairs)`<br>Obtain the type descriptors associated with object types or arrays from an array of scheama and type names. |
    | [`TypeDescriptor`](../TypeDescriptor.md)`[]` | OracleConnectionWrapper.[`getTypeDescriptorsFromList`](../../jdbc/OracleConnectionWrapper.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[][] schemaAndTypeNamePairs)`                                                                                                  |
    | [`TypeDescriptor`](../TypeDescriptor.md)`[]` | OracleConnectionWrapper.[`getTypeDescriptorsFromList`](../../jdbc/OracleConnectionWrapper.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[][] schemaAndTypeNamePairs)`                                                                                                  |
    | [`TypeDescriptor`](../TypeDescriptor.md)`[]` | OracleConnection.[`getTypeDescriptorsFromList`](../../jdbc/OracleConnection.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[][] schemaAndTypeNamePairs)`<br>Obtain the type descriptors associated with object types or arrays from an array of scheama and type names. |
    | [`TypeDescriptor`](../TypeDescriptor.md)`[]` | OracleConnection.[`getTypeDescriptorsFromListInCurrentSchema`](../../jdbc/OracleConnection.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[] typeNames)`<br>Obtain the type descriptors associated with object types or array in a schema from an array of type names.  |
    | [`TypeDescriptor`](../TypeDescriptor.md)`[]` | OracleConnectionWrapper.[`getTypeDescriptorsFromListInCurrentSchema`](../../jdbc/OracleConnectionWrapper.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[] typeNames)`                                                                                                  |
    | [`TypeDescriptor`](../TypeDescriptor.md)`[]` | OracleConnectionWrapper.[`getTypeDescriptorsFromListInCurrentSchema`](../../jdbc/OracleConnectionWrapper.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[] typeNames)`                                                                                                  |
    | [`TypeDescriptor`](../TypeDescriptor.md)`[]` | OracleConnection.[`getTypeDescriptorsFromListInCurrentSchema`](../../jdbc/OracleConnection.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[] typeNames)`<br>Obtain the type descriptors associated with object types or array in a schema from an array of type names.  |

  - ### Uses of [TypeDescriptor](../TypeDescriptor.md) in [oracle.sql](../package-summary.md)

    **Subclasses of [TypeDescriptor](../TypeDescriptor.md) in [oracle.sql](../package-summary.md)**

    | Modifier and Type | Class and Description                                                                                                                                                 |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `class `          | [`ArrayDescriptor`](../ArrayDescriptor.md)<br>Deprecated. <br>Use factory method OracleConnection.createOracleArray to create an instance of java.sql.Array directly. |
    | `class `          | [`OpaqueDescriptor`](../OpaqueDescriptor.md)<br>Deprecated. <br>OPAQUE types cannot be created on the client side.                                                    |
    | `class `          | [`StructDescriptor`](../StructDescriptor.md)<br>Deprecated. <br>Use factory method Connection.createStruct to create an instance of java.sql.Struct directly.         |

    **Methods in [oracle.sql](../package-summary.md) that return [TypeDescriptor](../TypeDescriptor.md)**

    | Modifier and Type                        | Method and Description                                                                                     |
    |------------------------------------------|------------------------------------------------------------------------------------------------------------|
    | [`TypeDescriptor`](../TypeDescriptor.md) | ANYDATA.[`getTypeDescriptor`](../ANYDATA.md)`()`<br>Returns the type description of this ANYDATA instance. |
    | [`TypeDescriptor`](../TypeDescriptor.md) | AttributeDescriptor.[`getTypeDescriptor`](../AttributeDescriptor.md)`()`                                   |
    | [`TypeDescriptor`](../TypeDescriptor.md) | AttributeDescriptor.[`getTypeDescriptor`](../AttributeDescriptor.md)`()`                                   |
    | [`TypeDescriptor`](../TypeDescriptor.md) | ANYDATA.[`getTypeDescriptor`](../ANYDATA.md)`()`<br>Returns the type description of this ANYDATA instance. |

    **Methods in [oracle.sql](../package-summary.md) with parameters of type [TypeDescriptor](../TypeDescriptor.md)**

    | Modifier and Type | Method and Description                                                                                               |
    |-------------------|----------------------------------------------------------------------------------------------------------------------|
    | `static void`     | DatumWithConnection.[`assertNotNull`](../DatumWithConnection.md)`(`[`TypeDescriptor`](../TypeDescriptor.md)` desc)`  |
    | `static void`     | DatumWithConnection.[`assertNotNull`](../DatumWithConnection.md)`(`[`TypeDescriptor`](../TypeDescriptor.md)` desc)`  |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../TypeDescriptor.md)
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
