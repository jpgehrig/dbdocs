Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFEChangesKeeper.md)
- [Next Class](NFEConnectionDescriptor.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.model.edit

## Class NFEConnectableEdge\<V\>

- java.lang.Object

- - oracle.spatial.network.nfe.model.edit.NFEConnectableEdge\<V\>

<!-- -->

- Type Parameters:
  `V` - The type of edge. Typically it would be a Line Feature Element or a Link.

  ------------------------------------------------------------------------



      public class NFEConnectableEdge<V>
      extends java.lang.Object

  Represents an edge and the location (relative to the edge and as a point in space) where the connection must be performed.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                  |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `NFEConnectableEdge``()`<br>Allocates an empty connectable edge                                                                                                                              |
    | `NFEConnectableEdge``(V edge, java.awt.geom.Point2D connPoint, `[`IntersectionLocation`](../spatial/interaction/IntersectionLocation.md)` connInterLoc)`<br>Allocates a new connectable edge |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                        | Method and Description                                                                                                                                                                                                                     |
    |--------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`IntersectionLocation`](../spatial/interaction/IntersectionLocation.md) | `getConnectableIntersectionLocation``()`<br>Gets the location of edge where the connection will be performed.                                                                                                                              |
    | `java.awt.geom.Point2D`                                                  | `getConnectableSpatialPoint``()`<br>Gets the edge's point that will be connected                                                                                                                                                           |
    | `long`                                                                   | `getConnectingLinePointRuleId``()`<br>Gets the line point rule ID that will connect the edge                                                                                                                                               |
    | `V`                                                                      | `getEdge``()`<br>Gets the edge to be connected                                                                                                                                                                                             |
    | `void`                                                                   | `setConnectableIntersectionLocation``(`[`IntersectionLocation`](../spatial/interaction/IntersectionLocation.md)` connectableIntersectionLocation)`<br>Sets the location (as a fixed value) of edge where the connection will be performed. |
    | `void`                                                                   | `setConnectableSpatialPoint``(java.awt.geom.Point2D connectableSpatialPoint)`<br>Sets the edge's point that will be connected                                                                                                              |
    | `void`                                                                   | `setConnectingLinePointRuleId``(long connLPRuleId)`<br>Sets the line point rule ID that will connect the edge                                                                                                                              |
    | `void`                                                                   | `setEdge``(V edge)`<br>Sets an edge to be connected                                                                                                                                                                                        |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEConnectableEdge

          public NFEConnectableEdge()

      Allocates an empty connectable edge

    <!-- -->

    - #### NFEConnectableEdge

          public NFEConnectableEdge(V edge,
                                    java.awt.geom.Point2D connPoint,
                                    IntersectionLocation connInterLoc)

      Allocates a new connectable edge
      Parameters:
      `edge` - the edge to be connected

      `connPoint` - the point in the edge where the connection must be performed

      `connInterLoc` - the edge's connection location (as an enum value)

  <!-- -->

  - ### Method Detail

    - #### getEdge

          public V getEdge()

      Gets the edge to be connected
      Returns:
      an edge instance

    <!-- -->

    - #### setEdge

          public void setEdge(V edge)

      Sets an edge to be connected
      Parameters:
      `edge` - an edge instance

    <!-- -->

    - #### getConnectableSpatialPoint

          public java.awt.geom.Point2D getConnectableSpatialPoint()

      Gets the edge's point that will be connected
      Returns:
      a java point that lying on the edge

    <!-- -->

    - #### setConnectableSpatialPoint

          public void setConnectableSpatialPoint(java.awt.geom.Point2D connectableSpatialPoint)

      Sets the edge's point that will be connected
      Parameters:
      `connectableSpatialPoint` - a java point lying on the edge

    <!-- -->

    - #### getConnectableIntersectionLocation

          public IntersectionLocation getConnectableIntersectionLocation()

      Gets the location of edge where the connection will be performed.
      Returns:
      an edge's location

    <!-- -->

    - #### setConnectableIntersectionLocation

          public void setConnectableIntersectionLocation(IntersectionLocation connectableIntersectionLocation)

      Sets the location (as a fixed value) of edge where the connection will be performed.
      Parameters:
      `connectableIntersectionLocation` - an edge's location

    <!-- -->

    - #### getConnectingLinePointRuleId

          public long getConnectingLinePointRuleId()

      Gets the line point rule ID that will connect the edge
      Returns:
      a line point rule ID

    <!-- -->

    - #### setConnectingLinePointRuleId

          public void setConnectingLinePointRuleId(long connLPRuleId)

      Sets the line point rule ID that will connect the edge
      Parameters:
      `connLPRuleId` - a line point rule ID

Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFEChangesKeeper.md)
- [Next Class](NFEConnectionDescriptor.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

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
