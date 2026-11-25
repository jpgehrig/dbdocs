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

- [Prev Class](ShapeDrawingLayer.md)
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

oracle.spatial.network.nfe.vis.maps.layer.ui

## Class SimpleBGLayer

- java.lang.Object

- - [oracle.spatial.network.nfe.vis.maps.layer.BasicLayer](../BasicLayer.md)

  - - oracle.spatial.network.nfe.vis.maps.layer.ui.SimpleBGLayer

<!-- -->

- All Implemented Interfaces:
  [Layer](../../core/Layer.md)

  ------------------------------------------------------------------------



      public class SimpleBGLayer
      extends BasicLayer

  A background layer that sits at the bottom of layer stack, and intercepts primarily mouse wheel zooming and mouse panning events.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description  |
    |---------------------------|------------------------|
    | `static java.lang.String` | `PROPERTY_BACKGROUND`  |
    | `static java.lang.String` | `PROPERTY_BORDER`      |

    - ### Fields inherited from interface oracle.spatial.network.nfe.vis.maps.core.[Layer](../../core/Layer.md)

      [`PROPERTY_NAME`](../../core/Layer.md)`, `[`PROPERTY_PROVIDERID`](../../core/Layer.md)`, `[`PROPERTY_SRID`](../../core/Layer.md)`, `[`PROPERTY_VISIBLE`](../../core/Layer.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                         |
    |---------------------------------------------------------------------|
    | `SimpleBGLayer``(`[`MapCanvas`](../../core/MapCanvas.md)` canvas)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                    |
    |-------------------|-----------------------------------------------------------------------------------------------------------|
    | `java.awt.Color`  | `getBackground``()`<br>Returns the background color                                                       |
    | `java.awt.Color`  | `getBorderColor``()`<br>Returns the border color                                                          |
    | `boolean`         | `handleEvent``(java.util.EventObject evt)`<br>The main method that performs event handling for this tool. |
    | `long`            | `render``(java.awt.Graphics2D g)`<br>Renders the layer contents to the given Graphics.                    |
    | `void`            | `setBackground``(java.awt.Color background)`<br>Sets the background color                                 |
    | `void`            | `setBorderColor``(java.awt.Color borderColor)`<br>Sets the border color                                   |
    | `void`            | `update``(long elapsedTime)`<br>updates the contents data model or structure.                             |

    - ### Methods inherited from class oracle.spatial.network.nfe.vis.maps.layer.[BasicLayer](../BasicLayer.md)

      [`added`](../BasicLayer.md)`, `[`addPropertyChangeListener`](../BasicLayer.md)`, `[`addPropertyChangeListener`](../BasicLayer.md)`, `[`clear`](../BasicLayer.md)`, `[`fromXMLElement`](../BasicLayer.md)`, `[`getCanvas`](../BasicLayer.md)`, `[`getDataMBR`](../BasicLayer.md)`, `[`getFullExtent`](../BasicLayer.md)`, `[`getIcon`](../BasicLayer.md)`, `[`getName`](../BasicLayer.md)`, `[`getProperties`](../BasicLayer.md)`, `[`getProperty`](../BasicLayer.md)`, `[`getProperty`](../BasicLayer.md)`, `[`getPropertyChangeListeners`](../BasicLayer.md)`, `[`getPropertyChangeListeners`](../BasicLayer.md)`, `[`getProviderID`](../BasicLayer.md)`, `[`getSRID`](../BasicLayer.md)`, `[`hitTest`](../BasicLayer.md)`, `[`hitTest`](../BasicLayer.md)`, `[`isVisible`](../BasicLayer.md)`, `[`mapRegionChanged`](../BasicLayer.md)`, `[`removed`](../BasicLayer.md)`, `[`removePropertyChangeListener`](../BasicLayer.md)`, `[`removePropertyChangeListener`](../BasicLayer.md)`, `[`repaint`](../BasicLayer.md)`, `[`setCanvas`](../BasicLayer.md)`, `[`setName`](../BasicLayer.md)`, `[`setProperty`](../BasicLayer.md)`, `[`setProviderID`](../BasicLayer.md)`, `[`setSRID`](../BasicLayer.md)`, `[`setVisible`](../BasicLayer.md)`, `[`toXMLElement`](../BasicLayer.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### PROPERTY_BACKGROUND

          public static final java.lang.String PROPERTY_BACKGROUND

      See Also:
      [Constant Field Values](../../../../../../../../constant-values.md)

    <!-- -->

    - #### PROPERTY_BORDER

          public static final java.lang.String PROPERTY_BORDER

      See Also:
      [Constant Field Values](../../../../../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### SimpleBGLayer

          public SimpleBGLayer(MapCanvas canvas)

  <!-- -->

  - ### Method Detail

    - #### handleEvent

          public boolean handleEvent(java.util.EventObject evt)

      Description copied from interface: [`Layer`](../../core/Layer.md)
      The main method that performs event handling for this tool. Returns whether the event should be propagated to other layers down stream (further down the layer stack) after the event has been handled.
      Specified by:
      [`handleEvent`](../../core/Layer.md) in interface [`Layer`](../../core/Layer.md)

      Overrides:
      [`handleEvent`](../BasicLayer.md) in class [`BasicLayer`](../BasicLayer.md)

    <!-- -->

    - #### render

          public long render(java.awt.Graphics2D g)

      Description copied from interface: [`Layer`](../../core/Layer.md)
      Renders the layer contents to the given Graphics.
      Specified by:
      [`render`](../../core/Layer.md) in interface [`Layer`](../../core/Layer.md)

      Overrides:
      [`render`](../BasicLayer.md) in class [`BasicLayer`](../BasicLayer.md)

      Parameters:
      `g` - the graphics object

      Returns:
      the rendering time in milliseconds.

    <!-- -->

    - #### update

          public void update(long elapsedTime)

      Description copied from interface: [`Layer`](../../core/Layer.md)
      updates the contents data model or structure.
      Specified by:
      [`update`](../../core/Layer.md) in interface [`Layer`](../../core/Layer.md)

      Overrides:
      [`update`](../BasicLayer.md) in class [`BasicLayer`](../BasicLayer.md)

      Parameters:
      `elapsedTime` - The elapsed time since last update.

    <!-- -->

    - #### getBackground

          public java.awt.Color getBackground()

      Returns the background color
      Returns:

    <!-- -->

    - #### setBackground

          public void setBackground(java.awt.Color background)

      Sets the background color
      Parameters:
      `background` -

    <!-- -->

    - #### getBorderColor

          public java.awt.Color getBorderColor()

      Returns the border color
      Returns:

    <!-- -->

    - #### setBorderColor

          public void setBorderColor(java.awt.Color borderColor)

      Sets the border color
      Parameters:
      `borderColor` -

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

- [Prev Class](ShapeDrawingLayer.md)
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
