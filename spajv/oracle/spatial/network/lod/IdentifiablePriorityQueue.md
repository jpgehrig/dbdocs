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

- [Prev Class](IdentifiableBinaryHeap.md)
- [Next Class](InMemoryPairwisePathResultIO.md)

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

## Interface IdentifiablePriorityQueue\<E extends [Identifiable](Identifiable.md) & java.lang.Comparable\>

- All Superinterfaces:
  [PriorityQueue](PriorityQueue.md)\<E\>

  <!-- -->

  All Known Implementing Classes:
  [IdentifiableBinaryHeap](IdentifiableBinaryHeap.md)

  ------------------------------------------------------------------------



      public interface IdentifiablePriorityQueue<E extends Identifiable & java.lang.Comparable>
      extends PriorityQueue<E>

  This interface defines the methods supported by a priority queue.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                            |
    |-------------------|-------------------------------------------------------------------------------------------------------------------|
    | `E`               | `getElement``(long id)`<br>Returns the element with the input ID, if the element exists; otherwise, returns null. |
    | `E`               | `replaceElement``(long id, E newElement)`<br>Replace the old element of the specified id with a new element.      |

    - ### Methods inherited from interface oracle.spatial.network.lod.[PriorityQueue](PriorityQueue.md)

      [`clear`](PriorityQueue.md)`, `[`deleteMin`](PriorityQueue.md)`, `[`findMin`](PriorityQueue.md)`, `[`insert`](PriorityQueue.md)`, `[`isEmpty`](PriorityQueue.md)`, `[`size`](PriorityQueue.md)

<!-- -->

- - ### Method Detail

    - #### getElement

          E getElement(long id)

      Returns the element with the input ID, if the element exists; otherwise, returns null.
      Parameters:

      `id` - ID of the element

      Returns:

    <!-- -->

    - #### replaceElement

          E replaceElement(long id,
                           E newElement)

      Replace the old element of the specified id with a new element. The ID of the new element does not need to be the same as the old element. If the old element does not exist in the queue, then simply insert the new element into the queue.
      Parameters:

      `id` - ID of the old element

      `newElement` - new element

      Returns:

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

- [Prev Class](IdentifiableBinaryHeap.md)
- [Next Class](InMemoryPairwisePathResultIO.md)

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
