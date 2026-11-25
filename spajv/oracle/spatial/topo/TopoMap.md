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

- [Prev Class](TopoFrame.md)
- [Next Class](TopoPreprocess.md)

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

oracle.spatial.topo

## Class TopoMap

- java.lang.Object

- - oracle.spatial.topo.TopoMap

<!-- -->

-

  ------------------------------------------------------------------------



      public class TopoMap
      extends java.lang.Object

  A `TopoMap` object serves as a smart cache for a database topology. Working through a connection to the database, it stores edges, nodes, and faces and provides methods for adding, changing, and deleting elements while maintaining topological consistency both in the cache and in the underlying database tables via a transaction context. It also provides methods for navigating the cache, accessing the topology database, and validating the topology.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description |
    |-------------------|-----------------------|
    | `static int`      | `BATCH_SIZE`          |
    | `static int`      | `NOID`                |
    | `static int`      | `UNIVERSE_FACE`       |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                                                             |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `TopoMap``(java.sql.Connection con, java.lang.String topoName, int numberOfEdges, int numberOfNodes, int numberOfFaces)`<br>Constructs a TopoMap object with a database Connection object and topology name.                                                                                                                                                            |
    | `TopoMap``(java.sql.Connection con, java.lang.String topoName, int numberOfEdges, int numberOfNodes, int numberOfFaces, `[`TopoPreprocess`](TopoPreprocess.md)` tp)`<br>Constructs a TopoMap object with a database Connection object and topology name, and an object which implements the TopoPreprocess interface for preprocessing on invocation of addXXXX methods |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                         | Method and Description                                                                                                                                                                                                                                                                                                                                                                               |
    |-------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`                                     | `addEdge``(int node1, int node2, `[`Point2DD`](Point2DD.md)`[] coords)`<br>Adds an `Edge` to the topology, making all necessary adjustments to the surrounding topological context.                                                                                                                                                                                                                  |
    | `int`                                     | `addIsolatedNode``(int faceID, `[`Point2DD`](Point2DD.md)` p)`<br>Adds an isolated node inside of a face when the face ID is known.                                                                                                                                                                                                                                                                  |
    | `int`                                     | `addIsolatedNode``(`[`Point2DD`](Point2DD.md)` p)`<br>Adds an isolated node inside of a face when the face ID is not known.                                                                                                                                                                                                                                                                          |
    | `int[]`                                   | `addLinearGeometry``(`[`JGeometry`](../geometry/JGeometry.md)` geom)`<br>Adds a linear (line string) geometry to the topology, inserting edges and nodes as necessary based on the full intersection of the geometry with the edges and nodes in the topology graph.                                                                                                                                 |
    | `int[]`                                   | `addLinearGeometry``(`[`Point2DD`](Point2DD.md)`[] coords)`<br>Adds a linear (line string) geometry to the topology, inserting edges and nodes as necessary based on the full intersection of the geometry with the edges and nodes in the topology graph.                                                                                                                                           |
    | `int`                                     | `addLoop``(int nodeID, `[`Point2DD`](Point2DD.md)`[] coords)`<br>Adds an edge that loops and connects to the same node.                                                                                                                                                                                                                                                                              |
    | `int`                                     | `addNode``(int edgeID, `[`Point2DD`](Point2DD.md)` p, int coordIndex, boolean isNewShapePoint)`<br>Adds a node to an edge, splitting the edge in the process.                                                                                                                                                                                                                                        |
    | `int`                                     | `addPointGeometry``(`[`JGeometry`](../geometry/JGeometry.md)` geom)`<br>Adds a point geometry to the topology.                                                                                                                                                                                                                                                                                       |
    | `int`                                     | `addPointGeometry``(`[`Point2DD`](Point2DD.md)` coord)`<br>Adds a point to the topology.                                                                                                                                                                                                                                                                                                             |
    | `int[]`                                   | `addPolygonGeometry``(`[`JGeometry`](../geometry/JGeometry.md)` geom)`<br>Adds a polygon geometry to the topology, inserting edges and nodes as necessary based on the full intersection of the geometry with the edges and nodes in the topology graph.                                                                                                                                             |
    | `int[]`                                   | `addPolygonGeometry``(`[`Point2DD`](Point2DD.md)`[] coords)`<br>Adds a single polygon geometry to the topology, inserting edges and nodes as necessary based on the full intersection of the polygon with the edges and nodes in the topology graph.                                                                                                                                                 |
    | `void`                                    | `changeEdgeCoords``(int edge, `[`Point2DD`](Point2DD.md)`[] coords)`<br>Replaces the coordinate string for an edge without changing the topological context of the edge.                                                                                                                                                                                                                             |
    | `void`                                    | `changeEdgeCoords``(int edge, `[`Point2DD`](Point2DD.md)`[] coords, java.util.ArrayList<java.lang.Integer> movedIsoNodes, java.util.ArrayList<java.lang.Integer> movedIsoEdges, boolean allowIsoMoves)`<br>Replaces the coordinate string for an edge without changing the topological context of the edge.                                                                                          |
    | `void`                                    | `clearCache``()`<br>Clears all entities from the object cache.                                                                                                                                                                                                                                                                                                                                       |
    | `void`                                    | `clearCacheForNLW``()`<br>Clears all entities from the object cache such that another loadWindow can be loaded witout doing a commit/rollback.                                                                                                                                                                                                                                                       |
    | `void`                                    | `clearPreprocess``()`<br>Clears the preprocessing listener for addXXXX methods                                                                                                                                                                                                                                                                                                                       |
    | `void`                                    | `closeStmt``()`<br>Closes the statement cursor.                                                                                                                                                                                                                                                                                                                                                      |
    | `void`                                    | `commitDB``()`<br>Commits any updates to the database and clears any row locks.                                                                                                                                                                                                                                                                                                                      |
    | `void`                                    | `createEdgeIndex``()`<br>Builds a ram-resident R-tree index for the edge cache.                                                                                                                                                                                                                                                                                                                      |
    | `void`                                    | `createFaceIndex``()`<br>Builds a ram-resident R-tree index for the face cache.                                                                                                                                                                                                                                                                                                                      |
    | `void`                                    | `dispose``()`                                                                                                                                                                                                                                                                                                                                                                                        |
    | `boolean`                                 | `fixFaceMBRs``()`<br>Adjusts the MBRs of any faces in the cache whose instance MBR does not match MBR computed from the edges in the outer boundary of the face.                                                                                                                                                                                                                                     |
    | [`Point2DD`](Point2DD.md)`[]`             | `getCacheBounds``()`<br>Determines the bounds of the data contained in the cache, using the index in the cache; useful for determining plot bounds, for example.                                                                                                                                                                                                                                     |
    | `int`                                     | `getCacheEdgeCount``()`<br>Returns the number of edges in the cache.                                                                                                                                                                                                                                                                                                                                 |
    | `int`                                     | `getCacheFaceCount``()`<br>Returns the number of faces in the cache.                                                                                                                                                                                                                                                                                                                                 |
    | `int`                                     | `getCacheNodeCount``()`<br>Returns the number of nodes in the cache.                                                                                                                                                                                                                                                                                                                                 |
    | `static java.sql.Connection`              | `getConnection``(java.lang.String connectString, java.lang.String userID, java.lang.String passwd)`<br>Static method to build a JDBC Connection object from a connection string, user ID, and password.                                                                                                                                                                                              |
    | `int`                                     | `getContainingFace``(`[`Point2DD`](Point2DD.md)` p)`<br>Overload provides the default behavior of getContaingFace(), that with allow_iso_coincidence false.                                                                                                                                                                                                                                          |
    | `int`                                     | `getContainingFace``(`[`Point2DD`](Point2DD.md)` p, boolean allow_iso_coincidence)`<br>From the faces in the instance cache, determines the one, if any, that contains the test point in its open set.                                                                                                                                                                                               |
    | [`Edge`](Edge.md)                         | `getEdge``(int id)`<br>Returns a reference to an `Edge` object given its logical ID.                                                                                                                                                                                                                                                                                                                 |
    | `java.util.ArrayList`                     | `getEdgeAdditions``()`<br>Provides a list of the edges that have been added in the cache.                                                                                                                                                                                                                                                                                                            |
    | `java.util.ArrayList<java.lang.Integer>`  | `getEdgeChanges``()`<br>Provides a list of the edges that have been changed in the cache.                                                                                                                                                                                                                                                                                                            |
    | `java.util.ArrayList<java.lang.Integer>`  | `getEdgeDeletions``()`<br>Provides a list of the edges that have been marked as deleted in the cache: deleted since the cache topology was loaded from the database, but not yet removed from the database.                                                                                                                                                                                          |
    | `java.util.Iterator<`[`Edge`](Edge.md)`>` | `getEdgeIterator``()`<br>Provides an `Iterator` for traversal of all the `Edge` objects contained in the instance cache.                                                                                                                                                                                                                                                                             |
    | [`Face`](Face.md)                         | `getFace``(int id)`<br>Returns a reference to a `Face` object given its logical ID.                                                                                                                                                                                                                                                                                                                  |
    | `java.util.ArrayList<java.lang.Integer>`  | `getFaceAdditions``()`<br>Provides a list of the faces that have been added in the cache.                                                                                                                                                                                                                                                                                                            |
    | `int[]`                                   | `getFaceBoundary``(int faceID, int option)`<br>Returns an array of edge IDs making up the boundary of a face, with several options                                                                                                                                                                                                                                                                   |
    | `java.util.ArrayList<java.lang.Integer>`  | `getFaceChanges``()`<br>Provides a list of the faces that have been changed in the cache.                                                                                                                                                                                                                                                                                                            |
    | `java.util.ArrayList<java.lang.Integer>`  | `getFaceDeletions``()`<br>Provides a list of the faces that have been marked as deleted in the cache: deleted since the cache topology was loaded from the database, but not yet removed from the database.                                                                                                                                                                                          |
    | `java.util.Iterator<`[`Face`](Face.md)`>` | `getFaceIterator``()`<br>Provides an `Iterator` for traversal of all the `Face` objects contained in the instance cache.                                                                                                                                                                                                                                                                             |
    | `boolean`                                 | `getIsEditable``()`<br>Returns the editing state.                                                                                                                                                                                                                                                                                                                                                    |
    | `int`                                     | `getNearestEdge``(`[`Point2DD`](Point2DD.md)` point)`<br>Returns the ID of the `Edge` object that is nearest to the specified point.                                                                                                                                                                                                                                                                 |
    | `int`                                     | `getNearestEdgeInCache``(`[`Point2DD`](Point2DD.md)` point)`<br>Returns the ID of the `Edge` object that of the edges loaded in the cache is nearest to the specified point.                                                                                                                                                                                                                         |
    | `int`                                     | `getNearestNode``(`[`Point2DD`](Point2DD.md)` point)`<br>Returns the ID of the `Node` object that is nearest to the specified point.                                                                                                                                                                                                                                                                 |
    | `int`                                     | `getNearestNodeInCache``(`[`Point2DD`](Point2DD.md)` p)`<br>Returns the ID of the `Node` object that of the nodes loaded in the cache is nearest to the specified point.                                                                                                                                                                                                                             |
    | [`Node`](Node.md)                         | `getNode``(int id)`<br>Returns a reference to a `Node` object given its logical ID.                                                                                                                                                                                                                                                                                                                  |
    | `java.util.ArrayList`                     | `getNodeAdditions``()`<br>Provides a list of the nodes that have been added in the cache.                                                                                                                                                                                                                                                                                                            |
    | `java.util.ArrayList<java.lang.Integer>`  | `getNodeChanges``()`<br>Provides a list of the nodes that have been changed in the cache.                                                                                                                                                                                                                                                                                                            |
    | `java.util.ArrayList<java.lang.Integer>`  | `getNodeDeletions``()`<br>Provides a list of the nodes that have been marked as deleted in the cache: deleted since the cache topology was loaded from the database, but not yet removed from the database.                                                                                                                                                                                          |
    | `int[]`                                   | `getNodeFaceStar``(int nodeID)`<br>Gets an array of integers representing the IDs of a clockwise enumeration of all the faces adjoining the given node.                                                                                                                                                                                                                                              |
    | `java.util.Iterator<`[`Node`](Node.md)`>` | `getNodeIterator``()`<br>Provides an `Iterator` for traversal of all the `Node` objects contained in the instance cache.                                                                                                                                                                                                                                                                             |
    | `int[]`                                   | `getNodeStar``(int nodeID)`<br>Gets an array of integers representing the IDs of a clockwise enumeration of all the edges connected to the given node.                                                                                                                                                                                                                                               |
    | `int`                                     | `getNodeStarCount``(int nodeID)`<br>Gets a count of the number of edges connected at a node.                                                                                                                                                                                                                                                                                                         |
    | `int`                                     | `getSrid``()`<br>Returns the SRID of the topology.                                                                                                                                                                                                                                                                                                                                                   |
    | [`Point2DD`](Point2DD.md)`[]`             | `getTopologyBounds``()`<br>Determines the bounds of the data contained in the database topology, using the spatial index in the database.                                                                                                                                                                                                                                                            |
    | `int`                                     | `getTopologyEdgeCount``()`<br>Returns the number of edges in the \<topologyName\>\_EDGE\$table.                                                                                                                                                                                                                                                                                                      |
    | `int`                                     | `getTopologyFaceCount``()`<br>Returns the number of faces in the \<topologyName\>\_FACE\$table.                                                                                                                                                                                                                                                                                                      |
    | `int`                                     | `getTopologyNodeCount``()`<br>Returns the number of nodes in the \<topologyName\>\_NODE\$table.                                                                                                                                                                                                                                                                                                      |
    | `java.lang.String`                        | `getTopoName``()`<br>Returns the name of the topology.                                                                                                                                                                                                                                                                                                                                               |
    | `int`                                     | `getTopoTransactionID``()`<br>Returns the topology transaction ID if there is data loaded in the cache for update.                                                                                                                                                                                                                                                                                   |
    | [`Edge`](Edge.md)                         | `loadEdge``(int id)`<br>Loads an edge from the database if the edge is not already in the cache.                                                                                                                                                                                                                                                                                                     |
    | [`Face`](Face.md)                         | `loadFace``(int id)`<br>Loads a face from the database if the face is not already in the cache.                                                                                                                                                                                                                                                                                                      |
    | [`Node`](Node.md)                         | `loadNode``(int id)`<br>Loads a node from the database if the node is not already in the cache.                                                                                                                                                                                                                                                                                                      |
    | `boolean`                                 | `loadTopology``(boolean lockForUpdate)`<br>Loads the entire topology from the database into the instance cache.                                                                                                                                                                                                                                                                                      |
    | `boolean`                                 | `loadTopology``(boolean lockForUpdate, boolean buildIndexes)`<br>Loads the entire topology from the database into the instance cache.                                                                                                                                                                                                                                                                |
    | `boolean`                                 | `loadWindow``(double xMin, double yMin, double xMax, double yMax, boolean lockForUpdate)`<br>Loads a portion of the topology specified by a query window.                                                                                                                                                                                                                                            |
    | `boolean`                                 | `loadWindow``(double xMin, double yMin, double xMax, double yMax, boolean lockForUpdate, boolean buildIndexes)`<br>Loads a portion of the topology specified by a query window.                                                                                                                                                                                                                      |
    | `boolean`                                 | `loadWindow``(double xMin, double yMin, double xMax, double yMax, boolean lockForUpdate, boolean buildIndexes, boolean nextLoadWindow)`<br>Loads a portion of the topology specified by a query window.                                                                                                                                                                                              |
    | `void`                                    | `moveEdge``(int edgeID, int sNodeID, int tNodeID, `[`Point2DD`](Point2DD.md)`[] edgeCoords)`<br>Moves one endpoint of an edge and changes the edge coordinates after checking that no topological changes would be required, other than some possible exceptions.                                                                                                                                    |
    | `void`                                    | `moveEdge``(int edgeID, int sNodeID, int tNodeID, `[`Point2DD`](Point2DD.md)`[] edgeCoords, java.util.ArrayList<java.lang.Integer> movedIsoNodes, java.util.ArrayList<java.lang.Integer> movedIsoEdges, boolean allowIsoMoves)`<br>Moves one endpoint of an edge and changes the edge coordinates after checking that no topological changes would be required, other than some possible exceptions. |
    | `void`                                    | `moveIsolatedNode``(int nodeID, `[`Point2DD`](Point2DD.md)` point)`<br>Moves an isolated node.                                                                                                                                                                                                                                                                                                       |
    | `void`                                    | `moveIsolatedNode``(int nodeID, `[`Point2DD`](Point2DD.md)` point, boolean allowFaceChange)`<br>Moves an isolated node to a new face.                                                                                                                                                                                                                                                                |
    | `void`                                    | `moveIsolatedNode``(int nodeID, `[`Point2DD`](Point2DD.md)` point, int faceID)`<br>Moves an isolated node to a new face.                                                                                                                                                                                                                                                                             |
    | `void`                                    | `moveNode``(int nodeID, `[`Point2DD`](Point2DD.md)`[][] edgesCoords)`<br>Moves a node and its attached edges after checking that no topological changes would be required, except that island edges and nodes may change containing faces.                                                                                                                                                           |
    | `void`                                    | `moveNode``(int nodeID, `[`Point2DD`](Point2DD.md)`[][] edgesCoords, java.util.ArrayList<java.lang.Integer> movedIsoNodes, java.util.ArrayList<java.lang.Integer> movedIsoEdges, boolean allowIsoMoves)`<br>Moves a node and its attached edges after checking that no topological changes would be required.                                                                                        |
    | `void`                                    | `removeEdge``(int edgeID)`<br>Remove an edge, merging faces if there are different faces on each side of the edge.                                                                                                                                                                                                                                                                                   |
    | `void`                                    | `removeNode``(int nodeID)`<br>Removes an isolated node or a node at the joining of two edges, merging the edges into one.                                                                                                                                                                                                                                                                            |
    | `boolean`                                 | `removeObsoleteNodes``()`<br>Removes any nodes in the cache which are connected to two and only two distinct edges, are not assigned to point features, and do not serve as the demarcation between mismatched linear features.                                                                                                                                                                      |
    | `void`                                    | `rollbackDB``()`<br>Rolls back any updates to the database and clears any row locks.                                                                                                                                                                                                                                                                                                                 |
    | `boolean`                                 | `searchEdgeRTree``(double[][] h, java.util.ArrayList a)`<br>Return the list of edges from edgeRtree for the given query MBR.                                                                                                                                                                                                                                                                         |
    | `boolean`                                 | `searchFaceRTree``(double[][] h, java.util.ArrayList a)`<br>Return the list of faces from faceRtree for the given query MBR.                                                                                                                                                                                                                                                                         |
    | `void`                                    | `setPreprocess``(`[`TopoPreprocess`](TopoPreprocess.md)` tp)`<br>Sets the preprocessing listener for addXXXX methods                                                                                                                                                                                                                                                                                 |
    | `double`                                  | `snapToGrid``(double d)`<br>Snaps a single double precision value to the instance grid                                                                                                                                                                                                                                                                                                               |
    | `void`                                    | `snapToGrid``(`[`Point2DD`](Point2DD.md)` p)`<br>Snaps the coordinate pair of the argument Point2DD to the instance grid.                                                                                                                                                                                                                                                                            |
    | `void`                                    | `snapToGrid``(`[`Point2DD`](Point2DD.md)`[] p)`<br>Snaps all the coordinate pairs of the array of Point2DD to the instance grid.                                                                                                                                                                                                                                                                     |
    | `void`                                    | `updateTopology``()`<br>Updates to the database topological changes in the instance.                                                                                                                                                                                                                                                                                                                 |
    | `boolean`                                 | `validateCache``()`<br>Wrapper for validateCache(int level).                                                                                                                                                                                                                                                                                                                                         |
    | `boolean`                                 | `validateCache``(int level)`<br>Performs a topological validation of the cache, checking the consistency of all pointer relationships in the edge/node/face graph.                                                                                                                                                                                                                                   |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### NOID

          public static final int NOID

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### UNIVERSE_FACE

          public static final int UNIVERSE_FACE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### BATCH_SIZE

          public static final int BATCH_SIZE

      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### TopoMap

          public TopoMap(java.sql.Connection con,
                         java.lang.String topoName,
                         int numberOfEdges,
                         int numberOfNodes,
                         int numberOfFaces,
                         TopoPreprocess tp)
                  throws java.sql.SQLException,
                         TopoEntityNotFoundException

      Constructs a TopoMap object with a database Connection object and topology name, and an object which implements the TopoPreprocess interface for preprocessing on invocation of addXXXX methods
      Parameters:
      `con` - an Oracle Connection object (produced, for example, by a call to getConnection() )

      `topoName` - the name of the topology in the database

      `numberOfEdges` - best estimate of the number of edges to be loaded into the object cache at one time. Will not overflow if the estimate is too low.

      `numberOfNodes` - like numberOfEdges; typically there will be half the number of edges

      `numberOfFaces` - like numberOfEdges; typically there will be half the number of edges

      `tp` - An implementation of the TopoPreprocess interface

      Throws:
      `java.sql.SQLException`

      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

    <!-- -->

    - #### TopoMap

          public TopoMap(java.sql.Connection con,
                         java.lang.String topoName,
                         int numberOfEdges,
                         int numberOfNodes,
                         int numberOfFaces)
                  throws java.sql.SQLException,
                         TopoEntityNotFoundException

      Constructs a TopoMap object with a database Connection object and topology name.
      Parameters:
      `con` - an Oracle Connection object (produced, for example, by a call to getConnection() )

      `topoName` - the name of the topology in the database

      `numberOfEdges` - best estimate of the number of edges to be loaded into the object cache at one time. Will not overflow if the estimate is too low.

      `numberOfNodes` - like numberOfEdges; typically there will be half the number of edges

      `numberOfFaces` - like numberOfEdges; typically there will be half the number of edges

      Throws:
      `java.sql.SQLException`

      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

  <!-- -->

  - ### Method Detail

    - #### getConnection

          public static java.sql.Connection getConnection(java.lang.String connectString,
                                                          java.lang.String userID,
                                                          java.lang.String passwd)
                                                   throws java.sql.SQLException,
                                                          java.lang.ClassNotFoundException

      Static method to build a JDBC Connection object from a connection string, user ID, and password. Use it to get a Connection object for the TopoMap constructor.
      Parameters:
      `connectString` - a connection string, for example: "jdbc:oracle:thin:@\<host\>:\<port\>:\<sid\>" - for a thin JDBC driver, or "jdbc:oracle:oci:@\<host\>:\<port\>:\<sid\>" - for a thick JDBC driver

      `userID` - user ID for database

      `passwd` - the password for the user account

      Returns:
      the JDBC connection object

      Throws:
      `java.sql.SQLException` - if cannot get connection from the database

      `java.lang.ClassNotFoundException` - if unable to load the OracleDriver class

    <!-- -->

    - #### snapToGrid

          public void snapToGrid(Point2DD p)

      Snaps the coordinate pair of the argument Point2DD to the instance grid.
      Parameters:
      `p` - the input point

    <!-- -->

    - #### snapToGrid

          public double snapToGrid(double d)

      Snaps a single double precision value to the instance grid
      Parameters:
      `d` - the input double

      Returns:
      the snapped double

    <!-- -->

    - #### snapToGrid

          public void snapToGrid(Point2DD[] p)

      Snaps all the coordinate pairs of the array of Point2DD to the instance grid. Snapping may result in duplicate points. These duplicate points will be removed, and therefore the Point2DD\[\] may not have the same length on return.
      Parameters:
      `p` - the array of points

    <!-- -->

    - #### setPreprocess

          public void setPreprocess(TopoPreprocess tp)

      Sets the preprocessing listener for addXXXX methods
      Parameters:
      `tp` - An object implementing the TopoPreprocess interface

    <!-- -->

    - #### clearPreprocess

          public void clearPreprocess()

      Clears the preprocessing listener for addXXXX methods

    <!-- -->

    - #### getTopologyEdgeCount

          public int getTopologyEdgeCount()
                                   throws java.sql.SQLException

      Returns the number of edges in the \<topologyName\>\_EDGE\$table.
      Returns:
      the edge count

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getCacheEdgeCount

          public int getCacheEdgeCount()

      Returns the number of edges in the cache.
      Returns:
      the edge count

    <!-- -->

    - #### getCacheNodeCount

          public int getCacheNodeCount()

      Returns the number of nodes in the cache.
      Returns:
      the node count

    <!-- -->

    - #### getCacheFaceCount

          public int getCacheFaceCount()

      Returns the number of faces in the cache.
      Returns:
      the face count

    <!-- -->

    - #### getTopologyNodeCount

          public int getTopologyNodeCount()
                                   throws java.sql.SQLException

      Returns the number of nodes in the \<topologyName\>\_NODE\$table.
      Returns:
      the node count

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### getTopologyFaceCount

          public int getTopologyFaceCount()
                                   throws java.sql.SQLException

      Returns the number of faces in the \<topologyName\>\_FACE\$table.
      Returns:
      the face count

      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### createEdgeIndex

          public void createEdgeIndex()
                               throws java.lang.Exception

      Builds a ram-resident R-tree index for the edge cache. A packed tree is built using recursive sorting.
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### createFaceIndex

          public void createFaceIndex()
                               throws java.lang.Exception

      Builds a ram-resident R-tree index for the face cache. A packed tree is built using recursive sorting.
      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### clearCache

          public void clearCache()
                          throws java.sql.SQLException,
                                 InvalidTopoOperationException

      Clears all entities from the object cache. Also clears the record of changed or added entities. If these need to be saved to the database, be sure to call updateTopology() and/or commitDB() first. The cache cannot be cleared if a call to updateTopology() has been made and a call to either rollbackDB() or commitDB() has not been made. rollBackDB() also clears the cache as a side effect, so a call to clearCache() would be superfluous in that case.
      Throws:
      `java.sql.SQLException`

      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

    <!-- -->

    - #### clearCacheForNLW

          public void clearCacheForNLW()
                                throws java.sql.SQLException,
                                       InvalidTopoOperationException

      Clears all entities from the object cache such that another loadWindow can be loaded witout doing a commit/rollback. This is similar to the clearCache except that this is called as pre-step to the next loadWindow call. All the rules of clearCache apply here as well.
      Throws:
      `java.sql.SQLException`

      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

    <!-- -->

    - #### getCacheBounds

          public Point2DD[] getCacheBounds()
                                    throws InvalidTopoOperationException

      Determines the bounds of the data contained in the cache, using the index in the cache; useful for determining plot bounds, for example. The returned window bounds may be larger than the bounds passed to loadWindow() when the cache was loaded because of either or both of the following: (1) ragged retrieval of edges bounding faces that overlap the edit window; (2) other entities that might have been cached by direct calls to loadEdge() or other methods.
      Returns:
      the mbr of all the edge, node, and face entities in the cache as an array of two `Point2DD` objects: \[0\] is the min x,y and \[1\] is max x,y

      Throws:
      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

    <!-- -->

    - #### getTopologyBounds

          public Point2DD[] getTopologyBounds()
                                       throws java.sql.SQLException,
                                              InvalidTopoOperationException

      Determines the bounds of the data contained in the database topology, using the spatial index in the database.
      Returns:
      the mbr of all the edge, node, and face entities in the topology as an array of two `Point2DD` objects: \[0\] is the min x,y and \[1\] is max x,y

      Throws:
      `java.sql.SQLException`

      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

    <!-- -->

    - #### loadWindow

          public boolean loadWindow(double xMin,
                                    double yMin,
                                    double xMax,
                                    double yMax,
                                    boolean lockForUpdate)
                             throws java.sql.SQLException,
                                    TopoEntityNotFoundException,
                                    InvalidTopoOperationException,
                                    java.lang.Exception

      Loads a portion of the topology specified by a query window. Loads all edges, nodes, and faces which intersect the query window. For faces, also loads any edges and isolated nodes on the boundary of the face, even if they do not intersect the query window. This is to ensure that everything is loaded that might be needed or affected by a topological editing operation, or for validation of the data in the window.
      If there is a prior transaction that has been initiated, it must be committed (via commitDB) or rolled back (via rollbackDB) before this method can be called for read-only access, even if the cache has been cleared. The lockForUpdate flag must be true if any edits are to be performed on the data. The client application will be able to delete, modify, or add elements only inside the window specified in the call to this routine. Data cannot be loaded if there is already data loaded. This method automatically builds indexes in the cache for edges and faces.

      Parameters:
      `xMin` - the minimum x-value of the query window

      `yMin` - the minimum y-value of the query window

      `xMax` - the maximum x-value of the query window

      `yMax` - the maximum y-value of the query window

      `lockForUpdate` - set true if you intend to edit inside the window and update the database. The retrieved entities will be locked for update by others.

      Returns:
      true if something was loaded; false otherwise

      Throws:
      `java.sql.SQLException`

      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

      `java.lang.Exception`

    <!-- -->

    - #### loadWindow

          public boolean loadWindow(double xMin,
                                    double yMin,
                                    double xMax,
                                    double yMax,
                                    boolean lockForUpdate,
                                    boolean buildIndexes)
                             throws java.sql.SQLException,
                                    TopoEntityNotFoundException,
                                    InvalidTopoOperationException,
                                    java.lang.Exception

      Loads a portion of the topology specified by a query window. Loads all edges, nodes, and faces which intersect the query window. For faces, also loads any edges and isolated nodes on the boundary of the face even if they do not intersect the query window. Finally, loads the start and end nodes of any edge that has been loaded unless they are already loaded. This is to ensure that everything is loaded that might be needed or affected by a topological editing operation, or for validation of the data in the window.
      If there is a prior transaction that has been initiated, it must be committed (via commitDB) or rolled back (via rollbackDB) before this method can be called for read-only access, even if the cache has been cleared. The lockForUpdate flag must be true if any edits are to be performed on the data. The client application will be able to delete, modify, or add elements only inside the window specified in the call to this routine. Data cannot be loaded if there is already data loaded. At the user's option, the edges and faces can be indexed in the cache.

      Parameters:
      `xMin` - The minimum x-value of the query window

      `yMin` - The minimum y-value of the query window

      `xMax` - The maximum x-value of the query window

      `yMax` - The maximum y-value of the query window

      `lockForUpdate` - set true if you intend to edit inside the window and update the database. The retrieved entities will be locked for update by others.

      `buildIndexes` - set true to auto-build indexes in the cache for edges and faces

      Returns:
      true if something was loaded; false otherwise

      Throws:
      `java.sql.SQLException`

      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

      `java.lang.Exception`

    <!-- -->

    - #### loadWindow

          public boolean loadWindow(double xMin,
                                    double yMin,
                                    double xMax,
                                    double yMax,
                                    boolean lockForUpdate,
                                    boolean buildIndexes,
                                    boolean nextLoadWindow)
                             throws java.sql.SQLException,
                                    TopoEntityNotFoundException,
                                    InvalidTopoOperationException,
                                    java.lang.Exception

      Loads a portion of the topology specified by a query window. Loads all edges, nodes, and faces which intersect the query window. For faces, also loads any edges and isolated nodes on the boundary of the face even if they do not intersect the query window. Finally, loads the start and end nodes of any edge that has been loaded unless they are already loaded. This is to ensure that everything is loaded that might be needed or affected by a topological editing operation, or for validation of the data in the window.
      If there is a prior transaction that has been initiated, this loadWindow method will continue that txn, provided a updateTopology() is issued before calling this method. The lockForUpdate flag must be true if any edits are to be performed on the data. The client application will be able to delete, modify, or add elements only inside the window specified in the call to this routine. Data cannot be loaded if there is already data loaded. At the user's option, the edges and faces can be indexed in the cache.

      Parameters:
      `xMin` - The minimum x-value of the query window

      `yMin` - The minimum y-value of the query window

      `xMax` - The maximum x-value of the query window

      `yMax` - The maximum y-value of the query window

      `lockForUpdate` - set true if you intend to edit inside the window and update the database. The retrieved entities will be locked for update by others.

      `buildIndexes` - set true to auto-build indexes in the cache for edges and faces

      `nextLoadWindow` - set true if this is not the first loadWindow in a sequence of loadWindow operations

      Returns:
      true if something was loaded; false otherwise

      Throws:
      `java.sql.SQLException`

      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

      `java.lang.Exception`

    <!-- -->

    - #### loadTopology

          public boolean loadTopology(boolean lockForUpdate)
                               throws java.sql.SQLException,
                                      InvalidTopoOperationException,
                                      TopoEntityNotFoundException,
                                      java.lang.Exception

      Loads the entire topology from the database into the instance cache. If there is a prior transaction that has been initiated, it must be committed (via commitDB) or rolled back (via rollbackDB) before this method can be called for read-only access, even if the cache has been cleared. Data cannot be loaded if there is data already in the cache. This method will auto-build R-tree indexes for edges and faces
      Parameters:
      `lockForUpdate` - whether the data is loaded read-only (false) or for editing (true).

      Returns:
      true if anything was loaded; false otherwise

      Throws:
      `java.sql.SQLException`

      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      `java.lang.Exception`

    <!-- -->

    - #### loadTopology

          public boolean loadTopology(boolean lockForUpdate,
                                      boolean buildIndexes)
                               throws java.sql.SQLException,
                                      InvalidTopoOperationException,
                                      TopoEntityNotFoundException,
                                      java.lang.Exception

      Loads the entire topology from the database into the instance cache. If there is a prior transaction that has been initiated, it must be committed (via commitDB) or rolled back (via rollbackDB) before this method can be called for read-only access, even if the cache has been cleared. Data cannot be loaded if there is data already in the cache. At the user's option, indexes can be built for edges and nodes in the cache.
      Parameters:
      `lockForUpdate` - whether the data is loaded read-only (false) or for editing (true).

      `buildIndexes` - whether (true) or not (false) to build edge and face indexes

      Returns:
      true if anything was loaded; false otherwise

      Throws:
      `java.sql.SQLException`

      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      `java.lang.Exception`

    <!-- -->

    - #### updateTopology

          public void updateTopology()
                              throws java.sql.SQLException,
                                     TopoEntityNotFoundException,
                                     TopoValidationException,
                                     java.lang.Exception

      Updates to the database topological changes in the instance. Database changes are NOT committed by this method and locks are still active. The window of data is still editable, but nothing remains on the lists of added, changed, and deleted entities.
      If the data has not been validated (via a call to validateCache(0) ) since anything was changed, a call to validateCache(0) is made implicitly by this method before updating the database. If any exception except a TopoValidationException is raised, the connection is rolled back (which clears the cache implicitly) before the exception is rethrown.

      Throws:
      `java.sql.SQLException`

      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      [`TopoValidationException`](TopoValidationException.md)

      `java.lang.Exception`

    <!-- -->

    - #### commitDB

          public void commitDB()
                        throws java.sql.SQLException,
                               TopoEntityNotFoundException,
                               TopoValidationException,
                               java.lang.Exception

      Commits any updates to the database and clears any row locks. Implicitly calls updateTopology to flush any changed or added entities from the cache to the database. The data in the cache is set uneditable since there are no more database locks.
      Throws:
      `java.sql.SQLException`

      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      [`TopoValidationException`](TopoValidationException.md)

      `java.lang.Exception`

    <!-- -->

    - #### rollbackDB

          public void rollbackDB()
                          throws java.sql.SQLException

      Rolls back any updates to the database and clears any row locks. The data in the cache is also cleared.
      Throws:
      `java.sql.SQLException`

    <!-- -->

    - #### searchEdgeRTree

          public boolean searchEdgeRTree(double[][] h,
                                         java.util.ArrayList a)

      Return the list of edges from edgeRtree for the given query MBR.
      Parameters:
      `h` - two dimensional array of doubles which are the minimum bounding MBR defining the search. The first index ranges over 0,1 (X and Y) and is the dimension of the space. The second index ranges over 0,1 and specifies the min and max.

      `a` - The ArrayList holds the objects found to satisfy the search. Should be preallocated by the caller and set via the constructor or ensureCapacity(int) for expected result size (for efficiency). Will not overflow if undersized.

      Returns:
      true if there are some results of the search; false if none. ArrayList a.size() will return the number of hits.

    <!-- -->

    - #### searchFaceRTree

          public boolean searchFaceRTree(double[][] h,
                                         java.util.ArrayList a)

      Return the list of faces from faceRtree for the given query MBR.
      Parameters:
      `h` - two dimensional array of doubles which are the minimum bounding MBR defining the search. The first index ranges over 0,1 (X and Y) and is the dimension of the space. The second index ranges over 0,1 and specifies the min and max.

      `a` - The ArrayList holds the objects found to satisfy the search. Should be preallocated by the caller and set via the constructor or ensureCapacity(int) for expected result size (for efficiency). Will not overflow if undersized.

      Returns:
      true if there are some results of the search; false if none. ArrayList a.size() will return the number of hits.

    <!-- -->

    - #### getEdge

          public Edge getEdge(int id)
                       throws TopoEntityNotFoundException

      Returns a reference to an `Edge` object given its logical ID. If the object is not found in the cache, a TopoEntityNotFoundException is thrown.
      Parameters:
      `id` - the entity's logical ID

      Returns:
      the Edge reference

      Throws:
      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

    <!-- -->

    - #### getNode

          public Node getNode(int id)
                       throws TopoEntityNotFoundException

      Returns a reference to a `Node` object given its logical ID. If the object is not found in the cache, a TopoEntityNotFoundException is thrown.
      Parameters:
      `id` - the entity's logical ID

      Returns:
      the Node reference

      Throws:
      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

    <!-- -->

    - #### getFace

          public Face getFace(int id)
                       throws TopoEntityNotFoundException

      Returns a reference to a `Face` object given its logical ID. If the object is not found in the cache, a TopoEntityNotFoundException is thrown.
      Parameters:
      `id` - the entity's logical ID

      Returns:
      the Face reference

      Throws:
      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

    <!-- -->

    - #### getFaceBoundary

          public int[] getFaceBoundary(int faceID,
                                       int option)
                                throws TopoEntityNotFoundException,
                                       TopoDataException

      Returns an array of edge IDs making up the boundary of a face, with several options
      Parameters:
      `faceID` - The face for which the boundary edges are desired

      `option` - What type of boundary return is desired (0, 1, or 2).

      0 = external boundary ring without doubly traced edges (spurs)

      1 = external and internal rings without spurs

      2 = external and internal rings with spurs - i.e. the full, possibly degenerate, boundary

      Returns:
      an array of ints representing the list of boundary edge IDs. Edge IDs appear in the array once only and in positive sense only

      Throws:
      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      [`TopoDataException`](TopoDataException.md)

    <!-- -->

    - #### getNearestEdge

          public int getNearestEdge(Point2DD point)
                             throws java.sql.SQLException,
                                    TopoEntityNotFoundException

      Returns the ID of the `Edge` object that is nearest to the specified point. The determination of the nearest edge is made from the representation of the topology in the database, using the spatial index.
      If there are changed, added, or deleted edges in the instance and if the database has not been updated to reflect those changes, the result of this operator may not reflect the true situation in the cache.

      Parameters:
      `point` - the point for which the closest edge is sought

      Returns:
      the ID of the nearest edge

      Throws:
      `java.sql.SQLException`

      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

    <!-- -->

    - #### getNearestEdgeInCache

          public int getNearestEdgeInCache(Point2DD point)

      Returns the ID of the `Edge` object that of the edges loaded in the cache is nearest to the specified point. In case of ties, any of the tying edges may be returned. If no data is loaded or there are no edges in the cache, returns NOID.
      Parameters:
      `point` - the point for which the closest edge is sought

      Returns:
      the ID of the nearest edge

    <!-- -->

    - #### getNearestNode

          public int getNearestNode(Point2DD point)
                             throws java.sql.SQLException,
                                    TopoEntityNotFoundException

      Returns the ID of the `Node` object that is nearest to the specified point. The determination of the nearest node is made from the representation of the topology in the database, using the spatial index.
      If there are changed, added, or deleted nodes in the instance and if the database has not been updated to reflect those changes, the result of this operator may not reflect the true situation in the cache.

      Parameters:
      `point` - the point for which the closest node is sought

      Returns:
      the ID of the nearest node

      Throws:
      `java.sql.SQLException`

      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

    <!-- -->

    - #### getNearestNodeInCache

          public int getNearestNodeInCache(Point2DD p)

      Returns the ID of the `Node` object that of the nodes loaded in the cache is nearest to the specified point. In case of ties, any of the tying nodes may be returned. If no data is loaded or there are no nodes in the cache, returns NOID.
      Parameters:
      `p` - the point for which the closest node is sought

      Returns:
      the ID of the nearest node

    <!-- -->

    - #### getEdgeIterator

          public java.util.Iterator<Edge> getEdgeIterator()

      Provides an `Iterator` for traversal of all the `Edge` objects contained in the instance cache.
      Returns:
      an `Iterator` over a `Collection` of Edges

    <!-- -->

    - #### getNodeIterator

          public java.util.Iterator<Node> getNodeIterator()

      Provides an `Iterator` for traversal of all the `Node` objects contained in the instance cache.
      Returns:
      an `Iterator` over a `Collection` of Nodes

    <!-- -->

    - #### getFaceIterator

          public java.util.Iterator<Face> getFaceIterator()

      Provides an `Iterator` for traversal of all the `Face` objects contained in the instance cache.
      Returns:
      an `Iterator` over a `Collection` of Faces

    <!-- -->

    - #### getEdgeChanges

          public java.util.ArrayList<java.lang.Integer> getEdgeChanges()

      Provides a list of the edges that have been changed in the cache. These are the edges that have been changed since the cache topology was loaded from the database, but have not yet been written back out to the database.
      Returns:
      an `ArrayList` holding `Integer` objects wrapping edge IDs

    <!-- -->

    - #### getNodeChanges

          public java.util.ArrayList<java.lang.Integer> getNodeChanges()

      Provides a list of the nodes that have been changed in the cache. These are the nodes that have been changed since the cache topology was loaded from the database, but have not yet been written back out to the database.
      Returns:
      an `ArrayList` holding `Integer` objects wrapping node IDs

    <!-- -->

    - #### getFaceChanges

          public java.util.ArrayList<java.lang.Integer> getFaceChanges()

      Provides a list of the faces that have been changed in the cache. These are the faces that have been changed since the cache topology was loaded from the database, but have not yet been written back out to the database.
      Returns:
      an `ArrayList` holding `Integer` objects wrapping face IDs

    <!-- -->

    - #### getEdgeAdditions

          public java.util.ArrayList getEdgeAdditions()

      Provides a list of the edges that have been added in the cache. These are the edges that have been created since the cache topology was loaded from the database, but have not yet been written out to the database.
      Returns:
      an `ArrayList` holding `Integer` objects wrapping edge IDs

    <!-- -->

    - #### getNodeAdditions

          public java.util.ArrayList getNodeAdditions()

      Provides a list of the nodes that have been added in the cache. These are the nodes that have been created since the cache topology was loaded from the database, but have not yet been written out to the database.
      Returns:
      an `ArrayList` holding `Integer` objects wrapping node IDs

    <!-- -->

    - #### getFaceAdditions

          public java.util.ArrayList<java.lang.Integer> getFaceAdditions()

      Provides a list of the faces that have been added in the cache. These are the faces that have been created since the cache topology was loaded from the database, but have not yet been written out to the database.
      Returns:
      an `ArrayList` holding `Integer` objects wrapping face IDs

    <!-- -->

    - #### getEdgeDeletions

          public java.util.ArrayList<java.lang.Integer> getEdgeDeletions()

      Provides a list of the edges that have been marked as deleted in the cache: deleted since the cache topology was loaded from the database, but not yet removed from the database.
      Returns:
      an `ArrayList` holding `Integer` objects wrapping edge IDs

    <!-- -->

    - #### getNodeDeletions

          public java.util.ArrayList<java.lang.Integer> getNodeDeletions()

      Provides a list of the nodes that have been marked as deleted in the cache: deleted since the cache topology was loaded from the database, but not yet removed from the database.
      Returns:
      an `ArrayList` holding `Integer` objects wrapping node IDs

    <!-- -->

    - #### getFaceDeletions

          public java.util.ArrayList<java.lang.Integer> getFaceDeletions()

      Provides a list of the faces that have been marked as deleted in the cache: deleted since the cache topology was loaded from the database, but not yet removed from the database.
      Returns:
      an `ArrayList` holding `Integer` objects wrapping face IDs

    <!-- -->

    - #### moveIsolatedNode

          public void moveIsolatedNode(int nodeID,
                                       Point2DD point,
                                       boolean allowFaceChange)
                                throws InvalidTopoOperationException,
                                       TopoEntityNotFoundException,
                                       java.sql.SQLException,
                                       java.lang.Exception

      Moves an isolated node to a new face. The node must be carried to a location inside the new face and removed from the face currently owning it. It must be deleted from the current face and recreated in the new face. If a SQLException is raised, the connection is rolled back (implicitly clearing the cache) before the exception is rethrown.
      Parameters:
      `nodeID` - the ID of the node being moved

      `point` - the new node coordinate

      `allowFaceChange` - specify whether to allow the target face to be different from the containing face of nodeID

      Throws:
      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      `java.sql.SQLException`

      `java.lang.Exception`

    <!-- -->

    - #### moveIsolatedNode

          public void moveIsolatedNode(int nodeID,
                                       Point2DD point)
                                throws InvalidTopoOperationException,
                                       TopoEntityNotFoundException,
                                       java.sql.SQLException,
                                       java.lang.Exception

      Moves an isolated node. The node must be carried to a location inside the face currently owning it. Otherwise, it must be deleted and recreated. If a SQLException is raised, the connection is rolled back (implicitly clearing the cache) before the exception is rethrown.
      Parameters:
      `nodeID` - the ID of the node being moved

      `point` - the new node coordinate

      Throws:
      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      `java.sql.SQLException`

      `java.lang.Exception`

    <!-- -->

    - #### moveIsolatedNode

          public void moveIsolatedNode(int nodeID,
                                       Point2DD point,
                                       int faceID)
                                throws InvalidTopoOperationException,
                                       TopoEntityNotFoundException,
                                       java.sql.SQLException,
                                       java.lang.Exception

      Moves an isolated node to a new face. The node must be carried to a location inside the new face and removed from the face currently owning it. It must be deleted from the current face and recreated in the new face. If a SQLException is raised, the connection is rolled back (implicitly clearing the cache) before the exception is rethrown.
      Parameters:
      `nodeID` - the ID of the node being moved

      `point` - the new node coordinate

      `faceID` - the ID of the new face to contain the node

      Throws:
      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      `java.sql.SQLException`

      `java.lang.Exception`

    <!-- -->

    - #### moveNode

          public void moveNode(int nodeID,
                               Point2DD[][] edgesCoords)
                        throws InvalidTopoOperationException,
                               TopoEntityNotFoundException,
                               java.lang.Exception,
                               java.sql.SQLException

      Moves a node and its attached edges after checking that no topological changes would be required, except that island edges and nodes may change containing faces. Since no topological elements are allowed to be created or destroyed (or even modified in most cases), there are no changes to the relationships of features to topological elements as a result of this method.
      If the node is isolated, you must use the method moveIsolatedNode() which has a simpler interface.

      Parameters:
      `nodeID` - the ID of the node being moved with its attached edges

      `edgesCoords` - an array of arrays of new edge coordinates for each attached edge, starting with the node start edge and proceeding in clockwise sequence as would be obtained by a call to getNodeStar(). The array for each edge must include the endpoints, match the others at the moved node and be unchanged at the other node, and be in the same sense as the original edge. Any loops which connect twice at the moved node should be in the array twice, again in the same sense.

      Throws:
      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      `java.lang.Exception`

      `java.sql.SQLException`

    <!-- -->

    - #### moveNode

          public void moveNode(int nodeID,
                               Point2DD[][] edgesCoords,
                               java.util.ArrayList<java.lang.Integer> movedIsoNodes,
                               java.util.ArrayList<java.lang.Integer> movedIsoEdges,
                               boolean allowIsoMoves)
                        throws InvalidTopoOperationException,
                               TopoEntityNotFoundException,
                               java.lang.Exception,
                               java.sql.SQLException

      Moves a node and its attached edges after checking that no topological changes would be required. There is one class of topological changes optionally permitted: At user choice, island edges and nodes may be allowed to change containing faces. Since no topological elements are allowed to be created or destroyed (or even modified in most cases), there are no changes to the relationships of features to topological elements as a result of this method
      If the node is isolated, you must use the method moveIsolatedNode(), which has a simpler interface.

      If a SQLException is raised, the connection is rolled back (implicitly clearing the cache) before the exception is rethrown.

      Parameters:
      `nodeID` - the ID of the node being moved with its attached edges

      `edgesCoords` - an array of arrays of new edge coordinates for each attached edge, starting with the node start edge and proceeding in clockwise sequence as would be obtained by a call to getNodeStar(). The array for each edge must include the endpoints, match the others at the moved node and be unchanged at the other node, and be in the same sense as the original edge. Any loops which connect twice at the moved node should be in the array twice, again in the same sense.

      `movedIsoNodes` - allocate with default capacity; this method will fill it with the IDs of isolated nodes which change faces as a result of the move

      `movedIsoEdges` - allocate with default capacity; this method will fill it with the IDs of isolated edges which change faces as a result of the move

      `allowIsoMoves` - whether (true) or not (false) to allow a node move operation that would cause any isolated nodes or edges to be in a different face. If such moves are allowed and any do occur, the containing face information for such isolated nodes and edges is adjusted.

      Throws:
      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      `java.lang.Exception`

      `java.sql.SQLException`

    <!-- -->

    - #### moveEdge

          public void moveEdge(int edgeID,
                               int sNodeID,
                               int tNodeID,
                               Point2DD[] edgeCoords)
                        throws InvalidTopoOperationException,
                               TopoEntityNotFoundException,
                               java.lang.Exception,
                               java.sql.SQLException

      Moves one endpoint of an edge and changes the edge coordinates after checking that no topological changes would be required, other than some possible exceptions. The possible exceptions are:
      - There will be topological changes at the node from which the edge is lifted and at the node to which the edge is reattached.
      - Some edges may change which boundary component they are a part of and therefore have their face pointers changed on one side.
      - Island edges and nodes may change containing faces. In the case of island edges this means that entire inner boundary components may change faces.

      Because no topological changes are permitted at the unmoved end of the edge, this also precludes a loop edge being opened up or a non-loop edge being turned into a loop, and this will be trapped.

      The edge to be moved must have different faces on each side. That means the edge is part of two face boundary components, at least one of which must be the outside boundary component of its face.

      The node to which the end of the edge is moved must be located in one of the two boundary components of which the original edge is a part; that is, the node must be reachable in a trace starting with the edge's nextEdgeL or nextEdgeR. Note that it is possible for the two boundary components to be the inside and outside of the same component, in which case the destination node would be found in both.

      Since no topological elements are allowed to be created or destroyed (or even modified in most cases), there are no changes to the relationships of features to topological elements as a result of this method.

      Parameters:
      `edgeID` - the moved edge

      `sNodeID` - the ID of the node from which the edge is detached (*s*ource node)

      `tNodeID` - the ID of the node to which the edge is reattached (*t*arget node)

      `edgeCoords` - an array of coordinates for the moved edge. The array must match the node coordinates at the new node and at the node at the other end, and be in the same sense as the old edge coordinates.

      Throws:
      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      `java.lang.Exception`

      `java.sql.SQLException`

    <!-- -->

    - #### moveEdge

          public void moveEdge(int edgeID,
                               int sNodeID,
                               int tNodeID,
                               Point2DD[] edgeCoords,
                               java.util.ArrayList<java.lang.Integer> movedIsoNodes,
                               java.util.ArrayList<java.lang.Integer> movedIsoEdges,
                               boolean allowIsoMoves)
                        throws InvalidTopoOperationException,
                               TopoEntityNotFoundException,
                               java.lang.Exception,
                               java.sql.SQLException

      Moves one endpoint of an edge and changes the edge coordinates after checking that no topological changes would be required, other than some possible exceptions. The possible exceptions are:
      - There will be topological changes at the node from which the edge is lifted and at the node to which the edge is reattached.
      - Some edges may change which boundary component they are a part of and therefore have their face pointers changed on one side.
      - Island edges and nodes may change containing faces. In the case of island edges this means that entire inner boundary components may change faces.

      Because no topological changes are permitted at the unmoved end of the edge, this also precludes a loop edge being opened up or a non-loop edge being turned into a loop, and this will be trapped.

      The edge to be moved must have different faces on each side. That means the edge is part of two face boundary components, at least one of which must be the outside boundary component of its face.

      The node to which the end of the edge is moved must be located in one of the two boundary components of which the original edge is a part; that is, the node must be reachable in a trace starting with the edge's nextEdgeL or nextEdgeR. Note that it is possible for the two boundary components to be the inside and outside of the same component, in which case the destination node would be found in both.

      Since no topological elements are allowed to be created or destroyed (or even modified in most cases), there are no changes to the relationships of features to topological elements as a result of this method.

      If a SQLException is raised, the connection is rolled back (implicitly clearing the cache) before the exception is rethrown.

      Parameters:
      `edgeID` - the moved edge

      `sNodeID` - the ID of the node from which the edge is detached (*s*ource node)

      `tNodeID` - the ID of the node to which the edge is reattached (*t*arget node)

      `edgeCoords` - an array of coordinates for the moved edge. The array must match the node coordinates at the new node and at the node at the other end, and be in the same sense as the old edge coordinates.

      `movedIsoNodes` - allocate with default capacity; this method will fill it with the IDs of isolated nodes which change faces as a result of the move

      `movedIsoEdges` - allocate with default capacity; this method will fill it with the IDs of isolated edges which change faces as a result of the move

      `allowIsoMoves` - whether (true) or not (false) to allow an edge move operation that would cause any isolated nodes or edges to be in a different face. If such moves are allowed and if any do occur, the containing face information for such isolated nodes and edges is adjusted.

      Throws:
      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      `java.lang.Exception`

      `java.sql.SQLException`

    <!-- -->

    - #### addEdge

          public int addEdge(int node1,
                             int node2,
                             Point2DD[] coords)
                      throws InvalidTopoOperationException,
                             TopoEntityNotFoundException,
                             java.sql.SQLException

      Adds an `Edge` to the topology, making all necessary adjustments to the surrounding topological context. The shape points of the edge must place the edge totally inside a single face.
      If a SQLException is raised, the connection is rolled back (implicitly clearing the cache) before the exception is rethrown.

      Parameters:
      `node1` - the logical ID of the start node of the new edge

      `node2` - the logical ID of the end node of the new edge

      `coords` - an array of points, including the endpoints (nodes), constituting the edge

      Returns:
      the logical ID of the added edge

      Throws:
      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      `java.sql.SQLException`

    <!-- -->

    - #### addLoop

          public int addLoop(int nodeID,
                             Point2DD[] coords)
                      throws TopoEntityNotFoundException,
                             java.sql.SQLException,
                             InvalidTopoOperationException

      Adds an edge that loops and connects to the same node. Can also be done by calling addEdge with node1=node2, which will wrap a call to this method.
      If a SQLException is raised, the connection is rolled back (implicitly clearing the cache) before the exception is rethrown.

      Parameters:
      `nodeID` - the node to which the loop is to be connected

      `coords` - array of points describing the loop, including the endpoints

      Returns:
      the logical ID of the added edge

      Throws:
      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      `java.sql.SQLException` - on database error

      [`InvalidTopoOperationException`](InvalidTopoOperationException.md) - if data is not loaded

    <!-- -->

    - #### addLinearGeometry

          public int[] addLinearGeometry(JGeometry geom)
                                  throws InvalidTopoOperationException,
                                         java.sql.SQLException,
                                         TopoEntityNotFoundException,
                                         java.lang.Exception

      Adds a linear (line string) geometry to the topology, inserting edges and nodes as necessary based on the full intersection of the geometry with the edges and nodes in the topology graph. Also will take a multiline string.
      Returns an array of the edge IDs of the inserted and shared edges in sequence from the start to the end of the geometry. The coordinate order of all inserted edges is in the same sense as the input geometry and are returned positive, but there may be edges shared with the original topology that are listed in negative sense.

      Parameters:
      `geom` - an sdoapi geometry representing a single or multi- line-string in order from start to finish

      Returns:
      an array of edge IDs for the inserted and shared edges in order from start to finish of the geometry

      Throws:
      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

      `java.sql.SQLException`

      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      `java.lang.Exception`

    <!-- -->

    - #### addLinearGeometry

          public int[] addLinearGeometry(Point2DD[] coords)
                                  throws InvalidTopoOperationException,
                                         java.sql.SQLException,
                                         TopoEntityNotFoundException,
                                         java.lang.Exception

      Adds a linear (line string) geometry to the topology, inserting edges and nodes as necessary based on the full intersection of the geometry with the edges and nodes in the topology graph.
      Returns an array of the edge IDs of the inserted and shared edges in sequence from the start to the end of the geometry. The coordinate order of all inserted edges is in the same sense as the input geometry and are returned positive, but there may be edges shared with the original topology that are listed in negative sense.

      Parameters:
      `coords` - an array of points representing a single line string in order from start to finish

      Returns:
      an array of edge IDs for the inserted and shared edges in order from start to finish of the line string

      Throws:
      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

      `java.sql.SQLException`

      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      `java.lang.Exception`

    <!-- -->

    - #### addPolygonGeometry

          public int[] addPolygonGeometry(JGeometry geom)
                                   throws InvalidTopoOperationException,
                                          java.sql.SQLException,
                                          TopoEntityNotFoundException,
                                          java.lang.Exception

      Adds a polygon geometry to the topology, inserting edges and nodes as necessary based on the full intersection of the geometry with the edges and nodes in the topology graph. The geometry may be a polygon or multipolygon. Each polygon must have a single outer ring, which may contain any number of interior (island) rings.
      Returns an array of the face IDs of all the faces which are contained inside any of the outer rings and are outside any inner rings.

      The geometry may not intersect itself and this will be trapped.

      Parameters:
      `geom` - the geometry which must be one outer ring each with zero or more interior island rings

      Returns:
      an array of face IDs for all faces which together exactly cover the geometry excluding its island rings

      Throws:
      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

      `java.sql.SQLException`

      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      `java.lang.Exception`

    <!-- -->

    - #### addPolygonGeometry

          public int[] addPolygonGeometry(Point2DD[] coords)
                                   throws InvalidTopoOperationException,
                                          java.sql.SQLException,
                                          TopoEntityNotFoundException,
                                          java.lang.Exception

      Adds a single polygon geometry to the topology, inserting edges and nodes as necessary based on the full intersection of the polygon with the edges and nodes in the topology graph. Returns an array of the face IDs of all the faces which are contained inside the polygon.
      The polygon must be stored counterclockwise. The polygon may not intersect itself and this will be trapped.

      Parameters:
      `coords` - an array of points representing the vertices of the polygon in counterclockwise order with the first vertex repeated in the last

      Returns:
      an array of face IDs for all faces which together exactly cover the polygon

      Throws:
      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

      `java.sql.SQLException`

      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      `java.lang.Exception`

    <!-- -->

    - #### fixFaceMBRs

          public boolean fixFaceMBRs()
                              throws TopoEntityNotFoundException,
                                     InvalidTopoOperationException

      Adjusts the MBRs of any faces in the cache whose instance MBR does not match MBR computed from the edges in the outer boundary of the face.
      Returns:
      true if any face MBR(s) was/were corrected; false otherwise

      Throws:
      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

    <!-- -->

    - #### removeObsoleteNodes

          public boolean removeObsoleteNodes()
                                      throws TopoEntityNotFoundException,
                                             java.sql.SQLException

      Removes any nodes in the cache which are connected to two and only two distinct edges, are not assigned to point features, and do not serve as the demarcation between mismatched linear features. Small numbers of such nodes may result when addPolygonGeometry() is used to build a topology from the repeated insertion of polygons. They may also exist when edges have been removed during editing operations, leaving some unnecessary nodes.
      Returns:
      true if any nodes were removed; false otherwise

      Throws:
      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      `java.sql.SQLException`

    <!-- -->

    - #### addPointGeometry

          public int addPointGeometry(JGeometry geom)
                               throws InvalidTopoOperationException,
                                      java.sql.SQLException,
                                      TopoEntityNotFoundException,
                                      java.lang.Exception

      Adds a point geometry to the topology. If the point coincides with an existing node, no changes are made to the topology. Otherwise, an isolated node or a node splitting an edge is added to the topology.
      Parameters:
      `geom` - the geometry which represents the point

      Returns:
      the ID of the added or reused node

      Throws:
      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

      `java.sql.SQLException`

      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      `java.lang.Exception`

    <!-- -->

    - #### addPointGeometry

          public int addPointGeometry(Point2DD coord)
                               throws InvalidTopoOperationException,
                                      java.sql.SQLException,
                                      TopoEntityNotFoundException,
                                      java.lang.Exception

      Adds a point to the topology. If the point coincides with an existing node, no changes are made to the topology. Otherwise, an isolated node or a node splitting an edge is added to the topology.
      Parameters:
      `coord` - the point

      Returns:
      the ID of the added or reused node

      Throws:
      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

      `java.sql.SQLException`

      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      `java.lang.Exception`

    <!-- -->

    - #### changeEdgeCoords

          public void changeEdgeCoords(int edge,
                                       Point2DD[] coords)
                                throws InvalidTopoOperationException,
                                       TopoEntityNotFoundException,
                                       java.sql.SQLException

      Replaces the coordinate string for an edge without changing the topological context of the edge. The only other changes this operation may require are: (1) the possible reassignments of island nodes and edges - this can only happen if the adjusted edge is a boundary between distinct faces; and (2) the adjustment of the MBRs of the faces on both sides, again only if they are distinct.
      The changed edge coordinates cannot move the nodes at the endpoints. If that is desired, the edge must be deleted, the node(s) deleted (if permissible), and new node(s) and edge added, or you must use the moveNode() and/or moveEdge() methods.

      The changed edge cannot reorder the node stars at the edge endpoints. The changed edge cannot be such as to reverse the faces on the left and right sides in the case of different faces on the two sides.

      If a SQLException is raised, the connection is rolled back (implicitly clearing the cache) before the exception is rethrown.

      Parameters:
      `edge` - the edge ID of the edge to be spatially changed

      `coords` - the new coordinates of the edge, including the node coordinates at both ends, which must match the existing node coordinates and therefore the terminal coordinates of the existing edge. The direction of the edge must also be preserved.

      Throws:
      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      `java.sql.SQLException`

    <!-- -->

    - #### changeEdgeCoords

          public void changeEdgeCoords(int edge,
                                       Point2DD[] coords,
                                       java.util.ArrayList<java.lang.Integer> movedIsoNodes,
                                       java.util.ArrayList<java.lang.Integer> movedIsoEdges,
                                       boolean allowIsoMoves)
                                throws InvalidTopoOperationException,
                                       TopoEntityNotFoundException,
                                       java.sql.SQLException

      Replaces the coordinate string for an edge without changing the topological context of the edge. There is one type of topological change permitted at the user's option: the possible reassignments of island nodes and edges - if the adjusted edge is a boundary between distinct faces. The adjustment of the MBRs of the faces on both sides, if distinct, will take place.
      The changed edge coordinates cannot move the nodes at the endpoints. If that is desired, the edge must be deleted, the node(s) deleted (if permissible), and new node(s) and edge added, or you must use the moveEdge() and/or moveNode() methods.

      The changed edge cannot reorder the node stars at the edge endpoints. The changed edge cannot be such as to reverse the faces on the left and right sides in the case of different faces on the two sides.

      If a SQLException is raised, the connection is rolled back (implicitly clearing the cache) before the exception is rethrown.

      Parameters:
      `edge` - the edge ID of the edge to be spatially changed

      `coords` - the new coordinates of the edge, including the node coordinates at both ends, which must match the existing node coordinates and therefore the terminal coordinates of the existing edge. The direction of the edge must also be preserved.

      `movedIsoNodes` - allocate with default capacity; this method will fill it with the IDs of isolated nodes which change faces as a result of the change

      `movedIsoEdges` - allocate with default capacity; this method will fill it with the IDs of isolated edges which change faces as a result of the change

      `allowIsoMoves` - whether (true) or not (false) to allow the move of isolated entities, and to adjust edge coordinates and island reassignments as needed.

      Throws:
      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      `java.sql.SQLException`

    <!-- -->

    - #### addNode

          public int addNode(int edgeID,
                             Point2DD p,
                             int coordIndex,
                             boolean isNewShapePoint)
                      throws TopoEntityNotFoundException,
                             InvalidTopoOperationException,
                             java.sql.SQLException

      Adds a node to an edge, splitting the edge in the process. The split piece at the beginning of the old edge will carry the old edge ID.
      If a SQLException is raised, the connection is rolled back (implicitly clearing the cache) before the exception is rethrown.

      Parameters:
      `edgeID` - the edge to be split by the added node (positive sense only)

      `p` - the `Point2DD` representing the position of the added node

      `coordIndex` - the index of the array position in the edge coord array on or after which the node is to be added (index is 0 for start)

      `isNewShapePoint` - true if the added node is to be a new shape point following the indexed vertex of the edge; false if the added node is to be exactly on the exactly on the indexed vertex

      Returns:
      the logical ID of the added node

      Throws:
      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

      `java.sql.SQLException`

    <!-- -->

    - #### addIsolatedNode

          public int addIsolatedNode(Point2DD p)
                              throws TopoEntityNotFoundException,
                                     InvalidTopoOperationException,
                                     java.sql.SQLException,
                                     java.lang.Exception

      Adds an isolated node inside of a face when the face ID is not known. If an Exception or any subclass but InvalidTopoOperation is raised, the connection is rolled back (implicitly clearing the cache) before the exception is rethrown.
      Parameters:
      `p` - coordinates of the node

      Returns:
      the logical ID of the added node

      Throws:
      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

      `java.sql.SQLException`

      `java.lang.Exception`

    <!-- -->

    - #### addIsolatedNode

          public int addIsolatedNode(int faceID,
                                     Point2DD p)
                              throws TopoEntityNotFoundException,
                                     InvalidTopoOperationException,
                                     java.sql.SQLException

      Adds an isolated node inside of a face when the face ID is known. If a SQLException is raised, the connection is rolled back (implicitly clearing the cache) before the exception is rethrown.
      Parameters:
      `faceID` - the logical ID of the face

      `p` - coordinates of the node

      Returns:
      the logical ID of the added node

      Throws:
      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

      `java.sql.SQLException`

    <!-- -->

    - #### removeNode

          public void removeNode(int nodeID)
                          throws InvalidTopoOperationException,
                                 java.sql.SQLException,
                                 TopoEntityNotFoundException

      Removes an isolated node or a node at the joining of two edges, merging the edges into one. An InvalidTopoOperationException is thrown if one or three or more edges meet at the node or if the positive and negative sense of same edge meet at node (a loop), if one or more point features are associated with the node, or if mismatched lineal features are assigned to the edges on either side.
      If a SQLException is raised, the connection is rolled back (implicitly clearing the cache) before the exception is rethrown.

      Parameters:
      `nodeID` - the node to be removed

      Throws:
      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

      `java.sql.SQLException`

      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

    <!-- -->

    - #### removeEdge

          public void removeEdge(int edgeID)
                          throws java.sql.SQLException,
                                 TopoEntityNotFoundException,
                                 InvalidTopoOperationException

      Remove an edge, merging faces if there are different faces on each side of the edge.
      If a linear feature is associated with the edge, if different area features are associated with the faces on the two sides in the merge face case, or if any portion of the edge is outside the editable window, an InvalidTopoOperationException is thrown. If the edge does not exist an InvalidTopoOperationException is also thrown. If any other exception is raised, the connection is rolled back (which implicitly clears the cache) before the exception is rethrown.

      Parameters:
      `edgeID` - the edge to be removed

      Throws:
      `java.sql.SQLException`

      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

    <!-- -->

    - #### validateCache

          public boolean validateCache()
                                throws TopoValidationException,
                                       TopoEntityNotFoundException,
                                       java.sql.SQLException,
                                       java.lang.Exception

      Wrapper for validateCache(int level). Simply calls validateCache(1) to provide validation with full computational geometry checking.
      Returns:
      true if no errors encountered

      Throws:
      [`TopoValidationException`](TopoValidationException.md)

      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      `java.sql.SQLException`

      `java.lang.Exception`

    <!-- -->

    - #### validateCache

          public boolean validateCache(int level)
                                throws TopoValidationException,
                                       TopoEntityNotFoundException,
                                       java.sql.SQLException,
                                       java.lang.Exception

      Performs a topological validation of the cache, checking the consistency of all pointer relationships in the edge/node/face graph. At the user's option, also performs computational geometry checking. Note this is cache-only and will not reveal errors in the database topology outside the cache bounds. The method loadWindow() ensures that enough surrounding data is loaded into the cache for this method to perform validation.
      Parameters:
      `level` - whether to check computational geometry (0 or 1).

      0 = without computational geometry: face trace closure including infinite loop trap; edge next/previous pointer consistency; edges meet at common nodes; island nodes point back to faces; all edges on a face boundary (inner and outer) link to the face.

      1 = all of level 0, plus computational geometry: island entities are inside face outer boundary; no edge intersects itself or another edge; end coordinates of edges match node coordinates; node stars are properly ordered geometrically.

      Returns:
      true if no errors encountered

      Throws:
      [`TopoValidationException`](TopoValidationException.md) - if an error is found in any test

      `java.lang.Exception` - if there is some missing data during computational geometry checksvalidateCache

      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md) - if some entity cannot be found and is pointed to by another entity

      `java.sql.SQLException`

    <!-- -->

    - #### getContainingFace

          public int getContainingFace(Point2DD p)
                                throws TopoEntityNotFoundException,
                                       java.sql.SQLException,
                                       java.lang.Exception

      Overload provides the default behavior of getContaingFace(), that with allow_iso_coincidence false. If the test point intersects an isolated node or a contained dendritic structure,it will not be considered contained in any face
      Parameters:
      `p` - the test point

      Returns:
      the face ID or the containing face or NOID

      Throws:
      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      `java.sql.SQLException`

      `java.lang.Exception`

    <!-- -->

    - #### getContainingFace

          public int getContainingFace(Point2DD p,
                                       boolean allow_iso_coincidence)
                                throws TopoEntityNotFoundException,
                                       java.sql.SQLException,
                                       java.lang.Exception

      From the faces in the instance cache, determines the one, if any, that contains the test point in its open set. Processing includes islands; that is, the point must be in the open set excluding islands, not just inside the outer polygon.
      If the point is exactly on an edge or node, NOID is returned. EXCEPT: If allow_iso_coincidence is passed true the method will return a face ID if the point is inside the outer boundary of the face but coincident with an isolated node or isolated dendritic edge (same face both sides) contained in the face.

      If a point is found not to be in any of the finite faces in the cache several situations exist for the return:
      1. The whole topology has been cached -- returns UNIVERSE_FACE
      2. A window has been loaded and:
        a. The point is outside the window -- returns NOID
        b. The point is inside the window -- returns UNIVERSE_FACE
      3. Neither a window nor the whole topology has been loaded -- returns NOID

      Parameters:
      `p` - the test point.

      `allow_iso_coincidence` - whether to ignore iso coincidence of test point

      Returns:
      the face ID of the containing face.

      Throws:
      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      `java.sql.SQLException`

      `java.lang.Exception`

    <!-- -->

    - #### getNodeStarCount

          public int getNodeStarCount(int nodeID)
                               throws TopoEntityNotFoundException

      Gets a count of the number of edges connected at a node.
      Returns:
      the count; from 0 for an isolated node to any number

      Throws:
      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

    <!-- -->

    - #### getNodeStar

          public int[] getNodeStar(int nodeID)
                            throws TopoEntityNotFoundException

      Gets an array of integers representing the IDs of a clockwise enumeration of all the edges connected to the given node. A positive edge ID represents an edge for which the node is its origin node. A negative edge ID represents an edge for which the node is its end node.
      If there are loops connected to the node, edges may appear in the list twice with opposite signs.

      Returns:
      an integer array which is the clockwise list of edges

      Throws:
      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

    <!-- -->

    - #### getNodeFaceStar

          public int[] getNodeFaceStar(int nodeID)
                                throws TopoEntityNotFoundException,
                                       java.sql.SQLException

      Gets an array of integers representing the IDs of a clockwise enumeration of all the faces adjoining the given node. There will be one face returned for each edge connected to the node. For an isolated node, the containing face is returned. A face may appear more than once in the list.
      Returns:
      an integer array which is the clockwise list of faces

      Throws:
      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      `java.sql.SQLException`

    <!-- -->

    - #### loadEdge

          public Edge loadEdge(int id)
                        throws TopoEntityNotFoundException,
                               InvalidTopoOperationException,
                               java.sql.SQLException

      Loads an edge from the database if the edge is not already in the cache. If it is already in the cache, an InvalidTopoOperationException is thrown. If it is not in the database, a TopoEntityNotFoundException is thrown.
      Returns:
      the Edge object loaded.

      Throws:
      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

      `java.sql.SQLException`

    <!-- -->

    - #### loadNode

          public Node loadNode(int id)
                        throws TopoEntityNotFoundException,
                               java.sql.SQLException,
                               InvalidTopoOperationException

      Loads a node from the database if the node is not already in the cache. If it is already in the cache, an InvalidTopoOperationException is thrown. If it is not in the database, a TopoEntityNotFoundException is thrown.
      Returns:
      the Node object loaded.

      Throws:
      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      `java.sql.SQLException`

      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

    <!-- -->

    - #### loadFace

          public Face loadFace(int id)
                        throws TopoEntityNotFoundException,
                               java.sql.SQLException,
                               InvalidTopoOperationException

      Loads a face from the database if the face is not already in the cache. If it is already in the cache, an InvalidTopoOperationException is thrown. If it is not in the database, a TopoEntityNotFoundException is thrown.
      Returns:
      the Face object loaded.

      Throws:
      [`TopoEntityNotFoundException`](TopoEntityNotFoundException.md)

      `java.sql.SQLException`

      [`InvalidTopoOperationException`](InvalidTopoOperationException.md)

    <!-- -->

    - #### getSrid

          public int getSrid()

      Returns the SRID of the topology.
      Returns:
      the SRID of the topology

    <!-- -->

    - #### getTopoTransactionID

          public int getTopoTransactionID()

      Returns the topology transaction ID if there is data loaded in the cache for update.
      Returns:
      the topology transaction ID for the editable cache. If the cache is not editable, returns 0.

    <!-- -->

    - #### getTopoName

          public java.lang.String getTopoName()

      Returns the name of the topology.
      Returns:
      the topology name

    <!-- -->

    - #### getIsEditable

          public boolean getIsEditable()

      Returns the editing state.
      Returns:
      isEditable

    <!-- -->

    - #### closeStmt

          public void closeStmt()
                         throws java.sql.SQLException

      Closes the statement cursor.
      Throws:
      `java.sql.SQLException` - if a database error occurs

    <!-- -->

    - #### dispose

          public void dispose()

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

- [Prev Class](TopoFrame.md)
- [Next Class](TopoPreprocess.md)

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
