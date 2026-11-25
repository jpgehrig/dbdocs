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

- [Prev Class](RectangleDrawer.md)
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

oracle.spatial.network.nfe.vis.maps.tools

## Interface Tool

- All Superinterfaces:
  [Layer](../core/Layer.md)

  <!-- -->

  All Known Implementing Classes:
  [BasicTool](BasicTool.md), [NFEAddFeatureElementTool](../../mapcanvas/tool/NFEAddFeatureElementTool.md), [NFEAddFeatureTool](../../mapcanvas/tool/NFEAddFeatureTool.md), [NFEBoxSelectionTool](../../mapcanvas/tool/NFEBoxSelectionTool.md), [NFEEditVertexTool](../../mapcanvas/tool/NFEEditVertexTool.md), [NFEFeatureElementSelectionTool](../../mapcanvas/tool/NFEFeatureElementSelectionTool.md), [NFEFeatureSelectionTool](../../mapcanvas/tool/NFEFeatureSelectionTool.md), [NFEManipulateTool](../../mapcanvas/tool/NFEManipulateTool.md), [NFENetElementSelectionTool](../../mapcanvas/tool/NFENetElementSelectionTool.md), [NFESelectionTool](../../mapcanvas/tool/NFESelectionTool.md), [NFETool](../../mapcanvas/tool/NFETool.md)

  ------------------------------------------------------------------------



      public interface Tool
      extends Layer

  A map tool defines what actions to be taken upon user input events.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](../core/Layer.md)

      [`PROPERTY_NAME`](../core/Layer.md)`, `[`PROPERTY_PROVIDERID`](../core/Layer.md)`, `[`PROPERTY_SRID`](../core/Layer.md)`, `[`PROPERTY_VISIBLE`](../core/Layer.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                      |
    |-------------------|-----------------------------------------------------------------------------|
    | `boolean`         | `isInAction``()`<br>Returns true if the tool is in the middle of an action. |

    - ### Methods inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](../core/Layer.md)

      [`added`](../core/Layer.md)`, `[`clear`](../core/Layer.md)`, `[`fromXMLElement`](../core/Layer.md)`, `[`getCanvas`](../core/Layer.md)`, `[`getDataMBR`](../core/Layer.md)`, `[`getFullExtent`](../core/Layer.md)`, `[`getIcon`](../core/Layer.md)`, `[`getName`](../core/Layer.md)`, `[`getProviderID`](../core/Layer.md)`, `[`getSRID`](../core/Layer.md)`, `[`handleEvent`](../core/Layer.md)`, `[`hitTest`](../core/Layer.md)`, `[`hitTest`](../core/Layer.md)`, `[`isVisible`](../core/Layer.md)`, `[`mapRegionChanged`](../core/Layer.md)`, `[`removed`](../core/Layer.md)`, `[`render`](../core/Layer.md)`, `[`repaint`](../core/Layer.md)`, `[`setCanvas`](../core/Layer.md)`, `[`setName`](../core/Layer.md)`, `[`setProviderID`](../core/Layer.md)`, `[`setSRID`](../core/Layer.md)`, `[`setVisible`](../core/Layer.md)`, `[`toXMLElement`](../core/Layer.md)`, `[`update`](../core/Layer.md)

<!-- -->

- - ### Method Detail

    - #### isInAction

          boolean isInAction()

      Returns true if the tool is in the middle of an action.
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

- [Prev Class](RectangleDrawer.md)
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
