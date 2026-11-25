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

- [Prev Class](NFEBasicModelObject.md)
- [Next Class](NFEDBSequenceIdGenerator.md)

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

## Class NFEBasicModelObjectFactory

- java.lang.Object

- - oracle.spatial.network.nfe.model.NFEBasicModelObjectFactory

<!-- -->

- All Implemented Interfaces:
  [NFEModelObjectFactory](NFEModelObjectFactory.md)

  ------------------------------------------------------------------------



      public class NFEBasicModelObjectFactory
      extends java.lang.Object
      implements NFEModelObjectFactory

  The dafault implementation of NFEModelObjectFactory

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description       |
    |-----------------------------------|
    | `NFEBasicModelObjectFactory``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

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

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEBasicModelObjectFactory

          public NFEBasicModelObjectFactory()

  <!-- -->

  - ### Method Detail

    - #### setModel

          public void setModel(NFEModel model)

      Description copied from interface: [`NFEModelObjectFactory`](NFEModelObjectFactory.md)
      Sets an instance of NFEModel.
      Specified by:
      [`setModel`](NFEModelObjectFactory.md) in interface [`NFEModelObjectFactory`](NFEModelObjectFactory.md)

      Parameters:
      `model` - an NFEModel instance

    <!-- -->

    - #### getModel

          public NFEModel getModel()

      Description copied from interface: [`NFEModelObjectFactory`](NFEModelObjectFactory.md)
      Returns the current NFEModel instance
      Specified by:
      [`getModel`](NFEModelObjectFactory.md) in interface [`NFEModelObjectFactory`](NFEModelObjectFactory.md)

      Returns:
      an NFEModel instance

    <!-- -->

    - #### setIdManager

          public void setIdManager(NFEIdManager idManager)

      Description copied from interface: [`NFEModelObjectFactory`](NFEModelObjectFactory.md)
      Sets an instance of NFEIdManager which is used to assign ID's to newly created instances. A default implementation is assigned automatically when a new NFEModel instance is created.
      Specified by:
      [`setIdManager`](NFEModelObjectFactory.md) in interface [`NFEModelObjectFactory`](NFEModelObjectFactory.md)

      Parameters:
      `idManager` - an NFEIdManager instance

    <!-- -->

    - #### getIdManager

          public NFEIdManager getIdManager()

      Description copied from interface: [`NFEModelObjectFactory`](NFEModelObjectFactory.md)
      Gets the NFEIdManager instance currently used.
      Specified by:
      [`getIdManager`](NFEModelObjectFactory.md) in interface [`NFEModelObjectFactory`](NFEModelObjectFactory.md)

      Returns:
      an NFEIdManager instance

    <!-- -->

    - #### createNetwork

          public NFENetwork createNetwork()

      Description copied from interface: [`NFEModelObjectFactory`](NFEModelObjectFactory.md)
      Creates a new instance of NFENetwork class. This method does not assign an ID automatically to the newly created instance
      Specified by:
      [`createNetwork`](NFEModelObjectFactory.md) in interface [`NFEModelObjectFactory`](NFEModelObjectFactory.md)

      Returns:
      an empty instance of NFENetwork

    <!-- -->

    - #### createNode

          public NFENode createNode()

      Description copied from interface: [`NFEModelObjectFactory`](NFEModelObjectFactory.md)
      Creates a new instance of NFENode and assigns an ID.
      Specified by:
      [`createNode`](NFEModelObjectFactory.md) in interface [`NFEModelObjectFactory`](NFEModelObjectFactory.md)

      Returns:
      an instance of NFENode

    <!-- -->

    - #### createNode

          public NFENode createNode(long id)

      Description copied from interface: [`NFEModelObjectFactory`](NFEModelObjectFactory.md)
      Creates a new instance of NFENode and sets the given ID.
      Specified by:
      [`createNode`](NFEModelObjectFactory.md) in interface [`NFEModelObjectFactory`](NFEModelObjectFactory.md)

      Parameters:
      `id` - a unique ID for the newly created NFENode instance

      Returns:
      an NFENode instance

    <!-- -->

    - #### createLink

          public NFELink createLink(NFENode startNode,
                                    NFENode endNode)

      Description copied from interface: [`NFEModelObjectFactory`](NFEModelObjectFactory.md)
      Creates a new instance of NFELink and assigns an ID. The given start and end nodes are set to the newly created NFELink.
      Specified by:
      [`createLink`](NFEModelObjectFactory.md) in interface [`NFEModelObjectFactory`](NFEModelObjectFactory.md)

      Parameters:
      `startNode` - the link's start node

      `endNode` - the link's end node

      Returns:
      an instance of NFELink

    <!-- -->

    - #### createLink

          public NFELink createLink(long id,
                                    NFENode startNode,
                                    NFENode endNode)

      Description copied from interface: [`NFEModelObjectFactory`](NFEModelObjectFactory.md)
      Creates a new instance of NFELink and sets the given ID. The given start and end nodes are set to the newly created NFELink.
      Specified by:
      [`createLink`](NFEModelObjectFactory.md) in interface [`NFEModelObjectFactory`](NFEModelObjectFactory.md)

      `startNode` - the link's start node

      `endNode` - the link's end node

      Returns:
      an instance of NFELink

    <!-- -->

    - #### createFeatureLayer

          public NFEFeatureLayer createFeatureLayer()

      Description copied from interface: [`NFEModelObjectFactory`](NFEModelObjectFactory.md)
      Creates a new instance of NFEFeatureLayer. This method does not assign an ID.
      Specified by:
      [`createFeatureLayer`](NFEModelObjectFactory.md) in interface [`NFEModelObjectFactory`](NFEModelObjectFactory.md)

      Returns:
      an empty instance of NFEFeatureLayer

    <!-- -->

    - #### createFeature

          public NFEFeature createFeature(long featureLayerId)

      Description copied from interface: [`NFEModelObjectFactory`](NFEModelObjectFactory.md)
      Creates a new instance of NFEFeature for the Feature Layer identified by the given featureLayerId.
      Specified by:
      [`createFeature`](NFEModelObjectFactory.md) in interface [`NFEModelObjectFactory`](NFEModelObjectFactory.md)

      Parameters:
      `featureLayerId` - an ID of an existing NFEFeatureLayer

      Returns:
      an instance of NFEFeature

    <!-- -->

    - #### createFeature

          public NFEFeature createFeature(long featureLayerId,
                                          long featureId)

      Description copied from interface: [`NFEModelObjectFactory`](NFEModelObjectFactory.md)
      Creates a new instance of NFEFeature for the Feature Layer identified by the given featureLayerId and sets the given Feature ID.
      Specified by:
      [`createFeature`](NFEModelObjectFactory.md) in interface [`NFEModelObjectFactory`](NFEModelObjectFactory.md)

      Parameters:
      `featureLayerId` - an ID of an existing NFEFeatureLayer

      `featureId` - a unique ID for the newly created NFEFeature instance

      Returns:
      an instance of NFEFeature

    <!-- -->

    - #### createFeatureElement

          public NFEFeatureElement createFeatureElement(long featureLayerId)

      Description copied from interface: [`NFEModelObjectFactory`](NFEModelObjectFactory.md)
      Creates a new instance of NFEFeatureElement for the Feature Layer identified by the given featureLayerId and automatically sets a sequence number to the Feature Element.
      Specified by:
      [`createFeatureElement`](NFEModelObjectFactory.md) in interface [`NFEModelObjectFactory`](NFEModelObjectFactory.md)

      Parameters:
      `featureLayerId` - an ID of an existing NFEFeatureLayer

      Returns:
      an instance of NFEFeatureElement

    <!-- -->

    - #### createFeatureElement

          public NFEFeatureElement createFeatureElement(long featureLayerId,
                                                        long sequence)

      Description copied from interface: [`NFEModelObjectFactory`](NFEModelObjectFactory.md)
      Creates a new instance of NFEFeatureElement for the Feature Layer identified by the given featureLayerId and sets the given sequence number to the Feature Element.
      Specified by:
      [`createFeatureElement`](NFEModelObjectFactory.md) in interface [`NFEModelObjectFactory`](NFEModelObjectFactory.md)

      Parameters:
      `featureLayerId` - an ID of an existing NFEFeatureLayer

      `sequence` - a sequence number for the newly created Feature Element

      Returns:
      an instance of NFEFeatureElement

    <!-- -->

    - #### createFeatureClass

          public NFEFeatureClass createFeatureClass()

      Description copied from interface: [`NFEModelObjectFactory`](NFEModelObjectFactory.md)
      Creates a new instance of NFEFeatureClass and automatically assigns an ID to it.
      Specified by:
      [`createFeatureClass`](NFEModelObjectFactory.md) in interface [`NFEModelObjectFactory`](NFEModelObjectFactory.md)

      Returns:
      an instance of NFEFeatureClass

    <!-- -->

    - #### createFeatureClass

          public NFEFeatureClass createFeatureClass(long featureClassId)

      Description copied from interface: [`NFEModelObjectFactory`](NFEModelObjectFactory.md)
      Creates a new instance of NFEFeatureClass and sets the given ID.
      Specified by:
      [`createFeatureClass`](NFEModelObjectFactory.md) in interface [`NFEModelObjectFactory`](NFEModelObjectFactory.md)

      Parameters:
      `featureClassId` - an ID for the newly created NFEFeatureClass instance

      Returns:
      an instance of NFEFeatureClass

    <!-- -->

    - #### createAttributeDescriptor

          public NFEAttributeDescriptor createAttributeDescriptor()

      Description copied from interface: [`NFEModelObjectFactory`](NFEModelObjectFactory.md)
      Creates a new instance of NFEAttributeDescriptor. An attribute descriptor does not contain an ID.
      Specified by:
      [`createAttributeDescriptor`](NFEModelObjectFactory.md) in interface [`NFEModelObjectFactory`](NFEModelObjectFactory.md)

      Returns:
      an instance of NFEAttributeDescriptor

    <!-- -->

    - #### createAttributeConstraint

          public NFEAttributeConstraint createAttributeConstraint()

      Description copied from interface: [`NFEModelObjectFactory`](NFEModelObjectFactory.md)
      Creates a new instance of NFEAttributeConstaint and automatically assigns an ID to it.
      Specified by:
      [`createAttributeConstraint`](NFEModelObjectFactory.md) in interface [`NFEModelObjectFactory`](NFEModelObjectFactory.md)

      Returns:
      an instance of NFEAttributeConstraint

    <!-- -->

    - #### createAttributeConstraint

          public NFEAttributeConstraint createAttributeConstraint(long attrConstraintId)

      Description copied from interface: [`NFEModelObjectFactory`](NFEModelObjectFactory.md)
      Creates a new instance of NFEAttributeConstaint and sets the given ID.
      Specified by:
      [`createAttributeConstraint`](NFEModelObjectFactory.md) in interface [`NFEModelObjectFactory`](NFEModelObjectFactory.md)

      Parameters:
      `attrConstraintId` - an ID for the newly created NFEAttributeConstraint instance

      Returns:
      an instance of NFEAttributeConstraint

    <!-- -->

    - #### createCatalog

          public NFECatalog createCatalog()

      Description copied from interface: [`NFEModelObjectFactory`](NFEModelObjectFactory.md)
      Creates a new instance of NFECatalog and automatically assigns an ID to it.
      Specified by:
      [`createCatalog`](NFEModelObjectFactory.md) in interface [`NFEModelObjectFactory`](NFEModelObjectFactory.md)

      Returns:
      an instance of NFECatalog

    <!-- -->

    - #### createCatalog

          public NFECatalog createCatalog(long catalogId)

      Description copied from interface: [`NFEModelObjectFactory`](NFEModelObjectFactory.md)
      Creates a new instance of NFECatalog and sets the given ID.
      Specified by:
      [`createCatalog`](NFEModelObjectFactory.md) in interface [`NFEModelObjectFactory`](NFEModelObjectFactory.md)

      Parameters:
      `catalogId` - an ID for the newly created NFECatalog instance

      Returns:
      an instance of NFECatalog

    <!-- -->

    - #### createCatalogValue

          public NFECatalogValue createCatalogValue()

      Description copied from interface: [`NFEModelObjectFactory`](NFEModelObjectFactory.md)
      Creates a new instance of NFECatalogValue. An NFECatalogValue does not contain an ID.
      Specified by:
      [`createCatalogValue`](NFEModelObjectFactory.md) in interface [`NFEModelObjectFactory`](NFEModelObjectFactory.md)

      Returns:
      an instance of NFECatalogValue

    <!-- -->

    - #### createPredefinedConnectedPoint

          public NFEPredefinedConnectedPoint createPredefinedConnectedPoint()

      Description copied from interface: [`NFEModelObjectFactory`](NFEModelObjectFactory.md)
      Creates a new instance of NFEPredefinedConnectedPoint with an ID assigned automatically.
      Specified by:
      [`createPredefinedConnectedPoint`](NFEModelObjectFactory.md) in interface [`NFEModelObjectFactory`](NFEModelObjectFactory.md)

      Returns:
      an instance of NFEPredefinedConnectedPoint

    <!-- -->

    - #### createPredefinedConnectedPoint

          public NFEPredefinedConnectedPoint createPredefinedConnectedPoint(long predefConnPointId)

      Description copied from interface: [`NFEModelObjectFactory`](NFEModelObjectFactory.md)
      Creates a new instance of NFEPredefinedConnectedPoint and sets the given ID.
      Specified by:
      [`createPredefinedConnectedPoint`](NFEModelObjectFactory.md) in interface [`NFEModelObjectFactory`](NFEModelObjectFactory.md)

      Parameters:
      `predefConnPointId` - an ID for the newly created NFEPredefinedConnectedPoint instance

      Returns:
      an instance of NFEPredefinedConnectedPoint

    <!-- -->

    - #### createLinePointRule

          public NFELinePointRule createLinePointRule()

      Description copied from interface: [`NFEModelObjectFactory`](NFEModelObjectFactory.md)
      Creates a new instance of NFELinePointRule with and automatically assigns an ID to it
      Specified by:
      [`createLinePointRule`](NFEModelObjectFactory.md) in interface [`NFEModelObjectFactory`](NFEModelObjectFactory.md)

      Returns:
      an instance of NFELinePointRule

    <!-- -->

    - #### createLineLineRule

          public NFELineLineRule createLineLineRule()

      Description copied from interface: [`NFEModelObjectFactory`](NFEModelObjectFactory.md)
      Creates a new instance of NFELineLineRule with and automatically assigns an ID to it
      Specified by:
      [`createLineLineRule`](NFEModelObjectFactory.md) in interface [`NFEModelObjectFactory`](NFEModelObjectFactory.md)

      Returns:
      an instance of NFELineLineRule

    <!-- -->

    - #### createLinePointRule

          public NFELinePointRule createLinePointRule(long ruleId)

      Description copied from interface: [`NFEModelObjectFactory`](NFEModelObjectFactory.md)
      Creates a new instance of NFELinePointRule with and sets the given ID
      Specified by:
      [`createLinePointRule`](NFEModelObjectFactory.md) in interface [`NFEModelObjectFactory`](NFEModelObjectFactory.md)

      Parameters:
      `ruleId` - an ID for the newly created NFELinePointRule instance

      Returns:
      an instance of NFELinePointRule

    <!-- -->

    - #### createLineLineRule

          public NFELineLineRule createLineLineRule(long ruleId)

      Description copied from interface: [`NFEModelObjectFactory`](NFEModelObjectFactory.md)
      Creates a new instance of NFELineLineRule with and sets the given ID
      Specified by:
      [`createLineLineRule`](NFEModelObjectFactory.md) in interface [`NFEModelObjectFactory`](NFEModelObjectFactory.md)

      Parameters:
      `ruleId` - an ID for the newly created NFELineLineRule instance

      Returns:
      an instance of NFELineLineRule

    <!-- -->

    - #### createRuleInstance

          public NFERuleInstance createRuleInstance()

      Description copied from interface: [`NFEModelObjectFactory`](NFEModelObjectFactory.md)
      Creates a new instance of NFERuleInstance with and automatically assigns an ID to it
      Specified by:
      [`createRuleInstance`](NFEModelObjectFactory.md) in interface [`NFEModelObjectFactory`](NFEModelObjectFactory.md)

      Returns:
      an instance of NFERuleInstance

    <!-- -->

    - #### createRuleInstance

          public NFERuleInstance createRuleInstance(long ruleInstanceId)

      Description copied from interface: [`NFEModelObjectFactory`](NFEModelObjectFactory.md)
      Creates a new instance of NFERuleInstance with and sets the given ID
      Specified by:
      [`createRuleInstance`](NFEModelObjectFactory.md) in interface [`NFEModelObjectFactory`](NFEModelObjectFactory.md)

      Parameters:
      `ruleInstanceId` - an ID for the newly created NFERuleInstance instance

      Returns:
      an instance of NFERuleInstance

    <!-- -->

    - #### createCardinalityRule

          public NFECardinalityRule createCardinalityRule()

      Description copied from interface: [`NFEModelObjectFactory`](NFEModelObjectFactory.md)
      Creates a new instance of NFECardinalityRule with and automatically assigns an ID to it
      Specified by:
      [`createCardinalityRule`](NFEModelObjectFactory.md) in interface [`NFEModelObjectFactory`](NFEModelObjectFactory.md)

      Returns:
      an instance of NFECardinalityRule

    <!-- -->

    - #### createCardinalityRule

          public NFECardinalityRule createCardinalityRule(long ruleId)

      Description copied from interface: [`NFEModelObjectFactory`](NFEModelObjectFactory.md)
      Creates a new instance of NFECardinalityRule with and sets the given ID
      Specified by:
      [`createCardinalityRule`](NFEModelObjectFactory.md) in interface [`NFEModelObjectFactory`](NFEModelObjectFactory.md)

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

- [Prev Class](NFEBasicModelObject.md)
- [Next Class](NFEDBSequenceIdGenerator.md)

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
