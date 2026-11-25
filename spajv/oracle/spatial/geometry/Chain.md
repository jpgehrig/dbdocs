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

- [Prev Class](AbstractRTree.PairDebug.md)
- [Next Class](Chain.AccurateSum.md)

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

## Class Chain

- java.lang.Object

- - oracle.spatial.geometry.Chain

<!-- -->

-

  ------------------------------------------------------------------------



      public final class Chain
      extends java.lang.Object

  Provides an efficient double-ended list of vertices, which can be referenced by either end. The following operations are provided:
  1.  Coordinates can be inserted onto either end in O(1) time
  2.  Two chains can be appended into one longer chain.
  3.  The time to build a chain of n vertices is O(n log n) time through any combination of inserting vertices and appending chains.

  The chain also supports storing lists of Chains with a Chain --- this is used to store polygons with holes (the chain itself as the exterior boundary, the list of chains as holes). When chains are merged the corresponding lists will be merged in an arbitrary order. Nothing in this class prevents arbitrary nesting, but current usage in Buffer does not have holes within holes, and any such would symptomatic of a bug in buffer.

  Note that the metadata add and get routines hold onto list objects and return live list objects, and that the routines may return null lists.

  Creation of a chain returns the two endpoints (two separate objects). Each end is indexed with "0" being the coordinate closest to that end (a newly added vertex on an end becomes the new 0th coordinate for that end), and the coordinate on the opposite end being at index (size - 1).

  Since:
  August 2012

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Class and Description                                                                                                               |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------|
    | `static class `   | [`Chain.AccurateSum`](Chain.AccurateSum.md)<br>Accurately accumulate a summation.                                                   |
    | `static class `   | [`Chain.CenterPoint`](Chain.CenterPoint.md)<br>Abusing subclassing --- this is used to store the centers of circular arcs in Chain. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description          |
    |--------------------|---------------------------------|
    | `java.lang.String` | `toString``()`                  |
    | `java.lang.String` | `WKT``()`<br>Debugging only     |
    | `java.lang.String` | `WKTList``()`<br>Debugging only |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### WKT

          public java.lang.String WKT()

      Debugging only
      Returns:
      Chain as a LINESTRING, arcs expanded into linears. Metadata is ignored.

    <!-- -->

    - #### WKTList

          public java.lang.String WKTList()

      Debugging only
      Returns:
      list as a bracket-enclosed list of comma-separated coordinates, arcs expaned into linestring approximations.

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Object`

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

- [Prev Class](AbstractRTree.PairDebug.md)
- [Next Class](Chain.AccurateSum.md)

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
