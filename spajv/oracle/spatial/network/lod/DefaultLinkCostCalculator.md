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

- [Prev Class](ConstraintOperator.md)
- [Next Class](DefaultNodeCostCalculator.md)

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

## Class DefaultLinkCostCalculator

- java.lang.Object

- - oracle.spatial.network.lod.DefaultLinkCostCalculator

<!-- -->

- All Implemented Interfaces:
  [LinkCostCalculator](LinkCostCalculator.md)

  ------------------------------------------------------------------------



      public class DefaultLinkCostCalculator
      extends java.lang.Object
      implements LinkCostCalculator

  This is the default link cost calculator implementation. It uses the cost attribute of the link as the link cost. This class is implemented as a singleton. To get the singleton instance use
          LinkCostCalculator lcc = DefaultLinkCostCalculator.getLinkCostCalculator();


  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description      |
    |----------------------------------|
    | `DefaultLinkCostCalculator``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                      | Method and Description                                                                                                              |
    |--------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------|
    | `double`                                               | `getLinkCost``(`[`LODAnalysisInfo`](LODAnalysisInfo.md)` analysisInfo)`<br>Computes the cost of the next link in the analysis info. |
    | `static `[`LinkCostCalculator`](LinkCostCalculator.md) | `getLinkCostCalculator``()`                                                                                                         |
    | `int[]`                                                | `getUserDataCategories``()`<br>Returns the required user data categories.                                                           |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### DefaultLinkCostCalculator

          public DefaultLinkCostCalculator()

  <!-- -->

  - ### Method Detail

    - #### getLinkCostCalculator

          public static LinkCostCalculator getLinkCostCalculator()

    <!-- -->

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

- [Prev Class](ConstraintOperator.md)
- [Next Class](DefaultNodeCostCalculator.md)

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
