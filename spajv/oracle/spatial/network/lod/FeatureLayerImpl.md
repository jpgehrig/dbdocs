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

- [Prev Class](FeatureLayer.md)
- [Next Class](FeatureLayerMetadata.md)

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

## Class FeatureLayerImpl

- java.lang.Object

- - oracle.spatial.network.lod.FeatureLayerImpl

<!-- -->

- All Implemented Interfaces:
  [FeatureLayer](FeatureLayer.md)

  ------------------------------------------------------------------------



      public class FeatureLayerImpl
      extends java.lang.Object
      implements FeatureLayer

  Default implementation of FeatureLayer.
  Since:
  12.1

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                   |
    |---------------------------------------------------------------|
    | `FeatureLayerImpl``()`<br>Constructs a FeatureLayer instance. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type           | Method and Description                                                                     |
    |-----------------------------|--------------------------------------------------------------------------------------------|
    | `void`                      | `addFeature``(`[`Feature`](Feature.md)` feature)`<br>Adds a feature to the feature layer.  |
    | [`Feature`](Feature.md)     | `getFeature``(long featureId)`<br>Returns the feature with the input feature ID.           |
    | `long[]`                    | `getFeatureIds``()`<br>Returns all the feature IDs in this feature layer.                  |
    | [`Feature`](Feature.md)`[]` | `getFeatures``()`<br>Returns all the features in this feature layer.                       |
    | [`Feature`](Feature.md)`[]` | `getFeaturesOnLink``(long linkId)`<br>Returns the features associated with the input link. |
    | [`Feature`](Feature.md)`[]` | `getFeaturesOnNode``(long nodeId)`<br>Returns the features associated with the input node. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### FeatureLayerImpl

          public FeatureLayerImpl()

      Constructs a FeatureLayer instance.

  <!-- -->

  - ### Method Detail

    - #### addFeature

          public void addFeature(Feature feature)

      Description copied from interface: [`FeatureLayer`](FeatureLayer.md)
      Adds a feature to the feature layer.
      Specified by:
      [`addFeature`](FeatureLayer.md) in interface [`FeatureLayer`](FeatureLayer.md)

    <!-- -->

    - #### getFeature

          public Feature getFeature(long featureId)

      Description copied from interface: [`FeatureLayer`](FeatureLayer.md)
      Returns the feature with the input feature ID.
      Specified by:

      [`getFeature`](FeatureLayer.md) in interface [`FeatureLayer`](FeatureLayer.md)

      Returns:

    <!-- -->

    - #### getFeatures

          public Feature[] getFeatures()

      Description copied from interface: [`FeatureLayer`](FeatureLayer.md)
      Returns all the features in this feature layer.
      Specified by:

      [`getFeatures`](FeatureLayer.md) in interface [`FeatureLayer`](FeatureLayer.md)

      Returns:

    <!-- -->

    - #### getFeaturesOnNode

          public Feature[] getFeaturesOnNode(long nodeId)

      Description copied from interface: [`FeatureLayer`](FeatureLayer.md)
      Returns the features associated with the input node.
      Specified by:

      [`getFeaturesOnNode`](FeatureLayer.md) in interface [`FeatureLayer`](FeatureLayer.md)

      Parameters:

      `nodeId` - ID of the node

      Returns:

    <!-- -->

    - #### getFeaturesOnLink

          public Feature[] getFeaturesOnLink(long linkId)

      Description copied from interface: [`FeatureLayer`](FeatureLayer.md)
      Returns the features associated with the input link.
      Specified by:

      [`getFeaturesOnLink`](FeatureLayer.md) in interface [`FeatureLayer`](FeatureLayer.md)

      Parameters:

      `linkId` - ID of the link

      Returns:

    <!-- -->

    - #### getFeatureIds

          public long[] getFeatureIds()

      Description copied from interface: [`FeatureLayer`](FeatureLayer.md)
      Returns all the feature IDs in this feature layer.
      Specified by:

      [`getFeatureIds`](FeatureLayer.md) in interface [`FeatureLayer`](FeatureLayer.md)

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

- [Prev Class](FeatureLayer.md)
- [Next Class](FeatureLayerMetadata.md)

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
