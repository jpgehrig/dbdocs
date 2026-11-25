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

- [Prev Class](HistoryMetadata.md)
- [Next Class](LinkCostFunction.md)

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

## Interface Link

- All Superinterfaces:
  java.lang.Cloneable, java.lang.Comparable, java.io.Serializable

  ------------------------------------------------------------------------



      public interface Link
      extends java.lang.Cloneable, java.io.Serializable, java.lang.Comparable

  This interface defines a network link.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                       | Method and Description                                                                                                                                                                                              |
    |-----------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                      | `clone``()`<br>Clones the link.                                                                                                                                                                                     |
    | `double[]`                              | `computeDistanceRatio``(double x, double y)`<br>Computes the distance ratio along a spatial link geometry.                                                                                                          |
    | `double`                                | `getActualCost``()`<br>Returns the cost stored in Link object This function can be used to return the cost stored in the Link object if the getCost() method is overridden by a LinkCostFunction provided by users. |
    | `Link[]`                                | `getChildLinkArray``()`<br>Returns the child links as an array.                                                                                                                                                     |
    | `java.util.Iterator`                    | `getChildLinks``()`<br>Returns the child links as an Iterator.                                                                                                                                                      |
    | `Link[]`                                | `getCoLinks``()`<br>Returns the co-links as an array.                                                                                                                                                               |
    | `double`                                | `getCost``()`<br>Returns the link cost.                                                                                                                                                                             |
    | `double`                                | `getDuration``()`<br>Gets link duration information                                                                                                                                                                 |
    | `double`                                | `getEndMeasure``()`<br>Gets the end measure of the referenced LRS geometry.                                                                                                                                         |
    | [`Node`](Node.md)                       | `getEndNode``()`<br>Returns the end node.                                                                                                                                                                           |
    | `double`                                | `getEndPercentage``()`<br>Returns the end percentage if the link is created based on an existing link                                                                                                               |
    | `double`                                | `getFlow``()`<br>Returns the flow on the link after flow analysis                                                                                                                                                   |
    | [`JGeometry`](../geometry/JGeometry.md) | `getGeometry``()`<br>Returns the link geometry (JGeometry).                                                                                                                                                         |
    | `int`                                   | `getGeomID``()`<br>Returns the LRS geometry ID.                                                                                                                                                                     |
    | `int`                                   | `getID``()`<br>Returns the link ID.                                                                                                                                                                                 |
    | `int`                                   | `getLinkLevel``()`<br>Returns the link level.                                                                                                                                                                       |
    | `java.lang.String`                      | `getName``()`<br>Returns the link name.                                                                                                                                                                             |
    | [`Network`](Network.md)                 | `getNetwork``()`<br>Returns the network that contains the link.                                                                                                                                                     |
    | `int`                                   | `getNoOfChildLinks``()`<br>Gets number of child links Returns 0 if the network is a non-hierarchical network                                                                                                        |
    | `int`                                   | `getNoOfSibilingLinks``()`<br>Gets number of sibling links Sibling links are links with the same parent                                                                                                             |
    | `Link`                                  | `getParentLink``()`<br>Returns the parent link.                                                                                                                                                                     |
    | `int`                                   | `getPartitionID``()`<br>Returns the link partition ID                                                                                                                                                               |
    | `Link`                                  | `getReferenceLink``()`<br>Gets the reference link if the link is created based on an existing link.                                                                                                                 |
    | `Link[]`                                | `getSiblingLinkArray``()`<br>Retunrs the sibling links as a Link array.                                                                                                                                             |
    | `java.util.Iterator`                    | `getSiblings``()`<br>Returns the sibling links as an Iterator.                                                                                                                                                      |
    | `double`                                | `getStartMeasure``()`<br>Gets the start measure of the referenced LRS geometry.                                                                                                                                     |
    | [`Node`](Node.md)                       | `getStartNode``()`<br>Returns the start node.                                                                                                                                                                       |
    | `double`                                | `getStartPercentage``()`<br>Returns the start percentage if the link is created based on an existing link                                                                                                           |
    | `boolean`                               | `getState``()`<br>Returns the link state.                                                                                                                                                                           |
    | `java.lang.String`                      | `getType``()`<br>Returns the link type.                                                                                                                                                                             |
    | `java.lang.Object`                      | `getUserData``()`<br>Gets the user defined data.                                                                                                                                                                    |
    | `java.lang.Object`                      | `getUserData``(java.lang.String name)`<br>Gets user data                                                                                                                                                            |
    | `boolean`                               | `isActive``()`<br>Checks if the link is active.                                                                                                                                                                     |
    | `boolean`                               | `isBidirected``()`<br>Checks if the link is bidiretced                                                                                                                                                              |
    | `boolean`                               | `isLogical``()`<br>Checks if the link is logical.                                                                                                                                                                   |
    | `boolean`                               | `isTemporary``()`<br>Checks if the link is temporary.                                                                                                                                                               |
    | `boolean`                               | `isUnidirected``()`<br>Checks if the link is uni-diretced                                                                                                                                                           |
    | [`MDPoint`](MDPoint.md)                 | `locatePoint``(double distanceRatio)`<br>Returns the (linearly interpreted) point on the link geometry of the given distance ratio.                                                                                 |
    | `void`                                  | `makeTemporary``()`<br>Makes the link temporary.                                                                                                                                                                    |
    | [`MDPoint`](MDPoint.md)`[]`             | `nearestPoint``(double x, double y)`<br>Returns the nearest point on the link geometry.                                                                                                                             |
    | [`Node`](Node.md)                       | `otherNode``(`[`Node`](Node.md)` node)`<br>Returns the other node of the link, if the start node = node, the end node is returned.                                                                                  |
    | `void`                                  | `setBidirected``(boolean isBidirected)`<br>Makes the directed link bidirected                                                                                                                                       |
    | `void`                                  | `setCost``(double cost)`<br>Sets the link cost.                                                                                                                                                                     |
    | `void`                                  | `setDuration``(double duration)`<br>Sets the link duration                                                                                                                                                          |
    | `void`                                  | `setEndNode``(`[`Node`](Node.md)` node)`<br>Sets the link end node.                                                                                                                                                 |
    | `void`                                  | `setFlow``(double flow)`<br>Sets the flow on the link for flow analysis                                                                                                                                             |
    | `void`                                  | `setGeometry``(`[`JGeometry`](../geometry/JGeometry.md)` geom)`<br>Sets the link geometry (JGeometry).                                                                                                              |
    | `void`                                  | `setGeomID``(int id)`<br>Sets the LRS geometry ID of this link.                                                                                                                                                     |
    | `void`                                  | `setLinkLevel``(int level)`<br>Sets the link level.                                                                                                                                                                 |
    | `void`                                  | `setMeasure``(double startMeasure, double endMeasure)`<br>Sets the LRS start and end measures.                                                                                                                      |
    | `void`                                  | `setName``(java.lang.String name)`<br>Sets the link name.                                                                                                                                                           |
    | `void`                                  | `setParentLink``(Link link)`<br>Sets the parent link.                                                                                                                                                               |
    | `void`                                  | `setPartitionID``(int partitionID)`<br>Sets the link partition ID                                                                                                                                                   |
    | `void`                                  | `setStartNode``(`[`Node`](Node.md)` node)`<br>Sets the link start node.                                                                                                                                             |
    | `void`                                  | `setState``(boolean state)`<br>Sets the active flag.                                                                                                                                                                |
    | `void`                                  | `setType``(java.lang.String type)`<br>Sets the link type.                                                                                                                                                           |
    | `void`                                  | `setUserData``(java.lang.Object userData)`<br>Sets the user defined data.                                                                                                                                           |
    | `void`                                  | `setUserData``(java.lang.String name, java.lang.Object data)`<br>Sets user data                                                                                                                                     |

    - ### Methods inherited from interface java.lang.Comparable

      `compareTo`

<!-- -->

- - ### Method Detail

    - #### getID

          int getID()

      Returns the link ID.

    <!-- -->

    - #### getName

          java.lang.String getName()

      Returns the link name.

    <!-- -->

    - #### getStartNode

          Node getStartNode()

      Returns the start node.

    <!-- -->

    - #### getEndNode

          Node getEndNode()

      Returns the end node.

    <!-- -->

    - #### getCost

          double getCost()

      Returns the link cost.

    <!-- -->

    - #### getState

          boolean getState()

      Returns the link state.

    <!-- -->

    - #### getLinkLevel

          int getLinkLevel()

      Returns the link level.

    <!-- -->

    - #### getType

          java.lang.String getType()

      Returns the link type.

    <!-- -->

    - #### getNetwork

          Network getNetwork()

      Returns the network that contains the link.

    <!-- -->

    - #### getGeometry

          JGeometry getGeometry()

      Returns the link geometry (JGeometry).
      See Also:
      [`JGeometry`](../geometry/JGeometry.md)

    <!-- -->

    - #### getCoLinks

          Link[] getCoLinks()

      Returns the co-links as an array. The co-link of a given link is defined as a link with reverse direction. i.e. the start node of the co-link = the end node of the link, and the end node of the co-link = the start node of the link.

    <!-- -->

    - #### getParentLink

          Link getParentLink()

      Returns the parent link.

    <!-- -->

    - #### getChildLinkArray

          Link[] getChildLinkArray()

      Returns the child links as an array.

    <!-- -->

    - #### getChildLinks

          java.util.Iterator getChildLinks()

      Returns the child links as an Iterator.

    <!-- -->

    - #### setLinkLevel

          void setLinkLevel(int level)

      Sets the link level.
      Parameters:
      `level` - the link level to be set

    <!-- -->

    - #### setType

          void setType(java.lang.String type)

      Sets the link type.
      Parameters:
      `type` - the link type to be set

    <!-- -->

    - #### setCost

          void setCost(double cost)

      Sets the link cost.
      Parameters:
      `cost` - the link cost to be set

    <!-- -->

    - #### setName

          void setName(java.lang.String name)

      Sets the link name.
      Parameters:
      `name` - the link name to be set

    <!-- -->

    - #### setStartNode

          void setStartNode(Node node)

      Sets the link start node.
      Parameters:
      `node` - the start node of the link

    <!-- -->

    - #### setEndNode

          void setEndNode(Node node)

      Sets the link end node.
      Parameters:
      `node` - the end node of the link

    <!-- -->

    - #### setGeometry

          void setGeometry(JGeometry geom)

      Sets the link geometry (JGeometry).
      Parameters:
      `geom` - the geometry of the link

      See Also:
      [`JGeometry`](../geometry/JGeometry.md)

    <!-- -->

    - #### setParentLink

          void setParentLink(Link link)

      Sets the parent link.
      Parameters:
      `link` - parent link to be set

    <!-- -->

    - #### isTemporary

          boolean isTemporary()

      Checks if the link is temporary.
      Returns:
      true if the link is temporary, false otherwise

    <!-- -->

    - #### makeTemporary

          void makeTemporary()

      Makes the link temporary.

    <!-- -->

    - #### otherNode

          Node otherNode(Node node)

      Returns the other node of the link, if the start node = node, the end node is returned. If the the end node = node, the start node is returned.
      Parameters:
      `node` - the specified end node.

    <!-- -->

    - #### setGeomID

          void setGeomID(int id)

      Sets the LRS geometry ID of this link.
      Parameters:
      `id` - the LRS geometry ID

    <!-- -->

    - #### getGeomID

          int getGeomID()

      Returns the LRS geometry ID.
      Returns:
      the LRS geometry ID

    <!-- -->

    - #### setMeasure

          void setMeasure(double startMeasure,
                          double endMeasure)

      Sets the LRS start and end measures.
      Parameters:
      `startMeasure` - the start measure of the referenced LRS geometry

      `endMeasure` - the end measure of the referenced LRS geometry

    <!-- -->

    - #### getStartMeasure

          double getStartMeasure()

      Gets the start measure of the referenced LRS geometry.
      Returns:
      the start measure of the referenced LRS geometry

    <!-- -->

    - #### getEndMeasure

          double getEndMeasure()

      Gets the end measure of the referenced LRS geometry.
      Returns:
      the end measure of the referenced LRS geometry

    <!-- -->

    - #### isLogical

          boolean isLogical()

      Checks if the link is logical.

    <!-- -->

    - #### isActive

          boolean isActive()

      Checks if the link is active.

    <!-- -->

    - #### isBidirected

          boolean isBidirected()

      Checks if the link is bidiretced

    <!-- -->

    - #### isUnidirected

          boolean isUnidirected()

      Checks if the link is uni-diretced

    <!-- -->

    - #### setBidirected

          void setBidirected(boolean isBidirected)

      Makes the directed link bidirected

    <!-- -->

    - #### getUserData

          java.lang.Object getUserData()

      Gets the user defined data.
      Returns:
      userData the user data as an Object

    <!-- -->

    - #### setUserData

          void setUserData(java.lang.Object userData)

      Sets the user defined data.
      Parameters:
      `userData` - the user data as an Object

    <!-- -->

    - #### setState

          void setState(boolean state)

      Sets the active flag.
      Parameters:
      `state` - true if active, false otherwise

    <!-- -->

    - #### clone

          java.lang.Object clone()

      Clones the link.

    <!-- -->

    - #### getSiblings

          java.util.Iterator getSiblings()

      Returns the sibling links as an Iterator.

    <!-- -->

    - #### getSiblingLinkArray

          Link[] getSiblingLinkArray()

      Retunrs the sibling links as a Link array.

    <!-- -->

    - #### getFlow

          double getFlow()

      Returns the flow on the link after flow analysis

    <!-- -->

    - #### setFlow

          void setFlow(double flow)

      Sets the flow on the link for flow analysis

    <!-- -->

    - #### getDuration

          double getDuration()

      Gets link duration information

    <!-- -->

    - #### setDuration

          void setDuration(double duration)

      Sets the link duration

    <!-- -->

    - #### getPartitionID

          int getPartitionID()

      Returns the link partition ID

    <!-- -->

    - #### setPartitionID

          void setPartitionID(int partitionID)

      Sets the link partition ID
      Parameters:
      `partitionID` - link partition ID

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

    - #### nearestPoint

          MDPoint[] nearestPoint(double x,
                                 double y)
                          throws NetworkDataException

      Returns the nearest point on the link geometry. It throws a NetworkDataException if the link is not a spatial link. It works on linestring geometry only If there exist multiple points with the same minimum distance. All of them will be returned.
      Parameters:
      `x` - first ordinate of the given point.

      `y` - second ordinate of the given point.

      Returns:
      the point(s) (MDPoint array) on the link geometry that has the minimum euclidean distance.

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### computeDistanceRatio

          double[] computeDistanceRatio(double x,
                                        double y)
                                 throws NetworkDataException

      Computes the distance ratio along a spatial link geometry. The given point can be on or off the given link geometry. If the point is off the link geometry, a snap operation is performed to the point(s) on the link geometry that has the minimum distance to the given point (x,y). If there exist multiple points with the same minimum distance, all of them will be returned. It works on linestring geometry only. The (Euclidean) distance is computed from the start point of the link geometry. The distance ratio is the distance divided by the link geometry length. For non-spatial links, a NetworkDataException will be thrown.
      Parameters:
      `x` - first ordinate of the given point

      `y` - second ordinate of the given point

      Returns:
      the distance ratio array (between 0.0 and 1.0 inclusive)

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### locatePoint

          MDPoint locatePoint(double distanceRatio)
                       throws NetworkDataException

      Returns the (linearly interpreted) point on the link geometry of the given distance ratio. The (Euclidean) distance ratio is between 0.0 and 1.0 The ratio is defined as the distance from the start point to this point over the distance (length) of the link geometry. This function works on linestring geometry. It throws a NetworkDataException if the link is non-spatial or non-linestring geometry
      Parameters:
      `distanceRatio` - the distance ratio (Euclidean distance)

      Returns:
      the point (MDPoint) identified by the given distance ratio

      Throws:
      [`NetworkDataException`](NetworkDataException.md)

    <!-- -->

    - #### getNoOfChildLinks

          int getNoOfChildLinks()

      Gets number of child links Returns 0 if the network is a non-hierarchical network

    <!-- -->

    - #### getNoOfSibilingLinks

          int getNoOfSibilingLinks()

      Gets number of sibling links Sibling links are links with the same parent

    <!-- -->

    - #### getReferenceLink

          Link getReferenceLink()

      Gets the reference link if the link is created based on an existing link. Such links are further identified by a start percentage and end percentage.

    <!-- -->

    - #### getStartPercentage

          double getStartPercentage()

      Returns the start percentage if the link is created based on an existing link

    <!-- -->

    - #### getEndPercentage

          double getEndPercentage()

      Returns the end percentage if the link is created based on an existing link

    <!-- -->

    - #### getActualCost

          double getActualCost()

      Returns the cost stored in Link object This function can be used to return the cost stored in the Link object if the getCost() method is overridden by a LinkCostFunction provided by users.
      Returns:
      cost stored in the link object

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

- [Prev Class](HistoryMetadata.md)
- [Next Class](LinkCostFunction.md)

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
