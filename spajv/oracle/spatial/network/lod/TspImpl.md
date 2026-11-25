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

- [Prev Class](TspConstraintOperator.CombinedConstraint.md)
- [Next Class](TspImpl.NetworkTspConstraint.md)

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

## Class TspImpl

- java.lang.Object

- - oracle.spatial.network.lod.TspImpl

<!-- -->

- All Implemented Interfaces:
  [TSP](TSP.md)

  <!-- -->

  Direct Known Subclasses:
  [TspOp2](TspOp2.md)

  ------------------------------------------------------------------------



      public class TspImpl
      extends java.lang.Object
      implements TSP

  The default two step TSP implementation, which first computes the pairwise costs between the TSP stops, and then optimizes the order the stops to be visited.
  Since:
  12.2

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Class and Description                                              |
    |-------------------|--------------------------------------------------------------------|
    | `static class `   | [`TspImpl.NetworkTspConstraint`](TspImpl.NetworkTspConstraint.md)  |

    - ### Nested classes/interfaces inherited from interface oracle.spatial.network.lod.[TSP](TSP.md)

      [`TSP.TourFlag`](TSP.TourFlag.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                               |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `TspImpl``()`                                                                                                                                                                             |
    | `TspImpl``(`[`PairwiseCostCalculator`](PairwiseCostCalculator.md)` pwcc, `[`TspOptimizer`](TspOptimizer.md)` optimizer, `[`ShortestPath`](ShortestPath.md)` spAlgorithm, int direction)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                     | Method and Description                                                                                                                                                                                                                                                                                                                  |
    |-------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`                                                 | `getDirection``()`                                                                                                                                                                                                                                                                                                                      |
    | [`NetworkAnalyst`](NetworkAnalyst.md)                 | `getNetworkAnalyst``()`                                                                                                                                                                                                                                                                                                                 |
    | [`PairwiseCostCalculator`](PairwiseCostCalculator.md) | `getPairwiseCostCalculator``()`                                                                                                                                                                                                                                                                                                         |
    | [`ShortestPath`](ShortestPath.md)                     | `getShortestPathAlgorithm``()`                                                                                                                                                                                                                                                                                                          |
    | [`TspOptimizer`](TspOptimizer.md)                     | `getTspOptimizer``()`                                                                                                                                                                                                                                                                                                                   |
    | `void`                                                | `setDirection``(int direction)`                                                                                                                                                                                                                                                                                                         |
    | `void`                                                | `setNetworkAnalyst``(`[`NetworkAnalyst`](NetworkAnalyst.md)` analyst)`<br>This method allows caller to pass the network analyst object to this TSP algorithm implementation, so that the algorithm can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst. |
    | `void`                                                | `setPairwiseCostCalculator``(`[`PairwiseCostCalculator`](PairwiseCostCalculator.md)` pwcc)`                                                                                                                                                                                                                                             |
    | `void`                                                | `setShortestPathAlgorithm``(`[`ShortestPath`](ShortestPath.md)` spAlgorithm)`                                                                                                                                                                                                                                                           |
    | `void`                                                | `setTspOptimizer``(`[`TspOptimizer`](TspOptimizer.md)` optimizer)`                                                                                                                                                                                                                                                                      |
    | [`TspPath`](TspPath.md)                               | `tspPath``(`[`PointOnNet`](PointOnNet.md)`[][] points, `[`TSP.TourFlag`](TSP.TourFlag.md)` tourFlag, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` networkConstraint, `[`TspConstraint`](TspConstraint.md)` tspConstraint)`<br>Returns the traveling salesman tour with the optimal or suboptimal cost.                           |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### TspImpl

          public TspImpl()

    <!-- -->

    - #### TspImpl

          public TspImpl(PairwiseCostCalculator pwcc,
                         TspOptimizer optimizer,
                         ShortestPath spAlgorithm,
                         int direction)

  <!-- -->

  - ### Method Detail

    - #### setDirection

          public void setDirection(int direction)

    <!-- -->

    - #### getDirection

          public int getDirection()

    <!-- -->

    - #### setPairwiseCostCalculator

          public void setPairwiseCostCalculator(PairwiseCostCalculator pwcc)

    <!-- -->

    - #### getPairwiseCostCalculator

          public PairwiseCostCalculator getPairwiseCostCalculator()

    <!-- -->

    - #### setTspOptimizer

          public void setTspOptimizer(TspOptimizer optimizer)

    <!-- -->

    - #### getTspOptimizer

          public TspOptimizer getTspOptimizer()

    <!-- -->

    - #### setShortestPathAlgorithm

          public void setShortestPathAlgorithm(ShortestPath spAlgorithm)

    <!-- -->

    - #### getShortestPathAlgorithm

          public ShortestPath getShortestPathAlgorithm()

    <!-- -->

    - #### setNetworkAnalyst

          public void setNetworkAnalyst(NetworkAnalyst analyst)

      Description copied from interface: [`TSP`](TSP.md)
      This method allows caller to pass the network analyst object to this TSP algorithm implementation, so that the algorithm can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst. If network analyst is not needed by the shortest path algorithm, the algorithm can choose to do nothing with this method.
      Specified by:
      [`setNetworkAnalyst`](TSP.md) in interface [`TSP`](TSP.md)

    <!-- -->

    - #### getNetworkAnalyst

          public NetworkAnalyst getNetworkAnalyst()

    <!-- -->

    - #### tspPath

          public TspPath tspPath(PointOnNet[][] points,
                                 TSP.TourFlag tourFlag,
                                 LODNetworkConstraint networkConstraint,
                                 TspConstraint tspConstraint)
                          throws LODNetworkException

      Description copied from interface: [`TSP`](TSP.md)
      Returns the traveling salesman tour with the optimal or suboptimal cost.
      Specified by:
      [`tspPath`](TSP.md) in interface [`TSP`](TSP.md)

      Parameters:
      `points` - points to visit on the TSP tour.

      `tourFlag` - a flag indicating whether the tour should be open or closed, and if the tour is open, whether the tour should have fixed start or end point.

      `networkConstraint` - network constraint

      `tspConstraint` - tsp constraint

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

- [Prev Class](TspConstraintOperator.CombinedConstraint.md)
- [Next Class](TspImpl.NetworkTspConstraint.md)

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
