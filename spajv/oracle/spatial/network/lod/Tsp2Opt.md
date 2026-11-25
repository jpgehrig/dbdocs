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

- [Prev Class](TSP.TourFlag.md)
- [Next Class](TspAnalysisInfo.md)

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

## Class Tsp2Opt

- java.lang.Object

- - oracle.spatial.network.lod.Tsp2Opt

<!-- -->

- All Implemented Interfaces:
  [TspOptimizer](TspOptimizer.md)

  ------------------------------------------------------------------------



      public class Tsp2Opt
      extends java.lang.Object
      implements TspOptimizer

  Since:
  release specific (what release of product did this appear in)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description    |
    |--------------------------------|
    | `Tsp2Opt``(double tolerance)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                                         |
    |-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `double`          | `getTolerance``()`                                                                                                                                             |
    | `int[]`           | `optimize``(`[`Matrix`](Matrix.md)`<double[]> pairwiseCosts, `[`TSP.TourFlag`](TSP.TourFlag.md)` tourFlag, `[`TspConstraint`](TspConstraint.md)` constraint)`  |
    | `void`            | `setTolerance``(double tolerance)`                                                                                                                             |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### Tsp2Opt

          public Tsp2Opt(double tolerance)

  <!-- -->

  - ### Method Detail

    - #### setTolerance

          public void setTolerance(double tolerance)

    <!-- -->

    - #### getTolerance

          public double getTolerance()

    <!-- -->

    - #### optimize

          public int[] optimize(Matrix<double[]> pairwiseCosts,
                                TSP.TourFlag tourFlag,
                                TspConstraint constraint)
                         throws LODNetworkException

      Specified by:
      [`optimize`](TspOptimizer.md) in interface [`TspOptimizer`](TspOptimizer.md)

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

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

- [Prev Class](TSP.TourFlag.md)
- [Next Class](TspAnalysisInfo.md)

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
