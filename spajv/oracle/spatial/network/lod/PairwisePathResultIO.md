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

- [Prev Class](PairwiseCostCalculator.md)
- [Next Class](PairwiseShortestPaths.md)

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

## Interface PairwisePathResultIO

- All Known Implementing Classes:
  [FilePairwisePathResultIO](FilePairwisePathResultIO.md), [InMemoryPairwisePathResultIO](InMemoryPairwisePathResultIO.md)

  ------------------------------------------------------------------------



      public interface PairwisePathResultIO

  Since:
  release specific (what release of product did this appear in)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                 |
    |-------------------|----------------------------------------------------------------------------------------|
    | `double`          | `readSubPathCost``(int startPointIndex, int endPointIndex)`                            |
    | `void`            | `resetPairwisePathResultIO``()`                                                        |
    | `void`            | `writeSubPathCosts``(int[] startPointIndexes, int[] endPointIndexes, double[] costs)`  |

<!-- -->

- - ### Method Detail

    - #### resetPairwisePathResultIO

          void resetPairwisePathResultIO()
                                  throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### writeSubPathCosts

          void writeSubPathCosts(int[] startPointIndexes,
                                 int[] endPointIndexes,
                                 double[] costs)
                          throws LODNetworkException

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSubPathCost

          double readSubPathCost(int startPointIndex,
                                 int endPointIndex)
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

- [Prev Class](PairwiseCostCalculator.md)
- [Next Class](PairwiseShortestPaths.md)

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
