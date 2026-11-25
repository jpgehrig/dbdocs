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

- [Prev Class](Pair.md)
- [Next Class](RStarTree.md)

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

oracle.spatial.geometry

## Interface RNode

- All Known Implementing Classes:
  [FastJGeometry](FastJGeometry.md), [J3D_Geometry](J3D_Geometry.md), [JGeometry](JGeometry.md), [Mer](Mer.md)

  ------------------------------------------------------------------------



      public interface RNode

  Marks an object with a Mer.
  Since:
  12.3

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                           |
    |-------------------|------------------------------------------------------------------|
    | [`Mer`](Mer.md)   | `getMer``()`<br>Returns the bounding box of this spatial object. |

<!-- -->

- - ### Method Detail

    - #### getMer

          Mer getMer()

      Returns the bounding box of this spatial object.
      Returns:
      a Mer that contains this object, preferably the minimal Mer. The caller must not modify the returned Mer.

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

- [Prev Class](Pair.md)
- [Next Class](RStarTree.md)

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
