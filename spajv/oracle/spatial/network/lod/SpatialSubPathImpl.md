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

- [Prev Class](SpatialSubPath.md)
- [Next Class](TimeWindow.md)

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

## Class SpatialSubPathImpl

- java.lang.Object

- - [oracle.spatial.network.lod.LogicalSubPathImpl](LogicalSubPathImpl.md)

  - - oracle.spatial.network.lod.SpatialSubPathImpl

<!-- -->

- All Implemented Interfaces:
  java.lang.Comparable, [LogicalLightSubPath](LogicalLightSubPath.md), [LogicalSubPath](LogicalSubPath.md), [SpatialSubPath](SpatialSubPath.md)

  ------------------------------------------------------------------------



      public class SpatialSubPathImpl
      extends LogicalSubPathImpl
      implements SpatialSubPath

  Default implementation of SpatialSubPath.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                     |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `SpatialSubPathImpl``(`[`SpatialPath`](SpatialPath.md)` referencePath, int startLinkIndex, double startPercentage, int endLinkIndex, double endPercentage, double[] costs, `[`JGeometry`](../../geometry/JGeometry.md)` geometry, `[`CategorizedUserData`](CategorizedUserData.md)` userData)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                               | Method and Description                                                                                                                                             |
    |-------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                              | `clone``()`<br>Support cloneable                                                                                                                                   |
    | `java.lang.Object`                              | `clone``()`<br>Support cloneable                                                                                                                                   |
    | `int`                                           | `compareTo``(java.lang.Object o)`                                                                                                                                  |
    | [`CategorizedUserData`](CategorizedUserData.md) | `getCategorizedUserData``()`<br>Returns categorized user data.                                                                                                     |
    | [`CategorizedUserData`](CategorizedUserData.md) | `getCategorizedUserData``()`<br>Returns categorized user data.                                                                                                     |
    | `double`                                        | `getCost``()`<br>Deprecated.                                                                                                                                       |
    | `double[]`                                      | `getCosts``()`<br>Returns the costs of the subpath.                                                                                                                |
    | `int`                                           | `getEndLinkIndex``()`<br>Returns the end link index.                                                                                                               |
    | `double`                                        | `getEndPercentage``()`<br>Returns the location of the end point of the subpath as a percentage of the last link of the containing path.                            |
    | [`JGeometry`](../../geometry/JGeometry.md)      | `getGeometry``()`<br>Returns the geometry information of the path.                                                                                                 |
    | [`LogicalLightPath`](LogicalLightPath.md)       | `getReferenceLightPath``()`<br>Returns the path containing the subpath.                                                                                            |
    | `int`                                           | `getStartLinkIndex``()`<br>Returns the start link index.                                                                                                           |
    | `double`                                        | `getStartPercentage``()`<br>Returns the location of the starting point of the subpath as a percentage of the first link of the containing path.                    |
    | [`UserData`](UserData.md)                       | `getUserData``(int category)`<br>Returns user data for the specified category.                                                                                     |
    | [`UserData`](UserData.md)                       | `getUserData``(int category)`<br>Returns user data for the specified category.                                                                                     |
    | `boolean`                                       | `isFullPath``()`<br>Returns true if the subpath covers the entire reference path.                                                                                  |
    | `void`                                          | `setCategorizedUserData``(`[`CategorizedUserData`](CategorizedUserData.md)` userData)`<br>Sets categorized user data.                                              |
    | `void`                                          | `setCategorizedUserData``(`[`CategorizedUserData`](CategorizedUserData.md)` cud)`<br>Sets categorized user data.                                                   |
    | `void`                                          | `setCosts``(double[] costs)`<br>Sets the costs of the subpath.                                                                                                     |
    | `void`                                          | `setEndLinkIndex``(int endLinkIndex)`<br>Sets the end link index.                                                                                                  |
    | `void`                                          | `setEndPercentage``(double endPercentage)`<br>Sets the location of the end point of the subpath as a percentage of the last link of the containing path.           |
    | `void`                                          | `setReferenceLightPath``(`[`LogicalLightPath`](LogicalLightPath.md)` refPath)`<br>Sets the path containing the subpath.                                            |
    | `void`                                          | `setStartLinkIndex``(int startLinkIndex)`<br>Sets the start link index.                                                                                            |
    | `void`                                          | `setStartPercentage``(double startPercentage)`<br>Sets the location of the starting point of the subpath as a percentage of the first link of the containing path. |
    | `void`                                          | `setUserData``(int category, `[`UserData`](UserData.md)` userData)`<br>Sets user data for the specified category.                                                  |
    | `void`                                          | `setUserData``(int category, `[`UserData`](UserData.md)` userData)`<br>Sets user data for the specified category.                                                  |

    - ### Methods inherited from class oracle.spatial.network.lod.[LogicalSubPathImpl](LogicalSubPathImpl.md)

      [`append`](LogicalSubPathImpl.md)`, `[`getCostsToNode`](LogicalSubPathImpl.md)`, `[`getReferencePath`](LogicalSubPathImpl.md)`, `[`knowsIntermediateNodeCosts`](LogicalSubPathImpl.md)`, `[`reverse`](LogicalSubPathImpl.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.lod.[LogicalSubPath](LogicalSubPath.md)

      [`append`](LogicalSubPath.md)`, `[`getCostsToNode`](LogicalSubPath.md)`, `[`getReferencePath`](LogicalSubPath.md)

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.lod.[LogicalLightSubPath](LogicalLightSubPath.md)

      [`getCost`](LogicalLightSubPath.md)`, `[`getCosts`](LogicalLightSubPath.md)`, `[`getEndLinkIndex`](LogicalLightSubPath.md)`, `[`getEndPercentage`](LogicalLightSubPath.md)`, `[`getReferenceLightPath`](LogicalLightSubPath.md)`, `[`getStartLinkIndex`](LogicalLightSubPath.md)`, `[`getStartPercentage`](LogicalLightSubPath.md)`, `[`isFullPath`](LogicalLightSubPath.md)`, `[`reverse`](LogicalLightSubPath.md)`, `[`setCosts`](LogicalLightSubPath.md)`, `[`setEndLinkIndex`](LogicalLightSubPath.md)`, `[`setEndPercentage`](LogicalLightSubPath.md)`, `[`setReferenceLightPath`](LogicalLightSubPath.md)`, `[`setStartLinkIndex`](LogicalLightSubPath.md)`, `[`setStartPercentage`](LogicalLightSubPath.md)

    <!-- -->

    - ### Methods inherited from interface java.lang.Comparable

      `compareTo`

<!-- -->

- - ### Constructor Detail

    - #### SpatialSubPathImpl

          public SpatialSubPathImpl(SpatialPath referencePath,
                                    int startLinkIndex,
                                    double startPercentage,
                                    int endLinkIndex,
                                    double endPercentage,
                                    double[] costs,
                                    JGeometry geometry,
                                    CategorizedUserData userData)

  <!-- -->

  - ### Method Detail

    - #### getGeometry

          public JGeometry getGeometry()

      Description copied from interface: [`SpatialSubPath`](SpatialSubPath.md)
      Returns the geometry information of the path.
      Specified by:
      [`getGeometry`](SpatialSubPath.md) in interface [`SpatialSubPath`](SpatialSubPath.md)

      Returns:
      the geometry information of the path

    <!-- -->

    - #### getCategorizedUserData

          public CategorizedUserData getCategorizedUserData()

      Returns categorized user data.
      Returns:

    <!-- -->

    - #### setCategorizedUserData

          public void setCategorizedUserData(CategorizedUserData userData)

      Sets categorized user data.
      Parameters:
      `userData` -

    <!-- -->

    - #### getUserData

          public UserData getUserData(int category)

      Returns user data for the specified category.
      Returns:

    <!-- -->

    - #### setUserData

          public void setUserData(int category,
                                  UserData userData)

      Sets user data for the specified category.
      Parameters:
      `userData` -

    <!-- -->

    - #### clone

          public java.lang.Object clone()
                                 throws java.lang.CloneNotSupportedException

      Support cloneable
      Returns:
      cloned object

      Throws:
      `java.lang.CloneNotSupportedException`

    <!-- -->

    - #### getReferenceLightPath

          public LogicalLightPath getReferenceLightPath()

      Description copied from interface: [`LogicalLightSubPath`](LogicalLightSubPath.md)
      Returns the path containing the subpath.
      Specified by:
      [`getReferenceLightPath`](LogicalLightSubPath.md) in interface [`LogicalLightSubPath`](LogicalLightSubPath.md)

      Returns:
      the light weight logical path that contains the subpath

    <!-- -->

    - #### getStartPercentage

          public double getStartPercentage()

      Description copied from interface: [`LogicalLightSubPath`](LogicalLightSubPath.md)
      Returns the location of the starting point of the subpath as a percentage of the first link of the containing path.
      Specified by:
      [`getStartPercentage`](LogicalLightSubPath.md) in interface [`LogicalLightSubPath`](LogicalLightSubPath.md)

      Returns:
      location of the starting point on the start link

    <!-- -->

    - #### getEndPercentage

          public double getEndPercentage()

      Description copied from interface: [`LogicalLightSubPath`](LogicalLightSubPath.md)
      Returns the location of the end point of the subpath as a percentage of the last link of the containing path.
      Specified by:
      [`getEndPercentage`](LogicalLightSubPath.md) in interface [`LogicalLightSubPath`](LogicalLightSubPath.md)

      Returns:
      location of the end point on the end link

    <!-- -->

    - #### getStartLinkIndex

          public int getStartLinkIndex()

      Description copied from interface: [`LogicalLightSubPath`](LogicalLightSubPath.md)
      Returns the start link index.
      Specified by:
      [`getStartLinkIndex`](LogicalLightSubPath.md) in interface [`LogicalLightSubPath`](LogicalLightSubPath.md)

      Returns:
      the start link index

    <!-- -->

    - #### getEndLinkIndex

          public int getEndLinkIndex()

      Description copied from interface: [`LogicalLightSubPath`](LogicalLightSubPath.md)
      Returns the end link index.
      Specified by:
      [`getEndLinkIndex`](LogicalLightSubPath.md) in interface [`LogicalLightSubPath`](LogicalLightSubPath.md)

      Returns:
      the end link index

    <!-- -->

    - #### getCost

          public double getCost()

      Deprecated. 
      Description copied from interface: [`LogicalLightSubPath`](LogicalLightSubPath.md)
      Returns the cost of the subpath.
      Specified by:
      [`getCost`](LogicalLightSubPath.md) in interface [`LogicalLightSubPath`](LogicalLightSubPath.md)

      Returns:
      cost of the subpath

    <!-- -->

    - #### isFullPath

          public boolean isFullPath()

      Description copied from interface: [`LogicalLightSubPath`](LogicalLightSubPath.md)
      Returns true if the subpath covers the entire reference path.
      Specified by:
      [`isFullPath`](LogicalLightSubPath.md) in interface [`LogicalLightSubPath`](LogicalLightSubPath.md)

      Returns:
      true if the subpath covers the entire reference path, false otherwise.

    <!-- -->

    - #### getCosts

          public double[] getCosts()

      Description copied from interface: [`LogicalLightSubPath`](LogicalLightSubPath.md)
      Returns the costs of the subpath.
      Specified by:
      [`getCosts`](LogicalLightSubPath.md) in interface [`LogicalLightSubPath`](LogicalLightSubPath.md)

      Returns:
      costs of the subpath

    <!-- -->

    - #### setReferenceLightPath

          public void setReferenceLightPath(LogicalLightPath refPath)

      Description copied from interface: [`LogicalLightSubPath`](LogicalLightSubPath.md)
      Sets the path containing the subpath.
      Specified by:
      [`setReferenceLightPath`](LogicalLightSubPath.md) in interface [`LogicalLightSubPath`](LogicalLightSubPath.md)

    <!-- -->

    - #### setStartPercentage

          public void setStartPercentage(double startPercentage)

      Description copied from interface: [`LogicalLightSubPath`](LogicalLightSubPath.md)
      Sets the location of the starting point of the subpath as a percentage of the first link of the containing path.
      Specified by:
      [`setStartPercentage`](LogicalLightSubPath.md) in interface [`LogicalLightSubPath`](LogicalLightSubPath.md)

    <!-- -->

    - #### setEndPercentage

          public void setEndPercentage(double endPercentage)

      Description copied from interface: [`LogicalLightSubPath`](LogicalLightSubPath.md)
      Sets the location of the end point of the subpath as a percentage of the last link of the containing path.
      Specified by:
      [`setEndPercentage`](LogicalLightSubPath.md) in interface [`LogicalLightSubPath`](LogicalLightSubPath.md)

    <!-- -->

    - #### setStartLinkIndex

          public void setStartLinkIndex(int startLinkIndex)

      Description copied from interface: [`LogicalLightSubPath`](LogicalLightSubPath.md)
      Sets the start link index.
      Specified by:
      [`setStartLinkIndex`](LogicalLightSubPath.md) in interface [`LogicalLightSubPath`](LogicalLightSubPath.md)

    <!-- -->

    - #### setEndLinkIndex

          public void setEndLinkIndex(int endLinkIndex)

      Description copied from interface: [`LogicalLightSubPath`](LogicalLightSubPath.md)
      Sets the end link index.
      Specified by:
      [`setEndLinkIndex`](LogicalLightSubPath.md) in interface [`LogicalLightSubPath`](LogicalLightSubPath.md)

    <!-- -->

    - #### setCosts

          public void setCosts(double[] costs)

      Description copied from interface: [`LogicalLightSubPath`](LogicalLightSubPath.md)
      Sets the costs of the subpath.
      Specified by:
      [`setCosts`](LogicalLightSubPath.md) in interface [`LogicalLightSubPath`](LogicalLightSubPath.md)

    <!-- -->

    - #### compareTo

          public int compareTo(java.lang.Object o)

      Specified by:
      `compareTo` in interface `java.lang.Comparable`

    <!-- -->

    - #### getCategorizedUserData

          public CategorizedUserData getCategorizedUserData()

      Returns categorized user data.
      Returns:

    <!-- -->

    - #### setCategorizedUserData

          public void setCategorizedUserData(CategorizedUserData cud)

      Sets categorized user data.

    <!-- -->

    - #### getUserData

          public UserData getUserData(int category)

      Returns user data for the specified category.
      Returns:

    <!-- -->

    - #### setUserData

          public void setUserData(int category,
                                  UserData userData)

      Sets user data for the specified category.

    <!-- -->

    - #### clone

          public java.lang.Object clone()
                                 throws java.lang.CloneNotSupportedException

      Support cloneable
      Overrides:
      `clone` in class `java.lang.Object`

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

- [Prev Class](SpatialSubPath.md)
- [Next Class](TimeWindow.md)

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
