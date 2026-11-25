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

- [Prev Class](JGeometry.md)
- [Next Class](JGeometry.Point.md)

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

## Interface JGeometry.GeomParser

- Enclosing class:
  [JGeometry](JGeometry.md)

  ------------------------------------------------------------------------



      public static interface JGeometry.GeomParser

  Callbacks for parsing this geometry via parseGeometry

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                 |
    |-------------------|--------------------------------------------------------------------------------------------------------|
    | `void`            | `circle``(double p1x, double p1y, double p2x, double p2y, double p3x, double p3y)`                     |
    | `void`            | `finish``()`                                                                                           |
    | `void`            | `linestring``(java.util.List<oracle.spatial.geometry.JGeometry.LineStringInfo> lineinfo)`              |
    | `void`            | `point``(double x, double y)`                                                                          |
    | `void`            | `ring``(boolean interior, java.util.List<oracle.spatial.geometry.JGeometry.LineStringInfo> lineinfo)`  |

<!-- -->

- - ### Method Detail

    - #### point

          void point(double x,
                     double y)
              throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### circle

          void circle(double p1x,
                      double p1y,
                      double p2x,
                      double p2y,
                      double p3x,
                      double p3y)
               throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### ring

          void ring(boolean interior,
                    java.util.List<oracle.spatial.geometry.JGeometry.LineStringInfo> lineinfo)
             throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### linestring

          void linestring(java.util.List<oracle.spatial.geometry.JGeometry.LineStringInfo> lineinfo)
                   throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### finish

          void finish()
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

- [Prev Class](JGeometry.md)
- [Next Class](JGeometry.Point.md)

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
