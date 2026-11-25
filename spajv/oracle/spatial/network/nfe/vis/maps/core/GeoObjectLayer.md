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

- [Prev Class](GeoObject.md)
- [Next Class](HoverableLayer.md)

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

## Interface GeoObjectLayer

- All Superinterfaces:
  [Layer](Layer.md)

  <!-- -->

  All Known Subinterfaces:
  [EditableLayer](EditableLayer.md), [HoverableLayer](HoverableLayer.md), [SelectableLayer](SelectableLayer.md)

  <!-- -->

  All Known Implementing Classes:
  [AbstractDataSetLayer](../layer/AbstractDataSetLayer.md), [NFEFeatureLayerRenderer](../../mapcanvas/render/NFEFeatureLayerRenderer.md), [NFEManipulableFeatureLayerRenderer](../../mapcanvas/render/NFEManipulableFeatureLayerRenderer.md), [NFENetworkRenderer](../../mapcanvas/render/NFENetworkRenderer.md), [NFEPathRenderer](../../mapcanvas/render/NFEPathRenderer.md), [NFERenderer](../../mapcanvas/render/NFERenderer.md)

  ------------------------------------------------------------------------



      public interface GeoObjectLayer
      extends Layer

  A layer to keep track of a group of GeoObjects

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](Layer.md)

      [`PROPERTY_NAME`](Layer.md)`, `[`PROPERTY_PROVIDERID`](Layer.md)`, `[`PROPERTY_SRID`](Layer.md)`, `[`PROPERTY_VISIBLE`](Layer.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type               | Method and Description                                                                      |
    |---------------------------------|---------------------------------------------------------------------------------------------|
    | [`GeoObject`](GeoObject.md)     | `getObject``(java.lang.Object key)`<br>Gets the GeoObject corresponding to the provided key |
    | [`GeoObject`](GeoObject.md)`[]` | `getObjects``()`<br>Gets all GeoObjects in this layer                                       |

    - ### Methods inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](Layer.md)

      [`added`](Layer.md)`, `[`clear`](Layer.md)`, `[`fromXMLElement`](Layer.md)`, `[`getCanvas`](Layer.md)`, `[`getDataMBR`](Layer.md)`, `[`getFullExtent`](Layer.md)`, `[`getIcon`](Layer.md)`, `[`getName`](Layer.md)`, `[`getProviderID`](Layer.md)`, `[`getSRID`](Layer.md)`, `[`handleEvent`](Layer.md)`, `[`hitTest`](Layer.md)`, `[`hitTest`](Layer.md)`, `[`isVisible`](Layer.md)`, `[`mapRegionChanged`](Layer.md)`, `[`removed`](Layer.md)`, `[`render`](Layer.md)`, `[`repaint`](Layer.md)`, `[`setCanvas`](Layer.md)`, `[`setName`](Layer.md)`, `[`setProviderID`](Layer.md)`, `[`setSRID`](Layer.md)`, `[`setVisible`](Layer.md)`, `[`toXMLElement`](Layer.md)`, `[`update`](Layer.md)

<!-- -->

- - ### Method Detail

    - #### getObjects

          GeoObject[] getObjects()

      Gets all GeoObjects in this layer
      Returns:

    <!-- -->

    - #### getObject

          GeoObject getObject(java.lang.Object key)

      Gets the GeoObject corresponding to the provided key
      Parameters:

      `key` -

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

- [Prev Class](GeoObject.md)
- [Next Class](HoverableLayer.md)

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
