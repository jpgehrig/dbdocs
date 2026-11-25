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

- [Prev Class](LiteralExpression.md)
- [Next Class](ModelCommand.md)

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

## Class LoadCommand

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.BuildCommand](BuildCommand.md)

    - - [oracle.olapi.syntax.SimpleCommand](SimpleCommand.md)

      - - oracle.olapi.syntax.LoadCommand

<!-- -->

-

  ------------------------------------------------------------------------



      public final class LoadCommand
      extends SimpleCommand

  A `SimpleCommand` that loads data into the dimensions or measures of an analytic workspace from relational source tables during a build. Options to a load command affect the loading of the data. You get an instance of a `LoadCommand` with an associated option by using one of static fields of this class or by using a constructor method.
  The following table lists the load command options and describes them.

  | Load Option | Effect on Load                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
  |:-----------:|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  |  `DEFAULT`  | For an `MdmPrimaryDimension`, the default option is a synchronized load.<br>For an `MdmCube`, the default option is an unsynchronized load.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
  |   `SYNCH`   | For an `MdmPrimaryDimension`, adds new members to the dimension and removes members that no longer exist in the relational source tables.<br>For an `MdmCube`, the `SYNCH` and `NO_SYNCH` options have the same effect. To avoid confusion, use the `NO_SYNCH` option for an `MdmCube`.                                                                                                                                                                                                                                                                                                                                                                                                                                         |
  | `NO_SYNCH`  | For an `MdmPrimaryDimension`, adds new members but does not remove members that no longer exist in the relational source tables. If the parent of a dimension member has changed in the relational data source, this option allows the load to change the parent-child relation in the analytic workspace.<br>For an `MdmCube`, loads the measure data for new dimension members but does not delete the data for dimension members that no longer exist. To remove the measure data for nonexistent dimension members, add a `ClearCommand` in the `BuildSpecification` before the `LoadCommand`. If you specify this option for an `MdmCube`, the build process determines whether to use a serial build or a parallel build. |
  |  `RETAIN`   | For an `MdmPrimaryDimension`, adds new members but does not remove members that no longer exist in the relational source tables. This option is the same as `NO_SYNCH` except that if the parent of a dimension member has changed in the relational source, `RETAIN` does not allow the load to change the parent-child relation in the analytic workspace. If the parentage has changed, then the load rejects the record. The rejection generates an error in the analytic workspace rejected records log, if the log is enabled.<br>For an `MdmCube`, this option does not apply.                                                                                                                                           |
  |  `SERIAL`   | For an `MdmCube`, loads the data into the measures using a single process. If a measure is partitioned, then this option loads the data of the partitions serially. If the partitioning of the cube does not match the partitioning of the source table, then a serial load is a good choice.<br>For an `MdmPrimaryDimension`, this option does not apply.                                                                                                                                                                                                                                                                                                                                                                      |
  | `PARALLEL`  | For an `MdmCube`, loads the data for partitioned measures using parallel processes. This option loads the data into the measures of the partitions simultaneously, using one process for each partition, or as many processes as are available.<br>For an `MdmPrimaryDimension`, this option does not apply.                                                                                                                                                                                                                                                                                                                                                                                                                    |
  |   `PRUNE`   | For an `MdmCube` with partitioned measures, spawns jobs only for the partitions for which measure data exists. Determining which partitions have data requires scanning the entire table. For tables that have terrabytes of data, a full table scan can be time comsuming.<br>For an `MdmPrimaryDimension`, this option does not apply.                                                                                                                                                                                                                                                                                                                                                                                        |

  If you want a `LoadCommand` that only loads data from a single `CubeMap`, then use a constructor that takes a `cubeMapName` parameter. If you create a `LoadCommand` without specifying a `CubeMap`, then the `LoadCommand` loads data from all of the `CubeMap` objects of the `MdmCube`.

  For more information about partitioned cubes, see the [`setPartitionLevel`](../metadata/deployment/AWCubeOrganization.md) method of `AWCubeOrganization`, the [`setParallelism`](../data/source/BuildProperties.md) method of `BuildProperties`, and *Oracle OLAP User's Guide*.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description                                                   |
    |---------------------------|-------------------------------------------------------------------------|
    | `static LoadCommand`      | `DEFAULT`<br>Produces a `LoadCommand` that executes a default load.     |
    | `static java.lang.String` | `DEFAULT_OPTION`<br>A constant that represents a default load.          |
    | `static java.lang.String` | `DELTA`<br>A constant that represents a DELTA load.                     |
    | `static java.lang.String` | `DELTA_ADD`<br>A constant that represents a DELTA ADD load.             |
    | `static java.lang.String` | `DELTA_SUBTRACT`<br>A constant that represents a DELTA SBUTRACT load.   |
    | `static LoadCommand`      | `NO_SYNCH`<br>Produces a `LoadCommand` that has the `NO_SYNCH` option.  |
    | `static java.lang.String` | `NO_SYNCH_OPTION`<br>A constant that represents an unsynchronized load. |
    | `static LoadCommand`      | `PARALLEL`<br>Produces a `LoadCommand` that has the `PARALLEL` option.  |
    | `static java.lang.String` | `PARALLEL_OPTION`<br>A constant that represents a parallel load.        |
    | `static LoadCommand`      | `PRUNE`<br>Produces a `LoadCommand` that has the `PRUNE` option.        |
    | `static java.lang.String` | `PRUNE_OPTION`<br>A constant that represents a pruned load.             |
    | `static LoadCommand`      | `RETAIN`<br>Produces a `LoadCommand` that has the `RETAIN` option.      |
    | `static java.lang.String` | `RETAIN_OPTION`<br>A constant that represents a retain load.            |
    | `static LoadCommand`      | `SERIAL`<br>Produces a `LoadCommand` that has the `SERIAL` option.      |
    | `static java.lang.String` | `SERIAL_OPTION`<br>A constant that represents a serial load.            |
    | `static LoadCommand`      | `SYNCH`<br>Produces a `LoadCommand` that has the `SYNCH` option.        |
    | `static java.lang.String` | `SYNCH_OPTION`<br>A constant that represents a synchronized load.       |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                               |
    |-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `LoadCommand``()`<br>Creates a `LoadCommand` with the default load command option.                                                                                                                                                                        |
    | `LoadCommand``(java.lang.String option)`<br>Creates a `LoadCommand` with the specified load command option.                                                                                                                                               |
    | `LoadCommand``(java.lang.String option, `[`Condition`](Condition.md)` whereCondition)`<br>Creates a `LoadCommand` with the specified load command option and `WHERE` `Condition`.                                                                         |
    | `LoadCommand``(java.lang.String option, `[`Condition`](Condition.md)` whereCondition, java.lang.String cubeMapName)`<br>Creates a `LoadCommand` with the specified load command option, `WHERE` `Condition`, and `CubeMap`.                               |
    | `LoadCommand``(java.lang.String option, java.lang.String cubeMapName)`<br>Creates a `LoadCommand` with the specified load command option and `CubeMap`.                                                                                                   |
    | `LoadCommand``(java.lang.String option, java.lang.String deltaOption, `[`Condition`](Condition.md)` whereCondition, java.lang.String cubeMapName)`<br>Creates a `LoadCommand` with the specified load command option, `WHERE` `Condition`, and `CubeMap`. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type           | Method and Description                                                                                                                                                                                                        |
    |-----------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String`          | `getCubeMapName``()`<br>Gets the name of the `CubeMap` that is associated with this `LoadCommand`.                                                                                                                            |
    | `java.lang.String`          | `getDeltaOption``()`<br>Gets the delta command option of this `LoadCommand`.                                                                                                                                                  |
    | `java.lang.String`          | `getLoadOption``()`<br>Gets the load command option of this `LoadCommand`.                                                                                                                                                    |
    | [`Condition`](Condition.md) | `getWhereCondition``()`<br>Gets the `Condition` of this `LoadCommand`.                                                                                                                                                        |
    | `java.lang.Object`          | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitLoadCommand` method of the `SyntaxObjectVisitor` and passes that method this `LoadCommand` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### DEFAULT_OPTION

          public static final java.lang.String DEFAULT_OPTION

      A constant that represents a default load.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SYNCH_OPTION

          public static final java.lang.String SYNCH_OPTION

      A constant that represents a synchronized load.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### NO_SYNCH_OPTION

          public static final java.lang.String NO_SYNCH_OPTION

      A constant that represents an unsynchronized load.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PRUNE_OPTION

          public static final java.lang.String PRUNE_OPTION

      A constant that represents a pruned load.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### SERIAL_OPTION

          public static final java.lang.String SERIAL_OPTION

      A constant that represents a serial load.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PARALLEL_OPTION

          public static final java.lang.String PARALLEL_OPTION

      A constant that represents a parallel load.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### RETAIN_OPTION

          public static final java.lang.String RETAIN_OPTION

      A constant that represents a retain load.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DELTA

          public static final java.lang.String DELTA

      A constant that represents a DELTA load.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DELTA_ADD

          public static final java.lang.String DELTA_ADD

      A constant that represents a DELTA ADD load.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DELTA_SUBTRACT

          public static final java.lang.String DELTA_SUBTRACT

      A constant that represents a DELTA SBUTRACT load.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### DEFAULT

          public static final LoadCommand DEFAULT

      Produces a `LoadCommand` that executes a default load.

    <!-- -->

    - #### SYNCH

          public static final LoadCommand SYNCH

      Produces a `LoadCommand` that has the `SYNCH` option.

    <!-- -->

    - #### SERIAL

          public static final LoadCommand SERIAL

      Produces a `LoadCommand` that has the `SERIAL` option.

    <!-- -->

    - #### PARALLEL

          public static final LoadCommand PARALLEL

      Produces a `LoadCommand` that has the `PARALLEL` option.

    <!-- -->

    - #### NO_SYNCH

          public static final LoadCommand NO_SYNCH

      Produces a `LoadCommand` that has the `NO_SYNCH` option.

    <!-- -->

    - #### PRUNE

          public static final LoadCommand PRUNE

      Produces a `LoadCommand` that has the `PRUNE` option.

    <!-- -->

    - #### RETAIN

          public static final LoadCommand RETAIN

      Produces a `LoadCommand` that has the `RETAIN` option.

  <!-- -->

  - ### Constructor Detail

    - #### LoadCommand

          public LoadCommand()

      Creates a `LoadCommand` with the default load command option.

    <!-- -->

    - #### LoadCommand

          public LoadCommand(java.lang.String option)

      Creates a `LoadCommand` with the specified load command option.
      Parameters:
      `option` - A `String` that contains a load command option.

    <!-- -->

    - #### LoadCommand

          public LoadCommand(java.lang.String option,
                             Condition whereCondition)

      Creates a `LoadCommand` with the specified load command option and `WHERE` `Condition`.
      Parameters:
      `option` - A `String` that contains a load command option.

      `whereCondition` - A `Condition` that Oracle OLAP applies to the base table during the load.

    <!-- -->

    - #### LoadCommand

          public LoadCommand(java.lang.String option,
                             Condition whereCondition,
                             java.lang.String cubeMapName)

      Creates a `LoadCommand` with the specified load command option, `WHERE` `Condition`, and `CubeMap`. Use this contructor if you want to load data from a single `CubeMap` and to apply a `WHERE` `Condition`.
      Parameters:
      `option` - A `String` that contains a load command option.

      `whereCondition` - A `Condition` that Oracle OLAP applies to the base table during the load.

      `cubeMapName` - A `String` that contains the name of a `CubeMap` to use when loading the measure data for an `MdmCube`.

    <!-- -->

    - #### LoadCommand

          public LoadCommand(java.lang.String option,
                             java.lang.String deltaOption,
                             Condition whereCondition,
                             java.lang.String cubeMapName)

      Creates a `LoadCommand` with the specified load command option, `WHERE` `Condition`, and `CubeMap`. Use this contructor if you want to load data from a single `CubeMap` and to apply a `WHERE` `Condition`.
      Parameters:
      `option` - A `String` that contains a load command option.

      `option` - A `String` that contains a load delta option.

      `whereCondition` - A `Condition` that Oracle OLAP applies to the base table during the load.

      `cubeMapName` - A `String` that contains the name of a `CubeMap` to use when loading the measure data for an `MdmCube`.

    <!-- -->

    - #### LoadCommand

          public LoadCommand(java.lang.String option,
                             java.lang.String cubeMapName)

      Creates a `LoadCommand` with the specified load command option and `CubeMap`. Use this contructor if you want to load data from a single `CubeMap`.
      Parameters:
      `option` - A `String` that contains a load command option.

      `cubeMapName` - A `String` that contains the name of a `CubeMap` to use when loading the measure data for an `MdmCube`.

  <!-- -->

  - ### Method Detail

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitLoadCommand` method of the `SyntaxObjectVisitor` and passes that method this `LoadCommand` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitLoadCommand` method.

    <!-- -->

    - #### getCubeMapName

          public java.lang.String getCubeMapName()

      Gets the name of the `CubeMap` that is associated with this `LoadCommand`.
      Returns:
      A `String` that contains the name of the `CubeMap` associated with this `LoadCommand`.

    <!-- -->

    - #### getLoadOption

          public java.lang.String getLoadOption()

      Gets the load command option of this `LoadCommand`. For the default option, this method returns an empty string.
      Returns:
      A `String` that contains the load command option of this `LoadCommand`.

    <!-- -->

    - #### getDeltaOption

          public java.lang.String getDeltaOption()

      Gets the delta command option of this `LoadCommand`. For the default option, this method returns an empty string.
      Returns:
      A `String` that contains the delta command option of this `LoadCommand`.

    <!-- -->

    - #### getWhereCondition

          public Condition getWhereCondition()

      Gets the `Condition` of this `LoadCommand`. Oracle OLAP applies the `Condition` to the base table during the load.
      Returns:
      A `CONDITION` that Oracle OLAP applies while executing this `LoadCommand`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](LiteralExpression.md)
- [Next Class](ModelCommand.md)

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
