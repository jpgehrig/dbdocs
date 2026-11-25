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

- [Prev Class](TspImpl.NetworkTspConstraint.md)
- [Next Class](TspOp2.md)

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

## Class TspNearestNeighbor

- java.lang.Object

- - oracle.spatial.network.lod.TspNearestNeighbor

<!-- -->

- All Implemented Interfaces:
  [TSP](TSP.md)

  ------------------------------------------------------------------------



      public class TspNearestNeighbor
      extends java.lang.Object
      implements TSP

  This is a simple heuristic TSP algorithm, which always picks the closest point as the next one to visit.
  Since:
  Oracle Database 11g Release 2 (11.2)

<!-- -->

- - ### Nested Class Summary

    - ### Nested classes/interfaces inherited from interface oracle.spatial.network.lod.[TSP](TSP.md)

      [`TSP.TourFlag`](TSP.TourFlag.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                            |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `TspNearestNeighbor``(`[`NetworkExplorer`](NetworkExplorer.md)` ne, `[`LinkCostCalculator`](LinkCostCalculator.md)`[] lccs, `[`NodeCostCalculator`](NodeCostCalculator.md)`[] nccs, `[`ShortestPath`](ShortestPath.md)` spAlgorithm)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                | Method and Description                                                                                                                                                                                                                                                                                                                  |
    |------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                           | `setNetworkAnalyst``(`[`NetworkAnalyst`](NetworkAnalyst.md)` analyst)`<br>This method allows caller to pass the network analyst object to this TSP algorithm implementation, so that the algorithm can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst. |
    | [`Matrix`](Matrix.md)`<`[`LogicalSubPath`](LogicalSubPath.md)`>` | `shortestPaths``(`[`PointOnNet`](PointOnNet.md)`[][] startPoints, `[`PointOnNet`](PointOnNet.md)`[][] endPoints, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`TSP.TourFlag`](TSP.TourFlag.md)` tourFlag)`                                                                                                         |
    | [`TspPath`](TspPath.md)                                          | `tspPath``(`[`PointOnNet`](PointOnNet.md)`[][] points, `[`TSP.TourFlag`](TSP.TourFlag.md)` tourFlag, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`TspConstraint`](TspConstraint.md)` tspConstraint)`<br>Returns the traveling salesman tour with the optimal or suboptimal cost.                                  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### TspNearestNeighbor

          public TspNearestNeighbor(NetworkExplorer ne,
                                    LinkCostCalculator[] lccs,
                                    NodeCostCalculator[] nccs,
                                    ShortestPath spAlgorithm)

  <!-- -->

  - ### Method Detail

    - #### tspPath

          public TspPath tspPath(PointOnNet[][] points,
                                 TSP.TourFlag tourFlag,
                                 LODNetworkConstraint constraint,
                                 TspConstraint tspConstraint)
                          throws LODNetworkException

      Description copied from interface: [`TSP`](TSP.md)
      Returns the traveling salesman tour with the optimal or suboptimal cost.
      Specified by:
      [`tspPath`](TSP.md) in interface [`TSP`](TSP.md)

      Parameters:
      `points` - points to visit on the TSP tour.

      `tourFlag` - a flag indicating whether the tour should be open or closed, and if the tour is open, whether the tour should have fixed start or end point.

      `constraint` - network constraint

      `tspConstraint` - tsp constraint

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### shortestPaths

          public Matrix<LogicalSubPath> shortestPaths(PointOnNet[][] startPoints,
                                                      PointOnNet[][] endPoints,
                                                      LODNetworkConstraint constraint,
                                                      TSP.TourFlag tourFlag)
                                               throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### setNetworkAnalyst

          public void setNetworkAnalyst(NetworkAnalyst analyst)

      Description copied from interface: [`TSP`](TSP.md)
      This method allows caller to pass the network analyst object to this TSP algorithm implementation, so that the algorithm can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst. If network analyst is not needed by the shortest path algorithm, the algorithm can choose to do nothing with this method.
      Specified by:
      [`setNetworkAnalyst`](TSP.md) in interface [`TSP`](TSP.md)

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

- [Prev Class](TspImpl.NetworkTspConstraint.md)
- [Next Class](TspOp2.md)

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
