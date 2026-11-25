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

- [Prev Class](PartitionBlobTranslator11gR2.md)
- [Next Class](PathFeature.md)

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

## Class PartitionUpdate

- java.lang.Object

- - oracle.spatial.network.lod.PartitionUpdate

<!-- -->

-

  ------------------------------------------------------------------------



      public class PartitionUpdate
      extends java.lang.Object

  A PartitionUpdate object contains partition update information.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description           |
    |---------------------------------------|
    | `PartitionUpdate``(int partitionId)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                   | Method and Description                                                   |
    |-------------------------------------|--------------------------------------------------------------------------|
    | `java.lang.Object`                  | `clone``()`                                                              |
    | `PartitionUpdate`                   | `combine``(PartitionUpdate partitionUpdate)`                             |
    | `void`                              | `deleteLink``(long id)`                                                  |
    | `void`                              | `deleteNode``(long id)`                                                  |
    | `long[]`                            | `getDeletedLinkIds``()`                                                  |
    | `long[]`                            | `getDeletedNodeIds``()`                                                  |
    | [`LogicalLink`](LogicalLink.md)     | `getLink``(long linkId)`                                                 |
    | [`LogicalNode`](LogicalNode.md)     | `getNode``(long nodeId)`                                                 |
    | `int`                               | `getNodePartitionId``(long nodeId)`                                      |
    | `int`                               | `getPartitionId``()`                                                     |
    | [`LogicalLink`](LogicalLink.md)`[]` | `getUpdatedLinks``()`                                                    |
    | [`LogicalNode`](LogicalNode.md)`[]` | `getUpdatedNodes``()`                                                    |
    | `boolean`                           | `isLinkDeleted``(long linkId)`                                           |
    | `boolean`                           | `isNodeDeleted``(long nodeId)`                                           |
    | `void`                              | `updateLink``(`[`LogicalLink`](LogicalLink.md)` link)`                   |
    | `void`                              | `updateNode``(`[`LogicalNode`](LogicalNode.md)` node, int partitionId)`  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### PartitionUpdate

          public PartitionUpdate(int partitionId)

  <!-- -->

  - ### Method Detail

    - #### getPartitionId

          public int getPartitionId()

    <!-- -->

    - #### updateNode

          public void updateNode(LogicalNode node,
                                 int partitionId)

    <!-- -->

    - #### deleteNode

          public void deleteNode(long id)

    <!-- -->

    - #### updateLink

          public void updateLink(LogicalLink link)

    <!-- -->

    - #### deleteLink

          public void deleteLink(long id)

    <!-- -->

    - #### getUpdatedNodes

          public LogicalNode[] getUpdatedNodes()

    <!-- -->

    - #### getDeletedNodeIds

          public long[] getDeletedNodeIds()

    <!-- -->

    - #### getUpdatedLinks

          public LogicalLink[] getUpdatedLinks()

    <!-- -->

    - #### getDeletedLinkIds

          public long[] getDeletedLinkIds()

    <!-- -->

    - #### getNodePartitionId

          public int getNodePartitionId(long nodeId)

    <!-- -->

    - #### getNode

          public LogicalNode getNode(long nodeId)

    <!-- -->

    - #### getLink

          public LogicalLink getLink(long linkId)

    <!-- -->

    - #### isLinkDeleted

          public boolean isLinkDeleted(long linkId)

    <!-- -->

    - #### isNodeDeleted

          public boolean isNodeDeleted(long nodeId)

    <!-- -->

    - #### combine

          public PartitionUpdate combine(PartitionUpdate partitionUpdate)

    <!-- -->

    - #### clone

          public java.lang.Object clone()

      Overrides:
      `clone` in class `java.lang.Object`

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

- [Prev Class](PartitionBlobTranslator11gR2.md)
- [Next Class](PathFeature.md)

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
