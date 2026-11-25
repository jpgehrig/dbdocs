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

- [Prev Class](JPoint3DD.md)
- [Next Class](Mer.md)

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

## Class LRSGeometryG3D

- java.lang.Object

- - oracle.spatial.geometry.LRSGeometryG3D

<!-- -->

-

  ------------------------------------------------------------------------



      public class LRSGeometryG3D
      extends java.lang.Object

  This class defines an LRS Geodetic 3D geometry object

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                    |
    |------------------------------------------------------------------------------------------------------------------------------------------------|
    | `LRSGeometryG3D``(`[`J3D_Geometry`](J3D_Geometry.md)` geometry, double[] measureArray, double smax, double flat, double geog_crs_uom_factor)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type        | Method and Description                                                                                                             |
    |--------------------------|------------------------------------------------------------------------------------------------------------------------------------|
    | `static LRSGeometryG3D`  | `clip``(LRSGeometryG3D lrsGeom, double ms, double me, double tolerance)`                                                           |
    | `static java.sql.Struct` | `clipG3D``(java.sql.Struct geom, NUMBER smax, NUMBER flat, NUMBER geog_crs_uom_factor, NUMBER ms, NUMBER me, NUMBER tolerance)`    |
    | `java.lang.Object`       | `clone``()`                                                                                                                        |
    | `static LRSGeometryG3D`  | `concatenate``(LRSGeometryG3D geom1, LRSGeometryG3D geom2, boolean shiftMeasure)`                                                  |
    | `static java.sql.Struct` | `defineG3D``(java.sql.Struct geom, NUMBER smax, NUMBER flat, NUMBER geog_crs_uom_factor, NUMBER ms, NUMBER me, NUMBER tolerance)`  |
    | `double`                 | `getEndMeasure``()`                                                                                                                |
    | `double`                 | `getEndMeasure``(int elemIndex)`                                                                                                   |
    | `double`                 | `getFlat``()`                                                                                                                      |
    | `double`                 | `getGeogCrsUomFactor``()`                                                                                                          |
    | `double`                 | `getLength``(double tolerance)`                                                                                                    |
    | `double`                 | `getSmax``()`                                                                                                                      |
    | `double`                 | `getStartMeasure``()`                                                                                                              |
    | `double`                 | `getStartMeasure``(int elemIndex)`                                                                                                 |
    | `boolean`                | `isDefined``()`                                                                                                                    |
    | `boolean`                | `isLRSGeom``()`                                                                                                                    |
    | `static NUMBER`          | `lengthG3D``(java.sql.Struct geom, NUMBER smax, NUMBER flat, NUMBER geog_crs_uom_factor, NUMBER tolerance)`                        |
    | `static java.sql.Struct` | `locateG3D``(java.sql.Struct geom, NUMBER smax, NUMBER flat, NUMBER geog_crs_uom_factor, NUMBER m, NUMBER tolerance)`              |
    | `static LRSGeometryG3D`  | `locatePoint``(LRSGeometryG3D lrsGeom, double m, double tolerance)`                                                                |
    | `static void`            | `main``(java.lang.String[] args)`                                                                                                  |
    | `static java.sql.Struct` | `projectG3D``(java.sql.Struct geom, NUMBER smax, NUMBER flat, NUMBER geog_crs_uom_factor, java.sql.Struct pt, NUMBER tolerance)`   |
    | `static LRSGeometryG3D`  | `projectPoint``(LRSGeometryG3D lrsGeom, LRSGeometryG3D pt, double tolerance)`                                                      |
    | `java.lang.String`       | `toString``()`                                                                                                                     |
    | `boolean`                | `validMeasure``(double m)`                                                                                                         |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### LRSGeometryG3D

          public LRSGeometryG3D(J3D_Geometry geometry,
                                double[] measureArray,
                                double smax,
                                double flat,
                                double geog_crs_uom_factor)

  <!-- -->

  - ### Method Detail

    - #### defineG3D

          public static java.sql.Struct defineG3D(java.sql.Struct geom,
                                                  NUMBER smax,
                                                  NUMBER flat,
                                                  NUMBER geog_crs_uom_factor,
                                                  NUMBER ms,
                                                  NUMBER me,
                                                  NUMBER tolerance)
                                           throws java.sql.SQLException,
                                                  java.lang.Exception

      Throws:
      `java.sql.SQLException`

      `java.lang.Exception`

    <!-- -->

    - #### locateG3D

          public static java.sql.Struct locateG3D(java.sql.Struct geom,
                                                  NUMBER smax,
                                                  NUMBER flat,
                                                  NUMBER geog_crs_uom_factor,
                                                  NUMBER m,
                                                  NUMBER tolerance)
                                           throws java.sql.SQLException,
                                                  java.lang.Exception

      Throws:
      `java.sql.SQLException`

      `java.lang.Exception`

    <!-- -->

    - #### clipG3D

          public static java.sql.Struct clipG3D(java.sql.Struct geom,
                                                NUMBER smax,
                                                NUMBER flat,
                                                NUMBER geog_crs_uom_factor,
                                                NUMBER ms,
                                                NUMBER me,
                                                NUMBER tolerance)
                                         throws java.sql.SQLException,
                                                java.lang.Exception

      Throws:
      `java.sql.SQLException`

      `java.lang.Exception`

    <!-- -->

    - #### projectG3D

          public static java.sql.Struct projectG3D(java.sql.Struct geom,
                                                   NUMBER smax,
                                                   NUMBER flat,
                                                   NUMBER geog_crs_uom_factor,
                                                   java.sql.Struct pt,
                                                   NUMBER tolerance)
                                            throws java.sql.SQLException,
                                                   java.lang.Exception

      Throws:
      `java.sql.SQLException`

      `java.lang.Exception`

    <!-- -->

    - #### lengthG3D

          public static NUMBER lengthG3D(java.sql.Struct geom,
                                         NUMBER smax,
                                         NUMBER flat,
                                         NUMBER geog_crs_uom_factor,
                                         NUMBER tolerance)
                                  throws java.sql.SQLException,
                                         java.lang.Exception

      Throws:
      `java.sql.SQLException`

      `java.lang.Exception`

    <!-- -->

    - #### isDefined

          public boolean isDefined()

    <!-- -->

    - #### isLRSGeom

          public boolean isLRSGeom()

    <!-- -->

    - #### getLength

          public double getLength(double tolerance)
                           throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getSmax

          public double getSmax()

    <!-- -->

    - #### getFlat

          public double getFlat()

    <!-- -->

    - #### getGeogCrsUomFactor

          public double getGeogCrsUomFactor()

    <!-- -->

    - #### getStartMeasure

          public double getStartMeasure()

    <!-- -->

    - #### getStartMeasure

          public double getStartMeasure(int elemIndex)

    <!-- -->

    - #### validMeasure

          public boolean validMeasure(double m)

    <!-- -->

    - #### getEndMeasure

          public double getEndMeasure()

    <!-- -->

    - #### getEndMeasure

          public double getEndMeasure(int elemIndex)

    <!-- -->

    - #### locatePoint

          public static LRSGeometryG3D locatePoint(LRSGeometryG3D lrsGeom,
                                                   double m,
                                                   double tolerance)
                                            throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### clip

          public static LRSGeometryG3D clip(LRSGeometryG3D lrsGeom,
                                            double ms,
                                            double me,
                                            double tolerance)
                                     throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### concatenate

          public static LRSGeometryG3D concatenate(LRSGeometryG3D geom1,
                                                   LRSGeometryG3D geom2,
                                                   boolean shiftMeasure)

    <!-- -->

    - #### projectPoint

          public static LRSGeometryG3D projectPoint(LRSGeometryG3D lrsGeom,
                                                    LRSGeometryG3D pt,
                                                    double tolerance)
                                             throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Object`

    <!-- -->

    - #### clone

          public java.lang.Object clone()

      Overrides:
      `clone` in class `java.lang.Object`

    <!-- -->

    - #### main

          public static void main(java.lang.String[] args)
                           throws java.lang.Exception

      Throws:
      `java.lang.Exception`

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

- [Prev Class](JPoint3DD.md)
- [Next Class](Mer.md)

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
