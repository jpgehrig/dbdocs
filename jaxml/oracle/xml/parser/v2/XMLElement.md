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

- **[Prev Class](XMLDOMImplementation.md)**
- **[Next Class](XMLEntity.md)**

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

## **Class XMLElement**

- **java.lang.Object**

- - **[oracle.xml.parser.v2.XMLNode](XMLNode.md)**

  - - **[oracle.xml.parser.v2.XMLNSNode](XMLNSNode.md)**

    - - **oracle.xml.parser.v2.XMLElement**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Externalizable, java.io.Serializable, java.lang.Cloneable, [NSResolver](NSResolver.md), [NSName](../../util/NSName.md), [Element](../../../../org/w3c/dom/Element.md), [EventTarget](../../../../org/w3c/dom/events/EventTarget.md), [Node](../../../../org/w3c/dom/Node.md), [ElementEditVAL](../../../../org/w3c/dom/validation/ElementEditVAL.md), [NodeEditVAL](../../../../org/w3c/dom/validation/NodeEditVAL.md)**

  <!-- -->

  **Direct Known Subclasses:**
  **[XMLDocument](XMLDocument.md), [XMLDocumentFragment](XMLDocumentFragment.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XMLElement
      extends XMLNSNode
      implements Element, java.io.Externalizable, NSName, NSResolver, ElementEditVAL

  **This class implements the DOM `Element` Interface**
  **See Also:**
  **[Serialized Form](../../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description   |
    |-------------------|-------------------------|
    | `static short`    | `ANY_CONTENTTYPE`       |
    | `static short`    | `ELEMENTS_CONTENTTYPE`  |
    | `static short`    | `EMPTY_CONTENTTYPE`     |
    | `static short`    | `MIXED_CONTENTTYPE`     |

    -

      ### **Fields inherited from class oracle.xml.parser.v2.[XMLNode](XMLNode.md)**

      **[`ATTRDECL`](XMLNode.md)`, `[`Auto_Events`](XMLNode.md)`, `[`capturing`](XMLNode.md)`, `[`DOMAttrModified`](XMLNode.md)`, `[`DOMCharacterDataModified`](XMLNode.md)`, `[`DOMNodeInserted`](XMLNode.md)`, `[`DOMNodeInsertedIntoDocument`](XMLNode.md)`, `[`DOMNodeRemoved`](XMLNode.md)`, `[`DOMNodeRemovedFromDocument`](XMLNode.md)`, `[`DOMSubtreeModified`](XMLNode.md)`, `[`ELEMENTDECL`](XMLNode.md)`, `[`KEPT_NODE`](XMLNode.md)`, `[`NAMESPACE_NODE`](XMLNode.md)`, `[`noncapturing`](XMLNode.md)`, `[`RANGE_DELETE_EVENT`](XMLNode.md)`, `[`RANGE_DELETETEXT_EVENT`](XMLNode.md)`, `[`RANGE_INSERT_EVENT`](XMLNode.md)`, `[`RANGE_INSERTTEXT_EVENT`](XMLNode.md)`, `[`RANGE_REPLACE_EVENT`](XMLNode.md)`, `[`RANGE_SETTEXT_EVENT`](XMLNode.md)`, `[`TRAVERSAL_DELETE_EVENT`](XMLNode.md)`, `[`TRAVERSAL_REPLACE_EVENT`](XMLNode.md)`, `[`XMLDECL_NODE`](XMLNode.md)**

    <!-- -->

    -

      ### **Fields inherited from interface org.w3c.dom.[Node](../../../../org/w3c/dom/Node.md)**

      **[`ATTRIBUTE_NODE`](../../../../org/w3c/dom/Node.md)`, `[`CDATA_SECTION_NODE`](../../../../org/w3c/dom/Node.md)`, `[`COMMENT_NODE`](../../../../org/w3c/dom/Node.md)`, `[`DOCUMENT_FRAGMENT_NODE`](../../../../org/w3c/dom/Node.md)`, `[`DOCUMENT_NODE`](../../../../org/w3c/dom/Node.md)`, `[`DOCUMENT_TYPE_NODE`](../../../../org/w3c/dom/Node.md)`, `[`ELEMENT_NODE`](../../../../org/w3c/dom/Node.md)`, `[`ENTITY_NODE`](../../../../org/w3c/dom/Node.md)`, `[`ENTITY_REFERENCE_NODE`](../../../../org/w3c/dom/Node.md)`, `[`NOTATION_NODE`](../../../../org/w3c/dom/Node.md)`, `[`PROCESSING_INSTRUCTION_NODE`](../../../../org/w3c/dom/Node.md)`, `[`TEXT_NODE`](../../../../org/w3c/dom/Node.md)**

    <!-- -->

    -

      ### **Fields inherited from interface org.w3c.dom.validation.[ElementEditVAL](../../../../org/w3c/dom/validation/ElementEditVAL.md)**

      **[`VAL_ANY_CONTENTTYPE`](../../../../org/w3c/dom/validation/ElementEditVAL.md)`, `[`VAL_ELEMENTS_CONTENTTYPE`](../../../../org/w3c/dom/validation/ElementEditVAL.md)`, `[`VAL_EMPTY_CONTENTTYPE`](../../../../org/w3c/dom/validation/ElementEditVAL.md)`, `[`VAL_MIXED_CONTENTTYPE`](../../../../org/w3c/dom/validation/ElementEditVAL.md)`, `[`VAL_SIMPLE_CONTENTTYPE`](../../../../org/w3c/dom/validation/ElementEditVAL.md)**

    <!-- -->

    -

      ### **Fields inherited from interface org.w3c.dom.validation.[NodeEditVAL](../../../../org/w3c/dom/validation/NodeEditVAL.md)**

      **[`VAL_FALSE`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`VAL_INCOMPLETE`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`VAL_NS_WF`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`VAL_SCHEMA`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`VAL_TRUE`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`VAL_UNKNOWN`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`VAL_WF`](../../../../org/w3c/dom/validation/NodeEditVAL.md)**

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                           | Method and Description                                                                                                                                                                                                                                                                                                |
    |-------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `short`                                                     | `canAppendChild``(`[`Node`](../../../../org/w3c/dom/Node.md)` newChild)`<br>Determines whether the `Node.appendChild` operation would make this document not compliant with the `VAL_INCOMPLETE` validity type.                                                                                                       |
    | `short`                                                     | `canInsertBefore``(`[`Node`](../../../../org/w3c/dom/Node.md)` newChild, `[`Node`](../../../../org/w3c/dom/Node.md)` refChild)`<br>Determines whether the `Node.insertBefore` operation would make this document not compliant with the `VAL_INCOMPLETE` validity type.                                               |
    | `short`                                                     | `canRemoveAttribute``(java.lang.String attrname)`<br>Verifies if an attribute by the given name can be removed.                                                                                                                                                                                                       |
    | `short`                                                     | `canRemoveAttributeNode``(`[`Node`](../../../../org/w3c/dom/Node.md)` attrNode)`<br>Determines if an attribute node can be removed.                                                                                                                                                                                   |
    | `short`                                                     | `canRemoveAttributeNS``(java.lang.String namespaceURI, java.lang.String localName)`<br>Verifies if an attribute by the given local name and namespace can be removed.                                                                                                                                                 |
    | `short`                                                     | `canRemoveChild``(`[`Node`](../../../../org/w3c/dom/Node.md)` oldChild)`<br>Determines whether the `Node.removeChild` operation would make this document not compliant with the `VAL_INCOMPLETE` validity type.                                                                                                       |
    | `short`                                                     | `canReplaceChild``(`[`Node`](../../../../org/w3c/dom/Node.md)` newChild, `[`Node`](../../../../org/w3c/dom/Node.md)` oldChild)`<br>Determines whether the `Node.replaceChild` operation would make this document not compliant with the `VAL_INCOMPLETE` validity type.                                               |
    | `short`                                                     | `canSetAttribute``(java.lang.String attrname, java.lang.String attrval)`<br>Determines if the value for specified attribute can be set.                                                                                                                                                                               |
    | `short`                                                     | `canSetAttributeNode``(`[`Attr`](../../../../org/w3c/dom/Attr.md)` attrNode)`<br>Determines if an attribute node can be added.                                                                                                                                                                                        |
    | `short`                                                     | `canSetAttributeNS``(java.lang.String namespaceURI, java.lang.String qualifiedName, java.lang.String value)`<br>Determines if the attribute with given namespace and qualified name can be created if not already present in the attribute list of the element.                                                       |
    | `short`                                                     | `canSetTextContent``(java.lang.String possibleTextContent)`<br>Determines if the text content of this node and its descendants can be set to the string passed in.                                                                                                                                                    |
    | [`NameList`](../../../../org/w3c/dom/NameList.md)           | `getAllowedAttributes``()`<br>A `NameList`, as described in \[[DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\] , of all possible attribute information items or wildcards that can appear as attributes of this element, or `null` if this element has no context or schema.              |
    | [`NameList`](../../../../org/w3c/dom/NameList.md)           | `getAllowedChildren``()`<br>A `NameList`, as described in \[ [DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\], of all possible element information items or wildcards that can appear as children of this element, or `null` if this element has no context or schema.                    |
    | [`NameList`](../../../../org/w3c/dom/NameList.md)           | `getAllowedFirstChildren``()`<br>A `NameList`, as described in \[ [DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\] , of all possible element information items or wildcards that can appear as a first child of this element, or `null` if this element has no context or schema.         |
    | [`NameList`](../../../../org/w3c/dom/NameList.md)           | `getAllowedNextSiblings``()`<br>A `NameList`, as described in \[ [DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\] , of all possible element information items or wildcards that can appear as a next sibling of this element, or `null` if this element has no context or schema.         |
    | [`NameList`](../../../../org/w3c/dom/NameList.md)           | `getAllowedParents``()`<br>A `NameList`, as described in \[ [DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\] , of all possible element information items that can appear as a parent this element, or `null` if this element has no context or schema.                                    |
    | [`NameList`](../../../../org/w3c/dom/NameList.md)           | `getAllowedPreviousSiblings``()`<br>A `NameList`, as described in \[ [DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\] , of all possible element information items or wildcards that can appear as a previous sibling of this element, or `null` if this element has no context or schema. |
    | `java.lang.String`                                          | `getAttribute``(java.lang.String name)`<br>Retrieves an attribute value by name.                                                                                                                                                                                                                                      |
    | [`Attr`](../../../../org/w3c/dom/Attr.md)                   | `getAttributeNode``(java.lang.String name)`<br>Retrieves an `Attr` node by name.                                                                                                                                                                                                                                      |
    | [`Attr`](../../../../org/w3c/dom/Attr.md)                   | `getAttributeNode``(java.lang.String name, java.lang.String namespace)`<br>Deprecated. <br>As of DOM 2                                                                                                                                                                                                                |
    | [`Attr`](../../../../org/w3c/dom/Attr.md)                   | `getAttributeNodeNS``(java.lang.String namespaceURI, java.lang.String localName)`<br>Retrieves an Attr node by local name and namespace URI.                                                                                                                                                                          |
    | `java.lang.String`                                          | `getAttributeNS``(java.lang.String namespaceURI, java.lang.String localName)`<br>Retrieves an attribute value by local name and namespace URI.                                                                                                                                                                        |
    | [`NamedNodeMap`](../../../../org/w3c/dom/NamedNodeMap.md)   | `getAttributes``()`<br>A `NamedNodeMap` containing the attributes of this node (if it is an `Element`) or `null` otherwise.                                                                                                                                                                                           |
    | [`NodeList`](../../../../org/w3c/dom/NodeList.md)           | `getChildrenByTagName``(java.lang.String name)`<br>Returns a `NodeList` of all immediate children with a given tag name,                                                                                                                                                                                              |
    | [`NodeList`](../../../../org/w3c/dom/NodeList.md)           | `getChildrenByTagName``(java.lang.String name, java.lang.String ns)`<br>Returns a `NodeList` of all immediate children with a given tag name and namespace                                                                                                                                                            |
    | `short`                                                     | `getContentType``()`<br>The content type of an element.                                                                                                                                                                                                                                                               |
    | `java.lang.String`                                          | `getDefaultValue``()`<br>The default value specified in an attribute or an element declaration or `null` if unspecified.                                                                                                                                                                                              |
    | [`NodeList`](../../../../org/w3c/dom/NodeList.md)           | `getElementsByTagName``(java.lang.String name)`<br>Returns a `NodeList` of all descendant elements with a given tag name, in the order in which they would be encountered in a preorder traversal of the `Element` tree.                                                                                              |
    | [`NodeList`](../../../../org/w3c/dom/NodeList.md)           | `getElementsByTagNameNS``(java.lang.String namespaceURI, java.lang.String localName)`<br>Returns a NodeList of all the descendant Elements with a given local name and namespace URI in the order in which they are encountered in a preorder traversal of this Element tree.                                         |
    | [`DOMStringList`](../../../../org/w3c/dom/DOMStringList.md) | `getEnumeratedValues``()`<br>A `DOMStringList`, as described in \[[DOM Level 3 Core](http://www.w3.org/TR/2003/CR-DOM-Level-3-Core-20031107)\] , of distinct values for an attribute or an element declaration or `null` if unspecified.                                                                              |
    | `java.lang.String`                                          | `getExpandedName``()`<br>Get the fully resolved name for this element.                                                                                                                                                                                                                                                |
    | [`XMLNode`](XMLNode.md)                                     | `getFirstAttribute``()`<br>Retrieves the first `Attr`.                                                                                                                                                                                                                                                                |
    | `java.lang.String`                                          | `getLocalName``()`<br>Gets the Local Name of this node                                                                                                                                                                                                                                                                |
    | `java.lang.String`                                          | `getNamespaceURI``()`<br>Gets the namespace URI of this node.                                                                                                                                                                                                                                                         |
    | `XMLElement`                                                | `getNextSiblingByName``()`                                                                                                                                                                                                                                                                                            |
    | `java.lang.String`                                          | `getNodeName``()`<br>Gets the name of this node, depending on its type                                                                                                                                                                                                                                                |
    | `short`                                                     | `getNodeType``()`<br>Gets a code representing the type of the underlying object                                                                                                                                                                                                                                       |
    | `java.lang.String`                                          | `getPrefix``()`<br>Get the namespace prefix for this element.                                                                                                                                                                                                                                                         |
    | `java.lang.String`                                          | `getQualifiedName``()`<br>Deprecated. <br>- Use getNodeName                                                                                                                                                                                                                                                           |
    | [`NameList`](../../../../org/w3c/dom/NameList.md)           | `getRequiredAttributes``()`<br>A `NameList`, as described in \[ [DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\], of required attribute information items that must appear on this element, or `null` if this element has no context or schema.                                           |
    | `java.lang.String`                                          | `getTagName``()`<br>Gets the name of the element.                                                                                                                                                                                                                                                                     |
    | `boolean`                                                   | `hasAttribute``(java.lang.String name)`<br>Returns true when an attribute with a given name is specified on this element or has a default value, false otherwise.                                                                                                                                                     |
    | `boolean`                                                   | `hasAttributeNS``(java.lang.String namespaceURI, java.lang.String localName)`<br>Returns true when an attribute with a given local name and namespace URI is specified on this element or has a default value,false otherwise                                                                                         |
    | `boolean`                                                   | `hasAttributes``()`<br>Returns whether this node (if it is an element) has any attributes.                                                                                                                                                                                                                            |
    | `short`                                                     | `isElementDefined``(java.lang.String name)`<br>Determines if `name` is defined in the schema.                                                                                                                                                                                                                         |
    | `short`                                                     | `isElementDefinedNS``(java.lang.String namespaceURI, java.lang.String name)`<br>Determines if `name` in this namespace is defined in the current context.                                                                                                                                                             |
    | `short`                                                     | `nodeValidity``(short wFValidityCheckLevel)`<br>Determines if the node is valid relative to the validation type specified in `valType`.                                                                                                                                                                               |
    | `void`                                                      | `normalize``()`<br>Deprecated. <br>As of DOM 2                                                                                                                                                                                                                                                                        |
    | `void`                                                      | `removeAttribute``(java.lang.String name)`<br>Removes an attribute by name.                                                                                                                                                                                                                                           |
    | [`Attr`](../../../../org/w3c/dom/Attr.md)                   | `removeAttributeNode``(`[`Attr`](../../../../org/w3c/dom/Attr.md)` attr)`<br>Removes the specified attribute.                                                                                                                                                                                                         |
    | `void`                                                      | `removeAttributeNS``(java.lang.String namespaceURI, java.lang.String localName)`<br>Removes an attribute by local name and namespace URI.                                                                                                                                                                             |
    | `void`                                                      | `reportSAXEvents``(`[`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)` cntHandler)`<br>Report SAX Events from a DOM Tree                                                                                                                                                                                  |
    | `java.lang.String`                                          | `resolveNamespacePrefix``(java.lang.String prefix)`<br>Given a namespace prefix, find the namespace definition in scope in this element.                                                                                                                                                                              |
    | `void`                                                      | `setAttribute``(java.lang.String name, java.lang.String value)`<br>Adds a new attribute.                                                                                                                                                                                                                              |
    | [`Attr`](../../../../org/w3c/dom/Attr.md)                   | `setAttributeNode``(`[`Attr`](../../../../org/w3c/dom/Attr.md)` attr)`<br>Adds a new attribute.                                                                                                                                                                                                                       |
    | [`Attr`](../../../../org/w3c/dom/Attr.md)                   | `setAttributeNodeNS``(`[`Attr`](../../../../org/w3c/dom/Attr.md)` newAttr)`<br>Adds a new attribute.                                                                                                                                                                                                                  |
    | `void`                                                      | `setAttributeNS``(java.lang.String namespaceURI, java.lang.String qualifiedName, java.lang.String value)`<br>Adds a new attribute.                                                                                                                                                                                    |
    | `void`                                                      | `setPrefix``(java.lang.String prefix)`<br>Sets the prefix of this node                                                                                                                                                                                                                                                |
    | `boolean`                                                   | `validateContent``(`[`DTD`](DTD.md)` dtd)`<br>Validates the content of a element node.                                                                                                                                                                                                                                |
    | `boolean`                                                   | `validateContent``(`[`XMLSchema`](../schema/XMLSchema.md)` schema)`<br>Validates the content of the element against given XML Schema                                                                                                                                                                                  |
    | `boolean`                                                   | `validateContent``(`[`XMLSchema`](../schema/XMLSchema.md)` schema, java.lang.String mode)`<br>Validates the content of the element against given XML Schema in the given mode.                                                                                                                                        |
    | [`XMLNode`](XMLNode.md)                                     | `validateContent``(`[`XSDValidator`](../schema/XSDValidator.md)` validator, boolean flag)`<br>Validates the content of the element using given validator                                                                                                                                                              |

    - ### Methods inherited from class oracle.xml.parser.v2.[XMLNSNode](XMLNSNode.md)

      [`addText`](XMLNSNode.md)`, `[`addText`](XMLNSNode.md)`, `[`appendChild`](XMLNSNode.md)`, `[`getChildNodes`](XMLNSNode.md)`, `[`getFirstChild`](XMLNSNode.md)`, `[`getLastChild`](XMLNSNode.md)`, `[`getText`](XMLNSNode.md)`, `[`insertBefore`](XMLNSNode.md)`, `[`removeChild`](XMLNSNode.md)`, `[`replaceChild`](XMLNSNode.md)

    <!-- -->

    - ### Methods inherited from class oracle.xml.parser.v2.[XMLNode](XMLNode.md)

      [`addEventListener`](XMLNode.md)`, `[`cloneNode`](XMLNode.md)`, `[`dispatchEvent`](XMLNode.md)`, `[`equals`](XMLNode.md)`, `[`getColumnNumber`](XMLNode.md)`, `[`getDebugMode`](XMLNode.md)`, `[`getFirstChildAsOffset`](XMLNode.md)`, `[`getLineNumber`](XMLNode.md)`, `[`getNextSibling`](XMLNode.md)`, `[`getNextSiblingAsOffset`](XMLNode.md)`, `[`getNodeValue`](XMLNode.md)`, `[`getNodeValueAsBinaryStream`](XMLNode.md)`, `[`getNodeValueAsBinaryStream`](XMLNode.md)`, `[`getNodeValueAsCharacterStream`](XMLNode.md)`, `[`getNodeValueAsCharacterStream`](XMLNode.md)`, `[`getOwnerDocument`](XMLNode.md)`, `[`getParentNode`](XMLNode.md)`, `[`getPreviousSibling`](XMLNode.md)`, `[`getPrimitiveTypeId`](XMLNode.md)`, `[`getProperty`](XMLNode.md)`, `[`getSystemId`](XMLNode.md)`, `[`getXMLError`](XMLNode.md)`, `[`hasChildNodes`](XMLNode.md)`, `[`hashCode`](XMLNode.md)`, `[`isDocumentFlag`](XMLNode.md)`, `[`isNodeFlag`](XMLNode.md)`, `[`isSupported`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`readExternal`](XMLNode.md)`, `[`removeEventListener`](XMLNode.md)`, `[`resetNodeFlag`](XMLNode.md)`, `[`selectNodes`](XMLNode.md)`, `[`selectNodes`](XMLNode.md)`, `[`selectSingleNode`](XMLNode.md)`, `[`selectSingleNode`](XMLNode.md)`, `[`setDebugInfo`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeValue`](XMLNode.md)`, `[`setNodeValueAsBinaryStream`](XMLNode.md)`, `[`setNodeValueAsBinaryStream`](XMLNode.md)`, `[`setNodeValueAsCharacterStream`](XMLNode.md)`, `[`setNodeValueAsCharacterStream`](XMLNode.md)`, `[`setProperty`](XMLNode.md)`, `[`transformNode`](XMLNode.md)`, `[`valueOf`](XMLNode.md)`, `[`valueOf`](XMLNode.md)`, `[`writeExternal`](XMLNode.md)`, `[`xdbGetNodeId`](XMLNode.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface org.w3c.dom.[Node](../../../../org/w3c/dom/Node.md)

      [`appendChild`](../../../../org/w3c/dom/Node.md)`, `[`cloneNode`](../../../../org/w3c/dom/Node.md)`, `[`getChildNodes`](../../../../org/w3c/dom/Node.md)`, `[`getFirstChild`](../../../../org/w3c/dom/Node.md)`, `[`getLastChild`](../../../../org/w3c/dom/Node.md)`, `[`getNextSibling`](../../../../org/w3c/dom/Node.md)`, `[`getNodeValue`](../../../../org/w3c/dom/Node.md)`, `[`getOwnerDocument`](../../../../org/w3c/dom/Node.md)`, `[`getParentNode`](../../../../org/w3c/dom/Node.md)`, `[`getPreviousSibling`](../../../../org/w3c/dom/Node.md)`, `[`hasChildNodes`](../../../../org/w3c/dom/Node.md)`, `[`insertBefore`](../../../../org/w3c/dom/Node.md)`, `[`isSupported`](../../../../org/w3c/dom/Node.md)`, `[`removeChild`](../../../../org/w3c/dom/Node.md)`, `[`replaceChild`](../../../../org/w3c/dom/Node.md)`, `[`setNodeValue`](../../../../org/w3c/dom/Node.md)

    <!-- -->

    - ### Methods inherited from interface java.io.Externalizable

      `readExternal, writeExternal`

    <!-- -->

    - ### Methods inherited from interface oracle.xml.util.[NSName](../../util/NSName.md)

      [`getNamespace`](../../util/NSName.md)

    <!-- -->

    - ### Methods inherited from interface org.w3c.dom.validation.[ElementEditVAL](../../../../org/w3c/dom/validation/ElementEditVAL.md)

      [`getAllowedFirstChildElements`](../../../../org/w3c/dom/validation/ElementEditVAL.md)

<!-- -->

- - ### Field Detail

    - #### EMPTY_CONTENTTYPE

          public static final short EMPTY_CONTENTTYPE

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ANY_CONTENTTYPE

          public static final short ANY_CONTENTTYPE

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### MIXED_CONTENTTYPE

          public static final short MIXED_CONTENTTYPE

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ELEMENTS_CONTENTTYPE

          public static final short ELEMENTS_CONTENTTYPE

      See Also:
      [Constant Field Values](../../../../constant-values.md)

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

    - #### getTagName

          public java.lang.String getTagName()

      Gets the name of the element.
      Specified by:
      [`getTagName`](../../../../org/w3c/dom/Element.md) in interface [`Element`](../../../../org/w3c/dom/Element.md)

      Returns:
      The element name

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

      Sets the prefix of this node
      Specified by:
      [`setPrefix`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`setPrefix`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Parameters:
      `prefix` - set the prefix

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - if any DOM Exception occurs

    <!-- -->

    - #### getAttributes

          public NamedNodeMap getAttributes()

      A `NamedNodeMap` containing the attributes of this node (if it is an `Element`) or `null` otherwise.
      Specified by:
      [`getAttributes`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`getAttributes`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Returns:
      The list of attributes of this element

    <!-- -->

    - #### normalize

          public void normalize()

      Deprecated. As of DOM 2
      Puts all `Text` nodes in the full depth of the sub-tree underneath this `Element` into a "normal" form where only markup (e.g., tags, comments, processing instructions, CDATA sections, and entity references) separates `Text` nodes, i.e., there are no adjacent `Text` nodes. This can be used to ensure that the DOM view of a document is the same as if it were saved and re-loaded, and is useful when operations (such as XPointer lookups) that depend on a particular doc1ument tree structure are to be used.
      Specified by:
      [`normalize`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`normalize`](XMLNSNode.md) in class [`XMLNSNode`](XMLNSNode.md)

      See Also:
      [`XMLNode.normalize()`](XMLNode.md)

    <!-- -->

    - #### hasAttribute

          public boolean hasAttribute(java.lang.String name)

      Returns true when an attribute with a given name is specified on this element or has a default value, false otherwise.
      Specified by:
      [`hasAttribute`](../../../../org/w3c/dom/Element.md) in interface [`Element`](../../../../org/w3c/dom/Element.md)

      Parameters:
      `name` - - Name of the attribute whose presence is checked as String

      Returns:
      true if the attribute whith the specified name is present, else null

      Since:
      DOM 2

    <!-- -->

    - #### hasAttributeNS

          public boolean hasAttributeNS(java.lang.String namespaceURI,
                                        java.lang.String localName)

      Returns true when an attribute with a given local name and namespace URI is specified on this element or has a default value,false otherwise
      Specified by:
      [`hasAttributeNS`](../../../../org/w3c/dom/Element.md) in interface [`Element`](../../../../org/w3c/dom/Element.md)

      Parameters:
      `namespaceURI` - - The namespace uri as String

      `localName` - - The local name of the attribute whose presence is checked as String

      Returns:
      true when an attribute with a given local name and namespace URI is specified on this element or has a default value,false otherwise

      Since:
      DOM 2

    <!-- -->

    - #### hasAttributes

          public boolean hasAttributes()

      Returns whether this node (if it is an element) has any attributes.
      Specified by:
      [`hasAttributes`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`hasAttributes`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Returns:
      `true` if this node has any attributes, `false` otherwise.

      Since:
      DOM Level 2

    <!-- -->

    - #### getAttribute

          public java.lang.String getAttribute(java.lang.String name)

      Retrieves an attribute value by name.
      Specified by:
      [`getAttribute`](../../../../org/w3c/dom/Element.md) in interface [`Element`](../../../../org/w3c/dom/Element.md)

      Parameters:
      `name` - The name of the attribute to retrieve.

      Returns:
      The `Attr` value as a string, or the empty string if that attribute does not have a specified or default value.

    <!-- -->

    - #### setAttribute

          public void setAttribute(java.lang.String name,
                                   java.lang.String value)
                            throws DOMException

      Adds a new attribute. If an attribute with that name is already present in the element, its value is changed to be that of the value parameter. This value is a simple string, it is not parsed as it is being set. So any markup (such as syntax to be recognized as an entity reference) is treated as literal text, and needs to be appropriately escaped by the implementation when it is written out. In order to assign an attribute value that contains entity references, the user must create an `Attr` node plus any `Text` and `EntityReference` nodes, build the appropriate subtree, and use `setAttributeNode` to assign it as the value of an attribute. This method is namespace unaware and hence wont result in update of namespace table if a new attr is added thru this method
      Specified by:
      [`setAttribute`](../../../../org/w3c/dom/Element.md) in interface [`Element`](../../../../org/w3c/dom/Element.md)

      Parameters:
      `name` - The name of the attribute to create or alter.

      `value` - Value to set in string form.

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - INVALID_CHARACTER_ERR: Raised if the specified name contains an invalid character.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.

    <!-- -->

    - #### removeAttribute

          public void removeAttribute(java.lang.String name)
                               throws DOMException

      Removes an attribute by name. If the removed attribute has a default value it is immediately replaced.
      Specified by:
      [`removeAttribute`](../../../../org/w3c/dom/Element.md) in interface [`Element`](../../../../org/w3c/dom/Element.md)

      Parameters:
      `name` - The name of the attribute to remove.

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.

    <!-- -->

    - #### getAttributeNS

          public java.lang.String getAttributeNS(java.lang.String namespaceURI,
                                                 java.lang.String localName)

      Retrieves an attribute value by local name and namespace URI.
      Specified by:
      [`getAttributeNS`](../../../../org/w3c/dom/Element.md) in interface [`Element`](../../../../org/w3c/dom/Element.md)

      Parameters:
      `namespaceURI` - namespace of the attribute requested

      `localName` - local name of the attribute requested

      Returns:
      the value of the attribute with the above mentioned namespace URI and localName if it exists ,else null.

      Since:
      DOM 2

    <!-- -->

    - #### setAttributeNS

          public void setAttributeNS(java.lang.String namespaceURI,
                                     java.lang.String qualifiedName,
                                     java.lang.String value)
                              throws DOMException

      Adds a new attribute. If an attribute with the same local name and namespace URI is already present on the element, its prefix is changed to be the prefix part of the qualifiedName, and its value is changed to be the value parameter. This value is a simple string; it is not parsed as it is being set. So any markup (such as syntax to be recognized as an entity reference) is treated as literal text, and needs to be appropriately escaped by the implementation when it is written out.
      Specified by:
      [`setAttributeNS`](../../../../org/w3c/dom/Element.md) in interface [`Element`](../../../../org/w3c/dom/Element.md)

      Parameters:
      `namespaceURI` - namespace of the attribute to be added

      `qualifiedName` - qualified name of the attribute to be added

      `value` - value of the attribute to be added

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - INVALID_CHARACTER_ERR: Raised if the specified qualified name contains illegal Characters NAMESPACE_ERR : Raised if the qualified name is malformed if the qualified name has a prefix and the namespace URI is null or an empty string,or if the qulaifiedName is "xmlns" and namespace URI is different from "http://www.w3.org/2000/xmlns/" ,or if qualifiedName has a prefix that is "xml" and the namespaceURI is different from http://www.w3.org/XML/1998/namespaces NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly

      Since:
      DOM 2

    <!-- -->

    - #### removeAttributeNS

          public void removeAttributeNS(java.lang.String namespaceURI,
                                        java.lang.String localName)
                                 throws DOMException

      Removes an attribute by local name and namespace URI.
      Specified by:
      [`removeAttributeNS`](../../../../org/w3c/dom/Element.md) in interface [`Element`](../../../../org/w3c/dom/Element.md)

      Parameters:
      `namespaceURI` - - The namespace uri as String

      `localName` - - The local name of the attribute to be removed as String

      Throws:
      `DOMEXception` - NO_MODIFICATIONS_ALLOWED_ERR : if this element is readonly

      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.

      Since:
      DOM 2

    <!-- -->

    - #### getAttributeNode

          public Attr getAttributeNode(java.lang.String name)

      Retrieves an `Attr` node by name.
      Specified by:
      [`getAttributeNode`](../../../../org/w3c/dom/Element.md) in interface [`Element`](../../../../org/w3c/dom/Element.md)

      Parameters:
      `name` - The name of the attribute to retrieve.

      Returns:
      The `Attr` node with the specified attribute name or `null` if there is no such attribute.

    <!-- -->

    - #### setAttributeNode

          public Attr setAttributeNode(Attr attr)
                                throws DOMException

      Adds a new attribute. If an attribute with that name is already present in the element, it is replaced by the new one.
      Specified by:
      [`setAttributeNode`](../../../../org/w3c/dom/Element.md) in interface [`Element`](../../../../org/w3c/dom/Element.md)

      Parameters:
      `attr` - The `Attr` node to add to the attribute list.

      Returns:
      If the `newAttr` attribute replaces an existing attribute with the same name, the previously existing `Attr` node is returned, otherwise `null` is returned.

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - WRONG_DOCUMENT_ERR: Raised if `newAttr` was created from a different document than the one that created the element.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.
      INUSE_ATTRIBUTE_ERR: Raised if `newAttr` is already an attribute of another `Element` object. The DOM user must explicitly clone `Attr` nodes to re-use them in other elements.

    <!-- -->

    - #### removeAttributeNode

          public Attr removeAttributeNode(Attr attr)
                                   throws DOMException

      Removes the specified attribute.
      Specified by:
      [`removeAttributeNode`](../../../../org/w3c/dom/Element.md) in interface [`Element`](../../../../org/w3c/dom/Element.md)

      Parameters:
      `attr` - The `Attr` node to remove from the attribute list. If the removed `Attr` has a default value it is immediately replaced.

      Returns:
      The `Attr` node that was removed.

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.
      NOT_FOUND_ERR: Raised if `oldAttr` is not an attribute of the element.

    <!-- -->

    - #### getAttributeNodeNS

          public Attr getAttributeNodeNS(java.lang.String namespaceURI,
                                         java.lang.String localName)

      Retrieves an Attr node by local name and namespace URI.
      Specified by:
      [`getAttributeNodeNS`](../../../../org/w3c/dom/Element.md) in interface [`Element`](../../../../org/w3c/dom/Element.md)

      Parameters:
      `namespaceURI` - namespace URI

      `localName` - the attribute to be retrieved

      Returns:
      Attribute with the given namespaceURI and localName if it exists, else null.

      Since:
      DOM 2

    <!-- -->

    - #### setAttributeNodeNS

          public Attr setAttributeNodeNS(Attr newAttr)
                                  throws DOMException

      Adds a new attribute. If an attribute with that local name and that namespace URI is already present in the element, it is replaced by the new one.
      Specified by:
      [`setAttributeNodeNS`](../../../../org/w3c/dom/Element.md) in interface [`Element`](../../../../org/w3c/dom/Element.md)

      Parameters:
      `newAttr` - node to be added

      Returns:
      the Attribute Node added

      Throws:
      [`DOMException`](../../../../org/w3c/dom/DOMException.md) - WRONG_DOCUMENT_ERR : raised if the newAttr was created from a document different from the one that created the document NO_MODIFICATIONS_ALLOWED_ERR :Raised if this element is readonly INUSE_ATTRIBUTE_ERR : Raised if newAttr is already an attribute of another Element object

      Since:
      DOM 2

    <!-- -->

    - #### getElementsByTagName

          public NodeList getElementsByTagName(java.lang.String name)

      Returns a `NodeList` of all descendant elements with a given tag name, in the order in which they would be encountered in a preorder traversal of the `Element` tree.
      Specified by:
      [`getElementsByTagName`](../../../../org/w3c/dom/Element.md) in interface [`Element`](../../../../org/w3c/dom/Element.md)

      Parameters:
      `name` - The name of the tag to match on. The special value "\*" matches all tags.

      Returns:
      A list of matching `Element` nodes.

    <!-- -->

    - #### getElementsByTagNameNS

          public NodeList getElementsByTagNameNS(java.lang.String namespaceURI,
                                                 java.lang.String localName)

      Returns a NodeList of all the descendant Elements with a given local name and namespace URI in the order in which they are encountered in a preorder traversal of this Element tree.
      Specified by:
      [`getElementsByTagNameNS`](../../../../org/w3c/dom/Element.md) in interface [`Element`](../../../../org/w3c/dom/Element.md)

      Parameters:
      `namespaceURI` - the namespace of the element

      `localName` - the local name of the element

      Returns:
      A new `NodeList` object containing all the matched `Elements`.

      Since:
      DOM 2

    <!-- -->

    - #### getDefaultValue

          public java.lang.String getDefaultValue()

      The default value specified in an attribute or an element declaration or `null` if unspecified. Elena wanted mention of XML Schema's canonical lexical representation here. Why?
      Specified by:
      [`getDefaultValue`](../../../../org/w3c/dom/validation/NodeEditVAL.md) in interface [`NodeEditVAL`](../../../../org/w3c/dom/validation/NodeEditVAL.md)

      Overrides:
      [`getDefaultValue`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

    <!-- -->

    - #### getEnumeratedValues

          public DOMStringList getEnumeratedValues()

      A `DOMStringList`, as described in \[[DOM Level 3 Core](http://www.w3.org/TR/2003/CR-DOM-Level-3-Core-20031107)\] , of distinct values for an attribute or an element declaration or `null` if unspecified. If the schema is a W3C XML schema, this is a list of strings which are lexical representations corresponding to the values in the \[value\] property of the enumeration component for the type of the attribute or element. It is recommended that the canonical lexical representations of the values be used.
      Specified by:
      [`getEnumeratedValues`](../../../../org/w3c/dom/validation/NodeEditVAL.md) in interface [`NodeEditVAL`](../../../../org/w3c/dom/validation/NodeEditVAL.md)

      Overrides:
      [`getEnumeratedValues`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

    <!-- -->

    - #### canInsertBefore

          public short canInsertBefore(Node newChild,
                                       Node refChild)

      Determines whether the `Node.insertBefore` operation would make this document not compliant with the `VAL_INCOMPLETE` validity type.
      Specified by:
      [`canInsertBefore`](../../../../org/w3c/dom/validation/NodeEditVAL.md) in interface [`NodeEditVAL`](../../../../org/w3c/dom/validation/NodeEditVAL.md)

      Overrides:
      [`canInsertBefore`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

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
      [`canRemoveChild`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

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
      [`canReplaceChild`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

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
      [`canAppendChild`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

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

      Overrides:
      [`nodeValidity`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Parameters:
      `wFValidityCheckLevel` - Flag to tell at what level validity and well-formedness checking is done.

      Returns:
      A validation state constant.

    <!-- -->

    - #### getAllowedChildren

          public NameList getAllowedChildren()

      A `NameList`, as described in \[ [DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\], of all possible element information items or wildcards that can appear as children of this element, or `null` if this element has no context or schema. Duplicate pairs of {namespaceURI, name} are eliminated.
      Specified by:
      [`getAllowedChildren`](../../../../org/w3c/dom/validation/ElementEditVAL.md) in interface [`ElementEditVAL`](../../../../org/w3c/dom/validation/ElementEditVAL.md)

    <!-- -->

    - #### getAllowedFirstChildren

          public NameList getAllowedFirstChildren()

      A `NameList`, as described in \[ [DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\] , of all possible element information items or wildcards that can appear as a first child of this element, or `null` if this element has no context or schema. Duplicate pairs of {namespaceURI, name} are eliminated.

    <!-- -->

    - #### getAllowedParents

          public NameList getAllowedParents()

      A `NameList`, as described in \[ [DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\] , of all possible element information items that can appear as a parent this element, or `null` if this element has no context or schema.
      Specified by:
      [`getAllowedParents`](../../../../org/w3c/dom/validation/ElementEditVAL.md) in interface [`ElementEditVAL`](../../../../org/w3c/dom/validation/ElementEditVAL.md)

    <!-- -->

    - #### getAllowedNextSiblings

          public NameList getAllowedNextSiblings()

      A `NameList`, as described in \[ [DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\] , of all possible element information items or wildcards that can appear as a next sibling of this element, or `null` if this element has no context or schema. Duplicate pairs of {namespaceURI, name} are eliminated.
      Specified by:
      [`getAllowedNextSiblings`](../../../../org/w3c/dom/validation/ElementEditVAL.md) in interface [`ElementEditVAL`](../../../../org/w3c/dom/validation/ElementEditVAL.md)

    <!-- -->

    - #### getAllowedPreviousSiblings

          public NameList getAllowedPreviousSiblings()

      A `NameList`, as described in \[ [DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\] , of all possible element information items or wildcards that can appear as a previous sibling of this element, or `null` if this element has no context or schema.
      Specified by:
      [`getAllowedPreviousSiblings`](../../../../org/w3c/dom/validation/ElementEditVAL.md) in interface [`ElementEditVAL`](../../../../org/w3c/dom/validation/ElementEditVAL.md)

    <!-- -->

    - #### getAllowedAttributes

          public NameList getAllowedAttributes()

      Description copied from interface: [`ElementEditVAL`](../../../../org/w3c/dom/validation/ElementEditVAL.md)
      A `NameList`, as described in \[[DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\] , of all possible attribute information items or wildcards that can appear as attributes of this element, or `null` if this element has no context or schema. Duplicate pairs of {namespaceURI, name} are eliminated.
      Specified by:
      [`getAllowedAttributes`](../../../../org/w3c/dom/validation/ElementEditVAL.md) in interface [`ElementEditVAL`](../../../../org/w3c/dom/validation/ElementEditVAL.md)

    <!-- -->

    - #### getRequiredAttributes

          public NameList getRequiredAttributes()

      A `NameList`, as described in \[ [DOM Level 3 Core](http://www.w3.org/TR/2002/WD-DOM-Level-3-Core-20021022)\], of required attribute information items that must appear on this element, or `null` if this element has no context or schema. Duplicate pairs of {namespaceURI, name} are eliminated.
      Specified by:
      [`getRequiredAttributes`](../../../../org/w3c/dom/validation/ElementEditVAL.md) in interface [`ElementEditVAL`](../../../../org/w3c/dom/validation/ElementEditVAL.md)

    <!-- -->

    - #### getContentType

          public short getContentType()

      The content type of an element.
      Specified by:
      [`getContentType`](../../../../org/w3c/dom/validation/ElementEditVAL.md) in interface [`ElementEditVAL`](../../../../org/w3c/dom/validation/ElementEditVAL.md)

    <!-- -->

    - #### canSetAttribute

          public short canSetAttribute(java.lang.String attrname,
                                       java.lang.String attrval)

      Determines if the value for specified attribute can be set.
      Specified by:
      [`canSetAttribute`](../../../../org/w3c/dom/validation/ElementEditVAL.md) in interface [`ElementEditVAL`](../../../../org/w3c/dom/validation/ElementEditVAL.md)

      Parameters:
      `attrname` - Name of attribute.

      `attrval` - Value to be assigned to the attribute.

      Returns:
      A validation state constant.

    <!-- -->

    - #### canSetAttributeNode

          public short canSetAttributeNode(Attr attrNode)

      Determines if an attribute node can be added.
      Specified by:
      [`canSetAttributeNode`](../../../../org/w3c/dom/validation/ElementEditVAL.md) in interface [`ElementEditVAL`](../../../../org/w3c/dom/validation/ElementEditVAL.md)

      Parameters:
      `attrNode` - `Node` in which the attribute can possibly be set.

      Returns:
      A validation state constant.

    <!-- -->

    - #### canSetAttributeNS

          public short canSetAttributeNS(java.lang.String namespaceURI,
                                         java.lang.String qualifiedName,
                                         java.lang.String value)

      Determines if the attribute with given namespace and qualified name can be created if not already present in the attribute list of the element. If the attribute with the same qualified name and namespaceURI is already present in the element's attribute list, it tests whether the value of the attribute and its prefix can be set to the new value. See DOM core `setAttributeNS`.
      Specified by:
      [`canSetAttributeNS`](../../../../org/w3c/dom/validation/ElementEditVAL.md) in interface [`ElementEditVAL`](../../../../org/w3c/dom/validation/ElementEditVAL.md)

      Parameters:
      `namespaceURI` - `namespaceURI` of namespace.

      `qualifiedName` - Qualified name of attribute.

      `value` - Value to be assigned to the attribute.

      Returns:
      A validation state constant.

    <!-- -->

    - #### canRemoveAttribute

          public short canRemoveAttribute(java.lang.String attrname)

      Verifies if an attribute by the given name can be removed.
      Specified by:
      [`canRemoveAttribute`](../../../../org/w3c/dom/validation/ElementEditVAL.md) in interface [`ElementEditVAL`](../../../../org/w3c/dom/validation/ElementEditVAL.md)

      Parameters:
      `attrname` - Name of attribute.

      Returns:
      A validation state constant.

    <!-- -->

    - #### canRemoveAttributeNS

          public short canRemoveAttributeNS(java.lang.String namespaceURI,
                                            java.lang.String localName)

      Verifies if an attribute by the given local name and namespace can be removed.
      Specified by:
      [`canRemoveAttributeNS`](../../../../org/w3c/dom/validation/ElementEditVAL.md) in interface [`ElementEditVAL`](../../../../org/w3c/dom/validation/ElementEditVAL.md)

      Parameters:
      `namespaceURI` - The namespace URI of the attribute to remove.

      `localName` - Local name of the attribute to be removed.

      Returns:
      A validation state constant.

    <!-- -->

    - #### canRemoveAttributeNode

          public short canRemoveAttributeNode(Node attrNode)

      Determines if an attribute node can be removed.
      Specified by:
      [`canRemoveAttributeNode`](../../../../org/w3c/dom/validation/ElementEditVAL.md) in interface [`ElementEditVAL`](../../../../org/w3c/dom/validation/ElementEditVAL.md)

      Parameters:
      `attrNode` - The `Attr` node to remove from the attribute list.

      Returns:
      A validation state constant.

    <!-- -->

    - #### canSetTextContent

          public short canSetTextContent(java.lang.String possibleTextContent)

      Determines if the text content of this node and its descendants can be set to the string passed in.
      Parameters:
      `possibleTextContent` - Possible text content string.

      Returns:
      A validation state constant.

    <!-- -->

    - #### isElementDefined

          public short isElementDefined(java.lang.String name)

      Determines if `name` is defined in the schema. This only applies to global declarations.
      Specified by:
      [`isElementDefined`](../../../../org/w3c/dom/validation/ElementEditVAL.md) in interface [`ElementEditVAL`](../../../../org/w3c/dom/validation/ElementEditVAL.md)

      Parameters:
      `name` - Name of element.

      Returns:
      A validation state constant.

    <!-- -->

    - #### isElementDefinedNS

          public short isElementDefinedNS(java.lang.String namespaceURI,
                                          java.lang.String name)

      Determines if `name` in this namespace is defined in the current context. Thus not only does this apply to global declarations . but depending on the content, this may also apply to local definitions.
      Specified by:
      [`isElementDefinedNS`](../../../../org/w3c/dom/validation/ElementEditVAL.md) in interface [`ElementEditVAL`](../../../../org/w3c/dom/validation/ElementEditVAL.md)

      Parameters:
      `namespaceURI` - `namespaceURI` of namespace.

      `name` - Name of element.

      Returns:
      A validation state constant.

    <!-- -->

    - #### getExpandedName

          public java.lang.String getExpandedName()

      Get the fully resolved name for this element.
      Specified by:
      [`getExpandedName`](../../util/NSName.md) in interface [`NSName`](../../util/NSName.md)

      Returns:
      the fully resolved name

    <!-- -->

    - #### getFirstAttribute

          public XMLNode getFirstAttribute()

      Retrieves the first `Attr`.
      Returns:
      The first `Attr` node `null` if there is no attribute.

    <!-- -->

    - #### getNextSiblingByName

          public XMLElement getNextSiblingByName()

    <!-- -->

    - #### resolveNamespacePrefix

          public java.lang.String resolveNamespacePrefix(java.lang.String prefix)

      Given a namespace prefix, find the namespace definition in scope in this element.
      Specified by:
      [`resolveNamespacePrefix`](NSResolver.md) in interface [`NSResolver`](NSResolver.md)

      Parameters:
      `prefix` - Namespace prefix to be resolved if the prefix == \#default, return the default namespace

      Returns:
      the resolved Namespace (null, if prefix could not be resolved)

    <!-- -->

    - #### getChildrenByTagName

          public NodeList getChildrenByTagName(java.lang.String name)

      Returns a `NodeList` of all immediate children with a given tag name,
      Parameters:
      `name` - The name of the tag to match on.

      Returns:
      A list of matching children

    <!-- -->

    - #### getChildrenByTagName

          public NodeList getChildrenByTagName(java.lang.String name,
                                               java.lang.String ns)

      Returns a `NodeList` of all immediate children with a given tag name and namespace
      Parameters:
      `name` - The name of the tag to match on. (should be local name)

      `ns` - The name space

      Returns:
      A list of matching children

    <!-- -->

    - #### reportSAXEvents

          public void reportSAXEvents(ContentHandler cntHandler)
                               throws SAXException

      Report SAX Events from a DOM Tree
      Overrides:
      [`reportSAXEvents`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Parameters:
      `cntHandler` - ContentHandler

      Throws:
      [`SAXException`](../../../../org/xml/sax/SAXException.md) - thrown by SAX Callback functions

    <!-- -->

    - #### validateContent

          public boolean validateContent(DTD dtd)

      Validates the content of a element node.
      Returns:
      True if valid, else false

    <!-- -->

    - #### validateContent

          public boolean validateContent(XMLSchema schema)
                                  throws XMLParseException

      Validates the content of the element against given XML Schema
      Parameters:
      `schema` - schema used to validate

      Returns:
      True if valid, else false

      Throws:
      [`XMLParseException`](XMLParseException.md)

    <!-- -->

    - #### validateContent

          public XMLNode validateContent(XSDValidator validator,
                                         boolean flag)
                                  throws XMLParseException

      Validates the content of the element using given validator
      Parameters:
      `validator` - - schema validator used to validate

      `flag` - - indicate if copy result or not

      Returns:
      this/a copy of this node with annotated psvi.

      Throws:
      [`XMLParseException`](XMLParseException.md)

    <!-- -->

    - #### validateContent

          public boolean validateContent(XMLSchema schema,
                                         java.lang.String mode)
                                  throws XMLParseException

      Validates the content of the element against given XML Schema in the given mode.
      Parameters:
      `schema` - - schema used to validate the content

      `mode` - - the validation mode

      Returns:
      True if valid, else false

      Throws:
      [`XMLParseException`](XMLParseException.md)

    <!-- -->

    - #### getAttributeNode

          public Attr getAttributeNode(java.lang.String name,
                                       java.lang.String namespace)

      Deprecated. As of DOM 2
      See Also:
      `getAttributeNodeNS(String ,String)`

    <!-- -->

    - #### getQualifiedName

          public java.lang.String getQualifiedName()

      Deprecated. - Use getNodeName
      Get the qualified name for this element.
      Specified by:
      [`getQualifiedName`](../../util/NSName.md) in interface [`NSName`](../../util/NSName.md)

      Returns:
      the qualified name

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

- **[Prev Class](XMLDOMImplementation.md)**
- **[Next Class](XMLEntity.md)**

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
