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

- [Prev Class](NFEBasicNetwork.md)
- [Next Class](NFELink.md)

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

## Class NFEBasicNode

- java.lang.Object

- - [oracle.spatial.network.nfe.model.NFEBasicModelObject](../NFEBasicModelObject.md)

  - - [oracle.spatial.network.nfe.model.network.NFENetworkElement](NFENetworkElement.md)

    - - [oracle.spatial.network.nfe.model.network.NFENode](NFENode.md)

      - - oracle.spatial.network.nfe.model.network.NFEBasicNode

<!-- -->

- All Implemented Interfaces:
  [NFEModelObject](../NFEModelObject.md)

  ------------------------------------------------------------------------



      public class NFEBasicNode
      extends NFENode

  The default implementation of [`NFENode`](NFENode.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from class oracle.spatial.network.nfe.model.network.[NFENode](NFENode.md)

      [`PROP_HIERARCHY_LEVEL`](NFENode.md)`, `[`PROP_PARENT_NODE_ID`](NFENode.md)

    <!-- -->

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
    | `NFEBasicNode``()`          |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                 | Method and Description                                                                |
    |---------------------------------------------------|---------------------------------------------------------------------------------------|
    | [`NFENetworkElement`](NFENetworkElement.md)       | `createCopy``()`<br>Returns object copy.                                              |
    | `int`                                             | `getHierarchyLevel``()`<br>Gets the node's hierarchy level                            |
    | `java.util.Collection<`[`NFELink`](NFELink.md)`>` | `getInLinks``()`<br>Gets all the in-links connected to the node                       |
    | `java.util.Collection<`[`NFELink`](NFELink.md)`>` | `getLinks``()`<br>Gets all the links (in and out) connected to the node               |
    | `int`                                             | `getNumberOfInLinks``()`<br>Gets the number of in-links connected to the node         |
    | `int`                                             | `getNumberOfLinks``()`<br>Gets the number of links (in and out) connected to the node |
    | `int`                                             | `getNumberOfOutLinks``()`<br>Gets the number of out-links connected to the node       |
    | `java.util.Collection<`[`NFELink`](NFELink.md)`>` | `getOutLinks``()`<br>Gets all the out-links connected to the node                     |
    | `long`                                            | `getParentNodeId``()`<br>Gets the node's parent node id if any                        |
    | `long`                                            | `getPartitionId``()`<br>Gets the node's partition id                                  |
    | `void`                                            | `setHierarchyLevel``(int hierarchyLevel)`<br>Sets the node's hierarchy level          |
    | `void`                                            | `setParentNodeId``(long parentNodeId)`<br>Sets the node's parent node id              |
    | `void`                                            | `setPartitionId``(long partitionId)`<br>Sets the node's partition id                  |

    - ### Methods inherited from class oracle.spatial.network.nfe.model.network.[NFENode](NFENode.md)

      [`getKey`](NFENode.md)`, `[`isLink`](NFENode.md)`, `[`isNode`](NFENode.md)

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

    - #### NFEBasicNode

          public NFEBasicNode()

  <!-- -->

  - ### Method Detail

    - #### setHierarchyLevel

          public void setHierarchyLevel(int hierarchyLevel)

      Description copied from class: [`NFENode`](NFENode.md)
      Sets the node's hierarchy level
      Specified by:
      [`setHierarchyLevel`](NFENode.md) in class [`NFENode`](NFENode.md)

      Parameters:
      `hierarchyLevel` - the node's hierarchy level

    <!-- -->

    - #### getHierarchyLevel

          public int getHierarchyLevel()

      Description copied from class: [`NFENode`](NFENode.md)
      Gets the node's hierarchy level
      Specified by:
      [`getHierarchyLevel`](NFENode.md) in class [`NFENode`](NFENode.md)

      Returns:
      the nodes hierarchy level

    <!-- -->

    - #### setParentNodeId

          public void setParentNodeId(long parentNodeId)

      Description copied from class: [`NFENode`](NFENode.md)
      Sets the node's parent node id
      Specified by:
      [`setParentNodeId`](NFENode.md) in class [`NFENode`](NFENode.md)

      Parameters:
      `parentNodeId` - the node's parent node id

    <!-- -->

    - #### getParentNodeId

          public long getParentNodeId()

      Description copied from class: [`NFENode`](NFENode.md)
      Gets the node's parent node id if any
      Specified by:
      [`getParentNodeId`](NFENode.md) in class [`NFENode`](NFENode.md)

      Returns:
      the node's parent node id or -1 if it does not have a parent node

    <!-- -->

    - #### getLinks

          public java.util.Collection<NFELink> getLinks()

      Description copied from class: [`NFENode`](NFENode.md)
      Gets all the links (in and out) connected to the node
      Specified by:
      [`getLinks`](NFENode.md) in class [`NFENode`](NFENode.md)

      Returns:
      a collection containing all the links connected to the node as instances of NFELink

    <!-- -->

    - #### getInLinks

          public java.util.Collection<NFELink> getInLinks()

      Description copied from class: [`NFENode`](NFENode.md)
      Gets all the in-links connected to the node
      Specified by:
      [`getInLinks`](NFENode.md) in class [`NFENode`](NFENode.md)

      Returns:
      a collection containing all the in-links connected to the node as instances of NFELink

    <!-- -->

    - #### getOutLinks

          public java.util.Collection<NFELink> getOutLinks()

      Description copied from class: [`NFENode`](NFENode.md)
      Gets all the out-links connected to the node
      Specified by:
      [`getOutLinks`](NFENode.md) in class [`NFENode`](NFENode.md)

      Returns:
      a collection containing all the out-links connected to the node as instances of NFELink

    <!-- -->

    - #### getNumberOfLinks

          public int getNumberOfLinks()

      Description copied from class: [`NFENode`](NFENode.md)
      Gets the number of links (in and out) connected to the node
      Specified by:
      [`getNumberOfLinks`](NFENode.md) in class [`NFENode`](NFENode.md)

      Returns:
      the total number of connected links

    <!-- -->

    - #### getNumberOfInLinks

          public int getNumberOfInLinks()

      Description copied from class: [`NFENode`](NFENode.md)
      Gets the number of in-links connected to the node
      Specified by:
      [`getNumberOfInLinks`](NFENode.md) in class [`NFENode`](NFENode.md)

      Returns:
      the total number of connected in-links

    <!-- -->

    - #### getNumberOfOutLinks

          public int getNumberOfOutLinks()

      Description copied from class: [`NFENode`](NFENode.md)
      Gets the number of out-links connected to the node
      Specified by:
      [`getNumberOfOutLinks`](NFENode.md) in class [`NFENode`](NFENode.md)

      Returns:
      the total number of connected out-links

    <!-- -->

    - #### getPartitionId

          public long getPartitionId()

      Description copied from class: [`NFENode`](NFENode.md)
      Gets the node's partition id
      Specified by:
      [`getPartitionId`](NFENode.md) in class [`NFENode`](NFENode.md)

      Returns:
      the node's partition id

    <!-- -->

    - #### setPartitionId

          public void setPartitionId(long partitionId)

      Description copied from class: [`NFENode`](NFENode.md)
      Sets the node's partition id
      Specified by:
      [`setPartitionId`](NFENode.md) in class [`NFENode`](NFENode.md)

      Parameters:
      `partitionId` - the node's partition id

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

- [Prev Class](NFEBasicNetwork.md)
- [Next Class](NFELink.md)

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
