Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleRef.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OraclePreparedStatement.md)
- [Next Class](OracleResultSet.md)

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

## Interface OracleRef

- All Superinterfaces:
  [Ref](http://download.oracle.com/javase/8/docs/api/java/sql/Ref.html?is-external=true)

  <!-- -->

  All Known Implementing Classes:
  [REF](../sql/REF.md)

  ------------------------------------------------------------------------



      public interface OracleRef
      extends Ref

  This interface defines the Oracle extensions to the standard JDBC interface [`Ref`](http://download.oracle.com/javase/8/docs/api/java/sql/Ref.html?is-external=true).
  Generally any new code should avoid the direct use of the class [`REF`](../sql/REF.md). For variable declarations use the interface [`Ref`](http://download.oracle.com/javase/8/docs/api/java/sql/Ref.html?is-external=true) or this interface as required.

  Obtaining java.sql.Ref from ResultSet

  `java.sql.Ref ref = resultSet.getRef(...);`
  There is no way to create [`Ref`](http://download.oracle.com/javase/8/docs/api/java/sql/Ref.html?is-external=true) on the client side.

  Since:
  11.2.0.3

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                             | Method and Description                       |
    |-----------------------------------------------|----------------------------------------------|
    | [`OracleTypeMetaData`](OracleTypeMetaData.md) | `getOracleMetaData``()`<br>Oracle extension. |

    - ### Methods inherited from interface java.sql.[Ref](http://download.oracle.com/javase/8/docs/api/java/sql/Ref.html?is-external=true)

      [`getBaseTypeName`](http://download.oracle.com/javase/8/docs/api/java/sql/Ref.html?is-external=true#getBaseTypeName__)`, `[`getObject`](http://download.oracle.com/javase/8/docs/api/java/sql/Ref.html?is-external=true#getObject__)`, `[`getObject`](http://download.oracle.com/javase/8/docs/api/java/sql/Ref.html?is-external=true#getObject_java_util_Map_)`, `[`setObject`](http://download.oracle.com/javase/8/docs/api/java/sql/Ref.html?is-external=true#setObject_java_lang_Object_)

<!-- -->

- - ### Method Detail

    - #### getOracleMetaData

          OracleTypeMetaData getOracleMetaData()
                                        throws SQLException

      Oracle extension. Get the SQL REF type metadata for the type of this object.
      Returns:
      metadata for this object's type

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleRef.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OraclePreparedStatement.md)
- [Next Class](OracleResultSet.md)

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
