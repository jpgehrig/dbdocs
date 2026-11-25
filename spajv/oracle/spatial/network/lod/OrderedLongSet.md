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

- [Prev Class](NodeNotFoundException.md)
- [Next Class](PairwiseCostCalculator.md)

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

## Class OrderedLongSet

- java.lang.Object

- - oracle.spatial.network.lod.OrderedLongSet

<!-- -->

- All Implemented Interfaces:
  java.lang.Cloneable

  ------------------------------------------------------------------------



      public class OrderedLongSet
      extends java.lang.Object
      implements java.lang.Cloneable

  Ordered Long Set
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description              |
    |------------------------------------------|
    | `OrderedLongSet``()`                     |
    | `OrderedLongSet``(int initialCapacity)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                    | Method and Description |
    |--------------------------------------|------------------------|
    | `boolean`                            | `add``(long id)`       |
    | `java.lang.Object`                   | `clone``()`            |
    | `boolean`                            | `contains``(long id)`  |
    | `java.util.Iterator<java.lang.Long>` | `iterator``()`         |
    | `boolean`                            | `remove``(long id)`    |
    | `int`                                | `size``()`             |
    | `long[]`                             | `toArray``()`          |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### OrderedLongSet

          public OrderedLongSet()

    <!-- -->

    - #### OrderedLongSet

          public OrderedLongSet(int initialCapacity)

  <!-- -->

  - ### Method Detail

    - #### add

          public boolean add(long id)

    <!-- -->

    - #### remove

          public boolean remove(long id)

    <!-- -->

    - #### contains

          public boolean contains(long id)

    <!-- -->

    - #### iterator

          public java.util.Iterator<java.lang.Long> iterator()

    <!-- -->

    - #### size

          public int size()

    <!-- -->

    - #### toArray

          public long[] toArray()

    <!-- -->

    - #### clone

          public java.lang.Object clone()

      Overrides:
      `clone` in class `java.lang.Object`

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

- [Prev Class](NodeNotFoundException.md)
- [Next Class](PairwiseCostCalculator.md)

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
