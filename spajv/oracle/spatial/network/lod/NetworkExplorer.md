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

- [Prev Class](NetworkBuffer.LinkIntervals.md)
- [Next Class](NetworkIO.md)

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

## Class NetworkExplorer

- java.lang.Object

- - oracle.spatial.network.lod.NetworkExplorer

<!-- -->

-

  ------------------------------------------------------------------------



      public class NetworkExplorer
      extends java.lang.Object

  This class provides methods to navigate a network. The network may contain dynamic network update information superimposed on the static network information.
  The following summarizes the basic steps in network navigation starting from a node:
  1. From the input node ID, get the network node object (LogicalNetNode) by calling
             networkExplorer.getNetNode(nodeId)


  The returned LogicalNetNode object contains reference to its adjacent network links, which in turn contains references to the next nodes, and so on.
  2. From the returned LogicalNetNode object, get the next node IDs or adjacent network link objects (LogicalNetLink), e.g.,
              netNode.getNextNodeIds(...), or
              netNode.getOutLinks(...)


  3\. From the returned LogicalNetLink objects, get the adjacent network node objects (LogicalNetNode), e.g.,
             netLink.getStartNode(), or
             netLink.getEndNode().


  4\. At this point, you may be tempted to navigate further directly from these adjacent nodes. However, the network node objects returned from step 3 might be external node objects in the containing partition, thus, may not have all the references to their adjacent links. If you plan to navigate further from these adjacent nodes, you should always call the following method to ensure that you have the corresponding internal node object that contains all the references to its adjacent links.
             networkExplorer.getNetNode(adjacentNode.getId())


  5\. From the adjacent network node objects returned from step 4, you can continue navigating the network by repeating step 2 and 3.
  6. Since the network node and link objects contain strong references to their adjacent objects, it is important to release any strong references to these objects as soon as you have finished investigating the corresponding part of the network, so that java VM can effectively garbage collect the network of objects that are interconnected to each other. If you have to keep some information from a network object for later, you should manage that information yourself without referencing the network object, or create a standalone object from the network object, and reference the standalone object instead. A standalone object does not contain any reference to other nodes or links.
  To create a standalone object from a network object use:
             netLink.toStandAloneLink(), or
             netNode.toStandAloneNode().


  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description |
    |-------------------|-----------------------|
    | `static int`      | `DIRECTION_BACKWARD`  |
    | `static int`      | `DIRECTION_BOTH`      |
    | `static int`      | `DIRECTION_FORWARD`   |
    | `static long`     | `INVALID_LINK_ID`     |
    | `static long`     | `INVALID_NODE_ID`     |
    | `static int`      | `MIN_LINK_LEVEL`      |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                           |
    |-----------------------------------------------------------------------------------------------------------------------|
    | `NetworkExplorer``(`[`NetworkIO`](NetworkIO.md)` reader)`<br>Constructs a NetworkExplorer with empty network updates. |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                                            | Method and Description                                                                                                                                                                                                                             |
    |------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`LeveledNetworkCache`](LeveledNetworkCache.md)                              | `getDynamicNetworkCache``()`<br>Returns the dynamic network cache.                                                                                                                                                                                 |
    | [`HeavyPointOnNet`](HeavyPointOnNet.md)`[]`                                  | `getHeavyPointsOnNet``(`[`PointOnNet`](PointOnNet.md)`[] points, int[] userDataCategories, int[] featureLayers)`                                                                                                                                   |
    | [`LogicalLink`](LogicalLink.md)                                              | `getLink``(long linkId, int[] userDataCategories)`<br>Returns the standalone logical link.                                                                                                                                                         |
    | [`LogicalNetLink`](LogicalNetLink.md)                                        | `getNetLink``(long linkId, int linkLevel, int partitionId, int[] userDataCategories, int[] featureLayers)`<br>Returns the network link from the specified partition.                                                                               |
    | [`LogicalNetNode`](LogicalNetNode.md)                                        | `getNetNode``(long nodeId, int linkLevel, int[] userDataCategories, int[] featureLayers)`<br>Returns the network node from the containing partition.                                                                                               |
    | [`LogicalNetNode`](LogicalNetNode.md)                                        | `getNetNodeForDummyExternalNode``(int partitionId, long adjacentNodeId, long incidentLinkId, int linkLevel, int[] userDataCategories, int[] featureLayers)`<br>Returns the network node from the containing partition for the dummy external Node. |
    | [`NetworkIO`](NetworkIO.md)                                                  | `getNetworkIO``()`<br>Returns the network IO.                                                                                                                                                                                                      |
    | `java.util.HashMap<java.lang.Integer,`[`NetworkUpdate`](NetworkUpdate.md)`>` | `getNetworkUpdates``()`<br>Returns the network updates for each link level.                                                                                                                                                                        |
    | [`LogicalNode`](LogicalNode.md)                                              | `getNode``(long nodeId, int[] userDataCategories)`<br>Returns the standalone node.                                                                                                                                                                 |
    | `int`                                                                        | `getNodePartitionId``(long nodeId, int linkLevel)`<br>Returns the partition ID for the specified node.                                                                                                                                             |
    | [`LogicalPartition`](LogicalPartition.md)                                    | `getPartition``(int partitionId, int linkLevel, int[] userDataCategories, int[] featureLayers)`<br>Returns the partition.                                                                                                                          |
    | [`NetworkIO`](NetworkIO.md)                                                  | `getReader``()`<br>Deprecated. <br>use getNetworkIO()                                                                                                                                                                                              |
    | `static int`                                                                 | `getReverseDirection``(int direction)`                                                                                                                                                                                                             |
    | `void`                                                                       | `setNetworkUpdate``(int linkLevel, `[`NetworkUpdate`](NetworkUpdate.md)` networkUpdate)`<br>Sets the network update object and initialize the dynamic cache.                                                                                       |
    | `void`                                                                       | `setNetworkUpdates``(java.util.HashMap<java.lang.Integer,`[`NetworkUpdate`](NetworkUpdate.md)`> networkUpdates)`<br>Sets the network update objects and re-initialize the dynamic cache.                                                           |
    | `void`                                                                       | `setReader``(`[`NetworkIO`](NetworkIO.md)` reader)`<br>Sets the network reader and the maximum link level.                                                                                                                                         |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### DIRECTION_BOTH

          public static final int DIRECTION_BOTH

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### DIRECTION_FORWARD

          public static final int DIRECTION_FORWARD

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### DIRECTION_BACKWARD

          public static final int DIRECTION_BACKWARD

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### MIN_LINK_LEVEL

          public static final int MIN_LINK_LEVEL

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### INVALID_LINK_ID

          public static final long INVALID_LINK_ID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### INVALID_NODE_ID

          public static final long INVALID_NODE_ID

      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### NetworkExplorer

          public NetworkExplorer(NetworkIO reader)
                          throws LODNetworkException

      Constructs a NetworkExplorer with empty network updates.
      Parameters:
      `reader` -

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

  <!-- -->

  - ### Method Detail

    - #### getReverseDirection

          public static int getReverseDirection(int direction)

    <!-- -->

    - #### setNetworkUpdates

          public void setNetworkUpdates(java.util.HashMap<java.lang.Integer,NetworkUpdate> networkUpdates)

      Sets the network update objects and re-initialize the dynamic cache. These network update objects will be super imposed to the static network information while the user navigates the network during network analysis.
      Parameters:
      `networkUpdates` - network update objects for different link levels

    <!-- -->

    - #### setNetworkUpdate

          public void setNetworkUpdate(int linkLevel,
                                       NetworkUpdate networkUpdate)

      Sets the network update object and initialize the dynamic cache. These network update objects will be super imposed to the static network information while navigating the network during network analysis.
      Parameters:
      `networkUpdate` - network update object

    <!-- -->

    - #### getHeavyPointsOnNet

          public HeavyPointOnNet[] getHeavyPointsOnNet(PointOnNet[] points,
                                                       int[] userDataCategories,
                                                       int[] featureLayers)
                                                throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### getLink

          public LogicalLink getLink(long linkId,
                                     int[] userDataCategories)
                              throws LODNetworkException

      Returns the standalone logical link. This method first searches for the link in the dynamic network update object. If not found, it reads the link through the NetworkIO object.
      Parameters:
      `linkId` - link ID

      `userDataCategories` - If set to true, this method will return a SpatialLink.

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### getNode

          public LogicalNode getNode(long nodeId,
                                     int[] userDataCategories)
                              throws LODNetworkException

      Returns the standalone node. This method first searches for the node in the dynamic network update object. If not found, it reads the node through the NetworkIO object.
      Parameters:
      `nodeId` - node ID

      `userDataCategories` - If set to true, this method will return a SpatialNode.

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### getPartition

          public LogicalPartition getPartition(int partitionId,
                                               int linkLevel,
                                               int[] userDataCategories,
                                               int[] featureLayers)
                                        throws LODNetworkException

      Returns the partition. This method first searches for the partition in the dynamic network update object. If not found, it reads the partition through the NetworkIO object.
      Parameters:
      `partitionId` - partition ID

      `linkLevel` - link level

      `userDataCategories` -

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### getNodePartitionId

          public int getNodePartitionId(long nodeId,
                                        int linkLevel)
                                 throws LODNetworkException

      Returns the partition ID for the specified node.
      Parameters:
      `nodeId` - node ID

      `linkLevel` - link level

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### getNetNode

          public LogicalNetNode getNetNode(long nodeId,
                                           int linkLevel,
                                           int[] userDataCategories,
                                           int[] featureLayers)
                                    throws LODNetworkException

      Returns the network node from the containing partition. The returned network node contains references to all its adjacent links.
      Parameters:
      `nodeId` - node ID

      `linkLevel` - link level

      `userDataCategories` -

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### getNetNodeForDummyExternalNode

          public LogicalNetNode getNetNodeForDummyExternalNode(int partitionId,
                                                               long adjacentNodeId,
                                                               long incidentLinkId,
                                                               int linkLevel,
                                                               int[] userDataCategories,
                                                               int[] featureLayers)
                                                        throws LODNetworkException

      Returns the network node from the containing partition for the dummy external Node. The only reliable information in a dummy external node is the ID of the containing partition. The returned network node contains references to all its adjacent links.
      Parameters:
      `partitionId` - ID of the partition that owns the external node

      `adjacentNodeId` - ID of the node on the other side of the incident link

      `incidentLinkId` - ID of the link that is incident to the external node

      `linkLevel` - link level of the containing partition

      `userDataCategories` -

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### getNetLink

          public LogicalNetLink getNetLink(long linkId,
                                           int linkLevel,
                                           int partitionId,
                                           int[] userDataCategories,
                                           int[] featureLayers)
                                    throws LODNetworkException

      Returns the network link from the specified partition.
      Parameters:
      `linkId` - link ID

      `linkLevel` - link level

      `partitionId` - ID of the partition that owns the link

      `userDataCategories` -

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### setReader

          public void setReader(NetworkIO reader)
                         throws LODNetworkException

      Sets the network reader and the maximum link level.
      Parameters:
      `reader` - network reader

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### getReader

          public NetworkIO getReader()

      Deprecated. use getNetworkIO()
      Returns the network reader.
      Returns:

    <!-- -->

    - #### getNetworkIO

          public NetworkIO getNetworkIO()

      Returns the network IO.
      Returns:

    <!-- -->

    - #### getNetworkUpdates

          public java.util.HashMap<java.lang.Integer,NetworkUpdate> getNetworkUpdates()

      Returns the network updates for each link level.
      Returns:

    <!-- -->

    - #### getDynamicNetworkCache

          public LeveledNetworkCache getDynamicNetworkCache()

      Returns the dynamic network cache.
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

- [Prev Class](NetworkBuffer.LinkIntervals.md)
- [Next Class](NetworkIO.md)

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
