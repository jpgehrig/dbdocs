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

- [Prev Class](ShapefileFeatureJGeom.md)
- [Next Class](SqlLdrStreamWrapper.md)

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

## Class ShapefileReaderJGeom

- java.lang.Object

- - oracle.spatial.util.ShapefileReaderJGeom

<!-- -->

-

  ------------------------------------------------------------------------



      public class ShapefileReaderJGeom
      extends java.lang.Object

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description |
    |-------------------|-----------------------|
    | `static int`      | `AV_MULTIPOINT`       |
    | `static int`      | `AV_MULTIPOINTM`      |
    | `static int`      | `AV_MULTIPOINTZ`      |
    | `static int`      | `AV_NULL`             |
    | `static int`      | `AV_POINT`            |
    | `static int`      | `AV_POINTM`           |
    | `static int`      | `AV_POINTZ`           |
    | `static int`      | `AV_POLYGON`          |
    | `static int`      | `AV_POLYGONM`         |
    | `static int`      | `AV_POLYGONZ`         |
    | `static int`      | `AV_POLYLINE`         |
    | `static int`      | `AV_POLYLINEM`        |
    | `static int`      | `AV_POLYLINEZ`        |
    | `static boolean`  | `shpMval`             |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                 |
    |-------------------------------------------------------------------------------------------------------------|
    | `ShapefileReaderJGeom``(java.lang.String name)`<br>construct an object out of the specified shapefile name. |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                | Method and Description                                                                    |
    |--------------------------------------------------|-------------------------------------------------------------------------------------------|
    | `void`                                           | `closeShapefile``()`<br>close this shapefile.                                             |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `getGeometry``(byte[] recBuffer, int srid)`                                               |
    | `byte[]`                                         | `getGeometryBytes``(int nth)`<br>retrieve nth shape record and return it as a byte array. |
    | `double`                                         | `getMaxMeasure``()`<br>return the maximum Measure value in file.                          |
    | `double`                                         | `getMaxX``()`<br>return the maximum X value in file.                                      |
    | `double`                                         | `getMaxY``()`<br>return the maximum Y value in file.                                      |
    | `double`                                         | `getMaxZ``()`<br>return the maximum Z value in file.                                      |
    | `double`                                         | `getMinMeasure``()`<br>return the minimum Measure value in file.                          |
    | `double`                                         | `getMinX``()`<br>return the minimum X value in file.                                      |
    | `double`                                         | `getMinY``()`<br>return the minimum Y value in file.                                      |
    | `double`                                         | `getMinZ``()`<br>return the minimum Z value in file.                                      |
    | `static int`                                     | `getShpDims``(int type, double maxM)`                                                     |
    | `int`                                            | `getShpFileType``()`<br>return the Shape Type in the file.                                |
    | `int`                                            | `numRecords``()`<br>return the number of shape records in the file.                       |
    | `static void`                                    | `swapBytes``(byte[] buf, int offset, int len)`                                            |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### AV_NULL

          public static final int AV_NULL

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### AV_POINT

          public static final int AV_POINT

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### AV_POLYLINE

          public static final int AV_POLYLINE

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### AV_POLYGON

          public static final int AV_POLYGON

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### AV_MULTIPOINT

          public static final int AV_MULTIPOINT

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### AV_POINTZ

          public static final int AV_POINTZ

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### AV_POLYLINEZ

          public static final int AV_POLYLINEZ

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### AV_POLYGONZ

          public static final int AV_POLYGONZ

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### AV_MULTIPOINTZ

          public static final int AV_MULTIPOINTZ

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### AV_POINTM

          public static final int AV_POINTM

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### AV_POLYLINEM

          public static final int AV_POLYLINEM

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### AV_POLYGONM

          public static final int AV_POLYGONM

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### AV_MULTIPOINTM

          public static final int AV_MULTIPOINTM

      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### shpMval

          public static boolean shpMval

  <!-- -->

  - ### Constructor Detail

    - #### ShapefileReaderJGeom

          public ShapefileReaderJGeom(java.lang.String name)
                               throws java.io.IOException

      construct an object out of the specified shapefile name.
      Throws:
      `java.io.IOException`

  <!-- -->

  - ### Method Detail

    - #### getShpDims

          public static int getShpDims(int type,
                                       double maxM)
                                throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### getGeometry

          public static JGeometry getGeometry(byte[] recBuffer,
                                              int srid)
                                       throws java.lang.Exception

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### swapBytes

          public static void swapBytes(byte[] buf,
                                       int offset,
                                       int len)

    <!-- -->

    - #### closeShapefile

          public void closeShapefile()
                              throws java.io.IOException

      close this shapefile.
      Throws:
      `java.io.IOException`

    <!-- -->

    - #### getGeometryBytes

          public byte[] getGeometryBytes(int nth)
                                  throws java.io.IOException

      retrieve nth shape record and return it as a byte array.
      Throws:
      `java.io.IOException`

    <!-- -->

    - #### numRecords

          public int numRecords()

      return the number of shape records in the file.

    <!-- -->

    - #### getShpFileType

          public int getShpFileType()

      return the Shape Type in the file.

    <!-- -->

    - #### getMaxMeasure

          public double getMaxMeasure()

      return the maximum Measure value in file.

    <!-- -->

    - #### getMinMeasure

          public double getMinMeasure()

      return the minimum Measure value in file.

    <!-- -->

    - #### getMaxZ

          public double getMaxZ()

      return the maximum Z value in file.

    <!-- -->

    - #### getMinZ

          public double getMinZ()

      return the minimum Z value in file.

    <!-- -->

    - #### getMaxX

          public double getMaxX()

      return the maximum X value in file.

    <!-- -->

    - #### getMinX

          public double getMinX()

      return the minimum X value in file.

    <!-- -->

    - #### getMaxY

          public double getMaxY()

      return the maximum Y value in file.

    <!-- -->

    - #### getMinY

          public double getMinY()

      return the minimum Y value in file.

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

- [Prev Class](ShapefileFeatureJGeom.md)
- [Next Class](SqlLdrStreamWrapper.md)

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
