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

- [Prev Class](BehavioralLayer.md)
- [Next Class](SelectionEditableLayer.md)

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

oracle.spatial.network.nfe.vis.mapcanvas.behavior

## Interface FeatureSelectableLayer

- All Superinterfaces:
  [BehavioralLayer](BehavioralLayer.md)

  <!-- -->

  All Known Implementing Classes:
  [NFEFeatureLayerRenderer](../render/NFEFeatureLayerRenderer.md), [NFEManipulableFeatureLayerRenderer](../render/NFEManipulableFeatureLayerRenderer.md)

  ------------------------------------------------------------------------



      public interface FeatureSelectableLayer
      extends BehavioralLayer

  Defines a feature layer which features can be selected.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                              | Method and Description                                                                                           |
    |--------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------|
    | `java.util.Collection<`[`NFEFeature`](../../../model/feature/NFEFeature.md)`>` | `getSelectedFeatures``()`<br>Gets the currently selected features                                                |
    | `void`                                                                         | `selectFeatures``(java.util.Collection<java.lang.Long> featureIds)`<br>Selects a group of features.              |
    | `void`                                                                         | `setFeatureSelection``(java.util.Collection<java.lang.Long> featureIds)`<br>Sets the given features as selected. |

    - ### Methods inherited from interface oracle.spatial.network.nfe.vis.mapcanvas.behavior.[BehavioralLayer](BehavioralLayer.md)

      [`refresh`](BehavioralLayer.md)

<!-- -->

- - ### Method Detail

    - #### selectFeatures

          void selectFeatures(java.util.Collection<java.lang.Long> featureIds)

      Selects a group of features. If there were selected features selected, they are still selected.
      Parameters:
      `featureIds` - a collection containing the IDs of the features to be selected

    <!-- -->

    - #### setFeatureSelection

          void setFeatureSelection(java.util.Collection<java.lang.Long> featureIds)

      Sets the given features as selected. Previously selected features are unselected
      Parameters:
      `featureIds` - a collection of feature IDs to be selected

    <!-- -->

    - #### getSelectedFeatures

          java.util.Collection<NFEFeature> getSelectedFeatures()

      Gets the currently selected features
      Returns:
      a collection of features

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

- [Prev Class](BehavioralLayer.md)
- [Next Class](SelectionEditableLayer.md)

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
