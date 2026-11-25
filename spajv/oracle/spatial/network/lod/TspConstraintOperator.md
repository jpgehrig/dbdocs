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

- [Prev Class](TspConstraint.md)
- [Next Class](TspConstraintOperator.CombinedConstraint.md)

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

## Class TspConstraintOperator

- java.lang.Object

- - oracle.spatial.network.lod.TspConstraintOperator

<!-- -->

-

  ------------------------------------------------------------------------



      public class TspConstraintOperator
      extends java.lang.Object

  Since:
  release specific (what release of product did this appear in)

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Class and Description                                                                      |
    |-------------------|--------------------------------------------------------------------------------------------|
    | `static class `   | [`TspConstraintOperator.CombinedConstraint`](TspConstraintOperator.CombinedConstraint.md)  |

  <!-- -->

  - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description |
    |-------------------|-----------------------|
    | `static int`      | `AND`                 |
    | `static int`      | `NOT`                 |
    | `static int`      | `OR`                  |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description  |
    |------------------------------|
    | `TspConstraintOperator``()`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                            | Method and Description                                                                                                                                    |
    |----------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static `[`TspConstraint`](TspConstraint.md) | `and``(`[`TspConstraint`](TspConstraint.md)`[] constraints)`<br>Performs "and" operation on an array of constraints, and returns the combined constraint. |
    | `static `[`TspConstraint`](TspConstraint.md) | `not``(`[`TspConstraint`](TspConstraint.md)` constraint)`<br>Performs "not" operation on the specified constraint, and returns the opposite constraint.   |
    | `static `[`TspConstraint`](TspConstraint.md) | `or``(`[`TspConstraint`](TspConstraint.md)`[] constraints)`<br>Performs "or" operation on an array of constraints, and returns the combined constraint.   |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### AND

          public static final int AND

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### OR

          public static final int OR

      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### NOT

          public static final int NOT

      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### TspConstraintOperator

          public TspConstraintOperator()

  <!-- -->

  - ### Method Detail

    - #### and

          public static TspConstraint and(TspConstraint[] constraints)

      Performs "and" operation on an array of constraints, and returns the combined constraint.
      Parameters:

      `constraints` -

      Returns:

    <!-- -->

    - #### or

          public static TspConstraint or(TspConstraint[] constraints)

      Performs "or" operation on an array of constraints, and returns the combined constraint.
      Parameters:

      `constraints` -

      Returns:

    <!-- -->

    - #### not

          public static TspConstraint not(TspConstraint constraint)

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

- [Prev Class](TspConstraint.md)
- [Next Class](TspConstraintOperator.CombinedConstraint.md)

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
