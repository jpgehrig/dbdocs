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

- [Prev Class](DefaultNodeCostCalculator.md)
- [Next Class](DefaultPairwiseShortestPaths.md)

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

## Class DefaultPairwiseCostCalculator

- java.lang.Object

- - oracle.spatial.network.lod.DefaultPairwiseCostCalculator

<!-- -->

- All Implemented Interfaces:
  [PairwiseCostCalculator](PairwiseCostCalculator.md), [XMLConfigurable](XMLConfigurable.md)

  ------------------------------------------------------------------------



      public class DefaultPairwiseCostCalculator
      extends java.lang.Object
      implements PairwiseCostCalculator, XMLConfigurable

  This is the default pairwise cost calculator. It calculates the pairwise costs using the input pairwise shortest path algorithm.
  Since:
  Oracle Database 11g Release 2 (11.2)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                     |
    |-------------------------------------------------------------------------------------------------------------------------------------------------|
    | `DefaultPairwiseCostCalculator``()`                                                                                                             |
    | `DefaultPairwiseCostCalculator``(`[`PairwiseShortestPaths`](PairwiseShortestPaths.md)` pwsp)`<br>Constructs a default pairwise cost calculator. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                | Method and Description                                                                                                                                                                                                                                                                                                                                                           |
    |------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                                        | `calculate``(`[`PointOnNet`](PointOnNet.md)`[][] startPoints, `[`PointOnNet`](PointOnNet.md)`[][] endPoints, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`Matrix`](Matrix.md)`<java.lang.Integer> pairwiseMatrix)`<br>Computes the pairwise shortest path and the pairwise costs using the pairwise shortest paths algorithm passed in to the constructor. |
    | [`Matrix`](Matrix.md)`<double[]>`                                | `getPairwiseCosts``()`<br>Returns the pairwise costs.                                                                                                                                                                                                                                                                                                                            |
    | [`Matrix`](Matrix.md)`<`[`LogicalSubPath`](LogicalSubPath.md)`>` | `getPairwisePaths``()`<br>Returns the pairwise shortest paths.                                                                                                                                                                                                                                                                                                                   |
    | `java.lang.String`                                               | `getXMLSchema``()`<br>Returns the XML schema for the input parameter.                                                                                                                                                                                                                                                                                                            |
    | `void`                                                           | `init``(org.w3c.dom.Element parameter)`<br>Initializes the XML configurable object with the input parameter.                                                                                                                                                                                                                                                                     |
    | `void`                                                           | `setNetworkAnalyst``(`[`NetworkAnalyst`](NetworkAnalyst.md)` analyst)`<br>This method allows caller to pass the network analyst object to this cost calculator implementation, so that the algorithm can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst.                                        |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### DefaultPairwiseCostCalculator

          public DefaultPairwiseCostCalculator()

    <!-- -->

    - #### DefaultPairwiseCostCalculator

          public DefaultPairwiseCostCalculator(PairwiseShortestPaths pwsp)

      Constructs a default pairwise cost calculator.
      Parameters:
      `pwsp` - pairwise shortest path algorithm.

  <!-- -->

  - ### Method Detail

    - #### calculate

          public boolean calculate(PointOnNet[][] startPoints,
                                   PointOnNet[][] endPoints,
                                   LODNetworkConstraint constraint,
                                   Matrix<java.lang.Integer> pairwiseMatrix)
                            throws LODNetworkException

      Computes the pairwise shortest path and the pairwise costs using the pairwise shortest paths algorithm passed in to the constructor.
      Specified by:
      [`calculate`](PairwiseCostCalculator.md) in interface [`PairwiseCostCalculator`](PairwiseCostCalculator.md)

      Parameters:
      `startPoints` -

      `endPoints` -

      `constraint` -

      `pairwiseMatrix` - a matrix that specifies for which pairs the costs need to be computed. If the matrix element for pair (i, j) is set to 0, then the cost from i to j does not need to be computed; otherwise it must be computed. If this parameter is set to null, then the costs for all pairs must be computed.

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### getPairwisePaths

          public Matrix<LogicalSubPath> getPairwisePaths()

      Returns the pairwise shortest paths.
      Specified by:

      [`getPairwisePaths`](PairwiseCostCalculator.md) in interface [`PairwiseCostCalculator`](PairwiseCostCalculator.md)

      Returns:

    <!-- -->

    - #### getPairwiseCosts

          public Matrix<double[]> getPairwiseCosts()

      Returns the pairwise costs.
      Specified by:

      [`getPairwiseCosts`](PairwiseCostCalculator.md) in interface [`PairwiseCostCalculator`](PairwiseCostCalculator.md)

      Returns:

    <!-- -->

    - #### setNetworkAnalyst

          public void setNetworkAnalyst(NetworkAnalyst analyst)

      Description copied from interface: [`PairwiseCostCalculator`](PairwiseCostCalculator.md)
      This method allows caller to pass the network analyst object to this cost calculator implementation, so that the algorithm can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst. If network analyst is not needed by the cost calculator, the calculator can choose to do nothing with this method.
      Specified by:
      [`setNetworkAnalyst`](PairwiseCostCalculator.md) in interface [`PairwiseCostCalculator`](PairwiseCostCalculator.md)

    <!-- -->

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

- [Prev Class](DefaultNodeCostCalculator.md)
- [Next Class](DefaultPairwiseShortestPaths.md)

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
