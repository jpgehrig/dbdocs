Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../StructDescriptor.md)
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

## Uses of Class oracle.sql.StructDescriptor

- **Packages that use [StructDescriptor](../StructDescriptor.md)**

  | Package     | Description                                                                                       |
  |-------------|---------------------------------------------------------------------------------------------------|
  | oracle.jdbc | Beginning in Oracle9*i*, the Oracle extensions to JDBC are captured in the package `oracle.jdbc`. |
  | oracle.sql  | A package of classes that represent java SQL types and Oracle specific SQL types.                 |

- - ### Uses of [StructDescriptor](../StructDescriptor.md) in [oracle.jdbc](../../jdbc/package-summary.md)

    **Methods in [oracle.jdbc](../../jdbc/package-summary.md) with parameters of type [StructDescriptor](../StructDescriptor.md)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                                                                           |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | OraclePreparedStatement.[`setStructDescriptor`](../../jdbc/OraclePreparedStatement.md)`(int parameterIndex, `[`StructDescriptor`](../StructDescriptor.md)` desc)`<br>Binds the bind type of designated parameter from an oracle.sql.StructDescriptor.                                                                                            |
    | `void`            | OraclePreparedStatement.[`setStructDescriptor`](../../jdbc/OraclePreparedStatement.md)`(int parameterIndex, `[`StructDescriptor`](../StructDescriptor.md)` desc)`<br>Binds the bind type of designated parameter from an oracle.sql.StructDescriptor.                                                                                            |
    | `void`            | OracleCallableStatement.[`setStructDescriptor`](../../jdbc/OracleCallableStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`StructDescriptor`](../StructDescriptor.md)` x)`                                                                                      |
    | `void`            | OracleCallableStatement.[`setStructDescriptor`](../../jdbc/OracleCallableStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`StructDescriptor`](../StructDescriptor.md)` x)`                                                                                      |
    | `void`            | OraclePreparedStatement.[`setStructDescriptorAtName`](../../jdbc/OraclePreparedStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`StructDescriptor`](../StructDescriptor.md)` desc)`<br>Sets the designated parameter to an `oracle.sql.StructDescriptor` value. |
    | `void`            | OraclePreparedStatement.[`setStructDescriptorAtName`](../../jdbc/OraclePreparedStatement.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`StructDescriptor`](../StructDescriptor.md)` desc)`<br>Sets the designated parameter to an `oracle.sql.StructDescriptor` value. |

  - ### Uses of [StructDescriptor](../StructDescriptor.md) in [oracle.sql](../package-summary.md)

    **Methods in [oracle.sql](../package-summary.md) that return [StructDescriptor](../StructDescriptor.md)**

    | Modifier and Type                                     | Method and Description                                                                                                                                                                                                                                                                                                                                        |
    |-------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`StructDescriptor`](../StructDescriptor.md) | StructDescriptor.[`createDescriptor`](../StructDescriptor.md)`(oracle.sql.SQLName name, `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn)`<br>Deprecated.                                                                                                                                        |
    | `static `[`StructDescriptor`](../StructDescriptor.md) | StructDescriptor.[`createDescriptor`](../StructDescriptor.md)`(oracle.sql.SQLName name, `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn)`<br>Deprecated.                                                                                                                                        |
    | `static `[`StructDescriptor`](../StructDescriptor.md) | StructDescriptor.[`createDescriptor`](../StructDescriptor.md)`(oracle.sql.SQLName sqlName, `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, boolean recurse, boolean force)`<br>Deprecated.                                                                                                     |
    | `static `[`StructDescriptor`](../StructDescriptor.md) | StructDescriptor.[`createDescriptor`](../StructDescriptor.md)`(oracle.sql.SQLName sqlName, `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, boolean recurse, boolean force)`<br>Deprecated.                                                                                                     |
    | `static `[`StructDescriptor`](../StructDescriptor.md) | StructDescriptor.[`createDescriptor`](../StructDescriptor.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name, `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn)`<br>Deprecated. <br>Descriptor factory.                                 |
    | `static `[`StructDescriptor`](../StructDescriptor.md) | StructDescriptor.[`createDescriptor`](../StructDescriptor.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name, `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn)`<br>Deprecated. <br>Descriptor factory.                                 |
    | `static `[`StructDescriptor`](../StructDescriptor.md) | StructDescriptor.[`createDescriptor`](../StructDescriptor.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name, `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, boolean recurse, boolean force)`<br>Deprecated. <br>Descriptor factory. |
    | `static `[`StructDescriptor`](../StructDescriptor.md) | StructDescriptor.[`createDescriptor`](../StructDescriptor.md)`(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` name, `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, boolean recurse, boolean force)`<br>Deprecated. <br>Descriptor factory. |
    | [`StructDescriptor`](../StructDescriptor.md)          | REF.[`getDescriptor`](../REF.md)`()`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                                                                                                     |
    | [`StructDescriptor`](../StructDescriptor.md)          | STRUCT.[`getDescriptor`](../STRUCT.md)`()`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                                                                                               |
    | [`StructDescriptor`](../StructDescriptor.md)          | STRUCT.[`getDescriptor`](../STRUCT.md)`()`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                                                                                               |
    | [`StructDescriptor`](../StructDescriptor.md)          | REF.[`getDescriptor`](../REF.md)`()`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                                                                                                     |

    **Constructors in [oracle.sql](../package-summary.md) with parameters of type [StructDescriptor](../StructDescriptor.md)**

    | Constructor and Description                                                                                                                                                                                                                                                                                                                    |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`JAVA_STRUCT`](../JAVA_STRUCT.md)`(`[`StructDescriptor`](../StructDescriptor.md)` type, `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)`[] attributes)`<br>Constructor.       |
    | [`JAVA_STRUCT`](../JAVA_STRUCT.md)`(`[`StructDescriptor`](../StructDescriptor.md)` type, `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)`[] attributes)`<br>Constructor.       |
    | [`STRUCT`](../STRUCT.md)`(`[`StructDescriptor`](../StructDescriptor.md)` type, `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)` attrList)`<br>Deprecated. <br>                       |
    | [`STRUCT`](../STRUCT.md)`(`[`StructDescriptor`](../StructDescriptor.md)` type, `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Map`](http://download.oracle.com/javase/8/docs/api/java/util/Map.html?is-external=true)` attrList)`<br>Deprecated. <br>                       |
    | [`STRUCT`](../STRUCT.md)`(`[`StructDescriptor`](../StructDescriptor.md)` type, `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)`[] attributes)`<br>Deprecated. <br>Constructor. |
    | [`STRUCT`](../STRUCT.md)`(`[`StructDescriptor`](../StructDescriptor.md)` type, `[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)`[] attributes)`<br>Deprecated. <br>Constructor. |

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](../package-summary.md)
- [Class](../StructDescriptor.md)
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
