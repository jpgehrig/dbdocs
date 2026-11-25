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

- [Prev Class](HeavyPointOnNet.md)
- [Next Class](Identifiable.md)

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

## Interface HeuristicCostFunction

- All Known Implementing Classes:
  [DummyCostFunction](DummyCostFunction.md), [EuclideanCostFunction](EuclideanCostFunction.md), [GeodeticCostFunction](GeodeticCostFunction.md)

  ------------------------------------------------------------------------



      public interface HeuristicCostFunction

  This interface defines the heuristic cost function from one point to another. This interface is used in A\* search and dynamic link level selector. This package provides two heuristic cost implementations for spatial networks: GeodeticCostFunction and EuclideanCostFunction. Users can provide their own cost estimates to guide the A\* search. In order to guarantee optimality of A\* search result, the heuristic cost from the current point to the target point must be smaller than the minimum cost from the current point to the target point.
  Since:
  Oracle Database 11g Release 2 (11.2)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                                                                                        |
    |-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `double`          | `getHeuristicCost``(`[`HeavyPointOnNet`](HeavyPointOnNet.md)` currentPoint, `[`HeavyPointOnNet`](HeavyPointOnNet.md)` targetPoint)`<br>Returns the heuristic cost from the current point to the target point. |
    | `int[]`           | `getUserDataCategories``()`<br>Returns the required user data categories.                                                                                                                                     |

<!-- -->

- - ### Method Detail

    - #### getHeuristicCost

          double getHeuristicCost(HeavyPointOnNet currentPoint,
                                  HeavyPointOnNet targetPoint)

      Returns the heuristic cost from the current point to the target point.
      Parameters:
      `currentPoint` - current point

      `targetPoint` - target point

      Returns:
      estimated cost from current point to target point)

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

- [Prev Class](HeavyPointOnNet.md)
- [Next Class](Identifiable.md)

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
