Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](TreeLink.md)
- [Next Class](UserDataIO.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

oracle.spatial.network

## Interface TreeNode

- All Superinterfaces:
  java.lang.Cloneable, java.lang.Comparable, java.io.Serializable

  ------------------------------------------------------------------------



      public interface TreeNode
      extends java.lang.Cloneable, java.io.Serializable, java.lang.Comparable

  This interface defines a tree node for trace-out. The nodes of the tree can either be network nodes or virtual nodes on network links.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                       | Method and Description                                                                                                                                                                    |
    |-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                  | `addChildNode``(`[`TreeLink`](TreeLink.md)` tLink, TreeNode tNode)`<br>Adds a child tree node to current tree node                                                                        |
    | `TreeNode[]`                            | `getChildNodeArray``()`<br>Returns the child tree node in an array                                                                                                                        |
    | `double`                                | `getCost``()`<br>Returns the cost from root node                                                                                                                                          |
    | `int`                                   | `getDepth``()`<br>Returns the depth of the node form root.                                                                                                                                |
    | `double`                                | `getDuration``()`<br>Returns the sum of duration from root to this tree node                                                                                                              |
    | [`JGeometry`](../geometry/JGeometry.md) | `getGeometry``()`<br>Returns the geometry of the tree node                                                                                                                                |
    | [`Link`](Link.md)                       | `getLink``()`<br>Returns the link and percentage on the link if the tree node is a node on the link isNodeOnLink() == true                                                                |
    | [`Node`](Node.md)                       | `getNode``()`<br>If the node is a regular node (not a node on a link)                                                                                                                     |
    | `TreeNode`                              | `getParentNode``()`<br>Returns the parent tree node                                                                                                                                       |
    | `double`                                | `getPercentage``()`<br>Returns the link and percentage on the link if the tree node is a node on the link isNodeOnLink() == true                                                          |
    | [`TreeLink`](TreeLink.md)               | `getTreeLink``()`<br>Returns the tree link that leads to this tree node                                                                                                                   |
    | `boolean`                               | `isLeafNode``()`<br>Returns the tree link array that leads to the child nodes i-th tree link leads to i-th child tree node public TreeLink getTreeLink() ; /\*\* Is the node a leaf node? |
    | `boolean`                               | `isNodeOnLink``()`<br>Check whether this node is on a link.                                                                                                                               |
    | `boolean`                               | `isRegularNode``()`<br>Returns the regular node if the tree node is a regular node isNodeOnLink() == false                                                                                |

    - ### Methods inherited from interface java.lang.Comparable

      `compareTo`

<!-- -->

- - ### Method Detail

    - #### getParentNode

          TreeNode getParentNode()

      Returns the parent tree node

    <!-- -->

    - #### getChildNodeArray

          TreeNode[] getChildNodeArray()

      Returns the child tree node in an array

    <!-- -->

    - #### isLeafNode

          boolean isLeafNode()

      Returns the tree link array that leads to the child nodes i-th tree link leads to i-th child tree node public TreeLink getTreeLink() ; /\*\* Is the node a leaf node?

    <!-- -->

    - #### isNodeOnLink

          boolean isNodeOnLink()

      Check whether this node is on a link. A tree node can either be a regular node or a node on a link

    <!-- -->

    - #### isRegularNode

          boolean isRegularNode()

      Returns the regular node if the tree node is a regular node isNodeOnLink() == false

    <!-- -->

    - #### getNode

          Node getNode()

      If the node is a regular node (not a node on a link)

    <!-- -->

    - #### getLink

          Link getLink()

      Returns the link and percentage on the link if the tree node is a node on the link isNodeOnLink() == true

    <!-- -->

    - #### getPercentage

          double getPercentage()

      Returns the link and percentage on the link if the tree node is a node on the link isNodeOnLink() == true

    <!-- -->

    - #### addChildNode

          void addChildNode(TreeLink tLink,
                            TreeNode tNode)

      Adds a child tree node to current tree node

    <!-- -->

    - #### getDepth

          int getDepth()

      Returns the depth of the node form root. Root has depth 0

    <!-- -->

    - #### getCost

          double getCost()

      Returns the cost from root node

    <!-- -->

    - #### getTreeLink

          TreeLink getTreeLink()

      Returns the tree link that leads to this tree node

    <!-- -->

    - #### getGeometry

          JGeometry getGeometry()

      Returns the geometry of the tree node

    <!-- -->

    - #### getDuration

          double getDuration()

      Returns the sum of duration from root to this tree node
      Returns:
      sum of duration

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](TreeLink.md)
- [Next Class](UserDataIO.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

<!-- -->

- Summary: 
- Nested \| 
- Field \| 
- Constr \| 
- Method

<!-- -->

- Detail: 
- Field \| 
- Constr \| 
- Method

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
