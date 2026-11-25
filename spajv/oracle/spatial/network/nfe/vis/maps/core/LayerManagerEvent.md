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

- [Prev Class](LayerManager.Entry.md)
- [Next Class](MapCanvas.md)

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

## Class LayerManagerEvent

- java.lang.Object

- - java.util.EventObject

  - - javax.swing.event.ChangeEvent

    - - oracle.spatial.network.nfe.vis.maps.core.LayerManagerEvent

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  ------------------------------------------------------------------------



      public class LayerManagerEvent
      extends javax.swing.event.ChangeEvent

  Represents an event in a LayerManager
  See Also:
  [Serialized Form](../../../../../../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description     |
    |-------------------|---------------------------|
    | `static int`      | `LAYER_ADDED`             |
    | `static int`      | `LAYER_POSITION_CHANGED`  |
    | `static int`      | `LAYER_REMOVED`           |
    | `static int`      | `LAYER_TAGGED`            |
    | `static int`      | `LAYER_UNTAGGED`          |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                  |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `LayerManagerEvent``(java.lang.Object src, int type, `[`Layer`](Layer.md)` layer, java.lang.Integer position)`                                               |
    | `LayerManagerEvent``(java.lang.Object src, int type, `[`Layer`](Layer.md)` layer, java.lang.Integer position, java.util.Collection<java.lang.String> tags)`  |
    | `LayerManagerEvent``(java.lang.Object src, int type, `[`Layer`](Layer.md)` layer, java.lang.Integer newPosition, java.lang.Integer oldPosition)`             |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                        | Method and Description |
    |------------------------------------------|------------------------|
    | [`Layer`](Layer.md)                      | `getLayer``()`         |
    | `java.lang.Integer`                      | `getOldPosition``()`   |
    | `java.lang.Integer`                      | `getPosition``()`      |
    | `java.util.Collection<java.lang.String>` | `getTags``()`          |
    | `int`                                    | `getType``()`          |

    - ### Methods inherited from class java.util.EventObject

      `getSource, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### LAYER_ADDED

          public static final int LAYER_ADDED

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### LAYER_REMOVED

          public static final int LAYER_REMOVED

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### LAYER_POSITION_CHANGED

          public static final int LAYER_POSITION_CHANGED

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### LAYER_TAGGED

          public static final int LAYER_TAGGED

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### LAYER_UNTAGGED

          public static final int LAYER_UNTAGGED

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### LayerManagerEvent

          public LayerManagerEvent(java.lang.Object src,
                                   int type,
                                   Layer layer,
                                   java.lang.Integer position)

    <!-- -->

    - #### LayerManagerEvent

          public LayerManagerEvent(java.lang.Object src,
                                   int type,
                                   Layer layer,
                                   java.lang.Integer newPosition,
                                   java.lang.Integer oldPosition)

    <!-- -->

    - #### LayerManagerEvent

          public LayerManagerEvent(java.lang.Object src,
                                   int type,
                                   Layer layer,
                                   java.lang.Integer position,
                                   java.util.Collection<java.lang.String> tags)

  <!-- -->

  - ### Method Detail

    - #### getType

          public int getType()

    <!-- -->

    - #### getLayer

          public Layer getLayer()

    <!-- -->

    - #### getOldPosition

          public java.lang.Integer getOldPosition()

    <!-- -->

    - #### getPosition

          public java.lang.Integer getPosition()

    <!-- -->

    - #### getTags

          public java.util.Collection<java.lang.String> getTags()

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

- [Prev Class](LayerManager.Entry.md)
- [Next Class](MapCanvas.md)

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
