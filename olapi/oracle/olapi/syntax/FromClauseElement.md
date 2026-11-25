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

- [Prev Class](FromClause.md)
- [Next Class](FunctionArgument.md)

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

## Class FromClauseElement

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.DataObject](DataObject.md)

    - - oracle.olapi.syntax.FromClauseElement

<!-- -->

-

  ------------------------------------------------------------------------



      public final class FromClauseElement
      extends DataObject

  A `DataObject` that contains a `Query` and is an element of a `FromClause`. You use the `getQuery` method of an `MdmTable` to get the `Query` for a `FromClauseElement`.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                      |
    |----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `FromClauseElement``(`[`Query`](Query.md)` query)`<br>Creates a `FromClauseElement` that has the specified `Query`.                                                                                                                                                              |
    | `FromClauseElement``(`[`Query`](Query.md)` query, java.lang.String alias)`<br>Creates a `FromClauseElement` that has the specified `Query` and alias.                                                                                                                            |
    | `FromClauseElement``(`[`Query`](Query.md)` query, java.lang.String alias, boolean hasAS)`<br>Creates a `FromClauseElement` that has the specified `Query` and alias and that specifies whether or not to insert the string `AS` between the syntax of the `Query` and the alias. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type   | Method and Description                                                                                                                                                                                                                    |
    |---------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`  | `getAlias``()`<br>Gets the alias for the `Query` of the `FromClauseElement`.                                                                                                                                                              |
    | `boolean`           | `getHasAS``()`<br>Indicates whether or not this `FromClauseElement` includes an `AS` between the `Query` syntax and the alias.                                                                                                            |
    | [`Query`](Query.md) | `getQuery``()`<br>Gets the `Query` of the `FromClauseElement`.                                                                                                                                                                            |
    | `java.lang.Object`  | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitFromClauseElement` method of the `SyntaxObjectVisitor` and passes that method this `FromClauseElement` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### FromClauseElement

          public FromClauseElement(Query query,
                                   java.lang.String alias,
                                   boolean hasAS)

      Creates a `FromClauseElement` that has the specified `Query` and alias and that specifies whether or not to insert the string `AS` between the syntax of the `Query` and the alias.
      Parameters:
      `query` - A `Query` for the element.

      `alias` - An `String` that contains an optional alias for the `Query`.

      `hasAS` - A `boolean` that is `true` to include an `AS` between the `Query` syntax and the alias or `false` to not include it.

    <!-- -->

    - #### FromClauseElement

          public FromClauseElement(Query query,
                                   java.lang.String alias)

      Creates a `FromClauseElement` that has the specified `Query` and alias.
      Parameters:
      `query` - A `Query` for the element.

      `alias` - An `String` that contains an optional alias for the `Query`.

    <!-- -->

    - #### FromClauseElement

          public FromClauseElement(Query query)

      Creates a `FromClauseElement` that has the specified `Query`.
      Parameters:
      `query` - A `Query` for the element.

  <!-- -->

  - ### Method Detail

    - #### getAlias

          public java.lang.String getAlias()

      Gets the alias for the `Query` of the `FromClauseElement`.
      Returns:
      A `String` that contains the alias for the `Query` of the `FromClauseElement`.

    <!-- -->

    - #### getQuery

          public Query getQuery()

      Gets the `Query` of the `FromClauseElement`.
      Returns:
      The `Query` of the `FromClauseElement`.

    <!-- -->

    - #### getHasAS

          public boolean getHasAS()

      Indicates whether or not this `FromClauseElement` includes an `AS` between the `Query` syntax and the alias.
      Returns:
      A `boolean` that is `true` if this `FromClauseElement` includes an `AS` between the `Query` syntax and the alias or `false` if it does not.

    <!-- -->

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitFromClauseElement` method of the `SyntaxObjectVisitor` and passes that method this `FromClauseElement` and an `Object`.
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

- [Prev Class](FromClause.md)
- [Next Class](FunctionArgument.md)

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
