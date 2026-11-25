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

- Prev Class
- [Next Class](DataProducer.md)

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

## Class CoreLoop

- java.lang.Object

- - oracle.spatial.network.nfe.vis.maps.core.CoreLoop

<!-- -->

- All Implemented Interfaces:
  java.awt.event.ActionListener, java.util.EventListener

  ------------------------------------------------------------------------



      public class CoreLoop
      extends java.lang.Object
      implements java.awt.event.ActionListener

  Each MapCanvas instance has a core rendering loop. Everything happens within this loop, from mouse and keyboard event handling, to interaction and layer display. This loop runs within the Swing event thread. So care should be taken that any update/render operations should complete quickly, to prevent the UI from frozen. Any time consuming task, such as loading data from MapViewer data server, should take place in a separate thread, and update the corresponding layer when done.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                       |
    |---------------------------------------------------|
    | `CoreLoop``(`[`MapCanvas`](MapCanvas.md)` view)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                    |
    |-------------------|---------------------------------------------------------------------------|
    | `void`            | `actionPerformed``(java.awt.event.ActionEvent e)`<br>Handle timer firing. |
    | `void`            | `start``()`                                                               |
    | `void`            | `stop``()`                                                                |
    | `void`            | `toggle``()`                                                              |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### CoreLoop

          public CoreLoop(MapCanvas view)

  <!-- -->

  - ### Method Detail

    - #### start

          public void start()

    <!-- -->

    - #### stop

          public void stop()

    <!-- -->

    - #### toggle

          public void toggle()

    <!-- -->

    - #### actionPerformed

          public void actionPerformed(java.awt.event.ActionEvent e)

      Handle timer firing.
      Specified by:
      `actionPerformed` in interface `java.awt.event.ActionListener`

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

- Prev Class
- [Next Class](DataProducer.md)

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
