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

- Prev Class
- [Next Class](AbstractRTree.PairDebug.md)

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

## Class AbstractRTree\<T extends [RNode](RNode.md)\>

- java.lang.Object

- - java.util.AbstractCollection\<T\>

  - - oracle.spatial.geometry.AbstractRTree\<T\>

<!-- -->

- Type Parameters:
  `T` - The data type stored in this RTree

  <!-- -->

  All Implemented Interfaces:
  java.lang.Iterable\<T\>, java.util.Collection\<T\>, [RTreeInterface](RTreeInterface.md)\<T\>

  <!-- -->

  Direct Known Subclasses:
  [RStarTree](RStarTree.md)

  ------------------------------------------------------------------------



      public abstract class AbstractRTree<T extends RNode>
      extends java.util.AbstractCollection<T>
      implements RTreeInterface<T>

  This class provides a skeletal implementation of the [`RTreeInterface`](RTreeInterface.md) interface to minimize the effort required to implement an RTree.
  The programmer should generally provide a void (no argument) and collection constructor, as per the recommendation in the `Collection`interface specification.

  Methods which modify the RTree should increment modCount so the stream methods can detect concurrent modification.

  Subclasses should consider implementing:

  - Standard Collection constructors: a no-argument constructor and a constructor taking a Collection
  - clear
  - add
  - addAll (if preprocessing is helpful)
  - Iterator iterator(); (to handle remove)
  - remove
  - removeAll (if doing a spatial join is helpful)
  - removeIf
  - retainAll (if doing a spatial join is helpful)

  Since:
  release specific (what release of product did this appear in)

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Class and Description                                                                                                               |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------|
    | `static class `   | [`AbstractRTree.PairDebug`](AbstractRTree.PairDebug.md)`<`[`P`](AbstractRTree.PairDebug.md)`,`[`Q`](AbstractRTree.PairDebug.md)`>`  |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `AbstractRTree``()`         |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                          | Method and Description                                                                                                                                                                                                                 |
    |--------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                                                                  | `contains``(java.lang.Object obj)`                                                                                                                                                                                                     |
    | `boolean`                                                                                  | `containsAll``(java.util.Collection<?> c)`                                                                                                                                                                                             |
    | `void`                                                                                     | `forEach``(java.util.function.Predicate<? super `[`Mer`](Mer.md)`> merFilter, java.util.function.Consumer<? super T> action)`<br>The specified action is applied to every node that touches the search mer.                            |
    | `boolean`                                                                                  | `isEmpty``()`                                                                                                                                                                                                                          |
    | `<Q extends `[`RNode`](RNode.md)`>`<br>`java.util.stream.Stream<`[`Pair`](Pair.md)`<T,Q>>` | `join``(`[`RTreeInterface`](RTreeInterface.md)`<Q> rtree1, java.util.function.Predicate<? super `[`Mer`](Mer.md)`> merFilter)`<br>Do a join of this RTree with rtree1.                                                                 |
    | `java.util.stream.Stream<T>`                                                               | `search``(java.util.Comparator<? super `[`RNode`](RNode.md)`> compareFunc)`<br>Search the tree (Mers) in the order specified by the comparator.                                                                                        |
    | `java.util.stream.Stream<T>`                                                               | `search``(java.util.function.ToDoubleFunction<? super `[`RNode`](RNode.md)`> sortMetric)`<br>Search the tree of Mers in the order specified by the metric computed on the Mers of the tree.                                            |
    | `java.util.stream.Stream<T>`                                                               | `searchMer``(java.util.function.Predicate<? super `[`Mer`](Mer.md)`> merFilter)`<br>Return all the objects which satisfy the merFilter.                                                                                                |
    | `T`                                                                                        | `searchNearest``(java.util.Comparator<? super `[`RNode`](RNode.md)`> compareFunc)`<br>Return the first data element as specified by the comparator.                                                                                    |
    | `T`                                                                                        | `searchNearest``(java.util.function.ToDoubleFunction<? super `[`RNode`](RNode.md)`> sortMetric)`<br>Search the tree of Mers in the order specified by the metric computed on the Mers of the tree and return the single smallest item. |

    - ### Methods inherited from class java.util.AbstractCollection

      `add, addAll, clear, iterator, remove, removeAll, retainAll, size, toArray, toArray, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.geometry.[RTreeInterface](RTreeInterface.md)

      [`add`](RTreeInterface.md)`, `[`forEach`](RTreeInterface.md)`, `[`join`](RTreeInterface.md)`, `[`join`](RTreeInterface.md)`, `[`removeIf`](RTreeInterface.md)`, `[`removeIf`](RTreeInterface.md)`, `[`search`](RTreeInterface.md)`, `[`searchMer`](RTreeInterface.md)`, `[`searchNearest`](RTreeInterface.md)`, `[`size`](RTreeInterface.md)

    <!-- -->

    - ### Methods inherited from interface java.util.Collection

      `addAll, clear, equals, hashCode, iterator, parallelStream, remove, removeAll, removeIf, retainAll, spliterator, stream, toArray, toArray`

    <!-- -->

    - ### Methods inherited from interface java.lang.Iterable

      `forEach`

<!-- -->

- - ### Constructor Detail

    - #### AbstractRTree

          public AbstractRTree()

  <!-- -->

  - ### Method Detail

    - #### isEmpty

          public boolean isEmpty()

      Specified by:
      `isEmpty` in interface `java.util.Collection<T extends `[`RNode`](RNode.md)`>`

      Overrides:
      `isEmpty` in class `java.util.AbstractCollection<T extends `[`RNode`](RNode.md)`>`

    <!-- -->

    - #### searchMer

          public java.util.stream.Stream<T> searchMer(java.util.function.Predicate<? super Mer> merFilter)

      Description copied from interface: [`RTreeInterface`](RTreeInterface.md)
      Return all the objects which satisfy the merFilter. See note on **merFilter** in the javadoc for this interface. For example, to create a list of all data in tree touching targetMer: `List<T> touches = tree.searchmer(x -> targetMer.interacts(x)).collect(Collectors.toList());`
      Specified by:
      [`searchMer`](RTreeInterface.md) in interface [`RTreeInterface`](RTreeInterface.md)`<T extends `[`RNode`](RNode.md)`>`

      Parameters:
      `merFilter` - the search mer

      Returns:
      a Stream of the selected objects

    <!-- -->

    - #### search

          public java.util.stream.Stream<T> search(java.util.Comparator<? super RNode> compareFunc)

      Description copied from interface: [`RTreeInterface`](RTreeInterface.md)
      Search the tree (Mers) in the order specified by the comparator. Creates a priority queue of all Mers seen as it searches the tree, choosing which subtree to descend according to the comparator.
      To order the priority queue, compareFunc will be called multiple times per node visited. If your comparison function is expensive, consider using [`RTreeInterface.search(ToDoubleFunction)`](RTreeInterface.md) instead.

      Specified by:
      [`search`](RTreeInterface.md) in interface [`RTreeInterface`](RTreeInterface.md)`<T extends `[`RNode`](RNode.md)`>`

      Parameters:
      `compareFunc` - indicates which Mer or leaf is closer to the target. See note on **distance metric** in the javadoc for this interface.

      Returns:
      a Stream of the objects in the tree, sorted according to compareFunc

    <!-- -->

    - #### searchNearest

          public T searchNearest(java.util.Comparator<? super RNode> compareFunc)

      Description copied from interface: [`RTreeInterface`](RTreeInterface.md)
      Return the first data element as specified by the comparator.
      To order the priority queue, compareFunc will be called multiple times per node visited. If your comparison function is expensive, consider using [`RTreeInterface.searchNearest(ToDoubleFunction)`](RTreeInterface.md) instead.

      Specified by:
      [`searchNearest`](RTreeInterface.md) in interface [`RTreeInterface`](RTreeInterface.md)`<T extends `[`RNode`](RNode.md)`>`

      Parameters:
      `compareFunc` - indicates which Mer or leaf is closest to the target. See note on **distance metric** in the javadoc for this interface.

      Returns:
      the closest leaf data in the tree (according to compareFunc), or null if the tree is empty.

    <!-- -->

    - #### search

          public java.util.stream.Stream<T> search(java.util.function.ToDoubleFunction<? super RNode> sortMetric)

      Description copied from interface: [`RTreeInterface`](RTreeInterface.md)
      Search the tree of Mers in the order specified by the metric computed on the Mers of the tree. The sortMetric function is called only once per node visited or returned (including internal nodes of the tree).
      Distances of Double.POSITIVE_INFINITY will not be searched or returned. Data nodes of distance Double.NEGATIVE_INFINITY are returned immediately as they are found and may reduce the search effort.

      Specified by:
      [`search`](RTreeInterface.md) in interface [`RTreeInterface`](RTreeInterface.md)`<T extends `[`RNode`](RNode.md)`>`

      Parameters:
      `sortMetric` - indicates the "distance" to the target as a double value. See note on **distance metric** in the javadoc for this interface.

      Returns:
      a Stream of the objects in the tree, sorted according to sortMetric

    <!-- -->

    - #### searchNearest

          public T searchNearest(java.util.function.ToDoubleFunction<? super RNode> sortMetric)

      Description copied from interface: [`RTreeInterface`](RTreeInterface.md)
      Search the tree of Mers in the order specified by the metric computed on the Mers of the tree and return the single smallest item. The sortMetric function is called only once per node visited or returned.
      Distances of Double.POSITIVE_INFINITY will not be searched or returned. A data node with distance Double.NEGATIVE_INFINITY will be returned immediately if found.

      Specified by:
      [`searchNearest`](RTreeInterface.md) in interface [`RTreeInterface`](RTreeInterface.md)`<T extends `[`RNode`](RNode.md)`>`

      Parameters:
      `sortMetric` - indicates the "distance" to the target as a double value. See note on **distance metric** in the javadoc for this interface.

      Returns:
      the closest leaf data in the tree (according to sortMetric), or null if the tree is empty.

    <!-- -->

    - #### join

          public <Q extends RNode> java.util.stream.Stream<Pair<T,Q>> join(RTreeInterface<Q> rtree1,
                                                                           java.util.function.Predicate<? super Mer> merFilter)

      Description copied from interface: [`RTreeInterface`](RTreeInterface.md)
      Do a join of this RTree with rtree1. Only areas touching merFilter are joined. See note on **merFilter** in the javadoc for this interface.
      Specified by:
      [`join`](RTreeInterface.md) in interface [`RTreeInterface`](RTreeInterface.md)`<T extends `[`RNode`](RNode.md)`>`

      Type Parameters:
      `Q` - the type of the joined rtree

      Parameters:
      `rtree1` - the tree to join

      `merFilter` - restricts the area of the join

      Returns:
      pairs of items whose Mers interact

    <!-- -->

    - #### contains

          public boolean contains(java.lang.Object obj)

      Specified by:
      `contains` in interface `java.util.Collection<T extends `[`RNode`](RNode.md)`>`

      Overrides:
      `contains` in class `java.util.AbstractCollection<T extends `[`RNode`](RNode.md)`>`

    <!-- -->

    - #### containsAll

          public boolean containsAll(java.util.Collection<?> c)

      Specified by:
      `containsAll` in interface `java.util.Collection<T extends `[`RNode`](RNode.md)`>`

      Overrides:
      `containsAll` in class `java.util.AbstractCollection<T extends `[`RNode`](RNode.md)`>`

    <!-- -->

    - #### forEach

          public void forEach(java.util.function.Predicate<? super Mer> merFilter,
                              java.util.function.Consumer<? super T> action)

      Description copied from interface: [`RTreeInterface`](RTreeInterface.md)
      The specified action is applied to every node that touches the search mer. The merFilter is used to reduce the search space. See note on **merFilter** in the javadoc for this interface.
      Specified by:
      [`forEach`](RTreeInterface.md) in interface [`RTreeInterface`](RTreeInterface.md)`<T extends `[`RNode`](RNode.md)`>`

      Parameters:
      `merFilter` - selects the objects to be processed.

      `action` - the action to apply objects of interest.

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

- Prev Class
- [Next Class](AbstractRTree.PairDebug.md)

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
