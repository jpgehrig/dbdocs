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

- [Prev Class](CoreLoop.md)
- [Next Class](DefaultSelectionManager.md)

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

## Interface DataProducer

- All Known Subinterfaces:
  [GeoDataProducer](GeoDataProducer.md)

  ------------------------------------------------------------------------



      public interface DataProducer

  A generic interface for all types of data producers. A data producer produces data, and notifies all interested layer once data is available, or if an exception occurred while loading data. Data consumers (Layers) typically listens

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type   | Method and Description                                                                                  |
    |---------------------|---------------------------------------------------------------------------------------------------------|
    | [`Layer`](Layer.md) | `getLayer``()`<br>Gets the layer that is currently consuming data from this producer.                   |
    | `void`              | `setLayer``(`[`Layer`](Layer.md)` layer)`<br>Sets the layer that should be notified when data is ready. |

<!-- -->

- - ### Method Detail

    - #### setLayer

          void setLayer(Layer layer)

      Sets the layer that should be notified when data is ready.
      Parameters:
      `layer` -

    <!-- -->

    - #### getLayer

          Layer getLayer()

      Gets the layer that is currently consuming data from this producer.

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

- [Prev Class](CoreLoop.md)
- [Next Class](DefaultSelectionManager.md)

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
