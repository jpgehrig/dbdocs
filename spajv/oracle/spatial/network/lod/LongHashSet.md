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

- [Prev Class](LongHashMap.md)
- [Next Class](LongLinkedHashMap.md)

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

## Class LongHashSet

- java.lang.Object

- - oracle.spatial.network.lod.LongHashSet

<!-- -->

-

  ------------------------------------------------------------------------



      public class LongHashSet
      extends java.lang.Object

  This is a bare-bones, application specific, optimized hash set implementation. We feel this will perform better than the java.util.HashMap implementation for our application both in terms of execution time and memory usage. This is an UNSYNCHRONIZED IMPLEMENTATION!
  Since:
  Oracle Database 11g Release 2 (11.2)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                             |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `LongHashSet``()`<br>Constructs a new, empty set; the backing `HashMap` instance has default initial capacity (16) and load factor (0.75).                                              |
    | `LongHashSet``(java.util.Collection<java.lang.Long> c)`<br>Constructs a new set containing the elements in the specified collection.                                                    |
    | `LongHashSet``(int initialCapacity)`<br>Constructs a new, empty set; the backing `HashMap` instance has the specified initial capacity and default load factor, which is `0.75`.        |
    | `LongHashSet``(int initialCapacity, float loadFactor)`<br>Constructs a new, empty set; the backing `HashMap` instance has the specified initial capacity and the specified load factor. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                    |
    |--------------------|-----------------------------------------------------------------------------------------------------------|
    | `boolean`          | `add``(long o)`<br>Adds the specified element to this set if it is not already present.                   |
    | `void`             | `clear``()`<br>Removes all of the elements from this set.                                                 |
    | `java.lang.Object` | `clone``()`<br>Returns a shallow copy of this `HashSet` instance: the elements themselves are not cloned. |
    | `boolean`          | `contains``(long o)`<br>Returns `true` if this set contains the specified element.                        |
    | `boolean`          | `isEmpty``()`<br>Returns `true` if this set contains no elements.                                         |
    | `boolean`          | `remove``(long o)`<br>Removes the specified element from this set if it is present.                       |
    | `int`              | `size``()`<br>Returns the number of elements in this set (its cardinality).                               |
    | `long[]`           | `toArray``()`<br>Returns an array of the elements in this set.                                            |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### LongHashSet

          public LongHashSet()

      Constructs a new, empty set; the backing `HashMap` instance has default initial capacity (16) and load factor (0.75).

    <!-- -->

    - #### LongHashSet

          public LongHashSet(java.util.Collection<java.lang.Long> c)

      Constructs a new set containing the elements in the specified collection. The `HashMap` is created with default load factor (0.75) and an initial capacity sufficient to contain the elements in the specified collection.
      Parameters:
      `c` - the collection whose elements are to be placed into this set.

      Throws:
      `java.lang.NullPointerException` - if the specified collection is null.

    <!-- -->

    - #### LongHashSet

          public LongHashSet(int initialCapacity,
                             float loadFactor)

      Constructs a new, empty set; the backing `HashMap` instance has the specified initial capacity and the specified load factor.
      Parameters:
      `initialCapacity` - the initial capacity of the hash map.

      `loadFactor` - the load factor of the hash map.

      Throws:
      `java.lang.IllegalArgumentException` - if the initial capacity is less than zero, or if the load factor is nonpositive.

    <!-- -->

    - #### LongHashSet

          public LongHashSet(int initialCapacity)

      Constructs a new, empty set; the backing `HashMap` instance has the specified initial capacity and default load factor, which is `0.75`.
      Parameters:
      `initialCapacity` - the initial capacity of the hash table.

      Throws:
      `java.lang.IllegalArgumentException` - if the initial capacity is less than zero.

  <!-- -->

  - ### Method Detail

    - #### toArray

          public long[] toArray()

      Returns an array of the elements in this set. The elements are returned in no particular order.
      Returns:
      an array of the elements in this set.

      See Also:
      `ConcurrentModificationException`

    <!-- -->

    - #### size

          public int size()

      Returns the number of elements in this set (its cardinality).
      Returns:
      the number of elements in this set (its cardinality).

    <!-- -->

    - #### isEmpty

          public boolean isEmpty()

      Returns `true` if this set contains no elements.
      Returns:
      `true` if this set contains no elements.

    <!-- -->

    - #### contains

          public boolean contains(long o)

      Returns `true` if this set contains the specified element.
      Parameters:
      `o` - element whose presence in this set is to be tested.

      Returns:
      `true` if this set contains the specified element.

    <!-- -->

    - #### add

          public boolean add(long o)

      Adds the specified element to this set if it is not already present.
      Parameters:
      `o` - element to be added to this set.

      Returns:
      `true` if the set did not already contain the specified element.

    <!-- -->

    - #### remove

          public boolean remove(long o)

      Removes the specified element from this set if it is present.
      Parameters:
      `o` - object to be removed from this set, if present.

      Returns:
      `true` if the set contained the specified element.

    <!-- -->

    - #### clear

          public void clear()

      Removes all of the elements from this set.

    <!-- -->

    - #### clone

          public java.lang.Object clone()

      Returns a shallow copy of this `HashSet` instance: the elements themselves are not cloned.
      Overrides:
      `clone` in class `java.lang.Object`

      Returns:
      a shallow copy of this set.

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

- [Prev Class](LongHashMap.md)
- [Next Class](LongLinkedHashMap.md)

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
