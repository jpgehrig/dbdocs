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

- [Prev Class](TspPath.md)
- [Next Class](TspTimeWindowConstraint.md)

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

## Class TspPathFeature

- java.lang.Object

- - oracle.spatial.network.lod.TspPathFeature

<!-- -->

-

  ------------------------------------------------------------------------



      public class TspPathFeature
      extends java.lang.Object

  A TspPathFeature object contains information about the tsp order and a sequence of path features from the first point until the last point.
  Since:
  release specific (what release of product did this appear in)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                            |
    |------------------------------------------------------------------------------------------------------------------------|
    | `TspPathFeature``(`[`PathFeature`](PathFeature.md)`[] paths, int[] tspOrder)`<br>Constructs a TspPathFeature instance. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                   | Method and Description                                                   |
    |-------------------------------------|--------------------------------------------------------------------------|
    | `double[]`                          | `getCosts``()`<br>Returns the total cost of the TSP tour.                |
    | [`PathFeature`](PathFeature.md)`[]` | `getPaths``()`<br>Returns the individual paths on the TSP tour.          |
    | `int[]`                             | `getTspOrder``()`<br>Returns the index of the features in visited order. |
    | `java.lang.String`                  | `toString``()`                                                           |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### TspPathFeature

          public TspPathFeature(PathFeature[] paths,
                                int[] tspOrder)

      Constructs a TspPathFeature instance.
      Parameters:
      `paths` - paths between two adjacent featurs on the tsp path.

      `tspOrder` - order of the points represented by the index of the points in the original input array to the tsp analysis function.

  <!-- -->

  - ### Method Detail

    - #### getPaths

          public PathFeature[] getPaths()

      Returns the individual paths on the TSP tour.
      Returns:
      logical path

    <!-- -->

    - #### getTspOrder

          public int[] getTspOrder()

      Returns the index of the features in visited order.
      Returns:

    <!-- -->

    - #### getCosts

          public double[] getCosts()

      Returns the total cost of the TSP tour.
      Returns:

    <!-- -->

    - #### toString

          public java.lang.String toString()

      Overrides:
      `toString` in class `java.lang.Object`

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

- [Prev Class](TspPath.md)
- [Next Class](TspTimeWindowConstraint.md)

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
