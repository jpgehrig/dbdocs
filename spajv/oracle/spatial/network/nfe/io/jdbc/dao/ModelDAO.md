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

- [Prev Class](FeatureDAO.md)
- [Next Class](ModelDAO.ModelFeatLayerRelation.md)

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

## Class ModelDAO

- java.lang.Object

- - [oracle.spatial.network.nfe.io.jdbc.dao.AbstractDAO](AbstractDAO.md)

  - - oracle.spatial.network.nfe.io.jdbc.dao.ModelDAO

<!-- -->

-

  ------------------------------------------------------------------------



      public class ModelDAO
      extends AbstractDAO

  The ModelDAO data access object provides methods to load, create and manage the model infrastructure. It is not recommended to use the data access objects methods, instead use the NFE services.

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Class and Description                                                                                                             |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------------|
    | `class `          | [`ModelDAO.ModelFeatLayerRelation`](ModelDAO.ModelFeatLayerRelation.md)<br>Class that store information about the feature layers. |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                             |
    |---------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `ModelDAO``(java.sql.Connection conn, `[`NFEModel`](../../../model/NFEModel.md)` model)`<br>Creates a ModelDAO with the specified connection and model. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                      | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    |--------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                                                 | `addAttributesToFeatureTable``(`[`NFEFeatureLayerMetadata`](../../../model/feature/NFEFeatureLayerMetadata.md)` featLayerMetadata, java.util.Collection<`[`NFEAttributeDescriptor`](../../../model/feature/NFEAttributeDescriptor.md)`> attributeDescriptors)`<br>Adds the specified attributes to the feature table.                                                                                                                                                                                             |
    | `void`                                                                                                 | `addFeatureLayerToModel``(`[`NFEFeatureLayer`](../../../model/feature/NFEFeatureLayer.md)` featureLayer, `[`NFEModelMetadata`](../../../model/NFEModelMetadata.md)` modelMetadata, boolean isPath)`<br>Adds the feature layer record to the table USER_SDO_NFE_MODEL_FTLAYER_REL.                                                                                                                                                                                                                                 |
    | `void`                                                                                                 | `createFeatureClass``(`[`NFEModelMetadata`](../../../model/NFEModelMetadata.md)` modelMetadata, `[`NFEFeatureClass`](../../../model/feature/NFEFeatureClass.md)` featClass, boolean addPredefinedConnectedPointInfo, boolean addAttributeConstraints)`<br>Persists a feature class.                                                                                                                                                                                                                               |
    | `long`                                                                                                 | `createFeatureLayer``(`[`NFEFeatureLayerMetadata`](../../../model/feature/NFEFeatureLayerMetadata.md)` featureLayerMetadata, java.util.Collection<`[`NFEAttributeDescriptor`](../../../model/feature/NFEAttributeDescriptor.md)`> attributeDescriptors)`<br>Creates the feature layer tables and metadata.                                                                                                                                                                                                        |
    | `void`                                                                                                 | `createModelSequence``(long modelId, java.lang.String ownerTable, java.lang.String sequenceName)`<br>Creates a sequence in database and a record in the model sequence table.                                                                                                                                                                                                                                                                                                                                     |
    | [`NFEModelMetadata`](../../../model/NFEModelMetadata.md)                                               | `createNewModelTables``(java.lang.String modelName, `[`NFEEditionMode`](../../../model/NFEEditionMode.md)` editionMode, boolean isVersionable)`<br>Creates the needed tables for a new model.                                                                                                                                                                                                                                                                                                                     |
    | `void`                                                                                                 | `deleteCatalog``(`[`NFEModelMetadata`](../../../model/NFEModelMetadata.md)` modelMetadata, java.lang.Long catalogId)`<br>Deletes the specified catalog.                                                                                                                                                                                                                                                                                                                                                           |
    | `void`                                                                                                 | `deleteFeatureClass``(`[`NFEModelMetadata`](../../../model/NFEModelMetadata.md)` nfeModelMetadata, `[`NFEFeatureClass`](../../../model/feature/NFEFeatureClass.md)` nfeFeatureClass)`<br>Deletes the feature class record from the FT_CLASS\_\[model_id\] table related to the specified feature class and delete the related connected points and attribute constraints information from tables FT_CLASS_DEF_CON_PT\_\[model_id\] and FT_CLASS_ATTR_CSTR\_\[model_id\].                                          |
    | `void`                                                                                                 | `deleteFeatureClasses``(`[`NFEModelMetadata`](../../../model/NFEModelMetadata.md)` nfeModelMetadata, `[`NFEFeatureLayer`](../../../model/feature/NFEFeatureLayer.md)` nfeFeatureLayer)`<br>Deletes the feature classes records from the FT_CLASS\_\[model_id\] table related to the specified feature layer and delete the related connected points and attribute constraints information from tables FT_CLASS_DEF_CON_PT\_\[model_id\] and FT_CLASS_ATTR_CSTR\_\[model_id\].                                     |
    | `void`                                                                                                 | `deleteFeatureClassesAttributesConstraints``(`[`NFEModelMetadata`](../../../model/NFEModelMetadata.md)` modelMetadata, java.util.Collection<`[`NFEFeatureClass`](../../../model/feature/NFEFeatureClass.md)`> featureClasses)`<br>Deletes all the attributes constraints related to the specified feature classes in the FT_CLASS_ATTR_CSTR\_\[model_id\] table.                                                                                                                                                  |
    | `void`                                                                                                 | `deleteFeatureClassHierarchyRelationship``(`[`NFEModelMetadata`](../../../model/NFEModelMetadata.md)` nfeModelMetadata, `[`NFEFeatureClass`](../../../model/feature/NFEFeatureClass.md)` featureClass, java.util.Collection<`[`NFEFeatureLayerMetadata`](../../../model/feature/NFEFeatureLayerMetadata.md)`> featureLayersMetadata)`<br>Deletes any relation of the class with the hierarchy table (parent or child)                                                                                             |
    | `void`                                                                                                 | `deleteFeatureClassRel``(`[`NFEModelMetadata`](../../../model/NFEModelMetadata.md)` nfeModelMetadata, `[`NFEFeatureClass`](../../../model/feature/NFEFeatureClass.md)` nfeFeatureClass)`<br>Deletes the records from the table FT_CLASS_REL\_\[model_id\] related to the specified feature class.                                                                                                                                                                                                                 |
    | `void`                                                                                                 | `deleteFeatureClassRel``(`[`NFEModelMetadata`](../../../model/NFEModelMetadata.md)` nfeModelMetadata, `[`NFEFeatureLayer`](../../../model/feature/NFEFeatureLayer.md)` nfeFeatureLayer)`<br>Deletes the records from the table FT_CLASS_REL\_\[model_id\] related to the specified feature classes.                                                                                                                                                                                                               |
    | `void`                                                                                                 | `deleteFeatureLayer``(`[`NFEFeatureLayerMetadata`](../../../model/feature/NFEFeatureLayerMetadata.md)` featureLayerMetadata)`<br>Drops (deletes) a feature layer using the database procedure sdo_net.drop_feature_layer.                                                                                                                                                                                                                                                                                         |
    | `void`                                                                                                 | `deleteFeatureLayerAttributes``(`[`NFEModelMetadata`](../../../model/NFEModelMetadata.md)` nfeModelMetadata, `[`NFEFeatureLayer`](../../../model/feature/NFEFeatureLayer.md)` nfeFeatureLayer, java.util.Collection<`[`NFEAttributeDescriptor`](../../../model/feature/NFEAttributeDescriptor.md)`> attributeDescriptors)`<br>Deletes the attributes for the specified feature layer from the user_sdo_network_user_data view and from the FT_CLASS_ATTR_CSTR\_\[model_id\] and FT_USR_DATA\_\[model_id\] tables. |
    | `void`                                                                                                 | `deleteFeatureLayerToProject``(`[`NFEFeatureLayer`](../../../model/feature/NFEFeatureLayer.md)` featureLayer, `[`NFEModelMetadata`](../../../model/NFEModelMetadata.md)` nfeModelMetadata)`<br>Deletes the feature layer record from the table USER_SDO_NFE_MODEL_FTLAYER_REL.                                                                                                                                                                                                                                    |
    | `void`                                                                                                 | `deleteModel``(long modelId)`<br>Deletes model structure.                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `void`                                                                                                 | `deleteModelTables``(int modelId)`<br>Drops the model's tables and its registry in the Model-Metadata table.                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `void`                                                                                                 | `dropAttributeFromFeatureTable``(`[`NFEFeatureLayerMetadata`](../../../model/feature/NFEFeatureLayerMetadata.md)` featLayerMetadata, `[`NFEAttributeDescriptor`](../../../model/feature/NFEAttributeDescriptor.md)` attrDescriptor)`<br>Drops the attribute column from the feature table.                                                                                                                                                                                                                        |
    | `void`                                                                                                 | `dropAttributesFromFeatureTable``(`[`NFEFeatureLayerMetadata`](../../../model/feature/NFEFeatureLayerMetadata.md)` featLayerMetadata, java.util.Collection<`[`NFEAttributeDescriptor`](../../../model/feature/NFEAttributeDescriptor.md)`> attributeDescriptors)`<br>Drops the specified attributes columns from the feature table.                                                                                                                                                                               |
    | `void`                                                                                                 | `dropFeatureTable``(java.lang.String featureTableName)`<br>Drops the feature table with the specified name.                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `java.util.Map<java.lang.Long,java.util.Collection<java.lang.String>>`                                 | `fetchFeatLayersAttributesUsingCatalog``(`[`NFEModelMetadata`](../../../model/NFEModelMetadata.md)` modelMetadata, long catalogId)`<br>Returns a map with as key the feature layer identifiers and as values the list of the attributes using the specified catalog.                                                                                                                                                                                                                                              |
    | `java.util.Collection<`[`ModelDAO.ModelFeatLayerRelation`](ModelDAO.ModelFeatLayerRelation.md)`>`      | `fetchModelFeatureLayersRelations``(`[`NFEModelMetadata`](../../../model/NFEModelMetadata.md)` modelMetadata, boolean path)`<br>Returns the feature layers information related to the specified model.                                                                                                                                                                                                                                                                                                            |
    | `java.util.HashMap<java.lang.Long,java.lang.String>`                                                   | `fetchModelIdentificators``()`<br>Returns a map containing the identifiers and names of all the existing models.                                                                                                                                                                                                                                                                                                                                                                                                  |
    | [`NFEModelMetadata`](../../../model/NFEModelMetadata.md)                                               | `fetchModelMetadata``(java.lang.String modelName)`<br>Retrieves the metadata for the model whose identifier is specified.                                                                                                                                                                                                                                                                                                                                                                                         |
    | `java.util.List<`[`NFECatalog`](../../../model/feature/NFECatalog.md)`>`                               | `getCatalogs``(`[`NFEModel`](../../../model/NFEModel.md)` nfeModel)`<br>Returns all the catalogs related to the specified model.                                                                                                                                                                                                                                                                                                                                                                                  |
    | `boolean`                                                                                              | `hasRelatedRules``(`[`NFEFeatureClass`](../../../model/feature/NFEFeatureClass.md)` featureClass)`<br>Returns true if the feature class is used in any NFE rule, false otherwise.                                                                                                                                                                                                                                                                                                                                 |
    | `boolean`                                                                                              | `hasRelatedRules``(`[`NFEFeatureLayer`](../../../model/feature/NFEFeatureLayer.md)` featureLayer)`<br>Returns true if the feature layer is used in any NFE rule, false otherwise.                                                                                                                                                                                                                                                                                                                                 |
    | `void`                                                                                                 | `initializeTables``(`[`NFEModelMetadata`](../../../model/NFEModelMetadata.md)` metadata)`<br>Creates default values in decision handler rules tables.                                                                                                                                                                                                                                                                                                                                                             |
    | `boolean`                                                                                              | `isFeatureTableEmpty``(`[`NFEFeatureClass`](../../../model/feature/NFEFeatureClass.md)` featureClass)`<br>Returns true if no features belong to the feature class, false otherwise.                                                                                                                                                                                                                                                                                                                               |
    | `boolean`                                                                                              | `isFeatureTableEmpty``(`[`NFEFeatureLayer`](../../../model/feature/NFEFeatureLayer.md)` featureLayer)`<br>Returns true if no features belong to the feature layer, false otherwise.                                                                                                                                                                                                                                                                                                                               |
    | `void`                                                                                                 | `loadSequencesRegistry``(java.util.Collection<java.lang.String> tableNames, `[`NFEModelMetadata`](../../../model/NFEModelMetadata.md)` modelMetadata)`<br>Loads the table sequences of the specified tables in the model metadata.                                                                                                                                                                                                                                                                                |
    | `boolean`                                                                                              | `modelExists``(java.lang.String modelName)`<br>Returns true if a model already exists with the specified name, false otherwise.                                                                                                                                                                                                                                                                                                                                                                                   |
    | `java.util.Collection<`[`NFEAttributeDescriptor`](../../../model/feature/NFEAttributeDescriptor.md)`>` | `registerFeatureLayerAttributes``(`[`NFEModelMetadata`](../../../model/NFEModelMetadata.md)` modelMetadata, `[`NFEFeatureLayerMetadata`](../../../model/feature/NFEFeatureLayerMetadata.md)` featLayerMetadata, java.util.Collection<`[`NFEAttributeDescriptor`](../../../model/feature/NFEAttributeDescriptor.md)`> attributeDescriptors)`<br>Registers the given attributes to the network and feature layer in xxx_sdo_network_data.                                                                           |
    | `void`                                                                                                 | `relateNetworkToModel``(long modelId, java.lang.String networkName)`<br>Relates a network with an NFE Model.                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `void`                                                                                                 | `removeModelSequence``(long modelId, java.lang.String sequenceName)`<br>Removes a sequence in database and the corresponding record in the model sequence table.                                                                                                                                                                                                                                                                                                                                                  |
    | `void`                                                                                                 | `removePointCardRule``(`[`NFEModelMetadata`](../../../model/NFEModelMetadata.md)` modelMetadata, `[`NFEFeatureClass`](../../../model/feature/NFEFeatureClass.md)` featClass)`<br>Removes the point cardinality rule from the point cardinality rule table related to the specified feature class.                                                                                                                                                                                                                 |
    | `void`                                                                                                 | `removePointCardRule``(`[`NFEModelMetadata`](../../../model/NFEModelMetadata.md)` modelMetadata, `[`NFEFeatureLayer`](../../../model/feature/NFEFeatureLayer.md)` featureLayer)`<br>Removes the point cardinality rule from the point cardinality rule table related to the specified feature layer.                                                                                                                                                                                                              |
    | `void`                                                                                                 | `saveCatalog``(`[`NFEModelMetadata`](../../../model/NFEModelMetadata.md)` modelMetadata, `[`NFECatalog`](../../../model/feature/NFECatalog.md)` catalog)`<br>Persists the catalog in the tables FT_USR_DATA_CATLG\_\[model_id\] and FT_USR_DATA_CVAL\_\[model_id\].                                                                                                                                                                                                                                               |
    | `void`                                                                                                 | `updateAttributeConstraints``(`[`NFEModelMetadata`](../../../model/NFEModelMetadata.md)` modelMetadata, java.lang.Long featureClassId, java.lang.String attributeName, java.lang.String newValue)`<br>Updates the attribute default value.                                                                                                                                                                                                                                                                        |
    | `void`                                                                                                 | `updateCatalogValues``(`[`NFEModelMetadata`](../../../model/NFEModelMetadata.md)` modelMetadata, long catalogId, java.util.Collection<`[`NFECatalogValue`](../../../model/feature/NFECatalogValue.md)`> catalogValues)`<br>Updates the catalog values of the specified catalog.                                                                                                                                                                                                                                   |
    | `void`                                                                                                 | `updateFeatureClass``(`[`NFEModel`](../../../model/NFEModel.md)` nfeModel, `[`NFEFeatureClass`](../../../model/feature/NFEFeatureClass.md)` featureClass, boolean addPredefinedConnectedPointInfo, boolean addAttributeConstraints)`<br>Updates the feature class.                                                                                                                                                                                                                                                |
    | `void`                                                                                                 | `updateFeatureLayerZOrder``(`[`NFEModelMetadata`](../../../model/NFEModelMetadata.md)` modelMetadata, `[`NFEFeatureLayer`](../../../model/feature/NFEFeatureLayer.md)` featLayer)`<br>Updates the feature layers Z-order.                                                                                                                                                                                                                                                                                         |

    - ### Methods inherited from class oracle.spatial.network.nfe.io.jdbc.dao.[AbstractDAO](AbstractDAO.md)

      [`getConnection`](AbstractDAO.md)`, `[`getModel`](AbstractDAO.md)`, `[`getSQLValidator`](AbstractDAO.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### ModelDAO

          public ModelDAO(java.sql.Connection conn,
                          NFEModel model)

      Creates a ModelDAO with the specified connection and model.
      Parameters:
      `conn` - connection

      `model` - model

  <!-- -->

  - ### Method Detail

    - #### modelExists

          public boolean modelExists(java.lang.String modelName)
                              throws NFEIOException

      Returns true if a model already exists with the specified name, false otherwise.
      Parameters:
      `modelName` - model name

      Returns:
      true if a model already exists with the specified name, false otherwise

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### createNewModelTables

          public NFEModelMetadata createNewModelTables(java.lang.String modelName,
                                                       NFEEditionMode editionMode,
                                                       boolean isVersionable)
                                                throws NFEIOException

      Creates the needed tables for a new model. See script `NFEResources#SQL_NFE_PACKAGE_BODY_SCRIPT_NAME` located in `NFEResources#SCRIPTS_PATH`.
      Parameters:
      `modelName` - model name

      `editionMode` - edition mode

      `isVersionable` - true if the model is versionable, false otherwise.

      Returns:
      model metadata

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteModelTables

          public void deleteModelTables(int modelId)
                                 throws NFEIOException

      Drops the model's tables and its registry in the Model-Metadata table.
      Parameters:
      `modelId` - Identifier of the model

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### relateNetworkToModel

          public void relateNetworkToModel(long modelId,
                                           java.lang.String networkName)
                                    throws NFEIOException

      Relates a network with an NFE Model. It is exclusively allowed to relate networks to models in this way for models created in the Over-An-Existing-Network mode.
      Parameters:
      `modelId` - Identifier of the model

      `networkName` - network name

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### fetchModelMetadata

          public NFEModelMetadata fetchModelMetadata(java.lang.String modelName)
                                              throws NFEIOException

      Retrieves the metadata for the model whose identifier is specified.
      Parameters:
      `modelName` - model name

      Returns:
      model metadata

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### loadSequencesRegistry

          public void loadSequencesRegistry(java.util.Collection<java.lang.String> tableNames,
                                            NFEModelMetadata modelMetadata)
                                     throws NFEIOException

      Loads the table sequences of the specified tables in the model metadata.
      Parameters:
      `tableNames` - table names

      `modelMetadata` - model metadata

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### createModelSequence

          public void createModelSequence(long modelId,
                                          java.lang.String ownerTable,
                                          java.lang.String sequenceName)
                                   throws NFEIOException

      Creates a sequence in database and a record in the model sequence table.
      Parameters:
      `modelId` - model identifier

      `ownerTable` - table for which the sequence was created

      `sequenceName` - sequence name

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### removeModelSequence

          public void removeModelSequence(long modelId,
                                          java.lang.String sequenceName)
                                   throws NFEIOException

      Removes a sequence in database and the corresponding record in the model sequence table.
      Parameters:
      `modelId` - model identifier

      `sequenceName` - sequence name

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### initializeTables

          public void initializeTables(NFEModelMetadata metadata)
                                throws NFEIOException

      Creates default values in decision handler rules tables.
      Parameters:
      `metadata` - model metadata

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteModel

          public void deleteModel(long modelId)
                           throws NFEIOException

      Deletes model structure. This function can only be used if the model has no feature layers defined nor rules.
      Parameters:
      `modelId` - model identifier

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### createFeatureLayer

          public long createFeatureLayer(NFEFeatureLayerMetadata featureLayerMetadata,
                                         java.util.Collection<NFEAttributeDescriptor> attributeDescriptors)
                                  throws NFEIOException

      Creates the feature layer tables and metadata.
      Parameters:
      `featureLayerMetadata` - feature layer metadata

      `attributeDescriptors` - attributes descriptors of the feature table

      Returns:
      feature layer identifier

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### registerFeatureLayerAttributes

          public java.util.Collection<NFEAttributeDescriptor> registerFeatureLayerAttributes(NFEModelMetadata modelMetadata,
                                                                                             NFEFeatureLayerMetadata featLayerMetadata,
                                                                                             java.util.Collection<NFEAttributeDescriptor> attributeDescriptors)
                                                                                      throws NFEIOException

      Registers the given attributes to the network and feature layer in xxx_sdo_network_data.
      Parameters:
      `modelMetadata` - model metadata

      `featLayerMetadata` - feature layer metadata

      `attributeDescriptors` - attribute descriptors

      Returns:
      the attributes which could be registered. If an attribute with the same name is already registered it is not included in the returned collection.

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### createFeatureClass

          public void createFeatureClass(NFEModelMetadata modelMetadata,
                                         NFEFeatureClass featClass,
                                         boolean addPredefinedConnectedPointInfo,
                                         boolean addAttributeConstraints)
                                  throws NFEIOException

      Persists a feature class.
      Parameters:
      `modelMetadata` - model metadata

      `featClass` - feature class

      `addPredefinedConnectedPointInfo` - true if the predefined connected points should be added, false otherwise

      `addAttributeConstraints` - true if the attribute constraints should be added, false otherwise

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### removePointCardRule

          public void removePointCardRule(NFEModelMetadata modelMetadata,
                                          NFEFeatureClass featClass)
                                   throws NFEIOException

      Removes the point cardinality rule from the point cardinality rule table related to the specified feature class.
      Parameters:
      `modelMetadata` - model metadata

      `featClass` - feature class

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### removePointCardRule

          public void removePointCardRule(NFEModelMetadata modelMetadata,
                                          NFEFeatureLayer featureLayer)
                                   throws NFEIOException

      Removes the point cardinality rule from the point cardinality rule table related to the specified feature layer.
      Parameters:
      `modelMetadata` - model metadata

      `featureLayer` - feature layer

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### addFeatureLayerToModel

          public void addFeatureLayerToModel(NFEFeatureLayer featureLayer,
                                             NFEModelMetadata modelMetadata,
                                             boolean isPath)
                                      throws NFEIOException

      Adds the feature layer record to the table USER_SDO_NFE_MODEL_FTLAYER_REL.
      Parameters:
      `featureLayer` - feature layer

      `modelMetadata` - model metadata

      `isPath` - true if the feature layer is a path feature layer, false otherwise

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### dropFeatureTable

          public void dropFeatureTable(java.lang.String featureTableName)
                                throws NFEIOException

      Drops the feature table with the specified name.
      Parameters:
      `featureTableName` - feature table name

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### fetchModelIdentificators

          public java.util.HashMap<java.lang.Long,java.lang.String> fetchModelIdentificators()
                                                                                      throws NFEIOException

      Returns a map containing the identifiers and names of all the existing models.
      Returns:
      map with the identifiers (key) and names (value) of all the existing models.

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteFeatureLayer

          public void deleteFeatureLayer(NFEFeatureLayerMetadata featureLayerMetadata)
                                  throws NFEIOException

      Drops (deletes) a feature layer using the database procedure sdo_net.drop_feature_layer.
      Parameters:
      `featureLayerMetadata` - feature layer metadata

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### addAttributesToFeatureTable

          public void addAttributesToFeatureTable(NFEFeatureLayerMetadata featLayerMetadata,
                                                  java.util.Collection<NFEAttributeDescriptor> attributeDescriptors)
                                           throws NFEIOException

      Adds the specified attributes to the feature table.
      Parameters:
      `featLayerMetadata` - feature layer metadata

      `attributeDescriptors` - attribute descriptors

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### updateFeatureClass

          public void updateFeatureClass(NFEModel nfeModel,
                                         NFEFeatureClass featureClass,
                                         boolean addPredefinedConnectedPointInfo,
                                         boolean addAttributeConstraints)
                                  throws NFEIOException

      Updates the feature class. Updates the name, shape, cardinality rules, style, predefined points and attribute constraints.
      Parameters:
      `nfeModel` - model

      `featureClass` - feature class

      `addPredefinedConnectedPointInfo` - true if the predefined connected points should be updated, false otherwise

      `addAttributeConstraints` - true if the attribute constraints should be updated, false otherwise

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### dropAttributesFromFeatureTable

          public void dropAttributesFromFeatureTable(NFEFeatureLayerMetadata featLayerMetadata,
                                                     java.util.Collection<NFEAttributeDescriptor> attributeDescriptors)
                                              throws NFEIOException

      Drops the specified attributes columns from the feature table.
      Parameters:
      `featLayerMetadata` - feature layer metadata

      `attributeDescriptors` - attribute descriptors

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### updateFeatureLayerZOrder

          public void updateFeatureLayerZOrder(NFEModelMetadata modelMetadata,
                                               NFEFeatureLayer featLayer)
                                        throws NFEIOException

      Updates the feature layers Z-order. The Z-order determines which feature layer appears on top of the other.
      Parameters:
      `modelMetadata` - model metadata

      `featLayer` - feature layers to update

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteFeatureClassHierarchyRelationship

          public void deleteFeatureClassHierarchyRelationship(NFEModelMetadata nfeModelMetadata,
                                                              NFEFeatureClass featureClass,
                                                              java.util.Collection<NFEFeatureLayerMetadata> featureLayersMetadata)
                                                       throws NFEIOException

      Deletes any relation of the class with the hierarchy table (parent or child)
      Parameters:
      `nfeModelMetadata` - model metadata

      `featureClass` - feature class

      `featureLayersMetadata` - The metadata of the featurelayers that could have any feature of the feature class as parent.

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteFeatureClassRel

          public void deleteFeatureClassRel(NFEModelMetadata nfeModelMetadata,
                                            NFEFeatureClass nfeFeatureClass)
                                     throws NFEIOException

      Deletes the records from the table FT_CLASS_REL\_\[model_id\] related to the specified feature class.
      Parameters:
      `nfeModelMetadata` - model metadata

      `nfeFeatureClass` - feature class

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### dropAttributeFromFeatureTable

          public void dropAttributeFromFeatureTable(NFEFeatureLayerMetadata featLayerMetadata,
                                                    NFEAttributeDescriptor attrDescriptor)
                                             throws NFEIOException

      Drops the attribute column from the feature table.
      Parameters:
      `featLayerMetadata` - feature layer metadata

      `attrDescriptor` - attribute to drop

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteFeatureClass

          public void deleteFeatureClass(NFEModelMetadata nfeModelMetadata,
                                         NFEFeatureClass nfeFeatureClass)
                                  throws NFEIOException

      Deletes the feature class record from the FT_CLASS\_\[model_id\] table related to the specified feature class and delete the related connected points and attribute constraints information from tables FT_CLASS_DEF_CON_PT\_\[model_id\] and FT_CLASS_ATTR_CSTR\_\[model_id\].
      Parameters:
      `nfeModelMetadata` - model metadata

      `nfeFeatureClass` - feature class

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteFeatureClassesAttributesConstraints

          public void deleteFeatureClassesAttributesConstraints(NFEModelMetadata modelMetadata,
                                                                java.util.Collection<NFEFeatureClass> featureClasses)
                                                         throws NFEIOException

      Deletes all the attributes constraints related to the specified feature classes in the FT_CLASS_ATTR_CSTR\_\[model_id\] table.
      Parameters:
      `modelMetadata` - model metadata

      `featureClasses` - feature classes

      Throws:
      `java.sql.SQLException` - if an SQL exception is thrown.

      [`NFEIOException`](../../NFEIOException.md)

    <!-- -->

    - #### deleteFeatureLayerAttributes

          public void deleteFeatureLayerAttributes(NFEModelMetadata nfeModelMetadata,
                                                   NFEFeatureLayer nfeFeatureLayer,
                                                   java.util.Collection<NFEAttributeDescriptor> attributeDescriptors)
                                            throws NFEIOException

      Deletes the attributes for the specified feature layer from the user_sdo_network_user_data view and from the FT_CLASS_ATTR_CSTR\_\[model_id\] and FT_USR_DATA\_\[model_id\] tables.
      Parameters:
      `nfeModelMetadata` - model metadata

      `nfeFeatureLayer` - feature layer

      `attributeDescriptors` - attribute descriptors

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteFeatureClasses

          public void deleteFeatureClasses(NFEModelMetadata nfeModelMetadata,
                                           NFEFeatureLayer nfeFeatureLayer)
                                    throws NFEIOException

      Deletes the feature classes records from the FT_CLASS\_\[model_id\] table related to the specified feature layer and delete the related connected points and attribute constraints information from tables FT_CLASS_DEF_CON_PT\_\[model_id\] and FT_CLASS_ATTR_CSTR\_\[model_id\].
      Parameters:
      `nfeModelMetadata` - model metadata

      `nfeFeatureLayer` - feature layer

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteFeatureLayerToProject

          public void deleteFeatureLayerToProject(NFEFeatureLayer featureLayer,
                                                  NFEModelMetadata nfeModelMetadata)
                                           throws NFEIOException

      Deletes the feature layer record from the table USER_SDO_NFE_MODEL_FTLAYER_REL.
      Parameters:
      `featureLayer` - feature layer

      `nfeModelMetadata` - model metadata

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteFeatureClassRel

          public void deleteFeatureClassRel(NFEModelMetadata nfeModelMetadata,
                                            NFEFeatureLayer nfeFeatureLayer)
                                     throws NFEIOException

      Deletes the records from the table FT_CLASS_REL\_\[model_id\] related to the specified feature classes.
      Parameters:
      `nfeModelMetadata` - model metadata

      `nfeFeatureLayer` - feature layer

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### saveCatalog

          public void saveCatalog(NFEModelMetadata modelMetadata,
                                  NFECatalog catalog)
                           throws NFEIOException

      Persists the catalog in the tables FT_USR_DATA_CATLG\_\[model_id\] and FT_USR_DATA_CVAL\_\[model_id\].
      Parameters:
      `modelMetadata` - model metadata

      `catalog` - catalog

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### hasRelatedRules

          public boolean hasRelatedRules(NFEFeatureClass featureClass)
                                  throws NFEIOException

      Returns true if the feature class is used in any NFE rule, false otherwise.
      Parameters:
      `featureClass` - feature class

      Returns:
      true if the feature class is used in any NFE rule, false otherwise

      Throws:
      `java.sql.SQLException` - if an SQL exception is thrown.

      [`NFEIOException`](../../NFEIOException.md)

    <!-- -->

    - #### hasRelatedRules

          public boolean hasRelatedRules(NFEFeatureLayer featureLayer)
                                  throws NFEIOException

      Returns true if the feature layer is used in any NFE rule, false otherwise.
      Parameters:
      `featureLayer` - feature layer

      Returns:
      true if the feature layer is used in any NFE rule, false otherwise

      Throws:
      `java.sql.SQLException` - if an SQL exception is thrown.

      [`NFEIOException`](../../NFEIOException.md)

    <!-- -->

    - #### isFeatureTableEmpty

          public boolean isFeatureTableEmpty(NFEFeatureClass featureClass)
                                      throws NFEIOException

      Returns true if no features belong to the feature class, false otherwise.
      Parameters:
      `featureClass` - feature class

      Returns:
      true if no features belong to the feature class, false otherwise

      Throws:
      `java.sql.SQLException` - if an SQL exception is thrown.

      [`NFEIOException`](../../NFEIOException.md)

    <!-- -->

    - #### isFeatureTableEmpty

          public boolean isFeatureTableEmpty(NFEFeatureLayer featureLayer)
                                      throws NFEIOException

      Returns true if no features belong to the feature layer, false otherwise.
      Parameters:
      `featureLayer` - feature layer

      Returns:
      true if no features belong to the feature layer, false otherwise

      Throws:
      `java.sql.SQLException` - if an SQL exception is thrown.

      [`NFEIOException`](../../NFEIOException.md)

    <!-- -->

    - #### getCatalogs

          public java.util.List<NFECatalog> getCatalogs(NFEModel nfeModel)
                                                 throws NFEIOException

      Returns all the catalogs related to the specified model.
      Parameters:
      `nfeModel` - model

      Returns:
      all the catalogs related to the specified model

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### updateCatalogValues

          public void updateCatalogValues(NFEModelMetadata modelMetadata,
                                          long catalogId,
                                          java.util.Collection<NFECatalogValue> catalogValues)
                                   throws NFEIOException,
                                          java.sql.SQLException

      Updates the catalog values of the specified catalog.
      Parameters:
      `modelMetadata` - model metadata

      `catalogId` - catalog identifier

      `catalogValues` - new catalog values

      Throws:
      `java.sql.SQLException` - if an SQL exception is thrown.

      [`NFEIOException`](../../NFEIOException.md)

    <!-- -->

    - #### fetchFeatLayersAttributesUsingCatalog

          public java.util.Map<java.lang.Long,java.util.Collection<java.lang.String>> fetchFeatLayersAttributesUsingCatalog(NFEModelMetadata modelMetadata,
                                                                                                                            long catalogId)
                                                                                                                     throws NFEIOException

      Returns a map with as key the feature layer identifiers and as values the list of the attributes using the specified catalog.
      Parameters:
      `modelMetadata` - model metadata

      `catalogId` - catalog identifier

      Returns:
      map with as key the feature layer identifiers and as values the list of the attributes using the catalog

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteCatalog

          public void deleteCatalog(NFEModelMetadata modelMetadata,
                                    java.lang.Long catalogId)
                             throws NFEIOException

      Deletes the specified catalog.
      Parameters:
      `modelMetadata` - model metadata

      `catalogId` - catalog identifier

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### updateAttributeConstraints

          public void updateAttributeConstraints(NFEModelMetadata modelMetadata,
                                                 java.lang.Long featureClassId,
                                                 java.lang.String attributeName,
                                                 java.lang.String newValue)
                                          throws NFEIOException

      Updates the attribute default value.
      Parameters:
      `modelMetadata` - model metadata

      `featureClassId` - feature class identifier

      `attributeName` - attribute name

      `newValue` - new attribute default value

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### fetchModelFeatureLayersRelations

          public java.util.Collection<ModelDAO.ModelFeatLayerRelation> fetchModelFeatureLayersRelations(NFEModelMetadata modelMetadata,
                                                                                                        boolean path)
                                                                                                 throws NFEIOException

      Returns the feature layers information related to the specified model. This information is loaded from the table USER_SDO_NFE_MODEL_FTLAYER_REL.
      Parameters:
      `modelMetadata` - model metadata

      `path` - true if the information to load belongs to the path feature layer, false otherwise

      Returns:
      the feature feature layers information related to the specified model

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

- [Prev Class](FeatureDAO.md)
- [Next Class](ModelDAO.ModelFeatLayerRelation.md)

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
