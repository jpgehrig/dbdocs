Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev Class](CompileCommand.md)
- [Next Class](ConsistentSolveCommand.md)

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

oracle.olapi.syntax

## Class Condition

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.DataObject](DataObject.md)

    - - [oracle.olapi.syntax.Expression](Expression.md)

      - - oracle.olapi.syntax.Condition

<!-- -->

- All Implemented Interfaces:
  [FunctionArgument](FunctionArgument.md)

  <!-- -->

  Direct Known Subclasses:
  [BetweenCondition](BetweenCondition.md), [BinaryOperatorCondition](BinaryOperatorCondition.md), [ComparisonCondition](ComparisonCondition.md), [FunctionCondition](FunctionCondition.md), [HierarchicalCondition](HierarchicalCondition.md), [IsCondition](IsCondition.md), [LikeCondition](LikeCondition.md), [NotCondition](NotCondition.md)

  ------------------------------------------------------------------------



      public abstract class Condition
      extends Expression

  An abstract base class for an `Expression` that represents a condition, which specifies a combination of one or more expressions and logical (Boolean) operators and evaluates to `true`, `false`, `null`, or `UNKNOWN`. The `Condition` class has methods that create a subclass that specifies a logical `AND`, `NOT`, or `OR` condition.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                                           |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
    | `Condition`       | `and``(Condition rhs)`<br>Creates a `Condition` that represents a logical `AND` condition.                                                       |
    | `boolean`         | `isCompositeObject``()`<br>Indicates whether this `Condition` contains other `SyntaxObject` objects.                                             |
    | `Condition`       | `not``()`<br>Creates a `Condition` that represents a logical `NOT` condition, which reverses, or negates, the Boolean value of this `Condition`. |
    | `Condition`       | `or``(Condition rhs)`<br>Creates a `Condition` that represents a logical `OR` condition.                                                         |

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`visit`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### and

          public final Condition and(Condition rhs)

      Creates a `Condition` that represents a logical `AND` condition. The `Condition` returned by this method represents a condition that evaluates to `true` if both this `Condition` and the specifed right-hand-side `Condition` are true, evaluates to `false` if either condition is false, or evaluates to `UNKNOWN` otherwise.
      Parameters:
      `rhs` - A `Condition` that is the right-hand-side condition.

      Returns:
      A `Condition` that represents a logical `AND` operation on this `Condition` and the `rhs` `Condition`.

    <!-- -->

    - #### or

          public final Condition or(Condition rhs)

      Creates a `Condition` that represents a logical `OR` condition. The `Condition` returned by this method represents a condition that evaluates to `true` if either this `Condition` or the specifed right-hand-side `Condition` is true, evaluates to `false` if both conditions are false, or evaluates to `UNKNOWN` otherwise.
      Parameters:
      `rhs` - A `Condition` that is the right-hand-side condition.

      Returns:
      A `Condition` that represents a logical `OR` operation on this `Condition` and the `rhs` `Condition`.

    <!-- -->

    - #### not

          public final Condition not()

      Creates a `Condition` that represents a logical `NOT` condition, which reverses, or negates, the Boolean value of this `Condition`. The `Condition` returned by this method represents a condition that evaluates to `true` if this `Condition` is false, evaluates to `false` if this `Condition` is true, or evaluates to `UNKNOWN` if this `Condition` is `UNKNOWN`.
      Returns:
      A `Condition` that represents the negation of this `Condition`.

    <!-- -->

    - #### isCompositeObject

          public boolean isCompositeObject()

      Indicates whether this `Condition` contains other `SyntaxObject` objects.
      Returns:
      A `boolean` that is `true` if `Condition` contains other `SyntaxObject` objects or is `false` otherwise.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](CompileCommand.md)
- [Next Class](ConsistentSolveCommand.md)

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
