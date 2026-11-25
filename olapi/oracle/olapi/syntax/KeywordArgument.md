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

- [Prev Class](IsCondition.md)
- [Next Class](KeywordCatalog.md)

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

## Class KeywordArgument

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.DataObject](DataObject.md)

    - - oracle.olapi.syntax.KeywordArgument

<!-- -->

- All Implemented Interfaces:
  [FunctionArgument](FunctionArgument.md)

  ------------------------------------------------------------------------



      public final class KeywordArgument
      extends DataObject
      implements FunctionArgument

  A `DataObject` that represents a keyword as a function argument.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                         |
    |-----------------------------------------------------------------------------------------------------|
    | `KeywordArgument``(java.lang.String name)`<br>Creates an `KeywordArgument` with the specified name. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                                                                |
    |--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`          | `equals``(java.lang.Object rhs)`<br>Indicates whether this `KeywordArgument` is the same as the specified `KeywordArgument`.                                                                                                          |
    | `java.lang.String` | `getName``()`<br>Gets the name of this `KeywordArgument`.                                                                                                                                                                             |
    | `java.lang.Object` | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitKeywordArgument` method of the `SyntaxObjectVisitor` and passes that method this `KeywordArgument` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### KeywordArgument

          public KeywordArgument(java.lang.String name)

      Creates an `KeywordArgument` with the specified name.
      Parameters:
      `name` - A `String` that contains a name for the new `KeywordArgument</CODE.`

  <!-- -->

  - ### `Method Detail`

    - #### `visit`

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      `Calls the ``visitKeywordArgument`` method of the ``SyntaxObjectVisitor`` and passes that method this ``KeywordArgument`` and an ``Object``.`
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitKeywordArgument` method.

    <!-- -->

    - #### getName

          public java.lang.String getName()

      Gets the name of this `KeywordArgument`.
      Returns:
      A `String` that contains the name of this `KeywordArgument</CODE.`

    <!-- -->

    - #### `equals`

          public boolean equals(java.lang.Object rhs)

      `Indicates whether this ``KeywordArgument`` is the same as the specified ``KeywordArgument``.`
      Overrides:
      `equals` in class `java.lang.Object`

      Parameters:
      `rhs` - A `KeywordArgument` to compare to this `KeywordArgument`.

      Returns:
      A `boolean` that is `true` if this `KeywordArgument` is the same as the input `KeywordArgument` or is `false` otherwise.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](IsCondition.md)
- [Next Class](KeywordCatalog.md)

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
