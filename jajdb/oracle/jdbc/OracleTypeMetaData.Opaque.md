Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleTypeMetaData.Opaque.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleTypeMetaData.Kind.md)
- [Next Class](OracleTypeMetaData.Struct.md)

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

## Interface OracleTypeMetaData.Opaque

- All Superinterfaces:
  [OracleTypeMetaData](OracleTypeMetaData.md)

  <!-- -->

  All Known Implementing Classes:
  [OpaqueDescriptor](../sql/OpaqueDescriptor.md)

  <!-- -->

  Enclosing interface:
  [OracleTypeMetaData](OracleTypeMetaData.md)

  ------------------------------------------------------------------------



      public static interface OracleTypeMetaData.Opaque
      extends OracleTypeMetaData

  This nested interface defines additional methods for opaque types

<!-- -->

- - ### Nested Class Summary

    - ### Nested classes/interfaces inherited from interface oracle.jdbc.[OracleTypeMetaData](OracleTypeMetaData.md)

      [`OracleTypeMetaData.Array`](OracleTypeMetaData.Array.md)`, `[`OracleTypeMetaData.ArrayStorage`](OracleTypeMetaData.ArrayStorage.md)`, `[`OracleTypeMetaData.Kind`](OracleTypeMetaData.Kind.md)`, OracleTypeMetaData.Opaque, `[`OracleTypeMetaData.Struct`](OracleTypeMetaData.Struct.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                            |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------------|
    | `long`            | `getMaxLength``()`<br>Return the maximun number of bytes this opaque object can hold.                                             |
    | `boolean`         | `hasFixedSize``()`<br>Indicates whether the Opaque type has fixed size.                                                           |
    | `boolean`         | `hasUnboundedSize``()`<br>Indicates whether the Opaque type has unbounded size ().                                                |
    | `boolean`         | `isModeledInC``()`<br>Indicates whether the Opaque type is modelled in C language.                                                |
    | `boolean`         | `isTrustedLibrary``()`<br>Indicates whether the Trusted Library implementing Support functions are specified for the Opaque type. |

    - ### Methods inherited from interface oracle.jdbc.[OracleTypeMetaData](OracleTypeMetaData.md)

      [`getKind`](OracleTypeMetaData.md)`, `[`getName`](OracleTypeMetaData.md)`, `[`getSchemaName`](OracleTypeMetaData.md)`, `[`getSQLName`](OracleTypeMetaData.md)`, `[`getTypeCode`](OracleTypeMetaData.md)`, `[`getTypeCodeName`](OracleTypeMetaData.md)

<!-- -->

- - ### Method Detail

    - #### getMaxLength

          long getMaxLength()
                     throws SQLException

      Return the maximun number of bytes this opaque object can hold.
      Returns:
      the maximum opaque size; return 0 if unbounded.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### isTrustedLibrary

          boolean isTrustedLibrary()
                            throws SQLException

      Indicates whether the Trusted Library implementing Support functions are specified for the Opaque type. This is the case for internal Opaque Types that are modeled in C.
      Returns:
      true if the Trusted Library implementing Support functions are specified; false, otherwise.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### isModeledInC

          boolean isModeledInC()
                        throws SQLException

      Indicates whether the Opaque type is modelled in C language.
      Returns:
      true if the Opaque type is modelled in C language; false, otherwise.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### hasUnboundedSize

          boolean hasUnboundedSize()
                            throws SQLException

      Indicates whether the Opaque type has unbounded size ().
      Returns:
      true if the Opaque type hsa unbounded size; false, otherwise.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### hasFixedSize

          boolean hasFixedSize()
                        throws SQLException

      Indicates whether the Opaque type has fixed size.
      Returns:
      true if the Opaque type has fixed size; false, otherwise.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleTypeMetaData.Opaque.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleTypeMetaData.Kind.md)
- [Next Class](OracleTypeMetaData.Struct.md)

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
