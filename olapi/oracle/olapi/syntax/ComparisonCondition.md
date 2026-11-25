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

- [Prev Class](ColumnExpression.md)
- [Next Class](CompileCommand.md)

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

## Class ComparisonCondition

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.DataObject](DataObject.md)

    - - [oracle.olapi.syntax.Expression](Expression.md)

      - - [oracle.olapi.syntax.Condition](Condition.md)

        - - oracle.olapi.syntax.ComparisonCondition

<!-- -->

- All Implemented Interfaces:
  [FunctionArgument](FunctionArgument.md)

  <!-- -->

  Direct Known Subclasses:
  [ListComparisonCondition](ListComparisonCondition.md), [ValueComparisonCondition](ValueComparisonCondition.md)

  ------------------------------------------------------------------------



      public abstract class ComparisonCondition
      extends Condition

  An abstract base class for a `Condition` that represents a comparison condition, which compares one expression to another expression or to a list of expressions. A `ComparisonCondition` evaluates to `true`, `false`, or `null`.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                                           |
    |---------------------------|-----------------------------------------------------------------|
    | `static java.lang.String` | `EQ`<br>A constant for the equal-to operator.                   |
    | `static java.lang.String` | `GE`<br>A constant for the greater-than-or-equal-to operator.   |
    | `static java.lang.String` | `GT`<br>A constant for the greater-than operator.               |
    | `static java.lang.String` | `LE`<br>A constant for the less-than-or-equal-to operator.      |
    | `static java.lang.String` | `LT`<br>A constant for the less-than operator.                  |
    | `static java.lang.String` | `NE`<br>A constant for the not-equals operator.                 |
    | `static java.lang.String` | `NE2`<br>A constant for the less-than-or-greater-than operator. |
    | `static java.lang.String` | `NE3`<br>A constant for the carot-equals operator.              |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                       | Method and Description                                                                                        |
    |-----------------------------------------|---------------------------------------------------------------------------------------------------------------|
    | [`TypedExpression`](TypedExpression.md) | `getLhsArgument``()`<br>Gets the expression that is the left-hand-side argument of this `ComprisonCondition`. |
    | `java.lang.String`                      | `getOperator``()`<br>Gets the operator for this `ComparisonCondition`.                                        |

    - ### Methods inherited from class oracle.olapi.syntax.[Condition](Condition.md)

      [`and`](Condition.md)`, `[`isCompositeObject`](Condition.md)`, `[`not`](Condition.md)`, `[`or`](Condition.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`visit`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### LT

          public static final java.lang.String LT

      A constant for the less-than operator.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### LE

          public static final java.lang.String LE

      A constant for the less-than-or-equal-to operator.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GT

          public static final java.lang.String GT

      A constant for the greater-than operator.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### GE

          public static final java.lang.String GE

      A constant for the greater-than-or-equal-to operator.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### EQ

          public static final java.lang.String EQ

      A constant for the equal-to operator.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### NE

          public static final java.lang.String NE

      A constant for the not-equals operator.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### NE2

          public static final java.lang.String NE2

      A constant for the less-than-or-greater-than operator.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### NE3

          public static final java.lang.String NE3

      A constant for the carot-equals operator.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getOperator

          public java.lang.String getOperator()

      Gets the operator for this `ComparisonCondition`. The constant fields of this class, such as `LT` and `EQ`, represent the operators.
      Returns:
      A `String` that contains the operator for this `ComparisonCondition`.

    <!-- -->

    - #### getLhsArgument

          public TypedExpression getLhsArgument()

      Gets the expression that is the left-hand-side argument of this `ComprisonCondition`.
      Returns:
      A `TypedExpression` that is the left-hand-side argument of this `ComprisonCondition`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](ColumnExpression.md)
- [Next Class](CompileCommand.md)

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
