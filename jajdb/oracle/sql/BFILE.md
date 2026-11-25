Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/BFILE.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](AttributeDescriptor.md)
- [Next Class](BINARY_DOUBLE.md)

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

## Class BFILE

- [java.lang.Object](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)

- - [oracle.sql.Datum](Datum.md)

  - - [oracle.sql.DatumWithConnection](DatumWithConnection.md)

    - - oracle.sql.BFILE

<!-- -->

- All Implemented Interfaces:
  [Serializable](http://download.oracle.com/javase/8/docs/api/java/io/Serializable.html?is-external=true), oracle.jdbc.internal.ACProxyable, oracle.jdbc.internal.OracleConcreteProxy, oracle.jdbc.internal.OracleDatumWithConnection, [OracleBfile](../jdbc/OracleBfile.md)

  ------------------------------------------------------------------------

  Deprecated. 
  Use oracle.jdbc.OracleBfile interface for declaration instead of using concrete class oracle.sql.BFILE.


      public class BFILE
      extends DatumWithConnection
      implements oracle.jdbc.internal.OracleBfile, oracle.jdbc.internal.OracleConcreteProxy

  A class for Oracle specific data type BFILE. Use [`OracleBfile`](../jdbc/OracleBfile.md) interface for declaration instead of using concrete class oracle.sql.BFILE. [`OracleBfile`](../jdbc/OracleBfile.md) has methods declared for all opertions.
  Obtaining OracleBfile from a [`ResultSet`](http://download.oracle.com/javase/8/docs/api/java/sql/ResultSet.html?is-external=true)

  `oracle.jdbc.OracleBfile bfile = ((OracleResultSet)resultSet).getBFILE(...);` There is no way to create [`OracleBfile`](../jdbc/OracleBfile.md) on the client side.
  See Also:
  [`OracleBfile`](../jdbc/OracleBfile.md), [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type                          | Field and Description                 |
    |--------------------------------------------|---------------------------------------|
    | `static int`                               | `MAX_CHUNK_SIZE`<br>Deprecated. <br>  |
    | `static int`                               | `MODE_READONLY`<br>Deprecated. <br>   |
    | `static int`                               | `MODE_READWRITE`<br>Deprecated. <br>  |
    | `protected oracle.jdbc.driver.OracleBfile` | `target`<br>Deprecated. <br>          |

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
    | `protected` | `BFILE``()`<br>Deprecated. <br>  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                                                       | Method and Description                                                                                                                                                                                                         |
    |---------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true) | `asciiStreamValue``()`<br>Deprecated. <br>Convert to an ascii stream representation of the datum object                                                                                                                        |
    | `void`                                                                                                  | `close``()`<br>Deprecated. <br>Close a previously opened external LOB.                                                                                                                                                         |
    | `void`                                                                                                  | `closeFile``()`<br>Deprecated. <br>Close the FILE.                                                                                                                                                                             |
    | `boolean`                                                                                               | `fileExists``()`<br>Deprecated. <br>Find out if a given BFILE (whose locator) points to a file that actually exists on the server's filesystem.                                                                                |
    | [`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true) | `getBinaryStream``()`<br>Deprecated. <br>Retrieve the entire BFILE as a stream.                                                                                                                                                |
    | [`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true) | `getBinaryStream``(long pos)`<br>Deprecated. <br>Read from the external LOB as a stream at the requested position.                                                                                                             |
    | `byte[]`                                                                                                | `getBytes``(long pos, int length)`<br>Deprecated. <br>Return a copy of the contents of the BFILE at the requested position.                                                                                                    |
    | `int`                                                                                                   | `getBytes``(long pos, int length, byte[] buf)`<br>Deprecated. <br>Copy the contents of the BFILE at the requested position to suppied buffer.                                                                                  |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getDirAlias``()`<br>Deprecated. <br>Gets the Bfile's directory alias.                                                                                                                                                         |
    | [`Connection`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true)  | `getJavaSqlConnection``()`<br>Deprecated. <br>Oracle extension Return the java.sql.Connection associated with the receiver.                                                                                                    |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getName``()`<br>Deprecated. <br>Gets the Bfile's file name.                                                                                                                                                                   |
    | `oracle.jdbc.driver.OracleBfile`                                                                        | `getTarget``()`<br>Deprecated. <br>                                                                                                                                                                                            |
    | `boolean`                                                                                               | `isConvertibleTo``(`[`Class`](http://download.oracle.com/javase/8/docs/api/java/lang/Class.html?is-external=true)` jClass)`<br>Deprecated. <br>Test whether this data object can be converted to the specified Java data type. |
    | `boolean`                                                                                               | `isFileOpen``()`<br>Deprecated. <br>Find out whether a BFILE was opened with the give BFILE.                                                                                                                                   |
    | `boolean`                                                                                               | `isOpen``()`<br>Deprecated. <br>Check whether the external LOB is opened.                                                                                                                                                      |
    | `long`                                                                                                  | `length``()`<br>Deprecated. <br>The length of the BFILE in bytes.                                                                                                                                                              |
    | `void`                                                                                                  | `open``()`<br>Deprecated. <br>Open a external LOB in the readonly mode.                                                                                                                                                        |
    | `void`                                                                                                  | `open``(int mode)`<br>Deprecated. <br>Open a external LOB in the indicated mode.                                                                                                                                               |
    | `void`                                                                                                  | `open``(`[`LargeObjectAccessMode`](../jdbc/LargeObjectAccessMode.md)` mode)`<br>Deprecated. <br>Public method using enum instead of int                                                                                        |
    | `void`                                                                                                  | `openFile``()`<br>Deprecated. <br>Open the FILE.                                                                                                                                                                               |
    | `long`                                                                                                  | `position``(BFILE pattern, long start)`<br>Deprecated. <br>Determine the byte position at which the given pattern                                                                                                              |
    | `long`                                                                                                  | `position``(byte[] pattern, long start)`<br>Deprecated. <br>Determine the byte position at which the given byte pattern                                                                                                        |
    | `long`                                                                                                  | `position``(`[`OracleBfile`](../jdbc/OracleBfile.md)` pattern, long start)`<br>Deprecated. <br>Determine the byte position at which the given pattern                                                                          |
    | `void`                                                                                                  | `setBytes``(byte[] locator)`<br>Deprecated. <br>Sets datum value using a byte array.                                                                                                                                           |
    | [`Object`](http://download.oracle.com/javase/8/docs/api/java/lang/Object.html?is-external=true)         | `toJdbc``()`<br>Deprecated. <br>Convert this data object into its default Java object type.                                                                                                                                    |

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

          protected oracle.jdbc.driver.OracleBfile target

      Deprecated. 

  <!-- -->

  - ### Constructor Detail

    - #### BFILE

          protected BFILE()

      Deprecated. 

  <!-- -->

  - ### Method Detail

    - #### getTarget

          public oracle.jdbc.driver.OracleBfile getTarget()

      Deprecated. 

    <!-- -->

    - #### length

          public long length()
                      throws SQLException

      Deprecated. 
      The length of the BFILE in bytes.
      Specified by:
      [`length`](../jdbc/OracleBfile.md) in interface [`OracleBfile`](../jdbc/OracleBfile.md)

      Returns:
      length of the BFILE in bytes

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getBytes

          public byte[] getBytes(long pos,
                                 int length)
                          throws SQLException

      Deprecated. 
      Return a copy of the contents of the BFILE at the requested position.
      Specified by:
      [`getBytes`](../jdbc/OracleBfile.md) in interface [`OracleBfile`](../jdbc/OracleBfile.md)

      Parameters:
      `pos` - is the first byte of the bfile to be extracted.(1-based)

      `length` - is the number of consecutive bytes to be copied.

      Returns:
      a byte array containing a portion of the BFILE

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getBytes

          public int getBytes(long pos,
                              int length,
                              byte[] buf)
                       throws SQLException

      Deprecated. 
      Copy the contents of the BFILE at the requested position to suppied buffer.
      Specified by:
      [`getBytes`](../jdbc/OracleBfile.md) in interface [`OracleBfile`](../jdbc/OracleBfile.md)

      Parameters:
      `pos` - is the first byte of the bfile to be extracted. (1-based)

      `length` - is the number of consecutive bytes to be copied.

      `buf` - is the buffer to had the extracted bytes.

      Returns:
      a byte array containing a portion of the BFILE

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getBinaryStream

          public InputStream getBinaryStream()
                                      throws SQLException

      Deprecated. 
      Retrieve the entire BFILE as a stream.
      Specified by:
      [`getBinaryStream`](../jdbc/OracleBfile.md) in interface [`OracleBfile`](../jdbc/OracleBfile.md)

      Returns:
      a stream containing the BFILE data

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### position

          public long position(byte[] pattern,
                               long start)
                        throws SQLException

      Deprecated. 
      Determine the byte position at which the given byte pattern
      Specified by:
      [`position`](../jdbc/OracleBfile.md) in interface [`OracleBfile`](../jdbc/OracleBfile.md)

      Parameters:
      `pattern` - is the pattern to search for.

      `start` - is the position at which to begin searching. (1-based)

      Returns:
      the position at which the pattern appears, else -1.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### position

          public long position(BFILE pattern,
                               long start)
                        throws SQLException

      Deprecated. 
      Determine the byte position at which the given pattern
      Parameters:
      `pattern` - is the pattern to search for.

      `start` - is the position at which to begin searching. (1-based)

      Returns:
      the position at which the pattern appears, else -1.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### position

          public long position(OracleBfile pattern,
                               long start)
                        throws SQLException

      Deprecated. 
      Determine the byte position at which the given pattern
      Specified by:
      [`position`](../jdbc/OracleBfile.md) in interface [`OracleBfile`](../jdbc/OracleBfile.md)

      Parameters:
      `pattern` - is the pattern to search for.

      `start` - is the position at which to begin searching. (1-based)

      Returns:
      the position at which the pattern appears, else -1.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getName

          public String getName()
                         throws SQLException

      Deprecated. 
      Gets the Bfile's file name.
      Specified by:
      [`getName`](../jdbc/OracleBfile.md) in interface [`OracleBfile`](../jdbc/OracleBfile.md)

      Parameters:
      `bfile` - The Bfile for which to get the file name.

      Returns:
      The file name.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getDirAlias

          public String getDirAlias()
                             throws SQLException

      Deprecated. 
      Gets the Bfile's directory alias.
      Specified by:
      [`getDirAlias`](../jdbc/OracleBfile.md) in interface [`OracleBfile`](../jdbc/OracleBfile.md)

      Parameters:
      `bfile` - The Bfile for which to get the directory alias.

      Returns:
      The directory alias name.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### openFile

          public void openFile()
                        throws SQLException

      Deprecated. 
      Open the FILE.
      Specified by:
      [`openFile`](../jdbc/OracleBfile.md) in interface [`OracleBfile`](../jdbc/OracleBfile.md)

      Parameters:
      `bfile` - The BFILE object to be opened.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### isFileOpen

          public boolean isFileOpen()
                             throws SQLException

      Deprecated. 
      Find out whether a BFILE was opened with the give BFILE.
      Specified by:
      [`isFileOpen`](../jdbc/OracleBfile.md) in interface [`OracleBfile`](../jdbc/OracleBfile.md)

      Parameters:
      `bfile` - The Bfile to be tested.

      Returns:
      true if the BFILE was opened, false if it was not opened.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### fileExists

          public boolean fileExists()
                             throws SQLException

      Deprecated. 
      Find out if a given BFILE (whose locator) points to a file that actually exists on the server's filesystem.
      Specified by:
      [`fileExists`](../jdbc/OracleBfile.md) in interface [`OracleBfile`](../jdbc/OracleBfile.md)

      Parameters:
      `bfile` - The Bfile to be tested.

      Returns:
      true if the physical file exists, false if it does not exist.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### closeFile

          public void closeFile()
                         throws SQLException

      Deprecated. 
      Close the FILE.
      Specified by:
      [`closeFile`](../jdbc/OracleBfile.md) in interface [`OracleBfile`](../jdbc/OracleBfile.md)

      Parameters:
      `bfile` - The Bfile to be closed.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getBinaryStream

          public InputStream getBinaryStream(long pos)
                                      throws SQLException

      Deprecated. 
      Read from the external LOB as a stream at the requested position.
      Specified by:
      [`getBinaryStream`](../jdbc/OracleBfile.md) in interface [`OracleBfile`](../jdbc/OracleBfile.md)

      Parameters:
      `pos` - is the position data to be read.

      Returns:
      a input stream to read data from the BFILE

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### open

          public void open()
                    throws SQLException

      Deprecated. 
      Open a external LOB in the readonly mode. It is an error to open the same LOB twice.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### open

          public void open(LargeObjectAccessMode mode)
                    throws SQLException

      Deprecated. 
      Public method using enum instead of int
      Specified by:
      [`open`](../jdbc/OracleBfile.md) in interface [`OracleBfile`](../jdbc/OracleBfile.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### open

          public void open(int mode)
                    throws SQLException

      Deprecated. 
      Open a external LOB in the indicated mode. Valid modes include MODE_READONLY only. It is an error to open the same LOB twice.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### close

          public void close()
                     throws SQLException

      Deprecated. 
      Close a previously opened external LOB.
      Specified by:
      [`close`](../jdbc/OracleBfile.md) in interface [`OracleBfile`](../jdbc/OracleBfile.md)

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### isOpen

          public boolean isOpen()
                         throws SQLException

      Deprecated. 
      Check whether the external LOB is opened.
      Specified by:
      [`isOpen`](../jdbc/OracleBfile.md) in interface [`OracleBfile`](../jdbc/OracleBfile.md)

      Returns:
      true if the LOB is opened.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

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

    - #### asciiStreamValue

          public InputStream asciiStreamValue()
                                       throws SQLException

      Deprecated. 
      Convert to an ascii stream representation of the datum object
      Specified by:
      `asciiStreamValue` in interface `oracle.jdbc.internal.OracleDatumWithConnection`

      Overrides:
      [`asciiStreamValue`](Datum.md) in class [`Datum`](Datum.md)

      Returns:
      ascii stream representation of the datum object

      Throws:
      `SQLException,` - if no ascii stream representation exists

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

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/BFILE.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](AttributeDescriptor.md)
- [Next Class](BINARY_DOUBLE.md)

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
