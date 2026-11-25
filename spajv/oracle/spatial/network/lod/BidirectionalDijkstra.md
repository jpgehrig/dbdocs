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

- [Prev Class](BidirectionalBfs.md)
- [Next Class](BinaryHeap.md)

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

## Class BidirectionalDijkstra

- java.lang.Object

- - [oracle.spatial.network.lod.BidirectionalBfs](BidirectionalBfs.md)

  - - oracle.spatial.network.lod.BidirectionalDijkstra

<!-- -->

- All Implemented Interfaces:
  [ShortestPath](ShortestPath.md)

  ------------------------------------------------------------------------



      public class BidirectionalDijkstra
      extends BidirectionalBfs
      implements ShortestPath

  Since:
  release specific (what release of product did this appear in)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                               |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `BidirectionalDijkstra``(`[`Dijkstra`](Dijkstra.md)` forwardSearch, `[`Dijkstra`](Dijkstra.md)` backwardSearch)`                                                                                                                                                                                                                          |
    | `BidirectionalDijkstra``(`[`NetworkExplorer`](NetworkExplorer.md)` ne, `[`LinkCostCalculator`](LinkCostCalculator.md)`[] lccs, `[`NodeCostCalculator`](NodeCostCalculator.md)`[] nccs, `[`LinkLevelSelector`](LinkLevelSelector.md)` forwardLinkLevelSelector, `[`LinkLevelSelector`](LinkLevelSelector.md)` backwardLinkLevelSelector)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                 | Method and Description |
    |-----------------------------------|------------------------|
    | [`ShortestPath`](ShortestPath.md) | `clone``()`            |

    - ### Methods inherited from class oracle.spatial.network.lod.[BidirectionalBfs](BidirectionalBfs.md)

      [`getLinkCostCalculators`](BidirectionalBfs.md)`, `[`getLinkLevelSelector`](BidirectionalBfs.md)`, `[`getNodeCostCalculators`](BidirectionalBfs.md)`, `[`setInitialAnalysisInfo`](BidirectionalBfs.md)`, `[`setLinkCostCalculators`](BidirectionalBfs.md)`, `[`setLinkLevelSelector`](BidirectionalBfs.md)`, `[`setNetworkAnalyst`](BidirectionalBfs.md)`, `[`setNodeCostCalculators`](BidirectionalBfs.md)`, `[`shortestPath`](BidirectionalBfs.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.lod.[ShortestPath](ShortestPath.md)

      [`getLinkCostCalculators`](ShortestPath.md)`, `[`getLinkLevelSelector`](ShortestPath.md)`, `[`getNodeCostCalculators`](ShortestPath.md)`, `[`setInitialAnalysisInfo`](ShortestPath.md)`, `[`setLinkCostCalculators`](ShortestPath.md)`, `[`setLinkLevelSelector`](ShortestPath.md)`, `[`setNetworkAnalyst`](ShortestPath.md)`, `[`setNodeCostCalculators`](ShortestPath.md)`, `[`shortestPath`](ShortestPath.md)

<!-- -->

- - ### Constructor Detail

    - #### BidirectionalDijkstra

          public BidirectionalDijkstra(NetworkExplorer ne,
                                       LinkCostCalculator[] lccs,
                                       NodeCostCalculator[] nccs,
                                       LinkLevelSelector forwardLinkLevelSelector,
                                       LinkLevelSelector backwardLinkLevelSelector)

    <!-- -->

    - #### BidirectionalDijkstra

          public BidirectionalDijkstra(Dijkstra forwardSearch,
                                       Dijkstra backwardSearch)

  <!-- -->

  - ### Method Detail

    - #### clone

          public ShortestPath clone()

      Specified by:
      [`clone`](ShortestPath.md) in interface [`ShortestPath`](ShortestPath.md)

      Overrides:
      [`clone`](BidirectionalBfs.md) in class [`BidirectionalBfs`](BidirectionalBfs.md)

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

- [Prev Class](BidirectionalBfs.md)
- [Next Class](BinaryHeap.md)

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
