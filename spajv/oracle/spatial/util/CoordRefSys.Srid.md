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

- [Prev Class](CoordRefSys.ProjectedSrid.md)
- [Next Class](CoordRefSys.TransverseMercatorSrid.md)

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

oracle.spatial.util

## Class CoordRefSys.Srid

- java.lang.Object

- - oracle.spatial.util.CoordRefSys.Srid

<!-- -->

- Direct Known Subclasses:
  [CoordRefSys.GeodeticSrid](CoordRefSys.GeodeticSrid.md), [CoordRefSys.ProjectedSrid](CoordRefSys.ProjectedSrid.md)

  <!-- -->

  Enclosing class:
  [CoordRefSys](CoordRefSys.md)

  ------------------------------------------------------------------------



      public abstract static class CoordRefSys.Srid
      extends java.lang.Object

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                       | Method and Description                                                                                                                   |
    |-----------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
    | [`JGeometry`](../geometry/JGeometry.md) | `getSampleTruthPoint``()`                                                                                                                |
    | `long`                                  | `getSrid``()`                                                                                                                            |
    | `java.lang.String`                      | `toString``()`                                                                                                                           |
    | `abstract void`                         | `transform``(double[] coords, int dim, `[`CoordRefSys.GeodeticSrid`](CoordRefSys.GeodeticSrid.md)` targetSrid)`                          |
    | `abstract void`                         | `transform``(double[] coords, int dim, `[`CoordRefSys.ProjectedSrid`](CoordRefSys.ProjectedSrid.md)` targetSrid)`                        |
    | [`JGeometry`](../geometry/JGeometry.md) | `transform``(`[`JGeometry`](../geometry/JGeometry.md)` geom, `[`CoordRefSys.GeodeticSrid`](CoordRefSys.GeodeticSrid.md)` targetSrid)`    |
    | [`JGeometry`](../geometry/JGeometry.md) | `transform``(`[`JGeometry`](../geometry/JGeometry.md)` geom, `[`CoordRefSys.ProjectedSrid`](CoordRefSys.ProjectedSrid.md)` targetSrid)`  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getSrid

          public long getSrid()

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Object`

    <!-- -->

    - #### getSampleTruthPoint

          public JGeometry getSampleTruthPoint()

    <!-- -->

    - #### transform

          public abstract void transform(double[] coords,
                                         int dim,
                                         CoordRefSys.GeodeticSrid targetSrid)

    <!-- -->

    - #### transform

          public abstract void transform(double[] coords,
                                         int dim,
                                         CoordRefSys.ProjectedSrid targetSrid)

    <!-- -->

    - #### transform

          public JGeometry transform(JGeometry geom,
                                     CoordRefSys.GeodeticSrid targetSrid)

    <!-- -->

    - #### transform

          public JGeometry transform(JGeometry geom,
                                     CoordRefSys.ProjectedSrid targetSrid)

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

- [Prev Class](CoordRefSys.ProjectedSrid.md)
- [Next Class](CoordRefSys.TransverseMercatorSrid.md)

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
