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

- [Prev Class](FeatureLayerMetadata.FeatureLayerType.md)
- [Next Class](FeaturePath.md)

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

## Class FeatureMetadata

- java.lang.Object

- - oracle.spatial.network.lod.FeatureMetadata

<!-- -->

-

  ------------------------------------------------------------------------



      public class FeatureMetadata
      extends java.lang.Object

  Metadata for all registered feature layers on a network.
  Since:
  12.1

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                 |
    |-------------------------------------------------------------------------------------------------------------|
    | `FeatureMetadata``(java.sql.Connection conn, java.lang.String networkOwner, java.lang.String networkName)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                     | Method and Description                                                                                                                 |
    |-------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|
    | `int[]`                                               | `getFeatureLayerIds``()`<br>Returns feature layer IDs in ascending order.                                                              |
    | [`FeatureLayerMetadata`](FeatureLayerMetadata.md)     | `getFeatureLayerMetadata``(int featureLayerId)`<br>Returns the feature layer metadata for the given feature layer ID.                  |
    | [`FeatureLayerMetadata`](FeatureLayerMetadata.md)     | `getFeatureLayerMetadata``(java.lang.String featureLayerName)`<br>Returns the feature layer metadata for the given feature layer name. |
    | [`FeatureLayerMetadata`](FeatureLayerMetadata.md)`[]` | `getFeatureLayerMetadataOrderById``()`<br>Returns the feature layer metadata array sorted by feature layer name.                       |
    | [`FeatureLayerMetadata`](FeatureLayerMetadata.md)`[]` | `getFeatureLayerMetadataOrderByName``()`<br>Returns the feature layer metadata array sorted by feature layer name.                     |
    | `java.lang.String[]`                                  | `getFeatureLayerNames``()`<br>Returns feature layer names in ascending order.                                                          |
    | `int`                                                 | `getNumberOfFeatureLayers``()`<br>Returns the number of feature layers.                                                                |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### FeatureMetadata

          public FeatureMetadata(java.sql.Connection conn,
                                 java.lang.String networkOwner,
                                 java.lang.String networkName)
                          throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

  <!-- -->

  - ### Method Detail

    - #### getNumberOfFeatureLayers

          public int getNumberOfFeatureLayers()

      Returns the number of feature layers.

    <!-- -->

    - #### getFeatureLayerIds

          public int[] getFeatureLayerIds()

      Returns feature layer IDs in ascending order.
      Returns:

    <!-- -->

    - #### getFeatureLayerNames

          public java.lang.String[] getFeatureLayerNames()

      Returns feature layer names in ascending order.
      Returns:

    <!-- -->

    - #### getFeatureLayerMetadata

          public FeatureLayerMetadata getFeatureLayerMetadata(int featureLayerId)

      Returns the feature layer metadata for the given feature layer ID.
      Parameters:

      `featureLayerId` -

      Returns:

    <!-- -->

    - #### getFeatureLayerMetadata

          public FeatureLayerMetadata getFeatureLayerMetadata(java.lang.String featureLayerName)

      Returns the feature layer metadata for the given feature layer name.
      Parameters:

      `featureLayerName` -

      Returns:

    <!-- -->

    - #### getFeatureLayerMetadataOrderByName

          public FeatureLayerMetadata[] getFeatureLayerMetadataOrderByName()

      Returns the feature layer metadata array sorted by feature layer name.
      Returns:

    <!-- -->

    - #### getFeatureLayerMetadataOrderById

          public FeatureLayerMetadata[] getFeatureLayerMetadataOrderById()

      Returns the feature layer metadata array sorted by feature layer name.
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

- [Prev Class](FeatureLayerMetadata.FeatureLayerType.md)
- [Next Class](FeaturePath.md)

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
