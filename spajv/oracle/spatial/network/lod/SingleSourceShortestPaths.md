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

- [Prev Class](SilhouetteClusterEvaluator.md)
- [Next Class](SpanningTree.md)

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

## Interface SingleSourceShortestPaths

- All Known Implementing Classes:
  [DefaultSingleSourceShortestPaths](DefaultSingleSourceShortestPaths.md), [Dijkstra](Dijkstra.md)

  ------------------------------------------------------------------------



      public interface SingleSourceShortestPaths

  Since:
  release specific (what release of product did this appear in)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                   | Method and Description                                                                                                                                                                                                                                                                                                                                              |
    |-----------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `SingleSourceShortestPaths`                         | `clone``()`                                                                                                                                                                                                                                                                                                                                                         |
    | `void`                                              | `setNetworkAnalyst``(`[`NetworkAnalyst`](NetworkAnalyst.md)` analyst)`<br>This method allows caller to pass the network analyst object to this shortest path algorithm implementation, so that the algorithm can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst.                   |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]`           | `shortestPaths``(`[`PointOnNet`](PointOnNet.md)`[] startPoint, `[`PointOnNet`](PointOnNet.md)`[][] endPoints, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, int direction)`<br>Returns the shortest paths from the start point (one of the start point candidates) to each set of end points (one of the end point candidates).                   |
    | [`LogicalLightSubPath`](LogicalLightSubPath.md)`[]` | `shortestPathsLight``(`[`PointOnNet`](PointOnNet.md)`[] startPoint, `[`PointOnNet`](PointOnNet.md)`[][] endPoints, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, int direction)`<br>Returns the light weight shortest paths from the start point (one of the start point candidates) to each set of end points (one of the end point candidates). |

<!-- -->

- - ### Method Detail

    - #### shortestPathsLight

          LogicalLightSubPath[] shortestPathsLight(PointOnNet[] startPoint,
                                                   PointOnNet[][] endPoints,
                                                   LODNetworkConstraint constraint,
                                                   int direction)
                                            throws LODNetworkException

      Returns the light weight shortest paths from the start point (one of the start point candidates) to each set of end points (one of the end point candidates).
      Parameters:
      `startPoint` - start point candidates

      `endPoints` - array of end point candidates

      `constraint` - network constraint

      `direction` - NetworkExplorer.DIRECTION_FORWARD or NetworkExplorer.DIRECTION_BACKWARD

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### shortestPaths

          LogicalSubPath[] shortestPaths(PointOnNet[] startPoint,
                                         PointOnNet[][] endPoints,
                                         LODNetworkConstraint constraint,
                                         int direction)
                                  throws LODNetworkException

      Returns the shortest paths from the start point (one of the start point candidates) to each set of end points (one of the end point candidates).
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

          void setNetworkAnalyst(NetworkAnalyst analyst)

      This method allows caller to pass the network analyst object to this shortest path algorithm implementation, so that the algorithm can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst. If network analyst is not needed by the shortest path algorithm, the algorithm can choose to do nothing with this method.

    <!-- -->

    - #### clone

          SingleSourceShortestPaths clone()

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

- [Prev Class](SilhouetteClusterEvaluator.md)
- [Next Class](SpanningTree.md)

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
