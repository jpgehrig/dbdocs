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

- [Prev Class](Tsp2Opt.md)
- [Next Class](TspConstraint.md)

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

## Class TspAnalysisInfo

- java.lang.Object

- - [oracle.spatial.network.lod.LODAnalysisInfo](LODAnalysisInfo.md)

  - - oracle.spatial.network.lod.TspAnalysisInfo

<!-- -->

-

  ------------------------------------------------------------------------



      public class TspAnalysisInfo
      extends LODAnalysisInfo

  This class contains the TSP points in order, besides other info in LODAnalysisInfo.
  Since:
  Oracle Database 11g Release 2 (11.2)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                 |
    |-----------------------------------------------------------------------------|
    | `TspAnalysisInfo``(int numTspPoints)`<br>Creates an TspAnalysisInfo object. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                          |
    |-------------------|-------------------------------------------------------------------------------------------------|
    | `double[]`        | `getTspCosts``(int pointIndex)`<br>Returns the costs to reach the input tsp point.              |
    | `int[]`           | `getTspOrder``()`<br>Returns TSP points in order.                                               |
    | `void`            | `setTspCosts``(int pointIndex, double[] costs)`<br>Sets the costs to reach the input tsp point. |
    | `void`            | `setTspOrder``(int[] tspOrder)`<br>Sets TSP points in order                                     |

    - ### Methods inherited from class oracle.spatial.network.lod.[LODAnalysisInfo](LODAnalysisInfo.md)

      [`getCurrentCost`](LODAnalysisInfo.md)`, `[`getCurrentCosts`](LODAnalysisInfo.md)`, `[`getCurrentDepth`](LODAnalysisInfo.md)`, `[`getCurrentLink`](LODAnalysisInfo.md)`, `[`getCurrentNode`](LODAnalysisInfo.md)`, `[`getCurrentUserObjects`](LODAnalysisInfo.md)`, `[`getDirection`](LODAnalysisInfo.md)`, `[`getEndNode`](LODAnalysisInfo.md)`, `[`getEndPoint`](LODAnalysisInfo.md)`, `[`getEndPoints`](LODAnalysisInfo.md)`, `[`getExpandedNode`](LODAnalysisInfo.md)`, `[`getNextCost`](LODAnalysisInfo.md)`, `[`getNextCosts`](LODAnalysisInfo.md)`, `[`getNextDepth`](LODAnalysisInfo.md)`, `[`getNextLink`](LODAnalysisInfo.md)`, `[`getNextNode`](LODAnalysisInfo.md)`, `[`getNextUserObject`](LODAnalysisInfo.md)`, `[`getStartNode`](LODAnalysisInfo.md)`, `[`getStartPoint`](LODAnalysisInfo.md)`, `[`getStartPoints`](LODAnalysisInfo.md)`, `[`setDirection`](LODAnalysisInfo.md)`, `[`setNextUserObject`](LODAnalysisInfo.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### TspAnalysisInfo

          public TspAnalysisInfo(int numTspPoints)

      Creates an TspAnalysisInfo object.
      Parameters:
      `numTspPoints` - number of TSP points

  <!-- -->

  - ### Method Detail

    - #### getTspOrder

          public int[] getTspOrder()

      Returns TSP points in order. Each element in the returned array is the first member of a TSP point candidate array in the TSP analysis.
      Returns:

    <!-- -->

    - #### setTspOrder

          public void setTspOrder(int[] tspOrder)

      Sets TSP points in order
      Parameters:
      `tspOrder` - TSP points in order. Each element in the input array is the first member of a TSP point candidate array in the TSP analysis.

    <!-- -->

    - #### getTspCosts

          public double[] getTspCosts(int pointIndex)

      Returns the costs to reach the input tsp point.

    <!-- -->

    - #### setTspCosts

          public void setTspCosts(int pointIndex,
                                  double[] costs)

      Sets the costs to reach the input tsp point.

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

- [Prev Class](Tsp2Opt.md)
- [Next Class](TspConstraint.md)

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
