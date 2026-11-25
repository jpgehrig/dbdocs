Skip navigation links

- [Overview](../../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../../deprecated-list.md)
- [Index](../../../../../../../index-all.md)
- [Help](../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](ModelDAO.ModelFeatLayerRelation.md)
- [Next Class](RuleDAO.md)

<!-- -->

- [Frames](../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.io.jdbc.dao

## Class NetworkDAO

- java.lang.Object

- - [oracle.spatial.network.nfe.io.jdbc.dao.AbstractDAO](AbstractDAO.md)

  - - oracle.spatial.network.nfe.io.jdbc.dao.NetworkDAO

<!-- -->

-

  ------------------------------------------------------------------------



      public class NetworkDAO
      extends AbstractDAO

  The NetworkDAO data access object provides methods to load, create and manage the network elements. The node table name is \_NODE\$ and the link table name is \_LINK\$. It is not recommended to use the data access objects methods, instead use the NFE services.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                 |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `NetworkDAO``(java.sql.Connection conn, `[`NFEModel`](../../../model/NFEModel.md)` model)`<br>Creates a NetworkDAO with the specified connection and model. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                            | Method and Description                                                                                                                                                                                                                                                                                                       |
    |----------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                                       | `createNetwork``(long modelId, java.lang.String networkName, java.lang.Integer hierarchyLevels, boolean directed, boolean nodeWithCost)`<br>Creates the network and the related sequences.                                                                                                                                   |
    | `void`                                                                                       | `deleteDanglingLinks``(`[`NFENetworkMetadata`](../../../model/network/NFENetworkMetadata.md)` nfeNetworkMetadata)`<br>Deletes the links that are not referenced by any feature in any feature layer.                                                                                                                         |
    | `void`                                                                                       | `deleteDanglingNodes``(`[`NFENetworkMetadata`](../../../model/network/NFENetworkMetadata.md)` nfeNetworkMetadata)`<br>Deletes the nodes that are not referenced by any feature in any feature layer.                                                                                                                         |
    | `void`                                                                                       | `deleteLinks``(java.util.Collection<`[`NFELink`](../../../model/network/NFELink.md)`> delLinks)`<br>Deletes the specified links.                                                                                                                                                                                             |
    | `void`                                                                                       | `deleteNetwork``(java.lang.String networkName)`<br>Drops the NFE Network (an SDO Network associated with a NFE project) along with its tables and sequences, and the relations with the NFE project.                                                                                                                         |
    | `void`                                                                                       | `deleteNodes``(java.util.Collection<`[`NFENode`](../../../model/network/NFENode.md)`> delNodes)`<br>Deletes the specified nodes and all the dependent network elements.                                                                                                                                                      |
    | [`NFELink`](../../../model/network/NFELink.md)                                               | `fetchLink``(`[`NFENetwork`](../../../model/network/NFENetwork.md)` network, java.lang.Long linkId)`<br>Returns the link object related to the specified link identifier.                                                                                                                                                    |
    | [`NFENetworkMetadata`](../../../model/network/NFENetworkMetadata.md)                         | `fetchNetworkMetadata``(java.lang.String networkName)`<br>Returns the network metadata from the view user_sdo_network_metadata.                                                                                                                                                                                              |
    | [`NFENode`](../../../model/network/NFENode.md)                                               | `fetchNode``(`[`NFENetwork`](../../../model/network/NFENetwork.md)` network, java.lang.Long nodeId)`<br>Returns the node object related to the specified node identifier.                                                                                                                                                    |
    | `java.util.List<`[`NFELink`](../../../model/network/NFELink.md)`>`                           | `getLinkInformation``(`[`NFEModel`](../../../model/NFEModel.md)` nfeModel, java.util.List<java.lang.Long> linkIds)`<br>Returns the links objects for the specified links identifiers list.                                                                                                                                   |
    | `java.util.List<java.lang.Long>`                                                             | `getLinksIdsByNodeId``(long nodeId, `[`NFENetworkMetadata`](../../../model/network/NFENetworkMetadata.md)` nfeNetworkMetadata)`<br>Returns the links identifiers from the links having as start node or end node the specified node.                                                                                         |
    | [`JGeometry`](../../../../../geometry/JGeometry.md)                                          | `getMBRForNodes``(java.lang.String geoColumn, java.lang.String table, java.util.List<java.lang.Long> nodeIds)`<br>Returns the minimum bounding rectangle of the specified nodes.                                                                                                                                             |
    | `java.util.List<`[`NFENode`](../../../model/network/NFENode.md)`>`                           | `getNodeInformation``(`[`NFEModel`](../../../model/NFEModel.md)` nfeModel, java.util.List<java.lang.Long> nodeIds)`<br>Returns the NFE node objects related to the specified nodes identifiers.                                                                                                                              |
    | `java.util.List<java.lang.Long>`                                                             | `getRelatedNodesIdsForLink``(java.lang.Long linkId, `[`NFENetworkMetadata`](../../../model/network/NFENetworkMetadata.md)` nfeNetworkMetadata)`<br>Returns start and end nodes identifiers of the link.                                                                                                                      |
    | `void`                                                                                       | `importNetwork``(java.lang.String srcNetworkName, long linesFeatureLayerId, long linesFeatureClassId, long pointsFeatureLayerId, long pointsFeatureClassId)`<br>Imports all the links and nodes from the specified network to the current model in the database, translating them into line and point features respectively. |
    | `java.util.Collection<`[`NFENetworkElement`](../../../model/network/NFENetworkElement.md)`>` | `loadNetworkElements``(java.util.Collection<`[`JGeometry`](../../../../../geometry/JGeometry.md)`> mbrs)`<br>Returns the network elements that interact spatially with the specified minimum bounding rectangle (MBR).                                                                                                       |
    | `boolean`                                                                                    | `networkExistsTest``(java.lang.String networkName)`<br>Returns true if the specified network exists, false otherwise.                                                                                                                                                                                                        |
    | `void`                                                                                       | `saveLinks``(java.util.Collection<`[`NFELink`](../../../model/network/NFELink.md)`> newLinks)`<br>Persists the new links in the link table.                                                                                                                                                                                  |
    | `void`                                                                                       | `saveNodes``(java.util.Collection<`[`NFENode`](../../../model/network/NFENode.md)`> newNodes)`<br>Persists the new nodes in the node table.                                                                                                                                                                                  |
    | `void`                                                                                       | `updateLinkCostAsLenght``(`[`NFENetworkMetadata`](../../../model/network/NFENetworkMetadata.md)` netMetadata, java.util.List<java.lang.Long> linksIds)`<br>Updates the link cost of the specified links to be equals to the links lengths.                                                                                   |
    | `void`                                                                                       | `updateLinks``(java.util.Collection<`[`NFELink`](../../../model/network/NFELink.md)`> updLinks)`<br>Updates the links information in the link table.                                                                                                                                                                         |
    | `void`                                                                                       | `updateLinksGeometry``(`[`NFENetworkMetadata`](../../../model/network/NFENetworkMetadata.md)` networkMetadata, java.util.List<java.lang.Long> linksIds)`<br>Updates the geometry of the specified links.                                                                                                                     |
    | `void`                                                                                       | `updateNodes``(java.util.Collection<`[`NFENode`](../../../model/network/NFENode.md)`> updNodes)`<br>Updates the nodes information in the node table.                                                                                                                                                                         |

    - ### Methods inherited from class oracle.spatial.network.nfe.io.jdbc.dao.[AbstractDAO](AbstractDAO.md)

      [`getConnection`](AbstractDAO.md)`, `[`getModel`](AbstractDAO.md)`, `[`getSQLValidator`](AbstractDAO.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NetworkDAO

          public NetworkDAO(java.sql.Connection conn,
                            NFEModel model)

      Creates a NetworkDAO with the specified connection and model.
      Parameters:
      `conn` - connection

      `model` - model

  <!-- -->

  - ### Method Detail

    - #### loadNetworkElements

          public java.util.Collection<NFENetworkElement> loadNetworkElements(java.util.Collection<JGeometry> mbrs)
                                                                      throws NFEIOException

      Returns the network elements that interact spatially with the specified minimum bounding rectangle (MBR). Note that the deleted elements in the model will not be loaded.
      Parameters:
      `mbrs` - minimum bounding rectangle geometries

      Returns:
      the network elements that interact spatially with the specified minimum bounding rectangle

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### saveNodes

          public void saveNodes(java.util.Collection<NFENode> newNodes)
                         throws NFEIOException

      Persists the new nodes in the node table.
      Parameters:
      `newNodes` - nodes to persist

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### saveLinks

          public void saveLinks(java.util.Collection<NFELink> newLinks)
                         throws NFEIOException

      Persists the new links in the link table. The link length will be saved in the cost column.
      Parameters:
      `newLinks` - links to persist

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### updateNodes

          public void updateNodes(java.util.Collection<NFENode> updNodes)
                           throws NFEIOException

      Updates the nodes information in the node table.
      Parameters:
      `updNodes` - nodes to update

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### updateLinks

          public void updateLinks(java.util.Collection<NFELink> updLinks)
                           throws NFEIOException

      Updates the links information in the link table.
      Parameters:
      `updLinks` - links to update

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteNodes

          public void deleteNodes(java.util.Collection<NFENode> delNodes)
                           throws NFEIOException

      Deletes the specified nodes and all the dependent network elements. For example, if the specified node is included in any link definitions, those links are deleted.
      Parameters:
      `delNodes` - nodes to delete

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteLinks

          public void deleteLinks(java.util.Collection<NFELink> delLinks)
                           throws NFEIOException

      Deletes the specified links.
      Parameters:
      `delLinks` - links to delete

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### fetchNode

          public NFENode fetchNode(NFENetwork network,
                                   java.lang.Long nodeId)
                            throws NFEIOException

      Returns the node object related to the specified node identifier. The node will be added to the NFE network.
      Parameters:
      `network` - network that contains the node

      `nodeId` - node identifier

      Returns:
      node object related to the specified node identifier

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### fetchLink

          public NFELink fetchLink(NFENetwork network,
                                   java.lang.Long linkId)
                            throws NFEIOException

      Returns the link object related to the specified link identifier. The link and the related nodes will be added to the NFE network.
      Parameters:
      `network` - network

      `linkId` - link identifier

      Returns:
      link object related to the specified link identifier

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### networkExistsTest

          public boolean networkExistsTest(java.lang.String networkName)
                                    throws NFEIOException

      Returns true if the specified network exists, false otherwise.
      Parameters:
      `networkName` - network name

      Returns:
      true if the specified network exists, false otherwise

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### createNetwork

          public void createNetwork(long modelId,
                                    java.lang.String networkName,
                                    java.lang.Integer hierarchyLevels,
                                    boolean directed,
                                    boolean nodeWithCost)
                             throws NFEIOException

      Creates the network and the related sequences. Update the column NETWORK_NAME from the table USER_SDO_NFE_MODEL_METADATA with the specified network name.
      Parameters:
      `modelId` - model identifier

      `networkName` - network name

      `hierarchyLevels` - Number of hierarchy levels for the links in the network. For an explanation of network hierarchy, see Section 5.5 of the NDM Developer Guide.

      `directed` - true indicates that the links are directed; false indicates that the links are undirected (not directed)

      `nodeWithCost` - true causes a column named COST to be included in the \_NODE\$ table; false causes a column named COST not to be included in the \_NODE\$ table

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### fetchNetworkMetadata

          public NFENetworkMetadata fetchNetworkMetadata(java.lang.String networkName)
                                                  throws NFEIOException

      Returns the network metadata from the view user_sdo_network_metadata.
      Parameters:
      `networkName` - network name

      Returns:
      the network metadata from the view user_sdo_network_metadata

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### importNetwork

          public void importNetwork(java.lang.String srcNetworkName,
                                    long linesFeatureLayerId,
                                    long linesFeatureClassId,
                                    long pointsFeatureLayerId,
                                    long pointsFeatureClassId)
                             throws NFEIOException

      Imports all the links and nodes from the specified network to the current model in the database, translating them into line and point features respectively.
      Parameters:
      `srcNetworkName` - network name to be imported

      `linesFeatureLayerId` - translating line features' feature layer id

      `linesFeatureClassId` - translating line features' feature class id

      `pointsFeatureLayerId` - translating node features' feature layer id

      `pointsFeatureClassId` - translating node features' feature class id

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getRelatedNodesIdsForLink

          public java.util.List<java.lang.Long> getRelatedNodesIdsForLink(java.lang.Long linkId,
                                                                          NFENetworkMetadata nfeNetworkMetadata)
                                                                   throws NFEIOException

      Returns start and end nodes identifiers of the link. If the link doesn't exist or doesn't have related nodes an empty list is returned.
      Parameters:
      `linkId` - link identifier

      `nfeNetworkMetadata` - network metadata

      Returns:
      start and end nodes identifiers

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getLinksIdsByNodeId

          public java.util.List<java.lang.Long> getLinksIdsByNodeId(long nodeId,
                                                                    NFENetworkMetadata nfeNetworkMetadata)
                                                             throws NFEIOException

      Returns the links identifiers from the links having as start node or end node the specified node.
      Parameters:
      `nodeId` - node identifier

      `nfeNetworkMetadata` - network metadata

      Returns:
      the links identifiers from the links having as start node or end node the specified node

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getLinkInformation

          public java.util.List<NFELink> getLinkInformation(NFEModel nfeModel,
                                                            java.util.List<java.lang.Long> linkIds)
                                                     throws NFEIOException

      Returns the links objects for the specified links identifiers list.
      Parameters:
      `nfeModel` - model

      `linkIds` - links identifiers list

      Returns:
      the links objects for the specified links identifiers list

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteDanglingLinks

          public void deleteDanglingLinks(NFENetworkMetadata nfeNetworkMetadata)
                                   throws NFEIOException

      Deletes the links that are not referenced by any feature in any feature layer.
      Parameters:
      `nfeNetworkMetadata` - network metadata

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteDanglingNodes

          public void deleteDanglingNodes(NFENetworkMetadata nfeNetworkMetadata)
                                   throws NFEIOException

      Deletes the nodes that are not referenced by any feature in any feature layer.
      Parameters:
      `nfeNetworkMetadata` - network metadata

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### updateLinksGeometry

          public void updateLinksGeometry(NFENetworkMetadata networkMetadata,
                                          java.util.List<java.lang.Long> linksIds)
                                   throws NFEIOException

      Updates the geometry of the specified links. This geometry will be the result to match the start of the geometry of the link with the start node of the link and the end of the geometry of the link with the end node.
      Parameters:
      `networkMetadata` - network metadata

      `linksIds` - links identifiers

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### updateLinkCostAsLenght

          public void updateLinkCostAsLenght(NFENetworkMetadata netMetadata,
                                             java.util.List<java.lang.Long> linksIds)
                                      throws NFEIOException

      Updates the link cost of the specified links to be equals to the links lengths.
      Parameters:
      `netMetadata` - network metadata

      `linksIds` - links identifiers

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getMBRForNodes

          public JGeometry getMBRForNodes(java.lang.String geoColumn,
                                          java.lang.String table,
                                          java.util.List<java.lang.Long> nodeIds)
                                   throws NFEIOException

      Returns the minimum bounding rectangle of the specified nodes.
      Parameters:
      `geoColumn` - geometry column in node table

      `table` - node table

      `nodeIds` - nodes identifiers

      Returns:
      the minimum bounding rectangle of the specified nodes

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getNodeInformation

          public java.util.List<NFENode> getNodeInformation(NFEModel nfeModel,
                                                            java.util.List<java.lang.Long> nodeIds)
                                                     throws NFEIOException

      Returns the NFE node objects related to the specified nodes identifiers.
      Parameters:
      `nfeModel` - model

      `nodeIds` - nodes identifiers

      Returns:
      the NFE nodes objects related to the specified nodes identifiers

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteNetwork

          public void deleteNetwork(java.lang.String networkName)
                             throws NFEIOException

      Drops the NFE Network (an SDO Network associated with a NFE project) along with its tables and sequences, and the relations with the NFE project.
      Parameters:
      `networkName` - network name to be deleted.

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

Skip navigation links

- [Overview](../../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../../deprecated-list.md)
- [Index](../../../../../../../index-all.md)
- [Help](../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](ModelDAO.ModelFeatLayerRelation.md)
- [Next Class](RuleDAO.md)

<!-- -->

- [Frames](../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../allclasses-noframe.md)

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
