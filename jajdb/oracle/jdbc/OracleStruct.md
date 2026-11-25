Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleStruct.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleStatement.md)
- [Next Class](OracleTemporalField.md)

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

## Interface OracleStruct

- All Superinterfaces:
  [Struct](http://download.oracle.com/javase/8/docs/api/java/sql/Struct.html?is-external=true)

  <!-- -->

  All Known Implementing Classes:
  [JAVA_STRUCT](../sql/JAVA_STRUCT.md), [STRUCT](../sql/STRUCT.md)

  ------------------------------------------------------------------------



      public interface OracleStruct
      extends Struct

  This interface defines the Oracle extensions to the standard JDBC interface [`Struct`](http://download.oracle.com/javase/8/docs/api/java/sql/Struct.html?is-external=true).
  Generally any new code should avoid the direct use of the class [`STRUCT`](../sql/STRUCT.md). For variable declarations use the interface [`Struct`](http://download.oracle.com/javase/8/docs/api/java/sql/Struct.html?is-external=true) or this interface as required. For creating a new oracle.jdbc.OracleStruct use `java.sql.Connection#createStruct()`.

  Since:
  11.2.0.3

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                             | Method and Description                       |
    |-----------------------------------------------|----------------------------------------------|
    | [`OracleTypeMetaData`](OracleTypeMetaData.md) | `getOracleMetaData``()`<br>Oracle extension. |

    - ### Methods inherited from interface java.sql.[Struct](http://download.oracle.com/javase/8/docs/api/java/sql/Struct.html?is-external=true)

      [`getAttributes`](http://download.oracle.com/javase/8/docs/api/java/sql/Struct.html?is-external=true#getAttributes__)`, `[`getAttributes`](http://download.oracle.com/javase/8/docs/api/java/sql/Struct.html?is-external=true#getAttributes_java_util_Map_)`, `[`getSQLTypeName`](http://download.oracle.com/javase/8/docs/api/java/sql/Struct.html?is-external=true#getSQLTypeName__)

<!-- -->

- - ### Method Detail

    - #### getOracleMetaData

          OracleTypeMetaData getOracleMetaData()
                                        throws SQLException

      Oracle extension. Get the SQL STRUCT type metadata for the type of this object.
      Returns:
      metadata for this object's type

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleStruct.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleStatement.md)
- [Next Class](OracleTemporalField.md)

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
