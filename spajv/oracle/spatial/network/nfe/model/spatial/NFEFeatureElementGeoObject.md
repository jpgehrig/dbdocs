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

- [Prev Class](IndexedSpatialSet.md)
- [Next Class](NFEGeoObject.md)

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

## Class NFEFeatureElementGeoObject

- java.lang.Object

- - [oracle.spatial.network.nfe.model.spatial.NFEGeoObject](NFEGeoObject.md)

  - - oracle.spatial.network.nfe.model.spatial.NFEFeatureElementGeoObject

<!-- -->

- All Implemented Interfaces:
  java.lang.Cloneable, [GeoObject](../../vis/maps/core/GeoObject.md)

  ------------------------------------------------------------------------



      public class NFEFeatureElementGeoObject
      extends NFEGeoObject

  A GeoObject representation of a feature element.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                    |
    |------------------------------------------------------------------------------------------------------------------------------------------------|
    | `NFEFeatureElementGeoObject``(`[`NFEFeatureElement`](../feature/NFEFeatureElement.md)` featElem)`<br>Allocates a new feature element GeoObject |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                      | Method and Description                                                              |
    |--------------------------------------------------------|-------------------------------------------------------------------------------------|
    | [`NFEFeatureElement`](../feature/NFEFeatureElement.md) | `getFeatureElement``()`<br>Gets the GeoObject feature element                       |
    | `boolean`                                              | `isLine``()`<br>Tells whether the type of the feature element is a line             |
    | `boolean`                                              | `isPOL``()`<br>Tells whether the type of the feature element is POL (point on link) |
    | `boolean`                                              | `isPON``()`<br>Tells whether the type of the feature element is PON (point on node) |
    | `void`                                                 | `refreshGeometry``()`<br>Updates the geoobject's geometry.                          |

    - ### Methods inherited from class oracle.spatial.network.nfe.model.spatial.[NFEGeoObject](NFEGeoObject.md)

      [`getDrawable`](NFEGeoObject.md)`, `[`getGeometry`](NFEGeoObject.md)`, `[`getKey`](NFEGeoObject.md)`, `[`getLayer`](NFEGeoObject.md)`, `[`getMBR`](NFEGeoObject.md)`, `[`isSubElementOf`](NFEGeoObject.md)`, `[`setGeometry`](NFEGeoObject.md)`, `[`setKey`](NFEGeoObject.md)`, `[`setLayer`](NFEGeoObject.md)`, `[`substract`](NFEGeoObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.nfe.vis.maps.core.[GeoObject](../../vis/maps/core/GeoObject.md)

      [`equals`](../../vis/maps/core/GeoObject.md)`, `[`hashCode`](../../vis/maps/core/GeoObject.md)

<!-- -->

- - ### Constructor Detail

    - #### NFEFeatureElementGeoObject

          public NFEFeatureElementGeoObject(NFEFeatureElement featElem)

      Allocates a new feature element GeoObject
      Parameters:
      `featElem` - the GeoObject's feature element

  <!-- -->

  - ### Method Detail

    - #### refreshGeometry

          public void refreshGeometry()

      Description copied from class: [`NFEGeoObject`](NFEGeoObject.md)
      Updates the geoobject's geometry. Do not call this method directly if the geometry is spatial-indexed
      Specified by:
      [`refreshGeometry`](NFEGeoObject.md) in class [`NFEGeoObject`](NFEGeoObject.md)

    <!-- -->

    - #### getFeatureElement

          public NFEFeatureElement getFeatureElement()

      Gets the GeoObject feature element
      Returns:
      a feature element object

    <!-- -->

    - #### isPON

          public boolean isPON()

      Tells whether the type of the feature element is PON (point on node)
      Returns:
      true if the feature element is a PON

    <!-- -->

    - #### isPOL

          public boolean isPOL()

      Tells whether the type of the feature element is POL (point on link)
      Returns:
      true if the feature element is a POL

    <!-- -->

    - #### isLine

          public boolean isLine()

      Tells whether the type of the feature element is a line
      Returns:
      true if the feature element is a line

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

- [Prev Class](IndexedSpatialSet.md)
- [Next Class](NFEGeoObject.md)

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
