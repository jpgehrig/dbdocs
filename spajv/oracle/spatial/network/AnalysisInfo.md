Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- Prev Class
- [Next Class](AStarCostFunction.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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

oracle.spatial.network

## Interface AnalysisInfo

-

  ------------------------------------------------------------------------



      public interface AnalysisInfo

  This interface defines methods for retrieving the analysis information. The information includes: the start node, the current node, the next node, the current link, the next link, the current path depth (no of links in the path), the current path cost, the current path duration, and all links in the current path.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type     | Method and Description                                                                                                                                                                                                                                                                                                                               |
    |-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `double`              | `getCurrentCost``()`<br>Returns the path cost of current node                                                                                                                                                                                                                                                                                        |
    | `int`                 | `getCurrentDepth``()`<br>Returns the path depth of current node.                                                                                                                                                                                                                                                                                     |
    | `double`              | `getCurrentDuration``()`<br>Returnspath the path duration of current node                                                                                                                                                                                                                                                                            |
    | [`Link`](Link.md)     | `getCurrentLink``()`<br>Returns the current link.                                                                                                                                                                                                                                                                                                    |
    | [`Node`](Node.md)     | `getCurrentNode``()`<br>Returns the current node.                                                                                                                                                                                                                                                                                                    |
    | `double`              | `getNextCost``()`<br>Returns the path cost of next node                                                                                                                                                                                                                                                                                              |
    | `int`                 | `getNextDepth``()`<br>Returns the path depth of next node.                                                                                                                                                                                                                                                                                           |
    | `double`              | `getNextDuration``()`<br>Returnspath the path duration of next node                                                                                                                                                                                                                                                                                  |
    | [`Link`](Link.md)     | `getNextLink``()`<br>Returns the next link.                                                                                                                                                                                                                                                                                                          |
    | [`Node`](Node.md)     | `getNextNode``()`<br>Returns the next node.                                                                                                                                                                                                                                                                                                          |
    | `java.util.Vector`    | `getPathLinkVec``()`<br>Returns the current path links as a Vector.                                                                                                                                                                                                                                                                                  |
    | `java.util.Vector`    | `getPathNodeVec``()`<br>Returns the current path nodes as a Vector.                                                                                                                                                                                                                                                                                  |
    | [`Node`](Node.md)     | `getStartNode``()`<br>Returns the start node.                                                                                                                                                                                                                                                                                                        |
    | `double[][]`          | `getTspNodeDuration``()`<br>Returns the TSP path node duration in an array of double The order of the duration is the same as the one in getTSPNodeNodeOrder() the duration is returned as an array of two doubles duration\[i\]\[0\] represents the arrival duration for the i-th TSP node and This information is only used for TSP related analys |
    | [`Node`](Node.md)`[]` | `getTspNodeOrder``()`<br>Returns the TSP path node visit order in an array of Node This information is only used for TSP related analysis                                                                                                                                                                                                            |

<!-- -->

- - ### Method Detail

    - #### getStartNode

          Node getStartNode()

      Returns the start node.

    <!-- -->

    - #### getCurrentNode

          Node getCurrentNode()

      Returns the current node.

    <!-- -->

    - #### getNextNode

          Node getNextNode()

      Returns the next node.

    <!-- -->

    - #### getCurrentLink

          Link getCurrentLink()

      Returns the current link.

    <!-- -->

    - #### getNextLink

          Link getNextLink()

      Returns the next link.

    <!-- -->

    - #### getCurrentDepth

          int getCurrentDepth()

      Returns the path depth of current node.

    <!-- -->

    - #### getNextDepth

          int getNextDepth()

      Returns the path depth of next node.

    <!-- -->

    - #### getCurrentCost

          double getCurrentCost()

      Returns the path cost of current node

    <!-- -->

    - #### getNextCost

          double getNextCost()

      Returns the path cost of next node

    <!-- -->

    - #### getPathLinkVec

          java.util.Vector getPathLinkVec()

      Returns the current path links as a Vector.

    <!-- -->

    - #### getPathNodeVec

          java.util.Vector getPathNodeVec()

      Returns the current path nodes as a Vector.

    <!-- -->

    - #### getCurrentDuration

          double getCurrentDuration()

      Returnspath the path duration of current node

    <!-- -->

    - #### getNextDuration

          double getNextDuration()

      Returnspath the path duration of next node

    <!-- -->

    - #### getTspNodeOrder

          Node[] getTspNodeOrder()

      Returns the TSP path node visit order in an array of Node This information is only used for TSP related analysis

    <!-- -->

    - #### getTspNodeDuration

          double[][] getTspNodeDuration()

      Returns the TSP path node duration in an array of double The order of the duration is the same as the one in getTSPNodeNodeOrder() the duration is returned as an array of two doubles duration\[i\]\[0\] represents the arrival duration for the i-th TSP node and This information is only used for TSP related analys

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Spatial and Graph Java API Reference
Release 19.1, E94803-01**

- Prev Class
- [Next Class](AStarCostFunction.md)

<!-- -->

- [Frames](../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../allclasses-noframe.md)

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
