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

- [Prev Class](CoordRefSys.LambertConformalConicSrid.md)
- [Next Class](CoordRefSys.Srid.md)

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

## Class CoordRefSys.ProjectedSrid

- java.lang.Object

- - [oracle.spatial.util.CoordRefSys.Srid](CoordRefSys.Srid.md)

  - - oracle.spatial.util.CoordRefSys.ProjectedSrid

<!-- -->

- Direct Known Subclasses:
  [CoordRefSys.LambertConformalConicSrid](CoordRefSys.LambertConformalConicSrid.md), [CoordRefSys.TransverseMercatorSrid](CoordRefSys.TransverseMercatorSrid.md)

  <!-- -->

  Enclosing class:
  [CoordRefSys](CoordRefSys.md)

  ------------------------------------------------------------------------



      public abstract static class CoordRefSys.ProjectedSrid
      extends CoordRefSys.Srid

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                         | Method and Description                                                                                           |
    |-----------------------------------------------------------|------------------------------------------------------------------------------------------------------------------|
    | `double`                                                  | `getDistUnitsPerMeter``()`                                                                                       |
    | `double`                                                  | `getFalseEastingInMeters``()`                                                                                    |
    | `double`                                                  | `getFalseNorthingInMeters``()`                                                                                   |
    | [`CoordRefSys.GeodeticSrid`](CoordRefSys.GeodeticSrid.md) | `getGeodeticSrid``()`                                                                                            |
    | `abstract void`                                           | `project``(double[] coords, int dim)`                                                                            |
    | `abstract void`                                           | `reverseProject``(double[] coords, int dim)`                                                                     |
    | `java.lang.String`                                        | `toString``()`                                                                                                   |
    | `void`                                                    | `transform``(double[] coords, int dim, `[`CoordRefSys.GeodeticSrid`](CoordRefSys.GeodeticSrid.md)` targetSrid)`  |
    | `void`                                                    | `transform``(double[] coords, int dim, CoordRefSys.ProjectedSrid targetSrid)`                                    |

    - ### Methods inherited from class oracle.spatial.util.[CoordRefSys.Srid](CoordRefSys.Srid.md)

      [`getSampleTruthPoint`](CoordRefSys.Srid.md)`, `[`getSrid`](CoordRefSys.Srid.md)`, `[`transform`](CoordRefSys.Srid.md)`, `[`transform`](CoordRefSys.Srid.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getGeodeticSrid

          public CoordRefSys.GeodeticSrid getGeodeticSrid()

    <!-- -->

    - #### getDistUnitsPerMeter

          public double getDistUnitsPerMeter()

    <!-- -->

    - #### getFalseEastingInMeters

          public double getFalseEastingInMeters()

    <!-- -->

    - #### getFalseNorthingInMeters

          public double getFalseNorthingInMeters()

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      [`toString`](CoordRefSys.Srid.md) in class [`CoordRefSys.Srid`](CoordRefSys.Srid.md)

    <!-- -->

    - #### project

          public abstract void project(double[] coords,
                                       int dim)

    <!-- -->

    - #### reverseProject

          public abstract void reverseProject(double[] coords,
                                              int dim)

    <!-- -->

    - #### transform

          public void transform(double[] coords,
                                int dim,
                                CoordRefSys.GeodeticSrid targetSrid)

      Specified by:
      [`transform`](CoordRefSys.Srid.md) in class [`CoordRefSys.Srid`](CoordRefSys.Srid.md)

    <!-- -->

    - #### transform

          public void transform(double[] coords,
                                int dim,
                                CoordRefSys.ProjectedSrid targetSrid)

      Specified by:
      [`transform`](CoordRefSys.Srid.md) in class [`CoordRefSys.Srid`](CoordRefSys.Srid.md)

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

- [Prev Class](CoordRefSys.LambertConformalConicSrid.md)
- [Next Class](CoordRefSys.Srid.md)

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
