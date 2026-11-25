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

- **[Prev Class](XDBDOMNotFoundErrException.md)**
- **[Next Class](XDBEntity.md)**

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

## **Class XDBElement**

- **java.lang.Object**

- - **[oracle.xdb.dom.XDBNode](XDBNode.md)**

  - - **oracle.xdb.dom.XDBElement**

<!-- -->

- **All Implemented Interfaces:**
  **[Element](../../../org/w3c/dom/Element.md), [Node](../../../org/w3c/dom/Node.md)**

  ------------------------------------------------------------------------

  **Deprecated. **
  **as of Oracle Database 11g release 1, use oracle.xml.parser.v2.XMLElement**
  **
  **

      public class XDBElement
      extends XDBNode
      implements Element

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

    | Modifier and Type                              | Method and Description                                                                                                                                                                                                                                                                 |
    |------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`                             | `getAttribute``(java.lang.String attr)`<br>Deprecated. <br>Retrieves an attribute value by name.                                                                                                                                                                                       |
    | [`Attr`](../../../org/w3c/dom/Attr.md)         | `getAttributeNode``(java.lang.String attr)`<br>Deprecated. <br>Retrieves an attribute node by name.                                                                                                                                                                                    |
    | [`Attr`](../../../org/w3c/dom/Attr.md)         | `getAttributeNodeNS``(java.lang.String namespaceURI, java.lang.String localName)`<br>Deprecated. <br>Retrieves an `Attr` node by local name and namespace URI.                                                                                                                         |
    | `java.lang.String`                             | `getAttributeNS``(java.lang.String namespaceURI, java.lang.String localName)`<br>Deprecated. <br>Retrieves an attribute value by local name and namespace URI.                                                                                                                         |
    | [`XDBNodeList`](XDBNodeList.md)                | `getChildrenByTagName``(java.lang.String tagName)`<br>Deprecated. <br>get the children node list based on the tag name                                                                                                                                                                 |
    | [`XDBNodeList`](XDBNodeList.md)                | `getChildrenByTagNameNS``(java.lang.String tagName, java.lang.String ns)`<br>Deprecated. <br>get the children node list based on the tag name                                                                                                                                          |
    | [`NodeList`](../../../org/w3c/dom/NodeList.md) | `getElementsByTagName``(java.lang.String tag)`<br>Deprecated. <br>Returns a `NodeList` of all descendant `Elements` with a given tag name, in the order in which they are encountered in a preorder traversal of this `Element` tree.                                                  |
    | [`NodeList`](../../../org/w3c/dom/NodeList.md) | `getElementsByTagNameNS``(java.lang.String nsURI, java.lang.String tag)`<br>Deprecated. <br>Returns a `NodeList` of all the descendant `Elements` with a given local name and namespace URI in the order in which they are encountered in a preorder traversal of this `Element` tree. |
    | [`TypeInfo`](../../../org/w3c/dom/TypeInfo.md) | `getSchemaTypeInfo``()`<br>Deprecated. <br>                                                                                                                                                                                                                                            |
    | `java.lang.String`                             | `getTagName``()`<br>Deprecated. <br>The name of the element.                                                                                                                                                                                                                           |
    | `boolean`                                      | `hasAttribute``(java.lang.String name)`<br>Deprecated. <br>Returns `true` when an attribute with a given name is specified on this element or has a default value, `false` otherwise.                                                                                                  |
    | `boolean`                                      | `hasAttributeNS``(java.lang.String nsURI, java.lang.String name)`<br>Deprecated. <br>Returns `true` when an attribute with a given local name and namespace URI is specified on this element or has a default value, `false` otherwise.                                                |
    | `void`                                         | `removeAttribute``(java.lang.String attr)`<br>Deprecated. <br>Removes an attribute by name.                                                                                                                                                                                            |
    | [`Attr`](../../../org/w3c/dom/Attr.md)         | `removeAttributeNode``(`[`Attr`](../../../org/w3c/dom/Attr.md)` oldattr)`<br>Deprecated. <br>Removes the specified attribute node.                                                                                                                                                     |
    | `void`                                         | `removeAttributeNS``(java.lang.String namespaceURI, java.lang.String localName)`<br>Deprecated. <br>Removes an attribute by local name and namespace URI.                                                                                                                              |
    | `java.lang.String`                             | `resolveNSPrefix``(java.lang.String prefix)`<br>Deprecated. <br>                                                                                                                                                                                                                       |
    | `void`                                         | `setAttribute``(java.lang.String name, java.lang.String attr)`<br>Deprecated. <br>Adds a new attribute.                                                                                                                                                                                |
    | [`Attr`](../../../org/w3c/dom/Attr.md)         | `setAttributeNode``(`[`Attr`](../../../org/w3c/dom/Attr.md)` newattr)`<br>Deprecated. <br>Adds a new attribute node.                                                                                                                                                                   |
    | [`Attr`](../../../org/w3c/dom/Attr.md)         | `setAttributeNodeNS``(`[`Attr`](../../../org/w3c/dom/Attr.md)` newAttr)`<br>Deprecated. <br>Adds a new attribute.                                                                                                                                                                      |
    | `void`                                         | `setAttributeNS``(java.lang.String namespaceURI, java.lang.String qualifiedName, java.lang.String value)`<br>Deprecated. <br>Adds a new attribute.                                                                                                                                     |
    | `void`                                         | `setIdAttribute``(java.lang.String name, boolean isId)`<br>Deprecated. <br>                                                                                                                                                                                                            |
    | `void`                                         | `setIdAttributeNode``(`[`Attr`](../../../org/w3c/dom/Attr.md)` idAttr, boolean isId)`<br>Deprecated. <br>                                                                                                                                                                              |
    | `void`                                         | `setIdAttributeNS``(java.lang.String namespaceURI, java.lang.String localName, boolean isId)`<br>Deprecated. <br>                                                                                                                                                                      |

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

    - #### getTagName

          public java.lang.String getTagName()

      Deprecated. 
      Description copied from interface: [`Element`](../../../org/w3c/dom/Element.md)
      The name of the element. For example, in:
           <elementExample
           id="demo"> ... </elementExample> ,

      `tagName` has the value `"elementExample"`. Note that this is case-preserving in XML, as are all of the operations of the DOM. The HTML DOM returns the `tagName` of an HTML element in the canonical uppercase form, regardless of the case in the source HTML document.
      Specified by:
      [`getTagName`](../../../org/w3c/dom/Element.md) in interface [`Element`](../../../org/w3c/dom/Element.md)

    <!-- -->

    - #### getAttribute

          public java.lang.String getAttribute(java.lang.String attr)

      Deprecated. 
      Description copied from interface: [`Element`](../../../org/w3c/dom/Element.md)
      Retrieves an attribute value by name.
      Specified by:
      [`getAttribute`](../../../org/w3c/dom/Element.md) in interface [`Element`](../../../org/w3c/dom/Element.md)

      Parameters:
      `attr` - The name of the attribute to retrieve.

      Returns:
      The `Attr` value as a string, or the empty string if that attribute does not have a specified or default value.

    <!-- -->

    - #### setAttribute

          public void setAttribute(java.lang.String name,
                                   java.lang.String attr)

      Deprecated. 
      Description copied from interface: [`Element`](../../../org/w3c/dom/Element.md)
      Adds a new attribute. If an attribute with that name is already present in the element, its value is changed to be that of the value parameter. This value is a simple string; it is not parsed as it is being set. So any markup (such as syntax to be recognized as an entity reference) is treated as literal text, and needs to be appropriately escaped by the implementation when it is written out. In order to assign an attribute value that contains entity references, the user must create an `Attr` node plus any `Text` and `EntityReference` nodes, build the appropriate subtree, and use `setAttributeNode` to assign it as the value of an attribute.
      To set an attribute with a qualified name and namespace URI, use the `setAttributeNS` method.
      Specified by:
      [`setAttribute`](../../../org/w3c/dom/Element.md) in interface [`Element`](../../../org/w3c/dom/Element.md)

      Parameters:
      `name` - The name of the attribute to create or alter.

      `attr` - Value to set in string form.

    <!-- -->

    - #### removeAttribute

          public void removeAttribute(java.lang.String attr)

      Deprecated. 
      Description copied from interface: [`Element`](../../../org/w3c/dom/Element.md)
      Removes an attribute by name. If the removed attribute is known to have a default value, an attribute immediately appears containing the default value as well as the corresponding namespace URI, local name, and prefix when applicable.
      To remove an attribute by local name and namespace URI, use the `removeAttributeNS` method.
      Specified by:
      [`removeAttribute`](../../../org/w3c/dom/Element.md) in interface [`Element`](../../../org/w3c/dom/Element.md)

      Parameters:
      `attr` - The name of the attribute to remove.

    <!-- -->

    - #### getAttributeNode

          public Attr getAttributeNode(java.lang.String attr)

      Deprecated. 
      Description copied from interface: [`Element`](../../../org/w3c/dom/Element.md)
      Retrieves an attribute node by name.
      To retrieve an attribute node by qualified name and namespace URI, use the `getAttributeNodeNS` method.
      Specified by:
      [`getAttributeNode`](../../../org/w3c/dom/Element.md) in interface [`Element`](../../../org/w3c/dom/Element.md)

      Parameters:
      `attr` - The name (`nodeName`) of the attribute to retrieve.

      Returns:
      The `Attr` node with the specified name ( `nodeName`) or `null` if there is no such attribute.

    <!-- -->

    - #### setAttributeNode

          public Attr setAttributeNode(Attr newattr)
                                throws DOMException

      Deprecated. 
      Description copied from interface: [`Element`](../../../org/w3c/dom/Element.md)
      Adds a new attribute node. If an attribute with that name ( `nodeName`) is already present in the element, it is replaced by the new one.
      To add a new attribute node with a qualified name and namespace URI, use the `setAttributeNodeNS` method.
      Specified by:
      [`setAttributeNode`](../../../org/w3c/dom/Element.md) in interface [`Element`](../../../org/w3c/dom/Element.md)

      Parameters:
      `newattr` - The `Attr` node to add to the attribute list.

      Returns:
      If the `newAttr` attribute replaces an existing attribute, the replaced `Attr` node is returned, otherwise `null` is returned.

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md) - WRONG_DOCUMENT_ERR: Raised if `newAttr` was created from a different document than the one that created the element.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.
      INUSE_ATTRIBUTE_ERR: Raised if `newAttr` is already an attribute of another `Element` object. The DOM user must explicitly clone `Attr` nodes to re-use them in other elements.

    <!-- -->

    - #### removeAttributeNode

          public Attr removeAttributeNode(Attr oldattr)

      Deprecated. 
      Description copied from interface: [`Element`](../../../org/w3c/dom/Element.md)
      Removes the specified attribute node. If the removed `Attr` has a default value it is immediately replaced. The replacing attribute has the same namespace URI and local name, as well as the original prefix, when applicable.
      Specified by:
      [`removeAttributeNode`](../../../org/w3c/dom/Element.md) in interface [`Element`](../../../org/w3c/dom/Element.md)

      Parameters:
      `oldattr` - The `Attr` node to remove from the attribute list.

      Returns:
      The `Attr` node that was removed.

    <!-- -->

    - #### getElementsByTagName

          public NodeList getElementsByTagName(java.lang.String tag)

      Deprecated. 
      Description copied from interface: [`Element`](../../../org/w3c/dom/Element.md)
      Returns a `NodeList` of all descendant `Elements` with a given tag name, in the order in which they are encountered in a preorder traversal of this `Element` tree.
      Specified by:
      [`getElementsByTagName`](../../../org/w3c/dom/Element.md) in interface [`Element`](../../../org/w3c/dom/Element.md)

      Parameters:
      `tag` - The name of the tag to match on. The special value "\*" matches all tags.

      Returns:
      A list of matching `Element` nodes.

    <!-- -->

    - #### getAttributeNS

          public java.lang.String getAttributeNS(java.lang.String namespaceURI,
                                                 java.lang.String localName)

      Deprecated. 
      Description copied from interface: [`Element`](../../../org/w3c/dom/Element.md)
      Retrieves an attribute value by local name and namespace URI. HTML-only DOM implementations do not need to implement this method.
      Specified by:
      [`getAttributeNS`](../../../org/w3c/dom/Element.md) in interface [`Element`](../../../org/w3c/dom/Element.md)

      Parameters:
      `namespaceURI` - The namespace URI of the attribute to retrieve.

      `localName` - The local name of the attribute to retrieve.

      Returns:
      The `Attr` value as a string, or the empty string if that attribute does not have a specified or default value.

    <!-- -->

    - #### setAttributeNS

          public void setAttributeNS(java.lang.String namespaceURI,
                                     java.lang.String qualifiedName,
                                     java.lang.String value)
                              throws DOMException

      Deprecated. 
      Description copied from interface: [`Element`](../../../org/w3c/dom/Element.md)
      Adds a new attribute. If an attribute with the same local name and namespace URI is already present on the element, its prefix is changed to be the prefix part of the `qualifiedName`, and its value is changed to be the `value` parameter. This value is a simple string; it is not parsed as it is being set. So any markup (such as syntax to be recognized as an entity reference) is treated as literal text, and needs to be appropriately escaped by the implementation when it is written out. In order to assign an attribute value that contains entity references, the user must create an `Attr` node plus any `Text` and `EntityReference` nodes, build the appropriate subtree, and use `setAttributeNodeNS` or `setAttributeNode` to assign it as the value of an attribute.
      HTML-only DOM implementations do not need to implement this method.
      Specified by:
      [`setAttributeNS`](../../../org/w3c/dom/Element.md) in interface [`Element`](../../../org/w3c/dom/Element.md)

      Parameters:
      `namespaceURI` - The namespace URI of the attribute to create or alter.

      `qualifiedName` - The qualified name of the attribute to create or alter.

      `value` - The value to set in string form.

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md) - INVALID_CHARACTER_ERR: Raised if the specified qualified name contains an illegal character.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.
      NAMESPACE_ERR: Raised if the `qualifiedName` is malformed, if the `qualifiedName` has a prefix and the `namespaceURI` is `null`, if the `qualifiedName` has a prefix that is "xml" and the `namespaceURI` is different from " http://www.w3.org/XML/1998/namespace", or if the `qualifiedName` is "xmlns" and the `namespaceURI` is different from " http://www.w3.org/2000/xmlns/".

    <!-- -->

    - #### removeAttributeNS

          public void removeAttributeNS(java.lang.String namespaceURI,
                                        java.lang.String localName)
                                 throws DOMException

      Deprecated. 
      Description copied from interface: [`Element`](../../../org/w3c/dom/Element.md)
      Removes an attribute by local name and namespace URI. If the removed attribute has a default value it is immediately replaced. The replacing attribute has the same namespace URI and local name, as well as the original prefix.
      HTML-only DOM implementations do not need to implement this method.
      Specified by:
      [`removeAttributeNS`](../../../org/w3c/dom/Element.md) in interface [`Element`](../../../org/w3c/dom/Element.md)

      Parameters:
      `namespaceURI` - The namespace URI of the attribute to remove.

      `localName` - The local name of the attribute to remove.

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md) - NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.

    <!-- -->

    - #### getAttributeNodeNS

          public Attr getAttributeNodeNS(java.lang.String namespaceURI,
                                         java.lang.String localName)

      Deprecated. 
      Description copied from interface: [`Element`](../../../org/w3c/dom/Element.md)
      Retrieves an `Attr` node by local name and namespace URI. HTML-only DOM implementations do not need to implement this method.
      Specified by:
      [`getAttributeNodeNS`](../../../org/w3c/dom/Element.md) in interface [`Element`](../../../org/w3c/dom/Element.md)

      Parameters:
      `namespaceURI` - The namespace URI of the attribute to retrieve.

      `localName` - The local name of the attribute to retrieve.

      Returns:
      The `Attr` node with the specified attribute local name and namespace URI or `null` if there is no such attribute.

    <!-- -->

    - #### setAttributeNodeNS

          public Attr setAttributeNodeNS(Attr newAttr)
                                  throws DOMException

      Deprecated. 
      Description copied from interface: [`Element`](../../../org/w3c/dom/Element.md)
      Adds a new attribute. If an attribute with that local name and that namespace URI is already present in the element, it is replaced by the new one.
      HTML-only DOM implementations do not need to implement this method.
      Specified by:
      [`setAttributeNodeNS`](../../../org/w3c/dom/Element.md) in interface [`Element`](../../../org/w3c/dom/Element.md)

      Parameters:
      `newAttr` - The `Attr` node to add to the attribute list.

      Returns:
      If the `newAttr` attribute replaces an existing attribute with the same local name and namespace URI, the replaced `Attr` node is returned, otherwise `null` is returned.

      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md) - WRONG_DOCUMENT_ERR: Raised if `newAttr` was created from a different document than the one that created the element.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.
      INUSE_ATTRIBUTE_ERR: Raised if `newAttr` is already an attribute of another `Element` object. The DOM user must explicitly clone `Attr` nodes to re-use them in other elements.

    <!-- -->

    - #### getElementsByTagNameNS

          public NodeList getElementsByTagNameNS(java.lang.String nsURI,
                                                 java.lang.String tag)

      Deprecated. 
      Description copied from interface: [`Element`](../../../org/w3c/dom/Element.md)
      Returns a `NodeList` of all the descendant `Elements` with a given local name and namespace URI in the order in which they are encountered in a preorder traversal of this `Element` tree.
      HTML-only DOM implementations do not need to implement this method.
      Specified by:
      [`getElementsByTagNameNS`](../../../org/w3c/dom/Element.md) in interface [`Element`](../../../org/w3c/dom/Element.md)

      Parameters:
      `nsURI` - The namespace URI of the elements to match on. The special value "\*" matches all namespaces.

      `tag` - The local name of the elements to match on. The special value "\*" matches all local names.

      Returns:
      A new `NodeList` object containing all the matched `Elements`.

    <!-- -->

    - #### hasAttribute

          public boolean hasAttribute(java.lang.String name)

      Deprecated. 
      Description copied from interface: [`Element`](../../../org/w3c/dom/Element.md)
      Returns `true` when an attribute with a given name is specified on this element or has a default value, `false` otherwise.
      Specified by:
      [`hasAttribute`](../../../org/w3c/dom/Element.md) in interface [`Element`](../../../org/w3c/dom/Element.md)

      Parameters:
      `name` - The name of the attribute to look for.

      Returns:
      `true` if an attribute with the given name is specified on this element or has a default value, `false` otherwise.

    <!-- -->

    - #### hasAttributeNS

          public boolean hasAttributeNS(java.lang.String nsURI,
                                        java.lang.String name)

      Deprecated. 
      Description copied from interface: [`Element`](../../../org/w3c/dom/Element.md)
      Returns `true` when an attribute with a given local name and namespace URI is specified on this element or has a default value, `false` otherwise. HTML-only DOM implementations do not need to implement this method.
      Specified by:
      [`hasAttributeNS`](../../../org/w3c/dom/Element.md) in interface [`Element`](../../../org/w3c/dom/Element.md)

      Parameters:
      `nsURI` - The namespace URI of the attribute to look for.

      `name` - The local name of the attribute to look for.

      Returns:
      `true` if an attribute with the given local name and namespace URI is specified or has a default value on this element, `false` otherwise.

    <!-- -->

    - #### getChildrenByTagName

          public XDBNodeList getChildrenByTagName(java.lang.String tagName)

      Deprecated. 
      get the children node list based on the tag name
      Returns:
      the children node list based on the tag name

    <!-- -->

    - #### getChildrenByTagNameNS

          public XDBNodeList getChildrenByTagNameNS(java.lang.String tagName,
                                                    java.lang.String ns)

      Deprecated. 
      get the children node list based on the tag name
      Returns:
      the children node list based on the tag name

    <!-- -->

    - #### resolveNSPrefix

          public java.lang.String resolveNSPrefix(java.lang.String prefix)

      Deprecated. 

    <!-- -->

    - #### getSchemaTypeInfo

          public TypeInfo getSchemaTypeInfo()

      Deprecated. 

    <!-- -->

    - #### setIdAttribute

          public void setIdAttribute(java.lang.String name,
                                     boolean isId)
                              throws DOMException

      Deprecated. 
      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md)

    <!-- -->

    - #### setIdAttributeNS

          public void setIdAttributeNS(java.lang.String namespaceURI,
                                       java.lang.String localName,
                                       boolean isId)
                                throws DOMException

      Deprecated. 
      Throws:
      [`DOMException`](../../../org/w3c/dom/DOMException.md)

    <!-- -->

    - #### setIdAttributeNode

          public void setIdAttributeNode(Attr idAttr,
                                         boolean isId)
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

- **[Prev Class](XDBDOMNotFoundErrException.md)**
- **[Next Class](XDBEntity.md)**

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
