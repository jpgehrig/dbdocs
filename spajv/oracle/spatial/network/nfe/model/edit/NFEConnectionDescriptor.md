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

- [Prev Class](NFEConnectableEdge.md)
- [Next Class](NFEConnectionManager.md)

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

## Class NFEConnectionDescriptor\<U,V\>

- java.lang.Object

- - oracle.spatial.network.nfe.model.edit.NFEConnectionDescriptor\<U,V\>

<!-- -->

- Type Parameters:
  `U` - The type of vertex

  `V` - The type of the edges

  ------------------------------------------------------------------------



      public class NFEConnectionDescriptor<U,V>
      extends java.lang.Object

  Holds a vertex a collections of edges to be connected to the point. Each edge is wrapped as an NFEConnectableEdge instance which contains the location where the edge must be connected. Additionally it contains the line point and line line rules which allow such connections.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                            |
    |------------------------------------------------------------------------|
    | `NFEConnectionDescriptor``()`<br>Allocates a new connection descriptor |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                    | Method and Description                                                                                                                                                 |
    |----------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                               | `addConnectableEdge``(`[`NFEConnectableEdge`](NFEConnectableEdge.md)`<V> connEdge)`<br>Sets a collection of edges to be connected to a vertex                          |
    | `void`                                                               | `addConnectableEdges``(java.util.Collection<`[`NFEConnectableEdge`](NFEConnectableEdge.md)`<V>> connEdges)`<br>Adds a connectable edge                                 |
    | `java.util.List<`[`NFEConnectableEdge`](NFEConnectableEdge.md)`<V>>` | `getConnectableEdges``()`<br>Gets a collection of edges to be connected to a vertex                                                                                    |
    | `U`                                                                  | `getConnectableVertex``()`<br>Gets the vertex instance to be connected                                                                                                 |
    | `long`                                                               | `getConnectingLineLineRuleId``()`<br>Gets the line line rule ID which allows the connections described                                                                 |
    | `long`                                                               | `getConnectingLinePointRuleId``()`<br>Gets the line point rule ID which allows the connections described                                                               |
    | `java.awt.geom.Point2D`                                              | `getConnectionSpatialPoint``()`<br>Gets the point in the space where the connecting vertex will be placed after the connection is performed                            |
    | `double`                                                             | `getTolerance``()`<br>Gets the tolerance that was used to determine the interaction between the elements in the connection descriptor                                  |
    | `boolean`                                                            | `removeConnectableEdge``(`[`NFEConnectableEdge`](NFEConnectableEdge.md)`<V> connEdge)`<br>Removes an edge from the connectable edges                                   |
    | `boolean`                                                            | `removeConnectableEdges``(java.util.Collection<`[`NFEConnectableEdge`](NFEConnectableEdge.md)`<V>> connEdges)`<br>Removes a group of edges from the connectable edges  |
    | `void`                                                               | `setConnectableVertex``(U vertexElement)`<br>Sets the vertex instance to be connected                                                                                  |
    | `void`                                                               | `setConnectingLineLineRuleId``(long connLLRuleId)`<br>Sets the line line rule ID which allows the connections described                                                |
    | `void`                                                               | `setConnectingLinePointRuleId``(long connLPRuleId)`<br>Sets the line point rule ID which allows the connections described                                              |
    | `void`                                                               | `setConnectionSpatilPoint``(java.awt.geom.Point2D point)`<br>Sets the point in the space where the connecting vertex will be placed after the connection is performed. |
    | `void`                                                               | `setTolerance``(double tolerance)`<br>Sets the tolerance that was used to determine the interaction between the elements in the connection descriptor                  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEConnectionDescriptor

          public NFEConnectionDescriptor()

      Allocates a new connection descriptor

  <!-- -->

  - ### Method Detail

    - #### getConnectionSpatialPoint

          public java.awt.geom.Point2D getConnectionSpatialPoint()

      Gets the point in the space where the connecting vertex will be placed after the connection is performed
      Returns:
      a java point

    <!-- -->

    - #### setConnectionSpatilPoint

          public void setConnectionSpatilPoint(java.awt.geom.Point2D point)

      Sets the point in the space where the connecting vertex will be placed after the connection is performed. If this is not specified, the vertex' spatial point will be used.
      Parameters:
      `point` - a java point

    <!-- -->

    - #### getTolerance

          public double getTolerance()

      Gets the tolerance that was used to determine the interaction between the elements in the connection descriptor
      Returns:
      a tolerance value

    <!-- -->

    - #### setTolerance

          public void setTolerance(double tolerance)

      Sets the tolerance that was used to determine the interaction between the elements in the connection descriptor
      Parameters:
      `tolerance` - a tolerance value, higher or equal to zero

    <!-- -->

    - #### getConnectableVertex

          public U getConnectableVertex()

      Gets the vertex instance to be connected
      Returns:
      an instance of the class specified to represent a vertex. It may be a point feature element or a node

    <!-- -->

    - #### setConnectableVertex

          public void setConnectableVertex(U vertexElement)

      Sets the vertex instance to be connected
      Parameters:
      `vertexElement` - an instance of the class specified to represent a vertex. It may be a point feature element or a node

    <!-- -->

    - #### getConnectableEdges

          public java.util.List<NFEConnectableEdge<V>> getConnectableEdges()

      Gets a collection of edges to be connected to a vertex
      Returns:
      a collection of instances representing edges such as line feature elements o links

    <!-- -->

    - #### addConnectableEdge

          public void addConnectableEdge(NFEConnectableEdge<V> connEdge)

      Sets a collection of edges to be connected to a vertex
      Parameters:
      `connEdge` - a collection of instances representing edges such as line feature elements o links

    <!-- -->

    - #### removeConnectableEdge

          public boolean removeConnectableEdge(NFEConnectableEdge<V> connEdge)

      Removes an edge from the connectable edges
      Parameters:
      `connEdge` - a connectable edge to be removed

      Returns:
      true if the edge was removed

    <!-- -->

    - #### removeConnectableEdges

          public boolean removeConnectableEdges(java.util.Collection<NFEConnectableEdge<V>> connEdges)

      Removes a group of edges from the connectable edges
      Parameters:
      `connEdges` - a collection of connectable edges to be removed

      Returns:
      true if all the edges were removed

    <!-- -->

    - #### addConnectableEdges

          public void addConnectableEdges(java.util.Collection<NFEConnectableEdge<V>> connEdges)

      Adds a connectable edge
      Parameters:
      `connEdges` - an edge instance

    <!-- -->

    - #### setConnectingLinePointRuleId

          public void setConnectingLinePointRuleId(long connLPRuleId)

      Sets the line point rule ID which allows the connections described
      Parameters:
      `connLPRuleId` - a line point rule ID

    <!-- -->

    - #### getConnectingLinePointRuleId

          public long getConnectingLinePointRuleId()

      Gets the line point rule ID which allows the connections described
      Returns:
      a line point rule ID

    <!-- -->

    - #### setConnectingLineLineRuleId

          public void setConnectingLineLineRuleId(long connLLRuleId)

      Sets the line line rule ID which allows the connections described
      Parameters:
      `connLLRuleId` - a line line rule ID

    <!-- -->

    - #### getConnectingLineLineRuleId

          public long getConnectingLineLineRuleId()

      Gets the line line rule ID which allows the connections described
      Returns:
      a line line rule ID

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

- [Prev Class](NFEConnectableEdge.md)
- [Next Class](NFEConnectionManager.md)

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
