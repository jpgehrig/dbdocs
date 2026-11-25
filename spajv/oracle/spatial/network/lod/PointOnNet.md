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

- [Prev Class](PointClustering.md)
- [Next Class](PriorityQueue.md)

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

## Class PointOnNet

- java.lang.Object

- - oracle.spatial.network.lod.PointOnNet

<!-- -->

- Direct Known Subclasses:
  [HeavyPointOnNet](HeavyPointOnNet.md)

  ------------------------------------------------------------------------



      public class PointOnNet
      extends java.lang.Object

  This class defines the methods supported by a point on a network. A point on a network can fall on a node or in the middle of a link. User data associated with a PointOnNet can be used in network constraints, cost calculators or heuristic cost functions, etc. For example, the heuristic cost function used in A\* shortest path search needs to know the location of the end point. If the end point is specified using link ID and a percentage, then the user must set the location user data of the end point either by passing it to the PointOnNet constructor or by calling setUserData method on the PointOnNet object. The following is an example on how to set the user data in a PointOnNet object. ` double xCoordinate = -122.45; double yCoordinate = 37.77; PointOnNet point = new PointOnNet(linkId, percentage); Object[] userDataObjects = {xCoordinate, yCoordinate}; UserData userData = new UserDataImpl(userDataObjects); point.setUserData(userData); `
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                           |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `PointOnNet``(long nodeId)`<br>Constructs a PointOnNet for a node.                                                                                    |
    | `PointOnNet``(long nodeId, `[`CategorizedUserData`](CategorizedUserData.md)` cud)`<br>Constructs a PointOnNet for a node.                             |
    | `PointOnNet``(long linkId, double percentage)`<br>Constructs a PointOnNet for a point on link.                                                        |
    | `PointOnNet``(long linkId, double percentage, `[`CategorizedUserData`](CategorizedUserData.md)` cud)`<br>Constructs a PointOnNet for a point on link. |
    | `PointOnNet``(long linkId, double percentage, `[`UserData`](UserData.md)` userData)`<br>Constructs a PointOnNet for a point on link.                  |
    | `PointOnNet``(long nodeId, `[`UserData`](UserData.md)` userData)`<br>Constructs a PointOnNet for a node.                                              |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                               | Method and Description                                                                                            |
    |-------------------------------------------------|-------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                              | `clone``()`<br>Support cloneable                                                                                  |
    | `boolean`                                       | `equals``(java.lang.Object o)`                                                                                    |
    | [`CategorizedUserData`](CategorizedUserData.md) | `getCategorizedUserData``()`<br>Returns categorized user data.                                                    |
    | `long`                                          | `getLinkId``()`<br>Returns the link ID, if the point falls on a link.                                             |
    | `long`                                          | `getNodeId``()`<br>Returns the node ID, if the point falls on a node.                                             |
    | `double`                                        | `getPercentage``()`<br>Returns the percentage on the link, if the point falls on a link.                          |
    | [`UserData`](UserData.md)                       | `getUserData``()`<br>Returns the user data associated with this point on net in the default user data category.   |
    | [`UserData`](UserData.md)                       | `getUserData``(int category)`<br>Returns user data for the specified category.                                    |
    | `int`                                           | `hashCode``()`                                                                                                    |
    | `boolean`                                       | `isNode``()`<br>Checks whether this point falls on a node or not.                                                 |
    | `boolean`                                       | `isPointOnLink``()`<br>Checks whether this point falls on a link or not.                                          |
    | `void`                                          | `removeUserData``()`<br>Removes all user data associated to this object.                                          |
    | `void`                                          | `setCategorizedUserData``(`[`CategorizedUserData`](CategorizedUserData.md)` cud)`<br>Sets categorized user data.  |
    | `void`                                          | `setUserData``(int category, `[`UserData`](UserData.md)` userData)`<br>Sets user data for the specified category. |
    | `void`                                          | `setUserData``(`[`UserData`](UserData.md)` userData)`<br>Sets user data.                                          |
    | `java.lang.String`                              | `toString``()`                                                                                                    |

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### PointOnNet

          public PointOnNet(long nodeId)

      Constructs a PointOnNet for a node.
      Parameters:
      `nodeId` - node ID

    <!-- -->

    - #### PointOnNet

          public PointOnNet(long linkId,
                            double percentage)

      Constructs a PointOnNet for a point on link.
      Parameters:
      `linkId` - link ID

      `percentage` - percentage on the link

    <!-- -->

    - #### PointOnNet

          public PointOnNet(long nodeId,
                            CategorizedUserData cud)

      Constructs a PointOnNet for a node.
      Parameters:
      `nodeId` - node ID

      `cud` - categorized user data

    <!-- -->

    - #### PointOnNet

          public PointOnNet(long nodeId,
                            UserData userData)

      Constructs a PointOnNet for a node.
      Parameters:
      `nodeId` - node ID

      `userData` - user data

    <!-- -->

    - #### PointOnNet

          public PointOnNet(long linkId,
                            double percentage,
                            CategorizedUserData cud)

      Constructs a PointOnNet for a point on link.
      Parameters:
      `linkId` - link ID

      `percentage` - percentage on the link

      `cud` - categorized user data

    <!-- -->

    - #### PointOnNet

          public PointOnNet(long linkId,
                            double percentage,
                            UserData userData)

      Constructs a PointOnNet for a point on link.
      Parameters:
      `linkId` - link ID

      `percentage` - percentage on the link

      `userData` - user data

  <!-- -->

  - ### Method Detail

    - #### isNode

          public boolean isNode()

      Checks whether this point falls on a node or not.
      Returns:
      true if the point falls on a node; false, if the point falls on a link.

    <!-- -->

    - #### isPointOnLink

          public boolean isPointOnLink()

      Checks whether this point falls on a link or not.
      Returns:
      true if the point falls on a link; false, if the point falls on a node.

    <!-- -->

    - #### getNodeId

          public long getNodeId()

      Returns the node ID, if the point falls on a node.
      Returns:
      the node ID, if the point falls on a node.

    <!-- -->

    - #### getLinkId

          public long getLinkId()

      Returns the link ID, if the point falls on a link.
      Returns:
      the link ID, if the point falls on a link.

    <!-- -->

    - #### getPercentage

          public double getPercentage()

      Returns the percentage on the link, if the point falls on a link.
      Returns:
      the percentage on the link, if the point falls on a link.

    <!-- -->

    - #### getUserData

          public UserData getUserData()

      Returns the user data associated with this point on net in the default user data category.
      Returns:
      user data

    <!-- -->

    - #### setUserData

          public void setUserData(UserData userData)

      Sets user data. Overwrite previous value, if the user data already exists.
      Parameters:
      `userData` - user data

    <!-- -->

    - #### removeUserData

          public void removeUserData()

      Removes all user data associated to this object.

    <!-- -->

    - #### equals

          public boolean equals(java.lang.Object o)

      Overrides:
      `equals` in class `java.lang.Object`

    <!-- -->

    - #### hashCode

          public int hashCode()

      Overrides:
      `hashCode` in class `java.lang.Object`

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Object`

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

- [Prev Class](PointClustering.md)
- [Next Class](PriorityQueue.md)

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
