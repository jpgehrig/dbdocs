Skip navigation links

- [Overview](../../../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../../../deprecated-list.md)
- [Index](../../../../../../../../index-all.md)
- [Help](../../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](FeatureLayerManipulationPreview.md)
- [Next Class](Manipulation.md)

<!-- -->

- [Frames](../../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.vis.mapcanvas.behavior.manipulate

## Interface ManipulableLayer

- All Superinterfaces:
  [BehavioralLayer](../BehavioralLayer.md)

  <!-- -->

  All Known Implementing Classes:
  [NFEManipulableFeatureLayerRenderer](../../render/NFEManipulableFeatureLayerRenderer.md), [NFENetworkRenderer](../../render/NFENetworkRenderer.md)

  ------------------------------------------------------------------------



      public interface ManipulableLayer
      extends BehavioralLayer

  Defines a layer which elements can be manipulated.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description             |
    |-------------------|-----------------------------------|
    | `static int`      | `TRANS_NONE`<br>No transformation |
    | `static int`      | `TRANS_PULL`<br>Pulling           |
    | `static int`      | `TRANS_TRANSLATE`<br>Translation  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                        | Method and Description                                                                                                                                                                                                                                                                              |
    |--------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                                   | `cancelManipulation``(long manId)`<br>Cancels the given manipulation and releases all the resources related to it                                                                                                                                                                                   |
    | `boolean`                                                                | `finishManipulation``(long manId, java.awt.geom.Point2D dataPoint)`<br>finishes the manipulation identified by the given id.                                                                                                                                                                        |
    | `int`                                                                    | `getApplicableTransformation``(`[`GeoObject`](../../../maps/core/GeoObject.md)` geoObj, java.util.Collection<`[`GeoObject`](../../../maps/core/GeoObject.md)`> manGeoObjGroup, JGeometrySegmentPoint snapPoint)`<br>Gets manipulation available for the given GeoObject and its current snap point. |
    | `double[]`                                                               | `getHandlePoints``(`[`GeoObject`](../../../maps/core/GeoObject.md)` geoObj)`<br>Gets the ordinates of the points from which a GeoObject can be manipulated                                                                                                                                          |
    | `java.util.Collection<`[`GeoObject`](../../../maps/core/GeoObject.md)`>` | `getManipulableGeoObjects``()`<br>Gets the layer's GeoObjects that can be manipulated                                                                                                                                                                                                               |
    | [`ManipulationPreview`](ManipulationPreview.md)                          | `getPreview``(long manId)`<br>Gets a preview for a manipulation                                                                                                                                                                                                                                     |
    | `JGeometrySegmentPoint`                                                  | `getSnapPoint``(`[`GeoObject`](../../../maps/core/GeoObject.md)` geoObj, java.awt.geom.Point2D dataPoint, double tolerance)`<br>Gets the closer GeoObject's snap point to the given point using the tolerance specified                                                                             |
    | `boolean`                                                                | `manipulate``(long manId, java.awt.geom.Point2D dataPoint)`<br>Updates the state of a manipulation with the last point.                                                                                                                                                                             |
    | `long`                                                                   | `startManipulation``(`[`GeoObject`](../../../maps/core/GeoObject.md)` geoObj, java.util.Collection<`[`GeoObject`](../../../maps/core/GeoObject.md)`> manGeoObjGroup, JGeometrySegmentPoint snapPoint, int transformation)`<br>Starts a manipulation session.                                        |

    - ### Methods inherited from interface oracle.spatial.network.nfe.vis.mapcanvas.behavior.[BehavioralLayer](../BehavioralLayer.md)

      [`refresh`](../BehavioralLayer.md)

<!-- -->

- - ### Field Detail

    - #### TRANS_NONE

          static final int TRANS_NONE

      No transformation
      See Also:
      [Constant Field Values](../../../../../../../../constant-values.md)

    <!-- -->

    - #### TRANS_TRANSLATE

          static final int TRANS_TRANSLATE

      Translation
      See Also:
      [Constant Field Values](../../../../../../../../constant-values.md)

    <!-- -->

    - #### TRANS_PULL

          static final int TRANS_PULL

      Pulling
      See Also:
      [Constant Field Values](../../../../../../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getManipulableGeoObjects

          java.util.Collection<GeoObject> getManipulableGeoObjects()

      Gets the layer's GeoObjects that can be manipulated
      Returns:
      a collection of GeoObjects

    <!-- -->

    - #### getHandlePoints

          double[] getHandlePoints(GeoObject geoObj)

      Gets the ordinates of the points from which a GeoObject can be manipulated
      Parameters:
      `geoObj` - a GeoObject

      Returns:
      an array of ordinates in model's coordinate system

    <!-- -->

    - #### getSnapPoint

          JGeometrySegmentPoint getSnapPoint(GeoObject geoObj,
                                             java.awt.geom.Point2D dataPoint,
                                             double tolerance)

      Gets the closer GeoObject's snap point to the given point using the tolerance specified
      Parameters:
      `geoObj` - a GeoObject

      `point` - a point in model's coordinate system

      `tolerance` - a tolarence in model's coordinate system

      Returns:
      a segment point relative to the GeoObject's geometry

    <!-- -->

    - #### getApplicableTransformation

          int getApplicableTransformation(GeoObject geoObj,
                                          java.util.Collection<GeoObject> manGeoObjGroup,
                                          JGeometrySegmentPoint snapPoint)

      Gets manipulation available for the given GeoObject and its current snap point. It is also specified all the GeoObjects that need to be manipulated along with the first GeoObject passed.
      Parameters:
      `geoObj` - a GeoObject

      `manGeoObjGroup` - a collection containing more GeoObjects to be manipulated. It can be null

      `snapPoint` - a segment point relative to the GeoObject's geometry

      Returns:
      a manipulation code

    <!-- -->

    - #### startManipulation

          long startManipulation(GeoObject geoObj,
                                 java.util.Collection<GeoObject> manGeoObjGroup,
                                 JGeometrySegmentPoint snapPoint,
                                 int transformation)

      Starts a manipulation session. The manipulation will be performed over the give GeoObject and the GeoObject group passed.
      Parameters:
      `geoObj` - the target GeoObject to be manipulated

      `manGeoObjGroup` - a group of GeoObjects to be manipulated

      `snapPoint` - a segment point relative to the GeoObject's geometry

      `transformation` - the type of manipulation to be performed

      Returns:
      a manipulation session id

    <!-- -->

    - #### finishManipulation

          boolean finishManipulation(long manId,
                                     java.awt.geom.Point2D dataPoint)

      finishes the manipulation identified by the given id. The last mouse point is specified.
      Parameters:
      `manId` - the manipulation session id

      `dataPoint` - the last point for the manipulation in model's coordinate system

      Returns:
      true if the manipulation was performed successfully

    <!-- -->

    - #### manipulate

          boolean manipulate(long manId,
                             java.awt.geom.Point2D dataPoint)

      Updates the state of a manipulation with the last point. It is useful if a live preview has to be shown.
      Parameters:
      `manId` - a manipulation session id

      `dataPoint` - the last user point (it may be a mouse point) in model's coordinate system

      Returns:
      true if the manipulation state was updated successfully

    <!-- -->

    - #### cancelManipulation

          void cancelManipulation(long manId)

      Cancels the given manipulation and releases all the resources related to it
      Parameters:
      `manId` - a manipulation session id

    <!-- -->

    - #### getPreview

          ManipulationPreview getPreview(long manId)

      Gets a preview for a manipulation
      Parameters:
      `manId` - a manipulation session id

      Returns:
      a manipulation preview object

Skip navigation links

- [Overview](../../../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../../../deprecated-list.md)
- [Index](../../../../../../../../index-all.md)
- [Help](../../../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](FeatureLayerManipulationPreview.md)
- [Next Class](Manipulation.md)

<!-- -->

- [Frames](../../../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../../../allclasses-noframe.md)

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
