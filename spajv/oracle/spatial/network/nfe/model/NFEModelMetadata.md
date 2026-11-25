Skip navigation links

- [Overview](../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFEModel.md)
- [Next Class](NFEModelObject.md)

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.model

## Class NFEModelMetadata

- java.lang.Object

- - [oracle.spatial.network.nfe.model.NFEMetadata](NFEMetadata.md)

  - - oracle.spatial.network.nfe.model.NFEModelMetadata

<!-- -->

-

  ------------------------------------------------------------------------



      public class NFEModelMetadata
      extends NFEMetadata

  This class holds metadata for an NFE model.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                                                                                         |
    |---------------------------|---------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String` | `MODEL_FEAT_LAYER_REL_TAB`<br>Model and feature layers relation table.                                        |
    | `static java.lang.String` | `MODEL_METADATA_TAB`<br>Model metadata table.                                                                 |
    | `static java.lang.String` | `MODEL_WORKSPACE_TAB`<br>Model workspace table.                                                               |
    | `static java.lang.String` | `TTYPE_FEAT_CLASS`<br>Table type FT_CLASS contained in table TABLE_REGISTRY\_{modelId}.                       |
    | `static java.lang.String` | `TTYPE_FEAT_CLASS_ATTR_CON`<br>Table type FT_CLASS_ATTR_CSTR contained in table TABLE_REGISTRY\_{modelId}.    |
    | `static java.lang.String` | `TTYPE_FEAT_CLASS_DEF_CON_PT`<br>Table type FT_CLASS_DEF_CON_PT contained in table TABLE_REGISTRY\_{modelId}. |
    | `static java.lang.String` | `TTYPE_FEAT_CLASS_REL`<br>Table type FT_CLASS_REL contained in table TABLE_REGISTRY\_{modelId}.               |
    | `static java.lang.String` | `TTYPE_FEAT_USER_DATA`<br>Table type FT_USR_DATA contained in table TABLE_REGISTRY\_{modelId}.                |
    | `static java.lang.String` | `TTYPE_FEAT_USER_DATA_CAT`<br>Table type FT_USR_DATA_CATLG contained in table TABLE_REGISTRY\_{modelId}.      |
    | `static java.lang.String` | `TTYPE_FEAT_USER_DATA_CVALUE`<br>Table type FT_USR_DATA_CVAL contained in table TABLE_REGISTRY\_{modelId}.    |
    | `static java.lang.String` | `TTYPE_FT_RULE_REL`<br>Table type FT_RULE_REL contained in table TABLE_REGISTRY\_{modelId}.                   |
    | `static java.lang.String` | `TTYPE_LINE_LINE_RULE`<br>Table type LINE_LINE_RULE contained in table TABLE_REGISTRY\_{modelId}.             |
    | `static java.lang.String` | `TTYPE_LINE_POINT_RULE`<br>Table type LINE_POINT_RULE contained in table TABLE_REGISTRY\_{modelId}.           |
    | `static java.lang.String` | `TTYPE_POINT_ATTR_DEF`<br>Table type POINT_ATTR_DEF contained in table TABLE_REGISTRY\_{modelId}.             |
    | `static java.lang.String` | `TTYPE_POINT_CARD_RULE`<br>Table type POINT_CARD_RULE contained in table TABLE_REGISTRY\_{modelId}.           |
    | `static java.lang.String` | `TTYPE_RULE_DEC_HANDLER`<br>Table type RULE_DEC_HANDLER contained in table TABLE_REGISTRY\_{modelId}.         |
    | `static java.lang.String` | `TTYPE_RULE_INSTANCE`<br>Table type RULE_INSTANCE contained in table TABLE_REGISTRY\_{modelId}.               |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `NFEModelMetadata``()`      |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                         | Method and Description                                                                                                                                   |
    |-------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                                                                 | `addFeatureLayerMetadata``(`[`NFEFeatureLayerMetadata`](feature/NFEFeatureLayerMetadata.md)` featLayerMetadata)`<br>Adds feature layer metadata.         |
    | [`NFEEditionMode`](NFEEditionMode.md)                                                     | `getEditionMode``()`<br>Returns edition mode.                                                                                                            |
    | `java.lang.String`                                                                        | `getFeatClassAttributesConstraintsTable``()`<br>Returns the feature class attributes constraints table.                                                  |
    | `java.lang.String`                                                                        | `getFeatClassDefaultConnectedPointTable``()`<br>Returns the default connected points table.                                                              |
    | `java.lang.String`                                                                        | `getFeatClassRelationTable``()`<br>Returns the feature class relation table.                                                                             |
    | `java.lang.String`                                                                        | `getFeatClassTable``()`<br>Returns feature class table.                                                                                                  |
    | `java.lang.String`                                                                        | `getFeatRulesRelTable``()`<br>Returns the table that keeps the relationship between features and rules.                                                  |
    | `java.util.Collection<`[`NFEFeatureLayerMetadata`](feature/NFEFeatureLayerMetadata.md)`>` | `getFeatureLayersMetadata``()`<br>Returns the feature layers metadata.                                                                                   |
    | `java.lang.String`                                                                        | `getFeatUserDataCatalogTable``()`<br>Returns the catalog table.                                                                                          |
    | `java.lang.String`                                                                        | `getFeatUserDataCatalogValueTable``()`<br>Returns the catalogs values table.                                                                             |
    | `java.lang.String`                                                                        | `getFeatUserDataTable``()`<br>Returns the feature user data table.                                                                                       |
    | [`NFEGeometryDescriptor`](NFEGeometryDescriptor.md)                                       | `getGeometryDescriptor``()`<br>Returns the geometry descriptor.                                                                                          |
    | `long`                                                                                    | `getId``()`<br>Returns model identifier.                                                                                                                 |
    | `java.lang.String`                                                                        | `getLineLineRuleTable``()`<br>Returns the line-line rules table.                                                                                         |
    | `java.lang.String`                                                                        | `getLinePointRuleTable``()`<br>Returns the line-point rules table.                                                                                       |
    | `java.lang.String`                                                                        | `getName``()`<br>Returns name.                                                                                                                           |
    | [`NFENetworkMetadata`](network/NFENetworkMetadata.md)                                     | `getNetworkMetadata``()`<br>Returns the network metadata.                                                                                                |
    | `java.lang.String`                                                                        | `getNetworkName``()`<br>Returns network name.                                                                                                            |
    | `java.lang.String`                                                                        | `getPointAttrDefTable``()`<br>Returns the default point attributes table.                                                                                |
    | `java.lang.String`                                                                        | `getPointCardRuleTable``()`<br>Returns the cardinality rules table.                                                                                      |
    | `java.lang.String`                                                                        | `getRuleDecHandlerTable``()`<br>Returns the rule decision handlers table.                                                                                |
    | `java.lang.String`                                                                        | `getRuleInstanceTable``()`<br>Returns the rule instance table.                                                                                           |
    | `java.lang.String`                                                                        | `getSeqRegistryTable``()`<br>Returns the table that keep the sequences names related to the model.                                                       |
    | `java.lang.String`                                                                        | `getTabRegistryTable``()`<br>Returns the table that keeps the model table names.                                                                         |
    | `boolean`                                                                                 | `isVersionable``()`<br>Returns true if the model is versionable, false otherwise.                                                                        |
    | `void`                                                                                    | `setEditionMode``(`[`NFEEditionMode`](NFEEditionMode.md)` editionMode)`<br>Sets edition mode.                                                            |
    | `void`                                                                                    | `setFeatClassAttributesConstraintsTable``(java.lang.String featClassAttributesConstraintsTable)`<br>Sets the feature class attributes constraints table. |
    | `void`                                                                                    | `setFeatClassDefaultConnectedPointTable``(java.lang.String featClassDefaultConnectedPointTable)`<br>Sets the default connected points table.             |
    | `void`                                                                                    | `setFeatClassRelationTable``(java.lang.String featClassRelationTable)`<br>Sets the feature class relation table.                                         |
    | `void`                                                                                    | `setFeatClassTable``(java.lang.String featClassTable)`<br>Sets feature class table.                                                                      |
    | `void`                                                                                    | `setFeatRulesRelTable``(java.lang.String featRulesRelTable)`<br>Sets the table that keeps the relationship between features and rules.                   |
    | `void`                                                                                    | `setFeatUserDataCatalogTable``(java.lang.String featUserDataCatalogTable)`<br>Sets the catalog table.                                                    |
    | `void`                                                                                    | `setFeatUserDataCatalogValueTable``(java.lang.String featUserDataCatalogValueTable)`<br>Sets the catalogs values table.                                  |
    | `void`                                                                                    | `setFeatUserDataTable``(java.lang.String featUserDataTable)`<br>Sets the feature user data table.                                                        |
    | `void`                                                                                    | `setGeometryDescriptor``(`[`NFEGeometryDescriptor`](NFEGeometryDescriptor.md)` geometryDescriptor)`<br>Sets the geometry descriptor.                     |
    | `void`                                                                                    | `setId``(long id)`<br>Sets model identifier.                                                                                                             |
    | `void`                                                                                    | `setLineLineRuleTable``(java.lang.String lineLineRuleTable)`<br>Sets the line-line rules table.                                                          |
    | `void`                                                                                    | `setLinePointRuleTable``(java.lang.String linePointRuleTable)`<br>Sets the line-point rules table.                                                       |
    | `void`                                                                                    | `setName``(java.lang.String name)`<br>Sets name.                                                                                                         |
    | `void`                                                                                    | `setNetworkMetadata``(`[`NFENetworkMetadata`](network/NFENetworkMetadata.md)` networkMetadata)`<br>Sets the network metadata.                            |
    | `void`                                                                                    | `setNetworkName``(java.lang.String networkName)`<br>Sets network name.                                                                                   |
    | `void`                                                                                    | `setPointAttrDefTable``(java.lang.String pointAttrDefTable)`<br>Sets the default point attributes table.                                                 |
    | `void`                                                                                    | `setPointCardRuleTable``(java.lang.String pointCardRuleTable)`<br>Sets the cardinality rules table.                                                      |
    | `void`                                                                                    | `setRuleDecHandlerTable``(java.lang.String ruleDecHandlerTable)`<br>Sets the rule decision handlers table.                                               |
    | `void`                                                                                    | `setRuleInstanceTable``(java.lang.String ruleInstanceTable)`<br>Sets the rule instance table.                                                            |
    | `void`                                                                                    | `setSeqRegistryTable``(java.lang.String seqRegistryTable)`<br>Sets the table that keep the sequences names related to the model.                         |
    | `void`                                                                                    | `setTabRegistryTable``(java.lang.String tabRegistryTable)`<br>Sets the table that keeps the model table names.                                           |
    | `void`                                                                                    | `setVersionable``(boolean isVersionable)`<br>Sets true if the model is versionable, false otherwise.                                                     |

    - ### Methods inherited from class oracle.spatial.network.nfe.model.[NFEMetadata](NFEMetadata.md)

      [`getTableSequence`](NFEMetadata.md)`, `[`getTablesWithSequence`](NFEMetadata.md)`, `[`hasSequence`](NFEMetadata.md)`, `[`setTableSequence`](NFEMetadata.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### MODEL_METADATA_TAB

          public static final java.lang.String MODEL_METADATA_TAB

      Model metadata table.
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### MODEL_WORKSPACE_TAB

          public static final java.lang.String MODEL_WORKSPACE_TAB

      Model workspace table.
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### MODEL_FEAT_LAYER_REL_TAB

          public static final java.lang.String MODEL_FEAT_LAYER_REL_TAB

      Model and feature layers relation table.
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### TTYPE_FEAT_CLASS

          public static final java.lang.String TTYPE_FEAT_CLASS

      Table type FT_CLASS contained in table TABLE_REGISTRY\_{modelId}.
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### TTYPE_FEAT_CLASS_DEF_CON_PT

          public static final java.lang.String TTYPE_FEAT_CLASS_DEF_CON_PT

      Table type FT_CLASS_DEF_CON_PT contained in table TABLE_REGISTRY\_{modelId}.
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### TTYPE_FEAT_CLASS_REL

          public static final java.lang.String TTYPE_FEAT_CLASS_REL

      Table type FT_CLASS_REL contained in table TABLE_REGISTRY\_{modelId}.
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### TTYPE_FEAT_CLASS_ATTR_CON

          public static final java.lang.String TTYPE_FEAT_CLASS_ATTR_CON

      Table type FT_CLASS_ATTR_CSTR contained in table TABLE_REGISTRY\_{modelId}.
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### TTYPE_FEAT_USER_DATA

          public static final java.lang.String TTYPE_FEAT_USER_DATA

      Table type FT_USR_DATA contained in table TABLE_REGISTRY\_{modelId}.
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### TTYPE_FEAT_USER_DATA_CAT

          public static final java.lang.String TTYPE_FEAT_USER_DATA_CAT

      Table type FT_USR_DATA_CATLG contained in table TABLE_REGISTRY\_{modelId}.
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### TTYPE_FEAT_USER_DATA_CVALUE

          public static final java.lang.String TTYPE_FEAT_USER_DATA_CVALUE

      Table type FT_USR_DATA_CVAL contained in table TABLE_REGISTRY\_{modelId}.
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### TTYPE_LINE_LINE_RULE

          public static final java.lang.String TTYPE_LINE_LINE_RULE

      Table type LINE_LINE_RULE contained in table TABLE_REGISTRY\_{modelId}.
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### TTYPE_LINE_POINT_RULE

          public static final java.lang.String TTYPE_LINE_POINT_RULE

      Table type LINE_POINT_RULE contained in table TABLE_REGISTRY\_{modelId}.
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### TTYPE_RULE_INSTANCE

          public static final java.lang.String TTYPE_RULE_INSTANCE

      Table type RULE_INSTANCE contained in table TABLE_REGISTRY\_{modelId}.
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### TTYPE_FT_RULE_REL

          public static final java.lang.String TTYPE_FT_RULE_REL

      Table type FT_RULE_REL contained in table TABLE_REGISTRY\_{modelId}.
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### TTYPE_RULE_DEC_HANDLER

          public static final java.lang.String TTYPE_RULE_DEC_HANDLER

      Table type RULE_DEC_HANDLER contained in table TABLE_REGISTRY\_{modelId}.
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### TTYPE_POINT_CARD_RULE

          public static final java.lang.String TTYPE_POINT_CARD_RULE

      Table type POINT_CARD_RULE contained in table TABLE_REGISTRY\_{modelId}.
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

    <!-- -->

    - #### TTYPE_POINT_ATTR_DEF

          public static final java.lang.String TTYPE_POINT_ATTR_DEF

      Table type POINT_ATTR_DEF contained in table TABLE_REGISTRY\_{modelId}.
      See Also:
      [Constant Field Values](../../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### NFEModelMetadata

          public NFEModelMetadata()

  <!-- -->

  - ### Method Detail

    - #### getNetworkMetadata

          public NFENetworkMetadata getNetworkMetadata()

      Returns the network metadata.
      Returns:
      network metadata

    <!-- -->

    - #### setNetworkMetadata

          public void setNetworkMetadata(NFENetworkMetadata networkMetadata)

      Sets the network metadata.
      Parameters:
      `networkMetadata` - network metadata

    <!-- -->

    - #### addFeatureLayerMetadata

          public boolean addFeatureLayerMetadata(NFEFeatureLayerMetadata featLayerMetadata)

      Adds feature layer metadata.
      Parameters:

      `featLayerMetadata` - feature layer metadata to add

      Returns:

    <!-- -->

    - #### getFeatureLayersMetadata

          public java.util.Collection<NFEFeatureLayerMetadata> getFeatureLayersMetadata()

      Returns the feature layers metadata.
      Returns:
      feature layers metadata.

    <!-- -->

    - #### getId

          public long getId()

      Returns model identifier.
      Returns:
      model identifier

    <!-- -->

    - #### setId

          public void setId(long id)

      Sets model identifier.
      Parameters:
      `id` - model identifier

    <!-- -->

    - #### getName

          public java.lang.String getName()

      Returns name.
      Returns:
      name

    <!-- -->

    - #### setName

          public void setName(java.lang.String name)

      Sets name.
      Parameters:
      `name` - name

    <!-- -->

    - #### isVersionable

          public boolean isVersionable()

      Returns true if the model is versionable, false otherwise.
      Returns:
      true if the model is versionable, false otherwise

    <!-- -->

    - #### setVersionable

          public void setVersionable(boolean isVersionable)

      Sets true if the model is versionable, false otherwise.
      Parameters:
      `isVersionable` - true if the model is versionable, false otherwise

    <!-- -->

    - #### getEditionMode

          public NFEEditionMode getEditionMode()

      Returns edition mode.
      Returns:
      edition mode

    <!-- -->

    - #### setEditionMode

          public void setEditionMode(NFEEditionMode editionMode)

      Sets edition mode.
      Parameters:
      `editionMode` - edition mode

    <!-- -->

    - #### getFeatClassTable

          public java.lang.String getFeatClassTable()

      Returns feature class table.
      Returns:
      feature class table

    <!-- -->

    - #### setFeatClassTable

          public void setFeatClassTable(java.lang.String featClassTable)

      Sets feature class table.
      Parameters:
      `featClassTable` - feature class table

    <!-- -->

    - #### getPointAttrDefTable

          public java.lang.String getPointAttrDefTable()

      Returns the default point attributes table.
      Returns:
      default point attributes table

    <!-- -->

    - #### setPointAttrDefTable

          public void setPointAttrDefTable(java.lang.String pointAttrDefTable)

      Sets the default point attributes table.
      Parameters:
      `pointAttrDefTable` - default point attributes table

    <!-- -->

    - #### getFeatClassRelationTable

          public java.lang.String getFeatClassRelationTable()

      Returns the feature class relation table.
      Returns:
      feature class relation table

    <!-- -->

    - #### setFeatClassRelationTable

          public void setFeatClassRelationTable(java.lang.String featClassRelationTable)

      Sets the feature class relation table.
      Parameters:
      `featClassRelationTable` - the feature class relation table

    <!-- -->

    - #### getFeatClassAttributesConstraintsTable

          public java.lang.String getFeatClassAttributesConstraintsTable()

      Returns the feature class attributes constraints table.
      Returns:
      feature class attributes constraints table

    <!-- -->

    - #### setFeatClassAttributesConstraintsTable

          public void setFeatClassAttributesConstraintsTable(java.lang.String featClassAttributesConstraintsTable)

      Sets the feature class attributes constraints table.
      Parameters:
      `featClassAttributesConstraintsTable` - feature class attributes constraints table

    <!-- -->

    - #### getFeatUserDataTable

          public java.lang.String getFeatUserDataTable()

      Returns the feature user data table. This table keeps the feature class attributes from catalog type.
      Returns:
      feature user data table

    <!-- -->

    - #### setFeatUserDataTable

          public void setFeatUserDataTable(java.lang.String featUserDataTable)

      Sets the feature user data table. This table keeps the feature class attributes from catalog type.
      Parameters:
      `featUserDataTable` - feature user data table

    <!-- -->

    - #### getFeatUserDataCatalogTable

          public java.lang.String getFeatUserDataCatalogTable()

      Returns the catalog table.
      Returns:
      catalog table

    <!-- -->

    - #### setFeatUserDataCatalogTable

          public void setFeatUserDataCatalogTable(java.lang.String featUserDataCatalogTable)

      Sets the catalog table.
      Parameters:
      `featUserDataCatalogTable` - catalog table

    <!-- -->

    - #### getFeatUserDataCatalogValueTable

          public java.lang.String getFeatUserDataCatalogValueTable()

      Returns the catalogs values table.
      Returns:
      catalogs values table

    <!-- -->

    - #### setFeatUserDataCatalogValueTable

          public void setFeatUserDataCatalogValueTable(java.lang.String featUserDataCatalogValueTable)

      Sets the catalogs values table.
      Parameters:
      `featUserDataCatalogValueTable` - catalogs values table

    <!-- -->

    - #### getFeatClassDefaultConnectedPointTable

          public java.lang.String getFeatClassDefaultConnectedPointTable()

      Returns the default connected points table.
      Returns:
      default connected points table

    <!-- -->

    - #### setFeatClassDefaultConnectedPointTable

          public void setFeatClassDefaultConnectedPointTable(java.lang.String featClassDefaultConnectedPointTable)

      Sets the default connected points table.
      Parameters:
      `featClassDefaultConnectedPointTable` - default connected points table

    <!-- -->

    - #### getGeometryDescriptor

          public NFEGeometryDescriptor getGeometryDescriptor()

      Returns the geometry descriptor.
      Returns:
      geometry descriptor

    <!-- -->

    - #### setGeometryDescriptor

          public void setGeometryDescriptor(NFEGeometryDescriptor geometryDescriptor)

      Sets the geometry descriptor.
      Parameters:
      `geometryDescriptor` - geometry descriptor

    <!-- -->

    - #### getTabRegistryTable

          public java.lang.String getTabRegistryTable()

      Returns the table that keeps the model table names.
      Returns:
      table that keeps the model table names

    <!-- -->

    - #### setTabRegistryTable

          public void setTabRegistryTable(java.lang.String tabRegistryTable)

      Sets the table that keeps the model table names.
      Parameters:
      `tabRegistryTable` - table that keeps the model table names

    <!-- -->

    - #### getSeqRegistryTable

          public java.lang.String getSeqRegistryTable()

      Returns the table that keep the sequences names related to the model.
      Returns:
      table that keep the sequences names related to the model

    <!-- -->

    - #### setSeqRegistryTable

          public void setSeqRegistryTable(java.lang.String seqRegistryTable)

      Sets the table that keep the sequences names related to the model.
      Parameters:
      `seqRegistryTable` - table that keep the sequences names related to the model

    <!-- -->

    - #### getNetworkName

          public java.lang.String getNetworkName()

      Returns network name.
      Returns:
      network name

    <!-- -->

    - #### setNetworkName

          public void setNetworkName(java.lang.String networkName)

      Sets network name.
      Parameters:
      `networkName` - network name

    <!-- -->

    - #### getFeatRulesRelTable

          public java.lang.String getFeatRulesRelTable()

      Returns the table that keeps the relationship between features and rules.
      Returns:
      table that keeps the relationship between features and rules

    <!-- -->

    - #### getLineLineRuleTable

          public java.lang.String getLineLineRuleTable()

      Returns the line-line rules table.
      Returns:
      line-line rules table

    <!-- -->

    - #### setLineLineRuleTable

          public void setLineLineRuleTable(java.lang.String lineLineRuleTable)

      Sets the line-line rules table.
      Parameters:
      `lineLineRuleTable` - line-line rules table

    <!-- -->

    - #### setFeatRulesRelTable

          public void setFeatRulesRelTable(java.lang.String featRulesRelTable)

      Sets the table that keeps the relationship between features and rules.
      Parameters:
      `featRulesRelTable` - table that keeps the relationship between features and rules

    <!-- -->

    - #### getLinePointRuleTable

          public java.lang.String getLinePointRuleTable()

      Returns the line-point rules table.
      Returns:
      line-point rules table

    <!-- -->

    - #### setLinePointRuleTable

          public void setLinePointRuleTable(java.lang.String linePointRuleTable)

      Sets the line-point rules table.
      Parameters:
      `linePointRuleTable` - line-point rules table

    <!-- -->

    - #### getRuleInstanceTable

          public java.lang.String getRuleInstanceTable()

      Returns the rule instance table.
      Returns:
      rule instance table

    <!-- -->

    - #### setRuleInstanceTable

          public void setRuleInstanceTable(java.lang.String ruleInstanceTable)

      Sets the rule instance table.
      Parameters:
      `ruleInstanceTable` - rule instance table

    <!-- -->

    - #### getRuleDecHandlerTable

          public java.lang.String getRuleDecHandlerTable()

      Returns the rule decision handlers table.
      Returns:
      rule decision handlers table

    <!-- -->

    - #### setRuleDecHandlerTable

          public void setRuleDecHandlerTable(java.lang.String ruleDecHandlerTable)

      Sets the rule decision handlers table.
      Parameters:
      `ruleDecHandlerTable` - rule decision handlers table

    <!-- -->

    - #### getPointCardRuleTable

          public java.lang.String getPointCardRuleTable()

      Returns the cardinality rules table.
      Returns:
      cardinality rules table

    <!-- -->

    - #### setPointCardRuleTable

          public void setPointCardRuleTable(java.lang.String pointCardRuleTable)

      Sets the cardinality rules table.
      Parameters:
      `pointCardRuleTable` - cardinality rules table

Skip navigation links

- [Overview](../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFEModel.md)
- [Next Class](NFEModelObject.md)

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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
