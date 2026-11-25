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

- [Prev Class](SymmetricCondition.md)
- [Next Class](SyntaxException.md)

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

## Class SymmetricConditionElement

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - oracle.olapi.syntax.SymmetricConditionElement

<!-- -->

-

  ------------------------------------------------------------------------



      public final class SymmetricConditionElement
      extends SyntaxObject

  A `SyntaxObject` that specifies a collection of the members of a dimension for a `SymmetricCondition`. You use a `SymmetricCondition` as the parameter for the [`setPrecomputeCondition(SymmetricCondition cond)`](../metadata/deployment/AWCubeOrganization.md) method of an `AWCubeOrganization`.
  When you create a `SymmetricConditionElement`, you specify an `MdmPrimaryDimension` and a qualifier or a collection of `MdmDimensionLevel` objects. The qualifier is one of the constant fields of this class, which specify either all of the members of a dimension or none of the members. The collection of `MdmDimensionLevel` objects can have one or more `MdmDimensionLevel` objects.

  For compatibility with the `SymmetricCondition` class in the 11.1 release of the Oracle OLAP Java API, you can also specify a `Condition` when creating a `SymmetricConditionElement`. The `Condition` is an `Expression` that specifies the dimension members. For an 11.2 application, use one of the other constructors.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                                                   |
    |---------------------------|-------------------------------------------------------------------------|
    | `static java.lang.String` | `ALL`<br>A constant that specifies all of the members of a dimension.   |
    | `static java.lang.String` | `NONE`<br>A constant that specifies none of the members of a dimension. |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                      |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `SymmetricConditionElement``(`[`MdmPrimaryDimension`](../metadata/mdm/MdmPrimaryDimension.md)` dimension, `[`Condition`](Condition.md)` condition)`<br>For compatibility with the 11.1 Oracle OLAP Java API, creates a `SymmetricConditionElement` with the specified dimension and `Condition`. |
    | `SymmetricConditionElement``(`[`MdmPrimaryDimension`](../metadata/mdm/MdmPrimaryDimension.md)` dimension, java.util.List<`[`MdmDimensionLevel`](../metadata/mdm/MdmDimensionLevel.md)`> levels)`<br>Creates a `SymmetricConditionElement` with the specified dimension and dimension levels.     |
    | `SymmetricConditionElement``(`[`MdmPrimaryDimension`](../metadata/mdm/MdmPrimaryDimension.md)` dimension, `[`MdmDimensionLevel`](../metadata/mdm/MdmDimensionLevel.md)`[] levels)`<br>Creates a `SymmetricConditionElement` with the specified dimension and dimension levels.                   |
    | `SymmetricConditionElement``(`[`MdmPrimaryDimension`](../metadata/mdm/MdmPrimaryDimension.md)` dimension, java.lang.String qualifier)`<br>Creates a `SymmetricConditionElement` with the specified dimension and qualifier.                                                                      |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                               | Method and Description                                                                                                                                                                                                                                    |
    |-----------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Condition`](Condition.md)                                     | `getCondition``()`<br>Gets the `Condition` that is associated with this `SymmetricConditionElement`.                                                                                                                                                      |
    | [`MdmPrimaryDimension`](../metadata/mdm/MdmPrimaryDimension.md) | `getDimension``()`<br>Gets the `MdmPrimaryDimension` that is associated with this `SymmetricConditionElement`.                                                                                                                                            |
    | `java.lang.String`                                              | `getDimensionID``()`<br>Gets the ID of the `MdmPrimaryDimension` that is associated with this `SymmetricConditionElement`.                                                                                                                                |
    | `java.lang.String[]`                                            | `getLevelIDs``()`<br>Gets the IDs of the `MdmDimensionLevel` objects that are associated with this `SymmetricConditionElement`.                                                                                                                           |
    | [`MdmDimensionLevel`](../metadata/mdm/MdmDimensionLevel.md)`[]` | `getLevels``()`<br>Gets the `MdmDimensionLevel` objects that are associated with this `SymmetricConditionElement`.                                                                                                                                        |
    | `java.lang.String`                                              | `getQualifier``()`<br>Gets the qualifier that is associated with this `SymmetricConditionElement`.                                                                                                                                                        |
    | `java.lang.Object`                                              | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitSymmetricConditionElement` method of the `SyntaxObjectVisitor` and passes that method this `SymmetricConditionElement` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### ALL

          public static final java.lang.String ALL

      A constant that specifies all of the members of a dimension.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### NONE

          public static final java.lang.String NONE

      A constant that specifies none of the members of a dimension.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### SymmetricConditionElement

          public SymmetricConditionElement(MdmPrimaryDimension dimension,
                                           java.lang.String qualifier)

      Creates a `SymmetricConditionElement` with the specified dimension and qualifier. The qualifier is one of the constants of this class, either `SymmetricConditionElement.ALL` or `SymmetricConditionElement.NONE`.
      Parameters:
      `dimension` - An `MdmPrimaryDimension`.

      `qualifier` - A `String` that is one of the constants of this class.

    <!-- -->

    - #### SymmetricConditionElement

          public SymmetricConditionElement(MdmPrimaryDimension dimension,
                                           Condition condition)

      For compatibility with the 11.1 Oracle OLAP Java API, creates a `SymmetricConditionElement` with the specified dimension and `Condition`. For an 11.2 application, use one of the other constructors.
      Parameters:
      `dimension` - An `MdmPrimaryDimension`.

      `condition` - A `Condition` that specifies members of the dimension.

    <!-- -->

    - #### SymmetricConditionElement

          public SymmetricConditionElement(MdmPrimaryDimension dimension,
                                           MdmDimensionLevel[] levels)

      Creates a `SymmetricConditionElement` with the specified dimension and dimension levels.
      Parameters:
      `dimension` - An `MdmPrimaryDimension`.

      `levels` - An array of `MdmDimensionLevel` objects.

    <!-- -->

    - #### SymmetricConditionElement

          public SymmetricConditionElement(MdmPrimaryDimension dimension,
                                           java.util.List<MdmDimensionLevel> levels)

      Creates a `SymmetricConditionElement` with the specified dimension and dimension levels.
      Parameters:
      `dimension` - An `MdmPrimaryDimension`.

      `levels` - A `List` of `MdmDimensionLevel` objects.

  <!-- -->

  - ### Method Detail

    - #### getDimension

          public MdmPrimaryDimension getDimension()

      Gets the `MdmPrimaryDimension` that is associated with this `SymmetricConditionElement`.
      Returns:
      The `MdmPrimaryDimension` object of this `SymmetricConditionElement`.

    <!-- -->

    - #### getDimensionID

          public java.lang.String getDimensionID()

      Gets the ID of the `MdmPrimaryDimension` that is associated with this `SymmetricConditionElement`.
      Returns:
      A `String` that contains the ID of the `MdmPrimaryDimension` object of this `SymmetricConditionElement`.

    <!-- -->

    - #### getCondition

          public Condition getCondition()

      Gets the `Condition` that is associated with this `SymmetricConditionElement`.
      Returns:
      The `Condition` object of this `SymmetricConditionElement`.

    <!-- -->

    - #### getLevelIDs

          public java.lang.String[] getLevelIDs()

      Gets the IDs of the `MdmDimensionLevel` objects that are associated with this `SymmetricConditionElement`.
      Returns:
      An array of `String` objects that contain the IDs of the `MdmDimensionLevel` objects of this `SymmetricConditionElement`.

    <!-- -->

    - #### getLevels

          public MdmDimensionLevel[] getLevels()

      Gets the `MdmDimensionLevel` objects that are associated with this `SymmetricConditionElement`.
      Returns:
      An array of the `MdmDimensionLevel` objects of this `SymmetricConditionElement`.

    <!-- -->

    - #### getQualifier

          public java.lang.String getQualifier()

      Gets the qualifier that is associated with this `SymmetricConditionElement`. A qualifier is one of the constant fields of this class.
      Returns:
      A `String` that contains the value of one of constant fields of this class or `null` if this `SymmetricConditionElement` does not have a qualifier.

    <!-- -->

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitSymmetricConditionElement` method of the `SyntaxObjectVisitor` and passes that method this `SymmetricConditionElement` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitSymmetricConditionElement` method.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](SymmetricCondition.md)
- [Next Class](SyntaxException.md)

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
