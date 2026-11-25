Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](XMLAttr.md)**
- **[Next Class](XMLComment.md)**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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

**oracle.xml.parser.v2**

## **Class XMLCDATA**

- **java.lang.Object**

- - **[oracle.xml.parser.v2.XMLNode](XMLNode.md)**

  - - **[oracle.xml.parser.v2.XMLText](XMLText.md)**

    - - **oracle.xml.parser.v2.XMLCDATA**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Externalizable, java.io.Serializable, java.lang.Cloneable, [CDATASection](../../../../org/w3c/dom/CDATASection.md), [CharacterData](../../../../org/w3c/dom/CharacterData.md), [EventTarget](../../../../org/w3c/dom/events/EventTarget.md), [Node](../../../../org/w3c/dom/Node.md), [Text](../../../../org/w3c/dom/Text.md), [CharacterDataEditVAL](../../../../org/w3c/dom/validation/CharacterDataEditVAL.md), [NodeEditVAL](../../../../org/w3c/dom/validation/NodeEditVAL.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XMLCDATA
      extends XMLText
      implements CDATASection, java.io.Externalizable

  **This class implements the DOM CDATASection interface.**
  **See Also:**
  **[`CDATASection`](../../../../org/w3c/dom/CDATASection.md), [`NodeFactory`](NodeFactory.md), [`DOMParser.setNodeFactory(oracle.xml.parser.v2.NodeFactory)`](DOMParser.md), [Serialized Form](../../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Field Summary**

    -

      ### **Fields inherited from class oracle.xml.parser.v2.[XMLNode](XMLNode.md)**

      **[`ATTRDECL`](XMLNode.md)`, `[`Auto_Events`](XMLNode.md)`, `[`capturing`](XMLNode.md)`, `[`DOMAttrModified`](XMLNode.md)`, `[`DOMCharacterDataModified`](XMLNode.md)`, `[`DOMNodeInserted`](XMLNode.md)`, `[`DOMNodeInsertedIntoDocument`](XMLNode.md)`, `[`DOMNodeRemoved`](XMLNode.md)`, `[`DOMNodeRemovedFromDocument`](XMLNode.md)`, `[`DOMSubtreeModified`](XMLNode.md)`, `[`ELEMENTDECL`](XMLNode.md)`, `[`KEPT_NODE`](XMLNode.md)`, `[`NAMESPACE_NODE`](XMLNode.md)`, `[`noncapturing`](XMLNode.md)`, `[`RANGE_DELETE_EVENT`](XMLNode.md)`, `[`RANGE_DELETETEXT_EVENT`](XMLNode.md)`, `[`RANGE_INSERT_EVENT`](XMLNode.md)`, `[`RANGE_INSERTTEXT_EVENT`](XMLNode.md)`, `[`RANGE_REPLACE_EVENT`](XMLNode.md)`, `[`RANGE_SETTEXT_EVENT`](XMLNode.md)`, `[`TRAVERSAL_DELETE_EVENT`](XMLNode.md)`, `[`TRAVERSAL_REPLACE_EVENT`](XMLNode.md)`, `[`XMLDECL_NODE`](XMLNode.md)**

    <!-- -->

    -

      ### **Fields inherited from interface org.w3c.dom.[Node](../../../../org/w3c/dom/Node.md)**

      **[`ATTRIBUTE_NODE`](../../../../org/w3c/dom/Node.md)`, `[`CDATA_SECTION_NODE`](../../../../org/w3c/dom/Node.md)`, `[`COMMENT_NODE`](../../../../org/w3c/dom/Node.md)`, `[`DOCUMENT_FRAGMENT_NODE`](../../../../org/w3c/dom/Node.md)`, `[`DOCUMENT_NODE`](../../../../org/w3c/dom/Node.md)`, `[`DOCUMENT_TYPE_NODE`](../../../../org/w3c/dom/Node.md)`, `[`ELEMENT_NODE`](../../../../org/w3c/dom/Node.md)`, `[`ENTITY_NODE`](../../../../org/w3c/dom/Node.md)`, `[`ENTITY_REFERENCE_NODE`](../../../../org/w3c/dom/Node.md)`, `[`NOTATION_NODE`](../../../../org/w3c/dom/Node.md)`, `[`PROCESSING_INSTRUCTION_NODE`](../../../../org/w3c/dom/Node.md)`, `[`TEXT_NODE`](../../../../org/w3c/dom/Node.md)**

    <!-- -->

    -

      ### **Fields inherited from interface org.w3c.dom.validation.[NodeEditVAL](../../../../org/w3c/dom/validation/NodeEditVAL.md)**

      **[`VAL_FALSE`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`VAL_INCOMPLETE`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`VAL_NS_WF`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`VAL_SCHEMA`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`VAL_TRUE`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`VAL_UNKNOWN`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`VAL_WF`](../../../../org/w3c/dom/validation/NodeEditVAL.md)**

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                 |
    |-------------------------------------------------------------------------------------------------------------|
    | `XMLCDATA``()`<br>Deprecated. <br>use createCDATASection(String) method of XMLDocument                      |
    | `XMLCDATA``(java.lang.String text)`<br>Deprecated. <br>see createCDATASection(String) method of XMLDocument |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                                       |
    |--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`             | `appendData``(java.lang.String arg)`<br>Append the string to the end of the character data of the node.                                                      |
    | `void`             | `deleteData``(int offset, int count)`<br>Remove a range of characters from the node.                                                                         |
    | `int`              | `getLength``()`<br>The number of characters that are available through `data` and the `substringData` method below.                                          |
    | `java.lang.String` | `getNodeName``()`<br>Gets a name of the node                                                                                                                 |
    | `short`            | `getNodeType``()`<br>Gets a code representing the type of the underlying object                                                                              |
    | `void`             | `insertData``(int offset, java.lang.String arg)`<br>Insert a string at the specified character offset.                                                       |
    | `short`            | `nodeValidity``(boolean deep, short wFValidityCheckLevel)`<br>Determines if the node is valid relative to the validation type specified in `valType`.        |
    | `short`            | `nodeValidity``(short wFValidityCheckLevel)`<br>DOM 3 ValidationAPI's \*\*\*                                                                                 |
    | `void`             | `replaceData``(int offset, int count, java.lang.String arg)`<br>Replace the characters starting at the specified character offset with the specified string. |
    | `void`             | `reportSAXEvents``(`[`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)` cntHandler)`<br>Report SAX Events from a DOM Tree                         |
    | `void`             | `setData``(java.lang.String data)`<br>Set the character data of this node                                                                                    |
    | `void`             | `setNodeValue``(java.lang.String nodeValue)`<br>The value of this node, depending on its type overrides method in XMLNode.                                   |
    | `java.lang.String` | `substringData``(int offset, int count)`<br>Extracts a range of data from the node.                                                                          |

    - ### Methods inherited from class oracle.xml.parser.v2.[XMLText](XMLText.md)

      [`addText`](XMLText.md)`, `[`canAppendData`](XMLText.md)`, `[`canDeleteData`](XMLText.md)`, `[`canInsertData`](XMLText.md)`, `[`canReplaceData`](XMLText.md)`, `[`canSetData`](XMLText.md)`, `[`getData`](XMLText.md)`, `[`getNodeValue`](XMLText.md)`, `[`isWhiteSpaceNode`](XMLText.md)`, `[`isWhitespaceOnly`](XMLText.md)`, `[`splitText`](XMLText.md)

    <!-- -->

    - ### Methods inherited from class oracle.xml.parser.v2.[XMLNode](XMLNode.md)

      [`addEventListener`](XMLNode.md)`, `[`appendChild`](XMLNode.md)`, `[`canAppendChild`](XMLNode.md)`, `[`canInsertBefore`](XMLNode.md)`, `[`canRemoveChild`](XMLNode.md)`, `[`canReplaceChild`](XMLNode.md)`, `[`cloneNode`](XMLNode.md)`, `[`dispatchEvent`](XMLNode.md)`, `[`equals`](XMLNode.md)`, `[`getAttributes`](XMLNode.md)`, `[`getChildNodes`](XMLNode.md)`, `[`getColumnNumber`](XMLNode.md)`, `[`getDebugMode`](XMLNode.md)`, `[`getDefaultValue`](XMLNode.md)`, `[`getEnumeratedValues`](XMLNode.md)`, `[`getFirstChild`](XMLNode.md)`, `[`getFirstChildAsOffset`](XMLNode.md)`, `[`getLastChild`](XMLNode.md)`, `[`getLineNumber`](XMLNode.md)`, `[`getLocalName`](XMLNode.md)`, `[`getNamespaceURI`](XMLNode.md)`, `[`getNextSibling`](XMLNode.md)`, `[`getNextSiblingAsOffset`](XMLNode.md)`, `[`getNodeValueAsBinaryStream`](XMLNode.md)`, `[`getNodeValueAsBinaryStream`](XMLNode.md)`, `[`getNodeValueAsCharacterStream`](XMLNode.md)`, `[`getNodeValueAsCharacterStream`](XMLNode.md)`, `[`getOwnerDocument`](XMLNode.md)`, `[`getParentNode`](XMLNode.md)`, `[`getPrefix`](XMLNode.md)`, `[`getPreviousSibling`](XMLNode.md)`, `[`getPrimitiveTypeId`](XMLNode.md)`, `[`getProperty`](XMLNode.md)`, `[`getSystemId`](XMLNode.md)`, `[`getText`](XMLNode.md)`, `[`getXMLError`](XMLNode.md)`, `[`hasAttributes`](XMLNode.md)`, `[`hasChildNodes`](XMLNode.md)`, `[`hashCode`](XMLNode.md)`, `[`insertBefore`](XMLNode.md)`, `[`isDocumentFlag`](XMLNode.md)`, `[`isNodeFlag`](XMLNode.md)`, `[`isSupported`](XMLNode.md)`, `[`normalize`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`readExternal`](XMLNode.md)`, `[`removeChild`](XMLNode.md)`, `[`removeEventListener`](XMLNode.md)`, `[`replaceChild`](XMLNode.md)`, `[`resetNodeFlag`](XMLNode.md)`, `[`selectNodes`](XMLNode.md)`, `[`selectNodes`](XMLNode.md)`, `[`selectSingleNode`](XMLNode.md)`, `[`selectSingleNode`](XMLNode.md)`, `[`setDebugInfo`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeValueAsBinaryStream`](XMLNode.md)`, `[`setNodeValueAsBinaryStream`](XMLNode.md)`, `[`setNodeValueAsCharacterStream`](XMLNode.md)`, `[`setNodeValueAsCharacterStream`](XMLNode.md)`, `[`setPrefix`](XMLNode.md)`, `[`setProperty`](XMLNode.md)`, `[`transformNode`](XMLNode.md)`, `[`valueOf`](XMLNode.md)`, `[`valueOf`](XMLNode.md)`, `[`writeExternal`](XMLNode.md)`, `[`xdbGetNodeId`](XMLNode.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface org.w3c.dom.[Text](../../../../org/w3c/dom/Text.md)

      [`splitText`](../../../../org/w3c/dom/Text.md)

    <!-- -->

    - ### Methods inherited from interface org.w3c.dom.[CharacterData](../../../../org/w3c/dom/CharacterData.md)

      [`appendData`](../../../../org/w3c/dom/CharacterData.md)`, `[`deleteData`](../../../../org/w3c/dom/CharacterData.md)`, `[`getData`](../../../../org/w3c/dom/CharacterData.md)`, `[`getLength`](../../../../org/w3c/dom/CharacterData.md)`, `[`insertData`](../../../../org/w3c/dom/CharacterData.md)`, `[`replaceData`](../../../../org/w3c/dom/CharacterData.md)`, `[`setData`](../../../../org/w3c/dom/CharacterData.md)`, `[`substringData`](../../../../org/w3c/dom/CharacterData.md)

    <!-- -->

    - ### Methods inherited from interface org.w3c.dom.[Node](../../../../org/w3c/dom/Node.md)

      [`appendChild`](../../../../org/w3c/dom/Node.md)`, `[`cloneNode`](../../../../org/w3c/dom/Node.md)`, `[`getAttributes`](../../../../org/w3c/dom/Node.md)`, `[`getChildNodes`](../../../../org/w3c/dom/Node.md)`, `[`getFirstChild`](../../../../org/w3c/dom/Node.md)`, `[`getLastChild`](../../../../org/w3c/dom/Node.md)`, `[`getLocalName`](../../../../org/w3c/dom/Node.md)`, `[`getNamespaceURI`](../../../../org/w3c/dom/Node.md)`, `[`getNextSibling`](../../../../org/w3c/dom/Node.md)`, `[`getNodeValue`](../../../../org/w3c/dom/Node.md)`, `[`getOwnerDocument`](../../../../org/w3c/dom/Node.md)`, `[`getParentNode`](../../../../org/w3c/dom/Node.md)`, `[`getPrefix`](../../../../org/w3c/dom/Node.md)`, `[`getPreviousSibling`](../../../../org/w3c/dom/Node.md)`, `[`hasAttributes`](../../../../org/w3c/dom/Node.md)`, `[`hasChildNodes`](../../../../org/w3c/dom/Node.md)`, `[`insertBefore`](../../../../org/w3c/dom/Node.md)`, `[`isSupported`](../../../../org/w3c/dom/Node.md)`, `[`normalize`](../../../../org/w3c/dom/Node.md)`, `[`removeChild`](../../../../org/w3c/dom/Node.md)`, `[`replaceChild`](../../../../org/w3c/dom/Node.md)`, `[`setNodeValue`](../../../../org/w3c/dom/Node.md)`, `[`setPrefix`](../../../../org/w3c/dom/Node.md)

    <!-- -->

    - ### Methods inherited from interface java.io.Externalizable

      `readExternal, writeExternal`

    <!-- -->

    - ### Methods inherited from interface org.w3c.dom.validation.[NodeEditVAL](../../../../org/w3c/dom/validation/NodeEditVAL.md)

      [`canAppendChild`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`canInsertBefore`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`canRemoveChild`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`canReplaceChild`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`getDefaultValue`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`getEnumeratedValues`](../../../../org/w3c/dom/validation/NodeEditVAL.md)

<!-- -->

- - ### Constructor Detail

    - #### XMLCDATA

          public XMLCDATA()

      Deprecated. use createCDATASection(String) method of XMLDocument
      Default constructor. Note that this constructor is used only during deserialization/decompression of this DOM node. In order to deserialize this node to construct the DOM node from the serialized/ compressed stream, it is required to create a handle of the object.

    <!-- -->

    - #### XMLCDATA

          public XMLCDATA(java.lang.String text)

      Deprecated. see createCDATASection(String) method of XMLDocument
      Creates a CDATA node having the given name and text.
      Parameters:
      `text` - Text of the node

  <!-- -->

  - ### Method Detail

    - #### getNodeType

          public short getNodeType()

      Gets a code representing the type of the underlying object
      Specified by:
      [`getNodeType`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`getNodeType`](XMLText.md) in class [`XMLText`](XMLText.md)

      Returns:
      type of the node

    <!-- -->

    - #### getNodeName

          public java.lang.String getNodeName()

      Gets a name of the node
      Specified by:
      [`getNodeName`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`getNodeName`](XMLText.md) in class [`XMLText`](XMLText.md)

      Returns:
      name of the node

    <!-- -->

    - #### reportSAXEvents

          public void reportSAXEvents(ContentHandler cntHandler)
                               throws SAXException

      Report SAX Events from a DOM Tree
      Overrides:
      [`reportSAXEvents`](XMLText.md) in class [`XMLText`](XMLText.md)

      Parameters:
      `cntHandler` - cntHandler

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - thrown by SAX Callback functions

    <!-- -->

    - #### nodeValidity

          public short nodeValidity(short wFValidityCheckLevel)

      DOM 3 ValidationAPI's \*\*\*
      Specified by:
      [`nodeValidity`](../../../../org/w3c/dom/validation/NodeEditVAL.md) in interface [`NodeEditVAL`](../../../../org/w3c/dom/validation/NodeEditVAL.md)

      Overrides:
      [`nodeValidity`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Parameters:
      `wFValidityCheckLevel` - Flag to tell at what level validity and well-formedness checking is done.

      Returns:
      A validation state constant.

    <!-- -->

    - #### setData

          public void setData(java.lang.String data)
                       throws DOMException

      Set the character data of this node
      Specified by:
      [`setData`](../../../../org/w3c/dom/CharacterData.md) in interface [`CharacterData`](../../../../org/w3c/dom/CharacterData.md)

      Parameters:
      `data` - the character data to be set

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - NO_MODIFICATION_ALLOWED_ERR: Raised when the node is readonly.

      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - DOMSTRING_SIZE_ERR: Raised when it would return more characters than fit in a `DOMString` variable on the implementation platform.

    <!-- -->

    - #### setNodeValue

          public void setNodeValue(java.lang.String nodeValue)
                            throws DOMException

      The value of this node, depending on its type overrides method in XMLNode.
      Specified by:
      [`setNodeValue`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`setNodeValue`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - NO_MODIFICATION_ALLOWED_ERR: Raised when the node is readonly.

      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - DOMSTRING_SIZE_ERR: Raised when it would return more characters than fit in a `DOMString` variable on the implementation platform.

    <!-- -->

    - #### getLength

          public int getLength()

      The number of characters that are available through `data` and the `substringData` method below. This may have the value zero, i.e., `CharacterData` nodes may be empty.
      Specified by:
      [`getLength`](../../../../org/w3c/dom/CharacterData.md) in interface [`CharacterData`](../../../../org/w3c/dom/CharacterData.md)

    <!-- -->

    - #### substringData

          public java.lang.String substringData(int offset,
                                                int count)
                                         throws DOMException

      Extracts a range of data from the node.
      Specified by:
      [`substringData`](../../../../org/w3c/dom/CharacterData.md) in interface [`CharacterData`](../../../../org/w3c/dom/CharacterData.md)

      Parameters:
      `offset` - Start offset of substring to extract.

      `count` - The number of characters to extract.

      Returns:
      The specified substring. If the sum of `offset` and `count` exceeds the `length`, then all characters to the end of the data are returned.

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - INDEX_SIZE_ERR: Raised if the specified offset is negative or greater than the number of characters in `data`, or if the specified `count` is negative.
      DOMSTRING_SIZE_ERR: Raised if the specified range of text does not fit into a `DOMString`.

    <!-- -->

    - #### appendData

          public void appendData(java.lang.String arg)
                          throws DOMException

      Append the string to the end of the character data of the node. Upon success, `data` provides access to the concatenation of `data` and the `DOMString` specified.
      Specified by:
      [`appendData`](../../../../org/w3c/dom/CharacterData.md) in interface [`CharacterData`](../../../../org/w3c/dom/CharacterData.md)

      Parameters:
      `arg` - The `DOMString` to append.

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.

    <!-- -->

    - #### insertData

          public void insertData(int offset,
                                 java.lang.String arg)
                          throws DOMException

      Insert a string at the specified character offset.
      Specified by:
      [`insertData`](../../../../org/w3c/dom/CharacterData.md) in interface [`CharacterData`](../../../../org/w3c/dom/CharacterData.md)

      Parameters:
      `offset` - The character offset at which to insert.

      `arg` - The `DOMString` to insert.

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - INDEX_SIZE_ERR: Raised if the specified offset is negative or greater than the number of characters in `data`.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.

    <!-- -->

    - #### deleteData

          public void deleteData(int offset,
                                 int count)
                          throws DOMException

      Remove a range of characters from the node. Upon success, `data` and `length` reflect the change.
      Specified by:
      [`deleteData`](../../../../org/w3c/dom/CharacterData.md) in interface [`CharacterData`](../../../../org/w3c/dom/CharacterData.md)

      Parameters:
      `offset` - The offset from which to remove characters.

      `count` - The number of characters to delete. If the sum of `offset` and `count` exceeds `length` then all characters from `offset` to the end of the data are deleted.

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - INDEX_SIZE_ERR: Raised if the specified offset is negative or greater than the number of characters in `data`, or if the specified `count` is negative.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.

    <!-- -->

    - #### replaceData

          public void replaceData(int offset,
                                  int count,
                                  java.lang.String arg)
                           throws DOMException

      Replace the characters starting at the specified character offset with the specified string.
      Specified by:
      [`replaceData`](../../../../org/w3c/dom/CharacterData.md) in interface [`CharacterData`](../../../../org/w3c/dom/CharacterData.md)

      Parameters:
      `offset` - The offset from which to start replacing.

      `count` - The number of characters to replace. If the sum of `offset` and `count` exceeds `length` , then all characters to the end of the data are replaced (i.e., the effect is the same as a `remove` method call with the same range, followed by an `append` method invocation).

      `arg` - The `DOMString` with which the range must be replaced.

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - INDEX_SIZE_ERR: Raised if the specified offset is negative or greater than the number of characters in `data`, or if the specified `count` is negative.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.

    <!-- -->

    - #### nodeValidity

          public short nodeValidity(boolean deep,
                                    short wFValidityCheckLevel)

      Determines if the node is valid relative to the validation type specified in `valType`. This operation doesn't normalize before checking if it is valid. To do so, one would need to explicitly call a normalize method. The difference between this method and the `validateDocument` method on the `DocumentVAL` interface is that `validateDocument` only checks to determine whether the entire document is valid.
      Parameters:
      `wFValidityCheckLevel` - Flag to tell at what level validity and well-formedness checking is done.

      Returns:
      A validation state constant.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](XMLAttr.md)**
- **[Next Class](XMLComment.md)**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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
