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

- **[Prev Class](XDBProcInst.md)**
- **Next Class**

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

## **Class XDBText**

- **java.lang.Object**

- - **[oracle.xdb.dom.XDBNode](XDBNode.md)**

  - - **[oracle.xdb.dom.XDBCharData](XDBCharData.md)**

    - - **oracle.xdb.dom.XDBText**

<!-- -->

- **All Implemented Interfaces:**
  **[CharacterData](../../../org/w3c/dom/CharacterData.md), [Node](../../../org/w3c/dom/Node.md), [Text](../../../org/w3c/dom/Text.md)**

  <!-- -->

  **Direct Known Subclasses:**
  **[XDBCData](XDBCData.md)**

  ------------------------------------------------------------------------

  **Deprecated. **
  **as of Oracle Database 11g release 1, use oracle.xml.parser.v2.XMLText**
  **
  **

      public class XDBText
      extends XDBCharData
      implements Text

  **This class implements the W3C Text interface**

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

    | Modifier and Type                      | Method and Description                                                                                                                        |
    |----------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`                     | `getWholeText``()`<br>Deprecated. <br>                                                                                                        |
    | `boolean`                              | `isElementContentWhitespace``()`<br>Deprecated. <br>                                                                                          |
    | [`Text`](../../../org/w3c/dom/Text.md) | `replaceWholeText``(java.lang.String content)`<br>Deprecated. <br>                                                                            |
    | [`Text`](../../../org/w3c/dom/Text.md) | `splitText``(int offset)`<br>Deprecated. <br>Breaks this node into two nodes at the specified `offset`, keeping both in the tree as siblings. |

    - ### Methods inherited from class oracle.xdb.dom.[XDBCharData](XDBCharData.md)

      [`appendData`](XDBCharData.md)`, `[`deleteData`](XDBCharData.md)`, `[`getData`](XDBCharData.md)`, `[`getLength`](XDBCharData.md)`, `[`insertData`](XDBCharData.md)`, `[`replaceData`](XDBCharData.md)`, `[`setData`](XDBCharData.md)`, `[`substringData`](XDBCharData.md)

    <!-- -->

    - ### Methods inherited from class oracle.xdb.dom.[XDBNode](XDBNode.md)

      [`appendChild`](XDBNode.md)`, `[`cloneNode`](XDBNode.md)`, `[`close`](XDBNode.md)`, `[`compareDocumentPosition`](XDBNode.md)`, `[`equals`](XDBNode.md)`, `[`finalize`](XDBNode.md)`, `[`getAttributes`](XDBNode.md)`, `[`getBaseURI`](XDBNode.md)`, `[`getChildNodes`](XDBNode.md)`, `[`getExpandedName`](XDBNode.md)`, `[`getFeature`](XDBNode.md)`, `[`getFirstChild`](XDBNode.md)`, `[`getInputStream`](XDBNode.md)`, `[`getLastChild`](XDBNode.md)`, `[`getLocalName`](XDBNode.md)`, `[`getNamespaceURI`](XDBNode.md)`, `[`getNextSibling`](XDBNode.md)`, `[`getNodeName`](XDBNode.md)`, `[`getNodeType`](XDBNode.md)`, `[`getNodeValue`](XDBNode.md)`, `[`getOwnerDocument`](XDBNode.md)`, `[`getParentNode`](XDBNode.md)`, `[`getPrefix`](XDBNode.md)`, `[`getPreviousSibling`](XDBNode.md)`, `[`getPrimitiveType`](XDBNode.md)`, `[`getQualifiedName`](XDBNode.md)`, `[`getSchemaNode`](XDBNode.md)`, `[`getTextContent`](XDBNode.md)`, `[`getUserData`](XDBNode.md)`, `[`hasAttributes`](XDBNode.md)`, `[`hasChildNodes`](XDBNode.md)`, `[`hashCode`](XDBNode.md)`, `[`insertBefore`](XDBNode.md)`, `[`isDefaultNamespace`](XDBNode.md)`, `[`isEqualNode`](XDBNode.md)`, `[`isNilled`](XDBNode.md)`, `[`isSameNode`](XDBNode.md)`, `[`isSchemaBased`](XDBNode.md)`, `[`isSupported`](XDBNode.md)`, `[`lookupNamespaceURI`](XDBNode.md)`, `[`lookupPrefix`](XDBNode.md)`, `[`normalize`](XDBNode.md)`, `[`removeChild`](XDBNode.md)`, `[`replaceChild`](XDBNode.md)`, `[`setNodeValue`](XDBNode.md)`, `[`setNodeXob`](XDBNode.md)`, `[`setOwner`](XDBNode.md)`, `[`setPrefix`](XDBNode.md)`, `[`setTextContent`](XDBNode.md)`, `[`setUserData`](XDBNode.md)`, `[`setXobCstate`](XDBNode.md)`, `[`toCState`](XDBNode.md)`, `[`toString`](XDBNode.md)`, `[`write`](XDBNode.md)`, `[`writeToOutputStream`](XDBNode.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface org.w3c.dom.[CharacterData](../../../org/w3c/dom/CharacterData.md)

      [`appendData`](../../../org/w3c/dom/CharacterData.md)`, `[`deleteData`](../../../org/w3c/dom/CharacterData.md)`, `[`getData`](../../../org/w3c/dom/CharacterData.md)`, `[`getLength`](../../../org/w3c/dom/CharacterData.md)`, `[`insertData`](../../../org/w3c/dom/CharacterData.md)`, `[`replaceData`](../../../org/w3c/dom/CharacterData.md)`, `[`setData`](../../../org/w3c/dom/CharacterData.md)`, `[`substringData`](../../../org/w3c/dom/CharacterData.md)

    <!-- -->

    - ### Methods inherited from interface org.w3c.dom.[Node](../../../org/w3c/dom/Node.md)

      [`appendChild`](../../../org/w3c/dom/Node.md)`, `[`cloneNode`](../../../org/w3c/dom/Node.md)`, `[`getAttributes`](../../../org/w3c/dom/Node.md)`, `[`getChildNodes`](../../../org/w3c/dom/Node.md)`, `[`getFirstChild`](../../../org/w3c/dom/Node.md)`, `[`getLastChild`](../../../org/w3c/dom/Node.md)`, `[`getLocalName`](../../../org/w3c/dom/Node.md)`, `[`getNamespaceURI`](../../../org/w3c/dom/Node.md)`, `[`getNextSibling`](../../../org/w3c/dom/Node.md)`, `[`getNodeName`](../../../org/w3c/dom/Node.md)`, `[`getNodeType`](../../../org/w3c/dom/Node.md)`, `[`getNodeValue`](../../../org/w3c/dom/Node.md)`, `[`getOwnerDocument`](../../../org/w3c/dom/Node.md)`, `[`getParentNode`](../../../org/w3c/dom/Node.md)`, `[`getPrefix`](../../../org/w3c/dom/Node.md)`, `[`getPreviousSibling`](../../../org/w3c/dom/Node.md)`, `[`hasAttributes`](../../../org/w3c/dom/Node.md)`, `[`hasChildNodes`](../../../org/w3c/dom/Node.md)`, `[`insertBefore`](../../../org/w3c/dom/Node.md)`, `[`isSupported`](../../../org/w3c/dom/Node.md)`, `[`normalize`](../../../org/w3c/dom/Node.md)`, `[`removeChild`](../../../org/w3c/dom/Node.md)`, `[`replaceChild`](../../../org/w3c/dom/Node.md)`, `[`setNodeValue`](../../../org/w3c/dom/Node.md)`, `[`setPrefix`](../../../org/w3c/dom/Node.md)

<!-- -->

- - ### Method Detail

    - #### splitText

          public Text splitText(int offset)
                         throws DOMException

      Deprecated. 
      Description copied from interface: [`Text`](../../../org/w3c/dom/Text.md)
      Breaks this node into two nodes at the specified `offset`, keeping both in the tree as siblings. After being split, this node will contain all the content up to the `offset` point. A new node of the same type, which contains all the content at and after the `offset` point, is returned. If the original node had a parent node, the new node is inserted as the next sibling of the original node. When the `offset` is equal to the length of this node, the new node has no data.
      Specified by:
      [`splitText`](../../../org/w3c/dom/Text.md) in interface [`Text`](../../../org/w3c/dom/Text.md)

      Parameters:
      `offset` - The 16-bit unit offset at which to split, starting from `0`.

      Returns:
      The new node, of the same type as this node.

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md) - INDEX_SIZE_ERR: Raised if the specified offset is negative or greater than the number of 16-bit units in `data`.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.

    <!-- -->

    - #### isElementContentWhitespace

          public boolean isElementContentWhitespace()

      Deprecated. 

    <!-- -->

    - #### getWholeText

          public java.lang.String getWholeText()

      Deprecated. 

    <!-- -->

    - #### replaceWholeText

          public Text replaceWholeText(java.lang.String content)
                                throws DOMException

      Deprecated. 
      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md)

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

- **[Prev Class](XDBProcInst.md)**
- **Next Class**

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
