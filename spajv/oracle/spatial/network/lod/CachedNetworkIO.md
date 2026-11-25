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

- [Prev Class](BreadthFirstSearch.md)
- [Next Class](CachedNetworkIOWM.md)

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

## Interface CachedNetworkIO

- All Superinterfaces:
  [NetworkIO](NetworkIO.md)

  <!-- -->

  All Known Subinterfaces:
  [CachedNetworkIOWM](CachedNetworkIOWM.md)

  ------------------------------------------------------------------------



      public interface CachedNetworkIO
      extends NetworkIO

  This interface defines methods related to cached network input and output.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                               | Method and Description                                                                                              |
    |-------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
    | [`LeveledNetworkCache`](LeveledNetworkCache.md) | `getNetworkCache``()`<br>Returns the network cache for all link levels.                                             |
    | `void`                                          | `setNetworkCache``(`[`LeveledNetworkCache`](LeveledNetworkCache.md)` cache)`<br>Sets the network cache.             |
    | `void`                                          | `updateNetworkCache``(int linkLevel, `[`NetworkUpdate`](NetworkUpdate.md)` networkUpdate)`<br>Update network cache. |

    - ### Methods inherited from interface oracle.spatial.network.lod.[NetworkIO](NetworkIO.md)

      [`close`](NetworkIO.md)`, `[`commit`](NetworkIO.md)`, `[`computeFeatureGeometries`](NetworkIO.md)`, `[`deleteNetworkBuffer`](NetworkIO.md)`, `[`deleteNetworkBuffer`](NetworkIO.md)`, `[`deletePath`](NetworkIO.md)`, `[`deletePaths`](NetworkIO.md)`, `[`deleteSubPath`](NetworkIO.md)`, `[`deleteSubPaths`](NetworkIO.md)`, `[`generatePartitionBlob`](NetworkIO.md)`, `[`generatePartitionBlob`](NetworkIO.md)`, `[`generatePartitionBlobs`](NetworkIO.md)`, `[`generatePartitionBlobs`](NetworkIO.md)`, `[`generatePartitionBlobs`](NetworkIO.md)`, `[`getConnection`](NetworkIO.md)`, `[`getDataSource`](NetworkIO.md)`, `[`getGlobalNetworkName`](NetworkIO.md)`, `[`getNetworkIOConfig`](NetworkIO.md)`, `[`getNetworkMetadata`](NetworkIO.md)`, `[`getNetworkName`](NetworkIO.md)`, `[`getNextId`](NetworkIO.md)`, `[`getNextTmpLinkId`](NetworkIO.md)`, `[`getNextTmpNodeId`](NetworkIO.md)`, `[`getPartitionBlobTranslator`](NetworkIO.md)`, `[`getUserDataIOs`](NetworkIO.md)`, `[`hasLinks`](NetworkIO.md)`, `[`hasNodes`](NetworkIO.md)`, `[`isLinksExist`](NetworkIO.md)`, `[`isNodesExist`](NetworkIO.md)`, `[`isReadFromBlob`](NetworkIO.md)`, `[`open`](NetworkIO.md)`, `[`readAdjacentPartitionIdsForLinks`](NetworkIO.md)`, `[`readAdjacentPartitionIdsForNodes`](NetworkIO.md)`, `[`readArbitraryLogicalLink`](NetworkIO.md)`, `[`readArbitraryLogicalLinks`](NetworkIO.md)`, `[`readArbitraryLogicalNode`](NetworkIO.md)`, `[`readArbitraryLogicalNodes`](NetworkIO.md)`, `[`readComponentId`](NetworkIO.md)`, `[`readComponentIds`](NetworkIO.md)`, `[`readFeatureData`](NetworkIO.md)`, `[`readFeatures`](NetworkIO.md)`, `[`readLinkIds`](NetworkIO.md)`, `[`readLinkPartitionIds`](NetworkIO.md)`, `[`readLinkPartitionIds`](NetworkIO.md)`, `[`readLogicalHeavyPath`](NetworkIO.md)`, `[`readLogicalHeavyPath`](NetworkIO.md)`, `[`readLogicalHeavyPaths`](NetworkIO.md)`, `[`readLogicalHeavyPaths`](NetworkIO.md)`, `[`readLogicalLink`](NetworkIO.md)`, `[`readLogicalLink`](NetworkIO.md)`, `[`readLogicalLinks`](NetworkIO.md)`, `[`readLogicalLinks`](NetworkIO.md)`, `[`readLogicalLinks`](NetworkIO.md)`, `[`readLogicalNetwork`](NetworkIO.md)`, `[`readLogicalNetwork`](NetworkIO.md)`, `[`readLogicalNetwork`](NetworkIO.md)`, `[`readLogicalNetwork`](NetworkIO.md)`, `[`readLogicalNetwork`](NetworkIO.md)`, `[`readLogicalNode`](NetworkIO.md)`, `[`readLogicalNode`](NetworkIO.md)`, `[`readLogicalNodes`](NetworkIO.md)`, `[`readLogicalNodes`](NetworkIO.md)`, `[`readLogicalNodes`](NetworkIO.md)`, `[`readLogicalPartition`](NetworkIO.md)`, `[`readLogicalPartition`](NetworkIO.md)`, `[`readLogicalPartition`](NetworkIO.md)`, `[`readLogicalPartition`](NetworkIO.md)`, `[`readLogicalPartition`](NetworkIO.md)`, `[`readLogicalPartition`](NetworkIO.md)`, `[`readLogicalPartitions`](NetworkIO.md)`, `[`readLogicalPartitions`](NetworkIO.md)`, `[`readLogicalPartitions`](NetworkIO.md)`, `[`readLogicalPartitions`](NetworkIO.md)`, `[`readLogicalPartitions`](NetworkIO.md)`, `[`readLogicalPartitions`](NetworkIO.md)`, `[`readLogicalPath`](NetworkIO.md)`, `[`readLogicalPath`](NetworkIO.md)`, `[`readLogicalPaths`](NetworkIO.md)`, `[`readLogicalPaths`](NetworkIO.md)`, `[`readLogicalSubPath`](NetworkIO.md)`, `[`readLogicalSubPath`](NetworkIO.md)`, `[`readLogicalSubPaths`](NetworkIO.md)`, `[`readLogicalSubPaths`](NetworkIO.md)`, `[`readMaximumIncomingLinkLevel`](NetworkIO.md)`, `[`readMaximumLinkLevel`](NetworkIO.md)`, `[`readMaximumLinkLevel`](NetworkIO.md)`, `[`readMaximumOutgoingLinkLevel`](NetworkIO.md)`, `[`readNetworkBuffer`](NetworkIO.md)`, `[`readNetworkBuffer`](NetworkIO.md)`, `[`readNetworkUpdate`](NetworkIO.md)`, `[`readNetworkUpdate`](NetworkIO.md)`, `[`readNetworkUpdate`](NetworkIO.md)`, `[`readNetworkUpdates`](NetworkIO.md)`, `[`readNodeIds`](NetworkIO.md)`, `[`readNodePartitionId`](NetworkIO.md)`, `[`readNodePartitionIds`](NetworkIO.md)`, `[`readNumberOfConnectedComponents`](NetworkIO.md)`, `[`readNumberOfLinkLevels`](NetworkIO.md)`, `[`readNumberOfLinks`](NetworkIO.md)`, `[`readNumberOfNodes`](NetworkIO.md)`, `[`readNumberOfPartitions`](NetworkIO.md)`, `[`readPartitionId`](NetworkIO.md)`, `[`readPartitionIds`](NetworkIO.md)`, `[`readPartitionIds`](NetworkIO.md)`, `[`readSpatialHeavyPath`](NetworkIO.md)`, `[`readSpatialHeavyPath`](NetworkIO.md)`, `[`readSpatialHeavyPaths`](NetworkIO.md)`, `[`readSpatialHeavyPaths`](NetworkIO.md)`, `[`readSpatialLink`](NetworkIO.md)`, `[`readSpatialLink`](NetworkIO.md)`, `[`readSpatialLinks`](NetworkIO.md)`, `[`readSpatialLinks`](NetworkIO.md)`, `[`readSpatialNetwork`](NetworkIO.md)`, `[`readSpatialNode`](NetworkIO.md)`, `[`readSpatialNode`](NetworkIO.md)`, `[`readSpatialNodes`](NetworkIO.md)`, `[`readSpatialNodes`](NetworkIO.md)`, `[`readSpatialPartition`](NetworkIO.md)`, `[`readSpatialPartition`](NetworkIO.md)`, `[`readSpatialPartition`](NetworkIO.md)`, `[`readSpatialPartition`](NetworkIO.md)`, `[`readSpatialPartition`](NetworkIO.md)`, `[`readSpatialPartitionMBR`](NetworkIO.md)`, `[`readSpatialPartitionMBRs`](NetworkIO.md)`, `[`readSpatialPath`](NetworkIO.md)`, `[`readSpatialPath`](NetworkIO.md)`, `[`readSpatialPath`](NetworkIO.md)`, `[`readSpatialPaths`](NetworkIO.md)`, `[`readSpatialPaths`](NetworkIO.md)`, `[`readSpatialPaths`](NetworkIO.md)`, `[`readSpatialSubPath`](NetworkIO.md)`, `[`readSpatialSubPath`](NetworkIO.md)`, `[`readSpatialSubPath`](NetworkIO.md)`, `[`readSpatialSubPaths`](NetworkIO.md)`, `[`readSpatialSubPaths`](NetworkIO.md)`, `[`readSpatialSubPaths`](NetworkIO.md)`, `[`readUserData`](NetworkIO.md)`, `[`rollback`](NetworkIO.md)`, `[`saveConnectedComponents`](NetworkIO.md)`, `[`setConnection`](NetworkIO.md)`, `[`setDataSource`](NetworkIO.md)`, `[`setGlobalNetworkName`](NetworkIO.md)`, `[`setNetworkMetadata`](NetworkIO.md)`, `[`setPartitionBlobTranslator`](NetworkIO.md)`, `[`setReadFromBlob`](NetworkIO.md)`, `[`setUserDataIOs`](NetworkIO.md)`, `[`updatePartitionBlobInfo`](NetworkIO.md)`, `[`writeNetworkBuffer`](NetworkIO.md)`, `[`writeNetworkBuffer`](NetworkIO.md)`, `[`writeNetworkBuffer`](NetworkIO.md)`, `[`writeNetworkBuffer`](NetworkIO.md)`, `[`writePath`](NetworkIO.md)`, `[`writePath`](NetworkIO.md)`, `[`writeSubPath`](NetworkIO.md)`, `[`writeSubPath`](NetworkIO.md)

<!-- -->

- - ### Method Detail

    - #### getNetworkCache

          LeveledNetworkCache getNetworkCache()

      Returns the network cache for all link levels.
      Returns:
      network cache for the specified link level

    <!-- -->

    - #### setNetworkCache

          void setNetworkCache(LeveledNetworkCache cache)

      Sets the network cache.
      Parameters:
      `cache` -

    <!-- -->

    - #### updateNetworkCache

          void updateNetworkCache(int linkLevel,
                                  NetworkUpdate networkUpdate)
                           throws LODNetworkException

      Update network cache.
      Parameters:
      `linkLevel` - network link level

      `networkUpdate` - network update object that contains all the changes that should be applied to the network cache

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

- [Prev Class](BreadthFirstSearch.md)
- [Next Class](CachedNetworkIOWM.md)

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
