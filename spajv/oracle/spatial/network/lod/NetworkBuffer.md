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

- [Prev Class](NetworkAnalyst.md)
- [Next Class](NetworkBuffer.DoubleInterval.md)

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

## Class NetworkBuffer

- java.lang.Object

- - oracle.spatial.network.lod.NetworkBuffer

<!-- -->

-

  ------------------------------------------------------------------------



      public class NetworkBuffer
      extends java.lang.Object

  A NetworkBuffer is defined by central points and the set of nodes and link intervals within certain radius from the cental points. A NetworkBuffer can return the minimum cost from a central point to any node or link interval covered by this NetworkBuffer.
  Since:
  Oracle Database 11g Release 2 (11.2)

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Class and Description                                                                                                                                                               |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static class `   | [`NetworkBuffer.DoubleInterval`](NetworkBuffer.DoubleInterval.md)<br>This class defines a double interval.                                                                          |
    | `static class `   | [`NetworkBuffer.Elements`](NetworkBuffer.Elements.md)<br>This class contains elements in a network buffer.                                                                          |
    | `static class `   | [`NetworkBuffer.LinkInterval`](NetworkBuffer.LinkInterval.md)                                                                                                                       |
    | `static class `   | [`NetworkBuffer.LinkIntervals`](NetworkBuffer.LinkIntervals.md)<br>An instance of this class contains a LogicalLink object and a list of intervals associated with the link object. |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                              |
    |------------------------------------------------------------------------------------------|
    | `NetworkBuffer``(double radius, int direction)`<br>Constructs a network buffer instance. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                     | Method and Description                                                                                                                                                     |
    |-----------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                | `addCentralPoint``(`[`PointOnNet`](PointOnNet.md)` centralPoint)`<br>Add a central point to network buffer.                                                                |
    | `void`                                                                | `addNode``(`[`LogicalNode`](LogicalNode.md)` node, double[] costs)`<br>Adds a node to the network buffer.                                                                  |
    | [`PointOnNet`](PointOnNet.md)`[]`                                     | `getCentralPoints``()`<br>Returns the central points.                                                                                                                      |
    | `double[]`                                                            | `getCosts``(`[`PointOnNet`](PointOnNet.md)` point)`<br>Returns the costs from a buffer center to the input point.                                                          |
    | `int`                                                                 | `getDirection``()`<br>Returns the direction (forward or backward) of the network buffer.                                                                                   |
    | [`NetworkBuffer.Elements`](NetworkBuffer.Elements.md)                 | `getElements``()`<br>Returns the elements in this network buffer.                                                                                                          |
    | `double[]`                                                            | `getLinkEnteringCosts``(long linkId, boolean isForward)`<br>Returns the cost before entering the link.                                                                     |
    | [`NetworkBuffer.DoubleInterval`](NetworkBuffer.DoubleInterval.md)`[]` | `getLinkIntervalCosts``(long linkId, `[`NetworkBuffer.DoubleInterval`](NetworkBuffer.DoubleInterval.md)` interval)`<br>Returns the cost range to reach the input interval. |
    | `double[]`                                                            | `getNodeCosts``(long nodeId)`<br>Returns the minimum costs to reach the node from a central point.                                                                         |
    | `double`                                                              | `getRadius``()`<br>Returns the radius (size) of the network buffer.                                                                                                        |
    | `boolean`                                                             | `isCovered``(`[`PointOnNet`](PointOnNet.md)` point)`                                                                                                                       |
    | `void`                                                                | `removeCentralPoint``(`[`PointOnNet`](PointOnNet.md)` centralPoint)`<br>Removes a central point.                                                                           |
    | `void`                                                                | `removeLink``(long linkId)`<br>Removes the specified link and all associated intervals from the network buffer.                                                            |
    | `void`                                                                | `removeNode``(long nodeId)`<br>Removes the specified node from the network buffer.                                                                                         |
    | `NetworkBuffer`                                                       | `subSet``(double cost)`<br>Computes the subset of the network buffer.                                                                                                      |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NetworkBuffer

          public NetworkBuffer(double radius,
                               int direction)

      Constructs a network buffer instance.

  <!-- -->

  - ### Method Detail

    - #### getRadius

          public double getRadius()

      Returns the radius (size) of the network buffer.
      Returns:

    <!-- -->

    - #### getDirection

          public int getDirection()

      Returns the direction (forward or backward) of the network buffer.
      Returns:

    <!-- -->

    - #### addCentralPoint

          public void addCentralPoint(PointOnNet centralPoint)

      Add a central point to network buffer. Costs of central points are zero.
      Parameters:
      `centralPoint` - zero cost point

    <!-- -->

    - #### getCentralPoints

          public PointOnNet[] getCentralPoints()

      Returns the central points.
      Returns:
      central points

    <!-- -->

    - #### removeCentralPoint

          public void removeCentralPoint(PointOnNet centralPoint)

      Removes a central point.
      Parameters:
      `centralPoint` - central point to be removed

    <!-- -->

    - #### isCovered

          public boolean isCovered(PointOnNet point)

    <!-- -->

    - #### getCosts

          public double[] getCosts(PointOnNet point)

      Returns the costs from a buffer center to the input point. The array of costs corresponds to the array of link and node cost calculators passed to network buffer analysis. Returns null if the point in not covered by this network buffer.
      Parameters:

      `point` -

      Returns:

    <!-- -->

    - #### getLinkIntervalCosts

          public NetworkBuffer.DoubleInterval[] getLinkIntervalCosts(long linkId,
                                                                     NetworkBuffer.DoubleInterval interval)

      Returns the cost range to reach the input interval. If the network buffer does not cover any portion of the link in the direction the input interval indicated, then this method returns null.
      Parameters:
      `interval` - start/end percentage on the link

      Returns:
      costs range to reach the input interval\`

    <!-- -->

    - #### getLinkEnteringCosts

          public double[] getLinkEnteringCosts(long linkId,
                                               boolean isForward)

      Returns the cost before entering the link.
      Parameters:
      `isForward` - true if the travel direction is from the start node to the end node; false other wise.

      Returns:
      costs range to reach the input interval\`

    <!-- -->

    - #### addNode

          public void addNode(LogicalNode node,
                              double[] costs)

      Adds a node to the network buffer.
      Parameters:
      `node` - node

      `costs` - minimum costs to reach the node from a central point

    <!-- -->

    - #### getNodeCosts

          public double[] getNodeCosts(long nodeId)

      Returns the minimum costs to reach the node from a central point.
      Parameters:
      `nodeId` - ID of the node

      Returns:
      costs to reach the node

    <!-- -->

    - #### getElements

          public NetworkBuffer.Elements getElements()

      Returns the elements in this network buffer.
      Returns:
      elements in the network buffer

    <!-- -->

    - #### removeLink

          public void removeLink(long linkId)

      Removes the specified link and all associated intervals from the network buffer.
      Parameters:
      `linkId` - ID of the link

    <!-- -->

    - #### removeNode

          public void removeNode(long nodeId)

      Removes the specified node from the network buffer.
      Parameters:
      `nodeId` - ID of the node

    <!-- -->

    - #### subSet

          public NetworkBuffer subSet(double cost)

      Computes the subset of the network buffer.
      Parameters:
      `cost` - cost of the subset

      Returns:
      a network buffer, which is a subset of this network buffer

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

- [Prev Class](NetworkAnalyst.md)
- [Next Class](NetworkBuffer.DoubleInterval.md)

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
