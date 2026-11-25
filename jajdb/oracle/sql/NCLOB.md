Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/NCLOB.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](JAVA_STRUCT.md)
- [Next Class](NUMBER.md)

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

oracle.sql

## Class NCLOB

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.sql.Datum](Datum.md)

  - - [oracle.sql.DatumWithConnection](DatumWithConnection.md)

    - - [oracle.sql.CLOB](CLOB.md)

      - - oracle.sql.NCLOB

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), [Clob](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true), [NClob](http://download.oracle.com/javase/8/docs/api/java/sql/NClob.html?is-external=true), oracle.jdbc.internal.ACProxyable, oracle.jdbc.internal.OracleConcreteProxy, oracle.jdbc.internal.OracleDatumWithConnection, oracle.jdbc.internal.OracleLargeObject, [OracleClob](../jdbc/OracleClob.md), [OracleNClob](../jdbc/OracleNClob.md)

  ------------------------------------------------------------------------

  Deprecated. 
  Use java.sql.NClob interface for declaration instead of using concrete class oracle.sql.NCLOB.


      public class NCLOB
      extends CLOB
      implements oracle.jdbc.internal.OracleNClob

  Use [`NClob`](http://download.oracle.com/javase/8/docs/api/java/sql/NClob.html?is-external=true) interface for declaration instead of using concrete class oracle.sql.NCLOB. java.sql.NClob has methods declared for all opertions. For Oracle specific methods use the interface [`OracleNClob`](../jdbc/OracleNClob.md).
  Obtaining NClob from the ResultSet

  `java.sql.NClob nclob = resultSet.getNClob(...);`
  Creating temporary NClob using factory method, [`Connection.createNClob()`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#createNClob__)

  `java.sql.NClob nclob = connection.createNClob();`
  See Also:
  [`NClob`](http://download.oracle.com/javase/8/docs/api/java/sql/NClob.html?is-external=true), [`OracleNClob`](../jdbc/OracleNClob.md), [`Connection.createNClob()`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#createNClob__), [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from class oracle.sql.[CLOB](CLOB.md)

      [`DURATION_CALL`](CLOB.md)`, `[`DURATION_INVALID`](CLOB.md)`, `[`DURATION_SESSION`](CLOB.md)`, `[`MAX_CHUNK_SIZE`](CLOB.md)`, `[`MODE_READONLY`](CLOB.md)`, `[`MODE_READWRITE`](CLOB.md)`, `[`OLD_WRONG_DURATION_CALL`](CLOB.md)`, `[`OLD_WRONG_DURATION_SESSION`](CLOB.md)`, `[`target`](CLOB.md)

    <!-- -->

    - ### Fields inherited from class oracle.sql.[DatumWithConnection](DatumWithConnection.md)

      [`targetDatumWithConnection`](DatumWithConnection.md)

    <!-- -->

    - ### Fields inherited from class oracle.sql.[Datum](Datum.md)

      [`ojiOracleDatumWithConnection`](Datum.md)`, `[`targetDatum`](Datum.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Modifier    | Constructor and Description      |
    |-------------|----------------------------------|
    | `protected` | `NCLOB``()`<br>Deprecated. <br>  |

  <!-- -->

  - ### Method Summary

    - ### Methods inherited from class oracle.sql.[CLOB](CLOB.md)

      [`canReadBasicLobDataInLocator`](CLOB.md)`, `[`close`](CLOB.md)`, `[`createTemporary`](CLOB.md)`, `[`createTemporary`](CLOB.md)`, `[`empty_lob`](CLOB.md)`, `[`free`](CLOB.md)`, `[`freeTemporary`](CLOB.md)`, `[`freeTemporary`](CLOB.md)`, `[`getAsciiOutputStream`](CLOB.md)`, `[`getAsciiOutputStream`](CLOB.md)`, `[`getAsciiStream`](CLOB.md)`, `[`getAsciiStream`](CLOB.md)`, `[`getAsciiStream`](CLOB.md)`, `[`getBufferSize`](CLOB.md)`, `[`getCharacterOutputStream`](CLOB.md)`, `[`getCharacterOutputStream`](CLOB.md)`, `[`getCharacterStream`](CLOB.md)`, `[`getCharacterStream`](CLOB.md)`, `[`getCharacterStream`](CLOB.md)`, `[`getChars`](CLOB.md)`, `[`getChunkSize`](CLOB.md)`, `[`getDuration`](CLOB.md)`, `[`getDuration`](CLOB.md)`, `[`getEmptyCLOB`](CLOB.md)`, `[`getFormOfUseFromLocator`](CLOB.md)`, `[`getJavaSqlConnection`](CLOB.md)`, `[`getPrefetchedDataSize`](CLOB.md)`, `[`getSubString`](CLOB.md)`, `[`getTarget`](CLOB.md)`, `[`isConvertibleTo`](CLOB.md)`, `[`isEmptyLob`](CLOB.md)`, `[`isNCLOB`](CLOB.md)`, `[`isOpen`](CLOB.md)`, `[`isSecureFile`](CLOB.md)`, `[`isTemporary`](CLOB.md)`, `[`isTemporary`](CLOB.md)`, `[`length`](CLOB.md)`, `[`open`](CLOB.md)`, `[`position`](CLOB.md)`, `[`position`](CLOB.md)`, `[`putChars`](CLOB.md)`, `[`putChars`](CLOB.md)`, `[`putChars`](CLOB.md)`, `[`putString`](CLOB.md)`, `[`setAsciiStream`](CLOB.md)`, `[`setBytes`](CLOB.md)`, `[`setCharacterStream`](CLOB.md)`, `[`setString`](CLOB.md)`, `[`setString`](CLOB.md)`, `[`stringValue`](CLOB.md)`, `[`toJdbc`](CLOB.md)`, `[`toSQLXML`](CLOB.md)`, `[`toSQLXML`](CLOB.md)`, `[`trim`](CLOB.md)`, `[`truncate`](CLOB.md)

    <!-- -->

    - ### Methods inherited from class oracle.sql.[DatumWithConnection](DatumWithConnection.md)

      [`assertNotNull`](DatumWithConnection.md)`, `[`assertNotNull`](DatumWithConnection.md)`, `[`getConnection`](DatumWithConnection.md)`, `[`getConnectionDuringExceptionHandling`](DatumWithConnection.md)`, `[`getOracleConnection`](DatumWithConnection.md)

    <!-- -->

    - ### Methods inherited from class oracle.sql.[Datum](Datum.md)

      [`bigDecimalValue`](Datum.md)`, `[`booleanValue`](Datum.md)`, `[`bytesEqual`](Datum.md)`, `[`bytesHashCode`](Datum.md)`, `[`byteValue`](Datum.md)`, `[`compareBytes`](Datum.md)`, `[`dateValue`](Datum.md)`, `[`doubleValue`](Datum.md)`, `[`equals`](Datum.md)`, `[`floatValue`](Datum.md)`, `[`getBytes`](Datum.md)`, `[`getLength`](Datum.md)`, `[`getStream`](Datum.md)`, `[`intValue`](Datum.md)`, `[`isNull`](Datum.md)`, `[`longValue`](Datum.md)`, `[`setShareBytes`](Datum.md)`, `[`shareBytes`](Datum.md)`, `[`stringValue`](Datum.md)`, `[`timestampValue`](Datum.md)`, `[`timestampValue`](Datum.md)`, `[`timeValue`](Datum.md)`, `[`timeValue`](Datum.md)`, `[`toClass`](Datum.md)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.internal.OracleClob

      `asciiStreamValue, binaryStreamValue, canReadBasicLobDataInLocator, characterStreamValue, clearCachedData, getAsciiOutputStream, getAsciiOutputStream, getAsciiStream, getBufferSize, getCharacterOutputStream, getCharacterOutputStream, getCharacterStream, getChars, getChunkSize, getDBAccess, getJavaSqlConnection, getLocator, getPrefetchedData, getPrefetchedDataSize, isActivePrefetch, isConvertibleTo, isNCLOB, makeJdbcArray, putChars, putChars, putString, setActivePrefetch, setChunkSize, setLength, setLocator, setPrefetchedData, setPrefetchedData, stringValue, toJdbc, trim`

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.internal.OracleDatumWithConnection

      `bigDecimalValue, booleanValue, byteValue, dateValue, doubleValue, floatValue, getBytes, getConnection, getInternalConnection, getLength, getOracleConnection, getStream, intValue, longValue, setBytes, setPhysicalConnectionOf, setShareBytes, shareBytes, stringValue, timestampValue, timestampValue, timeValue, timeValue`

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.[OracleClob](../jdbc/OracleClob.md)

      [`close`](../jdbc/OracleClob.md)`, `[`isEmptyLob`](../jdbc/OracleClob.md)`, `[`isOpen`](../jdbc/OracleClob.md)`, `[`isSecureFile`](../jdbc/OracleClob.md)`, `[`isTemporary`](../jdbc/OracleClob.md)`, `[`open`](../jdbc/OracleClob.md)`, `[`toSQLXML`](../jdbc/OracleClob.md)`, `[`toSQLXML`](../jdbc/OracleClob.md)

    <!-- -->

    - ### Methods inherited from interface java.sql.[Clob](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true)

      [`free`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#free__)`, `[`getAsciiStream`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#getAsciiStream__)`, `[`getCharacterStream`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#getCharacterStream__)`, `[`getCharacterStream`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#getCharacterStream_long_long_)`, `[`getSubString`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#getSubString_long_int_)`, `[`length`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#length__)`, `[`position`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#position_java_sql_Clob_long_)`, `[`position`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#position_java_lang_String_long_)`, `[`setAsciiStream`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#setAsciiStream_long_)`, `[`setCharacterStream`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#setCharacterStream_long_)`, `[`setString`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#setString_long_java_lang_String_)`, `[`setString`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#setString_long_java_lang_String_int_int_)`, `[`truncate`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#truncate_long_)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.internal.ACProxyable

      `getACProxy, setACProxy`

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.internal.OracleLargeObject

      `freeTemporary, getDuration, isTemporary`

<!-- -->

- - ### Constructor Detail

    - #### NCLOB

          protected NCLOB()

      Deprecated. 

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/NCLOB.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](JAVA_STRUCT.md)
- [Next Class](NUMBER.md)

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
