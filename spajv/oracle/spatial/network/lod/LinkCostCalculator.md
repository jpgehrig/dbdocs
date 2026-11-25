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

- [Prev Class](LeveledNetworkCache.md)
- [Next Class](LinkLevelSelector.md)

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

## Interface LinkCostCalculator

- All Known Implementing Classes:
  [DefaultLinkCostCalculator](DefaultLinkCostCalculator.md), [DummyLinkCostCalculator](DummyLinkCostCalculator.md)

  ------------------------------------------------------------------------



      public interface LinkCostCalculator

  This interface defines methods supported by a link cost calculator.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                              |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------|
    | `double`          | `getLinkCost``(`[`LODAnalysisInfo`](LODAnalysisInfo.md)` analysisInfo)`<br>Computes the cost of the next link in the analysis info. |
    | `int[]`           | `getUserDataCategories``()`<br>Returns the required user data categories.                                                           |

<!-- -->

- - ### Method Detail

    - #### getLinkCost

          double getLinkCost(LODAnalysisInfo analysisInfo)

      Computes the cost of the next link in the analysis info.
      Parameters:
      `analysisInfo` - analysis info

      Returns:
      link cost

    <!-- -->

    - #### getUserDataCategories

          int[] getUserDataCategories()

      Returns the required user data categories.
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

- [Prev Class](LeveledNetworkCache.md)
- [Next Class](LinkLevelSelector.md)

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
