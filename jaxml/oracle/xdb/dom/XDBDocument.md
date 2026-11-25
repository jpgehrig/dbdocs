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

- **[Prev Class](XDBDocFragment.md)**
- **[Next Class](XDBDocumentType.md)**

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

## **Class XDBDocument**

- **java.lang.Object**

- - **[oracle.xdb.dom.XDBNode](XDBNode.md)**

  - - **oracle.xdb.dom.XDBDocument**

<!-- -->

- **All Implemented Interfaces:**
  **[Document](../../../org/w3c/dom/Document.md), [Node](../../../org/w3c/dom/Node.md)**

  <!-- -->

  **Direct Known Subclasses:**
  **[XDBBinaryDocument](XDBBinaryDocument.md)**

  ------------------------------------------------------------------------

  **Deprecated. **
  **as of Oracle Database 11g release 1, use oracle.xml.parser.v2.XMLDocument**
  **
  **

      public class XDBDocument
      extends XDBNode
      implements Document

<!-- -->

-
  -

    ### **Field Summary**

    -

      ### **Fields inherited from interface org.w3c.dom.[Node](../../../org/w3c/dom/Node.md)**

      **[`ATTRIBUTE_NODE`](../../../org/w3c/dom/Node.md)`, `[`CDATA_SECTION_NODE`](../../../org/w3c/dom/Node.md)`, `[`COMMENT_NODE`](../../../org/w3c/dom/Node.md)`, `[`DOCUMENT_FRAGMENT_NODE`](../../../org/w3c/dom/Node.md)`, `[`DOCUMENT_NODE`](../../../org/w3c/dom/Node.md)`, `[`DOCUMENT_TYPE_NODE`](../../../org/w3c/dom/Node.md)`, `[`ELEMENT_NODE`](../../../org/w3c/dom/Node.md)`, `[`ENTITY_NODE`](../../../org/w3c/dom/Node.md)`, `[`ENTITY_REFERENCE_NODE`](../../../org/w3c/dom/Node.md)`, `[`NOTATION_NODE`](../../../org/w3c/dom/Node.md)`, `[`PROCESSING_INSTRUCTION_NODE`](../../../org/w3c/dom/Node.md)`, `[`TEXT_NODE`](../../../org/w3c/dom/Node.md)**

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                                     |
    |-----------------------------------------------------------------------------------------------------------------|
    | `XDBDocument``()`<br>Deprecated. <br>                                                                           |
    | `XDBDocument``(byte[] source)`<br>Deprecated. <br>                                                              |
    | `XDBDocument``(java.sql.Connection conn)`<br>Deprecated. <br>                                                   |
    | `XDBDocument``(java.sql.Connection conn, byte[] source)`<br>Deprecated. <br>                                    |
    | `XDBDocument``(java.sql.Connection conn, long xobd)`<br>Deprecated. <br>                                        |
    | `XDBDocument``(java.sql.Connection conn, java.lang.String source)`<br>Deprecated. <br>                          |
    | `XDBDocument``(java.lang.String source)`<br>Deprecated. <br>                                                    |
    | `XDBDocument``(`[`XMLType`](../XMLType.md)` parxmlt, java.sql.Connection conn, long xobd)`<br>Deprecated. <br>  |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                        | Method and Description                                                                                                                                                                                      |
    |--------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Node`](../../../org/w3c/dom/Node.md)                                   | `adoptNode``(`[`Node`](../../../org/w3c/dom/Node.md)` source)`<br>Deprecated. <br>                                                                                                                          |
    | [`Node`](../../../org/w3c/dom/Node.md)                                   | `appendChild``(`[`Node`](../../../org/w3c/dom/Node.md)` arg)`<br>Deprecated. <br>append the given node to the list of children of this node.                                                                |
    | `void`                                                                   | `close``()`<br>Deprecated. <br>                                                                                                                                                                             |
    | [`Attr`](../../../org/w3c/dom/Attr.md)                                   | `createAttribute``(java.lang.String qname)`<br>Deprecated. <br>create an empty attribute node.                                                                                                              |
    | [`Attr`](../../../org/w3c/dom/Attr.md)                                   | `createAttributeNS``(java.lang.String nsURI, java.lang.String qname)`<br>Deprecated. <br>create an empty attribute node given the namespace information.                                                    |
    | [`CDATASection`](../../../org/w3c/dom/CDATASection.md)                   | `createCDATASection``(java.lang.String data)`<br>Deprecated. <br>create a CDATA section node.                                                                                                               |
    | [`Comment`](../../../org/w3c/dom/Comment.md)                             | `createComment``(java.lang.String data)`<br>Deprecated. <br>create a comment node.                                                                                                                          |
    | [`DocumentFragment`](../../../org/w3c/dom/DocumentFragment.md)           | `createDocumentFragment``()`<br>Deprecated. <br>create an empty document fragment.                                                                                                                          |
    | [`Element`](../../../org/w3c/dom/Element.md)                             | `createElement``(java.lang.String tagName)`<br>Deprecated. <br>create and Return a new empty element associated with the document.                                                                          |
    | [`Element`](../../../org/w3c/dom/Element.md)                             | `createElementNS``(java.lang.String nsURI, java.lang.String qname)`<br>Deprecated. <br>create and Return a new empty element associated with the document.                                                  |
    | [`EntityReference`](../../../org/w3c/dom/EntityReference.md)             | `createEntityReference``(java.lang.String name)`<br>Deprecated. <br>create an entity reference node.                                                                                                        |
    | [`ProcessingInstruction`](../../../org/w3c/dom/ProcessingInstruction.md) | `createProcessingInstruction``(java.lang.String target, java.lang.String data)`<br>Deprecated. <br>create a processing instruction node.                                                                    |
    | [`Text`](../../../org/w3c/dom/Text.md)                                   | `createTextNode``(java.lang.String data)`<br>Deprecated. <br>create an empty text node.                                                                                                                     |
    | `void`                                                                   | `finalize``()`<br>Deprecated. <br>                                                                                                                                                                          |
    | [`DocumentType`](../../../org/w3c/dom/DocumentType.md)                   | `getDoctype``()`<br>Deprecated. <br>Returns the document type defn. of the doc.                                                                                                                             |
    | [`Element`](../../../org/w3c/dom/Element.md)                             | `getDocumentElement``()`<br>Deprecated. <br>Returns the root element of the document.                                                                                                                       |
    | `java.lang.String`                                                       | `getDocumentURI``()`<br>Deprecated. <br>                                                                                                                                                                    |
    | [`DOMConfiguration`](../../../org/w3c/dom/DOMConfiguration.md)           | `getDomConfig``()`<br>Deprecated. <br>                                                                                                                                                                      |
    | [`Element`](../../../org/w3c/dom/Element.md)                             | `getElementById``(java.lang.String id)`<br>Deprecated. <br>get elements of the given ID with a pre-order traversal of the document tree.                                                                    |
    | [`NodeList`](../../../org/w3c/dom/NodeList.md)                           | `getElementsByTagName``(java.lang.String tagname)`<br>Deprecated. <br>get elements of the given tagname with a pre-order traversal of the document tree.                                                    |
    | [`NodeList`](../../../org/w3c/dom/NodeList.md)                           | `getElementsByTagNameNS``(java.lang.String nsURI, java.lang.String tagname)`<br>Deprecated. <br>get elements of the given tagname and ns URI with a pre-order traversal of the document tree.               |
    | [`Node`](../../../org/w3c/dom/Node.md)                                   | `getFirstChild``()`<br>Deprecated. <br>Returns the first child of the node. must be overriden derived classes which support this                                                                            |
    | `static long`                                                            | `getGP``(java.sql.Connection conn)`<br>Deprecated. <br>                                                                                                                                                     |
    | [`DOMImplementation`](../../../org/w3c/dom/DOMImplementation.md)         | `getImplementation``()`<br>Deprecated. <br>Returns the dom implementation object.                                                                                                                           |
    | `java.lang.String`                                                       | `getInputEncoding``()`<br>Deprecated. <br>                                                                                                                                                                  |
    | [`Node`](../../../org/w3c/dom/Node.md)                                   | `getLastChild``()`<br>Deprecated. <br>Returns the last child of the node. must be overriden derived classes which support this                                                                              |
    | [`Node`](../../../org/w3c/dom/Node.md)                                   | `getNextSibling``()`<br>Deprecated. <br>Returns the next sibling of the node. must be overriden derived classes which support this                                                                          |
    | `java.lang.String`                                                       | `getNodeName``()`<br>Deprecated. <br>get the name of the node                                                                                                                                               |
    | [`Document`](../../../org/w3c/dom/Document.md)                           | `getOwnerDocument``()`<br>Deprecated. <br>the owner document for this node                                                                                                                                  |
    | [`Node`](../../../org/w3c/dom/Node.md)                                   | `getPreviousSibling``()`<br>Deprecated. <br>Returns the previous sibling of the node. must be overriden derived classes which support this                                                                  |
    | `boolean`                                                                | `getStrictErrorChecking``()`<br>Deprecated. <br>                                                                                                                                                            |
    | `java.lang.String`                                                       | `getXmlEncoding``()`<br>Deprecated. <br>                                                                                                                                                                    |
    | `boolean`                                                                | `getXmlStandalone``()`<br>Deprecated. <br>                                                                                                                                                                  |
    | `java.lang.String`                                                       | `getXmlVersion``()`<br>Deprecated. <br>                                                                                                                                                                     |
    | [`Node`](../../../org/w3c/dom/Node.md)                                   | `importNode``(`[`Node`](../../../org/w3c/dom/Node.md)` importNode, boolean deep)`<br>Deprecated. <br>import the given node from the original document based on the rules specified by the DOM specification |
    | [`Node`](../../../org/w3c/dom/Node.md)                                   | `insertBefore``(`[`Node`](../../../org/w3c/dom/Node.md)` newChild, `[`Node`](../../../org/w3c/dom/Node.md)` refChild)`<br>Deprecated. <br>insert the given node before the ref node.                        |
    | `boolean`                                                                | `isClosed``()`<br>Deprecated. <br>                                                                                                                                                                          |
    | `void`                                                                   | `normalizeDocument``()`<br>Deprecated. <br>                                                                                                                                                                 |
    | [`Node`](../../../org/w3c/dom/Node.md)                                   | `removeChild``(`[`Node`](../../../org/w3c/dom/Node.md)` arg)`<br>Deprecated. <br>remove the given node from the node.                                                                                       |
    | [`Node`](../../../org/w3c/dom/Node.md)                                   | `renameNode``(`[`Node`](../../../org/w3c/dom/Node.md)` n, java.lang.String namespaceURI, java.lang.String qualifiedName)`<br>Deprecated. <br>                                                               |
    | [`Node`](../../../org/w3c/dom/Node.md)                                   | `replaceChild``(`[`Node`](../../../org/w3c/dom/Node.md)` newChild, `[`Node`](../../../org/w3c/dom/Node.md)` oldChild)`<br>Deprecated. <br>replace the oldchild node with the newchild node.                 |
    | `void`                                                                   | `setDocumentURI``(java.lang.String documentURI)`<br>Deprecated. <br>                                                                                                                                        |
    | `void`                                                                   | `setStrictErrorChecking``(boolean strictErrorChecking)`<br>Deprecated. <br>                                                                                                                                 |
    | `void`                                                                   | `setXmlStandalone``(boolean xmlStandalone)`<br>Deprecated. <br>                                                                                                                                             |
    | `void`                                                                   | `setXmlVersion``(java.lang.String xmlVersion)`<br>Deprecated. <br>                                                                                                                                          |

    - ### Methods inherited from class oracle.xdb.dom.[XDBNode](XDBNode.md)

      [`cloneNode`](XDBNode.md)`, `[`compareDocumentPosition`](XDBNode.md)`, `[`equals`](XDBNode.md)`, `[`getAttributes`](XDBNode.md)`, `[`getBaseURI`](XDBNode.md)`, `[`getChildNodes`](XDBNode.md)`, `[`getExpandedName`](XDBNode.md)`, `[`getFeature`](XDBNode.md)`, `[`getInputStream`](XDBNode.md)`, `[`getLocalName`](XDBNode.md)`, `[`getNamespaceURI`](XDBNode.md)`, `[`getNodeType`](XDBNode.md)`, `[`getNodeValue`](XDBNode.md)`, `[`getParentNode`](XDBNode.md)`, `[`getPrefix`](XDBNode.md)`, `[`getPrimitiveType`](XDBNode.md)`, `[`getQualifiedName`](XDBNode.md)`, `[`getSchemaNode`](XDBNode.md)`, `[`getTextContent`](XDBNode.md)`, `[`getUserData`](XDBNode.md)`, `[`hasAttributes`](XDBNode.md)`, `[`hasChildNodes`](XDBNode.md)`, `[`hashCode`](XDBNode.md)`, `[`isDefaultNamespace`](XDBNode.md)`, `[`isEqualNode`](XDBNode.md)`, `[`isNilled`](XDBNode.md)`, `[`isSameNode`](XDBNode.md)`, `[`isSchemaBased`](XDBNode.md)`, `[`isSupported`](XDBNode.md)`, `[`lookupNamespaceURI`](XDBNode.md)`, `[`lookupPrefix`](XDBNode.md)`, `[`normalize`](XDBNode.md)`, `[`setNodeValue`](XDBNode.md)`, `[`setNodeXob`](XDBNode.md)`, `[`setOwner`](XDBNode.md)`, `[`setPrefix`](XDBNode.md)`, `[`setTextContent`](XDBNode.md)`, `[`setUserData`](XDBNode.md)`, `[`setXobCstate`](XDBNode.md)`, `[`toCState`](XDBNode.md)`, `[`toString`](XDBNode.md)`, `[`write`](XDBNode.md)`, `[`writeToOutputStream`](XDBNode.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface org.w3c.dom.[Node](../../../org/w3c/dom/Node.md)

      [`cloneNode`](../../../org/w3c/dom/Node.md)`, `[`getAttributes`](../../../org/w3c/dom/Node.md)`, `[`getChildNodes`](../../../org/w3c/dom/Node.md)`, `[`getLocalName`](../../../org/w3c/dom/Node.md)`, `[`getNamespaceURI`](../../../org/w3c/dom/Node.md)`, `[`getNodeType`](../../../org/w3c/dom/Node.md)`, `[`getNodeValue`](../../../org/w3c/dom/Node.md)`, `[`getParentNode`](../../../org/w3c/dom/Node.md)`, `[`getPrefix`](../../../org/w3c/dom/Node.md)`, `[`hasAttributes`](../../../org/w3c/dom/Node.md)`, `[`hasChildNodes`](../../../org/w3c/dom/Node.md)`, `[`isSupported`](../../../org/w3c/dom/Node.md)`, `[`normalize`](../../../org/w3c/dom/Node.md)`, `[`setNodeValue`](../../../org/w3c/dom/Node.md)`, `[`setPrefix`](../../../org/w3c/dom/Node.md)

<!-- -->

- - ### Constructor Detail

    - #### XDBDocument

          public XDBDocument()

      Deprecated. 

    <!-- -->

    - #### XDBDocument

          public XDBDocument(java.sql.Connection conn)
                      throws java.lang.Exception

      Deprecated. 
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### XDBDocument

          public XDBDocument(java.lang.String source)

      Deprecated. 

    <!-- -->

    - #### XDBDocument

          public XDBDocument(java.sql.Connection conn,
                             java.lang.String source)
                      throws java.lang.Exception

      Deprecated. 
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### XDBDocument

          public XDBDocument(byte[] source)

      Deprecated. 

    <!-- -->

    - #### XDBDocument

          public XDBDocument(java.sql.Connection conn,
                             byte[] source)
                      throws java.lang.Exception

      Deprecated. 
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### XDBDocument

          public XDBDocument(java.sql.Connection conn,
                             long xobd)
                      throws XDBDOMException

      Deprecated. 
      Throws:
      [`XDBDOMException`](XDBDOMException.md)

    <!-- -->

    - #### XDBDocument

          public XDBDocument(XMLType parxmlt,
                             java.sql.Connection conn,
                             long xobd)
                      throws XDBDOMException

      Deprecated. 
      Throws:
      [`XDBDOMException`](XDBDOMException.md)

  <!-- -->

  - ### Method Detail

    - #### getDoctype

          public DocumentType getDoctype()

      Deprecated. 
      Returns the document type defn. of the doc. We always return null
      Specified by:
      [`getDoctype`](../../../org/w3c/dom/Document.md) in interface [`Document`](../../../org/w3c/dom/Document.md)

      Returns:
      the document type defn. of the document.

    <!-- -->

    - #### getImplementation

          public DOMImplementation getImplementation()

      Deprecated. 
      Returns the dom implementation object.
      Specified by:
      [`getImplementation`](../../../org/w3c/dom/Document.md) in interface [`Document`](../../../org/w3c/dom/Document.md)

      Returns:
      the XDBDomImplementation object.

    <!-- -->

    - #### getDocumentElement

          public Element getDocumentElement()

      Deprecated. 
      Returns the root element of the document.
      Specified by:
      [`getDocumentElement`](../../../org/w3c/dom/Document.md) in interface [`Document`](../../../org/w3c/dom/Document.md)

      Returns:
      the root XDBElement of the XMLType.

    <!-- -->

    - #### createElement

          public Element createElement(java.lang.String tagName)
                                throws DOMException

      Deprecated. 
      create and Return a new empty element associated with the document. i.e. element with no children and not in the XMLType hierarchy.
      Specified by:
      [`createElement`](../../../org/w3c/dom/Document.md) in interface [`Document`](../../../org/w3c/dom/Document.md)

      Parameters:
      `tagName` - The name of the element type to instantiate. For XML, this is case-sensitive. For HTML, the `tagName` parameter may be provided in any case, but it must be mapped to the canonical uppercase form by the DOM implementation.

      Returns:
      a new XDBElement.

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md) - INVALID_CHARACTER_ERR: Raised if the specified name contains an illegal character.

    <!-- -->

    - #### createDocumentFragment

          public DocumentFragment createDocumentFragment()

      Deprecated. 
      create an empty document fragment.
      Specified by:
      [`createDocumentFragment`](../../../org/w3c/dom/Document.md) in interface [`Document`](../../../org/w3c/dom/Document.md)

      Returns:
      a Document Fragment object.

    <!-- -->

    - #### createTextNode

          public Text createTextNode(java.lang.String data)

      Deprecated. 
      create an empty text node.
      Specified by:
      [`createTextNode`](../../../org/w3c/dom/Document.md) in interface [`Document`](../../../org/w3c/dom/Document.md)

      Parameters:
      `data` - The data for the node.

      Returns:
      a text node object.

    <!-- -->

    - #### createComment

          public Comment createComment(java.lang.String data)

      Deprecated. 
      create a comment node. Not implemented yet.
      Specified by:
      [`createComment`](../../../org/w3c/dom/Document.md) in interface [`Document`](../../../org/w3c/dom/Document.md)

      Parameters:
      `data` - The data for the node.

      Returns:
      a comment node object.

    <!-- -->

    - #### createCDATASection

          public CDATASection createCDATASection(java.lang.String data)
                                          throws DOMException

      Deprecated. 
      create a CDATA section node. Not implemented yet.
      Specified by:
      [`createCDATASection`](../../../org/w3c/dom/Document.md) in interface [`Document`](../../../org/w3c/dom/Document.md)

      Parameters:
      `data` - The data for the `CDATASection` contents.

      Returns:
      a cdatasection object.

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md) - NOT_SUPPORTED_ERR: Raised if this document is an HTML document.

    <!-- -->

    - #### createProcessingInstruction

          public ProcessingInstruction createProcessingInstruction(java.lang.String target,
                                                                   java.lang.String data)
                                                            throws DOMException

      Deprecated. 
      create a processing instruction node.
      Specified by:
      [`createProcessingInstruction`](../../../org/w3c/dom/Document.md) in interface [`Document`](../../../org/w3c/dom/Document.md)

      Parameters:
      `target` - The target part of the processing instruction.

      `data` - The data for the node.

      Returns:
      a PI object.

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md) - INVALID_CHARACTER_ERR: Raised if the specified target contains an illegal character.
      NOT_SUPPORTED_ERR: Raised if this document is an HTML document.

    <!-- -->

    - #### createAttribute

          public Attr createAttribute(java.lang.String qname)
                               throws DOMException

      Deprecated. 
      create an empty attribute node.
      Specified by:
      [`createAttribute`](../../../org/w3c/dom/Document.md) in interface [`Document`](../../../org/w3c/dom/Document.md)

      Parameters:
      `qname` - The name of the attribute.

      Returns:
      an attribute object.

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md) - INVALID_CHARACTER_ERR: Raised if the specified name contains an illegal character.

    <!-- -->

    - #### createEntityReference

          public EntityReference createEntityReference(java.lang.String name)
                                                throws DOMException

      Deprecated. 
      create an entity reference node. We do not implement it
      Specified by:
      [`createEntityReference`](../../../org/w3c/dom/Document.md) in interface [`Document`](../../../org/w3c/dom/Document.md)

      Parameters:
      `name` - The name of the entity to reference.

      Returns:
      an entity reference object.

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md) - INVALID_CHARACTER_ERR: Raised if the specified name contains an illegal character.
      NOT_SUPPORTED_ERR: Raised if this document is an HTML document.

    <!-- -->

    - #### getElementsByTagName

          public NodeList getElementsByTagName(java.lang.String tagname)

      Deprecated. 
      get elements of the given tagname with a pre-order traversal of the document tree.
      Specified by:
      [`getElementsByTagName`](../../../org/w3c/dom/Document.md) in interface [`Document`](../../../org/w3c/dom/Document.md)

      Parameters:
      `tagname` - The name of the tag to match on. The special value "\*" matches all tags.

      Returns:
      a Nodelist of the matched items.

    <!-- -->

    - #### importNode

          public Node importNode(Node importNode,
                                 boolean deep)
                          throws DOMException

      Deprecated. 
      import the given node from the original document based on the rules specified by the DOM specification
      Specified by:
      [`importNode`](../../../org/w3c/dom/Document.md) in interface [`Document`](../../../org/w3c/dom/Document.md)

      Parameters:
      `importNode` - The node to import.

      `deep` - If `true`, recursively import the subtree under the specified node; if `false`, import only the node itself, as explained above. This has no effect on `Attr` , `EntityReference`, and `Notation` nodes.

      Returns:
      a new Node.

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md) - NOT_SUPPORTED_ERR: Raised if the type of node being imported is not supported.

    <!-- -->

    - #### createElementNS

          public Element createElementNS(java.lang.String nsURI,
                                         java.lang.String qname)
                                  throws DOMException

      Deprecated. 
      create and Return a new empty element associated with the document. i.e. element with no children and not in the XMLType hierarchy. This function uses the namespace information as well.
      Specified by:
      [`createElementNS`](../../../org/w3c/dom/Document.md) in interface [`Document`](../../../org/w3c/dom/Document.md)

      Parameters:
      `nsURI` - The namespace URI of the element to create.

      `qname` - The qualified name of the element type to instantiate.

      Returns:
      a new XDBElement.

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md) - INVALID_CHARACTER_ERR: Raised if the specified qualified name contains an illegal character.
      NAMESPACE_ERR: Raised if the `qualifiedName` is malformed, if the `qualifiedName` has a prefix and the `namespaceURI` is `null`, or if the `qualifiedName` has a prefix that is "xml" and the `namespaceURI` is different from " http://www.w3.org/XML/1998/namespace" .

    <!-- -->

    - #### createAttributeNS

          public Attr createAttributeNS(java.lang.String nsURI,
                                        java.lang.String qname)
                                 throws DOMException

      Deprecated. 
      create an empty attribute node given the namespace information.
      Specified by:
      [`createAttributeNS`](../../../org/w3c/dom/Document.md) in interface [`Document`](../../../org/w3c/dom/Document.md)

      Parameters:
      `nsURI` - The namespace URI of the attribute to create.

      `qname` - The qualified name of the attribute to instantiate.

      Returns:
      an attribute object.

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md) - INVALID_CHARACTER_ERR: Raised if the specified qualified name contains an illegal character.
      NAMESPACE_ERR: Raised if the `qualifiedName` is malformed, if the `qualifiedName` has a prefix and the `namespaceURI` is `null`, if the `qualifiedName` has a prefix that is "xml" and the `namespaceURI` is different from " http://www.w3.org/XML/1998/namespace", or if the `qualifiedName` is "xmlns" and the `namespaceURI` is different from " http://www.w3.org/2000/xmlns/".

    <!-- -->

    - #### getElementsByTagNameNS

          public NodeList getElementsByTagNameNS(java.lang.String nsURI,
                                                 java.lang.String tagname)

      Deprecated. 
      get elements of the given tagname and ns URI with a pre-order traversal of the document tree.
      Specified by:
      [`getElementsByTagNameNS`](../../../org/w3c/dom/Document.md) in interface [`Document`](../../../org/w3c/dom/Document.md)

      Parameters:
      `nsURI` - The namespace URI of the elements to match on. The special value "\*" matches all namespaces.

      `tagname` - The local name of the elements to match on. The special value "\*" matches all local names.

      Returns:
      a Nodelist of the matched items.

    <!-- -->

    - #### getElementById

          public Element getElementById(java.lang.String id)

      Deprecated. 
      get elements of the given ID with a pre-order traversal of the document tree.
      Specified by:
      [`getElementById`](../../../org/w3c/dom/Document.md) in interface [`Document`](../../../org/w3c/dom/Document.md)

      Parameters:
      `id` - The unique `id` value for an element.

      Returns:
      an Element with the matching ID.

    <!-- -->

    - #### getNodeName

          public java.lang.String getNodeName()

      Deprecated. 
      get the name of the node
      Specified by:
      [`getNodeName`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

      Overrides:
      [`getNodeName`](XDBNode.md) in class [`XDBNode`](XDBNode.md)

      Returns:
      the node name string, always "#document" for this node.

    <!-- -->

    - #### getOwnerDocument

          public Document getOwnerDocument()

      Deprecated. 
      the owner document for this node
      Specified by:
      [`getOwnerDocument`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

      Overrides:
      [`getOwnerDocument`](XDBNode.md) in class [`XDBNode`](XDBNode.md)

      Returns:
      always null for this node

    <!-- -->

    - #### insertBefore

          public Node insertBefore(Node newChild,
                                   Node refChild)
                            throws DOMException

      Deprecated. 
      insert the given node before the ref node. In this case, if the node already has children this function will throw an exception
      Specified by:
      [`insertBefore`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

      Overrides:
      [`insertBefore`](XDBNode.md) in class [`XDBNode`](XDBNode.md)

      Parameters:
      `newChild` - The node to insert.

      `refChild` - The reference node, i.e., the node before which the new node must be inserted.

      Returns:
      The newChild which is to be inserted

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md) - HIERARCHY_REQUEST_ERR: Raised if this node is of a type that does not allow children of the type of the `newChild` node, or if the node to insert is one of this node's ancestors.
      WRONG_DOCUMENT_ERR: Raised if `newChild` was created from a different document than the one that created this node.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly or if the parent of the node being inserted is readonly.
      NOT_FOUND_ERR: Raised if `refChild` is not a child of this node.

    <!-- -->

    - #### replaceChild

          public Node replaceChild(Node newChild,
                                   Node oldChild)
                            throws DOMException

      Deprecated. 
      replace the oldchild node with the newchild node.
      Specified by:
      [`replaceChild`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

      Overrides:
      [`replaceChild`](XDBNode.md) in class [`XDBNode`](XDBNode.md)

      Parameters:
      `newChild` - The new node to put in the child list.

      `oldChild` - The node being replaced in the list.

      Returns:
      The oldChild node which has been replaced

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md) - HIERARCHY_REQUEST_ERR: Raised if this node is of a type that does not allow children of the type of the `newChild` node, or if the node to put in is one of this node's ancestors.
      WRONG_DOCUMENT_ERR: Raised if `newChild` was created from a different document than the one that created this node.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node or the parent of the new node is readonly.
      NOT_FOUND_ERR: Raised if `oldChild` is not a child of this node.

    <!-- -->

    - #### removeChild

          public Node removeChild(Node arg)
                           throws DOMException

      Deprecated. 
      remove the given node from the node.
      Specified by:
      [`removeChild`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

      Overrides:
      [`removeChild`](XDBNode.md) in class [`XDBNode`](XDBNode.md)

      Parameters:
      `arg` - The node being removed.

      Returns:
      The node which is being removed

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md) - NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.
      NOT_FOUND_ERR: Raised if `oldChild` is not a child of this node.

    <!-- -->

    - #### appendChild

          public Node appendChild(Node arg)
                           throws DOMException

      Deprecated. 
      append the given node to the list of children of this node. This will work only if the document has no children
      Specified by:
      [`appendChild`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

      Overrides:
      [`appendChild`](XDBNode.md) in class [`XDBNode`](XDBNode.md)

      Parameters:
      `arg` - The node to add.If it is a `DocumentFragment` object, the entire contents of the document fragment are moved into the child list of this node

      Returns:
      The node which is being appended

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md) - HIERARCHY_REQUEST_ERR: Raised if this node is of a type that does not allow children of the type of the `newChild` node, or if the node to append is one of this node's ancestors.
      WRONG_DOCUMENT_ERR: Raised if `newChild` was created from a different document than the one that created this node.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.

    <!-- -->

    - #### getFirstChild

          public Node getFirstChild()

      Deprecated. 
      Description copied from class: [`XDBNode`](XDBNode.md)
      Returns the first child of the node. must be overriden derived classes which support this
      Specified by:
      [`getFirstChild`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

      Overrides:
      [`getFirstChild`](XDBNode.md) in class [`XDBNode`](XDBNode.md)

      Returns:
      the first child node

    <!-- -->

    - #### getLastChild

          public Node getLastChild()

      Deprecated. 
      Description copied from class: [`XDBNode`](XDBNode.md)
      Returns the last child of the node. must be overriden derived classes which support this
      Specified by:
      [`getLastChild`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

      Overrides:
      [`getLastChild`](XDBNode.md) in class [`XDBNode`](XDBNode.md)

      Returns:
      the last child node

    <!-- -->

    - #### getPreviousSibling

          public Node getPreviousSibling()

      Deprecated. 
      Description copied from class: [`XDBNode`](XDBNode.md)
      Returns the previous sibling of the node. must be overriden derived classes which support this
      Specified by:
      [`getPreviousSibling`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

      Overrides:
      [`getPreviousSibling`](XDBNode.md) in class [`XDBNode`](XDBNode.md)

      Returns:
      the previous node

    <!-- -->

    - #### getNextSibling

          public Node getNextSibling()

      Deprecated. 
      Description copied from class: [`XDBNode`](XDBNode.md)
      Returns the next sibling of the node. must be overriden derived classes which support this
      Specified by:
      [`getNextSibling`](../../../org/w3c/dom/Node.md) in interface [`Node`](../../../org/w3c/dom/Node.md)

      Overrides:
      [`getNextSibling`](XDBNode.md) in class [`XDBNode`](XDBNode.md)

      Returns:
      the next node

    <!-- -->

    - #### isClosed

          public boolean isClosed()

      Deprecated. 

    <!-- -->

    - #### close

          public void close()

      Deprecated. 
      Overrides:
      [`close`](XDBNode.md) in class [`XDBNode`](XDBNode.md)

    <!-- -->

    - #### finalize

          public void finalize()
                        throws java.lang.Throwable

      Deprecated. 
      Overrides:
      [`finalize`](XDBNode.md) in class [`XDBNode`](XDBNode.md)

      Throws:
      `java.lang.Throwable`

    <!-- -->

    - #### getGP

          public static long getGP(java.sql.Connection conn)

      Deprecated. 

    <!-- -->

    - #### renameNode

          public Node renameNode(Node n,
                                 java.lang.String namespaceURI,
                                 java.lang.String qualifiedName)
                          throws DOMException

      Deprecated. 
      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md)

    <!-- -->

    - #### getDomConfig

          public DOMConfiguration getDomConfig()

      Deprecated. 

    <!-- -->

    - #### normalizeDocument

          public void normalizeDocument()

      Deprecated. 

    <!-- -->

    - #### getStrictErrorChecking

          public boolean getStrictErrorChecking()

      Deprecated. 

    <!-- -->

    - #### setStrictErrorChecking

          public void setStrictErrorChecking(boolean strictErrorChecking)

      Deprecated. 

    <!-- -->

    - #### getDocumentURI

          public java.lang.String getDocumentURI()

      Deprecated. 

    <!-- -->

    - #### setDocumentURI

          public void setDocumentURI(java.lang.String documentURI)

      Deprecated. 

    <!-- -->

    - #### adoptNode

          public Node adoptNode(Node source)
                         throws DOMException

      Deprecated. 
      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md)

    <!-- -->

    - #### getInputEncoding

          public java.lang.String getInputEncoding()

      Deprecated. 

    <!-- -->

    - #### getXmlEncoding

          public java.lang.String getXmlEncoding()

      Deprecated. 

    <!-- -->

    - #### getXmlStandalone

          public boolean getXmlStandalone()

      Deprecated. 

    <!-- -->

    - #### setXmlStandalone

          public void setXmlStandalone(boolean xmlStandalone)
                                throws DOMException

      Deprecated. 
      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md)

    <!-- -->

    - #### getXmlVersion

          public java.lang.String getXmlVersion()

      Deprecated. 

    <!-- -->

    - #### setXmlVersion

          public void setXmlVersion(java.lang.String xmlVersion)
                             throws DOMException

      Deprecated. 
      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md)

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

- **[Prev Class](XDBDocFragment.md)**
- **[Next Class](XDBDocumentType.md)**

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
