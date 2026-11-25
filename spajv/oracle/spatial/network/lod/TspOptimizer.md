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

- [Prev Class](TspOp2.md)
- [Next Class](TspOrderConstraint.md)

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

## Interface TspOptimizer

- All Known Implementing Classes:
  [Tsp2Opt](Tsp2Opt.md)

  ------------------------------------------------------------------------



      public interface TspOptimizer

  Since:
  release specific (what release of product did this appear in)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                                |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int[]`           | `optimize``(`[`Matrix`](Matrix.md)`<double[]> pwcs, `[`TSP.TourFlag`](TSP.TourFlag.md)` tourFlag, `[`TspConstraint`](TspConstraint.md)` constraint)`  |

<!-- -->

- - ### Method Detail

    - #### optimize

          int[] optimize(Matrix<double[]> pwcs,
                         TSP.TourFlag tourFlag,
                         TspConstraint constraint)
                  throws LODNetworkException

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

- [Prev Class](TspOp2.md)
- [Next Class](TspOrderConstraint.md)

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
