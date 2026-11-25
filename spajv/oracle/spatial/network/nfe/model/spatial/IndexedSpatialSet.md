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

- Prev Class
- [Next Class](NFEFeatureElementGeoObject.md)

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

## Interface IndexedSpatialSet\<V extends [GeoObject](../../vis/maps/core/GeoObject.md)\>

- Type Parameters:
  `V` -

  <!-- -->

  All Superinterfaces:
  java.util.Collection\<V\>, java.lang.Iterable\<V\>, java.util.Set\<V\>

  <!-- -->

  All Known Implementing Classes:
  [RTreeIndexedSpatialSet](RTreeIndexedSpatialSet.md)

  ------------------------------------------------------------------------



      public interface IndexedSpatialSet<V extends GeoObject>
      extends java.util.Set<V>

  A set that is spatially indexed. Additionally to the functionality provided by a Set, it is possible to search items interacting with a geometry.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                      | Method and Description                                                                                                                       |
    |------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
    | `V`                                                                    | `get``(java.lang.Object key)`<br>Gets the object identified by the given key                                                                 |
    | `V`                                                                    | `get``(java.awt.geom.Point2D point, double tolerance)`<br>Gets the element which is closer to the given point but within the tolerance.      |
    | `java.util.Collection<V>`                                              | `getAll``(java.awt.geom.Point2D point, double tolerance)`<br>Gets all the elements which distance to the given point is within the tolerance |
    | `java.util.Collection<V>`                                              | `getAnyInteract``(java.awt.geom.Area area)`<br>Gets all the elements interacting in some way with the given area                             |
    | `java.util.Collection<V>`                                              | `getAnyInteract``(java.awt.geom.Rectangle2D mbr)`<br>Gets all the elements interacting in some way with the given rectangle                  |
    | [`AbstractSpatialIndex`](../../vis/maps/index/AbstractSpatialIndex.md) | `getSpatialindex``()`<br>Gets the underlying implementation used to perform spatial-indexing                                                 |
    | `boolean`                                                              | `refreshIndex``(java.lang.Object key)`<br>Rebuilds the index associated to an object identified by the given key                             |

    - ### Methods inherited from interface java.util.Set

      `add, addAll, clear, contains, containsAll, equals, hashCode, isEmpty, iterator, remove, removeAll, retainAll, size, spliterator, toArray, toArray`

    <!-- -->

    - ### Methods inherited from interface java.util.Collection

      `parallelStream, removeIf, stream`

    <!-- -->

    - ### Methods inherited from interface java.lang.Iterable

      `forEach`

<!-- -->

- - ### Method Detail

    - #### refreshIndex

          boolean refreshIndex(java.lang.Object key)

      Rebuilds the index associated to an object identified by the given key
      Parameters:
      `key` - an object's key

      Returns:
      true if the index could be refreshed

    <!-- -->

    - #### getSpatialindex

          AbstractSpatialIndex getSpatialindex()

      Gets the underlying implementation used to perform spatial-indexing
      Returns:
      an AbstractSpatialIndex instance

    <!-- -->

    - #### get

          V get(java.lang.Object key)

      Gets the object identified by the given key
      Parameters:
      `key` - an object's key

      Returns:
      the object associated to the key or null if no object is related to the key

    <!-- -->

    - #### get

          V get(java.awt.geom.Point2D point,
                double tolerance)

      Gets the element which is closer to the given point but within the tolerance.
      Parameters:
      `point` - a spatial point

      `tolerance` - the maximum distance an element can be from the point to be selected

      Returns:
      the element closest to the given point with a distance equal or less to the tolerance

    <!-- -->

    - #### getAll

          java.util.Collection<V> getAll(java.awt.geom.Point2D point,
                                         double tolerance)

      Gets all the elements which distance to the given point is within the tolerance
      Parameters:
      `point` - a spatial point

      `tolerance` - tolerance the maximum distance an element can be from the point to be selected

      Returns:
      a collection containing all the elements which distance to the given point is within the tolerance

    <!-- -->

    - #### getAnyInteract

          java.util.Collection<V> getAnyInteract(java.awt.geom.Rectangle2D mbr)

      Gets all the elements interacting in some way with the given rectangle
      Parameters:
      `mbr` - a rectangle

      Returns:
      a collection containing all the elements interacting in some way with the given rectangle

    <!-- -->

    - #### getAnyInteract

          java.util.Collection<V> getAnyInteract(java.awt.geom.Area area)

      Gets all the elements interacting in some way with the given area
      Parameters:
      `area` - a java area

      Returns:
      a collection containing all the elements interacting in some way with the given area

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

- Prev Class
- [Next Class](NFEFeatureElementGeoObject.md)

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
