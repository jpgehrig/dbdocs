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

- [Prev Class](SpatialPartition.md)
- [Next Class](SpatialSubNetwork.md)

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

## Interface SpatialPath

- All Superinterfaces:
  [LogicalLightPath](LogicalLightPath.md), [LogicalPath](LogicalPath.md)

  ------------------------------------------------------------------------



      public interface SpatialPath
      extends LogicalPath

  A SpatialPath is a LogicalPath with geometry information.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                               | Method and Description                                                                                                |
    |-------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                              | `clone``()`<br>Support cloneable                                                                                      |
    | [`CategorizedUserData`](CategorizedUserData.md) | `getCategorizedUserData``()`<br>Returns categorized user data.                                                        |
    | [`JGeometry`](../../geometry/JGeometry.md)      | `getGeometry``()`<br>Returns the geometry information of the path.                                                    |
    | [`UserData`](UserData.md)                       | `getUserData``(int category)`<br>Returns user data for the specified category.                                        |
    | `void`                                          | `setCategorizedUserData``(`[`CategorizedUserData`](CategorizedUserData.md)` userData)`<br>Sets categorized user data. |
    | `void`                                          | `setUserData``(int category, `[`UserData`](UserData.md)` userData)`<br>Sets user data for the specified category.     |

    - ### Methods inherited from interface oracle.spatial.network.lod.[LogicalPath](LogicalPath.md)

      [`append`](LogicalPath.md)`, `[`append`](LogicalPath.md)`, `[`append`](LogicalPath.md)`, `[`append`](LogicalPath.md)`, `[`getCostsAtNode`](LogicalPath.md)`, `[`getCostsAtNodes`](LogicalPath.md)`, `[`getCostsToNode`](LogicalPath.md)`, `[`getCostsToNodes`](LogicalPath.md)`, `[`getLinkIds`](LogicalPath.md)`, `[`getNodeIds`](LogicalPath.md)`, `[`indexOfLink`](LogicalPath.md)`, `[`indexOfNode`](LogicalPath.md)`, `[`isSimple`](LogicalPath.md)`, `[`prepend`](LogicalPath.md)`, `[`prepend`](LogicalPath.md)`, `[`prepend`](LogicalPath.md)`, `[`prepend`](LogicalPath.md)

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.lod.[LogicalLightPath](LogicalLightPath.md)

      [`getCost`](LogicalLightPath.md)`, `[`getCosts`](LogicalLightPath.md)`, `[`getEndNodeId`](LogicalLightPath.md)`, `[`getFirstLinkId`](LogicalLightPath.md)`, `[`getLastLinkId`](LogicalLightPath.md)`, `[`getNumberOfLinks`](LogicalLightPath.md)`, `[`getNumberOfNodes`](LogicalLightPath.md)`, `[`getStartNodeId`](LogicalLightPath.md)`, `[`isReverse`](LogicalLightPath.md)`, `[`reverse`](LogicalLightPath.md)`, `[`setCosts`](LogicalLightPath.md)

<!-- -->

- - ### Method Detail

    - #### getGeometry

          JGeometry getGeometry()

      Returns the geometry information of the path.
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

    <!-- -->

    - #### clone

          java.lang.Object clone()
                          throws java.lang.CloneNotSupportedException

      Support cloneable
      Returns:
      cloned object

      Throws:
      `java.lang.CloneNotSupportedException`

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

- [Prev Class](SpatialPartition.md)
- [Next Class](SpatialSubNetwork.md)

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
