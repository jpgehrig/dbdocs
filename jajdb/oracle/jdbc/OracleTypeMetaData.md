Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleTypeMetaData.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleType.md)
- [Next Class](OracleTypeMetaData.Array.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.jdbc

## Interface OracleTypeMetaData

- All Known Subinterfaces:
  [OracleTypeMetaData.Array](OracleTypeMetaData.Array.md), [OracleTypeMetaData.Opaque](OracleTypeMetaData.Opaque.md), [OracleTypeMetaData.Struct](OracleTypeMetaData.Struct.md)

  <!-- -->

  All Known Implementing Classes:
  [ArrayDescriptor](../sql/ArrayDescriptor.md), [OpaqueDescriptor](../sql/OpaqueDescriptor.md), [StructDescriptor](../sql/StructDescriptor.md), [TypeDescriptor](../sql/TypeDescriptor.md)

  ------------------------------------------------------------------------



      public interface OracleTypeMetaData

  This extension defines methods for meta data describing Oracle specific Types. [`OracleArray`](OracleArray.md) replaces [`ARRAY`](../sql/ARRAY.md). [`OracleOpaque`](OracleOpaque.md) replaces [`OPAQUE`](../sql/OPAQUE.md). [`OracleStruct`](OracleStruct.md) replaces [`STRUCT`](../sql/STRUCT.md).
  Since:
  11.2.0.3.0

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type   | Interface and Description                                                                                                        |
    |---------------------|----------------------------------------------------------------------------------------------------------------------------------|
    | `static interface ` | [`OracleTypeMetaData.Array`](OracleTypeMetaData.Array.md)<br>This nested interfacet defines additional methods for array types   |
    | `static class `     | [`OracleTypeMetaData.ArrayStorage`](OracleTypeMetaData.ArrayStorage.md)<br>Identifies                                            |
    | `static class `     | [`OracleTypeMetaData.Kind`](OracleTypeMetaData.Kind.md)<br>Identifies the kind of named type.                                    |
    | `static interface ` | [`OracleTypeMetaData.Opaque`](OracleTypeMetaData.Opaque.md)<br>This nested interface defines additional methods for opaque types |
    | `static interface ` | [`OracleTypeMetaData.Struct`](OracleTypeMetaData.Struct.md)<br>This nested interface defines additional methods for struct types |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                               | Method and Description                               |
    |-------------------------------------------------------------------------------------------------|------------------------------------------------------|
    | [`OracleTypeMetaData.Kind`](OracleTypeMetaData.Kind.md)                                         | `getKind``()`<br>Return the kind of type.            |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getName``()`<br>Return fully qualified type name.   |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getSchemaName``()`<br>Return sql schema name.       |
    | `oracle.sql.SQLName`                                                                            | `getSQLName``()`<br>Fully parsed named               |
    | `int`                                                                                           | `getTypeCode``()`<br>Returns type code.              |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getTypeCodeName``()`<br>Returns the type code name. |

<!-- -->

- - ### Method Detail

    - #### getKind

          OracleTypeMetaData.Kind getKind()

      Return the kind of type.
      Returns:
      kind of type

    <!-- -->

    - #### getName

          String getName()
                  throws SQLException

      Return fully qualified type name.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getSQLName

          oracle.sql.SQLName getSQLName()
                                 throws SQLException

      Fully parsed named
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getSchemaName

          String getSchemaName()
                        throws SQLException

      Return sql schema name.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getTypeCode

          int getTypeCode()
                   throws SQLException

      Returns type code.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getTypeCodeName

          String getTypeCodeName()
                          throws SQLException

      Returns the type code name.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleTypeMetaData.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleType.md)
- [Next Class](OracleTypeMetaData.Array.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Copyright © 2008, 2022, Oracle and/or its affiliates.
