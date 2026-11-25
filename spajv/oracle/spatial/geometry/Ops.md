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

- [Prev Class](Mer.md)
- [Next Class](OpsJGeometry.md)

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

## Class Ops

- java.lang.Object

- - oracle.spatial.geometry.Ops

<!-- -->

-

  ------------------------------------------------------------------------



      public class Ops
      extends java.lang.Object

  Utility class for a variety of geometry operations.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `Ops``()`                   |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                    | Method and Description                                                                                                               |
    |--------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`JGeometry`](JGeometry.md) | `concaveHullDig``(`[`JGeometry`](JGeometry.md)` geom, double digN)`<br>Return the concave hull of the specified multipoint geometry. |
    | `static `[`JGeometry`](JGeometry.md) | `convexHull``(`[`JGeometry`](JGeometry.md)` geom)`<br>Return the convex hull of the input geometry.                                  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### Ops

          public Ops()

  <!-- -->

  - ### Method Detail

    - #### convexHull

          public static JGeometry convexHull(JGeometry geom)
                                      throws java.lang.Exception

      Return the convex hull of the input geometry. Currently circular arcs and circles will be replaced with their MBR (this behaviour is consistent with the database).
      Processing is done as if the points were in the plane and may not be appropriate for geodetic geometries.

      Parameters:
      `geom` -

      Returns:
      Throws:
      `java.lang.Exception` - "13050: unable to construct empty spatial object" if input has no points (May in future return an empty geometry)

    <!-- -->

    - #### concaveHullDig

          public static JGeometry concaveHullDig(JGeometry geom,
                                                 double digN)
                                          throws java.lang.Exception

      Return the concave hull of the specified multipoint geometry.
      Uses the "dig" algorithm of Jin-Seo Park and Se-Jonh Oh, "A New Concave Hull Algorithm and Concaveness Measure for n-dimensional Datasets". Starting with a convex hull, interior points that are within (edge length)/digN of an edge will be added to the hull, "digging out" dents in the hull. Larger values of digN limit dents to be shallower.

      Input geometry must be points only. Processing is done as if the points were on the plane and may not be appropriate for geodetic pointsets.

      Parameters:
      `geom` - a multipoint geometry

      `digN` - non-negative parameter to the dig algorithm; larger values result in less "digging" of concavities. A digN of 0 will dig until all points are on the hull. Good values are data dependent; try a value of 3.0 to start.

      Returns:
      resulting polygon

      Throws:
      `java.lang.Exception` - if the input points do not have a valid convex hull "13024: polygon has less than three segments" (convex hull is not a polygon) "13028: Invalid Gtype in the SDO_GEOMETRY object" (input is not a MULTIPOINT)

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

- [Prev Class](Mer.md)
- [Next Class](OpsJGeometry.md)

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
