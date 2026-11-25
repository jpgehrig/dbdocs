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

- **[Prev Class](XMLDocument.md)**
- **[Next Class](XMLDocumentHandler.md)**

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

## **Class XMLDocumentFragment**

- **java.lang.Object**

- - **[oracle.xml.parser.v2.XMLNode](XMLNode.md)**

  - - **[oracle.xml.parser.v2.XMLNSNode](XMLNSNode.md)**

    - - **[oracle.xml.parser.v2.XMLElement](XMLElement.md)**

      - - **oracle.xml.parser.v2.XMLDocumentFragment**

<!-- -->

- **All Implemented Interfaces:**
  **java.io.Externalizable, java.io.Serializable, java.lang.Cloneable, [NSResolver](NSResolver.md), [NSName](../../util/NSName.md), [DocumentFragment](../../../../org/w3c/dom/DocumentFragment.md), [Element](../../../../org/w3c/dom/Element.md), [EventTarget](../../../../org/w3c/dom/events/EventTarget.md), [Node](../../../../org/w3c/dom/Node.md), [ElementEditVAL](../../../../org/w3c/dom/validation/ElementEditVAL.md), [NodeEditVAL](../../../../org/w3c/dom/validation/NodeEditVAL.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XMLDocumentFragment
      extends XMLElement
      implements DocumentFragment, java.io.Externalizable

  **This class implements the DOM interface for DocumentFragment. It extends XMLElement rather than XMLNode so it can be handled as an element. This is convenient in processing.**
  **See Also:**
  **[`DocumentFragment`](../../../../org/w3c/dom/DocumentFragment.md), [`NodeFactory`](NodeFactory.md), [`DOMParser.setNodeFactory(oracle.xml.parser.v2.NodeFactory)`](DOMParser.md), [Serialized Form](../../../../serialized-form.md)**

<!-- -->

-
  -

    ### **Field Summary**

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

      ### **Fields inherited from interface org.w3c.dom.validation.[ElementEditVAL](../../../../org/w3c/dom/validation/ElementEditVAL.md)**

      **[`VAL_ANY_CONTENTTYPE`](../../../../org/w3c/dom/validation/ElementEditVAL.md)`, `[`VAL_ELEMENTS_CONTENTTYPE`](../../../../org/w3c/dom/validation/ElementEditVAL.md)`, `[`VAL_EMPTY_CONTENTTYPE`](../../../../org/w3c/dom/validation/ElementEditVAL.md)`, `[`VAL_MIXED_CONTENTTYPE`](../../../../org/w3c/dom/validation/ElementEditVAL.md)`, `[`VAL_SIMPLE_CONTENTTYPE`](../../../../org/w3c/dom/validation/ElementEditVAL.md)**

    <!-- -->

    -

      ### **Fields inherited from interface org.w3c.dom.validation.[NodeEditVAL](../../../../org/w3c/dom/validation/NodeEditVAL.md)**

      **[`VAL_FALSE`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`VAL_INCOMPLETE`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`VAL_NS_WF`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`VAL_SCHEMA`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`VAL_TRUE`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`VAL_UNKNOWN`](../../../../org/w3c/dom/validation/NodeEditVAL.md)`, `[`VAL_WF`](../../../../org/w3c/dom/validation/NodeEditVAL.md)**

  <!-- -->

  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description                                                                     |
    |-------------------------------------------------------------------------------------------------|
    | `XMLDocumentFragment``()`<br>Deprecated. <br>use createDocumentFragment() method in XMLDocuemnt |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                         | Method and Description                                                                                                               |
    |-----------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------|
    | [`NamedNodeMap`](../../../../org/w3c/dom/NamedNodeMap.md) | `getAttributes``()`<br>A `NamedNodeMap` containing the attributes of this node (if it is an `Element`) or `null` otherwise.          |
    | `java.lang.String`                                        | `getBaseURI``()`<br>Gets the baseURI of this fragment                                                                                |
    | `java.lang.String`                                        | `getLocalName``()`<br>Gets the local Name for this element.                                                                          |
    | `java.lang.String`                                        | `getNamespaceURI``()`<br>Gets the name space URI of this element                                                                     |
    | [`Node`](../../../../org/w3c/dom/Node.md)                 | `getNextSibling``()`<br>Gets The node immediately following this node.                                                               |
    | `java.lang.String`                                        | `getNodeName``()`<br>Gets a name of the node                                                                                         |
    | `short`                                                   | `getNodeType``()`<br>Gets a code representing the type of the underlying object                                                      |
    | [`Node`](../../../../org/w3c/dom/Node.md)                 | `getParentNode``()`<br>Gets the parent of this node                                                                                  |
    | [`Node`](../../../../org/w3c/dom/Node.md)                 | `getPreviousSibling``()`<br>Gets the node immediately preceding this node.                                                           |
    | `void`                                                    | `reportSAXEvents``(`[`ContentHandler`](../../../../org/xml/sax/ContentHandler.md)` cntHandler)`<br>Report SAX Events from a DOM Tree |
    | `void`                                                    | `setBaseURI``(java.lang.String baseuri)`<br>Sets the baseURI of this fragment                                                        |

    - ### Methods inherited from class oracle.xml.parser.v2.[XMLElement](XMLElement.md)

      [`canAppendChild`](XMLElement.md)`, `[`canInsertBefore`](XMLElement.md)`, `[`canRemoveAttribute`](XMLElement.md)`, `[`canRemoveAttributeNode`](XMLElement.md)`, `[`canRemoveAttributeNS`](XMLElement.md)`, `[`canRemoveChild`](XMLElement.md)`, `[`canReplaceChild`](XMLElement.md)`, `[`canSetAttribute`](XMLElement.md)`, `[`canSetAttributeNode`](XMLElement.md)`, `[`canSetAttributeNS`](XMLElement.md)`, `[`canSetTextContent`](XMLElement.md)`, `[`getAllowedAttributes`](XMLElement.md)`, `[`getAllowedChildren`](XMLElement.md)`, `[`getAllowedFirstChildren`](XMLElement.md)`, `[`getAllowedNextSiblings`](XMLElement.md)`, `[`getAllowedParents`](XMLElement.md)`, `[`getAllowedPreviousSiblings`](XMLElement.md)`, `[`getAttribute`](XMLElement.md)`, `[`getAttributeNode`](XMLElement.md)`, `[`getAttributeNode`](XMLElement.md)`, `[`getAttributeNodeNS`](XMLElement.md)`, `[`getAttributeNS`](XMLElement.md)`, `[`getChildrenByTagName`](XMLElement.md)`, `[`getChildrenByTagName`](XMLElement.md)`, `[`getContentType`](XMLElement.md)`, `[`getDefaultValue`](XMLElement.md)`, `[`getElementsByTagName`](XMLElement.md)`, `[`getElementsByTagNameNS`](XMLElement.md)`, `[`getEnumeratedValues`](XMLElement.md)`, `[`getExpandedName`](XMLElement.md)`, `[`getFirstAttribute`](XMLElement.md)`, `[`getNextSiblingByName`](XMLElement.md)`, `[`getPrefix`](XMLElement.md)`, `[`getQualifiedName`](XMLElement.md)`, `[`getRequiredAttributes`](XMLElement.md)`, `[`getTagName`](XMLElement.md)`, `[`hasAttribute`](XMLElement.md)`, `[`hasAttributeNS`](XMLElement.md)`, `[`hasAttributes`](XMLElement.md)`, `[`isElementDefined`](XMLElement.md)`, `[`isElementDefinedNS`](XMLElement.md)`, `[`nodeValidity`](XMLElement.md)`, `[`normalize`](XMLElement.md)`, `[`removeAttribute`](XMLElement.md)`, `[`removeAttributeNode`](XMLElement.md)`, `[`removeAttributeNS`](XMLElement.md)`, `[`resolveNamespacePrefix`](XMLElement.md)`, `[`setAttribute`](XMLElement.md)`, `[`setAttributeNode`](XMLElement.md)`, `[`setAttributeNodeNS`](XMLElement.md)`, `[`setAttributeNS`](XMLElement.md)`, `[`setPrefix`](XMLElement.md)`, `[`validateContent`](XMLElement.md)`, `[`validateContent`](XMLElement.md)`, `[`validateContent`](XMLElement.md)`, `[`validateContent`](XMLElement.md)

    <!-- -->

    - ### Methods inherited from class oracle.xml.parser.v2.[XMLNSNode](XMLNSNode.md)

      [`addText`](XMLNSNode.md)`, `[`addText`](XMLNSNode.md)`, `[`appendChild`](XMLNSNode.md)`, `[`getChildNodes`](XMLNSNode.md)`, `[`getFirstChild`](XMLNSNode.md)`, `[`getLastChild`](XMLNSNode.md)`, `[`getText`](XMLNSNode.md)`, `[`insertBefore`](XMLNSNode.md)`, `[`removeChild`](XMLNSNode.md)`, `[`replaceChild`](XMLNSNode.md)

    <!-- -->

    - ### Methods inherited from class oracle.xml.parser.v2.[XMLNode](XMLNode.md)

      [`addEventListener`](XMLNode.md)`, `[`cloneNode`](XMLNode.md)`, `[`dispatchEvent`](XMLNode.md)`, `[`equals`](XMLNode.md)`, `[`getColumnNumber`](XMLNode.md)`, `[`getDebugMode`](XMLNode.md)`, `[`getFirstChildAsOffset`](XMLNode.md)`, `[`getLineNumber`](XMLNode.md)`, `[`getNextSiblingAsOffset`](XMLNode.md)`, `[`getNodeValue`](XMLNode.md)`, `[`getNodeValueAsBinaryStream`](XMLNode.md)`, `[`getNodeValueAsBinaryStream`](XMLNode.md)`, `[`getNodeValueAsCharacterStream`](XMLNode.md)`, `[`getNodeValueAsCharacterStream`](XMLNode.md)`, `[`getOwnerDocument`](XMLNode.md)`, `[`getPrimitiveTypeId`](XMLNode.md)`, `[`getProperty`](XMLNode.md)`, `[`getSystemId`](XMLNode.md)`, `[`getXMLError`](XMLNode.md)`, `[`hasChildNodes`](XMLNode.md)`, `[`hashCode`](XMLNode.md)`, `[`isDocumentFlag`](XMLNode.md)`, `[`isNodeFlag`](XMLNode.md)`, `[`isSupported`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`print`](XMLNode.md)`, `[`readExternal`](XMLNode.md)`, `[`removeEventListener`](XMLNode.md)`, `[`resetNodeFlag`](XMLNode.md)`, `[`selectNodes`](XMLNode.md)`, `[`selectNodes`](XMLNode.md)`, `[`selectSingleNode`](XMLNode.md)`, `[`selectSingleNode`](XMLNode.md)`, `[`setDebugInfo`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeFlag`](XMLNode.md)`, `[`setNodeValue`](XMLNode.md)`, `[`setNodeValueAsBinaryStream`](XMLNode.md)`, `[`setNodeValueAsBinaryStream`](XMLNode.md)`, `[`setNodeValueAsCharacterStream`](XMLNode.md)`, `[`setNodeValueAsCharacterStream`](XMLNode.md)`, `[`setProperty`](XMLNode.md)`, `[`transformNode`](XMLNode.md)`, `[`valueOf`](XMLNode.md)`, `[`valueOf`](XMLNode.md)`, `[`writeExternal`](XMLNode.md)`, `[`xdbGetNodeId`](XMLNode.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface org.w3c.dom.[Node](../../../../org/w3c/dom/Node.md)

      [`appendChild`](../../../../org/w3c/dom/Node.md)`, `[`cloneNode`](../../../../org/w3c/dom/Node.md)`, `[`getChildNodes`](../../../../org/w3c/dom/Node.md)`, `[`getFirstChild`](../../../../org/w3c/dom/Node.md)`, `[`getLastChild`](../../../../org/w3c/dom/Node.md)`, `[`getNodeValue`](../../../../org/w3c/dom/Node.md)`, `[`getOwnerDocument`](../../../../org/w3c/dom/Node.md)`, `[`getPrefix`](../../../../org/w3c/dom/Node.md)`, `[`hasAttributes`](../../../../org/w3c/dom/Node.md)`, `[`hasChildNodes`](../../../../org/w3c/dom/Node.md)`, `[`insertBefore`](../../../../org/w3c/dom/Node.md)`, `[`isSupported`](../../../../org/w3c/dom/Node.md)`, `[`normalize`](../../../../org/w3c/dom/Node.md)`, `[`removeChild`](../../../../org/w3c/dom/Node.md)`, `[`replaceChild`](../../../../org/w3c/dom/Node.md)`, `[`setNodeValue`](../../../../org/w3c/dom/Node.md)`, `[`setPrefix`](../../../../org/w3c/dom/Node.md)

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

- - ### Constructor Detail

    - #### XMLDocumentFragment

          public XMLDocumentFragment()

      Deprecated. use createDocumentFragment() method in XMLDocuemnt
      Creates an empty document fragment

  <!-- -->

  - ### Method Detail

    - #### getBaseURI

          public java.lang.String getBaseURI()

      Gets the baseURI of this fragment
      Overrides:
      [`getBaseURI`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Returns:
      baseURI

    <!-- -->

    - #### setBaseURI

          public void setBaseURI(java.lang.String baseuri)

      Sets the baseURI of this fragment
      Parameters:
      `baseuri` - string

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

    - #### getNamespaceURI

          public java.lang.String getNamespaceURI()

      Gets the name space URI of this element
      Specified by:
      [`getNamespaceURI`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`getNamespaceURI`](XMLElement.md) in class [`XMLElement`](XMLElement.md)

      Returns:
      the namespace URI of this element

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

    - #### getParentNode

          public Node getParentNode()

      Gets the parent of this node
      Specified by:
      [`getParentNode`](../../../../org/w3c/dom/Node.md) in interface [`Node`](../../../../org/w3c/dom/Node.md)

      Overrides:
      [`getParentNode`](XMLNode.md) in class [`XMLNode`](XMLNode.md)

      Returns:
      The parent of this node (always null)

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
      The list of attributes of this element

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

- **[Prev Class](XMLDocument.md)**
- **[Next Class](XMLDocumentHandler.md)**

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
