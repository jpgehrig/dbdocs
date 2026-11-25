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

- [Prev Class](AggregateOverMembersClause.md)
- [Next Class](AggregationCommand.md)

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

## Class AggregationCase

- java.lang.Object

- - [oracle.olapi.syntax.SyntaxObject](SyntaxObject.md)

  - - oracle.olapi.syntax.AggregationCase

<!-- -->

-

  ------------------------------------------------------------------------



      public final class AggregationCase
      extends SyntaxObject

  A `SyntaxObject` that represents an aggregation case for an `AggregationCommand`. An `AggregationCase` specifies a method of aggregation for a measure.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                                                                                                                                                                                                       |
    |-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `AggregationCase``(java.lang.String functionName, `[`FunctionArgument`](FunctionArgument.md)`[] args, `[`MdmBaseMeasure`](../metadata/mdm/MdmBaseMeasure.md)` measure)`<br>Creates an `AggregationCase` that has the specified function, with function arguments, as the aggregation method for the specified measure.                                            |
    | `AggregationCase``(java.lang.String functionName, `[`FunctionArgument`](FunctionArgument.md)`[] args, `[`TypedExpression`](TypedExpression.md)` aggregationSwitchValue)`<br>Creates an `AggregationCase` that has the specified function, with function arguments, as the aggregation method for the specified dimension member or attribute value.               |
    | `AggregationCase``(java.lang.String functionName, java.util.List<`[`FunctionArgument`](FunctionArgument.md)`> args, `[`MdmBaseMeasure`](../metadata/mdm/MdmBaseMeasure.md)` measure)`<br>Creates an `AggregationCase` that has the specified function, with function arguments, as the aggregation method for the specified measure.                              |
    | `AggregationCase``(java.lang.String functionName, java.util.List<`[`FunctionArgument`](FunctionArgument.md)`> args, `[`TypedExpression`](TypedExpression.md)` aggregationSwitchValue)`<br>Creates an `AggregationCase` that has the specified function, with function arguments, as the aggregation method for the specified dimension member or attribute value. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                     | Method and Description                                                                                                                                                                                                                |
    |-------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`TypedExpression`](TypedExpression.md)               | `getAggregationSwitchValue``()`<br>Gets the dimension member or attribute value that is associated with this `AggregationCase`.                                                                                                       |
    | [`FunctionArgument`](FunctionArgument.md)`[]`         | `getArguments``()`<br>Gets the function arguments contained by this `AggregationCase`.                                                                                                                                                |
    | [`FunctionDescriptor`](FunctionDescriptor.md)         | `getFunctionDescriptor``()`<br>Gets the function descriptor associated with this `AggregationCase`.                                                                                                                                   |
    | `java.lang.String`                                    | `getFunctionName``()`<br>Gets the name of the function for this `AggregationCase`.                                                                                                                                                    |
    | [`MdmBaseMeasure`](../metadata/mdm/MdmBaseMeasure.md) | `getMeasure``()`<br>Gets the measure that is associated with this `AggregationCase`.                                                                                                                                                  |
    | `java.lang.String`                                    | `getMeasureID``()`<br>Gets the ID of the measure that is associated with this `AggregationCase`.                                                                                                                                      |
    | `java.lang.Object`                                    | `visit``(`[`SyntaxObjectVisitor`](SyntaxObjectVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitAggregationCase` method of the `SyntaxObjectVisitor` and passes that method this `AggregationCase` and an `Object`. |

    - ### Methods inherited from class oracle.olapi.syntax.[SyntaxObject](SyntaxObject.md)

      [`equals`](SyntaxObject.md)`, `[`equals`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`fromSyntax`](SyntaxObject.md)`, `[`isValid`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)`, `[`toSyntax`](SyntaxObject.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### AggregationCase

          public AggregationCase(java.lang.String functionName,
                                 java.util.List<FunctionArgument> args,
                                 MdmBaseMeasure measure)

      Creates an `AggregationCase` that has the specified function, with function arguments, as the aggregation method for the specified measure.
      Parameters:
      `functionName` - A `String` that contains the name of the function to use to aggregate the data of the measure.

      `args` - A `List` of `FunctionArgument` objects that modify the function.

      `measure` - The `MdmBaseMeasure` to which to apply the aggregation.

    <!-- -->

    - #### AggregationCase

          public AggregationCase(java.lang.String functionName,
                                 FunctionArgument[] args,
                                 MdmBaseMeasure measure)

      Creates an `AggregationCase` that has the specified function, with function arguments, as the aggregation method for the specified measure.
      Parameters:
      `functionName` - A `String` that contains the name of the function to use to aggregate the data of the measure.

      `args` - An array of `FunctionArgument` objects that modify the function.

      `measure` - The `MdmBaseMeasure` to which to apply the aggregation.

    <!-- -->

    - #### AggregationCase

          public AggregationCase(java.lang.String functionName,
                                 java.util.List<FunctionArgument> args,
                                 TypedExpression aggregationSwitchValue)

      Creates an `AggregationCase` that has the specified function, with function arguments, as the aggregation method for the specified dimension member or attribute value.
      Parameters:
      `functionName` - A `String` that contains the name of the function to use to aggregate the data of the measure.

      `args` - A `List` of `FunctionArgument` objects that modify the function.

      `aggregationSwitchValue` - A `TypedExpression` that evaluates to a dimension member or attribute value for which to apply the aggregation.

    <!-- -->

    - #### AggregationCase

          public AggregationCase(java.lang.String functionName,
                                 FunctionArgument[] args,
                                 TypedExpression aggregationSwitchValue)

      Creates an `AggregationCase` that has the specified function, with function arguments, as the aggregation method for the specified dimension member or attribute value.
      Parameters:
      `functionName` - A `String` that contains the name of the function to use to aggregate the data of the measure.

      `args` - An array of `FunctionArgument` objects that modify the function.

      `aggregationSwitchValue` - A `TypedExpression` that evaluates to a dimension member or attribute value for which to apply the aggregation.

  <!-- -->

  - ### Method Detail

    - #### getArguments

          public FunctionArgument[] getArguments()

      Gets the function arguments contained by this `AggregationCase`.
      Returns:
      An array of the `FunctionArgument` of this `AggregationCase`.

    <!-- -->

    - #### getFunctionDescriptor

          public FunctionDescriptor getFunctionDescriptor()

      Gets the function descriptor associated with this `AggregationCase`.
      Returns:
      The `FunctionDescriptor` for this `AggregationCase`.

    <!-- -->

    - #### getFunctionName

          public java.lang.String getFunctionName()

      Gets the name of the function for this `AggregationCase`.
      Returns:
      A `String` that contains the name of the function for this `AggregationCase`.

    <!-- -->

    - #### getMeasure

          public MdmBaseMeasure getMeasure()

      Gets the measure that is associated with this `AggregationCase`.
      Returns:
      The `MdmBaseMeasure` associated with this `AggregationCase`.

    <!-- -->

    - #### getMeasureID

          public java.lang.String getMeasureID()

      Gets the ID of the measure that is associated with this `AggregationCase`.
      Returns:
      A `String` that contains the ID of the `MdmBaseMeasure` associated with this `AggregationCase`.

    <!-- -->

    - #### getAggregationSwitchValue

          public TypedExpression getAggregationSwitchValue()

      Gets the dimension member or attribute value that is associated with this `AggregationCase`.
      Returns:
      The `TypedExpression` that evaluates to a dimension member or attribute value of the `MdmPrimaryDimension` of the `AggregationCase`.

    <!-- -->

    - #### visit

          public java.lang.Object visit(SyntaxObjectVisitor visitor,
                                        java.lang.Object context)

      Calls the `visitAggregationCase` method of the `SyntaxObjectVisitor` and passes that method this `AggregationCase` and an `Object`.
      Specified by:
      [`visit`](SyntaxObject.md) in class [`SyntaxObject`](SyntaxObject.md)

      Parameters:
      `visitor` - A `SyntaxObjectVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitAggregationCase` method.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](AggregateOverMembersClause.md)
- [Next Class](AggregationCommand.md)

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
