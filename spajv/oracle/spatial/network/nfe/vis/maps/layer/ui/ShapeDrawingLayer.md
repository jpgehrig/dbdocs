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

- [Prev Class](ScaleBarLayer.md)
- [Next Class](SimpleBGLayer.md)

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

oracle.spatial.network.nfe.vis.maps.layer.ui

## Interface ShapeDrawingLayer

- All Known Implementing Classes:
  [MapNavLayer](MapNavLayer.md)

  ------------------------------------------------------------------------



      public interface ShapeDrawingLayer

  An interface for layers that use a tool to create a shape and draw it For example, rectangle selection, rectangle zoom box and rectangular polygon creation layers can use the same RectangleTool if they implement this interface

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type       | Method and Description                                                                                |
    |-------------------------|-------------------------------------------------------------------------------------------------------|
    | `java.awt.geom.Point2D` | `getSnapPoint``(java.awt.geom.Point2D point)`<br>Gets the shape snap point closest to the given point |
    | `void`                  | `setShape``(java.awt.Shape shape)`<br>Sets the shape to be drawn                                      |
    | `void`                  | `shapeCompleted``(java.awt.event.MouseEvent e)`<br>To be called when the shape is completely drawn    |

<!-- -->

- - ### Method Detail

    - #### setShape

          void setShape(java.awt.Shape shape)

      Sets the shape to be drawn
      Parameters:
      `shape` -

    <!-- -->

    - #### shapeCompleted

          void shapeCompleted(java.awt.event.MouseEvent e)

      To be called when the shape is completely drawn
      Parameters:
      `e` -

    <!-- -->

    - #### getSnapPoint

          java.awt.geom.Point2D getSnapPoint(java.awt.geom.Point2D point)

      Gets the shape snap point closest to the given point
      Parameters:

      `point` -

      Returns:

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

- [Prev Class](ScaleBarLayer.md)
- [Next Class](SimpleBGLayer.md)

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
