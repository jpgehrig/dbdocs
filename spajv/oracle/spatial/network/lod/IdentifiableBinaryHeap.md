Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](Identifiable.md)
- [Next Class](IdentifiablePriorityQueue.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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

oracle.spatial.network.lod

## Class IdentifiableBinaryHeap\<E extends [Identifiable](Identifiable.md) & java.lang.Comparable\>

- java.lang.Object

- - oracle.spatial.network.lod.IdentifiableBinaryHeap\<E\>

<!-- -->

- All Implemented Interfaces:
  [IdentifiablePriorityQueue](IdentifiablePriorityQueue.md)\<E\>, [PriorityQueue](PriorityQueue.md)\<E\>

  ------------------------------------------------------------------------



      public class IdentifiableBinaryHeap<E extends Identifiable & java.lang.Comparable>
      extends java.lang.Object
      implements IdentifiablePriorityQueue<E>

  a binary Min. heap priority queue implementation Note the elements have to implement the Identifiable and Comparable interface (int compareTo(Object obj) )

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                      |
    |--------------------------------------------------|
    | `IdentifiableBinaryHeap``()`                     |
    | `IdentifiableBinaryHeap``(int initialCapacity)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                            |
    |--------------------|-------------------------------------------------------------------------------------------------------------------|
    | `void`             | `clear``()`<br>Empties the queue.                                                                                 |
    | `E`                | `deleteElementAt``(int index)`                                                                                    |
    | `E`                | `deleteMin``()`<br>Deletes the minimum element in the queue.                                                      |
    | `int`              | `findElementIndex``(E element)`                                                                                   |
    | `E`                | `findMin``()`<br>Finds the minimum element in the queue.                                                          |
    | `E`                | `getElement``(long id)`<br>Returns the element with the input ID, if the element exists; otherwise, returns null. |
    | `void`             | `insert``(E element)`<br>Inserts an element into the queue.                                                       |
    | `boolean`          | `isEmpty``()`<br>Determines whether the queue is empty or not.                                                    |
    | `E`                | `replaceElement``(long id, E newElement)`<br>Replace the old element of the specified id with a new element.      |
    | `void`             | `setIndex``(E element, int index)`                                                                                |
    | `int`              | `size``()`<br>Returns the size of the queue.                                                                      |
    | `java.lang.String` | `toString``()`                                                                                                    |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### IdentifiableBinaryHeap

          public IdentifiableBinaryHeap()

    <!-- -->

    - #### IdentifiableBinaryHeap

          public IdentifiableBinaryHeap(int initialCapacity)

  <!-- -->

  - ### Method Detail

    - #### clear

          public void clear()

      Description copied from interface: [`PriorityQueue`](PriorityQueue.md)
      Empties the queue.
      Specified by:
      [`clear`](PriorityQueue.md) in interface [`PriorityQueue`](PriorityQueue.md)`<E extends `[`Identifiable`](Identifiable.md)` & java.lang.Comparable>`

    <!-- -->

    - #### getElement

          public E getElement(long id)

      Description copied from interface: [`IdentifiablePriorityQueue`](IdentifiablePriorityQueue.md)
      Returns the element with the input ID, if the element exists; otherwise, returns null.
      Specified by:

      [`getElement`](IdentifiablePriorityQueue.md) in interface [`IdentifiablePriorityQueue`](IdentifiablePriorityQueue.md)`<E extends `[`Identifiable`](Identifiable.md)` & java.lang.Comparable>`

      Parameters:

      `id` - ID of the element

      Returns:

    <!-- -->

    - #### insert

          public void insert(E element)

      Description copied from interface: [`PriorityQueue`](PriorityQueue.md)
      Inserts an element into the queue.
      Specified by:
      [`insert`](PriorityQueue.md) in interface [`PriorityQueue`](PriorityQueue.md)`<E extends `[`Identifiable`](Identifiable.md)` & java.lang.Comparable>`

    <!-- -->

    - #### replaceElement

          public E replaceElement(long id,
                                  E newElement)

      Description copied from interface: [`IdentifiablePriorityQueue`](IdentifiablePriorityQueue.md)
      Replace the old element of the specified id with a new element. The ID of the new element does not need to be the same as the old element. If the old element does not exist in the queue, then simply insert the new element into the queue.
      Specified by:

      [`replaceElement`](IdentifiablePriorityQueue.md) in interface [`IdentifiablePriorityQueue`](IdentifiablePriorityQueue.md)`<E extends `[`Identifiable`](Identifiable.md)` & java.lang.Comparable>`

      Parameters:

      `id` - ID of the old element

      `newElement` - new element

      Returns:

    <!-- -->

    - #### findElementIndex

          public int findElementIndex(E element)

    <!-- -->

    - #### deleteElementAt

          public E deleteElementAt(int index)

    <!-- -->

    - #### size

          public int size()

      Description copied from interface: [`PriorityQueue`](PriorityQueue.md)
      Returns the size of the queue.
      Specified by:

      [`size`](PriorityQueue.md) in interface [`PriorityQueue`](PriorityQueue.md)`<E extends `[`Identifiable`](Identifiable.md)` & java.lang.Comparable>`

      Returns:

    <!-- -->

    - #### isEmpty

          public boolean isEmpty()

      Description copied from interface: [`PriorityQueue`](PriorityQueue.md)
      Determines whether the queue is empty or not.
      Specified by:

      [`isEmpty`](PriorityQueue.md) in interface [`PriorityQueue`](PriorityQueue.md)`<E extends `[`Identifiable`](Identifiable.md)` & java.lang.Comparable>`

      Returns:

    <!-- -->

    - #### findMin

          public E findMin()

      Description copied from interface: [`PriorityQueue`](PriorityQueue.md)
      Finds the minimum element in the queue. This method is non-destructive peeking. The queue is left untouched.
      Specified by:
      [`findMin`](PriorityQueue.md) in interface [`PriorityQueue`](PriorityQueue.md)`<E extends `[`Identifiable`](Identifiable.md)` & java.lang.Comparable>`

      Returns:
      the minimum element in the queue. If the queue is empty, return null.

    <!-- -->

    - #### deleteMin

          public E deleteMin()

      Description copied from interface: [`PriorityQueue`](PriorityQueue.md)
      Deletes the minimum element in the queue.
      Specified by:
      [`deleteMin`](PriorityQueue.md) in interface [`PriorityQueue`](PriorityQueue.md)`<E extends `[`Identifiable`](Identifiable.md)` & java.lang.Comparable>`

      Returns:
      the minimum element in the queue. If the queue is empty, return null.

    <!-- -->

    - #### setIndex

          public void setIndex(E element,
                               int index)

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Object`

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](Identifiable.md)
- [Next Class](IdentifiablePriorityQueue.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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
