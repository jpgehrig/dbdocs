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

- [Prev Class](Dijkstra.md)
- [Next Class](DummyLinkCostCalculator.md)

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

## Class DummyCostFunction

- java.lang.Object

- - oracle.spatial.network.lod.DummyCostFunction

<!-- -->

- All Implemented Interfaces:
  [HeuristicCostFunction](HeuristicCostFunction.md)

  ------------------------------------------------------------------------



      public class DummyCostFunction
      extends java.lang.Object
      implements HeuristicCostFunction

  The heuristic cost function implemented in this class always returns 0.
  Since:
  Oracle Database 11g Release 2 (11.2)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description         |
    |-------------------------------------|
    | `DummyCostFunction``(double cost)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                                                                                      |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `double`          | `getHeuristicCost``(`[`HeavyPointOnNet`](HeavyPointOnNet.md)` currentPoint, `[`HeavyPointOnNet`](HeavyPointOnNet.md)` goalPoint)`<br>Returns the heuristic cost from the current point to the target point. |
    | `int[]`           | `getUserDataCategories``()`<br>Returns the required user data categories.                                                                                                                                   |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### DummyCostFunction

          public DummyCostFunction(double cost)

  <!-- -->

  - ### Method Detail

    - #### getHeuristicCost

          public double getHeuristicCost(HeavyPointOnNet currentPoint,
                                         HeavyPointOnNet goalPoint)

      Description copied from interface: [`HeuristicCostFunction`](HeuristicCostFunction.md)
      Returns the heuristic cost from the current point to the target point.
      Specified by:
      [`getHeuristicCost`](HeuristicCostFunction.md) in interface [`HeuristicCostFunction`](HeuristicCostFunction.md)

      Parameters:
      `currentPoint` - current point

      `goalPoint` - target point

      Returns:
      estimated cost from current point to target point)

    <!-- -->

    - #### getUserDataCategories

          public int[] getUserDataCategories()

      Description copied from interface: [`HeuristicCostFunction`](HeuristicCostFunction.md)
      Returns the required user data categories.
      Specified by:

      [`getUserDataCategories`](HeuristicCostFunction.md) in interface [`HeuristicCostFunction`](HeuristicCostFunction.md)

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

- [Prev Class](Dijkstra.md)
- [Next Class](DummyLinkCostCalculator.md)

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
