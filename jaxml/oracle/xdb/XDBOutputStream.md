Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](XDBError.md)**
- **[Next Class](XMLContext.md)**

<!-- -->

- **[Frames](../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../allclasses-noframe.md)**

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

**oracle.xdb**

## **Class XDBOutputStream**

- **java.lang.Object**

- - **java.io.OutputStream**

  - - **oracle.xdb.XDBOutputStream**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Closeable, java.io.Flushable, java.lang.AutoCloseable**

  <!-- -->

  **Direct Known Subclasses:**
  **[XDBRenderStream](event/XDBRenderStream.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XDBOutputStream
      extends java.io.OutputStream

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                |
    |-------------------|---------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `close``()`<br>Function to close the XDBOutputStream                                                                                  |
    | `void`            | `flush``()`<br>Function to flush the XDBOutputStream                                                                                  |
    | `void`            | `write``(byte[] b)`<br>Writes b.length bytes from the specified byte array to this output stream.                                     |
    | `void`            | `write``(byte[] b, int off, int len)`<br>Writes len bytes from the specified byte array starting at offset off to this output stream. |
    | `void`            | `write``(int b)`<br>Writes the specified byte to this output stream.                                                                  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### write

          public void write(byte[] b)

      Writes b.length bytes from the specified byte array to this output stream.
      Overrides:
      `write` in class `java.io.OutputStream`

      Parameters:
      `b` - The byte array to read into

    <!-- -->

    - #### write

          public void write(byte[] b,
                            int off,
                            int len)

      Writes len bytes from the specified byte array starting at offset off to this output stream.
      Overrides:
      `write` in class `java.io.OutputStream`

      Parameters:
      `b` - The byte array to read from

      `off` - Start offset of the data

      `len` - The number of bytes to write

    <!-- -->

    - #### write

          public void write(int b)

      Writes the specified byte to this output stream.
      Specified by:
      `write` in class `java.io.OutputStream`

      Parameters:
      `b` - byte to write

    <!-- -->

    - #### close

          public void close()

      Function to close the XDBOutputStream
      Specified by:
      `close` in interface `java.io.Closeable`

      Specified by:
      `close` in interface `java.lang.AutoCloseable`

      Overrides:
      `close` in class `java.io.OutputStream`

    <!-- -->

    - #### flush

          public void flush()

      Function to flush the XDBOutputStream
      Specified by:
      `flush` in interface `java.io.Flushable`

      Overrides:
      `flush` in class `java.io.OutputStream`

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](XDBError.md)**
- **[Next Class](XMLContext.md)**

<!-- -->

- **[Frames](../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../allclasses-noframe.md)**

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
