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

- [Prev Class](OrderByClause.md)
- [Next Class](PlaceholderExpression.md)

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

## Class OrderByElement

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.DataObject](DataObject.md)

    - - oracle.olapi.syntax.OrderByElement

<!-- -->

-

  ------------------------------------------------------------------------



      public final class OrderByElement
      extends DataObject

  A `DataObject` that represents an expression of an `OrderByClause`.
  See Also:
  [`OrderByClause`](OrderByClause.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                       |
    |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `OrderByElement``(`[`TypedExpression`](TypedExpression.md)` expression, boolean ascending, boolean nullsFirst)`<br>Creates an `OrderByElement` with the specified expression and characteristics. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                       | Method and Description                                                                                                                                                                                                              |
    |-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`TypedExpression`](TypedExpression.md) | `getExpression``()`<br>Gets the expression of this `OrderByElement`.                                                                                                                                                                |
    | `boolean`                               | `isAscending``()`<br>Indicates whether the ordering sequence is ascending.                                                                                                                                                          |
    | `boolean`                               | `isCompositeObject``()`<br>Indicates whether this `OrderByElement` contains other `SyntaxObject` objects.                                                                                                                           |
    | `boolean`                               | `isDescending``()`<br>Indicates whether the ordering sequence is descending.                                                                                                                                                        |
    | `boolean`                               | `isNullsFirst``()`<br>Indicates whether returned rows containing null values should appear first in the ordering sequence.                                                                                                          |
    | `boolean`                               | `isNullsLast``()`<br>Indicates whether returned rows containing null values should appear last in the ordering sequence.                                                                                                            |
    | `java.lang.Object`                      | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitOrderByElement` method of the `SyntaxObjectVisitor` and passes that method this `OrderByElement` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### OrderByElement

          public OrderByElement(TypedExpression expression,
                                boolean ascending,
                                boolean nullsFirst)

      Creates an `OrderByElement` with the specified expression and characteristics.
      Parameters:
      `expression` - A `TypedExpression` that represents an expression of an `OrderByClause`.

      `ascending` - A `boolean` that is `true` if the sequence of the results for the expression should be in ascending order or `false` if they should be in descending order.

      `nullsFirst` - A `boolean` that is `true` if `null` values should appear first in the sequence of the results for the expression or `false` if they should appear last.

  <!-- -->

  - ### Method Detail

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitOrderByElement` method of the `SyntaxObjectVisitor` and passes that method this `OrderByElement` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitOrderByElement` method.

    <!-- -->

    - #### getExpression

          public TypedExpression getExpression()

      Gets the expression of this `OrderByElement`.
      Returns:
      A `TypedExpression` that evaluates to an expression of a SQL `ORDER BY` clause.

    <!-- -->

    - #### isAscending

          public boolean isAscending()

      Indicates whether the ordering sequence is ascending.
      Returns:
      A `boolean` that is `true` is the ordering sequence is ascending or `false` if it is not.

    <!-- -->

    - #### isDescending

          public boolean isDescending()

      Indicates whether the ordering sequence is descending.
      Returns:
      A `boolean` that is `true` is the ordering sequence is descending or `false` if it is not.

    <!-- -->

    - #### isNullsFirst

          public boolean isNullsFirst()

      Indicates whether returned rows containing null values should appear first in the ordering sequence.
      Returns:
      A `boolean` that is `true` if `null` values should appear first in the ordering sequence or `false` if they should not.

    <!-- -->

    - #### isNullsLast

          public boolean isNullsLast()

      Indicates whether returned rows containing null values should appear last in the ordering sequence.
      Returns:
      A `boolean` that is `true` if `null` values should appear last in the ordering sequence or `false` if they should not.

    <!-- -->

    - #### isCompositeObject

          public boolean isCompositeObject()

      Indicates whether this `OrderByElement` contains other `SyntaxObject` objects. Because an `OrderByElement` contains a `TypedExpression`, this method returns `true`.
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

- [Prev Class](OrderByClause.md)
- [Next Class](PlaceholderExpression.md)

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
