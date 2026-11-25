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

- [Prev Class](VisitedNode.md)
- [Next Class](VrpClusterAndRoute.md)

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

## Interface VRP

- All Known Implementing Classes:
  [VrpClusterAndRoute](VrpClusterAndRoute.md)

  ------------------------------------------------------------------------



      public interface VRP

  Since:
  12.2

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type           | Method and Description                                                                                                                                                                                                                                                                      |
    |-----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`TspPath`](TspPath.md)`[]` | `vrp``(`[`PointOnNet`](PointOnNet.md)`[][] points, `[`TSP.TourFlag`](TSP.TourFlag.md)` tourFlag, int numVehicles, `[`PointOnNet`](PointOnNet.md)`[][] depots, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` networkConstraint, `[`TspConstraint`](TspConstraint.md)` tspConstraint)`  |

<!-- -->

- - ### Method Detail

    - #### vrp

          TspPath[] vrp(PointOnNet[][] points,
                        TSP.TourFlag tourFlag,
                        int numVehicles,
                        PointOnNet[][] depots,
                        LODNetworkConstraint networkConstraint,
                        TspConstraint tspConstraint)
                 throws LODNetworkException

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

- [Prev Class](VisitedNode.md)
- [Next Class](VrpClusterAndRoute.md)

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
