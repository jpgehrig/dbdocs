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

- [Prev Class](NFESelectionTool.md)
- Next Class

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

oracle.spatial.network.nfe.vis.mapcanvas.tool

## Class NFETool

- java.lang.Object

- - [oracle.spatial.network.nfe.vis.maps.layer.BasicLayer](../../maps/layer/BasicLayer.md)

  - - [oracle.spatial.network.nfe.vis.maps.tools.BasicTool](../../maps/tools/BasicTool.md)

    - - oracle.spatial.network.nfe.vis.mapcanvas.tool.NFETool

<!-- -->

- All Implemented Interfaces:
  [Layer](../../maps/core/Layer.md), [Tool](../../maps/tools/Tool.md)

  <!-- -->

  Direct Known Subclasses:
  [NFEAddFeatureElementTool](NFEAddFeatureElementTool.md), [NFEAddFeatureTool](NFEAddFeatureTool.md), [NFEEditVertexTool](NFEEditVertexTool.md), [NFEManipulateTool](NFEManipulateTool.md), [NFESelectionTool](NFESelectionTool.md)

  ------------------------------------------------------------------------



      public class NFETool
      extends BasicTool

  The basic class every NFE tool should implement. It provides common methods for NFE-related tasks.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](../../maps/core/Layer.md)

      [`PROPERTY_NAME`](../../maps/core/Layer.md)`, `[`PROPERTY_PROVIDERID`](../../maps/core/Layer.md)`, `[`PROPERTY_SRID`](../../maps/core/Layer.md)`, `[`PROPERTY_VISIBLE`](../../maps/core/Layer.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                          |
    |----------------------------------------------------------------------------------------------------------------------|
    | `NFETool``(`[`MapCanvas`](../../maps/core/MapCanvas.md)` canvas, `[`NFEModel`](../../../model/NFEModel.md)` model)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                        | Method and Description                                                                                    |
    |------------------------------------------|-----------------------------------------------------------------------------------------------------------|
    | [`NFEModel`](../../../model/NFEModel.md) | `getModel``()`<br>Gets the current model                                                                  |
    | `double`                                 | `getTolerance``()`<br>Gets the tolerance used by the tool                                                 |
    | `boolean`                                | `handleEvent``(java.util.EventObject evt)`<br>The main method that performs event handling for this tool. |
    | `boolean`                                | `isEnabled``()`<br>Tells whether the tool is enabled or not                                               |
    | `void`                                   | `setEnabled``(boolean enabled)`<br>Sets whether the tool is enabled or not                                |

    - ### Methods inherited from class oracle.spatial.network.nfe.vis.maps.tools.[BasicTool](../../maps/tools/BasicTool.md)

      [`isInAction`](../../maps/tools/BasicTool.md)

    <!-- -->

    - ### Methods inherited from class oracle.spatial.network.nfe.vis.maps.layer.[BasicLayer](../../maps/layer/BasicLayer.md)

      [`added`](../../maps/layer/BasicLayer.md)`, `[`addPropertyChangeListener`](../../maps/layer/BasicLayer.md)`, `[`addPropertyChangeListener`](../../maps/layer/BasicLayer.md)`, `[`clear`](../../maps/layer/BasicLayer.md)`, `[`fromXMLElement`](../../maps/layer/BasicLayer.md)`, `[`getCanvas`](../../maps/layer/BasicLayer.md)`, `[`getDataMBR`](../../maps/layer/BasicLayer.md)`, `[`getFullExtent`](../../maps/layer/BasicLayer.md)`, `[`getIcon`](../../maps/layer/BasicLayer.md)`, `[`getName`](../../maps/layer/BasicLayer.md)`, `[`getProperties`](../../maps/layer/BasicLayer.md)`, `[`getProperty`](../../maps/layer/BasicLayer.md)`, `[`getProperty`](../../maps/layer/BasicLayer.md)`, `[`getPropertyChangeListeners`](../../maps/layer/BasicLayer.md)`, `[`getPropertyChangeListeners`](../../maps/layer/BasicLayer.md)`, `[`getProviderID`](../../maps/layer/BasicLayer.md)`, `[`getSRID`](../../maps/layer/BasicLayer.md)`, `[`hitTest`](../../maps/layer/BasicLayer.md)`, `[`hitTest`](../../maps/layer/BasicLayer.md)`, `[`isVisible`](../../maps/layer/BasicLayer.md)`, `[`mapRegionChanged`](../../maps/layer/BasicLayer.md)`, `[`removed`](../../maps/layer/BasicLayer.md)`, `[`removePropertyChangeListener`](../../maps/layer/BasicLayer.md)`, `[`removePropertyChangeListener`](../../maps/layer/BasicLayer.md)`, `[`render`](../../maps/layer/BasicLayer.md)`, `[`repaint`](../../maps/layer/BasicLayer.md)`, `[`setCanvas`](../../maps/layer/BasicLayer.md)`, `[`setName`](../../maps/layer/BasicLayer.md)`, `[`setProperty`](../../maps/layer/BasicLayer.md)`, `[`setProviderID`](../../maps/layer/BasicLayer.md)`, `[`setSRID`](../../maps/layer/BasicLayer.md)`, `[`setVisible`](../../maps/layer/BasicLayer.md)`, `[`toXMLElement`](../../maps/layer/BasicLayer.md)`, `[`update`](../../maps/layer/BasicLayer.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](../../maps/core/Layer.md)

      [`added`](../../maps/core/Layer.md)`, `[`clear`](../../maps/core/Layer.md)`, `[`fromXMLElement`](../../maps/core/Layer.md)`, `[`getCanvas`](../../maps/core/Layer.md)`, `[`getDataMBR`](../../maps/core/Layer.md)`, `[`getFullExtent`](../../maps/core/Layer.md)`, `[`getIcon`](../../maps/core/Layer.md)`, `[`getName`](../../maps/core/Layer.md)`, `[`getProviderID`](../../maps/core/Layer.md)`, `[`getSRID`](../../maps/core/Layer.md)`, `[`hitTest`](../../maps/core/Layer.md)`, `[`hitTest`](../../maps/core/Layer.md)`, `[`isVisible`](../../maps/core/Layer.md)`, `[`mapRegionChanged`](../../maps/core/Layer.md)`, `[`removed`](../../maps/core/Layer.md)`, `[`render`](../../maps/core/Layer.md)`, `[`repaint`](../../maps/core/Layer.md)`, `[`setCanvas`](../../maps/core/Layer.md)`, `[`setName`](../../maps/core/Layer.md)`, `[`setProviderID`](../../maps/core/Layer.md)`, `[`setSRID`](../../maps/core/Layer.md)`, `[`setVisible`](../../maps/core/Layer.md)`, `[`toXMLElement`](../../maps/core/Layer.md)`, `[`update`](../../maps/core/Layer.md)

<!-- -->

- - ### Constructor Detail

    - #### NFETool

          public NFETool(MapCanvas canvas,
                         NFEModel model)

  <!-- -->

  - ### Method Detail

    - #### getModel

          public NFEModel getModel()

      Gets the current model
      Returns:
      an NFE model instance

    <!-- -->

    - #### setEnabled

          public void setEnabled(boolean enabled)

      Sets whether the tool is enabled or not
      Parameters:
      `enabled` - true for enabled

    <!-- -->

    - #### isEnabled

          public boolean isEnabled()

      Tells whether the tool is enabled or not
      Returns:
      true for enabled

    <!-- -->

    - #### handleEvent

          public boolean handleEvent(java.util.EventObject evt)

      Description copied from interface: [`Layer`](../../maps/core/Layer.md)
      The main method that performs event handling for this tool. Returns whether the event should be propagated to other layers down stream (further down the layer stack) after the event has been handled.
      Specified by:
      [`handleEvent`](../../maps/core/Layer.md) in interface [`Layer`](../../maps/core/Layer.md)

      Overrides:
      [`handleEvent`](../../maps/layer/BasicLayer.md) in class [`BasicLayer`](../../maps/layer/BasicLayer.md)

    <!-- -->

    - #### getTolerance

          public double getTolerance()

      Gets the tolerance used by the tool
      Returns:
      the tolerance value in model's coordinate system

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

- [Prev Class](NFESelectionTool.md)
- Next Class

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
