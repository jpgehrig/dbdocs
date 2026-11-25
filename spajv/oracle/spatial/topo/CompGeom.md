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

- Prev Class
- [Next Class](Edge.md)

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

oracle.spatial.topo

## Class CompGeom

- java.lang.Object

- - oracle.spatial.topo.CompGeom

<!-- -->

-

  ------------------------------------------------------------------------



      public class CompGeom
      extends java.lang.Object

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `CompGeom``()`              |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                                                   |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static int`      | `arcArcIntersect``(double arc1x1, double arc1y1, double arc1x2, double arc1y2, double c1x, double c1y, double r1, double arc2x1, double arc2y1, double arc2x2, double arc2y2, double c2x, double c2y, double r2, double[] result1, double[] result2)`<br>Finds the open-set intersection(s) of two arc segments, if any. |
    | `static boolean`  | `areSegmentsParallel``(double a1x, double a1y, double a2x, double a2y, double b1x, double b1y, double b2x, double b2y, boolean sameSenseOnly)`                                                                                                                                                                           |
    | `static boolean`  | `areSegmentsParallel``(`[`Point2DD`](Point2DD.md)` a1, `[`Point2DD`](Point2DD.md)` a2, `[`Point2DD`](Point2DD.md)` b1, `[`Point2DD`](Point2DD.md)` b2, boolean sameSenseOnly)`<br>Finds whether two line segments are parallel or, optionally, anti-parallel.                                                            |
    | `static void`     | `augmentMBR``(`[`Point2DD`](Point2DD.md)`[] mbrAdd, `[`Point2DD`](Point2DD.md)`[] mbrTarget)`<br>Expands target MBR to encompass added one.                                                                                                                                                                              |
    | `static void`     | `augmentMBR``(`[`Point2DD`](Point2DD.md)` p, `[`Point2DD`](Point2DD.md)`[] mbrTarget)`<br>Expands target MBR to encompass an added point.                                                                                                                                                                                |
    | `static void`     | `crossProduct``(double[] r1, double[] r2, double[] result)`<br>3-D crossproduct via arrays.                                                                                                                                                                                                                              |
    | `static double`   | `crossProduct``(double x1, double y1, double x2, double y2)`                                                                                                                                                                                                                                                             |
    | `static double`   | `crossProduct``(`[`Point2DD`](Point2DD.md)` p1, `[`Point2DD`](Point2DD.md)` p2)`                                                                                                                                                                                                                                         |
    | `static double`   | `dotProduct``(double x1, double y1, double x2, double y2)`                                                                                                                                                                                                                                                               |
    | `static double`   | `dotProduct``(`[`Point2DD`](Point2DD.md)` p1, `[`Point2DD`](Point2DD.md)` p2)`                                                                                                                                                                                                                                           |
    | `static boolean`  | `incPointInPolygon``(`[`Point2DD`](Point2DD.md)` p, `[`Point2DD`](Point2DD.md)`[] q, boolean state)`<br>Incremental Point in Polygon routine taking a string of coordinates representing a part (or all) of a ring boundary.                                                                                             |
    | `static boolean`  | `inLineRange``(double px, double py, double x1, double y1, double x2, double y2)`<br>computes whether the test point is on the open set of the input line segment with the assumption that the point is already known to be on the infinite line of which the line segment is a part.                                    |
    | `static boolean`  | `inSector``(double px, double py, double sp1x, double sp1y, double sp2x, double sp2y, double sp3x, double sp3y)`<br>inSector determines whether a line drawn from the middle vertex of a triad of vertices to a test point lies within the sector defined by the triad.                                                  |
    | `static boolean`  | `inSector``(`[`Point2DD`](Point2DD.md)` p, `[`Point2DD`](Point2DD.md)`[] sectorPoints)`<br>inSector determines whether a line drawn from the middle vertex of a triad of vertices to a test point lies within the sector defined by the triad.                                                                           |
    | `static int`      | `lineArcIntersect``(double x1, double y1, double x2, double y2, double arc_x1, double arc_y1, double arc_x2, double arc_y2, double xc, double yc, double r, double[] result1, double[] result2)`<br>Finds the open-set intersection of line and arc segments, if any.                                                    |
    | `static boolean`  | `lineLineIntersect``(double a1x, double a1y, double a2x, double a2y, double b1x, double b1y, double b2x, double b2y, double[] c)`<br>Finds the open-set intersection of two line segments, if any.                                                                                                                       |
    | `static boolean`  | `lineLineIntersect``(`[`Point2DD`](Point2DD.md)` a1, `[`Point2DD`](Point2DD.md)` a2, `[`Point2DD`](Point2DD.md)` b1, `[`Point2DD`](Point2DD.md)` b2, `[`Point2DD`](Point2DD.md)` c)`<br>Finds the open-set intersection of two line segments, if any.                                                                    |
    | `static void`     | `main``(java.lang.String[] args)`                                                                                                                                                                                                                                                                                        |
    | `static boolean`  | `pointInMBR``(double px, double py, double[][] mbr)`<br>Determines if a point is within the bounds of the specified rectangle.                                                                                                                                                                                           |
    | `static boolean`  | `pointInMBR``(`[`Point2DD`](Point2DD.md)` p, `[`Point2DD`](Point2DD.md)`[] mbr)`<br>Determines if a point is within the bounds of the specified rectangle.                                                                                                                                                               |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### CompGeom

          public CompGeom()

  <!-- -->

  - ### Method Detail

    - #### dotProduct

          public static double dotProduct(Point2DD p1,
                                          Point2DD p2)

    <!-- -->

    - #### crossProduct

          public static double crossProduct(Point2DD p1,
                                            Point2DD p2)

    <!-- -->

    - #### dotProduct

          public static double dotProduct(double x1,
                                          double y1,
                                          double x2,
                                          double y2)

    <!-- -->

    - #### crossProduct

          public static double crossProduct(double x1,
                                            double y1,
                                            double x2,
                                            double y2)

    <!-- -->

    - #### crossProduct

          public static void crossProduct(double[] r1,
                                          double[] r2,
                                          double[] result)

      3-D crossproduct via arrays. Can preallocate result vector or not

    <!-- -->

    - #### inSector

          public static boolean inSector(Point2DD p,
                                         Point2DD[] sectorPoints)

      inSector determines whether a line drawn from the middle vertex of a triad of vertices to a test point lies within the sector defined by the triad. In order the triad defines the sector in a clockwise direction. Results may be indeterminate for test points very near either segment defining the sector. If this is important, areSegmentsParallel() should be used since it has better control for lost precision.
      Parameters:
      `p` - The test point

      `sectorPoints` - The triad to be tested. Vertex \[0\] and \[2\] are the endpoints. Vertex \[1\] is the central vertex.

      Returns:
      The boolean result; true if point is in the sector of the triad

    <!-- -->

    - #### inLineRange

          public static boolean inLineRange(double px,
                                            double py,
                                            double x1,
                                            double y1,
                                            double x2,
                                            double y2)

      computes whether the test point is on the open set of the input line segment with the assumption that the point is already known to be on the infinite line of which the line segment is a part.
      If the point is equal to one of the endpoints this routine will return false;

      Parameters:
      `px` - The test point x value

      `py` - The test point y value

      `x1` - x value of line segment point 1

      `y1` - y value of line segment point 1

      `x2` - x value of line segment point 2

      `y2` - y value of line segment point 2

      Returns:
      The boolean result; true if point is in segment open set

    <!-- -->

    - #### inSector

          public static boolean inSector(double px,
                                         double py,
                                         double sp1x,
                                         double sp1y,
                                         double sp2x,
                                         double sp2y,
                                         double sp3x,
                                         double sp3y)

      inSector determines whether a line drawn from the middle vertex of a triad of vertices to a test point lies within the sector defined by the triad. In order the triad defines the sector in a clockwise direction. Results may be indeterminate for test points very near either segment defining the sector. If this is important, areSegmentsParallel() should be used since it has better control for lost precision.
      Parameters:
      `px` - The test point x value

      `py` - The test point y value

      `sp1x` - x value of triad point 1

      `sp1y` - y value of triad point 1

      `sp2x` - x value of triad point 2, the central vertex

      `sp2y` - y value of triad point 2

      `sp3x` - x value of triad point 3

      `sp3y` - y value of triad point 3

      Returns:
      The boolean result; true if point is in the sector of the triad

    <!-- -->

    - #### augmentMBR

          public static void augmentMBR(Point2DD[] mbrAdd,
                                        Point2DD[] mbrTarget)

      Expands target MBR to encompass added one. If target MBR has null contents the added one is just copied into it.
      Parameters:
      `mbrAdd` - the one to be added

      `mbrTarget` - the one that is augmented if necessary

    <!-- -->

    - #### augmentMBR

          public static void augmentMBR(Point2DD p,
                                        Point2DD[] mbrTarget)

      Expands target MBR to encompass an added point. If target MBR has null contents the added one is just copied into it.
      Parameters:
      `p` - the point to be added

      `mbrTarget` - the one that is augmented if necessary

    <!-- -->

    - #### pointInMBR

          public static boolean pointInMBR(Point2DD p,
                                           Point2DD[] mbr)
                                    throws java.lang.Exception

      Determines if a point is within the bounds of the specified rectangle. Will return true for points on the boundary. Traps null mbr array but will allow and return false for null members of mbr array.
      Parameters:
      `p` - the point to be tested.

      `mbr` - an array of Point2DD. \[0\] is the rectangle lower left corner. \[1\] is the rectangle upper right corner.

      Returns:
      true inside; false out; true on the boundary

      Throws:
      `java.lang.Exception`

    <!-- -->

    - #### pointInMBR

          public static boolean pointInMBR(double px,
                                           double py,
                                           double[][] mbr)

      Determines if a point is within the bounds of the specified rectangle. Will return true for points on the boundary. Traps null mbr array but will allow and return false for null members of mbr array.
      Parameters:
      `px` - x component of the point to be tested.

      `py` - y component of the point to be tested.

      `mbr` - a 2x2 array of doubles. First index is x,y. Second is min,max

      Returns:
      true inside; false out; true on the boundary

    <!-- -->

    - #### incPointInPolygon

          public static boolean incPointInPolygon(Point2DD p,
                                                  Point2DD[] q,
                                                  boolean state)

      Incremental Point in Polygon routine taking a string of coordinates representing a part (or all) of a ring boundary. Provides an incremental solution to the point in polygon problem. Input is an array of points representing vertices. The input state can be changed by each piece of data . Ordinarily use this with the return passed back on the input on the next piece of the polygon. If using this to incrementally solve the point in polygon problem, init state to FALSE, pass any consecutive group of coordinates with full closure on each other and on the start point, to include the possibility passing the whole polygon with the first coordinate repeated in the array. It makes no difference what orientation the strings of vertices have or in what sequence they are provided as long as they overlap each other's endpoints. As usual, this routine will return indeterminate results on the boundary. This must be tested for first, if important.
      Parameters:
      `p` - The test point

      `q` - The portion or all of the polygon perimeter

      `state` - the current in/out status of the determination. Set false intitially

      Returns:
      the new in/out status as a result of processing this piece of the boundary

    <!-- -->

    - #### lineArcIntersect

          public static int lineArcIntersect(double x1,
                                             double y1,
                                             double x2,
                                             double y2,
                                             double arc_x1,
                                             double arc_y1,
                                             double arc_x2,
                                             double arc_y2,
                                             double xc,
                                             double yc,
                                             double r,
                                             double[] result1,
                                             double[] result2)

      Finds the open-set intersection of line and arc segments, if any. An intersection is returned only if the segments cross within the open sets defined by their endpoints; that is, touching intersections involving the endpoints are returned false. Arc must be specified in a counter-clockwise sense. If there is(are) any intersection(s), results are returned in two x,y arrays of doubles. Only if needed these will be allocated by this method. One or both may be preallocated by the caller. If there are two intersections within the range of both segments, they are placed in order along the direction of the line segment, i.e. result1 to result2 is the same sense as (x1,y1) to (x2,y2).
      return values 0 -- no intersections

      -1 -- one touching (tangent) intersection

      1 -- one crossing intersection

      2 -- two crossing intersections; in-order on both segments

      -2 -- two crossing intersections; opposite order (placed in-order on the line)

      Resulting intersections are placed in the result1 and result2 arrays.

      Parameters:
      `x1` - x value of first endpoint of line segment

      `y1` - y value of first endpoint of line segment

      `x2` - x value of second endpoint of line segment

      `y2` - y value of second endpoint of line segment

      `arc_x1` - x of first endpoint of arc in counter-clockwise sense

      `arc_y1` - y of first endpoint of arc in counter-clockwise sense

      `arc_x2` - x of second endpoint of arc in counter-clockwise sense

      `arc_y2` - y of second endpoint of arc in counter-clockwise sense

      `xc` - x value of center of arc segment

      `yc` - y value of center of arc segment

      `r` - radius of arc

      `result1` - a 2-D array of intersection x,y pair if there are one or more open set intersections. Will be allocated here if not allocated by caller.

      `result2` - a 2-D array of intersection x,y pair if there are two open set intersections. Will be allocated here if not allocated by caller.

      Returns:
      an intersection classification

    <!-- -->

    - #### arcArcIntersect

          public static int arcArcIntersect(double arc1x1,
                                            double arc1y1,
                                            double arc1x2,
                                            double arc1y2,
                                            double c1x,
                                            double c1y,
                                            double r1,
                                            double arc2x1,
                                            double arc2y1,
                                            double arc2x2,
                                            double arc2y2,
                                            double c2x,
                                            double c2y,
                                            double r2,
                                            double[] result1,
                                            double[] result2)

      Finds the open-set intersection(s) of two arc segments, if any. An intersection is returned only if the segments cross within the open sets defined by their endpoints; that is, touching intersections involving the endpoints are returned false. Arcs must be specified in a counter-clockwise sense. If there is(are) any intersection(s), results are returned in two x,y arrays of doubles. Only if needed these will be allocated by this method. One or both may be preallocated by the caller. If there are two intersections within the range of both arcs, they are placed in order along the direction of the line segment, i.e. result1 to result2 is the same sense as the first arc.
      return values 0 -- no intersections

      -1 -- one touching (tangent) intersection

      1 -- one crossing intersection

      2 -- two crossing intersections; in-order on both segments

      -2 -- two crossing intersections; opposite order (placed in-order on the first arc)

      Resulting intersections are placed in the result1 and result2 arrays.

      Parameters:
      `x1` - x value of first endpoint of line segment

      `y1` - y value of first endpoint of line segment

      `x2` - x value of second endpoint of line segment

      `y2` - y value of second endpoint of line segment

      `arc_x1` - x of first endpoint of arc in counter-clockwise sense

      `arc_y1` - y of first endpoint of arc in counter-clockwise sense

      `arc_x2` - x of second endpoint of arc in counter-clockwise sense

      `arc_y2` - y of second endpoint of arc in counter-clockwise sense

      `xc` - x value of center of arc segment

      `yc` - y value of center of arc segment

      `r` - radius of arc

      `result1` - a 2-D array of intersection x,y pair if there are one or more open set intersections. Will be allocated here if not allocated by caller.

      `result2` - a 2-D array of intersection x,y pair if there are two open set intersections. Will be allocated here if not allocated by caller.

      Returns:
      an intersection classification

    <!-- -->

    - #### lineLineIntersect

          public static boolean lineLineIntersect(Point2DD a1,
                                                  Point2DD a2,
                                                  Point2DD b1,
                                                  Point2DD b2,
                                                  Point2DD c)

      Finds the open-set intersection of two line segments, if any. An intersection is returned only if the lines cross within the open sets defined by their endpoints; that is, touching intersections involving the endpoints are returned false. Use should be made of the method onLine() and the equals() method of the Point2DD class for coincidence of endpoints if knowledge of these conditions is desired.
      Parameters:
      `a1` - the first endpoint of line segment a

      `a2` - the second endpoint of line segment a

      `b1` - the first endpoint of line segment b

      `b2` - the second endpoint of line segment b

      `c` - the intersection (if any). May pass null; if non-null, may be overwritten even if result is false.

      Returns:
      true if there is an intersection; false otherwise

    <!-- -->

    - #### lineLineIntersect

          public static boolean lineLineIntersect(double a1x,
                                                  double a1y,
                                                  double a2x,
                                                  double a2y,
                                                  double b1x,
                                                  double b1y,
                                                  double b2x,
                                                  double b2y,
                                                  double[] c)

      Finds the open-set intersection of two line segments, if any. An intersection is returned only if the lines cross within the open sets defined by their endpoints; that is, touching intersections involving the endpoints are returned false. Testing for such equality should be done outside this routine if it is important.
      Parameters:
      `a1x` - the first endpoint x-value of line segment a

      `a1y` - the first endpoint y-value of line segment a

      `a2x` - the first endpoint x-value of line segment a

      `a2y` - the first endpoint y-value of line segment a

      `b1x` - the first endpoint x-value of line segment b

      `b1y` - the first endpoint y-value of line segment b

      `b2x` - the first endpoint x-value of line segment b

      `b2y` - the first endpoint y-value of line segment a

      `c` - the intersection (if any). May pass null; if non-null, may be overwritten even if result is false.

      Returns:
      true if there is an intersection; false otherwise

    <!-- -->

    - #### areSegmentsParallel

          public static boolean areSegmentsParallel(Point2DD a1,
                                                    Point2DD a2,
                                                    Point2DD b1,
                                                    Point2DD b2,
                                                    boolean sameSenseOnly)

      Finds whether two line segments are parallel or, optionally, anti-parallel. Since there is precision loss inevitable in the computation, account is taken of the loss in making the determination.
      Parameters:
      `a1` - the first point of the a segment

      `a2` - the second point of the a segment

      `b1` - the first point of the b segment

      `b2` - the second point of the b segemnt

      `sameSenseOnly` - whether parallel only or both parallel/anti-parallel pass

      Returns:
      true if the line segments are parallel if sameSenseOnly is true or if the segments are parallel or anti-parallel if sameSenseOnly is false; false otherwise

    <!-- -->

    - #### areSegmentsParallel

          public static boolean areSegmentsParallel(double a1x,
                                                    double a1y,
                                                    double a2x,
                                                    double a2y,
                                                    double b1x,
                                                    double b1y,
                                                    double b2x,
                                                    double b2y,
                                                    boolean sameSenseOnly)

    <!-- -->

    - #### main

          public static void main(java.lang.String[] args)
                           throws java.io.IOException

      Throws:
      `java.io.IOException`

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

- Prev Class
- [Next Class](Edge.md)

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
