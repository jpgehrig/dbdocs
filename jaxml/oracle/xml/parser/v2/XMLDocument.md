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

- **[Prev Class](XMLDeclPI.md)**
- **[Next Class](XMLDocumentFragment.md)**

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

## **Class XMLDocument**

- **java.lang.Object**

- - **[oracle.xml.parser.v2.XMLNode](XMLNode.md)**

  - - **[oracle.xml.parser.v2.XMLNSNode](XMLNSNode.md)**

    - - **[oracle.xml.parser.v2.XMLElement](XMLElement.md)**

      - - **oracle.xml.parser.v2.XMLDocument**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Externalizable, java.io.Serializable, java.lang.Cloneable, [NSResolver](NSResolver.md), [NSName](../../util/NSName.md), [Document](../../../../org/w3c/dom/Document.md), [Element](../../../../org/w3c/dom/Element.md), [DocumentEvent](../../../../org/w3c/dom/events/DocumentEvent.md), [EventTarget](../../../../org/w3c/dom/events/EventTarget.md), [Node](../../../../org/w3c/dom/Node.md), [DocumentTraversal](../../../../org/w3c/dom/traversal/DocumentTraversal.md), [DocumentEditVAL](../../../../org/w3c/dom/validation/DocumentEditVAL.md), [ElementEditVAL](../../../../org/w3c/dom/validation/ElementEditVAL.md), [NodeEditVAL](../../../../org/w3c/dom/validation/NodeEditVAL.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XMLDocument
      extends XMLElement
      implements Document, java.io.Externalizable, DocumentTraversal, DocumentEvent, DocumentEditVAL, EventTarget

  **This class implements the DOM Document interface, represents an entire XML document and serves the root of the Document Object Model tree. Each XML tag can either represent a node or a leaf of this tree.**
  **According to the XML specification, the root of the tree consists of any combination of comments and processing instructions, but only one root element. A helper method `getDocumentElement` is provided as a short cut to finding the root element.**

  **See Also:**
  **[Serialized Form](../../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description |
    |---------------------------|-----------------------|
    | `static java.lang.String` | `ACCESS_MODE`         |
    | `static int`              | `COMPACT_OFF`         |
    | `static java.lang.String` | `FORWARD_READ`        |
    | `static java.lang.String` | `READ_ONLY`           |
    | `static java.lang.String` | `SCALABLE_DOM`        |
    | `static java.lang.String` | `STREAM_READ`         |
    | `static java.lang.String` | `THICK`               |
    | `static java.lang.String` | `THIN`                |
    | `static java.lang.String` | `UPDATEABLE`          |

    -

      ### **Fields inherited from class oracle.xml.parser.v2.[XMLElement](XMLElement.md)**

      **[`ANY_CONTENTTYPE`](XMLElement.md)`, `[`ELEMENTS_CONTENTTYPE`](XMLElement.md)`, `[`EMPTY_CONTENTTYPE`](XMLElement.md)`, `[`MIXED_CONTENTTYPE`](XMLElement.md)**

    <!-- -->

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

      ### **Fields inherited from interface org.w3c.dom.validation.[ElementEditVAL](../../../../org/w3c/dom/validation/ElementEditVAL.md)**

      **[`VAL_ANY_CONTENTTYPE`](../../../../org/w3c/dom/validation/ElementEditVAL.md)`, `[`VAL_ELEMENTS_CONTENTTYPE`](../../../../org/w3c/dom/validation/ElementEditVAL.md)`, `[`VAL_EMPTY_CONTENTTYPE`](../../../../org/w3c/dom/validation/ElementEditVAL.md)`, `[`VAL_MIXED_CONTENTTYPE`](../../../../org/w3c/dom/validation/ElementEditVAL.md)`, `[`VAL_SIMPLE_CONTENTTYPE`](../../../../org/w3c/dom/validation/ElementEditVAL.md)**

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                     |
    |-------------------------------------------------|
    | `XMLDocument``()`<br>Creates an empty document. |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                           | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                   |
    |-----------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                      | `addID``(java.lang.String name, `[`XMLElement`](XMLElement.md)` e)`<br>Add a ID Element associated with this document                                                                                                                                                                                                                                                                                                                    |
    | [`Node`](../../../../org/w3c/dom/Node.md)                                   | `adoptNode``(`[`Node`](../../../../org/w3c/dom/Node.md)` srcNodeArg)`<br>Adopts a node from another document to this document.                                                                                                                                                                                                                                                                                                           |
    | [`Node`](../../../../org/w3c/dom/Node.md)                                   | `appendChild``(`[`Node`](../../../../org/w3c/dom/Node.md)` elem)`<br>Appends a new node to the document                                                                                                                                                                                                                                                                                                                                  |
    | `short`                                                                     | `canAppendChild``(`[`Node`](../../../../org/w3c/dom/Node.md)` newChild)`<br>Determines whether the `Node.appendChild` operation would make this document not compliant with the `VAL_INCOMPLETE` validity type.                                                                                                                                                                                                                          |
    | `short`                                                                     | `canInsertBefore``(`[`Node`](../../../../org/w3c/dom/Node.md)` newChild, `[`Node`](../../../../org/w3c/dom/Node.md)` refChild)`<br>Determines whether the `Node.insertBefore` operation would make this document not compliant with the `VAL_INCOMPLETE` validity type.                                                                                                                                                                  |
    | `short`                                                                     | `canRemoveChild``(`[`Node`](../../../../org/w3c/dom/Node.md)` oldChild)`<br>Determines whether the `Node.removeChild` operation would make this document not compliant with the `VAL_INCOMPLETE` validity type.                                                                                                                                                                                                                          |
    | `short`                                                                     | `canReplaceChild``(`[`Node`](../../../../org/w3c/dom/Node.md)` newChild, `[`Node`](../../../../org/w3c/dom/Node.md)` oldChild)`<br>Determines whether the `Node.replaceChild` operation would make this document not compliant with the `VAL_INCOMPLETE` validity type.                                                                                                                                                                  |
    | [`Attr`](../../../../org/w3c/dom/Attr.md)                                   | `createAttribute``(java.lang.String name)`<br>Creates an `Attr` of the given name.                                                                                                                                                                                                                                                                                                                                                       |
    | [`Attr`](../../../../org/w3c/dom/Attr.md)                                   | `createAttributeNS``(java.lang.String namespaceURI, java.lang.String qualifiedName)`<br>Creates an attribute with the given qualified name and namespace URI.                                                                                                                                                                                                                                                                            |
    | [`CDATASection`](../../../../org/w3c/dom/CDATASection.md)                   | `createCDATASection``(java.lang.String data)`<br>Creates a `CDATASection` node whose value is the specified string.                                                                                                                                                                                                                                                                                                                      |
    | [`Comment`](../../../../org/w3c/dom/Comment.md)                             | `createComment``(java.lang.String data)`<br>Creates a `Comment` node given the specified string.                                                                                                                                                                                                                                                                                                                                         |
    | [`DocumentFragment`](../../../../org/w3c/dom/DocumentFragment.md)           | `createDocumentFragment``()`<br>Creates an empty `DocumentFragment` object.                                                                                                                                                                                                                                                                                                                                                              |
    | [`Element`](../../../../org/w3c/dom/Element.md)                             | `createElement``(java.lang.String tagName)`<br>Creates an element of the type specified.                                                                                                                                                                                                                                                                                                                                                 |
    | [`Element`](../../../../org/w3c/dom/Element.md)                             | `createElementNS``(java.lang.String namespaceURI, java.lang.String qualifiedName)`<br>Creates an element of the given qualified name and namespace URI.                                                                                                                                                                                                                                                                                  |
    | [`EntityReference`](../../../../org/w3c/dom/EntityReference.md)             | `createEntityReference``(java.lang.String name)`<br>Creates an EntityReference object.                                                                                                                                                                                                                                                                                                                                                   |
    | [`Event`](../../../../org/w3c/dom/events/Event.md)                          | `createEvent``(java.lang.String type)`<br>Creates an event object of the specified type                                                                                                                                                                                                                                                                                                                                                  |
    | [`MutationEvent`](../../../../org/w3c/dom/events/MutationEvent.md)          | `createMutationEvent``(java.lang.String type)`<br>Creates a Mutation Event object of specified type                                                                                                                                                                                                                                                                                                                                      |
    | [`NodeIterator`](../../../../org/w3c/dom/traversal/NodeIterator.md)         | `createNodeIterator``(`[`Node`](../../../../org/w3c/dom/Node.md)` root, int whatToShow, `[`NodeFilter`](../../../../org/w3c/dom/traversal/NodeFilter.md)` filter, boolean expandEntityReferences)`<br>Creates a Node Iterator with specified root, flag which governs what type of nodes it should include in logical view, filter for filtering nodes, flag determining whether entity references and its descendants could be included |
    | [`ProcessingInstruction`](../../../../org/w3c/dom/ProcessingInstruction.md) | `createProcessingInstruction``(java.lang.String target, java.lang.String data)`<br>Creates a `ProcessingInstruction` node given the specified name and data strings.                                                                                                                                                                                                                                                                     |
    | [`Range`](../../../../org/w3c/dom/ranges/Range.md)                          | `createRange``()`<br>Create a new Document Range Object, with Start and End Boundary points at the begining of the document.                                                                                                                                                                                                                                                                                                             |
    | [`Event`](../../../../org/w3c/dom/events/Event.md)                          | `createRangeEvent``(java.lang.String type)`<br>Creates a Range Event object of specified type                                                                                                                                                                                                                                                                                                                                            |
    | [`Text`](../../../../org/w3c/dom/Text.md)                                   | `createTextNode``(java.lang.String data)`<br>Creates a `Text` node given the specified string.                                                                                                                                                                                                                                                                                                                                           |
    | [`Event`](../../../../org/w3c/dom/events/Event.md)                          | `createTraversalEvent``(java.lang.String type)`<br>Creates a Traversal Event object of specified type                                                                                                                                                                                                                                                                                                                                    |
    | [`TreeWalker`](../../../../org/w3c/dom/traversal/TreeWalker.md)             | `createTreeWalker``(`[`Node`](../../../../org/w3c/dom/Node.md)` root, int whatToShow, `[`NodeFilter`](../../../../org/w3c/dom/traversal/NodeFilter.md)` filter, boolean expandEntityReferences)`<br>Creates a Node Iterator with specified root, flag which governs what type of nodes it should include in logical view, filter for filtering nodes, flag determining whether entity references and its descendants could be included   |
    | `java.util.Vector`                                                          | `expectedElements``(`[`Element`](../../../../org/w3c/dom/Element.md)` e)`<br>Returns vector of element names that can be appended to the element.                                                                                                                                                                                                                                                                                        |
    | [`NamedNodeMap`](../../../../org/w3c/dom/NamedNodeMap.md)                   | `getAttributes``()`<br>A `NamedNodeMap` containing the attributes of this node (if it is an `Element`) or `null` otherwise.                                                                                                                                                                                                                                                                                                              |
    | `int`                                                                       | `getColumnNumber``()`<br>Get column number debug information                                                                                                                                                                                                                                                                                                                                                                             |
    | `boolean`                                                                   | `getContinuousValidityChecking``()`<br>An attribute specifying whether the validity of the document is continuously enforced.                                                                                                                                                                                                                                                                                                            |
    | `boolean`                                                                   | `getDebugMode``()`<br>Get the debug flag                                                                                                                                                                                                                                                                                                                                                                                                 |
    | [`NameList`](../../../../org/w3c/dom/NameList.md)                           | `getDefinedElements``(java.lang.String namespaceURI)`<br>Returns list of all element information item names of global declaration, belonging to the specified namespace.                                                                                                                                                                                                                                                                 |
    | [`DocumentType`](../../../../org/w3c/dom/DocumentType.md)                   | `getDoctype``()`<br>The Document Type Declaration (DTD) associated with this document.                                                                                                                                                                                                                                                                                                                                                   |
    | [`Element`](../../../../org/w3c/dom/Element.md)                             | `getDocumentElement``()`<br>This is a convenience attribute that allows direct access to the child node that is the root element of the document.                                                                                                                                                                                                                                                                                        |
    | [`Element`](../../../../org/w3c/dom/Element.md)                             | `getElementById``(java.lang.String elementId)`<br>Returns the Element whose ID is given by elementId.                                                                                                                                                                                                                                                                                                                                    |
    | [`NodeList`](../../../../org/w3c/dom/NodeList.md)                           | `getElementsByTagName``(java.lang.String tagname)`<br>Returns a `NodeList` of all the `Element`s with a given tag name in the order in which they would be encountered in a preorder traversal of the `Document` tree.                                                                                                                                                                                                                   |
    | [`NodeList`](../../../../org/w3c/dom/NodeList.md)                           | `getElementsByTagNameNS``(java.lang.String namespaceURI, java.lang.String localName)`<br>Returns a NodeList of all the Elements with a given local name and namespace URI in the order in which they are encountered in a preorder traversal of the Document tree.                                                                                                                                                                       |
    | `java.lang.String`                                                          | `getEncoding``()`<br>Retrieves the character encoding information.                                                                                                                                                                                                                                                                                                                                                                       |
    | [`XMLElement`](XMLElement.md)                                               | `getIDElement``(java.lang.String idValue)`<br>Deprecated. <br>As of DOM 2                                                                                                                                                                                                                                                                                                                                                                |
    | `java.util.Hashtable`                                                       | `getIDHashtable``()`<br>Get the ID element hashtable in the XML DOM Tree                                                                                                                                                                                                                                                                                                                                                                 |
    | [`DOMImplementation`](../../../../org/w3c/dom/DOMImplementation.md)         | `getImplementation``()`<br>The `DOMImplementation` object that handles this document.                                                                                                                                                                                                                                                                                                                                                    |
    | `int`                                                                       | `getLineNumber``()`<br>Get line number debug information                                                                                                                                                                                                                                                                                                                                                                                 |
    | `java.lang.String`                                                          | `getLocalName``()`<br>Gets the local Name for this element.                                                                                                                                                                                                                                                                                                                                                                              |
    | `java.lang.String`                                                          | `getNamespaceURI``()`<br>Gets the namespace URI of this node.                                                                                                                                                                                                                                                                                                                                                                            |
    | [`Node`](../../../../org/w3c/dom/Node.md)                                   | `getNextSibling``()`<br>Gets The node immediately following this node.                                                                                                                                                                                                                                                                                                                                                                   |
    | `java.lang.String`                                                          | `getNodeName``()`<br>Gets a name of the node                                                                                                                                                                                                                                                                                                                                                                                             |
    | `short`                                                                     | `getNodeType``()`<br>Gets a code representing the type of the underlying object                                                                                                                                                                                                                                                                                                                                                          |
    | [`Document`](../../../../org/w3c/dom/Document.md)                           | `getOwnerDocument``()`<br>The `Document` object associated with this node.                                                                                                                                                                                                                                                                                                                                                               |
    | [`Node`](../../../../org/w3c/dom/Node.md)                                   | `getParentNode``()`<br>Gets the parent of this node.                                                                                                                                                                                                                                                                                                                                                                                     |
    | [`Node`](../../../../org/w3c/dom/Node.md)                                   | `getPreviousSibling``()`<br>Gets the node immediately preceding this node.                                                                                                                                                                                                                                                                                                                                                               |
    | [`XMLSchema`](../schema/XMLSchema.md)                                       | `getSchema``()`<br>return the validator                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `java.lang.String`                                                          | `getStandalone``()`<br>Retrieves the standalone information.                                                                                                                                                                                                                                                                                                                                                                             |
    | `java.lang.String`                                                          | `getSystemId``()`<br>Get the system id of the entity contain this node                                                                                                                                                                                                                                                                                                                                                                   |
    | `java.lang.String`                                                          | `getText``()`<br>Returns the non-marked-up text contained by this element.                                                                                                                                                                                                                                                                                                                                                               |
    | `java.lang.String`                                                          | `getVersion``()`<br>Retrieves the version information.                                                                                                                                                                                                                                                                                                                                                                                   |
    | [`XMLNode`](XMLNode.md)                                                     | `getXMLNodeFromNode``(`[`Node`](../../../../org/w3c/dom/Node.md)` node)`                                                                                                                                                                                                                                                                                                                                                                 |
    | [`XMLNode`](XMLNode.md)                                                     | `importBinary``(`[`BinaryNav`](../../scalable/BinaryNav.md)` nav)`<br>Import binary from a binaryNav Create corresponding Element node                                                                                                                                                                                                                                                                                                   |
    | [`Node`](../../../../org/w3c/dom/Node.md)                                   | `importNode``(`[`Node`](../../../../org/w3c/dom/Node.md)` importedNode, boolean deep)`<br>Imports a node from another document to this document.                                                                                                                                                                                                                                                                                         |
    | [`Node`](../../../../org/w3c/dom/Node.md)                                   | `importNode``(`[`Node`](../../../../org/w3c/dom/Node.md)` context, java.lang.String pattern)`<br>Import node selected by given xpath from the context On Scalable DOM, if the xpath is streamable, the evaluation will switch to streaming xpath, avoid massive node materialization                                                                                                                                                     |
    | [`Node`](../../../../org/w3c/dom/Node.md)                                   | `insertBefore``(`[`Node`](../../../../org/w3c/dom/Node.md)` newChild, `[`Node`](../../../../org/w3c/dom/Node.md)` refChild)`<br>Inserts the node `newChild` before the existing child node `refChild`.                                                                                                                                                                                                                                   |
    | `short`                                                                     | `nodeValidity``(short wFValidityCheckLevel)`<br>Determines if the node is valid relative to the validation type specified in `valType`.                                                                                                                                                                                                                                                                                                  |
    | `void`                                                                      | `print``(java.io.OutputStream out)`<br>Writes the contents of this document to the given output stream.                                                                                                                                                                                                                                                                                                                                  |
    | `void`                                                                      | `print``(java.io.OutputStream out, java.lang.String enc)`<br>Writes the contents of this document to the given output stream.                                                                                                                                                                                                                                                                                                            |
    | `void`                                                                      | `print``(`[`PrintDriver`](PrintDriver.md)` pd)`<br>Writes the contents of this document to the given output stream.                                                                                                                                                                                                                                                                                                                      |
    | `void`                                                                      | `print``(java.io.PrintWriter out)`<br>Writes the contents of this document to the given output stream.                                                                                                                                                                                                                                                                                                                                   |
    | `void`                                                                      | `print``(java.io.Writer out)`<br>Writes the contents of this document to the given output stream.                                                                                                                                                                                                                                                                                                                                        |
    | `void`                                                                      | `printExternalDTD``(java.io.OutputStream out)`<br>Writes the contents of this document to the given output stream.                                                                                                                                                                                                                                                                                                                       |
    | `void`                                                                      | `printExternalDTD``(java.io.OutputStream out, java.lang.String enc)`<br>Writes the contents of the external DTD to the given output stream.                                                                                                                                                                                                                                                                                              |
    | `void`                                                                      | `printExternalDTD``(java.io.PrintWriter out)`<br>Writes the contents of this document to the given output stream.                                                                                                                                                                                                                                                                                                                        |
    | [`Node`](../../../../org/w3c/dom/Node.md)                                   | `removeChild``(`[`Node`](../../../../org/w3c/dom/Node.md)` elem)`<br>removes the elem from this documents list of child nodes                                                                                                                                                                                                                                                                                                            |
    | [`Node`](../../../../org/w3c/dom/Node.md)                                   | `replaceChild``(`[`Node`](../../../../org/w3c/dom/Node.md)` newChild, `[`Node`](../../../../org/w3c/dom/Node.md)` oldChild)`<br>Replaces the child node `oldChild` with `newChild` in the list of children, and returns the `oldChild` node.                                                                                                                                                                                             |
    | `void`                                                                      | `reportSAXEvents``(`[`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)` cntHandler)`<br>Report SAX Events from a DOM Tree                                                                                                                                                                                                                                                                                                     |
    | `void`                                                                      | `save``(`[`InfosetWriter`](../../scalable/InfosetWriter.md)` writer)`                                                                                                                                                                                                                                                                                                                                                                    |
    | `void`                                                                      | `save``(`[`InfosetWriter`](../../scalable/InfosetWriter.md)` writer, boolean ref)`<br>Serialize DOM using InfosetWriter                                                                                                                                                                                                                                                                                                                  |
    | `void`                                                                      | `setContinuousValidityChecking``(boolean continuousValidityChecking)`<br>An attribute specifying whether the validity of the document is continuously enforced.                                                                                                                                                                                                                                                                          |
    | `void`                                                                      | `setDoctype``(java.lang.String rootname, java.lang.String sysid, java.lang.String pubid)`<br>Sets the doctype URI for the document                                                                                                                                                                                                                                                                                                       |
    | `void`                                                                      | `setEncoding``(java.lang.String encoding)`<br>Sets the character encoding for output.                                                                                                                                                                                                                                                                                                                                                    |
    | `void`                                                                      | `setLocale``(java.util.Locale locale)`<br>Sets the locale for error reporting                                                                                                                                                                                                                                                                                                                                                            |
    | `void`                                                                      | `setParsedDoctype``(java.lang.String rootname, java.lang.String sysid, java.lang.String pubid)`<br>Sets the doctype object by parsing sysid                                                                                                                                                                                                                                                                                              |
    | `void`                                                                      | `setSchema``(`[`XMLSchema`](../schema/XMLSchema.md)` schema)`<br>set the XML Schema                                                                                                                                                                                                                                                                                                                                                      |
    | `void`                                                                      | `setStandalone``(java.lang.String value)`<br>Sets the standalone information stored in the \<?                                                                                                                                                                                                                                                                                                                                           |
    | `void`                                                                      | `setVersion``(java.lang.String version)`<br>Sets the version number stored in the \<?                                                                                                                                                                                                                                                                                                                                                    |
    | `short`                                                                     | `validateDocument``()`<br>Validates the document against the schema, e.g., a DTD or an XML Schema or another.                                                                                                                                                                                                                                                                                                                            |
    | `boolean`                                                                   | `validateElementContent``(`[`Element`](../../../../org/w3c/dom/Element.md)` e)`<br>Validates the content of a element node.                                                                                                                                                                                                                                                                                                              |

    - ### Methods inherited from class oracle.xml.parser.v2.[XMLElement](XMLElement.md)

      [`canRemoveAttribute`](XMLElement.md)`, `[`canRemoveAttributeNode`](XMLElement.md)`, `[`canRemoveAttributeNS`](XMLElement.md)`, `[`canSetAttribute`](XMLElement.md)`, `[`canSetAttributeNode`](XMLElement.md)`, `[`canSetAttributeNS`](XMLElement.md)`, `[`canSetTextContent`](XMLElement.md)`, `[`getAllowedAttributes`](XMLElement.md)`, `[`getAllowedChildren`](XMLElement.md)`, `[`getAllowedFirstChildren`](XMLElement.md)`, `[`getAllowedNextSiblings`](XMLElement.md)`, `[`getAllowedParents`](XMLElement.md)`, `[`getAllowedPreviousSiblings`](XMLElement.md)`, `[`getAttribute`](XMLElement.md)`, `[`getAttributeNode`](XMLElement.md)`, `[`getAttributeNode`](XMLElement.md)`, `[`getAttributeNodeNS`](XMLElement.md)`, `[`getAttributeNS`](XMLElement.md)`, `[`getChildrenByTagName`](XMLElement.md)`, `[`getChildrenByTagName`](XMLElement.md)`, `[`getContentType`](XMLElement.md)`, `[`getDefaultValue`](XMLElement.md)`, `[`getEnumeratedValues`](XMLElement.md)`, `[`getExpandedName`](XMLElement.md)`, `[`getFirstAttribute`](XMLElement.md)`, `[`getNextSiblingByName`](XMLElement.md)`, `[`getPrefix`](XMLElement.md)`, `[`getQualifiedName`](XMLElement.md)`, `[`getRequiredAttributes`](XMLElement.md)`, `[`getTagName`](XMLElement.md)`, `[`hasAttribute`](XMLElement.md)`, `[`hasAttributeNS`](XMLElement.md)`, `[`hasAttributes`](XMLElement.md)`, `[`isElementDefined`](XMLElement.md)`, `[`isElementDefinedNS`](XMLElement.md)`, `[`normalize`](XMLElement.md)`, `[`removeAttribute`](XMLElement.md)`, `[`removeAttributeNode`](XMLElement.md)`, `[`removeAttributeNS`](XMLElement.md)`, `[`resolveNamespacePrefix`](XMLElement.md)`, `[`setAttribute`](XMLElement.md)`, `[`setAttributeNode`](XMLElement.md)`, `[`setAttributeNodeNS`](XMLElement.md)`, `[`setAttributeNS`](XMLElement.md)`, `[`setPrefix`](XMLElement.md)`, `[`validateContent`](XMLElement.md)`, `[`validateContent`](XMLElement.md)`, `[`validateContent`](XMLElement.md)`, `[`validateContent`](XMLElement.md)

    <!-- -->

    - ### Methods inherited from class oracle.xml.parser.v2.[XMLNSNode](XMLNSNode.md)

      [`addText`](XMLNSNode.md)`, `[`addText`](XMLNSNode.md)`, `[`getChildNodes`](XMLNSNode.md)`, `[`getFirstChild`](XMLNSNode.md)`, `[`getLastChild`](XMLNSNode.md)

    <!-- -->

    - ### Methods inherited from class oracle.xml.parser.v2.[XMLNode](XMLNode.md)

      [`addEventListener`](XMLNode.md)`, `[`cloneNode`](XMLNode.md)`, `[`dispatchEvent`](XMLNode.md)`, `[`equals`](XMLNode.md)`, `[`getFirstChildAsOffset`](XMLNode.md)`, `[`getNextSiblingAsOffset`](XMLNode.md)`, `[`getNodeValue`](XMLNode.md)`, `[`getNodeValueAsBinaryStream`](XMLNode.md)`, `[`getNodeValueAsBinaryStream`](XMLNode.md)`, `[`getNodeValueAsCharacterStream`](XMLNode.md)`, `[`getNodeValueAsCharacterStream`](XMLNode.md)`, `[`getPrimitiveTypeId`](XMLNode.md)`, `[`getProperty`](XMLNode.md)`, `[`getXMLError`](XMLNode.md)`, `[`hasChildNodes`](XMLNode.md)`, `[`hashCode`](XMLNode.md)`, `[`isDocumentFlag`](XMLNode.md)`, `[`isNodeFlag`](XMLNode.md)`, `[`isSupported`](XMLNode.md)`, `[`readExternal`](XMLNode.md)`, `[`removeEventListener`](XMLNode.md)`, `[`resetNodeFlag`](XMLNode.md)`, `[`selectNodes`](XMLNode.md)`, `[`selectNodes`](XMLNode.md)`, `[`selectSingleNode`](XMLNode.md)`, `[`selectSingleNode`](XMLNode.md)`, `[`setDebugInfo`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeValue`](XMLNode.md)`, `[`setNodeValueAsBinaryStream`](XMLNode.md)`, `[`setNodeValueAsBinaryStream`](XMLNode.md)`, `[`setNodeValueAsCharacterStream`](XMLNode.md)`, `[`setNodeValueAsCharacterStream`](XMLNode.md)`, `[`setProperty`](XMLNode.md)`, `[`transformNode`](XMLNode.md)`, `[`valueOf`](XMLNode.md)`, `[`valueOf`](XMLNode.md)`, `[`writeExternal`](XMLNode.md)`, `[`xdbGetNodeId`](XMLNode.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface org.w3c.dom.[Node](../../../../org/w3c/dom/Node.md)

      [`cloneNode`](../../../../org/w3c/dom/Node.md)`, `[`getChildNodes`](../../../../org/w3c/dom/Node.md)`, `[`getFirstChild`](../../../../org/w3c/dom/Node.md)`, `[`getLastChild`](../../../../org/w3c/dom/Node.md)`, `[`getNodeValue`](../../../../org/w3c/dom/Node.md)`, `[`getPrefix`](../../../../org/w3c/dom/Node.md)`, `[`hasAttributes`](../../../../org/w3c/dom/Node.md)`, `[`hasChildNodes`](../../../../org/w3c/dom/Node.md)`, `[`isSupported`](../../../../org/w3c/dom/Node.md)`, `[`normalize`](../../../../org/w3c/dom/Node.md)`, `[`setNodeValue`](../../../../org/w3c/dom/Node.md)`, `[`setPrefix`](../../../../org/w3c/dom/Node.md)

    <!-- -->

    - ### Methods inherited from interface java.io.Externalizable

      `readExternal, writeExternal`

    <!-- -->

    - ### Methods inherited from interface org.w3c.dom.validation.[DocumentEditVAL](../../../../org/w3c/dom/validation/DocumentEditVAL.md)

      [`setContinuousValidityChecking`](../../../../org/w3c/dom/validation/DocumentEditVAL.md)

    <!-- -->

    - ### Methods inherited from interface org.w3c.dom.validation.[NodeEditVAL](../../../../org/w3c/dom/validation/NodeEditVAL.md)

      [`getDefaultValue`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`getEnumeratedValues`](../../../../org/w3c/dom/validation/NodeEditVAL.md)

    <!-- -->

    - ### Methods inherited from interface org.w3c.dom.events.[EventTarget](../../../../org/w3c/dom/events/EventTarget.md)

      [`addEventListener`](../../../../org/w3c/dom/events/EventTarget.md)`, `[`dispatchEvent`](../../../../org/w3c/dom/events/EventTarget.md)`, `[`removeEventListener`](../../../../org/w3c/dom/events/EventTarget.md)

    <!-- -->

    - ### Methods inherited from interface oracle.xml.util.[NSName](../../util/NSName.md)

      [`getNamespace`](../../util/NSName.md)

    <!-- -->

    - ### Methods inherited from interface org.w3c.dom.validation.[ElementEditVAL](../../../../org/w3c/dom/validation/ElementEditVAL.md)

      [`getAllowedFirstChildElements`](../../../../org/w3c/dom/validation/ElementEditVAL.md)

<!-- -->

- - ### Field Detail

    - #### COMPACT_OFF

          public static final int COMPACT_OFF

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### THICK

          public static final java.lang.String THICK

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### THIN

          public static final java.lang.String THIN

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ACCESS_MODE

          public static final java.lang.String ACCESS_MODE

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### UPDATEABLE

          public static final java.lang.String UPDATEABLE

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### READ_ONLY

          public static final java.lang.String READ_ONLY

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### FORWARD_READ

          public static final java.lang.String FORWARD_READ

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### STREAM_READ

          public static final java.lang.String STREAM_READ

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### SCALABLE_DOM

          public static final java.lang.String SCALABLE_DOM

      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### XMLDocument

          public XMLDocument()

      Creates an empty document.

  <!-- -->

  - ### Method Detail

    - #### save

          public void save(InfosetWriter writer)
                    throws java.io.IOException

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### save

          public void save(InfosetWriter writer,
                           boolean ref)
                    throws java.io.IOException

      Serialize DOM using InfosetWriter
      Parameters:
      `writer` - The InfosetWriter to use

      `ref` - indicate fully serialization or allow references

      Throws:
      `java.io.IOException`

    <!-- -->

    - #### getDoctype

          public DocumentType getDoctype()

      The Document Type Declaration (DTD) associated with this document. For XML documents without a DTD, this returns `null`. Note that the DOM Level 1 specification does not support editing the DTD.
      Specified by:
      [`getDoctype`](../../../../org/w3c/dom/Document.md) in interface [`Document`](../../../../org/w3c/dom/Document.md)

      Returns:
      The associated DTD

      See Also:
      [`DocumentType`](../../../../org/w3c/dom/DocumentType.md)

    <!-- -->

    - #### getNodeType

          public short getNodeType()

      Gets a code representing the type of the underlying object
      Specified by:
      [`getNodeType`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`getNodeType`](XMLElement.md) in class [`XMLElement`](XMLElement.md)

      Returns:
      type of the node

    <!-- -->

    - #### getNodeName

          public java.lang.String getNodeName()

      Gets a name of the node
      Specified by:
      [`getNodeName`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`getNodeName`](XMLElement.md) in class [`XMLElement`](XMLElement.md)

      Returns:
      name of the node

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

    - #### getImplementation

          public DOMImplementation getImplementation()

      The `DOMImplementation` object that handles this document. A DOM application may use objects from multiple implementations.
      Specified by:
      [`getImplementation`](../../../../org/w3c/dom/Document.md) in interface [`Document`](../../../../org/w3c/dom/Document.md)

      Returns:
      The associated DOM implementation.

    <!-- -->

    - #### getNamespaceURI

          public java.lang.String getNamespaceURI()

      Description copied from class: [`XMLElement`](XMLElement.md)
      Gets the namespace URI of this node.
      Specified by:
      [`getNamespaceURI`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`getNamespaceURI`](XMLElement.md) in class [`XMLElement`](XMLElement.md)

      Returns:
      the namespace URI of this element

      Since:
      DOM 2 Gets the name space URI of this element

    <!-- -->

    - #### getLocalName

          public java.lang.String getLocalName()

      Gets the local Name for this element.
      Specified by:
      [`getLocalName`](../../util/NSName.md) in interface [`NSName`](../../util/NSName.md)

      Specified by:
      [`getLocalName`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`getLocalName`](XMLElement.md) in class [`XMLElement`](XMLElement.md)

      Returns:
      the local Name

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

    - #### getAttributes

          public NamedNodeMap getAttributes()

      Description copied from class: [`XMLElement`](XMLElement.md)
      A `NamedNodeMap` containing the attributes of this node (if it is an `Element`) or `null` otherwise.
      Specified by:
      [`getAttributes`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`getAttributes`](XMLElement.md) in class [`XMLElement`](XMLElement.md)

      Returns:
      always null

    <!-- -->

    - #### getDocumentElement

          public Element getDocumentElement()

      This is a convenience attribute that allows direct access to the child node that is the root element of the document.
      Specified by:
      [`getDocumentElement`](../../../../org/w3c/dom/Document.md) in interface [`Document`](../../../../org/w3c/dom/Document.md)

      Returns:
      The root element

    <!-- -->

    - #### getOwnerDocument

          public Document getOwnerDocument()

      The `Document` object associated with this node. Since this node is a `Document` this is `null`.
      Specified by:
      [`getOwnerDocument`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`getOwnerDocument`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Returns:
      `null`

    <!-- -->

    - #### createElement

          public Element createElement(java.lang.String tagName)
                                throws DOMException

      Creates an element of the type specified. Note that the instance returned implements the Element interface, so attributes can be specified directly on the returned object.
      Specified by:
      [`createElement`](../../../../org/w3c/dom/Document.md) in interface [`Document`](../../../../org/w3c/dom/Document.md)

      Parameters:
      `tagName` - The name of the element type to instantiate. The name is treated as case-sensitive.

      Returns:
      A new `Element` object.

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - INVALID_CHARACTER_ERR: Raised if the specified name contains an invalid character.

    <!-- -->

    - #### createDocumentFragment

          public DocumentFragment createDocumentFragment()

      Creates an empty `DocumentFragment` object.
      Specified by:
      [`createDocumentFragment`](../../../../org/w3c/dom/Document.md) in interface [`Document`](../../../../org/w3c/dom/Document.md)

      Returns:
      A new `DocumentFragment`.

    <!-- -->

    - #### createTextNode

          public Text createTextNode(java.lang.String data)

      Creates a `Text` node given the specified string.
      Specified by:
      [`createTextNode`](../../../../org/w3c/dom/Document.md) in interface [`Document`](../../../../org/w3c/dom/Document.md)

      Parameters:
      `data` - The data for the node.

      Returns:
      The new `Text` object.

    <!-- -->

    - #### createComment

          public Comment createComment(java.lang.String data)

      Creates a `Comment` node given the specified string.
      Specified by:
      [`createComment`](../../../../org/w3c/dom/Document.md) in interface [`Document`](../../../../org/w3c/dom/Document.md)

      Parameters:
      `data` - The data for the node.

      Returns:
      The new `Comment` object.

    <!-- -->

    - #### createCDATASection

          public CDATASection createCDATASection(java.lang.String data)
                                          throws DOMException

      Creates a `CDATASection` node whose value is the specified string.
      Specified by:
      [`createCDATASection`](../../../../org/w3c/dom/Document.md) in interface [`Document`](../../../../org/w3c/dom/Document.md)

      Parameters:
      `data` - The data for the `CDATASection` contents.

      Returns:
      The new `CDATASection` object.

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - A `DOMException` could be thrown.

    <!-- -->

    - #### createProcessingInstruction

          public ProcessingInstruction createProcessingInstruction(java.lang.String target,
                                                                   java.lang.String data)
                                                            throws DOMException

      Creates a `ProcessingInstruction` node given the specified name and data strings.
      Specified by:
      [`createProcessingInstruction`](../../../../org/w3c/dom/Document.md) in interface [`Document`](../../../../org/w3c/dom/Document.md)

      Parameters:
      `target` - The target part of the processing instruction.

      `data` - The data for the node.

      Returns:
      The new `ProcessingInstruction` object.

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - INVALID_CHARACTER_ERR: Raised if an invalid character is specified.

    <!-- -->

    - #### createAttribute

          public Attr createAttribute(java.lang.String name)
                               throws DOMException

      Creates an `Attr` of the given name. Note that the `Attr` instance can then be set on an `Element` using the `setAttribute` method.
      Specified by:
      [`createAttribute`](../../../../org/w3c/dom/Document.md) in interface [`Document`](../../../../org/w3c/dom/Document.md)

      Parameters:
      `name` - The name of the attribute.

      Returns:
      A new `Attr` object.

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - INVALID_CHARACTER_ERR: Raised if the specified name contains an invalid character.

    <!-- -->

    - #### createEntityReference

          public EntityReference createEntityReference(java.lang.String name)
                                                throws DOMException

      Creates an EntityReference object.
      Specified by:
      [`createEntityReference`](../../../../org/w3c/dom/Document.md) in interface [`Document`](../../../../org/w3c/dom/Document.md)

      Parameters:
      `name` - The name of the entity to reference.

      Returns:
      The new `EntityReference` object.

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - INVALID_CHARACTER_ERR: Raised if the specified name contains an invalid character.

    <!-- -->

    - #### getElementsByTagName

          public NodeList getElementsByTagName(java.lang.String tagname)

      Returns a `NodeList` of all the `Element`s with a given tag name in the order in which they would be encountered in a preorder traversal of the `Document` tree.
      Specified by:
      [`getElementsByTagName`](../../../../org/w3c/dom/Document.md) in interface [`Document`](../../../../org/w3c/dom/Document.md)

      Specified by:
      [`getElementsByTagName`](../../../../org/w3c/dom/Element.md) in interface [`Element`](../../../../org/w3c/dom/Element.md)

      Overrides:
      [`getElementsByTagName`](XMLElement.md) in class [`XMLElement`](XMLElement.md)

      Parameters:
      `tagname` - The name of the tag to match on. The special value "\*" matches all tags.

      Returns:
      A new `NodeList` object containing all the matched `Element`s.

    <!-- -->

    - #### appendChild

          public Node appendChild(Node elem)
                           throws DOMException

      Appends a new node to the document
      Specified by:
      [`appendChild`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`appendChild`](XMLNSNode.md) in class [`XMLNSNode`](XMLNSNode.md)

      Parameters:
      `elem` - the new node to be added

      Returns:
      the node after appending it to the document

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - HIERARCHY_REQUEST_ERR: Raised if this node is of a type that does not allow children of the type of the `elem` node.
      WRONG_DOCUMENT_ERR: Raised if `elem` was created from a different document than this one.

    <!-- -->

    - #### replaceChild

          public Node replaceChild(Node newChild,
                                   Node oldChild)
                            throws DOMException

      Replaces the child node `oldChild` with `newChild` in the list of children, and returns the `oldChild` node. If the `newChild` is already in the tree, it is first removed. This is an override of the `XMLNode.removeChild` method
      Specified by:
      [`replaceChild`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`replaceChild`](XMLNSNode.md) in class [`XMLNSNode`](XMLNSNode.md)

      Parameters:
      `newChild` - The new node to put in the child list.

      `oldChild` - The node being replaced in the list.

      Returns:
      The node replaced.

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - HIERARCHY_REQUEST_ERR: Raised if this node is of a type that does not allow children of the type of the `newChild` node.
      WRONG_DOCUMENT_ERR: Raised if `newChild` was created from a different document than this one.
      NOT_FOUND_ERR: Raised if `oldChild` is not a child of this node.

    <!-- -->

    - #### removeChild

          public Node removeChild(Node elem)
                           throws DOMException

      removes the elem from this documents list of child nodes
      Specified by:
      [`removeChild`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`removeChild`](XMLNSNode.md) in class [`XMLNSNode`](XMLNSNode.md)

      Parameters:
      `elem` - the node to be removed

      Returns:
      the node after it's removed from the document

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - NO_MODIFICATION_ALLOWED_ERR: Raised if this document is readonly.
      NOT_FOUND_ERR: Raised if `oldChild` is not a child of this node.

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
      [`insertBefore`](XMLNSNode.md) in class [`XMLNSNode`](XMLNSNode.md)

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

    - #### setParsedDoctype

          public void setParsedDoctype(java.lang.String rootname,
                                       java.lang.String sysid,
                                       java.lang.String pubid)
                                throws DOMException

      Sets the doctype object by parsing sysid
      Parameters:
      `rootname` - The name of the root element

      `sysid` - The system id of the doctype

      `pubid` - The public id of the doctype (can be null)

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md)

    <!-- -->

    - #### setDoctype

          public void setDoctype(java.lang.String rootname,
                                 java.lang.String sysid,
                                 java.lang.String pubid)

      Sets the doctype URI for the document
      Parameters:
      `rootname` - The name of the root element

      `sysid` - The system id of the doctype

      `pubid` - The public id of the doctype (can be null)

    <!-- -->

    - #### addID

          public void addID(java.lang.String name,
                            XMLElement e)

      Add a ID Element associated with this document
      Parameters:
      `name` - String - id value

      `e` - XMLElement associated with id

    <!-- -->

    - #### getIDElement

          public XMLElement getIDElement(java.lang.String idValue)

      Deprecated. As of DOM 2
      Parameters:
      `idValue` -

      Returns:
      XMLElement associated with idvalue

      See Also:
      `Get the element in the XML DOM Tree with a given ID`

    <!-- -->

    - #### getIDHashtable

          public java.util.Hashtable getIDHashtable()

      Get the ID element hashtable in the XML DOM Tree
      Returns:
      Hashtable - associated with XMLDocument

    <!-- -->

    - #### getText

          public java.lang.String getText()

      Returns the non-marked-up text contained by this element. For text elements, this is the raw data. For elements with child nodes, this method traverses the entire subtree and appends the text for each terminal text element, effectively stripping out the XML markup for the subtree. For example, if the XML document contains the following: \<xmp\> \<AUTHOR\> \<FIRST\>William\</FIRST\> \<LAST\>Shakespeare\</LAST\> \</AUTHOR\> \</xmp\>
      `XMLDocument.getText` returns "William Shakespeare".

      Overrides:
      [`getText`](XMLNSNode.md) in class [`XMLNSNode`](XMLNSNode.md)

      Returns:
      non-marked-up text contained bu this element

    <!-- -->

    - #### print

          public void print(java.io.PrintWriter out)
                     throws java.io.IOException

      Writes the contents of this document to the given output stream.
      Overrides:
      [`print`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Parameters:
      `out` - `PrintWriter` to write to

      Throws:
      `java.io.IOException` - if an error occurs

    <!-- -->

    - #### print

          public void print(java.io.Writer out)
                     throws java.io.IOException

      Writes the contents of this document to the given output stream.
      Overrides:
      [`print`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Parameters:
      `out` - `Writer` to write to

      Throws:
      `java.io.IOException` - if an error occurs

    <!-- -->

    - #### print

          public void print(java.io.OutputStream out)
                     throws java.io.IOException

      Writes the contents of this document to the given output stream.
      Overrides:
      [`print`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Parameters:
      `out` - `OutputStream` to write to

      Throws:
      `java.io.IOException` - if an error occurs

    <!-- -->

    - #### print

          public void print(java.io.OutputStream out,
                            java.lang.String enc)
                     throws java.io.IOException

      Writes the contents of this document to the given output stream.
      Overrides:
      [`print`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Parameters:
      `out` - `OutputStream` to write to

      `enc` - Encoding to use for the output

      Throws:
      `java.io.IOException` - if an invalid encoding was specified or if any other error occurs

    <!-- -->

    - #### print

          public void print(PrintDriver pd)
                     throws java.io.IOException

      Writes the contents of this document to the given output stream.
      Parameters:
      `pd` - `PrintDriver` used to write each node

      Throws:
      `java.io.IOException` - if an error occurs

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

    - #### reportSAXEvents

          public void reportSAXEvents(ContentHandler cntHandler)
                               throws SAXException

      Report SAX Events from a DOM Tree
      Overrides:
      [`reportSAXEvents`](XMLElement.md) in class [`XMLElement`](XMLElement.md)

      Parameters:
      `cntHandler` - ContentHandler

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - thrown by SAX Callback functions

    <!-- -->

    - #### validateElementContent

          public boolean validateElementContent(Element e)

      Validates the content of a element node.
      Parameters:
      `e` - Element to be validated

      Returns:
      True if valid, else false

    <!-- -->

    - #### setLocale

          public final void setLocale(java.util.Locale locale)

      Sets the locale for error reporting
      Parameters:
      `locale` - Locale for error reporting.

    <!-- -->

    - #### expectedElements

          public java.util.Vector expectedElements(Element e)

      Returns vector of element names that can be appended to the element.
      Parameters:
      `e` - Element

      Returns:
      Vector of names

    <!-- -->

    - #### getVersion

          public java.lang.String getVersion()

      Retrieves the version information.
      Returns:
      the version number stored in the \<?xml ...?\> tag.

    <!-- -->

    - #### setVersion

          public void setVersion(java.lang.String version)

      Sets the version number stored in the \<?xml ...?\> tag.
      Parameters:
      `version` - The version information to set.

    <!-- -->

    - #### getEncoding

          public java.lang.String getEncoding()

      Retrieves the character encoding information.
      Returns:
      the encoding information stored in the \<?xml ...?\> tag or the user-defined output encoding if it has been more recently set or user-provided output encoding through command line option, -Doracle.xml.parser.default.character.set.

    <!-- -->

    - #### setEncoding

          public void setEncoding(java.lang.String encoding)

      Sets the character encoding for output. Eventually it sets the ENCODING stored in the \<?xml ...?\> tag, but not until the document is saved. You should not call this method until the Document has been loaded.
      Parameters:
      `encoding` - The character encoding to set

    <!-- -->

    - #### getStandalone

          public final java.lang.String getStandalone()

      Retrieves the standalone information.
      Returns:
      the standalone attribute stored in the \<?xml ...?\> tag.

    <!-- -->

    - #### setStandalone

          public void setStandalone(java.lang.String value)

      Sets the standalone information stored in the \<?xml ...?\> tag.
      Parameters:
      `value` - The attribute value ('yes' or 'no').

    <!-- -->

    - #### getDebugMode

          public boolean getDebugMode()

      Get the debug flag
      Overrides:
      [`getDebugMode`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Returns:
      boolean flag

    <!-- -->

    - #### getLineNumber

          public int getLineNumber()

      Get line number debug information
      Overrides:
      [`getLineNumber`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Returns:
      line the line number

    <!-- -->

    - #### getColumnNumber

          public int getColumnNumber()

      Get column number debug information
      Overrides:
      [`getColumnNumber`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Returns:
      column the column number

    <!-- -->

    - #### getSystemId

          public java.lang.String getSystemId()

      Get the system id of the entity contain this node
      Overrides:
      [`getSystemId`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Returns:
      sysid the system id

    <!-- -->

    - #### adoptNode

          public Node adoptNode(Node srcNodeArg)
                         throws DOMException

      Adopts a node from another document to this document. The returned node has no parent; (parentNode is null). The source node is removed from the original document;
      Parameters:
      `srcNodeArg` - Node to be adopted

      Returns:
      Node with document association updated

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - NOT_SUPPORTED_ERR: Raised if the type of the node being adopted is not supported.

    <!-- -->

    - #### importNode

          public Node importNode(Node importedNode,
                                 boolean deep)
                          throws DOMException

      Imports a node from another document to this document. The returned node has no parent; (parentNode is null). The source node is not altered or removed from the original document; this method creates a new copy of the source node.For all nodes, importing a node creates a node object owned by the importing document, with attribute values identical to the source node's nodeName and nodeType, plus the attributes related to namespaces (prefix, localName, and namespaceURI). As in the cloneNode operation on a Node, the source node is not altered.
      Specified by:
      [`importNode`](../../../../org/w3c/dom/Document.md) in interface [`Document`](../../../../org/w3c/dom/Document.md)

      Parameters:
      `importedNode` - Node to be imported

      `deep` - boolean variable indicating whether the descendants of this node are to be imported

      Returns:
      A copy of the importedNode which is attached to the current document but not a part of the document tree

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - NOT_SUPPORTED_ERR: Raised if the type of the node being imported is not supported.

      Since:
      DOM 2

    <!-- -->

    - #### importBinary

          public XMLNode importBinary(BinaryNav nav)

      Import binary from a binaryNav Create corresponding Element node
      Parameters:
      `nav` - - the navigator of the binary

      Returns:
      XMLNode - the XMLElement representing the element information

    <!-- -->

    - #### importNode

          public Node importNode(Node context,
                                 java.lang.String pattern)
                          throws DOMException,
                                 XSLException

      Import node selected by given xpath from the context On Scalable DOM, if the xpath is streamable, the evaluation will switch to streaming xpath, avoid massive node materialization
      Parameters:
      `context` - the context node for xpath

      `pattern` - the xpath to select the imported node

      Returns:
      A copy of imported node

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md)

      [`XSLException`](XSLException.md)

    <!-- -->

    - #### createElementNS

          public Element createElementNS(java.lang.String namespaceURI,
                                         java.lang.String qualifiedName)
                                  throws DOMException

      Creates an element of the given qualified name and namespace URI.
      Specified by:
      [`createElementNS`](../../../../org/w3c/dom/Document.md) in interface [`Document`](../../../../org/w3c/dom/Document.md)

      Parameters:
      `namespaceURI` - - the namespace uri

      `qualifiedName` - - String qualified name for the element to be created

      Returns:
      Element node with given qualified name and namespace URI

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - INVALID_CHARACTER_ERR: Raised if the specified qualified name contains illegal Characters NAMESPACE_ERR : Raised if the qualified name is malformed, if the qualified name has a prefix and the namespace URI is null or an empty string, or if the qulaifiedName has a prefix that is "xml" and namespace URI is different from "http://www.w3.org/XML/1998/namespace"

      Since:
      DOM 2

    <!-- -->

    - #### createAttributeNS

          public Attr createAttributeNS(java.lang.String namespaceURI,
                                        java.lang.String qualifiedName)
                                 throws DOMException

      Creates an attribute with the given qualified name and namespace URI.
      Specified by:
      [`createAttributeNS`](../../../../org/w3c/dom/Document.md) in interface [`Document`](../../../../org/w3c/dom/Document.md)

      Parameters:
      `namespaceURI` - - The namespace uri as String

      `qualifiedName` - - Qualified name for the attribute to be created as String

      Returns:
      Element node with given qualified name and namespace URI

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - INVALID_CHARACTER_ERR: Raised if the specified qualified name contains illegal Characters NAMESPACE_ERR : Raised if the qualified name is malformed, if the qualified name has a prefix and the namespace URI is null or an empty string, or if the qulaifiedName has a prefix that is "xml" and namespace URI is different from "http://www.w3.org/2000/xmlns/"

      Since:
      DOM 2

    <!-- -->

    - #### getElementsByTagNameNS

          public NodeList getElementsByTagNameNS(java.lang.String namespaceURI,
                                                 java.lang.String localName)

      Returns a NodeList of all the Elements with a given local name and namespace URI in the order in which they are encountered in a preorder traversal of the Document tree.
      Specified by:
      [`getElementsByTagNameNS`](../../../../org/w3c/dom/Document.md) in interface [`Document`](../../../../org/w3c/dom/Document.md)

      Specified by:
      [`getElementsByTagNameNS`](../../../../org/w3c/dom/Element.md) in interface [`Element`](../../../../org/w3c/dom/Element.md)

      Overrides:
      [`getElementsByTagNameNS`](XMLElement.md) in class [`XMLElement`](XMLElement.md)

      Parameters:
      `namespaceURI` - - The namespace uri that should match for the returned elements as String

      `localName` - - The local name that should match for the returned elements as String

      Returns:
      nodelist of matching elements

    <!-- -->

    - #### getElementById

          public Element getElementById(java.lang.String elementId)

      Returns the Element whose ID is given by elementId. If no such element exists, returns null. Behavior is not defined if more than one element has this ID.
      Specified by:
      [`getElementById`](../../../../org/w3c/dom/Document.md) in interface [`Document`](../../../../org/w3c/dom/Document.md)

      Parameters:
      `elementId` - String used to get the matching Id Element

      Returns:
      The matching Id Element if one exists or null if none exists

      Since:
      DOM 2

    <!-- -->

    - #### createNodeIterator

          public NodeIterator createNodeIterator(Node root,
                                                 int whatToShow,
                                                 NodeFilter filter,
                                                 boolean expandEntityReferences)
                                          throws DOMException

      Creates a Node Iterator with specified root, flag which governs what type of nodes it should include in logical view, filter for filtering nodes, flag determining whether entity references and its descendants could be included
      Specified by:
      [`createNodeIterator`](../../../../org/w3c/dom/traversal/DocumentTraversal.md) in interface [`DocumentTraversal`](../../../../org/w3c/dom/traversal/DocumentTraversal.md)

      Parameters:
      `root` - root node of the iterator

      `whatToShow` - flag indicating what type of nodes will be included

      `filter` - NodeFilter to filter unwanted nodes from iterator

      `expandEntityReferences` - flag to indicate traversal of entity references

      Returns:
      object that implements NodeIterator interface, created on this document

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - NOT_SUPPORTED_ERR: if the NodeIterator could not be created with specified root

    <!-- -->

    - #### createTreeWalker

          public TreeWalker createTreeWalker(Node root,
                                             int whatToShow,
                                             NodeFilter filter,
                                             boolean expandEntityReferences)
                                      throws DOMException

      Creates a Node Iterator with specified root, flag which governs what type of nodes it should include in logical view, filter for filtering nodes, flag determining whether entity references and its descendants could be included
      Specified by:
      [`createTreeWalker`](../../../../org/w3c/dom/traversal/DocumentTraversal.md) in interface [`DocumentTraversal`](../../../../org/w3c/dom/traversal/DocumentTraversal.md)

      Parameters:
      `root` - root node of the treewalker

      `whatToShow` - flag indicating what type of nodes will be included

      `filter` - NodeFilter to filter unwanted nodes from treewalker

      `expandEntityReferences` - flag to indicate traversal of entity references

      Returns:
      an object that implements TreeWalker interface, created on this document

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - NOT_SUPPORTED_ERR: if the TreeWalker could not be created with specified root

    <!-- -->

    - #### createRange

          public Range createRange()

      Create a new Document Range Object, with Start and End Boundary points at the begining of the document.
      Returns:
      new Range object with start and end boundary points at the begining of the document

    <!-- -->

    - #### createEvent

          public Event createEvent(java.lang.String type)

      Creates an event object of the specified type
      Specified by:
      [`createEvent`](../../../../org/w3c/dom/events/DocumentEvent.md) in interface [`DocumentEvent`](../../../../org/w3c/dom/events/DocumentEvent.md)

      Parameters:
      `type` - the type of the event

      Returns:
      Event object of the specified type

    <!-- -->

    - #### createMutationEvent

          public MutationEvent createMutationEvent(java.lang.String type)

      Creates a Mutation Event object of specified type
      Parameters:
      `type` - the type of the mutation event

      Returns:
      Event object of the specified type

    <!-- -->

    - #### createRangeEvent

          public Event createRangeEvent(java.lang.String type)

      Creates a Range Event object of specified type
      Parameters:
      `type` - the type of the event

      Returns:
      Event object of the specified type

    <!-- -->

    - #### createTraversalEvent

          public Event createTraversalEvent(java.lang.String type)

      Creates a Traversal Event object of specified type
      Parameters:
      `type` - the type of the event

      Returns:
      Event object of the specified type

    <!-- -->

    - #### setSchema

          public void setSchema(XMLSchema schema)

      set the XML Schema
      Parameters:
      `schema` - to be set

    <!-- -->

    - #### getSchema

          public XMLSchema getSchema()

      return the validator
      Returns:
      `XMLSchema`

    <!-- -->

    - #### getContinuousValidityChecking

          public boolean getContinuousValidityChecking()

      An attribute specifying whether the validity of the document is continuously enforced. When the attribute is set to `true`, the implementation may raise certain exceptions, depending on the situation (see the following). This attribute is `false` by default.
      Specified by:
      [`getContinuousValidityChecking`](../../../../org/w3c/dom/validation/DocumentEditVAL.md) in interface [`DocumentEditVAL`](../../../../org/w3c/dom/validation/DocumentEditVAL.md)

    <!-- -->

    - #### setContinuousValidityChecking

          public void setContinuousValidityChecking(boolean continuousValidityChecking)
                                             throws DOMException,
                                                    ExceptionVAL

      An attribute specifying whether the validity of the document is continuously enforced. When the attribute is set to `true` , the implementation may raise certain exceptions, depending on the situation (see the following). This attribute is `false` by default.
      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - NOT_SUPPORTED_ERR: Raised if the implementation does not support setting this attribute to `true`.

      [`ExceptionVAL`](../../../../org/w3c/dom/validation/ExceptionVAL.md) - NO_SCHEMA_AVAILABLE_ERR: Raised if this attribute is set to `true` and a schema is unavailable.

      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - VALIDATION_ERR: Raised if an operation makes this document not compliant with the `VAL_INCOMPLETE` validity type or the document is invalid, and this attribute is set to `true` .

    <!-- -->

    - #### getDefinedElements

          public NameList getDefinedElements(java.lang.String namespaceURI)

      Returns list of all element information item names of global declaration, belonging to the specified namespace.
      Specified by:
      [`getDefinedElements`](../../../../org/w3c/dom/validation/DocumentEditVAL.md) in interface [`DocumentEditVAL`](../../../../org/w3c/dom/validation/DocumentEditVAL.md)

      Parameters:
      `namespaceURI` - `namespaceURI` of namespace. For DTDs, this is `null`.

      Returns:
      List of all element information item names belonging to the specified namespace or `null` if no schema is available.

    <!-- -->

    - #### validateDocument

          public short validateDocument()

      Validates the document against the schema, e.g., a DTD or an XML Schema or another. This method's behavior is implementation- dependent; and the any attempt to modify any part of the document while validating results in implementation-dependent behavior. In addition, the validation operation itself cannot modify the document, e.g., for default attributes. This method makes use of the passed-in error handler, as described in the \[ [DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\] `DOMConfiguration` interface, with all errors being `SEVERITY_ERROR` as defined in the `DOMError` interface.
      Specified by:
      [`validateDocument`](../../../../org/w3c/dom/validation/DocumentEditVAL.md) in interface [`DocumentEditVAL`](../../../../org/w3c/dom/validation/DocumentEditVAL.md)

      Returns:
      A validation state constant.

    <!-- -->

    - #### nodeValidity

          public short nodeValidity(short wFValidityCheckLevel)

      Determines if the node is valid relative to the validation type specified in `valType`. This operation doesn't normalize before checking if it is valid. To do so, one would need to explicitly call a normalize method. The difference between this method and the `validateDocument` method on the `DocumentVAL` interface is that `validateDocument` only checks to determine whether the entire document is valid.
      Specified by:
      [`nodeValidity`](../../../../org/w3c/dom/validation/NodeEditVAL.md) in interface [`NodeEditVAL`](../../../../org/w3c/dom/validation/NodeEditVAL.md)

      Overrides:
      [`nodeValidity`](XMLElement.md) in class [`XMLElement`](XMLElement.md)

      Parameters:
      `wFValidityCheckLevel` - Flag to tell at what level validity and well-formedness checking is done.

      Returns:
      A validation state constant.

    <!-- -->

    - #### canInsertBefore

          public short canInsertBefore(Node newChild,
                                       Node refChild)

      Determines whether the `Node.insertBefore` operation would make this document not compliant with the `VAL_INCOMPLETE` validity type.
      Specified by:
      [`canInsertBefore`](../../../../org/w3c/dom/validation/NodeEditVAL.md) in interface [`NodeEditVAL`](../../../../org/w3c/dom/validation/NodeEditVAL.md)

      Overrides:
      [`canInsertBefore`](XMLElement.md) in class [`XMLElement`](XMLElement.md)

      Parameters:
      `newChild` - `Node` to be inserted.

      `refChild` - Reference `Node`.

      Returns:
      A validation state constant.

    <!-- -->

    - #### canRemoveChild

          public short canRemoveChild(Node oldChild)

      Determines whether the `Node.removeChild` operation would make this document not compliant with the `VAL_INCOMPLETE` validity type.
      Specified by:
      [`canRemoveChild`](../../../../org/w3c/dom/validation/NodeEditVAL.md) in interface [`NodeEditVAL`](../../../../org/w3c/dom/validation/NodeEditVAL.md)

      Overrides:
      [`canRemoveChild`](XMLElement.md) in class [`XMLElement`](XMLElement.md)

      Parameters:
      `oldChild` - `Node` to be removed.

      Returns:
      A validation state constant.

    <!-- -->

    - #### canReplaceChild

          public short canReplaceChild(Node newChild,
                                       Node oldChild)

      Determines whether the `Node.replaceChild` operation would make this document not compliant with the `VAL_INCOMPLETE` validity type.
      Specified by:
      [`canReplaceChild`](../../../../org/w3c/dom/validation/NodeEditVAL.md) in interface [`NodeEditVAL`](../../../../org/w3c/dom/validation/NodeEditVAL.md)

      Overrides:
      [`canReplaceChild`](XMLElement.md) in class [`XMLElement`](XMLElement.md)

      Parameters:
      `newChild` - New `Node`.

      `oldChild` - `Node` to be replaced.

      Returns:
      A validation state constant.

    <!-- -->

    - #### canAppendChild

          public short canAppendChild(Node newChild)

      Determines whether the `Node.appendChild` operation would make this document not compliant with the `VAL_INCOMPLETE` validity type.
      Specified by:
      [`canAppendChild`](../../../../org/w3c/dom/validation/NodeEditVAL.md) in interface [`NodeEditVAL`](../../../../org/w3c/dom/validation/NodeEditVAL.md)

      Overrides:
      [`canAppendChild`](XMLElement.md) in class [`XMLElement`](XMLElement.md)

      Parameters:
      `newChild` - `Node` to be appended.

      Returns:
      A validation state constant.

    <!-- -->

    - #### getXMLNodeFromNode

          public XMLNode getXMLNodeFromNode(Node node)

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

- **[Prev Class](XMLDeclPI.md)**
- **[Next Class](XMLDocumentFragment.md)**

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
