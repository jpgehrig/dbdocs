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

- [Prev Class](SelectionEditableLayer.md)
- Next Class

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

oracle.spatial.network.nfe.vis.mapcanvas.behavior

## Interface VertexEditableLayer

- All Superinterfaces:
  [BehavioralLayer](BehavioralLayer.md)

  <!-- -->

  All Known Implementing Classes:
  [NFENetworkRenderer](../render/NFENetworkRenderer.md)

  ------------------------------------------------------------------------



      public interface VertexEditableLayer
      extends BehavioralLayer

  Defines a layer which line elements' vertices can be edited or added

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                     | Method and Description                                                                                                                                                                                           |
    |-----------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                                             | `addVertex``(`[`GeoObject`](../../maps/core/GeoObject.md)` geoObj, JGeometrySegmentPoint snapPoint)`<br>Adds a vertex to the given GeoObject at the specified snap point                                         |
    | `boolean`                                                             | `canAddVertex``(`[`GeoObject`](../../maps/core/GeoObject.md)` geoObj, JGeometrySegmentPoint snapPoint)`<br>Tells whether it is possible to add a new vertex to the GeoObject at the specified snap point         |
    | `JGeometrySegmentPoint`                                               | `getSnapPoint``(`[`GeoObject`](../../maps/core/GeoObject.md)` geoObj, java.awt.geom.Point2D point, double tolerance)`<br>Gets the closer GeoObject's snap point to the given point using the tolerance specified |
    | `java.util.Collection<`[`GeoObject`](../../maps/core/GeoObject.md)`>` | `getVertexEditableGeoObjects``()`<br>Gets all the GeoObjects which vertices can be edited                                                                                                                        |
    | `double[]`                                                            | `getVertices``(`[`GeoObject`](../../maps/core/GeoObject.md)` geoObj)`<br>Gets all the vertices of the GeoObject                                                                                                  |

    - ### Methods inherited from interface oracle.spatial.network.nfe.vis.mapcanvas.behavior.[BehavioralLayer](BehavioralLayer.md)

      [`refresh`](BehavioralLayer.md)

<!-- -->

- - ### Method Detail

    - #### getVertexEditableGeoObjects

          java.util.Collection<GeoObject> getVertexEditableGeoObjects()

      Gets all the GeoObjects which vertices can be edited
      Returns:
      a collection of GeoObjects

    <!-- -->

    - #### getVertices

          double[] getVertices(GeoObject geoObj)

      Gets all the vertices of the GeoObject
      Parameters:
      `geoObj` - a GeoObject

      Returns:
      an array containing the ordinates of the GeoObject's vertices

    <!-- -->

    - #### getSnapPoint

          JGeometrySegmentPoint getSnapPoint(GeoObject geoObj,
                                             java.awt.geom.Point2D point,
                                             double tolerance)

      Gets the closer GeoObject's snap point to the given point using the tolerance specified
      Parameters:
      `geoObj` - a GeoObject

      `point` - a point in model's coordinate system

      `tolerance` - a tolarence in model's coordinate system

      Returns:
      a segment point relative to the GeoObject's geometry

    <!-- -->

    - #### canAddVertex

          boolean canAddVertex(GeoObject geoObj,
                               JGeometrySegmentPoint snapPoint)

      Tells whether it is possible to add a new vertex to the GeoObject at the specified snap point
      Parameters:
      `geoObj` - a GeoObject

      `snapPoint` - a segment point relative to the GeoObject's geometry

      Returns:
      true if it is possible to add a new vertex

    <!-- -->

    - #### addVertex

          boolean addVertex(GeoObject geoObj,
                            JGeometrySegmentPoint snapPoint)

      Adds a vertex to the given GeoObject at the specified snap point
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

- [Prev Class](SelectionEditableLayer.md)
- Next Class

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
