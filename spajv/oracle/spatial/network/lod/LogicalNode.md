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

- [Prev Class](LogicalNetNodeImpl.md)
- [Next Class](LogicalPartition.md)

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

## Interface LogicalNode

- All Known Subinterfaces:
  [LogicalNetNode](LogicalNetNode.md), [SpatialNetNode](SpatialNetNode.md), [SpatialNode](SpatialNode.md)

  <!-- -->

  All Known Implementing Classes:
  [LogicalNetNodeImpl](LogicalNetNodeImpl.md)

  ------------------------------------------------------------------------



      public interface LogicalNode

  This interface defines a standalone node.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                               | Method and Description                                                                                                |
    |-------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                              | `clone``()`<br>Support cloneable                                                                                      |
    | [`CategorizedUserData`](CategorizedUserData.md) | `getCategorizedUserData``()`<br>Returns categorized user data.                                                        |
    | `double`                                        | `getCost``()`<br>Returns the cost of this node.                                                                       |
    | `long`                                          | `getId``()`<br>Returns the node ID                                                                                    |
    | `int`                                           | `getMaxLinkLevel``()`<br>Returns the maximum link level of the links incident to this node.                           |
    | [`UserData`](UserData.md)                       | `getUserData``(int category)`<br>Returns user data for the specified category.                                        |
    | `boolean`                                       | `isActive``()`<br>Checks whether the node is active.                                                                  |
    | `void`                                          | `setCategorizedUserData``(`[`CategorizedUserData`](CategorizedUserData.md)` userData)`<br>Sets categorized user data. |
    | `void`                                          | `setCost``(double cost)`<br>Sets the cost of this node.                                                               |
    | `void`                                          | `setIsActive``(boolean isActive)`<br>Sets whether this node is active.                                                |
    | `void`                                          | `setMaxLinkLevel``(int maxLinkLevel)`<br>Sets the maximum link level of the links incident to this node.              |
    | `void`                                          | `setUserData``(int category, `[`UserData`](UserData.md)` userData)`<br>Sets user data for the specified category.     |
    | `void`                                          | `update``(LogicalNode node)`<br>Copies the attributes of the input node to this node.                                 |

<!-- -->

- - ### Method Detail

    - #### getId

          long getId()

      Returns the node ID
      Returns:
      node ID

    <!-- -->

    - #### getCost

          double getCost()

      Returns the cost of this node.
      Returns:
      node cost

    <!-- -->

    - #### setCost

          void setCost(double cost)

      Sets the cost of this node.
      Parameters:
      `cost` - node cost

    <!-- -->

    - #### getMaxLinkLevel

          int getMaxLinkLevel()

      Returns the maximum link level of the links incident to this node.
      Returns:
      the maximum link level of the links incident to this node

    <!-- -->

    - #### setMaxLinkLevel

          void setMaxLinkLevel(int maxLinkLevel)

      Sets the maximum link level of the links incident to this node.
      Parameters:
      `maxLinkLevel` - maximum link level of the links incident to this node

    <!-- -->

    - #### isActive

          boolean isActive()

      Checks whether the node is active.
      Returns:
      true if the node is active

    <!-- -->

    - #### setIsActive

          void setIsActive(boolean isActive)

      Sets whether this node is active.
      Parameters:
      `isActive` - true if the node is active; false otherwise.

    <!-- -->

    - #### update

          void update(LogicalNode node)

      Copies the attributes of the input node to this node.
      Parameters:
      `node` - node containing the attributes to copy from

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

- [Prev Class](LogicalNetNodeImpl.md)
- [Next Class](LogicalPartition.md)

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
