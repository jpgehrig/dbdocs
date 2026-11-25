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

- [Prev Class](DataProducer.md)
- [Next Class](Drawable.md)

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

## Class DefaultSelectionManager\<V extends [GeoObject](GeoObject.md)\>

- java.lang.Object

- - oracle.spatial.network.nfe.vis.maps.core.DefaultSelectionManager\<V\>

<!-- -->

-

  ------------------------------------------------------------------------



      public class DefaultSelectionManager<V extends GeoObject>
      extends java.lang.Object

  A helper component that can be used by a [`Layer`](Layer.md) to keep track of the geo-objects selected

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                      |
    |------------------------------------------------------------------------------------------------------------------|
    | `DefaultSelectionManager``(`[`Layer`](Layer.md)` parent)`<br>Crates a new instance associated to the given layer |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type   | Method and Description                                                                                                                                                           |
    |---------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`              | `addSelectionListener``(`[`SelectionListener`](SelectionListener.md)` l)`<br>Adds a selection listener                                                                           |
    | `boolean`           | `clear``()`<br>Clears the selection                                                                                                                                              |
    | `void`              | `fireSelectionChanged``(`[`SelectionEvent`](SelectionEvent.md)` evt)`<br>Notifies the given SelectionEvent to all the registered selection listeners                             |
    | `java.util.List<V>` | `getSelection``()`<br>Gets a list of selected objects                                                                                                                            |
    | `java.util.List<V>` | `getSelection``(V obj)`<br>Returns selected objects that are children of the provided objects GeoObject's isSubElementOf() determines if an object is children of another object |
    | `boolean`           | `isSelected``(V obj)`<br>True if the object is selected                                                                                                                          |
    | `void`              | `removeSelectionListener``(`[`SelectionListener`](SelectionListener.md)` l)`<br>Removes the given selection listener                                                             |
    | `boolean`           | `select``(java.util.List<V> objs)`<br>Sets the objects in the list as selected without clearing the previous selections                                                          |
    | `boolean`           | `setSelection``(java.util.List<V> objs)`<br>Sets all the objects in the list as selected.                                                                                        |
    | `int`               | `size``()`<br>Returns the number of selected objects                                                                                                                             |
    | `boolean`           | `unselect``(java.util.List<V> objs)`<br>Marks the given objects as not selected                                                                                                  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### DefaultSelectionManager

          public DefaultSelectionManager(Layer parent)

      Crates a new instance associated to the given layer
      Parameters:
      `parent` -

  <!-- -->

  - ### Method Detail

    - #### isSelected

          public boolean isSelected(V obj)

      True if the object is selected
      Parameters:

      `obj` -

      Returns:

    <!-- -->

    - #### clear

          public boolean clear()

      Clears the selection
      Returns:

    <!-- -->

    - #### size

          public int size()

      Returns the number of selected objects
      Returns:

    <!-- -->

    - #### getSelection

          public java.util.List<V> getSelection()

      Gets a list of selected objects
      Returns:

    <!-- -->

    - #### getSelection

          public java.util.List<V> getSelection(V obj)

      Returns selected objects that are children of the provided objects GeoObject's isSubElementOf() determines if an object is children of another object
      Parameters:

      `obj` -

      Returns:

    <!-- -->

    - #### setSelection

          public boolean setSelection(java.util.List<V> objs)

      Sets all the objects in the list as selected. It clears the previous selection.
      Parameters:

      `objs` -

      Returns:

    <!-- -->

    - #### select

          public boolean select(java.util.List<V> objs)

      Sets the objects in the list as selected without clearing the previous selections
      Parameters:

      `objs` -

      Returns:

    <!-- -->

    - #### unselect

          public boolean unselect(java.util.List<V> objs)

      Marks the given objects as not selected
      Parameters:

      `objs` -

      Returns:

    <!-- -->

    - #### addSelectionListener

          public void addSelectionListener(SelectionListener l)

      Adds a selection listener
      Parameters:
      `l` -

    <!-- -->

    - #### removeSelectionListener

          public void removeSelectionListener(SelectionListener l)

      Removes the given selection listener
      Parameters:
      `l` -

    <!-- -->

    - #### fireSelectionChanged

          public void fireSelectionChanged(SelectionEvent evt)

      Notifies the given SelectionEvent to all the registered selection listeners
      Parameters:
      `evt` -

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

- [Prev Class](DataProducer.md)
- [Next Class](Drawable.md)

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
