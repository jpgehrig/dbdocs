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

- [Prev Class](Qualifier.md)
- [Next Class](RowExpression.md)

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

## Class Query

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.DataObject](DataObject.md)

    - - oracle.olapi.syntax.Query

<!-- -->

- Direct Known Subclasses:
  [BaseQuery](BaseQuery.md), [UnresolvedQuery](UnresolvedQuery.md)

  ------------------------------------------------------------------------



      public abstract class Query
      extends DataObject

  A `DataObject` that represents a multirow, multicolumn result set that is similar to a relational table, a SQL `SELECT` statement, or an OLAP function.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                      | Method and Description                                                                                     |
    |------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
    | `abstract `[`ColumnExpression`](ColumnExpression.md)                   | `getColumnExpression``(java.lang.String colName)`<br>Gets the specified `ColumnExpression` of the `Query`. |
    | `abstract java.util.List<`[`ColumnExpression`](ColumnExpression.md)`>` | `getColumnExpressions``()`<br>Gets the `ColumnExpression` objects that are associated with the `Query`.    |
    | `abstract java.lang.String`                                            | `getName``()`<br>Gets the name of the `Query`.                                                             |
    | `boolean`                                                              | `isFullyDimensioned``()`<br>Indicates whether the `Query` is fully dimensioned.                            |

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`visit`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getName

          public abstract java.lang.String getName()

      Gets the name of the `Query`.
      Returns:
      A `String` that contains the name of the `Query`.

    <!-- -->

    - #### isFullyDimensioned

          public boolean isFullyDimensioned()

      Indicates whether the `Query` is fully dimensioned.
      Returns:
      A `boolean` that is `true` if the `Query` is fully dimensioned or `false` if it is not.

    <!-- -->

    - #### getColumnExpressions

          public abstract java.util.List<ColumnExpression> getColumnExpressions()

      Gets the `ColumnExpression` objects that are associated with the `Query`.
      Returns:
      A `List` of the `ColumnExpression` objects associated with the `Query`.

    <!-- -->

    - #### getColumnExpression

          public abstract ColumnExpression getColumnExpression(java.lang.String colName)

      Gets the specified `ColumnExpression` of the `Query`.
      Parameters:
      `colName` - A `String` that contains the name of the column to get.

      Returns:
      The `ColumnExpression` with the specified name.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](Qualifier.md)
- [Next Class](RowExpression.md)

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
