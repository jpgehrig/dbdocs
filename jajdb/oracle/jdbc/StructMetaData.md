Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/StructMetaData.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleXAConnectionBuilder.md)
- Next Class

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

## Interface StructMetaData

- All Superinterfaces:
  [OracleResultSetMetaData](OracleResultSetMetaData.md), [ResultSetMetaData](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true), [Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true)

  ------------------------------------------------------------------------



      public interface StructMetaData
      extends OracleResultSetMetaData

  An interface to get information about structured column types.

<!-- -->

- - ### Nested Class Summary

    - ### Nested classes/interfaces inherited from interface oracle.jdbc.[OracleResultSetMetaData](OracleResultSetMetaData.md)

      [`OracleResultSetMetaData.SecurityAttribute`](OracleResultSetMetaData.SecurityAttribute.md)

  <!-- -->

  - ### Field Summary

    - ### Fields inherited from interface java.sql.[ResultSetMetaData](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true)

      [`columnNoNulls`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#columnNoNulls)`, `[`columnNullable`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#columnNullable)`, `[`columnNullableUnknown`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#columnNullableUnknown)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                               | Method and Description                                                                                                                                                                                                     |
    |-------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getAttributeJavaName``(int column)`<br>Gets a JAVA_STRUCT attribute's external name.                                                                                                                                      |
    | `int`                                                                                           | `getLocalColumnCount``()`<br>Get number of local attributes i.e.                                                                                                                                                           |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true) | `getOracleColumnClassName``(int column)`<br>Return the fully-qualified name of the Datum class whose instances are manufactured if the method OracleResultSet.getOracleObject is called to retrieve a value from a column. |
    | `boolean`                                                                                       | `isInherited``(int column)`<br>Indicates whether the attribute is inherited from its supertype.                                                                                                                            |

    - ### Methods inherited from interface oracle.jdbc.[OracleResultSetMetaData](OracleResultSetMetaData.md)

      [`getSecurityAttribute`](OracleResultSetMetaData.md)`, `[`isColumnInvisible`](OracleResultSetMetaData.md)`, `[`isColumnJSON`](OracleResultSetMetaData.md)`, `[`isNCHAR`](OracleResultSetMetaData.md)`, `[`isVariableScale`](OracleResultSetMetaData.md)

    <!-- -->

    - ### Methods inherited from interface java.sql.[ResultSetMetaData](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true)

      [`getCatalogName`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#getCatalogName_int_)`, `[`getColumnClassName`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#getColumnClassName_int_)`, `[`getColumnCount`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#getColumnCount__)`, `[`getColumnDisplaySize`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#getColumnDisplaySize_int_)`, `[`getColumnLabel`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#getColumnLabel_int_)`, `[`getColumnName`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#getColumnName_int_)`, `[`getColumnType`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#getColumnType_int_)`, `[`getColumnTypeName`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#getColumnTypeName_int_)`, `[`getPrecision`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#getPrecision_int_)`, `[`getScale`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#getScale_int_)`, `[`getSchemaName`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#getSchemaName_int_)`, `[`getTableName`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#getTableName_int_)`, `[`isAutoIncrement`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#isAutoIncrement_int_)`, `[`isCaseSensitive`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#isCaseSensitive_int_)`, `[`isCurrency`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#isCurrency_int_)`, `[`isDefinitelyWritable`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#isDefinitelyWritable_int_)`, `[`isNullable`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#isNullable_int_)`, `[`isReadOnly`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#isReadOnly_int_)`, `[`isSearchable`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#isSearchable_int_)`, `[`isSigned`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#isSigned_int_)`, `[`isWritable`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#isWritable_int_)

    <!-- -->

    - ### Methods inherited from interface java.sql.[Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true)

      [`isWrapperFor`](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true#isWrapperFor_java_lang_Class_)`, `[`unwrap`](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true#unwrap_java_lang_Class_)

<!-- -->

- - ### Method Detail

    - #### getAttributeJavaName

          String getAttributeJavaName(int column)
                               throws SQLException

      Gets a JAVA_STRUCT attribute's external name.
      Parameters:
      `column` - the first attribue is 1, the second is 2, ...

      Returns:
      attribute external name; return null if the attribute is not a attribute of a JAVA_STRUCT object.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      8.2.0

    <!-- -->

    - #### getOracleColumnClassName

          String getOracleColumnClassName(int column)
                                   throws SQLException

      Return the fully-qualified name of the Datum class whose instances are manufactured if the method OracleResultSet.getOracleObject is called to retrieve a value from a column.
      Parameters:
      `column` -

      Returns:
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### isInherited

          boolean isInherited(int column)
                       throws SQLException

      Indicates whether the attribute is inherited from its supertype.
      Parameters:
      `column` -

      Returns:
      true is the attribute is inherited from the object type's supertype(s). Returns false if the attribute is defined in the subtype.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      8.2.0

    <!-- -->

    - #### getLocalColumnCount

          int getLocalColumnCount()
                           throws SQLException

      Get number of local attributes i.e. not inherited from its supertype.
      Returns:
      number of local attribute.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      8.2.0

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/StructMetaData.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleXAConnectionBuilder.md)
- Next Class

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
