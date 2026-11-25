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

- [Prev Class](SelectableLayer.md)
- [Next Class](SelectionListener.md)

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

## Class SelectionEvent

- java.lang.Object

- - java.util.EventObject

  - - javax.swing.event.ChangeEvent

    - - oracle.spatial.network.nfe.vis.maps.core.SelectionEvent

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  ------------------------------------------------------------------------



      public class SelectionEvent
      extends javax.swing.event.ChangeEvent

  Represents a geo-object selection event.
  See Also:
  [Serialized Form](../../../../../../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description     |
    |-------------------|---------------------------|
    | `static int`      | `TYPE_SELECTION_ADDED`    |
    | `static int`      | `TYPE_SELECTION_CLEARED`  |
    | `static int`      | `TYPE_SELECTION_REMOVED`  |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                       |
    |-----------------------------------------------------------------------------------|
    | `SelectionEvent``(`[`Layer`](Layer.md)` src, int type)`<br>Creates a new instance |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type   | Method and Description                                    |
    |---------------------|-----------------------------------------------------------|
    | [`Layer`](Layer.md) | `getSource``()`                                           |
    | `int`               | `getType``()`<br>Returns the type of selection event      |
    | `void`              | `setType``(int type)`<br>Sets the type of selection event |

    - ### Methods inherited from class java.util.EventObject

      `toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### TYPE_SELECTION_ADDED

          public static final int TYPE_SELECTION_ADDED

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### TYPE_SELECTION_REMOVED

          public static final int TYPE_SELECTION_REMOVED

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

    <!-- -->

    - #### TYPE_SELECTION_CLEARED

          public static final int TYPE_SELECTION_CLEARED

      See Also:
      [Constant Field Values](../../../../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### SelectionEvent

          public SelectionEvent(Layer src,
                                int type)

      Creates a new instance
      Parameters:
      `src` - the layer that fired the event

      `type` - the type of selection event

  <!-- -->

  - ### Method Detail

    - #### getSource

          public Layer getSource()

      Overrides:
      `getSource` in class `java.util.EventObject`

    <!-- -->

    - #### setType

          public void setType(int type)

      Sets the type of selection event
      Parameters:
      `type` -

    <!-- -->

    - #### getType

          public int getType()

      Returns the type of selection event
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

- [Prev Class](SelectableLayer.md)
- [Next Class](SelectionListener.md)

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
