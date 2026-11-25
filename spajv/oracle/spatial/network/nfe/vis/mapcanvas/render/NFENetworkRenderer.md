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

- [Prev Class](NFEManipulableFeatureLayerRenderer.md)
- [Next Class](NFEPathRenderer.md)

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

## Class NFENetworkRenderer

- java.lang.Object

- - [oracle.spatial.network.nfe.vis.maps.layer.BasicLayer](../../maps/layer/BasicLayer.md)

  - - [oracle.spatial.network.nfe.vis.mapcanvas.render.NFERenderer](NFERenderer.md)\<[NFENetworkElementGeoObject](../../../model/spatial/NFENetworkElementGeoObject.md)\>

    - - oracle.spatial.network.nfe.vis.mapcanvas.render.NFENetworkRenderer

<!-- -->

- All Implemented Interfaces:
  java.util.EventListener, javax.swing.event.ChangeListener, [NFEModelListener](../../../model/event/NFEModelListener.md), [BehavioralLayer](../behavior/BehavioralLayer.md), [ManipulableLayer](../behavior/manipulate/ManipulableLayer.md), [VertexEditableLayer](../behavior/VertexEditableLayer.md), [GeoObjectLayer](../../maps/core/GeoObjectLayer.md), [HoverableLayer](../../maps/core/HoverableLayer.md), [Layer](../../maps/core/Layer.md), [SelectableLayer](../../maps/core/SelectableLayer.md)

  ------------------------------------------------------------------------



      public class NFENetworkRenderer
      extends NFERenderer<NFENetworkElementGeoObject>
      implements NFEModelListener, ManipulableLayer, VertexEditableLayer

  Layer used for rendering network elements (nodes and links). It is automatically subscribed to the model's network to draw or erase network elements as they are added, modified or removed. Support is provided for manipulating network elements.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.spatial.network.nfe.model.event.[NFEModelListener](../../../model/event/NFEModelListener.md)

      [`METHOD_MODEL_OBJECT_ADDED`](../../../model/event/NFEModelListener.md)`, `[`METHOD_MODEL_OBJECT_REMOVED`](../../../model/event/NFEModelListener.md)`, `[`METHOD_MODEL_OBJECTS_ADDED`](../../../model/event/NFEModelListener.md)`, `[`METHOD_MODEL_OBJECTS_REMOVED`](../../../model/event/NFEModelListener.md)`, `[`METHOD_PROPERTY_CHANGED`](../../../model/event/NFEModelListener.md)

    <!-- -->

    - ### Fields inherited from interface oracle.spatial.network.nfe.vis.mapcanvas.behavior.manipulate.[ManipulableLayer](../behavior/manipulate/ManipulableLayer.md)

      [`TRANS_NONE`](../behavior/manipulate/ManipulableLayer.md)`, `[`TRANS_PULL`](../behavior/manipulate/ManipulableLayer.md)`, `[`TRANS_TRANSLATE`](../behavior/manipulate/ManipulableLayer.md)

    <!-- -->

    - ### Fields inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](../../maps/core/Layer.md)

      [`PROPERTY_NAME`](../../maps/core/Layer.md)`, `[`PROPERTY_PROVIDERID`](../../maps/core/Layer.md)`, `[`PROPERTY_SRID`](../../maps/core/Layer.md)`, `[`PROPERTY_VISIBLE`](../../maps/core/Layer.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                        |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `NFENetworkRenderer``(`[`MapCanvas`](../../maps/core/MapCanvas.md)` canvas, `[`NFEModel`](../../../model/NFEModel.md)` model)`<br>Allocates a new network renderer |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                           | Method and Description                                                                                                                                                                                                                                                                        |
    |-----------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                      | `addFeatureLayerRenderer``(`[`NFEFeatureLayerRenderer`](NFEFeatureLayerRenderer.md)` flRenderer)`<br>Associates a feature layer renderer                                                                                                                                                      |
    | `boolean`                                                                   | `addVertex``(`[`GeoObject`](../../maps/core/GeoObject.md)` geoObj, JGeometrySegmentPoint snapPoint)`<br>Adds a vertex to the given GeoObject at the specified snap point                                                                                                                      |
    | `boolean`                                                                   | `canAddVertex``(`[`GeoObject`](../../maps/core/GeoObject.md)` geoObj, JGeometrySegmentPoint snapPoint)`<br>Tells whether it is possible to add a new vertex to the GeoObject at the specified snap point                                                                                      |
    | `void`                                                                      | `cancelManipulation``(long manId)`<br>Cancels the given manipulation and releases all the resources related to it                                                                                                                                                                             |
    | `boolean`                                                                   | `finishManipulation``(long manId, java.awt.geom.Point2D dataPoint)`<br>finishes the manipulation identified by the given id.                                                                                                                                                                  |
    | `int`                                                                       | `getApplicableTransformation``(`[`GeoObject`](../../maps/core/GeoObject.md)` geoObj, java.util.Collection<`[`GeoObject`](../../maps/core/GeoObject.md)`> manGeoObjGroup, JGeometrySegmentPoint snapPoint)`<br>Gets manipulation available for the given GeoObject and its current snap point. |
    | `java.util.List<`[`NFEFeatureLayerRenderer`](NFEFeatureLayerRenderer.md)`>` | `getFeatureLayerRenderers``()`<br>Gets all the feature layer renderers associated                                                                                                                                                                                                             |
    | `double[]`                                                                  | `getHandlePoints``(`[`GeoObject`](../../maps/core/GeoObject.md)` geoObj)`<br>Gets the ordinates of the points from which a GeoObject can be manipulated                                                                                                                                       |
    | `java.util.Collection<`[`GeoObject`](../../maps/core/GeoObject.md)`>`       | `getManipulableGeoObjects``()`<br>Gets the layer's GeoObjects that can be manipulated                                                                                                                                                                                                         |
    | [`ManipulationPreview`](../behavior/manipulate/ManipulationPreview.md)      | `getPreview``(long manId)`<br>Gets a preview for a manipulation                                                                                                                                                                                                                               |
    | `JGeometrySegmentPoint`                                                     | `getSnapPoint``(`[`GeoObject`](../../maps/core/GeoObject.md)` geoObj, java.awt.geom.Point2D dataPoint, double tolerance)`<br>Gets the closer GeoObject's snap point to the given point using the tolerance specified                                                                          |
    | `java.util.Collection<`[`GeoObject`](../../maps/core/GeoObject.md)`>`       | `getVertexEditableGeoObjects``()`<br>Gets all the GeoObjects which vertices can be edited                                                                                                                                                                                                     |
    | `double[]`                                                                  | `getVertices``(`[`GeoObject`](../../maps/core/GeoObject.md)` geoObj)`<br>Gets all the vertices of the GeoObject                                                                                                                                                                               |
    | `boolean`                                                                   | `isHidden``()`<br>Tells whether the layer is hidden                                                                                                                                                                                                                                           |
    | `boolean`                                                                   | `isShowFlow``()`<br>Tells whether flow indicators are displayed for links                                                                                                                                                                                                                     |
    | `boolean`                                                                   | `manipulate``(long manId, java.awt.geom.Point2D dataPoint)`<br>Updates the state of a manipulation with the last point.                                                                                                                                                                       |
    | `void`                                                                      | `mapRegionChanged``(`[`MapRegionEvent`](../../maps/core/MapRegionEvent.md)` e)`<br>When the associated canvas's map region is changed, this method is called to notify the layer of the change.                                                                                               |
    | `void`                                                                      | `modelObjectAdded``(`[`NFEModelObjectEvent`](../../../model/event/NFEModelObjectEvent.md)` event)`<br>Invoked when a model object has been added                                                                                                                                              |
    | `void`                                                                      | `modelObjectPropertyChanged``(`[`NFEModelObjectPropertyChangedEvent`](../../../model/event/NFEModelObjectPropertyChangedEvent.md)` event)`<br>Invoked when a model object's property has been changed                                                                                         |
    | `void`                                                                      | `modelObjectRemoved``(`[`NFEModelObjectEvent`](../../../model/event/NFEModelObjectEvent.md)` event)`<br>Invoked when a model object has been removed                                                                                                                                          |
    | `void`                                                                      | `modelObjectsAdded``(`[`NFEModelObjectsEvent`](../../../model/event/NFEModelObjectsEvent.md)` event)`<br>Invoked when one or more model objects have been added                                                                                                                               |
    | `void`                                                                      | `modelObjectsRemoved``(`[`NFEModelObjectsEvent`](../../../model/event/NFEModelObjectsEvent.md)` event)`<br>Invoked when one or more model objects have been removed                                                                                                                           |
    | `void`                                                                      | `refresh``()`<br>Refreshes the current data window                                                                                                                                                                                                                                            |
    | `boolean`                                                                   | `removeFeatureLayerRenderer``(`[`NFEFeatureLayerRenderer`](NFEFeatureLayerRenderer.md)` flRenderer)`<br>Removes the association to a feature layer renderer                                                                                                                                   |
    | `long`                                                                      | `render``(java.awt.Graphics2D graphics)`<br>Renders the layer contents to the given Graphics.                                                                                                                                                                                                 |
    | `void`                                                                      | `setHidden``(boolean hidden)`<br>Sets whether the layer is hidden or not                                                                                                                                                                                                                      |
    | `void`                                                                      | `setShowFlow``(boolean showFlow)`<br>Sets whether flow indicators are displayed for links                                                                                                                                                                                                     |
    | `long`                                                                      | `startManipulation``(`[`GeoObject`](../../maps/core/GeoObject.md)` geoObj, java.util.Collection<`[`GeoObject`](../../maps/core/GeoObject.md)`> manGeoObjGroup, JGeometrySegmentPoint snapPoint, int transformation)`<br>Starts a manipulation session.                                        |
    | `void`                                                                      | `synchronizeWithModel``()`<br>Refreshes the current state to refresh the state of the model's network                                                                                                                                                                                         |

    - ### Methods inherited from class oracle.spatial.network.nfe.vis.mapcanvas.render.[NFERenderer](NFERenderer.md)

      [`addContextualMenuHandler`](NFERenderer.md)`, `[`addSelectionListener`](NFERenderer.md)`, `[`clear`](NFERenderer.md)`, `[`clearHover`](NFERenderer.md)`, `[`clearSelection`](NFERenderer.md)`, `[`getDataMBR`](NFERenderer.md)`, `[`getFullExtent`](NFERenderer.md)`, `[`getGeoObject`](NFERenderer.md)`, `[`getHover`](NFERenderer.md)`, `[`getImageOpacityAlpha`](NFERenderer.md)`, `[`getObject`](NFERenderer.md)`, `[`getObjects`](NFERenderer.md)`, `[`getSelection`](NFERenderer.md)`, `[`getSelection`](NFERenderer.md)`, `[`getSnapPoint`](NFERenderer.md)`, `[`getTolerance`](NFERenderer.md)`, `[`handleEvent`](NFERenderer.md)`, `[`hitTest`](NFERenderer.md)`, `[`hitTest`](NFERenderer.md)`, `[`isHover`](NFERenderer.md)`, `[`isSelected`](NFERenderer.md)`, `[`numHovered`](NFERenderer.md)`, `[`numSelected`](NFERenderer.md)`, `[`refresh`](NFERenderer.md)`, `[`removeContextualMenuHandler`](NFERenderer.md)`, `[`removeSelectionListener`](NFERenderer.md)`, `[`select`](NFERenderer.md)`, `[`setHover`](NFERenderer.md)`, `[`setImageOpacityAlpha`](NFERenderer.md)`, `[`setSelection`](NFERenderer.md)`, `[`stateChanged`](NFERenderer.md)`, `[`unselect`](NFERenderer.md)`, `[`update`](NFERenderer.md)

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

    - #### NFENetworkRenderer

          public NFENetworkRenderer(MapCanvas canvas,
                                    NFEModel model)

      Allocates a new network renderer
      Parameters:
      `canvas` - the MapCanvas where the layer will be rendered

      `model` - the model containing the network to be rendered

  <!-- -->

  - ### Method Detail

    - #### synchronizeWithModel

          public void synchronizeWithModel()

      Refreshes the current state to refresh the state of the model's network

    <!-- -->

    - #### isShowFlow

          public boolean isShowFlow()

      Tells whether flow indicators are displayed for links
      Returns:
      true if flow is shown

    <!-- -->

    - #### setShowFlow

          public void setShowFlow(boolean showFlow)

      Sets whether flow indicators are displayed for links
      Parameters:
      `showFlow` - true if flow should be shown

    <!-- -->

    - #### getFeatureLayerRenderers

          public java.util.List<NFEFeatureLayerRenderer> getFeatureLayerRenderers()

      Gets all the feature layer renderers associated
      Returns:
      a list of feature layer renderers

    <!-- -->

    - #### addFeatureLayerRenderer

          public void addFeatureLayerRenderer(NFEFeatureLayerRenderer flRenderer)

      Associates a feature layer renderer
      Parameters:
      `flRenderer` - a feature layer renderer

    <!-- -->

    - #### removeFeatureLayerRenderer

          public boolean removeFeatureLayerRenderer(NFEFeatureLayerRenderer flRenderer)

      Removes the association to a feature layer renderer
      Parameters:
      `flRenderer` - a feature layer renderer

      Returns:
      true if the association was removed

    <!-- -->

    - #### isHidden

          public boolean isHidden()

      Tells whether the layer is hidden
      Returns:
      true if it is hidden

    <!-- -->

    - #### setHidden

          public void setHidden(boolean hidden)

      Sets whether the layer is hidden or not
      Parameters:
      `hidden` - true if it should be hidden

    <!-- -->

    - #### refresh

          public void refresh()

      Description copied from class: [`NFERenderer`](NFERenderer.md)
      Refreshes the current data window
      Specified by:
      [`refresh`](../behavior/BehavioralLayer.md) in interface [`BehavioralLayer`](../behavior/BehavioralLayer.md)

      Overrides:
      [`refresh`](NFERenderer.md) in class [`NFERenderer`](NFERenderer.md)`<`[`NFENetworkElementGeoObject`](../../../model/spatial/NFENetworkElementGeoObject.md)`>`

    <!-- -->

    - #### mapRegionChanged

          public void mapRegionChanged(MapRegionEvent e)

      Description copied from interface: [`Layer`](../../maps/core/Layer.md)
      When the associated canvas's map region is changed, this method is called to notify the layer of the change. Note that either a device window change (as a result of resizing the application window) or a data window change can cause this method to be invoked. Query the canvas' MapRegion object to get the changed values. Inside a mapRegionChanged() implementation, the layer typically needs to update its data contents accordingly.
      Specified by:
      [`mapRegionChanged`](../../maps/core/Layer.md) in interface [`Layer`](../../maps/core/Layer.md)

      Overrides:
      [`mapRegionChanged`](NFERenderer.md) in class [`NFERenderer`](NFERenderer.md)`<`[`NFENetworkElementGeoObject`](../../../model/spatial/NFENetworkElementGeoObject.md)`>`

    <!-- -->

    - #### render

          public long render(java.awt.Graphics2D graphics)

      Description copied from interface: [`Layer`](../../maps/core/Layer.md)
      Renders the layer contents to the given Graphics.
      Specified by:
      [`render`](../../maps/core/Layer.md) in interface [`Layer`](../../maps/core/Layer.md)

      Overrides:
      [`render`](NFERenderer.md) in class [`NFERenderer`](NFERenderer.md)`<`[`NFENetworkElementGeoObject`](../../../model/spatial/NFENetworkElementGeoObject.md)`>`

      Parameters:
      `graphics` - the graphics object

      Returns:
      the rendering time in milliseconds.

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

    - #### getManipulableGeoObjects

          public java.util.Collection<GeoObject> getManipulableGeoObjects()

      Description copied from interface: [`ManipulableLayer`](../behavior/manipulate/ManipulableLayer.md)
      Gets the layer's GeoObjects that can be manipulated
      Specified by:
      [`getManipulableGeoObjects`](../behavior/manipulate/ManipulableLayer.md) in interface [`ManipulableLayer`](../behavior/manipulate/ManipulableLayer.md)

      Returns:
      a collection of GeoObjects

    <!-- -->

    - #### getHandlePoints

          public double[] getHandlePoints(GeoObject geoObj)

      Description copied from interface: [`ManipulableLayer`](../behavior/manipulate/ManipulableLayer.md)
      Gets the ordinates of the points from which a GeoObject can be manipulated
      Specified by:
      [`getHandlePoints`](../behavior/manipulate/ManipulableLayer.md) in interface [`ManipulableLayer`](../behavior/manipulate/ManipulableLayer.md)

      Parameters:
      `geoObj` - a GeoObject

      Returns:
      an array of ordinates in model's coordinate system

    <!-- -->

    - #### getSnapPoint

          public JGeometrySegmentPoint getSnapPoint(GeoObject geoObj,
                                                    java.awt.geom.Point2D dataPoint,
                                                    double tolerance)

      Description copied from interface: [`ManipulableLayer`](../behavior/manipulate/ManipulableLayer.md)
      Gets the closer GeoObject's snap point to the given point using the tolerance specified
      Specified by:
      [`getSnapPoint`](../behavior/manipulate/ManipulableLayer.md) in interface [`ManipulableLayer`](../behavior/manipulate/ManipulableLayer.md)

      Specified by:
      [`getSnapPoint`](../behavior/VertexEditableLayer.md) in interface [`VertexEditableLayer`](../behavior/VertexEditableLayer.md)

      Parameters:
      `geoObj` - a GeoObject

      `dataPoint` - a point in model's coordinate system

      `tolerance` - a tolarence in model's coordinate system

      Returns:
      a segment point relative to the GeoObject's geometry

    <!-- -->

    - #### getApplicableTransformation

          public int getApplicableTransformation(GeoObject geoObj,
                                                 java.util.Collection<GeoObject> manGeoObjGroup,
                                                 JGeometrySegmentPoint snapPoint)

      Description copied from interface: [`ManipulableLayer`](../behavior/manipulate/ManipulableLayer.md)
      Gets manipulation available for the given GeoObject and its current snap point. It is also specified all the GeoObjects that need to be manipulated along with the first GeoObject passed.
      Specified by:
      [`getApplicableTransformation`](../behavior/manipulate/ManipulableLayer.md) in interface [`ManipulableLayer`](../behavior/manipulate/ManipulableLayer.md)

      Parameters:
      `geoObj` - a GeoObject

      `manGeoObjGroup` - a collection containing more GeoObjects to be manipulated. It can be null

      `snapPoint` - a segment point relative to the GeoObject's geometry

      Returns:
      a manipulation code

    <!-- -->

    - #### startManipulation

          public long startManipulation(GeoObject geoObj,
                                        java.util.Collection<GeoObject> manGeoObjGroup,
                                        JGeometrySegmentPoint snapPoint,
                                        int transformation)

      Description copied from interface: [`ManipulableLayer`](../behavior/manipulate/ManipulableLayer.md)
      Starts a manipulation session. The manipulation will be performed over the give GeoObject and the GeoObject group passed.
      Specified by:
      [`startManipulation`](../behavior/manipulate/ManipulableLayer.md) in interface [`ManipulableLayer`](../behavior/manipulate/ManipulableLayer.md)

      Parameters:
      `geoObj` - the target GeoObject to be manipulated

      `manGeoObjGroup` - a group of GeoObjects to be manipulated

      `snapPoint` - a segment point relative to the GeoObject's geometry

      `transformation` - the type of manipulation to be performed

      Returns:
      a manipulation session id

    <!-- -->

    - #### finishManipulation

          public boolean finishManipulation(long manId,
                                            java.awt.geom.Point2D dataPoint)

      Description copied from interface: [`ManipulableLayer`](../behavior/manipulate/ManipulableLayer.md)
      finishes the manipulation identified by the given id. The last mouse point is specified.
      Specified by:
      [`finishManipulation`](../behavior/manipulate/ManipulableLayer.md) in interface [`ManipulableLayer`](../behavior/manipulate/ManipulableLayer.md)

      Parameters:
      `manId` - the manipulation session id

      `dataPoint` - the last point for the manipulation in model's coordinate system

      Returns:
      true if the manipulation was performed successfully

    <!-- -->

    - #### manipulate

          public boolean manipulate(long manId,
                                    java.awt.geom.Point2D dataPoint)

      Description copied from interface: [`ManipulableLayer`](../behavior/manipulate/ManipulableLayer.md)
      Updates the state of a manipulation with the last point. It is useful if a live preview has to be shown.
      Specified by:
      [`manipulate`](../behavior/manipulate/ManipulableLayer.md) in interface [`ManipulableLayer`](../behavior/manipulate/ManipulableLayer.md)

      Parameters:
      `manId` - a manipulation session id

      `dataPoint` - the last user point (it may be a mouse point) in model's coordinate system

      Returns:
      true if the manipulation state was updated successfully

    <!-- -->

    - #### cancelManipulation

          public void cancelManipulation(long manId)

      Description copied from interface: [`ManipulableLayer`](../behavior/manipulate/ManipulableLayer.md)
      Cancels the given manipulation and releases all the resources related to it
      Specified by:
      [`cancelManipulation`](../behavior/manipulate/ManipulableLayer.md) in interface [`ManipulableLayer`](../behavior/manipulate/ManipulableLayer.md)

      Parameters:
      `manId` - a manipulation session id

    <!-- -->

    - #### getPreview

          public ManipulationPreview getPreview(long manId)

      Description copied from interface: [`ManipulableLayer`](../behavior/manipulate/ManipulableLayer.md)
      Gets a preview for a manipulation
      Specified by:
      [`getPreview`](../behavior/manipulate/ManipulableLayer.md) in interface [`ManipulableLayer`](../behavior/manipulate/ManipulableLayer.md)

      Parameters:
      `manId` - a manipulation session id

      Returns:
      a manipulation preview object

    <!-- -->

    - #### getVertexEditableGeoObjects

          public java.util.Collection<GeoObject> getVertexEditableGeoObjects()

      Description copied from interface: [`VertexEditableLayer`](../behavior/VertexEditableLayer.md)
      Gets all the GeoObjects which vertices can be edited
      Specified by:
      [`getVertexEditableGeoObjects`](../behavior/VertexEditableLayer.md) in interface [`VertexEditableLayer`](../behavior/VertexEditableLayer.md)

      Returns:
      a collection of GeoObjects

    <!-- -->

    - #### getVertices

          public double[] getVertices(GeoObject geoObj)

      Description copied from interface: [`VertexEditableLayer`](../behavior/VertexEditableLayer.md)
      Gets all the vertices of the GeoObject
      Specified by:
      [`getVertices`](../behavior/VertexEditableLayer.md) in interface [`VertexEditableLayer`](../behavior/VertexEditableLayer.md)

      Parameters:
      `geoObj` - a GeoObject

      Returns:
      an array containing the ordinates of the GeoObject's vertices

    <!-- -->

    - #### canAddVertex

          public boolean canAddVertex(GeoObject geoObj,
                                      JGeometrySegmentPoint snapPoint)

      Description copied from interface: [`VertexEditableLayer`](../behavior/VertexEditableLayer.md)
      Tells whether it is possible to add a new vertex to the GeoObject at the specified snap point
      Specified by:
      [`canAddVertex`](../behavior/VertexEditableLayer.md) in interface [`VertexEditableLayer`](../behavior/VertexEditableLayer.md)

      Parameters:
      `geoObj` - a GeoObject

      `snapPoint` - a segment point relative to the GeoObject's geometry

      Returns:
      true if it is possible to add a new vertex

    <!-- -->

    - #### addVertex

          public boolean addVertex(GeoObject geoObj,
                                   JGeometrySegmentPoint snapPoint)

      Description copied from interface: [`VertexEditableLayer`](../behavior/VertexEditableLayer.md)
      Adds a vertex to the given GeoObject at the specified snap point
      Specified by:
      [`addVertex`](../behavior/VertexEditableLayer.md) in interface [`VertexEditableLayer`](../behavior/VertexEditableLayer.md)

      Parameters:
      `geoObj` - a GeoObject

      `snapPoint` - a segment point relative to the GeoObject's geometry

      Returns:
      true if the vertex was successfully added

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

- [Prev Class](NFEManipulableFeatureLayerRenderer.md)
- [Next Class](NFEPathRenderer.md)

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
