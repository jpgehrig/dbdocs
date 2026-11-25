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

- [Prev Class](Expression.md)
- [Next Class](FromClauseElement.md)

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

## Class FromClause

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.DataObject](DataObject.md)

    - - oracle.olapi.syntax.FromClause

<!-- -->

-

  ------------------------------------------------------------------------



      public final class FromClause
      extends DataObject

  A `DataObject` that represents a list of relational tables. A `FromClause` has one or more `FromClauseElement` objects, each of which has an associated `Query`. You use a `FromClause` to specify data sources for a `CubeMap` or a `DimensionMap`. A `FromClause` that has only one `FromClauseElement` is functionally the same as a `Query`.
  See Also:
  [`CubeMap`](../metadata/mapping/CubeMap.md), [`DimensionMap`](../metadata/mapping/DimensionMap.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                 |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `FromClause``(`[`FromClauseElement`](FromClauseElement.md)`[] fromClauseElements)`<br>Creates a `FromClause` that has the specified elements.               |
    | `FromClause``(java.util.List<`[`FromClauseElement`](FromClauseElement.md)`> fromClauseElements)`<br>Creates a `FromClause` that has the specified elements. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                               | Method and Description                                                                                                                                                                                                      |
    |-------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`FromClauseElement`](FromClauseElement.md)`[]` | `getFromClauseElements``()`<br>Gets the `FromClauseElement` objects that are associated with the `FromClause`.                                                                                                              |
    | `java.lang.Object`                              | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitFromClause` method of the `SyntaxObjectVisitor` and passes that method this `FromClause` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### FromClause

          public FromClause(FromClauseElement[] fromClauseElements)

      Creates a `FromClause` that has the specified elements.
      Parameters:
      `fromClauseElements` - An array of `FromClauseElement` objects.

    <!-- -->

    - #### FromClause

          public FromClause(java.util.List<FromClauseElement> fromClauseElements)

      Creates a `FromClause` that has the specified elements.
      Parameters:
      `fromClauseElements` - A `List` of `FromClauseElement` objects.

  <!-- -->

  - ### Method Detail

    - #### getFromClauseElements

          public FromClauseElement[] getFromClauseElements()

      Gets the `FromClauseElement` objects that are associated with the `FromClause`.
      Returns:
      An array of the `FromClauseElement` objects associated with the `FromClause`.

    <!-- -->

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitFromClause` method of the `SyntaxObjectVisitor` and passes that method this `FromClause` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitFromClause` method.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](Expression.md)
- [Next Class](FromClauseElement.md)

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
