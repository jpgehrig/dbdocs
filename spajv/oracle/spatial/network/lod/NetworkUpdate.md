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

- [Prev Class](NetworkSearch.md)
- [Next Class](NodeCostCalculator.md)

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

## Class NetworkUpdate

- java.lang.Object

- - oracle.spatial.network.lod.NetworkUpdate

<!-- -->

-

  ------------------------------------------------------------------------



      public class NetworkUpdate
      extends java.lang.Object

  A NetworkUpdate object contains network update information.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `NetworkUpdate``()`         |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                       | Method and Description                                                                                                                                         |
    |-----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                  | `deleteLink``(long linkId)`<br>Deletes a link from the network                                                                                                 |
    | `void`                                  | `deleteLink``(long linkId, int enclosingPartitionId)`<br>Deletes a link from the network                                                                       |
    | `void`                                  | `deleteNode``(long nodeId)`<br>Deletes a node from the network                                                                                                 |
    | `void`                                  | `deleteNode``(long nodeId, int enclosingPartitionId)`<br>Delete a node from the network.                                                                       |
    | `long[]`                                | `getDeletedLinkIds``()`                                                                                                                                        |
    | `long[]`                                | `getDeletedNodeIds``()`                                                                                                                                        |
    | [`LogicalLink`](LogicalLink.md)         | `getLink``(long linkId)`                                                                                                                                       |
    | [`LogicalNode`](LogicalNode.md)         | `getNode``(long nodeId)`                                                                                                                                       |
    | `int`                                   | `getNodePartitionId``(long nodeId)`<br>Returns the partition ID the node is assigned to.                                                                       |
    | [`PartitionUpdate`](PartitionUpdate.md) | `getPartitionUpdate``(int partitionId)`<br>Returns the update information of the specified partition.                                                          |
    | `int[]`                                 | `getUpdatedPartitionIds``()`<br>Returns the IDs of all the updated partitions.                                                                                 |
    | `boolean`                               | `isLinkDeleted``(long linkId)`                                                                                                                                 |
    | `boolean`                               | `isNodeDeleted``(long nodeId)`                                                                                                                                 |
    | `void`                                  | `setPartitionUpdate``(int partitionId, `[`PartitionUpdate`](PartitionUpdate.md)` partitionUpdate)`<br>Sets the update information for the specified partition. |
    | `void`                                  | `updateLink``(`[`LogicalLink`](LogicalLink.md)` link, int enclosingPartitionId)`<br>Adds or updates a link in the network                                      |
    | `void`                                  | `updateNode``(`[`LogicalNode`](LogicalNode.md)` node, int enclosingPartitionId, int nodePartitionId)`<br>Adds or updates a node in the network.                |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NetworkUpdate

          public NetworkUpdate()

  <!-- -->

  - ### Method Detail

    - #### getUpdatedPartitionIds

          public int[] getUpdatedPartitionIds()

      Returns the IDs of all the updated partitions.
      Returns:
      partition IDs

    <!-- -->

    - #### getPartitionUpdate

          public PartitionUpdate getPartitionUpdate(int partitionId)

      Returns the update information of the specified partition.
      Parameters:
      `partitionId` - partition ID

      Returns:
      partition update information

    <!-- -->

    - #### setPartitionUpdate

          public void setPartitionUpdate(int partitionId,
                                         PartitionUpdate partitionUpdate)

      Sets the update information for the specified partition.
      Parameters:
      `partitionId` - partition ID

      `partitionUpdate` - partition update information

    <!-- -->

    - #### updateNode

          public void updateNode(LogicalNode node,
                                 int enclosingPartitionId,
                                 int nodePartitionId)

      Adds or updates a node in the network.
      Parameters:
      `node` - node to be updated

      `enclosingPartitionId` - the network partition to update the node in. Note that, when the node is an external node in the enclosing partition, the enclosing partition ID is different from the partition ID the node is assigned to.

      `nodePartitionId` - the partition ID the node is assigned to

    <!-- -->

    - #### deleteNode

          public void deleteNode(long nodeId,
                                 int enclosingPartitionId)

      Delete a node from the network.
      Parameters:
      `nodeId` - ID of the node to be deleted

      `enclosingPartitionId` - the network partition to delete the node from. Note that, when the node is an external node in the enclosing partition, the enclosing partition ID is different from the partition ID the node is assigned to.

    <!-- -->

    - #### deleteNode

          public void deleteNode(long nodeId)

      Deletes a node from the network
      Parameters:
      `nodeId` - ID of the node to be deleted

    <!-- -->

    - #### updateLink

          public void updateLink(LogicalLink link,
                                 int enclosingPartitionId)

      Adds or updates a link in the network
      Parameters:
      `link` - link to be updated

      `enclosingPartitionId` - the network partition to update the link in

    <!-- -->

    - #### deleteLink

          public void deleteLink(long linkId,
                                 int enclosingPartitionId)

      Deletes a link from the network
      Parameters:
      `linkId` - ID of the link to be deleted

      `enclosingPartitionId` - the network partition to delete the link from

    <!-- -->

    - #### deleteLink

          public void deleteLink(long linkId)

      Deletes a link from the network
      Parameters:
      `linkId` - ID of the link to be deleted

    <!-- -->

    - #### getNodePartitionId

          public int getNodePartitionId(long nodeId)

      Returns the partition ID the node is assigned to.
      Parameters:
      `nodeId` - node ID

      Returns:
      ID of the partition the node is assigned to

    <!-- -->

    - #### getNode

          public LogicalNode getNode(long nodeId)

    <!-- -->

    - #### getLink

          public LogicalLink getLink(long linkId)

    <!-- -->

    - #### getDeletedNodeIds

          public long[] getDeletedNodeIds()

    <!-- -->

    - #### getDeletedLinkIds

          public long[] getDeletedLinkIds()

    <!-- -->

    - #### isLinkDeleted

          public boolean isLinkDeleted(long linkId)

    <!-- -->

    - #### isNodeDeleted

          public boolean isNodeDeleted(long nodeId)

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

- [Prev Class](NetworkSearch.md)
- [Next Class](NodeCostCalculator.md)

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
