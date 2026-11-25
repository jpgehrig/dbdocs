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

- **[Prev Class](DOMParser.md)**
- **[Next Class](ElementDecl.md)**

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

## **Class DTD**

- **java.lang.Object**

- - **[oracle.xml.parser.v2.XMLNode](XMLNode.md)**

  - - **oracle.xml.parser.v2.DTD**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Externalizable, java.io.Serializable, java.lang.Cloneable, [DocumentType](../../../../org/w3c/dom/DocumentType.md), [EventTarget](../../../../org/w3c/dom/events/EventTarget.md), [Node](../../../../org/w3c/dom/Node.md), [NodeEditVAL](../../../../org/w3c/dom/validation/NodeEditVAL.md)**

  ------------------------------------------------------------------------

  **
  **

      public class DTD
      extends XMLNode
      implements DocumentType, java.io.Externalizable

  **Implements the DOM DocumentType interface and holds the Document Type Definition information for an XML document.**
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

    | Constructor and Description       |
    |-----------------------------------|
    | `DTD``()`<br>Default constructor. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                         | Method and Description                                                                                                                                                                                                                       |
    |-----------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`XMLDocument`](XMLDocument.md)                           | `convertDTD2Schema``()`<br>get XML Schema DOM tree from this DTD object                                                                                                                                                                      |
    | [`ElementDecl`](ElementDecl.md)                           | `findElementDecl``(java.lang.String name)`<br>Finds an element declaration for the given tag name.                                                                                                                                           |
    | [`Entity`](../../../../org/w3c/dom/Entity.md)             | `findEntity``(java.lang.String name, boolean isPE)`<br>Finds a named entity in the DTD.                                                                                                                                                      |
    | [`Notation`](../../../../org/w3c/dom/Notation.md)         | `findNotation``(java.lang.String name)`<br>Retrieves the named notation from the DTD.                                                                                                                                                        |
    | [`NamedNodeMap`](../../../../org/w3c/dom/NamedNodeMap.md) | `getElementDecls``()`<br>A `NamedNodeMap` containing the element declarations in the DTD.                                                                                                                                                    |
    | [`NamedNodeMap`](../../../../org/w3c/dom/NamedNodeMap.md) | `getEntities``()`<br>A `NamedNodeMap` containing the general entities, both external and internal, declared in the DTD.                                                                                                                      |
    | `java.lang.String`                                        | `getInternalSubset``()`<br>Gets the internal subset of the DTD                                                                                                                                                                               |
    | `java.lang.String`                                        | `getName``()`<br>Gets the name of the DTD; i.e., the name immediately following the `DOCTYPE` keyword.                                                                                                                                       |
    | `java.lang.String`                                        | `getNodeName``()`<br>Gets the name of this node, depending on its type                                                                                                                                                                       |
    | `short`                                                   | `getNodeType``()`<br>Gets a code representing the type of the underlying object                                                                                                                                                              |
    | [`NamedNodeMap`](../../../../org/w3c/dom/NamedNodeMap.md) | `getNotations``()`<br>A `NamedNodeMap` containing the notations declared in the DTD.                                                                                                                                                         |
    | [`Document`](../../../../org/w3c/dom/Document.md)         | `getOwnerDocument``()`<br>Gets the `Document` object associated with this node.                                                                                                                                                              |
    | `java.lang.String`                                        | `getPublicId``()`<br>Gets The public identifier associated with the DTD, if specified.                                                                                                                                                       |
    | `java.lang.String`                                        | `getRootTag``()`<br>Get the root tag for the DTD                                                                                                                                                                                             |
    | `java.lang.String`                                        | `getSystemId``()`<br>Gets the system identifier associated with the DTD, if specified.                                                                                                                                                       |
    | `boolean`                                                 | `hasChildNodes``()`<br>This is a convenience method to allow easy determination of whether a node has any children. return false always, as DTD cannot have any overrides method in XMLNode                                                  |
    | [`Node`](../../../../org/w3c/dom/Node.md)                 | `insertBefore``(`[`Node`](../../../../org/w3c/dom/Node.md)` newChild, `[`Node`](../../../../org/w3c/dom/Node.md)` refChild)`<br>Inserts the node `newChild` before the existing child node `refChild`.                                       |
    | `void`                                                    | `printExternalDTD``(java.io.OutputStream out)`<br>Writes the contents of this document to the given output stream.                                                                                                                           |
    | `void`                                                    | `printExternalDTD``(java.io.OutputStream out, java.lang.String enc)`<br>Writes the contents of the external DTD to the given output stream.                                                                                                  |
    | `void`                                                    | `printExternalDTD``(java.io.PrintWriter out)`<br>Writes the contents of this document to the given output stream.                                                                                                                            |
    | `void`                                                    | `readExternal``(java.io.ObjectInput inArg)`<br>This method reads the information written in the compressed stream by writeExternal method and restores the object correspondingly.                                                           |
    | [`Node`](../../../../org/w3c/dom/Node.md)                 | `replaceChild``(`[`Node`](../../../../org/w3c/dom/Node.md)` newChild, `[`Node`](../../../../org/w3c/dom/Node.md)` oldChild)`<br>Replaces the child node `oldChild` with `newChild` in the list of children, and returns the `oldChild` node. |
    | `void`                                                    | `setRootTag``(java.lang.String root)`<br>Set the root tag for the DTD                                                                                                                                                                        |
    | `void`                                                    | `writeExternal``(java.io.ObjectOutput outArg)`<br>This method saves the state of the object by creating a binray compressed stream with information about this object.                                                                       |

    - ### Methods inherited from class oracle.xml.parser.v2.[XMLNode](XMLNode.md)

      [`addEventListener`](XMLNode.md)`, `[`addText`](XMLNode.md)`, `[`appendChild`](XMLNode.md)`, `[`canAppendChild`](XMLNode.md)`, `[`canInsertBefore`](XMLNode.md)`, `[`canRemoveChild`](XMLNode.md)`, `[`canReplaceChild`](XMLNode.md)`, `[`cloneNode`](XMLNode.md)`, `[`dispatchEvent`](XMLNode.md)`, `[`equals`](XMLNode.md)`, `[`getAttributes`](XMLNode.md)`, `[`getChildNodes`](XMLNode.md)`, `[`getColumnNumber`](XMLNode.md)`, `[`getDebugMode`](XMLNode.md)`, `[`getDefaultValue`](XMLNode.md)`, `[`getEnumeratedValues`](XMLNode.md)`, `[`getFirstChild`](XMLNode.md)`, `[`getFirstChildAsOffset`](XMLNode.md)`, `[`getLastChild`](XMLNode.md)`, `[`getLineNumber`](XMLNode.md)`, `[`getLocalName`](XMLNode.md)`, `[`getNamespaceURI`](XMLNode.md)`, `[`getNextSibling`](XMLNode.md)`, `[`getNextSiblingAsOffset`](XMLNode.md)`, `[`getNodeValue`](XMLNode.md)`, `[`getNodeValueAsBinaryStream`](XMLNode.md)`, `[`getNodeValueAsBinaryStream`](XMLNode.md)`, `[`getNodeValueAsCharacterStream`](XMLNode.md)`, `[`getNodeValueAsCharacterStream`](XMLNode.md)`, `[`getParentNode`](XMLNode.md)`, `[`getPrefix`](XMLNode.md)`, `[`getPreviousSibling`](XMLNode.md)`, `[`getPrimitiveTypeId`](XMLNode.md)`, `[`getProperty`](XMLNode.md)`, `[`getText`](XMLNode.md)`, `[`getXMLError`](XMLNode.md)`, `[`hasAttributes`](XMLNode.md)`, `[`hashCode`](XMLNode.md)`, `[`isDocumentFlag`](XMLNode.md)`, `[`isNodeFlag`](XMLNode.md)`, `[`isSupported`](XMLNode.md)`, `[`nodeValidity`](XMLNode.md)`, `[`normalize`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`removeChild`](XMLNode.md)`, `[`removeEventListener`](XMLNode.md)`, `[`reportSAXEvents`](XMLNode.md)`, `[`resetNodeFlag`](XMLNode.md)`, `[`selectNodes`](XMLNode.md)`, `[`selectNodes`](XMLNode.md)`, `[`selectSingleNode`](XMLNode.md)`, `[`selectSingleNode`](XMLNode.md)`, `[`setDebugInfo`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeValue`](XMLNode.md)`, `[`setNodeValueAsBinaryStream`](XMLNode.md)`, `[`setNodeValueAsBinaryStream`](XMLNode.md)`, `[`setNodeValueAsCharacterStream`](XMLNode.md)`, `[`setNodeValueAsCharacterStream`](XMLNode.md)`, `[`setPrefix`](XMLNode.md)`, `[`setProperty`](XMLNode.md)`, `[`transformNode`](XMLNode.md)`, `[`valueOf`](XMLNode.md)`, `[`valueOf`](XMLNode.md)`, `[`xdbGetNodeId`](XMLNode.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface org.w3c.dom.[Node](../../../../org/w3c/dom/Node.md)

      [`appendChild`](../../../../org/w3c/dom/Node.md)`, `[`cloneNode`](../../../../org/w3c/dom/Node.md)`, `[`getAttributes`](../../../../org/w3c/dom/Node.md)`, `[`getChildNodes`](../../../../org/w3c/dom/Node.md)`, `[`getFirstChild`](../../../../org/w3c/dom/Node.md)`, `[`getLastChild`](../../../../org/w3c/dom/Node.md)`, `[`getLocalName`](../../../../org/w3c/dom/Node.md)`, `[`getNamespaceURI`](../../../../org/w3c/dom/Node.md)`, `[`getNextSibling`](../../../../org/w3c/dom/Node.md)`, `[`getNodeValue`](../../../../org/w3c/dom/Node.md)`, `[`getParentNode`](../../../../org/w3c/dom/Node.md)`, `[`getPrefix`](../../../../org/w3c/dom/Node.md)`, `[`getPreviousSibling`](../../../../org/w3c/dom/Node.md)`, `[`hasAttributes`](../../../../org/w3c/dom/Node.md)`, `[`isSupported`](../../../../org/w3c/dom/Node.md)`, `[`normalize`](../../../../org/w3c/dom/Node.md)`, `[`removeChild`](../../../../org/w3c/dom/Node.md)`, `[`setNodeValue`](../../../../org/w3c/dom/Node.md)`, `[`setPrefix`](../../../../org/w3c/dom/Node.md)

<!-- -->

- - ### Constructor Detail

    - #### DTD

          public DTD()

      Default constructor. Note that this constructor is used only during deserialization/decompression of this DOM node. In order to deserialize this node to construct the DOM node from the serialized/ compressed stream, it is required to create a handle of the object.

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

      Gets the name of the DTD; i.e., the name immediately following the `DOCTYPE` keyword.
      Specified by:
      [`getName`](../../../../org/w3c/dom/DocumentType.md) in interface [`DocumentType`](../../../../org/w3c/dom/DocumentType.md)

      Returns:
      Name of the DTD

    <!-- -->

    - #### getEntities

          public NamedNodeMap getEntities()

      A `NamedNodeMap` containing the general entities, both external and internal, declared in the DTD. Duplicates are discarded. For example in:\<!DOCTYPE ex SYSTEM "ex.dtd" \[ \<!ENTITY foo "foo"\> \<!ENTITY bar "bar"\> \<!ENTITY % baz "baz"\>\]\> \<ex/\> the interface provides access to `foo` and `bar` but not `baz`. Every node in this map also implements the `Entity` interface.
      The DOM Level 1 does not support editing entities, therefore `entities` cannot be altered in any way.
      Specified by:
      [`getEntities`](../../../../org/w3c/dom/DocumentType.md) in interface [`DocumentType`](../../../../org/w3c/dom/DocumentType.md)

      Returns:
      The entities declared in the DTD

    <!-- -->

    - #### getNotations

          public NamedNodeMap getNotations()

      A `NamedNodeMap` containing the notations declared in the DTD. Duplicates are discarded. Every node in this map also implements the `Notation` interface.
      The DOM Level 1 does not support editing notations, therefore `notations` cannot be altered in any way.
      Specified by:
      [`getNotations`](../../../../org/w3c/dom/DocumentType.md) in interface [`DocumentType`](../../../../org/w3c/dom/DocumentType.md)

      Returns:
      The notations declared in the DTD

    <!-- -->

    - #### getElementDecls

          public NamedNodeMap getElementDecls()

      A `NamedNodeMap` containing the element declarations in the DTD. Every node in this map is an `ElementDecl` object.
      Returns:
      The element declarations in the DTD
      The DOM Level 1 does not support editing elementdecls, therefore `elementdecls` cannot be altered in any way.

    <!-- -->

    - #### hasChildNodes

          public boolean hasChildNodes()

      This is a convenience method to allow easy determination of whether a node has any children. return false always, as DTD cannot have any overrides method in XMLNode
      Specified by:
      [`hasChildNodes`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`hasChildNodes`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Returns:
      `false` as DTD node can not have any children,

    <!-- -->

    - #### getPublicId

          public java.lang.String getPublicId()

      Gets The public identifier associated with the DTD, if specified. If the public identifier was not specified, this is `null`.
      Specified by:
      [`getPublicId`](../../../../org/w3c/dom/DocumentType.md) in interface [`DocumentType`](../../../../org/w3c/dom/DocumentType.md)

      Returns:
      the public identifier associated with the DTD

    <!-- -->

    - #### getSystemId

          public java.lang.String getSystemId()

      Gets the system identifier associated with the DTD, if specified. If the system identifier was not specified, this is `null`.
      Specified by:
      [`getSystemId`](../../../../org/w3c/dom/DocumentType.md) in interface [`DocumentType`](../../../../org/w3c/dom/DocumentType.md)

      Overrides:
      [`getSystemId`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Returns:
      the system identifier associated with the DTD

    <!-- -->

    - #### getInternalSubset

          public java.lang.String getInternalSubset()

      Gets the internal subset of the DTD
      Specified by:
      [`getInternalSubset`](../../../../org/w3c/dom/DocumentType.md) in interface [`DocumentType`](../../../../org/w3c/dom/DocumentType.md)

      Returns:
      the internal subset declarations as a string

    <!-- -->

    - #### getOwnerDocument

          public Document getOwnerDocument()

      Gets the `Document` object associated with this node. This is also the `Document` object used to create new nodes. When this node is a `Document` this is `null`.
      Specified by:
      [`getOwnerDocument`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`getOwnerDocument`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Returns:
      The document associated with this node

    <!-- -->

    - #### setRootTag

          public void setRootTag(java.lang.String root)

      Set the root tag for the DTD
      Parameters:
      `root` - the root tag

    <!-- -->

    - #### getRootTag

          public java.lang.String getRootTag()

      Get the root tag for the DTD
      Returns:
      root tag

    <!-- -->

    - #### findEntity

          public final Entity findEntity(java.lang.String name,
                                         boolean isPE)

      Finds a named entity in the DTD.
      Parameters:
      `name` - The name of the entity.

      `isPE` - Is this a parameter entity (as opposed to a general entity)?

      Returns:
      the specified `Entity` object; returns null if it is not found.

    <!-- -->

    - #### findElementDecl

          public final ElementDecl findElementDecl(java.lang.String name)

      Finds an element declaration for the given tag name.
      Parameters:
      `name` - The tag name.

      Returns:
      the element declaration object.

    <!-- -->

    - #### findNotation

          public final Notation findNotation(java.lang.String name)

      Retrieves the named notation from the DTD.
      Parameters:
      `name` - The name of the notation.

      Returns:
      the `Notation` object; returns null if it is not found.

    <!-- -->

    - #### convertDTD2Schema

          public XMLDocument convertDTD2Schema()

      get XML Schema DOM tree from this DTD object
      Returns:
      converted XML Schema Document

    <!-- -->

    - #### printExternalDTD

          public void printExternalDTD(java.io.PrintWriter out)
                                throws java.io.IOException

      Writes the contents of this document to the given output stream.
      Parameters:
      `out` - `PrintWriter` to write to

      Throws:
      `java.io.IOException` - if an error occurs

    <!-- -->

    - #### printExternalDTD

          public void printExternalDTD(java.io.OutputStream out)
                                throws java.io.IOException

      Writes the contents of this document to the given output stream.
      Parameters:
      `out` - `OutputStream` to write to

      Throws:
      `java.io.IOException` - if an error occurs

    <!-- -->

    - #### printExternalDTD

          public void printExternalDTD(java.io.OutputStream out,
                                       java.lang.String enc)
                                throws java.io.IOException

      Writes the contents of the external DTD to the given output stream.
      Parameters:
      `out` - `OutputStream` to write to

      `enc` - Encoding to use for the output

      Throws:
      `java.io.IOException` - if an invalid encoding was specified or if any other error occurs

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

    <!-- -->

    - #### insertBefore

          public Node insertBefore(Node newChild,
                                   Node refChild)
                            throws DOMException

      Inserts the node `newChild` before the existing child node `refChild`. If `refChild` is `null`, insert `newChild` at the end of the list of children.
      If `newChild` is a `DocumentFragment` object, all of its children are inserted, in the same order, before `refChild`. If the `newChild` is already in the tree, it is first removed.
      Specified by:
      [`insertBefore`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`insertBefore`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Parameters:
      `newChild` - The node to insert.

      `refChild` - The reference node, i.e., the node before which the new node must be inserted.

      Returns:
      The node being inserted.

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - HIERARCHY_REQUEST_ERR: Raised if this node is of a type that does not allow children of the type of the `newChild` node, or if the node to insert is one of this node's ancestors.
      WRONG_DOCUMENT_ERR: Raised if `newChild` was created from a different document than the one that created this node.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.
      NOT_FOUND_ERR: Raised if `refChild` is not a child of this node.

    <!-- -->

    - #### replaceChild

          public Node replaceChild(Node newChild,
                                   Node oldChild)
                            throws DOMException

      Replaces the child node `oldChild` with `newChild` in the list of children, and returns the `oldChild` node. If the `newChild` is already in the tree, it is first removed.
      Specified by:
      [`replaceChild`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`replaceChild`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Parameters:
      `newChild` - The new node to put in the child list.

      `oldChild` - The node being replaced in the list.

      Returns:
      The node replaced.

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - HIERARCHY_REQUEST_ERR: Raised if this node is of a type that does not allow children of the type of the `newChild` node, or it the node to put in is one of this node's ancestors.
      WRONG_DOCUMENT_ERR: Raised if `newChild` was created from a different document than the one that created this node.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.
      NOT_FOUND_ERR: Raised if `oldChild` is not a child of this node.

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

- **[Prev Class](DOMParser.md)**
- **[Next Class](ElementDecl.md)**

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
