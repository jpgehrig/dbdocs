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

- [Prev Class](TimeWindow.md)
- [Next Class](TSP.TourFlag.md)

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

## Interface TSP

- All Known Implementing Classes:
  [TspImpl](TspImpl.md), [TspNearestNeighbor](TspNearestNeighbor.md), [TspOp2](TspOp2.md)

  ------------------------------------------------------------------------



      public interface TSP

  This interface defines methods supported by traveling salesman problem algorithm.
  Since:
  Oracle Database 11g Release 2 (11.2)

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Interface and Description                                                                                                                                                     |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static class `   | [`TSP.TourFlag`](TSP.TourFlag.md)<br>Enumeration whose values indicate whether a tsp tour is open or closed, and if open, whether the tour have fixed start and/or end point. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type       | Method and Description                                                                                                                                                                                                                                                                                                                  |
    |-------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                  | `setNetworkAnalyst``(`[`NetworkAnalyst`](NetworkAnalyst.md)` analyst)`<br>This method allows caller to pass the network analyst object to this TSP algorithm implementation, so that the algorithm can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst. |
    | [`TspPath`](TspPath.md) | `tspPath``(`[`PointOnNet`](PointOnNet.md)`[][] points, `[`TSP.TourFlag`](TSP.TourFlag.md)` tourFlag, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` pathConstraint, `[`TspConstraint`](TspConstraint.md)` tspConstraint)`<br>Returns the traveling salesman tour with the optimal or suboptimal cost.                              |

<!-- -->

- - ### Method Detail

    - #### setNetworkAnalyst

          void setNetworkAnalyst(NetworkAnalyst analyst)

      This method allows caller to pass the network analyst object to this TSP algorithm implementation, so that the algorithm can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst. If network analyst is not needed by the shortest path algorithm, the algorithm can choose to do nothing with this method.

    <!-- -->

    - #### tspPath

          TspPath tspPath(PointOnNet[][] points,
                          TSP.TourFlag tourFlag,
                          LODNetworkConstraint pathConstraint,
                          TspConstraint tspConstraint)
                   throws LODNetworkException

      Returns the traveling salesman tour with the optimal or suboptimal cost.
      Parameters:
      `points` - points to visit on the TSP tour.

      `tourFlag` - a flag indicating whether the tour should be open or closed, and if the tour is open, whether the tour should have fixed start or end point.

      `pathConstraint` - network constraint

      `tspConstraint` - tsp constraint

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

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

- [Prev Class](TimeWindow.md)
- [Next Class](TSP.TourFlag.md)

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
