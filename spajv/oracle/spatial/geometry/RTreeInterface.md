Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](RStarTree.md)
- [Next Class](Union.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

oracle.spatial.geometry

## Interface RTreeInterface\<T extends [RNode](RNode.md)\>

- Type Parameters:
  `T` - the type of object stored in the tree.

  <!-- -->

  All Superinterfaces:
  java.util.Collection\<T\>, java.lang.Iterable\<T\>

  <!-- -->

  All Known Subinterfaces:
  [RTreeInterface](../util/RTreeInterface.md)\<T\>

  <!-- -->

  All Known Implementing Classes:
  [AbstractRTree](AbstractRTree.md), [RStarTree](RStarTree.md)

  ------------------------------------------------------------------------



      public interface RTreeInterface<T extends RNode>
      extends java.util.Collection<T>

  An RTree or RTree-like data structure, in which objects are stored by Mers in a nested hierarchy where the Mer of each internal (non-data) node covers the Mers of all its descendents. Operations on R-Trees use this nested hierarchy to reduce search and join efforts. As a result, methods which take a comparator, a double-valued distance function, or a merFilter must return appropriate results on the larger Mers of internal tree nodes that match the leaf nodes that could be stored under that internal node. In particular:
  Distance metric
  The search methods take a distance metric parameter, either explicitly as a double-valued function or implicitly defined with a Comparator. The distance metric used must have the property that if Mer A is contained in Mer B, then the distance to Mer B is no larger than the distance to Mer A. Similarly, if leaf data L is contained in Mer B, then the distance to B is no larger than the distance to L (ties are fine).

  Comparators taking an RNode will be called both with the user's data and with internal nodes of the RTree. You can use `instanceof` to discover whether a node is data and do different processing, as long as that processing is consistent with the required property of a distance metric.

  merFilter
  Usually it is more appropriate to use a method that takes a Mer instead of a merFilter. The merFilter predicates are rarely needed.

  The merFilter predicate used in various methods must return true for the desired data **and** any internal node containing your desired data. Ensure that your merFilter returns true for any larger Mer that contains your desired Mers. The two most used merFilter predicates for a given targetMer are:

  - `x -> x.interacts(targetMer)` to find any object that might interact with targetMer
  - `x -> x.covers(targetMer)` to find an object whose mer is targetMer, or which interacts with all of a target object.

  Note that interacts is the behavior if you use a Mer instead of a merFilter predicate, and are encouraged to use the method that takes a Mer instead of a merFilter predicate.

  Multiples calls to getMer() on an object must return the same Mer for as long as the object is in the tree.

  Since:
  12.2

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Default Methods](javascript:show(16);)**

    | Modifier and Type                                                                                  | Method and Description                                                                                                                                                                                                                                                                            |
    |----------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                                                                          | `add``(T node)`<br>Insert a new node into an RTree.                                                                                                                                                                                                                                               |
    | `default void`                                                                                     | `forEach``(`[`Mer`](Mer.md)` targetMer, java.util.function.Consumer<? super T> action)`<br>The specified action is applied to every node that touches the targetMer.                                                                                                                              |
    | `void`                                                                                             | `forEach``(java.util.function.Predicate<? super `[`Mer`](Mer.md)`> merFilter, java.util.function.Consumer<? super T> action)`<br>The specified action is applied to every node that touches the search mer.                                                                                       |
    | `default <Q extends `[`RNode`](RNode.md)`>`<br>`java.util.stream.Stream<`[`Pair`](Pair.md)`<T,Q>>` | `join``(RTreeInterface<Q> rtree1)`<br>Do a join of this RTree with rtree1.                                                                                                                                                                                                                        |
    | `default <Q extends `[`RNode`](RNode.md)`>`<br>`java.util.stream.Stream<`[`Pair`](Pair.md)`<T,Q>>` | `join``(RTreeInterface<Q> rtree1, `[`Mer`](Mer.md)` targetMer)`<br>Do a join of this RTree with rtree1.                                                                                                                                                                                           |
    | `<Q extends `[`RNode`](RNode.md)`>`<br>`java.util.stream.Stream<`[`Pair`](Pair.md)`<T,Q>>`         | `join``(RTreeInterface<Q> rtree1, java.util.function.Predicate<? super `[`Mer`](Mer.md)`> merFilter)`<br>Do a join of this RTree with rtree1.                                                                                                                                                     |
    | `default boolean`                                                                                  | `removeIf``(`[`Mer`](Mer.md)` targetMer, java.util.function.Predicate<? super T> filter)`<br>Remove all nodes touching targetMer for which filter is true.                                                                                                                                        |
    | `boolean`                                                                                          | `removeIf``(java.util.function.Predicate<? super `[`Mer`](Mer.md)`> merFilter, java.util.function.Predicate<? super T> filter)`<br>Remove all nodes for which merFilter and filter are both true.                                                                                                 |
    | `java.util.stream.Stream<T>`                                                                       | `search``(java.util.Comparator<? super `[`RNode`](RNode.md)`> compareFunc)`<br>Search the tree (Mers) in the order specified by the comparator.                                                                                                                                                   |
    | `default java.util.stream.Stream<T>`                                                               | `search``(`[`JGeometry`](JGeometry.md)` targetGeom, java.lang.Class<T> classT, java.util.function.Function<? super T,`[`JGeometry`](JGeometry.md)`> geomField)`<br>Assuming each node contains a JGeometry, this method returns the data in this tree ordered by proximity to a target JGeometry. |
    | `java.util.stream.Stream<T>`                                                                       | `search``(java.util.function.ToDoubleFunction<? super `[`RNode`](RNode.md)`> sortMetric)`<br>Search the tree of Mers in the order specified by the metric computed on the Mers of the tree.                                                                                                       |
    | `default java.util.stream.Stream<T>`                                                               | `searchMer``(`[`Mer`](Mer.md)` targetMer)`<br>Return all the objects which touch the search mer.                                                                                                                                                                                                  |
    | `java.util.stream.Stream<T>`                                                                       | `searchMer``(java.util.function.Predicate<? super `[`Mer`](Mer.md)`> merFilter)`<br>Return all the objects which satisfy the merFilter.                                                                                                                                                           |
    | `T`                                                                                                | `searchNearest``(java.util.Comparator<? super `[`RNode`](RNode.md)`> compareFunc)`<br>Return the first data element as specified by the comparator.                                                                                                                                               |
    | `default T`                                                                                        | `searchNearest``(`[`JGeometry`](JGeometry.md)` targetGeom, java.lang.Class<T> classT, java.util.function.Function<? super T,`[`JGeometry`](JGeometry.md)`> geomField)`<br>Assuming each node contains a JGeometry, this method returns the closest node to a target JGeometry                     |
    | `T`                                                                                                | `searchNearest``(java.util.function.ToDoubleFunction<? super `[`RNode`](RNode.md)`> sortMetric)`<br>Search the tree of Mers in the order specified by the metric computed on the Mers of the tree and return the single smallest item.                                                            |
    | `int`                                                                                              | `size``()`<br>Gives the size of the tree.                                                                                                                                                                                                                                                         |

    - ### Methods inherited from interface java.util.Collection

      `addAll, clear, contains, containsAll, equals, hashCode, isEmpty, iterator, parallelStream, remove, removeAll, removeIf, retainAll, spliterator, stream, toArray, toArray`

    <!-- -->

    - ### Methods inherited from interface java.lang.Iterable

      `forEach`

<!-- -->

- - ### Method Detail

    - #### add

          boolean add(T node)
               throws java.lang.UnsupportedOperationException

      Insert a new node into an RTree.
      Note that node.getMer() will be called repeatedly during RTree operations and should be efficient, typically implemented by the node caching a Mer which it returns on each call.

      node.isData() must return true.

      Specified by:
      `add` in interface `java.util.Collection<T extends `[`RNode`](RNode.md)`>`

      Parameters:
      `node` - the node to insert

      Throws:
      `java.lang.UnsupportedOperationException` - if the tree does not support insertions

    <!-- -->

    - #### forEach

          void forEach(java.util.function.Predicate<? super Mer> merFilter,
                       java.util.function.Consumer<? super T> action)

      The specified action is applied to every node that touches the search mer. The merFilter is used to reduce the search space. See note on **merFilter** in the javadoc for this interface.
      Parameters:
      `merFilter` - selects the objects to be processed.

      `action` - the action to apply objects of interest.

    <!-- -->

    - #### forEach

          default void forEach(Mer targetMer,
                               java.util.function.Consumer<? super T> action)

      The specified action is applied to every node that touches the targetMer.
      Parameters:
      `targetMer` - selects the region where the forEach will be applied

      `action` - the action to apply objects of interest.

    <!-- -->

    - #### removeIf

          boolean removeIf(java.util.function.Predicate<? super Mer> merFilter,
                           java.util.function.Predicate<? super T> filter)
                    throws java.lang.UnsupportedOperationException

      Remove all nodes for which merFilter and filter are both true. The merFilter is used to reduce the search space. See note on **merFilter** in the javadoc for this interface. There are no restrictions on the tests done by filter, as it is only applied to the data nodes.
      Most users should instead use the simpler removeIf(Mer, Predicate).

      For example, if tree is an `RTree<JGeometry>`, we could remove all geometries smaller than 1000 m^2 that are completely contained in the Western hemisphere: `Mer westHemi = new Mer(2); westHemi.extend(-180, -90); westHemi.extend( 0, +90); tree.removeIf(x -> westHemi.interacts(x), x -> westHemi.covers(x) && x.area(0.001) < 1000); ` Note that `westHemi.covers(x)` violates the merFilter requirements and must be put in the filter predicate instead.

      Parameters:
      `merFilter` - restricts the search area

      `filter` - the test for determining whether to remove a node

      Returns:
      true if any elements were removed

      Throws:
      `java.lang.UnsupportedOperationException` - if remove is not supported

    <!-- -->

    - #### removeIf

          default boolean removeIf(Mer targetMer,
                                   java.util.function.Predicate<? super T> filter)
                            throws java.lang.UnsupportedOperationException

      Remove all nodes touching targetMer for which filter is true.
      Parameters:
      `targetMer` - restricts the search area

      `filter` - the test for determining whether to remove a node

      Returns:
      true if any elements were removed

      Throws:
      `java.lang.UnsupportedOperationException` - if remove is not supported

    <!-- -->

    - #### size

          int size()

      Gives the size of the tree.
      Specified by:
      `size` in interface `java.util.Collection<T extends `[`RNode`](RNode.md)`>`

      Returns:
      the number of data nodes in the tree.

    <!-- -->

    - #### searchMer

          java.util.stream.Stream<T> searchMer(java.util.function.Predicate<? super Mer> merFilter)

      Return all the objects which satisfy the merFilter. See note on **merFilter** in the javadoc for this interface. For example, to create a list of all data in tree touching targetMer: `List<T> touches = tree.searchmer(x -> targetMer.interacts(x)).collect(Collectors.toList());`
      Parameters:
      `merFilter` - the search mer

      `merFilter` - selector for the desired area of the tree

      Returns:
      a Stream of the selected objects

    <!-- -->

    - #### searchMer

          default java.util.stream.Stream<T> searchMer(Mer targetMer)

      Return all the objects which touch the search mer.
      Parameters:
      `targetMer` - the search mer

      Returns:
      a Stream of the overlapping objects

    <!-- -->

    - #### search

          java.util.stream.Stream<T> search(java.util.Comparator<? super RNode> compareFunc)

      Search the tree (Mers) in the order specified by the comparator. Creates a priority queue of all Mers seen as it searches the tree, choosing which subtree to descend according to the comparator.
      To order the priority queue, compareFunc will be called multiple times per node visited. If your comparison function is expensive, consider using `search(ToDoubleFunction)` instead.

      Parameters:
      `compareFunc` - indicates which Mer or leaf is closer to the target. See note on **distance metric** in the javadoc for this interface.

      Returns:
      a Stream of the objects in the tree, sorted according to compareFunc

    <!-- -->

    - #### search

          default java.util.stream.Stream<T> search(JGeometry targetGeom,
                                                    java.lang.Class<T> classT,
                                                    java.util.function.Function<? super T,JGeometry> geomField)

      Assuming each node contains a JGeometry, this method returns the data in this tree ordered by proximity to a target JGeometry.
      Example usage: Print the five customers closest to (85, 45) `class CustomerData implements RNode { private String label; private JGeometry geom; } RTreeInterface<CustomerData> customerRTree = new RStarTree<>(2, Arrays.stream(customerList)); customerRTree.search(new JGeometry(85, 45, 0), CustomerData.class, node -> node.geom).limit(5) .forEach(cust -> System.out.println(cust.label)); `

      Parameters:
      `targetGeom` - the target of the search

      `classT` - Specifies the concrete class of the type in the tree.

      `geomField` - A functiont that returns the JGeometry from the stored datatype.

      Returns:
      stream of the objects stored in this rtree, sorted by distance from targetGeom.

    <!-- -->

    - #### searchNearest

          default T searchNearest(JGeometry targetGeom,
                                  java.lang.Class<T> classT,
                                  java.util.function.Function<? super T,JGeometry> geomField)

      Assuming each node contains a JGeometry, this method returns the closest node to a target JGeometry
      Example usage: Print the customer closest to (85, 45) `class CustomerData implements RNode { private String label; private JGeometry geom; } RTreeInterface<CustomerData> customerRTree = new RStarTree<>(2, Arrays.stream(customerList)); System.out.println(customerRTree.searchNearest(new JGeometry(85, 45, 0), CustomerData.class, node -> node.geom)); `

      Parameters:
      `targetGeom` - the target of the search

      `classT` - Specifies the concrete class of the type in the tree.

      `geomField` - A functiont that returns the JGeometry from the stored datatype.

      Returns:
      stream of the objects stored in this rtree, sorted by distance from targetGeom.

    <!-- -->

    - #### searchNearest

          T searchNearest(java.util.Comparator<? super RNode> compareFunc)

      Return the first data element as specified by the comparator.
      To order the priority queue, compareFunc will be called multiple times per node visited. If your comparison function is expensive, consider using `searchNearest(ToDoubleFunction)` instead.

      Parameters:
      `compareFunc` - indicates which Mer or leaf is closest to the target. See note on **distance metric** in the javadoc for this interface.

      Returns:
      the closest leaf data in the tree (according to compareFunc), or null if the tree is empty.

    <!-- -->

    - #### search

          java.util.stream.Stream<T> search(java.util.function.ToDoubleFunction<? super RNode> sortMetric)

      Search the tree of Mers in the order specified by the metric computed on the Mers of the tree. The sortMetric function is called only once per node visited or returned (including internal nodes of the tree).
      Distances of Double.POSITIVE_INFINITY will not be searched or returned. Data nodes of distance Double.NEGATIVE_INFINITY are returned immediately as they are found and may reduce the search effort.

      Parameters:
      `sortMetric` - indicates the "distance" to the target as a double value. See note on **distance metric** in the javadoc for this interface.

      Returns:
      a Stream of the objects in the tree, sorted according to sortMetric

    <!-- -->

    - #### searchNearest

          T searchNearest(java.util.function.ToDoubleFunction<? super RNode> sortMetric)

      Search the tree of Mers in the order specified by the metric computed on the Mers of the tree and return the single smallest item. The sortMetric function is called only once per node visited or returned.
      Distances of Double.POSITIVE_INFINITY will not be searched or returned. A data node with distance Double.NEGATIVE_INFINITY will be returned immediately if found.

      Parameters:
      `sortMetric` - indicates the "distance" to the target as a double value. See note on **distance metric** in the javadoc for this interface.

      Returns:
      the closest leaf data in the tree (according to sortMetric), or null if the tree is empty.

    <!-- -->

    - #### join

          <Q extends RNode> java.util.stream.Stream<Pair<T,Q>> join(RTreeInterface<Q> rtree1,
                                                                    java.util.function.Predicate<? super Mer> merFilter)
                                                             throws java.lang.UnsupportedOperationException,
                                                                    java.lang.ClassCastException

      Do a join of this RTree with rtree1. Only areas touching merFilter are joined. See note on **merFilter** in the javadoc for this interface.
      Type Parameters:
      `Q` - the type of the joined rtree

      Parameters:
      `rtree1` - the tree to join

      `merFilter` - restricts the area of the join

      Returns:
      pairs of items whose Mers interact

      Throws:
      `java.lang.UnsupportedOperationException` - if unable to perform the requested type of join.

      `java.lang.ClassCastException` - if rtree1 is not same type as this RTreeInterface

    <!-- -->

    - #### join

          default <Q extends RNode> java.util.stream.Stream<Pair<T,Q>> join(RTreeInterface<Q> rtree1,
                                                                            Mer targetMer)
                                                                     throws java.lang.UnsupportedOperationException,
                                                                            java.lang.ClassCastException

      Do a join of this RTree with rtree1. Only areas touching targetMer are joined.
      Type Parameters:
      `Q` - the type of the joined rtree

      Parameters:
      `rtree1` - the tree to join

      `targetMer` - the region to join

      Returns:
      pairs of items whose Mers interact

      Throws:
      `java.lang.UnsupportedOperationException` - if unable to perform the requested type of join.

      `java.lang.ClassCastException` - if rtree1 is not same type as this RTreeInterface

    <!-- -->

    - #### join

          default <Q extends RNode> java.util.stream.Stream<Pair<T,Q>> join(RTreeInterface<Q> rtree1)
                                                                     throws java.lang.UnsupportedOperationException,
                                                                            java.lang.ClassCastException

      Do a join of this RTree with rtree1.
      Type Parameters:
      `Q` - the type of the joined rtree

      Parameters:
      `rtree1` - the tree to join

      Returns:
      pairs of items whose Mers interact

      Throws:
      `java.lang.UnsupportedOperationException` - if unable to perform the requested type of join.

      `java.lang.ClassCastException` - if rtree1 is not same type as this RTreeInterface

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- [Prev Class](RStarTree.md)
- [Next Class](Union.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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
