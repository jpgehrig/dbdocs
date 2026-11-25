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

- [Prev Class](BinaryHeap.md)
- [Next Class](CachedNetworkIO.md)

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

## Class BreadthFirstSearch

- java.lang.Object

- - [oracle.spatial.network.lod.NetworkSearch](NetworkSearch.md)

  - - oracle.spatial.network.lod.BreadthFirstSearch

<!-- -->

- All Implemented Interfaces:
  [ShortestPath](ShortestPath.md)

  <!-- -->

  Direct Known Subclasses:
  [AStar](AStar.md), [Dijkstra](Dijkstra.md), [KShortestPathsBfs](KShortestPathsBfs.md)

  ------------------------------------------------------------------------



      public class BreadthFirstSearch
      extends NetworkSearch
      implements ShortestPath

  Network search algorithm that explores the network in breadth first manner.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                           |
    |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `BreadthFirstSearch``()`                                                                                                                                                                                                                                                              |
    | `BreadthFirstSearch``(`[`NetworkExplorer`](NetworkExplorer.md)` ne, `[`LinkCostCalculator`](LinkCostCalculator.md)`[] lccs, `[`NodeCostCalculator`](NodeCostCalculator.md)`[] nccs, `[`LinkLevelSelector`](LinkLevelSelector.md)` lls)`                                               |
    | `BreadthFirstSearch``(`[`NetworkExplorer`](NetworkExplorer.md)` ne, `[`LinkCostCalculator`](LinkCostCalculator.md)`[] lccs, `[`NodeCostCalculator`](NodeCostCalculator.md)`[] nccs, `[`LinkLevelSelector`](LinkLevelSelector.md)` lls, `[`PriorityQueue`](PriorityQueue.md)` queue)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                   | Method and Description                                                                                                                                                                                                                                                                                                |
    |-----------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `BreadthFirstSearch`                                | `clone``()`                                                                                                                                                                                                                                                                                                           |
    | [`FeaturePath`](FeaturePath.md)`[]`                 | `nearestFeatures``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, int numberOfFeatures, int[] featureLayers, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`FeatureFilter`](FeatureFilter.md)` featureFilter, int direction)`                                                                     |
    | [`LogicalLightSubPath`](LogicalLightSubPath.md)`[]` | `nearestNeighbors``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, int numberOfNeighbors, int direction, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNode, boolean returnFullPath)`                                                                         |
    | [`PathToPoint`](PathToPoint.md)`[]`                 | `nearestPoints``(`[`PointOnNet`](PointOnNet.md)`[] startPoint, `[`PointOnNet`](PointOnNet.md)`[][] endPoints, int k, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, int direction, boolean returnFullPath)`                                                                                          |
    | [`NetworkBuffer`](NetworkBuffer.md)                 | `networkBuffer``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, double cost, int direction, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint)`<br>Returns network buffer within the specified cost.                                                                                                     |
    | [`LogicalSubPath`](LogicalSubPath.md)               | `shortestPath``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, `[`PointOnNet`](PointOnNet.md)`[] endPoints, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, int direction)`<br>Returns the shortest path between a set of candidate start points and a set of end points.                             |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`           | `shortestPaths``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, `[`PointOnNet`](PointOnNet.md)`[][] endPoints, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, int direction)`                                                                                                                        |
    | [`LogicalLightSubPath`](LogicalLightSubPath.md)`[]` | `shortestPathsLight``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, `[`PointOnNet`](PointOnNet.md)`[][] endPoints, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, int direction)`                                                                                                                   |
    | [`LogicalLightSubPath`](LogicalLightSubPath.md)`[]` | `traceOut``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, double cost, int direction, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNode, boolean returnFullPath, boolean returnBoundaryPointsOnly)`                                                         |
    | [`LogicalLightSubPath`](LogicalLightSubPath.md)`[]` | `withinCost``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, double cost, int direction, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNode, boolean returnFullPath, boolean returnBoundaryPointsOnly)`                                                       |
    | [`FeaturePath`](FeaturePath.md)`[]`                 | `withinCostFeatures``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, double cost, int[] featureLayers, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`FeatureFilter`](FeatureFilter.md)` featureFilter, int direction)`<br>Returns the features and the paths to/from them within the given cost. |
    | [`PathToPoint`](PathToPoint.md)`[]`                 | `withinCostPoints``(`[`PointOnNet`](PointOnNet.md)`[] startPoint, `[`PointOnNet`](PointOnNet.md)`[][] endPoints, double maxCost, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, int direction, boolean returnFullPath)`                                                                              |

    - ### Methods inherited from class oracle.spatial.network.lod.[NetworkSearch](NetworkSearch.md)

      [`findConnectedFeatures`](NetworkSearch.md)`, `[`getLinkCostCalculators`](NetworkSearch.md)`, `[`getLinkLevelSelector`](NetworkSearch.md)`, `[`getNodeCostCalculators`](NetworkSearch.md)`, `[`getXMLSchema`](NetworkSearch.md)`, `[`init`](NetworkSearch.md)`, `[`initSearch`](NetworkSearch.md)`, `[`preparePathFeature`](NetworkSearch.md)`, `[`reset`](NetworkSearch.md)`, `[`setInitialAnalysisInfo`](NetworkSearch.md)`, `[`setLinkCostCalculators`](NetworkSearch.md)`, `[`setLinkLevelSelector`](NetworkSearch.md)`, `[`setNetworkAnalyst`](NetworkSearch.md)`, `[`setNetworkExplorer`](NetworkSearch.md)`, `[`setNodeCostCalculators`](NetworkSearch.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.lod.[ShortestPath](ShortestPath.md)

      [`getLinkCostCalculators`](ShortestPath.md)`, `[`getLinkLevelSelector`](ShortestPath.md)`, `[`getNodeCostCalculators`](ShortestPath.md)`, `[`setInitialAnalysisInfo`](ShortestPath.md)`, `[`setLinkCostCalculators`](ShortestPath.md)`, `[`setLinkLevelSelector`](ShortestPath.md)`, `[`setNetworkAnalyst`](ShortestPath.md)`, `[`setNodeCostCalculators`](ShortestPath.md)

<!-- -->

- - ### Constructor Detail

    - #### BreadthFirstSearch

          public BreadthFirstSearch()

    <!-- -->

    - #### BreadthFirstSearch

          public BreadthFirstSearch(NetworkExplorer ne,
                                    LinkCostCalculator[] lccs,
                                    NodeCostCalculator[] nccs,
                                    LinkLevelSelector lls,
                                    PriorityQueue queue)

    <!-- -->

    - #### BreadthFirstSearch

          public BreadthFirstSearch(NetworkExplorer ne,
                                    LinkCostCalculator[] lccs,
                                    NodeCostCalculator[] nccs,
                                    LinkLevelSelector lls)

  <!-- -->

  - ### Method Detail

    - #### clone

          public BreadthFirstSearch clone()

      Specified by:
      [`clone`](ShortestPath.md) in interface [`ShortestPath`](ShortestPath.md)

      Overrides:
      `clone` in class `java.lang.Object`

    <!-- -->

    - #### nearestNeighbors

          public LogicalLightSubPath[] nearestNeighbors(PointOnNet[] startPoints,
                                                        int numberOfNeighbors,
                                                        int direction,
                                                        LODNetworkConstraint constraint,
                                                        LODGoalNode goalNode,
                                                        boolean returnFullPath)
                                                 throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### nearestPoints

          public PathToPoint[] nearestPoints(PointOnNet[] startPoint,
                                             PointOnNet[][] endPoints,
                                             int k,
                                             LODNetworkConstraint constraint,
                                             int direction,
                                             boolean returnFullPath)
                                      throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### withinCostPoints

          public PathToPoint[] withinCostPoints(PointOnNet[] startPoint,
                                                PointOnNet[][] endPoints,
                                                double maxCost,
                                                LODNetworkConstraint constraint,
                                                int direction,
                                                boolean returnFullPath)
                                         throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### withinCost

          public LogicalLightSubPath[] withinCost(PointOnNet[] startPoints,
                                                  double cost,
                                                  int direction,
                                                  LODNetworkConstraint constraint,
                                                  LODGoalNode goalNode,
                                                  boolean returnFullPath,
                                                  boolean returnBoundaryPointsOnly)
                                           throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### traceOut

          public LogicalLightSubPath[] traceOut(PointOnNet[] startPoints,
                                                double cost,
                                                int direction,
                                                LODNetworkConstraint constraint,
                                                LODGoalNode goalNode,
                                                boolean returnFullPath,
                                                boolean returnBoundaryPointsOnly)
                                         throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### networkBuffer

          public NetworkBuffer networkBuffer(PointOnNet[] startPoints,
                                             double cost,
                                             int direction,
                                             LODNetworkConstraint constraint)
                                      throws LODNetworkException

      Returns network buffer within the specified cost.
      Parameters:
      `startPoints` -

      `cost` -

      `direction` -

      `constraint` -

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### nearestFeatures

          public FeaturePath[] nearestFeatures(PointOnNet[] startPoints,
                                               int numberOfFeatures,
                                               int[] featureLayers,
                                               LODNetworkConstraint constraint,
                                               FeatureFilter featureFilter,
                                               int direction)
                                        throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### withinCostFeatures

          public FeaturePath[] withinCostFeatures(PointOnNet[] startPoints,
                                                  double cost,
                                                  int[] featureLayers,
                                                  LODNetworkConstraint constraint,
                                                  FeatureFilter featureFilter,
                                                  int direction)
                                           throws LODNetworkException

      Returns the features and the paths to/from them within the given cost.
      Parameters:
      `startPoints` -

      `cost` -

      `direction` -

      `constraint` -

      `featureFilter` -

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

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

    - #### shortestPaths

          public LogicalSubPath[] shortestPaths(PointOnNet[] startPoints,
                                                PointOnNet[][] endPoints,
                                                LODNetworkConstraint constraint,
                                                int direction)
                                         throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### shortestPathsLight

          public LogicalLightSubPath[] shortestPathsLight(PointOnNet[] startPoints,
                                                          PointOnNet[][] endPoints,
                                                          LODNetworkConstraint constraint,
                                                          int direction)
                                                   throws LODNetworkException

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

- [Prev Class](BinaryHeap.md)
- [Next Class](CachedNetworkIO.md)

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
