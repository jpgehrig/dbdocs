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

- [Prev Class](FeatureClassDescriptor.md)
- [Next Class](FeatureElementDescriptor.md)

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

## Class FeatureDescriptor

- java.lang.Object

- - oracle.spatial.network.nfe.workspace.FeatureDescriptor

<!-- -->

- All Implemented Interfaces:
  java.lang.Comparable

  ------------------------------------------------------------------------



      public class FeatureDescriptor
      extends java.lang.Object
      implements java.lang.Comparable

  Describes a feature involve in a conflict.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `FeatureDescriptor``()`     |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                 | Method and Description                                                                                                                                                                            |
    |-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`                                                                             | `compareTo``(java.lang.Object o)`                                                                                                                                                                 |
    | `boolean`                                                                         | `equals``(java.lang.Object obj)`                                                                                                                                                                  |
    | `java.lang.Integer`                                                               | `getConflictsNumber``()`<br>Returns the number of attributes in conflict.                                                                                                                         |
    | `java.lang.Integer`                                                               | `getConflictsNumberWithoutShape``()`<br>Returns the number of non shape attributes in conflict.                                                                                                   |
    | `java.util.List<`[`FeatureAttributeDescriptor`](FeatureAttributeDescriptor.md)`>` | `getFeatureAttributeDescriptorList``()`<br>Returns the feature attributes descriptors.                                                                                                            |
    | [`FeatureClassDescriptor`](FeatureClassDescriptor.md)                             | `getFeatureClassDescriptor``()`<br>Returns the feature class descriptor.                                                                                                                          |
    | `java.util.List<`[`FeatureElementDescriptor`](FeatureElementDescriptor.md)`>`     | `getFeatureElementDescriptorList``()`<br>Returns the feature element descriptors.                                                                                                                 |
    | `java.lang.Long`                                                                  | `getFeatureId``()`<br>Returns the feature identifier.                                                                                                                                             |
    | `java.util.List<java.lang.Long>`                                                  | `getImpactedNodesIds``()`<br>Returns the nodes identifiers that directly are part of the conflict or that are the start or end of a link that is in conflict.                                     |
    | `java.util.List<java.lang.Long>`                                                  | `getInvolvedNodesIds``()`<br>Returns the nodes identifiers that belongs to the feature and conflict regions.                                                                                      |
    | `int`                                                                             | `hashCode``()`                                                                                                                                                                                    |
    | `void`                                                                            | `setFeatureAttributeDescriptorList``(java.util.List<`[`FeatureAttributeDescriptor`](FeatureAttributeDescriptor.md)`> featureAttributeDescriptorList)`<br>Sets the feature attributes descriptors. |
    | `void`                                                                            | `setFeatureClassDescriptor``(`[`FeatureClassDescriptor`](FeatureClassDescriptor.md)` featureClassDescriptor)`<br>Sets the feature class descriptor.                                               |
    | `void`                                                                            | `setFeatureElementDescriptorList``(java.util.List<`[`FeatureElementDescriptor`](FeatureElementDescriptor.md)`> featureElementDescriptorList)`<br>Sets the feature elements descriptors.           |
    | `void`                                                                            | `setFeatureId``(java.lang.Long featureId)`<br>Sets the feature identifier.                                                                                                                        |
    | `java.lang.String`                                                                | `toString``()`                                                                                                                                                                                    |

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### FeatureDescriptor

          public FeatureDescriptor()

  <!-- -->

  - ### Method Detail

    - #### getFeatureId

          public java.lang.Long getFeatureId()

      Returns the feature identifier.
      Returns:
      feature identifier

    <!-- -->

    - #### setFeatureId

          public void setFeatureId(java.lang.Long featureId)

      Sets the feature identifier.
      Parameters:
      `featureId` - feature identifier

    <!-- -->

    - #### getFeatureAttributeDescriptorList

          public java.util.List<FeatureAttributeDescriptor> getFeatureAttributeDescriptorList()

      Returns the feature attributes descriptors.
      Returns:
      feature attributes descriptors

    <!-- -->

    - #### setFeatureAttributeDescriptorList

          public void setFeatureAttributeDescriptorList(java.util.List<FeatureAttributeDescriptor> featureAttributeDescriptorList)

      Sets the feature attributes descriptors.
      Parameters:
      `featureAttributeDescriptorList` - feature attributes descriptors

    <!-- -->

    - #### getFeatureElementDescriptorList

          public java.util.List<FeatureElementDescriptor> getFeatureElementDescriptorList()

      Returns the feature element descriptors.
      Returns:
      feature element descriptors

    <!-- -->

    - #### setFeatureElementDescriptorList

          public void setFeatureElementDescriptorList(java.util.List<FeatureElementDescriptor> featureElementDescriptorList)

      Sets the feature elements descriptors.
      Parameters:
      `featureElementDescriptorList` - feature elements descriptors

    <!-- -->

    - #### getFeatureClassDescriptor

          public FeatureClassDescriptor getFeatureClassDescriptor()

      Returns the feature class descriptor.
      Returns:
      feature class descriptor

    <!-- -->

    - #### setFeatureClassDescriptor

          public void setFeatureClassDescriptor(FeatureClassDescriptor featureClassDescriptor)

      Sets the feature class descriptor.
      Parameters:
      `featureClassDescriptor` - feature class descriptor

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Object`

    <!-- -->

    - #### getConflictsNumber

          public java.lang.Integer getConflictsNumber()

      Returns the number of attributes in conflict.
      Returns:
      number of attributes in conflict

    <!-- -->

    - #### getConflictsNumberWithoutShape

          public java.lang.Integer getConflictsNumberWithoutShape()

      Returns the number of non shape attributes in conflict.
      Returns:
      number of non shape attributes in conflict

    <!-- -->

    - #### getInvolvedNodesIds

          public java.util.List<java.lang.Long> getInvolvedNodesIds()

      Returns the nodes identifiers that belongs to the feature and conflict regions. It can be used to get the minimum bounding rectangle (MBR) of the conflict for example. The nodes returned will belong to any conflictive network element or to any element that logically links conflictive elements.
      Returns:
      nodes identifiers

    <!-- -->

    - #### getImpactedNodesIds

          public java.util.List<java.lang.Long> getImpactedNodesIds()

      Returns the nodes identifiers that directly are part of the conflict or that are the start or end of a link that is in conflict.
      Returns:
      nodes identifiers

    <!-- -->

    - #### compareTo

          public int compareTo(java.lang.Object o)

      Specified by:
      `compareTo` in interface `java.lang.Comparable`

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

- [Prev Class](FeatureClassDescriptor.md)
- [Next Class](FeatureElementDescriptor.md)

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
