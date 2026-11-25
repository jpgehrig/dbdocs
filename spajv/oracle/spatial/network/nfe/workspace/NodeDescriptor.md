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

- [Prev Class](NFEConflictsDescriptor.md)
- Next Class

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

## Class NodeDescriptor

- java.lang.Object

- - oracle.spatial.network.nfe.workspace.NodeDescriptor

<!-- -->

-

  ------------------------------------------------------------------------



      public class NodeDescriptor
      extends java.lang.Object

  Describes a node. The node can be the related to more nodes and links in case of a shape conflict.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `NodeDescriptor``()`        |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                         | Method and Description                                                                                                                                                                                 |
    |-----------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                                 | `equals``(java.lang.Object obj)`                                                                                                                                                                       |
    | [`ConflictDescriptor`](ConflictDescriptor.md)             | `getConflictDescriptor``()`<br>Returns the conflict descriptor.                                                                                                                                        |
    | `java.util.List<`[`LinkDescriptor`](LinkDescriptor.md)`>` | `getImpactedLinkDescriptorList``()`<br>Returns the links that belongs to the same conflict in case of a conflict group.                                                                                |
    | `java.util.List<NodeDescriptor>`                          | `getImpactedNodeDescriptorList``()`<br>Returns the nodes that belongs to the same conflict in case of a conflict group.                                                                                |
    | `java.lang.Long`                                          | `getNodeId``()`<br>Returns the node identifier.                                                                                                                                                        |
    | `int`                                                     | `hashCode``()`                                                                                                                                                                                         |
    | `void`                                                    | `setConflictDescriptor``(`[`ConflictDescriptor`](ConflictDescriptor.md)` conflictDescriptor)`<br>Sets the conflict descriptor.                                                                         |
    | `void`                                                    | `setImpactedLinkDescriptorList``(java.util.List<`[`LinkDescriptor`](LinkDescriptor.md)`> impactedLinkDescriptorList)`<br>Sets the links that belongs to the same conflict in case of a conflict group. |
    | `void`                                                    | `setImpactedNodeDescriptorList``(java.util.List<NodeDescriptor> impactedNodeDescriptorList)`<br>Sets the nodes that belongs to the same conflict in case of a conflict group.                          |
    | `void`                                                    | `setNodeId``(java.lang.Long nodeId)`<br>Sets the node identifier.                                                                                                                                      |

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NodeDescriptor

          public NodeDescriptor()

  <!-- -->

  - ### Method Detail

    - #### getImpactedNodeDescriptorList

          public java.util.List<NodeDescriptor> getImpactedNodeDescriptorList()

      Returns the nodes that belongs to the same conflict in case of a conflict group.
      Returns:
      nodes descriptors

    <!-- -->

    - #### setImpactedNodeDescriptorList

          public void setImpactedNodeDescriptorList(java.util.List<NodeDescriptor> impactedNodeDescriptorList)

      Sets the nodes that belongs to the same conflict in case of a conflict group.
      Parameters:
      `impactedNodeDescriptorList` - nodes descriptors

    <!-- -->

    - #### getImpactedLinkDescriptorList

          public java.util.List<LinkDescriptor> getImpactedLinkDescriptorList()

      Returns the links that belongs to the same conflict in case of a conflict group.
      Returns:
      links descriptors

    <!-- -->

    - #### setImpactedLinkDescriptorList

          public void setImpactedLinkDescriptorList(java.util.List<LinkDescriptor> impactedLinkDescriptorList)

      Sets the links that belongs to the same conflict in case of a conflict group.
      Parameters:
      `impactedLinkDescriptorList` - links descriptors

    <!-- -->

    - #### getNodeId

          public java.lang.Long getNodeId()

      Returns the node identifier.
      Returns:
      node identifier

    <!-- -->

    - #### setNodeId

          public void setNodeId(java.lang.Long nodeId)

      Sets the node identifier.
      Parameters:
      `nodeId` - node identifier

    <!-- -->

    - #### getConflictDescriptor

          public ConflictDescriptor getConflictDescriptor()

      Returns the conflict descriptor.
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

- [Prev Class](NFEConflictsDescriptor.md)
- Next Class

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
