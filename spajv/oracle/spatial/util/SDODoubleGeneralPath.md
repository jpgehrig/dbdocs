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

- [Prev Class](SchemaEntityResolver.md)
- [Next Class](SdoPointInPolygon.md)

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

## Class SDODoubleGeneralPath

- java.lang.Object

- - oracle.spatial.util.SDODoubleGeneralPath

<!-- -->

- All Implemented Interfaces:
  java.awt.Shape, java.lang.Cloneable

  ------------------------------------------------------------------------



      public final class SDODoubleGeneralPath
      extends java.lang.Object
      implements java.awt.Shape, java.lang.Cloneable

  The `GeneralPath` class represents a geometric path constructed from straight lines, and quadratic and cubic (Bézier) curves. It can contain multiple subpaths.
  The winding rule specifies how the interior of a path is determined. There are two types of winding rules: EVEN_ODD and NON_ZERO.

  An EVEN_ODD winding rule means that enclosed regions of the path alternate between interior and exterior areas as traversed from the outside of the path towards a point inside the region.

  A NON_ZERO winding rule means that if a ray is drawn in any direction from a given point to infinity and the places where the path intersects the ray are examined, the point is inside of the path if and only if the number of times that the path crosses the ray from left to right does not equal the number of times that the path crosses the ray from right to left.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                                               |
    |-------------------|-------------------------------------------------------------------------------------|
    | `static int`      | `WIND_EVEN_ODD`<br>An even-odd winding rule for determining the interior of a path. |
    | `static int`      | `WIND_NON_ZERO`<br>A non-zero winding rule for determining the interior of a path.  |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                    |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `SDODoubleGeneralPath``()`<br>Constructs a new `GeneralPath` object.                                                                                                                           |
    | `SDODoubleGeneralPath``(int rule)`<br>Constructs a new `GeneralPath` object with the specified winding rule to control operations that require the interior of the path to be defined.         |
    | `SDODoubleGeneralPath``(int rule, int initialCapacity)`<br>Constructs a new `GeneralPath` object with the specified winding rule and the specified initial capacity to store path coordinates. |
    | `SDODoubleGeneralPath``(java.awt.Shape s)`<br>Constructs a new `GeneralPath` object from an arbitrary `Shape` object.                                                                          |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type            | Method and Description                                                                                                                                                                                                                                                                                                           |
    |------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                       | `append``(java.awt.geom.PathIterator pi, boolean connect)`<br>Appends the geometry of the specified `PathIterator` object to the path, possibly connecting the new geometry to the existing path segments with a line segment.                                                                                                   |
    | `void`                       | `append``(java.awt.Shape s, boolean connect)`<br>Appends the geometry of the specified `Shape` object to the path, possibly connecting the new geometry to the existing path segments with a line segment.                                                                                                                       |
    | `java.lang.Object`           | `clone``()`<br>Creates a new object of the same class as this object.                                                                                                                                                                                                                                                            |
    | `void`                       | `closePath``()`<br>Closes the current subpath by drawing a straight line back to the coordinates of the last `moveTo`.                                                                                                                                                                                                           |
    | `boolean`                    | `contains``(double x, double y)`<br>Tests if the specified coordinates are inside the boundary of this `Shape`.                                                                                                                                                                                                                  |
    | `boolean`                    | `contains``(double x, double y, double w, double h)`<br>Tests if the specified rectangular area is inside the boundary of this `Shape`.                                                                                                                                                                                          |
    | `boolean`                    | `contains``(java.awt.geom.Point2D p)`<br>Tests if the specified `Point2D` is inside the boundary of this `Shape`.                                                                                                                                                                                                                |
    | `boolean`                    | `contains``(java.awt.geom.Rectangle2D r)`<br>Tests if the specified `Rectangle2D` is inside the boundary of this `Shape`.                                                                                                                                                                                                        |
    | `java.awt.Shape`             | `createTransformedShape``(java.awt.geom.AffineTransform at)`<br>Returns a new transformed `Shape`.                                                                                                                                                                                                                               |
    | `void`                       | `curveTo``(double x1, double y1, double x2, double y2, double x3, double y3)`<br>Adds a curved segment, defined by three new points, to the path by drawing a Bézier curve that intersects both the current coordinates and the coordinates (x3, y3), using the specified points (x1, y1) and (x2, y2) as Bézier control points. |
    | `java.awt.Rectangle`         | `getBounds``()`<br>Return the bounding box of the path.                                                                                                                                                                                                                                                                          |
    | `java.awt.geom.Rectangle2D`  | `getBounds2D``()`<br>Returns the bounding box of the path.                                                                                                                                                                                                                                                                       |
    | `java.awt.geom.Point2D`      | `getCurrentPoint``()`<br>Returns the coordinates most recently added to the end of the path as a `Point2D` object.                                                                                                                                                                                                               |
    | `java.awt.geom.PathIterator` | `getPathIterator``(java.awt.geom.AffineTransform at)`<br>Returns a `PathIterator` object that iterates along the boundary of this `Shape` and provides access to the geometry of the outline of this `Shape`.                                                                                                                    |
    | `java.awt.geom.PathIterator` | `getPathIterator``(java.awt.geom.AffineTransform at, double flatness)`<br>Returns a `PathIterator` object that iterates along the boundary of the flattened `Shape` and provides access to the geometry of the outline of the `Shape`.                                                                                           |
    | `int`                        | `getWindingRule``()`<br>Returns the fill style winding rule.                                                                                                                                                                                                                                                                     |
    | `boolean`                    | `intersects``(double x, double y, double w, double h)`<br>Tests if the interior of this `Shape` intersects the interior of a specified set of rectangular coordinates.                                                                                                                                                           |
    | `boolean`                    | `intersects``(java.awt.geom.Rectangle2D r)`<br>Tests if the interior of this `Shape` intersects the interior of a specified `Rectangle2D`.                                                                                                                                                                                       |
    | `void`                       | `lineTo``(double x, double y)`<br>Adds a point to the path by drawing a straight line from the current coordinates to the new specified coordinates.                                                                                                                                                                             |
    | `void`                       | `moveTo``(double x, double y)`<br>Adds a point to the path by moving to the specified coordinates.                                                                                                                                                                                                                               |
    | `void`                       | `quadTo``(double x1, double y1, double x2, double y2)`<br>Adds a curved segment, defined by two new points, to the path by drawing a Quadratic curve that intersects both the current coordinates and the coordinates (x2, y2), using the specified point (x1, y1) as a quadratic parametric control point.                      |
    | `void`                       | `reset``()`<br>Resets the path to empty.                                                                                                                                                                                                                                                                                         |
    | `void`                       | `setWindingRule``(int rule)`<br>Sets the winding rule for this path to the specified value.                                                                                                                                                                                                                                      |
    | `void`                       | `transform``(java.awt.geom.AffineTransform at)`<br>Transforms the geometry of this path using the specified `AffineTransform`.                                                                                                                                                                                                   |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### WIND_EVEN_ODD

          public static final int WIND_EVEN_ODD

      An even-odd winding rule for determining the interior of a path.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### WIND_NON_ZERO

          public static final int WIND_NON_ZERO

      A non-zero winding rule for determining the interior of a path.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### SDODoubleGeneralPath

          public SDODoubleGeneralPath()

      Constructs a new `GeneralPath` object. If an operation performed on this path requires the interior of the path to be defined then the default NON_ZERO winding rule is used.
      See Also:
      `WIND_NON_ZERO`

    <!-- -->

    - #### SDODoubleGeneralPath

          public SDODoubleGeneralPath(int rule)

      Constructs a new `GeneralPath` object with the specified winding rule to control operations that require the interior of the path to be defined.
      Parameters:
      `rule` - the winding rule

      See Also:
      `WIND_EVEN_ODD`, `WIND_NON_ZERO`

    <!-- -->

    - #### SDODoubleGeneralPath

          public SDODoubleGeneralPath(int rule,
                                      int initialCapacity)

      Constructs a new `GeneralPath` object with the specified winding rule and the specified initial capacity to store path coordinates. This number is an initial guess as to how many path segments are in the path, but the storage is expanded as needed to store whatever path segments are added to this path.
      Parameters:
      `rule` - the winding rule

      `initialCapacity` - the estimate for the number of path segments in the path

      See Also:
      `WIND_EVEN_ODD`, `WIND_NON_ZERO`

    <!-- -->

    - #### SDODoubleGeneralPath

          public SDODoubleGeneralPath(java.awt.Shape s)

      Constructs a new `GeneralPath` object from an arbitrary `Shape` object. All of the initial geometry and the winding rule for this path are taken from the specified `Shape` object.
      Parameters:
      `s` - the specified `Shape` object

  <!-- -->

  - ### Method Detail

    - #### moveTo

          public void moveTo(double x,
                             double y)

      Adds a point to the path by moving to the specified coordinates.
      Parameters:
      `x` - the specified x coordinate

      `y` - the specified y coordinate

    <!-- -->

    - #### lineTo

          public void lineTo(double x,
                             double y)

      Adds a point to the path by drawing a straight line from the current coordinates to the new specified coordinates.
      Parameters:
      `x` - the specified x coordinate

      `y` - the specified y coordinate

    <!-- -->

    - #### quadTo

          public void quadTo(double x1,
                             double y1,
                             double x2,
                             double y2)

      Adds a curved segment, defined by two new points, to the path by drawing a Quadratic curve that intersects both the current coordinates and the coordinates (x2, y2), using the specified point (x1, y1) as a quadratic parametric control point.
      Parameters:
      `x1` - the x coordinate of the first quadratic control point

      `y1` - the y coordinate of the first quadratic control point

      `x2` - the x coordinate of the final endpoint

      `y2` - the y coordinate of the final endpoint

    <!-- -->

    - #### curveTo

          public void curveTo(double x1,
                              double y1,
                              double x2,
                              double y2,
                              double x3,
                              double y3)

      Adds a curved segment, defined by three new points, to the path by drawing a Bézier curve that intersects both the current coordinates and the coordinates (x3, y3), using the specified points (x1, y1) and (x2, y2) as Bézier control points.
      Parameters:
      `x1` - the x coordinate of the first Béezier control point

      `y1` - the y coordinate of the first Béezier control point

      `x2` - the x coordinate of the second Bézier control point

      `y2` - the y coordinate of the second Bézier control point

      `x3` - the x coordinate of the final endpoint

      `y3` - the y coordinate of the final endpoint

    <!-- -->

    - #### closePath

          public void closePath()

      Closes the current subpath by drawing a straight line back to the coordinates of the last `moveTo`. If the path is already closed then this method has no effect.

    <!-- -->

    - #### append

          public void append(java.awt.Shape s,
                             boolean connect)

      Appends the geometry of the specified `Shape` object to the path, possibly connecting the new geometry to the existing path segments with a line segment. If the `connect` parameter is `true` and the path is not empty then any initial `moveTo` in the geometry of the appended `Shape` is turned into a `lineTo` segment. If the destination coordinates of such a connecting `lineTo` segment match the ending coordinates of a currently open subpath then the segment is omitted as superfluous. The winding rule of the specified `Shape` is ignored and the appended geometry is governed by the winding rule specified for this path.
      Parameters:
      `s` - the `Shape` whose geometry is appended to this path

      `connect` - a boolean to control whether or not to turn an initial `moveTo` segment into a `lineTo` segment to connect the new geometry to the existing path

    <!-- -->

    - #### append

          public void append(java.awt.geom.PathIterator pi,
                             boolean connect)

      Appends the geometry of the specified `PathIterator` object to the path, possibly connecting the new geometry to the existing path segments with a line segment. If the `connect` parameter is `true` and the path is not empty then any initial `moveTo` in the geometry of the appended `Shape` is turned into a `lineTo` segment. If the destination coordinates of such a connecting `lineTo` segment match the ending coordinates of a currently open subpath then the segment is omitted as superfluous. The winding rule of the specified `Shape` is ignored and the appended geometry is governed by the winding rule specified for this path.
      Parameters:
      `pi` - the `PathIterator` whose geometry is appended to this path

      `connect` - a boolean to control whether or not to turn an initial `moveTo` segment into a `lineTo` segment to connect the new geometry to the existing path

    <!-- -->

    - #### getWindingRule

          public int getWindingRule()

      Returns the fill style winding rule.
      Returns:
      an integer representing the current winding rule.

      See Also:
      `WIND_EVEN_ODD`, `WIND_NON_ZERO`, `setWindingRule(int)`

    <!-- -->

    - #### setWindingRule

          public void setWindingRule(int rule)

      Sets the winding rule for this path to the specified value.
      Parameters:
      `rule` - an integer representing the specified winding rule

      Throws:
      `IllegalArgumentException` - if `rule` is not either `WIND_EVEN_ODD` or `WIND_NON_ZERO`

      See Also:
      `WIND_EVEN_ODD`, `WIND_NON_ZERO`, `getWindingRule()`

    <!-- -->

    - #### getCurrentPoint

          public java.awt.geom.Point2D getCurrentPoint()

      Returns the coordinates most recently added to the end of the path as a `Point2D` object.
      Returns:
      a `Point2D` object containing the ending coordinates of the path or `null` if there are no points in the path.

    <!-- -->

    - #### reset

          public void reset()

      Resets the path to empty. The append position is set back to the beginning of the path and all coordinates and point types are forgotten.

    <!-- -->

    - #### transform

          public void transform(java.awt.geom.AffineTransform at)

      Transforms the geometry of this path using the specified `AffineTransform`. The geometry is transformed in place, which permanently changes the boundary defined by this object.
      Parameters:
      `at` - the `AffineTransform` used to transform the area

    <!-- -->

    - #### createTransformedShape

          public java.awt.Shape createTransformedShape(java.awt.geom.AffineTransform at)

      Returns a new transformed `Shape`.
      Parameters:
      `at` - the `AffineTransform` used to transform a new `Shape`.

      Returns:
      a new `Shape`, transformed with the specified `AffineTransform`.

    <!-- -->

    - #### getBounds

          public java.awt.Rectangle getBounds()

      Return the bounding box of the path.
      Specified by:
      `getBounds` in interface `java.awt.Shape`

      Returns:
      a `Rectangle` object that bounds the current path.

    <!-- -->

    - #### getBounds2D

          public java.awt.geom.Rectangle2D getBounds2D()

      Returns the bounding box of the path.
      Specified by:
      `getBounds2D` in interface `java.awt.Shape`

      Returns:
      a `Rectangle2D` object that bounds the current path.

    <!-- -->

    - #### contains

          public boolean contains(double x,
                                  double y)

      Tests if the specified coordinates are inside the boundary of this `Shape`.
      Specified by:
      `contains` in interface `java.awt.Shape`

      Parameters:
      `x` - the specified x coordinate

      `y` - the specified y coordinate

      Returns:
      `true` if the specified coordinates are inside this `Shape`; `false` otherwise

    <!-- -->

    - #### contains

          public boolean contains(java.awt.geom.Point2D p)

      Tests if the specified `Point2D` is inside the boundary of this `Shape`.
      Specified by:
      `contains` in interface `java.awt.Shape`

      Parameters:
      `p` - the specified `Point2D`

      Returns:
      `true` if this `Shape` contains the specified `Point2D`, `false` otherwise.

    <!-- -->

    - #### contains

          public boolean contains(double x,
                                  double y,
                                  double w,
                                  double h)

      Tests if the specified rectangular area is inside the boundary of this `Shape`.
      Specified by:
      `contains` in interface `java.awt.Shape`

      Parameters:
      `x` - the specified x coordinate

      `y` - the specified y coordinate

      `w` - the width of the specified rectangular area

      `h` - the height of the specified rectangular area

      Returns:
      `true` if this `Shape` contains the specified rectangluar area; `false` otherwise.

    <!-- -->

    - #### contains

          public boolean contains(java.awt.geom.Rectangle2D r)

      Tests if the specified `Rectangle2D` is inside the boundary of this `Shape`.
      Specified by:
      `contains` in interface `java.awt.Shape`

      Parameters:
      `r` - a specified `Rectangle2D`

      Returns:
      `true` if this `Shape` bounds the specified `Rectangle2D`; `false` otherwise.

    <!-- -->

    - #### intersects

          public boolean intersects(double x,
                                    double y,
                                    double w,
                                    double h)

      Tests if the interior of this `Shape` intersects the interior of a specified set of rectangular coordinates.
      Specified by:
      `intersects` in interface `java.awt.Shape`

      Parameters:
      `x` - the specified x coordinate

      `y` - the specified y coordinate

      `w` - the width of the specified rectangular coordinates

      `h` - the height of the specified rectangular coordinates

      Returns:
      `true` if this `Shape` and the interior of the specified set of rectangular coordinates intersect each other; `false` otherwise.

    <!-- -->

    - #### intersects

          public boolean intersects(java.awt.geom.Rectangle2D r)

      Tests if the interior of this `Shape` intersects the interior of a specified `Rectangle2D`.
      Specified by:
      `intersects` in interface `java.awt.Shape`

      Parameters:
      `r` - the specified `Rectangle2D`

      Returns:
      `true` if this `Shape` and the interior of the specified `Rectangle2D` intersect each other; `false` otherwise.

    <!-- -->

    - #### getPathIterator

          public java.awt.geom.PathIterator getPathIterator(java.awt.geom.AffineTransform at)

      Returns a `PathIterator` object that iterates along the boundary of this `Shape` and provides access to the geometry of the outline of this `Shape`. The iterator for this class is not multi-threaded safe, which means that this `GeneralPath` class does not guarantee that modifications to the geometry of this `GeneralPath` object do not affect any iterations of that geometry that are already in process.
      Specified by:
      `getPathIterator` in interface `java.awt.Shape`

      Parameters:
      `at` - an `AffineTransform`

      Returns:
      a new `PathIterator` that iterates along the boundary of this `Shape` and provides access to the geometry of this `Shape`'s outline

    <!-- -->

    - #### getPathIterator

          public java.awt.geom.PathIterator getPathIterator(java.awt.geom.AffineTransform at,
                                                            double flatness)

      Returns a `PathIterator` object that iterates along the boundary of the flattened `Shape` and provides access to the geometry of the outline of the `Shape`. The iterator for this class is not multi-threaded safe, which means that this `GeneralPath` class does not guarantee that modifications to the geometry of this `GeneralPath` object do not affect any iterations of that geometry that are already in process.
      Specified by:
      `getPathIterator` in interface `java.awt.Shape`

      Parameters:
      `at` - an `AffineTransform`

      `flatness` - the maximum distance that the line segments used to approximate the curved segments are allowed to deviate from any point on the original curve

      Returns:
      a new `PathIterator` that iterates along the flattened `Shape` boundary.

    <!-- -->

    - #### clone

          public java.lang.Object clone()

      Creates a new object of the same class as this object.
      Overrides:
      `clone` in class `java.lang.Object`

      Returns:
      a clone of this instance.

      Throws:
      `java.lang.OutOfMemoryError` - if there is not enough memory.

      Since:
      1.2

      See Also:
      `Cloneable`

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

- [Prev Class](SchemaEntityResolver.md)
- [Next Class](SdoPointInPolygon.md)

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
