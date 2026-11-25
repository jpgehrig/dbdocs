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

- [Prev Class](LogicalLightPath.md)
- [Next Class](LogicalLink.md)

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

## Interface LogicalLightSubPath

- All Superinterfaces:
  java.lang.Comparable

  <!-- -->

  All Known Subinterfaces:
  [LogicalSubPath](LogicalSubPath.md), [SpatialSubPath](SpatialSubPath.md)

  <!-- -->

  All Known Implementing Classes:
  [LogicalSubPathImpl](LogicalSubPathImpl.md), [SpatialSubPathImpl](SpatialSubPathImpl.md)

  ------------------------------------------------------------------------



      public interface LogicalLightSubPath
      extends java.lang.Comparable

  Light weight logical sub-path that references to a `LogicalLightPath`
  Since:
  Oracle Database 11g Release 2 (11.2)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                               | Method and Description                                                                                                                                             |
    |-------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                              | `clone``()`<br>Support cloneable                                                                                                                                   |
    | [`CategorizedUserData`](CategorizedUserData.md) | `getCategorizedUserData``()`<br>Returns categorized user data.                                                                                                     |
    | `double`                                        | `getCost``()`<br>Deprecated. <br>use getCosts();                                                                                                                   |
    | `double[]`                                      | `getCosts``()`<br>Returns the costs of the subpath.                                                                                                                |
    | `int`                                           | `getEndLinkIndex``()`<br>Returns the end link index.                                                                                                               |
    | `double`                                        | `getEndPercentage``()`<br>Returns the location of the end point of the subpath as a percentage of the last link of the containing path.                            |
    | [`LogicalLightPath`](LogicalLightPath.md)       | `getReferenceLightPath``()`<br>Returns the path containing the subpath.                                                                                            |
    | `int`                                           | `getStartLinkIndex``()`<br>Returns the start link index.                                                                                                           |
    | `double`                                        | `getStartPercentage``()`<br>Returns the location of the starting point of the subpath as a percentage of the first link of the containing path.                    |
    | [`UserData`](UserData.md)                       | `getUserData``(int category)`<br>Returns user data for the specified category.                                                                                     |
    | `boolean`                                       | `isFullPath``()`<br>Returns true if the subpath covers the entire reference path.                                                                                  |
    | `void`                                          | `reverse``()`<br>Reverses the sub-path, and flip the isReverse flag of the reference path.                                                                         |
    | `void`                                          | `setCategorizedUserData``(`[`CategorizedUserData`](CategorizedUserData.md)` userData)`<br>Sets categorized user data.                                              |
    | `void`                                          | `setCosts``(double[] costs)`<br>Sets the costs of the subpath.                                                                                                     |
    | `void`                                          | `setEndLinkIndex``(int endLinkIndex)`<br>Sets the end link index.                                                                                                  |
    | `void`                                          | `setEndPercentage``(double endPercentage)`<br>Sets the location of the end point of the subpath as a percentage of the last link of the containing path.           |
    | `void`                                          | `setReferenceLightPath``(`[`LogicalLightPath`](LogicalLightPath.md)` refPath)`<br>Sets the path containing the subpath.                                            |
    | `void`                                          | `setStartLinkIndex``(int startLinkIndex)`<br>Sets the start link index.                                                                                            |
    | `void`                                          | `setStartPercentage``(double startPercentage)`<br>Sets the location of the starting point of the subpath as a percentage of the first link of the containing path. |
    | `void`                                          | `setUserData``(int category, `[`UserData`](UserData.md)` userData)`<br>Sets user data for the specified category.                                                  |

    - ### Methods inherited from interface java.lang.Comparable

      `compareTo`

<!-- -->

- - ### Method Detail

    - #### getReferenceLightPath

          LogicalLightPath getReferenceLightPath()

      Returns the path containing the subpath.
      Returns:
      the light weight logical path that contains the subpath

    <!-- -->

    - #### getStartPercentage

          double getStartPercentage()

      Returns the location of the starting point of the subpath as a percentage of the first link of the containing path.
      Returns:
      location of the starting point on the start link

    <!-- -->

    - #### getEndPercentage

          double getEndPercentage()

      Returns the location of the end point of the subpath as a percentage of the last link of the containing path.
      Returns:
      location of the end point on the end link

    <!-- -->

    - #### getStartLinkIndex

          int getStartLinkIndex()

      Returns the start link index.
      Returns:
      the start link index

    <!-- -->

    - #### getEndLinkIndex

          int getEndLinkIndex()

      Returns the end link index.
      Returns:
      the end link index

    <!-- -->

    - #### getCost

          double getCost()

      Deprecated. use getCosts();
      Returns the cost of the subpath.
      Returns:
      cost of the subpath

    <!-- -->

    - #### getCosts

          double[] getCosts()

      Returns the costs of the subpath.
      Returns:
      costs of the subpath

    <!-- -->

    - #### setReferenceLightPath

          void setReferenceLightPath(LogicalLightPath refPath)

      Sets the path containing the subpath.

    <!-- -->

    - #### setStartPercentage

          void setStartPercentage(double startPercentage)

      Sets the location of the starting point of the subpath as a percentage of the first link of the containing path.

    <!-- -->

    - #### setEndPercentage

          void setEndPercentage(double endPercentage)

      Sets the location of the end point of the subpath as a percentage of the last link of the containing path.

    <!-- -->

    - #### setStartLinkIndex

          void setStartLinkIndex(int startLinkIndex)

      Sets the start link index.

    <!-- -->

    - #### setEndLinkIndex

          void setEndLinkIndex(int endLinkIndex)

      Sets the end link index.

    <!-- -->

    - #### setCosts

          void setCosts(double[] costs)

      Sets the costs of the subpath.

    <!-- -->

    - #### isFullPath

          boolean isFullPath()

      Returns true if the subpath covers the entire reference path.
      Returns:
      true if the subpath covers the entire reference path, false otherwise.

    <!-- -->

    - #### reverse

          void reverse()

      Reverses the sub-path, and flip the isReverse flag of the reference path. Similar to a path, a sub-path can be represented in the traveling direction, or in the reverse direction. When represented in reverse direction, the isReverse flag of its reference path is set to true.

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

- [Prev Class](LogicalLightPath.md)
- [Next Class](LogicalLink.md)

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
