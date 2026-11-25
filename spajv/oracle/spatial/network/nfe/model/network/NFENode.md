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

- [Prev Class](NFENetworkMetadata.md)
- Next Class

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

## Class NFENode

- java.lang.Object

- - [oracle.spatial.network.nfe.model.NFEBasicModelObject](../NFEBasicModelObject.md)

  - - [oracle.spatial.network.nfe.model.network.NFENetworkElement](NFENetworkElement.md)

    - - oracle.spatial.network.nfe.model.network.NFENode

<!-- -->

- All Implemented Interfaces:
  [NFEModelObject](../NFEModelObject.md)

  <!-- -->

  Direct Known Subclasses:
  [NFEBasicNode](NFEBasicNode.md)

  ------------------------------------------------------------------------



      public abstract class NFENode
      extends NFENetworkElement

  Base class for representing a network node.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                                  |
    |---------------------------|--------------------------------------------------------|
    | `static java.lang.String` | `PROP_HIERARCHY_LEVEL`<br>The hierarchy level property |
    | `static java.lang.String` | `PROP_PARENT_NODE_ID`<br>The parent node id property   |

    - ### Fields inherited from class oracle.spatial.network.nfe.model.network.[NFENetworkElement](NFENetworkElement.md)

      [`PROP_ACTIVE`](NFENetworkElement.md)`, `[`PROP_COST`](NFENetworkElement.md)`, `[`PROP_GEOMETRY`](NFENetworkElement.md)`, `[`PROP_ID`](NFENetworkElement.md)`, `[`PROP_NAME`](NFENetworkElement.md)

    <!-- -->

    - ### Fields inherited from interface oracle.spatial.network.nfe.model.[NFEModelObject](../NFEModelObject.md)

      [`EFLAG_EXISTING`](../NFEModelObject.md)`, `[`EFLAG_REMOVED`](../NFEModelObject.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `NFENode``()`               |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                          | Method and Description                                                                |
    |------------------------------------------------------------|---------------------------------------------------------------------------------------|
    | `abstract int`                                             | `getHierarchyLevel``()`<br>Gets the node's hierarchy level                            |
    | `abstract java.util.Collection<`[`NFELink`](NFELink.md)`>` | `getInLinks``()`<br>Gets all the in-links connected to the node                       |
    | `java.lang.String`                                         | `getKey``()`<br>Gets the network element's key.                                       |
    | `abstract java.util.Collection<`[`NFELink`](NFELink.md)`>` | `getLinks``()`<br>Gets all the links (in and out) connected to the node               |
    | `abstract int`                                             | `getNumberOfInLinks``()`<br>Gets the number of in-links connected to the node         |
    | `abstract int`                                             | `getNumberOfLinks``()`<br>Gets the number of links (in and out) connected to the node |
    | `abstract int`                                             | `getNumberOfOutLinks``()`<br>Gets the number of out-links connected to the node       |
    | `abstract java.util.Collection<`[`NFELink`](NFELink.md)`>` | `getOutLinks``()`<br>Gets all the out-links connected to the node                     |
    | `abstract long`                                            | `getParentNodeId``()`<br>Gets the node's parent node id if any                        |
    | `abstract long`                                            | `getPartitionId``()`<br>Gets the node's partition id                                  |
    | `boolean`                                                  | `isLink``()`<br>Tells whether the network element is a link or not                    |
    | `boolean`                                                  | `isNode``()`<br>Tells whether the network element is a node or not                    |
    | `abstract void`                                            | `setHierarchyLevel``(int hierarchyLevel)`<br>Sets the node's hierarchy level          |
    | `abstract void`                                            | `setParentNodeId``(long parentNodeId)`<br>Sets the node's parent node id              |
    | `abstract void`                                            | `setPartitionId``(long partitionId)`<br>Sets the node's partition id                  |

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

    - #### PROP_HIERARCHY_LEVEL

          public static final java.lang.String PROP_HIERARCHY_LEVEL

      The hierarchy level property
      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

    <!-- -->

    - #### PROP_PARENT_NODE_ID

          public static final java.lang.String PROP_PARENT_NODE_ID

      The parent node id property
      See Also:
      [Constant Field Values](../../../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### NFENode

          public NFENode()

  <!-- -->

  - ### Method Detail

    - #### setHierarchyLevel

          public abstract void setHierarchyLevel(int hierarchyLevel)

      Sets the node's hierarchy level
      Parameters:
      `hierarchyLevel` - the node's hierarchy level

    <!-- -->

    - #### getHierarchyLevel

          public abstract int getHierarchyLevel()

      Gets the node's hierarchy level
      Returns:
      the nodes hierarchy level

    <!-- -->

    - #### setParentNodeId

          public abstract void setParentNodeId(long parentNodeId)

      Sets the node's parent node id
      Parameters:
      `parentNodeId` - the node's parent node id

    <!-- -->

    - #### getParentNodeId

          public abstract long getParentNodeId()

      Gets the node's parent node id if any
      Returns:
      the node's parent node id or -1 if it does not have a parent node

    <!-- -->

    - #### getLinks

          public abstract java.util.Collection<NFELink> getLinks()

      Gets all the links (in and out) connected to the node
      Returns:
      a collection containing all the links connected to the node as instances of NFELink

    <!-- -->

    - #### getInLinks

          public abstract java.util.Collection<NFELink> getInLinks()

      Gets all the in-links connected to the node
      Returns:
      a collection containing all the in-links connected to the node as instances of NFELink

    <!-- -->

    - #### getOutLinks

          public abstract java.util.Collection<NFELink> getOutLinks()

      Gets all the out-links connected to the node
      Returns:
      a collection containing all the out-links connected to the node as instances of NFELink

    <!-- -->

    - #### getNumberOfLinks

          public abstract int getNumberOfLinks()

      Gets the number of links (in and out) connected to the node
      Returns:
      the total number of connected links

    <!-- -->

    - #### getNumberOfInLinks

          public abstract int getNumberOfInLinks()

      Gets the number of in-links connected to the node
      Returns:
      the total number of connected in-links

    <!-- -->

    - #### getNumberOfOutLinks

          public abstract int getNumberOfOutLinks()

      Gets the number of out-links connected to the node
      Returns:
      the total number of connected out-links

    <!-- -->

    - #### getPartitionId

          public abstract long getPartitionId()

      Gets the node's partition id
      Returns:
      the node's partition id

    <!-- -->

    - #### setPartitionId

          public abstract void setPartitionId(long partitionId)

      Sets the node's partition id
      Parameters:
      `partitionId` - the node's partition id

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

- [Prev Class](NFENetworkMetadata.md)
- Next Class

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
