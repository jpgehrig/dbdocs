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

- **[Prev Class](CDATASection.md)**
- **[Next Class](Comment.md)**

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

## **Interface CharacterData**

- **All Superinterfaces:**
  **[Node](Node.md)**

  <!-- -->

  **All Known Subinterfaces:**
  **[CDATASection](CDATASection.md), [Comment](Comment.md), [Text](Text.md)**

  <!-- -->

  **All Known Implementing Classes:**
  **[XDBCData](../../../oracle/xdb/dom/XDBCData.md), [XDBCharData](../../../oracle/xdb/dom/XDBCharData.md), [XDBComment](../../../oracle/xdb/dom/XDBComment.md), [XDBText](../../../oracle/xdb/dom/XDBText.md), [XMLCDATA](../../../oracle/xml/parser/v2/XMLCDATA.md), [XMLComment](../../../oracle/xml/parser/v2/XMLComment.md), [XMLDeclPI](../../../oracle/xml/parser/v2/XMLDeclPI.md), [XMLPI](../../../oracle/xml/parser/v2/XMLPI.md), [XMLText](../../../oracle/xml/parser/v2/XMLText.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface CharacterData
      extends Node

  **The `CharacterData` interface extends Node with a set of attributes and methods for accessing character data in the DOM. For clarity this set is defined here rather than on each object that uses these attributes and methods. No DOM objects correspond directly to `CharacterData`, though `Text` and others do inherit the interface from it. All `offsets` in this interface start from `0`.**
  **As explained in the `DOMString` interface, text strings in the DOM are represented in UTF-16, i.e. as a sequence of 16-bit units. In the following, the term 16-bit units is used whenever necessary to indicate that indexing on CharacterData is done in 16-bit units.**

  **See also the [Document Object Model (DOM) Level 2 Core Specification](http://www.w3.org/TR/2000/REC-DOM-Level-2-Core-20001113).**

<!-- -->

-
  -

    ### **Field Summary**

    -

      ### **Fields inherited from interface org.w3c.dom.[Node](Node.md)**

      **[`ATTRIBUTE_NODE`](Node.md)`, `[`CDATA_SECTION_NODE`](Node.md)`, `[`COMMENT_NODE`](Node.md)`, `[`DOCUMENT_FRAGMENT_NODE`](Node.md)`, `[`DOCUMENT_NODE`](Node.md)`, `[`DOCUMENT_TYPE_NODE`](Node.md)`, `[`ELEMENT_NODE`](Node.md)`, `[`ENTITY_NODE`](Node.md)`, `[`ENTITY_REFERENCE_NODE`](Node.md)`, `[`NOTATION_NODE`](Node.md)`, `[`PROCESSING_INSTRUCTION_NODE`](Node.md)`, `[`TEXT_NODE`](Node.md)**

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                                                                                         |
    |--------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`             | `appendData``(java.lang.String arg)`<br>Append the string to the end of the character data of the node.                                                        |
    | `void`             | `deleteData``(int offset, int count)`<br>Remove a range of 16-bit units from the node.                                                                         |
    | `java.lang.String` | `getData``()`<br>The character data of the node that implements this interface.                                                                                |
    | `int`              | `getLength``()`<br>The number of 16-bit units that are available through `data` and the `substringData` method below.                                          |
    | `void`             | `insertData``(int offset, java.lang.String arg)`<br>Insert a string at the specified 16-bit unit offset.                                                       |
    | `void`             | `replaceData``(int offset, int count, java.lang.String arg)`<br>Replace the characters starting at the specified 16-bit unit offset with the specified string. |
    | `void`             | `setData``(java.lang.String data)`                                                                                                                             |
    | `java.lang.String` | `substringData``(int offset, int count)`<br>Extracts a range of data from the node.                                                                            |

    - ### Methods inherited from interface org.w3c.dom.[Node](Node.md)

      [`appendChild`](Node.md)`, `[`cloneNode`](Node.md)`, `[`getAttributes`](Node.md)`, `[`getChildNodes`](Node.md)`, `[`getFirstChild`](Node.md)`, `[`getLastChild`](Node.md)`, `[`getLocalName`](Node.md)`, `[`getNamespaceURI`](Node.md)`, `[`getNextSibling`](Node.md)`, `[`getNodeName`](Node.md)`, `[`getNodeType`](Node.md)`, `[`getNodeValue`](Node.md)`, `[`getOwnerDocument`](Node.md)`, `[`getParentNode`](Node.md)`, `[`getPrefix`](Node.md)`, `[`getPreviousSibling`](Node.md)`, `[`hasAttributes`](Node.md)`, `[`hasChildNodes`](Node.md)`, `[`insertBefore`](Node.md)`, `[`isSupported`](Node.md)`, `[`normalize`](Node.md)`, `[`removeChild`](Node.md)`, `[`replaceChild`](Node.md)`, `[`setNodeValue`](Node.md)`, `[`setPrefix`](Node.md)

<!-- -->

- - ### Method Detail

    - #### getData

          java.lang.String getData()
                            throws DOMException

      The character data of the node that implements this interface. The DOM implementation may not put arbitrary limits on the amount of data that may be stored in a `CharacterData` node. However, implementation limits may mean that the entirety of a node's data may not fit into a single `DOMString`. In such cases, the user may call `substringData` to retrieve the data in appropriately sized pieces.
      Throws:
      [`DOMException`](DOMException.md) - NO_MODIFICATION_ALLOWED_ERR: Raised when the node is readonly.

      [`DOMException`](DOMException.md) - DOMSTRING_SIZE_ERR: Raised when it would return more characters than fit in a `DOMString` variable on the implementation platform.

    <!-- -->

    - #### setData

          void setData(java.lang.String data)
                throws DOMException

      Throws:
      [`DOMException`](DOMException.md)

    <!-- -->

    - #### getLength

          int getLength()

      The number of 16-bit units that are available through `data` and the `substringData` method below. This may have the value zero, i.e., `CharacterData` nodes may be empty.

    <!-- -->

    - #### substringData

          java.lang.String substringData(int offset,
                                         int count)
                                  throws DOMException

      Extracts a range of data from the node.
      Parameters:
      `offset` - Start offset of substring to extract.

      `count` - The number of 16-bit units to extract.

      Returns:
      The specified substring. If the sum of `offset` and `count` exceeds the `length`, then all 16-bit units to the end of the data are returned.

      Throws:
      [`DOMException`](DOMException.md) - INDEX_SIZE_ERR: Raised if the specified `offset` is negative or greater than the number of 16-bit units in `data`, or if the specified `count` is negative.
      DOMSTRING_SIZE_ERR: Raised if the specified range of text does not fit into a `DOMString`.

    <!-- -->

    - #### appendData

          void appendData(java.lang.String arg)
                   throws DOMException

      Append the string to the end of the character data of the node. Upon success, `data` provides access to the concatenation of `data` and the `DOMString` specified.
      Parameters:
      `arg` - The `DOMString` to append.

      Throws:
      [`DOMException`](DOMException.md) - NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.

    <!-- -->

    - #### insertData

          void insertData(int offset,
                          java.lang.String arg)
                   throws DOMException

      Insert a string at the specified 16-bit unit offset.
      Parameters:
      `offset` - The character offset at which to insert.

      `arg` - The `DOMString` to insert.

      Throws:
      [`DOMException`](DOMException.md) - INDEX_SIZE_ERR: Raised if the specified `offset` is negative or greater than the number of 16-bit units in `data`.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.

    <!-- -->

    - #### deleteData

          void deleteData(int offset,
                          int count)
                   throws DOMException

      Remove a range of 16-bit units from the node. Upon success, `data` and `length` reflect the change.
      Parameters:
      `offset` - The offset from which to start removing.

      `count` - The number of 16-bit units to delete. If the sum of `offset` and `count` exceeds `length` then all 16-bit units from `offset` to the end of the data are deleted.

      Throws:
      [`DOMException`](DOMException.md) - INDEX_SIZE_ERR: Raised if the specified `offset` is negative or greater than the number of 16-bit units in `data`, or if the specified `count` is negative.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.

    <!-- -->

    - #### replaceData

          void replaceData(int offset,
                           int count,
                           java.lang.String arg)
                    throws DOMException

      Replace the characters starting at the specified 16-bit unit offset with the specified string.
      Parameters:
      `offset` - The offset from which to start replacing.

      `count` - The number of 16-bit units to replace. If the sum of `offset` and `count` exceeds `length`, then all 16-bit units to the end of the data are replaced; (i.e., the effect is the same as a `remove` method call with the same range, followed by an `append` method invocation).

      `arg` - The `DOMString` with which the range must be replaced.

      Throws:
      [`DOMException`](DOMException.md) - INDEX_SIZE_ERR: Raised if the specified `offset` is negative or greater than the number of 16-bit units in `data`, or if the specified `count` is negative.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.

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

- **[Prev Class](CDATASection.md)**
- **[Next Class](Comment.md)**

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
