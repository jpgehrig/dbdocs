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

- [Prev Class](LogicalSubPathImpl.md)
- [Next Class](LongHashSet.md)

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

## Class LongHashMap\<V\>

- java.lang.Object

- - oracle.spatial.network.lod.LongHashMap\<V\>

<!-- -->

- Direct Known Subclasses:
  [LongHashTable](../nfe/util/LongHashTable.md), [LongLinkedHashMap](LongLinkedHashMap.md)

  ------------------------------------------------------------------------



      public class LongHashMap<V>
      extends java.lang.Object

  This is a bare-bones, application specific, optimized hash table implementation. We feel this will perform better than the java.util.HashMap implementation for our application both in terms of execution time and memory usage. This is an UNSYNCHRONIZED IMPLEMENTATION!
  Since:
  11g

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                             |
    |---------------------------------------------------------|
    | `LongHashMap``()`                                       |
    | `LongHashMap``(int initialCapacity)`                    |
    | `LongHashMap``(int initialCapacity, float loadFactor)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type       | Method and Description      |
    |-------------------------|-----------------------------|
    | `void`                  | `clear``()`                 |
    | `java.lang.Object`      | `clone``()`                 |
    | `boolean`               | `containsKey``(long key)`   |
    | `V`                     | `get``(long key)`           |
    | `static long`           | `getRehashTime``()`         |
    | `java.lang.String`      | `getStatistics``()`         |
    | `boolean`               | `isEmpty``()`               |
    | `long[]`                | `keys``()`                  |
    | `V`                     | `put``(long key, V value)`  |
    | `V`                     | `remove``(long key)`        |
    | `int`                   | `size``()`                  |
    | `java.util.Iterator<V>` | `valuesIterator``()`        |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### LongHashMap

          public LongHashMap(int initialCapacity,
                             float loadFactor)

    <!-- -->

    - #### LongHashMap

          public LongHashMap(int initialCapacity)

    <!-- -->

    - #### LongHashMap

          public LongHashMap()

  <!-- -->

  - ### Method Detail

    - #### size

          public final int size()

    <!-- -->

    - #### isEmpty

          public final boolean isEmpty()

    <!-- -->

    - #### getStatistics

          public final java.lang.String getStatistics()

    <!-- -->

    - #### put

          public final V put(long key,
                             V value)

    <!-- -->

    - #### containsKey

          public final boolean containsKey(long key)

    <!-- -->

    - #### get

          public final V get(long key)

    <!-- -->

    - #### remove

          public final V remove(long key)

    <!-- -->

    - #### valuesIterator

          public java.util.Iterator<V> valuesIterator()

    <!-- -->

    - #### getRehashTime

          public static long getRehashTime()

    <!-- -->

    - #### clear

          public void clear()

    <!-- -->

    - #### clone

          public java.lang.Object clone()

      Overrides:
      `clone` in class `java.lang.Object`

    <!-- -->

    - #### keys

          public long[] keys()

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

- [Prev Class](LogicalSubPathImpl.md)
- [Next Class](LongHashSet.md)

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
