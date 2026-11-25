Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](Feature.FeatureType.md)
- [Next Class](FeatureDataImpl.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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

oracle.spatial.network.lod

## Interface FeatureData

- All Known Implementing Classes:
  [FeatureDataImpl](FeatureDataImpl.md)

  ------------------------------------------------------------------------



      public interface FeatureData

  FeatureData contains information about all feature data associated with the network elements in a network, sub-network or a partition. Feature data are grouped in feature layers. Each feature layer is represented by a FeatureLayer object.
  Since:
  12.1

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                 | Method and Description                                                                                                                          |
    |-----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`FeatureLayer`](FeatureLayer.md) | `getFeatureLayer``(int featureLayerId)`<br>Returns the feature data for the input feature layer.                                                |
    | `int[]`                           | `getFeatureLayerIds``()`<br>Returns the feature layer IDs.                                                                                      |
    | `void`                            | `setFeatureLayer``(int featureLayerId, `[`FeatureLayer`](FeatureLayer.md)` featureLayer)`<br>Sets the feature data for the input feature layer. |

<!-- -->

- - ### Method Detail

    - #### getFeatureLayer

          FeatureLayer getFeatureLayer(int featureLayerId)

      Returns the feature data for the input feature layer.
      Parameters:

      `featureLayerId` -

      Returns:

    <!-- -->

    - #### setFeatureLayer

          void setFeatureLayer(int featureLayerId,
                               FeatureLayer featureLayer)

      Sets the feature data for the input feature layer.
      Parameters:
      `featureLayerId` - feature layer ID

      `featureLayer` - feature layer object

    <!-- -->

    - #### getFeatureLayerIds

          int[] getFeatureLayerIds()

      Returns the feature layer IDs.
      Returns:

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](Feature.FeatureType.md)
- [Next Class](FeatureDataImpl.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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
