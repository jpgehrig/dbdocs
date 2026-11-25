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

- **[Prev Class](XMLMultiHandler.md)**
- **[Next Class](XMLNotation.md)**

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

## **Class XMLNode**

- **java.lang.Object**

- - **oracle.xml.parser.v2.XMLNode**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Externalizable, java.io.Serializable, java.lang.Cloneable, [EventTarget](../../../../org/w3c/dom/events/EventTarget.md), [Node](../../../../org/w3c/dom/Node.md), [NodeEditVAL](../../../../org/w3c/dom/validation/NodeEditVAL.md)**

  <!-- -->

  **Direct Known Subclasses:**
  **[AttrDecl](AttrDecl.md), [DTD](DTD.md), [ElementDecl](ElementDecl.md), [XMLComment](XMLComment.md), [XMLNotation](XMLNotation.md), [XMLNSNode](XMLNSNode.md), [XMLPI](XMLPI.md), [XMLText](XMLText.md)**

  ------------------------------------------------------------------------

  **
  **

      public abstract class XMLNode
      extends java.lang.Object
      implements Node, java.io.Externalizable, java.lang.Cloneable, EventTarget, NodeEditVAL

  **Implements the DOM `Node` interface and serves as the primary datatype for the entire Document Object Model. It represents a single node in the document tree.**
  **The attributes `nodeName`, `nodeValue` and `attributes` are included as a mechanism to get at node information without casting down to the specific derived instance. In cases where there is no obvious mapping of these attributes for a specific `nodeType` (e.g., `nodeValue` for an Element or `attributes` for a Comment), this returns `null`. Note that the derived classes may contain additional and more convenient mechanisms to get and set the relevant information.**

  **See Also:**
  **[Serialized Form](../../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type         | Field and Description                                            |
    |---------------------------|------------------------------------------------------------------|
    | `static short`            | `ATTRDECL`<br>A attribute declaration node                       |
    | `static java.lang.String` | `Auto_Events`<br>Flag to set Auto EVENTS                         |
    | `static java.lang.String` | `capturing`                                                      |
    | `static java.lang.String` | `DOMAttrModified`                                                |
    | `static java.lang.String` | `DOMCharacterDataModified`                                       |
    | `static java.lang.String` | `DOMNodeInserted`                                                |
    | `static java.lang.String` | `DOMNodeInsertedIntoDocument`                                    |
    | `static java.lang.String` | `DOMNodeRemoved`                                                 |
    | `static java.lang.String` | `DOMNodeRemovedFromDocument`                                     |
    | `static java.lang.String` | `DOMSubtreeModified`                                             |
    | `static short`            | `ELEMENTDECL`<br>An element declaration node.                    |
    | `static int`              | `KEPT_NODE`                                                      |
    | `static short`            | `NAMESPACE_NODE`<br>A namespace node                             |
    | `static java.lang.String` | `noncapturing`                                                   |
    | `static java.lang.String` | `RANGE_DELETE_EVENT`<br>Flag to delete range event               |
    | `static java.lang.String` | `RANGE_DELETETEXT_EVENT`<br>Flag to set range delete text event  |
    | `static java.lang.String` | `RANGE_INSERT_EVENT`<br>Flag to set range event                  |
    | `static java.lang.String` | `RANGE_INSERTTEXT_EVENT`<br>Flag to set range insert text event  |
    | `static java.lang.String` | `RANGE_REPLACE_EVENT`<br>Flag to replace range event             |
    | `static java.lang.String` | `RANGE_SETTEXT_EVENT`<br>Flag to set range text event            |
    | `static java.lang.String` | `TRAVERSAL_DELETE_EVENT`<br>Flag to set traversal delete event   |
    | `static java.lang.String` | `TRAVERSAL_REPLACE_EVENT`<br>Flag to set traversal replace event |
    | `static short`            | `XMLDECL_NODE`<br>A attribute declaration node                   |

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

    | Modifier and Type                                                 | Method and Description                                                                                                                                                                                                                                                                                                                               |
    |-------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                            | `addEventListener``(java.lang.String type, `[`EventListener`](../../../../org/w3c/dom/events/EventListener.md)` listener, boolean useCapture)`<br>This method allows the registration of event listeners on the event target                                                                                                                         |
    | `void`                                                            | `addText``(char[] ch, int start, int length)`<br>Adds text to this node, or appends str to the last child if the last child is a text node.                                                                                                                                                                                                          |
    | [`Node`](../../../../org/w3c/dom/Node.md)                         | `appendChild``(`[`Node`](../../../../org/w3c/dom/Node.md)` newChild)`<br>Adds the node `newChild` to the end of the list of children of this node.                                                                                                                                                                                                   |
    | `short`                                                           | `canAppendChild``(`[`Node`](../../../../org/w3c/dom/Node.md)` newChild)`<br>Determines whether the `Node.appendChild` operation would make this document not compliant with the `VAL_INCOMPLETE` validity type.                                                                                                                                      |
    | `short`                                                           | `canInsertBefore``(`[`Node`](../../../../org/w3c/dom/Node.md)` newChild, `[`Node`](../../../../org/w3c/dom/Node.md)` refChild)`<br>Determines whether the `Node.insertBefore` operation would make this document not compliant with the `VAL_INCOMPLETE` validity type.                                                                              |
    | `short`                                                           | `canRemoveChild``(`[`Node`](../../../../org/w3c/dom/Node.md)` oldChild)`<br>Determines whether the `Node.removeChild` operation would make this document not compliant with the `VAL_INCOMPLETE` validity type.                                                                                                                                      |
    | `short`                                                           | `canReplaceChild``(`[`Node`](../../../../org/w3c/dom/Node.md)` newChild, `[`Node`](../../../../org/w3c/dom/Node.md)` oldChild)`<br>Determines whether the `Node.replaceChild` operation would make this document not compliant with the `VAL_INCOMPLETE` validity type.                                                                              |
    | [`Node`](../../../../org/w3c/dom/Node.md)                         | `cloneNode``(boolean deep)`<br>Returns a duplicate of this node, i.e., serves as a generic copy constructor for nodes.                                                                                                                                                                                                                               |
    | `boolean`                                                         | `dispatchEvent``(`[`Event`](../../../../org/w3c/dom/events/Event.md)` evtArg)`<br>This method allows the dispatch of events into the implementations event model                                                                                                                                                                                     |
    | `boolean`                                                         | `equals``(java.lang.Object obj)`<br>Indicates whether some other object is "equal to" this one.                                                                                                                                                                                                                                                      |
    | [`NamedNodeMap`](../../../../org/w3c/dom/NamedNodeMap.md)         | `getAttributes``()`<br>Gets a `NamedNodeMap` containing the attributes of this node (if it is an `Element`) or `null` otherwise.                                                                                                                                                                                                                     |
    | [`NodeList`](../../../../org/w3c/dom/NodeList.md)                 | `getChildNodes``()`<br>Gets a `NodeList` that contains all children of this node.                                                                                                                                                                                                                                                                    |
    | `int`                                                             | `getColumnNumber``()`<br>Get column number debug information                                                                                                                                                                                                                                                                                         |
    | `boolean`                                                         | `getDebugMode``()`<br>Get debug information mode                                                                                                                                                                                                                                                                                                     |
    | `java.lang.String`                                                | `getDefaultValue``()`<br>The default value specified in an attribute or an element declaration or `null` if unspecified.                                                                                                                                                                                                                             |
    | [`DOMStringList`](../../../../org/w3c/dom/DOMStringList.md)       | `getEnumeratedValues``()`<br>A `DOMStringList`, as described in \[[DOM Level 3 Core](http://www.w3.org/TR/2003/CR-DOM-Level-3-Core-20031107)\], of distinct values for an attribute or an element declaration or `null` if unspecified.                                                                                                              |
    | [`Node`](../../../../org/w3c/dom/Node.md)                         | `getFirstChild``()`<br>Gets the first child of this node.                                                                                                                                                                                                                                                                                            |
    | `java.lang.Object`                                                | `getFirstChildAsOffset``()`                                                                                                                                                                                                                                                                                                                          |
    | [`Node`](../../../../org/w3c/dom/Node.md)                         | `getLastChild``()`<br>Gets the last child of this node.                                                                                                                                                                                                                                                                                              |
    | `int`                                                             | `getLineNumber``()`<br>Get line number debug information                                                                                                                                                                                                                                                                                             |
    | `java.lang.String`                                                | `getLocalName``()`<br>Gets the Local Name of this node                                                                                                                                                                                                                                                                                               |
    | `java.lang.String`                                                | `getNamespaceURI``()`<br>Gets the namespace URI of this node.                                                                                                                                                                                                                                                                                        |
    | [`Node`](../../../../org/w3c/dom/Node.md)                         | `getNextSibling``()`<br>Gets The node immediately following this node.                                                                                                                                                                                                                                                                               |
    | `java.lang.Object`                                                | `getNextSiblingAsOffset``()`                                                                                                                                                                                                                                                                                                                         |
    | `java.lang.String`                                                | `getNodeName``()`<br>Gets the name of this node                                                                                                                                                                                                                                                                                                      |
    | `short`                                                           | `getNodeType``()`<br>Gets the type of the node                                                                                                                                                                                                                                                                                                       |
    | `java.lang.String`                                                | `getNodeValue``()`<br>Gets the value of this node, depending on its type                                                                                                                                                                                                                                                                             |
    | `java.io.InputStream`                                             | `getNodeValueAsBinaryStream``()`                                                                                                                                                                                                                                                                                                                     |
    | `void`                                                            | `getNodeValueAsBinaryStream``(java.io.OutputStream ostream)`                                                                                                                                                                                                                                                                                         |
    | `java.io.Reader`                                                  | `getNodeValueAsCharacterStream``()`                                                                                                                                                                                                                                                                                                                  |
    | `void`                                                            | `getNodeValueAsCharacterStream``(java.io.Writer writer)`                                                                                                                                                                                                                                                                                             |
    | [`Document`](../../../../org/w3c/dom/Document.md)                 | `getOwnerDocument``()`<br>Gets the `Document` object associated with this node.                                                                                                                                                                                                                                                                      |
    | [`Node`](../../../../org/w3c/dom/Node.md)                         | `getParentNode``()`<br>Gets the parent of this node.                                                                                                                                                                                                                                                                                                 |
    | `java.lang.String`                                                | `getPrefix``()`<br>Get the namespace prefix for this element.                                                                                                                                                                                                                                                                                        |
    | [`Node`](../../../../org/w3c/dom/Node.md)                         | `getPreviousSibling``()`<br>Gets the node immediately preceding this node.                                                                                                                                                                                                                                                                           |
    | `int`                                                             | `getPrimitiveTypeId``()`<br>Get Schema primitive type id                                                                                                                                                                                                                                                                                             |
    | `java.lang.Object`                                                | `getProperty``(java.lang.String propName)`<br>Get a property of the node                                                                                                                                                                                                                                                                             |
    | `java.lang.String`                                                | `getSystemId``()`<br>Get the system id of the entity contain this node                                                                                                                                                                                                                                                                               |
    | `java.lang.String`                                                | `getText``()`<br>Returns the non-marked-up text contained by this element.                                                                                                                                                                                                                                                                           |
    | [`XMLError`](XMLError.md)                                         | `getXMLError``()`<br>Gets XMLError set in the document node                                                                                                                                                                                                                                                                                          |
    | `boolean`                                                         | `hasAttributes``()`<br>Returns whether this node (if it is an element) has any attributes.                                                                                                                                                                                                                                                           |
    | `boolean`                                                         | `hasChildNodes``()`<br>This is a convenience method to allow easy determination of whether a node has any children.                                                                                                                                                                                                                                  |
    | `int`                                                             | `hashCode``()`<br>Returns a hash code value for the object.                                                                                                                                                                                                                                                                                          |
    | [`Node`](../../../../org/w3c/dom/Node.md)                         | `insertBefore``(`[`Node`](../../../../org/w3c/dom/Node.md)` newChild, `[`Node`](../../../../org/w3c/dom/Node.md)` refChild)`<br>Inserts the node `newChild` before the existing child node `refChild`.                                                                                                                                               |
    | `boolean`                                                         | `isDocumentFlag``(int flag)`<br>Returns the document flag information                                                                                                                                                                                                                                                                                |
    | `boolean`                                                         | `isNodeFlag``(int flag)`<br>Returns the node flag information                                                                                                                                                                                                                                                                                        |
    | `boolean`                                                         | `isSupported``(java.lang.String feature, java.lang.String version)`<br>Tests whether the DOM implementation implements a specific feature and that feature is supported by this node.                                                                                                                                                                |
    | `short`                                                           | `nodeValidity``(short wFValidityCheckLevel)`<br>Determines if the node is valid relative to the validation type specified in `valType`.                                                                                                                                                                                                              |
    | `void`                                                            | `normalize``()`<br>Puts all Text nodes in the full depth of the sub-tree underneath this Node, including attribute nodes, into "normal" form where only structure (e.g., elements, comments, processing instructions, CDATA sections, and entity references) separates Text nodes, i.e., there are neither adjacent Text nodes nor empty Text nodes. |
    | `void`                                                            | `print``(java.io.OutputStream out)`<br>Writes the contents of this node to the given output stream.                                                                                                                                                                                                                                                  |
    | `void`                                                            | `print``(java.io.OutputStream out, java.lang.String enc)`<br>Writes the contents of this node to the given output stream.                                                                                                                                                                                                                            |
    | `void`                                                            | `print``(java.io.PrintWriter out)`<br>Writes the contents of this node using the given print writer.                                                                                                                                                                                                                                                 |
    | `void`                                                            | `print``(java.io.Writer out)`<br>Writes the contents of this node using the given print writer.                                                                                                                                                                                                                                                      |
    | `void`                                                            | `readExternal``(java.io.ObjectInput inArg)`<br>This method reads the information that was written to the compressed stream by the writeExternal() method, and restores the object correspondingly.                                                                                                                                                   |
    | [`Node`](../../../../org/w3c/dom/Node.md)                         | `removeChild``(`[`Node`](../../../../org/w3c/dom/Node.md)` oldChild)`<br>Removes the child node indicated by `oldChild` from the list of children, and returns it.                                                                                                                                                                                   |
    | `void`                                                            | `removeEventListener``(java.lang.String type, `[`EventListener`](../../../../org/w3c/dom/events/EventListener.md)` listener, boolean useCapture)`<br>This method allows the removal of event listeners from the event target.                                                                                                                        |
    | [`Node`](../../../../org/w3c/dom/Node.md)                         | `replaceChild``(`[`Node`](../../../../org/w3c/dom/Node.md)` newChild, `[`Node`](../../../../org/w3c/dom/Node.md)` oldChild)`<br>Replaces the child node `oldChild` with `newChild` in the list of children, and returns the `oldChild` node.                                                                                                         |
    | `void`                                                            | `reportSAXEvents``(`[`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)` cntHandler)`<br>Report SAX Events from a DOM Tree                                                                                                                                                                                                                 |
    | `void`                                                            | `resetNodeFlag``(int flag)`<br>Resets the node flag information                                                                                                                                                                                                                                                                                      |
    | [`NodeList`](../../../../org/w3c/dom/NodeList.md)                 | `selectNodes``(java.lang.String pattern)`<br>Selects nodes from the tree which match the given pattern.                                                                                                                                                                                                                                              |
    | [`NodeList`](../../../../org/w3c/dom/NodeList.md)                 | `selectNodes``(java.lang.String pattern, `[`NSResolver`](NSResolver.md)` nsr)`<br>Selects nodes from the tree which match the given pattern                                                                                                                                                                                                          |
    | [`Node`](../../../../org/w3c/dom/Node.md)                         | `selectSingleNode``(java.lang.String pattern)`<br>Selects the first node from the tree that matches the given pattern                                                                                                                                                                                                                                |
    | [`Node`](../../../../org/w3c/dom/Node.md)                         | `selectSingleNode``(java.lang.String pattern, `[`NSResolver`](NSResolver.md)` nsr)`<br>Selects the first node from the tree that matches the given pattern                                                                                                                                                                                           |
    | `void`                                                            | `setDebugInfo``(int line, int col, java.lang.String sysid)`<br>Set debug information in the node                                                                                                                                                                                                                                                     |
    | `void`                                                            | `setNodeFlag``(int flag)`<br>Sets the node flag information                                                                                                                                                                                                                                                                                          |
    | `void`                                                            | `setNodeFlag``(int flag, boolean val)`<br>Sets or resets the node flag information                                                                                                                                                                                                                                                                   |
    | `void`                                                            | `setNodeFlag``(int flag, int mask)`<br>Sets the node multi bit flag information                                                                                                                                                                                                                                                                      |
    | `void`                                                            | `setNodeValue``(java.lang.String nodeValue)`<br>Sets the value of this node, depending on its type                                                                                                                                                                                                                                                   |
    | `java.io.OutputStream`                                            | `setNodeValueAsBinaryStream``()`                                                                                                                                                                                                                                                                                                                     |
    | `void`                                                            | `setNodeValueAsBinaryStream``(java.io.InputStream istream)`                                                                                                                                                                                                                                                                                          |
    | `java.io.Writer`                                                  | `setNodeValueAsCharacterStream``()`                                                                                                                                                                                                                                                                                                                  |
    | `void`                                                            | `setNodeValueAsCharacterStream``(java.io.Reader reader)`                                                                                                                                                                                                                                                                                             |
    | `void`                                                            | `setPrefix``(java.lang.String prefix)`<br>Sets the prefix of this node                                                                                                                                                                                                                                                                               |
    | `void`                                                            | `setProperty``(java.lang.String propName, java.lang.Object propValue)`<br>Set a property of the node                                                                                                                                                                                                                                                 |
    | [`DocumentFragment`](../../../../org/w3c/dom/DocumentFragment.md) | `transformNode``(`[`XSLStylesheet`](XSLStylesheet.md)` xsl)`<br>Transforms a node in the tree using the given stylesheet                                                                                                                                                                                                                             |
    | `java.lang.String`                                                | `valueOf``(java.lang.String pattern)`<br>Selects the value of the first node from tree that matches the pattern                                                                                                                                                                                                                                      |
    | `java.lang.String`                                                | `valueOf``(java.lang.String pattern, `[`NSResolver`](NSResolver.md)` nsr)`<br>Selects the value of the first node from tree that matches the pattern                                                                                                                                                                                                 |
    | `void`                                                            | `writeExternal``(java.io.ObjectOutput outArg)`<br>This method saves the state of the object by creating a binary compressed stream with information about this object.                                                                                                                                                                               |
    | `long`                                                            | `xdbGetNodeId``()`                                                                                                                                                                                                                                                                                                                                   |

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### ELEMENTDECL

          public static final short ELEMENTDECL

      An element declaration node.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ATTRDECL

          public static final short ATTRDECL

      A attribute declaration node
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### XMLDECL_NODE

          public static final short XMLDECL_NODE

      A attribute declaration node
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### NAMESPACE_NODE

          public static final short NAMESPACE_NODE

      A namespace node
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### KEPT_NODE

          public static final int KEPT_NODE

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### Auto_Events

          public static final java.lang.String Auto_Events

      Flag to set Auto EVENTS
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### RANGE_SETTEXT_EVENT

          public static final java.lang.String RANGE_SETTEXT_EVENT

      Flag to set range text event
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### RANGE_INSERTTEXT_EVENT

          public static final java.lang.String RANGE_INSERTTEXT_EVENT

      Flag to set range insert text event
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### RANGE_DELETETEXT_EVENT

          public static final java.lang.String RANGE_DELETETEXT_EVENT

      Flag to set range delete text event
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### RANGE_INSERT_EVENT

          public static final java.lang.String RANGE_INSERT_EVENT

      Flag to set range event
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### RANGE_DELETE_EVENT

          public static final java.lang.String RANGE_DELETE_EVENT

      Flag to delete range event
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### RANGE_REPLACE_EVENT

          public static final java.lang.String RANGE_REPLACE_EVENT

      Flag to replace range event
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### TRAVERSAL_DELETE_EVENT

          public static final java.lang.String TRAVERSAL_DELETE_EVENT

      Flag to set traversal delete event
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### TRAVERSAL_REPLACE_EVENT

          public static final java.lang.String TRAVERSAL_REPLACE_EVENT

      Flag to set traversal replace event
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### DOMSubtreeModified

          public static final java.lang.String DOMSubtreeModified

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### DOMNodeInserted

          public static final java.lang.String DOMNodeInserted

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### DOMNodeRemoved

          public static final java.lang.String DOMNodeRemoved

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### DOMNodeRemovedFromDocument

          public static final java.lang.String DOMNodeRemovedFromDocument

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### DOMNodeInsertedIntoDocument

          public static final java.lang.String DOMNodeInsertedIntoDocument

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### DOMAttrModified

          public static final java.lang.String DOMAttrModified

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### DOMCharacterDataModified

          public static final java.lang.String DOMCharacterDataModified

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### capturing

          public static final java.lang.String capturing

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### noncapturing

          public static final java.lang.String noncapturing

      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getNodeType

          public short getNodeType()

      Gets the type of the node
      Specified by:
      [`getNodeType`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Returns:
      type of the node

    <!-- -->

    - #### getNodeName

          public java.lang.String getNodeName()

      Gets the name of this node
      Specified by:
      [`getNodeName`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Returns:
      Name of this node

    <!-- -->

    - #### getLocalName

          public java.lang.String getLocalName()

      Gets the Local Name of this node
      Specified by:
      [`getLocalName`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Returns:
      LocalName of the node

    <!-- -->

    - #### getNamespaceURI

          public java.lang.String getNamespaceURI()

      Gets the namespace URI of this node.
      Specified by:
      [`getNamespaceURI`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Returns:
      the namespace

    <!-- -->

    - #### getPrefix

          public java.lang.String getPrefix()

      Get the namespace prefix for this element.
      Specified by:
      [`getPrefix`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Returns:
      the namespace prefix

    <!-- -->

    - #### setPrefix

          public void setPrefix(java.lang.String prefix)
                         throws DOMException

      Sets the prefix of this node
      Specified by:
      [`setPrefix`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Parameters:
      `prefix` - set the prefix

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md)

    <!-- -->

    - #### getNodeValue

          public java.lang.String getNodeValue()
                                        throws DOMException

      Gets the value of this node, depending on its type
      Specified by:
      [`getNodeValue`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Returns:
      Value of this node

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md)

    <!-- -->

    - #### getNodeValueAsCharacterStream

          public java.io.Reader getNodeValueAsCharacterStream()
                                                       throws DOMException

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md)

    <!-- -->

    - #### getNodeValueAsBinaryStream

          public java.io.InputStream getNodeValueAsBinaryStream()
                                                         throws DOMException

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md)

    <!-- -->

    - #### getNodeValueAsCharacterStream

          public void getNodeValueAsCharacterStream(java.io.Writer writer)
                                             throws DOMException,
                                                    java.io.IOException

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md)

      `java.io.IOException`

    <!-- -->

    - #### getNodeValueAsBinaryStream

          public void getNodeValueAsBinaryStream(java.io.OutputStream ostream)
                                          throws DOMException,
                                                 java.io.IOException

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md)

      `java.io.IOException`

    <!-- -->

    - #### setNodeValueAsCharacterStream

          public java.io.Writer setNodeValueAsCharacterStream()
                                                       throws DOMException

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md)

    <!-- -->

    - #### setNodeValueAsCharacterStream

          public void setNodeValueAsCharacterStream(java.io.Reader reader)
                                             throws DOMException,
                                                    java.io.IOException

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md)

      `java.io.IOException`

    <!-- -->

    - #### setNodeValueAsBinaryStream

          public java.io.OutputStream setNodeValueAsBinaryStream()

    <!-- -->

    - #### setNodeValueAsBinaryStream

          public void setNodeValueAsBinaryStream(java.io.InputStream istream)
                                          throws DOMException,
                                                 java.io.IOException

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md)

      `java.io.IOException`

    <!-- -->

    - #### setNodeValue

          public void setNodeValue(java.lang.String nodeValue)
                            throws DOMException

      Sets the value of this node, depending on its type
      Specified by:
      [`setNodeValue`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - NO_MODIFICATION_ALLOWED_ERR: Raised when the node is readonly.

    <!-- -->

    - #### getParentNode

          public Node getParentNode()

      Gets the parent of this node. All nodes, except `Document`, `DocumentFragment`, and `Attr` may have a parent. However, if a node has just been created and not yet added to the tree, or if it has been removed from the tree, this is `null`.
      Specified by:
      [`getParentNode`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Returns:
      The parent of this node

    <!-- -->

    - #### getChildNodes

          public NodeList getChildNodes()

      Gets a `NodeList` that contains all children of this node. If there are no children, this is a `NodeList` containing no nodes. The content of the returned `NodeList` is "live" in the sense that, for instance, changes to the children of the node object that it was created from are immediately reflected in the nodes returned by the `NodeList` accessors; it is not a static snapshot of the content of the node. This is true for every `NodeList`, including the ones returned by the `getElementsByTagName` method.
      Specified by:
      [`getChildNodes`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Returns:
      The children of this node

    <!-- -->

    - #### getFirstChild

          public Node getFirstChild()

      Gets the first child of this node. If there is no such node, this returns `null`.
      Specified by:
      [`getFirstChild`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Returns:
      The first child of this node

    <!-- -->

    - #### getLastChild

          public Node getLastChild()

      Gets the last child of this node. If there is no such node, this returns `null`.
      Specified by:
      [`getLastChild`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Returns:
      The last child of this node

    <!-- -->

    - #### getPreviousSibling

          public Node getPreviousSibling()

      Gets the node immediately preceding this node. If there is no such node, this returns `null`.
      Specified by:
      [`getPreviousSibling`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Returns:
      the previous node

    <!-- -->

    - #### getNextSibling

          public Node getNextSibling()

      Gets The node immediately following this node. If there is no such node, this returns `null`.
      Specified by:
      [`getNextSibling`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Returns:
      the next node

    <!-- -->

    - #### getAttributes

          public NamedNodeMap getAttributes()

      Gets a `NamedNodeMap` containing the attributes of this node (if it is an `Element`) or `null` otherwise.
      Specified by:
      [`getAttributes`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Returns:
      the attributes of this node

    <!-- -->

    - #### getOwnerDocument

          public Document getOwnerDocument()

      Gets the `Document` object associated with this node. This is also the `Document` object used to create new nodes. When this node is a `Document` this is `null`.
      Specified by:
      [`getOwnerDocument`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Returns:
      The document associated with this node

    <!-- -->

    - #### hasAttributes

          public boolean hasAttributes()

      Returns whether this node (if it is an element) has any attributes.
      Specified by:
      [`hasAttributes`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Returns:
      `true` if this node has any attributes, `false` otherwise.

    <!-- -->

    - #### hasChildNodes

          public boolean hasChildNodes()

      This is a convenience method to allow easy determination of whether a node has any children.
      Specified by:
      [`hasChildNodes`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Returns:
      `true` if the node has any children, `false` if the node has no children.

    <!-- -->

    - #### isSupported

          public boolean isSupported(java.lang.String feature,
                                     java.lang.String version)

      Tests whether the DOM implementation implements a specific feature and that feature is supported by this node.
      Specified by:
      [`isSupported`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Parameters:
      `feature` -

      `version` -

      Returns:
      true, if the feature is supported else false

    <!-- -->

    - #### appendChild

          public Node appendChild(Node newChild)
                           throws DOMException

      Adds the node `newChild` to the end of the list of children of this node. If the `newChild` is already in the tree, it is first removed.
      Specified by:
      [`appendChild`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Parameters:
      `newChild` - The node to add.If it is a `DocumentFragment` object, the entire contents of the document fragment are moved into the child list of this node

      Returns:
      The node added.

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - HIERARCHY_REQUEST_ERR: Raised if this node is of a type that does not allow children of the type of the `newChild` node, or if the node to append is one of this node's ancestors.
      WRONG_DOCUMENT_ERR: Raised if `newChild` was created from a different document than the one that created this node.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.

    <!-- -->

    - #### removeChild

          public Node removeChild(Node oldChild)
                           throws DOMException

      Removes the child node indicated by `oldChild` from the list of children, and returns it.
      Specified by:
      [`removeChild`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Parameters:
      `oldChild` - The node being removed.

      Returns:
      The node removed.

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.
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

    <!-- -->

    - #### cloneNode

          public Node cloneNode(boolean deep)

      Returns a duplicate of this node, i.e., serves as a generic copy constructor for nodes. The duplicate node has no parent ( `parentNode` returns `null`.).
      Cloning an `Element` copies all attributes and their values, including those generated by the XML processor to represent defaulted attributes, but this method does not copy any text it contains unless it is a deep clone, since the text is contained in a child `Text` node. Cloning any other type of node simply returns a copy of this node.
      Specified by:
      [`cloneNode`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Parameters:
      `deep` - If `true`, recursively clone the subtree under the specified node; if `false`, clone only the node itself (and its attributes, if it is an `Element`).

      Returns:
      The duplicate node.

    <!-- -->

    - #### normalize

          public void normalize()

      Puts all Text nodes in the full depth of the sub-tree underneath this Node, including attribute nodes, into "normal" form where only structure (e.g., elements, comments, processing instructions, CDATA sections, and entity references) separates Text nodes, i.e., there are neither adjacent Text nodes nor empty Text nodes. This can be used to ensure that the DOM view of a document is the same as if it were saved and re-loaded, and is useful when operations (such as XPointer lookups) that depend on a particulardocument tree structure are to be used.
      Specified by:
      [`normalize`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

    <!-- -->

    - #### addEventListener

          public void addEventListener(java.lang.String type,
                                       EventListener listener,
                                       boolean useCapture)

      This method allows the registration of event listeners on the event target
      Specified by:
      [`addEventListener`](../../../../org/w3c/dom/events/EventTarget.md) in interface [`EventTarget`](../../../../org/w3c/dom/events/EventTarget.md)

      Parameters:
      `type` - the type of event for which the event listener wants to register

      `listener` - the listener to be registered

      `useCapture` - flag to indicate if the listener wants to initiate capture

    <!-- -->

    - #### removeEventListener

          public void removeEventListener(java.lang.String type,
                                          EventListener listener,
                                          boolean useCapture)

      Description copied from interface: [`EventTarget`](../../../../org/w3c/dom/events/EventTarget.md)
      This method allows the removal of event listeners from the event target. If an `EventListener` is removed from an `EventTarget` while it is processing an event, it will not be triggered by the current actions. `EventListener`s can never be invoked after being removed.
      Calling `removeEventListener` with arguments which do not identify any currently registered `EventListener` on the `EventTarget` has no effect.
      Specified by:
      [`removeEventListener`](../../../../org/w3c/dom/events/EventTarget.md) in interface [`EventTarget`](../../../../org/w3c/dom/events/EventTarget.md)

      Parameters:
      `type` - Specifies the event type of the `EventListener` being removed.

      `listener` - The `EventListener` parameter indicates the `EventListener` to be removed.

      `useCapture` - Specifies whether the `EventListener` being removed was registered as a capturing listener or not. If a listener was registered twice, one with capture and one without, each must be removed separately. Removal of a capturing listener does not affect a non-capturing version of the same listener, and vice versa.

    <!-- -->

    - #### dispatchEvent

          public boolean dispatchEvent(Event evtArg)
                                throws DOMException

      This method allows the dispatch of events into the implementations event model
      Specified by:
      [`dispatchEvent`](../../../../org/w3c/dom/events/EventTarget.md) in interface [`EventTarget`](../../../../org/w3c/dom/events/EventTarget.md)

      Parameters:
      `evtArg` - - event to dispatch

      Returns:
      boolean value that indicates whether preventDefault or stopPropogation was called

      Throws:
      `UNSPECIFIED_EVENT_TYPE:` - Raised if the Event's type was not specified by initializing the event before dispatchEvent was called

      [`DOMException`](../../../../org/w3c/dom/DOMException.md)

    <!-- -->

    - #### getDefaultValue

          public java.lang.String getDefaultValue()

      The default value specified in an attribute or an element declaration or `null` if unspecified. Elena wanted mention of XML Schema's canonical lexical representation here. Why?
      Specified by:
      [`getDefaultValue`](../../../../org/w3c/dom/validation/NodeEditVAL.md) in interface [`NodeEditVAL`](../../../../org/w3c/dom/validation/NodeEditVAL.md)

    <!-- -->

    - #### getEnumeratedValues

          public DOMStringList getEnumeratedValues()

      A `DOMStringList`, as described in \[[DOM Level 3 Core](http://www.w3.org/TR/2003/CR-DOM-Level-3-Core-20031107)\], of distinct values for an attribute or an element declaration or `null` if unspecified. If the schema is a W3C XML schema, this is a list of strings which are lexical representations corresponding to the values in the \[value\] property of the enumeration component for the type of the attribute or element. It is recommended that the canonical lexical representations of the values be used.
      Specified by:
      [`getEnumeratedValues`](../../../../org/w3c/dom/validation/NodeEditVAL.md) in interface [`NodeEditVAL`](../../../../org/w3c/dom/validation/NodeEditVAL.md)

    <!-- -->

    - #### canInsertBefore

          public short canInsertBefore(Node newChild,
                                       Node refChild)

      Determines whether the `Node.insertBefore` operation would make this document not compliant with the `VAL_INCOMPLETE` validity type.
      Specified by:
      [`canInsertBefore`](../../../../org/w3c/dom/validation/NodeEditVAL.md) in interface [`NodeEditVAL`](../../../../org/w3c/dom/validation/NodeEditVAL.md)

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

      Parameters:
      `newChild` - `Node` to be appended.

      Returns:
      A validation state constant.

    <!-- -->

    - #### nodeValidity

          public short nodeValidity(short wFValidityCheckLevel)

      Determines if the node is valid relative to the validation type specified in `valType`. This operation doesn't normalize before checking if it is valid. To do so, one would need to explicitly call a normalize method. The difference between this method and the `validateDocument` method on the `DocumentVAL` interface is that `validateDocument` only checks to determine whether the entire document is valid.
      Specified by:
      [`nodeValidity`](../../../../org/w3c/dom/validation/NodeEditVAL.md) in interface [`NodeEditVAL`](../../../../org/w3c/dom/validation/NodeEditVAL.md)

      Parameters:
      `wFValidityCheckLevel` - Flag to tell at what level validity and well-formedness checking is done.

      Returns:
      A validation state constant.

    <!-- -->

    - #### addText

          public void addText(char[] ch,
                              int start,
                              int length)
                       throws XMLDOMException

      Adds text to this node, or appends str to the last child if the last child is a text node.
      Parameters:
      `ch` - char array to add

      `start` - start index in the char array

      `length` - no of chars to be added

      Throws:
      [`XMLDOMException`](XMLDOMException.md) - if text can't be added to this node

    <!-- -->

    - #### getText

          public java.lang.String getText()

      Returns the non-marked-up text contained by this element. For text elements, this is the raw data. For elements with child nodes, this method traverses the entire subtree and appends the text for each terminal text element, effectively stripping out the XML markup for the subtree. For example, if the XML document contains the following: \<xmp\> \<AUTHOR\> \<FIRST\>William\</FIRST\> \<LAST\>Shakespeare\</LAST\> \</AUTHOR\> \</xmp\>
      `XMLDocument.getText` returns "William Shakespeare".

      Returns:
      non-marked-up text contained bu this element

    <!-- -->

    - #### reportSAXEvents

          public void reportSAXEvents(ContentHandler cntHandler)
                               throws SAXException

      Report SAX Events from a DOM Tree
      Parameters:
      `cntHandler` -

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - thrown by SAX Callback functions

    <!-- -->

    - #### transformNode

          public DocumentFragment transformNode(XSLStylesheet xsl)
                                         throws XSLException

      Transforms a node in the tree using the given stylesheet
      Parameters:
      `xsl` - `XSLStylesheet` to be used for transformation

      Returns:
      a document fragment

      Throws:
      [`XSLException`](XSLException.md) - Raised if there is an error while doing the XSL transformation.

    <!-- -->

    - #### selectNodes

          public NodeList selectNodes(java.lang.String pattern,
                                      NSResolver nsr)
                               throws XSLException

      Selects nodes from the tree which match the given pattern
      Parameters:
      `pattern` - XSL pattern to match

      `nsr` - NSResolver to resolve any namespace prefixes that occur in the given pattern

      Returns:
      a list of matching nodes

      Throws:
      [`XSLException`](XSLException.md) - Raised if there is an error while doing the match

    <!-- -->

    - #### selectNodes

          public NodeList selectNodes(java.lang.String pattern)
                               throws XSLException

      Selects nodes from the tree which match the given pattern. This method assumes that the pattern does not contain namespace prefixes.
      Parameters:
      `pattern` - XSL pattern to match

      Returns:
      a list of matching nodes

      Throws:
      [`XSLException`](XSLException.md) - Raised if there is an error while doing the match

    <!-- -->

    - #### selectSingleNode

          public Node selectSingleNode(java.lang.String pattern,
                                       NSResolver nsr)
                                throws XSLException

      Selects the first node from the tree that matches the given pattern
      Parameters:
      `pattern` - XSL pattern to match

      `nsr` - NSResolver to resolve any prefixes that occur in given pattern

      Returns:
      matching node

      Throws:
      [`XSLException`](XSLException.md) - Raised if there is an error while doing the match

    <!-- -->

    - #### selectSingleNode

          public Node selectSingleNode(java.lang.String pattern)
                                throws XSLException

      Selects the first node from the tree that matches the given pattern
      Parameters:
      `pattern` - XSL pattern to match

      Returns:
      matching node

      Throws:
      [`XSLException`](XSLException.md) - Raised if there is an error while doing the match

    <!-- -->

    - #### valueOf

          public java.lang.String valueOf(java.lang.String pattern,
                                          NSResolver nsr)
                                   throws XSLException

      Selects the value of the first node from tree that matches the pattern
      Parameters:
      `pattern` - XSL pattern to match

      `nsr` - NSResolver to resolve any prefixes that occur in given pattern

      Returns:
      value of the matching node

      Throws:
      [`XSLException`](XSLException.md) - Raised if there is an error while doing the match

    <!-- -->

    - #### valueOf

          public java.lang.String valueOf(java.lang.String pattern)
                                   throws XSLException

      Selects the value of the first node from tree that matches the pattern
      Parameters:
      `pattern` - XSL pattern to match

      Returns:
      value of the matching node

      Throws:
      [`XSLException`](XSLException.md) - Raised if there is an error while doing the match

    <!-- -->

    - #### isNodeFlag

          public boolean isNodeFlag(int flag)

      Returns the node flag information
      Returns:
      true if the flag is set

    <!-- -->

    - #### isDocumentFlag

          public boolean isDocumentFlag(int flag)

      Returns the document flag information
      Returns:
      true if the flag is set

    <!-- -->

    - #### setNodeFlag

          public void setNodeFlag(int flag)

      Sets the node flag information
      Parameters:
      `flag` - the node flag

    <!-- -->

    - #### setNodeFlag

          public void setNodeFlag(int flag,
                                  boolean val)

      Sets or resets the node flag information
      Parameters:
      `flag` - the node flag

      `val` - boolean, the flag is set if val is true, otherwise reset

    <!-- -->

    - #### setNodeFlag

          public void setNodeFlag(int flag,
                                  int mask)

      Sets the node multi bit flag information
      Parameters:
      `flag` - the node flag

      `mask` - the mask for the multiple bits

    <!-- -->

    - #### resetNodeFlag

          public void resetNodeFlag(int flag)

      Resets the node flag information
      Parameters:
      `flag` - the node flag

    <!-- -->

    - #### getPrimitiveTypeId

          public int getPrimitiveTypeId()

      Get Schema primitive type id
      Returns:
      schema type id

    <!-- -->

    - #### getDebugMode

          public boolean getDebugMode()

      Get debug information mode
      Returns:
      flag debugging mode

    <!-- -->

    - #### setDebugInfo

          public void setDebugInfo(int line,
                                   int col,
                                   java.lang.String sysid)

      Set debug information in the node
      Parameters:
      `line` - the line number

      `col` - the col number

      `sysid` - the system id

    <!-- -->

    - #### getLineNumber

          public int getLineNumber()

      Get line number debug information
      Returns:
      line the line number

    <!-- -->

    - #### getColumnNumber

          public int getColumnNumber()

      Get column number debug information
      Returns:
      column the column number

    <!-- -->

    - #### getSystemId

          public java.lang.String getSystemId()

      Get the system id of the entity contain this node
      Returns:
      sysid the system id

    <!-- -->

    - #### getXMLError

          public XMLError getXMLError()

      Gets XMLError set in the document node
      Returns:
      XMLError

    <!-- -->

    - #### setProperty

          public void setProperty(java.lang.String propName,
                                  java.lang.Object propValue)

      Set a property of the node
      Parameters:
      `propName` - - Name of the property

      `propValue` - - Value of the property

    <!-- -->

    - #### getProperty

          public java.lang.Object getProperty(java.lang.String propName)

      Get a property of the node
      Parameters:
      `propName` - - Name of the property

      Returns:
      Object propValue - Value of the property

    <!-- -->

    - #### print

          public void print(java.io.Writer out)
                     throws java.io.IOException

      Writes the contents of this node using the given print writer.
      Parameters:
      `out` - `PrintWriter` to use

      Throws:
      `java.io.IOException` - if an error occurs

    <!-- -->

    - #### print

          public void print(java.io.PrintWriter out)
                     throws java.io.IOException

      Writes the contents of this node using the given print writer.
      Parameters:
      `out` - `PrintWriter` to use

      Throws:
      `java.io.IOException` - if an error occurs

    <!-- -->

    - #### print

          public void print(java.io.OutputStream out)
                     throws java.io.IOException

      Writes the contents of this node to the given output stream.
      Parameters:
      `out` - `OutputStream` to write to

      Throws:
      `java.io.IOException` - if an error occurs

    <!-- -->

    - #### print

          public void print(java.io.OutputStream out,
                            java.lang.String enc)
                     throws java.io.IOException

      Writes the contents of this node to the given output stream.
      Parameters:
      `out` - `OutputStream` to write to

      `enc` - Encoding to use for the output

      Throws:
      `java.io.IOException` - if an invalid encoding was specified or if any other error occurs

    <!-- -->

    - #### writeExternal

          public void writeExternal(java.io.ObjectOutput outArg)
                             throws java.io.IOException

      This method saves the state of the object by creating a binary compressed stream with information about this object.
      Specified by:
      `writeExternal` in interface `java.io.Externalizable`

      Parameters:
      `outArg` - The ObjectOutput stream used to write the serialized/compressed stream.

      Throws:
      `java.io.IOException` - is thrown when there is an exception while writing the serialized/compressed stream.

    <!-- -->

    - #### readExternal

          public void readExternal(java.io.ObjectInput inArg)
                            throws java.io.IOException,
                                   java.lang.ClassNotFoundException

      This method reads the information that was written to the compressed stream by the writeExternal() method, and restores the object correspondingly.
      Specified by:
      `readExternal` in interface `java.io.Externalizable`

      Parameters:
      `inArg` - the ObjectInput used for reading the compressed stream

      Throws:
      `java.io.IOException` - is thrown when there is an error in reading the input stream.

      `java.lang.ClassNotFoundException` - is thrown when the class is not found

    <!-- -->

    - #### equals

          public boolean equals(java.lang.Object obj)

      Indicates whether some other object is "equal to" this one.
      Overrides:
      `equals` in class `java.lang.Object`

      Parameters:
      `obj` - the reference object with which to compare.

      Returns:
      `true` if this object is the same as the obj argument; `false` otherwise.

    <!-- -->

    - #### hashCode

          public int hashCode()

      Returns a hash code value for the object. This method is supported for the benefit of hashtables such as those provided by `java.util.Hashtable`.
      Overrides:
      `hashCode` in class `java.lang.Object`

      Returns:
      a hash code value for this object.

    <!-- -->

    - #### getFirstChildAsOffset

          public java.lang.Object getFirstChildAsOffset()

    <!-- -->

    - #### getNextSiblingAsOffset

          public java.lang.Object getNextSiblingAsOffset()

    <!-- -->

    - #### xdbGetNodeId

          public long xdbGetNodeId()

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

- **[Prev Class](XMLMultiHandler.md)**
- **[Next Class](XMLNotation.md)**

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
