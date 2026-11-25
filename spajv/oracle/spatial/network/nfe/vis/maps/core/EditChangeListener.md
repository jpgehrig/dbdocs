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

- [Prev Class](EditableLayer.md)
- [Next Class](EventManager.md)

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

## Interface EditChangeListener

- All Superinterfaces:
  java.util.EventListener

  <!-- -->

  All Known Implementing Classes:
  [LayerManager](LayerManager.md)

  ------------------------------------------------------------------------



      public interface EditChangeListener
      extends java.util.EventListener

  Implementers will be notified when a layer content is edited

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                          |
    |-------------------|---------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `editStateChanged``(javax.swing.event.ChangeEvent e)`<br>Invoked when the layer has changed as a result of editing it's objects |

<!-- -->

- - ### Method Detail

    - #### editStateChanged

          void editStateChanged(javax.swing.event.ChangeEvent e)

      Invoked when the layer has changed as a result of editing it's objects
      Parameters:
      `e` - a ChangeEvent object

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

- [Prev Class](EditableLayer.md)
- [Next Class](EventManager.md)

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
