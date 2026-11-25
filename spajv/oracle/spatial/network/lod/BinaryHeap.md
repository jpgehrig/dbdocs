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

- [Prev Class](BidirectionalDijkstra.md)
- [Next Class](BreadthFirstSearch.md)

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

## Class BinaryHeap\<E extends java.lang.Comparable\>

- java.lang.Object

- - oracle.spatial.network.lod.BinaryHeap\<E\>

<!-- -->

- All Implemented Interfaces:
  [PriorityQueue](PriorityQueue.md)\<E\>

  ------------------------------------------------------------------------



      public class BinaryHeap<E extends java.lang.Comparable>
      extends java.lang.Object
      implements PriorityQueue<E>

  a binary Min. heap priority queue implementation Note the value has to implement the Comparable interface (int compareTo(Object obj) )

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                            |
    |------------------------------------------------------------------------------------------------------------------------|
    | `BinaryHeap``()`                                                                                                       |
    | `BinaryHeap``(boolean isMinHeap)`                                                                                      |
    | `BinaryHeap``(int initialCapacity)`                                                                                    |
    | `BinaryHeap``(int initialCapacity, oracle.spatial.network.lod.BinaryHeap.IndexKeeper indexKeeper)`                     |
    | `BinaryHeap``(int initialCapacity, oracle.spatial.network.lod.BinaryHeap.IndexKeeper indexKeeper, boolean isMinHeap)`  |
    | `BinaryHeap``(int initialCapacity, boolean isMinHeap)`                                                                 |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                         |
    |--------------------|----------------------------------------------------------------|
    | `void`             | `clear``()`<br>Empties the queue.                              |
    | `E`                | `deleteMin``()`<br>Deletes the minimum element in the queue.   |
    | `E`                | `findMin``()`<br>Finds the minimum element in the queue.       |
    | `E`                | `getElementAtIndex``(int index)`                               |
    | `void`             | `insert``(E element)`<br>Inserts an element into the queue.    |
    | `boolean`          | `isEmpty``()`<br>Determines whether the queue is empty or not. |
    | `int`              | `size``()`<br>Returns the size of the queue.                   |
    | `java.lang.String` | `toString``()`                                                 |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### BinaryHeap

          public BinaryHeap()

    <!-- -->

    - #### BinaryHeap

          public BinaryHeap(boolean isMinHeap)

    <!-- -->

    - #### BinaryHeap

          public BinaryHeap(int initialCapacity)

    <!-- -->

    - #### BinaryHeap

          public BinaryHeap(int initialCapacity,
                            boolean isMinHeap)

    <!-- -->

    - #### BinaryHeap

          public BinaryHeap(int initialCapacity,
                            oracle.spatial.network.lod.BinaryHeap.IndexKeeper indexKeeper)

    <!-- -->

    - #### BinaryHeap

          public BinaryHeap(int initialCapacity,
                            oracle.spatial.network.lod.BinaryHeap.IndexKeeper indexKeeper,
                            boolean isMinHeap)

  <!-- -->

  - ### Method Detail

    - #### insert

          public void insert(E element)

      Description copied from interface: [`PriorityQueue`](PriorityQueue.md)
      Inserts an element into the queue.
      Specified by:
      [`insert`](PriorityQueue.md) in interface [`PriorityQueue`](PriorityQueue.md)`<E extends java.lang.Comparable>`

    <!-- -->

    - #### deleteMin

          public E deleteMin()

      Description copied from interface: [`PriorityQueue`](PriorityQueue.md)
      Deletes the minimum element in the queue.
      Specified by:
      [`deleteMin`](PriorityQueue.md) in interface [`PriorityQueue`](PriorityQueue.md)`<E extends java.lang.Comparable>`

      Returns:
      the minimum element in the queue. If the queue is empty, return null.

    <!-- -->

    - #### isEmpty

          public boolean isEmpty()

      Description copied from interface: [`PriorityQueue`](PriorityQueue.md)
      Determines whether the queue is empty or not.
      Specified by:

      [`isEmpty`](PriorityQueue.md) in interface [`PriorityQueue`](PriorityQueue.md)`<E extends java.lang.Comparable>`

      Returns:

    <!-- -->

    - #### getElementAtIndex

          public E getElementAtIndex(int index)

    <!-- -->

    - #### clear

          public void clear()

      Description copied from interface: [`PriorityQueue`](PriorityQueue.md)
      Empties the queue.
      Specified by:
      [`clear`](PriorityQueue.md) in interface [`PriorityQueue`](PriorityQueue.md)`<E extends java.lang.Comparable>`

    <!-- -->

    - #### size

          public int size()

      Description copied from interface: [`PriorityQueue`](PriorityQueue.md)
      Returns the size of the queue.
      Specified by:

      [`size`](PriorityQueue.md) in interface [`PriorityQueue`](PriorityQueue.md)`<E extends java.lang.Comparable>`

      Returns:

    <!-- -->

    - #### findMin

          public E findMin()

      Description copied from interface: [`PriorityQueue`](PriorityQueue.md)
      Finds the minimum element in the queue. This method is non-destructive peeking. The queue is left untouched.
      Specified by:
      [`findMin`](PriorityQueue.md) in interface [`PriorityQueue`](PriorityQueue.md)`<E extends java.lang.Comparable>`

      Returns:
      the minimum element in the queue. If the queue is empty, return null.

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

- [Prev Class](BidirectionalDijkstra.md)
- [Next Class](BreadthFirstSearch.md)

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
