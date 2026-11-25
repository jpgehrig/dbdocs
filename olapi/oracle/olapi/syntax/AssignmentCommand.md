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

- [Prev Class](AnalyzeCommand.md)
- [Next Class](BaseQuery.md)

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

## Class AssignmentCommand

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.BuildCommand](BuildCommand.md)

    - - [oracle.olapi.syntax.SimpleCommand](SimpleCommand.md)

      - - oracle.olapi.syntax.AssignmentCommand

<!-- -->

-

  ------------------------------------------------------------------------



      public final class AssignmentCommand
      extends SimpleCommand

  A `SimpleCommand` that represents the assignment of values for a measure of an `MdmCube` or an attribute of an `MdmPrimaryDimension` in a `BuildSpecification`.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                     |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `AssignmentCommand``(`[`MdmBaseAttribute`](../metadata/mdm/MdmBaseAttribute.md)` base, java.util.List<`[`Qualifier`](Qualifier.md)`> qualifiers, `[`TypedExpression`](TypedExpression.md)` rhsExpression)`<br>Creates a `AssignmentCommand` with the specified base expression and dimension member qualifiers. |
    | `AssignmentCommand``(`[`MdmBaseAttribute`](../metadata/mdm/MdmBaseAttribute.md)` base, `[`Qualifier`](Qualifier.md)`[] qualifiers, `[`TypedExpression`](TypedExpression.md)` rhsExpression)`<br>Creates a `AssignmentCommand` with the specified base expression and dimension member qualifiers.               |
    | `AssignmentCommand``(`[`MdmBaseMeasure`](../metadata/mdm/MdmBaseMeasure.md)` base, java.util.List<`[`Qualifier`](Qualifier.md)`> qualifiers, `[`TypedExpression`](TypedExpression.md)` rhsExpression)`<br>Creates a `AssignmentCommand` with the specified base expression and dimension member qualifiers.     |
    | `AssignmentCommand``(`[`MdmBaseMeasure`](../metadata/mdm/MdmBaseMeasure.md)` base, `[`Qualifier`](Qualifier.md)`[] qualifiers, `[`TypedExpression`](TypedExpression.md)` rhsExpression)`<br>Creates a `AssignmentCommand` with the specified base expression and dimension member qualifiers.                   |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                 | Method and Description                                                                                                                                                                                                                    |
    |-------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`MdmBaseAttribute`](../metadata/mdm/MdmBaseAttribute.md)         | `getBaseAttribute``()`<br>Gets the `MdmBaseAttribute` to which this `AssignmentCommand` assigns values.                                                                                                                                   |
    | [`MdmBaseMeasure`](../metadata/mdm/MdmBaseMeasure.md)             | `getBaseMeasure``()`<br>Gets the `MdmBaseMeasure` to which this `AssignmentCommand` assigns values.                                                                                                                                       |
    | [`Qualifier`](Qualifier.md)`[]`                                   | `getQualifiers``()`<br>Gets the qualifiers of this `AssignmentCommand`.                                                                                                                                                                   |
    | [`TypedExpression`](TypedExpression.md)                           | `getRHSExpression``()`<br>Gets the expression that specifies the values that this `AssignmentCommand` assigns.                                                                                                                            |
    | [`MdmDimensionedObject`](../metadata/mdm/MdmDimensionedObject.md) | `getTarget``()`<br>Gets the `MdmBaseAttribute` or `MdmBaseMeasure` to which this `AssignmentCommand` assigns values.                                                                                                                      |
    | `java.lang.String`                                                | `getTargetID``()`<br>Gets the ID of the `MdmBaseAttribute` or `MdmBaseMeasure` to which this `AssignmentCommand` assigns values.                                                                                                          |
    | `java.lang.Object`                                                | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitAssignmentCommand` method of the `SyntaxObjectVisitor` and passes that method this `AssignmentCommand` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### AssignmentCommand

          public AssignmentCommand(MdmBaseMeasure base,
                                   Qualifier[] qualifiers,
                                   TypedExpression rhsExpression)

      Creates a `AssignmentCommand` with the specified base expression and dimension member qualifiers.
      Parameters:
      `base` - The `MdmBaseMeasure` to which you are assigning values.

      `qualifiers` - An array of `Qualifier` objects that specify members of the dimensions of the measure.

      `rhsExpression` - A `TypedExpression` that resolves to the value that you want to assign.

    <!-- -->

    - #### AssignmentCommand

          public AssignmentCommand(MdmBaseMeasure base,
                                   java.util.List<Qualifier> qualifiers,
                                   TypedExpression rhsExpression)

      Creates a `AssignmentCommand` with the specified base expression and dimension member qualifiers.
      Parameters:
      `base` - The `MdmBaseMeasure` to which you are assigning values.

      `qualifiers` - A `List` of `Qualifier` objects that specify members of the dimensions of the measure.

      `rhsExpression` - A `TypedExpression` that resolves to the value that you want to assign.

    <!-- -->

    - #### AssignmentCommand

          public AssignmentCommand(MdmBaseAttribute base,
                                   Qualifier[] qualifiers,
                                   TypedExpression rhsExpression)

      Creates a `AssignmentCommand` with the specified base expression and dimension member qualifiers.
      Parameters:
      `base` - The `MdmBaseAttribute` to which you are assigning values.

      `qualifiers` - An array of `Qualifier` objects that specify members of the dimensions of the attribute.

      `rhsExpression` - A `TypedExpression` that resolves to the value that you want to assign.

    <!-- -->

    - #### AssignmentCommand

          public AssignmentCommand(MdmBaseAttribute base,
                                   java.util.List<Qualifier> qualifiers,
                                   TypedExpression rhsExpression)

      Creates a `AssignmentCommand` with the specified base expression and dimension member qualifiers.
      Parameters:
      `base` - The `MdmBaseAttribute` to which you are assigning values.

      `qualifiers` - A `List` of `Qualifier` objects that specify members of the dimensions of the attribute.

      `rhsExpression` - A `TypedExpression` that resolves to the value that you want to assign.

  <!-- -->

  - ### Method Detail

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitAssignmentCommand` method of the `SyntaxObjectVisitor` and passes that method this `AssignmentCommand` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitAssignmentCommand` method.

    <!-- -->

    - #### getBaseMeasure

          public MdmBaseMeasure getBaseMeasure()

      Gets the `MdmBaseMeasure` to which this `AssignmentCommand` assigns values.
      Returns:
      The `MdmBaseMeasure` of this `AssignmentCommand`.

    <!-- -->

    - #### getBaseAttribute

          public MdmBaseAttribute getBaseAttribute()

      Gets the `MdmBaseAttribute` to which this `AssignmentCommand` assigns values.
      Returns:
      The `MdmBaseAttribute` of this `AssignmentCommand`.

    <!-- -->

    - #### getTarget

          public MdmDimensionedObject getTarget()

      Gets the `MdmBaseAttribute` or `MdmBaseMeasure` to which this `AssignmentCommand` assigns values.
      Returns:
      The `MdmDimensionedObject` of this `AssignmentCommand`.

    <!-- -->

    - #### getTargetID

          public java.lang.String getTargetID()

      Gets the ID of the `MdmBaseAttribute` or `MdmBaseMeasure` to which this `AssignmentCommand` assigns values.
      Returns:
      A `String` that contains the ID of the `MdmDimensionedObject` of this `AssignmentCommand`.

    <!-- -->

    - #### getQualifiers

          public Qualifier[] getQualifiers()

      Gets the qualifiers of this `AssignmentCommand`.
      Returns:
      An array of `Qualifier` objects that limit the data of the base expression of this `AssignmentCommand`.

    <!-- -->

    - #### getRHSExpression

          public TypedExpression getRHSExpression()

      Gets the expression that specifies the values that this `AssignmentCommand` assigns.
      Returns:
      A `TypedExpression` that evaluates to an expression that specifies the values assigned by this `AssignmentCommand`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](AnalyzeCommand.md)
- [Next Class](BaseQuery.md)

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
