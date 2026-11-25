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

- [Prev Class](PointOnNet.md)
- [Next Class](ShortestPath.md)

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

## Interface PriorityQueue\<E extends java.lang.Comparable\>

- All Known Subinterfaces:
  [IdentifiablePriorityQueue](IdentifiablePriorityQueue.md)\<E\>

  <!-- -->

  All Known Implementing Classes:
  [BinaryHeap](BinaryHeap.md), [IdentifiableBinaryHeap](IdentifiableBinaryHeap.md)

  ------------------------------------------------------------------------



      public interface PriorityQueue<E extends java.lang.Comparable>

  This interface defines the methods supported by a priority queue.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                         |
    |-------------------|----------------------------------------------------------------|
    | `void`            | `clear``()`<br>Empties the queue.                              |
    | `E`               | `deleteMin``()`<br>Deletes the minimum element in the queue.   |
    | `E`               | `findMin``()`<br>Finds the minimum element in the queue.       |
    | `void`            | `insert``(E element)`<br>Inserts an element into the queue.    |
    | `boolean`         | `isEmpty``()`<br>Determines whether the queue is empty or not. |
    | `int`             | `size``()`<br>Returns the size of the queue.                   |

<!-- -->

- - ### Method Detail

    - #### clear

          void clear()

      Empties the queue.

    <!-- -->

    - #### size

          int size()

      Returns the size of the queue.
      Returns:

    <!-- -->

    - #### insert

          void insert(E element)

      Inserts an element into the queue.
      Parameters:
      `element` -

    <!-- -->

    - #### isEmpty

          boolean isEmpty()

      Determines whether the queue is empty or not.
      Returns:

    <!-- -->

    - #### findMin

          E findMin()

      Finds the minimum element in the queue. This method is non-destructive peeking. The queue is left untouched.
      Returns:
      the minimum element in the queue. If the queue is empty, return null.

    <!-- -->

    - #### deleteMin

          E deleteMin()

      Deletes the minimum element in the queue.
      Returns:
      the minimum element in the queue. If the queue is empty, return null.

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

- [Prev Class](PointOnNet.md)
- [Next Class](ShortestPath.md)

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
