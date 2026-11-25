Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleResultSetMetaData.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleResultSet.AuthorizationIndicator.md)
- [Next Class](OracleResultSetMetaData.SecurityAttribute.md)

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

## Interface OracleResultSetMetaData

- All Superinterfaces:
  [ResultSetMetaData](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true), [Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true)

  <!-- -->

  All Known Subinterfaces:
  [StructMetaData](StructMetaData.md)

  ------------------------------------------------------------------------



      public interface OracleResultSetMetaData
      extends ResultSetMetaData

  An object that can be used to get information about the types and properties of the columns in a ResultSet object.

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Interface and Description                                                                                                                |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------|
    | `static class `   | [`OracleResultSetMetaData.SecurityAttribute`](OracleResultSetMetaData.SecurityAttribute.md)<br>eXtensible Data Security (XDS) attribute. |

  <!-- -->

  - ### Field Summary

    - ### Fields inherited from interface java.sql.[ResultSetMetaData](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true)

      [`columnNoNulls`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#columnNoNulls)`, `[`columnNullable`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#columnNullable)`, `[`columnNullableUnknown`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#columnNullableUnknown)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                           | Method and Description                                                                                                                                   |
    |---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OracleResultSetMetaData.SecurityAttribute`](OracleResultSetMetaData.SecurityAttribute.md) | `getSecurityAttribute``(int indexOfColumnInResultSet)`<br>Returns the eXtensible Data Security (XDS) attribute of this column.                           |
    | `boolean`                                                                                   | `isColumnInvisible``(int indexOfColumnInResultSet)`<br>Returns the column visibility information of the specified column.                                |
    | `boolean`                                                                                   | `isColumnJSON``(int column)`<br>Returns true if the specified column contains JSON data otherwise returns false.                                         |
    | `boolean`                                                                                   | `isNCHAR``(int index)`<br>isNCHAR (int)                                                                                                                  |
    | `boolean`                                                                                   | `isVariableScale``(int column)`<br>If the scale of Oracle NUMBER, FLOAT, DECIMAL and DOUBLE database datatype is unspecified this method returns `true`. |

    - ### Methods inherited from interface java.sql.[ResultSetMetaData](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true)

      [`getCatalogName`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#getCatalogName_int_)`, `[`getColumnClassName`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#getColumnClassName_int_)`, `[`getColumnCount`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#getColumnCount__)`, `[`getColumnDisplaySize`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#getColumnDisplaySize_int_)`, `[`getColumnLabel`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#getColumnLabel_int_)`, `[`getColumnName`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#getColumnName_int_)`, `[`getColumnType`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#getColumnType_int_)`, `[`getColumnTypeName`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#getColumnTypeName_int_)`, `[`getPrecision`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#getPrecision_int_)`, `[`getScale`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#getScale_int_)`, `[`getSchemaName`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#getSchemaName_int_)`, `[`getTableName`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#getTableName_int_)`, `[`isAutoIncrement`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#isAutoIncrement_int_)`, `[`isCaseSensitive`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#isCaseSensitive_int_)`, `[`isCurrency`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#isCurrency_int_)`, `[`isDefinitelyWritable`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#isDefinitelyWritable_int_)`, `[`isNullable`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#isNullable_int_)`, `[`isReadOnly`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#isReadOnly_int_)`, `[`isSearchable`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#isSearchable_int_)`, `[`isSigned`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#isSigned_int_)`, `[`isWritable`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSetMetaData.html?is-external=true#isWritable_int_)

    <!-- -->

    - ### Methods inherited from interface java.sql.[Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true)

      [`isWrapperFor`](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true#isWrapperFor_java_lang_Class_)`, `[`unwrap`](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true#unwrap_java_lang_Class_)

<!-- -->

- - ### Method Detail

    - #### isNCHAR

          boolean isNCHAR(int index)
                   throws SQLException

      isNCHAR (int)
      Parameters:
      `index` - the column index

      Returns:
      true if the column is of type NCHAR/NVARCHAR/NCLOB false if the column is not of type NCHAR/NVARCHAR/NCLOB

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getSecurityAttribute

          OracleResultSetMetaData.SecurityAttribute getSecurityAttribute(int indexOfColumnInResultSet)
                                                                  throws SQLException

      Returns the eXtensible Data Security (XDS) attribute of this column.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      See Also:
      `OracleResultSet.getAuthorizationIndicator`

    <!-- -->

    - #### isColumnInvisible

          boolean isColumnInvisible(int indexOfColumnInResultSet)
                             throws SQLException

      Returns the column visibility information of the specified column.
      An invisible column is a user defined/specified hidden column which can be later changed to visible. It is created as:

               create table test_tab (col1 integer invisibile, col2 integer);


      It can be modified later by using:
               alter table test_tab modify (col1 visible);


      Parameters:
      `indexOfColumnInResultSet` - the column index

      Returns:
      true if the column is invisible false if the column is not invisible

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### isVariableScale

          boolean isVariableScale(int column)
                           throws SQLException

      If the scale of Oracle NUMBER, FLOAT, DECIMAL and DOUBLE database datatype is unspecified this method returns `true`. Oracle database returns -127 if scale is unspecified.
      Parameters:
      `column` - the first column is 1, the second is 2, ...

      Returns:
      true if the column type has variable scale

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### isColumnJSON

          boolean isColumnJSON(int column)
                        throws SQLException

      Returns true if the specified column contains JSON data otherwise returns false.
      A columns that always contains JSON data is a textual (VARCHAR2 or CLOB) or binary (BLOB) table column with an IS JSON check constraint or a view column that has an underlyign JSON generation function .

      Parameters:
      `column` - the column index

      Returns:
      true if the column contains JSON data false if the column does not contan JSON data

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleResultSetMetaData.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleResultSet.AuthorizationIndicator.md)
- [Next Class](OracleResultSetMetaData.SecurityAttribute.md)

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
