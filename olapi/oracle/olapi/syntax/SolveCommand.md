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

- [Prev Class](SimpleCommand.md)
- [Next Class](SolveStepCommand.md)

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

## Class SolveCommand

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.BuildCommand](BuildCommand.md)

    - - [oracle.olapi.syntax.SimpleCommand](SimpleCommand.md)

      - - oracle.olapi.syntax.SolveCommand

<!-- -->

-

  ------------------------------------------------------------------------



      public final class SolveCommand
      extends SimpleCommand

  A `SimpleCommand` that initiates the operations that calculate the data for the measures of an `MdmCube`. You get an instance of a `SolveCommand` by using one of static constant fields of the class. You add a `SolveCommand` after a `LoadCommand` in the list of build commands in the `BuildSpecification` that you associate with the `MdmCube`.
  For an `MdmCube` that is partitioned, you can specify a serial solve or a parallel solve. A serial solve calculates the data for the measures of the partitions serially, using a single process, regardless of the parallelism setting specified by the `BuildProperties` object that is associated with the `BuildProcess` that includes the cube. A parallel solve calculates the data for the measures of the partitions simultaneously, using one process for each partition, or as many processes as are available. If the partitioning of the cube does not match the partitioning of the source table, then a serial solve is a good choice.

  See Also:
  [`LoadCommand`](LoadCommand.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                                                                                                |
    |---------------------------|----------------------------------------------------------------------------------------------------------------------|
    | `static java.lang.String` | `NO_PARALLELISM_OPTION`<br>A constant that specifies no parallelism for a `SolveCommand`.                            |
    | `static java.lang.String` | `PARALLEL_OPTION`<br>A constant that specifies using parallel processes, if possible, for a `SolveCommand`.          |
    | `static java.lang.String` | `SERIAL_OPTION`<br>A constant that specifies using a single process for a `SolveCommand`.                            |
    | `static SolveCommand`     | `SOLVE`<br>Produces a `SolveCommand`.                                                                                |
    | `static SolveCommand`     | `SOLVE_PARALLEL`<br>Produces a `SolveCommand` that specifies solving the data using parallel processes, if possible. |
    | `static SolveCommand`     | `SOLVE_SERIAL`<br>Produces a `SolveCommand` that specifies solving the data using a single process.                  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                                                          |
    |--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String` | `getParallelismOption``()`<br>Gets a static value that indicates the parallelism option of this `SolveCommand`, which can be `PARALLEL_OPTION`, `SERIAL_OPTION`, or `NO_PARALLELISM_OPTION`.                                    |
    | `java.lang.Object` | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitSolveCommand` method of the `SyntaxObjectVisitor` and passes that method this `SolveCommand` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### NO_PARALLELISM_OPTION

          public static final java.lang.String NO_PARALLELISM_OPTION

      A constant that specifies no parallelism for a `SolveCommand`.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SERIAL_OPTION

          public static final java.lang.String SERIAL_OPTION

      A constant that specifies using a single process for a `SolveCommand`.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PARALLEL_OPTION

          public static final java.lang.String PARALLEL_OPTION

      A constant that specifies using parallel processes, if possible, for a `SolveCommand`.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SOLVE

          public static final SolveCommand SOLVE

      Produces a `SolveCommand`.

    <!-- -->

    - #### SOLVE_SERIAL

          public static final SolveCommand SOLVE_SERIAL

      Produces a `SolveCommand` that specifies solving the data using a single process.

    <!-- -->

    - #### SOLVE_PARALLEL

          public static final SolveCommand SOLVE_PARALLEL

      Produces a `SolveCommand` that specifies solving the data using parallel processes, if possible.

  <!-- -->

  - ### Method Detail

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitSolveCommand` method of the `SyntaxObjectVisitor` and passes that method this `SolveCommand` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitSolveCommand` method.

    <!-- -->

    - #### getParallelismOption

          public java.lang.String getParallelismOption()

      Gets a static value that indicates the parallelism option of this `SolveCommand`, which can be `PARALLEL_OPTION`, `SERIAL_OPTION`, or `NO_PARALLELISM_OPTION`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](SimpleCommand.md)
- [Next Class](SolveStepCommand.md)

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
