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

- [Prev Class](LogicalPartitionImpl.md)
- [Next Class](LogicalSubNetwork.md)

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

## Interface LogicalPath

- All Superinterfaces:
  [LogicalLightPath](LogicalLightPath.md)

  <!-- -->

  All Known Subinterfaces:
  [SpatialPath](SpatialPath.md)

  ------------------------------------------------------------------------



      public interface LogicalPath
      extends LogicalLightPath

  A LogicalPath is defined by an array of link IDs, array of node IDs, and the costs for traversing through this path. The cost of a path is the sum of the costs of the the links and nodes on the path, excluding that of the end node. The costs of the links and nodes are defined by LinkCostCalculator and NodeCostCalculator.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                               | Method and Description                                                                                                                                                                                                 |
    |-------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `LogicalPath`                                   | `append``(LogicalPath path)`<br>Appends a path to the end this path.                                                                                                                                                   |
    | `LogicalPath`                                   | `append``(LogicalPath path, double connectorNodeCost)`<br>Deprecated. <br>use append(LogicalPath path);                                                                                                                |
    | `LogicalPath`                                   | `append``(long nextLinkId, double[] nextLinkCosts, long nextNodeId, double[] connectorNodeCosts)`<br>Append a link to this path.                                                                                       |
    | `LogicalPath`                                   | `append``(long nextLinkId, double nextLinkCost, long nextNodeId, double connectorNodeCosts)`<br>Deprecated. <br>use append(long nextLinkId, double\[\] nextLinkCosts, long nextNodeId, double\[\] connectorNodeCosts); |
    | `java.lang.Object`                              | `clone``()`<br>Support cloneable                                                                                                                                                                                       |
    | [`CategorizedUserData`](CategorizedUserData.md) | `getCategorizedUserData``()`<br>Returns categorized user data.                                                                                                                                                         |
    | `double[]`                                      | `getCostsAtNode``(int nodeIndex)`<br>Returns the costs to pass through the input node.                                                                                                                                 |
    | `double[][]`                                    | `getCostsAtNodes``()`<br>Returns an array of costs at each individual nodes on the path.                                                                                                                               |
    | `double[]`                                      | `getCostsToNode``(int nodeIndex)`<br>Returns the cumulative costs from the start node to the input node.                                                                                                               |
    | `double[][]`                                    | `getCostsToNodes``()`<br>Returns an array of cumulative costs from the start node to the nodes on the path.                                                                                                            |
    | `long[]`                                        | `getLinkIds``()`<br>Returns the array of link IDs on this path.                                                                                                                                                        |
    | `long[]`                                        | `getNodeIds``()`<br>Returns the array of node IDs on this path.                                                                                                                                                        |
    | [`UserData`](UserData.md)                       | `getUserData``(int category)`<br>Returns user data for the specified category.                                                                                                                                         |
    | `int`                                           | `indexOfLink``(long linkId)`<br>Returns the index of the specified link in this path.                                                                                                                                  |
    | `int`                                           | `indexOfNode``(long nodeId)`<br>Returns the index of the specified node in this path.                                                                                                                                  |
    | `boolean`                                       | `isSimple``()`<br>Checks whether this path is simple or not.                                                                                                                                                           |
    | `LogicalPath`                                   | `prepend``(LogicalPath path)`<br>Appends a path to the beginning of this path.                                                                                                                                         |
    | `LogicalPath`                                   | `prepend``(LogicalPath path, double connectorNodeCost)`<br>Deprecated. <br>use prepend(LogicalPath path);                                                                                                              |
    | `LogicalPath`                                   | `prepend``(long prevLinkId, double[] prevLinkCosts, long prevNodeId, double[] prevNodeCosts)`<br>Prepend a link to this path.                                                                                          |
    | `LogicalPath`                                   | `prepend``(long prevLinkId, double prevLinkCost, long prevNodeId, double prevNodeCost)`<br>Deprecated. <br>use prepend(long prevLinkId, double\[\] prevLinkCosts, long prevNodeId, double\[\] connectorNodeCosts);     |
    | `void`                                          | `setCategorizedUserData``(`[`CategorizedUserData`](CategorizedUserData.md)` userData)`<br>Sets categorized user data.                                                                                                  |
    | `void`                                          | `setUserData``(int category, `[`UserData`](UserData.md)` userData)`<br>Sets user data for the specified category.                                                                                                      |

    - ### Methods inherited from interface oracle.spatial.network.lod.[LogicalLightPath](LogicalLightPath.md)

      [`getCost`](LogicalLightPath.md)`, `[`getCosts`](LogicalLightPath.md)`, `[`getEndNodeId`](LogicalLightPath.md)`, `[`getFirstLinkId`](LogicalLightPath.md)`, `[`getLastLinkId`](LogicalLightPath.md)`, `[`getNumberOfLinks`](LogicalLightPath.md)`, `[`getNumberOfNodes`](LogicalLightPath.md)`, `[`getStartNodeId`](LogicalLightPath.md)`, `[`isReverse`](LogicalLightPath.md)`, `[`reverse`](LogicalLightPath.md)`, `[`setCosts`](LogicalLightPath.md)

<!-- -->

- - ### Method Detail

    - #### getLinkIds

          long[] getLinkIds()

      Returns the array of link IDs on this path.
      Returns:
      array of link IDs

    <!-- -->

    - #### getNodeIds

          long[] getNodeIds()

      Returns the array of node IDs on this path.
      Returns:
      array of node IDs

    <!-- -->

    - #### isSimple

          boolean isSimple()

      Checks whether this path is simple or not. A path is simple if no node is visited twice on this path, i.e., no loop exists on this path.
      Returns:
      true, if the path is simple; false, otherwise.

    <!-- -->

    - #### append

          LogicalPath append(long nextLinkId,
                             double nextLinkCost,
                             long nextNodeId,
                             double connectorNodeCosts)
                      throws LODNetworkException

      Deprecated. use append(long nextLinkId, double\[\] nextLinkCosts, long nextNodeId, double\[\] connectorNodeCosts);
      Append a link to this path.
      Parameters:
      `nextLinkId` - ID of the next link

      `nextLinkCost` - cost of the next link

      `nextNodeId` - ID of the next node

      `connectorNodeCosts` - cost of the connector node

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### append

          LogicalPath append(long nextLinkId,
                             double[] nextLinkCosts,
                             long nextNodeId,
                             double[] connectorNodeCosts)
                      throws LODNetworkException

      Append a link to this path.
      Parameters:
      `nextLinkId` - ID of the next link

      `nextLinkCosts` - costs of the next link

      `nextNodeId` - ID of the next node

      `connectorNodeCosts` - costs of the connector node

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### prepend

          LogicalPath prepend(long prevLinkId,
                              double prevLinkCost,
                              long prevNodeId,
                              double prevNodeCost)
                       throws LODNetworkException

      Deprecated. use prepend(long prevLinkId, double\[\] prevLinkCosts, long prevNodeId, double\[\] connectorNodeCosts);
      Prepend a link to this path.
      Parameters:
      `prevLinkId` - ID of the previous link

      `prevLinkCost` - cost of the previous link

      `prevNodeId` - ID of the previous node

      `prevNodeCost` - costs of the node to be prepended

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### prepend

          LogicalPath prepend(long prevLinkId,
                              double[] prevLinkCosts,
                              long prevNodeId,
                              double[] prevNodeCosts)
                       throws LODNetworkException

      Prepend a link to this path.
      Parameters:
      `prevLinkId` - ID of the previous link

      `prevLinkCosts` - costs of the previous link

      `prevNodeId` - ID of the previous node

      `prevNodeCosts` - costs of the node to be prepended

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### append

          LogicalPath append(LogicalPath path,
                             double connectorNodeCost)
                      throws LODNetworkException

      Deprecated. use append(LogicalPath path);
      Appends a path to the end this path.
      Parameters:
      `path` - path to append to the end

      `connectorNodeCost` - cost of the connector node

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### append

          LogicalPath append(LogicalPath path)
                      throws LODNetworkException

      Appends a path to the end this path.
      Parameters:
      `path` - path to append to the end

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### prepend

          LogicalPath prepend(LogicalPath path,
                              double connectorNodeCost)
                       throws LODNetworkException

      Deprecated. use prepend(LogicalPath path);
      Appends a path to the beginning of this path.
      Parameters:
      `path` - path to append at the beginning

      `connectorNodeCost` - cost of the connector node

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### prepend

          LogicalPath prepend(LogicalPath path)
                       throws LODNetworkException

      Appends a path to the beginning of this path.
      Parameters:
      `path` - path to append at the beginning

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### indexOfNode

          int indexOfNode(long nodeId)

      Returns the index of the specified node in this path.
      Parameters:
      `nodeId` - node id

      Returns:
      the index of the node, if the path contains the node; -1, otherwise.

    <!-- -->

    - #### indexOfLink

          int indexOfLink(long linkId)

      Returns the index of the specified link in this path.
      Parameters:
      `linkId` - link id

      Returns:
      the index of the link, if the path contains the link; -1, otherwise.

    <!-- -->

    - #### getCostsToNode

          double[] getCostsToNode(int nodeIndex)

      Returns the cumulative costs from the start node to the input node.
      Parameters:

      `nodeIndex` - index of node in the reference path

      Returns:

    <!-- -->

    - #### getCostsAtNode

          double[] getCostsAtNode(int nodeIndex)

      Returns the costs to pass through the input node.
      Parameters:

      `nodeIndex` -

      Returns:

    <!-- -->

    - #### getCostsToNodes

          double[][] getCostsToNodes()

      Returns an array of cumulative costs from the start node to the nodes on the path.
      Returns:

    <!-- -->

    - #### getCostsAtNodes

          double[][] getCostsAtNodes()

      Returns an array of costs at each individual nodes on the path.
      Returns:

    <!-- -->

    - #### getCategorizedUserData

          CategorizedUserData getCategorizedUserData()

      Returns categorized user data.
      Returns:

    <!-- -->

    - #### setCategorizedUserData

          void setCategorizedUserData(CategorizedUserData userData)

      Sets categorized user data.
      Parameters:
      `userData` -

    <!-- -->

    - #### getUserData

          UserData getUserData(int category)

      Returns user data for the specified category.
      Returns:

    <!-- -->

    - #### setUserData

          void setUserData(int category,
                           UserData userData)

      Sets user data for the specified category.
      Parameters:
      `userData` -

    <!-- -->

    - #### clone

          java.lang.Object clone()
                          throws java.lang.CloneNotSupportedException

      Support cloneable
      Returns:
      cloned object

      Throws:
      `java.lang.CloneNotSupportedException`

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

- [Prev Class](LogicalPartitionImpl.md)
- [Next Class](LogicalSubNetwork.md)

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
