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

- [Prev Class](KeywordCatalog.md)
- [Next Class](ListComparisonCondition.md)

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

## Class LikeCondition

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.DataObject](DataObject.md)

    - - [oracle.olapi.syntax.Expression](Expression.md)

      - - [oracle.olapi.syntax.Condition](Condition.md)

        - - oracle.olapi.syntax.LikeCondition

<!-- -->

- All Implemented Interfaces:
  [FunctionArgument](FunctionArgument.md)

  ------------------------------------------------------------------------



      public final class LikeCondition
      extends Condition

  A `Condition` that represents a pattern-matching condition that compares the values of `StringExpression` objects. The operators of a `LikeCondition` specify a test that can match patterns defined by special pattern-matching ("wildcard") characters.
  The left-hand-side expression of a `LikeCondition` specifies the text expression to search.

  The operator is one of the constants of the class, which are `LIKE`, `LIKEC`, `LIKE2`, and `LIKE4`.

  The right-hand-side expression specifies the pattern to search for. The pattern can contain these wildcard characters:

  - An underscore (\_), which matches exactly one character (as opposed to one byte in a multibyte character set) in the value.
  - A percent sign (%, which) can match zero or more characters (as opposed to bytes in a multibyte character set) in the value. A '%' cannot match a null.

  The escape expression is a text expression, usually a literal, that is one character long. This escape character identifies an underscore or a percent sign in the pattern as a literal character instead of a wildcard character. You can also search for the escape character itself by repeating it. For example, if @ is the escape character, then you can use @% to search for % and @@ to search for @.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                                                                  |
    |---------------------------|----------------------------------------------------------------------------------------|
    | `static java.lang.String` | `LIKE`<br>A constant for an operator that tests characters in the input character set. |
    | `static java.lang.String` | `LIKE2`<br>A constant for an operator that tests UCS2 code points.                     |
    | `static java.lang.String` | `LIKE4`<br>A constant for an operator that tests UCS4 code points.                     |
    | `static java.lang.String` | `LIKEC`<br>A constant for an operator that tests Unicode complete characters.          |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                                                                                               |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `LikeCondition``(`[`TypedExpression`](TypedExpression.md)` lhsExpression, java.lang.String operator, `[`TypedExpression`](TypedExpression.md)` rhsExpression)`<br>Creates a `LikeCondition` that has the specified left-hand-side expression, operator, and right-hand-side expression, does not have an escape character, and is not negated.                                                            |
    | `LikeCondition``(`[`TypedExpression`](TypedExpression.md)` lhsExpression, java.lang.String operator, `[`TypedExpression`](TypedExpression.md)` rhsExpression, `[`TypedExpression`](TypedExpression.md)` escapeExpression, boolean negate)`<br>Creates a `LikeCondition` that has the specified left-hand-side expression, operator, right-hand-side expression, escape character, and negation indicator. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                       | Method and Description                                                                                                                                                                                                            |
    |-----------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`TypedExpression`](TypedExpression.md) | `getEscapeExpression``()`<br>Gets the escape expression for this `LikeCondition`.                                                                                                                                                 |
    | [`TypedExpression`](TypedExpression.md) | `getLhsExpression``()`<br>Gets the expression that is the left-hand-side argument of this `LikeCondition`, which contains the text to search.                                                                                     |
    | `java.lang.String`                      | `getOperator``()`<br>Gets the operator for this `LikeCondition`, which is one of the constants of this class.                                                                                                                     |
    | [`TypedExpression`](TypedExpression.md) | `getRhsExpression``()`<br>Gets the expression that is the right-hand-side argument of this `LikeCondition`, which contains the text pattern to search for.                                                                        |
    | `boolean`                               | `isNegated``()`<br>Indicates whether this `LikeCondition` includes the `NOT` operator.                                                                                                                                            |
    | `java.lang.Object`                      | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitLikeCondition` method of the `SyntaxObjectVisitor` and passes that method this `LikeCondition` and an `Object`. |

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

    - #### LIKE

          public static final java.lang.String LIKE

      A constant for an operator that tests characters in the input character set.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### LIKEC

          public static final java.lang.String LIKEC

      A constant for an operator that tests Unicode complete characters. It treats a Unicode supplementary character as two characters.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### LIKE2

          public static final java.lang.String LIKE2

      A constant for an operator that tests UCS2 code points. It treats a Unicode supplementary character as one character.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### LIKE4

          public static final java.lang.String LIKE4

      A constant for an operator that tests UCS4 code points. It treats a composite character as one character.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### LikeCondition

          public LikeCondition(TypedExpression lhsExpression,
                               java.lang.String operator,
                               TypedExpression rhsExpression,
                               TypedExpression escapeExpression,
                               boolean negate)

      Creates a `LikeCondition` that has the specified left-hand-side expression, operator, right-hand-side expression, escape character, and negation indicator.
      Parameters:
      `lhsExpression` - A `TypedExpression` that has the text expression for the search value.

      `operator` - A `LikeCondition` constant that specifies the opeator for the condition test.

      `rhsExpression` - A `TypedExpression` that has the text expression for the pattern.

      `escapeExpression` - A `TypedExpression` that has the text expression to use as the escape character.

      `negate` - A `boolean` that if `true` adds `NOT` to the operator or if `false` does not add `NOT` to the operator.

    <!-- -->

    - #### LikeCondition

          public LikeCondition(TypedExpression lhsExpression,
                               java.lang.String operator,
                               TypedExpression rhsExpression)

      Creates a `LikeCondition` that has the specified left-hand-side expression, operator, and right-hand-side expression, does not have an escape character, and is not negated. For a `LikeCondition` created by this constructor, the `getEscapeExpression` method returns `null` and the `isNegated` method returns `false`.
      Parameters:
      `lhsExpression` - A `TypedExpression` that has the text expression for the search value.

      `operator` - A `LikeCondition` constant that specifies the opeator for the condition test.

      `rhsExpression` - A `TypedExpression` that has the text expression for the pattern.

  <!-- -->

  - ### Method Detail

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitLikeCondition` method of the `SyntaxObjectVisitor` and passes that method this `LikeCondition` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitLikeCondition` method.

    <!-- -->

    - #### isNegated

          public boolean isNegated()

      Indicates whether this `LikeCondition` includes the `NOT` operator.
      Returns:
      A `boolean` that is `true` if this `LikeCondition` includes the `NOT` operator or `false` if it does not.

    <!-- -->

    - #### getOperator

          public java.lang.String getOperator()

      Gets the operator for this `LikeCondition`, which is one of the constants of this class.
      Returns:
      A `String` that contains the operator for this `LikeCondition`.

    <!-- -->

    - #### getEscapeExpression

          public TypedExpression getEscapeExpression()

      Gets the escape expression for this `LikeCondition`.
      Returns:
      A `String` that contains the escape expression for this `LikeCondition`.

    <!-- -->

    - #### getLhsExpression

          public TypedExpression getLhsExpression()

      Gets the expression that is the left-hand-side argument of this `LikeCondition`, which contains the text to search.
      Returns:
      A `TypedExpression` that is the left-hand-side argument of this `LikeCondition`.

    <!-- -->

    - #### getRhsExpression

          public TypedExpression getRhsExpression()

      Gets the expression that is the right-hand-side argument of this `LikeCondition`, which contains the text pattern to search for.
      Returns:
      A `TypedExpression` that is the right-hand-side argument of this `LikeCondition`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](KeywordCatalog.md)
- [Next Class](ListComparisonCondition.md)

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
