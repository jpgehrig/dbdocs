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

- **[Prev Class](NameList.md)**
- **[Next Class](NodeList.md)**

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

**org.w3c.dom**

## **Interface Node**

- **All Known Subinterfaces:**
  **[Attr](Attr.md), [CDATASection](CDATASection.md), [CharacterData](CharacterData.md), [Comment](Comment.md), [Document](Document.md), [DocumentFragment](DocumentFragment.md), [DocumentType](DocumentType.md), [Element](Element.md), [Entity](Entity.md), [EntityReference](EntityReference.md), [Notation](Notation.md), [ProcessingInstruction](ProcessingInstruction.md), [Text](Text.md)**

  <!-- -->

  **All Known Implementing Classes:**
  **[AttrDecl](../../../oracle/xml/parser/v2/AttrDecl.md), [DTD](../../../oracle/xml/parser/v2/DTD.md), [ElementDecl](../../../oracle/xml/parser/v2/ElementDecl.md), [XDBAttribute](../../../oracle/xdb/dom/XDBAttribute.md), [XDBBinaryDocument](../../../oracle/xdb/dom/XDBBinaryDocument.md), [XDBCData](../../../oracle/xdb/dom/XDBCData.md), [XDBCharData](../../../oracle/xdb/dom/XDBCharData.md), [XDBComment](../../../oracle/xdb/dom/XDBComment.md), [XDBDocFragment](../../../oracle/xdb/dom/XDBDocFragment.md), [XDBDocument](../../../oracle/xdb/dom/XDBDocument.md), [XDBDocumentType](../../../oracle/xdb/dom/XDBDocumentType.md), [XDBElement](../../../oracle/xdb/dom/XDBElement.md), [XDBEntity](../../../oracle/xdb/dom/XDBEntity.md), [XDBEntityReference](../../../oracle/xdb/dom/XDBEntityReference.md), [XDBNode](../../../oracle/xdb/dom/XDBNode.md), [XDBNotation](../../../oracle/xdb/dom/XDBNotation.md), [XDBProcInst](../../../oracle/xdb/dom/XDBProcInst.md), [XDBText](../../../oracle/xdb/dom/XDBText.md), [XMLAttr](../../../oracle/xml/parser/v2/XMLAttr.md), [XMLCDATA](../../../oracle/xml/parser/v2/XMLCDATA.md), [XMLComment](../../../oracle/xml/parser/v2/XMLComment.md), [XMLDeclPI](../../../oracle/xml/parser/v2/XMLDeclPI.md), [XMLDocument](../../../oracle/xml/parser/v2/XMLDocument.md), [XMLDocumentFragment](../../../oracle/xml/parser/v2/XMLDocumentFragment.md), [XMLElement](../../../oracle/xml/parser/v2/XMLElement.md), [XMLEntity](../../../oracle/xml/parser/v2/XMLEntity.md), [XMLEntityReference](../../../oracle/xml/parser/v2/XMLEntityReference.md), [XMLNode](../../../oracle/xml/parser/v2/XMLNode.md), [XMLNotation](../../../oracle/xml/parser/v2/XMLNotation.md), [XMLNSNode](../../../oracle/xml/parser/v2/XMLNSNode.md), [XMLPI](../../../oracle/xml/parser/v2/XMLPI.md), [XMLText](../../../oracle/xml/parser/v2/XMLText.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface Node

  **The `Node` interface is the primary datatype for the entire Document Object Model. It represents a single node in the document tree. While all objects implementing the `Node` interface expose methods for dealing with children, not all objects implementing the `Node` interface may have children. For example, `Text` nodes may not have children, and adding children to such nodes results in a `DOMException` being raised.**
  **The attributes `nodeName`, `nodeValue` and `attributes` are included as a mechanism to get at node information without casting down to the specific derived interface. In cases where there is no obvious mapping of these attributes for a specific `nodeType` (e.g., `nodeValue` for an `Element` or `attributes` for a `Comment` ), this returns `null`. Note that the specialized interfaces may contain additional and more convenient mechanisms to get and set the relevant information.**

  **See also the [Document Object Model (DOM) Level 2 Core Specification](http://www.w3.org/TR/2000/REC-DOM-Level-2-Core-20001113).**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description                                                   |
    |-------------------|-------------------------------------------------------------------------|
    | `static short`    | `ATTRIBUTE_NODE`<br>The node is an `Attr`.                              |
    | `static short`    | `CDATA_SECTION_NODE`<br>The node is a `CDATASection`.                   |
    | `static short`    | `COMMENT_NODE`<br>The node is a `Comment`.                              |
    | `static short`    | `DOCUMENT_FRAGMENT_NODE`<br>The node is a `DocumentFragment`.           |
    | `static short`    | `DOCUMENT_NODE`<br>The node is a `Document`.                            |
    | `static short`    | `DOCUMENT_TYPE_NODE`<br>The node is a `DocumentType`.                   |
    | `static short`    | `ELEMENT_NODE`<br>The node is an `Element`.                             |
    | `static short`    | `ENTITY_NODE`<br>The node is an `Entity`.                               |
    | `static short`    | `ENTITY_REFERENCE_NODE`<br>The node is an `EntityReference`.            |
    | `static short`    | `NOTATION_NODE`<br>The node is a `Notation`.                            |
    | `static short`    | `PROCESSING_INSTRUCTION_NODE`<br>The node is a `ProcessingInstruction`. |
    | `static short`    | `TEXT_NODE`<br>The node is a `Text` node.                               |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                 | Method and Description                                                                                                                                                                                                                                                                                                                                           |
    |-----------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `Node`                            | `appendChild``(Node newChild)`<br>Adds the node `newChild` to the end of the list of children of this node.                                                                                                                                                                                                                                                      |
    | `Node`                            | `cloneNode``(boolean deep)`<br>Returns a duplicate of this node, i.e., serves as a generic copy constructor for nodes.                                                                                                                                                                                                                                           |
    | [`NamedNodeMap`](NamedNodeMap.md) | `getAttributes``()`<br>A `NamedNodeMap` containing the attributes of this node (if it is an `Element`) or `null` otherwise.                                                                                                                                                                                                                                      |
    | [`NodeList`](NodeList.md)         | `getChildNodes``()`<br>A `NodeList` that contains all children of this node.                                                                                                                                                                                                                                                                                     |
    | `Node`                            | `getFirstChild``()`<br>The first child of this node.                                                                                                                                                                                                                                                                                                             |
    | `Node`                            | `getLastChild``()`<br>The last child of this node.                                                                                                                                                                                                                                                                                                               |
    | `java.lang.String`                | `getLocalName``()`<br>Returns the local part of the qualified name of this node.                                                                                                                                                                                                                                                                                 |
    | `java.lang.String`                | `getNamespaceURI``()`<br>The namespace URI of this node, or `null` if it is unspecified.                                                                                                                                                                                                                                                                         |
    | `Node`                            | `getNextSibling``()`<br>The node immediately following this node.                                                                                                                                                                                                                                                                                                |
    | `java.lang.String`                | `getNodeName``()`<br>The name of this node, depending on its type; see the table above.                                                                                                                                                                                                                                                                          |
    | `short`                           | `getNodeType``()`<br>A code representing the type of the underlying object, as defined above.                                                                                                                                                                                                                                                                    |
    | `java.lang.String`                | `getNodeValue``()`<br>The value of this node, depending on its type; see the table above.                                                                                                                                                                                                                                                                        |
    | [`Document`](Document.md)         | `getOwnerDocument``()`<br>The `Document` object associated with this node.                                                                                                                                                                                                                                                                                       |
    | `Node`                            | `getParentNode``()`<br>The parent of this node.                                                                                                                                                                                                                                                                                                                  |
    | `java.lang.String`                | `getPrefix``()`<br>The namespace prefix of this node, or `null` if it is unspecified.                                                                                                                                                                                                                                                                            |
    | `Node`                            | `getPreviousSibling``()`<br>The node immediately preceding this node.                                                                                                                                                                                                                                                                                            |
    | `boolean`                         | `hasAttributes``()`<br>Returns whether this node (if it is an element) has any attributes.                                                                                                                                                                                                                                                                       |
    | `boolean`                         | `hasChildNodes``()`<br>Returns whether this node has any children.                                                                                                                                                                                                                                                                                               |
    | `Node`                            | `insertBefore``(Node newChild, Node refChild)`<br>Inserts the node `newChild` before the existing child node `refChild`.                                                                                                                                                                                                                                         |
    | `boolean`                         | `isSupported``(java.lang.String feature, java.lang.String version)`<br>Tests whether the DOM implementation implements a specific feature and that feature is supported by this node.                                                                                                                                                                            |
    | `void`                            | `normalize``()`<br>Puts all `Text` nodes in the full depth of the sub-tree underneath this `Node`, including attribute nodes, into a "normal" form where only structure (e.g., elements, comments, processing instructions, CDATA sections, and entity references) separates `Text` nodes, i.e., there are neither adjacent `Text` nodes nor empty `Text` nodes. |
    | `Node`                            | `removeChild``(Node oldChild)`<br>Removes the child node indicated by `oldChild` from the list of children, and returns it.                                                                                                                                                                                                                                      |
    | `Node`                            | `replaceChild``(Node newChild, Node oldChild)`<br>Replaces the child node `oldChild` with `newChild` in the list of children, and returns the `oldChild` node.                                                                                                                                                                                                   |
    | `void`                            | `setNodeValue``(java.lang.String nodeValue)`                                                                                                                                                                                                                                                                                                                     |
    | `void`                            | `setPrefix``(java.lang.String prefix)`                                                                                                                                                                                                                                                                                                                           |

<!-- -->

- - ### Field Detail

    - #### ELEMENT_NODE

          static final short ELEMENT_NODE

      The node is an `Element`.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ATTRIBUTE_NODE

          static final short ATTRIBUTE_NODE

      The node is an `Attr`.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### TEXT_NODE

          static final short TEXT_NODE

      The node is a `Text` node.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CDATA_SECTION_NODE

          static final short CDATA_SECTION_NODE

      The node is a `CDATASection`.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ENTITY_REFERENCE_NODE

          static final short ENTITY_REFERENCE_NODE

      The node is an `EntityReference`.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ENTITY_NODE

          static final short ENTITY_NODE

      The node is an `Entity`.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PROCESSING_INSTRUCTION_NODE

          static final short PROCESSING_INSTRUCTION_NODE

      The node is a `ProcessingInstruction`.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### COMMENT_NODE

          static final short COMMENT_NODE

      The node is a `Comment`.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DOCUMENT_NODE

          static final short DOCUMENT_NODE

      The node is a `Document`.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DOCUMENT_TYPE_NODE

          static final short DOCUMENT_TYPE_NODE

      The node is a `DocumentType`.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DOCUMENT_FRAGMENT_NODE

          static final short DOCUMENT_FRAGMENT_NODE

      The node is a `DocumentFragment`.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### NOTATION_NODE

          static final short NOTATION_NODE

      The node is a `Notation`.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getNodeName

          java.lang.String getNodeName()

      The name of this node, depending on its type; see the table above.

    <!-- -->

    - #### getNodeValue

          java.lang.String getNodeValue()
                                 throws DOMException

      The value of this node, depending on its type; see the table above. When it is defined to be `null`, setting it has no effect.
      Throws:
      [`DOMException`](DOMException.md) - NO_MODIFICATION_ALLOWED_ERR: Raised when the node is readonly.

      [`DOMException`](DOMException.md) - DOMSTRING_SIZE_ERR: Raised when it would return more characters than fit in a `DOMString` variable on the implementation platform.

    <!-- -->

    - #### setNodeValue

          void setNodeValue(java.lang.String nodeValue)
                     throws DOMException

      Throws:
      [`DOMException`](DOMException.md)

    <!-- -->

    - #### getNodeType

          short getNodeType()

      A code representing the type of the underlying object, as defined above.

    <!-- -->

    - #### getParentNode

          Node getParentNode()

      The parent of this node. All nodes, except `Attr`, `Document`, `DocumentFragment`, `Entity`, and `Notation` may have a parent. However, if a node has just been created and not yet added to the tree, or if it has been removed from the tree, this is `null`.

    <!-- -->

    - #### getChildNodes

          NodeList getChildNodes()

      A `NodeList` that contains all children of this node. If there are no children, this is a `NodeList` containing no nodes.

    <!-- -->

    - #### getFirstChild

          Node getFirstChild()

      The first child of this node. If there is no such node, this returns `null`.

    <!-- -->

    - #### getLastChild

          Node getLastChild()

      The last child of this node. If there is no such node, this returns `null`.

    <!-- -->

    - #### getPreviousSibling

          Node getPreviousSibling()

      The node immediately preceding this node. If there is no such node, this returns `null`.

    <!-- -->

    - #### getNextSibling

          Node getNextSibling()

      The node immediately following this node. If there is no such node, this returns `null`.

    <!-- -->

    - #### getAttributes

          NamedNodeMap getAttributes()

      A `NamedNodeMap` containing the attributes of this node (if it is an `Element`) or `null` otherwise.

    <!-- -->

    - #### getOwnerDocument

          Document getOwnerDocument()

      The `Document` object associated with this node. This is also the `Document` object used to create new nodes. When this node is a `Document` or a `DocumentType` which is not used with any `Document` yet, this is `null`.

    <!-- -->

    - #### insertBefore

          Node insertBefore(Node newChild,
                            Node refChild)
                     throws DOMException

      Inserts the node `newChild` before the existing child node `refChild`. If `refChild` is `null`, insert `newChild` at the end of the list of children.
      If `newChild` is a `DocumentFragment` object, all of its children are inserted, in the same order, before `refChild`. If the `newChild` is already in the tree, it is first removed.
      Parameters:
      `newChild` - The node to insert.

      `refChild` - The reference node, i.e., the node before which the new node must be inserted.

      Returns:
      The node being inserted.

      Throws:
      [`DOMException`](DOMException.md) - HIERARCHY_REQUEST_ERR: Raised if this node is of a type that does not allow children of the type of the `newChild` node, or if the node to insert is one of this node's ancestors.
      WRONG_DOCUMENT_ERR: Raised if `newChild` was created from a different document than the one that created this node.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly or if the parent of the node being inserted is readonly.
      NOT_FOUND_ERR: Raised if `refChild` is not a child of this node.

    <!-- -->

    - #### replaceChild

          Node replaceChild(Node newChild,
                            Node oldChild)
                     throws DOMException

      Replaces the child node `oldChild` with `newChild` in the list of children, and returns the `oldChild` node.
      If `newChild` is a `DocumentFragment` object, `oldChild` is replaced by all of the `DocumentFragment` children, which are inserted in the same order. If the `newChild` is already in the tree, it is first removed.
      Parameters:
      `newChild` - The new node to put in the child list.

      `oldChild` - The node being replaced in the list.

      Returns:
      The node replaced.

      Throws:
      [`DOMException`](DOMException.md) - HIERARCHY_REQUEST_ERR: Raised if this node is of a type that does not allow children of the type of the `newChild` node, or if the node to put in is one of this node's ancestors.
      WRONG_DOCUMENT_ERR: Raised if `newChild` was created from a different document than the one that created this node.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node or the parent of the new node is readonly.
      NOT_FOUND_ERR: Raised if `oldChild` is not a child of this node.

    <!-- -->

    - #### removeChild

          Node removeChild(Node oldChild)
                    throws DOMException

      Removes the child node indicated by `oldChild` from the list of children, and returns it.
      Parameters:
      `oldChild` - The node being removed.

      Returns:
      The node removed.

      Throws:
      [`DOMException`](DOMException.md) - NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.
      NOT_FOUND_ERR: Raised if `oldChild` is not a child of this node.

    <!-- -->

    - #### appendChild

          Node appendChild(Node newChild)
                    throws DOMException

      Adds the node `newChild` to the end of the list of children of this node. If the `newChild` is already in the tree, it is first removed.
      Parameters:
      `newChild` - The node to add.If it is a `DocumentFragment` object, the entire contents of the document fragment are moved into the child list of this node

      Returns:
      The node added.

      Throws:
      [`DOMException`](DOMException.md) - HIERARCHY_REQUEST_ERR: Raised if this node is of a type that does not allow children of the type of the `newChild` node, or if the node to append is one of this node's ancestors.
      WRONG_DOCUMENT_ERR: Raised if `newChild` was created from a different document than the one that created this node.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.

    <!-- -->

    - #### hasChildNodes

          boolean hasChildNodes()

      Returns whether this node has any children.
      Returns:
      `true` if this node has any children, `false` otherwise.

    <!-- -->

    - #### cloneNode

          Node cloneNode(boolean deep)

      Returns a duplicate of this node, i.e., serves as a generic copy constructor for nodes. The duplicate node has no parent; ( `parentNode` is `null`.).
      Cloning an `Element` copies all attributes and their values, including those generated by the XML processor to represent defaulted attributes, but this method does not copy any text it contains unless it is a deep clone, since the text is contained in a child `Text` node. Cloning an `Attribute` directly, as opposed to be cloned as part of an `Element` cloning operation, returns a specified attribute ( `specified` is `true`). Cloning any other type of node simply returns a copy of this node.
      Note that cloning an immutable subtree results in a mutable copy, but the children of an `EntityReference` clone are readonly . In addition, clones of unspecified `Attr` nodes are specified. And, cloning `Document`, `DocumentType`, `Entity`, and `Notation` nodes is implementation dependent.
      Parameters:
      `deep` - If `true`, recursively clone the subtree under the specified node; if `false`, clone only the node itself (and its attributes, if it is an `Element`).

      Returns:
      The duplicate node.

    <!-- -->

    - #### normalize

          void normalize()

      Puts all `Text` nodes in the full depth of the sub-tree underneath this `Node`, including attribute nodes, into a "normal" form where only structure (e.g., elements, comments, processing instructions, CDATA sections, and entity references) separates `Text` nodes, i.e., there are neither adjacent `Text` nodes nor empty `Text` nodes. This can be used to ensure that the DOM view of a document is the same as if it were saved and re-loaded, and is useful when operations (such as XPointer lookups) that depend on a particular document tree structure are to be used.In cases where the document contains `CDATASections`, the normalize operation alone may not be sufficient, since XPointers do not differentiate between `Text` nodes and `CDATASection` nodes.

    <!-- -->

    - #### isSupported

          boolean isSupported(java.lang.String feature,
                              java.lang.String version)

      Tests whether the DOM implementation implements a specific feature and that feature is supported by this node.
      Parameters:
      `feature` - The name of the feature to test. This is the same name which can be passed to the method `hasFeature` on `DOMImplementation`.

      `version` - This is the version number of the feature to test. In Level 2, version 1, this is the string "2.0". If the version is not specified, supporting any version of the feature will cause the method to return `true`.

      Returns:
      Returns `true` if the specified feature is supported on this node, `false` otherwise.

      Since:
      DOM Level 2

    <!-- -->

    - #### getNamespaceURI

          java.lang.String getNamespaceURI()

      The namespace URI of this node, or `null` if it is unspecified.
      This is not a computed value that is the result of a namespace lookup based on an examination of the namespace declarations in scope. It is merely the namespace URI given at creation time.
      For nodes of any type other than `ELEMENT_NODE` and `ATTRIBUTE_NODE` and nodes created with a DOM Level 1 method, such as `createElement` from the `Document` interface, this is always `null`.Per the Namespaces in XML Specification an attribute does not inherit its namespace from the element it is attached to. If an attribute is not explicitly given a namespace, it simply has no namespace.
      Since:
      DOM Level 2

    <!-- -->

    - #### getPrefix

          java.lang.String getPrefix()

      The namespace prefix of this node, or `null` if it is unspecified.
      Note that setting this attribute, when permitted, changes the `nodeName` attribute, which holds the qualified name, as well as the `tagName` and `name` attributes of the `Element` and `Attr` interfaces, when applicable.
      Note also that changing the prefix of an attribute that is known to have a default value, does not make a new attribute with the default value and the original prefix appear, since the `namespaceURI` and `localName` do not change.
      For nodes of any type other than `ELEMENT_NODE` and `ATTRIBUTE_NODE` and nodes created with a DOM Level 1 method, such as `createElement` from the `Document` interface, this is always `null`.
      Throws:
      [`DOMException`](DOMException.md) - INVALID_CHARACTER_ERR: Raised if the specified prefix contains an illegal character.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.
      NAMESPACE_ERR: Raised if the specified `prefix` is malformed, if the `namespaceURI` of this node is `null`, if the specified prefix is "xml" and the `namespaceURI` of this node is different from " http://www.w3.org/XML/1998/namespace", if this node is an attribute and the specified prefix is "xmlns" and the `namespaceURI` of this node is different from " http://www.w3.org/2000/xmlns/", or if this node is an attribute and the `qualifiedName` of this node is "xmlns" .

      Since:
      DOM Level 2

    <!-- -->

    - #### setPrefix

          void setPrefix(java.lang.String prefix)
                  throws DOMException

      Throws:
      [`DOMException`](DOMException.md)

    <!-- -->

    - #### getLocalName

          java.lang.String getLocalName()

      Returns the local part of the qualified name of this node.
      For nodes of any type other than `ELEMENT_NODE` and `ATTRIBUTE_NODE` and nodes created with a DOM Level 1 method, such as `createElement` from the `Document` interface, this is always `null`.
      Since:
      DOM Level 2

    <!-- -->

    - #### hasAttributes

          boolean hasAttributes()

      Returns whether this node (if it is an element) has any attributes.
      Returns:
      `true` if this node has any attributes, `false` otherwise.

      Since:
      DOM Level 2

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

- **[Prev Class](NameList.md)**
- **[Next Class](NodeList.md)**

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

**Copyright © 2000 [W3C](http://www.w3.org/)<sup>®</sup> ([MIT](http://www.csail.mit.edu/), [INRIA](http://www.inria.fr/), [Keio](http://www.keio.ac.jp/)), All Rights Reserved. W3C [liability](http://www.w3.org/Consortium/Legal/2002/ipr-notice-20021231), [trademark](http://www.w3.org/Consortium/Legal/2002/ipr-notice-20021231), [document use](http://www.w3.org/Consortium/Legal/copyright-documents-19990405) and [software licensing](http://www.w3.org/Consortium/Legal/copyright-software-19980720) rules apply. This document has been reviewed by W3C Members and other interested parties and has been endorsed by the Director as a [W3C Recommendation](http://www.w3.org/Consortium/Process/Process-19991111/tr.html#RecsW3C).**
