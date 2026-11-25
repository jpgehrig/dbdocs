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

- [Prev Class](Constraint.md)
- [Next Class](DefaultLinkCostCalculator.md)

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

## Class ConstraintOperator

- java.lang.Object

- - oracle.spatial.network.lod.ConstraintOperator

<!-- -->

-

  ------------------------------------------------------------------------



      public class ConstraintOperator
      extends java.lang.Object

  Supports "and", "or", and "not" operations on network constraints.
  Since:
  Oracle Database 11g Release 2 (11.2)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `ConstraintOperator``()`    |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                          | Method and Description                                                                                                                                                  |
    |------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`LODNetworkConstraint`](LODNetworkConstraint.md) | `and``(`[`LODNetworkConstraint`](LODNetworkConstraint.md)`[] constraints)`<br>Performs "and" operation on an array of constraints, and returns the combined constraint. |
    | `static `[`LODNetworkConstraint`](LODNetworkConstraint.md) | `not``(`[`LODNetworkConstraint`](LODNetworkConstraint.md)` constraint)`<br>Performs "not" operation on the specified constraint, and returns the opposite constraint.   |
    | `static `[`LODNetworkConstraint`](LODNetworkConstraint.md) | `or``(`[`LODNetworkConstraint`](LODNetworkConstraint.md)`[] constraints)`<br>Performs "or" operation on an array of constraints, and returns the combined constraint.   |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### ConstraintOperator

          public ConstraintOperator()

  <!-- -->

  - ### Method Detail

    - #### and

          public static LODNetworkConstraint and(LODNetworkConstraint[] constraints)

      Performs "and" operation on an array of constraints, and returns the combined constraint.
      Parameters:

      `constraints` -

      Returns:

    <!-- -->

    - #### or

          public static LODNetworkConstraint or(LODNetworkConstraint[] constraints)

      Performs "or" operation on an array of constraints, and returns the combined constraint.
      Parameters:

      `constraints` -

      Returns:

    <!-- -->

    - #### not

          public static LODNetworkConstraint not(LODNetworkConstraint constraint)

      Performs "not" operation on the specified constraint, and returns the opposite constraint.
      Parameters:

      `constraint` -

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

- [Prev Class](Constraint.md)
- [Next Class](DefaultLinkCostCalculator.md)

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
