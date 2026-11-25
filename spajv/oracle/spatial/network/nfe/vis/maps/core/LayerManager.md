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

- [Prev Class](Layer.md)
- [Next Class](LayerManager.Entry.md)

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

## Class LayerManager

- java.lang.Object

- - oracle.spatial.network.nfe.vis.maps.core.LayerManager

<!-- -->

- All Implemented Interfaces:
  java.beans.PropertyChangeListener, java.lang.Iterable\<[Layer](Layer.md)\>, java.util.Collection\<[Layer](Layer.md)\>, java.util.EventListener, [EditChangeListener](EditChangeListener.md), [SelectionListener](SelectionListener.md)

  ------------------------------------------------------------------------



      public class LayerManager
      extends java.lang.Object
      implements java.util.Collection<Layer>, EditChangeListener, SelectionListener, java.beans.PropertyChangeListener

  Contains and manages all the Layers to be displayed by the MapCanvas

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Class and Description                          |
    |-------------------|------------------------------------------------|
    | `static class `   | [`LayerManager.Entry`](LayerManager.Entry.md)  |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                            |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `LayerManager``(`[`MapCanvas`](MapCanvas.md)` canvas)`                                                                                                                                                                                                 |
    | `LayerManager``(`[`MapCanvas`](MapCanvas.md)` canvas, java.util.Collection<? extends `[`Layer`](Layer.md)`> lm)`<br>Constructs a list containing the elements of the specified collection, in the order they are returned by the collection's iterator |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                         | Method and Description                                                                                                                                                         |
    |---------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                                                 | `add``(`[`Layer`](Layer.md)` layer)`<br>Inserts the specified layer at the end of this list.                                                                                   |
    | `boolean`                                                                 | `add``(`[`Layer`](Layer.md)` layer, java.lang.Integer position)`<br>Inserts the specified layer at the end of the specified position in this list.                             |
    | `boolean`                                                                 | `addAll``(java.util.Collection<? extends `[`Layer`](Layer.md)`> c)`                                                                                                            |
    | `void`                                                                    | `addChangeListener``(javax.swing.event.ChangeListener l)`                                                                                                                      |
    | `void`                                                                    | `addEditChangeListener``(`[`EditChangeListener`](EditChangeListener.md)` l)`                                                                                                   |
    | `boolean`                                                                 | `addFirst``(`[`Layer`](Layer.md)` layer)`<br>Inserts the specified layer at the begining of this list.                                                                         |
    | `boolean`                                                                 | `addFirst``(`[`Layer`](Layer.md)` layer, java.lang.Integer position)`<br>Inserts the specified layer at the begining of the specified position in this list.                   |
    | `boolean`                                                                 | `addLast``(`[`Layer`](Layer.md)` layer)`<br>Inserts the specified layer at the end of this list.                                                                               |
    | `boolean`                                                                 | `addLast``(`[`Layer`](Layer.md)` layer, java.lang.Integer position)`<br>Inserts the specified layer at the end of the specified position in this list.                         |
    | `void`                                                                    | `addPropertyChangeListener``(java.beans.PropertyChangeListener listener)`                                                                                                      |
    | `void`                                                                    | `addPropertyChangeListener``(java.lang.String propertyName, java.beans.PropertyChangeListener listener)`                                                                       |
    | `void`                                                                    | `addSelectionListener``(`[`SelectionListener`](SelectionListener.md)` l)`                                                                                                      |
    | `void`                                                                    | `clear``()`                                                                                                                                                                    |
    | `void`                                                                    | `clearAllHover``()`                                                                                                                                                            |
    | `void`                                                                    | `clearAllSelections``()`                                                                                                                                                       |
    | `boolean`                                                                 | `contains``(java.lang.Object o)`                                                                                                                                               |
    | `boolean`                                                                 | `containsAll``(java.util.Collection<?> c)`                                                                                                                                     |
    | `java.util.Iterator<`[`LayerManager.Entry`](LayerManager.Entry.md)`>`     | `descendingEntryIterator``()`                                                                                                                                                  |
    | `java.util.Iterator<`[`Layer`](Layer.md)`>`                               | `descendingLayerIterator``()`                                                                                                                                                  |
    | `void`                                                                    | `editStateChanged``(javax.swing.event.ChangeEvent e)`<br>Invoked when the layer has changed as a result of editing it's objects                                                |
    | `java.util.Iterator<`[`LayerManager.Entry`](LayerManager.Entry.md)`>`     | `entryIterator``()`                                                                                                                                                            |
    | `java.util.ListIterator<`[`LayerManager.Entry`](LayerManager.Entry.md)`>` | `entryIterator``(java.lang.Integer position)`                                                                                                                                  |
    | `java.util.ListIterator<`[`LayerManager.Entry`](LayerManager.Entry.md)`>` | `entryIterator``(`[`Layer`](Layer.md)` layer)`                                                                                                                                 |
    | `boolean`                                                                 | `equals``(java.lang.Object o)`                                                                                                                                                 |
    | `LayerManager`                                                            | `filterSet``(`[`Filter`](Filter.md)`<`[`Layer`](Layer.md)`> filter)`                                                                                                           |
    | `LayerManager`                                                            | `filterSet``(`[`Filter`](Filter.md)`<`[`Layer`](Layer.md)`> filter, int stopAt)`                                                                                               |
    | `LayerManager`                                                            | `filterSetByTags``(java.lang.String[] tags)`                                                                                                                                   |
    | [`Layer`](Layer.md)                                                       | `get``(int i)`<br>Gets the layer at the given position                                                                                                                         |
    | `java.util.List<`[`GeoObject`](GeoObject.md)`>`                           | `getAllSelections``()`                                                                                                                                                         |
    | [`Layer`](Layer.md)                                                       | `getFirst``()`<br>Returns the first layer from this list, or `null` if this list is empty.                                                                                     |
    | [`Layer`](Layer.md)                                                       | `getFirst``(java.lang.Integer position)`<br>Returns the first layer from the specified position in the list, or `null` if there are no layers at that position.                |
    | [`Layer`](Layer.md)                                                       | `getLast``()`<br>Returns the last layer from this list, or `null` if this list is empty.                                                                                       |
    | [`Layer`](Layer.md)                                                       | `getLast``(java.lang.Integer position)`<br>Returns the last layer from the specified position in the list, or `null` if there are no layers at that position.                  |
    | [`Layer`](Layer.md)                                                       | `getLayerByName``(java.lang.String name)`                                                                                                                                      |
    | [`Layer`](Layer.md)                                                       | `getLayerByPosition``(java.lang.Integer position)`                                                                                                                             |
    | [`Layer`](Layer.md)                                                       | `getLayerByTag``(java.lang.String tag)`                                                                                                                                        |
    | [`MapCanvas`](MapCanvas.md)                                               | `getMapCanvas``()`                                                                                                                                                             |
    | `java.lang.Integer`                                                       | `getPosition``(`[`Layer`](Layer.md)` layer)`<br>Gets the layer position                                                                                                        |
    | `java.beans.PropertyChangeListener[]`                                     | `getPropertyChangeListeners``()`                                                                                                                                               |
    | `java.beans.PropertyChangeListener[]`                                     | `getPropertyChangeListeners``(java.lang.String propertyName)`                                                                                                                  |
    | `java.util.Collection<java.lang.String>`                                  | `getTags``(`[`Layer`](Layer.md)` layer)`<br>Returns the layer tags                                                                                                             |
    | `LayerManager`                                                            | `headSet``(java.lang.Integer toPosition)`                                                                                                                                      |
    | `LayerManager`                                                            | `headSet``(java.lang.Integer toPosition, boolean inclusive)`                                                                                                                   |
    | `boolean`                                                                 | `isEmpty``()`                                                                                                                                                                  |
    | `java.util.Iterator<`[`Layer`](Layer.md)`>`                               | `iterator``()`                                                                                                                                                                 |
    | `java.util.Iterator<`[`Layer`](Layer.md)`>`                               | `layerIterator``()`                                                                                                                                                            |
    | `java.util.ListIterator<`[`Layer`](Layer.md)`>`                           | `layerIterator``(java.lang.Integer position)`                                                                                                                                  |
    | `java.util.ListIterator<`[`Layer`](Layer.md)`>`                           | `layerIterator``(`[`Layer`](Layer.md)` layer)`                                                                                                                                 |
    | `java.lang.Integer`                                                       | `moveDown``(`[`Layer`](Layer.md)` layer, boolean crossPositions)`                                                                                                              |
    | `java.lang.Integer`                                                       | `moveUp``(`[`Layer`](Layer.md)` layer, boolean crossPositions)`                                                                                                                |
    | `void`                                                                    | `propertyChange``(java.beans.PropertyChangeEvent evt)`                                                                                                                         |
    | `boolean`                                                                 | `remove``(java.lang.Object o)`                                                                                                                                                 |
    | `boolean`                                                                 | `removeAll``(java.util.Collection<?> c)`                                                                                                                                       |
    | `void`                                                                    | `removeChangeListener``(javax.swing.event.ChangeListener l)`                                                                                                                   |
    | `void`                                                                    | `removeEditChangeListener``(`[`EditChangeListener`](EditChangeListener.md)` l)`                                                                                                |
    | [`Layer`](Layer.md)                                                       | `removeFirst``()`<br>Removes and returns the first layer from this list, or `null` if this list is empty.                                                                      |
    | [`Layer`](Layer.md)                                                       | `removeFirst``(java.lang.Integer position)`<br>Removes and returns the first layer from the specified position in the list, or `null` if there are no layers at that position. |
    | [`Layer`](Layer.md)                                                       | `removeLast``()`<br>Removes and returns the last layer from this list, or `null` if this list is empty.                                                                        |
    | [`Layer`](Layer.md)                                                       | `removeLast``(java.lang.Integer position)`<br>Removes and returns the last layer from the specified position in the list, or `null` if there are no layers at that position.   |
    | `void`                                                                    | `removePropertyChangeListener``(java.beans.PropertyChangeListener listener)`                                                                                                   |
    | `void`                                                                    | `removePropertyChangeListener``(java.lang.String propertyName, java.beans.PropertyChangeListener listener)`                                                                    |
    | `void`                                                                    | `removeSelectionListener``(`[`SelectionListener`](SelectionListener.md)` l)`                                                                                                   |
    | `boolean`                                                                 | `retainAll``(java.util.Collection<?> c)`                                                                                                                                       |
    | `void`                                                                    | `selectionChanged``(`[`SelectionEvent`](SelectionEvent.md)` evt)`<br>This method is called when a selection event is fired.                                                    |
    | `void`                                                                    | `setMapCanvas``(`[`MapCanvas`](MapCanvas.md)` canvas)`                                                                                                                         |
    | `java.lang.Integer`                                                       | `setPositionFirst``(`[`Layer`](Layer.md)` layer, java.lang.Integer position)`                                                                                                  |
    | `java.lang.Integer`                                                       | `setPositionLast``(`[`Layer`](Layer.md)` layer, java.lang.Integer position)`                                                                                                   |
    | `int`                                                                     | `size``()`                                                                                                                                                                     |
    | `LayerManager`                                                            | `subSet``(java.lang.Integer fromPosition, boolean fromInclusive, java.lang.Integer toPosition, boolean toInclusive)`                                                           |
    | `LayerManager`                                                            | `subSet``(java.lang.Integer fromPosition, java.lang.Integer toPosition)`                                                                                                       |
    | `boolean`                                                                 | `tag``(`[`Layer`](Layer.md)` layer, java.lang.String tag)`<br>Adds a a tag to the given layer                                                                                  |
    | `boolean`                                                                 | `tag``(`[`Layer`](Layer.md)` layer, java.lang.String[] tags)`<br>Adds tags to the given layer                                                                                  |
    | `LayerManager`                                                            | `tailSet``(java.lang.Integer fromPosition)`                                                                                                                                    |
    | `LayerManager`                                                            | `tailSet``(java.lang.Integer fromPosition, boolean inclusive)`                                                                                                                 |
    | [`Layer`](Layer.md)`[]`                                                   | `toArray``()`                                                                                                                                                                  |
    | `<T> T[]`                                                                 | `toArray``(T[] a)`                                                                                                                                                             |
    | `java.lang.String`                                                        | `toString``()`<br>For debugging purposes                                                                                                                                       |
    | `org.w3c.dom.Element`                                                     | `toXMLElement``()`                                                                                                                                                             |
    | `boolean`                                                                 | `untag``(`[`Layer`](Layer.md)` layer, java.lang.String tag)`<br>Removes the tag from the given layer                                                                           |
    | `boolean`                                                                 | `untag``(`[`Layer`](Layer.md)` layer, java.lang.String[] tags)`<br>Removes tags from the given layer                                                                           |
    | `boolean`                                                                 | `untag``(java.lang.String tag)`<br>Removes the given tag from all the layers                                                                                                   |

    - ### Methods inherited from class java.lang.Object

      `getClass, hashCode, notify, notifyAll, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface java.util.Collection

      `hashCode, parallelStream, removeIf, spliterator, stream`

    <!-- -->

    - ### Methods inherited from interface java.lang.Iterable

      `forEach`

<!-- -->

- - ### Constructor Detail

    - #### LayerManager

          public LayerManager(MapCanvas canvas)

    <!-- -->

    - #### LayerManager

          public LayerManager(MapCanvas canvas,
                              java.util.Collection<? extends Layer> lm)

      Constructs a list containing the elements of the specified collection, in the order they are returned by the collection's iterator
      Parameters:
      `lm` -

  <!-- -->

  - ### Method Detail

    - #### add

          public boolean add(Layer layer)

      Inserts the specified layer at the end of this list. If the list is not empty the layer will be assigned the same position of the layer previously at the end, or the default position of 1 if the list was empty.
      This method is equivalent to `addLast(Layer)`

      Specified by:
      `add` in interface `java.util.Collection<`[`Layer`](Layer.md)`>`

      Parameters:
      `layer` - layer to be inserted

      Returns:
      `true` (as specified by `Collection.add(E)`)

    <!-- -->

    - #### add

          public boolean add(Layer layer,
                             java.lang.Integer position)

      Inserts the specified layer at the end of the specified position in this list. If there are other layers with the same position, this will be placed after them.
      This method is equivalent to `addLast(Layer, Integer)`

      Parameters:

      `layer` - layer to be inserted

      `position` - position at the end of which the specified layer is to be inserted

      Returns:

    <!-- -->

    - #### addFirst

          public boolean addFirst(Layer layer)

      Inserts the specified layer at the begining of this list. If the list is not empty the layer will be assigned the same position of the layer previously at the begining, or the default position of 1 if the list was empty.
      Parameters:
      `layer` - layer to be inserted

      Returns:
      `true` (as specified by `Collection.add(E)`)

    <!-- -->

    - #### addFirst

          public boolean addFirst(Layer layer,
                                  java.lang.Integer position)

      Inserts the specified layer at the begining of the specified position in this list. If there are other layers with the same position, this will be placed before them.
      Parameters:
      `layer` - layer to be inserted

      `position` - position at the begining of which the specified layer is to be inserted

      Returns:
      `true` (as specified by `Collection.add(E)`)

    <!-- -->

    - #### addLast

          public boolean addLast(Layer layer)

      Inserts the specified layer at the end of this list. If the list is not empty the layer will be assigned the same position of the layer previously at the end, or the default position of 1 if the list was empty.
      Parameters:
      `layer` - layer to be inserted

      Returns:
      `true` (as specified by `Collection.add(E)`)

    <!-- -->

    - #### addLast

          public boolean addLast(Layer layer,
                                 java.lang.Integer position)

      Inserts the specified layer at the end of the specified position in this list. If there are other layers with the same position, this will be placed after them.
      Parameters:
      `layer` - layer to be inserted

      `position` - position at the end of which the specified layer is to be inserted

      Returns:
      `true` (as specified by `Collection.add(E)`)

    <!-- -->

    - #### removeFirst

          public Layer removeFirst()

      Removes and returns the first layer from this list, or `null` if this list is empty.
      Returns:
      the first layer from this list or `null` if empty

    <!-- -->

    - #### removeFirst

          public Layer removeFirst(java.lang.Integer position)

      Removes and returns the first layer from the specified position in the list, or `null` if there are no layers at that position.
      Returns:
      the first layer at the position or `null`

    <!-- -->

    - #### removeLast

          public Layer removeLast()

      Removes and returns the last layer from this list, or `null` if this list is empty.
      Returns:
      the last layer from this list or `null` if empty

    <!-- -->

    - #### removeLast

          public Layer removeLast(java.lang.Integer position)

      Removes and returns the last layer from the specified position in the list, or `null` if there are no layers at that position.
      Returns:
      the last layer at the position or `null`

    <!-- -->

    - #### get

          public Layer get(int i)

      Gets the layer at the given position
      Parameters:

      `i` -

      Returns:

    <!-- -->

    - #### getFirst

          public Layer getFirst()

      Returns the first layer from this list, or `null` if this list is empty.
      Returns:
      the first layer from this list or `null` if empty

    <!-- -->

    - #### getFirst

          public Layer getFirst(java.lang.Integer position)

      Returns the first layer from the specified position in the list, or `null` if there are no layers at that position.
      Returns:
      the first layer at the position or `null`

    <!-- -->

    - #### getLast

          public Layer getLast()

      Returns the last layer from this list, or `null` if this list is empty.
      Returns:
      the last layer from this list or `null` if empty

    <!-- -->

    - #### getLast

          public Layer getLast(java.lang.Integer position)

      Returns the last layer from the specified position in the list, or `null` if there are no layers at that position.
      Returns:
      the last layer at the position or `null`

    <!-- -->

    - #### addAll

          public boolean addAll(java.util.Collection<? extends Layer> c)

      Specified by:
      `addAll` in interface `java.util.Collection<`[`Layer`](Layer.md)`>`

    <!-- -->

    - #### tag

          public boolean tag(Layer layer,
                             java.lang.String tag)

      Adds a a tag to the given layer
      Parameters:

      `layer` -

      `tag` -

      Returns:

    <!-- -->

    - #### tag

          public boolean tag(Layer layer,
                             java.lang.String[] tags)

      Adds tags to the given layer
      Parameters:

      `layer` -

      `tags` -

      Returns:

    <!-- -->

    - #### untag

          public boolean untag(java.lang.String tag)

      Removes the given tag from all the layers
      Parameters:

      `tag` -

      Returns:

    <!-- -->

    - #### untag

          public boolean untag(Layer layer,
                               java.lang.String tag)

      Removes the tag from the given layer
      Parameters:

      `layer` -

      `tag` -

      Returns:

    <!-- -->

    - #### untag

          public boolean untag(Layer layer,
                               java.lang.String[] tags)

      Removes tags from the given layer
      Parameters:

      `layer` -

      `tags` -

      Returns:

    <!-- -->

    - #### getPosition

          public java.lang.Integer getPosition(Layer layer)

      Gets the layer position
      Parameters:

      `layer` -

      Returns:

    <!-- -->

    - #### getTags

          public java.util.Collection<java.lang.String> getTags(Layer layer)

      Returns the layer tags
      Parameters:

      `layer` -

      Returns:

    <!-- -->

    - #### setPositionFirst

          public java.lang.Integer setPositionFirst(Layer layer,
                                                    java.lang.Integer position)

    <!-- -->

    - #### setPositionLast

          public java.lang.Integer setPositionLast(Layer layer,
                                                   java.lang.Integer position)

    <!-- -->

    - #### moveUp

          public java.lang.Integer moveUp(Layer layer,
                                          boolean crossPositions)

    <!-- -->

    - #### moveDown

          public java.lang.Integer moveDown(Layer layer,
                                            boolean crossPositions)

    <!-- -->

    - #### filterSet

          public LayerManager filterSet(Filter<Layer> filter,
                                        int stopAt)

    <!-- -->

    - #### filterSet

          public LayerManager filterSet(Filter<Layer> filter)

    <!-- -->

    - #### filterSetByTags

          public LayerManager filterSetByTags(java.lang.String[] tags)

    <!-- -->

    - #### getLayerByTag

          public Layer getLayerByTag(java.lang.String tag)

    <!-- -->

    - #### getLayerByName

          public Layer getLayerByName(java.lang.String name)

    <!-- -->

    - #### getLayerByPosition

          public Layer getLayerByPosition(java.lang.Integer position)

    <!-- -->

    - #### entryIterator

          public java.util.ListIterator<LayerManager.Entry> entryIterator(java.lang.Integer position)

    <!-- -->

    - #### layerIterator

          public java.util.ListIterator<Layer> layerIterator(java.lang.Integer position)

    <!-- -->

    - #### entryIterator

          public java.util.ListIterator<LayerManager.Entry> entryIterator(Layer layer)

    <!-- -->

    - #### layerIterator

          public java.util.ListIterator<Layer> layerIterator(Layer layer)

    <!-- -->

    - #### entryIterator

          public java.util.Iterator<LayerManager.Entry> entryIterator()

    <!-- -->

    - #### layerIterator

          public java.util.Iterator<Layer> layerIterator()

    <!-- -->

    - #### descendingEntryIterator

          public java.util.Iterator<LayerManager.Entry> descendingEntryIterator()

    <!-- -->

    - #### descendingLayerIterator

          public java.util.Iterator<Layer> descendingLayerIterator()

    <!-- -->

    - #### iterator

          public java.util.Iterator<Layer> iterator()

      Specified by:
      `iterator` in interface `java.lang.Iterable<`[`Layer`](Layer.md)`>`

      Specified by:
      `iterator` in interface `java.util.Collection<`[`Layer`](Layer.md)`>`

    <!-- -->

    - #### subSet

          public LayerManager subSet(java.lang.Integer fromPosition,
                                     boolean fromInclusive,
                                     java.lang.Integer toPosition,
                                     boolean toInclusive)

    <!-- -->

    - #### subSet

          public LayerManager subSet(java.lang.Integer fromPosition,
                                     java.lang.Integer toPosition)

    <!-- -->

    - #### headSet

          public LayerManager headSet(java.lang.Integer toPosition)

    <!-- -->

    - #### headSet

          public LayerManager headSet(java.lang.Integer toPosition,
                                      boolean inclusive)

    <!-- -->

    - #### tailSet

          public LayerManager tailSet(java.lang.Integer fromPosition)

    <!-- -->

    - #### tailSet

          public LayerManager tailSet(java.lang.Integer fromPosition,
                                      boolean inclusive)

    <!-- -->

    - #### equals

          public boolean equals(java.lang.Object o)

      Specified by:
      `equals` in interface `java.util.Collection<`[`Layer`](Layer.md)`>`

      Overrides:
      `equals` in class `java.lang.Object`

    <!-- -->

    - #### clear

          public void clear()

      Specified by:
      `clear` in interface `java.util.Collection<`[`Layer`](Layer.md)`>`

    <!-- -->

    - #### contains

          public boolean contains(java.lang.Object o)

      Specified by:
      `contains` in interface `java.util.Collection<`[`Layer`](Layer.md)`>`

    <!-- -->

    - #### containsAll

          public boolean containsAll(java.util.Collection<?> c)

      Specified by:
      `containsAll` in interface `java.util.Collection<`[`Layer`](Layer.md)`>`

    <!-- -->

    - #### isEmpty

          public boolean isEmpty()

      Specified by:
      `isEmpty` in interface `java.util.Collection<`[`Layer`](Layer.md)`>`

    <!-- -->

    - #### remove

          public boolean remove(java.lang.Object o)

      Specified by:
      `remove` in interface `java.util.Collection<`[`Layer`](Layer.md)`>`

    <!-- -->

    - #### removeAll

          public boolean removeAll(java.util.Collection<?> c)

      Specified by:
      `removeAll` in interface `java.util.Collection<`[`Layer`](Layer.md)`>`

    <!-- -->

    - #### retainAll

          public boolean retainAll(java.util.Collection<?> c)

      Specified by:
      `retainAll` in interface `java.util.Collection<`[`Layer`](Layer.md)`>`

    <!-- -->

    - #### size

          public int size()

      Specified by:
      `size` in interface `java.util.Collection<`[`Layer`](Layer.md)`>`

    <!-- -->

    - #### toArray

          public Layer[] toArray()

      Specified by:
      `toArray` in interface `java.util.Collection<`[`Layer`](Layer.md)`>`

    <!-- -->

    - #### toArray

          public <T> T[] toArray(T[] a)

      Specified by:
      `toArray` in interface `java.util.Collection<`[`Layer`](Layer.md)`>`

    <!-- -->

    - #### clearAllHover

          public void clearAllHover()

    <!-- -->

    - #### clearAllSelections

          public void clearAllSelections()

    <!-- -->

    - #### getAllSelections

          public java.util.List<GeoObject> getAllSelections()

    <!-- -->

    - #### toXMLElement

          public org.w3c.dom.Element toXMLElement()

    <!-- -->

    - #### toString

          public java.lang.String toString()

      For debugging purposes
      Overrides:

      `toString` in class `java.lang.Object`

      Returns:

    <!-- -->

    - #### propertyChange

          public void propertyChange(java.beans.PropertyChangeEvent evt)

      Specified by:
      `propertyChange` in interface `java.beans.PropertyChangeListener`

    <!-- -->

    - #### addPropertyChangeListener

          public void addPropertyChangeListener(java.beans.PropertyChangeListener listener)

    <!-- -->

    - #### addPropertyChangeListener

          public void addPropertyChangeListener(java.lang.String propertyName,
                                                java.beans.PropertyChangeListener listener)

    <!-- -->

    - #### getPropertyChangeListeners

          public java.beans.PropertyChangeListener[] getPropertyChangeListeners()

    <!-- -->

    - #### getPropertyChangeListeners

          public java.beans.PropertyChangeListener[] getPropertyChangeListeners(java.lang.String propertyName)

    <!-- -->

    - #### removePropertyChangeListener

          public void removePropertyChangeListener(java.beans.PropertyChangeListener listener)

    <!-- -->

    - #### removePropertyChangeListener

          public void removePropertyChangeListener(java.lang.String propertyName,
                                                   java.beans.PropertyChangeListener listener)

    <!-- -->

    - #### selectionChanged

          public void selectionChanged(SelectionEvent evt)

      Description copied from interface: [`SelectionListener`](SelectionListener.md)
      This method is called when a selection event is fired.
      Specified by:
      [`selectionChanged`](SelectionListener.md) in interface [`SelectionListener`](SelectionListener.md)

    <!-- -->

    - #### addSelectionListener

          public void addSelectionListener(SelectionListener l)

    <!-- -->

    - #### removeSelectionListener

          public void removeSelectionListener(SelectionListener l)

    <!-- -->

    - #### editStateChanged

          public void editStateChanged(javax.swing.event.ChangeEvent e)

      Description copied from interface: [`EditChangeListener`](EditChangeListener.md)
      Invoked when the layer has changed as a result of editing it's objects
      Specified by:
      [`editStateChanged`](EditChangeListener.md) in interface [`EditChangeListener`](EditChangeListener.md)

      Parameters:
      `e` - a ChangeEvent object

    <!-- -->

    - #### addEditChangeListener

          public void addEditChangeListener(EditChangeListener l)

    <!-- -->

    - #### removeEditChangeListener

          public void removeEditChangeListener(EditChangeListener l)

    <!-- -->

    - #### addChangeListener

          public void addChangeListener(javax.swing.event.ChangeListener l)

    <!-- -->

    - #### removeChangeListener

          public void removeChangeListener(javax.swing.event.ChangeListener l)

    <!-- -->

    - #### getMapCanvas

          public MapCanvas getMapCanvas()

    <!-- -->

    - #### setMapCanvas

          public void setMapCanvas(MapCanvas canvas)

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

- [Prev Class](Layer.md)
- [Next Class](LayerManager.Entry.md)

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
