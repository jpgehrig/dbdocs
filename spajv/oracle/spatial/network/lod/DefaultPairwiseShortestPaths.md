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

- [Prev Class](DefaultPairwiseCostCalculator.md)
- [Next Class](DefaultSingleSourceShortestPaths.md)

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

## Class DefaultPairwiseShortestPaths

- java.lang.Object

- - oracle.spatial.network.lod.DefaultPairwiseShortestPaths

<!-- -->

- All Implemented Interfaces:
  [PairwiseShortestPaths](PairwiseShortestPaths.md), [XMLConfigurable](XMLConfigurable.md)

  ------------------------------------------------------------------------



      public class DefaultPairwiseShortestPaths
      extends java.lang.Object
      implements PairwiseShortestPaths, XMLConfigurable

  This is the default pairwise shortest paths algorithm. It computes the pairwise shortest paths one by one using the input shortest path algorithm.
  Since:
  Oracle Database 11g Release 2 (11.2)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                      |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `DefaultPairwiseShortestPaths``(`[`NetworkExplorer`](NetworkExplorer.md)` ne, `[`LinkCostCalculator`](LinkCostCalculator.md)`[] lccs, `[`NodeCostCalculator`](NodeCostCalculator.md)`[] nccs, `[`ShortestPath`](ShortestPath.md)` spAlgorithm)`<br>Deprecated.   |
    | `DefaultPairwiseShortestPaths``(`[`ShortestPath`](ShortestPath.md)` spAlgorithm)`<br>Construct a DefaultPairwiseShortestPaths instance.                                                                                                                          |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                          | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    |----------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`                                                         | `getXMLSchema``()`<br>Returns the XML schema for the input parameter.                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `void`                                                                     | `init``(org.w3c.dom.Element parameter)`<br>Initializes the XML configurable object with the input parameter.                                                                                                                                                                                                                                                                                                                                                                                            |
    | `void`                                                                     | `setInitialAnalysisInfo``(`[`LODAnalysisInfo`](LODAnalysisInfo.md)` analysisInfo)`                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `void`                                                                     | `setNetworkAnalyst``(`[`NetworkAnalyst`](NetworkAnalyst.md)` analyst)`<br>This method allows caller to pass the network analyst object to this pairwise shortest paths implementation, so that the algorithm can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst.                                                                                                                                                       |
    | `double[][]`                                                               | `shortestPathCosts``(`[`PointOnNet`](PointOnNet.md)`[][] startPoints, `[`PointOnNet`](PointOnNet.md)`[][] endPoints, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`Matrix`](Matrix.md)`<java.lang.Integer> pairwiseMatrix, int direction)`<br>Returns the pair-wise shortest path cost between a set of candidate start points and end points.                                                                                                                                     |
    | [`Matrix`](Matrix.md)`<`[`LogicalSubPath`](LogicalSubPath.md)`>`           | `shortestPaths``(`[`PointOnNet`](PointOnNet.md)`[][] startPoints, `[`PointOnNet`](PointOnNet.md)`[][] endPoints, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`Matrix`](Matrix.md)`<java.lang.Integer> pairwiseMatrix, int direction)`<br>Returns the pair-wise shortest paths between a set of candidate start points and end points.                                                                                                                                             |
    | [`Matrix`](Matrix.md)`<`[`LogicalLightSubPath`](LogicalLightSubPath.md)`>` | `shortestPathsLight``(`[`PointOnNet`](PointOnNet.md)`[][] startPoints, `[`PointOnNet`](PointOnNet.md)`[][] endPoints, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`Matrix`](Matrix.md)`<java.lang.Integer> pairwiseMatrix, int direction)`<br>Returns the pair-wise light weight shortest paths between a set of candidate start points and end points.                                                                                                                           |
    | `void`                                                                     | `shortestPathsLight``(`[`PointOnNet`](PointOnNet.md)`[][] startPoints, `[`PointOnNet`](PointOnNet.md)`[][] endPoints, `[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint, `[`Matrix`](Matrix.md)`<java.lang.Integer> pairwiseMatrix, int direction, `[`PairwisePathResultIO`](PairwisePathResultIO.md)` pathIO)`<br>Computes the pair-wise light weight shortest paths between a set of candidate start points and end points, and outputs the light weight paths via PairwisePathResultIO. |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### DefaultPairwiseShortestPaths

          public DefaultPairwiseShortestPaths(NetworkExplorer ne,
                                              LinkCostCalculator[] lccs,
                                              NodeCostCalculator[] nccs,
                                              ShortestPath spAlgorithm)

      Deprecated. 
      Parameters:
      `ne` -

      `lccs` -

      `nccs` -

      `spAlgorithm` -

    <!-- -->

    - #### DefaultPairwiseShortestPaths

          public DefaultPairwiseShortestPaths(ShortestPath spAlgorithm)

      Construct a DefaultPairwiseShortestPaths instance.
      Parameters:
      `spAlgorithm` -

  <!-- -->

  - ### Method Detail

    - #### setInitialAnalysisInfo

          public void setInitialAnalysisInfo(LODAnalysisInfo analysisInfo)

    <!-- -->

    - #### shortestPaths

          public Matrix<LogicalSubPath> shortestPaths(PointOnNet[][] startPoints,
                                                      PointOnNet[][] endPoints,
                                                      LODNetworkConstraint constraint,
                                                      Matrix<java.lang.Integer> pairwiseMatrix,
                                                      int direction)
                                               throws LODNetworkException

      Description copied from interface: [`PairwiseShortestPaths`](PairwiseShortestPaths.md)
      Returns the pair-wise shortest paths between a set of candidate start points and end points.
      Specified by:
      [`shortestPaths`](PairwiseShortestPaths.md) in interface [`PairwiseShortestPaths`](PairwiseShortestPaths.md)

      Parameters:
      `startPoints` - array of start candidates

      `endPoints` - array of end candidates

      `constraint` - network constraint

      `pairwiseMatrix` - a matrix that specifies for which pairs the shortest paths need to be computed. If the matrix element for pair (i, j) is set to 0, then the shortest path from i to j does not need to be computed; otherwise it must be computed. If this parameter is set to null, then the shortest paths for all pairs must be computed.

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### shortestPathsLight

          public Matrix<LogicalLightSubPath> shortestPathsLight(PointOnNet[][] startPoints,
                                                                PointOnNet[][] endPoints,
                                                                LODNetworkConstraint constraint,
                                                                Matrix<java.lang.Integer> pairwiseMatrix,
                                                                int direction)
                                                         throws LODNetworkException

      Description copied from interface: [`PairwiseShortestPaths`](PairwiseShortestPaths.md)
      Returns the pair-wise light weight shortest paths between a set of candidate start points and end points.
      Specified by:
      [`shortestPathsLight`](PairwiseShortestPaths.md) in interface [`PairwiseShortestPaths`](PairwiseShortestPaths.md)

      Parameters:
      `startPoints` - array of start candidates

      `endPoints` - array of end candidates

      `constraint` - network constraint

      `pairwiseMatrix` - a matrix that specifies for which pairs the shortest paths need to be computed. If the matrix element for pair (i, j) is set to 0, then the shortest path from i to j does not need to be computed; otherwise it must be computed. If this parameter is set to null, then the shortest paths for all pairs must be computed.

      Returns:
      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### setNetworkAnalyst

          public void setNetworkAnalyst(NetworkAnalyst analyst)

      Description copied from interface: [`PairwiseShortestPaths`](PairwiseShortestPaths.md)
      This method allows caller to pass the network analyst object to this pairwise shortest paths implementation, so that the algorithm can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst. If network analyst is not needed by the algorithm, the algorithm can choose to do nothing with this method.
      Specified by:
      [`setNetworkAnalyst`](PairwiseShortestPaths.md) in interface [`PairwiseShortestPaths`](PairwiseShortestPaths.md)

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

    <!-- -->

    - #### shortestPathsLight

          public void shortestPathsLight(PointOnNet[][] startPoints,
                                         PointOnNet[][] endPoints,
                                         LODNetworkConstraint constraint,
                                         Matrix<java.lang.Integer> pairwiseMatrix,
                                         int direction,
                                         PairwisePathResultIO pathIO)
                                  throws LODNetworkException

      Description copied from interface: [`PairwiseShortestPaths`](PairwiseShortestPaths.md)
      Computes the pair-wise light weight shortest paths between a set of candidate start points and end points, and outputs the light weight paths via PairwisePathResultIO.
      Specified by:
      [`shortestPathsLight`](PairwiseShortestPaths.md) in interface [`PairwiseShortestPaths`](PairwiseShortestPaths.md)

      Parameters:
      `startPoints` - array of start candidates

      `endPoints` - array of end candidates

      `constraint` - network constraint

      `pairwiseMatrix` - a matrix that specifies for which pairs the shortest paths need to be computed. If the matrix element for pair (i, j) is set to 0, then the shortest path from i to j does not need to be computed; otherwise it must be computed. If this parameter is set to null, then the shortest paths for all pairs must be computed.

      Throws:
      [`LODNetworkException`](LODNetworkException.md)

    <!-- -->

    - #### shortestPathCosts

          public double[][] shortestPathCosts(PointOnNet[][] startPoints,
                                              PointOnNet[][] endPoints,
                                              LODNetworkConstraint constraint,
                                              Matrix<java.lang.Integer> pairwiseMatrix,
                                              int direction)
                                       throws LODNetworkException

      Description copied from interface: [`PairwiseShortestPaths`](PairwiseShortestPaths.md)
      Returns the pair-wise shortest path cost between a set of candidate start points and end points. This method can be used when the caller is only interested in path costs. the light path results.
      Specified by:
      [`shortestPathCosts`](PairwiseShortestPaths.md) in interface [`PairwiseShortestPaths`](PairwiseShortestPaths.md)

      Parameters:
      `startPoints` - array of start candidates

      `endPoints` - array of end candidates

      `constraint` - network constraint

      `pairwiseMatrix` - a matrix that specifies for which pairs the shortest paths need to be computed. If the matrix element for pair (i, j) is set to 0, then the shortest path from i to j does not need to be computed; otherwise it must be computed. If this parameter is set to null, then the shortest paths for all pairs must be computed.

      Returns:
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

- [Prev Class](DefaultPairwiseCostCalculator.md)
- [Next Class](DefaultSingleSourceShortestPaths.md)

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
