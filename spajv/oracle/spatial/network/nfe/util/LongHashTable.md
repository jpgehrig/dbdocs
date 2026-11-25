Skip navigation links

- [Overview](../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](FileUtils.md)
- [Next Class](NFEFeatureUtils.md)

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.util

## Class LongHashTable\<V\>

- java.lang.Object

- - [oracle.spatial.network.lod.LongHashMap](../../lod/LongHashMap.md)\<V\>

  - - oracle.spatial.network.nfe.util.LongHashTable\<V\>

<!-- -->

- Type Parameters:
  `V` - The type of the values of the map.

  <!-- -->

  All Implemented Interfaces:
  java.util.Map\<java.lang.Long,V\>

  ------------------------------------------------------------------------



      public class LongHashTable<V>
      extends LongHashMap<V>
      implements java.util.Map<java.lang.Long,V>

  A subclass of [`LongHashMap`](../../lod/LongHashMap.md) that implements `Map` the interface.

<!-- -->

- - ### Nested Class Summary

    - ### Nested classes/interfaces inherited from interface java.util.Map

      `java.util.Map.Entry<K,V>`

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                        |
    |----------------------------------------------------|
    | `LongHashTable``()`                                |
    | `LongHashTable``(int capacity)`                    |
    | `LongHashTable``(int capacity, float loadFactor)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                      | Method and Description                                               |
    |--------------------------------------------------------|----------------------------------------------------------------------|
    | `boolean`                                              | `containsKey``(java.lang.Object key)`                                |
    | `boolean`                                              | `containsValue``(java.lang.Object value)`                            |
    | `java.util.Set<java.util.Map.Entry<java.lang.Long,V>>` | `entrySet``()`                                                       |
    | `V`                                                    | `get``(java.lang.Object key)`                                        |
    | `java.util.Set<java.lang.Long>`                        | `keySet``()`                                                         |
    | `V`                                                    | `put``(java.lang.Long key, V value)`                                 |
    | `void`                                                 | `putAll``(java.util.Map<? extends java.lang.Long,? extends V> map)`  |
    | `V`                                                    | `remove``(java.lang.Object key)`                                     |
    | `java.util.Collection<V>`                              | `values``()`                                                         |

    - ### Methods inherited from class oracle.spatial.network.lod.[LongHashMap](../../lod/LongHashMap.md)

      [`clear`](../../lod/LongHashMap.md)`, `[`clone`](../../lod/LongHashMap.md)`, `[`containsKey`](../../lod/LongHashMap.md)`, `[`get`](../../lod/LongHashMap.md)`, `[`getRehashTime`](../../lod/LongHashMap.md)`, `[`getStatistics`](../../lod/LongHashMap.md)`, `[`isEmpty`](../../lod/LongHashMap.md)`, `[`keys`](../../lod/LongHashMap.md)`, `[`put`](../../lod/LongHashMap.md)`, `[`remove`](../../lod/LongHashMap.md)`, `[`size`](../../lod/LongHashMap.md)`, `[`valuesIterator`](../../lod/LongHashMap.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface java.util.Map

      `clear, compute, computeIfAbsent, computeIfPresent, equals, forEach, getOrDefault, hashCode, isEmpty, merge, putIfAbsent, remove, replace, replace, replaceAll, size`

<!-- -->

- - ### Constructor Detail

    - #### LongHashTable

          public LongHashTable(int capacity,
                               float loadFactor)

    <!-- -->

    - #### LongHashTable

          public LongHashTable(int capacity)

    <!-- -->

    - #### LongHashTable

          public LongHashTable()

  <!-- -->

  - ### Method Detail

    - #### containsKey

          public boolean containsKey(java.lang.Object key)

      Specified by:
      `containsKey` in interface `java.util.Map<java.lang.Long,V>`

    <!-- -->

    - #### containsValue

          public boolean containsValue(java.lang.Object value)

      Specified by:
      `containsValue` in interface `java.util.Map<java.lang.Long,V>`

    <!-- -->

    - #### entrySet

          public java.util.Set<java.util.Map.Entry<java.lang.Long,V>> entrySet()

      Specified by:
      `entrySet` in interface `java.util.Map<java.lang.Long,V>`

    <!-- -->

    - #### get

          public V get(java.lang.Object key)

      Specified by:
      `get` in interface `java.util.Map<java.lang.Long,V>`

    <!-- -->

    - #### keySet

          public java.util.Set<java.lang.Long> keySet()

      Specified by:
      `keySet` in interface `java.util.Map<java.lang.Long,V>`

    <!-- -->

    - #### put

          public V put(java.lang.Long key,
                       V value)

      Specified by:
      `put` in interface `java.util.Map<java.lang.Long,V>`

    <!-- -->

    - #### putAll

          public void putAll(java.util.Map<? extends java.lang.Long,? extends V> map)

      Specified by:
      `putAll` in interface `java.util.Map<java.lang.Long,V>`

    <!-- -->

    - #### remove

          public V remove(java.lang.Object key)

      Specified by:
      `remove` in interface `java.util.Map<java.lang.Long,V>`

    <!-- -->

    - #### values

          public java.util.Collection<V> values()

      Specified by:
      `values` in interface `java.util.Map<java.lang.Long,V>`

Skip navigation links

- [Overview](../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../deprecated-list.md)
- [Index](../../../../../index-all.md)
- [Help](../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](FileUtils.md)
- [Next Class](NFEFeatureUtils.md)

<!-- -->

- [Frames](../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../allclasses-noframe.md)

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
