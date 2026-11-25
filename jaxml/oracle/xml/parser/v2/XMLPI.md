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

- **[Prev Class](XMLParser.md)**
- **[Next Class](XMLPrintDriver.md)**

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

## **Class XMLPI**

- **java.lang.Object**

- - **[oracle.xml.parser.v2.XMLNode](XMLNode.md)**

  - - **oracle.xml.parser.v2.XMLPI**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Externalizable, java.io.Serializable, java.lang.Cloneable, [CharacterData](../../../../org/w3c/dom/CharacterData.md), [EventTarget](../../../../org/w3c/dom/events/EventTarget.md), [Node](../../../../org/w3c/dom/Node.md), [ProcessingInstruction](../../../../org/w3c/dom/ProcessingInstruction.md), [CharacterDataEditVAL](../../../../org/w3c/dom/validation/CharacterDataEditVAL.md), [NodeEditVAL](../../../../org/w3c/dom/validation/NodeEditVAL.md)**

  <!-- -->

  **Direct Known Subclasses:**
  **[XMLDeclPI](XMLDeclPI.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XMLPI
      extends XMLNode
      implements ProcessingInstruction, java.io.Externalizable

  **This class implements the DOM Processing Instruction interface.**
  **See Also:**
  **[`ProcessingInstruction`](../../../../org/w3c/dom/ProcessingInstruction.md), [`NodeFactory`](NodeFactory.md), [`DOMParser.setNodeFactory(oracle.xml.parser.v2.NodeFactory)`](DOMParser.md), [Serialized Form](../../../../serialized-form.md)**

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

    | Constructor and Description                                                                                                         |
    |-------------------------------------------------------------------------------------------------------------------------------------|
    | `XMLPI``()`<br>Deprecated. <br>use createProcessingInstruction(String) method of XMLDocument                                        |
    | `XMLPI``(java.lang.String target, java.lang.String data)`<br>Deprecated. <br>see createProcessingInstruction(String) of XMLDocument |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type       | Method and Description                                                                                                                                       |
    |-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`XMLNode`](XMLNode.md) | `addText``(java.lang.String str)`<br>Adds text string to the node                                                                                            |
    | `void`                  | `appendData``(java.lang.String arg)`<br>Append the string to the end of the character data of the node.                                                      |
    | `short`                 | `canAppendData``(java.lang.String arg)`<br>Determines if data can be appended.                                                                               |
    | `short`                 | `canDeleteData``(int offset, int count)`<br>Determines if data can be deleted.                                                                               |
    | `short`                 | `canInsertData``(int offset, java.lang.String arg)`<br>Determines if data can be inserted.                                                                   |
    | `short`                 | `canReplaceData``(int offset, int count, java.lang.String arg)`<br>Determines if data can be replaced.                                                       |
    | `short`                 | `canSetData``(java.lang.String arg)`<br>Determines if data can be set.                                                                                       |
    | `void`                  | `deleteData``(int offset, int count)`<br>Remove a range of characters from the node.                                                                         |
    | `java.lang.String`      | `getData``()`<br>Get the character data of this node                                                                                                         |
    | `int`                   | `getLength``()`<br>The number of characters that are available through `data` and the `substringData` method below.                                          |
    | `java.lang.String`      | `getNodeName``()`<br>Gets the name of this node, depending on its type                                                                                       |
    | `short`                 | `getNodeType``()`<br>Gets a code representing the type of the underlying object                                                                              |
    | `java.lang.String`      | `getNodeValue``()`<br>Gets the value of this node, depending on its type                                                                                     |
    | `java.lang.String`      | `getTarget``()`<br>Returns the target of this PI.                                                                                                            |
    | `void`                  | `insertData``(int offset, java.lang.String arg)`<br>Insert a string at the specified character offset.                                                       |
    | `short`                 | `isWhitespaceOnly``()`<br>Determines if data is only whitespace.                                                                                             |
    | `short`                 | `nodeValidity``(boolean deep, short wFValidityCheckLevel)`<br>Determines if the node is valid relative to the validation type specified in `valType`.        |
    | `void`                  | `replaceData``(int offset, int count, java.lang.String arg)`<br>Replace the characters starting at the specified character offset with the specified string. |
    | `void`                  | `reportSAXEvents``(`[`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)` cntHandler)`<br>Report SAX Events from a DOM Tree                         |
    | `void`                  | `setData``(java.lang.String data)`<br>Set the character data of this node                                                                                    |
    | `void`                  | `setNodeValue``(java.lang.String nodeValue)`<br>The value of this node, depending on its type overrides method in XMLNode.                                   |
    | `java.lang.String`      | `substringData``(int offset, int count)`<br>Extracts a range of data from the node.                                                                          |

    - ### Methods inherited from class oracle.xml.parser.v2.[XMLNode](XMLNode.md)

      [`addEventListener`](XMLNode.md)`, `[`addText`](XMLNode.md)`, `[`appendChild`](XMLNode.md)`, `[`canAppendChild`](XMLNode.md)`, `[`canInsertBefore`](XMLNode.md)`, `[`canRemoveChild`](XMLNode.md)`, `[`canReplaceChild`](XMLNode.md)`, `[`cloneNode`](XMLNode.md)`, `[`dispatchEvent`](XMLNode.md)`, `[`equals`](XMLNode.md)`, `[`getAttributes`](XMLNode.md)`, `[`getChildNodes`](XMLNode.md)`, `[`getColumnNumber`](XMLNode.md)`, `[`getDebugMode`](XMLNode.md)`, `[`getDefaultValue`](XMLNode.md)`, `[`getEnumeratedValues`](XMLNode.md)`, `[`getFirstChild`](XMLNode.md)`, `[`getFirstChildAsOffset`](XMLNode.md)`, `[`getLastChild`](XMLNode.md)`, `[`getLineNumber`](XMLNode.md)`, `[`getLocalName`](XMLNode.md)`, `[`getNamespaceURI`](XMLNode.md)`, `[`getNextSibling`](XMLNode.md)`, `[`getNextSiblingAsOffset`](XMLNode.md)`, `[`getNodeValueAsBinaryStream`](XMLNode.md)`, `[`getNodeValueAsBinaryStream`](XMLNode.md)`, `[`getNodeValueAsCharacterStream`](XMLNode.md)`, `[`getNodeValueAsCharacterStream`](XMLNode.md)`, `[`getOwnerDocument`](XMLNode.md)`, `[`getParentNode`](XMLNode.md)`, `[`getPrefix`](XMLNode.md)`, `[`getPreviousSibling`](XMLNode.md)`, `[`getPrimitiveTypeId`](XMLNode.md)`, `[`getProperty`](XMLNode.md)`, `[`getSystemId`](XMLNode.md)`, `[`getText`](XMLNode.md)`, `[`getXMLError`](XMLNode.md)`, `[`hasAttributes`](XMLNode.md)`, `[`hasChildNodes`](XMLNode.md)`, `[`hashCode`](XMLNode.md)`, `[`insertBefore`](XMLNode.md)`, `[`isDocumentFlag`](XMLNode.md)`, `[`isNodeFlag`](XMLNode.md)`, `[`isSupported`](XMLNode.md)`, `[`nodeValidity`](XMLNode.md)`, `[`normalize`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`readExternal`](XMLNode.md)`, `[`removeChild`](XMLNode.md)`, `[`removeEventListener`](XMLNode.md)`, `[`replaceChild`](XMLNode.md)`, `[`resetNodeFlag`](XMLNode.md)`, `[`selectNodes`](XMLNode.md)`, `[`selectNodes`](XMLNode.md)`, `[`selectSingleNode`](XMLNode.md)`, `[`selectSingleNode`](XMLNode.md)`, `[`setDebugInfo`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeValueAsBinaryStream`](XMLNode.md)`, `[`setNodeValueAsBinaryStream`](XMLNode.md)`, `[`setNodeValueAsCharacterStream`](XMLNode.md)`, `[`setNodeValueAsCharacterStream`](XMLNode.md)`, `[`setPrefix`](XMLNode.md)`, `[`setProperty`](XMLNode.md)`, `[`transformNode`](XMLNode.md)`, `[`valueOf`](XMLNode.md)`, `[`valueOf`](XMLNode.md)`, `[`writeExternal`](XMLNode.md)`, `[`xdbGetNodeId`](XMLNode.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface org.w3c.dom.[ProcessingInstruction](../../../../org/w3c/dom/ProcessingInstruction.md)

      [`setData`](../../../../org/w3c/dom/ProcessingInstruction.md)

    <!-- -->

    - ### Methods inherited from interface org.w3c.dom.[Node](../../../../org/w3c/dom/Node.md)

      [`appendChild`](../../../../org/w3c/dom/Node.md)`, `[`cloneNode`](../../../../org/w3c/dom/Node.md)`, `[`getAttributes`](../../../../org/w3c/dom/Node.md)`, `[`getChildNodes`](../../../../org/w3c/dom/Node.md)`, `[`getFirstChild`](../../../../org/w3c/dom/Node.md)`, `[`getLastChild`](../../../../org/w3c/dom/Node.md)`, `[`getLocalName`](../../../../org/w3c/dom/Node.md)`, `[`getNamespaceURI`](../../../../org/w3c/dom/Node.md)`, `[`getNextSibling`](../../../../org/w3c/dom/Node.md)`, `[`getNodeValue`](../../../../org/w3c/dom/Node.md)`, `[`getOwnerDocument`](../../../../org/w3c/dom/Node.md)`, `[`getParentNode`](../../../../org/w3c/dom/Node.md)`, `[`getPrefix`](../../../../org/w3c/dom/Node.md)`, `[`getPreviousSibling`](../../../../org/w3c/dom/Node.md)`, `[`hasAttributes`](../../../../org/w3c/dom/Node.md)`, `[`hasChildNodes`](../../../../org/w3c/dom/Node.md)`, `[`insertBefore`](../../../../org/w3c/dom/Node.md)`, `[`isSupported`](../../../../org/w3c/dom/Node.md)`, `[`normalize`](../../../../org/w3c/dom/Node.md)`, `[`removeChild`](../../../../org/w3c/dom/Node.md)`, `[`replaceChild`](../../../../org/w3c/dom/Node.md)`, `[`setNodeValue`](../../../../org/w3c/dom/Node.md)`, `[`setPrefix`](../../../../org/w3c/dom/Node.md)

    <!-- -->

    - ### Methods inherited from interface java.io.Externalizable

      `readExternal, writeExternal`

    <!-- -->

    - ### Methods inherited from interface org.w3c.dom.validation.[NodeEditVAL](../../../../org/w3c/dom/validation/NodeEditVAL.md)

      [`canAppendChild`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`canInsertBefore`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`canRemoveChild`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`canReplaceChild`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`getDefaultValue`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`getEnumeratedValues`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`nodeValidity`](../../../../org/w3c/dom/validation/NodeEditVAL.md)

<!-- -->

- - ### Constructor Detail

    - #### XMLPI

          public XMLPI()

      Deprecated. use createProcessingInstruction(String) method of XMLDocument
      Default constructor. Note that this constructor is used only during deserialization/decompression of this DOM node. In order to deserialize this node to construct the DOM node from the serialized/ compressed stream, it is required to create a handle of the object.

    <!-- -->

    - #### XMLPI

          public XMLPI(java.lang.String target,
                       java.lang.String data)

      Deprecated. see createProcessingInstruction(String) of XMLDocument
      Creates a new ProcessingInstruction node with the given target and the data.
      Parameters:
      `target` - The target of this PI

      `data` - The content of this PI

  <!-- -->

  - ### Method Detail

    - #### getNodeType

          public short getNodeType()

      Gets a code representing the type of the underlying object
      Specified by:
      [`getNodeType`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`getNodeType`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Returns:
      type of the node

    <!-- -->

    - #### getNodeName

          public java.lang.String getNodeName()

      Gets the name of this node, depending on its type
      Specified by:
      [`getNodeName`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`getNodeName`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Returns:
      Name of this node

    <!-- -->

    - #### getData

          public java.lang.String getData()

      Get the character data of this node
      Specified by:
      [`getData`](../../../../org/w3c/dom/CharacterData.md) in interface [`CharacterData`](../../../../org/w3c/dom/CharacterData.md)

      Specified by:
      [`getData`](../../../../org/w3c/dom/ProcessingInstruction.md) in interface [`ProcessingInstruction`](../../../../org/w3c/dom/ProcessingInstruction.md)

      Returns:
      the character data

    <!-- -->

    - #### getTarget

          public java.lang.String getTarget()

      Returns the target of this PI. XML defines this as the first token following markup that begins the processing instruction.
      Specified by:
      [`getTarget`](../../../../org/w3c/dom/ProcessingInstruction.md) in interface [`ProcessingInstruction`](../../../../org/w3c/dom/ProcessingInstruction.md)

      Returns:
      The target of the PI.

    <!-- -->

    - #### addText

          public XMLNode addText(java.lang.String str)

      Adds text string to the node
      Parameters:
      `str` - the text string to be added

      Returns:
      the node

    <!-- -->

    - #### reportSAXEvents

          public void reportSAXEvents(ContentHandler cntHandler)
                               throws SAXException

      Report SAX Events from a DOM Tree
      Overrides:
      [`reportSAXEvents`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Parameters:
      `cntHandler` - ContentHandler

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - thrown by SAX Callback functions

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

    - #### getNodeValue

          public java.lang.String getNodeValue()
                                        throws DOMException

      Gets the value of this node, depending on its type
      Specified by:
      [`getNodeValue`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`getNodeValue`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Returns:
      Value of this node

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - NO_MODIFICATION_ALLOWED_ERR: Raised when the node is readonly. DOMSTRING_SIZE_ERR: Raised when it would return more characters than fit in a `DOMString` variable on the implementation platform.

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

    - #### isWhitespaceOnly

          public short isWhitespaceOnly()

      Determines if data is only whitespace.
      Specified by:
      [`isWhitespaceOnly`](../../../../org/w3c/dom/validation/CharacterDataEditVAL.md) in interface [`CharacterDataEditVAL`](../../../../org/w3c/dom/validation/CharacterDataEditVAL.md)

      Returns:
      A validation state constant.

    <!-- -->

    - #### canSetData

          public short canSetData(java.lang.String arg)

      Determines if data can be set.
      Specified by:
      [`canSetData`](../../../../org/w3c/dom/validation/CharacterDataEditVAL.md) in interface [`CharacterDataEditVAL`](../../../../org/w3c/dom/validation/CharacterDataEditVAL.md)

      Parameters:
      `arg` - Argument to be set.

      Returns:
      A validation state constant.

    <!-- -->

    - #### canAppendData

          public short canAppendData(java.lang.String arg)

      Determines if data can be appended.
      Specified by:
      [`canAppendData`](../../../../org/w3c/dom/validation/CharacterDataEditVAL.md) in interface [`CharacterDataEditVAL`](../../../../org/w3c/dom/validation/CharacterDataEditVAL.md)

      Parameters:
      `arg` - Data to be appended.

      Returns:
      A validation state constant.

    <!-- -->

    - #### canReplaceData

          public short canReplaceData(int offset,
                                      int count,
                                      java.lang.String arg)
                               throws DOMException

      Determines if data can be replaced.
      Specified by:
      [`canReplaceData`](../../../../org/w3c/dom/validation/CharacterDataEditVAL.md) in interface [`CharacterDataEditVAL`](../../../../org/w3c/dom/validation/CharacterDataEditVAL.md)

      Parameters:
      `offset` - Offset.

      `count` - Replacement.

      `arg` - Argument to be set.

      Returns:
      A validation state constant.

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - INDEX_SIZE_ERR: Raised if the specified offset is negative or greater than the number of 16-bit units in data, or if the specified count is negative.

    <!-- -->

    - #### canInsertData

          public short canInsertData(int offset,
                                     java.lang.String arg)
                              throws DOMException

      Determines if data can be inserted.
      Specified by:
      [`canInsertData`](../../../../org/w3c/dom/validation/CharacterDataEditVAL.md) in interface [`CharacterDataEditVAL`](../../../../org/w3c/dom/validation/CharacterDataEditVAL.md)

      Parameters:
      `offset` - Offset.

      `arg` - Argument to be set.

      Returns:
      A validation state constant.

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - INDEX_SIZE_ERR: Raised if the specified offset is negative or greater than the number of 16-bit units in data.

    <!-- -->

    - #### canDeleteData

          public short canDeleteData(int offset,
                                     int count)
                              throws DOMException

      Determines if data can be deleted.
      Specified by:
      [`canDeleteData`](../../../../org/w3c/dom/validation/CharacterDataEditVAL.md) in interface [`CharacterDataEditVAL`](../../../../org/w3c/dom/validation/CharacterDataEditVAL.md)

      Parameters:
      `offset` - Offset.

      `count` - Number of 16-bit units to delete.

      Returns:
      A validation state constant.

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - INDEX_SIZE_ERR: Raised if the specified offset is negative or greater than the number of 16-bit units in data, or if the specified count is negative.

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

- **[Prev Class](XMLParser.md)**
- **[Next Class](XMLPrintDriver.md)**

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
