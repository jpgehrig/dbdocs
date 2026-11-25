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

- [Prev Class](FeatureLayerDescriptor.md)
- [Next Class](NFEConflictsDescriptor.md)

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

## Class LinkDescriptor

- java.lang.Object

- - oracle.spatial.network.nfe.workspace.LinkDescriptor

<!-- -->

-

  ------------------------------------------------------------------------



      public class LinkDescriptor
      extends java.lang.Object

  Describes a link.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `LinkDescriptor``()`        |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                             | Method and Description                                                                                                         |
    |-----------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                     | `equals``(java.lang.Object obj)`                                                                                               |
    | [`ConflictDescriptor`](ConflictDescriptor.md) | `getConflictDescriptor``()`<br>Returns the link conflict descriptor.                                                           |
    | `java.lang.Long`                              | `getEndNodeIdChild``()`<br>Returns the end node identifier of the child workspace.                                             |
    | `java.lang.Long`                              | `getEndNodeIdParent``()`<br>Returns the end node identifier of the parent workspace.                                           |
    | `java.lang.Long`                              | `getLinkId``()`<br>Returns the link identifier.                                                                                |
    | `java.lang.Long`                              | `getStartNodeIdChild``()`<br>Returns the start node identifier of the child workspace.                                         |
    | `java.lang.Long`                              | `getStartNodeIdParent``()`<br>Returns the start node identifier of the parent workspace.                                       |
    | `int`                                         | `hashCode``()`                                                                                                                 |
    | `void`                                        | `setConflictDescriptor``(`[`ConflictDescriptor`](ConflictDescriptor.md)` conflictDescriptor)`<br>Sets the conflict descriptor. |
    | `void`                                        | `setEndNodeIdChild``(java.lang.Long endNodeIdChild)`<br>Sets the end node identifier of the child workspace.                   |
    | `void`                                        | `setEndNodeIdParent``(java.lang.Long endNodeIdParent)`<br>Sets the end node identifier of the parent workspace.                |
    | `void`                                        | `setLinkId``(java.lang.Long linkId)`<br>Sets the link identifier.                                                              |
    | `void`                                        | `setStartNodeIdChild``(java.lang.Long startNodeIdChild)`<br>Sets the start node identifier of the child workspace.             |
    | `void`                                        | `setStartNodeIdParent``(java.lang.Long startNodeIdParent)`<br>Sets the start node identifier of the parent workspace.          |

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### LinkDescriptor

          public LinkDescriptor()

  <!-- -->

  - ### Method Detail

    - #### getLinkId

          public java.lang.Long getLinkId()

      Returns the link identifier.
      Returns:
      link identifier

    <!-- -->

    - #### setLinkId

          public void setLinkId(java.lang.Long linkId)

      Sets the link identifier.
      Parameters:
      `linkId` - link identifier

    <!-- -->

    - #### getStartNodeIdChild

          public java.lang.Long getStartNodeIdChild()

      Returns the start node identifier of the child workspace.
      Returns:
      start node identifier of the child workspace

    <!-- -->

    - #### setStartNodeIdChild

          public void setStartNodeIdChild(java.lang.Long startNodeIdChild)

      Sets the start node identifier of the child workspace.
      Parameters:
      `startNodeIdChild` - start node identifier of the child workspace

    <!-- -->

    - #### getEndNodeIdChild

          public java.lang.Long getEndNodeIdChild()

      Returns the end node identifier of the child workspace.
      Returns:
      end node identifier of the child workspace

    <!-- -->

    - #### setEndNodeIdChild

          public void setEndNodeIdChild(java.lang.Long endNodeIdChild)

      Sets the end node identifier of the child workspace.
      Parameters:
      `endNodeIdChild` - end node identifier of the child workspace

    <!-- -->

    - #### getStartNodeIdParent

          public java.lang.Long getStartNodeIdParent()

      Returns the start node identifier of the parent workspace.
      Returns:
      start node identifier of the parent workspace

    <!-- -->

    - #### setStartNodeIdParent

          public void setStartNodeIdParent(java.lang.Long startNodeIdParent)

      Sets the start node identifier of the parent workspace.
      Parameters:
      `startNodeIdParent` - start node identifier of the parent workspace

    <!-- -->

    - #### getEndNodeIdParent

          public java.lang.Long getEndNodeIdParent()

      Returns the end node identifier of the parent workspace.
      Returns:
      end node identifier of the parent workspace

    <!-- -->

    - #### setEndNodeIdParent

          public void setEndNodeIdParent(java.lang.Long endNodeIdParent)

      Sets the end node identifier of the parent workspace.
      Parameters:
      `endNodeIdParent` - end node identifier of the parent workspace

    <!-- -->

    - #### getConflictDescriptor

          public ConflictDescriptor getConflictDescriptor()

      Returns the link conflict descriptor. Return null if the link has no conflicts.
      Returns:
      conflict descriptor

    <!-- -->

    - #### setConflictDescriptor

          public void setConflictDescriptor(ConflictDescriptor conflictDescriptor)

      Sets the conflict descriptor.
      Parameters:
      `conflictDescriptor` - conflict descriptor

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

- [Prev Class](FeatureLayerDescriptor.md)
- [Next Class](NFEConflictsDescriptor.md)

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
