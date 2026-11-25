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

- [Prev Class](IntersectionMember.md)
- [Next Class](LineIntersectionMember.md)

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

oracle.spatial.network.nfe.model.spatial.interaction

## Class LineIntersectionList\<E\>

- java.lang.Object

- - java.util.AbstractCollection\<E\>

  - - java.util.AbstractList\<E\>

    - - java.util.AbstractSequentialList\<E\>

      - - java.util.LinkedList\<[Intersection](Intersection.md)\<E\>\>

        - - oracle.spatial.network.nfe.model.spatial.interaction.LineIntersectionList\<E\>

<!-- -->

- Type Parameters:
  `E` - The type of intersection members contained in the list

  <!-- -->

  All Implemented Interfaces:
  java.io.Serializable, java.lang.Cloneable, java.lang.Iterable\<[Intersection](Intersection.md)\<E\>\>, java.util.Collection\<[Intersection](Intersection.md)\<E\>\>, java.util.Deque\<[Intersection](Intersection.md)\<E\>\>, java.util.List\<[Intersection](Intersection.md)\<E\>\>, java.util.Queue\<[Intersection](Intersection.md)\<E\>\>

  ------------------------------------------------------------------------



      public class LineIntersectionList<E>
      extends java.util.LinkedList<Intersection<E>>

  A list implementation that stores intersection across a line and facilitates sorting and finding those intersections
  See Also:
  [Serialized Form](../../../../../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                 |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `LineIntersectionList``(E element, `[`JGeometry`](../../../../../geometry/JGeometry.md)` line, double tolerance)`<br>Allocates a new line intersection list |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                   | Method and Description                                                                                                           |
    |-----------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                           | `add``(`[`Intersection`](Intersection.md)`<E> intersection)`                                                                     |
    | [`Intersection`](Intersection.md)`<E>`              | `findIntersection``(JGeometrySegmentPoint segPoint)`<br>Looks for an intersection taking place at the given line's segment point |
    | [`Intersection`](Intersection.md)`<E>`              | `findIntersection``(java.awt.geom.Point2D point)`<br>Looks for an intersection taking place at the given line's point            |
    | `E`                                                 | `getElement``()`<br>Gets the element represented by the line                                                                     |
    | [`JGeometry`](../../../../../geometry/JGeometry.md) | `getLine``()`<br>Gets the current line geometry                                                                                  |
    | `double`                                            | `getTolerance``()`<br>Gets the tolerance used to determine if two points can be considered the same point                        |

    - ### Methods inherited from class java.util.LinkedList

      `add, addAll, addAll, addFirst, addLast, clear, clone, contains, descendingIterator, element, get, getFirst, getLast, indexOf, lastIndexOf, listIterator, offer, offerFirst, offerLast, peek, peekFirst, peekLast, poll, pollFirst, pollLast, pop, push, remove, remove, remove, removeFirst, removeFirstOccurrence, removeLast, removeLastOccurrence, set, size, spliterator, toArray, toArray`

    <!-- -->

    - ### Methods inherited from class java.util.AbstractSequentialList

      `iterator`

    <!-- -->

    - ### Methods inherited from class java.util.AbstractList

      `equals, hashCode, listIterator, subList`

    <!-- -->

    - ### Methods inherited from class java.util.AbstractCollection

      `containsAll, isEmpty, removeAll, retainAll, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `getClass, notify, notifyAll, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface java.util.List

      `containsAll, equals, hashCode, isEmpty, iterator, listIterator, removeAll, replaceAll, retainAll, sort, subList`

    <!-- -->

    - ### Methods inherited from interface java.util.Deque

      `iterator`

    <!-- -->

    - ### Methods inherited from interface java.util.Collection

      `parallelStream, removeIf, stream`

    <!-- -->

    - ### Methods inherited from interface java.lang.Iterable

      `forEach`

<!-- -->

- - ### Constructor Detail

    - #### LineIntersectionList

          public LineIntersectionList(E element,
                                      JGeometry line,
                                      double tolerance)

      Allocates a new line intersection list
      Parameters:
      `element` - the element represented by the line

      `line` - the line where the intersections take place

      `tolerance` - the tolerance used to determine if a two points are the same point

  <!-- -->

  - ### Method Detail

    - #### findIntersection

          public Intersection<E> findIntersection(java.awt.geom.Point2D point)

      Looks for an intersection taking place at the given line's point
      Parameters:
      `point` - a point in the line

      Returns:
      an intersection if it was found

    <!-- -->

    - #### getElement

          public E getElement()

      Gets the element represented by the line
      Returns:
      an element owner of the line

    <!-- -->

    - #### getLine

          public JGeometry getLine()

      Gets the current line geometry
      Returns:
      a line string geometry

    <!-- -->

    - #### getTolerance

          public double getTolerance()

      Gets the tolerance used to determine if two points can be considered the same point
      Returns:
      a tolerance value

    <!-- -->

    - #### findIntersection

          public Intersection<E> findIntersection(JGeometrySegmentPoint segPoint)

      Looks for an intersection taking place at the given line's segment point
      Parameters:
      `segPoint` - a line's segment point

      Returns:
      an intersection if some was found

    <!-- -->

    - #### add

          public boolean add(Intersection<E> intersection)

      Specified by:
      `add` in interface `java.util.Collection<`[`Intersection`](Intersection.md)`<E>>`

      Specified by:
      `add` in interface `java.util.Deque<`[`Intersection`](Intersection.md)`<E>>`

      Specified by:
      `add` in interface `java.util.List<`[`Intersection`](Intersection.md)`<E>>`

      Specified by:
      `add` in interface `java.util.Queue<`[`Intersection`](Intersection.md)`<E>>`

      Overrides:
      `add` in class `java.util.LinkedList<`[`Intersection`](Intersection.md)`<E>>`

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

- [Prev Class](IntersectionMember.md)
- [Next Class](LineIntersectionMember.md)

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
