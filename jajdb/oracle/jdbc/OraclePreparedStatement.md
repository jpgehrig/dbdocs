Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OraclePreparedStatement.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OraclePooledConnectionBuilder.md)
- [Next Class](OracleRef.md)

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

## Interface OraclePreparedStatement

- All Superinterfaces:
  [AutoCloseable](http://download.oracle.com/javase/8/docs/api/java/lang/AutoCloseable.html?is-external=true), [OracleStatement](OracleStatement.md), [PreparedStatement](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true), [Statement](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true), [Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true)

  <!-- -->

  All Known Subinterfaces:
  [OracleCallableStatement](OracleCallableStatement.md)

  ------------------------------------------------------------------------



      public interface OraclePreparedStatement
      extends PreparedStatement, OracleStatement

  This interface defines the Oracle extensions to the standard JDBC interface `java.sql.PreparedStatement`. You can use `java.sql.PreparedStatement` in your application where you do not make use of the Oracle extensions. However, when your application uses the Oracle extensions to `java.sql.PreparedStatement` you must cast your prepared statement object to the type `oracle.jdbc.OraclePreparedStatement`. Although the type by which the java compiler will identify the statement object is changed, the object itself is unchanged.
  Extended functionality consists of `setXXX()` methods for binding `oracle.sql.` types and objects into prepared statements, and methods to support Oracle performance extensions on a statement-by-statements basis.

  **About prepared statements** : To write changes to the database, such as for `INSERT` or `UPDATE` operations, you will typically create a `PreparedStatement` object. This allows you to execute a statement with varying sets of input parameters. The `prepareStatement()` method of your JDBC `Connection` object allows you to define a statement that takes variable bind parameters, and returns a JDBC `PreparedStatement` object with your statement definition.

  **Bind your data** : Use `setXXX()` methods on the `PreparedStatement` object to bind data into the prepared statement to be sent to the database. Again, some of these methods are Oracle specific and require that you cast your `PreparedStatement` object to the `OraclePreparedStatement` type.

  For example, if you have a `Connection` object named `conn` and a RAW named `my_raw`, then write the RAW to the database as follows:

        PreparedStatement ps = conn.prepareStatement
        ("INSERT INTO raw_table VALUES(?)");
        ((OraclePreparedStatement)ps).setRAW(1, my_raw);
        ps.execute();


  Since:
  8.1.7

  See Also:
  `Connection.prepareStatement`

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                                                             |
    |-------------------|---------------------------------------------------------------------------------------------------|
    | `static short`    | `FORM_CHAR`<br>Specifies the "form of use" for SQL CHAR datatypes (CHAR, VARCHAR2 and CLOB).      |
    | `static short`    | `FORM_NCHAR`<br>Specifies the "form of use" for SQL NCHAR datatypes (NCHAR, NVARCHAR2 and NCLOB). |

    - ### Fields inherited from interface oracle.jdbc.[OracleStatement](OracleStatement.md)

      [`EXPLICIT`](OracleStatement.md)`, `[`IMPLICIT`](OracleStatement.md)`, `[`NEW`](OracleStatement.md)

    <!-- -->

    - ### Fields inherited from interface java.sql.[Statement](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true)

      [`CLOSE_ALL_RESULTS`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#CLOSE_ALL_RESULTS)`, `[`CLOSE_CURRENT_RESULT`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#CLOSE_CURRENT_RESULT)`, `[`EXECUTE_FAILED`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#EXECUTE_FAILED)`, `[`KEEP_CURRENT_RESULT`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#KEEP_CURRENT_RESULT)`, `[`NO_GENERATED_KEYS`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#NO_GENERATED_KEYS)`, `[`RETURN_GENERATED_KEYS`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#RETURN_GENERATED_KEYS)`, `[`SUCCESS_NO_INFO`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#SUCCESS_NO_INFO)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                                                    | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                       |
    |------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                                               | `defineParameterType``(int param_index, int type, int max_size)`<br>Define the type under which you will bind the parameter and the maximum size (in characters) of data you will bind in binds.                                                                                                                                                                                                                             |
    | `void`                                                                                               | `defineParameterTypeBytes``(int param_index, int type, int max_size)`<br>Define the type under which you will bind the parameter and the maximum size (in bytes) of data you will bind in binds.                                                                                                                                                                                                                             |
    | `void`                                                                                               | `defineParameterTypeChars``(int param_index, int type, int max_size)`<br>Define the type under which you will bind the parameter and the maximum size (in characters) of data you will bind in binds.                                                                                                                                                                                                                        |
    | `int`                                                                                                | `getExecuteBatch``()`<br>Deprecated. <br>As of 12.1 all APIs related to oracle-style statement batching are deprecated in favor of standard JDBC batching. We recommend using the standard model going forward as it is spec compliant and provides more information and control to the application.                                                                                                                         |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true) | `getReturnResultSet``()`<br>Returns result set that contains data returned from DML Returning.                                                                                                                                                                                                                                                                                                                               |
    | [`OracleParameterMetaData`](OracleParameterMetaData.md)                                              | `OracleGetParameterMetaData``()`<br>Retrieves the number, types and properties of this `PreparedStatement` object's parameters.                                                                                                                                                                                                                                                                                              |
    | `void`                                                                                               | `registerReturnParameter``(int paramIndex, int externalType)`<br>Registers return parameter for DML Returning.                                                                                                                                                                                                                                                                                                               |
    | `void`                                                                                               | `registerReturnParameter``(int paramIndex, int externalType, int maxSize)`<br>Registers return parameter for DML Returning.                                                                                                                                                                                                                                                                                                  |
    | `void`                                                                                               | `registerReturnParameter``(int paramIndex, int externalType, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` typeName)`<br>Registers return parameter for DML Returning.                                                                                                                                                                                                   |
    | `int`                                                                                                | `sendBatch``()`<br>Deprecated. <br>As of 12.1 all APIs related to oracle-style statement batching are deprecated in favor of standard JDBC batching. We recommend using the standard model going forward as it is spec compliant and provides more information and control to the application.                                                                                                                               |
    | `void`                                                                                               | `setARRAY``(int parameterIndex, `[`ARRAY`](../sql/ARRAY.md)` arr)`<br>Binds the designated parameter to a `oracle.sql.ARRAY`.                                                                                                                                                                                                                                                                                                |
    | `void`                                                                                               | `setArrayAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Array`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true)` value)`<br>Sets the designated parameter to a Java Array value.                                                                                                                            |
    | `void`                                                                                               | `setARRAYAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`ARRAY`](../sql/ARRAY.md)` value)`<br>Sets the designated parameter to a `oracle.sql.ARRAY` value.                                                                                                                                                                                      |
    | `void`                                                                                               | `setAsciiStreamAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` stream)`<br>Sets the designated parameter to a Java AsciiStream value.                                                                                                    |
    | `void`                                                                                               | `setAsciiStreamAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` stream, int length)`<br>Sets the designated parameter to a Java AsciiStream value.                                                                                        |
    | `void`                                                                                               | `setAsciiStreamAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` stream, long length)`<br>Sets the designated parameter to a Java AsciiStream value.                                                                                       |
    | `void`                                                                                               | `setBfile``(int parameterIndex, `[`BFILE`](../sql/BFILE.md)` file)`<br>Binds the designated parameter to a `oracle.sql.BFILE` value.                                                                                                                                                                                                                                                                                         |
    | `void`                                                                                               | `setBFILE``(int parameterIndex, `[`BFILE`](../sql/BFILE.md)` file)`<br>Binds the designated parameter to a `oracle.sql.BFILE` value.                                                                                                                                                                                                                                                                                         |
    | `void`                                                                                               | `setBfileAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`BFILE`](../sql/BFILE.md)` value)`<br>Sets the designated parameter to a `oracle.sql.BFILE`value.                                                                                                                                                                                       |
    | `void`                                                                                               | `setBFILEAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`BFILE`](../sql/BFILE.md)` value)`<br>Sets the designated parameter to a `oracle.sql.BFILE`value.                                                                                                                                                                                       |
    | `void`                                                                                               | `setBigDecimalAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`BigDecimal`](http://download.oracle.com/javase/8/docs/api/java/math/BigDecimal.html?is-external=true)` value)`<br>Sets the designated parameter to a Java BigDecimal value.                                                                                                       |
    | `void`                                                                                               | `setBinaryDouble``(int parameterIndex, `[`BINARY_DOUBLE`](../sql/BINARY_DOUBLE.md)` value)`<br>Sets the designated parameter to an oracle.sql.BINARY_DOUBLE value.                                                                                                                                                                                                                                                           |
    | `void`                                                                                               | `setBinaryDouble``(int parameterIndex, double value)`<br>Sets the designated parameter to a Java double value.                                                                                                                                                                                                                                                                                                               |
    | `void`                                                                                               | `setBinaryDoubleAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`BINARY_DOUBLE`](../sql/BINARY_DOUBLE.md)` value)`<br>Sets the designated parameter to an oracle.sql.BINARY_DOUBLE value.                                                                                                                                                        |
    | `void`                                                                                               | `setBinaryDoubleAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, double value)`<br>Sets the designated parameter to a Java Double value.                                                                                                                                                                                                            |
    | `void`                                                                                               | `setBinaryFloat``(int parameterIndex, `[`BINARY_FLOAT`](../sql/BINARY_FLOAT.md)` value)`<br>Sets the designated parameter to an oracle.sql.BINARY_FLOAT value.                                                                                                                                                                                                                                                               |
    | `void`                                                                                               | `setBinaryFloat``(int parameterIndex, float value)`<br>Sets the designated parameter to a Java float value.                                                                                                                                                                                                                                                                                                                  |
    | `void`                                                                                               | `setBinaryFloatAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`BINARY_FLOAT`](../sql/BINARY_FLOAT.md)` value)`<br>Sets the designated parameter to an oracle.sql.BINARY_FLOAT value.                                                                                                                                                            |
    | `void`                                                                                               | `setBinaryFloatAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, float value)`<br>Sets the designated parameter to a Java Float value.                                                                                                                                                                                                               |
    | `void`                                                                                               | `setBinaryStreamAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` stream)`<br>Sets the designated parameter to a Java BinaryStream value.                                                                                                  |
    | `void`                                                                                               | `setBinaryStreamAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` stream, int length)`<br>Sets the designated parameter to a Java BinaryStream value.                                                                                      |
    | `void`                                                                                               | `setBinaryStreamAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` stream, long length)`<br>Sets the designated parameter to a Java BinaryStream value.                                                                                     |
    | `void`                                                                                               | `setBLOB``(int parameterIndex, `[`BLOB`](../sql/BLOB.md)` lob)`<br>Binds the designated parameter to a `oracle.sql.BLOB` value.                                                                                                                                                                                                                                                                                              |
    | `void`                                                                                               | `setBlobAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Blob`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true)` value)`<br>Sets the designated parameter to a Java Blob value.                                                                                                                                |
    | `void`                                                                                               | `setBLOBAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`BLOB`](../sql/BLOB.md)` value)`<br>Sets the designated parameter to an oracle.sql.BLOB value.                                                                                                                                                                                           |
    | `void`                                                                                               | `setBlobAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` stream)`<br>Sets the designated parameter to a stream value.                                                                                                                     |
    | `void`                                                                                               | `setBlobAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` stream, long length)`<br>Sets the designated parameter to a stream value.                                                                                                        |
    | `void`                                                                                               | `setBooleanAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, boolean value)`<br>Sets the designated parameter to a Java Boolean value.                                                                                                                                                                                                               |
    | `void`                                                                                               | `setByteAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, byte value)`<br>Sets the designated parameter to a Java Byte value.                                                                                                                                                                                                                        |
    | `void`                                                                                               | `setBytesAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, byte[] value)`<br>Sets the designated parameter to a Java Bytes value.                                                                                                                                                                                                                    |
    | `void`                                                                                               | `setBytesForBlob``(int parameterIndex, byte[] value)`<br>Sets the designated parameter to a Java bytes value.                                                                                                                                                                                                                                                                                                                |
    | `void`                                                                                               | `setBytesForBlobAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, byte[] value)`<br>Sets the designated parameter to a Java byte array value.                                                                                                                                                                                                        |
    | `void`                                                                                               | `setCHAR``(int parameterIndex, `[`CHAR`](../sql/CHAR.md)` ch)`<br>Binds the designated parameter to a `oracle.sql.CHAR` value.                                                                                                                                                                                                                                                                                               |
    | `void`                                                                                               | `setCharacterStreamAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Reader`](http://download.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)` reader)`<br>Sets the designated parameter to a Java CharacterStream value.                                                                                                      |
    | `void`                                                                                               | `setCharacterStreamAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Reader`](http://download.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)` reader, long length)`<br>Sets the designated parameter to a Java CharacterStream value.                                                                                         |
    | `void`                                                                                               | `setCHARAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`CHAR`](../sql/CHAR.md)` value)`<br>Sets the designated parameter to an oracle.sql.CHAR value.                                                                                                                                                                                           |
    | `void`                                                                                               | `setCheckBindTypes``(boolean flag)`<br>Enable/disable bind type checking.                                                                                                                                                                                                                                                                                                                                                    |
    | `void`                                                                                               | `setCLOB``(int parameterIndex, `[`CLOB`](../sql/CLOB.md)` lob)`<br>Binds the designated parameter to a `oracle.sql.CLOB` value.                                                                                                                                                                                                                                                                                              |
    | `void`                                                                                               | `setClobAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Clob`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true)` value)`<br>Sets the designated parameter to a Java Clob value.                                                                                                                                |
    | `void`                                                                                               | `setCLOBAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`CLOB`](../sql/CLOB.md)` value)`<br>Sets the designated parameter to an oracle.sql.CLOB value.                                                                                                                                                                                           |
    | `void`                                                                                               | `setClobAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Reader`](http://download.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)` reader)`<br>Sets the designated parameter to a stream value.                                                                                                                               |
    | `void`                                                                                               | `setClobAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Reader`](http://download.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)` reader, long length)`<br>Sets the designated parameter to a stream value.                                                                                                                  |
    | `void`                                                                                               | `setCursor``(int parameterIndex, `[`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true)` rs)`<br>Deprecated.                                                                                                                                                                                                                                                                  |
    | `void`                                                                                               | `setCursorAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true)` value)`<br>Sets the designated parameter to a Java Cursor value.                                                                                                                  |
    | `void`                                                                                               | `setCustomDatum``(int parameterIndex, `[`CustomDatum`](../sql/CustomDatum.md)` x)`<br>Deprecated.                                                                                                                                                                                                                                                                                                                            |
    | `void`                                                                                               | `setCustomDatumAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`CustomDatum`](../sql/CustomDatum.md)` value)`<br>Sets the designated parameter to a Java CustomDatum value.                                                                                                                                                                      |
    | `void`                                                                                               | `setDATE``(int parameterIndex, `[`DATE`](../sql/DATE.md)` date)`<br>Binds the designated parameter to a `oracle.sql.DATE` value.                                                                                                                                                                                                                                                                                             |
    | `void`                                                                                               | `setDateAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)` value)`<br>Sets the designated parameter to a Java Date value.                                                                                                                                |
    | `void`                                                                                               | `setDATEAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`DATE`](../sql/DATE.md)` value)`<br>Sets the designated parameter to an oracle.sql.DATE value.                                                                                                                                                                                           |
    | `void`                                                                                               | `setDateAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)` value, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Sets the designated parameter to a Java Date value.                     |
    | `void`                                                                                               | `setDisableStmtCaching``(boolean cache)`<br>Don't Cache this object even when the corresponding Connection is Cache Enabled.                                                                                                                                                                                                                                                                                                 |
    | `void`                                                                                               | `setDoubleAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, double value)`<br>Sets the designated parameter to a Java Double value.                                                                                                                                                                                                                  |
    | `void`                                                                                               | `setExecuteBatch``(int batchValue)`<br>Deprecated. <br>As of 12.1 all APIs related to oracle-style statement batching are deprecated in favor of standard JDBC batching. We recommend using the standard model going forward as it is spec compliant and provides more information and control to the application.                                                                                                           |
    | `void`                                                                                               | `setFixedCHAR``(int parameterIndex, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` x)`<br>Sets the disignated parameter to a `String` and executes a non-padded comparison with a SQL CHAR.                                                                                                                                                                               |
    | `void`                                                                                               | `setFixedCHARAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` value)`<br>Sets the designated parameter to a Java FixedCHAR value.                                                                                                                 |
    | `void`                                                                                               | `setFloatAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, float value)`<br>Sets the designated parameter to a Java Float value.                                                                                                                                                                                                                     |
    | `void`                                                                                               | `setFormOfUse``(int parameterIndex, short formOfUse)`<br>Specifies if the data is bound for a SQL NCHAR datatype.                                                                                                                                                                                                                                                                                                            |
    | `void`                                                                                               | `setIntAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, int value)`<br>Sets the designated parameter to a Java Int value.                                                                                                                                                                                                                           |
    | `void`                                                                                               | `setINTERVALDS``(int parameterIndex, `[`INTERVALDS`](../sql/INTERVALDS.md)` x)`<br>Binds the designated parameter to an oracle.sql.INTERVALDS value.                                                                                                                                                                                                                                                                         |
    | `void`                                                                                               | `setINTERVALDSAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`INTERVALDS`](../sql/INTERVALDS.md)` value)`<br>Sets the designated parameter to an oracle.sql.INTERVALDS value.                                                                                                                                                                   |
    | `void`                                                                                               | `setINTERVALYM``(int parameterIndex, `[`INTERVALYM`](../sql/INTERVALYM.md)` x)`<br>Binds the designated parameter to an oracle.sql.INTERVALYM value.                                                                                                                                                                                                                                                                         |
    | `void`                                                                                               | `setINTERVALYMAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`INTERVALYM`](../sql/INTERVALYM.md)` value)`<br>Sets the designated parameter to an oracle.sql.INTERVALYM value.                                                                                                                                                                   |
    | `void`                                                                                               | `setLongAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, long value)`<br>Sets the designated parameter to a Java Long value.                                                                                                                                                                                                                        |
    | `void`                                                                                               | `setNCharacterStreamAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Reader`](http://download.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)` reader)`<br>Sets the designated parameter to a Java CharacterStream value using the NCHAR character set.                                                                       |
    | `void`                                                                                               | `setNCharacterStreamAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Reader`](http://download.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)` reader, long length)`<br>Sets the designated parameter to a Java CharacterStream value using the NCHAR character set.                                                          |
    | `void`                                                                                               | `setNClobAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`NClob`](http://download.oracle.com/javase/8/docs/api/java/sql/NClob.html?is-external=true)` value)`<br>Sets the designated parameter to a `java.sql.NClob`value.                                                                                                                       |
    | `void`                                                                                               | `setNClobAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Reader`](http://download.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)` reader)`<br>Sets the designated parameter to a `java.sql.NClob`value.                                                                                                                     |
    | `void`                                                                                               | `setNClobAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Reader`](http://download.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)` reader, long length)`<br>Sets the designated parameter to a `java.sql.NClob`value.                                                                                                        |
    | `void`                                                                                               | `setNStringAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` value)`<br>Sets the designated parameter to a `java.sql.String`value using the NCHAR character set                                                                                    |
    | `void`                                                                                               | `setNullAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, int sqlType)`<br>Sets the designated parameter to a SQL NULL value.                                                                                                                                                                                                                        |
    | `void`                                                                                               | `setNullAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, int sqlType, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` sqlName)`<br>Sets the designated parameter to a SQL NULL value.                                                                                                             |
    | `void`                                                                                               | `setNUMBER``(int parameterIndex, `[`NUMBER`](../sql/NUMBER.md)` num)`<br>Binds the designated parameter to a `oracle.sql.NUMBER` value.                                                                                                                                                                                                                                                                                      |
    | `void`                                                                                               | `setNUMBERAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`NUMBER`](../sql/NUMBER.md)` value)`<br>Sets the designated parameter to an `oracle.sql.NUMBER` value.                                                                                                                                                                                 |
    | `void`                                                                                               | `setObjectAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` value)`<br>Sets the designated parameter to a Java Object value.                                                                                                                       |
    | `void`                                                                                               | `setObjectAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` value, int targetSqlType)`<br>Sets the designated parameter to a Java Object value.                                                                                                    |
    | `void`                                                                                               | `setObjectAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` value, int targetSqlType, int scale)`<br>Sets the designated parameter to a Java Object value.                                                                                         |
    | `void`                                                                                               | `setOPAQUE``(int parameterIndex, `[`OPAQUE`](../sql/OPAQUE.md)` val)`<br>Binds the designated parameter to a `oracle.sql.OPAQUE` value.                                                                                                                                                                                                                                                                                      |
    | `void`                                                                                               | `setOPAQUEAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`OPAQUE`](../sql/OPAQUE.md)` value)`<br>Sets the designated parameter to an `oracle.sql.OPAQUE`value.                                                                                                                                                                                  |
    | `void`                                                                                               | `setOracleObject``(int parameterIndex, `[`Datum`](../sql/Datum.md)` x)`<br>Binds the designated parameter to a `oracle.sql.Datum` value.                                                                                                                                                                                                                                                                                     |
    | `void`                                                                                               | `setOracleObjectAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Datum`](../sql/Datum.md)` value)`<br>Sets the designated parameter to an `oracle.sql.Datum`value.                                                                                                                                                                               |
    | `void`                                                                                               | `setORAData``(int parameterIndex, `[`ORAData`](../sql/ORAData.md)` x)`<br>Binds the designated parameter to a `oracle.sql.ORAData` value.                                                                                                                                                                                                                                                                                    |
    | `void`                                                                                               | `setORADataAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`ORAData`](../sql/ORAData.md)` value)`<br>Sets the designated parameter to an `oracle.sql.ORAData`value.                                                                                                                                                                              |
    | `void`                                                                                               | `setPlsqlIndexTable``(int parameterIndex, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` arrayData, int maxLen, int curLen, int elemSqlType, int elemMaxLen)`<br>Deprecated. <br>since 18.1. Use java.sql.PreparedStatement.setObject(int parameterIndex, Object x).                                                                                                      |
    | `void`                                                                                               | `setRAW``(int parameterIndex, `[`RAW`](../sql/RAW.md)` raw)`<br>Binds the designated parameter to a `oracle.sql.RAW` value.                                                                                                                                                                                                                                                                                                  |
    | `void`                                                                                               | `setRAWAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`RAW`](../sql/RAW.md)` value)`<br>Sets the designated parameter to an `oracle.sql.RAW`value.                                                                                                                                                                                              |
    | `void`                                                                                               | `setREF``(int parameterIndex, `[`REF`](../sql/REF.md)` ref)`<br>Binds the designated parameter to a `oracle.sql.REF` value.                                                                                                                                                                                                                                                                                                  |
    | `void`                                                                                               | `setRefAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Ref`](http://download.oracle.com/javase/8/docs/api/java/sql/Ref.html?is-external=true)` value)`<br>Sets the designated parameter to a Java Ref value.                                                                                                                                    |
    | `void`                                                                                               | `setREFAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`REF`](../sql/REF.md)` value)`<br>Sets the designated parameter to an `oracle.sql.REF`value.                                                                                                                                                                                              |
    | `void`                                                                                               | `setRefType``(int parameterIndex, `[`REF`](../sql/REF.md)` ref)`<br>Binds the designated parameter to a `oracle.sql.REF` value.                                                                                                                                                                                                                                                                                              |
    | `void`                                                                                               | `setRefTypeAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`REF`](../sql/REF.md)` value)`<br>Sets the designated parameter to an `oracle.sql.REF`value.                                                                                                                                                                                          |
    | `void`                                                                                               | `setROWID``(int parameterIndex, `[`ROWID`](../sql/ROWID.md)` rowid)`<br>Binds the designated parameter to a `oracle.sql.ROWID` value.                                                                                                                                                                                                                                                                                        |
    | `void`                                                                                               | `setRowIdAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`RowId`](http://download.oracle.com/javase/8/docs/api/java/sql/RowId.html?is-external=true)` value)`<br>Sets the designated parameter to a `java.sql.RowId`value.                                                                                                                       |
    | `void`                                                                                               | `setROWIDAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`ROWID`](../sql/ROWID.md)` value)`<br>Sets the designated parameter to an `oracle.sql.ROWID`value.                                                                                                                                                                                      |
    | `void`                                                                                               | `setShortAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, short value)`<br>Sets the designated parameter to a Java Short value.                                                                                                                                                                                                                     |
    | `void`                                                                                               | `setSQLXMLAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`SQLXML`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLXML.html?is-external=true)` value)`<br>Sets the designated parameter to a `java.sql.SQLXML`value.                                                                                                                   |
    | `void`                                                                                               | `setStringAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` value)`<br>Sets the designated parameter to a Java String value.                                                                                                                       |
    | `void`                                                                                               | `setStringForClob``(int parameterIndex, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` value)`<br>Sets the designated parameter to a Java String value.                                                                                                                                                                                                                   |
    | `void`                                                                                               | `setStringForClobAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` value)`<br>Sets the designated parameter to a Java String value.                                                                                                                |
    | `void`                                                                                               | `setSTRUCT``(int parameterIndex, `[`STRUCT`](../sql/STRUCT.md)` struct)`<br>Binds the designated parameter to a `oracle.sql.STRUCT` value.                                                                                                                                                                                                                                                                                   |
    | `void`                                                                                               | `setSTRUCTAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`STRUCT`](../sql/STRUCT.md)` value)`<br>Sets the designated parameter to an `oracle.sql.STRUCT`value.                                                                                                                                                                                  |
    | `void`                                                                                               | `setStructDescriptor``(int parameterIndex, `[`StructDescriptor`](../sql/StructDescriptor.md)` desc)`<br>Binds the bind type of designated parameter from an oracle.sql.StructDescriptor.                                                                                                                                                                                                                                     |
    | `void`                                                                                               | `setStructDescriptorAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`StructDescriptor`](../sql/StructDescriptor.md)` desc)`<br>Sets the designated parameter to an `oracle.sql.StructDescriptor` value.                                                                                                                                          |
    | `void`                                                                                               | `setTimeAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)` value)`<br>Sets the designated parameter to a Java Time value.                                                                                                                                |
    | `void`                                                                                               | `setTimeAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)` value, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Sets the designated parameter to a Java Time value.                     |
    | `void`                                                                                               | `setTIMESTAMP``(int parameterIndex, `[`TIMESTAMP`](../sql/TIMESTAMP.md)` x)`<br>Binds the designated parameter to an oracle.sql.TIMESTAMP value.                                                                                                                                                                                                                                                                             |
    | `void`                                                                                               | `setTimestampAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` value)`<br>Sets the designated parameter to a Java Timestamp value.                                                                                                            |
    | `void`                                                                                               | `setTIMESTAMPAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`TIMESTAMP`](../sql/TIMESTAMP.md)` value)`<br>Sets the designated parameter to an `oracle.sql.TIMESTAMP` value.                                                                                                                                                                     |
    | `void`                                                                                               | `setTimestampAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` value, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Sets the designated parameter to a Java Timestamp value. |
    | `void`                                                                                               | `setTIMESTAMPLTZ``(int parameterIndex, `[`TIMESTAMPLTZ`](../sql/TIMESTAMPLTZ.md)` x)`<br>Binds the designated parameter to an `oracle.sql.TIMESTAMPLTZ` value.                                                                                                                                                                                                                                                               |
    | `void`                                                                                               | `setTIMESTAMPLTZAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`TIMESTAMPLTZ`](../sql/TIMESTAMPLTZ.md)` value)`<br>Sets the designated parameter to an `oracle.sql.TIMESTAMPLTZ` value.                                                                                                                                                         |
    | `void`                                                                                               | `setTIMESTAMPTZ``(int parameterIndex, `[`TIMESTAMPTZ`](../sql/TIMESTAMPTZ.md)` x)`<br>Binds the designated parameter to an `oracle.sql.TIMESTAMPTZ` value.                                                                                                                                                                                                                                                                   |
    | `void`                                                                                               | `setTIMESTAMPTZAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`TIMESTAMPTZ`](../sql/TIMESTAMPTZ.md)` value)`<br>Sets the designated parameter to an `oracle.sql.TIMESTAMPTZ` value.                                                                                                                                                             |
    | `void`                                                                                               | `setUnicodeStreamAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` stream, int length)`<br>Sets the designated parameter to a Java UnicodeStream value.                                                                                    |
    | `void`                                                                                               | `setURLAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`URL`](http://download.oracle.com/javase/8/docs/api/java/net/URL.html?is-external=true)` value)`<br>Sets the designated parameter to a Java URL value.                                                                                                                                    |

    - ### Methods inherited from interface java.sql.[PreparedStatement](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true)

      [`addBatch`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#addBatch__)`, `[`clearParameters`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#clearParameters__)`, `[`execute`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#execute__)`, `[`executeLargeUpdate`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#executeLargeUpdate__)`, `[`executeQuery`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#executeQuery__)`, `[`executeUpdate`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#executeUpdate__)`, `[`getMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#getMetaData__)`, `[`getParameterMetaData`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#getParameterMetaData__)`, `[`setArray`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setArray_int_java_sql_Array_)`, `[`setAsciiStream`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setAsciiStream_int_java_io_InputStream_)`, `[`setAsciiStream`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setAsciiStream_int_java_io_InputStream_int_)`, `[`setAsciiStream`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setAsciiStream_int_java_io_InputStream_long_)`, `[`setBigDecimal`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setBigDecimal_int_java_math_BigDecimal_)`, `[`setBinaryStream`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setBinaryStream_int_java_io_InputStream_)`, `[`setBinaryStream`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setBinaryStream_int_java_io_InputStream_int_)`, `[`setBinaryStream`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setBinaryStream_int_java_io_InputStream_long_)`, `[`setBlob`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setBlob_int_java_sql_Blob_)`, `[`setBlob`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setBlob_int_java_io_InputStream_)`, `[`setBlob`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setBlob_int_java_io_InputStream_long_)`, `[`setBoolean`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setBoolean_int_boolean_)`, `[`setByte`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setByte_int_byte_)`, `[`setBytes`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setBytes_int_byte_A_)`, `[`setCharacterStream`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setCharacterStream_int_java_io_Reader_)`, `[`setCharacterStream`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setCharacterStream_int_java_io_Reader_int_)`, `[`setCharacterStream`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setCharacterStream_int_java_io_Reader_long_)`, `[`setClob`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setClob_int_java_sql_Clob_)`, `[`setClob`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setClob_int_java_io_Reader_)`, `[`setClob`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setClob_int_java_io_Reader_long_)`, `[`setDate`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setDate_int_java_sql_Date_)`, `[`setDate`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setDate_int_java_sql_Date_java_util_Calendar_)`, `[`setDouble`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setDouble_int_double_)`, `[`setFloat`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setFloat_int_float_)`, `[`setInt`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setInt_int_int_)`, `[`setLong`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setLong_int_long_)`, `[`setNCharacterStream`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setNCharacterStream_int_java_io_Reader_)`, `[`setNCharacterStream`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setNCharacterStream_int_java_io_Reader_long_)`, `[`setNClob`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setNClob_int_java_sql_NClob_)`, `[`setNClob`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setNClob_int_java_io_Reader_)`, `[`setNClob`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setNClob_int_java_io_Reader_long_)`, `[`setNString`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setNString_int_java_lang_String_)`, `[`setNull`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setNull_int_int_)`, `[`setNull`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setNull_int_int_java_lang_String_)`, `[`setObject`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setObject_int_java_lang_Object_)`, `[`setObject`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setObject_int_java_lang_Object_int_)`, `[`setObject`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setObject_int_java_lang_Object_int_int_)`, `[`setObject`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setObject_int_java_lang_Object_java_sql_SQLType_)`, `[`setObject`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setObject_int_java_lang_Object_java_sql_SQLType_int_)`, `[`setRef`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setRef_int_java_sql_Ref_)`, `[`setRowId`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setRowId_int_java_sql_RowId_)`, `[`setShort`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setShort_int_short_)`, `[`setSQLXML`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setSQLXML_int_java_sql_SQLXML_)`, `[`setString`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setString_int_java_lang_String_)`, `[`setTime`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setTime_int_java_sql_Time_)`, `[`setTime`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setTime_int_java_sql_Time_java_util_Calendar_)`, `[`setTimestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setTimestamp_int_java_sql_Timestamp_)`, `[`setTimestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setTimestamp_int_java_sql_Timestamp_java_util_Calendar_)`, `[`setUnicodeStream`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setUnicodeStream_int_java_io_InputStream_int_)`, `[`setURL`](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true#setURL_int_java_net_URL_)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.[OracleStatement](OracleStatement.md)

      [`clearDefines`](OracleStatement.md)`, `[`closeOnCompletion`](OracleStatement.md)`, `[`closeWithKey`](OracleStatement.md)`, `[`creationState`](OracleStatement.md)`, `[`defineColumnType`](OracleStatement.md)`, `[`defineColumnType`](OracleStatement.md)`, `[`defineColumnType`](OracleStatement.md)`, `[`defineColumnType`](OracleStatement.md)`, `[`defineColumnTypeBytes`](OracleStatement.md)`, `[`defineColumnTypeChars`](OracleStatement.md)`, `[`enquoteIdentifier`](OracleStatement.md)`, `[`enquoteLiteral`](OracleStatement.md)`, `[`enquoteNCharLiteral`](OracleStatement.md)`, `[`getLobPrefetchSize`](OracleStatement.md)`, `[`getRegisteredQueryId`](OracleStatement.md)`, `[`getRegisteredTableNames`](OracleStatement.md)`, `[`getRowPrefetch`](OracleStatement.md)`, `[`isNCHAR`](OracleStatement.md)`, `[`isSimpleIdentifier`](OracleStatement.md)`, `[`setDatabaseChangeRegistration`](OracleStatement.md)`, `[`setLobPrefetchSize`](OracleStatement.md)`, `[`setRowPrefetch`](OracleStatement.md)

    <!-- -->

    - ### Methods inherited from interface java.sql.[Statement](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true)

      [`addBatch`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#addBatch_java_lang_String_)`, `[`cancel`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#cancel__)`, `[`clearBatch`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#clearBatch__)`, `[`clearWarnings`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#clearWarnings__)`, `[`close`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#close__)`, `[`execute`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#execute_java_lang_String_)`, `[`execute`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#execute_java_lang_String_int_)`, `[`execute`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#execute_java_lang_String_int_A_)`, `[`execute`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#execute_java_lang_String_java_lang_String_A_)`, `[`executeBatch`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#executeBatch__)`, `[`executeLargeBatch`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#executeLargeBatch__)`, `[`executeLargeUpdate`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#executeLargeUpdate_java_lang_String_)`, `[`executeLargeUpdate`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#executeLargeUpdate_java_lang_String_int_)`, `[`executeLargeUpdate`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#executeLargeUpdate_java_lang_String_int_A_)`, `[`executeLargeUpdate`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#executeLargeUpdate_java_lang_String_java_lang_String_A_)`, `[`executeQuery`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#executeQuery_java_lang_String_)`, `[`executeUpdate`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#executeUpdate_java_lang_String_)`, `[`executeUpdate`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#executeUpdate_java_lang_String_int_)`, `[`executeUpdate`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#executeUpdate_java_lang_String_int_A_)`, `[`executeUpdate`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#executeUpdate_java_lang_String_java_lang_String_A_)`, `[`getConnection`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getConnection__)`, `[`getFetchDirection`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getFetchDirection__)`, `[`getFetchSize`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getFetchSize__)`, `[`getGeneratedKeys`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getGeneratedKeys__)`, `[`getLargeMaxRows`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getLargeMaxRows__)`, `[`getLargeUpdateCount`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getLargeUpdateCount__)`, `[`getMaxFieldSize`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getMaxFieldSize__)`, `[`getMaxRows`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getMaxRows__)`, `[`getMoreResults`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getMoreResults__)`, `[`getMoreResults`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getMoreResults_int_)`, `[`getQueryTimeout`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getQueryTimeout__)`, `[`getResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getResultSet__)`, `[`getResultSetConcurrency`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getResultSetConcurrency__)`, `[`getResultSetHoldability`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getResultSetHoldability__)`, `[`getResultSetType`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getResultSetType__)`, `[`getUpdateCount`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getUpdateCount__)`, `[`getWarnings`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#getWarnings__)`, `[`isClosed`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#isClosed__)`, `[`isCloseOnCompletion`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#isCloseOnCompletion__)`, `[`isPoolable`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#isPoolable__)`, `[`setCursorName`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#setCursorName_java_lang_String_)`, `[`setEscapeProcessing`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#setEscapeProcessing_boolean_)`, `[`setFetchDirection`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#setFetchDirection_int_)`, `[`setFetchSize`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#setFetchSize_int_)`, `[`setLargeMaxRows`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#setLargeMaxRows_long_)`, `[`setMaxFieldSize`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#setMaxFieldSize_int_)`, `[`setMaxRows`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#setMaxRows_int_)`, `[`setPoolable`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#setPoolable_boolean_)`, `[`setQueryTimeout`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#setQueryTimeout_int_)

    <!-- -->

    - ### Methods inherited from interface java.sql.[Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true)

      [`isWrapperFor`](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true#isWrapperFor_java_lang_Class_)`, `[`unwrap`](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true#unwrap_java_lang_Class_)

<!-- -->

- - ### Field Detail

    - #### FORM_NCHAR

          static final short FORM_NCHAR

      Specifies the "form of use" for SQL NCHAR datatypes (NCHAR, NVARCHAR2 and NCLOB). It is used only in the argument to `setFormOfUse()`.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### FORM_CHAR

          static final short FORM_CHAR

      Specifies the "form of use" for SQL CHAR datatypes (CHAR, VARCHAR2 and CLOB). It is used only in the argument to `setFormOfUse()`.
      See Also:
      [Constant Field Values](../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### defineParameterTypeBytes

          void defineParameterTypeBytes(int param_index,
                                        int type,
                                        int max_size)
                                 throws SQLException

      Define the type under which you will bind the parameter and the maximum size (in bytes) of data you will bind in binds.
      Similarly to `defineColumnType()`. Before executing a Query you may choose to inform JDBC of the type and maximum length of the bind parameter. If not, based on the `setXXX` call, the maximum length of the type is taken, i.e., for a setString a 4k buffer is allocated. This API does not reduce the network round trip. It is purely a memory optimization API.

      **Note:** You should use `OracleTypes.CHAR` as the type value if you are going bind later as `setCHAR` and use `OracleTypes.VARCHAR` if you are going to bind as `setString` for effective results.

      Parameters:
      `param_index` - Index of bind parameter (should be \>=0)

      `type` - Type to be assigned to bind parameter. This type could be different from the native type of the column. Appropriate conversions will be done.

      `max_size` - Maximum length of bind data in bytes (should be \>=0)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the type you specify is not available

    <!-- -->

    - #### defineParameterTypeChars

          void defineParameterTypeChars(int param_index,
                                        int type,
                                        int max_size)
                                 throws SQLException

      Define the type under which you will bind the parameter and the maximum size (in characters) of data you will bind in binds.
      Similarly to `defineColumnType()`. Before executing a Query you may choose to inform JDBC of the type and maximum length of the bind parameter. If not, based on the `setXXX` call, the maximum length of the type is taken, i.e., for a setString a 4k buffer is allocated. This API does not reduce the network round trip. It is purely a memory optimization API.

      **Note:** You should use `OracleTypes.CHAR` as the type value if you are going bind later as `setCHAR` and use `OracleTypes.VARCHAR` if you are going to bind as `setString` for effective results.

      Parameters:
      `param_index` - Index of bind parameter (should be \>=0)

      `type` - Type to be assigned to bind parameter. This type could be different from the native type of the column. Appropriate conversions will be done.

      `max_size` - Maximum length of bind data in bytes (should be \>=0)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if the type you specify is not available

    <!-- -->

    - #### defineParameterType

          void defineParameterType(int param_index,
                                   int type,
                                   int max_size)
                            throws SQLException

      Define the type under which you will bind the parameter and the maximum size (in characters) of data you will bind in binds. Depending on the value of the dataSizeUnits connection property, max_size will be measured in bytes or characters.
      Parameters:
      `param_index` -

      `type` -

      `max_size` -

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getExecuteBatch

          int getExecuteBatch()

      Deprecated. As of 12.1 all APIs related to oracle-style statement batching are deprecated in favor of standard JDBC batching. We recommend using the standard model going forward as it is spec compliant and provides more information and control to the application.
      Executions are not batched but sent immediately. Oracle style of batching has been deprecated in 12.1 and made a no-op in 12.2. We recommend using the standard model of batching.
      Returns:
      the batch value (always 1).

      See Also:
      [`OracleConnection.setDefaultExecuteBatch`](OracleConnection.md), `setExecuteBatch`

    <!-- -->

    - #### sendBatch

          int sendBatch()
                 throws SQLException

      Deprecated. As of 12.1 all APIs related to oracle-style statement batching are deprecated in favor of standard JDBC batching. We recommend using the standard model going forward as it is spec compliant and provides more information and control to the application.
      Executions are not batched but sent immediately. Oracle style of batching has been deprecated in 12.1 and made a no-op in 12.2. We recommend using the standard model of batching.
      Returns:
      the update count (always 0).

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - never thrown.

    <!-- -->

    - #### setARRAY

          void setARRAY(int parameterIndex,
                        ARRAY arr)
                 throws SQLException

      Binds the designated parameter to a `oracle.sql.ARRAY`.
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, ...

      `arr` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setBfile

          void setBfile(int parameterIndex,
                        BFILE file)
                 throws SQLException

      Binds the designated parameter to a `oracle.sql.BFILE` value.
      **Note:** This is the same as `setBFILE`.

      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, ...

      `file` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      See Also:
      `setBFILE`

    <!-- -->

    - #### setBFILE

          void setBFILE(int parameterIndex,
                        BFILE file)
                 throws SQLException

      Binds the designated parameter to a `oracle.sql.BFILE` value.
      **Note:** An instance of the `oracle.sql.BFILE` class contains only the locator of the BFILE, not the data. Thus, this method binds the designated parameter to a BFILE **locator** not to the data.

      For example, assume you want to insert a BFILE locator into a table, and you have an `OraclePreparedStatement` object `ops` to insert data into a table. The first column is a string (to designate a row number), the second column is a BFILE, and you have a valid `oracle.sql.BFILE` object (`bfile`). Write the BFILE to the database as follows:

              OraclePreparedStatement ops = (OraclePreparedStatement)conn.prepareStatement
              ("INSERT INTO my_bfile_table VALUES(?,?)");
              ops.setString(1, "one");
              ops.setBFILE(2, bfile);
              ops.execute();


      This stores only the locator of the BFILE in the `my_bfile_table`. See the [`BFILE`](../sql/BFILE.md) class to get more details about how to deal with the data.

      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, ...

      `file` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setBLOB

          void setBLOB(int parameterIndex,
                       BLOB lob)
                throws SQLException

      Binds the designated parameter to a `oracle.sql.BLOB` value.
      **Note:** An instance of the `oracle.sql.BLOB` class contains only the locator of the BLOB, not the data. Thus, this method binds the designated parameter to a BLOB **locator** not to the data.

      For example, if you have an `OraclePreparedStatement` object `ops` and a BLOB named `my_blob`, then write the BLOB to the database as follows:

              OraclePreparedStatement ops = (OraclePreparedStatement)conn.prepareStatement
              ("INSERT INTO blob_table VALUES(?)");
              ops.setBLOB(1, my_blob);
              ops.execute();


      This stores only the locator of the BLOB in the `clob_table`. Use the method [`BLOB.getBinaryOutputStream`](../sql/BLOB.md) to write data to a BLOB.

      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, ...

      `lob` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setCHAR

          void setCHAR(int parameterIndex,
                       CHAR ch)
                throws SQLException

      Binds the designated parameter to a `oracle.sql.CHAR` value.
      `setCHAR` checks the character set of the argument. If it is not the same as the network character set, then the bytes of the argument are converted to the network character set and those bytes are sent to the database. The conversion between the argument character set and the network character set is via the Universal Character Set (UCS2). That is, the argument is converted to UCS2, then the UCS2 bytes are converted to the network character set.

      **Note:** If an input character does not have a representation in UCS2, or if the UCS2 does not have a representation of the network character set, `setCHAR` will throw an exception.

      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, ...

      `ch` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      See Also:
      `setFixedChar`

    <!-- -->

    - #### setCLOB

          void setCLOB(int parameterIndex,
                       CLOB lob)
                throws SQLException

      Binds the designated parameter to a `oracle.sql.CLOB` value.
      **Note:** An instance of the `oracle.sql.CLOB` class contains only the locator of the CLOB, not the data. Thus, this method binds the designated parameter to a CLOB **locator** not to the data.

      For example, if you have an `OraclePreparedStatement` object `ops` and a CLOB named `my_clob`, then write the CLOB to the database as follows:

              OraclePreparedStatement ops = (OraclePreparedStatement)conn.prepareStatement
              ("INSERT INTO clob_table VALUES(?)");
              ops.setCLOB(1, my_clob);
              ops.execute();


      This stores only the locator of the CLOB in the `clob_table`. Use the methods [`CLOB.getCharacterOutputStream`](../sql/CLOB.md) or [`CLOB.getAsciiOutputStream`](../sql/CLOB.md) to write data to a CLOB.

      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, ...

      `lob` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setCursor

          void setCursor(int parameterIndex,
                         ResultSet rs)
                  throws SQLException

      Deprecated. 
      Binds the designated parameter to a `java.sql.ResultSet`. This is used for RefCursor parameter only.
      **NOTE:** The method is a misnomer. You should use CURSOR only in callable statements.

      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, ...

      `rs` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      See Also:
      [`OracleCallableStatement.getCursor`](OracleCallableStatement.md)

    <!-- -->

    - #### setCustomDatum

          void setCustomDatum(int parameterIndex,
                              CustomDatum x)
                       throws SQLException

      Deprecated. 
      Binds the designated parameter to a `oracle.sql.CustomDatum` value.
      In the 9i release the `oracle.sql.CustomDatum` has been deprecated and replaced by the `oracle.sql.ORAData` interface. For this reason, this method is also deprecated. It is recommended to use `setORAData()` instead.

      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, ...

      `x` - the parameter value, should not be null.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs, or if null value is passed as x.

    <!-- -->

    - #### setORAData

          void setORAData(int parameterIndex,
                          ORAData x)
                   throws SQLException

      Binds the designated parameter to a `oracle.sql.ORAData` value.
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, ...

      `x` - the parameter value, should not be null.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs, or if null value is passed as x.

    <!-- -->

    - #### setDATE

          void setDATE(int parameterIndex,
                       DATE date)
                throws SQLException

      Binds the designated parameter to a `oracle.sql.DATE` value.
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, ...

      `date` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setExecuteBatch

          void setExecuteBatch(int batchValue)
                        throws SQLException

      Deprecated. As of 12.1 all APIs related to oracle-style statement batching are deprecated in favor of standard JDBC batching. We recommend using the standard model going forward as it is spec compliant and provides more information and control to the application.
      Executions are not batched but sent immediately. Oracle style of batching has been deprecated in 12.1 and made a no-op in 12.2. We recommend using the standard model of batching.
      Parameters:
      `batchValue` - batch value to be set, this is discarded.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if `batchValue` is less than 1 (never thrown).

      See Also:
      `getExecuteBatch`, [`OracleConnection.setDefaultExecuteBatch`](OracleConnection.md)

    <!-- -->

    - #### setFixedCHAR

          void setFixedCHAR(int parameterIndex,
                            String x)
                     throws SQLException

      Sets the disignated parameter to a `String` and executes a non-padded comparison with a SQL CHAR.
      CHAR data in the database is padded to the column width. This leads to a limitation in using the `setCHAR()` method to bind character data into the `WHERE` clause of a `SELECT` statement--the character data in the `WHERE` clause must also be padded to the column width to produce a match in the `SELECT` statement. This is especially troublesome if you do not know the column width.

      `setFixedCHAR()` remedies this. This method executes a non-padded comparison.

      **Notes:**

      - Remember to cast your prepared statement object to `OraclePreparedStatement` to use the `setFixedCHAR()` method.
      - There is no need to use setFixedCHAR() for an INSERT statement. The database always automatically pads the data to the column width as it inserts it.

      The following example demonstrates the difference between the `setString()`, `setCHAR()` and `setFixedCHAR()` methods.

              // Schema is : create table my_table (col1 char(10));
              //             insert into my_table values ('JDBC');
              PreparedStatement pstmt = conn.prepareStatement
              ("select count() from my_table where col1 = ?");
              ResultSet rs;

              pstmt.setString (1, "JDBC");  // Set the Bind Value
              rs = pstmt.executeQuery();    // This does not match any row
              // ... do something with rs
              CHAR ch = new CHAR("JDBC      ", null);
              ((OraclePreparedStatement)pstmt).setCHAR(1, ch); // Pad it to 10 bytes
              rs = pstmt.executeQuery();     // This matches one row
              // ... do something with rs
              ((OraclePreparedStatement)pstmt).setFixedCHAR(1, "JDBC");
              rs = pstmt.executeQuery();     // This matches one row
              // ... do something with rs


      Parameters:
      `parameterIndex` - index of the bind variable (first is 1)

      `x` - the literal/variable to be bound.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs while binding

      See Also:
      `setCHAR`

    <!-- -->

    - #### setNUMBER

          void setNUMBER(int parameterIndex,
                         NUMBER num)
                  throws SQLException

      Binds the designated parameter to a `oracle.sql.NUMBER` value.
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, ...

      `num` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setBinaryFloat

          void setBinaryFloat(int parameterIndex,
                              float value)
                       throws SQLException

      Sets the designated parameter to a Java float value. The float data is converted to the server internal BINARY_FLOAT format before being sent to the server.
      Note that with the JDBC standard setFloat API the float data is converted to server internal NUMBER format before being sent to the server. In Oracle the SQL REAL, FLOAT, and DOUBLE PRECISION datatypes are NUMBER types.

      The connection property SetFloatAndDoubleUseBinary causes the setFloat API to use binary conversion.

      Binary conversion sent to a BINARY_FLOAT parameter is fast and bit exact. Binary conversion sent to a NUMBER parameter moves CPU load to the server but the data will be the same as NUMBER conversion on the client.

      NUMBER conversion sent to a NUMBER parameter is correct and keeps the CPU load on the client. NUMBER conversion sent to a BINARY_FLOAT parameter is not bit exact and has extra CPU load on both client and server

      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, ...

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      10gR1

    <!-- -->

    - #### setBinaryFloat

          void setBinaryFloat(int parameterIndex,
                              BINARY_FLOAT value)
                       throws SQLException

      Sets the designated parameter to an oracle.sql.BINARY_FLOAT value. See setBinaryFloat for additional information.
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, ...

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setBinaryDouble

          void setBinaryDouble(int parameterIndex,
                               double value)
                        throws SQLException

      Sets the designated parameter to a Java double value. The double data is converted to the server internal BINARY_DOUBLE format before being sent to the server.
      Note that with the JDBC standard setDouble API the float data is converted to server internal NUMBER format before being sent to the server. In Oracle the SQL REAL, FLOAT, and DOUBLE PRECISION datatypes are NUMBER types.

      The connection property SetFloatAndDoubleUseBinary causes the setDouble API to use binary conversion.

      Binary conversion sent to a BINARY_DOUBLE parameter is fast and bit exact. Binary conversion sent to a NUMBER parameter moves CPU load to the server but the data will be the same as NUMBER conversion on the client.

      NUMBER conversion sent to a NUMBER parameter is correct and keeps the CPU load on the client. NUMBER conversion sent to a BINARY_DOUBLE parameter is not bit exact and has extra CPU load on both client and server

      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, ...

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setBinaryDouble

          void setBinaryDouble(int parameterIndex,
                               BINARY_DOUBLE value)
                        throws SQLException

      Sets the designated parameter to an oracle.sql.BINARY_DOUBLE value. See setBinaryDouble for additional information.
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, ...

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setOPAQUE

          void setOPAQUE(int parameterIndex,
                         OPAQUE val)
                  throws SQLException

      Binds the designated parameter to a `oracle.sql.OPAQUE` value.
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, ...

      `val` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setOracleObject

          void setOracleObject(int parameterIndex,
                               Datum x)
                        throws SQLException

      Binds the designated parameter to a `oracle.sql.Datum` value.
      This is a generic `setXXX()` method for binding `oracle.sql.` data into a prepared statement as an `oracle.sql.Datum` object.

      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, ...

      `x` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setStructDescriptor

          void setStructDescriptor(int parameterIndex,
                                   StructDescriptor desc)
                            throws SQLException

      Binds the bind type of designated parameter from an oracle.sql.StructDescriptor.
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, ...

      `desc` - the StructDescriptor to bind

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setRAW

          void setRAW(int parameterIndex,
                      RAW raw)
               throws SQLException

      Binds the designated parameter to a `oracle.sql.RAW` value.
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, ...

      `raw` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setREF

          void setREF(int parameterIndex,
                      REF ref)
               throws SQLException

      Binds the designated parameter to a `oracle.sql.REF` value.
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, ...

      `ref` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setRefType

          void setRefType(int parameterIndex,
                          REF ref)
                   throws SQLException

      Binds the designated parameter to a `oracle.sql.REF` value.
      **Note:** This is the same as `setREF`.

      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, ...

      `ref` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      See Also:
      `setREF`

    <!-- -->

    - #### setROWID

          void setROWID(int parameterIndex,
                        ROWID rowid)
                 throws SQLException

      Binds the designated parameter to a `oracle.sql.ROWID` value.
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, ...

      `rowid` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setSTRUCT

          void setSTRUCT(int parameterIndex,
                         STRUCT struct)
                  throws SQLException

      Binds the designated parameter to a `oracle.sql.STRUCT` value.
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, ...

      `struct` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setTIMESTAMP

          void setTIMESTAMP(int parameterIndex,
                            TIMESTAMP x)
                     throws SQLException

      Binds the designated parameter to an oracle.sql.TIMESTAMP value.
      Parameters:
      `parameterIndex` - specifies the parameter index. Index starts from 1.

      `x` - specifies the parameter value.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs

      Since:
      9i

    <!-- -->

    - #### setTIMESTAMPTZ

          void setTIMESTAMPTZ(int parameterIndex,
                              TIMESTAMPTZ x)
                       throws SQLException

      Binds the designated parameter to an `oracle.sql.TIMESTAMPTZ` value.
      Parameters:
      `parameterIndex` - specifies the parameter index. Index starts from 1.

      `x` - specifies the parameter value.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs

      Since:
      9i

    <!-- -->

    - #### setTIMESTAMPLTZ

          void setTIMESTAMPLTZ(int parameterIndex,
                               TIMESTAMPLTZ x)
                        throws SQLException

      Binds the designated parameter to an `oracle.sql.TIMESTAMPLTZ` value.
      In order to use this method, the calling program must first set the session time zone of the corresponding connection by using `OracleConnection.setSessionTimeZone()`.

      Parameters:
      `parameterIndex` - specifies the parameter index. Index starts from 1.

      `x` - specifies the parameter value.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs

      Since:
      9i

    <!-- -->

    - #### setINTERVALYM

          void setINTERVALYM(int parameterIndex,
                             INTERVALYM x)
                      throws SQLException

      Binds the designated parameter to an oracle.sql.INTERVALYM value.
      Parameters:
      `parameterIndex` - specifies the parameter index. Index starts from 1.

      `x` - specifies the parameter value.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs

      Since:
      9i

    <!-- -->

    - #### setINTERVALDS

          void setINTERVALDS(int parameterIndex,
                             INTERVALDS x)
                      throws SQLException

      Binds the designated parameter to an oracle.sql.INTERVALDS value.
      Parameters:
      `parameterIndex` - specifies the parameter index. Index starts from 1.

      `x` - specifies the parameter value.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs

      Since:
      10i

    <!-- -->

    - #### setNullAtName

          void setNullAtName(String parameterName,
                             int sqlType,
                             String sqlName)
                      throws SQLException

      Sets the designated parameter to a SQL NULL value.
      Parameters:
      `parameterName` -

      `sqlType` -

      `sqlName` - the name of the SQL type

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setNullAtName

          void setNullAtName(String parameterName,
                             int sqlType)
                      throws SQLException

      Sets the designated parameter to a SQL NULL value.
      Parameters:
      `parameterName` -

      `sqlType` -

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setBooleanAtName

          void setBooleanAtName(String parameterName,
                                boolean value)
                         throws SQLException

      Sets the designated parameter to a Java Boolean value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setByteAtName

          void setByteAtName(String parameterName,
                             byte value)
                      throws SQLException

      Sets the designated parameter to a Java Byte value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setShortAtName

          void setShortAtName(String parameterName,
                              short value)
                       throws SQLException

      Sets the designated parameter to a Java Short value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setIntAtName

          void setIntAtName(String parameterName,
                            int value)
                     throws SQLException

      Sets the designated parameter to a Java Int value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setLongAtName

          void setLongAtName(String parameterName,
                             long value)
                      throws SQLException

      Sets the designated parameter to a Java Long value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setFloatAtName

          void setFloatAtName(String parameterName,
                              float value)
                       throws SQLException

      Sets the designated parameter to a Java Float value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setDoubleAtName

          void setDoubleAtName(String parameterName,
                               double value)
                        throws SQLException

      Sets the designated parameter to a Java Double value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setBinaryFloatAtName

          void setBinaryFloatAtName(String parameterName,
                                    float value)
                             throws SQLException

      Sets the designated parameter to a Java Float value. See setBinaryFloat for additional information.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setBinaryFloatAtName

          void setBinaryFloatAtName(String parameterName,
                                    BINARY_FLOAT value)
                             throws SQLException

      Sets the designated parameter to an oracle.sql.BINARY_FLOAT value. See setBinaryFloat for additional information.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setBinaryDoubleAtName

          void setBinaryDoubleAtName(String parameterName,
                                     double value)
                              throws SQLException

      Sets the designated parameter to a Java Double value. See setBinaryDouble for additional information.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setBinaryDoubleAtName

          void setBinaryDoubleAtName(String parameterName,
                                     BINARY_DOUBLE value)
                              throws SQLException

      Sets the designated parameter to an oracle.sql.BINARY_DOUBLE value. See setBinaryDouble for additional information.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setBigDecimalAtName

          void setBigDecimalAtName(String parameterName,
                                   BigDecimal value)
                            throws SQLException

      Sets the designated parameter to a Java BigDecimal value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setStringAtName

          void setStringAtName(String parameterName,
                               String value)
                        throws SQLException

      Sets the designated parameter to a Java String value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setStringForClob

          void setStringForClob(int parameterIndex,
                                String value)
                         throws SQLException

      Sets the designated parameter to a Java String value. For large strings this will only work correctly with a CLOB column.
      Parameters:
      `parameterIndex` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setStringForClobAtName

          void setStringForClobAtName(String parameterName,
                                      String value)
                               throws SQLException

      Sets the designated parameter to a Java String value. For large strings this will only work correctly with a CLOB column.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setFixedCHARAtName

          void setFixedCHARAtName(String parameterName,
                                  String value)
                           throws SQLException

      Sets the designated parameter to a Java FixedCHAR value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setCursorAtName

          void setCursorAtName(String parameterName,
                               ResultSet value)
                        throws SQLException

      Sets the designated parameter to a Java Cursor value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setROWIDAtName

          void setROWIDAtName(String parameterName,
                              ROWID value)
                       throws SQLException

      Sets the designated parameter to an `oracle.sql.ROWID`value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setArrayAtName

          void setArrayAtName(String parameterName,
                              Array value)
                       throws SQLException

      Sets the designated parameter to a Java Array value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setARRAYAtName

          void setARRAYAtName(String parameterName,
                              ARRAY value)
                       throws SQLException

      Sets the designated parameter to a `oracle.sql.ARRAY` value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setOPAQUEAtName

          void setOPAQUEAtName(String parameterName,
                               OPAQUE value)
                        throws SQLException

      Sets the designated parameter to an `oracle.sql.OPAQUE`value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setStructDescriptorAtName

          void setStructDescriptorAtName(String parameterName,
                                         StructDescriptor desc)
                                  throws SQLException

      Sets the designated parameter to an `oracle.sql.StructDescriptor` value.
      Parameters:
      `parameterName` -

      `desc` - the StructDescriptor to bind

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setSTRUCTAtName

          void setSTRUCTAtName(String parameterName,
                               STRUCT value)
                        throws SQLException

      Sets the designated parameter to an `oracle.sql.STRUCT`value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setRAWAtName

          void setRAWAtName(String parameterName,
                            RAW value)
                     throws SQLException

      Sets the designated parameter to an `oracle.sql.RAW`value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setCHARAtName

          void setCHARAtName(String parameterName,
                             CHAR value)
                      throws SQLException

      Sets the designated parameter to an oracle.sql.CHAR value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setDATEAtName

          void setDATEAtName(String parameterName,
                             DATE value)
                      throws SQLException

      Sets the designated parameter to an oracle.sql.DATE value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setNUMBERAtName

          void setNUMBERAtName(String parameterName,
                               NUMBER value)
                        throws SQLException

      Sets the designated parameter to an `oracle.sql.NUMBER` value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setBLOBAtName

          void setBLOBAtName(String parameterName,
                             BLOB value)
                      throws SQLException

      Sets the designated parameter to an oracle.sql.BLOB value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setBlobAtName

          void setBlobAtName(String parameterName,
                             Blob value)
                      throws SQLException

      Sets the designated parameter to a Java Blob value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setBlobAtName

          void setBlobAtName(String parameterName,
                             InputStream stream,
                             long length)
                      throws SQLException

      Sets the designated parameter to a stream value.
      Parameters:
      `parameterName` -

      `stream` - the stream from which to read the value

      `length` - the number of bytes to read

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setBlobAtName

          void setBlobAtName(String parameterName,
                             InputStream stream)
                      throws SQLException

      Sets the designated parameter to a stream value.
      Parameters:
      `parameterName` -

      `stream` - the stream from which to read the value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setCLOBAtName

          void setCLOBAtName(String parameterName,
                             CLOB value)
                      throws SQLException

      Sets the designated parameter to an oracle.sql.CLOB value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setClobAtName

          void setClobAtName(String parameterName,
                             Clob value)
                      throws SQLException

      Sets the designated parameter to a Java Clob value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setClobAtName

          void setClobAtName(String parameterName,
                             Reader reader,
                             long length)
                      throws SQLException

      Sets the designated parameter to a stream value.
      Parameters:
      `parameterName` -

      `reader` - the Reader from which to get the value

      `length` - the number of bytes to read

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setClobAtName

          void setClobAtName(String parameterName,
                             Reader reader)
                      throws SQLException

      Sets the designated parameter to a stream value.
      Parameters:
      `parameterName` -

      `reader` - the Reader from which to get the value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setBFILEAtName

          void setBFILEAtName(String parameterName,
                              BFILE value)
                       throws SQLException

      Sets the designated parameter to a `oracle.sql.BFILE`value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setBfileAtName

          void setBfileAtName(String parameterName,
                              BFILE value)
                       throws SQLException

      Sets the designated parameter to a `oracle.sql.BFILE`value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setBytesAtName

          void setBytesAtName(String parameterName,
                              byte[] value)
                       throws SQLException

      Sets the designated parameter to a Java Bytes value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setBytesForBlob

          void setBytesForBlob(int parameterIndex,
                               byte[] value)
                        throws SQLException

      Sets the designated parameter to a Java bytes value. For large byte arrays this will only work correctly with a BLOB or LONG RAW column
      Parameters:
      `parameterIndex` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setBytesForBlobAtName

          void setBytesForBlobAtName(String parameterName,
                                     byte[] value)
                              throws SQLException

      Sets the designated parameter to a Java byte array value. For large byte arrays this will only work correctly with a BLOB or LONG RAW column.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setDateAtName

          void setDateAtName(String parameterName,
                             Date value)
                      throws SQLException

      Sets the designated parameter to a Java Date value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setDateAtName

          void setDateAtName(String parameterName,
                             Date value,
                             Calendar cal)
                      throws SQLException

      Sets the designated parameter to a Java Date value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      `cal` - the calendar to interpret the date

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setTimeAtName

          void setTimeAtName(String parameterName,
                             Time value)
                      throws SQLException

      Sets the designated parameter to a Java Time value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setTimeAtName

          void setTimeAtName(String parameterName,
                             Time value,
                             Calendar cal)
                      throws SQLException

      Sets the designated parameter to a Java Time value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      `cal` - the Calendar to use to interpret the value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setTimestampAtName

          void setTimestampAtName(String parameterName,
                                  Timestamp value)
                           throws SQLException

      Sets the designated parameter to a Java Timestamp value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setTimestampAtName

          void setTimestampAtName(String parameterName,
                                  Timestamp value,
                                  Calendar cal)
                           throws SQLException

      Sets the designated parameter to a Java Timestamp value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      `cal` - the Calendar to use to interpret the date

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setINTERVALYMAtName

          void setINTERVALYMAtName(String parameterName,
                                   INTERVALYM value)
                            throws SQLException

      Sets the designated parameter to an oracle.sql.INTERVALYM value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setINTERVALDSAtName

          void setINTERVALDSAtName(String parameterName,
                                   INTERVALDS value)
                            throws SQLException

      Sets the designated parameter to an oracle.sql.INTERVALDS value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setTIMESTAMPAtName

          void setTIMESTAMPAtName(String parameterName,
                                  TIMESTAMP value)
                           throws SQLException

      Sets the designated parameter to an `oracle.sql.TIMESTAMP` value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setTIMESTAMPTZAtName

          void setTIMESTAMPTZAtName(String parameterName,
                                    TIMESTAMPTZ value)
                             throws SQLException

      Sets the designated parameter to an `oracle.sql.TIMESTAMPTZ` value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setTIMESTAMPLTZAtName

          void setTIMESTAMPLTZAtName(String parameterName,
                                     TIMESTAMPLTZ value)
                              throws SQLException

      Sets the designated parameter to an `oracle.sql.TIMESTAMPLTZ` value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setAsciiStreamAtName

          void setAsciiStreamAtName(String parameterName,
                                    InputStream stream,
                                    int length)
                             throws SQLException

      Sets the designated parameter to a Java AsciiStream value.
      Parameters:
      `parameterName` -

      `stream` - the stream value

      `length` -

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setAsciiStreamAtName

          void setAsciiStreamAtName(String parameterName,
                                    InputStream stream,
                                    long length)
                             throws SQLException

      Sets the designated parameter to a Java AsciiStream value.
      Parameters:
      `parameterName` -

      `stream` - the stream value

      `length` -

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setAsciiStreamAtName

          void setAsciiStreamAtName(String parameterName,
                                    InputStream stream)
                             throws SQLException

      Sets the designated parameter to a Java AsciiStream value.
      Parameters:
      `parameterName` -

      `stream` - the stream value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setBinaryStreamAtName

          void setBinaryStreamAtName(String parameterName,
                                     InputStream stream,
                                     int length)
                              throws SQLException

      Sets the designated parameter to a Java BinaryStream value.
      Parameters:
      `parameterName` -

      `stream` -

      `length` -

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setBinaryStreamAtName

          void setBinaryStreamAtName(String parameterName,
                                     InputStream stream,
                                     long length)
                              throws SQLException

      Sets the designated parameter to a Java BinaryStream value.
      Parameters:
      `parameterName` -

      `stream` -

      `length` -

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setBinaryStreamAtName

          void setBinaryStreamAtName(String parameterName,
                                     InputStream stream)
                              throws SQLException

      Sets the designated parameter to a Java BinaryStream value.
      Parameters:
      `parameterName` -

      `stream` -

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setCharacterStreamAtName

          void setCharacterStreamAtName(String parameterName,
                                        Reader reader,
                                        long length)
                                 throws SQLException

      Sets the designated parameter to a Java CharacterStream value.
      Parameters:
      `parameterName` -

      `reader` -

      `length` -

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setCharacterStreamAtName

          void setCharacterStreamAtName(String parameterName,
                                        Reader reader)
                                 throws SQLException

      Sets the designated parameter to a Java CharacterStream value.
      Parameters:
      `parameterName` -

      `reader` -

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setUnicodeStreamAtName

          void setUnicodeStreamAtName(String parameterName,
                                      InputStream stream,
                                      int length)
                               throws SQLException

      Sets the designated parameter to a Java UnicodeStream value.
      Parameters:
      `parameterName` -

      `stream` -

      `length` -

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setCustomDatumAtName

          void setCustomDatumAtName(String parameterName,
                                    CustomDatum value)
                             throws SQLException

      Sets the designated parameter to a Java CustomDatum value.
      Parameters:
      `parameterName` -

      `value` - the parameter value, should not be null.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs, of if null value is passed as value.

    <!-- -->

    - #### setORADataAtName

          void setORADataAtName(String parameterName,
                                ORAData value)
                         throws SQLException

      Sets the designated parameter to an `oracle.sql.ORAData`value.
      Parameters:
      `parameterName` -

      `value` - the parameter value, should not be null.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs, or if null value is passed as value.

    <!-- -->

    - #### setObjectAtName

          void setObjectAtName(String parameterName,
                               Object value,
                               int targetSqlType,
                               int scale)
                        throws SQLException

      Sets the designated parameter to a Java Object value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      `targetSqlType` -

      `scale` -

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setObjectAtName

          void setObjectAtName(String parameterName,
                               Object value,
                               int targetSqlType)
                        throws SQLException

      Sets the designated parameter to a Java Object value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      `targetSqlType` -

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setRefTypeAtName

          void setRefTypeAtName(String parameterName,
                                REF value)
                         throws SQLException

      Sets the designated parameter to an `oracle.sql.REF`value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setRefAtName

          void setRefAtName(String parameterName,
                            Ref value)
                     throws SQLException

      Sets the designated parameter to a Java Ref value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setREFAtName

          void setREFAtName(String parameterName,
                            REF value)
                     throws SQLException

      Sets the designated parameter to an `oracle.sql.REF`value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setObjectAtName

          void setObjectAtName(String parameterName,
                               Object value)
                        throws SQLException

      Sets the designated parameter to a Java Object value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setOracleObjectAtName

          void setOracleObjectAtName(String parameterName,
                                     Datum value)
                              throws SQLException

      Sets the designated parameter to an `oracle.sql.Datum`value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setURLAtName

          void setURLAtName(String parameterName,
                            URL value)
                     throws SQLException

      Sets the designated parameter to a Java URL value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setCheckBindTypes

          void setCheckBindTypes(boolean flag)

      Enable/disable bind type checking.
      When bind type checking is disabled, the Jdbc driver does not check bind types for every execute. It is intended to be used as a performance enhancement if the user knows for fact that bind types do not change across different executions. The default is `true`.

      Parameters:
      `flag` - set it to false if Bind Types doesn't change

    <!-- -->

    - #### setPlsqlIndexTable

          @Deprecated
          void setPlsqlIndexTable(int parameterIndex,
                                              Object arrayData,
                                              int maxLen,
                                              int curLen,
                                              int elemSqlType,
                                              int elemMaxLen)
                                       throws SQLException

      Deprecated. since 18.1. Use java.sql.PreparedStatement.setObject(int parameterIndex, Object x).
      Binds a PL/SQL Associative Array parameter in the IN parameter mode.
      Associative Arrays were formerly called index-by-tables. In PL/SQL they are arrays of key-value pairs where the keys may be numeric or string types and the values may be any scalar type. The keys may be sparse. See the PL/SQL manual

      The database only exports a limited form of this to the client where the keys must be numeric, positive and dense and the values can be only numeric or string. The lengths of the string data are limited to 32767 bytes. The number of characters depends on the character set used. See the PL/SQL manual. The JDBC-thin and JDBC-OCI drivers support 32767 bytes. The server side internal driver is limited to 16382 bytes for input.

      Parameters:
      `parameterIndex` - This argument indicates the parameter position within the statement. The first parameter is 1, the second is 2, ...

      `arrayData` - This argument is an array of values to be bound to the PL/SQL index-by table parameter. The value is of type java.lang.Object, and the value can be a Java primitive type array such as int\[\] or a Java object array such as BigDecimal\[\].

      `maxLen` - This argument specifies the maximum table length of the index-by table bind value which defines the maximum possible curLen for batch updates. For standalone binds, maxLen should use the same value as curLen. This argument is required.

      `curLen` - This argument specifies the actual size of the index-by table bind value in arrayData. If the curLen value is smaller than the size of arrayData, only the curLen number of table elements is passed to the database. If the curLen value is larger than the size of arrayData, the entire arrayData is sent to the database.

      `elemSqlType` - This argument specifies the index-by table element type based on the values defined in the OracleTypes class.

      `elemMaxLen` - This argument specifies the index-table element maximum length in case the element type is CHAR, VARCHAR, or RAW. This value is ignored for other types. A value of 0 for elemMaxLen would inidicate the driver to calculate the elemMaxLen based on the actual length of data bound. For a non zero value if the data bound is greater than elemMaxLen it is truncated.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      8.1.7

    <!-- -->

    - #### setFormOfUse

          void setFormOfUse(int parameterIndex,
                            short formOfUse)

      Specifies if the data is bound for a SQL NCHAR datatype. It sets the "form of use" of a column of this prepared statement. There are two constants that specify the "form of use": `FORM_CHAR` for SQL CHAR datatypes and `FORM_NCHAR` for SQL NCHAR datatypes, where `FORM_CHAR` is the default. If the "form of use" is set to `FORM_NCHAR`, the JDBC driver will represent the provided data in the national character set of the server.
      The usage of SQL NCHAR datatypes is similar to that of the SQL CHAR (`CHAR`, `VARCHAR2`, and `CLOB`) datatypes. JDBC uses the same classes and methods to access SQL NCHAR datatypes that are used for the corresponding SQL CHAR datatypes. Therefore, there are no separate, corresponding classes defined in the `oracle.sql` package for SQL NCHAR datatypes. Likewise, there is no separate, corresponding constant defined in the `oracle.jdbc.OracleTypes` class for SQL NCHAR datatypes. The only difference in usage between the two datatypes occur in a data bind situation: a JDBC program must call the `setFormOfUse()` method to specify if the data is bound for a SQL NCHAR datatype.

      In order to put this method in effect, you must invoke this method before `setXXX()` and `registerOutParameter()` for the column.

      The following code shows how to access SQL NCHAR data:

              //
              // Table TEST has the following columns:
              // - NUMBER
              // - NVARCHAR2
              // - NCHAR
              //
              oracle.jdbc.OraclePreparedStatement pstmt =
              (oracle.jdbc.OraclePreparedStatement)
              conn.prepareStatement("insert into TEST values(?, ?, ?)");

              // oracle.jdbc.OraclePreparedStatement.FORM_NCHAR should be used for all NCHAR,
              // NVARCHAR2 and NCLOB data types.

              pstmt.setFormOfUse(2, FORM_NCHAR);
              pstmt.setFormOfUse(3, FORM_NCHAR);
              pstmt.setInt(1, 1);                    // NUMBER column
              pstmt.setString(2, myUnicodeString1);  // NVARCHAR2 column
              pstmt.setString(3, myUnicodeString2);  // NCHAR column
              pstmt.execute();


      Parameters:
      `parameterIndex` - index of the column in the preparedStatment

      `formOfUse` - use FORM_CHAR for CHAR, VARCHAR2 and CLOB data, or FORM_NCHAR for NCHAR, NVARCHAR2 and NCLOB data. FORM_CHAR is the default.

      Since:
      9i

    <!-- -->

    - #### setDisableStmtCaching

          void setDisableStmtCaching(boolean cache)

      Don't Cache this object even when the corresponding Connection is Cache Enabled.
      Parameters:
      `cache` - Set it to true, if you don't want this statement to be cached.

    <!-- -->

    - #### OracleGetParameterMetaData

          OracleParameterMetaData OracleGetParameterMetaData()
                                                      throws SQLException

      Retrieves the number, types and properties of this `PreparedStatement` object's parameters.
      Returns:
      an `OracleParameterMetaData` object that contains information about the number, types and properties of this `PreparedStatement` object's parameters

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

      See Also:
      [`OracleParameterMetaData`](OracleParameterMetaData.md)

    <!-- -->

    - #### registerReturnParameter

          void registerReturnParameter(int paramIndex,
                                       int externalType)
                                throws SQLException

      Registers return parameter for DML Returning.
      Parameters:
      `paramIndex` - Index of return parameter (should be \> 0)

      `externalType` - Type of return parameter.
      For OracleTypes REF, STRUCT, JAVA_STRUCT, ARRAY, use:
      `registerReturnParameter(int paramIndex, int externalType, String typeName)`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs

      Since:
      10.2

    <!-- -->

    - #### registerReturnParameter

          void registerReturnParameter(int paramIndex,
                                       int externalType,
                                       int maxSize)
                                throws SQLException

      Registers return parameter for DML Returning. maxSize is the max bytes or chars of the return parameter, depending on the type of the return parameter. This method can be only used with char or raw types. If you don't know the max size of return parameters, you should use registerReturnParameter(int paramIndex, int externalType), which picks the default max size for you. If you know the max size of return parameters, using this method can reduce memory consumption.
      Parameters:
      `paramIndex` - Index of return parameter (should be \> 0)

      `externalType` - Type of return parameter

      `maxSize` - Max bytes or chars of return parameter

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs

      Since:
      10.2

    <!-- -->

    - #### registerReturnParameter

          void registerReturnParameter(int paramIndex,
                                       int externalType,
                                       String typeName)
                                throws SQLException

      Registers return parameter for DML Returning.
      Parameters:
      `paramIndex` - Index of return parameter (should be \> 0)

      `externalType` - Type of return parameter

      `typeName` - The fully-qualified name of an SQL structured type

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs

      Since:
      10.2

    <!-- -->

    - #### getReturnResultSet

          ResultSet getReturnResultSet()
                                throws SQLException

      Returns result set that contains data returned from DML Returning.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs

      Since:
      10.2

    <!-- -->

    - #### setNCharacterStreamAtName

          void setNCharacterStreamAtName(String parameterName,
                                         Reader reader,
                                         long length)
                                  throws SQLException

      Sets the designated parameter to a Java CharacterStream value using the NCHAR character set.
      Parameters:
      `parameterName` -

      `reader` -

      `length` -

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setNCharacterStreamAtName

          void setNCharacterStreamAtName(String parameterName,
                                         Reader reader)
                                  throws SQLException

      Sets the designated parameter to a Java CharacterStream value using the NCHAR character set.
      Parameters:
      `parameterName` -

      `reader` -

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setNClobAtName

          void setNClobAtName(String parameterName,
                              NClob value)
                       throws SQLException

      Sets the designated parameter to a `java.sql.NClob`value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setNClobAtName

          void setNClobAtName(String parameterName,
                              Reader reader,
                              long length)
                       throws SQLException

      Sets the designated parameter to a `java.sql.NClob`value.
      Parameters:
      `parameterName` -

      `reader` - the Reader from which to get the value

      `length` - the number of characters to read

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setNClobAtName

          void setNClobAtName(String parameterName,
                              Reader reader)
                       throws SQLException

      Sets the designated parameter to a `java.sql.NClob`value.
      Parameters:
      `parameterName` -

      `reader` - the Reader from which to get the value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setNStringAtName

          void setNStringAtName(String parameterName,
                                String value)
                         throws SQLException

      Sets the designated parameter to a `java.sql.String`value using the NCHAR character set
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setRowIdAtName

          void setRowIdAtName(String parameterName,
                              RowId value)
                       throws SQLException

      Sets the designated parameter to a `java.sql.RowId`value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setSQLXMLAtName

          void setSQLXMLAtName(String parameterName,
                               SQLXML value)
                        throws SQLException

      Sets the designated parameter to a `java.sql.SQLXML`value.
      Parameters:
      `parameterName` -

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OraclePreparedStatement.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OraclePooledConnectionBuilder.md)
- [Next Class](OracleRef.md)

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
