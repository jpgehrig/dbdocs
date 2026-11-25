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

- **[Prev Class](XDBAttribute.md)**
- **[Next Class](XDBCData.md)**

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

## **Class XDBBinaryDocument**

- **java.lang.Object**

- - **[oracle.xdb.dom.XDBNode](XDBNode.md)**

  - - **[oracle.xdb.dom.XDBDocument](XDBDocument.md)**

    - - **oracle.xdb.dom.XDBBinaryDocument**

<!-- -->

- **All Implemented Interfaces:**
  **[Document](../../../org/w3c/dom/Document.md), [Node](../../../org/w3c/dom/Node.md)**

  ------------------------------------------------------------------------

  **Deprecated. **
  **as of Oracle Database 11g release 1**
  **
  **

      public class XDBBinaryDocument
      extends XDBDocument

<!-- -->

-
  -

    ### **Field Summary**

    -

      ### **Fields inherited from interface org.w3c.dom.[Node](../../../org/w3c/dom/Node.md)**

      **[`ATTRIBUTE_NODE`](../../../org/w3c/dom/Node.md)`, `[`CDATA_SECTION_NODE`](../../../org/w3c/dom/Node.md)`, `[`COMMENT_NODE`](../../../org/w3c/dom/Node.md)`, `[`DOCUMENT_FRAGMENT_NODE`](../../../org/w3c/dom/Node.md)`, `[`DOCUMENT_NODE`](../../../org/w3c/dom/Node.md)`, `[`DOCUMENT_TYPE_NODE`](../../../org/w3c/dom/Node.md)`, `[`ELEMENT_NODE`](../../../org/w3c/dom/Node.md)`, `[`ENTITY_NODE`](../../../org/w3c/dom/Node.md)`, `[`ENTITY_REFERENCE_NODE`](../../../org/w3c/dom/Node.md)`, `[`NOTATION_NODE`](../../../org/w3c/dom/Node.md)`, `[`PROCESSING_INSTRUCTION_NODE`](../../../org/w3c/dom/Node.md)`, `[`TEXT_NODE`](../../../org/w3c/dom/Node.md)**

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                     |
    |---------------------------------------------------------------------------------|
    | `XDBBinaryDocument``()`<br>Deprecated. <br>                                     |
    | `XDBBinaryDocument``(java.sql.Connection conn)`<br>Deprecated. <br>             |
    | `XDBBinaryDocument``(java.sql.Connection conn, long xobd)`<br>Deprecated. <br>  |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type     | Method and Description                                     |
    |-----------------------|------------------------------------------------------------|
    | `java.io.InputStream` | `getStream``()`<br>Deprecated. <br>                        |
    | `void`                | `setStream``(java.io.InputStream is)`<br>Deprecated. <br>  |

    - ### Methods inherited from class oracle.xdb.dom.[XDBDocument](XDBDocument.md)

      [`adoptNode`](XDBDocument.md)`, `[`appendChild`](XDBDocument.md)`, `[`close`](XDBDocument.md)`, `[`createAttribute`](XDBDocument.md)`, `[`createAttributeNS`](XDBDocument.md)`, `[`createCDATASection`](XDBDocument.md)`, `[`createComment`](XDBDocument.md)`, `[`createDocumentFragment`](XDBDocument.md)`, `[`createElement`](XDBDocument.md)`, `[`createElementNS`](XDBDocument.md)`, `[`createEntityReference`](XDBDocument.md)`, `[`createProcessingInstruction`](XDBDocument.md)`, `[`createTextNode`](XDBDocument.md)`, `[`finalize`](XDBDocument.md)`, `[`getDoctype`](XDBDocument.md)`, `[`getDocumentElement`](XDBDocument.md)`, `[`getDocumentURI`](XDBDocument.md)`, `[`getDomConfig`](XDBDocument.md)`, `[`getElementById`](XDBDocument.md)`, `[`getElementsByTagName`](XDBDocument.md)`, `[`getElementsByTagNameNS`](XDBDocument.md)`, `[`getFirstChild`](XDBDocument.md)`, `[`getGP`](XDBDocument.md)`, `[`getImplementation`](XDBDocument.md)`, `[`getInputEncoding`](XDBDocument.md)`, `[`getLastChild`](XDBDocument.md)`, `[`getNextSibling`](XDBDocument.md)`, `[`getNodeName`](XDBDocument.md)`, `[`getOwnerDocument`](XDBDocument.md)`, `[`getPreviousSibling`](XDBDocument.md)`, `[`getStrictErrorChecking`](XDBDocument.md)`, `[`getXmlEncoding`](XDBDocument.md)`, `[`getXmlStandalone`](XDBDocument.md)`, `[`getXmlVersion`](XDBDocument.md)`, `[`importNode`](XDBDocument.md)`, `[`insertBefore`](XDBDocument.md)`, `[`isClosed`](XDBDocument.md)`, `[`normalizeDocument`](XDBDocument.md)`, `[`removeChild`](XDBDocument.md)`, `[`renameNode`](XDBDocument.md)`, `[`replaceChild`](XDBDocument.md)`, `[`setDocumentURI`](XDBDocument.md)`, `[`setStrictErrorChecking`](XDBDocument.md)`, `[`setXmlStandalone`](XDBDocument.md)`, `[`setXmlVersion`](XDBDocument.md)

    <!-- -->

    - ### Methods inherited from class oracle.xdb.dom.[XDBNode](XDBNode.md)

      [`cloneNode`](XDBNode.md)`, `[`compareDocumentPosition`](XDBNode.md)`, `[`equals`](XDBNode.md)`, `[`getAttributes`](XDBNode.md)`, `[`getBaseURI`](XDBNode.md)`, `[`getChildNodes`](XDBNode.md)`, `[`getExpandedName`](XDBNode.md)`, `[`getFeature`](XDBNode.md)`, `[`getInputStream`](XDBNode.md)`, `[`getLocalName`](XDBNode.md)`, `[`getNamespaceURI`](XDBNode.md)`, `[`getNodeType`](XDBNode.md)`, `[`getNodeValue`](XDBNode.md)`, `[`getParentNode`](XDBNode.md)`, `[`getPrefix`](XDBNode.md)`, `[`getPrimitiveType`](XDBNode.md)`, `[`getQualifiedName`](XDBNode.md)`, `[`getSchemaNode`](XDBNode.md)`, `[`getTextContent`](XDBNode.md)`, `[`getUserData`](XDBNode.md)`, `[`hasAttributes`](XDBNode.md)`, `[`hasChildNodes`](XDBNode.md)`, `[`hashCode`](XDBNode.md)`, `[`isDefaultNamespace`](XDBNode.md)`, `[`isEqualNode`](XDBNode.md)`, `[`isNilled`](XDBNode.md)`, `[`isSameNode`](XDBNode.md)`, `[`isSchemaBased`](XDBNode.md)`, `[`isSupported`](XDBNode.md)`, `[`lookupNamespaceURI`](XDBNode.md)`, `[`lookupPrefix`](XDBNode.md)`, `[`normalize`](XDBNode.md)`, `[`setNodeValue`](XDBNode.md)`, `[`setNodeXob`](XDBNode.md)`, `[`setOwner`](XDBNode.md)`, `[`setPrefix`](XDBNode.md)`, `[`setTextContent`](XDBNode.md)`, `[`setUserData`](XDBNode.md)`, `[`setXobCstate`](XDBNode.md)`, `[`toCState`](XDBNode.md)`, `[`toString`](XDBNode.md)`, `[`write`](XDBNode.md)`, `[`writeToOutputStream`](XDBNode.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface org.w3c.dom.[Node](../../../org/w3c/dom/Node.md)

      [`cloneNode`](../../../org/w3c/dom/Node.md)`, `[`getAttributes`](../../../org/w3c/dom/Node.md)`, `[`getChildNodes`](../../../org/w3c/dom/Node.md)`, `[`getLocalName`](../../../org/w3c/dom/Node.md)`, `[`getNamespaceURI`](../../../org/w3c/dom/Node.md)`, `[`getNodeType`](../../../org/w3c/dom/Node.md)`, `[`getNodeValue`](../../../org/w3c/dom/Node.md)`, `[`getParentNode`](../../../org/w3c/dom/Node.md)`, `[`getPrefix`](../../../org/w3c/dom/Node.md)`, `[`hasAttributes`](../../../org/w3c/dom/Node.md)`, `[`hasChildNodes`](../../../org/w3c/dom/Node.md)`, `[`isSupported`](../../../org/w3c/dom/Node.md)`, `[`normalize`](../../../org/w3c/dom/Node.md)`, `[`setNodeValue`](../../../org/w3c/dom/Node.md)`, `[`setPrefix`](../../../org/w3c/dom/Node.md)

<!-- -->

- - ### Constructor Detail

    - #### XDBBinaryDocument

          public XDBBinaryDocument()

      Deprecated. 

    <!-- -->

    - #### XDBBinaryDocument

          public XDBBinaryDocument(java.sql.Connection conn)
                            throws java.lang.Exception

      Deprecated. 
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### XDBBinaryDocument

          public XDBBinaryDocument(java.sql.Connection conn,
                                   long xobd)

      Deprecated. 

  <!-- -->

  - ### Method Detail

    - #### getStream

          public java.io.InputStream getStream()
                                        throws java.sql.SQLException

      Deprecated. 
      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### setStream

          public void setStream(java.io.InputStream is)
                         throws java.io.IOException

      Deprecated. 
      Throws:
      `java.io.IOException`

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

- **[Prev Class](XDBAttribute.md)**
- **[Next Class](XDBCData.md)**

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
