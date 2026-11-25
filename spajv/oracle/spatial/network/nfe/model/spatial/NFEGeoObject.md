Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFEFeatureElementGeoObject.md)
- [Next Class](NFENetworkElementGeoObject.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.model.spatial

## Class NFEGeoObject

- java.lang.Object

- - oracle.spatial.network.nfe.model.spatial.NFEGeoObject

<!-- -->

- All Implemented Interfaces:
  java.lang.Cloneable, [GeoObject](../../vis/maps/core/GeoObject.md)

  <!-- -->

  Direct Known Subclasses:
  [NFEFeatureElementGeoObject](NFEFeatureElementGeoObject.md), [NFENetworkElementGeoObject](NFENetworkElementGeoObject.md)

  ------------------------------------------------------------------------



      public abstract class NFEGeoObject
      extends java.lang.Object
      implements GeoObject

  The base GeoObject class used by NFE. It exposes the GeoObject's geometry.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                               |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `NFEGeoObject``(java.lang.Object key, `[`JGeometry`](../../../../geometry/JGeometry.md)` geom, `[`Layer`](../../vis/maps/core/Layer.md)` layer)`<br>Allocates a new instance of a subclass implementation |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                   | Method and Description                                                                                                                                                                                        |
    |---------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Drawable`](../../vis/maps/core/Drawable.md)                       | `getDrawable``(java.awt.geom.AffineTransform viewportTransform)`<br>This method returns a drawable Java2D shape or point that can be directly rendered onto a device.                                         |
    | [`JGeometry`](../../../../geometry/JGeometry.md)                    | `getGeometry``()`<br>Gets the GeoObject's geometry                                                                                                                                                            |
    | `java.lang.Object`                                                  | `getKey``()`<br>Gets the key of the selected object.                                                                                                                                                          |
    | [`Layer`](../../vis/maps/core/Layer.md)                             | `getLayer``()`<br>Gets the associated layer for this object.                                                                                                                                                  |
    | `java.awt.geom.Rectangle2D`                                         | `getMBR``()`<br>Gets the minimum bounding rectangle of this geo-object.                                                                                                                                       |
    | `boolean`                                                           | `isSubElementOf``(`[`GeoObject`](../../vis/maps/core/GeoObject.md)` obj)`<br>Returns true if this GeoObject is a sub element of the provided GeoObject                                                        |
    | `abstract void`                                                     | `refreshGeometry``()`<br>Updates the geoobject's geometry.                                                                                                                                                    |
    | `void`                                                              | `setGeometry``(`[`JGeometry`](../../../../geometry/JGeometry.md)` geom)`<br>Sets the GeoObject's geometry.                                                                                                    |
    | `java.lang.Object`                                                  | `setKey``(java.lang.Object key)`<br>Sets a new key on the object.                                                                                                                                             |
    | `void`                                                              | `setLayer``(`[`Layer`](../../vis/maps/core/Layer.md)` layer)`<br>Sets the layer to be associated with this object.                                                                                            |
    | `java.util.List<`[`GeoObject`](../../vis/maps/core/GeoObject.md)`>` | `substract``(java.util.List<? extends `[`GeoObject`](../../vis/maps/core/GeoObject.md)`> objs)`<br>Returns a set of GeoObjects that represent the substraction of the provided GeoObjects from this GeoObject |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.nfe.vis.maps.core.[GeoObject](../../vis/maps/core/GeoObject.md)

      [`equals`](../../vis/maps/core/GeoObject.md)`, `[`hashCode`](../../vis/maps/core/GeoObject.md)

<!-- -->

- - ### Constructor Detail

    - #### NFEGeoObject

          public NFEGeoObject(java.lang.Object key,
                              JGeometry geom,
                              Layer layer)

      Allocates a new instance of a subclass implementation
      Parameters:
      `key` - the value that uniquely identifies to the GeoObject among other GeoObjects in the same layer

      `geom` - the GeoObject's geometry

      `layer` - the layer where the GeoObject is contained

  <!-- -->

  - ### Method Detail

    - #### getKey

          public java.lang.Object getKey()

      Description copied from interface: [`GeoObject`](../../vis/maps/core/GeoObject.md)
      Gets the key of the selected object.
      Specified by:
      [`getKey`](../../vis/maps/core/GeoObject.md) in interface [`GeoObject`](../../vis/maps/core/GeoObject.md)

      Returns:
      the key

    <!-- -->

    - #### setKey

          public java.lang.Object setKey(java.lang.Object key)

      Description copied from interface: [`GeoObject`](../../vis/maps/core/GeoObject.md)
      Sets a new key on the object.
      Specified by:
      [`setKey`](../../vis/maps/core/GeoObject.md) in interface [`GeoObject`](../../vis/maps/core/GeoObject.md)

      Parameters:
      `key` - the new key to be set.

      Returns:
      previously set key

    <!-- -->

    - #### getLayer

          public Layer getLayer()

      Description copied from interface: [`GeoObject`](../../vis/maps/core/GeoObject.md)
      Gets the associated layer for this object.
      Specified by:
      [`getLayer`](../../vis/maps/core/GeoObject.md) in interface [`GeoObject`](../../vis/maps/core/GeoObject.md)

      Returns:
      typically an Layer instance that owns this object.

    <!-- -->

    - #### setLayer

          public void setLayer(Layer layer)

      Description copied from interface: [`GeoObject`](../../vis/maps/core/GeoObject.md)
      Sets the layer to be associated with this object.
      Specified by:
      [`setLayer`](../../vis/maps/core/GeoObject.md) in interface [`GeoObject`](../../vis/maps/core/GeoObject.md)

      Parameters:
      `layer` - the Layer instance to be associated.

    <!-- -->

    - #### getDrawable

          public Drawable getDrawable(java.awt.geom.AffineTransform viewportTransform)

      Description copied from interface: [`GeoObject`](../../vis/maps/core/GeoObject.md)
      This method returns a drawable Java2D shape or point that can be directly rendered onto a device. If a non-null viewportTransform is supplied, then it is applied and result returned.
      Specified by:
      [`getDrawable`](../../vis/maps/core/GeoObject.md) in interface [`GeoObject`](../../vis/maps/core/GeoObject.md)

      Returns:
      a Drawable instance that references either a Shape or a Point2D

    <!-- -->

    - #### getMBR

          public java.awt.geom.Rectangle2D getMBR()

      Description copied from interface: [`GeoObject`](../../vis/maps/core/GeoObject.md)
      Gets the minimum bounding rectangle of this geo-object. The rectangle is in the same coordinate system as the object value.
      Specified by:
      [`getMBR`](../../vis/maps/core/GeoObject.md) in interface [`GeoObject`](../../vis/maps/core/GeoObject.md)

    <!-- -->

    - #### isSubElementOf

          public boolean isSubElementOf(GeoObject obj)

      Description copied from interface: [`GeoObject`](../../vis/maps/core/GeoObject.md)
      Returns true if this GeoObject is a sub element of the provided GeoObject
      Specified by:

      [`isSubElementOf`](../../vis/maps/core/GeoObject.md) in interface [`GeoObject`](../../vis/maps/core/GeoObject.md)

      Returns:

    <!-- -->

    - #### substract

          public java.util.List<GeoObject> substract(java.util.List<? extends GeoObject> objs)

      Description copied from interface: [`GeoObject`](../../vis/maps/core/GeoObject.md)
      Returns a set of GeoObjects that represent the substraction of the provided GeoObjects from this GeoObject
      Specified by:

      [`substract`](../../vis/maps/core/GeoObject.md) in interface [`GeoObject`](../../vis/maps/core/GeoObject.md)

      Returns:

    <!-- -->

    - #### setGeometry

          public void setGeometry(JGeometry geom)

      Sets the GeoObject's geometry. Null values are not allowed
      Parameters:
      `geom` - a geometry object

    <!-- -->

    - #### getGeometry

          public JGeometry getGeometry()

      Gets the GeoObject's geometry
      Returns:
      a geometry object

    <!-- -->

    - #### refreshGeometry

          public abstract void refreshGeometry()

      Updates the geoobject's geometry. Do not call this method directly if the geometry is spatial-indexed

Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFEFeatureElementGeoObject.md)
- [Next Class](NFENetworkElementGeoObject.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

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
