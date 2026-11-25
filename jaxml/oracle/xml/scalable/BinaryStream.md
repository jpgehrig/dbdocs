Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](BinaryNav.md)**
- **[Next Class](FilePageManager.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**oracle.xml.scalable**

## **Class BinaryStream**

- **java.lang.Object**

- - **oracle.xml.scalable.BinaryStream**

<!-- -->

-

  ------------------------------------------------------------------------

  **
  **

      public class BinaryStream
      extends java.lang.Object

  **This class represents binary xml with write/read APIs. It is built on top of different binary source/storage: Blob, file, byte array and Input/output (object) stream. The stream is independent of the binary format and it is the base class for various binary stream implementations.**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description |
    |---------------------------|-----------------------|
    | `static java.lang.String` | `BINARY_FORMAT`       |
    | `static int`              | `BUFSIZE`             |
    | `static int`              | `NBUFFERS`            |
    | `static java.lang.String` | `SUN_FI`              |
    | `static java.lang.String` | `XDB_BINXML`          |
    | `static java.lang.String` | `XDK_CXML`            |
    | `static java.lang.String` | `XDK_XTI`             |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                   | Method and Description                                                                                                                                |
    |-------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                              | `close``()`<br>Closes data resoures allocated by this stream.                                                                                         |
    | `void`                              | `closeAll``()`<br>Closes all resources associated with this stream.                                                                                   |
    | `void`                              | `flush``()`<br>Flushes the stream.                                                                                                                    |
    | `void`                              | `flushBuffer``(byte[] buffer, int length)`<br>Flush write buffer with given length and stop                                                           |
    | `void`                              | `flushBuffer``(byte[] buffer, int offset, int length)`<br>Flush write buffer with given length and stop                                               |
    | `void`                              | `flushWriBuffer``()`<br>Flush the whole write buffer and continue                                                                                     |
    | `void`                              | `flushWriBuffer``(int length)`<br>Flush write buffer with given length and stop                                                                       |
    | [`BinaryIndex`](BinaryIndex.md)     | `getBinaryIndex``()`<br>Get the index                                                                                                                 |
    | `int`                               | `getBufferSize``()`<br>Get the size of the buffer                                                                                                     |
    | `byte[]`                            | `getByteArray``()`<br>Get byte array                                                                                                                  |
    | [`DTD`](../parser/v2/DTD.md)        | `getDTD``()`<br>Get DTD                                                                                                                               |
    | `java.lang.String`                  | `getEncoding``()`<br>Get Encoding                                                                                                                     |
    | [`InfosetReader`](InfosetReader.md) | `getInfosetReader``()`<br>Get InfosetReader from the BinaryStream                                                                                     |
    | [`InfosetWriter`](InfosetWriter.md) | `getInfosetWriter``()`<br>Get InfosetWriter from the BinaryStream                                                                                     |
    | `long`                              | `getSize``()`<br>Get the size of the BinaryStream                                                                                                     |
    | `java.lang.String`                  | `getStandalone``()`<br>Get Standalone                                                                                                                 |
    | `java.lang.String`                  | `getSystemId``()`                                                                                                                                     |
    | `java.util.Vector`                  | `getTypeList``()`<br>Get typeList                                                                                                                     |
    | `java.lang.String`                  | `getVersion``()`<br>Get Version                                                                                                                       |
    | `byte[]`                            | `getWriteBuffer``()`                                                                                                                                  |
    | `java.io.OutputStream`              | `getWriteStream``()`                                                                                                                                  |
    | `boolean`                           | `isIndexingSupported``()`<br>Check if indexing is supported                                                                                           |
    | `boolean`                           | `isSeekSupported``()`<br>Check if the stream supports seek                                                                                            |
    | `byte[]`                            | `load``(int pageid, boolean forupdate)`                                                                                                               |
    | `byte[]`                            | `load``(int pageid, int size, boolean forupdate)`                                                                                                     |
    | `static BinaryStream`               | `newInstance``(java.lang.String format)`<br>Factory method to creat format specific BinaryStream                                                      |
    | `void`                              | `readToPageManager``()`<br>Read binary from InputStream to PageManger then close InputStream and release it.                                          |
    | `void`                              | `reset``()`                                                                                                                                           |
    | `void`                              | `setBlob``(java.sql.Blob b)`<br>Set a Blob as the binary source                                                                                       |
    | `void`                              | `setByteArray``(byte[] array)`<br>Set byte array                                                                                                      |
    | `void`                              | `setDTD``(`[`DTD`](../parser/v2/DTD.md)` dtd)`<br>Set DTD                                                                                             |
    | `void`                              | `setEncoding``(java.lang.String enc)`<br>Set Encoding                                                                                                 |
    | `void`                              | `setFile``(java.io.File f)`<br>Set a file as the binary storage                                                                                       |
    | `void`                              | `setInputStream``(java.io.InputStream ois)`<br>Set a InputStream to read data                                                                         |
    | `void`                              | `setOutputStream``(java.io.OutputStream oos)`<br>Set a OutputStream to write to                                                                       |
    | `void`                              | `setPageManager``(`[`PageManager`](PageManager.md)` pageMgr)`<br>Set pageManager to cache binary, stream becomes seekable when source is InputStream. |
    | `void`                              | `setStandalone``(java.lang.String sda)`<br>Set Standalone                                                                                             |
    | `void`                              | `setSystemId``(java.lang.String id)`                                                                                                                  |
    | `void`                              | `setVersion``(java.lang.String ver)`<br>Set Version                                                                                                   |
    | `void`                              | `unload``(int pageid, boolean forupdate, byte[] page)`                                                                                                |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### NBUFFERS

          public static int NBUFFERS

    <!-- -->

    - #### BUFSIZE

          public static int BUFSIZE

    <!-- -->

    - #### BINARY_FORMAT

          public static final java.lang.String BINARY_FORMAT

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XDK_CXML

          public static final java.lang.String XDK_CXML

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XDB_BINXML

          public static final java.lang.String XDB_BINXML

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SUN_FI

          public static final java.lang.String SUN_FI

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### XDK_XTI

          public static final java.lang.String XDK_XTI

      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### newInstance

          public static BinaryStream newInstance(java.lang.String format)

      Factory method to creat format specific BinaryStream
      Parameters:
      `format` - - String for the binary format

      Returns:
      format specific binary stream.

    <!-- -->

    - #### getInfosetReader

          public InfosetReader getInfosetReader()

      Get InfosetReader from the BinaryStream
      Returns:
      InfosetReader, null if stream doesn't support streaming decoding

    <!-- -->

    - #### getInfosetWriter

          public InfosetWriter getInfosetWriter()

      Get InfosetWriter from the BinaryStream
      Returns:
      InfosetWriter, null if stream doesn't support streaming encoding

    <!-- -->

    - #### isIndexingSupported

          public boolean isIndexingSupported()

      Check if indexing is supported
      Returns:
      trure if indexing is supported, false otherwise

    <!-- -->

    - #### getBinaryIndex

          public BinaryIndex getBinaryIndex()

      Get the index
      Returns:
      the full element index if indexing is supported, null otherwise

    <!-- -->

    - #### getSize

          public long getSize()

      Get the size of the BinaryStream
      Returns:
      the size of the stream

    <!-- -->

    - #### getBufferSize

          public int getBufferSize()

      Get the size of the buffer
      Returns:
      the size of the buffer

    <!-- -->

    - #### setDTD

          public void setDTD(DTD dtd)

      Set DTD
      Parameters:
      `dtd` - the DTD to set

    <!-- -->

    - #### getDTD

          public DTD getDTD()

      Get DTD
      Returns:
      dtd the DTD of the stream

    <!-- -->

    - #### setEncoding

          public void setEncoding(java.lang.String enc)

      Set Encoding
      Parameters:
      `enc` - the encoding string to set

    <!-- -->

    - #### getEncoding

          public java.lang.String getEncoding()

      Get Encoding
      Returns:
      encoding the encoding string

    <!-- -->

    - #### setStandalone

          public void setStandalone(java.lang.String sda)

      Set Standalone
      Parameters:
      `sda` - the standalone string to set

    <!-- -->

    - #### getStandalone

          public java.lang.String getStandalone()

      Get Standalone
      Returns:
      the standalone string

    <!-- -->

    - #### setVersion

          public void setVersion(java.lang.String ver)

      Set Version
      Parameters:
      `ver` - the version string to set

    <!-- -->

    - #### getTypeList

          public java.util.Vector getTypeList()

      Get typeList
      Returns:
      the Vector of typeList

    <!-- -->

    - #### isSeekSupported

          public boolean isSeekSupported()

      Check if the stream supports seek
      Returns:
      true if seek is supported, false otherwise.

    <!-- -->

    - #### getVersion

          public java.lang.String getVersion()

      Get Version
      Returns:
      the version string

    <!-- -->

    - #### setOutputStream

          public void setOutputStream(java.io.OutputStream oos)

      Set a OutputStream to write to
      Parameters:
      `oos` - - OutputStream source stream

    <!-- -->

    - #### setBlob

          public void setBlob(java.sql.Blob b)
                       throws java.io.IOException

      Set a Blob as the binary source
      Parameters:
      `b` - - Blob binary storage

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### setFile

          public void setFile(java.io.File f)
                       throws java.io.IOException

      Set a file as the binary storage
      Parameters:
      `f` - - file for binary storage

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### setInputStream

          public void setInputStream(java.io.InputStream ois)

      Set a InputStream to read data
      Parameters:
      `ois` - - InputStream source stream

    <!-- -->

    - #### setByteArray

          public void setByteArray(byte[] array)

      Set byte array
      Parameters:
      `array` - - Byte array for input and output

    <!-- -->

    - #### getByteArray

          public byte[] getByteArray()

      Get byte array

    <!-- -->

    - #### setPageManager

          public void setPageManager(PageManager pageMgr)

      Set pageManager to cache binary, stream becomes seekable when source is InputStream. This setting has no effect if the the source is already seekable.
      Parameters:
      `pageMgr` - - PageManager to be used.

    <!-- -->

    - #### readToPageManager

          public void readToPageManager()

      Read binary from InputStream to PageManger then close InputStream and release it. No op if pageManager is not set, or binary already read
      Throws:
      `java.io.IOException` - for any error during the read

    <!-- -->

    - #### load

          public byte[] load(int pageid,
                             boolean forupdate)

    <!-- -->

    - #### load

          public byte[] load(int pageid,
                             int size,
                             boolean forupdate)

    <!-- -->

    - #### unload

          public void unload(int pageid,
                             boolean forupdate,
                             byte[] page)

    <!-- -->

    - #### getWriteBuffer

          public byte[] getWriteBuffer()

    <!-- -->

    - #### getWriteStream

          public java.io.OutputStream getWriteStream()

    <!-- -->

    - #### flushWriBuffer

          public void flushWriBuffer()
                              throws java.io.IOException

      Flush the whole write buffer and continue
      Throws:
      `java.io.IOException`

    <!-- -->

    - #### flushWriBuffer

          public void flushWriBuffer(int length)
                              throws java.io.IOException

      Flush write buffer with given length and stop
      Throws:
      `java.io.IOException`

    <!-- -->

    - #### flushBuffer

          public void flushBuffer(byte[] buffer,
                                  int length)
                           throws java.io.IOException

      Flush write buffer with given length and stop
      Throws:
      `java.io.IOException`

    <!-- -->

    - #### flushBuffer

          public void flushBuffer(byte[] buffer,
                                  int offset,
                                  int length)
                           throws java.io.IOException

      Flush write buffer with given length and stop
      Throws:
      `java.io.IOException`

    <!-- -->

    - #### flush

          public void flush()
                     throws java.io.IOException

      Flushes the stream. This will write any buffered output bytes.
      Throws:
      `java.io.IOException` - If an I/O error has occurred.

    <!-- -->

    - #### reset

          public void reset()

    <!-- -->

    - #### setSystemId

          public void setSystemId(java.lang.String id)

    <!-- -->

    - #### getSystemId

          public java.lang.String getSystemId()

    <!-- -->

    - #### close

          public void close()

      Closes data resoures allocated by this stream.

    <!-- -->

    - #### closeAll

          public void closeAll()
                        throws java.io.IOException

      Closes all resources associated with this stream.
      Throws:
      `java.io.IOException` - If an I/O error has occurred.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](BinaryNav.md)**
- **[Next Class](FilePageManager.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
