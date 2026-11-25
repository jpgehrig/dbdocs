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

- **[Prev Class](DOMStringList.md)**
- **[Next Class](Entity.md)**

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

## **Interface Element**

- **All Superinterfaces:**
  **[Node](Node.md)**

  <!-- -->

  **All Known Implementing Classes:**
  **[XDBElement](../../../oracle/xdb/dom/XDBElement.md), [XMLDocument](../../../oracle/xml/parser/v2/XMLDocument.md), [XMLDocumentFragment](../../../oracle/xml/parser/v2/XMLDocumentFragment.md), [XMLElement](../../../oracle/xml/parser/v2/XMLElement.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface Element
      extends Node

  **The `Element` interface represents an element in an HTML or XML document. Elements may have attributes associated with them; since the `Element` interface inherits from `Node`, the generic `Node` interface attribute `attributes` may be used to retrieve the set of all attributes for an element. There are methods on the `Element` interface to retrieve either an `Attr` object by name or an attribute value by name. In XML, where an attribute value may contain entity references, an `Attr` object should be retrieved to examine the possibly fairly complex sub-tree representing the attribute value. On the other hand, in HTML, where all attributes have simple string values, methods to directly access an attribute value can safely be used as a convenience.In DOM Level 2, the method `normalize` is inherited from the `Node` interface where it was moved.**
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

    | Modifier and Type         | Method and Description                                                                                                                                                                                                                                                              |
    |---------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`        | `getAttribute``(java.lang.String name)`<br>Retrieves an attribute value by name.                                                                                                                                                                                                    |
    | [`Attr`](Attr.md)         | `getAttributeNode``(java.lang.String name)`<br>Retrieves an attribute node by name.                                                                                                                                                                                                 |
    | [`Attr`](Attr.md)         | `getAttributeNodeNS``(java.lang.String namespaceURI, java.lang.String localName)`<br>Retrieves an `Attr` node by local name and namespace URI.                                                                                                                                      |
    | `java.lang.String`        | `getAttributeNS``(java.lang.String namespaceURI, java.lang.String localName)`<br>Retrieves an attribute value by local name and namespace URI.                                                                                                                                      |
    | [`NodeList`](NodeList.md) | `getElementsByTagName``(java.lang.String name)`<br>Returns a `NodeList` of all descendant `Elements` with a given tag name, in the order in which they are encountered in a preorder traversal of this `Element` tree.                                                              |
    | [`NodeList`](NodeList.md) | `getElementsByTagNameNS``(java.lang.String namespaceURI, java.lang.String localName)`<br>Returns a `NodeList` of all the descendant `Elements` with a given local name and namespace URI in the order in which they are encountered in a preorder traversal of this `Element` tree. |
    | `java.lang.String`        | `getTagName``()`<br>The name of the element.                                                                                                                                                                                                                                        |
    | `boolean`                 | `hasAttribute``(java.lang.String name)`<br>Returns `true` when an attribute with a given name is specified on this element or has a default value, `false` otherwise.                                                                                                               |
    | `boolean`                 | `hasAttributeNS``(java.lang.String namespaceURI, java.lang.String localName)`<br>Returns `true` when an attribute with a given local name and namespace URI is specified on this element or has a default value, `false` otherwise.                                                 |
    | `void`                    | `removeAttribute``(java.lang.String name)`<br>Removes an attribute by name.                                                                                                                                                                                                         |
    | [`Attr`](Attr.md)         | `removeAttributeNode``(`[`Attr`](Attr.md)` oldAttr)`<br>Removes the specified attribute node.                                                                                                                                                                                       |
    | `void`                    | `removeAttributeNS``(java.lang.String namespaceURI, java.lang.String localName)`<br>Removes an attribute by local name and namespace URI.                                                                                                                                           |
    | `void`                    | `setAttribute``(java.lang.String name, java.lang.String value)`<br>Adds a new attribute.                                                                                                                                                                                            |
    | [`Attr`](Attr.md)         | `setAttributeNode``(`[`Attr`](Attr.md)` newAttr)`<br>Adds a new attribute node.                                                                                                                                                                                                     |
    | [`Attr`](Attr.md)         | `setAttributeNodeNS``(`[`Attr`](Attr.md)` newAttr)`<br>Adds a new attribute.                                                                                                                                                                                                        |
    | `void`                    | `setAttributeNS``(java.lang.String namespaceURI, java.lang.String qualifiedName, java.lang.String value)`<br>Adds a new attribute.                                                                                                                                                  |

    - ### Methods inherited from interface org.w3c.dom.[Node](Node.md)

      [`appendChild`](Node.md)`, `[`cloneNode`](Node.md)`, `[`getAttributes`](Node.md)`, `[`getChildNodes`](Node.md)`, `[`getFirstChild`](Node.md)`, `[`getLastChild`](Node.md)`, `[`getLocalName`](Node.md)`, `[`getNamespaceURI`](Node.md)`, `[`getNextSibling`](Node.md)`, `[`getNodeName`](Node.md)`, `[`getNodeType`](Node.md)`, `[`getNodeValue`](Node.md)`, `[`getOwnerDocument`](Node.md)`, `[`getParentNode`](Node.md)`, `[`getPrefix`](Node.md)`, `[`getPreviousSibling`](Node.md)`, `[`hasAttributes`](Node.md)`, `[`hasChildNodes`](Node.md)`, `[`insertBefore`](Node.md)`, `[`isSupported`](Node.md)`, `[`normalize`](Node.md)`, `[`removeChild`](Node.md)`, `[`replaceChild`](Node.md)`, `[`setNodeValue`](Node.md)`, `[`setPrefix`](Node.md)

<!-- -->

- - ### Method Detail

    - #### getTagName

          java.lang.String getTagName()

      The name of the element. For example, in:
           <elementExample
           id="demo"> ... </elementExample> ,

      `tagName` has the value `"elementExample"`. Note that this is case-preserving in XML, as are all of the operations of the DOM. The HTML DOM returns the `tagName` of an HTML element in the canonical uppercase form, regardless of the case in the source HTML document.

    <!-- -->

    - #### getAttribute

          java.lang.String getAttribute(java.lang.String name)

      Retrieves an attribute value by name.
      Parameters:
      `name` - The name of the attribute to retrieve.

      Returns:
      The `Attr` value as a string, or the empty string if that attribute does not have a specified or default value.

    <!-- -->

    - #### setAttribute

          void setAttribute(java.lang.String name,
                            java.lang.String value)
                     throws DOMException

      Adds a new attribute. If an attribute with that name is already present in the element, its value is changed to be that of the value parameter. This value is a simple string; it is not parsed as it is being set. So any markup (such as syntax to be recognized as an entity reference) is treated as literal text, and needs to be appropriately escaped by the implementation when it is written out. In order to assign an attribute value that contains entity references, the user must create an `Attr` node plus any `Text` and `EntityReference` nodes, build the appropriate subtree, and use `setAttributeNode` to assign it as the value of an attribute.
      To set an attribute with a qualified name and namespace URI, use the `setAttributeNS` method.
      Parameters:
      `name` - The name of the attribute to create or alter.

      `value` - Value to set in string form.

      Throws:
      [`DOMException`](DOMException.md) - INVALID_CHARACTER_ERR: Raised if the specified name contains an illegal character.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.

    <!-- -->

    - #### removeAttribute

          void removeAttribute(java.lang.String name)
                        throws DOMException

      Removes an attribute by name. If the removed attribute is known to have a default value, an attribute immediately appears containing the default value as well as the corresponding namespace URI, local name, and prefix when applicable.
      To remove an attribute by local name and namespace URI, use the `removeAttributeNS` method.
      Parameters:
      `name` - The name of the attribute to remove.

      Throws:
      [`DOMException`](DOMException.md) - NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.

    <!-- -->

    - #### getAttributeNode

          Attr getAttributeNode(java.lang.String name)

      Retrieves an attribute node by name.
      To retrieve an attribute node by qualified name and namespace URI, use the `getAttributeNodeNS` method.
      Parameters:
      `name` - The name (`nodeName`) of the attribute to retrieve.

      Returns:
      The `Attr` node with the specified name ( `nodeName`) or `null` if there is no such attribute.

    <!-- -->

    - #### setAttributeNode

          Attr setAttributeNode(Attr newAttr)
                         throws DOMException

      Adds a new attribute node. If an attribute with that name ( `nodeName`) is already present in the element, it is replaced by the new one.
      To add a new attribute node with a qualified name and namespace URI, use the `setAttributeNodeNS` method.
      Parameters:
      `newAttr` - The `Attr` node to add to the attribute list.

      Returns:
      If the `newAttr` attribute replaces an existing attribute, the replaced `Attr` node is returned, otherwise `null` is returned.

      Throws:
      [`DOMException`](DOMException.md) - WRONG_DOCUMENT_ERR: Raised if `newAttr` was created from a different document than the one that created the element.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.
      INUSE_ATTRIBUTE_ERR: Raised if `newAttr` is already an attribute of another `Element` object. The DOM user must explicitly clone `Attr` nodes to re-use them in other elements.

    <!-- -->

    - #### removeAttributeNode

          Attr removeAttributeNode(Attr oldAttr)
                            throws DOMException

      Removes the specified attribute node. If the removed `Attr` has a default value it is immediately replaced. The replacing attribute has the same namespace URI and local name, as well as the original prefix, when applicable.
      Parameters:
      `oldAttr` - The `Attr` node to remove from the attribute list.

      Returns:
      The `Attr` node that was removed.

      Throws:
      [`DOMException`](DOMException.md) - NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.
      NOT_FOUND_ERR: Raised if `oldAttr` is not an attribute of the element.

    <!-- -->

    - #### getElementsByTagName

          NodeList getElementsByTagName(java.lang.String name)

      Returns a `NodeList` of all descendant `Elements` with a given tag name, in the order in which they are encountered in a preorder traversal of this `Element` tree.
      Parameters:
      `name` - The name of the tag to match on. The special value "\*" matches all tags.

      Returns:
      A list of matching `Element` nodes.

    <!-- -->

    - #### getAttributeNS

          java.lang.String getAttributeNS(java.lang.String namespaceURI,
                                          java.lang.String localName)

      Retrieves an attribute value by local name and namespace URI. HTML-only DOM implementations do not need to implement this method.
      Parameters:
      `namespaceURI` - The namespace URI of the attribute to retrieve.

      `localName` - The local name of the attribute to retrieve.

      Returns:
      The `Attr` value as a string, or the empty string if that attribute does not have a specified or default value.

      Since:
      DOM Level 2

    <!-- -->

    - #### setAttributeNS

          void setAttributeNS(java.lang.String namespaceURI,
                              java.lang.String qualifiedName,
                              java.lang.String value)
                       throws DOMException

      Adds a new attribute. If an attribute with the same local name and namespace URI is already present on the element, its prefix is changed to be the prefix part of the `qualifiedName`, and its value is changed to be the `value` parameter. This value is a simple string; it is not parsed as it is being set. So any markup (such as syntax to be recognized as an entity reference) is treated as literal text, and needs to be appropriately escaped by the implementation when it is written out. In order to assign an attribute value that contains entity references, the user must create an `Attr` node plus any `Text` and `EntityReference` nodes, build the appropriate subtree, and use `setAttributeNodeNS` or `setAttributeNode` to assign it as the value of an attribute.
      HTML-only DOM implementations do not need to implement this method.
      Parameters:
      `namespaceURI` - The namespace URI of the attribute to create or alter.

      `qualifiedName` - The qualified name of the attribute to create or alter.

      `value` - The value to set in string form.

      Throws:
      [`DOMException`](DOMException.md) - INVALID_CHARACTER_ERR: Raised if the specified qualified name contains an illegal character.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.
      NAMESPACE_ERR: Raised if the `qualifiedName` is malformed, if the `qualifiedName` has a prefix and the `namespaceURI` is `null`, if the `qualifiedName` has a prefix that is "xml" and the `namespaceURI` is different from " http://www.w3.org/XML/1998/namespace", or if the `qualifiedName` is "xmlns" and the `namespaceURI` is different from " http://www.w3.org/2000/xmlns/".

      Since:
      DOM Level 2

    <!-- -->

    - #### removeAttributeNS

          void removeAttributeNS(java.lang.String namespaceURI,
                                 java.lang.String localName)
                          throws DOMException

      Removes an attribute by local name and namespace URI. If the removed attribute has a default value it is immediately replaced. The replacing attribute has the same namespace URI and local name, as well as the original prefix.
      HTML-only DOM implementations do not need to implement this method.
      Parameters:
      `namespaceURI` - The namespace URI of the attribute to remove.

      `localName` - The local name of the attribute to remove.

      Throws:
      [`DOMException`](DOMException.md) - NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.

      Since:
      DOM Level 2

    <!-- -->

    - #### getAttributeNodeNS

          Attr getAttributeNodeNS(java.lang.String namespaceURI,
                                  java.lang.String localName)

      Retrieves an `Attr` node by local name and namespace URI. HTML-only DOM implementations do not need to implement this method.
      Parameters:
      `namespaceURI` - The namespace URI of the attribute to retrieve.

      `localName` - The local name of the attribute to retrieve.

      Returns:
      The `Attr` node with the specified attribute local name and namespace URI or `null` if there is no such attribute.

      Since:
      DOM Level 2

    <!-- -->

    - #### setAttributeNodeNS

          Attr setAttributeNodeNS(Attr newAttr)
                           throws DOMException

      Adds a new attribute. If an attribute with that local name and that namespace URI is already present in the element, it is replaced by the new one.
      HTML-only DOM implementations do not need to implement this method.
      Parameters:
      `newAttr` - The `Attr` node to add to the attribute list.

      Returns:
      If the `newAttr` attribute replaces an existing attribute with the same local name and namespace URI, the replaced `Attr` node is returned, otherwise `null` is returned.

      Throws:
      [`DOMException`](DOMException.md) - WRONG_DOCUMENT_ERR: Raised if `newAttr` was created from a different document than the one that created the element.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this node is readonly.
      INUSE_ATTRIBUTE_ERR: Raised if `newAttr` is already an attribute of another `Element` object. The DOM user must explicitly clone `Attr` nodes to re-use them in other elements.

      Since:
      DOM Level 2

    <!-- -->

    - #### getElementsByTagNameNS

          NodeList getElementsByTagNameNS(java.lang.String namespaceURI,
                                          java.lang.String localName)

      Returns a `NodeList` of all the descendant `Elements` with a given local name and namespace URI in the order in which they are encountered in a preorder traversal of this `Element` tree.
      HTML-only DOM implementations do not need to implement this method.
      Parameters:
      `namespaceURI` - The namespace URI of the elements to match on. The special value "\*" matches all namespaces.

      `localName` - The local name of the elements to match on. The special value "\*" matches all local names.

      Returns:
      A new `NodeList` object containing all the matched `Elements`.

      Since:
      DOM Level 2

    <!-- -->

    - #### hasAttribute

          boolean hasAttribute(java.lang.String name)

      Returns `true` when an attribute with a given name is specified on this element or has a default value, `false` otherwise.
      Parameters:
      `name` - The name of the attribute to look for.

      Returns:
      `true` if an attribute with the given name is specified on this element or has a default value, `false` otherwise.

      Since:
      DOM Level 2

    <!-- -->

    - #### hasAttributeNS

          boolean hasAttributeNS(java.lang.String namespaceURI,
                                 java.lang.String localName)

      Returns `true` when an attribute with a given local name and namespace URI is specified on this element or has a default value, `false` otherwise. HTML-only DOM implementations do not need to implement this method.
      Parameters:
      `namespaceURI` - The namespace URI of the attribute to look for.

      `localName` - The local name of the attribute to look for.

      Returns:
      `true` if an attribute with the given local name and namespace URI is specified or has a default value on this element, `false` otherwise.

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

- **[Prev Class](DOMStringList.md)**
- **[Next Class](Entity.md)**

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
