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

- [Prev Class](NFEPathRenderer.md)
- [Next Class](NFERenderer.md)

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

oracle.spatial.network.nfe.vis.mapcanvas.render

## Class NFEProgressIndicatorLayer

- java.lang.Object

- - [oracle.spatial.network.nfe.vis.maps.layer.BasicLayer](../../maps/layer/BasicLayer.md)

  - - [oracle.spatial.network.nfe.vis.maps.layer.ui.ProgressIndicatorLayer](../../maps/layer/ui/ProgressIndicatorLayer.md)

    - - oracle.spatial.network.nfe.vis.mapcanvas.render.NFEProgressIndicatorLayer

<!-- -->

- All Implemented Interfaces:
  [Layer](../../maps/core/Layer.md)

  ------------------------------------------------------------------------



      public class NFEProgressIndicatorLayer
      extends ProgressIndicatorLayer

  This layer displays a (indeterminate) progress indicator in the center of the map. Typical usage is to call the taskStarted() method when a long running task just started. When the task is either completed or aborted make sure to call the taskCompleted() method. You can call taskStarted() as many times as the number of concurrent long-running tasks. The Progress indicator layer maintains an internal count of running tasks. The spinning clock will disappear only when all long running tasks have completed (or aborted).

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](../../maps/core/Layer.md)

      [`PROPERTY_NAME`](../../maps/core/Layer.md)`, `[`PROPERTY_PROVIDERID`](../../maps/core/Layer.md)`, `[`PROPERTY_SRID`](../../maps/core/Layer.md)`, `[`PROPERTY_VISIBLE`](../../maps/core/Layer.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                          |
    |--------------------------------------------------------------------------------------|
    | `NFEProgressIndicatorLayer``(`[`MapCanvas`](../../maps/core/MapCanvas.md)` canvas)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                                                                          |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`         | `handleEvent``(java.util.EventObject evt)`<br>The main method that performs event handling for this tool.                                                                                       |
    | `void`            | `mapRegionChanged``(`[`MapRegionEvent`](../../maps/core/MapRegionEvent.md)` e)`<br>When the associated canvas's map region is changed, this method is called to notify the layer of the change. |
    | `long`            | `render``(java.awt.Graphics2D g)`<br>Renders the layer contents to the given Graphics.                                                                                                          |
    | `void`            | `reset``()`<br>Resets the internal task count to zero.                                                                                                                                          |
    | `void`            | `taskCompleted``()`<br>Call this method when the task is completed or aborted.                                                                                                                  |
    | `void`            | `taskStarted``()`<br>Call this method to display a progress indicator on the map.                                                                                                               |
    | `void`            | `update``(long elapsedTime)`<br>updates the contents data model or structure.                                                                                                                   |

    - ### Methods inherited from class oracle.spatial.network.nfe.vis.maps.layer.[BasicLayer](../../maps/layer/BasicLayer.md)

      [`added`](../../maps/layer/BasicLayer.md)`, `[`addPropertyChangeListener`](../../maps/layer/BasicLayer.md)`, `[`addPropertyChangeListener`](../../maps/layer/BasicLayer.md)`, `[`clear`](../../maps/layer/BasicLayer.md)`, `[`fromXMLElement`](../../maps/layer/BasicLayer.md)`, `[`getCanvas`](../../maps/layer/BasicLayer.md)`, `[`getDataMBR`](../../maps/layer/BasicLayer.md)`, `[`getFullExtent`](../../maps/layer/BasicLayer.md)`, `[`getIcon`](../../maps/layer/BasicLayer.md)`, `[`getName`](../../maps/layer/BasicLayer.md)`, `[`getProperties`](../../maps/layer/BasicLayer.md)`, `[`getProperty`](../../maps/layer/BasicLayer.md)`, `[`getProperty`](../../maps/layer/BasicLayer.md)`, `[`getPropertyChangeListeners`](../../maps/layer/BasicLayer.md)`, `[`getPropertyChangeListeners`](../../maps/layer/BasicLayer.md)`, `[`getProviderID`](../../maps/layer/BasicLayer.md)`, `[`getSRID`](../../maps/layer/BasicLayer.md)`, `[`hitTest`](../../maps/layer/BasicLayer.md)`, `[`hitTest`](../../maps/layer/BasicLayer.md)`, `[`isVisible`](../../maps/layer/BasicLayer.md)`, `[`removed`](../../maps/layer/BasicLayer.md)`, `[`removePropertyChangeListener`](../../maps/layer/BasicLayer.md)`, `[`removePropertyChangeListener`](../../maps/layer/BasicLayer.md)`, `[`repaint`](../../maps/layer/BasicLayer.md)`, `[`setCanvas`](../../maps/layer/BasicLayer.md)`, `[`setName`](../../maps/layer/BasicLayer.md)`, `[`setProperty`](../../maps/layer/BasicLayer.md)`, `[`setProviderID`](../../maps/layer/BasicLayer.md)`, `[`setSRID`](../../maps/layer/BasicLayer.md)`, `[`setVisible`](../../maps/layer/BasicLayer.md)`, `[`toXMLElement`](../../maps/layer/BasicLayer.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEProgressIndicatorLayer

          public NFEProgressIndicatorLayer(MapCanvas canvas)

  <!-- -->

  - ### Method Detail

    - #### taskStarted

          public void taskStarted()

      Call this method to display a progress indicator on the map. This is typically called when a long run task has just been started. You must call the corresponding taskCompleted() when the task is either completed or aborted. Failure to do so may result in the indicator being displayed indefinitely on the map.
      Overrides:
      [`taskStarted`](../../maps/layer/ui/ProgressIndicatorLayer.md) in class [`ProgressIndicatorLayer`](../../maps/layer/ui/ProgressIndicatorLayer.md)

    <!-- -->

    - #### taskCompleted

          public void taskCompleted()

      Call this method when the task is completed or aborted.
      Overrides:
      [`taskCompleted`](../../maps/layer/ui/ProgressIndicatorLayer.md) in class [`ProgressIndicatorLayer`](../../maps/layer/ui/ProgressIndicatorLayer.md)

    <!-- -->

    - #### update

          public void update(long elapsedTime)

      Description copied from interface: [`Layer`](../../maps/core/Layer.md)
      updates the contents data model or structure.
      Specified by:
      [`update`](../../maps/core/Layer.md) in interface [`Layer`](../../maps/core/Layer.md)

      Overrides:
      [`update`](../../maps/layer/ui/ProgressIndicatorLayer.md) in class [`ProgressIndicatorLayer`](../../maps/layer/ui/ProgressIndicatorLayer.md)

      Parameters:
      `elapsedTime` - The elapsed time since last update.

    <!-- -->

    - #### mapRegionChanged

          public void mapRegionChanged(MapRegionEvent e)

      Description copied from interface: [`Layer`](../../maps/core/Layer.md)
      When the associated canvas's map region is changed, this method is called to notify the layer of the change. Note that either a device window change (as a result of resizing the application window) or a data window change can cause this method to be invoked. Query the canvas' MapRegion object to get the changed values. Inside a mapRegionChanged() implementation, the layer typically needs to update its data contents accordingly.
      Specified by:
      [`mapRegionChanged`](../../maps/core/Layer.md) in interface [`Layer`](../../maps/core/Layer.md)

      Overrides:
      [`mapRegionChanged`](../../maps/layer/ui/ProgressIndicatorLayer.md) in class [`ProgressIndicatorLayer`](../../maps/layer/ui/ProgressIndicatorLayer.md)

    <!-- -->

    - #### render

          public long render(java.awt.Graphics2D g)

      Description copied from interface: [`Layer`](../../maps/core/Layer.md)
      Renders the layer contents to the given Graphics.
      Specified by:
      [`render`](../../maps/core/Layer.md) in interface [`Layer`](../../maps/core/Layer.md)

      Overrides:
      [`render`](../../maps/layer/ui/ProgressIndicatorLayer.md) in class [`ProgressIndicatorLayer`](../../maps/layer/ui/ProgressIndicatorLayer.md)

      Parameters:
      `g` - the graphics object

      Returns:
      the rendering time in milliseconds.

    <!-- -->

    - #### reset

          public void reset()

      Resets the internal task count to zero. This also makes the indicator disappear (until a new call to the taskStarted method).
      Overrides:
      [`reset`](../../maps/layer/ui/ProgressIndicatorLayer.md) in class [`ProgressIndicatorLayer`](../../maps/layer/ui/ProgressIndicatorLayer.md)

    <!-- -->

    - #### handleEvent

          public boolean handleEvent(java.util.EventObject evt)

      Description copied from interface: [`Layer`](../../maps/core/Layer.md)
      The main method that performs event handling for this tool. Returns whether the event should be propagated to other layers down stream (further down the layer stack) after the event has been handled.
      Specified by:
      [`handleEvent`](../../maps/core/Layer.md) in interface [`Layer`](../../maps/core/Layer.md)

      Overrides:
      [`handleEvent`](../../maps/layer/ui/ProgressIndicatorLayer.md) in class [`ProgressIndicatorLayer`](../../maps/layer/ui/ProgressIndicatorLayer.md)

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

- [Prev Class](NFEPathRenderer.md)
- [Next Class](NFERenderer.md)

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
