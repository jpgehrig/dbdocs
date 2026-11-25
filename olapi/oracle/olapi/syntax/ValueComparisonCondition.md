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

- [Prev Class](UnresolvedQuery.md)
- Next Class

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

## Class ValueComparisonCondition

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.DataObject](DataObject.md)

    - - [oracle.olapi.syntax.Expression](Expression.md)

      - - [oracle.olapi.syntax.Condition](Condition.md)

        - - [oracle.olapi.syntax.ComparisonCondition](ComparisonCondition.md)

          - - oracle.olapi.syntax.ValueComparisonCondition

<!-- -->

- All Implemented Interfaces:
  [FunctionArgument](FunctionArgument.md)

  ------------------------------------------------------------------------



      public final class ValueComparisonCondition
      extends ComparisonCondition

  A `ComparisonCondition` that represents a simple comparison condition, which compares one expression to another expression.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from class oracle.olapi.syntax.[ComparisonCondition](ComparisonCondition.md)

      [`EQ`](ComparisonCondition.md)`, `[`GE`](ComparisonCondition.md)`, `[`GT`](ComparisonCondition.md)`, `[`LE`](ComparisonCondition.md)`, `[`LT`](ComparisonCondition.md)`, `[`NE`](ComparisonCondition.md)`, `[`NE2`](ComparisonCondition.md)`, `[`NE3`](ComparisonCondition.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                    |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `ValueComparisonCondition``(`[`TypedExpression`](TypedExpression.md)` lhsArgument, java.lang.String operator, `[`TypedExpression`](TypedExpression.md)` rhsArgument)`<br>Creates a new `ValueComparisonCondition` that has the specified left-hand-side and right-hand-side argument expressions and operator. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                       | Method and Description                                                                                                                                                                                                                                  |
    |-----------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`TypedExpression`](TypedExpression.md) | `getRhsArgument``()`<br>Gets the expression that is the right-hand-side argument of this `ValueComprisonCondition`.                                                                                                                                     |
    | `java.lang.Object`                      | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitValueComparisonCondition` method of the `SyntaxObjectVisitor` and passes that method this `ValueComparisonCondition` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[ComparisonCondition](ComparisonCondition.md)

      [`getLhsArgument`](ComparisonCondition.md)`, `[`getOperator`](ComparisonCondition.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.syntax.[Condition](Condition.md)

      [`and`](Condition.md)`, `[`isCompositeObject`](Condition.md)`, `[`not`](Condition.md)`, `[`or`](Condition.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### ValueComparisonCondition

          public ValueComparisonCondition(TypedExpression lhsArgument,
                                          java.lang.String operator,
                                          TypedExpression rhsArgument)

      Creates a new `ValueComparisonCondition` that has the specified left-hand-side and right-hand-side argument expressions and operator.
      Parameters:
      `lhsArgument` - The `TypedExpression` to use as the left-hand-side argument.

      `operator` - The operator to use, which can be any of the `ComparisonCondition` constants.

      `rhsArgument` - The `TypedExpression` to use as the right-hand-side argument.

  <!-- -->

  - ### Method Detail

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitValueComparisonCondition` method of the `SyntaxObjectVisitor` and passes that method this `ValueComparisonCondition` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitValueComparisonCondition` method.

    <!-- -->

    - #### getRhsArgument

          public TypedExpression getRhsArgument()

      Gets the expression that is the right-hand-side argument of this `ValueComprisonCondition`.
      Returns:
      A `TypedExpression` that is the right-hand-side argument of this `ValueComprisonCondition`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](UnresolvedQuery.md)
- Next Class

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
