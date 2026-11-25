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

- [Prev Class](SearchedCaseExpression.md)
- [Next Class](SimpleCaseExpression.md)

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

## Class SimpleCase

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.DataObject](DataObject.md)

    - - oracle.olapi.syntax.SimpleCase

<!-- -->

-

  ------------------------------------------------------------------------



      public final class SimpleCase
      extends DataObject

  A `DataObject` that contains a pair of `WHEN` and `THEN` expressions for a [`SimpleCaseExpression`](SimpleCaseExpression.md).

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                        |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `SimpleCase``(int when, `[`TypedExpression`](TypedExpression.md)` thenExpression)`<br>Creates a `SimpleCase` that has the specified `WHEN` and `THEN` expressions.                                                 |
    | `SimpleCase``(java.lang.String when, `[`TypedExpression`](TypedExpression.md)` thenExpression)`<br>Creates a `SimpleCase` that has the specified `WHEN` and `THEN` expressions.                                    |
    | `SimpleCase``(`[`TypedExpression`](TypedExpression.md)` whenExpression, `[`TypedExpression`](TypedExpression.md)` thenExpression)`<br>Creates a `SimpleCase` that has the specified `WHEN` and `THEN` expressions. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                       | Method and Description                                                                                                                                                                                                      |
    |-----------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`TypedExpression`](TypedExpression.md) | `getThenExpression``()`<br>Gets the `TypedExpression` that resolves to the `THEN` expression of this `SimpleCase`.                                                                                                          |
    | [`TypedExpression`](TypedExpression.md) | `getWhenExpression``()`<br>Gets the `TypedExpression` that resolves to the `WHEN` expression of this `SimpleCase`.                                                                                                          |
    | `boolean`                               | `isCompositeObject``()`<br>Indicates whether this `SimpleCase` contains other `SyntaxObject` objects.                                                                                                                       |
    | `java.lang.Object`                      | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitSimpleCase` method of the `SyntaxObjectVisitor` and passes that method this `SimpleCase` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### SimpleCase

          public SimpleCase(TypedExpression whenExpression,
                            TypedExpression thenExpression)

      Creates a `SimpleCase` that has the specified `WHEN` and `THEN` expressions.
      Parameters:
      `whenExpression` - A `TypedExpression` that resolves to a `WHEN` expression for a simple case expression clause of a `CASE` expression.

      `thenExpression` - A `TypedExpression` that resolves to a `THEN` expression for a simple case expression clause of a `CASE` expression.

    <!-- -->

    - #### SimpleCase

          public SimpleCase(int when,
                            TypedExpression thenExpression)

      Creates a `SimpleCase` that has the specified `WHEN` and `THEN` expressions.
      Parameters:
      `when` - An integer to use as the `WHEN` expression for a simple case expression clause of a `CASE` expression.

      `thenExpression` - A `TypedExpression` that resolves to a `THEN` expression for a simple case expression clause of a `CASE` expression.

    <!-- -->

    - #### SimpleCase

          public SimpleCase(java.lang.String when,
                            TypedExpression thenExpression)

      Creates a `SimpleCase` that has the specified `WHEN` and `THEN` expressions.
      Parameters:
      `when` - A `String` to use as the `WHEN` expression for a simple case expression clause of a `CASE` expression.

      `thenExpression` - A `TypedExpression` that resolves to a `THEN` expression for a simple case expression clause of a `CASE` expression.

  <!-- -->

  - ### Method Detail

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitSimpleCase` method of the `SyntaxObjectVisitor` and passes that method this `SimpleCase` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitSimpleCase` method.

    <!-- -->

    - #### getWhenExpression

          public TypedExpression getWhenExpression()

      Gets the `TypedExpression` that resolves to the `WHEN` expression of this `SimpleCase`.
      Returns:
      A `TypedExpression` that represents the `WHEN` expression of a simple case expression clause of a `Case` expression.

    <!-- -->

    - #### getThenExpression

          public TypedExpression getThenExpression()

      Gets the `TypedExpression` that resolves to the `THEN` expression of this `SimpleCase`.
      Returns:
      A `TypedExpression` that represents the `THEN` expression of a simple case expression clause of a `Case` expression.

    <!-- -->

    - #### isCompositeObject

          public boolean isCompositeObject()

      Indicates whether this `SimpleCase` contains other `SyntaxObject` objects. Because a `SimpleCase` has at least one `TypedExpression`, which is a `SyntaxObject`, this method returns `true`.
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

- [Prev Class](SearchedCaseExpression.md)
- [Next Class](SimpleCaseExpression.md)

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
