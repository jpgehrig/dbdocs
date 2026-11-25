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

- [Prev Class](LogicalNode.md)
- [Next Class](LogicalPartitionImpl.md)

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

## Interface LogicalPartition

- All Superinterfaces:
  java.lang.Cloneable, [LogicalBasicNetwork](LogicalBasicNetwork.md), [LogicalSubNetwork](LogicalSubNetwork.md)

  <!-- -->

  All Known Subinterfaces:
  [SpatialPartition](SpatialPartition.md)

  <!-- -->

  All Known Implementing Classes:
  [LogicalPartitionImpl](LogicalPartitionImpl.md)

  ------------------------------------------------------------------------



      public interface LogicalPartition
      extends LogicalSubNetwork

  This interface defines methods supported by a logical network partition.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                  |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `addNode``(`[`LogicalNetNode`](LogicalNetNode.md)` node, int partitionId)`<br>Adds a node to the network partition.                     |
    | `int[]`           | `getLinkPartitionIds``(long linkId)`<br>Returns the ID of the partitions that the start and end nodes of the input link belongs to.     |
    | `int`             | `getNodePartitionId``(long nodeId)`<br>Returns the ID of the partition that the input node belongs to.                                  |
    | `int`             | `getPartitionId``()`<br>Returns the partition ID of this partition.                                                                     |
    | `void`            | `setNodePartitionId``(long nodeId, int partitionId)`<br>Sets the partition the node belongs to.                                         |
    | `void`            | `update``(`[`PartitionUpdate`](PartitionUpdate.md)` pu)`<br>Updates this network partition with the input partition update information. |

    - ### Methods inherited from interface oracle.spatial.network.lod.[LogicalSubNetwork](LogicalSubNetwork.md)

      [`addNode`](LogicalSubNetwork.md)`, `[`getBoundaryLinkIds`](LogicalSubNetwork.md)`, `[`getExternalNodeIds`](LogicalSubNetwork.md)`, `[`getIncomingLinkIds`](LogicalSubNetwork.md)`, `[`getInternalBoundaryNodeIds`](LogicalSubNetwork.md)`, `[`getInternalLinkIds`](LogicalSubNetwork.md)`, `[`getInternalNodeIds`](LogicalSubNetwork.md)`, `[`getInternalNonBoundaryNodeIds`](LogicalSubNetwork.md)`, `[`getNumberOfBoundaryLinks`](LogicalSubNetwork.md)`, `[`getNumberOfExternalNodes`](LogicalSubNetwork.md)`, `[`getNumberOfIncomingLinks`](LogicalSubNetwork.md)`, `[`getNumberOfInternalLinks`](LogicalSubNetwork.md)`, `[`getNumberOfInternalNodes`](LogicalSubNetwork.md)`, `[`getNumberOfOutgoingLinks`](LogicalSubNetwork.md)`, `[`getOutgoingLinkIds`](LogicalSubNetwork.md)`, `[`isIncomingLink`](LogicalSubNetwork.md)`, `[`isInternalLink`](LogicalSubNetwork.md)`, `[`isInternalNode`](LogicalSubNetwork.md)`, `[`isOutgoingLink`](LogicalSubNetwork.md)

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.lod.[LogicalBasicNetwork](LogicalBasicNetwork.md)

      [`addFeatureLayer`](LogicalBasicNetwork.md)`, `[`addLink`](LogicalBasicNetwork.md)`, `[`addNode`](LogicalBasicNetwork.md)`, `[`addUserDataCategory`](LogicalBasicNetwork.md)`, `[`clone`](LogicalBasicNetwork.md)`, `[`getFeatureData`](LogicalBasicNetwork.md)`, `[`getLink`](LogicalBasicNetwork.md)`, `[`getLinkIds`](LogicalBasicNetwork.md)`, `[`getLinkLevel`](LogicalBasicNetwork.md)`, `[`getLinks`](LogicalBasicNetwork.md)`, `[`getName`](LogicalBasicNetwork.md)`, `[`getNode`](LogicalBasicNetwork.md)`, `[`getNodeIds`](LogicalBasicNetwork.md)`, `[`getNodes`](LogicalBasicNetwork.md)`, `[`getNumberOfLinks`](LogicalBasicNetwork.md)`, `[`getNumberOfNodes`](LogicalBasicNetwork.md)`, `[`getUserDataCategories`](LogicalBasicNetwork.md)`, `[`isFeatureLayerLoaded`](LogicalBasicNetwork.md)`, `[`isUserDataCategoryLoaded`](LogicalBasicNetwork.md)`, `[`isUserDataLoaded`](LogicalBasicNetwork.md)`, `[`removeLink`](LogicalBasicNetwork.md)`, `[`removeNode`](LogicalBasicNetwork.md)`, `[`setFeatureData`](LogicalBasicNetwork.md)`, `[`setIsUserDataLoaded`](LogicalBasicNetwork.md)

<!-- -->

- - ### Method Detail

    - #### getPartitionId

          int getPartitionId()

      Returns the partition ID of this partition.
      Returns:
      partition ID of this partition

    <!-- -->

    - #### addNode

          void addNode(LogicalNetNode node,
                       int partitionId)

      Adds a node to the network partition. The input partition ID can be the same as the partition ID of this network partition, in which case, the node to be added is an internal node; otherwise, the node is an external node, belong to a neighboring partition.
      Parameters:
      `node` - logical node

      `partitionId` - ID of the partition that the node belongs to

    <!-- -->

    - #### getNodePartitionId

          int getNodePartitionId(long nodeId)
                          throws NodeNotFoundException

      Returns the ID of the partition that the input node belongs to.
      Parameters:
      `nodeId` - node ID

      Returns:
      partition ID

      Throws:
      [`NodeNotFoundException`](NodeNotFoundException.md)

    <!-- -->

    - #### setNodePartitionId

          void setNodePartitionId(long nodeId,
                                  int partitionId)

      Sets the partition the node belongs to.
      Parameters:
      `nodeId` - node ID

      `partitionId` - partition ID

    <!-- -->

    - #### getLinkPartitionIds

          int[] getLinkPartitionIds(long linkId)
                             throws LinkNotFoundException

      Returns the ID of the partitions that the start and end nodes of the input link belongs to.
      Parameters:
      `linkId` - link ID

      Returns:
      partition IDs

      Throws:
      [`LinkNotFoundException`](LinkNotFoundException.md)

    <!-- -->

    - #### update

          void update(PartitionUpdate pu)
               throws LODNetworkException

      Updates this network partition with the input partition update information.
      Parameters:
      `pu` - partition update information

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

- [Prev Class](LogicalNode.md)
- [Next Class](LogicalPartitionImpl.md)

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
