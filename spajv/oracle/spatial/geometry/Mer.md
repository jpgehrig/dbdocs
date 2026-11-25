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

- [Prev Class](LRSGeometryG3D.md)
- [Next Class](Ops.md)

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

## Class Mer

- java.lang.Object

- - oracle.spatial.geometry.Mer

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, [RNode](RNode.md)

  ------------------------------------------------------------------------



      public final class Mer
      extends java.lang.Object
      implements java.io.Serializable, RNode

  Provides helper methods for mers stored as bare arrays, as well as an encapsulated type. A mer provides lower bounds and upper bounds for an arbitrary number of dimensions (but usually 2 or 3). A non-empty Mer has its upper bound `>= ` lower bound for each dimension.
  A standard empty Mer as created by the `Mer(int)` constructor have POSITIVE_INFINITY for its lower bounds and NEGATIVE_INFINITY for its upper bounds (inverted relationship). All Mers used or output by this code are either non-empty or the standard empty Mer.

  Since:
  12.1

  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                 |
    |---------------------------------------------------------------------------------------------|
    | `Mer``(double[] arrayMer)`<br>Create a Mer from a bare array.                               |
    | `Mer``(double[] arrayMer, boolean deepCopy)`<br>Create a Mer from a bare array.             |
    | `Mer``(int dim)`<br>Create a mer that contains nothing; it can be extended into a real mer. |
    | `Mer``(Mer m)`<br>Copy constructor.                                                         |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                                                 |
    |--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static boolean`   | `covers``(double[] firstMer, double[] queryMer)`<br>Test if the query mer is completely covered by the first mer                                                       |
    | `boolean`          | `covers``(Mer query)`<br>Return true if this Mer completely covers the query mer.                                                                                      |
    | `int`              | `dim``()`<br>Return the dimension of this mer.                                                                                                                         |
    | `static double`    | `distance``(double[] merA, double[] merB)`<br>Return the Euclidean distance between two mers.                                                                          |
    | `double`           | `distance``(Mer targetMer)`<br>Return the Euclidean distance from this mer to targetMer.                                                                               |
    | `static double`    | `distance2``(double[] merA, double[] merB)`<br>Return square of the Euclidean distance between two mers.                                                               |
    | `double`           | `distance2``(Mer targetMer)`<br>Return square of the Euclidean distance from this mer to targetMer.                                                                    |
    | `static double[]`  | `emptyMer``(int dim)`<br>Create a new, standard empty mer of dimension dim.                                                                                            |
    | `void`             | `extend``(double[] pt)`<br>Extend this mer to include pt.                                                                                                              |
    | `static double[]`  | `extend``(double[] target, double[] ptMer)`<br>Extend a target MER to include a new MER or a new point.                                                                |
    | `static double[]`  | `extend``(double[] target, `[`JPoint2DD`](JPoint2DD.md)` pt)`<br>Extend a 2D target MER to include a new MER or a new point.                                           |
    | `void`             | `extend``(`[`JPoint2DD`](JPoint2DD.md)` pt)`<br>Extend this mer to include pt.                                                                                         |
    | `void`             | `extend``(Mer m)`<br>Extend this mer to include m.                                                                                                                     |
    | `double[]`         | `getArray``()`<br>Returns the mer as array - changing the returned array results in undefined behavior.                                                                |
    | `Mer`              | `getMer``()`<br>Returns the bounding box of this spatial object.                                                                                                       |
    | `double[][]`       | `getRanges``()`<br>Create and return a copy of the mer is an array of ranges, ` { {min x, max x}, {min y, max y}, etc.`                                                |
    | `static double[]`  | `infiniteMer``(int dim)`<br>Create a new mer that covers the universe (infinite extent).                                                                               |
    | `boolean`          | `interacts``(double[] pt)`<br>Return true if pt touches or is inside this mer.                                                                                         |
    | `static boolean`   | `interacts``(double[] target, double[] ptOrMer)`<br>Test if the point or mer touches the target mer.                                                                   |
    | `static boolean`   | `interacts``(double[] target, double[] ptMer, double tol)`<br>Test if the point or mer touches the target mer + tolerance.                                             |
    | `static boolean`   | `interacts``(double[] target, `[`JPoint2DD`](JPoint2DD.md)` pt)`<br>Test if the 2D MER contains the given point.                                                       |
    | `boolean`          | `interacts``(`[`JPoint2DD`](JPoint2DD.md)` pt)`<br>Return true if pt touches or is inside this mer.                                                                    |
    | `boolean`          | `interacts``(Mer target)`<br>Return true if target touches or is inside this mer.                                                                                      |
    | `boolean`          | `interacts``(Mer target, double tol)`<br>Return true if target touches or is inside this mer.                                                                          |
    | `static boolean`   | `interactsTile``(double[] tileMer, `[`JPoint2DD`](JPoint2DD.md)` pt)`<br>Test if the 2D MER contains the given point, excluding the right and bottom edges of the mer. |
    | `boolean`          | `interactsTile``(`[`JPoint2DD`](JPoint2DD.md)` pt)`<br>Return true if pt is inside this mer, or touches the top or left edge.                                          |
    | `boolean`          | `isEmpty``()`<br>Test whether this Mer is empty.                                                                                                                       |
    | `static boolean`   | `isEmpty``(double[] mer)`<br>Test whether a Mer is empty.                                                                                                              |
    | `java.lang.String` | `toString``()`                                                                                                                                                         |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### Mer

          public Mer(int dim)

      Create a mer that contains nothing; it can be extended into a real mer.
      Parameters:
      `dim` -

    <!-- -->

    - #### Mer

          public Mer(double[] arrayMer)

      Create a Mer from a bare array. The new Mer is a deep copy of the given array. `Mer(double[], boolean)`
      Parameters:
      `arrayMer` -

    <!-- -->

    - #### Mer

          public Mer(double[] arrayMer,
                     boolean deepCopy)

      Create a Mer from a bare array. The caller can specify whether a deep copy of the array is desired. Note that if deepCopy == false, behavior is undefined if arrayMer is later changed.
      Parameters:
      `arrayMer` -

      `deepCopy` -

    <!-- -->

    - #### Mer

          public Mer(Mer m)

      Copy constructor. Makes a deep copy of the specified Mer.
      Parameters:
      `m` -

  <!-- -->

  - ### Method Detail

    - #### extend

          public static final double[] extend(double[] target,
                                              double[] ptMer)

      Extend a target MER to include a new MER or a new point. Returns the extended target MER. Both must have same dimension dim.
      Parameters:
      `target` - the mer to extend (modified by this call).

      `ptMer` - the pt/mer to be included (if size dim, is a point; if size dim\*2, is a MER).

      Returns:
      the input target mer, extended to include pt

    <!-- -->

    - #### extend

          public static final double[] extend(double[] target,
                                              JPoint2DD pt)

      Extend a 2D target MER to include a new MER or a new point. Returns the extended target MER. Both must have same dimension dim.
      Parameters:
      `target` - the 2D mer to extend (modified by this call).

      `pt` - the pt/mer to be included (if size dim, is a point; if size dim\*2, is a MER).

      Returns:
      the input target mer, extended to include pt

    <!-- -->

    - #### interacts

          public static final boolean interacts(double[] target,
                                                double[] ptOrMer)

      Test if the point or mer touches the target mer.
      Parameters:
      `target` -

      `ptOrMer` - point if size = dim, mer if size = 2\*dim

      Returns:
      true iff ptOrMer touches the target Mer.

    <!-- -->

    - #### covers

          public static final boolean covers(double[] firstMer,
                                             double[] queryMer)

      Test if the query mer is completely covered by the first mer
      Parameters:
      `firstMer` -

      `queryMer` -

      Returns:
      true iff firstMer covers queryMer

    <!-- -->

    - #### interacts

          public static final boolean interacts(double[] target,
                                                double[] ptMer,
                                                double tol)

      Test if the point or mer touches the target mer + tolerance.
      Parameters:
      `target` -

      `ptMer` -

      `tol` - effectively expands (shrinks, if negative) the mer in all dimensions by this tolerance

      Returns:
      true iff

    <!-- -->

    - #### interacts

          public static final boolean interacts(double[] target,
                                                JPoint2DD pt)

      Test if the 2D MER contains the given point.
      Parameters:
      `target` -

      `pt` -

      Returns:
      true iff

    <!-- -->

    - #### interactsTile

          public static final boolean interactsTile(double[] tileMer,
                                                    JPoint2DD pt)

      Test if the 2D MER contains the given point, excluding the right and bottom edges of the mer. If a set of Mers tiles a region without overlapping, then a point in the region will test true for exactly one of those Mers.
      Parameters:

      `tileMer` -

      `pt` -

      Returns:

    <!-- -->

    - #### isEmpty

          public static final boolean isEmpty(double[] mer)

      Test whether a Mer is empty. A mer is empty if it has a lower bound larger than an upper bound for any dimension. For example, the `Mer(int)` constructor constructs an empty Mer with lower bounds of positibve infinity and upper bounds of negative infinity.
      Returns:
      true if the Mer is empty.

    <!-- -->

    - #### emptyMer

          public static final double[] emptyMer(int dim)

      Create a new, standard empty mer of dimension dim.
      Parameters:
      `dim` - the dimension to create

      Returns:
      the new, empty mer in standard form.

    <!-- -->

    - #### infiniteMer

          public static final double[] infiniteMer(int dim)

      Create a new mer that covers the universe (infinite extent).
      To create a correspoinding Mer object, use `new Mer(Mer.infiniteMer(dim))`

      Parameters:
      `dim` - the dimension to create

      Returns:
      the new, empty mer in standard form.

    <!-- -->

    - #### distance2

          public static final double distance2(double[] merA,
                                               double[] merB)

      Return square of the Euclidean distance between two mers. Mers which touch are distance zero. An empty Mer as created by `Mer(int)` is infinite distance from any other Mer; other non-standard empty Mers will provide unexpected results.
      Parameters:
      `merA` - first Mer

      `merB` - second Mer

      Returns:
      the distance between the two Mers

    <!-- -->

    - #### distance

          public static final double distance(double[] merA,
                                              double[] merB)

      Return the Euclidean distance between two mers. Mers which touch are distance zero. An empty Mer as created by `Mer(int)` is infinite distance from any other Mer; other non-standard empty Mers will provide unexpected results.
      Parameters:
      `merA` - first Mer

      `merB` - second Mer

      Returns:
      the distance between the two Mers

    <!-- -->

    - #### getArray

          public double[] getArray()

      Returns the mer as array - changing the returned array results in undefined behavior.
      Returns:
      the array we store the Mer in

    <!-- -->

    - #### getRanges

          public double[][] getRanges()

      Create and return a copy of the mer is an array of ranges, ` { {min x, max x}, {min y, max y}, etc. } `
      Returns:

    <!-- -->

    - #### extend

          public final void extend(Mer m)

      Extend this mer to include m.
      Parameters:
      `m` -

    <!-- -->

    - #### extend

          public final void extend(JPoint2DD pt)

      Extend this mer to include pt.
      Parameters:
      `pt` -

    <!-- -->

    - #### extend

          public final void extend(double[] pt)

      Extend this mer to include pt.
      Parameters:
      `pt` -

    <!-- -->

    - #### interacts

          public final boolean interacts(double[] pt)

      Return true if pt touches or is inside this mer.
      Parameters:

      `pt` -

      Returns:

    <!-- -->

    - #### interacts

          public final boolean interacts(JPoint2DD pt)

      Return true if pt touches or is inside this mer.
      Parameters:

      `pt` -

      Returns:

    <!-- -->

    - #### interacts

          public final boolean interacts(Mer target)

      Return true if target touches or is inside this mer.
      Parameters:

      `target` -

      Returns:

    <!-- -->

    - #### interacts

          public final boolean interacts(Mer target,
                                         double tol)

      Return true if target touches or is inside this mer.
      Parameters:

      `target` -

      `tol` - effectively expands (shrinks, if negative) this mer in all dimensions by this tolerance

      Returns:

    <!-- -->

    - #### interactsTile

          public final boolean interactsTile(JPoint2DD pt)

      Return true if pt is inside this mer, or touches the top or left edge. Useful for a set of MERs that tile the plane.
      Parameters:

      `pt` -

      Returns:

    <!-- -->

    - #### isEmpty

          public final boolean isEmpty()

      Test whether this Mer is empty. A mer is empty if it has a lower bound larger than an upper bound for any dimension. For example, the `Mer(int)` constructor constructs an empty Mer with lower bounds of positibve infinity and upper bounds of negative infinity.
      Returns:
      true if the Mer is empty.

    <!-- -->

    - #### dim

          public final int dim()

      Return the dimension of this mer.
      Returns:

    <!-- -->

    - #### covers

          public final boolean covers(Mer query)

      Return true if this Mer completely covers the query mer.
      Parameters:
      `query` - mer to test

      Returns:
      true if no part of query is beyond this mer.

    <!-- -->

    - #### distance2

          public final double distance2(Mer targetMer)

      Return square of the Euclidean distance from this mer to targetMer. Mers which touch are distance zero. An empty Mer as created by `Mer(int)` is infinite distance from any other Mer; other non-standard empty Mers will provide unexpected results.
      Parameters:
      `targetMer` - the other Mer

      Returns:
      the distance between the two Mers

    <!-- -->

    - #### distance

          public final double distance(Mer targetMer)

      Return the Euclidean distance from this mer to targetMer. Mers which touch are distance zero. An empty Mer as created by `Mer(int)` is infinite distance from any other Mer; other non-standard empty Mers will provide unexpected results.
      Parameters:
      `targetMer` - the other mer

      Returns:
      the distance between the two Mers

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Object`

    <!-- -->

    - #### getMer

          public Mer getMer()

      Description copied from interface: [`RNode`](RNode.md)
      Returns the bounding box of this spatial object.
      Specified by:
      [`getMer`](RNode.md) in interface [`RNode`](RNode.md)

      Returns:
      a Mer that contains this object, preferably the minimal Mer. The caller must not modify the returned Mer.

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

- [Prev Class](LRSGeometryG3D.md)
- [Next Class](Ops.md)

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
