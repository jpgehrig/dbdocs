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

- [Prev Class](JDBCUtil.md)
- [Next Class](KML2.md)

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

## Class KML

- java.lang.Object

- - oracle.spatial.util.KML

<!-- -->

-

  ------------------------------------------------------------------------



      public class KML
      extends java.lang.Object

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `KML``()`                   |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                | Method and Description                                                                              |
    |--------------------------------------------------|-----------------------------------------------------------------------------------------------------|
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToCurve``(org.w3c.dom.Node nd)`                                                            |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToGeometry``(org.w3c.dom.Node nd)`                                                         |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToGeometryCollection``(org.w3c.dom.Node nd)`                                               |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToLinearRing``(org.w3c.dom.Node nd)`                                                       |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToPoint``(org.w3c.dom.Node nd)`                                                            |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToPolygon``(org.w3c.dom.Node nd)`                                                          |
    | `static java.util.Vector`                        | `getGeometry``(org.w3c.dom.Node start, java.lang.String[] geometryTypes)`                           |
    | `static void`                                    | `getGeometry``(org.w3c.dom.Node start, java.lang.String[] geometryTypes, java.util.Vector result)`  |
    | `static java.lang.String`                        | `getNameSpace``()`                                                                                  |
    | `static void`                                    | `setConnection``(java.sql.Connection conn)`                                                         |
    | `static void`                                    | `setsrsNameSpace``(java.lang.String srsNameSpace)`                                                  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### KML

          public KML()

  <!-- -->

  - ### Method Detail

    - #### setConnection

          public static void setConnection(java.sql.Connection conn)

    <!-- -->

    - #### setsrsNameSpace

          public static void setsrsNameSpace(java.lang.String srsNameSpace)

    <!-- -->

    - #### getNameSpace

          public static java.lang.String getNameSpace()

    <!-- -->

    - #### fromNodeToPoint

          public static JGeometry fromNodeToPoint(org.w3c.dom.Node nd)
                                           throws DataException,
                                                  java.lang.Exception

      Throws:
      [`DataException`](../geometry/DataException.md)

      `java.lang.Exception`

    <!-- -->

    - #### fromNodeToCurve

          public static JGeometry fromNodeToCurve(org.w3c.dom.Node nd)
                                           throws DataException,
                                                  java.lang.Exception

      Throws:
      [`DataException`](../geometry/DataException.md)

      `java.lang.Exception`

    <!-- -->

    - #### fromNodeToPolygon

          public static JGeometry fromNodeToPolygon(org.w3c.dom.Node nd)
                                             throws DataException,
                                                    java.lang.Exception

      Throws:
      [`DataException`](../geometry/DataException.md)

      `java.lang.Exception`

    <!-- -->

    - #### fromNodeToGeometry

          public static JGeometry fromNodeToGeometry(org.w3c.dom.Node nd)
                                              throws DataException,
                                                     java.lang.Exception

      Throws:
      [`DataException`](../geometry/DataException.md)

      `java.lang.Exception`

    <!-- -->

    - #### fromNodeToGeometryCollection

          public static JGeometry fromNodeToGeometryCollection(org.w3c.dom.Node nd)
                                                        throws DataException,
                                                               java.lang.Exception

      Throws:
      [`DataException`](../geometry/DataException.md)

      `java.lang.Exception`

    <!-- -->

    - #### fromNodeToLinearRing

          public static JGeometry fromNodeToLinearRing(org.w3c.dom.Node nd)
                                                throws DataException,
                                                       java.lang.Exception

      Throws:
      [`DataException`](../geometry/DataException.md)

      `java.lang.Exception`

    <!-- -->

    - #### getGeometry

          public static java.util.Vector getGeometry(org.w3c.dom.Node start,
                                                     java.lang.String[] geometryTypes)

    <!-- -->

    - #### getGeometry

          public static void getGeometry(org.w3c.dom.Node start,
                                         java.lang.String[] geometryTypes,
                                         java.util.Vector result)

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

- [Prev Class](JDBCUtil.md)
- [Next Class](KML2.md)

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
