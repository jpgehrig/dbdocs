Skip navigation links

- [Overview](../../../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../../../deprecated-list.md)
- [Index](../../../../../../../../index-all.md)
- [Help](../../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](MapNavLayer.md)
- [Next Class](ProgressIndicatorLayer.md)

<!-- -->

- [Frames](../../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.vis.maps.layer.ui

## Class PointerLocationLayer

- java.lang.Object

- - [oracle.spatial.network.nfe.vis.maps.layer.BasicLayer](../BasicLayer.md)

  - - oracle.spatial.network.nfe.vis.maps.layer.ui.PointerLocationLayer

<!-- -->

- All Implemented Interfaces:
  [Layer](../../core/Layer.md)

  ------------------------------------------------------------------------



      public class PointerLocationLayer
      extends BasicLayer

  This layer displays helpful information related to the current mouse cursor, such as the ground coordinates.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](../../core/Layer.md)

      [`PROPERTY_NAME`](../../core/Layer.md)`, `[`PROPERTY_PROVIDERID`](../../core/Layer.md)`, `[`PROPERTY_SRID`](../../core/Layer.md)`, `[`PROPERTY_VISIBLE`](../../core/Layer.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                |
    |----------------------------------------------------------------------------|
    | `PointerLocationLayer``(`[`MapCanvas`](../../core/MapCanvas.md)` canvas)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                 |
    |-------------------|----------------------------------------------------------------------------------------|
    | `void`            | `handleTheEvent``(java.util.EventObject evt)`                                          |
    | `boolean`         | `isMyEvent``(java.util.EventObject evt)`<br>This layer always returns false            |
    | `boolean`         | `propagateEvent``(java.util.EventObject evt)`                                          |
    | `long`            | `render``(java.awt.Graphics2D g)`<br>Renders the layer contents to the given Graphics. |

    - ### Methods inherited from class oracle.spatial.network.nfe.vis.maps.layer.[BasicLayer](../BasicLayer.md)

      [`added`](../BasicLayer.md)`, `[`addPropertyChangeListener`](../BasicLayer.md)`, `[`addPropertyChangeListener`](../BasicLayer.md)`, `[`clear`](../BasicLayer.md)`, `[`fromXMLElement`](../BasicLayer.md)`, `[`getCanvas`](../BasicLayer.md)`, `[`getDataMBR`](../BasicLayer.md)`, `[`getFullExtent`](../BasicLayer.md)`, `[`getIcon`](../BasicLayer.md)`, `[`getName`](../BasicLayer.md)`, `[`getProperties`](../BasicLayer.md)`, `[`getProperty`](../BasicLayer.md)`, `[`getProperty`](../BasicLayer.md)`, `[`getPropertyChangeListeners`](../BasicLayer.md)`, `[`getPropertyChangeListeners`](../BasicLayer.md)`, `[`getProviderID`](../BasicLayer.md)`, `[`getSRID`](../BasicLayer.md)`, `[`handleEvent`](../BasicLayer.md)`, `[`hitTest`](../BasicLayer.md)`, `[`hitTest`](../BasicLayer.md)`, `[`isVisible`](../BasicLayer.md)`, `[`mapRegionChanged`](../BasicLayer.md)`, `[`removed`](../BasicLayer.md)`, `[`removePropertyChangeListener`](../BasicLayer.md)`, `[`removePropertyChangeListener`](../BasicLayer.md)`, `[`repaint`](../BasicLayer.md)`, `[`setCanvas`](../BasicLayer.md)`, `[`setName`](../BasicLayer.md)`, `[`setProperty`](../BasicLayer.md)`, `[`setProviderID`](../BasicLayer.md)`, `[`setSRID`](../BasicLayer.md)`, `[`setVisible`](../BasicLayer.md)`, `[`toXMLElement`](../BasicLayer.md)`, `[`update`](../BasicLayer.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### PointerLocationLayer

          public PointerLocationLayer(MapCanvas canvas)

  <!-- -->

  - ### Method Detail

    - #### render

          public long render(java.awt.Graphics2D g)

      Description copied from interface: [`Layer`](../../core/Layer.md)
      Renders the layer contents to the given Graphics.
      Specified by:
      [`render`](../../core/Layer.md) in interface [`Layer`](../../core/Layer.md)

      Overrides:
      [`render`](../BasicLayer.md) in class [`BasicLayer`](../BasicLayer.md)

      Parameters:
      `g` - the graphics object

      Returns:
      the rendering time in milliseconds.

    <!-- -->

    - #### isMyEvent

          public boolean isMyEvent(java.util.EventObject evt)

      This layer always returns false
      Parameters:

      `evt` -

      Returns:

    <!-- -->

    - #### propagateEvent

          public boolean propagateEvent(java.util.EventObject evt)

    <!-- -->

    - #### handleTheEvent

          public void handleTheEvent(java.util.EventObject evt)

Skip navigation links

- [Overview](../../../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../../../deprecated-list.md)
- [Index](../../../../../../../../index-all.md)
- [Help](../../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](MapNavLayer.md)
- [Next Class](ProgressIndicatorLayer.md)

<!-- -->

- [Frames](../../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../../allclasses-noframe.md)

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
