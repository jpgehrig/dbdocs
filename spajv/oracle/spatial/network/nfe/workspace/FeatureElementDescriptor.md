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

- [Prev Class](FeatureDescriptor.md)
- [Next Class](FeatureLayerDescriptor.md)

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

## Class FeatureElementDescriptor

- java.lang.Object

- - oracle.spatial.network.nfe.workspace.FeatureElementDescriptor

<!-- -->

-

  ------------------------------------------------------------------------



      public class FeatureElementDescriptor
      extends java.lang.Object

  Describes a feature element or a network element that is part of a feature descriptor. FeatureElementDescriptor doesn't map directly feature elements in database. FeatureElementDescriptor can refer to feature elements in database or can be use to describe network elements.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description     |
    |---------------------------------|
    | `FeatureElementDescriptor``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                             | Method and Description                                                                                                             |
    |-----------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                     | `equals``(java.lang.Object obj)`                                                                                                   |
    | [`ConflictDescriptor`](ConflictDescriptor.md) | `getConflictDescriptor``()`<br>Returns the conflict descriptor if any conflict is related to this feature element, null otherwise. |
    | `java.lang.Integer`                           | `getElementType``()`<br>Returns the feature element type.                                                                          |
    | [`LinkDescriptor`](LinkDescriptor.md)         | `getLinkDescriptor``()`<br>Returns the link descriptor if the network element is a link, null otherwise.                           |
    | `java.lang.Long`                              | `getNetElementId``()`<br>Returns the network element identifier.                                                                   |
    | [`NodeDescriptor`](NodeDescriptor.md)         | `getNodeDescriptor``()`<br>Returns the node descriptor if the network element is a node, null otherwise.                           |
    | `java.lang.Integer`                           | `getSequence``()`<br>Returns the feature element sequence.                                                                         |
    | `int`                                         | `hashCode``()`                                                                                                                     |
    | `boolean`                                     | `isNode``()`<br>Returns true if the network element is a node, false otherwise.                                                    |
    | `void`                                        | `setConflictDescriptor``(`[`ConflictDescriptor`](ConflictDescriptor.md)` conflictDescriptor)`<br>Sets the conflict descriptor.     |
    | `void`                                        | `setElementType``(java.lang.Integer elementType)`<br>Sets the feature element type.                                                |
    | `void`                                        | `setLinkDescriptor``(`[`LinkDescriptor`](LinkDescriptor.md)` linkDescriptor)`<br>Sets the link descriptor.                         |
    | `void`                                        | `setNetElementId``(java.lang.Long netElementId)`<br>Sets the network element identifier.                                           |
    | `void`                                        | `setNodeDescriptor``(`[`NodeDescriptor`](NodeDescriptor.md)` nodeDescriptor)`<br>Sets the node descriptor.                         |
    | `void`                                        | `setSequence``(java.lang.Integer sequence)`<br>Sets the feature element sequence.                                                  |

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### FeatureElementDescriptor

          public FeatureElementDescriptor()

  <!-- -->

  - ### Method Detail

    - #### getConflictDescriptor

          public ConflictDescriptor getConflictDescriptor()

      Returns the conflict descriptor if any conflict is related to this feature element, null otherwise.
      Returns:
      conflict descriptor

    <!-- -->

    - #### setConflictDescriptor

          public void setConflictDescriptor(ConflictDescriptor conflictDescriptor)

      Sets the conflict descriptor.
      Parameters:
      `conflictDescriptor` - conflict descriptor

    <!-- -->

    - #### getNodeDescriptor

          public NodeDescriptor getNodeDescriptor()

      Returns the node descriptor if the network element is a node, null otherwise.
      Returns:
      node descriptor

    <!-- -->

    - #### setNodeDescriptor

          public void setNodeDescriptor(NodeDescriptor nodeDescriptor)

      Sets the node descriptor.
      Parameters:
      `nodeDescriptor` - node descriptor

    <!-- -->

    - #### getLinkDescriptor

          public LinkDescriptor getLinkDescriptor()

      Returns the link descriptor if the network element is a link, null otherwise.
      Returns:
      link descriptor

    <!-- -->

    - #### setLinkDescriptor

          public void setLinkDescriptor(LinkDescriptor linkDescriptor)

      Sets the link descriptor.
      Parameters:
      `linkDescriptor` - link descriptor

    <!-- -->

    - #### getElementType

          public java.lang.Integer getElementType()

      Returns the feature element type. Feature element type is one of the following: 1 point on node, 2 point on link, 3 line.
      Returns:
      feature element type

    <!-- -->

    - #### setElementType

          public void setElementType(java.lang.Integer elementType)

      Sets the feature element type.
      Parameters:
      `elementType` - element type

    <!-- -->

    - #### getNetElementId

          public java.lang.Long getNetElementId()

      Returns the network element identifier.
      Returns:
      network element identifier

    <!-- -->

    - #### setNetElementId

          public void setNetElementId(java.lang.Long netElementId)

      Sets the network element identifier.
      Parameters:
      `netElementId` - network element identifier

    <!-- -->

    - #### isNode

          public boolean isNode()

      Returns true if the network element is a node, false otherwise.
      Returns:
      true if the network element is a node, false otherwise

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

    - #### getSequence

          public java.lang.Integer getSequence()

      Returns the feature element sequence.
      Returns:
      feature element sequence

    <!-- -->

    - #### setSequence

          public void setSequence(java.lang.Integer sequence)

      Sets the feature element sequence.
      Parameters:
      `sequence` - feature element sequence

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

- [Prev Class](FeatureDescriptor.md)
- [Next Class](FeatureLayerDescriptor.md)

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
