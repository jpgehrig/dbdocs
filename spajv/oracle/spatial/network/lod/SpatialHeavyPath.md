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

- [Prev Class](SpatialBisectClustering.md)
- [Next Class](SpatialKMeansClustering.md)

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

## Interface SpatialHeavyPath

- All Superinterfaces:
  [LogicalHeavyPath](LogicalHeavyPath.md)

  ------------------------------------------------------------------------



      public interface SpatialHeavyPath
      extends LogicalHeavyPath

  A SpatialHeavyPath is a LogicalHeavyPath with geometry information.
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
    | [`SpatialPath`](SpatialPath.md)                 | `toSpatialPath``()`<br>Returns the SpatialPath object.                                                                |

    - ### Methods inherited from interface oracle.spatial.network.lod.[LogicalHeavyPath](LogicalHeavyPath.md)

      [`append`](LogicalHeavyPath.md)`, `[`append`](LogicalHeavyPath.md)`, `[`getCost`](LogicalHeavyPath.md)`, `[`getCosts`](LogicalHeavyPath.md)`, `[`getEndNode`](LogicalHeavyPath.md)`, `[`getFirstLink`](LogicalHeavyPath.md)`, `[`getLastLink`](LogicalHeavyPath.md)`, `[`getLinks`](LogicalHeavyPath.md)`, `[`getNodes`](LogicalHeavyPath.md)`, `[`getStartNode`](LogicalHeavyPath.md)`, `[`getUserData`](LogicalHeavyPath.md)`, `[`getUserData`](LogicalHeavyPath.md)`, `[`isReverse`](LogicalHeavyPath.md)`, `[`prepend`](LogicalHeavyPath.md)`, `[`prepend`](LogicalHeavyPath.md)`, `[`setCost`](LogicalHeavyPath.md)`, `[`setCosts`](LogicalHeavyPath.md)`, `[`setUserData`](LogicalHeavyPath.md)`, `[`setUserData`](LogicalHeavyPath.md)`, `[`toLogicalPath`](LogicalHeavyPath.md)

<!-- -->

- - ### Method Detail

    - #### getGeometry

          JGeometry getGeometry()

      Returns the geometry information of the path.
      Returns:
      sdo geometry

    <!-- -->

    - #### toSpatialPath

          SpatialPath toSpatialPath()

      Returns the SpatialPath object.
      Returns:
      spatial path

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

- [Prev Class](SpatialBisectClustering.md)
- [Next Class](SpatialKMeansClustering.md)

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
