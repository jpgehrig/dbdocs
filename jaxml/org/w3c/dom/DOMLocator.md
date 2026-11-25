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

- **[Prev Class](DOMImplementationSource.md)**
- **[Next Class](DOMStringList.md)**

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

**org.w3c.dom**

## **Interface DOMLocator**

-

  ------------------------------------------------------------------------

  **
  **

      public interface DOMLocator

  **`DOMLocator` is an interface that describes a location (e.g. where an error occurred).**
  **See also the [Document Object Model (DOM) Level 3 Core Specification](http://www.w3.org/TR/2003/CR-DOM-Level-3-Core-20031107).**

  **Since:**
  **DOM Level 3**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                                       |
    |--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`              | `getByteOffset``()`<br>The byte offset into the input source this locator is pointing to or `-1` if there is no byte offset available.                                                                       |
    | `int`              | `getColumnNumber``()`<br>The column number this locator is pointing to, or `-1` if there is no column number available.                                                                                      |
    | `int`              | `getLineNumber``()`<br>The line number this locator is pointing to, or `-1` if there is no column number available.                                                                                          |
    | [`Node`](Node.md)  | `getRelatedNode``()`<br>The node this locator is pointing to, or `null` if no node is available.                                                                                                             |
    | `java.lang.String` | `getUri``()`<br>The URI this locator is pointing to, or `null` if no URI is available.                                                                                                                       |
    | `int`              | `getUtf16Offset``()`<br>The UTF-16, as defined in \[Unicode\] and Amendment 1 of \[ISO/IEC 10646\], offset into the input source this locator is pointing to or `-1` if there is no UTF-16 offset available. |

<!-- -->

- - ### Method Detail

    - #### getLineNumber

          int getLineNumber()

      The line number this locator is pointing to, or `-1` if there is no column number available.

    <!-- -->

    - #### getColumnNumber

          int getColumnNumber()

      The column number this locator is pointing to, or `-1` if there is no column number available.

    <!-- -->

    - #### getByteOffset

          int getByteOffset()

      The byte offset into the input source this locator is pointing to or `-1` if there is no byte offset available.

    <!-- -->

    - #### getUtf16Offset

          int getUtf16Offset()

      The UTF-16, as defined in \[Unicode\] and Amendment 1 of \[ISO/IEC 10646\], offset into the input source this locator is pointing to or `-1` if there is no UTF-16 offset available.

    <!-- -->

    - #### getRelatedNode

          Node getRelatedNode()

      The node this locator is pointing to, or `null` if no node is available.

    <!-- -->

    - #### getUri

          java.lang.String getUri()

      The URI this locator is pointing to, or `null` if no URI is available.

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

- **[Prev Class](DOMImplementationSource.md)**
- **[Next Class](DOMStringList.md)**

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

**Copyright © 2000 [W3C](http://www.w3.org/)<sup>®</sup> ([MIT](http://www.csail.mit.edu/), [INRIA](http://www.inria.fr/), [Keio](http://www.keio.ac.jp/)), All Rights Reserved. W3C [liability](http://www.w3.org/Consortium/Legal/2002/ipr-notice-20021231), [trademark](http://www.w3.org/Consortium/Legal/2002/ipr-notice-20021231), [document use](http://www.w3.org/Consortium/Legal/copyright-documents-19990405) and [software licensing](http://www.w3.org/Consortium/Legal/copyright-software-19980720) rules apply. This document has been reviewed by W3C Members and other interested parties and has been endorsed by the Director as a [W3C Recommendation](http://www.w3.org/Consortium/Process/Process-19991111/tr.html#RecsW3C).**
