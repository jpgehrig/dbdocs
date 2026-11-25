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

- [Prev Class](NFELink.md)
- [Next Class](NFENetworkElement.md)

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

## Class NFENetwork

- java.lang.Object

- - oracle.spatial.network.nfe.model.network.NFENetwork

<!-- -->

- Direct Known Subclasses:
  [NFEBasicNetwork](NFEBasicNetwork.md)

  ------------------------------------------------------------------------



      public abstract class NFENetwork
      extends java.lang.Object

  Memory representation of an SDO network. Use NFEModelObjectFactory.createNetwork() to get an instance of this class. An instance of this class is usually created and populated automatically when an NFEModel is created.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `NFENetwork``()`            |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                              | Method and Description                                                                                                                                                                                                    |
    |----------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `abstract boolean`                                                                                             | `addLink``(`[`NFELink`](NFELink.md)` link)`<br>Adds an existing link to the network.                                                                                                                                      |
    | `abstract boolean`                                                                                             | `addLink``(`[`NFELink`](NFELink.md)` link, long startNodeId, long endNodeId)`<br>Adds an existing link to the network and sets the link's start and end nodes.                                                            |
    | `abstract void`                                                                                                | `addLinks``(java.util.Collection<`[`NFELink`](NFELink.md)`> links)`<br>Adds all the links contained in the given collection.                                                                                              |
    | `abstract void`                                                                                                | `addModelListener``(`[`NFEModelListener`](../event/NFEModelListener.md)` listener)`<br>Subscribes a model listener instance to this class                                                                                 |
    | `abstract boolean`                                                                                             | `addNode``(`[`NFENode`](NFENode.md)` node)`<br>Adds an existing node to the network.                                                                                                                                      |
    | `abstract void`                                                                                                | `addNodes``(java.util.Collection<`[`NFENode`](NFENode.md)`> nodes)`<br>Adds a collection of nodes to the network                                                                                                          |
    | `abstract boolean`                                                                                             | `changeLinkEndNode``(long linkId, long endNodeId)`<br>Changes the end node of the link identified by linkId to the node identified by endNodeId                                                                           |
    | `abstract boolean`                                                                                             | `changeLinkStartNode``(long linkId, long startNodeId)`<br>Changes the start node of the link identified by linkId to the node identified by startNodeId                                                                   |
    | `abstract boolean`                                                                                             | `contains``(`[`NFENetworkElement`](NFENetworkElement.md)` networkElement)`<br>Tells whether the network contains the given networkElement or not                                                                          |
    | [`NFEEventDispatcher`](../event/NFEEventDispatcher.md)`<`[`NFEModelListener`](../event/NFEModelListener.md)`>` | `getEventDispatcher``()`<br>Gets the event dispatcher currently used.                                                                                                                                                     |
    | `long`                                                                                                         | `getId``()`<br>Gets the ID of the network                                                                                                                                                                                 |
    | `abstract `[`NFELink`](NFELink.md)                                                                             | `getLink``(long linkId)`<br>Gets the link identified by the given ID.                                                                                                                                                     |
    | `abstract java.util.Collection<`[`NFELink`](NFELink.md)`>`                                                     | `getLinks``()`<br>Gets all the links contained in the network                                                                                                                                                             |
    | [`NFENetworkMetadata`](NFENetworkMetadata.md)                                                                  | `getMetadata``()`<br>Gets the network's metadata                                                                                                                                                                          |
    | `java.lang.String`                                                                                             | `getName``()`<br>Gets the name of the network                                                                                                                                                                             |
    | `abstract `[`NFENode`](NFENode.md)                                                                             | `getNode``(long nodeId)`<br>Gets the node identified by the given ID.                                                                                                                                                     |
    | `abstract java.util.Collection<`[`NFENode`](NFENode.md)`>`                                                     | `getNodes``()`<br>Gets all the nodes contained in the network                                                                                                                                                             |
    | `abstract `[`NFELink`](NFELink.md)                                                                             | `removeLink``(long linkId)`<br>Removes a link identified by the given ID from the network                                                                                                                                 |
    | `abstract void`                                                                                                | `removeModelListener``(`[`NFEModelListener`](../event/NFEModelListener.md)` listener)`<br>Removes the given model listener from this class                                                                                |
    | `abstract `[`NFENode`](NFENode.md)                                                                             | `removeNode``(long nodeId)`<br>Removes a node identified by the given ID from the network                                                                                                                                 |
    | `void`                                                                                                         | `setEventDispatcher``(`[`NFEEventDispatcher`](../event/NFEEventDispatcher.md)`<`[`NFEModelListener`](../event/NFEModelListener.md)`> eventDispatcher)`<br>Sets the event dispatcher that will be used to fire new events. |
    | `void`                                                                                                         | `setId``(long id)`<br>Sets the ID for the network                                                                                                                                                                         |
    | `void`                                                                                                         | `setMetadata``(`[`NFENetworkMetadata`](NFENetworkMetadata.md)` networkMetadata)`<br>Sets the metadata of the network                                                                                                      |
    | `void`                                                                                                         | `setName``(java.lang.String name)`<br>Sets the name of the network                                                                                                                                                        |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFENetwork

          public NFENetwork()

  <!-- -->

  - ### Method Detail

    - #### setId

          public void setId(long id)

      Sets the ID for the network
      Parameters:
      `id` - a network ID

    <!-- -->

    - #### getId

          public long getId()

      Gets the ID of the network
      Returns:
      a network ID

    <!-- -->

    - #### setName

          public void setName(java.lang.String name)

      Sets the name of the network
      Parameters:
      `name` - the network's name

    <!-- -->

    - #### getName

          public java.lang.String getName()

      Gets the name of the network
      Returns:
      the network's name

    <!-- -->

    - #### setMetadata

          public void setMetadata(NFENetworkMetadata networkMetadata)

      Sets the metadata of the network
      Parameters:
      `networkMetadata` - an instance of NFENetworkMetadata

    <!-- -->

    - #### getMetadata

          public NFENetworkMetadata getMetadata()

      Gets the network's metadata
      Returns:
      an instance of NFENetworkMetadata

    <!-- -->

    - #### setEventDispatcher

          public void setEventDispatcher(NFEEventDispatcher<NFEModelListener> eventDispatcher)

      Sets the event dispatcher that will be used to fire new events. If it is set to null, no events will be fired.
      Parameters:
      `eventDispatcher` - an NFEEventDispatcher instance.

    <!-- -->

    - #### getEventDispatcher

          public NFEEventDispatcher<NFEModelListener> getEventDispatcher()

      Gets the event dispatcher currently used.
      Returns:
      an NFEEventDispatcher instance.

    <!-- -->

    - #### getNodes

          public abstract java.util.Collection<NFENode> getNodes()

      Gets all the nodes contained in the network
      Returns:
      a collection of NFENode instances

    <!-- -->

    - #### getLinks

          public abstract java.util.Collection<NFELink> getLinks()

      Gets all the links contained in the network
      Returns:
      a collection of NFELink instances

    <!-- -->

    - #### getNode

          public abstract NFENode getNode(long nodeId)

      Gets the node identified by the given ID.
      Parameters:
      `nodeId` - a node ID

      Returns:
      an NFENode instance or null if it was not found

    <!-- -->

    - #### getLink

          public abstract NFELink getLink(long linkId)

      Gets the link identified by the given ID.
      Parameters:
      `linkId` - a link ID

      Returns:
      an NFELink instance or null if it was not found

    <!-- -->

    - #### removeNode

          public abstract NFENode removeNode(long nodeId)

      Removes a node identified by the given ID from the network
      Parameters:
      `nodeId` - a node ID

      Returns:
      the removed NFENode instance or null if it was not found or could not be removed

    <!-- -->

    - #### removeLink

          public abstract NFELink removeLink(long linkId)

      Removes a link identified by the given ID from the network
      Parameters:
      `linkId` - a link ID

      Returns:
      the removed NFELink instance or null if it was not found or could not be removed

    <!-- -->

    - #### contains

          public abstract boolean contains(NFENetworkElement networkElement)

      Tells whether the network contains the given networkElement or not
      Parameters:
      `networkElement` - a network element instance (a node or a link)

      Returns:
      true if the network contains the element

    <!-- -->

    - #### addNode

          public abstract boolean addNode(NFENode node)

      Adds an existing node to the network.
      Parameters:
      `node` - an NFENode instance

      Returns:
      true if the node was added

    <!-- -->

    - #### addNodes

          public abstract void addNodes(java.util.Collection<NFENode> nodes)

      Adds a collection of nodes to the network
      Parameters:
      `nodes` - a collection of nodes

    <!-- -->

    - #### addLink

          public abstract boolean addLink(NFELink link)

      Adds an existing link to the network. The link's start and end nodes must be contained in the network.
      Parameters:
      `link` - an NFELink instance.

      Returns:
      true if the link was added

    <!-- -->

    - #### addLink

          public abstract boolean addLink(NFELink link,
                                          long startNodeId,
                                          long endNodeId)

      Adds an existing link to the network and sets the link's start and end nodes.
      Parameters:
      `link` - an NFELink instance

      `startNodeId` - the ID of a node contained in the network

      `endNodeId` - the ID of a node contained in the network

      Returns:
      true if the link was added

    <!-- -->

    - #### addLinks

          public abstract void addLinks(java.util.Collection<NFELink> links)

      Adds all the links contained in the given collection. All the links must have a start and end node already contained in the network.
      Parameters:
      `links` - a collection of links

    <!-- -->

    - #### changeLinkStartNode

          public abstract boolean changeLinkStartNode(long linkId,
                                                      long startNodeId)

      Changes the start node of the link identified by linkId to the node identified by startNodeId
      Parameters:
      `linkId` - the ID of a link contained in the network

      `startNodeId` - the ID of a node contained in the network

      Returns:
      true if the node was changed

    <!-- -->

    - #### changeLinkEndNode

          public abstract boolean changeLinkEndNode(long linkId,
                                                    long endNodeId)

      Changes the end node of the link identified by linkId to the node identified by endNodeId
      Parameters:
      `linkId` - linkId the ID of a link contained in the network

      `endNodeId` - the ID of a node contained in the network

      Returns:
      true if the node was changed

    <!-- -->

    - #### addModelListener

          public abstract void addModelListener(NFEModelListener listener)

      Subscribes a model listener instance to this class
      Parameters:
      `listener` - an NFEModelListener instance

    <!-- -->

    - #### removeModelListener

          public abstract void removeModelListener(NFEModelListener listener)

      Removes the given model listener from this class
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

- [Prev Class](NFELink.md)
- [Next Class](NFENetworkElement.md)

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
