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

- **[Prev Class](SAXParser.md)**
- **[Next Class](XMLCDATA.md)**

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

## **Class XMLAttr**

- **java.lang.Object**

- - **[oracle.xml.parser.v2.XMLNode](XMLNode.md)**

  - - **[oracle.xml.parser.v2.XMLNSNode](XMLNSNode.md)**

    - - **oracle.xml.parser.v2.XMLAttr**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Externalizable, java.io.Serializable, java.lang.Cloneable, [NSName](../../util/NSName.md), [Attr](../../../../org/w3c/dom/Attr.md), [EventTarget](../../../../org/w3c/dom/events/EventTarget.md), [Node](../../../../org/w3c/dom/Node.md), [NodeEditVAL](../../../../org/w3c/dom/validation/NodeEditVAL.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XMLAttr
      extends XMLNSNode
      implements Attr, NSName, java.io.Externalizable

  **This class implements the DOM Attr interface and holds information on each attribute of an element.**
  **See Also:**
  **[`Attr`](../../../../org/w3c/dom/Attr.md), [`NodeFactory`](NodeFactory.md), [`DOMParser.setNodeFactory(oracle.xml.parser.v2.NodeFactory)`](DOMParser.md), [Serialized Form](../../../../serialized-form.md)**

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

    | Constructor and Description                                                                                                                                                                                                           |
    |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `XMLAttr``()`<br>Deprecated. <br>use createAttribute(String) or createAttributeNS(String, String) of XMLDocument                                                                                                                      |
    | `XMLAttr``(java.lang.String n, java.lang.String v)`<br>Deprecated. <br>use createAttribute(String) method of XMLDocument                                                                                                              |
    | `XMLAttr``(java.lang.String name, java.lang.String prefix, java.lang.String namespace, java.lang.String v)`<br>Deprecated. <br>use createAttributeNS(String, String) method of XMLDocument                                            |
    | `XMLAttr``(java.lang.String name, java.lang.String prefix, java.lang.String qname, java.lang.String namespace, java.lang.String v)`<br>Deprecated. <br>use crateAttribute(String) or createAttributeNS(String, String) of XMLDocument |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                           | Method and Description                                                                                                                                                                                                                   |
    |-------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`XMLNode`](XMLNode.md)                                     | `addText``(java.lang.String str)`<br>Append the given value to the attribute value                                                                                                                                                       |
    | `short`                                                     | `canRemoveChild``(`[`Node`](../../../../org/w3c/dom/Node.md)` oldChild)`<br>Determines whether the `Node.removeChild` operation would make this document not compliant with the `VAL_INCOMPLETE` validity type.                          |
    | [`DOMStringList`](../../../../org/w3c/dom/DOMStringList.md) | `getEnumeratedValues``()`<br>A `DOMStringList`, as described in \[[DOM Level 3 Core](http://www.w3.org/TR/2003/CR-DOM-Level-3-Core-20031107)\] , of distinct values for an attribute or an element declaration or `null` if unspecified. |
    | `java.lang.String`                                          | `getExpandedName``()`<br>Gets the fully resolved Name for this attribute                                                                                                                                                                 |
    | [`Node`](../../../../org/w3c/dom/Node.md)                   | `getFirstChild``()`<br>Gets the first child of this node.                                                                                                                                                                                |
    | [`Node`](../../../../org/w3c/dom/Node.md)                   | `getLastChild``()`<br>Gets the last child of this node.                                                                                                                                                                                  |
    | `java.lang.String`                                          | `getLocalName``()`<br>Gets the Local Name of this node                                                                                                                                                                                   |
    | `java.lang.String`                                          | `getName``()`<br>Gets the attribute name.                                                                                                                                                                                                |
    | `java.lang.String`                                          | `getNamespaceURI``()`<br>Gets the namespace URI of this node.                                                                                                                                                                            |
    | `XMLAttr`                                                   | `getNextAttribute``()`<br>Gets the next attribute if any                                                                                                                                                                                 |
    | [`Node`](../../../../org/w3c/dom/Node.md)                   | `getNextSibling``()`<br>Gets The node immediately following this node.                                                                                                                                                                   |
    | `java.lang.String`                                          | `getNodeName``()`<br>Gets the name of this node, depending on its type                                                                                                                                                                   |
    | `short`                                                     | `getNodeType``()`<br>Gets a code representing the type of the underlying object                                                                                                                                                          |
    | `java.lang.String`                                          | `getNodeValue``()`<br>Gets the value of this node, depending on its type                                                                                                                                                                 |
    | [`Element`](../../../../org/w3c/dom/Element.md)             | `getOwnerElement``()`<br>Gets the element which owns this attribute                                                                                                                                                                      |
    | [`Node`](../../../../org/w3c/dom/Node.md)                   | `getParentNode``()`<br>Gets the parent of this node.                                                                                                                                                                                     |
    | `java.lang.String`                                          | `getPrefix``()`<br>Get the namespace prefix for this element.                                                                                                                                                                            |
    | `XMLAttr`                                                   | `getPrevAttribute``()`<br>Deprecated.                                                                                                                                                                                                    |
    | [`Node`](../../../../org/w3c/dom/Node.md)                   | `getPreviousSibling``()`<br>Gets the node immediately preceding this node.                                                                                                                                                               |
    | `java.lang.String`                                          | `getQualifiedName``()`<br>Gets the qualified name for this attribute                                                                                                                                                                     |
    | [`TypeInfo`](../../../../org/w3c/dom/TypeInfo.md)           | `getSchemaTypeInfo``()`<br>The type information associated with this attribute.                                                                                                                                                          |
    | `boolean`                                                   | `getSpecified``()`<br>Returns true if the attribute was specified explicity in the element                                                                                                                                               |
    | `java.lang.String`                                          | `getText``()`<br>Gets the attribute value.                                                                                                                                                                                               |
    | `java.lang.String`                                          | `getUniqueId``()`<br>Override the method is XMLNode for SDOM                                                                                                                                                                             |
    | `java.lang.String`                                          | `getValue``()`<br>Gets the attribute value.                                                                                                                                                                                              |
    | `void`                                                      | `setNodeValue``(java.lang.String nodeValue)`<br>Sets the value of this node, depending on its type                                                                                                                                       |
    | `void`                                                      | `setPrefix``(java.lang.String prefix)`<br>Sets the prefix for attribute Note that setting the prefix, when permitted, changes the nodeName.                                                                                              |
    | `void`                                                      | `setValue``(java.lang.String arg)`<br>Sets the value.                                                                                                                                                                                    |

    - ### Methods inherited from class oracle.xml.parser.v2.[XMLNSNode](XMLNSNode.md)

      [`addText`](XMLNSNode.md)`, `[`appendChild`](XMLNSNode.md)`, `[`getChildNodes`](XMLNSNode.md)`, `[`insertBefore`](XMLNSNode.md)`, `[`normalize`](XMLNSNode.md)`, `[`removeChild`](XMLNSNode.md)`, `[`replaceChild`](XMLNSNode.md)

    <!-- -->

    - ### Methods inherited from class oracle.xml.parser.v2.[XMLNode](XMLNode.md)

      [`addEventListener`](XMLNode.md)`, `[`canAppendChild`](XMLNode.md)`, `[`canInsertBefore`](XMLNode.md)`, `[`canReplaceChild`](XMLNode.md)`, `[`cloneNode`](XMLNode.md)`, `[`dispatchEvent`](XMLNode.md)`, `[`equals`](XMLNode.md)`, `[`getAttributes`](XMLNode.md)`, `[`getColumnNumber`](XMLNode.md)`, `[`getDebugMode`](XMLNode.md)`, `[`getDefaultValue`](XMLNode.md)`, `[`getFirstChildAsOffset`](XMLNode.md)`, `[`getLineNumber`](XMLNode.md)`, `[`getNextSiblingAsOffset`](XMLNode.md)`, `[`getNodeValueAsBinaryStream`](XMLNode.md)`, `[`getNodeValueAsBinaryStream`](XMLNode.md)`, `[`getNodeValueAsCharacterStream`](XMLNode.md)`, `[`getNodeValueAsCharacterStream`](XMLNode.md)`, `[`getOwnerDocument`](XMLNode.md)`, `[`getPrimitiveTypeId`](XMLNode.md)`, `[`getProperty`](XMLNode.md)`, `[`getSystemId`](XMLNode.md)`, `[`getXMLError`](XMLNode.md)`, `[`hasAttributes`](XMLNode.md)`, `[`hasChildNodes`](XMLNode.md)`, `[`hashCode`](XMLNode.md)`, `[`isDocumentFlag`](XMLNode.md)`, `[`isNodeFlag`](XMLNode.md)`, `[`isSupported`](XMLNode.md)`, `[`nodeValidity`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`readExternal`](XMLNode.md)`, `[`removeEventListener`](XMLNode.md)`, `[`reportSAXEvents`](XMLNode.md)`, `[`resetNodeFlag`](XMLNode.md)`, `[`selectNodes`](XMLNode.md)`, `[`selectNodes`](XMLNode.md)`, `[`selectSingleNode`](XMLNode.md)`, `[`selectSingleNode`](XMLNode.md)`, `[`setDebugInfo`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeValueAsBinaryStream`](XMLNode.md)`, `[`setNodeValueAsBinaryStream`](XMLNode.md)`, `[`setNodeValueAsCharacterStream`](XMLNode.md)`, `[`setNodeValueAsCharacterStream`](XMLNode.md)`, `[`setProperty`](XMLNode.md)`, `[`transformNode`](XMLNode.md)`, `[`valueOf`](XMLNode.md)`, `[`valueOf`](XMLNode.md)`, `[`writeExternal`](XMLNode.md)`, `[`xdbGetNodeId`](XMLNode.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface org.w3c.dom.[Node](../../../../org/w3c/dom/Node.md)

      [`appendChild`](../../../../org/w3c/dom/Node.md)`, `[`cloneNode`](../../../../org/w3c/dom/Node.md)`, `[`getAttributes`](../../../../org/w3c/dom/Node.md)`, `[`getChildNodes`](../../../../org/w3c/dom/Node.md)`, `[`getOwnerDocument`](../../../../org/w3c/dom/Node.md)`, `[`hasAttributes`](../../../../org/w3c/dom/Node.md)`, `[`hasChildNodes`](../../../../org/w3c/dom/Node.md)`, `[`insertBefore`](../../../../org/w3c/dom/Node.md)`, `[`isSupported`](../../../../org/w3c/dom/Node.md)`, `[`normalize`](../../../../org/w3c/dom/Node.md)`, `[`removeChild`](../../../../org/w3c/dom/Node.md)`, `[`replaceChild`](../../../../org/w3c/dom/Node.md)

    <!-- -->

    - ### Methods inherited from interface oracle.xml.util.[NSName](../../util/NSName.md)

      [`getNamespace`](../../util/NSName.md)

    <!-- -->

    - ### Methods inherited from interface java.io.Externalizable

      `readExternal, writeExternal`

<!-- -->

- - ### Constructor Detail

    - #### XMLAttr

          public XMLAttr()

      Deprecated. use createAttribute(String) or createAttributeNS(String, String) of XMLDocument
      Default constructor. Note that this constructor is used only during deserialization/decompression of this DOM node. In order to deserialize this node to construct the DOM node from the serialized/ compressed stream, it is required to create a handle of the object. For all normal XMLAttr creation use createAttribute(String) or createAttributeNS(String, String) of XMLDocument

    <!-- -->

    - #### XMLAttr

          public XMLAttr(java.lang.String n,
                         java.lang.String v)

      Deprecated. use createAttribute(String) method of XMLDocument
      Construct attribute with given name and value.
      Parameters:
      `n` - Name of the attribute

      `v` - Value of the attribute

    <!-- -->

    - #### XMLAttr

          public XMLAttr(java.lang.String name,
                         java.lang.String prefix,
                         java.lang.String namespace,
                         java.lang.String v)

      Deprecated. use createAttributeNS(String, String) method of XMLDocument
      Namespace support
      Parameters:
      `name` - Local name of the attribute

      `prefix` - Prefix of the attribute

      `namespace` - Namespace of the attribute

      `v` - Value of the attribute

    <!-- -->

    - #### XMLAttr

          public XMLAttr(java.lang.String name,
                         java.lang.String prefix,
                         java.lang.String qname,
                         java.lang.String namespace,
                         java.lang.String v)

      Deprecated. use crateAttribute(String) or createAttributeNS(String, String) of XMLDocument
      Private constructor (doesn't intern names)
      Parameters:
      `name` - Local name of the attribute

      `prefix` - Prefix of the attribute

      `qname` - Qname of the attribute

      `namespace` - Namespace of the attribute

      `v` - Value of the attribute

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

    - #### getName

          public java.lang.String getName()

      Gets the attribute name.
      Specified by:
      [`getName`](../../../../org/w3c/dom/Attr.md) in interface [`Attr`](../../../../org/w3c/dom/Attr.md)

      Returns:
      attribute name

    <!-- -->

    - #### getLocalName

          public java.lang.String getLocalName()

      Gets the Local Name of this node
      Specified by:
      [`getLocalName`](../../util/NSName.md) in interface [`NSName`](../../util/NSName.md)

      Specified by:
      [`getLocalName`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`getLocalName`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Returns:
      LocalName of the node

    <!-- -->

    - #### getNamespaceURI

          public java.lang.String getNamespaceURI()

      Gets the namespace URI of this node.
      Specified by:
      [`getNamespaceURI`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`getNamespaceURI`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Returns:
      the namespace

    <!-- -->

    - #### getPrefix

          public java.lang.String getPrefix()

      Get the namespace prefix for this element.
      Specified by:
      [`getPrefix`](../../util/NSName.md) in interface [`NSName`](../../util/NSName.md)

      Specified by:
      [`getPrefix`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`getPrefix`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Returns:
      the namespace prefix

    <!-- -->

    - #### setPrefix

          public void setPrefix(java.lang.String prefix)
                         throws DOMException

      Sets the prefix for attribute Note that setting the prefix, when permitted, changes the nodeName. For nodes of any type other than ELEMENT_NODE and ATTRIBUTE_NODE and nodes created with a DOM Level 1 method, such as createElement from the Document interface, prefix should always be null. Exceptions on setting DOMException INVALID_CHARACTER_ERR: Raised if the specified prefix contains an illegal character. NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly. NAMESPACE_ERR: Raised if the specified prefix is malformed, if the namespaceURI of this node is null, if the specified prefix is "xml" and the namespaceURI of this node is different from "http://www.w3.org/XML/1998/namespace", if this node is an attribute and the specified prefix is "xmlns" and the namespaceURI of this node is different from "http://www.w3.org/2000/xmlns/", or if this node is an attribute and the qualifiedName of this node is "xmlns"
      Specified by:
      [`setPrefix`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`setPrefix`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Parameters:
      `prefix` - Sets the prefix of the node

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - if any DOM Exception occurs

    <!-- -->

    - #### getText

          public final java.lang.String getText()

      Gets the attribute value.
      Overrides:
      [`getText`](XMLNSNode.md) in class [`XMLNSNode`](XMLNSNode.md)

      Returns:
      attribute value

    <!-- -->

    - #### getValue

          public java.lang.String getValue()

      Gets the attribute value.
      Specified by:
      [`getValue`](../../../../org/w3c/dom/Attr.md) in interface [`Attr`](../../../../org/w3c/dom/Attr.md)

      Returns:
      attribute value

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

    - #### setValue

          public void setValue(java.lang.String arg)
                        throws DOMException

      Sets the value.
      Specified by:
      [`setValue`](../../../../org/w3c/dom/Attr.md) in interface [`Attr`](../../../../org/w3c/dom/Attr.md)

      Parameters:
      `arg` - Value to set

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md)

    <!-- -->

    - #### setNodeValue

          public void setNodeValue(java.lang.String nodeValue)
                            throws DOMException

      Sets the value of this node, depending on its type
      Specified by:
      [`setNodeValue`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`setNodeValue`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Parameters:
      `nodeValue` - the value of thenode to be set

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - NO_MODIFICATION_ALLOWED_ERR: Raised when the node is readonly. DOMSTRING_SIZE_ERR: Raised when it would return more characters than fit in a `DOMString` variable on the implementation platform.

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

    - #### getOwnerElement

          public Element getOwnerElement()

      Gets the element which owns this attribute
      Specified by:
      [`getOwnerElement`](../../../../org/w3c/dom/Attr.md) in interface [`Attr`](../../../../org/w3c/dom/Attr.md)

      Returns:
      the element node that owns this attribute

    <!-- -->

    - #### getSpecified

          public boolean getSpecified()

      Returns true if the attribute was specified explicity in the element
      Specified by:
      [`getSpecified`](../../../../org/w3c/dom/Attr.md) in interface [`Attr`](../../../../org/w3c/dom/Attr.md)

      Returns:
      `true`, if the attribute was specified explicitly, `false`, if it was not

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

    - #### getSchemaTypeInfo

          public TypeInfo getSchemaTypeInfo()

      The type information associated with this attribute. While the type information contained in this attribute is guarantee to be correct after loading the document or invoking `Document.normalizeDocument()`, `schemaTypeInfo` may not be reliable if the node was moved.
      Since:
      DOM Level 3

    <!-- -->

    - #### canRemoveChild

          public short canRemoveChild(Node oldChild)

      Determines whether the `Node.removeChild` operation would make this document not compliant with the `VAL_INCOMPLETE` validity type.
      Specified by:
      [`canRemoveChild`](../../../../org/w3c/dom/validation/NodeEditVAL.md) in interface [`NodeEditVAL`](../../../../org/w3c/dom/validation/NodeEditVAL.md)

      Overrides:
      [`canRemoveChild`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Parameters:
      `oldChild` - `Node` to be removed.

      Returns:
      A validation state constant.

    <!-- -->

    - #### getEnumeratedValues

          public DOMStringList getEnumeratedValues()

      A `DOMStringList`, as described in \[[DOM Level 3 Core](http://www.w3.org/TR/2003/CR-DOM-Level-3-Core-20031107)\] , of distinct values for an attribute or an element declaration or `null` if unspecified. If the schema is a W3C XML schema, this is a list of strings which are lexical representations corresponding to the values in the \[value\] property of the enumeration component for the type of the attribute or element. It is recommended that the canonical lexical representations of the values be used.
      Specified by:
      [`getEnumeratedValues`](../../../../org/w3c/dom/validation/NodeEditVAL.md) in interface [`NodeEditVAL`](../../../../org/w3c/dom/validation/NodeEditVAL.md)

      Overrides:
      [`getEnumeratedValues`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

    <!-- -->

    - #### getQualifiedName

          public java.lang.String getQualifiedName()

      Gets the qualified name for this attribute
      Specified by:
      [`getQualifiedName`](../../util/NSName.md) in interface [`NSName`](../../util/NSName.md)

      Returns:
      the qualified name

    <!-- -->

    - #### getExpandedName

          public java.lang.String getExpandedName()

      Gets the fully resolved Name for this attribute
      Specified by:
      [`getExpandedName`](../../util/NSName.md) in interface [`NSName`](../../util/NSName.md)

      Returns:
      the fully resolved Name

    <!-- -->

    - #### getNextAttribute

          public XMLAttr getNextAttribute()

      Gets the next attribute if any
      Returns:
      the next attribute

    <!-- -->

    - #### addText

          public XMLNode addText(java.lang.String str)

      Append the given value to the attribute value
      Overrides:
      [`addText`](XMLNSNode.md) in class [`XMLNSNode`](XMLNSNode.md)

      Parameters:
      `str` - - text to be added

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

    <!-- -->

    - #### getUniqueId

          public java.lang.String getUniqueId()

      Override the method is XMLNode for SDOM
      Overrides:
      [`getUniqueId`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Returns:
      unique ID

    <!-- -->

    - #### getPrevAttribute

          public XMLAttr getPrevAttribute()

      Deprecated. 
      Gets the prev attribute if any
      Returns:
      the prev attribute

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

- **[Prev Class](SAXParser.md)**
- **[Next Class](XMLCDATA.md)**

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
