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

- [Prev Class](GeodeticCostFunction.md)
- [Next Class](GoalNodeOperator.md)

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

## Class GeodeticPairwiseCostCalculator

- java.lang.Object

- - oracle.spatial.network.lod.GeodeticPairwiseCostCalculator

<!-- -->

- All Implemented Interfaces:
  [PairwiseCostCalculator](PairwiseCostCalculator.md), [XMLConfigurable](XMLConfigurable.md)

  ------------------------------------------------------------------------



      public class GeodeticPairwiseCostCalculator
      extends java.lang.Object
      implements PairwiseCostCalculator, XMLConfigurable

  Since:
  release specific (what release of product did this appear in)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description           |
    |---------------------------------------|
    | `GeodeticPairwiseCostCalculator``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                | Method and Description                                                                                                                                                                                                                                                                                                                    |
    |------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                                        | `calculate``(`[`PointOnNet`](PointOnNet.md)`[][] startPoints, `[`PointOnNet`](PointOnNet.md)`[][] endPoints, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`Matrix`](Matrix.md)`<java.lang.Integer> pairwiseMatrix)`<br>Computes the pairwise costs between two sets of points.                                       |
    | [`Matrix`](Matrix.md)`<double[]>`                                | `getPairwiseCosts``()`<br>Returns the pairwise costs that was computed when calculate was called.                                                                                                                                                                                                                                         |
    | [`Matrix`](Matrix.md)`<`[`LogicalSubPath`](LogicalSubPath.md)`>` | `getPairwisePaths``()`<br>Returns the pairwise paths that was computed when calculate was called.                                                                                                                                                                                                                                         |
    | `java.lang.String`                                               | `getXMLSchema``()`<br>Returns the XML schema for the input parameter.                                                                                                                                                                                                                                                                     |
    | `void`                                                           | `init``(org.w3c.dom.Element parameter)`<br>Initializes the XML configurable object with the input parameter.                                                                                                                                                                                                                              |
    | `void`                                                           | `setNetworkAnalyst``(`[`NetworkAnalyst`](NetworkAnalyst.md)` analyst)`<br>This method allows caller to pass the network analyst object to this cost calculator implementation, so that the algorithm can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### GeodeticPairwiseCostCalculator

          public GeodeticPairwiseCostCalculator()

  <!-- -->

  - ### Method Detail

    - #### calculate

          public boolean calculate(PointOnNet[][] startPoints,
                                   PointOnNet[][] endPoints,
                                   LODNetworkConstraint constraint,
                                   Matrix<java.lang.Integer> pairwiseMatrix)
                            throws LODNetworkException

      Description copied from interface: [`PairwiseCostCalculator`](PairwiseCostCalculator.md)
      Computes the pairwise costs between two sets of points.
      Specified by:
      [`calculate`](PairwiseCostCalculator.md) in interface [`PairwiseCostCalculator`](PairwiseCostCalculator.md)

      Parameters:
      `startPoints` - start point candidates

      `endPoints` - end point candidates

      `constraint` - network constraint

      `pairwiseMatrix` - a matrix that specifies for which pairs the costs need to be computed. If the matrix element for pair (i, j) is set to 0, then the cost from i to j does not need to be computed; otherwise it must be computed. If this parameter is set to null, then the costs for all pairs must be computed.

      Returns:
      true if the pairwise paths are also computed in addition to the pairwise costs; false otherwise

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### getPairwisePaths

          public Matrix<LogicalSubPath> getPairwisePaths()

      Description copied from interface: [`PairwiseCostCalculator`](PairwiseCostCalculator.md)
      Returns the pairwise paths that was computed when calculate was called. Returns null if the pairwise paths were not computed.
      Specified by:

      [`getPairwisePaths`](PairwiseCostCalculator.md) in interface [`PairwiseCostCalculator`](PairwiseCostCalculator.md)

      Returns:

    <!-- -->

    - #### getPairwiseCosts

          public Matrix<double[]> getPairwiseCosts()

      Description copied from interface: [`PairwiseCostCalculator`](PairwiseCostCalculator.md)
      Returns the pairwise costs that was computed when calculate was called. The pairwise costs must have been computed when calculate was called.
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

- [Prev Class](GeodeticCostFunction.md)
- [Next Class](GoalNodeOperator.md)

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
