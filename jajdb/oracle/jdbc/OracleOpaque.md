Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleOpaque.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleOCIFailover.md)
- [Next Class](OracleParameterMetaData.md)

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

## Interface OracleOpaque

- All Known Implementing Classes:
  [OPAQUE](../sql/OPAQUE.md)

  ------------------------------------------------------------------------



      public interface OracleOpaque

  This interface defines methods for Oracle specific Opaque.
  Opaque is an Oracle proprietary type and is opaque to the user.

  Since:
  11.2.0.3

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                               | Method and Description                                                                                                                                        |
    |-------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OracleTypeMetaData`](OracleTypeMetaData.md)                                                   | `getOracleMetaData``()`<br>Oracle extension.                                                                                                                  |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getSQLTypeName``()`<br>Implements the Struct interface function Retrieves the SQL type name of the SQL structured type that this `Struct` object represents. |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true) | `getValue``()`<br>Return the Opaque value.                                                                                                                    |

<!-- -->

- - ### Method Detail

    - #### getOracleMetaData

          OracleTypeMetaData getOracleMetaData()
                                        throws SQLException

      Oracle extension. Get the SQL OPAQUE type metadata for the type of this object.
      Returns:
      metadata for this object's type

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs

    <!-- -->

    - #### getSQLTypeName

          String getSQLTypeName()
                         throws SQLException

      Implements the Struct interface function Retrieves the SQL type name of the SQL structured type that this `Struct` object represents.
      Returns:
      the fully-qualified type name of the SQL structured type for which this `Struct` object is the generic representation

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### getValue

          Object getValue()
                   throws SQLException

      Return the Opaque value.
      Returns:
      a Java object that represents the opaque value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleOpaque.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleOCIFailover.md)
- [Next Class](OracleParameterMetaData.md)

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
