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

- [Prev Class](FunctionCondition.md)
- [Next Class](FunctionDescriptorArgument.md)

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

## Class FunctionDescriptor

- java.lang.Object

- - oracle.olapi.syntax.FunctionDescriptor

<!-- -->

-

  ------------------------------------------------------------------------



      public final class FunctionDescriptor
      extends java.lang.Object

  An object that describes the structure of an `Expression` function. A `FunctionDescriptor` contains information about a function, such as the function name and the data type of the value returned by the function. The name is returned by the `getFunctionName` method and the data type is returned by the `getFunctionReturnType method`.
  Most `FunctionDescriptor` objects contain one or more `FunctionDescriptorArgument` objects that represent the required or optional arguments that apply to the function. The arguments are returned by the `getArguments` method.

  A `FunctionDescriptor` has a category, such as `DATETIME` or `NUMERIC`, and a function type, which is one of the fields of this class, such as `OLAP_FUNCTION`. The class has methods that get the category and function type. It also has methods that indicate whether the function applies to an analytic workspace, and whether the function described is a pseudocolumn.

  Oracle OLAP creates instances of this class when an application creates an `Expression` or uses a method that returns an `Expression`. An application can get the `FunctionDescriptor` for `TypedExpression` classes that have a `getFunctionDescriptor` method, such as `OLAPFunctionExpression` and `RowFunctionExpression`.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                                                                                                        |
    |-------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
    | `static int`      | `AGGREGATION_EXPRESSION_FUNCTION`<br>A constant that represents an aggregation function that is used by an AggregationFunctionExpression.    |
    | `static int`      | `AGGREGATION_FUNCTION`<br>A constant that represents an aggregation function, such as `MAX` or `SUM`, that is used by an AggregationCommand. |
    | `static int`      | `ALLOCATION_FUNCTION`<br>A constant that represents an allocation function, such as `MIN_ALLOC` or `FIRST_ALLOC`.                            |
    | `static int`      | `CONDITION_FUNCTION`<br>A constant that represents an condition function, such as `HIER_HAS_CHILDREN` or `EQUALS_PATH`.                      |
    | `static int`      | `FORECAST_FUNCTION`<br>A constant that represents an forecasting function, such as `FORECAST` or `FORECAST_SEASONAL`.                        |
    | `static int`      | `OLAP_FUNCTION`<br>A constant that represents an OLAP function, such as `HIER_PARENT` or `SHARE`.                                            |
    | `static int`      | `OLAP_HIER_FUNCTION`<br>A constant that represents an hierarchical OLAP function, such as `LAG` or `RANK`.                                   |
    | `static int`      | `PSEUDO_COLUMN_FUNCTION`<br>A constant that represents a pseudocolumn function, such as `SYSDATE` or `USER`.                                 |
    | `static int`      | `QUERY_FUNCTION`<br>A constant that represents an query function, such as `HIER_ANCESTORS` or `HIER_SIBLINGS`.                               |
    | `static int`      | `ROW_FUNCTION`<br>A constant that represents a row function, such as `ABS` or `LENGTH`.                                                      |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                 | Method and Description                                                                                                                          |
    |-------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`FunctionDescriptorArgument`](FunctionDescriptorArgument.md)`[]` | `getArguments``()`<br>Gets the function descriptor arguments that are associated with this `FunctionDescriptor`.                                |
    | `java.lang.String`                                                | `getCategory``()`<br>Gets the name of the category of the function that is associated with this `FunctionDescriptor`.                           |
    | `java.lang.String`                                                | `getFunctionName``()`<br>Gets the name of the function that is associated with this `FunctionDescriptor`.                                       |
    | [`DataType`](DataType.md)                                         | `getFunctionReturnType``()`<br>Gets the data type of the value returned by the function.                                                        |
    | `int`                                                             | `getFunctionType``()`<br>Gets the type of the function, which is one of the constants of this class, such as `FunctionDescriptor.ROW_FUNCTION`. |
    | `boolean`                                                         | `isAWFunction``()`<br>Indicates whether the function applies to an analytic workspace deployment.                                               |
    | `boolean`                                                         | `isPseudoColumn``()`<br>Indicates whether this `FunctionDescriptor` is associated with a pseudocolumn function.                                 |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### PSEUDO_COLUMN_FUNCTION

          public static final int PSEUDO_COLUMN_FUNCTION

      A constant that represents a pseudocolumn function, such as `SYSDATE` or `USER`.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ROW_FUNCTION

          public static final int ROW_FUNCTION

      A constant that represents a row function, such as `ABS` or `LENGTH`.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### OLAP_FUNCTION

          public static final int OLAP_FUNCTION

      A constant that represents an OLAP function, such as `HIER_PARENT` or `SHARE`.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### OLAP_HIER_FUNCTION

          public static final int OLAP_HIER_FUNCTION

      A constant that represents an hierarchical OLAP function, such as `LAG` or `RANK`.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### AGGREGATION_FUNCTION

          public static final int AGGREGATION_FUNCTION

      A constant that represents an aggregation function, such as `MAX` or `SUM`, that is used by an AggregationCommand.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### ALLOCATION_FUNCTION

          public static final int ALLOCATION_FUNCTION

      A constant that represents an allocation function, such as `MIN_ALLOC` or `FIRST_ALLOC`.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### FORECAST_FUNCTION

          public static final int FORECAST_FUNCTION

      A constant that represents an forecasting function, such as `FORECAST` or `FORECAST_SEASONAL`.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### CONDITION_FUNCTION

          public static final int CONDITION_FUNCTION

      A constant that represents an condition function, such as `HIER_HAS_CHILDREN` or `EQUALS_PATH`.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### QUERY_FUNCTION

          public static final int QUERY_FUNCTION

      A constant that represents an query function, such as `HIER_ANCESTORS` or `HIER_SIBLINGS`.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### AGGREGATION_EXPRESSION_FUNCTION

          public static final int AGGREGATION_EXPRESSION_FUNCTION

      A constant that represents an aggregation function that is used by an AggregationFunctionExpression.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getFunctionName

          public final java.lang.String getFunctionName()

      Gets the name of the function that is associated with this `FunctionDescriptor`.
      Returns:
      A `String` that contains the name of the function associated with this `FunctionDescriptor`.

    <!-- -->

    - #### getCategory

          public final java.lang.String getCategory()

      Gets the name of the category of the function that is associated with this `FunctionDescriptor`. Examples of catgory names are `HIERARCHICAL`, `NUMERIC`, and `CHARACTER`.
      Returns:
      A `String` that contains the name of the category of the function associated with this `FunctionDescriptor`.

    <!-- -->

    - #### isAWFunction

          public final boolean isAWFunction()

      Indicates whether the function applies to an analytic workspace deployment.
      Returns:
      A `boolean` that is `true` if the function applies to an analytic workspace or `false` if it does not.

    <!-- -->

    - #### getArguments

          public final FunctionDescriptorArgument[] getArguments()

      Gets the function descriptor arguments that are associated with this `FunctionDescriptor`.
      Returns:
      An array of the `FunctionDescriptorArgument` objects associated with this `FunctionDescriptor`.

    <!-- -->

    - #### getFunctionReturnType

          public final DataType getFunctionReturnType()

      Gets the data type of the value returned by the function. This method returns `null` if the function does not return a typed value or if the return type varies depending on the arguments. For example, for the `HIER_HAS_CHILDREN` function, which is a condition function, this method returns `null`.
      Returns:
      A `DataType` that represents the data type of the value returned by the function.

    <!-- -->

    - #### getFunctionType

          public int getFunctionType()

      Gets the type of the function, which is one of the constants of this class, such as `FunctionDescriptor.ROW_FUNCTION`.
      Returns:
      An integer that is the value of one of the constants of this class.

    <!-- -->

    - #### isPseudoColumn

          public boolean isPseudoColumn()

      Indicates whether this `FunctionDescriptor` is associated with a pseudocolumn function.
      Returns:
      A `boolean` that is `true` if this `FunctionDescriptor` is associated with a pseudocolumn function or `false` if it is not.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](FunctionCondition.md)
- [Next Class](FunctionDescriptorArgument.md)

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
