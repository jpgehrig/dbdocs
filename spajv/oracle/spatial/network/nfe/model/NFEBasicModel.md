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

- Prev Class
- [Next Class](NFEBasicModelObject.md)

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

## Class NFEBasicModel

- java.lang.Object

- - oracle.spatial.network.nfe.model.NFEBasicModel

<!-- -->

- All Implemented Interfaces:
  java.util.EventListener, [NFEModelListener](event/NFEModelListener.md), [NFEModel](NFEModel.md)

  ------------------------------------------------------------------------



      public class NFEBasicModel
      extends java.lang.Object
      implements NFEModel, NFEModelListener

  The default implementation of NFEModel

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.spatial.network.nfe.model.event.[NFEModelListener](event/NFEModelListener.md)

      [`METHOD_MODEL_OBJECT_ADDED`](event/NFEModelListener.md)`, `[`METHOD_MODEL_OBJECT_REMOVED`](event/NFEModelListener.md)`, `[`METHOD_MODEL_OBJECTS_ADDED`](event/NFEModelListener.md)`, `[`METHOD_MODEL_OBJECTS_REMOVED`](event/NFEModelListener.md)`, `[`METHOD_PROPERTY_CHANGED`](event/NFEModelListener.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `NFEBasicModel``()`         |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

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
    | `void`                                                                                                   | `modelObjectAdded``(`[`NFEModelObjectEvent`](event/NFEModelObjectEvent.md)` event)`<br>Invoked when a model object has been added                                                                                                                                                          |
    | `void`                                                                                                   | `modelObjectPropertyChanged``(`[`NFEModelObjectPropertyChangedEvent`](event/NFEModelObjectPropertyChangedEvent.md)` event)`<br>Invoked when a model object's property has been changed                                                                                                     |
    | `void`                                                                                                   | `modelObjectRemoved``(`[`NFEModelObjectEvent`](event/NFEModelObjectEvent.md)` event)`<br>Invoked when a model object has been removed                                                                                                                                                      |
    | `void`                                                                                                   | `modelObjectsAdded``(`[`NFEModelObjectsEvent`](event/NFEModelObjectsEvent.md)` event)`<br>Invoked when one or more model objects have been added                                                                                                                                           |
    | `void`                                                                                                   | `modelObjectsRemoved``(`[`NFEModelObjectsEvent`](event/NFEModelObjectsEvent.md)` event)`<br>Invoked when one or more model objects have been removed                                                                                                                                       |
    | [`NFEFeatureLayer`](feature/NFEFeatureLayer.md)                                                          | `removeFeatureLayer``(long featureLayerId)`<br>Removes a feature layer with specified from the model                                                                                                                                                                                       |
    | `void`                                                                                                   | `removeModelListener``(`[`NFEModelListener`](event/NFEModelListener.md)` listener)`<br>Removes a listener from the model.                                                                                                                                                                  |
    | `void`                                                                                                   | `setAnalysisLayer``(`[`NFEFeatureLayer`](feature/NFEFeatureLayer.md)` analysisFeatureLayer)`<br>Sets a feature layer which contains paths from analysis.                                                                                                                                   |
    | `void`                                                                                                   | `setEditionManager``(`[`NFEEditionManager`](edit/NFEEditionManager.md)` em)`<br>Sets the edition managaer to be used by the current model to track changes made to the model's content.                                                                                                    |
    | `void`                                                                                                   | `setEventDispatcher``(`[`NFEEventDispatcher`](event/NFEEventDispatcher.md)`<`[`NFEModelListener`](event/NFEModelListener.md)`> eventDispatcher)`<br>Sets the event dispatcher used by the model to fire model events.                                                                      |
    | `void`                                                                                                   | `setIdManager``(`[`NFEIdManager`](NFEIdManager.md)` idManager)`<br>Sets the id manager used by the current model to assign ids to newly created objects                                                                                                                                    |
    | `void`                                                                                                   | `setMetadata``(`[`NFEModelMetadata`](NFEModelMetadata.md)` metadata)`<br>Sets the metadata of the model.                                                                                                                                                                                   |
    | `void`                                                                                                   | `setModelObjectFactory``(`[`NFEModelObjectFactory`](NFEModelObjectFactory.md)` moFactory)`<br>Sets the model object factory which will be used by the model to create new instances of model objects such as nodes, links, features and all the elements that are associated to the model. |
    | `void`                                                                                                   | `setNetwork``(`[`NFENetwork`](network/NFENetwork.md)` network)`<br>Sets a network to the current model.                                                                                                                                                                                    |
    | `void`                                                                                                   | `setServiceProvider``(`[`NFEIOServiceProvider`](../io/service/NFEIOServiceProvider.md)` serviceProvider)`<br>Sets the service provider to the current model.                                                                                                                               |
    | `void`                                                                                                   | `setWorkspaceInfo``(`[`NFEWorkspaceInfo`](NFEWorkspaceInfo.md)` workspaceInfo)`<br>Sets the workspace manager configuration used by the model for IO operations                                                                                                                            |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NFEBasicModel

          public NFEBasicModel()

  <!-- -->

  - ### Method Detail

    - #### setMetadata

          public void setMetadata(NFEModelMetadata metadata)

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Sets the metadata of the model. This is typically set automatically when a model is loaded from the database.
      Specified by:
      [`setMetadata`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Parameters:
      `metadata` - The current model's metedata

    <!-- -->

    - #### getMetadata

          public NFEModelMetadata getMetadata()

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Gets the metadata of the current model.
      Specified by:
      [`getMetadata`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Returns:
      The current model's metedata

    <!-- -->

    - #### getId

          public long getId()

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Gets the ID of the model. The ID is unique across all the models stored for a user in the database.
      Specified by:
      [`getId`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Returns:
      The current model's ID

    <!-- -->

    - #### getName

          public java.lang.String getName()

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Gets the name of the model.
      Specified by:
      [`getName`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Returns:
      The current model's name

    <!-- -->

    - #### getEditionMode

          public NFEEditionMode getEditionMode()

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Gets the edition mode of the current model. The mode can be FromScratch edition mode or ExistingNetwork edition mode.
      Specified by:
      [`getEditionMode`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Returns:
      The current model's edition mode

    <!-- -->

    - #### getGeometryDescriptor

          public NFEGeometryDescriptor getGeometryDescriptor()

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Gets the geometry descriptor of the current model. It contains the SRID used by the model along with dimensions' boundaries.
      Specified by:
      [`getGeometryDescriptor`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Returns:
      The current model's geometry descriptor

    <!-- -->

    - #### setWorkspaceInfo

          public void setWorkspaceInfo(NFEWorkspaceInfo workspaceInfo)

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Sets the workspace manager configuration used by the model for IO operations
      Specified by:
      [`setWorkspaceInfo`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Parameters:
      `workspaceInfo` - Workspace Manager data

    <!-- -->

    - #### getWorkspaceInfo

          public NFEWorkspaceInfo getWorkspaceInfo()

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Gets the workspace manager related data associated to the current model
      Specified by:
      [`getWorkspaceInfo`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Returns:
      Workspace Manager data

    <!-- -->

    - #### setModelObjectFactory

          public void setModelObjectFactory(NFEModelObjectFactory moFactory)

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Sets the model object factory which will be used by the model to create new instances of model objects such as nodes, links, features and all the elements that are associated to the model. A default instance of model object factory is set automatically when a model is created or loaded.
      Specified by:
      [`setModelObjectFactory`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Parameters:
      `moFactory` - A model object factory instance

    <!-- -->

    - #### getModelObjectFactory

          public NFEModelObjectFactory getModelObjectFactory()

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Gets the model object factory instance used by the current model.
      Specified by:
      [`getModelObjectFactory`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Returns:
      a model object factory instance

    <!-- -->

    - #### setIdManager

          public void setIdManager(NFEIdManager idManager)

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Sets the id manager used by the current model to assign ids to newly created objects
      Specified by:
      [`setIdManager`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Parameters:
      `idManager` - an id manager instance

    <!-- -->

    - #### getIdManager

          public NFEIdManager getIdManager()

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Gets the id manager used by the current model
      Specified by:
      [`getIdManager`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Returns:
      an id manager instance

    <!-- -->

    - #### getServiceProvider

          public NFEIOServiceProvider getServiceProvider()

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Gets the service provider used by the model to perform IO operations
      Specified by:
      [`getServiceProvider`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Returns:
      a service provider instance

    <!-- -->

    - #### setServiceProvider

          public void setServiceProvider(NFEIOServiceProvider serviceProvider)

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Sets the service provider to the current model.
      Specified by:
      [`setServiceProvider`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Parameters:
      `serviceProvider` - a service provider instance

    <!-- -->

    - #### setNetwork

          public void setNetwork(NFENetwork network)

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Sets a network to the current model. Typically a network is automatically set when a model is created or loaded using IOServices through the service provider. The network may not contain nodes or links if the content has not been added or loaded from the database.
      Specified by:
      [`setNetwork`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Parameters:
      `network` - a network instance

    <!-- -->

    - #### getNetwork

          public NFENetwork getNetwork()

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Gets the current model's network
      Specified by:
      [`getNetwork`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Returns:
      a not null, possibly empty, network instance

    <!-- -->

    - #### addFeatureLayer

          public void addFeatureLayer(NFEFeatureLayer featureLayer)

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Adds a feature layer to the model. A feature layer instance usually is added automatically when it is created using IOServices through the service provider
      Specified by:
      [`addFeatureLayer`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Parameters:
      `featureLayer` - a not null, possibly empty, feature layer instance

    <!-- -->

    - #### getFeatureLayers

          public java.util.Collection<NFEFeatureLayer> getFeatureLayers()

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Gets the feature layers of the current model. The feature layers may not contain features if content has not be added or loaded from the database.
      Specified by:
      [`getFeatureLayers`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Returns:
      a collection of feature layers.

    <!-- -->

    - #### getFeatureLayer

          public NFEFeatureLayer getFeatureLayer(long featureLayerId)

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Gets a model's feature layer by its id.
      Specified by:
      [`getFeatureLayer`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Parameters:
      `featureLayerId` - a feature layer id

      Returns:
      a feature layer instance contained in the model. Null otherwise

    <!-- -->

    - #### getFeatureLayer

          public NFEFeatureLayer getFeatureLayer(java.lang.String featureLayerName)

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Gets a model's feature layer by its name
      Specified by:

      [`getFeatureLayer`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Returns:

    <!-- -->

    - #### removeFeatureLayer

          public NFEFeatureLayer removeFeatureLayer(long featureLayerId)

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Removes a feature layer with specified from the model
      Specified by:
      [`removeFeatureLayer`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Parameters:
      `featureLayerId` - a feature layer id

      Returns:
      the removed feature layer instance if it was contained in the model. Null otherwise

    <!-- -->

    - #### getLoadedArea

          public java.awt.geom.Area getLoadedArea()

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Gets the area currently loaded model's content. Model's content is all the network elements and features loaded into memory. The model should have loaded at least, the content lying into the loaded area. Additionally, a model could have boundary content loaded and other content loaded an analysis
      Specified by:
      [`getLoadedArea`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Returns:
      the area of the currently loaded network elements and features

    <!-- -->

    - #### addLoadedArea

          public void addLoadedArea(java.awt.geom.Area area)

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Adds an area loaded. Typically it is called by the IOServices when content is loaded.
      Specified by:
      [`addLoadedArea`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Parameters:
      `area` - the area of a recently loaded model's content

    <!-- -->

    - #### getFeatureElementsOnNetworkElement

          public java.util.Collection<NFEFeatureElement> getFeatureElementsOnNetworkElement(NFENetworkElement networkElement)

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Gets all the feature elements associated to a network element
      Specified by:
      [`getFeatureElementsOnNetworkElement`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Parameters:
      `networkElement` - a network element from the model's network

      Returns:
      a collection of feature elements associated to the network element. Null or empty collection if the network element does not contain feature elements.

    <!-- -->

    - #### getFeatureElementsOnNetworkElement

          public java.util.Collection<NFEFeatureElement> getFeatureElementsOnNetworkElement(NFENetworkElement networkElement,
                                                                                            int hierarchyLevel)

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Gets all the feature elements with the given hierarchy level associated to a network element
      Specified by:
      [`getFeatureElementsOnNetworkElement`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Parameters:
      `networkElement` - a network element from the model's network

      `hierarchyLevel` - the hierarchy level of the returned feature elements

      Returns:
      a collection of feature elements associated to the network element. Null or empty collection if the network element does not contain feature elements with the given hierarchy level.

    <!-- -->

    - #### getFeatureElementsCount

          public int getFeatureElementsCount(NFENetworkElement networkElement)

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Gets the number of feature elements associated to a network element
      Specified by:
      [`getFeatureElementsCount`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Parameters:
      `networkElement` - a network element from the model's network

      Returns:
      the number of feature elements associated to the network element

    <!-- -->

    - #### getFeaturesOnNetworkElement

          public java.util.Collection<NFEFeature> getFeaturesOnNetworkElement(NFENetworkElement networkElement)

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Gets all the features containing feature elements associated to the specified network element
      Specified by:
      [`getFeaturesOnNetworkElement`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Parameters:
      `networkElement` - a network element from the model's network

      Returns:
      a collection of features. Null or empty collection if the network element does not contain feature elements

    <!-- -->

    - #### setEditionManager

          public void setEditionManager(NFEEditionManager em)

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Sets the edition managaer to be used by the current model to track changes made to the model's content. An instance is set by default when the model is created or loaded through the IOServices.
      Specified by:
      [`setEditionManager`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Parameters:
      `em` - an edition manager instance

    <!-- -->

    - #### getEditionManager

          public NFEEditionManager getEditionManager()

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Gets the edition manager used by the current model
      Specified by:
      [`getEditionManager`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Returns:
      an edition manager instance

    <!-- -->

    - #### setEventDispatcher

          public void setEventDispatcher(NFEEventDispatcher<NFEModelListener> eventDispatcher)

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Sets the event dispatcher used by the model to fire model events. An instance is set by default when the model is created or loaded through the IOServices. If the event dispatcher is set to null, no events will be reported.
      Specified by:
      [`setEventDispatcher`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Parameters:
      `eventDispatcher` - an event dispatcher instance

    <!-- -->

    - #### getDispatcher

          public NFEEventDispatcher<NFEModelListener> getDispatcher()

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Gets the event dispatcher used by the model.
      Specified by:
      [`getDispatcher`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Returns:
      an even dispatcher instance or null if it was removed.

    <!-- -->

    - #### modelObjectAdded

          public void modelObjectAdded(NFEModelObjectEvent event)

      Description copied from interface: [`NFEModelListener`](event/NFEModelListener.md)
      Invoked when a model object has been added
      Specified by:
      [`modelObjectAdded`](event/NFEModelListener.md) in interface [`NFEModelListener`](event/NFEModelListener.md)

      Parameters:
      `event` - contains a reference to the model object that has been added

    <!-- -->

    - #### modelObjectsAdded

          public void modelObjectsAdded(NFEModelObjectsEvent event)

      Description copied from interface: [`NFEModelListener`](event/NFEModelListener.md)
      Invoked when one or more model objects have been added
      Specified by:
      [`modelObjectsAdded`](event/NFEModelListener.md) in interface [`NFEModelListener`](event/NFEModelListener.md)

      Parameters:
      `event` - contains a collection of references to the model objects that have been added

    <!-- -->

    - #### modelObjectRemoved

          public void modelObjectRemoved(NFEModelObjectEvent event)

      Description copied from interface: [`NFEModelListener`](event/NFEModelListener.md)
      Invoked when a model object has been removed
      Specified by:
      [`modelObjectRemoved`](event/NFEModelListener.md) in interface [`NFEModelListener`](event/NFEModelListener.md)

      Parameters:
      `event` - contains a reference to the model object that has been removed

    <!-- -->

    - #### modelObjectsRemoved

          public void modelObjectsRemoved(NFEModelObjectsEvent event)

      Description copied from interface: [`NFEModelListener`](event/NFEModelListener.md)
      Invoked when one or more model objects have been removed
      Specified by:
      [`modelObjectsRemoved`](event/NFEModelListener.md) in interface [`NFEModelListener`](event/NFEModelListener.md)

      Parameters:
      `event` - contains a collection of references to the model objects that have been removed

    <!-- -->

    - #### modelObjectPropertyChanged

          public void modelObjectPropertyChanged(NFEModelObjectPropertyChangedEvent event)

      Description copied from interface: [`NFEModelListener`](event/NFEModelListener.md)
      Invoked when a model object's property has been changed
      Specified by:
      [`modelObjectPropertyChanged`](event/NFEModelListener.md) in interface [`NFEModelListener`](event/NFEModelListener.md)

      Parameters:
      `event` - contains a reference to the model objects which property has been changed and the name and previous value of the changed property

    <!-- -->

    - #### getAnalysisLayer

          public NFEFeatureLayer getAnalysisLayer()

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Gets a feature layer containing the paths resulting from analysis (if any)
      Specified by:
      [`getAnalysisLayer`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Returns:
      a feature layer instance

    <!-- -->

    - #### setAnalysisLayer

          public void setAnalysisLayer(NFEFeatureLayer analysisFeatureLayer)

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Sets a feature layer which contains paths from analysis.
      Specified by:
      [`setAnalysisLayer`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Parameters:
      `analysisFeatureLayer` - a feature layer instance

    <!-- -->

    - #### addModelListener

          public void addModelListener(NFEModelListener listener)

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Adds a listener to the model. The listener will be notified about every event in the model, network and feature layers contained in the model.
      Specified by:
      [`addModelListener`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Parameters:
      `listener` - a model listener instance

    <!-- -->

    - #### removeModelListener

          public void removeModelListener(NFEModelListener listener)

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Removes a listener from the model. It is also removed from the network and feature layers.
      Specified by:
      [`removeModelListener`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Parameters:
      `listener` - a model listener instance

    <!-- -->

    - #### getSpatialModel

          public NFESpatialModel getSpatialModel()

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Gets the spatial model used by the current model to keep track of the spatial positions of its content (network elements and feature elements)
      Specified by:
      [`getSpatialModel`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Returns:
      a spatial model instance

    <!-- -->

    - #### getManipulator

          public NFEManipulator getManipulator()

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Gets the manipulator instance which helps to perform some trivial feature-network operations over the model's content
      Specified by:
      [`getManipulator`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

      Returns:
      a manipulator instance

    <!-- -->

    - #### getRulesModel

          public NFERulesModel getRulesModel()

      Description copied from interface: [`NFEModel`](NFEModel.md)
      Gets the rules model associated to the current model. The rules model contains information of all the rule definitions and rules instances of the current model.
      Specified by:
      [`getRulesModel`](NFEModel.md) in interface [`NFEModel`](NFEModel.md)

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

- Prev Class
- [Next Class](NFEBasicModelObject.md)

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
