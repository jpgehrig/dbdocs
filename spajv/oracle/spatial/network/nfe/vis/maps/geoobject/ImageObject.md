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

- [Prev Class](GeometryFeature.md)
- [Next Class](WorkSpace.md)

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

## Class ImageObject

- java.lang.Object

- - oracle.spatial.network.nfe.vis.maps.geoobject.ImageObject

<!-- -->

- All Implemented Interfaces:
  java.lang.Cloneable, [GeoObject](../core/GeoObject.md)

  ------------------------------------------------------------------------



      public class ImageObject
      extends java.lang.Object
      implements GeoObject

  An image based feature to be rendered in canvas

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                        |
    |--------------------------------------------------------------------------------------------------------------------|
    | `ImageObject``(java.lang.Object key, java.awt.Image value)`<br>Creates a new instance with the given key and image |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                       | Method and Description                                                                                                                                                                           |
    |---------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `ImageObject`                                           | `clone``()`                                                                                                                                                                                      |
    | [`Drawable`](../core/Drawable.md)                       | `getDrawable``(java.awt.geom.AffineTransform viewportTransform)`<br>This method returns a drawable Java2D shape or point that can be directly rendered onto a device.                            |
    | [`Drawable`](../core/Drawable.md)`[]`                   | `getDrawables``(java.awt.geom.AffineTransform viewportTransform)`<br>This method returns an array of drawable Java2D shape or point that can be directly rendered onto a device.                 |
    | `java.awt.Image`                                        | `getImage``()`<br>Gets the image associated with this geo-object.                                                                                                                                |
    | `java.lang.Object`                                      | `getKey``()`<br>Gets the key of the selected object.                                                                                                                                             |
    | [`Layer`](../core/Layer.md)                             | `getLayer``()`<br>Gets the associated layer for this object.                                                                                                                                     |
    | `java.awt.geom.Rectangle2D`                             | `getMBR``()`<br>Gets the minimum bounding rectangle of this geo-object.                                                                                                                          |
    | `boolean`                                               | `isSubElementOf``(`[`GeoObject`](../core/GeoObject.md)` obj)`<br>Returns true if this GeoObject is a sub element of the provided GeoObject                                                       |
    | `java.lang.Object`                                      | `setKey``(java.lang.Object key)`<br>Sets a new key on the object.                                                                                                                                |
    | `void`                                                  | `setLayer``(`[`Layer`](../core/Layer.md)` layer)`<br>Sets the layer to be associated with this object.                                                                                           |
    | `java.util.List<`[`GeoObject`](../core/GeoObject.md)`>` | `substract``(java.util.List<? extends `[`GeoObject`](../core/GeoObject.md)`> obj)`<br>Returns a set of GeoObjects that represent the substraction of the provided GeoObjects from this GeoObject |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.nfe.vis.maps.core.[GeoObject](../core/GeoObject.md)

      [`equals`](../core/GeoObject.md)`, `[`hashCode`](../core/GeoObject.md)

<!-- -->

- - ### Constructor Detail

    - #### ImageObject

          public ImageObject(java.lang.Object key,
                             java.awt.Image value)

      Creates a new instance with the given key and image
      Parameters:
      `key` -

      `value` -

  <!-- -->

  - ### Method Detail

    - #### clone

          public ImageObject clone()

      Overrides:
      `clone` in class `java.lang.Object`

    <!-- -->

    - #### isSubElementOf

          public boolean isSubElementOf(GeoObject obj)

      Description copied from interface: [`GeoObject`](../core/GeoObject.md)
      Returns true if this GeoObject is a sub element of the provided GeoObject
      Specified by:

      [`isSubElementOf`](../core/GeoObject.md) in interface [`GeoObject`](../core/GeoObject.md)

      Returns:

    <!-- -->

    - #### substract

          public java.util.List<GeoObject> substract(java.util.List<? extends GeoObject> obj)

      Description copied from interface: [`GeoObject`](../core/GeoObject.md)
      Returns a set of GeoObjects that represent the substraction of the provided GeoObjects from this GeoObject
      Specified by:

      [`substract`](../core/GeoObject.md) in interface [`GeoObject`](../core/GeoObject.md)

      Returns:

    <!-- -->

    - #### getKey

          public java.lang.Object getKey()

      Gets the key of the selected object.
      Specified by:
      [`getKey`](../core/GeoObject.md) in interface [`GeoObject`](../core/GeoObject.md)

      Returns:
      the key

    <!-- -->

    - #### setKey

          public java.lang.Object setKey(java.lang.Object key)

      Sets a new key on the object.
      Specified by:
      [`setKey`](../core/GeoObject.md) in interface [`GeoObject`](../core/GeoObject.md)

      Parameters:
      `key` - the new key to be set.

      Returns:
      previously set key

    <!-- -->

    - #### getLayer

          public Layer getLayer()

      Gets the associated layer for this object.
      Specified by:
      [`getLayer`](../core/GeoObject.md) in interface [`GeoObject`](../core/GeoObject.md)

      Returns:
      the Layer instance that owns this object.

    <!-- -->

    - #### setLayer

          public void setLayer(Layer layer)

      Sets the layer to be associated with this object.
      Specified by:
      [`setLayer`](../core/GeoObject.md) in interface [`GeoObject`](../core/GeoObject.md)

      Parameters:
      `layer` - the layer to be associated.

    <!-- -->

    - #### getImage

          public java.awt.Image getImage()

      Gets the image associated with this geo-object.
      Returns:

    <!-- -->

    - #### getDrawable

          public Drawable getDrawable(java.awt.geom.AffineTransform viewportTransform)

      This method returns a drawable Java2D shape or point that can be directly rendered onto a device. If a non-null viewportTransform is supplied, then it is applied and result returned.
      Specified by:
      [`getDrawable`](../core/GeoObject.md) in interface [`GeoObject`](../core/GeoObject.md)

      Parameters:
      `viewportTransform` -

      Returns:
      a Drawable instance that references either a Shape or a Point2D

    <!-- -->

    - #### getDrawables

          public Drawable[] getDrawables(java.awt.geom.AffineTransform viewportTransform)

      This method returns an array of drawable Java2D shape or point that can be directly rendered onto a device. If a non-null viewportTransform is supplied, then it is applied and result returned. This can be used to get pieces of geometry collections or multi points.
      Parameters:
      `viewportTransform` -

      Returns:
      a Drawable instance that references either a Shape or a Point2D

    <!-- -->

    - #### getMBR

          public java.awt.geom.Rectangle2D getMBR()

      Description copied from interface: [`GeoObject`](../core/GeoObject.md)
      Gets the minimum bounding rectangle of this geo-object. The rectangle is in the same coordinate system as the object value.
      Specified by:
      [`getMBR`](../core/GeoObject.md) in interface [`GeoObject`](../core/GeoObject.md)

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

- [Prev Class](GeometryFeature.md)
- [Next Class](WorkSpace.md)

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
