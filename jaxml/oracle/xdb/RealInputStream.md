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

- **[Prev Class](CState.md)**
- **[Next Class](SQLXMLType.md)**

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

## **Class RealInputStream**

- **java.lang.Object**

- - **java.io.InputStream**

  - - **oracle.xdb.RealInputStream**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Closeable, java.lang.AutoCloseable**

  ------------------------------------------------------------------------

  **
  **

      public class RealInputStream
      extends java.io.InputStream

  **Class that provides an inputstream abstraction to support reading from an underlying oracle stream.**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description                            |
    |-------------------|--------------------------------------------------|
    | `static int`      | `KGHSSTREAM`<br>Constant to denote a kghsstream. |
    | `static int`      | `OCISTREAM`<br>Constant to denote an ocistream.  |

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                  |
    |----------------------------------------------------------------------------------------------|
    | `RealInputStream``(java.sql.Connection conn, long c_state, int type)`<br>Public constructor. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                              |
    |-------------------|-----------------------------------------------------------------------------------------------------|
    | `void`            | `close``()`<br>Function to close the RealInputStream                                                |
    | `boolean`         | `markSupported``()`<br>Function to check if "mark" and "reset" are supported                        |
    | `int`             | `read``()`<br>Function to read the next byte of data                                                |
    | `int`             | `read``(byte[] b)`<br>Function to read upto b.length bytes of data into a byte array                |
    | `int`             | `read``(byte[] b, int off, int len)`<br>Function to read upto "len" bytes of data into a byte array |

    - ### Methods inherited from class java.io.InputStream

      `available, mark, reset, skip`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### OCISTREAM

          public static final int OCISTREAM

      Constant to denote an ocistream.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### KGHSSTREAM

          public static final int KGHSSTREAM

      Constant to denote a kghsstream.
      See Also:
      [Constant Field Values](../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### RealInputStream

          public RealInputStream(java.sql.Connection conn,
                                 long c_state,
                                 int type)
                          throws java.sql.SQLException

      Public constructor.
      Parameters:
      `c_state` - Pointer to the corresponding C state.

      Throws:
      `java.sql.SQLException`

  <!-- -->

  - ### Method Detail

    - #### read

          public int read(byte[] b)

      Function to read upto b.length bytes of data into a byte array
      Overrides:
      `read` in class `java.io.InputStream`

      Parameters:
      `b` - The byte array to read into

      Returns:
      The total number of bytes read into the buffer (-1) if the end of the stream is reached

    <!-- -->

    - #### read

          public int read()

      Function to read the next byte of data
      Specified by:
      `read` in class `java.io.InputStream`

      Returns:
      The next byte of data (-1) if the end of the stream is reached

    <!-- -->

    - #### markSupported

          public boolean markSupported()

      Function to check if "mark" and "reset" are supported
      Overrides:
      `markSupported` in class `java.io.InputStream`

      Returns:
      FALSE indicating that these operations are not supported

    <!-- -->

    - #### read

          public int read(byte[] b,
                          int off,
                          int len)

      Function to read upto "len" bytes of data into a byte array
      Overrides:
      `read` in class `java.io.InputStream`

      Parameters:
      `b` - The byte array to read into

      `off` - Start offset of the data

      `len` - The maximum number of bytes to read

      Returns:
      The total number of bytes read into the buffer (-1) if the end of the stream is reached

    <!-- -->

    - #### close

          public void close()

      Function to close the RealInputStream
      Specified by:
      `close` in interface `java.io.Closeable`

      Specified by:
      `close` in interface `java.lang.AutoCloseable`

      Overrides:
      `close` in class `java.io.InputStream`

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

- **[Prev Class](CState.md)**
- **[Next Class](SQLXMLType.md)**

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
