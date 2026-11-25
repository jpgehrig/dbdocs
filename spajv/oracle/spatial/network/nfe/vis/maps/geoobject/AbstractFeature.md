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

- Prev Class
- [Next Class](GeometryFeature.md)

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

## Class AbstractFeature

- java.lang.Object

- - oracle.spatial.network.nfe.vis.maps.geoobject.AbstractFeature

<!-- -->

- All Implemented Interfaces:
  java.lang.Cloneable, [GeoObject](../core/GeoObject.md)

  <!-- -->

  Direct Known Subclasses:
  [GeometryFeature](GeometryFeature.md)

  ------------------------------------------------------------------------



      public abstract class AbstractFeature
      extends java.lang.Object
      implements GeoObject

  Defines an abstract class that represents a geospatial feature. A feature is defined by a spatial attribute and a set of non-complex (and non-spatial) attributes. Each spatial type, must extend this abstract class. Examples of features include geometry feature, annotation text feature, and topology feature.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `AbstractFeature``()`       |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                    | Method and Description                                                                                                  |
    |--------------------------------------|-------------------------------------------------------------------------------------------------------------------------|
    | `AbstractFeature`                    | `clone``()`<br>A shallow clone                                                                                          |
    | `AbstractFeature`                    | `deepClone``()`<br>A deep clone (except the layer reference)                                                            |
    | `boolean`                            | `equals``(java.lang.Object obj)`                                                                                        |
    | `Field`                              | `getAttribute``(java.lang.String attrName)`                                                                             |
    | `java.util.Set<java.lang.String>`    | `getAttributeNames``()`<br>return the set of attribute names.                                                           |
    | `Field[]`                            | `getAttributes``()`                                                                                                     |
    | `Field[]`                            | `getAttributes``(java.lang.String[] names)`<br>Returns the field values for attribute names.                            |
    | `java.lang.Object`                   | `getKey``()`<br>Gets the key of the selected object.                                                                    |
    | [`Layer`](../core/Layer.md)          | `getLayer``()`<br>Gets the associated layer for this object.                                                            |
    | `abstract java.awt.geom.Rectangle2D` | `getMBR``()`<br>Returns the minimum bounding rectangle of the spatial attribute.                                        |
    | `java.lang.Object`                   | `getSpatialAttribute``()`<br>Returns the spatial attribute object.                                                      |
    | `abstract java.lang.Object`          | `getSpatialAttributeClone``()`<br>Returns a clone of the spatial attribute                                              |
    | `abstract int`                       | `getSpatialDimension``()`<br>Returns the feature spatial dimension.                                                     |
    | `abstract java.awt.geom.Point2D[]`   | `getSpatialJavaPoints``()`<br>Returns an array of java points representing the vertexes location of the spatial object. |
    | `boolean`                            | `removeAttribute``(java.lang.String attrName)`                                                                          |
    | `boolean`                            | `setAttribute``(java.lang.String attrName, Field value)`                                                                |
    | `void`                               | `setAttributes``(Field[] fields)`<br>Sets the field attributes.                                                         |
    | `java.lang.Object`                   | `setKey``(java.lang.Object key)`<br>Sets a new key on the object.                                                       |
    | `void`                               | `setLayer``(`[`Layer`](../core/Layer.md)` layer)`<br>Sets the layer to be associated with this object.                  |
    | `void`                               | `setSpatialAttribute``(java.lang.Object spatialAttr)`<br>Sets the spatial attribute object                              |

    - ### Methods inherited from class java.lang.Object

      `getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.nfe.vis.maps.core.[GeoObject](../core/GeoObject.md)

      [`getDrawable`](../core/GeoObject.md)`, `[`hashCode`](../core/GeoObject.md)`, `[`isSubElementOf`](../core/GeoObject.md)`, `[`substract`](../core/GeoObject.md)

<!-- -->

- - ### Constructor Detail

    - #### AbstractFeature

          public AbstractFeature()

  <!-- -->

  - ### Method Detail

    - #### clone

          public AbstractFeature clone()

      A shallow clone
      Overrides:

      `clone` in class `java.lang.Object`

      Returns:

    <!-- -->

    - #### deepClone

          public AbstractFeature deepClone()

      A deep clone (except the layer reference)

    <!-- -->

    - #### equals

          public boolean equals(java.lang.Object obj)

      Specified by:
      [`equals`](../core/GeoObject.md) in interface [`GeoObject`](../core/GeoObject.md)

      Overrides:
      `equals` in class `java.lang.Object`

    <!-- -->

    - #### getAttribute

          public Field getAttribute(java.lang.String attrName)

      Parameters:

      `attrName` -

      Returns:

    <!-- -->

    - #### getAttributeNames

          public java.util.Set<java.lang.String> getAttributeNames()

      return the set of attribute names.

    <!-- -->

    - #### setAttribute

          public boolean setAttribute(java.lang.String attrName,
                                      Field value)

      Parameters:

      `attrName` -

      `value` -

      Returns:

    <!-- -->

    - #### removeAttribute

          public boolean removeAttribute(java.lang.String attrName)

      Parameters:

      `attrName` -

      Returns:

    <!-- -->

    - #### getKey

          public java.lang.Object getKey()

      Description copied from interface: [`GeoObject`](../core/GeoObject.md)
      Gets the key of the selected object.
      Specified by:
      [`getKey`](../core/GeoObject.md) in interface [`GeoObject`](../core/GeoObject.md)

      Returns:
      the key

    <!-- -->

    - #### setKey

          public java.lang.Object setKey(java.lang.Object key)

      Description copied from interface: [`GeoObject`](../core/GeoObject.md)
      Sets a new key on the object.
      Specified by:
      [`setKey`](../core/GeoObject.md) in interface [`GeoObject`](../core/GeoObject.md)

      Parameters:
      `key` - the new key to be set.

      Returns:
      previously set key

    <!-- -->

    - #### getAttributes

          public Field[] getAttributes()

      Returns:

    <!-- -->

    - #### getAttributes

          public Field[] getAttributes(java.lang.String[] names)

      Returns the field values for attribute names.
      Parameters:

      `names` - attributes

      Returns:

    <!-- -->

    - #### setAttributes

          public void setAttributes(Field[] fields)

      Sets the field attributes. The current attribute list is not erased, and new field names are added to the attribute list, while existing names are updated.
      Parameters:
      `fields` -

    <!-- -->

    - #### getLayer

          public Layer getLayer()

      Description copied from interface: [`GeoObject`](../core/GeoObject.md)
      Gets the associated layer for this object.
      Specified by:
      [`getLayer`](../core/GeoObject.md) in interface [`GeoObject`](../core/GeoObject.md)

      Returns:
      typically an Layer instance that owns this object.

    <!-- -->

    - #### setLayer

          public void setLayer(Layer layer)

      Description copied from interface: [`GeoObject`](../core/GeoObject.md)
      Sets the layer to be associated with this object.
      Specified by:
      [`setLayer`](../core/GeoObject.md) in interface [`GeoObject`](../core/GeoObject.md)

      Parameters:
      `layer` - the Layer instance to be associated.

    <!-- -->

    - #### getSpatialAttribute

          public java.lang.Object getSpatialAttribute()

      Returns the spatial attribute object.
      Returns:

    <!-- -->

    - #### setSpatialAttribute

          public void setSpatialAttribute(java.lang.Object spatialAttr)

      Sets the spatial attribute object
      Parameters:
      `spatialAttr` -

    <!-- -->

    - #### getSpatialAttributeClone

          public abstract java.lang.Object getSpatialAttributeClone()

      Returns a clone of the spatial attribute
      Returns:

    <!-- -->

    - #### getMBR

          public abstract java.awt.geom.Rectangle2D getMBR()

      Returns the minimum bounding rectangle of the spatial attribute.
      Specified by:

      [`getMBR`](../core/GeoObject.md) in interface [`GeoObject`](../core/GeoObject.md)

      Returns:

    <!-- -->

    - #### getSpatialDimension

          public abstract int getSpatialDimension()

      Returns the feature spatial dimension.
      Returns:

    <!-- -->

    - #### getSpatialJavaPoints

          public abstract java.awt.geom.Point2D[] getSpatialJavaPoints()

      Returns an array of java points representing the vertexes location of the spatial object.
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

- Prev Class
- [Next Class](GeometryFeature.md)

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
