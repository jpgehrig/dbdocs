Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- Prev Class
- [Next Class](NFEBasicNetwork.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.model.network

## Class NFEBasicLink

- java.lang.Object

- - [oracle.spatial.network.nfe.model.NFEBasicModelObject](../NFEBasicModelObject.md)

  - - [oracle.spatial.network.nfe.model.network.NFENetworkElement](NFENetworkElement.md)

    - - [oracle.spatial.network.nfe.model.network.NFELink](NFELink.md)

      - - oracle.spatial.network.nfe.model.network.NFEBasicLink

<!-- -->

- All Implemented Interfaces:
  [NFEModelObject](../NFEModelObject.md)

  ------------------------------------------------------------------------



      public class NFEBasicLink
      extends NFELink

  The default implementation of [`NFELink`](NFELink.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from class oracle.spatial.network.nfe.model.network.[NFELink](NFELink.md)

      [`PROP_BIDIRECTED`](NFELink.md)`, `[`PROP_END_NODE`](NFELink.md)`, `[`PROP_LEVEL`](NFELink.md)`, `[`PROP_PARENT_LINK_ID`](NFELink.md)`, `[`PROP_START_NODE`](NFELink.md)

    <!-- -->

    - ### Fields inherited from class oracle.spatial.network.nfe.model.network.[NFENetworkElement](NFENetworkElement.md)

      [`PROP_ACTIVE`](NFENetworkElement.md)`, `[`PROP_COST`](NFENetworkElement.md)`, `[`PROP_GEOMETRY`](NFENetworkElement.md)`, `[`PROP_ID`](NFENetworkElement.md)`, `[`PROP_NAME`](NFENetworkElement.md)

    <!-- -->

    - ### Fields inherited from interface oracle.spatial.network.nfe.model.[NFEModelObject](../NFEModelObject.md)

      [`EFLAG_EXISTING`](../NFEModelObject.md)`, `[`EFLAG_REMOVED`](../NFEModelObject.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                               |
    |-------------------------------------------------------------------------------------------|
    | `NFEBasicLink``(`[`NFENode`](NFENode.md)` startNode, `[`NFENode`](NFENode.md)` endNode)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                           | Method and Description                                                              |
    |---------------------------------------------|-------------------------------------------------------------------------------------|
    | [`NFENetworkElement`](NFENetworkElement.md) | `createCopy``()`<br>Returns object copy.                                            |
    | `int`                                       | `getLevel``()`<br>Gets the link's level                                             |
    | `long`                                      | `getParentLinkId``()`<br>Gets the link's parent link ID (if any)                    |
    | `boolean`                                   | `isBidirected``()`<br>Tells whether the link is bidirected or not                   |
    | `void`                                      | `setBidirected``(boolean bidirected)`<br>Sets whether the link is bidirected or not |
    | `void`                                      | `setLevel``(int level)`<br>Sets the link's level                                    |
    | `void`                                      | `setParentLinkId``(long parentLinkId)`<br>Sets the link's parent link ID            |

    - ### Methods inherited from class oracle.spatial.network.nfe.model.network.[NFELink](NFELink.md)

      [`getEndNode`](NFELink.md)`, `[`getKey`](NFELink.md)`, `[`getStartNode`](NFELink.md)`, `[`isLink`](NFELink.md)`, `[`isNode`](NFELink.md)

    <!-- -->

    - ### Methods inherited from class oracle.spatial.network.nfe.model.network.[NFENetworkElement](NFENetworkElement.md)

      [`getCost`](NFENetworkElement.md)`, `[`getGeometry`](NFENetworkElement.md)`, `[`getId`](NFENetworkElement.md)`, `[`getName`](NFENetworkElement.md)`, `[`getNetwork`](NFENetworkElement.md)`, `[`isActive`](NFENetworkElement.md)`, `[`setActive`](NFENetworkElement.md)`, `[`setCost`](NFENetworkElement.md)`, `[`setGeometry`](NFENetworkElement.md)`, `[`setId`](NFENetworkElement.md)`, `[`setName`](NFENetworkElement.md)`, `[`setNetwork`](NFENetworkElement.md)

    <!-- -->

    - ### Methods inherited from class oracle.spatial.network.nfe.model.[NFEBasicModelObject](../NFEBasicModelObject.md)

      [`addEditionFlag`](../NFEBasicModelObject.md)`, `[`containsEditionFlag`](../NFEBasicModelObject.md)`, `[`getEditionFlags`](../NFEBasicModelObject.md)`, `[`removeEditionFlag`](../NFEBasicModelObject.md)`, `[`setEditionFlags`](../NFEBasicModelObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEBasicLink

          public NFEBasicLink(NFENode startNode,
                              NFENode endNode)

  <!-- -->

  - ### Method Detail

    - #### setLevel

          public void setLevel(int level)

      Description copied from class: [`NFELink`](NFELink.md)
      Sets the link's level
      Specified by:
      [`setLevel`](NFELink.md) in class [`NFELink`](NFELink.md)

      Parameters:
      `level` - the link's level

    <!-- -->

    - #### getLevel

          public int getLevel()

      Description copied from class: [`NFELink`](NFELink.md)
      Gets the link's level
      Specified by:
      [`getLevel`](NFELink.md) in class [`NFELink`](NFELink.md)

      Returns:
      the link's level

    <!-- -->

    - #### setBidirected

          public void setBidirected(boolean bidirected)

      Description copied from class: [`NFELink`](NFELink.md)
      Sets whether the link is bidirected or not
      Specified by:
      [`setBidirected`](NFELink.md) in class [`NFELink`](NFELink.md)

      Parameters:
      `bidirected` - true for bidirected, false for single direction

    <!-- -->

    - #### isBidirected

          public boolean isBidirected()

      Description copied from class: [`NFELink`](NFELink.md)
      Tells whether the link is bidirected or not
      Specified by:
      [`isBidirected`](NFELink.md) in class [`NFELink`](NFELink.md)

      Returns:
      true for bidirected, false for single direction

    <!-- -->

    - #### setParentLinkId

          public void setParentLinkId(long parentLinkId)

      Description copied from class: [`NFELink`](NFELink.md)
      Sets the link's parent link ID
      Specified by:
      [`setParentLinkId`](NFELink.md) in class [`NFELink`](NFELink.md)

      Parameters:
      `parentLinkId` - the link's parent link ID

    <!-- -->

    - #### getParentLinkId

          public long getParentLinkId()

      Description copied from class: [`NFELink`](NFELink.md)
      Gets the link's parent link ID (if any)
      Specified by:
      [`getParentLinkId`](NFELink.md) in class [`NFELink`](NFELink.md)

      Returns:
      the link's parent link ID or -1 if the link does not have a parent link

    <!-- -->

    - #### createCopy

          public NFENetworkElement createCopy()

      Description copied from class: [`NFENetworkElement`](NFENetworkElement.md)
      Returns object copy.
      Specified by:
      [`createCopy`](NFENetworkElement.md) in class [`NFENetworkElement`](NFENetworkElement.md)

      Returns:
      object copy

Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- Prev Class
- [Next Class](NFEBasicNetwork.md)

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

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
