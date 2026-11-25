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

- [Prev Class](GeodeticPairwiseCostCalculator.md)
- [Next Class](HeavyPointOnNet.md)

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

## Class GoalNodeOperator

- java.lang.Object

- - oracle.spatial.network.lod.GoalNodeOperator

<!-- -->

-

  ------------------------------------------------------------------------



      public class GoalNodeOperator
      extends java.lang.Object

  Supports "and", "or", and "not" operations on goal node filters.
  Since:
  Oracle Database 11g Release 1 (11.1)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `GoalNodeOperator``()`      |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                        | Method and Description                                                                                                                                          |
    |------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`LODGoalNode`](LODGoalNode.md) | `and``(`[`LODGoalNode`](LODGoalNode.md)`[] goalNodes)`<br>Performs "and" operation on an array of goal node filters, and returns the combined goal node filter. |
    | `static `[`LODGoalNode`](LODGoalNode.md) | `not``(`[`LODGoalNode`](LODGoalNode.md)` goalNode)`<br>Performs "not" operation on the specified goal node filter, and returns the opposite goal node filter.   |
    | `static `[`LODGoalNode`](LODGoalNode.md) | `or``(`[`LODGoalNode`](LODGoalNode.md)`[] goalNodes)`<br>Performs "or" operation on an array of goal node filters, and returns the combined goal node filter.   |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### GoalNodeOperator

          public GoalNodeOperator()

  <!-- -->

  - ### Method Detail

    - #### and

          public static LODGoalNode and(LODGoalNode[] goalNodes)

      Performs "and" operation on an array of goal node filters, and returns the combined goal node filter.

    <!-- -->

    - #### or

          public static LODGoalNode or(LODGoalNode[] goalNodes)

      Performs "or" operation on an array of goal node filters, and returns the combined goal node filter.

    <!-- -->

    - #### not

          public static LODGoalNode not(LODGoalNode goalNode)

      Performs "not" operation on the specified goal node filter, and returns the opposite goal node filter.

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

- [Prev Class](GeodeticPairwiseCostCalculator.md)
- [Next Class](HeavyPointOnNet.md)

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
