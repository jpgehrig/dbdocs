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

- [Prev Class](RNode.md)
- [Next Class](RTreeInterface.md)

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

## Class RStarTree\<T extends [RNode](RNode.md)\>

- java.lang.Object

- - java.util.AbstractCollection\<T\>

  - - [oracle.spatial.geometry.AbstractRTree](AbstractRTree.md)\<T\>

    - - oracle.spatial.geometry.RStarTree\<T\>

<!-- -->

- Type Parameters:
  `T` -

  <!-- -->

  All Implemented Interfaces:
  java.io.Serializable, java.lang.Iterable\<T\>, java.util.Collection\<T\>, [RTreeInterface](RTreeInterface.md)\<T\>

  ------------------------------------------------------------------------



      public class RStarTree<T extends RNode>
      extends AbstractRTree<T>
      implements RTreeInterface<T>, java.io.Serializable

  TODO Must work for arbitrary dimension --- check that there's no 2D-specific stuff! An in-memory implementation of R\*-tree.
  All items must have the same dimension.

  Only leaf nodes may be inserted.

  Since:
  12.2

  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Nested Class Summary

    - ### Nested classes/interfaces inherited from class oracle.spatial.geometry.[AbstractRTree](AbstractRTree.md)

      [`AbstractRTree.PairDebug`](AbstractRTree.PairDebug.md)`<`[`P`](AbstractRTree.PairDebug.md)`,`[`Q`](AbstractRTree.PairDebug.md)`>`

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                           |
    |-----------------------------------------------------------------------|
    | `RStarTree``(int dim)`                                                |
    | `RStarTree``(int dim, java.util.Collection<? extends T> c)`           |
    | `RStarTree``(int dim, int minFill, int maxFill)`                      |
    | `RStarTree``(int dim, java.util.stream.Stream<? extends T> preload)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                 | Method and Description                                                                                                                                                                            |
    |---------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                         | `add``(T node)`<br>Insert a new node into an RTree.                                                                                                                                               |
    | `oracle.spatial.geometry.RStarTree.RStarInternal` | `getRoot``()`                                                                                                                                                                                     |
    | `java.util.Iterator<T>`                           | `iterator``()`                                                                                                                                                                                    |
    | `boolean`                                         | `remove``(java.lang.Object obj)`                                                                                                                                                                  |
    | `boolean`                                         | `removeIf``(java.util.function.Predicate<? super `[`Mer`](Mer.md)`> merFilter, java.util.function.Predicate<? super T> filter)`<br>Remove all nodes for which merFilter and filter are both true. |
    | `int`                                             | `size``()`<br>Gives the size of the tree.                                                                                                                                                         |

    - ### Methods inherited from class oracle.spatial.geometry.[AbstractRTree](AbstractRTree.md)

      [`contains`](AbstractRTree.md)`, `[`containsAll`](AbstractRTree.md)`, `[`forEach`](AbstractRTree.md)`, `[`isEmpty`](AbstractRTree.md)`, `[`join`](AbstractRTree.md)`, `[`search`](AbstractRTree.md)`, `[`search`](AbstractRTree.md)`, `[`searchMer`](AbstractRTree.md)`, `[`searchNearest`](AbstractRTree.md)`, `[`searchNearest`](AbstractRTree.md)

    <!-- -->

    - ### Methods inherited from class java.util.AbstractCollection

      `addAll, clear, removeAll, retainAll, toArray, toArray, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.geometry.[RTreeInterface](RTreeInterface.md)

      [`forEach`](RTreeInterface.md)`, `[`forEach`](RTreeInterface.md)`, `[`join`](RTreeInterface.md)`, `[`join`](RTreeInterface.md)`, `[`join`](RTreeInterface.md)`, `[`removeIf`](RTreeInterface.md)`, `[`search`](RTreeInterface.md)`, `[`search`](RTreeInterface.md)`, `[`search`](RTreeInterface.md)`, `[`searchMer`](RTreeInterface.md)`, `[`searchMer`](RTreeInterface.md)`, `[`searchNearest`](RTreeInterface.md)`, `[`searchNearest`](RTreeInterface.md)`, `[`searchNearest`](RTreeInterface.md)

    <!-- -->

    - ### Methods inherited from interface java.util.Collection

      `addAll, clear, contains, containsAll, equals, hashCode, isEmpty, parallelStream, removeAll, removeIf, retainAll, spliterator, stream, toArray, toArray`

    <!-- -->

    - ### Methods inherited from interface java.lang.Iterable

      `forEach`

<!-- -->

- - ### Constructor Detail

    - #### RStarTree

          public RStarTree(int dim,
                           int minFill,
                           int maxFill)

    <!-- -->

    - #### RStarTree

          public RStarTree(int dim)

    <!-- -->

    - #### RStarTree

          public RStarTree(int dim,
                           java.util.stream.Stream<? extends T> preload)

    <!-- -->

    - #### RStarTree

          public RStarTree(int dim,
                           java.util.Collection<? extends T> c)

  <!-- -->

  - ### Method Detail

    - #### size

          public int size()

      Description copied from interface: [`RTreeInterface`](RTreeInterface.md)
      Gives the size of the tree.
      Specified by:
      `size` in interface `java.util.Collection<T extends `[`RNode`](RNode.md)`>`

      Specified by:
      [`size`](RTreeInterface.md) in interface [`RTreeInterface`](RTreeInterface.md)`<T extends `[`RNode`](RNode.md)`>`

      Specified by:
      `size` in class `java.util.AbstractCollection<T extends `[`RNode`](RNode.md)`>`

      Returns:
      the number of data nodes in the tree.

    <!-- -->

    - #### getRoot

          public oracle.spatial.geometry.RStarTree.RStarInternal getRoot()

    <!-- -->

    - #### add

          public boolean add(T node)
                      throws java.lang.UnsupportedOperationException

      Description copied from interface: [`RTreeInterface`](RTreeInterface.md)
      Insert a new node into an RTree.
      Note that node.getMer() will be called repeatedly during RTree operations and should be efficient, typically implemented by the node caching a Mer which it returns on each call.

      node.isData() must return true.

      Specified by:
      `add` in interface `java.util.Collection<T extends `[`RNode`](RNode.md)`>`

      Specified by:
      [`add`](RTreeInterface.md) in interface [`RTreeInterface`](RTreeInterface.md)`<T extends `[`RNode`](RNode.md)`>`

      Overrides:
      `add` in class `java.util.AbstractCollection<T extends `[`RNode`](RNode.md)`>`

      Parameters:
      `node` - the node to insert

      Throws:
      `java.lang.UnsupportedOperationException` - if the tree does not support insertions

    <!-- -->

    - #### remove

          public boolean remove(java.lang.Object obj)
                         throws java.lang.UnsupportedOperationException,
                                java.util.NoSuchElementException

      Specified by:
      `remove` in interface `java.util.Collection<T extends `[`RNode`](RNode.md)`>`

      Overrides:
      `remove` in class `java.util.AbstractCollection<T extends `[`RNode`](RNode.md)`>`

      Throws:
      `java.lang.UnsupportedOperationException`

      `java.util.NoSuchElementException`

    <!-- -->

    - #### iterator

          public java.util.Iterator<T> iterator()

      Specified by:
      `iterator` in interface `java.lang.Iterable<T extends `[`RNode`](RNode.md)`>`

      Specified by:
      `iterator` in interface `java.util.Collection<T extends `[`RNode`](RNode.md)`>`

      Specified by:
      `iterator` in class `java.util.AbstractCollection<T extends `[`RNode`](RNode.md)`>`

    <!-- -->

    - #### removeIf

          public boolean removeIf(java.util.function.Predicate<? super Mer> merFilter,
                                  java.util.function.Predicate<? super T> filter)
                           throws java.lang.UnsupportedOperationException

      Description copied from interface: [`RTreeInterface`](RTreeInterface.md)
      Remove all nodes for which merFilter and filter are both true. The merFilter is used to reduce the search space. See note on **merFilter** in the javadoc for this interface. There are no restrictions on the tests done by filter, as it is only applied to the data nodes.
      Most users should instead use the simpler removeIf(Mer, Predicate).

      For example, if tree is an `RTree<JGeometry>`, we could remove all geometries smaller than 1000 m^2 that are completely contained in the Western hemisphere: `Mer westHemi = new Mer(2); westHemi.extend(-180, -90); westHemi.extend( 0, +90); tree.removeIf(x -> westHemi.interacts(x), x -> westHemi.covers(x) && x.area(0.001) < 1000); ` Note that `westHemi.covers(x)` violates the merFilter requirements and must be put in the filter predicate instead.

      Specified by:
      [`removeIf`](RTreeInterface.md) in interface [`RTreeInterface`](RTreeInterface.md)`<T extends `[`RNode`](RNode.md)`>`

      Parameters:
      `merFilter` - restricts the search area

      `filter` - the test for determining whether to remove a node

      Returns:
      true if any elements were removed

      Throws:
      `java.lang.UnsupportedOperationException` - if remove is not supported

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

- [Prev Class](RNode.md)
- [Next Class](RTreeInterface.md)

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
