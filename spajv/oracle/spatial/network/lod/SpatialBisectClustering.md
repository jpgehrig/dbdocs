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

- [Prev Class](SpatialBasicNetwork.md)
- [Next Class](SpatialHeavyPath.md)

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

## Class SpatialBisectClustering

- java.lang.Object

- - oracle.spatial.network.lod.SpatialBisectClustering

<!-- -->

- All Implemented Interfaces:
  [PointClustering](PointClustering.md)

  ------------------------------------------------------------------------



      public class SpatialBisectClustering
      extends java.lang.Object
      implements PointClustering

  Since:
  release specific (what release of product did this appear in)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                    |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `SpatialBisectClustering``(int numClusters, `[`NetworkExplorer`](NetworkExplorer.md)` ne, int userDataCategory, int xCoordUserDataIndex, int yCoordUserDataIndex, int geometryUserDataIndex)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                 | Method and Description                                                                       |
    |---------------------------------------------------|----------------------------------------------------------------------------------------------|
    | [`ClusterResult`](ClusterResult.md)               | `cluster``(`[`PointOnNet`](PointOnNet.md)`[] points)`                                        |
    | [`ClusteringConstraint`](ClusteringConstraint.md) | `getClusteringConstraint``()`                                                                |
    | `void`                                            | `setClusteringConstraint``(`[`ClusteringConstraint`](ClusteringConstraint.md)` constraint)`  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### SpatialBisectClustering

          public SpatialBisectClustering(int numClusters,
                                         NetworkExplorer ne,
                                         int userDataCategory,
                                         int xCoordUserDataIndex,
                                         int yCoordUserDataIndex,
                                         int geometryUserDataIndex)

  <!-- -->

  - ### Method Detail

    - #### cluster

          public ClusterResult cluster(PointOnNet[] points)
                                throws LODNetworkException

      Specified by:
      [`cluster`](PointClustering.md) in interface [`PointClustering`](PointClustering.md)

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### setClusteringConstraint

          public void setClusteringConstraint(ClusteringConstraint constraint)

      Specified by:
      [`setClusteringConstraint`](PointClustering.md) in interface [`PointClustering`](PointClustering.md)

    <!-- -->

    - #### getClusteringConstraint

          public ClusteringConstraint getClusteringConstraint()

      Specified by:
      [`getClusteringConstraint`](PointClustering.md) in interface [`PointClustering`](PointClustering.md)

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

- [Prev Class](SpatialBasicNetwork.md)
- [Next Class](SpatialHeavyPath.md)

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
