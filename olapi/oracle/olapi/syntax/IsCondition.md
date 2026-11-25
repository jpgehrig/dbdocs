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

- [Prev Class](IntervalLiteralExpression.md)
- [Next Class](KeywordArgument.md)

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

## Class IsCondition

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.DataObject](DataObject.md)

    - - [oracle.olapi.syntax.Expression](Expression.md)

      - - [oracle.olapi.syntax.Condition](Condition.md)

        - - oracle.olapi.syntax.IsCondition

<!-- -->

- All Implemented Interfaces:
  [FunctionArgument](FunctionArgument.md)

  ------------------------------------------------------------------------



      public final class IsCondition
      extends Condition

  A `Condition` that represents a special condition. An `IsCondition` determines whether an expression evaluates to `null` or to the special values `INFINITE` or `NAN` (not a number), which is the undefined result of an operation. The `INFINITE` and `NAN` conditions are the SQL floating-point conditions.
  An `IsCondition` has the following associations:

  - A base expression to test against the condition.
  - A comparison value which is one of the constants of the class: `IS_INFINITE`, `IS_NAN`, `IS_NULL`.
  - A `boolean` value that specifies whether to apply the `NOT` operator to the comparison. This value is returned by the `isNegated` method.

  The following table lists the possible combinations of comparison values and negation values, describes the results of operation that the comparison performs, and provides an example of the syntax for the condition. In the syntax, the value of the base expression is `'comm_pct'`. If you passed the syntax to the `SyntaxObject.fromSyntax` method, then the method would return an `IsCondition` object that specifies the operation described.

  An example of creating an `IsCondition` from a syntax example is the following, where `metadataProvider` is an `MdmMetadataProvider`:

       IsCondition ic = (IsCondition) SyntaxObject.fromSyntax("'com_pct' IS NAN",
                                                               metadataProvider);

  | Type of Comparison | `isNegated`<br>Value | Operation Result                                                                                      | Syntax Example              |
  |--------------------|----------------------|-------------------------------------------------------------------------------------------------------|-----------------------------|
  | `IS_INFINITE`      | `false`              | Evaluates to `true` if the base expression is the special infinite value or to `false` it is not.     | `'com_pct' IS INFINITE`     |
  | `IS_INFINITE`      | `true`               | Evaluates to `true` if the base expression is not the special infinite value or to `false` it is.     | `'com_pct' IS NOT INFINITE` |
  | `IS_NAN`           | `false`              | Evaluates to `true` if the base expression is the special not-a-number value or to `false` it is not. | `'com_pct' IS NAN`          |
  | `IS_NAN`           | `true`               | Evaluates to `true` if the base expression is not the special not-a-number value or to `false` it is. | `'com_pct' IS NOT NAN`      |
  | `IS_NULL`          | `false`              | Evaluates to `true` if the base expression is `null` or to `false` it is not.                         | `'com_pct' IS NULL`         |
  | `IS_NULL`          | `true`               | Evaluates to `true` if the base expression is not `null` or to `false` it is.                         | `'com_pct' IS NOT NULL`     |

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                                                                 |
    |---------------------------|---------------------------------------------------------------------------------------|
    | `static java.lang.String` | `IS_INFINITE`<br>A constant for an operator that tests whether the value is infinite. |
    | `static java.lang.String` | `IS_NAN`<br>A constant for an operator that tests whether the value is not a number.  |
    | `static java.lang.String` | `IS_NULL`<br>A constant for an operator that tests whether the value is `null`.       |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `IsCondition``(`[`TypedExpression`](TypedExpression.md)` argument)`<br>Creates an `IsCondition` that has the specified argument, has a comparison type of `IS_NULL`, and does not include the `NOT` operator.              |
    | `IsCondition``(`[`TypedExpression`](TypedExpression.md)` argument, boolean negate)`<br>Creates an `IsCondition` that has the specified argument and negation indicator, and has a comparison type of `IS_NULL`.            |
    | `IsCondition``(`[`TypedExpression`](TypedExpression.md)` argument, java.lang.String comparisonType, boolean negate)`<br>Creates an `IsCondition` that has the specified argument, comparison type, and negation indicator. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                       | Method and Description                                                                                                                                                                                                        |
    |-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`TypedExpression`](TypedExpression.md) | `getBaseExpression``()`<br>Gets the expression that is the basis of the condition determination.                                                                                                                              |
    | `java.lang.String`                      | `getComparison``()`<br>Gets the comparison type, which can be one of the `IsCondition` constants.                                                                                                                             |
    | `boolean`                               | `isNegated``()`<br>Indicates whether this `IsCondition` includes the `NOT` operator.                                                                                                                                          |
    | `java.lang.Object`                      | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitIsCondition` method of the `SyntaxObjectVisitor` and passes that method this `IsCondition` and an `Object`. |

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

    - #### IS_NULL

          public static final java.lang.String IS_NULL

      A constant for an operator that tests whether the value is `null`.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### IS_NAN

          public static final java.lang.String IS_NAN

      A constant for an operator that tests whether the value is not a number.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### IS_INFINITE

          public static final java.lang.String IS_INFINITE

      A constant for an operator that tests whether the value is infinite.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### IsCondition

          public IsCondition(TypedExpression argument,
                             java.lang.String comparisonType,
                             boolean negate)

      Creates an `IsCondition` that has the specified argument, comparison type, and negation indicator.
      Parameters:
      `argument` - A `TypedExpression` that has the value to compare.

      `comparisonType` - A `String` that specifies the comparison type, which can be one of the `IsCondition` constants.

      `negate` - A `boolean` that specifies whether to include the `NOT` operator in the condition.

    <!-- -->

    - #### IsCondition

          public IsCondition(TypedExpression argument,
                             boolean negate)

      Creates an `IsCondition` that has the specified argument and negation indicator, and has a comparison type of `IS_NULL`.
      Parameters:
      `argument` - A `TypedExpression` that has the value to compare.

      `negate` - A `boolean` that specifies whether to include the `NOT` operator in the condition.

    <!-- -->

    - #### IsCondition

          public IsCondition(TypedExpression argument)

      Creates an `IsCondition` that has the specified argument, has a comparison type of `IS_NULL`, and does not include the `NOT` operator.
      Parameters:
      `argument` - A `TypedExpression` that has the value to compare.

  <!-- -->

  - ### Method Detail

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitIsCondition` method of the `SyntaxObjectVisitor` and passes that method this `IsCondition` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitIsCondition` method.

    <!-- -->

    - #### getComparison

          public java.lang.String getComparison()

      Gets the comparison type, which can be one of the `IsCondition` constants.
      Returns:
      A `String` that has the comparison type.

    <!-- -->

    - #### isNegated

          public boolean isNegated()

      Indicates whether this `IsCondition` includes the `NOT` operator.
      Returns:
      A `boolean` that is `true` if this `IsCondition` includes the `NOT` operator or `false` if it does not.

    <!-- -->

    - #### getBaseExpression

          public TypedExpression getBaseExpression()

      Gets the expression that is the basis of the condition determination.
      Returns:
      A `TypedExpression` that has the value that is the basis of the test of the condition.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](IntervalLiteralExpression.md)
- [Next Class](KeywordArgument.md)

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
