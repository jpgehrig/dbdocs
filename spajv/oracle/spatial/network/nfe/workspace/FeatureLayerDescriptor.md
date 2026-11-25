Skip navigation links

- [Overview](../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](FeatureElementDescriptor.md)
- [Next Class](LinkDescriptor.md)

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.workspace

## Class FeatureLayerDescriptor

- java.lang.Object

- - oracle.spatial.network.nfe.workspace.FeatureLayerDescriptor

<!-- -->

-

  ------------------------------------------------------------------------



      public class FeatureLayerDescriptor
      extends java.lang.Object

  Describes a feature layer with features involved in a conflict.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description   |
    |-------------------------------|
    | `FeatureLayerDescriptor``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                         | Method and Description                                                                                                                                                       |
    |---------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                                                 | `equals``(java.lang.Object obj)`                                                                                                                                             |
    | `java.lang.Integer`                                                       | `getConflictsNumber``()`<br>Returns the number of conflicts.                                                                                                                 |
    | `java.util.List<`[`FeatureClassDescriptor`](FeatureClassDescriptor.md)`>` | `getFeatureClassDescriptorList``()`<br>Returns the feature class descriptors.                                                                                                |
    | `java.lang.Long`                                                          | `getFeatureLayerId``()`<br>Returns the feature layer identifier.                                                                                                             |
    | `java.lang.Integer`                                                       | `getFeaturesNumber``()`<br>Returns the number of features in conflict.                                                                                                       |
    | [`NFEFeatureLayer`](../model/feature/NFEFeatureLayer.md)                  | `getNfeFeatureLayer``()`<br>Returns the NFE feature layer.                                                                                                                   |
    | `int`                                                                     | `hashCode``()`                                                                                                                                                               |
    | `void`                                                                    | `setFeatureClassDescriptorList``(java.util.List<`[`FeatureClassDescriptor`](FeatureClassDescriptor.md)`> featureClassDescriptorList)`<br>Sets the feature class descriptors. |
    | `void`                                                                    | `setFeatureLayerId``(java.lang.Long featureLayerId)`<br>Sets the feature layer identifier.                                                                                   |
    | `void`                                                                    | `setNfeFeatureLayer``(`[`NFEFeatureLayer`](../model/feature/NFEFeatureLayer.md)` nfeFeatureLayer)`<br>Sets the NFE feature layer.                                            |

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### FeatureLayerDescriptor

          public FeatureLayerDescriptor()

  <!-- -->

  - ### Method Detail

    - #### getFeatureLayerId

          public java.lang.Long getFeatureLayerId()

      Returns the feature layer identifier.
      Returns:
      feature layer identifier

    <!-- -->

    - #### setFeatureLayerId

          public void setFeatureLayerId(java.lang.Long featureLayerId)

      Sets the feature layer identifier.
      Parameters:
      `featureLayerId` - feature layer identifier

    <!-- -->

    - #### getFeatureClassDescriptorList

          public java.util.List<FeatureClassDescriptor> getFeatureClassDescriptorList()

      Returns the feature class descriptors.
      Returns:
      feature class descriptors

    <!-- -->

    - #### setFeatureClassDescriptorList

          public void setFeatureClassDescriptorList(java.util.List<FeatureClassDescriptor> featureClassDescriptorList)

      Sets the feature class descriptors.
      Parameters:
      `featureClassDescriptorList` - feature class descriptors

    <!-- -->

    - #### getNfeFeatureLayer

          public NFEFeatureLayer getNfeFeatureLayer()

      Returns the NFE feature layer.
      Returns:
      NFE feature layer

    <!-- -->

    - #### setNfeFeatureLayer

          public void setNfeFeatureLayer(NFEFeatureLayer nfeFeatureLayer)

      Sets the NFE feature layer.
      Parameters:
      `nfeFeatureLayer` - NFE feature layer

    <!-- -->

    - #### hashCode

          public int hashCode()

      Overrides:
      `hashCode` in class `java.lang.Object`

    <!-- -->

    - #### equals

          public boolean equals(java.lang.Object obj)

      Overrides:
      `equals` in class `java.lang.Object`

    <!-- -->

    - #### getConflictsNumber

          public java.lang.Integer getConflictsNumber()

      Returns the number of conflicts.
      Returns:
      number of conflicts

    <!-- -->

    - #### getFeaturesNumber

          public java.lang.Integer getFeaturesNumber()

      Returns the number of features in conflict. Some features can group a conflict region.
      Returns:
      number of features.

Skip navigation links

- [Overview](../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](FeatureElementDescriptor.md)
- [Next Class](LinkDescriptor.md)

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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
