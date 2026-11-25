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

- **[Prev Class](XDBDocument.md)**
- **[Next Class](XDBDOMException.md)**

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

**oracle.xdb.dom**

## **Class XDBDocumentType**

- **java.lang.Object**

- - **[oracle.xdb.dom.XDBNode](XDBNode.md)**

  - - **oracle.xdb.dom.XDBDocumentType**

<!-- -->

- **All Implemented Interfaces:**
  **[DocumentType](../../../org/w3c/dom/DocumentType.md), [Node](../../../org/w3c/dom/Node.md)**

  ------------------------------------------------------------------------

  **Deprecated. **
  **as of Oracle Database 11g release 1, use oracle.xml.parser.v2.DTD**
  **
  **

      public class XDBDocumentType
      extends XDBNode
      implements DocumentType

  **This class implements the W3C Notation interface**

<!-- -->

-
  -

    ### **Field Summary**

    -

      ### **Fields inherited from interface org.w3c.dom.[Node](../../../org/w3c/dom/Node.md)**

      **[`ATTRIBUTE_NODE`](../../../org/w3c/dom/Node.md)`, `[`CDATA_SECTION_NODE`](../../../org/w3c/dom/Node.md)`, `[`COMMENT_NODE`](../../../org/w3c/dom/Node.md)`, `[`DOCUMENT_FRAGMENT_NODE`](../../../org/w3c/dom/Node.md)`, `[`DOCUMENT_NODE`](../../../org/w3c/dom/Node.md)`, `[`DOCUMENT_TYPE_NODE`](../../../org/w3c/dom/Node.md)`, `[`ELEMENT_NODE`](../../../org/w3c/dom/Node.md)`, `[`ENTITY_NODE`](../../../org/w3c/dom/Node.md)`, `[`ENTITY_REFERENCE_NODE`](../../../org/w3c/dom/Node.md)`, `[`NOTATION_NODE`](../../../org/w3c/dom/Node.md)`, `[`PROCESSING_INSTRUCTION_NODE`](../../../org/w3c/dom/Node.md)`, `[`TEXT_NODE`](../../../org/w3c/dom/Node.md)**

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                      | Method and Description                                                                                                         |
    |--------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------|
    | [`XDBEntity`](XDBEntity.md)                            | `findEntity``(java.lang.String name)`<br>Deprecated. <br>Finds the entity node of the document type based on the given name.   |
    | [`XDBNotation`](XDBNotation.md)                        | `findNotation``(java.lang.String name)`<br>Deprecated. <br>Finds the entity node of the document type based on the given name. |
    | [`NamedNodeMap`](../../../org/w3c/dom/NamedNodeMap.md) | `getEntities``()`<br>Deprecated. <br>Returns the entity map of the document type node                                          |
    | `java.lang.String`                                     | `getInternalSubset``()`<br>Deprecated. <br>Returns the internal subset.                                                        |
    | `java.lang.String`                                     | `getName``()`<br>Deprecated. <br>Returns the name map of the document type node                                                |
    | [`NamedNodeMap`](../../../org/w3c/dom/NamedNodeMap.md) | `getNotations``()`<br>Deprecated. <br>Returns the notation map of the document type node                                       |
    | `java.lang.String`                                     | `getPublicId``()`<br>Deprecated. <br>Returns the public id of the document type node                                           |
    | `java.lang.String`                                     | `getSystemId``()`<br>Deprecated. <br>Returns the system id of the entity node                                                  |

    - ### Methods inherited from class oracle.xdb.dom.[XDBNode](XDBNode.md)

      [`appendChild`](XDBNode.md)`, `[`cloneNode`](XDBNode.md)`, `[`close`](XDBNode.md)`, `[`compareDocumentPosition`](XDBNode.md)`, `[`equals`](XDBNode.md)`, `[`finalize`](XDBNode.md)`, `[`getAttributes`](XDBNode.md)`, `[`getBaseURI`](XDBNode.md)`, `[`getChildNodes`](XDBNode.md)`, `[`getExpandedName`](XDBNode.md)`, `[`getFeature`](XDBNode.md)`, `[`getFirstChild`](XDBNode.md)`, `[`getInputStream`](XDBNode.md)`, `[`getLastChild`](XDBNode.md)`, `[`getLocalName`](XDBNode.md)`, `[`getNamespaceURI`](XDBNode.md)`, `[`getNextSibling`](XDBNode.md)`, `[`getNodeName`](XDBNode.md)`, `[`getNodeType`](XDBNode.md)`, `[`getNodeValue`](XDBNode.md)`, `[`getOwnerDocument`](XDBNode.md)`, `[`getParentNode`](XDBNode.md)`, `[`getPrefix`](XDBNode.md)`, `[`getPreviousSibling`](XDBNode.md)`, `[`getPrimitiveType`](XDBNode.md)`, `[`getQualifiedName`](XDBNode.md)`, `[`getSchemaNode`](XDBNode.md)`, `[`getTextContent`](XDBNode.md)`, `[`getUserData`](XDBNode.md)`, `[`hasAttributes`](XDBNode.md)`, `[`hasChildNodes`](XDBNode.md)`, `[`hashCode`](XDBNode.md)`, `[`insertBefore`](XDBNode.md)`, `[`isDefaultNamespace`](XDBNode.md)`, `[`isEqualNode`](XDBNode.md)`, `[`isNilled`](XDBNode.md)`, `[`isSameNode`](XDBNode.md)`, `[`isSchemaBased`](XDBNode.md)`, `[`isSupported`](XDBNode.md)`, `[`lookupNamespaceURI`](XDBNode.md)`, `[`lookupPrefix`](XDBNode.md)`, `[`normalize`](XDBNode.md)`, `[`removeChild`](XDBNode.md)`, `[`replaceChild`](XDBNode.md)`, `[`setNodeValue`](XDBNode.md)`, `[`setNodeXob`](XDBNode.md)`, `[`setOwner`](XDBNode.md)`, `[`setPrefix`](XDBNode.md)`, `[`setTextContent`](XDBNode.md)`, `[`setUserData`](XDBNode.md)`, `[`setXobCstate`](XDBNode.md)`, `[`toCState`](XDBNode.md)`, `[`toString`](XDBNode.md)`, `[`write`](XDBNode.md)`, `[`writeToOutputStream`](XDBNode.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface org.w3c.dom.[Node](../../../org/w3c/dom/Node.md)

      [`appendChild`](../../../org/w3c/dom/Node.md)`, `[`cloneNode`](../../../org/w3c/dom/Node.md)`, `[`getAttributes`](../../../org/w3c/dom/Node.md)`, `[`getChildNodes`](../../../org/w3c/dom/Node.md)`, `[`getFirstChild`](../../../org/w3c/dom/Node.md)`, `[`getLastChild`](../../../org/w3c/dom/Node.md)`, `[`getLocalName`](../../../org/w3c/dom/Node.md)`, `[`getNamespaceURI`](../../../org/w3c/dom/Node.md)`, `[`getNextSibling`](../../../org/w3c/dom/Node.md)`, `[`getNodeName`](../../../org/w3c/dom/Node.md)`, `[`getNodeType`](../../../org/w3c/dom/Node.md)`, `[`getNodeValue`](../../../org/w3c/dom/Node.md)`, `[`getOwnerDocument`](../../../org/w3c/dom/Node.md)`, `[`getParentNode`](../../../org/w3c/dom/Node.md)`, `[`getPrefix`](../../../org/w3c/dom/Node.md)`, `[`getPreviousSibling`](../../../org/w3c/dom/Node.md)`, `[`hasAttributes`](../../../org/w3c/dom/Node.md)`, `[`hasChildNodes`](../../../org/w3c/dom/Node.md)`, `[`insertBefore`](../../../org/w3c/dom/Node.md)`, `[`isSupported`](../../../org/w3c/dom/Node.md)`, `[`normalize`](../../../org/w3c/dom/Node.md)`, `[`removeChild`](../../../org/w3c/dom/Node.md)`, `[`replaceChild`](../../../org/w3c/dom/Node.md)`, `[`setNodeValue`](../../../org/w3c/dom/Node.md)`, `[`setPrefix`](../../../org/w3c/dom/Node.md)

<!-- -->

- - ### Method Detail

    - #### getNotations

          public NamedNodeMap getNotations()

      Deprecated. 
      Returns the notation map of the document type node
      Specified by:
      [`getNotations`](../../../org/w3c/dom/DocumentType.md) in interface [`DocumentType`](../../../org/w3c/dom/DocumentType.md)

      Returns:
      the notation name of the document type node

    <!-- -->

    - #### getName

          public java.lang.String getName()

      Deprecated. 
      Returns the name map of the document type node
      Specified by:
      [`getName`](../../../org/w3c/dom/DocumentType.md) in interface [`DocumentType`](../../../org/w3c/dom/DocumentType.md)

      Returns:
      the name map of the document type node

    <!-- -->

    - #### getEntities

          public NamedNodeMap getEntities()

      Deprecated. 
      Returns the entity map of the document type node
      Specified by:
      [`getEntities`](../../../org/w3c/dom/DocumentType.md) in interface [`DocumentType`](../../../org/w3c/dom/DocumentType.md)

      Returns:
      the entity map of the document type node

    <!-- -->

    - #### getInternalSubset

          public java.lang.String getInternalSubset()

      Deprecated. 
      Returns the internal subset. Currently always return null.
      Specified by:
      [`getInternalSubset`](../../../org/w3c/dom/DocumentType.md) in interface [`DocumentType`](../../../org/w3c/dom/DocumentType.md)

      Returns:
      the internal subset

    <!-- -->

    - #### getPublicId

          public java.lang.String getPublicId()

      Deprecated. 
      Returns the public id of the document type node
      Specified by:
      [`getPublicId`](../../../org/w3c/dom/DocumentType.md) in interface [`DocumentType`](../../../org/w3c/dom/DocumentType.md)

      Returns:
      the public id of the document type node

    <!-- -->

    - #### getSystemId

          public java.lang.String getSystemId()

      Deprecated. 
      Returns the system id of the entity node
      Specified by:
      [`getSystemId`](../../../org/w3c/dom/DocumentType.md) in interface [`DocumentType`](../../../org/w3c/dom/DocumentType.md)

      Returns:
      the system id of the entity node

    <!-- -->

    - #### findEntity

          public XDBEntity findEntity(java.lang.String name)

      Deprecated. 
      Finds the entity node of the document type based on the given name.
      Returns:
      the entity node of the document type

    <!-- -->

    - #### findNotation

          public XDBNotation findNotation(java.lang.String name)

      Deprecated. 
      Finds the entity node of the document type based on the given name.
      Returns:
      the entity node of the document type

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

- **[Prev Class](XDBDocument.md)**
- **[Next Class](XDBDOMException.md)**

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
