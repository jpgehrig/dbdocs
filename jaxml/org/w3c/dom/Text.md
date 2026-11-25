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

- **[Prev Class](ProcessingInstruction.md)**
- **[Next Class](TypeInfo.md)**

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

## **Interface Text**

- **All Superinterfaces:**
  **[CharacterData](CharacterData.md), [Node](Node.md)**

  <!-- -->

  **All Known Subinterfaces:**
  **[CDATASection](CDATASection.md)**

  <!-- -->

  **All Known Implementing Classes:**
  **[XDBCData](../../../oracle/xdb/dom/XDBCData.md), [XDBText](../../../oracle/xdb/dom/XDBText.md), [XMLCDATA](../../../oracle/xml/parser/v2/XMLCDATA.md), [XMLText](../../../oracle/xml/parser/v2/XMLText.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface Text
      extends CharacterData

  **The `Text` interface inherits from `CharacterData` and represents the textual content (termed character data in XML) of an `Element` or `Attr`. If there is no markup inside an element's content, the text is contained in a single object implementing the `Text` interface that is the only child of the element. If there is markup, it is parsed into the information items (elements, comments, etc.) and `Text` nodes that form the list of children of the element.**
  **When a document is first made available via the DOM, there is only one `Text` node for each block of text. Users may create adjacent `Text` nodes that represent the contents of a given element without any intervening markup, but should be aware that there is no way to represent the separations between these nodes in XML or HTML, so they will not (in general) persist between DOM editing sessions. The `normalize()` method on `Node` merges any such adjacent `Text` objects into a single node for each block of text.**

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

    | Modifier and Type | Method and Description                                                                                                        |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------|
    | `Text`            | `splitText``(int offset)`<br>Breaks this node into two nodes at the specified `offset`, keeping both in the tree as siblings. |

    - ### Methods inherited from interface org.w3c.dom.[CharacterData](CharacterData.md)

      [`appendData`](CharacterData.md)`, `[`deleteData`](CharacterData.md)`, `[`getData`](CharacterData.md)`, `[`getLength`](CharacterData.md)`, `[`insertData`](CharacterData.md)`, `[`replaceData`](CharacterData.md)`, `[`setData`](CharacterData.md)`, `[`substringData`](CharacterData.md)

    <!-- -->

    - ### Methods inherited from interface org.w3c.dom.[Node](Node.md)

      [`appendChild`](Node.md)`, `[`cloneNode`](Node.md)`, `[`getAttributes`](Node.md)`, `[`getChildNodes`](Node.md)`, `[`getFirstChild`](Node.md)`, `[`getLastChild`](Node.md)`, `[`getLocalName`](Node.md)`, `[`getNamespaceURI`](Node.md)`, `[`getNextSibling`](Node.md)`, `[`getNodeName`](Node.md)`, `[`getNodeType`](Node.md)`, `[`getNodeValue`](Node.md)`, `[`getOwnerDocument`](Node.md)`, `[`getParentNode`](Node.md)`, `[`getPrefix`](Node.md)`, `[`getPreviousSibling`](Node.md)`, `[`hasAttributes`](Node.md)`, `[`hasChildNodes`](Node.md)`, `[`insertBefore`](Node.md)`, `[`isSupported`](Node.md)`, `[`normalize`](Node.md)`, `[`removeChild`](Node.md)`, `[`replaceChild`](Node.md)`, `[`setNodeValue`](Node.md)`, `[`setPrefix`](Node.md)

<!-- -->

- - ### Method Detail

    - #### splitText

          Text splitText(int offset)
                  throws DOMException

      Breaks this node into two nodes at the specified `offset`, keeping both in the tree as siblings. After being split, this node will contain all the content up to the `offset` point. A new node of the same type, which contains all the content at and after the `offset` point, is returned. If the original node had a parent node, the new node is inserted as the next sibling of the original node. When the `offset` is equal to the length of this node, the new node has no data.
      Parameters:
      `offset` - The 16-bit unit offset at which to split, starting from `0`.

      Returns:
      The new node, of the same type as this node.

      Throws:
      [`DOMException`](DOMException.md) - INDEX_SIZE_ERR: Raised if the specified offset is negative or greater than the number of 16-bit units in `data`.
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

- **[Prev Class](ProcessingInstruction.md)**
- **[Next Class](TypeInfo.md)**

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
