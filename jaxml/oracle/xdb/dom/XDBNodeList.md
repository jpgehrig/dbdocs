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

- **[Prev Class](XDBNode.md)**
- **[Next Class](XDBNotation.md)**

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

## **Class XDBNodeList**

- **java.lang.Object**

- - **oracle.xdb.dom.XDBNodeList**

<!-- -->

- **All Implemented Interfaces:**
  **[NodeList](../../../org/w3c/dom/NodeList.md)**

  ------------------------------------------------------------------------

  **Deprecated. **
  **as of Oracle Database 11g release 1, use oracle.xml.parser.v2.XMLNodeList**
  **
  **

      public class XDBNodeList
      extends java.lang.Object
      implements NodeList

  **This class implements the W3C NodeList interface**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                      | Method and Description                                                               |
    |----------------------------------------|--------------------------------------------------------------------------------------|
    | `int`                                  | `getLength``()`<br>Deprecated. <br>The number of nodes in the list.                  |
    | [`Node`](../../../org/w3c/dom/Node.md) | `item``(int index)`<br>Deprecated. <br>Returns the `index`th item in the collection. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getLength

          public int getLength()

      Deprecated. 
      Description copied from interface: [`NodeList`](../../../org/w3c/dom/NodeList.md)
      The number of nodes in the list. The range of valid child node indices is 0 to `length-1` inclusive.
      Specified by:
      [`getLength`](../../../org/w3c/dom/NodeList.md) in interface [`NodeList`](../../../org/w3c/dom/NodeList.md)

    <!-- -->

    - #### item

          public Node item(int index)

      Deprecated. 
      Description copied from interface: [`NodeList`](../../../org/w3c/dom/NodeList.md)
      Returns the `index`th item in the collection. If `index` is greater than or equal to the number of nodes in the list, this returns `null`.
      Specified by:
      [`item`](../../../org/w3c/dom/NodeList.md) in interface [`NodeList`](../../../org/w3c/dom/NodeList.md)

      Parameters:
      `index` - Index into the collection.

      Returns:
      The node at the `index`th position in the `NodeList`, or `null` if that is not a valid index.

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

- **[Prev Class](XDBNode.md)**
- **[Next Class](XDBNotation.md)**

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
