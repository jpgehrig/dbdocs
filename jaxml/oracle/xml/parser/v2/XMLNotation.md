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

- **[Prev Class](XMLNode.md)**
- **[Next Class](XMLNSNode.md)**

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

## **Class XMLNotation**

- **java.lang.Object**

- - **[oracle.xml.parser.v2.XMLNode](XMLNode.md)**

  - - **oracle.xml.parser.v2.XMLNotation**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Externalizable, java.io.Serializable, java.lang.Cloneable, [EventTarget](../../../../org/w3c/dom/events/EventTarget.md), [Node](../../../../org/w3c/dom/Node.md), [Notation](../../../../org/w3c/dom/Notation.md), [NodeEditVAL](../../../../org/w3c/dom/validation/NodeEditVAL.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XMLNotation
      extends XMLNode
      implements Notation, java.io.Externalizable

  **This class implements the DOM `Notation` interface and represents a notation declared in the Document Type Definition.**
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

    | Constructor and Description                                                     |
    |---------------------------------------------------------------------------------|
    | `XMLNotation``()`<br>Deprecated. <br>use XMLNotation(String)                    |
    | `XMLNotation``(java.lang.String name)`<br>Create a notation with the given name |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                         | Method and Description                                                                                                                                                             |
    |-------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Node`](../../../../org/w3c/dom/Node.md) | `getNextSibling``()`<br>Gets The node immediately following this node.                                                                                                             |
    | `java.lang.String`                        | `getNodeName``()`<br>Gets the name of this node, depending on its type                                                                                                             |
    | `short`                                   | `getNodeType``()`<br>Gets a code representing the type of the underlying object                                                                                                    |
    | [`Node`](../../../../org/w3c/dom/Node.md) | `getParentNode``()`<br>Gets the parent of this node.                                                                                                                               |
    | [`Node`](../../../../org/w3c/dom/Node.md) | `getPreviousSibling``()`<br>Gets the node immediately preceding this node.                                                                                                         |
    | `java.lang.String`                        | `getPublicId``()`<br>Gets the Public identifer; if not specified, then `null`                                                                                                      |
    | `java.lang.String`                        | `getSystemId``()`<br>Gets the System identifer; if not specified, then `null`                                                                                                      |
    | `void`                                    | `readExternal``(java.io.ObjectInput inArg)`<br>This method reads the information written in the compressed stream by writeExternal method and restores the object correspondingly. |
    | `void`                                    | `setPublicId``(java.lang.String pubid)`<br>Sets the Public Identifier                                                                                                              |
    | `void`                                    | `setSystemId``(java.lang.String url)`<br>Sets the System Identifier                                                                                                                |
    | `void`                                    | `writeExternal``(java.io.ObjectOutput outArg)`<br>This method saves the state of the object by creating a binray compressed stream with information about this object.             |

    - ### Methods inherited from class oracle.xml.parser.v2.[XMLNode](XMLNode.md)

      [`addEventListener`](XMLNode.md)`, `[`addText`](XMLNode.md)`, `[`appendChild`](XMLNode.md)`, `[`canAppendChild`](XMLNode.md)`, `[`canInsertBefore`](XMLNode.md)`, `[`canRemoveChild`](XMLNode.md)`, `[`canReplaceChild`](XMLNode.md)`, `[`cloneNode`](XMLNode.md)`, `[`dispatchEvent`](XMLNode.md)`, `[`equals`](XMLNode.md)`, `[`getAttributes`](XMLNode.md)`, `[`getChildNodes`](XMLNode.md)`, `[`getColumnNumber`](XMLNode.md)`, `[`getDebugMode`](XMLNode.md)`, `[`getDefaultValue`](XMLNode.md)`, `[`getEnumeratedValues`](XMLNode.md)`, `[`getFirstChild`](XMLNode.md)`, `[`getFirstChildAsOffset`](XMLNode.md)`, `[`getLastChild`](XMLNode.md)`, `[`getLineNumber`](XMLNode.md)`, `[`getLocalName`](XMLNode.md)`, `[`getNamespaceURI`](XMLNode.md)`, `[`getNextSiblingAsOffset`](XMLNode.md)`, `[`getNodeValue`](XMLNode.md)`, `[`getNodeValueAsBinaryStream`](XMLNode.md)`, `[`getNodeValueAsBinaryStream`](XMLNode.md)`, `[`getNodeValueAsCharacterStream`](XMLNode.md)`, `[`getNodeValueAsCharacterStream`](XMLNode.md)`, `[`getOwnerDocument`](XMLNode.md)`, `[`getPrefix`](XMLNode.md)`, `[`getPrimitiveTypeId`](XMLNode.md)`, `[`getProperty`](XMLNode.md)`, `[`getText`](XMLNode.md)`, `[`getXMLError`](XMLNode.md)`, `[`hasAttributes`](XMLNode.md)`, `[`hasChildNodes`](XMLNode.md)`, `[`hashCode`](XMLNode.md)`, `[`insertBefore`](XMLNode.md)`, `[`isDocumentFlag`](XMLNode.md)`, `[`isNodeFlag`](XMLNode.md)`, `[`isSupported`](XMLNode.md)`, `[`nodeValidity`](XMLNode.md)`, `[`normalize`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`removeChild`](XMLNode.md)`, `[`removeEventListener`](XMLNode.md)`, `[`replaceChild`](XMLNode.md)`, `[`reportSAXEvents`](XMLNode.md)`, `[`resetNodeFlag`](XMLNode.md)`, `[`selectNodes`](XMLNode.md)`, `[`selectNodes`](XMLNode.md)`, `[`selectSingleNode`](XMLNode.md)`, `[`selectSingleNode`](XMLNode.md)`, `[`setDebugInfo`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeValue`](XMLNode.md)`, `[`setNodeValueAsBinaryStream`](XMLNode.md)`, `[`setNodeValueAsBinaryStream`](XMLNode.md)`, `[`setNodeValueAsCharacterStream`](XMLNode.md)`, `[`setNodeValueAsCharacterStream`](XMLNode.md)`, `[`setPrefix`](XMLNode.md)`, `[`setProperty`](XMLNode.md)`, `[`transformNode`](XMLNode.md)`, `[`valueOf`](XMLNode.md)`, `[`valueOf`](XMLNode.md)`, `[`xdbGetNodeId`](XMLNode.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface org.w3c.dom.[Node](../../../../org/w3c/dom/Node.md)

      [`appendChild`](../../../../org/w3c/dom/Node.md)`, `[`cloneNode`](../../../../org/w3c/dom/Node.md)`, `[`getAttributes`](../../../../org/w3c/dom/Node.md)`, `[`getChildNodes`](../../../../org/w3c/dom/Node.md)`, `[`getFirstChild`](../../../../org/w3c/dom/Node.md)`, `[`getLastChild`](../../../../org/w3c/dom/Node.md)`, `[`getLocalName`](../../../../org/w3c/dom/Node.md)`, `[`getNamespaceURI`](../../../../org/w3c/dom/Node.md)`, `[`getNodeValue`](../../../../org/w3c/dom/Node.md)`, `[`getOwnerDocument`](../../../../org/w3c/dom/Node.md)`, `[`getPrefix`](../../../../org/w3c/dom/Node.md)`, `[`hasAttributes`](../../../../org/w3c/dom/Node.md)`, `[`hasChildNodes`](../../../../org/w3c/dom/Node.md)`, `[`insertBefore`](../../../../org/w3c/dom/Node.md)`, `[`isSupported`](../../../../org/w3c/dom/Node.md)`, `[`normalize`](../../../../org/w3c/dom/Node.md)`, `[`removeChild`](../../../../org/w3c/dom/Node.md)`, `[`replaceChild`](../../../../org/w3c/dom/Node.md)`, `[`setNodeValue`](../../../../org/w3c/dom/Node.md)`, `[`setPrefix`](../../../../org/w3c/dom/Node.md)

<!-- -->

- - ### Constructor Detail

    - #### XMLNotation

          public XMLNotation()

      Deprecated. use XMLNotation(String)
      Default constructor. Note that this constructor is used only during deserialization/decompression of this DOM node. In order to deserialize this node to construct the DOM node from the serialized/ compressed stream, it is required to create a handle of the object. For all normal XMLElement creation use XMLNotation(String)

    <!-- -->

    - #### XMLNotation

          public XMLNotation(java.lang.String name)

      Create a notation with the given name
      Parameters:
      `name` - Name of the notation

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

    - #### getPublicId

          public java.lang.String getPublicId()

      Gets the Public identifer; if not specified, then `null`
      Specified by:
      [`getPublicId`](../../../../org/w3c/dom/Notation.md) in interface [`Notation`](../../../../org/w3c/dom/Notation.md)

      Returns:
      The public identifier

    <!-- -->

    - #### getSystemId

          public java.lang.String getSystemId()

      Gets the System identifer; if not specified, then `null`
      Specified by:
      [`getSystemId`](../../../../org/w3c/dom/Notation.md) in interface [`Notation`](../../../../org/w3c/dom/Notation.md)

      Overrides:
      [`getSystemId`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Returns:
      The System identifier

    <!-- -->

    - #### setPublicId

          public void setPublicId(java.lang.String pubid)

      Sets the Public Identifier
      Parameters:
      `pubid` - Public Identifier to set

    <!-- -->

    - #### setSystemId

          public void setSystemId(java.lang.String url)

      Sets the System Identifier
      Parameters:
      `url` - System Identifier to set

    <!-- -->

    - #### writeExternal

          public void writeExternal(java.io.ObjectOutput outArg)
                             throws java.io.IOException

      This method saves the state of the object by creating a binray compressed stream with information about this object.
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
                                   java.lang.ClassNotFoundException

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

- **[Prev Class](XMLNode.md)**
- **[Next Class](XMLNSNode.md)**

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
