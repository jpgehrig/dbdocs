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
- [Next Class](NFEFeatureLayerRenderer.md)

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

## Interface ContextualMenuHandler

-

  ------------------------------------------------------------------------



      public interface ContextualMenuHandler

  Interface to implement a class that will add menu items to the contextual menu.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                   |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `handleMenu``(javax.swing.JPopupMenu popup, java.util.List<`[`GeoObject`](../../maps/core/GeoObject.md)`> hits)`<br>Handles menu method. |

<!-- -->

- - ### Method Detail

    - #### handleMenu

          void handleMenu(javax.swing.JPopupMenu popup,
                          java.util.List<GeoObject> hits)

      Handles menu method.
      Parameters:
      `popup` - Popup menu to add the menu items

      `hits` - list of objects for which to display the menu. It can be network elements or feature elements.

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
- [Next Class](NFEFeatureLayerRenderer.md)

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
