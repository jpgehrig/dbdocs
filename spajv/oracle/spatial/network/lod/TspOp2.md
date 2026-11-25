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

- [Prev Class](TspNearestNeighbor.md)
- [Next Class](TspOptimizer.md)

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

## Class TspOp2

- java.lang.Object

- - [oracle.spatial.network.lod.TspImpl](TspImpl.md)

  - - oracle.spatial.network.lod.TspOp2

<!-- -->

- All Implemented Interfaces:
  [TSP](TSP.md), [XMLConfigurable](XMLConfigurable.md)

  ------------------------------------------------------------------------



      public class TspOp2
      extends TspImpl
      implements TSP, XMLConfigurable

  This class implements the 2-opt heuristic algorithm for the Traveling-Salesman-Problem.
  Since:
  Oracle Database 11g Release 2 (11.2)

<!-- -->

- - ### Nested Class Summary

    - ### Nested classes/interfaces inherited from class oracle.spatial.network.lod.[TspImpl](TspImpl.md)

      [`TspImpl.NetworkTspConstraint`](TspImpl.NetworkTspConstraint.md)

    <!-- -->

    - ### Nested classes/interfaces inherited from interface oracle.spatial.network.lod.[TSP](TSP.md)

      [`TSP.TourFlag`](TSP.TourFlag.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `TspOp2``()`<br>Default constructor.                                                                                                                                                                                                                       |
    | `TspOp2``(`[`LinkCostCalculator`](LinkCostCalculator.md)`[] lccs, `[`NodeCostCalculator`](NodeCostCalculator.md)`[] nccs, `[`ShortestPath`](ShortestPath.md)` spAlgorithm, `[`PairwiseCostCalculator`](PairwiseCostCalculator.md)` pwcc)`<br>Deprecated.   |
    | `TspOp2``(`[`PairwiseCostCalculator`](PairwiseCostCalculator.md)` pwcc, `[`ShortestPath`](ShortestPath.md)` spAlgorithm)`                                                                                                                                  |
    | `TspOp2``(`[`PairwiseCostCalculator`](PairwiseCostCalculator.md)` pwcc, `[`ShortestPath`](ShortestPath.md)` spAlgorithm, int direction, double tolerance)`                                                                                                 |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                       |
    |--------------------|--------------------------------------------------------------------------------------------------------------|
    | `java.lang.String` | `getXMLSchema``()`<br>Returns the XML schema for the input parameter.                                        |
    | `void`             | `init``(org.w3c.dom.Element parameter)`<br>Initializes the XML configurable object with the input parameter. |

    - ### Methods inherited from class oracle.spatial.network.lod.[TspImpl](TspImpl.md)

      [`getDirection`](TspImpl.md)`, `[`getNetworkAnalyst`](TspImpl.md)`, `[`getPairwiseCostCalculator`](TspImpl.md)`, `[`getShortestPathAlgorithm`](TspImpl.md)`, `[`getTspOptimizer`](TspImpl.md)`, `[`setDirection`](TspImpl.md)`, `[`setNetworkAnalyst`](TspImpl.md)`, `[`setPairwiseCostCalculator`](TspImpl.md)`, `[`setShortestPathAlgorithm`](TspImpl.md)`, `[`setTspOptimizer`](TspImpl.md)`, `[`tspPath`](TspImpl.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.spatial.network.lod.[TSP](TSP.md)

      [`setNetworkAnalyst`](TSP.md)`, `[`tspPath`](TSP.md)

<!-- -->

- - ### Constructor Detail

    - #### TspOp2

          public TspOp2()

      Default constructor. After this object is created using this default constructor, method init(Element) should be called to initialize it.

    <!-- -->

    - #### TspOp2

          public TspOp2(LinkCostCalculator[] lccs,
                        NodeCostCalculator[] nccs,
                        ShortestPath spAlgorithm,
                        PairwiseCostCalculator pwcc)

      Deprecated. 
      Parameters:
      `lccs` -

      `nccs` -

      `spAlgorithm` -

      `pwcc` -

    <!-- -->

    - #### TspOp2

          public TspOp2(PairwiseCostCalculator pwcc,
                        ShortestPath spAlgorithm)

    <!-- -->

    - #### TspOp2

          public TspOp2(PairwiseCostCalculator pwcc,
                        ShortestPath spAlgorithm,
                        int direction,
                        double tolerance)

  <!-- -->

  - ### Method Detail

    - #### init

          public void init(org.w3c.dom.Element parameter)

      Description copied from interface: [`XMLConfigurable`](XMLConfigurable.md)
      Initializes the XML configurable object with the input parameter.
      Specified by:
      [`init`](XMLConfigurable.md) in interface [`XMLConfigurable`](XMLConfigurable.md)

      Parameters:
      `parameter` - an XML element containing the necessary information to initialize the object.

    <!-- -->

    - #### getXMLSchema

          public java.lang.String getXMLSchema()

      Description copied from interface: [`XMLConfigurable`](XMLConfigurable.md)
      Returns the XML schema for the input parameter.
      Specified by:

      [`getXMLSchema`](XMLConfigurable.md) in interface [`XMLConfigurable`](XMLConfigurable.md)

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

- [Prev Class](TspNearestNeighbor.md)
- [Next Class](TspOptimizer.md)

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
