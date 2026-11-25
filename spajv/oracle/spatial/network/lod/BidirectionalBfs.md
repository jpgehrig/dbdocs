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

- [Prev Class](AStar.md)
- [Next Class](BidirectionalDijkstra.md)

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

## Class BidirectionalBfs

- java.lang.Object

- - oracle.spatial.network.lod.BidirectionalBfs

<!-- -->

- All Implemented Interfaces:
  [ShortestPath](ShortestPath.md)

  <!-- -->

  Direct Known Subclasses:
  [BidirectionalDijkstra](BidirectionalDijkstra.md)

  ------------------------------------------------------------------------



      public class BidirectionalBfs
      extends java.lang.Object
      implements ShortestPath

  Since:
  release specific (what release of product did this appear in)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                          |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `BidirectionalBfs``(`[`BreadthFirstSearch`](BreadthFirstSearch.md)` forwardBfs, `[`BreadthFirstSearch`](BreadthFirstSearch.md)` backwardBfs)`                                                                                                                                                                                        |
    | `BidirectionalBfs``(`[`NetworkExplorer`](NetworkExplorer.md)` ne, `[`LinkCostCalculator`](LinkCostCalculator.md)`[] lccs, `[`NodeCostCalculator`](NodeCostCalculator.md)`[] nccs, `[`LinkLevelSelector`](LinkLevelSelector.md)` forwardLinkLevelSelector, `[`LinkLevelSelector`](LinkLevelSelector.md)` backwardLinkLevelSelector)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                 | Method and Description                                                                                                                                                                                                                                                                                                                            |
    |---------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`ShortestPath`](ShortestPath.md)                 | `clone``()`                                                                                                                                                                                                                                                                                                                                       |
    | [`LinkCostCalculator`](LinkCostCalculator.md)`[]` | `getLinkCostCalculators``()`<br>Returns the link cost calculators.                                                                                                                                                                                                                                                                                |
    | [`LinkLevelSelector`](LinkLevelSelector.md)       | `getLinkLevelSelector``()`<br>Returns the link level selector.                                                                                                                                                                                                                                                                                    |
    | [`NodeCostCalculator`](NodeCostCalculator.md)`[]` | `getNodeCostCalculators``()`<br>Returns the node cost calculators.                                                                                                                                                                                                                                                                                |
    | `void`                                            | `setInitialAnalysisInfo``(`[`LODAnalysisInfo`](LODAnalysisInfo.md)` analysisInfo)`<br>Sets the initial analysis info.                                                                                                                                                                                                                             |
    | `void`                                            | `setLinkCostCalculators``(`[`LinkCostCalculator`](LinkCostCalculator.md)`[] lccs)`<br>Sets the link cost calculators.                                                                                                                                                                                                                             |
    | `void`                                            | `setLinkLevelSelector``(`[`LinkLevelSelector`](LinkLevelSelector.md)` lls)`<br>Sets the link level selector.                                                                                                                                                                                                                                      |
    | `void`                                            | `setNetworkAnalyst``(`[`NetworkAnalyst`](NetworkAnalyst.md)` analyst)`<br>This method allows caller to pass the network analyst object to this shortest path algorithm implementation, so that the algorithm can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst. |
    | `void`                                            | `setNodeCostCalculators``(`[`NodeCostCalculator`](NodeCostCalculator.md)`[] nccs)`<br>Sets the node cost calculators.                                                                                                                                                                                                                             |
    | [`LogicalSubPath`](LogicalSubPath.md)             | `shortestPath``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, `[`PointOnNet`](PointOnNet.md)`[] endPoints, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, int direction)`<br>Returns the shortest path between a set of candidate start points and a set of end points.                                                         |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### BidirectionalBfs

          public BidirectionalBfs(NetworkExplorer ne,
                                  LinkCostCalculator[] lccs,
                                  NodeCostCalculator[] nccs,
                                  LinkLevelSelector forwardLinkLevelSelector,
                                  LinkLevelSelector backwardLinkLevelSelector)

    <!-- -->

    - #### BidirectionalBfs

          public BidirectionalBfs(BreadthFirstSearch forwardBfs,
                                  BreadthFirstSearch backwardBfs)

  <!-- -->

  - ### Method Detail

    - #### shortestPath

          public LogicalSubPath shortestPath(PointOnNet[] startPoints,
                                             PointOnNet[] endPoints,
                                             LODNetworkConstraint constraint,
                                             int direction)
                                      throws LODNetworkException

      Description copied from interface: [`ShortestPath`](ShortestPath.md)
      Returns the shortest path between a set of candidate start points and a set of end points.
      Specified by:
      [`shortestPath`](ShortestPath.md) in interface [`ShortestPath`](ShortestPath.md)

      Parameters:
      `startPoints` - start candidates

      `endPoints` - end candidates

      `constraint` - network constraint

      `direction` - NetworkExplorer.DIRECTION_FORWARD or NetworkExplorer.DIRECTION_BACKWARD

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### setInitialAnalysisInfo

          public void setInitialAnalysisInfo(LODAnalysisInfo analysisInfo)

      Description copied from interface: [`ShortestPath`](ShortestPath.md)
      Sets the initial analysis info. This method allows analysis info to be passed to subsequent analysis.
      Specified by:
      [`setInitialAnalysisInfo`](ShortestPath.md) in interface [`ShortestPath`](ShortestPath.md)

      Parameters:
      `analysisInfo` - analysis information

    <!-- -->

    - #### getLinkLevelSelector

          public LinkLevelSelector getLinkLevelSelector()

      Description copied from interface: [`ShortestPath`](ShortestPath.md)
      Returns the link level selector.
      Specified by:

      [`getLinkLevelSelector`](ShortestPath.md) in interface [`ShortestPath`](ShortestPath.md)

      Returns:

    <!-- -->

    - #### setLinkLevelSelector

          public void setLinkLevelSelector(LinkLevelSelector lls)

      Description copied from interface: [`ShortestPath`](ShortestPath.md)
      Sets the link level selector.
      Specified by:
      [`setLinkLevelSelector`](ShortestPath.md) in interface [`ShortestPath`](ShortestPath.md)

      Parameters:
      `lls` - link level selector

    <!-- -->

    - #### getLinkCostCalculators

          public LinkCostCalculator[] getLinkCostCalculators()

      Description copied from interface: [`ShortestPath`](ShortestPath.md)
      Returns the link cost calculators.
      Specified by:

      [`getLinkCostCalculators`](ShortestPath.md) in interface [`ShortestPath`](ShortestPath.md)

      Returns:

    <!-- -->

    - #### setLinkCostCalculators

          public void setLinkCostCalculators(LinkCostCalculator[] lccs)

      Description copied from interface: [`ShortestPath`](ShortestPath.md)
      Sets the link cost calculators.
      Specified by:
      [`setLinkCostCalculators`](ShortestPath.md) in interface [`ShortestPath`](ShortestPath.md)

    <!-- -->

    - #### getNodeCostCalculators

          public NodeCostCalculator[] getNodeCostCalculators()

      Description copied from interface: [`ShortestPath`](ShortestPath.md)
      Returns the node cost calculators.
      Specified by:

      [`getNodeCostCalculators`](ShortestPath.md) in interface [`ShortestPath`](ShortestPath.md)

      Returns:

    <!-- -->

    - #### setNodeCostCalculators

          public void setNodeCostCalculators(NodeCostCalculator[] nccs)

      Description copied from interface: [`ShortestPath`](ShortestPath.md)
      Sets the node cost calculators.
      Specified by:
      [`setNodeCostCalculators`](ShortestPath.md) in interface [`ShortestPath`](ShortestPath.md)

    <!-- -->

    - #### setNetworkAnalyst

          public void setNetworkAnalyst(NetworkAnalyst analyst)

      Description copied from interface: [`ShortestPath`](ShortestPath.md)
      This method allows caller to pass the network analyst object to this shortest path algorithm implementation, so that the algorithm can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst. If network analyst is not needed by the shortest path algorithm, the algorithm can choose to do nothing with this method.
      Specified by:
      [`setNetworkAnalyst`](ShortestPath.md) in interface [`ShortestPath`](ShortestPath.md)

    <!-- -->

    - #### clone

          public ShortestPath clone()

      Specified by:
      [`clone`](ShortestPath.md) in interface [`ShortestPath`](ShortestPath.md)

      Overrides:
      `clone` in class `java.lang.Object`

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

- [Prev Class](AStar.md)
- [Next Class](BidirectionalDijkstra.md)

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
