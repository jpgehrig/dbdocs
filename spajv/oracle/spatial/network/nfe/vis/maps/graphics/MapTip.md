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

- [Prev Class](GraphicsUtilities.md)
- [Next Class](ShadowRenderer.md)

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

oracle.spatial.network.nfe.vis.maps.graphics

## Class MapTip

- java.lang.Object

- - oracle.spatial.network.nfe.vis.maps.graphics.MapTip

<!-- -->

-

  ------------------------------------------------------------------------



      public class MapTip
      extends java.lang.Object

  Displays a one line tip that contains a short description of a feature in hover.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `MapTip``()`                |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                          |
    |--------------------|-----------------------------------------------------------------------------------------------------------------|
    | `java.awt.Font`    | `getFont``()`                                                                                                   |
    | `int`              | `getHeight``()`                                                                                                 |
    | `java.lang.String` | `getText``()`                                                                                                   |
    | `int`              | `getWidth``()`                                                                                                  |
    | `boolean`          | `isBorderless``()`                                                                                              |
    | `boolean`          | `isDraggable``()`                                                                                               |
    | `boolean`          | `isNeverShrink``()`                                                                                             |
    | `boolean`          | `isRounded``()`                                                                                                 |
    | `boolean`          | `isShadow``()`                                                                                                  |
    | `long`             | `render``(java.awt.Graphics2D g, java.awt.geom.Point2D topLeftCorner)`                                          |
    | `void`             | `setBorderless``(boolean borderless)`                                                                           |
    | `void`             | `setDraggable``(boolean draggable)`<br>Sets the flag to indicate if this map tip can be dragged around the map. |
    | `void`             | `setFont``(java.awt.Font font)`                                                                                 |
    | `void`             | `setNeverShrink``(boolean neverShrink)`                                                                         |
    | `void`             | `setRounded``(boolean rounded)`                                                                                 |
    | `void`             | `setShadow``(boolean shadow)`                                                                                   |
    | `void`             | `setText``(java.lang.String text)`                                                                              |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### MapTip

          public MapTip()

  <!-- -->

  - ### Method Detail

    - #### render

          public long render(java.awt.Graphics2D g,
                             java.awt.geom.Point2D topLeftCorner)

    <!-- -->

    - #### getText

          public java.lang.String getText()

    <!-- -->

    - #### setText

          public void setText(java.lang.String text)

    <!-- -->

    - #### getFont

          public java.awt.Font getFont()

    <!-- -->

    - #### setFont

          public void setFont(java.awt.Font font)

    <!-- -->

    - #### isRounded

          public boolean isRounded()

    <!-- -->

    - #### setRounded

          public void setRounded(boolean rounded)

    <!-- -->

    - #### isDraggable

          public boolean isDraggable()

    <!-- -->

    - #### setDraggable

          public void setDraggable(boolean draggable)

      Sets the flag to indicate if this map tip can be dragged around the map.
      Parameters:
      `draggable` -

    <!-- -->

    - #### isShadow

          public boolean isShadow()

    <!-- -->

    - #### setShadow

          public void setShadow(boolean shadow)

    <!-- -->

    - #### isBorderless

          public boolean isBorderless()

    <!-- -->

    - #### setBorderless

          public void setBorderless(boolean borderless)

    <!-- -->

    - #### isNeverShrink

          public boolean isNeverShrink()

    <!-- -->

    - #### setNeverShrink

          public void setNeverShrink(boolean neverShrink)

    <!-- -->

    - #### getWidth

          public int getWidth()

    <!-- -->

    - #### getHeight

          public int getHeight()

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

- [Prev Class](GraphicsUtilities.md)
- [Next Class](ShadowRenderer.md)

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
