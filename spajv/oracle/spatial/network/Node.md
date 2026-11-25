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

- [Prev Class](NetworkMetadata.md)
- [Next Class](OraTst.md)

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

## Interface Node

- All Superinterfaces:
  java.lang.Cloneable, java.lang.Comparable, [MDPoint](MDPoint.md), java.io.Serializable

  ------------------------------------------------------------------------



      public interface Node
      extends MDPoint, java.lang.Cloneable, java.io.Serializable, java.lang.Comparable

  This interface defines a network node.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                       | Method and Description                                                                                                                    |
    |-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                      | `clone``()`<br>Clones a node.                                                                                                             |
    | [`Link`](Link.md)`[]`                   | `findLinks``(Node endNode)`<br>Finds the links that connect current node to the specified node.                                           |
    | `Node[]`                                | `getAdjacentNodeArray``()`<br>Returns the adjacent nodes as an array.                                                                     |
    | `java.util.Iterator`                    | `getAdjacentNodes``()`<br>Returns the adjacent nodes as an Iterator.                                                                      |
    | `Node[]`                                | `getChildNodeArray``()`<br>Returns the child nodes as an array.                                                                           |
    | `java.util.Iterator`                    | `getChildNodes``()`<br>Returns the child nodes as an Iterator.                                                                            |
    | `int`                                   | `getComponentNo``()`<br>Returns the node component number.                                                                                |
    | `double`                                | `getCost``()`<br>Returns the node cost.                                                                                                   |
    | `int`                                   | `getDegree``()`<br>Gets the degree(number of links taht connect to the node) of a node                                                    |
    | `double`                                | `getDuration``()`<br>Gets node duration information                                                                                       |
    | [`JGeometry`](../geometry/JGeometry.md) | `getGeometry``()`<br>Returns the point geometry (JGeometry).                                                                              |
    | `int`                                   | `getGeomID``()`<br>Returns the LRS geomeetry ID.                                                                                          |
    | `int`                                   | `getHierarchyLevel``()`<br>Returns the node hierarchy level.                                                                              |
    | `int`                                   | `getID``()`<br>Returns the node ID.                                                                                                       |
    | [`Link`](Link.md)`[]`                   | `getIncidentLinks``()`<br>Returns the incident links of the node as an array.                                                             |
    | `int`                                   | `getInDegree``()`<br>Gets the in-degree of the node in a directed network                                                                 |
    | [`Link`](Link.md)`[]`                   | `getInLinks``()`<br>Returns the in-links of the node as an array.                                                                         |
    | [`MDPoint`](MDPoint.md)                 | `getMDPoint``()`<br>Returns the MDpoint of the node.                                                                                      |
    | `double`                                | `getMeasure``()`<br>Returns the LRS measure.                                                                                              |
    | `java.lang.String`                      | `getName``()`<br>Returns the node name.                                                                                                   |
    | [`Network`](Network.md)                 | `getNetwork``()`<br>Returns the network that contains the node.                                                                           |
    | [`Link`](Link.md)`[]`                   | `getNextLinks``()`<br>Returns Links that go out from this node in an array for directed networks, these links are out-links of this nodes |
    | `int`                                   | `getNoOfChildNodes``()`<br>Gets number of child nodes Returns 0 if the network is a non-hierarchical network                              |
    | `int`                                   | `getNoOfSibilingNodes``()`<br>Gets number of sibling nodes Sibling nodes are nodes with the same parent                                   |
    | `int`                                   | `getOutDegree``()`<br>Gets the out-degree of the node in a directed network                                                               |
    | [`Link`](Link.md)`[]`                   | `getOutLinks``()`<br>Returns the out-links of the node as an array.                                                                       |
    | `Node`                                  | `getParentNode``()`<br>Returns the parent node.                                                                                           |
    | `int`                                   | `getPartitionID``()`<br>Returns the node partition ID.                                                                                    |
    | `double`                                | `getPercentage``()`<br>Returns the percentage if the node is created based on an existing link                                            |
    | [`Link`](Link.md)`[]`                   | `getPrevLinks``()`<br>Returns Links that come into this node in an array for directed networks, these links are in-links of this nodes    |
    | [`Link`](Link.md)                       | `getReferenceLink``()`<br>Gets the reference link if the node is created based on an existing link.                                       |
    | `Node[]`                                | `getSiblingNodeArray``()`<br>Retunrs the sibling nodes as a Node array.                                                                   |
    | `java.util.Iterator`                    | `getSiblings``()`<br>Retunrs the sibling nodes as an Iterator.                                                                            |
    | `boolean`                               | `getState``()`<br>Returns the node state.                                                                                                 |
    | `java.lang.String`                      | `getType``()`<br>Returns the node type.                                                                                                   |
    | `java.lang.Object`                      | `getUserData``()`<br>Gets user defined data.                                                                                              |
    | `java.lang.Object`                      | `getUserData``(java.lang.String name)`<br>Gets user data                                                                                  |
    | `boolean`                               | `isActive``()`<br>Checks if the node is active.                                                                                           |
    | `boolean`                               | `isLogical``()`                                                                                                                           |
    | `boolean`                               | `isMarked``()`<br>Checks if the node is marked.                                                                                           |
    | `boolean`                               | `isTemporary``()`<br>Checks if the node is temporary.                                                                                     |
    | `boolean`                               | `linkExists``(Node endNode)`<br>Checks if the link is bound by the node and the specified nodes.                                          |
    | `void`                                  | `makeTemporary``()`<br>Makes the node temporary.                                                                                          |
    | `void`                                  | `setComponentNo``(int no)`<br>Sets the node component number.                                                                             |
    | `void`                                  | `setCost``(double cost)`<br>Sets the node cost.                                                                                           |
    | `void`                                  | `setDuration``(double duration)`<br>Sets the node duration                                                                                |
    | `void`                                  | `setGeometry``(`[`JGeometry`](../geometry/JGeometry.md)` geom)`<br>Sets the node geometry (JGeometry).                                    |
    | `void`                                  | `setGeomID``(int id)`<br>Sets the LRS geometry ID.                                                                                        |
    | `void`                                  | `setHierarchyLevel``(int id)`<br>Sets the node hierarchy level.                                                                           |
    | `void`                                  | `setMDPoint``(`[`MDPoint`](MDPoint.md)` pt)`<br>Sets the node location (MDPoint).                                                         |
    | `void`                                  | `setMeasure``(double measure)`<br>Sets the LRS measure.                                                                                   |
    | `void`                                  | `setName``(java.lang.String name)`<br>Sets the node name.                                                                                 |
    | `void`                                  | `setParentNode``(Node node)`<br>Sets the parent node.                                                                                     |
    | `void`                                  | `setPartitionID``(int id)`<br>Sets the node partition ID.                                                                                 |
    | `void`                                  | `setState``(boolean state)`<br>Sets the active flag.                                                                                      |
    | `void`                                  | `setType``(java.lang.String type)`<br>Sets the node type.                                                                                 |
    | `void`                                  | `setUserData``(java.lang.Object userData)`<br>Sets user defined data.                                                                     |
    | `void`                                  | `setUserData``(java.lang.String name, java.lang.Object data)`<br>Sets user data                                                           |

    - ### Methods inherited from interface oracle.spatial.network.[MDPoint](MDPoint.md)

      [`distance`](MDPoint.md)`, `[`geodeticDistanceInMeters`](MDPoint.md)`, `[`getNoOfDims`](MDPoint.md)`, `[`getOrd`](MDPoint.md)`, `[`getOrd`](MDPoint.md)`, `[`getSrid`](MDPoint.md)`, `[`inside`](MDPoint.md)`, `[`inside`](MDPoint.md)`, `[`setOrd`](MDPoint.md)`, `[`setSrid`](MDPoint.md)`, `[`toArray`](MDPoint.md)`, `[`toGeometry`](MDPoint.md)`, `[`toSDOGeometry`](MDPoint.md)

    <!-- -->

    - ### Methods inherited from interface java.lang.Comparable

      `compareTo`

<!-- -->

- - ### Method Detail

    - #### getID

          int getID()

      Returns the node ID.

    <!-- -->

    - #### getName

          java.lang.String getName()

      Returns the node name.

    <!-- -->

    - #### getType

          java.lang.String getType()

      Returns the node type.

    <!-- -->

    - #### getCost

          double getCost()

      Returns the node cost.

    <!-- -->

    - #### getComponentNo

          int getComponentNo()

      Returns the node component number.

    <!-- -->

    - #### getInLinks

          Link[] getInLinks()

      Returns the in-links of the node as an array.

    <!-- -->

    - #### getOutLinks

          Link[] getOutLinks()

      Returns the out-links of the node as an array.

    <!-- -->

    - #### getIncidentLinks

          Link[] getIncidentLinks()

      Returns the incident links of the node as an array.

    <!-- -->

    - #### getState

          boolean getState()

      Returns the node state.

    <!-- -->

    - #### getNetwork

          Network getNetwork()

      Returns the network that contains the node.

    <!-- -->

    - #### getMDPoint

          MDPoint getMDPoint()

      Returns the MDpoint of the node.

    <!-- -->

    - #### getGeometry

          JGeometry getGeometry()

      Returns the point geometry (JGeometry).

    <!-- -->

    - #### getHierarchyLevel

          int getHierarchyLevel()

      Returns the node hierarchy level.

    <!-- -->

    - #### getPartitionID

          int getPartitionID()

      Returns the node partition ID.

    <!-- -->

    - #### getChildNodeArray

          Node[] getChildNodeArray()

      Returns the child nodes as an array.

    <!-- -->

    - #### getChildNodes

          java.util.Iterator getChildNodes()

      Returns the child nodes as an Iterator.

    <!-- -->

    - #### getParentNode

          Node getParentNode()

      Returns the parent node.

    <!-- -->

    - #### getGeomID

          int getGeomID()

      Returns the LRS geomeetry ID.

    <!-- -->

    - #### setGeomID

          void setGeomID(int id)

      Sets the LRS geometry ID.
      Parameters:
      `id` - the LRS geometry ID in the referenced LRS layer

    <!-- -->

    - #### getMeasure

          double getMeasure()

      Returns the LRS measure.

    <!-- -->

    - #### setMeasure

          void setMeasure(double measure)

      Sets the LRS measure.
      Parameters:
      `measure` - the LRS measure in the referenced LRS layer

    <!-- -->

    - #### setComponentNo

          void setComponentNo(int no)

      Sets the node component number.
      Parameters:
      `no` - the component number to be set

    <!-- -->

    - #### setName

          void setName(java.lang.String name)

      Sets the node name.
      Parameters:
      `name` - the node name to be set

    <!-- -->

    - #### setType

          void setType(java.lang.String type)

      Sets the node type.
      Parameters:
      `type` - the node type to be set

    <!-- -->

    - #### setCost

          void setCost(double cost)

      Sets the node cost.
      Parameters:
      `cost` - the node cost to be set

    <!-- -->

    - #### setMDPoint

          void setMDPoint(MDPoint pt)

      Sets the node location (MDPoint).
      Parameters:
      `pt` - the point location to be set

    <!-- -->

    - #### setGeometry

          void setGeometry(JGeometry geom)

      Sets the node geometry (JGeometry).
      Parameters:
      `geom` - the point geometry to be set

    <!-- -->

    - #### setHierarchyLevel

          void setHierarchyLevel(int id)

      Sets the node hierarchy level.
      Parameters:
      `id` - the hierarchy level to be set

    <!-- -->

    - #### setPartitionID

          void setPartitionID(int id)

      Sets the node partition ID.
      Parameters:
      `id` - the partition ID to be set

    <!-- -->

    - #### setParentNode

          void setParentNode(Node node)

      Sets the parent node.
      Parameters:
      `node` - the parent node to be set

    <!-- -->

    - #### isMarked

          boolean isMarked()

      Checks if the node is marked.

    <!-- -->

    - #### linkExists

          boolean linkExists(Node endNode)

      Checks if the link is bound by the node and the specified nodes.
      Parameters:
      `endNode` - the specified node

    <!-- -->

    - #### isTemporary

          boolean isTemporary()

      Checks if the node is temporary.

    <!-- -->

    - #### makeTemporary

          void makeTemporary()

      Makes the node temporary.

    <!-- -->

    - #### isLogical

          boolean isLogical()

    <!-- -->

    - #### isActive

          boolean isActive()

      Checks if the node is active.

    <!-- -->

    - #### getUserData

          java.lang.Object getUserData()

      Gets user defined data.
      Returns:
      userData the user data

    <!-- -->

    - #### setUserData

          void setUserData(java.lang.Object userData)

      Sets user defined data.
      Parameters:
      `userData` - the user data.

    <!-- -->

    - #### setState

          void setState(boolean state)

      Sets the active flag.
      Parameters:
      `state` - true if active, false otherwise

    <!-- -->

    - #### findLinks

          Link[] findLinks(Node endNode)

      Finds the links that connect current node to the specified node.
      Parameters:
      `endNode` - the specified node

    <!-- -->

    - #### getAdjacentNodeArray

          Node[] getAdjacentNodeArray()

      Returns the adjacent nodes as an array.

    <!-- -->

    - #### getAdjacentNodes

          java.util.Iterator getAdjacentNodes()

      Returns the adjacent nodes as an Iterator.

    <!-- -->

    - #### clone

          java.lang.Object clone()

      Clones a node.

    <!-- -->

    - #### getSiblings

          java.util.Iterator getSiblings()

      Retunrs the sibling nodes as an Iterator.

    <!-- -->

    - #### getSiblingNodeArray

          Node[] getSiblingNodeArray()

      Retunrs the sibling nodes as a Node array.

    <!-- -->

    - #### getDuration

          double getDuration()

      Gets node duration information

    <!-- -->

    - #### setDuration

          void setDuration(double duration)

      Sets the node duration

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

    - #### getNoOfChildNodes

          int getNoOfChildNodes()

      Gets number of child nodes Returns 0 if the network is a non-hierarchical network

    <!-- -->

    - #### getNoOfSibilingNodes

          int getNoOfSibilingNodes()

      Gets number of sibling nodes Sibling nodes are nodes with the same parent

    <!-- -->

    - #### getInDegree

          int getInDegree()

      Gets the in-degree of the node in a directed network

    <!-- -->

    - #### getOutDegree

          int getOutDegree()

      Gets the out-degree of the node in a directed network

    <!-- -->

    - #### getDegree

          int getDegree()

      Gets the degree(number of links taht connect to the node) of a node

    <!-- -->

    - #### getReferenceLink

          Link getReferenceLink()

      Gets the reference link if the node is created based on an existing link. Such nodes are further identified by percentage on the referenced link.

    <!-- -->

    - #### getPercentage

          double getPercentage()

      Returns the percentage if the node is created based on an existing link

    <!-- -->

    - #### getNextLinks

          Link[] getNextLinks()

      Returns Links that go out from this node in an array for directed networks, these links are out-links of this nodes

    <!-- -->

    - #### getPrevLinks

          Link[] getPrevLinks()

      Returns Links that come into this node in an array for directed networks, these links are in-links of this nodes

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

- [Prev Class](NetworkMetadata.md)
- [Next Class](OraTst.md)

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
