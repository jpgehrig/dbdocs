Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/CLOB.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](CharacterWalker.md)
- [Next Class](ConcreteProxyUtil.md)

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

## Class CLOB

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.sql.Datum](Datum.md)

  - - [oracle.sql.DatumWithConnection](DatumWithConnection.md)

    - - oracle.sql.CLOB

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), [Clob](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true), oracle.jdbc.internal.ACProxyable, oracle.jdbc.internal.OracleConcreteProxy, oracle.jdbc.internal.OracleDatumWithConnection, oracle.jdbc.internal.OracleLargeObject, [OracleClob](../jdbc/OracleClob.md)

  <!-- -->

  Direct Known Subclasses:
  [NCLOB](NCLOB.md)

  ------------------------------------------------------------------------

  Deprecated. 
  Use java.sql.Clob interface for declaration instead of using concrete class oracle.sql.CLOB.


      public class CLOB
      extends DatumWithConnection
      implements oracle.jdbc.internal.OracleClob, oracle.jdbc.internal.OracleConcreteProxy

  This class implements java.sql.Clob interface in JDBC.2.0. Use java.sql.Clob interface for declaration instead of using concrete class oracle.sql.CLOB. java.sql.Clob has methods declared for all opertions. For Oracle specific methods use the interface oracle.jdbc.OracleClob. There is no need for the user to bother about chunk sizes any more it is taken care of internally.
  Obtaining java.sql.Clob from ResultSet

  `java.sql.Clob clob = resultSet.getClob(...);`
  Creating a temporary Clob should use [`Connection.createClob()`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#createClob__)

  `java.sql.Clob clob = connection.createClob();`
  See Also:
  [`Clob`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true), [`OracleClob`](../jdbc/OracleClob.md), [`Connection.createClob()`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#createClob__), [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type                         | Field and Description                             |
    |-------------------------------------------|---------------------------------------------------|
    | `static int`                              | `DURATION_CALL`<br>Deprecated. <br>               |
    | `static int`                              | `DURATION_INVALID`<br>Deprecated. <br>            |
    | `static int`                              | `DURATION_SESSION`<br>Deprecated. <br>            |
    | `static int`                              | `MAX_CHUNK_SIZE`<br>Deprecated. <br>              |
    | `static int`                              | `MODE_READONLY`<br>Deprecated. <br>               |
    | `static int`                              | `MODE_READWRITE`<br>Deprecated. <br>              |
    | `static int`                              | `OLD_WRONG_DURATION_CALL`<br>Deprecated. <br>     |
    | `static int`                              | `OLD_WRONG_DURATION_SESSION`<br>Deprecated. <br>  |
    | `protected oracle.jdbc.driver.OracleClob` | `target`<br>Deprecated. <br>                      |

    - ### Fields inherited from class oracle.sql.[DatumWithConnection](DatumWithConnection.md)

      [`targetDatumWithConnection`](DatumWithConnection.md)

    <!-- -->

    - ### Fields inherited from class oracle.sql.[Datum](Datum.md)

      [`ojiOracleDatumWithConnection`](Datum.md)`, `[`targetDatum`](Datum.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Modifier    | Constructor and Description                                                                                                  |
    |-------------|------------------------------------------------------------------------------------------------------------------------------|
    | `protected` | `CLOB``()`<br>Deprecated. <br>                                                                                               |
    | `protected` | `CLOB``(oracle.jdbc.driver.OracleClob c)`<br>Deprecated. <br>Call from empty lob static method                               |
    | ` `         | `CLOB``(`[`OracleConnection`](../jdbc/OracleConnection.md)` conn, byte[] lob_descriptor, short csform)`<br>Deprecated. <br>  |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                                                         | Method and Description                                                                                                                                                                                                                                                                             |
    |-----------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                                                                                 | `canReadBasicLobDataInLocator``()`<br>Deprecated. <br>Can the lob data be read directly from the locator?                                                                                                                                                                                          |
    | `void`                                                                                                    | `close``()`<br>Deprecated. <br>Close a previously opened CLOB.                                                                                                                                                                                                                                     |
    | `static CLOB`                                                                                             | `createTemporary``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, boolean cache, int _duration)`<br>Deprecated. <br>Create a temporary clob.                                                                                       |
    | `static CLOB`                                                                                             | `createTemporary``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, boolean cache, int _duration, short form_of_use)`<br>Deprecated. <br>Create a temporary clob or nclob.                                                           |
    | `static CLOB`                                                                                             | `empty_lob``()`<br>Deprecated. <br>use getEmptyCLOB instead                                                                                                                                                                                                                                        |
    | `void`                                                                                                    | `free``()`<br>Deprecated. <br>Free the resources the clob holds.                                                                                                                                                                                                                                   |
    | `void`                                                                                                    | `freeTemporary``()`<br>Deprecated. <br>Free the contents and the locator of the temporary clob.                                                                                                                                                                                                    |
    | `static void`                                                                                             | `freeTemporary``(CLOB temp_lob)`<br>Deprecated. <br>Free the contents and the locator of the temporary clob.                                                                                                                                                                                       |
    | [`OutputStream`](http://download.oracle.com/javase/8/docs/api/java/io/OutputStream.html?is-external=true) | `getAsciiOutputStream``()`<br>Deprecated. <br>This method is deprecated. Use setAsciiStream( 1L );                                                                                                                                                                                                 |
    | [`OutputStream`](http://download.oracle.com/javase/8/docs/api/java/io/OutputStream.html?is-external=true) | `getAsciiOutputStream``(long pos)`<br>Deprecated. <br>This method is deprecated. Use setAsciiStream.                                                                                                                                                                                               |
    | [`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)   | `getAsciiStream``()`<br>Deprecated. <br>Implements the Clob interface method.                                                                                                                                                                                                                      |
    | [`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)   | `getAsciiStream``(boolean isInternal)`<br>Deprecated. <br>Implements the Clob interface method.                                                                                                                                                                                                    |
    | [`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)   | `getAsciiStream``(long pos)`<br>Deprecated. <br>Read from the CLOB as a stream at the requested position.                                                                                                                                                                                          |
    | `int`                                                                                                     | `getBufferSize``()`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                                                           |
    | [`Writer`](http://download.oracle.com/javase/8/docs/api/java/io/Writer.html?is-external=true)             | `getCharacterOutputStream``()`<br>Deprecated. <br>This method is deprecated. Use setCharacterStream( 1L ).                                                                                                                                                                                         |
    | [`Writer`](http://download.oracle.com/javase/8/docs/api/java/io/Writer.html?is-external=true)             | `getCharacterOutputStream``(long pos)`<br>Deprecated. <br>This method is deprecated. Use setCharacterStream.                                                                                                                                                                                       |
    | [`Reader`](http://download.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)             | `getCharacterStream``()`<br>Deprecated. <br>Implements the Clob interface method.                                                                                                                                                                                                                  |
    | [`Reader`](http://download.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)             | `getCharacterStream``(long pos)`<br>Deprecated. <br>Read from the CLOB as a stream at the requested position.                                                                                                                                                                                      |
    | [`Reader`](http://download.oracle.com/javase/8/docs/api/java/io/Reader.html?is-external=true)             | `getCharacterStream``(long pos, long length)`<br>Deprecated. <br>Return a character stream beginning at the specified position and ofthe specified length.                                                                                                                                         |
    | `int`                                                                                                     | `getChars``(long pos, int length, char[] buffer)`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                             |
    | `int`                                                                                                     | `getChunkSize``()`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                                                            |
    | `short`                                                                                                   | `getDuration``()`<br>Deprecated. <br>return the duration of a temporary LOB                                                                                                                                                                                                                        |
    | `static short`                                                                                            | `getDuration``(CLOB lob)`<br>Deprecated. <br>return the duration of a temporary LOB                                                                                                                                                                                                                |
    | `static CLOB`                                                                                             | `getEmptyCLOB``()`<br>Deprecated. <br>Return a empty lob.                                                                                                                                                                                                                                          |
    | `static short`                                                                                            | `getFormOfUseFromLocator``(byte[] lob_descriptor)`<br>Deprecated. <br>                                                                                                                                                                                                                             |
    | [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)    | `getJavaSqlConnection``()`<br>Deprecated. <br>Oracle extension Return the java.sql.Connection associated with the receiver.                                                                                                                                                                        |
    | `int`                                                                                                     | `getPrefetchedDataSize``()`<br>Deprecated. <br>                                                                                                                                                                                                                                                    |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)           | `getSubString``(long pos, int length)`<br>Deprecated. <br>Implements the Clob interface method.                                                                                                                                                                                                    |
    | `oracle.jdbc.driver.OracleClob`                                                                           | `getTarget``()`<br>Deprecated. <br>                                                                                                                                                                                                                                                                |
    | `boolean`                                                                                                 | `isConvertibleTo``(`[`Class`](http://download.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)` jClass)`<br>Deprecated. <br>Test whether this data object can be converted to the specified Java data type.                                                                     |
    | `boolean`                                                                                                 | `isEmptyLob``()`<br>Deprecated. <br>Return true if this is a empty lob.                                                                                                                                                                                                                            |
    | `boolean`                                                                                                 | `isNCLOB``()`<br>Deprecated. <br>                                                                                                                                                                                                                                                                  |
    | `boolean`                                                                                                 | `isOpen``()`<br>Deprecated. <br>Check whether the CLOB is opened.                                                                                                                                                                                                                                  |
    | `boolean`                                                                                                 | `isSecureFile``()`<br>Deprecated. <br>Returns `true` if this is a SecureFile (LOBs with the STORE AS SECUREFILE option, which were introduced in Oracle Database 11g Release 1).                                                                                                                   |
    | `boolean`                                                                                                 | `isTemporary``()`<br>Deprecated. <br>Return true if the lob locator points to a temporary clob.                                                                                                                                                                                                    |
    | `static boolean`                                                                                          | `isTemporary``(CLOB lob)`<br>Deprecated. <br>Return true if the lob locator points to a temporary clob.                                                                                                                                                                                            |
    | `long`                                                                                                    | `length``()`<br>Deprecated. <br>Implements the Clob interface method.                                                                                                                                                                                                                              |
    | `void`                                                                                                    | `open``(`[`LargeObjectAccessMode`](../jdbc/LargeObjectAccessMode.md)` mode)`<br>Deprecated. <br>Public method using enum instead of int                                                                                                                                                            |
    | `long`                                                                                                    | `position``(`[`Clob`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true)` searchstr, long start)`<br>Deprecated. <br>Implements the Clob interface method.                                                                                                          |
    | `long`                                                                                                    | `position``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` searchstr, long start)`<br>Deprecated. <br>Implements the Clob interface method.                                                                                                     |
    | `int`                                                                                                     | `putChars``(long pos, char[] chars)`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                                          |
    | `int`                                                                                                     | `putChars``(long pos, char[] chars, int length)`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                              |
    | `int`                                                                                                     | `putChars``(long pos, char[] chars, int offset, int length)`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                                  |
    | `int`                                                                                                     | `putString``(long pos, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str)`<br>Deprecated. <br>This method is deprecated -- use setString.                                                                                                      |
    | [`OutputStream`](http://download.oracle.com/javase/8/docs/api/java/io/OutputStream.html?is-external=true) | `setAsciiStream``(long pos)`<br>Deprecated. <br>JDBC 3.0 Retrieves a stream to be used to write Ascii characters to the `CLOB` value that this `Clob` object represents, starting at position `pos`.                                                                                               |
    | `void`                                                                                                    | `setBytes``(byte[] locator)`<br>Deprecated. <br>Sets datum value using a byte array.                                                                                                                                                                                                               |
    | [`Writer`](http://download.oracle.com/javase/8/docs/api/java/io/Writer.html?is-external=true)             | `setCharacterStream``(long pos)`<br>Deprecated. <br>JDBC 3.0 Retrieves a stream to be used to write a stream of Unicode characters to the `CLOB` value that this `Clob` object represents, at position `pos`.                                                                                      |
    | `int`                                                                                                     | `setString``(long pos, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str)`<br>Deprecated. <br>JDBC 3.0 Writes the given Java `String` to the `CLOB` value that this `Clob` object designates at the position `pos`.                            |
    | `int`                                                                                                     | `setString``(long pos, `[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` str, int offset, int len)`<br>Deprecated. <br>JDBC 3.0 Writes `len` characters of `str`, starting at character `offset`, to the `CLOB` value that this `Clob` represents. |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)           | `stringValue``()`<br>Deprecated. <br>Convert to a String representation of the datum object                                                                                                                                                                                                        |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)           | `toJdbc``()`<br>Deprecated. <br>Convert this data object into its default Java object type.                                                                                                                                                                                                        |
    | [`SQLXML`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLXML.html?is-external=true)            | `toSQLXML``()`<br>Deprecated. <br>Returns an object which impements java.sql.SQLXML with content take from this Clob.                                                                                                                                                                              |
    | [`SQLXML`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLXML.html?is-external=true)            | `toSQLXML``(`[`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)` schemaURL)`<br>Deprecated. <br>Returns an object which impements java.sql.SQLXML with content taken from this Clob.                                                                  |
    | `void`                                                                                                    | `trim``(long newlen)`<br>Deprecated. <br>This method is deprecated. Use truncate().                                                                                                                                                                                                                |
    | `void`                                                                                                    | `truncate``(long len)`<br>Deprecated. <br>JDBC 3.0 Truncates the `CLOB` value that this `Clob` designates to have a length of `len` characters.                                                                                                                                                    |

    - ### Methods inherited from class oracle.sql.[DatumWithConnection](DatumWithConnection.md)

      [`assertNotNull`](DatumWithConnection.md)`, `[`assertNotNull`](DatumWithConnection.md)`, `[`getConnection`](DatumWithConnection.md)`, `[`getConnectionDuringExceptionHandling`](DatumWithConnection.md)`, `[`getOracleConnection`](DatumWithConnection.md)

    <!-- -->

    - ### Methods inherited from class oracle.sql.[Datum](Datum.md)

      [`bigDecimalValue`](Datum.md)`, `[`booleanValue`](Datum.md)`, `[`bytesEqual`](Datum.md)`, `[`bytesHashCode`](Datum.md)`, `[`byteValue`](Datum.md)`, `[`compareBytes`](Datum.md)`, `[`dateValue`](Datum.md)`, `[`doubleValue`](Datum.md)`, `[`equals`](Datum.md)`, `[`floatValue`](Datum.md)`, `[`getBytes`](Datum.md)`, `[`getLength`](Datum.md)`, `[`getStream`](Datum.md)`, `[`intValue`](Datum.md)`, `[`isNull`](Datum.md)`, `[`longValue`](Datum.md)`, `[`setShareBytes`](Datum.md)`, `[`shareBytes`](Datum.md)`, `[`stringValue`](Datum.md)`, `[`timestampValue`](Datum.md)`, `[`timestampValue`](Datum.md)`, `[`timeValue`](Datum.md)`, `[`timeValue`](Datum.md)`, `[`toClass`](Datum.md)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.internal.OracleDatumWithConnection

      `bigDecimalValue, booleanValue, byteValue, dateValue, doubleValue, floatValue, getBytes, getConnection, getInternalConnection, getLength, getOracleConnection, getStream, intValue, longValue, setPhysicalConnectionOf, setShareBytes, shareBytes, stringValue, timestampValue, timestampValue, timeValue, timeValue`

<!-- -->

- - ### Field Detail

    - #### MAX_CHUNK_SIZE

          public static final int MAX_CHUNK_SIZE

      Deprecated. 
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DURATION_INVALID

          public static final int DURATION_INVALID

      Deprecated. 
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DURATION_SESSION

          public static final int DURATION_SESSION

      Deprecated. 
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DURATION_CALL

          public static final int DURATION_CALL

      Deprecated. 
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### OLD_WRONG_DURATION_SESSION

          public static final int OLD_WRONG_DURATION_SESSION

      Deprecated. 
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### OLD_WRONG_DURATION_CALL

          public static final int OLD_WRONG_DURATION_CALL

      Deprecated. 
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### MODE_READONLY

          public static final int MODE_READONLY

      Deprecated. 
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### MODE_READWRITE

          public static final int MODE_READWRITE

      Deprecated. 
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### target

          protected oracle.jdbc.driver.OracleClob target

      Deprecated. 

  <!-- -->

  - ### Constructor Detail

    - #### CLOB

          protected CLOB()

      Deprecated. 

    <!-- -->

    - #### CLOB

          protected CLOB(oracle.jdbc.driver.OracleClob c)

      Deprecated. 
      Call from empty lob static method

    <!-- -->

    - #### CLOB

          public CLOB(OracleConnection conn,
                      byte[] lob_descriptor,
                      short csform)
               throws SQLException

      Deprecated. 
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

  <!-- -->

  - ### Method Detail

    - #### getTarget

          public oracle.jdbc.driver.OracleClob getTarget()

      Deprecated. 

    <!-- -->

    - #### getFormOfUseFromLocator

          public static final short getFormOfUseFromLocator(byte[] lob_descriptor)

      Deprecated. 

    <!-- -->

    - #### isNCLOB

          public boolean isNCLOB()

      Deprecated. 
      Returns:
      true if the data is bound for a SQL NCHAR datatype false otherwise

    <!-- -->

    - #### length

          public long length()
                      throws SQLException

      Deprecated. 
      Implements the Clob interface method. Returns the number of characters in the `CLOB` value designated by this `Clob` object.
      Specified by:
      [`length`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#length__) in interface [`Clob`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true)

      Returns:
      length of the `CLOB` in characters

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if there is an error accessing the length of the `CLOB`

    <!-- -->

    - #### getSubString

          public String getSubString(long pos,
                                     int length)
                              throws SQLException

      Deprecated. 
      Implements the Clob interface method. Returns a copy of the specified substring in the `CLOB` value designated by this `Clob` object. The substring begins at position `pos` and has up to `length` consecutive characters.
      Specified by:
      [`getSubString`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#getSubString_long_int_) in interface [`Clob`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true)

      Parameters:
      `pos` - the first character of the substring to be extracted. The first character is at position 1.

      `length` - the number of consecutive characters to be copied

      Returns:
      a `String` that is the specified substring in the `CLOB` value designated by this `Clob` object. If the `pos` argument is larger than the length of the data the result is an empty `String`. If the `pos` argument is less than the length of the data, but the sum of `pos` argument and the `length` is greater than the length of the data, the result will be smaller than the length requested.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if there is an error accessing the `CLOB`

    <!-- -->

    - #### getCharacterStream

          public Reader getCharacterStream()
                                    throws SQLException

      Deprecated. 
      Implements the Clob interface method. Gets the `Clob` contents as a Unicode stream.
      Specified by:
      [`getCharacterStream`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#getCharacterStream__) in interface [`Clob`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true)

      Returns:
      a Unicode stream containing the `CLOB` data

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if there is an error accessing the `CLOB`

    <!-- -->

    - #### getAsciiStream

          public InputStream getAsciiStream()
                                     throws SQLException

      Deprecated. 
      Implements the Clob interface method. Gets the `CLOB` value designated by this `Clob` object as a stream of Ascii bytes.
      Specified by:
      [`getAsciiStream`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#getAsciiStream__) in interface [`Clob`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true)

      Returns:
      an ascii stream containing the `CLOB` data

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if there is an error accessing the `CLOB` value

    <!-- -->

    - #### getAsciiStream

          public InputStream getAsciiStream(boolean isInternal)
                                     throws SQLException

      Deprecated. 
      Implements the Clob interface method. Gets the `CLOB` value designated by this `Clob` object as a stream of Ascii bytes.
      Returns:
      an ascii stream containing the `CLOB` data

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if there is an error accessing the `CLOB` value

    <!-- -->

    - #### position

          public long position(String searchstr,
                               long start)
                        throws SQLException

      Deprecated. 
      Implements the Clob interface method. Determine the character position at which the given substring
      Specified by:
      [`position`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#position_java_lang_String_long_) in interface [`Clob`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true)

      Parameters:
      `searchstr` - is the substring to search for.

      `start` - is the position at which to begin searching.

      Returns:
      the position at which the substring appears, else -1.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### position

          public long position(Clob searchstr,
                               long start)
                        throws SQLException

      Deprecated. 
      Implements the Clob interface method. Determine the character position at which the given substring
      Specified by:
      [`position`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#position_java_sql_Clob_long_) in interface [`Clob`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true)

      Parameters:
      `searchstr` - is the substring to search for.

      `start` - is the position at which to begin searching.

      Returns:
      the position at which the substring appears, else -1.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getChars

          public int getChars(long pos,
                              int length,
                              char[] buffer)
                       throws SQLException

      Deprecated. 
      Oracle extension. Return copy of the substring of the CLOB at the requested position.
      Parameters:
      `buffer` - is the buffer into whcih the characters are read.

      `pos` - is the first character of the substring to be extracted.

      `length` - is the number of consecutive character to be copied.

      Returns:
      the actual number of characters read.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getCharacterOutputStream

          public Writer getCharacterOutputStream()
                                          throws SQLException

      Deprecated. This method is deprecated. Use setCharacterStream( 1L ).
      Oracle extension. Write Unicode stream to the CLOB.
      Returns:
      a Unicode character output stream.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getAsciiOutputStream

          public OutputStream getAsciiOutputStream()
                                            throws SQLException

      Deprecated. This method is deprecated. Use setAsciiStream( 1L );
      Oracle extension. Write ascii stream to the CLOB.
      Returns:
      a ascii output stream.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### putChars

          public int putChars(long pos,
                              char[] chars)
                       throws SQLException

      Deprecated. 
      Oracle extension. Write characters at the requested position.
      Parameters:
      `pos` - is the position to write characters.

      `chars` - is the buffer of characters to be written.

      Returns:
      the actual number of characters written.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### putChars

          public int putChars(long pos,
                              char[] chars,
                              int length)
                       throws SQLException

      Deprecated. 
      Oracle extension. Write characters at the requested position.
      Parameters:
      `pos` - is the position to write characters.

      `chars` - is the buffer of characters to be written.

      `length` - is the length to write

      Returns:
      the actual number of characters written.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### putChars

          public int putChars(long pos,
                              char[] chars,
                              int offset,
                              int length)
                       throws SQLException

      Deprecated. 
      Oracle extension. Write characters at the requested position.
      Parameters:
      `pos` - is the position to write characters.

      `chars` - is the buffer of characters to be written.

      `offset` - is the position in the buffer from which to begin

      `length` - is the length to write

      Returns:
      the actual number of characters written.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### putString

          public int putString(long pos,
                               String str)
                        throws SQLException

      Deprecated. This method is deprecated -- use setString.
      Oracle extension. Write String to a CLOB This method provides support to return a 32-bit specification of the number of characters written to the CLOB.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getChunkSize

          public int getChunkSize()
                           throws SQLException

      Deprecated. 
      Oracle extension. Get database LOB storage chunk size. There is no need for the user to use this, since the driver does the read and writes in chunk sizes internally.
      Returns:
      the size in terms of characters.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getBufferSize

          public int getBufferSize()
                            throws SQLException

      Deprecated. 
      Oracle extension. Get ideal LOB db access buffer size.
      Returns:
      the size in terms of characters.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### empty_lob

          public static CLOB empty_lob()
                                throws SQLException

      Deprecated. use getEmptyCLOB instead
      Return a empty lob. An empty lob is used initialize a LOB column/attribute. Note: an empty lob can not be read or written
      Returns:
      a empty lob

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.1.7

    <!-- -->

    - #### getEmptyCLOB

          public static CLOB getEmptyCLOB()
                                   throws SQLException

      Deprecated. 
      Return a empty lob. An empty lob is used initialize a LOB column/attribute. Note: an empty lob can not be read or written
      Returns:
      a empty lob

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      10.2

    <!-- -->

    - #### isEmptyLob

          public boolean isEmptyLob()
                             throws SQLException

      Deprecated. 
      Return true if this is a empty lob.
      Specified by:
      [`isEmptyLob`](../jdbc/OracleClob.md) in interface [`OracleClob`](../jdbc/OracleClob.md)

      Returns:
      true if this is a empty lob. This method supports only Clobs that are not returned from the database. For Clobs returned from the database, use length(), i.e. check for zero length

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.1.7

      See Also:
      `empty_lob`

    <!-- -->

    - #### isSecureFile

          public boolean isSecureFile()
                               throws SQLException

      Deprecated. 
      Returns `true` if this is a SecureFile (LOBs with the STORE AS SECUREFILE option, which were introduced in Oracle Database 11g Release 1).
      Specified by:
      [`isSecureFile`](../jdbc/OracleClob.md) in interface [`OracleClob`](../jdbc/OracleClob.md)

      Returns:
      `true` if this is a SecureFile and `false` otherwise.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getAsciiOutputStream

          public OutputStream getAsciiOutputStream(long pos)
                                            throws SQLException

      Deprecated. This method is deprecated. Use setAsciiStream.
      Write to the CLOB from a stream at the requested position.
      Parameters:
      `pos` - is the position data to be put.

      Returns:
      a output stream to write data to the CLOB

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### getCharacterOutputStream

          public Writer getCharacterOutputStream(long pos)
                                          throws SQLException

      Deprecated. This method is deprecated. Use setCharacterStream.
      Write to the CLOB from a stream at the requested position.
      Parameters:
      `pos` - is the position data to be put.

      Returns:
      a output stream to write data to the CLOB

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### getAsciiStream

          public InputStream getAsciiStream(long pos)
                                     throws SQLException

      Deprecated. 
      Read from the CLOB as a stream at the requested position.
      Parameters:
      `pos` - is the position data to be put.

      Returns:
      a input stream to read data from the CLOB

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### getCharacterStream

          public Reader getCharacterStream(long pos)
                                    throws SQLException

      Deprecated. 
      Read from the CLOB as a stream at the requested position.
      Parameters:
      `pos` - is the position data to be put.

      Returns:
      a input stream to read data from the CLOB

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### trim

          public void trim(long newlen)
                    throws SQLException

      Deprecated. This method is deprecated. Use truncate().
      Trim the value of the CLOB to the length you specify in the newlen parameter.
      Parameters:
      `newlen` - the new length of the CLOB.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### createTemporary

          public static CLOB createTemporary(Connection conn,
                                             boolean cache,
                                             int _duration)
                                      throws SQLException

      Deprecated. 
      Create a temporary clob.
      Parameters:
      `cache` - Specifies if LOB should be read into buffer cache or not.

      `_duration` - The duration of the temporary LOB. The following are valid values: DURATION_SESSION, DURATION_CALL.

      Returns:
      A temporary clob.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### createTemporary

          public static CLOB createTemporary(Connection conn,
                                             boolean cache,
                                             int _duration,
                                             short form_of_use)
                                      throws SQLException

      Deprecated. 
      Create a temporary clob or nclob.
      Parameters:
      `cache` - Specifies if LOB should be read into buffer cache or not.

      `_duration` - The duration of the temporary LOB. The following are valid values: DURATION_SESSION, DURATION_CALL.

      `form_of_use` - Valid values are FORM_CHAR and FORM_NCHAR

      Returns:
      A temporary clob.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      10g

    <!-- -->

    - #### freeTemporary

          public static void freeTemporary(CLOB temp_lob)
                                    throws SQLException

      Deprecated. 
      Free the contents and the locator of the temporary clob.
      Parameters:
      `temp_lob` - A temporary clob to be freeed.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if temp_lob is a permanent lob or temp_lob has already been freed.

      Since:
      8.2.0

    <!-- -->

    - #### isTemporary

          public static boolean isTemporary(CLOB lob)
                                     throws SQLException

      Deprecated. 
      Return true if the lob locator points to a temporary clob. False if it does not.
      Parameters:
      `lob` - the clob to test.

      Returns:
      true if the lob locator points to a temporary clob. False if it does not.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### getDuration

          public static short getDuration(CLOB lob)
                                   throws SQLException

      Deprecated. 
      return the duration of a temporary LOB
      Returns:
      the duration of a temporary LOB

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      18.1

    <!-- -->

    - #### freeTemporary

          public void freeTemporary()
                             throws SQLException

      Deprecated. 
      Free the contents and the locator of the temporary clob.
      Specified by:
      `freeTemporary` in interface `oracle.jdbc.internal.OracleLargeObject`

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if self is a permanent lob or self has already been freed.

      Since:
      8.2.0

    <!-- -->

    - #### isTemporary

          public boolean isTemporary()
                              throws SQLException

      Deprecated. 
      Return true if the lob locator points to a temporary clob. False if it does not.
      Specified by:
      `isTemporary` in interface `oracle.jdbc.internal.OracleLargeObject`

      Specified by:
      [`isTemporary`](../jdbc/OracleClob.md) in interface [`OracleClob`](../jdbc/OracleClob.md)

      Returns:
      true if the lob locator points to a temporary clob. False if it does not.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### getDuration

          public short getDuration()
                            throws SQLException

      Deprecated. 
      return the duration of a temporary LOB
      Specified by:
      `getDuration` in interface `oracle.jdbc.internal.OracleLargeObject`

      Returns:
      the duration of a temporary LOB

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      18.1

    <!-- -->

    - #### open

          public void open(LargeObjectAccessMode mode)
                    throws SQLException

      Deprecated. 
      Public method using enum instead of int
      Specified by:
      [`open`](../jdbc/OracleClob.md) in interface [`OracleClob`](../jdbc/OracleClob.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### close

          public void close()
                     throws SQLException

      Deprecated. 
      Close a previously opened CLOB.
      Specified by:
      [`close`](../jdbc/OracleClob.md) in interface [`OracleClob`](../jdbc/OracleClob.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### isOpen

          public boolean isOpen()
                         throws SQLException

      Deprecated. 
      Check whether the CLOB is opened.
      Specified by:
      [`isOpen`](../jdbc/OracleClob.md) in interface [`OracleClob`](../jdbc/OracleClob.md)

      Returns:
      true if the LOB is opened.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### setString

          public int setString(long pos,
                               String str)
                        throws SQLException

      Deprecated. 
      JDBC 3.0 Writes the given Java `String` to the `CLOB` value that this `Clob` object designates at the position `pos`.
      Specified by:
      [`setString`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#setString_long_java_lang_String_) in interface [`Clob`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true)

      Parameters:
      `pos` - the position at which to start writing to the `CLOB` value that this `Clob` object represents

      `str` - the string to be written to the `CLOB` value that this `Clob` designates

      Returns:
      the number of characters written

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if there is an error accessing the `CLOB` value

      Since:
      9.0.2

    <!-- -->

    - #### setString

          public int setString(long pos,
                               String str,
                               int offset,
                               int len)
                        throws SQLException

      Deprecated. 
      JDBC 3.0 Writes `len` characters of `str`, starting at character `offset`, to the `CLOB` value that this `Clob` represents.
      Specified by:
      [`setString`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#setString_long_java_lang_String_int_int_) in interface [`Clob`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true)

      Parameters:
      `pos` - the position at which to start writing to this `CLOB` object

      `str` - the string to be written to the `CLOB` value that this `Clob` object represents

      `offset` - the offset into `str` to start reading the characters to be written

      `len` - the number of characters to be written

      Returns:
      the number of characters written

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if there is an error accessing the `CLOB` value

      Since:
      9.0.2 This method is currently not supported. Use setString( long pos, String str )

    <!-- -->

    - #### setAsciiStream

          public OutputStream setAsciiStream(long pos)
                                      throws SQLException

      Deprecated. 
      JDBC 3.0 Retrieves a stream to be used to write Ascii characters to the `CLOB` value that this `Clob` object represents, starting at position `pos`.
      Specified by:
      [`setAsciiStream`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#setAsciiStream_long_) in interface [`Clob`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true)

      Parameters:
      `pos` - the position at which to start writing to this `CLOB` object

      Returns:
      the stream to which ASCII encoded characters can be written

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if there is an error accessing the `CLOB` value

      Since:
      9.0.2

    <!-- -->

    - #### setCharacterStream

          public Writer setCharacterStream(long pos)
                                    throws SQLException

      Deprecated. 
      JDBC 3.0 Retrieves a stream to be used to write a stream of Unicode characters to the `CLOB` value that this `Clob` object represents, at position `pos`.
      Specified by:
      [`setCharacterStream`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#setCharacterStream_long_) in interface [`Clob`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true)

      Parameters:
      `pos` - the position at which to start writing to the `CLOB` value

      Returns:
      a stream to which Unicode encoded characters can be written

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if there is an error accessing the `CLOB` value

      Since:
      9.0.2

    <!-- -->

    - #### truncate

          public void truncate(long len)
                        throws SQLException

      Deprecated. 
      JDBC 3.0 Truncates the `CLOB` value that this `Clob` designates to have a length of `len` characters.
      Specified by:
      [`truncate`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#truncate_long_) in interface [`Clob`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true)

      Parameters:
      `len` - the length, in bytes, to which the `CLOB` value should be truncated

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if there is an error accessing the `CLOB` value

      Since:
      9.0.2

    <!-- -->

    - #### toJdbc

          public Object toJdbc()
                        throws SQLException

      Deprecated. 
      Convert this data object into its default Java object type.
      Specified by:
      `toJdbc` in interface `oracle.jdbc.internal.OracleDatumWithConnection`

      Specified by:
      [`toJdbc`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      this object.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if any of the lower layer code throws an exception.

    <!-- -->

    - #### isConvertibleTo

          public boolean isConvertibleTo(Class jClass)

      Deprecated. 
      Test whether this data object can be converted to the specified Java data type.
      Specified by:
      `isConvertibleTo` in interface `oracle.jdbc.internal.OracleDatumWithConnection`

      Specified by:
      [`isConvertibleTo`](Datum.md) in class [`Datum`](Datum.md)

      Parameters:
      `jClass` - specifies the Java data type to test against.

      Returns:
      true if this data object is convertible to the specified Java class, and a corresponding xxxValue() method is available; otherwise, a false is returned.

    <!-- -->

    - #### stringValue

          public String stringValue()
                             throws SQLException

      Deprecated. 
      Convert to a String representation of the datum object
      Specified by:
      `stringValue` in interface `oracle.jdbc.internal.OracleDatumWithConnection`

      Overrides:
      [`stringValue`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      String representation of the datum object

      Throws:
      `SQLException,` - if no String representation exists

      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getJavaSqlConnection

          public Connection getJavaSqlConnection()
                                          throws SQLException

      Deprecated. 
      Description copied from class: [`DatumWithConnection`](DatumWithConnection.md)
      Oracle extension Return the java.sql.Connection associated with the receiver. Since 9.0.0 not all Oracle JDBC connection objects are assignment compatible with oracle.jdbc.driver.OracleConnection. If the connection is wrapped, return the outermost wrapper.
      Specified by:
      `getJavaSqlConnection` in interface `oracle.jdbc.internal.OracleDatumWithConnection`

      Overrides:
      [`getJavaSqlConnection`](DatumWithConnection.md) in class [`DatumWithConnection`](DatumWithConnection.md)

      Returns:
      the connection

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if an error occurs

    <!-- -->

    - #### getPrefetchedDataSize

          public final int getPrefetchedDataSize()

      Deprecated. 

    <!-- -->

    - #### canReadBasicLobDataInLocator

          public boolean canReadBasicLobDataInLocator()
                                               throws SQLException

      Deprecated. 
      Can the lob data be read directly from the locator?
      Returns:
      True if we can; false otherwise.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### free

          public void free()
                    throws SQLException

      Deprecated. 
      Free the resources the clob holds.
      Specified by:
      [`free`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#free__) in interface [`Clob`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      11.0

    <!-- -->

    - #### getCharacterStream

          public Reader getCharacterStream(long pos,
                                           long length)
                                    throws SQLException

      Deprecated. 
      Return a character stream beginning at the specified position and ofthe specified length.
      Specified by:
      [`getCharacterStream`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true#getCharacterStream_long_long_) in interface [`Clob`](http://download.oracle.com/javase/8/docs/api/java/sql/Clob.html?is-external=true)

      Parameters:
      `pos` - start position

      `length` - number of characters in the result

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - - if pos is less than 1 or if pos is greater than the number of characters in the Clob or if pos + length is greater than the number of characters in the Clob or if an error occurs

      Since:
      11.0

    <!-- -->

    - #### setBytes

          public void setBytes(byte[] locator)

      Deprecated. 
      Description copied from class: [`Datum`](Datum.md)
      Sets datum value using a byte array. The byte array is copied.
      Specified by:
      `setBytes` in interface `oracle.jdbc.internal.OracleDatumWithConnection`

      Overrides:
      [`setBytes`](Datum.md) in class [`Datum`](Datum.md)

      Parameters:
      `locator` - byte array used to set the datum value

    <!-- -->

    - #### toSQLXML

          public SQLXML toSQLXML()
                          throws SQLException

      Deprecated. 
      Returns an object which impements java.sql.SQLXML with content take from this Clob.
      Specified by:
      [`toSQLXML`](../jdbc/OracleClob.md) in interface [`OracleClob`](../jdbc/OracleClob.md)

      Returns:
      the new SQLXML object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      12.2

    <!-- -->

    - #### toSQLXML

          public SQLXML toSQLXML(String schemaURL)
                          throws SQLException

      Deprecated. 
      Returns an object which impements java.sql.SQLXML with content taken from this Clob.
      Specified by:
      [`toSQLXML`](../jdbc/OracleClob.md) in interface [`OracleClob`](../jdbc/OracleClob.md)

      Returns:
      the new SQLXML object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      12.2

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/CLOB.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](CharacterWalker.md)
- [Next Class](ConcreteProxyUtil.md)

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
