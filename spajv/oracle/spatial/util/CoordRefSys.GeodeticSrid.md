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

- [Prev Class](CoordRefSys.md)
- [Next Class](CoordRefSys.LambertConformalConicSrid.md)

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

## Class CoordRefSys.GeodeticSrid

- java.lang.Object

- - [oracle.spatial.util.CoordRefSys.Srid](CoordRefSys.Srid.md)

  - - oracle.spatial.util.CoordRefSys.GeodeticSrid

<!-- -->

- Enclosing class:
  [CoordRefSys](CoordRefSys.md)

  ------------------------------------------------------------------------



      public static class CoordRefSys.GeodeticSrid
      extends CoordRefSys.Srid

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                             |
    |--------------------|--------------------------------------------------------------------------------------------------------------------|
    | `double`           | `getAngleUnitsPerRadian``()`                                                                                       |
    | `double`           | `getInverseFlattening``()`                                                                                         |
    | `double`           | `getPrimeMeridianInRadian``()`                                                                                     |
    | `double`           | `getSemiMajorAxisInMeters``()`                                                                                     |
    | `double[]`         | `getToWgs84Params``()`                                                                                             |
    | `java.lang.String` | `toString``()`                                                                                                     |
    | `void`             | `transform``(double[] coords, int dim, CoordRefSys.GeodeticSrid targetSrid)`                                       |
    | `void`             | `transform``(double[] coords, int dim, `[`CoordRefSys.ProjectedSrid`](CoordRefSys.ProjectedSrid.md)` targetSrid)`  |

    - ### Methods inherited from class oracle.spatial.util.[CoordRefSys.Srid](CoordRefSys.Srid.md)

      [`getSampleTruthPoint`](CoordRefSys.Srid.md)`, `[`getSrid`](CoordRefSys.Srid.md)`, `[`transform`](CoordRefSys.Srid.md)`, `[`transform`](CoordRefSys.Srid.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getSemiMajorAxisInMeters

          public double getSemiMajorAxisInMeters()

    <!-- -->

    - #### getInverseFlattening

          public double getInverseFlattening()

    <!-- -->

    - #### getToWgs84Params

          public double[] getToWgs84Params()

    <!-- -->

    - #### getAngleUnitsPerRadian

          public double getAngleUnitsPerRadian()

    <!-- -->

    - #### getPrimeMeridianInRadian

          public double getPrimeMeridianInRadian()

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      [`toString`](CoordRefSys.Srid.md) in class [`CoordRefSys.Srid`](CoordRefSys.Srid.md)

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

- [Prev Class](CoordRefSys.md)
- [Next Class](CoordRefSys.LambertConformalConicSrid.md)

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
