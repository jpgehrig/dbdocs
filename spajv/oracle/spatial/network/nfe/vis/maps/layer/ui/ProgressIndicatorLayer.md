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

- [Prev Class](PointerLocationLayer.md)
- [Next Class](ScaleBarLayer.md)

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

## Class ProgressIndicatorLayer

- java.lang.Object

- - [oracle.spatial.network.nfe.vis.maps.layer.BasicLayer](../BasicLayer.md)

  - - oracle.spatial.network.nfe.vis.maps.layer.ui.ProgressIndicatorLayer

<!-- -->

- All Implemented Interfaces:
  [Layer](../../core/Layer.md)

  <!-- -->

  Direct Known Subclasses:
  [NFEProgressIndicatorLayer](../../../mapcanvas/render/NFEProgressIndicatorLayer.md)

  ------------------------------------------------------------------------



      public class ProgressIndicatorLayer
      extends BasicLayer

  This layer displays a (indeterminate) progress indicator in the center of the map. The default indicator is a clock with spinning hour and minute hands. Typical usage is to call the taskStarted() method when a long running task just started. When the task is either completed or aborted make sure to call the taskCompleted() method. You can call taskStarted() as many times as the number of concurrent long-running tasks. The Progress indicator layer maintains an internal count of running tasks. The spinning clock will disappear only when all long running tasks have completed (or aborted).

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](../../core/Layer.md)

      [`PROPERTY_NAME`](../../core/Layer.md)`, `[`PROPERTY_PROVIDERID`](../../core/Layer.md)`, `[`PROPERTY_SRID`](../../core/Layer.md)`, `[`PROPERTY_VISIBLE`](../../core/Layer.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                  |
    |------------------------------------------------------------------------------|
    | `ProgressIndicatorLayer``(`[`MapCanvas`](../../core/MapCanvas.md)` canvas)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                                                                     |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`         | `handleEvent``(java.util.EventObject evt)`<br>The main method that performs event handling for this tool.                                                                                  |
    | `void`            | `mapRegionChanged``(`[`MapRegionEvent`](../../core/MapRegionEvent.md)` e)`<br>When the associated canvas's map region is changed, this method is called to notify the layer of the change. |
    | `long`            | `render``(java.awt.Graphics2D g)`<br>Renders the layer contents to the given Graphics.                                                                                                     |
    | `void`            | `reset``()`<br>Resets the internal task count to zero.                                                                                                                                     |
    | `void`            | `taskCompleted``()`<br>This method should be called when a task has either completed or aborted.                                                                                           |
    | `void`            | `taskStarted``()`<br>Call this method to display a progress indicator on the map.                                                                                                          |
    | `void`            | `update``(long elapsedTime)`<br>updates the contents data model or structure.                                                                                                              |

    - ### Methods inherited from class oracle.spatial.network.nfe.vis.maps.layer.[BasicLayer](../BasicLayer.md)

      [`added`](../BasicLayer.md)`, `[`addPropertyChangeListener`](../BasicLayer.md)`, `[`addPropertyChangeListener`](../BasicLayer.md)`, `[`clear`](../BasicLayer.md)`, `[`fromXMLElement`](../BasicLayer.md)`, `[`getCanvas`](../BasicLayer.md)`, `[`getDataMBR`](../BasicLayer.md)`, `[`getFullExtent`](../BasicLayer.md)`, `[`getIcon`](../BasicLayer.md)`, `[`getName`](../BasicLayer.md)`, `[`getProperties`](../BasicLayer.md)`, `[`getProperty`](../BasicLayer.md)`, `[`getProperty`](../BasicLayer.md)`, `[`getPropertyChangeListeners`](../BasicLayer.md)`, `[`getPropertyChangeListeners`](../BasicLayer.md)`, `[`getProviderID`](../BasicLayer.md)`, `[`getSRID`](../BasicLayer.md)`, `[`hitTest`](../BasicLayer.md)`, `[`hitTest`](../BasicLayer.md)`, `[`isVisible`](../BasicLayer.md)`, `[`removed`](../BasicLayer.md)`, `[`removePropertyChangeListener`](../BasicLayer.md)`, `[`removePropertyChangeListener`](../BasicLayer.md)`, `[`repaint`](../BasicLayer.md)`, `[`setCanvas`](../BasicLayer.md)`, `[`setName`](../BasicLayer.md)`, `[`setProperty`](../BasicLayer.md)`, `[`setProviderID`](../BasicLayer.md)`, `[`setSRID`](../BasicLayer.md)`, `[`setVisible`](../BasicLayer.md)`, `[`toXMLElement`](../BasicLayer.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### ProgressIndicatorLayer

          public ProgressIndicatorLayer(MapCanvas canvas)

  <!-- -->

  - ### Method Detail

    - #### taskStarted

          public void taskStarted()

      Call this method to display a progress indicator on the map. This is typically called when a long run task has just been started. You must call the corresponding taskCompleted() when the task is either completed or aborted. Failure to do so may result in the indicator being displayed indefinitely on the map.

    <!-- -->

    - #### taskCompleted

          public void taskCompleted()

      This method should be called when a task has either completed or aborted.

    <!-- -->

    - #### update

          public void update(long elapsedTime)

      Description copied from interface: [`Layer`](../../core/Layer.md)
      updates the contents data model or structure.
      Specified by:
      [`update`](../../core/Layer.md) in interface [`Layer`](../../core/Layer.md)

      Overrides:
      [`update`](../BasicLayer.md) in class [`BasicLayer`](../BasicLayer.md)

      Parameters:
      `elapsedTime` - The elapsed time since last update.

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

    - #### mapRegionChanged

          public void mapRegionChanged(MapRegionEvent e)

      Description copied from interface: [`Layer`](../../core/Layer.md)
      When the associated canvas's map region is changed, this method is called to notify the layer of the change. Note that either a device window change (as a result of resizing the application window) or a data window change can cause this method to be invoked. Query the canvas' MapRegion object to get the changed values. Inside a mapRegionChanged() implementation, the layer typically needs to update its data contents accordingly.
      Specified by:
      [`mapRegionChanged`](../../core/Layer.md) in interface [`Layer`](../../core/Layer.md)

      Overrides:
      [`mapRegionChanged`](../BasicLayer.md) in class [`BasicLayer`](../BasicLayer.md)

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

    - #### reset

          public void reset()

      Resets the internal task count to zero. This also makes the indicator disappear (until a new call to the taskStarted method).

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

- [Prev Class](PointerLocationLayer.md)
- [Next Class](ScaleBarLayer.md)

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
