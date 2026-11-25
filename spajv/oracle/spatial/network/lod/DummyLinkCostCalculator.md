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

- [Prev Class](DummyCostFunction.md)
- [Next Class](DummyLinkLevelSelector.md)

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

## Class DummyLinkCostCalculator

- java.lang.Object

- - oracle.spatial.network.lod.DummyLinkCostCalculator

<!-- -->

- All Implemented Interfaces:
  [LinkCostCalculator](LinkCostCalculator.md)

  ------------------------------------------------------------------------



      public class DummyLinkCostCalculator
      extends java.lang.Object
      implements LinkCostCalculator

  This implementation of LinkCostCalculator always returns a fixed number as link cost.
  Since:
  Oracle Database 11g Release 2 (11.2)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description               |
    |-------------------------------------------|
    | `DummyLinkCostCalculator``()`             |
    | `DummyLinkCostCalculator``(double cost)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                              |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------|
    | `double`          | `getLinkCost``(`[`LODAnalysisInfo`](LODAnalysisInfo.md)` analysisInfo)`<br>Computes the cost of the next link in the analysis info. |
    | `int[]`           | `getUserDataCategories``()`<br>Returns the required user data categories.                                                           |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### DummyLinkCostCalculator

          public DummyLinkCostCalculator()

    <!-- -->

    - #### DummyLinkCostCalculator

          public DummyLinkCostCalculator(double cost)

  <!-- -->

  - ### Method Detail

    - #### getLinkCost

          public double getLinkCost(LODAnalysisInfo analysisInfo)

      Description copied from interface: [`LinkCostCalculator`](LinkCostCalculator.md)
      Computes the cost of the next link in the analysis info.
      Specified by:
      [`getLinkCost`](LinkCostCalculator.md) in interface [`LinkCostCalculator`](LinkCostCalculator.md)

      Parameters:
      `analysisInfo` - analysis info

      Returns:
      link cost

    <!-- -->

    - #### getUserDataCategories

          public int[] getUserDataCategories()

      Description copied from interface: [`LinkCostCalculator`](LinkCostCalculator.md)
      Returns the required user data categories.
      Specified by:

      [`getUserDataCategories`](LinkCostCalculator.md) in interface [`LinkCostCalculator`](LinkCostCalculator.md)

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

- [Prev Class](DummyCostFunction.md)
- [Next Class](DummyLinkLevelSelector.md)

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
