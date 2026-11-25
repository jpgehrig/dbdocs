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

- [Prev Class](LogicalHeavyPath.md)
- [Next Class](LogicalLightSubPath.md)

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

## Interface LogicalLightPath

- All Known Subinterfaces:
  [LogicalPath](LogicalPath.md), [SpatialPath](SpatialPath.md)

  ------------------------------------------------------------------------



      public interface LogicalLightPath

  Light-weight logical path, which only contains the start and end node IDs on the path.
  Since:
  Oracle Database 11g Release 2 (11.2)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Deprecated Methods](javascript:show(32);)**

    | Modifier and Type                               | Method and Description                                                                                                                                    |
    |-------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                              | `clone``()`<br>Support cloneable                                                                                                                          |
    | [`CategorizedUserData`](CategorizedUserData.md) | `getCategorizedUserData``()`<br>Returns categorized user data.                                                                                            |
    | `double`                                        | `getCost``()`<br>Deprecated. <br>use getCosts()                                                                                                           |
    | `double[]`                                      | `getCosts``()`<br>Returns the costs of this path.                                                                                                         |
    | `long`                                          | `getEndNodeId``()`<br>Returns the end node ID of this path.                                                                                               |
    | `long`                                          | `getFirstLinkId``()`<br>Returns the ID of the first link on this path.                                                                                    |
    | `long`                                          | `getLastLinkId``()`<br>Returns the ID of the last link on this path.                                                                                      |
    | `int`                                           | `getNumberOfLinks``()`<br>Returns the number of links on this path.                                                                                       |
    | `int`                                           | `getNumberOfNodes``()`<br>Returns the number of nodes on this path.                                                                                       |
    | `long`                                          | `getStartNodeId``()`<br>Returns the start node ID of this path.                                                                                           |
    | [`UserData`](UserData.md)                       | `getUserData``(int category)`<br>Returns user data for the specified category.                                                                            |
    | `boolean`                                       | `isReverse``()`<br>Returns false if the path is represented in the traveling direction; Returns true if the path is represented in the reverse direction. |
    | `void`                                          | `reverse``()`<br>Reverses node and link order of this path, and flip the isReverse flag of the path.                                                      |
    | `void`                                          | `setCategorizedUserData``(`[`CategorizedUserData`](CategorizedUserData.md)` userData)`<br>Sets categorized user data.                                     |
    | `void`                                          | `setCosts``(double[] costs)`<br>Sets the costs of the path.                                                                                               |
    | `void`                                          | `setUserData``(int category, `[`UserData`](UserData.md)` userData)`<br>Sets user data for the specified category.                                         |

<!-- -->

- - ### Method Detail

    - #### getCost

          double getCost()

      Deprecated. use getCosts()
      Returns the primary cost of this path.
      Returns:
      primary cost of the path

    <!-- -->

    - #### getCosts

          double[] getCosts()

      Returns the costs of this path.
      Returns:
      costs of the path

    <!-- -->

    - #### setCosts

          void setCosts(double[] costs)

      Sets the costs of the path.
      Parameters:
      `costs` -

    <!-- -->

    - #### getStartNodeId

          long getStartNodeId()

      Returns the start node ID of this path.
      Returns:
      start node ID

    <!-- -->

    - #### getEndNodeId

          long getEndNodeId()

      Returns the end node ID of this path.
      Returns:
      end node ID

    <!-- -->

    - #### getFirstLinkId

          long getFirstLinkId()

      Returns the ID of the first link on this path.
      Returns:
      ID of the first link

    <!-- -->

    - #### getLastLinkId

          long getLastLinkId()

      Returns the ID of the last link on this path.
      Returns:
      ID of the last link

    <!-- -->

    - #### getNumberOfNodes

          int getNumberOfNodes()

      Returns the number of nodes on this path.
      Returns:
      number of nodes

    <!-- -->

    - #### getNumberOfLinks

          int getNumberOfLinks()

      Returns the number of links on this path.
      Returns:
      number of links

    <!-- -->

    - #### isReverse

          boolean isReverse()

      Returns false if the path is represented in the traveling direction; Returns true if the path is represented in the reverse direction. The nodes and links of a reverse path are listed in reverse order w.r.t the traveling direction.
      Returns:

    <!-- -->

    - #### reverse

          void reverse()

      Reverses node and link order of this path, and flip the isReverse flag of the path.
      Parameters:
      `newStartNodeCosts` -

      `oldStartNodeCosts` -

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

- [Prev Class](LogicalHeavyPath.md)
- [Next Class](LogicalLightSubPath.md)

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
