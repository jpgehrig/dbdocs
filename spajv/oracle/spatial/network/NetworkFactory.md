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

- [Prev Class](NetworkDataException.md)
- [Next Class](NetworkManager.md)

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

## Class NetworkFactory

- java.lang.Object

- - oracle.spatial.network.NetworkFactory

<!-- -->

-

  ------------------------------------------------------------------------



      public class NetworkFactory
      extends java.lang.Object

  This class handles network element creation for Oracle Spatial Network Data Model.

<!-- -->

- - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                                  | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    |----------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static void`                                      | `addBidirectedLinkColumn``(java.sql.Connection conn, `[`Network`](Network.md)` network)`<br>add a bidirected column to the network link table                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static void`                                      | `addColumn``(java.sql.Connection conn, java.lang.String tableName, java.lang.String columnName, java.lang.String columnDataType)`<br>Add a column in a database table                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static void`                                      | `addUserDataSchema``(java.sql.Connection conn, `[`NetworkMetadata`](NetworkMetadata.md)` metadata)`                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static `[`Path`](Path.md)                         | `createComplexPath``(int id, `[`Node`](Node.md)` startNode, `[`Node`](Node.md)` endNode, `[`Link`](Link.md)`[] links)`<br>Creates a complex path with the specified start node and end node                                                                                                                                                                                                                                                                                                                                                               |
    | `static `[`MDPoint`](MDPoint.md)`[]`               | `createConvexHull``(`[`JGeometry`](../geometry/JGeometry.md)` geom)`<br>Creates a convex hull as an array of MDpoint for the specified geometry.                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static `[`MDPoint`](MDPoint.md)`[]`               | `createConvexHull``(`[`MDPoint`](MDPoint.md)`[] points)`<br>Creates the convex hull as an array of MDpoint for the specified array of MDPoints.                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static `[`MDPoint`](MDPoint.md)`[]`               | `createConvexHull``(`[`Network`](Network.md)` network)`<br>Creates the convex hull as an array of MDpoint for the specified network.                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`Network`](Network.md)                   | `createDirectedNetwork``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static `[`GeometryMetadata`](GeometryMetadata.md) | `createGeometryMetadata``(java.lang.String tableName)`<br>Deprecated.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static `[`GeometryMetadata`](GeometryMetadata.md) | `createGeometryMetadata``(java.lang.String owner, java.lang.String tableName)`<br>Creates a geometry metadata.                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static `[`GeometryMetadata`](GeometryMetadata.md) | `createGeometryMetadata``(java.lang.String tableName, java.lang.String geomColumnName, int srid, int noOfDims)`<br>Deprecated.                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static `[`GeometryMetadata`](GeometryMetadata.md) | `createGeometryMetadata``(java.lang.String owner, java.lang.String tableName, java.lang.String geomColumnName, int srid, int noOfDims)`<br>Creates a spatial geometry metadata.                                                                                                                                                                                                                                                                                                                                                                           |
    | `static `[`Link`](Link.md)                         | `createLink``(int id, `[`Network`](Network.md)` network, int startNodeID, int endNodeID, double cost)`<br>Creates a logical network link.                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static `[`Link`](Link.md)                         | `createLink``(int id, `[`Node`](Node.md)` startNode, `[`Node`](Node.md)` endNode, double cost)`<br>Creates a logical network link.                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static `[`Link`](Link.md)                         | `createLink``(int id, java.lang.String name, `[`Node`](Node.md)` startNode, `[`Node`](Node.md)` endNode, double cost)`<br>Creates a logical network link.                                                                                                                                                                                                                                                                                                                                                                                                 |
    | [`JGeometry`](../geometry/JGeometry.md)            | `createLinkGeometry``(int srid, int noOfDims, double[] ordArray)`<br>Returns a link geometry (a linestring JGeometry).                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static void`                                      | `createLinkTable``(java.sql.Connection conn, java.lang.String tableName, java.lang.String geomType, java.lang.String geomColumnName, java.lang.String costColumnName, int noOfHierarchyLevels)`<br>Creates an empty network link table in the database.                                                                                                                                                                                                                                                                                                   |
    | `static `[`Link`](Link.md)                         | `createLogicalLink``(int linkID, java.lang.String linkName, `[`Node`](Node.md)` startNode, `[`Node`](Node.md)` endNode, double cost)`<br>Creates a logical link.                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static `[`Network`](Network.md)                   | `createLogicalNetwork``(java.lang.String networkName, int noOfHierarchyLevels, boolean isDirected)`<br>Creates an empty logical network with the default naming convension: node table name = network_name + "\_NODE\$", link table name = network_name + "\_LINK\$, path table name = network_name + "\_PATH\$", path-link table name = network_name + "PLINK\$", subPath table name = network_name + "SPATH\$", all cost column name = "COST".                                                                                                          |
    | `static `[`Network`](Network.md)                   | `createLogicalNetwork``(java.lang.String networkName, int noOfHierarchyLevels, boolean isDirected, java.lang.String nodeTableName, java.lang.String nodeCostColumn, java.lang.String linkTableName, java.lang.String linkCostColumn, java.lang.String pathTableName, java.lang.String pathLinkTableName)`<br>Creates an empty logical network.                                                                                                                                                                                                            |
    | `static `[`Network`](Network.md)                   | `createLogicalNetwork``(java.lang.String networkName, int noOfHierarchyLevels, boolean isDirected, java.lang.String nodeTableName, java.lang.String nodeCostColumn, java.lang.String linkTableName, java.lang.String linkCostColumn, java.lang.String pathTableName, java.lang.String pathLinkTableName, java.lang.String subPathTableName)`<br>Creates an empty logical network.                                                                                                                                                                         |
    | `static `[`Node`](Node.md)                         | `createLogicalNode``(int nodeID, java.lang.String nodeName)`<br>Creates a logical node.                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static `[`Link`](Link.md)                         | `createLRSLink``(int linkID, java.lang.String linkName, `[`Node`](Node.md)` startNode, `[`Node`](Node.md)` endNode, double cost, int geomID, double startMeasure, double endMeasure, `[`JGeometry`](../geometry/JGeometry.md)` geom)`<br>Creates an LRS geometry link.                                                                                                                                                                                                                                                                                    |
    | `static `[`Network`](Network.md)                   | `createLRSNetwork``(java.lang.String networkName, int noOfHierarchyLevels, boolean isDirected, int srid, int noOfDims, java.lang.String lrsTableName, java.lang.String lrsGeomColumn)`<br>Creates an empty spatial LRS_GEOMETRY network.                                                                                                                                                                                                                                                                                                                  |
    | `static `[`Network`](Network.md)                   | `createLRSNetwork``(java.lang.String networkName, int noOfHierarchyLevels, boolean isDirected, int srid, int noOfDims, java.lang.String nodeTableName, java.lang.String nodeCostColumn, java.lang.String linkTableName, java.lang.String linkCostColumn, java.lang.String lrsTableName, java.lang.String lrsGeomColumn, java.lang.String pathTableName, java.lang.String pathGeomColumn, java.lang.String pathLinkTableName)`<br>Creates an empty spatial LRS_GEOMETRY network.                                                                           |
    | `static `[`Network`](Network.md)                   | `createLRSNetwork``(java.lang.String networkName, int noOfHierarchyLevels, boolean isDirected, int srid, int noOfDims, java.lang.String nodeTableName, java.lang.String nodeCostColumn, java.lang.String linkTableName, java.lang.String linkCostColumn, java.lang.String lrsTableName, java.lang.String lrsGeomColumn, java.lang.String pathTableName, java.lang.String pathGeomColumn, java.lang.String pathLinkTableName, java.lang.String subPathTableName, java.lang.String subPathGeomColumn)`<br>Creates an empty spatial LRS_GEOMETRY network.    |
    | `static `[`Node`](Node.md)                         | `createLRSNode``(int nodeID, java.lang.String nodeName, int geomID, double measure, `[`JGeometry`](../geometry/JGeometry.md)` geom)`<br>Creates an LRS geometry node.                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static void`                                      | `createLRSTable``(java.sql.Connection conn, java.lang.String tableName, java.lang.String geomColumnName)`<br>Creates an empty network LRS table in the database.                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static `[`MBR`](MBR.md)                           | `createMBR``(double[] min, double[] max)`<br>Creates an MBR.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static `[`MBR`](MBR.md)                           | `createMBR``(`[`JGeometry`](../geometry/JGeometry.md)` geom)`<br>Creates an MBR of the specified geometry.                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static `[`MDPoint`](MDPoint.md)                   | `createMDPoint``(double x)`<br>Creates a 1D MDPoint.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`MDPoint`](MDPoint.md)                   | `createMDPoint``(double[] pt)`<br>Creates an MDPoint.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static `[`MDPoint`](MDPoint.md)                   | `createMDPoint``(double x, double y)`<br>Creates a 2D MDPoint.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static `[`MDPoint`](MDPoint.md)                   | `createMDPoint``(double x, double y, double z)`<br>Creates a 3D MDPoint.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static `[`Network`](Network.md)                   | `createNetwork``(`[`Network`](Network.md)` network)`<br>Creates an empty network from the specified network (metadata).                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static void`                                      | `createNetworkTables``(java.sql.Connection conn, `[`Network`](Network.md)` network)`<br>Creates the network tables based on the specified network metadata.                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static `[`Node`](Node.md)                         | `createNode``(int id)`<br>Creates a logical network node.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static `[`Node`](Node.md)                         | `createNode``(int id, double x, double y)`<br>Creates a spatial network node.                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `static `[`Node`](Node.md)                         | `createNode``(int id, java.lang.String name)`<br>Creates a logical network node.                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | [`JGeometry`](../geometry/JGeometry.md)            | `createNodeGeometry``(int srid, int noOfDims, double[] ordArray)`<br>Returns a node point geometry (JGeometry).                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static void`                                      | `createNodeTable``(java.sql.Connection conn, java.lang.String tableName, java.lang.String geomType, java.lang.String geomColumnName, java.lang.String costColumnName, int noOfHierarchyLevels)`<br>Creates an empty network node table in the database.                                                                                                                                                                                                                                                                                                   |
    | `static void`                                      | `createNodeTable``(java.sql.Connection conn, java.lang.String tableName, java.lang.String geomType, java.lang.String geomColumnName, java.lang.String costColumnName, java.lang.String partitionColumnName, int noOfHierarchyLevels)`<br>Creates an empty network node table in the database.                                                                                                                                                                                                                                                             |
    | `static `[`Network`](Network.md)                   | `createPartitionNetwork``(java.sql.Connection conn, java.lang.String networkName, java.lang.String partitionNetworkName)`<br>Returns the partition network with the partitions as nodes and the connections between partitions as links.                                                                                                                                                                                                                                                                                                                  |
    | `static `[`Network`](Network.md)                   | `createPartitionNetwork``(`[`Network`](Network.md)` network, java.lang.String partitionNetworkName)`<br>Returns the partition network with the partitions as nodes and the connections between partitions as links.                                                                                                                                                                                                                                                                                                                                       |
    | `static void`                                      | `createPartitionTable``(java.sql.Connection conn, java.lang.String tableName)`<br>Creates an empty network partition table in the database.                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static `[`Path`](Path.md)                         | `createPath``(int id, `[`Node`](Node.md)` startNode, `[`Node`](Node.md)` endNode, `[`Link`](Link.md)`[] links)`<br>Creates a path with the specified start node and the specified end node.                                                                                                                                                                                                                                                                                                                                                               |
    | `static `[`Path`](Path.md)                         | `createPath``(`[`Node`](Node.md)` startNode, `[`Node`](Node.md)` endNode)`<br>Creates an empty path with the specified start node and end node.                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static `[`Path`](Path.md)                         | `createPath``(`[`Node`](Node.md)` startNode, `[`Node`](Node.md)` endNode, `[`Link`](Link.md)`[] links)`<br>Creates a path with the specified start node and the specified end node.                                                                                                                                                                                                                                                                                                                                                                       |
    | `static void`                                      | `createPathLinkTable``(java.sql.Connection conn, java.lang.String tableName)`<br>Creates an empty network path-link table in the database.                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static void`                                      | `createPathTable``(java.sql.Connection conn, java.lang.String tableName, java.lang.String geomColumnName)`<br>Creates an empty network path table in the database.                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static `[`SDODimArray`](SDODimArray.md)           | `createSDODimArray``(boolean isGeodetic, double lowerBound, double upperBound, double tolerance)`<br>Creates a java 2D SDO_DIM_ARRAY.                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static `[`SDODimArray`](SDODimArray.md)           | `createSDODimArray``(java.lang.String[] dimNames, double[] lowerBounds, double[] upperBounds, double[] tolerances)`<br>Creates a java SDO_DIM_ARRAY.                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`Link`](Link.md)                         | `createSDOLink``(int linkID, java.lang.String linkName, `[`Node`](Node.md)` startNode, `[`Node`](Node.md)` endNode, double cost, double[] ords, int dimNo, int srid)`<br>Creates an SDO geometry link.                                                                                                                                                                                                                                                                                                                                                    |
    | `static `[`Link`](Link.md)                         | `createSDOLink``(int linkID, java.lang.String linkName, `[`Node`](Node.md)` startNode, `[`Node`](Node.md)` endNode, double cost, `[`JGeometry`](../geometry/JGeometry.md)` geom)`<br>Creates an SDO geometry link.                                                                                                                                                                                                                                                                                                                                        |
    | `static `[`Network`](Network.md)                   | `createSDONetwork``(java.lang.String networkName, int noOfHierarchyLevels, boolean isDirected, int srid, int noOfDims)`<br>Creates an empty spatial SDO_GEOMETRY network with the default naming convension: node table name = network_name + "\_NODE\$", link table name = network_name + "\_LINK\$, path table name = network_name + "\_PATH\$", path-link table name = network_name + "PLINK\$", subpath table name = network_name + "\_SPATH\$", all geometry column name = "GEOMETRY" and all cost column name = "COST"                              |
    | `static `[`Network`](Network.md)                   | `createSDONetwork``(java.lang.String networkName, int noOfHierarchyLevels, boolean isDirected, int srid, int noOfDims, java.lang.String nodeTableName, java.lang.String nodeGeomColumn, java.lang.String nodeCostColumn, java.lang.String linkTableName, java.lang.String linkGeomColumn, java.lang.String linkCostColumn, java.lang.String pathTableName, java.lang.String pathGeomColumn, java.lang.String pathLinkTableName)`<br>Creates an empty spatial SDO_GEOMETRY network.                                                                        |
    | `static `[`Network`](Network.md)                   | `createSDONetwork``(java.lang.String networkName, int noOfHierarchyLevels, boolean isDirected, int srid, int noOfDims, java.lang.String nodeTableName, java.lang.String nodeGeomColumn, java.lang.String nodeCostColumn, java.lang.String linkTableName, java.lang.String linkGeomColumn, java.lang.String linkCostColumn, java.lang.String pathTableName, java.lang.String pathGeomColumn, java.lang.String pathLinkTableName, java.lang.String subPathTableName, java.lang.String subPathGeomColumn)`<br>Creates an empty spatial SDO_GEOMETRY network. |
    | `static `[`Node`](Node.md)                         | `createSDONode``(int nodeID, java.lang.String nodeName, double x, double y)`<br>Creates a spatial node (SDO_GEOMETRY with SRID = 0).                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`Node`](Node.md)                         | `createSDONode``(int nodeID, java.lang.String nodeName, double x, double y, int srid)`<br>Creates a spatial node (SDO_GEOMETRY).                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static `[`Path`](Path.md)                         | `createSimplePath``(int id, `[`Node`](Node.md)` startNode, `[`Node`](Node.md)` endNode, `[`Link`](Link.md)`[] links)`<br>Creates a simple path with the specified start node and end node.                                                                                                                                                                                                                                                                                                                                                                |
    | `static `[`SubPath`](SubPath.md)                   | `createSubPath``(int id, `[`Path`](Path.md)` referencePath, int startLinkIndex, double startPercentage, int endLinkIndex, double endPercentage)`<br>Creates a sub path                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static `[`SubPath`](SubPath.md)                   | `createSubPath``(`[`Path`](Path.md)` referencePath, int startLinkIndex, double startPercentage, int endLinkIndex, double endPercentage)`<br>Creates a sub path                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static void`                                      | `createSubPathTable``(java.sql.Connection conn, java.lang.String tableName, java.lang.String geomColumnName)`<br>Creates an empty network subpath table in the database.                                                                                                                                                                                                                                                                                                                                                                                  |
    | `static `[`Tree`](Tree.md)                         | `createTree``(`[`TreeNode`](TreeNode.md)` root)`<br>Creates a tree.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static `[`Tree`](Tree.md)                         | `createTree``(`[`TreeNode`](TreeNode.md)` root, boolean forward)`<br>Creates a tree.                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `static `[`TreeLink`](TreeLink.md)                 | `createTreeLink``(`[`Link`](Link.md)` link)`<br>Creates a tree link containing a regular network link                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `static `[`TreeLink`](TreeLink.md)                 | `createTreeLink``(`[`Link`](Link.md)` link, double startPercentage, double endPercentage)`<br>Creates a tree link containing a partial link                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `static `[`TreeNode`](TreeNode.md)                 | `createTreeNode``(`[`Link`](Link.md)` link, double percentage)`<br>Creates a tree node containg a node on a link                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `static `[`TreeNode`](TreeNode.md)                 | `createTreeNode``(`[`Node`](Node.md)` node)`<br>Creates a tree node containing a regular node                                                                                                                                                                                                                                                                                                                                                                                                                                                             |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### createDirectedNetwork

          public static Network createDirectedNetwork()

    <!-- -->

    - #### createNetwork

          public static Network createNetwork(Network network)

      Creates an empty network from the specified network (metadata).
      Parameters:
      `network` - the specified network

    <!-- -->

    - #### createNode

          public static Node createNode(int id)

      Creates a logical network node.
      Parameters:
      `id` - the node ID

    <!-- -->

    - #### createNode

          public static Node createNode(int id,
                                        java.lang.String name)

      Creates a logical network node.
      Parameters:
      `id` - the node ID

      `name` - node Name

    <!-- -->

    - #### createNode

          public static Node createNode(int id,
                                        double x,
                                        double y)

      Creates a spatial network node.
      Parameters:
      `id` - the node ID

      `x` - the x ordinate

      `y` - the y ordinate

    <!-- -->

    - #### createLink

          public static Link createLink(int id,
                                        java.lang.String name,
                                        Node startNode,
                                        Node endNode,
                                        double cost)

      Creates a logical network link.
      Parameters:
      `id` - the link ID

      `name` - the link name

      `startNode` - the start node

      `endNode` - the end node

      `cost` - the link cost

    <!-- -->

    - #### createLink

          public static Link createLink(int id,
                                        Node startNode,
                                        Node endNode,
                                        double cost)

      Creates a logical network link.
      Parameters:
      `id` - the link ID

      `startNode` - the start node

      `endNode` - the end node

      `cost` - the link cost

    <!-- -->

    - #### createLink

          public static Link createLink(int id,
                                        Network network,
                                        int startNodeID,
                                        int endNodeID,
                                        double cost)
                                 throws NetworkDataException

      Creates a logical network link.
      Parameters:
      `id` - the link ID

      `network` - the specified network

      `startNodeID` - the start node ID

      `endNodeID` - the end node ID

      `cost` - the link cost

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### createPath

          public static Path createPath(Node startNode,
                                        Node endNode)

      Creates an empty path with the specified start node and end node.
      Parameters:
      `startNode` - the start node

      `endNode` - the end node

    <!-- -->

    - #### createSimplePath

          public static Path createSimplePath(int id,
                                              Node startNode,
                                              Node endNode,
                                              Link[] links)
                                       throws NetworkDataException

      Creates a simple path with the specified start node and end node.
      Parameters:
      `id` - the path ID

      `startNode` - the start node

      `endNode` - the end node

      `links` - the array of the path links

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### createComplexPath

          public static Path createComplexPath(int id,
                                               Node startNode,
                                               Node endNode,
                                               Link[] links)
                                        throws NetworkDataException

      Creates a complex path with the specified start node and end node
      Parameters:
      `id` - the path ID

      `startNode` - the start node

      `endNode` - the end node

      `links` - the array of the path links

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### createPath

          public static Path createPath(Node startNode,
                                        Node endNode,
                                        Link[] links)

      Creates a path with the specified start node and the specified end node.
      Parameters:
      `startNode` - the start node

      `endNode` - the end node

      `links` - the array of the path links

    <!-- -->

    - #### createPath

          public static Path createPath(int id,
                                        Node startNode,
                                        Node endNode,
                                        Link[] links)

      Creates a path with the specified start node and the specified end node.
      Parameters:
      `id` - the path ID

      `startNode` - the start node

      `endNode` - the end node

      `links` - the array of the path links

    <!-- -->

    - #### createMBR

          public static MBR createMBR(double[] min,
                                      double[] max)

      Creates an MBR.
      Parameters:
      `min` - the ordinates of low point

      `max` - the ordinates of high point

    <!-- -->

    - #### createMBR

          public static MBR createMBR(JGeometry geom)

      Creates an MBR of the specified geometry.
      Parameters:
      `geom` - the specified geometry

    <!-- -->

    - #### createMDPoint

          public static MDPoint createMDPoint(double[] pt)

      Creates an MDPoint.
      Parameters:
      `pt` - the point ordinates

    <!-- -->

    - #### createMDPoint

          public static MDPoint createMDPoint(double x)

      Creates a 1D MDPoint.
      Parameters:
      `x` - the x ordinate

    <!-- -->

    - #### createMDPoint

          public static MDPoint createMDPoint(double x,
                                              double y)

      Creates a 2D MDPoint.
      Parameters:
      `x` - the x ordinate

      `y` - the y ordinate

    <!-- -->

    - #### createMDPoint

          public static MDPoint createMDPoint(double x,
                                              double y,
                                              double z)

      Creates a 3D MDPoint.
      Parameters:
      `x` - the x ordinate

      `y` - the y ordinate

      `z` - the z ordinate

    <!-- -->

    - #### createConvexHull

          public static MDPoint[] createConvexHull(JGeometry geom)

      Creates a convex hull as an array of MDpoint for the specified geometry.
      Parameters:
      `geom` - the specified geometry

    <!-- -->

    - #### createConvexHull

          public static MDPoint[] createConvexHull(MDPoint[] points)

      Creates the convex hull as an array of MDpoint for the specified array of MDPoints.
      Parameters:
      `points` -

    <!-- -->

    - #### createConvexHull

          public static MDPoint[] createConvexHull(Network network)

      Creates the convex hull as an array of MDpoint for the specified network.
      Parameters:
      `network` - network from which the convex hull is to be created

    <!-- -->

    - #### createGeometryMetadata

          public static GeometryMetadata createGeometryMetadata(java.lang.String tableName)

      Deprecated. 
      Creates a geometry metadata.

    <!-- -->

    - #### createGeometryMetadata

          public static GeometryMetadata createGeometryMetadata(java.lang.String owner,
                                                                java.lang.String tableName)

      Creates a geometry metadata.

    <!-- -->

    - #### createGeometryMetadata

          public static GeometryMetadata createGeometryMetadata(java.lang.String tableName,
                                                                java.lang.String geomColumnName,
                                                                int srid,
                                                                int noOfDims)

      Deprecated. 
      Creates a spatial geometry metadata.
      Parameters:
      `tableName` - the geometry table Name

      `geomColumnName` - the geometry column name

      `srid` - the SRID

      `noOfDims` - the number of dimensions

    <!-- -->

    - #### createGeometryMetadata

          public static GeometryMetadata createGeometryMetadata(java.lang.String owner,
                                                                java.lang.String tableName,
                                                                java.lang.String geomColumnName,
                                                                int srid,
                                                                int noOfDims)

      Creates a spatial geometry metadata.
      Parameters:
      `tableName` - the geometry table Name

      `geomColumnName` - the geometry column name

      `srid` - the SRID

      `noOfDims` - the number of dimensions

    <!-- -->

    - #### createLogicalNetwork

          public static Network createLogicalNetwork(java.lang.String networkName,
                                                     int noOfHierarchyLevels,
                                                     boolean isDirected,
                                                     java.lang.String nodeTableName,
                                                     java.lang.String nodeCostColumn,
                                                     java.lang.String linkTableName,
                                                     java.lang.String linkCostColumn,
                                                     java.lang.String pathTableName,
                                                     java.lang.String pathLinkTableName)

      Creates an empty logical network.
      Parameters:
      `networkName` - the network name

      `noOfHierarchyLevels` - the number of hierarchy levels

      `isDirected` - is the network directed?

      `nodeTableName` - the node table name name

      `nodeCostColumn` - the node cost column

      `linkTableName` - the link table name

      `linkCostColumn` - the link cost column name

      `pathTableName` - the path table name

      `pathLinkTableName` - the path-link table name

    <!-- -->

    - #### createLogicalNetwork

          public static Network createLogicalNetwork(java.lang.String networkName,
                                                     int noOfHierarchyLevels,
                                                     boolean isDirected,
                                                     java.lang.String nodeTableName,
                                                     java.lang.String nodeCostColumn,
                                                     java.lang.String linkTableName,
                                                     java.lang.String linkCostColumn,
                                                     java.lang.String pathTableName,
                                                     java.lang.String pathLinkTableName,
                                                     java.lang.String subPathTableName)

      Creates an empty logical network.
      Parameters:
      `networkName` - the network name

      `noOfHierarchyLevels` - the number of hierarchy levels

      `isDirected` - is the network directed?

      `nodeTableName` - the node table name name

      `nodeCostColumn` - the node cost column

      `linkTableName` - the link table name

      `linkCostColumn` - the link cost column name

      `pathTableName` - the path table name

      `pathLinkTableName` - the path-link table name

      `isComplex` - is this network a complex network that referes to other networks

    <!-- -->

    - #### createLogicalNetwork

          public static Network createLogicalNetwork(java.lang.String networkName,
                                                     int noOfHierarchyLevels,
                                                     boolean isDirected)

      Creates an empty logical network with the default naming convension: node table name = network_name + "\_NODE\$", link table name = network_name + "\_LINK\$, path table name = network_name + "\_PATH\$", path-link table name = network_name + "PLINK\$", subPath table name = network_name + "SPATH\$", all cost column name = "COST".
      Parameters:
      `networkName` - the network name

      `noOfHierarchyLevels` - the number of hierarchy levels

      `isDirected` - is the network directed?

    <!-- -->

    - #### createSDONetwork

          public static Network createSDONetwork(java.lang.String networkName,
                                                 int noOfHierarchyLevels,
                                                 boolean isDirected,
                                                 int srid,
                                                 int noOfDims,
                                                 java.lang.String nodeTableName,
                                                 java.lang.String nodeGeomColumn,
                                                 java.lang.String nodeCostColumn,
                                                 java.lang.String linkTableName,
                                                 java.lang.String linkGeomColumn,
                                                 java.lang.String linkCostColumn,
                                                 java.lang.String pathTableName,
                                                 java.lang.String pathGeomColumn,
                                                 java.lang.String pathLinkTableName)

      Creates an empty spatial SDO_GEOMETRY network.
      Parameters:
      `networkName` - the network name

      `noOfHierarchyLevels` - the number of hierarchy levels

      `isDirected` - is the network directed?

      `srid` - the SRID

      `noOfDims` - the number of dimensions

      `nodeTableName` - the node table name

      `nodeGeomColumn` - the node geometry column name

      `nodeCostColumn` - the node cost column name

      `linkTableName` - the link table name

      `linkGeomColumn` - the link geometry column name

      `linkCostColumn` - the link cost column name

      `pathTableName` - the path table name

      `pathGeomColumn` - the path geometry column name

      `pathLinkTableName` - the path link table name

    <!-- -->

    - #### createSDONetwork

          public static Network createSDONetwork(java.lang.String networkName,
                                                 int noOfHierarchyLevels,
                                                 boolean isDirected,
                                                 int srid,
                                                 int noOfDims,
                                                 java.lang.String nodeTableName,
                                                 java.lang.String nodeGeomColumn,
                                                 java.lang.String nodeCostColumn,
                                                 java.lang.String linkTableName,
                                                 java.lang.String linkGeomColumn,
                                                 java.lang.String linkCostColumn,
                                                 java.lang.String pathTableName,
                                                 java.lang.String pathGeomColumn,
                                                 java.lang.String pathLinkTableName,
                                                 java.lang.String subPathTableName,
                                                 java.lang.String subPathGeomColumn)

      Creates an empty spatial SDO_GEOMETRY network.
      Parameters:
      `networkName` - the network name

      `noOfHierarchyLevels` - the number of hierarchy levels

      `isDirected` - is the network directed?

      `srid` - the SRID

      `noOfDims` - the number of dimensions

      `nodeTableName` - the node table name

      `nodeGeomColumn` - the node geometry column name

      `nodeCostColumn` - the node cost column name

      `linkTableName` - the link table name

      `linkGeomColumn` - the link geometry column name

      `linkCostColumn` - the link cost column name

      `pathTableName` - the path table name

      `pathGeomColumn` - the path geometry column name

      `pathLinkTableName` - the path link table name

      `subPathTableName` - the subpath table name

      `subPathGeomColumn` - the subpath geometry column name

    <!-- -->

    - #### createSDONetwork

          public static Network createSDONetwork(java.lang.String networkName,
                                                 int noOfHierarchyLevels,
                                                 boolean isDirected,
                                                 int srid,
                                                 int noOfDims)

      Creates an empty spatial SDO_GEOMETRY network with the default naming convension: node table name = network_name + "\_NODE\$", link table name = network_name + "\_LINK\$, path table name = network_name + "\_PATH\$", path-link table name = network_name + "PLINK\$", subpath table name = network_name + "\_SPATH\$", all geometry column name = "GEOMETRY" and all cost column name = "COST"
      Parameters:
      `networkName` - the network name

      `noOfHierarchyLevels` - the number of hierarchy levels

      `isDirected` - is the network directed?

      `srid` - the SRID

      `noOfDims` - the number of dimensions

    <!-- -->

    - #### createLRSNetwork

          public static Network createLRSNetwork(java.lang.String networkName,
                                                 int noOfHierarchyLevels,
                                                 boolean isDirected,
                                                 int srid,
                                                 int noOfDims,
                                                 java.lang.String nodeTableName,
                                                 java.lang.String nodeCostColumn,
                                                 java.lang.String linkTableName,
                                                 java.lang.String linkCostColumn,
                                                 java.lang.String lrsTableName,
                                                 java.lang.String lrsGeomColumn,
                                                 java.lang.String pathTableName,
                                                 java.lang.String pathGeomColumn,
                                                 java.lang.String pathLinkTableName,
                                                 java.lang.String subPathTableName,
                                                 java.lang.String subPathGeomColumn)

      Creates an empty spatial LRS_GEOMETRY network.
      Parameters:
      `networkName` - the network name

      `noOfHierarchyLevels` - the number of hierarchy levels

      `isDirected` - is the network directed?

      `srid` - the SRID

      `noOfDims` - the number of dimensions

      `nodeTableName` - the node table name

      `nodeCostColumn` - the node cost column name

      `linkTableName` - the link table name

      `linkCostColumn` - the link cost column name

      `lrsTableName` - the LRS table name

      `lrsGeomColumn` - the LRS geometry column name

      `pathTableName` - the path table name

      `pathGeomColumn` - the path geometry column

      `pathLinkTableName` - the path link table name

      `subPathTableName` - the path table name

      `subPathGeomColumn` - the path geometry column networks

    <!-- -->

    - #### createLRSNetwork

          public static Network createLRSNetwork(java.lang.String networkName,
                                                 int noOfHierarchyLevels,
                                                 boolean isDirected,
                                                 int srid,
                                                 int noOfDims,
                                                 java.lang.String nodeTableName,
                                                 java.lang.String nodeCostColumn,
                                                 java.lang.String linkTableName,
                                                 java.lang.String linkCostColumn,
                                                 java.lang.String lrsTableName,
                                                 java.lang.String lrsGeomColumn,
                                                 java.lang.String pathTableName,
                                                 java.lang.String pathGeomColumn,
                                                 java.lang.String pathLinkTableName)

      Creates an empty spatial LRS_GEOMETRY network.
      Parameters:
      `networkName` - the network name

      `noOfHierarchyLevels` - the number of hierarchy levels

      `isDirected` - is the network directed?

      `srid` - the SRID

      `noOfDims` - the number of dimensions

      `nodeTableName` - the node table name

      `nodeCostColumn` - the node cost column name

      `linkTableName` - the link table name

      `linkCostColumn` - the link cost column name

      `lrsTableName` - the LRS table name

      `lrsGeomColumn` - the LRS geometry column name

      `pathTableName` - the path table name

      `pathGeomColumn` - the path geometry column

      `pathLinkTableName` - the path link table name

    <!-- -->

    - #### createLRSNetwork

          public static Network createLRSNetwork(java.lang.String networkName,
                                                 int noOfHierarchyLevels,
                                                 boolean isDirected,
                                                 int srid,
                                                 int noOfDims,
                                                 java.lang.String lrsTableName,
                                                 java.lang.String lrsGeomColumn)

      Creates an empty spatial LRS_GEOMETRY network.
      Parameters:
      `networkName` - the network name

      `noOfHierarchyLevels` - the number of hierarchy levels

      `isDirected` - is the network directed?

      `srid` - the SRID

      `noOfDims` - the number of dimensions

      `lrsTableName` - the LRS table name

      `lrsGeomColumn` - the LRS geometry column name

    <!-- -->

    - #### createNodeTable

          public static void createNodeTable(java.sql.Connection conn,
                                             java.lang.String tableName,
                                             java.lang.String geomType,
                                             java.lang.String geomColumnName,
                                             java.lang.String costColumnName,
                                             java.lang.String partitionColumnName,
                                             int noOfHierarchyLevels)
                                      throws java.sql.SQLException

      Creates an empty network node table in the database.
      Parameters:
      `conn` - the database connection

      `tableName` - the node table name

      `geomType` - the geometry type: (null \| "SDO_GEOMETRY" \|"LRS_GEOMETRY" \| "TOPO_GEOMETRY"

      `geomColumnName` - the geometry column name

      `costColumnName` - the node cost column

      `partitionColumnName` - the node partition column name

      `noOfHierarchyLevels` - the number of hierarchy levels

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### createNodeTable

          public static void createNodeTable(java.sql.Connection conn,
                                             java.lang.String tableName,
                                             java.lang.String geomType,
                                             java.lang.String geomColumnName,
                                             java.lang.String costColumnName,
                                             int noOfHierarchyLevels)
                                      throws java.sql.SQLException

      Creates an empty network node table in the database.
      Parameters:
      `conn` - the database connection

      `tableName` - the node table name

      `geomType` - the geometry type: (null \| "SDO_GEOMETRY" \|"LRS_GEOMETRY" \| "TOPO_GEOMETRY"

      `geomColumnName` - the geometry column name

      `costColumnName` - the node cost column

      `noOfHierarchyLevels` - the number of hierarchy levels

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### createLinkTable

          public static void createLinkTable(java.sql.Connection conn,
                                             java.lang.String tableName,
                                             java.lang.String geomType,
                                             java.lang.String geomColumnName,
                                             java.lang.String costColumnName,
                                             int noOfHierarchyLevels)
                                      throws java.sql.SQLException

      Creates an empty network link table in the database.
      Parameters:
      `conn` - the database connection

      `tableName` - the link table name

      `geomType` - geometry type: (null \| "SDO_GEOMETRY" \|"LRS_GEOMETRY" \| "TOPO_GEOMETRY"

      `geomColumnName` - the geometry column name

      `costColumnName` - the link cost column name

      `noOfHierarchyLevels` - the number of hierarchy levels

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### createLRSTable

          public static void createLRSTable(java.sql.Connection conn,
                                            java.lang.String tableName,
                                            java.lang.String geomColumnName)
                                     throws java.sql.SQLException

      Creates an empty network LRS table in the database.
      Parameters:
      `conn` - the database connection

      `tableName` - the LRS table name

      `geomColumnName` - the LRS geometry column name

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### createPathTable

          public static void createPathTable(java.sql.Connection conn,
                                             java.lang.String tableName,
                                             java.lang.String geomColumnName)
                                      throws java.sql.SQLException

      Creates an empty network path table in the database.
      Parameters:
      `conn` - the database connection

      `tableName` - the path table name

      `geomColumnName` - the path geometry column name

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### createSubPathTable

          public static void createSubPathTable(java.sql.Connection conn,
                                                java.lang.String tableName,
                                                java.lang.String geomColumnName)
                                         throws java.sql.SQLException

      Creates an empty network subpath table in the database.
      Parameters:
      `conn` - the database connection

      `tableName` - the subpath table name

      `geomColumnName` - the subpath geometry column name

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### createPathLinkTable

          public static void createPathLinkTable(java.sql.Connection conn,
                                                 java.lang.String tableName)
                                          throws java.sql.SQLException

      Creates an empty network path-link table in the database.
      Parameters:
      `conn` - the database connection

      `tableName` - the path-link table name

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### createPartitionTable

          public static void createPartitionTable(java.sql.Connection conn,
                                                  java.lang.String tableName)
                                           throws java.sql.SQLException

      Creates an empty network partition table in the database.
      Parameters:
      `conn` - the database connection

      `tableName` - the partition table name

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### createLogicalNode

          public static Node createLogicalNode(int nodeID,
                                               java.lang.String nodeName)

      Creates a logical node.
      Parameters:
      `nodeID` - the node ID

      `nodeName` - the node name

    <!-- -->

    - #### createSDONode

          public static Node createSDONode(int nodeID,
                                           java.lang.String nodeName,
                                           double x,
                                           double y,
                                           int srid)

      Creates a spatial node (SDO_GEOMETRY).
      Parameters:
      `nodeID` - the node ID

      `nodeName` - the node name

      `x` - the x ordiaate

      `y` - the y ordinate

      `srid` - SRID for the node geometry

    <!-- -->

    - #### createSDONode

          public static Node createSDONode(int nodeID,
                                           java.lang.String nodeName,
                                           double x,
                                           double y)

      Creates a spatial node (SDO_GEOMETRY with SRID = 0).
      Parameters:
      `nodeID` - the node ID

      `nodeName` - the node name

      `x` - the x ordiaate

      `y` - the y ordinate

    <!-- -->

    - #### createLRSNode

          public static Node createLRSNode(int nodeID,
                                           java.lang.String nodeName,
                                           int geomID,
                                           double measure,
                                           JGeometry geom)

      Creates an LRS geometry node.
      Parameters:
      `nodeID` - the node ID

      `nodeName` - the node name

      `geomID` - the LRS geometry ID

      `measure` - the LRS node measure

      `geom` - the node geometry

    <!-- -->

    - #### createLogicalLink

          public static Link createLogicalLink(int linkID,
                                               java.lang.String linkName,
                                               Node startNode,
                                               Node endNode,
                                               double cost)

      Creates a logical link.
      Parameters:
      `linkID` - the link ID

      `linkName` - the link name

      `startNode` - the start node

      `endNode` - the end node

      `cost` - the link cost

    <!-- -->

    - #### createSDOLink

          public static Link createSDOLink(int linkID,
                                           java.lang.String linkName,
                                           Node startNode,
                                           Node endNode,
                                           double cost,
                                           double[] ords,
                                           int dimNo,
                                           int srid)

      Creates an SDO geometry link.
      Parameters:
      `linkID` - the link ID

      `linkName` - the link name

      `startNode` - the start node

      `endNode` - the end node

      `cost` - the link cost

      `ords` - the geometry odrinates

      `dimNo` - the number of dimensions

      `srid` - the SRID

    <!-- -->

    - #### createSDOLink

          public static Link createSDOLink(int linkID,
                                           java.lang.String linkName,
                                           Node startNode,
                                           Node endNode,
                                           double cost,
                                           JGeometry geom)

      Creates an SDO geometry link.
      Parameters:
      `linkID` - the link ID

      `linkName` - the link name

      `startNode` - the start node

      `endNode` - the end node

      `cost` - the link cost

      `geom` - the link geometry

    <!-- -->

    - #### createLRSLink

          public static Link createLRSLink(int linkID,
                                           java.lang.String linkName,
                                           Node startNode,
                                           Node endNode,
                                           double cost,
                                           int geomID,
                                           double startMeasure,
                                           double endMeasure,
                                           JGeometry geom)

      Creates an LRS geometry link.
      Parameters:
      `linkID` - the link ID

      `linkName` - the link name

      `startNode` - the start node

      `endNode` - the end node

      `cost` - the link cost

      `geom` - the link geometry

      `geomID` - the LRS geometry ID

      `startMeasure` - the LRS start measure

      `endMeasure` - the LRS end measure

    <!-- -->

    - #### createNetworkTables

          public static void createNetworkTables(java.sql.Connection conn,
                                                 Network network)
                                          throws java.sql.SQLException,
                                                 NetworkDataException

      Creates the network tables based on the specified network metadata. The following tables will be created: node table, link table, path table and path-link table (if specified)
      Parameters:
      `conn` - the database connection

      `network` - the specified network

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### createSDODimArray

          public static SDODimArray createSDODimArray(java.lang.String[] dimNames,
                                                      double[] lowerBounds,
                                                      double[] upperBounds,
                                                      double[] tolerances)

      Creates a java SDO_DIM_ARRAY.
      Parameters:
      `dimNames` - the dimension names

      `lowerBounds` - the lower bounds

      `upperBounds` - the upper bounds

      `tolerances` - the tolerances

    <!-- -->

    - #### createSDODimArray

          public static SDODimArray createSDODimArray(boolean isGeodetic,
                                                      double lowerBound,
                                                      double upperBound,
                                                      double tolerance)

      Creates a java 2D SDO_DIM_ARRAY.
      Parameters:
      `isGeodetic` - is it in a geodetic coordinate (lat., lon.)?

      `lowerBound` - the lower bound

      `upperBound` - the upper bound

      `tolerance` - the tolerance

    <!-- -->

    - #### createNodeGeometry

          public JGeometry createNodeGeometry(int srid,
                                              int noOfDims,
                                              double[] ordArray)

      Returns a node point geometry (JGeometry).
      Parameters:
      `srid` - the SRID

      `noOfDims` - the number of dimensions

      `ordArray` - the ordinate array of the point geometry

    <!-- -->

    - #### createLinkGeometry

          public JGeometry createLinkGeometry(int srid,
                                              int noOfDims,
                                              double[] ordArray)

      Returns a link geometry (a linestring JGeometry).
      Parameters:
      `srid` - the SRID

      `noOfDims` - the number of the dimensions

      `ordArray` - the ordinate array of the link geometry(x1,y1,....xn,yn)

    <!-- -->

    - #### createPartitionNetwork

          public static Network createPartitionNetwork(java.sql.Connection conn,
                                                       java.lang.String networkName,
                                                       java.lang.String partitionNetworkName)
                                                throws java.sql.SQLException,
                                                       NetworkDataException

      Returns the partition network with the partitions as nodes and the connections between partitions as links. The partition network represents the connection relationship between the partitions of the specified partitioned network
      Parameters:
      `conn` - the database connection

      `networkName` - the network name

      `partitionNetworkName` - the resulting partition network name

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### createPartitionNetwork

          public static Network createPartitionNetwork(Network network,
                                                       java.lang.String partitionNetworkName)
                                                throws NetworkDataException

      Returns the partition network with the partitions as nodes and the connections between partitions as links. The partition network represents the connection relationship between the partitions of the specified partitioned network
      Parameters:
      `network` - the network name

      `partitionNetworkName` - the resulting partition network name

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### addColumn

          public static void addColumn(java.sql.Connection conn,
                                       java.lang.String tableName,
                                       java.lang.String columnName,
                                       java.lang.String columnDataType)
                                throws java.sql.SQLException,
                                       NetworkDataException

      Add a column in a database table
      Parameters:
      `conn` - database connection

      `tableName` - table name

      `columnName` - column name to be added

      `columnDataType` - data type for the column

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### addBidirectedLinkColumn

          public static void addBidirectedLinkColumn(java.sql.Connection conn,
                                                     Network network)
                                              throws java.sql.SQLException,
                                                     NetworkDataException

      add a bidirected column to the network link table
      Parameters:
      `conn` - database connection

      `network` - network object

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### addUserDataSchema

          public static void addUserDataSchema(java.sql.Connection conn,
                                               NetworkMetadata metadata)
                                        throws java.sql.SQLException,
                                               NetworkDataException

      Throws:
      `java.sql.SQLException`

      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### createSubPath

          public static SubPath createSubPath(Path referencePath,
                                              int startLinkIndex,
                                              double startPercentage,
                                              int endLinkIndex,
                                              double endPercentage)
                                       throws NetworkDataException

      Creates a sub path
      Parameters:
      `referencePath` - reference path for the sub path

      `startLinkIndex` - start link index of the sub path \[0,noOfLinks-1\]

      `startPercentage` - end link index of the sub path \[0,noOfLinks-1\]

      `endLinkIndex` - start percentage of the sub path \[0,1\]

      `endPercentage` - end percentage of the sub path \[0,1\]

      Returns:
      SubPath

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### createSubPath

          public static SubPath createSubPath(int id,
                                              Path referencePath,
                                              int startLinkIndex,
                                              double startPercentage,
                                              int endLinkIndex,
                                              double endPercentage)
                                       throws NetworkDataException

      Creates a sub path
      Parameters:
      `id` - subpath ID

      `referencePath` - reference path for the sub path

      `startLinkIndex` - start link index of the sub path \[0,noOfLinks-1\]

      `startPercentage` - end link index of the sub path \[0,noOfLinks-1\]

      `endLinkIndex` - start percentage of the sub path \[0,1\]

      `endPercentage` - end percentage of the sub path \[0,1\]

      Returns:
      SubPath

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### createTree

          public static Tree createTree(TreeNode root,
                                        boolean forward)

      Creates a tree. The tree nodes of a tree can either contain a regular node or a node on a link. The tree links of a tree can contain either a regular link or a partial link. A node on a link is defined by a link and a percentage information. A partial link is defined by a link , a start percentage and an end percentage.
      Parameters:
      `root` - root node of the tree

      `forward` - true if the traverse direction is forward (starting from root), false backward

      Returns:
      Tree

    <!-- -->

    - #### createTree

          public static Tree createTree(TreeNode root)

      Creates a tree. The tree nodes of a tree can either contain a regular node or a node on a link. The tree links of a tree can contain either a regular link or a partial link. A node on a link is defined by a link and a percentage information. A partial link is defined by a link , a start percentage and an end percentage. The traverse direction is forward.
      Parameters:
      `root` - root node of the tree

      Returns:
      Tree

    <!-- -->

    - #### createTreeNode

          public static TreeNode createTreeNode(Node node)

      Creates a tree node containing a regular node
      Parameters:
      `node` - a network node

      Returns:
      TREENode

    <!-- -->

    - #### createTreeNode

          public static TreeNode createTreeNode(Link link,
                                                double percentage)
                                         throws NetworkDataException

      Creates a tree node containg a node on a link
      Parameters:
      `link` - given network link

      `percentage` - percentage information (between 0 and 1)

      Returns:
      TreeNode

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### createTreeLink

          public static TreeLink createTreeLink(Link link)

      Creates a tree link containing a regular network link
      Parameters:
      `link` - network link

      Returns:
      TreeLink

    <!-- -->

    - #### createTreeLink

          public static TreeLink createTreeLink(Link link,
                                                double startPercentage,
                                                double endPercentage)
                                         throws NetworkDataException

      Creates a tree link containing a partial link
      Parameters:
      `link` - the given network link

      `startPercentage` - start percentage of the partial link

      `endPercentage` - end percentage of the partial link

      Returns:
      TreeLink

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

- [Prev Class](NetworkDataException.md)
- [Next Class](NetworkManager.md)

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
