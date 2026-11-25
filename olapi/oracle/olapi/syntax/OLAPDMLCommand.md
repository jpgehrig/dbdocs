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

- [Prev Class](NumberExpression.md)
- [Next Class](OLAPDMLExpression.md)

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

## Class OLAPDMLCommand

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.BuildCommand](BuildCommand.md)

    - - [oracle.olapi.syntax.SimpleCommand](SimpleCommand.md)

      - - oracle.olapi.syntax.OLAPDMLCommand

<!-- -->

-

  ------------------------------------------------------------------------



      public final class OLAPDMLCommand
      extends SimpleCommand

  A `SimpleCommand` that represents an OLAP DML command in a `BuildSpecification`.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                                                                                                  |
    |---------------------------|------------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String` | `DEFAULT_OPTION`<br>A constant that represents the default option to the OLAP DML command.                             |
    | `static java.lang.String` | `PARALLEL_OPTION`<br>A constant that represents an option that specifies parallel processing for the OLAP DML command. |
    | `static java.lang.String` | `SERIAL_OPTION`<br>A constant that represents an option that specifies serial processing for the OLAP DML command.     |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                 |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `OLAPDMLCommand``(java.lang.String dml)`<br>Creates an `OLAPDMLCommand` object that has the specified OLAP DML command.                                     |
    | `OLAPDMLCommand``(java.lang.String dml, java.lang.String option)`<br>Creates an `OLAPDMLCommand` object that has the specified OLAP DML command and option. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                                                              |
    |--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String` | `getDML``()`<br>Gets the OLAP DML command of this `OLAPDMLCommand`.                                                                                                                                                                 |
    | `java.lang.String` | `getOption``()`<br>Gets the option specified for this `OLAPDMLCommand`.                                                                                                                                                             |
    | `java.lang.Object` | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitOLAPDMLCommand` method of the `SyntaxObjectVisitor` and passes that method this `OLAPDMLCommand` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### DEFAULT_OPTION

          public static final java.lang.String DEFAULT_OPTION

      A constant that represents the default option to the OLAP DML command. The default is to specify no option.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SERIAL_OPTION

          public static final java.lang.String SERIAL_OPTION

      A constant that represents an option that specifies serial processing for the OLAP DML command.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PARALLEL_OPTION

          public static final java.lang.String PARALLEL_OPTION

      A constant that represents an option that specifies parallel processing for the OLAP DML command.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### OLAPDMLCommand

          public OLAPDMLCommand(java.lang.String dml,
                                java.lang.String option)

      Creates an `OLAPDMLCommand` object that has the specified OLAP DML command and option. If you specify the PARALLEL_OPTION, then Oracle OLAP runs the commands in parallel by cube partition. If you specify the SERIAL_OPTION or the DEFAULT_OPTION, then Oracle OLAP runs the commands serially for the entire cube.
      Parameters:
      `dml` - A `String` that contains an OLAP DML command.

      `option` - A `String` that contains one of the options for this class: DEFAULT_OPTION, SERIAL_OPTION, or PARALLEL_OPTION.

    <!-- -->

    - #### OLAPDMLCommand

          public OLAPDMLCommand(java.lang.String dml)

      Creates an `OLAPDMLCommand` object that has the specified OLAP DML command.
      Parameters:
      `dml` - A `String` that contains an OLAP DML command.

  <!-- -->

  - ### Method Detail

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitOLAPDMLCommand` method of the `SyntaxObjectVisitor` and passes that method this `OLAPDMLCommand` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitOLAPDMLCommand` method.

    <!-- -->

    - #### getDML

          public java.lang.String getDML()

      Gets the OLAP DML command of this `OLAPDMLCommand`.
      Returns:
      A `String` that contains the OLAP DML command of this `OLAPDMLCommand`.

    <!-- -->

    - #### getOption

          public java.lang.String getOption()

      Gets the option specified for this `OLAPDMLCommand`. The option is the value of one of the contants of this class: DEFAULT_OPTION, SERIAL_OPTION, or PARALLEL_OPTION.
      Returns:
      A `String` that contains the option for the OLAP DML command of this `OLAPDMLCommand`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](NumberExpression.md)
- [Next Class](OLAPDMLExpression.md)

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
