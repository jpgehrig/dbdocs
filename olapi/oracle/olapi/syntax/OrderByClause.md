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

- [Prev Class](OLAPFunctionExpression.md)
- [Next Class](OrderByElement.md)

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

## Class OrderByClause

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.DataObject](DataObject.md)

    - - oracle.olapi.syntax.OrderByClause

<!-- -->

-

  ------------------------------------------------------------------------



      public final class OrderByClause
      extends DataObject

  A `DataObject` that represents an ordering of the results of the evaluation of an `Expression`. An `OrderByClause` is similar to the `ORDER BY` clause of a SQL `SELECT` statement. The `OrderByElement` objects of an `OrderByClause` specify the order.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                      |
    |--------------------------------------------------------------------------------------------------------------------------------------------------|
    | `OrderByClause``(java.util.List<`[`OrderByElement`](OrderByElement.md)`> elements)`                                                              |
    | `OrderByClause``(`[`OrderByElement`](OrderByElement.md)`[] elements)`<br>Creates an `OrderByClause` with the specified `OrderByElement` objects. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                         | Method and Description                                                                                                                                                                                                            |
    |-------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`OrderByElement`](OrderByElement.md)`[]` | `getElements``()`<br>Gets the elements of this `OrderByClause`, which specify the ordering of the results.                                                                                                                        |
    | `boolean`                                 | `isCompositeObject``()`<br>Indicates whether this `OrderByClause` contains other `SyntaxObject` objects.                                                                                                                          |
    | `java.lang.Object`                        | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitOrderByClause` method of the `SyntaxObjectVisitor` and passes that method this `OrderByClause` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### OrderByClause

          public OrderByClause(OrderByElement[] elements)

      Creates an `OrderByClause` with the specified `OrderByElement` objects.
      Parameters:
      `elements` - An array of `OrderByElement` objects that specify the ordering sequence.

    <!-- -->

    - #### OrderByClause

          public OrderByClause(java.util.List<OrderByElement> elements)

  <!-- -->

  - ### Method Detail

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitOrderByClause` method of the `SyntaxObjectVisitor` and passes that method this `OrderByClause` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitOrderByClause` method.

    <!-- -->

    - #### getElements

          public OrderByElement[] getElements()

      Gets the elements of this `OrderByClause`, which specify the ordering of the results.
      Returns:
      An array of `OrderByElement` objects that specify the ordering sequence.

    <!-- -->

    - #### isCompositeObject

          public boolean isCompositeObject()

      Indicates whether this `OrderByClause` contains other `SyntaxObject` objects. Because an `OrderByClause` contains one or more `OrderByElement` objects, this method returns `true`.
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

- [Prev Class](OLAPFunctionExpression.md)
- [Next Class](OrderByElement.md)

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
