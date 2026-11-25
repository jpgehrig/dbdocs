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

- **[Prev Class](DocumentFragment.md)**
- **[Next Class](DOMConfiguration.md)**

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

## **Interface DocumentType**

- **All Superinterfaces:**
  **[Node](Node.md)**

  <!-- -->

  **All Known Implementing Classes:**
  **[DTD](../../../oracle/xml/parser/v2/DTD.md), [XDBDocumentType](../../../oracle/xdb/dom/XDBDocumentType.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface DocumentType
      extends Node

  **Each `Document` has a `doctype` attribute whose value is either `null` or a `DocumentType` object. The `DocumentType` interface in the DOM Core provides an interface to the list of entities that are defined for the document, and little else because the effect of namespaces and the various XML schema efforts on DTD representation are not clearly understood as of this writing.**
  **The DOM Level 2 doesn't support editing `DocumentType` nodes.**

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

    | Modifier and Type                 | Method and Description                                                                                                                                     |
    |-----------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`NamedNodeMap`](NamedNodeMap.md) | `getEntities``()`<br>A `NamedNodeMap` containing the general entities, both external and internal, declared in the DTD.                                    |
    | `java.lang.String`                | `getInternalSubset``()`<br>The internal subset as a string.The actual content returned depends on how much information is available to the implementation. |
    | `java.lang.String`                | `getName``()`<br>The name of DTD; i.e., the name immediately following the `DOCTYPE` keyword.                                                              |
    | [`NamedNodeMap`](NamedNodeMap.md) | `getNotations``()`<br>A `NamedNodeMap` containing the notations declared in the DTD.                                                                       |
    | `java.lang.String`                | `getPublicId``()`<br>The public identifier of the external subset.                                                                                         |
    | `java.lang.String`                | `getSystemId``()`<br>The system identifier of the external subset.                                                                                         |

    - ### Methods inherited from interface org.w3c.dom.[Node](Node.md)

      [`appendChild`](Node.md)`, `[`cloneNode`](Node.md)`, `[`getAttributes`](Node.md)`, `[`getChildNodes`](Node.md)`, `[`getFirstChild`](Node.md)`, `[`getLastChild`](Node.md)`, `[`getLocalName`](Node.md)`, `[`getNamespaceURI`](Node.md)`, `[`getNextSibling`](Node.md)`, `[`getNodeName`](Node.md)`, `[`getNodeType`](Node.md)`, `[`getNodeValue`](Node.md)`, `[`getOwnerDocument`](Node.md)`, `[`getParentNode`](Node.md)`, `[`getPrefix`](Node.md)`, `[`getPreviousSibling`](Node.md)`, `[`hasAttributes`](Node.md)`, `[`hasChildNodes`](Node.md)`, `[`insertBefore`](Node.md)`, `[`isSupported`](Node.md)`, `[`normalize`](Node.md)`, `[`removeChild`](Node.md)`, `[`replaceChild`](Node.md)`, `[`setNodeValue`](Node.md)`, `[`setPrefix`](Node.md)

<!-- -->

- - ### Method Detail

    - #### getName

          java.lang.String getName()

      The name of DTD; i.e., the name immediately following the `DOCTYPE` keyword.

    <!-- -->

    - #### getEntities

          NamedNodeMap getEntities()

      A `NamedNodeMap` containing the general entities, both external and internal, declared in the DTD. Parameter entities are not contained. Duplicates are discarded. For example in:
          <!DOCTYPE
           ex SYSTEM "ex.dtd" [ <!ENTITY foo "foo"> <!ENTITY bar
           "bar"> <!ENTITY bar "bar2"> <!ENTITY % baz "baz">
           ]> <ex/>

      the interface provides access to `foo` and the first declaration of `bar` but not the second declaration of `bar` or `baz`. Every node in this map also implements the `Entity` interface.
      The DOM Level 2 does not support editing entities, therefore `entities` cannot be altered in any way.

    <!-- -->

    - #### getNotations

          NamedNodeMap getNotations()

      A `NamedNodeMap` containing the notations declared in the DTD. Duplicates are discarded. Every node in this map also implements the `Notation` interface.
      The DOM Level 2 does not support editing notations, therefore `notations` cannot be altered in any way.

    <!-- -->

    - #### getPublicId

          java.lang.String getPublicId()

      The public identifier of the external subset.
      Since:
      DOM Level 2

    <!-- -->

    - #### getSystemId

          java.lang.String getSystemId()

      The system identifier of the external subset.
      Since:
      DOM Level 2

    <!-- -->

    - #### getInternalSubset

          java.lang.String getInternalSubset()

      The internal subset as a string.The actual content returned depends on how much information is available to the implementation. This may vary depending on various parameters, including the XML processor used to build the document.
      Since:
      DOM Level 2

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

- **[Prev Class](DocumentFragment.md)**
- **[Next Class](DOMConfiguration.md)**

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
