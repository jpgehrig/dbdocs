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

- **[Prev Class](XMLNotation.md)**
- **[Next Class](XMLObjectInputStream.md)**

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

## **Class XMLNSNode**

- **java.lang.Object**

- - **[oracle.xml.parser.v2.XMLNode](XMLNode.md)**

  - - **oracle.xml.parser.v2.XMLNSNode**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Externalizable, java.io.Serializable, java.lang.Cloneable, [EventTarget](../../../../org/w3c/dom/events/EventTarget.md), [Node](../../../../org/w3c/dom/Node.md), [NodeEditVAL](../../../../org/w3c/dom/validation/NodeEditVAL.md)**

  <!-- -->

  **Direct Known Subclasses:**
  **[XMLAttr](XMLAttr.md), [XMLElement](XMLElement.md), [XMLEntity](XMLEntity.md), [XMLEntityReference](XMLEntityReference.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XMLNSNode
      extends XMLNode
      implements java.io.Externalizable

  **Extends XMLNode to add support for Namespace names and children**
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

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                 | Method and Description                                                                                                                                                                                                                                                                                                                              |
    |---------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                            | `addText``(char[] ch, int start, int length)`<br>Adds text to this node, or appends str to the last child if the last child is a text node.                                                                                                                                                                                                         |
    | [`XMLNode`](XMLNode.md)                           | `addText``(java.lang.String str)`<br>Adds text to this node, or appends str to the last child if the last child is a text node.                                                                                                                                                                                                                     |
    | [`Node`](../../../../org/w3c/dom/Node.md)         | `appendChild``(`[`Node`](../../../../org/w3c/dom/Node.md)` newChildArg)`<br>Adds the node `newChild` to the end of the list of children of this node.                                                                                                                                                                                               |
    | [`NodeList`](../../../../org/w3c/dom/NodeList.md) | `getChildNodes``()`<br>Gets a `NodeList` that contains all children of this node.                                                                                                                                                                                                                                                                   |
    | [`Node`](../../../../org/w3c/dom/Node.md)         | `getFirstChild``()`<br>Gets the first child of this node.                                                                                                                                                                                                                                                                                           |
    | [`Node`](../../../../org/w3c/dom/Node.md)         | `getLastChild``()`<br>Gets the last child of this node.                                                                                                                                                                                                                                                                                             |
    | `java.lang.String`                                | `getText``()`<br>Returns the non-marked-up text contained by this element.                                                                                                                                                                                                                                                                          |
    | [`Node`](../../../../org/w3c/dom/Node.md)         | `insertBefore``(`[`Node`](../../../../org/w3c/dom/Node.md)` newChildArg, `[`Node`](../../../../org/w3c/dom/Node.md)` refChildArg)`<br>Inserts the node `newChild` before the existing child node `refChild`.                                                                                                                                        |
    | `void`                                            | `normalize``()`<br>Puts all Text nodes in the full depth of the sub-tree underneath this Node, including attribute nodes, into "normal" form where only structure (e.g., elements, comments, processing instructions, CDATA sections, and entity references) separates Text nodes,i.e., there are neither adjacent Text nodes nor empty Text nodes. |
    | [`Node`](../../../../org/w3c/dom/Node.md)         | `removeChild``(`[`Node`](../../../../org/w3c/dom/Node.md)` oldChildArg)`<br>Removes the child node indicated by `oldChildArg` from the list of children, and returns it.                                                                                                                                                                            |
    | [`Node`](../../../../org/w3c/dom/Node.md)         | `replaceChild``(`[`Node`](../../../../org/w3c/dom/Node.md)` newChildArg, `[`Node`](../../../../org/w3c/dom/Node.md)` oldChildArg)`<br>Replaces the child node `oldChildArg` with `newChildArg` in the list of children, and returns the `oldChildArg` node.                                                                                         |

    - ### Methods inherited from class oracle.xml.parser.v2.[XMLNode](XMLNode.md)

      [`addEventListener`](XMLNode.md)`, `[`canAppendChild`](XMLNode.md)`, `[`canInsertBefore`](XMLNode.md)`, `[`canRemoveChild`](XMLNode.md)`, `[`canReplaceChild`](XMLNode.md)`, `[`cloneNode`](XMLNode.md)`, `[`dispatchEvent`](XMLNode.md)`, `[`equals`](XMLNode.md)`, `[`getAttributes`](XMLNode.md)`, `[`getColumnNumber`](XMLNode.md)`, `[`getDebugMode`](XMLNode.md)`, `[`getDefaultValue`](XMLNode.md)`, `[`getEnumeratedValues`](XMLNode.md)`, `[`getFirstChildAsOffset`](XMLNode.md)`, `[`getLineNumber`](XMLNode.md)`, `[`getLocalName`](XMLNode.md)`, `[`getNamespaceURI`](XMLNode.md)`, `[`getNextSibling`](XMLNode.md)`, `[`getNextSiblingAsOffset`](XMLNode.md)`, `[`getNodeName`](XMLNode.md)`, `[`getNodeType`](XMLNode.md)`, `[`getNodeValue`](XMLNode.md)`, `[`getNodeValueAsBinaryStream`](XMLNode.md)`, `[`getNodeValueAsBinaryStream`](XMLNode.md)`, `[`getNodeValueAsCharacterStream`](XMLNode.md)`, `[`getNodeValueAsCharacterStream`](XMLNode.md)`, `[`getOwnerDocument`](XMLNode.md)`, `[`getParentNode`](XMLNode.md)`, `[`getPrefix`](XMLNode.md)`, `[`getPreviousSibling`](XMLNode.md)`, `[`getPrimitiveTypeId`](XMLNode.md)`, `[`getProperty`](XMLNode.md)`, `[`getSystemId`](XMLNode.md)`, `[`getXMLError`](XMLNode.md)`, `[`hasAttributes`](XMLNode.md)`, `[`hasChildNodes`](XMLNode.md)`, `[`hashCode`](XMLNode.md)`, `[`isDocumentFlag`](XMLNode.md)`, `[`isNodeFlag`](XMLNode.md)`, `[`isSupported`](XMLNode.md)`, `[`nodeValidity`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`readExternal`](XMLNode.md)`, `[`removeEventListener`](XMLNode.md)`, `[`reportSAXEvents`](XMLNode.md)`, `[`resetNodeFlag`](XMLNode.md)`, `[`selectNodes`](XMLNode.md)`, `[`selectNodes`](XMLNode.md)`, `[`selectSingleNode`](XMLNode.md)`, `[`selectSingleNode`](XMLNode.md)`, `[`setDebugInfo`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeValue`](XMLNode.md)`, `[`setNodeValueAsBinaryStream`](XMLNode.md)`, `[`setNodeValueAsBinaryStream`](XMLNode.md)`, `[`setNodeValueAsCharacterStream`](XMLNode.md)`, `[`setNodeValueAsCharacterStream`](XMLNode.md)`, `[`setPrefix`](XMLNode.md)`, `[`setProperty`](XMLNode.md)`, `[`transformNode`](XMLNode.md)`, `[`valueOf`](XMLNode.md)`, `[`valueOf`](XMLNode.md)`, `[`writeExternal`](XMLNode.md)`, `[`xdbGetNodeId`](XMLNode.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface java.io.Externalizable

      `readExternal, writeExternal`

<!-- -->

- - ### Method Detail

    - #### getChildNodes

          public NodeList getChildNodes()

      Gets a `NodeList` that contains all children of this node. If there are no children, this is a `NodeList` containing no nodes. The content of the returned `NodeList` is "live" in the sense that, for instance, changes to the children of the node object that it was created from are immediately reflected in the nodes returned by the `NodeList` accessors; it is not a static snapshot of the content of the node. This is true for every `NodeList`, including the ones returned by the `getElementsByTagName` method.
      Specified by:
      [`getChildNodes`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`getChildNodes`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Returns:
      The children of this node

    <!-- -->

    - #### getFirstChild

          public Node getFirstChild()

      Gets the first child of this node. If there is no such node, this returns `null`.
      Specified by:
      [`getFirstChild`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`getFirstChild`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Returns:
      The first child of this node

    <!-- -->

    - #### getLastChild

          public Node getLastChild()

      Gets the last child of this node. If there is no such node, this returns `null`.
      Specified by:
      [`getLastChild`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`getLastChild`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Returns:
      The last child of this node

    <!-- -->

    - #### appendChild

          public Node appendChild(Node newChildArg)
                           throws DOMException

      Adds the node `newChild` to the end of the list of children of this node. If the `newChild` is already in the tree, it is first removed.
      Specified by:
      [`appendChild`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`appendChild`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Parameters:
      `newChildArg` - The node to add. If it is a `DocumentFragment` object, the entire contents of the document fragment are moved into the child list of this node

      Returns:
      The node added.

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - HIERARCHY_REQUEST_ERR: Raised if this node is of a type that does not allow children of the type of the `newChild` node, or if the node to append is one of this node's ancestors.
      WRONG_DOCUMENT_ERR: Raised if `newChild` was created from a different document than the one that created this node.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.

    <!-- -->

    - #### removeChild

          public Node removeChild(Node oldChildArg)
                           throws DOMException

      Removes the child node indicated by `oldChildArg` from the list of children, and returns it.
      Specified by:
      [`removeChild`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`removeChild`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Parameters:
      `oldChildArg` - The node being removed.

      Returns:
      The node removed.

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.
      NOT_FOUND_ERR: Raised if `oldChildArg` is not a child of this node.

    <!-- -->

    - #### insertBefore

          public Node insertBefore(Node newChildArg,
                                   Node refChildArg)
                            throws DOMException

      Inserts the node `newChild` before the existing child node `refChild`. If `refChild` is `null`, insert `newChild` at the end of the list of children.
      If `newChild` is a `DocumentFragment` object, all of its children are inserted, in the same order, before `refChild`. If the `newChild` is already in the tree, it is first removed.
      Specified by:
      [`insertBefore`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`insertBefore`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Parameters:
      `newChildArg` - The node to insert.

      `refChildArg` - The reference node, i.e., the node before which the new node must be inserted.

      Returns:
      The node being inserted.

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - HIERARCHY_REQUEST_ERR: Raised if this node is of a type that does not allow children of the type of the `newChild` node, or if the node to insert is one of this node's ancestors.
      WRONG_DOCUMENT_ERR: Raised if `newChild` was created from a different document than the one that created this node.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.
      NOT_FOUND_ERR: Raised if `refChild` is not a child of this node.

    <!-- -->

    - #### replaceChild

          public Node replaceChild(Node newChildArg,
                                   Node oldChildArg)
                            throws DOMException

      Replaces the child node `oldChildArg` with `newChildArg` in the list of children, and returns the `oldChildArg` node. If the `newChildArg` is already in the tree, it is first removed.
      Specified by:
      [`replaceChild`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`replaceChild`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Parameters:
      `newChildArg` - The new node to put in the child list.

      `oldChildArg` - The node being replaced in the list.

      Returns:
      The node replaced.

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - HIERARCHY_REQUEST_ERR: Raised if this node is of a type that does not allow children of the type of the `newChildArg` node, or it the node to put in is one of this node's ancestors.
      WRONG_DOCUMENT_ERR: Raised if `newChildArg` was created from a different document than the one that created this node.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.
      NOT_FOUND_ERR: Raised if `oldChildArg` is not a child of this node.

    <!-- -->

    - #### normalize

          public void normalize()

      Puts all Text nodes in the full depth of the sub-tree underneath this Node, including attribute nodes, into "normal" form where only structure (e.g., elements, comments, processing instructions, CDATA sections, and entity references) separates Text nodes,i.e., there are neither adjacent Text nodes nor empty Text nodes. This can be used to ensure that the DOM view of a document is the same as if it were saved and re-loaded, and is useful when operations (such as XPointer lookups) that depend on a particular document tree structure are to be used. DOM 3.0 optional feature - this method does not support the parameter "normalize-characters=true" of the DOMConfiguration object, attached to the Node.ownerDocument.
      Specified by:
      [`normalize`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`normalize`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Since:
      DOM 2

    <!-- -->

    - #### addText

          public XMLNode addText(java.lang.String str)
                          throws XMLDOMException

      Adds text to this node, or appends str to the last child if the last child is a text node.
      Parameters:
      `str` - text to add

      Throws:
      [`XMLDOMException`](XMLDOMException.md) - if text can't be added to this node

    <!-- -->

    - #### addText

          public void addText(char[] ch,
                              int start,
                              int length)
                       throws XMLDOMException

      Adds text to this node, or appends str to the last child if the last child is a text node.
      Overrides:
      [`addText`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Parameters:
      `ch` - char array to add

      `start` - start index in the char array

      `length` - no of chars to be added

      Throws:
      [`XMLDOMException`](XMLDOMException.md) - if text can't be added to this node

    <!-- -->

    - #### getText

          public java.lang.String getText()

      Returns the non-marked-up text contained by this element. For text elements, this is the raw For elements with child nodes, this method traverses the entire subtree and appends the text for each terminal text element, effectively stripping out the XML markup for the subtree. For example, if the XML document contains the following: \<xmp\> \<AUTHOR\> \<FIRST\>William\</FIRST\> \<LAST\>Shakespeare\</LAST\> \</AUTHOR\> \</xmp\>
      `XMLDocument.getText` returns "William Shakespeare".

      Overrides:
      [`getText`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Returns:
      non-marked-up text contained bu this element

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

- **[Prev Class](XMLNotation.md)**
- **[Next Class](XMLObjectInputStream.md)**

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
