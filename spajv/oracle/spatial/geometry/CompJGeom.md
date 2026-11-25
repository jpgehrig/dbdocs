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

- [Prev Class](Chain.CenterPoint.md)
- [Next Class](CoordSysInfo.md)

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

## Class CompJGeom

- java.lang.Object

- - oracle.spatial.geometry.CompJGeom

<!-- -->

-

  ------------------------------------------------------------------------



      public final class CompJGeom
      extends java.lang.Object

  Since:
  release specific (what release of product did this appear in)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `CompJGeom``()`             |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                                                                                        |
    |-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static double`   | `distToLine``(double px, double py, double q1x, double q1y, double q2x, double q2y)`<br>Finds the planar closest distance from a point to a line segment.                                                     |
    | `static double`   | `distToLine``(`[`JPoint2DD`](JPoint2DD.md)` pt, `[`JPoint2DD`](JPoint2DD.md)` q1, `[`JPoint2DD`](JPoint2DD.md)` q2, `[`CoordSysInfo`](CoordSysInfo.md)` CSI)`<br>Compute the distance from a point to a line. |
    | `static boolean`  | `lineLineIntersect``(double a1x, double a1y, double a2x, double a2y, double b1x, double b1y, double b2x, double b2y, double[] c)`<br>Finds the open-set intersection of two line segments, if any.            |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### CompJGeom

          public CompJGeom()

  <!-- -->

  - ### Method Detail

    - #### lineLineIntersect

          public static final boolean lineLineIntersect(double a1x,
                                                        double a1y,
                                                        double a2x,
                                                        double a2y,
                                                        double b1x,
                                                        double b1y,
                                                        double b2x,
                                                        double b2y,
                                                        double[] c)

      Finds the open-set intersection of two line segments, if any.
      Returns false ("no intersection") if the lines are nearly parallel (regardless of whether they cross).

      If the end-point of a segment lies very near to the other segment, intersection test is not reliable; the caller should test the point-on-line case separately. If the endpoint lies exactly on an endpoint of the other segment this method guarantees to return false.

      Parameters:
      `a1x` - the first endpoint x-value of line segment a

      `a1y` - the first endpoint y-value of line segment a

      `a2x` - the first endpoint x-value of line segment a

      `a2y` - the first endpoint y-value of line segment a

      `b1x` - the first endpoint x-value of line segment b

      `b1y` - the first endpoint y-value of line segment b

      `b2x` - the first endpoint x-value of line segment b

      `b2y` - the first endpoint y-value of line segment a

      `c` - the intersection (if any). May pass null. If non-null, may be overwritten even if result is false.

      Returns:
      true if there is an intersection; false otherwise

    <!-- -->

    - #### distToLine

          public static final double distToLine(JPoint2DD pt,
                                                JPoint2DD q1,
                                                JPoint2DD q2,
                                                CoordSysInfo CSI)

      Compute the distance from a point to a line. Geodetic computations assume a sphere. All input is in degrees.
      Parameters:
      `pt` - the point

      `q1` - one end of the line

      `q2` - other end of the line

      `CSI` - coordinate system

      Returns:
      distance in coordiante system units (meters if geodetic)

    <!-- -->

    - #### distToLine

          public static final double distToLine(double px,
                                                double py,
                                                double q1x,
                                                double q1y,
                                                double q2x,
                                                double q2y)

      Finds the planar closest distance from a point to a line segment.
      Parameters:
      `p` - The point

      `q1` - The first vertex of the line segment

      `q2` - The second vertex of the line segment

      Returns:
      The distance in coordinate system units

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

- [Prev Class](Chain.CenterPoint.md)
- [Next Class](CoordSysInfo.md)

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
