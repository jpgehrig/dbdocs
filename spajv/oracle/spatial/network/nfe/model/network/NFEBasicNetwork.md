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

- [Prev Class](NFEBasicLink.md)
- [Next Class](NFEBasicNode.md)

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

## Class NFEBasicNetwork

- java.lang.Object

- - [oracle.spatial.network.nfe.model.network.NFENetwork](NFENetwork.md)

  - - oracle.spatial.network.nfe.model.network.NFEBasicNetwork

<!-- -->

-

  ------------------------------------------------------------------------



      public class NFEBasicNetwork
      extends NFENetwork

  The default implementation of [`NFENetwork`](NFENetwork.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `NFEBasicNetwork``()`       |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                 | Method and Description                                                                                                                                         |
    |---------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                         | `addLink``(`[`NFELink`](NFELink.md)` link)`<br>Adds an existing link to the network.                                                                           |
    | `boolean`                                         | `addLink``(`[`NFELink`](NFELink.md)` link, long startNodeId, long endNodeId)`<br>Adds an existing link to the network and sets the link's start and end nodes. |
    | `void`                                            | `addLinks``(java.util.Collection<`[`NFELink`](NFELink.md)`> links)`<br>Adds all the links contained in the given collection.                                   |
    | `void`                                            | `addModelListener``(`[`NFEModelListener`](../event/NFEModelListener.md)` listener)`<br>Subscribes a model listener instance to this class                      |
    | `boolean`                                         | `addNode``(`[`NFENode`](NFENode.md)` node)`<br>Adds an existing node to the network.                                                                           |
    | `void`                                            | `addNodes``(java.util.Collection<`[`NFENode`](NFENode.md)`> nodes)`<br>Adds a collection of nodes to the network                                               |
    | `boolean`                                         | `changeLinkEndNode``(long linkId, long endNodeId)`<br>Changes the end node of the link identified by linkId to the node identified by endNodeId                |
    | `boolean`                                         | `changeLinkStartNode``(long linkId, long startNodeId)`<br>Changes the start node of the link identified by linkId to the node identified by startNodeId        |
    | `boolean`                                         | `contains``(`[`NFENetworkElement`](NFENetworkElement.md)` networkElement)`<br>Tells whether the network contains the given networkElement or not               |
    | [`NFELink`](NFELink.md)                           | `getLink``(long linkId)`<br>Gets the link identified by the given ID.                                                                                          |
    | `java.util.Collection<`[`NFELink`](NFELink.md)`>` | `getLinks``()`<br>Gets all the links contained in the network                                                                                                  |
    | [`NFENode`](NFENode.md)                           | `getNode``(long nodeId)`<br>Gets the node identified by the given ID.                                                                                          |
    | `java.util.Collection<`[`NFENode`](NFENode.md)`>` | `getNodes``()`<br>Gets all the nodes contained in the network                                                                                                  |
    | [`NFELink`](NFELink.md)                           | `removeLink``(long linkId)`<br>Removes a link identified by the given ID from the network                                                                      |
    | `void`                                            | `removeModelListener``(`[`NFEModelListener`](../event/NFEModelListener.md)` listener)`<br>Removes the given model listener from this class                     |
    | [`NFENode`](NFENode.md)                           | `removeNode``(long nodeId)`<br>Removes a node identified by the given ID from the network                                                                      |

    - ### Methods inherited from class oracle.spatial.network.nfe.model.network.[NFENetwork](NFENetwork.md)

      [`getEventDispatcher`](NFENetwork.md)`, `[`getId`](NFENetwork.md)`, `[`getMetadata`](NFENetwork.md)`, `[`getName`](NFENetwork.md)`, `[`setEventDispatcher`](NFENetwork.md)`, `[`setId`](NFENetwork.md)`, `[`setMetadata`](NFENetwork.md)`, `[`setName`](NFENetwork.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEBasicNetwork

          public NFEBasicNetwork()

  <!-- -->

  - ### Method Detail

    - #### getNodes

          public java.util.Collection<NFENode> getNodes()

      Description copied from class: [`NFENetwork`](NFENetwork.md)
      Gets all the nodes contained in the network
      Specified by:
      [`getNodes`](NFENetwork.md) in class [`NFENetwork`](NFENetwork.md)

      Returns:
      a collection of NFENode instances

    <!-- -->

    - #### getLinks

          public java.util.Collection<NFELink> getLinks()

      Description copied from class: [`NFENetwork`](NFENetwork.md)
      Gets all the links contained in the network
      Specified by:
      [`getLinks`](NFENetwork.md) in class [`NFENetwork`](NFENetwork.md)

      Returns:
      a collection of NFELink instances

    <!-- -->

    - #### getNode

          public NFENode getNode(long nodeId)

      Description copied from class: [`NFENetwork`](NFENetwork.md)
      Gets the node identified by the given ID.
      Specified by:
      [`getNode`](NFENetwork.md) in class [`NFENetwork`](NFENetwork.md)

      Parameters:
      `nodeId` - a node ID

      Returns:
      an NFENode instance or null if it was not found

    <!-- -->

    - #### getLink

          public NFELink getLink(long linkId)

      Description copied from class: [`NFENetwork`](NFENetwork.md)
      Gets the link identified by the given ID.
      Specified by:
      [`getLink`](NFENetwork.md) in class [`NFENetwork`](NFENetwork.md)

      Parameters:
      `linkId` - a link ID

      Returns:
      an NFELink instance or null if it was not found

    <!-- -->

    - #### contains

          public boolean contains(NFENetworkElement networkElement)

      Description copied from class: [`NFENetwork`](NFENetwork.md)
      Tells whether the network contains the given networkElement or not
      Specified by:
      [`contains`](NFENetwork.md) in class [`NFENetwork`](NFENetwork.md)

      Parameters:
      `networkElement` - a network element instance (a node or a link)

      Returns:
      true if the network contains the element

    <!-- -->

    - #### addNode

          public boolean addNode(NFENode node)

      Description copied from class: [`NFENetwork`](NFENetwork.md)
      Adds an existing node to the network.
      Specified by:
      [`addNode`](NFENetwork.md) in class [`NFENetwork`](NFENetwork.md)

      Parameters:
      `node` - an NFENode instance

      Returns:
      true if the node was added

    <!-- -->

    - #### addNodes

          public void addNodes(java.util.Collection<NFENode> nodes)

      Description copied from class: [`NFENetwork`](NFENetwork.md)
      Adds a collection of nodes to the network
      Specified by:
      [`addNodes`](NFENetwork.md) in class [`NFENetwork`](NFENetwork.md)

      Parameters:
      `nodes` - a collection of nodes

    <!-- -->

    - #### addLink

          public boolean addLink(NFELink link,
                                 long startNodeId,
                                 long endNodeId)

      Description copied from class: [`NFENetwork`](NFENetwork.md)
      Adds an existing link to the network and sets the link's start and end nodes.
      Specified by:
      [`addLink`](NFENetwork.md) in class [`NFENetwork`](NFENetwork.md)

      Parameters:
      `link` - an NFELink instance

      `startNodeId` - the ID of a node contained in the network

      `endNodeId` - the ID of a node contained in the network

      Returns:
      true if the link was added

    <!-- -->

    - #### addLink

          public boolean addLink(NFELink link)

      Description copied from class: [`NFENetwork`](NFENetwork.md)
      Adds an existing link to the network. The link's start and end nodes must be contained in the network.
      Specified by:
      [`addLink`](NFENetwork.md) in class [`NFENetwork`](NFENetwork.md)

      Parameters:
      `link` - an NFELink instance.

      Returns:
      true if the link was added

    <!-- -->

    - #### addLinks

          public void addLinks(java.util.Collection<NFELink> links)

      Description copied from class: [`NFENetwork`](NFENetwork.md)
      Adds all the links contained in the given collection. All the links must have a start and end node already contained in the network.
      Specified by:
      [`addLinks`](NFENetwork.md) in class [`NFENetwork`](NFENetwork.md)

      Parameters:
      `links` - a collection of links

    <!-- -->

    - #### removeNode

          public NFENode removeNode(long nodeId)

      Description copied from class: [`NFENetwork`](NFENetwork.md)
      Removes a node identified by the given ID from the network
      Specified by:
      [`removeNode`](NFENetwork.md) in class [`NFENetwork`](NFENetwork.md)

      Parameters:
      `nodeId` - a node ID

      Returns:
      the removed NFENode instance or null if it was not found or could not be removed

    <!-- -->

    - #### removeLink

          public NFELink removeLink(long linkId)

      Description copied from class: [`NFENetwork`](NFENetwork.md)
      Removes a link identified by the given ID from the network
      Specified by:
      [`removeLink`](NFENetwork.md) in class [`NFENetwork`](NFENetwork.md)

      Parameters:
      `linkId` - a link ID

      Returns:
      the removed NFELink instance or null if it was not found or could not be removed

    <!-- -->

    - #### changeLinkStartNode

          public boolean changeLinkStartNode(long linkId,
                                             long startNodeId)

      Description copied from class: [`NFENetwork`](NFENetwork.md)
      Changes the start node of the link identified by linkId to the node identified by startNodeId
      Specified by:
      [`changeLinkStartNode`](NFENetwork.md) in class [`NFENetwork`](NFENetwork.md)

      Parameters:
      `linkId` - the ID of a link contained in the network

      `startNodeId` - the ID of a node contained in the network

      Returns:
      true if the node was changed

    <!-- -->

    - #### changeLinkEndNode

          public boolean changeLinkEndNode(long linkId,
                                           long endNodeId)

      Description copied from class: [`NFENetwork`](NFENetwork.md)
      Changes the end node of the link identified by linkId to the node identified by endNodeId
      Specified by:
      [`changeLinkEndNode`](NFENetwork.md) in class [`NFENetwork`](NFENetwork.md)

      Parameters:
      `linkId` - linkId the ID of a link contained in the network

      `endNodeId` - the ID of a node contained in the network

      Returns:
      true if the node was changed

    <!-- -->

    - #### addModelListener

          public void addModelListener(NFEModelListener listener)

      Description copied from class: [`NFENetwork`](NFENetwork.md)
      Subscribes a model listener instance to this class
      Specified by:
      [`addModelListener`](NFENetwork.md) in class [`NFENetwork`](NFENetwork.md)

      Parameters:
      `listener` - an NFEModelListener instance

    <!-- -->

    - #### removeModelListener

          public void removeModelListener(NFEModelListener listener)

      Description copied from class: [`NFENetwork`](NFENetwork.md)
      Removes the given model listener from this class
      Specified by:
      [`removeModelListener`](NFENetwork.md) in class [`NFENetwork`](NFENetwork.md)

      Parameters:
      `listener` - an NFEModelListener instance

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

- [Prev Class](NFEBasicLink.md)
- [Next Class](NFEBasicNode.md)

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
