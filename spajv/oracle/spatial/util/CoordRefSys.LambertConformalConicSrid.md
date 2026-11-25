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

- [Prev Class](CoordRefSys.GeodeticSrid.md)
- [Next Class](CoordRefSys.ProjectedSrid.md)

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

## Class CoordRefSys.LambertConformalConicSrid

- java.lang.Object

- - [oracle.spatial.util.CoordRefSys.Srid](CoordRefSys.Srid.md)

  - - [oracle.spatial.util.CoordRefSys.ProjectedSrid](CoordRefSys.ProjectedSrid.md)

    - - oracle.spatial.util.CoordRefSys.LambertConformalConicSrid

<!-- -->

- Enclosing class:
  [CoordRefSys](CoordRefSys.md)

  ------------------------------------------------------------------------



      public static class CoordRefSys.LambertConformalConicSrid
      extends CoordRefSys.ProjectedSrid

<!-- -->

- - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                         |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `project``(double[] coords, int dim)`                                                                                                                                                                                                                                                          |
    | `static void`     | `registerLambertConformalConicSrid``(long srid, long geodeticSrid, double distUnitsPerMeter, double falseEastingInMeters, double falseNorthingInMeters, double latitudeOfOriginInRadian, double centralMeridianInRadian, double standardParallel1InRadian, double standardParallel2InRadian)`  |
    | `void`            | `reverseProject``(double[] coords, int dim)`                                                                                                                                                                                                                                                   |

    - ### Methods inherited from class oracle.spatial.util.[CoordRefSys.ProjectedSrid](CoordRefSys.ProjectedSrid.md)

      [`getDistUnitsPerMeter`](CoordRefSys.ProjectedSrid.md)`, `[`getFalseEastingInMeters`](CoordRefSys.ProjectedSrid.md)`, `[`getFalseNorthingInMeters`](CoordRefSys.ProjectedSrid.md)`, `[`getGeodeticSrid`](CoordRefSys.ProjectedSrid.md)`, `[`toString`](CoordRefSys.ProjectedSrid.md)`, `[`transform`](CoordRefSys.ProjectedSrid.md)`, `[`transform`](CoordRefSys.ProjectedSrid.md)

    <!-- -->

    - ### Methods inherited from class oracle.spatial.util.[CoordRefSys.Srid](CoordRefSys.Srid.md)

      [`getSampleTruthPoint`](CoordRefSys.Srid.md)`, `[`getSrid`](CoordRefSys.Srid.md)`, `[`transform`](CoordRefSys.Srid.md)`, `[`transform`](CoordRefSys.Srid.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### registerLambertConformalConicSrid

          public static void registerLambertConformalConicSrid(long srid,
                                                               long geodeticSrid,
                                                               double distUnitsPerMeter,
                                                               double falseEastingInMeters,
                                                               double falseNorthingInMeters,
                                                               double latitudeOfOriginInRadian,
                                                               double centralMeridianInRadian,
                                                               double standardParallel1InRadian,
                                                               double standardParallel2InRadian)

    <!-- -->

    - #### project

          public void project(double[] coords,
                              int dim)

      Specified by:
      [`project`](CoordRefSys.ProjectedSrid.md) in class [`CoordRefSys.ProjectedSrid`](CoordRefSys.ProjectedSrid.md)

    <!-- -->

    - #### reverseProject

          public void reverseProject(double[] coords,
                                     int dim)

      Specified by:
      [`reverseProject`](CoordRefSys.ProjectedSrid.md) in class [`CoordRefSys.ProjectedSrid`](CoordRefSys.ProjectedSrid.md)

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

- [Prev Class](CoordRefSys.GeodeticSrid.md)
- [Next Class](CoordRefSys.ProjectedSrid.md)

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
