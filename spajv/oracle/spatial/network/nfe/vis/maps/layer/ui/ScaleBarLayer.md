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

- [Prev Class](ProgressIndicatorLayer.md)
- [Next Class](ShapeDrawingLayer.md)

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

## Class ScaleBarLayer

- java.lang.Object

- - [oracle.spatial.network.nfe.vis.maps.layer.BasicLayer](../BasicLayer.md)

  - - oracle.spatial.network.nfe.vis.maps.layer.ui.ScaleBarLayer

<!-- -->

- All Implemented Interfaces:
  [Layer](../../core/Layer.md)

  ------------------------------------------------------------------------



      public class ScaleBarLayer
      extends BasicLayer

  A background layer that sits at the bottom of layer stack, and intercepts primarily mouse wheel zooming and mouse panning events.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](../../core/Layer.md)

      [`PROPERTY_NAME`](../../core/Layer.md)`, `[`PROPERTY_PROVIDERID`](../../core/Layer.md)`, `[`PROPERTY_SRID`](../../core/Layer.md)`, `[`PROPERTY_VISIBLE`](../../core/Layer.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                         |
    |---------------------------------------------------------------------|
    | `ScaleBarLayer``(`[`MapCanvas`](../../core/MapCanvas.md)` parent)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                                                                     |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`         | `handleEvent``(java.util.EventObject evt)`<br>The main method that performs event handling for this tool.                                                                                  |
    | `void`            | `mapRegionChanged``(`[`MapRegionEvent`](../../core/MapRegionEvent.md)` e)`<br>When the associated canvas's map region is changed, this method is called to notify the layer of the change. |
    | `long`            | `render``(java.awt.Graphics2D g)`<br>Renders the layer contents to the given Graphics.                                                                                                     |
    | `void`            | `setVisible``(boolean v)`<br>Sets the visibility of this layer.                                                                                                                            |

    - ### Methods inherited from class oracle.spatial.network.nfe.vis.maps.layer.[BasicLayer](../BasicLayer.md)

      [`added`](../BasicLayer.md)`, `[`addPropertyChangeListener`](../BasicLayer.md)`, `[`addPropertyChangeListener`](../BasicLayer.md)`, `[`clear`](../BasicLayer.md)`, `[`fromXMLElement`](../BasicLayer.md)`, `[`getCanvas`](../BasicLayer.md)`, `[`getDataMBR`](../BasicLayer.md)`, `[`getFullExtent`](../BasicLayer.md)`, `[`getIcon`](../BasicLayer.md)`, `[`getName`](../BasicLayer.md)`, `[`getProperties`](../BasicLayer.md)`, `[`getProperty`](../BasicLayer.md)`, `[`getProperty`](../BasicLayer.md)`, `[`getPropertyChangeListeners`](../BasicLayer.md)`, `[`getPropertyChangeListeners`](../BasicLayer.md)`, `[`getProviderID`](../BasicLayer.md)`, `[`getSRID`](../BasicLayer.md)`, `[`hitTest`](../BasicLayer.md)`, `[`hitTest`](../BasicLayer.md)`, `[`isVisible`](../BasicLayer.md)`, `[`removed`](../BasicLayer.md)`, `[`removePropertyChangeListener`](../BasicLayer.md)`, `[`removePropertyChangeListener`](../BasicLayer.md)`, `[`repaint`](../BasicLayer.md)`, `[`setCanvas`](../BasicLayer.md)`, `[`setName`](../BasicLayer.md)`, `[`setProperty`](../BasicLayer.md)`, `[`setProviderID`](../BasicLayer.md)`, `[`setSRID`](../BasicLayer.md)`, `[`toXMLElement`](../BasicLayer.md)`, `[`update`](../BasicLayer.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### ScaleBarLayer

          public ScaleBarLayer(MapCanvas parent)

  <!-- -->

  - ### Method Detail

    - #### handleEvent

          public boolean handleEvent(java.util.EventObject evt)

      Description copied from interface: [`Layer`](../../core/Layer.md)
      The main method that performs event handling for this tool. Returns whether the event should be propagated to other layers down stream (further down the layer stack) after the event has been handled.
      Specified by:
      [`handleEvent`](../../core/Layer.md) in interface [`Layer`](../../core/Layer.md)

      Overrides:
      [`handleEvent`](../BasicLayer.md) in class [`BasicLayer`](../BasicLayer.md)

    <!-- -->

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

    - #### setVisible

          public void setVisible(boolean v)

      Description copied from interface: [`Layer`](../../core/Layer.md)
      Sets the visibility of this layer.
      Specified by:
      [`setVisible`](../../core/Layer.md) in interface [`Layer`](../../core/Layer.md)

      Overrides:
      [`setVisible`](../BasicLayer.md) in class [`BasicLayer`](../BasicLayer.md)

    <!-- -->

    - #### mapRegionChanged

          public void mapRegionChanged(MapRegionEvent e)

      Description copied from interface: [`Layer`](../../core/Layer.md)
      When the associated canvas's map region is changed, this method is called to notify the layer of the change. Note that either a device window change (as a result of resizing the application window) or a data window change can cause this method to be invoked. Query the canvas' MapRegion object to get the changed values. Inside a mapRegionChanged() implementation, the layer typically needs to update its data contents accordingly.
      Specified by:
      [`mapRegionChanged`](../../core/Layer.md) in interface [`Layer`](../../core/Layer.md)

      Overrides:
      [`mapRegionChanged`](../BasicLayer.md) in class [`BasicLayer`](../BasicLayer.md)

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

- [Prev Class](ProgressIndicatorLayer.md)
- [Next Class](ShapeDrawingLayer.md)

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
