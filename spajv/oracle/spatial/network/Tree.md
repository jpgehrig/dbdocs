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

- [Prev Class](SystemConstraint.md)
- [Next Class](TreeLink.md)

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

## Interface Tree

- All Superinterfaces:
  java.lang.Cloneable, java.io.Serializable

  ------------------------------------------------------------------------



      public interface Tree
      extends java.lang.Cloneable, java.io.Serializable

  This interface defines a tree for trace-out. The nodes of the tree can either be network nodes or virtual nodes on network links.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type             | Method and Description                                                                                                    |
    |-------------------------------|---------------------------------------------------------------------------------------------------------------------------|
    | [`TreeNode`](TreeNode.md)`[]` | `bestFirstSearch``()`<br>Best First Search based on cost                                                                  |
    | [`TreeNode`](TreeNode.md)`[]` | `breadthFirstSearch``()`<br>Breadth First Search                                                                          |
    | `void`                        | `clear``()`<br>Clears the tree structure                                                                                  |
    | `boolean`                     | `containsPartialLinks``()`<br>Does the tree contain particial links?                                                      |
    | [`TreeNode`](TreeNode.md)`[]` | `depthFirstSearch``()`<br>Depth First Search                                                                              |
    | [`TreeNode`](TreeNode.md)     | `get``(`[`Node`](Node.md)` node)`<br>Returns the tree node that contains the given network node                           |
    | [`TreeNode`](TreeNode.md)`[]` | `getLeafNodeArray``()`<br>Returns leaf nodes in an array                                                                  |
    | [`TreeNode`](TreeNode.md)     | `getRootNode``()`<br>Returns the root node                                                                                |
    | [`SubPath`](SubPath.md)       | `getSubPath``(`[`TreeNode`](TreeNode.md)` treeNode)`<br>Returns the subpath between the given tree node and the root node |
    | `boolean`                     | `isForward``()`<br>Returns the traverse direction                                                                         |
    | `boolean`                     | `isLogical``()`<br>Checks if the tree is logical                                                                          |
    | `int`                         | `size``()`<br>Returns number of tree nodes                                                                                |

<!-- -->

- - ### Method Detail

    - #### getRootNode

          TreeNode getRootNode()

      Returns the root node

    <!-- -->

    - #### containsPartialLinks

          boolean containsPartialLinks()

      Does the tree contain particial links?

    <!-- -->

    - #### clear

          void clear()

      Clears the tree structure

    <!-- -->

    - #### depthFirstSearch

          TreeNode[] depthFirstSearch()

      Depth First Search

    <!-- -->

    - #### breadthFirstSearch

          TreeNode[] breadthFirstSearch()

      Breadth First Search

    <!-- -->

    - #### bestFirstSearch

          TreeNode[] bestFirstSearch()

      Best First Search based on cost

    <!-- -->

    - #### getLeafNodeArray

          TreeNode[] getLeafNodeArray()

      Returns leaf nodes in an array

    <!-- -->

    - #### isLogical

          boolean isLogical()

      Checks if the tree is logical
      Returns:
      true if logical tree, false if it is a spatial tree

    <!-- -->

    - #### get

          TreeNode get(Node node)

      Returns the tree node that contains the given network node
      Parameters:
      `node` - given network node

      Returns:
      tree node that contains the given network node, null if node not in the tree

    <!-- -->

    - #### size

          int size()

      Returns number of tree nodes
      Returns:
      no of tree nodes

    <!-- -->

    - #### isForward

          boolean isForward()

      Returns the traverse direction
      Returns:
      true if the traverse direction is forward (starting from rott), false otherwise

    <!-- -->

    - #### getSubPath

          SubPath getSubPath(TreeNode treeNode)
                      throws NetworkDataException

      Returns the subpath between the given tree node and the root node
      Parameters:
      `treeNode` - the given tree node in the tree

      Returns:
      subpath between the tree node and the root node

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

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

- [Prev Class](SystemConstraint.md)
- [Next Class](TreeLink.md)

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
