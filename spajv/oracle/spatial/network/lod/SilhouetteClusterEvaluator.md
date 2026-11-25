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

- [Prev Class](ShortestPath.md)
- [Next Class](SingleSourceShortestPaths.md)

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

## Class SilhouetteClusterEvaluator

- java.lang.Object

- - oracle.spatial.network.lod.SilhouetteClusterEvaluator

<!-- -->

- All Implemented Interfaces:
  [ClusterEvaluator](ClusterEvaluator.md)

  ------------------------------------------------------------------------



      public class SilhouetteClusterEvaluator
      extends java.lang.Object
      implements ClusterEvaluator

  This implementation uses the Silhouette method to measure cluster quality. The returned score lies between -1 and 1. The closer the score to 1, the better the cluster quality. http://en.wikipedia.org/wiki/Silhouette\_(clustering)
  Since:
  release specific (what release of product did this appear in)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                      |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `SilhouetteClusterEvaluator``(`[`NetworkExplorer`](NetworkExplorer.md)` ne, int userDataCategory, int xCoordUserDataIndex, int yCoordUserDataIndex, int geometryUserDataIndex)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                       |
    |-------------------|--------------------------------------------------------------------------------------------------------------|
    | `double`          | `evaluate``(`[`PointOnNet`](PointOnNet.md)`[] points, `[`ClusterResult`](ClusterResult.md)` clusterResult)`  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### SilhouetteClusterEvaluator

          public SilhouetteClusterEvaluator(NetworkExplorer ne,
                                            int userDataCategory,
                                            int xCoordUserDataIndex,
                                            int yCoordUserDataIndex,
                                            int geometryUserDataIndex)

  <!-- -->

  - ### Method Detail

    - #### evaluate

          public double evaluate(PointOnNet[] points,
                                 ClusterResult clusterResult)
                          throws LODNetworkException

      Specified by:
      [`evaluate`](ClusterEvaluator.md) in interface [`ClusterEvaluator`](ClusterEvaluator.md)

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

- [Prev Class](ShortestPath.md)
- [Next Class](SingleSourceShortestPaths.md)

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
