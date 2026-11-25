Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleTypeMetaData.Struct.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleTypeMetaData.Opaque.md)
- [Next Class](OracleTypes.md)

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

## Interface OracleTypeMetaData.Struct

- All Superinterfaces:
  [OracleTypeMetaData](OracleTypeMetaData.md)

  <!-- -->

  All Known Implementing Classes:
  [StructDescriptor](../sql/StructDescriptor.md)

  <!-- -->

  Enclosing interface:
  [OracleTypeMetaData](OracleTypeMetaData.md)

  ------------------------------------------------------------------------



      public static interface OracleTypeMetaData.Struct
      extends OracleTypeMetaData

  This nested interface defines additional methods for struct types

<!-- -->

- - ### Nested Class Summary

    - ### Nested classes/interfaces inherited from interface oracle.jdbc.[OracleTypeMetaData](OracleTypeMetaData.md)

      [`OracleTypeMetaData.Array`](OracleTypeMetaData.Array.md)`, `[`OracleTypeMetaData.ArrayStorage`](OracleTypeMetaData.ArrayStorage.md)`, `[`OracleTypeMetaData.Kind`](OracleTypeMetaData.Kind.md)`, `[`OracleTypeMetaData.Opaque`](OracleTypeMetaData.Opaque.md)`, OracleTypeMetaData.Struct`

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                                                    | Method and Description                                                                   |
    |----------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------|
    | `int`                                                                                                                | `getLength``()`<br>The number of fields in the Object Type.                              |
    | `int`                                                                                                                | `getLocalAttributeCount``()`<br>Returns the number of attributes defined in the subtype. |
    | [`ResultSetMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true) | `getMetaData``()`<br>Gets the metadata regarding this type.                              |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)`[]`                  | `getSubtypeNames``()`<br>Returns the SQL type names of the direct subtypes.              |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)                      | `getSupertypeName``()`<br>Returns the SQL type name of the direct subtype.               |
    | `int`                                                                                                                | `getTypeVersion``()`                                                                     |
    | `boolean`                                                                                                            | `isFinalType``()`<br>Indicates whether the object type is a final type.                  |
    | `boolean`                                                                                                            | `isInstantiable``()`<br>Indicates whether the object type is instantiable.               |
    | `boolean`                                                                                                            | `isSubtype``()`<br>Indicates whether the object type is a subtype.                       |

    - ### Methods inherited from interface oracle.jdbc.[OracleTypeMetaData](OracleTypeMetaData.md)

      [`getKind`](OracleTypeMetaData.md)`, `[`getName`](OracleTypeMetaData.md)`, `[`getSchemaName`](OracleTypeMetaData.md)`, `[`getSQLName`](OracleTypeMetaData.md)`, `[`getTypeCode`](OracleTypeMetaData.md)`, `[`getTypeCodeName`](OracleTypeMetaData.md)

<!-- -->

- - ### Method Detail

    - #### getTypeVersion

          int getTypeVersion()
                      throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getLength

          int getLength()
                 throws SQLException

      The number of fields in the Object Type.
      Returns:
      the size.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getMetaData

          ResultSetMetaData getMetaData()
                                 throws SQLException

      Gets the metadata regarding this type. The return ResultSetMetaData contains the attribute name, attribute type id and attribute type precision information. The column index in ResultSetMetaData maps to the position of the attribute in a Struct (with the first attribute being at index 1).
      Returns:
      a ResultSetMetaData object that contains the type info

      Throws:
      `if` - database access error occurs

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### isFinalType

          boolean isFinalType()
                       throws SQLException

      Indicates whether the object type is a final type.
      Returns:
      true if the object type is a final type and false otherwise.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### isSubtype

          boolean isSubtype()
                     throws SQLException

      Indicates whether the object type is a subtype.
      Returns:
      true if the object type is a subtype and false otherwise.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### isInstantiable

          boolean isInstantiable()
                          throws SQLException

      Indicates whether the object type is instantiable.
      Returns:
      true if the object type is instantiable and false otherwise.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getSupertypeName

          String getSupertypeName()
                           throws SQLException

      Returns the SQL type name of the direct subtype.
      Returns:
      the fully qualified name of the supertype. Returns null if the object type is not a subtype.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getLocalAttributeCount

          int getLocalAttributeCount()
                              throws SQLException

      Returns the number of attributes defined in the subtype.
      Returns:
      number of subtype attributes.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getSubtypeNames

          String[] getSubtypeNames()
                            throws SQLException

      Returns the SQL type names of the direct subtypes.
      Returns:
      the fully qualifed name of the direct subtypes. Returns an empty String array if there is no subtypes.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleTypeMetaData.Struct.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleTypeMetaData.Opaque.md)
- [Next Class](OracleTypes.md)

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
