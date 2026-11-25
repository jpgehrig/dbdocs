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

- [Prev Class](LODGoalNode.md)
- [Next Class](LODNetworkException.md)

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

## Interface LODNetworkConstraint

- All Superinterfaces:
  [Constraint](Constraint.md)\<[LODAnalysisInfo](LODAnalysisInfo.md)\>

  <!-- -->

  All Known Implementing Classes:
  [MaxCostConstraint](MaxCostConstraint.md), [MaxDepthConstraint](MaxDepthConstraint.md)

  ------------------------------------------------------------------------



      public interface LODNetworkConstraint
      extends Constraint<LODAnalysisInfo>

  This interface defines a general network constraint for network analysis. With this interface, users can plug in their own network constraint logic, which will be called during network analysis.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                                                 |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int`             | `getNumberOfUserObjects``()`<br>Returns the max number of user objects to be returned by the getCurrentUserObjects method in LODAnalysisInfo.                                                                                                                                                                          |
    | `int[]`           | `getUserDataCategories``()`<br>Returns the required user data categories.                                                                                                                                                                                                                                              |
    | `boolean`         | `isCurrentNodePartiallyExpanded``(`[`LODAnalysisInfo`](LODAnalysisInfo.md)` info)`<br>While expanding a node during network search, the search algorithm may not be able to access all the outgoing links due to network constraint, and we call a node with unaccessible outgoing links partially expanded node.      |
    | `void`            | `reset``()`<br>This method allows a stateful network constraint object to be reset to its original state and reused by network analysis functions.                                                                                                                                                                     |
    | `void`            | `setNetworkAnalyst``(`[`NetworkAnalyst`](NetworkAnalyst.md)` analyst)`<br>This method allows caller to pass the network analyst object to this constraint, so that the constraint can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst. |

    - ### Methods inherited from interface oracle.spatial.network.lod.[Constraint](Constraint.md)

      [`isSatisfied`](Constraint.md)

<!-- -->

- - ### Method Detail

    - #### getUserDataCategories

          int[] getUserDataCategories()

      Returns the required user data categories.
      Returns:

    <!-- -->

    - #### getNumberOfUserObjects

          int getNumberOfUserObjects()

      Returns the max number of user objects to be returned by the getCurrentUserObjects method in LODAnalysisInfo.
      Returns:

    <!-- -->

    - #### isCurrentNodePartiallyExpanded

          boolean isCurrentNodePartiallyExpanded(LODAnalysisInfo info)

      While expanding a node during network search, the search algorithm may not be able to access all the outgoing links due to network constraint, and we call a node with unaccessible outgoing links partially expanded node. However, if the node can be revisited and expanded again later, say from a different incoming link, then the unaccessible outgoing links might become accessible, making the node fully expanded. In this case, this method should return true if the current node is partially expanded at this point of the search, and false when the current node is fully expanded.
      A node should be considered partially expanded if you plan to revisit it after it is expanded, even if all the outgoing links from the node has been accessed.
      The contraint implementation class needs to maintain a partially expanded node list, which contains all the nodes that can be revisited later during the search and the corresponding outgoing link status associated with these nodes. Each time the node is revisited, the status of its outgoing links needs to be updated. A node should be removed from the partially expanded list when it no longer needs to be revisited.
      Parameters:

      `info` -

      Returns:

    <!-- -->

    - #### reset

          void reset()

      This method allows a stateful network constraint object to be reset to its original state and reused by network analysis functions.

    <!-- -->

    - #### setNetworkAnalyst

          void setNetworkAnalyst(NetworkAnalyst analyst)

      This method allows caller to pass the network analyst object to this constraint, so that the constraint can call the analysis functions provided by the network analyst, or access the network explorer associated with the network analyst. If network analyst is not needed by the constraint, the link level selector can choose to do nothing with this method.

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

- [Prev Class](LODGoalNode.md)
- [Next Class](LODNetworkException.md)

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
