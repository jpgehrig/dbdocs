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

- [Prev Class](ClusterSizeConstraint.md)
- [Next Class](ConstraintOperator.md)

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

## Interface Constraint\<T\>

- All Known Subinterfaces:
  [LODNetworkConstraint](LODNetworkConstraint.md), [TspConstraint](TspConstraint.md)

  <!-- -->

  All Known Implementing Classes:
  [MaxCostConstraint](MaxCostConstraint.md), [MaxDepthConstraint](MaxDepthConstraint.md), [TspConstraintOperator.CombinedConstraint](TspConstraintOperator.CombinedConstraint.md), [TspImpl.NetworkTspConstraint](TspImpl.NetworkTspConstraint.md), [TspOrderConstraint](TspOrderConstraint.md), [TspTimeWindowConstraint](TspTimeWindowConstraint.md)

  ------------------------------------------------------------------------



      public interface Constraint<T>

  Since:
  12.2

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                               |
    |-------------------|----------------------------------------------------------------------|
    | `boolean`         | `isSatisfied``(T context)`<br>Checks if the constraint is satisfied. |

<!-- -->

- - ### Method Detail

    - #### isSatisfied

          boolean isSatisfied(T context)

      Checks if the constraint is satisfied.
      Parameters:
      `context` - the analysis context

      See Also:
      [`LODAnalysisInfo`](LODAnalysisInfo.md)

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

- [Prev Class](ClusterSizeConstraint.md)
- [Next Class](ConstraintOperator.md)

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
