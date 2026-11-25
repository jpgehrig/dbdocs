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

- [Prev Class](GoalNodeOperator.md)
- [Next Class](HeuristicCostFunction.md)

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

## Class HeavyPointOnNet

- java.lang.Object

- - [oracle.spatial.network.lod.PointOnNet](PointOnNet.md)

  - - oracle.spatial.network.lod.HeavyPointOnNet

<!-- -->

-

  ------------------------------------------------------------------------



      public class HeavyPointOnNet
      extends PointOnNet

  A HeavyPointOnNet is a PointOnNet with reference to the underlying LogialNode and LogicalLink object.
  Since:
  Oracle Database 11g Release 2 (11.2)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                      |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `HeavyPointOnNet``(`[`LogicalLink`](LogicalLink.md)` link, double percentage, `[`UserData`](UserData.md)` userData)`<br>Constructs a HeavyPointOnNet object for a point on link. |
    | `HeavyPointOnNet``(`[`LogicalNode`](LogicalNode.md)` node, `[`CategorizedUserData`](CategorizedUserData.md)` userData)`<br>Constructs a HeavyPointOnNet object for a node.       |
    | `HeavyPointOnNet``(`[`LogicalNode`](LogicalNode.md)` node, `[`UserData`](UserData.md)` userData)`<br>Constructs a HeavyPointOnNet object for a node.                             |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                               | Method and Description                                                                                            |
    |-------------------------------------------------|-------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object`                              | `clone``()`<br>Support cloneable                                                                                  |
    | [`CategorizedUserData`](CategorizedUserData.md) | `getCategorizedUserData``()`<br>Returns categorized user data.                                                    |
    | [`LogicalLink`](LogicalLink.md)                 | `getLink``()`<br>Returns link.                                                                                    |
    | [`LogicalNode`](LogicalNode.md)                 | `getNode``()`<br>Returns node.                                                                                    |
    | [`UserData`](UserData.md)                       | `getUserData``(int category)`<br>Returns user data for the specified category.                                    |
    | `void`                                          | `setCategorizedUserData``(`[`CategorizedUserData`](CategorizedUserData.md)` cud)`<br>Sets categorized user data.  |
    | `void`                                          | `setUserData``(int category, `[`UserData`](UserData.md)` userData)`<br>Sets user data for the specified category. |

    - ### Methods inherited from class oracle.spatial.network.lod.[PointOnNet](PointOnNet.md)

      [`equals`](PointOnNet.md)`, `[`getLinkId`](PointOnNet.md)`, `[`getNodeId`](PointOnNet.md)`, `[`getPercentage`](PointOnNet.md)`, `[`getUserData`](PointOnNet.md)`, `[`hashCode`](PointOnNet.md)`, `[`isNode`](PointOnNet.md)`, `[`isPointOnLink`](PointOnNet.md)`, `[`removeUserData`](PointOnNet.md)`, `[`setUserData`](PointOnNet.md)`, `[`toString`](PointOnNet.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### HeavyPointOnNet

          public HeavyPointOnNet(LogicalNode node,
                                 UserData userData)

      Constructs a HeavyPointOnNet object for a node.
      Parameters:
      `node` - node

      `userData` - user data

    <!-- -->

    - #### HeavyPointOnNet

          public HeavyPointOnNet(LogicalNode node,
                                 CategorizedUserData userData)

      Constructs a HeavyPointOnNet object for a node.
      Parameters:
      `node` - node

      `userData` - user data

    <!-- -->

    - #### HeavyPointOnNet

          public HeavyPointOnNet(LogicalLink link,
                                 double percentage,
                                 UserData userData)

      Constructs a HeavyPointOnNet object for a point on link.
      Parameters:
      `link` - link

      `userData` - user data

  <!-- -->

  - ### Method Detail

    - #### getNode

          public LogicalNode getNode()

      Returns node. The caller must make sure this HeavyPointOnNet object is a node.
      Returns:

    <!-- -->

    - #### getLink

          public LogicalLink getLink()

      Returns link. The caller must make sure this HeavyPointOnNet object is a point on link.
      Returns:

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

- [Prev Class](GoalNodeOperator.md)
- [Next Class](HeuristicCostFunction.md)

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
