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

- **[Prev Class](InfosetWriter.md)**
- **[Next Class](PageManager.PageId.md)**

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

## **Interface PageManager**

- **All Known Implementing Classes:**
  **[FilePageManager](FilePageManager.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface PageManager

  **Interface for managing pages**

<!-- -->

-
  -

    ### **Nested Class Summary**

    **Nested Classes**

    | Modifier and Type   | Interface and Description                                         |
    |---------------------|-------------------------------------------------------------------|
    | `static interface ` | [`PageManager.PageId`](PageManager.PageId.md)<br>PageId Interface |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                             | Method and Description                                                                                                                                                                        |
    |-----------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                        | `close``()`<br>Closes the PageManager.                                                                                                                                                        |
    | `void`                                        | `deletePage``(`[`PageManager.PageId`](PageManager.PageId.md)` id)`<br>Delete the page for the given page id.                                                                                  |
    | [`PageManager.PageId`](PageManager.PageId.md) | `pageIdFromBytes``(byte[] buf, int start)`<br>Create pageId from a byte representation in the byte buffer starting at 'start' index.                                                          |
    | `byte`                                        | `pageIdToBytes``(`[`PageManager.PageId`](PageManager.PageId.md)` pageid, byte[] buf, int start)`<br>Write a byte representation of the PageId into the byte buffer starting at 'start' index. |
    | `int`                                         | `pageLength``(`[`PageManager.PageId`](PageManager.PageId.md)` id)`<br>Gets the page length.                                                                                                   |
    | `int`                                         | `readPage``(`[`PageManager.PageId`](PageManager.PageId.md)` id, byte[] buffer, int start)`<br>Fill the buffer for the given page id.                                                          |
    | [`PageManager.PageId`](PageManager.PageId.md) | `writePage``(byte[] buffer, int start, int length)`<br>Writes/Stores a page.                                                                                                                  |
    | [`PageManager.PageId`](PageManager.PageId.md) | `writePage``(`[`PageManager.PageId`](PageManager.PageId.md)` id, byte[] buffer, int start, int length)`<br>Updates a page for the given page id.                                              |

<!-- -->

- - ### Method Detail

    - #### writePage

          PageManager.PageId writePage(byte[] buffer,
                                       int start,
                                       int length)

      Writes/Stores a page. Returns the page Id.
      Parameters:
      `buffer` - - byte buffer containing a page to be stored.

      `start` - - start of the page in the buffer.

      `length` - - the length of the page.

      Returns:
      \- an Object containing the page Id.

    <!-- -->

    - #### writePage

          PageManager.PageId writePage(PageManager.PageId id,
                                       byte[] buffer,
                                       int start,
                                       int length)

      Updates a page for the given page id.
      Parameters:
      `id` - - an Object containing the page Id.

      `buffer` - - byte buffer containing a page to be stored.

      `start` - - start of the page in the buffer.

      `length` - - the length of the page.

      Returns:
      \- an Object containing the page Id.

    <!-- -->

    - #### readPage

          int readPage(PageManager.PageId id,
                       byte[] buffer,
                       int start)

      Fill the buffer for the given page id.
      Parameters:
      `id` - - an Object containing the page Id.

      `buffer` - - byte buffer containing a page to be stored.

      `start` - - start of the page in the buffer.

      Returns:
      \- the length of the page.

    <!-- -->

    - #### deletePage

          void deletePage(PageManager.PageId id)

      Delete the page for the given page id.
      Parameters:
      `id` - - an Object containing the page Id.

    <!-- -->

    - #### pageLength

          int pageLength(PageManager.PageId id)

      Gets the page length.
      Parameters:
      `id` - - an Object containing the page Id.

      Returns:
      \- the length of the page.

    <!-- -->

    - #### close

          void close()

      Closes the PageManager.

    <!-- -->

    - #### pageIdToBytes

          byte pageIdToBytes(PageManager.PageId pageid,
                             byte[] buf,
                             int start)

      Write a byte representation of the PageId into the byte buffer starting at 'start' index.
      Parameters:
      `pageid` - - pageId to be converted to bytes

      `buf` - - byte array to write into

      `start` - - start index

      Returns:
      number of bytes written, or -1 if buffer size is not sufficient

    <!-- -->

    - #### pageIdFromBytes

          PageManager.PageId pageIdFromBytes(byte[] buf,
                                             int start)

      Create pageId from a byte representation in the byte buffer starting at 'start' index.
      Parameters:
      `buf` - - byte array to read from

      `start` - - start index

      Returns:
      pageId - pageId converted from bytes in buf or null if bytes in the buf are invalid

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

- **[Prev Class](InfosetWriter.md)**
- **[Next Class](PageManager.PageId.md)**

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
