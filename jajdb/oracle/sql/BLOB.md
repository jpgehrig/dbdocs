Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/BLOB.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](BINARY_FLOAT.md)
- [Next Class](CHAR.md)

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

## Class BLOB

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.sql.Datum](Datum.md)

  - - [oracle.sql.DatumWithConnection](DatumWithConnection.md)

    - - oracle.sql.BLOB

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), [Blob](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true), oracle.jdbc.internal.ACProxyable, oracle.jdbc.internal.OracleConcreteProxy, oracle.jdbc.internal.OracleDatumWithConnection, oracle.jdbc.internal.OracleLargeObject, [OracleBlob](../jdbc/OracleBlob.md)

  ------------------------------------------------------------------------

  Deprecated. 
  Use java.sql.Blob interface for declaration instead of using concrete class oracle.sql.BLOB.


      public class BLOB
      extends DatumWithConnection
      implements oracle.jdbc.internal.OracleBlob, oracle.jdbc.internal.OracleConcreteProxy

  This class implements the java.sql.Blob interface in JDBC 2.0. It provides the native implementation of the Blob methods. Use [`Blob`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true) interface for declaration instead of using concrete class oracle.sql.BLOB. java.sql.Blob has methods declared for all opertions. For Oracle specific methods use the interface [`OracleBlob`](../jdbc/OracleBlob.md).
  Obtaining Blob from ResultSet

  `java.sql.Blob blob = resultSet.getBlob(...);`
  Creating temporary Blob from factory method, `java.sql.Connection#crateBlob()`

  `java.sql.Blob blob = connection.createBlob();`
  See Also:
  [`Blob`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true), [`OracleBlob`](../jdbc/OracleBlob.md), [`Connection.createBlob()`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#createBlob__), [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type                         | Field and Description                                                                    |
    |-------------------------------------------|------------------------------------------------------------------------------------------|
    | `static int`                              | `DURATION_CALL`<br>Deprecated. <br>                                                      |
    | `static int`                              | `DURATION_INVALID`<br>Deprecated. <br>                                                   |
    | `static int`                              | `DURATION_SESSION`<br>Deprecated. <br>                                                   |
    | `static int`                              | `MAX_CHUNK_SIZE`<br>Deprecated. <br>1907584: Changed MAX_CHUNK_SIZE from 32512 to 32768. |
    | `static int`                              | `MODE_READONLY`<br>Deprecated. <br>                                                      |
    | `static int`                              | `MODE_READWRITE`<br>Deprecated. <br>                                                     |
    | `static int`                              | `OLD_WRONG_DURATION_CALL`<br>Deprecated. <br>                                            |
    | `static int`                              | `OLD_WRONG_DURATION_SESSION`<br>Deprecated. <br>                                         |
    | `protected oracle.jdbc.driver.OracleBlob` | `target`<br>Deprecated. <br>                                                             |
    | `static boolean`                          | `TRACE`<br>Deprecated. <br>                                                              |

    - ### Fields inherited from class oracle.sql.[DatumWithConnection](DatumWithConnection.md)

      [`targetDatumWithConnection`](DatumWithConnection.md)

    <!-- -->

    - ### Fields inherited from class oracle.sql.[Datum](Datum.md)

      [`ojiOracleDatumWithConnection`](Datum.md)`, `[`targetDatum`](Datum.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Modifier    | Constructor and Description                                                                    |
    |-------------|------------------------------------------------------------------------------------------------|
    | `protected` | `BLOB``()`<br>Deprecated. <br>                                                                 |
    | `protected` | `BLOB``(oracle.jdbc.driver.OracleBlob b)`<br>Deprecated. <br>Call from empty lob static method |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                                                         | Method and Description                                                                                                                                                                                                             |
    |-----------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                                                                                 | `canReadBasicLobDataInLocator``()`<br>Deprecated. <br>Can the lob data be read directly from the locator?                                                                                                                          |
    | `void`                                                                                                    | `close``()`<br>Deprecated. <br>Close a previously opened BLOB.                                                                                                                                                                     |
    | `static BLOB`                                                                                             | `createTemporary``(`[`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)` conn, boolean cache, int _duration)`<br>Deprecated. <br>Create a temporary blob.                       |
    | `static BLOB`                                                                                             | `empty_lob``()`<br>Deprecated. <br>use getEmptyBLOB instead                                                                                                                                                                        |
    | `void`                                                                                                    | `free``()`<br>Deprecated. <br>Free the resources the blob holds.                                                                                                                                                                   |
    | `void`                                                                                                    | `freeTemporary``()`<br>Deprecated. <br>Free the contents and the locator of the temporary blob.                                                                                                                                    |
    | `static void`                                                                                             | `freeTemporary``(BLOB temp_lob)`<br>Deprecated. <br>Free the contents and the locator of the temporary blob.                                                                                                                       |
    | [`OutputStream`](http://download.oracle.com/javase/8/docs/api/java/io/OutputStream.html?is-external=true) | `getBinaryOutputStream``()`<br>Deprecated. <br>This method is deprecated. Use setBinaryStream(1L).                                                                                                                                 |
    | [`OutputStream`](http://download.oracle.com/javase/8/docs/api/java/io/OutputStream.html?is-external=true) | `getBinaryOutputStream``(long pos)`<br>Deprecated. <br>This method is deprecated -- use setBinaryStream                                                                                                                            |
    | [`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)   | `getBinaryStream``()`<br>Deprecated. <br>Implements the Blob interface function.                                                                                                                                                   |
    | [`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)   | `getBinaryStream``(boolean isInternal)`<br>Deprecated. <br>Implements the Blob interface function.                                                                                                                                 |
    | [`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)   | `getBinaryStream``(long pos)`<br>Deprecated. <br>Read from the BLOB as a stream at the requested position.                                                                                                                         |
    | [`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true)   | `getBinaryStream``(long pos, long length)`<br>Deprecated. <br>Return a binary stream beginning at the specified position and ofthe specified length.                                                                               |
    | `int`                                                                                                     | `getBufferSize``()`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                           |
    | `byte[]`                                                                                                  | `getBytes``(long pos, int length)`<br>Deprecated. <br>Implements the Blob interface function.                                                                                                                                      |
    | `int`                                                                                                     | `getBytes``(long pos, int length, byte[] buf)`<br>Deprecated. <br>Oracle extension.                                                                                                                                                |
    | `int`                                                                                                     | `getChunkSize``()`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                            |
    | `short`                                                                                                   | `getDuration``()`<br>Deprecated. <br>return the duration of a temporary LOB                                                                                                                                                        |
    | `static short`                                                                                            | `getDuration``(BLOB lob)`<br>Deprecated. <br>return the duration of a temporary LOB                                                                                                                                                |
    | `static BLOB`                                                                                             | `getEmptyBLOB``()`<br>Deprecated. <br>Return a empty lob.                                                                                                                                                                          |
    | [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)    | `getJavaSqlConnection``()`<br>Deprecated. <br>Oracle extension Return the java.sql.Connection associated with the receiver.                                                                                                        |
    | `int`                                                                                                     | `getPrefetchedDataSize``()`<br>Deprecated. <br>                                                                                                                                                                                    |
    | `oracle.jdbc.driver.OracleBlob`                                                                           | `getTarget``()`<br>Deprecated. <br>                                                                                                                                                                                                |
    | `boolean`                                                                                                 | `isConvertibleTo``(`[`Class`](http://download.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)` jClass)`<br>Deprecated. <br>Oracle extension.                                                                   |
    | `boolean`                                                                                                 | `isEmptyLob``()`<br>Deprecated. <br>Return true if the lob locator points to a empty blob.                                                                                                                                         |
    | `boolean`                                                                                                 | `isOpen``()`<br>Deprecated. <br>Check whether the BLOB is opened.                                                                                                                                                                  |
    | `boolean`                                                                                                 | `isSecureFile``()`<br>Deprecated. <br>Returns `true` if this is a SecureFile (LOBs with the STORE AS SECUREFILE option, which were introduced in Oracle Database 11g Release 1).                                                   |
    | `boolean`                                                                                                 | `isTemporary``()`<br>Deprecated. <br>Return true if the lob locator points to a temporary blob.                                                                                                                                    |
    | `static boolean`                                                                                          | `isTemporary``(BLOB lob)`<br>Deprecated. <br>Return true if the lob locator points to a temporary blob.                                                                                                                            |
    | `long`                                                                                                    | `length``()`<br>Deprecated. <br>Implements the Blob interface function.                                                                                                                                                            |
    | `void`                                                                                                    | `open``(int mode)`<br>Deprecated. <br>Open a BLOB in the indicated mode.                                                                                                                                                           |
    | `void`                                                                                                    | `open``(`[`LargeObjectAccessMode`](../jdbc/LargeObjectAccessMode.md)` mode)`<br>Deprecated. <br>Public method using enum instead of int                                                                                            |
    | `long`                                                                                                    | `position``(`[`Blob`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true)` pattern, long start)`<br>Deprecated. <br>Implements the Blob interface function.                                          |
    | `long`                                                                                                    | `position``(byte[] pattern, long start)`<br>Deprecated. <br>Implements the Blob interface function.                                                                                                                                |
    | `int`                                                                                                     | `putBytes``(long pos, byte[] bytes)`<br>Deprecated. <br>This method is deprecated -- use setBytes                                                                                                                                  |
    | `int`                                                                                                     | `putBytes``(long pos, byte[] bytes, int length)`<br>Deprecated. <br>This method is deprecated -- use setBytes                                                                                                                      |
    | [`OutputStream`](http://download.oracle.com/javase/8/docs/api/java/io/OutputStream.html?is-external=true) | `setBinaryStream``(long pos)`<br>Deprecated. <br>JDBC 3.0 Retrieves a stream that can be used to write to the `BLOB` value that this `Blob` object represents.                                                                     |
    | `void`                                                                                                    | `setBytes``(byte[] locator)`<br>Deprecated. <br>Sets datum value using a byte array.                                                                                                                                               |
    | `int`                                                                                                     | `setBytes``(long pos, byte[] bytes)`<br>Deprecated. <br>JDBC 3.0 Writes the given array of bytes to the `BLOB` value that this `Blob` object represents, starting at position `pos`, and returns the number of bytes written.      |
    | `int`                                                                                                     | `setBytes``(long pos, byte[] bytes, int offset, int len)`<br>Deprecated. <br>JDBC 3.0 Writes all or part of the given `byte` array to the `BLOB` value that this `Blob` object represents and returns the number of bytes written. |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)           | `toJdbc``()`<br>Deprecated. <br>Oracle extension.                                                                                                                                                                                  |
    | [`SQLXML`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLXML.html?is-external=true)            | `toSQLXML``()`<br>Deprecated. <br>Returns an object which impements java.sql.SQLXML with content take from this Clob.                                                                                                              |
    | [`SQLXML`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLXML.html?is-external=true)            | `toSQLXML``(int csid)`<br>Deprecated. <br>Returns an object which impements java.sql.SQLXML with content taken from this Blob.                                                                                                     |
    | `void`                                                                                                    | `trim``(long newlen)`<br>Deprecated. <br>This method id deprecated -- use truncate                                                                                                                                                 |
    | `void`                                                                                                    | `truncate``(long len)`<br>Deprecated. <br>JDBC 3.0 Truncates the `BLOB` value that this `Blob` object represents to be `len` bytes in length.                                                                                      |

    - ### Methods inherited from class oracle.sql.[DatumWithConnection](DatumWithConnection.md)

      [`assertNotNull`](DatumWithConnection.md)`, `[`assertNotNull`](DatumWithConnection.md)`, `[`getConnection`](DatumWithConnection.md)`, `[`getConnectionDuringExceptionHandling`](DatumWithConnection.md)`, `[`getOracleConnection`](DatumWithConnection.md)

    <!-- -->

    - ### Methods inherited from class oracle.sql.[Datum](Datum.md)

      [`bigDecimalValue`](Datum.md)`, `[`booleanValue`](Datum.md)`, `[`bytesEqual`](Datum.md)`, `[`bytesHashCode`](Datum.md)`, `[`byteValue`](Datum.md)`, `[`compareBytes`](Datum.md)`, `[`dateValue`](Datum.md)`, `[`doubleValue`](Datum.md)`, `[`equals`](Datum.md)`, `[`floatValue`](Datum.md)`, `[`getBytes`](Datum.md)`, `[`getLength`](Datum.md)`, `[`getStream`](Datum.md)`, `[`intValue`](Datum.md)`, `[`isNull`](Datum.md)`, `[`longValue`](Datum.md)`, `[`setShareBytes`](Datum.md)`, `[`shareBytes`](Datum.md)`, `[`stringValue`](Datum.md)`, `[`stringValue`](Datum.md)`, `[`timestampValue`](Datum.md)`, `[`timestampValue`](Datum.md)`, `[`timeValue`](Datum.md)`, `[`timeValue`](Datum.md)`, `[`toClass`](Datum.md)

    <!-- -->

    - ### Methods inherited from class java.lang.[Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

      [`clone`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#clone__)`, `[`finalize`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#finalize__)`, `[`getClass`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#getClass__)`, `[`hashCode`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#hashCode__)`, `[`notify`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notify__)`, `[`notifyAll`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#notifyAll__)`, `[`toString`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#toString__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait__)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_)`, `[`wait`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true#wait_long_int_)

    <!-- -->

    - ### Methods inherited from interface oracle.jdbc.internal.OracleDatumWithConnection

      `bigDecimalValue, booleanValue, byteValue, dateValue, doubleValue, floatValue, getBytes, getConnection, getInternalConnection, getLength, getOracleConnection, getStream, intValue, longValue, setPhysicalConnectionOf, setShareBytes, shareBytes, stringValue, stringValue, timestampValue, timestampValue, timeValue, timeValue`

<!-- -->

- - ### Field Detail

    - #### MAX_CHUNK_SIZE

          public static final int MAX_CHUNK_SIZE

      Deprecated. 
      1907584: Changed MAX_CHUNK_SIZE from 32512 to 32768. This was done to accommodate larger DB_BLOCK_SIZEs. Using 32512 would cause getBufferSize() to return 32512 for DB_BLOCK_SIZEs from 8192-32768. For these block sizes getBufferSize() should return getChunkSize(); not 32512. By using 32768 as the MAX_CHUNK_SIZE, getBufferSize() returns the correct chunk size. Please see bug for details.
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

          protected oracle.jdbc.driver.OracleBlob target

      Deprecated. 

    <!-- -->

    - #### TRACE

          public static final boolean TRACE

      Deprecated. 
      See Also:
      [Constant Field Values](../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### BLOB

          protected BLOB()

      Deprecated. 

    <!-- -->

    - #### BLOB

          protected BLOB(oracle.jdbc.driver.OracleBlob b)

      Deprecated. 
      Call from empty lob static method

  <!-- -->

  - ### Method Detail

    - #### getTarget

          public oracle.jdbc.driver.OracleBlob getTarget()

      Deprecated. 

    <!-- -->

    - #### length

          public long length()
                      throws SQLException

      Deprecated. 
      Implements the Blob interface function. Return the length of the Binary Large OBject in bytes.
      Specified by:
      [`length`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true#length__) in interface [`Blob`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true)

      Returns:
      length of the BLOB in bytes

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getBytes

          public byte[] getBytes(long pos,
                                 int length)
                          throws SQLException

      Deprecated. 
      Implements the Blob interface function. Return a copy of the contents of the BLOB at the requested position.
      Specified by:
      [`getBytes`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true#getBytes_long_int_) in interface [`Blob`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true)

      Parameters:
      `pos` - is the first byte of the blob to be extracted.

      `length` - is the number of consecutive bytes to be copied.

      Returns:
      a byte array containing a portion of the BLOB If the `pos` argument is larger than the length of the data the result is null. If the `pos` argument is less than the length of the data, but the sum of `pos` argument and the `length` is greater than the length of the data, the result will be smaller than the length requested. If the `length` is zero return and empty array

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getBinaryStream

          public InputStream getBinaryStream()
                                      throws SQLException

      Deprecated. 
      Implements the Blob interface function. Retrieve the entire BLOB as a stream.
      Specified by:
      [`getBinaryStream`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true#getBinaryStream__) in interface [`Blob`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true)

      Returns:
      a stream containing the BLOB data

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getBinaryStream

          public InputStream getBinaryStream(boolean isInternal)
                                      throws SQLException

      Deprecated. 
      Implements the Blob interface function. Retrieve the entire BLOB as a stream.
      Returns:
      a stream containing the BLOB data

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### position

          public long position(byte[] pattern,
                               long start)
                        throws SQLException

      Deprecated. 
      Implements the Blob interface function. Determine the byte position at which the given byte pattern
      Specified by:
      [`position`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true#position_byte_A_long_) in interface [`Blob`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true)

      Parameters:
      `pattern` - is the pattern to search for.

      `start` - is the position at which to begin searching.

      Returns:
      the position at which the pattern appears, else -1.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### position

          public long position(Blob pattern,
                               long start)
                        throws SQLException

      Deprecated. 
      Implements the Blob interface function. Determine the byte position at which the given pattern
      Specified by:
      [`position`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true#position_java_sql_Blob_long_) in interface [`Blob`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true)

      Parameters:
      `pattern` - is the pattern to search for.

      `start` - is the position at which to begin searching.

      Returns:
      the position at which the pattern appears, else -1.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getBytes

          public int getBytes(long pos,
                              int length,
                              byte[] buf)
                       throws SQLException

      Deprecated. 
      Oracle extension. Copy the contents of the BLOB at the requested position to suppied buffer.
      Specified by:
      [`getBytes`](../jdbc/OracleBlob.md) in interface [`OracleBlob`](../jdbc/OracleBlob.md)

      Parameters:
      `pos` - is the first byte of the blob to be extracted.

      `length` - is the number of consecutive bytes to be copied.

      `buf` - is the buffer to had the extracted bytes.

      Returns:
      a byte array containing a portion of the BLOB

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### putBytes

          public int putBytes(long pos,
                              byte[] bytes)
                       throws SQLException

      Deprecated. This method is deprecated -- use setBytes
      Oracle extension. Put data to the BLOB at the requested position.
      Parameters:
      `pos` - is the position data to be put.

      `bytes` - is the data to be written into BLOB.

      Returns:
      the number of bytes actually written.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### putBytes

          public int putBytes(long pos,
                              byte[] bytes,
                              int length)
                       throws SQLException

      Deprecated. This method is deprecated -- use setBytes
      Oracle extension. Put data to the BLOB at the requested position.
      Parameters:
      `pos` - is the position data to be put.

      `bytes` - is the data to be written into BLOB.

      `length` - is the length of the data to be written into BLOB.

      Returns:
      the number of bytes actually written.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getBinaryOutputStream

          public OutputStream getBinaryOutputStream()
                                             throws SQLException

      Deprecated. This method is deprecated. Use setBinaryStream(1L).
      Oracle extension. Write to the BLOB from a stream.
      Returns:
      a output stream to write data to the BLOB

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getChunkSize

          public int getChunkSize()
                           throws SQLException

      Deprecated. 
      Oracle extension. Get database LOB storage chunk size in database.
      Returns:
      size in bytes

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getBufferSize

          public int getBufferSize()
                            throws SQLException

      Deprecated. 
      Oracle extension. Get ideal LOB db access buffer size.
      Returns:
      size in bytes

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### empty_lob

          public static BLOB empty_lob()
                                throws SQLException

      Deprecated. use getEmptyBLOB instead
      Return a empty lob. An empty lob is used initialize a LOB column/attribute. Note: an empty lob can not be read or written
      Returns:
      a empty lob

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.1.7

    <!-- -->

    - #### getEmptyBLOB

          public static BLOB getEmptyBLOB()
                                   throws SQLException

      Deprecated. 
      Return a empty lob. An empty lob is used initialize a BLOB column/attribute. Note: an empty lob can not be read or written
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
      Return true if the lob locator points to a empty blob. False if it does not. This method supports only Blobs that are not returned from the database. For Blobs returned from the database, use length(), i.e. check for zero length.
      Specified by:
      [`isEmptyLob`](../jdbc/OracleBlob.md) in interface [`OracleBlob`](../jdbc/OracleBlob.md)

      Returns:
      true if the lob locator points to a empty blob. False if it does not.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.1.7

    <!-- -->

    - #### isSecureFile

          public boolean isSecureFile()
                               throws SQLException

      Deprecated. 
      Returns `true` if this is a SecureFile (LOBs with the STORE AS SECUREFILE option, which were introduced in Oracle Database 11g Release 1).
      Specified by:
      [`isSecureFile`](../jdbc/OracleBlob.md) in interface [`OracleBlob`](../jdbc/OracleBlob.md)

      Returns:
      `true` if this is a SecureFile and `false` otherwise.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getBinaryOutputStream

          public OutputStream getBinaryOutputStream(long pos)
                                             throws SQLException

      Deprecated. This method is deprecated -- use setBinaryStream
      Write to the BLOB from a stream at the requested position.
      Parameters:
      `pos` - is the position data to be put.

      Returns:
      a output stream to write data to the BLOB

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### getBinaryStream

          public InputStream getBinaryStream(long pos)
                                      throws SQLException

      Deprecated. 
      Read from the BLOB as a stream at the requested position.
      Specified by:
      [`getBinaryStream`](../jdbc/OracleBlob.md) in interface [`OracleBlob`](../jdbc/OracleBlob.md)

      Parameters:
      `pos` - is the position data to be read, should be greater than 0.

      Returns:
      a input stream to read data from the BLOB

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### trim

          public void trim(long newlen)
                    throws SQLException

      Deprecated. This method id deprecated -- use truncate
      Trim the value of the BLOB to the length you specify in the newlen parameter.
      Parameters:
      `newlen` - the new length of the BLOB.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### createTemporary

          public static BLOB createTemporary(Connection conn,
                                             boolean cache,
                                             int _duration)
                                      throws SQLException

      Deprecated. 
      Create a temporary blob.
      Parameters:
      `cache` - Specifies if LOB should be read into buffer cache or not.

      `_duration` - The duration of the temporary LOB. The following are valid values: DURATION_SESSION, DURATION_CALL.

      Returns:
      A temporary blob.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### freeTemporary

          public static void freeTemporary(BLOB temp_lob)
                                    throws SQLException

      Deprecated. 
      Free the contents and the locator of the temporary blob.
      Parameters:
      `temp_lob` - A temporary blob to be freeed.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if temp_lob is a permanent lob or temp_lob has already been freed.

      Since:
      8.2.0

    <!-- -->

    - #### isTemporary

          public static boolean isTemporary(BLOB lob)
                                     throws SQLException

      Deprecated. 
      Return true if the lob locator points to a temporary blob. False if it does not.
      Parameters:
      `lob` - the blob to test.

      Returns:
      true if the lob locator points to a temporary blob. False if it does not.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### getDuration

          public static short getDuration(BLOB lob)
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
      Free the contents and the locator of the temporary blob.
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
      Return true if the lob locator points to a temporary blob. False if it does not.
      Specified by:
      `isTemporary` in interface `oracle.jdbc.internal.OracleLargeObject`

      Specified by:
      [`isTemporary`](../jdbc/OracleBlob.md) in interface [`OracleBlob`](../jdbc/OracleBlob.md)

      Returns:
      true if the lob locator points to a temporary blob. False if it does not.

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
      [`open`](../jdbc/OracleBlob.md) in interface [`OracleBlob`](../jdbc/OracleBlob.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### open

          public void open(int mode)
                    throws SQLException

      Deprecated. 
      Open a BLOB in the indicated mode. Valid modes include MODE_READONLY, and MODE_READWRITE. It is an error to open the same LOB twice.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### close

          public void close()
                     throws SQLException

      Deprecated. 
      Close a previously opened BLOB.
      Specified by:
      [`close`](../jdbc/OracleBlob.md) in interface [`OracleBlob`](../jdbc/OracleBlob.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### isOpen

          public boolean isOpen()
                         throws SQLException

      Deprecated. 
      Check whether the BLOB is opened.
      Specified by:
      [`isOpen`](../jdbc/OracleBlob.md) in interface [`OracleBlob`](../jdbc/OracleBlob.md)

      Returns:
      true if the LOB is opened.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### setBytes

          public int setBytes(long pos,
                              byte[] bytes)
                       throws SQLException

      Deprecated. 
      JDBC 3.0 Writes the given array of bytes to the `BLOB` value that this `Blob` object represents, starting at position `pos`, and returns the number of bytes written.
      Specified by:
      [`setBytes`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true#setBytes_long_byte_A_) in interface [`Blob`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true)

      Parameters:
      `pos` - the position in the `BLOB` object at which to start writing

      `bytes` - the array of bytes to be written to the `BLOB` value that this `Blob` object represents

      Returns:
      the number of bytes written

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if there is an error accessing the `BLOB` value

      Since:
      9.0.2

    <!-- -->

    - #### setBytes

          public int setBytes(long pos,
                              byte[] bytes,
                              int offset,
                              int len)
                       throws SQLException

      Deprecated. 
      JDBC 3.0 Writes all or part of the given `byte` array to the `BLOB` value that this `Blob` object represents and returns the number of bytes written. Writing starts at position `pos` in the `BLOB` value; `len` bytes from the given byte array are written.
      Specified by:
      [`setBytes`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true#setBytes_long_byte_A_int_int_) in interface [`Blob`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true)

      Parameters:
      `pos` - the position in the `BLOB` object at which to start writing

      `bytes` - the array of bytes to be written to this `BLOB` object

      `offset` - the offset into the array `bytes` at which to start reading the bytes to be set

      `len` - the number of bytes to be written to the `BLOB` value from the array of bytes `bytes`

      Returns:
      the number of bytes written

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if there is an error accessing the `BLOB` value

      Since:
      9.0.2

    <!-- -->

    - #### setBinaryStream

          public OutputStream setBinaryStream(long pos)
                                       throws SQLException

      Deprecated. 
      JDBC 3.0 Retrieves a stream that can be used to write to the `BLOB` value that this `Blob` object represents. The stream begins at position `pos`.
      Specified by:
      [`setBinaryStream`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true#setBinaryStream_long_) in interface [`Blob`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true)

      Parameters:
      `pos` - the position in the `BLOB` value at which to start writing

      Returns:
      a `java.io.OutputStream` object to which data can be written

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if there is an error accessing the `BLOB` value

      Since:
      9.0.2

      See Also:
      `getBinaryStream()`

    <!-- -->

    - #### truncate

          public void truncate(long len)
                        throws SQLException

      Deprecated. 
      JDBC 3.0 Truncates the `BLOB` value that this `Blob` object represents to be `len` bytes in length.
      Specified by:
      [`truncate`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true#truncate_long_) in interface [`Blob`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true)

      Parameters:
      `len` - the length, in bytes, to which the `BLOB` value that this `Blob` object represents should be truncated

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if there is an error accessing the `BLOB` value

      Since:
      9.0.2

    <!-- -->

    - #### toJdbc

          public Object toJdbc()
                        throws SQLException

      Deprecated. 
      Oracle extension. Convert this data object into its default Java object type.
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
      Oracle extension. Test whether this data object can be converted to the specified Java data type.
      Specified by:
      `isConvertibleTo` in interface `oracle.jdbc.internal.OracleDatumWithConnection`

      Specified by:
      [`isConvertibleTo`](Datum.md) in class [`Datum`](Datum.md)

      Parameters:
      `jClass` - specifies the Java data type to test against.

      Returns:
      true if this data object is convertible to the specified Java class, and a corresponding xxxValue() method is available; otherwise, a false is returned.

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
      Free the resources the blob holds.
      Specified by:
      [`free`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true#free__) in interface [`Blob`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      11.0

    <!-- -->

    - #### getBinaryStream

          public InputStream getBinaryStream(long pos,
                                             long length)
                                      throws SQLException

      Deprecated. 
      Return a binary stream beginning at the specified position and ofthe specified length.
      Specified by:
      [`getBinaryStream`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true#getBinaryStream_long_long_) in interface [`Blob`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true)

      Parameters:
      `pos` - start position

      `length` - number of bytes in the result

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true) - if pos is less than 1 or if pos is greater than the number of bytes in the Blob or if pos + length is greater than the number of bytes in the Blob.

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
      [`toSQLXML`](../jdbc/OracleBlob.md) in interface [`OracleBlob`](../jdbc/OracleBlob.md)

      Returns:
      the new SQLXML object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      12.2

    <!-- -->

    - #### toSQLXML

          public SQLXML toSQLXML(int csid)
                          throws SQLException

      Deprecated. 
      Returns an object which impements java.sql.SQLXML with content taken from this Blob.
      Specified by:
      [`toSQLXML`](../jdbc/OracleBlob.md) in interface [`OracleBlob`](../jdbc/OracleBlob.md)

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
- [Use](class-use/BLOB.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](BINARY_FLOAT.md)
- [Next Class](CHAR.md)

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
