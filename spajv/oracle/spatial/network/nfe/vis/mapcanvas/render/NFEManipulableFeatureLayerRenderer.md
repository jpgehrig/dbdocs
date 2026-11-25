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

- [Prev Class](NFEFeatureLayerRenderer.md)
- [Next Class](NFENetworkRenderer.md)

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

## Class NFEManipulableFeatureLayerRenderer

- java.lang.Object

- - [oracle.spatial.network.nfe.vis.maps.layer.BasicLayer](../../maps/layer/BasicLayer.md)

  - - [oracle.spatial.network.nfe.vis.mapcanvas.render.NFERenderer](NFERenderer.md)\<[NFEFeatureElementGeoObject](../../../model/spatial/NFEFeatureElementGeoObject.md)\>

    - - [oracle.spatial.network.nfe.vis.mapcanvas.render.NFEFeatureLayerRenderer](NFEFeatureLayerRenderer.md)

      - - oracle.spatial.network.nfe.vis.mapcanvas.render.NFEManipulableFeatureLayerRenderer

<!-- -->

- All Implemented Interfaces:
  java.util.EventListener, javax.swing.event.ChangeListener, [NFEModelListener](../../../model/event/NFEModelListener.md), [BehavioralLayer](../behavior/BehavioralLayer.md), [FeatureSelectableLayer](../behavior/FeatureSelectableLayer.md), [ManipulableLayer](../behavior/manipulate/ManipulableLayer.md), [SelectionEditableLayer](../behavior/SelectionEditableLayer.md), [GeoObjectLayer](../../maps/core/GeoObjectLayer.md), [HoverableLayer](../../maps/core/HoverableLayer.md), [Layer](../../maps/core/Layer.md), [SelectableLayer](../../maps/core/SelectableLayer.md)

  ------------------------------------------------------------------------



      public class NFEManipulableFeatureLayerRenderer
      extends NFEFeatureLayerRenderer
      implements ManipulableLayer

  A manipulable feature layer renderer.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.spatial.network.nfe.vis.mapcanvas.behavior.manipulate.[ManipulableLayer](../behavior/manipulate/ManipulableLayer.md)

      [`TRANS_NONE`](../behavior/manipulate/ManipulableLayer.md)`, `[`TRANS_PULL`](../behavior/manipulate/ManipulableLayer.md)`, `[`TRANS_TRANSLATE`](../behavior/manipulate/ManipulableLayer.md)

    <!-- -->

    - ### Fields inherited from interface oracle.spatial.network.nfe.model.event.[NFEModelListener](../../../model/event/NFEModelListener.md)

      [`METHOD_MODEL_OBJECT_ADDED`](../../../model/event/NFEModelListener.md)`, `[`METHOD_MODEL_OBJECT_REMOVED`](../../../model/event/NFEModelListener.md)`, `[`METHOD_MODEL_OBJECTS_ADDED`](../../../model/event/NFEModelListener.md)`, `[`METHOD_MODEL_OBJECTS_REMOVED`](../../../model/event/NFEModelListener.md)`, `[`METHOD_PROPERTY_CHANGED`](../../../model/event/NFEModelListener.md)

    <!-- -->

    - ### Fields inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](../../maps/core/Layer.md)

      [`PROPERTY_NAME`](../../maps/core/Layer.md)`, `[`PROPERTY_PROVIDERID`](../../maps/core/Layer.md)`, `[`PROPERTY_SRID`](../../maps/core/Layer.md)`, `[`PROPERTY_VISIBLE`](../../maps/core/Layer.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                            |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `NFEManipulableFeatureLayerRenderer``(`[`MapCanvas`](../../maps/core/MapCanvas.md)` canvas, `[`NFEModel`](../../../model/NFEModel.md)` model, long featLayerId)`<br>Allocates a new manipulable feature layer renderer |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                      | Method and Description                                                                                                                                                                                                                                                                        |
    |------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                 | `cancelManipulation``(long manId)`<br>Cancels the given manipulation and releases all the resources related to it                                                                                                                                                                             |
    | `boolean`                                                              | `finishManipulation``(long manId, java.awt.geom.Point2D dataPoint)`<br>finishes the manipulation identified by the given id.                                                                                                                                                                  |
    | `int`                                                                  | `getApplicableTransformation``(`[`GeoObject`](../../maps/core/GeoObject.md)` geoObj, java.util.Collection<`[`GeoObject`](../../maps/core/GeoObject.md)`> manGeoObjGroup, JGeometrySegmentPoint snapPoint)`<br>Gets manipulation available for the given GeoObject and its current snap point. |
    | `double[]`                                                             | `getHandlePoints``(`[`GeoObject`](../../maps/core/GeoObject.md)` geoObj)`<br>Gets the ordinates of the points from which a GeoObject can be manipulated                                                                                                                                       |
    | `java.util.Collection<`[`GeoObject`](../../maps/core/GeoObject.md)`>`  | `getManipulableGeoObjects``()`<br>Gets the layer's GeoObjects that can be manipulated                                                                                                                                                                                                         |
    | [`ManipulationPreview`](../behavior/manipulate/ManipulationPreview.md) | `getPreview``(long manId)`<br>Gets a preview for a manipulation                                                                                                                                                                                                                               |
    | `JGeometrySegmentPoint`                                                | `getSnapPoint``(`[`GeoObject`](../../maps/core/GeoObject.md)` geoObj, java.awt.geom.Point2D dataPoint, double tolerance)`<br>Gets the closer GeoObject's snap point to the given point using the tolerance specified                                                                          |
    | `boolean`                                                              | `manipulate``(long manId, java.awt.geom.Point2D dataPoint)`<br>Updates the state of a manipulation with the last point.                                                                                                                                                                       |
    | `long`                                                                 | `startManipulation``(`[`GeoObject`](../../maps/core/GeoObject.md)` geoObj, java.util.Collection<`[`GeoObject`](../../maps/core/GeoObject.md)`> manGeoObjGroup, JGeometrySegmentPoint snapPoint, int transformation)`<br>Starts a manipulation session.                                        |

    - ### Methods inherited from class oracle.spatial.network.nfe.vis.mapcanvas.render.[NFEFeatureLayerRenderer](NFEFeatureLayerRenderer.md)

      [`clearSelection`](NFEFeatureLayerRenderer.md)`, `[`createPreview`](NFEFeatureLayerRenderer.md)`, `[`deleteSelection`](NFEFeatureLayerRenderer.md)`, `[`getFeatureLayer`](NFEFeatureLayerRenderer.md)`, `[`getModel`](NFEFeatureLayerRenderer.md)`, `[`getSelectedFeatures`](NFEFeatureLayerRenderer.md)`, `[`isShowFlow`](NFEFeatureLayerRenderer.md)`, `[`modelObjectAdded`](NFEFeatureLayerRenderer.md)`, `[`modelObjectPropertyChanged`](NFEFeatureLayerRenderer.md)`, `[`modelObjectRemoved`](NFEFeatureLayerRenderer.md)`, `[`modelObjectsAdded`](NFEFeatureLayerRenderer.md)`, `[`modelObjectsRemoved`](NFEFeatureLayerRenderer.md)`, `[`select`](NFEFeatureLayerRenderer.md)`, `[`selectFeatures`](NFEFeatureLayerRenderer.md)`, `[`setFeatureSelection`](NFEFeatureLayerRenderer.md)`, `[`setSelection`](NFEFeatureLayerRenderer.md)`, `[`setShowFlow`](NFEFeatureLayerRenderer.md)`, `[`synchronizeWithModel`](NFEFeatureLayerRenderer.md)

    <!-- -->

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

    - #### NFEManipulableFeatureLayerRenderer

          public NFEManipulableFeatureLayerRenderer(MapCanvas canvas,
                                                    NFEModel model,
                                                    long featLayerId)

      Allocates a new manipulable feature layer renderer
      Parameters:
      `canvas` - the MapCanvas where the layer will be rendered

      `model` - the feature layer's model

      `featLayerId` - the feature layer ID

  <!-- -->

  - ### Method Detail

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

      Parameters:
      `geoObj` - a GeoObject

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

- [Prev Class](NFEFeatureLayerRenderer.md)
- [Next Class](NFENetworkRenderer.md)

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
