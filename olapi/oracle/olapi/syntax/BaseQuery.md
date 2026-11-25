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

- [Prev Class](AssignmentCommand.md)
- [Next Class](BetweenCondition.md)

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

## Class BaseQuery

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.DataObject](DataObject.md)

    - - [oracle.olapi.syntax.Query](Query.md)

      - - oracle.olapi.syntax.BaseQuery

<!-- -->

-

  ------------------------------------------------------------------------



      public final class BaseQuery
      extends Query

  A `Query` for an object that implements the `MdmQuery` interface, such as an `MdmCube` or an `MdmPrimaryDimension`. To get a `BaseQuery`, an application calls the `getQuery` method of the `MdmQuery`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                             | Method and Description                                                                                                                                                                                                    |
    |---------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                                                     | `equals``(java.lang.Object obj)`<br>Indicates whether this `BaseQuery` is the same as the specified `BaseQuery`, which is true if both `BaseQuery` objects are associated with the same `MdmQuery`.                       |
    | [`ColumnExpression`](ColumnExpression.md)                     | `getColumnExpression``(java.lang.String colName)`<br>Gets the specified `ColumnExpression` of the `BaseQuery`..                                                                                                           |
    | `java.util.List<`[`ColumnExpression`](ColumnExpression.md)`>` | `getColumnExpressions``()`<br>Gets the `ColumnExpression` objects that are associated with the `BaseQuery`.                                                                                                               |
    | [`MdmQuery`](../metadata/mdm/MdmQuery.md)                     | `getMdmQuery``()`<br>Gets the `MdmQuery` that is associated with this `BaseQuery`.                                                                                                                                        |
    | `java.lang.String`                                            | `getMdmQueryID``()`<br>Gets the ID of the `MdmQuery` that is associated with this `BaseQuery`.                                                                                                                            |
    | `java.lang.String`                                            | `getName``()`<br>Gets the name of the `BaseQuery`, which is the name of the `MdmQuery` that is associated with this `BaseQuery`.                                                                                          |
    | `java.lang.Object`                                            | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitBaseQuery` method of the `SyntaxObjectVisitor` and passes that method this `BaseQuery` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[Query](Query.md)

      [`isFullyDimensioned`](Query.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitBaseQuery` method of the `SyntaxObjectVisitor` and passes that method this `BaseQuery` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitBaseQuery` method.

    <!-- -->

    - #### getMdmQuery

          public MdmQuery getMdmQuery()

      Gets the `MdmQuery` that is associated with this `BaseQuery`.
      Returns:
      The `MdmQuery` of this `BaseQuery`.

    <!-- -->

    - #### getMdmQueryID

          public java.lang.String getMdmQueryID()

      Gets the ID of the `MdmQuery` that is associated with this `BaseQuery`.
      Returns:
      A `String` that contains the ID of the `MdmQuery` of this `BaseQuery`.

    <!-- -->

    - #### getName

          public java.lang.String getName()

      Gets the name of the `BaseQuery`, which is the name of the `MdmQuery` that is associated with this `BaseQuery`.
      Specified by:
      [`getName`](Query.md) in class [`Query`](Query.md)

      Returns:
      A `String` that contains the name of the `BaseQuery`.

    <!-- -->

    - #### getColumnExpressions

          public java.util.List<ColumnExpression> getColumnExpressions()

      Gets the `ColumnExpression` objects that are associated with the `BaseQuery`.
      Specified by:
      [`getColumnExpressions`](Query.md) in class [`Query`](Query.md)

      Returns:
      A `List` of the `ColumnExpression` objects associated with the `BaseQuery`.

    <!-- -->

    - #### getColumnExpression

          public ColumnExpression getColumnExpression(java.lang.String colName)

      Gets the specified `ColumnExpression` of the `BaseQuery`..
      Specified by:
      [`getColumnExpression`](Query.md) in class [`Query`](Query.md)

      Parameters:
      `colName` - A `String` that contains the name of the column to get.

      Returns:
      The `ColumnExpression` with the specified name.

    <!-- -->

    - #### equals

          public boolean equals(java.lang.Object obj)

      Indicates whether this `BaseQuery` is the same as the specified `BaseQuery`, which is true if both `BaseQuery` objects are associated with the same `MdmQuery`.
      Overrides:
      `equals` in class `java.lang.Object`

      Parameters:
      `obj` - A `BaseQuery` to compare to this `BaseQuery`.

      Returns:
      A `boolean` that is `true` if this `BaseQuery` has the same `MdmQuery` as the input `BaseQuery` or is `false` otherwise.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](AssignmentCommand.md)
- [Next Class](BetweenCondition.md)

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
