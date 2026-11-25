Skip navigation links

- [Overview](../../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../../deprecated-list.md)
- [Index](../../../../../../../index-all.md)
- [Help](../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](DefaultSelectionManager.md)
- [Next Class](EditableLayer.md)

<!-- -->

- [Frames](../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.vis.maps.core

## Class Drawable

- java.lang.Object

- - oracle.spatial.network.nfe.vis.maps.core.Drawable

<!-- -->

-

  ------------------------------------------------------------------------



      public class Drawable
      extends java.lang.Object

  A Drawable references either a Java2D Shape or Point2D instance, but never both. It's sole purpose is to provide a unified way of representing either a shape (polygon, polyline, rectangle et al) or a point, since Shape and Point2D do not share a common drawing interface in Java. For multi points, a shape has lineTos and needs a special handling when rendering. Drawable also implements useful Shape methods such as getBounds() and contains(), but extends them to the point type as well.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                               |
    |-------------------|-----------------------------------------------------|
    | `static int`      | `TYPE_AREA`<br>polygon or multi-polygon             |
    | `static int`      | `TYPE_IMAGE`<br>Image                               |
    | `static int`      | `TYPE_LINESTRING`<br>linestring or multi-linestring |
    | `static int`      | `TYPE_ORIENTED_POINT`<br>Oriented point             |
    | `static int`      | `TYPE_POINT`<br>point or multi-point                |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                           |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `Drawable``()`                                                                                                                                                                                                        |
    | `Drawable``(java.awt.Image img)`                                                                                                                                                                                      |
    | `Drawable``(java.awt.geom.Point2D point)`<br>Constructs a Drawable instance that is a point.                                                                                                                          |
    | `Drawable``(java.awt.geom.Point2D point, double vectorX, double vectorY)`<br>Constructs a Drawable instance that is an oriented point, with vectorX and vectorY representing the end point of the orientation vector. |
    | `Drawable``(java.awt.Shape shape, int type)`<br>Constructs a Drawable instance that is a shape.                                                                                                                       |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type           | Method and Description                                                                                                                                                                               |
    |-----------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                   | `contains``(double x, double y)`<br>Tests if the specified coordinates are inside the boundary of the Drawable.                                                                                      |
    | `boolean`                   | `contains``(java.awt.geom.Point2D p)`<br>Tests if a specified Point2D is inside the boundary of the Shape.                                                                                           |
    | `static Drawable`           | `createDrawable``(`[`JGeometry`](../../../../../geometry/JGeometry.md)`[] geoms, java.awt.geom.AffineTransform at)`<br>Creates a Drawable instance collection out from the given JGeometry instances |
    | `static Drawable`           | `createDrawable``(`[`JGeometry`](../../../../../geometry/JGeometry.md)` geom, java.awt.geom.AffineTransform at)`<br>Creates a Drawable instance out from a JGeometry instance                        |
    | `void`                      | `draw``(java.awt.Graphics2D g)`<br>Draws the current Drawable instance                                                                                                                               |
    | `void`                      | `fill``(java.awt.Graphics2D g)`<br>Fills the current Drawable instance                                                                                                                               |
    | `java.awt.Rectangle`        | `getBounds``()`<br>Returns an integer Rectangle that completely encloses the Drawable.                                                                                                               |
    | `java.awt.geom.Rectangle2D` | `getBounds2D``()`<br>Returns a high precision and more accurate bounding box of the Drawable than the getBounds method.                                                                              |
    | `static int`                | `getDefaultPointSize``()`<br>Gets the default point size                                                                                                                                             |
    | `Drawable`                  | `getLast``()`<br>Gets the last Drawable instance in a Drawable collection                                                                                                                            |
    | `Drawable`                  | `getNext``()`<br>Gets the next Drawable instance in a Drawable collection                                                                                                                            |
    | `java.awt.geom.Point2D`     | `getPoint``()`<br>Gets the referenced point.                                                                                                                                                         |
    | `java.awt.Shape`            | `getShape``()`<br>Gets the referenced shape.                                                                                                                                                         |
    | `int`                       | `getType``()`<br>Gets the type of drawable.                                                                                                                                                          |
    | `double`                    | `getVectorX``()`<br>Gets the end point's x ordinate of an oriented point                                                                                                                             |
    | `double`                    | `getVectorY``()`<br>Gets the end point's y ordinate of an oriented point                                                                                                                             |
    | `boolean`                   | `hitTest``(java.awt.geom.Point2D p, double tolerance)`<br>Hit-test the specified point against this drawable object.                                                                                 |
    | `boolean`                   | `isPoint``()`<br>Tests to see if this Drawable is a point.                                                                                                                                           |
    | `boolean`                   | `isShape``()`<br>Tests to see if this Drawable is a shape.                                                                                                                                           |
    | `static void`               | `setDefaultPointSize``(int defaultPointSize)`<br>Sets the default point size                                                                                                                         |
    | `void`                      | `setNext``(Drawable dr)`<br>Sets the next Drawable instance for a collection of Drawable instances                                                                                                   |
    | `void`                      | `setPoint``(java.awt.geom.Point2D pt)`                                                                                                                                                               |
    | `void`                      | `setShape``(java.awt.Shape shp, int type)`<br>Sets the shape for this drawable.                                                                                                                      |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### TYPE_AREA

          public static final int TYPE_AREA

      polygon or multi-polygon
      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### TYPE_LINESTRING

          public static final int TYPE_LINESTRING

      linestring or multi-linestring
      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### TYPE_POINT

          public static final int TYPE_POINT

      point or multi-point
      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### TYPE_ORIENTED_POINT

          public static final int TYPE_ORIENTED_POINT

      Oriented point
      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### TYPE_IMAGE

          public static final int TYPE_IMAGE

      Image
      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### Drawable

          public Drawable()

    <!-- -->

    - #### Drawable

          public Drawable(java.awt.Shape shape,
                          int type)

      Constructs a Drawable instance that is a shape.
      Parameters:
      `shape` - the shape to be referenced by this instance.

      `type` - the type of shape which is either TYPE_AREA (for polygon or multi-polygons) or TYPE_LINESTRING (for linestring or multi-linestrings).

    <!-- -->

    - #### Drawable

          public Drawable(java.awt.geom.Point2D point)

      Constructs a Drawable instance that is a point.
      Parameters:
      `point` - the point to be referenced by this instance.

    <!-- -->

    - #### Drawable

          public Drawable(java.awt.geom.Point2D point,
                          double vectorX,
                          double vectorY)

      Constructs a Drawable instance that is an oriented point, with vectorX and vectorY representing the end point of the orientation vector.

    <!-- -->

    - #### Drawable

          public Drawable(java.awt.Image img)

  <!-- -->

  - ### Method Detail

    - #### getShape

          public java.awt.Shape getShape()

      Gets the referenced shape. Should only be called if the isShape() test returns true.
      Returns:
      the shape object.

    <!-- -->

    - #### getPoint

          public java.awt.geom.Point2D getPoint()

      Gets the referenced point. Should only be called if the isPoint() test returns true.
      Returns:
      the point object.

    <!-- -->

    - #### setShape

          public void setShape(java.awt.Shape shp,
                               int type)

      Sets the shape for this drawable. It also removes the point object if it exists.
      Parameters:
      `shp` -

    <!-- -->

    - #### setPoint

          public void setPoint(java.awt.geom.Point2D pt)

    <!-- -->

    - #### isShape

          public boolean isShape()

      Tests to see if this Drawable is a shape. A shape can be either a polygon or a linestring.
      Returns:
      true if this Drawable references a shape.

    <!-- -->

    - #### isPoint

          public boolean isPoint()

      Tests to see if this Drawable is a point.
      Returns:
      true if this Drawable is a point.

    <!-- -->

    - #### getBounds2D

          public java.awt.geom.Rectangle2D getBounds2D()

      Returns a high precision and more accurate bounding box of the Drawable than the getBounds method. For point Drawable, the returned rectangle has a zero width and height.
      Returns:
      an instance of Rectangle2D that is a high-precision bounding box of the Drawable.

    <!-- -->

    - #### getBounds

          public java.awt.Rectangle getBounds()

      Returns an integer Rectangle that completely encloses the Drawable. For point Drawable, the returned rectangle has a zero width and height.
      Returns:
      an integer Rectangle that completely encloses the Shape.

    <!-- -->

    - #### contains

          public boolean contains(double x,
                                  double y)

      Tests if the specified coordinates are inside the boundary of the Drawable.
      Parameters:
      `x` - the specified x coordinate

      `y` - the specified y coordinate

      Returns:
      true if the specified coordinates are inside the Shape boundary (if Shape type) or match the point location (if Point type); false otherwise.

    <!-- -->

    - #### contains

          public boolean contains(java.awt.geom.Point2D p)

      Tests if a specified Point2D is inside the boundary of the Shape.
      Parameters:
      `p` - a specified Point2D

      Returns:
      true if the specified point is inside the Shape boundary (for shape Drawable) or match the point location (for point Drawable); false otherwise.

    <!-- -->

    - #### hitTest

          public boolean hitTest(java.awt.geom.Point2D p,
                                 double tolerance)

      Hit-test the specified point against this drawable object. If the drawable contains or interacts with the point then this method returns true. For points or lines this test also takes into account the provided tolerance value. It basically creates a buffer around a linestring or point, then does a hit-test with the generated buffer polygon.
      Parameters:

      `p` - the point to test

      `tolerance` - the tolerance value to be considered; value should be in pixels.

      Returns:

    <!-- -->

    - #### draw

          public void draw(java.awt.Graphics2D g)

      Draws the current Drawable instance
      Parameters:
      `g` -

    <!-- -->

    - #### fill

          public void fill(java.awt.Graphics2D g)

      Fills the current Drawable instance
      Parameters:
      `g` -

    <!-- -->

    - #### setNext

          public void setNext(Drawable dr)

      Sets the next Drawable instance for a collection of Drawable instances
      Parameters:
      `dr` -

    <!-- -->

    - #### getNext

          public Drawable getNext()

      Gets the next Drawable instance in a Drawable collection
      Returns:

    <!-- -->

    - #### getLast

          public Drawable getLast()

      Gets the last Drawable instance in a Drawable collection
      Returns:

    <!-- -->

    - #### getDefaultPointSize

          public static int getDefaultPointSize()

      Gets the default point size
      Returns:

    <!-- -->

    - #### setDefaultPointSize

          public static void setDefaultPointSize(int defaultPointSize)

      Sets the default point size
      Parameters:
      `defaultPointSize` -

    <!-- -->

    - #### getType

          public int getType()

      Gets the type of drawable.
      Returns:
      TYPE_AREA if this is a polygon type, TYPE_LINESTRING if a linestring (curve) type, or TYPE_POINT if this is of point type.

    <!-- -->

    - #### getVectorX

          public double getVectorX()

      Gets the end point's x ordinate of an oriented point
      Returns:

    <!-- -->

    - #### getVectorY

          public double getVectorY()

      Gets the end point's y ordinate of an oriented point
      Returns:

    <!-- -->

    - #### createDrawable

          public static Drawable createDrawable(JGeometry geom,
                                                java.awt.geom.AffineTransform at)

      Creates a Drawable instance out from a JGeometry instance
      Parameters:
      `geom` - a JGeometry instance

      `at` - the AffineTransform used

      Returns:
      a Drawable instance. In case of a geometry collection, it returns the first element in the collection

    <!-- -->

    - #### createDrawable

          public static Drawable createDrawable(JGeometry[] geoms,
                                                java.awt.geom.AffineTransform at)

      Creates a Drawable instance collection out from the given JGeometry instances
      Parameters:
      `geom` - a JGeometry array

      `at` - the AffineTransform used

      Returns:
      the first element of the drawable collection

Skip navigation links

- [Overview](../../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../../deprecated-list.md)
- [Index](../../../../../../../index-all.md)
- [Help](../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](DefaultSelectionManager.md)
- [Next Class](EditableLayer.md)

<!-- -->

- [Frames](../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../allclasses-noframe.md)

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
