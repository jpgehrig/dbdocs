Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NetworkBuffer.DoubleInterval.md)
- [Next Class](NetworkBuffer.LinkInterval.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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

oracle.spatial.network.lod

## Class NetworkBuffer.Elements

- java.lang.Object

- - oracle.spatial.network.lod.NetworkBuffer.Elements

<!-- -->

- Enclosing class:
  [NetworkBuffer](NetworkBuffer.md)

  ------------------------------------------------------------------------



      public static class NetworkBuffer.Elements
      extends java.lang.Object

  This class contains elements in a network buffer.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `Elements``()`              |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                   | Method and Description                                                                                 |
    |---------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------|
    | `void`                                                              | `addLinkIntervals``(`[`NetworkBuffer.LinkIntervals`](NetworkBuffer.LinkIntervals.md)` linkIntervals)`  |
    | `void`                                                              | `addNode``(`[`LogicalNode`](LogicalNode.md)` node)`<br>Adds a node to the network elements.            |
    | [`NetworkBuffer.LinkIntervals`](NetworkBuffer.LinkIntervals.md)`[]` | `getLinkIntervals``()`<br>Returns the link intervals in the network elements.                          |
    | [`NetworkBuffer.LinkIntervals`](NetworkBuffer.LinkIntervals.md)     | `getLinkIntervals``(long linkId)`<br>Returns the link intervals of the specified link.                 |
    | [`LogicalNode`](LogicalNode.md)                                     | `getNode``(long nodeId)`<br>Returns the node object of the specified node.                             |
    | [`LogicalNode`](LogicalNode.md)`[]`                                 | `getNodes``()`<br>Returns the nodes in the network elements.                                           |
    | `int`                                                               | `getNumberOfLinks``()`<br>Returns the number of links in the network elements.                         |
    | `int`                                                               | `getNumberOfNodes``()`<br>Returns the number of nodes in the network elements.                         |
    | `boolean`                                                           | `hasLink``(long linkId)`<br>Checks whether the network elements contains the specified link.           |
    | `boolean`                                                           | `hasNode``(long nodeId)`<br>Checks whether the network elements contains the specified node.           |
    | `void`                                                              | `removeLink``(long linkId)`<br>Removes the specified link from the network elements.                   |
    | `void`                                                              | `removeNode``(long nodeId)`<br>Removes the specified node from the network elements.                   |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### Elements

          public Elements()

  <!-- -->

  - ### Method Detail

    - #### addLinkIntervals

          public void addLinkIntervals(NetworkBuffer.LinkIntervals linkIntervals)

    <!-- -->

    - #### addNode

          public void addNode(LogicalNode node)

      Adds a node to the network elements.
      Parameters:
      `node` -

    <!-- -->

    - #### getLinkIntervals

          public NetworkBuffer.LinkIntervals[] getLinkIntervals()

      Returns the link intervals in the network elements.
      Returns:

    <!-- -->

    - #### getLinkIntervals

          public NetworkBuffer.LinkIntervals getLinkIntervals(long linkId)

      Returns the link intervals of the specified link.
      Parameters:

      `linkId` - ID of the link

      Returns:

    <!-- -->

    - #### getNodes

          public LogicalNode[] getNodes()

      Returns the nodes in the network elements.
      Returns:

    <!-- -->

    - #### getNode

          public LogicalNode getNode(long nodeId)

      Returns the node object of the specified node.
      Parameters:

      `nodeId` - ID of the node

      Returns:

    <!-- -->

    - #### getNumberOfNodes

          public int getNumberOfNodes()

      Returns the number of nodes in the network elements.
      Returns:

    <!-- -->

    - #### getNumberOfLinks

          public int getNumberOfLinks()

      Returns the number of links in the network elements.
      Returns:

    <!-- -->

    - #### hasLink

          public boolean hasLink(long linkId)

      Checks whether the network elements contains the specified link.
      Parameters:

      `linkId` - ID of the link

      Returns:

    <!-- -->

    - #### hasNode

          public boolean hasNode(long nodeId)

      Checks whether the network elements contains the specified node.
      Parameters:

      `nodeId` - ID of the node

      Returns:

    <!-- -->

    - #### removeLink

          public void removeLink(long linkId)

      Removes the specified link from the network elements.
      Parameters:
      `linkId` - ID of the link

    <!-- -->

    - #### removeNode

          public void removeNode(long nodeId)

      Removes the specified node from the network elements.
      Parameters:
      `nodeId` - ID of the node

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NetworkBuffer.DoubleInterval.md)
- [Next Class](NetworkBuffer.LinkInterval.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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
