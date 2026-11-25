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

- [Prev Class](InMemoryPairwisePathResultIO.md)
- [Next Class](KShortestPathsBfs.md)

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

## Interface KShortestPaths

- All Known Implementing Classes:
  [KShortestPathsBfs](KShortestPathsBfs.md), [YenDeviation](YenDeviation.md)

  ------------------------------------------------------------------------



      public interface KShortestPaths

  This interface defines methods supported by a k shortest path algorithm.
  Since:
  Oracle Database 11g Release 2 (11.2)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                         | Method and Description                                                                                                                                                                                                                                                                                                                               |
    |-------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`LogicalSubPath`](LogicalSubPath.md)`[]` | `kShortestPaths``(`[`PointOnNet`](PointOnNet.md)`[] startPoint, `[`PointOnNet`](PointOnNet.md)`[] endPoint, int k, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`PathFilter`](PathFilter.md)` pathFilter, int direction)`<br>Returns the k shortest paths from the start point to the end point.                                |
    | `void`                                    | `setLinkLevelSelector``(`[`LinkLevelSelector`](LinkLevelSelector.md)` lls)`<br>Sets link level selector.                                                                                                                                                                                                                                             |
    | `void`                                    | `setNetworkAnalyst``(`[`NetworkAnalyst`](NetworkAnalyst.md)` analyst)`<br>This method allows caller to pass the network analyst object to this k shortest paths algorithm implementation, so that the algorithm can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst. |

<!-- -->

- - ### Method Detail

    - #### kShortestPaths

          LogicalSubPath[] kShortestPaths(PointOnNet[] startPoint,
                                          PointOnNet[] endPoint,
                                          int k,
                                          LODNetworkConstraint constraint,
                                          PathFilter pathFilter,
                                          int direction)
                                   throws LODNetworkException

      Returns the k shortest paths from the start point to the end point.
      Parameters:
      `startPoint` - candidate start points

      `endPoint` - candidate end points

      `k` - max number of paths to be returned

      `constraint` - network constraint

      `direction` - NetworkExplorer.DIRECTION_FORWARD or NetworkExplorer.DIRECTION_BACKWARD

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### setLinkLevelSelector

          void setLinkLevelSelector(LinkLevelSelector lls)

      Sets link level selector.
      Parameters:
      `lls` - link level selector

    <!-- -->

    - #### setNetworkAnalyst

          void setNetworkAnalyst(NetworkAnalyst analyst)

      This method allows caller to pass the network analyst object to this k shortest paths algorithm implementation, so that the algorithm can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst. If network analyst is not needed by the shortest path algorithm, the algorithm can choose to do nothing with this method.

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

- [Prev Class](InMemoryPairwisePathResultIO.md)
- [Next Class](KShortestPathsBfs.md)

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
