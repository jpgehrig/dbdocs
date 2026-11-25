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

- [Prev Class](SpatialLink.md)
- [Next Class](SpatialNetNode.md)

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

## Interface SpatialNetLink

- All Superinterfaces:
  [LogicalLink](LogicalLink.md), [LogicalNetLink](LogicalNetLink.md)

  ------------------------------------------------------------------------



      public interface SpatialNetLink
      extends LogicalNetLink

  A SpatialNetLink is a LogicalNetLink with geometry information.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                               | Method and Description                                                                                                |
    |-------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
    | [`CategorizedUserData`](CategorizedUserData.md) | `getCategorizedUserData``()`<br>Returns categorized user data.                                                        |
    | [`JGeometry`](../../geometry/JGeometry.md)      | `getGeometry``()`<br>Returns the geometry information of the link.                                                    |
    | [`UserData`](UserData.md)                       | `getUserData``(int category)`<br>Returns user data for the specified category.                                        |
    | `void`                                          | `setCategorizedUserData``(`[`CategorizedUserData`](CategorizedUserData.md)` userData)`<br>Sets categorized user data. |
    | `void`                                          | `setUserData``(int category, `[`UserData`](UserData.md)` userData)`<br>Sets user data for the specified category.     |

    - ### Methods inherited from interface oracle.spatial.network.lod.[LogicalNetLink](LogicalNetLink.md)

      [`clone`](LogicalNetLink.md)`, `[`getEndNode`](LogicalNetLink.md)`, `[`getPartitionId`](LogicalNetLink.md)`, `[`getStartNode`](LogicalNetLink.md)`, `[`isPartiallyLoaded`](LogicalNetLink.md)`, `[`setEndNode`](LogicalNetLink.md)`, `[`setPartitionId`](LogicalNetLink.md)`, `[`setStartNode`](LogicalNetLink.md)`, `[`toStandAloneLink`](LogicalNetLink.md)

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.lod.[LogicalLink](LogicalLink.md)

      [`getCost`](LogicalLink.md)`, `[`getEndNodeId`](LogicalLink.md)`, `[`getId`](LogicalLink.md)`, `[`getLevel`](LogicalLink.md)`, `[`getStartNodeId`](LogicalLink.md)`, `[`isActive`](LogicalLink.md)`, `[`isBidirected`](LogicalLink.md)`, `[`setCost`](LogicalLink.md)`, `[`setEndNodeId`](LogicalLink.md)`, `[`setIsActive`](LogicalLink.md)`, `[`setIsBidirected`](LogicalLink.md)`, `[`setStartNodeId`](LogicalLink.md)`, `[`toLogicalNetLink`](LogicalLink.md)`, `[`update`](LogicalLink.md)

<!-- -->

- - ### Method Detail

    - #### getGeometry

          JGeometry getGeometry()

      Returns the geometry information of the link.
      Returns:

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

- [Prev Class](SpatialLink.md)
- [Next Class](SpatialNetNode.md)

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
