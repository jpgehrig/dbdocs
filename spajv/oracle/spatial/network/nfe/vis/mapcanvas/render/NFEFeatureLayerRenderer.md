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

- [Prev Class](ContextualMenuHandler.md)
- [Next Class](NFEManipulableFeatureLayerRenderer.md)

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

oracle.spatial.network.nfe.vis.mapcanvas.render

## Class NFEFeatureLayerRenderer

- java.lang.Object

- - [oracle.spatial.network.nfe.vis.maps.layer.BasicLayer](../../maps/layer/BasicLayer.md)

  - - [oracle.spatial.network.nfe.vis.mapcanvas.render.NFERenderer](NFERenderer.md)\<[NFEFeatureElementGeoObject](../../../model/spatial/NFEFeatureElementGeoObject.md)\>

    - - oracle.spatial.network.nfe.vis.mapcanvas.render.NFEFeatureLayerRenderer

<!-- -->

- All Implemented Interfaces:
  java.util.EventListener, javax.swing.event.ChangeListener, [NFEModelListener](../../../model/event/NFEModelListener.md), [BehavioralLayer](../behavior/BehavioralLayer.md), [FeatureSelectableLayer](../behavior/FeatureSelectableLayer.md), [SelectionEditableLayer](../behavior/SelectionEditableLayer.md), [GeoObjectLayer](../../maps/core/GeoObjectLayer.md), [HoverableLayer](../../maps/core/HoverableLayer.md), [Layer](../../maps/core/Layer.md), [SelectableLayer](../../maps/core/SelectableLayer.md)

  <!-- -->

  Direct Known Subclasses:
  [NFEManipulableFeatureLayerRenderer](NFEManipulableFeatureLayerRenderer.md)

  ------------------------------------------------------------------------



      public class NFEFeatureLayerRenderer
      extends NFERenderer<NFEFeatureElementGeoObject>
      implements NFEModelListener, FeatureSelectableLayer, SelectionEditableLayer

  MapCanvas Layer implementation for rendering an NFE feature layer. It is automatically subscribed for listening its network's and feature layer's events to reflect the state and show the same elements with the same properties. Additionally to the basic selection feature provided by the basic NFERenderer, it allows selecting features as a whole (all the feature's feature elements are selected)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.spatial.network.nfe.model.event.[NFEModelListener](../../../model/event/NFEModelListener.md)

      [`METHOD_MODEL_OBJECT_ADDED`](../../../model/event/NFEModelListener.md)`, `[`METHOD_MODEL_OBJECT_REMOVED`](../../../model/event/NFEModelListener.md)`, `[`METHOD_MODEL_OBJECTS_ADDED`](../../../model/event/NFEModelListener.md)`, `[`METHOD_MODEL_OBJECTS_REMOVED`](../../../model/event/NFEModelListener.md)`, `[`METHOD_PROPERTY_CHANGED`](../../../model/event/NFEModelListener.md)

    <!-- -->

    - ### Fields inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](../../maps/core/Layer.md)

      [`PROPERTY_NAME`](../../maps/core/Layer.md)`, `[`PROPERTY_PROVIDERID`](../../maps/core/Layer.md)`, `[`PROPERTY_SRID`](../../maps/core/Layer.md)`, `[`PROPERTY_VISIBLE`](../../maps/core/Layer.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                     |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `NFEFeatureLayerRenderer``(`[`MapCanvas`](../../maps/core/MapCanvas.md)` canvas, `[`NFEModel`](../../../model/NFEModel.md)` model, long featLayerId)`<br>Allocates a new feature layer renderer |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                              | Method and Description                                                                                                                                                                                                                                       |
    |--------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                                                      | `clearSelection``()`<br>Clears all selected objects                                                                                                                                                                                                          |
    | [`ManipulationPreview`](../behavior/manipulate/ManipulationPreview.md)         | `createPreview``(java.util.Collection<`[`Manipulation`](../behavior/manipulate/Manipulation.md)`<`[`NFENetworkElement`](../../../model/network/NFENetworkElement.md)`>> manipulations)`<br>Creates a preview for the given manipulations to network elements |
    | `void`                                                                         | `deleteSelection``()`<br>Deletes the elements currently selected                                                                                                                                                                                             |
    | [`NFEFeatureLayer`](../../../model/feature/NFEFeatureLayer.md)                 | `getFeatureLayer``()`<br>Gets the rendered feature layer                                                                                                                                                                                                     |
    | [`NFEModel`](../../../model/NFEModel.md)                                       | `getModel``()`<br>Gets the NFE model                                                                                                                                                                                                                         |
    | `java.util.Collection<`[`NFEFeature`](../../../model/feature/NFEFeature.md)`>` | `getSelectedFeatures``()`<br>Gets the currently selected features                                                                                                                                                                                            |
    | `boolean`                                                                      | `isShowFlow``()`<br>Tells whether the line features flow is shown                                                                                                                                                                                            |
    | `void`                                                                         | `modelObjectAdded``(`[`NFEModelObjectEvent`](../../../model/event/NFEModelObjectEvent.md)` event)`<br>Invoked when a model object has been added                                                                                                             |
    | `void`                                                                         | `modelObjectPropertyChanged``(`[`NFEModelObjectPropertyChangedEvent`](../../../model/event/NFEModelObjectPropertyChangedEvent.md)` event)`<br>Invoked when a model object's property has been changed                                                        |
    | `void`                                                                         | `modelObjectRemoved``(`[`NFEModelObjectEvent`](../../../model/event/NFEModelObjectEvent.md)` event)`<br>Invoked when a model object has been removed                                                                                                         |
    | `void`                                                                         | `modelObjectsAdded``(`[`NFEModelObjectsEvent`](../../../model/event/NFEModelObjectsEvent.md)` event)`<br>Invoked when one or more model objects have been added                                                                                              |
    | `void`                                                                         | `modelObjectsRemoved``(`[`NFEModelObjectsEvent`](../../../model/event/NFEModelObjectsEvent.md)` event)`<br>Invoked when one or more model objects have been removed                                                                                          |
    | `boolean`                                                                      | `select``(java.util.List<`[`GeoObject`](../../maps/core/GeoObject.md)`> objs)`<br>Adds the provided objects to the selection list                                                                                                                            |
    | `void`                                                                         | `selectFeatures``(java.util.Collection<java.lang.Long> featureIds)`<br>Selects a group of features.                                                                                                                                                          |
    | `void`                                                                         | `setFeatureSelection``(java.util.Collection<java.lang.Long> featureIds)`<br>Sets the given features as selected.                                                                                                                                             |
    | `boolean`                                                                      | `setSelection``(java.util.List<`[`GeoObject`](../../maps/core/GeoObject.md)`> selectedGeoObjects)`<br>Clears selection before setting the provided objects as selected                                                                                       |
    | `void`                                                                         | `setShowFlow``(boolean showFlow)`<br>Sets whether the line features flow should be shown                                                                                                                                                                     |
    | `void`                                                                         | `synchronizeWithModel``()`<br>Updates the state to reflect the feature layer's state and refreshes the view                                                                                                                                                  |

    - ### Methods inherited from class oracle.spatial.network.nfe.vis.mapcanvas.render.[NFERenderer](NFERenderer.md)

      [`addContextualMenuHandler`](NFERenderer.md)`, `[`addSelectionListener`](NFERenderer.md)`, `[`clear`](NFERenderer.md)`, `[`clearHover`](NFERenderer.md)`, `[`getDataMBR`](NFERenderer.md)`, `[`getFullExtent`](NFERenderer.md)`, `[`getGeoObject`](NFERenderer.md)`, `[`getHover`](NFERenderer.md)`, `[`getImageOpacityAlpha`](NFERenderer.md)`, `[`getObject`](NFERenderer.md)`, `[`getObjects`](NFERenderer.md)`, `[`getSelection`](NFERenderer.md)`, `[`getSelection`](NFERenderer.md)`, `[`getSnapPoint`](NFERenderer.md)`, `[`getTolerance`](NFERenderer.md)`, `[`handleEvent`](NFERenderer.md)`, `[`hitTest`](NFERenderer.md)`, `[`hitTest`](NFERenderer.md)`, `[`isHover`](NFERenderer.md)`, `[`isSelected`](NFERenderer.md)`, `[`mapRegionChanged`](NFERenderer.md)`, `[`numHovered`](NFERenderer.md)`, `[`numSelected`](NFERenderer.md)`, `[`refresh`](NFERenderer.md)`, `[`refresh`](NFERenderer.md)`, `[`removeContextualMenuHandler`](NFERenderer.md)`, `[`removeSelectionListener`](NFERenderer.md)`, `[`render`](NFERenderer.md)`, `[`setHover`](NFERenderer.md)`, `[`setImageOpacityAlpha`](NFERenderer.md)`, `[`stateChanged`](NFERenderer.md)`, `[`unselect`](NFERenderer.md)`, `[`update`](NFERenderer.md)

    <!-- -->

    - ### Methods inherited from class oracle.spatial.network.nfe.vis.maps.layer.[BasicLayer](../../maps/layer/BasicLayer.md)

      [`added`](../../maps/layer/BasicLayer.md)`, `[`addPropertyChangeListener`](../../maps/layer/BasicLayer.md)`, `[`addPropertyChangeListener`](../../maps/layer/BasicLayer.md)`, `[`fromXMLElement`](../../maps/layer/BasicLayer.md)`, `[`getCanvas`](../../maps/layer/BasicLayer.md)`, `[`getIcon`](../../maps/layer/BasicLayer.md)`, `[`getName`](../../maps/layer/BasicLayer.md)`, `[`getProperties`](../../maps/layer/BasicLayer.md)`, `[`getProperty`](../../maps/layer/BasicLayer.md)`, `[`getProperty`](../../maps/layer/BasicLayer.md)`, `[`getPropertyChangeListeners`](../../maps/layer/BasicLayer.md)`, `[`getPropertyChangeListeners`](../../maps/layer/BasicLayer.md)`, `[`getProviderID`](../../maps/layer/BasicLayer.md)`, `[`getSRID`](../../maps/layer/BasicLayer.md)`, `[`isVisible`](../../maps/layer/BasicLayer.md)`, `[`removed`](../../maps/layer/BasicLayer.md)`, `[`removePropertyChangeListener`](../../maps/layer/BasicLayer.md)`, `[`removePropertyChangeListener`](../../maps/layer/BasicLayer.md)`, `[`repaint`](../../maps/layer/BasicLayer.md)`, `[`setCanvas`](../../maps/layer/BasicLayer.md)`, `[`setName`](../../maps/layer/BasicLayer.md)`, `[`setProperty`](../../maps/layer/BasicLayer.md)`, `[`setProviderID`](../../maps/layer/BasicLayer.md)`, `[`setSRID`](../../maps/layer/BasicLayer.md)`, `[`setVisible`](../../maps/layer/BasicLayer.md)`, `[`toXMLElement`](../../maps/layer/BasicLayer.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.nfe.vis.mapcanvas.behavior.[BehavioralLayer](../behavior/BehavioralLayer.md)

      [`refresh`](../behavior/BehavioralLayer.md)

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](../../maps/core/Layer.md)

      [`added`](../../maps/core/Layer.md)`, `[`fromXMLElement`](../../maps/core/Layer.md)`, `[`getCanvas`](../../maps/core/Layer.md)`, `[`getIcon`](../../maps/core/Layer.md)`, `[`getName`](../../maps/core/Layer.md)`, `[`getProviderID`](../../maps/core/Layer.md)`, `[`getSRID`](../../maps/core/Layer.md)`, `[`isVisible`](../../maps/core/Layer.md)`, `[`removed`](../../maps/core/Layer.md)`, `[`repaint`](../../maps/core/Layer.md)`, `[`setCanvas`](../../maps/core/Layer.md)`, `[`setName`](../../maps/core/Layer.md)`, `[`setProviderID`](../../maps/core/Layer.md)`, `[`setSRID`](../../maps/core/Layer.md)`, `[`setVisible`](../../maps/core/Layer.md)`, `[`toXMLElement`](../../maps/core/Layer.md)

<!-- -->

- - ### Constructor Detail

    - #### NFEFeatureLayerRenderer

          public NFEFeatureLayerRenderer(MapCanvas canvas,
                                         NFEModel model,
                                         long featLayerId)

      Allocates a new feature layer renderer
      Parameters:
      `canvas` - the MapCanvas where the layer will be rendered

      `model` - the feature layer's model

      `featLayerId` - the feature layer's ID

  <!-- -->

  - ### Method Detail

    - #### getFeatureLayer

          public NFEFeatureLayer getFeatureLayer()

      Gets the rendered feature layer
      Returns:
      a feature layer instance

    <!-- -->

    - #### getModel

          public NFEModel getModel()

      Gets the NFE model
      Returns:
      an NFE model instance

    <!-- -->

    - #### isShowFlow

          public boolean isShowFlow()

      Tells whether the line features flow is shown
      Returns:
      true if the flow is shown

    <!-- -->

    - #### setShowFlow

          public void setShowFlow(boolean showFlow)

      Sets whether the line features flow should be shown
      Parameters:
      `showFlow` - true if the flow is shown

    <!-- -->

    - #### synchronizeWithModel

          public void synchronizeWithModel()

      Updates the state to reflect the feature layer's state and refreshes the view

    <!-- -->

    - #### modelObjectAdded

          public void modelObjectAdded(NFEModelObjectEvent event)

      Description copied from interface: [`NFEModelListener`](../../../model/event/NFEModelListener.md)
      Invoked when a model object has been added
      Specified by:
      [`modelObjectAdded`](../../../model/event/NFEModelListener.md) in interface [`NFEModelListener`](../../../model/event/NFEModelListener.md)

      Parameters:
      `event` - contains a reference to the model object that has been added

    <!-- -->

    - #### modelObjectsAdded

          public void modelObjectsAdded(NFEModelObjectsEvent event)

      Description copied from interface: [`NFEModelListener`](../../../model/event/NFEModelListener.md)
      Invoked when one or more model objects have been added
      Specified by:
      [`modelObjectsAdded`](../../../model/event/NFEModelListener.md) in interface [`NFEModelListener`](../../../model/event/NFEModelListener.md)

      Parameters:
      `event` - contains a collection of references to the model objects that have been added

    <!-- -->

    - #### modelObjectRemoved

          public void modelObjectRemoved(NFEModelObjectEvent event)

      Description copied from interface: [`NFEModelListener`](../../../model/event/NFEModelListener.md)
      Invoked when a model object has been removed
      Specified by:
      [`modelObjectRemoved`](../../../model/event/NFEModelListener.md) in interface [`NFEModelListener`](../../../model/event/NFEModelListener.md)

      Parameters:
      `event` - contains a reference to the model object that has been removed

    <!-- -->

    - #### modelObjectsRemoved

          public void modelObjectsRemoved(NFEModelObjectsEvent event)

      Description copied from interface: [`NFEModelListener`](../../../model/event/NFEModelListener.md)
      Invoked when one or more model objects have been removed
      Specified by:
      [`modelObjectsRemoved`](../../../model/event/NFEModelListener.md) in interface [`NFEModelListener`](../../../model/event/NFEModelListener.md)

      Parameters:
      `event` - contains a collection of references to the model objects that have been removed

    <!-- -->

    - #### modelObjectPropertyChanged

          public void modelObjectPropertyChanged(NFEModelObjectPropertyChangedEvent event)

      Description copied from interface: [`NFEModelListener`](../../../model/event/NFEModelListener.md)
      Invoked when a model object's property has been changed
      Specified by:
      [`modelObjectPropertyChanged`](../../../model/event/NFEModelListener.md) in interface [`NFEModelListener`](../../../model/event/NFEModelListener.md)

      Parameters:
      `event` - contains a reference to the model objects which property has been changed and the name and previous value of the changed property

    <!-- -->

    - #### selectFeatures

          public void selectFeatures(java.util.Collection<java.lang.Long> featureIds)

      Description copied from interface: [`FeatureSelectableLayer`](../behavior/FeatureSelectableLayer.md)
      Selects a group of features. If there were selected features selected, they are still selected.
      Specified by:
      [`selectFeatures`](../behavior/FeatureSelectableLayer.md) in interface [`FeatureSelectableLayer`](../behavior/FeatureSelectableLayer.md)

      Parameters:
      `featureIds` - a collection containing the IDs of the features to be selected

    <!-- -->

    - #### setFeatureSelection

          public void setFeatureSelection(java.util.Collection<java.lang.Long> featureIds)

      Description copied from interface: [`FeatureSelectableLayer`](../behavior/FeatureSelectableLayer.md)
      Sets the given features as selected. Previously selected features are unselected
      Specified by:
      [`setFeatureSelection`](../behavior/FeatureSelectableLayer.md) in interface [`FeatureSelectableLayer`](../behavior/FeatureSelectableLayer.md)

      Parameters:
      `featureIds` - a collection of feature IDs to be selected

    <!-- -->

    - #### getSelectedFeatures

          public java.util.Collection<NFEFeature> getSelectedFeatures()

      Description copied from interface: [`FeatureSelectableLayer`](../behavior/FeatureSelectableLayer.md)
      Gets the currently selected features
      Specified by:
      [`getSelectedFeatures`](../behavior/FeatureSelectableLayer.md) in interface [`FeatureSelectableLayer`](../behavior/FeatureSelectableLayer.md)

      Returns:
      a collection of features

    <!-- -->

    - #### setSelection

          public boolean setSelection(java.util.List<GeoObject> selectedGeoObjects)

      Description copied from interface: [`SelectableLayer`](../../maps/core/SelectableLayer.md)
      Clears selection before setting the provided objects as selected
      Specified by:

      [`setSelection`](../../maps/core/SelectableLayer.md) in interface [`SelectableLayer`](../../maps/core/SelectableLayer.md)

      Overrides:

      [`setSelection`](NFERenderer.md) in class [`NFERenderer`](NFERenderer.md)`<`[`NFEFeatureElementGeoObject`](../../../model/spatial/NFEFeatureElementGeoObject.md)`>`

      Returns:

    <!-- -->

    - #### select

          public boolean select(java.util.List<GeoObject> objs)

      Description copied from interface: [`SelectableLayer`](../../maps/core/SelectableLayer.md)
      Adds the provided objects to the selection list
      Specified by:

      [`select`](../../maps/core/SelectableLayer.md) in interface [`SelectableLayer`](../../maps/core/SelectableLayer.md)

      Overrides:

      [`select`](NFERenderer.md) in class [`NFERenderer`](NFERenderer.md)`<`[`NFEFeatureElementGeoObject`](../../../model/spatial/NFEFeatureElementGeoObject.md)`>`

      Returns:

    <!-- -->

    - #### clearSelection

          public boolean clearSelection()

      Description copied from interface: [`SelectableLayer`](../../maps/core/SelectableLayer.md)
      Clears all selected objects
      Specified by:
      [`clearSelection`](../../maps/core/SelectableLayer.md) in interface [`SelectableLayer`](../../maps/core/SelectableLayer.md)

      Overrides:
      [`clearSelection`](NFERenderer.md) in class [`NFERenderer`](NFERenderer.md)`<`[`NFEFeatureElementGeoObject`](../../../model/spatial/NFEFeatureElementGeoObject.md)`>`

      Returns:
      true if changes where made

    <!-- -->

    - #### createPreview

          public ManipulationPreview createPreview(java.util.Collection<Manipulation<NFENetworkElement>> manipulations)

      Creates a preview for the given manipulations to network elements
      Parameters:
      `manipulations` - a collection of network element manipulations

      Returns:
      a manipulation preview

    <!-- -->

    - #### deleteSelection

          public void deleteSelection()

      Description copied from interface: [`SelectionEditableLayer`](../behavior/SelectionEditableLayer.md)
      Deletes the elements currently selected
      Specified by:
      [`deleteSelection`](../behavior/SelectionEditableLayer.md) in interface [`SelectionEditableLayer`](../behavior/SelectionEditableLayer.md)

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

- [Prev Class](ContextualMenuHandler.md)
- [Next Class](NFEManipulableFeatureLayerRenderer.md)

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
