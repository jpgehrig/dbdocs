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

- [Prev Class](ConflictDescriptor.md)
- [Next Class](FeatureClassDescriptor.md)

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

## Class FeatureAttributeDescriptor

- java.lang.Object

- - oracle.spatial.network.nfe.workspace.FeatureAttributeDescriptor

<!-- -->

-

  ------------------------------------------------------------------------



      public class FeatureAttributeDescriptor
      extends java.lang.Object

  Describes a feature attribute descriptor.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description       |
    |-----------------------------------|
    | `FeatureAttributeDescriptor``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                             | Method and Description                                                                                                                   |
    |-----------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                     | `equals``(java.lang.Object obj)`                                                                                                         |
    | `java.lang.String`                            | `getAttributeChildValue``()`<br>Returns the attribute value in the child workspace.                                                      |
    | `java.lang.String`                            | `getAttributeName``()`<br>Returns the attribute name.                                                                                    |
    | `java.lang.String`                            | `getAttributeParentValue``()`<br>Returns the attribute value in the parent workspace.                                                    |
    | [`ConflictDescriptor`](ConflictDescriptor.md) | `getConflictDescriptor``()`<br>Returns the attribute conflict descriptor if any conflict is related to this attribute, null otherwise.   |
    | [`FeatureDescriptor`](FeatureDescriptor.md)   | `getFeatureDescriptor``()`<br>Returns the feature descriptor.                                                                            |
    | `int`                                         | `hashCode``()`                                                                                                                           |
    | `void`                                        | `setAttributeChildValue``(java.lang.String attributeChildValue)`<br>Sets the attribute value in the child workspace.                     |
    | `void`                                        | `setAttributeName``(java.lang.String attributeName)`<br>Sets the attribute name.                                                         |
    | `void`                                        | `setAttributeParentValue``(java.lang.String attributeParentValue)`<br>Sets the attribute value in the parent workspace.                  |
    | `void`                                        | `setConflictDescriptor``(`[`ConflictDescriptor`](ConflictDescriptor.md)` conflictDescriptor)`<br>Sets the attribute conflict descriptor. |
    | `void`                                        | `setFeatureDescriptor``(`[`FeatureDescriptor`](FeatureDescriptor.md)` featureDescriptor)`<br>Sets the feature descriptor.                |

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### FeatureAttributeDescriptor

          public FeatureAttributeDescriptor()

  <!-- -->

  - ### Method Detail

    - #### getAttributeName

          public java.lang.String getAttributeName()

      Returns the attribute name.
      Returns:
      attribute name

    <!-- -->

    - #### setAttributeName

          public void setAttributeName(java.lang.String attributeName)

      Sets the attribute name.
      Parameters:
      `attributeName` - attribute name

    <!-- -->

    - #### getAttributeChildValue

          public java.lang.String getAttributeChildValue()

      Returns the attribute value in the child workspace.
      Returns:
      attribute value in the child workspace

    <!-- -->

    - #### setAttributeChildValue

          public void setAttributeChildValue(java.lang.String attributeChildValue)

      Sets the attribute value in the child workspace.
      Parameters:
      `attributeChildValue` - attribute value in the child workspace

    <!-- -->

    - #### getAttributeParentValue

          public java.lang.String getAttributeParentValue()

      Returns the attribute value in the parent workspace.
      Returns:
      attribute value in the parent workspace

    <!-- -->

    - #### setAttributeParentValue

          public void setAttributeParentValue(java.lang.String attributeParentValue)

      Sets the attribute value in the parent workspace.
      Parameters:
      `attributeParentValue` - attribute value in the parent workspace

    <!-- -->

    - #### getConflictDescriptor

          public ConflictDescriptor getConflictDescriptor()

      Returns the attribute conflict descriptor if any conflict is related to this attribute, null otherwise.
      Returns:
      attribute conflict descriptor

    <!-- -->

    - #### setConflictDescriptor

          public void setConflictDescriptor(ConflictDescriptor conflictDescriptor)

      Sets the attribute conflict descriptor.
      Parameters:
      `conflictDescriptor` - attribute conflict descriptor.

    <!-- -->

    - #### getFeatureDescriptor

          public FeatureDescriptor getFeatureDescriptor()

      Returns the feature descriptor.
      Returns:
      feature descriptor.

    <!-- -->

    - #### setFeatureDescriptor

          public void setFeatureDescriptor(FeatureDescriptor featureDescriptor)

      Sets the feature descriptor.
      Parameters:
      `featureDescriptor` - feature descriptor

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

- [Prev Class](ConflictDescriptor.md)
- [Next Class](FeatureClassDescriptor.md)

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
