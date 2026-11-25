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

- [Prev Class](LoadCommand.md)
- [Next Class](NotCondition.md)

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

## Class ModelCommand

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.BuildCommand](BuildCommand.md)

    - - [oracle.olapi.syntax.SimpleCommand](SimpleCommand.md)

      - - oracle.olapi.syntax.ModelCommand

<!-- -->

- All Implemented Interfaces:
  [ConsistentSolveCommand](ConsistentSolveCommand.md)

  ------------------------------------------------------------------------



      public final class ModelCommand
      extends SimpleCommand
      implements ConsistentSolveCommand

  A `SimpleCommand` that represents an `MdmDimensionCalculationModel` in a `BuildSpecification`.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                                                                                                 |
    |---------------------------|-----------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String` | `DEFAULT_OPTION`<br>A constant that represents the default option to an OLAP DML command.                             |
    | `static java.lang.String` | `PARALLEL_OPTION`<br>A constant that represents an option that specifies parallel processing for an OLAP DML command. |
    | `static java.lang.String` | `SERIAL_OPTION`<br>A constant that represents an option that specifies serial processing for an OLAP DML command.     |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                               |
    |---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `ModelCommand``(`[`MdmDimensionCalculationModel`](../metadata/mdm/MdmDimensionCalculationModel.md)` model)`<br>Creates a `ModelCommand` object for the specified `MdmDimensionCalculationModel`.                          |
    | `ModelCommand``(`[`MdmDimensionCalculationModel`](../metadata/mdm/MdmDimensionCalculationModel.md)` model, java.lang.String option)`<br>Creates a `ModelCommand` object for the specified `MdmDimensionCalculationModel`. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                                 | Method and Description                                                                                                                                                                                                          |
    |-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`MdmDimensionCalculationModel`](../metadata/mdm/MdmDimensionCalculationModel.md) | `getModel``()`<br>Gets the `MdmDimensionCalculationModel` that is associated with this `ModelCommand`.                                                                                                                          |
    | `java.lang.String`                                                                | `getModelID``()`<br>Gets the ID of the `MdmDimensionCalculationModel` that is associated with this `ModelCommand`.                                                                                                              |
    | `java.lang.String`                                                                | `getOption``()`<br>Gets the option specified for this `ModelCommand`.                                                                                                                                                           |
    | `java.lang.Object`                                                                | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitModelCommand` method of the `SyntaxObjectVisitor` and passes that method this `ModelCommand` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### DEFAULT_OPTION

          public static final java.lang.String DEFAULT_OPTION

      A constant that represents the default option to an OLAP DML command. The default is to specify no option.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SERIAL_OPTION

          public static final java.lang.String SERIAL_OPTION

      A constant that represents an option that specifies serial processing for an OLAP DML command.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PARALLEL_OPTION

          public static final java.lang.String PARALLEL_OPTION

      A constant that represents an option that specifies parallel processing for an OLAP DML command.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### ModelCommand

          public ModelCommand(MdmDimensionCalculationModel model,
                              java.lang.String option)

      Creates a `ModelCommand` object for the specified `MdmDimensionCalculationModel`.
      Parameters:
      `model` - The `MdmDimensionCalculationModel` to include in the build specification.

      `option` - A `String` that contains one of the options for this class: DEFAULT_OPTION, SERIAL_OPTION, or PARALLEL_OPTION.

    <!-- -->

    - #### ModelCommand

          public ModelCommand(MdmDimensionCalculationModel model)

      Creates a `ModelCommand` object for the specified `MdmDimensionCalculationModel`.
      Parameters:
      `model` - The `MdmDimensionCalculationModel` to include in the build specification.

  <!-- -->

  - ### Method Detail

    - #### getModel

          public MdmDimensionCalculationModel getModel()

      Gets the `MdmDimensionCalculationModel` that is associated with this `ModelCommand`.
      Returns:
      The `MdmDimensionCalculationModel` to build.

    <!-- -->

    - #### getModelID

          public java.lang.String getModelID()

      Gets the ID of the `MdmDimensionCalculationModel` that is associated with this `ModelCommand`.
      Returns:
      A `String` that contains the ID of the `MdmDimensionCalculationModel` to build.

    <!-- -->

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitModelCommand` method of the `SyntaxObjectVisitor` and passes that method this `ModelCommand` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitModelCommand` method.

    <!-- -->

    - #### getOption

          public java.lang.String getOption()

      Gets the option specified for this `ModelCommand`. The option is the value of one of the contants of this class: DEFAULT_OPTION, SERIAL_OPTION, or PARALLEL_OPTION.
      Returns:
      A `String` that contains the option for the command of this `ModelCommand`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](LoadCommand.md)
- [Next Class](NotCondition.md)

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
