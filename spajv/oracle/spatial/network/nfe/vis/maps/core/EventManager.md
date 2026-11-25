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

- [Prev Class](EditChangeListener.md)
- [Next Class](Filter.md)

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

## Class EventManager

- java.lang.Object

- - oracle.spatial.network.nfe.vis.maps.core.EventManager

<!-- -->

- All Implemented Interfaces:
  java.awt.event.ActionListener, java.awt.event.ComponentListener, java.awt.event.FocusListener, java.awt.event.KeyListener, java.awt.event.MouseListener, java.awt.event.MouseMotionListener, java.awt.event.MouseWheelListener, java.util.EventListener, javax.swing.event.ChangeListener

  ------------------------------------------------------------------------



      public class EventManager
      extends java.lang.Object
      implements java.awt.event.KeyListener, java.awt.event.MouseListener, java.awt.event.MouseMotionListener, java.awt.event.MouseWheelListener, java.awt.event.ComponentListener, java.awt.event.ActionListener, javax.swing.event.ChangeListener, java.awt.event.FocusListener

  EventManager keeps track of current keyboard, mouse inputs and other critical events for the associated map canvas.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `EventManager``()`          |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type           | Method and Description                                                                                                                                                                                                                            |
    |-----------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                      | `actionPerformed``(java.awt.event.ActionEvent evt)`                                                                                                                                                                                               |
    | `void`                      | `componentHidden``(java.awt.event.ComponentEvent e)`                                                                                                                                                                                              |
    | `void`                      | `componentMoved``(java.awt.event.ComponentEvent e)`                                                                                                                                                                                               |
    | `void`                      | `componentResized``(java.awt.event.ComponentEvent e)`                                                                                                                                                                                             |
    | `void`                      | `componentShown``(java.awt.event.ComponentEvent e)`                                                                                                                                                                                               |
    | `void`                      | `focusGained``(java.awt.event.FocusEvent e)`                                                                                                                                                                                                      |
    | `void`                      | `focusLost``(java.awt.event.FocusEvent e)`                                                                                                                                                                                                        |
    | [`MapCanvas`](MapCanvas.md) | `getCanvas``()`<br>Gets the associated MapCanvas                                                                                                                                                                                                  |
    | `void`                      | `keyPressed``(java.awt.event.KeyEvent e)`                                                                                                                                                                                                         |
    | `void`                      | `keyReleased``(java.awt.event.KeyEvent e)`                                                                                                                                                                                                        |
    | `void`                      | `keyTyped``(java.awt.event.KeyEvent e)`                                                                                                                                                                                                           |
    | `void`                      | `mouseClicked``(java.awt.event.MouseEvent e)`                                                                                                                                                                                                     |
    | `void`                      | `mouseDragged``(java.awt.event.MouseEvent e)`                                                                                                                                                                                                     |
    | `void`                      | `mouseEntered``(java.awt.event.MouseEvent e)`                                                                                                                                                                                                     |
    | `void`                      | `mouseExited``(java.awt.event.MouseEvent e)`                                                                                                                                                                                                      |
    | `void`                      | `mouseMoved``(java.awt.event.MouseEvent e)`                                                                                                                                                                                                       |
    | `void`                      | `mousePressed``(java.awt.event.MouseEvent e)`                                                                                                                                                                                                     |
    | `void`                      | `mouseReleased``(java.awt.event.MouseEvent e)`                                                                                                                                                                                                    |
    | `void`                      | `mouseWheelMoved``(java.awt.event.MouseWheelEvent e)`                                                                                                                                                                                             |
    | `void`                      | `runLater``(java.lang.Runnable r)`<br>Queue a runnable to be run after all layers have been iterated over for the current input event being processed For example, to remove a layer from the canvas as a result from an input event in the layer |
    | `void`                      | `setCanvas``(`[`MapCanvas`](MapCanvas.md)` canvas)`<br>Sets the associated MapCanvas                                                                                                                                                              |
    | `void`                      | `stateChanged``(javax.swing.event.ChangeEvent e)`                                                                                                                                                                                                 |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### EventManager

          public EventManager()

  <!-- -->

  - ### Method Detail

    - #### keyPressed

          public void keyPressed(java.awt.event.KeyEvent e)

      Specified by:
      `keyPressed` in interface `java.awt.event.KeyListener`

    <!-- -->

    - #### keyReleased

          public void keyReleased(java.awt.event.KeyEvent e)

      Specified by:
      `keyReleased` in interface `java.awt.event.KeyListener`

    <!-- -->

    - #### keyTyped

          public void keyTyped(java.awt.event.KeyEvent e)

      Specified by:
      `keyTyped` in interface `java.awt.event.KeyListener`

    <!-- -->

    - #### mouseEntered

          public void mouseEntered(java.awt.event.MouseEvent e)

      Specified by:
      `mouseEntered` in interface `java.awt.event.MouseListener`

    <!-- -->

    - #### mouseExited

          public void mouseExited(java.awt.event.MouseEvent e)

      Specified by:
      `mouseExited` in interface `java.awt.event.MouseListener`

    <!-- -->

    - #### mouseClicked

          public void mouseClicked(java.awt.event.MouseEvent e)

      Specified by:
      `mouseClicked` in interface `java.awt.event.MouseListener`

    <!-- -->

    - #### mousePressed

          public void mousePressed(java.awt.event.MouseEvent e)

      Specified by:
      `mousePressed` in interface `java.awt.event.MouseListener`

    <!-- -->

    - #### mouseReleased

          public void mouseReleased(java.awt.event.MouseEvent e)

      Specified by:
      `mouseReleased` in interface `java.awt.event.MouseListener`

    <!-- -->

    - #### mouseDragged

          public void mouseDragged(java.awt.event.MouseEvent e)

      Specified by:
      `mouseDragged` in interface `java.awt.event.MouseMotionListener`

    <!-- -->

    - #### mouseMoved

          public void mouseMoved(java.awt.event.MouseEvent e)

      Specified by:
      `mouseMoved` in interface `java.awt.event.MouseMotionListener`

    <!-- -->

    - #### mouseWheelMoved

          public void mouseWheelMoved(java.awt.event.MouseWheelEvent e)

      Specified by:
      `mouseWheelMoved` in interface `java.awt.event.MouseWheelListener`

    <!-- -->

    - #### stateChanged

          public void stateChanged(javax.swing.event.ChangeEvent e)

      Specified by:
      `stateChanged` in interface `javax.swing.event.ChangeListener`

    <!-- -->

    - #### componentHidden

          public void componentHidden(java.awt.event.ComponentEvent e)

      Specified by:
      `componentHidden` in interface `java.awt.event.ComponentListener`

    <!-- -->

    - #### componentMoved

          public void componentMoved(java.awt.event.ComponentEvent e)

      Specified by:
      `componentMoved` in interface `java.awt.event.ComponentListener`

    <!-- -->

    - #### componentResized

          public void componentResized(java.awt.event.ComponentEvent e)

      Specified by:
      `componentResized` in interface `java.awt.event.ComponentListener`

    <!-- -->

    - #### componentShown

          public void componentShown(java.awt.event.ComponentEvent e)

      Specified by:
      `componentShown` in interface `java.awt.event.ComponentListener`

    <!-- -->

    - #### focusGained

          public void focusGained(java.awt.event.FocusEvent e)

      Specified by:
      `focusGained` in interface `java.awt.event.FocusListener`

    <!-- -->

    - #### focusLost

          public void focusLost(java.awt.event.FocusEvent e)

      Specified by:
      `focusLost` in interface `java.awt.event.FocusListener`

    <!-- -->

    - #### actionPerformed

          public void actionPerformed(java.awt.event.ActionEvent evt)

      Specified by:
      `actionPerformed` in interface `java.awt.event.ActionListener`

    <!-- -->

    - #### runLater

          public void runLater(java.lang.Runnable r)

      Queue a runnable to be run after all layers have been iterated over for the current input event being processed For example, to remove a layer from the canvas as a result from an input event in the layer
      Parameters:
      `r` -

    <!-- -->

    - #### getCanvas

          public MapCanvas getCanvas()

      Gets the associated MapCanvas
      Returns:

    <!-- -->

    - #### setCanvas

          public void setCanvas(MapCanvas canvas)

      Sets the associated MapCanvas
      Parameters:
      `canvas` -

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

- [Prev Class](EditChangeListener.md)
- [Next Class](Filter.md)

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
