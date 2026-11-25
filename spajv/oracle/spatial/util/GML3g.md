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

- [Prev Class](GML3.GMLVersion.md)
- [Next Class](GroupingLOD1Generalization.md)

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

## Class GML3g

- java.lang.Object

- - oracle.spatial.util.GML3g

<!-- -->

-

  ------------------------------------------------------------------------



      public class GML3g
      extends java.lang.Object

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                                                                                                       |
    |---------------------------|-----------------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String` | `GML_COORD_ELEMENT`<br>Deprecated with GML version 3.0                                                                      |
    | `static java.lang.String` | `GML_COORDINATES_ELEMENT`<br>Deprecated with GML 3.1.0 Use the explicit properties "lowerCorner" and "upperCorner" instead. |
    | `static java.lang.String` | `GML_LOWER_CORNER_ELEMENT`                                                                                                  |
    | `static java.lang.String` | `GML_POS_LIST_ELEMENT`                                                                                                      |
    | `static java.lang.String` | `GML_SRS_DIMENSION_ATTRIBUTE`                                                                                               |
    | `static java.lang.String` | `GML_UPPER_CORNER_ELEMENT`                                                                                                  |
    | `static java.lang.String` | `GML_X`                                                                                                                     |
    | `static java.lang.String` | `GML_Y`                                                                                                                     |
    | `static java.lang.String` | `GML_Z`                                                                                                                     |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `GML3g``()`                 |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                | Method and Description                                                       |
    |--------------------------------------------------|------------------------------------------------------------------------------|
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToCompositeCurve``(org.w3c.dom.Node nd)`                            |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToCompositeSolid``(org.w3c.dom.Node nd)`                            |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToCompositeSurface``(org.w3c.dom.Node nd)`                          |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToCurve``(org.w3c.dom.Node nd)`                                     |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToEnvelope``(org.w3c.dom.Node nd)`                                  |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToGeometry``(org.w3c.dom.Node nd)`                                  |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToGeometry``(org.w3c.dom.Node nd, int coordOrder)`                  |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToGeometryCollection``(org.w3c.dom.Node nd)`                        |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToLinearRing``(org.w3c.dom.Node nd)`                                |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToLineString``(org.w3c.dom.Node nd)`                                |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToMultiCurve``(org.w3c.dom.Node nd)`                                |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToMultiPoint``(org.w3c.dom.Node nd)`                                |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToMultiSolid``(org.w3c.dom.Node nd)`                                |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToMultiSurface``(org.w3c.dom.Node nd)`                              |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToPoint``(org.w3c.dom.Node nd)`                                     |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToPolygon``(org.w3c.dom.Node nd)`                                   |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToSolid``(org.w3c.dom.Node nd)`                                     |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToSurface``(org.w3c.dom.Node nd)`                                   |
    | `static java.lang.String`                        | `getNameSpace``()`                                                           |
    | `static int`                                     | `reverseAxisOrder``(int coordOrder, int theSRID, java.sql.Connection conn)`  |
    | `static void`                                    | `setConnection``(java.sql.Connection conn)`                                  |
    | `static void`                                    | `setsrsNameSpace``(java.lang.String srsNameSpace)`                           |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `switchXYOrdinates``(`[`JGeometry`](../geometry/JGeometry.md)` g1)`          |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### GML_POS_LIST_ELEMENT

          public static final java.lang.String GML_POS_LIST_ELEMENT

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GML_SRS_DIMENSION_ATTRIBUTE

          public static final java.lang.String GML_SRS_DIMENSION_ATTRIBUTE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GML_COORDINATES_ELEMENT

          public static final java.lang.String GML_COORDINATES_ELEMENT

      Deprecated with GML 3.1.0 Use the explicit properties "lowerCorner" and "upperCorner" instead.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GML_COORD_ELEMENT

          public static final java.lang.String GML_COORD_ELEMENT

      Deprecated with GML version 3.0
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GML_LOWER_CORNER_ELEMENT

          public static final java.lang.String GML_LOWER_CORNER_ELEMENT

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GML_UPPER_CORNER_ELEMENT

          public static final java.lang.String GML_UPPER_CORNER_ELEMENT

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GML_X

          public static final java.lang.String GML_X

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GML_Y

          public static final java.lang.String GML_Y

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GML_Z

          public static final java.lang.String GML_Z

      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### GML3g

          public GML3g()

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

    - #### fromNodeToEnvelope

          public static final JGeometry fromNodeToEnvelope(org.w3c.dom.Node nd)
                                                    throws DataException,
                                                           java.lang.Exception

      Throws:
      [`DataException`](../geometry/DataException.md)

      `java.lang.Exception`

    <!-- -->

    - #### fromNodeToLineString

          public static JGeometry fromNodeToLineString(org.w3c.dom.Node nd)
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

    - #### fromNodeToSurface

          public static JGeometry fromNodeToSurface(org.w3c.dom.Node nd)
                                             throws DataException,
                                                    java.lang.Exception

      Throws:
      [`DataException`](../geometry/DataException.md)

      `java.lang.Exception`

    <!-- -->

    - #### fromNodeToMultiCurve

          public static JGeometry fromNodeToMultiCurve(org.w3c.dom.Node nd)
                                                throws DataException,
                                                       java.lang.Exception

      Throws:
      [`DataException`](../geometry/DataException.md)

      `java.lang.Exception`

    <!-- -->

    - #### fromNodeToMultiPoint

          public static JGeometry fromNodeToMultiPoint(org.w3c.dom.Node nd)
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

    - #### fromNodeToGeometry

          public static JGeometry fromNodeToGeometry(org.w3c.dom.Node nd,
                                                     int coordOrder)
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

    - #### fromNodeToMultiSurface

          public static JGeometry fromNodeToMultiSurface(org.w3c.dom.Node nd)
                                                  throws DataException,
                                                         java.lang.Exception

      Parameters:
      `nd` - A Node representing the input GML

      Returns:
      The resulting JGeometry

      Throws:
      [`DataException`](../geometry/DataException.md)

      `java.lang.Exception`

    <!-- -->

    - #### fromNodeToCompositeCurve

          public static JGeometry fromNodeToCompositeCurve(org.w3c.dom.Node nd)
                                                    throws DataException,
                                                           java.lang.Exception,
                                                           GeometryExceptionWithContext

      Throws:
      [`DataException`](../geometry/DataException.md)

      `java.lang.Exception`

      [`GeometryExceptionWithContext`](GeometryExceptionWithContext.md)

    <!-- -->

    - #### fromNodeToCompositeSurface

          public static JGeometry fromNodeToCompositeSurface(org.w3c.dom.Node nd)
                                                      throws DataException,
                                                             java.lang.Exception

      Throws:
      [`DataException`](../geometry/DataException.md)

      `java.lang.Exception`

    <!-- -->

    - #### fromNodeToSolid

          public static JGeometry fromNodeToSolid(org.w3c.dom.Node nd)
                                           throws DataException,
                                                  java.lang.Exception

      Throws:
      [`DataException`](../geometry/DataException.md)

      `java.lang.Exception`

    <!-- -->

    - #### fromNodeToCompositeSolid

          public static JGeometry fromNodeToCompositeSolid(org.w3c.dom.Node nd)
                                                    throws DataException,
                                                           java.lang.Exception

      Throws:
      [`DataException`](../geometry/DataException.md)

      `java.lang.Exception`

    <!-- -->

    - #### fromNodeToMultiSolid

          public static JGeometry fromNodeToMultiSolid(org.w3c.dom.Node nd)
                                                throws DataException,
                                                       java.lang.Exception

      Throws:
      [`DataException`](../geometry/DataException.md)

      `java.lang.Exception`

    <!-- -->

    - #### reverseAxisOrder

          public static int reverseAxisOrder(int coordOrder,
                                             int theSRID,
                                             java.sql.Connection conn)
                                      throws DataException,
                                             java.lang.Exception

      Throws:
      [`DataException`](../geometry/DataException.md)

      `java.lang.Exception`

    <!-- -->

    - #### switchXYOrdinates

          public static JGeometry switchXYOrdinates(JGeometry g1)
                                             throws DataException,
                                                    java.lang.Exception

      Throws:
      [`DataException`](../geometry/DataException.md)

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

- [Prev Class](GML3.GMLVersion.md)
- [Next Class](GroupingLOD1Generalization.md)

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
