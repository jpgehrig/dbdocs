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

- **[Prev Class](XMLElement.md)**
- **[Next Class](XMLEntityReference.md)**

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

## **Class XMLEntity**

- **java.lang.Object**

- - **[oracle.xml.parser.v2.XMLNode](XMLNode.md)**

  - - **[oracle.xml.parser.v2.XMLNSNode](XMLNSNode.md)**

    - - **oracle.xml.parser.v2.XMLEntity**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Externalizable, java.io.Serializable, java.lang.Cloneable, [Entity](../../../../org/w3c/dom/Entity.md), [EventTarget](../../../../org/w3c/dom/events/EventTarget.md), [Node](../../../../org/w3c/dom/Node.md), [NodeEditVAL](../../../../org/w3c/dom/validation/NodeEditVAL.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XMLEntity
      extends XMLNSNode
      implements Entity, java.io.Externalizable

  **This class implements the DOM `Entity` interface and represents an XML internal or external entity as defined in the XML Document Type Definition (DTD).**
  **See Also:**
  **[Serialized Form](../../../../serialized-form.md)**

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

    | Constructor and Description             |
    |-----------------------------------------|
    | `XMLEntity``()`<br>Default constructor. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                         | Method and Description                                                                                                                                                             |
    |-------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Node`](../../../../org/w3c/dom/Node.md) | `getFirstChild``()`<br>Gets the first child of this node.                                                                                                                          |
    | [`Node`](../../../../org/w3c/dom/Node.md) | `getLastChild``()`<br>Gets the last child of this node.                                                                                                                            |
    | [`Node`](../../../../org/w3c/dom/Node.md) | `getNextSibling``()`<br>Gets The node immediately following this node.                                                                                                             |
    | `java.lang.String`                        | `getNodeName``()`<br>Gets the name of this node, depending on its type                                                                                                             |
    | `short`                                   | `getNodeType``()`<br>Gets a code representing the type of the underlying object                                                                                                    |
    | `java.lang.String`                        | `getNodeValue``()`<br>Gets the value of this node, depending on its type                                                                                                           |
    | `java.lang.String`                        | `getNotationName``()`<br>For unparsed entities, gets the name of the notation for the entity.                                                                                      |
    | [`Node`](../../../../org/w3c/dom/Node.md) | `getParentNode``()`<br>Gets the parent of this node.                                                                                                                               |
    | [`Node`](../../../../org/w3c/dom/Node.md) | `getPreviousSibling``()`<br>Gets the node immediately preceding this node.                                                                                                         |
    | `java.lang.String`                        | `getPublicId``()`<br>Gets the public identifier associated with the entity, if specified.                                                                                          |
    | `java.lang.String`                        | `getSystemId``()`<br>Gets the system identifier associated with the entity, if specified.                                                                                          |
    | `void`                                    | `readExternal``(java.io.ObjectInput inArg)`<br>This method reads the information written in the compressed stream by writeExternal method and restores the object correspondingly. |
    | `void`                                    | `setNodeValue``(java.lang.String arg)`<br>Sets the value of entity.                                                                                                                |
    | `void`                                    | `writeExternal``(java.io.ObjectOutput outArg)`<br>This method saves the state of the object by creating a binary compressed stream with information about this object.             |

    - ### Methods inherited from class oracle.xml.parser.v2.[XMLNSNode](XMLNSNode.md)

      [`addText`](XMLNSNode.md)`, `[`addText`](XMLNSNode.md)`, `[`appendChild`](XMLNSNode.md)`, `[`getChildNodes`](XMLNSNode.md)`, `[`getText`](XMLNSNode.md)`, `[`insertBefore`](XMLNSNode.md)`, `[`normalize`](XMLNSNode.md)`, `[`removeChild`](XMLNSNode.md)`, `[`replaceChild`](XMLNSNode.md)

    <!-- -->

    - ### Methods inherited from class oracle.xml.parser.v2.[XMLNode](XMLNode.md)

      [`addEventListener`](XMLNode.md)`, `[`canAppendChild`](XMLNode.md)`, `[`canInsertBefore`](XMLNode.md)`, `[`canRemoveChild`](XMLNode.md)`, `[`canReplaceChild`](XMLNode.md)`, `[`cloneNode`](XMLNode.md)`, `[`dispatchEvent`](XMLNode.md)`, `[`equals`](XMLNode.md)`, `[`getAttributes`](XMLNode.md)`, `[`getColumnNumber`](XMLNode.md)`, `[`getDebugMode`](XMLNode.md)`, `[`getDefaultValue`](XMLNode.md)`, `[`getEnumeratedValues`](XMLNode.md)`, `[`getFirstChildAsOffset`](XMLNode.md)`, `[`getLineNumber`](XMLNode.md)`, `[`getLocalName`](XMLNode.md)`, `[`getNamespaceURI`](XMLNode.md)`, `[`getNextSiblingAsOffset`](XMLNode.md)`, `[`getNodeValueAsBinaryStream`](XMLNode.md)`, `[`getNodeValueAsBinaryStream`](XMLNode.md)`, `[`getNodeValueAsCharacterStream`](XMLNode.md)`, `[`getNodeValueAsCharacterStream`](XMLNode.md)`, `[`getOwnerDocument`](XMLNode.md)`, `[`getPrefix`](XMLNode.md)`, `[`getPrimitiveTypeId`](XMLNode.md)`, `[`getProperty`](XMLNode.md)`, `[`getXMLError`](XMLNode.md)`, `[`hasAttributes`](XMLNode.md)`, `[`hasChildNodes`](XMLNode.md)`, `[`hashCode`](XMLNode.md)`, `[`isDocumentFlag`](XMLNode.md)`, `[`isNodeFlag`](XMLNode.md)`, `[`isSupported`](XMLNode.md)`, `[`nodeValidity`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`removeEventListener`](XMLNode.md)`, `[`reportSAXEvents`](XMLNode.md)`, `[`resetNodeFlag`](XMLNode.md)`, `[`selectNodes`](XMLNode.md)`, `[`selectNodes`](XMLNode.md)`, `[`selectSingleNode`](XMLNode.md)`, `[`selectSingleNode`](XMLNode.md)`, `[`setDebugInfo`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeValueAsBinaryStream`](XMLNode.md)`, `[`setNodeValueAsBinaryStream`](XMLNode.md)`, `[`setNodeValueAsCharacterStream`](XMLNode.md)`, `[`setNodeValueAsCharacterStream`](XMLNode.md)`, `[`setPrefix`](XMLNode.md)`, `[`setProperty`](XMLNode.md)`, `[`transformNode`](XMLNode.md)`, `[`valueOf`](XMLNode.md)`, `[`valueOf`](XMLNode.md)`, `[`xdbGetNodeId`](XMLNode.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface org.w3c.dom.[Node](../../../../org/w3c/dom/Node.md)

      [`appendChild`](../../../../org/w3c/dom/Node.md)`, `[`cloneNode`](../../../../org/w3c/dom/Node.md)`, `[`getAttributes`](../../../../org/w3c/dom/Node.md)`, `[`getChildNodes`](../../../../org/w3c/dom/Node.md)`, `[`getLocalName`](../../../../org/w3c/dom/Node.md)`, `[`getNamespaceURI`](../../../../org/w3c/dom/Node.md)`, `[`getOwnerDocument`](../../../../org/w3c/dom/Node.md)`, `[`getPrefix`](../../../../org/w3c/dom/Node.md)`, `[`hasAttributes`](../../../../org/w3c/dom/Node.md)`, `[`hasChildNodes`](../../../../org/w3c/dom/Node.md)`, `[`insertBefore`](../../../../org/w3c/dom/Node.md)`, `[`isSupported`](../../../../org/w3c/dom/Node.md)`, `[`normalize`](../../../../org/w3c/dom/Node.md)`, `[`removeChild`](../../../../org/w3c/dom/Node.md)`, `[`replaceChild`](../../../../org/w3c/dom/Node.md)`, `[`setPrefix`](../../../../org/w3c/dom/Node.md)

<!-- -->

- - ### Constructor Detail

    - #### XMLEntity

          public XMLEntity()

      Default constructor. Note that this constructor is used only during deserialization/decompression of this DOM node. In order to deserialize this node to construct the DOM node from the serialized/compressed stream, it is required to create a handle of the object.

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

    - #### getPublicId

          public java.lang.String getPublicId()

      Gets the public identifier associated with the entity, if specified. If the public identifier was not specified, this is `null`.
      Specified by:
      [`getPublicId`](../../../../org/w3c/dom/Entity.md) in interface [`Entity`](../../../../org/w3c/dom/Entity.md)

      Returns:
      The public identifier

    <!-- -->

    - #### getSystemId

          public java.lang.String getSystemId()

      Gets the system identifier associated with the entity, if specified. If the system identifier was not specified, this is `null`.
      Specified by:
      [`getSystemId`](../../../../org/w3c/dom/Entity.md) in interface [`Entity`](../../../../org/w3c/dom/Entity.md)

      Overrides:
      [`getSystemId`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Returns:
      The system identifier

    <!-- -->

    - #### getNotationName

          public java.lang.String getNotationName()

      For unparsed entities, gets the name of the notation for the entity. For parsed entities, this is `null`.
      Specified by:
      [`getNotationName`](../../../../org/w3c/dom/Entity.md) in interface [`Entity`](../../../../org/w3c/dom/Entity.md)

      Returns:
      The notation name

    <!-- -->

    - #### getParentNode

          public Node getParentNode()

      Gets the parent of this node. All nodes, except `Document`, `DocumentFragment`, and `Attr` may have a parent. However, if a node has just been created and not yet added to the tree, or if it has been removed from the tree, this is `null`.
      Specified by:
      [`getParentNode`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`getParentNode`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Returns:
      The parent of this node

    <!-- -->

    - #### getPreviousSibling

          public Node getPreviousSibling()

      Gets the node immediately preceding this node. If there is no such node, this returns `null`.
      Specified by:
      [`getPreviousSibling`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`getPreviousSibling`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Returns:
      the previous node

    <!-- -->

    - #### getNextSibling

          public Node getNextSibling()

      Gets The node immediately following this node. If there is no such node, this returns `null`.
      Specified by:
      [`getNextSibling`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`getNextSibling`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Returns:
      the next node

    <!-- -->

    - #### setNodeValue

          public void setNodeValue(java.lang.String arg)

      Sets the value of entity.
      Specified by:
      [`setNodeValue`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`setNodeValue`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Parameters:
      `arg` - The new value of the entity.

    <!-- -->

    - #### writeExternal

          public void writeExternal(java.io.ObjectOutput outArg)
                             throws java.io.IOException

      This method saves the state of the object by creating a binary compressed stream with information about this object.
      Specified by:
      `writeExternal` in interface `java.io.Externalizable`

      Overrides:
      [`writeExternal`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Parameters:
      `outArg` - The ObjectOutput stream used to write the serialized/ compressed stream.

      Throws:
      `java.io.IOException` - is thrown when there is an exception while writing the serialized/compressed stream.

    <!-- -->

    - #### readExternal

          public void readExternal(java.io.ObjectInput inArg)
                            throws java.io.IOException,
                                   java.lang.ClassNotFoundException,
                                   java.io.EOFException

      This method reads the information written in the compressed stream by writeExternal method and restores the object correspondingly.
      Specified by:
      `readExternal` in interface `java.io.Externalizable`

      Overrides:
      [`readExternal`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Parameters:
      `inArg` - the ObjectInput stream used for reading the compressed stream.

      Throws:
      `java.io.IOException` - is thrown when there is an error in reading the input stream.

      `java.lang.ClassNotFoundException` - is thrown when the class is not found.

      `java.io.EOFException` - is thrown when End of File is encountered.

    <!-- -->

    - #### getFirstChild

          public Node getFirstChild()

      Gets the first child of this node. If there is no such node, this returns `null`.
      Specified by:
      [`getFirstChild`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`getFirstChild`](XMLNSNode.md) in class [`XMLNSNode`](XMLNSNode.md)

      Returns:
      The first child of this node

    <!-- -->

    - #### getLastChild

          public Node getLastChild()

      Gets the last child of this node. If there is no such node, this returns `null`.
      Specified by:
      [`getLastChild`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`getLastChild`](XMLNSNode.md) in class [`XMLNSNode`](XMLNSNode.md)

      Returns:
      The last child of this node

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

- **[Prev Class](XMLElement.md)**
- **[Next Class](XMLEntityReference.md)**

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
