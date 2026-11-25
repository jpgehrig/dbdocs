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

- [Prev Class](MapUndoManager.md)
- [Next Class](SelectableLayer.md)

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

## Interface MVThemeLayer

- All Superinterfaces:
  [Layer](Layer.md)

  <!-- -->

  All Known Implementing Classes:
  [AbstractDataSetLayer](../layer/AbstractDataSetLayer.md)

  ------------------------------------------------------------------------



      public interface MVThemeLayer
      extends Layer

  A layer that renders a MapViewer theme

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](Layer.md)

      [`PROPERTY_NAME`](Layer.md)`, `[`PROPERTY_PROVIDERID`](Layer.md)`, `[`PROPERTY_SRID`](Layer.md)`, `[`PROPERTY_VISIBLE`](Layer.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                  |
    |-------------------|---------------------------------------------------------------------------------------------------------|
    | `ThemeDescriptor` | `getThemeDescriptor``()`<br>The theme descriptor used by a producer to perform the request to MapViewer |

    - ### Methods inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](Layer.md)

      [`added`](Layer.md)`, `[`clear`](Layer.md)`, `[`fromXMLElement`](Layer.md)`, `[`getCanvas`](Layer.md)`, `[`getDataMBR`](Layer.md)`, `[`getFullExtent`](Layer.md)`, `[`getIcon`](Layer.md)`, `[`getName`](Layer.md)`, `[`getProviderID`](Layer.md)`, `[`getSRID`](Layer.md)`, `[`handleEvent`](Layer.md)`, `[`hitTest`](Layer.md)`, `[`hitTest`](Layer.md)`, `[`isVisible`](Layer.md)`, `[`mapRegionChanged`](Layer.md)`, `[`removed`](Layer.md)`, `[`render`](Layer.md)`, `[`repaint`](Layer.md)`, `[`setCanvas`](Layer.md)`, `[`setName`](Layer.md)`, `[`setProviderID`](Layer.md)`, `[`setSRID`](Layer.md)`, `[`setVisible`](Layer.md)`, `[`toXMLElement`](Layer.md)`, `[`update`](Layer.md)

<!-- -->

- - ### Method Detail

    - #### getThemeDescriptor

          ThemeDescriptor getThemeDescriptor()

      The theme descriptor used by a producer to perform the request to MapViewer
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

- [Prev Class](MapUndoManager.md)
- [Next Class](SelectableLayer.md)

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
