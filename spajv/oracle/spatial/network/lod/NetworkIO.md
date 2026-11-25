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

- [Prev Class](NetworkExplorer.md)
- [Next Class](NetworkSearch.md)

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

## Interface NetworkIO

- All Known Subinterfaces:
  [CachedNetworkIO](CachedNetworkIO.md), [CachedNetworkIOWM](CachedNetworkIOWM.md)

  ------------------------------------------------------------------------



      public interface NetworkIO

  This interface defines methods to read/write network information from/to a datasource.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                               | Method and Description                                                                                                                                                                                                                                                                                                    |
    |---------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                          | `close``()`                                                                                                                                                                                                                                                                                                               |
    | `void`                                                                          | `commit``()`<br>Sends out commit command to the database.                                                                                                                                                                                                                                                                 |
    | [`JGeometry`](../../geometry/JGeometry.md)`[]`                                  | `computeFeatureGeometries``(`[`Feature`](Feature.md)`[] features, int nodeGeomUserDataCategory, int nodeGeomUserDataIndex, int linkGeomUserDataCategory, int linkGeomUserDataIndex, boolean consolidate)`<br>Constructs the feature geometry from the geometries of its network elements.                                 |
    | `void`                                                                          | `deleteNetworkBuffer``(long id)`<br>Deletes the network buffer from the database.                                                                                                                                                                                                                                         |
    | `void`                                                                          | `deleteNetworkBuffer``(long id, java.lang.String bufferName)`<br>Deletes the network buffer from the database.                                                                                                                                                                                                            |
    | `void`                                                                          | `deletePath``(long pathId)`<br>Deletes path.                                                                                                                                                                                                                                                                              |
    | `void`                                                                          | `deletePaths``(long[] pathIds)`<br>Deletes paths.                                                                                                                                                                                                                                                                         |
    | `void`                                                                          | `deleteSubPath``(long subPathId)`<br>Deletes sub-path.                                                                                                                                                                                                                                                                    |
    | `void`                                                                          | `deleteSubPaths``(long[] subPathIds)`<br>Deletes sub-paths.                                                                                                                                                                                                                                                               |
    | `void`                                                                          | `generatePartitionBlob``(int partitionId, int linkLevel, boolean includeUserData)`<br>Generate partition BLOB for the specified partition.                                                                                                                                                                                |
    | `void`                                                                          | `generatePartitionBlob``(int partitionId, int linkLevel, boolean includeUserData, boolean performDeltaUpdate)`<br>Generates partition BLOB for the specified partition.                                                                                                                                                   |
    | `void`                                                                          | `generatePartitionBlobs``(boolean includeUserData, boolean commitForEachBlob, boolean performDeltaUpdate)`<br>Generates partition BLOBs for all link levels.                                                                                                                                                              |
    | `void`                                                                          | `generatePartitionBlobs``(int linkLevel, boolean includeUserData, boolean commitForEachBlob)`<br>Generates partition BLOBs for the specified link level.                                                                                                                                                                  |
    | `void`                                                                          | `generatePartitionBlobs``(int linkLevel, boolean includeUserData, boolean commitForEachBlob, boolean performDeltaUpdate)`<br>Generates partition BLOBs for the specified link level.                                                                                                                                      |
    | `java.sql.Connection`                                                           | `getConnection``()`<br>Deprecated. <br>use getDataSource instead                                                                                                                                                                                                                                                          |
    | `IDataSource`                                                                   | `getDataSource``()`<br>Returns the data source.                                                                                                                                                                                                                                                                           |
    | `java.lang.String`                                                              | `getGlobalNetworkName``()`<br>Returns the global network name, i.e., the network name that is globally unique, and is used as the cache key for the network.                                                                                                                                                              |
    | [`NetworkIOConfig`](config/NetworkIOConfig.md)                                  | `getNetworkIOConfig``()`<br>Returns the network IO configuration.                                                                                                                                                                                                                                                         |
    | [`NetworkMetadata`](../NetworkMetadata.md)                                      | `getNetworkMetadata``()`<br>Returns the network metadata.                                                                                                                                                                                                                                                                 |
    | `java.lang.String`                                                              | `getNetworkName``()`<br>Returns the network name used in network metadata.                                                                                                                                                                                                                                                |
    | `long`                                                                          | `getNextId``()`<br>Returns the next value from the NDM ID sequence.                                                                                                                                                                                                                                                       |
    | `long`                                                                          | `getNextTmpLinkId``()`<br>Returns the next temporary link ID.                                                                                                                                                                                                                                                             |
    | `long`                                                                          | `getNextTmpNodeId``()`<br>Returns the next temporary node ID.                                                                                                                                                                                                                                                             |
    | [`PartitionBlobTranslator`](PartitionBlobTranslator.md)                         | `getPartitionBlobTranslator``()`<br>Returns the partition blob translator implementation.                                                                                                                                                                                                                                 |
    | [`LODUserDataIO`](LODUserDataIO.md)`[]`                                         | `getUserDataIOs``()`<br>Returns the user data IO implementations.                                                                                                                                                                                                                                                         |
    | `boolean[]`                                                                     | `hasLinks``(long[] linkIds)`<br>Checks whether the input links exist or not                                                                                                                                                                                                                                               |
    | `boolean[]`                                                                     | `hasNodes``(long[] nodeIds)`<br>Checks whether the input nodes exist or not                                                                                                                                                                                                                                               |
    | `boolean[]`                                                                     | `isLinksExist``(long[] linkIds)`<br>Checks whether the input links exist or not                                                                                                                                                                                                                                           |
    | `boolean[]`                                                                     | `isNodesExist``(long[] nodeIds)`<br>Checks whether the input nodes exist or not                                                                                                                                                                                                                                           |
    | `boolean`                                                                       | `isReadFromBlob``()`<br>Returns true if the partitions are read from BLOB; false if the partitions are read from node/link tables.                                                                                                                                                                                        |
    | `void`                                                                          | `open``()`                                                                                                                                                                                                                                                                                                                |
    | [`LongHashMap`](LongHashMap.md)`<int[]>`                                        | `readAdjacentPartitionIdsForLinks``(long[] linkIds, int linkLevel)`<br>Retrieves the relevant partition IDs for the specified node IDs.                                                                                                                                                                                   |
    | [`LongHashMap`](LongHashMap.md)`<int[]>`                                        | `readAdjacentPartitionIdsForNodes``(long[] nodeIds, int linkLevel)`<br>Retrieves the adjacent partition IDs for the specified node IDs.                                                                                                                                                                                   |
    | [`LogicalLink`](LogicalLink.md)                                                 | `readArbitraryLogicalLink``(int linkLevel, int[] userDataCategories)`<br>Returns an arbitrary link from the specified link level.                                                                                                                                                                                         |
    | [`LogicalLink`](LogicalLink.md)`[]`                                             | `readArbitraryLogicalLinks``(int linkLevel, int numberOfLinks, int[] userDataCategories)`<br>Returns an array of arbitrary links from the specified link level.                                                                                                                                                           |
    | [`LogicalNode`](LogicalNode.md)                                                 | `readArbitraryLogicalNode``(int linkLevel, int[] userDataCategories)`<br>Returns an arbitrary node from the specified link level.                                                                                                                                                                                         |
    | [`LogicalNode`](LogicalNode.md)`[]`                                             | `readArbitraryLogicalNodes``(int linkLevel, int numberOfNodes, int[] userDataCategories)`<br>Returns an array of arbitrary nodes from the specified link level.                                                                                                                                                           |
    | `int`                                                                           | `readComponentId``(long nodeId, int linkLevel)`<br>Retrieves the component ID assigned to the specified node ID.                                                                                                                                                                                                          |
    | `int[]`                                                                         | `readComponentIds``(int linkLevel)`<br>Retrieves the component IDs stored in the connected component table.                                                                                                                                                                                                               |
    | `void`                                                                          | `readFeatureData``(`[`LogicalPartition`](LogicalPartition.md)` partition, int[] featureLayerIds, int[] userDataCategories)`<br>Adds feature data to the logical partition                                                                                                                                                 |
    | [`Feature`](Feature.md)`[]`                                                     | `readFeatures``(int featureLayerId, long[] featureIds, int[] userDataCategories)`<br>Read features.                                                                                                                                                                                                                       |
    | `long[]`                                                                        | `readLinkIds``(int linkLevel)`                                                                                                                                                                                                                                                                                            |
    | `int[]`                                                                         | `readLinkPartitionIds``(long[] linkIds, int linkLevel)`<br>Retrieves the partition IDs for the specified links.                                                                                                                                                                                                           |
    | `int[]`                                                                         | `readLinkPartitionIds``(long linkId, int linkLevel)`<br>Retrieves the partition IDs for the specified link.                                                                                                                                                                                                               |
    | [`LogicalHeavyPath`](LogicalHeavyPath.md)                                       | `readLogicalHeavyPath``(`[`LogicalPath`](LogicalPath.md)` path, boolean includeUserData)`<br>Retrieves node and link information for the specified logical path.                                                                                                                                                          |
    | [`LogicalHeavyPath`](LogicalHeavyPath.md)                                       | `readLogicalHeavyPath``(`[`LogicalPath`](LogicalPath.md)` path, int[] userDataCategories)`<br>Retrieves node and link information for the specified logical path.                                                                                                                                                         |
    | [`LogicalHeavyPath`](LogicalHeavyPath.md)`[]`                                   | `readLogicalHeavyPaths``(`[`LogicalPath`](LogicalPath.md)`[] paths, boolean includeUserData)`<br>Retrieves node and link information for the specified logical paths.                                                                                                                                                     |
    | [`LogicalHeavyPath`](LogicalHeavyPath.md)`[]`                                   | `readLogicalHeavyPaths``(`[`LogicalPath`](LogicalPath.md)`[] paths, int[] userDataCategories)`<br>Retrieves node and link information for the specified logical paths.                                                                                                                                                    |
    | [`LogicalLink`](LogicalLink.md)                                                 | `readLogicalLink``(long linkId, boolean includeUserData)`<br>Retrieves the standalone logical link, i.e., the logical link without references to the start and end nodes, for the specified link ID.                                                                                                                      |
    | [`LogicalLink`](LogicalLink.md)                                                 | `readLogicalLink``(long linkId, int[] userDataCategories)`<br>Retrieves the standalone logical link, i.e., the logical link without references to the start and end nodes, for the specified link ID.                                                                                                                     |
    | [`LogicalLink`](LogicalLink.md)`[]`                                             | `readLogicalLinks``(int linkLevel, int[] userDataCategories)`<br>Returns the links on the specified link level.                                                                                                                                                                                                           |
    | [`LogicalLink`](LogicalLink.md)`[]`                                             | `readLogicalLinks``(long[] linkIds, boolean includeUserData)`<br>Retrieves the standalone logical links, i.e., the logical link without references to the start and end nodes, for the specified link ID.                                                                                                                 |
    | [`LogicalLink`](LogicalLink.md)`[]`                                             | `readLogicalLinks``(long[] linkIds, int[] userDataCategories)`<br>Retrieves the standalone logical links, i.e., the logical link without references to the start and end nodes, for the specified link ID.                                                                                                                |
    | [`LogicalBasicNetwork`](LogicalBasicNetwork.md)                                 | `readLogicalNetwork``(int linkLevel, boolean includeUserData)`<br>Retrieves the logical network.                                                                                                                                                                                                                          |
    | [`LogicalBasicNetwork`](LogicalBasicNetwork.md)                                 | `readLogicalNetwork``(int linkLevel, boolean includeUserData, boolean readFromBlob)`<br>Retrieves the logical network.                                                                                                                                                                                                    |
    | [`LogicalBasicNetwork`](LogicalBasicNetwork.md)                                 | `readLogicalNetwork``(int linkLevel, int[] userDataCategories)`<br>Retrieves the logical network.                                                                                                                                                                                                                         |
    | [`LogicalBasicNetwork`](LogicalBasicNetwork.md)                                 | `readLogicalNetwork``(int linkLevel, int[] userDataCategories, int[] featureLayerIds)`<br>Retrieves the logical network.                                                                                                                                                                                                  |
    | [`LogicalBasicNetwork`](LogicalBasicNetwork.md)                                 | `readLogicalNetwork``(int linkLevel, int[] userDataCategories, int[] featureLayerIds, boolean readFromBlob)`<br>Retrieves the logical network.                                                                                                                                                                            |
    | [`LogicalNode`](LogicalNode.md)                                                 | `readLogicalNode``(long nodeId, boolean includeUserData)`<br>Retrieves the standalone logical node, i.e., the logical node without references to incoming and outgoing links, for the specified node ID.                                                                                                                  |
    | [`LogicalNode`](LogicalNode.md)                                                 | `readLogicalNode``(long nodeId, int[] userDataCategories)`<br>Retrieves the standalone logical node, i.e., the logical node without references to incoming and outgoing links, for the specified node ID.                                                                                                                 |
    | [`LogicalNode`](LogicalNode.md)`[]`                                             | `readLogicalNodes``(int linkLevel, int[] userDataCategories)`<br>Returns the nodes on the specified link level.                                                                                                                                                                                                           |
    | [`LogicalNode`](LogicalNode.md)`[]`                                             | `readLogicalNodes``(long[] nodeIds, boolean includeUserData)`<br>Retrieves the standalone logical nodes, i.e., the logical nodes without references to incoming and outgoing links, for the specified node IDs.                                                                                                           |
    | [`LogicalNode`](LogicalNode.md)`[]`                                             | `readLogicalNodes``(long[] nodeIds, int[] userDataCategories)`<br>Retrieves the standalone logical nodes, i.e., the logical nodes without references to incoming and outgoing links, for the specified node IDs.                                                                                                          |
    | [`LogicalPartition`](LogicalPartition.md)                                       | `readLogicalPartition``(int partitionId, int linkLevel, boolean includeUserData)`<br>Retrieves the logical network partition for the specified partition ID.                                                                                                                                                              |
    | [`LogicalPartition`](LogicalPartition.md)                                       | `readLogicalPartition``(int partitionId, int linkLevel, boolean includeUserData, boolean readFromBlob)`<br>Retrieves the logical network partition for the specified partition ID.                                                                                                                                        |
    | [`LogicalPartition`](LogicalPartition.md)                                       | `readLogicalPartition``(int partitionId, int linkLevel, int[] userDataCategories)`<br>Retrieves the logical network partition for the specified partition ID.                                                                                                                                                             |
    | [`LogicalPartition`](LogicalPartition.md)                                       | `readLogicalPartition``(int partitionId, int linkLevel, int[] userDataCategories, boolean readFromBlob)`<br>Retrieves the logical network partition for the specified partition ID.                                                                                                                                       |
    | [`LogicalPartition`](LogicalPartition.md)                                       | `readLogicalPartition``(int partitionId, int linkLevel, int[] userDataCategories, int[] featureLayerIds)`<br>Retrieves the logical network partition for the specified partition ID.                                                                                                                                      |
    | [`LogicalPartition`](LogicalPartition.md)                                       | `readLogicalPartition``(int partitionId, int linkLevel, int[] userDataCategories, int[] featureLayerIds, boolean readFromBlob)`<br>Retrieves the logical network partition for the specified partition ID.                                                                                                                |
    | [`LogicalPartition`](LogicalPartition.md)`[]`                                   | `readLogicalPartitions``(int linkLevel, boolean includeUserData)`<br>Retrieves all the logical network partitions in this network.                                                                                                                                                                                        |
    | [`LogicalPartition`](LogicalPartition.md)`[]`                                   | `readLogicalPartitions``(int linkLevel, boolean includeUserData, boolean readFromBlob)`<br>Retrieves all the logical network partitions.                                                                                                                                                                                  |
    | [`LogicalPartition`](LogicalPartition.md)`[]`                                   | `readLogicalPartitions``(int linkLevel, int[] userDataCategories)`<br>Retrieves all the logical network partitions in this network.                                                                                                                                                                                       |
    | [`LogicalPartition`](LogicalPartition.md)`[]`                                   | `readLogicalPartitions``(int linkLevel, int[] userDataCategories, boolean readFromBlob)`<br>Retrieves all the logical network partitions.                                                                                                                                                                                 |
    | [`LogicalPartition`](LogicalPartition.md)`[]`                                   | `readLogicalPartitions``(int linkLevel, int[] userDataCategories, int[] featureLayerIds)`<br>Retrieves all the logical network partitions in this network.                                                                                                                                                                |
    | [`LogicalPartition`](LogicalPartition.md)`[]`                                   | `readLogicalPartitions``(int linkLevel, int[] userDataCategories, int[] featureLayerIds, boolean readFromBlob)`<br>Retrieves all the logical network partitions.                                                                                                                                                          |
    | [`LogicalPath`](LogicalPath.md)                                                 | `readLogicalPath``(long pathId, boolean includeUserData)`<br>Retrieves the logical path for the specified path ID.                                                                                                                                                                                                        |
    | [`LogicalPath`](LogicalPath.md)                                                 | `readLogicalPath``(long pathId, int[] userDataCategories)`<br>Retrieves the logical path for the specified path ID.                                                                                                                                                                                                       |
    | [`LogicalPath`](LogicalPath.md)`[]`                                             | `readLogicalPaths``(long[] pathIds, boolean includeUserData)`<br>Retrieves the logical paths for the specified path IDs.                                                                                                                                                                                                  |
    | [`LogicalPath`](LogicalPath.md)`[]`                                             | `readLogicalPaths``(long[] pathIds, int[] userDataCategories)`<br>Retrieves the logical paths for the specified path IDs.                                                                                                                                                                                                 |
    | [`LogicalSubPath`](LogicalSubPath.md)                                           | `readLogicalSubPath``(long subPathId, boolean includeUserData)`<br>Retrieves the logical subpath for the specified subpath ID.                                                                                                                                                                                            |
    | [`LogicalSubPath`](LogicalSubPath.md)                                           | `readLogicalSubPath``(long subPathId, int[] userDataCategories)`<br>Retrieves the logical subpath for the specified subpath ID.                                                                                                                                                                                           |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`                                       | `readLogicalSubPaths``(long[] subPathIds, boolean includeUserData)`<br>Retrieves the logical subpaths for the specified subpath IDs.                                                                                                                                                                                      |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`                                       | `readLogicalSubPaths``(long[] subPathIds, int[] userDataCategories)`<br>Retrieves the logical subpaths for the specified subpath IDs.                                                                                                                                                                                     |
    | `int`                                                                           | `readMaximumIncomingLinkLevel``(long nodeId)`<br>Retrieves the maximum link level of the incoming links connected to the specified node.                                                                                                                                                                                  |
    | `int`                                                                           | `readMaximumLinkLevel``()`<br>Retrieves the maximum link level of the network.                                                                                                                                                                                                                                            |
    | `int`                                                                           | `readMaximumLinkLevel``(long nodeId)`<br>Retrieves the maximum link level of the links connected to the specified node.                                                                                                                                                                                                   |
    | `int`                                                                           | `readMaximumOutgoingLinkLevel``(long nodeId)`<br>Retrieves the maximum link level of the outgoing links connected to the specified node.                                                                                                                                                                                  |
    | [`NetworkBuffer`](NetworkBuffer.md)                                             | `readNetworkBuffer``(long bufferId)`<br>Reads the network buffer with the specified buffer ID.                                                                                                                                                                                                                            |
    | [`NetworkBuffer`](NetworkBuffer.md)                                             | `readNetworkBuffer``(long bufferId, java.lang.String bufferName)`<br>Reads the network buffer with the specified buffer ID.                                                                                                                                                                                               |
    | [`NetworkUpdate`](NetworkUpdate.md)                                             | `readNetworkUpdate``(int linkLevel, java.util.Calendar lastUpdateTime, int[] userDataCategories)`                                                                                                                                                                                                                         |
    | [`NetworkUpdate`](NetworkUpdate.md)                                             | `readNetworkUpdate``(int linkLevel, long[] changedNodeIds, long[] changedLinkIds, int[] userDataCategories)`<br>Constructs network update object according to the changed node and link IDs.                                                                                                                              |
    | [`NetworkUpdate`](NetworkUpdate.md)                                             | `readNetworkUpdate``(int linkLevel, long[] updatedNodeIds, long[] deletedNodeIds, long[] updatedLinkIds, long[] deletedLinkIds, int[] userDataCategories)`<br>Constructs network update object according to the changed node and link IDs.                                                                                |
    | [`NetworkUpdate`](NetworkUpdate.md)`[]`                                         | `readNetworkUpdates``(java.util.Calendar lastUpdateTime, int[] userDataCategories)`                                                                                                                                                                                                                                       |
    | `long[]`                                                                        | `readNodeIds``(int linkLevel)`<br>Retrieves the array of node IDs in the network.                                                                                                                                                                                                                                         |
    | `int`                                                                           | `readNodePartitionId``(long nodeId, int linkLevel)`<br>Retrieves the partition ID for the specified node ID.                                                                                                                                                                                                              |
    | `int[]`                                                                         | `readNodePartitionIds``(long[] nodeIds, int linkLevel)`<br>Retrieves the partition IDs for the specified node IDs.                                                                                                                                                                                                        |
    | `int`                                                                           | `readNumberOfConnectedComponents``(int linkLevel)`<br>Retrieves the number of connected components stored in the component table.                                                                                                                                                                                         |
    | `int`                                                                           | `readNumberOfLinkLevels``()`<br>Retrieves the number of link levels.                                                                                                                                                                                                                                                      |
    | `int`                                                                           | `readNumberOfLinks``(int linkLevel)`<br>Retrieves the number of links in the network.                                                                                                                                                                                                                                     |
    | `int`                                                                           | `readNumberOfNodes``(int linkLevel)`<br>Retrieves the number of nodes in the network.                                                                                                                                                                                                                                     |
    | `int`                                                                           | `readNumberOfPartitions``(int linkLevel)`<br>Retrieves the number of partitions in the network.                                                                                                                                                                                                                           |
    | `int`                                                                           | `readPartitionId``(long nodeId, int linkLevel)`<br>Retrieves the partition ID for the specified node ID.                                                                                                                                                                                                                  |
    | `int[]`                                                                         | `readPartitionIds``(int linkLevel)`<br>Retrieves all the partition IDs in the network.                                                                                                                                                                                                                                    |
    | `int[]`                                                                         | `readPartitionIds``(long[] nodeIds, int linkLevel)`<br>Retrieves the partition IDs for the specified node IDs.                                                                                                                                                                                                            |
    | [`SpatialHeavyPath`](SpatialHeavyPath.md)                                       | `readSpatialHeavyPath``(`[`LogicalPath`](LogicalPath.md)` path, boolean includeUserData)`<br>Retrieves node and link information for the specified logical paths.                                                                                                                                                         |
    | [`SpatialHeavyPath`](SpatialHeavyPath.md)                                       | `readSpatialHeavyPath``(`[`LogicalPath`](LogicalPath.md)` path, int[] userDataCategories)`<br>Retrieves node and link information for the specified logical paths.                                                                                                                                                        |
    | [`SpatialHeavyPath`](SpatialHeavyPath.md)`[]`                                   | `readSpatialHeavyPaths``(`[`LogicalPath`](LogicalPath.md)`[] paths, boolean includeUserData)`<br>Retrieves node and link information for the specified logical paths.                                                                                                                                                     |
    | [`SpatialHeavyPath`](SpatialHeavyPath.md)`[]`                                   | `readSpatialHeavyPaths``(`[`LogicalPath`](LogicalPath.md)`[] paths, int[] userDataCategories)`<br>Retrieves node and link information for the specified logical paths.                                                                                                                                                    |
    | [`SpatialLink`](SpatialLink.md)                                                 | `readSpatialLink``(long linkId, boolean includeUserData)`<br>Retrieves the spatial link for the specified link ID.                                                                                                                                                                                                        |
    | [`SpatialLink`](SpatialLink.md)                                                 | `readSpatialLink``(long linkId, int[] userDataCategories)`<br>Retrieves the spatial link for the specified link ID.                                                                                                                                                                                                       |
    | [`SpatialLink`](SpatialLink.md)`[]`                                             | `readSpatialLinks``(long[] linkIds, boolean includeUserData)`<br>Retrieves the spatial links for the specified link IDs.                                                                                                                                                                                                  |
    | [`SpatialLink`](SpatialLink.md)`[]`                                             | `readSpatialLinks``(long[] linkIds, int[] userDataCategories)`<br>Retrieves the spatial links for the specified link IDs.                                                                                                                                                                                                 |
    | [`SpatialBasicNetwork`](SpatialBasicNetwork.md)                                 | `readSpatialNetwork``(`[`LogicalBasicNetwork`](LogicalBasicNetwork.md)` logicalNetwork)`<br>Retrieves spatial information for the logical network, and returns the spatial network.                                                                                                                                       |
    | [`SpatialNode`](SpatialNode.md)                                                 | `readSpatialNode``(long nodeId, boolean includeUserData)`<br>Retrieves the spatial node for the specified node ID.                                                                                                                                                                                                        |
    | [`SpatialNode`](SpatialNode.md)                                                 | `readSpatialNode``(long nodeId, int[] userDataCategories)`<br>Retrieves the spatial node for the specified node ID.                                                                                                                                                                                                       |
    | [`SpatialNode`](SpatialNode.md)`[]`                                             | `readSpatialNodes``(long[] nodeIds, boolean includeUserData)`<br>Retrieves the spatial nodes for the specified node IDs.                                                                                                                                                                                                  |
    | [`SpatialNode`](SpatialNode.md)`[]`                                             | `readSpatialNodes``(long[] nodeIds, int[] userDataCategories)`<br>Retrieves the spatial nodes for the specified node IDs.                                                                                                                                                                                                 |
    | [`SpatialPartition`](SpatialPartition.md)                                       | `readSpatialPartition``(int partitionId, int linkLevel, boolean includeUserData)`<br>Retrieves spatial partition.                                                                                                                                                                                                         |
    | [`SpatialPartition`](SpatialPartition.md)                                       | `readSpatialPartition``(int partitionId, int linkLevel, boolean includeUserData, boolean readFromBlob)`<br>Retrieves spatial partition.                                                                                                                                                                                   |
    | [`SpatialPartition`](SpatialPartition.md)                                       | `readSpatialPartition``(int partitionId, int linkLevel, int[] userDataCategories, int[] featureLayerIds)`<br>Retrieves spatial partition.                                                                                                                                                                                 |
    | [`SpatialPartition`](SpatialPartition.md)                                       | `readSpatialPartition``(int partitionId, int linkLevel, int[] userDataCategories, int[] featureLayerIds, boolean readFromBlob)`<br>Retrieves spatial partition.                                                                                                                                                           |
    | [`SpatialPartition`](SpatialPartition.md)                                       | `readSpatialPartition``(`[`LogicalPartition`](LogicalPartition.md)` logicalPartition)`<br>Retrieves spatial information for the logical network partition, and returns the spatial network partition.                                                                                                                     |
    | [`JGeometry`](../../geometry/JGeometry.md)                                      | `readSpatialPartitionMBR``(int partitionId, int linkLevel)`<br>Returns the minimum bounding rectangle (MBR) encompassing all the **nodes** in the specified partition.                                                                                                                                                    |
    | `java.util.Map<java.lang.Integer,`[`JGeometry`](../../geometry/JGeometry.md)`>` | `readSpatialPartitionMBRs``(int linkLevel)`<br>Returns the minimum bounding rectangles (MBR) of all the partitions in this network.                                                                                                                                                                                       |
    | [`SpatialPath`](SpatialPath.md)                                                 | `readSpatialPath``(`[`LogicalPath`](LogicalPath.md)` logicalPath)`<br>Retrieves the spatial information for the specified logical path, and returns the spatial path.                                                                                                                                                     |
    | [`SpatialPath`](SpatialPath.md)                                                 | `readSpatialPath``(long pathId, boolean includeUserData)`<br>Retrieves the spatial path for the specified path ID.                                                                                                                                                                                                        |
    | [`SpatialPath`](SpatialPath.md)                                                 | `readSpatialPath``(long pathId, int[] userDataCategories)`<br>Retrieves the spatial path for the specified path ID.                                                                                                                                                                                                       |
    | [`SpatialPath`](SpatialPath.md)`[]`                                             | `readSpatialPaths``(`[`LogicalPath`](LogicalPath.md)`[] logicalPath)`<br>Retrieves the spatial information for the specified logical path, and returns the spatial path.                                                                                                                                                  |
    | [`SpatialPath`](SpatialPath.md)`[]`                                             | `readSpatialPaths``(long[] pathIds, boolean includeUserData)`<br>Retrieves the spatial path for the specified path ID.                                                                                                                                                                                                    |
    | [`SpatialPath`](SpatialPath.md)`[]`                                             | `readSpatialPaths``(long[] pathIds, int[] userDataCategories)`<br>Retrieves the spatial path for the specified path ID.                                                                                                                                                                                                   |
    | [`SpatialSubPath`](SpatialSubPath.md)                                           | `readSpatialSubPath``(`[`LogicalSubPath`](LogicalSubPath.md)` logicalSubPath)`<br>Retrieves the spatial information of the specified logical subpath, and returns the spatial subpath.                                                                                                                                    |
    | [`SpatialSubPath`](SpatialSubPath.md)                                           | `readSpatialSubPath``(long subPathId, boolean includeUserData)`<br>Retrieves the spatial subpath information.                                                                                                                                                                                                             |
    | [`SpatialSubPath`](SpatialSubPath.md)                                           | `readSpatialSubPath``(long subPathId, int[] userDataCategories)`<br>Retrieves the spatial subpath information.                                                                                                                                                                                                            |
    | [`SpatialSubPath`](SpatialSubPath.md)`[]`                                       | `readSpatialSubPaths``(`[`LogicalSubPath`](LogicalSubPath.md)`[] logicalSubPaths)`<br>Retrieves the spatial information of the specified logical subpaths, and returns the spatial subpath.                                                                                                                               |
    | [`SpatialSubPath`](SpatialSubPath.md)`[]`                                       | `readSpatialSubPaths``(long[] subPathIds, boolean includeUserData)`<br>Retrieves the spatial subpath information.                                                                                                                                                                                                         |
    | [`SpatialSubPath`](SpatialSubPath.md)`[]`                                       | `readSpatialSubPaths``(long[] subPathIds, int[] userDataCategories)`<br>Retrieves the spatial subpath information.                                                                                                                                                                                                        |
    | `void`                                                                          | `readUserData``(`[`LogicalPartition`](LogicalPartition.md)` partition, int[] userDataCategories)`<br>Adds user data information to the logical partition                                                                                                                                                                  |
    | `void`                                                                          | `rollback``()`<br>Sends out rollback command to the database.                                                                                                                                                                                                                                                             |
    | `void`                                                                          | `saveConnectedComponents``(`[`OrderedLongSet`](OrderedLongSet.md)`[] components, int linkLevel)`<br>Stores the connected components information in the component table.                                                                                                                                                   |
    | `void`                                                                          | `setConnection``(java.sql.Connection conn)`<br>Deprecated. <br>use setDataSource instead                                                                                                                                                                                                                                  |
    | `void`                                                                          | `setDataSource``(IDataSource dataSource)`<br>Sets the data source.                                                                                                                                                                                                                                                        |
    | `void`                                                                          | `setGlobalNetworkName``(java.lang.String globalNetworkName)`<br>Sets the global network name, i.e., the network name that is globally unique, and is used as the cache key for the network.                                                                                                                               |
    | `void`                                                                          | `setNetworkMetadata``(`[`NetworkMetadata`](../NetworkMetadata.md)` metadata)`<br>Sets network metadata                                                                                                                                                                                                                    |
    | `void`                                                                          | `setPartitionBlobTranslator``(`[`PartitionBlobTranslator`](PartitionBlobTranslator.md)` translator)`<br>Sets the partition blob translator.                                                                                                                                                                               |
    | `void`                                                                          | `setReadFromBlob``(boolean readFromBlob)`<br>Sets whether to read partitions from BLOBs.                                                                                                                                                                                                                                  |
    | `void`                                                                          | `setUserDataIOs``(`[`LODUserDataIO`](LODUserDataIO.md)`[] udios)`<br>Sets the user data IO implementations.                                                                                                                                                                                                               |
    | `void`                                                                          | `updatePartitionBlobInfo``(int partitionId, int linkLevel, int numberOfInternalNodes, int numberOfExternalNodes, int numberOfInternalLinks, int numberOfBoundaryLinks, int numberOfIncomingLinks, int numberOfOutgoingLinks, boolean isUserDataIncluded)`<br>Updates the partition BLOB info in the partition BLOB table. |
    | `long`                                                                          | `writeNetworkBuffer``(`[`NetworkBuffer`](NetworkBuffer.md)` buffer)`<br>Stores the network buffer into the database.                                                                                                                                                                                                      |
    | `void`                                                                          | `writeNetworkBuffer``(`[`NetworkBuffer`](NetworkBuffer.md)` networkBuffer, long bufferId)`<br>Stores the network buffer into the database.                                                                                                                                                                                |
    | `void`                                                                          | `writeNetworkBuffer``(`[`NetworkBuffer`](NetworkBuffer.md)` networkBuffer, long bufferId, java.lang.String bufferName)`<br>Stores the network buffer into the database.                                                                                                                                                   |
    | `long`                                                                          | `writeNetworkBuffer``(`[`NetworkBuffer`](NetworkBuffer.md)` buffer, java.lang.String bufferName)`<br>Stores the network buffer into the database.                                                                                                                                                                         |
    | `void`                                                                          | `writePath``(`[`LogicalPath`](LogicalPath.md)` path, long pathId, java.lang.String pathName, java.lang.String pathType)`<br>Stores a path in the database.                                                                                                                                                                |
    | `long`                                                                          | `writePath``(`[`LogicalPath`](LogicalPath.md)` path, java.lang.String pathName, java.lang.String pathType)`<br>Stores a path in the database.                                                                                                                                                                             |
    | `void`                                                                          | `writeSubPath``(`[`LogicalSubPath`](LogicalSubPath.md)` subPath, long subPathId, long referencePathId, java.lang.String subPathName, java.lang.String subPathType)`<br>Stores a sub-path in the database.                                                                                                                 |
    | `long`                                                                          | `writeSubPath``(`[`LogicalSubPath`](LogicalSubPath.md)` subPath, long referencePathId, java.lang.String subPathName, java.lang.String subPathType)`<br>Stores a sub-path in the database.                                                                                                                                 |

<!-- -->

- - ### Method Detail

    - #### close

          void close()
              throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### open

          void open()
             throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### getConnection

          java.sql.Connection getConnection()

      Deprecated. use getDataSource instead
      Returns the cached database connection managed by the user.
      Returns:

    <!-- -->

    - #### setConnection

          void setConnection(java.sql.Connection conn)

      Deprecated. use setDataSource instead
      Sets the cached database connection managed by the user.
      Parameters:
      `conn` -

    <!-- -->

    - #### getDataSource

          IDataSource getDataSource()

      Returns the data source.
      Returns:

    <!-- -->

    - #### setDataSource

          void setDataSource(IDataSource dataSource)

      Sets the data source.
      Parameters:
      `dataSource` -

    <!-- -->

    - #### getGlobalNetworkName

          java.lang.String getGlobalNetworkName()

      Returns the global network name, i.e., the network name that is globally unique, and is used as the cache key for the network.
      Returns:
      global network name

    <!-- -->

    - #### setGlobalNetworkName

          void setGlobalNetworkName(java.lang.String globalNetworkName)

      Sets the global network name, i.e., the network name that is globally unique, and is used as the cache key for the network.
      Parameters:
      `globalNetworkName` - global network name

    <!-- -->

    - #### getNetworkName

          java.lang.String getNetworkName()

      Returns the network name used in network metadata.
      Returns:
      global network name

    <!-- -->

    - #### getNetworkMetadata

          NetworkMetadata getNetworkMetadata()

      Returns the network metadata.
      Returns:
      network metadata

    <!-- -->

    - #### getNetworkIOConfig

          NetworkIOConfig getNetworkIOConfig()

      Returns the network IO configuration.
      Returns:

    <!-- -->

    - #### setNetworkMetadata

          void setNetworkMetadata(NetworkMetadata metadata)

      Sets network metadata
      Parameters:
      `metadata` - network metadata

    <!-- -->

    - #### getUserDataIOs

          LODUserDataIO[] getUserDataIOs()

      Returns the user data IO implementations.
      Returns:
      user data IO implementations

    <!-- -->

    - #### setUserDataIOs

          void setUserDataIOs(LODUserDataIO[] udios)

      Sets the user data IO implementations.
      Parameters:
      `udios` -

    <!-- -->

    - #### isReadFromBlob

          boolean isReadFromBlob()

      Returns true if the partitions are read from BLOB; false if the partitions are read from node/link tables.

    <!-- -->

    - #### setReadFromBlob

          void setReadFromBlob(boolean readFromBlob)

      Sets whether to read partitions from BLOBs.
      Parameters:
      `readFromBlob` - true if the partitions are read from BLOBs; false if the partitions are read from node/link tables.

    <!-- -->

    - #### getPartitionBlobTranslator

          PartitionBlobTranslator getPartitionBlobTranslator()

      Returns the partition blob translator implementation.

    <!-- -->

    - #### setPartitionBlobTranslator

          void setPartitionBlobTranslator(PartitionBlobTranslator translator)

      Sets the partition blob translator.
      Parameters:
      `translator` -

    <!-- -->

    - #### commit

          void commit()
               throws LODNetworkException

      Sends out commit command to the database.
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### rollback

          void rollback()
                 throws LODNetworkException

      Sends out rollback command to the database.
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### getNextId

          long getNextId()
                  throws LODNetworkException

      Returns the next value from the NDM ID sequence.
      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### isNodesExist

          boolean[] isNodesExist(long[] nodeIds)
                          throws LODNetworkException

      Checks whether the input nodes exist or not
      Parameters:
      `nodeIds` - IDs of the nodes

      Returns:
      array of boolean indicating whether each of the input nodes exist or not.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### hasNodes

          boolean[] hasNodes(long[] nodeIds)
                      throws LODNetworkException

      Checks whether the input nodes exist or not
      Parameters:
      `nodeIds` - IDs of the nodes

      Returns:
      array of boolean indicating whether each of the input nodes exist or not.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### isLinksExist

          boolean[] isLinksExist(long[] linkIds)
                          throws LODNetworkException

      Checks whether the input links exist or not
      Parameters:
      `linkIds` - IDs of the links

      Returns:
      array of boolean indicating whether each of the input links exist or not.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### hasLinks

          boolean[] hasLinks(long[] linkIds)
                      throws LODNetworkException

      Checks whether the input links exist or not
      Parameters:
      `linkIds` - IDs of the links

      Returns:
      array of boolean indicating whether each of the input links exist or not.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### updatePartitionBlobInfo

          void updatePartitionBlobInfo(int partitionId,
                                       int linkLevel,
                                       int numberOfInternalNodes,
                                       int numberOfExternalNodes,
                                       int numberOfInternalLinks,
                                       int numberOfBoundaryLinks,
                                       int numberOfIncomingLinks,
                                       int numberOfOutgoingLinks,
                                       boolean isUserDataIncluded)
                                throws LODNetworkException

      Updates the partition BLOB info in the partition BLOB table.
      Parameters:
      `partitionId` - partition ID

      `linkLevel` - link level

      `numberOfInternalNodes` - number of internal nodes

      `numberOfExternalNodes` - number of external nodes

      `numberOfInternalLinks` - number of internal links

      `numberOfBoundaryLinks` - number of boundary links

      `numberOfIncomingLinks` - number of incoming links

      `numberOfOutgoingLinks` - number of outgoing links

      `isUserDataIncluded` - whether user data is included in the partition BLOB or not

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readNumberOfNodes

          int readNumberOfNodes(int linkLevel)
                         throws LODNetworkException

      Retrieves the number of nodes in the network.
      Parameters:
      `linkLevel` - link level

      Returns:
      the number of nodes in the network

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readNumberOfLinks

          int readNumberOfLinks(int linkLevel)
                         throws LODNetworkException

      Retrieves the number of links in the network.
      Parameters:
      `linkLevel` - link level

      Returns:
      the number of links in the network

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readNodeIds

          long[] readNodeIds(int linkLevel)
                      throws LODNetworkException

      Retrieves the array of node IDs in the network.
      Parameters:
      `linkLevel` - link level

      Returns:
      the array of node IDs in the network

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLinkIds

          long[] readLinkIds(int linkLevel)
                      throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalNodes

          LogicalNode[] readLogicalNodes(int linkLevel,
                                         int[] userDataCategories)
                                  throws LODNetworkException

      Returns the nodes on the specified link level.
      Parameters:
      `linkLevel` - link level

      `userDataCategories` - user data categories to be loaded

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalLinks

          LogicalLink[] readLogicalLinks(int linkLevel,
                                         int[] userDataCategories)
                                  throws LODNetworkException

      Returns the links on the specified link level.
      Parameters:
      `linkLevel` - link level

      `userDataCategories` - user data categories to be loaded

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readArbitraryLogicalNodes

          LogicalNode[] readArbitraryLogicalNodes(int linkLevel,
                                                  int numberOfNodes,
                                                  int[] userDataCategories)
                                           throws LODNetworkException

      Returns an array of arbitrary nodes from the specified link level.
      Parameters:
      `linkLevel` - link level

      `numberOfNodes` - number of nodes

      `userDataCategories` - user data categories to be included

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readArbitraryLogicalLinks

          LogicalLink[] readArbitraryLogicalLinks(int linkLevel,
                                                  int numberOfLinks,
                                                  int[] userDataCategories)
                                           throws LODNetworkException

      Returns an array of arbitrary links from the specified link level.
      Parameters:
      `linkLevel` - link level

      `numberOfLinks` - number of links

      `userDataCategories` - user data categories to be included

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readArbitraryLogicalNode

          LogicalNode readArbitraryLogicalNode(int linkLevel,
                                               int[] userDataCategories)
                                        throws LODNetworkException

      Returns an arbitrary node from the specified link level.
      Parameters:
      `linkLevel` - link level

      `userDataCategories` - user data categories to be included

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readArbitraryLogicalLink

          LogicalLink readArbitraryLogicalLink(int linkLevel,
                                               int[] userDataCategories)
                                        throws LODNetworkException

      Returns an arbitrary link from the specified link level.
      Parameters:
      `linkLevel` - link level

      `userDataCategories` - user data categories to be included

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalNetwork

          LogicalBasicNetwork readLogicalNetwork(int linkLevel,
                                                 boolean includeUserData,
                                                 boolean readFromBlob)
                                          throws LODNetworkException

      Retrieves the logical network.
      Parameters:
      `linkLevel` - link level

      `includeUserData` - whether to include user data or not

      `readFromBlob` - whether to read from BLOBs or from table

      Returns:
      the logical network

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalNetwork

          LogicalBasicNetwork readLogicalNetwork(int linkLevel,
                                                 int[] userDataCategories,
                                                 int[] featureLayerIds,
                                                 boolean readFromBlob)
                                          throws LODNetworkException

      Retrieves the logical network.
      Parameters:
      `linkLevel` - link level

      `userDataCategories` - user data categories to be included

      `readFromBlob` - whether to read from BLOBs or from table

      Returns:
      the logical network

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalNetwork

          LogicalBasicNetwork readLogicalNetwork(int linkLevel,
                                                 boolean includeUserData)
                                          throws LODNetworkException

      Retrieves the logical network. Whether the network is loaded from BLOBs or from node and link tables depends on how it is configured in the LOD configuration xml.
      Parameters:
      `linkLevel` - link level

      `includeUserData` - whether to include user data or not

      Returns:
      the logical network

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalNetwork

          LogicalBasicNetwork readLogicalNetwork(int linkLevel,
                                                 int[] userDataCategories)
                                          throws LODNetworkException

      Retrieves the logical network.
      Parameters:
      `linkLevel` - link level

      `userDataCategories` - user data categories to be included

      Returns:
      the logical network

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalNetwork

          LogicalBasicNetwork readLogicalNetwork(int linkLevel,
                                                 int[] userDataCategories,
                                                 int[] featureLayerIds)
                                          throws LODNetworkException

      Retrieves the logical network.
      Parameters:
      `linkLevel` - link level

      `userDataCategories` - user data categories to be included

      Returns:
      the logical network

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalPartition

          LogicalPartition readLogicalPartition(int partitionId,
                                                int linkLevel,
                                                boolean includeUserData,
                                                boolean readFromBlob)
                                         throws LODNetworkException

      Retrieves the logical network partition for the specified partition ID.
      Parameters:
      `partitionId` - partition ID

      `linkLevel` - link level

      `includeUserData` - whether to include user data or not

      `readFromBlob` - whether to read from BLOBs or from table

      Returns:
      logical network partition

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalPartition

          LogicalPartition readLogicalPartition(int partitionId,
                                                int linkLevel,
                                                int[] userDataCategories,
                                                boolean readFromBlob)
                                         throws LODNetworkException

      Retrieves the logical network partition for the specified partition ID.
      Parameters:
      `partitionId` - partition ID

      `linkLevel` - link level

      `userDataCategories` - user data categories to be included

      `readFromBlob` - whether to read from BLOBs or from table

      Returns:
      logical network partition

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalPartition

          LogicalPartition readLogicalPartition(int partitionId,
                                                int linkLevel,
                                                int[] userDataCategories,
                                                int[] featureLayerIds,
                                                boolean readFromBlob)
                                         throws LODNetworkException

      Retrieves the logical network partition for the specified partition ID.
      Parameters:
      `partitionId` - partition ID

      `linkLevel` - link level

      `userDataCategories` - user data categories to be included

      `featureLayerIds` - feature layers to be included

      `readFromBlob` - whether to read from BLOBs or from table

      Returns:
      logical network partition

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalPartition

          LogicalPartition readLogicalPartition(int partitionId,
                                                int linkLevel,
                                                boolean includeUserData)
                                         throws LODNetworkException

      Retrieves the logical network partition for the specified partition ID. Whether the network partition is loaded from BLOBs or from node and link tables depends on how it is configured in the LOD configuration xml.
      Parameters:
      `partitionId` - partition ID

      `linkLevel` - link level

      `includeUserData` - whether to include user data or not

      Returns:
      logical network partition

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalPartition

          LogicalPartition readLogicalPartition(int partitionId,
                                                int linkLevel,
                                                int[] userDataCategories)
                                         throws LODNetworkException

      Retrieves the logical network partition for the specified partition ID.
      Parameters:
      `partitionId` - partition ID

      `linkLevel` - link level

      `userDataCategories` - user data categories to be included

      Returns:
      logical network partition

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalPartition

          LogicalPartition readLogicalPartition(int partitionId,
                                                int linkLevel,
                                                int[] userDataCategories,
                                                int[] featureLayerIds)
                                         throws LODNetworkException

      Retrieves the logical network partition for the specified partition ID.
      Parameters:
      `partitionId` - partition ID

      `linkLevel` - link level

      `userDataCategories` - user data categories to be included

      `featureLayerIds` - feature layer IDs

      Returns:
      logical network partition

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalPartitions

          LogicalPartition[] readLogicalPartitions(int linkLevel,
                                                   boolean includeUserData,
                                                   boolean readFromBlob)
                                            throws LODNetworkException

      Retrieves all the logical network partitions.
      Parameters:
      `linkLevel` - link level

      `includeUserData` - whether to include user data or not

      `readFromBlob` - whether to read from BLOBs or from table

      Returns:
      logical network partition

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalPartitions

          LogicalPartition[] readLogicalPartitions(int linkLevel,
                                                   int[] userDataCategories,
                                                   int[] featureLayerIds,
                                                   boolean readFromBlob)
                                            throws LODNetworkException

      Retrieves all the logical network partitions.
      Parameters:
      `linkLevel` - link level

      `userDataCategories` - user data categories to be included

      `readFromBlob` - whether to read from BLOBs or from table

      Returns:
      logical network partition

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalPartitions

          LogicalPartition[] readLogicalPartitions(int linkLevel,
                                                   int[] userDataCategories,
                                                   boolean readFromBlob)
                                            throws LODNetworkException

      Retrieves all the logical network partitions.
      Parameters:
      `linkLevel` - link level

      `userDataCategories` - user data categories to be included

      `readFromBlob` - whether to read from BLOBs or from table

      Returns:
      logical network partition

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalPartitions

          LogicalPartition[] readLogicalPartitions(int linkLevel,
                                                   boolean includeUserData)
                                            throws LODNetworkException

      Retrieves all the logical network partitions in this network.
      Parameters:
      `linkLevel` - link level

      `includeUserData` - whether to include user data or not

      Returns:
      all logical network partitions in this network

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalPartitions

          LogicalPartition[] readLogicalPartitions(int linkLevel,
                                                   int[] userDataCategories)
                                            throws LODNetworkException

      Retrieves all the logical network partitions in this network.
      Parameters:
      `linkLevel` - link level

      `userDataCategories` - user data categories to be included

      Returns:
      all logical network partitions in this network

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalPartitions

          LogicalPartition[] readLogicalPartitions(int linkLevel,
                                                   int[] userDataCategories,
                                                   int[] featureLayerIds)
                                            throws LODNetworkException

      Retrieves all the logical network partitions in this network.
      Parameters:
      `linkLevel` - link level

      `userDataCategories` - user data categories to be included

      `featureLayerIds` - feature layer IDs

      Returns:
      all logical network partitions in this network

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readUserData

          void readUserData(LogicalPartition partition,
                            int[] userDataCategories)
                     throws LODNetworkException

      Adds user data information to the logical partition
      Parameters:
      `partition` - logical partition

      `userDataCategories` - user data categories to be included

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readPartitionId

          int readPartitionId(long nodeId,
                              int linkLevel)
                       throws LODNetworkException

      Retrieves the partition ID for the specified node ID.
      Parameters:
      `nodeId` - node ID

      `linkLevel` - link level

      Returns:
      partition ID

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readPartitionIds

          int[] readPartitionIds(long[] nodeIds,
                                 int linkLevel)
                          throws LODNetworkException

      Retrieves the partition IDs for the specified node IDs.
      Parameters:
      `nodeIds` - node IDs

      `linkLevel` - link level

      Returns:
      partition IDs

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readNodePartitionId

          int readNodePartitionId(long nodeId,
                                  int linkLevel)
                           throws LODNetworkException

      Retrieves the partition ID for the specified node ID.
      Parameters:
      `nodeId` - node ID

      `linkLevel` - link level

      Returns:
      partition ID

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readNodePartitionIds

          int[] readNodePartitionIds(long[] nodeIds,
                                     int linkLevel)
                              throws LODNetworkException

      Retrieves the partition IDs for the specified node IDs.
      Parameters:
      `nodeIds` - node IDs

      `linkLevel` - link level

      Returns:
      partition IDs

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLinkPartitionIds

          int[] readLinkPartitionIds(long linkId,
                                     int linkLevel)
                              throws LODNetworkException

      Retrieves the partition IDs for the specified link.
      Parameters:
      `linkId` - link ID

      `linkLevel` - link level

      Returns:
      array of length 1 if the link is an internal link; array of length 2 if the link is a boundary link; null if the link does not exist on the specified link level of the network.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLinkPartitionIds

          int[] readLinkPartitionIds(long[] linkIds,
                                     int linkLevel)
                              throws LODNetworkException

      Retrieves the partition IDs for the specified links.
      Parameters:
      `linkIds` - link IDs

      `linkLevel` - link level

      Returns:
      array of length two times the number of the input link IDs. Element 2\*i of array contains partition ID of the start node of link i. Element 2\*i+1 of the array contains the partition ID of the end node of link i. Both element 2\*i and 2\*i+1 are set to -1 if link i does not exist on the specified link level of the network.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readAdjacentPartitionIdsForNodes

          LongHashMap<int[]> readAdjacentPartitionIdsForNodes(long[] nodeIds,
                                                              int linkLevel)
                                                       throws LODNetworkException

      Retrieves the adjacent partition IDs for the specified node IDs. A partition is adjacent to a node if the node is either an internal or external node in this partition.
      Parameters:
      `nodeIds` - node IDs

      `linkLevel` - link level

      Returns:
      relevant partition IDs for each node ID.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readAdjacentPartitionIdsForLinks

          LongHashMap<int[]> readAdjacentPartitionIdsForLinks(long[] linkIds,
                                                              int linkLevel)
                                                       throws LODNetworkException

      Retrieves the relevant partition IDs for the specified node IDs. A partition is adjacent to a link if the link is either an internal or boundary link in this partition.
      Parameters:
      `linkIds` - link IDs

      `linkLevel` - link level

      Returns:
      relevant partition IDs for eath node ID.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readPartitionIds

          int[] readPartitionIds(int linkLevel)
                          throws LODNetworkException

      Retrieves all the partition IDs in the network.
      Parameters:
      `linkLevel` - link level

      Returns:
      array of partition IDs

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readNumberOfPartitions

          int readNumberOfPartitions(int linkLevel)
                              throws LODNetworkException

      Retrieves the number of partitions in the network.
      Parameters:
      `linkLevel` - link level

      Returns:
      number of partitions

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readNumberOfConnectedComponents

          int readNumberOfConnectedComponents(int linkLevel)
                                       throws LODNetworkException

      Retrieves the number of connected components stored in the component table. This method should be called after the connected components have been pre-computed and stored in the database.
      Parameters:
      `linkLevel` - link level

      Returns:
      number of connected components, if the connected components have been pre-computed and stored in the database;
      -1, otherwise

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readComponentIds

          int[] readComponentIds(int linkLevel)
                          throws LODNetworkException

      Retrieves the component IDs stored in the connected component table. This method should be called after the connected components habe been pre-computed and stored in the database.
      Parameters:
      `linkLevel` - link level

      Returns:
      the component ID array, if the connected components have been pre-computed and stored in the database;
      null, otherwise

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readComponentId

          int readComponentId(long nodeId,
                              int linkLevel)
                       throws LODNetworkException

      Retrieves the component ID assigned to the specified node ID. This method should be called after the connected components habe been pre-computed and stored in the database.
      Parameters:
      `nodeId` - node ID

      `linkLevel` - link level

      Returns:
      the component ID assigned to the specified node ID, if the connected components have been pre-computed and stored in the database;
      -1, otherwise

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalLink

          LogicalLink readLogicalLink(long linkId,
                                      boolean includeUserData)
                               throws LODNetworkException

      Retrieves the standalone logical link, i.e., the logical link without references to the start and end nodes, for the specified link ID.
      Parameters:
      `linkId` - link ID

      `includeUserData` - whether to include the userdata or not

      Returns:
      logical link

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalLink

          LogicalLink readLogicalLink(long linkId,
                                      int[] userDataCategories)
                               throws LODNetworkException

      Retrieves the standalone logical link, i.e., the logical link without references to the start and end nodes, for the specified link ID.
      Parameters:
      `linkId` - link ID

      `userDataCategories` - user data categories to be included

      Returns:
      logical link

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalLinks

          LogicalLink[] readLogicalLinks(long[] linkIds,
                                         boolean includeUserData)
                                  throws LODNetworkException

      Retrieves the standalone logical links, i.e., the logical link without references to the start and end nodes, for the specified link ID.
      Parameters:
      `linkIds` - link ID

      `includeUserData` - whether to include the userdata or not

      Returns:
      logical link

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalLinks

          LogicalLink[] readLogicalLinks(long[] linkIds,
                                         int[] userDataCategories)
                                  throws LODNetworkException

      Retrieves the standalone logical links, i.e., the logical link without references to the start and end nodes, for the specified link ID.
      Parameters:
      `linkIds` - link ID

      `userDataCategories` -

      Returns:
      logical link

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalNode

          LogicalNode readLogicalNode(long nodeId,
                                      boolean includeUserData)
                               throws LODNetworkException

      Retrieves the standalone logical node, i.e., the logical node without references to incoming and outgoing links, for the specified node ID.
      Parameters:
      `nodeId` - node ID

      `includeUserData` - whether to include the userdata or not

      Returns:
      logical node

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalNodes

          LogicalNode[] readLogicalNodes(long[] nodeIds,
                                         boolean includeUserData)
                                  throws LODNetworkException

      Retrieves the standalone logical nodes, i.e., the logical nodes without references to incoming and outgoing links, for the specified node IDs.
      Parameters:
      `nodeIds` - node IDs

      `includeUserData` - whether to include the userdata or not

      Returns:
      logical node

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalNode

          LogicalNode readLogicalNode(long nodeId,
                                      int[] userDataCategories)
                               throws LODNetworkException

      Retrieves the standalone logical node, i.e., the logical node without references to incoming and outgoing links, for the specified node ID.
      Parameters:
      `nodeId` - node ID

      `userDataCategories` -

      Returns:
      logical node

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalNodes

          LogicalNode[] readLogicalNodes(long[] nodeIds,
                                         int[] userDataCategories)
                                  throws LODNetworkException

      Retrieves the standalone logical nodes, i.e., the logical nodes without references to incoming and outgoing links, for the specified node IDs.
      Parameters:
      `nodeIds` - node IDs

      `userDataCategories` -

      Returns:
      logical node

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalPath

          LogicalPath readLogicalPath(long pathId,
                                      boolean includeUserData)
                               throws LODNetworkException

      Retrieves the logical path for the specified path ID.
      Parameters:
      `pathId` - path ID

      `includeUserData` - whether to include the userdata or not

      Returns:
      logical path

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalPaths

          LogicalPath[] readLogicalPaths(long[] pathIds,
                                         boolean includeUserData)
                                  throws LODNetworkException

      Retrieves the logical paths for the specified path IDs.
      Parameters:
      `pathIds` - path IDs

      `includeUserData` - whether to include the userdata or not

      Returns:
      logical paths

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalPath

          LogicalPath readLogicalPath(long pathId,
                                      int[] userDataCategories)
                               throws LODNetworkException

      Retrieves the logical path for the specified path ID.
      Parameters:
      `pathId` - path ID

      `userDataCategories` -

      Returns:
      logical path

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalPaths

          LogicalPath[] readLogicalPaths(long[] pathIds,
                                         int[] userDataCategories)
                                  throws LODNetworkException

      Retrieves the logical paths for the specified path IDs.
      Parameters:
      `pathIds` - path IDs

      `userDataCategories` -

      Returns:
      logical paths

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalSubPath

          LogicalSubPath readLogicalSubPath(long subPathId,
                                            boolean includeUserData)
                                     throws LODNetworkException

      Retrieves the logical subpath for the specified subpath ID.
      Parameters:
      `subPathId` - subpath ID

      `includeUserData` - whether to include the userdata or not

      Returns:
      logical subpath

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalSubPaths

          LogicalSubPath[] readLogicalSubPaths(long[] subPathIds,
                                               boolean includeUserData)
                                        throws LODNetworkException

      Retrieves the logical subpaths for the specified subpath IDs.
      Parameters:
      `subPathIds` - subpath IDs

      `includeUserData` - whether to include the userdata or not

      Returns:
      logical subpaths

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalSubPath

          LogicalSubPath readLogicalSubPath(long subPathId,
                                            int[] userDataCategories)
                                     throws LODNetworkException

      Retrieves the logical subpath for the specified subpath ID.
      Parameters:
      `subPathId` - subpath ID

      `userDataCategories` -

      Returns:
      logical subpath

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalSubPaths

          LogicalSubPath[] readLogicalSubPaths(long[] subPathIds,
                                               int[] userDataCategories)
                                        throws LODNetworkException

      Retrieves the logical subpaths for the specified subpath IDs.
      Parameters:
      `subPathIds` - subpath IDs

      `userDataCategories` -

      Returns:
      logical subpaths

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalHeavyPath

          LogicalHeavyPath readLogicalHeavyPath(LogicalPath path,
                                                boolean includeUserData)
                                         throws LODNetworkException

      Retrieves node and link information for the specified logical path.
      Parameters:
      `path` - logical path without detailed node and link information

      `includeUserData` - whether to include user data or not

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalHeavyPaths

          LogicalHeavyPath[] readLogicalHeavyPaths(LogicalPath[] paths,
                                                   boolean includeUserData)
                                            throws LODNetworkException

      Retrieves node and link information for the specified logical paths.
      Parameters:
      `paths` - logical paths without detailed node and link information

      `includeUserData` - whether to include user data or not

      Returns:
      heavy logical paths, i.e., logical paths with detailed node and link information

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalHeavyPath

          LogicalHeavyPath readLogicalHeavyPath(LogicalPath path,
                                                int[] userDataCategories)
                                         throws LODNetworkException

      Retrieves node and link information for the specified logical path.
      Parameters:
      `path` - logical path without detailed node and link information

      `userDataCategories` -

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readLogicalHeavyPaths

          LogicalHeavyPath[] readLogicalHeavyPaths(LogicalPath[] paths,
                                                   int[] userDataCategories)
                                            throws LODNetworkException

      Retrieves node and link information for the specified logical paths.
      Parameters:
      `paths` - logical paths without detailed node and link information

      `userDataCategories` -

      Returns:
      heavy logical paths, i.e., logical paths with detailed node and link information

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSpatialNetwork

          SpatialBasicNetwork readSpatialNetwork(LogicalBasicNetwork logicalNetwork)
                                          throws LODNetworkException

      Retrieves spatial information for the logical network, and returns the spatial network.
      Parameters:
      `logicalNetwork` - logical network

      Returns:
      spatial network

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSpatialPartition

          SpatialPartition readSpatialPartition(LogicalPartition logicalPartition)
                                         throws LODNetworkException

      Retrieves spatial information for the logical network partition, and returns the spatial network partition.
      Parameters:
      `logicalPartition` - logical network partition

      Returns:
      spatial network partition

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSpatialPartition

          SpatialPartition readSpatialPartition(int partitionId,
                                                int linkLevel,
                                                int[] userDataCategories,
                                                int[] featureLayerIds)
                                         throws LODNetworkException

      Retrieves spatial partition.
      Parameters:
      `partitionId` - partitionId

      `linkLevel` - linkLevel

      `userDataCategories` - user data categories

      Returns:
      spatial network partition

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSpatialPartition

          SpatialPartition readSpatialPartition(int partitionId,
                                                int linkLevel,
                                                boolean includeUserData)
                                         throws LODNetworkException

      Retrieves spatial partition.
      Parameters:
      `partitionId` - partitionId

      `linkLevel` - linkLevel

      `includeUserData` - whether to include user data or not

      Returns:
      spatial network partition

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSpatialPartition

          SpatialPartition readSpatialPartition(int partitionId,
                                                int linkLevel,
                                                boolean includeUserData,
                                                boolean readFromBlob)
                                         throws LODNetworkException

      Retrieves spatial partition.
      Parameters:
      `partitionId` - partitionId

      `linkLevel` - linkLevel

      `includeUserData` - whether to include user data or not

      `readFromBlob` - whether to read from BLOB or not

      Returns:
      spatial network partition

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSpatialPartition

          SpatialPartition readSpatialPartition(int partitionId,
                                                int linkLevel,
                                                int[] userDataCategories,
                                                int[] featureLayerIds,
                                                boolean readFromBlob)
                                         throws LODNetworkException

      Retrieves spatial partition.
      Parameters:
      `partitionId` - partitionId

      `linkLevel` - linkLevel

      `userDataCategories` - user data categories

      `readFromBlob` - whether to read from BLOB or not

      Returns:
      spatial network partition

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSpatialPartitionMBR

          JGeometry readSpatialPartitionMBR(int partitionId,
                                            int linkLevel)
                                     throws LODNetworkException

      Returns the minimum bounding rectangle (MBR) encompassing all the **nodes** in the specified partition. Note that link geometries in the partition might cross the boundaries of the returned MBR.
      Parameters:
      `partitionId` - partition ID

      `linkLevel` - link level

      Returns:
      a polygon type JGeometry instance representing the MBR

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSpatialPartitionMBRs

          java.util.Map<java.lang.Integer,JGeometry> readSpatialPartitionMBRs(int linkLevel)
                                                                       throws LODNetworkException

      Returns the minimum bounding rectangles (MBR) of all the partitions in this network.
      Parameters:
      `linkLevel` - link level

      Returns:
      a map, whose keys are the partition IDs in the network, and whose values are polygon type JGeometry instances representing the MBRs of the corresponding partitions.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSpatialPath

          SpatialPath readSpatialPath(long pathId,
                                      boolean includeUserData)
                               throws LODNetworkException

      Retrieves the spatial path for the specified path ID.
      Parameters:
      `pathId` - path ID

      `includeUserData` - whether to include the userdata or not

      Returns:
      spatial path

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSpatialPath

          SpatialPath readSpatialPath(long pathId,
                                      int[] userDataCategories)
                               throws LODNetworkException

      Retrieves the spatial path for the specified path ID.
      Parameters:
      `pathId` - path ID

      `userDataCategories` - user data categories to be included

      Returns:
      spatial path

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSpatialPaths

          SpatialPath[] readSpatialPaths(long[] pathIds,
                                         boolean includeUserData)
                                  throws LODNetworkException

      Retrieves the spatial path for the specified path ID.
      Parameters:
      `pathIds` - path ID

      `includeUserData` - whether to include the userdata or not

      Returns:
      spatial path

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSpatialPaths

          SpatialPath[] readSpatialPaths(long[] pathIds,
                                         int[] userDataCategories)
                                  throws LODNetworkException

      Retrieves the spatial path for the specified path ID.
      Parameters:
      `pathIds` - path ID

      `userDataCategories` - user data categories to be included

      Returns:
      spatial path

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSpatialPath

          SpatialPath readSpatialPath(LogicalPath logicalPath)
                               throws LODNetworkException

      Retrieves the spatial information for the specified logical path, and returns the spatial path.
      Parameters:
      `logicalPath` - logical path

      Returns:
      spatial path

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSpatialPaths

          SpatialPath[] readSpatialPaths(LogicalPath[] logicalPath)
                                  throws LODNetworkException

      Retrieves the spatial information for the specified logical path, and returns the spatial path.
      Parameters:
      `logicalPath` - logical path

      Returns:
      spatial path

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSpatialSubPath

          SpatialSubPath readSpatialSubPath(long subPathId,
                                            boolean includeUserData)
                                     throws LODNetworkException

      Retrieves the spatial subpath information.
      Parameters:
      `subPathId` - subpath ID

      `includeUserData` - whether to include the userdata or not

      Returns:
      spatial subpath

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSpatialSubPath

          SpatialSubPath readSpatialSubPath(long subPathId,
                                            int[] userDataCategories)
                                     throws LODNetworkException

      Retrieves the spatial subpath information.
      Parameters:
      `subPathId` - subpath ID

      `userDataCategories` - user data categories to be included

      Returns:
      spatial subpath

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSpatialSubPaths

          SpatialSubPath[] readSpatialSubPaths(long[] subPathIds,
                                               boolean includeUserData)
                                        throws LODNetworkException

      Retrieves the spatial subpath information.
      Parameters:
      `subPathIds` - subpath IDs

      `includeUserData` - whether to include the userdata or not

      Returns:
      spatial subpath

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSpatialSubPaths

          SpatialSubPath[] readSpatialSubPaths(long[] subPathIds,
                                               int[] userDataCategories)
                                        throws LODNetworkException

      Retrieves the spatial subpath information.
      Parameters:
      `subPathIds` - subpath IDs

      `userDataCategories` - user data categories to be included

      Returns:
      spatial subpath

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSpatialSubPath

          SpatialSubPath readSpatialSubPath(LogicalSubPath logicalSubPath)
                                     throws LODNetworkException

      Retrieves the spatial information of the specified logical subpath, and returns the spatial subpath.
      Parameters:
      `logicalSubPath` - logical subpath

      Returns:
      spatial subpath

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSpatialSubPaths

          SpatialSubPath[] readSpatialSubPaths(LogicalSubPath[] logicalSubPaths)
                                        throws LODNetworkException

      Retrieves the spatial information of the specified logical subpaths, and returns the spatial subpath.
      Parameters:
      `logicalSubPaths` - logical subpath

      Returns:
      spatial subpaths

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSpatialHeavyPath

          SpatialHeavyPath readSpatialHeavyPath(LogicalPath path,
                                                boolean includeUserData)
                                         throws LODNetworkException

      Retrieves node and link information for the specified logical paths.
      Parameters:
      `path` - logical path without detailed node and link information

      `includeUserData` - whether to include user data or not

      Returns:
      heavy logical path, i.e., logical path with detailed node and link information

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSpatialHeavyPath

          SpatialHeavyPath readSpatialHeavyPath(LogicalPath path,
                                                int[] userDataCategories)
                                         throws LODNetworkException

      Retrieves node and link information for the specified logical paths.
      Parameters:
      `path` - logical path without detailed node and link information

      `userDataCategories` - user data categories to be included

      Returns:
      heavy logical path, i.e., logical path with detailed node and link information

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSpatialHeavyPaths

          SpatialHeavyPath[] readSpatialHeavyPaths(LogicalPath[] paths,
                                                   boolean includeUserData)
                                            throws LODNetworkException

      Retrieves node and link information for the specified logical paths.
      Parameters:
      `paths` - logical paths without detailed node and link information

      `includeUserData` - whether to include user data or not

      Returns:
      heavy logical paths, i.e., logical paths with detailed node and link information

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSpatialHeavyPaths

          SpatialHeavyPath[] readSpatialHeavyPaths(LogicalPath[] paths,
                                                   int[] userDataCategories)
                                            throws LODNetworkException

      Retrieves node and link information for the specified logical paths.
      Parameters:
      `paths` - logical paths without detailed node and link information

      `userDataCategories` - user data categories to be included

      Returns:
      heavy logical paths, i.e., logical paths with detailed node and link information

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSpatialLink

          SpatialLink readSpatialLink(long linkId,
                                      boolean includeUserData)
                               throws LODNetworkException

      Retrieves the spatial link for the specified link ID.
      Parameters:
      `linkId` - link ID

      Returns:
      spatial link

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSpatialLink

          SpatialLink readSpatialLink(long linkId,
                                      int[] userDataCategories)
                               throws LODNetworkException

      Retrieves the spatial link for the specified link ID.
      Parameters:
      `linkId` - link ID

      `userDataCategories` - user data categories to be included

      Returns:
      spatial link

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSpatialLinks

          SpatialLink[] readSpatialLinks(long[] linkIds,
                                         boolean includeUserData)
                                  throws LODNetworkException

      Retrieves the spatial links for the specified link IDs.
      Parameters:
      `linkIds` - link IDs

      Returns:
      spatial links

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSpatialLinks

          SpatialLink[] readSpatialLinks(long[] linkIds,
                                         int[] userDataCategories)
                                  throws LODNetworkException

      Retrieves the spatial links for the specified link IDs.
      Parameters:
      `linkIds` - link IDs

      `userDataCategories` - user data categories to be included

      Returns:
      spatial links

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSpatialNode

          SpatialNode readSpatialNode(long nodeId,
                                      boolean includeUserData)
                               throws LODNetworkException

      Retrieves the spatial node for the specified node ID.
      Parameters:
      `nodeId` - node ID

      Returns:
      spatial node

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSpatialNode

          SpatialNode readSpatialNode(long nodeId,
                                      int[] userDataCategories)
                               throws LODNetworkException

      Retrieves the spatial node for the specified node ID.
      Parameters:
      `nodeId` - node ID

      `userDataCategories` - user data categories to be included

      Returns:
      spatial node

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSpatialNodes

          SpatialNode[] readSpatialNodes(long[] nodeIds,
                                         boolean includeUserData)
                                  throws LODNetworkException

      Retrieves the spatial nodes for the specified node IDs.
      Parameters:
      `nodeIds` - node IDs

      Returns:
      spatial nodes

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSpatialNodes

          SpatialNode[] readSpatialNodes(long[] nodeIds,
                                         int[] userDataCategories)
                                  throws LODNetworkException

      Retrieves the spatial nodes for the specified node IDs.
      Parameters:
      `nodeIds` - node IDs

      `userDataCategories` - user data categories to be included

      Returns:
      spatial nodes

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readNumberOfLinkLevels

          int readNumberOfLinkLevels()
                              throws LODNetworkException

      Retrieves the number of link levels.
      Returns:
      number of link levels

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readMaximumLinkLevel

          int readMaximumLinkLevel()
                            throws LODNetworkException

      Retrieves the maximum link level of the network.
      Returns:
      maximum link level of the network

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readMaximumLinkLevel

          int readMaximumLinkLevel(long nodeId)
                            throws LODNetworkException

      Retrieves the maximum link level of the links connected to the specified node.
      Parameters:
      `nodeId` - node ID

      Returns:
      maximum link level

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readMaximumIncomingLinkLevel

          int readMaximumIncomingLinkLevel(long nodeId)
                                    throws LODNetworkException

      Retrieves the maximum link level of the incoming links connected to the specified node.
      Parameters:
      `nodeId` - node ID

      Returns:
      maximum incoming link level

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readMaximumOutgoingLinkLevel

          int readMaximumOutgoingLinkLevel(long nodeId)
                                    throws LODNetworkException

      Retrieves the maximum link level of the outgoing links connected to the specified node.
      Parameters:
      `nodeId` - node ID

      Returns:
      maximum outgoing link level

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readNetworkUpdate

          NetworkUpdate readNetworkUpdate(int linkLevel,
                                          long[] updatedNodeIds,
                                          long[] deletedNodeIds,
                                          long[] updatedLinkIds,
                                          long[] deletedLinkIds,
                                          int[] userDataCategories)
                                   throws LODNetworkException

      Constructs network update object according to the changed node and link IDs.
      Parameters:
      `linkLevel` - link level

      `updatedNodeIds` - new and updated node IDs

      `deletedNodeIds` - deleted node IDs

      `updatedLinkIds` - new and updated link IDs

      `deletedLinkIds` - deleted link IDs

      Returns:
      network update object

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readNetworkUpdate

          NetworkUpdate readNetworkUpdate(int linkLevel,
                                          long[] changedNodeIds,
                                          long[] changedLinkIds,
                                          int[] userDataCategories)
                                   throws LODNetworkException

      Constructs network update object according to the changed node and link IDs.
      Parameters:
      `linkLevel` - link level

      `changedNodeIds` - new, updated and deleted node IDs

      `changedLinkIds` - new, updated and deleted link IDs

      Returns:
      network update object

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readNetworkUpdate

          NetworkUpdate readNetworkUpdate(int linkLevel,
                                          java.util.Calendar lastUpdateTime,
                                          int[] userDataCategories)
                                   throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readNetworkUpdates

          NetworkUpdate[] readNetworkUpdates(java.util.Calendar lastUpdateTime,
                                             int[] userDataCategories)
                                      throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### writePath

          long writePath(LogicalPath path,
                         java.lang.String pathName,
                         java.lang.String pathType)
                  throws LODNetworkException

      Stores a path in the database.
      Parameters:
      `path` - path

      `pathName` - user specified path name

      `pathType` - user specified path type

      Returns:
      path ID

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### writePath

          void writePath(LogicalPath path,
                         long pathId,
                         java.lang.String pathName,
                         java.lang.String pathType)
                  throws LODNetworkException

      Stores a path in the database.
      Parameters:
      `path` - path

      `pathId` - path ID

      `pathName` - user specified path name

      `pathType` - user specified path type

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### writeSubPath

          long writeSubPath(LogicalSubPath subPath,
                            long referencePathId,
                            java.lang.String subPathName,
                            java.lang.String subPathType)
                     throws LODNetworkException

      Stores a sub-path in the database. Before calling this method, the reference path must have already been stored in the database.
      Parameters:
      `subPath` - sub-path

      `referencePathId` - reference path ID

      `subPathName` - user specified sub-path name

      `subPathType` - user specified sub-path type

      Returns:
      sub-path ID

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### writeSubPath

          void writeSubPath(LogicalSubPath subPath,
                            long subPathId,
                            long referencePathId,
                            java.lang.String subPathName,
                            java.lang.String subPathType)
                     throws LODNetworkException

      Stores a sub-path in the database. Before calling this method, the reference path must have already been stored in the database.
      Parameters:
      `subPath` - sub-path

      `subPathId` - sub-path ID

      `referencePathId` - reference path ID

      `subPathName` - user specified sub-path name

      `subPathType` - user specified sub-path type

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### deletePath

          void deletePath(long pathId)
                   throws LODNetworkException

      Deletes path.
      Parameters:
      `pathId` - path ID

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### deletePaths

          void deletePaths(long[] pathIds)
                    throws LODNetworkException

      Deletes paths.
      Parameters:
      `pathIds` - path IDs

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### deleteSubPath

          void deleteSubPath(long subPathId)
                      throws LODNetworkException

      Deletes sub-path.
      Parameters:
      `subPathId` - sub-path ID

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### deleteSubPaths

          void deleteSubPaths(long[] subPathIds)
                       throws LODNetworkException

      Deletes sub-paths.
      Parameters:
      `subPathIds` - sub-path IDs

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readNetworkBuffer

          NetworkBuffer readNetworkBuffer(long bufferId)
                                   throws LODNetworkException

      Reads the network buffer with the specified buffer ID. Use network name as the buffer name.
      Parameters:
      `bufferId` - ID of the network buffer

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readNetworkBuffer

          NetworkBuffer readNetworkBuffer(long bufferId,
                                          java.lang.String bufferName)
                                   throws LODNetworkException

      Reads the network buffer with the specified buffer ID.
      Parameters:
      `bufferId` - ID of the network buffer

      `bufferName` - name of the network buffer

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### writeNetworkBuffer

          long writeNetworkBuffer(NetworkBuffer buffer)
                           throws LODNetworkException

      Stores the network buffer into the database. An ID will be automatically assigned to this buffer. Network name is used as buffer name.
      Parameters:
      `buffer` - network buffer to be stored

      Returns:
      the ID of the network buffer

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### writeNetworkBuffer

          long writeNetworkBuffer(NetworkBuffer buffer,
                                  java.lang.String bufferName)
                           throws LODNetworkException

      Stores the network buffer into the database. An ID will be automatically assigned to this buffer.
      Parameters:
      `buffer` - network buffer to be stored

      Returns:
      the ID of the network buffer

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### writeNetworkBuffer

          void writeNetworkBuffer(NetworkBuffer networkBuffer,
                                  long bufferId)
                           throws LODNetworkException

      Stores the network buffer into the database. Use the network name as the buffer name.
      Parameters:
      `networkBuffer` - network buffer to be stored

      `bufferId` - ID of the network buffer in the database

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### writeNetworkBuffer

          void writeNetworkBuffer(NetworkBuffer networkBuffer,
                                  long bufferId,
                                  java.lang.String bufferName)
                           throws LODNetworkException

      Stores the network buffer into the database.
      Parameters:
      `networkBuffer` - network buffer to be stored

      `bufferId` - ID of the network buffer in the database

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### deleteNetworkBuffer

          void deleteNetworkBuffer(long id)
                            throws LODNetworkException

      Deletes the network buffer from the database. Use the network name as buffer name.
      Parameters:
      `id` - ID of the network buffer

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### deleteNetworkBuffer

          void deleteNetworkBuffer(long id,
                                   java.lang.String bufferName)
                            throws LODNetworkException

      Deletes the network buffer from the database.
      Parameters:
      `id` - ID of the network buffer

      `bufferName` - name of the network buffer

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### saveConnectedComponents

          void saveConnectedComponents(OrderedLongSet[] components,
                                       int linkLevel)
                                throws LODNetworkException

      Stores the connected components information in the component table.
      Parameters:
      `components` - array of connected components. Each connected component is represented by a set of node IDs.

      `linkLevel` - link level

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### generatePartitionBlobs

          void generatePartitionBlobs(int linkLevel,
                                      boolean includeUserData,
                                      boolean commitForEachBlob)
                               throws LODNetworkException

      Generates partition BLOBs for the specified link level. This method reads partition information from the network node and link tables/views directly, and writes the partition information to BLOB.
      Parameters:
      `linkLevel` - link level

      `includeUserData` - whether to include user data or not. If set to true, user data of category 0 will be included in the blob.

      `commitForEachBlob` - whether to call commit after writing the BLOB for each partition

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### generatePartitionBlobs

          void generatePartitionBlobs(boolean includeUserData,
                                      boolean commitForEachBlob,
                                      boolean performDeltaUpdate)
                               throws LODNetworkException

      Generates partition BLOBs for all link levels. Depending on the value of the flag performDeltaUpdate, partition information can be read from the original network node and link tables/views, or from the existing partition BLOBs combined with the information from the network update history table.
      Parameters:
      `includeUserData` - whether to include user data or not. If set to true, user data of category 0 will be included in the blob.

      `commitForEachBlob` - whether to call commit after writing the BLOB for each partition

      `performDeltaUpdate` - whether to use network update history to perform delta update on existing BLOBs or to reload the network information directly from the network node and link tables/views.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

      Since:
      Oracle Database 11g Release 2 (11.2)

    <!-- -->

    - #### generatePartitionBlobs

          void generatePartitionBlobs(int linkLevel,
                                      boolean includeUserData,
                                      boolean commitForEachBlob,
                                      boolean performDeltaUpdate)
                               throws LODNetworkException

      Generates partition BLOBs for the specified link level. Depending on the value of the flag performDeltaUpdate, partition information can be read from the original network node and link tables/views, or from the existing partition BLOBs combined with the information from the network update history table.
      Parameters:
      `linkLevel` - link level

      `includeUserData` - whether to include user data or not. If set to true, user data of category 0 will be included in the blob.

      `commitForEachBlob` - whether to call commit after writing the BLOB for each partition

      `performDeltaUpdate` - whether to use network update history to perform delta update on existing BLOBs or to reload the network information directly from the network node and link tables/views.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

      Since:
      Oracle Database 11g Release 2 (11.2)

    <!-- -->

    - #### generatePartitionBlob

          void generatePartitionBlob(int partitionId,
                                     int linkLevel,
                                     boolean includeUserData)
                              throws LODNetworkException

      Generate partition BLOB for the specified partition. This method reads partition information from the original network node and link tables/views directly, and writes the partition information to BLOB.
      Parameters:
      `partitionId` - partition ID

      `linkLevel` - link level

      `includeUserData` - whether to include user data or not. If set to true, user data of category 0 will be included in the blob.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### generatePartitionBlob

          void generatePartitionBlob(int partitionId,
                                     int linkLevel,
                                     boolean includeUserData,
                                     boolean performDeltaUpdate)
                              throws LODNetworkException

      Generates partition BLOB for the specified partition. Depending on the value of the flag performDeltaUpdate, partition information can be read from the original network node and link tables/views, or from the existing partition BLOB combined with the information from the network update history table.
      Parameters:
      `partitionId` - partition ID

      `linkLevel` - link level

      `includeUserData` - whether to include user data or not. If set to true, user data of category 0 will be included in the blob.

      `performDeltaUpdate` - whether to use network update history to perform delta update on existing BLOBs or to reload the network information directly from the network node and link tables/views.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

      Since:
      Oracle Database 11g Release 2 (11.2)

    <!-- -->

    - #### getNextTmpNodeId

          long getNextTmpNodeId()

      Returns the next temporary node ID.
      Returns:

    <!-- -->

    - #### getNextTmpLinkId

          long getNextTmpLinkId()

      Returns the next temporary link ID.
      Returns:

    <!-- -->

    - #### readFeatureData

          void readFeatureData(LogicalPartition partition,
                               int[] featureLayerIds,
                               int[] userDataCategories)
                        throws LODNetworkException

      Adds feature data to the logical partition
      Parameters:
      `partition` - logical partition

      `featureLayerIds` - feature layer IDs

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readFeatures

          Feature[] readFeatures(int featureLayerId,
                                 long[] featureIds,
                                 int[] userDataCategories)
                          throws LODNetworkException

      Read features.
      Parameters:
      `featureIds` - feature IDs

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### computeFeatureGeometries

          JGeometry[] computeFeatureGeometries(Feature[] features,
                                               int nodeGeomUserDataCategory,
                                               int nodeGeomUserDataIndex,
                                               int linkGeomUserDataCategory,
                                               int linkGeomUserDataIndex,
                                               boolean consolidate)
                                        throws LODNetworkException

      Constructs the feature geometry from the geometries of its network elements.
      Parameters:
      `features` -

      `nodeGeomUserDataCategory` -

      `nodeGeomUserDataIndex` -

      `linkGeomUserDataCategory` -

      `linkGeomUserDataIndex` -

      `consolidate` - whether to consolidate the overlapping points into one point and connect the links that touches each other into one link

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

- [Prev Class](NetworkExplorer.md)
- [Next Class](NetworkSearch.md)

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
