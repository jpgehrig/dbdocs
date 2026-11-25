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

- [Prev Class](MVThemeLayer.md)
- [Next Class](SelectionEvent.md)

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

## Interface SelectableLayer

- All Superinterfaces:
  [GeoObjectLayer](GeoObjectLayer.md), [Layer](Layer.md)

  <!-- -->

  All Known Implementing Classes:
  [AbstractDataSetLayer](../layer/AbstractDataSetLayer.md), [NFEFeatureLayerRenderer](../../mapcanvas/render/NFEFeatureLayerRenderer.md), [NFEManipulableFeatureLayerRenderer](../../mapcanvas/render/NFEManipulableFeatureLayerRenderer.md), [NFENetworkRenderer](../../mapcanvas/render/NFENetworkRenderer.md), [NFEPathRenderer](../../mapcanvas/render/NFEPathRenderer.md), [NFERenderer](../../mapcanvas/render/NFERenderer.md)

  ------------------------------------------------------------------------



      public interface SelectableLayer
      extends GeoObjectLayer

  An interface for layers that have objects that can be selected They use a SelectionManager to handle selections

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](Layer.md)

      [`PROPERTY_NAME`](Layer.md)`, `[`PROPERTY_PROVIDERID`](Layer.md)`, `[`PROPERTY_SRID`](Layer.md)`, `[`PROPERTY_VISIBLE`](Layer.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                               | Method and Description                                                                                                                                                                                       |
    |-------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                          | `addSelectionListener``(`[`SelectionListener`](SelectionListener.md)` l)`<br>Adds a SelectionListener                                                                                                        |
    | `boolean`                                       | `clearSelection``()`<br>Clears all selected objects                                                                                                                                                          |
    | `java.util.List<`[`GeoObject`](GeoObject.md)`>` | `getSelection``()`<br>Returns all selected objects                                                                                                                                                           |
    | `java.util.List<`[`GeoObject`](GeoObject.md)`>` | `getSelection``(`[`GeoObject`](GeoObject.md)` obj)`<br>Returns selected objects that are children of the provided objects GeoObject's isSubElementOf() determines if an object is children of another object |
    | `boolean`                                       | `isSelected``(`[`GeoObject`](GeoObject.md)` obj)`<br>Checks if an object is selected                                                                                                                         |
    | `int`                                           | `numSelected``()`<br>Returns the number of selected objects                                                                                                                                                  |
    | `void`                                          | `removeSelectionListener``(`[`SelectionListener`](SelectionListener.md)` l)`<br>Removes the given SelectionListener                                                                                          |
    | `boolean`                                       | `select``(java.util.List<`[`GeoObject`](GeoObject.md)`> objs)`<br>Adds the provided objects to the selection list                                                                                            |
    | `boolean`                                       | `setSelection``(java.util.List<`[`GeoObject`](GeoObject.md)`> objs)`<br>Clears selection before setting the provided objects as selected                                                                     |
    | `boolean`                                       | `unselect``(java.util.List<`[`GeoObject`](GeoObject.md)`> objs)`<br>Removes the provided objects from the selection list                                                                                     |

    - ### Methods inherited from interface oracle.spatial.network.nfe.vis.maps.core.[GeoObjectLayer](GeoObjectLayer.md)

      [`getObject`](GeoObjectLayer.md)`, `[`getObjects`](GeoObjectLayer.md)

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](Layer.md)

      [`added`](Layer.md)`, `[`clear`](Layer.md)`, `[`fromXMLElement`](Layer.md)`, `[`getCanvas`](Layer.md)`, `[`getDataMBR`](Layer.md)`, `[`getFullExtent`](Layer.md)`, `[`getIcon`](Layer.md)`, `[`getName`](Layer.md)`, `[`getProviderID`](Layer.md)`, `[`getSRID`](Layer.md)`, `[`handleEvent`](Layer.md)`, `[`hitTest`](Layer.md)`, `[`hitTest`](Layer.md)`, `[`isVisible`](Layer.md)`, `[`mapRegionChanged`](Layer.md)`, `[`removed`](Layer.md)`, `[`render`](Layer.md)`, `[`repaint`](Layer.md)`, `[`setCanvas`](Layer.md)`, `[`setName`](Layer.md)`, `[`setProviderID`](Layer.md)`, `[`setSRID`](Layer.md)`, `[`setVisible`](Layer.md)`, `[`toXMLElement`](Layer.md)`, `[`update`](Layer.md)

<!-- -->

- - ### Method Detail

    - #### isSelected

          boolean isSelected(GeoObject obj)

      Checks if an object is selected
      Returns:
      true if the provided object is selected

    <!-- -->

    - #### clearSelection

          boolean clearSelection()

      Clears all selected objects
      Returns:
      true if changes where made

    <!-- -->

    - #### numSelected

          int numSelected()

      Returns the number of selected objects
      Returns:
      the number of selected objects

    <!-- -->

    - #### getSelection

          java.util.List<GeoObject> getSelection()

      Returns all selected objects
      Returns:

    <!-- -->

    - #### getSelection

          java.util.List<GeoObject> getSelection(GeoObject obj)

      Returns selected objects that are children of the provided objects GeoObject's isSubElementOf() determines if an object is children of another object
      Parameters:

      `obj` -

      Returns:

    <!-- -->

    - #### setSelection

          boolean setSelection(java.util.List<GeoObject> objs)

      Clears selection before setting the provided objects as selected
      Parameters:

      `objs` -

      Returns:

    <!-- -->

    - #### select

          boolean select(java.util.List<GeoObject> objs)

      Adds the provided objects to the selection list
      Parameters:

      `objs` -

      Returns:

    <!-- -->

    - #### unselect

          boolean unselect(java.util.List<GeoObject> objs)

      Removes the provided objects from the selection list
      Parameters:

      `objs` -

      Returns:

    <!-- -->

    - #### addSelectionListener

          void addSelectionListener(SelectionListener l)

      Adds a SelectionListener
      Parameters:
      `l` -

    <!-- -->

    - #### removeSelectionListener

          void removeSelectionListener(SelectionListener l)

      Removes the given SelectionListener
      Parameters:
      `l` -

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

- [Prev Class](MVThemeLayer.md)
- [Next Class](SelectionEvent.md)

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
