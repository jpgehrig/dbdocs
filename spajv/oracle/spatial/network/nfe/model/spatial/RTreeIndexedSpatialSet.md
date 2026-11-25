Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFESpatialModel.md)
- Next Class

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

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

oracle.spatial.network.nfe.model.spatial

## Class RTreeIndexedSpatialSet\<V extends [NFEGeoObject](NFEGeoObject.md)\>

- java.lang.Object

- - oracle.spatial.network.nfe.model.spatial.RTreeIndexedSpatialSet\<V\>

<!-- -->

- Type Parameters:
  `V` - The type of elements in the set. Any subclass of NFEGeoObject

  <!-- -->

  All Implemented Interfaces:
  java.lang.Iterable\<V\>, java.util.Collection\<V\>, java.util.Set\<V\>, [IndexedSpatialSet](IndexedSpatialSet.md)\<V\>

  ------------------------------------------------------------------------



      public class RTreeIndexedSpatialSet<V extends NFEGeoObject>
      extends java.lang.Object
      implements IndexedSpatialSet<V>

  An implementation of IndexedSpatialSet that uses an R-tree index and stores instances of NFEGeoObject.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                              |
    |----------------------------------------------------------------------------------------------------------|
    | `RTreeIndexedSpatialSet``()`                                                                             |
    | `RTreeIndexedSpatialSet``(int[] expectedGeometryTypes)`<br>Creates an instance of RTreeIndexedSpatialSet |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                      | Method and Description                                                                                                                       |
    |------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                                              | `add``(V geoObj)`                                                                                                                            |
    | `boolean`                                                              | `addAll``(java.util.Collection<? extends V> geoObjects)`                                                                                     |
    | `void`                                                                 | `clear``()`                                                                                                                                  |
    | `boolean`                                                              | `contains``(java.lang.Object obj)`                                                                                                           |
    | `boolean`                                                              | `containsAll``(java.util.Collection<?> geoObjects)`                                                                                          |
    | `V`                                                                    | `get``(java.lang.Object key)`<br>Gets the object identified by the given key                                                                 |
    | `V`                                                                    | `get``(java.awt.geom.Point2D point, double tolerance)`<br>Gets the element which is closer to the given point but within the tolerance.      |
    | `java.util.Collection<V>`                                              | `getAll``(java.awt.geom.Point2D point, double tolerance)`<br>Gets all the elements which distance to the given point is within the tolerance |
    | `java.util.Collection<V>`                                              | `getAnyInteract``(java.awt.geom.Area area)`<br>Gets all the elements interacting in some way with the given area                             |
    | `java.util.Collection<V>`                                              | `getAnyInteract``(java.awt.geom.Rectangle2D mbr)`<br>Gets all the elements interacting in some way with the given rectangle                  |
    | [`AbstractSpatialIndex`](../../vis/maps/index/AbstractSpatialIndex.md) | `getSpatialindex``()`<br>Gets the underlying implementation used to perform spatial-indexing                                                 |
    | `boolean`                                                              | `isEmpty``()`                                                                                                                                |
    | `boolean`                                                              | `isGeometryTypeExpected``(int geometryType)`<br>Tells whether the set is expecting the specified geometry type (from JGeometry).             |
    | `java.util.Iterator<V>`                                                | `iterator``()`                                                                                                                               |
    | `boolean`                                                              | `refreshIndex``(java.lang.Object key)`<br>Rebuilds the index associated to an object identified by the given key                             |
    | `boolean`                                                              | `remove``(java.lang.Object obj)`                                                                                                             |
    | `boolean`                                                              | `removeAll``(java.util.Collection<?> geoObjects)`                                                                                            |
    | `boolean`                                                              | `retainAll``(java.util.Collection<?> arg0)`                                                                                                  |
    | `int`                                                                  | `size``()`                                                                                                                                   |
    | `java.lang.Object[]`                                                   | `toArray``()`                                                                                                                                |
    | `<T> T[]`                                                              | `toArray``(T[] array)`                                                                                                                       |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface java.util.Set

      `equals, hashCode, spliterator`

    <!-- -->

    - ### Methods inherited from interface java.util.Collection

      `parallelStream, removeIf, stream`

    <!-- -->

    - ### Methods inherited from interface java.lang.Iterable

      `forEach`

<!-- -->

- - ### Constructor Detail

    - #### RTreeIndexedSpatialSet

          public RTreeIndexedSpatialSet()

    <!-- -->

    - #### RTreeIndexedSpatialSet

          public RTreeIndexedSpatialSet(int[] expectedGeometryTypes)

      Creates an instance of RTreeIndexedSpatialSet
      Parameters:
      `geometryTypes` - A list of geometry types (from JGeometry) which will be expected to be contained in the set. By providing this values, spatial searches may be optimized since only geometries of the expected types will be looked.

  <!-- -->

  - ### Method Detail

    - #### getSpatialindex

          public AbstractSpatialIndex getSpatialindex()

      Description copied from interface: [`IndexedSpatialSet`](IndexedSpatialSet.md)
      Gets the underlying implementation used to perform spatial-indexing
      Specified by:
      [`getSpatialindex`](IndexedSpatialSet.md) in interface [`IndexedSpatialSet`](IndexedSpatialSet.md)`<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

      Returns:
      an AbstractSpatialIndex instance

    <!-- -->

    - #### add

          public boolean add(V geoObj)

      Specified by:
      `add` in interface `java.util.Collection<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

      Specified by:
      `add` in interface `java.util.Set<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

    <!-- -->

    - #### size

          public int size()

      Specified by:
      `size` in interface `java.util.Collection<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

      Specified by:
      `size` in interface `java.util.Set<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

    <!-- -->

    - #### isEmpty

          public boolean isEmpty()

      Specified by:
      `isEmpty` in interface `java.util.Collection<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

      Specified by:
      `isEmpty` in interface `java.util.Set<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

    <!-- -->

    - #### clear

          public void clear()

      Specified by:
      `clear` in interface `java.util.Collection<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

      Specified by:
      `clear` in interface `java.util.Set<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

    <!-- -->

    - #### refreshIndex

          public boolean refreshIndex(java.lang.Object key)

      Description copied from interface: [`IndexedSpatialSet`](IndexedSpatialSet.md)
      Rebuilds the index associated to an object identified by the given key
      Specified by:
      [`refreshIndex`](IndexedSpatialSet.md) in interface [`IndexedSpatialSet`](IndexedSpatialSet.md)`<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

      Parameters:
      `key` - an object's key

      Returns:
      true if the index could be refreshed

    <!-- -->

    - #### get

          public V get(java.lang.Object key)

      Description copied from interface: [`IndexedSpatialSet`](IndexedSpatialSet.md)
      Gets the object identified by the given key
      Specified by:
      [`get`](IndexedSpatialSet.md) in interface [`IndexedSpatialSet`](IndexedSpatialSet.md)`<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

      Parameters:
      `key` - an object's key

      Returns:
      the object associated to the key or null if no object is related to the key

    <!-- -->

    - #### get

          public V get(java.awt.geom.Point2D point,
                       double tolerance)

      Description copied from interface: [`IndexedSpatialSet`](IndexedSpatialSet.md)
      Gets the element which is closer to the given point but within the tolerance.
      Specified by:
      [`get`](IndexedSpatialSet.md) in interface [`IndexedSpatialSet`](IndexedSpatialSet.md)`<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

      Parameters:
      `point` - a spatial point

      `tolerance` - the maximum distance an element can be from the point to be selected

      Returns:
      the element closest to the given point with a distance equal or less to the tolerance

    <!-- -->

    - #### getAll

          public java.util.Collection<V> getAll(java.awt.geom.Point2D point,
                                                double tolerance)

      Description copied from interface: [`IndexedSpatialSet`](IndexedSpatialSet.md)
      Gets all the elements which distance to the given point is within the tolerance
      Specified by:
      [`getAll`](IndexedSpatialSet.md) in interface [`IndexedSpatialSet`](IndexedSpatialSet.md)`<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

      Parameters:
      `point` - a spatial point

      `tolerance` - tolerance the maximum distance an element can be from the point to be selected

      Returns:
      a collection containing all the elements which distance to the given point is within the tolerance

    <!-- -->

    - #### getAnyInteract

          public java.util.Collection<V> getAnyInteract(java.awt.geom.Rectangle2D mbr)

      Description copied from interface: [`IndexedSpatialSet`](IndexedSpatialSet.md)
      Gets all the elements interacting in some way with the given rectangle
      Specified by:
      [`getAnyInteract`](IndexedSpatialSet.md) in interface [`IndexedSpatialSet`](IndexedSpatialSet.md)`<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

      Parameters:
      `mbr` - a rectangle

      Returns:
      a collection containing all the elements interacting in some way with the given rectangle

    <!-- -->

    - #### getAnyInteract

          public java.util.Collection<V> getAnyInteract(java.awt.geom.Area area)

      Description copied from interface: [`IndexedSpatialSet`](IndexedSpatialSet.md)
      Gets all the elements interacting in some way with the given area
      Specified by:
      [`getAnyInteract`](IndexedSpatialSet.md) in interface [`IndexedSpatialSet`](IndexedSpatialSet.md)`<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

      Parameters:
      `area` - a java area

      Returns:
      a collection containing all the elements interacting in some way with the given area

    <!-- -->

    - #### addAll

          public boolean addAll(java.util.Collection<? extends V> geoObjects)

      Specified by:
      `addAll` in interface `java.util.Collection<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

      Specified by:
      `addAll` in interface `java.util.Set<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

    <!-- -->

    - #### contains

          public boolean contains(java.lang.Object obj)

      Specified by:
      `contains` in interface `java.util.Collection<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

      Specified by:
      `contains` in interface `java.util.Set<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

    <!-- -->

    - #### containsAll

          public boolean containsAll(java.util.Collection<?> geoObjects)

      Specified by:
      `containsAll` in interface `java.util.Collection<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

      Specified by:
      `containsAll` in interface `java.util.Set<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

    <!-- -->

    - #### iterator

          public java.util.Iterator<V> iterator()

      Specified by:
      `iterator` in interface `java.lang.Iterable<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

      Specified by:
      `iterator` in interface `java.util.Collection<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

      Specified by:
      `iterator` in interface `java.util.Set<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

    <!-- -->

    - #### remove

          public boolean remove(java.lang.Object obj)

      Specified by:
      `remove` in interface `java.util.Collection<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

      Specified by:
      `remove` in interface `java.util.Set<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

    <!-- -->

    - #### removeAll

          public boolean removeAll(java.util.Collection<?> geoObjects)

      Specified by:
      `removeAll` in interface `java.util.Collection<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

      Specified by:
      `removeAll` in interface `java.util.Set<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

    <!-- -->

    - #### retainAll

          public boolean retainAll(java.util.Collection<?> arg0)

      Specified by:
      `retainAll` in interface `java.util.Collection<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

      Specified by:
      `retainAll` in interface `java.util.Set<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

    <!-- -->

    - #### toArray

          public java.lang.Object[] toArray()

      Specified by:
      `toArray` in interface `java.util.Collection<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

      Specified by:
      `toArray` in interface `java.util.Set<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

    <!-- -->

    - #### toArray

          public <T> T[] toArray(T[] array)

      Specified by:
      `toArray` in interface `java.util.Collection<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

      Specified by:
      `toArray` in interface `java.util.Set<V extends `[`NFEGeoObject`](NFEGeoObject.md)`>`

    <!-- -->

    - #### isGeometryTypeExpected

          public boolean isGeometryTypeExpected(int geometryType)

      Tells whether the set is expecting the specified geometry type (from JGeometry). If the set has no expected geometry types defined it will always return true for any type.
      Parameters:

      `geometryType` -

      Returns:

Skip navigation links

- [Overview](../../../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../../../deprecated-list.md)
- [Index](../../../../../../index-all.md)
- [Help](../../../../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](NFESpatialModel.md)
- Next Class

<!-- -->

- [Frames](../../../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../../../allclasses-noframe.md)

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
