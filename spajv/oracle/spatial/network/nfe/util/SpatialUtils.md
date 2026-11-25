Skip navigation links

- [Overview](../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](PathUtil.md)
- [Next Class](StringUtils.md)

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.util

## Class SpatialUtils

- java.lang.Object

- - oracle.spatial.network.nfe.util.SpatialUtils

<!-- -->

-

  ------------------------------------------------------------------------



      public class SpatialUtils
      extends java.lang.Object

  This class provides multiple static methods for performing different spatial-related tasks

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `SpatialUtils``()`          |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                      | Method and Description                                                                                                                                                                                                                                   |
    |--------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static JGeometrySegmentPoint`                         | `createSegmentPoint``(double pointX, double pointY, double[] lineOrdinates, int segmentIndex)`<br>Creates a JGeometrySegmentPoint for the given line ordinates.                                                                                          |
    | `static double`                                        | `distToLine``(java.awt.geom.Point2D point, `[`JGeometry`](../../../geometry/JGeometry.md)` line)`<br>Gets the distance from the given point to the nearest point at the given line                                                                       |
    | `static double`                                        | `getDataSRSTolerance``(java.awt.geom.AffineTransform affineTransform, double pxTolerance)`<br>Gets a tolerance in the data coordinate system given a tolerance in pixels                                                                                 |
    | `static double`                                        | `getDistance``(double x1, double y1, double x2, double y2)`<br>Gets the distance between two points                                                                                                                                                      |
    | `static double`                                        | `getDistance``(java.awt.geom.Point2D point1, java.awt.geom.Point2D point2)`<br>Gets the distance between two points                                                                                                                                      |
    | `static double`                                        | `getLineLength``(double[] lineOrdinates)`<br>Gets the length of a line.                                                                                                                                                                                  |
    | `static JGeometrySegment`                              | `getLineNearestSegment``(double[] ordinates, java.awt.geom.Point2D targetPoint, double tolerance)`<br>Gets the line's segment nearest to the given point as long as it is not farer than the given tolerance                                             |
    | `static JGeometrySegment`                              | `getLineNearestSegment``(`[`JGeometry`](../../../geometry/JGeometry.md)` line, java.awt.geom.Point2D targetPoint, double tolerance)`<br>Gets the line's segment nearest to the given point as long as it is not farer than the given tolerance           |
    | `static JGeometrySegmentPoint`                         | `getLineSegmentPoint``(double[] ordinates, java.awt.geom.Point2D targetPoint, double tolerance)`<br>Gets the nearest segment point in the line to the given point as long as it is not farer than the given tolerance.                                   |
    | `static JGeometrySegmentPoint`                         | `getLineSegmentPoint``(`[`JGeometry`](../../../geometry/JGeometry.md)` line, java.awt.geom.Point2D point)`<br>Gets the nearest segment point in the line to the given point.                                                                             |
    | `static JGeometrySegmentPoint`                         | `getLineSegmentPoint``(`[`JGeometry`](../../../geometry/JGeometry.md)` line, java.awt.geom.Point2D targetPoint, double tolerance)`<br>Gets the nearest segment point in the line to the given point as long as it is not farer than the given tolerance. |
    | `static java.awt.geom.Rectangle2D`                     | `getMBR``(`[`JGeometry`](../../../geometry/JGeometry.md)` geom, double threshold)`<br>Gets the MBR of the given geometry containing the given threshold                                                                                                  |
    | `static java.awt.geom.Point2D`                         | `getPointOnLine``(double[] lineOrdinates, double positionPercentage)`<br>Gets the spatial location of a point in the line given a percentage of the line's length                                                                                        |
    | `static double`                                        | `getPositionPercentage``(`[`JGeometry`](../../../geometry/JGeometry.md)` lineGeom, JGeometrySegmentPoint segmentPoint)`<br>Given a line and a line's segment point, gives the corresponding percentage of that point relative to the line's length.      |
    | `static double`                                        | `getPositionPercentage``(`[`JGeometry`](../../../geometry/JGeometry.md)` lineGeom, java.awt.geom.Point2D point, double tolerance)`<br>Given a line and a point, gives the corresponding percentage of that point relative to the line's length.          |
    | `static JGeometrySegmentPoint`                         | `getSegmentPoint``(double[] lineOrdinates, double positionPercentage)`<br>Gets the line segment point information corresponding to a position in the line given as a percentage of the line's length                                                     |
    | `static `[`JGeometry`](../../../geometry/JGeometry.md) | `getSubLine``(`[`JGeometry`](../../../geometry/JGeometry.md)` line, double startPos, double endPos)`<br>Gets the geometry of a portion of the given line                                                                                                 |
    | `static `[`JGeometry`](../../../geometry/JGeometry.md) | `getSubLine``(`[`JGeometry`](../../../geometry/JGeometry.md)` line, JGeometrySegmentPoint startSegPoint, JGeometrySegmentPoint endSegPoint)`<br>Gets the geometry of a portion of the given line                                                         |
    | `static `[`JGeometry`](../../../geometry/JGeometry.md) | `getSubLine``(`[`JGeometry`](../../../geometry/JGeometry.md)` line, java.awt.geom.Point2D startPoint, java.awt.geom.Point2D endPoint, double tolerance)`<br>Gets the geometry of a portion of the given line                                             |
    | `static double`                                        | `getSubLineLength``(`[`JGeometry`](../../../geometry/JGeometry.md)` lineGeom, JGeometrySegmentPoint segmentPoint)`<br>Gets the length from the line's start point to the given point in the line.                                                        |
    | `static double`                                        | `getSubLineLength``(`[`JGeometry`](../../../geometry/JGeometry.md)` lineGeom, java.awt.geom.Point2D point, double tolerance)`<br>Gets the length from the line's start point to the given point in the line.                                             |
    | `static boolean`                                       | `isSamePoint``(double[] point1, double[] point2)`<br>Tells whether the given points are located at the same position                                                                                                                                     |
    | `static `[`JGeometry`](../../../geometry/JGeometry.md) | `joinAdjacentLines``(`[`JGeometry`](../../../geometry/JGeometry.md)` srcLine, `[`JGeometry`](../../../geometry/JGeometry.md)` endLine)`<br>Joins two lines into one single line                                                                          |
    | `static `[`JGeometry`](../../../geometry/JGeometry.md) | `moveLinePoint``(`[`JGeometry`](../../../geometry/JGeometry.md)` line, int pointIndex, java.awt.geom.Point2D newPoint)`<br>Replaces line's point by another                                                                                              |
    | `static `[`JGeometry`](../../../geometry/JGeometry.md) | `translate``(`[`JGeometry`](../../../geometry/JGeometry.md)` geom, double transX, double transY)`<br>Translates a geometry                                                                                                                               |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### SpatialUtils

          public SpatialUtils()

  <!-- -->

  - ### Method Detail

    - #### getDataSRSTolerance

          public static double getDataSRSTolerance(java.awt.geom.AffineTransform affineTransform,
                                                   double pxTolerance)
                                            throws java.awt.geom.NoninvertibleTransformException

      Gets a tolerance in the data coordinate system given a tolerance in pixels
      Parameters:
      `affineTransform` - the affine transform used for converting between coordinate systems

      `pxTolerance` - a tolerance in pixels

      Returns:
      a tolerance in the data coordinate system

      Throws:
      `java.awt.geom.NoninvertibleTransformException`

    <!-- -->

    - #### getDistance

          public static double getDistance(java.awt.geom.Point2D point1,
                                           java.awt.geom.Point2D point2)

      Gets the distance between two points
      Parameters:
      `point1` - a point object

      `point2` - a point object

      Returns:
      the distance between two points

    <!-- -->

    - #### getDistance

          public static double getDistance(double x1,
                                           double y1,
                                           double x2,
                                           double y2)

      Gets the distance between two points
      Parameters:
      `x1` - the first point's x ordinate

      `y1` - the first point's y ordinate

      `x2` - the second point's x ordinate

      `y2` - the second point's y ordinate

      Returns:
      the distance between two points

    <!-- -->

    - #### distToLine

          public static double distToLine(java.awt.geom.Point2D point,
                                          JGeometry line)

      Gets the distance from the given point to the nearest point at the given line
      Parameters:
      `point` - a point object

      `line` - a line string geometry object

      Returns:
      the distance from the point to the nearest point at the line

    <!-- -->

    - #### isSamePoint

          public static boolean isSamePoint(double[] point1,
                                            double[] point2)

      Tells whether the given points are located at the same position
      Parameters:
      `point1` - a two-valued array containing the coordinates of a point

      `point2` - a two-valued array containing the coordinates of a point

      Returns:
      true if both points are equals

    <!-- -->

    - #### moveLinePoint

          public static JGeometry moveLinePoint(JGeometry line,
                                                int pointIndex,
                                                java.awt.geom.Point2D newPoint)

      Replaces line's point by another
      Parameters:
      `line` - a line string geometry object

      `pointIndex` - the index of the point to be replaced. Given the line's ordinate array, the index corresponds to the position por the x ordinate of the point that is going to be replaced.

      `newPoint` - a point object that will be the new line's point

      Returns:
      the line after replacing the point

    <!-- -->

    - #### getLineLength

          public static double getLineLength(double[] lineOrdinates)

      Gets the length of a line. The length is the sum of the length of each line segment.
      Parameters:
      `lineOrdinates` - the line ordinates

      Returns:
      the length of the line

    <!-- -->

    - #### getPointOnLine

          public static java.awt.geom.Point2D getPointOnLine(double[] lineOrdinates,
                                                             double positionPercentage)

      Gets the spatial location of a point in the line given a percentage of the line's length
      Parameters:
      `lineOrdinates` - the line ordinates

      `positionPercentage` - a percentage of the line's length

      Returns:
      a point object

    <!-- -->

    - #### getSegmentPoint

          public static JGeometrySegmentPoint getSegmentPoint(double[] lineOrdinates,
                                                              double positionPercentage)

      Gets the line segment point information corresponding to a position in the line given as a percentage of the line's length
      Parameters:
      `lineOrdinates` - the line ordinates

      `positionPercentage` - a percentage of the line's length

      Returns:
      the segment point information

    <!-- -->

    - #### createSegmentPoint

          public static JGeometrySegmentPoint createSegmentPoint(double pointX,
                                                                 double pointY,
                                                                 double[] lineOrdinates,
                                                                 int segmentIndex)

      Creates a JGeometrySegmentPoint for the given line ordinates. This method is meant to help on avoiding boilerplate code regarding to the creation of a JGeometrySegment point but does not perform any verification.
      Parameters:

      `pointX` - the x ordinate of the segment point

      `pointY` - the y ordinate of the segment point

      `lineOrdinates` - a line ordinates

      `segmentIndex` - the index of the line segment. The index is based on the number of segments in the line, not the ordinates, and it is zero based.

      Returns:

    <!-- -->

    - #### getLineSegmentPoint

          public static JGeometrySegmentPoint getLineSegmentPoint(JGeometry line,
                                                                  java.awt.geom.Point2D targetPoint,
                                                                  double tolerance)

      Gets the nearest segment point in the line to the given point as long as it is not farer than the given tolerance.
      Parameters:
      `line` - a line string

      `targetPoint` - a point object

      `tolerance` - the maximum distance between the given point and the line's point

      Returns:
      the segment point object for the line's point

    <!-- -->

    - #### getLineSegmentPoint

          public static JGeometrySegmentPoint getLineSegmentPoint(double[] ordinates,
                                                                  java.awt.geom.Point2D targetPoint,
                                                                  double tolerance)

      Gets the nearest segment point in the line to the given point as long as it is not farer than the given tolerance.
      Parameters:
      `ordinates` - a line string ordinates

      `targetPoint` - a point object

      `tolerance` - the maximum distance between the given point and the line's point

      Returns:
      the segment point object for the line's point

    <!-- -->

    - #### getLineSegmentPoint

          public static JGeometrySegmentPoint getLineSegmentPoint(JGeometry line,
                                                                  java.awt.geom.Point2D point)

      Gets the nearest segment point in the line to the given point.
      Parameters:
      `line` - a line string

      `point` - a point object

      Returns:
      the segment point object for the line's point

    <!-- -->

    - #### getLineNearestSegment

          public static JGeometrySegment getLineNearestSegment(JGeometry line,
                                                               java.awt.geom.Point2D targetPoint,
                                                               double tolerance)

      Gets the line's segment nearest to the given point as long as it is not farer than the given tolerance
      Parameters:
      `line` - a line string

      `targetPoint` - a point object

      `tolerance` - the value bounding the distance

      Returns:
      the line's segment information

    <!-- -->

    - #### getLineNearestSegment

          public static JGeometrySegment getLineNearestSegment(double[] ordinates,
                                                               java.awt.geom.Point2D targetPoint,
                                                               double tolerance)

      Gets the line's segment nearest to the given point as long as it is not farer than the given tolerance
      Parameters:
      `ordinates` - a line string ordinates

      `targetPoint` - a point object

      `tolerance` - the value bounding the distance

      Returns:
      the line's segment information

    <!-- -->

    - #### getSubLine

          public static JGeometry getSubLine(JGeometry line,
                                             java.awt.geom.Point2D startPoint,
                                             java.awt.geom.Point2D endPoint,
                                             double tolerance)

      Gets the geometry of a portion of the given line
      Parameters:
      `line` - a line string

      `startPoint` - a point of the original line that will be the start point of the sub line

      `endPoint` - a point of the original line that will be the end point of the sub line

      `tolerance` - tells how far can be the given start and end points to be considered as points in the line

      Returns:
      a line string geometry or null if the given start and end points are outside the tolerance

    <!-- -->

    - #### getSubLine

          public static JGeometry getSubLine(JGeometry line,
                                             double startPos,
                                             double endPos)

      Gets the geometry of a portion of the given line
      Parameters:
      `line` - a line string

      `startPoint` - a point of the original line that will be the start point of the sub line

      `endPoint` - a point of the original line that will be the end point of the sub line

      Returns:
      a line string geometry

    <!-- -->

    - #### getSubLine

          public static JGeometry getSubLine(JGeometry line,
                                             JGeometrySegmentPoint startSegPoint,
                                             JGeometrySegmentPoint endSegPoint)

      Gets the geometry of a portion of the given line
      Parameters:
      `line` - a line string

      `startSegPoint` - a segment point of the original line that will be the start point of the sub line

      `endSegPoint` - a segment point of the original line that will be the end point of the sub line

      Returns:
      a line string geometry

    <!-- -->

    - #### getPositionPercentage

          public static double getPositionPercentage(JGeometry lineGeom,
                                                     java.awt.geom.Point2D point,
                                                     double tolerance)

      Given a line and a point, gives the corresponding percentage of that point relative to the line's length.
      Parameters:
      `lineGeom` - a line string

      `point` - a point object

      `tolerance` - the maximum distance from the point to the line to be considered as a point on the line

      Returns:
      a percentage of the line length. A value between 0 and 1 inclusive.

    <!-- -->

    - #### getPositionPercentage

          public static double getPositionPercentage(JGeometry lineGeom,
                                                     JGeometrySegmentPoint segmentPoint)

      Given a line and a line's segment point, gives the corresponding percentage of that point relative to the line's length.
      Parameters:
      `lineGeom` - a line string

      `segmentPoint` - the line's segment point

      Returns:
      a percentage of the line length. A value between 0 and 1 inclusive.

    <!-- -->

    - #### getSubLineLength

          public static double getSubLineLength(JGeometry lineGeom,
                                                java.awt.geom.Point2D point,
                                                double tolerance)

      Gets the length from the line's start point to the given point in the line.
      Parameters:
      `lineGeom` - a line string

      `point` - a point object

      `tolerance` - the maximum distance from the point to the line

      Returns:
      the length of the sub line described or an invalid number if the given point does not lay on the line.

    <!-- -->

    - #### getSubLineLength

          public static double getSubLineLength(JGeometry lineGeom,
                                                JGeometrySegmentPoint segmentPoint)

      Gets the length from the line's start point to the given point in the line.
      Parameters:
      `lineGeom` - a line string

      `segmentPoint` - a line's segment point

      Returns:
      the length of the sub line described

    <!-- -->

    - #### translate

          public static JGeometry translate(JGeometry geom,
                                            double transX,
                                            double transY)

      Translates a geometry
      Parameters:
      `geom` - a geometry object

      `transX` - the distance the geometry will be moved in the x dimension

      `transY` - the distance the geometry will be moved in the y dimension

      Returns:
      the translated geometry

    <!-- -->

    - #### getMBR

          public static java.awt.geom.Rectangle2D getMBR(JGeometry geom,
                                                         double threshold)

      Gets the MBR of the given geometry containing the given threshold
      Parameters:
      `geom` - a geometry object

      `threshold` - an additional distance added to each side of the resulting MBR

      Returns:
      the geometry's MBR as a rectangle object

    <!-- -->

    - #### joinAdjacentLines

          public static JGeometry joinAdjacentLines(JGeometry srcLine,
                                                    JGeometry endLine)

      Joins two lines into one single line
      Parameters:
      `srcLine` - a line string which will be the initial line segments of the resulting lines

      `endLine` - a line string which will be the last line segments of the resulting lines

      Returns:
      a new line string geometry

Skip navigation links

- [Overview](../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](PathUtil.md)
- [Next Class](StringUtils.md)

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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
