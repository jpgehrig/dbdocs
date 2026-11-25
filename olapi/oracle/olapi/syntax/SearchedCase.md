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

- [Prev Class](RowFunctionExpression.md)
- [Next Class](SearchedCaseExpression.md)

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

## Class SearchedCase

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.DataObject](DataObject.md)

    - - oracle.olapi.syntax.SearchedCase

<!-- -->

-

  ------------------------------------------------------------------------



      public final class SearchedCase
      extends DataObject

  A `DataObject` that contains a `WHEN` condition and a `THEN` expression for a [`SearchedCaseExpression`](SearchedCaseExpression.md).

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                        |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `SearchedCase``(`[`Condition`](Condition.md)` whenCondition, `[`TypedExpression`](TypedExpression.md)` thenExpression)`<br>Creates a `SearchedCase` that has the specified `WHEN` condition and `THEN` expression. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                       | Method and Description                                                                                                                                                                                                          |
    |-----------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`TypedExpression`](TypedExpression.md) | `getThenExpression``()`<br>Gets the `TypedExpression` that resolves to the `THEN` expression of this `SearchedCase`.                                                                                                            |
    | [`Condition`](Condition.md)             | `getWhenCondition``()`<br>Gets the `Condition` that resolves to the `WHEN` condition of this `SearchedCase`.                                                                                                                    |
    | `boolean`                               | `isCompositeObject``()`<br>Indicates whether this `SearchedCase` contains other `SyntaxObject` objects.                                                                                                                         |
    | `java.lang.Object`                      | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitSearchedCase` method of the `SyntaxObjectVisitor` and passes that method this `SearchedCase` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### SearchedCase

          public SearchedCase(Condition whenCondition,
                              TypedExpression thenExpression)

      Creates a `SearchedCase` that has the specified `WHEN` condition and `THEN` expression.
      Parameters:
      `whenCondition` - A `Condition` that resolves to a condition for a searched case expression clause of a `CASE` expression.

      `thenExpression` - A `TypedExpression` that resolves to a `THEN` expression for a searched case expression clause of a `CASE` expression.

  <!-- -->

  - ### Method Detail

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitSearchedCase` method of the `SyntaxObjectVisitor` and passes that method this `SearchedCase` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitSearchedCase` method.

    <!-- -->

    - #### getWhenCondition

          public Condition getWhenCondition()

      Gets the `Condition` that resolves to the `WHEN` condition of this `SearchedCase`.
      Returns:
      A `Condition` that represents the `WHEN` condition of a searched case expression clause of a `Case` expression.

    <!-- -->

    - #### getThenExpression

          public TypedExpression getThenExpression()

      Gets the `TypedExpression` that resolves to the `THEN` expression of this `SearchedCase`.
      Returns:
      A `TypedExpression` that represents the `THEN` expression of a searched case expression clause of a `Case` expression.

    <!-- -->

    - #### isCompositeObject

          public boolean isCompositeObject()

      Indicates whether this `SearchedCase` contains other `SyntaxObject` objects. Because a `SearchedCase` has a `Condition` and a `TypedExpression`, which are `SyntaxObject` objects, this method returns `true`.
      Returns:
      A `boolean` that is `true`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](RowFunctionExpression.md)
- [Next Class](SearchedCaseExpression.md)

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
