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

- [Prev Class](TspOrderConstraint.md)
- [Next Class](TspPathFeature.md)

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

## Class TspPath

- java.lang.Object

- - oracle.spatial.network.lod.TspPath

<!-- -->

-

  ------------------------------------------------------------------------



      public class TspPath
      extends java.lang.Object

  A TspPath consists of an array of LogicalSubPath and the order of the points on the TSP tour.
  Since:
  Oracle Database 11g Release 2 (11.2)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                    |
    |----------------------------------------------------------------------------------------------------------------|
    | `TspPath``(`[`LogicalSubPath`](LogicalSubPath.md)`[] paths, int[] tspOrder)`<br>Constructs a TspPath instance. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                         | Method and Description                                                 |
    |-------------------------------------------|------------------------------------------------------------------------|
    | `double[]`                                | `getCosts``()`<br>Returns the total cost of the TSP tour.              |
    | [`LogicalSubPath`](LogicalSubPath.md)`[]` | `getPaths``()`<br>Returns the logical sub-path for the TSP tour.       |
    | `int[]`                                   | `getTspOrder``()`<br>Returns the index of the points in visited order. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### TspPath

          public TspPath(LogicalSubPath[] paths,
                         int[] tspOrder)

      Constructs a TspPath instance.
      Parameters:
      `paths` - paths between two consecutive points on the tsp path.

      `tspOrder` - order of the points represented by the index of the points in the original input array to the tsp analysis function.

  <!-- -->

  - ### Method Detail

    - #### getPaths

          public LogicalSubPath[] getPaths()

      Returns the logical sub-path for the TSP tour.
      Returns:
      logical path

    <!-- -->

    - #### getTspOrder

          public int[] getTspOrder()

      Returns the index of the points in visited order.
      Returns:

    <!-- -->

    - #### getCosts

          public double[] getCosts()

      Returns the total cost of the TSP tour.
      Returns:

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

- [Prev Class](TspOrderConstraint.md)
- [Next Class](TspPathFeature.md)

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
