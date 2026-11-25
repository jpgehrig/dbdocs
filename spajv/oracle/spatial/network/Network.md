Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NDMTimer.md)
- [Next Class](NetworkConstraint.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

oracle.spatial.network

## Interface Network

- All Superinterfaces:
  java.lang.Cloneable, java.io.Serializable

  ------------------------------------------------------------------------



      public interface Network
      extends java.lang.Cloneable, java.io.Serializable

  This interface defines a network.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description |
    |-------------------|-----------------------|
    | `static int`      | `BIDIRECTED_LINK`     |
    | `static int`      | `DIRECTED_LINK`       |
    | `static int`      | `LOGICAL_NETWORK`     |
    | `static int`      | `LRS_GEOMETRY_TYPE`   |
    | `static int`      | `SDO_GEOMETRY_TYPE`   |
    | `static int`      | `SPATIAL_NETWORK`     |
    | `static int`      | `TOPO_GEOMETRY_TYPE`  |
    | `static int`      | `UNDIRECTED_LINK`     |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                       | Method and Description                                                                                                                                                                                                                                                            |
    |-----------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                  | `addLink``(`[`Link`](Link.md)` l)`<br>Adds a link to the network.                                                                                                                                                                                                                 |
    | `void`                                  | `addLinkData``(java.lang.String dataName, java.lang.String dataType, int dataLength)`<br>Adds a link user data entry A NetworkDataException is thrown if the data already exists                                                                                                  |
    | `void`                                  | `addLinks``(`[`Link`](Link.md)`[] linkArray)`<br>Adds an array of links to the network.                                                                                                                                                                                           |
    | `void`                                  | `addNetwork``(Network n)`<br>Adds a network to the current network.                                                                                                                                                                                                               |
    | [`Node`](Node.md)                       | `addNode``(`[`Link`](Link.md)` l, double distanceRatio, boolean isTemporary)`<br>Adds a node on a link to the network.                                                                                                                                                            |
    | `void`                                  | `addNode``(`[`Node`](Node.md)` n)`<br>Adds a node to the network.                                                                                                                                                                                                                 |
    | `void`                                  | `addNodeData``(java.lang.String dataName, java.lang.String dataType, int dataLength)`<br>Adds a node user data entry A NetworkDataException is thrown if the data already exists                                                                                                  |
    | `void`                                  | `addNodes``(`[`Node`](Node.md)`[] nodeArray)`<br>Adds an array of nodes to the network.                                                                                                                                                                                           |
    | `void`                                  | `addPath``(`[`Path`](Path.md)` path)`<br>Adds a path to the network.                                                                                                                                                                                                              |
    | `void`                                  | `addPathData``(java.lang.String dataName, java.lang.String dataType, int dataLength)`<br>Adds a path user data entry A NetworkDataException is thrown if the data already exists                                                                                                  |
    | `void`                                  | `addPaths``(`[`Path`](Path.md)`[] pathArray)`<br>Adds an array of paths to the network.                                                                                                                                                                                           |
    | `void`                                  | `addSubPath``(`[`SubPath`](SubPath.md)` subPath)`<br>Adds a subpath to the network.                                                                                                                                                                                               |
    | `void`                                  | `addSubPathData``(java.lang.String dataName, java.lang.String dataType, int dataLength)`<br>Adds a subpath user data entry A NetworkDataException is thrown if the data already exists                                                                                            |
    | `void`                                  | `addSubPaths``(`[`SubPath`](SubPath.md)`[] subPathArray)`<br>Adds an array of subpaths to the network.                                                                                                                                                                            |
    | [`Node`](Node.md)                       | `addTemporaryNode``(`[`Link`](Link.md)` l, double distanceRatio)`<br>Adds a Temporary node (non-persistent) on a link.                                                                                                                                                            |
    | `void`                                  | `clear``()`<br>Clears all network structure.                                                                                                                                                                                                                                      |
    | `void`                                  | `clearTemporaryCache``()`<br>Clears the temporatory cache                                                                                                                                                                                                                         |
    | `java.lang.Object`                      | `clone``()`<br>Clones the network.                                                                                                                                                                                                                                                |
    | `boolean`                               | `containsLink``(int linkID)`<br>Checks if the network contains the given link                                                                                                                                                                                                     |
    | `boolean`                               | `containsLink``(java.lang.String linkID)`<br>Checks if the network contains the given link                                                                                                                                                                                        |
    | `boolean`                               | `containsNode``(int nodeID)`<br>Checks if the network contains the given node                                                                                                                                                                                                     |
    | `boolean`                               | `containsNode``(java.lang.String nodeID)`<br>Checks if the network contains the given node                                                                                                                                                                                        |
    | `boolean`                               | `containsPath``(int pathID)`<br>Checks if the network contains the given path                                                                                                                                                                                                     |
    | `boolean`                               | `containsPath``(java.lang.String pathID)`<br>Checks if the network contains the given path                                                                                                                                                                                        |
    | `boolean`                               | `containsSubPath``(int subPathID)`<br>Checks if the network contains the given subpath                                                                                                                                                                                            |
    | `boolean`                               | `containsSubPath``(java.lang.String subPathID)`<br>Checks if the network contains the given subpath                                                                                                                                                                               |
    | `boolean`                               | `containsUserData``()`<br>Checks if the network has user data defined in user_network_user_data                                                                                                                                                                                   |
    | `void`                                  | `deleteLink``(int linkID)`<br>Deletes a link by ID.                                                                                                                                                                                                                               |
    | `void`                                  | `deleteLink``(`[`Link`](Link.md)` l)`<br>Deletes a link.                                                                                                                                                                                                                          |
    | `void`                                  | `deleteLink``(java.lang.String linkID)`<br>Deletes a link by the String ID.                                                                                                                                                                                                       |
    | `void`                                  | `deleteLinkData``(java.lang.String dataName)`<br>Deletes a link user data entry                                                                                                                                                                                                   |
    | `void`                                  | `deleteNetwork``(Network n)`<br>Deletes a sub-network.                                                                                                                                                                                                                            |
    | `void`                                  | `deleteNode``(int nodeID)`<br>Deletes a node by ID.                                                                                                                                                                                                                               |
    | `void`                                  | `deleteNode``(`[`Node`](Node.md)` n)`<br>Deletes a node.                                                                                                                                                                                                                          |
    | `void`                                  | `deleteNode``(java.lang.String nodeID)`<br>Deletes a node by the STring ID.                                                                                                                                                                                                       |
    | `void`                                  | `deleteNodeData``(java.lang.String dataName)`<br>Deletes a node user data entry                                                                                                                                                                                                   |
    | `void`                                  | `deletePath``(int pathID)`<br>Deletes a path by ID.                                                                                                                                                                                                                               |
    | `void`                                  | `deletePath``(`[`Path`](Path.md)` path)`<br>Deletes a path.                                                                                                                                                                                                                       |
    | `void`                                  | `deletePath``(java.lang.String pathID)`<br>Deletes a path by the String ID.                                                                                                                                                                                                       |
    | `void`                                  | `deletePathData``(java.lang.String dataName)`<br>Deletes a path user data entry                                                                                                                                                                                                   |
    | `void`                                  | `deleteSubPath``(int subPathID)`<br>Deletes a subpath by ID.                                                                                                                                                                                                                      |
    | `void`                                  | `deleteSubPath``(java.lang.String subPathID)`<br>Deletes a subpath by the String ID.                                                                                                                                                                                              |
    | `void`                                  | `deleteSubPath``(`[`SubPath`](SubPath.md)` subPath)`<br>Deletes a subpath.                                                                                                                                                                                                        |
    | `void`                                  | `deleteSubPathData``(java.lang.String dataName)`<br>Deletes a subpath user data entry                                                                                                                                                                                             |
    | `void`                                  | `deleteTemporaryElements``()`<br>Deletes all temporary elements (nodes and links).                                                                                                                                                                                                |
    | [`Link`](Link.md)                       | `getLink``(int linkID)`<br>Returns the link by ID.                                                                                                                                                                                                                                |
    | [`Link`](Link.md)                       | `getLink``(int startNodeID, int endNodeID)`<br>Returns the link by the start and the end node IDs                                                                                                                                                                                 |
    | [`Link`](Link.md)                       | `getLink``(java.lang.String linkID)`<br>Returns the link by the STring ID.                                                                                                                                                                                                        |
    | [`Link`](Link.md)`[]`                   | `getLinkArray``()`<br>Returns the links as an array.                                                                                                                                                                                                                              |
    | [`Link`](Link.md)`[]`                   | `getLinkArray``(boolean active)`<br>Returns the links with the specified active flag as an array.                                                                                                                                                                                 |
    | [`Link`](Link.md)`[]`                   | `getLinkArray``(int level)`<br>Returns the links with the specified level as an array.                                                                                                                                                                                            |
    | [`Link`](Link.md)`[]`                   | `getLinkArray``(java.lang.String type)`<br>Returns the links with the specified type as an array.                                                                                                                                                                                 |
    | `java.lang.String`                      | `getLinkDurationColumn``()`<br>Deprecated.                                                                                                                                                                                                                                        |
    | `int[]`                                 | `getLinkHierarchyLevelArray``()`<br>Returns the link hierarchy levels as an array.                                                                                                                                                                                                |
    | `int[]`                                 | `getLinkLevelArray``()`<br>Returns the link levels as an array.                                                                                                                                                                                                                   |
    | `java.lang.String`                      | `getLinkPartitionColumn``()`<br>Deprecated.                                                                                                                                                                                                                                       |
    | `java.util.Iterator`                    | `getLinks``()`<br>Returns the links as an Iterator.                                                                                                                                                                                                                               |
    | `java.util.Iterator`                    | `getLinks``(boolean active)`<br>Returns the links with the specified active flag as an Iterator.                                                                                                                                                                                  |
    | `java.util.Iterator`                    | `getLinks``(int level)`<br>Returns the links with the specified link level as an Iterator.                                                                                                                                                                                        |
    | `java.util.Iterator`                    | `getLinks``(java.lang.String type)`<br>Returns the links with the specified type as an Iterator.                                                                                                                                                                                  |
    | `java.util.Set`                         | `getLinksByPartitionID``(int partitionID)`<br>Returns the links with the specified partition ID as a Set.                                                                                                                                                                         |
    | `java.lang.String`                      | `getLinkTableName``()`<br>Deprecated.                                                                                                                                                                                                                                             |
    | `java.lang.String`                      | `getLRSTableName``()`<br>Deprecated.                                                                                                                                                                                                                                              |
    | `int`                                   | `getMaxLinkID``()`<br>Returns the maximum link ID.                                                                                                                                                                                                                                |
    | `int`                                   | `getMaxNodeID``()`<br>Returns the maximun node ID.                                                                                                                                                                                                                                |
    | `int`                                   | `getMaxPathID``()`<br>Returns the maximum path ID.                                                                                                                                                                                                                                |
    | `int`                                   | `getMaxSubPathID``()`<br>Returns the maximum subpath ID.                                                                                                                                                                                                                          |
    | [`MBR`](MBR.md)                         | `getMBR``()`<br>Returns the network MBR.                                                                                                                                                                                                                                          |
    | [`NetworkMetadata`](NetworkMetadata.md) | `getMetadata``()`<br>Returns the network metadata.                                                                                                                                                                                                                                |
    | `java.lang.String`                      | `getMetadataViewName``()`<br>Returns the network metadata view name (user_sdo_network_metadata).                                                                                                                                                                                  |
    | `java.lang.String`                      | `getName``()`<br>Returns the network name.                                                                                                                                                                                                                                        |
    | `oracle.spatial.network.NetworkCache`   | `getNetworkCache``()`<br>Returns the network cache for editing purpose.                                                                                                                                                                                                           |
    | `int`                                   | `getNetworkID``()`<br>Returns the network ID.                                                                                                                                                                                                                                     |
    | [`Node`](Node.md)                       | `getNode``(int nodeID)`<br>Returns the node by ID.                                                                                                                                                                                                                                |
    | [`Node`](Node.md)                       | `getNode``(java.lang.String nodeID)`<br>Returns the node by the String ID.                                                                                                                                                                                                        |
    | [`Node`](Node.md)`[]`                   | `getNodeArray``()`<br>Returns the nodes as an array.                                                                                                                                                                                                                              |
    | [`Node`](Node.md)`[]`                   | `getNodeArray``(boolean active)`<br>Returns the nodes with the specified acvive flag as an array.                                                                                                                                                                                 |
    | [`Node`](Node.md)`[]`                   | `getNodeArray``(int hierarchyLevel)`<br>Returns the nodes with the specified hierarchy level as an array.                                                                                                                                                                         |
    | [`Node`](Node.md)`[]`                   | `getNodeArray``(java.lang.String type)`<br>Returns the nodes with the specified type as an array.                                                                                                                                                                                 |
    | `java.lang.String`                      | `getNodeDurationColumn``()`<br>Deprecated.                                                                                                                                                                                                                                        |
    | `java.lang.String`                      | `getNodeGeomColumn``()`<br>Returns the node geometry column name in the database.                                                                                                                                                                                                 |
    | `int[]`                                 | `getNodeHierarchyLevelArray``()`<br>Returns the node hierarchy levels as an array.                                                                                                                                                                                                |
    | `java.lang.String`                      | `getNodePartitionColumn``()`<br>Deprecated.                                                                                                                                                                                                                                       |
    | `java.util.Iterator`                    | `getNodes``()`<br>Returns the nodes as an Iterator.                                                                                                                                                                                                                               |
    | `java.util.Iterator`                    | `getNodes``(boolean active)`<br>Returns the nodes with the specified acvive flag as an Iterator                                                                                                                                                                                   |
    | `java.util.Iterator`                    | `getNodes``(int hierarchyLevel)`<br>Returns the nodes with the specified hierarchy level as an Iterator.                                                                                                                                                                          |
    | `java.util.Iterator`                    | `getNodes``(java.lang.String type)`<br>Returns the nodes with the specified type as an Iterator.                                                                                                                                                                                  |
    | `java.util.Set`                         | `getNodesByPartitionID``(int partitionID)`<br>Returns the nodes with the specified partition ID as a Set.                                                                                                                                                                         |
    | `java.lang.String`                      | `getNodeTableName``()`<br>Deprecated.                                                                                                                                                                                                                                             |
    | `int`                                   | `getNoOfHierarchyLevels``()`<br>Returns the number of hierarcchy levels.                                                                                                                                                                                                          |
    | `int`                                   | `getNoOfLinks``()`<br>Returns the number of links.                                                                                                                                                                                                                                |
    | `int`                                   | `getNoOfLinks``(boolean active)`<br>Returns the number of links with the specified active flag.                                                                                                                                                                                   |
    | `int`                                   | `getNoOfLinks``(int level)`<br>Returns the number of links with the specified link level.                                                                                                                                                                                         |
    | `int`                                   | `getNoOfNodes``()`<br>Returns the number of nodes.                                                                                                                                                                                                                                |
    | `int`                                   | `getNoOfNodes``(boolean active)`<br>Returns the number of nodes with the specified active flag.                                                                                                                                                                                   |
    | `int`                                   | `getNoOfNodes``(int hierarchyLevel)`<br>Returns the number of nodes with the specified hierachy level.                                                                                                                                                                            |
    | `int`                                   | `getNoOfPartitions``()`<br>Returns the number of partitions.                                                                                                                                                                                                                      |
    | `int`                                   | `getNoOfPaths``()`<br>Returns the number of paths.                                                                                                                                                                                                                                |
    | `int`                                   | `getNoOfPaths``(boolean active)`<br>Returns the number of paths with the specified active flag.                                                                                                                                                                                   |
    | `int`                                   | `getNoOfSubPaths``()`<br>Returns the number of subpaths.                                                                                                                                                                                                                          |
    | `java.lang.String`                      | `getPartitionTableName``()`<br>Returns the partition table name in the database.                                                                                                                                                                                                  |
    | [`Path`](Path.md)                       | `getPath``(int pathID)`<br>Returns the path by ID.                                                                                                                                                                                                                                |
    | [`Path`](Path.md)                       | `getPath``(java.lang.String pathID)`<br>Returns the path by the String ID.                                                                                                                                                                                                        |
    | [`Path`](Path.md)`[]`                   | `getPathArray``()`<br>Returns the paths as an array.                                                                                                                                                                                                                              |
    | [`Path`](Path.md)`[]`                   | `getPathArray``(boolean active)`<br>Returns the paths with the specified active flag as an array.                                                                                                                                                                                 |
    | [`Path`](Path.md)`[]`                   | `getPathArray``(java.lang.String type)`<br>Returns the paths with the specified type as an array.                                                                                                                                                                                 |
    | `java.lang.String`                      | `getPathLinkTableName``()`<br>Deprecated.                                                                                                                                                                                                                                         |
    | `java.util.Iterator`                    | `getPaths``()`<br>Returns the paths as an Iterator.                                                                                                                                                                                                                               |
    | `java.util.Iterator`                    | `getPaths``(boolean active)`<br>Returns paths with the specified active as an Iterator.                                                                                                                                                                                           |
    | `java.util.Iterator`                    | `getPaths``(java.lang.String type)`<br>Returns the paths with the specified type as an Iterator.                                                                                                                                                                                  |
    | `java.lang.String`                      | `getPathTableName``()`<br>Deprecated.                                                                                                                                                                                                                                             |
    | `Network`                               | `getSubNetwork``(`[`MBR`](MBR.md)` mbr)`<br>Returns the sub-network bound by the specified MBR.                                                                                                                                                                                   |
    | [`SubPath`](SubPath.md)                 | `getSubPath``(int subPathID)`<br>Returns the subpath by ID.                                                                                                                                                                                                                       |
    | [`SubPath`](SubPath.md)                 | `getSubPath``(java.lang.String subPathID)`<br>Returns the subpath by the String ID.                                                                                                                                                                                               |
    | [`SubPath`](SubPath.md)`[]`             | `getSubPathArray``()`<br>Returns the subpaths as an array.                                                                                                                                                                                                                        |
    | [`SubPath`](SubPath.md)`[]`             | `getSubPathArray``(boolean active)`<br>Returns the subpaths with the specified active flag as an array.                                                                                                                                                                           |
    | [`SubPath`](SubPath.md)`[]`             | `getSubPathArray``(java.lang.String type)`<br>Returns the subpaths with the specified type as an array.                                                                                                                                                                           |
    | `java.util.Iterator`                    | `getSubPaths``()`<br>Returns the subpaths as an Iterator.                                                                                                                                                                                                                         |
    | `java.util.Iterator`                    | `getSubPaths``(boolean active)`<br>Returns subpaths with the specified active as an Iterator.                                                                                                                                                                                     |
    | `java.util.Iterator`                    | `getSubPaths``(java.lang.String type)`<br>Returns the subpaths with the specified type as an Iterator.                                                                                                                                                                            |
    | `java.lang.String`                      | `getSubPathTableName``()`<br>Deprecated.                                                                                                                                                                                                                                          |
    | [`Link`](Link.md)`[]`                   | `getTemporaryLinkArray``()`<br>Returns all temporary links as an array.                                                                                                                                                                                                           |
    | [`Node`](Node.md)`[]`                   | `getTemporaryNodeArray``()`<br>Returns all temporary nodes as an array.                                                                                                                                                                                                           |
    | `java.lang.Object`                      | `getUserData``()`<br>Gets user defined data.                                                                                                                                                                                                                                      |
    | `java.lang.Object`                      | `getUserData``(java.lang.String name)`<br>Gets user data                                                                                                                                                                                                                          |
    | `boolean`                               | `hasNodeCost``()`<br>Checks if the network has node cost.                                                                                                                                                                                                                         |
    | `boolean`                               | `hasStringID``()`<br>Checks if the network has String ID index                                                                                                                                                                                                                    |
    | `Network`                               | `intersectNetwork``(Network network)`<br>Intersects the network with the given network.                                                                                                                                                                                           |
    | `boolean`                               | `isConnected``()`<br>Checks if the network is connected.                                                                                                                                                                                                                          |
    | `boolean`                               | `isDirected``()`<br>Checks if the network is directed.                                                                                                                                                                                                                            |
    | `boolean`                               | `isHierarchical``()`<br>Checks if the network is hierarchical (hierarchy level \> 1).                                                                                                                                                                                             |
    | `boolean`                               | `isLogical``()`<br>Checks if the network is logical (without spatial information).                                                                                                                                                                                                |
    | `boolean`                               | `isLRSGeometry``()`<br>Checks if the network is from an LRS geometry layer.                                                                                                                                                                                                       |
    | `boolean`                               | `isModified``()`<br>Checks if the network has been modified.                                                                                                                                                                                                                      |
    | `boolean`                               | `isPartitioned``()`<br>Checks if the network is partitioned.                                                                                                                                                                                                                      |
    | `boolean`                               | `isPersistent``()`<br>Checks if the network is persistent (stored in the database).                                                                                                                                                                                               |
    | `boolean`                               | `isReadOnly``()`<br>Checks if the network is read-only to the database.                                                                                                                                                                                                           |
    | `boolean`                               | `isSDOGeometry``()`<br>Checks if the network is from an SDO geometry layer.                                                                                                                                                                                                       |
    | `boolean`                               | `isSimple``()`<br>Deprecated.                                                                                                                                                                                                                                                     |
    | `boolean`                               | `isSpatial``()`<br>Checks if the network is spatial (with spatial information).                                                                                                                                                                                                   |
    | `boolean`                               | `isTopoGeometry``()`<br>Checks if the network is from a TOPO geometry layer.                                                                                                                                                                                                      |
    | `boolean`                               | `isTree``()`<br>Checks if the network is a tree.                                                                                                                                                                                                                                  |
    | `boolean`                               | `isUndirected``()`<br>Checks if the network is un-directed.                                                                                                                                                                                                                       |
    | `boolean`                               | `isVersioned``()`<br>Checks if the network is versioned                                                                                                                                                                                                                           |
    | [`Link`](Link.md)`[]`                   | `nearestLink``(double x, double y)`<br>Gets the nearest link in a spatial network The result is in an array of Link.                                                                                                                                                              |
    | [`Node`](Node.md)`[]`                   | `nearestNode``(double x, double y)`<br>Gets the nearest node in a spatial network The result is in an array of Node.                                                                                                                                                              |
    | `void`                                  | `resetComponentNo``(int no)`<br>Resets the node compomnent number to the specified number                                                                                                                                                                                         |
    | `void`                                  | `setCategory``(int category)`<br>Sets the network category.                                                                                                                                                                                                                       |
    | `void`                                  | `setLinkCostFunction``(`[`LinkCostFunction`](LinkCostFunction.md)` costFunction)`<br>Sets up user defined link cost function                                                                                                                                                      |
    | `void`                                  | `setLinkDurationColumn``(java.lang.String durationColumn)`<br>Deprecated.                                                                                                                                                                                                         |
    | `void`                                  | `setLinkPartitionColumn``(java.lang.String partitionColumnName)`<br>Deprecated.                                                                                                                                                                                                   |
    | `void`                                  | `setMaxLinkID``(int maxID)`<br>Sets the max link ID to maxID                                                                                                                                                                                                                      |
    | `void`                                  | `setMaxNodeID``(int maxID)`<br>Sets the max node ID to maxID                                                                                                                                                                                                                      |
    | `void`                                  | `setMaxPathID``(int maxID)`<br>Sets the max path ID to maxID                                                                                                                                                                                                                      |
    | `void`                                  | `setMaxSubPathID``(int maxID)`<br>Sets the max subpath ID to maxID                                                                                                                                                                                                                |
    | `void`                                  | `setNodeDurationColumn``(java.lang.String durationColumn)`<br>Deprecated.                                                                                                                                                                                                         |
    | `void`                                  | `setNodePartitionColumn``(java.lang.String partitionColumnName)`<br>Deprecated.                                                                                                                                                                                                   |
    | `void`                                  | `setNoOfHierarchyLevels``(int no)`<br>Deprecated.                                                                                                                                                                                                                                 |
    | `void`                                  | `setPartitionTableName``(java.lang.String partitionTableName)`<br>Deprecated.                                                                                                                                                                                                     |
    | `void`                                  | `setStringIDIndex``()`<br>Sets String ID indexes for nodes, links ,and paths.                                                                                                                                                                                                     |
    | `void`                                  | `setStringIDIndex``(oracle.spatial.network.NDMStringID nodeStringID, oracle.spatial.network.NDMStringID linkStringID, oracle.spatial.network.NDMStringID pathStringID)`<br>Sets String ID indexes for nodes,links ,and paths.                                                     |
    | `void`                                  | `setStringIDIndex``(oracle.spatial.network.NDMStringID nodeStringID, oracle.spatial.network.NDMStringID linkStringID, oracle.spatial.network.NDMStringID pathStringID, oracle.spatial.network.NDMStringID subPathStringID)`<br>Sets String ID indexes for nodes,links ,and paths. |
    | `void`                                  | `setTemporaryCachingEnabled``(boolean flag)`<br>Enable/Disable Temporatory Element caching.                                                                                                                                                                                       |
    | `void`                                  | `setUserData``(java.lang.Object userData)`<br>Sets user defined data.                                                                                                                                                                                                             |
    | `void`                                  | `setUserData``(java.lang.String name, java.lang.Object data)`<br>Sets user data                                                                                                                                                                                                   |

<!-- -->

- - ### Field Detail

    - #### LOGICAL_NETWORK

          static final int LOGICAL_NETWORK

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SPATIAL_NETWORK

          static final int SPATIAL_NETWORK

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UNDIRECTED_LINK

          static final int UNDIRECTED_LINK

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### BIDIRECTED_LINK

          static final int BIDIRECTED_LINK

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DIRECTED_LINK

          static final int DIRECTED_LINK

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SDO_GEOMETRY_TYPE

          static final int SDO_GEOMETRY_TYPE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### LRS_GEOMETRY_TYPE

          static final int LRS_GEOMETRY_TYPE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### TOPO_GEOMETRY_TYPE

          static final int TOPO_GEOMETRY_TYPE

      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getMetadata

          NetworkMetadata getMetadata()

      Returns the network metadata.

    <!-- -->

    - #### getName

          java.lang.String getName()

      Returns the network name.

    <!-- -->

    - #### getNodeArray

          Node[] getNodeArray()

      Returns the nodes as an array.

    <!-- -->

    - #### getNodes

          java.util.Iterator getNodes()

      Returns the nodes as an Iterator.

    <!-- -->

    - #### getNodeArray

          Node[] getNodeArray(boolean active)

      Returns the nodes with the specified acvive flag as an array.

    <!-- -->

    - #### getNodes

          java.util.Iterator getNodes(boolean active)

      Returns the nodes with the specified acvive flag as an Iterator
      Parameters:
      `active` - the active flag

    <!-- -->

    - #### getNodeArray

          Node[] getNodeArray(int hierarchyLevel)

      Returns the nodes with the specified hierarchy level as an array.
      Parameters:
      `hierarchyLevel` - the hierarchy level

    <!-- -->

    - #### getNodes

          java.util.Iterator getNodes(int hierarchyLevel)

      Returns the nodes with the specified hierarchy level as an Iterator.
      Parameters:
      `hierarchyLevel` - the hierarchy level of the nodes

    <!-- -->

    - #### getNodeArray

          Node[] getNodeArray(java.lang.String type)

      Returns the nodes with the specified type as an array.
      Parameters:
      `type` - the node type

    <!-- -->

    - #### getNodes

          java.util.Iterator getNodes(java.lang.String type)

      Returns the nodes with the specified type as an Iterator.
      Parameters:
      `type` - the node type

    <!-- -->

    - #### getLinkArray

          Link[] getLinkArray()

      Returns the links as an array.

    <!-- -->

    - #### getLinks

          java.util.Iterator getLinks()

      Returns the links as an Iterator.

    <!-- -->

    - #### getLinkArray

          Link[] getLinkArray(boolean active)

      Returns the links with the specified active flag as an array.
      Parameters:
      `active` - the active flag

    <!-- -->

    - #### getLinks

          java.util.Iterator getLinks(boolean active)

      Returns the links with the specified active flag as an Iterator.
      Parameters:
      `active` - the active flag

    <!-- -->

    - #### getLinkArray

          Link[] getLinkArray(int level)

      Returns the links with the specified level as an array.
      Parameters:
      `level` - target link level

    <!-- -->

    - #### getLinks

          java.util.Iterator getLinks(int level)

      Returns the links with the specified link level as an Iterator.
      Parameters:
      `level` - target link level

    <!-- -->

    - #### getLinkArray

          Link[] getLinkArray(java.lang.String type)

      Returns the links with the specified type as an array.
      Parameters:
      `type` - the link type

    <!-- -->

    - #### getLinks

          java.util.Iterator getLinks(java.lang.String type)

      Returns the links with the specified type as an Iterator.
      Parameters:
      `type` - the link type

    <!-- -->

    - #### getNoOfNodes

          int getNoOfNodes()

      Returns the number of nodes.

    <!-- -->

    - #### getNoOfNodes

          int getNoOfNodes(boolean active)

      Returns the number of nodes with the specified active flag.
      Parameters:
      `active` - the active flag

    <!-- -->

    - #### getNoOfNodes

          int getNoOfNodes(int hierarchyLevel)

      Returns the number of nodes with the specified hierachy level.
      Parameters:
      `hierarchyLevel` - the hierarchy level

    <!-- -->

    - #### getNoOfLinks

          int getNoOfLinks()

      Returns the number of links.

    <!-- -->

    - #### getNoOfLinks

          int getNoOfLinks(boolean active)

      Returns the number of links with the specified active flag.
      Parameters:
      `active` - the active flag

    <!-- -->

    - #### getNoOfLinks

          int getNoOfLinks(int level)

      Returns the number of links with the specified link level.
      Parameters:
      `level` - the link level

    <!-- -->

    - #### getNoOfPaths

          int getNoOfPaths()

      Returns the number of paths.

    <!-- -->

    - #### getNoOfSubPaths

          int getNoOfSubPaths()

      Returns the number of subpaths.

    <!-- -->

    - #### getNoOfPaths

          int getNoOfPaths(boolean active)

      Returns the number of paths with the specified active flag.
      Parameters:
      `active` - the active flag

    <!-- -->

    - #### isConnected

          boolean isConnected()

      Checks if the network is connected.
      Returns:
      true if connected, false otherwise

    <!-- -->

    - #### isDirected

          boolean isDirected()

      Checks if the network is directed.
      Returns:
      true if directed, false otherwise

    <!-- -->

    - #### isUndirected

          boolean isUndirected()

      Checks if the network is un-directed.
      Returns:
      true if un-directed, false otherwise

    <!-- -->

    - #### isLogical

          boolean isLogical()

      Checks if the network is logical (without spatial information).
      Returns:
      true if logical, false otherwise

    <!-- -->

    - #### isSpatial

          boolean isSpatial()

      Checks if the network is spatial (with spatial information).
      Returns:
      true if spatial, false otherwise

    <!-- -->

    - #### isLRSGeometry

          boolean isLRSGeometry()

      Checks if the network is from an LRS geometry layer.

    <!-- -->

    - #### isSDOGeometry

          boolean isSDOGeometry()

      Checks if the network is from an SDO geometry layer.

    <!-- -->

    - #### isTopoGeometry

          boolean isTopoGeometry()

      Checks if the network is from a TOPO geometry layer.

    <!-- -->

    - #### isHierarchical

          boolean isHierarchical()

      Checks if the network is hierarchical (hierarchy level \> 1).
      Returns:
      true if the network is hierarchical, false otherwise

    <!-- -->

    - #### getNoOfHierarchyLevels

          int getNoOfHierarchyLevels()

      Returns the number of hierarcchy levels.

    <!-- -->

    - #### getNoOfPartitions

          int getNoOfPartitions()

      Returns the number of partitions.

    <!-- -->

    - #### clear

          void clear()

      Clears all network structure.

    <!-- -->

    - #### getNode

          Node getNode(int nodeID)
                throws NetworkDataException

      Returns the node by ID.
      Parameters:
      `nodeID` - the node ID

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### getNode

          Node getNode(java.lang.String nodeID)
                throws NetworkDataException

      Returns the node by the String ID.
      Parameters:
      `nodeID` - the node String ID

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### getLink

          Link getLink(int linkID)
                throws NetworkDataException

      Returns the link by ID.
      Parameters:
      `linkID` - the link ID

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### getLink

          Link getLink(java.lang.String linkID)
                throws NetworkDataException

      Returns the link by the STring ID.
      Parameters:
      `linkID` - the link String ID

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### getLink

          Link getLink(int startNodeID,
                       int endNodeID)
                throws NetworkDataException

      Returns the link by the start and the end node IDs
      Parameters:
      `startNodeID` - the start node ID

      `endNodeID` - the end node ID

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### getPath

          Path getPath(int pathID)
                throws NetworkDataException

      Returns the path by ID.
      Parameters:
      `pathID` - the path ID

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### getPath

          Path getPath(java.lang.String pathID)
                throws NetworkDataException

      Returns the path by the String ID.
      Parameters:
      `pathID` - the path ID

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### getPathArray

          Path[] getPathArray()

      Returns the paths as an array.

    <!-- -->

    - #### getPaths

          java.util.Iterator getPaths()

      Returns the paths as an Iterator.

    <!-- -->

    - #### getPathArray

          Path[] getPathArray(boolean active)

      Returns the paths with the specified active flag as an array.
      Parameters:
      `active` - the active flag

    <!-- -->

    - #### getPaths

          java.util.Iterator getPaths(boolean active)

      Returns paths with the specified active as an Iterator.
      Parameters:
      `active` - the active flag

    <!-- -->

    - #### getPathArray

          Path[] getPathArray(java.lang.String type)

      Returns the paths with the specified type as an array.
      Parameters:
      `type` - the path type

    <!-- -->

    - #### getPaths

          java.util.Iterator getPaths(java.lang.String type)

      Returns the paths with the specified type as an Iterator.
      Parameters:
      `type` - the path type

    <!-- -->

    - #### getSubPath

          SubPath getSubPath(int subPathID)
                      throws NetworkDataException

      Returns the subpath by ID.
      Parameters:
      `subPathID` - the subpath ID

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### getSubPath

          SubPath getSubPath(java.lang.String subPathID)
                      throws NetworkDataException

      Returns the subpath by the String ID.
      Parameters:
      `subPathID` - the subpath ID

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### getSubPathArray

          SubPath[] getSubPathArray()

      Returns the subpaths as an array.

    <!-- -->

    - #### getSubPaths

          java.util.Iterator getSubPaths()

      Returns the subpaths as an Iterator.

    <!-- -->

    - #### getSubPathArray

          SubPath[] getSubPathArray(boolean active)

      Returns the subpaths with the specified active flag as an array.
      Parameters:
      `active` - the active flag

    <!-- -->

    - #### getSubPaths

          java.util.Iterator getSubPaths(boolean active)

      Returns subpaths with the specified active as an Iterator.
      Parameters:
      `active` - the active flag

    <!-- -->

    - #### getSubPathArray

          SubPath[] getSubPathArray(java.lang.String type)

      Returns the subpaths with the specified type as an array.
      Parameters:
      `type` - the subpath type

    <!-- -->

    - #### getSubPaths

          java.util.Iterator getSubPaths(java.lang.String type)

      Returns the subpaths with the specified type as an Iterator.
      Parameters:
      `type` - the path type

    <!-- -->

    - #### addNode

          void addNode(Node n)
                throws NetworkDataException

      Adds a node to the network.
      Parameters:
      `n` - the node to be added

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### addNodes

          void addNodes(Node[] nodeArray)
                 throws NetworkDataException

      Adds an array of nodes to the network.
      Parameters:
      `nodeArray` - the array of nodes to be added

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### addNode

          Node addNode(Link l,
                       double distanceRatio,
                       boolean isTemporary)
                throws NetworkDataException

      Adds a node on a link to the network.
      Parameters:
      `l` - the link on which the node is added

      `distanceRatio` - the ratio (between 0 and 1) from the start point of the link

      `isTemporary` - if the node is temporary node

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### addTemporaryNode

          Node addTemporaryNode(Link l,
                                double distanceRatio)
                         throws NetworkDataException

      Adds a Temporary node (non-persistent) on a link.
      Parameters:
      `l` - the link on which the node is added

      `distanceRatio` - ratio (between 0 and 1) from the start point of the link

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### addLink

          void addLink(Link l)
                throws NetworkDataException

      Adds a link to the network.
      Parameters:
      `l` - the link to be added

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### addLinks

          void addLinks(Link[] linkArray)
                 throws NetworkDataException

      Adds an array of links to the network.
      Parameters:
      `linkArray` - the array of links to be added

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### deleteNode

          void deleteNode(int nodeID)
                   throws NetworkDataException

      Deletes a node by ID.
      Parameters:
      `nodeID` - the node ID

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### deleteNode

          void deleteNode(java.lang.String nodeID)
                   throws NetworkDataException

      Deletes a node by the STring ID.
      Parameters:
      `nodeID` - the node String ID

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### deleteNode

          void deleteNode(Node n)

      Deletes a node.
      Parameters:
      `n` - the node to be deleted

    <!-- -->

    - #### deleteLink

          void deleteLink(int linkID)
                   throws NetworkDataException

      Deletes a link by ID.
      Parameters:
      `linkID` - the link ID

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### deleteLink

          void deleteLink(java.lang.String linkID)
                   throws NetworkDataException

      Deletes a link by the String ID.
      Parameters:
      `linkID` - the link String ID

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### deleteLink

          void deleteLink(Link l)

      Deletes a link.
      Parameters:
      `l` - the link to be deleted

    <!-- -->

    - #### addPath

          void addPath(Path path)
                throws NetworkDataException

      Adds a path to the network.
      Parameters:
      `path` - the path to be added

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### addSubPath

          void addSubPath(SubPath subPath)
                   throws NetworkDataException

      Adds a subpath to the network.
      Parameters:
      `subPath` - the subpath to be added

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### addPaths

          void addPaths(Path[] pathArray)
                 throws NetworkDataException

      Adds an array of paths to the network.
      Parameters:
      `pathArray` - the array of paths to be added

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### addSubPaths

          void addSubPaths(SubPath[] subPathArray)
                    throws NetworkDataException

      Adds an array of subpaths to the network.
      Parameters:
      `subPathArray` - the array of subpaths to be added

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### deletePath

          void deletePath(int pathID)
                   throws NetworkDataException

      Deletes a path by ID.
      Parameters:
      `pathID` - the path to be deleted

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### deletePath

          void deletePath(java.lang.String pathID)
                   throws NetworkDataException

      Deletes a path by the String ID.
      Parameters:
      `pathID` - the path to be deleted

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### deletePath

          void deletePath(Path path)

      Deletes a path.
      Parameters:
      `path` - the path to be deleted

    <!-- -->

    - #### deleteSubPath

          void deleteSubPath(int subPathID)
                      throws NetworkDataException

      Deletes a subpath by ID.
      Parameters:
      `subPathID` - the subpath to be deleted

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### deleteSubPath

          void deleteSubPath(java.lang.String subPathID)
                      throws NetworkDataException

      Deletes a subpath by the String ID.
      Parameters:
      `subPathID` - the subpath to be deleted

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### deleteSubPath

          void deleteSubPath(SubPath subPath)

      Deletes a subpath.
      Parameters:
      `subPath` - the subpath to be deleted

    <!-- -->

    - #### resetComponentNo

          void resetComponentNo(int no)

      Resets the node compomnent number to the specified number
      Parameters:
      `no` - new component number

    <!-- -->

    - #### isTree

          boolean isTree()

      Checks if the network is a tree.

    <!-- -->

    - #### getMaxNodeID

          int getMaxNodeID()

      Returns the maximun node ID.

    <!-- -->

    - #### getMaxLinkID

          int getMaxLinkID()

      Returns the maximum link ID.

    <!-- -->

    - #### getMaxPathID

          int getMaxPathID()

      Returns the maximum path ID.

    <!-- -->

    - #### getMaxSubPathID

          int getMaxSubPathID()

      Returns the maximum subpath ID.

    <!-- -->

    - #### getTemporaryNodeArray

          Node[] getTemporaryNodeArray()

      Returns all temporary nodes as an array.

    <!-- -->

    - #### getTemporaryLinkArray

          Link[] getTemporaryLinkArray()

      Returns all temporary links as an array.

    <!-- -->

    - #### deleteTemporaryElements

          void deleteTemporaryElements()

      Deletes all temporary elements (nodes and links).

    <!-- -->

    - #### getSubNetwork

          Network getSubNetwork(MBR mbr)

      Returns the sub-network bound by the specified MBR.
      Parameters:
      `mbr` - the specified MBR

    <!-- -->

    - #### addNetwork

          void addNetwork(Network n)
                   throws NetworkDataException

      Adds a network to the current network. The elements that have the same IDs are considered the same.
      Parameters:
      `n` - the network to be added

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### deleteNetwork

          void deleteNetwork(Network n)
                      throws NetworkDataException

      Deletes a sub-network.
      Parameters:
      `n` - the sub-network to be deleted

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### setNoOfHierarchyLevels

          void setNoOfHierarchyLevels(int no)

      Deprecated. 
      Sets the number of hierarchy levels.
      Parameters:
      `no` - the number of hierarchy levels

    <!-- -->

    - #### getNodeTableName

          java.lang.String getNodeTableName()

      Deprecated. 
      Returns the node table name in the database.

    <!-- -->

    - #### getLinkTableName

          java.lang.String getLinkTableName()

      Deprecated. 
      Returns the link table name in the database.

    <!-- -->

    - #### getPathTableName

          java.lang.String getPathTableName()

      Deprecated. 
      Returns the path table name in the database.

    <!-- -->

    - #### getSubPathTableName

          java.lang.String getSubPathTableName()

      Deprecated. 
      Returns the subpath table name in the database.

    <!-- -->

    - #### getPathLinkTableName

          java.lang.String getPathLinkTableName()

      Deprecated. 
      Returns the path link table name in the database.

    <!-- -->

    - #### getPartitionTableName

          java.lang.String getPartitionTableName()

      Returns the partition table name in the database.

    <!-- -->

    - #### getLRSTableName

          java.lang.String getLRSTableName()

      Deprecated. 
      Returns the network geometry (LRS) table name in the database.

    <!-- -->

    - #### getNodeGeomColumn

          java.lang.String getNodeGeomColumn()

      Returns the node geometry column name in the database.

    <!-- -->

    - #### getNetworkCache

          oracle.spatial.network.NetworkCache getNetworkCache()

      Returns the network cache for editing purpose.

    <!-- -->

    - #### getMetadataViewName

          java.lang.String getMetadataViewName()

      Returns the network metadata view name (user_sdo_network_metadata).

    <!-- -->

    - #### getNodeHierarchyLevelArray

          int[] getNodeHierarchyLevelArray()

      Returns the node hierarchy levels as an array.

    <!-- -->

    - #### getLinkHierarchyLevelArray

          int[] getLinkHierarchyLevelArray()

      Returns the link hierarchy levels as an array.

    <!-- -->

    - #### getLinkLevelArray

          int[] getLinkLevelArray()

      Returns the link levels as an array.

    <!-- -->

    - #### getMBR

          MBR getMBR()

      Returns the network MBR. It will return null for logical networks.

    <!-- -->

    - #### getNodesByPartitionID

          java.util.Set getNodesByPartitionID(int partitionID)

      Returns the nodes with the specified partition ID as a Set.

    <!-- -->

    - #### getLinksByPartitionID

          java.util.Set getLinksByPartitionID(int partitionID)

      Returns the links with the specified partition ID as a Set.

    <!-- -->

    - #### getNodePartitionColumn

          java.lang.String getNodePartitionColumn()

      Deprecated. 
      Returns the node partition column in the database.

    <!-- -->

    - #### getLinkPartitionColumn

          java.lang.String getLinkPartitionColumn()

      Deprecated. 
      Returns the link partition column in the database.

    <!-- -->

    - #### getUserData

          java.lang.Object getUserData()

      Gets user defined data.

    <!-- -->

    - #### setUserData

          void setUserData(java.lang.Object userData)

      Sets user defined data.

    <!-- -->

    - #### isPersistent

          boolean isPersistent()

      Checks if the network is persistent (stored in the database).
      Returns:
      true if persistent, false otherwise

    <!-- -->

    - #### setCategory

          void setCategory(int category)

      Sets the network category.
      Parameters:
      `category` - the network category It is eitehr Network.SPATIAL_NETWORK or Network.LOGICAL_NETWORK

    <!-- -->

    - #### hasNodeCost

          boolean hasNodeCost()

      Checks if the network has node cost.
      Returns:
      true if the node cost column information is specified, false otherwise

    <!-- -->

    - #### isModified

          boolean isModified()

      Checks if the network has been modified.

    <!-- -->

    - #### isPartitioned

          boolean isPartitioned()

      Checks if the network is partitioned.

    <!-- -->

    - #### clone

          java.lang.Object clone()

      Clones the network.

    <!-- -->

    - #### intersectNetwork

          Network intersectNetwork(Network network)
                            throws NetworkDataException

      Intersects the network with the given network. The elements that have same IDs are considered the same. The intersection network is returned.
      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### getNetworkID

          int getNetworkID()

      Returns the network ID.

    <!-- -->

    - #### setStringIDIndex

          void setStringIDIndex()
                         throws NetworkDataException

      Sets String ID indexes for nodes, links ,and paths. This provides a fast search mechanism for lable-based networks. The element name is used as the String ID and the HashMaps based on the element String IDs will be built. Note that the String IDs have to be unique or an exception will be thrown. Once the String ID Indexes of a network are created, getNode(String nodeStringID), getLink(String linkSTringID), and getPath(String pathStringID) can be used.
      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### setStringIDIndex

          void setStringIDIndex(oracle.spatial.network.NDMStringID nodeStringID,
                                oracle.spatial.network.NDMStringID linkStringID,
                                oracle.spatial.network.NDMStringID pathStringID,
                                oracle.spatial.network.NDMStringID subPathStringID)
                         throws NetworkDataException

      Sets String ID indexes for nodes,links ,and paths. This provides a fast search mechanism for lable-based networks. The network element String IDs are defined by the user via the NDMStringID interface This interface takes a Node , a Link, and a Path as inputs and returns a unique String ID. If the StringID function is null, the element name is used as the String ID and the HashMaps based on the element String IDs will be built. Note that the String IDs have to be unique or an exception will be thrown. Once the String ID Index of a network is created, getNode(String nodeStringID), getLink(String linkSTringID), and getPath(String pathStringID) can be used.
      Parameters:
      `nodeStringID` - node string ID interface

      `linkStringID` - link string ID interface

      `pathStringID` - path string ID interface

      `subPathStringID` - subpath string ID interface

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### setStringIDIndex

          void setStringIDIndex(oracle.spatial.network.NDMStringID nodeStringID,
                                oracle.spatial.network.NDMStringID linkStringID,
                                oracle.spatial.network.NDMStringID pathStringID)
                         throws NetworkDataException

      Sets String ID indexes for nodes,links ,and paths. This provides a fast search mechanism for lable-based networks. The network element String IDs are defined by the user via the NDMStringID interface This interface takes a Node , a Link, and a Path as inputs and returns a unique String ID. If the StringID function is null, the element name is used as the String ID and the HashMaps based on the element String IDs will be built. Note that the String IDs have to be unique or an exception will be thrown. Once the String ID Index of a network is created, getNode(String nodeStringID), getLink(String linkSTringID), and getPath(String pathStringID) can be used.
      Parameters:
      `nodeStringID` - node string ID interface

      `linkStringID` - link string ID interface

      `pathStringID` - path string ID interface

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### hasStringID

          boolean hasStringID()

      Checks if the network has String ID index

    <!-- -->

    - #### isSimple

          boolean isSimple()

      Deprecated. 
      Checks if the network is a simple network whcih does not refer to other networks

    <!-- -->

    - #### setNodePartitionColumn

          void setNodePartitionColumn(java.lang.String partitionColumnName)

      Deprecated. 
      Sets the node partition column name
      Parameters:
      `partitionColumnName` - node partition column

    <!-- -->

    - #### setLinkPartitionColumn

          void setLinkPartitionColumn(java.lang.String partitionColumnName)

      Deprecated. 
      Sets the link partition column name
      Parameters:
      `partitionColumnName` - link partition column

    <!-- -->

    - #### isReadOnly

          boolean isReadOnly()

      Checks if the network is read-only to the database.

    <!-- -->

    - #### setTemporaryCachingEnabled

          void setTemporaryCachingEnabled(boolean flag)

      Enable/Disable Temporatory Element caching. The default temporatory caching is disable.
      Parameters:
      `flag` - true if enabled, false disabled

    <!-- -->

    - #### clearTemporaryCache

          void clearTemporaryCache()

      Clears the temporatory cache

    <!-- -->

    - #### containsNode

          boolean containsNode(int nodeID)

      Checks if the network contains the given node

    <!-- -->

    - #### containsLink

          boolean containsLink(int linkID)

      Checks if the network contains the given link

    <!-- -->

    - #### containsPath

          boolean containsPath(int pathID)

      Checks if the network contains the given path

    <!-- -->

    - #### containsSubPath

          boolean containsSubPath(int subPathID)

      Checks if the network contains the given subpath

    <!-- -->

    - #### containsNode

          boolean containsNode(java.lang.String nodeID)

      Checks if the network contains the given node

    <!-- -->

    - #### containsLink

          boolean containsLink(java.lang.String linkID)

      Checks if the network contains the given link

    <!-- -->

    - #### containsPath

          boolean containsPath(java.lang.String pathID)

      Checks if the network contains the given path

    <!-- -->

    - #### containsSubPath

          boolean containsSubPath(java.lang.String subPathID)

      Checks if the network contains the given subpath

    <!-- -->

    - #### setPartitionTableName

          void setPartitionTableName(java.lang.String partitionTableName)

      Deprecated. 
      Sets partition table name

    <!-- -->

    - #### setNodeDurationColumn

          void setNodeDurationColumn(java.lang.String durationColumn)

      Deprecated. 
      Sets node duration column name

    <!-- -->

    - #### setLinkDurationColumn

          void setLinkDurationColumn(java.lang.String durationColumn)

      Deprecated. 
      Sets link duration column name

    <!-- -->

    - #### getNodeDurationColumn

          java.lang.String getNodeDurationColumn()

      Deprecated. 
      Gets node duration column name

    <!-- -->

    - #### getLinkDurationColumn

          java.lang.String getLinkDurationColumn()

      Deprecated. 
      Gets link duration column name

    <!-- -->

    - #### setUserData

          void setUserData(java.lang.String name,
                           java.lang.Object data)

      Sets user data
      Parameters:
      `name` - name for the user data

      `data` - user data

    <!-- -->

    - #### getUserData

          java.lang.Object getUserData(java.lang.String name)

      Gets user data
      Parameters:
      `name` - name for the user data

      Returns:
      user data as an Java Object

    <!-- -->

    - #### nearestNode

          Node[] nearestNode(double x,
                             double y)

      Gets the nearest node in a spatial network The result is in an array of Node. All nodes that are of the minimum distance to the given point (x,y) will be returned.
      Parameters:
      `x` - first ordinate of the given point

      `y` - second ordinate of the given point

      Returns:
      an array of Node with minimum distance to the given point(x,y)

    <!-- -->

    - #### nearestLink

          Link[] nearestLink(double x,
                             double y)

      Gets the nearest link in a spatial network The result is in an array of Link. All Links that are of the minimum distance to the given point (x,y) will be returned.
      Parameters:
      `x` - first ordinate of the given point

      `y` - second ordinate of the given point

      Returns:
      an array of Link with minimum distance to the given point(x,y)

    <!-- -->

    - #### containsUserData

          boolean containsUserData()

      Checks if the network has user data defined in user_network_user_data

    <!-- -->

    - #### addNodeData

          void addNodeData(java.lang.String dataName,
                           java.lang.String dataType,
                           int dataLength)
                    throws NetworkDataException

      Adds a node user data entry A NetworkDataException is thrown if the data already exists
      Parameters:
      `dataName` - data name for the user data

      `dataType` - data type for the user data ("INTEGER","NUMBER", "VARCHAR2")

      `dataLength` - data length for "VARCHAR2"

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### addLinkData

          void addLinkData(java.lang.String dataName,
                           java.lang.String dataType,
                           int dataLength)
                    throws NetworkDataException

      Adds a link user data entry A NetworkDataException is thrown if the data already exists
      Parameters:
      `dataName` - data name for the user data

      `dataType` - data type for the user data ("INTEGER","NUMBER", "VARCHAR2")

      `dataLength` - data length for "VARCHAR2"

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### addPathData

          void addPathData(java.lang.String dataName,
                           java.lang.String dataType,
                           int dataLength)
                    throws NetworkDataException

      Adds a path user data entry A NetworkDataException is thrown if the data already exists
      Parameters:
      `dataName` - data name for the user data

      `dataType` - data type for the user data ("INTEGER","NUMBER", "VARCHAR2")

      `dataLength` - data length for "VARCHAR2"

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### addSubPathData

          void addSubPathData(java.lang.String dataName,
                              java.lang.String dataType,
                              int dataLength)
                       throws NetworkDataException

      Adds a subpath user data entry A NetworkDataException is thrown if the data already exists
      Parameters:
      `dataName` - data name for the user data

      `dataType` - data type for the user data ("INTEGER","NUMBER", "VARCHAR2")

      `dataLength` - data length for "VARCHAR2"

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### deleteNodeData

          void deleteNodeData(java.lang.String dataName)

      Deletes a node user data entry
      Parameters:
      `dataName` - data name for the user data

    <!-- -->

    - #### deleteLinkData

          void deleteLinkData(java.lang.String dataName)

      Deletes a link user data entry
      Parameters:
      `dataName` - data name for the user data

    <!-- -->

    - #### deletePathData

          void deletePathData(java.lang.String dataName)

      Deletes a path user data entry
      Parameters:
      `dataName` - data name for the user data

    <!-- -->

    - #### deleteSubPathData

          void deleteSubPathData(java.lang.String dataName)

      Deletes a subpath user data entry
      Parameters:
      `dataName` - data name for the user data

    <!-- -->

    - #### isVersioned

          boolean isVersioned()

      Checks if the network is versioned

    <!-- -->

    - #### setLinkCostFunction

          void setLinkCostFunction(LinkCostFunction costFunction)

      Sets up user defined link cost function
      Parameters:
      `costFunction` - user defined link cost function

    <!-- -->

    - #### setMaxNodeID

          void setMaxNodeID(int maxID)

      Sets the max node ID to maxID
      Parameters:
      `maxID` -

    <!-- -->

    - #### setMaxLinkID

          void setMaxLinkID(int maxID)

      Sets the max link ID to maxID

    <!-- -->

    - #### setMaxPathID

          void setMaxPathID(int maxID)

      Sets the max path ID to maxID

    <!-- -->

    - #### setMaxSubPathID

          void setMaxSubPathID(int maxID)

      Sets the max subpath ID to maxID

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NDMTimer.md)
- [Next Class](NetworkConstraint.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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
