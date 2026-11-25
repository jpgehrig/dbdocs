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

- Prev Class
- [Next Class](PointerLocationLayer.md)

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

## Class MapNavLayer

- java.lang.Object

- - [oracle.spatial.network.nfe.vis.maps.layer.BasicLayer](../BasicLayer.md)

  - - oracle.spatial.network.nfe.vis.maps.layer.ui.MapNavLayer

<!-- -->

- All Implemented Interfaces:
  java.beans.PropertyChangeListener, java.util.EventListener, javax.swing.event.ChangeListener, [Layer](../../core/Layer.md), [ShapeDrawingLayer](ShapeDrawingLayer.md)

  ------------------------------------------------------------------------



      public class MapNavLayer
      extends BasicLayer
      implements ShapeDrawingLayer, javax.swing.event.ChangeListener, java.beans.PropertyChangeListener

  MapNavLayer renders and handles the events for the Navigation Panel that includes a panning dial, zoom buttons, and if a tile layer is present, a zoom slider

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type       | Field and Description   |
    |-------------------------|-------------------------|
    | `static float`          | `BKGND_ALPHA`           |
    | `static float`          | `BORDER_ALPHA`          |
    | `static java.awt.Color` | `ENABLED_BLUE`          |
    | `static java.awt.Color` | `MOUSEOVER_BLUE`        |
    | `static int`            | `PAN_DELTA`             |
    | `static float`          | `ZOOMBOX_BKGND_ALPHA`   |
    | `static float`          | `ZOOMBOX_BORDER_ALPHA`  |

    - ### Fields inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](../../core/Layer.md)

      [`PROPERTY_NAME`](../../core/Layer.md)`, `[`PROPERTY_PROVIDERID`](../../core/Layer.md)`, `[`PROPERTY_SRID`](../../core/Layer.md)`, `[`PROPERTY_VISIBLE`](../../core/Layer.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                       |
    |-------------------------------------------------------------------|
    | `MapNavLayer``(`[`MapCanvas`](../../core/MapCanvas.md)` parent)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type       | Method and Description                                                                                                                                                                     |
    |-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`               | `getSliderEnabled``()`                                                                                                                                                                     |
    | `java.awt.geom.Point2D` | `getSnapPoint``(java.awt.geom.Point2D point)`<br>Gets the shape snap point closest to the given point                                                                                      |
    | `boolean`               | `handleEvent``(java.util.EventObject evt)`<br>The main method that performs event handling for this tool.                                                                                  |
    | `void`                  | `mapRegionChanged``(`[`MapRegionEvent`](../../core/MapRegionEvent.md)` e)`<br>When the associated canvas's map region is changed, this method is called to notify the layer of the change. |
    | `void`                  | `propertyChange``(java.beans.PropertyChangeEvent evt)`                                                                                                                                     |
    | `long`                  | `render``(java.awt.Graphics2D g)`<br>Renders the layer contents to the given Graphics.                                                                                                     |
    | `void`                  | `setCanvas``(`[`MapCanvas`](../../core/MapCanvas.md)` canvas)`<br>Sets the map canvas on which this layer is displayed.                                                                    |
    | `void`                  | `setNumTicks``(int numTicks)`                                                                                                                                                              |
    | `void`                  | `setShape``(java.awt.Shape zoomBox)`<br>Sets the shape to be drawn                                                                                                                         |
    | `void`                  | `setSliderEnabled``(boolean enabled)`                                                                                                                                                      |
    | `void`                  | `shapeCompleted``(java.awt.event.MouseEvent e)`<br>To be called when the shape is completely drawn                                                                                         |
    | `void`                  | `stateChanged``(javax.swing.event.ChangeEvent evt)`                                                                                                                                        |

    - ### Methods inherited from class oracle.spatial.network.nfe.vis.maps.layer.[BasicLayer](../BasicLayer.md)

      [`added`](../BasicLayer.md)`, `[`addPropertyChangeListener`](../BasicLayer.md)`, `[`addPropertyChangeListener`](../BasicLayer.md)`, `[`clear`](../BasicLayer.md)`, `[`fromXMLElement`](../BasicLayer.md)`, `[`getCanvas`](../BasicLayer.md)`, `[`getDataMBR`](../BasicLayer.md)`, `[`getFullExtent`](../BasicLayer.md)`, `[`getIcon`](../BasicLayer.md)`, `[`getName`](../BasicLayer.md)`, `[`getProperties`](../BasicLayer.md)`, `[`getProperty`](../BasicLayer.md)`, `[`getProperty`](../BasicLayer.md)`, `[`getPropertyChangeListeners`](../BasicLayer.md)`, `[`getPropertyChangeListeners`](../BasicLayer.md)`, `[`getProviderID`](../BasicLayer.md)`, `[`getSRID`](../BasicLayer.md)`, `[`hitTest`](../BasicLayer.md)`, `[`hitTest`](../BasicLayer.md)`, `[`isVisible`](../BasicLayer.md)`, `[`removed`](../BasicLayer.md)`, `[`removePropertyChangeListener`](../BasicLayer.md)`, `[`removePropertyChangeListener`](../BasicLayer.md)`, `[`repaint`](../BasicLayer.md)`, `[`setName`](../BasicLayer.md)`, `[`setProperty`](../BasicLayer.md)`, `[`setProviderID`](../BasicLayer.md)`, `[`setSRID`](../BasicLayer.md)`, `[`setVisible`](../BasicLayer.md)`, `[`toXMLElement`](../BasicLayer.md)`, `[`update`](../BasicLayer.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### BORDER_ALPHA

          public static final float BORDER_ALPHA

      See Also:
      [Constant Field Values](../../../../../../../../constant-values.md)

    <!-- -->

    - #### BKGND_ALPHA

          public static final float BKGND_ALPHA

      See Also:
      [Constant Field Values](../../../../../../../../constant-values.md)

    <!-- -->

    - #### ZOOMBOX_BORDER_ALPHA

          public static final float ZOOMBOX_BORDER_ALPHA

      See Also:
      [Constant Field Values](../../../../../../../../constant-values.md)

    <!-- -->

    - #### ZOOMBOX_BKGND_ALPHA

          public static final float ZOOMBOX_BKGND_ALPHA

      See Also:
      [Constant Field Values](../../../../../../../../constant-values.md)

    <!-- -->

    - #### ENABLED_BLUE

          public static final java.awt.Color ENABLED_BLUE

    <!-- -->

    - #### MOUSEOVER_BLUE

          public static final java.awt.Color MOUSEOVER_BLUE

    <!-- -->

    - #### PAN_DELTA

          public static final int PAN_DELTA

      See Also:
      [Constant Field Values](../../../../../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### MapNavLayer

          public MapNavLayer(MapCanvas parent)

  <!-- -->

  - ### Method Detail

    - #### setCanvas

          public void setCanvas(MapCanvas canvas)

      Description copied from interface: [`Layer`](../../core/Layer.md)
      Sets the map canvas on which this layer is displayed.
      Specified by:
      [`setCanvas`](../../core/Layer.md) in interface [`Layer`](../../core/Layer.md)

      Overrides:
      [`setCanvas`](../BasicLayer.md) in class [`BasicLayer`](../BasicLayer.md)

    <!-- -->

    - #### propertyChange

          public void propertyChange(java.beans.PropertyChangeEvent evt)

      Specified by:
      `propertyChange` in interface `java.beans.PropertyChangeListener`

    <!-- -->

    - #### stateChanged

          public void stateChanged(javax.swing.event.ChangeEvent evt)

      Specified by:
      `stateChanged` in interface `javax.swing.event.ChangeListener`

    <!-- -->

    - #### mapRegionChanged

          public void mapRegionChanged(MapRegionEvent e)

      Description copied from interface: [`Layer`](../../core/Layer.md)
      When the associated canvas's map region is changed, this method is called to notify the layer of the change. Note that either a device window change (as a result of resizing the application window) or a data window change can cause this method to be invoked. Query the canvas' MapRegion object to get the changed values. Inside a mapRegionChanged() implementation, the layer typically needs to update its data contents accordingly.
      Specified by:
      [`mapRegionChanged`](../../core/Layer.md) in interface [`Layer`](../../core/Layer.md)

      Overrides:
      [`mapRegionChanged`](../BasicLayer.md) in class [`BasicLayer`](../BasicLayer.md)

    <!-- -->

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

    - #### setShape

          public void setShape(java.awt.Shape zoomBox)

      Description copied from interface: [`ShapeDrawingLayer`](ShapeDrawingLayer.md)
      Sets the shape to be drawn
      Specified by:
      [`setShape`](ShapeDrawingLayer.md) in interface [`ShapeDrawingLayer`](ShapeDrawingLayer.md)

    <!-- -->

    - #### shapeCompleted

          public void shapeCompleted(java.awt.event.MouseEvent e)

      Description copied from interface: [`ShapeDrawingLayer`](ShapeDrawingLayer.md)
      To be called when the shape is completely drawn
      Specified by:
      [`shapeCompleted`](ShapeDrawingLayer.md) in interface [`ShapeDrawingLayer`](ShapeDrawingLayer.md)

    <!-- -->

    - #### getSnapPoint

          public java.awt.geom.Point2D getSnapPoint(java.awt.geom.Point2D point)

      Description copied from interface: [`ShapeDrawingLayer`](ShapeDrawingLayer.md)
      Gets the shape snap point closest to the given point
      Specified by:

      [`getSnapPoint`](ShapeDrawingLayer.md) in interface [`ShapeDrawingLayer`](ShapeDrawingLayer.md)

      Returns:

    <!-- -->

    - #### setSliderEnabled

          public void setSliderEnabled(boolean enabled)

    <!-- -->

    - #### getSliderEnabled

          public boolean getSliderEnabled()

    <!-- -->

    - #### setNumTicks

          public void setNumTicks(int numTicks)

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

- Prev Class
- [Next Class](PointerLocationLayer.md)

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
