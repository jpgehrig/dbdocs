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

- **Prev Class**
- **[Next Class](XDBBinaryDocument.md)**

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

## **Class XDBAttribute**

- **java.lang.Object**

- - **[oracle.xdb.dom.XDBNode](XDBNode.md)**

  - - **oracle.xdb.dom.XDBAttribute**

<!-- -->

- **All Implemented Interfaces:**
  **[Attr](../../../org/w3c/dom/Attr.md), [Node](../../../org/w3c/dom/Node.md)**

  ------------------------------------------------------------------------

  **Deprecated. **
  **as of Oracle Database 11g release 1, use oracle.xml.parser.v2.XMLAttr**
  **
  **

      public class XDBAttribute
      extends XDBNode
      implements Attr

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

    | Modifier and Type                              | Method and Description                                                                                                                       |
    |------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`                             | `getName``()`<br>Deprecated. <br>Returns the name of the attribute.                                                                          |
    | [`Element`](../../../org/w3c/dom/Element.md)   | `getOwnerElement``()`<br>Deprecated. <br>gets the owner element of the attribute; null if the attribute has not been attached to any element |
    | [`TypeInfo`](../../../org/w3c/dom/TypeInfo.md) | `getSchemaTypeInfo``()`<br>Deprecated. <br>                                                                                                  |
    | `boolean`                                      | `getSpecified``()`<br>Deprecated. <br>specifies whether the attribute has been assigned a value                                              |
    | `java.lang.String`                             | `getValue``()`<br>Deprecated. <br>get the value the attribute                                                                                |
    | `boolean`                                      | `isId``()`<br>Deprecated. <br>                                                                                                               |
    | `void`                                         | `setValue``(java.lang.String value)`<br>Deprecated. <br>set the value of the node                                                            |

    - ### Methods inherited from class oracle.xdb.dom.[XDBNode](XDBNode.md)

      [`appendChild`](XDBNode.md)`, `[`cloneNode`](XDBNode.md)`, `[`close`](XDBNode.md)`, `[`compareDocumentPosition`](XDBNode.md)`, `[`equals`](XDBNode.md)`, `[`finalize`](XDBNode.md)`, `[`getAttributes`](XDBNode.md)`, `[`getBaseURI`](XDBNode.md)`, `[`getChildNodes`](XDBNode.md)`, `[`getExpandedName`](XDBNode.md)`, `[`getFeature`](XDBNode.md)`, `[`getFirstChild`](XDBNode.md)`, `[`getInputStream`](XDBNode.md)`, `[`getLastChild`](XDBNode.md)`, `[`getLocalName`](XDBNode.md)`, `[`getNamespaceURI`](XDBNode.md)`, `[`getNextSibling`](XDBNode.md)`, `[`getNodeName`](XDBNode.md)`, `[`getNodeType`](XDBNode.md)`, `[`getNodeValue`](XDBNode.md)`, `[`getOwnerDocument`](XDBNode.md)`, `[`getParentNode`](XDBNode.md)`, `[`getPrefix`](XDBNode.md)`, `[`getPreviousSibling`](XDBNode.md)`, `[`getPrimitiveType`](XDBNode.md)`, `[`getQualifiedName`](XDBNode.md)`, `[`getSchemaNode`](XDBNode.md)`, `[`getTextContent`](XDBNode.md)`, `[`getUserData`](XDBNode.md)`, `[`hasAttributes`](XDBNode.md)`, `[`hasChildNodes`](XDBNode.md)`, `[`hashCode`](XDBNode.md)`, `[`insertBefore`](XDBNode.md)`, `[`isDefaultNamespace`](XDBNode.md)`, `[`isEqualNode`](XDBNode.md)`, `[`isNilled`](XDBNode.md)`, `[`isSameNode`](XDBNode.md)`, `[`isSchemaBased`](XDBNode.md)`, `[`isSupported`](XDBNode.md)`, `[`lookupNamespaceURI`](XDBNode.md)`, `[`lookupPrefix`](XDBNode.md)`, `[`normalize`](XDBNode.md)`, `[`removeChild`](XDBNode.md)`, `[`replaceChild`](XDBNode.md)`, `[`setNodeValue`](XDBNode.md)`, `[`setNodeXob`](XDBNode.md)`, `[`setOwner`](XDBNode.md)`, `[`setPrefix`](XDBNode.md)`, `[`setTextContent`](XDBNode.md)`, `[`setUserData`](XDBNode.md)`, `[`setXobCstate`](XDBNode.md)`, `[`toCState`](XDBNode.md)`, `[`toString`](XDBNode.md)`, `[`write`](XDBNode.md)`, `[`writeToOutputStream`](XDBNode.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface org.w3c.dom.[Node](../../../org/w3c/dom/Node.md)

      [`appendChild`](../../../org/w3c/dom/Node.md)`, `[`cloneNode`](../../../org/w3c/dom/Node.md)`, `[`getAttributes`](../../../org/w3c/dom/Node.md)`, `[`getChildNodes`](../../../org/w3c/dom/Node.md)`, `[`getFirstChild`](../../../org/w3c/dom/Node.md)`, `[`getLastChild`](../../../org/w3c/dom/Node.md)`, `[`getLocalName`](../../../org/w3c/dom/Node.md)`, `[`getNamespaceURI`](../../../org/w3c/dom/Node.md)`, `[`getNextSibling`](../../../org/w3c/dom/Node.md)`, `[`getNodeName`](../../../org/w3c/dom/Node.md)`, `[`getNodeType`](../../../org/w3c/dom/Node.md)`, `[`getNodeValue`](../../../org/w3c/dom/Node.md)`, `[`getOwnerDocument`](../../../org/w3c/dom/Node.md)`, `[`getParentNode`](../../../org/w3c/dom/Node.md)`, `[`getPrefix`](../../../org/w3c/dom/Node.md)`, `[`getPreviousSibling`](../../../org/w3c/dom/Node.md)`, `[`hasAttributes`](../../../org/w3c/dom/Node.md)`, `[`hasChildNodes`](../../../org/w3c/dom/Node.md)`, `[`insertBefore`](../../../org/w3c/dom/Node.md)`, `[`isSupported`](../../../org/w3c/dom/Node.md)`, `[`normalize`](../../../org/w3c/dom/Node.md)`, `[`removeChild`](../../../org/w3c/dom/Node.md)`, `[`replaceChild`](../../../org/w3c/dom/Node.md)`, `[`setNodeValue`](../../../org/w3c/dom/Node.md)`, `[`setPrefix`](../../../org/w3c/dom/Node.md)

<!-- -->

- - ### Method Detail

    - #### getName

          public java.lang.String getName()

      Deprecated. 
      Returns the name of the attribute.
      Specified by:
      [`getName`](../../../org/w3c/dom/Attr.md) in interface [`Attr`](../../../org/w3c/dom/Attr.md)

      Returns:
      the name of the attribute

    <!-- -->

    - #### getSpecified

          public boolean getSpecified()

      Deprecated. 
      specifies whether the attribute has been assigned a value
      Specified by:
      [`getSpecified`](../../../org/w3c/dom/Attr.md) in interface [`Attr`](../../../org/w3c/dom/Attr.md)

      Returns:
      true if attribute has value false otherwise

    <!-- -->

    - #### getValue

          public java.lang.String getValue()

      Deprecated. 
      get the value the attribute
      Specified by:
      [`getValue`](../../../org/w3c/dom/Attr.md) in interface [`Attr`](../../../org/w3c/dom/Attr.md)

      Returns:
      the node name string, always null for this node.

    <!-- -->

    - #### setValue

          public void setValue(java.lang.String value)
                        throws DOMException

      Deprecated. 
      set the value of the node
      Specified by:
      [`setValue`](../../../org/w3c/dom/Attr.md) in interface [`Attr`](../../../org/w3c/dom/Attr.md)

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md)

    <!-- -->

    - #### getOwnerElement

          public Element getOwnerElement()

      Deprecated. 
      gets the owner element of the attribute; null if the attribute has not been attached to any element
      Specified by:
      [`getOwnerElement`](../../../org/w3c/dom/Attr.md) in interface [`Attr`](../../../org/w3c/dom/Attr.md)

      Returns:
      the owner element

    <!-- -->

    - #### getSchemaTypeInfo

          public TypeInfo getSchemaTypeInfo()

      Deprecated. 

    <!-- -->

    - #### isId

          public boolean isId()

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

- **Prev Class**
- **[Next Class](XDBBinaryDocument.md)**

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
