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

- [Prev Class](BaseQuery.md)
- [Next Class](BinaryOperatorCondition.md)

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

## Class BetweenCondition

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.DataObject](DataObject.md)

    - - [oracle.olapi.syntax.Expression](Expression.md)

      - - [oracle.olapi.syntax.Condition](Condition.md)

        - - oracle.olapi.syntax.BetweenCondition

<!-- -->

- All Implemented Interfaces:
  [FunctionArgument](FunctionArgument.md)

  ------------------------------------------------------------------------



      public final class BetweenCondition
      extends Condition

  A `Condition` that represents a `BETWEEN` condition, which determines whether a value is in a specific range of values. A `BetweenCondition` evaluates to `true` if the base expression is greater than or equal to the start expression and is less than or equal to the end expression.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                                                     |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `BetweenCondition``(`[`TypedExpression`](TypedExpression.md)` baseExpression, `[`TypedExpression`](TypedExpression.md)` startExpression, `[`TypedExpression`](TypedExpression.md)` endExpression)`<br>Creates a new `BetweenCondition` that has the specified base, start, and end expressions and determines whether the base value is in the range of values. |
    | `BetweenCondition``(`[`TypedExpression`](TypedExpression.md)` baseExpression, `[`TypedExpression`](TypedExpression.md)` startExpression, `[`TypedExpression`](TypedExpression.md)` endExpression, boolean negate)`<br>Creates a new `BetweenCondition` that has the specified base, start, and end expressions.                                                 |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                       | Method and Description                                                                                                                                                                                                                  |
    |-----------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`TypedExpression`](TypedExpression.md) | `getBaseExpression``()`<br>Gets the `TypedExpression` that has the value that is the base of the condition.                                                                                                                             |
    | [`TypedExpression`](TypedExpression.md) | `getEndExpression``()`<br>Gets the `TypedExpression` that has the value that is the end of the range of values to compare to the base value.                                                                                            |
    | [`TypedExpression`](TypedExpression.md) | `getStartExpression``()`<br>Gets the `TypedExpression` that has the value that is the start of the range of values to compare to the base value.                                                                                        |
    | `boolean`                               | `isNegated``()`<br>Indicates whether this `BetweenCondition` determines that the base value is in the specified range or is not in the range.                                                                                           |
    | `java.lang.Object`                      | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitBetweenCondition` method of the `SyntaxObjectVisitor` and passes that method this `BetweenCondition` and an `Object`. |

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

    - #### BetweenCondition

          public BetweenCondition(TypedExpression baseExpression,
                                  TypedExpression startExpression,
                                  TypedExpression endExpression,
                                  boolean negate)

      Creates a new `BetweenCondition` that has the specified base, start, and end expressions. The `negate` parameter specifies whether to determine that the base value is in the range or is not in the range.
      Parameters:
      `baseExpression` - A `TypedExpression` that has the base value of the condition.

      `startExpression` - A `TypedExpression` that has the value that is the start of the range.

      `endExpression` - A `TypedExpression` that has the value that is the end of the range.

      `negate` - A `boolean` that is `true` to determine if the base value is not in the range or `false` to determine if the base value is in the range.

    <!-- -->

    - #### BetweenCondition

          public BetweenCondition(TypedExpression baseExpression,
                                  TypedExpression startExpression,
                                  TypedExpression endExpression)

      Creates a new `BetweenCondition` that has the specified base, start, and end expressions and determines whether the base value is in the range of values.
      Parameters:
      `baseExpression` - A `TypedExpression` that has the base value of the condition.

      `startExpression` - A `TypedExpression` that has the value that is the start of the range.

      `endExpression` - A `TypedExpression` that has the value that is the end of the range.

  <!-- -->

  - ### Method Detail

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitBetweenCondition` method of the `SyntaxObjectVisitor` and passes that method this `BetweenCondition` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitBetweenCondition` method.

    <!-- -->

    - #### getBaseExpression

          public TypedExpression getBaseExpression()

      Gets the `TypedExpression` that has the value that is the base of the condition.
      Returns:
      A `TypedExpression` that has the value to compare to the start and end values.

    <!-- -->

    - #### getStartExpression

          public TypedExpression getStartExpression()

      Gets the `TypedExpression` that has the value that is the start of the range of values to compare to the base value.
      Returns:
      A `TypedExpression` that has the value that is the start of the range of values.

    <!-- -->

    - #### getEndExpression

          public TypedExpression getEndExpression()

      Gets the `TypedExpression` that has the value that is the end of the range of values to compare to the base value.
      Returns:
      A `TypedExpression` that has the value that is the end of the range of values.

    <!-- -->

    - #### isNegated

          public boolean isNegated()

      Indicates whether this `BetweenCondition` determines that the base value is in the specified range or is not in the range.
      Returns:
      A `boolean` that is `true` if this `BetweenCondition` determines whether the base value is not in the range or is `false` if it determines that the base value is in the range.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](BaseQuery.md)
- [Next Class](BinaryOperatorCondition.md)

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
