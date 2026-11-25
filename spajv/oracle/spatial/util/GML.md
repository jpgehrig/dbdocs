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

- [Prev Class](GeometryExceptionWithContext.md)
- [Next Class](GML2.md)

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

## Class GML

- java.lang.Object

- - oracle.spatial.util.GML

<!-- -->

-

  ------------------------------------------------------------------------



      public class GML
      extends java.lang.Object

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `GML``()`                   |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    |--------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToEnvelope``(org.w3c.dom.Node nd)`<br>Example:<br>\<pre\><br>    \<Box srsName="EPSG:4326"\><br>        \<coordinates\><br>                0.0,0.0 100.0,100.0<br>        \</coordinates\><br>    \</Box\><br>\</pre\><br>Note: Each Box Element encloses a single coordinates element or four Coord, the latter containing precisely two coordinate tuples.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToGeometry``(org.w3c.dom.Node nd)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToGeometry``(org.w3c.dom.Node nd, int coordOrder)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToGeometryCollection``(org.w3c.dom.Node nd)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToLinearRing``(org.w3c.dom.Node nd)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToLineString``(org.w3c.dom.Node nd)`<br>Example:<br>\<pre\><br>    \<LineString srsName="EPSG:4326"\><br>        \<coordinates\><br>            0.0,0.0 100.0,100.0<br>        \</coordinates\><br>    \</LineString\><br>\</pre\><br>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToMultiLineString``(org.w3c.dom.Node nd)`<br>Example:<br>\<pre\><br>    \<MultiLineString srsName="EPSG:4326"\><br>        \<lineStringMember\><br>            \<LineString\><br>                \<coordinates\>56.1,0.45 67.23,0.67\</coordinates\><br>            \</LineString\><br>        \</lineStringMember\><br>        \<lineStringMember\><br>            \<LineString\><br>                \<coordinates\>46.71,9.25 56.88,10.44\</coordinates\><br>            \</LineString\><br>        \</lineStringMember\><br>        \<lineStringMember\><br>            \<LineString\><br>                \<coordinates\>324.1,219.7 0.45,0.56\</coordinates\><br>            \</LineString\><br>        \</lineStringMember\><br>    \</MultiLineString\><br>\</pre\><br>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToMultiPoint``(org.w3c.dom.Node nd)`<br>Example:<br>\<pre\><br>    \<MultiPoint srsName="EPSG:4326"\><br>        \<pointMember\><br>            \<Point\><br>                \<coordinates\>56.1,0.45\</coordinates\><br>            \</Point\><br>        \</pointMember\><br>        \<pointMember\><br>            \<Point\><br>                \<coordinates\>46.71,9.25\</coordinates\><br>            \</Point\><br>        \</pointMember\><br>        \<pointMember\><br>            \<Point\><br>                \<coordinates\>56.88,10.44\</coordinates\><br>            \</Point\><br>        \</pointMember\><br>    \</MultiPoint \><br>\</pre\><br>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToMultiPolygon``(org.w3c.dom.Node nd)`<br>Example:<br>\<pre\><br>\<MultiPolygon srsName="EPSG:4326"\><br>  \<PolygonMember\><br>    \<Polygon srsName="EPSG:4326"\><br>      \<outerBoundaryIs\><br>        \<LinearRing\><br>          \<coordinates\><br>            0.0,0.0 100.0,0.0 100.0,100.0 0.0,100.0 0.0,0.0<br>          \</coordinates\><br>        \</LinearRing\><br>      \</outerBoundaryIs\><br>      \<innerBoundaryIs\><br>        \<LinearRing\><br>          \<coordinates\><br>            10.0,10.0 10.0,40.0 40.0,40.0 40.0,10.0 10.0,10.0<br>          \</coordinates\><br>        \</LinearRing\><br>      \</innerBoundaryIs\><br>      \<innerBoundaryIs\><br>        \<LinearRing\><br>          \<coordinates\><br>            60.0,60.0 60.0,90.0 90.0,90.0 90.0,60.0 60.0,60.0<br>          \</coordinates\><br>        \</LinearRing\><br>      \</innerBoundaryIs\><br>    \</Polygon\><br>  \</PolygonMember\><br>  \<PolygonMember\><br>    \<Polygon srsName="EPSG:4326"\><br>      \<outerBoundaryIs\><br>        \<LinearRing\><br>          \<coordinates\><br>            1000.0,0.0 1100.0,0.0 1100.0,100.0 1000.0,100.0 1000.0,0.0<br>          \</coordinates\><br>        \</LinearRing\><br>      \</outerBoundaryIs\><br>      \<innerBoundaryIs\><br>        \<LinearRing\><br>          \<coordinates\><br>            1010.0,10.0 1010.0,40.0 1040.0,40.0 1040.0,10.0 1010.0,10.0<br>          \</coordinates\><br>        \</LinearRing\><br>      \</innerBoundaryIs\><br>      \<innerBoundaryIs\><br>        \<LinearRing\><br>          \<coordinates\><br>            1060.0,60.0 1060.0,90.0 1090.0,90.0 1090.0,60.0 1060.0,60.0<br>          \</coordinates\><br>        \</LinearRing\><br>      \</innerBoundaryIs\><br>    \</Polygon\><br>  \</PolygonMember\><br>  \<PolygonMember\><br>    \<Polygon srsName="EPSG:4326"\><br>      \<outerBoundaryIs\><br>        \<LinearRing\><br>          \<coordinates\><br>            2000.0,0.0 2100.0,0.0 2100.0,100.0 2000.0,100.0 2000.0,0.0<br>          \</coordinates\><br>        \</LinearRing\><br>      \</outerBoundaryIs\><br>      \<innerBoundaryIs\><br>        \<LinearRing\><br>          \<coordinates\><br>            2010.0,10.0 2010.0,40.0 2040.0,40.0 2040.0,10.0 2010.0,10.0<br>          \</coordinates\><br>        \</LinearRing\><br>      \</innerBoundaryIs\><br>      \<innerBoundaryIs\><br>        \<LinearRing\><br>          \<coordinates\><br>            2060.0,60.0 2060.0,90.0 2090.0,90.0 2090.0,60.0 2060.0,60.0<br>          \</coordinates\><br>        \</LinearRing\><br>      \</innerBoundaryIs\><br>    \</Polygon\><br>  \</PolygonMember\><br>\</MultiPolygon\><br>\</pre\><br> |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToPoint``(org.w3c.dom.Node nd)`<br>Example 1:<br>\<pre\><br>    \<Point srsName="EPSG:4326"\><br>        \<coordinates\><br>            56.1,0.45<br>        \</coordinates\><br>    \</Point\><br>\</pre\><br>Example 2:<br>\<pre\><br>    \<Point srsName="8265"\><br>        \<coord\><br>            \<x\>56.1\</x\><br>            \<y\>0.45\</y\><br>        \</coord\><br>    \</Point\><br>\</pre\><br>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToPolygon``(org.w3c.dom.Node nd)`<br>Example:<br>\<pre\><br>    \<Polygon srsName="EPSG:4326"\><br>        \<outerBoundaryIs\><br>            \<LinearRing\><br>                \<coordinates\><br>                    0.0,0.0 100.0,0.0 100.0,100.0 0.0,100.0 0.0,0.0<br>                \</coordinates\><br>            \</LinearRing\><br>        \</outerBoundaryIs\><br>        \<innerBoundaryIs\><br>            \<LinearRing\><br>                \<coordinates\><br>                    10.0,10.0 10.0,40.0 40.0,40.0 40.0,10.0 10.0,10.0<br>                \</coordinates\><br>            \</LinearRing\><br>        \</innerBoundaryIs\><br>        \<innerBoundaryIs\><br>            \<LinearRing\><br>                \<coordinates\><br>                    60.0,60.0 60.0,90.0 90.0,90.0 90.0,60.0 60.0,60.0<br>                \</coordinates\><br>            \</LinearRing\><br>        \</innerBoundaryIs\><br>    \</Polygon\><br>\</pre\><br>                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `static `[`JGeometry`](../geometry/JGeometry.md) | `fromNodeToSurface``(org.w3c.dom.Node nd)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `static java.util.Vector`                        | `getAll``(org.w3c.dom.Node start, java.lang.String[] path)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static void`                                    | `getAll``(org.w3c.dom.Node start, java.lang.String[] path, int posInPath, java.util.Vector result)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `static java.lang.String`                        | `getNameSpace``()`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `static void`                                    | `setConnection``(java.sql.Connection conn)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `static void`                                    | `setsrsNameSpace``(java.lang.String srsNameSpace)`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### GML

          public GML()

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

      Example 1:
      \<pre\>
          \<Point srsName="EPSG:4326"\>
              \<coordinates\>
                  56.1,0.45
              \</coordinates\>
          \</Point\>
      \</pre\>
      Example 2:
      \<pre\>
          \<Point srsName="8265"\>
              \<coord\>
                  \<x\>56.1\</x\>
                  \<y\>0.45\</y\>
              \</coord\>
          \</Point\>
      \</pre\>
      Throws:
      [`DataException`](../geometry/DataException.md)

      `java.lang.Exception`

    <!-- -->

    - #### fromNodeToEnvelope

          public static final JGeometry fromNodeToEnvelope(org.w3c.dom.Node nd)
                                                    throws DataException,
                                                           java.lang.Exception

      Example:
      \<pre\>
          \<Box srsName="EPSG:4326"\>
              \<coordinates\>
                      0.0,0.0 100.0,100.0
              \</coordinates\>
          \</Box\>
      \</pre\>
      Note: Each Box Element encloses a single coordinates element or four Coord, the latter containing precisely two coordinate tuples. The first of these is constructued from the minimum values measured along for all the axes, and the second is constructed from the maximum values measured along all the axes.
      Throws:
      [`DataException`](../geometry/DataException.md)

      `java.lang.Exception`

    <!-- -->

    - #### fromNodeToLineString

          public static JGeometry fromNodeToLineString(org.w3c.dom.Node nd)
                                                throws DataException,
                                                       java.lang.Exception

      Example:
      \<pre\>
          \<LineString srsName="EPSG:4326"\>
              \<coordinates\>
                  0.0,0.0 100.0,100.0
              \</coordinates\>
          \</LineString\>
      \</pre\>
      Throws:
      [`DataException`](../geometry/DataException.md)

      `java.lang.Exception`

    <!-- -->

    - #### fromNodeToPolygon

          public static JGeometry fromNodeToPolygon(org.w3c.dom.Node nd)
                                             throws DataException,
                                                    java.lang.Exception

      Example:
      \<pre\>
          \<Polygon srsName="EPSG:4326"\>
              \<outerBoundaryIs\>
                  \<LinearRing\>
                      \<coordinates\>
                          0.0,0.0 100.0,0.0 100.0,100.0 0.0,100.0 0.0,0.0
                      \</coordinates\>
                  \</LinearRing\>
              \</outerBoundaryIs\>
              \<innerBoundaryIs\>
                  \<LinearRing\>
                      \<coordinates\>
                          10.0,10.0 10.0,40.0 40.0,40.0 40.0,10.0 10.0,10.0
                      \</coordinates\>
                  \</LinearRing\>
              \</innerBoundaryIs\>
              \<innerBoundaryIs\>
                  \<LinearRing\>
                      \<coordinates\>
                          60.0,60.0 60.0,90.0 90.0,90.0 90.0,60.0 60.0,60.0
                      \</coordinates\>
                  \</LinearRing\>
              \</innerBoundaryIs\>
          \</Polygon\>
      \</pre\>
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

    - #### fromNodeToMultiLineString

          public static JGeometry fromNodeToMultiLineString(org.w3c.dom.Node nd)
                                                     throws DataException,
                                                            java.lang.Exception

      Example:
      \<pre\>
          \<MultiLineString srsName="EPSG:4326"\>
              \<lineStringMember\>
                  \<LineString\>
                      \<coordinates\>56.1,0.45 67.23,0.67\</coordinates\>
                  \</LineString\>
              \</lineStringMember\>
              \<lineStringMember\>
                  \<LineString\>
                      \<coordinates\>46.71,9.25 56.88,10.44\</coordinates\>
                  \</LineString\>
              \</lineStringMember\>
              \<lineStringMember\>
                  \<LineString\>
                      \<coordinates\>324.1,219.7 0.45,0.56\</coordinates\>
                  \</LineString\>
              \</lineStringMember\>
          \</MultiLineString\>
      \</pre\>
      Throws:
      [`DataException`](../geometry/DataException.md)

      `java.lang.Exception`

    <!-- -->

    - #### fromNodeToMultiPoint

          public static JGeometry fromNodeToMultiPoint(org.w3c.dom.Node nd)
                                                throws DataException,
                                                       java.lang.Exception

      Example:
      \<pre\>
          \<MultiPoint srsName="EPSG:4326"\>
              \<pointMember\>
                  \<Point\>
                      \<coordinates\>56.1,0.45\</coordinates\>
                  \</Point\>
              \</pointMember\>
              \<pointMember\>
                  \<Point\>
                      \<coordinates\>46.71,9.25\</coordinates\>
                  \</Point\>
              \</pointMember\>
              \<pointMember\>
                  \<Point\>
                      \<coordinates\>56.88,10.44\</coordinates\>
                  \</Point\>
              \</pointMember\>
          \</MultiPoint \>
      \</pre\>
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

    - #### fromNodeToMultiPolygon

          public static JGeometry fromNodeToMultiPolygon(org.w3c.dom.Node nd)
                                                  throws DataException,
                                                         java.lang.Exception

      Example:
      \<pre\>
      \<MultiPolygon srsName="EPSG:4326"\>
        \<PolygonMember\>
          \<Polygon srsName="EPSG:4326"\>
            \<outerBoundaryIs\>
              \<LinearRing\>
                \<coordinates\>
                  0.0,0.0 100.0,0.0 100.0,100.0 0.0,100.0 0.0,0.0
                \</coordinates\>
              \</LinearRing\>
            \</outerBoundaryIs\>
            \<innerBoundaryIs\>
              \<LinearRing\>
                \<coordinates\>
                  10.0,10.0 10.0,40.0 40.0,40.0 40.0,10.0 10.0,10.0
                \</coordinates\>
              \</LinearRing\>
            \</innerBoundaryIs\>
            \<innerBoundaryIs\>
              \<LinearRing\>
                \<coordinates\>
                  60.0,60.0 60.0,90.0 90.0,90.0 90.0,60.0 60.0,60.0
                \</coordinates\>
              \</LinearRing\>
            \</innerBoundaryIs\>
          \</Polygon\>
        \</PolygonMember\>
        \<PolygonMember\>
          \<Polygon srsName="EPSG:4326"\>
            \<outerBoundaryIs\>
              \<LinearRing\>
                \<coordinates\>
                  1000.0,0.0 1100.0,0.0 1100.0,100.0 1000.0,100.0 1000.0,0.0
                \</coordinates\>
              \</LinearRing\>
            \</outerBoundaryIs\>
            \<innerBoundaryIs\>
              \<LinearRing\>
                \<coordinates\>
                  1010.0,10.0 1010.0,40.0 1040.0,40.0 1040.0,10.0 1010.0,10.0
                \</coordinates\>
              \</LinearRing\>
            \</innerBoundaryIs\>
            \<innerBoundaryIs\>
              \<LinearRing\>
                \<coordinates\>
                  1060.0,60.0 1060.0,90.0 1090.0,90.0 1090.0,60.0 1060.0,60.0
                \</coordinates\>
              \</LinearRing\>
            \</innerBoundaryIs\>
          \</Polygon\>
        \</PolygonMember\>
        \<PolygonMember\>
          \<Polygon srsName="EPSG:4326"\>
            \<outerBoundaryIs\>
              \<LinearRing\>
                \<coordinates\>
                  2000.0,0.0 2100.0,0.0 2100.0,100.0 2000.0,100.0 2000.0,0.0
                \</coordinates\>
              \</LinearRing\>
            \</outerBoundaryIs\>
            \<innerBoundaryIs\>
              \<LinearRing\>
                \<coordinates\>
                  2010.0,10.0 2010.0,40.0 2040.0,40.0 2040.0,10.0 2010.0,10.0
                \</coordinates\>
              \</LinearRing\>
            \</innerBoundaryIs\>
            \<innerBoundaryIs\>
              \<LinearRing\>
                \<coordinates\>
                  2060.0,60.0 2060.0,90.0 2090.0,90.0 2090.0,60.0 2060.0,60.0
                \</coordinates\>
              \</LinearRing\>
            \</innerBoundaryIs\>
          \</Polygon\>
        \</PolygonMember\>
      \</MultiPolygon\>
      \</pre\>
      Parameters:
      `nd` - A Node representing the input GML

      Returns:
      The resulting JGeometry

      Throws:
      [`DataException`](../geometry/DataException.md)

      `java.lang.Exception`

    <!-- -->

    - #### getAll

          public static java.util.Vector getAll(org.w3c.dom.Node start,
                                                java.lang.String[] path)

    <!-- -->

    - #### getAll

          public static void getAll(org.w3c.dom.Node start,
                                    java.lang.String[] path,
                                    int posInPath,
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

- [Prev Class](GeometryExceptionWithContext.md)
- [Next Class](GML2.md)

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
