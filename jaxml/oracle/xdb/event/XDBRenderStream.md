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

- **[Prev Class](XDBPath.md)**
- **[Next Class](XDBRepositoryEvent.md)**

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

**oracle.xdb.event**

## **Class XDBRenderStream**

- **java.lang.Object**

- - **java.io.OutputStream**

  - - **[oracle.xdb.XDBOutputStream](../XDBOutputStream.md)**

    - - **oracle.xdb.event.XDBRenderStream**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Closeable, java.io.Flushable, java.lang.AutoCloseable**

  ------------------------------------------------------------------------

  **
  **

      public class XDBRenderStream
      extends XDBOutputStream

  **This class is used by the `XDBRepositoryEvent` class by `getOutputStream` and `setRenderStream` methods**
  **Since:**
  **11.1.0.0.0**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                |
    |-------------------|---------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `close``()`<br>Function to close the `XDBRenderStream`.                                                                               |
    | `void`            | `write``(byte[] b)`<br>Writes b.length bytes from specified byte array to this output stream.                                         |
    | `void`            | `write``(byte[] b, int off, int len)`<br>Writes len bytes from the specified byte array starting at offset off to this output stream. |
    | `void`            | `write``(int b)`<br>Writes the specified byte to this output stream.                                                                  |

    - ### Methods inherited from class oracle.xdb.[XDBOutputStream](../XDBOutputStream.md)

      [`flush`](../XDBOutputStream.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### write

          public void write(byte[] b)

      Writes b.length bytes from specified byte array to this output stream.
      Overrides:
      [`write`](../XDBOutputStream.md) in class [`XDBOutputStream`](../XDBOutputStream.md)

      Parameters:
      `b` - The byte array to read into

    <!-- -->

    - #### write

          public void write(byte[] b,
                            int off,
                            int len)

      Writes len bytes from the specified byte array starting at offset off to this output stream.
      Overrides:
      [`write`](../XDBOutputStream.md) in class [`XDBOutputStream`](../XDBOutputStream.md)

      Parameters:
      `b` - The byte array to read from

      `off` - Start offset of the data

      `len` - The number of bytes to write

    <!-- -->

    - #### write

          public void write(int b)

      Writes the specified byte to this output stream.
      Overrides:
      [`write`](../XDBOutputStream.md) in class [`XDBOutputStream`](../XDBOutputStream.md)

      Parameters:
      `b` - byte to write

    <!-- -->

    - #### close

          public void close()

      Function to close the `XDBRenderStream`. Cannot close the output stream from inside a handler.
      Specified by:
      `close` in interface `java.io.Closeable`

      Specified by:
      `close` in interface `java.lang.AutoCloseable`

      Overrides:
      [`close`](../XDBOutputStream.md) in class [`XDBOutputStream`](../XDBOutputStream.md)

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

- **[Prev Class](XDBPath.md)**
- **[Next Class](XDBRepositoryEvent.md)**

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
