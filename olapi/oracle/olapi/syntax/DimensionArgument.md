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

- [Prev Class](DateExpression.md)
- [Next Class](Expression.md)

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

## Class DimensionArgument

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.DataObject](DataObject.md)

    - - oracle.olapi.syntax.DimensionArgument

<!-- -->

- All Implemented Interfaces:
  [FunctionArgument](FunctionArgument.md)

  <!-- -->

  Direct Known Subclasses:
  [UnresolvedDimensionArgument](UnresolvedDimensionArgument.md)

  ------------------------------------------------------------------------



      public class DimensionArgument
      extends DataObject
      implements FunctionArgument

  A `DataObject` that represents an `MdmDimension` as a function argument.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                         |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------|
    | `DimensionArgument``(`[`MdmDimension`](../metadata/mdm/MdmDimension.md)` dimension)`<br>Creates a `DimensionArgument` with the specified dimension. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                 | Method and Description                                                                                                                                                                                                                    |
    |---------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`MdmDimension`](../metadata/mdm/MdmDimension.md) | `getDimension``()`<br>Gets the dimension that is associated with this `DimensionArgument`.                                                                                                                                                |
    | `java.lang.String`                                | `getDimensionID``()`<br>Gets the ID of the dimension that is associated with this `DimensionArgument`.                                                                                                                                    |
    | `java.lang.Object`                                | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitDimensionArgument` method of the `SyntaxObjectVisitor` and passes that method this `DimensionArgument` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### DimensionArgument

          public DimensionArgument(MdmDimension dimension)

      Creates a `DimensionArgument` with the specified dimension.
      Parameters:
      `dimension` - The `MdmDimension` to associate with the new `DimensionArgument</CODE.`

  <!-- -->

  - ### `Method Detail`

    - #### `visit`

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      `Calls the ``visitDimensionArgument`` method of the ``SyntaxObjectVisitor`` and passes that method this ``DimensionArgument`` and an ``Object``.`
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitDimensionArgument` method.

    <!-- -->

    - #### getDimension

          public MdmDimension getDimension()

      Gets the dimension that is associated with this `DimensionArgument`.
      Returns:
      The `MdmDimension` of this `DimensionArgument`.

    <!-- -->

    - #### getDimensionID

          public java.lang.String getDimensionID()

      Gets the ID of the dimension that is associated with this `DimensionArgument`.
      Returns:
      A `String` that contains the ID of the `MdmDimension` of this `DimensionArgument`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](DateExpression.md)
- [Next Class](Expression.md)

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
