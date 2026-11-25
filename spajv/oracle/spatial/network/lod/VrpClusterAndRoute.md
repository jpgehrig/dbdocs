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

- [Prev Class](VRP.md)
- [Next Class](VrpPath.md)

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

## Class VrpClusterAndRoute

- java.lang.Object

- - oracle.spatial.network.lod.VrpClusterAndRoute

<!-- -->

- All Implemented Interfaces:
  [VRP](VRP.md)

  ------------------------------------------------------------------------



      public class VrpClusterAndRoute
      extends java.lang.Object
      implements VRP

  Since:
  release specific (what release of product did this appear in)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                  |
    |--------------------------------------------------------------------------------------------------------------|
    | `VrpClusterAndRoute``(`[`PointClustering`](PointClustering.md)` clusteringAlgo, `[`TSP`](TSP.md)` tspAlgo)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type           | Method and Description                                                                                                                                                                                                                                                                      |
    |-----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`TspPath`](TspPath.md)`[]` | `vrp``(`[`PointOnNet`](PointOnNet.md)`[][] points, `[`TSP.TourFlag`](TSP.TourFlag.md)` tourFlag, int numVehicles, `[`PointOnNet`](PointOnNet.md)`[][] depots, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` networkConstraint, `[`TspConstraint`](TspConstraint.md)` tspConstraint)`  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### VrpClusterAndRoute

          public VrpClusterAndRoute(PointClustering clusteringAlgo,
                                    TSP tspAlgo)

  <!-- -->

  - ### Method Detail

    - #### vrp

          public TspPath[] vrp(PointOnNet[][] points,
                               TSP.TourFlag tourFlag,
                               int numVehicles,
                               PointOnNet[][] depots,
                               LODNetworkConstraint networkConstraint,
                               TspConstraint tspConstraint)
                        throws LODNetworkException

      Specified by:
      [`vrp`](VRP.md) in interface [`VRP`](VRP.md)

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

- [Prev Class](VRP.md)
- [Next Class](VrpPath.md)

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
