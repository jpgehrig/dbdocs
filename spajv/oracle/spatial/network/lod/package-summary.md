Skip navigation links

- [Overview](../../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Package](../package-summary.md)
- [Next Package](config/package-summary.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

# Package oracle.spatial.network.lod

Provides support for the Load-On-Demand (LOD) approach of network analysis in the Oracle Spatial network data model, which is documented in *Oracle Spatial Topology and Network Data Models.*

See: Description

- **Interface Summary**

  | Interface                                                                                                                     | Description                                                                                                                                   |
  |-------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
  | [CachedNetworkIO](CachedNetworkIO.md)                                                                                         | This interface defines methods related to cached network input and output.                                                                    |
  | [CachedNetworkIOWM](CachedNetworkIOWM.md)                                                                                     | This interface defines methods related to workspace change.                                                                                   |
  | [CachingHandler](CachingHandler.md)                                                                                           | This interface defines methods supported by a caching handler.                                                                                |
  | [CategorizedUserData](CategorizedUserData.md)                                                                                 | This interface defines methods supported by a categorized user data object.                                                                   |
  | [Cluster](Cluster.md)                                                                                                         |                                                                                                                                               |
  | [ClusterEvaluator](ClusterEvaluator.md)                                                                                       |                                                                                                                                               |
  | [ClusteringConstraint](ClusteringConstraint.md)                                                                               |                                                                                                                                               |
  | [ClusterResult](ClusterResult.md)                                                                                             |                                                                                                                                               |
  | [Constraint](Constraint.md)\<T\>                                                                                              |                                                                                                                                               |
  | [Feature](Feature.md)                                                                                                         | This interface defines the methods supported by a network feature.                                                                            |
  | [FeatureData](FeatureData.md)                                                                                                 | FeatureData contains information about all feature data associated with the network elements in a network, sub-network or a partition.        |
  | [FeatureElement](FeatureElement.md)                                                                                           | A feature element is a point or line defined on a network element.                                                                            |
  | [FeatureFilter](FeatureFilter.md)                                                                                             | This interface defines the methods to check whether a given feature is a goal feature during network analysis.                                |
  | [FeatureLayer](FeatureLayer.md)                                                                                               | Features associated with elements in a network, sub-network or a partition, in a feature layer.                                               |
  | [HeuristicCostFunction](HeuristicCostFunction.md)                                                                             | This interface defines the heuristic cost function from one point to another.                                                                 |
  | [Identifiable](Identifiable.md)                                                                                               |                                                                                                                                               |
  | [IdentifiablePriorityQueue](IdentifiablePriorityQueue.md)\<E extends [Identifiable](Identifiable.md) & java.lang.Comparable\> | This interface defines the methods supported by a priority queue.                                                                             |
  | [KShortestPaths](KShortestPaths.md)                                                                                           | This interface defines methods supported by a k shortest path algorithm.                                                                      |
  | [LinkCostCalculator](LinkCostCalculator.md)                                                                                   | This interface defines methods supported by a link cost calculator.                                                                           |
  | [LinkLevelSelector](LinkLevelSelector.md)                                                                                     | A LinkLevelSelector selects the link level for the next node to expand on.                                                                    |
  | [LODGoalNode](LODGoalNode.md)                                                                                                 | This interface defines methods to check whether a given node is a goal node.                                                                  |
  | [LODNetworkConstraint](LODNetworkConstraint.md)                                                                               | This interface defines a general network constraint for network analysis.                                                                     |
  | [LODUserDataIO](LODUserDataIO.md)                                                                                             | This interface defines methods to read and write user defined data from and to the database.                                                  |
  | [LogicalBasicNetwork](LogicalBasicNetwork.md)                                                                                 | This interface defines methods supported by a logical network.                                                                                |
  | [LogicalHeavyPath](LogicalHeavyPath.md)                                                                                       | A LogicalHeavyPath is a logical path with detailed node and link information.                                                                 |
  | [LogicalLightPath](LogicalLightPath.md)                                                                                       | Light-weight logical path, which only contains the start and end node IDs on the path.                                                        |
  | [LogicalLightSubPath](LogicalLightSubPath.md)                                                                                 | Light weight logical sub-path that references to a `LogicalLightPath`                                                                         |
  | [LogicalLink](LogicalLink.md)                                                                                                 | This interface defines a standalone link.                                                                                                     |
  | [LogicalNetLink](LogicalNetLink.md)                                                                                           | A LogicalNetLink defines a network link, which is a LogicalLink with reference to the LogicalNetNode objects of its start and end nodes.      |
  | [LogicalNetNode](LogicalNetNode.md)                                                                                           | A LogicalNetNode is a LogicalNode with reference to adjacent node and link objects.                                                           |
  | [LogicalNode](LogicalNode.md)                                                                                                 | This interface defines a standalone node.                                                                                                     |
  | [LogicalPartition](LogicalPartition.md)                                                                                       | This interface defines methods supported by a logical network partition.                                                                      |
  | [LogicalPath](LogicalPath.md)                                                                                                 | A LogicalPath is defined by an array of link IDs, array of node IDs, and the costs for traversing through this path.                          |
  | [LogicalSubNetwork](LogicalSubNetwork.md)                                                                                     | A LogicalSubNetwork is a LogicalNetwork that connects to external nodes.                                                                      |
  | [LogicalSubPath](LogicalSubPath.md)                                                                                           | LogicalSubPath represents a portion of a LogicalPath, with the start and/or end points located on links of the the containing path.           |
  | [MinimumSpanningTree](MinimumSpanningTree.md)                                                                                 | This interface defines methods supported by a minimum-spanning-tree algorithm.                                                                |
  | [NetworkIO](NetworkIO.md)                                                                                                     | This interface defines methods to read/write network information from/to a datasource.                                                        |
  | [NodeCostCalculator](NodeCostCalculator.md)                                                                                   | This interface defines methods supported by a node cost calculator.                                                                           |
  | [PairwiseCostCalculator](PairwiseCostCalculator.md)                                                                           | This interface defines methods to calculate the pairwise costs between two sets of points.                                                    |
  | [PairwisePathResultIO](PairwisePathResultIO.md)                                                                               |                                                                                                                                               |
  | [PairwiseShortestPaths](PairwiseShortestPaths.md)                                                                             | A PairwiseShortestPaths is an algorithm to calculate the the pair-wise shortest paths between a set of candidate start points and end points. |
  | [PartitionBlobTranslator](PartitionBlobTranslator.md)                                                                         | This interface defines methods supported by a partition blob translator.                                                                      |
  | [PathFeature](PathFeature.md)                                                                                                 | A feature representing a path on a network.                                                                                                   |
  | [PathFilter](PathFilter.md)                                                                                                   | This interface defines the methods to check whether a given sub-path is a goal sub-path during network analysis.                              |
  | [PointClustering](PointClustering.md)                                                                                         |                                                                                                                                               |
  | [PriorityQueue](PriorityQueue.md)\<E extends java.lang.Comparable\>                                                           | This interface defines the methods supported by a priority queue.                                                                             |
  | [ShortestPath](ShortestPath.md)                                                                                               | This interface defines methods supported by a shortest path algorithm.                                                                        |
  | [SingleSourceShortestPaths](SingleSourceShortestPaths.md)                                                                     |                                                                                                                                               |
  | [SpatialBasicNetwork](SpatialBasicNetwork.md)                                                                                 | A SpatialNetwork is a LogicalNetwork with geometry information.                                                                               |
  | [SpatialHeavyPath](SpatialHeavyPath.md)                                                                                       | A SpatialHeavyPath is a LogicalHeavyPath with geometry information.                                                                           |
  | [SpatialLink](SpatialLink.md)                                                                                                 | A SpatialLink is a LogicalLink with geometry information.                                                                                     |
  | [SpatialNetLink](SpatialNetLink.md)                                                                                           | A SpatialNetLink is a LogicalNetLink with geometry information.                                                                               |
  | [SpatialNetNode](SpatialNetNode.md)                                                                                           | A SpatialNetNode is a LogicalNetNode with geometry information.                                                                               |
  | [SpatialNode](SpatialNode.md)                                                                                                 | A SpatialNode is a LogicalNode with geometry information.                                                                                     |
  | [SpatialPartition](SpatialPartition.md)                                                                                       | A SpatialPartition is a LogicalPartition with geometry information.                                                                           |
  | [SpatialPath](SpatialPath.md)                                                                                                 | A SpatialPath is a LogicalPath with geometry information.                                                                                     |
  | [SpatialSubNetwork](SpatialSubNetwork.md)                                                                                     | A SpatialSubNetwork is a LogicalSubNetwork with geometry information.                                                                         |
  | [SpatialSubPath](SpatialSubPath.md)                                                                                           | A SpatialSubPath is a LogicalSubPath with geometry information.                                                                               |
  | [TSP](TSP.md)                                                                                                                 | This interface defines methods supported by traveling salesman problem algorithm.                                                             |
  | [TspConstraint](TspConstraint.md)                                                                                             |                                                                                                                                               |
  | [TspOptimizer](TspOptimizer.md)                                                                                               |                                                                                                                                               |
  | [UserData](UserData.md)                                                                                                       | This interface defines methods supported by a user data set.                                                                                  |
  | [VRP](VRP.md)                                                                                                                 |                                                                                                                                               |
  | [XMLConfigurable](XMLConfigurable.md)                                                                                         | This interface defines methods that make a customized XML configuration implementation.                                                       |

- **Class Summary**

  | Class                                                                                                                   | Description                                                                                                                                                   |
  |-------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [AnalysisEngine](AnalysisEngine.md)                                                                                     |                                                                                                                                                               |
  | [AnalysisEngine.DefaultCallable](AnalysisEngine.DefaultCallable.md)                                                     |                                                                                                                                                               |
  | [AStar](AStar.md)                                                                                                       | This class implements A\* shortest path algorithm.                                                                                                            |
  | [BidirectionalBfs](BidirectionalBfs.md)                                                                                 |                                                                                                                                                               |
  | [BidirectionalDijkstra](BidirectionalDijkstra.md)                                                                       |                                                                                                                                                               |
  | [BinaryHeap](BinaryHeap.md)\<E extends java.lang.Comparable\>                                                           | a binary Min.                                                                                                                                                 |
  | [BreadthFirstSearch](BreadthFirstSearch.md)                                                                             | Network search algorithm that explores the network in breadth first manner.                                                                                   |
  | [CategorizedUserDataImpl](CategorizedUserDataImpl.md)                                                                   | Default implementation for CategorizedUserData.                                                                                                               |
  | [ClusterSizeConstraint](ClusterSizeConstraint.md)                                                                       |                                                                                                                                                               |
  | [ConstraintOperator](ConstraintOperator.md)                                                                             | Supports "and", "or", and "not" operations on network constraints.                                                                                            |
  | [DefaultLinkCostCalculator](DefaultLinkCostCalculator.md)                                                               | This is the default link cost calculator implementation.                                                                                                      |
  | [DefaultNodeCostCalculator](DefaultNodeCostCalculator.md)                                                               | This is the default node cost calculator implementation.                                                                                                      |
  | [DefaultPairwiseCostCalculator](DefaultPairwiseCostCalculator.md)                                                       | This is the default pairwise cost calculator.                                                                                                                 |
  | [DefaultPairwiseShortestPaths](DefaultPairwiseShortestPaths.md)                                                         | This is the default pairwise shortest paths algorithm.                                                                                                        |
  | [DefaultSingleSourceShortestPaths](DefaultSingleSourceShortestPaths.md)                                                 |                                                                                                                                                               |
  | [Dijkstra](Dijkstra.md)                                                                                                 | This class implements Dijkstra shortest path algorithm.                                                                                                       |
  | [DummyCostFunction](DummyCostFunction.md)                                                                               | The heuristic cost function implemented in this class always returns 0.                                                                                       |
  | [DummyLinkCostCalculator](DummyLinkCostCalculator.md)                                                                   | This implementation of LinkCostCalculator always returns a fixed number as link cost.                                                                         |
  | [DummyLinkLevelSelector](DummyLinkLevelSelector.md)                                                                     | This implementation of LinkLevelSelector always returns the fixed link level specified in the constructor.                                                    |
  | [DummyNodeCostCalculator](DummyNodeCostCalculator.md)                                                                   | This implementation of NodeCostCalculator always returns a fixed number as node cost.                                                                         |
  | [DynamicLinkLevelSelector](DynamicLinkLevelSelector.md)                                                                 | This implementation of LinkLevelSelector dynamically assigns link level to the next node according to the distance from the next node to the start/end point. |
  | [EuclideanCostFunction](EuclideanCostFunction.md)                                                                       | This class implements the A\* heuristic cost function as the 2D euclidean distance between the current node and the goal node.                                |
  | [FeatureDataImpl](FeatureDataImpl.md)                                                                                   | Default implementations for FeatureData.                                                                                                                      |
  | [FeatureElementImpl](FeatureElementImpl.md)                                                                             | Default implementation of FeatureElement.                                                                                                                     |
  | [FeatureFilterOperator](FeatureFilterOperator.md)                                                                       | Supports "and", "or", and "not" operations on feature filters.                                                                                                |
  | [FeatureImpl](FeatureImpl.md)                                                                                           | Default implementation of Feature.                                                                                                                            |
  | [FeatureLayerImpl](FeatureLayerImpl.md)                                                                                 | Default implementation of FeatureLayer.                                                                                                                       |
  | [FeatureLayerMetadata](FeatureLayerMetadata.md)                                                                         | Metadata information for a feature layer.                                                                                                                     |
  | [FeatureMetadata](FeatureMetadata.md)                                                                                   | Metadata for all registered feature layers on a network.                                                                                                      |
  | [FeaturePath](FeaturePath.md)                                                                                           | A FeaturePath object consists of a Feature and the PathFeature that ends at the feature.                                                                      |
  | [FilePairwisePathResultIO](FilePairwisePathResultIO.md)                                                                 |                                                                                                                                                               |
  | [GeodeticCostFunction](GeodeticCostFunction.md)                                                                         | This class implements the heuristic cost as the 2D geodetic distance in meters between the current node and the goal node.                                    |
  | [GeodeticPairwiseCostCalculator](GeodeticPairwiseCostCalculator.md)                                                     |                                                                                                                                                               |
  | [GoalNodeOperator](GoalNodeOperator.md)                                                                                 | Supports "and", "or", and "not" operations on goal node filters.                                                                                              |
  | [HeavyPointOnNet](HeavyPointOnNet.md)                                                                                   | A HeavyPointOnNet is a PointOnNet with reference to the underlying LogialNode and LogicalLink object.                                                         |
  | [IdentifiableBinaryHeap](IdentifiableBinaryHeap.md)\<E extends [Identifiable](Identifiable.md) & java.lang.Comparable\> | a binary Min.                                                                                                                                                 |
  | [InMemoryPairwisePathResultIO](InMemoryPairwisePathResultIO.md)                                                         |                                                                                                                                                               |
  | [KShortestPathsBfs](KShortestPathsBfs.md)                                                                               | BFS implementation of K-shortest paths search.                                                                                                                |
  | [LeveledNetworkCache](LeveledNetworkCache.md)                                                                           | An instance of this class contains the cache for all link levels of a network.                                                                                |
  | [LODAnalysisInfo](LODAnalysisInfo.md)                                                                                   | An instance of this class carries the analysis information.                                                                                                   |
  | [LODNetworkFactory](LODNetworkFactory.md)                                                                               | This class handles network element creation for Oracle Spatial Network Data Model.                                                                            |
  | [LODNetworkManager](LODNetworkManager.md)                                                                               | This class is the entry point of all functionalities provided by the lod package.                                                                             |
  | [LODNetworkWrapper](LODNetworkWrapper.md)                                                                               | This is the wrapper class containing LOD related java stored procedures used by SDO_NET package.                                                              |
  | [LODUserDataIOSDO](LODUserDataIOSDO.md)                                                                                 | This implementation of LODUserDataIO reads all the user defined data from the node, link and path tables.                                                     |
  | [LogicalNetLinkImpl](LogicalNetLinkImpl.md)                                                                             | Default implementation of LogicalNetLink.                                                                                                                     |
  | [LogicalNetNodeImpl](LogicalNetNodeImpl.md)                                                                             | Default implementation of LogicalNetNode.                                                                                                                     |
  | [LogicalPartitionImpl](LogicalPartitionImpl.md)                                                                         | Default implementation of LogicalPartition.                                                                                                                   |
  | [LogicalSubPathImpl](LogicalSubPathImpl.md)                                                                             | Default implementation of LogicalSubPath.                                                                                                                     |
  | [LongHashMap](LongHashMap.md)\<V\>                                                                                      | This is a bare-bones, application specific, optimized hash table implementation.                                                                              |
  | [LongHashSet](LongHashSet.md)                                                                                           | This is a bare-bones, application specific, optimized hash set implementation.                                                                                |
  | [LongLinkedHashMap](LongLinkedHashMap.md)\<V\>                                                                          | This is a bare-bones, application specific, optimized ordered hash map implementation.                                                                        |
  | [LRUCachingHandler](LRUCachingHandler.md)                                                                               | This class implements the Least Recently Used (LRU) caching handler.                                                                                          |
  | [Matrix](Matrix.md)\<E\>                                                                                                | A simple double array matrix implementation.                                                                                                                  |
  | [MaxCostConstraint](MaxCostConstraint.md)                                                                               | Maximum cost network constraint.                                                                                                                              |
  | [MaxDepthConstraint](MaxDepthConstraint.md)                                                                             | Maximum depth network constraint.                                                                                                                             |
  | [NetworkAnalyst](NetworkAnalyst.md)                                                                                     | This class is the single entry point to all the network analysis operations supported by NDM LOD.                                                             |
  | [NetworkBuffer](NetworkBuffer.md)                                                                                       | A NetworkBuffer is defined by central points and the set of nodes and link intervals within certain radius from the cental points.                            |
  | [NetworkBuffer.DoubleInterval](NetworkBuffer.DoubleInterval.md)                                                         | This class defines a double interval.                                                                                                                         |
  | [NetworkBuffer.Elements](NetworkBuffer.Elements.md)                                                                     | This class contains elements in a network buffer.                                                                                                             |
  | [NetworkBuffer.LinkInterval](NetworkBuffer.LinkInterval.md)                                                             |                                                                                                                                                               |
  | [NetworkBuffer.LinkIntervals](NetworkBuffer.LinkIntervals.md)                                                           | An instance of this class contains a LogicalLink object and a list of intervals associated with the link object.                                              |
  | [NetworkExplorer](NetworkExplorer.md)                                                                                   | This class provides methods to navigate a network.                                                                                                            |
  | [NetworkSearch](NetworkSearch.md)                                                                                       |                                                                                                                                                               |
  | [NetworkUpdate](NetworkUpdate.md)                                                                                       | A NetworkUpdate object contains network update information.                                                                                                   |
  | [OrderedLongSet](OrderedLongSet.md)                                                                                     | Ordered Long Set                                                                                                                                              |
  | [ParallelPairwiseShortestPaths](ParallelPairwiseShortestPaths.md)                                                       |                                                                                                                                                               |
  | [PartitionBlob](PartitionBlob.md)                                                                                       | An instance of the PartitionBlob represents a row in the partition BLOB table in the database.                                                                |
  | [PartitionBlobTranslator11g](PartitionBlobTranslator11g.md)                                                             | The class to translate a network partition BLOB to a LogicalPartition object, or vice versa.                                                                  |
  | [PartitionBlobTranslator11gR2](PartitionBlobTranslator11gR2.md)                                                         | The class translates a network partition BLOB to a LogicalPartition object, or vice versa.                                                                    |
  | [PartitionUpdate](PartitionUpdate.md)                                                                                   | A PartitionUpdate object contains partition update information.                                                                                               |
  | [PathFeatureImpl](PathFeatureImpl.md)                                                                                   | Default implementation of PathFeature.                                                                                                                        |
  | [PathToPoint](PathToPoint.md)                                                                                           |                                                                                                                                                               |
  | [PointOnNet](PointOnNet.md)                                                                                             | This class defines the methods supported by a point on a network.                                                                                             |
  | [SilhouetteClusterEvaluator](SilhouetteClusterEvaluator.md)                                                             | This implementation uses the Silhouette method to measure cluster quality.                                                                                    |
  | [SpanningTree](SpanningTree.md)                                                                                         | A spanning tree on the network.                                                                                                                               |
  | [SpatialBisectClustering](SpatialBisectClustering.md)                                                                   |                                                                                                                                                               |
  | [SpatialKMeansClustering](SpatialKMeansClustering.md)                                                                   |                                                                                                                                                               |
  | [SpatialSubPathImpl](SpatialSubPathImpl.md)                                                                             | Default implementation of SpatialSubPath.                                                                                                                     |
  | [TimeWindow](TimeWindow.md)                                                                                             |                                                                                                                                                               |
  | [Tsp2Opt](Tsp2Opt.md)                                                                                                   |                                                                                                                                                               |
  | [TspAnalysisInfo](TspAnalysisInfo.md)                                                                                   | This class contains the TSP points in order, besides other info in LODAnalysisInfo.                                                                           |
  | [TspConstraintOperator](TspConstraintOperator.md)                                                                       |                                                                                                                                                               |
  | [TspConstraintOperator.CombinedConstraint](TspConstraintOperator.CombinedConstraint.md)                                 |                                                                                                                                                               |
  | [TspImpl](TspImpl.md)                                                                                                   | The default two step TSP implementation, which first computes the pairwise costs between the TSP stops, and then optimizes the order the stops to be visited. |
  | [TspImpl.NetworkTspConstraint](TspImpl.NetworkTspConstraint.md)                                                         |                                                                                                                                                               |
  | [TspNearestNeighbor](TspNearestNeighbor.md)                                                                             | This is a simple heuristic TSP algorithm, which always picks the closest point as the next one to visit.                                                      |
  | [TspOp2](TspOp2.md)                                                                                                     | This class implements the 2-opt heuristic algorithm for the Traveling-Salesman-Problem.                                                                       |
  | [TspOrderConstraint](TspOrderConstraint.md)                                                                             | TSP ordering constraint implementation.                                                                                                                       |
  | [TspPath](TspPath.md)                                                                                                   | A TspPath consists of an array of LogicalSubPath and the order of the points on the TSP tour.                                                                 |
  | [TspPathFeature](TspPathFeature.md)                                                                                     | A TspPathFeature object contains information about the tsp order and a sequence of path features from the first point until the last point.                   |
  | [TspTimeWindowConstraint](TspTimeWindowConstraint.md)                                                                   |                                                                                                                                                               |
  | [UserDataImpl](UserDataImpl.md)                                                                                         | Default implementation of UserData.                                                                                                                           |
  | [VisitedNode](VisitedNode.md)                                                                                           | This class represents a node visited while exploring a network.                                                                                               |
  | [VrpClusterAndRoute](VrpClusterAndRoute.md)                                                                             |                                                                                                                                                               |
  | [VrpPath](VrpPath.md)                                                                                                   |                                                                                                                                                               |
  | [YenDeviation](YenDeviation.md)                                                                                         | This class implements Yen's Deviation Algorithm for finding the k shortest loopless paths.                                                                    |

- **Enum Summary**

  | Enum                                                                              | Description                                                                                                                              |
  |-----------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
  | [Feature.FeatureType](Feature.FeatureType.md)                                     | A list of valid feature types.                                                                                                           |
  | [FeatureElement.FeatureElementType](FeatureElement.FeatureElementType.md)         | A list of valid feature element types.                                                                                                   |
  | [FeatureLayerMetadata.FeatureLayerType](FeatureLayerMetadata.FeatureLayerType.md) | A list of valid feature layer types.                                                                                                     |
  | [TSP.TourFlag](TSP.TourFlag.md)                                                   | Enumeration whose values indicate whether a tsp tour is open or closed, and if open, whether the tour have fixed start and/or end point. |

- **Exception Summary**

  | Exception                                                     | Description                                               |
  |---------------------------------------------------------------|-----------------------------------------------------------|
  | [LinkNotFoundException](LinkNotFoundException.md)             | Thrown when a link(s) cannot be found.                    |
  | [LODNetworkException](LODNetworkException.md)                 | Base exception class for Load-On-Demand network analysis. |
  | [MethodNotSupportedException](MethodNotSupportedException.md) | Thrown when an unsupported or invalid method is called.   |
  | [NodeNotFoundException](NodeNotFoundException.md)             | Thrown when a node(s) cannot be found.                    |

## Package oracle.spatial.network.lod Description

Provides support for the Load-On-Demand (LOD) approach of network analysis in the Oracle Spatial network data model, which is documented in *Oracle Spatial Topology and Network Data Models.*

This package provides methods to
- read network information,
- perform network analysis,
- store analysis results, and
- configure the load-on-demand settings, such as cache size, caching policy, load network from the node/link tables or from the blobs, etc.,

`LODNetworkManager` is the entry point for all the functionalities provided by this package.
To read network information, first obtain a `NetworIO` object from the `NetworkManager`, and then call various network IO methods provided by `NetworkIO`. For example,

      NetworkIO networkIO    = LODNetworkManager.getCachedNetworkIO(myConnection, "MYNETWORK", "MYNETWORK");
      int numberOfPartitions = networkIO.readNumberOfPartitions(1);
      int numberOfNodes      = networkIO.readNumberOfNodes(1);
      LogicalPartition part  = networkIO.readLogicalPartition(1, 1, true, true);

To analyze a network, first obtain a `NetworkAnalyst` object from the `NetworkManager`, and then call the various network analysis functions provided by the network analyst. For example,

      NetworkAnalyst analyst = LODNetworkManager.getNetworkAnalyst(networkIO);
      LogicalSubPath path = analyst.shortestPathDijkstra(
                              new PointOnNet(2000), new PointOnNet(6700), null);
      LogicalSubPath[] paths = analyst.nearestNeighbors(
                                 new PointOnNet(2000), 10, null, null);

To configure load-on-demand settings, create or edit your LOD configuration xml file, obtain the `ConfigManager` object from the `NetworkManager`, and then call the loadConfig method to load the configuration. For example,

      InputStream in = ClassLoader.getSystemResourceAsStream("lodconfig.xml");
      LODNetworkManager.getConfigManager().loadConfig(in);

Skip navigation links

- [Overview](../../../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Package](../package-summary.md)
- [Next Package](config/package-summary.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

Copyright © 2007, 2019, Oracle and/or its affiliates. All Rights Reserved.
