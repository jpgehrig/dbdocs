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

- [Prev Class](AbstractFeature.md)
- [Next Class](ImageObject.md)

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

oracle.spatial.network.nfe.vis.maps.geoobject

## Class GeometryFeature

- java.lang.Object

- - [oracle.spatial.network.nfe.vis.maps.geoobject.AbstractFeature](AbstractFeature.md)

  - - oracle.spatial.network.nfe.vis.maps.geoobject.GeometryFeature

<!-- -->

- All Implemented Interfaces:
  java.lang.Cloneable, [GeoObject](../core/GeoObject.md)

  ------------------------------------------------------------------------



      public class GeometryFeature
      extends AbstractFeature

  Defines a geometry feature to be used in editable geometry sets.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `GeometryFeature``()`       |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                       | Method and Description                                                                                                                                                                           |
    |---------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Drawable`](../core/Drawable.md)                       | `getDrawable``(java.awt.geom.AffineTransform viewportTransform)`<br>This method returns a drawable Java2D shape or point that can be directly rendered onto a device.                            |
    | `java.awt.geom.Rectangle2D`                             | `getMBR``()`<br>Returns the minimum bounding rectangle of the spatial attribute.                                                                                                                 |
    | [`JGeometry`](../../../../../geometry/JGeometry.md)     | `getSpatialAttribute``()`<br>Returns the spatial attribute object.                                                                                                                               |
    | [`JGeometry`](../../../../../geometry/JGeometry.md)     | `getSpatialAttributeClone``()`<br>Returns a clone of the spatial attribute                                                                                                                       |
    | `int`                                                   | `getSpatialDimension``()`<br>Returns the feature spatial dimension.                                                                                                                              |
    | `java.awt.geom.Point2D[]`                               | `getSpatialJavaPoints``()`<br>Returns an array of java points representing the vertexes location of the spatial object.                                                                          |
    | `boolean`                                               | `isSubElementOf``(`[`GeoObject`](../core/GeoObject.md)` obj)`<br>Returns true if this GeoObject is a sub element of the provided GeoObject                                                       |
    | `void`                                                  | `setSpatialAttribute``(java.lang.Object spatialAttr)`<br>Sets the spatial attribute object                                                                                                       |
    | `java.util.List<`[`GeoObject`](../core/GeoObject.md)`>` | `substract``(java.util.List<? extends `[`GeoObject`](../core/GeoObject.md)`> obj)`<br>Returns a set of GeoObjects that represent the substraction of the provided GeoObjects from this GeoObject |

    - ### Methods inherited from class oracle.spatial.network.nfe.vis.maps.geoobject.[AbstractFeature](AbstractFeature.md)

      [`clone`](AbstractFeature.md)`, `[`deepClone`](AbstractFeature.md)`, `[`equals`](AbstractFeature.md)`, `[`getAttribute`](AbstractFeature.md)`, `[`getAttributeNames`](AbstractFeature.md)`, `[`getAttributes`](AbstractFeature.md)`, `[`getAttributes`](AbstractFeature.md)`, `[`getKey`](AbstractFeature.md)`, `[`getLayer`](AbstractFeature.md)`, `[`removeAttribute`](AbstractFeature.md)`, `[`setAttribute`](AbstractFeature.md)`, `[`setAttributes`](AbstractFeature.md)`, `[`setKey`](AbstractFeature.md)`, `[`setLayer`](AbstractFeature.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.nfe.vis.maps.core.[GeoObject](../core/GeoObject.md)

      [`hashCode`](../core/GeoObject.md)

<!-- -->

- - ### Constructor Detail

    - #### GeometryFeature

          public GeometryFeature()

  <!-- -->

  - ### Method Detail

    - #### getSpatialAttribute

          public JGeometry getSpatialAttribute()

      Returns the spatial attribute object.
      Overrides:

      [`getSpatialAttribute`](AbstractFeature.md) in class [`AbstractFeature`](AbstractFeature.md)

      Returns:

    <!-- -->

    - #### setSpatialAttribute

          public void setSpatialAttribute(java.lang.Object spatialAttr)

      Sets the spatial attribute object
      Overrides:
      [`setSpatialAttribute`](AbstractFeature.md) in class [`AbstractFeature`](AbstractFeature.md)

      Parameters:
      `spatialAttr` -

    <!-- -->

    - #### getMBR

          public java.awt.geom.Rectangle2D getMBR()

      Returns the minimum bounding rectangle of the spatial attribute.
      Specified by:

      [`getMBR`](../core/GeoObject.md) in interface [`GeoObject`](../core/GeoObject.md)

      Specified by:

      [`getMBR`](AbstractFeature.md) in class [`AbstractFeature`](AbstractFeature.md)

      Returns:

    <!-- -->

    - #### getSpatialDimension

          public int getSpatialDimension()

      Returns the feature spatial dimension.
      Specified by:
      [`getSpatialDimension`](AbstractFeature.md) in class [`AbstractFeature`](AbstractFeature.md)

      Returns:
      -1 if geometry is null.

    <!-- -->

    - #### getSpatialAttributeClone

          public JGeometry getSpatialAttributeClone()

      Returns a clone of the spatial attribute
      Specified by:

      [`getSpatialAttributeClone`](AbstractFeature.md) in class [`AbstractFeature`](AbstractFeature.md)

      Returns:

    <!-- -->

    - #### getSpatialJavaPoints

          public java.awt.geom.Point2D[] getSpatialJavaPoints()

      Returns an array of java points representing the vertexes location of the spatial object.
      Specified by:

      [`getSpatialJavaPoints`](AbstractFeature.md) in class [`AbstractFeature`](AbstractFeature.md)

      Returns:

    <!-- -->

    - #### getDrawable

          public Drawable getDrawable(java.awt.geom.AffineTransform viewportTransform)

      Description copied from interface: [`GeoObject`](../core/GeoObject.md)
      This method returns a drawable Java2D shape or point that can be directly rendered onto a device. If a non-null viewportTransform is supplied, then it is applied and result returned.
      Returns:
      a Drawable instance that references either a Shape or a Point2D

    <!-- -->

    - #### isSubElementOf

          public boolean isSubElementOf(GeoObject obj)

      Description copied from interface: [`GeoObject`](../core/GeoObject.md)
      Returns true if this GeoObject is a sub element of the provided GeoObject
      Returns:

    <!-- -->

    - #### substract

          public java.util.List<GeoObject> substract(java.util.List<? extends GeoObject> obj)

      Description copied from interface: [`GeoObject`](../core/GeoObject.md)
      Returns a set of GeoObjects that represent the substraction of the provided GeoObjects from this GeoObject
      Returns:

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

- [Prev Class](AbstractFeature.md)
- [Next Class](ImageObject.md)

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
