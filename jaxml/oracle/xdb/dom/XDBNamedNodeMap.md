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

- **[Prev Class](XDBEntityReference.md)**
- **[Next Class](XDBNode.md)**

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

## **Class XDBNamedNodeMap**

- **java.lang.Object**

- - **oracle.xdb.dom.XDBNamedNodeMap**

<!-- -->

- **All Implemented Interfaces:**
  **[NamedNodeMap](../../../org/w3c/dom/NamedNodeMap.md)**

  ------------------------------------------------------------------------

  **Deprecated. **
  **as of Oracle Database 11g release 1, use oracle.xml.parser.v2.XMLAttrList**
  **
  **

      public class XDBNamedNodeMap
      extends java.lang.Object
      implements NamedNodeMap

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                      | Method and Description                                                                                                                            |
    |----------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`                                  | `getLength``()`<br>Deprecated. <br>The number of nodes in this map.                                                                               |
    | [`Node`](../../../org/w3c/dom/Node.md) | `getNamedItem``(java.lang.String name)`<br>Deprecated. <br>Retrieves a node specified by name.                                                    |
    | [`Node`](../../../org/w3c/dom/Node.md) | `getNamedItemNS``(java.lang.String nsURI, java.lang.String name)`<br>Deprecated. <br>Retrieves a node specified by local name and namespace URI.  |
    | [`Node`](../../../org/w3c/dom/Node.md) | `item``(int index)`<br>Deprecated. <br>Returns the `index`th item in the map.                                                                     |
    | [`Node`](../../../org/w3c/dom/Node.md) | `removeNamedItem``(java.lang.String name)`<br>Deprecated. <br>Removes a node specified by name.                                                   |
    | [`Node`](../../../org/w3c/dom/Node.md) | `removeNamedItemNS``(java.lang.String nsURI, java.lang.String name)`<br>Deprecated. <br>Removes a node specified by local name and namespace URI. |
    | [`Node`](../../../org/w3c/dom/Node.md) | `setNamedItem``(`[`Node`](../../../org/w3c/dom/Node.md)` node)`<br>Deprecated. <br>Adds a node using its `nodeName` attribute.                    |
    | [`Node`](../../../org/w3c/dom/Node.md) | `setNamedItemNS``(`[`Node`](../../../org/w3c/dom/Node.md)` node)`<br>Deprecated. <br>Adds a node using its `namespaceURI` and `localName`.        |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getLength

          public int getLength()

      Deprecated. 
      Description copied from interface: [`NamedNodeMap`](../../../org/w3c/dom/NamedNodeMap.md)
      The number of nodes in this map. The range of valid child node indices is `0` to `length-1` inclusive.
      Specified by:
      [`getLength`](../../../org/w3c/dom/NamedNodeMap.md) in interface [`NamedNodeMap`](../../../org/w3c/dom/NamedNodeMap.md)

    <!-- -->

    - #### getNamedItem

          public Node getNamedItem(java.lang.String name)

      Deprecated. 
      Description copied from interface: [`NamedNodeMap`](../../../org/w3c/dom/NamedNodeMap.md)
      Retrieves a node specified by name.
      Specified by:
      [`getNamedItem`](../../../org/w3c/dom/NamedNodeMap.md) in interface [`NamedNodeMap`](../../../org/w3c/dom/NamedNodeMap.md)

      Parameters:
      `name` - The `nodeName` of a node to retrieve.

      Returns:
      A `Node` (of any type) with the specified `nodeName`, or `null` if it does not identify any node in this map.

    <!-- -->

    - #### setNamedItem

          public Node setNamedItem(Node node)

      Deprecated. 
      Description copied from interface: [`NamedNodeMap`](../../../org/w3c/dom/NamedNodeMap.md)
      Adds a node using its `nodeName` attribute. If a node with that name is already present in this map, it is replaced by the new one.
      As the `nodeName` attribute is used to derive the name which the node must be stored under, multiple nodes of certain types (those that have a "special" string value) cannot be stored as the names would clash. This is seen as preferable to allowing nodes to be aliased.
      Specified by:
      [`setNamedItem`](../../../org/w3c/dom/NamedNodeMap.md) in interface [`NamedNodeMap`](../../../org/w3c/dom/NamedNodeMap.md)

      Parameters:
      `node` - node to store in this map. The node will later be accessible using the value of its `nodeName` attribute.

      Returns:
      If the new `Node` replaces an existing node the replaced `Node` is returned, otherwise `null` is returned.

    <!-- -->

    - #### removeNamedItem

          public Node removeNamedItem(java.lang.String name)

      Deprecated. 
      Description copied from interface: [`NamedNodeMap`](../../../org/w3c/dom/NamedNodeMap.md)
      Removes a node specified by name. When this map contains the attributes attached to an element, if the removed attribute is known to have a default value, an attribute immediately appears containing the default value as well as the corresponding namespace URI, local name, and prefix when applicable.
      Specified by:
      [`removeNamedItem`](../../../org/w3c/dom/NamedNodeMap.md) in interface [`NamedNodeMap`](../../../org/w3c/dom/NamedNodeMap.md)

      Parameters:
      `name` - The `nodeName` of the node to remove.

      Returns:
      The node removed from this map if a node with such a name exists.

    <!-- -->

    - #### getNamedItemNS

          public Node getNamedItemNS(java.lang.String nsURI,
                                     java.lang.String name)

      Deprecated. 
      Description copied from interface: [`NamedNodeMap`](../../../org/w3c/dom/NamedNodeMap.md)
      Retrieves a node specified by local name and namespace URI. HTML-only DOM implementations do not need to implement this method.
      Specified by:
      [`getNamedItemNS`](../../../org/w3c/dom/NamedNodeMap.md) in interface [`NamedNodeMap`](../../../org/w3c/dom/NamedNodeMap.md)

      Parameters:
      `nsURI` - The namespace URI of the node to retrieve.

      `name` - The local name of the node to retrieve.

      Returns:
      A `Node` (of any type) with the specified local name and namespace URI, or `null` if they do not identify any node in this map.

    <!-- -->

    - #### setNamedItemNS

          public Node setNamedItemNS(Node node)

      Deprecated. 
      Description copied from interface: [`NamedNodeMap`](../../../org/w3c/dom/NamedNodeMap.md)
      Adds a node using its `namespaceURI` and `localName`. If a node with that namespace URI and that local name is already present in this map, it is replaced by the new one.
      HTML-only DOM implementations do not need to implement this method.
      Specified by:
      [`setNamedItemNS`](../../../org/w3c/dom/NamedNodeMap.md) in interface [`NamedNodeMap`](../../../org/w3c/dom/NamedNodeMap.md)

      Parameters:
      `node` - node to store in this map. The node will later be accessible using the value of its `namespaceURI` and `localName` attributes.

      Returns:
      If the new `Node` replaces an existing node the replaced `Node` is returned, otherwise `null` is returned.

    <!-- -->

    - #### removeNamedItemNS

          public Node removeNamedItemNS(java.lang.String nsURI,
                                        java.lang.String name)

      Deprecated. 
      Description copied from interface: [`NamedNodeMap`](../../../org/w3c/dom/NamedNodeMap.md)
      Removes a node specified by local name and namespace URI. A removed attribute may be known to have a default value when this map contains the attributes attached to an element, as returned by the attributes attribute of the `Node` interface. If so, an attribute immediately appears containing the default value as well as the corresponding namespace URI, local name, and prefix when applicable.
      HTML-only DOM implementations do not need to implement this method.
      Specified by:
      [`removeNamedItemNS`](../../../org/w3c/dom/NamedNodeMap.md) in interface [`NamedNodeMap`](../../../org/w3c/dom/NamedNodeMap.md)

      Parameters:
      `nsURI` - The namespace URI of the node to remove.

      `name` - The local name of the node to remove.

      Returns:
      The node removed from this map if a node with such a local name and namespace URI exists.

    <!-- -->

    - #### item

          public Node item(int index)

      Deprecated. 
      Description copied from interface: [`NamedNodeMap`](../../../org/w3c/dom/NamedNodeMap.md)
      Returns the `index`th item in the map. If `index` is greater than or equal to the number of nodes in this map, this returns `null`.
      Specified by:
      [`item`](../../../org/w3c/dom/NamedNodeMap.md) in interface [`NamedNodeMap`](../../../org/w3c/dom/NamedNodeMap.md)

      Parameters:
      `index` - Index into this map.

      Returns:
      The node at the `index`th position in the map, or `null` if that is not a valid index.

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

- **[Prev Class](XDBEntityReference.md)**
- **[Next Class](XDBNode.md)**

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
