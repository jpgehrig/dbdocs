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

- **[Prev Class](XDBCData.md)**
- **[Next Class](XDBComment.md)**

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

## **Class XDBCharData**

- **java.lang.Object**

- - **[oracle.xdb.dom.XDBNode](XDBNode.md)**

  - - **oracle.xdb.dom.XDBCharData**

<!-- -->

- **All Implemented Interfaces:**
  **[CharacterData](../../../org/w3c/dom/CharacterData.md), [Node](../../../org/w3c/dom/Node.md)**

  <!-- -->

  **Direct Known Subclasses:**
  **[XDBComment](XDBComment.md), [XDBText](XDBText.md)**

  ------------------------------------------------------------------------

  **Deprecated. **
  **as of Oracle Database 11g release 1, use oracle.xml.parser.v2.CharData**
  **
  **

      public class XDBCharData
      extends XDBNode
      implements CharacterData

  **This class implements the W3C CharacterData interface**

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

    | Modifier and Type  | Method and Description                                                                                                                      |
    |--------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`             | `appendData``(java.lang.String appstring)`<br>Deprecated. <br>append the specified string to the char data                                  |
    | `void`             | `deleteData``(int offset, int count)`<br>Deprecated. <br>delete the specified substring string from the char data                           |
    | `java.lang.String` | `getData``()`<br>Deprecated. <br>Returns the char data                                                                                      |
    | `int`              | `getLength``()`<br>Deprecated. <br>gets the length of the char data                                                                         |
    | `void`             | `insertData``(int offset, java.lang.String appstring)`<br>Deprecated. <br>insert the specified string into the char data                    |
    | `void`             | `replaceData``(int offset, int count, java.lang.String repdata)`<br>Deprecated. <br>replace the specified substring string in the char data |
    | `void`             | `setData``(java.lang.String data)`<br>Deprecated. <br>sets the char data                                                                    |
    | `java.lang.String` | `substringData``(int offset, int count)`<br>Deprecated. <br>gets the specified substring of the char data                                   |

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

    - #### getData

          public java.lang.String getData()
                                   throws DOMException

      Deprecated. 
      Returns the char data
      Specified by:
      [`getData`](../../../org/w3c/dom/CharacterData.md) in interface [`CharacterData`](../../../org/w3c/dom/CharacterData.md)

      Returns:
      the character data

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md) - NO_MODIFICATION_ALLOWED_ERR: Raised when the node is readonly.

    <!-- -->

    - #### setData

          public void setData(java.lang.String data)
                       throws DOMException

      Deprecated. 
      sets the char data
      Specified by:
      [`setData`](../../../org/w3c/dom/CharacterData.md) in interface [`CharacterData`](../../../org/w3c/dom/CharacterData.md)

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md)

    <!-- -->

    - #### getLength

          public int getLength()
                        throws DOMException

      Deprecated. 
      gets the length of the char data
      Specified by:
      [`getLength`](../../../org/w3c/dom/CharacterData.md) in interface [`CharacterData`](../../../org/w3c/dom/CharacterData.md)

      Returns:
      data len

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md)

    <!-- -->

    - #### substringData

          public java.lang.String substringData(int offset,
                                                int count)
                                         throws DOMException

      Deprecated. 
      gets the specified substring of the char data
      Specified by:
      [`substringData`](../../../org/w3c/dom/CharacterData.md) in interface [`CharacterData`](../../../org/w3c/dom/CharacterData.md)

      Parameters:
      `offset` - Start offset of substring to extract.

      `count` - The number of 16-bit units to extract.

      Returns:
      substring

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md) - INDEX_SIZE_ERR: Raised if the specified `offset` is negative or greater than the number of 16-bit units in `data`, or if the specified `count` is negative.
      DOMSTRING_SIZE_ERR: Raised if the specified range of text does not fit into a `DOMString`.

    <!-- -->

    - #### appendData

          public void appendData(java.lang.String appstring)
                          throws DOMException

      Deprecated. 
      append the specified string to the char data
      Specified by:
      [`appendData`](../../../org/w3c/dom/CharacterData.md) in interface [`CharacterData`](../../../org/w3c/dom/CharacterData.md)

      Parameters:
      `appstring` - The `DOMString` to append.

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md) - NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.

    <!-- -->

    - #### insertData

          public void insertData(int offset,
                                 java.lang.String appstring)
                          throws DOMException

      Deprecated. 
      insert the specified string into the char data
      Specified by:
      [`insertData`](../../../org/w3c/dom/CharacterData.md) in interface [`CharacterData`](../../../org/w3c/dom/CharacterData.md)

      Parameters:
      `offset` - The character offset at which to insert.

      `appstring` - The `DOMString` to insert.

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md) - INDEX_SIZE_ERR: Raised if the specified `offset` is negative or greater than the number of 16-bit units in `data`.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.

    <!-- -->

    - #### deleteData

          public void deleteData(int offset,
                                 int count)
                          throws DOMException

      Deprecated. 
      delete the specified substring string from the char data
      Specified by:
      [`deleteData`](../../../org/w3c/dom/CharacterData.md) in interface [`CharacterData`](../../../org/w3c/dom/CharacterData.md)

      Parameters:
      `offset` - The offset from which to start removing.

      `count` - The number of 16-bit units to delete. If the sum of `offset` and `count` exceeds `length` then all 16-bit units from `offset` to the end of the data are deleted.

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md) - INDEX_SIZE_ERR: Raised if the specified `offset` is negative or greater than the number of 16-bit units in `data`, or if the specified `count` is negative.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.

    <!-- -->

    - #### replaceData

          public void replaceData(int offset,
                                  int count,
                                  java.lang.String repdata)
                           throws DOMException

      Deprecated. 
      replace the specified substring string in the char data
      Specified by:
      [`replaceData`](../../../org/w3c/dom/CharacterData.md) in interface [`CharacterData`](../../../org/w3c/dom/CharacterData.md)

      Parameters:
      `offset` - The offset from which to start replacing.

      `count` - The number of 16-bit units to replace. If the sum of `offset` and `count` exceeds `length`, then all 16-bit units to the end of the data are replaced; (i.e., the effect is the same as a `remove` method call with the same range, followed by an `append` method invocation).

      `repdata` - The `DOMString` with which the range must be replaced.

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md) - INDEX_SIZE_ERR: Raised if the specified `offset` is negative or greater than the number of 16-bit units in `data`, or if the specified `count` is negative.
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

- **[Prev Class](XDBCData.md)**
- **[Next Class](XDBComment.md)**

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
