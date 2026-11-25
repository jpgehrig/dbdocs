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

- [Prev Class](NFEGeoObject.md)
- [Next Class](NFERTreeSpatialModel.md)

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

## Class NFENetworkElementGeoObject

- java.lang.Object

- - [oracle.spatial.network.nfe.model.spatial.NFEGeoObject](NFEGeoObject.md)

  - - oracle.spatial.network.nfe.model.spatial.NFENetworkElementGeoObject

<!-- -->

- All Implemented Interfaces:
  java.lang.Cloneable, [GeoObject](../../vis/maps/core/GeoObject.md)

  ------------------------------------------------------------------------



      public class NFENetworkElementGeoObject
      extends NFEGeoObject

  A GeoObject representation of a network element. It holds a reference to a network element.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                   |
    |-----------------------------------------------------------------------------------------------------------------------------------------------|
    | `NFENetworkElementGeoObject``(`[`NFENetworkElement`](../network/NFENetworkElement.md)` netElem)`<br>Allocates a new network element GeoObject |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                      | Method and Description                                                  |
    |--------------------------------------------------------|-------------------------------------------------------------------------|
    | [`NFENetworkElement`](../network/NFENetworkElement.md) | `getNetworkElement``()`<br>Gets the GeoObject's network element         |
    | `boolean`                                              | `isLink``()`<br>Tells whether the GeoObject's network element is a link |
    | `boolean`                                              | `isNode``()`<br>Tells whether the GeoObject's network element is a node |
    | `void`                                                 | `refreshGeometry``()`<br>Updates the geoobject's geometry.              |

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

    - #### NFENetworkElementGeoObject

          public NFENetworkElementGeoObject(NFENetworkElement netElem)

      Allocates a new network element GeoObject
      Parameters:
      `netElem` - the GeoObject's network element

  <!-- -->

  - ### Method Detail

    - #### refreshGeometry

          public void refreshGeometry()

      Description copied from class: [`NFEGeoObject`](NFEGeoObject.md)
      Updates the geoobject's geometry. Do not call this method directly if the geometry is spatial-indexed
      Specified by:
      [`refreshGeometry`](NFEGeoObject.md) in class [`NFEGeoObject`](NFEGeoObject.md)

    <!-- -->

    - #### getNetworkElement

          public NFENetworkElement getNetworkElement()

      Gets the GeoObject's network element
      Returns:
      a network element object

    <!-- -->

    - #### isLink

          public boolean isLink()

      Tells whether the GeoObject's network element is a link
      Returns:
      true if the network element is a link

    <!-- -->

    - #### isNode

          public boolean isNode()

      Tells whether the GeoObject's network element is a node
      Returns:
      true if the network element is a node

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

- [Prev Class](NFEGeoObject.md)
- [Next Class](NFERTreeSpatialModel.md)

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
