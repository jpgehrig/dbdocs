Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- Prev Class
- [Next Class](BatchedException.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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

oracle.olapi

## Class ArraySet

- java.lang.Object

- - java.util.AbstractCollection\<E\>

  - - java.util.AbstractList\<E\>

    - - java.util.ArrayList

      - - oracle.olapi.ArraySet

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.lang.Cloneable, java.lang.Iterable, java.util.Collection, java.util.List, java.util.RandomAccess, java.util.Set

  ------------------------------------------------------------------------



      public class ArraySet
      extends java.util.ArrayList
      implements java.util.Set

  A resizable-array implementation of the `Set` interface from the collections framework. A set cannot contain duplicate elements.
  For the `util` package documentation, see [Package java.util](http://docs.oracle.com/javase/6/docs/api/java/util/package-summary.html).

  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from class java.util.AbstractList

      `modCount`

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                      |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `ArraySet``()`<br>Creates an empty set.                                                                                                                                          |
    | `ArraySet``(java.util.Collection c)`<br>Creates a set that contains all of the elements of the specified `Collection` in the order returned by the iterator of the `Collection`. |
    | `ArraySet``(int initialCapacity)`<br>Creates an empty set whose size is the specified initial capacity.                                                                          |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                               |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`         | `add``(java.lang.Object o)`<br>Adds the specified element to the end of the set if the element is not already present in the set.    |
    | `boolean`         | `equals``(java.lang.Object o)`<br>Determines whether the specified `Object` contains the same set of elements as this `ArraySet`.    |
    | `int`             | `hashCode``()`<br>Gets the hash code value for the `ArraySet`, which is the sum of all of the hash codes of the elements of the set. |

    - ### Methods inherited from class java.util.ArrayList

      `add, addAll, addAll, clear, clone, contains, ensureCapacity, forEach, get, indexOf, isEmpty, iterator, lastIndexOf, listIterator, listIterator, remove, remove, removeAll, removeIf, removeRange, replaceAll, retainAll, set, size, sort, spliterator, subList, toArray, toArray, trimToSize`

    <!-- -->

    - ### Methods inherited from class java.util.AbstractCollection

      `containsAll, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `finalize, getClass, notify, notifyAll, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface java.util.Set

      `addAll, clear, contains, containsAll, isEmpty, iterator, remove, removeAll, retainAll, size, spliterator, toArray, toArray`

    <!-- -->

    - ### Methods inherited from interface java.util.Collection

      `parallelStream, removeIf, stream`

    <!-- -->

    - ### Methods inherited from interface java.lang.Iterable

      `forEach`

    <!-- -->

    - ### Methods inherited from interface java.util.List

      `containsAll`

<!-- -->

- - ### Constructor Detail

    - #### ArraySet

          public ArraySet()

      Creates an empty set.

    <!-- -->

    - #### ArraySet

          public ArraySet(java.util.Collection c)

      Creates a set that contains all of the elements of the specified `Collection` in the order returned by the iterator of the `Collection`.
      Parameters:
      `c` - A `Collection` that has the elements that you want the `ArraySet` to have.

    <!-- -->

    - #### ArraySet

          public ArraySet(int initialCapacity)

      Creates an empty set whose size is the specified initial capacity.
      Parameters:
      `initialCapacity` - An integer that specifies an initial size for the `ArraySet`.

  <!-- -->

  - ### Method Detail

    - #### add

          public boolean add(java.lang.Object o)

      Adds the specified element to the end of the set if the element is not already present in the set.
      Specified by:
      `add` in interface `java.util.Collection`

      Specified by:
      `add` in interface `java.util.List`

      Specified by:
      `add` in interface `java.util.Set`

      Overrides:
      `add` in class `java.util.ArrayList`

      Parameters:
      `o` - The element to add to the set.

      Returns:
      A `boolean` that is `true` if this method adds the element to the set or `false` if it does not.

    <!-- -->

    - #### equals

          public boolean equals(java.lang.Object o)

      Determines whether the specified `Object` contains the same set of elements as this `ArraySet`.
      Specified by:
      `equals` in interface `java.util.Collection`

      Specified by:
      `equals` in interface `java.util.List`

      Specified by:
      `equals` in interface `java.util.Set`

      Overrides:
      `equals` in class `java.util.AbstractList`

      Parameters:
      `o` - The `Object` to compare to the `ArraySet`.

      Returns:
      A `boolean` that is `true` if the elements of the `ArraySet` are the same as the specified `Object` or `false` if they are not.

    <!-- -->

    - #### hashCode

          public int hashCode()

      Gets the hash code value for the `ArraySet`, which is the sum of all of the hash codes of the elements of the set. The hash code of a `null` element is zero.
      Specified by:
      `hashCode` in interface `java.util.Collection`

      Specified by:
      `hashCode` in interface `java.util.List`

      Specified by:
      `hashCode` in interface `java.util.Set`

      Overrides:
      `hashCode` in class `java.util.AbstractList`

      Returns:
      An integer that is the hash code value for the `ArraySet`.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- Prev Class
- [Next Class](BatchedException.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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
