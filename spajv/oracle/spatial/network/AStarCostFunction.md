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

- [Prev Class](AnalysisInfo.md)
- [Next Class](GeometryMetadata.md)

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

## Interface AStarCostFunction

-

  ------------------------------------------------------------------------



      public interface AStarCostFunction

  This interface defines the heuristic cost function for A\* search Users can provide their own cost estimates to guide the A\* search. Default heuristic cost for spatial networks is the Euliddean cost and 0 for logical networks.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                                              |
    |-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `double`          | `getHeuristicCost``(java.lang.Object currentNodeObj, java.lang.Object goalNodeObj)`<br>Returns the heuristic cost between 2 AStarNodes (currnet node and goal node) |

<!-- -->

- - ### Method Detail

    - #### getHeuristicCost

          double getHeuristicCost(java.lang.Object currentNodeObj,
                                  java.lang.Object goalNodeObj)

      Returns the heuristic cost between 2 AStarNodes (currnet node and goal node)
      Parameters:
      `currentNodeObj` - AStarNode current node object

      `goalNodeObj` - AStarNode goal node object

      Returns:
      A\* heuristic cost (estimated cost from current node to goal node)

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

- [Prev Class](AnalysisInfo.md)
- [Next Class](GeometryMetadata.md)

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
