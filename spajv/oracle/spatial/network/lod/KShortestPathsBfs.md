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

- [Prev Class](KShortestPaths.md)
- [Next Class](LeveledNetworkCache.md)

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

## Class KShortestPathsBfs

- java.lang.Object

- - [oracle.spatial.network.lod.NetworkSearch](NetworkSearch.md)

  - - [oracle.spatial.network.lod.BreadthFirstSearch](BreadthFirstSearch.md)

    - - oracle.spatial.network.lod.KShortestPathsBfs

<!-- -->

- All Implemented Interfaces:
  [KShortestPaths](KShortestPaths.md), [ShortestPath](ShortestPath.md)

  ------------------------------------------------------------------------



      public class KShortestPathsBfs
      extends BreadthFirstSearch
      implements KShortestPaths

  BFS implementation of K-shortest paths search.
  Since:
  release specific (what release of product did this appear in)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                              |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `KShortestPathsBfs``()`                                                                                                                                                                                                                                                                                                  |
    | `KShortestPathsBfs``(`[`NetworkExplorer`](NetworkExplorer.md)` ne, `[`LinkCostCalculator`](LinkCostCalculator.md)`[] lccs, `[`NodeCostCalculator`](NodeCostCalculator.md)`[] nccs, `[`LinkLevelSelector`](LinkLevelSelector.md)` lls, double maxToMinBound, long timeout)`                                               |
    | `KShortestPathsBfs``(`[`NetworkExplorer`](NetworkExplorer.md)` ne, `[`LinkCostCalculator`](LinkCostCalculator.md)`[] lccs, `[`NodeCostCalculator`](NodeCostCalculator.md)`[] nccs, `[`LinkLevelSelector`](LinkLevelSelector.md)` lls, `[`PriorityQueue`](PriorityQueue.md)` queue, double maxToMinBound, long timeout)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                         | Method and Description                                                                                                                                                                                                                                                                                                     |
    |-------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `KShortestPathsBfs`                       | `clone``()`                                                                                                                                                                                                                                                                                                                |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]` | `kShortestPaths``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, `[`PointOnNet`](PointOnNet.md)`[] endPoints, int topK, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`PathFilter`](PathFilter.md)` pathFilter, int direction)`<br>Returns the k shortest paths from the start point to the end point. |

    - ### Methods inherited from class oracle.spatial.network.lod.[BreadthFirstSearch](BreadthFirstSearch.md)

      [`nearestFeatures`](BreadthFirstSearch.md)`, `[`nearestNeighbors`](BreadthFirstSearch.md)`, `[`nearestPoints`](BreadthFirstSearch.md)`, `[`networkBuffer`](BreadthFirstSearch.md)`, `[`shortestPath`](BreadthFirstSearch.md)`, `[`shortestPaths`](BreadthFirstSearch.md)`, `[`shortestPathsLight`](BreadthFirstSearch.md)`, `[`traceOut`](BreadthFirstSearch.md)`, `[`withinCost`](BreadthFirstSearch.md)`, `[`withinCostFeatures`](BreadthFirstSearch.md)`, `[`withinCostPoints`](BreadthFirstSearch.md)

    <!-- -->

    - ### Methods inherited from class oracle.spatial.network.lod.[NetworkSearch](NetworkSearch.md)

      [`findConnectedFeatures`](NetworkSearch.md)`, `[`getLinkCostCalculators`](NetworkSearch.md)`, `[`getLinkLevelSelector`](NetworkSearch.md)`, `[`getNodeCostCalculators`](NetworkSearch.md)`, `[`getXMLSchema`](NetworkSearch.md)`, `[`init`](NetworkSearch.md)`, `[`initSearch`](NetworkSearch.md)`, `[`preparePathFeature`](NetworkSearch.md)`, `[`reset`](NetworkSearch.md)`, `[`setInitialAnalysisInfo`](NetworkSearch.md)`, `[`setLinkCostCalculators`](NetworkSearch.md)`, `[`setLinkLevelSelector`](NetworkSearch.md)`, `[`setNetworkAnalyst`](NetworkSearch.md)`, `[`setNetworkExplorer`](NetworkSearch.md)`, `[`setNodeCostCalculators`](NetworkSearch.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.lod.[KShortestPaths](KShortestPaths.md)

      [`setLinkLevelSelector`](KShortestPaths.md)`, `[`setNetworkAnalyst`](KShortestPaths.md)

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.lod.[ShortestPath](ShortestPath.md)

      [`getLinkCostCalculators`](ShortestPath.md)`, `[`getLinkLevelSelector`](ShortestPath.md)`, `[`getNodeCostCalculators`](ShortestPath.md)`, `[`setInitialAnalysisInfo`](ShortestPath.md)`, `[`setLinkCostCalculators`](ShortestPath.md)`, `[`setLinkLevelSelector`](ShortestPath.md)`, `[`setNetworkAnalyst`](ShortestPath.md)`, `[`setNodeCostCalculators`](ShortestPath.md)

<!-- -->

- - ### Constructor Detail

    - #### KShortestPathsBfs

          public KShortestPathsBfs()

    <!-- -->

    - #### KShortestPathsBfs

          public KShortestPathsBfs(NetworkExplorer ne,
                                   LinkCostCalculator[] lccs,
                                   NodeCostCalculator[] nccs,
                                   LinkLevelSelector lls,
                                   PriorityQueue queue,
                                   double maxToMinBound,
                                   long timeout)

    <!-- -->

    - #### KShortestPathsBfs

          public KShortestPathsBfs(NetworkExplorer ne,
                                   LinkCostCalculator[] lccs,
                                   NodeCostCalculator[] nccs,
                                   LinkLevelSelector lls,
                                   double maxToMinBound,
                                   long timeout)

  <!-- -->

  - ### Method Detail

    - #### clone

          public KShortestPathsBfs clone()

      Specified by:
      [`clone`](ShortestPath.md) in interface [`ShortestPath`](ShortestPath.md)

      Overrides:
      [`clone`](BreadthFirstSearch.md) in class [`BreadthFirstSearch`](BreadthFirstSearch.md)

    <!-- -->

    - #### kShortestPaths

          public LogicalSubPath[] kShortestPaths(PointOnNet[] startPoints,
                                                 PointOnNet[] endPoints,
                                                 int topK,
                                                 LODNetworkConstraint constraint,
                                                 PathFilter pathFilter,
                                                 int direction)
                                          throws LODNetworkException

      Description copied from interface: [`KShortestPaths`](KShortestPaths.md)
      Returns the k shortest paths from the start point to the end point.
      Specified by:
      [`kShortestPaths`](KShortestPaths.md) in interface [`KShortestPaths`](KShortestPaths.md)

      Parameters:
      `startPoints` - candidate start points

      `endPoints` - candidate end points

      `topK` - max number of paths to be returned

      `constraint` - network constraint

      `direction` - NetworkExplorer.DIRECTION_FORWARD or NetworkExplorer.DIRECTION_BACKWARD

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

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

- [Prev Class](KShortestPaths.md)
- [Next Class](LeveledNetworkCache.md)

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
