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

- [Prev Class](DefaultPairwiseShortestPaths.md)
- [Next Class](Dijkstra.md)

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

## Class DefaultSingleSourceShortestPaths

- java.lang.Object

- - oracle.spatial.network.lod.DefaultSingleSourceShortestPaths

<!-- -->

- All Implemented Interfaces:
  [SingleSourceShortestPaths](SingleSourceShortestPaths.md)

  ------------------------------------------------------------------------



      public class DefaultSingleSourceShortestPaths
      extends java.lang.Object
      implements SingleSourceShortestPaths

  Since:
  release specific (what release of product did this appear in)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                            |
    |----------------------------------------------------------------------------------------|
    | `DefaultSingleSourceShortestPaths``(`[`ShortestPath`](ShortestPath.md)` spAlgorithm)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                   | Method and Description                                                                                                                                                                                                                                                                                                                                              |
    |-----------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `DefaultSingleSourceShortestPaths`                  | `clone``()`                                                                                                                                                                                                                                                                                                                                                         |
    | `void`                                              | `setNetworkAnalyst``(`[`NetworkAnalyst`](NetworkAnalyst.md)` analyst)`<br>This method allows caller to pass the network analyst object to this shortest path algorithm implementation, so that the algorithm can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst.                   |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`           | `shortestPaths``(`[`PointOnNet`](PointOnNet.md)`[] startPoint, `[`PointOnNet`](PointOnNet.md)`[][] endPoints, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, int direction)`<br>Returns the shortest paths from the start point (one of the start point candidates) to each set of end points (one of the end point candidates).                   |
    | [`LogicalLightSubPath`](LogicalLightSubPath.md)`[]` | `shortestPathsLight``(`[`PointOnNet`](PointOnNet.md)`[] startPoint, `[`PointOnNet`](PointOnNet.md)`[][] endPoints, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, int direction)`<br>Returns the light weight shortest paths from the start point (one of the start point candidates) to each set of end points (one of the end point candidates). |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### DefaultSingleSourceShortestPaths

          public DefaultSingleSourceShortestPaths(ShortestPath spAlgorithm)

  <!-- -->

  - ### Method Detail

    - #### shortestPaths

          public LogicalSubPath[] shortestPaths(PointOnNet[] startPoint,
                                                PointOnNet[][] endPoints,
                                                LODNetworkConstraint constraint,
                                                int direction)
                                         throws LODNetworkException

      Description copied from interface: [`SingleSourceShortestPaths`](SingleSourceShortestPaths.md)
      Returns the shortest paths from the start point (one of the start point candidates) to each set of end points (one of the end point candidates).
      Specified by:
      [`shortestPaths`](SingleSourceShortestPaths.md) in interface [`SingleSourceShortestPaths`](SingleSourceShortestPaths.md)

      Parameters:
      `startPoint` - start point candidates

      `endPoints` - array of end point candidates

      `constraint` - network constraint

      `direction` - NetworkExplorer.DIRECTION_FORWARD or NetworkExplorer.DIRECTION_BACKWARD

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### shortestPathsLight

          public LogicalLightSubPath[] shortestPathsLight(PointOnNet[] startPoint,
                                                          PointOnNet[][] endPoints,
                                                          LODNetworkConstraint constraint,
                                                          int direction)
                                                   throws LODNetworkException

      Description copied from interface: [`SingleSourceShortestPaths`](SingleSourceShortestPaths.md)
      Returns the light weight shortest paths from the start point (one of the start point candidates) to each set of end points (one of the end point candidates).
      Specified by:
      [`shortestPathsLight`](SingleSourceShortestPaths.md) in interface [`SingleSourceShortestPaths`](SingleSourceShortestPaths.md)

      Parameters:
      `startPoint` - start point candidates

      `endPoints` - array of end point candidates

      `constraint` - network constraint

      `direction` - NetworkExplorer.DIRECTION_FORWARD or NetworkExplorer.DIRECTION_BACKWARD

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### setNetworkAnalyst

          public void setNetworkAnalyst(NetworkAnalyst analyst)

      Description copied from interface: [`SingleSourceShortestPaths`](SingleSourceShortestPaths.md)
      This method allows caller to pass the network analyst object to this shortest path algorithm implementation, so that the algorithm can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst. If network analyst is not needed by the shortest path algorithm, the algorithm can choose to do nothing with this method.
      Specified by:
      [`setNetworkAnalyst`](SingleSourceShortestPaths.md) in interface [`SingleSourceShortestPaths`](SingleSourceShortestPaths.md)

    <!-- -->

    - #### clone

          public DefaultSingleSourceShortestPaths clone()

      Specified by:
      [`clone`](SingleSourceShortestPaths.md) in interface [`SingleSourceShortestPaths`](SingleSourceShortestPaths.md)

      Overrides:
      `clone` in class `java.lang.Object`

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

- [Prev Class](DefaultPairwiseShortestPaths.md)
- [Next Class](Dijkstra.md)

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
