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

- [Prev Class](DefaultLinkCostCalculator.md)
- [Next Class](DefaultPairwiseCostCalculator.md)

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

## Class DefaultNodeCostCalculator

- java.lang.Object

- - oracle.spatial.network.lod.DefaultNodeCostCalculator

<!-- -->

- All Implemented Interfaces:
  [NodeCostCalculator](NodeCostCalculator.md)

  ------------------------------------------------------------------------



      public class DefaultNodeCostCalculator
      extends java.lang.Object
      implements NodeCostCalculator

  This is the default node cost calculator implementation. It uses the cost attribute of the node as the node cost. This class is implemented as a singleton. To get the singleton instance use
          NodeCostCalculator lcc = DefaultNodeCostCalculator.getNodeCostCalculator();


  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                 |
    |-------------------------------------------------------------|
    | `DefaultNodeCostCalculator``()`                             |
    | `DefaultNodeCostCalculator``(boolean ignoreStartNodeCost)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                      | Method and Description                                                                                                                 |
    |--------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------|
    | `double`                                               | `getNodeCost``(`[`LODAnalysisInfo`](LODAnalysisInfo.md)` analysisInfo)`<br>Computes the cost of the current node in the analysis info. |
    | `static `[`NodeCostCalculator`](NodeCostCalculator.md) | `getNodeCostCalculator``()`                                                                                                            |
    | `int[]`                                                | `getUserDataCategories``()`<br>Returns the required user data categories.                                                              |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### DefaultNodeCostCalculator

          public DefaultNodeCostCalculator()

    <!-- -->

    - #### DefaultNodeCostCalculator

          public DefaultNodeCostCalculator(boolean ignoreStartNodeCost)

  <!-- -->

  - ### Method Detail

    - #### getNodeCostCalculator

          public static NodeCostCalculator getNodeCostCalculator()

    <!-- -->

    - #### getNodeCost

          public double getNodeCost(LODAnalysisInfo analysisInfo)

      Description copied from interface: [`NodeCostCalculator`](NodeCostCalculator.md)
      Computes the cost of the current node in the analysis info.
      Specified by:
      [`getNodeCost`](NodeCostCalculator.md) in interface [`NodeCostCalculator`](NodeCostCalculator.md)

      Parameters:
      `analysisInfo` - analysis info

      Returns:
      node cost

    <!-- -->

    - #### getUserDataCategories

          public int[] getUserDataCategories()

      Description copied from interface: [`NodeCostCalculator`](NodeCostCalculator.md)
      Returns the required user data categories.
      Specified by:

      [`getUserDataCategories`](NodeCostCalculator.md) in interface [`NodeCostCalculator`](NodeCostCalculator.md)

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

- [Prev Class](DefaultLinkCostCalculator.md)
- [Next Class](DefaultPairwiseCostCalculator.md)

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
