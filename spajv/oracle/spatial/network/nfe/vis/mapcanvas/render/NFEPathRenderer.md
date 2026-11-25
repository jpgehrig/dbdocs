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

- [Prev Class](NFENetworkRenderer.md)
- [Next Class](NFEProgressIndicatorLayer.md)

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

## Class NFEPathRenderer

- java.lang.Object

- - [oracle.spatial.network.nfe.vis.maps.layer.BasicLayer](../../maps/layer/BasicLayer.md)

  - - [oracle.spatial.network.nfe.vis.mapcanvas.render.NFERenderer](NFERenderer.md)\<[NFEFeatureElementGeoObject](../../../model/spatial/NFEFeatureElementGeoObject.md)\>

    - - oracle.spatial.network.nfe.vis.mapcanvas.render.NFEPathRenderer

<!-- -->

- All Implemented Interfaces:
  java.util.EventListener, javax.swing.event.ChangeListener, [NFEModelListener](../../../model/event/NFEModelListener.md), [GeoObjectLayer](../../maps/core/GeoObjectLayer.md), [HoverableLayer](../../maps/core/HoverableLayer.md), [Layer](../../maps/core/Layer.md), [SelectableLayer](../../maps/core/SelectableLayer.md)

  ------------------------------------------------------------------------



      public class NFEPathRenderer
      extends NFERenderer<NFEFeatureElementGeoObject>
      implements NFEModelListener

  Layer used for rendering feature paths (nodes and links).

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

    | Constructor and Description                                                                                                                                                                   |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `NFEPathRenderer``(`[`MapCanvas`](../../maps/core/MapCanvas.md)` canvas, `[`NFEModel`](../../../model/NFEModel.md)` model, long pathFeatureId)`<br>/\*\* Allocates a new path layer renderer. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                    | Method and Description                                                                                                                                                                                |
    |------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`NFEFeature`](../../../model/feature/NFEFeature.md) | `getPathFeature``()`<br>Returns the path feature.                                                                                                                                                     |
    | `boolean`                                            | `isShowFlow``()`<br>Tells whether the line features flow is shown.                                                                                                                                    |
    | `void`                                               | `modelObjectAdded``(`[`NFEModelObjectEvent`](../../../model/event/NFEModelObjectEvent.md)` event)`<br>Invoked when a model object has been added                                                      |
    | `void`                                               | `modelObjectPropertyChanged``(`[`NFEModelObjectPropertyChangedEvent`](../../../model/event/NFEModelObjectPropertyChangedEvent.md)` event)`<br>Invoked when a model object's property has been changed |
    | `void`                                               | `modelObjectRemoved``(`[`NFEModelObjectEvent`](../../../model/event/NFEModelObjectEvent.md)` event)`<br>Invoked when a model object has been removed                                                  |
    | `void`                                               | `modelObjectsAdded``(`[`NFEModelObjectsEvent`](../../../model/event/NFEModelObjectsEvent.md)` event)`<br>Invoked when one or more model objects have been added                                       |
    | `void`                                               | `modelObjectsRemoved``(`[`NFEModelObjectsEvent`](../../../model/event/NFEModelObjectsEvent.md)` event)`<br>Invoked when one or more model objects have been removed                                   |
    | `void`                                               | `setShowFlow``(boolean showFlow)`<br>Sets whether the line features flow should be shown.                                                                                                             |
    | `void`                                               | `synchronizeWithModel``()`<br>Updates the state to reflect the feature layer's state and refreshes the view.                                                                                          |

    - ### Methods inherited from class oracle.spatial.network.nfe.vis.mapcanvas.render.[NFERenderer](NFERenderer.md)

      [`addContextualMenuHandler`](NFERenderer.md)`, `[`addSelectionListener`](NFERenderer.md)`, `[`clear`](NFERenderer.md)`, `[`clearHover`](NFERenderer.md)`, `[`clearSelection`](NFERenderer.md)`, `[`getDataMBR`](NFERenderer.md)`, `[`getFullExtent`](NFERenderer.md)`, `[`getGeoObject`](NFERenderer.md)`, `[`getHover`](NFERenderer.md)`, `[`getImageOpacityAlpha`](NFERenderer.md)`, `[`getObject`](NFERenderer.md)`, `[`getObjects`](NFERenderer.md)`, `[`getSelection`](NFERenderer.md)`, `[`getSelection`](NFERenderer.md)`, `[`getSnapPoint`](NFERenderer.md)`, `[`getTolerance`](NFERenderer.md)`, `[`handleEvent`](NFERenderer.md)`, `[`hitTest`](NFERenderer.md)`, `[`hitTest`](NFERenderer.md)`, `[`isHover`](NFERenderer.md)`, `[`isSelected`](NFERenderer.md)`, `[`mapRegionChanged`](NFERenderer.md)`, `[`numHovered`](NFERenderer.md)`, `[`numSelected`](NFERenderer.md)`, `[`refresh`](NFERenderer.md)`, `[`refresh`](NFERenderer.md)`, `[`removeContextualMenuHandler`](NFERenderer.md)`, `[`removeSelectionListener`](NFERenderer.md)`, `[`render`](NFERenderer.md)`, `[`select`](NFERenderer.md)`, `[`setHover`](NFERenderer.md)`, `[`setImageOpacityAlpha`](NFERenderer.md)`, `[`setSelection`](NFERenderer.md)`, `[`stateChanged`](NFERenderer.md)`, `[`unselect`](NFERenderer.md)`, `[`update`](NFERenderer.md)

    <!-- -->

    - ### Methods inherited from class oracle.spatial.network.nfe.vis.maps.layer.[BasicLayer](../../maps/layer/BasicLayer.md)

      [`added`](../../maps/layer/BasicLayer.md)`, `[`addPropertyChangeListener`](../../maps/layer/BasicLayer.md)`, `[`addPropertyChangeListener`](../../maps/layer/BasicLayer.md)`, `[`fromXMLElement`](../../maps/layer/BasicLayer.md)`, `[`getCanvas`](../../maps/layer/BasicLayer.md)`, `[`getIcon`](../../maps/layer/BasicLayer.md)`, `[`getName`](../../maps/layer/BasicLayer.md)`, `[`getProperties`](../../maps/layer/BasicLayer.md)`, `[`getProperty`](../../maps/layer/BasicLayer.md)`, `[`getProperty`](../../maps/layer/BasicLayer.md)`, `[`getPropertyChangeListeners`](../../maps/layer/BasicLayer.md)`, `[`getPropertyChangeListeners`](../../maps/layer/BasicLayer.md)`, `[`getProviderID`](../../maps/layer/BasicLayer.md)`, `[`getSRID`](../../maps/layer/BasicLayer.md)`, `[`isVisible`](../../maps/layer/BasicLayer.md)`, `[`removed`](../../maps/layer/BasicLayer.md)`, `[`removePropertyChangeListener`](../../maps/layer/BasicLayer.md)`, `[`removePropertyChangeListener`](../../maps/layer/BasicLayer.md)`, `[`repaint`](../../maps/layer/BasicLayer.md)`, `[`setCanvas`](../../maps/layer/BasicLayer.md)`, `[`setName`](../../maps/layer/BasicLayer.md)`, `[`setProperty`](../../maps/layer/BasicLayer.md)`, `[`setProviderID`](../../maps/layer/BasicLayer.md)`, `[`setSRID`](../../maps/layer/BasicLayer.md)`, `[`setVisible`](../../maps/layer/BasicLayer.md)`, `[`toXMLElement`](../../maps/layer/BasicLayer.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](../../maps/core/Layer.md)

      [`added`](../../maps/core/Layer.md)`, `[`fromXMLElement`](../../maps/core/Layer.md)`, `[`getCanvas`](../../maps/core/Layer.md)`, `[`getIcon`](../../maps/core/Layer.md)`, `[`getName`](../../maps/core/Layer.md)`, `[`getProviderID`](../../maps/core/Layer.md)`, `[`getSRID`](../../maps/core/Layer.md)`, `[`isVisible`](../../maps/core/Layer.md)`, `[`removed`](../../maps/core/Layer.md)`, `[`repaint`](../../maps/core/Layer.md)`, `[`setCanvas`](../../maps/core/Layer.md)`, `[`setName`](../../maps/core/Layer.md)`, `[`setProviderID`](../../maps/core/Layer.md)`, `[`setSRID`](../../maps/core/Layer.md)`, `[`setVisible`](../../maps/core/Layer.md)`, `[`toXMLElement`](../../maps/core/Layer.md)

<!-- -->

- - ### Constructor Detail

    - #### NFEPathRenderer

          public NFEPathRenderer(MapCanvas canvas,
                                 NFEModel model,
                                 long pathFeatureId)

      /\*\* Allocates a new path layer renderer.
      Parameters:
      `canvas` - the MapCanvas where the layer will be rendered

      `model` - the feature layer's model

      `pathFeatureId` - the feature layer's ID

  <!-- -->

  - ### Method Detail

    - #### synchronizeWithModel

          public void synchronizeWithModel()

      Updates the state to reflect the feature layer's state and refreshes the view.

    <!-- -->

    - #### isShowFlow

          public boolean isShowFlow()

      Tells whether the line features flow is shown.
      Returns:
      true if the flow is shown

    <!-- -->

    - #### setShowFlow

          public void setShowFlow(boolean showFlow)

      Sets whether the line features flow should be shown.
      Parameters:
      `showFlow` - true if the flow is shown

    <!-- -->

    - #### getPathFeature

          public NFEFeature getPathFeature()

      Returns the path feature.
      Returns:
      path feature

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

- [Prev Class](NFENetworkRenderer.md)
- [Next Class](NFEProgressIndicatorLayer.md)

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
