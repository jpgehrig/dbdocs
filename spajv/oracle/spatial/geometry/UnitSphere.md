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

- [Prev Class](Union.md)
- Next Class

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

## Class UnitSphere

- java.lang.Object

- - [oracle.spatial.geometry.JPoint3DD](JPoint3DD.md)

  - - oracle.spatial.geometry.UnitSphere

<!-- -->

-

  ------------------------------------------------------------------------



      public final class UnitSphere
      extends JPoint3DD

  Immutable 3D representation of a point on a sphere with conversions to and from long/lat. The vector is always normalized (length 1) unless it is zero.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                 |
    |---------------------------------------------------------------------------------------------------------------------------------------------|
    | `UnitSphere``(double x, double y)`<br>Create this UnitSphere equivalent to the given long/lat point.                                        |
    | `UnitSphere``(double x, double y, double z)`<br>Creates a normalized (x, y, z) (unless they are all zero, in which case creates (0, 0, 0)). |
    | `UnitSphere``(`[`JPoint2DD`](JPoint2DD.md)` pt2D)`<br>Create this UnitSphere equivalent to the given long/lat point.                        |
    | `UnitSphere``(`[`JPoint3DD`](JPoint3DD.md)` pt)`<br>Creates a 3D vector on the unit sphere as a normalized copy of the passed 3D point.     |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                    | Method and Description                                                                                                                                                                                 |
    |--------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`JPoint2DD`](JPoint2DD.md)          | `computeLongLat``()`<br>Compute and return the long/lat equivalent to this unit-sphere point.                                                                                                          |
    | `static double`                      | `distancePtLineRadians``(UnitSphere pt, UnitSphere a, UnitSphere b)`<br>Return the distance on the unit sphere (an angle) between a point and a great-circle line segment.                             |
    | `static double`                      | `distanceRadians``(UnitSphere a, UnitSphere b)`<br>Distance on the unit sphere between two points.                                                                                                     |
    | `boolean`                            | `equals``(java.lang.Object obj)`<br>Equality is based on the (x, y, z) values.                                                                                                                         |
    | [`JPoint2DD`](JPoint2DD.md)          | `getLongLat``()`<br>Retuns original long/lat equivalent of this UnitSphere, or if none, computes one.                                                                                                  |
    | `static `[`JPoint3DD`](JPoint3DD.md) | `greatCircle``(UnitSphere a, UnitSphere b)`<br>Compute the great circle through two points, and return it as the vector perpindicular to the plane through the two points and the center of the earth. |
    | `int`                                | `hashCode``()`                                                                                                                                                                                         |
    | `static UnitSphere`                  | `intersect``(`[`JPoint3DD`](JPoint3DD.md)` GCa, `[`JPoint3DD`](JPoint3DD.md)` GCb)`<br>Return the intersection of two great-circles.                                                                   |
    | `static UnitSphere`                  | `intersect``(UnitSphere a1, UnitSphere a2, UnitSphere b1, UnitSphere b2)`<br>Return an intersection of two great-circle segments, or null if none.                                                     |
    | `static UnitSphere`                  | `nearestPtLine``(UnitSphere pt, UnitSphere a, UnitSphere b)`<br>Return a point on great-circle segment ab that is closest to pt.                                                                       |
    | `java.lang.String`                   | `toString``()`                                                                                                                                                                                         |

    - ### Methods inherited from class oracle.spatial.geometry.[JPoint3DD](JPoint3DD.md)

      [`cross`](JPoint3DD.md)`, `[`dot`](JPoint3DD.md)`, `[`getX`](JPoint3DD.md)`, `[`getY`](JPoint3DD.md)`, `[`getZ`](JPoint3DD.md)`, `[`isZero`](JPoint3DD.md)`, `[`length`](JPoint3DD.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### UnitSphere

          public UnitSphere(double x,
                            double y)

      Create this UnitSphere equivalent to the given long/lat point.
      Parameters:
      `x` - longitude in degrees

      `y` - latitude in degrees

    <!-- -->

    - #### UnitSphere

          public UnitSphere(JPoint2DD pt2D)

      Create this UnitSphere equivalent to the given long/lat point.
      Parameters:
      `pt2D` - (Longitude, latitude) in degrees.

    <!-- -->

    - #### UnitSphere

          public UnitSphere(double x,
                            double y,
                            double z)

      Creates a normalized (x, y, z) (unless they are all zero, in which case creates (0, 0, 0)).
      Parameters:
      `x` -

      `y` -

      `z` -

    <!-- -->

    - #### UnitSphere

          public UnitSphere(JPoint3DD pt)

      Creates a 3D vector on the unit sphere as a normalized copy of the passed 3D point.
      Parameters:
      `pt` -

  <!-- -->

  - ### Method Detail

    - #### distanceRadians

          public static double distanceRadians(UnitSphere a,
                                               UnitSphere b)

      Distance on the unit sphere between two points. Result is just the angle between the two points (vectors); multiply by the radius of the earth to get the distance in the units you want.
      Parameters:
      `a` -

      `b` -

      Returns:
      angle in radians

    <!-- -->

    - #### greatCircle

          public static JPoint3DD greatCircle(UnitSphere a,
                                              UnitSphere b)

      Compute the great circle through two points, and return it as the vector perpindicular to the plane through the two points and the center of the earth. Note that vector is not normalized.
      Parameters:
      `a` -

      `b` -

      Returns:
      perpindicular to plane through a, b, center-of-earth

    <!-- -->

    - #### intersect

          public static UnitSphere intersect(JPoint3DD GCa,
                                             JPoint3DD GCb)

      Return the intersection of two great-circles.
      Parameters:
      `GCa` - a vector perpindicular to one great-circle cut through the earth

      `GCb` - a vector perpindicular to the other great circle.

      Returns:
      vector pointing along the line of intersection (Or zero-length, if coincident)

    <!-- -->

    - #### intersect

          public static UnitSphere intersect(UnitSphere a1,
                                             UnitSphere a2,
                                             UnitSphere b1,
                                             UnitSphere b2)

      Return an intersection of two great-circle segments, or null if none. Note that a great-circle that is larger than half the earth could have two intersections, but since we always interpret great-circle segments to be the short way around, the only way that could happen is via two great-circle segments between antipods, and we have no way of representing such great-circles distinctly anyway.
      Does not reliably find endpoint-on-segment intersections; test for those separately.

      Parameters:
      `a1` - (a1, a2) is the first segment

      `a2` -

      `b1` - (b1, b2) is the second segment

      `b2` -

      Returns:
      intersection point, or null

    <!-- -->

    - #### distancePtLineRadians

          public static double distancePtLineRadians(UnitSphere pt,
                                                     UnitSphere a,
                                                     UnitSphere b)

      Return the distance on the unit sphere (an angle) between a point and a great-circle line segment.
      Parameters:
      `pt` -

      `a` -

      `b` -

      Returns:
      distance as an angle in radians

    <!-- -->

    - #### nearestPtLine

          public static UnitSphere nearestPtLine(UnitSphere pt,
                                                 UnitSphere a,
                                                 UnitSphere b)

      Return a point on great-circle segment ab that is closest to pt.
      Parameters:
      `pt` -

      `a` -

      `b` -

      Returns:
      closest point on segment

    <!-- -->

    - #### getLongLat

          public JPoint2DD getLongLat()

      Retuns original long/lat equivalent of this UnitSphere, or if none, computes one.
      Returns:
      copy of the long/lat equivalent of this UnitSphere.

    <!-- -->

    - #### computeLongLat

          public JPoint2DD computeLongLat()

      Compute and return the long/lat equivalent to this unit-sphere point. Compare to getLongLat(). Does not use original value.
      Returns:
      computed longitude/latitude equivalent

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      [`toString`](JPoint3DD.md) in class [`JPoint3DD`](JPoint3DD.md)

    <!-- -->

    - #### equals

          public boolean equals(java.lang.Object obj)

      Equality is based on the (x, y, z) values. The origLongLat field is not included.
      Overrides:

      [`equals`](JPoint3DD.md) in class [`JPoint3DD`](JPoint3DD.md)

      Parameters:

      `obj` -

      Returns:

    <!-- -->

    - #### hashCode

          public int hashCode()

      Overrides:
      [`hashCode`](JPoint3DD.md) in class [`JPoint3DD`](JPoint3DD.md)

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

- [Prev Class](Union.md)
- Next Class

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
