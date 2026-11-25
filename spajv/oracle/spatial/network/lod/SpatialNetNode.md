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

- [Prev Class](SpatialNetLink.md)
- [Next Class](SpatialNode.md)

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

## Interface SpatialNetNode

- All Superinterfaces:
  [LogicalNetNode](LogicalNetNode.md), [LogicalNode](LogicalNode.md)

  ------------------------------------------------------------------------



      public interface SpatialNetNode
      extends LogicalNetNode

  A SpatialNetNode is a LogicalNetNode with geometry information.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                               | Method and Description                                                                                                |
    |-------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
    | [`CategorizedUserData`](CategorizedUserData.md) | `getCategorizedUserData``()`<br>Returns categorized user data.                                                        |
    | [`JGeometry`](../../geometry/JGeometry.md)      | `getGeometry``()`<br>Returns the geometry information of the node.                                                    |
    | [`UserData`](UserData.md)                       | `getUserData``(int category)`<br>Returns user data for the specified category.                                        |
    | `void`                                          | `setCategorizedUserData``(`[`CategorizedUserData`](CategorizedUserData.md)` userData)`<br>Sets categorized user data. |
    | `void`                                          | `setUserData``(int category, `[`UserData`](UserData.md)` userData)`<br>Sets user data for the specified category.     |

    - ### Methods inherited from interface oracle.spatial.network.lod.[LogicalNetNode](LogicalNetNode.md)

      [`addInLink`](LogicalNetNode.md)`, `[`addOutLink`](LogicalNetNode.md)`, `[`clone`](LogicalNetNode.md)`, `[`getAdjacentNodeIds`](LogicalNetNode.md)`, `[`getIncidentLinks`](LogicalNetNode.md)`, `[`getInLinks`](LogicalNetNode.md)`, `[`getLinkLevel`](LogicalNetNode.md)`, `[`getNextNodeIds`](LogicalNetNode.md)`, `[`getNumberOfInLinks`](LogicalNetNode.md)`, `[`getNumberOfOutLinks`](LogicalNetNode.md)`, `[`getOutLinks`](LogicalNetNode.md)`, `[`getPartitionId`](LogicalNetNode.md)`, `[`getPreviousNodeIds`](LogicalNetNode.md)`, `[`isDummyExternalNode`](LogicalNetNode.md)`, `[`isPartiallyLoaded`](LogicalNetNode.md)`, `[`removeInLink`](LogicalNetNode.md)`, `[`removeOutLink`](LogicalNetNode.md)`, `[`setPartitionId`](LogicalNetNode.md)`, `[`toStandAloneNode`](LogicalNetNode.md)

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.lod.[LogicalNode](LogicalNode.md)

      [`getCost`](LogicalNode.md)`, `[`getId`](LogicalNode.md)`, `[`getMaxLinkLevel`](LogicalNode.md)`, `[`isActive`](LogicalNode.md)`, `[`setCost`](LogicalNode.md)`, `[`setIsActive`](LogicalNode.md)`, `[`setMaxLinkLevel`](LogicalNode.md)`, `[`update`](LogicalNode.md)

<!-- -->

- - ### Method Detail

    - #### getGeometry

          JGeometry getGeometry()

      Returns the geometry information of the node.
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

- [Prev Class](SpatialNetLink.md)
- [Next Class](SpatialNode.md)

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
