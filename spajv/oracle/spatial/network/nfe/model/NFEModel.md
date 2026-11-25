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

- [Prev Class](NFEMetadata.md)
- [Next Class](NFEModelMetadata.md)

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

## Interface NFEModel

- All Known Implementing Classes:
  [NFEBasicModel](NFEBasicModel.md)

  ------------------------------------------------------------------------



      public interface NFEModel

  NFEModel is the entry point for representing Network Feature Model in memory. It contains the model definition (metadata, network, feature layers), content (nodes, links, features, feature elements) and additional classes which help or keep track of the editing tasks. There are two ways to get a new NFEModel instance:
  1) by creating a new model in the database: NFEModel model = modelService.createFromScratchModel("test", false, geomDescriptor);
  2) by loading an existing model from the database: NFEModel model = modelService.createFromScratchModel("test", false, geomDescriptor);
  An instance of NFEModelIOService is used in both cases. The NFEModelIOService returns a fully functional instance of NFEModel manager containing a network, feature layers (if it was loaded) and ready to edit, keep tracks, notify events and create model objects.
  The model's network and feature layers are empty and need to be populated by adding new elements (node, link, features, feature elements) or by loading the elements from the database.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                                        | Method and Description                                                                                                                                                                                                                                                                     |
    |----------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                                                   | `addFeatureLayer``(`[`NFEFeatureLayer`](feature/NFEFeatureLayer.md)` featureLayer)`<br>Adds a feature layer to the model.                                                                                                                                                                  |
    | `void`                                                                                                   | `addLoadedArea``(java.awt.geom.Area area)`<br>Adds an area loaded.                                                                                                                                                                                                                         |
    | `void`                                                                                                   | `addModelListener``(`[`NFEModelListener`](event/NFEModelListener.md)` listener)`<br>Adds a listener to the model.                                                                                                                                                                          |
    | [`NFEFeatureLayer`](feature/NFEFeatureLayer.md)                                                          | `getAnalysisLayer``()`<br>Gets a feature layer containing the paths resulting from analysis (if any)                                                                                                                                                                                       |
    | [`NFEEventDispatcher`](event/NFEEventDispatcher.md)`<`[`NFEModelListener`](event/NFEModelListener.md)`>` | `getDispatcher``()`<br>Gets the event dispatcher used by the model.                                                                                                                                                                                                                        |
    | [`NFEEditionManager`](edit/NFEEditionManager.md)                                                         | `getEditionManager``()`<br>Gets the edition manager used by the current model                                                                                                                                                                                                              |
    | [`NFEEditionMode`](NFEEditionMode.md)                                                                    | `getEditionMode``()`<br>Gets the edition mode of the current model.                                                                                                                                                                                                                        |
    | `int`                                                                                                    | `getFeatureElementsCount``(`[`NFENetworkElement`](network/NFENetworkElement.md)` networkElement)`<br>Gets the number of feature elements associated to a network element                                                                                                                   |
    | `java.util.Collection<`[`NFEFeatureElement`](feature/NFEFeatureElement.md)`>`                            | `getFeatureElementsOnNetworkElement``(`[`NFENetworkElement`](network/NFENetworkElement.md)` networkElement)`<br>Gets all the feature elements associated to a network element                                                                                                              |
    | `java.util.Collection<`[`NFEFeatureElement`](feature/NFEFeatureElement.md)`>`                            | `getFeatureElementsOnNetworkElement``(`[`NFENetworkElement`](network/NFENetworkElement.md)` networkElement, int hierarchyLevel)`<br>Gets all the feature elements with the given hierarchy level associated to a network element                                                           |
    | [`NFEFeatureLayer`](feature/NFEFeatureLayer.md)                                                          | `getFeatureLayer``(long featureLayerId)`<br>Gets a model's feature layer by its id.                                                                                                                                                                                                        |
    | [`NFEFeatureLayer`](feature/NFEFeatureLayer.md)                                                          | `getFeatureLayer``(java.lang.String featureLayerName)`<br>Gets a model's feature layer by its name                                                                                                                                                                                         |
    | `java.util.Collection<`[`NFEFeatureLayer`](feature/NFEFeatureLayer.md)`>`                                | `getFeatureLayers``()`<br>Gets the feature layers of the current model.                                                                                                                                                                                                                    |
    | `java.util.Collection<`[`NFEFeature`](feature/NFEFeature.md)`>`                                          | `getFeaturesOnNetworkElement``(`[`NFENetworkElement`](network/NFENetworkElement.md)` networkElement)`<br>Gets all the features containing feature elements associated to the specified network element                                                                                     |
    | [`NFEGeometryDescriptor`](NFEGeometryDescriptor.md)                                                      | `getGeometryDescriptor``()`<br>Gets the geometry descriptor of the current model.                                                                                                                                                                                                          |
    | `long`                                                                                                   | `getId``()`<br>Gets the ID of the model.                                                                                                                                                                                                                                                   |
    | [`NFEIdManager`](NFEIdManager.md)                                                                        | `getIdManager``()`<br>Gets the id manager used by the current model                                                                                                                                                                                                                        |
    | `java.awt.geom.Area`                                                                                     | `getLoadedArea``()`<br>Gets the area currently loaded model's content.                                                                                                                                                                                                                     |
    | [`NFEManipulator`](edit/NFEManipulator.md)                                                               | `getManipulator``()`<br>Gets the manipulator instance which helps to perform some trivial feature-network operations over the model's content                                                                                                                                              |
    | [`NFEModelMetadata`](NFEModelMetadata.md)                                                                | `getMetadata``()`<br>Gets the metadata of the current model.                                                                                                                                                                                                                               |
    | [`NFEModelObjectFactory`](NFEModelObjectFactory.md)                                                      | `getModelObjectFactory``()`<br>Gets the model object factory instance used by the current model.                                                                                                                                                                                           |
    | `java.lang.String`                                                                                       | `getName``()`<br>Gets the name of the model.                                                                                                                                                                                                                                               |
    | [`NFENetwork`](network/NFENetwork.md)                                                                    | `getNetwork``()`<br>Gets the current model's network                                                                                                                                                                                                                                       |
    | [`NFERulesModel`](rule/NFERulesModel.md)                                                                 | `getRulesModel``()`<br>Gets the rules model associated to the current model.                                                                                                                                                                                                               |
    | [`NFEIOServiceProvider`](../io/service/NFEIOServiceProvider.md)                                          | `getServiceProvider``()`<br>Gets the service provider used by the model to perform IO operations                                                                                                                                                                                           |
    | [`NFESpatialModel`](spatial/NFESpatialModel.md)                                                          | `getSpatialModel``()`<br>Gets the spatial model used by the current model to keep track of the spatial positions of its content (network elements and feature elements)                                                                                                                    |
    | [`NFEWorkspaceInfo`](NFEWorkspaceInfo.md)                                                                | `getWorkspaceInfo``()`<br>Gets the workspace manager related data associated to the current model                                                                                                                                                                                          |
    | [`NFEFeatureLayer`](feature/NFEFeatureLayer.md)                                                          | `removeFeatureLayer``(long featureLayerId)`<br>Removes a feature layer with specified from the model                                                                                                                                                                                       |
    | `void`                                                                                                   | `removeModelListener``(`[`NFEModelListener`](event/NFEModelListener.md)` listener)`<br>Removes a listener from the model.                                                                                                                                                                  |
    | `void`                                                                                                   | `setAnalysisLayer``(`[`NFEFeatureLayer`](feature/NFEFeatureLayer.md)` analysisFeatureLayer)`<br>Sets a feature layer which contains paths from analysis.                                                                                                                                   |
    | `void`                                                                                                   | `setEditionManager``(`[`NFEEditionManager`](edit/NFEEditionManager.md)` em)`<br>Sets the edition managaer to be used by the current model to track changes made to the model's content.                                                                                                    |
    | `void`                                                                                                   | `setEventDispatcher``(`[`NFEEventDispatcher`](event/NFEEventDispatcher.md)`<`[`NFEModelListener`](event/NFEModelListener.md)`> eventDispatcher)`<br>Sets the event dispatcher used by the model to fire model events.                                                                      |
    | `void`                                                                                                   | `setIdManager``(`[`NFEIdManager`](NFEIdManager.md)` idManager)`<br>Sets the id manager used by the current model to assign ids to newly created objects                                                                                                                                    |
    | `void`                                                                                                   | `setMetadata``(`[`NFEModelMetadata`](NFEModelMetadata.md)` metadata)`<br>Sets the metadata of the model.                                                                                                                                                                                   |
    | `void`                                                                                                   | `setModelObjectFactory``(`[`NFEModelObjectFactory`](NFEModelObjectFactory.md)` moFactory)`<br>Sets the model object factory which will be used by the model to create new instances of model objects such as nodes, links, features and all the elements that are associated to the model. |
    | `void`                                                                                                   | `setNetwork``(`[`NFENetwork`](network/NFENetwork.md)` network)`<br>Sets a network to the current model.                                                                                                                                                                                    |
    | `void`                                                                                                   | `setServiceProvider``(`[`NFEIOServiceProvider`](../io/service/NFEIOServiceProvider.md)` sp)`<br>Sets the service provider to the current model.                                                                                                                                            |
    | `void`                                                                                                   | `setWorkspaceInfo``(`[`NFEWorkspaceInfo`](NFEWorkspaceInfo.md)` workspace)`<br>Sets the workspace manager configuration used by the model for IO operations                                                                                                                                |

<!-- -->

- - ### Method Detail

    - #### setMetadata

          void setMetadata(NFEModelMetadata metadata)

      Sets the metadata of the model. This is typically set automatically when a model is loaded from the database.
      Parameters:
      `metadata` - The current model's metedata

    <!-- -->

    - #### getMetadata

          NFEModelMetadata getMetadata()

      Gets the metadata of the current model.
      Returns:
      The current model's metedata

    <!-- -->

    - #### getId

          long getId()

      Gets the ID of the model. The ID is unique across all the models stored for a user in the database.
      Returns:
      The current model's ID

    <!-- -->

    - #### getName

          java.lang.String getName()

      Gets the name of the model.
      Returns:
      The current model's name

    <!-- -->

    - #### getEditionMode

          NFEEditionMode getEditionMode()

      Gets the edition mode of the current model. The mode can be FromScratch edition mode or ExistingNetwork edition mode.
      Returns:
      The current model's edition mode

    <!-- -->

    - #### getGeometryDescriptor

          NFEGeometryDescriptor getGeometryDescriptor()

      Gets the geometry descriptor of the current model. It contains the SRID used by the model along with dimensions' boundaries.
      Returns:
      The current model's geometry descriptor

    <!-- -->

    - #### setWorkspaceInfo

          void setWorkspaceInfo(NFEWorkspaceInfo workspace)

      Sets the workspace manager configuration used by the model for IO operations
      Parameters:
      `workspace` - Workspace Manager data

    <!-- -->

    - #### getWorkspaceInfo

          NFEWorkspaceInfo getWorkspaceInfo()

      Gets the workspace manager related data associated to the current model
      Returns:
      Workspace Manager data

    <!-- -->

    - #### setModelObjectFactory

          void setModelObjectFactory(NFEModelObjectFactory moFactory)

      Sets the model object factory which will be used by the model to create new instances of model objects such as nodes, links, features and all the elements that are associated to the model. A default instance of model object factory is set automatically when a model is created or loaded.
      Parameters:
      `moFactory` - A model object factory instance

    <!-- -->

    - #### getModelObjectFactory

          NFEModelObjectFactory getModelObjectFactory()

      Gets the model object factory instance used by the current model.
      Returns:
      a model object factory instance

    <!-- -->

    - #### setIdManager

          void setIdManager(NFEIdManager idManager)

      Sets the id manager used by the current model to assign ids to newly created objects
      Parameters:
      `idManager` - an id manager instance

    <!-- -->

    - #### getIdManager

          NFEIdManager getIdManager()

      Gets the id manager used by the current model
      Returns:
      an id manager instance

    <!-- -->

    - #### getServiceProvider

          NFEIOServiceProvider getServiceProvider()

      Gets the service provider used by the model to perform IO operations
      Returns:
      a service provider instance

    <!-- -->

    - #### setServiceProvider

          void setServiceProvider(NFEIOServiceProvider sp)

      Sets the service provider to the current model.
      Parameters:
      `sp` - a service provider instance

    <!-- -->

    - #### setNetwork

          void setNetwork(NFENetwork network)

      Sets a network to the current model. Typically a network is automatically set when a model is created or loaded using IOServices through the service provider. The network may not contain nodes or links if the content has not been added or loaded from the database.
      Parameters:
      `network` - a network instance

    <!-- -->

    - #### getNetwork

          NFENetwork getNetwork()

      Gets the current model's network
      Returns:
      a not null, possibly empty, network instance

    <!-- -->

    - #### addFeatureLayer

          void addFeatureLayer(NFEFeatureLayer featureLayer)

      Adds a feature layer to the model. A feature layer instance usually is added automatically when it is created using IOServices through the service provider
      Parameters:
      `featureLayer` - a not null, possibly empty, feature layer instance

    <!-- -->

    - #### getFeatureLayers

          java.util.Collection<NFEFeatureLayer> getFeatureLayers()

      Gets the feature layers of the current model. The feature layers may not contain features if content has not be added or loaded from the database.
      Returns:
      a collection of feature layers.

    <!-- -->

    - #### getFeatureLayer

          NFEFeatureLayer getFeatureLayer(long featureLayerId)

      Gets a model's feature layer by its id.
      Parameters:
      `featureLayerId` - a feature layer id

      Returns:
      a feature layer instance contained in the model. Null otherwise

    <!-- -->

    - #### getFeatureLayer

          NFEFeatureLayer getFeatureLayer(java.lang.String featureLayerName)

      Gets a model's feature layer by its name
      Parameters:

      `featureLayerName` -

      Returns:

    <!-- -->

    - #### removeFeatureLayer

          NFEFeatureLayer removeFeatureLayer(long featureLayerId)

      Removes a feature layer with specified from the model
      Parameters:
      `featureLayerId` - a feature layer id

      Returns:
      the removed feature layer instance if it was contained in the model. Null otherwise

    <!-- -->

    - #### getLoadedArea

          java.awt.geom.Area getLoadedArea()

      Gets the area currently loaded model's content. Model's content is all the network elements and features loaded into memory. The model should have loaded at least, the content lying into the loaded area. Additionally, a model could have boundary content loaded and other content loaded an analysis
      Returns:
      the area of the currently loaded network elements and features

    <!-- -->

    - #### addLoadedArea

          void addLoadedArea(java.awt.geom.Area area)

      Adds an area loaded. Typically it is called by the IOServices when content is loaded.
      Parameters:
      `area` - the area of a recently loaded model's content

    <!-- -->

    - #### getFeatureElementsOnNetworkElement

          java.util.Collection<NFEFeatureElement> getFeatureElementsOnNetworkElement(NFENetworkElement networkElement)

      Gets all the feature elements associated to a network element
      Parameters:
      `networkElement` - a network element from the model's network

      Returns:
      a collection of feature elements associated to the network element. Null or empty collection if the network element does not contain feature elements.

    <!-- -->

    - #### getFeatureElementsOnNetworkElement

          java.util.Collection<NFEFeatureElement> getFeatureElementsOnNetworkElement(NFENetworkElement networkElement,
                                                                                     int hierarchyLevel)

      Gets all the feature elements with the given hierarchy level associated to a network element
      Parameters:
      `networkElement` - a network element from the model's network

      `hierarchyLevel` - the hierarchy level of the returned feature elements

      Returns:
      a collection of feature elements associated to the network element. Null or empty collection if the network element does not contain feature elements with the given hierarchy level.

    <!-- -->

    - #### getFeatureElementsCount

          int getFeatureElementsCount(NFENetworkElement networkElement)

      Gets the number of feature elements associated to a network element
      Parameters:
      `networkElement` - a network element from the model's network

      Returns:
      the number of feature elements associated to the network element

    <!-- -->

    - #### getFeaturesOnNetworkElement

          java.util.Collection<NFEFeature> getFeaturesOnNetworkElement(NFENetworkElement networkElement)

      Gets all the features containing feature elements associated to the specified network element
      Parameters:
      `networkElement` - a network element from the model's network

      Returns:
      a collection of features. Null or empty collection if the network element does not contain feature elements

    <!-- -->

    - #### setEditionManager

          void setEditionManager(NFEEditionManager em)

      Sets the edition managaer to be used by the current model to track changes made to the model's content. An instance is set by default when the model is created or loaded through the IOServices.
      Parameters:
      `em` - an edition manager instance

    <!-- -->

    - #### getEditionManager

          NFEEditionManager getEditionManager()

      Gets the edition manager used by the current model
      Returns:
      an edition manager instance

    <!-- -->

    - #### setEventDispatcher

          void setEventDispatcher(NFEEventDispatcher<NFEModelListener> eventDispatcher)

      Sets the event dispatcher used by the model to fire model events. An instance is set by default when the model is created or loaded through the IOServices. If the event dispatcher is set to null, no events will be reported.
      Parameters:
      `eventDispatcher` - an event dispatcher instance

    <!-- -->

    - #### getDispatcher

          NFEEventDispatcher<NFEModelListener> getDispatcher()

      Gets the event dispatcher used by the model.
      Returns:
      an even dispatcher instance or null if it was removed.

    <!-- -->

    - #### getAnalysisLayer

          NFEFeatureLayer getAnalysisLayer()

      Gets a feature layer containing the paths resulting from analysis (if any)
      Returns:
      a feature layer instance

    <!-- -->

    - #### setAnalysisLayer

          void setAnalysisLayer(NFEFeatureLayer analysisFeatureLayer)

      Sets a feature layer which contains paths from analysis.
      Parameters:
      `analysisFeatureLayer` - a feature layer instance

    <!-- -->

    - #### addModelListener

          void addModelListener(NFEModelListener listener)

      Adds a listener to the model. The listener will be notified about every event in the model, network and feature layers contained in the model.
      Parameters:
      `listener` - a model listener instance

    <!-- -->

    - #### removeModelListener

          void removeModelListener(NFEModelListener listener)

      Removes a listener from the model. It is also removed from the network and feature layers.
      Parameters:
      `listener` - a model listener instance

    <!-- -->

    - #### getSpatialModel

          NFESpatialModel getSpatialModel()

      Gets the spatial model used by the current model to keep track of the spatial positions of its content (network elements and feature elements)
      Returns:
      a spatial model instance

    <!-- -->

    - #### getManipulator

          NFEManipulator getManipulator()

      Gets the manipulator instance which helps to perform some trivial feature-network operations over the model's content
      Returns:
      a manipulator instance

    <!-- -->

    - #### getRulesModel

          NFERulesModel getRulesModel()

      Gets the rules model associated to the current model. The rules model contains information of all the rule definitions and rules instances of the current model.
      Returns:
      a rules model instance

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

- [Prev Class](NFEMetadata.md)
- [Next Class](NFEModelMetadata.md)

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
