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

- [Prev Class](LogicalNetLinkImpl.md)
- [Next Class](LogicalNetNodeImpl.md)

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

## Interface LogicalNetNode

- All Superinterfaces:
  [LogicalNode](LogicalNode.md)

  <!-- -->

  All Known Subinterfaces:
  [SpatialNetNode](SpatialNetNode.md)

  <!-- -->

  All Known Implementing Classes:
  [LogicalNetNodeImpl](LogicalNetNodeImpl.md)

  ------------------------------------------------------------------------



      public interface LogicalNetNode
      extends LogicalNode

  A LogicalNetNode is a LogicalNode with reference to adjacent node and link objects.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                               | Method and Description                                                                                                  |
    |-------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------|
    | `void`                                          | `addInLink``(`[`LogicalNetLink`](LogicalNetLink.md)` link)`<br>Adds an incoming link to this node.                      |
    | `void`                                          | `addOutLink``(`[`LogicalNetLink`](LogicalNetLink.md)` link)`<br>Adds an outgoing link to this node.                     |
    | `java.lang.Object`                              | `clone``()`<br>Support cloneable.                                                                                       |
    | `long[]`                                        | `getAdjacentNodeIds``(boolean activeOnly)`<br>Returns the IDs of all the nodes with a direct link to or from this node. |
    | [`CategorizedUserData`](CategorizedUserData.md) | `getCategorizedUserData``()`<br>Returns categorized user data.                                                          |
    | [`LogicalNetLink`](LogicalNetLink.md)`[]`       | `getIncidentLinks``(boolean activeOnly)`<br>Returns the IDs of all the links incident to this node.                     |
    | [`LogicalNetLink`](LogicalNetLink.md)`[]`       | `getInLinks``(boolean activeOnly)`<br>Returns the array of incoming links to this node.                                 |
    | `int`                                           | `getLinkLevel``()`<br>Returns the link level of the containing partition.                                               |
    | `long[]`                                        | `getNextNodeIds``(boolean activeOnly)`<br>Returns the IDs of all the nodes with a direct link from this node.           |
    | `int`                                           | `getNumberOfInLinks``()`<br>Returns the number of incoming links.                                                       |
    | `int`                                           | `getNumberOfOutLinks``()`<br>Returns the number of outgoing links.                                                      |
    | [`LogicalNetLink`](LogicalNetLink.md)`[]`       | `getOutLinks``(boolean activeOnly)`<br>Returns the array of outgoing links from this node.                              |
    | `int`                                           | `getPartitionId``()`<br>Returns the partition ID.                                                                       |
    | `long[]`                                        | `getPreviousNodeIds``(boolean activeOnly)`<br>Returns the IDs of all the nodes with a direct link to this node.         |
    | [`UserData`](UserData.md)                       | `getUserData``(int category)`<br>Returns user data for the specified category.                                          |
    | `boolean`                                       | `isDummyExternalNode``()`<br>Returns true if the net node object is an external node and                                |
    | `boolean`                                       | `isPartiallyLoaded``()`<br>Returns true if the net node object is an external node and partially loaded.                |
    | `void`                                          | `removeInLink``(long linkId)`<br>Removes the incoming link with the specified link ID.                                  |
    | `void`                                          | `removeOutLink``(long linkId)`<br>Removes the outgoing link with the specified link ID.                                 |
    | `void`                                          | `setCategorizedUserData``(`[`CategorizedUserData`](CategorizedUserData.md)` userData)`<br>Sets categorized user data.   |
    | `void`                                          | `setPartitionId``(int partitionId)`<br>Sets the partition ID.                                                           |
    | `void`                                          | `setUserData``(int category, `[`UserData`](UserData.md)` userData)`<br>Sets user data for the specified category.       |
    | [`LogicalNode`](LogicalNode.md)                 | `toStandAloneNode``()`<br>Returns a new instance of a standalone node, which has the same properties as this node.      |

    - ### Methods inherited from interface oracle.spatial.network.lod.[LogicalNode](LogicalNode.md)

      [`getCost`](LogicalNode.md)`, `[`getId`](LogicalNode.md)`, `[`getMaxLinkLevel`](LogicalNode.md)`, `[`isActive`](LogicalNode.md)`, `[`setCost`](LogicalNode.md)`, `[`setIsActive`](LogicalNode.md)`, `[`setMaxLinkLevel`](LogicalNode.md)`, `[`update`](LogicalNode.md)

<!-- -->

- - ### Method Detail

    - #### getLinkLevel

          int getLinkLevel()

      Returns the link level of the containing partition.
      Returns:

    <!-- -->

    - #### getPartitionId

          int getPartitionId()

      Returns the partition ID.
      Returns:

    <!-- -->

    - #### setPartitionId

          void setPartitionId(int partitionId)

      Sets the partition ID.
      Parameters:
      `partitionId` -

    <!-- -->

    - #### getInLinks

          LogicalNetLink[] getInLinks(boolean activeOnly)

      Returns the array of incoming links to this node.
      Returns:
      array of links

    <!-- -->

    - #### getOutLinks

          LogicalNetLink[] getOutLinks(boolean activeOnly)

      Returns the array of outgoing links from this node.
      Returns:
      array of links

    <!-- -->

    - #### getNumberOfInLinks

          int getNumberOfInLinks()

      Returns the number of incoming links.
      Returns:
      number of incoming links

    <!-- -->

    - #### getNumberOfOutLinks

          int getNumberOfOutLinks()

      Returns the number of outgoing links.
      Returns:
      number of outgoing links

    <!-- -->

    - #### addInLink

          void addInLink(LogicalNetLink link)

      Adds an incoming link to this node.
      Parameters:
      `link` - incoming link

    <!-- -->

    - #### addOutLink

          void addOutLink(LogicalNetLink link)

      Adds an outgoing link to this node.
      Parameters:
      `link` - outgoing link

    <!-- -->

    - #### getIncidentLinks

          LogicalNetLink[] getIncidentLinks(boolean activeOnly)

      Returns the IDs of all the links incident to this node.
      Returns:
      array of incident link IDs

    <!-- -->

    - #### getPreviousNodeIds

          long[] getPreviousNodeIds(boolean activeOnly)

      Returns the IDs of all the nodes with a direct link to this node.
      Returns:
      array of previous node IDs

    <!-- -->

    - #### getNextNodeIds

          long[] getNextNodeIds(boolean activeOnly)

      Returns the IDs of all the nodes with a direct link from this node.
      Returns:
      array of next node IDs

    <!-- -->

    - #### getAdjacentNodeIds

          long[] getAdjacentNodeIds(boolean activeOnly)

      Returns the IDs of all the nodes with a direct link to or from this node.
      Returns:
      array of adjacent node IDs

    <!-- -->

    - #### removeInLink

          void removeInLink(long linkId)

      Removes the incoming link with the specified link ID.
      Parameters:
      `linkId` - link ID

    <!-- -->

    - #### removeOutLink

          void removeOutLink(long linkId)

      Removes the outgoing link with the specified link ID.
      Parameters:
      `linkId` - link ID

    <!-- -->

    - #### isPartiallyLoaded

          boolean isPartiallyLoaded()

      Returns true if the net node object is an external node and partially loaded.
      Returns:

    <!-- -->

    - #### isDummyExternalNode

          boolean isDummyExternalNode()

      Returns true if the net node object is an external node and
      Returns:

    <!-- -->

    - #### toStandAloneNode

          LogicalNode toStandAloneNode()

      Returns a new instance of a standalone node, which has the same properties as this node.
      Returns:
      a standalone node

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

- [Prev Class](LogicalNetLinkImpl.md)
- [Next Class](LogicalNetNodeImpl.md)

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
