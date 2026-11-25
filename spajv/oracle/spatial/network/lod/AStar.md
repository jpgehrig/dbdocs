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

- [Prev Class](AnalysisEngine.DefaultCallable.md)
- [Next Class](BidirectionalBfs.md)

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

## Class AStar

- java.lang.Object

- - [oracle.spatial.network.lod.NetworkSearch](NetworkSearch.md)

  - - [oracle.spatial.network.lod.BreadthFirstSearch](BreadthFirstSearch.md)

    - - oracle.spatial.network.lod.AStar

<!-- -->

- All Implemented Interfaces:
  [ShortestPath](ShortestPath.md), [XMLConfigurable](XMLConfigurable.md)

  ------------------------------------------------------------------------



      public class AStar
      extends BreadthFirstSearch
      implements ShortestPath, XMLConfigurable

  This class implements A\* shortest path algorithm.
  Since:
  Oracle Database 11g Release 2 (11.2)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                          |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `AStar``()`<br>Default constructor.                                                                                                                                                                                                                                                                  |
    | `AStar``(`[`NetworkExplorer`](NetworkExplorer.md)` ne, `[`LinkCostCalculator`](LinkCostCalculator.md)`[] lccs, `[`NodeCostCalculator`](NodeCostCalculator.md)`[] nccs, `[`HeuristicCostFunction`](HeuristicCostFunction.md)` astarCostFunction, `[`LinkLevelSelector`](LinkLevelSelector.md)` lls)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                       |
    |--------------------|--------------------------------------------------------------------------------------------------------------|
    | `AStar`            | `clone``()`                                                                                                  |
    | `java.lang.String` | `getXMLSchema``()`<br>Returns the XML schema for the input parameter.                                        |
    | `void`             | `init``(org.w3c.dom.Element parameter)`<br>Initializes the XML configurable object with the input parameter. |

    - ### Methods inherited from class oracle.spatial.network.lod.[BreadthFirstSearch](BreadthFirstSearch.md)

      [`nearestFeatures`](BreadthFirstSearch.md)`, `[`nearestNeighbors`](BreadthFirstSearch.md)`, `[`nearestPoints`](BreadthFirstSearch.md)`, `[`networkBuffer`](BreadthFirstSearch.md)`, `[`shortestPath`](BreadthFirstSearch.md)`, `[`shortestPaths`](BreadthFirstSearch.md)`, `[`shortestPathsLight`](BreadthFirstSearch.md)`, `[`traceOut`](BreadthFirstSearch.md)`, `[`withinCost`](BreadthFirstSearch.md)`, `[`withinCostFeatures`](BreadthFirstSearch.md)`, `[`withinCostPoints`](BreadthFirstSearch.md)

    <!-- -->

    - ### Methods inherited from class oracle.spatial.network.lod.[NetworkSearch](NetworkSearch.md)

      [`findConnectedFeatures`](NetworkSearch.md)`, `[`getLinkCostCalculators`](NetworkSearch.md)`, `[`getLinkLevelSelector`](NetworkSearch.md)`, `[`getNodeCostCalculators`](NetworkSearch.md)`, `[`initSearch`](NetworkSearch.md)`, `[`preparePathFeature`](NetworkSearch.md)`, `[`reset`](NetworkSearch.md)`, `[`setInitialAnalysisInfo`](NetworkSearch.md)`, `[`setLinkCostCalculators`](NetworkSearch.md)`, `[`setLinkLevelSelector`](NetworkSearch.md)`, `[`setNetworkAnalyst`](NetworkSearch.md)`, `[`setNetworkExplorer`](NetworkSearch.md)`, `[`setNodeCostCalculators`](NetworkSearch.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.lod.[ShortestPath](ShortestPath.md)

      [`getLinkCostCalculators`](ShortestPath.md)`, `[`getLinkLevelSelector`](ShortestPath.md)`, `[`getNodeCostCalculators`](ShortestPath.md)`, `[`setInitialAnalysisInfo`](ShortestPath.md)`, `[`setLinkCostCalculators`](ShortestPath.md)`, `[`setLinkLevelSelector`](ShortestPath.md)`, `[`setNetworkAnalyst`](ShortestPath.md)`, `[`setNodeCostCalculators`](ShortestPath.md)`, `[`shortestPath`](ShortestPath.md)

<!-- -->

- - ### Constructor Detail

    - #### AStar

          public AStar()

      Default constructor. After this object is created using this default constructor, method init(Element) should be called to initialize it.

    <!-- -->

    - #### AStar

          public AStar(NetworkExplorer ne,
                       LinkCostCalculator[] lccs,
                       NodeCostCalculator[] nccs,
                       HeuristicCostFunction astarCostFunction,
                       LinkLevelSelector lls)

  <!-- -->

  - ### Method Detail

    - #### clone

          public AStar clone()

      Specified by:
      [`clone`](ShortestPath.md) in interface [`ShortestPath`](ShortestPath.md)

      Overrides:
      [`clone`](BreadthFirstSearch.md) in class [`BreadthFirstSearch`](BreadthFirstSearch.md)

    <!-- -->

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

    - #### getXMLSchema

          public java.lang.String getXMLSchema()

      Description copied from interface: [`XMLConfigurable`](XMLConfigurable.md)
      Returns the XML schema for the input parameter.
      Specified by:

      [`getXMLSchema`](XMLConfigurable.md) in interface [`XMLConfigurable`](XMLConfigurable.md)

      Overrides:

      [`getXMLSchema`](NetworkSearch.md) in class [`NetworkSearch`](NetworkSearch.md)

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

- [Prev Class](AnalysisEngine.DefaultCallable.md)
- [Next Class](BidirectionalBfs.md)

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
