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

- [Prev Class](LikeCondition.md)
- [Next Class](LiteralExpression.md)

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

## Class ListComparisonCondition

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.DataObject](DataObject.md)

    - - [oracle.olapi.syntax.Expression](Expression.md)

      - - [oracle.olapi.syntax.Condition](Condition.md)

        - - [oracle.olapi.syntax.ComparisonCondition](ComparisonCondition.md)

          - - oracle.olapi.syntax.ListComparisonCondition

<!-- -->

- All Implemented Interfaces:
  [FunctionArgument](FunctionArgument.md)

  ------------------------------------------------------------------------



      public final class ListComparisonCondition
      extends ComparisonCondition

  A `ComparisonCondition` that represents a group comparison condition, which compares one expression to a list of expressions. The operator for a `ListComparisonCondition` is any of the `ComparisonCondition` constants. That operator is qualified by one of the `ListComparisonCondition` constants, `ALL`, `ANY`, or `SOME`.
  A `ListComparisonCondition` with the `ANY` or `SOME` qualifier evaluates to `true` if the value of the left-hand-side expression matches the value of one or more expressions in the right-hand-side list of expressions. A `ListComparisonCondition` with the `ALL` qualifier evaluates to `true` if the value of the left-hand-side expression matches the values of all of the expressions in the list of expressions.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                       |
    |---------------------------|---------------------------------------------|
    | `static java.lang.String` | `ALL`<br>A constant for the ALL operator.   |
    | `static java.lang.String` | `ANY`<br>A constant for the ANY operator.   |
    | `static java.lang.String` | `SOME`<br>A constant for the SOME operator. |

    - ### Fields inherited from class oracle.olapi.syntax.[ComparisonCondition](ComparisonCondition.md)

      [`EQ`](ComparisonCondition.md)`, `[`GE`](ComparisonCondition.md)`, `[`GT`](ComparisonCondition.md)`, `[`LE`](ComparisonCondition.md)`, `[`LT`](ComparisonCondition.md)`, `[`NE`](ComparisonCondition.md)`, `[`NE2`](ComparisonCondition.md)`, `[`NE3`](ComparisonCondition.md)

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                                                         |
    |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `ListComparisonCondition``(`[`TypedExpression`](TypedExpression.md)` lhs, java.lang.String operator, java.lang.String qualifier, java.util.List<`[`TypedExpression`](TypedExpression.md)`> list)`<br>Creates a new `ListComparisonCondition` that has the specified left-hand-side argument expression, operator, qualifier, and list of `TypedExpression` objects. |
    | `ListComparisonCondition``(`[`TypedExpression`](TypedExpression.md)` lhs, java.lang.String operator, java.lang.String qualifier, `[`TypedExpression`](TypedExpression.md)`[] list)`<br>Creates a new `ListComparisonCondition` that has the specified left-hand-side argument expression, operator, qualifier, and list of `TypedExpression` objects.               |
    | `ListComparisonCondition``(`[`TypedExpression`](TypedExpression.md)` lhs, java.lang.String operator, `[`TypedExpression`](TypedExpression.md)`[] list)`<br>Creates a new `ListComparisonCondition` that has the specified left-hand-side argument expression, operator, and list of `TypedExpression` objects, and has the `ANY` qualifier.                         |
    | `ListComparisonCondition``(`[`TypedExpression`](TypedExpression.md)` lhs, `[`TypedExpression`](TypedExpression.md)`[] list)`<br>Creates a new `ListComparisonCondition` that has the specified left-hand-side argument expression and list of `TypedExpression` objects, and has the `EQ` operator and the `ANY` qualifier.                                         |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                           | Method and Description                                                                                                                                                                                                                                |
    |---------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`TypedExpression`](TypedExpression.md)`[]` | `getList``()`<br>Gets the list of expressions of this `ListComprisonCondition` that the operation compares to the left-hand-side argument expression.                                                                                                 |
    | `java.lang.String`                          | `getQualifier``()`<br>Gets the qualifier of this `ListComprisonCondition`, which can be `ALL`, `ANY`, or `SOME`.                                                                                                                                      |
    | `java.lang.Object`                          | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitListComparisonCondition` method of the `SyntaxObjectVisitor` and passes that method this `ListComparisonCondition` and an `Object`. |

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

- - ### Field Detail

    - #### ALL

          public static final java.lang.String ALL

      A constant for the ALL operator.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SOME

          public static final java.lang.String SOME

      A constant for the SOME operator.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ANY

          public static final java.lang.String ANY

      A constant for the ANY operator.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### ListComparisonCondition

          public ListComparisonCondition(TypedExpression lhs,
                                         java.lang.String operator,
                                         java.lang.String qualifier,
                                         TypedExpression[] list)

      Creates a new `ListComparisonCondition` that has the specified left-hand-side argument expression, operator, qualifier, and list of `TypedExpression` objects.
      Parameters:
      `lhs` - The `TypedExpression` to use as the left-hand-side argument.

      `operator` - The operator to use, which can be any of the `ComparisonCondition` constants.

      `qualifier` - One of the `ListComparisonCondition` constants `ALL`, `ANY`, or `SOME`.

      `list` - An array of `TypedExpression` objects.

    <!-- -->

    - #### ListComparisonCondition

          public ListComparisonCondition(TypedExpression lhs,
                                         java.lang.String operator,
                                         java.lang.String qualifier,
                                         java.util.List<TypedExpression> list)

      Creates a new `ListComparisonCondition` that has the specified left-hand-side argument expression, operator, qualifier, and list of `TypedExpression` objects.
      Parameters:
      `lhs` - The `TypedExpression` to use as the left-hand-side argument.

      `operator` - The operator to use, which can be any of the `ComparisonCondition` constants.

      `qualifier` - One of the `ListComparisonCondition` constants `ALL`, `ANY`, or `SOME`.

      `list` - A `List` of `TypedExpression` objects.

    <!-- -->

    - #### ListComparisonCondition

          public ListComparisonCondition(TypedExpression lhs,
                                         java.lang.String operator,
                                         TypedExpression[] list)

      Creates a new `ListComparisonCondition` that has the specified left-hand-side argument expression, operator, and list of `TypedExpression` objects, and has the `ANY` qualifier.
      Parameters:
      `lhs` - The `TypedExpression` to use as the left-hand-side argument.

      `operator` - The operator to use, which can be any of the `ComparisonCondition` constants.

      `list` - An array of `TypedExpression` objects.

    <!-- -->

    - #### ListComparisonCondition

          public ListComparisonCondition(TypedExpression lhs,
                                         TypedExpression[] list)

      Creates a new `ListComparisonCondition` that has the specified left-hand-side argument expression and list of `TypedExpression` objects, and has the `EQ` operator and the `ANY` qualifier.
      Parameters:
      `lhs` - The `TypedExpression` to use as the left-hand-side argument.

      `list` - An array of `TypedExpression` objects.

  <!-- -->

  - ### Method Detail

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitListComparisonCondition` method of the `SyntaxObjectVisitor` and passes that method this `ListComparisonCondition` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitListComparisonCondition` method.

    <!-- -->

    - #### getList

          public TypedExpression[] getList()

      Gets the list of expressions of this `ListComprisonCondition` that the operation compares to the left-hand-side argument expression.
      Returns:
      An array of `TypedExpression` objects.

    <!-- -->

    - #### getQualifier

          public java.lang.String getQualifier()

      Gets the qualifier of this `ListComprisonCondition`, which can be `ALL`, `ANY`, or `SOME`.
      Returns:
      A `String` that contains the qualifier of this `ListComprisonCondition`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](LikeCondition.md)
- [Next Class](LiteralExpression.md)

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
