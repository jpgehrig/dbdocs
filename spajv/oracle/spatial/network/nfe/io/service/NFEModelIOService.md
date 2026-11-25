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

- [Prev Class](NFEIOServiceProvider.md)
- [Next Class](NFEWorkspaceIOService.md)

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

## Interface NFEModelIOService

- All Superinterfaces:
  [NFEIOService](NFEIOService.md)

  <!-- -->

  All Known Implementing Classes:
  [JDBCModelIOService](../jdbc/service/JDBCModelIOService.md)

  ------------------------------------------------------------------------



      public interface NFEModelIOService
      extends NFEIOService

  The model service provides methods to load, create and manage the model infrastructure.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                           | Method and Description                                                                                                                                                                                                                                                                                                                                       |
    |-----------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`NFEFeatureLayer`](../../model/feature/NFEFeatureLayer.md)                 | `createFeatureLayer``(java.lang.String featureLayerName, java.lang.String featureTable, java.lang.String relationTable, java.lang.String hierarchyTable, java.util.Collection<`[`NFEAttributeDescriptor`](../../model/feature/NFEAttributeDescriptor.md)`> attrDescriptors, int hierarchyLevel, int zOrder)`<br>Creates a feature layer.                     |
    | [`NFEModel`](../../model/NFEModel.md)                                       | `createFromScratchModel``(java.lang.String modelName, boolean directedNetwork, `[`NFEGeometryDescriptor`](../../model/NFEGeometryDescriptor.md)` geomDescriptor)`<br>Creates a model in from scratch mode.                                                                                                                                                   |
    | [`NFEModel`](../../model/NFEModel.md)                                       | `createOverExistingNetworkModel``(java.lang.String modelName, java.lang.String networkName)`<br>Creates a model in from existing network mode.                                                                                                                                                                                                               |
    | `void`                                                                      | `deleteCatalog``(long catalogId)`<br>Deletes the specified catalog.                                                                                                                                                                                                                                                                                          |
    | `void`                                                                      | `deleteFeatureClass``(`[`NFEFeatureClass`](../../model/feature/NFEFeatureClass.md)` featClass)`<br>Deletes the feature class.                                                                                                                                                                                                                                |
    | `void`                                                                      | `deleteFeatureLayer``(`[`NFEFeatureLayer`](../../model/feature/NFEFeatureLayer.md)` featLayer)`<br>Deletes the feature layer.                                                                                                                                                                                                                                |
    | `void`                                                                      | `deleteFeatureLayerAttributes``(`[`NFEFeatureLayer`](../../model/feature/NFEFeatureLayer.md)` featLayer, java.util.Collection<`[`NFEAttributeDescriptor`](../../model/feature/NFEAttributeDescriptor.md)`> attrDescriptors)`<br>Deletes the feature layer attributes.                                                                                        |
    | `void`                                                                      | `deleteModel``()`<br>Deletes the model.                                                                                                                                                                                                                                                                                                                      |
    | `void`                                                                      | `enableAnalysisInModel``()`<br>Enables the analysis searching creating the path layer.                                                                                                                                                                                                                                                                       |
    | `java.util.Collection<`[`NFECatalog`](../../model/feature/NFECatalog.md)`>` | `getCatalogs``()`<br>Returns all the catalogs related to the model.                                                                                                                                                                                                                                                                                          |
    | `java.util.Map<java.lang.Long,java.util.Collection<java.lang.String>>`      | `getFeatureLayersAttributesUsingCatalog``(long catalogId)`<br>Returns a map with as key the feature layer identifiers and as values the list of attributes using the catalog.                                                                                                                                                                                |
    | `java.util.Map<java.lang.Long,java.lang.String>`                            | `getModelsIdentificators``()`<br>Returns a map with identifiers and names of all the existing models.                                                                                                                                                                                                                                                        |
    | [`NFEModel`](../../model/NFEModel.md)                                       | `loadModel``(java.lang.String modelName)`<br>Loads the NFE model.                                                                                                                                                                                                                                                                                            |
    | `void`                                                                      | `persistCatalog``(`[`NFECatalog`](../../model/feature/NFECatalog.md)` catalog)`<br>Persists a catalog.                                                                                                                                                                                                                                                       |
    | `void`                                                                      | `persistFeatureClass``(`[`NFEFeatureClass`](../../model/feature/NFEFeatureClass.md)` featClass)`<br>Persists a feature class.                                                                                                                                                                                                                                |
    | `void`                                                                      | `persistFeatureLayerAttributes``(`[`NFEFeatureLayer`](../../model/feature/NFEFeatureLayer.md)` featLayer, java.util.Collection<`[`NFEAttributeDescriptor`](../../model/feature/NFEAttributeDescriptor.md)`> attrDescriptors)`<br>Persists the feature layer attributes.                                                                                      |
    | `void`                                                                      | `persistRules``(java.util.Collection<`[`NFEConnectivityRule`](../../model/rule/NFEConnectivityRule.md)`> newRules, java.util.Collection<`[`NFEConnectivityRule`](../../model/rule/NFEConnectivityRule.md)`> deletedRules, java.util.Collection<`[`NFEConnectivityRule`](../../model/rule/NFEConnectivityRule.md)`> updatedRules)`<br>Persists the NFE rules. |
    | `long`                                                                      | `registerRuleHandler``(java.lang.String handlerFQClassName, `[`NFEConnectivityRule.ConnectivityRuleType`](../../model/rule/NFEConnectivityRule.ConnectivityRuleType.md)` ruleType)`<br>Registers the rule handler for the specified rule.                                                                                                                    |
    | `void`                                                                      | `updateAttributeConstraints``(java.lang.Long featureClassId, java.lang.String attributeName, java.lang.String newValue)`<br>Updates the attribute default value for the specified feature class.                                                                                                                                                             |
    | `void`                                                                      | `updateCatalog``(`[`NFECatalog`](../../model/feature/NFECatalog.md)` catalog)`<br>Updates the catalog values of the specified catalog.                                                                                                                                                                                                                       |
    | `void`                                                                      | `updateFeatureClass``(`[`NFEFeatureClass`](../../model/feature/NFEFeatureClass.md)` featClass)`<br>Updates the feature class.                                                                                                                                                                                                                                |
    | `void`                                                                      | `updateFeatureLayersZOrder``(java.util.Collection<`[`NFEFeatureLayer`](../../model/feature/NFEFeatureLayer.md)`> featLayers)`<br>Updates the feature layers Z-order.                                                                                                                                                                                         |

    - ### Methods inherited from interface oracle.spatial.network.nfe.io.service.[NFEIOService](NFEIOService.md)

      [`getDataSource`](NFEIOService.md)`, `[`getModel`](NFEIOService.md)`, `[`getServiceProvider`](NFEIOService.md)`, `[`setDataSource`](NFEIOService.md)`, `[`setModel`](NFEIOService.md)

<!-- -->

- - ### Method Detail

    - #### createFromScratchModel

          NFEModel createFromScratchModel(java.lang.String modelName,
                                          boolean directedNetwork,
                                          NFEGeometryDescriptor geomDescriptor)
                                   throws NFEIOException

      Creates a model in from scratch mode. The function will create the initial model infrastructure if it doesn't exists along with the network used by the model. Also the function creates the tables related to the model: FT_CLASS, FT_CLASS_REL, FT_CLASS_ATTR_CSTR, FT_USR_DATA, FT_USR_DATA_CATLG, FT_USR_DATA_CVAL, FT_CLASS_DEF_CON_PT, LINE_LINE_RULE, LINE_POINT_RULE, RULE_INSTANCE, FT_RULE_REL, RULE_DEC_HANDLER, POINT_CARD_RULE.
      Parameters:
      `modelName` - NFE model name

      `directedNetwork` - true if the network to create has to be directed, false otherwise

      `geomDescriptor` - network geometry descriptor

      Returns:
      NFE model

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### createOverExistingNetworkModel

          NFEModel createOverExistingNetworkModel(java.lang.String modelName,
                                                  java.lang.String networkName)
                                           throws NFEIOException

      Creates a model in from existing network mode. The function will create the initial model infrastructure if it doesn't exists. Also the function creates the tables related to the model: FT_CLASS, FT_CLASS_REL, FT_CLASS_ATTR_CSTR, FT_USR_DATA, FT_USR_DATA_CATLG, FT_USR_DATA_CVAL, FT_CLASS_DEF_CON_PT, LINE_LINE_RULE, LINE_POINT_RULE, RULE_INSTANCE, FT_RULE_REL, RULE_DEC_HANDLER, POINT_CARD_RULE.
      Parameters:
      `modelName` - model name

      `networkName` - network name

      Returns:
      NFE model

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### createFeatureLayer

          NFEFeatureLayer createFeatureLayer(java.lang.String featureLayerName,
                                             java.lang.String featureTable,
                                             java.lang.String relationTable,
                                             java.lang.String hierarchyTable,
                                             java.util.Collection<NFEAttributeDescriptor> attrDescriptors,
                                             int hierarchyLevel,
                                             int zOrder)
                                      throws NFEIOException

      Creates a feature layer. Version disable the model before to execute this function (NFEWorkspaceIOService.disableAllVersioning) and reload the model after to execute it.
      Parameters:
      `featureLayerName` - feature layer name

      `featureTable` - feature table

      `relationTable` - relation table

      `hierarchyTable` - hierarchy table

      `attrDescriptors` - attributes descriptors

      `hierarchyLevel` - hierarchy level of the feature layer

      `zOrder` - Z-order of the feature layer. The Z-order determines which feature layer appears on top of the other.

      Returns:
      NFE feature layer

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### loadModel

          NFEModel loadModel(java.lang.String modelName)
                      throws NFEIOException

      Loads the NFE model. Note that the metadata and information about the feature layers will loaded but not the related features.
      Parameters:
      `modelName` - model name

      Returns:
      NFE model

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### persistFeatureClass

          void persistFeatureClass(NFEFeatureClass featClass)
                            throws NFEIOException

      Persists a feature class. Version disable the model before to execute this function (NFEWorkspaceIOService.disableAllVersioning) and reload the model after to execute it.
      Parameters:
      `featClass` - feature class

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### persistFeatureLayerAttributes

          void persistFeatureLayerAttributes(NFEFeatureLayer featLayer,
                                             java.util.Collection<NFEAttributeDescriptor> attrDescriptors)
                                      throws NFEIOException

      Persists the feature layer attributes. Version disable the model before to execute this function (NFEWorkspaceIOService.disableAllVersioning) and reload the model after to execute it.
      Parameters:
      `featLayer` - feature layer

      `attrDescriptors` - attributes descriptors

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### persistCatalog

          void persistCatalog(NFECatalog catalog)
                       throws NFEIOException

      Persists a catalog.
      Parameters:
      `catalog` - catalog

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### updateFeatureLayersZOrder

          void updateFeatureLayersZOrder(java.util.Collection<NFEFeatureLayer> featLayers)
                                  throws NFEIOException

      Updates the feature layers Z-order. The Z-order determines which feature layer appears on top of the other.
      Parameters:
      `featLayers` - feature layers to update

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### updateFeatureClass

          void updateFeatureClass(NFEFeatureClass featClass)
                           throws NFEIOException

      Updates the feature class. Updates the name, shape, cardinality rules, style, predefined points and attribute constraints. Version disable the model before to execute this function (NFEWorkspaceIOService.disableAllVersioning) and reloads the model after to execute it.
      Parameters:
      `featClass` - feature class

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### updateAttributeConstraints

          void updateAttributeConstraints(java.lang.Long featureClassId,
                                          java.lang.String attributeName,
                                          java.lang.String newValue)
                                   throws NFEIOException

      Updates the attribute default value for the specified feature class. Version disable the model before to execute this function (NFEWorkspaceIOService.disableAllVersioning) and reload the model after to execute it.
      Parameters:
      `featureClassId` - feature class id

      `attributeName` - attribute name

      `newValue` - new attribute default value

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### updateCatalog

          void updateCatalog(NFECatalog catalog)
                      throws NFEIOException

      Updates the catalog values of the specified catalog. Version disable the model before to execute this function (NFEWorkspaceIOService.disableAllVersioning) and reload the model after to execute it.
      Parameters:
      `catalog` - catalog

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteModel

          void deleteModel()
                    throws NFEIOException

      Deletes the model. Use carefully since this function will delete all the feature layers, tables and the network related to the model.
      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteFeatureLayer

          void deleteFeatureLayer(NFEFeatureLayer featLayer)
                           throws NFEIOException

      Deletes the feature layer. Use carefully since this function will delete all the data related to the feature layer. Before to execute this function delete the related features and rules. Version disable the model before to execute this function (NFEWorkspaceIOService.disableAllVersioning) and reload the model after to execute it.
      Parameters:
      `featLayer` - feature layer

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteFeatureClass

          void deleteFeatureClass(NFEFeatureClass featClass)
                           throws NFEIOException

      Deletes the feature class. Use carefully since this function will delete all the data related to the feature class. Before to execute this function delete the related features and rules. Version disable the model before to execute this function (NFEWorkspaceIOService.disableAllVersioning) and reload the model after to execute it.
      Parameters:
      `featClass` - feature class

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteFeatureLayerAttributes

          void deleteFeatureLayerAttributes(NFEFeatureLayer featLayer,
                                            java.util.Collection<NFEAttributeDescriptor> attrDescriptors)
                                     throws NFEIOException

      Deletes the feature layer attributes. Version disable the model before to execute this function (NFEWorkspaceIOService.disableAllVersioning) and reload the model after to execute it.
      Parameters:
      `featLayer` - feature layer

      `attrDescriptors` - attributes to delete

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteCatalog

          void deleteCatalog(long catalogId)
                      throws NFEIOException

      Deletes the specified catalog. The function getFeatureLayersAttributesUsingCatalog can be used to ensure that the catalog is not in use.
      Parameters:
      `catalogId` - catalog id

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getModelsIdentificators

          java.util.Map<java.lang.Long,java.lang.String> getModelsIdentificators()
                                                                          throws NFEIOException

      Returns a map with identifiers and names of all the existing models.
      Returns:
      map with identifiers (key) and names (value) of all the existing models.

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getCatalogs

          java.util.Collection<NFECatalog> getCatalogs()
                                                throws NFEIOException

      Returns all the catalogs related to the model.
      Returns:
      all the catalogs related to the model

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getFeatureLayersAttributesUsingCatalog

          java.util.Map<java.lang.Long,java.util.Collection<java.lang.String>> getFeatureLayersAttributesUsingCatalog(long catalogId)
                                                                                                               throws NFEIOException

      Returns a map with as key the feature layer identifiers and as values the list of attributes using the catalog.
      Parameters:
      `catalogId` - catalog id

      Returns:
      map with as key the feature layer identifiers and as values the list of attributes using the catalog

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### enableAnalysisInModel

          void enableAnalysisInModel()
                              throws NFEIOException

      Enables the analysis searching creating the path layer. It is mandatory to call this function before to perform any analysis. Additionally the paths that are saved in database will be load in Model. Note that if your model is analysis enabled the path features will be deleted when any related link or node is deleted.
      Throws:
      [`NFEIOException`](../NFEIOException.md)

    <!-- -->

    - #### persistRules

          void persistRules(java.util.Collection<NFEConnectivityRule> newRules,
                            java.util.Collection<NFEConnectivityRule> deletedRules,
                            java.util.Collection<NFEConnectivityRule> updatedRules)
                     throws NFEIOException

      Persists the NFE rules. In case of update or delete operations the rule has to be unused by any feature. This implies that no record related to the rule has to be in the table FT_RULE_REL\_\[model_id\]. In case of the line line rules create or update operations the line point rules have to refer to the same point feature including the same attributes conditions if any.
      Parameters:
      `newRules` - rules to add

      `deletedRules` - rules to delete

      `updatedRules` - rules to update

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### registerRuleHandler

          long registerRuleHandler(java.lang.String handlerFQClassName,
                                   NFEConnectivityRule.ConnectivityRuleType ruleType)
                            throws NFEIOException

      Registers the rule handler for the specified rule.
      Parameters:
      `handlerFQClassName` - rule handler full qualified class name

      `ruleType` - type of rule the handler is for

      Returns:
      the id of the registered rule handler

      Throws:
      [`NFEIOException`](../NFEIOException.md) - if an NFE error occurs.

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

- [Prev Class](NFEIOServiceProvider.md)
- [Next Class](NFEWorkspaceIOService.md)

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
