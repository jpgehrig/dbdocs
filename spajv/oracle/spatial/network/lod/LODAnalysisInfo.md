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

- [Prev Class](LinkNotFoundException.md)
- [Next Class](LODGoalNode.md)

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

## Class LODAnalysisInfo

- java.lang.Object

- - oracle.spatial.network.lod.LODAnalysisInfo

<!-- -->

- Direct Known Subclasses:
  [TspAnalysisInfo](TspAnalysisInfo.md)

  ------------------------------------------------------------------------



      public class LODAnalysisInfo
      extends java.lang.Object

  An instance of this class carries the analysis information.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                           | Method and Description                                                                             |
    |---------------------------------------------|----------------------------------------------------------------------------------------------------|
    | `double`                                    | `getCurrentCost``()`<br>Deprecated.                                                                |
    | `double[]`                                  | `getCurrentCosts``()`<br>Returns the costs of the current node.                                    |
    | `int`                                       | `getCurrentDepth``()`<br>Returns the path depth of the current node.                               |
    | [`LogicalNetLink`](LogicalNetLink.md)       | `getCurrentLink``()`<br>Returns the current link.                                                  |
    | [`LogicalNetNode`](LogicalNetNode.md)       | `getCurrentNode``()`<br>Returns the current node.                                                  |
    | `java.lang.Object[]`                        | `getCurrentUserObjects``()`<br>Returns the user objects that have been accumulated so far.         |
    | `int`                                       | `getDirection``()`<br>Returns the direction the network is being explored.                         |
    | [`LogicalNode`](LogicalNode.md)             | `getEndNode``()`<br>Deprecated. <br>use getEndPoints                                               |
    | [`HeavyPointOnNet`](HeavyPointOnNet.md)     | `getEndPoint``()`<br>Deprecated. <br>use getEndPoints                                              |
    | [`HeavyPointOnNet`](HeavyPointOnNet.md)`[]` | `getEndPoints``()`<br>Returns the end points.                                                      |
    | [`VisitedNode`](VisitedNode.md)             | `getExpandedNode``()`<br>Returns the node currently being expanded.                                |
    | `double`                                    | `getNextCost``()`<br>Returns the path cost of next node.                                           |
    | `double[]`                                  | `getNextCosts``()`<br>Returns the costs of next node.                                              |
    | `int`                                       | `getNextDepth``()`<br>Returns the path depth of the next node.                                     |
    | [`LogicalNetLink`](LogicalNetLink.md)       | `getNextLink``()`<br>Returns the next link.                                                        |
    | [`LogicalNetNode`](LogicalNetNode.md)       | `getNextNode``()`<br>Returns the next node.                                                        |
    | `java.lang.Object`                          | `getNextUserObject``()`<br>Returns the next user object.                                           |
    | [`LogicalNode`](LogicalNode.md)             | `getStartNode``()`<br>Deprecated. <br>use getStartPoints                                           |
    | [`HeavyPointOnNet`](HeavyPointOnNet.md)     | `getStartPoint``()`<br>Deprecated. <br>use getStartPoints                                          |
    | [`HeavyPointOnNet`](HeavyPointOnNet.md)`[]` | `getStartPoints``()`<br>Returns the start points.                                                  |
    | `void`                                      | `setDirection``(int direction)`<br>Sets the direction the network is being explored.               |
    | `void`                                      | `setNextUserObject``(java.lang.Object userObject)`<br>Sets the next user object to be accumulated. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getStartNode

          public LogicalNode getStartNode()

      Deprecated. use getStartPoints
      Returns the start node.

    <!-- -->

    - #### getEndNode

          public LogicalNode getEndNode()

      Deprecated. use getEndPoints
      Returns the end node.

    <!-- -->

    - #### getStartPoint

          public HeavyPointOnNet getStartPoint()

      Deprecated. use getStartPoints
      Returns the start point.

    <!-- -->

    - #### getEndPoint

          public HeavyPointOnNet getEndPoint()

      Deprecated. use getEndPoints
      Returns the end point.

    <!-- -->

    - #### getStartPoints

          public HeavyPointOnNet[] getStartPoints()

      Returns the start points.

    <!-- -->

    - #### getEndPoints

          public HeavyPointOnNet[] getEndPoints()

      Returns the end points.

    <!-- -->

    - #### getCurrentNode

          public LogicalNetNode getCurrentNode()

      Returns the current node.

    <!-- -->

    - #### getNextNode

          public LogicalNetNode getNextNode()

      Returns the next node.

    <!-- -->

    - #### getCurrentLink

          public LogicalNetLink getCurrentLink()

      Returns the current link.

    <!-- -->

    - #### getNextLink

          public LogicalNetLink getNextLink()

      Returns the next link.

    <!-- -->

    - #### getExpandedNode

          public VisitedNode getExpandedNode()

      Returns the node currently being expanded.
      Returns:

    <!-- -->

    - #### getCurrentDepth

          public int getCurrentDepth()

      Returns the path depth of the current node.

    <!-- -->

    - #### getNextDepth

          public int getNextDepth()

      Returns the path depth of the next node.

    <!-- -->

    - #### getCurrentCost

          public double getCurrentCost()

      Deprecated. 
      Returns the path cost of the current node.

    <!-- -->

    - #### getCurrentCosts

          public double[] getCurrentCosts()

      Returns the costs of the current node.

    <!-- -->

    - #### getNextCost

          public double getNextCost()

      Returns the path cost of next node.

    <!-- -->

    - #### getNextCosts

          public double[] getNextCosts()

      Returns the costs of next node.

    <!-- -->

    - #### getNextUserObject

          public java.lang.Object getNextUserObject()

      Returns the next user object.
      Returns:

    <!-- -->

    - #### setNextUserObject

          public void setNextUserObject(java.lang.Object userObject)

      Sets the next user object to be accumulated.
      Parameters:
      `userObject` -

    <!-- -->

    - #### getCurrentUserObjects

          public java.lang.Object[] getCurrentUserObjects()

      Returns the user objects that have been accumulated so far.
      Returns:

    <!-- -->

    - #### getDirection

          public int getDirection()

      Returns the direction the network is being explored.
      Returns:
      NetworkExplorer.DIRECTION_FORWARD or NetworkExplorer.DIRECTION_BACKWARD

    <!-- -->

    - #### setDirection

          public void setDirection(int direction)

      Sets the direction the network is being explored.
      Parameters:
      `direction` - NetworkExplorer.DIRECTION_FORWARD or NetworkExplorer.DIRECTION_BACKWARD

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

- [Prev Class](LinkNotFoundException.md)
- [Next Class](LODGoalNode.md)

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
