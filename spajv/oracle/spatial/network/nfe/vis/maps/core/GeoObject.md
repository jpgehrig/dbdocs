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

- [Prev Class](GeoDataProducer.md)
- [Next Class](GeoObjectLayer.md)

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

## Interface GeoObject

- All Superinterfaces:
  java.lang.Cloneable

  <!-- -->

  All Known Implementing Classes:
  [AbstractFeature](../geoobject/AbstractFeature.md), [GeometryFeature](../geoobject/GeometryFeature.md), [ImageObject](../geoobject/ImageObject.md), [NFEFeatureElementGeoObject](../../../model/spatial/NFEFeatureElementGeoObject.md), [NFEGeoObject](../../../model/spatial/NFEGeoObject.md), [NFENetworkElementGeoObject](../../../model/spatial/NFENetworkElementGeoObject.md)

  ------------------------------------------------------------------------



      public interface GeoObject
      extends java.lang.Cloneable

  An interface representing a piece of geo-spatial object. It can be a vector shape, a raster imagery, or any other geo-spatial entity, even an entire data set. A GeoObject must always have a key, which can be obtained using the getKey() method. It is also typically associated with a Layer instance, although this is optional.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type           | Method and Description                                                                                                                                                |
    |-----------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                   | `equals``(java.lang.Object obj)`                                                                                                                                      |
    | [`Drawable`](Drawable.md)   | `getDrawable``(java.awt.geom.AffineTransform viewportTransform)`<br>This method returns a drawable Java2D shape or point that can be directly rendered onto a device. |
    | `java.lang.Object`          | `getKey``()`<br>Gets the key of the selected object.                                                                                                                  |
    | [`Layer`](Layer.md)         | `getLayer``()`<br>Gets the associated layer for this object.                                                                                                          |
    | `java.awt.geom.Rectangle2D` | `getMBR``()`<br>Gets the minimum bounding rectangle of this geo-object.                                                                                               |
    | `int`                       | `hashCode``()`                                                                                                                                                        |
    | `boolean`                   | `isSubElementOf``(GeoObject obj)`<br>Returns true if this GeoObject is a sub element of the provided GeoObject                                                        |
    | `java.lang.Object`          | `setKey``(java.lang.Object key)`<br>Sets a new key on the object.                                                                                                     |
    | `void`                      | `setLayer``(`[`Layer`](Layer.md)` layer)`<br>Sets the layer to be associated with this object.                                                                        |
    | `java.util.List<GeoObject>` | `substract``(java.util.List<? extends GeoObject> objs)`<br>Returns a set of GeoObjects that represent the substraction of the provided GeoObjects from this GeoObject |

<!-- -->

- - ### Method Detail

    - #### equals

          boolean equals(java.lang.Object obj)

      Overrides:
      `equals` in class `java.lang.Object`

    <!-- -->

    - #### hashCode

          int hashCode()

      Overrides:
      `hashCode` in class `java.lang.Object`

    <!-- -->

    - #### getKey

          java.lang.Object getKey()

      Gets the key of the selected object.
      Returns:
      the key

    <!-- -->

    - #### setKey

          java.lang.Object setKey(java.lang.Object key)

      Sets a new key on the object.
      Parameters:
      `key` - the new key to be set.

      Returns:
      previously set key

    <!-- -->

    - #### getLayer

          Layer getLayer()

      Gets the associated layer for this object.
      Returns:
      typically an Layer instance that owns this object.

    <!-- -->

    - #### setLayer

          void setLayer(Layer layer)

      Sets the layer to be associated with this object.
      Parameters:
      `layer` - the Layer instance to be associated.

    <!-- -->

    - #### getDrawable

          Drawable getDrawable(java.awt.geom.AffineTransform viewportTransform)

      This method returns a drawable Java2D shape or point that can be directly rendered onto a device. If a non-null viewportTransform is supplied, then it is applied and result returned.
      Parameters:
      `viewportTransform` -

      Returns:
      a Drawable instance that references either a Shape or a Point2D

    <!-- -->

    - #### getMBR

          java.awt.geom.Rectangle2D getMBR()

      Gets the minimum bounding rectangle of this geo-object. The rectangle is in the same coordinate system as the object value.

    <!-- -->

    - #### isSubElementOf

          boolean isSubElementOf(GeoObject obj)

      Returns true if this GeoObject is a sub element of the provided GeoObject
      Parameters:

      `obj` -

      Returns:

    <!-- -->

    - #### substract

          java.util.List<GeoObject> substract(java.util.List<? extends GeoObject> objs)

      Returns a set of GeoObjects that represent the substraction of the provided GeoObjects from this GeoObject
      Parameters:

      `objs` -

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

- [Prev Class](GeoDataProducer.md)
- [Next Class](GeoObjectLayer.md)

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
