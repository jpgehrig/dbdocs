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

- [Prev Class](TspAnalysisInfo.md)
- [Next Class](TspConstraintOperator.md)

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

## Interface TspConstraint

- All Superinterfaces:
  [Constraint](Constraint.md)\<[TspAnalysisInfo](TspAnalysisInfo.md)\>

  <!-- -->

  All Known Implementing Classes:
  [TspConstraintOperator.CombinedConstraint](TspConstraintOperator.CombinedConstraint.md), [TspImpl.NetworkTspConstraint](TspImpl.NetworkTspConstraint.md), [TspOrderConstraint](TspOrderConstraint.md), [TspTimeWindowConstraint](TspTimeWindowConstraint.md)

  ------------------------------------------------------------------------



      public interface TspConstraint
      extends Constraint<TspAnalysisInfo>

  Since:
  release specific (what release of product did this appear in)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                                                                                                                                                                                                 |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `int[]`           | `getUserDataCategories``()`<br>Returns the required user data categories.                                                                                                                                                                                                                                              |
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

- [Prev Class](TspAnalysisInfo.md)
- [Next Class](TspConstraintOperator.md)

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
