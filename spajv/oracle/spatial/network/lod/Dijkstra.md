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

- [Prev Class](DefaultSingleSourceShortestPaths.md)
- [Next Class](DummyCostFunction.md)

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

## Class Dijkstra

- java.lang.Object

- - [oracle.spatial.network.lod.NetworkSearch](NetworkSearch.md)

  - - [oracle.spatial.network.lod.BreadthFirstSearch](BreadthFirstSearch.md)

    - - oracle.spatial.network.lod.Dijkstra

<!-- -->

- All Implemented Interfaces:
  [ShortestPath](ShortestPath.md), [SingleSourceShortestPaths](SingleSourceShortestPaths.md), [XMLConfigurable](XMLConfigurable.md)

  ------------------------------------------------------------------------



      public class Dijkstra
      extends BreadthFirstSearch
      implements ShortestPath, SingleSourceShortestPaths, XMLConfigurable

  This class implements Dijkstra shortest path algorithm.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                    |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `Dijkstra``()`<br>Default constructor.                                                                                                                                                                                         |
    | `Dijkstra``(`[`NetworkExplorer`](NetworkExplorer.md)` ne, `[`LinkCostCalculator`](LinkCostCalculator.md)`[] lccs, `[`NodeCostCalculator`](NodeCostCalculator.md)`[] nccs, `[`LinkLevelSelector`](LinkLevelSelector.md)` lls)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                       |
    |-------------------|--------------------------------------------------------------------------------------------------------------|
    | `Dijkstra`        | `clone``()`                                                                                                  |
    | `void`            | `init``(org.w3c.dom.Element parameter)`<br>Initializes the XML configurable object with the input parameter. |

    - ### Methods inherited from class oracle.spatial.network.lod.[BreadthFirstSearch](BreadthFirstSearch.md)

      [`nearestFeatures`](BreadthFirstSearch.md)`, `[`nearestNeighbors`](BreadthFirstSearch.md)`, `[`nearestPoints`](BreadthFirstSearch.md)`, `[`networkBuffer`](BreadthFirstSearch.md)`, `[`shortestPath`](BreadthFirstSearch.md)`, `[`shortestPaths`](BreadthFirstSearch.md)`, `[`shortestPathsLight`](BreadthFirstSearch.md)`, `[`traceOut`](BreadthFirstSearch.md)`, `[`withinCost`](BreadthFirstSearch.md)`, `[`withinCostFeatures`](BreadthFirstSearch.md)`, `[`withinCostPoints`](BreadthFirstSearch.md)

    <!-- -->

    - ### Methods inherited from class oracle.spatial.network.lod.[NetworkSearch](NetworkSearch.md)

      [`findConnectedFeatures`](NetworkSearch.md)`, `[`getLinkCostCalculators`](NetworkSearch.md)`, `[`getLinkLevelSelector`](NetworkSearch.md)`, `[`getNodeCostCalculators`](NetworkSearch.md)`, `[`getXMLSchema`](NetworkSearch.md)`, `[`initSearch`](NetworkSearch.md)`, `[`preparePathFeature`](NetworkSearch.md)`, `[`reset`](NetworkSearch.md)`, `[`setInitialAnalysisInfo`](NetworkSearch.md)`, `[`setLinkCostCalculators`](NetworkSearch.md)`, `[`setLinkLevelSelector`](NetworkSearch.md)`, `[`setNetworkAnalyst`](NetworkSearch.md)`, `[`setNetworkExplorer`](NetworkSearch.md)`, `[`setNodeCostCalculators`](NetworkSearch.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.lod.[ShortestPath](ShortestPath.md)

      [`getLinkCostCalculators`](ShortestPath.md)`, `[`getLinkLevelSelector`](ShortestPath.md)`, `[`getNodeCostCalculators`](ShortestPath.md)`, `[`setInitialAnalysisInfo`](ShortestPath.md)`, `[`setLinkCostCalculators`](ShortestPath.md)`, `[`setLinkLevelSelector`](ShortestPath.md)`, `[`setNetworkAnalyst`](ShortestPath.md)`, `[`setNodeCostCalculators`](ShortestPath.md)`, `[`shortestPath`](ShortestPath.md)

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.lod.[SingleSourceShortestPaths](SingleSourceShortestPaths.md)

      [`setNetworkAnalyst`](SingleSourceShortestPaths.md)`, `[`shortestPaths`](SingleSourceShortestPaths.md)`, `[`shortestPathsLight`](SingleSourceShortestPaths.md)

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.lod.[XMLConfigurable](XMLConfigurable.md)

      [`getXMLSchema`](XMLConfigurable.md)

<!-- -->

- - ### Constructor Detail

    - #### Dijkstra

          public Dijkstra()

      Default constructor. After this object is created using this default constructor, method init(Element) should be called to initialize it.

    <!-- -->

    - #### Dijkstra

          public Dijkstra(NetworkExplorer ne,
                          LinkCostCalculator[] lccs,
                          NodeCostCalculator[] nccs,
                          LinkLevelSelector lls)

  <!-- -->

  - ### Method Detail

    - #### init

          public void init(org.w3c.dom.Element parameter)

      Description copied from interface: [`XMLConfigurable`](XMLConfigurable.md)
      Initializes the XML configurable object with the input parameter.
      Specified by:
      [`init`](XMLConfigurable.md) in interface [`XMLConfigurable`](XMLConfigurable.md)

      Overrides:
      [`init`](NetworkSearch.md) in class [`NetworkSearch`](NetworkSearch.md)

      Parameters:
      `parameter` - an XML element containing the necessary information to initialize the object.

    <!-- -->

    - #### clone

          public Dijkstra clone()

      Specified by:
      [`clone`](ShortestPath.md) in interface [`ShortestPath`](ShortestPath.md)

      Specified by:
      [`clone`](SingleSourceShortestPaths.md) in interface [`SingleSourceShortestPaths`](SingleSourceShortestPaths.md)

      Overrides:
      [`clone`](BreadthFirstSearch.md) in class [`BreadthFirstSearch`](BreadthFirstSearch.md)

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

- [Prev Class](DefaultSingleSourceShortestPaths.md)
- [Next Class](DummyCostFunction.md)

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
