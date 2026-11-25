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

- [Prev Class](AbstractDAO.md)
- [Next Class](ModelDAO.md)

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

## Class FeatureDAO

- java.lang.Object

- - [oracle.spatial.network.nfe.io.jdbc.dao.AbstractDAO](AbstractDAO.md)

  - - oracle.spatial.network.nfe.io.jdbc.dao.FeatureDAO

<!-- -->

-

  ------------------------------------------------------------------------



      public class FeatureDAO
      extends AbstractDAO

  The FeatureDAO data access object provides methods to load and manage the model features. It is not recommended to use the data access objects methods, instead use the NFE services.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                 |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `FeatureDAO``(java.sql.Connection conn, `[`NFEModel`](../../../model/NFEModel.md)` model)`<br>Creates a FeatureDAO with the specified connection and model. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                                        | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                            |
    |----------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                                                   | `deleteDanglingFeatureElements``(`[`NFEFeatureLayerMetadata`](../../../model/feature/NFEFeatureLayerMetadata.md)` metadata)`<br>Deletes feature elements that refer to features that do not exist.                                                                                                                                                                                                                                                |
    | `void`                                                                                                   | `deleteFeatureElements``(java.util.Collection<`[`NFEFeatureElement`](../../../model/feature/NFEFeatureElement.md)`> featElems)`<br>Deletes the feature elements from the feature element relationship table.                                                                                                                                                                                                                                      |
    | `void`                                                                                                   | `deleteFeatureParentRelationship``(`[`NFEFeature`](../../../model/feature/NFEFeature.md)` feature)`<br>Deletes the feature parent relationship where the feature is parent or child.                                                                                                                                                                                                                                                              |
    | `void`                                                                                                   | `deleteFeatures``(java.util.Collection<`[`NFEFeature`](../../../model/feature/NFEFeature.md)`> features)`<br>Deletes the features in the feature and hierarchy tables, also deletes the record in the feature class relationship table.                                                                                                                                                                                                           |
    | `java.util.Collection<`[`NFEAttributeDescriptor`](../../../model/feature/NFEAttributeDescriptor.md)`>`   | `fetchFeatureLayerAttributeDescriptors``(`[`NFEFeatureLayerMetadata`](../../../model/feature/NFEFeatureLayerMetadata.md)` featLayerMetadata)`<br>Fetches the attribute descriptors of the specified feature layer.                                                                                                                                                                                                                                |
    | `java.util.Collection<`[`NFEFeatureLayerMetadata`](../../../model/feature/NFEFeatureLayerMetadata.md)`>` | `fetchFeatureLayersMetadata``(`[`NFEModelMetadata`](../../../model/NFEModelMetadata.md)` modelMetadata, java.util.Collection<java.lang.Long> featLayerIds)`<br>Fetches the metadata of the specified feature layers.                                                                                                                                                                                                                              |
    | `java.util.List<java.lang.Long>`                                                                         | `findFeaturesIds``(`[`NFEModelMetadata`](../../../model/NFEModelMetadata.md)` nfeModelMetadata, `[`NFESearchParams`](../../../beans/NFESearchParams.md)` searchParams)`<br>Searches features.                                                                                                                                                                                                                                                     |
    | `java.util.List<`[`FeatureAttributeDescriptor`](../../../workspace/FeatureAttributeDescriptor.md)`>`     | `getAttributesPerFeature``(`[`NFEFeatureLayer`](../../../model/feature/NFEFeatureLayer.md)` nfeFeatureLayer, java.lang.Long featureId)`<br>Returns the workspace attribute descriptors related to the specified feature.                                                                                                                                                                                                                          |
    | `java.util.List<`[`NFEFeature`](../../../model/feature/NFEFeature.md)`>`                                 | `getChildFeatures``(`[`NFEModel`](../../../model/NFEModel.md)` nfeModel, `[`NFEFeature`](../../../model/feature/NFEFeature.md)` nfeFeature)`<br>Returns the children of the specified feature.                                                                                                                                                                                                                                                    |
    | `java.lang.Long`                                                                                         | `getFeatureClassIdOfFeature``(`[`NFEModelMetadata`](../../../model/NFEModelMetadata.md)` nfeModelMetadata, java.lang.Long featureId, java.util.Collection<`[`NFEFeatureClass`](../../../model/feature/NFEFeatureClass.md)`> featureClasses)`<br>Returns the feature class identifier of the specified feature                                                                                                                                     |
    | `java.lang.String`                                                                                       | `getParentForFeature``(`[`NFEFeatureLayer`](../../../model/feature/NFEFeatureLayer.md)` nfeFeatureLayer, java.lang.Long featureId)`<br>Returns the value of the column NFE_PARENT\$ and NFE_PARENT_LAYER\$ that is in the feature table.                                                                                                                                                                                                          |
    | `java.util.List<java.lang.Long>`                                                                         | `getRelatedLinkIdsForFeature``(`[`NFEFeatureLayer`](../../../model/feature/NFEFeatureLayer.md)` featureLayer, java.lang.Long featureId)`<br>Returns the links identifiers of links related to the feature.                                                                                                                                                                                                                                        |
    | `java.util.List<java.lang.Long>`                                                                         | `getRelatedNodeIdsForFeature``(`[`NFEFeatureLayer`](../../../model/feature/NFEFeatureLayer.md)` featureLayer, java.lang.Long featureId)`<br>Returns the nodes identifiers of the nodes related to the feature.                                                                                                                                                                                                                                    |
    | `void`                                                                                                   | `loadFeatureClasses``(`[`NFEFeatureLayer`](../../../model/feature/NFEFeatureLayer.md)` featLayer)`<br>Loads the feature classes of the specified feature layer.                                                                                                                                                                                                                                                                                   |
    | `void`                                                                                                   | `loadFeatureLayerContent``(`[`NFEFeatureLayer`](../../../model/feature/NFEFeatureLayer.md)` featLayer, java.util.Collection<`[`NFENetworkElement`](../../../model/network/NFENetworkElement.md)`> netElements)`<br>Loads the features and rules instances related to the specified feature layer and network elements.                                                                                                                            |
    | `java.util.List<`[`NFEFeature`](../../../model/feature/NFEFeature.md)`>`                                 | `loadNetElementFeatures``(`[`NFEFeatureLayer`](../../../model/feature/NFEFeatureLayer.md)` featureLayer, `[`NFENetworkElement`](../../../model/network/NFENetworkElement.md)` networkElement)`<br>Loads the features related to the specified network element.                                                                                                                                                                                    |
    | `void`                                                                                                   | `saveFeatureElements``(java.util.Collection<`[`NFEFeatureElement`](../../../model/feature/NFEFeatureElement.md)`> featElems)`<br>Saves the new feature elements in the feature element relationship table.                                                                                                                                                                                                                                        |
    | `void`                                                                                                   | `saveFeatures``(java.util.Collection<`[`NFEFeature`](../../../model/feature/NFEFeature.md)`> features)`<br>Saves the new features in the feature and hierarchy tables, also creates a record in the feature class relationship table.                                                                                                                                                                                                             |
    | `void`                                                                                                   | `updateAttributeForFeatures``(`[`NFEModelMetadata`](../../../model/NFEModelMetadata.md)` nfeModelMetadata, `[`NFEFeatureLayer`](../../../model/feature/NFEFeatureLayer.md)` nfeFeatureLayer, java.lang.Long featureClassId, java.lang.String attributeName, java.lang.String newValue, java.lang.String oldValue)`<br>Updates the attributes for the features having the value oldValue and belonging to the specified feature class to newValue. |
    | `void`                                                                                                   | `updateFeatureElements``(java.util.Collection<`[`NFEFeatureElement`](../../../model/feature/NFEFeatureElement.md)`> featElems)`<br>Updates the feature elements in the feature element relationship table.                                                                                                                                                                                                                                        |
    | `void`                                                                                                   | `updateFeatureHierarchy``(`[`NFEFeature`](../../../model/feature/NFEFeature.md)` feature)`<br>Updates the feature hierarchy in the feature and hierarchy tables.                                                                                                                                                                                                                                                                                  |
    | `void`                                                                                                   | `updateFeatures``(java.util.Collection<`[`NFEFeature`](../../../model/feature/NFEFeature.md)`> features)`<br>Updates the features attributes and parents information.                                                                                                                                                                                                                                                                             |

    - ### Methods inherited from class oracle.spatial.network.nfe.io.jdbc.dao.[AbstractDAO](AbstractDAO.md)

      [`getConnection`](AbstractDAO.md)`, `[`getModel`](AbstractDAO.md)`, `[`getSQLValidator`](AbstractDAO.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### FeatureDAO

          public FeatureDAO(java.sql.Connection conn,
                            NFEModel model)

      Creates a FeatureDAO with the specified connection and model.
      Parameters:
      `conn` - connection

      `model` - model

  <!-- -->

  - ### Method Detail

    - #### saveFeatures

          public void saveFeatures(java.util.Collection<NFEFeature> features)
                            throws NFEIOException

      Saves the new features in the feature and hierarchy tables, also creates a record in the feature class relationship table. This method doesn't save the network elements used by the features neither the feature elements.
      Parameters:
      `features` - features

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### updateFeatures

          public void updateFeatures(java.util.Collection<NFEFeature> features)
                              throws NFEIOException

      Updates the features attributes and parents information.
      Parameters:
      `features` - features

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteFeatures

          public void deleteFeatures(java.util.Collection<NFEFeature> features)
                              throws NFEIOException

      Deletes the features in the feature and hierarchy tables, also deletes the record in the feature class relationship table. This method doesn't delete the network elements used by the features neither the feature elements.
      Parameters:
      `features` - features

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### saveFeatureElements

          public void saveFeatureElements(java.util.Collection<NFEFeatureElement> featElems)
                                   throws NFEIOException

      Saves the new feature elements in the feature element relationship table.
      Parameters:
      `featElems` - feature elements

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### updateFeatureElements

          public void updateFeatureElements(java.util.Collection<NFEFeatureElement> featElems)
                                     throws NFEIOException

      Updates the feature elements in the feature element relationship table.
      Parameters:
      `featElems` - feature elements

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteFeatureElements

          public void deleteFeatureElements(java.util.Collection<NFEFeatureElement> featElems)
                                     throws NFEIOException

      Deletes the feature elements from the feature element relationship table.
      Parameters:
      `featElems` - feature elements

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### loadFeatureLayerContent

          public void loadFeatureLayerContent(NFEFeatureLayer featLayer,
                                              java.util.Collection<NFENetworkElement> netElements)
                                       throws NFEIOException

      Loads the features and rules instances related to the specified feature layer and network elements.
      Parameters:
      `featLayer` - feature layer

      `netElements` - network elements

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### fetchFeatureLayersMetadata

          public java.util.Collection<NFEFeatureLayerMetadata> fetchFeatureLayersMetadata(NFEModelMetadata modelMetadata,
                                                                                          java.util.Collection<java.lang.Long> featLayerIds)
                                                                                   throws NFEIOException

      Fetches the metadata of the specified feature layers.
      Parameters:
      `modelMetadata` - model metadata

      `featLayerIds` - feature layers identifiers

      Returns:
      feature layers metadata

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### fetchFeatureLayerAttributeDescriptors

          public java.util.Collection<NFEAttributeDescriptor> fetchFeatureLayerAttributeDescriptors(NFEFeatureLayerMetadata featLayerMetadata)
                                                                                             throws NFEIOException

      Fetches the attribute descriptors of the specified feature layer.
      Parameters:
      `featLayerMetadata` - feature layer metadata

      Returns:
      attribute descriptors

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### loadFeatureClasses

          public void loadFeatureClasses(NFEFeatureLayer featLayer)
                                  throws NFEIOException

      Loads the feature classes of the specified feature layer.
      Parameters:
      `featLayer` - feature layer

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getFeatureClassIdOfFeature

          public java.lang.Long getFeatureClassIdOfFeature(NFEModelMetadata nfeModelMetadata,
                                                           java.lang.Long featureId,
                                                           java.util.Collection<NFEFeatureClass> featureClasses)
                                                    throws NFEIOException

      Returns the feature class identifier of the specified feature
      Parameters:
      `nfeModelMetadata` - model metadata

      `featureId` - feature id

      `featureClasses` - the possible feature class the feature could belong to (should be all the feature class of the feature layer the features belongs to)

      Returns:
      the feature class identifier

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getRelatedNodeIdsForFeature

          public java.util.List<java.lang.Long> getRelatedNodeIdsForFeature(NFEFeatureLayer featureLayer,
                                                                            java.lang.Long featureId)
                                                                     throws NFEIOException

      Returns the nodes identifiers of the nodes related to the feature.
      Parameters:
      `featureLayer` - feature layer

      `featureId` - feature identifier

      Returns:
      list of nodes identifiers

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getRelatedLinkIdsForFeature

          public java.util.List<java.lang.Long> getRelatedLinkIdsForFeature(NFEFeatureLayer featureLayer,
                                                                            java.lang.Long featureId)
                                                                     throws NFEIOException

      Returns the links identifiers of links related to the feature.
      Parameters:
      `featureLayer` - feature layer

      `featureId` - feature identifier

      Returns:
      list of links identifiers

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### loadNetElementFeatures

          public java.util.List<NFEFeature> loadNetElementFeatures(NFEFeatureLayer featureLayer,
                                                                   NFENetworkElement networkElement)
                                                            throws NFEIOException

      Loads the features related to the specified network element.
      Parameters:
      `featureLayer` - feature layer of the feature

      `networkElement` - network element

      Returns:
      list of feature

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getAttributesPerFeature

          public java.util.List<FeatureAttributeDescriptor> getAttributesPerFeature(NFEFeatureLayer nfeFeatureLayer,
                                                                                    java.lang.Long featureId)
                                                                             throws NFEIOException

      Returns the workspace attribute descriptors related to the specified feature.
      Parameters:
      `nfeFeatureLayer` - feature layer of the feature

      `featureId` - feature identifier

      Returns:
      workspace attribute descriptors

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getParentForFeature

          public java.lang.String getParentForFeature(NFEFeatureLayer nfeFeatureLayer,
                                                      java.lang.Long featureId)
                                               throws NFEIOException

      Returns the value of the column NFE_PARENT\$ and NFE_PARENT_LAYER\$ that is in the feature table. NFE_PARENT\$ is the feature identifier of the parent. NFE_PARENT_LAYER\$ is the feature layer identifier of the parent. If not null the parent is returned in the format NFE_PARENT_LAYER\$-NFE_PARENT, else an empty string is returned.
      Parameters:
      `nfeFeatureLayer` - feature layer of the feature

      `featureId` - feature identifier

      Returns:
      parent string

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteFeatureParentRelationship

          public void deleteFeatureParentRelationship(NFEFeature feature)
                                               throws NFEIOException

      Deletes the feature parent relationship where the feature is parent or child.
      Parameters:
      `feature` - feature

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### updateFeatureHierarchy

          public void updateFeatureHierarchy(NFEFeature feature)
                                      throws NFEIOException

      Updates the feature hierarchy in the feature and hierarchy tables.
      Parameters:
      `feature` - feature

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### getChildFeatures

          public java.util.List<NFEFeature> getChildFeatures(NFEModel nfeModel,
                                                             NFEFeature nfeFeature)
                                                      throws NFEIOException

      Returns the children of the specified feature.
      Parameters:
      `nfeModel` - model

      `nfeFeature` - feature

      Returns:
      children of the feature

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### findFeaturesIds

          public java.util.List<java.lang.Long> findFeaturesIds(NFEModelMetadata nfeModelMetadata,
                                                                NFESearchParams searchParams)
                                                         throws NFEIOException

      Searches features. In the object searchParams the featureLayerId is mandatory, the parameters featureClassId, featureId and conditionString are optional. The conditionString parameter will be added to the where clause of the search query on the feature table.
      Parameters:
      `nfeModelMetadata` - model metadata

      `searchParams` - search parameters

      Returns:
      identifiers of the resulting features

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### deleteDanglingFeatureElements

          public void deleteDanglingFeatureElements(NFEFeatureLayerMetadata metadata)
                                             throws NFEIOException

      Deletes feature elements that refer to features that do not exist.
      Parameters:
      `metadata` - feature layer metadata

      Throws:
      [`NFEIOException`](../../NFEIOException.md) - if an NFE error occurs.

    <!-- -->

    - #### updateAttributeForFeatures

          public void updateAttributeForFeatures(NFEModelMetadata nfeModelMetadata,
                                                 NFEFeatureLayer nfeFeatureLayer,
                                                 java.lang.Long featureClassId,
                                                 java.lang.String attributeName,
                                                 java.lang.String newValue,
                                                 java.lang.String oldValue)
                                          throws NFEIOException

      Updates the attributes for the features having the value oldValue and belonging to the specified feature class to newValue.
      Parameters:
      `nfeModelMetadata` - model metadata

      `nfeFeatureLayer` - feature layer

      `featureClassId` - feature class identifier

      `attributeName` - attribute name

      `newValue` - new value

      `oldValue` - old value

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

- [Prev Class](AbstractDAO.md)
- [Next Class](ModelDAO.md)

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
