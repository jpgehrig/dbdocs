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

- **[Prev Class](Attr.md)**
- **[Next Class](CharacterData.md)**

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

## **Interface CDATASection**

- **All Superinterfaces:**
  **[CharacterData](CharacterData.md), [Node](Node.md), [Text](Text.md)**

  <!-- -->

  **All Known Implementing Classes:**
  **[XDBCData](../../../oracle/xdb/dom/XDBCData.md), [XMLCDATA](../../../oracle/xml/parser/v2/XMLCDATA.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface CDATASection
      extends Text

  **CDATA sections are used to escape blocks of text containing characters that would otherwise be regarded as markup. The only delimiter that is recognized in a CDATA section is the "\]\]\>" string that ends the CDATA section. CDATA sections cannot be nested. Their primary purpose is for including material such as XML fragments, without needing to escape all the delimiters.**
  **The `DOMString` attribute of the `Text` node holds the text that is contained by the CDATA section. Note that this may contain characters that need to be escaped outside of CDATA sections and that, depending on the character encoding ("charset") chosen for serialization, it may be impossible to write out some characters as part of a CDATA section.**

  **The `CDATASection` interface inherits from the `CharacterData` interface through the `Text` interface. Adjacent `CDATASection` nodes are not merged by use of the `normalize` method of the `Node` interface. Because no markup is recognized within a `CDATASection`, character numeric references cannot be used as an escape mechanism when serializing. Therefore, action needs to be taken when serializing a `CDATASection` with a character encoding where some of the contained characters cannot be represented. Failure to do so would not produce well-formed XML.One potential solution in the serialization process is to end the CDATA section before the character, output the character using a character reference or entity reference, and open a new CDATA section for any further characters in the text node. Note, however, that some code conversion libraries at the time of writing do not return an error or exception when a character is missing from the encoding, making the task of ensuring that data is not corrupted on serialization more difficult.**

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

    -

      ### **Methods inherited from interface org.w3c.dom.[Text](Text.md)**

      **[`splitText`](Text.md)**

    <!-- -->

    -

      ### **Methods inherited from interface org.w3c.dom.[CharacterData](CharacterData.md)**

      **[`appendData`](CharacterData.md)`, `[`deleteData`](CharacterData.md)`, `[`getData`](CharacterData.md)`, `[`getLength`](CharacterData.md)`, `[`insertData`](CharacterData.md)`, `[`replaceData`](CharacterData.md)`, `[`setData`](CharacterData.md)`, `[`substringData`](CharacterData.md)**

    <!-- -->

    -

      ### **Methods inherited from interface org.w3c.dom.[Node](Node.md)**

      **[`appendChild`](Node.md)`, `[`cloneNode`](Node.md)`, `[`getAttributes`](Node.md)`, `[`getChildNodes`](Node.md)`, `[`getFirstChild`](Node.md)`, `[`getLastChild`](Node.md)`, `[`getLocalName`](Node.md)`, `[`getNamespaceURI`](Node.md)`, `[`getNextSibling`](Node.md)`, `[`getNodeName`](Node.md)`, `[`getNodeType`](Node.md)`, `[`getNodeValue`](Node.md)`, `[`getOwnerDocument`](Node.md)`, `[`getParentNode`](Node.md)`, `[`getPrefix`](Node.md)`, `[`getPreviousSibling`](Node.md)`, `[`hasAttributes`](Node.md)`, `[`hasChildNodes`](Node.md)`, `[`insertBefore`](Node.md)`, `[`isSupported`](Node.md)`, `[`normalize`](Node.md)`, `[`removeChild`](Node.md)`, `[`replaceChild`](Node.md)`, `[`setNodeValue`](Node.md)`, `[`setPrefix`](Node.md)**

**Skip navigation links**

- **[Overview](../../../overview-summary.md)**
- **[Package](package-summary.md)**
- **Class**
- **[Tree](package-tree.md)**
- **[Deprecated](../../../deprecated-list.md)**
- **[Index](../../../index-all.md)**
- **[Help](../../../help-doc.md)**

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](Attr.md)**
- **[Next Class](CharacterData.md)**

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
