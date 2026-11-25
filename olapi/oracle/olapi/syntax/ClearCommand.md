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

- [Prev Class](CaseExpression.md)
- [Next Class](ColumnExpression.md)

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

## Class ClearCommand

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.BuildCommand](BuildCommand.md)

    - - [oracle.olapi.syntax.SimpleCommand](SimpleCommand.md)

      - - oracle.olapi.syntax.ClearCommand

<!-- -->

-

  ------------------------------------------------------------------------



      public final class ClearCommand
      extends SimpleCommand

  A `SimpleCommand` that clears data from the measures of a cube during a build process. You use a `ClearCommand` in a `BuildSpecification` for an `MdmCube` to delete existing data before using a `LoadCommand` to load data in the measures of the cube.
  You can add `ClearCommand` in a `BuildSpecification` for an `MdmPrimaryDimension`, which deletes all members of the dimension. Instead, however, you can use a synchronized load command, which deletes dimension members that no longer exist in the relational source tables. To get a synchronized load command, use the `LoadCommand.SYNCH` constant.

  You get an instance of a `ClearCommand` by using one of static constant fields of this class. Each constant produces a `ClearCommand` that specifies a different extent and manner of clearing of data. You can clear detail (leaf-level) values only, aggregate values only, or all values. You can also clear the data serially or by using parallel processes. A serial clear operation uses a single process when clearing partitioned data, regardless of the parallelism setting specified by the `BuildProperties` object that is associated with the `BuildProcess`. A parallel clear operation uses multiple processes when clearing partitioned data.

  For the constant fields `CLEAR`, `CLEAR_PARALLEL`, and `CLEAR_SERIAL`, which do not explicitly specify that the target of the CLEAR operation is the detail, aggregate, or all values, the target is determined by the refresh method specified for the build. For a description of the refresh methods, see the [`setRefreshMethod`](../data/source/BuildProperties.md) of `BuildProperties`. The refresh method affects a `ClearCommand` as follows.

  | Refresh Method | Effect on ClearCommand                                                                                                              |
  |:--------------:|-------------------------------------------------------------------------------------------------------------------------------------|
  |      `C`       | Results in a `CLEAR_VALUES`, which deletes all values.                                                                              |
  |      `S`       | Results in a `CLEAR_LEAVES`, which deletes detail-level values.                                                                     |
  |   `F` or `P`   | Results in the refreshing of materialized views, which does not involve a CLEAR operation.                                          |
  |      `?`       | Results in the effect of an `F`, `P`, `C`, or `S`, depending on the cube and the changes that have occurred since the last refresh. |

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                                                                                                                                                                    |
    |---------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static ClearCommand`     | `CLEAR`<br>Produces a `ClearCommand` that specifies deleting either detail values only or all values, depending on the refresh method of the build.                                      |
    | `static ClearCommand`     | `CLEAR_AGGREGATES`<br>Produces a `ClearCommand` that specifies deleting only the aggregate values of the measures of a cube.                                                             |
    | `static ClearCommand`     | `CLEAR_AGGREGATES_PARALLEL`<br>Produces a `ClearCommand` that specifies deleting only the aggregate values of the measures of a cube using parallel processes, if possible.              |
    | `static ClearCommand`     | `CLEAR_AGGREGATES_SERIAL`<br>Produces a `ClearCommand` that specifies deleting only the aggregate values of the measures of a cube using a single process.                               |
    | `static ClearCommand`     | `CLEAR_LEAVES`<br>Produces a `ClearCommand` that specifies deleting only the detail values of the measures of a cube.                                                                    |
    | `static ClearCommand`     | `CLEAR_LEAVES_PARALLEL`<br>Produces a `ClearCommand` that specifies deleting only the detail values of the measures of a cube using parallel processes, if possible.                     |
    | `static ClearCommand`     | `CLEAR_LEAVES_SERIAL`<br>Produces a `ClearCommand` that specifies deleting only the detail values of the measures of a cube using a single process.                                      |
    | `static ClearCommand`     | `CLEAR_PARALLEL`<br>Produces a `ClearCommand` that specifies using parallel processes in deleting either detail values only or all values, depending on the refresh method of the build. |
    | `static ClearCommand`     | `CLEAR_SERIAL`<br>Produces a `ClearCommand` that specifies using a single process in deleting either detail values only or all values, depending on the refresh method of the build.     |
    | `static java.lang.String` | `CLEAR_TARGET_AGGREGATES`<br>A constant that specifies clearing the aggregate values of the target.                                                                                      |
    | `static java.lang.String` | `CLEAR_TARGET_ALL_AGGREGATES`<br>A constant that specifies clearing all of the aggregate values of the target.                                                                           |
    | `static java.lang.String` | `CLEAR_TARGET_LEAVES`<br>A constant that specifies clearing the leaf values of the target.                                                                                               |
    | `static java.lang.String` | `CLEAR_TARGET_NONE`<br>A constant that specifies clearing none of the values of the target.                                                                                              |
    | `static java.lang.String` | `CLEAR_TARGET_STALE_AGGREGATES`<br>A constant that specifies clearing the stale aggregate values of the target.                                                                          |
    | `static java.lang.String` | `CLEAR_TARGET_VALUES`<br>A constant that specifies clearing all of the values of the target.                                                                                             |
    | `static ClearCommand`     | `CLEAR_VALUES`<br>Produces a `ClearCommand` that specifies deleting all of the values of the measures of a cube.                                                                         |
    | `static ClearCommand`     | `CLEAR_VALUES_PARALLEL`<br>Produces a `ClearCommand` that specifies deleting all of the values of the measures of a cube using parallel processes, if possible.                          |
    | `static ClearCommand`     | `CLEAR_VALUES_SERIAL`<br>Produces a `ClearCommand` that specifies deleting all of the values of the measures of a cube using a single process.                                           |
    | `static java.lang.String` | `NO_PARALLELISM_OPTION`<br>A constant that specifies no parallelism for a `ClearCommand`.                                                                                                |
    | `static java.lang.String` | `PARALLEL_OPTION`<br>A constant that specifies using parallel processes, if possible, for a `ClearCommand`.                                                                              |
    | `static java.lang.String` | `SERIAL_OPTION`<br>A constant that specifies using a single process for a `ClearCommand`.                                                                                                |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                       |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `ClearCommand``(java.lang.String clearTarget, java.lang.String parallelismOption)`<br>Creates a `ClearCommand` with the specified target and parallelism options. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                                                                                   |
    |--------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String` | `getClearTarget``()`<br>Gets a static value that indicates the extent of the clearing of measure values that this `ClearCommand` represents, such as `CLEAR_TARGET_AGGREGATES`, `CLEAR_TARGET_LEAVES`, or `CLEAR_TARGET_VALUES`, or `CLEAR_TARGET_NONE`. |
    | `java.lang.String` | `getParallelismOption``()`<br>Gets a static value that indicates the parallelism option of this `ClearCommand`, which can be `PARALLEL_OPTION`, `SERIAL_OPTION`, or `NO_PARALLELISM_OPTION`.                                                             |
    | `java.lang.Object` | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitClearCommand` method of the `SyntaxObjectVisitor` and passes that method this `ClearCommand` and an `Object`.                          |

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### NO_PARALLELISM_OPTION

          public static final java.lang.String NO_PARALLELISM_OPTION

      A constant that specifies no parallelism for a `ClearCommand`.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SERIAL_OPTION

          public static final java.lang.String SERIAL_OPTION

      A constant that specifies using a single process for a `ClearCommand`.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PARALLEL_OPTION

          public static final java.lang.String PARALLEL_OPTION

      A constant that specifies using parallel processes, if possible, for a `ClearCommand`.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CLEAR_TARGET_AGGREGATES

          public static final java.lang.String CLEAR_TARGET_AGGREGATES

      A constant that specifies clearing the aggregate values of the target.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CLEAR_TARGET_LEAVES

          public static final java.lang.String CLEAR_TARGET_LEAVES

      A constant that specifies clearing the leaf values of the target.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CLEAR_TARGET_VALUES

          public static final java.lang.String CLEAR_TARGET_VALUES

      A constant that specifies clearing all of the values of the target.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CLEAR_TARGET_NONE

          public static final java.lang.String CLEAR_TARGET_NONE

      A constant that specifies clearing none of the values of the target.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CLEAR_TARGET_STALE_AGGREGATES

          public static final java.lang.String CLEAR_TARGET_STALE_AGGREGATES

      A constant that specifies clearing the stale aggregate values of the target.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CLEAR_TARGET_ALL_AGGREGATES

          public static final java.lang.String CLEAR_TARGET_ALL_AGGREGATES

      A constant that specifies clearing all of the aggregate values of the target.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CLEAR

          public static final ClearCommand CLEAR

      Produces a `ClearCommand` that specifies deleting either detail values only or all values, depending on the refresh method of the build.

    <!-- -->

    - #### CLEAR_PARALLEL

          public static final ClearCommand CLEAR_PARALLEL

      Produces a `ClearCommand` that specifies using parallel processes in deleting either detail values only or all values, depending on the refresh method of the build.

    <!-- -->

    - #### CLEAR_SERIAL

          public static final ClearCommand CLEAR_SERIAL

      Produces a `ClearCommand` that specifies using a single process in deleting either detail values only or all values, depending on the refresh method of the build.

    <!-- -->

    - #### CLEAR_VALUES

          public static final ClearCommand CLEAR_VALUES

      Produces a `ClearCommand` that specifies deleting all of the values of the measures of a cube.

    <!-- -->

    - #### CLEAR_VALUES_SERIAL

          public static final ClearCommand CLEAR_VALUES_SERIAL

      Produces a `ClearCommand` that specifies deleting all of the values of the measures of a cube using a single process.

    <!-- -->

    - #### CLEAR_VALUES_PARALLEL

          public static final ClearCommand CLEAR_VALUES_PARALLEL

      Produces a `ClearCommand` that specifies deleting all of the values of the measures of a cube using parallel processes, if possible.

    <!-- -->

    - #### CLEAR_AGGREGATES

          public static final ClearCommand CLEAR_AGGREGATES

      Produces a `ClearCommand` that specifies deleting only the aggregate values of the measures of a cube.

    <!-- -->

    - #### CLEAR_AGGREGATES_PARALLEL

          public static final ClearCommand CLEAR_AGGREGATES_PARALLEL

      Produces a `ClearCommand` that specifies deleting only the aggregate values of the measures of a cube using parallel processes, if possible.

    <!-- -->

    - #### CLEAR_AGGREGATES_SERIAL

          public static final ClearCommand CLEAR_AGGREGATES_SERIAL

      Produces a `ClearCommand` that specifies deleting only the aggregate values of the measures of a cube using a single process.

    <!-- -->

    - #### CLEAR_LEAVES

          public static final ClearCommand CLEAR_LEAVES

      Produces a `ClearCommand` that specifies deleting only the detail values of the measures of a cube.

    <!-- -->

    - #### CLEAR_LEAVES_SERIAL

          public static final ClearCommand CLEAR_LEAVES_SERIAL

      Produces a `ClearCommand` that specifies deleting only the detail values of the measures of a cube using a single process.

    <!-- -->

    - #### CLEAR_LEAVES_PARALLEL

          public static final ClearCommand CLEAR_LEAVES_PARALLEL

      Produces a `ClearCommand` that specifies deleting only the detail values of the measures of a cube using parallel processes, if possible.

  <!-- -->

  - ### Constructor Detail

    - #### ClearCommand

          public ClearCommand(java.lang.String clearTarget,
                              java.lang.String parallelismOption)

      Creates a `ClearCommand` with the specified target and parallelism options.
      Parameters:
      `clearTarget` - One of the `ClearTarget` constants, such as `ClearTargetAggregates` or `ClearTargetValues`.

      `parallelismOption` - `NO_PARALLELISM_OPTION`, `PARALLEL_OPTION`, or `SERIAL_OPTION`.

  <!-- -->

  - ### Method Detail

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitClearCommand` method of the `SyntaxObjectVisitor` and passes that method this `ClearCommand` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitClearCommand` method.

    <!-- -->

    - #### getClearTarget

          public java.lang.String getClearTarget()

      Gets a static value that indicates the extent of the clearing of measure values that this `ClearCommand` represents, such as `CLEAR_TARGET_AGGREGATES`, `CLEAR_TARGET_LEAVES`, or `CLEAR_TARGET_VALUES`, or `CLEAR_TARGET_NONE`. For the `ClearCommand` objects produced by the `CLEAR`, `CLEAR_PARALLEL`, and `CLEAR_SERIAL` constants, this method returns `CLEAR_TARGET_NONE`.
      Returns:
      A `String` that indicates the extent of the clearing of the measure values.

    <!-- -->

    - #### getParallelismOption

          public java.lang.String getParallelismOption()

      Gets a static value that indicates the parallelism option of this `ClearCommand`, which can be `PARALLEL_OPTION`, `SERIAL_OPTION`, or `NO_PARALLELISM_OPTION`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](CaseExpression.md)
- [Next Class](ColumnExpression.md)

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
