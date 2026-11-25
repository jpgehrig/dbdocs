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

- [Prev Class](NetworkFactory.md)
- [Next Class](NetworkMetadata.md)

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

## Class NetworkManager

- java.lang.Object

- - oracle.spatial.network.NetworkManager

<!-- -->

-

  ------------------------------------------------------------------------



      public class NetworkManager
      extends java.lang.Object

  This class defines methods for the network data I/O and network analysis.

<!-- -->

- - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                    | Method and Description                                                                                                                                                                                                                                                                                                                                                                                 |
    |------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static void`                                        | `addNetworkToCache``(java.lang.String networkName, `[`Network`](Network.md)` network)`<br>Adds a network in the network cahce                                                                                                                                                                                                                                                                          |
    | `static `[`Path`](Path.md)`[]`                       | `allPaths``(`[`Network`](Network.md)` network, int startNodeID, int goalNodeID, int depthLimit, double costLimit, int noOfSolutions)`<br>Returns all paths between the start node and the goal node.                                                                                                                                                                                                   |
    | `static `[`Path`](Path.md)`[]`                       | `allPaths``(`[`Network`](Network.md)` network, int startNodeID, int goalNodeID, `[`NetworkConstraint`](NetworkConstraint.md)` constraint, int noOfSolutions)`<br>Returns all paths between the start node and the goal node.                                                                                                                                                                           |
    | `static `[`Path`](Path.md)`[]`                       | `allPaths``(`[`Path`](Path.md)` complexPath, int depthLimit, double costLimit, int noOfSolutions)`<br>Returns all paths between the start node and the goal node of the complex path.                                                                                                                                                                                                                  |
    | `static void`                                        | `clearNetworkCache``()`<br>Clears the network cache                                                                                                                                                                                                                                                                                                                                                    |
    | `static `[`Network`](Network.md)                     | `convertNetworkBetweenWorkspaces``(java.sql.Connection conn, `[`Network`](Network.md)` sourceNetwork, java.lang.String sourceWorkspace, java.lang.String sourceSavepoint, java.lang.String targetWorkspace, java.lang.String targetSavepoint)`<br>Converts the source network into the network in the target workspace and savepoint based on their diffs in a workspace(version-enabled) environment. |
    | `static void`                                        | `createNetworkHiearchy``(`[`Network`](Network.md)` network, int numHierarchy, int[] ndNumLevel)`<br>Creates a network hiearchy with the given number of levels.                                                                                                                                                                                                                                        |
    | `static void`                                        | `createRefConstraints``(java.sql.Connection conn, java.lang.String network)`<br>Creates the referential constraints on the link and the path tables.                                                                                                                                                                                                                                                   |
    | `static void`                                        | `deregisterJavaObject``(java.sql.Connection conn, java.lang.String name)`<br>Deregister the given Java object from user_sdo_network_java_objects                                                                                                                                                                                                                                                       |
    | `static void`                                        | `deregisterNetworkConstraint``(java.sql.Connection conn, java.lang.String networkConstraintName)`<br>Deregister the given constraint from user_sdo_network_constraints                                                                                                                                                                                                                                 |
    | `static void`                                        | `disableRefConstraints``(java.sql.Connection conn, java.lang.String network)`<br>Disables the referential constraints on the link and the path tables.                                                                                                                                                                                                                                                 |
    | `static void`                                        | `dropNetwork``(java.sql.Connection conn, java.lang.String network)`<br>Drops the network from the database.                                                                                                                                                                                                                                                                                            |
    | `static void`                                        | `dropRefConstraints``(java.sql.Connection conn, java.lang.String network)`<br>Drops the referential constraints on the link and the path tables.                                                                                                                                                                                                                                                       |
    | `static void`                                        | `enableRefConstraints``(java.sql.Connection conn, java.lang.String network)`<br>Enables the referential constraints on the link and the path tables.                                                                                                                                                                                                                                                   |
    | `static int`                                         | `findConnectedComponents``(`[`Network`](Network.md)` network)`<br>Returns the number of connected components in the network.                                                                                                                                                                                                                                                                           |
    | `static java.util.Vector`                            | `findConnectedComponentVector``(`[`Network`](Network.md)` network)`<br>Returns connected components of the network in a Vector.                                                                                                                                                                                                                                                                        |
    | `static `[`Link`](Link.md)`[]`                       | `findExternalLinks``(`[`Node`](Node.md)`[] nodeArray1, `[`Node`](Node.md)`[] nodeArray2)`<br>Returns external links between the two arrays of nodes.                                                                                                                                                                                                                                                   |
    | `static `[`Link`](Link.md)`[]`                       | `findInternalLinks``(`[`Node`](Node.md)`[] nodeArray)`<br>Returns the internal links of the node array.                                                                                                                                                                                                                                                                                                |
    | `static int`                                         | `findMaxNodeDegree``(`[`Network`](Network.md)` network, int degreeType)`<br>Finds the maximum node degree of the network                                                                                                                                                                                                                                                                               |
    | `static `[`MBR`](MBR.md)                             | `findMBR``(`[`Node`](Node.md)`[] nodeArray, double expandFactor)`<br>Returns the MBR of the node array and expanded it by the specified factor.                                                                                                                                                                                                                                                        |
    | `static int`                                         | `findMinNodeDegree``(`[`Network`](Network.md)` network, int degreeType)`<br>Finds the minimum node degree of the network                                                                                                                                                                                                                                                                               |
    | `static `[`Node`](Node.md)`[]`                       | `findNodesWithinDegreeBounds``(`[`Network`](Network.md)` network, int degreeType, int minDegree, int maxDegree)`<br>Finds nodes with degree within the given degree bounds.                                                                                                                                                                                                                            |
    | `static `[`Node`](Node.md)`[]`                       | `findReachableNodes``(`[`Network`](Network.md)` network, int sourceNodeID)`<br>Returns all nodes that can be reached from the source node.                                                                                                                                                                                                                                                             |
    | `static `[`Node`](Node.md)`[]`                       | `findReachableNodes``(`[`Network`](Network.md)` network, int sourceNodeID, `[`MBR`](MBR.md)` mbr)`<br>Returns all nodes that can be reached from the source node.                                                                                                                                                                                                                                      |
    | `static `[`Node`](Node.md)`[]`                       | `findReachableNodes``(`[`Network`](Network.md)` network, int sourceNodeID, `[`MBR`](MBR.md)` mbr, int depthLimit)`<br>Returns all nodes that can be reached from the source node.                                                                                                                                                                                                                      |
    | `static `[`Node`](Node.md)`[]`                       | `findReachableNodes``(`[`Network`](Network.md)` network, int sourceNodeID, `[`MBR`](MBR.md)` mbr, int depthLimit, int maxNoOfNodes)`<br>Returns all nodes that can be reached from the source node.                                                                                                                                                                                                    |
    | `static `[`Node`](Node.md)`[]`                       | `findReachableNodes``(`[`Network`](Network.md)` network, int sourceNodeID, `[`MBR`](MBR.md)` mbr, int depthLimit, `[`NetworkConstraint`](NetworkConstraint.md)` constraint, int maxNoOfNodes)`<br>Returns all nodes that can be reached from the source node.                                                                                                                                          |
    | `static `[`Node`](Node.md)`[]`                       | `findReachableNodes``(`[`Network`](Network.md)` network, int sourceNodeID, `[`NetworkConstraint`](NetworkConstraint.md)` constraint)`<br>Returns all nodes that can be reached from the source node.                                                                                                                                                                                                   |
    | `static `[`Node`](Node.md)`[]`                       | `findReachingNodes``(`[`Network`](Network.md)` network, int targetNodeID)`<br>Returns all nodes that can reach the target node.                                                                                                                                                                                                                                                                        |
    | `static `[`Node`](Node.md)`[]`                       | `findReachingNodes``(`[`Network`](Network.md)` network, int targetNodeID, `[`MBR`](MBR.md)` mbr)`<br>Returns all nodes that can reach the target node.                                                                                                                                                                                                                                                 |
    | `static `[`Node`](Node.md)`[]`                       | `findReachingNodes``(`[`Network`](Network.md)` network, int targetNodeID, `[`MBR`](MBR.md)` mbr, int depthLimit)`<br>Returns all nodes that can reach the target node.                                                                                                                                                                                                                                 |
    | `static `[`Node`](Node.md)`[]`                       | `findReachingNodes``(`[`Network`](Network.md)` network, int targetNodeID, `[`MBR`](MBR.md)` mbr, int depthLimit, `[`NetworkConstraint`](NetworkConstraint.md)` constraint, int maxNoOfNodes)`<br>Returns all nodes that can reach the target node.                                                                                                                                                     |
    | `static `[`Node`](Node.md)`[]`                       | `findReachingNodes``(`[`Network`](Network.md)` network, int targetNodeID, `[`NetworkConstraint`](NetworkConstraint.md)` constraint)`<br>Returns all nodes that can reach the target node.                                                                                                                                                                                                              |
    | `static long`                                        | `getMaxFlow``(`[`Network`](Network.md)` network, int sourceNodeID, int sinkNodeID, java.util.Vector linkFlowVec)`<br>Retunrs the max flow between the source node and the sink node                                                                                                                                                                                                                    |
    | `static java.util.HashMap`                           | `getNetworkCacheMap``()`<br>Returns the network cache as a HashMap with network name (type: String) as keys and networks (type: Network) as values                                                                                                                                                                                                                                                     |
    | `static `[`Network`](Network.md)                     | `getNetworkFromCache``(java.lang.String networkName)`<br>Gets the network from the network cache if the specified network is not in the cache, null will be returned To add a network in the cache, use Networkmanager.putNetworkToCache(networkname, network)                                                                                                                                         |
    | `static int`                                         | `getNetworkIDFromName``(java.sql.Connection conn, java.lang.String networkName)`<br>Returns the network ID from a given network name                                                                                                                                                                                                                                                                   |
    | `static java.util.HashMap`                           | `getNetworkIDs``(java.sql.Connection conn)`<br>Retunrs network names and IDs from the database.                                                                                                                                                                                                                                                                                                        |
    | `static java.lang.String`                            | `getNetworkNameFromID``(java.sql.Connection conn, int networkID)`<br>Returns the network name from a given network ID                                                                                                                                                                                                                                                                                  |
    | `static java.util.HashMap`                           | `getNetworkNames``(java.sql.Connection conn)`<br>Retunrs network names and IDs from the database.                                                                                                                                                                                                                                                                                                      |
    | [`JGeometry`](../geometry/JGeometry.md)              | `getPathGeomFromDB``(java.sql.Connection conn, `[`Network`](Network.md)` network, `[`Path`](Path.md)` path, java.lang.String linkTableName, java.lang.String linkGeomColumnName, java.lang.String nodeTableName, java.lang.String nodeGeomColumnName, double tolerance)`<br>Gets/Computes the path geometry based on the geometries of path links and nodes in the database                            |
    | `static java.lang.String`                            | `getVersion``()`<br>Returns the version of the SDO networkAdapter.                                                                                                                                                                                                                                                                                                                                     |
    | `static void`                                        | `insertGeomMetadata``(java.sql.Connection conn, java.lang.String tableName, java.lang.String geomColumnName, int srid, `[`SDODimArray`](SDODimArray.md)` dimArray)`<br>Inserts the geometry metadata to the database.                                                                                                                                                                                  |
    | `static boolean`                                     | `isNetworkInCache``(java.lang.String networkName)`<br>Checks if a given network is in the cache                                                                                                                                                                                                                                                                                                        |
    | `static boolean`                                     | `isNetworkPartitioned``(java.sql.Connection conn, java.lang.String networkName)`<br>Returns the partition ID of the given node                                                                                                                                                                                                                                                                         |
    | `static boolean`                                     | `isReachable``(`[`Network`](Network.md)` network, int sourceNodeID, int targetNodeID)`<br>Checks if the source node can reach the target node.                                                                                                                                                                                                                                                         |
    | `static boolean`                                     | `isReachable``(`[`Network`](Network.md)` network, int sourceNodeID, int targetNodeID, `[`MBR`](MBR.md)` mbr, int depthLimit)`<br>Checks if the source node can reach the target node.                                                                                                                                                                                                                  |
    | `static boolean`                                     | `isReachable``(`[`Network`](Network.md)` network, int sourceNodeID, int targetNodeID, `[`NetworkConstraint`](NetworkConstraint.md)` constraint)`<br>Checks if the source node can reach the target node.                                                                                                                                                                                               |
    | `static void`                                        | `makeLogical``(`[`Network`](Network.md)` network)`<br>Convert a spatial network to a logical network Note this only updates the network metadata information original spatial information remains unahcnged                                                                                                                                                                                            |
    | `static void`                                        | `makeSpatial``(`[`Network`](Network.md)` network, java.lang.String nodeGeomColumn, java.lang.String linkGeomColumn, java.lang.String pathGeomColumn)`<br>Convert a logical network to a spatial network Note this only updates the network metadata information                                                                                                                                        |
    | `static `[`Network`](Network.md)                     | `mcst``(`[`Network`](Network.md)` network)`<br>Returns the minimum cost spanning tree (Kruskal Algorithm) as a network.                                                                                                                                                                                                                                                                                |
    | `static `[`Link`](Link.md)`[]`                       | `mcstLinkArray``(`[`Network`](Network.md)` network)`<br>Returns the minimum cost spanning tree (Kruskal Algorithm).                                                                                                                                                                                                                                                                                    |
    | `static `[`Path`](Path.md)`[]`                       | `nearestNeighbors``(`[`Network`](Network.md)` network, int startNodeID, int noOfNeighbors)`<br>Returns the shortest paths of the N nearest neighbors from the start node.                                                                                                                                                                                                                              |
    | `static `[`Path`](Path.md)`[]`                       | `nearestNeighbors``(`[`Network`](Network.md)` network, int startNodeID, int noOfNeighbors, `[`NetworkConstraint`](NetworkConstraint.md)` constraint)`<br>Returns the shortest paths of the N nearest neighbors from the start node.                                                                                                                                                                    |
    | `static `[`Path`](Path.md)`[]`                       | `nearestNeighbors``(`[`Network`](Network.md)` network, int startNodeID, int noOfNeighbors, `[`NetworkConstraint`](NetworkConstraint.md)` constraint, `[`GoalNode`](GoalNode.md)` goalNodeFilter)`<br>Returns the shortest paths of the N nearest neighbors from the specified start node.                                                                                                              |
    | `static `[`Path`](Path.md)`[]`                       | `nearestReachingNeighbors``(`[`Network`](Network.md)` network, int startNodeID, int noOfNeighbors)`<br>Returns the shortest paths of the N nearest reaching neighbors to the specified start node.                                                                                                                                                                                                     |
    | `static `[`Path`](Path.md)`[]`                       | `nearestReachingNeighbors``(`[`Network`](Network.md)` network, int startNodeID, int noOfNeighbors, `[`GoalNode`](GoalNode.md)` goalNodeFilter)`<br>Returns the shortest paths of the N nearest reaching neighbors to the specified start node.                                                                                                                                                         |
    | `static `[`Path`](Path.md)`[]`                       | `nearestReachingNeighbors``(`[`Network`](Network.md)` network, int startNodeID, int noOfNeighbors, `[`NetworkConstraint`](NetworkConstraint.md)` constraint, `[`GoalNode`](GoalNode.md)` goalNodeFilter)`<br>Returns the shortest paths of the N nearest reaching neighbors to the specified start node.                                                                                               |
    | `static boolean`                                     | `networkExists``(java.sql.Connection conn, java.lang.String network)`<br>Checks if the given network exists in the database.                                                                                                                                                                                                                                                                           |
    | `static `[`Path`](Path.md)                           | `newPathToDestination``(`[`Network`](Network.md)` network, `[`Path`](Path.md)` referencePath, int newStartNodeID, `[`NetworkConstraint`](NetworkConstraint.md)` constraint)`<br>Creates a new path starting from the new start node to the node on the reference path closest to the start node and to the end node of the reference path                                                              |
    | `static java.util.HashMap`                           | `readGeometryFromDB``(java.sql.Connection conn, java.lang.String tableName, java.lang.String geomColumnName, java.lang.String keyColumnName, java.lang.String[] keyIDArray)`<br>Returns Geometry from DB table in a HashaMap                                                                                                                                                                           |
    | `static java.lang.Object`                            | `readJavaObject``(java.sql.Connection conn, java.lang.String name)`<br>Reads in the given Java object from the database to memory                                                                                                                                                                                                                                                                      |
    | `static `[`Network`](Network.md)                     | `readNetwork``(java.sql.Connection conn, java.lang.String networkName)`<br>Returns the read-only network from the database.                                                                                                                                                                                                                                                                            |
    | `static `[`Network`](Network.md)                     | `readNetwork``(java.sql.Connection conn, java.lang.String networkName, boolean readForUpdate)`<br>Returns the network from the database.                                                                                                                                                                                                                                                               |
    | `static `[`Network`](Network.md)                     | `readNetwork``(java.sql.Connection conn, java.lang.String networkName, boolean readForUpdate, `[`UserDataIO`](UserDataIO.md)` ioFunction, java.lang.String sqlNodeFilter, java.lang.String sqlLinkFilter, java.lang.String sqlPathFilter)`<br>Returns the network with regard to the given filters.                                                                                                    |
    | `static `[`Network`](Network.md)                     | `readNetwork``(java.sql.Connection conn, java.lang.String networkName, boolean readForUpdate, `[`UserDataIO`](UserDataIO.md)` ioFunction, java.lang.String sqlNodeFilter, java.lang.String sqlLinkFilter, java.lang.String sqlPathFilter, boolean linksWithinNodeSet)`<br>Returns the network with regard to the given filters.                                                                        |
    | `static `[`Network`](Network.md)                     | `readNetwork``(java.sql.Connection conn, java.lang.String networkName, int linkLevel, boolean readForUpdate)`<br>Returns the network with the specified link level.                                                                                                                                                                                                                                    |
    | `static `[`Network`](Network.md)                     | `readNetwork``(java.sql.Connection conn, java.lang.String networkName, int linkLevel, boolean readForUpdate, `[`UserDataIO`](UserDataIO.md)` ioFunction)`<br>Returns the network with the specified link level.                                                                                                                                                                                        |
    | `static `[`Network`](Network.md)                     | `readNetwork``(java.sql.Connection conn, java.lang.String networkName, `[`MBR`](MBR.md)` mbr, boolean readForUpdate)`<br>Returns the network that is inside the specified MBR.                                                                                                                                                                                                                         |
    | `static `[`Network`](Network.md)                     | `readNetwork``(java.sql.Connection conn, java.lang.String networkName, `[`MBR`](MBR.md)` mbr, boolean readForUpdate, `[`UserDataIO`](UserDataIO.md)` ioFunction)`<br>Returns the network that is inside the specified MBR.                                                                                                                                                                             |
    | `static `[`NetworkConstraint`](NetworkConstraint.md) | `readNetworkConstraint``(java.sql.Connection conn, java.lang.String networkConstraintName)`<br>Reads in the given network constraint from the database to memory                                                                                                                                                                                                                                       |
    | `static java.lang.Object`                            | `readNetworkConstraintObject``(java.sql.Connection conn, java.lang.String networkConstraintName)`<br>Reads in the given network constraint from the database to memory                                                                                                                                                                                                                                 |
    | `static java.util.HashMap`                           | `readNetworkConstraints``(java.sql.Connection conn)`<br>Reads in the network constraints owned by the current schema from the database to memory                                                                                                                                                                                                                                                       |
    | `static java.util.HashMap`                           | `readNetworkMetadata``(java.sql.Connection conn)`<br>Returns all network metadata from the database.                                                                                                                                                                                                                                                                                                   |
    | `static `[`NetworkMetadata`](NetworkMetadata.md)     | `readNetworkMetadata``(java.sql.Connection conn, int networkID)`<br>Returns the network metadata from the database by network ID.                                                                                                                                                                                                                                                                      |
    | `static `[`NetworkMetadata`](NetworkMetadata.md)     | `readNetworkMetadata``(java.sql.Connection conn, java.lang.String networkName)`<br>Returns the network metadata from the database by network name.                                                                                                                                                                                                                                                     |
    | `static void`                                        | `registerJavaObject``(java.sql.Connection conn, java.lang.String name, java.lang.String className, java.lang.String directoryName, java.lang.String description, java.lang.String javaInterface)`<br>Register the given Java object into user_sdo_network_java_objects                                                                                                                                 |
    | `static void`                                        | `registerNetworkConstraint``(java.sql.Connection conn, java.lang.String networkConstraintName, java.lang.String className, java.lang.String directoryName, java.lang.String description)`<br>Register the given network constraint into user_sdo_network_constraints                                                                                                                                   |
    | `static void`                                        | `removeNetworkFromCache``(java.lang.String networkName)`<br>Removes a network from the network cahce                                                                                                                                                                                                                                                                                                   |
    | `static `[`SubPath`](SubPath.md)                     | `shortestPath``(`[`Network`](Network.md)` network, int startLinkID, double startPercentage, int endLinkID, double endPercentage, `[`NetworkConstraint`](NetworkConstraint.md)` constraint)`<br>Returns the shortest path as a sub path                                                                                                                                                                 |
    | `static `[`SubPath`](SubPath.md)                     | `shortestPath``(`[`Network`](Network.md)` network, int startLinkID, double startPercentage, int endNodeID, `[`NetworkConstraint`](NetworkConstraint.md)` constraint)`<br>Returns the shortest path as a sub path                                                                                                                                                                                       |
    | `static `[`Path`](Path.md)                           | `shortestPath``(`[`Network`](Network.md)` network, int startNodeID, int goalNodeID)`<br>Returns the shortest path based on the Dijkstra algorithm.                                                                                                                                                                                                                                                     |
    | `static `[`SubPath`](SubPath.md)                     | `shortestPath``(`[`Network`](Network.md)` network, int startNodeID, int endLinkID, double endPercentage, `[`NetworkConstraint`](NetworkConstraint.md)` constraint)`<br>Returns the shortest path as a sub path                                                                                                                                                                                         |
    | `static `[`Path`](Path.md)                           | `shortestPath``(`[`Network`](Network.md)` network, int startNodeID, int goalNodeID, `[`NetworkConstraint`](NetworkConstraint.md)` constraint)`<br>Returns the shortest path based on the Dijkstra algorithm.                                                                                                                                                                                           |
    | `static `[`Path`](Path.md)                           | `shortestPath``(`[`Path`](Path.md)` complexPath, `[`NetworkConstraint`](NetworkConstraint.md)` constraint)`<br>Returns the shortest path based on the Dijkstra algorithm.                                                                                                                                                                                                                              |
    | `static `[`SubPath`](SubPath.md)                     | `shortestPathAStar``(`[`Network`](Network.md)` network, int startLinkID, double startPercentage, int endLinkID, double endPercentage, `[`NetworkConstraint`](NetworkConstraint.md)` constraint)`<br>Returns the shortest path as a sub path using A\* algorithm                                                                                                                                        |
    | `static `[`Path`](Path.md)                           | `shortestPathAStar``(`[`Network`](Network.md)` network, int startNodeID, int goalNodeID)`<br>Returns the shortest path based on the A\* search algorithm.                                                                                                                                                                                                                                              |
    | `static `[`Path`](Path.md)                           | `shortestPathAStar``(`[`Network`](Network.md)` network, int startNodeID, int goalNodeID, `[`NetworkConstraint`](NetworkConstraint.md)` constraint)`<br>Returns the shortest path based on the A\* search algorithm.                                                                                                                                                                                    |
    | `static `[`Path`](Path.md)                           | `shortestPathAStar``(`[`Network`](Network.md)` network, int startNodeID, int goalNodeID, `[`NetworkConstraint`](NetworkConstraint.md)` constraint, `[`AStarCostFunction`](AStarCostFunction.md)` userCostFunction, double searchMultiplier)`<br>Returns the shortest path based on the A\* search algorithm.                                                                                           |
    | `static `[`SubPath`](SubPath.md)                     | `shortestPathDijkstra``(`[`Network`](Network.md)` network, int startLinkID, double startPercentage, int endLinkID, double endPercentage, `[`NetworkConstraint`](NetworkConstraint.md)` constraint)`<br>Returns the shortest path as a sub path using Dijkstra algorithm                                                                                                                                |
    | `static `[`Path`](Path.md)                           | `shortestPathDijkstra``(`[`Network`](Network.md)` network, int startNodeID, int goalNodeID)`<br>Returns the shortest path based on the Dijkstra algorithm.                                                                                                                                                                                                                                             |
    | `static `[`Path`](Path.md)                           | `shortestPathDijkstra``(`[`Network`](Network.md)` network, int startNodeID, int goalNodeID, `[`NetworkConstraint`](NetworkConstraint.md)` constraint)`<br>Returns the shortest path based on the Dijkstra algorithm.                                                                                                                                                                                   |
    | `static `[`Path`](Path.md)                           | `shortestPathDijkstra``(`[`Path`](Path.md)` complexPath, `[`NetworkConstraint`](NetworkConstraint.md)` constraint)`<br>Returns the shortest path based on the Dijkstra algorithm.                                                                                                                                                                                                                      |
    | `static `[`Path`](Path.md)`[]`                       | `shortestPaths``(`[`Network`](Network.md)` network, int startNodeID)`<br>Returns all shortest paths from the given start node based on the Dijkstra algorithm.                                                                                                                                                                                                                                         |
    | `static `[`Path`](Path.md)`[]`                       | `shortestPaths``(`[`Network`](Network.md)` network, int startNodeID, `[`NetworkConstraint`](NetworkConstraint.md)` constraint)`<br>Returns the shortest paths from the specified source node to any other nodes based on the Dijkstra algorithm.                                                                                                                                                       |
    | `static `[`SubPath`](SubPath.md)`[]`                 | `traceIn``(`[`Network`](Network.md)` network, int endLinkID, double endPercentage, double cost, `[`NetworkConstraint`](NetworkConstraint.md)` constraint)`<br>Returns trace in results in an array of SubPath                                                                                                                                                                                          |
    | `static `[`SubPath`](SubPath.md)`[]`                 | `traceIn``(`[`Network`](Network.md)` network, int endNodeID, double cost, `[`NetworkConstraint`](NetworkConstraint.md)` constraint)`<br>Returns trace in results in an array of SubPath                                                                                                                                                                                                                |
    | `static `[`SubPath`](SubPath.md)`[]`                 | `traceOut``(`[`Network`](Network.md)` network, int startLinkID, double startPercentage, double cost, `[`NetworkConstraint`](NetworkConstraint.md)` constraint)`<br>Returns trace out results in an array of SubPath                                                                                                                                                                                    |
    | `static `[`SubPath`](SubPath.md)`[]`                 | `traceOut``(`[`Network`](Network.md)` network, int startNodeID, double cost, `[`NetworkConstraint`](NetworkConstraint.md)` constraint)`<br>Returns trace out results in an array of SubPath                                                                                                                                                                                                            |
    | `static `[`Path`](Path.md)                           | `tspPath``(`[`Network`](Network.md)` network, int[] nodeIDArray, boolean isClosed, boolean useExactCost, `[`NetworkConstraint`](NetworkConstraint.md)` constraint)`<br>Returns a TSP tour.                                                                                                                                                                                                             |
    | `static `[`Path`](Path.md)                           | `tspPath``(`[`Network`](Network.md)` network, int[] nodeIDArray, `[`NetworkConstraint`](NetworkConstraint.md)` constraint)`<br>Returns a TSP tour.                                                                                                                                                                                                                                                     |
    | `static `[`Path`](Path.md)                           | `tspPath``(`[`Node`](Node.md)`[] nodeArray, boolean isClosed, boolean useExactCost, `[`NetworkConstraint`](NetworkConstraint.md)` constraint)`<br>Returns a TSP tour.                                                                                                                                                                                                                                  |
    | `static void`                                        | `updateLinks``(java.sql.Connection conn, `[`Network`](Network.md)` network, int[] linkIDArray)`<br>Updates in-memory links from database                                                                                                                                                                                                                                                               |
    | `static void`                                        | `updateNetworkLinkCost``(java.sql.Connection conn, `[`Network`](Network.md)` network, java.lang.String costTableName, java.lang.String costColumnName)`<br>Updates the cost of all network links with the value of the given cost column in the given table.                                                                                                                                           |
    | `static void`                                        | `updateNetworkNodeCost``(java.sql.Connection conn, `[`Network`](Network.md)` network, java.lang.String costTableName, java.lang.String costColumnName)`<br>Updates the cost of all network node with the value of the given cost column in the given table.                                                                                                                                            |
    | `static void`                                        | `updateNodes``(java.sql.Connection conn, `[`Network`](Network.md)` network, int[] nodeIDArray)`<br>Updates in-memory nodes from database                                                                                                                                                                                                                                                               |
    | `static void`                                        | `updatePaths``(java.sql.Connection conn, `[`Network`](Network.md)` network, int[] pathIDArray)`                                                                                                                                                                                                                                                                                                        |
    | `static void`                                        | `updateSubPaths``(java.sql.Connection conn, `[`Network`](Network.md)` network, int[] subPathIDArray)`                                                                                                                                                                                                                                                                                                  |
    | `static java.lang.String`                            | `validateNetwork``(`[`Network`](Network.md)` network)`<br>Validates the reference relationship of the given network return the validation result as a String                                                                                                                                                                                                                                           |
    | `static java.lang.String`                            | `validateNetworkSchema``(java.sql.Connection conn, java.lang.String networkName)`<br>Validates the network tables and reports any errors if exist.                                                                                                                                                                                                                                                     |
    | `static `[`Path`](Path.md)`[]`                       | `withinCost``(`[`Network`](Network.md)` network, int startNodeID, double cost)`<br>Returns the shortest paths of the nodes that are within the specified cost from the given node.                                                                                                                                                                                                                     |
    | `static `[`Path`](Path.md)`[]`                       | `withinCost``(`[`Network`](Network.md)` network, int startNodeID, double cost, `[`NetworkConstraint`](NetworkConstraint.md)` constraint)`<br>Returns all paths that are within the specified cost.                                                                                                                                                                                                     |
    | `static `[`Path`](Path.md)`[]`                       | `withinReachingCost``(`[`Network`](Network.md)` network, int startNodeID, double cost)`<br>Returns all reaching paths that are within the specified cost.                                                                                                                                                                                                                                              |
    | `static `[`Path`](Path.md)`[]`                       | `withinReachingCost``(`[`Network`](Network.md)` network, int startNodeID, double cost, `[`NetworkConstraint`](NetworkConstraint.md)` constraint)`<br>Returns all reaching paths that are within the specified cost.                                                                                                                                                                                    |
    | `static void`                                        | `writeNetwork``(java.sql.Connection conn, `[`Network`](Network.md)` network)`<br>Writes the network to the database.                                                                                                                                                                                                                                                                                   |
    | `static void`                                        | `writeNetwork``(java.sql.Connection conn, `[`Network`](Network.md)` network, `[`UserDataIO`](UserDataIO.md)` ioFunction)`<br>Writes the network to the database.                                                                                                                                                                                                                                       |
    | `static void`                                        | `writeNetworkMetadata``(java.sql.Connection conn, `[`NetworkMetadata`](NetworkMetadata.md)` metadata)`<br>Writes the network metadata to the database.                                                                                                                                                                                                                                                 |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getVersion

          public static java.lang.String getVersion()

      Returns the version of the SDO networkAdapter.
      Returns:
      adapter version

    <!-- -->

    - #### readNetwork

          public static Network readNetwork(java.sql.Connection conn,
                                            java.lang.String networkName)
                                     throws java.sql.SQLException,
                                            NetworkDataException

      Returns the read-only network from the database.
      Parameters:
      `conn` - the database connection

      `networkName` - the network name

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### readNetwork

          public static Network readNetwork(java.sql.Connection conn,
                                            java.lang.String networkName,
                                            boolean readForUpdate)
                                     throws java.sql.SQLException,
                                            NetworkDataException

      Returns the network from the database.
      Parameters:
      `conn` - the database connection

      `networkName` - the network name

      `readForUpdate` - the update mode if true or the read-only mode if false

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### readNetwork

          public static Network readNetwork(java.sql.Connection conn,
                                            java.lang.String networkName,
                                            MBR mbr,
                                            boolean readForUpdate)
                                     throws java.sql.SQLException,
                                            NetworkDataException

      Returns the network that is inside the specified MBR.
      Parameters:
      `conn` - the database connection

      `networkName` - the network name

      `mbr` - the bounding MBR

      `readForUpdate` - the update mode if true or the read-only mode if false

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### readNetwork

          public static Network readNetwork(java.sql.Connection conn,
                                            java.lang.String networkName,
                                            int linkLevel,
                                            boolean readForUpdate)
                                     throws java.sql.SQLException,
                                            NetworkDataException

      Returns the network with the specified link level.
      Parameters:
      `conn` - the database connection

      `networkName` - the network name

      `linkLevel` - the link level

      `readForUpdate` - the update mode if true, read-only mode otherwise

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### readNetwork

          public static Network readNetwork(java.sql.Connection conn,
                                            java.lang.String networkName,
                                            MBR mbr,
                                            boolean readForUpdate,
                                            UserDataIO ioFunction)
                                     throws java.sql.SQLException,
                                            NetworkDataException

      Returns the network that is inside the specified MBR.
      Parameters:
      `conn` - the database connection

      `networkName` - the network name

      `mbr` - the bounding MBR

      `readForUpdate` - the update mode if true or the read-only mode otherwise

      `ioFunction` - the UserDataIO implementation for reading user data

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### readNetwork

          public static Network readNetwork(java.sql.Connection conn,
                                            java.lang.String networkName,
                                            boolean readForUpdate,
                                            UserDataIO ioFunction,
                                            java.lang.String sqlNodeFilter,
                                            java.lang.String sqlLinkFilter,
                                            java.lang.String sqlPathFilter,
                                            boolean linksWithinNodeSet)
                                     throws java.sql.SQLException,
                                            NetworkDataException

      Returns the network with regard to the given filters.
      Parameters:
      `conn` - the database connection

      `networkName` - the network name

      `readForUpdate` - the update mode if true or the read-only mode otherwise

      `ioFunction` - the UserDataIO implementation for reading user data

      `sqlNodeFilter` - SQL node filter

      `sqlLinkFilter` - SQL link filter

      `sqlPathFilter` - SQL path filter

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### readNetwork

          public static Network readNetwork(java.sql.Connection conn,
                                            java.lang.String networkName,
                                            boolean readForUpdate,
                                            UserDataIO ioFunction,
                                            java.lang.String sqlNodeFilter,
                                            java.lang.String sqlLinkFilter,
                                            java.lang.String sqlPathFilter)
                                     throws java.sql.SQLException,
                                            NetworkDataException

      Returns the network with regard to the given filters.
      Parameters:
      `conn` - the database connection

      `networkName` - the network name

      `readForUpdate` - the update mode if true or the read-only mode otherwise

      `ioFunction` - the UserDataIO implementation for reading user data

      `sqlNodeFilter` - SQL node filter

      `sqlLinkFilter` - SQL link filter

      `sqlPathFilter` - SQL path filter

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### readNetwork

          public static Network readNetwork(java.sql.Connection conn,
                                            java.lang.String networkName,
                                            int linkLevel,
                                            boolean readForUpdate,
                                            UserDataIO ioFunction)
                                     throws java.sql.SQLException,
                                            NetworkDataException

      Returns the network with the specified link level.
      Parameters:
      `conn` - the database connection

      `networkName` - the network name

      `linkLevel` - the link level

      `readForUpdate` - the update mode if true or the read-only mode otherwise

      `ioFunction` - the UserDataIO implementation for reading user data

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### readNetworkMetadata

          public static java.util.HashMap readNetworkMetadata(java.sql.Connection conn)
                                                       throws java.sql.SQLException,
                                                              NetworkDataException

      Returns all network metadata from the database.
      Parameters:
      `conn` - the database connection

      Returns:
      a HashMap with the network names as keys and NetworkMetadata as values

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### readNetworkMetadata

          public static NetworkMetadata readNetworkMetadata(java.sql.Connection conn,
                                                            java.lang.String networkName)
                                                     throws java.sql.SQLException,
                                                            NetworkDataException

      Returns the network metadata from the database by network name.
      Parameters:
      `conn` - the database connection

      `networkName` - the network name

      Returns:
      a NetworkMetadata

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### readNetworkMetadata

          public static NetworkMetadata readNetworkMetadata(java.sql.Connection conn,
                                                            int networkID)
                                                     throws java.sql.SQLException,
                                                            NetworkDataException

      Returns the network metadata from the database by network ID.
      Parameters:
      `conn` - the database connection

      `networkID` - the network name

      Returns:
      NetworkMetadata

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### writeNetworkMetadata

          public static void writeNetworkMetadata(java.sql.Connection conn,
                                                  NetworkMetadata metadata)
                                           throws java.sql.SQLException,
                                                  NetworkDataException

      Writes the network metadata to the database.
      Parameters:
      `conn` - the database connection

      `metadata` - the network metadata

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### writeNetwork

          public static void writeNetwork(java.sql.Connection conn,
                                          Network network)
                                   throws java.sql.SQLException,
                                          NetworkDataException

      Writes the network to the database.
      Parameters:
      `conn` - the database connection

      `network` - the specified network

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### writeNetwork

          public static void writeNetwork(java.sql.Connection conn,
                                          Network network,
                                          UserDataIO ioFunction)
                                   throws java.sql.SQLException,
                                          NetworkDataException

      Writes the network to the database.
      Parameters:
      `conn` - the database connection

      `network` - the specified network

      `ioFunction` - the UserDataIO implementation for writing user data

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### readNetworkConstraints

          public static java.util.HashMap readNetworkConstraints(java.sql.Connection conn)
                                                          throws java.sql.SQLException,
                                                                 NetworkDataException,
                                                                 java.lang.ClassNotFoundException,
                                                                 java.lang.InstantiationException,
                                                                 java.lang.IllegalAccessException

      Reads in the network constraints owned by the current schema from the database to memory
      Parameters:
      `conn` - database connection

      Returns:
      the desired network constraints in a HashMap with constraint name as keys and constraint classes as values

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

      `java.lang.ClassNotFoundException`

      `java.lang.InstantiationException`

      `java.lang.IllegalAccessException`

    <!-- -->

    - #### readNetworkConstraint

          public static NetworkConstraint readNetworkConstraint(java.sql.Connection conn,
                                                                java.lang.String networkConstraintName)
                                                         throws java.sql.SQLException,
                                                                NetworkDataException,
                                                                java.lang.ClassNotFoundException,
                                                                java.lang.InstantiationException,
                                                                java.lang.IllegalAccessException

      Reads in the given network constraint from the database to memory
      Parameters:
      `conn` - database connection

      `networkConstraintName` - the name of the network constraint

      Returns:
      the desired network constraint

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

      `java.lang.ClassNotFoundException`

      `java.lang.InstantiationException`

      `java.lang.IllegalAccessException`

    <!-- -->

    - #### readNetworkConstraintObject

          public static java.lang.Object readNetworkConstraintObject(java.sql.Connection conn,
                                                                     java.lang.String networkConstraintName)
                                                              throws java.sql.SQLException,
                                                                     NetworkDataException,
                                                                     java.lang.ClassNotFoundException,
                                                                     java.lang.InstantiationException,
                                                                     java.lang.IllegalAccessException

      Reads in the given network constraint from the database to memory
      Parameters:
      `conn` - database connection

      `networkConstraintName` - the name of the network constraint

      Returns:
      the desired network constraint

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

      `java.lang.ClassNotFoundException`

      `java.lang.InstantiationException`

      `java.lang.IllegalAccessException`

    <!-- -->

    - #### readJavaObject

          public static java.lang.Object readJavaObject(java.sql.Connection conn,
                                                        java.lang.String name)
                                                 throws java.sql.SQLException,
                                                        NetworkDataException,
                                                        java.lang.ClassNotFoundException,
                                                        java.lang.InstantiationException,
                                                        java.lang.IllegalAccessException

      Reads in the given Java object from the database to memory
      Parameters:
      `conn` - database connection

      `name` - the name of the Java object in user_sdo_network_java_objects

      Returns:
      the desired java object

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

      `java.lang.ClassNotFoundException`

      `java.lang.InstantiationException`

      `java.lang.IllegalAccessException`

    <!-- -->

    - #### registerNetworkConstraint

          public static void registerNetworkConstraint(java.sql.Connection conn,
                                                       java.lang.String networkConstraintName,
                                                       java.lang.String className,
                                                       java.lang.String directoryName,
                                                       java.lang.String description)
                                                throws java.sql.SQLException,
                                                       NetworkDataException

      Register the given network constraint into user_sdo_network_constraints
      Parameters:
      `conn` - database connection

      `networkConstraintName` - constraint name

      `className` - Should be given without suffix ".class"

      `directoryName` - Must be the name of a valid Oracle directory object

      `description` -

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### deregisterNetworkConstraint

          public static void deregisterNetworkConstraint(java.sql.Connection conn,
                                                         java.lang.String networkConstraintName)
                                                  throws java.sql.SQLException,
                                                         NetworkDataException

      Deregister the given constraint from user_sdo_network_constraints
      Parameters:
      `conn` - database connection

      `networkConstraintName` - constraint name

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### registerJavaObject

          public static void registerJavaObject(java.sql.Connection conn,
                                                java.lang.String name,
                                                java.lang.String className,
                                                java.lang.String directoryName,
                                                java.lang.String description,
                                                java.lang.String javaInterface)
                                         throws java.sql.SQLException,
                                                NetworkDataException

      Register the given Java object into user_sdo_network_java_objects
      Parameters:
      `conn` - database connection

      `name` - name of object in user_sdo_network_java_classes

      `className` - Should be given without suffix ".class"

      `directoryName` - Must be the name of a valid Oracle directory object

      `description` - object description

      `javaInterface` - Java interface implemented by this Java object

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### deregisterJavaObject

          public static void deregisterJavaObject(java.sql.Connection conn,
                                                  java.lang.String name)
                                           throws java.sql.SQLException,
                                                  NetworkDataException

      Deregister the given Java object from user_sdo_network_java_objects
      Parameters:
      `conn` - database connection

      `name` - name of object in user_sdo_network_java_classes

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### mcst

          public static Network mcst(Network network)

      Returns the minimum cost spanning tree (Kruskal Algorithm) as a network.
      Parameters:
      `network` - the specified network

    <!-- -->

    - #### mcstLinkArray

          public static Link[] mcstLinkArray(Network network)

      Returns the minimum cost spanning tree (Kruskal Algorithm). as an array of links.
      Parameters:
      `network` - the specified network

    <!-- -->

    - #### isReachable

          public static boolean isReachable(Network network,
                                            int sourceNodeID,
                                            int targetNodeID,
                                            MBR mbr,
                                            int depthLimit)
                                     throws NetworkDataException

      Checks if the source node can reach the target node.
      Parameters:
      `network` - the specified network

      `sourceNodeID` - the source node ID

      `targetNodeID` - the target node ID

      `mbr` - the bounding MBR

      `depthLimit` - the depth limit

      Returns:
      true if reachable or false otherwise

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### isReachable

          public static boolean isReachable(Network network,
                                            int sourceNodeID,
                                            int targetNodeID)
                                     throws NetworkDataException

      Checks if the source node can reach the target node.
      Parameters:
      `network` - the specified network

      `sourceNodeID` - the source node ID

      `targetNodeID` - the target node ID

      Returns:
      true if reachable or false otherwise

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### isReachable

          public static boolean isReachable(Network network,
                                            int sourceNodeID,
                                            int targetNodeID,
                                            NetworkConstraint constraint)
                                     throws NetworkDataException

      Checks if the source node can reach the target node.
      Parameters:
      `network` - the specified network

      `sourceNodeID` - the source node ID

      `targetNodeID` - the target node ID

      `constraint` - the network constraint

      Returns:
      true if reachable or false otherwise

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### findConnectedComponents

          public static int findConnectedComponents(Network network)

      Returns the number of connected components in the network. The component number of each node will be set. The component number can be obtained using getComponentNo() from a node. Nodes that belong to the same component have the same component number. Note this function is not thread safe as it sets the component number of each node.
      Parameters:
      `network` - the specified network

    <!-- -->

    - #### findConnectedComponentVector

          public static java.util.Vector findConnectedComponentVector(Network network)

      Returns connected components of the network in a Vector. The number of connected components is the size of the return Vector. Each connected component is returned as a HashSet containing all nodes in the Vector. Note this function is thread safe and no Node component number will be set.
      Parameters:
      `network` - the specified network

    <!-- -->

    - #### findReachableNodes

          public static Node[] findReachableNodes(Network network,
                                                  int sourceNodeID)
                                           throws NetworkDataException

      Returns all nodes that can be reached from the source node.
      Parameters:
      `network` - the specified network

      `sourceNodeID` - the source node ID

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### findReachableNodes

          public static Node[] findReachableNodes(Network network,
                                                  int sourceNodeID,
                                                  MBR mbr)
                                           throws NetworkDataException

      Returns all nodes that can be reached from the source node.
      Parameters:
      `network` - the specified network

      `sourceNodeID` - the source node ID

      `mbr` - the bounding MBR

      Returns:
      an array of nodes that can be reached

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### findReachableNodes

          public static Node[] findReachableNodes(Network network,
                                                  int sourceNodeID,
                                                  MBR mbr,
                                                  int depthLimit)
                                           throws NetworkDataException

      Returns all nodes that can be reached from the source node.
      Parameters:
      `network` - the specified network

      `sourceNodeID` - the source node ID

      `mbr` - the MBR

      `depthLimit` - the depth limit

      Returns:
      an array of nodes that can be reached

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### findReachableNodes

          public static Node[] findReachableNodes(Network network,
                                                  int sourceNodeID,
                                                  MBR mbr,
                                                  int depthLimit,
                                                  int maxNoOfNodes)
                                           throws NetworkDataException

      Returns all nodes that can be reached from the source node.
      Parameters:
      `network` - the specified network

      `sourceNodeID` - the source node ID

      `mbr` - the MBR

      `depthLimit` - the depth limit

      `maxNoOfNodes` - max. no of nodes returned

      Returns:
      an array of nodes that can be reached

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### findReachableNodes

          public static Node[] findReachableNodes(Network network,
                                                  int sourceNodeID,
                                                  MBR mbr,
                                                  int depthLimit,
                                                  NetworkConstraint constraint,
                                                  int maxNoOfNodes)
                                           throws NetworkDataException

      Returns all nodes that can be reached from the source node.
      Parameters:
      `network` - the specified network

      `sourceNodeID` - the source node ID

      `mbr` - the MBR

      `depthLimit` - the depth limit

      `constraint` - network constraint

      `maxNoOfNodes` - max. no of nodes returned

      Returns:
      an array of nodes that can be reached

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### findReachableNodes

          public static Node[] findReachableNodes(Network network,
                                                  int sourceNodeID,
                                                  NetworkConstraint constraint)
                                           throws NetworkDataException

      Returns all nodes that can be reached from the source node.
      Parameters:
      `network` - the specified network

      `sourceNodeID` - the source node ID

      `constraint` - the network constraint

      Returns:
      an array of nodes that can be reached

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### findReachingNodes

          public static Node[] findReachingNodes(Network network,
                                                 int targetNodeID)
                                          throws NetworkDataException

      Returns all nodes that can reach the target node.
      Parameters:
      `network` - the specified network

      `targetNodeID` - the target node ID

      Returns:
      an array of nodes that can reach the target node

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### findReachingNodes

          public static Node[] findReachingNodes(Network network,
                                                 int targetNodeID,
                                                 MBR mbr)
                                          throws NetworkDataException

      Returns all nodes that can reach the target node.
      Parameters:
      `network` - the specified network

      `targetNodeID` - the target node ID

      `mbr` - the MBR

      Returns:
      an array of nodes that can reach the target node

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### findReachingNodes

          public static Node[] findReachingNodes(Network network,
                                                 int targetNodeID,
                                                 MBR mbr,
                                                 int depthLimit)
                                          throws NetworkDataException

      Returns all nodes that can reach the target node.
      Parameters:
      `network` - the specified network

      `targetNodeID` - the target node ID

      `mbr` - the MBR

      `depthLimit` - the depth limit

      Returns:
      an array of nodes that can reach the target node

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### findReachingNodes

          public static Node[] findReachingNodes(Network network,
                                                 int targetNodeID,
                                                 MBR mbr,
                                                 int depthLimit,
                                                 NetworkConstraint constraint,
                                                 int maxNoOfNodes)
                                          throws NetworkDataException

      Returns all nodes that can reach the target node.
      Parameters:
      `network` - the specified network

      `targetNodeID` - the target node ID

      `mbr` - the MBR

      `depthLimit` - the depth limit

      `constraint` - network constraint

      `maxNoOfNodes` - max. no. of nodes returned

      Returns:
      an array of nodes that can reach the target node

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### findReachingNodes

          public static Node[] findReachingNodes(Network network,
                                                 int targetNodeID,
                                                 NetworkConstraint constraint)
                                          throws NetworkDataException

      Returns all nodes that can reach the target node.
      Parameters:
      `network` - the specified network

      `targetNodeID` - the target node ID

      `constraint` - the network constraint

      Returns:
      an array of nodes that can reach the target node

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### shortestPathAStar

          public static Path shortestPathAStar(Network network,
                                               int startNodeID,
                                               int goalNodeID,
                                               NetworkConstraint constraint,
                                               AStarCostFunction userCostFunction,
                                               double searchMultiplier)
                                        throws NetworkDataException

      Returns the shortest path based on the A\* search algorithm.
      Parameters:
      `network` - the specified network

      `startNodeID` - the start node ID

      `goalNodeID` - the goal node ID

      `constraint` - the network constraint, null if none

      `userCostFunction` - a user-defined A\* heuristic cost function

      `searchMultiplier` - a multiplier that applied to the user cost (default = 1.0)

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### shortestPathAStar

          public static Path shortestPathAStar(Network network,
                                               int startNodeID,
                                               int goalNodeID,
                                               NetworkConstraint constraint)
                                        throws NetworkDataException

      Returns the shortest path based on the A\* search algorithm.
      Parameters:
      `network` - the specified network

      `startNodeID` - the start node ID

      `goalNodeID` - the goal node ID

      `constraint` - the network constraint, null if none

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### shortestPathAStar

          public static SubPath shortestPathAStar(Network network,
                                                  int startLinkID,
                                                  double startPercentage,
                                                  int endLinkID,
                                                  double endPercentage,
                                                  NetworkConstraint constraint)
                                           throws NetworkDataException

      Returns the shortest path as a sub path using A\* algorithm
      Parameters:
      `network` - target network

      `startLinkID` - start link ID

      `startPercentage` - start percentage \[0,1\]

      `endLinkID` - end link ID

      `endPercentage` - end percentage \[0,1\]

      `constraint` - network constraint

      Returns:
      SubPath

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### shortestPathAStar

          public static Path shortestPathAStar(Network network,
                                               int startNodeID,
                                               int goalNodeID)
                                        throws NetworkDataException

      Returns the shortest path based on the A\* search algorithm.
      Parameters:
      `network` - the specified network

      `startNodeID` - the start node ID

      `goalNodeID` - the goal node ID

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### shortestPath

          public static Path shortestPath(Network network,
                                          int startNodeID,
                                          int goalNodeID)
                                   throws NetworkDataException

      Returns the shortest path based on the Dijkstra algorithm.
      Parameters:
      `network` - the specified network

      `startNodeID` - the start node ID

      `goalNodeID` - the goal node ID

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### shortestPath

          public static Path shortestPath(Network network,
                                          int startNodeID,
                                          int goalNodeID,
                                          NetworkConstraint constraint)
                                   throws NetworkDataException

      Returns the shortest path based on the Dijkstra algorithm.
      Parameters:
      `network` - the given network

      `startNodeID` - the start node ID

      `goalNodeID` - the goal node ID

      `constraint` - the network constraint, null if none

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### shortestPath

          public static SubPath shortestPath(Network network,
                                             int startLinkID,
                                             double startPercentage,
                                             int endLinkID,
                                             double endPercentage,
                                             NetworkConstraint constraint)
                                      throws NetworkDataException

      Returns the shortest path as a sub path
      Parameters:
      `network` - target network

      `startLinkID` - start link ID

      `startPercentage` - start percentage \[0,1\]

      `endLinkID` - end link ID

      `endPercentage` - end percentage \[0,1\]

      `constraint` - network constraint

      Returns:
      SubPath

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### shortestPath

          public static SubPath shortestPath(Network network,
                                             int startNodeID,
                                             int endLinkID,
                                             double endPercentage,
                                             NetworkConstraint constraint)
                                      throws NetworkDataException

      Returns the shortest path as a sub path
      Parameters:
      `network` - target network

      `startNodeID` - start node ID

      `endLinkID` - end link ID

      `endPercentage` - end percentage \[0,1\]

      `constraint` - network constraint

      Returns:
      SubPath

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### shortestPath

          public static SubPath shortestPath(Network network,
                                             int startLinkID,
                                             double startPercentage,
                                             int endNodeID,
                                             NetworkConstraint constraint)
                                      throws NetworkDataException

      Returns the shortest path as a sub path
      Parameters:
      `network` - target network

      `startLinkID` - start link ID

      `startPercentage` - start percentage \[0,1\]

      `endNodeID` - end node ID

      `constraint` - network constraint

      Returns:
      SubPath

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### shortestPath

          public static Path shortestPath(Path complexPath,
                                          NetworkConstraint constraint)
                                   throws NetworkDataException

      Returns the shortest path based on the Dijkstra algorithm.
      Parameters:
      `complexPath` - the given complex path

      `constraint` - the network constraint, null if none

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### shortestPathDijkstra

          public static Path shortestPathDijkstra(Network network,
                                                  int startNodeID,
                                                  int goalNodeID,
                                                  NetworkConstraint constraint)
                                           throws NetworkDataException

      Returns the shortest path based on the Dijkstra algorithm.
      Parameters:
      `network` - the given network

      `startNodeID` - the start node ID

      `goalNodeID` - the goal node ID

      `constraint` - the network constraint, null if none

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### shortestPathDijkstra

          public static SubPath shortestPathDijkstra(Network network,
                                                     int startLinkID,
                                                     double startPercentage,
                                                     int endLinkID,
                                                     double endPercentage,
                                                     NetworkConstraint constraint)
                                              throws NetworkDataException

      Returns the shortest path as a sub path using Dijkstra algorithm
      Parameters:
      `network` - target network

      `startLinkID` - start link ID

      `startPercentage` - start percentage \[0,1\]

      `endLinkID` - end link ID

      `endPercentage` - end percentage \[0,1\]

      `constraint` - network constraint

      Returns:
      SubPath

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### shortestPathDijkstra

          public static Path shortestPathDijkstra(Network network,
                                                  int startNodeID,
                                                  int goalNodeID)
                                           throws NetworkDataException

      Returns the shortest path based on the Dijkstra algorithm.
      Parameters:
      `network` - the given network

      `startNodeID` - the start node ID

      `goalNodeID` - the goal node ID

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### shortestPathDijkstra

          public static Path shortestPathDijkstra(Path complexPath,
                                                  NetworkConstraint constraint)
                                           throws NetworkDataException

      Returns the shortest path based on the Dijkstra algorithm.
      Parameters:
      `complexPath` - the given complex path

      `constraint` - the network constraint, null if none

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### shortestPaths

          public static Path[] shortestPaths(Network network,
                                             int startNodeID,
                                             NetworkConstraint constraint)
                                      throws NetworkDataException

      Returns the shortest paths from the specified source node to any other nodes based on the Dijkstra algorithm.
      Parameters:
      `network` - the given network

      `startNodeID` - the start node ID

      `constraint` - the network constraint, null if none

      Returns:
      an array of all shortest paths from given start node

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### shortestPaths

          public static Path[] shortestPaths(Network network,
                                             int startNodeID)
                                      throws NetworkDataException

      Returns all shortest paths from the given start node based on the Dijkstra algorithm.
      Parameters:
      `network` - the given network

      `startNodeID` - the start node ID

      Returns:
      an array of all shortest paths from given start node

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### allPaths

          public static Path[] allPaths(Network network,
                                        int startNodeID,
                                        int goalNodeID,
                                        int depthLimit,
                                        double costLimit,
                                        int noOfSolutions)
                                 throws NetworkDataException

      Returns all paths between the start node and the goal node.
      Parameters:
      `network` - the given network

      `startNodeID` - the start node ID

      `goalNodeID` - the goal node ID

      `depthLimit` - the depth limit

      `costLimit` - the cost limit

      `noOfSolutions` - the number of solutions specified

      Returns:
      an array of all paths from the start node to the goal node

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### allPaths

          public static Path[] allPaths(Network network,
                                        int startNodeID,
                                        int goalNodeID,
                                        NetworkConstraint constraint,
                                        int noOfSolutions)
                                 throws NetworkDataException

      Returns all paths between the start node and the goal node.
      Parameters:
      `network` - the given network

      `startNodeID` - the start node ID

      `goalNodeID` - the goal node ID

      `constraint` - the network constraint

      `noOfSolutions` - the number of solutions specified

      Returns:
      an array of all paths from the start node to the goal node

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### allPaths

          public static Path[] allPaths(Path complexPath,
                                        int depthLimit,
                                        double costLimit,
                                        int noOfSolutions)
                                 throws NetworkDataException

      Returns all paths between the start node and the goal node of the complex path.
      Parameters:
      `complexPath` - the given complex path

      `depthLimit` - the depth limit

      `costLimit` - the cost limit

      Returns:
      an array of all paths from given start node to the goal node

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### withinCost

          public static Path[] withinCost(Network network,
                                          int startNodeID,
                                          double cost,
                                          NetworkConstraint constraint)
                                   throws NetworkDataException

      Returns all paths that are within the specified cost.
      Parameters:
      `network` - the given network

      `startNodeID` - the start node ID

      `cost` - the cost limit

      `constraint` - the network constraint, null if none

      Returns:
      all paths from the start node bound by the given cost

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### withinCost

          public static Path[] withinCost(Network network,
                                          int startNodeID,
                                          double cost)
                                   throws NetworkDataException

      Returns the shortest paths of the nodes that are within the specified cost from the given node.
      Parameters:
      `network` - the given network

      `startNodeID` - the start node ID

      `cost` - the cost limit

      Returns:
      all paths from the start node bound by the given cost

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### withinReachingCost

          public static Path[] withinReachingCost(Network network,
                                                  int startNodeID,
                                                  double cost)
                                           throws NetworkDataException

      Returns all reaching paths that are within the specified cost.
      Parameters:
      `network` - the given network

      `startNodeID` - the start node ID

      `cost` - the cost limit

      Returns:
      all paths from the start node bound by the given cost

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### withinReachingCost

          public static Path[] withinReachingCost(Network network,
                                                  int startNodeID,
                                                  double cost,
                                                  NetworkConstraint constraint)
                                           throws NetworkDataException

      Returns all reaching paths that are within the specified cost.
      Parameters:
      `network` - the given network

      `startNodeID` - the start node ID

      `cost` - the cost limit

      `constraint` - the network constraint, null if none

      Returns:
      all paths from the start node bound by the given cost

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### nearestNeighbors

          public static Path[] nearestNeighbors(Network network,
                                                int startNodeID,
                                                int noOfNeighbors,
                                                NetworkConstraint constraint,
                                                GoalNode goalNodeFilter)
                                         throws NetworkDataException

      Returns the shortest paths of the N nearest neighbors from the specified start node. and goal node filter
      Parameters:
      `network` - the given network

      `startNodeID` - the start node ID

      `noOfNeighbors` - the number of neighbors

      `constraint` - the network constraint

      `goalNodeFilter` - the goal node filter

      Returns:
      an array of paths of the nearest neighbors

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### nearestNeighbors

          public static Path[] nearestNeighbors(Network network,
                                                int startNodeID,
                                                int noOfNeighbors,
                                                NetworkConstraint constraint)
                                         throws NetworkDataException

      Returns the shortest paths of the N nearest neighbors from the start node.
      Parameters:
      `network` - the given network

      `startNodeID` - the start node ID

      `noOfNeighbors` - the number of neighbors

      `constraint` - the network constraint

      Returns:
      an array of paths of the nearest neighbors

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### nearestNeighbors

          public static Path[] nearestNeighbors(Network network,
                                                int startNodeID,
                                                int noOfNeighbors)
                                         throws NetworkDataException

      Returns the shortest paths of the N nearest neighbors from the start node.
      Parameters:
      `network` - the given network

      `startNodeID` - the start node ID

      `noOfNeighbors` - the number of neighbors

      Returns:
      an array of paths of the nearest neighbors

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### nearestReachingNeighbors

          public static Path[] nearestReachingNeighbors(Network network,
                                                        int startNodeID,
                                                        int noOfNeighbors,
                                                        NetworkConstraint constraint,
                                                        GoalNode goalNodeFilter)
                                                 throws NetworkDataException

      Returns the shortest paths of the N nearest reaching neighbors to the specified start node. and goal node filter
      Parameters:
      `network` - the given network

      `startNodeID` - the start node ID

      `noOfNeighbors` - the number of neighbors

      `constraint` - the network constraint

      `goalNodeFilter` - the goal node filter

      Returns:
      an array of paths of the nearest neighbors

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### nearestReachingNeighbors

          public static Path[] nearestReachingNeighbors(Network network,
                                                        int startNodeID,
                                                        int noOfNeighbors,
                                                        GoalNode goalNodeFilter)
                                                 throws NetworkDataException

      Returns the shortest paths of the N nearest reaching neighbors to the specified start node. and goal node filter
      Parameters:
      `network` - the given network

      `startNodeID` - the start node ID

      `noOfNeighbors` - the number of neighbors

      `goalNodeFilter` - the goal node filter

      Returns:
      an array of paths of the nearest neighbors

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### nearestReachingNeighbors

          public static Path[] nearestReachingNeighbors(Network network,
                                                        int startNodeID,
                                                        int noOfNeighbors)
                                                 throws NetworkDataException

      Returns the shortest paths of the N nearest reaching neighbors to the specified start node. and goal node filter
      Parameters:
      `network` - the given network

      `startNodeID` - the start node ID

      `noOfNeighbors` - the number of neighbors

      Returns:
      an array of paths of the nearest neighbors

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### validateNetworkSchema

          public static java.lang.String validateNetworkSchema(java.sql.Connection conn,
                                                               java.lang.String networkName)

      Validates the network tables and reports any errors if exist.
      Returns:
      "TRUE" if no errors, return the specific error message otherwise

    <!-- -->

    - #### networkExists

          public static boolean networkExists(java.sql.Connection conn,
                                              java.lang.String network)
                                       throws java.sql.SQLException

      Checks if the given network exists in the database.
      Parameters:
      `conn` - the database connection

      `networkName` - the network name

      Returns:
      true if network exists, false otherwise

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### dropNetwork

          public static void dropNetwork(java.sql.Connection conn,
                                         java.lang.String network)
                                  throws java.sql.SQLException

      Drops the network from the database.
      Parameters:
      `conn` - the database connection

      `networkName` - the network to be dropped

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### createNetworkHiearchy

          public static void createNetworkHiearchy(Network network,
                                                   int numHierarchy,
                                                   int[] ndNumLevel)
                                            throws NetworkDataException,
                                                   java.sql.SQLException

      Creates a network hiearchy with the given number of levels. This operation stops when the givne number of hierarchy levels has been built or it can not achieve the meaningful reduction of node numbers from one level to the next level. In the latter case, the resultant number of hierarchy levels can be less than the given number of hierarchy levels.
      Parameters:
      `network` - the network whose hierarchy will be built. The assumption is that no hierarchy exists in this network before invoking this function.

      `numHierarchy` - the extra number of hierarchy levels for this network. This number should be greater than one and less than the number o nodes in the given network. Since we assume the original network is at the level 1, after this operation, we will have numHierarchy+1 levels of network hierarchy. specifies the additional numHierarchy levels on top of the original network which is at the level one.

      `ndNumLevel` - the number of nodes specified at each level. Here the node number should decrease with the increase of the level as we assume the original network is at the bottom level, i.e. level 1.

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

      `java.sql.SQLException`

    <!-- -->

    - #### createRefConstraints

          public static void createRefConstraints(java.sql.Connection conn,
                                                  java.lang.String network)
                                           throws java.sql.SQLException

      Creates the referential constraints on the link and the path tables. When the constraints are created, they are enabled by default and can be disabled later.
      Parameters:
      `conn` - the database connection

      `networkName` - the network name

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### enableRefConstraints

          public static void enableRefConstraints(java.sql.Connection conn,
                                                  java.lang.String network)
                                           throws java.sql.SQLException

      Enables the referential constraints on the link and the path tables.
      Parameters:
      `conn` - the database connection

      `networkName` - the network name

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getMaxFlow

          public static long getMaxFlow(Network network,
                                        int sourceNodeID,
                                        int sinkNodeID,
                                        java.util.Vector linkFlowVec)
                                 throws NetworkDataException,
                                        java.io.IOException

      Retunrs the max flow between the source node and the sink node
      Parameters:
      `network` - network to be analyzed

      `sourceNodeID` - source Node ID

      `sinkNodeID` - sink node ID

      `linkFlowVec` - link flow returned in a Vector

      Returns:
      the max. flow

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

      `java.io.IOException`

    <!-- -->

    - #### disableRefConstraints

          public static void disableRefConstraints(java.sql.Connection conn,
                                                   java.lang.String network)
                                            throws java.sql.SQLException

      Disables the referential constraints on the link and the path tables.
      Parameters:
      `conn` - the database connection

      `networkName` - the network name

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### dropRefConstraints

          public static void dropRefConstraints(java.sql.Connection conn,
                                                java.lang.String network)
                                         throws java.sql.SQLException

      Drops the referential constraints on the link and the path tables.
      Parameters:
      `conn` - the database connection

      `networkName` - the network name

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### findMBR

          public static MBR findMBR(Node[] nodeArray,
                                    double expandFactor)

      Returns the MBR of the node array and expanded it by the specified factor.

    <!-- -->

    - #### tspPath

          public static Path tspPath(Network network,
                                     int[] nodeIDArray,
                                     NetworkConstraint constraint)
                              throws NetworkDataException

      Returns a TSP tour.
      Parameters:
      `network` - the specified network

      `nodeIDArray` - an array containing IDs of nodes to be visited

      `constraint` - the network constraint

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### tspPath

          public static Path tspPath(Network network,
                                     int[] nodeIDArray,
                                     boolean isClosed,
                                     boolean useExactCost,
                                     NetworkConstraint constraint)
                              throws NetworkDataException

      Returns a TSP tour.
      Parameters:
      `network` - the specified network

      `nodeIDArray` - an array containing IDs of nodes to be visited

      `isClosed` - is the tour is closed?

      `useExactCost` - if true, use the real cost, use the Cartesian distance otherwise

      `constraint` - the network constraint

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### tspPath

          public static Path tspPath(Node[] nodeArray,
                                     boolean isClosed,
                                     boolean useExactCost,
                                     NetworkConstraint constraint)
                              throws NetworkDataException

      Returns a TSP tour.
      Parameters:
      `nodeArray` - an array containing nodes to be visited

      `isClosed` - is the tour closed?

      `useExactCost` - if true, use the real cost, use the Cartesian distance otherwise

      `constraint` - network constraint

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### findInternalLinks

          public static Link[] findInternalLinks(Node[] nodeArray)

      Returns the internal links of the node array. Internal links are the links that connect the nodes in the specified array

    <!-- -->

    - #### findExternalLinks

          public static Link[] findExternalLinks(Node[] nodeArray1,
                                                 Node[] nodeArray2)

      Returns external links between the two arrays of nodes. External links are the links that connect the nodes in the specified node arrays.

    <!-- -->

    - #### makeSpatial

          public static void makeSpatial(Network network,
                                         java.lang.String nodeGeomColumn,
                                         java.lang.String linkGeomColumn,
                                         java.lang.String pathGeomColumn)

      Convert a logical network to a spatial network Note this only updates the network metadata information
      Parameters:
      `network` - network to be converted

      `nodeGeomColumn` - geometry column name for node table

      `linkGeomColumn` - geometry column name for link table

      `pathGeomColumn` - geometry column name for path table

    <!-- -->

    - #### makeLogical

          public static void makeLogical(Network network)

      Convert a spatial network to a logical network Note this only updates the network metadata information original spatial information remains unahcnged
      Parameters:
      `network` - network to be converted

    <!-- -->

    - #### insertGeomMetadata

          public static void insertGeomMetadata(java.sql.Connection conn,
                                                java.lang.String tableName,
                                                java.lang.String geomColumnName,
                                                int srid,
                                                SDODimArray dimArray)
                                         throws java.sql.SQLException

      Inserts the geometry metadata to the database.
      Parameters:
      `conn` - the database connection

      `tableName` - the geometry table name

      `geomColumnName` - the geometry column name

      `srid` - the SRID

      `dimArray` - the SDODimArray

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getNetworkNameFromID

          public static java.lang.String getNetworkNameFromID(java.sql.Connection conn,
                                                              int networkID)
                                                       throws java.sql.SQLException

      Returns the network name from a given network ID
      Parameters:
      `conn` - the database connection

      `networkID` - the network ID

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getNetworkIDFromName

          public static int getNetworkIDFromName(java.sql.Connection conn,
                                                 java.lang.String networkName)
                                          throws java.sql.SQLException

      Returns the network ID from a given network name
      Parameters:
      `conn` - the database connection

      `networkName` - the network name

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getNetworkNames

          public static java.util.HashMap getNetworkNames(java.sql.Connection conn)
                                                   throws java.sql.SQLException

      Retunrs network names and IDs from the database. The result is in a HashMap with names as keys and IDs as values (Integers)
      Parameters:
      `conn` - the database connection

      Returns:
      a HashMap with network names as keys and IDs as values

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getNetworkIDs

          public static java.util.HashMap getNetworkIDs(java.sql.Connection conn)
                                                 throws java.sql.SQLException

      Retunrs network names and IDs from the database. The result is in a HashMap with IDs as keys (Integers) and names as values
      Parameters:
      `conn` - the database connection

      Returns:
      a HashMap with network IDs as keys and names as values

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### isNetworkPartitioned

          public static boolean isNetworkPartitioned(java.sql.Connection conn,
                                                     java.lang.String networkName)
                                              throws NetworkDataException,
                                                     java.sql.SQLException

      Returns the partition ID of the given node
      Parameters:
      `conn` - database connection

      `networkName` - network name in database

      `nodeID` - given node ID

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

      `java.sql.SQLException`

    <!-- -->

    - #### validateNetwork

          public static java.lang.String validateNetwork(Network network)

      Validates the reference relationship of the given network return the validation result as a String

    <!-- -->

    - #### isNetworkInCache

          public static boolean isNetworkInCache(java.lang.String networkName)

      Checks if a given network is in the cache
      Parameters:
      `networkName` - the given network name

    <!-- -->

    - #### getNetworkFromCache

          public static Network getNetworkFromCache(java.lang.String networkName)

      Gets the network from the network cache if the specified network is not in the cache, null will be returned To add a network in the cache, use Networkmanager.putNetworkToCache(networkname, network)
      Parameters:
      `networkName` - network name

    <!-- -->

    - #### addNetworkToCache

          public static void addNetworkToCache(java.lang.String networkName,
                                               Network network)

      Adds a network in the network cahce
      Parameters:
      `networkName` - network name

      `network` - network to be cached

    <!-- -->

    - #### removeNetworkFromCache

          public static void removeNetworkFromCache(java.lang.String networkName)

      Removes a network from the network cahce
      Parameters:
      `networkName` - network name

    <!-- -->

    - #### getNetworkCacheMap

          public static java.util.HashMap getNetworkCacheMap()

      Returns the network cache as a HashMap with network name (type: String) as keys and networks (type: Network) as values

    <!-- -->

    - #### clearNetworkCache

          public static void clearNetworkCache()

      Clears the network cache

    <!-- -->

    - #### findNodesWithinDegreeBounds

          public static Node[] findNodesWithinDegreeBounds(Network network,
                                                           int degreeType,
                                                           int minDegree,
                                                           int maxDegree)

      Finds nodes with degree within the given degree bounds. Note the result will be sorted accoding to the degree in a decreasing order.
      Parameters:
      `degreeType` - type of node degree, -1 : in-degree, 1: out-degree and 0: degree

      `minDegree` - minmum node degree

      `maxDegree` - maximum node degree

    <!-- -->

    - #### findMaxNodeDegree

          public static int findMaxNodeDegree(Network network,
                                              int degreeType)

      Finds the maximum node degree of the network
      Parameters:
      `degreeType` - type of node degree, -1 : in-degree, 1: out-degree and 0: degree

    <!-- -->

    - #### findMinNodeDegree

          public static int findMinNodeDegree(Network network,
                                              int degreeType)

      Finds the minimum node degree of the network
      Parameters:
      `degreeType` - type of node degree, -1 : in-degree, 1: out-degree and 0: degree

    <!-- -->

    - #### traceOut

          public static SubPath[] traceOut(Network network,
                                           int startNodeID,
                                           double cost,
                                           NetworkConstraint constraint)
                                    throws NetworkDataException

      Returns trace out results in an array of SubPath
      Parameters:
      `network` - target network

      `startNodeID` - start node for trace out

      `cost` - trace out cost limit

      `constraint` - network constraint

      Returns:
      an array of SubPath

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### traceOut

          public static SubPath[] traceOut(Network network,
                                           int startLinkID,
                                           double startPercentage,
                                           double cost,
                                           NetworkConstraint constraint)
                                    throws NetworkDataException

      Returns trace out results in an array of SubPath
      Parameters:
      `network` - target network

      `startLinkID` - start link ID

      `startPercentage` - start percentage \[0,1\]

      `cost` - trace out cost limit

      `constraint` - network constraint

      Returns:
      an array of SubPath

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### traceIn

          public static SubPath[] traceIn(Network network,
                                          int endNodeID,
                                          double cost,
                                          NetworkConstraint constraint)
                                   throws NetworkDataException

      Returns trace in results in an array of SubPath
      Parameters:
      `network` - target network

      `endNodeID` - end node for trace out

      `cost` - trace in cost limit

      `constraint` - network constraint

      Returns:
      an array of SubPath

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### traceIn

          public static SubPath[] traceIn(Network network,
                                          int endLinkID,
                                          double endPercentage,
                                          double cost,
                                          NetworkConstraint constraint)
                                   throws NetworkDataException

      Returns trace in results in an array of SubPath
      Parameters:
      `network` - target network

      `endLinkID` - end link ID

      `endPercentage` - end percentage

      `cost` - trace in cost limit

      `constraint` - network constraint

      Returns:
      an array of SubPath

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### readGeometryFromDB

          public static java.util.HashMap readGeometryFromDB(java.sql.Connection conn,
                                                             java.lang.String tableName,
                                                             java.lang.String geomColumnName,
                                                             java.lang.String keyColumnName,
                                                             java.lang.String[] keyIDArray)
                                                      throws java.sql.SQLException

      Returns Geometry from DB table in a HashaMap
      Parameters:
      `conn` - jdbc connection

      `tableName` - geometry table name

      `geomColumnName` - geometry column name

      `keyColumnName` - key column name

      `keyIDArray` - key IDarray

      Returns:
      HashMap hash map containing key IDs as keys and JGeometry as values

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### updateNodes

          public static void updateNodes(java.sql.Connection conn,
                                         Network network,
                                         int[] nodeIDArray)
                                  throws java.sql.SQLException,
                                         NetworkDataException

      Updates in-memory nodes from database
      Parameters:
      `conn` - jdbc connection

      `network` - target network

      `nodeIDArray` - ID array of the nodes to be updated

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### updateLinks

          public static void updateLinks(java.sql.Connection conn,
                                         Network network,
                                         int[] linkIDArray)
                                  throws java.sql.SQLException,
                                         NetworkDataException

      Updates in-memory links from database
      Parameters:
      `conn` - jdbc connection

      `network` - target network

      `linkIDArray` - ID array of the links to be updated

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### updatePaths

          public static void updatePaths(java.sql.Connection conn,
                                         Network network,
                                         int[] pathIDArray)
                                  throws java.sql.SQLException,
                                         NetworkDataException

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### updateSubPaths

          public static void updateSubPaths(java.sql.Connection conn,
                                            Network network,
                                            int[] subPathIDArray)
                                     throws java.sql.SQLException,
                                            NetworkDataException

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### getPathGeomFromDB

          public JGeometry getPathGeomFromDB(java.sql.Connection conn,
                                             Network network,
                                             Path path,
                                             java.lang.String linkTableName,
                                             java.lang.String linkGeomColumnName,
                                             java.lang.String nodeTableName,
                                             java.lang.String nodeGeomColumnName,
                                             double tolerance)
                                      throws java.sql.SQLException,
                                             NetworkDataException

      Gets/Computes the path geometry based on the geometries of path links and nodes in the database
      Parameters:
      `conn` - jdbc connection

      `network` - target network

      `path` - target path

      `linkTableName` - link table name

      `linkGeomColumnName` - link geometry column name

      `nodeTableName` - node table name

      `nodeGeomColumnName` - node geometry column name

      `tolerance` - tolerance for geometric connectivity

      Returns:
      path geometry

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### updateNetworkLinkCost

          public static void updateNetworkLinkCost(java.sql.Connection conn,
                                                   Network network,
                                                   java.lang.String costTableName,
                                                   java.lang.String costColumnName)
                                            throws java.sql.SQLException,
                                                   NetworkDataException

      Updates the cost of all network links with the value of the given cost column in the given table. This function only updates the cost of the links in the network
      Parameters:
      `conn` - databae connection

      `network` - target network

      `costTableName` - given cost table name. must have LINK_ID as primary key. if null network link table name will be used

      `costColumnName` - given cost column name in the cost table. must be numeric data type

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### updateNetworkNodeCost

          public static void updateNetworkNodeCost(java.sql.Connection conn,
                                                   Network network,
                                                   java.lang.String costTableName,
                                                   java.lang.String costColumnName)
                                            throws java.sql.SQLException,
                                                   NetworkDataException

      Updates the cost of all network node with the value of the given cost column in the given table. This function only updates the cost of the nodes in the network
      Parameters:
      `conn` - databae connection

      `network` - target network

      `costTableName` - given cost table name. must have NODE_ID as primary key. if null network node table name will be used

      `costColumnName` - given cost column name in the cost table. must be of numeric data type

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### convertNetworkBetweenWorkspaces

          public static Network convertNetworkBetweenWorkspaces(java.sql.Connection conn,
                                                                Network sourceNetwork,
                                                                java.lang.String sourceWorkspace,
                                                                java.lang.String sourceSavepoint,
                                                                java.lang.String targetWorkspace,
                                                                java.lang.String targetSavepoint)
                                                         throws java.sql.SQLException,
                                                                NetworkDataException

      Converts the source network into the network in the target workspace and savepoint based on their diffs in a workspace(version-enabled) environment.
      Parameters:
      `conn` - database connection

      `sourceNetwork` - network in (sourceWorkspace,sourceSavepoint)

      `sourceWorkspace` - source workspace

      `sourceSavepoint` - source savepoint, "LATEST" if null

      `targetWorkspace` - target workspace

      `targetSavepoint` - target savepoint, "LATEST" if null

      Returns:
      network in the target workspace and savepoint

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### newPathToDestination

          public static Path newPathToDestination(Network network,
                                                  Path referencePath,
                                                  int newStartNodeID,
                                                  NetworkConstraint constraint)
                                           throws NetworkDataException

      Creates a new path starting from the new start node to the node on the reference path closest to the start node and to the end node of the reference path
      Parameters:
      `network` - target network

      `referencePath` - reference path

      `newStartNodeID` - new start node ID

      `constraint` - constraint

      Returns:
      new path

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

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

- [Prev Class](NetworkFactory.md)
- [Next Class](NetworkMetadata.md)

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
