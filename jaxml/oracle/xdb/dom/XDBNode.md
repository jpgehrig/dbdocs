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

- **[Prev Class](XDBNamedNodeMap.md)**
- **[Next Class](XDBNodeList.md)**

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

## **Class XDBNode**

- **java.lang.Object**

- - **oracle.xdb.dom.XDBNode**

<!-- -->

- **All Implemented Interfaces:**
  **[Node](../../../org/w3c/dom/Node.md)**

  <!-- -->

  **Direct Known Subclasses:**
  **[XDBAttribute](XDBAttribute.md), [XDBCharData](XDBCharData.md), [XDBDocFragment](XDBDocFragment.md), [XDBDocument](XDBDocument.md), [XDBDocumentType](XDBDocumentType.md), [XDBElement](XDBElement.md), [XDBEntity](XDBEntity.md), [XDBEntityReference](XDBEntityReference.md), [XDBNotation](XDBNotation.md), [XDBProcInst](XDBProcInst.md)**

  ------------------------------------------------------------------------

  **Deprecated. **
  **as of Oracle Database 11g release 1, use oracle.xml.parser.v2.XMLNode**
  **
  **

      public abstract class XDBNode
      extends java.lang.Object
      implements Node

  **This class implements the W3C DOM Node interface for interacting with XOBs.**

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

    | Modifier and Type                                      | Method and Description                                                                                                                                                                                                                                         |
    |--------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Node`](../../../org/w3c/dom/Node.md)                 | `appendChild``(`[`Node`](../../../org/w3c/dom/Node.md)` arg)`<br>Deprecated. <br>append the new child to the end of the child list; must be overriden by sub classes which support this method.                                                                |
    | [`Node`](../../../org/w3c/dom/Node.md)                 | `cloneNode``(boolean deep)`<br>Deprecated. <br>Returns the copy of the node. the parent of the clone is set to null                                                                                                                                            |
    | `void`                                                 | `close``()`<br>Deprecated. <br>                                                                                                                                                                                                                                |
    | `short`                                                | `compareDocumentPosition``(`[`Node`](../../../org/w3c/dom/Node.md)` other)`<br>Deprecated. <br>                                                                                                                                                                |
    | `boolean`                                              | `equals``(java.lang.Object obj)`<br>Deprecated. <br>Tests to see if the given object refers to the same node in the DOM tree as this.                                                                                                                          |
    | `void`                                                 | `finalize``()`<br>Deprecated. <br>                                                                                                                                                                                                                             |
    | [`NamedNodeMap`](../../../org/w3c/dom/NamedNodeMap.md) | `getAttributes``()`<br>Deprecated. <br>Returns the attributes of the node.                                                                                                                                                                                     |
    | `java.lang.String`                                     | `getBaseURI``()`<br>Deprecated. <br>                                                                                                                                                                                                                           |
    | [`NodeList`](../../../org/w3c/dom/NodeList.md)         | `getChildNodes``()`<br>Deprecated. <br>Returns the nodelist of child nodes.                                                                                                                                                                                    |
    | `java.lang.String`                                     | `getExpandedName``()`<br>Deprecated. <br>get the expanded name of the node                                                                                                                                                                                     |
    | `java.lang.Object`                                     | `getFeature``(java.lang.String feature, java.lang.String version)`<br>Deprecated. <br>                                                                                                                                                                         |
    | [`Node`](../../../org/w3c/dom/Node.md)                 | `getFirstChild``()`<br>Deprecated. <br>Returns the first child of the node. must be overriden derived classes which support this                                                                                                                               |
    | `java.io.InputStream`                                  | `getInputStream``()`<br>Deprecated. <br>Get an InputStream from the node, applications can read XML data from the stream                                                                                                                                       |
    | [`Node`](../../../org/w3c/dom/Node.md)                 | `getLastChild``()`<br>Deprecated. <br>Returns the last child of the node. must be overriden derived classes which support this                                                                                                                                 |
    | `java.lang.String`                                     | `getLocalName``()`<br>Deprecated. <br>get the local name of the node                                                                                                                                                                                           |
    | `java.lang.String`                                     | `getNamespaceURI``()`<br>Deprecated. <br>The namespace URI of this node, or `null` if it is unspecified.                                                                                                                                                       |
    | [`Node`](../../../org/w3c/dom/Node.md)                 | `getNextSibling``()`<br>Deprecated. <br>Returns the next sibling of the node. must be overriden derived classes which support this                                                                                                                             |
    | `java.lang.String`                                     | `getNodeName``()`<br>Deprecated. <br>get the name of the node; sub classes need to override this method.                                                                                                                                                       |
    | `short`                                                | `getNodeType``()`<br>Deprecated. <br>Returns the type of the node.                                                                                                                                                                                             |
    | `java.lang.String`                                     | `getNodeValue``()`<br>Deprecated. <br>get the value of the node; sub classes which need to return valid values should override this method.                                                                                                                    |
    | [`Document`](../../../org/w3c/dom/Document.md)         | `getOwnerDocument``()`<br>Deprecated. <br>Returns the owner document of the node.                                                                                                                                                                              |
    | [`Node`](../../../org/w3c/dom/Node.md)                 | `getParentNode``()`<br>Deprecated. <br>Returns the parent of the node.                                                                                                                                                                                         |
    | `java.lang.String`                                     | `getPrefix``()`<br>Deprecated. <br>The namespace prefix of this node, or `null` if it is unspecified.                                                                                                                                                          |
    | [`Node`](../../../org/w3c/dom/Node.md)                 | `getPreviousSibling``()`<br>Deprecated. <br>Returns the previous sibling of the node. must be overriden derived classes which support this                                                                                                                     |
    | `int`                                                  | `getPrimitiveType``()`<br>Deprecated. <br>get the primitive type of a node                                                                                                                                                                                     |
    | `java.lang.String`                                     | `getQualifiedName``()`<br>Deprecated. <br>get the qualified name of the node                                                                                                                                                                                   |
    | [`Node`](../../../org/w3c/dom/Node.md)                 | `getSchemaNode``()`<br>Deprecated. <br>                                                                                                                                                                                                                        |
    | `java.lang.String`                                     | `getTextContent``()`<br>Deprecated. <br>                                                                                                                                                                                                                       |
    | `java.lang.Object`                                     | `getUserData``(java.lang.String key)`<br>Deprecated. <br>                                                                                                                                                                                                      |
    | `boolean`                                              | `hasAttributes``()`<br>Deprecated. <br>tests if the node has attributes.                                                                                                                                                                                       |
    | `boolean`                                              | `hasChildNodes``()`<br>Deprecated. <br>determines if the node has any children; sub classes must override this.                                                                                                                                                |
    | `int`                                                  | `hashCode``()`<br>Deprecated. <br>                                                                                                                                                                                                                             |
    | [`Node`](../../../org/w3c/dom/Node.md)                 | `insertBefore``(`[`Node`](../../../org/w3c/dom/Node.md)` newChild, `[`Node`](../../../org/w3c/dom/Node.md)` refChild)`<br>Deprecated. <br>Insert the newchild before the refchild; if refchild is null insert the newchild at the end of the child list.       |
    | `boolean`                                              | `isDefaultNamespace``(java.lang.String namespaceURI)`<br>Deprecated. <br>                                                                                                                                                                                      |
    | `boolean`                                              | `isEqualNode``(`[`Node`](../../../org/w3c/dom/Node.md)` arg)`<br>Deprecated. <br>                                                                                                                                                                              |
    | `boolean`                                              | `isNilled``()`<br>Deprecated. <br>tests if xsi:nil is set for the node                                                                                                                                                                                         |
    | `boolean`                                              | `isSameNode``(`[`Node`](../../../org/w3c/dom/Node.md)` other)`<br>Deprecated. <br>                                                                                                                                                                             |
    | `boolean`                                              | `isSchemaBased``()`<br>Deprecated. <br>tests if the node is schema-based or not                                                                                                                                                                                |
    | `boolean`                                              | `isSupported``(java.lang.String feature, java.lang.String version)`<br>Deprecated. <br>test if a feature is supported in the given version                                                                                                                     |
    | `java.lang.String`                                     | `lookupNamespaceURI``(java.lang.String prefix)`<br>Deprecated. <br>                                                                                                                                                                                            |
    | `java.lang.String`                                     | `lookupPrefix``(java.lang.String namespaceURI)`<br>Deprecated. <br>                                                                                                                                                                                            |
    | `void`                                                 | `normalize``()`<br>Deprecated. <br>normalize                                                                                                                                                                                                                   |
    | [`Node`](../../../org/w3c/dom/Node.md)                 | `removeChild``(`[`Node`](../../../org/w3c/dom/Node.md)` arg)`<br>Deprecated. <br>remove the child from the childlist; must be overriden by sub classes which support this method.                                                                              |
    | [`Node`](../../../org/w3c/dom/Node.md)                 | `replaceChild``(`[`Node`](../../../org/w3c/dom/Node.md)` newChild, `[`Node`](../../../org/w3c/dom/Node.md)` oldChild)`<br>Deprecated. <br>replace the oldchild in the childlist with the newchild; must be overriden by sub classes which support this method. |
    | `void`                                                 | `setNodeValue``(java.lang.String value)`<br>Deprecated. <br>set the value of the node                                                                                                                                                                          |
    | `void`                                                 | `setNodeXob``(int propnum)`<br>Deprecated. <br>Set the Xob state based on the owner document                                                                                                                                                                   |
    | `void`                                                 | `setOwner``(`[`XDBDocument`](XDBDocument.md)` owner)`<br>Deprecated. <br>                                                                                                                                                                                      |
    | `void`                                                 | `setPrefix``(java.lang.String prefix)`<br>Deprecated. <br>                                                                                                                                                                                                     |
    | `void`                                                 | `setTextContent``(java.lang.String textContent)`<br>Deprecated. <br>                                                                                                                                                                                           |
    | `java.lang.Object`                                     | `setUserData``(java.lang.String key, java.lang.Object data, `[`UserDataHandler`](../../../org/w3c/dom/UserDataHandler.md)` handler)`<br>Deprecated. <br>                                                                                                       |
    | `void`                                                 | `setXobCstate``(long xob)`<br>Deprecated. <br>                                                                                                                                                                                                                 |
    | `long`                                                 | `toCState``()`<br>Deprecated. <br>Returns a long integer, which is actually the pointer to the underlying qmxob struct.                                                                                                                                        |
    | `java.lang.String`                                     | `toString``()`<br>Deprecated. <br>                                                                                                                                                                                                                             |
    | `void`                                                 | `write``(java.io.OutputStream s, java.lang.String charEncoding, short indent)`<br>Deprecated. <br>Writes the XML for this Node (and all subnodes) to an OutputStream.                                                                                          |
    | `void`                                                 | `writeToOutputStream``(java.io.OutputStream os)`<br>Deprecated. <br>Write the contents of the node to an OutputStream.                                                                                                                                         |

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getNodeName

          public java.lang.String getNodeName()

      Deprecated. 
      get the name of the node; sub classes need to override this method.
      Specified by:
      [`getNodeName`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

      Returns:
      the node name string, always null for this node.

    <!-- -->

    - #### getNodeType

          public short getNodeType()

      Deprecated. 
      Returns the type of the node. The node type i.e. document, element, etc. is defined in org.w3c.dom.Node
      Specified by:
      [`getNodeType`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

      Returns:
      the type of the Node

    <!-- -->

    - #### getNodeValue

          public java.lang.String getNodeValue()

      Deprecated. 
      get the value of the node; sub classes which need to return valid values should override this method.
      Specified by:
      [`getNodeValue`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

      Returns:
      the node value string, always null for this node.

    <!-- -->

    - #### setNodeValue

          public void setNodeValue(java.lang.String value)
                            throws DOMException

      Deprecated. 
      set the value of the node
      Specified by:
      [`setNodeValue`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md)

    <!-- -->

    - #### getParentNode

          public Node getParentNode()

      Deprecated. 
      Returns the parent of the node. Must be overridden by sub classes which are expected to support this.
      Specified by:
      [`getParentNode`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

      Returns:
      the parent node

    <!-- -->

    - #### getSchemaNode

          public Node getSchemaNode()

      Deprecated. 

    <!-- -->

    - #### getChildNodes

          public NodeList getChildNodes()

      Deprecated. 
      Returns the nodelist of child nodes. Sub classes must overrider this to return the appropriate child list.
      Specified by:
      [`getChildNodes`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

      Returns:
      the child Nodelist of the node.

    <!-- -->

    - #### getLocalName

          public java.lang.String getLocalName()

      Deprecated. 
      get the local name of the node
      Specified by:
      [`getLocalName`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

      Returns:
      null for anything other than attribute and elem

    <!-- -->

    - #### getPrefix

          public java.lang.String getPrefix()

      Deprecated. 
      Description copied from interface: [`Node`](../../../org/w3c/dom/Node.md)
      The namespace prefix of this node, or `null` if it is unspecified.
      Note that setting this attribute, when permitted, changes the `nodeName` attribute, which holds the qualified name, as well as the `tagName` and `name` attributes of the `Element` and `Attr` interfaces, when applicable.
      Note also that changing the prefix of an attribute that is known to have a default value, does not make a new attribute with the default value and the original prefix appear, since the `namespaceURI` and `localName` do not change.
      For nodes of any type other than `ELEMENT_NODE` and `ATTRIBUTE_NODE` and nodes created with a DOM Level 1 method, such as `createElement` from the `Document` interface, this is always `null`.
      Specified by:
      [`getPrefix`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

    <!-- -->

    - #### setPrefix

          public void setPrefix(java.lang.String prefix)
                         throws DOMException

      Deprecated. 
      Specified by:
      [`setPrefix`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md)

    <!-- -->

    - #### getNamespaceURI

          public java.lang.String getNamespaceURI()

      Deprecated. 
      Description copied from interface: [`Node`](../../../org/w3c/dom/Node.md)
      The namespace URI of this node, or `null` if it is unspecified.
      This is not a computed value that is the result of a namespace lookup based on an examination of the namespace declarations in scope. It is merely the namespace URI given at creation time.
      For nodes of any type other than `ELEMENT_NODE` and `ATTRIBUTE_NODE` and nodes created with a DOM Level 1 method, such as `createElement` from the `Document` interface, this is always `null`.Per the Namespaces in XML Specification an attribute does not inherit its namespace from the element it is attached to. If an attribute is not explicitly given a namespace, it simply has no namespace.
      Specified by:
      [`getNamespaceURI`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

    <!-- -->

    - #### getPreviousSibling

          public Node getPreviousSibling()

      Deprecated. 
      Returns the previous sibling of the node. must be overriden derived classes which support this
      Specified by:
      [`getPreviousSibling`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

      Returns:
      the previous node

    <!-- -->

    - #### getNextSibling

          public Node getNextSibling()

      Deprecated. 
      Returns the next sibling of the node. must be overriden derived classes which support this
      Specified by:
      [`getNextSibling`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

      Returns:
      the next node

    <!-- -->

    - #### getFirstChild

          public Node getFirstChild()

      Deprecated. 
      Returns the first child of the node. must be overriden derived classes which support this
      Specified by:
      [`getFirstChild`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

      Returns:
      the first child node

    <!-- -->

    - #### getLastChild

          public Node getLastChild()

      Deprecated. 
      Returns the last child of the node. must be overriden derived classes which support this
      Specified by:
      [`getLastChild`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

      Returns:
      the last child node

    <!-- -->

    - #### getAttributes

          public NamedNodeMap getAttributes()

      Deprecated. 
      Returns the attributes of the node. If The node is not an element, returns null
      Specified by:
      [`getAttributes`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

      Returns:
      the attribute map of the node.

    <!-- -->

    - #### hasAttributes

          public boolean hasAttributes()

      Deprecated. 
      tests if the node has attributes.
      Specified by:
      [`hasAttributes`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

      Returns:
      true or false.

    <!-- -->

    - #### getOwnerDocument

          public Document getOwnerDocument()

      Deprecated. 
      Returns the owner document of the node.
      Specified by:
      [`getOwnerDocument`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

      Returns:
      the document associated with the node.

    <!-- -->

    - #### insertBefore

          public Node insertBefore(Node newChild,
                                   Node refChild)
                            throws DOMException

      Deprecated. 
      Insert the newchild before the refchild; if refchild is null insert the newchild at the end of the child list. This method should be overriden by subclasses which support it.
      Specified by:
      [`insertBefore`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

      Parameters:
      `newChild` - The node to insert.

      `refChild` - The reference node, i.e., the node before which the new node must be inserted.

      Returns:
      the new child.

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md) - HIERARCHY_REQUEST_ERR: Raised if this node is of a type that does not allow children of the type of the `newChild` node, or if the node to insert is one of this node's ancestors.
      WRONG_DOCUMENT_ERR: Raised if `newChild` was created from a different document than the one that created this node.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly or if the parent of the node being inserted is readonly.
      NOT_FOUND_ERR: Raised if `refChild` is not a child of this node.

    <!-- -->

    - #### removeChild

          public Node removeChild(Node arg)
                           throws DOMException

      Deprecated. 
      remove the child from the childlist; must be overriden by sub classes which support this method.
      Specified by:
      [`removeChild`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

      Parameters:
      `arg` - The node being removed.

      Returns:
      the node being removed.

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md) - NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.
      NOT_FOUND_ERR: Raised if `oldChild` is not a child of this node.

    <!-- -->

    - #### replaceChild

          public Node replaceChild(Node newChild,
                                   Node oldChild)
                            throws DOMException

      Deprecated. 
      replace the oldchild in the childlist with the newchild; must be overriden by sub classes which support this method.
      Specified by:
      [`replaceChild`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

      Parameters:
      `newChild` - The new node to put in the child list.

      `oldChild` - The node being replaced in the list.

      Returns:
      the node being replaced.

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md) - HIERARCHY_REQUEST_ERR: Raised if this node is of a type that does not allow children of the type of the `newChild` node, or if the node to put in is one of this node's ancestors.
      WRONG_DOCUMENT_ERR: Raised if `newChild` was created from a different document than the one that created this node.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node or the parent of the new node is readonly.
      NOT_FOUND_ERR: Raised if `oldChild` is not a child of this node.

    <!-- -->

    - #### appendChild

          public Node appendChild(Node arg)
                           throws DOMException

      Deprecated. 
      append the new child to the end of the child list; must be overriden by sub classes which support this method.
      Specified by:
      [`appendChild`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

      Parameters:
      `arg` - The node to add.If it is a `DocumentFragment` object, the entire contents of the document fragment are moved into the child list of this node

      Returns:
      the node being appended.

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md) - HIERARCHY_REQUEST_ERR: Raised if this node is of a type that does not allow children of the type of the `newChild` node, or if the node to append is one of this node's ancestors.
      WRONG_DOCUMENT_ERR: Raised if `newChild` was created from a different document than the one that created this node.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.

    <!-- -->

    - #### hasChildNodes

          public boolean hasChildNodes()

      Deprecated. 
      determines if the node has any children; sub classes must override this.
      Specified by:
      [`hasChildNodes`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

      Returns:
      true if node has child nodes

    <!-- -->

    - #### cloneNode

          public Node cloneNode(boolean deep)

      Deprecated. 
      Returns the copy of the node. the parent of the clone is set to null
      Specified by:
      [`cloneNode`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

      Parameters:
      `deep` - If `true`, recursively clone the subtree under the specified node; if `false`, clone only the node itself (and its attributes, if it is an `Element`).

      Returns:
      the new node

    <!-- -->

    - #### normalize

          public void normalize()

      Deprecated. 
      normalize
      Specified by:
      [`normalize`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

    <!-- -->

    - #### isSupported

          public boolean isSupported(java.lang.String feature,
                                     java.lang.String version)

      Deprecated. 
      test if a feature is supported in the given version
      Specified by:
      [`isSupported`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

      Parameters:
      `feature` - The name of the feature to test. This is the same name which can be passed to the method `hasFeature` on `DOMImplementation`.

      `version` - This is the version number of the feature to test. In Level 2, version 1, this is the string "2.0". If the version is not specified, supporting any version of the feature will cause the method to return `true`.

      Returns:
      true or false

    <!-- -->

    - #### isSchemaBased

          public boolean isSchemaBased()

      Deprecated. 
      tests if the node is schema-based or not
      Returns:
      true or false

    <!-- -->

    - #### isNilled

          public boolean isNilled()

      Deprecated. 
      tests if xsi:nil is set for the node
      Returns:
      true or false

    <!-- -->

    - #### getPrimitiveType

          public int getPrimitiveType()

      Deprecated. 
      get the primitive type of a node
      Returns:
      xquery primitive type id

    <!-- -->

    - #### equals

          public boolean equals(java.lang.Object obj)

      Deprecated. 
      Tests to see if the given object refers to the same node in the DOM tree as this. If obj is not an instance of XDBNode (or one of its descendents) this clearly this is always false. Example: If we have some node n, then n.getFirstChild() == n.getFirstChild() will evaluate to false, because a new Java object is instantiated with each call. However, since they do refer to the same node in the document tree, n.getFirstChild().equals(n.getFirstChild()) will evaluate to true.
      Overrides:
      `equals` in class `java.lang.Object`

    <!-- -->

    - #### toCState

          public long toCState()

      Deprecated. 
      Returns a long integer, which is actually the pointer to the underlying qmxob struct. This method really should not be public, and is only a temporary workaround.
      Returns:
      the pointer to the underlying qmxob struct, typecast to a long

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Deprecated. 
      Overrides:
      `toString` in class `java.lang.Object`

    <!-- -->

    - #### write

          public void write(java.io.OutputStream s,
                            java.lang.String charEncoding,
                            short indent)
                     throws java.io.IOException

      Deprecated. 
      Writes the XML for this Node (and all subnodes) to an OutputStream. If the OutputStream is a ServletOutputStream, the servlet output is committed and the data is written using a native stream mechanism.
      Parameters:
      `s` - The stream to write the output to

      `charEncoding` - The IANA char code (e.g. "ISO-8859")

      `indent` - Number of chars to indent nested elements

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### close

          public void close()

      Deprecated. 

    <!-- -->

    - #### finalize

          public void finalize()
                        throws java.lang.Throwable

      Deprecated. 
      Overrides:
      `finalize` in class `java.lang.Object`

      Throws:
      `java.lang.Throwable`

    <!-- -->

    - #### getQualifiedName

          public java.lang.String getQualifiedName()

      Deprecated. 
      get the qualified name of the node
      Returns:
      the qualified node name string

    <!-- -->

    - #### getExpandedName

          public java.lang.String getExpandedName()

      Deprecated. 
      get the expanded name of the node
      Returns:
      the expanded node name string

    <!-- -->

    - #### setOwner

          public void setOwner(XDBDocument owner)

      Deprecated. 

    <!-- -->

    - #### setXobCstate

          public void setXobCstate(long xob)

      Deprecated. 

    <!-- -->

    - #### setNodeXob

          public void setNodeXob(int propnum)

      Deprecated. 
      Set the Xob state based on the owner document

    <!-- -->

    - #### hashCode

          public int hashCode()

      Deprecated. 
      Overrides:
      `hashCode` in class `java.lang.Object`

    <!-- -->

    - #### getInputStream

          public java.io.InputStream getInputStream()
                                             throws java.sql.SQLException

      Deprecated. 
      Get an InputStream from the node, applications can read XML data from the stream
      Returns:
      the InputStream for the node.

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### writeToOutputStream

          public void writeToOutputStream(java.io.OutputStream os)
                                   throws java.sql.SQLException

      Deprecated. 
      Write the contents of the node to an OutputStream.
      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getUserData

          public java.lang.Object getUserData(java.lang.String key)

      Deprecated. 

    <!-- -->

    - #### setUserData

          public java.lang.Object setUserData(java.lang.String key,
                                              java.lang.Object data,
                                              UserDataHandler handler)

      Deprecated. 

    <!-- -->

    - #### getFeature

          public java.lang.Object getFeature(java.lang.String feature,
                                             java.lang.String version)

      Deprecated. 

    <!-- -->

    - #### isEqualNode

          public boolean isEqualNode(Node arg)

      Deprecated. 

    <!-- -->

    - #### lookupNamespaceURI

          public java.lang.String lookupNamespaceURI(java.lang.String prefix)

      Deprecated. 

    <!-- -->

    - #### compareDocumentPosition

          public short compareDocumentPosition(Node other)
                                        throws DOMException

      Deprecated. 
      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md)

    <!-- -->

    - #### getTextContent

          public java.lang.String getTextContent()
                                          throws DOMException

      Deprecated. 
      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md)

    <!-- -->

    - #### setTextContent

          public void setTextContent(java.lang.String textContent)
                              throws DOMException

      Deprecated. 
      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md)

    <!-- -->

    - #### isSameNode

          public boolean isSameNode(Node other)

      Deprecated. 

    <!-- -->

    - #### lookupPrefix

          public java.lang.String lookupPrefix(java.lang.String namespaceURI)

      Deprecated. 

    <!-- -->

    - #### isDefaultNamespace

          public boolean isDefaultNamespace(java.lang.String namespaceURI)

      Deprecated. 

    <!-- -->

    - #### getBaseURI

          public java.lang.String getBaseURI()

      Deprecated. 

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

- **[Prev Class](XDBNamedNodeMap.md)**
- **[Next Class](XDBNodeList.md)**

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
