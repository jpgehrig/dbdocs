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

- [Prev Class](JDBCIOServiceProvider.md)
- [Next Class](JDBCWorkspaceIOService.md)

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

## Class JDBCModelIOService

- java.lang.Object

- - [oracle.spatial.network.nfe.io.jdbc.service.JDBCAbstractIOService](JDBCAbstractIOService.md)

  - - oracle.spatial.network.nfe.io.jdbc.service.JDBCModelIOService

<!-- -->

- All Implemented Interfaces:
  [NFEIOService](../../service/NFEIOService.md), [NFEModelIOService](../../service/NFEModelIOService.md)

  ------------------------------------------------------------------------



      public class JDBCModelIOService
      extends JDBCAbstractIOService
      implements NFEModelIOService

  Provides the default implementation for the model service.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                |
    |------------------------------------------------------------------------------------------------------------|
    | `JDBCModelIOService``(`[`NFEIOServiceProvider`](../../service/NFEIOServiceProvider.md)` serviceProvider)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                              | Method and Description                                                                                                                                                                                                                                                                                                                                                |
    |--------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`NFEFeatureLayer`](../../../model/feature/NFEFeatureLayer.md)                 | `createFeatureLayer``(java.lang.String featureLayerName, java.lang.String featureTable, java.lang.String relationTable, java.lang.String hierarchyTable, java.util.Collection<`[`NFEAttributeDescriptor`](../../../model/feature/NFEAttributeDescriptor.md)`> attrDescriptors, int hierarchyLevel, int zOrder)`<br>Creates a feature layer.                           |
    | [`NFEModel`](../../../model/NFEModel.md)                                       | `createFromScratchModel``(java.lang.String modelName, boolean directedNetwork, `[`NFEGeometryDescriptor`](../../../model/NFEGeometryDescriptor.md)` geomDescriptor)`<br>Creates a model in from scratch mode.                                                                                                                                                         |
    | [`NFEModel`](../../../model/NFEModel.md)                                       | `createOverExistingNetworkModel``(java.lang.String modelName, java.lang.String networkName)`<br>Creates a model in from existing network mode.                                                                                                                                                                                                                        |
    | `void`                                                                         | `deleteCatalog``(long catalogId)`<br>Deletes the specified catalog.                                                                                                                                                                                                                                                                                                   |
    | `void`                                                                         | `deleteFeatureClass``(`[`NFEFeatureClass`](../../../model/feature/NFEFeatureClass.md)` featClass)`<br>Deletes the feature class.                                                                                                                                                                                                                                      |
    | `void`                                                                         | `deleteFeatureLayer``(`[`NFEFeatureLayer`](../../../model/feature/NFEFeatureLayer.md)` featLayer)`<br>Deletes the feature layer.                                                                                                                                                                                                                                      |
    | `void`                                                                         | `deleteFeatureLayerAttributes``(`[`NFEFeatureLayer`](../../../model/feature/NFEFeatureLayer.md)` featLayer, java.util.Collection<`[`NFEAttributeDescriptor`](../../../model/feature/NFEAttributeDescriptor.md)`> attrDescriptors)`<br>Deletes the feature layer attributes.                                                                                           |
    | `void`                                                                         | `deleteModel``()`<br>Deletes the model.                                                                                                                                                                                                                                                                                                                               |
    | `void`                                                                         | `enableAnalysisInModel``()`<br>Enables the analysis searching creating the path layer.                                                                                                                                                                                                                                                                                |
    | `java.util.Collection<`[`NFECatalog`](../../../model/feature/NFECatalog.md)`>` | `getCatalogs``()`<br>Returns all the catalogs related to the model.                                                                                                                                                                                                                                                                                                   |
    | `java.util.Map<java.lang.Long,java.util.Collection<java.lang.String>>`         | `getFeatureLayersAttributesUsingCatalog``(long catalogId)`<br>Returns a map with as key the feature layer identifiers and as values the list of attributes using the catalog.                                                                                                                                                                                         |
    | `java.util.Map<java.lang.Long,java.lang.String>`                               | `getModelsIdentificators``()`<br>Returns a map with identifiers and names of all the existing models.                                                                                                                                                                                                                                                                 |
    | [`NFEModel`](../../../model/NFEModel.md)                                       | `loadModel``(java.lang.String modelName)`<br>Loads the NFE model.                                                                                                                                                                                                                                                                                                     |
    | `void`                                                                         | `persistCatalog``(`[`NFECatalog`](../../../model/feature/NFECatalog.md)` catalog)`<br>Persists a catalog.                                                                                                                                                                                                                                                             |
    | `void`                                                                         | `persistFeatureClass``(`[`NFEFeatureClass`](../../../model/feature/NFEFeatureClass.md)` featClass)`<br>Persists a feature class.                                                                                                                                                                                                                                      |
    | `void`                                                                         | `persistFeatureLayerAttributes``(`[`NFEFeatureLayer`](../../../model/feature/NFEFeatureLayer.md)` featLayer, java.util.Collection<`[`NFEAttributeDescriptor`](../../../model/feature/NFEAttributeDescriptor.md)`> attrDescriptors)`<br>Persists the feature layer attributes.                                                                                         |
    | `void`                                                                         | `persistRules``(java.util.Collection<`[`NFEConnectivityRule`](../../../model/rule/NFEConnectivityRule.md)`> newRules, java.util.Collection<`[`NFEConnectivityRule`](../../../model/rule/NFEConnectivityRule.md)`> deletedRules, java.util.Collection<`[`NFEConnectivityRule`](../../../model/rule/NFEConnectivityRule.md)`> updatedRules)`<br>Persists the NFE rules. |
    | `long`                                                                         | `registerRuleHandler``(java.lang.String handlerFQClassName, `[`NFEConnectivityRule.ConnectivityRuleType`](../../../model/rule/NFEConnectivityRule.ConnectivityRuleType.md)` ruleType)`<br>Registers the rule handler for the specified rule.                                                                                                                          |
    | `void`                                                                         | `updateAttributeConstraints``(java.lang.Long featureClassId, java.lang.String attributeName, java.lang.String newValue)`<br>Updates the attribute default value for the specified feature class.                                                                                                                                                                      |
    | `void`                                                                         | `updateCatalog``(`[`NFECatalog`](../../../model/feature/NFECatalog.md)` catalog)`<br>Updates the catalog values of the specified catalog.                                                                                                                                                                                                                             |
    | `void`                                                                         | `updateFeatureClass``(`[`NFEFeatureClass`](../../../model/feature/NFEFeatureClass.md)` featClass)`<br>Updates the feature class.                                                                                                                                                                                                                                      |
    | `void`                                                                         | `updateFeatureLayersZOrder``(java.util.Collection<`[`NFEFeatureLayer`](../../../model/feature/NFEFeatureLayer.md)`> featLayers)`<br>Updates the feature layers Z-order.                                                                                                                                                                                               |

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

    - #### JDBCModelIOService

          public JDBCModelIOService(NFEIOServiceProvider serviceProvider)

  <!-- -->

  - ### Method Detail

    - #### createFromScratchModel

          public NFEModel createFromScratchModel(java.lang.String modelName,
                                                 boolean directedNetwork,
                                                 NFEGeometryDescriptor geomDescriptor)
                                          throws NFEIOException

      Description copied from interface: [`NFEModelIOService`](../../service/NFEModelIOService.md)
      Creates a model in from scratch mode. The function will create the initial model infrastructure if it doesn't exists along with the network used by the model. Also the function creates the tables related to the model: FT_CLASS, FT_CLASS_REL, FT_CLASS_ATTR_CSTR, FT_USR_DATA, FT_USR_DATA_CATLG, FT_USR_DATA_CVAL, FT_CLASS_DEF_CON_PT, LINE_LINE_RULE, LINE_POINT_RULE, RULE_INSTANCE, FT_RULE_REL, RULE_DEC_HANDLER, POINT_CARD_RULE.
      Specified by:
      [`createFromScratchModel`](../../service/NFEModelIOService.md) in interface [`NFEModelIOService`](../../service/NFEModelIOService.md)

      Parameters:
      `modelName` - NFE model name

      `directedNetwork` - true if the network to create has to be directed, false otherwise

      `geomDescriptor` - network geometry descriptor

      Returns:
      NFE model

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### createOverExistingNetworkModel

          public NFEModel createOverExistingNetworkModel(java.lang.String modelName,
                                                         java.lang.String networkName)
                                                  throws NFEIOException

      Description copied from interface: [`NFEModelIOService`](../../service/NFEModelIOService.md)
      Creates a model in from existing network mode. The function will create the initial model infrastructure if it doesn't exists. Also the function creates the tables related to the model: FT_CLASS, FT_CLASS_REL, FT_CLASS_ATTR_CSTR, FT_USR_DATA, FT_USR_DATA_CATLG, FT_USR_DATA_CVAL, FT_CLASS_DEF_CON_PT, LINE_LINE_RULE, LINE_POINT_RULE, RULE_INSTANCE, FT_RULE_REL, RULE_DEC_HANDLER, POINT_CARD_RULE.
      Specified by:
      [`createOverExistingNetworkModel`](../../service/NFEModelIOService.md) in interface [`NFEModelIOService`](../../service/NFEModelIOService.md)

      Parameters:
      `modelName` - model name

      `networkName` - network name

      Returns:
      NFE model

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### createFeatureLayer

          public NFEFeatureLayer createFeatureLayer(java.lang.String featureLayerName,
                                                    java.lang.String featureTable,
                                                    java.lang.String relationTable,
                                                    java.lang.String hierarchyTable,
                                                    java.util.Collection<NFEAttributeDescriptor> attrDescriptors,
                                                    int hierarchyLevel,
                                                    int zOrder)
                                             throws NFEIOException

      Description copied from interface: [`NFEModelIOService`](../../service/NFEModelIOService.md)
      Creates a feature layer. Version disable the model before to execute this function (NFEWorkspaceIOService.disableAllVersioning) and reload the model after to execute it.
      Specified by:
      [`createFeatureLayer`](../../service/NFEModelIOService.md) in interface [`NFEModelIOService`](../../service/NFEModelIOService.md)

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
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### enableAnalysisInModel

          public void enableAnalysisInModel()
                                     throws NFEIOException

      Description copied from interface: [`NFEModelIOService`](../../service/NFEModelIOService.md)
      Enables the analysis searching creating the path layer. It is mandatory to call this function before to perform any analysis. Additionally the paths that are saved in database will be load in Model. Note that if your model is analysis enabled the path features will be deleted when any related link or node is deleted.
      Specified by:
      [`enableAnalysisInModel`](../../service/NFEModelIOService.md) in interface [`NFEModelIOService`](../../service/NFEModelIOService.md)

      Throws:
      [`NFEIOException`](../../NFEIOException.md)

    <!-- -->

    - #### loadModel

          public NFEModel loadModel(java.lang.String modelName)
                             throws NFEIOException

      Description copied from interface: [`NFEModelIOService`](../../service/NFEModelIOService.md)
      Loads the NFE model. Note that the metadata and information about the feature layers will loaded but not the related features.
      Specified by:
      [`loadModel`](../../service/NFEModelIOService.md) in interface [`NFEModelIOService`](../../service/NFEModelIOService.md)

      Parameters:
      `modelName` - model name

      Returns:
      NFE model

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### persistFeatureClass

          public void persistFeatureClass(NFEFeatureClass featClass)
                                   throws NFEIOException

      Description copied from interface: [`NFEModelIOService`](../../service/NFEModelIOService.md)
      Persists a feature class. Version disable the model before to execute this function (NFEWorkspaceIOService.disableAllVersioning) and reload the model after to execute it.
      Specified by:
      [`persistFeatureClass`](../../service/NFEModelIOService.md) in interface [`NFEModelIOService`](../../service/NFEModelIOService.md)

      Parameters:
      `featClass` - feature class

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### persistFeatureLayerAttributes

          public void persistFeatureLayerAttributes(NFEFeatureLayer featLayer,
                                                    java.util.Collection<NFEAttributeDescriptor> attrDescriptors)
                                             throws NFEIOException

      Description copied from interface: [`NFEModelIOService`](../../service/NFEModelIOService.md)
      Persists the feature layer attributes. Version disable the model before to execute this function (NFEWorkspaceIOService.disableAllVersioning) and reload the model after to execute it.
      Specified by:
      [`persistFeatureLayerAttributes`](../../service/NFEModelIOService.md) in interface [`NFEModelIOService`](../../service/NFEModelIOService.md)

      Parameters:
      `featLayer` - feature layer

      `attrDescriptors` - attributes descriptors

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### persistCatalog

          public void persistCatalog(NFECatalog catalog)
                              throws NFEIOException

      Description copied from interface: [`NFEModelIOService`](../../service/NFEModelIOService.md)
      Persists a catalog.
      Specified by:
      [`persistCatalog`](../../service/NFEModelIOService.md) in interface [`NFEModelIOService`](../../service/NFEModelIOService.md)

      Parameters:
      `catalog` - catalog

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### updateFeatureLayersZOrder

          public void updateFeatureLayersZOrder(java.util.Collection<NFEFeatureLayer> featLayers)
                                         throws NFEIOException

      Description copied from interface: [`NFEModelIOService`](../../service/NFEModelIOService.md)
      Updates the feature layers Z-order. The Z-order determines which feature layer appears on top of the other.
      Specified by:
      [`updateFeatureLayersZOrder`](../../service/NFEModelIOService.md) in interface [`NFEModelIOService`](../../service/NFEModelIOService.md)

      Parameters:
      `featLayers` - feature layers to update

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### updateFeatureClass

          public void updateFeatureClass(NFEFeatureClass featClass)
                                  throws NFEIOException

      Description copied from interface: [`NFEModelIOService`](../../service/NFEModelIOService.md)
      Updates the feature class. Updates the name, shape, cardinality rules, style, predefined points and attribute constraints. Version disable the model before to execute this function (NFEWorkspaceIOService.disableAllVersioning) and reloads the model after to execute it.
      Specified by:
      [`updateFeatureClass`](../../service/NFEModelIOService.md) in interface [`NFEModelIOService`](../../service/NFEModelIOService.md)

      Parameters:
      `featClass` - feature class

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### updateAttributeConstraints

          public void updateAttributeConstraints(java.lang.Long featureClassId,
                                                 java.lang.String attributeName,
                                                 java.lang.String newValue)
                                          throws NFEIOException

      Description copied from interface: [`NFEModelIOService`](../../service/NFEModelIOService.md)
      Updates the attribute default value for the specified feature class. Version disable the model before to execute this function (NFEWorkspaceIOService.disableAllVersioning) and reload the model after to execute it.
      Specified by:
      [`updateAttributeConstraints`](../../service/NFEModelIOService.md) in interface [`NFEModelIOService`](../../service/NFEModelIOService.md)

      Parameters:
      `featureClassId` - feature class id

      `attributeName` - attribute name

      `newValue` - new attribute default value

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### updateCatalog

          public void updateCatalog(NFECatalog catalog)
                             throws NFEIOException

      Description copied from interface: [`NFEModelIOService`](../../service/NFEModelIOService.md)
      Updates the catalog values of the specified catalog. Version disable the model before to execute this function (NFEWorkspaceIOService.disableAllVersioning) and reload the model after to execute it.
      Specified by:
      [`updateCatalog`](../../service/NFEModelIOService.md) in interface [`NFEModelIOService`](../../service/NFEModelIOService.md)

      Parameters:
      `catalog` - catalog

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteModel

          public void deleteModel()
                           throws NFEIOException

      Description copied from interface: [`NFEModelIOService`](../../service/NFEModelIOService.md)
      Deletes the model. Use carefully since this function will delete all the feature layers, tables and the network related to the model.
      Specified by:
      [`deleteModel`](../../service/NFEModelIOService.md) in interface [`NFEModelIOService`](../../service/NFEModelIOService.md)

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteFeatureLayer

          public void deleteFeatureLayer(NFEFeatureLayer featLayer)
                                  throws NFEIOException

      Description copied from interface: [`NFEModelIOService`](../../service/NFEModelIOService.md)
      Deletes the feature layer. Use carefully since this function will delete all the data related to the feature layer. Before to execute this function delete the related features and rules. Version disable the model before to execute this function (NFEWorkspaceIOService.disableAllVersioning) and reload the model after to execute it.
      Specified by:
      [`deleteFeatureLayer`](../../service/NFEModelIOService.md) in interface [`NFEModelIOService`](../../service/NFEModelIOService.md)

      Parameters:
      `featLayer` - feature layer

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteFeatureClass

          public void deleteFeatureClass(NFEFeatureClass featClass)
                                  throws NFEIOException

      Description copied from interface: [`NFEModelIOService`](../../service/NFEModelIOService.md)
      Deletes the feature class. Use carefully since this function will delete all the data related to the feature class. Before to execute this function delete the related features and rules. Version disable the model before to execute this function (NFEWorkspaceIOService.disableAllVersioning) and reload the model after to execute it.
      Specified by:
      [`deleteFeatureClass`](../../service/NFEModelIOService.md) in interface [`NFEModelIOService`](../../service/NFEModelIOService.md)

      Parameters:
      `featClass` - feature class

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteFeatureLayerAttributes

          public void deleteFeatureLayerAttributes(NFEFeatureLayer featLayer,
                                                   java.util.Collection<NFEAttributeDescriptor> attrDescriptors)
                                            throws NFEIOException

      Description copied from interface: [`NFEModelIOService`](../../service/NFEModelIOService.md)
      Deletes the feature layer attributes. Version disable the model before to execute this function (NFEWorkspaceIOService.disableAllVersioning) and reload the model after to execute it.
      Specified by:
      [`deleteFeatureLayerAttributes`](../../service/NFEModelIOService.md) in interface [`NFEModelIOService`](../../service/NFEModelIOService.md)

      Parameters:
      `featLayer` - feature layer

      `attrDescriptors` - attributes to delete

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteCatalog

          public void deleteCatalog(long catalogId)
                             throws NFEIOException

      Description copied from interface: [`NFEModelIOService`](../../service/NFEModelIOService.md)
      Deletes the specified catalog. The function getFeatureLayersAttributesUsingCatalog can be used to ensure that the catalog is not in use.
      Specified by:
      [`deleteCatalog`](../../service/NFEModelIOService.md) in interface [`NFEModelIOService`](../../service/NFEModelIOService.md)

      Parameters:
      `catalogId` - catalog id

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getModelsIdentificators

          public java.util.Map<java.lang.Long,java.lang.String> getModelsIdentificators()
                                                                                 throws NFEIOException

      Description copied from interface: [`NFEModelIOService`](../../service/NFEModelIOService.md)
      Returns a map with identifiers and names of all the existing models.
      Specified by:
      [`getModelsIdentificators`](../../service/NFEModelIOService.md) in interface [`NFEModelIOService`](../../service/NFEModelIOService.md)

      Returns:
      map with identifiers (key) and names (value) of all the existing models.

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getCatalogs

          public java.util.Collection<NFECatalog> getCatalogs()
                                                       throws NFEIOException

      Description copied from interface: [`NFEModelIOService`](../../service/NFEModelIOService.md)
      Returns all the catalogs related to the model.
      Specified by:
      [`getCatalogs`](../../service/NFEModelIOService.md) in interface [`NFEModelIOService`](../../service/NFEModelIOService.md)

      Returns:
      all the catalogs related to the model

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getFeatureLayersAttributesUsingCatalog

          public java.util.Map<java.lang.Long,java.util.Collection<java.lang.String>> getFeatureLayersAttributesUsingCatalog(long catalogId)
                                                                                                                      throws NFEIOException

      Description copied from interface: [`NFEModelIOService`](../../service/NFEModelIOService.md)
      Returns a map with as key the feature layer identifiers and as values the list of attributes using the catalog.
      Specified by:
      [`getFeatureLayersAttributesUsingCatalog`](../../service/NFEModelIOService.md) in interface [`NFEModelIOService`](../../service/NFEModelIOService.md)

      Parameters:
      `catalogId` - catalog id

      Returns:
      map with as key the feature layer identifiers and as values the list of attributes using the catalog

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### persistRules

          public void persistRules(java.util.Collection<NFEConnectivityRule> newRules,
                                   java.util.Collection<NFEConnectivityRule> deletedRules,
                                   java.util.Collection<NFEConnectivityRule> updatedRules)
                            throws NFEIOException

      Description copied from interface: [`NFEModelIOService`](../../service/NFEModelIOService.md)
      Persists the NFE rules. In case of update or delete operations the rule has to be unused by any feature. This implies that no record related to the rule has to be in the table FT_RULE_REL\_\[model_id\]. In case of the line line rules create or update operations the line point rules have to refer to the same point feature including the same attributes conditions if any.
      Specified by:
      [`persistRules`](../../service/NFEModelIOService.md) in interface [`NFEModelIOService`](../../service/NFEModelIOService.md)

      Parameters:
      `newRules` - rules to add

      `deletedRules` - rules to delete

      `updatedRules` - rules to update

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### registerRuleHandler

          public long registerRuleHandler(java.lang.String handlerFQClassName,
                                          NFEConnectivityRule.ConnectivityRuleType ruleType)
                                   throws NFEIOException

      Description copied from interface: [`NFEModelIOService`](../../service/NFEModelIOService.md)
      Registers the rule handler for the specified rule.
      Specified by:
      [`registerRuleHandler`](../../service/NFEModelIOService.md) in interface [`NFEModelIOService`](../../service/NFEModelIOService.md)

      Parameters:
      `handlerFQClassName` - rule handler full qualified class name

      `ruleType` - type of rule the handler is for

      Returns:
      the id of the registered rule handler

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

- [Prev Class](JDBCIOServiceProvider.md)
- [Next Class](JDBCWorkspaceIOService.md)

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
