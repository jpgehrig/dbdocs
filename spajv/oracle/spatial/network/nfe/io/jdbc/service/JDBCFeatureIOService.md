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

- [Prev Class](JDBCAnalysisIOService.md)
- [Next Class](JDBCIOServiceProvider.md)

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

oracle.spatial.network.nfe.io.jdbc.service

## Class JDBCFeatureIOService

- java.lang.Object

- - [oracle.spatial.network.nfe.io.jdbc.service.JDBCAbstractIOService](JDBCAbstractIOService.md)

  - - oracle.spatial.network.nfe.io.jdbc.service.JDBCFeatureIOService

<!-- -->

- All Implemented Interfaces:
  [NFEFeatureIOService](../../service/NFEFeatureIOService.md), [NFEIOService](../../service/NFEIOService.md)

  ------------------------------------------------------------------------



      public class JDBCFeatureIOService
      extends JDBCAbstractIOService
      implements NFEFeatureIOService

  Provides the default implementation for the feature service.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                  |
    |--------------------------------------------------------------------------------------------------------------|
    | `JDBCFeatureIOService``(`[`NFEIOServiceProvider`](../../service/NFEIOServiceProvider.md)` serviceProvider)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                              | Method and Description                                                                                                                                                                                                                                                                                                                       |
    |--------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`JGeometry`](../../../../../geometry/JGeometry.md)                            | `calculatePersistedNetworkMBR``()`<br>Returns the minimum bounding rectangle of the model network.                                                                                                                                                                                                                                           |
    | `java.util.List<java.lang.Long>`                                               | `findFeaturesIds``(`[`NFESearchParams`](../../../beans/NFESearchParams.md)` searchParams)`<br>Searches features based on the specified parameters.                                                                                                                                                                                           |
    | `java.util.List<`[`NFEFeature`](../../../model/feature/NFEFeature.md)`>`       | `getChildFeatures``(`[`NFEFeature`](../../../model/feature/NFEFeature.md)` nfeFeature)`<br>Returns the child features of the specified feature.                                                                                                                                                                                              |
    | [`JGeometry`](../../../../../geometry/JGeometry.md)                            | `getMBRForNodes``(java.lang.String geoColumn, java.lang.String table, java.util.List<java.lang.Long> nodeIds, java.lang.String workspace)`<br>Returns the minimum bounding rectangle of the specified nodes.                                                                                                                                 |
    | `java.util.List<java.lang.Long>`                                               | `getRelatedLinkIdsForFeature``(`[`NFEFeatureLayer`](../../../model/feature/NFEFeatureLayer.md)` featureLayer, java.lang.Long featureId)`<br>Returns the links identifiers of the links related by the specified feature.                                                                                                                     |
    | `java.util.List<java.lang.Long>`                                               | `getRelatedNodeIdsForFeature``(`[`NFEFeatureLayer`](../../../model/feature/NFEFeatureLayer.md)` featureLayer, java.lang.Long featureId)`<br>Returns the nodes identifiers of the nodes related by the specified feature.                                                                                                                     |
    | `java.util.List<java.lang.Long>`                                               | `getRelatedNodesIdsForLink``(java.lang.Long linkId)`<br>Returns the start and end nodes identifiers of the specified link.                                                                                                                                                                                                                   |
    | `void`                                                                         | `importNetworkElementsAsFeatures``(java.lang.String srcNetworkName, long linesFeatureLayerId, long linesFeatureClassId, long nodesFeatureLayerId, long nodesFeatureClassId)`<br>Imports all the links and nodes from the specified network to the current model in the database, translating them into line and point features respectively. |
    | [`NFEFeature`](../../../model/feature/NFEFeature.md)                           | `loadFeature``(long featureLayerId, long featureId)`<br>Loads the feature, network elements, feature elements and rules instances related to the specified feature.                                                                                                                                                                          |
    | `void`                                                                         | `loadFeatureLayersContent``(java.awt.geom.Area queryArea, java.util.Collection<java.lang.Long> featLayerIds)`<br>Loads the network elements, feature elements, features and rules instances that interact spatially with the specified area.                                                                                                 |
    | `java.util.Collection<`[`NFEFeature`](../../../model/feature/NFEFeature.md)`>` | `loadLinkFeatures``(long linkId)`<br>Loads into the Model the link and the features associated to the link.                                                                                                                                                                                                                                  |
    | `java.util.Collection<`[`NFEFeature`](../../../model/feature/NFEFeature.md)`>` | `loadNodeFeatures``(long nodeId)`<br>Loads into the Model the node and the features associated to the node.                                                                                                                                                                                                                                  |
    | `void`                                                                         | `saveModelContent``()`<br>Saves the feature layers network elements, feature elements, features and rules instances that were created, modified or deleted.                                                                                                                                                                                  |
    | `void`                                                                         | `saveModelContent``(java.sql.Connection conn)`<br>Saves the feature layers network elements, feature elements, features and rules instances that were created, modified or deleted, the specified connection will NOT be closed, rollback or commited.                                                                                       |
    | `void`                                                                         | `updateAttributeForFeatures``(`[`NFEFeatureLayer`](../../../model/feature/NFEFeatureLayer.md)` nfeFeatureLayer, java.lang.Long featureClassId, java.lang.String attributeName, java.lang.String newValue, java.lang.String oldValue)`<br>Updates the features attributes from the old value to the new value.                                |

    - ### Methods inherited from class oracle.spatial.network.nfe.io.jdbc.service.[JDBCAbstractIOService](JDBCAbstractIOService.md)

      [`getDataSource`](JDBCAbstractIOService.md)`, `[`getModel`](JDBCAbstractIOService.md)`, `[`getServiceProvider`](JDBCAbstractIOService.md)`, `[`setDataSource`](JDBCAbstractIOService.md)`, `[`setModel`](JDBCAbstractIOService.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.nfe.io.service.[NFEIOService](../../service/NFEIOService.md)

      [`getDataSource`](../../service/NFEIOService.md)`, `[`getModel`](../../service/NFEIOService.md)`, `[`getServiceProvider`](../../service/NFEIOService.md)`, `[`setDataSource`](../../service/NFEIOService.md)`, `[`setModel`](../../service/NFEIOService.md)

<!-- -->

- - ### Constructor Detail

    - #### JDBCFeatureIOService

          public JDBCFeatureIOService(NFEIOServiceProvider serviceProvider)

  <!-- -->

  - ### Method Detail

    - #### loadNodeFeatures

          public java.util.Collection<NFEFeature> loadNodeFeatures(long nodeId)
                                                            throws NFEIOException

      Description copied from interface: [`NFEFeatureIOService`](../../service/NFEFeatureIOService.md)
      Loads into the Model the node and the features associated to the node.
      Specified by:
      [`loadNodeFeatures`](../../service/NFEFeatureIOService.md) in interface [`NFEFeatureIOService`](../../service/NFEFeatureIOService.md)

      Parameters:
      `nodeId` - id of the node to be loaded along with its features

      Returns:
      A collection containing the features associated to the passed nodeId

      Throws:
      [`NFEIOException`](../../NFEIOException.md)

    <!-- -->

    - #### loadLinkFeatures

          public java.util.Collection<NFEFeature> loadLinkFeatures(long linkId)
                                                            throws NFEIOException

      Description copied from interface: [`NFEFeatureIOService`](../../service/NFEFeatureIOService.md)
      Loads into the Model the link and the features associated to the link.
      Specified by:
      [`loadLinkFeatures`](../../service/NFEFeatureIOService.md) in interface [`NFEFeatureIOService`](../../service/NFEFeatureIOService.md)

      Parameters:
      `linkId` - id of the link to be loaded along with its features

      Returns:
      A collection containing the features associated to the passed linkId

      Throws:
      [`NFEIOException`](../../NFEIOException.md)

    <!-- -->

    - #### loadFeature

          public NFEFeature loadFeature(long featureLayerId,
                                        long featureId)
                                 throws NFEIOException

      Description copied from interface: [`NFEFeatureIOService`](../../service/NFEFeatureIOService.md)
      Loads the feature, network elements, feature elements and rules instances related to the specified feature. Note that the deleted features in the model will not be loaded.
      Specified by:
      [`loadFeature`](../../service/NFEFeatureIOService.md) in interface [`NFEFeatureIOService`](../../service/NFEFeatureIOService.md)

      Parameters:
      `featureLayerId` - feature layer identifier of the feature to load

      `featureId` - feature identifier

      Returns:
      feature

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### loadFeatureLayersContent

          public void loadFeatureLayersContent(java.awt.geom.Area queryArea,
                                               java.util.Collection<java.lang.Long> featLayerIds)
                                        throws NFEIOException

      Description copied from interface: [`NFEFeatureIOService`](../../service/NFEFeatureIOService.md)
      Loads the network elements, feature elements, features and rules instances that interact spatially with the specified area. Note that the deleted elements in the model will not be loaded.
      Specified by:
      [`loadFeatureLayersContent`](../../service/NFEFeatureIOService.md) in interface [`NFEFeatureIOService`](../../service/NFEFeatureIOService.md)

      Parameters:
      `queryArea` - area to load the feature layers content

      `featLayerIds` - identifiers of the feature layers to load the content

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### saveModelContent

          public void saveModelContent()
                                throws NFEIOException

      Description copied from interface: [`NFEFeatureIOService`](../../service/NFEFeatureIOService.md)
      Saves the feature layers network elements, feature elements, features and rules instances that were created, modified or deleted.
      Specified by:
      [`saveModelContent`](../../service/NFEFeatureIOService.md) in interface [`NFEFeatureIOService`](../../service/NFEFeatureIOService.md)

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### saveModelContent

          public void saveModelContent(java.sql.Connection conn)
                                throws NFEIOException

      Description copied from interface: [`NFEFeatureIOService`](../../service/NFEFeatureIOService.md)
      Saves the feature layers network elements, feature elements, features and rules instances that were created, modified or deleted, the specified connection will NOT be closed, rollback or commited. This saving function allow to perform more tasks and to commit and close the connection when needed.
      Specified by:
      [`saveModelContent`](../../service/NFEFeatureIOService.md) in interface [`NFEFeatureIOService`](../../service/NFEFeatureIOService.md)

      Parameters:
      `conn` - Connection

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### calculatePersistedNetworkMBR

          public JGeometry calculatePersistedNetworkMBR()
                                                 throws NFEIOException

      Description copied from interface: [`NFEFeatureIOService`](../../service/NFEFeatureIOService.md)
      Returns the minimum bounding rectangle of the model network.
      Specified by:
      [`calculatePersistedNetworkMBR`](../../service/NFEFeatureIOService.md) in interface [`NFEFeatureIOService`](../../service/NFEFeatureIOService.md)

      Returns:
      minimum bounding rectangle of the model network

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### findFeaturesIds

          public java.util.List<java.lang.Long> findFeaturesIds(NFESearchParams searchParams)
                                                         throws NFEIOException

      Description copied from interface: [`NFEFeatureIOService`](../../service/NFEFeatureIOService.md)
      Searches features based on the specified parameters. In the object searchParams the featureLayerId is mandatory, the parameters featureClassId, featureId and conditionString are optional. The conditionString parameter will be added to the where clause of the search query on the feature table.
      Specified by:
      [`findFeaturesIds`](../../service/NFEFeatureIOService.md) in interface [`NFEFeatureIOService`](../../service/NFEFeatureIOService.md)

      Parameters:
      `searchParams` - search parameters

      Returns:
      identifiers of the resulting features

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getRelatedNodeIdsForFeature

          public java.util.List<java.lang.Long> getRelatedNodeIdsForFeature(NFEFeatureLayer featureLayer,
                                                                            java.lang.Long featureId)
                                                                     throws NFEIOException

      Description copied from interface: [`NFEFeatureIOService`](../../service/NFEFeatureIOService.md)
      Returns the nodes identifiers of the nodes related by the specified feature.
      Specified by:
      [`getRelatedNodeIdsForFeature`](../../service/NFEFeatureIOService.md) in interface [`NFEFeatureIOService`](../../service/NFEFeatureIOService.md)

      Parameters:
      `featureLayer` - feature layer

      `featureId` - feature id

      Returns:
      list of nodes identifiers

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getRelatedLinkIdsForFeature

          public java.util.List<java.lang.Long> getRelatedLinkIdsForFeature(NFEFeatureLayer featureLayer,
                                                                            java.lang.Long featureId)
                                                                     throws NFEIOException

      Description copied from interface: [`NFEFeatureIOService`](../../service/NFEFeatureIOService.md)
      Returns the links identifiers of the links related by the specified feature.
      Specified by:
      [`getRelatedLinkIdsForFeature`](../../service/NFEFeatureIOService.md) in interface [`NFEFeatureIOService`](../../service/NFEFeatureIOService.md)

      Parameters:
      `featureLayer` - feature layer

      `featureId` - feature id

      Returns:
      list of links identifiers

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getChildFeatures

          public java.util.List<NFEFeature> getChildFeatures(NFEFeature nfeFeature)
                                                      throws NFEIOException

      Description copied from interface: [`NFEFeatureIOService`](../../service/NFEFeatureIOService.md)
      Returns the child features of the specified feature. Note that the deleted features in the model will not be returned.
      Specified by:
      [`getChildFeatures`](../../service/NFEFeatureIOService.md) in interface [`NFEFeatureIOService`](../../service/NFEFeatureIOService.md)

      Parameters:
      `nfeFeature` - feature parent

      Returns:
      child features

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getRelatedNodesIdsForLink

          public java.util.List<java.lang.Long> getRelatedNodesIdsForLink(java.lang.Long linkId)
                                                                   throws NFEIOException

      Description copied from interface: [`NFEFeatureIOService`](../../service/NFEFeatureIOService.md)
      Returns the start and end nodes identifiers of the specified link.
      Specified by:
      [`getRelatedNodesIdsForLink`](../../service/NFEFeatureIOService.md) in interface [`NFEFeatureIOService`](../../service/NFEFeatureIOService.md)

      Parameters:
      `linkId` - link id

      Returns:
      start and end nodes identifiers

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getMBRForNodes

          public JGeometry getMBRForNodes(java.lang.String geoColumn,
                                          java.lang.String table,
                                          java.util.List<java.lang.Long> nodeIds,
                                          java.lang.String workspace)
                                   throws NFEIOException

      Description copied from interface: [`NFEFeatureIOService`](../../service/NFEFeatureIOService.md)
      Returns the minimum bounding rectangle of the specified nodes.
      Specified by:
      [`getMBRForNodes`](../../service/NFEFeatureIOService.md) in interface [`NFEFeatureIOService`](../../service/NFEFeatureIOService.md)

      Parameters:
      `geoColumn` - geometry column name in nodes table

      `table` - nodes table

      `nodeIds` - nodes identifiers

      `workspace` - workspace that will be used by the connection, if null the current workspace will be used

      Returns:
      the minimum bounding rectangle of the specified nodes

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### updateAttributeForFeatures

          public void updateAttributeForFeatures(NFEFeatureLayer nfeFeatureLayer,
                                                 java.lang.Long featureClassId,
                                                 java.lang.String attributeName,
                                                 java.lang.String newValue,
                                                 java.lang.String oldValue)
                                          throws NFEIOException

      Description copied from interface: [`NFEFeatureIOService`](../../service/NFEFeatureIOService.md)
      Updates the features attributes from the old value to the new value. The features have to belong to the specified feature layer and feature class. Only the attributes having the current value as the old value will be updated. This method can be used for example to update all the affected attributes when a catalog value changes.
      Specified by:
      [`updateAttributeForFeatures`](../../service/NFEFeatureIOService.md) in interface [`NFEFeatureIOService`](../../service/NFEFeatureIOService.md)

      Parameters:
      `nfeFeatureLayer` - feature layer

      `featureClassId` - feature class identifier

      `attributeName` - attribute name

      `newValue` - new value

      `oldValue` - old value

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### importNetworkElementsAsFeatures

          public void importNetworkElementsAsFeatures(java.lang.String srcNetworkName,
                                                      long linesFeatureLayerId,
                                                      long linesFeatureClassId,
                                                      long nodesFeatureLayerId,
                                                      long nodesFeatureClassId)
                                               throws NFEIOException

      Description copied from interface: [`NFEFeatureIOService`](../../service/NFEFeatureIOService.md)
      Imports all the links and nodes from the specified network to the current model in the database, translating them into line and point features respectively.
      Specified by:
      [`importNetworkElementsAsFeatures`](../../service/NFEFeatureIOService.md) in interface [`NFEFeatureIOService`](../../service/NFEFeatureIOService.md)

      Parameters:
      `srcNetworkName` - network name to be imported

      `linesFeatureLayerId` - translating line features' feature layer id

      `linesFeatureClassId` - translating line features' feature class id

      `nodesFeatureLayerId` - translating node features' feature layer id

      `nodesFeatureClassId` - translating node features' feature class id

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

- [Prev Class](JDBCAnalysisIOService.md)
- [Next Class](JDBCIOServiceProvider.md)

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
