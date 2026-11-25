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

- [Prev Class](BasicManipulationPreview.md)
- [Next Class](ManipulableLayer.md)

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

## Class FeatureLayerManipulationPreview

- java.lang.Object

- - [oracle.spatial.network.nfe.vis.mapcanvas.behavior.manipulate.BasicManipulationPreview](BasicManipulationPreview.md)

  - - oracle.spatial.network.nfe.vis.mapcanvas.behavior.manipulate.FeatureLayerManipulationPreview

<!-- -->

- All Implemented Interfaces:
  [ManipulationPreview](ManipulationPreview.md)

  ------------------------------------------------------------------------



      public class FeatureLayerManipulationPreview
      extends BasicManipulationPreview

  A manipulation preview implementation for creating a feature layer manipulation preview. The changes in the feature layer's element are deduced from the manipulations made to its underlying network elements.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                                                                                                                            |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `FeatureLayerManipulationPreview``(`[`NFEModel`](../../../../model/NFEModel.md)` model, java.util.Collection<`[`NFEFeatureElement`](../../../../model/feature/NFEFeatureElement.md)`> featElems, java.util.Map<java.lang.String,`[`Manipulation`](Manipulation.md)`<`[`NFENetworkElement`](../../../../model/network/NFENetworkElement.md)`>> manNetElemsMap, double tolerance)`<br>Allocates a new feature layer manipulation preview |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                    |
    |-------------------|-----------------------------------------------------------------------------------------------------------|
    | `void`            | `preview``(java.awt.Graphics2D graphics, java.awt.geom.AffineTransform transform)`<br>Renders the preview |

    - ### Methods inherited from class oracle.spatial.network.nfe.vis.mapcanvas.behavior.manipulate.[BasicManipulationPreview](BasicManipulationPreview.md)

      [`addPreview`](BasicManipulationPreview.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### FeatureLayerManipulationPreview

          public FeatureLayerManipulationPreview(NFEModel model,
                                                 java.util.Collection<NFEFeatureElement> featElems,
                                                 java.util.Map<java.lang.String,Manipulation<NFENetworkElement>> manNetElemsMap,
                                                 double tolerance)

      Allocates a new feature layer manipulation preview
      Parameters:
      `model` - the current NFE model

      `featElems` - the feature elements that were affected by the manipulation of its underlying network elements

      `manNetElemsMap` - the manipulations performed over the underlying network elements

      `tolerance` - the tolerance used in model's coordinate system

  <!-- -->

  - ### Method Detail

    - #### preview

          public void preview(java.awt.Graphics2D graphics,
                              java.awt.geom.AffineTransform transform)

      Description copied from interface: [`ManipulationPreview`](ManipulationPreview.md)
      Renders the preview
      Specified by:
      [`preview`](ManipulationPreview.md) in interface [`ManipulationPreview`](ManipulationPreview.md)

      Overrides:
      [`preview`](BasicManipulationPreview.md) in class [`BasicManipulationPreview`](BasicManipulationPreview.md)

      Parameters:
      `graphics` - a graphics object

      `transform` - the transform used

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

- [Prev Class](BasicManipulationPreview.md)
- [Next Class](ManipulableLayer.md)

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
