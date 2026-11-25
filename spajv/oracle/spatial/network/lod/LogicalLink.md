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

- [Prev Class](LogicalLightSubPath.md)
- [Next Class](LogicalNetLink.md)

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

## Interface LogicalLink

- All Known Subinterfaces:
  [LogicalNetLink](LogicalNetLink.md), [SpatialLink](SpatialLink.md), [SpatialNetLink](SpatialNetLink.md)

  <!-- -->

  All Known Implementing Classes:
  [LogicalNetLinkImpl](LogicalNetLinkImpl.md)

  ------------------------------------------------------------------------



      public interface LogicalLink

  This interface defines a standalone link.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                               | Method and Description                                                                                                          |
    |-------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                              | `clone``()`<br>Support cloneable.                                                                                               |
    | [`CategorizedUserData`](CategorizedUserData.md) | `getCategorizedUserData``()`<br>Returns categorized user data.                                                                  |
    | `double`                                        | `getCost``()`<br>Returns the cost of this link.                                                                                 |
    | `long`                                          | `getEndNodeId``()`<br>Returns the end node ID.                                                                                  |
    | `long`                                          | `getId``()`<br>Returns the link ID.                                                                                             |
    | `int`                                           | `getLevel``()`<br>Returns the link level.                                                                                       |
    | `long`                                          | `getStartNodeId``()`<br>Returns the start node ID.                                                                              |
    | [`UserData`](UserData.md)                       | `getUserData``(int category)`<br>Returns user data for the specified category.                                                  |
    | `boolean`                                       | `isActive``()`<br>Checks whether the link is active.                                                                            |
    | `boolean`                                       | `isBidirected``()`<br>Checks whether this link is bidirected or not.                                                            |
    | `void`                                          | `setCategorizedUserData``(`[`CategorizedUserData`](CategorizedUserData.md)` userData)`<br>Sets categorized user data.           |
    | `void`                                          | `setCost``(double cost)`<br>Sets the cost of this link.                                                                         |
    | `void`                                          | `setEndNodeId``(long endNodeId)`<br>Sets the end node ID.                                                                       |
    | `void`                                          | `setIsActive``(boolean isActive)`<br>Sets whether the link is active.                                                           |
    | `void`                                          | `setIsBidirected``(boolean isBidirected)`<br>Sets whether the link is bidirected or not.                                        |
    | `void`                                          | `setStartNodeId``(long startNodeId)`<br>Sets the start node ID.                                                                 |
    | `void`                                          | `setUserData``(int category, `[`UserData`](UserData.md)` userData)`<br>Sets user data for the specified category.               |
    | [`LogicalNetLink`](LogicalNetLink.md)           | `toLogicalNetLink``(`[`LogicalPartition`](LogicalPartition.md)` partition)`<br>Converts the standalone link to a partition link |
    | `void`                                          | `update``(LogicalLink link)`<br>Copies the attributes of the input link to this link.                                           |

<!-- -->

- - ### Method Detail

    - #### getId

          long getId()

      Returns the link ID.
      Returns:
      link ID

    <!-- -->

    - #### getLevel

          int getLevel()

      Returns the link level.
      Returns:
      link level

    <!-- -->

    - #### getStartNodeId

          long getStartNodeId()

      Returns the start node ID.
      Returns:
      start node ID

    <!-- -->

    - #### setStartNodeId

          void setStartNodeId(long startNodeId)

      Sets the start node ID.
      Parameters:
      `startNodeId` - start node ID

    <!-- -->

    - #### getEndNodeId

          long getEndNodeId()

      Returns the end node ID.
      Returns:
      end node ID

    <!-- -->

    - #### setEndNodeId

          void setEndNodeId(long endNodeId)

      Sets the end node ID.
      Parameters:
      `endNodeId` - end node ID

    <!-- -->

    - #### getCost

          double getCost()

      Returns the cost of this link.
      Returns:
      link cost

    <!-- -->

    - #### setCost

          void setCost(double cost)

      Sets the cost of this link.
      Parameters:
      `cost` - link cost

    <!-- -->

    - #### isBidirected

          boolean isBidirected()

      Checks whether this link is bidirected or not.
      Returns:
      true, if this link is bidirected; false, otherwise.

    <!-- -->

    - #### setIsBidirected

          void setIsBidirected(boolean isBidirected)

      Sets whether the link is bidirected or not.
      Parameters:
      `isBidirected` - true, if this link is bidirected; false, otherwise.

    <!-- -->

    - #### toLogicalNetLink

          LogicalNetLink toLogicalNetLink(LogicalPartition partition)

      Converts the standalone link to a partition link
      Parameters:

      `partition` - the partition that contains the link

      Returns:

    <!-- -->

    - #### isActive

          boolean isActive()

      Checks whether the link is active.
      Returns:
      true if the link is active; false otherwise.

    <!-- -->

    - #### setIsActive

          void setIsActive(boolean isActive)

      Sets whether the link is active.
      Parameters:
      `isActive` - true if the link is active; false otherwise.

    <!-- -->

    - #### update

          void update(LogicalLink link)

      Copies the attributes of the input link to this link.
      Parameters:
      `link` - link to copy from

    <!-- -->

    - #### clone

          java.lang.Object clone()
                          throws java.lang.CloneNotSupportedException

      Support cloneable.
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

- [Prev Class](LogicalLightSubPath.md)
- [Next Class](LogicalNetLink.md)

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
