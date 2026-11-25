Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Tree
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev](../package-tree.md)
-

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

# Hierarchy For Package oracle.spatial.network.lod

Package Hierarchies:

- [All Packages](../../../../overview-tree.md)

## Class Hierarchy

- java.lang.Object
  - oracle.spatial.network.lod.[AnalysisEngine](AnalysisEngine.md)
  - oracle.spatial.network.lod.[AnalysisEngine.DefaultCallable](AnalysisEngine.DefaultCallable.md) (implements java.util.concurrent.Callable\<V\>)
  - oracle.spatial.network.lod.[BidirectionalBfs](BidirectionalBfs.md) (implements oracle.spatial.network.lod.[ShortestPath](ShortestPath.md))
    - oracle.spatial.network.lod.[BidirectionalDijkstra](BidirectionalDijkstra.md) (implements oracle.spatial.network.lod.[ShortestPath](ShortestPath.md))
  - oracle.spatial.network.lod.[BinaryHeap](BinaryHeap.md)\<E\> (implements oracle.spatial.network.lod.[PriorityQueue](PriorityQueue.md)\<E\>)
  - oracle.spatial.network.lod.[CategorizedUserDataImpl](CategorizedUserDataImpl.md) (implements oracle.spatial.network.lod.[CategorizedUserData](CategorizedUserData.md), java.io.Serializable)
  - oracle.spatial.network.lod.[ClusterSizeConstraint](ClusterSizeConstraint.md) (implements oracle.spatial.network.lod.[ClusteringConstraint](ClusteringConstraint.md))
  - oracle.spatial.network.lod.[ConstraintOperator](ConstraintOperator.md)
  - oracle.spatial.network.lod.[DefaultLinkCostCalculator](DefaultLinkCostCalculator.md) (implements oracle.spatial.network.lod.[LinkCostCalculator](LinkCostCalculator.md))
  - oracle.spatial.network.lod.[DefaultNodeCostCalculator](DefaultNodeCostCalculator.md) (implements oracle.spatial.network.lod.[NodeCostCalculator](NodeCostCalculator.md))
  - oracle.spatial.network.lod.[DefaultPairwiseCostCalculator](DefaultPairwiseCostCalculator.md) (implements oracle.spatial.network.lod.[PairwiseCostCalculator](PairwiseCostCalculator.md), oracle.spatial.network.lod.[XMLConfigurable](XMLConfigurable.md))
  - oracle.spatial.network.lod.[DefaultPairwiseShortestPaths](DefaultPairwiseShortestPaths.md) (implements oracle.spatial.network.lod.[PairwiseShortestPaths](PairwiseShortestPaths.md), oracle.spatial.network.lod.[XMLConfigurable](XMLConfigurable.md))
  - oracle.spatial.network.lod.[DefaultSingleSourceShortestPaths](DefaultSingleSourceShortestPaths.md) (implements oracle.spatial.network.lod.[SingleSourceShortestPaths](SingleSourceShortestPaths.md))
  - oracle.spatial.network.lod.[DummyCostFunction](DummyCostFunction.md) (implements oracle.spatial.network.lod.[HeuristicCostFunction](HeuristicCostFunction.md))
  - oracle.spatial.network.lod.[DummyLinkCostCalculator](DummyLinkCostCalculator.md) (implements oracle.spatial.network.lod.[LinkCostCalculator](LinkCostCalculator.md))
  - oracle.spatial.network.lod.[DummyLinkLevelSelector](DummyLinkLevelSelector.md) (implements oracle.spatial.network.lod.[LinkLevelSelector](LinkLevelSelector.md))
  - oracle.spatial.network.lod.[DummyNodeCostCalculator](DummyNodeCostCalculator.md) (implements oracle.spatial.network.lod.[NodeCostCalculator](NodeCostCalculator.md))
  - oracle.spatial.network.lod.[DynamicLinkLevelSelector](DynamicLinkLevelSelector.md) (implements oracle.spatial.network.lod.[LinkLevelSelector](LinkLevelSelector.md), oracle.spatial.network.lod.[XMLConfigurable](XMLConfigurable.md))
  - oracle.spatial.network.lod.[EuclideanCostFunction](EuclideanCostFunction.md) (implements oracle.spatial.network.lod.[HeuristicCostFunction](HeuristicCostFunction.md), oracle.spatial.network.lod.[XMLConfigurable](XMLConfigurable.md))
  - oracle.spatial.network.lod.[FeatureDataImpl](FeatureDataImpl.md) (implements oracle.spatial.network.lod.[FeatureData](FeatureData.md))
  - oracle.spatial.network.lod.[FeatureElementImpl](FeatureElementImpl.md) (implements oracle.spatial.network.lod.[FeatureElement](FeatureElement.md))
  - oracle.spatial.network.lod.[FeatureFilterOperator](FeatureFilterOperator.md)
  - oracle.spatial.network.lod.[FeatureImpl](FeatureImpl.md) (implements oracle.spatial.network.lod.[Feature](Feature.md))
    - oracle.spatial.network.lod.[PathFeatureImpl](PathFeatureImpl.md) (implements oracle.spatial.network.lod.[PathFeature](PathFeature.md))
  - oracle.spatial.network.lod.[FeatureLayerImpl](FeatureLayerImpl.md) (implements oracle.spatial.network.lod.[FeatureLayer](FeatureLayer.md))
  - oracle.spatial.network.lod.[FeatureLayerMetadata](FeatureLayerMetadata.md)
  - oracle.spatial.network.lod.[FeatureMetadata](FeatureMetadata.md)
  - oracle.spatial.network.lod.[FeaturePath](FeaturePath.md) (implements java.lang.Comparable\<T\>)
  - oracle.spatial.network.lod.[FilePairwisePathResultIO](FilePairwisePathResultIO.md) (implements oracle.spatial.network.lod.[PairwisePathResultIO](PairwisePathResultIO.md))
  - oracle.spatial.network.lod.[GeodeticCostFunction](GeodeticCostFunction.md) (implements oracle.spatial.network.lod.[HeuristicCostFunction](HeuristicCostFunction.md), oracle.spatial.network.lod.[XMLConfigurable](XMLConfigurable.md))
  - oracle.spatial.network.lod.[GeodeticPairwiseCostCalculator](GeodeticPairwiseCostCalculator.md) (implements oracle.spatial.network.lod.[PairwiseCostCalculator](PairwiseCostCalculator.md), oracle.spatial.network.lod.[XMLConfigurable](XMLConfigurable.md))
  - oracle.spatial.network.lod.[GoalNodeOperator](GoalNodeOperator.md)
  - oracle.spatial.network.lod.[IdentifiableBinaryHeap](IdentifiableBinaryHeap.md)\<E\> (implements oracle.spatial.network.lod.[IdentifiablePriorityQueue](IdentifiablePriorityQueue.md)\<E\>)
  - oracle.spatial.network.lod.[InMemoryPairwisePathResultIO](InMemoryPairwisePathResultIO.md) (implements oracle.spatial.network.lod.[PairwisePathResultIO](PairwisePathResultIO.md))
  - oracle.spatial.network.lod.[LeveledNetworkCache](LeveledNetworkCache.md)
  - oracle.spatial.network.lod.[LODAnalysisInfo](LODAnalysisInfo.md)
    - oracle.spatial.network.lod.[TspAnalysisInfo](TspAnalysisInfo.md)
  - oracle.spatial.network.lod.[LODNetworkFactory](LODNetworkFactory.md)
  - oracle.spatial.network.lod.[LODNetworkManager](LODNetworkManager.md)
  - oracle.spatial.network.lod.[LODNetworkWrapper](LODNetworkWrapper.md)
  - oracle.spatial.network.lod.[LODUserDataIOSDO](LODUserDataIOSDO.md) (implements oracle.spatial.network.lod.[LODUserDataIO](LODUserDataIO.md))
  - oracle.spatial.network.lod.[LogicalNetLinkImpl](LogicalNetLinkImpl.md) (implements oracle.spatial.network.lod.[LogicalNetLink](LogicalNetLink.md))
  - oracle.spatial.network.lod.[LogicalNetNodeImpl](LogicalNetNodeImpl.md) (implements oracle.spatial.network.lod.[LogicalNetNode](LogicalNetNode.md))
  - oracle.spatial.network.lod.[LogicalPartitionImpl](LogicalPartitionImpl.md) (implements oracle.spatial.network.lod.[LogicalPartition](LogicalPartition.md))
  - oracle.spatial.network.lod.[LogicalSubPathImpl](LogicalSubPathImpl.md) (implements oracle.spatial.network.lod.[LogicalSubPath](LogicalSubPath.md))
    - oracle.spatial.network.lod.[SpatialSubPathImpl](SpatialSubPathImpl.md) (implements oracle.spatial.network.lod.[SpatialSubPath](SpatialSubPath.md))
  - oracle.spatial.network.lod.[LongHashMap](LongHashMap.md)\<V\>
    - oracle.spatial.network.lod.[LongLinkedHashMap](LongLinkedHashMap.md)\<V\>
  - oracle.spatial.network.lod.[LongHashSet](LongHashSet.md)
  - oracle.spatial.network.lod.[LRUCachingHandler](LRUCachingHandler.md) (implements oracle.spatial.network.lod.[CachingHandler](CachingHandler.md))
  - oracle.spatial.network.lod.[Matrix](Matrix.md)\<E\>
  - oracle.spatial.network.lod.[MaxCostConstraint](MaxCostConstraint.md) (implements oracle.spatial.network.lod.[LODNetworkConstraint](LODNetworkConstraint.md))
  - oracle.spatial.network.lod.[MaxDepthConstraint](MaxDepthConstraint.md) (implements oracle.spatial.network.lod.[LODNetworkConstraint](LODNetworkConstraint.md))
  - oracle.spatial.network.lod.[NetworkAnalyst](NetworkAnalyst.md)
  - oracle.spatial.network.lod.[NetworkBuffer](NetworkBuffer.md)
  - oracle.spatial.network.lod.[NetworkBuffer.DoubleInterval](NetworkBuffer.DoubleInterval.md)
  - oracle.spatial.network.lod.[NetworkBuffer.Elements](NetworkBuffer.Elements.md)
  - oracle.spatial.network.lod.[NetworkBuffer.LinkInterval](NetworkBuffer.LinkInterval.md)
  - oracle.spatial.network.lod.[NetworkBuffer.LinkIntervals](NetworkBuffer.LinkIntervals.md)
  - oracle.spatial.network.lod.[NetworkExplorer](NetworkExplorer.md)
  - oracle.spatial.network.lod.[NetworkSearch](NetworkSearch.md)
    - oracle.spatial.network.lod.[BreadthFirstSearch](BreadthFirstSearch.md) (implements oracle.spatial.network.lod.[ShortestPath](ShortestPath.md))
      - oracle.spatial.network.lod.[AStar](AStar.md) (implements oracle.spatial.network.lod.[ShortestPath](ShortestPath.md), oracle.spatial.network.lod.[XMLConfigurable](XMLConfigurable.md))
      - oracle.spatial.network.lod.[Dijkstra](Dijkstra.md) (implements oracle.spatial.network.lod.[ShortestPath](ShortestPath.md), oracle.spatial.network.lod.[SingleSourceShortestPaths](SingleSourceShortestPaths.md), oracle.spatial.network.lod.[XMLConfigurable](XMLConfigurable.md))
      - oracle.spatial.network.lod.[KShortestPathsBfs](KShortestPathsBfs.md) (implements oracle.spatial.network.lod.[KShortestPaths](KShortestPaths.md))
  - oracle.spatial.network.lod.[NetworkUpdate](NetworkUpdate.md)
  - oracle.spatial.network.lod.[OrderedLongSet](OrderedLongSet.md) (implements java.lang.Cloneable)
  - oracle.spatial.network.lod.[ParallelPairwiseShortestPaths](ParallelPairwiseShortestPaths.md) (implements oracle.spatial.network.lod.[PairwiseShortestPaths](PairwiseShortestPaths.md))
  - oracle.spatial.network.lod.[PartitionBlob](PartitionBlob.md)
  - oracle.spatial.network.lod.[PartitionBlobTranslator11g](PartitionBlobTranslator11g.md) (implements oracle.spatial.network.lod.[PartitionBlobTranslator](PartitionBlobTranslator.md))
  - oracle.spatial.network.lod.[PartitionBlobTranslator11gR2](PartitionBlobTranslator11gR2.md) (implements oracle.spatial.network.lod.[PartitionBlobTranslator](PartitionBlobTranslator.md))
  - oracle.spatial.network.lod.[PartitionUpdate](PartitionUpdate.md)
  - oracle.spatial.network.lod.[PathToPoint](PathToPoint.md) (implements java.lang.Comparable\<T\>)
  - oracle.spatial.network.lod.[PointOnNet](PointOnNet.md)
    - oracle.spatial.network.lod.[HeavyPointOnNet](HeavyPointOnNet.md)
  - oracle.spatial.network.lod.[SilhouetteClusterEvaluator](SilhouetteClusterEvaluator.md) (implements oracle.spatial.network.lod.[ClusterEvaluator](ClusterEvaluator.md))
  - oracle.spatial.network.lod.[SpanningTree](SpanningTree.md)
  - oracle.spatial.network.lod.[SpatialBisectClustering](SpatialBisectClustering.md) (implements oracle.spatial.network.lod.[PointClustering](PointClustering.md))
  - oracle.spatial.network.lod.[SpatialKMeansClustering](SpatialKMeansClustering.md) (implements oracle.spatial.network.lod.[PointClustering](PointClustering.md))
  - java.lang.Throwable (implements java.io.Serializable)
    - java.lang.Exception
      - oracle.spatial.network.lod.[LODNetworkException](LODNetworkException.md)
        - oracle.spatial.network.lod.[LinkNotFoundException](LinkNotFoundException.md)
        - oracle.spatial.network.lod.[MethodNotSupportedException](MethodNotSupportedException.md)
        - oracle.spatial.network.lod.[NodeNotFoundException](NodeNotFoundException.md)
  - oracle.spatial.network.lod.[TimeWindow](TimeWindow.md)
  - oracle.spatial.network.lod.[Tsp2Opt](Tsp2Opt.md) (implements oracle.spatial.network.lod.[TspOptimizer](TspOptimizer.md))
  - oracle.spatial.network.lod.[TspConstraintOperator](TspConstraintOperator.md)
  - oracle.spatial.network.lod.[TspConstraintOperator.CombinedConstraint](TspConstraintOperator.CombinedConstraint.md) (implements oracle.spatial.network.lod.[TspConstraint](TspConstraint.md))
  - oracle.spatial.network.lod.[TspImpl](TspImpl.md) (implements oracle.spatial.network.lod.[TSP](TSP.md))
    - oracle.spatial.network.lod.[TspOp2](TspOp2.md) (implements oracle.spatial.network.lod.[TSP](TSP.md), oracle.spatial.network.lod.[XMLConfigurable](XMLConfigurable.md))
  - oracle.spatial.network.lod.[TspImpl.NetworkTspConstraint](TspImpl.NetworkTspConstraint.md) (implements oracle.spatial.network.lod.[TspConstraint](TspConstraint.md))
  - oracle.spatial.network.lod.[TspNearestNeighbor](TspNearestNeighbor.md) (implements oracle.spatial.network.lod.[TSP](TSP.md))
  - oracle.spatial.network.lod.[TspOrderConstraint](TspOrderConstraint.md) (implements oracle.spatial.network.lod.[TspConstraint](TspConstraint.md))
  - oracle.spatial.network.lod.[TspPath](TspPath.md)
  - oracle.spatial.network.lod.[TspPathFeature](TspPathFeature.md)
  - oracle.spatial.network.lod.[TspTimeWindowConstraint](TspTimeWindowConstraint.md) (implements oracle.spatial.network.lod.[TspConstraint](TspConstraint.md))
  - oracle.spatial.network.lod.[UserDataImpl](UserDataImpl.md) (implements java.io.Serializable, oracle.spatial.network.lod.[UserData](UserData.md))
  - oracle.spatial.network.lod.[VisitedNode](VisitedNode.md) (implements java.lang.Comparable\<T\>, oracle.spatial.network.lod.[Identifiable](Identifiable.md))
  - oracle.spatial.network.lod.[VrpClusterAndRoute](VrpClusterAndRoute.md) (implements oracle.spatial.network.lod.[VRP](VRP.md))
  - oracle.spatial.network.lod.[VrpPath](VrpPath.md)
  - oracle.spatial.network.lod.[YenDeviation](YenDeviation.md) (implements oracle.spatial.network.lod.[KShortestPaths](KShortestPaths.md), oracle.spatial.network.lod.[XMLConfigurable](XMLConfigurable.md))

## Interface Hierarchy

- oracle.spatial.network.lod.[CachingHandler](CachingHandler.md)
- java.lang.Cloneable
  - oracle.spatial.network.lod.[FeatureElement](FeatureElement.md)
  - oracle.spatial.network.lod.[LogicalBasicNetwork](LogicalBasicNetwork.md)
    - oracle.spatial.network.lod.[LogicalSubNetwork](LogicalSubNetwork.md)
      - oracle.spatial.network.lod.[LogicalPartition](LogicalPartition.md)
        - oracle.spatial.network.lod.[SpatialPartition](SpatialPartition.md)
      - oracle.spatial.network.lod.[SpatialSubNetwork](SpatialSubNetwork.md)
    - oracle.spatial.network.lod.[SpatialBasicNetwork](SpatialBasicNetwork.md)
- oracle.spatial.network.lod.[Cluster](Cluster.md)
- oracle.spatial.network.lod.[ClusterEvaluator](ClusterEvaluator.md)
- oracle.spatial.network.lod.[ClusteringConstraint](ClusteringConstraint.md)
- oracle.spatial.network.lod.[ClusterResult](ClusterResult.md)
- java.lang.Comparable\<T\>
  - oracle.spatial.network.lod.[LogicalLightSubPath](LogicalLightSubPath.md)
    - oracle.spatial.network.lod.[LogicalSubPath](LogicalSubPath.md)
      - oracle.spatial.network.lod.[SpatialSubPath](SpatialSubPath.md)
- oracle.spatial.network.lod.[Constraint](Constraint.md)\<T\>
  - oracle.spatial.network.lod.[LODNetworkConstraint](LODNetworkConstraint.md)
  - oracle.spatial.network.lod.[TspConstraint](TspConstraint.md)
- oracle.spatial.network.lod.[FeatureData](FeatureData.md)
- oracle.spatial.network.lod.[FeatureFilter](FeatureFilter.md)
- oracle.spatial.network.lod.[FeatureLayer](FeatureLayer.md)
- oracle.spatial.network.lod.[HeuristicCostFunction](HeuristicCostFunction.md)
- oracle.spatial.network.lod.[Identifiable](Identifiable.md)
- oracle.spatial.network.lod.[KShortestPaths](KShortestPaths.md)
- oracle.spatial.network.lod.[LinkCostCalculator](LinkCostCalculator.md)
- oracle.spatial.network.lod.[LinkLevelSelector](LinkLevelSelector.md)
- oracle.spatial.network.lod.[LODGoalNode](LODGoalNode.md)
- oracle.spatial.network.lod.[LODUserDataIO](LODUserDataIO.md)
- oracle.spatial.network.lod.[MinimumSpanningTree](MinimumSpanningTree.md)
- oracle.spatial.network.lod.[NetworkIO](NetworkIO.md)
  - oracle.spatial.network.lod.[CachedNetworkIO](CachedNetworkIO.md)
    - oracle.spatial.network.lod.[CachedNetworkIOWM](CachedNetworkIOWM.md)
- oracle.spatial.network.lod.[NodeCostCalculator](NodeCostCalculator.md)
- oracle.spatial.network.lod.[PairwiseCostCalculator](PairwiseCostCalculator.md)
- oracle.spatial.network.lod.[PairwisePathResultIO](PairwisePathResultIO.md)
- oracle.spatial.network.lod.[PairwiseShortestPaths](PairwiseShortestPaths.md)
- oracle.spatial.network.lod.[PartitionBlobTranslator](PartitionBlobTranslator.md)
- oracle.spatial.network.lod.[PathFilter](PathFilter.md)
- oracle.spatial.network.lod.[PointClustering](PointClustering.md)
- oracle.spatial.network.lod.[PriorityQueue](PriorityQueue.md)\<E\>
  - oracle.spatial.network.lod.[IdentifiablePriorityQueue](IdentifiablePriorityQueue.md)\<E\>
- java.io.Serializable
  - oracle.spatial.network.lod.[CategorizedUserData](CategorizedUserData.md)
  - oracle.spatial.network.lod.[UserData](UserData.md)
- oracle.spatial.network.lod.[ShortestPath](ShortestPath.md)
- oracle.spatial.network.lod.[SingleSourceShortestPaths](SingleSourceShortestPaths.md)
- oracle.spatial.network.lod.[TSP](TSP.md)
- oracle.spatial.network.lod.[TspOptimizer](TspOptimizer.md)
- oracle.spatial.network.lod.UserDataHolder
  - oracle.spatial.network.lod.[Feature](Feature.md)
    - oracle.spatial.network.lod.[PathFeature](PathFeature.md)
  - oracle.spatial.network.lod.[LogicalHeavyPath](LogicalHeavyPath.md)
    - oracle.spatial.network.lod.[SpatialHeavyPath](SpatialHeavyPath.md)
  - oracle.spatial.network.lod.[LogicalLightPath](LogicalLightPath.md)
    - oracle.spatial.network.lod.[LogicalPath](LogicalPath.md)
      - oracle.spatial.network.lod.[SpatialPath](SpatialPath.md)
  - oracle.spatial.network.lod.[LogicalLightSubPath](LogicalLightSubPath.md) (also extends java.lang.Comparable\<T\>)
    - oracle.spatial.network.lod.[LogicalSubPath](LogicalSubPath.md)
      - oracle.spatial.network.lod.[SpatialSubPath](SpatialSubPath.md)
  - oracle.spatial.network.lod.[LogicalLink](LogicalLink.md)
    - oracle.spatial.network.lod.[LogicalNetLink](LogicalNetLink.md)
      - oracle.spatial.network.lod.[SpatialNetLink](SpatialNetLink.md)
    - oracle.spatial.network.lod.[SpatialLink](SpatialLink.md)
  - oracle.spatial.network.lod.[LogicalNode](LogicalNode.md)
    - oracle.spatial.network.lod.[LogicalNetNode](LogicalNetNode.md)
      - oracle.spatial.network.lod.[SpatialNetNode](SpatialNetNode.md)
    - oracle.spatial.network.lod.[SpatialNode](SpatialNode.md)
- oracle.spatial.network.lod.[VRP](VRP.md)
- oracle.spatial.network.lod.[XMLConfigurable](XMLConfigurable.md)

## Enum Hierarchy

- java.lang.Object
  - java.lang.Enum\<E\> (implements java.lang.Comparable\<T\>, java.io.Serializable)
    - oracle.spatial.network.lod.[TSP.TourFlag](TSP.TourFlag.md)
    - oracle.spatial.network.lod.[FeatureLayerMetadata.FeatureLayerType](FeatureLayerMetadata.FeatureLayerType.md)
    - oracle.spatial.network.lod.[FeatureElement.FeatureElementType](FeatureElement.FeatureElementType.md)
    - oracle.spatial.network.lod.[Feature.FeatureType](Feature.FeatureType.md)

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- Tree
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev](../package-tree.md)
-

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
