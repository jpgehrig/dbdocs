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

- [Prev Class](PathToPoint.md)
- [Next Class](PointOnNet.md)

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

## Interface PointClustering

- All Known Implementing Classes:
  [SpatialBisectClustering](SpatialBisectClustering.md), [SpatialKMeansClustering](SpatialKMeansClustering.md)

  ------------------------------------------------------------------------



      public interface PointClustering

  Since:
  12.2

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                 | Method and Description                                                                       |
    |---------------------------------------------------|----------------------------------------------------------------------------------------------|
    | [`ClusterResult`](ClusterResult.md)               | `cluster``(`[`PointOnNet`](PointOnNet.md)`[] points)`                                        |
    | [`ClusteringConstraint`](ClusteringConstraint.md) | `getClusteringConstraint``()`                                                                |
    | `void`                                            | `setClusteringConstraint``(`[`ClusteringConstraint`](ClusteringConstraint.md)` constraint)`  |

<!-- -->

- - ### Method Detail

    - #### cluster

          ClusterResult cluster(PointOnNet[] points)
                         throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### setClusteringConstraint

          void setClusteringConstraint(ClusteringConstraint constraint)

    <!-- -->

    - #### getClusteringConstraint

          ClusteringConstraint getClusteringConstraint()

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

- [Prev Class](PathToPoint.md)
- [Next Class](PointOnNet.md)

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
