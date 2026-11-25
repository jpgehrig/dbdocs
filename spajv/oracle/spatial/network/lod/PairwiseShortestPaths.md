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

- [Prev Class](PairwisePathResultIO.md)
- [Next Class](ParallelPairwiseShortestPaths.md)

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

## Interface PairwiseShortestPaths

- All Known Implementing Classes:
  [DefaultPairwiseShortestPaths](DefaultPairwiseShortestPaths.md), [ParallelPairwiseShortestPaths](ParallelPairwiseShortestPaths.md)

  ------------------------------------------------------------------------



      public interface PairwiseShortestPaths

  A PairwiseShortestPaths is an algorithm to calculate the the pair-wise shortest paths between a set of candidate start points and end points.
  Since:
  Oracle Database 11g Release 2 (11.2)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                          | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    |----------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                     | `setNetworkAnalyst``(`[`NetworkAnalyst`](NetworkAnalyst.md)` analyst)`<br>This method allows caller to pass the network analyst object to this pairwise shortest paths implementation, so that the algorithm can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst.                                                                                                                                                       |
    | `double[][]`                                                               | `shortestPathCosts``(`[`PointOnNet`](PointOnNet.md)`[][] startPoints, `[`PointOnNet`](PointOnNet.md)`[][] endPoints, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`Matrix`](Matrix.md)`<java.lang.Integer> pairwiseMatrix, int direction)`<br>Returns the pair-wise shortest path cost between a set of candidate start points and end points.                                                                                                                                     |
    | [`Matrix`](Matrix.md)`<`[`LogicalSubPath`](LogicalSubPath.md)`>`           | `shortestPaths``(`[`PointOnNet`](PointOnNet.md)`[][] startPoints, `[`PointOnNet`](PointOnNet.md)`[][] endPoints, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`Matrix`](Matrix.md)`<java.lang.Integer> pairwiseMatrix, int direction)`<br>Returns the pair-wise shortest paths between a set of candidate start points and end points.                                                                                                                                             |
    | [`Matrix`](Matrix.md)`<`[`LogicalLightSubPath`](LogicalLightSubPath.md)`>` | `shortestPathsLight``(`[`PointOnNet`](PointOnNet.md)`[][] startPoints, `[`PointOnNet`](PointOnNet.md)`[][] endPoints, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`Matrix`](Matrix.md)`<java.lang.Integer> pairwiseMatrix, int direction)`<br>Returns the pair-wise light weight shortest paths between a set of candidate start points and end points.                                                                                                                           |
    | `void`                                                                     | `shortestPathsLight``(`[`PointOnNet`](PointOnNet.md)`[][] startPoints, `[`PointOnNet`](PointOnNet.md)`[][] endPoints, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`Matrix`](Matrix.md)`<java.lang.Integer> pairwiseMatrix, int direction, `[`PairwisePathResultIO`](PairwisePathResultIO.md)` pathIO)`<br>Computes the pair-wise light weight shortest paths between a set of candidate start points and end points, and outputs the light weight paths via PairwisePathResultIO. |

<!-- -->

- - ### Method Detail

    - #### shortestPaths

          Matrix<LogicalSubPath> shortestPaths(PointOnNet[][] startPoints,
                                               PointOnNet[][] endPoints,
                                               LODNetworkConstraint constraint,
                                               Matrix<java.lang.Integer> pairwiseMatrix,
                                               int direction)
                                        throws LODNetworkException

      Returns the pair-wise shortest paths between a set of candidate start points and end points.
      Parameters:
      `startPoints` - array of start candidates

      `endPoints` - array of end candidates

      `constraint` - network constraint

      `pairwiseMatrix` - a matrix that specifies for which pairs the shortest paths need to be computed. If the matrix element for pair (i, j) is set to 0, then the shortest path from i to j does not need to be computed; otherwise it must be computed. If this parameter is set to null, then the shortest paths for all pairs must be computed.

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### shortestPathsLight

          Matrix<LogicalLightSubPath> shortestPathsLight(PointOnNet[][] startPoints,
                                                         PointOnNet[][] endPoints,
                                                         LODNetworkConstraint constraint,
                                                         Matrix<java.lang.Integer> pairwiseMatrix,
                                                         int direction)
                                                  throws LODNetworkException

      Returns the pair-wise light weight shortest paths between a set of candidate start points and end points.
      Parameters:
      `startPoints` - array of start candidates

      `endPoints` - array of end candidates

      `constraint` - network constraint

      `pairwiseMatrix` - a matrix that specifies for which pairs the shortest paths need to be computed. If the matrix element for pair (i, j) is set to 0, then the shortest path from i to j does not need to be computed; otherwise it must be computed. If this parameter is set to null, then the shortest paths for all pairs must be computed.

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### shortestPathsLight

          void shortestPathsLight(PointOnNet[][] startPoints,
                                  PointOnNet[][] endPoints,
                                  LODNetworkConstraint constraint,
                                  Matrix<java.lang.Integer> pairwiseMatrix,
                                  int direction,
                                  PairwisePathResultIO pathIO)
                           throws LODNetworkException

      Computes the pair-wise light weight shortest paths between a set of candidate start points and end points, and outputs the light weight paths via PairwisePathResultIO.
      Parameters:
      `startPoints` - array of start candidates

      `endPoints` - array of end candidates

      `constraint` - network constraint

      `pairwiseMatrix` - a matrix that specifies for which pairs the shortest paths need to be computed. If the matrix element for pair (i, j) is set to 0, then the shortest path from i to j does not need to be computed; otherwise it must be computed. If this parameter is set to null, then the shortest paths for all pairs must be computed.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### shortestPathCosts

          double[][] shortestPathCosts(PointOnNet[][] startPoints,
                                       PointOnNet[][] endPoints,
                                       LODNetworkConstraint constraint,
                                       Matrix<java.lang.Integer> pairwiseMatrix,
                                       int direction)
                                throws LODNetworkException

      Returns the pair-wise shortest path cost between a set of candidate start points and end points. This method can be used when the caller is only interested in path costs. the light path results.
      Parameters:
      `startPoints` - array of start candidates

      `endPoints` - array of end candidates

      `constraint` - network constraint

      `pairwiseMatrix` - a matrix that specifies for which pairs the shortest paths need to be computed. If the matrix element for pair (i, j) is set to 0, then the shortest path from i to j does not need to be computed; otherwise it must be computed. If this parameter is set to null, then the shortest paths for all pairs must be computed.

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### setNetworkAnalyst

          void setNetworkAnalyst(NetworkAnalyst analyst)

      This method allows caller to pass the network analyst object to this pairwise shortest paths implementation, so that the algorithm can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst. If network analyst is not needed by the algorithm, the algorithm can choose to do nothing with this method.

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

- [Prev Class](PairwisePathResultIO.md)
- [Next Class](ParallelPairwiseShortestPaths.md)

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
