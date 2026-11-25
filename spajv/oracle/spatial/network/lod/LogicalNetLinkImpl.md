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

- [Prev Class](LogicalNetLink.md)
- [Next Class](LogicalNetNode.md)

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

## Class LogicalNetLinkImpl

- java.lang.Object

- - oracle.spatial.network.lod.LogicalNetLinkImpl

<!-- -->

- All Implemented Interfaces:
  [LogicalLink](LogicalLink.md), [LogicalNetLink](LogicalNetLink.md)

  ------------------------------------------------------------------------



      public class LogicalNetLinkImpl
      extends java.lang.Object
      implements LogicalNetLink

  Default implementation of LogicalNetLink.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                           |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `LogicalNetLinkImpl``(long id, int partitionId, int level, `[`LogicalNetNode`](LogicalNetNode.md)` startNode, `[`LogicalNetNode`](LogicalNetNode.md)` endNode, double cost, boolean isBidirected, boolean isActive, boolean isExternal, `[`CategorizedUserData`](CategorizedUserData.md)` userData)`  |
    | `LogicalNetLinkImpl``(long id, int partitionId, int level, `[`LogicalNetNode`](LogicalNetNode.md)` startNode, `[`LogicalNetNode`](LogicalNetNode.md)` endNode, double cost, boolean isBidirected, boolean isActive, `[`CategorizedUserData`](CategorizedUserData.md)` userData)`                      |
    | `LogicalNetLinkImpl``(long id, int level, `[`LogicalNetNode`](LogicalNetNode.md)` startNode, `[`LogicalNetNode`](LogicalNetNode.md)` endNode, double cost, boolean isBidirected, boolean isActive, `[`CategorizedUserData`](CategorizedUserData.md)` userData)`<br>Deprecated.                        |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                               | Method and Description                                                                                                          |
    |-------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                              | `clone``()`<br>Support cloneable                                                                                                |
    | [`CategorizedUserData`](CategorizedUserData.md) | `getCategorizedUserData``()`<br>Returns categorized user data.                                                                  |
    | [`CategorizedUserData`](CategorizedUserData.md) | `getCategorizedUserData``()`<br>Returns categorized user data.                                                                  |
    | `double`                                        | `getCost``()`<br>Returns the cost of this link.                                                                                 |
    | [`LogicalNetNode`](LogicalNetNode.md)           | `getEndNode``()`<br>Returns the reference to the end node.                                                                      |
    | `long`                                          | `getEndNodeId``()`<br>Returns the end node ID.                                                                                  |
    | `long`                                          | `getId``()`<br>Returns the link ID.                                                                                             |
    | `int`                                           | `getLevel``()`<br>Returns the link level.                                                                                       |
    | `int`                                           | `getPartitionId``()`<br>Returns the ID of the partition that owns the link.                                                     |
    | [`LogicalNetNode`](LogicalNetNode.md)           | `getStartNode``()`<br>Returns the reference to the start node.                                                                  |
    | `long`                                          | `getStartNodeId``()`<br>Returns the start node ID.                                                                              |
    | [`UserData`](UserData.md)                       | `getUserData``(int category)`<br>Returns user data for the specified category.                                                  |
    | [`UserData`](UserData.md)                       | `getUserData``(int category)`<br>Returns user data for the specified category.                                                  |
    | `boolean`                                       | `isActive``()`<br>Checks whether the link is active.                                                                            |
    | `boolean`                                       | `isBidirected``()`<br>Checks whether this link is bidirected or not.                                                            |
    | `boolean`                                       | `isPartiallyLoaded``()`<br>Use link level as an indicator for whether a link is external.                                       |
    | `void`                                          | `setCategorizedUserData``(`[`CategorizedUserData`](CategorizedUserData.md)` userData)`<br>Sets categorized user data.           |
    | `void`                                          | `setCategorizedUserData``(`[`CategorizedUserData`](CategorizedUserData.md)` cud)`<br>Sets categorized user data.                |
    | `void`                                          | `setCost``(double cost)`<br>Sets the cost of this link.                                                                         |
    | `void`                                          | `setEndNode``(`[`LogicalNetNode`](LogicalNetNode.md)` endNode)`<br>Sets the reference to the end node of this link.             |
    | `void`                                          | `setEndNodeId``(long endNodeId)`<br>Sets the end node ID.                                                                       |
    | `void`                                          | `setIsActive``(boolean isActive)`<br>Sets whether the link is active.                                                           |
    | `void`                                          | `setIsBidirected``(boolean isBidirected)`<br>Sets whether the link is bidirected or not.                                        |
    | `void`                                          | `setPartitionId``(int partitionId)`<br>Sets the ID of the partition that owns the link.                                         |
    | `void`                                          | `setStartNode``(`[`LogicalNetNode`](LogicalNetNode.md)` startNode)`<br>Sets the reference to the start node of this link.       |
    | `void`                                          | `setStartNodeId``(long startNodeId)`<br>Sets the start node ID.                                                                 |
    | `void`                                          | `setUserData``(int category, `[`UserData`](UserData.md)` userData)`<br>Sets user data for the specified category.               |
    | `void`                                          | `setUserData``(int category, `[`UserData`](UserData.md)` userData)`<br>Sets user data for the specified category.               |
    | [`LogicalNetLink`](LogicalNetLink.md)           | `toLogicalNetLink``(`[`LogicalPartition`](LogicalPartition.md)` partition)`<br>Converts the standalone link to a partition link |
    | [`LogicalLink`](LogicalLink.md)                 | `toStandAloneLink``()`<br>Returns a new instance of a standalone link, which has the same properties as this link.              |
    | `void`                                          | `update``(`[`LogicalLink`](LogicalLink.md)` link)`<br>Copies the attributes of the input link to this link.                     |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.lod.[LogicalLink](LogicalLink.md)

      [`getCost`](LogicalLink.md)`, `[`getEndNodeId`](LogicalLink.md)`, `[`getId`](LogicalLink.md)`, `[`getLevel`](LogicalLink.md)`, `[`getStartNodeId`](LogicalLink.md)`, `[`isActive`](LogicalLink.md)`, `[`isBidirected`](LogicalLink.md)`, `[`setCost`](LogicalLink.md)`, `[`setEndNodeId`](LogicalLink.md)`, `[`setIsActive`](LogicalLink.md)`, `[`setIsBidirected`](LogicalLink.md)`, `[`setStartNodeId`](LogicalLink.md)`, `[`toLogicalNetLink`](LogicalLink.md)`, `[`update`](LogicalLink.md)

<!-- -->

- - ### Constructor Detail

    - #### LogicalNetLinkImpl

          public LogicalNetLinkImpl(long id,
                                    int partitionId,
                                    int level,
                                    LogicalNetNode startNode,
                                    LogicalNetNode endNode,
                                    double cost,
                                    boolean isBidirected,
                                    boolean isActive,
                                    CategorizedUserData userData)

    <!-- -->

    - #### LogicalNetLinkImpl

          public LogicalNetLinkImpl(long id,
                                    int partitionId,
                                    int level,
                                    LogicalNetNode startNode,
                                    LogicalNetNode endNode,
                                    double cost,
                                    boolean isBidirected,
                                    boolean isActive,
                                    boolean isExternal,
                                    CategorizedUserData userData)

    <!-- -->

    - #### LogicalNetLinkImpl

          public LogicalNetLinkImpl(long id,
                                    int level,
                                    LogicalNetNode startNode,
                                    LogicalNetNode endNode,
                                    double cost,
                                    boolean isBidirected,
                                    boolean isActive,
                                    CategorizedUserData userData)

      Deprecated. 

  <!-- -->

  - ### Method Detail

    - #### getPartitionId

          public int getPartitionId()

      Description copied from interface: [`LogicalNetLink`](LogicalNetLink.md)
      Returns the ID of the partition that owns the link.
      Specified by:

      [`getPartitionId`](LogicalNetLink.md) in interface [`LogicalNetLink`](LogicalNetLink.md)

      Returns:

    <!-- -->

    - #### setPartitionId

          public void setPartitionId(int partitionId)

      Description copied from interface: [`LogicalNetLink`](LogicalNetLink.md)
      Sets the ID of the partition that owns the link.
      Specified by:
      [`setPartitionId`](LogicalNetLink.md) in interface [`LogicalNetLink`](LogicalNetLink.md)

    <!-- -->

    - #### getStartNode

          public LogicalNetNode getStartNode()

      Description copied from interface: [`LogicalNetLink`](LogicalNetLink.md)
      Returns the reference to the start node.
      Specified by:
      [`getStartNode`](LogicalNetLink.md) in interface [`LogicalNetLink`](LogicalNetLink.md)

      Returns:
      start node object

    <!-- -->

    - #### getEndNode

          public LogicalNetNode getEndNode()

      Description copied from interface: [`LogicalNetLink`](LogicalNetLink.md)
      Returns the reference to the end node.
      Specified by:
      [`getEndNode`](LogicalNetLink.md) in interface [`LogicalNetLink`](LogicalNetLink.md)

      Returns:
      end node object

    <!-- -->

    - #### setStartNode

          public void setStartNode(LogicalNetNode startNode)

      Description copied from interface: [`LogicalNetLink`](LogicalNetLink.md)
      Sets the reference to the start node of this link.
      Specified by:
      [`setStartNode`](LogicalNetLink.md) in interface [`LogicalNetLink`](LogicalNetLink.md)

      Parameters:
      `startNode` - start node

    <!-- -->

    - #### setEndNode

          public void setEndNode(LogicalNetNode endNode)

      Description copied from interface: [`LogicalNetLink`](LogicalNetLink.md)
      Sets the reference to the end node of this link.
      Specified by:
      [`setEndNode`](LogicalNetLink.md) in interface [`LogicalNetLink`](LogicalNetLink.md)

      Parameters:
      `endNode` - end node

    <!-- -->

    - #### isPartiallyLoaded

          public boolean isPartiallyLoaded()

      Use link level as an indicator for whether a link is external. If the link level is less than 0, then the link must be an external link that is partially loaded.
      Specified by:

      [`isPartiallyLoaded`](LogicalNetLink.md) in interface [`LogicalNetLink`](LogicalNetLink.md)

      Returns:

    <!-- -->

    - #### toStandAloneLink

          public LogicalLink toStandAloneLink()

      Description copied from interface: [`LogicalNetLink`](LogicalNetLink.md)
      Returns a new instance of a standalone link, which has the same properties as this link.
      Specified by:
      [`toStandAloneLink`](LogicalNetLink.md) in interface [`LogicalNetLink`](LogicalNetLink.md)

      Returns:
      a standalone link

    <!-- -->

    - #### clone

          public java.lang.Object clone()
                                 throws java.lang.CloneNotSupportedException

      Support cloneable
      Specified by:
      [`clone`](LogicalLink.md) in interface [`LogicalLink`](LogicalLink.md)

      Specified by:
      [`clone`](LogicalNetLink.md) in interface [`LogicalNetLink`](LogicalNetLink.md)

      Returns:
      cloned object

      Throws:
      `java.lang.CloneNotSupportedException`

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

    - #### getId

          public long getId()

      Description copied from interface: [`LogicalLink`](LogicalLink.md)
      Returns the link ID.
      Specified by:
      [`getId`](LogicalLink.md) in interface [`LogicalLink`](LogicalLink.md)

      Returns:
      link ID

    <!-- -->

    - #### getLevel

          public int getLevel()

      Description copied from interface: [`LogicalLink`](LogicalLink.md)
      Returns the link level.
      Specified by:
      [`getLevel`](LogicalLink.md) in interface [`LogicalLink`](LogicalLink.md)

      Returns:
      link level

    <!-- -->

    - #### getStartNodeId

          public long getStartNodeId()

      Description copied from interface: [`LogicalLink`](LogicalLink.md)
      Returns the start node ID.
      Specified by:
      [`getStartNodeId`](LogicalLink.md) in interface [`LogicalLink`](LogicalLink.md)

      Returns:
      start node ID

    <!-- -->

    - #### setStartNodeId

          public void setStartNodeId(long startNodeId)

      Description copied from interface: [`LogicalLink`](LogicalLink.md)
      Sets the start node ID.
      Specified by:
      [`setStartNodeId`](LogicalLink.md) in interface [`LogicalLink`](LogicalLink.md)

      Parameters:
      `startNodeId` - start node ID

    <!-- -->

    - #### getEndNodeId

          public long getEndNodeId()

      Description copied from interface: [`LogicalLink`](LogicalLink.md)
      Returns the end node ID.
      Specified by:
      [`getEndNodeId`](LogicalLink.md) in interface [`LogicalLink`](LogicalLink.md)

      Returns:
      end node ID

    <!-- -->

    - #### setEndNodeId

          public void setEndNodeId(long endNodeId)

      Description copied from interface: [`LogicalLink`](LogicalLink.md)
      Sets the end node ID.
      Specified by:
      [`setEndNodeId`](LogicalLink.md) in interface [`LogicalLink`](LogicalLink.md)

      Parameters:
      `endNodeId` - end node ID

    <!-- -->

    - #### getCost

          public double getCost()

      Description copied from interface: [`LogicalLink`](LogicalLink.md)
      Returns the cost of this link.
      Specified by:
      [`getCost`](LogicalLink.md) in interface [`LogicalLink`](LogicalLink.md)

      Returns:
      link cost

    <!-- -->

    - #### setCost

          public void setCost(double cost)

      Description copied from interface: [`LogicalLink`](LogicalLink.md)
      Sets the cost of this link.
      Specified by:
      [`setCost`](LogicalLink.md) in interface [`LogicalLink`](LogicalLink.md)

      Parameters:
      `cost` - link cost

    <!-- -->

    - #### isBidirected

          public boolean isBidirected()

      Description copied from interface: [`LogicalLink`](LogicalLink.md)
      Checks whether this link is bidirected or not.
      Specified by:
      [`isBidirected`](LogicalLink.md) in interface [`LogicalLink`](LogicalLink.md)

      Returns:
      true, if this link is bidirected; false, otherwise.

    <!-- -->

    - #### isActive

          public boolean isActive()

      Description copied from interface: [`LogicalLink`](LogicalLink.md)
      Checks whether the link is active.
      Specified by:
      [`isActive`](LogicalLink.md) in interface [`LogicalLink`](LogicalLink.md)

      Returns:
      true if the link is active; false otherwise.

    <!-- -->

    - #### setIsActive

          public void setIsActive(boolean isActive)

      Description copied from interface: [`LogicalLink`](LogicalLink.md)
      Sets whether the link is active.
      Specified by:
      [`setIsActive`](LogicalLink.md) in interface [`LogicalLink`](LogicalLink.md)

      Parameters:
      `isActive` - true if the link is active; false otherwise.

    <!-- -->

    - #### setIsBidirected

          public void setIsBidirected(boolean isBidirected)

      Description copied from interface: [`LogicalLink`](LogicalLink.md)
      Sets whether the link is bidirected or not.
      Specified by:
      [`setIsBidirected`](LogicalLink.md) in interface [`LogicalLink`](LogicalLink.md)

      Parameters:
      `isBidirected` - true, if this link is bidirected; false, otherwise.

    <!-- -->

    - #### toLogicalNetLink

          public LogicalNetLink toLogicalNetLink(LogicalPartition partition)

      Description copied from interface: [`LogicalLink`](LogicalLink.md)
      Converts the standalone link to a partition link
      Specified by:

      [`toLogicalNetLink`](LogicalLink.md) in interface [`LogicalLink`](LogicalLink.md)

      Parameters:

      `partition` - the partition that contains the link

      Returns:

    <!-- -->

    - #### update

          public void update(LogicalLink link)

      Description copied from interface: [`LogicalLink`](LogicalLink.md)
      Copies the attributes of the input link to this link.
      Specified by:
      [`update`](LogicalLink.md) in interface [`LogicalLink`](LogicalLink.md)

      Parameters:
      `link` - link to copy from

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

- [Prev Class](LogicalNetLink.md)
- [Next Class](LogicalNetNode.md)

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
