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

- [Prev Class](StringExpression.md)
- [Next Class](SymmetricConditionElement.md)

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

## Class SymmetricCondition

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - oracle.olapi.syntax.SymmetricCondition

<!-- -->

-

  ------------------------------------------------------------------------



      public final class SymmetricCondition
      extends SyntaxObject

  A `SyntaxObject` that specifies a collection of the members one or more dimensions. You use a `SymmetricCondition` as the parameter for the [`setPrecomputeCondition(SymmetricCondition cond)`](../metadata/deployment/AWCubeOrganization.md) method of an `AWCubeOrganization`.
  When you create a `SymmetricCondition`, you specify a collection of one or more `SymmetricConditionElement` objects. Each `SymmetricConditionElement` limits the selection of dimension members to all or none of the members of a dimension, or all of the members of one or more levels of the dimension. A `SymmetricCondition` is similar to a SQL `WHERE` clause.

  For compatibility with the `SymmetricCondition` class in the 11.1 release of the Oracle OLAP Java API, you can also specify a collection of `Condition` objects when creating a `SymmetricCondition`. Each `Condition` is an `Expression` that specifies dimension members. For an 11.2 application, use a constructor that takes `SymmetricConditionElement` objects.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                   |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `SymmetricCondition``(java.util.List<`[`MdmPrimaryDimension`](../metadata/mdm/MdmPrimaryDimension.md)`> dimensions, java.util.List<`[`Condition`](Condition.md)`> conditions)`<br>For compatibility with the 11.1 Oracle OLAP Java API, creates a `SymmetricCondition` with the specified dimensions and `Condition` objects. |
    | `SymmetricCondition``(java.util.List<`[`SymmetricConditionElement`](SymmetricConditionElement.md)`> elements)`<br>Creates a `SymmetricCondition` with the specified elements.                                                                                                                                                 |
    | `SymmetricCondition``(`[`MdmPrimaryDimension`](../metadata/mdm/MdmPrimaryDimension.md)`[] dimensions, `[`Condition`](Condition.md)`[] conditions)`<br>For compatibility with the 11.1 Oracle OLAP Java API, creates a `SymmetricCondition` with the specified dimensions and `Condition` objects.                             |
    | `SymmetricCondition``(`[`SymmetricConditionElement`](SymmetricConditionElement.md)`[] elements)`<br>Creates a `SymmetricCondition` with the specified elements.                                                                                                                                                               |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                   | Method and Description                                                                                                                                                                                                                      |
    |---------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Condition`](Condition.md)`[]`                                     | `getConditions``()`<br>Gets the `Condition` objects that are associated with this `SymmetricCondition`.                                                                                                                                     |
    | [`MdmPrimaryDimension`](../metadata/mdm/MdmPrimaryDimension.md)`[]` | `getDimensions``()`<br>Gets the `MdmPrimaryDimension` objects that are associated with this `SymmetricCondition`.                                                                                                                           |
    | [`SymmetricConditionElement`](SymmetricConditionElement.md)`[]`     | `getElements``()`<br>Gets the `SymmetricConditionElement` objects that are associated with this `SymmetricCondition`.                                                                                                                       |
    | `java.lang.Object`                                                  | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitSymmetricCondition` method of the `SyntaxObjectVisitor` and passes that method this `SymmetricCondition` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### SymmetricCondition

          public SymmetricCondition(MdmPrimaryDimension[] dimensions,
                                    Condition[] conditions)

      For compatibility with the 11.1 Oracle OLAP Java API, creates a `SymmetricCondition` with the specified dimensions and `Condition` objects. Each dimension must have a corresponding `Condition`. The order of the `Condition` objects must match the order of the dimensions. Each `Condition` is an `Expression` that specifies all, some, or none of the members of a dimension.
      For an 11.2 application, use a constructor that has a `List` or an array of `SymmetricConditionElement` objects as a parameter.

      Parameters:
      `dimensions` - An array of `MdmPrimaryDimension` objects.

      `conditions` - An array of `Condition` objects. Each `Condition` evaluates to a selection of dimension members. The number of elements in this array must match the number of elements in the `dimensions` array. Each `Condition` element must specify members of the corresponding `MdmPrimaryDimension` element of the `dimensions` array.

    <!-- -->

    - #### SymmetricCondition

          public SymmetricCondition(java.util.List<MdmPrimaryDimension> dimensions,
                                    java.util.List<Condition> conditions)

      For compatibility with the 11.1 Oracle OLAP Java API, creates a `SymmetricCondition` with the specified dimensions and `Condition` objects. Each dimension must have a corresponding `Condition`. The order of the `Condition` objects must match the order of the dimensions. Each `Condition` is an `Expression` that specifies all, some, or none of the members of a dimension.
      For an 11.2 application, use a constructor that has a `List` or an array of `SymmetricConditionElement` objects as a parameter.

      Parameters:
      `dimensions` - A `List` of `MdmPrimaryDimension` objects.

      `conditions` - A `List` of `Condition` objects. Each `Condition` evaluates to a selection of dimension members. The number of elements in this list must match the number of elements in the `dimensions` list. Each `Condition` element must specify members of the corresponding `MdmPrimaryDimension` element of the `dimensions` list.

    <!-- -->

    - #### SymmetricCondition

          public SymmetricCondition(SymmetricConditionElement[] elements)

      Creates a `SymmetricCondition` with the specified elements. Each `SymmetricConditionElement` specifies an `MdmPrimaryDimension` and a selection of members of the dimension.
      Parameters:
      `elements` - An array of `SymmetricConditionElement` objects.

    <!-- -->

    - #### SymmetricCondition

          public SymmetricCondition(java.util.List<SymmetricConditionElement> elements)

      Creates a `SymmetricCondition` with the specified elements. Each `SymmetricConditionElement` specifies an `MdmPrimaryDimension` and a selection of members of the dimension.
      Parameters:
      `elements` - A `List` of `SymmetricConditionElement` objects.

  <!-- -->

  - ### Method Detail

    - #### getDimensions

          public MdmPrimaryDimension[] getDimensions()

      Gets the `MdmPrimaryDimension` objects that are associated with this `SymmetricCondition`.
      Returns:
      An array of the `MdmPrimaryDimension` objects of this `SymmetricCondition`.

    <!-- -->

    - #### getConditions

          public Condition[] getConditions()

      Gets the `Condition` objects that are associated with this `SymmetricCondition`.
      Returns:
      An array of the `Condition` objects of this `SymmetricCondition`. If there is no `Condition` corresponding to an associated `MdmPrimaryDimension`, then returns null for that array element.

    <!-- -->

    - #### getElements

          public SymmetricConditionElement[] getElements()

      Gets the `SymmetricConditionElement` objects that are associated with this `SymmetricCondition`.
      Returns:
      An array of the `SymmetricConditionElement` objects of this `SymmetricCondition`.

    <!-- -->

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitSymmetricCondition` method of the `SyntaxObjectVisitor` and passes that method this `SymmetricCondition` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitSymmetricCondition` method.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](StringExpression.md)
- [Next Class](SymmetricConditionElement.md)

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
