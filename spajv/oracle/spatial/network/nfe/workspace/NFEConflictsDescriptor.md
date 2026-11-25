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

- [Prev Class](LinkDescriptor.md)
- [Next Class](NodeDescriptor.md)

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

## Class NFEConflictsDescriptor

- java.lang.Object

- - oracle.spatial.network.nfe.workspace.NFEConflictsDescriptor

<!-- -->

-

  ------------------------------------------------------------------------



      public class NFEConflictsDescriptor
      extends java.lang.Object

  Class describing the NFE conflicts.
  The data will follow the structure:

       NFEConflictDescriptor
              featureLayerDescriptors
                      featureClassDescriptors
                              featureDescriptors
                                      attributeDescriptors
                                              conflictDescriptor


  The non conflictive attributes will have conflictDescriptor set to null.
  It is possible to resolve the attributes one by one or grouped.
  To resolve an attribute conflict call the function nfeWorkspaceIOService.resolveConflicts with as parameter the attributes and the information about the child, parent and chosen workspace.

  If the model is in from scratch mode the feature can group conflict regions in case of shape conflicts.
  For example if a link is in conflict and a node linked to this link is also in conflict they will be group in a single conflict.
  Note that he function featureDescriptor.getInvolvedNodesIds will return the involved nodes in a conflict. It can be used to get the minimum bounding rectangle (MBR) of the conflict for example.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description   |
    |-------------------------------|
    | `NFEConflictsDescriptor``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                         | Method and Description                                                                                                                                                        |
    |---------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Integer`                                                       | `getConflictsNumber``()`<br>Returns the number of conflicts.                                                                                                                  |
    | `java.util.List<`[`FeatureLayerDescriptor`](FeatureLayerDescriptor.md)`>` | `getFeatureLayerDescriptorList``()`<br>Returns the feature layers descriptors.                                                                                                |
    | `java.lang.Integer`                                                       | `getFeaturesNumber``()`<br>Returns the number of features in conflict.                                                                                                        |
    | `void`                                                                    | `setFeatureLayerDescriptorList``(java.util.List<`[`FeatureLayerDescriptor`](FeatureLayerDescriptor.md)`> featureLayerDescriptorList)`<br>Sets the feature layers descriptors. |
    | `java.lang.String`                                                        | `toString``()`                                                                                                                                                                |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEConflictsDescriptor

          public NFEConflictsDescriptor()

  <!-- -->

  - ### Method Detail

    - #### getFeatureLayerDescriptorList

          public java.util.List<FeatureLayerDescriptor> getFeatureLayerDescriptorList()

      Returns the feature layers descriptors.
      Returns:
      feature layers descriptors

    <!-- -->

    - #### setFeatureLayerDescriptorList

          public void setFeatureLayerDescriptorList(java.util.List<FeatureLayerDescriptor> featureLayerDescriptorList)

      Sets the feature layers descriptors.
      Parameters:
      `featureLayerDescriptorList` - feature layers descriptors

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Object`

    <!-- -->

    - #### getConflictsNumber

          public java.lang.Integer getConflictsNumber()

      Returns the number of conflicts.
      Returns:
      number of conflicts

    <!-- -->

    - #### getFeaturesNumber

          public java.lang.Integer getFeaturesNumber()

      Returns the number of features in conflict. Note that some features can group a conflict region.
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

- [Prev Class](LinkDescriptor.md)
- [Next Class](NodeDescriptor.md)

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
