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

- [Prev Class](MinimumSpanningTree.md)
- [Next Class](NetworkBuffer.md)

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

## Class NetworkAnalyst

- java.lang.Object

- - oracle.spatial.network.lod.NetworkAnalyst

<!-- -->

-

  ------------------------------------------------------------------------



      public class NetworkAnalyst
      extends java.lang.Object

  This class is the single entry point to all the network analysis operations supported by NDM LOD. To get an instance of this class, use
          NetworkAnalyst analyst = LODNetworkManager.getNetworkAnalyst(networkIO);


  where networkIO is an NetworkIO object for the network of interest.
  Users can define their own link cost calculators or node cost calculators. Note that if you choose to use your own link or node cost calculators, you must set both link and node cost calculators in pairs, that is, there must be the same number of link cost calculators as that of the node cost calculators, and the *i*th link cost calculator must correspond to the *i*th node cost calculator.

  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                     |
    |-------------------|-----------------------------------------------------------|
    | `static int`      | `ACCURACY_LEVEL_HIGH`                                     |
    | `static int`      | `ACCURACY_LEVEL_HIGHEST`                                  |
    | `static int`      | `ACCURACY_LEVEL_LOW`                                      |
    | `static int`      | `ACCURACY_LEVEL_LOWEST`                                   |
    | `static int`      | `ACCURACY_LEVEL_MEDIUM`                                   |
    | `static int`      | `BREADTH_FIRST_SEARCH`<br>Constant for bread-first-search |
    | `static int`      | `DEPTH_FIRST_SEARCH`<br>Constant for depth-first-search   |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `NetworkAnalyst``(`[`NetworkIO`](NetworkIO.md)` reader, `[`NetworkAnalysisConfig`](config/NetworkAnalysisConfig.md)` config)`<br>Constructs an instance of NetworkAnalyst. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                     | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    |-------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `allDetourShortestPathsWithCostLimit``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, `[`PointOnNet`](PointOnNet.md)`[] endPoints, double maxCost, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint)`<br>Finds all paths from the start points to the end points with the following properties: The cost of the path is smaller than or equal to the given cost bound The subpath from the start points to any intermediate node on the path is the shortest possible path from the start points to that node.  |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `allDetourShortestPathsWithDepthLimit``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, `[`PointOnNet`](PointOnNet.md)`[] endPoints, int maxDepth, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint)`<br>Finds all paths from the start points to the end points with the following properties: The depth of the path is smaller than or equal to the given depth bound The subpath from the start points to any intermediate node on the path is the shortest possible path from the start points to that node. |
    | [`ClusterResult`](ClusterResult.md)                   | `bisectClustering``(`[`PointOnNet`](PointOnNet.md)`[] points, int numClusters, int userDataCategory, int xCoordUserDataIndex, int yCoordUserDataIndex, int geometryUserDataIndex)`                                                                                                                                                                                                                                                                                                                                            |
    | [`JGeometry`](../../geometry/JGeometry.md)            | `fastWithinCostPolygon``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, double cost, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter)`<br>Returns the polygon covering the nodes, links or partial links that are within the given cost from the start point candidates.                                                                                                                                                                                     |
    | [`JGeometry`](../../geometry/JGeometry.md)            | `fastWithinCostPolygon``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, double cost, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter, boolean isLowAccuracy)`<br>Returns the polygon covering the nodes, links or partial links that are within the given cost from the start point candidates.                                                                                                                                                              |
    | [`JGeometry`](../../geometry/JGeometry.md)            | `fastWithinReachingCostPolygon``(`[`PointOnNet`](PointOnNet.md)`[] endPoints, double cost, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter)`<br>Returns the polygon covering the nodes, links or partial links that are within the given cost to the end point candidates.                                                                                                                                                                                   |
    | [`JGeometry`](../../geometry/JGeometry.md)            | `fastWithinReachingCostPolygon``(`[`PointOnNet`](PointOnNet.md)`[] endPoints, double cost, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter, boolean isLowAccuracy)`<br>Returns the polygon covering the nodes, links or partial links that are within the given cost to the end point candidates.                                                                                                                                                            |
    | [`OrderedLongSet`](OrderedLongSet.md)`[]`             | `findConnectedComponents``(int linkLevel)`<br>Finds the connected components for the given link level.                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `int`                                                 | `findConnectedComponentsInPartition``(int partitionId, int linkLevel, int startComponentId, java.util.ArrayList<oracle.spatial.network.lod.AnalysisUtility.NodeComponent> nodeComponentArray)`<br>Find the connected components within a partition, with all the external nodes and boundary links included.                                                                                                                                                                                                                  |
    | [`OrderedLongSet`](OrderedLongSet.md)                 | `findConnectedNodes``(int searchMethod, long nodeId, int linkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNode)`<br>Deprecated. <br>use `findConnectedNodes(int, PointOnNet[], int, LODNetworkConstraint, LODGoalNode)`                                                                                                                                                                                                                                       |
    | [`OrderedLongSet`](OrderedLongSet.md)                 | `findConnectedNodes``(int searchMethod, `[`PointOnNet`](PointOnNet.md)`[] points, int linkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNode)`<br>Finds the nodes connected to the given points.                                                                                                                                                                                                                                                               |
    | [`Feature`](Feature.md)`[]`                           | `findReachableFeatures``(int searchMethod, `[`PointOnNet`](PointOnNet.md)`[] startPoints, int linkLevel, int[] featureLayerIds, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`FeatureFilter`](FeatureFilter.md)` featureFilter)`<br>Finds the nodes reachable from the given node.                                                                                                                                                                                                                       |
    | [`OrderedLongSet`](OrderedLongSet.md)                 | `findReachableNodes``(int searchMethod, long startNodeId, int linkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNode)`<br>Deprecated. <br>use `findReachableNodes(int, PointOnNet[], int, LODNetworkConstraint, LODGoalNode)`                                                                                                                                                                                                                                  |
    | [`OrderedLongSet`](OrderedLongSet.md)                 | `findReachableNodes``(int searchMethod, `[`PointOnNet`](PointOnNet.md)`[] startPoints, int linkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNode)`<br>Finds the nodes reachable from the given points.                                                                                                                                                                                                                                                        |
    | [`Feature`](Feature.md)`[]`                           | `findReachingFeatures``(int searchMethod, `[`PointOnNet`](PointOnNet.md)`[] startPoints, int linkLevel, int[] featureLayerIds, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`FeatureFilter`](FeatureFilter.md)` featureFilter)`<br>Finds the nodes that can reach the given node.                                                                                                                                                                                                                        |
    | [`OrderedLongSet`](OrderedLongSet.md)                 | `findReachingNodes``(int searchMethod, long endNodeId, int linkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNode)`<br>Deprecated. <br>use `findReachingNodes(int, PointOnNet[], int, LODNetworkConstraint, LODGoalNode)`                                                                                                                                                                                                                                      |
    | [`OrderedLongSet`](OrderedLongSet.md)                 | `findReachingNodes``(int searchMethod, `[`PointOnNet`](PointOnNet.md)`[] endPoints, int linkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNode)`<br>Finds the nodes that can reach the given points.                                                                                                                                                                                                                                                           |
    | [`LODGoalNode`](LODGoalNode.md)`[]`                   | `getGoalNodeFilters``()`<br>Returns the default goal node filters to be applied to all analysis functions.                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | [`KShortestPaths`](KShortestPaths.md)                 | `getKShortestPathsAlgorithm``()`<br>Returns the default k-shortest paths algorithm.                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | [`LinkCostCalculator`](LinkCostCalculator.md)         | `getLinkCostCalculator``()`<br>Returns the primary link cost calculator.                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | [`LinkCostCalculator`](LinkCostCalculator.md)`[]`     | `getLinkCostCalculators``()`<br>Returns the link cost calculators.                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | [`LinkLevelSelector`](LinkLevelSelector.md)           | `getLinkLevelSelector``()`<br>Returns the link level selector to be used by all analysis functions.                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | [`LODNetworkConstraint`](LODNetworkConstraint.md)`[]` | `getNetworkConstraints``()`<br>Returns the default network constraints to be applied to all analysis functions.                                                                                                                                                                                                                                                                                                                                                                                                               |
    | [`NetworkExplorer`](NetworkExplorer.md)               | `getNetworkExplorer``()`<br>Returns the network explorer used by this network analyst.                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | [`NodeCostCalculator`](NodeCostCalculator.md)         | `getNodeCostCalculator``()`<br>Returns the primary node cost calculator.                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | [`NodeCostCalculator`](NodeCostCalculator.md)`[]`     | `getNodeCostCalculators``()`<br>Returns the node cost calculators.                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | [`PairwiseCostCalculator`](PairwiseCostCalculator.md) | `getPairwiseCostCalculator``()`<br>Returns the default pairwise cost calculator.                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | [`PairwiseShortestPaths`](PairwiseShortestPaths.md)   | `getPairwiseShortestPathsAlgorithm``()`<br>Returns the default pairwise shortest paths algorithm.                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | [`ShortestPath`](ShortestPath.md)                     | `getShortestPathAlgorithm``()`<br>Returns the default shortest path algorithm.                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | [`TSP`](TSP.md)                                       | `getTspAlgorithm``()`<br>Returns the default TSP algorithm.                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `boolean`                                             | `isReachable``(`[`Feature`](Feature.md)`[] start, `[`Feature`](Feature.md)`[] end, int linkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint)`<br>Checks whether there is a path from the start features to the end features using the given link level for long-haul search.                                                                                                                                                                                                                             |
    | `boolean`                                             | `isReachable``(long startNodeId, long endNodeId, int linkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint)`<br>Checks whether there is a path from the start node to the end node using the given link level for long-haul search.                                                                                                                                                                                                                                                                       |
    | `boolean`                                             | `isReachable``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, `[`PointOnNet`](PointOnNet.md)`[] endPoints, int linkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint)`<br>Checks whether there is a path from the start node to the end node using the given link level for long-haul search.                                                                                                                                                                                                             |
    | [`ClusterResult`](ClusterResult.md)                   | `kMeansClustering``(`[`PointOnNet`](PointOnNet.md)`[] points, int numClusters, int maxSize, int minSize, int userDataCategory, int xCoordUserDataIndex, int yCoordUserDataIndex, int geometryUserDataIndex)`                                                                                                                                                                                                                                                                                                                  |
    | [`PathFeature`](PathFeature.md)`[]`                   | `kShortestPaths``(`[`Feature`](Feature.md)`[] start, `[`Feature`](Feature.md)`[] end, int k, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`KShortestPaths`](KShortestPaths.md)` algorithm)`<br>Finds the top k shortest paths from the start feature candidates to the end feature candidates.                                                                                                                                                                                                           |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `kShortestPaths``(`[`PointOnNet`](PointOnNet.md)`[] startPoint, `[`PointOnNet`](PointOnNet.md)`[] endPoint, int k, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint)`<br>Returns K shortest loopless paths from the start point candidates to the end point candidates.                                                                                                                                                                                                                                         |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `kShortestPaths``(`[`PointOnNet`](PointOnNet.md)`[] startPoint, `[`PointOnNet`](PointOnNet.md)`[] endPoint, int k, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`KShortestPaths`](KShortestPaths.md)` kspAlgorithm)`<br>Returns K shortest loopless paths from the start point candiates to the end point candidates.                                                                                                                                                                                    |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `kShortestPaths``(`[`PointOnNet`](PointOnNet.md)`[] startPoint, `[`PointOnNet`](PointOnNet.md)`[] endPoint, int k, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`PathFilter`](PathFilter.md)` pathFilter, `[`KShortestPaths`](KShortestPaths.md)` kspAlgorithm)`                                                                                                                                                                                                                                         |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `kShortestPathsBfs``(`[`PointOnNet`](PointOnNet.md)`[] startPoint, `[`PointOnNet`](PointOnNet.md)`[] endPoint, int k, double maxToMinBound, long timeout, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`PathFilter`](PathFilter.md)` pathFilter)`<br>Returns K shortest loopless paths from the start point candidates to the end point candidates.                                                                                                                                                      |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `kShortestPathsDijkstra``(`[`PointOnNet`](PointOnNet.md)`[] startPoint, `[`PointOnNet`](PointOnNet.md)`[] endPoint, int k, double maxToMinBound, long timeout, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`PathFilter`](PathFilter.md)` pathFilter)`<br>Returns K shortest paths from the start point candidates to the end point candidates.                                                                                                                                                          |
    | `long[]`                                              | `mcst``(int linkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint)`<br>Deprecated. <br>use `mst(int, LODNetworkConstraint, MinimumSpanningTree)`                                                                                                                                                                                                                                                                                                                                                          |
    | `long[]`                                              | `mcst``(int linkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`NetworkUpdate`](NetworkUpdate.md)` tmpNetworkUpdate)`<br>Deprecated. <br>use `mst(int, LODNetworkConstraint, MinimumSpanningTree)`                                                                                                                                                                                                                                                                                                  |
    | [`SpanningTree`](SpanningTree.md)                     | `mst``(int linkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint)`<br>Returns the minimum-spanning-tree for the network on the given link level.                                                                                                                                                                                                                                                                                                                                                          |
    | [`SpanningTree`](SpanningTree.md)                     | `mst``(int linkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`MinimumSpanningTree`](MinimumSpanningTree.md)` algorithm)`<br>Returns the minimum-spanning-tree for the network on the given link level.                                                                                                                                                                                                                                                                                             |
    | [`FeaturePath`](FeaturePath.md)`[]`                   | `nearestFeatures``(`[`Feature`](Feature.md)`[] start, int numberOfFeatures, int[] featureLayerIds, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`FeatureFilter`](FeatureFilter.md)` featureFilter)`<br>Finds the nearest features from the start feature candidates.                                                                                                                                                                                                                                     |
    | [`FeaturePath`](FeaturePath.md)`[]`                   | `nearestFeatures``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, int numberOfFeatures, int[] featureLayerIds, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`FeatureFilter`](FeatureFilter.md)` featureFilter)`<br>Finds the nearest features from the start point candidates.                                                                                                                                                                                                                           |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `nearestNeighbors``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, int numberOfNeighbors, int searchLinkLevel, int targetLinkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter)`<br>Finds the nearest neighbors from the start point candidates.                                                                                                                                                                                                        |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `nearestNeighbors``(`[`PointOnNet`](PointOnNet.md)` startPoint, int numberOfNeighbors, int searchLinkLevel, int targetLinkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter)`<br>Finds the nearest neighbors from the start point.                                                                                                                                                                                                                      |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `nearestNeighbors``(`[`PointOnNet`](PointOnNet.md)` startPoint, int numberOfNeighbors, int targetLinkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter)`<br>Finds the nearest neighbors from the start point.                                                                                                                                                                                                                                           |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `nearestNeighbors``(`[`PointOnNet`](PointOnNet.md)` startPoint, int numberOfNeighbors, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter)`<br>Finds the nearest neighbors from the start point.                                                                                                                                                                                                                                                                |
    | [`LogicalLightSubPath`](LogicalLightSubPath.md)`[]`   | `nearestNeighborsLight``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, int numberOfNeighbors, int searchLinkLevel, int targetLinkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter)`<br>Finds the nearest neighbors from the start point candidates.                                                                                                                                                                                                   |
    | [`PathToPoint`](PathToPoint.md)`[]`                   | `nearestPoints``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, `[`PointOnNet`](PointOnNet.md)`[][] targetPoints, int k, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, boolean returnFullPath)`<br>Returns the top k nearest target points from the start points.                                                                                                                                                                                                                                           |
    | [`FeaturePath`](FeaturePath.md)`[]`                   | `nearestReachingFeatures``(`[`Feature`](Feature.md)`[] end, int numberOfFeatures, int[] featureLayerIds, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`FeatureFilter`](FeatureFilter.md)` featureFilter)`<br>Finds the nearest reaching features to the end feature candidates.                                                                                                                                                                                                                          |
    | [`FeaturePath`](FeaturePath.md)`[]`                   | `nearestReachingFeatures``(`[`PointOnNet`](PointOnNet.md)`[] endPoints, int numberOfFeatures, int[] featureLayerIds, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`FeatureFilter`](FeatureFilter.md)` featureFilter)`<br>Finds the nearest reaching features to the end point candidates.                                                                                                                                                                                                                |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `nearestReachingNeighbors``(`[`PointOnNet`](PointOnNet.md)`[] endPoints, int numberOfNeighbors, int searchLinkLevel, int targetLinkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter)`<br>Finds the nearest reaching neighbors to the end point candidates.                                                                                                                                                                                             |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `nearestReachingNeighbors``(`[`PointOnNet`](PointOnNet.md)` endPoint, int numberOfNeighbors, int searchLinkLevel, int targetLinkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter)`<br>Finds the nearest reaching neighbors to the end point.                                                                                                                                                                                                           |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `nearestReachingNeighbors``(`[`PointOnNet`](PointOnNet.md)` endPoint, int numberOfNeighbors, int targetLinkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter)`<br>Finds the nearest reaching neighbors to the end point.                                                                                                                                                                                                                                |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `nearestReachingNeighbors``(`[`PointOnNet`](PointOnNet.md)` endPoint, int numberOfNeighbors, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter)`<br>Finds the nearest reaching neighbors to the end point.                                                                                                                                                                                                                                                     |
    | [`LogicalLightSubPath`](LogicalLightSubPath.md)`[]`   | `nearestReachingNeighborsLight``(`[`PointOnNet`](PointOnNet.md)`[] endPoints, int numberOfNeighbors, int searchLinkLevel, int targetLinkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter)`<br>Finds the nearest reaching neighbors to the end point candidates.                                                                                                                                                                                        |
    | [`PathToPoint`](PathToPoint.md)`[]`                   | `nearestReachingPoints``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, `[`PointOnNet`](PointOnNet.md)`[][] targetPoints, int k, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, boolean returnFullPath)`<br>Returns the top k nearest reaching target points to the start points.                                                                                                                                                                                                                            |
    | [`NetworkBuffer`](NetworkBuffer.md)                   | `networkBuffer``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, double cost, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint)`<br>Computes network buffer within the given cost from the start point candidates.                                                                                                                                                                                                                                                                                               |
    | [`NetworkBuffer`](NetworkBuffer.md)                   | `reachingNetworkBuffer``(`[`PointOnNet`](PointOnNet.md)`[] endPoints, double cost, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint)`<br>Computes network buffer within the given cost to the end point candidates.                                                                                                                                                                                                                                                                                             |
    | `void`                                                | `resetCostCalculators``()`<br>Restores the default settings of link cost calculators and node cost calculators, which uses the DefaultLinkCostCalculator as the primary link cost calculator and the DefaultNodeCostCalculator as the primary node cost calculator.                                                                                                                                                                                                                                                           |
    | [`PathFeature`](PathFeature.md)`[]`                   | `reverseKShortestPaths``(`[`Feature`](Feature.md)`[] end, `[`Feature`](Feature.md)`[] start, int k, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`KShortestPaths`](KShortestPaths.md)` algorithm)`<br>Finds the top k shortest paths from the start feature candidates to the end feature candidates, using reverse search direction.                                                                                                                                                                    |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `reverseKShortestPaths``(`[`PointOnNet`](PointOnNet.md)`[] endPoint, `[`PointOnNet`](PointOnNet.md)`[] startPoint, int k, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint)`<br>Returns K shortest loopless paths from the start point candidates to the end point candidates, using reverse search direction.                                                                                                                                                                                                  |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `reverseKShortestPaths``(`[`PointOnNet`](PointOnNet.md)`[] endPoint, `[`PointOnNet`](PointOnNet.md)`[] startPoint, int k, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`KShortestPaths`](KShortestPaths.md)` kspAlgorithm)`<br>Returns reverse K shortest loopless paths from the start point candiates to the end point candidates, using reverse search direction.                                                                                                                                     |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `reverseKShortestPaths``(`[`PointOnNet`](PointOnNet.md)`[] endPoint, `[`PointOnNet`](PointOnNet.md)`[] startPoint, int k, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`PathFilter`](PathFilter.md)` pathFilter, `[`KShortestPaths`](KShortestPaths.md)` kspAlgorithm)`                                                                                                                                                                                                                                  |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `reverseKShortestPathsBfs``(`[`PointOnNet`](PointOnNet.md)`[] startPoint, `[`PointOnNet`](PointOnNet.md)`[] endPoint, int k, double maxToMinBound, long timeout, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`PathFilter`](PathFilter.md)` pathFilter)`<br>Returns K shortest loopless paths from the start point candidates to the end point candidates.                                                                                                                                               |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `reverseKShortestPathsDijkstra``(`[`PointOnNet`](PointOnNet.md)`[] startPoint, `[`PointOnNet`](PointOnNet.md)`[] endPoint, int k, double maxToMinBound, long timeout, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`PathFilter`](PathFilter.md)` pathFilter)`<br>Returns K shortest loopless paths from the start point candidates to the end point candidates.                                                                                                                                          |
    | [`PathFeature`](PathFeature.md)                       | `reverseShortestPath``(`[`Feature`](Feature.md)`[] end, `[`Feature`](Feature.md)`[] start, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`ShortestPath`](ShortestPath.md)` algorithm)`<br>Finds the shortest path from the start feature candidates to the end feature candidates, using reverse search direction.                                                                                                                                                                                        |
    | [`LogicalSubPath`](LogicalSubPath.md)                 | `reverseShortestPath``(`[`PointOnNet`](PointOnNet.md)`[] endPoints, `[`PointOnNet`](PointOnNet.md)`[] startPoints, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`ShortestPath`](ShortestPath.md)` algorithm)`<br>Finds the shortest path using the input algorithm, using reverse search direction.                                                                                                                                                                                                      |
    | `void`                                                | `setKShortestPathsAlgorithm``(`[`KShortestPaths`](KShortestPaths.md)` kspAlgorithm)`<br>Sets the default k-shortest paths algorithm.                                                                                                                                                                                                                                                                                                                                                                                          |
    | `void`                                                | `setLinkCostCalculator``(`[`LinkCostCalculator`](LinkCostCalculator.md)` calculator)`<br>Sets the primary link cost calculator, and removes all secondary link cost calculators.                                                                                                                                                                                                                                                                                                                                              |
    | `void`                                                | `setLinkCostCalculators``(`[`LinkCostCalculator`](LinkCostCalculator.md)`[] calculators)`<br>Sets the link cost calculators.                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `void`                                                | `setNetworkExplorer``(`[`NetworkExplorer`](NetworkExplorer.md)` ne)`                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `void`                                                | `setNetworkUpdate``(java.util.HashMap<java.lang.Integer,`[`NetworkUpdate`](NetworkUpdate.md)`> networkUpdates)`<br>Sets the network update objects.                                                                                                                                                                                                                                                                                                                                                                           |
    | `void`                                                | `setNetworkUpdates``(java.util.HashMap<java.lang.Integer,`[`NetworkUpdate`](NetworkUpdate.md)`> networkUpdates)`<br>Sets the network update objects.                                                                                                                                                                                                                                                                                                                                                                          |
    | `void`                                                | `setNodeCostCalculator``(`[`NodeCostCalculator`](NodeCostCalculator.md)` calculator)`<br>Sets the primary node cost calculator, and removes all secondary node cost calculators.                                                                                                                                                                                                                                                                                                                                              |
    | `void`                                                | `setNodeCostCalculators``(`[`NodeCostCalculator`](NodeCostCalculator.md)`[] calculators)`<br>Sets the node cost calculators.                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `void`                                                | `setPairwiseCostCalculator``(`[`PairwiseCostCalculator`](PairwiseCostCalculator.md)` pwcc)`<br>Sets the default pairwise cost calculator.                                                                                                                                                                                                                                                                                                                                                                                     |
    | `void`                                                | `setPairwiseShortestPathsAlgorithm``(`[`PairwiseShortestPaths`](PairwiseShortestPaths.md)` pwspAlgorithm)`<br>Sets the default pairwise shortest paths algorithm.                                                                                                                                                                                                                                                                                                                                                             |
    | `void`                                                | `setShortestPathAlgorithm``(`[`ShortestPath`](ShortestPath.md)` spAlgorithm)`<br>Sets the default shortest path algorithm.                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `void`                                                | `setTspAlgorithm``(`[`TSP`](TSP.md)` tspAlgorithm)`<br>Sets the default TSP algorithm.                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | [`PathFeature`](PathFeature.md)                       | `shortestPath``(`[`Feature`](Feature.md)`[] start, `[`Feature`](Feature.md)`[] end, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`ShortestPath`](ShortestPath.md)` algorithm)`<br>Finds the shortest path from the start feature candidates to the end feature candidates.                                                                                                                                                                                                                               |
    | [`LogicalSubPath`](LogicalSubPath.md)                 | `shortestPath``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, `[`PointOnNet`](PointOnNet.md)`[] endPoints, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`ShortestPath`](ShortestPath.md)` algorithm)`<br>Finds the shortest path using the input algorithm.                                                                                                                                                                                                                                             |
    | [`PathFeature`](PathFeature.md)                       | `shortestPathAStar``(`[`Feature`](Feature.md)`[] start, `[`Feature`](Feature.md)`[] end, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`HeuristicCostFunction`](HeuristicCostFunction.md)` hcf, `[`LinkLevelSelector`](LinkLevelSelector.md)` lls)`<br>Finds the shortest path from the start feature candidates to the end feature candidates.                                                                                                                                                           |
    | [`LogicalSubPath`](LogicalSubPath.md)                 | `shortestPathAStar``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, `[`PointOnNet`](PointOnNet.md)`[] endPoints, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`HeuristicCostFunction`](HeuristicCostFunction.md)` hcf, `[`LinkLevelSelector`](LinkLevelSelector.md)` lls)`<br>Finds the shortest path using A\* algorithm.                                                                                                                                                                               |
    | [`LogicalSubPath`](LogicalSubPath.md)                 | `shortestPathAStar``(`[`PointOnNet`](PointOnNet.md)` startPoint, `[`PointOnNet`](PointOnNet.md)` endPoint, int searchLinkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`HeuristicCostFunction`](HeuristicCostFunction.md)` hcf, double[] costThresholds)`<br>Finds the shortest path using A\* algorithm with dynamic link level selector.                                                                                                                                                         |
    | [`LogicalSubPath`](LogicalSubPath.md)                 | `shortestPathAStar``(`[`PointOnNet`](PointOnNet.md)` startPoint, `[`PointOnNet`](PointOnNet.md)` endPoint, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`HeuristicCostFunction`](HeuristicCostFunction.md)` hcf, double[] costThresholds)`<br>Finds the shortest path using A\* algorithm using dynamic link level selector.                                                                                                                                                                             |
    | [`LogicalSubPath`](LogicalSubPath.md)                 | `shortestPathAStar``(`[`PointOnNet`](PointOnNet.md)` startPoint, `[`PointOnNet`](PointOnNet.md)` endPoint, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`HeuristicCostFunction`](HeuristicCostFunction.md)` hcf, `[`LinkLevelSelector`](LinkLevelSelector.md)` lls)`<br>Finds the shortest path using A\* algorithm.                                                                                                                                                                                     |
    | [`PathFeature`](PathFeature.md)                       | `shortestPathDijkstra``(`[`Feature`](Feature.md)`[] start, `[`Feature`](Feature.md)`[] end, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LinkLevelSelector`](LinkLevelSelector.md)` lls)`<br>Finds the shortest path from the start feature candidates to the end feature candidates.                                                                                                                                                                                                                   |
    | [`LogicalSubPath`](LogicalSubPath.md)                 | `shortestPathDijkstra``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, `[`PointOnNet`](PointOnNet.md)`[] endPoints, int searchLinkLevel, int maxHighLevelNodesToConsider, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint)`<br>Finds the shortest path using Dijkstra algorithm where the long-haul path is computed on the given link level.                                                                                                                                                                  |
    | [`LogicalSubPath`](LogicalSubPath.md)                 | `shortestPathDijkstra``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, `[`PointOnNet`](PointOnNet.md)`[] endPoints, int searchLinkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint)`<br>Finds the shortest path using Dijkstra algorithm where the long-haul path is computed on the given link level.                                                                                                                                                                                                   |
    | [`LogicalSubPath`](LogicalSubPath.md)                 | `shortestPathDijkstra``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, `[`PointOnNet`](PointOnNet.md)`[] endPoints, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LinkLevelSelector`](LinkLevelSelector.md)` lls)`<br>Finds the shortest path using Dijkstra algorithm with the given link level selector.                                                                                                                                                                                               |
    | [`LogicalSubPath`](LogicalSubPath.md)                 | `shortestPathDijkstra``(`[`PointOnNet`](PointOnNet.md)` startPoint, `[`PointOnNet`](PointOnNet.md)` endPoint, int searchLinkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint)`<br>Finds the shortest path using Dijkstra algorithm where the long-haul path is computed on the given link level.                                                                                                                                                                                                         |
    | [`LogicalSubPath`](LogicalSubPath.md)                 | `shortestPathDijkstra``(`[`PointOnNet`](PointOnNet.md)` startPoint, `[`PointOnNet`](PointOnNet.md)` endPoint, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint)`<br>Finds the shortest path on the minimum link level using Dijkstra algorithm.                                                                                                                                                                                                                                                                 |
    | [`LogicalSubPath`](LogicalSubPath.md)                 | `shortestPathDijkstraMaxLevel``(`[`PointOnNet`](PointOnNet.md)` startPoint, `[`PointOnNet`](PointOnNet.md)` endPoint, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint)`<br>Finds the shortest path using Dijkstra algorithm where the long-haul path is computed on the maximum link level.                                                                                                                                                                                                                    |
    | [`LogicalSubPath`](LogicalSubPath.md)                 | `shortestPathHierarchical``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, `[`PointOnNet`](PointOnNet.md)`[] endPoints, int searchLinkLevel, int maxHighLevelNodesToConsider, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`ShortestPath`](ShortestPath.md)` algorithm)`<br>Finds the shortest path from the start point candidates to the end point candidates.                                                                                                                                         |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `traceIn``(`[`PointOnNet`](PointOnNet.md)`[] endPoints, double cost, int searchLinkLevel, int targetLinkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter, boolean returnBoundaryPointsOnly)`<br>Finds the nodes and partial links within the given cost to the end point candidates.                                                                                                                                                                   |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `traceIn``(`[`PointOnNet`](PointOnNet.md)` endPoint, double cost, int searchLinkLevel, int targetLinkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter)`<br>Finds the nodes and partial links within the given cost to the end point.                                                                                                                                                                                                                   |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `traceIn``(`[`PointOnNet`](PointOnNet.md)` endPoint, double cost, int targetLinkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter)`<br>Finds the nodes and partial links within the given cost to the end point.                                                                                                                                                                                                                                        |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `traceIn``(`[`PointOnNet`](PointOnNet.md)` endPoint, double cost, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter)`<br>Finds the nodes and partial links within the given cost to the end point.                                                                                                                                                                                                                                                             |
    | [`LogicalLightSubPath`](LogicalLightSubPath.md)`[]`   | `traceInLight``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, double cost, int searchLinkLevel, int targetLinkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter, boolean returnBoundaryPointsOnly)`<br>Finds the nodes and partial links within the given cost to the end point candidates.                                                                                                                                                            |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `traceOut``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, double cost, int searchLinkLevel, int targetLinkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter, boolean returnBoundaryPointsOnly)`<br>Finds the nodes and partial links within the given cost from the start point candidates.                                                                                                                                                            |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `traceOut``(`[`PointOnNet`](PointOnNet.md)` startPoint, double cost, int searchLinkLevel, int targetLinkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter)`<br>Finds the nodes and partial links within the given cost from the start point.                                                                                                                                                                                                            |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `traceOut``(`[`PointOnNet`](PointOnNet.md)` startPoint, double cost, int targetLinkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter)`<br>Finds the nodes and partial links within the given cost from the start point.                                                                                                                                                                                                                                 |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `traceOut``(`[`PointOnNet`](PointOnNet.md)` startPoint, double cost, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter)`<br>Finds the nodes and partial links within the given cost from the start point.                                                                                                                                                                                                                                                      |
    | [`LogicalLightSubPath`](LogicalLightSubPath.md)`[]`   | `traceOutLight``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, double cost, int searchLinkLevel, int targetLinkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter, boolean returnBoundaryPointsOnly)`<br>Finds the nodes and partial links within the given cost from the start points.                                                                                                                                                                 |
    | [`TspPathFeature`](TspPathFeature.md)                 | `tsp``(`[`Feature`](Feature.md)`[][] featuresToVisit, `[`TSP.TourFlag`](TSP.TourFlag.md)` tourFlag, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`TSP`](TSP.md)` algorithm)`<br>Returns the traveling salesman tour covering the input features.                                                                                                                                                                                                                                                         |
    | [`TspPathFeature`](TspPathFeature.md)                 | `tsp``(`[`Feature`](Feature.md)`[][] featuresToVisit, `[`TSP.TourFlag`](TSP.TourFlag.md)` tourFlag, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` networkConstraint, `[`TspConstraint`](TspConstraint.md)` tspConstraint, `[`TSP`](TSP.md)` algorithm)`<br>Returns the traveling salesman tour covering the input features.                                                                                                                                                                                             |
    | [`TspPath`](TspPath.md)                               | `tsp``(`[`PointOnNet`](PointOnNet.md)`[][] pointsToVisit, `[`TSP.TourFlag`](TSP.TourFlag.md)` tourFlag, int linkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint)`<br>Returns the traveling salesman tour covering the given points.                                                                                                                                                                                                                                                                     |
    | [`TspPath`](TspPath.md)                               | `tsp``(`[`PointOnNet`](PointOnNet.md)`[][] pointsToVisit, `[`TSP.TourFlag`](TSP.TourFlag.md)` tourFlag, int linkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`TSP`](TSP.md)` algorithm)`<br>Returns the traveling salesman tour covering the input points.                                                                                                                                                                                                                                        |
    | [`TspPath`](TspPath.md)                               | `tsp``(`[`PointOnNet`](PointOnNet.md)`[][] pointsToVisit, `[`TSP.TourFlag`](TSP.TourFlag.md)` tourFlag, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` networkConstraint)`<br>Returns the traveling salesman tour covering the input points.                                                                                                                                                                                                                                                                             |
    | [`TspPath`](TspPath.md)                               | `tsp``(`[`PointOnNet`](PointOnNet.md)`[][] pointsToVisit, `[`TSP.TourFlag`](TSP.TourFlag.md)` tourFlag, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` networkConstraint, `[`TSP`](TSP.md)` algorithm)`<br>Returns the traveling salesman tour covering the input points.                                                                                                                                                                                                                                                |
    | [`TspPath`](TspPath.md)                               | `tsp``(`[`PointOnNet`](PointOnNet.md)`[][] pointsToVisit, `[`TSP.TourFlag`](TSP.TourFlag.md)` tourFlag, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` networkConstraint, `[`TspConstraint`](TspConstraint.md)` tspConstraint)`<br>Returns the traveling salesman tour covering the input points.                                                                                                                                                                                                                        |
    | [`TspPath`](TspPath.md)                               | `tsp``(`[`PointOnNet`](PointOnNet.md)`[][] pointsToVisit, `[`TSP.TourFlag`](TSP.TourFlag.md)` tourFlag, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` networkConstraint, `[`TspConstraint`](TspConstraint.md)` tspConstraint, `[`TSP`](TSP.md)` algorithm)`<br>Returns the traveling salesman tour covering the input points.                                                                                                                                                                                           |
    | [`TspPath`](TspPath.md)`[]`                           | `vrpNoDepot``(`[`PointOnNet`](PointOnNet.md)`[][] points, int numVehicles, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` networkConstraint, `[`TspConstraint`](TspConstraint.md)` tspConstraint, int userDataCategory, int xUserDataIndex, int yUserDataIndex, int geometryUserDataIndex)`                                                                                                                                                                                                                              |
    | [`TspPath`](TspPath.md)`[]`                           | `vrpNoDepot``(`[`PointOnNet`](PointOnNet.md)`[][] points, int numVehicles, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` networkConstraint, `[`TspConstraint`](TspConstraint.md)` tspConstraint, `[`VRP`](VRP.md)` vrpAlgo)`                                                                                                                                                                                                                                                                                            |
    | [`TspPath`](TspPath.md)`[]`                           | `vrpSingleDepot``(`[`PointOnNet`](PointOnNet.md)`[][] points, int numVehicles, `[`PointOnNet`](PointOnNet.md)`[] depot, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` networkConstraint, `[`TspConstraint`](TspConstraint.md)` tspConstraint, int userDataCategory, int xUserDataIndex, int yUserDataIndex, int geometryUserDataIndex)`                                                                                                                                                                                 |
    | [`TspPath`](TspPath.md)`[]`                           | `vrpSingleDepot``(`[`PointOnNet`](PointOnNet.md)`[][] points, int numVehicles, `[`PointOnNet`](PointOnNet.md)`[] depot, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` networkConstraint, `[`TspConstraint`](TspConstraint.md)` tspConstraint, `[`VRP`](VRP.md)` vrpAlgo)`                                                                                                                                                                                                                                               |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `withinCost``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, double cost, int searchLinkLevel, int targetLinkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter, boolean returnBoundaryNodesOnly)`<br>Finds the nodes within the given cost from the start point candidates.                                                                                                                                                                             |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `withinCost``(`[`PointOnNet`](PointOnNet.md)` startPoint, double cost, int searchLinkLevel, int targetLinkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter)`<br>Finds the nodes within the given cost from the start point.                                                                                                                                                                                                                            |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `withinCost``(`[`PointOnNet`](PointOnNet.md)` startPoint, double cost, int targetLinkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter)`<br>Finds the nodes within the given cost from the start point.                                                                                                                                                                                                                                                 |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `withinCost``(`[`PointOnNet`](PointOnNet.md)` startPoint, double cost, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter)`<br>Finds the nodes within the given cost from the start point.                                                                                                                                                                                                                                                                      |
    | [`FeaturePath`](FeaturePath.md)`[]`                   | `withinCostFeatures``(`[`Feature`](Feature.md)`[] start, double cost, int[] featureLayerIds, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`FeatureFilter`](FeatureFilter.md)` featureFilter)`<br>Finds features within the given cost from the start features.                                                                                                                                                                                                                                           |
    | [`FeaturePath`](FeaturePath.md)`[]`                   | `withinCostFeatures``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, double cost, int[] featureLayerIds, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`FeatureFilter`](FeatureFilter.md)` featureFilter)`<br>Finds features within the given cost from the start features.                                                                                                                                                                                                                               |
    | [`LogicalLightSubPath`](LogicalLightSubPath.md)`[]`   | `withinCostLight``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, double cost, int searchLinkLevel, int targetLinkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter, boolean returnBoundaryNodesOnly)`<br>Finds the nodes within the given cost from the start point candidates.                                                                                                                                                                        |
    | [`PathToPoint`](PathToPoint.md)`[]`                   | `withinCostPoints``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, `[`PointOnNet`](PointOnNet.md)`[][] targetPoints, double cost, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, boolean returnFullPath)`                                                                                                                                                                                                                                                                                                    |
    | [`JGeometry`](../../geometry/JGeometry.md)            | `withinCostPolygon``(`[`Feature`](Feature.md)`[] startFeatures, double cost, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter)`<br>Returns the polygon covering the nodes, links or partial links that are within the given cost from the start feature candidates.                                                                                                                                                                                           |
    | [`JGeometry`](../../geometry/JGeometry.md)            | `withinCostPolygon``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, double cost, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter)`<br>Returns the polygon covering the nodes, links or partial links that are within the given cost from the start point candidates.                                                                                                                                                                                         |
    | [`JGeometry`](../../geometry/JGeometry.md)            | `withinCostPolygon``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, double cost, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter, int accuracyLevel)`<br>Returns the polygon covering the nodes, links or partial links that are within the given cost from the start point candidates.                                                                                                                                                                      |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `withinReachingCost``(`[`PointOnNet`](PointOnNet.md)`[] endPoints, double cost, int searchLinkLevel, int targetLinkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter, boolean returnBoundaryNodesOnly)`<br>Finds the nodes within the given cost to the end point candidates.                                                                                                                                                                           |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `withinReachingCost``(`[`PointOnNet`](PointOnNet.md)` endPoint, double cost, int searchLinkLevel, int targetLinkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter)`<br>Finds the nodes within the given cost to the end point.                                                                                                                                                                                                                          |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `withinReachingCost``(`[`PointOnNet`](PointOnNet.md)` endPoint, double cost, int targetLinkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter)`<br>Finds the nodes within the given cost to the end point.                                                                                                                                                                                                                                               |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`             | `withinReachingCost``(`[`PointOnNet`](PointOnNet.md)` endPoint, double cost, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter)`<br>Finds the nodes within the given cost to the end point.                                                                                                                                                                                                                                                                    |
    | [`FeaturePath`](FeaturePath.md)`[]`                   | `withinReachingCostFeatures``(`[`Feature`](Feature.md)`[] endFeatures, double cost, int[] featureLayerIds, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`FeatureFilter`](FeatureFilter.md)` featureFilter)`<br>Finds features within the given cost to the end features.                                                                                                                                                                                                                                 |
    | [`FeaturePath`](FeaturePath.md)`[]`                   | `withinReachingCostFeatures``(`[`PointOnNet`](PointOnNet.md)`[] endPoints, double cost, int[] featureLayerIds, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`FeatureFilter`](FeatureFilter.md)` featureFilter)`<br>Finds features within the given cost to the end features.                                                                                                                                                                                                                             |
    | [`LogicalLightSubPath`](LogicalLightSubPath.md)`[]`   | `withinReachingCostLight``(`[`PointOnNet`](PointOnNet.md)`[] endPoints, double cost, int searchLinkLevel, int targetLinkLevel, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter, boolean returnBoundaryNodesOnly)`<br>Finds the nodes within the given cost to the end points.                                                                                                                                                                                |
    | [`PathToPoint`](PathToPoint.md)`[]`                   | `withinReachingCostPoints``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, `[`PointOnNet`](PointOnNet.md)`[][] targetPoints, double cost, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, boolean returnFullPath)`                                                                                                                                                                                                                                                                                            |
    | [`JGeometry`](../../geometry/JGeometry.md)            | `withinReachingCostPolygon``(`[`Feature`](Feature.md)`[] endFeatures, double cost, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter)`<br>Returns the polygon covering the nodes, links or partial links that are within the given cost to the end feature candidates.                                                                                                                                                                                         |
    | [`JGeometry`](../../geometry/JGeometry.md)            | `withinReachingCostPolygon``(`[`PointOnNet`](PointOnNet.md)`[] endPoints, double cost, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter)`<br>Returns the polygon covering the nodes, links or partial links that are within the given cost to the end point candidates.                                                                                                                                                                                       |
    | [`JGeometry`](../../geometry/JGeometry.md)            | `withinReachingCostPolygon``(`[`PointOnNet`](PointOnNet.md)`[] endPoints, double cost, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`LODGoalNode`](LODGoalNode.md)` goalNodeFilter, int accuracyLevel)`<br>Returns the polygon covering the nodes, links or partial links that are within the given cost to the end point candidates.                                                                                                                                                                    |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### BREADTH_FIRST_SEARCH

          public static final int BREADTH_FIRST_SEARCH

      Constant for bread-first-search
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### DEPTH_FIRST_SEARCH

          public static final int DEPTH_FIRST_SEARCH

      Constant for depth-first-search
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ACCURACY_LEVEL_LOWEST

          public static final int ACCURACY_LEVEL_LOWEST

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ACCURACY_LEVEL_LOW

          public static final int ACCURACY_LEVEL_LOW

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ACCURACY_LEVEL_MEDIUM

          public static final int ACCURACY_LEVEL_MEDIUM

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ACCURACY_LEVEL_HIGH

          public static final int ACCURACY_LEVEL_HIGH

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### ACCURACY_LEVEL_HIGHEST

          public static final int ACCURACY_LEVEL_HIGHEST

      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### NetworkAnalyst

          public NetworkAnalyst(NetworkIO reader,
                                NetworkAnalysisConfig config)
                         throws LODNetworkException

      Constructs an instance of NetworkAnalyst.
      Parameters:
      `reader` - network reader for the network to be analyzed

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

  <!-- -->

  - ### Method Detail

    - #### getNetworkExplorer

          public NetworkExplorer getNetworkExplorer()

      Returns the network explorer used by this network analyst.

    <!-- -->

    - #### setNetworkExplorer

          public void setNetworkExplorer(NetworkExplorer ne)

    <!-- -->

    - #### setNetworkUpdates

          public void setNetworkUpdates(java.util.HashMap<java.lang.Integer,NetworkUpdate> networkUpdates)

      Sets the network update objects. These objects will be super imposed to the static network information during network analysis.
      Parameters:
      `networkUpdates` - network update objects for different link levels

    <!-- -->

    - #### setNetworkUpdate

          public void setNetworkUpdate(java.util.HashMap<java.lang.Integer,NetworkUpdate> networkUpdates)

      Sets the network update objects. These objects will be super imposed to the static network information during network analysis.
      Parameters:
      `networkUpdates` - network update objects for different link levels

    <!-- -->

    - #### getGoalNodeFilters

          public LODGoalNode[] getGoalNodeFilters()

      Returns the default goal node filters to be applied to all analysis functions.
      Returns:

    <!-- -->

    - #### getNetworkConstraints

          public LODNetworkConstraint[] getNetworkConstraints()

      Returns the default network constraints to be applied to all analysis functions.
      Returns:

    <!-- -->

    - #### getLinkLevelSelector

          public LinkLevelSelector getLinkLevelSelector()

      Returns the link level selector to be used by all analysis functions.
      Returns:

    <!-- -->

    - #### getShortestPathAlgorithm

          public ShortestPath getShortestPathAlgorithm()

      Returns the default shortest path algorithm.
      Returns:

    <!-- -->

    - #### setShortestPathAlgorithm

          public void setShortestPathAlgorithm(ShortestPath spAlgorithm)

      Sets the default shortest path algorithm.
      Parameters:
      `spAlgorithm` -

    <!-- -->

    - #### getKShortestPathsAlgorithm

          public KShortestPaths getKShortestPathsAlgorithm()

      Returns the default k-shortest paths algorithm.
      Returns:

    <!-- -->

    - #### setKShortestPathsAlgorithm

          public void setKShortestPathsAlgorithm(KShortestPaths kspAlgorithm)

      Sets the default k-shortest paths algorithm.
      Parameters:
      `kspAlgorithm` -

    <!-- -->

    - #### getPairwiseShortestPathsAlgorithm

          public PairwiseShortestPaths getPairwiseShortestPathsAlgorithm()

      Returns the default pairwise shortest paths algorithm.
      Returns:

    <!-- -->

    - #### setPairwiseShortestPathsAlgorithm

          public void setPairwiseShortestPathsAlgorithm(PairwiseShortestPaths pwspAlgorithm)

      Sets the default pairwise shortest paths algorithm.
      Parameters:
      `pwspAlgorithm` -

    <!-- -->

    - #### getPairwiseCostCalculator

          public PairwiseCostCalculator getPairwiseCostCalculator()

      Returns the default pairwise cost calculator.
      Returns:

    <!-- -->

    - #### setPairwiseCostCalculator

          public void setPairwiseCostCalculator(PairwiseCostCalculator pwcc)

      Sets the default pairwise cost calculator.
      Parameters:
      `pwcc` -

    <!-- -->

    - #### getTspAlgorithm

          public TSP getTspAlgorithm()

      Returns the default TSP algorithm.
      Returns:

    <!-- -->

    - #### setTspAlgorithm

          public void setTspAlgorithm(TSP tspAlgorithm)

      Sets the default TSP algorithm.
      Parameters:
      `tspAlgorithm` -

    <!-- -->

    - #### resetCostCalculators

          public void resetCostCalculators()

      Restores the default settings of link cost calculators and node cost calculators, which uses the DefaultLinkCostCalculator as the primary link cost calculator and the DefaultNodeCostCalculator as the primary node cost calculator. No secondary cost calculators are set.

    <!-- -->

    - #### setLinkCostCalculator

          public void setLinkCostCalculator(LinkCostCalculator calculator)

      Sets the primary link cost calculator, and removes all secondary link cost calculators. The primary link cost calculator is used to calculate the objective cost during network analysis.
      Parameters:
      `calculator` - link cost calculator

    <!-- -->

    - #### getLinkCostCalculator

          public LinkCostCalculator getLinkCostCalculator()

      Returns the primary link cost calculator. The primary link cost calculator is used to calculate the objective cost during network analysis.
      Returns:
      link cost calculator

    <!-- -->

    - #### setNodeCostCalculator

          public void setNodeCostCalculator(NodeCostCalculator calculator)

      Sets the primary node cost calculator, and removes all secondary node cost calculators. The primary node cost calculator is used to calculate the objective cost during network analysis.
      Parameters:
      `calculator` - node cost calculator

    <!-- -->

    - #### getNodeCostCalculator

          public NodeCostCalculator getNodeCostCalculator()

      Returns the primary node cost calculator. The primary node cost calculator is used to calculate the objective cost during network analysis.
      Returns:
      node cost calculator

    <!-- -->

    - #### setLinkCostCalculators

          public void setLinkCostCalculators(LinkCostCalculator[] calculators)

      Sets the link cost calculators. The first element in the array is the primary link cost calculator, which is used in calculating the objective cost during network analysis. The rest of the elements in the the array are secondary cost calculators, which can be used in network constraints.
      Parameters:
      `calculators` - link cost calculators

    <!-- -->

    - #### getLinkCostCalculators

          public LinkCostCalculator[] getLinkCostCalculators()

      Returns the link cost calculators. The first element in the array is the primary link cost calculator, which is used in calculating the objective cost during network analysis. The rest of the elements in the the array are secondary cost calculators, which can be used in network constraints.
      Returns:
      link cost calculators

    <!-- -->

    - #### setNodeCostCalculators

          public void setNodeCostCalculators(NodeCostCalculator[] calculators)

      Sets the node cost calculators. The first element in the array is the primary node cost calculator, which is used in calculating the objective cost during network analysis. The rest of the elements in the the array are secondary cost calculators, which can be used in network constraints.
      Parameters:
      `calculators` - node cost calculators

    <!-- -->

    - #### getNodeCostCalculators

          public NodeCostCalculator[] getNodeCostCalculators()

      Returns the node cost calculators. The first element in the array is the primary node cost calculator, which is used in calculating the objective cost during network analysis. The rest of the elements in the the array are secondary cost calculators, which can be used in network constraints.
      Returns:
      node cost calculators

    <!-- -->

    - #### nearestNeighbors

          public LogicalSubPath[] nearestNeighbors(PointOnNet startPoint,
                                                   int numberOfNeighbors,
                                                   LODNetworkConstraint constraint,
                                                   LODGoalNode goalNodeFilter)
                                            throws LODNetworkException

      Finds the nearest neighbors from the start point. Both the search and the target link level are set to the lowest link level
      Parameters:
      `startPoint` - start point on the network

      `numberOfNeighbors` - number of neighbors to be returned

      `constraint` - network constraint

      `goalNodeFilter` - goal node implementation

      Returns:
      paths to the nearest neighbors from the start point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### nearestNeighbors

          public LogicalSubPath[] nearestNeighbors(PointOnNet startPoint,
                                                   int numberOfNeighbors,
                                                   int targetLinkLevel,
                                                   LODNetworkConstraint constraint,
                                                   LODGoalNode goalNodeFilter)
                                            throws LODNetworkException

      Finds the nearest neighbors from the start point. The search uses the lowest link level.
      Parameters:
      `startPoint` - start point on the network

      `numberOfNeighbors` - number of neighbors to be returned

      `targetLinkLevel` - maximum outgoing link level of the neighbors

      `constraint` - network constraint

      `goalNodeFilter` - goal node implementation

      Returns:
      paths to the nearest neighbors from the start point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### nearestNeighbors

          public LogicalSubPath[] nearestNeighbors(PointOnNet startPoint,
                                                   int numberOfNeighbors,
                                                   int searchLinkLevel,
                                                   int targetLinkLevel,
                                                   LODNetworkConstraint constraint,
                                                   LODGoalNode goalNodeFilter)
                                            throws LODNetworkException

      Finds the nearest neighbors from the start point.
      Parameters:
      `startPoint` - start point on the network

      `numberOfNeighbors` - number of neighbors to be returned

      `searchLinkLevel` - the link level to search for neighbors

      `targetLinkLevel` - maximum outgoing link level of the neighbors

      `constraint` - network constraint

      `goalNodeFilter` - goal node implementation

      Returns:
      paths to the nearest neighbors from the start point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### nearestNeighbors

          public LogicalSubPath[] nearestNeighbors(PointOnNet[] startPoints,
                                                   int numberOfNeighbors,
                                                   int searchLinkLevel,
                                                   int targetLinkLevel,
                                                   LODNetworkConstraint constraint,
                                                   LODGoalNode goalNodeFilter)
                                            throws LODNetworkException

      Finds the nearest neighbors from the start point candidates.
      Parameters:
      `startPoints` - start point candidates on the network

      `numberOfNeighbors` - number of neighbors to be returned

      `searchLinkLevel` - the link level to search for neighbors

      `targetLinkLevel` - maximum outgoing link level of the neighbors

      `constraint` - network constraint

      `goalNodeFilter` - goal node implementation

      Returns:
      paths to the nearest neighbors from the start point candidates

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### nearestNeighborsLight

          public LogicalLightSubPath[] nearestNeighborsLight(PointOnNet[] startPoints,
                                                             int numberOfNeighbors,
                                                             int searchLinkLevel,
                                                             int targetLinkLevel,
                                                             LODNetworkConstraint constraint,
                                                             LODGoalNode goalNodeFilter)
                                                      throws LODNetworkException

      Finds the nearest neighbors from the start point candidates.
      Parameters:
      `startPoints` - start point candidates on the network

      `numberOfNeighbors` - number of neighbors to be returned

      `searchLinkLevel` - the link level to search for neighbors

      `targetLinkLevel` - maximum outgoing link level of the neighbors

      `constraint` - network constraint

      `goalNodeFilter` - goal node implementation

      Returns:
      paths to the nearest neighbors from the start point candidates

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### nearestReachingNeighbors

          public LogicalSubPath[] nearestReachingNeighbors(PointOnNet endPoint,
                                                           int numberOfNeighbors,
                                                           LODNetworkConstraint constraint,
                                                           LODGoalNode goalNodeFilter)
                                                    throws LODNetworkException

      Finds the nearest reaching neighbors to the end point. Both the search and the target link levels are set to the lowest link level.
      Parameters:
      `endPoint` - end point on the network

      `numberOfNeighbors` - number of neighbors to be returned

      `constraint` - network constraint

      `goalNodeFilter` - goal node implementation

      Returns:
      paths from the nearest reaching neighbors to the end point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### nearestReachingNeighbors

          public LogicalSubPath[] nearestReachingNeighbors(PointOnNet endPoint,
                                                           int numberOfNeighbors,
                                                           int targetLinkLevel,
                                                           LODNetworkConstraint constraint,
                                                           LODGoalNode goalNodeFilter)
                                                    throws LODNetworkException

      Finds the nearest reaching neighbors to the end point. The search uses the lowest link level.
      Parameters:
      `endPoint` - end point on the network

      `numberOfNeighbors` - number of neighbors to be returned

      `targetLinkLevel` - maximum incoming link level of the neighbors

      `constraint` - network constraint

      `goalNodeFilter` - goal node implementation

      Returns:
      paths from the nearest reaching neighbors to the end point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### nearestReachingNeighbors

          public LogicalSubPath[] nearestReachingNeighbors(PointOnNet endPoint,
                                                           int numberOfNeighbors,
                                                           int searchLinkLevel,
                                                           int targetLinkLevel,
                                                           LODNetworkConstraint constraint,
                                                           LODGoalNode goalNodeFilter)
                                                    throws LODNetworkException

      Finds the nearest reaching neighbors to the end point.
      Parameters:
      `endPoint` - end point on the network

      `numberOfNeighbors` - number of neighbors to be returned

      `searchLinkLevel` - the preferred link level to search for neighbors

      `targetLinkLevel` - maximum incoming link level of the neighbors

      `constraint` - network constraint

      `goalNodeFilter` - goal node implementation

      Returns:
      paths from the nearest reaching neighbors to the end point candidates

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### nearestReachingNeighbors

          public LogicalSubPath[] nearestReachingNeighbors(PointOnNet[] endPoints,
                                                           int numberOfNeighbors,
                                                           int searchLinkLevel,
                                                           int targetLinkLevel,
                                                           LODNetworkConstraint constraint,
                                                           LODGoalNode goalNodeFilter)
                                                    throws LODNetworkException

      Finds the nearest reaching neighbors to the end point candidates.
      Parameters:
      `endPoints` - end point candidates on the network

      `numberOfNeighbors` - number of neighbors to be returned

      `searchLinkLevel` - the preferred link level to search for neighbors

      `targetLinkLevel` - maximum incoming link level of the neighbors

      `constraint` - network constraint

      `goalNodeFilter` - goal node implementation

      Returns:
      paths from the nearest reaching neighbors to the end point candidates

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### nearestReachingNeighborsLight

          public LogicalLightSubPath[] nearestReachingNeighborsLight(PointOnNet[] endPoints,
                                                                     int numberOfNeighbors,
                                                                     int searchLinkLevel,
                                                                     int targetLinkLevel,
                                                                     LODNetworkConstraint constraint,
                                                                     LODGoalNode goalNodeFilter)
                                                              throws LODNetworkException

      Finds the nearest reaching neighbors to the end point candidates.
      Parameters:
      `endPoints` - end point candidates on the network

      `numberOfNeighbors` - number of neighbors to be returned

      `searchLinkLevel` - the preferred link level to search for neighbors

      `targetLinkLevel` - maximum incoming link level of the neighbors

      `constraint` - network constraint

      `goalNodeFilter` - goal node implementation

      Returns:
      paths from the nearest reaching neighbors to the end point candidates

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### withinCost

          public LogicalSubPath[] withinCost(PointOnNet startPoint,
                                             double cost,
                                             LODNetworkConstraint constraint,
                                             LODGoalNode goalNodeFilter)
                                      throws LODNetworkException

      Finds the nodes within the given cost from the start point. Both the search and the target link levels are set to the lowest link level.
      Parameters:
      `startPoint` - start point

      `cost` - cost bound

      `constraint` - network constraint

      `goalNodeFilter` - goal node implementation

      Returns:
      paths to the target nodes from the start point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### withinCost

          public LogicalSubPath[] withinCost(PointOnNet startPoint,
                                             double cost,
                                             int targetLinkLevel,
                                             LODNetworkConstraint constraint,
                                             LODGoalNode goalNodeFilter)
                                      throws LODNetworkException

      Finds the nodes within the given cost from the start point. The search uses the lowest link level.
      Parameters:
      `startPoint` - start point

      `cost` - cost bound

      `targetLinkLevel` - maximum outgoing link level of the targets

      `constraint` - network constraint

      `goalNodeFilter` - goal node implementation

      Returns:
      paths to the target nodes from the start point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### withinCost

          public LogicalSubPath[] withinCost(PointOnNet startPoint,
                                             double cost,
                                             int searchLinkLevel,
                                             int targetLinkLevel,
                                             LODNetworkConstraint constraint,
                                             LODGoalNode goalNodeFilter)
                                      throws LODNetworkException

      Finds the nodes within the given cost from the start point.
      Parameters:
      `startPoint` - start point

      `cost` - cost bound

      `searchLinkLevel` - the link level to search for targets

      `targetLinkLevel` - maximum outgoing link level of the targets

      `constraint` - network constraint

      `goalNodeFilter` - goal node implementation

      Returns:
      paths to the target nodes from the start point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### withinCost

          public LogicalSubPath[] withinCost(PointOnNet[] startPoints,
                                             double cost,
                                             int searchLinkLevel,
                                             int targetLinkLevel,
                                             LODNetworkConstraint constraint,
                                             LODGoalNode goalNodeFilter,
                                             boolean returnBoundaryNodesOnly)
                                      throws LODNetworkException

      Finds the nodes within the given cost from the start point candidates.
      Parameters:
      `startPoints` - start point candidates

      `cost` - cost bound

      `searchLinkLevel` - the link level to search for targets

      `targetLinkLevel` - maximum outgoing link level of the targets

      `constraint` - network constraint

      `goalNodeFilter` - goal node implementation

      `returnBoundaryNodesOnly` - whether to return the boundary nodes only

      Returns:
      paths to the target nodes from the start point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### withinCostLight

          public LogicalLightSubPath[] withinCostLight(PointOnNet[] startPoints,
                                                       double cost,
                                                       int searchLinkLevel,
                                                       int targetLinkLevel,
                                                       LODNetworkConstraint constraint,
                                                       LODGoalNode goalNodeFilter,
                                                       boolean returnBoundaryNodesOnly)
                                                throws LODNetworkException

      Finds the nodes within the given cost from the start point candidates.
      Parameters:
      `startPoints` - start point candidates

      `cost` - cost bound

      `searchLinkLevel` - the link level to search for targets

      `targetLinkLevel` - maximum outgoing link level of the targets

      `constraint` - network constraint

      `goalNodeFilter` - goal node implementation

      `returnBoundaryNodesOnly` - whether to return the boundary nodes only

      Returns:
      paths to the target nodes from the start point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### withinReachingCost

          public LogicalSubPath[] withinReachingCost(PointOnNet endPoint,
                                                     double cost,
                                                     LODNetworkConstraint constraint,
                                                     LODGoalNode goalNodeFilter)
                                              throws LODNetworkException

      Finds the nodes within the given cost to the end point. Both the search and the target link levels are set to the lowest link level.
      Parameters:
      `endPoint` - end point

      `cost` - cost bound

      `constraint` - network constraint

      `goalNodeFilter` - goal node implementation

      Returns:
      paths from the target nodes to the end point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### withinReachingCost

          public LogicalSubPath[] withinReachingCost(PointOnNet endPoint,
                                                     double cost,
                                                     int targetLinkLevel,
                                                     LODNetworkConstraint constraint,
                                                     LODGoalNode goalNodeFilter)
                                              throws LODNetworkException

      Finds the nodes within the given cost to the end point. The search uses the lowest link level.
      Parameters:
      `endPoint` - end point

      `cost` - cost bound

      `targetLinkLevel` - maximum incoming link level of the targets

      `constraint` - network constraint

      `goalNodeFilter` - goal node implementation

      Returns:
      paths from the target nodes to the end point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### withinReachingCost

          public LogicalSubPath[] withinReachingCost(PointOnNet endPoint,
                                                     double cost,
                                                     int searchLinkLevel,
                                                     int targetLinkLevel,
                                                     LODNetworkConstraint constraint,
                                                     LODGoalNode goalNodeFilter)
                                              throws LODNetworkException

      Finds the nodes within the given cost to the end point.
      Parameters:
      `endPoint` - end point

      `cost` - cost bound

      `searchLinkLevel` - the link level to search for targets

      `targetLinkLevel` - maximum incoming link level of the targets

      `constraint` - network constraint

      `goalNodeFilter` - goal node implementation

      Returns:
      paths from the target nodes to the end point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### withinReachingCost

          public LogicalSubPath[] withinReachingCost(PointOnNet[] endPoints,
                                                     double cost,
                                                     int searchLinkLevel,
                                                     int targetLinkLevel,
                                                     LODNetworkConstraint constraint,
                                                     LODGoalNode goalNodeFilter,
                                                     boolean returnBoundaryNodesOnly)
                                              throws LODNetworkException

      Finds the nodes within the given cost to the end point candidates.
      Parameters:
      `endPoints` - end point candidates

      `cost` - cost bound

      `searchLinkLevel` - the link level to search for targets

      `targetLinkLevel` - maximum incoming link level of the targets

      `constraint` - network constraint

      `goalNodeFilter` - goal node implementation

      `returnBoundaryNodesOnly` - whether to return the boundary nodes only

      Returns:
      paths from the target nodes to the end point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### withinReachingCostLight

          public LogicalLightSubPath[] withinReachingCostLight(PointOnNet[] endPoints,
                                                               double cost,
                                                               int searchLinkLevel,
                                                               int targetLinkLevel,
                                                               LODNetworkConstraint constraint,
                                                               LODGoalNode goalNodeFilter,
                                                               boolean returnBoundaryNodesOnly)
                                                        throws LODNetworkException

      Finds the nodes within the given cost to the end points.
      Parameters:
      `endPoints` - end points

      `cost` - cost bound

      `searchLinkLevel` - the link level to search for targets

      `targetLinkLevel` - maximum incoming link level of the targets

      `constraint` - network constraint

      `goalNodeFilter` - goal node implementation

      `returnBoundaryNodesOnly` - whether to return the boundary nodes only

      Returns:
      paths from the target nodes to the end point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### fastWithinCostPolygon

          public JGeometry fastWithinCostPolygon(PointOnNet[] startPoints,
                                                 double cost,
                                                 LODNetworkConstraint constraint,
                                                 LODGoalNode goalNodeFilter)
                                          throws LODNetworkException

      Returns the polygon covering the nodes, links or partial links that are within the given cost from the start point candidates. X and Y of Node need to be predefined in UserData.
      Parameters:
      `startPoints` - start point candidates

      `cost` - cost range

      `constraint` - network constraint

      `goalNodeFilter` - goal node filter

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### fastWithinCostPolygon

          public JGeometry fastWithinCostPolygon(PointOnNet[] startPoints,
                                                 double cost,
                                                 LODNetworkConstraint constraint,
                                                 LODGoalNode goalNodeFilter,
                                                 boolean isLowAccuracy)
                                          throws LODNetworkException

      Returns the polygon covering the nodes, links or partial links that are within the given cost from the start point candidates. X and Y of Node need to be predefined in UserData.
      Parameters:
      `startPoints` - start point candidates

      `cost` - cost range

      `constraint` - network constraint

      `goalNodeFilter` - goal node filter

      `isLowAccuracy` - use low accuracy to improve 25% running time within 25% area error when driving cost is small(E.g. less than 1800s)

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### fastWithinReachingCostPolygon

          public JGeometry fastWithinReachingCostPolygon(PointOnNet[] endPoints,
                                                         double cost,
                                                         LODNetworkConstraint constraint,
                                                         LODGoalNode goalNodeFilter)
                                                  throws LODNetworkException

      Returns the polygon covering the nodes, links or partial links that are within the given cost to the end point candidates.
      Parameters:
      `endPoints` - end point candidates

      `cost` - cost range

      `constraint` - network constraint

      `goalNodeFilter` - goal node filter

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### fastWithinReachingCostPolygon

          public JGeometry fastWithinReachingCostPolygon(PointOnNet[] endPoints,
                                                         double cost,
                                                         LODNetworkConstraint constraint,
                                                         LODGoalNode goalNodeFilter,
                                                         boolean isLowAccuracy)
                                                  throws LODNetworkException

      Returns the polygon covering the nodes, links or partial links that are within the given cost to the end point candidates.
      Parameters:
      `endPoints` - end point candidates

      `cost` - cost range

      `constraint` - network constraint

      `goalNodeFilter` - goal node filter

      `isLowAccuracy` - use low accuracy to improve 25% running time within 25% area error when driving cost is small(E.g. less than 1800s)

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### withinCostPolygon

          public JGeometry withinCostPolygon(PointOnNet[] startPoints,
                                             double cost,
                                             LODNetworkConstraint constraint,
                                             LODGoalNode goalNodeFilter)
                                      throws LODNetworkException

      Returns the polygon covering the nodes, links or partial links that are within the given cost from the start point candidates.
      Parameters:
      `startPoints` - start point candidates

      `cost` - cost range

      `constraint` - network constraint

      `goalNodeFilter` - goal node filter

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### withinCostPolygon

          public JGeometry withinCostPolygon(PointOnNet[] startPoints,
                                             double cost,
                                             LODNetworkConstraint constraint,
                                             LODGoalNode goalNodeFilter,
                                             int accuracyLevel)
                                      throws LODNetworkException

      Returns the polygon covering the nodes, links or partial links that are within the given cost from the start point candidates.
      Parameters:
      `startPoints` - start point candidates

      `cost` - cost range

      `constraint` - network constraint

      `goalNodeFilter` - goal node filter

      `accuracyLevel` - Use one of the constants: ACCURACY_LEVEL_LOWEST, ACCURACY_LEVEL_LOW, ACCURACY_LEVEL_MEDIUM, ACCURACY_LEVEL_HIGH, or ACCURACY_LEVEL_HIGHEST.

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### withinReachingCostPolygon

          public JGeometry withinReachingCostPolygon(PointOnNet[] endPoints,
                                                     double cost,
                                                     LODNetworkConstraint constraint,
                                                     LODGoalNode goalNodeFilter)
                                              throws LODNetworkException

      Returns the polygon covering the nodes, links or partial links that are within the given cost to the end point candidates.
      Parameters:
      `endPoints` - end point candidates

      `cost` - cost range

      `constraint` - network constraint

      `goalNodeFilter` - goal node filter

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### withinReachingCostPolygon

          public JGeometry withinReachingCostPolygon(PointOnNet[] endPoints,
                                                     double cost,
                                                     LODNetworkConstraint constraint,
                                                     LODGoalNode goalNodeFilter,
                                                     int accuracyLevel)
                                              throws LODNetworkException

      Returns the polygon covering the nodes, links or partial links that are within the given cost to the end point candidates.
      Parameters:
      `endPoints` - end point candidates

      `cost` - cost range

      `constraint` - network constraint

      `goalNodeFilter` - goal node filter

      `accuracyLevel` - Use one of the constants: ACCURACY_LEVEL_LOWEST, ACCURACY_LEVEL_LOW, ACCURACY_LEVEL_MEDIUM, ACCURACY_LEVEL_HIGH, or ACCURACY_LEVEL_HIGHEST.

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### traceOut

          public LogicalSubPath[] traceOut(PointOnNet startPoint,
                                           double cost,
                                           LODNetworkConstraint constraint,
                                           LODGoalNode goalNodeFilter)
                                    throws LODNetworkException

      Finds the nodes and partial links within the given cost from the start point. Both the search and the target link levels are set to the lowest link level.
      Parameters:
      `startPoint` - start point

      `cost` - cost bound

      `constraint` - network constraint

      `goalNodeFilter` - goal node implementation

      Returns:
      paths to the target nodes and links from the start point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### traceOut

          public LogicalSubPath[] traceOut(PointOnNet startPoint,
                                           double cost,
                                           int targetLinkLevel,
                                           LODNetworkConstraint constraint,
                                           LODGoalNode goalNodeFilter)
                                    throws LODNetworkException

      Finds the nodes and partial links within the given cost from the start point. The search uses the lowest link level.
      Parameters:
      `startPoint` - start point

      `cost` - cost bound

      `targetLinkLevel` - maximum outgoing link level of the targets

      `constraint` - network constraint

      `goalNodeFilter` - goal node implementation

      Returns:
      paths to the target nodes and links from the start point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### traceOut

          public LogicalSubPath[] traceOut(PointOnNet startPoint,
                                           double cost,
                                           int searchLinkLevel,
                                           int targetLinkLevel,
                                           LODNetworkConstraint constraint,
                                           LODGoalNode goalNodeFilter)
                                    throws LODNetworkException

      Finds the nodes and partial links within the given cost from the start point.
      Parameters:
      `startPoint` - start point

      `cost` - cost bound

      `searchLinkLevel` - the link level to search on

      `targetLinkLevel` - maximum outgoing link level of the targets

      `constraint` - network constraint

      `goalNodeFilter` - goal node implementation

      Returns:
      paths to the target nodes and links from the start point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### traceOut

          public LogicalSubPath[] traceOut(PointOnNet[] startPoints,
                                           double cost,
                                           int searchLinkLevel,
                                           int targetLinkLevel,
                                           LODNetworkConstraint constraint,
                                           LODGoalNode goalNodeFilter,
                                           boolean returnBoundaryPointsOnly)
                                    throws LODNetworkException

      Finds the nodes and partial links within the given cost from the start point candidates.
      Parameters:
      `startPoints` - start points

      `cost` - cost bound

      `searchLinkLevel` - the link level to search on

      `targetLinkLevel` - maximum outgoing link level of the targets

      `constraint` - network constraint

      `goalNodeFilter` - goal node implementation

      `returnBoundaryPointsOnly` - whether to return boundary points only

      Returns:
      paths to the target nodes and links from the start point candidates

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### traceOutLight

          public LogicalLightSubPath[] traceOutLight(PointOnNet[] startPoints,
                                                     double cost,
                                                     int searchLinkLevel,
                                                     int targetLinkLevel,
                                                     LODNetworkConstraint constraint,
                                                     LODGoalNode goalNodeFilter,
                                                     boolean returnBoundaryPointsOnly)
                                              throws LODNetworkException

      Finds the nodes and partial links within the given cost from the start points.
      Parameters:
      `startPoints` - start points

      `cost` - cost bound

      `searchLinkLevel` - the link level to search on

      `targetLinkLevel` - maximum outgoing link level of the targets

      `constraint` - network constraint

      `goalNodeFilter` - goal node implementation

      `returnBoundaryPointsOnly` - whether to return boundary points only

      Returns:
      paths to the target nodes and links from the start point candidates

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### traceIn

          public LogicalSubPath[] traceIn(PointOnNet endPoint,
                                          double cost,
                                          LODNetworkConstraint constraint,
                                          LODGoalNode goalNodeFilter)
                                   throws LODNetworkException

      Finds the nodes and partial links within the given cost to the end point. Both the search and the target link levels are set to the lowest link level.
      Parameters:
      `endPoint` - end point

      `cost` - cost bound

      `constraint` - network constraint

      `goalNodeFilter` - goal node implementation

      Returns:
      paths from the target nodes and links to the start point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### traceIn

          public LogicalSubPath[] traceIn(PointOnNet endPoint,
                                          double cost,
                                          int targetLinkLevel,
                                          LODNetworkConstraint constraint,
                                          LODGoalNode goalNodeFilter)
                                   throws LODNetworkException

      Finds the nodes and partial links within the given cost to the end point. The search uses the lowest link level.
      Parameters:
      `endPoint` - end point

      `cost` - cost bound

      `targetLinkLevel` - maximum incoming link level of the targets

      `constraint` - network constraint

      `goalNodeFilter` - goal node implementation

      Returns:
      paths from the target nodes and links to the start point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### traceIn

          public LogicalSubPath[] traceIn(PointOnNet endPoint,
                                          double cost,
                                          int searchLinkLevel,
                                          int targetLinkLevel,
                                          LODNetworkConstraint constraint,
                                          LODGoalNode goalNodeFilter)
                                   throws LODNetworkException

      Finds the nodes and partial links within the given cost to the end point.
      Parameters:
      `endPoint` - end point

      `cost` - cost bound

      `searchLinkLevel` - the link level to search on

      `targetLinkLevel` - maximum incoming link level of the targets

      `constraint` - network constraint

      `goalNodeFilter` - goal node implementation

      Returns:
      paths from the target nodes and links to the end point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### traceIn

          public LogicalSubPath[] traceIn(PointOnNet[] endPoints,
                                          double cost,
                                          int searchLinkLevel,
                                          int targetLinkLevel,
                                          LODNetworkConstraint constraint,
                                          LODGoalNode goalNodeFilter,
                                          boolean returnBoundaryPointsOnly)
                                   throws LODNetworkException

      Finds the nodes and partial links within the given cost to the end point candidates.
      Parameters:
      `endPoints` - end point candidates

      `cost` - cost bound

      `searchLinkLevel` - the link level to search on

      `targetLinkLevel` - maximum incoming link level of the targets

      `constraint` - network constraint

      `goalNodeFilter` - goal node implementation

      `returnBoundaryPointsOnly` - whether to return boundary points only

      Returns:
      paths from the target nodes and links to the end point candidates

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### traceInLight

          public LogicalLightSubPath[] traceInLight(PointOnNet[] startPoints,
                                                    double cost,
                                                    int searchLinkLevel,
                                                    int targetLinkLevel,
                                                    LODNetworkConstraint constraint,
                                                    LODGoalNode goalNodeFilter,
                                                    boolean returnBoundaryPointsOnly)
                                             throws LODNetworkException

      Finds the nodes and partial links within the given cost to the end point candidates.
      Parameters:
      `startPoints` - start point candidates

      `cost` - cost bound

      `searchLinkLevel` - the link level to search on

      `targetLinkLevel` - maximum outgoing link level of the targets

      `constraint` - network constraint

      `goalNodeFilter` - goal node implementation

      `returnBoundaryPointsOnly` - whether to return boundary points only

      Returns:
      paths to the target nodes and links from the end point candidates

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### findConnectedNodes

          public OrderedLongSet findConnectedNodes(int searchMethod,
                                                   long nodeId,
                                                   int linkLevel,
                                                   LODNetworkConstraint constraint,
                                                   LODGoalNode goalNode)
                                            throws LODNetworkException

      Deprecated. use `findConnectedNodes(int, PointOnNet[], int, LODNetworkConstraint, LODGoalNode)`
      Finds the nodes connected to the given node.
      Parameters:
      `searchMethod` - search method. It can take the following values:

      NetworkAnalyst.BREADTH_FIRST_SEARCH, or

      NetworkAnalyst.DEPTH_FIRST_SEARCH.

      `nodeId` - node ID

      `linkLevel` - link level to search on

      Returns:
      node IDs connected to the given node

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### findConnectedNodes

          public OrderedLongSet findConnectedNodes(int searchMethod,
                                                   PointOnNet[] points,
                                                   int linkLevel,
                                                   LODNetworkConstraint constraint,
                                                   LODGoalNode goalNode)
                                            throws LODNetworkException

      Finds the nodes connected to the given points.
      Parameters:
      `searchMethod` - search method. It can take the following values:

      NetworkAnalyst.BREADTH_FIRST_SEARCH, or

      NetworkAnalyst.DEPTH_FIRST_SEARCH.

      `points` -

      `linkLevel` - link level to search on

      `constraint` -

      `goalNode` -

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### findReachableNodes

          public OrderedLongSet findReachableNodes(int searchMethod,
                                                   long startNodeId,
                                                   int linkLevel,
                                                   LODNetworkConstraint constraint,
                                                   LODGoalNode goalNode)
                                            throws LODNetworkException

      Deprecated. use `findReachableNodes(int, PointOnNet[], int, LODNetworkConstraint, LODGoalNode)`
      Finds the nodes reachable from the given node.
      Parameters:
      `searchMethod` - search method. It can take the following values:

      NetworkAnalyst.BREADTH_FIRST_SEARCH, or

      NetworkAnalyst.DEPTH_FIRST_SEARCH.

      `startNodeId` - start node ID

      `linkLevel` - link level to search on

      Returns:
      node IDs reachable from the given node ID

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### findReachableNodes

          public OrderedLongSet findReachableNodes(int searchMethod,
                                                   PointOnNet[] startPoints,
                                                   int linkLevel,
                                                   LODNetworkConstraint constraint,
                                                   LODGoalNode goalNode)
                                            throws LODNetworkException

      Finds the nodes reachable from the given points.
      Parameters:
      `searchMethod` - search method. It can take the following values:

      NetworkAnalyst.BREADTH_FIRST_SEARCH, or

      NetworkAnalyst.DEPTH_FIRST_SEARCH.

      `startPoints` - start points

      Returns:
      node IDs reachable from the given node

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### findReachingNodes

          public OrderedLongSet findReachingNodes(int searchMethod,
                                                  long endNodeId,
                                                  int linkLevel,
                                                  LODNetworkConstraint constraint,
                                                  LODGoalNode goalNode)
                                           throws LODNetworkException

      Deprecated. use `findReachingNodes(int, PointOnNet[], int, LODNetworkConstraint, LODGoalNode)`
      Finds the nodes that can reach the given node.
      Parameters:
      `searchMethod` - search method. It can take the following values:

      NetworkAnalyst.BREADTH_FIRST_SEARCH, or

      NetworkAnalyst.DEPTH_FIRST_SEARCH.

      `endNodeId` - end node ID

      `linkLevel` - maximum link level to search on

      Returns:
      node IDs that can reach the given node ID

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### findReachingNodes

          public OrderedLongSet findReachingNodes(int searchMethod,
                                                  PointOnNet[] endPoints,
                                                  int linkLevel,
                                                  LODNetworkConstraint constraint,
                                                  LODGoalNode goalNode)
                                           throws LODNetworkException

      Finds the nodes that can reach the given points.
      Parameters:
      `searchMethod` - search method. It can take the following values:

      NetworkAnalyst.BREADTH_FIRST_SEARCH, or

      NetworkAnalyst.DEPTH_FIRST_SEARCH.

      `endPoints` - end points

      `linkLevel` - link level to search on

      Returns:
      node IDs that can reach the given node ID

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### isReachable

          public boolean isReachable(long startNodeId,
                                     long endNodeId,
                                     int linkLevel,
                                     LODNetworkConstraint constraint)
                              throws LODNetworkException

      Checks whether there is a path from the start node to the end node using the given link level for long-haul search.
      Parameters:
      `startNodeId` - start node ID

      `endNodeId` - end node ID

      `linkLevel` - maximum link level to search on

      Returns:
      true, if there exists a path from the start node to the end node; false, otherwise.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### isReachable

          public boolean isReachable(PointOnNet[] startPoints,
                                     PointOnNet[] endPoints,
                                     int linkLevel,
                                     LODNetworkConstraint constraint)
                              throws LODNetworkException

      Checks whether there is a path from the start node to the end node using the given link level for long-haul search.
      Parameters:
      `startPoints` - start points

      `endPoints` - end points

      `linkLevel` - maximum link level to search on

      Returns:
      true, if there exists a path from the start node to the end node; false, otherwise.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### findConnectedComponents

          public OrderedLongSet[] findConnectedComponents(int linkLevel)
                                                   throws LODNetworkException

      Finds the connected components for the given link level.
      Parameters:
      `linkLevel` - maximum link level to search on

      Returns:
      the connected components

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### findConnectedComponentsInPartition

          public int findConnectedComponentsInPartition(int partitionId,
                                                        int linkLevel,
                                                        int startComponentId,
                                                        java.util.ArrayList<oracle.spatial.network.lod.AnalysisUtility.NodeComponent> nodeComponentArray)
                                                 throws LODNetworkException

      Find the connected components within a partition, with all the external nodes and boundary links included. This method writes the node id - component id assignment information into the input array, and returns the maximum component ID that has been used so far.
      Parameters:
      `partitionId` - ID of the partition in which the connected component is computed

      `linkLevel` - link level on which the connected component is computed

      `startComponentId` - start component ID to be used. All component IDs being assigned to the nodes in the partition must be no smaller than the start component ID.

      `nodeComponentArray` - empty list where the result node ID - component ID pair is written into

      Returns:
      the maximum component ID that has been used so far.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### shortestPath

          public LogicalSubPath shortestPath(PointOnNet[] startPoints,
                                             PointOnNet[] endPoints,
                                             LODNetworkConstraint constraint,
                                             ShortestPath algorithm)
                                      throws LODNetworkException

      Finds the shortest path using the input algorithm.
      Parameters:
      `startPoints` - start point candidates on the network

      `endPoints` - end point on candidates the network

      `constraint` - network constraint

      `algorithm` - shortest path algorithm, such as Dijkstra or A\*

      Returns:
      shortest path from the start point to the end point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### reverseShortestPath

          public LogicalSubPath reverseShortestPath(PointOnNet[] endPoints,
                                                    PointOnNet[] startPoints,
                                                    LODNetworkConstraint constraint,
                                                    ShortestPath algorithm)
                                             throws LODNetworkException

      Finds the shortest path using the input algorithm, using reverse search direction.
      Parameters:
      `startPoints` - start point candidates on the network

      `endPoints` - end point on candidates the network

      `constraint` - network constraint

      `algorithm` - shortest path algorithm, such as Dijkstra or A\*

      Returns:
      shortest path from the start point to the end point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### shortestPathDijkstra

          public LogicalSubPath shortestPathDijkstra(PointOnNet startPoint,
                                                     PointOnNet endPoint,
                                                     LODNetworkConstraint constraint)
                                              throws LODNetworkException

      Finds the shortest path on the minimum link level using Dijkstra algorithm.
      Parameters:
      `startPoint` - start point on the network

      `endPoint` - end point on the network

      `constraint` - network constraint

      Returns:
      shortest path from the start point to the end point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### shortestPathDijkstraMaxLevel

          public LogicalSubPath shortestPathDijkstraMaxLevel(PointOnNet startPoint,
                                                             PointOnNet endPoint,
                                                             LODNetworkConstraint constraint)
                                                      throws LODNetworkException

      Finds the shortest path using Dijkstra algorithm where the long-haul path is computed on the maximum link level.
      Parameters:
      `startPoint` - start point

      `endPoint` - end point

      `constraint` - network constraint

      Returns:
      shortest path from the start node to the end node

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### shortestPathDijkstra

          public LogicalSubPath shortestPathDijkstra(PointOnNet startPoint,
                                                     PointOnNet endPoint,
                                                     int searchLinkLevel,
                                                     LODNetworkConstraint constraint)
                                              throws LODNetworkException

      Finds the shortest path using Dijkstra algorithm where the long-haul path is computed on the given link level.
      Parameters:
      `startPoint` - start point on the network

      `endPoint` - end point on the network

      `constraint` - network constraint

      Returns:
      shortest path from the start point to the end point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### shortestPathDijkstra

          public LogicalSubPath shortestPathDijkstra(PointOnNet[] startPoints,
                                                     PointOnNet[] endPoints,
                                                     int searchLinkLevel,
                                                     LODNetworkConstraint constraint)
                                              throws LODNetworkException

      Finds the shortest path using Dijkstra algorithm where the long-haul path is computed on the given link level.
      Parameters:
      `startPoints` - candidate start points on the network

      `endPoints` - candidate end points on the network

      `constraint` - network constraint

      Returns:
      shortest path from the start point to the end point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### shortestPathDijkstra

          public LogicalSubPath shortestPathDijkstra(PointOnNet[] startPoints,
                                                     PointOnNet[] endPoints,
                                                     int searchLinkLevel,
                                                     int maxHighLevelNodesToConsider,
                                                     LODNetworkConstraint constraint)
                                              throws LODNetworkException

      Finds the shortest path using Dijkstra algorithm where the long-haul path is computed on the given link level.
      Parameters:
      `startPoints` - candidate start points on the network

      `endPoints` - candidate end points on the network

      `constraint` - network constraint

      Returns:
      shortest path from the start point to the end point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### shortestPathDijkstra

          public LogicalSubPath shortestPathDijkstra(PointOnNet[] startPoints,
                                                     PointOnNet[] endPoints,
                                                     LODNetworkConstraint constraint,
                                                     LinkLevelSelector lls)
                                              throws LODNetworkException

      Finds the shortest path using Dijkstra algorithm with the given link level selector.
      Parameters:
      `startPoints` - candidate start points on the network

      `endPoints` - candidate end points on the network

      `constraint` -

      `lls` -

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### shortestPathAStar

          public LogicalSubPath shortestPathAStar(PointOnNet startPoint,
                                                  PointOnNet endPoint,
                                                  LODNetworkConstraint constraint,
                                                  HeuristicCostFunction hcf,
                                                  double[] costThresholds)
                                           throws LODNetworkException

      Finds the shortest path using A\* algorithm using dynamic link level selector. The prefered search link level of the dynamic link level selector is set to the maximum link level of the network.
      Parameters:
      `startPoint` - start point on the network

      `endPoint` - end point on the network

      `constraint` - network constraint

      `hcf` - Heuristic cost function implementation

      Returns:
      shortest path from the start point to the end point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### shortestPathAStar

          public LogicalSubPath shortestPathAStar(PointOnNet startPoint,
                                                  PointOnNet endPoint,
                                                  int searchLinkLevel,
                                                  LODNetworkConstraint constraint,
                                                  HeuristicCostFunction hcf,
                                                  double[] costThresholds)
                                           throws LODNetworkException

      Finds the shortest path using A\* algorithm with dynamic link level selector.
      Parameters:
      `startPoint` - start point on the network

      `endPoint` - end point on the network

      `searchLinkLevel` - prefered link level to compute long-haul path

      `constraint` - network constraint

      `hcf` - Heuristic cost function implementation

      Returns:
      shortest path from the start point to the end point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### shortestPathAStar

          public LogicalSubPath shortestPathAStar(PointOnNet startPoint,
                                                  PointOnNet endPoint,
                                                  LODNetworkConstraint constraint,
                                                  HeuristicCostFunction hcf,
                                                  LinkLevelSelector lls)
                                           throws LODNetworkException

      Finds the shortest path using A\* algorithm.
      Parameters:
      `startPoint` - start point on the network

      `endPoint` - end point on the network

      `constraint` - network constraint

      `hcf` - Heuristic cost function implementation

      `lls` - link level selector to be used in A\* algorithm

      Returns:
      shortest path from the start point to the end point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### shortestPathAStar

          public LogicalSubPath shortestPathAStar(PointOnNet[] startPoints,
                                                  PointOnNet[] endPoints,
                                                  LODNetworkConstraint constraint,
                                                  HeuristicCostFunction hcf,
                                                  LinkLevelSelector lls)
                                           throws LODNetworkException

      Finds the shortest path using A\* algorithm.
      Parameters:
      `startPoints` - start point candidates on the network

      `endPoints` - end point on candidates the network

      `constraint` - network constraint

      `hcf` - Heuristic cost function implementation

      `lls` - link level selector to be used in A\* algorithm

      Returns:
      shortest path from the start point to the end point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### shortestPathHierarchical

          public LogicalSubPath shortestPathHierarchical(PointOnNet[] startPoints,
                                                         PointOnNet[] endPoints,
                                                         int searchLinkLevel,
                                                         int maxHighLevelNodesToConsider,
                                                         LODNetworkConstraint constraint,
                                                         ShortestPath algorithm)
                                                  throws LODNetworkException

      Finds the shortest path from the start point candidates to the end point candidates. This method takes advantage of multi-leveled network, by routing the start/end points to the nearest higher level network, and then navigate on the higher level network only.
      Parameters:
      `startPoints` - start point candidates on the network

      `endPoints` - end point candidates on the network

      `maxHighLevelNodesToConsider` - maximum high level nodes to consider

      `constraint` - network constraint

      `algorithm` - basic single-level shortest path algorithm, such as Dijkstra or A\*.

      Returns:
      shortest path from the start point candidates to the end point candidates

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### mst

          public SpanningTree mst(int linkLevel,
                                  LODNetworkConstraint constraint)
                           throws LODNetworkException

      Returns the minimum-spanning-tree for the network on the given link level.
      Parameters:
      `linkLevel` - link level

      Returns:
      the minimum-spanning-tree

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### mst

          public SpanningTree mst(int linkLevel,
                                  LODNetworkConstraint constraint,
                                  MinimumSpanningTree algorithm)
                           throws LODNetworkException

      Returns the minimum-spanning-tree for the network on the given link level.
      Parameters:
      `linkLevel` -

      `constraint` -

      `algorithm` -

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### mcst

          public long[] mcst(int linkLevel,
                             LODNetworkConstraint constraint)
                      throws LODNetworkException

      Deprecated. use `mst(int, LODNetworkConstraint, MinimumSpanningTree)`
      Returns the link IDs of the minimum-spanning-tree.
      Parameters:
      `linkLevel` - link level

      Returns:
      link IDs of the minimum-spanning-tree

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### mcst

          public long[] mcst(int linkLevel,
                             LODNetworkConstraint constraint,
                             NetworkUpdate tmpNetworkUpdate)
                      throws LODNetworkException

      Deprecated. use `mst(int, LODNetworkConstraint, MinimumSpanningTree)`
      Returns the link IDs of the minimum-spanning-tree.
      Parameters:
      `linkLevel` - link level

      `tmpNetworkUpdate` - temporary network update. This parameter is ignored. Please use the setNetworkUpdates(...) method to set dynamic network updates instead.

      Returns:
      link IDs of the minimum-spanning-tree

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### tsp

          public TspPath tsp(PointOnNet[][] pointsToVisit,
                             TSP.TourFlag tourFlag,
                             int linkLevel,
                             LODNetworkConstraint constraint)
                      throws LODNetworkException

      Returns the traveling salesman tour covering the given points.
      Parameters:
      `pointsToVisit` - points to visit on the tour

      `tourFlag` - a flag indicating whether the tour should be open or closed, and if the tour is open, whether the tour should have fixed start or end point.

      `constraint` - network constraint

      Returns:
      traveling salesman tour

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### tsp

          public TspPath tsp(PointOnNet[][] pointsToVisit,
                             TSP.TourFlag tourFlag,
                             int linkLevel,
                             LODNetworkConstraint constraint,
                             TSP algorithm)
                      throws LODNetworkException

      Returns the traveling salesman tour covering the input points.
      Parameters:
      `pointsToVisit` - points to visit on the tour.

      `tourFlag` - a flag indicating whether the tour should be open or closed, and if the tour is open, whether the tour should have fixed start or end point.

      `constraint` - network constraint

      `algorithm` - tsp algorithm

      Returns:
      traveling salesman tour

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### tsp

          public TspPath tsp(PointOnNet[][] pointsToVisit,
                             TSP.TourFlag tourFlag,
                             LODNetworkConstraint networkConstraint)
                      throws LODNetworkException

      Returns the traveling salesman tour covering the input points.
      Parameters:
      `pointsToVisit` - points to visit on the tour

      `tourFlag` - a flag indicating whether the tour should be open or closed, and if the tour is open, whether the tour should have fixed start or end point.

      `networkConstraint` - network constraint

      Returns:
      traveling salesman tour

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### tsp

          public TspPath tsp(PointOnNet[][] pointsToVisit,
                             TSP.TourFlag tourFlag,
                             LODNetworkConstraint networkConstraint,
                             TspConstraint tspConstraint)
                      throws LODNetworkException

      Returns the traveling salesman tour covering the input points.
      Parameters:
      `pointsToVisit` - points to visit on the tour

      `tourFlag` - a flag indicating whether the tour should be open or closed, and if the tour is open, whether the tour should have fixed start or end point.

      `networkConstraint` - network constraint

      `tspConstraint` - TSP constraint

      Returns:
      traveling salesman tour

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### tsp

          public TspPath tsp(PointOnNet[][] pointsToVisit,
                             TSP.TourFlag tourFlag,
                             LODNetworkConstraint networkConstraint,
                             TSP algorithm)
                      throws LODNetworkException

      Returns the traveling salesman tour covering the input points.
      Parameters:
      `pointsToVisit` - points to visit on the tour.

      `tourFlag` - a flag indicating whether the tour should be open or closed, and if the tour is open, whether the tour should have fixed start or end point.

      `networkConstraint` - network constraint

      `algorithm` - tsp algorithm

      Returns:
      traveling salesman tour

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### tsp

          public TspPath tsp(PointOnNet[][] pointsToVisit,
                             TSP.TourFlag tourFlag,
                             LODNetworkConstraint networkConstraint,
                             TspConstraint tspConstraint,
                             TSP algorithm)
                      throws LODNetworkException

      Returns the traveling salesman tour covering the input points.
      Parameters:
      `pointsToVisit` - points to visit on the tour.

      `tourFlag` - a flag indicating whether the tour should be open or closed, and if the tour is open, whether the tour should have fixed start or end point.

      `networkConstraint` - network constraint

      `algorithm` - tsp algorithm

      Returns:
      traveling salesman tour

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### kShortestPaths

          public LogicalSubPath[] kShortestPaths(PointOnNet[] startPoint,
                                                 PointOnNet[] endPoint,
                                                 int k,
                                                 LODNetworkConstraint constraint)
                                          throws LODNetworkException

      Returns K shortest loopless paths from the start point candidates to the end point candidates.
      Parameters:
      `startPoint` - start point candidates

      `endPoint` - end point candidates

      `k` - number of loopless paths to be returned

      `constraint` - network constraint

      Returns:
      K shortest loopless paths from the start point to the end point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### kShortestPathsBfs

          public LogicalSubPath[] kShortestPathsBfs(PointOnNet[] startPoint,
                                                    PointOnNet[] endPoint,
                                                    int k,
                                                    double maxToMinBound,
                                                    long timeout,
                                                    LODNetworkConstraint constraint,
                                                    PathFilter pathFilter)
                                             throws LODNetworkException

      Returns K shortest loopless paths from the start point candidates to the end point candidates.
      Parameters:
      `startPoint` - start point candidates

      `endPoint` - end point candidates

      `k` - number of loopless paths to be returned

      `constraint` - network constraint

      Returns:
      K shortest loopless paths from the start point to the end point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### kShortestPathsDijkstra

          public LogicalSubPath[] kShortestPathsDijkstra(PointOnNet[] startPoint,
                                                         PointOnNet[] endPoint,
                                                         int k,
                                                         double maxToMinBound,
                                                         long timeout,
                                                         LODNetworkConstraint constraint,
                                                         PathFilter pathFilter)
                                                  throws LODNetworkException

      Returns K shortest paths from the start point candidates to the end point candidates.
      Parameters:
      `startPoint` - start point candidates

      `endPoint` - end point candidates

      `k` - number of loopless paths to be returned

      `constraint` - network constraint

      Returns:
      K shortest loopless paths from the start point to the end point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### reverseKShortestPathsBfs

          public LogicalSubPath[] reverseKShortestPathsBfs(PointOnNet[] startPoint,
                                                           PointOnNet[] endPoint,
                                                           int k,
                                                           double maxToMinBound,
                                                           long timeout,
                                                           LODNetworkConstraint constraint,
                                                           PathFilter pathFilter)
                                                    throws LODNetworkException

      Returns K shortest loopless paths from the start point candidates to the end point candidates.
      Parameters:
      `startPoint` - start point candidates

      `endPoint` - end point candidates

      `k` - number of loopless paths to be returned

      `constraint` - network constraint

      Returns:
      K shortest loopless paths from the start point to the end point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### reverseKShortestPathsDijkstra

          public LogicalSubPath[] reverseKShortestPathsDijkstra(PointOnNet[] startPoint,
                                                                PointOnNet[] endPoint,
                                                                int k,
                                                                double maxToMinBound,
                                                                long timeout,
                                                                LODNetworkConstraint constraint,
                                                                PathFilter pathFilter)
                                                         throws LODNetworkException

      Returns K shortest loopless paths from the start point candidates to the end point candidates.
      Parameters:
      `startPoint` - start point candidates

      `endPoint` - end point candidates

      `k` - number of loopless paths to be returned

      `constraint` - network constraint

      Returns:
      K shortest loopless paths from the start point to the end point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### kShortestPaths

          public LogicalSubPath[] kShortestPaths(PointOnNet[] startPoint,
                                                 PointOnNet[] endPoint,
                                                 int k,
                                                 LODNetworkConstraint constraint,
                                                 KShortestPaths kspAlgorithm)
                                          throws LODNetworkException

      Returns K shortest loopless paths from the start point candiates to the end point candidates.
      Parameters:
      `startPoint` - start point candidates

      `endPoint` - end point candidates

      `k` - number of loopless paths to be returned

      `constraint` - network constraint

      `kspAlgorithm` - K-shortest paths algorithm

      Returns:
      K shortest loopless paths from the start point to the end point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### kShortestPaths

          public LogicalSubPath[] kShortestPaths(PointOnNet[] startPoint,
                                                 PointOnNet[] endPoint,
                                                 int k,
                                                 LODNetworkConstraint constraint,
                                                 PathFilter pathFilter,
                                                 KShortestPaths kspAlgorithm)
                                          throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### reverseKShortestPaths

          public LogicalSubPath[] reverseKShortestPaths(PointOnNet[] endPoint,
                                                        PointOnNet[] startPoint,
                                                        int k,
                                                        LODNetworkConstraint constraint)
                                                 throws LODNetworkException

      Returns K shortest loopless paths from the start point candidates to the end point candidates, using reverse search direction.
      Parameters:
      `startPoint` - start point candidates

      `endPoint` - end point candidates

      `k` - number of loopless paths to be returned

      `constraint` - network constraint

      Returns:
      K shortest loopless paths from the start point to the end point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### reverseKShortestPaths

          public LogicalSubPath[] reverseKShortestPaths(PointOnNet[] endPoint,
                                                        PointOnNet[] startPoint,
                                                        int k,
                                                        LODNetworkConstraint constraint,
                                                        KShortestPaths kspAlgorithm)
                                                 throws LODNetworkException

      Returns reverse K shortest loopless paths from the start point candiates to the end point candidates, using reverse search direction.
      Parameters:
      `startPoint` - start point candidates

      `endPoint` - end point candidates

      `k` - number of loopless paths to be returned

      `constraint` - network constraint

      `kspAlgorithm` - K-shortest paths algorithm

      Returns:
      K shortest loopless paths from the start point to the end point

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### reverseKShortestPaths

          public LogicalSubPath[] reverseKShortestPaths(PointOnNet[] endPoint,
                                                        PointOnNet[] startPoint,
                                                        int k,
                                                        LODNetworkConstraint constraint,
                                                        PathFilter pathFilter,
                                                        KShortestPaths kspAlgorithm)
                                                 throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### networkBuffer

          public NetworkBuffer networkBuffer(PointOnNet[] startPoints,
                                             double cost,
                                             LODNetworkConstraint constraint)
                                      throws LODNetworkException

      Computes network buffer within the given cost from the start point candidates.
      Parameters:
      `startPoints` - start point candidates

      `cost` - cost range of the network buffer

      `constraint` - network constraint

      Returns:
      network buffer within the given cost from the start point candidates

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### reachingNetworkBuffer

          public NetworkBuffer reachingNetworkBuffer(PointOnNet[] endPoints,
                                                     double cost,
                                                     LODNetworkConstraint constraint)
                                              throws LODNetworkException

      Computes network buffer within the given cost to the end point candidates.
      Parameters:
      `endPoints` - end point candidates

      `cost` - cost range of the network buffer

      `constraint` - network constraint

      Returns:
      network buffer within the given cost to the end point candidates

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### allDetourShortestPathsWithCostLimit

          public LogicalSubPath[] allDetourShortestPathsWithCostLimit(PointOnNet[] startPoints,
                                                                      PointOnNet[] endPoints,
                                                                      double maxCost,
                                                                      LODNetworkConstraint constraint)
                                                               throws LODNetworkException

      Finds all paths from the start points to the end points with the following properties:
      The cost of the path is smaller than or equal to the given cost bound
      The subpath from the start points to any intermediate node on the path is the shortest possible path from the start points to that node.
      The subpath from any intermediate node to the end points is the shortest possible path from that node to the end points.
      Parameters:
      `startPoints` - start point candidates

      `endPoints` - end point candidates

      `maxCost` - cost bound

      `constraint` - network constraint

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### allDetourShortestPathsWithDepthLimit

          public LogicalSubPath[] allDetourShortestPathsWithDepthLimit(PointOnNet[] startPoints,
                                                                       PointOnNet[] endPoints,
                                                                       int maxDepth,
                                                                       LODNetworkConstraint constraint)
                                                                throws LODNetworkException

      Finds all paths from the start points to the end points with the following properties:
      The depth of the path is smaller than or equal to the given depth bound
      The subpath from the start points to any intermediate node on the path is the shortest possible path from the start points to that node.
      The subpath from any intermediate node to the end points is the shortest possible path from that node to the end points.
      Parameters:
      `startPoints` - start point candidates

      `endPoints` - end point candidates

      `maxDepth` - depth bound

      `constraint` - network constraint

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### shortestPath

          public PathFeature shortestPath(Feature[] start,
                                          Feature[] end,
                                          LODNetworkConstraint constraint,
                                          ShortestPath algorithm)
                                   throws LODNetworkException

      Finds the shortest path from the start feature candidates to the end feature candidates. The start feature candidates and the end feature candidates can belong to different feature layers. If there are more than one start or end feature candidates, it returns the shortest path among all candidate paths.
      Parameters:
      `start` - start feature candidates

      `end` - end feature candidates

      `constraint` - network constraint

      `algorithm` - shortest path algorithm

      Returns:
      a PathFeature object representing the shortest path from the start feature(s) to the end feature(s).

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### shortestPathAStar

          public PathFeature shortestPathAStar(Feature[] start,
                                               Feature[] end,
                                               LODNetworkConstraint constraint,
                                               HeuristicCostFunction hcf,
                                               LinkLevelSelector lls)
                                        throws LODNetworkException

      Finds the shortest path from the start feature candidates to the end feature candidates. The start feature candidates and the end feature candidates can belong to different feature layers. If there are more than one start or end feature candidates, it returns the shortest path among all candidate paths.
      Parameters:
      `start` - start feature candidates

      `end` - end feature candidates

      `constraint` - network constraint

      `hcf` - heuristic cost function

      `lls` - link level selector

      Returns:
      a PathFeature object representing the shortest path from the start feature(s) to the end feature(s).

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### shortestPathDijkstra

          public PathFeature shortestPathDijkstra(Feature[] start,
                                                  Feature[] end,
                                                  LODNetworkConstraint constraint,
                                                  LinkLevelSelector lls)
                                           throws LODNetworkException

      Finds the shortest path from the start feature candidates to the end feature candidates. The start feature candidates and the end feature candidates can belong to different feature layers. If there are more than one start or end feature candidates, it returns the shortest path among all candidate paths.
      Parameters:
      `start` - start feature candidates

      `end` - end feature candidates

      `constraint` - network constraint

      `lls` - link level selector

      Returns:
      a PathFeature object representing the shortest path from the start feature(s) to the end feature(s).

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### kShortestPaths

          public PathFeature[] kShortestPaths(Feature[] start,
                                              Feature[] end,
                                              int k,
                                              LODNetworkConstraint constraint,
                                              KShortestPaths algorithm)
                                       throws LODNetworkException

      Finds the top k shortest paths from the start feature candidates to the end feature candidates. The start feature candidates and the end feature candidates can belong to different feature layers. If there are more than one start or end feature candidates, it returns the top k shortest paths among all candidate paths.
      Parameters:
      `start` - start feature candidates

      `end` - end feature candidates

      `k` - number of paths to return

      `constraint` - network constraint

      `algorithm` - shortest path algorithm

      Returns:
      a PathFeature object representing the shortest path from the start feature(s) to the end feature(s).

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### reverseKShortestPaths

          public PathFeature[] reverseKShortestPaths(Feature[] end,
                                                     Feature[] start,
                                                     int k,
                                                     LODNetworkConstraint constraint,
                                                     KShortestPaths algorithm)
                                              throws LODNetworkException

      Finds the top k shortest paths from the start feature candidates to the end feature candidates, using reverse search direction. The start feature candidates and the end feature candidates can belong to different feature layers. If there are more than one start or end feature candidates, it returns the top k shortest paths among all candidate paths.
      Parameters:
      `end` - end feature candidates

      `start` - start feature candidates

      `k` - number of paths to return

      `constraint` - network constraint

      `algorithm` - shortest path algorithm

      Returns:
      a PathFeature object representing the shortest path from the start feature(s) to the end feature(s).

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### reverseShortestPath

          public PathFeature reverseShortestPath(Feature[] end,
                                                 Feature[] start,
                                                 LODNetworkConstraint constraint,
                                                 ShortestPath algorithm)
                                          throws LODNetworkException

      Finds the shortest path from the start feature candidates to the end feature candidates, using reverse search direction. The start feature candidates and the end feature candidates can belong to different feature layers. If there are more than one start or end feature candidates, it returns the shortest path among all candidate paths.
      Parameters:
      `start` - start feature candidates

      `end` - end feature candidates

      `constraint` - network constraint

      `algorithm` - shortest path algorithm

      Returns:
      a PathFeature object representing the shortest path from the start feature(s) to the end feature(s).

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### nearestPoints

          public PathToPoint[] nearestPoints(PointOnNet[] startPoints,
                                             PointOnNet[][] targetPoints,
                                             int k,
                                             LODNetworkConstraint constraint,
                                             boolean returnFullPath)
                                      throws LODNetworkException

      Returns the top k nearest target points from the start points.
      Parameters:
      `startPoints` - start point candidates

      `targetPoints` - target points to choose from

      `k` - number of points to be returned

      `constraint` -

      `returnFullPath` - whether to return full paths to the target points or the light weight paths.

      Returns:
      The top k nearest points among the specified target points and the paths to those points.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### nearestReachingPoints

          public PathToPoint[] nearestReachingPoints(PointOnNet[] startPoints,
                                                     PointOnNet[][] targetPoints,
                                                     int k,
                                                     LODNetworkConstraint constraint,
                                                     boolean returnFullPath)
                                              throws LODNetworkException

      Returns the top k nearest reaching target points to the start points.
      Parameters:
      `startPoints` - start point candidates

      `targetPoints` - target points to choose from

      `k` - number of points to be returned

      `constraint` -

      `returnFullPath` - whether to return full paths to the target points or the light weight paths.

      Returns:
      The top k nearest points among the specified target points and the paths to those points.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### withinCostPoints

          public PathToPoint[] withinCostPoints(PointOnNet[] startPoints,
                                                PointOnNet[][] targetPoints,
                                                double cost,
                                                LODNetworkConstraint constraint,
                                                boolean returnFullPath)
                                         throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### withinReachingCostPoints

          public PathToPoint[] withinReachingCostPoints(PointOnNet[] startPoints,
                                                        PointOnNet[][] targetPoints,
                                                        double cost,
                                                        LODNetworkConstraint constraint,
                                                        boolean returnFullPath)
                                                 throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### nearestFeatures

          public FeaturePath[] nearestFeatures(Feature[] start,
                                               int numberOfFeatures,
                                               int[] featureLayerIds,
                                               LODNetworkConstraint constraint,
                                               FeatureFilter featureFilter)
                                        throws LODNetworkException

      Finds the nearest features from the start feature candidates. If there are more than one start feature candidates, it returns the nearest features to any of the start features.
      Parameters:
      `start` - start feature candidates

      `numberOfFeatures` - number of features to return

      `featureLayerIds` - feature layer IDs

      `constraint` - network constraint

      Returns:
      PathFeature objects representing the shortest paths from a start feature to the nearest neighbors.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### nearestFeatures

          public FeaturePath[] nearestFeatures(PointOnNet[] startPoints,
                                               int numberOfFeatures,
                                               int[] featureLayerIds,
                                               LODNetworkConstraint constraint,
                                               FeatureFilter featureFilter)
                                        throws LODNetworkException

      Finds the nearest features from the start point candidates. If there are more than one start point candidates, it returns the nearest features from any of the start points.
      Parameters:
      `startPoints` - start point candidates

      `numberOfFeatures` - number of features to return

      `featureLayerIds` - feature layer IDs

      `constraint` - network constraint

      Returns:
      PathFeature objects representing the shortest paths from a start point to the nearest neighbors.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### nearestReachingFeatures

          public FeaturePath[] nearestReachingFeatures(Feature[] end,
                                                       int numberOfFeatures,
                                                       int[] featureLayerIds,
                                                       LODNetworkConstraint constraint,
                                                       FeatureFilter featureFilter)
                                                throws LODNetworkException

      Finds the nearest reaching features to the end feature candidates. If there are more than one end feature candidates, it returns the nearest features to any of the end features.
      Parameters:
      `end` - end feature candidates

      `numberOfFeatures` - number of features to return

      `featureLayerIds` - feature layer IDs

      `constraint` - network constraint

      Returns:
      PathFeature objects representing the shortest paths from the nearest neighbors to an end feature.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### nearestReachingFeatures

          public FeaturePath[] nearestReachingFeatures(PointOnNet[] endPoints,
                                                       int numberOfFeatures,
                                                       int[] featureLayerIds,
                                                       LODNetworkConstraint constraint,
                                                       FeatureFilter featureFilter)
                                                throws LODNetworkException

      Finds the nearest reaching features to the end point candidates. If there are more than one end point candidates, it returns the nearest features to any of the end points.
      Parameters:
      `endPoints` - end point candidates

      `numberOfFeatures` - number of features to return

      `featureLayerIds` - feature layer IDs

      `constraint` - network constraint

      Returns:
      PathFeature objects representing the shortest paths from the nearest neighbors to an end points.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### withinCostFeatures

          public FeaturePath[] withinCostFeatures(Feature[] start,
                                                  double cost,
                                                  int[] featureLayerIds,
                                                  LODNetworkConstraint constraint,
                                                  FeatureFilter featureFilter)
                                           throws LODNetworkException

      Finds features within the given cost from the start features.
      Parameters:
      `start` - start feature candidates

      `cost` - cost range

      `featureLayerIds` - feature layer IDs

      `constraint` - network constraint

      Returns:
      PathFeature objects representing the shortest paths from a start feature to the features within the given cost.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### withinCostFeatures

          public FeaturePath[] withinCostFeatures(PointOnNet[] startPoints,
                                                  double cost,
                                                  int[] featureLayerIds,
                                                  LODNetworkConstraint constraint,
                                                  FeatureFilter featureFilter)
                                           throws LODNetworkException

      Finds features within the given cost from the start features.
      Parameters:
      `startPoints` - start point candidates

      `cost` - cost range

      `featureLayerIds` - feature layer IDs

      `constraint` - network constraint

      Returns:
      PathFeature objects representing the shortest paths from a start point to the features within the given cost.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### withinReachingCostFeatures

          public FeaturePath[] withinReachingCostFeatures(Feature[] endFeatures,
                                                          double cost,
                                                          int[] featureLayerIds,
                                                          LODNetworkConstraint constraint,
                                                          FeatureFilter featureFilter)
                                                   throws LODNetworkException

      Finds features within the given cost to the end features.
      Parameters:
      `endFeatures` - end feature candidates

      `cost` - cost range

      `featureLayerIds` - feature layer IDs

      `constraint` - network constraint

      Returns:
      PathFeature objects representing the shortest paths from the features within the given cost to an end feature.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### withinReachingCostFeatures

          public FeaturePath[] withinReachingCostFeatures(PointOnNet[] endPoints,
                                                          double cost,
                                                          int[] featureLayerIds,
                                                          LODNetworkConstraint constraint,
                                                          FeatureFilter featureFilter)
                                                   throws LODNetworkException

      Finds features within the given cost to the end features.
      Parameters:
      `endPoints` - end point candidates

      `cost` - cost range

      `featureLayerIds` - feature layer IDs

      `constraint` - network constraint

      Returns:
      PathFeature objects representing the shortest paths from the features within the given cost to an end point.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### withinCostPolygon

          public JGeometry withinCostPolygon(Feature[] startFeatures,
                                             double cost,
                                             LODNetworkConstraint constraint,
                                             LODGoalNode goalNodeFilter)
                                      throws LODNetworkException

      Returns the polygon covering the nodes, links or partial links that are within the given cost from the start feature candidates.
      Parameters:
      `startFeatures` - start feature candidates

      `cost` - cost range

      `constraint` - network constraint

      `goalNodeFilter` - goal node filter

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### withinReachingCostPolygon

          public JGeometry withinReachingCostPolygon(Feature[] endFeatures,
                                                     double cost,
                                                     LODNetworkConstraint constraint,
                                                     LODGoalNode goalNodeFilter)
                                              throws LODNetworkException

      Returns the polygon covering the nodes, links or partial links that are within the given cost to the end feature candidates.
      Parameters:
      `endFeatures` - end feature candidates

      `cost` - cost range

      `constraint` - network constraint

      `goalNodeFilter` - goal node filter

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### tsp

          public TspPathFeature tsp(Feature[][] featuresToVisit,
                                    TSP.TourFlag tourFlag,
                                    LODNetworkConstraint constraint,
                                    TSP algorithm)
                             throws LODNetworkException

      Returns the traveling salesman tour covering the input features.
      Parameters:
      `featuresToVisit` - features to visit on the tour.

      `tourFlag` - a flag indicating whether the tour should be open or closed, and if the tour is open, whether the tour should have fixed start or end point.

      `constraint` - network constraint

      `algorithm` - tsp algorithm

      Returns:
      traveling salesman tour

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### tsp

          public TspPathFeature tsp(Feature[][] featuresToVisit,
                                    TSP.TourFlag tourFlag,
                                    LODNetworkConstraint networkConstraint,
                                    TspConstraint tspConstraint,
                                    TSP algorithm)
                             throws LODNetworkException

      Returns the traveling salesman tour covering the input features.
      Parameters:
      `featuresToVisit` - features to visit on the tour.

      `tourFlag` - a flag indicating whether the tour should be open or closed, and if the tour is open, whether the tour should have fixed start or end point.

      `networkConstraint` - network constraint

      `tspConstraint` - tsp constraint

      `algorithm` - tsp algorithm

      Returns:
      traveling salesman tour

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### isReachable

          public boolean isReachable(Feature[] start,
                                     Feature[] end,
                                     int linkLevel,
                                     LODNetworkConstraint constraint)
                              throws LODNetworkException

      Checks whether there is a path from the start features to the end features using the given link level for long-haul search.
      Parameters:
      `start` - start feature candidates

      `end` - end feature candidates

      `linkLevel` - maximum link level to search on

      Returns:
      true, if there exists a path from the start features to the end features; false, otherwise.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### findReachableFeatures

          public Feature[] findReachableFeatures(int searchMethod,
                                                 PointOnNet[] startPoints,
                                                 int linkLevel,
                                                 int[] featureLayerIds,
                                                 LODNetworkConstraint constraint,
                                                 FeatureFilter featureFilter)
                                          throws LODNetworkException

      Finds the nodes reachable from the given node.
      Parameters:
      `searchMethod` - search method. It can take the following values:

      NetworkAnalyst.BREADTH_FIRST_SEARCH, or

      NetworkAnalyst.DEPTH_FIRST_SEARCH.

      `startPoints` - start points

      Returns:
      node IDs reachable from the given node

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### findReachingFeatures

          public Feature[] findReachingFeatures(int searchMethod,
                                                PointOnNet[] startPoints,
                                                int linkLevel,
                                                int[] featureLayerIds,
                                                LODNetworkConstraint constraint,
                                                FeatureFilter featureFilter)
                                         throws LODNetworkException

      Finds the nodes that can reach the given node.
      Parameters:
      `searchMethod` - search method. It can take the following values:

      NetworkAnalyst.BREADTH_FIRST_SEARCH, or

      NetworkAnalyst.DEPTH_FIRST_SEARCH.

      `startPoints` - start points

      Returns:
      node IDs reachable from the given node

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### bisectClustering

          public ClusterResult bisectClustering(PointOnNet[] points,
                                                int numClusters,
                                                int userDataCategory,
                                                int xCoordUserDataIndex,
                                                int yCoordUserDataIndex,
                                                int geometryUserDataIndex)
                                         throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### kMeansClustering

          public ClusterResult kMeansClustering(PointOnNet[] points,
                                                int numClusters,
                                                int maxSize,
                                                int minSize,
                                                int userDataCategory,
                                                int xCoordUserDataIndex,
                                                int yCoordUserDataIndex,
                                                int geometryUserDataIndex)
                                         throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### vrpNoDepot

          public TspPath[] vrpNoDepot(PointOnNet[][] points,
                                      int numVehicles,
                                      LODNetworkConstraint networkConstraint,
                                      TspConstraint tspConstraint,
                                      VRP vrpAlgo)
                               throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### vrpSingleDepot

          public TspPath[] vrpSingleDepot(PointOnNet[][] points,
                                          int numVehicles,
                                          PointOnNet[] depot,
                                          LODNetworkConstraint networkConstraint,
                                          TspConstraint tspConstraint,
                                          VRP vrpAlgo)
                                   throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### vrpNoDepot

          public TspPath[] vrpNoDepot(PointOnNet[][] points,
                                      int numVehicles,
                                      LODNetworkConstraint networkConstraint,
                                      TspConstraint tspConstraint,
                                      int userDataCategory,
                                      int xUserDataIndex,
                                      int yUserDataIndex,
                                      int geometryUserDataIndex)
                               throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### vrpSingleDepot

          public TspPath[] vrpSingleDepot(PointOnNet[][] points,
                                          int numVehicles,
                                          PointOnNet[] depot,
                                          LODNetworkConstraint networkConstraint,
                                          TspConstraint tspConstraint,
                                          int userDataCategory,
                                          int xUserDataIndex,
                                          int yUserDataIndex,
                                          int geometryUserDataIndex)
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

- [Prev Class](MinimumSpanningTree.md)
- [Next Class](NetworkBuffer.md)

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
