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

- [Prev Class](FeaturePath.md)
- [Next Class](GeodeticCostFunction.md)

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

## Class FilePairwisePathResultIO

- java.lang.Object

- - oracle.spatial.network.lod.FilePairwisePathResultIO

<!-- -->

- All Implemented Interfaces:
  [PairwisePathResultIO](PairwisePathResultIO.md)

  ------------------------------------------------------------------------



      public class FilePairwisePathResultIO
      extends java.lang.Object
      implements PairwisePathResultIO

  Since:
  release specific (what release of product did this appear in)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                |
    |----------------------------------------------------------------------------|
    | `FilePairwisePathResultIO``(java.lang.String fileName, int numEndPoints)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                 |
    |-------------------|----------------------------------------------------------------------------------------|
    | `void`            | `closePairwisePathResultIO``()`                                                        |
    | `void`            | `openPairwisePathResultIO``()`                                                         |
    | `double`          | `readSubPathCost``(int startPointIndex, int endPointIndex)`                            |
    | `void`            | `resetPairwisePathResultIO``()`                                                        |
    | `void`            | `writeSubPathCosts``(int[] startPointIndexes, int[] endPointIndexes, double[] costs)`  |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### FilePairwisePathResultIO

          public FilePairwisePathResultIO(java.lang.String fileName,
                                          int numEndPoints)

  <!-- -->

  - ### Method Detail

    - #### resetPairwisePathResultIO

          public void resetPairwisePathResultIO()
                                         throws LODNetworkException

      Specified by:
      [`resetPairwisePathResultIO`](PairwisePathResultIO.md) in interface [`PairwisePathResultIO`](PairwisePathResultIO.md)

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### writeSubPathCosts

          public void writeSubPathCosts(int[] startPointIndexes,
                                        int[] endPointIndexes,
                                        double[] costs)
                                 throws LODNetworkException

      Specified by:
      [`writeSubPathCosts`](PairwisePathResultIO.md) in interface [`PairwisePathResultIO`](PairwisePathResultIO.md)

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### readSubPathCost

          public double readSubPathCost(int startPointIndex,
                                        int endPointIndex)
                                 throws LODNetworkException

      Specified by:
      [`readSubPathCost`](PairwisePathResultIO.md) in interface [`PairwisePathResultIO`](PairwisePathResultIO.md)

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### openPairwisePathResultIO

          public void openPairwisePathResultIO()

    <!-- -->

    - #### closePairwisePathResultIO

          public void closePairwisePathResultIO()

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

- [Prev Class](FeaturePath.md)
- [Next Class](GeodeticCostFunction.md)

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
