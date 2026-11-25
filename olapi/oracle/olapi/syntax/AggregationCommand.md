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

- [Prev Class](AggregationCase.md)
- [Next Class](AggregationFunctionExpression.md)

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

## Class AggregationCommand

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - [oracle.olapi.syntax.BuildCommand](BuildCommand.md)

    - - [oracle.olapi.syntax.SimpleCommand](SimpleCommand.md)

      - - [oracle.olapi.syntax.SolveStepCommand](SolveStepCommand.md)

        - - oracle.olapi.syntax.AggregationCommand

<!-- -->

- All Implemented Interfaces:
  [ConsistentSolveCommand](ConsistentSolveCommand.md)

  ------------------------------------------------------------------------



      public final class AggregationCommand
      extends SolveStepCommand
      implements ConsistentSolveCommand

  A `SolveStepCommand` that represents an aggregation command in a `BuildSpecification`.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                                                                                     |
    |-------------------|---------------------------------------------------------------------------------------------------------------------------|
    | `static boolean`  | `ALLOW_DIVISION_BY_ZERO_DEFAULT`<br>A constant that indicates whether the aggregation allows division by zero by default. |
    | `static boolean`  | `ALLOW_OVERFLOW_DEFAULT`<br>A constant that indicates whether the aggregation allows overflow by default.                 |
    | `static boolean`  | `IGNORE_NULLS_DEFAULT`<br>A constant that indicates whether the aggregation ignores `null` values by default.             |
    | `static boolean`  | `MAINTAIN_COUNT_DEFAULT`<br>A constant that indicates whether the aggregation maintains a count by default.               |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `AggregationCommand``(java.lang.String functionName)`<br>Creates an `AggregationCommand` that specifies the aggregation of all of the summary data of the measures of a cube.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `AggregationCommand``(java.lang.String functionName, `[`FunctionArgument`](FunctionArgument.md)`[] args, `[`AggregationCase`](AggregationCase.md)`[] aggCases, `[`MdmPrimaryDimension`](../metadata/mdm/MdmPrimaryDimension.md)` dim, `[`MdmHierarchy`](../metadata/mdm/MdmHierarchy.md)`[] hiers, boolean ignoreNulls, boolean allowOverflow, boolean allowDivisionByZero, boolean maintainCount)`<br>Creates an `AggregationCommand` that specifies the aggregation of the summary data of the measures of a cube for the specified dimension hierarchies and that has the characteristics specified by the `boolean` parameters.                                                                                                                                                                                                                                                                                                            |
    | `AggregationCommand``(java.lang.String functionName, `[`FunctionArgument`](FunctionArgument.md)`[] args, `[`AggregationCase`](AggregationCase.md)`[] aggCases, `[`MdmPrimaryDimension`](../metadata/mdm/MdmPrimaryDimension.md)` dim, `[`MdmHierarchy`](../metadata/mdm/MdmHierarchy.md)`[] hiers, boolean ignoreNulls, boolean allowOverflow, boolean allowDivisionByZero, boolean maintainCount, `[`Condition`](Condition.md)` membersCondition)`<br>Creates an `AggregationCommand` that specifies the aggregation of the summary data of the measures of a cube for the specified dimension hierarchies, that specifies a floor for the aggregation, and that has the characteristics specified by the `boolean` parameters.                                                                                                                                                                                                               |
    | `AggregationCommand``(java.lang.String functionName, `[`FunctionArgument`](FunctionArgument.md)`[] args, `[`MdmPrimaryDimension`](../metadata/mdm/MdmPrimaryDimension.md)` dim)`<br>Creates an `AggregationCommand` that specifies the aggregation of the summary data of the measures of a cube for the specified dimension.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `AggregationCommand``(java.lang.String functionName, `[`FunctionArgument`](FunctionArgument.md)`[] args, `[`MdmPrimaryDimension`](../metadata/mdm/MdmPrimaryDimension.md)` dim, `[`MdmHierarchy`](../metadata/mdm/MdmHierarchy.md)`[] hiers)`<br>Creates an `AggregationCommand` that specifies the aggregation of the summary data of the measures of a cube for the specified dimension hierarchies.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `AggregationCommand``(java.lang.String functionName, java.util.List<`[`FunctionArgument`](FunctionArgument.md)`> args, java.util.List<`[`AggregationCase`](AggregationCase.md)`> aggCases, `[`MdmPrimaryDimension`](../metadata/mdm/MdmPrimaryDimension.md)` dim, java.util.List<`[`MdmHierarchy`](../metadata/mdm/MdmHierarchy.md)`> hiers, boolean ignoreNulls, boolean allowOverflow, boolean allowDivisionByZero, boolean maintainCount)`<br>Creates an `AggregationCommand` that specifies the aggregation of the summary data of the measures of a cube for the specified dimension hierarchies and that has the characteristics specified by the `boolean` parameters.                                                                                                                                                                                                                                                                  |
    | `AggregationCommand``(java.lang.String functionName, java.util.List<`[`FunctionArgument`](FunctionArgument.md)`> args, java.util.List<`[`AggregationCase`](AggregationCase.md)`> aggCases, `[`MdmPrimaryDimension`](../metadata/mdm/MdmPrimaryDimension.md)` dim, java.util.List<`[`MdmHierarchy`](../metadata/mdm/MdmHierarchy.md)`> hiers, boolean ignoreNulls, boolean allowOverflow, boolean allowDivisionByZero, boolean maintainCount, `[`Condition`](Condition.md)` membersCondition)`<br>Creates an `AggregationCommand` that specifies the aggregation of the summary data of the measures of a cube for the specified dimension hierarchies, that specifies a floor for the aggregation, and that has the characteristics specified by the `boolean` parameters.                                                                                                                                                                     |
    | `AggregationCommand``(java.lang.String functionName, java.util.List<`[`FunctionArgument`](FunctionArgument.md)`> args, java.util.List<`[`AggregationCase`](AggregationCase.md)`> aggCases, `[`MdmPrimaryDimension`](../metadata/mdm/MdmPrimaryDimension.md)` dim, java.util.List<`[`MdmHierarchy`](../metadata/mdm/MdmHierarchy.md)`> hiers, boolean ignoreNulls, boolean allowOverflow, boolean allowDivisionByZero, boolean maintainCount, `[`Condition`](Condition.md)` membersCondition, `[`MdmBaseAttribute`](../metadata/mdm/MdmBaseAttribute.md)` aggregationSwitch)`<br>Creates an `AggregationCommand` that specifies the aggregation of the summary data of the measures of a cube for the specified dimension hierarchies, that has the characteristics specified by the `boolean` parameters, that specifies a floor for the aggregation, and that specifies an attribute by which varying aggregation methods are specified.      |
    | `AggregationCommand``(java.lang.String functionName, java.util.List<`[`FunctionArgument`](FunctionArgument.md)`> args, java.util.List<`[`AggregationCase`](AggregationCase.md)`> aggCases, `[`MdmPrimaryDimension`](../metadata/mdm/MdmPrimaryDimension.md)` dim, java.util.List<`[`MdmHierarchy`](../metadata/mdm/MdmHierarchy.md)`> hiers, boolean ignoreNulls, boolean allowOverflow, boolean allowDivisionByZero, boolean maintainCount, `[`Condition`](Condition.md)` membersCondition, `[`MdmPrimaryDimension`](../metadata/mdm/MdmPrimaryDimension.md)` aggregationSwitch)`<br>Creates an `AggregationCommand` that specifies the aggregation of the summary data of the measures of a cube for the specified dimension hierarchies, that has the characteristics specified by the `boolean` parameters, that specifies a floor for the aggregation, and that specifies a dimension by which varying aggregation methods are specified. |
    | `AggregationCommand``(java.lang.String functionName, java.util.List<`[`FunctionArgument`](FunctionArgument.md)`> args, `[`MdmPrimaryDimension`](../metadata/mdm/MdmPrimaryDimension.md)` dim, java.util.List<`[`MdmHierarchy`](../metadata/mdm/MdmHierarchy.md)`> hiers)`<br>Creates an `AggregationCommand` that specifies the aggregation of the summary data of the measures of a cube for the specified dimension hierarchies.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                               | Method and Description                                                                                                                                                                                                                      |
    |-----------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`AggregationCase`](AggregationCase.md)`[]`                     | `getAggregationCases``()`<br>Gets the `AggregationCase` objects that are associated with this `AggregationCommand`.                                                                                                                         |
    | [`MdmObject`](../metadata/mdm/MdmObject.md)                     | `getAggregationSwitch``()`<br>Gets the aggregation switch that is associated with this `AggregationCommand`.                                                                                                                                |
    | `java.lang.String`                                              | `getAggregationSwitchID``()`<br>Gets the ID of the aggregation switch that is associated with this `AggregationCommand`.                                                                                                                    |
    | `boolean`                                                       | `getAllowDivisionByZero``()`<br>Indicates whether the aggregation allows division by zero.                                                                                                                                                  |
    | `boolean`                                                       | `getAllowOverflow``()`<br>Indicates whether the aggregation allows overflows.                                                                                                                                                               |
    | [`MdmHierarchy`](../metadata/mdm/MdmHierarchy.md)`[]`           | `getHierarchies``()`<br>Gets the hierarchies that are associated with this `AggregationCommand`.                                                                                                                                            |
    | `java.lang.String[]`                                            | `getHierarchyIDs``()`<br>Gets the IDs of the hierarchies that are associated with this `AggregationCommand`.                                                                                                                                |
    | `boolean`                                                       | `getIgnoreNulls``()`<br>Indicates whether the aggregation ignores `null` values.                                                                                                                                                            |
    | `boolean`                                                       | `getMaintainCount``()`<br>Indicates whether the aggregation maintains a count.                                                                                                                                                              |
    | [`Condition`](Condition.md)                                     | `getMembersCondition``()`<br>Gets a `Condition` that specifies a set of dimension members to use as a floor for the aggregation.                                                                                                            |
    | [`MdmPrimaryDimension`](../metadata/mdm/MdmPrimaryDimension.md) | `getPrimaryDimension``()`<br>Gets the dimension that is associated with this `AggregationCommand`.                                                                                                                                          |
    | `java.lang.String`                                              | `getPrimaryDimensionID``()`<br>Gets the ID of the dimension that is associated with this `AggregationCommand`.                                                                                                                              |
    | `java.lang.Object`                                              | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitAggregationCommand` method of the `SyntaxObjectVisitor` and passes that method this `AggregationCommand` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[SolveStepCommand](SolveStepCommand.md)

      [`getArguments`](SolveStepCommand.md)`, `[`getFunctionDescriptor`](SolveStepCommand.md)`, `[`getFunctionName`](SolveStepCommand.md)

    <!-- -->

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### IGNORE_NULLS_DEFAULT

          public static final boolean IGNORE_NULLS_DEFAULT

      A constant that indicates whether the aggregation ignores `null` values by default.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ALLOW_OVERFLOW_DEFAULT

          public static final boolean ALLOW_OVERFLOW_DEFAULT

      A constant that indicates whether the aggregation allows overflow by default.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ALLOW_DIVISION_BY_ZERO_DEFAULT

          public static final boolean ALLOW_DIVISION_BY_ZERO_DEFAULT

      A constant that indicates whether the aggregation allows division by zero by default.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### MAINTAIN_COUNT_DEFAULT

          public static final boolean MAINTAIN_COUNT_DEFAULT

      A constant that indicates whether the aggregation maintains a count by default.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### AggregationCommand

          public AggregationCommand(java.lang.String functionName)

      Creates an `AggregationCommand` that specifies the aggregation of all of the summary data of the measures of a cube.
      Parameters:
      `functionName` - A `String` that contains the name of the function to use for the aggregation.

    <!-- -->

    - #### AggregationCommand

          public AggregationCommand(java.lang.String functionName,
                                    FunctionArgument[] args,
                                    MdmPrimaryDimension dim)

      Creates an `AggregationCommand` that specifies the aggregation of the summary data of the measures of a cube for the specified dimension.
      Parameters:
      `functionName` - A `String` that contains the name of the function to use for the aggregation.

      `args` - An array of `FunctionArgument` objects that specify aspects of the aggregation.

      `dim` - The `MdmPrimaryDimension` for which to aggregate the measure values.

    <!-- -->

    - #### AggregationCommand

          public AggregationCommand(java.lang.String functionName,
                                    FunctionArgument[] args,
                                    MdmPrimaryDimension dim,
                                    MdmHierarchy[] hiers)

      Creates an `AggregationCommand` that specifies the aggregation of the summary data of the measures of a cube for the specified dimension hierarchies.
      Parameters:
      `functionName` - A `String` that contains the name of the function to use for the aggregation.

      `args` - An array of `FunctionArgument` objects that specify aspects of the aggregation.

      `dim` - The `MdmPrimaryDimension` for which to aggregate the measure values.

      `hiers` - An array of `MdmHierarchy` objects for which to aggregate the measure values.

    <!-- -->

    - #### AggregationCommand

          public AggregationCommand(java.lang.String functionName,
                                    FunctionArgument[] args,
                                    AggregationCase[] aggCases,
                                    MdmPrimaryDimension dim,
                                    MdmHierarchy[] hiers,
                                    boolean ignoreNulls,
                                    boolean allowOverflow,
                                    boolean allowDivisionByZero,
                                    boolean maintainCount)

      Creates an `AggregationCommand` that specifies the aggregation of the summary data of the measures of a cube for the specified dimension hierarchies and that has the characteristics specified by the `boolean` parameters.
      Parameters:
      `functionName` - A `String` that contains the name of the function to use for the aggregation.

      `args` - An array of `FunctionArgument` objects that specify aspects of the aggregation.

      `aggCases` - An array of `AggregationCase` objects that redefine the aggregation for specific measures.

      `dim` - The `MdmPrimaryDimension` for which to aggregate the measure values.

      `hiers` - An array of `MdmHierarchy` objects for which to aggregate the measure values.

      `ignoreNulls` - A `boolean` that is `true` to ignore null values or `false` to not ignore them.

      `allowOverflow` - A `boolean` that is `true` to allow overflows or `false` to not allow them.

      `allowDivisionByZero` - A `boolean` that is `true` to allow division by zero or `false` to not allow it.

      `maintainCount` - A `boolean` that is `true` to maintain a count or `false` to not maintain one.

    <!-- -->

    - #### AggregationCommand

          public AggregationCommand(java.lang.String functionName,
                                    FunctionArgument[] args,
                                    AggregationCase[] aggCases,
                                    MdmPrimaryDimension dim,
                                    MdmHierarchy[] hiers,
                                    boolean ignoreNulls,
                                    boolean allowOverflow,
                                    boolean allowDivisionByZero,
                                    boolean maintainCount,
                                    Condition membersCondition)

      Creates an `AggregationCommand` that specifies the aggregation of the summary data of the measures of a cube for the specified dimension hierarchies, that specifies a floor for the aggregation, and that has the characteristics specified by the `boolean` parameters.
      Parameters:
      `functionName` - A `String` that contains the name of the function to use for the aggregation.

      `args` - An array of `FunctionArgument` objects that specify aspects of the aggregation.

      `aggCases` - An array of `AggregationCase` objects that redefine the aggregation for specific measures.

      `dim` - The `MdmPrimaryDimension` for which to aggregate the measure values.

      `hiers` - An array of `MdmHierarchy` objects for which to aggregate the measure values.

      `ignoreNulls` - A `boolean` that is `true` to ignore null values or `false` to not ignore them.

      `allowOverflow` - A `boolean` that is `true` to allow overflows or `false` to not allow them.

      `allowDivisionByZero` - A `boolean` that is `true` to allow division by zero or `false` to not allow it.

      `maintainCount` - A `boolean` that is `true` to maintain a count or `false` to not maintain one.

      `membersCondition` - A `Condition` that specifies a set of dimension members to use as a floor for aggregation.

    <!-- -->

    - #### AggregationCommand

          public AggregationCommand(java.lang.String functionName,
                                    java.util.List<FunctionArgument> args,
                                    java.util.List<AggregationCase> aggCases,
                                    MdmPrimaryDimension dim,
                                    java.util.List<MdmHierarchy> hiers,
                                    boolean ignoreNulls,
                                    boolean allowOverflow,
                                    boolean allowDivisionByZero,
                                    boolean maintainCount)

      Creates an `AggregationCommand` that specifies the aggregation of the summary data of the measures of a cube for the specified dimension hierarchies and that has the characteristics specified by the `boolean` parameters.
      Parameters:
      `functionName` - A `String` that contains the name of the function to use for the aggregation.

      `args` - A `List` of `FunctionArgument` objects that specify aspects of the aggregation.

      `aggCases` - A `List` of `AggregationCase` objects that redefine the aggregation for specific measures.

      `dim` - The `MdmPrimaryDimension` for which to aggregate the measure values.

      `hiers` - A `List` of `MdmHierarchy` objects for which to aggregate the measure values.

      `ignoreNulls` - A `boolean` that is `true` to ignore null values or `false` to not ignore them.

      `allowOverflow` - A `boolean` that is `true` to allow overflows or `false` to not allow them.

      `allowDivisionByZero` - A `boolean` that is `true` to allow division by zero or `false` to not allow it.

      `maintainCount` - A `boolean` that is `true` to maintain a count or `false` to not maintain one.

    <!-- -->

    - #### AggregationCommand

          public AggregationCommand(java.lang.String functionName,
                                    java.util.List<FunctionArgument> args,
                                    java.util.List<AggregationCase> aggCases,
                                    MdmPrimaryDimension dim,
                                    java.util.List<MdmHierarchy> hiers,
                                    boolean ignoreNulls,
                                    boolean allowOverflow,
                                    boolean allowDivisionByZero,
                                    boolean maintainCount,
                                    Condition membersCondition)

      Creates an `AggregationCommand` that specifies the aggregation of the summary data of the measures of a cube for the specified dimension hierarchies, that specifies a floor for the aggregation, and that has the characteristics specified by the `boolean` parameters.
      Parameters:
      `functionName` - A `String` that contains the name of the function to use for the aggregation.

      `args` - A `List` of `FunctionArgument` objects that specify aspects of the aggregation.

      `aggCases` - A `List` of `AggregationCase` objects that redefine the aggregation for specific measures.

      `dim` - The `MdmPrimaryDimension` for which to aggregate the measure values.

      `hiers` - A `List` of `MdmHierarchy` objects for which to aggregate the measure values.

      `ignoreNulls` - A `boolean` that is `true` to ignore null values or `false` to not ignore them.

      `allowOverflow` - A `boolean` that is `true` to allow overflows or `false` to not allow them.

      `allowDivisionByZero` - A `boolean` that is `true` to allow division by zero or `false` to not allow it.

      `maintainCount` - A `boolean` that is `true` to maintain a count or `false` to not maintain one.

      `membersCondition` - A `Condition` that specifies a set of dimension members to use as a floor for aggregation.

    <!-- -->

    - #### AggregationCommand

          public AggregationCommand(java.lang.String functionName,
                                    java.util.List<FunctionArgument> args,
                                    java.util.List<AggregationCase> aggCases,
                                    MdmPrimaryDimension dim,
                                    java.util.List<MdmHierarchy> hiers,
                                    boolean ignoreNulls,
                                    boolean allowOverflow,
                                    boolean allowDivisionByZero,
                                    boolean maintainCount,
                                    Condition membersCondition,
                                    MdmPrimaryDimension aggregationSwitch)

      Creates an `AggregationCommand` that specifies the aggregation of the summary data of the measures of a cube for the specified dimension hierarchies, that has the characteristics specified by the `boolean` parameters, that specifies a floor for the aggregation, and that specifies a dimension by which varying aggregation methods are specified.
      With the `aggregationSwitch`, you can vary the aggregation method by dimension member. You specify a dimension member with the `aggregationSwitchValue` of an `AggregationCase`. You specify the aggregation function to use for that member with the `functionName` parameter of the `AggregationCase`.

      If the `AggregationCommand` has an `AggregationCase` that has a null `aggregationSwitchValue`, then the aggregation varies by measure.

      Parameters:
      `functionName` - A `String` that contains the name of the function to use for the aggregation.

      `args` - A `List` of `FunctionArgument` objects that specify aspects of the aggregation.

      `aggCases` - A `List` of `AggregationCase` objects that redefine the aggregation for specific measures.

      `dim` - The `MdmPrimaryDimension` for which to aggregate the measure values.

      `hiers` - A `List` of `MdmHierarchy` objects for which to aggregate the measure values.

      `ignoreNulls` - A `boolean` that is `true` to ignore null values or `false` to not ignore them.

      `allowOverflow` - A `boolean` that is `true` to allow overflows or `false` to not allow them.

      `allowDivisionByZero` - A `boolean` that is `true` to allow division by zero or `false` to not allow it.

      `maintainCount` - A `boolean` that is `true` to maintain a count or `false` to not maintain one.

      `membersCondition` - A `Condition` that specifies a set of dimension members to use as a floor for aggregation.

      `aggregationSwitch` - The `MdmPrimaryDimension` by which varying aggregation methods are specified.

    <!-- -->

    - #### AggregationCommand

          public AggregationCommand(java.lang.String functionName,
                                    java.util.List<FunctionArgument> args,
                                    java.util.List<AggregationCase> aggCases,
                                    MdmPrimaryDimension dim,
                                    java.util.List<MdmHierarchy> hiers,
                                    boolean ignoreNulls,
                                    boolean allowOverflow,
                                    boolean allowDivisionByZero,
                                    boolean maintainCount,
                                    Condition membersCondition,
                                    MdmBaseAttribute aggregationSwitch)

      Creates an `AggregationCommand` that specifies the aggregation of the summary data of the measures of a cube for the specified dimension hierarchies, that has the characteristics specified by the `boolean` parameters, that specifies a floor for the aggregation, and that specifies an attribute by which varying aggregation methods are specified.
      With the `aggregationSwitch`, you can vary the aggregation method by attribute value. You specify an attribute value with the `aggregationSwitchValue` of an `AggregationCase`. You specify the aggregation function to use for that attribute value with the `functionName` parameter of the `AggregationCase`.

      If the `AggregationCommand` has an `AggregationCase` that has a null `aggregationSwitchValue`, then the aggregation varies by measure.

      Parameters:
      `functionName` - A `String` that contains the name of the function to use for the aggregation.

      `args` - A `List` of `FunctionArgument` objects that specify aspects of the aggregation.

      `aggCases` - A `List` of `AggregationCase` objects that redefine the aggregation for specific measures.

      `dim` - The `MdmPrimaryDimension` for which to aggregate the measure values.

      `hiers` - A `List` of `MdmHierarchy` objects for which to aggregate the measure values.

      `ignoreNulls` - A `boolean` that is `true` to ignore null values or `false` to not ignore them.

      `allowOverflow` - A `boolean` that is `true` to allow overflows or `false` to not allow them.

      `allowDivisionByZero` - A `boolean` that is `true` to allow division by zero or `false` to not allow it.

      `maintainCount` - A `boolean` that is `true` to maintain a count or `false` to not maintain one.

      `membersCondition` - A `Condition` that specifies a set of dimension members to use as a floor for aggregation.

      `aggregationSwitch` - The `MdmBaseAttribute` by which varying aggregation methods are specified.

    <!-- -->

    - #### AggregationCommand

          public AggregationCommand(java.lang.String functionName,
                                    java.util.List<FunctionArgument> args,
                                    MdmPrimaryDimension dim,
                                    java.util.List<MdmHierarchy> hiers)

      Creates an `AggregationCommand` that specifies the aggregation of the summary data of the measures of a cube for the specified dimension hierarchies.
      Parameters:
      `functionName` - A `String` that contains the name of the function to use for the aggregation.

      `args` - A `List` of `FunctionArgument` objects that specify aspects of the aggregation.

      `dim` - The `MdmPrimaryDimension` for which to aggregate the measure values.

      `hiers` - A `List` of `MdmHierarchy` objects for which to aggregate the measure values.

  <!-- -->

  - ### Method Detail

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitAggregationCommand` method of the `SyntaxObjectVisitor` and passes that method this `AggregationCommand` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitAggregationCommand` method.

    <!-- -->

    - #### getHierarchies

          public MdmHierarchy[] getHierarchies()

      Gets the hierarchies that are associated with this `AggregationCommand`.
      Returns:
      An array of the `MdmHierarchy` objects of this `AggregationCommand`.

    <!-- -->

    - #### getHierarchyIDs

          public java.lang.String[] getHierarchyIDs()

      Gets the IDs of the hierarchies that are associated with this `AggregationCommand`.
      Returns:
      An array of the `String` objects that contain the IDs of the `MdmHierarchy` objects of this `AggregationCommand`.

    <!-- -->

    - #### getAggregationCases

          public AggregationCase[] getAggregationCases()

      Gets the `AggregationCase` objects that are associated with this `AggregationCommand`.
      Returns:
      An array of the `AggregationCase` associated with this `AggregationCommand`.

    <!-- -->

    - #### getPrimaryDimension

          public MdmPrimaryDimension getPrimaryDimension()

      Gets the dimension that is associated with this `AggregationCommand`.
      Returns:
      The `MdmPrimaryDimension` of this `AggregationCommand`.

    <!-- -->

    - #### getPrimaryDimensionID

          public java.lang.String getPrimaryDimensionID()

      Gets the ID of the dimension that is associated with this `AggregationCommand`.
      Returns:
      A `String` that contains the ID of the dimension of this `AggregationCommand`.

    <!-- -->

    - #### getAggregationSwitch

          public MdmObject getAggregationSwitch()

      Gets the aggregation switch that is associated with this `AggregationCommand`.
      Returns:
      The `MdmObject` that is the aggregation switch of this `AggregationCommand`.

    <!-- -->

    - #### getAggregationSwitchID

          public java.lang.String getAggregationSwitchID()

      Gets the ID of the aggregation switch that is associated with this `AggregationCommand`.
      Returns:
      The `String` that contains the ID of the `MdmObject` that is the aggregation switch of this `AggregationCommand`.

    <!-- -->

    - #### getIgnoreNulls

          public boolean getIgnoreNulls()

      Indicates whether the aggregation ignores `null` values.
      Returns:
      A `boolean` that indicates whether the aggregation ignores `null` values.

    <!-- -->

    - #### getAllowOverflow

          public boolean getAllowOverflow()

      Indicates whether the aggregation allows overflows.
      Returns:
      A `boolean` that indicates whether the aggregation allows overflows.

    <!-- -->

    - #### getAllowDivisionByZero

          public boolean getAllowDivisionByZero()

      Indicates whether the aggregation allows division by zero.
      Returns:
      A `boolean` that indicates whether the aggregation allows division by zero.

    <!-- -->

    - #### getMaintainCount

          public boolean getMaintainCount()

      Indicates whether the aggregation maintains a count.
      Returns:
      A `boolean` that indicates whether the aggregation maintains a count.

    <!-- -->

    - #### getMembersCondition

          public Condition getMembersCondition()

      Gets a `Condition` that specifies a set of dimension members to use as a floor for the aggregation.
      Returns:
      A `Condition` that specifies a set of dimension members or `null` if this `AggregationCommand` does not have such a `Condition`.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](AggregationCase.md)
- [Next Class](AggregationFunctionExpression.md)

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
