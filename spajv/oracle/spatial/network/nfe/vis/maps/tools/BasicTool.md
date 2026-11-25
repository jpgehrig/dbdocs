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
- [Next Class](RectangleDrawer.md)

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

## Class BasicTool

- java.lang.Object

- - [oracle.spatial.network.nfe.vis.maps.layer.BasicLayer](../layer/BasicLayer.md)

  - - oracle.spatial.network.nfe.vis.maps.tools.BasicTool

<!-- -->

- All Implemented Interfaces:
  [Layer](../core/Layer.md), [Tool](Tool.md)

  <!-- -->

  Direct Known Subclasses:
  [NFETool](../../mapcanvas/tool/NFETool.md)

  ------------------------------------------------------------------------



      public class BasicTool
      extends BasicLayer
      implements Tool

  A basic do-nothing tool intended for extension by concrete tools.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](../core/Layer.md)

      [`PROPERTY_NAME`](../core/Layer.md)`, `[`PROPERTY_PROVIDERID`](../core/Layer.md)`, `[`PROPERTY_SRID`](../core/Layer.md)`, `[`PROPERTY_VISIBLE`](../core/Layer.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                  |
    |--------------------------------------------------------------|
    | `BasicTool``(`[`MapCanvas`](../core/MapCanvas.md)` canvas)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                 |
    |-------------------|------------------------------------------------------------------------|
    | `boolean`         | `isInAction``()`<br>Returns if the tool in in the middle of an action. |

    - ### Methods inherited from class oracle.spatial.network.nfe.vis.maps.layer.[BasicLayer](../layer/BasicLayer.md)

      [`added`](../layer/BasicLayer.md)`, `[`addPropertyChangeListener`](../layer/BasicLayer.md)`, `[`addPropertyChangeListener`](../layer/BasicLayer.md)`, `[`clear`](../layer/BasicLayer.md)`, `[`fromXMLElement`](../layer/BasicLayer.md)`, `[`getCanvas`](../layer/BasicLayer.md)`, `[`getDataMBR`](../layer/BasicLayer.md)`, `[`getFullExtent`](../layer/BasicLayer.md)`, `[`getIcon`](../layer/BasicLayer.md)`, `[`getName`](../layer/BasicLayer.md)`, `[`getProperties`](../layer/BasicLayer.md)`, `[`getProperty`](../layer/BasicLayer.md)`, `[`getProperty`](../layer/BasicLayer.md)`, `[`getPropertyChangeListeners`](../layer/BasicLayer.md)`, `[`getPropertyChangeListeners`](../layer/BasicLayer.md)`, `[`getProviderID`](../layer/BasicLayer.md)`, `[`getSRID`](../layer/BasicLayer.md)`, `[`handleEvent`](../layer/BasicLayer.md)`, `[`hitTest`](../layer/BasicLayer.md)`, `[`hitTest`](../layer/BasicLayer.md)`, `[`isVisible`](../layer/BasicLayer.md)`, `[`mapRegionChanged`](../layer/BasicLayer.md)`, `[`removed`](../layer/BasicLayer.md)`, `[`removePropertyChangeListener`](../layer/BasicLayer.md)`, `[`removePropertyChangeListener`](../layer/BasicLayer.md)`, `[`render`](../layer/BasicLayer.md)`, `[`repaint`](../layer/BasicLayer.md)`, `[`setCanvas`](../layer/BasicLayer.md)`, `[`setName`](../layer/BasicLayer.md)`, `[`setProperty`](../layer/BasicLayer.md)`, `[`setProviderID`](../layer/BasicLayer.md)`, `[`setSRID`](../layer/BasicLayer.md)`, `[`setVisible`](../layer/BasicLayer.md)`, `[`toXMLElement`](../layer/BasicLayer.md)`, `[`update`](../layer/BasicLayer.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](../core/Layer.md)

      [`added`](../core/Layer.md)`, `[`clear`](../core/Layer.md)`, `[`fromXMLElement`](../core/Layer.md)`, `[`getCanvas`](../core/Layer.md)`, `[`getDataMBR`](../core/Layer.md)`, `[`getFullExtent`](../core/Layer.md)`, `[`getIcon`](../core/Layer.md)`, `[`getName`](../core/Layer.md)`, `[`getProviderID`](../core/Layer.md)`, `[`getSRID`](../core/Layer.md)`, `[`handleEvent`](../core/Layer.md)`, `[`hitTest`](../core/Layer.md)`, `[`hitTest`](../core/Layer.md)`, `[`isVisible`](../core/Layer.md)`, `[`mapRegionChanged`](../core/Layer.md)`, `[`removed`](../core/Layer.md)`, `[`render`](../core/Layer.md)`, `[`repaint`](../core/Layer.md)`, `[`setCanvas`](../core/Layer.md)`, `[`setName`](../core/Layer.md)`, `[`setProviderID`](../core/Layer.md)`, `[`setSRID`](../core/Layer.md)`, `[`setVisible`](../core/Layer.md)`, `[`toXMLElement`](../core/Layer.md)`, `[`update`](../core/Layer.md)

<!-- -->

- - ### Constructor Detail

    - #### BasicTool

          public BasicTool(MapCanvas canvas)

  <!-- -->

  - ### Method Detail

    - #### isInAction

          public boolean isInAction()

      Returns if the tool in in the middle of an action.
      Specified by:

      [`isInAction`](Tool.md) in interface [`Tool`](Tool.md)

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

- Prev Class
- [Next Class](RectangleDrawer.md)

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
