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

- [Prev Class](UnresolvedExpression.md)
- [Next Class](ValueComparisonCondition.md)

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

## Class UnresolvedQuery

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.DataObject](DataObject.md)

    - - [oracle.olapi.syntax.Query](Query.md)

      - - oracle.olapi.syntax.UnresolvedQuery

<!-- -->

-

  ------------------------------------------------------------------------



      public final class UnresolvedQuery
      extends Query

  A `Query` that represents an invalid or unresolvable identifier. An application might encounter this class if it has passed an implementation of the `XMLParserCallback` interface in a call to a `SyntaxObject.fromSyntax` or `MdmMetadataProvider.importXML` method. If the methods of the `XMLParserCallback` implementation return `XMLParserCallback.ERROR_BY_INVALIDATING`, then Oracle OLAP does not throw an exception when it encounters an invalid or unresolvable identifier. Instead, it marks the object as invalid and continues parsing the XML or producing the `SyntaxObject`. However, if the application gets the `Query` for the invalid object, that `Query` is an instance of `UnresolvedQuery`.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description |
    |-----------------------------|
    | `UnresolvedQuery``()`       |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                             | Method and Description                                                                                                                                                                                                                     |
    |---------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`ColumnExpression`](ColumnExpression.md)                     | `getColumnExpression``(java.lang.String colName)`<br>Gets the specified `ColumnExpression` of this `UnresolvedQuery`.                                                                                                                      |
    | `java.util.List<`[`ColumnExpression`](ColumnExpression.md)`>` | `getColumnExpressions``()`<br>Gets the `ColumnExpression` objects that are associated with this `UnresolvedQuery`.                                                                                                                         |
    | `java.lang.String`                                            | `getName``()`<br>Gets the name of this `UnresolvedQuery`.                                                                                                                                                                                  |
    | `java.lang.Object`                                            | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitUnresolvedExpression` method of the `SyntaxObjectVisitor` and passes that method this `UnresolvedQuery` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[Query](Query.md)

      [`isFullyDimensioned`](Query.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### UnresolvedQuery

          public UnresolvedQuery()

  <!-- -->

  - ### Method Detail

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitUnresolvedExpression` method of the `SyntaxObjectVisitor` and passes that method this `UnresolvedQuery` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitUnresolvedQuery` method.

    <!-- -->

    - #### getColumnExpressions

          public java.util.List<ColumnExpression> getColumnExpressions()

      Gets the `ColumnExpression` objects that are associated with this `UnresolvedQuery`.
      Specified by:
      [`getColumnExpressions`](Query.md) in class [`Query`](Query.md)

      Returns:
      A `List` that contains the `ColumnExpression` objects associated with this `UnresolvedQuery`.

    <!-- -->

    - #### getColumnExpression

          public ColumnExpression getColumnExpression(java.lang.String colName)

      Gets the specified `ColumnExpression` of this `UnresolvedQuery`.
      Specified by:
      [`getColumnExpression`](Query.md) in class [`Query`](Query.md)

      Parameters:
      `colName` - A `String` that contains the name of a column.

      Returns:
      The `ColumnExpression` that has the specified name.

    <!-- -->

    - #### getName

          public java.lang.String getName()

      Gets the name of this `UnresolvedQuery`.
      Specified by:
      [`getName`](Query.md) in class [`Query`](Query.md)

      Returns:
      A `String` that contains the name of this `UnresolvedQuery`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](UnresolvedExpression.md)
- [Next Class](ValueComparisonCondition.md)

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
