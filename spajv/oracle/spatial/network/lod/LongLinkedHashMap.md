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

- [Prev Class](LongHashSet.md)
- [Next Class](LRUCachingHandler.md)

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

## Class LongLinkedHashMap\<V\>

- java.lang.Object

- - [oracle.spatial.network.lod.LongHashMap](LongHashMap.md)\<V\>

  - - oracle.spatial.network.lod.LongLinkedHashMap\<V\>

<!-- -->

-

  ------------------------------------------------------------------------



      public class LongLinkedHashMap<V>
      extends LongHashMap<V>

  This is a bare-bones, application specific, optimized ordered hash map implementation.
  Since:
  release specific (what release of product did this appear in)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                         |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `LongLinkedHashMap``()`<br>Constructs an empty insertion-ordered `LinkedHashMap` instance with the default initial capacity (16) and load factor (0.75).                            |
    | `LongLinkedHashMap``(int initialCapacity)`<br>Constructs an empty insertion-ordered `LinkedHashMap` instance with the specified initial capacity and a default load factor (0.75).  |
    | `LongLinkedHashMap``(int initialCapacity, float loadFactor)`<br>Constructs an empty insertion-ordered `LinkedHashMap` instance with the specified initial capacity and load factor. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type       | Method and Description                                                                 |
    |-------------------------|----------------------------------------------------------------------------------------|
    | `void`                  | `clear``()`<br>Removes all of the mappings from this map.                              |
    | `long[]`                | `keys``()`<br>Returns `true` if this map maps one or more keys to the specified value. |
    | `long[]`                | `keysReverse``()`                                                                      |
    | `java.util.Iterator<V>` | `valuesIterator``()`                                                                   |
    | `java.util.Iterator<V>` | `valuesReverseIterator``()`                                                            |

    - ### Methods inherited from class oracle.spatial.network.lod.[LongHashMap](LongHashMap.md)

      [`clone`](LongHashMap.md)`, `[`containsKey`](LongHashMap.md)`, `[`get`](LongHashMap.md)`, `[`getRehashTime`](LongHashMap.md)`, `[`getStatistics`](LongHashMap.md)`, `[`isEmpty`](LongHashMap.md)`, `[`put`](LongHashMap.md)`, `[`remove`](LongHashMap.md)`, `[`size`](LongHashMap.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### LongLinkedHashMap

          public LongLinkedHashMap(int initialCapacity,
                                   float loadFactor)

      Constructs an empty insertion-ordered `LinkedHashMap` instance with the specified initial capacity and load factor.
      Parameters:
      `initialCapacity` - the initial capacity

      `loadFactor` - the load factor

      Throws:
      `java.lang.IllegalArgumentException` - if the initial capacity is negative or the load factor is nonpositive

    <!-- -->

    - #### LongLinkedHashMap

          public LongLinkedHashMap(int initialCapacity)

      Constructs an empty insertion-ordered `LinkedHashMap` instance with the specified initial capacity and a default load factor (0.75).
      Parameters:
      `initialCapacity` - the initial capacity

      Throws:
      `java.lang.IllegalArgumentException` - if the initial capacity is negative

    <!-- -->

    - #### LongLinkedHashMap

          public LongLinkedHashMap()

      Constructs an empty insertion-ordered `LinkedHashMap` instance with the default initial capacity (16) and load factor (0.75).

  <!-- -->

  - ### Method Detail

    - #### keys

          public long[] keys()

      Returns `true` if this map maps one or more keys to the specified value.
      Overrides:
      [`keys`](LongHashMap.md) in class [`LongHashMap`](LongHashMap.md)`<V>`

      Parameters:
      `value` - value whose presence in this map is to be tested

      Returns:
      `true` if this map maps one or more keys to the specified value

    <!-- -->

    - #### keysReverse

          public long[] keysReverse()

    <!-- -->

    - #### valuesIterator

          public java.util.Iterator<V> valuesIterator()

      Overrides:
      [`valuesIterator`](LongHashMap.md) in class [`LongHashMap`](LongHashMap.md)`<V>`

    <!-- -->

    - #### valuesReverseIterator

          public java.util.Iterator<V> valuesReverseIterator()

    <!-- -->

    - #### clear

          public void clear()

      Removes all of the mappings from this map. The map will be empty after this call returns.
      Overrides:
      [`clear`](LongHashMap.md) in class [`LongHashMap`](LongHashMap.md)`<V>`

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

- [Prev Class](LongHashSet.md)
- [Next Class](LRUCachingHandler.md)

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
