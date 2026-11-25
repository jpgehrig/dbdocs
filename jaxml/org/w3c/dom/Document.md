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

- **[Prev Class](Comment.md)**
- **[Next Class](DocumentFragment.md)**

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

## **Interface Document**

- **All Superinterfaces:**
  **[Node](Node.md)**

  <!-- -->

  **All Known Implementing Classes:**
  **[XDBBinaryDocument](../../../oracle/xdb/dom/XDBBinaryDocument.md), [XDBDocument](../../../oracle/xdb/dom/XDBDocument.md), [XMLDocument](../../../oracle/xml/parser/v2/XMLDocument.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface Document
      extends Node

  **The `Document` interface represents the entire HTML or XML document. Conceptually, it is the root of the document tree, and provides the primary access to the document's data.**
  **Since elements, text nodes, comments, processing instructions, etc. cannot exist outside the context of a `Document`, the `Document` interface also contains the factory methods needed to create these objects. The `Node` objects created have a `ownerDocument` attribute which associates them with the `Document` within whose context they were created.**

  **See also the [Document Object Model (DOM) Level 2 Core Specification](http://www.w3.org/TR/2000/REC-DOM-Level-2-Core-20001113).**

<!-- -->

-
  -

    ### **Field Summary**

    -

      ### **Fields inherited from interface org.w3c.dom.[Node](Node.md)**

      **[`ATTRIBUTE_NODE`](Node.md)`, `[`CDATA_SECTION_NODE`](Node.md)`, `[`COMMENT_NODE`](Node.md)`, `[`DOCUMENT_FRAGMENT_NODE`](Node.md)`, `[`DOCUMENT_NODE`](Node.md)`, `[`DOCUMENT_TYPE_NODE`](Node.md)`, `[`ELEMENT_NODE`](Node.md)`, `[`ENTITY_NODE`](Node.md)`, `[`ENTITY_REFERENCE_NODE`](Node.md)`, `[`NOTATION_NODE`](Node.md)`, `[`PROCESSING_INSTRUCTION_NODE`](Node.md)`, `[`TEXT_NODE`](Node.md)**

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                   | Method and Description                                                                                                                                                                                                                                                   |
    |-----------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Attr`](Attr.md)                                   | `createAttribute``(java.lang.String name)`<br>Creates an `Attr` of the given name.                                                                                                                                                                                       |
    | [`Attr`](Attr.md)                                   | `createAttributeNS``(java.lang.String namespaceURI, java.lang.String qualifiedName)`<br>Creates an attribute of the given qualified name and namespace URI.                                                                                                              |
    | [`CDATASection`](CDATASection.md)                   | `createCDATASection``(java.lang.String data)`<br>Creates a `CDATASection` node whose value is the specified string.                                                                                                                                                      |
    | [`Comment`](Comment.md)                             | `createComment``(java.lang.String data)`<br>Creates a `Comment` node given the specified string.                                                                                                                                                                         |
    | [`DocumentFragment`](DocumentFragment.md)           | `createDocumentFragment``()`<br>Creates an empty `DocumentFragment` object.                                                                                                                                                                                              |
    | [`Element`](Element.md)                             | `createElement``(java.lang.String tagName)`<br>Creates an element of the type specified.                                                                                                                                                                                 |
    | [`Element`](Element.md)                             | `createElementNS``(java.lang.String namespaceURI, java.lang.String qualifiedName)`<br>Creates an element of the given qualified name and namespace URI.                                                                                                                  |
    | [`EntityReference`](EntityReference.md)             | `createEntityReference``(java.lang.String name)`<br>Creates an `EntityReference` object.                                                                                                                                                                                 |
    | [`ProcessingInstruction`](ProcessingInstruction.md) | `createProcessingInstruction``(java.lang.String target, java.lang.String data)`<br>Creates a `ProcessingInstruction` node given the specified name and data strings.                                                                                                     |
    | [`Text`](Text.md)                                   | `createTextNode``(java.lang.String data)`<br>Creates a `Text` node given the specified string.                                                                                                                                                                           |
    | [`DocumentType`](DocumentType.md)                   | `getDoctype``()`<br>The Document Type Declaration (see `DocumentType`) associated with this document.                                                                                                                                                                    |
    | [`Element`](Element.md)                             | `getDocumentElement``()`<br>This is a convenience attribute that allows direct access to the child node that is the root element of the document.                                                                                                                        |
    | [`Element`](Element.md)                             | `getElementById``(java.lang.String elementId)`<br>Returns the `Element` whose `ID` is given by `elementId`.                                                                                                                                                              |
    | [`NodeList`](NodeList.md)                           | `getElementsByTagName``(java.lang.String tagname)`<br>Returns a `NodeList` of all the `Elements` with a given tag name in the order in which they are encountered in a preorder traversal of the `Document` tree.                                                        |
    | [`NodeList`](NodeList.md)                           | `getElementsByTagNameNS``(java.lang.String namespaceURI, java.lang.String localName)`<br>Returns a `NodeList` of all the `Elements` with a given local name and namespace URI in the order in which they are encountered in a preorder traversal of the `Document` tree. |
    | [`DOMImplementation`](DOMImplementation.md)         | `getImplementation``()`<br>The `DOMImplementation` object that handles this document.                                                                                                                                                                                    |
    | [`Node`](Node.md)                                   | `importNode``(`[`Node`](Node.md)` importedNode, boolean deep)`<br>Imports a node from another document to this document.                                                                                                                                                 |

    - ### Methods inherited from interface org.w3c.dom.[Node](Node.md)

      [`appendChild`](Node.md)`, `[`cloneNode`](Node.md)`, `[`getAttributes`](Node.md)`, `[`getChildNodes`](Node.md)`, `[`getFirstChild`](Node.md)`, `[`getLastChild`](Node.md)`, `[`getLocalName`](Node.md)`, `[`getNamespaceURI`](Node.md)`, `[`getNextSibling`](Node.md)`, `[`getNodeName`](Node.md)`, `[`getNodeType`](Node.md)`, `[`getNodeValue`](Node.md)`, `[`getOwnerDocument`](Node.md)`, `[`getParentNode`](Node.md)`, `[`getPrefix`](Node.md)`, `[`getPreviousSibling`](Node.md)`, `[`hasAttributes`](Node.md)`, `[`hasChildNodes`](Node.md)`, `[`insertBefore`](Node.md)`, `[`isSupported`](Node.md)`, `[`normalize`](Node.md)`, `[`removeChild`](Node.md)`, `[`replaceChild`](Node.md)`, `[`setNodeValue`](Node.md)`, `[`setPrefix`](Node.md)

<!-- -->

- - ### Method Detail

    - #### getDoctype

          DocumentType getDoctype()

      The Document Type Declaration (see `DocumentType`) associated with this document. For HTML documents as well as XML documents without a document type declaration this returns `null`. The DOM Level 2 does not support editing the Document Type Declaration. `docType` cannot be altered in any way, including through the use of methods inherited from the `Node` interface, such as `insertNode` or `removeNode`.

    <!-- -->

    - #### getImplementation

          DOMImplementation getImplementation()

      The `DOMImplementation` object that handles this document. A DOM application may use objects from multiple implementations.

    <!-- -->

    - #### getDocumentElement

          Element getDocumentElement()

      This is a convenience attribute that allows direct access to the child node that is the root element of the document. For HTML documents, this is the element with the tagName "HTML".

    <!-- -->

    - #### createElement

          Element createElement(java.lang.String tagName)
                         throws DOMException

      Creates an element of the type specified. Note that the instance returned implements the `Element` interface, so attributes can be specified directly on the returned object.
      In addition, if there are known attributes with default values, `Attr` nodes representing them are automatically created and attached to the element.
      To create an element with a qualified name and namespace URI, use the `createElementNS` method.
      Parameters:
      `tagName` - The name of the element type to instantiate. For XML, this is case-sensitive. For HTML, the `tagName` parameter may be provided in any case, but it must be mapped to the canonical uppercase form by the DOM implementation.

      Returns:
      A new `Element` object with the `nodeName` attribute set to `tagName`, and `localName`, `prefix`, and `namespaceURI` set to `null`.

      Throws:
      [`DOMException`](DOMException.md) - INVALID_CHARACTER_ERR: Raised if the specified name contains an illegal character.

    <!-- -->

    - #### createDocumentFragment

          DocumentFragment createDocumentFragment()

      Creates an empty `DocumentFragment` object.
      Returns:
      A new `DocumentFragment`.

    <!-- -->

    - #### createTextNode

          Text createTextNode(java.lang.String data)

      Creates a `Text` node given the specified string.
      Parameters:
      `data` - The data for the node.

      Returns:
      The new `Text` object.

    <!-- -->

    - #### createComment

          Comment createComment(java.lang.String data)

      Creates a `Comment` node given the specified string.
      Parameters:
      `data` - The data for the node.

      Returns:
      The new `Comment` object.

    <!-- -->

    - #### createCDATASection

          CDATASection createCDATASection(java.lang.String data)
                                   throws DOMException

      Creates a `CDATASection` node whose value is the specified string.
      Parameters:
      `data` - The data for the `CDATASection` contents.

      Returns:
      The new `CDATASection` object.

      Throws:
      [`DOMException`](DOMException.md) - NOT_SUPPORTED_ERR: Raised if this document is an HTML document.

    <!-- -->

    - #### createProcessingInstruction

          ProcessingInstruction createProcessingInstruction(java.lang.String target,
                                                            java.lang.String data)
                                                     throws DOMException

      Creates a `ProcessingInstruction` node given the specified name and data strings.
      Parameters:
      `target` - The target part of the processing instruction.

      `data` - The data for the node.

      Returns:
      The new `ProcessingInstruction` object.

      Throws:
      [`DOMException`](DOMException.md) - INVALID_CHARACTER_ERR: Raised if the specified target contains an illegal character.
      NOT_SUPPORTED_ERR: Raised if this document is an HTML document.

    <!-- -->

    - #### createAttribute

          Attr createAttribute(java.lang.String name)
                        throws DOMException

      Creates an `Attr` of the given name. Note that the `Attr` instance can then be set on an `Element` using the `setAttributeNode` method.
      To create an attribute with a qualified name and namespace URI, use the `createAttributeNS` method.
      Parameters:
      `name` - The name of the attribute.

      Returns:
      A new `Attr` object with the `nodeName` attribute set to `name`, and `localName`, `prefix`, and `namespaceURI` set to `null`. The value of the attribute is the empty string.

      Throws:
      [`DOMException`](DOMException.md) - INVALID_CHARACTER_ERR: Raised if the specified name contains an illegal character.

    <!-- -->

    - #### createEntityReference

          EntityReference createEntityReference(java.lang.String name)
                                         throws DOMException

      Creates an `EntityReference` object. In addition, if the referenced entity is known, the child list of the `EntityReference` node is made the same as that of the corresponding `Entity` node.If any descendant of the `Entity` node has an unbound namespace prefix, the corresponding descendant of the created `EntityReference` node is also unbound; (its `namespaceURI` is `null`). The DOM Level 2 does not support any mechanism to resolve namespace prefixes.
      Parameters:
      `name` - The name of the entity to reference.

      Returns:
      The new `EntityReference` object.

      Throws:
      [`DOMException`](DOMException.md) - INVALID_CHARACTER_ERR: Raised if the specified name contains an illegal character.
      NOT_SUPPORTED_ERR: Raised if this document is an HTML document.

    <!-- -->

    - #### getElementsByTagName

          NodeList getElementsByTagName(java.lang.String tagname)

      Returns a `NodeList` of all the `Elements` with a given tag name in the order in which they are encountered in a preorder traversal of the `Document` tree.
      Parameters:
      `tagname` - The name of the tag to match on. The special value "\*" matches all tags.

      Returns:
      A new `NodeList` object containing all the matched `Elements`.

    <!-- -->

    - #### importNode

          Node importNode(Node importedNode,
                          boolean deep)
                   throws DOMException

      Imports a node from another document to this document. The returned node has no parent; (`parentNode` is `null`). The source node is not altered or removed from the original document; this method creates a new copy of the source node.
      For all nodes, importing a node creates a node object owned by the importing document, with attribute values identical to the source node's `nodeName` and `nodeType`, plus the attributes related to namespaces (`prefix`, `localName`, and `namespaceURI`). As in the `cloneNode` operation on a `Node`, the source node is not altered.
      Additional information is copied as appropriate to the `nodeType`, attempting to mirror the behavior expected if a fragment of XML or HTML source was copied from one document to another, recognizing that the two documents may have different DTDs in the XML case. The following list describes the specifics for each type of node.
      ATTRIBUTE_NODE
      The `ownerElement` attribute is set to `null` and the `specified` flag is set to `true` on the generated `Attr`. The descendants of the source `Attr` are recursively imported and the resulting nodes reassembled to form the corresponding subtree. Note that the `deep` parameter has no effect on `Attr` nodes; they always carry their children with them when imported.

      DOCUMENT_FRAGMENT_NODE
      If the `deep` option was set to `true`, the descendants of the source element are recursively imported and the resulting nodes reassembled to form the corresponding subtree. Otherwise, this simply generates an empty `DocumentFragment`.

      DOCUMENT_NODE
      `Document` nodes cannot be imported.

      DOCUMENT_TYPE_NODE
      `DocumentType` nodes cannot be imported.

      ELEMENT_NODE
      Specified attribute nodes of the source element are imported, and the generated `Attr` nodes are attached to the generated `Element`. Default attributes are not copied, though if the document being imported into defines default attributes for this element name, those are assigned. If the `importNode` `deep` parameter was set to `true`, the descendants of the source element are recursively imported and the resulting nodes reassembled to form the corresponding subtree.

      ENTITY_NODE
      `Entity` nodes can be imported, however in the current release of the DOM the `DocumentType` is readonly. Ability to add these imported nodes to a `DocumentType` will be considered for addition to a future release of the DOM.On import, the `publicId`, `systemId`, and `notationName` attributes are copied. If a `deep` import is requested, the descendants of the the source `Entity` are recursively imported and the resulting nodes reassembled to form the corresponding subtree.

      ENTITY_REFERENCE_NODE
      Only the `EntityReference` itself is copied, even if a `deep` import is requested, since the source and destination documents might have defined the entity differently. If the document being imported into provides a definition for this entity name, its value is assigned.

      NOTATION_NODE
      `Notation` nodes can be imported, however in the current release of the DOM the `DocumentType` is readonly. Ability to add these imported nodes to a `DocumentType` will be considered for addition to a future release of the DOM.On import, the `publicId` and `systemId` attributes are copied. Note that the `deep` parameter has no effect on `Notation` nodes since they never have any children.

      PROCESSING_INSTRUCTION_NODE
      The imported node copies its `target` and `data` values from those of the source node.

      TEXT_NODE, CDATA_SECTION_NODE, COMMENT_NODE
      These three types of nodes inheriting from `CharacterData` copy their `data` and `length` attributes from those of the source node.

      <!-- -->

      Parameters:
      `importedNode` - The node to import.

      `deep` - If `true`, recursively import the subtree under the specified node; if `false`, import only the node itself, as explained above. This has no effect on `Attr` , `EntityReference`, and `Notation` nodes.

      Returns:
      The imported node that belongs to this `Document`.

      Throws:
      [`DOMException`](DOMException.md) - NOT_SUPPORTED_ERR: Raised if the type of node being imported is not supported.

      Since:
      DOM Level 2

    <!-- -->

    - #### createElementNS

          Element createElementNS(java.lang.String namespaceURI,
                                  java.lang.String qualifiedName)
                           throws DOMException

      Creates an element of the given qualified name and namespace URI. HTML-only DOM implementations do not need to implement this method.
      Parameters:
      `namespaceURI` - The namespace URI of the element to create.

      `qualifiedName` - The qualified name of the element type to instantiate.

      Returns:
      A new `Element` object with the following attributes:AttributeValue`Node.nodeName` `qualifiedName``Node.namespaceURI` `namespaceURI``Node.prefix`prefix, extracted from `qualifiedName`, or `null` if there is no prefix`Node.localName`local name, extracted from `qualifiedName``Element.tagName` `qualifiedName`

      Throws:
      [`DOMException`](DOMException.md) - INVALID_CHARACTER_ERR: Raised if the specified qualified name contains an illegal character.
      NAMESPACE_ERR: Raised if the `qualifiedName` is malformed, if the `qualifiedName` has a prefix and the `namespaceURI` is `null`, or if the `qualifiedName` has a prefix that is "xml" and the `namespaceURI` is different from " http://www.w3.org/XML/1998/namespace" .

      Since:
      DOM Level 2

    <!-- -->

    - #### createAttributeNS

          Attr createAttributeNS(java.lang.String namespaceURI,
                                 java.lang.String qualifiedName)
                          throws DOMException

      Creates an attribute of the given qualified name and namespace URI. HTML-only DOM implementations do not need to implement this method.
      Parameters:
      `namespaceURI` - The namespace URI of the attribute to create.

      `qualifiedName` - The qualified name of the attribute to instantiate.

      Returns:
      A new `Attr` object with the following attributes: AttributeValue`Node.nodeName`qualifiedName `Node.namespaceURI``namespaceURI` `Node.prefix`prefix, extracted from `qualifiedName`, or `null` if there is no prefix`Node.localName`local name, extracted from `qualifiedName``Attr.name` `qualifiedName``Node.nodeValue`the empty string

      Throws:
      [`DOMException`](DOMException.md) - INVALID_CHARACTER_ERR: Raised if the specified qualified name contains an illegal character.
      NAMESPACE_ERR: Raised if the `qualifiedName` is malformed, if the `qualifiedName` has a prefix and the `namespaceURI` is `null`, if the `qualifiedName` has a prefix that is "xml" and the `namespaceURI` is different from " http://www.w3.org/XML/1998/namespace", or if the `qualifiedName` is "xmlns" and the `namespaceURI` is different from " http://www.w3.org/2000/xmlns/".

      Since:
      DOM Level 2

    <!-- -->

    - #### getElementsByTagNameNS

          NodeList getElementsByTagNameNS(java.lang.String namespaceURI,
                                          java.lang.String localName)

      Returns a `NodeList` of all the `Elements` with a given local name and namespace URI in the order in which they are encountered in a preorder traversal of the `Document` tree.
      Parameters:
      `namespaceURI` - The namespace URI of the elements to match on. The special value "\*" matches all namespaces.

      `localName` - The local name of the elements to match on. The special value "\*" matches all local names.

      Returns:
      A new `NodeList` object containing all the matched `Elements`.

      Since:
      DOM Level 2

    <!-- -->

    - #### getElementById

          Element getElementById(java.lang.String elementId)

      Returns the `Element` whose `ID` is given by `elementId`. If no such element exists, returns `null`. Behavior is not defined if more than one element has this `ID`. The DOM implementation must have information that says which attributes are of type ID. Attributes with the name "ID" are not of type ID unless so defined. Implementations that do not know whether attributes are of type ID or not are expected to return `null`.
      Parameters:
      `elementId` - The unique `id` value for an element.

      Returns:
      The matching element.

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

- **[Prev Class](Comment.md)**
- **[Next Class](DocumentFragment.md)**

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
