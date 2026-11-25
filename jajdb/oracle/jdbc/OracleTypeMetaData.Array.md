Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleTypeMetaData.Array.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleTypeMetaData.md)
- [Next Class](OracleTypeMetaData.ArrayStorage.md)

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

## Interface OracleTypeMetaData.Array

- All Superinterfaces:
  [OracleTypeMetaData](OracleTypeMetaData.md)

  <!-- -->

  All Known Implementing Classes:
  [ArrayDescriptor](../sql/ArrayDescriptor.md)

  <!-- -->

  Enclosing interface:
  [OracleTypeMetaData](OracleTypeMetaData.md)

  ------------------------------------------------------------------------



      public static interface OracleTypeMetaData.Array
      extends OracleTypeMetaData

  This nested interfacet defines additional methods for array types

<!-- -->

- - ### Nested Class Summary

    - ### Nested classes/interfaces inherited from interface oracle.jdbc.[OracleTypeMetaData](OracleTypeMetaData.md)

      `OracleTypeMetaData.Array, `[`OracleTypeMetaData.ArrayStorage`](OracleTypeMetaData.ArrayStorage.md)`, `[`OracleTypeMetaData.Kind`](OracleTypeMetaData.Kind.md)`, `[`OracleTypeMetaData.Opaque`](OracleTypeMetaData.Opaque.md)`, `[`OracleTypeMetaData.Struct`](OracleTypeMetaData.Struct.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                               | Method and Description                                                                                                                            |
    |-------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OracleTypeMetaData.ArrayStorage`](OracleTypeMetaData.ArrayStorage.md)                         | `getArrayStorage``()`<br>Return the database type of the array.                                                                                   |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getBaseName``()`<br>In case the elements are named types the fully qualified name of their type.Otherwise, return type name used by the database |
    | `int`                                                                                           | `getBaseType``()`<br>Return element's type code.                                                                                                  |
    | `long`                                                                                          | `getMaxLength``()`<br>Return the maximun number of elements this array object can hold.                                                           |

    - ### Methods inherited from interface oracle.jdbc.[OracleTypeMetaData](OracleTypeMetaData.md)

      [`getKind`](OracleTypeMetaData.md)`, `[`getName`](OracleTypeMetaData.md)`, `[`getSchemaName`](OracleTypeMetaData.md)`, `[`getSQLName`](OracleTypeMetaData.md)`, `[`getTypeCode`](OracleTypeMetaData.md)`, `[`getTypeCodeName`](OracleTypeMetaData.md)

<!-- -->

- - ### Method Detail

    - #### getBaseType

          int getBaseType()
                   throws SQLException

      Return element's type code.
      Returns:
      the type code of elements of the array

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getBaseName

          String getBaseName()
                      throws SQLException

      In case the elements are named types the fully qualified name of their type.Otherwise, return type name used by the database
      Returns:
      the name of the base type.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the element's type is not named.

    <!-- -->

    - #### getArrayStorage

          OracleTypeMetaData.ArrayStorage getArrayStorage()
                                                   throws SQLException

      Return the database type of the array. The possible return values ArrayStorage.VARRAY and ArrayStorage.NESTED_TABLE.
      Returns:
      how the array is stored in the database

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getMaxLength

          long getMaxLength()
                     throws SQLException

      Return the maximun number of elements this array object can hold.
      Returns:
      the maximum array size; return 0 if no limit.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleTypeMetaData.Array.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleTypeMetaData.md)
- [Next Class](OracleTypeMetaData.ArrayStorage.md)

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
