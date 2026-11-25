Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleBfile.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleArray.md)
- [Next Class](OracleBlob.md)

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

## Interface OracleBfile

- All Known Implementing Classes:
  [BFILE](../sql/BFILE.md)

  ------------------------------------------------------------------------



      public interface OracleBfile

  This interface defines methods for Oracle specific Bfile. BFILE is an Oracle proprietary data type that provides read-only access to data located outside the database tablespaces.
  Since:
  11.2.0.3.0

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                                       | Method and Description                                                                                                          |
    |---------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                                                  | `close``()`<br>Close a previously opened external LOB.                                                                          |
    | `void`                                                                                                  | `closeFile``()`<br>Close the FILE.                                                                                              |
    | `boolean`                                                                                               | `fileExists``()`<br>Find out if a given BFILE (whose locator) points to a file that actually exists on the server's filesystem. |
    | [`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true) | `getBinaryStream``()`<br>Retrieve the entire BFILE as a stream.                                                                 |
    | [`InputStream`](http://download.oracle.com/javase/8/docs/api/java/io/InputStream.html?is-external=true) | `getBinaryStream``(long pos)`<br>Read from the external LOB as a stream at the requested position.                              |
    | `byte[]`                                                                                                | `getBytes``(long pos, int length)`<br>Return a copy of the contents of the BFILE at the requested position.                     |
    | `int`                                                                                                   | `getBytes``(long pos, int length, byte[] buf)`<br>Copy the contents of the BFILE at the requested position to suppied buffer.   |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getDirAlias``()`<br>Gets the Bfile's directory alias.                                                                          |
    | [`String`](http://download.oracle.com/javase/8/docs/api/java/lang/String.html?is-external=true)         | `getName``()`<br>Gets the Bfile's file name.                                                                                    |
    | `boolean`                                                                                               | `isFileOpen``()`<br>Find out whether a BFILE was opened                                                                         |
    | `boolean`                                                                                               | `isOpen``()`<br>Check whether the external LOB is opened.                                                                       |
    | `long`                                                                                                  | `length``()`<br>The length of the BFILE in bytes.                                                                               |
    | `void`                                                                                                  | `open``(`[`LargeObjectAccessMode`](LargeObjectAccessMode.md)` mode)`<br>Open a external LOB in the indicated mode.              |
    | `void`                                                                                                  | `openFile``()`<br>Open the FILE.                                                                                                |
    | `long`                                                                                                  | `position``(byte[] pattern, long start)`<br>Determine the byte position at which the given byte pattern                         |
    | `long`                                                                                                  | `position``(OracleBfile pattern, long start)`<br>Determine the byte position at which the given pattern                         |

<!-- -->

- - ### Method Detail

    - #### length

          long length()
               throws SQLException

      The length of the BFILE in bytes.
      Returns:
      length of the BFILE in bytes

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getBytes

          byte[] getBytes(long pos,
                          int length)
                   throws SQLException

      Return a copy of the contents of the BFILE at the requested position.
      Parameters:
      `pos` - is the first byte of the bfile to be extracted.(1-based)

      `length` - is the number of consecutive bytes to be copied.

      Returns:
      a byte array containing a portion of the BFILE

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getBytes

          int getBytes(long pos,
                       int length,
                       byte[] buf)
                throws SQLException

      Copy the contents of the BFILE at the requested position to suppied buffer.
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

          InputStream getBinaryStream()
                               throws SQLException

      Retrieve the entire BFILE as a stream.
      Returns:
      a stream containing the BFILE data

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getBinaryStream

          InputStream getBinaryStream(long pos)
                               throws SQLException

      Read from the external LOB as a stream at the requested position.
      Parameters:
      `pos` - is the position data to be read.

      Returns:
      a input stream to read data from the BFILE

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### position

          long position(byte[] pattern,
                        long start)
                 throws SQLException

      Determine the byte position at which the given byte pattern
      Parameters:
      `pattern` - is the pattern to search for.

      `start` - is the position at which to begin searching. (1-based)

      Returns:
      the position at which the pattern appears, else -1.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### position

          long position(OracleBfile pattern,
                        long start)
                 throws SQLException

      Determine the byte position at which the given pattern
      Parameters:
      `pattern` - is the pattern to search for.

      `start` - is the position at which to begin searching. (1-based)

      Returns:
      the position at which the pattern appears, else -1.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getName

          String getName()
                  throws SQLException

      Gets the Bfile's file name.
      Parameters:
      `bfile` - The Bfile for which to get the file name.

      Returns:
      The file name.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### getDirAlias

          String getDirAlias()
                      throws SQLException

      Gets the Bfile's directory alias.
      Parameters:
      `bfile` - The Bfile for which to get the directory alias.

      Returns:
      The directory alias name.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### openFile

          void openFile()
                 throws SQLException

      Open the FILE.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### isFileOpen

          boolean isFileOpen()
                      throws SQLException

      Find out whether a BFILE was opened
      Returns:
      true if the BFILE was opened, false if it was not opened.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### fileExists

          boolean fileExists()
                      throws SQLException

      Find out if a given BFILE (whose locator) points to a file that actually exists on the server's filesystem.
      Returns:
      true if the physical file exists, false if it does not exist.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### closeFile

          void closeFile()
                  throws SQLException

      Close the FILE.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

    <!-- -->

    - #### open

          void open(LargeObjectAccessMode mode)
             throws SQLException

      Open a external LOB in the indicated mode. Valid modes include MODE_READONLY only. It is an error to open the same LOB twice.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      11.2.0.3.0

    <!-- -->

    - #### close

          void close()
              throws SQLException

      Close a previously opened external LOB.
      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

    <!-- -->

    - #### isOpen

          boolean isOpen()
                  throws SQLException

      Check whether the external LOB is opened.
      Returns:
      true if the LOB is opened.

      Throws:
      [`SQLException`](http://download.oracle.com/javase/8/docs/api/java/sql/SQLException.html?is-external=true)

      Since:
      8.2.0

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Use](class-use/OracleBfile.md)
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Oracle JDBC Java API Reference
19*c* Release
E96460-08

- [Prev Class](OracleArray.md)
- [Next Class](OracleBlob.md)

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
