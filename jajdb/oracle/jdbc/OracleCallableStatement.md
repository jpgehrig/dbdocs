Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleCallableStatement.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleBlob.md)
- [Next Class](OracleClob.md)

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

## Interface OracleCallableStatement

- All Superinterfaces:
  [AutoCloseable](http://download.oracle.com/javase/8/docs/api/java/lang/AutoCloseable.html?is-external=true), [CallableStatement](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true), [OraclePreparedStatement](OraclePreparedStatement.md), [OracleStatement](OracleStatement.md), [PreparedStatement](http://download.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html?is-external=true), [Statement](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true), [Wrapper](http://download.oracle.com/javase/8/docs/api/java/sql/Wrapper.html?is-external=true)

  ------------------------------------------------------------------------



      public interface OracleCallableStatement
      extends CallableStatement, OraclePreparedStatement

  This interface extends the `OraclePreparedStatement` (which extends the `OracleStatement` interface) and incorporates standard JDBC callable statement functionality. It is used to execute SQL stored procedure.
  Oracle JDBC drivers support execution of PL/SQL stored procedures and anonymous blocks. They support both SQL92 escape syntax and Oracle PL/SQL block syntax. The following PL/SQL calls would work with any Oracle JDBC driver:

        // SQL92 syntax
        CallableStatement cs1 = conn.prepareCall
        ( "{call proc (?,?)}" ) ; // stored proc
        CallableStatement cs2 = conn.prepareCall
        ( "{? = call func (?,?)}" ) ; // stored func
        // Oracle PL/SQL block syntax
        CallableStatement cs3 = conn.prepareCall
        ( "begin proc (?,?); end;" ) ; // stored proc
        CallableStatement cs4 = conn.prepareCall
        ( "begin ? := func(?,?); end;" ) ; // stored func


  As an example of using Oracle syntax, here is a PL/SQL code snippet that creates a stored function. The PL/SQL function gets a character sequence and concatenates a suffix to it:

        create or replace function foo (val1 char)
        return char as
        begin
        return val1 || 'suffix';
        end;


  Your invocation call in your JDBC program should look like:

        Connection conn = DriverManager.getConnection
        ("jdbc:oracle:oci8:@<hoststring>", "scott", "tiger");
        CallableStatement cs = conn.prepareCall ("begin ? := foo(?); end;");
        cs.registerOutParameter(1,Types.CHAR);
        cs.setString(2, "aa");
        cs.executeUpdate();
        String result = cs.getString(1);


  Since:
  8.1.7

  See Also:
  `Connection.prepareCall`

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.jdbc.[OraclePreparedStatement](OraclePreparedStatement.md)

      [`FORM_CHAR`](OraclePreparedStatement.md)`, `[`FORM_NCHAR`](OraclePreparedStatement.md)

    <!-- -->

    - ### Fields inherited from interface oracle.jdbc.[OracleStatement](OracleStatement.md)

      [`EXPLICIT`](OracleStatement.md)`, `[`IMPLICIT`](OracleStatement.md)`, `[`NEW`](OracleStatement.md)

    <!-- -->

    - ### Fields inherited from interface java.sql.[Statement](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true)

      [`CLOSE_ALL_RESULTS`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#CLOSE_ALL_RESULTS)`, `[`CLOSE_CURRENT_RESULT`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#CLOSE_CURRENT_RESULT)`, `[`EXECUTE_FAILED`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#EXECUTE_FAILED)`, `[`KEEP_CURRENT_RESULT`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#KEEP_CURRENT_RESULT)`, `[`NO_GENERATED_KEYS`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#NO_GENERATED_KEYS)`, `[`RETURN_GENERATED_KEYS`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#RETURN_GENERATED_KEYS)`, `[`SUCCESS_NO_INFO`](http://download.oracle.com/javase/8/docs/api/java/sql/Statement.html?is-external=true#SUCCESS_NO_INFO)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                                                       | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    |---------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)         | `getAnyDataEmbeddedObject``(int parameterIndex)`<br>Deprecated. <br>As of Oracle 11R1 there is full support for ANYTYPE and ANYDATA. Please use oracle.sql.ANYDATA for new code and plan on replacing any use of this method by the next major release. Note that in 11R1 this method is reimplemnted using the ANYDATA support and will now also function in all the drivers, not just oci. In the previous implementation it was possible to call registerOutParameter with a sqlType of either oracle.jdbc.OracleTypes.OPAQUE or oracle.jdbc.OracleTypes.STRUCT The new implemention requires the correct type which is OPAQUE. |
    | [`ARRAY`](../sql/ARRAY.md)                                                                              | `getARRAY``(int parameterIndex)`<br>Retrieves data into an `oracle.sql.ARRAY` object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | [`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true) | `getAsciiStream``(int parameterIndex)`<br>Retrieves data into an `java.io.InputStream` object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | [`BFILE`](../sql/BFILE.md)                                                                              | `getBfile``(int parameterIndex)`<br>Retrieves data into an `oracle.sql.BFILE` object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | [`BFILE`](../sql/BFILE.md)                                                                              | `getBFILE``(int parameterIndex)`<br>Retrieves data into an `oracle.sql.BFILE` object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | [`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true) | `getBinaryStream``(int parameterIndex)`<br>Retrieves data into an `java.io.InputStream` object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | [`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true) | `getBinaryStream``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName)`<br>Retrieves data into an `java.io.InputStream` object.                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | [`BLOB`](../sql/BLOB.md)                                                                                | `getBLOB``(int parameterIndex)`<br>Retrieves data into an `oracle.sql.BLOB` object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | [`CHAR`](../sql/CHAR.md)                                                                                | `getCHAR``(int parameterIndex)`<br>Retrieves data into an `oracle.sql.CHAR` object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | [`Reader`](http://download.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)           | `getCharacterStream``(int parameterIndex)`<br>Retrieves data into an `java.io.Reader` object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | [`CLOB`](../sql/CLOB.md)                                                                                | `getCLOB``(int parameterIndex)`<br>Retrieves data into an `oracle.sql.CLOB` object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true)    | `getCursor``(int parameterIndex)`<br>Retrieves data into an `java.sql.ResultSet` object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)         | `getCustomDatum``(int parameterIndex, `[`CustomDatumFactory`](../sql/CustomDatumFactory.md)` factory)`<br>Deprecated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | [`DATE`](../sql/DATE.md)                                                                                | `getDATE``(int parameterIndex)`<br>Retrieves data into an `oracle.sql.DATE` object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | [`INTERVALDS`](../sql/INTERVALDS.md)                                                                    | `getINTERVALDS``(int parameterIndex)`<br>Retrieves data into an `oracle.sql.INTERVALDS` object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | [`INTERVALYM`](../sql/INTERVALYM.md)                                                                    | `getINTERVALYM``(int parameterIndex)`<br>Retrieves data into an `oracle.sql.INTERVALYM` object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | [`NUMBER`](../sql/NUMBER.md)                                                                            | `getNUMBER``(int parameterIndex)`<br>Retrieves data into an `oracle.sql.NUMBER` object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)         | `getObject``(int parameterIndex, `[`OracleDataFactory`](OracleDataFactory.md)` factory)`<br>Returns an instance of `OracleData`, which is returned by the factory's "create" method                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | [`OPAQUE`](../sql/OPAQUE.md)                                                                            | `getOPAQUE``(int parameterIndex)`<br>Retrieves data into an `oracle.sql.OPAQUE` object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | [`Datum`](../sql/Datum.md)                                                                              | `getOracleObject``(int parameterIndex)`<br>Retrieves data into an `oracle.sql.Datum` object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | [`Datum`](../sql/Datum.md)`[]`                                                                          | `getOraclePlsqlIndexTable``(int paramIndex)`<br>Deprecated. <br>since 18.1 Use java.sql.CallableStatement.getObject(int parameterIndex) method.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)         | `getORAData``(int parameterIndex, `[`ORADataFactory`](../sql/ORADataFactory.md)` factory)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)         | `getPlsqlIndexTable``(int paramIndex)`<br>Deprecated. <br>since 18.1. Use java.sql.CallableStatement.getObject(int parameterIndex) method.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)         | `getPlsqlIndexTable``(int paramIndex, `[`Class`](http://download.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)` primitiveType)`<br>Deprecated. <br>since 18.1. Use java.sql.CallableStatement.getObject(int parameterIndex, Class\<T\> type) method.                                                                                                                                                                                                                                                                                                                                                         |
    | [`RAW`](../sql/RAW.md)                                                                                  | `getRAW``(int parameterIndex)`<br>Retrieves data into an `oracle.sql.RAW` object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | [`REF`](../sql/REF.md)                                                                                  | `getREF``(int parameterIndex)`<br>Retrieves data into an `oracle.sql.REF` object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | [`ROWID`](../sql/ROWID.md)                                                                              | `getROWID``(int parameterIndex)`<br>Retrieves data into an `oracle.sql.ROWID` object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | [`STRUCT`](../sql/STRUCT.md)                                                                            | `getSTRUCT``(int parameterIndex)`<br>Retrieves data into an `oracle.sql.STRUCT` object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | [`TIMESTAMP`](../sql/TIMESTAMP.md)                                                                      | `getTIMESTAMP``(int paramIdx)`<br>Retrieves data into an `oracle.sql.TIMESTAMP` object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | [`TIMESTAMPLTZ`](../sql/TIMESTAMPLTZ.md)                                                                | `getTIMESTAMPLTZ``(int paramIdx)`<br>Retrieves data into an `oracle.sql.TIMESTAMPLTZ` object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | [`TIMESTAMPTZ`](../sql/TIMESTAMPTZ.md)                                                                  | `getTIMESTAMPTZ``(int paramIdx)`<br>Retrieves data into an `oracle.sql.TIMESTAMPTZ` object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | [`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true) | `getUnicodeStream``(int parameterIndex)`<br>Retrieves data into an `java.io.InputStream` object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | [`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true) | `getUnicodeStream``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName)`<br>Retrieves data into an `java.io.InputStream` object.                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `void`                                                                                                  | `registerIndexTableOutParameter``(int paramIndex, int maxLen, int elemSqlType, int elemMaxLen)`<br>Deprecated. <br>since 18.1. Use java.sql.CallableStatement.registerOutParameter (int parameterIndex, int sqlType, String typeName).                                                                                                                                                                                                                                                                                                                                                                                             |
    | `void`                                                                                                  | `registerOutParameter``(int paramIndex, int sqlType, int scale, int maxLength)`<br>Special Oracle version of registerOutParameter for registering CHAR, VARCHAR, LONG, RAW and LONG RAW columns.                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `void`                                                                                                  | `registerOutParameter``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, int sqlType, int scale, int maxLength)`<br>Special Oracle version of registerOutParameter for registering CHAR, VARCHAR, LONG, RAW and LONG RAW columns.                                                                                                                                                                                                                                                                                                                                  |
    | `void`                                                                                                  | `registerOutParameterAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterMarkerName, int sqlType)`<br>Special Oracle method to registerOutParameter by the parameterMarkerName of oracle style parameter markers instead of parameterIndex.                                                                                                                                                                                                                                                                                                                        |
    | `void`                                                                                                  | `registerOutParameterAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterMarkerName, int sqlType, int scale)`<br>Special Oracle method to registerOutParameter by the parameterMarkerName of oracle style parameter markers instead of parameterIndex.                                                                                                                                                                                                                                                                                                             |
    | `void`                                                                                                  | `registerOutParameterAtName``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterMarkerName, int sqlType, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` typeName)`<br>Special Oracle method to registerOutParameter by the parameterMarkerName of oracle style parameter markers instead of parameterIndex.                                                                                                                                                                                                            |
    | `void`                                                                                                  | `registerOutParameterBytes``(int paramIndex, int sqlType, int scale, int maxLength)`<br>Deprecated. <br>As of Oracle 10g Release 1 all character values are measured in Java chars so this method is no longer supported. It now is the equivalent of calling registerOutParameter with the same args. Since the number of bytes is at least as large as the number of characters this will always work although it may waste memory. Use registerOutParameter with the number of Java chars instead.                                                                                                                              |
    | `void`                                                                                                  | `registerOutParameterChars``(int paramIndex, int sqlType, int scale, int maxLength)`<br>Deprecated. <br>As of Oracle 10g Release 1 all character values are measured in Java chars so this method is no longer needed. Call registerOutParameter with the same args instead.                                                                                                                                                                                                                                                                                                                                                       |
    | `int`                                                                                                   | `sendBatch``()`<br>Send the sets of parameters batched (for Oracle-style batching only).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `void`                                                                                                  | `setArray``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Array`](http://download.oracle.com/javase/8/docs/api/java/sql/Array.html?is-external=true)` x)`<br>Sets the designated parameter to an `java.sql.Array`value.                                                                                                                                                                                                                                                                                                                                      |
    | `void`                                                                                                  | `setARRAY``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`ARRAY`](../sql/ARRAY.md)` x)`<br>Sets the designated parameter to an `oracle.sql.ARRAY`value.                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `void`                                                                                                  | `setAsciiStream``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` x, int y)`<br>Sets the designated parameter to the given input stream, which will have the specified number of bytes.                                                                                                                                                                                                                                                                 |
    | `void`                                                                                                  | `setBfile``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`BFILE`](../sql/BFILE.md)` x)`<br>Sets the designated parameter to an `oracle.sql.BFILE`value.                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `void`                                                                                                  | `setBFILE``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`BFILE`](../sql/BFILE.md)` x)`<br>Sets the designated parameter to an `oracle.sql.BFILE`value.                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `void`                                                                                                  | `setBigDecimal``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`BigDecimal`](http://download.oracle.com/javase/8/docs/api/java/math/BigDecimal.html?is-external=true)` x)`<br>Sets the designated parameter to the given `java.math.BigDecimal` value.                                                                                                                                                                                                                                                                                                        |
    | `void`                                                                                                  | `setBinaryDouble``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`BINARY_DOUBLE`](../sql/BINARY_DOUBLE.md)` x)`<br>Sets the designated parameter to the given `oracle.sql.BINARY_FLOAT` value.                                                                                                                                                                                                                                                                                                                                                                |
    | `void`                                                                                                  | `setBinaryDouble``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, double x)`<br>Sets the designated parameter to the given `oracle.sql.BINARY_FLOAT` value.                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `void`                                                                                                  | `setBinaryFloat``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`BINARY_FLOAT`](../sql/BINARY_FLOAT.md)` x)`<br>Sets the designated parameter to the given `oracle.sql.BINARY_FLOAT` value.                                                                                                                                                                                                                                                                                                                                                                   |
    | `void`                                                                                                  | `setBinaryFloat``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, float x)`<br>Sets the designated parameter to the given Java `float` value.                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `void`                                                                                                  | `setBinaryStream``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` x, int y)`<br>Sets the designated parameter to the given input stream, which will have the specified number of bytes.                                                                                                                                                                                                                                                                |
    | `void`                                                                                                  | `setBlob``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Blob`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true)` x)`<br>Sets the designated parameter to an `java.sql.Blob`value.                                                                                                                                                                                                                                                                                                                                          |
    | `void`                                                                                                  | `setBLOB``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`BLOB`](../sql/BLOB.md)` x)`<br>Sets the designated parameter to an `oracle.sql.BLOB`value.                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `void`                                                                                                  | `setBoolean``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, boolean x)`<br>Sets the designated parameter to the given Java `boolean` value.                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `void`                                                                                                  | `setByte``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, byte x)`<br>Sets the designated parameter to the given Java `byte` value.                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `void`                                                                                                  | `setBytes``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, byte[] x)`<br>Sets the designated parameter to the given Java array of bytes.                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `void`                                                                                                  | `setBytesForBlob``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, byte[] x)`<br>Sets the designated parameter to the given Java `byte[]` value.                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `void`                                                                                                  | `setCHAR``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`CHAR`](../sql/CHAR.md)` x)`<br>Sets the designated parameter to an `oracle.sql.CHAR`value.                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `void`                                                                                                  | `setCharacterStream``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Reader`](http://download.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)` x, int y)`<br>Sets the designated parameter to the given `Reader` object, which is the given number of characters long.                                                                                                                                                                                                                                                                     |
    | `void`                                                                                                  | `setClob``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Clob`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true)` x)`<br>Sets the designated parameter to an `java.sql.Clob`value.                                                                                                                                                                                                                                                                                                                                          |
    | `void`                                                                                                  | `setCLOB``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`CLOB`](../sql/CLOB.md)` x)`<br>Sets the designated parameter to an `oracle.sql.CLOB`value.                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `void`                                                                                                  | `setCursor``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true)` x)`<br>Sets the designated parameter to a Java Cursor value.                                                                                                                                                                                                                                                                                                                                  |
    | `void`                                                                                                  | `setCustomDatum``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`CustomDatum`](../sql/CustomDatum.md)` x)`<br>Sets the designated parameter to an `oracle.sql.CustomDatum`value.                                                                                                                                                                                                                                                                                                                                                                              |
    | `void`                                                                                                  | `setDate``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)` x)`<br>Sets the designated parameter to the given `java.sql.Date` value.                                                                                                                                                                                                                                                                                                                                  |
    | `void`                                                                                                  | `setDATE``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`DATE`](../sql/DATE.md)` x)`<br>Sets the designated parameter to an `oracle.sql.DATE`value.                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `void`                                                                                                  | `setDate``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Date`](http://download.oracle.com/javase/8/docs/api/java/sql/Date.html?is-external=true)` x, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Sets the designated parameter to the given `java.sql.Date` value, using the given `Calendar` object.                                                                                                                                                                                    |
    | `void`                                                                                                  | `setDouble``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, double x)`<br>Sets the designated parameter to the given Java `double` value.                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `void`                                                                                                  | `setExecuteBatch``(int nrows)`<br>Deprecated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `void`                                                                                                  | `setFixedCHAR``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` x)`<br>Sets the designated parameter to a `String` See the javadoc for the setFixedChar(int, String) method in OraclePreparedStatement.                                                                                                                                                                                                                                                         |
    | `void`                                                                                                  | `setFloat``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, float x)`<br>Sets the designated parameter to the given Java `float` value.                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `void`                                                                                                  | `setInt``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, int x)`<br>Sets the designated parameter to the given Java `int` value.                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `void`                                                                                                  | `setINTERVALDS``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`INTERVALDS`](../sql/INTERVALDS.md)` x)`<br>Sets the designated parameter to an `oracle.sql.INTERVALDS`value.                                                                                                                                                                                                                                                                                                                                                                                  |
    | `void`                                                                                                  | `setINTERVALYM``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`INTERVALYM`](../sql/INTERVALYM.md)` x)`<br>Sets the designated parameter to an `oracle.sql.INTERVALYM`value.                                                                                                                                                                                                                                                                                                                                                                                  |
    | `void`                                                                                                  | `setLong``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, long x)`<br>Sets the designated parameter to the given Java `long` value.                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `void`                                                                                                  | `setNull``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, int sqlType)`<br>Sets the designated parameter to SQL `NULL`.                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `void`                                                                                                  | `setNull``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, int sqlType, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` typeName)`<br>Sets the designated parameter to SQL `NULL`.                                                                                                                                                                                                                                                                                                                              |
    | `void`                                                                                                  | `setNUMBER``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`NUMBER`](../sql/NUMBER.md)` x)`<br>Sets the designated parameter to an `oracle.sql.NUMBER`value.                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `void`                                                                                                  | `setObject``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` x)`<br>Sets the value of the designated parameter with the given object.                                                                                                                                                                                                                                                                                                                           |
    | `void`                                                                                                  | `setObject``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` x, int y)`<br>Sets the value of the designated parameter with the given object.                                                                                                                                                                                                                                                                                                                    |
    | `void`                                                                                                  | `setObject``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)` x, int targetSqlType, int scale)`<br>Sets the value of the designated parameter with the given object.                                                                                                                                                                                                                                                                                             |
    | `void`                                                                                                  | `setOPAQUE``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`OPAQUE`](../sql/OPAQUE.md)` x)`<br>Sets the designated parameter to an `oracle.sql.OPAQUE`value.                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `void`                                                                                                  | `setOracleObject``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Datum`](../sql/Datum.md)` x)`<br>Sets the designated parameter to an `oracle.sql.Datum`value.                                                                                                                                                                                                                                                                                                                                                                                               |
    | `void`                                                                                                  | `setORAData``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`ORAData`](../sql/ORAData.md)` x)`<br>Sets the designated parameter to an `oracle.sql.ORAData`value.                                                                                                                                                                                                                                                                                                                                                                                              |
    | `void`                                                                                                  | `setRAW``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`RAW`](../sql/RAW.md)` x)`<br>Sets the designated parameter to an `oracle.sql.RAW`value.                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `void`                                                                                                  | `setRef``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Ref`](http://download.oracle.com/javase/8/docs/api/java/sql/Ref.html?is-external=true)` x)`<br>Sets the designated parameter to an `jdbc.sql.Ref`value.                                                                                                                                                                                                                                                                                                                                              |
    | `void`                                                                                                  | `setREF``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`REF`](../sql/REF.md)` x)`<br>Sets the designated parameter to an `oracle.sql.REF`value.                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `void`                                                                                                  | `setRefType``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`REF`](../sql/REF.md)` x)`<br>Sets the designated parameter to an `oracle.sql.REF`value.                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `void`                                                                                                  | `setROWID``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`ROWID`](../sql/ROWID.md)` x)`<br>Sets the designated parameter to an `oracle.sql.ROWID`value.                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `void`                                                                                                  | `setShort``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, short x)`<br>Sets the designated parameter to the given Java `short` value.                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `void`                                                                                                  | `setString``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` x)`<br>Sets the designated parameter to the given Java `String` value.                                                                                                                                                                                                                                                                                                                             |
    | `void`                                                                                                  | `setStringForClob``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` x)`<br>Sets the designated parameter to the given Java `String` value.                                                                                                                                                                                                                                                                                                                      |
    | `void`                                                                                                  | `setSTRUCT``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`STRUCT`](../sql/STRUCT.md)` x)`<br>Sets the designated parameter to an `oracle.sql.STRUCT`value.                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `void`                                                                                                  | `setStructDescriptor``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`StructDescriptor`](../sql/StructDescriptor.md)` x)`                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `void`                                                                                                  | `setTime``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)` x)`<br>Sets the designated parameter to the given `java.sql.Time` value.                                                                                                                                                                                                                                                                                                                                  |
    | `void`                                                                                                  | `setTime``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Time`](http://download.oracle.com/javase/8/docs/api/java/sql/Time.html?is-external=true)` x, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Sets the designated parameter to the given `java.sql.Time` value, using the given `Calendar` object.                                                                                                                                                                                    |
    | `void`                                                                                                  | `setTimestamp``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` x)`<br>Sets the designated parameter to the given `java.sql.Timestamp` value.                                                                                                                                                                                                                                                                                                              |
    | `void`                                                                                                  | `setTIMESTAMP``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`TIMESTAMP`](../sql/TIMESTAMP.md)` x)`<br>Sets the designated parameter to an `oracle.sql.TIMESTAMP`value.                                                                                                                                                                                                                                                                                                                                                                                      |
    | `void`                                                                                                  | `setTimestamp``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`Timestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/Timestamp.html?is-external=true)` x, `[`Calendar`](http://download.oracle.com/javase/8/docs/api/java/util/Calendar.html?is-external=true)` cal)`<br>Sets the designated parameter to the given `java.sql.Timestamp` value, using the given `Calendar` object.                                                                                                                                                                |
    | `void`                                                                                                  | `setTIMESTAMPLTZ``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`TIMESTAMPLTZ`](../sql/TIMESTAMPLTZ.md)` x)`<br>Sets the designated parameter to an `oracle.sql.TIMESTAMPLTZ`value.                                                                                                                                                                                                                                                                                                                                                                          |
    | `void`                                                                                                  | `setTIMESTAMPTZ``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`TIMESTAMPTZ`](../sql/TIMESTAMPTZ.md)` x)`<br>Sets the designated parameter to an `oracle.sql.TIMESTAMPTZ`value.                                                                                                                                                                                                                                                                                                                                                                              |
    | `void`                                                                                                  | `setUnicodeStream``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)` x, int y)`<br>Sets the designated parameter to a Java UnicodeStream value.                                                                                                                                                                                                                                                                                                          |
    | `void`                                                                                                  | `setURL``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` parameterName, `[`URL`](http://download.oracle.com/javase/8/docs/api/java/net/URL.html?is-external=true)` x)`<br>Sets the designated parameter to the given `java.net.URL` object.                                                                                                                                                                                                                                                                                                                                     |

    - ### Methods inherited from interface java.sql.[CallableStatement](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)

      [`getArray`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getArray_int_)`, `[`getArray`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getArray_java_lang_String_)`, `[`getBigDecimal`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getBigDecimal_int_)`, `[`getBigDecimal`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getBigDecimal_int_int_)`, `[`getBigDecimal`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getBigDecimal_java_lang_String_)`, `[`getBlob`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getBlob_int_)`, `[`getBlob`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getBlob_java_lang_String_)`, `[`getBoolean`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getBoolean_int_)`, `[`getBoolean`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getBoolean_java_lang_String_)`, `[`getByte`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getByte_int_)`, `[`getByte`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getByte_java_lang_String_)`, `[`getBytes`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getBytes_int_)`, `[`getBytes`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getBytes_java_lang_String_)`, `[`getCharacterStream`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getCharacterStream_java_lang_String_)`, `[`getClob`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getClob_int_)`, `[`getClob`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getClob_java_lang_String_)`, `[`getDate`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getDate_int_)`, `[`getDate`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getDate_int_java_util_Calendar_)`, `[`getDate`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getDate_java_lang_String_)`, `[`getDate`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getDate_java_lang_String_java_util_Calendar_)`, `[`getDouble`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getDouble_int_)`, `[`getDouble`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getDouble_java_lang_String_)`, `[`getFloat`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getFloat_int_)`, `[`getFloat`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getFloat_java_lang_String_)`, `[`getInt`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getInt_int_)`, `[`getInt`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getInt_java_lang_String_)`, `[`getLong`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getLong_int_)`, `[`getLong`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getLong_java_lang_String_)`, `[`getNCharacterStream`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getNCharacterStream_int_)`, `[`getNCharacterStream`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getNCharacterStream_java_lang_String_)`, `[`getNClob`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getNClob_int_)`, `[`getNClob`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getNClob_java_lang_String_)`, `[`getNString`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getNString_int_)`, `[`getNString`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getNString_java_lang_String_)`, `[`getObject`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getObject_int_)`, `[`getObject`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getObject_int_java_lang_Class_)`, `[`getObject`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getObject_int_java_util_Map_)`, `[`getObject`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getObject_java_lang_String_)`, `[`getObject`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getObject_java_lang_String_java_lang_Class_)`, `[`getObject`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getObject_java_lang_String_java_util_Map_)`, `[`getRef`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getRef_int_)`, `[`getRef`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getRef_java_lang_String_)`, `[`getRowId`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getRowId_int_)`, `[`getRowId`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getRowId_java_lang_String_)`, `[`getShort`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getShort_int_)`, `[`getShort`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getShort_java_lang_String_)`, `[`getSQLXML`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getSQLXML_int_)`, `[`getSQLXML`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getSQLXML_java_lang_String_)`, `[`getString`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getString_int_)`, `[`getString`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getString_java_lang_String_)`, `[`getTime`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getTime_int_)`, `[`getTime`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getTime_int_java_util_Calendar_)`, `[`getTime`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getTime_java_lang_String_)`, `[`getTime`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getTime_java_lang_String_java_util_Calendar_)`, `[`getTimestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getTimestamp_int_)`, `[`getTimestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getTimestamp_int_java_util_Calendar_)`, `[`getTimestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getTimestamp_java_lang_String_)`, `[`getTimestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getTimestamp_java_lang_String_java_util_Calendar_)`, `[`getURL`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getURL_int_)`, `[`getURL`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getURL_java_lang_String_)`, `[`registerOutParameter`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#registerOutParameter_int_int_)`, `[`registerOutParameter`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#registerOutParameter_int_int_int_)`, `[`registerOutParameter`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#registerOutParameter_int_int_java_lang_String_)`, `[`registerOutParameter`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#registerOutParameter_int_java_sql_SQLType_)`, `[`registerOutParameter`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#registerOutParameter_int_java_sql_SQLType_int_)`, `[`registerOutParameter`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#registerOutParameter_int_java_sql_SQLType_java_lang_String_)`, `[`registerOutParameter`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#registerOutParameter_java_lang_String_int_)`, `[`registerOutParameter`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#registerOutParameter_java_lang_String_int_int_)`, `[`registerOutParameter`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#registerOutParameter_java_lang_String_int_java_lang_String_)`, `[`registerOutParameter`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#registerOutParameter_java_lang_String_java_sql_SQLType_)`, `[`registerOutParameter`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#registerOutParameter_java_lang_String_java_sql_SQLType_int_)`, `[`registerOutParameter`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#registerOutParameter_java_lang_String_java_sql_SQLType_java_lang_String_)`, `[`setAsciiStream`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setAsciiStream_java_lang_String_java_io_InputStream_)`, `[`setAsciiStream`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setAsciiStream_java_lang_String_java_io_InputStream_long_)`, `[`setBinaryStream`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setBinaryStream_java_lang_String_java_io_InputStream_)`, `[`setBinaryStream`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setBinaryStream_java_lang_String_java_io_InputStream_long_)`, `[`setBlob`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setBlob_java_lang_String_java_io_InputStream_)`, `[`setBlob`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setBlob_java_lang_String_java_io_InputStream_long_)`, `[`setCharacterStream`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setCharacterStream_java_lang_String_java_io_Reader_)`, `[`setCharacterStream`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setCharacterStream_java_lang_String_java_io_Reader_long_)`, `[`setClob`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setClob_java_lang_String_java_io_Reader_)`, `[`setClob`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setClob_java_lang_String_java_io_Reader_long_)`, `[`setNCharacterStream`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setNCharacterStream_java_lang_String_java_io_Reader_)`, `[`setNCharacterStream`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setNCharacterStream_java_lang_String_java_io_Reader_long_)`, `[`setNClob`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setNClob_java_lang_String_java_sql_NClob_)`, `[`setNClob`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setNClob_java_lang_String_java_io_Reader_)`, `[`setNClob`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setNClob_java_lang_String_java_io_Reader_long_)`, `[`setNString`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setNString_java_lang_String_java_lang_String_)`, `[`setObject`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setObject_java_lang_String_java_lang_Object_java_sql_SQLType_)`, `[`setObject`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setObject_java_lang_String_java_lang_Object_java_sql_SQLType_int_)`, `[`setRowId`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setRowId_java_lang_String_java_sql_RowId_)`, `[`setSQLXML`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setSQLXML_java_lang_String_java_sql_SQLXML_)`, `[`wasNull`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#wasNull__)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.[OraclePreparedStatement](OraclePreparedStatement.md)

      [`defineParameterType`](OraclePreparedStatement.md)`, `[`defineParameterTypeBytes`](OraclePreparedStatement.md)`, `[`defineParameterTypeChars`](OraclePreparedStatement.md)`, `[`getExecuteBatch`](OraclePreparedStatement.md)`, `[`getReturnResultSet`](OraclePreparedStatement.md)`, `[`OracleGetParameterMetaData`](OraclePreparedStatement.md)`, `[`registerReturnParameter`](OraclePreparedStatement.md)`, `[`registerReturnParameter`](OraclePreparedStatement.md)`, `[`registerReturnParameter`](OraclePreparedStatement.md)`, `[`setARRAY`](OraclePreparedStatement.md)`, `[`setArrayAtName`](OraclePreparedStatement.md)`, `[`setARRAYAtName`](OraclePreparedStatement.md)`, `[`setAsciiStreamAtName`](OraclePreparedStatement.md)`, `[`setAsciiStreamAtName`](OraclePreparedStatement.md)`, `[`setAsciiStreamAtName`](OraclePreparedStatement.md)`, `[`setBfile`](OraclePreparedStatement.md)`, `[`setBFILE`](OraclePreparedStatement.md)`, `[`setBfileAtName`](OraclePreparedStatement.md)`, `[`setBFILEAtName`](OraclePreparedStatement.md)`, `[`setBigDecimalAtName`](OraclePreparedStatement.md)`, `[`setBinaryDouble`](OraclePreparedStatement.md)`, `[`setBinaryDouble`](OraclePreparedStatement.md)`, `[`setBinaryDoubleAtName`](OraclePreparedStatement.md)`, `[`setBinaryDoubleAtName`](OraclePreparedStatement.md)`, `[`setBinaryFloat`](OraclePreparedStatement.md)`, `[`setBinaryFloat`](OraclePreparedStatement.md)`, `[`setBinaryFloatAtName`](OraclePreparedStatement.md)`, `[`setBinaryFloatAtName`](OraclePreparedStatement.md)`, `[`setBinaryStreamAtName`](OraclePreparedStatement.md)`, `[`setBinaryStreamAtName`](OraclePreparedStatement.md)`, `[`setBinaryStreamAtName`](OraclePreparedStatement.md)`, `[`setBLOB`](OraclePreparedStatement.md)`, `[`setBlobAtName`](OraclePreparedStatement.md)`, `[`setBLOBAtName`](OraclePreparedStatement.md)`, `[`setBlobAtName`](OraclePreparedStatement.md)`, `[`setBlobAtName`](OraclePreparedStatement.md)`, `[`setBooleanAtName`](OraclePreparedStatement.md)`, `[`setByteAtName`](OraclePreparedStatement.md)`, `[`setBytesAtName`](OraclePreparedStatement.md)`, `[`setBytesForBlob`](OraclePreparedStatement.md)`, `[`setBytesForBlobAtName`](OraclePreparedStatement.md)`, `[`setCHAR`](OraclePreparedStatement.md)`, `[`setCharacterStreamAtName`](OraclePreparedStatement.md)`, `[`setCharacterStreamAtName`](OraclePreparedStatement.md)`, `[`setCHARAtName`](OraclePreparedStatement.md)`, `[`setCheckBindTypes`](OraclePreparedStatement.md)`, `[`setCLOB`](OraclePreparedStatement.md)`, `[`setClobAtName`](OraclePreparedStatement.md)`, `[`setCLOBAtName`](OraclePreparedStatement.md)`, `[`setClobAtName`](OraclePreparedStatement.md)`, `[`setClobAtName`](OraclePreparedStatement.md)`, `[`setCursor`](OraclePreparedStatement.md)`, `[`setCursorAtName`](OraclePreparedStatement.md)`, `[`setCustomDatum`](OraclePreparedStatement.md)`, `[`setCustomDatumAtName`](OraclePreparedStatement.md)`, `[`setDATE`](OraclePreparedStatement.md)`, `[`setDateAtName`](OraclePreparedStatement.md)`, `[`setDATEAtName`](OraclePreparedStatement.md)`, `[`setDateAtName`](OraclePreparedStatement.md)`, `[`setDisableStmtCaching`](OraclePreparedStatement.md)`, `[`setDoubleAtName`](OraclePreparedStatement.md)`, `[`setFixedCHAR`](OraclePreparedStatement.md)`, `[`setFixedCHARAtName`](OraclePreparedStatement.md)`, `[`setFloatAtName`](OraclePreparedStatement.md)`, `[`setFormOfUse`](OraclePreparedStatement.md)`, `[`setIntAtName`](OraclePreparedStatement.md)`, `[`setINTERVALDS`](OraclePreparedStatement.md)`, `[`setINTERVALDSAtName`](OraclePreparedStatement.md)`, `[`setINTERVALYM`](OraclePreparedStatement.md)`, `[`setINTERVALYMAtName`](OraclePreparedStatement.md)`, `[`setLongAtName`](OraclePreparedStatement.md)`, `[`setNCharacterStreamAtName`](OraclePreparedStatement.md)`, `[`setNCharacterStreamAtName`](OraclePreparedStatement.md)`, `[`setNClobAtName`](OraclePreparedStatement.md)`, `[`setNClobAtName`](OraclePreparedStatement.md)`, `[`setNClobAtName`](OraclePreparedStatement.md)`, `[`setNStringAtName`](OraclePreparedStatement.md)`, `[`setNullAtName`](OraclePreparedStatement.md)`, `[`setNullAtName`](OraclePreparedStatement.md)`, `[`setNUMBER`](OraclePreparedStatement.md)`, `[`setNUMBERAtName`](OraclePreparedStatement.md)`, `[`setObjectAtName`](OraclePreparedStatement.md)`, `[`setObjectAtName`](OraclePreparedStatement.md)`, `[`setObjectAtName`](OraclePreparedStatement.md)`, `[`setOPAQUE`](OraclePreparedStatement.md)`, `[`setOPAQUEAtName`](OraclePreparedStatement.md)`, `[`setOracleObject`](OraclePreparedStatement.md)`, `[`setOracleObjectAtName`](OraclePreparedStatement.md)`, `[`setORAData`](OraclePreparedStatement.md)`, `[`setORADataAtName`](OraclePreparedStatement.md)`, `[`setPlsqlIndexTable`](OraclePreparedStatement.md)`, `[`setRAW`](OraclePreparedStatement.md)`, `[`setRAWAtName`](OraclePreparedStatement.md)`, `[`setREF`](OraclePreparedStatement.md)`, `[`setRefAtName`](OraclePreparedStatement.md)`, `[`setREFAtName`](OraclePreparedStatement.md)`, `[`setRefType`](OraclePreparedStatement.md)`, `[`setRefTypeAtName`](OraclePreparedStatement.md)`, `[`setROWID`](OraclePreparedStatement.md)`, `[`setRowIdAtName`](OraclePreparedStatement.md)`, `[`setROWIDAtName`](OraclePreparedStatement.md)`, `[`setShortAtName`](OraclePreparedStatement.md)`, `[`setSQLXMLAtName`](OraclePreparedStatement.md)`, `[`setStringAtName`](OraclePreparedStatement.md)`, `[`setStringForClob`](OraclePreparedStatement.md)`, `[`setStringForClobAtName`](OraclePreparedStatement.md)`, `[`setSTRUCT`](OraclePreparedStatement.md)`, `[`setSTRUCTAtName`](OraclePreparedStatement.md)`, `[`setStructDescriptor`](OraclePreparedStatement.md)`, `[`setStructDescriptorAtName`](OraclePreparedStatement.md)`, `[`setTimeAtName`](OraclePreparedStatement.md)`, `[`setTimeAtName`](OraclePreparedStatement.md)`, `[`setTIMESTAMP`](OraclePreparedStatement.md)`, `[`setTimestampAtName`](OraclePreparedStatement.md)`, `[`setTIMESTAMPAtName`](OraclePreparedStatement.md)`, `[`setTimestampAtName`](OraclePreparedStatement.md)`, `[`setTIMESTAMPLTZ`](OraclePreparedStatement.md)`, `[`setTIMESTAMPLTZAtName`](OraclePreparedStatement.md)`, `[`setTIMESTAMPTZ`](OraclePreparedStatement.md)`, `[`setTIMESTAMPTZAtName`](OraclePreparedStatement.md)`, `[`setUnicodeStreamAtName`](OraclePreparedStatement.md)`, `[`setURLAtName`](OraclePreparedStatement.md)

    <!-- -->

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

- - ### Method Detail

    - #### getARRAY

          ARRAY getARRAY(int parameterIndex)
                  throws SQLException

      Retrieves data into an `oracle.sql.ARRAY` object.
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, and so on

      Returns:
      data into an `ARRAY`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

    <!-- -->

    - #### getAsciiStream

          InputStream getAsciiStream(int parameterIndex)
                              throws SQLException

      Retrieves data into an `java.io.InputStream` object.
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, and so on

      Returns:
      data into an `java.io.InputStream`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

    <!-- -->

    - #### getBFILE

          BFILE getBFILE(int parameterIndex)
                  throws SQLException

      Retrieves data into an `oracle.sql.BFILE` object.
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, and so on

      Returns:
      data into an `oracle.sql.BFILE`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

    <!-- -->

    - #### getBfile

          BFILE getBfile(int parameterIndex)
                  throws SQLException

      Retrieves data into an `oracle.sql.BFILE` object.
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, and so on

      Returns:
      data into an `oracle.sql.BFILE`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

    <!-- -->

    - #### getBinaryStream

          InputStream getBinaryStream(int parameterIndex)
                               throws SQLException

      Retrieves data into an `java.io.InputStream` object.
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, and so on

      Returns:
      data into an `java.io.InputStream`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

    <!-- -->

    - #### getBinaryStream

          InputStream getBinaryStream(String parameterName)
                               throws SQLException

      Retrieves data into an `java.io.InputStream` object.
      Parameters:
      `parameterName` - the name of the stored procedure formal parameter

      Returns:
      data into an `java.io.InputStream`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

    <!-- -->

    - #### getBLOB

          BLOB getBLOB(int parameterIndex)
                throws SQLException

      Retrieves data into an `oracle.sql.BLOB` object.
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, and so on

      Returns:
      data into an `oracle.sql.BLOB`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

    <!-- -->

    - #### getCHAR

          CHAR getCHAR(int parameterIndex)
                throws SQLException

      Retrieves data into an `oracle.sql.CHAR` object.
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, and so on

      Returns:
      data into an `oracle.sql.CHAR`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

    <!-- -->

    - #### getCharacterStream

          Reader getCharacterStream(int parameterIndex)
                             throws SQLException

      Retrieves data into an `java.io.Reader` object.
      Specified by:
      [`getCharacterStream`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getCharacterStream_int_) in interface [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)

      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, and so on

      Returns:
      data into an `java.io.Reader`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

    <!-- -->

    - #### getCLOB

          CLOB getCLOB(int parameterIndex)
                throws SQLException

      Retrieves data into an `oracle.sql.CLOB` object.
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, and so on

      Returns:
      data into an `oracle.sql.CLOB`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

    <!-- -->

    - #### getCursor

          ResultSet getCursor(int parameterIndex)
                       throws SQLException

      Retrieves data into an `java.sql.ResultSet` object.
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, and so on

      Returns:
      data into an `java.sql.ResultSet`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

    <!-- -->

    - #### getCustomDatum

          Object getCustomDatum(int parameterIndex,
                                CustomDatumFactory factory)
                         throws SQLException

      Deprecated. 
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, and so on

      `factory` -

      Returns:
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

    <!-- -->

    - #### getORAData

          Object getORAData(int parameterIndex,
                            ORADataFactory factory)
                     throws SQLException

      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, and so on

      `factory` -

      Returns:
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

    <!-- -->

    - #### getObject

          Object getObject(int parameterIndex,
                           OracleDataFactory factory)
                    throws SQLException

      Returns an instance of `OracleData`, which is returned by the factory's "create" method
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, and so on

      `factory` -

      Returns:
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

    <!-- -->

    - #### getAnyDataEmbeddedObject

          Object getAnyDataEmbeddedObject(int parameterIndex)
                                   throws SQLException

      Deprecated. As of Oracle 11R1 there is full support for ANYTYPE and ANYDATA. Please use oracle.sql.ANYDATA for new code and plan on replacing any use of this method by the next major release. Note that in 11R1 this method is reimplemnted using the ANYDATA support and will now also function in all the drivers, not just oci. In the previous implementation it was possible to call registerOutParameter with a sqlType of either oracle.jdbc.OracleTypes.OPAQUE or oracle.jdbc.OracleTypes.STRUCT The new implemention requires the correct type which is OPAQUE.
      Retrieves data of an embedded object within AnyData
      Parameters:
      `parameterIndex` - the first parameter is 1

      Returns:
      data depending on the embedded type in AnyData

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

    <!-- -->

    - #### getDATE

          DATE getDATE(int parameterIndex)
                throws SQLException

      Retrieves data into an `oracle.sql.DATE` object.
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, and so on

      Returns:
      data into an `oracle.sql.DATE`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

    <!-- -->

    - #### getNUMBER

          NUMBER getNUMBER(int parameterIndex)
                    throws SQLException

      Retrieves data into an `oracle.sql.NUMBER` object.
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, and so on

      Returns:
      data into an `oracle.sql.NUMBER`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

    <!-- -->

    - #### getOPAQUE

          OPAQUE getOPAQUE(int parameterIndex)
                    throws SQLException

      Retrieves data into an `oracle.sql.OPAQUE` object.
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, and so on

      Returns:
      data into an `oracle.sql.OPAQUE`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

    <!-- -->

    - #### getOracleObject

          Datum getOracleObject(int parameterIndex)
                         throws SQLException

      Retrieves data into an `oracle.sql.Datum` object.
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, and so on

      Returns:
      data into an `oracle.sql.Datum`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

    <!-- -->

    - #### getRAW

          RAW getRAW(int parameterIndex)
              throws SQLException

      Retrieves data into an `oracle.sql.RAW` object.
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, and so on

      Returns:
      data into an `oracle.sql.RAW`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

    <!-- -->

    - #### getREF

          REF getREF(int parameterIndex)
              throws SQLException

      Retrieves data into an `oracle.sql.REF` object.
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, and so on

      Returns:
      data into an `oracle.sql.REF`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

    <!-- -->

    - #### getROWID

          ROWID getROWID(int parameterIndex)
                  throws SQLException

      Retrieves data into an `oracle.sql.ROWID` object.
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, and so on

      Returns:
      data into an `oracle.sql.ROWID`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

    <!-- -->

    - #### getSTRUCT

          STRUCT getSTRUCT(int parameterIndex)
                    throws SQLException

      Retrieves data into an `oracle.sql.STRUCT` object.
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, and so on

      Returns:
      data into an `oracle.sql.STRUCT`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

    <!-- -->

    - #### getINTERVALYM

          INTERVALYM getINTERVALYM(int parameterIndex)
                            throws SQLException

      Retrieves data into an `oracle.sql.INTERVALYM` object.
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, and so on

      Returns:
      data into an `oracle.sql.INTERVALYM`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

      Since:
      9i

    <!-- -->

    - #### getINTERVALDS

          INTERVALDS getINTERVALDS(int parameterIndex)
                            throws SQLException

      Retrieves data into an `oracle.sql.INTERVALDS` object.
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, and so on

      Returns:
      data into an `oracle.sql.INTERVALDS`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

      Since:
      10i

    <!-- -->

    - #### getTIMESTAMP

          TIMESTAMP getTIMESTAMP(int paramIdx)
                          throws SQLException

      Retrieves data into an `oracle.sql.TIMESTAMP` object.
      Parameters:
      `paramIdx` - the first parameter is 1, the second is 2, and so on

      Returns:
      data into an `oracle.sql.TIMESTAMP`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

      Since:
      9i

    <!-- -->

    - #### getTIMESTAMPTZ

          TIMESTAMPTZ getTIMESTAMPTZ(int paramIdx)
                              throws SQLException

      Retrieves data into an `oracle.sql.TIMESTAMPTZ` object.
      Parameters:
      `paramIdx` - the first parameter is 1, the second is 2, and so on

      Returns:
      data into an `oracle.sql.TIMESTAMPTZ`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

      Since:
      9i

    <!-- -->

    - #### getTIMESTAMPLTZ

          TIMESTAMPLTZ getTIMESTAMPLTZ(int paramIdx)
                                throws SQLException

      Retrieves data into an `oracle.sql.TIMESTAMPLTZ` object.
      Parameters:
      `paramIdx` - the first parameter is 1, the second is 2, and so on

      Returns:
      data into an `oracle.sql.TIMESTAMPLTZ`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

      Since:
      9i

    <!-- -->

    - #### getUnicodeStream

          InputStream getUnicodeStream(int parameterIndex)
                                throws SQLException

      Retrieves data into an `java.io.InputStream` object.
      Parameters:
      `parameterIndex` - the first parameter is 1, the second is 2, and so on

      Returns:
      data into an `java.io.InputStream`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

    <!-- -->

    - #### getUnicodeStream

          InputStream getUnicodeStream(String parameterName)
                                throws SQLException

      Retrieves data into an `java.io.InputStream` object.
      Parameters:
      `parameterName` - the name of the stored procedure formal parameter

      Returns:
      data into an `java.io.InputStream`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

    <!-- -->

    - #### registerOutParameter

          void registerOutParameter(int paramIndex,
                                    int sqlType,
                                    int scale,
                                    int maxLength)
                             throws SQLException

      Special Oracle version of registerOutParameter for registering CHAR, VARCHAR, LONG, RAW and LONG RAW columns. Depending on the value of OracleConnection.getDataSizeUnits(), maxLength will be measured in bytes or characters.
      Parameters:
      `paramIndex` - parameter index (the first parameter is 1).

      `sqlType` - type of the bind parameter

      `scale` - not used

      `maxLength` - maximum length of the column, specified in bytes or characters.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

    <!-- -->

    - #### registerOutParameterBytes

          void registerOutParameterBytes(int paramIndex,
                                         int sqlType,
                                         int scale,
                                         int maxLength)
                                  throws SQLException

      Deprecated. As of Oracle 10g Release 1 all character values are measured in Java chars so this method is no longer supported. It now is the equivalent of calling registerOutParameter with the same args. Since the number of bytes is at least as large as the number of characters this will always work although it may waste memory. Use registerOutParameter with the number of Java chars instead.
      Special Oracle version of registerOutParameter for registering CHAR, VARCHAR, LONG, RAW and LONG RAW columns. This version accepts a maxLength parameter measured in **bytes**.
      Parameters:
      `paramIndex` - parameter index (the first parameter is 1).

      `sqlType` - type of the bind parameter

      `scale` - not used

      `maxLength` - maximum length of the column, specified in bytes. If not specified, maximum length allowed for that type is used.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

    <!-- -->

    - #### registerOutParameterChars

          void registerOutParameterChars(int paramIndex,
                                         int sqlType,
                                         int scale,
                                         int maxLength)
                                  throws SQLException

      Deprecated. As of Oracle 10g Release 1 all character values are measured in Java chars so this method is no longer needed. Call registerOutParameter with the same args instead.
      Special Oracle version of registerOutParameter for registering CHAR, VARCHAR, LONG, RAW and LONG RAW columns. This version accepts a maxLength parameter measured in **characters**.
      Parameters:
      `paramIndex` - parameter index (the first parameter is 1).

      `sqlType` - type of the bind parameter

      `scale` - not used

      `maxLength` - maximum length of the column, specified in characters. If not specified, maximum length allowed for that type is used.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

    <!-- -->

    - #### sendBatch

          int sendBatch()
                 throws SQLException

      Send the sets of parameters batched (for Oracle-style batching only).
      Oracle-style batching is not supported for a callable statement. This method simply returns the number of valid rows.

      Specified by:
      [`sendBatch`](OraclePreparedStatement.md) in interface [`OraclePreparedStatement`](OraclePreparedStatement.md)

      Returns:
      the update count (always 0).

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

    <!-- -->

    - #### setExecuteBatch

          void setExecuteBatch(int nrows)
                        throws SQLException

      Deprecated. 
      Set the batch value (for Oracle-style batching only).
      Oracle-style batching is not supported for a callable statement. This method always sets the batch value to 1.

      Specified by:
      [`setExecuteBatch`](OraclePreparedStatement.md) in interface [`OraclePreparedStatement`](OraclePreparedStatement.md)

      Parameters:
      `nrows` - batch value to be set, this is discarded.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

      See Also:
      [`getExecuteBatch`](OraclePreparedStatement.md), [`OracleConnection.setDefaultExecuteBatch`](OracleConnection.md)

    <!-- -->

    - #### getPlsqlIndexTable

          @Deprecated
          Object getPlsqlIndexTable(int paramIndex)
                                         throws SQLException

      Deprecated. since 18.1. Use java.sql.CallableStatement.getObject(int parameterIndex) method.
      Get the value of a PLSQL Associative Array ( formerly known as index-by-table ) parameter as a Java array. The type of the Java arry will be the default Java object type corresponding to the element's SQL type, following the mapping for built-in types specified in the JDBC spec.
      Parameters:
      `paramIndex` - the first parameter is 1, the second is 2, and so on

      Returns:
      A java.lang.Object holding the parameter value.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database-access error occurs.

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

      See Also:
      `registerIndexTableOutParameter(int, int, int, int)`

    <!-- -->

    - #### getPlsqlIndexTable

          @Deprecated
          Object getPlsqlIndexTable(int paramIndex,
                                                Class primitiveType)
                                         throws SQLException

      Deprecated. since 18.1. Use java.sql.CallableStatement.getObject(int parameterIndex, Class\<T\> type) method.
      Get the value of a PLSQL Associative Array ( formerly known as index-by-table ) parameter as a primitive array. 'primitiveType' speicifies the return array type.
      Parameters:
      `paramIndex` - the first parameter is 1, the second is 2, and so on

      `primitiveType` - is a primitive type class. For example,java.lang.Double.Type

      Returns:
      A java.lang.Object holding the parameter value.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database-access error occurs.

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

      See Also:
      `registerIndexTableOutParameter(int, int, int, int)`

    <!-- -->

    - #### getOraclePlsqlIndexTable

          @Deprecated
          Datum[] getOraclePlsqlIndexTable(int paramIndex)
                                                throws SQLException

      Deprecated. since 18.1 Use java.sql.CallableStatement.getObject(int parameterIndex) method.
      Get the value of a PLSQL Associative Array ( formerly known as index-by-table ) parameter as a oracle.sql.Datum array.
      Parameters:
      `paramIndex` - the first parameter is 1, the second is 2, and so on

      Returns:
      A Datum array holding the parameter value.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database-access error occurs.

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

      See Also:
      `registerIndexTableOutParameter(int, int, int, int)`

    <!-- -->

    - #### registerIndexTableOutParameter

          @Deprecated
          void registerIndexTableOutParameter(int paramIndex,
                                                          int maxLen,
                                                          int elemSqlType,
                                                          int elemMaxLen)
                                                   throws SQLException

      Deprecated. since 18.1. Use java.sql.CallableStatement.registerOutParameter (int parameterIndex, int sqlType, String typeName).
      Special Oracle version of registerOutParameter for registering a limited form of PL/SQL Associative Array parameters. Associative Arrays were formerly called index-by-tables. In PL/SQL they are arrays of key-value pairs where the keys may be numeric or string types and the values may be any scalar type. The keys may be sparse. See the PL/SQL manual. The database only exports a limited form of this to the client where the keys must be numeric, positive and dense and the values can be only numeric or string. This API is supported by the oci and thin driver It is also supported by the server side internal driver with a limitation on the element length for string of 1999 characters. For oci and thin this is the same as the database limitation of 32767 characters.
      Parameters:
      `paramIndex` - the first parameter is 1, the second is 2, and so on

      `maxLen` - the maximum possible number of elements.

      `elemSqlType` - index table element SQL type (as defined in java.sql.Types or OracleTypes).

      `elemMaxLen` - maximum length of the element. If not specified, maximum length allowed for that type is used.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if sqlType is invalid, or an error occurred.

      Since:
      8.1.7

    <!-- -->

    - #### setBinaryFloat

          void setBinaryFloat(String parameterName,
                              BINARY_FLOAT x)
                       throws SQLException

      Sets the designated parameter to the given `oracle.sql.BINARY_FLOAT` value.
      Parameters:
      `the` - name of the stored procedure formal parameter

      `x` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      10.0

      See Also:
      [`CallableStatement.getFloat(int)`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getFloat_int_)

    <!-- -->

    - #### setBinaryDouble

          void setBinaryDouble(String parameterName,
                               BINARY_DOUBLE x)
                        throws SQLException

      Sets the designated parameter to the given `oracle.sql.BINARY_FLOAT` value.
      Parameters:
      `the` - name of the stored procedure formal parameter

      `x` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      10.0

      See Also:
      [`CallableStatement.getDouble(int)`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getDouble_int_)

    <!-- -->

    - #### setStringForClob

          void setStringForClob(String parameterName,
                                String x)
                         throws SQLException

      Sets the designated parameter to the given Java `String` value. The driver converts this to an SQL `VARCHAR` or `LONGVARCHAR` value (depending on the argument's size relative to the driver's limits on `VARCHAR` values) when it sends it to the database. If the string is larger than 32765 it is converted to a temporary clob and that is sent to the database. This clob conversion produces data truncation for columns of type `VARCHAR` and `LONGVARCHAR`. This is wrong.
      Parameters:
      `the` - name of the stored procedure formal parameter

      `x` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      10i Release 1

      See Also:
      [`CallableStatement.getString(int)`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getString_int_)

    <!-- -->

    - #### setBytesForBlob

          void setBytesForBlob(String parameterName,
                               byte[] x)
                        throws SQLException

      Sets the designated parameter to the given Java `byte[]` value. The driver converts this to an SQL `BINARY` or `LONGBINARY CHECK THIS` value (depending on the argument's size relative to the driver's limits on `VARCHAR` values) when it sends it to the database. If the byte array is larger than 32765 it is converted to a temporary blob and that is sent to the database. This blob conversion produces data truncation for columns of type `BINARY`..
      Parameters:
      `the` - name of the stored procedure formal parameter

      `x` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      10i Release 1

      See Also:
      [`CallableStatement.getString(int)`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getString_int_)

    <!-- -->

    - #### registerOutParameter

          void registerOutParameter(String parameterName,
                                    int sqlType,
                                    int scale,
                                    int maxLength)
                             throws SQLException

      Special Oracle version of registerOutParameter for registering CHAR, VARCHAR, LONG, RAW and LONG RAW columns. Depending on the value of OracleConnection.getDataSizeUnits(), maxLength will be measured in bytes or characters.
      Parameters:
      `parameterName` - the name of the parameter

      `sqlType` - SQL type code defined by `java.sql.Types`.

      `scale` - the desired number of digits to the right of the decimal point. It must be greater than or equal to zero.

      `maxLength` - maximum length of the column, specified in bytes or characters.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs (conversion or database-access error)

      Since:
      10i Release 1

    <!-- -->

    - #### setNull

          void setNull(String parameterName,
                       int sqlType,
                       String typeName)
                throws SQLException

      Sets the designated parameter to SQL `NULL`. This version of the method `setNull` should be used for user-defined types and REF type parameters. Examples of user-defined types include: STRUCT, DISTINCT, JAVA_OBJECT, and named array types.
      **Note:** To be portable, applications must give the SQL type code and the fully-qualified SQL type name when specifying a NULL user-defined or REF parameter. In the case of a user-defined type the name is the type name of the parameter itself. For a REF parameter, the name is the type name of the referenced type. If a JDBC driver does not need the type code or type name information, it may ignore it. Although it is intended for user-defined and Ref parameters, this method may be used to set a null parameter of any JDBC type. If the parameter does not have a user-defined or REF type, the given typeName is ignored.

      Specified by:
      [`setNull`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setNull_java_lang_String_int_java_lang_String_) in interface [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)

      Parameters:
      `the` - name of the stored procedure formal parameter

      `sqlType` - a value from `java.sql.Types`

      `typeName` - the fully-qualified name of an SQL user-defined type; ignored if the parameter is not a user-defined type or SQL `REF` value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      10i Release 1

    <!-- -->

    - #### setNull

          void setNull(String parameterName,
                       int sqlType)
                throws SQLException

      Sets the designated parameter to SQL `NULL`.
      **Note:** You must specify the parameter's SQL type.

      Specified by:
      [`setNull`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setNull_java_lang_String_int_) in interface [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)

      Parameters:
      `the` - name of the stored procedure formal parameter

      `sqlType` - the SQL type code defined in `java.sql.Types`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

    <!-- -->

    - #### setBoolean

          void setBoolean(String parameterName,
                          boolean x)
                   throws SQLException

      Sets the designated parameter to the given Java `boolean` value. The driver converts this to an SQL `BIT` value when it sends it to the database.
      Specified by:
      [`setBoolean`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setBoolean_java_lang_String_boolean_) in interface [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)

      Parameters:
      `the` - name of the stored procedure formal parameter

      `x` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

      See Also:
      [`CallableStatement.getBoolean(int)`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getBoolean_int_)

    <!-- -->

    - #### setByte

          void setByte(String parameterName,
                       byte x)
                throws SQLException

      Sets the designated parameter to the given Java `byte` value. The driver converts this to an SQL `TINYINT` value when it sends it to the database.
      Specified by:
      [`setByte`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setByte_java_lang_String_byte_) in interface [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)

      Parameters:
      `the` - name of the stored procedure formal parameter

      `x` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

      See Also:
      [`CallableStatement.getByte(int)`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getByte_int_)

    <!-- -->

    - #### setShort

          void setShort(String parameterName,
                        short x)
                 throws SQLException

      Sets the designated parameter to the given Java `short` value. The driver converts this to an SQL `SMALLINT` value when it sends it to the database.
      Specified by:
      [`setShort`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setShort_java_lang_String_short_) in interface [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)

      Parameters:
      `the` - name of the stored procedure formal parameter

      `x` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

      See Also:
      [`CallableStatement.getShort(int)`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getShort_int_)

    <!-- -->

    - #### setInt

          void setInt(String parameterName,
                      int x)
               throws SQLException

      Sets the designated parameter to the given Java `int` value. The driver converts this to an SQL `INTEGER` value when it sends it to the database.
      Specified by:
      [`setInt`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setInt_java_lang_String_int_) in interface [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)

      Parameters:
      `the` - name of the stored procedure formal parameter

      `x` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

      See Also:
      [`CallableStatement.getInt(int)`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getInt_int_)

    <!-- -->

    - #### setLong

          void setLong(String parameterName,
                       long x)
                throws SQLException

      Sets the designated parameter to the given Java `long` value. The driver converts this to an SQL `BIGINT` value when it sends it to the database.
      Specified by:
      [`setLong`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setLong_java_lang_String_long_) in interface [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)

      Parameters:
      `the` - name of the stored procedure formal parameter

      `x` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

      See Also:
      [`CallableStatement.getLong(int)`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getLong_int_)

    <!-- -->

    - #### setFloat

          void setFloat(String parameterName,
                        float x)
                 throws SQLException

      Sets the designated parameter to the given Java `float` value. The driver converts this to an SQL `FLOAT` value when it sends it to the database.
      Specified by:
      [`setFloat`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setFloat_java_lang_String_float_) in interface [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)

      Parameters:
      `the` - name of the stored procedure formal parameter

      `x` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

      See Also:
      [`CallableStatement.getFloat(int)`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getFloat_int_)

    <!-- -->

    - #### setBinaryFloat

          void setBinaryFloat(String parameterName,
                              float x)
                       throws SQLException

      Sets the designated parameter to the given Java `float` value. The driver converts this to an SQL `BINARY_FLOAT` value when it sends it to the database.
      Parameters:
      `the` - name of the stored procedure formal parameter

      `x` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      10.0

      See Also:
      [`CallableStatement.getFloat(int)`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getFloat_int_)

    <!-- -->

    - #### setBinaryDouble

          void setBinaryDouble(String parameterName,
                               double x)
                        throws SQLException

      Sets the designated parameter to the given `oracle.sql.BINARY_FLOAT` value.
      Parameters:
      `the` - name of the stored procedure formal parameter

      `x` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      10.0

      See Also:
      [`CallableStatement.getFloat(int)`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getFloat_int_)

    <!-- -->

    - #### setDouble

          void setDouble(String parameterName,
                         double x)
                  throws SQLException

      Sets the designated parameter to the given Java `double` value. The driver converts this to an SQL `DOUBLE` value when it sends it to the database.
      Specified by:
      [`setDouble`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setDouble_java_lang_String_double_) in interface [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)

      Parameters:
      `the` - name of the stored procedure formal parameter

      `x` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

      See Also:
      [`CallableStatement.getDouble(int)`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getDouble_int_)

    <!-- -->

    - #### setBigDecimal

          void setBigDecimal(String parameterName,
                             BigDecimal x)
                      throws SQLException

      Sets the designated parameter to the given `java.math.BigDecimal` value. The driver converts this to an SQL `NUMERIC` value when it sends it to the database.
      Specified by:
      [`setBigDecimal`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setBigDecimal_java_lang_String_java_math_BigDecimal_) in interface [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)

      Parameters:
      `the` - name of the stored procedure formal parameter

      `x` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

      See Also:
      [`CallableStatement.getBigDecimal(int, int)`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getBigDecimal_int_int_)

    <!-- -->

    - #### setString

          void setString(String parameterName,
                         String x)
                  throws SQLException

      Sets the designated parameter to the given Java `String` value. The driver converts this to an SQL `VARCHAR` or `LONGVARCHAR` value (depending on the argument's size relative to the driver's limits on `VARCHAR` values) when it sends it to the database.
      Specified by:
      [`setString`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setString_java_lang_String_java_lang_String_) in interface [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)

      Parameters:
      `the` - name of the stored procedure formal parameter

      `x` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

      See Also:
      [`CallableStatement.getString(int)`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getString_int_)

    <!-- -->

    - #### setFixedCHAR

          void setFixedCHAR(String parameterName,
                            String x)
                     throws SQLException

      Sets the designated parameter to a `String` See the javadoc for the setFixedChar(int, String) method in OraclePreparedStatement. Note that PL/SQL comparison operators do provide blank padding.
      Parameters:
      `parameterName` - the name of the stored procedure formal parameter

      `x` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setCursor

          void setCursor(String parameterName,
                         ResultSet x)
                  throws SQLException

      Sets the designated parameter to a Java Cursor value.
      Parameters:
      `parameterName` - the name of the stored procedure formal parameter

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setROWID

          void setROWID(String parameterName,
                        ROWID x)
                 throws SQLException

      Sets the designated parameter to an `oracle.sql.ROWID`value.
      Parameters:
      `parameterName` - the name of the stored procedure formal parameter

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setRAW

          void setRAW(String parameterName,
                      RAW x)
               throws SQLException

      Sets the designated parameter to an `oracle.sql.RAW`value.
      Parameters:
      `parameterName` - the name of the stored procedure formal parameter

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setCHAR

          void setCHAR(String parameterName,
                       CHAR x)
                throws SQLException

      Sets the designated parameter to an `oracle.sql.CHAR`value.
      Parameters:
      `parameterName` - the name of the stored procedure formal parameter

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setDATE

          void setDATE(String parameterName,
                       DATE x)
                throws SQLException

      Sets the designated parameter to an `oracle.sql.DATE`value.
      Parameters:
      `parameterName` - the name of the stored procedure formal parameter

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setNUMBER

          void setNUMBER(String parameterName,
                         NUMBER x)
                  throws SQLException

      Sets the designated parameter to an `oracle.sql.NUMBER`value.
      Parameters:
      `parameterName` - the name of the stored procedure formal parameter

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setBLOB

          void setBLOB(String parameterName,
                       BLOB x)
                throws SQLException

      Sets the designated parameter to an `oracle.sql.BLOB`value.
      Parameters:
      `parameterName` - the name of the stored procedure formal parameter

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setBlob

          void setBlob(String parameterName,
                       Blob x)
                throws SQLException

      Sets the designated parameter to an `java.sql.Blob`value.
      Specified by:
      [`setBlob`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setBlob_java_lang_String_java_sql_Blob_) in interface [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)

      Parameters:
      `parameterName` - the name of the stored procedure formal parameter

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setCLOB

          void setCLOB(String parameterName,
                       CLOB x)
                throws SQLException

      Sets the designated parameter to an `oracle.sql.CLOB`value.
      Parameters:
      `parameterName` - the name of the stored procedure formal parameter

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setClob

          void setClob(String parameterName,
                       Clob x)
                throws SQLException

      Sets the designated parameter to an `java.sql.Clob`value.
      Specified by:
      [`setClob`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setClob_java_lang_String_java_sql_Clob_) in interface [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)

      Parameters:
      `parameterName` - the name of the stored procedure formal parameter

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setBFILE

          void setBFILE(String parameterName,
                        BFILE x)
                 throws SQLException

      Sets the designated parameter to an `oracle.sql.BFILE`value.
      Parameters:
      `parameterName` - the name of the stored procedure formal parameter

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setBfile

          void setBfile(String parameterName,
                        BFILE x)
                 throws SQLException

      Sets the designated parameter to an `oracle.sql.BFILE`value.
      Parameters:
      `parameterName` - the name of the stored procedure formal parameter

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setBytes

          void setBytes(String parameterName,
                        byte[] x)
                 throws SQLException

      Sets the designated parameter to the given Java array of bytes. The driver converts this to an SQL `VARBINARY` or `LONGVARBINARY` (depending on the argument's size relative to the driver's limits on `VARBINARY` values) when it sends it to the database.
      Specified by:
      [`setBytes`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setBytes_java_lang_String_byte_A_) in interface [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)

      Parameters:
      `the` - name of the stored procedure formal parameter

      `x` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

      See Also:
      [`CallableStatement.getBytes(int)`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getBytes_int_)

    <!-- -->

    - #### setDate

          void setDate(String parameterName,
                       Date x)
                throws SQLException

      Sets the designated parameter to the given `java.sql.Date` value. The driver converts this to an SQL `DATE` value when it sends it to the database.
      Specified by:
      [`setDate`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setDate_java_lang_String_java_sql_Date_) in interface [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)

      Parameters:
      `the` - name of the stored procedure formal parameter

      `x` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

      See Also:
      [`CallableStatement.getDate(int)`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getDate_int_)

    <!-- -->

    - #### setTime

          void setTime(String parameterName,
                       Time x)
                throws SQLException

      Sets the designated parameter to the given `java.sql.Time` value. The driver converts this to an SQL `TIME` value when it sends it to the database.
      Specified by:
      [`setTime`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setTime_java_lang_String_java_sql_Time_) in interface [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)

      Parameters:
      `the` - name of the stored procedure formal parameter

      `x` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

      See Also:
      [`CallableStatement.getTime(int)`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getTime_int_)

    <!-- -->

    - #### setTimestamp

          void setTimestamp(String parameterName,
                            Timestamp x)
                     throws SQLException

      Sets the designated parameter to the given `java.sql.Timestamp` value. The driver converts this to an SQL `TIMESTAMP` value when it sends it to the database.
      Specified by:
      [`setTimestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setTimestamp_java_lang_String_java_sql_Timestamp_) in interface [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)

      Parameters:
      `the` - name of the stored procedure formal parameter

      `x` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

      See Also:
      [`CallableStatement.getTimestamp(int)`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getTimestamp_int_)

    <!-- -->

    - #### setINTERVALYM

          void setINTERVALYM(String parameterName,
                             INTERVALYM x)
                      throws SQLException

      Sets the designated parameter to an `oracle.sql.INTERVALYM`value.
      Parameters:
      `parameterName` - the name of the stored procedure formal parameter

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setINTERVALDS

          void setINTERVALDS(String parameterName,
                             INTERVALDS x)
                      throws SQLException

      Sets the designated parameter to an `oracle.sql.INTERVALDS`value.
      Parameters:
      `parameterName` - the name of the stored procedure formal parameter

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setTIMESTAMP

          void setTIMESTAMP(String parameterName,
                            TIMESTAMP x)
                     throws SQLException

      Sets the designated parameter to an `oracle.sql.TIMESTAMP`value.
      Parameters:
      `parameterName` - the name of the stored procedure formal parameter

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setTIMESTAMPTZ

          void setTIMESTAMPTZ(String parameterName,
                              TIMESTAMPTZ x)
                       throws SQLException

      Sets the designated parameter to an `oracle.sql.TIMESTAMPTZ`value.
      Parameters:
      `parameterName` - the name of the stored procedure formal parameter

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setTIMESTAMPLTZ

          void setTIMESTAMPLTZ(String parameterName,
                               TIMESTAMPLTZ x)
                        throws SQLException

      Sets the designated parameter to an `oracle.sql.TIMESTAMPLTZ`value.
      Parameters:
      `parameterName` - the name of the stored procedure formal parameter

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setAsciiStream

          void setAsciiStream(String parameterName,
                              InputStream x,
                              int y)
                       throws SQLException

      Sets the designated parameter to the given input stream, which will have the specified number of bytes. When a very large ASCII value is input to a `LONGVARCHAR` parameter, it may be more practical to send it via a `java.io.InputStream`. Data will be read from the stream as needed until end-of-file is reached. The JDBC driver will do any necessary conversion from ASCII to the database char format.
      **Note:** This stream object can either be a standard Java stream object or your own subclass that implements the standard interface.

      Specified by:
      [`setAsciiStream`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setAsciiStream_java_lang_String_java_io_InputStream_int_) in interface [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)

      Parameters:
      `parameterName` - the name of the stored procedure formal parameter

      `x` - the Java input stream that contains the ASCII parameter value

      `length` - the number of bytes in the stream

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

    <!-- -->

    - #### setBinaryStream

          void setBinaryStream(String parameterName,
                               InputStream x,
                               int y)
                        throws SQLException

      Sets the designated parameter to the given input stream, which will have the specified number of bytes. When a very large binary value is input to a `LONGVARBINARY` parameter, it may be more practical to send it via a `java.io.InputStream` object. The data will be read from the stream as needed until end-of-file is reached.
      **Note:** This stream object can either be a standard Java stream object or your own subclass that implements the standard interface.

      Specified by:
      [`setBinaryStream`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setBinaryStream_java_lang_String_java_io_InputStream_int_) in interface [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)

      Parameters:
      `parameterName` - the name of the stored procedure formal parameter

      `x` - the java input stream which contains the binary parameter value

      `length` - the number of bytes in the stream

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

    <!-- -->

    - #### setUnicodeStream

          void setUnicodeStream(String parameterName,
                                InputStream x,
                                int y)
                         throws SQLException

      Sets the designated parameter to a Java UnicodeStream value.
      Parameters:
      `parameterName` - the name of the stored procedure formal parameter

      `x` - the java input stream which contains the binary parameter value

      `length` - the number of bytes in the stream

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setCharacterStream

          void setCharacterStream(String parameterName,
                                  Reader x,
                                  int y)
                           throws SQLException

      Sets the designated parameter to the given `Reader` object, which is the given number of characters long. When a very large UNICODE value is input to a `LONGVARCHAR` parameter, it may be more practical to send it via a `java.io.Reader` object. The data will be read from the stream as needed until end-of-file is reached. The JDBC driver will do any necessary conversion from UNICODE to the database char format.
      **Note:** This stream object can either be a standard Java stream object or your own subclass that implements the standard interface.

      Specified by:
      [`setCharacterStream`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setCharacterStream_java_lang_String_java_io_Reader_int_) in interface [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)

      Parameters:
      `the` - name of the stored procedure formal parameter

      `reader` - the `java.io.Reader` object that contains the UNICODE data used as the designated parameter

      `length` - the number of characters in the stream

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

    <!-- -->

    - #### setDate

          void setDate(String parameterName,
                       Date x,
                       Calendar cal)
                throws SQLException

      Sets the designated parameter to the given `java.sql.Date` value, using the given `Calendar` object. The driver uses the `Calendar` object to construct an SQL `DATE` value, which the driver then sends to the database. With a a `Calendar` object, the driver can calculate the date taking into account a custom time zone. If no `Calendar` object is specified, the driver uses the default time zone, which is that of the virtual machine running the application.
      Specified by:
      [`setDate`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setDate_java_lang_String_java_sql_Date_java_util_Calendar_) in interface [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)

      Parameters:
      `the` - name of the stored procedure formal parameter

      `x` - the parameter value

      `cal` - the `Calendar` object the driver will use to construct the date

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

      See Also:
      [`CallableStatement.getDate(int)`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getDate_int_)

    <!-- -->

    - #### setTime

          void setTime(String parameterName,
                       Time x,
                       Calendar cal)
                throws SQLException

      Sets the designated parameter to the given `java.sql.Time` value, using the given `Calendar` object. The driver uses the `Calendar` object to construct an SQL `TIME` value, which the driver then sends to the database. With a a `Calendar` object, the driver can calculate the time taking into account a custom time zone. If no `Calendar` object is specified, the driver uses the default time zone, which is that of the virtual machine running the application.
      Specified by:
      [`setTime`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setTime_java_lang_String_java_sql_Time_java_util_Calendar_) in interface [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)

      Parameters:
      `the` - name of the stored procedure formal parameter

      `x` - the parameter value

      `cal` - the `Calendar` object the driver will use to construct the time

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

      See Also:
      [`CallableStatement.getTime(int)`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getTime_int_)

    <!-- -->

    - #### setTimestamp

          void setTimestamp(String parameterName,
                            Timestamp x,
                            Calendar cal)
                     throws SQLException

      Sets the designated parameter to the given `java.sql.Timestamp` value, using the given `Calendar` object. The driver uses the `Calendar` object to construct an SQL `TIMESTAMP` value, which the driver then sends to the database. With a a `Calendar` object, the driver can calculate the timestamp taking into account a custom time zone. If no `Calendar` object is specified, the driver uses the default time zone, which is that of the virtual machine running the application.
      Specified by:
      [`setTimestamp`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setTimestamp_java_lang_String_java_sql_Timestamp_java_util_Calendar_) in interface [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)

      Parameters:
      `the` - name of the stored procedure formal parameter

      `x` - the parameter value

      `cal` - the `Calendar` object the driver will use to construct the timestamp

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

      See Also:
      [`CallableStatement.getTimestamp(int)`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getTimestamp_int_)

    <!-- -->

    - #### setURL

          void setURL(String parameterName,
                      URL x)
               throws SQLException

      Sets the designated parameter to the given `java.net.URL` object. The driver converts this to an SQL `DATALINK` value when it sends it to the database.
      Specified by:
      [`setURL`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setURL_java_lang_String_java_net_URL_) in interface [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)

      Parameters:
      `the` - name of the stored procedure formal parameter

      `val` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs, or if a URL is malformed

      Since:
      9.0.2

      See Also:
      [`CallableStatement.getURL(int)`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#getURL_int_)

    <!-- -->

    - #### setArray

          void setArray(String parameterName,
                        Array x)
                 throws SQLException

      Sets the designated parameter to an `java.sql.Array`value.
      Parameters:
      `parameterName` - the name of the stored procedure formal parameter

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setARRAY

          void setARRAY(String parameterName,
                        ARRAY x)
                 throws SQLException

      Sets the designated parameter to an `oracle.sql.ARRAY`value.
      Parameters:
      `parameterName` - the name of the stored procedure formal parameter

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setOPAQUE

          void setOPAQUE(String parameterName,
                         OPAQUE x)
                  throws SQLException

      Sets the designated parameter to an `oracle.sql.OPAQUE`value.
      Parameters:
      `parameterName` - the name of the stored procedure formal parameter

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setStructDescriptor

          void setStructDescriptor(String parameterName,
                                   StructDescriptor x)
                            throws SQLException

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### setSTRUCT

          void setSTRUCT(String parameterName,
                         STRUCT x)
                  throws SQLException

      Sets the designated parameter to an `oracle.sql.STRUCT`value.
      Parameters:
      `parameterName` - the name of the stored procedure formal parameter

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setCustomDatum

          void setCustomDatum(String parameterName,
                              CustomDatum x)
                       throws SQLException

      Sets the designated parameter to an `oracle.sql.CustomDatum`value.
      Parameters:
      `parameterName` - the name of the stored procedure formal parameter

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setORAData

          void setORAData(String parameterName,
                          ORAData x)
                   throws SQLException

      Sets the designated parameter to an `oracle.sql.ORAData`value.
      Parameters:
      `parameterName` - the name of the stored procedure formal parameter

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setObject

          void setObject(String parameterName,
                         Object x,
                         int targetSqlType,
                         int scale)
                  throws SQLException

      Sets the value of the designated parameter with the given object. The second argument must be an object type; for integral values, the `java.lang` equivalent objects should be used.
      The given Java object will be converted to the given targetSqlType before being sent to the database. If the object has a custom mapping (is of a class implementing the interface `SQLData`), the JDBC driver should call the method `SQLData.writeSQL` to write it to the SQL data stream. If, on the other hand, the object is of a class implementing `Ref`, `Blob`, `Clob`, `Struct`, or `Array`, the driver should pass it to the database as a value of the corresponding SQL type.

      Note that this method may be used to pass database- specific abstract data types.

      Specified by:
      [`setObject`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setObject_java_lang_String_java_lang_Object_int_int_) in interface [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)

      Parameters:
      `the` - name of the stored procedure formal parameter

      `x` - the object containing the input parameter value

      `targetSqlType` - the SQL type (as defined in java.sql.Types) to be sent to the database. The scale argument may further qualify this type.

      `scale` - for java.sql.Types.DECIMAL or java.sql.Types.NUMERIC types, this is the number of digits after the decimal point. For all other types, this value will be ignored.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

      See Also:
      [`Types`](http://download.oracle.com/javase/8/docs/api/java/sql/Types.html?is-external=true), `getObject(int, oracle.jdbc.OracleDataFactory)`

    <!-- -->

    - #### setObject

          void setObject(String parameterName,
                         Object x,
                         int y)
                  throws SQLException

      Sets the value of the designated parameter with the given object. This method is like the method `setObject` above, except that it assumes a scale of zero.
      Specified by:
      [`setObject`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setObject_java_lang_String_java_lang_Object_int_) in interface [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)

      Parameters:
      `the` - name of the stored procedure formal parameter

      `x` - the object containing the input parameter value

      `targetSqlType` - the SQL type (as defined in java.sql.Types) to be sent to the database

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

      Since:
      9.0.2

      See Also:
      `getObject(int, oracle.jdbc.OracleDataFactory)`

    <!-- -->

    - #### setRefType

          void setRefType(String parameterName,
                          REF x)
                   throws SQLException

      Sets the designated parameter to an `oracle.sql.REF`value.
      Parameters:
      `parameterName` - the name of the stored procedure formal parameter

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setRef

          void setRef(String parameterName,
                      Ref x)
               throws SQLException

      Sets the designated parameter to an `jdbc.sql.Ref`value.
      Parameters:
      `parameterName` - the name of the stored procedure formal parameter

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setREF

          void setREF(String parameterName,
                      REF x)
               throws SQLException

      Sets the designated parameter to an `oracle.sql.REF`value.
      Parameters:
      `parameterName` - the name of the stored procedure formal parameter

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### setObject

          void setObject(String parameterName,
                         Object x)
                  throws SQLException

      Sets the value of the designated parameter with the given object. The second parameter must be of type `Object`; therefore, the `java.lang` equivalent objects should be used for built-in types.
      The JDBC specification specifies a standard mapping from Java `Object` types to SQL types. The given argument will be converted to the corresponding SQL type before being sent to the database.

      Note that this method may be used to pass database- specific abstract data types, by using a driver-specific Java type. If the object is of a class implementing the interface `SQLData`, the JDBC driver should call the method `SQLData.writeSQL` to write it to the SQL data stream. If, on the other hand, the object is of a class implementing `Ref`, `Blob`, `Clob`, `Struct`, or `Array`, the driver should pass it to the database as a value of the corresponding SQL type.

      This method throws an exception if there is an ambiguity, for example, if the object is of a class implementing more than one of the interfaces named above.

      Specified by:
      [`setObject`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true#setObject_java_lang_String_java_lang_Object_) in interface [`CallableStatement`](http://download.oracle.com/javase/8/docs/api/java/sql/CallableStatement.html?is-external=true)

      Parameters:
      `the` - name of the stored procedure formal parameter

      `x` - the object containing the input parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs or if the given `Object` parameter is ambiguous

      Since:
      9.0.2

      See Also:
      `getObject(int, oracle.jdbc.OracleDataFactory)`

    <!-- -->

    - #### setOracleObject

          void setOracleObject(String parameterName,
                               Datum x)
                        throws SQLException

      Sets the designated parameter to an `oracle.sql.Datum`value.
      Parameters:
      `the` - name of the stored procedure formal parameter

      `value` - the parameter value

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if a database access error occurs

    <!-- -->

    - #### registerOutParameterAtName

          void registerOutParameterAtName(String parameterMarkerName,
                                          int sqlType)
                                   throws SQLException

      Special Oracle method to registerOutParameter by the parameterMarkerName of oracle style parameter markers instead of parameterIndex. Please note that it takes the name of the parameter marker and not the name of the parameter.
      Parameters:
      `parameterMarkerName` - The name of the oracle style parameter marker

      `sqlType` - a value from [`Types`](http://download.oracle.com/javase/8/docs/api/java/sql/Types.html?is-external=true)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### registerOutParameterAtName

          void registerOutParameterAtName(String parameterMarkerName,
                                          int sqlType,
                                          int scale)
                                   throws SQLException

      Special Oracle method to registerOutParameter by the parameterMarkerName of oracle style parameter markers instead of parameterIndex. Please note that it takes the name of the parameter marker and not the name of the parameter.
      Parameters:
      `parameterMarkerName` - The name of the oracle style parameter marker

      `sqlType` - a value from [`Types`](http://download.oracle.com/javase/8/docs/api/java/sql/Types.html?is-external=true)

      `scale` - the desired number of digits to the right of the decimal point. It must be greater than or equal to zero.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### registerOutParameterAtName

          void registerOutParameterAtName(String parameterMarkerName,
                                          int sqlType,
                                          String typeName)
                                   throws SQLException

      Special Oracle method to registerOutParameter by the parameterMarkerName of oracle style parameter markers instead of parameterIndex. Please note that it takes the name of the parameter marker and not the name of the parameter.
      Parameters:
      `parameterMarkerName` - The name of the oracle style parameter marker

      `sqlType` - a value from [`Types`](http://download.oracle.com/javase/8/docs/api/java/sql/Types.html?is-external=true)

      `typeName` - the fully-qualified name of an SQL structured type

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleCallableStatement.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleBlob.md)
- [Next Class](OracleClob.md)

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
