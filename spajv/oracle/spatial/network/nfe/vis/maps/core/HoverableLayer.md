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

- [Prev Class](GeoObjectLayer.md)
- [Next Class](HoverManager.md)

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

## Interface HoverableLayer

- All Superinterfaces:
  [GeoObjectLayer](GeoObjectLayer.md), [Layer](Layer.md)

  <!-- -->

  All Known Implementing Classes:
  [AbstractDataSetLayer](../layer/AbstractDataSetLayer.md), [NFEFeatureLayerRenderer](../../mapcanvas/render/NFEFeatureLayerRenderer.md), [NFEManipulableFeatureLayerRenderer](../../mapcanvas/render/NFEManipulableFeatureLayerRenderer.md), [NFENetworkRenderer](../../mapcanvas/render/NFENetworkRenderer.md), [NFEPathRenderer](../../mapcanvas/render/NFEPathRenderer.md), [NFERenderer](../../mapcanvas/render/NFERenderer.md)

  ------------------------------------------------------------------------



      public interface HoverableLayer
      extends GeoObjectLayer

  An interface for layers that have objects that can be hovered over

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](Layer.md)

      [`PROPERTY_NAME`](Layer.md)`, `[`PROPERTY_PROVIDERID`](Layer.md)`, `[`PROPERTY_SRID`](Layer.md)`, `[`PROPERTY_VISIBLE`](Layer.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                               | Method and Description                                                                                  |
    |-------------------------------------------------|---------------------------------------------------------------------------------------------------------|
    | `boolean`                                       | `clearHover``()`<br>Removes the hovering state from all the geo-objects                                 |
    | `java.util.List<`[`GeoObject`](GeoObject.md)`>` | `getHover``()`<br>Returns all the geo-object that are being hovered                                     |
    | `boolean`                                       | `isHover``(`[`GeoObject`](GeoObject.md)` obj)`<br>Returns true if the geo-object is being hovered       |
    | `int`                                           | `numHovered``()`<br>Returns the number of geo-objects that are being hovered                            |
    | `boolean`                                       | `setHover``(java.util.List<`[`GeoObject`](GeoObject.md)`> objs)`<br>A list of geo-objects being hovered |

    - ### Methods inherited from interface oracle.spatial.network.nfe.vis.maps.core.[GeoObjectLayer](GeoObjectLayer.md)

      [`getObject`](GeoObjectLayer.md)`, `[`getObjects`](GeoObjectLayer.md)

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](Layer.md)

      [`added`](Layer.md)`, `[`clear`](Layer.md)`, `[`fromXMLElement`](Layer.md)`, `[`getCanvas`](Layer.md)`, `[`getDataMBR`](Layer.md)`, `[`getFullExtent`](Layer.md)`, `[`getIcon`](Layer.md)`, `[`getName`](Layer.md)`, `[`getProviderID`](Layer.md)`, `[`getSRID`](Layer.md)`, `[`handleEvent`](Layer.md)`, `[`hitTest`](Layer.md)`, `[`hitTest`](Layer.md)`, `[`isVisible`](Layer.md)`, `[`mapRegionChanged`](Layer.md)`, `[`removed`](Layer.md)`, `[`render`](Layer.md)`, `[`repaint`](Layer.md)`, `[`setCanvas`](Layer.md)`, `[`setName`](Layer.md)`, `[`setProviderID`](Layer.md)`, `[`setSRID`](Layer.md)`, `[`setVisible`](Layer.md)`, `[`toXMLElement`](Layer.md)`, `[`update`](Layer.md)

<!-- -->

- - ### Method Detail

    - #### setHover

          boolean setHover(java.util.List<GeoObject> objs)

      A list of geo-objects being hovered
      Parameters:
      `objs` -

      Returns:
      true if the objects were hovered

    <!-- -->

    - #### clearHover

          boolean clearHover()

      Removes the hovering state from all the geo-objects
      Returns:

    <!-- -->

    - #### getHover

          java.util.List<GeoObject> getHover()

      Returns all the geo-object that are being hovered
      Returns:

    <!-- -->

    - #### isHover

          boolean isHover(GeoObject obj)

      Returns true if the geo-object is being hovered
      Parameters:

      `obj` -

      Returns:

    <!-- -->

    - #### numHovered

          int numHovered()

      Returns the number of geo-objects that are being hovered
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

- [Prev Class](GeoObjectLayer.md)
- [Next Class](HoverManager.md)

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
