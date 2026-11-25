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

- **[Prev Class](EntityReference.md)**
- **[Next Class](NameList.md)**

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

## **Interface NamedNodeMap**

- **All Known Implementing Classes:**
  **[XDBNamedNodeMap](../../../oracle/xdb/dom/XDBNamedNodeMap.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface NamedNodeMap

  **Objects implementing the `NamedNodeMap` interface are used to represent collections of nodes that can be accessed by name. Note that `NamedNodeMap` does not inherit from `NodeList`; `NamedNodeMaps` are not maintained in any particular order. Objects contained in an object implementing `NamedNodeMap` may also be accessed by an ordinal index, but this is simply to allow convenient enumeration of the contents of a `NamedNodeMap`, and does not imply that the DOM specifies an order to these Nodes.**
  **`NamedNodeMap` objects in the DOM are live.**

  **See also the [Document Object Model (DOM) Level 2 Core Specification](http://www.w3.org/TR/2000/REC-DOM-Level-2-Core-20001113).**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                        |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`             | `getLength``()`<br>The number of nodes in this map.                                                                                           |
    | [`Node`](Node.md) | `getNamedItem``(java.lang.String name)`<br>Retrieves a node specified by name.                                                                |
    | [`Node`](Node.md) | `getNamedItemNS``(java.lang.String namespaceURI, java.lang.String localName)`<br>Retrieves a node specified by local name and namespace URI.  |
    | [`Node`](Node.md) | `item``(int index)`<br>Returns the `index`th item in the map.                                                                                 |
    | [`Node`](Node.md) | `removeNamedItem``(java.lang.String name)`<br>Removes a node specified by name.                                                               |
    | [`Node`](Node.md) | `removeNamedItemNS``(java.lang.String namespaceURI, java.lang.String localName)`<br>Removes a node specified by local name and namespace URI. |
    | [`Node`](Node.md) | `setNamedItem``(`[`Node`](Node.md)` arg)`<br>Adds a node using its `nodeName` attribute.                                                      |
    | [`Node`](Node.md) | `setNamedItemNS``(`[`Node`](Node.md)` arg)`<br>Adds a node using its `namespaceURI` and `localName`.                                          |

<!-- -->

- - ### Method Detail

    - #### getNamedItem

          Node getNamedItem(java.lang.String name)

      Retrieves a node specified by name.
      Parameters:
      `name` - The `nodeName` of a node to retrieve.

      Returns:
      A `Node` (of any type) with the specified `nodeName`, or `null` if it does not identify any node in this map.

    <!-- -->

    - #### setNamedItem

          Node setNamedItem(Node arg)
                     throws DOMException

      Adds a node using its `nodeName` attribute. If a node with that name is already present in this map, it is replaced by the new one.
      As the `nodeName` attribute is used to derive the name which the node must be stored under, multiple nodes of certain types (those that have a "special" string value) cannot be stored as the names would clash. This is seen as preferable to allowing nodes to be aliased.
      Parameters:
      `arg` - node to store in this map. The node will later be accessible using the value of its `nodeName` attribute.

      Returns:
      If the new `Node` replaces an existing node the replaced `Node` is returned, otherwise `null` is returned.

      Throws:
      [`DOMException`](DOMException.md) - WRONG_DOCUMENT_ERR: Raised if `arg` was created from a different document than the one that created this map.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this map is readonly.
      INUSE_ATTRIBUTE_ERR: Raised if `arg` is an `Attr` that is already an attribute of another `Element` object. The DOM user must explicitly clone `Attr` nodes to re-use them in other elements.

    <!-- -->

    - #### removeNamedItem

          Node removeNamedItem(java.lang.String name)
                        throws DOMException

      Removes a node specified by name. When this map contains the attributes attached to an element, if the removed attribute is known to have a default value, an attribute immediately appears containing the default value as well as the corresponding namespace URI, local name, and prefix when applicable.
      Parameters:
      `name` - The `nodeName` of the node to remove.

      Returns:
      The node removed from this map if a node with such a name exists.

      Throws:
      [`DOMException`](DOMException.md) - NOT_FOUND_ERR: Raised if there is no node named `name` in this map.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this map is readonly.

    <!-- -->

    - #### item

          Node item(int index)

      Returns the `index`th item in the map. If `index` is greater than or equal to the number of nodes in this map, this returns `null`.
      Parameters:
      `index` - Index into this map.

      Returns:
      The node at the `index`th position in the map, or `null` if that is not a valid index.

    <!-- -->

    - #### getLength

          int getLength()

      The number of nodes in this map. The range of valid child node indices is `0` to `length-1` inclusive.

    <!-- -->

    - #### getNamedItemNS

          Node getNamedItemNS(java.lang.String namespaceURI,
                              java.lang.String localName)

      Retrieves a node specified by local name and namespace URI. HTML-only DOM implementations do not need to implement this method.
      Parameters:
      `namespaceURI` - The namespace URI of the node to retrieve.

      `localName` - The local name of the node to retrieve.

      Returns:
      A `Node` (of any type) with the specified local name and namespace URI, or `null` if they do not identify any node in this map.

      Since:
      DOM Level 2

    <!-- -->

    - #### setNamedItemNS

          Node setNamedItemNS(Node arg)
                       throws DOMException

      Adds a node using its `namespaceURI` and `localName`. If a node with that namespace URI and that local name is already present in this map, it is replaced by the new one.
      HTML-only DOM implementations do not need to implement this method.
      Parameters:
      `arg` - node to store in this map. The node will later be accessible using the value of its `namespaceURI` and `localName` attributes.

      Returns:
      If the new `Node` replaces an existing node the replaced `Node` is returned, otherwise `null` is returned.

      Throws:
      [`DOMException`](DOMException.md) - WRONG_DOCUMENT_ERR: Raised if `arg` was created from a different document than the one that created this map.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this map is readonly.
      INUSE_ATTRIBUTE_ERR: Raised if `arg` is an `Attr` that is already an attribute of another `Element` object. The DOM user must explicitly clone `Attr` nodes to re-use them in other elements.

      Since:
      DOM Level 2

    <!-- -->

    - #### removeNamedItemNS

          Node removeNamedItemNS(java.lang.String namespaceURI,
                                 java.lang.String localName)
                          throws DOMException

      Removes a node specified by local name and namespace URI. A removed attribute may be known to have a default value when this map contains the attributes attached to an element, as returned by the attributes attribute of the `Node` interface. If so, an attribute immediately appears containing the default value as well as the corresponding namespace URI, local name, and prefix when applicable.
      HTML-only DOM implementations do not need to implement this method.
      Parameters:
      `namespaceURI` - The namespace URI of the node to remove.

      `localName` - The local name of the node to remove.

      Returns:
      The node removed from this map if a node with such a local name and namespace URI exists.

      Throws:
      [`DOMException`](DOMException.md) - NOT_FOUND_ERR: Raised if there is no node with the specified `namespaceURI` and `localName` in this map.
      NO_MODIFICATION_ALLOWED_ERR: Raised if this map is readonly.

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

- **[Prev Class](EntityReference.md)**
- **[Next Class](NameList.md)**

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
