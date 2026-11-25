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

- [Prev Class](NFEAnalysisIOService.md)
- [Next Class](NFEIOService.md)

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

oracle.spatial.network.nfe.io.service

## Interface NFEFeatureIOService

- All Superinterfaces:
  [NFEIOService](NFEIOService.md)

  <!-- -->

  All Known Implementing Classes:
  [JDBCFeatureIOService](../jdbc/service/JDBCFeatureIOService.md)

  ------------------------------------------------------------------------



      public interface NFEFeatureIOService
      extends NFEIOService

  The feature service provides methods to load and manage the model features.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                           | Method and Description                                                                                                                                                                                                                                                                                                                       |
    |-----------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`JGeometry`](../../../../geometry/JGeometry.md)                            | `calculatePersistedNetworkMBR``()`<br>Returns the minimum bounding rectangle of the model network.                                                                                                                                                                                                                                           |
    | `java.util.List<java.lang.Long>`                                            | `findFeaturesIds``(`[`NFESearchParams`](../../beans/NFESearchParams.md)` searchParams)`<br>Searches features based on the specified parameters.                                                                                                                                                                                              |
    | `java.util.List<`[`NFEFeature`](../../model/feature/NFEFeature.md)`>`       | `getChildFeatures``(`[`NFEFeature`](../../model/feature/NFEFeature.md)` nfeFeature)`<br>Returns the child features of the specified feature.                                                                                                                                                                                                 |
    | [`JGeometry`](../../../../geometry/JGeometry.md)                            | `getMBRForNodes``(java.lang.String geoColumn, java.lang.String table, java.util.List<java.lang.Long> nodeIds, java.lang.String workspace)`<br>Returns the minimum bounding rectangle of the specified nodes.                                                                                                                                 |
    | `java.util.List<java.lang.Long>`                                            | `getRelatedLinkIdsForFeature``(`[`NFEFeatureLayer`](../../model/feature/NFEFeatureLayer.md)` featureLayer, java.lang.Long featureId)`<br>Returns the links identifiers of the links related by the specified feature.                                                                                                                        |
    | `java.util.List<java.lang.Long>`                                            | `getRelatedNodeIdsForFeature``(`[`NFEFeatureLayer`](../../model/feature/NFEFeatureLayer.md)` featureLayer, java.lang.Long featureId)`<br>Returns the nodes identifiers of the nodes related by the specified feature.                                                                                                                        |
    | `java.util.List<java.lang.Long>`                                            | `getRelatedNodesIdsForLink``(java.lang.Long linkId)`<br>Returns the start and end nodes identifiers of the specified link.                                                                                                                                                                                                                   |
    | `void`                                                                      | `importNetworkElementsAsFeatures``(java.lang.String srcNetworkName, long linesFeatureLayerId, long linesFeatureClassId, long nodesFeatureLayerId, long nodesFeatureClassId)`<br>Imports all the links and nodes from the specified network to the current model in the database, translating them into line and point features respectively. |
    | [`NFEFeature`](../../model/feature/NFEFeature.md)                           | `loadFeature``(long featureLayerId, long featureId)`<br>Loads the feature, network elements, feature elements and rules instances related to the specified feature.                                                                                                                                                                          |
    | `void`                                                                      | `loadFeatureLayersContent``(java.awt.geom.Area queryArea, java.util.Collection<java.lang.Long> featLayerIds)`<br>Loads the network elements, feature elements, features and rules instances that interact spatially with the specified area.                                                                                                 |
    | `java.util.Collection<`[`NFEFeature`](../../model/feature/NFEFeature.md)`>` | `loadLinkFeatures``(long linkId)`<br>Loads into the Model the link and the features associated to the link.                                                                                                                                                                                                                                  |
    | `java.util.Collection<`[`NFEFeature`](../../model/feature/NFEFeature.md)`>` | `loadNodeFeatures``(long nodeId)`<br>Loads into the Model the node and the features associated to the node.                                                                                                                                                                                                                                  |
    | `void`                                                                      | `saveModelContent``()`<br>Saves the feature layers network elements, feature elements, features and rules instances that were created, modified or deleted.                                                                                                                                                                                  |
    | `void`                                                                      | `saveModelContent``(java.sql.Connection conn)`<br>Saves the feature layers network elements, feature elements, features and rules instances that were created, modified or deleted, the specified connection will NOT be closed, rollback or commited.                                                                                       |
    | `void`                                                                      | `updateAttributeForFeatures``(`[`NFEFeatureLayer`](../../model/feature/NFEFeatureLayer.md)` nfeFeatureLayer, java.lang.Long featureClassId, java.lang.String attributeName, java.lang.String newValue, java.lang.String oldValue)`<br>Updates the features attributes from the old value to the new value.                                   |

    - ### Methods inherited from interface oracle.spatial.network.nfe.io.service.[NFEIOService](NFEIOService.md)

      [`getDataSource`](NFEIOService.md)`, `[`getModel`](NFEIOService.md)`, `[`getServiceProvider`](NFEIOService.md)`, `[`setDataSource`](NFEIOService.md)`, `[`setModel`](NFEIOService.md)

<!-- -->

- - ### Method Detail

    - #### loadFeatureLayersContent

          void loadFeatureLayersContent(java.awt.geom.Area queryArea,
                                        java.util.Collection<java.lang.Long> featLayerIds)
                                 throws NFEIOException

      Loads the network elements, feature elements, features and rules instances that interact spatially with the specified area. Note that the deleted elements in the model will not be loaded.
      Parameters:
      `queryArea` - area to load the feature layers content

      `featLayerIds` - identifiers of the feature layers to load the content

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### saveModelContent

          void saveModelContent()
                         throws NFEIOException

      Saves the feature layers network elements, feature elements, features and rules instances that were created, modified or deleted.
      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### saveModelContent

          void saveModelContent(java.sql.Connection conn)
                         throws NFEIOException

      Saves the feature layers network elements, feature elements, features and rules instances that were created, modified or deleted, the specified connection will NOT be closed, rollback or commited. This saving function allow to perform more tasks and to commit and close the connection when needed.
      Parameters:
      `conn` - Connection

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### findFeaturesIds

          java.util.List<java.lang.Long> findFeaturesIds(NFESearchParams searchParams)
                                                  throws NFEIOException

      Searches features based on the specified parameters. In the object searchParams the featureLayerId is mandatory, the parameters featureClassId, featureId and conditionString are optional. The conditionString parameter will be added to the where clause of the search query on the feature table.
      Parameters:
      `searchParams` - search parameters

      Returns:
      identifiers of the resulting features

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getRelatedNodeIdsForFeature

          java.util.List<java.lang.Long> getRelatedNodeIdsForFeature(NFEFeatureLayer featureLayer,
                                                                     java.lang.Long featureId)
                                                              throws NFEIOException

      Returns the nodes identifiers of the nodes related by the specified feature.
      Parameters:
      `featureLayer` - feature layer

      `featureId` - feature id

      Returns:
      list of nodes identifiers

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getRelatedLinkIdsForFeature

          java.util.List<java.lang.Long> getRelatedLinkIdsForFeature(NFEFeatureLayer featureLayer,
                                                                     java.lang.Long featureId)
                                                              throws NFEIOException

      Returns the links identifiers of the links related by the specified feature.
      Parameters:
      `featureLayer` - feature layer

      `featureId` - feature id

      Returns:
      list of links identifiers

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getChildFeatures

          java.util.List<NFEFeature> getChildFeatures(NFEFeature nfeFeature)
                                               throws NFEIOException

      Returns the child features of the specified feature. Note that the deleted features in the model will not be returned.
      Parameters:
      `nfeFeature` - feature parent

      Returns:
      child features

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getRelatedNodesIdsForLink

          java.util.List<java.lang.Long> getRelatedNodesIdsForLink(java.lang.Long linkId)
                                                            throws NFEIOException

      Returns the start and end nodes identifiers of the specified link.
      Parameters:
      `linkId` - link id

      Returns:
      start and end nodes identifiers

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getMBRForNodes

          JGeometry getMBRForNodes(java.lang.String geoColumn,
                                   java.lang.String table,
                                   java.util.List<java.lang.Long> nodeIds,
                                   java.lang.String workspace)
                            throws NFEIOException

      Returns the minimum bounding rectangle of the specified nodes.
      Parameters:
      `geoColumn` - geometry column name in nodes table

      `table` - nodes table

      `nodeIds` - nodes identifiers

      `workspace` - workspace that will be used by the connection, if null the current workspace will be used

      Returns:
      the minimum bounding rectangle of the specified nodes

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### updateAttributeForFeatures

          void updateAttributeForFeatures(NFEFeatureLayer nfeFeatureLayer,
                                          java.lang.Long featureClassId,
                                          java.lang.String attributeName,
                                          java.lang.String newValue,
                                          java.lang.String oldValue)
                                   throws NFEIOException

      Updates the features attributes from the old value to the new value. The features have to belong to the specified feature layer and feature class. Only the attributes having the current value as the old value will be updated. This method can be used for example to update all the affected attributes when a catalog value changes.
      Parameters:
      `nfeFeatureLayer` - feature layer

      `featureClassId` - feature class identifier

      `attributeName` - attribute name

      `newValue` - new value

      `oldValue` - old value

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### loadFeature

          NFEFeature loadFeature(long featureLayerId,
                                 long featureId)
                          throws NFEIOException

      Loads the feature, network elements, feature elements and rules instances related to the specified feature. Note that the deleted features in the model will not be loaded.
      Parameters:
      `featureLayerId` - feature layer identifier of the feature to load

      `featureId` - feature identifier

      Returns:
      feature

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### importNetworkElementsAsFeatures

          void importNetworkElementsAsFeatures(java.lang.String srcNetworkName,
                                               long linesFeatureLayerId,
                                               long linesFeatureClassId,
                                               long nodesFeatureLayerId,
                                               long nodesFeatureClassId)
                                        throws NFEIOException

      Imports all the links and nodes from the specified network to the current model in the database, translating them into line and point features respectively.
      Parameters:
      `srcNetworkName` - network name to be imported

      `linesFeatureLayerId` - translating line features' feature layer id

      `linesFeatureClassId` - translating line features' feature class id

      `nodesFeatureLayerId` - translating node features' feature layer id

      `nodesFeatureClassId` - translating node features' feature class id

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### calculatePersistedNetworkMBR

          JGeometry calculatePersistedNetworkMBR()
                                          throws NFEIOException

      Returns the minimum bounding rectangle of the model network.
      Returns:
      minimum bounding rectangle of the model network

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### loadNodeFeatures

          java.util.Collection<NFEFeature> loadNodeFeatures(long nodeId)
                                                     throws NFEIOException

      Loads into the Model the node and the features associated to the node.
      Parameters:
      `nodeId` - id of the node to be loaded along with its features

      Returns:
      A collection containing the features associated to the passed nodeId

      Throws:
      [`NFEIOException`](../NFEIOException.md)

    <!-- -->

    - #### loadLinkFeatures

          java.util.Collection<NFEFeature> loadLinkFeatures(long linkId)
                                                     throws NFEIOException

      Loads into the Model the link and the features associated to the link.
      Parameters:
      `linkId` - id of the link to be loaded along with its features

      Returns:
      A collection containing the features associated to the passed linkId

      Throws:
      [`NFEIOException`](../NFEIOException.md)

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

- [Prev Class](NFEAnalysisIOService.md)
- [Next Class](NFEIOService.md)

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
