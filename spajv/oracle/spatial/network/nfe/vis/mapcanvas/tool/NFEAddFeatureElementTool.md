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

- Prev Class
- [Next Class](NFEAddFeatureTool.md)

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

## Class NFEAddFeatureElementTool

- java.lang.Object

- - [oracle.spatial.network.nfe.vis.maps.layer.BasicLayer](../../maps/layer/BasicLayer.md)

  - - [oracle.spatial.network.nfe.vis.maps.tools.BasicTool](../../maps/tools/BasicTool.md)

    - - [oracle.spatial.network.nfe.vis.mapcanvas.tool.NFETool](NFETool.md)

      - - oracle.spatial.network.nfe.vis.mapcanvas.tool.NFEAddFeatureElementTool

<!-- -->

- All Implemented Interfaces:
  [Layer](../../maps/core/Layer.md), [Tool](../../maps/tools/Tool.md)

  ------------------------------------------------------------------------



      public class NFEAddFeatureElementTool
      extends NFETool

  Tool used for creating new feature elements for a feature layer

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](../../maps/core/Layer.md)

      [`PROPERTY_NAME`](../../maps/core/Layer.md)`, `[`PROPERTY_PROVIDERID`](../../maps/core/Layer.md)`, `[`PROPERTY_SRID`](../../maps/core/Layer.md)`, `[`PROPERTY_VISIBLE`](../../maps/core/Layer.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                      |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `NFEAddFeatureElementTool``(`[`MapCanvas`](../../maps/core/MapCanvas.md)` canvas, `[`NFEModel`](../../../model/NFEModel.md)` model)`<br>Allocates a new add feature element tool |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                              | Method and Description                                                                                                                                                                                   |
    |----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                         | `clear``()`<br>Clears all contents of this layer.                                                                                                                                                        |
    | [`NFEFeatureClass`](../../../model/feature/NFEFeatureClass.md) | `getFeatureClass``()`<br>Gets the feature class used for creating new features in case a target feature has not been specified                                                                           |
    | [`HoverableLayer`](../../maps/core/HoverableLayer.md)          | `getHoverLayer``()`<br>Gets the layer that is hovered when adding feature elements.                                                                                                                      |
    | [`NFEFeature`](../../../model/feature/NFEFeature.md)           | `getTargetFeature``()`<br>Gets the feature to which the new feature elements will be added                                                                                                               |
    | `boolean`                                                      | `handleEvent``(java.util.EventObject evt)`<br>The main method that performs event handling for this tool.                                                                                                |
    | `long`                                                         | `render``(java.awt.Graphics2D g)`<br>Renders the layer contents to the given Graphics.                                                                                                                   |
    | `void`                                                         | `setFeatureClass``(`[`NFEFeatureClass`](../../../model/feature/NFEFeatureClass.md)` featClass)`<br>Sets the feature class used for creating new features in case a target feature has not been specified |
    | `void`                                                         | `setHoverLayer``(`[`HoverableLayer`](../../maps/core/HoverableLayer.md)` targetLayer)`<br>Sets the layer that is hovered when adding feature elements.                                                   |
    | `void`                                                         | `setTargetFeature``(`[`NFEFeature`](../../../model/feature/NFEFeature.md)` targetFeature)`<br>Sets the feature to which the new feature elements will be added.                                          |

    - ### Methods inherited from class oracle.spatial.network.nfe.vis.mapcanvas.tool.[NFETool](NFETool.md)

      [`getModel`](NFETool.md)`, `[`getTolerance`](NFETool.md)`, `[`isEnabled`](NFETool.md)`, `[`setEnabled`](NFETool.md)

    <!-- -->

    - ### Methods inherited from class oracle.spatial.network.nfe.vis.maps.tools.[BasicTool](../../maps/tools/BasicTool.md)

      [`isInAction`](../../maps/tools/BasicTool.md)

    <!-- -->

    - ### Methods inherited from class oracle.spatial.network.nfe.vis.maps.layer.[BasicLayer](../../maps/layer/BasicLayer.md)

      [`added`](../../maps/layer/BasicLayer.md)`, `[`addPropertyChangeListener`](../../maps/layer/BasicLayer.md)`, `[`addPropertyChangeListener`](../../maps/layer/BasicLayer.md)`, `[`fromXMLElement`](../../maps/layer/BasicLayer.md)`, `[`getCanvas`](../../maps/layer/BasicLayer.md)`, `[`getDataMBR`](../../maps/layer/BasicLayer.md)`, `[`getFullExtent`](../../maps/layer/BasicLayer.md)`, `[`getIcon`](../../maps/layer/BasicLayer.md)`, `[`getName`](../../maps/layer/BasicLayer.md)`, `[`getProperties`](../../maps/layer/BasicLayer.md)`, `[`getProperty`](../../maps/layer/BasicLayer.md)`, `[`getProperty`](../../maps/layer/BasicLayer.md)`, `[`getPropertyChangeListeners`](../../maps/layer/BasicLayer.md)`, `[`getPropertyChangeListeners`](../../maps/layer/BasicLayer.md)`, `[`getProviderID`](../../maps/layer/BasicLayer.md)`, `[`getSRID`](../../maps/layer/BasicLayer.md)`, `[`hitTest`](../../maps/layer/BasicLayer.md)`, `[`hitTest`](../../maps/layer/BasicLayer.md)`, `[`isVisible`](../../maps/layer/BasicLayer.md)`, `[`mapRegionChanged`](../../maps/layer/BasicLayer.md)`, `[`removed`](../../maps/layer/BasicLayer.md)`, `[`removePropertyChangeListener`](../../maps/layer/BasicLayer.md)`, `[`removePropertyChangeListener`](../../maps/layer/BasicLayer.md)`, `[`repaint`](../../maps/layer/BasicLayer.md)`, `[`setCanvas`](../../maps/layer/BasicLayer.md)`, `[`setName`](../../maps/layer/BasicLayer.md)`, `[`setProperty`](../../maps/layer/BasicLayer.md)`, `[`setProviderID`](../../maps/layer/BasicLayer.md)`, `[`setSRID`](../../maps/layer/BasicLayer.md)`, `[`setVisible`](../../maps/layer/BasicLayer.md)`, `[`toXMLElement`](../../maps/layer/BasicLayer.md)`, `[`update`](../../maps/layer/BasicLayer.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](../../maps/core/Layer.md)

      [`added`](../../maps/core/Layer.md)`, `[`fromXMLElement`](../../maps/core/Layer.md)`, `[`getCanvas`](../../maps/core/Layer.md)`, `[`getDataMBR`](../../maps/core/Layer.md)`, `[`getFullExtent`](../../maps/core/Layer.md)`, `[`getIcon`](../../maps/core/Layer.md)`, `[`getName`](../../maps/core/Layer.md)`, `[`getProviderID`](../../maps/core/Layer.md)`, `[`getSRID`](../../maps/core/Layer.md)`, `[`hitTest`](../../maps/core/Layer.md)`, `[`hitTest`](../../maps/core/Layer.md)`, `[`isVisible`](../../maps/core/Layer.md)`, `[`mapRegionChanged`](../../maps/core/Layer.md)`, `[`removed`](../../maps/core/Layer.md)`, `[`repaint`](../../maps/core/Layer.md)`, `[`setCanvas`](../../maps/core/Layer.md)`, `[`setName`](../../maps/core/Layer.md)`, `[`setProviderID`](../../maps/core/Layer.md)`, `[`setSRID`](../../maps/core/Layer.md)`, `[`setVisible`](../../maps/core/Layer.md)`, `[`toXMLElement`](../../maps/core/Layer.md)`, `[`update`](../../maps/core/Layer.md)

<!-- -->

- - ### Constructor Detail

    - #### NFEAddFeatureElementTool

          public NFEAddFeatureElementTool(MapCanvas canvas,
                                          NFEModel model)

      Allocates a new add feature element tool
      Parameters:
      `canvas` - the current MapCanvas

      `model` - the current NFE model

  <!-- -->

  - ### Method Detail

    - #### getFeatureClass

          public NFEFeatureClass getFeatureClass()

      Gets the feature class used for creating new features in case a target feature has not been specified
      Returns:
      a feature class

    <!-- -->

    - #### setFeatureClass

          public void setFeatureClass(NFEFeatureClass featClass)

      Sets the feature class used for creating new features in case a target feature has not been specified
      Parameters:
      `featClass` - a feature class

    <!-- -->

    - #### getTargetFeature

          public NFEFeature getTargetFeature()

      Gets the feature to which the new feature elements will be added
      Returns:
      a feature

    <!-- -->

    - #### setTargetFeature

          public void setTargetFeature(NFEFeature targetFeature)

      Sets the feature to which the new feature elements will be added. If a target feature is set, there is not need to set the current feature class.
      Parameters:
      `targetFeature` - a feature

    <!-- -->

    - #### getHoverLayer

          public HoverableLayer getHoverLayer()

      Gets the layer that is hovered when adding feature elements. Typically it would be a network layer
      Returns:
      a hoverable layer

    <!-- -->

    - #### setHoverLayer

          public void setHoverLayer(HoverableLayer targetLayer)

      Sets the layer that is hovered when adding feature elements. Typically it would be a network layer
      Parameters:
      `targetLayer` - a hoverable layer

    <!-- -->

    - #### handleEvent

          public boolean handleEvent(java.util.EventObject evt)

      Description copied from interface: [`Layer`](../../maps/core/Layer.md)
      The main method that performs event handling for this tool. Returns whether the event should be propagated to other layers down stream (further down the layer stack) after the event has been handled.
      Specified by:
      [`handleEvent`](../../maps/core/Layer.md) in interface [`Layer`](../../maps/core/Layer.md)

      Overrides:
      [`handleEvent`](NFETool.md) in class [`NFETool`](NFETool.md)

    <!-- -->

    - #### clear

          public void clear()

      Description copied from interface: [`Layer`](../../maps/core/Layer.md)
      Clears all contents of this layer.
      Specified by:
      [`clear`](../../maps/core/Layer.md) in interface [`Layer`](../../maps/core/Layer.md)

      Overrides:
      [`clear`](../../maps/layer/BasicLayer.md) in class [`BasicLayer`](../../maps/layer/BasicLayer.md)

    <!-- -->

    - #### render

          public long render(java.awt.Graphics2D g)

      Description copied from interface: [`Layer`](../../maps/core/Layer.md)
      Renders the layer contents to the given Graphics.
      Specified by:
      [`render`](../../maps/core/Layer.md) in interface [`Layer`](../../maps/core/Layer.md)

      Overrides:
      [`render`](../../maps/layer/BasicLayer.md) in class [`BasicLayer`](../../maps/layer/BasicLayer.md)

      Parameters:
      `g` - the graphics object

      Returns:
      the rendering time in milliseconds.

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

- Prev Class
- [Next Class](NFEAddFeatureTool.md)

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
