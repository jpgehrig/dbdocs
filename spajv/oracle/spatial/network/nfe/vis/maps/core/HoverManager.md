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

- [Prev Class](HoverableLayer.md)
- [Next Class](Layer.md)

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

## Class HoverManager

- java.lang.Object

- - oracle.spatial.network.nfe.vis.maps.core.HoverManager

<!-- -->

-

  ------------------------------------------------------------------------



      public class HoverManager
      extends java.lang.Object

  A HoverManager is associated with a MapCanvas, and keeps a reference to the GeoObject that is currently in hover. Note that a GeoObject in hover is not necessarily selected. Typically any object that comes under the mouse cursor is in hover, which only becomes selected if the user then clicks on that object. The HoverManager fires a ChangeEvent whenever the GeoObject in hover changes, or if a hovering GeoObject loses its in hover state (such as after a certain period of time).

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `HoverManager``()`          |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type           | Method and Description                                                                                               |
    |-----------------------------|----------------------------------------------------------------------------------------------------------------------|
    | `void`                      | `addChangeListener``(javax.swing.event.ChangeListener l)`<br>Adds a change listener to listen for selection changes. |
    | `void`                      | `clear``()`                                                                                                          |
    | [`GeoObject`](GeoObject.md) | `getHover``()`                                                                                                       |
    | `boolean`                   | `isHover``(`[`GeoObject`](GeoObject.md)` obj)`<br>Checks to see if the given GeoObject is currently selected.        |
    | `void`                      | `removeChangeListener``(javax.swing.event.ChangeListener l)`                                                         |
    | `void`                      | `setHover``(`[`GeoObject`](GeoObject.md)` obj)`                                                                      |
    | `int`                       | `size``()`<br>Returns the number of GeoObject in hover.                                                              |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### HoverManager

          public HoverManager()

  <!-- -->

  - ### Method Detail

    - #### setHover

          public void setHover(GeoObject obj)

    <!-- -->

    - #### clear

          public void clear()

    <!-- -->

    - #### getHover

          public GeoObject getHover()

    <!-- -->

    - #### size

          public int size()

      Returns the number of GeoObject in hover.
      Returns:
      1 if there is a GeoObject currently in hover, 0 otherwise.

    <!-- -->

    - #### isHover

          public boolean isHover(GeoObject obj)

      Checks to see if the given GeoObject is currently selected.
      Parameters:
      `obj` - the GeoObject to be checked

      Returns:
      true if the given GeoObject is currently selected, false otherwise

    <!-- -->

    - #### addChangeListener

          public void addChangeListener(javax.swing.event.ChangeListener l)

      Adds a change listener to listen for selection changes.
      Parameters:
      `l` -

    <!-- -->

    - #### removeChangeListener

          public void removeChangeListener(javax.swing.event.ChangeListener l)

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

- [Prev Class](HoverableLayer.md)
- [Next Class](Layer.md)

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
