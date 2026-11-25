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

- [Prev Class](NFEBasicNode.md)
- [Next Class](NFENetwork.md)

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

## Class NFELink

- java.lang.Object

- - [oracle.spatial.network.nfe.model.NFEBasicModelObject](../NFEBasicModelObject.md)

  - - [oracle.spatial.network.nfe.model.network.NFENetworkElement](NFENetworkElement.md)

    - - oracle.spatial.network.nfe.model.network.NFELink

<!-- -->

- All Implemented Interfaces:
  [NFEModelObject](../NFEModelObject.md)

  <!-- -->

  Direct Known Subclasses:
  [NFEBasicLink](NFEBasicLink.md)

  ------------------------------------------------------------------------



      public abstract class NFELink
      extends NFENetworkElement

  Base class for representing network links.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                            |
    |---------------------------|--------------------------------------------------|
    | `static java.lang.String` | `PROP_BIDIRECTED`<br>Link bidirected property    |
    | `static java.lang.String` | `PROP_END_NODE`<br>Link's end node property      |
    | `static java.lang.String` | `PROP_LEVEL`<br>Link level property              |
    | `static java.lang.String` | `PROP_PARENT_LINK_ID`<br>Parent link id property |
    | `static java.lang.String` | `PROP_START_NODE`<br>Link's start node property  |

    - ### Fields inherited from class oracle.spatial.network.nfe.model.network.[NFENetworkElement](NFENetworkElement.md)

      [`PROP_ACTIVE`](NFENetworkElement.md)`, `[`PROP_COST`](NFENetworkElement.md)`, `[`PROP_GEOMETRY`](NFENetworkElement.md)`, `[`PROP_ID`](NFENetworkElement.md)`, `[`PROP_NAME`](NFENetworkElement.md)

    <!-- -->

    - ### Fields inherited from interface oracle.spatial.network.nfe.model.[NFEModelObject](../NFEModelObject.md)

      [`EFLAG_EXISTING`](../NFEModelObject.md)`, `[`EFLAG_REMOVED`](../NFEModelObject.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                          |
    |--------------------------------------------------------------------------------------|
    | `NFELink``(`[`NFENode`](NFENode.md)` startNode, `[`NFENode`](NFENode.md)` endNode)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type       | Method and Description                                                              |
    |-------------------------|-------------------------------------------------------------------------------------|
    | [`NFENode`](NFENode.md) | `getEndNode``()`<br>Gets the link's end node                                        |
    | `java.lang.String`      | `getKey``()`<br>Gets the network element's key.                                     |
    | `abstract int`          | `getLevel``()`<br>Gets the link's level                                             |
    | `abstract long`         | `getParentLinkId``()`<br>Gets the link's parent link ID (if any)                    |
    | [`NFENode`](NFENode.md) | `getStartNode``()`<br>Gets the link's start node                                    |
    | `abstract boolean`      | `isBidirected``()`<br>Tells whether the link is bidirected or not                   |
    | `boolean`               | `isLink``()`<br>Tells whether the network element is a link or not                  |
    | `boolean`               | `isNode``()`<br>Tells whether the network element is a node or not                  |
    | `abstract void`         | `setBidirected``(boolean bidirected)`<br>Sets whether the link is bidirected or not |
    | `abstract void`         | `setLevel``(int level)`<br>Sets the link's level                                    |
    | `abstract void`         | `setParentLinkId``(long parentLinkId)`<br>Sets the link's parent link ID            |

    - ### Methods inherited from class oracle.spatial.network.nfe.model.network.[NFENetworkElement](NFENetworkElement.md)

      [`createCopy`](NFENetworkElement.md)`, `[`getCost`](NFENetworkElement.md)`, `[`getGeometry`](NFENetworkElement.md)`, `[`getId`](NFENetworkElement.md)`, `[`getName`](NFENetworkElement.md)`, `[`getNetwork`](NFENetworkElement.md)`, `[`isActive`](NFENetworkElement.md)`, `[`setActive`](NFENetworkElement.md)`, `[`setCost`](NFENetworkElement.md)`, `[`setGeometry`](NFENetworkElement.md)`, `[`setId`](NFENetworkElement.md)`, `[`setName`](NFENetworkElement.md)`, `[`setNetwork`](NFENetworkElement.md)

    <!-- -->

    - ### Methods inherited from class oracle.spatial.network.nfe.model.[NFEBasicModelObject](../NFEBasicModelObject.md)

      [`addEditionFlag`](../NFEBasicModelObject.md)`, `[`containsEditionFlag`](../NFEBasicModelObject.md)`, `[`getEditionFlags`](../NFEBasicModelObject.md)`, `[`removeEditionFlag`](../NFEBasicModelObject.md)`, `[`setEditionFlags`](../NFEBasicModelObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### PROP_LEVEL

          public static final java.lang.String PROP_LEVEL

      Link level property
      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

    <!-- -->

    - #### PROP_BIDIRECTED

          public static final java.lang.String PROP_BIDIRECTED

      Link bidirected property
      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

    <!-- -->

    - #### PROP_PARENT_LINK_ID

          public static final java.lang.String PROP_PARENT_LINK_ID

      Parent link id property
      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

    <!-- -->

    - #### PROP_START_NODE

          public static final java.lang.String PROP_START_NODE

      Link's start node property
      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

    <!-- -->

    - #### PROP_END_NODE

          public static final java.lang.String PROP_END_NODE

      Link's end node property
      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### NFELink

          public NFELink(NFENode startNode,
                         NFENode endNode)

  <!-- -->

  - ### Method Detail

    - #### setLevel

          public abstract void setLevel(int level)

      Sets the link's level
      Parameters:
      `level` - the link's level

    <!-- -->

    - #### getLevel

          public abstract int getLevel()

      Gets the link's level
      Returns:
      the link's level

    <!-- -->

    - #### setBidirected

          public abstract void setBidirected(boolean bidirected)

      Sets whether the link is bidirected or not
      Parameters:
      `bidirected` - true for bidirected, false for single direction

    <!-- -->

    - #### isBidirected

          public abstract boolean isBidirected()

      Tells whether the link is bidirected or not
      Returns:
      true for bidirected, false for single direction

    <!-- -->

    - #### setParentLinkId

          public abstract void setParentLinkId(long parentLinkId)

      Sets the link's parent link ID
      Parameters:
      `parentLinkId` - the link's parent link ID

    <!-- -->

    - #### getParentLinkId

          public abstract long getParentLinkId()

      Gets the link's parent link ID (if any)
      Returns:
      the link's parent link ID or -1 if the link does not have a parent link

    <!-- -->

    - #### getStartNode

          public NFENode getStartNode()

      Gets the link's start node
      Returns:
      an NFENode instance

    <!-- -->

    - #### getEndNode

          public NFENode getEndNode()

      Gets the link's end node
      Returns:
      an NFENode instance

    <!-- -->

    - #### isNode

          public boolean isNode()

      Description copied from class: [`NFENetworkElement`](NFENetworkElement.md)
      Tells whether the network element is a node or not
      Specified by:
      [`isNode`](NFENetworkElement.md) in class [`NFENetworkElement`](NFENetworkElement.md)

      Returns:
      true if the network element is a node

    <!-- -->

    - #### isLink

          public boolean isLink()

      Description copied from class: [`NFENetworkElement`](NFENetworkElement.md)
      Tells whether the network element is a link or not
      Specified by:
      [`isLink`](NFENetworkElement.md) in class [`NFENetworkElement`](NFENetworkElement.md)

      Returns:
      true if the network element is a link

    <!-- -->

    - #### getKey

          public java.lang.String getKey()

      Description copied from class: [`NFENetworkElement`](NFENetworkElement.md)
      Gets the network element's key. The key is a unique value to differentiate a network element among other network elements in the same network. There could be a node and a link with the same ID but cannot exist two network elements (node or links) with the same key
      Specified by:
      [`getKey`](NFENetworkElement.md) in class [`NFENetworkElement`](NFENetworkElement.md)

      Returns:
      the network element's key

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

- [Prev Class](NFEBasicNode.md)
- [Next Class](NFENetwork.md)

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
