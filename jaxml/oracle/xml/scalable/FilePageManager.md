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

- **[Prev Class](BinaryStream.md)**
- **[Next Class](InfosetReader.md)**

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

## **Class FilePageManager**

- **java.lang.Object**

- - **oracle.xml.scalable.AbstractPageManager**

  - - **oracle.xml.scalable.FilePageManager**

<!-- -->

- **All Implemented Interfaces:**
  **[PageManager](PageManager.md)**

  ------------------------------------------------------------------------

  **
  **

      public class FilePageManager
      extends oracle.xml.scalable.AbstractPageManager

  **A @see PageManger that stores pages in a file.**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                  |
    |------------------------------------------------------------------------------|
    | `FilePageManager``(java.lang.String filename)`<br>Creates a FilePageManager. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                       |
    |-------------------|--------------------------------------------------------------------------------------------------------------|
    | `void`            | `close``()`<br>Closes the session.                                                                           |
    | `void`            | `deletePage``(`[`PageManager.PageId`](PageManager.PageId.md)` id)`<br>Delete the page for the given page id. |
    | `int`             | `read``(byte[] buf, int off, int len)`<br>Read from the given offset into the buffer                         |
    | `void`            | `seek``(long offset)`<br>Seek to the given offset                                                            |
    | `void`            | `write``(byte[] buf, int off, int len)`<br>Write at the given offset from the buffer                         |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### FilePageManager

          public FilePageManager(java.lang.String filename)

      Creates a FilePageManager.
      Parameters:
      `filename` - - the system-dependent filename

  <!-- -->

  - ### Method Detail

    - #### seek

          public void seek(long offset)
                    throws java.io.IOException

      Seek to the given offset
      Throws:
      `java.io.IOException`

    <!-- -->

    - #### read

          public int read(byte[] buf,
                          int off,
                          int len)
                   throws java.io.IOException

      Read from the given offset into the buffer
      Parameters:
      `buf` - - result buffer

      `off` - - offset to start reading from

      `len` - - number of bytes to read

      Returns:
      \- number of bytes read

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### write

          public void write(byte[] buf,
                            int off,
                            int len)
                     throws java.io.IOException

      Write at the given offset from the buffer
      Parameters:
      `buf` - - input buffer

      `off` - - offset to start writing from

      `len` - - number of bytes to write

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### deletePage

          public void deletePage(PageManager.PageId id)

      Delete the page for the given page id.
      Specified by:
      [`deletePage`](PageManager.md) in interface [`PageManager`](PageManager.md)

      Parameters:
      `id` - - an Object containing the page Id.

    <!-- -->

    - #### close

          public void close()

      Closes the session.
      Specified by:
      [`close`](PageManager.md) in interface [`PageManager`](PageManager.md)

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

- **[Prev Class](BinaryStream.md)**
- **[Next Class](InfosetReader.md)**

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
