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

- [Prev Class](LogicalPartition.md)
- [Next Class](LogicalPath.md)

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

## Class LogicalPartitionImpl

- java.lang.Object

- - oracle.spatial.network.lod.LogicalPartitionImpl

<!-- -->

- All Implemented Interfaces:
  java.lang.Cloneable, [LogicalBasicNetwork](LogicalBasicNetwork.md), [LogicalPartition](LogicalPartition.md), [LogicalSubNetwork](LogicalSubNetwork.md)

  ------------------------------------------------------------------------



      public class LogicalPartitionImpl
      extends java.lang.Object
      implements LogicalPartition

  Default implementation of LogicalPartition.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                             |
    |-----------------------------------------------------------------------------------------|
    | `LogicalPartitionImpl``(java.lang.String networkName, int partitionId, int linkLevel)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                         | Method and Description                                                                                                                            |
    |-------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                    | `addFeatureLayer``(int featureLayerId, `[`FeatureLayer`](FeatureLayer.md)` featureLayer)`<br>Adds the feature layer.                              |
    | `void`                                    | `addLink``(`[`LogicalNetLink`](LogicalNetLink.md)` link)`<br>Adds a logical link to the network.                                                  |
    | `void`                                    | `addNode``(`[`LogicalNetNode`](LogicalNetNode.md)` node)`<br>Adds a logical node to the network.                                                  |
    | `void`                                    | `addNode``(`[`LogicalNetNode`](LogicalNetNode.md)` node, boolean isInternal)`<br>Adds a logical node to the sub-network.                          |
    | `void`                                    | `addNode``(`[`LogicalNetNode`](LogicalNetNode.md)` node, int partitionId)`<br>Adds a node to the network partition.                               |
    | `void`                                    | `addUserDataCategories``(int[] userDataCategories)`                                                                                               |
    | `void`                                    | `addUserDataCategory``(int userDataCategory)`<br>Adds the user data category that have been loaded to the network.                                |
    | `java.lang.Object`                        | `clone``()`<br>Supports cloneable                                                                                                                 |
    | `long[]`                                  | `getBoundaryLinkIds``()`<br>Returns all the boundary link IDs in the sub-network.                                                                 |
    | `long[]`                                  | `getExternalNodeIds``()`<br>Returns all the external node IDs in the sub-network.                                                                 |
    | [`FeatureData`](FeatureData.md)           | `getFeatureData``()`<br>Returns the feature data associated to this network.                                                                      |
    | `long[]`                                  | `getIncomingLinkIds``()`<br>Returns all the incoming link IDs in the sub-network.                                                                 |
    | `long[]`                                  | `getInternalBoundaryNodeIds``()`<br>Returns all the internal node IDs in the sub-network without a link to any external nodes.                    |
    | `long[]`                                  | `getInternalLinkIds``()`<br>Returns all the internal link IDs in the sub-network.                                                                 |
    | `long[]`                                  | `getInternalNodeIds``()`<br>Returns all the internal node IDs in the sub-network.                                                                 |
    | `long[]`                                  | `getInternalNonBoundaryNodeIds``()`<br>Returns all the internal node IDs in the sub-network without a link to any external nodes.                 |
    | [`LogicalNetLink`](LogicalNetLink.md)     | `getLink``(long linkId)`<br>Returns the logical link object for the specified link id.                                                            |
    | `long[]`                                  | `getLinkIds``()`<br>Returns all the link ids in the network.                                                                                      |
    | `int`                                     | `getLinkLevel``()`<br>Returns the link level of the network.                                                                                      |
    | `int[]`                                   | `getLinkPartitionIds``(long linkId)`<br>Returns the ID of the partitions that the start and end nodes of the input link belongs to.               |
    | [`LogicalNetLink`](LogicalNetLink.md)`[]` | `getLinks``()`<br>Returns all the links in the network.                                                                                           |
    | `java.lang.String`                        | `getName``()`<br>Returns the internal network name, for example, the network name stored in network metadata table.                               |
    | [`LogicalNetNode`](LogicalNetNode.md)     | `getNode``(long nodeId)`<br>Returns the logical node object for the specified node id.                                                            |
    | `long[]`                                  | `getNodeIds``()`<br>Returns all the node ids in the network.                                                                                      |
    | `int`                                     | `getNodePartitionId``(long nodeId)`<br>Returns the ID of the partition that the input node belongs to.                                            |
    | [`LogicalNetNode`](LogicalNetNode.md)`[]` | `getNodes``()`<br>Returns all the nodes in the network.                                                                                           |
    | `int`                                     | `getNumberOfBoundaryLinks``()`<br>Returns the number of boundary links in the sub-network, which includes both incoming links and outgoing links. |
    | `int`                                     | `getNumberOfExternalNodes``()`<br>Returns the number of external nodes in the sub-network.                                                        |
    | `int`                                     | `getNumberOfIncomingLinks``()`<br>Returns the number of incoming links to the sub-network.                                                        |
    | `int`                                     | `getNumberOfInternalLinks``()`<br>Returns the number of internal links in the sub-network.                                                        |
    | `int`                                     | `getNumberOfInternalNodes``()`<br>Returns the number of internal nodes in the sub-network.                                                        |
    | `int`                                     | `getNumberOfLinks``()`<br>Returns the total number of links in the network.                                                                       |
    | `int`                                     | `getNumberOfNodes``()`<br>Returns the total number of nodes in the network.                                                                       |
    | `int`                                     | `getNumberOfOutgoingLinks``()`<br>Returns the number of outgoing links from the sub-network.                                                      |
    | `long[]`                                  | `getOutgoingLinkIds``()`<br>Returns all the outgoing link IDs in the sub-network.                                                                 |
    | `int`                                     | `getPartitionId``()`<br>Returns the partition ID of this partition.                                                                               |
    | `int[]`                                   | `getUserDataCategories``()`<br>Returns the user data categories loaded in the network.                                                            |
    | `boolean`                                 | `isFeatureLayerLoaded``(int featureLayerId)`<br>Returns whether the specified user data category is loaded.                                       |
    | `boolean`                                 | `isIncomingLink``(long linkId)`<br>Checks whether the input link is an incoming link or not.                                                      |
    | `boolean`                                 | `isInternalLink``(long linkId)`<br>Checks whether the input link is an internal link or not.                                                      |
    | `boolean`                                 | `isInternalNode``(long nodeId)`<br>Checks whether the input node is an internal node or not.                                                      |
    | `boolean`                                 | `isOutgoingLink``(long linkId)`<br>Checks whether the input link is an outgoing link or not.                                                      |
    | `boolean`                                 | `isUserDataCategoryLoaded``(int category)`<br>Returns whether the specified user data category is loaded.                                         |
    | `boolean`                                 | `isUserDataLoaded``()`<br>Deprecated.                                                                                                             |
    | `void`                                    | `removeLink``(long linkId)`<br>Removes a link from the network.                                                                                   |
    | `void`                                    | `removeNode``(long nodeId)`<br>Removes a node from the network.                                                                                   |
    | `void`                                    | `setFeatureData``(`[`FeatureData`](FeatureData.md)` featureData)`<br>Sets the feature data associated to this network.                            |
    | `void`                                    | `setIsUserDataLoaded``(boolean isUserDataLoaded)`<br>Deprecated.                                                                                  |
    | `void`                                    | `setNodePartitionId``(long nodeId, int partitionId)`<br>Sets the partition the node belongs to.                                                   |
    | `void`                                    | `update``(`[`PartitionUpdate`](PartitionUpdate.md)` pu)`<br>Updates this network partition with the input partition update information.           |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.lod.[LogicalSubNetwork](LogicalSubNetwork.md)

      [`addNode`](LogicalSubNetwork.md)`, `[`getBoundaryLinkIds`](LogicalSubNetwork.md)`, `[`getExternalNodeIds`](LogicalSubNetwork.md)`, `[`getIncomingLinkIds`](LogicalSubNetwork.md)`, `[`getInternalBoundaryNodeIds`](LogicalSubNetwork.md)`, `[`getInternalLinkIds`](LogicalSubNetwork.md)`, `[`getInternalNodeIds`](LogicalSubNetwork.md)`, `[`getInternalNonBoundaryNodeIds`](LogicalSubNetwork.md)`, `[`getNumberOfBoundaryLinks`](LogicalSubNetwork.md)`, `[`getNumberOfExternalNodes`](LogicalSubNetwork.md)`, `[`getNumberOfIncomingLinks`](LogicalSubNetwork.md)`, `[`getNumberOfInternalLinks`](LogicalSubNetwork.md)`, `[`getNumberOfInternalNodes`](LogicalSubNetwork.md)`, `[`getNumberOfOutgoingLinks`](LogicalSubNetwork.md)`, `[`getOutgoingLinkIds`](LogicalSubNetwork.md)`, `[`isIncomingLink`](LogicalSubNetwork.md)`, `[`isInternalLink`](LogicalSubNetwork.md)`, `[`isInternalNode`](LogicalSubNetwork.md)`, `[`isOutgoingLink`](LogicalSubNetwork.md)

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.lod.[LogicalBasicNetwork](LogicalBasicNetwork.md)

      [`addFeatureLayer`](LogicalBasicNetwork.md)`, `[`addLink`](LogicalBasicNetwork.md)`, `[`addNode`](LogicalBasicNetwork.md)`, `[`addUserDataCategory`](LogicalBasicNetwork.md)`, `[`getFeatureData`](LogicalBasicNetwork.md)`, `[`getLink`](LogicalBasicNetwork.md)`, `[`getLinkIds`](LogicalBasicNetwork.md)`, `[`getLinkLevel`](LogicalBasicNetwork.md)`, `[`getLinks`](LogicalBasicNetwork.md)`, `[`getName`](LogicalBasicNetwork.md)`, `[`getNode`](LogicalBasicNetwork.md)`, `[`getNodeIds`](LogicalBasicNetwork.md)`, `[`getNodes`](LogicalBasicNetwork.md)`, `[`getNumberOfLinks`](LogicalBasicNetwork.md)`, `[`getNumberOfNodes`](LogicalBasicNetwork.md)`, `[`getUserDataCategories`](LogicalBasicNetwork.md)`, `[`isFeatureLayerLoaded`](LogicalBasicNetwork.md)`, `[`isUserDataCategoryLoaded`](LogicalBasicNetwork.md)`, `[`isUserDataLoaded`](LogicalBasicNetwork.md)`, `[`removeLink`](LogicalBasicNetwork.md)`, `[`setFeatureData`](LogicalBasicNetwork.md)`, `[`setIsUserDataLoaded`](LogicalBasicNetwork.md)

<!-- -->

- - ### Constructor Detail

    - #### LogicalPartitionImpl

          public LogicalPartitionImpl(java.lang.String networkName,
                                      int partitionId,
                                      int linkLevel)

  <!-- -->

  - ### Method Detail

    - #### getPartitionId

          public int getPartitionId()

      Description copied from interface: [`LogicalPartition`](LogicalPartition.md)
      Returns the partition ID of this partition.
      Specified by:
      [`getPartitionId`](LogicalPartition.md) in interface [`LogicalPartition`](LogicalPartition.md)

      Returns:
      partition ID of this partition

    <!-- -->

    - #### addNode

          public void addNode(LogicalNetNode node,
                              int partitionId)

      Description copied from interface: [`LogicalPartition`](LogicalPartition.md)
      Adds a node to the network partition. The input partition ID can be the same as the partition ID of this network partition, in which case, the node to be added is an internal node; otherwise, the node is an external node, belong to a neighboring partition.
      Specified by:
      [`addNode`](LogicalPartition.md) in interface [`LogicalPartition`](LogicalPartition.md)

      Parameters:
      `node` - logical node

      `partitionId` - ID of the partition that the node belongs to

    <!-- -->

    - #### getNodePartitionId

          public int getNodePartitionId(long nodeId)
                                 throws NodeNotFoundException

      Description copied from interface: [`LogicalPartition`](LogicalPartition.md)
      Returns the ID of the partition that the input node belongs to.
      Specified by:
      [`getNodePartitionId`](LogicalPartition.md) in interface [`LogicalPartition`](LogicalPartition.md)

      Parameters:
      `nodeId` - node ID

      Returns:
      partition ID

      Throws:
      [`NodeNotFoundException`](NodeNotFoundException.md)

    <!-- -->

    - #### setNodePartitionId

          public void setNodePartitionId(long nodeId,
                                         int partitionId)

      Description copied from interface: [`LogicalPartition`](LogicalPartition.md)
      Sets the partition the node belongs to.
      Specified by:
      [`setNodePartitionId`](LogicalPartition.md) in interface [`LogicalPartition`](LogicalPartition.md)

      Parameters:
      `nodeId` - node ID

      `partitionId` - partition ID

    <!-- -->

    - #### getLinkPartitionIds

          public int[] getLinkPartitionIds(long linkId)
                                    throws LinkNotFoundException

      Description copied from interface: [`LogicalPartition`](LogicalPartition.md)
      Returns the ID of the partitions that the start and end nodes of the input link belongs to.
      Specified by:
      [`getLinkPartitionIds`](LogicalPartition.md) in interface [`LogicalPartition`](LogicalPartition.md)

      Parameters:
      `linkId` - link ID

      Returns:
      partition IDs

      Throws:
      [`LinkNotFoundException`](LinkNotFoundException.md)

    <!-- -->

    - #### removeNode

          public void removeNode(long nodeId)

      Description copied from interface: [`LogicalBasicNetwork`](LogicalBasicNetwork.md)
      Removes a node from the network.
      Specified by:
      [`removeNode`](LogicalBasicNetwork.md) in interface [`LogicalBasicNetwork`](LogicalBasicNetwork.md)

      Parameters:
      `nodeId` - ID of the node to be removed

    <!-- -->

    - #### update

          public void update(PartitionUpdate pu)
                      throws LODNetworkException

      Description copied from interface: [`LogicalPartition`](LogicalPartition.md)
      Updates this network partition with the input partition update information.
      Specified by:
      [`update`](LogicalPartition.md) in interface [`LogicalPartition`](LogicalPartition.md)

      Parameters:
      `pu` - partition update information

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### clone

          public java.lang.Object clone()
                                 throws java.lang.CloneNotSupportedException

      Description copied from interface: [`LogicalBasicNetwork`](LogicalBasicNetwork.md)
      Supports cloneable
      Specified by:
      [`clone`](LogicalBasicNetwork.md) in interface [`LogicalBasicNetwork`](LogicalBasicNetwork.md)

      Returns:
      cloned object

      Throws:
      `java.lang.CloneNotSupportedException`

    <!-- -->

    - #### getNumberOfInternalNodes

          public int getNumberOfInternalNodes()

      Description copied from interface: [`LogicalSubNetwork`](LogicalSubNetwork.md)
      Returns the number of internal nodes in the sub-network.
      Specified by:
      [`getNumberOfInternalNodes`](LogicalSubNetwork.md) in interface [`LogicalSubNetwork`](LogicalSubNetwork.md)

      Returns:
      number of internal nodes

    <!-- -->

    - #### getNumberOfExternalNodes

          public int getNumberOfExternalNodes()

      Description copied from interface: [`LogicalSubNetwork`](LogicalSubNetwork.md)
      Returns the number of external nodes in the sub-network.
      Specified by:
      [`getNumberOfExternalNodes`](LogicalSubNetwork.md) in interface [`LogicalSubNetwork`](LogicalSubNetwork.md)

      Returns:
      number of external nodes

    <!-- -->

    - #### getInternalNodeIds

          public long[] getInternalNodeIds()

      Description copied from interface: [`LogicalSubNetwork`](LogicalSubNetwork.md)
      Returns all the internal node IDs in the sub-network.
      Specified by:
      [`getInternalNodeIds`](LogicalSubNetwork.md) in interface [`LogicalSubNetwork`](LogicalSubNetwork.md)

      Returns:
      array of internal node IDs

    <!-- -->

    - #### getInternalBoundaryNodeIds

          public long[] getInternalBoundaryNodeIds()

      Description copied from interface: [`LogicalSubNetwork`](LogicalSubNetwork.md)
      Returns all the internal node IDs in the sub-network without a link to any external nodes.
      Specified by:
      [`getInternalBoundaryNodeIds`](LogicalSubNetwork.md) in interface [`LogicalSubNetwork`](LogicalSubNetwork.md)

      Returns:
      array of internal boundary node IDs

    <!-- -->

    - #### getInternalNonBoundaryNodeIds

          public long[] getInternalNonBoundaryNodeIds()

      Description copied from interface: [`LogicalSubNetwork`](LogicalSubNetwork.md)
      Returns all the internal node IDs in the sub-network without a link to any external nodes.
      Specified by:
      [`getInternalNonBoundaryNodeIds`](LogicalSubNetwork.md) in interface [`LogicalSubNetwork`](LogicalSubNetwork.md)

      Returns:
      array of internal non-boundary node IDs

    <!-- -->

    - #### getExternalNodeIds

          public long[] getExternalNodeIds()

      Description copied from interface: [`LogicalSubNetwork`](LogicalSubNetwork.md)
      Returns all the external node IDs in the sub-network.
      Specified by:
      [`getExternalNodeIds`](LogicalSubNetwork.md) in interface [`LogicalSubNetwork`](LogicalSubNetwork.md)

      Returns:
      array of external node IDs

    <!-- -->

    - #### isInternalNode

          public boolean isInternalNode(long nodeId)

      Description copied from interface: [`LogicalSubNetwork`](LogicalSubNetwork.md)
      Checks whether the input node is an internal node or not.
      Specified by:
      [`isInternalNode`](LogicalSubNetwork.md) in interface [`LogicalSubNetwork`](LogicalSubNetwork.md)

      Parameters:
      `nodeId` - node id

      Returns:
      true, if the input node is an internal node; false, otherwise.

    <!-- -->

    - #### isInternalLink

          public boolean isInternalLink(long linkId)

      Description copied from interface: [`LogicalSubNetwork`](LogicalSubNetwork.md)
      Checks whether the input link is an internal link or not.
      Specified by:
      [`isInternalLink`](LogicalSubNetwork.md) in interface [`LogicalSubNetwork`](LogicalSubNetwork.md)

      Parameters:
      `linkId` - link ID

      Returns:
      true, if the input link is an internal link; false, otherwise.

    <!-- -->

    - #### isIncomingLink

          public boolean isIncomingLink(long linkId)

      Description copied from interface: [`LogicalSubNetwork`](LogicalSubNetwork.md)
      Checks whether the input link is an incoming link or not.
      Specified by:
      [`isIncomingLink`](LogicalSubNetwork.md) in interface [`LogicalSubNetwork`](LogicalSubNetwork.md)

      Parameters:
      `linkId` - link ID

      Returns:
      true, if the input link is an incoming link; false, otherwise.

    <!-- -->

    - #### isOutgoingLink

          public boolean isOutgoingLink(long linkId)

      Description copied from interface: [`LogicalSubNetwork`](LogicalSubNetwork.md)
      Checks whether the input link is an outgoing link or not.
      Specified by:
      [`isOutgoingLink`](LogicalSubNetwork.md) in interface [`LogicalSubNetwork`](LogicalSubNetwork.md)

      Parameters:
      `linkId` - link ID

      Returns:
      true, if the input link is an outgoing link; false, otherwise.

    <!-- -->

    - #### getInternalLinkIds

          public long[] getInternalLinkIds()

      Description copied from interface: [`LogicalSubNetwork`](LogicalSubNetwork.md)
      Returns all the internal link IDs in the sub-network.
      Specified by:
      [`getInternalLinkIds`](LogicalSubNetwork.md) in interface [`LogicalSubNetwork`](LogicalSubNetwork.md)

      Returns:
      array of internal link IDs.

    <!-- -->

    - #### getBoundaryLinkIds

          public long[] getBoundaryLinkIds()

      Description copied from interface: [`LogicalSubNetwork`](LogicalSubNetwork.md)
      Returns all the boundary link IDs in the sub-network.
      Specified by:
      [`getBoundaryLinkIds`](LogicalSubNetwork.md) in interface [`LogicalSubNetwork`](LogicalSubNetwork.md)

      Returns:
      array of boundary link IDs.

    <!-- -->

    - #### getIncomingLinkIds

          public long[] getIncomingLinkIds()

      Description copied from interface: [`LogicalSubNetwork`](LogicalSubNetwork.md)
      Returns all the incoming link IDs in the sub-network.
      Specified by:
      [`getIncomingLinkIds`](LogicalSubNetwork.md) in interface [`LogicalSubNetwork`](LogicalSubNetwork.md)

      Returns:
      array of incoming link IDs.

    <!-- -->

    - #### getOutgoingLinkIds

          public long[] getOutgoingLinkIds()

      Description copied from interface: [`LogicalSubNetwork`](LogicalSubNetwork.md)
      Returns all the outgoing link IDs in the sub-network.
      Specified by:
      [`getOutgoingLinkIds`](LogicalSubNetwork.md) in interface [`LogicalSubNetwork`](LogicalSubNetwork.md)

      Returns:
      array of outgoing link IDs.

    <!-- -->

    - #### getNumberOfInternalLinks

          public int getNumberOfInternalLinks()

      Description copied from interface: [`LogicalSubNetwork`](LogicalSubNetwork.md)
      Returns the number of internal links in the sub-network.
      Specified by:
      [`getNumberOfInternalLinks`](LogicalSubNetwork.md) in interface [`LogicalSubNetwork`](LogicalSubNetwork.md)

      Returns:
      number of internal links

    <!-- -->

    - #### getNumberOfBoundaryLinks

          public int getNumberOfBoundaryLinks()

      Description copied from interface: [`LogicalSubNetwork`](LogicalSubNetwork.md)
      Returns the number of boundary links in the sub-network, which includes both incoming links and outgoing links.
      Specified by:
      [`getNumberOfBoundaryLinks`](LogicalSubNetwork.md) in interface [`LogicalSubNetwork`](LogicalSubNetwork.md)

      Returns:
      number of boundary links

    <!-- -->

    - #### getNumberOfIncomingLinks

          public int getNumberOfIncomingLinks()

      Description copied from interface: [`LogicalSubNetwork`](LogicalSubNetwork.md)
      Returns the number of incoming links to the sub-network.
      Specified by:
      [`getNumberOfIncomingLinks`](LogicalSubNetwork.md) in interface [`LogicalSubNetwork`](LogicalSubNetwork.md)

      Returns:
      number of incoming links

    <!-- -->

    - #### getNumberOfOutgoingLinks

          public int getNumberOfOutgoingLinks()

      Description copied from interface: [`LogicalSubNetwork`](LogicalSubNetwork.md)
      Returns the number of outgoing links from the sub-network.
      Specified by:
      [`getNumberOfOutgoingLinks`](LogicalSubNetwork.md) in interface [`LogicalSubNetwork`](LogicalSubNetwork.md)

      Returns:
      number of outgoing links

    <!-- -->

    - #### addNode

          public void addNode(LogicalNetNode node,
                              boolean isInternal)

      Description copied from interface: [`LogicalSubNetwork`](LogicalSubNetwork.md)
      Adds a logical node to the sub-network.
      Specified by:
      [`addNode`](LogicalSubNetwork.md) in interface [`LogicalSubNetwork`](LogicalSubNetwork.md)

      Parameters:
      `node` - logical node

      `isInternal` - set to true, if the node is an internal node; false, otherwise.

    <!-- -->

    - #### getLinkLevel

          public int getLinkLevel()

      Description copied from interface: [`LogicalBasicNetwork`](LogicalBasicNetwork.md)
      Returns the link level of the network.
      Specified by:

      [`getLinkLevel`](LogicalBasicNetwork.md) in interface [`LogicalBasicNetwork`](LogicalBasicNetwork.md)

      Returns:

    <!-- -->

    - #### addLink

          public void addLink(LogicalNetLink link)

      Description copied from interface: [`LogicalBasicNetwork`](LogicalBasicNetwork.md)
      Adds a logical link to the network.
      Specified by:
      [`addLink`](LogicalBasicNetwork.md) in interface [`LogicalBasicNetwork`](LogicalBasicNetwork.md)

      Parameters:
      `link` - logical link

    <!-- -->

    - #### addNode

          public void addNode(LogicalNetNode node)

      Description copied from interface: [`LogicalBasicNetwork`](LogicalBasicNetwork.md)
      Adds a logical node to the network.
      Specified by:
      [`addNode`](LogicalBasicNetwork.md) in interface [`LogicalBasicNetwork`](LogicalBasicNetwork.md)

    <!-- -->

    - #### getName

          public java.lang.String getName()

      Description copied from interface: [`LogicalBasicNetwork`](LogicalBasicNetwork.md)
      Returns the internal network name, for example, the network name stored in network metadata table. Note that the internal network names for different networks are not guaranteed to be unique across multiple database connections.
      Specified by:
      [`getName`](LogicalBasicNetwork.md) in interface [`LogicalBasicNetwork`](LogicalBasicNetwork.md)

      Returns:
      network name

    <!-- -->

    - #### getNumberOfNodes

          public int getNumberOfNodes()

      Description copied from interface: [`LogicalBasicNetwork`](LogicalBasicNetwork.md)
      Returns the total number of nodes in the network.
      Specified by:
      [`getNumberOfNodes`](LogicalBasicNetwork.md) in interface [`LogicalBasicNetwork`](LogicalBasicNetwork.md)

      Returns:
      number of nodes

    <!-- -->

    - #### getNumberOfLinks

          public int getNumberOfLinks()

      Description copied from interface: [`LogicalBasicNetwork`](LogicalBasicNetwork.md)
      Returns the total number of links in the network.
      Specified by:
      [`getNumberOfLinks`](LogicalBasicNetwork.md) in interface [`LogicalBasicNetwork`](LogicalBasicNetwork.md)

      Returns:
      number of links

    <!-- -->

    - #### getNodes

          public LogicalNetNode[] getNodes()

      Description copied from interface: [`LogicalBasicNetwork`](LogicalBasicNetwork.md)
      Returns all the nodes in the network.
      Specified by:
      [`getNodes`](LogicalBasicNetwork.md) in interface [`LogicalBasicNetwork`](LogicalBasicNetwork.md)

      Returns:
      array of nodes

    <!-- -->

    - #### getLinks

          public LogicalNetLink[] getLinks()

      Description copied from interface: [`LogicalBasicNetwork`](LogicalBasicNetwork.md)
      Returns all the links in the network.
      Specified by:
      [`getLinks`](LogicalBasicNetwork.md) in interface [`LogicalBasicNetwork`](LogicalBasicNetwork.md)

      Returns:
      array of links

    <!-- -->

    - #### getNode

          public LogicalNetNode getNode(long nodeId)

      Description copied from interface: [`LogicalBasicNetwork`](LogicalBasicNetwork.md)
      Returns the logical node object for the specified node id.
      Specified by:
      [`getNode`](LogicalBasicNetwork.md) in interface [`LogicalBasicNetwork`](LogicalBasicNetwork.md)

      Parameters:
      `nodeId` - node id

      Returns:
      logical node object

    <!-- -->

    - #### getLink

          public LogicalNetLink getLink(long linkId)

      Description copied from interface: [`LogicalBasicNetwork`](LogicalBasicNetwork.md)
      Returns the logical link object for the specified link id.
      Specified by:
      [`getLink`](LogicalBasicNetwork.md) in interface [`LogicalBasicNetwork`](LogicalBasicNetwork.md)

      Parameters:
      `linkId` - link id

      Returns:
      logical link object

    <!-- -->

    - #### getNodeIds

          public long[] getNodeIds()

      Description copied from interface: [`LogicalBasicNetwork`](LogicalBasicNetwork.md)
      Returns all the node ids in the network.
      Specified by:
      [`getNodeIds`](LogicalBasicNetwork.md) in interface [`LogicalBasicNetwork`](LogicalBasicNetwork.md)

      Returns:
      array of node ids

    <!-- -->

    - #### getLinkIds

          public long[] getLinkIds()

      Description copied from interface: [`LogicalBasicNetwork`](LogicalBasicNetwork.md)
      Returns all the link ids in the network.
      Specified by:
      [`getLinkIds`](LogicalBasicNetwork.md) in interface [`LogicalBasicNetwork`](LogicalBasicNetwork.md)

      Returns:
      array of link ids

    <!-- -->

    - #### isUserDataLoaded

          public boolean isUserDataLoaded()

      Deprecated. 
      Description copied from interface: [`LogicalBasicNetwork`](LogicalBasicNetwork.md)
      Returns whether the user data are loaded to the network.
      Specified by:
      [`isUserDataLoaded`](LogicalBasicNetwork.md) in interface [`LogicalBasicNetwork`](LogicalBasicNetwork.md)

      Returns:
      true, if the user data are loaded; false, otherwise.

    <!-- -->

    - #### setIsUserDataLoaded

          public void setIsUserDataLoaded(boolean isUserDataLoaded)

      Deprecated. 
      Description copied from interface: [`LogicalBasicNetwork`](LogicalBasicNetwork.md)
      Sets whether the user data is loaded to the network.
      Specified by:
      [`setIsUserDataLoaded`](LogicalBasicNetwork.md) in interface [`LogicalBasicNetwork`](LogicalBasicNetwork.md)

      Parameters:
      `isUserDataLoaded` - true, if the user data are loaded; false, otherwise.

    <!-- -->

    - #### getUserDataCategories

          public int[] getUserDataCategories()

      Description copied from interface: [`LogicalBasicNetwork`](LogicalBasicNetwork.md)
      Returns the user data categories loaded in the network.
      Specified by:

      [`getUserDataCategories`](LogicalBasicNetwork.md) in interface [`LogicalBasicNetwork`](LogicalBasicNetwork.md)

      Returns:

    <!-- -->

    - #### addUserDataCategories

          public void addUserDataCategories(int[] userDataCategories)

    <!-- -->

    - #### addUserDataCategory

          public void addUserDataCategory(int userDataCategory)

      Description copied from interface: [`LogicalBasicNetwork`](LogicalBasicNetwork.md)
      Adds the user data category that have been loaded to the network.
      Specified by:
      [`addUserDataCategory`](LogicalBasicNetwork.md) in interface [`LogicalBasicNetwork`](LogicalBasicNetwork.md)

      Parameters:
      `userDataCategory` - user data category

    <!-- -->

    - #### isUserDataCategoryLoaded

          public boolean isUserDataCategoryLoaded(int category)

      Description copied from interface: [`LogicalBasicNetwork`](LogicalBasicNetwork.md)
      Returns whether the specified user data category is loaded.
      Specified by:

      [`isUserDataCategoryLoaded`](LogicalBasicNetwork.md) in interface [`LogicalBasicNetwork`](LogicalBasicNetwork.md)

      Returns:

    <!-- -->

    - #### removeLink

          public void removeLink(long linkId)

      Description copied from interface: [`LogicalBasicNetwork`](LogicalBasicNetwork.md)
      Removes a link from the network.
      Specified by:
      [`removeLink`](LogicalBasicNetwork.md) in interface [`LogicalBasicNetwork`](LogicalBasicNetwork.md)

      Parameters:
      `linkId` - ID of the link to be removed

    <!-- -->

    - #### getFeatureData

          public FeatureData getFeatureData()

      Returns the feature data associated to this network.
      Specified by:

      [`getFeatureData`](LogicalBasicNetwork.md) in interface [`LogicalBasicNetwork`](LogicalBasicNetwork.md)

      Returns:

    <!-- -->

    - #### setFeatureData

          public void setFeatureData(FeatureData featureData)

      Sets the feature data associated to this network.
      Specified by:
      [`setFeatureData`](LogicalBasicNetwork.md) in interface [`LogicalBasicNetwork`](LogicalBasicNetwork.md)

      Parameters:
      `featureData` -

    <!-- -->

    - #### addFeatureLayer

          public void addFeatureLayer(int featureLayerId,
                                      FeatureLayer featureLayer)

      Description copied from interface: [`LogicalBasicNetwork`](LogicalBasicNetwork.md)
      Adds the feature layer.
      Specified by:
      [`addFeatureLayer`](LogicalBasicNetwork.md) in interface [`LogicalBasicNetwork`](LogicalBasicNetwork.md)

    <!-- -->

    - #### isFeatureLayerLoaded

          public boolean isFeatureLayerLoaded(int featureLayerId)

      Description copied from interface: [`LogicalBasicNetwork`](LogicalBasicNetwork.md)
      Returns whether the specified user data category is loaded.
      Specified by:

      [`isFeatureLayerLoaded`](LogicalBasicNetwork.md) in interface [`LogicalBasicNetwork`](LogicalBasicNetwork.md)

      Returns:

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

- [Prev Class](LogicalPartition.md)
- [Next Class](LogicalPath.md)

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
