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

- [Prev Class](MapRegion.md)
- [Next Class](MapUndoManager.md)

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

oracle.spatial.network.nfe.vis.maps.core

## Class MapRegionEvent

- java.lang.Object

- - java.util.EventObject

  - - javax.swing.event.ChangeEvent

    - - oracle.spatial.network.nfe.vis.maps.core.MapRegionEvent

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  ------------------------------------------------------------------------



      public class MapRegionEvent
      extends javax.swing.event.ChangeEvent

  Contains information regarding a change in a canvas's map region
  See Also:
  [Serialized Form](../../../../../../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description |
    |-------------------|-----------------------|
    | `static int`      | `TYPE_PAN`            |
    | `static int`      | `TYPE_ZOOMIN`         |
    | `static int`      | `TYPE_ZOOMOUT`        |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                      |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `MapRegionEvent``(java.lang.Object src, java.awt.geom.AffineTransform oldXFM, java.awt.geom.AffineTransform newXFM, java.awt.geom.Rectangle2D oldDataWindow, java.awt.geom.Rectangle2D newDataWindow)`<br>Creates a new instance |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type               | Method and Description                                                                                                                                                                 |
    |---------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.awt.geom.Rectangle2D`     | `getNewDataWindow``()`<br>Gets the current data window                                                                                                                                 |
    | `java.awt.geom.AffineTransform` | `getNewViewportTransform``()`<br>Gets the current AffineTransform                                                                                                                      |
    | `java.awt.geom.Rectangle2D`     | `getOldDataWindow``()`<br>Gets the data window before the event                                                                                                                        |
    | `java.awt.geom.AffineTransform` | `getOldViewportTransform``()`<br>Gets the AffineTransform instance before the event                                                                                                    |
    | `java.awt.geom.AffineTransform` | `getTransformDifference``()`<br>The transformation difference from the old to the new Objects rendered in the old transformation can apply this to be transformed to the new transform |

    - ### Methods inherited from class java.util.EventObject

      `getSource, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### TYPE_ZOOMIN

          public static int TYPE_ZOOMIN

    <!-- -->

    - #### TYPE_ZOOMOUT

          public static int TYPE_ZOOMOUT

    <!-- -->

    - #### TYPE_PAN

          public static int TYPE_PAN

  <!-- -->

  - ### Constructor Detail

    - #### MapRegionEvent

          public MapRegionEvent(java.lang.Object src,
                                java.awt.geom.AffineTransform oldXFM,
                                java.awt.geom.AffineTransform newXFM,
                                java.awt.geom.Rectangle2D oldDataWindow,
                                java.awt.geom.Rectangle2D newDataWindow)

      Creates a new instance
      Parameters:
      `src` - the source that fired the event

      `oldXFM` - the AffineTransform instance before the event

      `newXFM` - the current AffineTransform

      `oldDataWindow` - the data window before the event

      `newDataWindow` - the current data window

  <!-- -->

  - ### Method Detail

    - #### getOldViewportTransform

          public java.awt.geom.AffineTransform getOldViewportTransform()

      Gets the AffineTransform instance before the event
      Returns:

    <!-- -->

    - #### getNewViewportTransform

          public java.awt.geom.AffineTransform getNewViewportTransform()

      Gets the current AffineTransform
      Returns:

    <!-- -->

    - #### getTransformDifference

          public java.awt.geom.AffineTransform getTransformDifference()

      The transformation difference from the old to the new Objects rendered in the old transformation can apply this to be transformed to the new transform
      Returns:

    <!-- -->

    - #### getOldDataWindow

          public java.awt.geom.Rectangle2D getOldDataWindow()

      Gets the data window before the event
      Returns:

    <!-- -->

    - #### getNewDataWindow

          public java.awt.geom.Rectangle2D getNewDataWindow()

      Gets the current data window
      Returns:

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

- [Prev Class](MapRegion.md)
- [Next Class](MapUndoManager.md)

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
