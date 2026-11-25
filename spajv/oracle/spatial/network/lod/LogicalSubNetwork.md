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

- [Prev Class](LogicalPath.md)
- [Next Class](LogicalSubPath.md)

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

## Interface LogicalSubNetwork

- All Superinterfaces:
  java.lang.Cloneable, [LogicalBasicNetwork](LogicalBasicNetwork.md)

  <!-- -->

  All Known Subinterfaces:
  [LogicalPartition](LogicalPartition.md), [SpatialPartition](SpatialPartition.md), [SpatialSubNetwork](SpatialSubNetwork.md)

  <!-- -->

  All Known Implementing Classes:
  [LogicalPartitionImpl](LogicalPartitionImpl.md)

  ------------------------------------------------------------------------



      public interface LogicalSubNetwork
      extends LogicalBasicNetwork

  A LogicalSubNetwork is a LogicalNetwork that connects to external nodes.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                            |
    |-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `addNode``(`[`LogicalNetNode`](LogicalNetNode.md)` node, boolean isInternal)`<br>Adds a logical node to the sub-network.                          |
    | `long[]`          | `getBoundaryLinkIds``()`<br>Returns all the boundary link IDs in the sub-network.                                                                 |
    | `long[]`          | `getExternalNodeIds``()`<br>Returns all the external node IDs in the sub-network.                                                                 |
    | `long[]`          | `getIncomingLinkIds``()`<br>Returns all the incoming link IDs in the sub-network.                                                                 |
    | `long[]`          | `getInternalBoundaryNodeIds``()`<br>Returns all the internal node IDs in the sub-network without a link to any external nodes.                    |
    | `long[]`          | `getInternalLinkIds``()`<br>Returns all the internal link IDs in the sub-network.                                                                 |
    | `long[]`          | `getInternalNodeIds``()`<br>Returns all the internal node IDs in the sub-network.                                                                 |
    | `long[]`          | `getInternalNonBoundaryNodeIds``()`<br>Returns all the internal node IDs in the sub-network without a link to any external nodes.                 |
    | `int`             | `getNumberOfBoundaryLinks``()`<br>Returns the number of boundary links in the sub-network, which includes both incoming links and outgoing links. |
    | `int`             | `getNumberOfExternalNodes``()`<br>Returns the number of external nodes in the sub-network.                                                        |
    | `int`             | `getNumberOfIncomingLinks``()`<br>Returns the number of incoming links to the sub-network.                                                        |
    | `int`             | `getNumberOfInternalLinks``()`<br>Returns the number of internal links in the sub-network.                                                        |
    | `int`             | `getNumberOfInternalNodes``()`<br>Returns the number of internal nodes in the sub-network.                                                        |
    | `int`             | `getNumberOfOutgoingLinks``()`<br>Returns the number of outgoing links from the sub-network.                                                      |
    | `long[]`          | `getOutgoingLinkIds``()`<br>Returns all the outgoing link IDs in the sub-network.                                                                 |
    | `boolean`         | `isIncomingLink``(long linkId)`<br>Checks whether the input link is an incoming link or not.                                                      |
    | `boolean`         | `isInternalLink``(long linkId)`<br>Checks whether the input link is an internal link or not.                                                      |
    | `boolean`         | `isInternalNode``(long nodeId)`<br>Checks whether the input node is an internal node or not.                                                      |
    | `boolean`         | `isOutgoingLink``(long linkId)`<br>Checks whether the input link is an outgoing link or not.                                                      |

    - ### Methods inherited from interface oracle.spatial.network.lod.[LogicalBasicNetwork](LogicalBasicNetwork.md)

      [`addFeatureLayer`](LogicalBasicNetwork.md)`, `[`addLink`](LogicalBasicNetwork.md)`, `[`addNode`](LogicalBasicNetwork.md)`, `[`addUserDataCategory`](LogicalBasicNetwork.md)`, `[`clone`](LogicalBasicNetwork.md)`, `[`getFeatureData`](LogicalBasicNetwork.md)`, `[`getLink`](LogicalBasicNetwork.md)`, `[`getLinkIds`](LogicalBasicNetwork.md)`, `[`getLinkLevel`](LogicalBasicNetwork.md)`, `[`getLinks`](LogicalBasicNetwork.md)`, `[`getName`](LogicalBasicNetwork.md)`, `[`getNode`](LogicalBasicNetwork.md)`, `[`getNodeIds`](LogicalBasicNetwork.md)`, `[`getNodes`](LogicalBasicNetwork.md)`, `[`getNumberOfLinks`](LogicalBasicNetwork.md)`, `[`getNumberOfNodes`](LogicalBasicNetwork.md)`, `[`getUserDataCategories`](LogicalBasicNetwork.md)`, `[`isFeatureLayerLoaded`](LogicalBasicNetwork.md)`, `[`isUserDataCategoryLoaded`](LogicalBasicNetwork.md)`, `[`isUserDataLoaded`](LogicalBasicNetwork.md)`, `[`removeLink`](LogicalBasicNetwork.md)`, `[`removeNode`](LogicalBasicNetwork.md)`, `[`setFeatureData`](LogicalBasicNetwork.md)`, `[`setIsUserDataLoaded`](LogicalBasicNetwork.md)

<!-- -->

- - ### Method Detail

    - #### getNumberOfInternalNodes

          int getNumberOfInternalNodes()

      Returns the number of internal nodes in the sub-network.
      Returns:
      number of internal nodes

    <!-- -->

    - #### getNumberOfExternalNodes

          int getNumberOfExternalNodes()

      Returns the number of external nodes in the sub-network.
      Returns:
      number of external nodes

    <!-- -->

    - #### getNumberOfInternalLinks

          int getNumberOfInternalLinks()

      Returns the number of internal links in the sub-network.
      Returns:
      number of internal links

    <!-- -->

    - #### getNumberOfBoundaryLinks

          int getNumberOfBoundaryLinks()

      Returns the number of boundary links in the sub-network, which includes both incoming links and outgoing links.
      Returns:
      number of boundary links

    <!-- -->

    - #### getNumberOfIncomingLinks

          int getNumberOfIncomingLinks()

      Returns the number of incoming links to the sub-network.
      Returns:
      number of incoming links

    <!-- -->

    - #### getNumberOfOutgoingLinks

          int getNumberOfOutgoingLinks()

      Returns the number of outgoing links from the sub-network.
      Returns:
      number of outgoing links

    <!-- -->

    - #### getInternalNodeIds

          long[] getInternalNodeIds()

      Returns all the internal node IDs in the sub-network.
      Returns:
      array of internal node IDs

    <!-- -->

    - #### getInternalBoundaryNodeIds

          long[] getInternalBoundaryNodeIds()

      Returns all the internal node IDs in the sub-network without a link to any external nodes.
      Returns:
      array of internal boundary node IDs

    <!-- -->

    - #### getInternalNonBoundaryNodeIds

          long[] getInternalNonBoundaryNodeIds()

      Returns all the internal node IDs in the sub-network without a link to any external nodes.
      Returns:
      array of internal non-boundary node IDs

    <!-- -->

    - #### getExternalNodeIds

          long[] getExternalNodeIds()

      Returns all the external node IDs in the sub-network.
      Returns:
      array of external node IDs

    <!-- -->

    - #### isInternalNode

          boolean isInternalNode(long nodeId)

      Checks whether the input node is an internal node or not.
      Parameters:
      `nodeId` - node id

      Returns:
      true, if the input node is an internal node; false, otherwise.

    <!-- -->

    - #### isInternalLink

          boolean isInternalLink(long linkId)

      Checks whether the input link is an internal link or not.
      Parameters:
      `linkId` - link ID

      Returns:
      true, if the input link is an internal link; false, otherwise.

    <!-- -->

    - #### isIncomingLink

          boolean isIncomingLink(long linkId)

      Checks whether the input link is an incoming link or not.
      Parameters:
      `linkId` - link ID

      Returns:
      true, if the input link is an incoming link; false, otherwise.

    <!-- -->

    - #### isOutgoingLink

          boolean isOutgoingLink(long linkId)

      Checks whether the input link is an outgoing link or not.
      Parameters:
      `linkId` - link ID

      Returns:
      true, if the input link is an outgoing link; false, otherwise.

    <!-- -->

    - #### getInternalLinkIds

          long[] getInternalLinkIds()

      Returns all the internal link IDs in the sub-network.
      Returns:
      array of internal link IDs.

    <!-- -->

    - #### getBoundaryLinkIds

          long[] getBoundaryLinkIds()

      Returns all the boundary link IDs in the sub-network.
      Returns:
      array of boundary link IDs.

    <!-- -->

    - #### getIncomingLinkIds

          long[] getIncomingLinkIds()

      Returns all the incoming link IDs in the sub-network.
      Returns:
      array of incoming link IDs.

    <!-- -->

    - #### getOutgoingLinkIds

          long[] getOutgoingLinkIds()

      Returns all the outgoing link IDs in the sub-network.
      Returns:
      array of outgoing link IDs.

    <!-- -->

    - #### addNode

          void addNode(LogicalNetNode node,
                       boolean isInternal)

      Adds a logical node to the sub-network.
      Parameters:
      `node` - logical node

      `isInternal` - set to true, if the node is an internal node; false, otherwise.

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

- [Prev Class](LogicalPath.md)
- [Next Class](LogicalSubPath.md)

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
