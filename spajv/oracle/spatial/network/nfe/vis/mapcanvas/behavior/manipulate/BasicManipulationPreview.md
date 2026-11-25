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

- Prev Class
- [Next Class](FeatureLayerManipulationPreview.md)

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

## Class BasicManipulationPreview

- java.lang.Object

- - oracle.spatial.network.nfe.vis.mapcanvas.behavior.manipulate.BasicManipulationPreview

<!-- -->

- All Implemented Interfaces:
  [ManipulationPreview](ManipulationPreview.md)

  <!-- -->

  Direct Known Subclasses:
  [FeatureLayerManipulationPreview](FeatureLayerManipulationPreview.md)

  ------------------------------------------------------------------------



      public class BasicManipulationPreview
      extends java.lang.Object
      implements ManipulationPreview

  The manipulation preview containing other manipulation previews.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description     |
    |---------------------------------|
    | `BasicManipulationPreview``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                             |
    |-------------------|--------------------------------------------------------------------------------------------------------------------|
    | `void`            | `addPreview``(`[`ManipulationPreview`](ManipulationPreview.md)` preview)`<br>Adds a preview to the current preview |
    | `void`            | `preview``(java.awt.Graphics2D graphics, java.awt.geom.AffineTransform transform)`<br>Renders the preview          |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### BasicManipulationPreview

          public BasicManipulationPreview()

  <!-- -->

  - ### Method Detail

    - #### preview

          public void preview(java.awt.Graphics2D graphics,
                              java.awt.geom.AffineTransform transform)

      Description copied from interface: [`ManipulationPreview`](ManipulationPreview.md)
      Renders the preview
      Specified by:
      [`preview`](ManipulationPreview.md) in interface [`ManipulationPreview`](ManipulationPreview.md)

      Parameters:
      `graphics` - a graphics object

      `transform` - the transform used

    <!-- -->

    - #### addPreview

          public void addPreview(ManipulationPreview preview)

      Description copied from interface: [`ManipulationPreview`](ManipulationPreview.md)
      Adds a preview to the current preview
      Specified by:
      [`addPreview`](ManipulationPreview.md) in interface [`ManipulationPreview`](ManipulationPreview.md)

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

- Prev Class
- [Next Class](FeatureLayerManipulationPreview.md)

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
