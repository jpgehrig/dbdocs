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

- [Prev Class](OraTst.md)
- [Next Class](SDODimArray.md)

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

## Interface Path

- All Superinterfaces:
  java.lang.Cloneable, java.lang.Comparable, java.io.Serializable

  ------------------------------------------------------------------------



      public interface Path
      extends java.lang.Cloneable, java.io.Serializable, java.lang.Comparable

  This interface defines a network path.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                       | Method and Description                                                                                                                                                                                                                                                                                                                               |
    |-----------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.util.ArrayList`                   | `add``(java.util.ArrayList pathList)`<br>Adds a list of paths to the path.                                                                                                                                                                                                                                                                           |
    | `java.util.ArrayList`                   | `add``(Path path)`<br>Adds a given path to the path.                                                                                                                                                                                                                                                                                                 |
    | `java.lang.Object`                      | `clone``()`<br>Clones the path.                                                                                                                                                                                                                                                                                                                      |
    | `void`                                  | `computeGeometry``(double tolerance)`<br>Computes the path geometry from its link geometries.                                                                                                                                                                                                                                                        |
    | `boolean`                               | `contains``(`[`Link`](Link.md)` l)`<br>Checks if the path contains the specified link.                                                                                                                                                                                                                                                               |
    | `boolean`                               | `contains``(`[`Node`](Node.md)` n)`<br>Checks if the path contains the specified node.                                                                                                                                                                                                                                                               |
    | `boolean`                               | `contains``(Path path)`<br>Checks if the path contains the specified path.                                                                                                                                                                                                                                                                           |
    | `void`                                  | `extendPath``(`[`Link`](Link.md)` newStartLink, `[`Link`](Link.md)` newEndLink)`<br>Extends the path by adding a new start link and a new end link The given links must be topologically connected to the path or an exception will be thrown No extension in the specific direction (start or end) if a null link is given                          |
    | `java.util.ArrayList`                   | `getCommonLinks``(Path path)`<br>Returns the common links between two paths Note only links with consistent path direction will be returned                                                                                                                                                                                                          |
    | `java.util.ArrayList`                   | `getCommonNodes``(Path path)`<br>Returns the common nodes between two paths                                                                                                                                                                                                                                                                          |
    | `java.util.ArrayList`                   | `getCommonSubPaths``(Path path)`<br>Returns the common sub-paths between two paths                                                                                                                                                                                                                                                                   |
    | `double`                                | `getCost``()`<br>Returns the path cost.                                                                                                                                                                                                                                                                                                              |
    | `double`                                | `getDuration``()`<br>Gets path duration information                                                                                                                                                                                                                                                                                                  |
    | [`Node`](Node.md)                       | `getEndNode``()`<br>Returns the end node of the path.                                                                                                                                                                                                                                                                                                |
    | [`JGeometry`](../geometry/JGeometry.md) | `getGeometry``()`<br>Returns the path geometry (JGeometry).                                                                                                                                                                                                                                                                                          |
    | `int`                                   | `getID``()`<br>Returns the path ID.                                                                                                                                                                                                                                                                                                                  |
    | [`Link`](Link.md)`[]`                   | `getLinkArray``()`<br>Returns the path links as an array.                                                                                                                                                                                                                                                                                            |
    | [`Link`](Link.md)                       | `getLinkAt``(int index)`                                                                                                                                                                                                                                                                                                                             |
    | `java.util.Iterator`                    | `getLinks``()`<br>Returns the path links as an Iterator.                                                                                                                                                                                                                                                                                             |
    | `java.lang.String`                      | `getName``()`<br>Returns the path name.                                                                                                                                                                                                                                                                                                              |
    | [`Network`](Network.md)                 | `getNetwork``()`<br>Returns the network that contains the path.                                                                                                                                                                                                                                                                                      |
    | [`Node`](Node.md)`[]`                   | `getNodeArray``()`<br>Returns the path nodes as an array.                                                                                                                                                                                                                                                                                            |
    | [`Node`](Node.md)                       | `getNodeAt``(int index)`<br>Returns the specified node of the path.                                                                                                                                                                                                                                                                                  |
    | `java.util.Iterator`                    | `getNodes``()`<br>Returns the path nodes as an Iterator.                                                                                                                                                                                                                                                                                             |
    | `int`                                   | `getNoOfLinks``()`<br>Returns the number of links in the path.                                                                                                                                                                                                                                                                                       |
    | [`Node`](Node.md)                       | `getStartNode``()`<br>Returns the start node of the path.                                                                                                                                                                                                                                                                                            |
    | `boolean`                               | `getState``()`<br>Gets the path state.                                                                                                                                                                                                                                                                                                               |
    | `Path`                                  | `getSubPath``(int startNodeIndex, int endNodeIndex)`<br>Returns the sub-path between startNodeIndex and ednNodeIndex                                                                                                                                                                                                                                 |
    | `double[][]`                            | `getTspNodeDuration``()`<br>Returns the TSP path node duration in an array of double The order of the duration is the same as the one in getTSPNodeNodeOrder() the duration is returned as an array of two doubles duration\[i\]\[0\] represents the arrival duration for the i-th TSP node and This information is only used for TSP related analys |
    | [`Node`](Node.md)`[]`                   | `getTspNodeOrder``()`<br>Returns the TSP path node visit order in an array of Node This information is only used for TSP related analysis                                                                                                                                                                                                            |
    | `java.lang.String`                      | `getType``()`<br>Returns the path type.                                                                                                                                                                                                                                                                                                              |
    | `java.lang.Object`                      | `getUserData``()`<br>Gets user defined data.                                                                                                                                                                                                                                                                                                         |
    | `java.lang.Object`                      | `getUserData``(java.lang.String name)`<br>Gets user data                                                                                                                                                                                                                                                                                             |
    | `int`                                   | `indexOf``(`[`Link`](Link.md)` link)`<br>Returns the link index of the given link in the path                                                                                                                                                                                                                                                        |
    | `int`                                   | `indexOf``(`[`Link`](Link.md)` link, int fromIndex)`<br>Returns the link index of the given link in the path starting from fromIndex                                                                                                                                                                                                                 |
    | `int`                                   | `indexOf``(`[`Node`](Node.md)` node)`<br>Returns the node index of the given node in the path                                                                                                                                                                                                                                                        |
    | `int`                                   | `indexOf``(`[`Node`](Node.md)` node, int fromIndex)`<br>Returns the node index of the given node in the path starting from fromIndex                                                                                                                                                                                                                 |
    | `boolean`                               | `isActive``()`<br>Checks if the path is active.                                                                                                                                                                                                                                                                                                      |
    | `boolean`                               | `isClosed``()`<br>Checks if the path is closed.                                                                                                                                                                                                                                                                                                      |
    | `boolean`                               | `isConnected``(Path path)`<br>Checks if the path is connected.                                                                                                                                                                                                                                                                                       |
    | `boolean`                               | `isLinkGeometryReversed``(int linkIndex, double tolerance)`<br>Checks if the given i-th link geometry in the path is reversed in the path direction                                                                                                                                                                                                  |
    | `boolean`                               | `isLinkReversed``(int linkIndex)`<br>Checks if the given i-th link in the path is reversed in the path direction                                                                                                                                                                                                                                     |
    | `boolean`                               | `isLogical``()`<br>Chceks if the path is logical.                                                                                                                                                                                                                                                                                                    |
    | `boolean`                               | `isReversePath``(Path path)`<br>Checks if the given path is the reverse path of the path                                                                                                                                                                                                                                                             |
    | `boolean`                               | `isSameDirection``(Path path)`<br>Checks if two paths the have same direction (indicated by the path node orde).                                                                                                                                                                                                                                     |
    | `boolean`                               | `isSamePath``(Path path)`<br>Checks if the given path has the same path links                                                                                                                                                                                                                                                                        |
    | `boolean`                               | `isSimple``()`<br>Checks if the path is simple (no self-crossing).                                                                                                                                                                                                                                                                                   |
    | `boolean`                               | `isTemporary``()`<br>Checks if the path is temporary.                                                                                                                                                                                                                                                                                                |
    | `boolean`                               | `isTspPath``()`<br>Checks if the path is a Tsp Path                                                                                                                                                                                                                                                                                                  |
    | `Path`                                  | `reverse``()`<br>Reverses the path and returns it.                                                                                                                                                                                                                                                                                                   |
    | `void`                                  | `setGeometry``(`[`JGeometry`](../geometry/JGeometry.md)` geom)`<br>Sets the path geometry (JGeometry).                                                                                                                                                                                                                                               |
    | `void`                                  | `setID``(int id)`<br>Sets the path ID.                                                                                                                                                                                                                                                                                                               |
    | `void`                                  | `setName``(java.lang.String name)`<br>Sets the path name.                                                                                                                                                                                                                                                                                            |
    | `void`                                  | `setType``(java.lang.String type)`<br>Sets the path type.                                                                                                                                                                                                                                                                                            |
    | `void`                                  | `setUserData``(java.lang.Object userData)`<br>Sets user defined data.                                                                                                                                                                                                                                                                                |
    | `void`                                  | `setUserData``(java.lang.String name, java.lang.Object data)`<br>Sets user data                                                                                                                                                                                                                                                                      |
    | `int`                                   | `size``()`<br>Returns the number of links in the path                                                                                                                                                                                                                                                                                                |
    | `java.util.ArrayList`                   | `subtract``(java.util.ArrayList pathList)`<br>Subtracts a list of paths from the path.                                                                                                                                                                                                                                                               |
    | `java.util.ArrayList`                   | `subtract``(Path path)`<br>Subtracts a given from the path.                                                                                                                                                                                                                                                                                          |
    | `void`                                  | `validate``()`<br>Validates the path.                                                                                                                                                                                                                                                                                                                |

    - ### Methods inherited from interface java.lang.Comparable

      `compareTo`

<!-- -->

- - ### Method Detail

    - #### getID

          int getID()

      Returns the path ID.

    <!-- -->

    - #### setID

          void setID(int id)
              throws NetworkDataException

      Sets the path ID.
      Parameters:
      `id` - the path ID to be set

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### getName

          java.lang.String getName()

      Returns the path name.

    <!-- -->

    - #### setName

          void setName(java.lang.String name)

      Sets the path name.
      Parameters:
      `name` - the path name to be set

    <!-- -->

    - #### getType

          java.lang.String getType()

      Returns the path type.

    <!-- -->

    - #### setType

          void setType(java.lang.String type)

      Sets the path type.
      Parameters:
      `type` - the path type to be set

    <!-- -->

    - #### getLinkAt

          Link getLinkAt(int index)

    <!-- -->

    - #### getNodeAt

          Node getNodeAt(int index)

      Returns the specified node of the path.
      Parameters:
      `index` - the specified node position

    <!-- -->

    - #### isClosed

          boolean isClosed()

      Checks if the path is closed.

    <!-- -->

    - #### getStartNode

          Node getStartNode()

      Returns the start node of the path.

    <!-- -->

    - #### getEndNode

          Node getEndNode()

      Returns the end node of the path.

    <!-- -->

    - #### getNetwork

          Network getNetwork()

      Returns the network that contains the path.

    <!-- -->

    - #### getLinkArray

          Link[] getLinkArray()

      Returns the path links as an array.

    <!-- -->

    - #### getLinks

          java.util.Iterator getLinks()

      Returns the path links as an Iterator.

    <!-- -->

    - #### getNodeArray

          Node[] getNodeArray()

      Returns the path nodes as an array.

    <!-- -->

    - #### getNodes

          java.util.Iterator getNodes()

      Returns the path nodes as an Iterator.

    <!-- -->

    - #### getNoOfLinks

          int getNoOfLinks()

      Returns the number of links in the path.

    <!-- -->

    - #### size

          int size()

      Returns the number of links in the path

    <!-- -->

    - #### getCost

          double getCost()

      Returns the path cost.

    <!-- -->

    - #### isConnected

          boolean isConnected(Path path)

      Checks if the path is connected.

    <!-- -->

    - #### isSimple

          boolean isSimple()

      Checks if the path is simple (no self-crossing).

    <!-- -->

    - #### isTemporary

          boolean isTemporary()

      Checks if the path is temporary.

    <!-- -->

    - #### contains

          boolean contains(Node n)

      Checks if the path contains the specified node.
      Parameters:
      `n` - the specified node

    <!-- -->

    - #### contains

          boolean contains(Link l)

      Checks if the path contains the specified link.
      Parameters:
      `l` - the specified link

    <!-- -->

    - #### contains

          boolean contains(Path path)

      Checks if the path contains the specified path.
      Parameters:
      `path` - the specified path

    <!-- -->

    - #### clone

          java.lang.Object clone()

      Clones the path.

    <!-- -->

    - #### getGeometry

          JGeometry getGeometry()

      Returns the path geometry (JGeometry).

    <!-- -->

    - #### setGeometry

          void setGeometry(JGeometry geom)

      Sets the path geometry (JGeometry).

    <!-- -->

    - #### isLogical

          boolean isLogical()

      Chceks if the path is logical.

    <!-- -->

    - #### isActive

          boolean isActive()

      Checks if the path is active.

    <!-- -->

    - #### getUserData

          java.lang.Object getUserData()

      Gets user defined data.
      Returns:
      userData the user data.

    <!-- -->

    - #### setUserData

          void setUserData(java.lang.Object userData)

      Sets user defined data.
      Parameters:
      `userData` - the user data.

    <!-- -->

    - #### getState

          boolean getState()

      Gets the path state.

    <!-- -->

    - #### computeGeometry

          void computeGeometry(double tolerance)

      Computes the path geometry from its link geometries. The tolerance is used for comparing path node geometry and end point geometry of path links. Link geometry is reversed if needed so that it is consistent with path direction.
      Parameters:
      `tolerance` - the tolerance for testing if two points are the same.

    <!-- -->

    - #### getDuration

          double getDuration()

      Gets path duration information

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

    - #### isTspPath

          boolean isTspPath()

      Checks if the path is a Tsp Path

    <!-- -->

    - #### getTspNodeOrder

          Node[] getTspNodeOrder()

      Returns the TSP path node visit order in an array of Node This information is only used for TSP related analysis

    <!-- -->

    - #### getTspNodeDuration

          double[][] getTspNodeDuration()

      Returns the TSP path node duration in an array of double The order of the duration is the same as the one in getTSPNodeNodeOrder() the duration is returned as an array of two doubles duration\[i\]\[0\] represents the arrival duration for the i-th TSP node and This information is only used for TSP related analys

    <!-- -->

    - #### extendPath

          void extendPath(Link newStartLink,
                          Link newEndLink)
                   throws NetworkDataException

      Extends the path by adding a new start link and a new end link The given links must be topologically connected to the path or an exception will be thrown No extension in the specific direction (start or end) if a null link is given
      Parameters:
      `newStartLink` - new start link which will be insert at the start of the path null if none added

      `newEndLink` - new end link that will be insert at the end of the path null if none added

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### isLinkReversed

          boolean isLinkReversed(int linkIndex)

      Checks if the given i-th link in the path is reversed in the path direction
      Parameters:
      `linkIndex` - the given link index in the path

      Returns:
      true if the link is reversed in the path, false otherwise

    <!-- -->

    - #### isLinkGeometryReversed

          boolean isLinkGeometryReversed(int linkIndex,
                                         double tolerance)

      Checks if the given i-th link geometry in the path is reversed in the path direction
      Parameters:
      `linkIndex` - the given link index in the path

      `tolerance` - tolerance for end point comparasion

      Returns:
      true if the link geometry is reversed in the path, false otherwise

    <!-- -->

    - #### indexOf

          int indexOf(Link link)

      Returns the link index of the given link in the path
      Parameters:
      `link` - given link in the path

      Returns:
      link index starting from 0, -1 if not in the path

    <!-- -->

    - #### indexOf

          int indexOf(Link link,
                      int fromIndex)

      Returns the link index of the given link in the path starting from fromIndex
      Parameters:
      `link` - link given link in the path

      `fromIndex` - starting index

      Returns:
      link index starting from 0, -1 if not in the path

    <!-- -->

    - #### indexOf

          int indexOf(Node node)

      Returns the node index of the given node in the path
      Parameters:
      `node` - given node in the path

      Returns:
      node index starting from 0, -1 if no in the path

    <!-- -->

    - #### indexOf

          int indexOf(Node node,
                      int fromIndex)

      Returns the node index of the given node in the path starting from fromIndex
      Parameters:
      `node` - given node in the path

      `fromIndex` - starting index

      Returns:
      node index starting from 0, -1 if no in the path

    <!-- -->

    - #### getSubPath

          Path getSubPath(int startNodeIndex,
                          int endNodeIndex)

      Returns the sub-path between startNodeIndex and ednNodeIndex
      Parameters:
      `startNodeIndex` - start node index

      `endNodeIndex` - end node index

      Returns:
      sub-path bound by the start and end node index

    <!-- -->

    - #### getCommonLinks

          java.util.ArrayList getCommonLinks(Path path)

      Returns the common links between two paths Note only links with consistent path direction will be returned
      Parameters:
      `path` - given path

      Returns:
      common links in a list

    <!-- -->

    - #### getCommonNodes

          java.util.ArrayList getCommonNodes(Path path)

      Returns the common nodes between two paths
      Parameters:
      `path` - given path

      Returns:
      common nodes in a list

    <!-- -->

    - #### getCommonSubPaths

          java.util.ArrayList getCommonSubPaths(Path path)
                                         throws NetworkDataException

      Returns the common sub-paths between two paths
      Parameters:
      `path` - the given path

      Returns:
      the common sub-paths in a list

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### validate

          void validate()
                 throws NetworkDataException

      Validates the path. It throws an exception if the path is not valid
      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### add

          java.util.ArrayList add(Path path)
                           throws NetworkDataException

      Adds a given path to the path. If these two paths can be merged as a simple connected path, the merged path is returned. Otherwise both paths are returned. Common links are ignored in the merged path.
      Parameters:
      `path` - given path

      Returns:
      merged path or original paths in a list

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### add

          java.util.ArrayList add(java.util.ArrayList pathList)
                           throws NetworkDataException

      Adds a list of paths to the path. Paths that can be merged are merged and returnded. Note the result is indepdent of the path order in the given list
      Parameters:
      `pathList` - the given path list

      Returns:
      a list of merged path(s)

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### subtract

          java.util.ArrayList subtract(Path path)
                                throws NetworkDataException

      Subtracts a given from the path. The result is returned in a list
      Parameters:
      `path` - given path

      Returns:
      a path list

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### subtract

          java.util.ArrayList subtract(java.util.ArrayList pathList)
                                throws NetworkDataException

      Subtracts a list of paths from the path. The result is returned in a list
      Parameters:
      `pathList` - given path list

      Returns:
      a path list

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### isSameDirection

          boolean isSameDirection(Path path)

      Checks if two paths the have same direction (indicated by the path node orde). The checking is based on the common links and nodes of the two paths. Paths don not have common links or nodes are considered to have different directions.
      Parameters:
      `path` - given path

      Returns:
      true if these two paths have the same direction, false otherwise

    <!-- -->

    - #### reverse

          Path reverse()
                throws NetworkDataException

      Reverses the path and returns it. If the reverse cannot be done , an exception is thrown. Paths that are made of bi-directed links are always reversible. Paths that are made of directed links might not be reversible if there is no reverse link for all path links. Path links with more than one reverse links are returned randomly.
      Returns:
      the reverse path

      Throws:
      [`NetworkDataException`](NetworkDataException.md) - if the path cannot be reversed

    <!-- -->

    - #### isReversePath

          boolean isReversePath(Path path)

      Checks if the given path is the reverse path of the path
      Parameters:
      `path` - given path

      Returns:
      true if the given path is the reverse path of the path, false otherwise

    <!-- -->

    - #### isSamePath

          boolean isSamePath(Path path)

      Checks if the given path has the same path links
      Parameters:
      `path` - given path

      Returns:
      true if two path have the same path links, false otherwise

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

- [Prev Class](OraTst.md)
- [Next Class](SDODimArray.md)

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
