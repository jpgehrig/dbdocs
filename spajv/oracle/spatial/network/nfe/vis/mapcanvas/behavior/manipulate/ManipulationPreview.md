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

- [Prev Class](Manipulation.md)
- Next Class

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

## Interface ManipulationPreview

- All Known Implementing Classes:
  [BasicManipulationPreview](BasicManipulationPreview.md), [FeatureLayerManipulationPreview](FeatureLayerManipulationPreview.md)

  ------------------------------------------------------------------------



      public interface ManipulationPreview

  Represents a preview of a manipulation performed over a ManipulableLayer.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                    |
    |-------------------|-----------------------------------------------------------------------------------------------------------|
    | `void`            | `addPreview``(ManipulationPreview preview)`<br>Adds a preview to the current preview                      |
    | `void`            | `preview``(java.awt.Graphics2D graphics, java.awt.geom.AffineTransform transform)`<br>Renders the preview |

<!-- -->

- - ### Method Detail

    - #### preview

          void preview(java.awt.Graphics2D graphics,
                       java.awt.geom.AffineTransform transform)

      Renders the preview
      Parameters:
      `graphics` - a graphics object

      `transform` - the transform used

    <!-- -->

    - #### addPreview

          void addPreview(ManipulationPreview preview)

      Adds a preview to the current preview
      Parameters:
      `preview` - a manipulation preview

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

- [Prev Class](Manipulation.md)
- Next Class

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
