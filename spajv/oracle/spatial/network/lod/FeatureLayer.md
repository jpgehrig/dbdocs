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

- [Prev Class](FeatureImpl.md)
- [Next Class](FeatureLayerImpl.md)

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

## Interface FeatureLayer

- All Known Implementing Classes:
  [FeatureLayerImpl](FeatureLayerImpl.md)

  ------------------------------------------------------------------------



      public interface FeatureLayer

  Features associated with elements in a network, sub-network or a partition, in a feature layer.
  Since:
  12.1

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type           | Method and Description                                                                     |
    |-----------------------------|--------------------------------------------------------------------------------------------|
    | `void`                      | `addFeature``(`[`Feature`](Feature.md)` feature)`<br>Adds a feature to the feature layer.  |
    | [`Feature`](Feature.md)     | `getFeature``(long featureId)`<br>Returns the feature with the input feature ID.           |
    | `long[]`                    | `getFeatureIds``()`<br>Returns all the feature IDs in this feature layer.                  |
    | [`Feature`](Feature.md)`[]` | `getFeatures``()`<br>Returns all the features in this feature layer.                       |
    | [`Feature`](Feature.md)`[]` | `getFeaturesOnLink``(long linkId)`<br>Returns the features associated with the input link. |
    | [`Feature`](Feature.md)`[]` | `getFeaturesOnNode``(long nodeId)`<br>Returns the features associated with the input node. |

<!-- -->

- - ### Method Detail

    - #### addFeature

          void addFeature(Feature feature)

      Adds a feature to the feature layer.
      Parameters:
      `feature` -

    <!-- -->

    - #### getFeature

          Feature getFeature(long featureId)

      Returns the feature with the input feature ID.
      Parameters:

      `featureId` -

      Returns:

    <!-- -->

    - #### getFeatures

          Feature[] getFeatures()

      Returns all the features in this feature layer.
      Returns:

    <!-- -->

    - #### getFeaturesOnNode

          Feature[] getFeaturesOnNode(long nodeId)

      Returns the features associated with the input node.
      Parameters:

      `nodeId` - ID of the node

      Returns:

    <!-- -->

    - #### getFeaturesOnLink

          Feature[] getFeaturesOnLink(long linkId)

      Returns the features associated with the input link.
      Parameters:

      `linkId` - ID of the link

      Returns:

    <!-- -->

    - #### getFeatureIds

          long[] getFeatureIds()

      Returns all the feature IDs in this feature layer.
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

- [Prev Class](FeatureImpl.md)
- [Next Class](FeatureLayerImpl.md)

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
