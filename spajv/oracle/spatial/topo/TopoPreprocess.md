Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](TopoMap.md)
- [Next Class](TopoValidationException.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

oracle.spatial.topo

## Interface TopoPreprocess

-

  ------------------------------------------------------------------------



      public interface TopoPreprocess

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                           |
    |-------------------|----------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`         | `addEdgePre``(int nodeID1, int nodeID2, `[`Point2DD`](Point2DD.md)`[] coords, `[`TopoMap`](TopoMap.md)` t)`                      |
    | `boolean`         | `addIsolatedNodePre``(`[`Point2DD`](Point2DD.md)` p, `[`TopoMap`](TopoMap.md)` t)`                                               |
    | `boolean`         | `addLoopPre``(int nodeID, `[`Point2DD`](Point2DD.md)`[] coords, `[`TopoMap`](TopoMap.md)` t)`                                    |
    | `boolean`         | `addNodePre``(int edgeID, `[`Point2DD`](Point2DD.md)` p, int coordIndex, boolean isNewShapePoint, `[`TopoMap`](TopoMap.md)` t)`  |

<!-- -->

- - ### Method Detail

    - #### addEdgePre

          boolean addEdgePre(int nodeID1,
                             int nodeID2,
                             Point2DD[] coords,
                             TopoMap t)

    <!-- -->

    - #### addIsolatedNodePre

          boolean addIsolatedNodePre(Point2DD p,
                                     TopoMap t)

    <!-- -->

    - #### addNodePre

          boolean addNodePre(int edgeID,
                             Point2DD p,
                             int coordIndex,
                             boolean isNewShapePoint,
                             TopoMap t)

    <!-- -->

    - #### addLoopPre

          boolean addLoopPre(int nodeID,
                             Point2DD[] coords,
                             TopoMap t)

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](TopoMap.md)
- [Next Class](TopoValidationException.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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
