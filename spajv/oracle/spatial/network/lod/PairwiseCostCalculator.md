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

- [Prev Class](OrderedLongSet.md)
- [Next Class](PairwisePathResultIO.md)

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

## Interface PairwiseCostCalculator

- All Known Implementing Classes:
  [DefaultPairwiseCostCalculator](DefaultPairwiseCostCalculator.md), [GeodeticPairwiseCostCalculator](GeodeticPairwiseCostCalculator.md)

  ------------------------------------------------------------------------



      public interface PairwiseCostCalculator

  This interface defines methods to calculate the pairwise costs between two sets of points.
  Since:
  Oracle Database 11g Release 2 (11.2)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                | Method and Description                                                                                                                                                                                                                                                                                                                    |
    |------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                                        | `calculate``(`[`PointOnNet`](PointOnNet.md)`[][] startPoints, `[`PointOnNet`](PointOnNet.md)`[][] endPoints, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`Matrix`](Matrix.md)`<java.lang.Integer> pairwiseMatrix)`<br>Computes the pairwise costs between two sets of points.                                       |
    | [`Matrix`](Matrix.md)`<double[]>`                                | `getPairwiseCosts``()`<br>Returns the pairwise costs that was computed when calculate was called.                                                                                                                                                                                                                                         |
    | [`Matrix`](Matrix.md)`<`[`LogicalSubPath`](LogicalSubPath.md)`>` | `getPairwisePaths``()`<br>Returns the pairwise paths that was computed when calculate was called.                                                                                                                                                                                                                                         |
    | `void`                                                           | `setNetworkAnalyst``(`[`NetworkAnalyst`](NetworkAnalyst.md)` analyst)`<br>This method allows caller to pass the network analyst object to this cost calculator implementation, so that the algorithm can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst. |

<!-- -->

- - ### Method Detail

    - #### calculate

          boolean calculate(PointOnNet[][] startPoints,
                            PointOnNet[][] endPoints,
                            LODNetworkConstraint constraint,
                            Matrix<java.lang.Integer> pairwiseMatrix)
                     throws LODNetworkException

      Computes the pairwise costs between two sets of points.
      Parameters:
      `startPoints` - start point candidates

      `endPoints` - end point candidates

      `constraint` - network constraint

      `pairwiseMatrix` - a matrix that specifies for which pairs the costs need to be computed. If the matrix element for pair (i, j) is set to 0, then the cost from i to j does not need to be computed; otherwise it must be computed. If this parameter is set to null, then the costs for all pairs must be computed.

      Returns:
      true if the pairwise paths are also computed in addition to the pairwise costs; false otherwise

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### getPairwisePaths

          Matrix<LogicalSubPath> getPairwisePaths()

      Returns the pairwise paths that was computed when calculate was called. Returns null if the pairwise paths were not computed.
      Returns:

    <!-- -->

    - #### getPairwiseCosts

          Matrix<double[]> getPairwiseCosts()

      Returns the pairwise costs that was computed when calculate was called. The pairwise costs must have been computed when calculate was called.
      Returns:

    <!-- -->

    - #### setNetworkAnalyst

          void setNetworkAnalyst(NetworkAnalyst analyst)

      This method allows caller to pass the network analyst object to this cost calculator implementation, so that the algorithm can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst. If network analyst is not needed by the cost calculator, the calculator can choose to do nothing with this method.

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

- [Prev Class](OrderedLongSet.md)
- [Next Class](PairwisePathResultIO.md)

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
