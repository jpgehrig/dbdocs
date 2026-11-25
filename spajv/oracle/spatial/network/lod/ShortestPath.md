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

- [Prev Class](PriorityQueue.md)
- [Next Class](SilhouetteClusterEvaluator.md)

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

## Interface ShortestPath

- All Known Implementing Classes:
  [AStar](AStar.md), [BidirectionalBfs](BidirectionalBfs.md), [BidirectionalDijkstra](BidirectionalDijkstra.md), [BreadthFirstSearch](BreadthFirstSearch.md), [Dijkstra](Dijkstra.md), [KShortestPathsBfs](KShortestPathsBfs.md)

  ------------------------------------------------------------------------



      public interface ShortestPath

  This interface defines methods supported by a shortest path algorithm.
  Since:
  Oracle Database 11g Release 2 (11.2)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                 | Method and Description                                                                                                                                                                                                                                                                                                                            |
    |---------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `ShortestPath`                                    | `clone``()`                                                                                                                                                                                                                                                                                                                                       |
    | [`LinkCostCalculator`](LinkCostCalculator.md)`[]` | `getLinkCostCalculators``()`<br>Returns the link cost calculators.                                                                                                                                                                                                                                                                                |
    | [`LinkLevelSelector`](LinkLevelSelector.md)       | `getLinkLevelSelector``()`<br>Returns the link level selector.                                                                                                                                                                                                                                                                                    |
    | [`NodeCostCalculator`](NodeCostCalculator.md)`[]` | `getNodeCostCalculators``()`<br>Returns the node cost calculators.                                                                                                                                                                                                                                                                                |
    | `void`                                            | `setInitialAnalysisInfo``(`[`LODAnalysisInfo`](LODAnalysisInfo.md)` analysisInfo)`<br>Sets the initial analysis info.                                                                                                                                                                                                                             |
    | `void`                                            | `setLinkCostCalculators``(`[`LinkCostCalculator`](LinkCostCalculator.md)`[] lccs)`<br>Sets the link cost calculators.                                                                                                                                                                                                                             |
    | `void`                                            | `setLinkLevelSelector``(`[`LinkLevelSelector`](LinkLevelSelector.md)` lls)`<br>Sets the link level selector.                                                                                                                                                                                                                                      |
    | `void`                                            | `setNetworkAnalyst``(`[`NetworkAnalyst`](NetworkAnalyst.md)` analyst)`<br>This method allows caller to pass the network analyst object to this shortest path algorithm implementation, so that the algorithm can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst. |
    | `void`                                            | `setNodeCostCalculators``(`[`NodeCostCalculator`](NodeCostCalculator.md)`[] nccs)`<br>Sets the node cost calculators.                                                                                                                                                                                                                             |
    | [`LogicalSubPath`](LogicalSubPath.md)             | `shortestPath``(`[`PointOnNet`](PointOnNet.md)`[] startPoints, `[`PointOnNet`](PointOnNet.md)`[] endPoints, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, int direction)`<br>Returns the shortest path between a set of candidate start points and a set of end points.                                                         |

<!-- -->

- - ### Method Detail

    - #### setInitialAnalysisInfo

          void setInitialAnalysisInfo(LODAnalysisInfo analysisInfo)

      Sets the initial analysis info. This method allows analysis info to be passed to subsequent analysis.
      Parameters:
      `analysisInfo` - analysis information

    <!-- -->

    - #### shortestPath

          LogicalSubPath shortestPath(PointOnNet[] startPoints,
                                      PointOnNet[] endPoints,
                                      LODNetworkConstraint constraint,
                                      int direction)
                               throws LODNetworkException

      Returns the shortest path between a set of candidate start points and a set of end points.
      Parameters:
      `startPoints` - start candidates

      `endPoints` - end candidates

      `constraint` - network constraint

      `direction` - NetworkExplorer.DIRECTION_FORWARD or NetworkExplorer.DIRECTION_BACKWARD

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### getLinkLevelSelector

          LinkLevelSelector getLinkLevelSelector()

      Returns the link level selector.
      Returns:

    <!-- -->

    - #### setLinkLevelSelector

          void setLinkLevelSelector(LinkLevelSelector lls)

      Sets the link level selector.
      Parameters:
      `lls` - link level selector

    <!-- -->

    - #### getLinkCostCalculators

          LinkCostCalculator[] getLinkCostCalculators()

      Returns the link cost calculators.
      Returns:

    <!-- -->

    - #### setLinkCostCalculators

          void setLinkCostCalculators(LinkCostCalculator[] lccs)

      Sets the link cost calculators.
      Parameters:
      `lccs` -

    <!-- -->

    - #### getNodeCostCalculators

          NodeCostCalculator[] getNodeCostCalculators()

      Returns the node cost calculators.
      Returns:

    <!-- -->

    - #### setNodeCostCalculators

          void setNodeCostCalculators(NodeCostCalculator[] nccs)

      Sets the node cost calculators.
      Parameters:
      `nccs` -

    <!-- -->

    - #### setNetworkAnalyst

          void setNetworkAnalyst(NetworkAnalyst analyst)

      This method allows caller to pass the network analyst object to this shortest path algorithm implementation, so that the algorithm can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst. If network analyst is not needed by the shortest path algorithm, the algorithm can choose to do nothing with this method.

    <!-- -->

    - #### clone

          ShortestPath clone()

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

- [Prev Class](PriorityQueue.md)
- [Next Class](SilhouetteClusterEvaluator.md)

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
