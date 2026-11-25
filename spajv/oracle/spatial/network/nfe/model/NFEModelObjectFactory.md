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

- [Prev Class](NFEModelObject.md)
- [Next Class](NFEWorkspaceInfo.md)

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

## Interface NFEModelObjectFactory

- All Known Implementing Classes:
  [NFEBasicModelObjectFactory](NFEBasicModelObjectFactory.md)

  ------------------------------------------------------------------------



      public interface NFEModelObjectFactory

  Implementations of this class are used to get new instances of most of the classes in the NFE API. Use NFEModel.getModelObjectFactory() to get a default instance of NDEModelObjectFactory. If it is needed to use different implementations than the provided by default, set a new implementation of NFEModelObjectFactory using NFEModel.setNFEModelObjecFactory(). Most of the methods used for instantiating Model Object Classes come in two flavors: - Parameterless: usually, these methods automatically assign an ID to the newly created instance - ID-parameter: these methods assign the given ID to the newly created instance. This methods are typically used when loading existing elements from the database.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                       | Method and Description                                                                                                                                                                                                              |
    |-------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`NFEAttributeConstraint`](feature/NFEAttributeConstraint.md)           | `createAttributeConstraint``()`<br>Creates a new instance of NFEAttributeConstaint and automatically assigns an ID to it.                                                                                                           |
    | [`NFEAttributeConstraint`](feature/NFEAttributeConstraint.md)           | `createAttributeConstraint``(long attrConstraintId)`<br>Creates a new instance of NFEAttributeConstaint and sets the given ID.                                                                                                      |
    | [`NFEAttributeDescriptor`](feature/NFEAttributeDescriptor.md)           | `createAttributeDescriptor``()`<br>Creates a new instance of NFEAttributeDescriptor.                                                                                                                                                |
    | [`NFECardinalityRule`](rule/NFECardinalityRule.md)                      | `createCardinalityRule``()`<br>Creates a new instance of NFECardinalityRule with and automatically assigns an ID to it                                                                                                              |
    | [`NFECardinalityRule`](rule/NFECardinalityRule.md)                      | `createCardinalityRule``(long ruleId)`<br>Creates a new instance of NFECardinalityRule with and sets the given ID                                                                                                                   |
    | [`NFECatalog`](feature/NFECatalog.md)                                   | `createCatalog``()`<br>Creates a new instance of NFECatalog and automatically assigns an ID to it.                                                                                                                                  |
    | [`NFECatalog`](feature/NFECatalog.md)                                   | `createCatalog``(long catalogId)`<br>Creates a new instance of NFECatalog and sets the given ID.                                                                                                                                    |
    | [`NFECatalogValue`](feature/NFECatalogValue.md)                         | `createCatalogValue``()`<br>Creates a new instance of NFECatalogValue.                                                                                                                                                              |
    | [`NFEFeature`](feature/NFEFeature.md)                                   | `createFeature``(long featureLayerId)`<br>Creates a new instance of NFEFeature for the Feature Layer identified by the given featureLayerId.                                                                                        |
    | [`NFEFeature`](feature/NFEFeature.md)                                   | `createFeature``(long featureLayerId, long featureId)`<br>Creates a new instance of NFEFeature for the Feature Layer identified by the given featureLayerId and sets the given Feature ID.                                          |
    | [`NFEFeatureClass`](feature/NFEFeatureClass.md)                         | `createFeatureClass``()`<br>Creates a new instance of NFEFeatureClass and automatically assigns an ID to it.                                                                                                                        |
    | [`NFEFeatureClass`](feature/NFEFeatureClass.md)                         | `createFeatureClass``(long featureClassId)`<br>Creates a new instance of NFEFeatureClass and sets the given ID.                                                                                                                     |
    | [`NFEFeatureElement`](feature/NFEFeatureElement.md)                     | `createFeatureElement``(long featureLayerId)`<br>Creates a new instance of NFEFeatureElement for the Feature Layer identified by the given featureLayerId and automatically sets a sequence number to the Feature Element.          |
    | [`NFEFeatureElement`](feature/NFEFeatureElement.md)                     | `createFeatureElement``(long featureLayerId, long sequence)`<br>Creates a new instance of NFEFeatureElement for the Feature Layer identified by the given featureLayerId and sets the given sequence number to the Feature Element. |
    | [`NFEFeatureLayer`](feature/NFEFeatureLayer.md)                         | `createFeatureLayer``()`<br>Creates a new instance of NFEFeatureLayer.                                                                                                                                                              |
    | [`NFELineLineRule`](rule/NFELineLineRule.md)                            | `createLineLineRule``()`<br>Creates a new instance of NFELineLineRule with and automatically assigns an ID to it                                                                                                                    |
    | [`NFELineLineRule`](rule/NFELineLineRule.md)                            | `createLineLineRule``(long ruleId)`<br>Creates a new instance of NFELineLineRule with and sets the given ID                                                                                                                         |
    | [`NFELinePointRule`](rule/NFELinePointRule.md)                          | `createLinePointRule``()`<br>Creates a new instance of NFELinePointRule with and automatically assigns an ID to it                                                                                                                  |
    | [`NFELinePointRule`](rule/NFELinePointRule.md)                          | `createLinePointRule``(long ruleId)`<br>Creates a new instance of NFELinePointRule with and sets the given ID                                                                                                                       |
    | [`NFELink`](network/NFELink.md)                                         | `createLink``(long id, `[`NFENode`](network/NFENode.md)` startNode, `[`NFENode`](network/NFENode.md)` endNode)`<br>Creates a new instance of NFELink and sets the given ID.                                                         |
    | [`NFELink`](network/NFELink.md)                                         | `createLink``(`[`NFENode`](network/NFENode.md)` startNode, `[`NFENode`](network/NFENode.md)` endNode)`<br>Creates a new instance of NFELink and assigns an ID.                                                                      |
    | [`NFENetwork`](network/NFENetwork.md)                                   | `createNetwork``()`<br>Creates a new instance of NFENetwork class.                                                                                                                                                                  |
    | [`NFENode`](network/NFENode.md)                                         | `createNode``()`<br>Creates a new instance of NFENode and assigns an ID.                                                                                                                                                            |
    | [`NFENode`](network/NFENode.md)                                         | `createNode``(long id)`<br>Creates a new instance of NFENode and sets the given ID.                                                                                                                                                 |
    | [`NFEPredefinedConnectedPoint`](feature/NFEPredefinedConnectedPoint.md) | `createPredefinedConnectedPoint``()`<br>Creates a new instance of NFEPredefinedConnectedPoint with an ID assigned automatically.                                                                                                    |
    | [`NFEPredefinedConnectedPoint`](feature/NFEPredefinedConnectedPoint.md) | `createPredefinedConnectedPoint``(long predefConnPointId)`<br>Creates a new instance of NFEPredefinedConnectedPoint and sets the given ID.                                                                                          |
    | [`NFERuleInstance`](rule/NFERuleInstance.md)                            | `createRuleInstance``()`<br>Creates a new instance of NFERuleInstance with and automatically assigns an ID to it                                                                                                                    |
    | [`NFERuleInstance`](rule/NFERuleInstance.md)                            | `createRuleInstance``(long ruleInstanceId)`<br>Creates a new instance of NFERuleInstance with and sets the given ID                                                                                                                 |
    | [`NFEIdManager`](NFEIdManager.md)                                       | `getIdManager``()`<br>Gets the NFEIdManager instance currently used.                                                                                                                                                                |
    | [`NFEModel`](NFEModel.md)                                               | `getModel``()`<br>Returns the current NFEModel instance                                                                                                                                                                             |
    | `void`                                                                  | `setIdManager``(`[`NFEIdManager`](NFEIdManager.md)` idManager)`<br>Sets an instance of NFEIdManager which is used to assign ID's to newly created instances.                                                                        |
    | `void`                                                                  | `setModel``(`[`NFEModel`](NFEModel.md)` model)`<br>Sets an instance of NFEModel.                                                                                                                                                    |

<!-- -->

- - ### Method Detail

    - #### setModel

          void setModel(NFEModel model)

      Sets an instance of NFEModel.
      Parameters:
      `model` - an NFEModel instance

    <!-- -->

    - #### getModel

          NFEModel getModel()

      Returns the current NFEModel instance
      Returns:
      an NFEModel instance

    <!-- -->

    - #### setIdManager

          void setIdManager(NFEIdManager idManager)

      Sets an instance of NFEIdManager which is used to assign ID's to newly created instances. A default implementation is assigned automatically when a new NFEModel instance is created.
      Parameters:
      `idManager` - an NFEIdManager instance

    <!-- -->

    - #### getIdManager

          NFEIdManager getIdManager()

      Gets the NFEIdManager instance currently used.
      Returns:
      an NFEIdManager instance

    <!-- -->

    - #### createNetwork

          NFENetwork createNetwork()

      Creates a new instance of NFENetwork class. This method does not assign an ID automatically to the newly created instance
      Returns:
      an empty instance of NFENetwork

    <!-- -->

    - #### createNode

          NFENode createNode()

      Creates a new instance of NFENode and assigns an ID.
      Returns:
      an instance of NFENode

    <!-- -->

    - #### createNode

          NFENode createNode(long id)

      Creates a new instance of NFENode and sets the given ID.
      Parameters:
      `id` - a unique ID for the newly created NFENode instance

      Returns:
      an NFENode instance

    <!-- -->

    - #### createLink

          NFELink createLink(NFENode startNode,
                             NFENode endNode)

      Creates a new instance of NFELink and assigns an ID. The given start and end nodes are set to the newly created NFELink.
      Parameters:
      `startNode` - the link's start node

      `endNode` - the link's end node

      Returns:
      an instance of NFELink

    <!-- -->

    - #### createLink

          NFELink createLink(long id,
                             NFENode startNode,
                             NFENode endNode)

      Creates a new instance of NFELink and sets the given ID. The given start and end nodes are set to the newly created NFELink.
      Parameters:
      `startNode` - the link's start node

      `endNode` - the link's end node

      Returns:
      an instance of NFELink

    <!-- -->

    - #### createFeatureLayer

          NFEFeatureLayer createFeatureLayer()

      Creates a new instance of NFEFeatureLayer. This method does not assign an ID.
      Returns:
      an empty instance of NFEFeatureLayer

    <!-- -->

    - #### createFeature

          NFEFeature createFeature(long featureLayerId)

      Creates a new instance of NFEFeature for the Feature Layer identified by the given featureLayerId.
      Parameters:
      `featureLayerId` - an ID of an existing NFEFeatureLayer

      Returns:
      an instance of NFEFeature

    <!-- -->

    - #### createFeature

          NFEFeature createFeature(long featureLayerId,
                                   long featureId)

      Creates a new instance of NFEFeature for the Feature Layer identified by the given featureLayerId and sets the given Feature ID.
      Parameters:
      `featureLayerId` - an ID of an existing NFEFeatureLayer

      `featureId` - a unique ID for the newly created NFEFeature instance

      Returns:
      an instance of NFEFeature

    <!-- -->

    - #### createFeatureElement

          NFEFeatureElement createFeatureElement(long featureLayerId)

      Creates a new instance of NFEFeatureElement for the Feature Layer identified by the given featureLayerId and automatically sets a sequence number to the Feature Element.
      Parameters:
      `featureLayerId` - an ID of an existing NFEFeatureLayer

      Returns:
      an instance of NFEFeatureElement

    <!-- -->

    - #### createFeatureElement

          NFEFeatureElement createFeatureElement(long featureLayerId,
                                                 long sequence)

      Creates a new instance of NFEFeatureElement for the Feature Layer identified by the given featureLayerId and sets the given sequence number to the Feature Element.
      Parameters:
      `featureLayerId` - an ID of an existing NFEFeatureLayer

      `sequence` - a sequence number for the newly created Feature Element

      Returns:
      an instance of NFEFeatureElement

    <!-- -->

    - #### createFeatureClass

          NFEFeatureClass createFeatureClass()

      Creates a new instance of NFEFeatureClass and automatically assigns an ID to it.
      Returns:
      an instance of NFEFeatureClass

    <!-- -->

    - #### createFeatureClass

          NFEFeatureClass createFeatureClass(long featureClassId)

      Creates a new instance of NFEFeatureClass and sets the given ID.
      Parameters:
      `featureClassId` - an ID for the newly created NFEFeatureClass instance

      Returns:
      an instance of NFEFeatureClass

    <!-- -->

    - #### createAttributeDescriptor

          NFEAttributeDescriptor createAttributeDescriptor()

      Creates a new instance of NFEAttributeDescriptor. An attribute descriptor does not contain an ID.
      Returns:
      an instance of NFEAttributeDescriptor

    <!-- -->

    - #### createAttributeConstraint

          NFEAttributeConstraint createAttributeConstraint()

      Creates a new instance of NFEAttributeConstaint and automatically assigns an ID to it.
      Returns:
      an instance of NFEAttributeConstraint

    <!-- -->

    - #### createAttributeConstraint

          NFEAttributeConstraint createAttributeConstraint(long attrConstraintId)

      Creates a new instance of NFEAttributeConstaint and sets the given ID.
      Parameters:
      `attrConstraintId` - an ID for the newly created NFEAttributeConstraint instance

      Returns:
      an instance of NFEAttributeConstraint

    <!-- -->

    - #### createCatalog

          NFECatalog createCatalog()

      Creates a new instance of NFECatalog and automatically assigns an ID to it.
      Returns:
      an instance of NFECatalog

    <!-- -->

    - #### createCatalog

          NFECatalog createCatalog(long catalogId)

      Creates a new instance of NFECatalog and sets the given ID.
      Parameters:
      `catalogId` - an ID for the newly created NFECatalog instance

      Returns:
      an instance of NFECatalog

    <!-- -->

    - #### createCatalogValue

          NFECatalogValue createCatalogValue()

      Creates a new instance of NFECatalogValue. An NFECatalogValue does not contain an ID.
      Returns:
      an instance of NFECatalogValue

    <!-- -->

    - #### createPredefinedConnectedPoint

          NFEPredefinedConnectedPoint createPredefinedConnectedPoint()

      Creates a new instance of NFEPredefinedConnectedPoint with an ID assigned automatically.
      Returns:
      an instance of NFEPredefinedConnectedPoint

    <!-- -->

    - #### createPredefinedConnectedPoint

          NFEPredefinedConnectedPoint createPredefinedConnectedPoint(long predefConnPointId)

      Creates a new instance of NFEPredefinedConnectedPoint and sets the given ID.
      Parameters:
      `predefConnPointId` - an ID for the newly created NFEPredefinedConnectedPoint instance

      Returns:
      an instance of NFEPredefinedConnectedPoint

    <!-- -->

    - #### createLinePointRule

          NFELinePointRule createLinePointRule()

      Creates a new instance of NFELinePointRule with and automatically assigns an ID to it
      Returns:
      an instance of NFELinePointRule

    <!-- -->

    - #### createLinePointRule

          NFELinePointRule createLinePointRule(long ruleId)

      Creates a new instance of NFELinePointRule with and sets the given ID
      Parameters:
      `ruleId` - an ID for the newly created NFELinePointRule instance

      Returns:
      an instance of NFELinePointRule

    <!-- -->

    - #### createLineLineRule

          NFELineLineRule createLineLineRule()

      Creates a new instance of NFELineLineRule with and automatically assigns an ID to it
      Returns:
      an instance of NFELineLineRule

    <!-- -->

    - #### createLineLineRule

          NFELineLineRule createLineLineRule(long ruleId)

      Creates a new instance of NFELineLineRule with and sets the given ID
      Parameters:
      `ruleId` - an ID for the newly created NFELineLineRule instance

      Returns:
      an instance of NFELineLineRule

    <!-- -->

    - #### createRuleInstance

          NFERuleInstance createRuleInstance()

      Creates a new instance of NFERuleInstance with and automatically assigns an ID to it
      Returns:
      an instance of NFERuleInstance

    <!-- -->

    - #### createRuleInstance

          NFERuleInstance createRuleInstance(long ruleInstanceId)

      Creates a new instance of NFERuleInstance with and sets the given ID
      Parameters:
      `ruleInstanceId` - an ID for the newly created NFERuleInstance instance

      Returns:
      an instance of NFERuleInstance

    <!-- -->

    - #### createCardinalityRule

          NFECardinalityRule createCardinalityRule()

      Creates a new instance of NFECardinalityRule with and automatically assigns an ID to it
      Returns:
      an instance of NFECardinalityRule

    <!-- -->

    - #### createCardinalityRule

          NFECardinalityRule createCardinalityRule(long ruleId)

      Creates a new instance of NFECardinalityRule with and sets the given ID
      Parameters:
      `ruleId` - an ID for the newly created NFECardinalityRule instance

      Returns:
      an instance of NFECardinalityRule

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

- [Prev Class](NFEModelObject.md)
- [Next Class](NFEWorkspaceInfo.md)

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
