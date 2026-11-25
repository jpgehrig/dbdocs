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

- [Prev Class](LODUserDataIOSDO.md)
- [Next Class](LogicalHeavyPath.md)

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

## Interface LogicalBasicNetwork

- All Superinterfaces:
  java.lang.Cloneable

  <!-- -->

  All Known Subinterfaces:
  [LogicalPartition](LogicalPartition.md), [LogicalSubNetwork](LogicalSubNetwork.md), [SpatialBasicNetwork](SpatialBasicNetwork.md), [SpatialPartition](SpatialPartition.md), [SpatialSubNetwork](SpatialSubNetwork.md)

  <!-- -->

  All Known Implementing Classes:
  [LogicalPartitionImpl](LogicalPartitionImpl.md)

  ------------------------------------------------------------------------



      public interface LogicalBasicNetwork
      extends java.lang.Cloneable

  This interface defines methods supported by a logical network.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                         | Method and Description                                                                                                 |
    |-------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
    | `void`                                    | `addFeatureLayer``(int featureLayerId, `[`FeatureLayer`](FeatureLayer.md)` featureLayer)`<br>Adds the feature layer.   |
    | `void`                                    | `addLink``(`[`LogicalNetLink`](LogicalNetLink.md)` link)`<br>Adds a logical link to the network.                       |
    | `void`                                    | `addNode``(`[`LogicalNetNode`](LogicalNetNode.md)` node)`<br>Adds a logical node to the network.                       |
    | `void`                                    | `addUserDataCategory``(int userDataCategory)`<br>Adds the user data category that have been loaded to the network.     |
    | `java.lang.Object`                        | `clone``()`<br>Supports cloneable                                                                                      |
    | [`FeatureData`](FeatureData.md)           | `getFeatureData``()`<br>Returns the feature data associated to this network.                                           |
    | [`LogicalNetLink`](LogicalNetLink.md)     | `getLink``(long linkId)`<br>Returns the logical link object for the specified link id.                                 |
    | `long[]`                                  | `getLinkIds``()`<br>Returns all the link ids in the network.                                                           |
    | `int`                                     | `getLinkLevel``()`<br>Returns the link level of the network.                                                           |
    | [`LogicalNetLink`](LogicalNetLink.md)`[]` | `getLinks``()`<br>Returns all the links in the network.                                                                |
    | `java.lang.String`                        | `getName``()`<br>Returns the internal network name, for example, the network name stored in network metadata table.    |
    | [`LogicalNetNode`](LogicalNetNode.md)     | `getNode``(long nodeId)`<br>Returns the logical node object for the specified node id.                                 |
    | `long[]`                                  | `getNodeIds``()`<br>Returns all the node ids in the network.                                                           |
    | [`LogicalNetNode`](LogicalNetNode.md)`[]` | `getNodes``()`<br>Returns all the nodes in the network.                                                                |
    | `int`                                     | `getNumberOfLinks``()`<br>Returns the total number of links in the network.                                            |
    | `int`                                     | `getNumberOfNodes``()`<br>Returns the total number of nodes in the network.                                            |
    | `int[]`                                   | `getUserDataCategories``()`<br>Returns the user data categories loaded in the network.                                 |
    | `boolean`                                 | `isFeatureLayerLoaded``(int featureLayerId)`<br>Returns whether the specified user data category is loaded.            |
    | `boolean`                                 | `isUserDataCategoryLoaded``(int category)`<br>Returns whether the specified user data category is loaded.              |
    | `boolean`                                 | `isUserDataLoaded``()`<br>Deprecated. <br>use getUserDataCategories                                                    |
    | `void`                                    | `removeLink``(long linkId)`<br>Removes a link from the network.                                                        |
    | `void`                                    | `removeNode``(long nodeId)`<br>Removes a node from the network.                                                        |
    | `void`                                    | `setFeatureData``(`[`FeatureData`](FeatureData.md)` featureData)`<br>Sets the feature data associated to this network. |
    | `void`                                    | `setIsUserDataLoaded``(boolean isUserDataLoaded)`<br>Deprecated. <br>use addUserDataCategory                           |

<!-- -->

- - ### Method Detail

    - #### getName

          java.lang.String getName()

      Returns the internal network name, for example, the network name stored in network metadata table. Note that the internal network names for different networks are not guaranteed to be unique across multiple database connections.
      Returns:
      network name

    <!-- -->

    - #### getLinkLevel

          int getLinkLevel()

      Returns the link level of the network.
      Returns:

    <!-- -->

    - #### addLink

          void addLink(LogicalNetLink link)

      Adds a logical link to the network.
      Parameters:
      `link` - logical link

    <!-- -->

    - #### addNode

          void addNode(LogicalNetNode node)

      Adds a logical node to the network.
      Parameters:
      `node` -

    <!-- -->

    - #### getNumberOfNodes

          int getNumberOfNodes()

      Returns the total number of nodes in the network.
      Returns:
      number of nodes

    <!-- -->

    - #### getNumberOfLinks

          int getNumberOfLinks()

      Returns the total number of links in the network.
      Returns:
      number of links

    <!-- -->

    - #### getNodes

          LogicalNetNode[] getNodes()

      Returns all the nodes in the network.
      Returns:
      array of nodes

    <!-- -->

    - #### getLinks

          LogicalNetLink[] getLinks()

      Returns all the links in the network.
      Returns:
      array of links

    <!-- -->

    - #### getNode

          LogicalNetNode getNode(long nodeId)

      Returns the logical node object for the specified node id.
      Parameters:
      `nodeId` - node id

      Returns:
      logical node object

    <!-- -->

    - #### getLink

          LogicalNetLink getLink(long linkId)

      Returns the logical link object for the specified link id.
      Parameters:
      `linkId` - link id

      Returns:
      logical link object

    <!-- -->

    - #### getNodeIds

          long[] getNodeIds()

      Returns all the node ids in the network.
      Returns:
      array of node ids

    <!-- -->

    - #### getLinkIds

          long[] getLinkIds()

      Returns all the link ids in the network.
      Returns:
      array of link ids

    <!-- -->

    - #### isUserDataLoaded

          boolean isUserDataLoaded()

      Deprecated. use getUserDataCategories
      Returns whether the user data are loaded to the network.
      Returns:
      true, if the user data are loaded; false, otherwise.

    <!-- -->

    - #### setIsUserDataLoaded

          void setIsUserDataLoaded(boolean isUserDataLoaded)

      Deprecated. use addUserDataCategory
      Sets whether the user data is loaded to the network.
      Parameters:
      `isUserDataLoaded` - true, if the user data are loaded; false, otherwise.

    <!-- -->

    - #### getUserDataCategories

          int[] getUserDataCategories()

      Returns the user data categories loaded in the network.
      Returns:

    <!-- -->

    - #### addUserDataCategory

          void addUserDataCategory(int userDataCategory)

      Adds the user data category that have been loaded to the network.
      Parameters:
      `userDataCategory` - user data category

    <!-- -->

    - #### isUserDataCategoryLoaded

          boolean isUserDataCategoryLoaded(int category)

      Returns whether the specified user data category is loaded.
      Parameters:

      `category` -

      Returns:

    <!-- -->

    - #### removeNode

          void removeNode(long nodeId)

      Removes a node from the network.
      Parameters:
      `nodeId` - ID of the node to be removed

    <!-- -->

    - #### removeLink

          void removeLink(long linkId)

      Removes a link from the network.
      Parameters:
      `linkId` - ID of the link to be removed

    <!-- -->

    - #### getFeatureData

          FeatureData getFeatureData()

      Returns the feature data associated to this network.
      Returns:

    <!-- -->

    - #### setFeatureData

          void setFeatureData(FeatureData featureData)

      Sets the feature data associated to this network.
      Parameters:
      `featureData` -

    <!-- -->

    - #### addFeatureLayer

          void addFeatureLayer(int featureLayerId,
                               FeatureLayer featureLayer)

      Adds the feature layer.
      Parameters:
      `featureLayer` -

    <!-- -->

    - #### isFeatureLayerLoaded

          boolean isFeatureLayerLoaded(int featureLayerId)

      Returns whether the specified user data category is loaded.
      Parameters:

      `featureLayerId` -

      Returns:

    <!-- -->

    - #### clone

          java.lang.Object clone()
                          throws java.lang.CloneNotSupportedException

      Supports cloneable
      Returns:
      cloned object

      Throws:
      `java.lang.CloneNotSupportedException`

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

- [Prev Class](LODUserDataIOSDO.md)
- [Next Class](LogicalHeavyPath.md)

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
