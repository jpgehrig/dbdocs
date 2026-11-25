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

- [Prev Class](FeatureAttributeDescriptor.md)
- [Next Class](FeatureDescriptor.md)

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

## Class FeatureClassDescriptor

- java.lang.Object

- - oracle.spatial.network.nfe.workspace.FeatureClassDescriptor

<!-- -->

- All Implemented Interfaces:
  java.lang.Comparable

  ------------------------------------------------------------------------



      public class FeatureClassDescriptor
      extends java.lang.Object
      implements java.lang.Comparable

  Describes a feature class with features involved in a conflict.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description   |
    |-------------------------------|
    | `FeatureClassDescriptor``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                               | Method and Description                                                                                                                                                 |
    |-----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`                                                           | `compareTo``(java.lang.Object o)`                                                                                                                                      |
    | `boolean`                                                       | `equals``(java.lang.Object obj)`                                                                                                                                       |
    | `java.lang.Integer`                                             | `getConflictsNumber``()`<br>Returns the number of conflicts.                                                                                                           |
    | `java.lang.Long`                                                | `getFeatureClassId``()`<br>Returns the feature class identifier.                                                                                                       |
    | `java.lang.String`                                              | `getFeatureClassName``()`<br>Returns the feature class name.                                                                                                           |
    | `java.util.List<`[`FeatureDescriptor`](FeatureDescriptor.md)`>` | `getFeatureDescriptorList``()`<br>Returns the list of features involved in a conflict.                                                                                 |
    | [`FeatureLayerDescriptor`](FeatureLayerDescriptor.md)           | `getFeatureLayerDescriptor``()`<br>Returns the feature layer descriptor.                                                                                               |
    | `java.lang.Integer`                                             | `getFeaturesNumber``()`<br>Returns the number of features in conflict.                                                                                                 |
    | `int`                                                           | `hashCode``()`                                                                                                                                                         |
    | `void`                                                          | `setFeatureClassId``(java.lang.Long featureClassId)`<br>Sets the feature class identifier.                                                                             |
    | `void`                                                          | `setFeatureClassName``(java.lang.String featureClassName)`<br>Sets the feature class name.                                                                             |
    | `void`                                                          | `setFeatureDescriptorList``(java.util.List<`[`FeatureDescriptor`](FeatureDescriptor.md)`> featureDescriptorList)`<br>Sets the list of features involved in a conflict. |
    | `void`                                                          | `setFeatureLayerDescriptor``(`[`FeatureLayerDescriptor`](FeatureLayerDescriptor.md)` featureLayerDescriptor)`<br>Sets the feature layer descriptor.                    |
    | `java.lang.String`                                              | `toString``()`                                                                                                                                                         |

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### FeatureClassDescriptor

          public FeatureClassDescriptor()

  <!-- -->

  - ### Method Detail

    - #### getFeatureClassId

          public java.lang.Long getFeatureClassId()

      Returns the feature class identifier.
      Returns:
      feature class identifier

    <!-- -->

    - #### setFeatureClassId

          public void setFeatureClassId(java.lang.Long featureClassId)

      Sets the feature class identifier.
      Parameters:
      `featureClassId` - feature class identifier

    <!-- -->

    - #### getFeatureClassName

          public java.lang.String getFeatureClassName()

      Returns the feature class name.
      Returns:
      feature class name

    <!-- -->

    - #### setFeatureClassName

          public void setFeatureClassName(java.lang.String featureClassName)

      Sets the feature class name.
      Parameters:
      `featureClassName` - feature class name

    <!-- -->

    - #### getFeatureDescriptorList

          public java.util.List<FeatureDescriptor> getFeatureDescriptorList()

      Returns the list of features involved in a conflict.
      Returns:
      list of features

    <!-- -->

    - #### setFeatureDescriptorList

          public void setFeatureDescriptorList(java.util.List<FeatureDescriptor> featureDescriptorList)

      Sets the list of features involved in a conflict.
      Parameters:
      `featureDescriptorList` - list of features

    <!-- -->

    - #### getFeatureLayerDescriptor

          public FeatureLayerDescriptor getFeatureLayerDescriptor()

      Returns the feature layer descriptor.
      Returns:
      feature layer descriptor.

    <!-- -->

    - #### setFeatureLayerDescriptor

          public void setFeatureLayerDescriptor(FeatureLayerDescriptor featureLayerDescriptor)

      Sets the feature layer descriptor.
      Parameters:
      `featureLayerDescriptor` - feature layer descriptor

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

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Object`

    <!-- -->

    - #### compareTo

          public int compareTo(java.lang.Object o)

      Specified by:
      `compareTo` in interface `java.lang.Comparable`

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

- [Prev Class](FeatureAttributeDescriptor.md)
- [Next Class](FeatureDescriptor.md)

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
