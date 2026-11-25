Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleBlob.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleBfile.md)
- [Next Class](OracleCallableStatement.md)

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

## Interface OracleBlob

- All Superinterfaces:
  [Blob](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true)

  <!-- -->

  All Known Implementing Classes:
  [BLOB](../sql/BLOB.md)

  ------------------------------------------------------------------------



      public interface OracleBlob
      extends Blob

  This interface defines the Oracle extensions to the standard JDBC interface [`Blob`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true) .
  Generally any new code should avoid the direct use of the class [`BLOB`](../sql/BLOB.md). For variable declarations use the interface [`Blob`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true) or this interface as required. Instead of the static methods [`BLOB.createTemporary(java.sql.Connection, boolean, int)`](../sql/BLOB.md) and [`BLOB.empty_lob()`](../sql/BLOB.md) please use [`Connection.createBlob()`](http://download.oracle.com/javase/8/docs/api/java/sql/Connection.html?is-external=true#createBlob__) and [`BLOB.getEmptyBLOB()`](../sql/BLOB.md) respectively.

  Since:
  11.2.0.3

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                                       | Method and Description                                                                                                                                           |
    |---------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                                                  | `close``()`<br>Close a previously opened BLOB.                                                                                                                   |
    | [`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true) | `getBinaryStream``(long pos)`<br>Read from the BLOB as a stream at the requested position.                                                                       |
    | `int`                                                                                                   | `getBytes``(long pos, int length, byte[] buf)`<br>Oracle extension.                                                                                              |
    | `boolean`                                                                                               | `isEmptyLob``()`<br>Return true if the lob locator points to a empty blob.                                                                                       |
    | `boolean`                                                                                               | `isOpen``()`<br>Check whether the BLOB is opened.                                                                                                                |
    | `boolean`                                                                                               | `isSecureFile``()`<br>Returns `true` if this is a SecureFile (LOBs with the STORE AS SECUREFILE option, which were introduced in Oracle Database 11g Release 1). |
    | `boolean`                                                                                               | `isTemporary``()`<br>Return true if the lob locator points to a temporary blob.                                                                                  |
    | `void`                                                                                                  | `open``(`[`LargeObjectAccessMode`](LargeObjectAccessMode.md)` mode)`<br>Open a BLOB in the indicated mode.                                                       |
    | [`SQLXML`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLXML.html?is-external=true)          | `toSQLXML``()`<br>Returns an object which impements java.sql.SQLXML with content take from this Clob.                                                            |
    | [`SQLXML`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLXML.html?is-external=true)          | `toSQLXML``(int csid)`<br>Returns an object which impements java.sql.SQLXML with content taken from this Blob.                                                   |

    - ### Methods inherited from interface java.sql.[Blob](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true)

      [`free`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true#free__)`, `[`getBinaryStream`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true#getBinaryStream__)`, `[`getBinaryStream`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true#getBinaryStream_long_long_)`, `[`getBytes`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true#getBytes_long_int_)`, `[`length`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true#length__)`, `[`position`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true#position_java_sql_Blob_long_)`, `[`position`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true#position_byte_A_long_)`, `[`setBinaryStream`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true#setBinaryStream_long_)`, `[`setBytes`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true#setBytes_long_byte_A_)`, `[`setBytes`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true#setBytes_long_byte_A_int_int_)`, `[`truncate`](http://download.oracle.com/javase/8/docs/api/java/sql/Blob.html?is-external=true#truncate_long_)

<!-- -->

- - ### Method Detail

    - #### open

          void open(LargeObjectAccessMode mode)
             throws SQLException

      Open a BLOB in the indicated mode. Valid modes include MODE_READONLY, and MODE_READWRITE. It is an error to open the same LOB twice.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### close

          void close()
              throws SQLException

      Close a previously opened BLOB.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### isOpen

          boolean isOpen()
                  throws SQLException

      Check whether the BLOB is opened.
      Returns:
      true if the LOB is opened.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### getBytes

          int getBytes(long pos,
                       int length,
                       byte[] buf)
                throws SQLException

      Oracle extension. Copy the contents of the BLOB at the requested position to the supplied buffer.
      Parameters:
      `pos` - is the first byte of the blob to be extracted.

      `length` - is the number of consecutive bytes to be copied.

      `buf` - is the buffer to had the extracted bytes.

      Returns:
      a byte array containing a portion of the BLOB

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### isEmptyLob

          boolean isEmptyLob()
                      throws SQLException

      Return true if the lob locator points to a empty blob. False if it does not.
      Returns:
      true if the lob locator points to a empty blob. False if it does not.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.1.7

    <!-- -->

    - #### isSecureFile

          boolean isSecureFile()
                        throws SQLException

      Returns `true` if this is a SecureFile (LOBs with the STORE AS SECUREFILE option, which were introduced in Oracle Database 11g Release 1).
      Returns:
      `true` if this is a SecureFile and `false` otherwise.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getBinaryStream

          InputStream getBinaryStream(long pos)
                               throws SQLException

      Read from the BLOB as a stream at the requested position.
      Parameters:
      `pos` - is the position data to be read.

      Returns:
      a input stream to read data from the BLOB

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### isTemporary

          boolean isTemporary()
                       throws SQLException

      Return true if the lob locator points to a temporary blob. False if it does not.
      Returns:
      true if the lob locator points to a temporary blob. False if it does not.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### toSQLXML

          SQLXML toSQLXML()
                   throws SQLException

      Returns an object which impements java.sql.SQLXML with content take from this Clob.
      Returns:
      the new SQLXML object

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      12.2

    <!-- -->

    - #### toSQLXML

          SQLXML toSQLXML(int csid)
                   throws SQLException

      Returns an object which impements java.sql.SQLXML with content taken from this Blob.
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
- [Use](class-use/OracleBlob.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleBfile.md)
- [Next Class](OracleCallableStatement.md)

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
