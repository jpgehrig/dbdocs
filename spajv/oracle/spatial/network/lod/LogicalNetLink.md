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

- [Prev Class](LogicalLink.md)
- [Next Class](LogicalNetLinkImpl.md)

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

## Interface LogicalNetLink

- All Superinterfaces:
  [LogicalLink](LogicalLink.md)

  <!-- -->

  All Known Subinterfaces:
  [SpatialNetLink](SpatialNetLink.md)

  <!-- -->

  All Known Implementing Classes:
  [LogicalNetLinkImpl](LogicalNetLinkImpl.md)

  ------------------------------------------------------------------------



      public interface LogicalNetLink
      extends LogicalLink

  A LogicalNetLink defines a network link, which is a LogicalLink with reference to the LogicalNetNode objects of its start and end nodes.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                               | Method and Description                                                                                                    |
    |-------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                              | `clone``()`<br>Support cloneable.                                                                                         |
    | [`CategorizedUserData`](CategorizedUserData.md) | `getCategorizedUserData``()`<br>Returns categorized user data.                                                            |
    | [`LogicalNetNode`](LogicalNetNode.md)           | `getEndNode``()`<br>Returns the reference to the end node.                                                                |
    | `int`                                           | `getPartitionId``()`<br>Returns the ID of the partition that owns the link.                                               |
    | [`LogicalNetNode`](LogicalNetNode.md)           | `getStartNode``()`<br>Returns the reference to the start node.                                                            |
    | [`UserData`](UserData.md)                       | `getUserData``(int category)`<br>Returns user data for the specified category.                                            |
    | `boolean`                                       | `isPartiallyLoaded``()`<br>Returns true if the net link object is an external link that is partially loaded.              |
    | `void`                                          | `setCategorizedUserData``(`[`CategorizedUserData`](CategorizedUserData.md)` userData)`<br>Sets categorized user data.     |
    | `void`                                          | `setEndNode``(`[`LogicalNetNode`](LogicalNetNode.md)` endNode)`<br>Sets the reference to the end node of this link.       |
    | `void`                                          | `setPartitionId``(int partitionId)`<br>Sets the ID of the partition that owns the link.                                   |
    | `void`                                          | `setStartNode``(`[`LogicalNetNode`](LogicalNetNode.md)` startNode)`<br>Sets the reference to the start node of this link. |
    | `void`                                          | `setUserData``(int category, `[`UserData`](UserData.md)` userData)`<br>Sets user data for the specified category.         |
    | [`LogicalLink`](LogicalLink.md)                 | `toStandAloneLink``()`<br>Returns a new instance of a standalone link, which has the same properties as this link.        |

    - ### Methods inherited from interface oracle.spatial.network.lod.[LogicalLink](LogicalLink.md)

      [`getCost`](LogicalLink.md)`, `[`getEndNodeId`](LogicalLink.md)`, `[`getId`](LogicalLink.md)`, `[`getLevel`](LogicalLink.md)`, `[`getStartNodeId`](LogicalLink.md)`, `[`isActive`](LogicalLink.md)`, `[`isBidirected`](LogicalLink.md)`, `[`setCost`](LogicalLink.md)`, `[`setEndNodeId`](LogicalLink.md)`, `[`setIsActive`](LogicalLink.md)`, `[`setIsBidirected`](LogicalLink.md)`, `[`setStartNodeId`](LogicalLink.md)`, `[`toLogicalNetLink`](LogicalLink.md)`, `[`update`](LogicalLink.md)

<!-- -->

- - ### Method Detail

    - #### getStartNode

          LogicalNetNode getStartNode()

      Returns the reference to the start node.
      Returns:
      start node object

    <!-- -->

    - #### getEndNode

          LogicalNetNode getEndNode()

      Returns the reference to the end node.
      Returns:
      end node object

    <!-- -->

    - #### setStartNode

          void setStartNode(LogicalNetNode startNode)

      Sets the reference to the start node of this link.
      Parameters:
      `startNode` - start node

    <!-- -->

    - #### setEndNode

          void setEndNode(LogicalNetNode endNode)

      Sets the reference to the end node of this link.
      Parameters:
      `endNode` - end node

    <!-- -->

    - #### getPartitionId

          int getPartitionId()

      Returns the ID of the partition that owns the link.
      Returns:

    <!-- -->

    - #### setPartitionId

          void setPartitionId(int partitionId)

      Sets the ID of the partition that owns the link.
      Parameters:
      `partitionId` -

    <!-- -->

    - #### isPartiallyLoaded

          boolean isPartiallyLoaded()

      Returns true if the net link object is an external link that is partially loaded. An external link is an inter-partition link that belongs to the adjacent partition.
      Returns:

    <!-- -->

    - #### toStandAloneLink

          LogicalLink toStandAloneLink()

      Returns a new instance of a standalone link, which has the same properties as this link.
      Returns:
      a standalone link

    <!-- -->

    - #### clone

          java.lang.Object clone()
                          throws java.lang.CloneNotSupportedException

      Support cloneable.
      Specified by:
      [`clone`](LogicalLink.md) in interface [`LogicalLink`](LogicalLink.md)

      Returns:
      cloned object

      Throws:
      `java.lang.CloneNotSupportedException`

    <!-- -->

    - #### getCategorizedUserData

          CategorizedUserData getCategorizedUserData()

      Returns categorized user data.
      Returns:

    <!-- -->

    - #### setCategorizedUserData

          void setCategorizedUserData(CategorizedUserData userData)

      Sets categorized user data.
      Parameters:
      `userData` -

    <!-- -->

    - #### getUserData

          UserData getUserData(int category)

      Returns user data for the specified category.
      Returns:

    <!-- -->

    - #### setUserData

          void setUserData(int category,
                           UserData userData)

      Sets user data for the specified category.
      Parameters:
      `userData` -

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

- [Prev Class](LogicalLink.md)
- [Next Class](LogicalNetLinkImpl.md)

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
