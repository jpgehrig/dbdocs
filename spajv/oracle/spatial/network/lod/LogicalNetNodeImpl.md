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

- [Prev Class](LogicalNetNode.md)
- [Next Class](LogicalNode.md)

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

## Class LogicalNetNodeImpl

- java.lang.Object

- - oracle.spatial.network.lod.LogicalNetNodeImpl

<!-- -->

- All Implemented Interfaces:
  [LogicalNetNode](LogicalNetNode.md), [LogicalNode](LogicalNode.md)

  ------------------------------------------------------------------------



      public class LogicalNetNodeImpl
      extends java.lang.Object
      implements LogicalNetNode

  Default implementation of LogicalNetNode.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                          |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `LogicalNetNodeImpl``(long id, int partitionId, int linkLevel, double cost, boolean isActive, int maxLinkLevel, int numInLinks, int numOutLinks, `[`CategorizedUserData`](CategorizedUserData.md)` userData)`<br>Constructs a LogicalNetNode object. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                               | Method and Description                                                                                                  |
    |-------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------|
    | `void`                                          | `addInLink``(`[`LogicalNetLink`](LogicalNetLink.md)` link)`<br>Adds an incoming link to this node.                      |
    | `void`                                          | `addOutLink``(`[`LogicalNetLink`](LogicalNetLink.md)` link)`<br>Adds an outgoing link to this node.                     |
    | `java.lang.Object`                              | `clone``()`<br>Support cloneable                                                                                        |
    | `long[]`                                        | `getAdjacentNodeIds``(boolean activeOnly)`<br>Returns the IDs of all the nodes with a direct link to or from this node. |
    | [`CategorizedUserData`](CategorizedUserData.md) | `getCategorizedUserData``()`<br>Returns categorized user data.                                                          |
    | [`CategorizedUserData`](CategorizedUserData.md) | `getCategorizedUserData``()`<br>Returns categorized user data.                                                          |
    | `double`                                        | `getCost``()`<br>Returns the cost of this node.                                                                         |
    | `long`                                          | `getId``()`<br>Returns the node ID                                                                                      |
    | [`LogicalNetLink`](LogicalNetLink.md)`[]`       | `getIncidentLinks``(boolean activeOnly)`<br>Returns the IDs of all the links incident to this node.                     |
    | [`LogicalNetLink`](LogicalNetLink.md)`[]`       | `getInLinks``(boolean activeOnly)`<br>Returns the array of incoming links to this node.                                 |
    | `int`                                           | `getLinkLevel``()`<br>Returns the link level of the containing partition.                                               |
    | `int`                                           | `getMaxLinkLevel``()`<br>Returns the maximum link level of the links incident to this node.                             |
    | `long[]`                                        | `getNextNodeIds``(boolean activeOnly)`<br>Returns the IDs of all the nodes with a direct link from this node.           |
    | `int`                                           | `getNumberOfInLinks``()`<br>Returns the number of incoming links.                                                       |
    | `int`                                           | `getNumberOfOutLinks``()`<br>Returns the number of outgoing links.                                                      |
    | [`LogicalNetLink`](LogicalNetLink.md)`[]`       | `getOutLinks``(boolean activeOnly)`<br>Returns the array of outgoing links from this node.                              |
    | `int`                                           | `getPartitionId``()`<br>Returns the partition ID.                                                                       |
    | `long[]`                                        | `getPreviousNodeIds``(boolean activeOnly)`<br>Returns the IDs of all the nodes with a direct link to this node.         |
    | [`UserData`](UserData.md)                       | `getUserData``(int category)`<br>Returns user data for the specified category.                                          |
    | [`UserData`](UserData.md)                       | `getUserData``(int category)`<br>Returns user data for the specified category.                                          |
    | `boolean`                                       | `isActive``()`<br>Checks whether the node is active.                                                                    |
    | `boolean`                                       | `isDummyExternalNode``()`<br>Returns true if the net node object is an external node and                                |
    | `boolean`                                       | `isPartiallyLoaded``()`<br>Use max link level as an indicator for whether a node is external.                           |
    | `void`                                          | `removeInLink``(long linkId)`<br>Removes the incoming link with the specified link ID.                                  |
    | `void`                                          | `removeOutLink``(long linkId)`<br>Removes the outgoing link with the specified link ID.                                 |
    | `void`                                          | `setCategorizedUserData``(`[`CategorizedUserData`](CategorizedUserData.md)` userData)`<br>Sets categorized user data.   |
    | `void`                                          | `setCategorizedUserData``(`[`CategorizedUserData`](CategorizedUserData.md)` cud)`<br>Sets categorized user data.        |
    | `void`                                          | `setCost``(double cost)`<br>Sets the cost of this node.                                                                 |
    | `void`                                          | `setIsActive``(boolean isActive)`<br>Sets whether this node is active.                                                  |
    | `void`                                          | `setMaxLinkLevel``(int maxLinkLevel)`<br>Sets the maximum link level of the links incident to this node.                |
    | `void`                                          | `setPartitionId``(int partitionId)`<br>Sets the partition ID.                                                           |
    | `void`                                          | `setUserData``(int category, `[`UserData`](UserData.md)` userData)`<br>Sets user data for the specified category.       |
    | `void`                                          | `setUserData``(int category, `[`UserData`](UserData.md)` userData)`<br>Sets user data for the specified category.       |
    | [`LogicalNode`](LogicalNode.md)                 | `toStandAloneNode``()`<br>Returns a new instance of a standalone node, which has the same properties as this node.      |
    | `void`                                          | `update``(`[`LogicalNode`](LogicalNode.md)` node)`<br>Copies the attributes of the input node to this node.             |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.lod.[LogicalNode](LogicalNode.md)

      [`getCost`](LogicalNode.md)`, `[`getId`](LogicalNode.md)`, `[`getMaxLinkLevel`](LogicalNode.md)`, `[`isActive`](LogicalNode.md)`, `[`setCost`](LogicalNode.md)`, `[`setIsActive`](LogicalNode.md)`, `[`setMaxLinkLevel`](LogicalNode.md)`, `[`update`](LogicalNode.md)

<!-- -->

- - ### Constructor Detail

    - #### LogicalNetNodeImpl

          public LogicalNetNodeImpl(long id,
                                    int partitionId,
                                    int linkLevel,
                                    double cost,
                                    boolean isActive,
                                    int maxLinkLevel,
                                    int numInLinks,
                                    int numOutLinks,
                                    CategorizedUserData userData)

      Constructs a LogicalNetNode object.
      Parameters:
      `id` - ID of the node

      `partitionId` - the partition which the node belongs to

      `linkLevel` - link level of the partition

      `cost` - cost of the node

      `isActive` - whether the node is active

      `maxLinkLevel` - maximum link level

      `numInLinks` -

      `numOutLinks` -

      `userData` -

  <!-- -->

  - ### Method Detail

    - #### getLinkLevel

          public int getLinkLevel()

      Description copied from interface: [`LogicalNetNode`](LogicalNetNode.md)
      Returns the link level of the containing partition.
      Specified by:

      [`getLinkLevel`](LogicalNetNode.md) in interface [`LogicalNetNode`](LogicalNetNode.md)

      Returns:

    <!-- -->

    - #### getPartitionId

          public int getPartitionId()

      Description copied from interface: [`LogicalNetNode`](LogicalNetNode.md)
      Returns the partition ID.
      Specified by:

      [`getPartitionId`](LogicalNetNode.md) in interface [`LogicalNetNode`](LogicalNetNode.md)

      Returns:

    <!-- -->

    - #### setPartitionId

          public void setPartitionId(int partitionId)

      Description copied from interface: [`LogicalNetNode`](LogicalNetNode.md)
      Sets the partition ID.
      Specified by:
      [`setPartitionId`](LogicalNetNode.md) in interface [`LogicalNetNode`](LogicalNetNode.md)

    <!-- -->

    - #### getInLinks

          public LogicalNetLink[] getInLinks(boolean activeOnly)

      Description copied from interface: [`LogicalNetNode`](LogicalNetNode.md)
      Returns the array of incoming links to this node.
      Specified by:
      [`getInLinks`](LogicalNetNode.md) in interface [`LogicalNetNode`](LogicalNetNode.md)

      Returns:
      array of links

    <!-- -->

    - #### getOutLinks

          public LogicalNetLink[] getOutLinks(boolean activeOnly)

      Description copied from interface: [`LogicalNetNode`](LogicalNetNode.md)
      Returns the array of outgoing links from this node.
      Specified by:
      [`getOutLinks`](LogicalNetNode.md) in interface [`LogicalNetNode`](LogicalNetNode.md)

      Returns:
      array of links

    <!-- -->

    - #### getIncidentLinks

          public LogicalNetLink[] getIncidentLinks(boolean activeOnly)

      Description copied from interface: [`LogicalNetNode`](LogicalNetNode.md)
      Returns the IDs of all the links incident to this node.
      Specified by:
      [`getIncidentLinks`](LogicalNetNode.md) in interface [`LogicalNetNode`](LogicalNetNode.md)

      Returns:
      array of incident link IDs

    <!-- -->

    - #### getNumberOfInLinks

          public int getNumberOfInLinks()

      Description copied from interface: [`LogicalNetNode`](LogicalNetNode.md)
      Returns the number of incoming links.
      Specified by:
      [`getNumberOfInLinks`](LogicalNetNode.md) in interface [`LogicalNetNode`](LogicalNetNode.md)

      Returns:
      number of incoming links

    <!-- -->

    - #### getNumberOfOutLinks

          public int getNumberOfOutLinks()

      Description copied from interface: [`LogicalNetNode`](LogicalNetNode.md)
      Returns the number of outgoing links.
      Specified by:
      [`getNumberOfOutLinks`](LogicalNetNode.md) in interface [`LogicalNetNode`](LogicalNetNode.md)

      Returns:
      number of outgoing links

    <!-- -->

    - #### addInLink

          public void addInLink(LogicalNetLink link)

      Description copied from interface: [`LogicalNetNode`](LogicalNetNode.md)
      Adds an incoming link to this node.
      Specified by:
      [`addInLink`](LogicalNetNode.md) in interface [`LogicalNetNode`](LogicalNetNode.md)

      Parameters:
      `link` - incoming link

    <!-- -->

    - #### addOutLink

          public void addOutLink(LogicalNetLink link)

      Description copied from interface: [`LogicalNetNode`](LogicalNetNode.md)
      Adds an outgoing link to this node.
      Specified by:
      [`addOutLink`](LogicalNetNode.md) in interface [`LogicalNetNode`](LogicalNetNode.md)

      Parameters:
      `link` - outgoing link

    <!-- -->

    - #### getPreviousNodeIds

          public long[] getPreviousNodeIds(boolean activeOnly)

      Description copied from interface: [`LogicalNetNode`](LogicalNetNode.md)
      Returns the IDs of all the nodes with a direct link to this node.
      Specified by:
      [`getPreviousNodeIds`](LogicalNetNode.md) in interface [`LogicalNetNode`](LogicalNetNode.md)

      Returns:
      array of previous node IDs

    <!-- -->

    - #### getNextNodeIds

          public long[] getNextNodeIds(boolean activeOnly)

      Description copied from interface: [`LogicalNetNode`](LogicalNetNode.md)
      Returns the IDs of all the nodes with a direct link from this node.
      Specified by:
      [`getNextNodeIds`](LogicalNetNode.md) in interface [`LogicalNetNode`](LogicalNetNode.md)

      Returns:
      array of next node IDs

    <!-- -->

    - #### getAdjacentNodeIds

          public long[] getAdjacentNodeIds(boolean activeOnly)

      Description copied from interface: [`LogicalNetNode`](LogicalNetNode.md)
      Returns the IDs of all the nodes with a direct link to or from this node.
      Specified by:
      [`getAdjacentNodeIds`](LogicalNetNode.md) in interface [`LogicalNetNode`](LogicalNetNode.md)

      Returns:
      array of adjacent node IDs

    <!-- -->

    - #### removeInLink

          public void removeInLink(long linkId)

      Description copied from interface: [`LogicalNetNode`](LogicalNetNode.md)
      Removes the incoming link with the specified link ID.
      Specified by:
      [`removeInLink`](LogicalNetNode.md) in interface [`LogicalNetNode`](LogicalNetNode.md)

      Parameters:
      `linkId` - link ID

    <!-- -->

    - #### removeOutLink

          public void removeOutLink(long linkId)

      Description copied from interface: [`LogicalNetNode`](LogicalNetNode.md)
      Removes the outgoing link with the specified link ID.
      Specified by:
      [`removeOutLink`](LogicalNetNode.md) in interface [`LogicalNetNode`](LogicalNetNode.md)

      Parameters:
      `linkId` - link ID

    <!-- -->

    - #### isPartiallyLoaded

          public boolean isPartiallyLoaded()

      Use max link level as an indicator for whether a node is external. If the max link level is less than the minimum allowed number 1, then the node must be an external node that is partially loaded.
      Specified by:

      [`isPartiallyLoaded`](LogicalNetNode.md) in interface [`LogicalNetNode`](LogicalNetNode.md)

      Returns:

    <!-- -->

    - #### toStandAloneNode

          public LogicalNode toStandAloneNode()

      Description copied from interface: [`LogicalNetNode`](LogicalNetNode.md)
      Returns a new instance of a standalone node, which has the same properties as this node.
      Specified by:
      [`toStandAloneNode`](LogicalNetNode.md) in interface [`LogicalNetNode`](LogicalNetNode.md)

      Returns:
      a standalone node

    <!-- -->

    - #### clone

          public java.lang.Object clone()
                                 throws java.lang.CloneNotSupportedException

      Support cloneable
      Specified by:
      [`clone`](LogicalNetNode.md) in interface [`LogicalNetNode`](LogicalNetNode.md)

      Returns:
      cloned object

      Throws:
      `java.lang.CloneNotSupportedException`

    <!-- -->

    - #### isDummyExternalNode

          public boolean isDummyExternalNode()

      Description copied from interface: [`LogicalNetNode`](LogicalNetNode.md)
      Returns true if the net node object is an external node and
      Specified by:

      [`isDummyExternalNode`](LogicalNetNode.md) in interface [`LogicalNetNode`](LogicalNetNode.md)

      Returns:

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

      Description copied from interface: [`LogicalNode`](LogicalNode.md)
      Returns the node ID
      Specified by:
      [`getId`](LogicalNode.md) in interface [`LogicalNode`](LogicalNode.md)

      Returns:
      node ID

    <!-- -->

    - #### getCost

          public double getCost()

      Description copied from interface: [`LogicalNode`](LogicalNode.md)
      Returns the cost of this node.
      Specified by:
      [`getCost`](LogicalNode.md) in interface [`LogicalNode`](LogicalNode.md)

      Returns:
      node cost

    <!-- -->

    - #### setCost

          public void setCost(double cost)

      Description copied from interface: [`LogicalNode`](LogicalNode.md)
      Sets the cost of this node.
      Specified by:
      [`setCost`](LogicalNode.md) in interface [`LogicalNode`](LogicalNode.md)

      Parameters:
      `cost` - node cost

    <!-- -->

    - #### getMaxLinkLevel

          public int getMaxLinkLevel()

      Description copied from interface: [`LogicalNode`](LogicalNode.md)
      Returns the maximum link level of the links incident to this node.
      Specified by:
      [`getMaxLinkLevel`](LogicalNode.md) in interface [`LogicalNode`](LogicalNode.md)

      Returns:
      the maximum link level of the links incident to this node

    <!-- -->

    - #### setMaxLinkLevel

          public void setMaxLinkLevel(int maxLinkLevel)

      Description copied from interface: [`LogicalNode`](LogicalNode.md)
      Sets the maximum link level of the links incident to this node.
      Specified by:
      [`setMaxLinkLevel`](LogicalNode.md) in interface [`LogicalNode`](LogicalNode.md)

      Parameters:
      `maxLinkLevel` - maximum link level of the links incident to this node

    <!-- -->

    - #### isActive

          public boolean isActive()

      Description copied from interface: [`LogicalNode`](LogicalNode.md)
      Checks whether the node is active.
      Specified by:
      [`isActive`](LogicalNode.md) in interface [`LogicalNode`](LogicalNode.md)

      Returns:
      true if the node is active

    <!-- -->

    - #### setIsActive

          public void setIsActive(boolean isActive)

      Description copied from interface: [`LogicalNode`](LogicalNode.md)
      Sets whether this node is active.
      Specified by:
      [`setIsActive`](LogicalNode.md) in interface [`LogicalNode`](LogicalNode.md)

      Parameters:
      `isActive` - true if the node is active; false otherwise.

    <!-- -->

    - #### update

          public void update(LogicalNode node)

      Description copied from interface: [`LogicalNode`](LogicalNode.md)
      Copies the attributes of the input node to this node.
      Specified by:
      [`update`](LogicalNode.md) in interface [`LogicalNode`](LogicalNode.md)

      Parameters:
      `node` - node containing the attributes to copy from

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

- [Prev Class](LogicalNetNode.md)
- [Next Class](LogicalNode.md)

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
