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

- [Prev Class](FeatureData.md)
- [Next Class](FeatureElement.md)

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

## Class FeatureDataImpl

- java.lang.Object

- - oracle.spatial.network.lod.FeatureDataImpl

<!-- -->

- All Implemented Interfaces:
  [FeatureData](FeatureData.md)

  ------------------------------------------------------------------------



      public class FeatureDataImpl
      extends java.lang.Object
      implements FeatureData

  Default implementations for FeatureData.
  Since:
  12.1

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `FeatureDataImpl``()`       |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                 | Method and Description                                                                                                                          |
    |-----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`FeatureLayer`](FeatureLayer.md) | `getFeatureLayer``(int featureLayerId)`<br>Returns the feature data for the input feature layer.                                                |
    | `int[]`                           | `getFeatureLayerIds``()`<br>Returns the feature layer IDs.                                                                                      |
    | `void`                            | `setFeatureLayer``(int featureLayerId, `[`FeatureLayer`](FeatureLayer.md)` featureLayer)`<br>Sets the feature data for the input feature layer. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### FeatureDataImpl

          public FeatureDataImpl()

  <!-- -->

  - ### Method Detail

    - #### getFeatureLayer

          public FeatureLayer getFeatureLayer(int featureLayerId)

      Description copied from interface: [`FeatureData`](FeatureData.md)
      Returns the feature data for the input feature layer.
      Specified by:

      [`getFeatureLayer`](FeatureData.md) in interface [`FeatureData`](FeatureData.md)

      Returns:

    <!-- -->

    - #### setFeatureLayer

          public void setFeatureLayer(int featureLayerId,
                                      FeatureLayer featureLayer)

      Description copied from interface: [`FeatureData`](FeatureData.md)
      Sets the feature data for the input feature layer.
      Specified by:
      [`setFeatureLayer`](FeatureData.md) in interface [`FeatureData`](FeatureData.md)

      Parameters:
      `featureLayerId` - feature layer ID

      `featureLayer` - feature layer object

    <!-- -->

    - #### getFeatureLayerIds

          public int[] getFeatureLayerIds()

      Description copied from interface: [`FeatureData`](FeatureData.md)
      Returns the feature layer IDs.
      Specified by:

      [`getFeatureLayerIds`](FeatureData.md) in interface [`FeatureData`](FeatureData.md)

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

- [Prev Class](FeatureData.md)
- [Next Class](FeatureElement.md)

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
