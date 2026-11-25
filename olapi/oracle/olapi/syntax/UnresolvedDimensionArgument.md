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

- [Prev Class](UnaryOperatorExpression.md)
- [Next Class](UnresolvedExpression.md)

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

## Class UnresolvedDimensionArgument

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.DataObject](DataObject.md)

    - - [oracle.olapi.syntax.DimensionArgument](DimensionArgument.md)

      - - oracle.olapi.syntax.UnresolvedDimensionArgument

<!-- -->

- All Implemented Interfaces:
  [FunctionArgument](FunctionArgument.md)

  ------------------------------------------------------------------------



      public final class UnresolvedDimensionArgument
      extends DimensionArgument

  A `DimensionArgument` that represents an invalid or unresolvable identifier. An application might encounter this class if it has passed an implementation of the `XMLParserCallback` interface in a call to a `SyntaxObject.fromSyntax` or `MdmMetadataProvider.importXML` method. If the methods of the `XMLParserCallback` implementation return `XMLParserCallback.ERROR_BY_INVALIDATING`, then Oracle OLAP does not throw an exception when it encounters an invalid or unresolvable identifier. Instead, it marks the object as invalid and continues parsing the XML or producing the `SyntaxObject`. However, if the application gets a `DimensionArgument` for the invalid object, that `DimensionArgument` is an instance of `UnresolvedDimensionArgument`.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                    |
    |--------------------------------------------------------------------------------|
    | `UnresolvedDimensionArgument``()`<br>Creates an `UnresolvedDimensionArgument`. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                                                                                 |
    |--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object` | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitUnresolvedExpression` method of the `SyntaxObjectVisitor` and passes that method this `UnresolvedDimensionArgument` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[DimensionArgument](DimensionArgument.md)

      [`getDimension`](DimensionArgument.md)`, `[`getDimensionID`](DimensionArgument.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### UnresolvedDimensionArgument

          public UnresolvedDimensionArgument()

      Creates an `UnresolvedDimensionArgument`.

  <!-- -->

  - ### Method Detail

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitUnresolvedExpression` method of the `SyntaxObjectVisitor` and passes that method this `UnresolvedDimensionArgument` and an `Object`.
      Overrides:
      [`visit`](DimensionArgument.md) in class [`DimensionArgument`](DimensionArgument.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitUnresolvedDimensionArgument` method.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](UnaryOperatorExpression.md)
- [Next Class](UnresolvedExpression.md)

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
