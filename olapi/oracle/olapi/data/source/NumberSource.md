Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® OLAP Java API Reference
19c**
E96404-01

- [Prev Class](NumberParameter.md)
- [Next Class](Parameter.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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

oracle.olapi.data.source

## Class NumberSource

- java.lang.Object

- - [oracle.olapi.data.source.Source](Source.md)

  - - oracle.olapi.data.source.NumberSource

<!-- -->

- All Implemented Interfaces:
  [SourceIdentifier](../cursor/SourceIdentifier.md)

  ------------------------------------------------------------------------



      public final class NumberSource
      extends Source

  A `Source` whose elements have numeric values, which are `double`, `float`, `int`, or `short` values, or some combination of those values. Depending on the data type of its values, a `NumberSource` has an OLAP Java API data type of Double, Float, Integer, Short, or Number.
  The `NumberSource` class implements the following types of methods:

  - Some `Source` methods so that they use numeric values, such as `appendValue`.
  - Methods that perform numeric operations, such as `div`, `plus`, and `times`.
  - Methods that perform standard mathematical functions, such as `abs` and `average`.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from class oracle.olapi.data.source.[Source](Source.md)

      [`COMPARISON_RULE_ASCENDING`](Source.md)`, `[`COMPARISON_RULE_ASCENDING_NULLS_FIRST`](Source.md)`, `[`COMPARISON_RULE_ASCENDING_NULLS_LAST`](Source.md)`, `[`COMPARISON_RULE_DESCENDING`](Source.md)`, `[`COMPARISON_RULE_DESCENDING_NULLS_FIRST`](Source.md)`, `[`COMPARISON_RULE_DESCENDING_NULLS_LAST`](Source.md)`, `[`COMPARISON_RULE_REMOVE`](Source.md)`, `[`COMPARISON_RULE_SELECT`](Source.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                   | Method and Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    |-------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `NumberSource`                      | `abs``()`<br>Calculates the absolute value of the value of each element of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `NumberSource`                      | `appendValue``(double appendValue)`<br>Appends an element with the specified `double` value to this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `NumberSource`                      | `appendValue``(float appendValue)`<br>Appends an element with the specified `float` value to this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `NumberSource`                      | `appendValue``(int appendValue)`<br>Appends an element with the specified `int` value to this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `NumberSource`                      | `appendValue``(short appendValue)`<br>Appends an element with the specified `short` value to this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `NumberSource`                      | `appendValues``(double[] appendValues)`<br>Appends elements with the specified `double` values to this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `NumberSource`                      | `appendValues``(float[] appendValues)`<br>Appends elements with the specified `float` values to this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `NumberSource`                      | `appendValues``(int[] appendValues)`<br>Appends elements with the specified `int` values to this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `NumberSource`                      | `appendValues``(short[] appendValues)`<br>Appends elements with the specified `short` values to this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `NumberSource`                      | `arccos``()`<br>Calculates the angle value (in radians) of the value (interpreted as a cosine) of each element of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `NumberSource`                      | `arcsin``()`<br>Calculates the angle value (in radians) of the value (interpreted as a sine) of each element of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `NumberSource`                      | `arctan``()`<br>Calculates the angle value (in radians) of the value (interpreted as a tangent) of each element of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `NumberSource`                      | `average``()`<br>Calculates the average of the values of the elements of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `NumberSource`                      | `cos``()`<br>Calculates the cosine of the value (interpreted as an angle value in radians) of each element of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `NumberSource`                      | `cosh``()`<br>Calculates the hyperbolic cosine of the value (interpreted as an angle value in radians) of each element of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `NumberSource`                      | `cumulativeAverage``(`[`MdmLevelHierarchy`](../../metadata/mdm/MdmLevelHierarchy.md)` dimension, int offset)`<br>For each element of this `NumberSource`, calculates the average of the values of the elements of this `NumberSource` that are specified by the values of the elements of `dimension` that are at the same level of the hierarchy from the first element of `dimension` to the current element of `dimension` plus the number of elements specified by `offset`.                                                                                                                                                  |
    | `NumberSource`                      | `cumulativeAverage``(`[`MdmLevelHierarchy`](../../metadata/mdm/MdmLevelHierarchy.md)` dimension, int offset, `[`MdmLevel`](../../metadata/mdm/MdmLevel.md)` resetLevel)`<br>For each element of this `NumberSource`, calculates the average of the values of the elements of this `NumberSource` that are specified by the values of the elements of `dimension` that are at the same level of the hierarchy from the first element of `dimension` to the current element of `dimension` plus the number of elements specified by `offset`, with the cumulative average calculation reset at the level specified by `resetLevel`. |
    | `NumberSource`                      | `cumulativeMaximum``(`[`MdmLevelHierarchy`](../../metadata/mdm/MdmLevelHierarchy.md)` dimension, int offset)`<br>For each element of this `NumberSource`, calculates the maximum value of the elements of this `NumberSource` that are specified by the values of the elements of `dimension` that are at the same level of the hierarchy from the first element of `dimension` to the current element of `dimension` plus the number of elements specified by `offset`.                                                                                                                                                          |
    | `NumberSource`                      | `cumulativeMaximum``(`[`MdmLevelHierarchy`](../../metadata/mdm/MdmLevelHierarchy.md)` dimension, int offset, `[`MdmLevel`](../../metadata/mdm/MdmLevel.md)` resetLevel)`<br>For each element of this `NumberSource`, calculates the maximum value of the elements of this `NumberSource` that are specified by the values of the elements of `dimension` that are at the same level of the hierarchy from the first element of `dimension` to the current element of `dimension` plus the number of elements specified by `offset`, with the cumulative maximum calculation reset at the level specified by `resetLevel`.         |
    | `NumberSource`                      | `cumulativeMinimum``(`[`MdmLevelHierarchy`](../../metadata/mdm/MdmLevelHierarchy.md)` dimension, int offset)`<br>For each element of this `NumberSource`, calculates the minimum value of the elements of this `NumberSource` that are specified by the values of the elements of `dimension` that are at the same level of the hierarchy from the first element of `dimension` to the current element of `dimension` plus the number of elements specified by `offset`.                                                                                                                                                          |
    | `NumberSource`                      | `cumulativeMinimum``(`[`MdmLevelHierarchy`](../../metadata/mdm/MdmLevelHierarchy.md)` dimension, int offset, `[`MdmLevel`](../../metadata/mdm/MdmLevel.md)` resetLevel)`<br>For each element of this `NumberSource`, calculates the minimum value of the elements of this `NumberSource` that are specified by the values of the elements of `dimension` that are at the same level of the hierarchy from the first element of `dimension` to the current element of `dimension` plus the number of elements specified by `offset`, with the cumulative minimum calculation reset at the level specified by `resetLevel`.         |
    | `NumberSource`                      | `cumulativeTotal``(`[`MdmLevelHierarchy`](../../metadata/mdm/MdmLevelHierarchy.md)` dimension, int offset)`<br>For each element of this `NumberSource`, calculates the total of the values of the elements of this `NumberSource` that are specified by the values of the elements of `dimension` that are at the same level of the hierarchy from the first element of `dimension` to the current element of `dimension` plus the number of elements specified by `offset`.                                                                                                                                                      |
    | `NumberSource`                      | `cumulativeTotal``(`[`MdmLevelHierarchy`](../../metadata/mdm/MdmLevelHierarchy.md)` dimension, int offset, `[`MdmLevel`](../../metadata/mdm/MdmLevel.md)` resetLevel)`<br>For each element of this `NumberSource`, calculates the total of the values of the elements of this `NumberSource` that are specified by the values of the elements of `dimension` that are at the same level of the hierarchy from the first element of `dimension` to the current element of `dimension` plus the number of elements specified by `offset`, with the cumulative total calculation reset at the level specified by `resetLevel`.       |
    | `NumberSource`                      | `div``(double rhs)`<br>Divides the value of the elements of this `NumberSource` by the specified `double` value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `NumberSource`                      | `div``(double rhs, boolean safe)`<br>Divides the value of the elements of this `NumberSource` by the specified `double` value; if `safe` is `true` and the divisor is zero, then this method returns `null`.                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `NumberSource`                      | `div``(float rhs)`<br>Divides the value of the elements of this `NumberSource` by the specified `float` value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `NumberSource`                      | `div``(float rhs, boolean safe)`<br>Divides the value of the elements of this `NumberSource` by the specified `float` value; if `safe` is `true` and the divisor is zero, then this method returns `null`.                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `NumberSource`                      | `div``(int rhs)`<br>Divides the value of the elements of this `NumberSource` by the specified `int` value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `NumberSource`                      | `div``(int rhs, boolean safe)`<br>Divides the value of the elements of this `NumberSource` by the specified `int` value; if `safe` is `true` and the divisor is zero, then this method returns `null`.                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `NumberSource`                      | `div``(NumberSource rhs)`<br>Divides the value of the elements of this `NumberSource` by the values of the elements of the specified `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `NumberSource`                      | `div``(NumberSource rhs, boolean safe)`<br>Divides the value of the elements of this `NumberSource` by the values of the elements of the specified `NumberSource`; if `safe` is `true` and a divisor is zero, then this method returns `null` as the result of the division.                                                                                                                                                                                                                                                                                                                                                      |
    | `NumberSource`                      | `div``(short rhs)`<br>Divides the value of the elements of this `NumberSource` by the specified `short` value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `NumberSource`                      | `div``(short rhs, boolean safe)`<br>Divides the value of the elements of this `NumberSource` by the specified `short` value; if `safe` is `true` and the divisor is zero, then this method returns `null`.                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | [`BooleanSource`](BooleanSource.md) | `eq``(double rhs)`<br>Compares the value of each element of this `NumberSource` to the specified `double` value and determines if the values are equal.                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | [`BooleanSource`](BooleanSource.md) | `eq``(float rhs)`<br>Compares the value of each element of this `NumberSource` to the specified `float` value and determines if the values are equal.                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | [`BooleanSource`](BooleanSource.md) | `eq``(int rhs)`<br>Compares the value of each element of this `NumberSource` to the specified `int` value and determines if the values are equal.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | [`BooleanSource`](BooleanSource.md) | `eq``(short rhs)`<br>Compares the value of each element of this `NumberSource` to the specified `short` value and determines if the values are equal.                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | [`BooleanSource`](BooleanSource.md) | `ge``(double rhs)`<br>Compares the value of each element of this `NumberSource` to the specified `double` value, and determines whether it is a greater or equal value.                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | [`BooleanSource`](BooleanSource.md) | `ge``(float rhs)`<br>Compares the value of each element of this `NumberSource` to the specified `float` value, and determines whether it is a greater or equal value.                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | [`BooleanSource`](BooleanSource.md) | `ge``(int rhs)`<br>Compares the value of each element of this `NumberSource` to the specified `int` value, and determines whether it is a greater or equal value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | [`BooleanSource`](BooleanSource.md) | `ge``(short rhs)`<br>Compares the value of each element of this `NumberSource` to the specified `short` value, and determines whether it is a greater or equal value.                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | [`Source`](Source.md)               | `getDataType``()`<br>Gets the fundamental `Source` that represents the OLAP Java API data type of this `NumberSource`, which can be Double, Float, Integer, Number, or Short, depending on the values of its elements.                                                                                                                                                                                                                                                                                                                                                                                                            |
    | [`BooleanSource`](BooleanSource.md) | `gt``(double rhs)`<br>Compares the value of each element of this `NumberSource` to the specified `double` value, and determines whether it is a greater value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | [`BooleanSource`](BooleanSource.md) | `gt``(float rhs)`<br>Compares the value of each element of this `NumberSource` to the specified `float` value, and determines whether it is a greater value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | [`BooleanSource`](BooleanSource.md) | `gt``(int rhs)`<br>Compares the value of each element of this `NumberSource` to the specified `int` value, and determines whether it is a greater value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | [`BooleanSource`](BooleanSource.md) | `gt``(short rhs)`<br>Compares the value of each element of this `NumberSource` to the specified `short` value, and determines whether it is a greater value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `NumberSource`                      | `intpart``()`<br>Identifies the integer portion of the value of each element of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `NumberSource`                      | `lag``(`[`MdmLevelHierarchy`](../../metadata/mdm/MdmLevelHierarchy.md)` dimension, int offset)`<br>Selects the elements of this `NumberSource` that are specified by the values of the elements of `dimension` that are the `offset` number of values away from each value of the `dimension` hierarchy that is at the same level of the hierarchy.                                                                                                                                                                                                                                                                               |
    | `NumberSource`                      | `lagDays``(`[`MdmLevelHierarchy`](../../metadata/mdm/MdmLevelHierarchy.md)` timeDim, int offset)`<br>Selects the elements of this `NumberSource` that are specified by the day values of `timeDim` that are the `offset` number of days away from each day value of `timeDim`.                                                                                                                                                                                                                                                                                                                                                    |
    | `NumberSource`                      | `lagMonths``(`[`MdmLevelHierarchy`](../../metadata/mdm/MdmLevelHierarchy.md)` timeDim, int offset)`<br>Selects the elements of this `NumberSource` that are specified by the month values of `timeDim` that are the `offset` number of months away from each month value of `timeDim`.                                                                                                                                                                                                                                                                                                                                            |
    | `NumberSource`                      | `lagQuarters``(`[`MdmLevelHierarchy`](../../metadata/mdm/MdmLevelHierarchy.md)` timeDim, int offset)`<br>Selects the elements of this `NumberSource` that are specified by the quarter values of `timeDim` that are the `offset` number of quarters away from each quarter value of `timeDim`.                                                                                                                                                                                                                                                                                                                                    |
    | `NumberSource`                      | `lagWeeks``(`[`MdmLevelHierarchy`](../../metadata/mdm/MdmLevelHierarchy.md)` timeDim, int offset)`<br>Selects the elements of this `NumberSource` that are specified by the week values of `timeDim` that are the `offset` number of weeks away from each week value of `timeDim`.                                                                                                                                                                                                                                                                                                                                                |
    | `NumberSource`                      | `lagYears``(`[`MdmLevelHierarchy`](../../metadata/mdm/MdmLevelHierarchy.md)` timeDim, int offset)`<br>Selects the elements of this `NumberSource` that are specified by the year values of `timeDim` that are the `offset` number of years away from each year value of `timeDim`.                                                                                                                                                                                                                                                                                                                                                |
    | [`BooleanSource`](BooleanSource.md) | `le``(double rhs)`<br>Compares the value of each element of this `NumberSource` to the specified `double` value, and determines whether it is a lesser or equal value.                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | [`BooleanSource`](BooleanSource.md) | `le``(float rhs)`<br>Compares the value of each element of this `NumberSource` to the specified `float` value, and determines whether it is a lesser or equal value.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | [`BooleanSource`](BooleanSource.md) | `le``(int rhs)`<br>Compares the value of each element of this `NumberSource` to the specified `int` value, and determines whether it is a lesser or equal value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | [`BooleanSource`](BooleanSource.md) | `le``(short rhs)`<br>Compares the value of each element of this `NumberSource` to the specified `short` value, and determines whether it is a lesser or equal value.                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `NumberSource`                      | `lead``(`[`MdmLevelHierarchy`](../../metadata/mdm/MdmLevelHierarchy.md)` dimension, int offset)`<br>Selects the elements of this `NumberSource` that are specified by the values of the elements of `dimension` that are the `offset` number of values away from each value of the `dimension` hierarchy that is at the same level of the hierarchy.                                                                                                                                                                                                                                                                              |
    | `NumberSource`                      | `log``()`<br>Calculates the natural logarithm of the value of each element of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | [`BooleanSource`](BooleanSource.md) | `lt``(double rhs)`<br>Compares the value of each element of this `NumberSource` to the specified `double` value, and determines whether it is a lesser value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | [`BooleanSource`](BooleanSource.md) | `lt``(float rhs)`<br>Compares the value of each element of this `NumberSource` to the specified `float` value, and determines whether it is a lesser value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | [`BooleanSource`](BooleanSource.md) | `lt``(int rhs)`<br>Compares the value of each element of this `NumberSource` to the specified `int` value, and determines whether it is a lesser value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | [`BooleanSource`](BooleanSource.md) | `lt``(short rhs)`<br>Compares the value of each element of this `NumberSource` to the specified `short` value, and determines whether it is a lesser value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `NumberSource`                      | `maximum``()`<br>Identifies the largest value of the elements of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `NumberSource`                      | `median``()`<br>Calculates the median values of the elements of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `NumberSource`                      | `minimum``()`<br>Identifies the smallest value of the elements of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `NumberSource`                      | `minus``(double rhs)`<br>Subtracts the specified `double` value from the value of each element of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `NumberSource`                      | `minus``(float rhs)`<br>Subtracts the specified `float` value from the value of each element of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `NumberSource`                      | `minus``(int rhs)`<br>Subtracts the specified `int` value from the value of each element of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `NumberSource`                      | `minus``(NumberSource rhs)`<br>Subtracts the values of the elments of the specified `NumberSource` from the value of each element of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `NumberSource`                      | `minus``(short rhs)`<br>Subtracts the specified `short` value from the value of each element of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `NumberSource`                      | `movingAverage``(`[`MdmLevelHierarchy`](../../metadata/mdm/MdmLevelHierarchy.md)` dimension, int startOffset, int endOffset)`<br>For each element of this `NumberSource`, calculates the average of the values of the elements of this `NumberSource` that are specified by the values of the elements of `dimension` that are at the same level of the hierarchy from the element of `dimension` specified by `startOffset` to the element specified by `endOffset`.                                                                                                                                                             |
    | `NumberSource`                      | `movingMaximum``(`[`MdmLevelHierarchy`](../../metadata/mdm/MdmLevelHierarchy.md)` dimension, int startOffset, int endOffset)`<br>For each element of this `NumberSource`, determines the maximum value of the elements of this `NumberSource` that are specified by the values of the elements of `dimension` that are at the same level of the hierarchy from the element of `dimension` specified by `startOffset` to the element specified by `endOffset`.                                                                                                                                                                     |
    | `NumberSource`                      | `movingMinimum``(`[`MdmLevelHierarchy`](../../metadata/mdm/MdmLevelHierarchy.md)` dimension, int startOffset, int endOffset)`<br>For each element of this `NumberSource`, determines the minimum value of the elements of this `NumberSource` that are specified by the values of the elements of `dimension` that are at the same level of the hierarchy from the element of `dimension` specified by `startOffset` to the element specified by `endOffset`.                                                                                                                                                                     |
    | `NumberSource`                      | `movingTotal``(`[`MdmLevelHierarchy`](../../metadata/mdm/MdmLevelHierarchy.md)` dimension, int startOffset, int endOffset)`<br>For each element of this `NumberSource`, calculates the total of the values of the elements of this `NumberSource` that are specified by the values of the elements of `dimension` that are at the same level of the hierarchy from the element of `dimension` specified by `startOffset` to the element specified by `endOffset`.                                                                                                                                                                 |
    | [`BooleanSource`](BooleanSource.md) | `ne``(double rhs)`<br>Compares the value of each element of this `NumberSource` to the specified `double` value, and determines whether it is not equal to the value.                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | [`BooleanSource`](BooleanSource.md) | `ne``(float rhs)`<br>Compares the value of each element of this `NumberSource` to the specified `float` value, and determines whether it is not equal to the value.                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | [`BooleanSource`](BooleanSource.md) | `ne``(int rhs)`<br>Compares the value of each element of this `NumberSource` to the specified `int` value, and determines whether it is not equal to the value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | [`BooleanSource`](BooleanSource.md) | `ne``(short rhs)`<br>Compares the value of each element of this `NumberSource` to the specified `short` value, and determines whether it is not equal to the value.                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `NumberSource`                      | `negate``()`<br>Negates the value of each of the elements of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `NumberSource`                      | `plus``(double rhs)`<br>Adds the specified `double` value to the value of each element of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `NumberSource`                      | `plus``(float rhs)`<br>Adds the specified `float` value to the value of each element of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `NumberSource`                      | `plus``(int rhs)`<br>Adds the specified `int` value to the value of each element of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `NumberSource`                      | `plus``(NumberSource rhs)`<br>Adds the values of the elements of the specified `NumberSource` to the value of each element of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `NumberSource`                      | `plus``(short rhs)`<br>Adds the specified `short` value to the value of each element of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `NumberSource`                      | `positionalPeriodsAgo``(`[`MdmLevelHierarchy`](../../metadata/mdm/MdmLevelHierarchy.md)` hierarchy, `[`MdmLevel`](../../metadata/mdm/MdmLevel.md)` offsetLevel, int offset)`<br>Selects the elements of this `NumberSource` that are specified by the members of `offsetLevel` that are the `offset` number of positions away from each member of the `offsetLevel` level of the hierarchy.                                                                                                                                                                                                                                       |
    | `NumberSource`                      | `positionOfValue``(double value)`<br>Identifies the positions of elements in this `NumberSource` that have the specified `double` value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `NumberSource`                      | `positionOfValue``(float value)`<br>Identifies the positions of elements in this `NumberSource` that have the specified `float` value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `NumberSource`                      | `positionOfValue``(int value)`<br>Identifies the positions of elements in this `NumberSource` that have the specified `int` value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `NumberSource`                      | `positionOfValue``(short value)`<br>Identifies the positions of elements in this `NumberSource` that have the specified `short` value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `NumberSource`                      | `positionOfValues``(double[] values)`<br>Identifies the positions of elements in this `NumberSource` that have the specified `double` values.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `NumberSource`                      | `positionOfValues``(float[] values)`<br>Identifies the positions of elements in this `NumberSource` that have the specified `float` values.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `NumberSource`                      | `positionOfValues``(int[] values)`<br>Identifies the positions of elements in this `NumberSource` that have the specified `int` values.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `NumberSource`                      | `positionOfValues``(short[] values)`<br>Identifies the positions of elements in this `NumberSource` that have the specified `short` values.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
    | `NumberSource`                      | `pow``(double rhs)`<br>Raises the value of each element of this `NumberSource` to the specified `double` value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `NumberSource`                      | `pow``(float rhs)`<br>Raises the value of each element of this `NumberSource` to the specified `float` value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `NumberSource`                      | `pow``(int rhs)`<br>Raises the value of each element of this `NumberSource` to the specified `int` value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `NumberSource`                      | `pow``(NumberSource rhs)`<br>Raises the value of each element of this `NumberSource` to the values of the elements of the specified `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `NumberSource`                      | `pow``(short rhs)`<br>Raises the value of each element of this `NumberSource` to the specified `short` value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `NumberSource`                      | `rem``(double rhs)`<br>Divides the value of each element of this `NumberSource` by the specified `double` value and determines the remainder for each operation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
    | `NumberSource`                      | `rem``(float rhs)`<br>Divides the value of each element of this `NumberSource` by the specified `float` value and determines the remainder for each operation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `NumberSource`                      | `rem``(int rhs)`<br>Divides the value of each element of this `NumberSource` by the specified `int` value and determines the remainder for each operation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
    | `NumberSource`                      | `rem``(NumberSource rhs)`<br>Divides the value of each element of this `NumberSource` by the values of the elements of the specified `NumberSource` and determines the remainder for each operation.                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `NumberSource`                      | `rem``(short rhs)`<br>Divides the value of each element of this `NumberSource` by the specified `short` value and determines the remainder for each operation.                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `NumberSource`                      | `removeValue``(double value)`<br>Removes the elements of this `NumberSource` that have the specified `double` value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `NumberSource`                      | `removeValue``(float value)`<br>Removes the elements of this `NumberSource` that have the specified `float` value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `NumberSource`                      | `removeValue``(int value)`<br>Removes the elements of this `NumberSource` that have the specified `int` value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `NumberSource`                      | `removeValue``(short value)`<br>Removes the elements of this `NumberSource` that have the specified `double` value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `NumberSource`                      | `removeValues``(double[] values)`<br>Removes the elements of this `NumberSource` that have the specified `double` values.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `NumberSource`                      | `removeValues``(float[] values)`<br>Removes the elements of this `NumberSource` that have the specified `float` values.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `NumberSource`                      | `removeValues``(int[] values)`<br>Removes the elements of this `NumberSource` that have the specified `int` values.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `NumberSource`                      | `removeValues``(short[] values)`<br>Removes the elements of this `NumberSource` that have the specified `short` values.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `NumberSource`                      | `round``(double precision)`<br>Rounds the value of each element of this `NumberSource` to the precision specified by the `double` value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          |
    | `NumberSource`                      | `round``(float precision)`<br>Rounds the value of each element of this `NumberSource` to the precision specified by the `float` value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `NumberSource`                      | `round``(int precision)`<br>Rounds the value of each element of this `NumberSource` to the precision specified by the `int` value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `NumberSource`                      | `round``(NumberSource precision)`<br>Rounds the value of each element of this `NumberSource` to the precisions specified by the `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `NumberSource`                      | `round``(short precision)`<br>Rounds the value of each element of this `NumberSource` to the precision specified by the `short` value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `NumberSource`                      | `selectValue``(double value)`<br>Selects the elements of this `NumberSource` that have the specified `double` value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `NumberSource`                      | `selectValue``(float value)`<br>Selects the elements of this `NumberSource` that have the specified `float` value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `NumberSource`                      | `selectValue``(int value)`<br>Selects the elements of this `NumberSource` that have the specified `int` value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `NumberSource`                      | `selectValue``(short value)`<br>Selects the elements of this `NumberSource` that have the specified `short` value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `NumberSource`                      | `selectValues``(double[] values)`<br>Selects the elements of this `NumberSource` that have the specified `double` values.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `NumberSource`                      | `selectValues``(float[] values)`<br>Selects the elements of this `NumberSource` that have the specified `float` values.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `NumberSource`                      | `selectValues``(int[] values)`<br>Selects the elements of this `NumberSource` that have the specified `int` values.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `NumberSource`                      | `selectValues``(short[] values)`<br>Selects the elements of this `NumberSource` that have the specified `short` values.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `NumberSource`                      | `sin``()`<br>Calculates the sine of the value (interpreted as an angle) of each element of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `NumberSource`                      | `sinh``()`<br>Calculates the hyperbolic of the value (interpreted as an angle) of each element of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `NumberSource`                      | `sqrt``()`<br>Calculates the square root of the value of each element of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
    | `NumberSource`                      | `stdev``()`<br>Calculates the standard deviation of the values of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
    | `NumberSource`                      | `stdevPop``()`<br>Calculates the population standard deviation of the values of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
    | `NumberSource`                      | `stdevSamp``()`<br>Calculates the cumulative sample standard deviation of the values of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
    | `NumberSource`                      | `tan``()`<br>Calculates the tangent of the value (interpreted as an angle) of each element of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                |
    | `NumberSource`                      | `tanh``()`<br>Calculates the hyperbolic tangent of the value (interpreted as an angle) of each element of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
    | `NumberSource`                      | `times``(double rhs)`<br>Multiplies the value of each element of this `NumberSource` by the specified `double` value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
    | `NumberSource`                      | `times``(float rhs)`<br>Multiplies the value of each element of this `NumberSource` by the specified `float` value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `NumberSource`                      | `times``(int rhs)`<br>Multiplies the value of each element of this `NumberSource` by the specified `int` value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `NumberSource`                      | `times``(NumberSource rhs)`<br>Multiplies the value of each element of this `NumberSource` by the values of the elements of the specified `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
    | `NumberSource`                      | `times``(short rhs)`<br>Multiplies the value of each element of this `NumberSource` by the specified `short` value.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
    | `NumberSource`                      | `total``()`<br>Calculates the sum of the values of the elements of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
    | `NumberSource`                      | `variance``()`<br>Calculates the variance of the elements of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
    | `NumberSource`                      | `variancePop``()`<br>Calculates the population variance of the elements of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
    | `NumberSource`                      | `varianceSamp``()`<br>Calculates the sample variance of the elements of this `NumberSource`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

    - ### Methods inherited from class oracle.olapi.data.source.[Source](Source.md)

      [`alias`](Source.md)`, `[`appendValue`](Source.md)`, `[`appendValues`](Source.md)`, `[`appendValues`](Source.md)`, `[`at`](Source.md)`, `[`at`](Source.md)`, `[`count`](Source.md)`, `[`count`](Source.md)`, `[`cumulativeInterval`](Source.md)`, `[`cumulativeInterval`](Source.md)`, `[`cumulativeInterval`](Source.md)`, `[`distinct`](Source.md)`, `[`eq`](Source.md)`, `[`extract`](Source.md)`, `[`findMatchFor`](Source.md)`, `[`first`](Source.md)`, `[`ge`](Source.md)`, `[`getDataProvider`](Source.md)`, `[`getDefinition`](Source.md)`, `[`getExtractionInputs`](Source.md)`, `[`getID`](Source.md)`, `[`getInputs`](Source.md)`, `[`getMetadataProvider`](Source.md)`, `[`getMetadataProviderID`](Source.md)`, `[`getModel`](Source.md)`, `[`getOutputs`](Source.md)`, `[`getRegularInputs`](Source.md)`, `[`getType`](Source.md)`, `[`gt`](Source.md)`, `[`hasValue`](Source.md)`, `[`in`](Source.md)`, `[`interval`](Source.md)`, `[`interval`](Source.md)`, `[`isSubtypeOf`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`joinHidden`](Source.md)`, `[`last`](Source.md)`, `[`le`](Source.md)`, `[`lt`](Source.md)`, `[`movingInterval`](Source.md)`, `[`movingInterval`](Source.md)`, `[`ne`](Source.md)`, `[`nullSource`](Source.md)`, `[`offset`](Source.md)`, `[`offset`](Source.md)`, `[`position`](Source.md)`, `[`position`](Source.md)`, `[`positionOfValue`](Source.md)`, `[`positionOfValues`](Source.md)`, `[`positionOfValues`](Source.md)`, `[`recursiveJoin`](Source.md)`, `[`recursiveJoin`](Source.md)`, `[`recursiveJoin`](Source.md)`, `[`recursiveJoin`](Source.md)`, `[`recursiveJoin`](Source.md)`, `[`recursiveJoin`](Source.md)`, `[`recursiveJoin`](Source.md)`, `[`remove`](Source.md)`, `[`removeValue`](Source.md)`, `[`removeValues`](Source.md)`, `[`removeValues`](Source.md)`, `[`select`](Source.md)`, `[`selectDescendants`](Source.md)`, `[`selectValue`](Source.md)`, `[`selectValues`](Source.md)`, `[`selectValues`](Source.md)`, `[`sortAscending`](Source.md)`, `[`sortAscending`](Source.md)`, `[`sortAscending`](Source.md)`, `[`sortAscendingHierarchically`](Source.md)`, `[`sortAscendingHierarchically`](Source.md)`, `[`sortAscendingHierarchically`](Source.md)`, `[`sortAscendingHierarchically`](Source.md)`, `[`sortDescending`](Source.md)`, `[`sortDescending`](Source.md)`, `[`sortDescending`](Source.md)`, `[`sortDescendingHierarchically`](Source.md)`, `[`sortDescendingHierarchically`](Source.md)`, `[`sortDescendingHierarchically`](Source.md)`, `[`sortDescendingHierarchically`](Source.md)`, `[`toDoubleSource`](Source.md)`, `[`toFloatSource`](Source.md)`, `[`toIntegerSource`](Source.md)`, `[`toShortSource`](Source.md)`, `[`toStringSource`](Source.md)`, `[`value`](Source.md)`, `[`value`](Source.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### abs

          public final NumberSource abs()

      Calculates the absolute value of the value of each element of this `NumberSource`.
      Returns:
      A `NumberSource` that has an element with a `double` value that is the absolute value of the value of the corresponding element of this `NumberSource`.

    <!-- -->

    - #### appendValue

          public final NumberSource appendValue(double appendValue)

      Appends an element with the specified `double` value to this `NumberSource`. The outputs of this `NumberSource`, if any, do not appear in the resulting `NumberSource`.
      Parameters:
      `appendValue` - The `double` value that you want to append to this `NumberSource`.

      Returns:
      A `NumberSource` that has the same elements as this `NumberSource` and that has an additional appended element that has the specified `double` value.

    <!-- -->

    - #### appendValue

          public final NumberSource appendValue(float appendValue)

      Appends an element with the specified `float` value to this `NumberSource`. The outputs of this `NumberSource`, if any, do not appear in the resulting `NumberSource`.
      Parameters:
      `appendValue` - The `float` value that you want to append to this `NumberSource`.

      Returns:
      A `NumberSource` that has the same elements as this `NumberSource` and that has an additional appended element that has the specified `float` value.

    <!-- -->

    - #### appendValue

          public final NumberSource appendValue(int appendValue)

      Appends an element with the specified `int` value to this `NumberSource`. The outputs of this `NumberSource`, if any, do not appear in the resulting `NumberSource`.
      Parameters:
      `appendValue` - The `int` value that you want to append to this `NumberSource`.

      Returns:
      A `NumberSource` that has the same elements as this `NumberSource` and that has an additional appended element that has the specified `int` value.

    <!-- -->

    - #### appendValue

          public final NumberSource appendValue(short appendValue)

      Appends an element with the specified `short` value to this `NumberSource`. The outputs of this `NumberSource`, if any, do not appear in the resulting `NumberSource`.
      Parameters:
      `appendValue` - The `short` value that you want to append to this `NumberSource`.

      Returns:
      A `NumberSource` that has the same elements as this `NumberSource` and that has an additional appended element that has the specified `short` value.

    <!-- -->

    - #### appendValues

          public final NumberSource appendValues(double[] appendValues)

      Appends elements with the specified `double` values to this `NumberSource`. The outputs of this `NumberSource`, if any, do not appear in the resulting `NumberSource`.
      Parameters:
      `appendValues` - An array that has the `double` values that you want to append to this `NumberSource`.

      Returns:
      A `NumberSource` that has the same elements as this `NumberSource` and that has additional appended elements that have the specified `double` values.

    <!-- -->

    - #### appendValues

          public final NumberSource appendValues(float[] appendValues)

      Appends elements with the specified `float` values to this `NumberSource`. The outputs of this `NumberSource`, if any, do not appear in the resulting `NumberSource`.
      Parameters:
      `appendValues` - An array that has the `float` values that you want to append to this `NumberSource`.

      Returns:
      A `NumberSource` that has the same elements as this `NumberSource` and that has additional appended elements that have the specified `float` values.

    <!-- -->

    - #### appendValues

          public final NumberSource appendValues(int[] appendValues)

      Appends elements with the specified `int` values to this `NumberSource`. The outputs of this `NumberSource`, if any, do not appear in the resulting `NumberSource`.
      Parameters:
      `appendValues` - An array that has the `int` values that you want to append to this `NumberSource`.

      Returns:
      A `NumberSource` that has the same elements as this `NumberSource` and that has additional appended elements that have the specified `int` values.

    <!-- -->

    - #### appendValues

          public final NumberSource appendValues(short[] appendValues)

      Appends elements with the specified `short` values to this `NumberSource`. The outputs of this `NumberSource`, if any, do not appear in the resulting `NumberSource`.
      Parameters:
      `appendValues` - An array that has the `short` values that you want to append to this `NumberSource`.

      Returns:
      A `NumberSource` that has the same elements as this `NumberSource` and that has additional appended elements that have the specified `short` values.

    <!-- -->

    - #### arccos

          public final NumberSource arccos()

      Calculates the angle value (in radians) of the value (interpreted as a cosine) of each element of this `NumberSource`.
      Returns:
      A `NumberSource` whose elements have `double` values that are the angle values (in radians) of the values of the corresponding elements of this `NumberSource`.

    <!-- -->

    - #### arcsin

          public final NumberSource arcsin()

      Calculates the angle value (in radians) of the value (interpreted as a sine) of each element of this `NumberSource`.
      Returns:
      A `NumberSource` whose elements have `double` values that are the angle values (in radians) of the values of the corresponding elements of this `NumberSource`.

    <!-- -->

    - #### arctan

          public final NumberSource arctan()

      Calculates the angle value (in radians) of the value (interpreted as a tangent) of each element of this `NumberSource`.
      Returns:
      A `NumberSource` whose elements have `double` values that are the angle values (in radians) of the values of the corresponding elements of this `NumberSource`.

    <!-- -->

    - #### average

          public final NumberSource average()

      Calculates the average of the values of the elements of this `NumberSource`.
      Returns:
      A `NumberSource` that has an element whose value is the average of the values of the elements of this `NumberSource`.

    <!-- -->

    - #### cos

          public final NumberSource cos()

      Calculates the cosine of the value (interpreted as an angle value in radians) of each element of this `NumberSource`.
      Returns:
      A `NumberSource` whose elements have `double` values that are the cosines of the values of the corresponding elements of this `NumberSource`.

    <!-- -->

    - #### cosh

          public final NumberSource cosh()

      Calculates the hyperbolic cosine of the value (interpreted as an angle value in radians) of each element of this `NumberSource`.
      Returns:
      A `NumberSource` whose elements have `double` values that are the hyperbolic cosines of the values of the corresponding elements of this `NumberSource`.

    <!-- -->

    - #### div

          public final NumberSource div(double rhs)

      Divides the value of the elements of this `NumberSource` by the specified `double` value.
      Parameters:
      `rhs` - The `double` value that you want to use as the divisor.

      Returns:
      A `NumberSource` whose elements have values that that are the result of dividing the values of the elements of this `NumberSource` by the specified divisor.

    <!-- -->

    - #### div

          public final NumberSource div(double rhs,
                                        boolean safe)

      Divides the value of the elements of this `NumberSource` by the specified `double` value; if `safe` is `true` and the divisor is zero, then this method returns `null`.
      Parameters:
      `rhs` - The `double` value that you want to use as the divisor.

      `safe` - A `boolean` that indicates whether you want this method to return `null` when the divisor is zero.

      Returns:
      A `NumberSource` whose elements have values that that are the result of dividing the values of the elements of this `NumberSource` by the specified divisor.

    <!-- -->

    - #### div

          public final NumberSource div(float rhs)

      Divides the value of the elements of this `NumberSource` by the specified `float` value.
      Parameters:
      `rhs` - The `float` value that you want to use as the divisor.

      Returns:
      A `NumberSource` whose elements have values that that are the result of dividing the values of the elements of this `NumberSource` by the specified divisor.

    <!-- -->

    - #### div

          public final NumberSource div(float rhs,
                                        boolean safe)

      Divides the value of the elements of this `NumberSource` by the specified `float` value; if `safe` is `true` and the divisor is zero, then this method returns `null`.
      Parameters:
      `rhs` - The `float` value that you want to use as the divisor.

      `safe` - A `boolean` that indicates whether you want this method to return `null` when the divisor is zero.

      Returns:
      A `NumberSource` whose elements have values that that are the result of dividing the values of the elements of this `NumberSource` by the specified divisor.

    <!-- -->

    - #### div

          public final NumberSource div(int rhs)

      Divides the value of the elements of this `NumberSource` by the specified `int` value.
      Parameters:
      `rhs` - The `int` value that you want to use as the divisor.

      Returns:
      A `NumberSource` whose elements have values that that are the result of dividing the values of the elements of this `NumberSource` by the specified divisor.

    <!-- -->

    - #### div

          public final NumberSource div(int rhs,
                                        boolean safe)

      Divides the value of the elements of this `NumberSource` by the specified `int` value; if `safe` is `true` and the divisor is zero, then this method returns `null`.
      Parameters:
      `rhs` - The `int` value that you want to use as the divisor.

      `safe` - A `boolean` that indicates whether you want this method to return `null` when the divisor is zero.

      Returns:
      A `NumberSource` whose elements have values that that are the result of dividing the values of the elements of this `NumberSource` by the specified divisor.

    <!-- -->

    - #### div

          public final NumberSource div(NumberSource rhs)

      Divides the value of the elements of this `NumberSource` by the values of the elements of the specified `NumberSource`.
      Parameters:
      `rhs` - A `NumberSource` whose element values you want to use as divisors.

      Returns:
      A `NumberSource` whose elements have values that that are the result of dividing the values of the elements of this `NumberSource` by the specified divisors.

    <!-- -->

    - #### div

          public final NumberSource div(NumberSource rhs,
                                        boolean safe)

      Divides the value of the elements of this `NumberSource` by the values of the elements of the specified `NumberSource`; if `safe` is `true` and a divisor is zero, then this method returns `null` as the result of the division.
      Parameters:
      `rhs` - The `NumberSource` whose element values you want to use as divisors.

      `safe` - A `boolean` that indicates whether you want this method to return `null` when the divisor is zero.

      Returns:
      A `NumberSource` whose elements have values that that are the result of dividing the values of the elements of this `NumberSource` by the specified divisors.

    <!-- -->

    - #### div

          public final NumberSource div(short rhs)

      Divides the value of the elements of this `NumberSource` by the specified `short` value.
      Parameters:
      `rhs` - The `short` value that you want to use as the divisor.

      Returns:
      A `NumberSource` whose elements have values that that are the result of dividing the values of the elements of this `NumberSource` by the specified divisor.

    <!-- -->

    - #### div

          public final NumberSource div(short rhs,
                                        boolean safe)

      Divides the value of the elements of this `NumberSource` by the specified `short` value; if `safe` is `true` and the divisor is zero, then this method returns `null`.
      Parameters:
      `rhs` - The `short` value that you want to use as the divisor.

      `safe` - A `boolean` that indicates whether you want this method to return `null` when the divisor is zero.

      Returns:
      A `NumberSource` whose elements have values that that are the result of dividing the values of the elements of this `NumberSource` by the specified divisor.

    <!-- -->

    - #### eq

          public final BooleanSource eq(double rhs)

      Compares the value of each element of this `NumberSource` to the specified `double` value and determines if the values are equal.
      Parameters:
      `rhs` - The `double` value that you want to compare to the values of the elements of this `NumberSource`.

      Returns:
      A `BooleanSource` that has an element that has a value of `true` when the value of the corresponding element of this `NumberSource` equals the specified `double` value or `false` when it does not.

    <!-- -->

    - #### eq

          public final BooleanSource eq(float rhs)

      Compares the value of each element of this `NumberSource` to the specified `float` value and determines if the values are equal.
      Parameters:
      `rhs` - The `float` value that you want to compare to the values of the elements of this `NumberSource`.

      Returns:
      A `BooleanSource` that has an element that has a value of `true` when the value of the corresponding element of this `NumberSource` equals the specified `float` value or `false` when it does not.

    <!-- -->

    - #### eq

          public final BooleanSource eq(int rhs)

      Compares the value of each element of this `NumberSource` to the specified `int` value and determines if the values are equal.
      Parameters:
      `rhs` - The `int` value that you want to compare to the values of the elements of this `NumberSource`.

      Returns:
      A `BooleanSource` that has an element that has a value of `true` when the value of the corresponding element of this `NumberSource` equals the specified `int` value or `false` when it does not.

    <!-- -->

    - #### eq

          public final BooleanSource eq(short rhs)

      Compares the value of each element of this `NumberSource` to the specified `short` value and determines if the values are equal.
      Parameters:
      `rhs` - The `short` value that you want to compare to the values of the elements of this `NumberSource`.

      Returns:
      A `BooleanSource` that has an element that has a value of `true` when the value of the corresponding element of this `NumberSource` equals the specified `short` value or `false` when it does not.

    <!-- -->

    - #### ge

          public final BooleanSource ge(double rhs)

      Compares the value of each element of this `NumberSource` to the specified `double` value, and determines whether it is a greater or equal value.
      Parameters:
      `rhs` - The `double` value that you want to compare to the values of the elements of this `NumberSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of the corresponding element of this `NumberSource` is greater than or equal to the specified `double` value, or `false` when it is not.

    <!-- -->

    - #### ge

          public final BooleanSource ge(float rhs)

      Compares the value of each element of this `NumberSource` to the specified `float` value, and determines whether it is a greater or equal value.
      Parameters:
      `rhs` - The `float` value that you want to compare to the values of the elements of this `NumberSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of the corresponding element of this `NumberSource` is greater than or equal to the specified `float` value, or `false` when it is not.

    <!-- -->

    - #### ge

          public final BooleanSource ge(int rhs)

      Compares the value of each element of this `NumberSource` to the specified `int` value, and determines whether it is a greater or equal value.
      Parameters:
      `rhs` - The `int` value that you want to compare to the values of the elements of this `NumberSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of the corresponding element of this `NumberSource` is greater than or equal to the specified `int` value, or `false` when it is not.

    <!-- -->

    - #### ge

          public final BooleanSource ge(short rhs)

      Compares the value of each element of this `NumberSource` to the specified `short` value, and determines whether it is a greater or equal value.
      Parameters:
      `rhs` - The `short` value that you want to compare to the values of the elements of this `NumberSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of the corresponding element of this `NumberSource` is greater than or equal to the specified `short` value, or `false` when it is not.

    <!-- -->

    - #### getDataType

          public Source getDataType()

      Gets the fundamental `Source` that represents the OLAP Java API data type of this `NumberSource`, which can be Double, Float, Integer, Number, or Short, depending on the values of its elements.
      Overrides:
      [`getDataType`](Source.md) in class [`Source`](Source.md)

      Returns:
      The fundamental `Source` that represents the OLAP Java API data type of this `NumberSource`.

    <!-- -->

    - #### gt

          public final BooleanSource gt(double rhs)

      Compares the value of each element of this `NumberSource` to the specified `double` value, and determines whether it is a greater value.
      Parameters:
      `rhs` - The `double` value that you want to compare to the values of the elements of this `NumberSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of the corresponding element of this `NumberSource` is greater than the specified `double` value, or `false` when it is not.

    <!-- -->

    - #### gt

          public final BooleanSource gt(float rhs)

      Compares the value of each element of this `NumberSource` to the specified `float` value, and determines whether it is a greater value.
      Parameters:
      `rhs` - The `float` value that you want to compare to the values of the elements of this `NumberSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of the corresponding element of this `NumberSource` is greater than the specified `float` value, or `false` when it is not.

    <!-- -->

    - #### gt

          public final BooleanSource gt(int rhs)

      Compares the value of each element of this `NumberSource` to the specified `int` value, and determines whether it is a greater value.
      Parameters:
      `rhs` - The `int` value that you want to compare to the values of the elements of this `NumberSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of the corresponding element of this `NumberSource` is greater than the specified `int` value, or `false` when it is not.

    <!-- -->

    - #### gt

          public final BooleanSource gt(short rhs)

      Compares the value of each element of this `NumberSource` to the specified `short` value, and determines whether it is a greater value.
      Parameters:
      `rhs` - The `short` value that you want to compare to the values of the elements of this `NumberSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of the corresponding element of this `NumberSource` is greater than the specified `short` value, or `false` when it is not.

    <!-- -->

    - #### intpart

          public final NumberSource intpart()

      Identifies the integer portion of the value of each element of this `NumberSource`.
      Returns:
      A `NumberSource` whose elements have the integer portion of the values of the elements of this `NumberSource`.

    <!-- -->

    - #### le

          public final BooleanSource le(double rhs)

      Compares the value of each element of this `NumberSource` to the specified `double` value, and determines whether it is a lesser or equal value.
      Parameters:
      `rhs` - The `double` value that you want to compare to the values of the elements of this `NumberSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of a given element of this `NumberSource` is less than or equal to the specified `double` value, or `false` when it is not.

    <!-- -->

    - #### le

          public final BooleanSource le(float rhs)

      Compares the value of each element of this `NumberSource` to the specified `float` value, and determines whether it is a lesser or equal value.
      Parameters:
      `rhs` - The `float` value that you want to compare to the values of the elements of this `NumberSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of a given element of this `NumberSource` is less than or equal to the specified `float` value, or `false` when it is not.

    <!-- -->

    - #### le

          public final BooleanSource le(int rhs)

      Compares the value of each element of this `NumberSource` to the specified `int` value, and determines whether it is a lesser or equal value.
      Parameters:
      `rhs` - The `int` value that you want to compare to the values of the elements of this `NumberSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of a given element of this `NumberSource` is less than or equal to the specified `int` value, or `false` when it is not.

    <!-- -->

    - #### le

          public final BooleanSource le(short rhs)

      Compares the value of each element of this `NumberSource` to the specified `short` value, and determines whether it is a lesser or equal value.
      Parameters:
      `rhs` - The `short` value that you want to compare to the values of the elements of this `NumberSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of a given element of this `NumberSource` is less than or equal to the specified `short` value, or `false` when it is not.

    <!-- -->

    - #### log

          public final NumberSource log()

      Calculates the natural logarithm of the value of each element of this `NumberSource`.
      Returns:
      A `NumberSource` that has `double` values that are the natural logarithms of the values of the elements of this `NumberSource`.

    <!-- -->

    - #### lt

          public final BooleanSource lt(double rhs)

      Compares the value of each element of this `NumberSource` to the specified `double` value, and determines whether it is a lesser value.
      Parameters:
      `rhs` - The `double` value that you want to compare to the values of the elements of this `NumberSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of the corresponding element of this `NumberSource` is less than the specified `double` value, or `false` when it is not.

    <!-- -->

    - #### lt

          public final BooleanSource lt(float rhs)

      Compares the value of each element of this `NumberSource` to the specified `float` value, and determines whether it is a lesser value.
      Parameters:
      `rhs` - The `float` value that you want to compare to the values of the elements of this `NumberSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of the corresponding element of this `NumberSource` is less than the specified `float` value, or `false` when it is not.

    <!-- -->

    - #### lt

          public final BooleanSource lt(int rhs)

      Compares the value of each element of this `NumberSource` to the specified `int` value, and determines whether it is a lesser value.
      Parameters:
      `rhs` - The `int` value that you want to compare to the values of the elements of this `NumberSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of the corresponding element of this `NumberSource` is less than the specified `int` value, or `false` when it is not.

    <!-- -->

    - #### lt

          public final BooleanSource lt(short rhs)

      Compares the value of each element of this `NumberSource` to the specified `short` value, and determines whether it is a lesser value.
      Parameters:
      `rhs` - The `short` value that you want to compare to the values of the elements of this `NumberSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of the corresponding element of this `NumberSource` is less than the specified `short` value, or `false` when it is not.

    <!-- -->

    - #### maximum

          public final NumberSource maximum()

      Identifies the largest value of the elements of this `NumberSource`.
      Returns:
      A `NumberSource` that has an element whose value is the largest value of the elements of this `NumberSource`.

    <!-- -->

    - #### minimum

          public final NumberSource minimum()

      Identifies the smallest value of the elements of this `NumberSource`.
      Returns:
      A `NumberSource` that has an element whose value is the smallest value of the elements of this `NumberSource`.

    <!-- -->

    - #### minus

          public final NumberSource minus(double rhs)

      Subtracts the specified `double` value from the value of each element of this `NumberSource`.
      Parameters:
      `rhs` - The `double` value that you want to subtract from the values of the elements of this `NumberSource`.

      Returns:
      A `NumberSource`, each of whose elements has a value that results from subtracting the specified `double` value from the value of the corresponding element of this `NumberSource`.

    <!-- -->

    - #### minus

          public final NumberSource minus(float rhs)

      Subtracts the specified `float` value from the value of each element of this `NumberSource`.
      Parameters:
      `rhs` - The `float` value that you want to subtract from the values of the elements of this `NumberSource`.

      Returns:
      A `NumberSource`, each of whose elements has a value that results from subtracting the specified `float` value from the value of the corresponding element of this `NumberSource`.

    <!-- -->

    - #### minus

          public final NumberSource minus(int rhs)

      Subtracts the specified `int` value from the value of each element of this `NumberSource`.
      Parameters:
      `rhs` - The `int` value that you want to subtract from the values of the elements of this `NumberSource`.

      Returns:
      A `NumberSource`, each of whose elements has a value that results from subtracting the specified `int` value from the value of the corresponding element of this `NumberSource`.

    <!-- -->

    - #### minus

          public final NumberSource minus(NumberSource rhs)

      Subtracts the values of the elments of the specified `NumberSource` from the value of each element of this `NumberSource`.
      Parameters:
      `rhs` - The `NumberSource`, the values of whose elements you want to subtract from the values of the elements of this `NumberSource`.

      Returns:
      A `NumberSource` whose elements have values that result from subtracting the values of the elements of the specified `NumberSource` from the values of the elements of this `NumberSource`.

    <!-- -->

    - #### minus

          public final NumberSource minus(short rhs)

      Subtracts the specified `short` value from the value of each element of this `NumberSource`.
      Parameters:
      `rhs` - The `short` value that you want to subtract from the values of the elements of this `NumberSource`.

      Returns:
      A `NumberSource`, each of whose elements has a value that results from subtracting the specified `short` value from the value of the corresponding element of this `NumberSource`.

    <!-- -->

    - #### ne

          public final BooleanSource ne(double rhs)

      Compares the value of each element of this `NumberSource` to the specified `double` value, and determines whether it is not equal to the value.
      Parameters:
      `rhs` - The `double` value that you want to compare to the values of the elements of this `NumberSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of the corresponding element of this `NumberSource` is not equal to the specified `double` value, or `false` when it is equal to the specified value.

    <!-- -->

    - #### ne

          public final BooleanSource ne(float rhs)

      Compares the value of each element of this `NumberSource` to the specified `float` value, and determines whether it is not equal to the value.
      Parameters:
      `rhs` - The `float` value that you want to compare to the values of the elements of this `NumberSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of the corresponding element of this `NumberSource` is not equal to the specified `float` value, or `false` when it is equal to the specified value.

    <!-- -->

    - #### ne

          public final BooleanSource ne(int rhs)

      Compares the value of each element of this `NumberSource` to the specified `int` value, and determines whether it is not equal to the value.
      Parameters:
      `rhs` - The `int` value that you want to compare to the values of the elements of this `NumberSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of the corresponding element of this `NumberSource` is not equal to the specified `int` value, or `false` when it is equal to the specified value.

    <!-- -->

    - #### ne

          public final BooleanSource ne(short rhs)

      Compares the value of each element of this `NumberSource` to the specified `short` value, and determines whether it is not equal to the value.
      Parameters:
      `rhs` - The `short` value that you want to compare to the values of the elements of this `NumberSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of the corresponding element of this `NumberSource` is not equal to the specified `short` value, or `false` when it is equal to the specified value.

    <!-- -->

    - #### negate

          public final NumberSource negate()

      Negates the value of each of the elements of this `NumberSource`.
      Returns:
      A `NumberSource`, the values of whose elements are the negative values of the values of the corresponding elements of this `NumberSource`.

    <!-- -->

    - #### plus

          public final NumberSource plus(double rhs)

      Adds the specified `double` value to the value of each element of this `NumberSource`.
      Parameters:
      `rhs` - The `double` value that you want to add to the value of each element of this `NumberSource`.

      Returns:
      A `NumberSource` that has elements that have the values of the corresponding elements of this `NumberSource` with the specified `double` value added to them.

    <!-- -->

    - #### plus

          public final NumberSource plus(float rhs)

      Adds the specified `float` value to the value of each element of this `NumberSource`.
      Parameters:
      `rhs` - The `float` value that you want to add to the value of each element of this `NumberSource`.

      Returns:
      A `NumberSource` that has elements that have the values of the corresponding elements of this `NumberSource` with the specified `float` value added to them.

    <!-- -->

    - #### plus

          public final NumberSource plus(int rhs)

      Adds the specified `int` value to the value of each element of this `NumberSource`.
      Parameters:
      `rhs` - The `int` value that you want to add to the value of each element of this `NumberSource`.

      Returns:
      A `NumberSource` that has elements that have the values of the corresponding elements of this `NumberSource` with the specified `int` value added to them.

    <!-- -->

    - #### plus

          public final NumberSource plus(NumberSource rhs)

      Adds the values of the elements of the specified `NumberSource` to the value of each element of this `NumberSource`.
      Parameters:
      `rhs` - The `NumberSource` the values of the elements of which you want to add to the values of the elements of this `NumberSource`.

      Returns:
      A `NumberSource` that has elements that have the values of the elements of this `NumberSource` with the values of the elements of the specified `NumberSource` added to them.

    <!-- -->

    - #### plus

          public final NumberSource plus(short rhs)

      Adds the specified `short` value to the value of each element of this `NumberSource`.
      Parameters:
      `rhs` - The `short` value that you want to add to the value of each element of this `NumberSource`.

      Returns:
      A `NumberSource` that has elements that have the values of the corresponding elements of this `NumberSource` with the specified `short` value added to them.

    <!-- -->

    - #### positionOfValue

          public final NumberSource positionOfValue(double value)

      Identifies the positions of elements in this `NumberSource` that have the specified `double` value.
      Parameters:
      `value` - The `double` value that you want to compare to the values of the elements of this `NumberSource`.

      Returns:
      A `NumberSource` whose elements have `int` values that identify the positions of the elements in this `NumberSource` that have the specified `double` value. If this `NumberSource` does not have any elements that have the specified value, then this method returns an empty `NumberSource`, which has no elements.

    <!-- -->

    - #### positionOfValue

          public final NumberSource positionOfValue(float value)

      Identifies the positions of elements in this `NumberSource` that have the specified `float` value.
      Parameters:
      `value` - The `float` value that you want to compare to the values of the elements of this `NumberSource`.

      Returns:
      A `NumberSource` whose elements have `int` values that identify the positions of the elements in this `NumberSource` that have the specified `float` value. If this `NumberSource` does not have any elements that have the specified value, then this method returns an empty `NumberSource`, which has no elements.

    <!-- -->

    - #### positionOfValue

          public final NumberSource positionOfValue(int value)

      Identifies the positions of elements in this `NumberSource` that have the specified `int` value.
      Parameters:
      `value` - The `int` value that you want to compare to the values of the elements of this `NumberSource`.

      Returns:
      A `NumberSource` whose elements have `int` values that identify the positions of the elements in this `NumberSource` that have the specified `int` value. If this `NumberSource` does not have any elements that have the specified value, then this method returns an empty `NumberSource`, which has no elements.

    <!-- -->

    - #### positionOfValue

          public final NumberSource positionOfValue(short value)

      Identifies the positions of elements in this `NumberSource` that have the specified `short` value.
      Parameters:
      `value` - The `short` value that you want to compare to the values of the elements of this `NumberSource`.

      Returns:
      A `NumberSource` whose elements have `int` values that identify the positions of the elements in this `NumberSource` that have the specified `short` value. If this `NumberSource` does not have any elements that have the specified value, then this method returns an empty `NumberSource`, which has no elements.

    <!-- -->

    - #### positionOfValues

          public final NumberSource positionOfValues(double[] values)

      Identifies the positions of elements in this `NumberSource` that have the specified `double` values.
      Parameters:
      `values` - An array of `double` values that you want to compare to the values of the elements of this `NumberSource`.

      Returns:
      A `NumberSource` whose elements have `int` values that identify the positions of the elements in this `NumberSource` that have the specified `double` values. If this `NumberSource` does not have any elements that have the specified values, then this method returns an empty `NumberSource`, which has no elements.

    <!-- -->

    - #### positionOfValues

          public final NumberSource positionOfValues(float[] values)

      Identifies the positions of elements in this `NumberSource` that have the specified `float` values.
      Parameters:
      `values` - An array of `float` values that you want to compare to the values of the elements of this `NumberSource`.

      Returns:
      A `NumberSource` whose elements have `int` values that identify the positions of the elements in this `NumberSource` that have the specified `float` values. If this `NumberSource` does not have any elements that have the specified values, then this method returns an empty `NumberSource`, which has no elements.

    <!-- -->

    - #### positionOfValues

          public final NumberSource positionOfValues(int[] values)

      Identifies the positions of elements in this `NumberSource` that have the specified `int` values.
      Parameters:
      `values` - An array of `int` values that you want to compare to the values of the elements of this `NumberSource`.

      Returns:
      A `NumberSource` whose elements have `int` values that identify the positions of the elements in this `NumberSource` that have the specified `int` values. If this `NumberSource` does not have any elements that have the specified values, then this method returns an empty `NumberSource`, which has no elements.

    <!-- -->

    - #### positionOfValues

          public final NumberSource positionOfValues(short[] values)

      Identifies the positions of elements in this `NumberSource` that have the specified `short` values.
      Parameters:
      `values` - An array of `short` values that you want to compare to the values of the elements of this `NumberSource`.

      Returns:
      A `NumberSource` whose elements have `int` values that identify the positions of the elements in this `NumberSource` that have the specified `short` values. If this `NumberSource` does not have any elements that have the specified values, then this method returns an empty `NumberSource`, which has no elements.

    <!-- -->

    - #### pow

          public final NumberSource pow(double rhs)

      Raises the value of each element of this `NumberSource` to the specified `double` value.
      Parameters:
      `rhs` - The `double` value by which you want to raise the value of each element of this `NumberSource`.

      Returns:
      A `NumberSource` that has elements that have the values of the corresponding elements of this `NumberSource` raised to the power of the specified `double` value.

    <!-- -->

    - #### pow

          public final NumberSource pow(float rhs)

      Raises the value of each element of this `NumberSource` to the specified `float` value.
      Parameters:
      `rhs` - The `float` value by which you want to raise the value of each element of this `NumberSource`.

      Returns:
      A `NumberSource` that has elements that have the values of the corresponding elements of this `NumberSource` raised to the power of the specified `float` value.

    <!-- -->

    - #### pow

          public final NumberSource pow(int rhs)

      Raises the value of each element of this `NumberSource` to the specified `int` value.
      Parameters:
      `rhs` - The `int` value by which you want to raise the value of each element of this `NumberSource`.

      Returns:
      A `NumberSource` that has elements that have the values of the corresponding elements of this `NumberSource` raised to the power of the specified `int` value.

    <!-- -->

    - #### pow

          public final NumberSource pow(NumberSource rhs)

      Raises the value of each element of this `NumberSource` to the values of the elements of the specified `NumberSource`.
      Parameters:
      `rhs` - The `NumberSource`, the values of whose elements you want to raise to the values of the elements of this `NumberSource`.

      Returns:
      A `NumberSource` that has elements that have the values of the elements of this `NumberSource` raised to the values of the elements of the specified `NumberSource`.

    <!-- -->

    - #### pow

          public final NumberSource pow(short rhs)

      Raises the value of each element of this `NumberSource` to the specified `short` value.
      Parameters:
      `rhs` - The `short` value by which you want to raise the value of each element of this `NumberSource`.

      Returns:
      A `NumberSource` that has elements that have the values of the corresponding elements of this `NumberSource` raised to the power of the specified `short` value.

    <!-- -->

    - #### rem

          public final NumberSource rem(double rhs)

      Divides the value of each element of this `NumberSource` by the specified `double` value and determines the remainder for each operation.
      Parameters:
      `rhs` - The `double` value that you want to divide into the value of each element of this `NumberSource`.

      Returns:
      A `NumberSource` whose elements have values that are the remainders of dividing the values of the elements of this `NumberSource` by the specified `double` value.

    <!-- -->

    - #### rem

          public final NumberSource rem(float rhs)

      Divides the value of each element of this `NumberSource` by the specified `float` value and determines the remainder for each operation.
      Parameters:
      `rhs` - The `float` value that you want to divide into the value of each element of this `NumberSource`.

      Returns:
      A `NumberSource` whose elements have values that are the remainders of dividing the values of the elements of this `NumberSource` by the specified `float` value.

    <!-- -->

    - #### rem

          public final NumberSource rem(int rhs)

      Divides the value of each element of this `NumberSource` by the specified `int` value and determines the remainder for each operation.
      Parameters:
      `rhs` - The `int` value that you want to divide into the value of each element of this `NumberSource`.

      Returns:
      A `NumberSource` whose elements have values that are the remainders of dividing the values of the elements of this `NumberSource` by the specified `int` value.

    <!-- -->

    - #### rem

          public final NumberSource rem(NumberSource rhs)

      Divides the value of each element of this `NumberSource` by the values of the elements of the specified `NumberSource` and determines the remainder for each operation.
      Parameters:
      `rhs` - The `NumberSource`, the values of whose elements by which you want to divide the values of the elements of this `NumberSource`.

      Returns:
      A `NumberSource` whose elements have values that are the remainders of dividing the values of the elements of this `NumberSource` by the values of the elements of the specified `NumberSource`.

    <!-- -->

    - #### rem

          public final NumberSource rem(short rhs)

      Divides the value of each element of this `NumberSource` by the specified `short` value and determines the remainder for each operation.
      Parameters:
      `rhs` - The `short` value that you want to divide into the value of each element of this `NumberSource`.

      Returns:
      A `NumberSource` whose elements have values that are the remainders of dividing the values of the elements of this `NumberSource` by the specified `short` value.

    <!-- -->

    - #### removeValue

          public final NumberSource removeValue(double value)

      Removes the elements of this `NumberSource` that have the specified `double` value.
      Parameters:
      `value` - The `double` value you do not want to have in the returned `NumberSource`.

      Returns:
      A `NumberSource` that has the elements of this `NumberSource` that do not have the specified `double` value.

    <!-- -->

    - #### removeValue

          public final NumberSource removeValue(float value)

      Removes the elements of this `NumberSource` that have the specified `float` value.
      Parameters:
      `value` - The `float` value you do not want to have in the returned `NumberSource`.

      Returns:
      A `NumberSource` that has the elements of this `NumberSource` that do not have the specified `float` value.

    <!-- -->

    - #### removeValue

          public final NumberSource removeValue(int value)

      Removes the elements of this `NumberSource` that have the specified `int` value.
      Parameters:
      `value` - The `int` value you do not want to have in the returned `NumberSource`.

      Returns:
      A `NumberSource` that has the elements of this `NumberSource` that do not have the specified `int` value.

    <!-- -->

    - #### removeValue

          public final NumberSource removeValue(short value)

      Removes the elements of this `NumberSource` that have the specified `double` value.
      Parameters:
      `value` - The `double` value you do not want to have in the returned `NumberSource`.

      Returns:
      A `NumberSource` that has the elements of this `NumberSource` that do not have the specified `double` value.

    <!-- -->

    - #### removeValues

          public final NumberSource removeValues(double[] values)

      Removes the elements of this `NumberSource` that have the specified `double` values.
      Parameters:
      `values` - An array of the `double` values that you do not want to have in the returned `NumberSource`.

      Returns:
      A `NumberSource` that has the elements of this `NumberSource` that do not have the specified `double` values.

    <!-- -->

    - #### removeValues

          public final NumberSource removeValues(float[] values)

      Removes the elements of this `NumberSource` that have the specified `float` values.
      Parameters:
      `values` - An array of the `float` values that you do not want to have in the returned `NumberSource`.

      Returns:
      A `NumberSource` that has the elements of this `NumberSource` that do not have the specified `float` values.

    <!-- -->

    - #### removeValues

          public final NumberSource removeValues(int[] values)

      Removes the elements of this `NumberSource` that have the specified `int` values.
      Parameters:
      `values` - An array of the `int` values that you do not want to have in the returned `NumberSource`.

      Returns:
      A `NumberSource` that has the elements of this `NumberSource` that do not have the specified `int` values.

    <!-- -->

    - #### removeValues

          public final NumberSource removeValues(short[] values)

      Removes the elements of this `NumberSource` that have the specified `short` values.
      Parameters:
      `values` - An array of the `short` values that you do not want to have in the returned `NumberSource`.

      Returns:
      A `NumberSource` that has the elements of this `NumberSource` that do not have the specified `short` values.

    <!-- -->

    - #### round

          public final NumberSource round(double precision)

      Rounds the value of each element of this `NumberSource` to the precision specified by the `double` value.
      Parameters:
      `precision` - The `double` value that specifies the precision.

      Returns:
      A `NumberSource` whose elements have the values of this `NumberSource` rounded to the precision specified by the `double` value.

    <!-- -->

    - #### round

          public final NumberSource round(float precision)

      Rounds the value of each element of this `NumberSource` to the precision specified by the `float` value.
      Parameters:
      `precision` - The `float` value that specifies the precision.

      Returns:
      A `NumberSource` whose elements have the values of this `NumberSource` rounded to the precision specified by the `float` value.

    <!-- -->

    - #### round

          public final NumberSource round(int precision)

      Rounds the value of each element of this `NumberSource` to the precision specified by the `int` value.
      Parameters:
      `precision` - The `int` value that specifies the precision.

      Returns:
      A `NumberSource` whose elements have the values of this `NumberSource` rounded to the precision specified by the `int` value.

    <!-- -->

    - #### round

          public final NumberSource round(NumberSource precision)

      Rounds the value of each element of this `NumberSource` to the precisions specified by the `NumberSource`.
      Parameters:
      `precision` - A `NumberSource` whose elements specify the precision values.

      Returns:
      A `NumberSource` whose elements have the values of this `NumberSource` rounded to the precisions specified by the `double` value.

    <!-- -->

    - #### round

          public final NumberSource round(short precision)

      Rounds the value of each element of this `NumberSource` to the precision specified by the `short` value.
      Parameters:
      `precision` - The `short` value that specifies the precision.

      Returns:
      A `NumberSource` whose elements have the values of this `NumberSource` rounded to the precision specified by the `short` value.

    <!-- -->

    - #### selectValue

          public final NumberSource selectValue(double value)

      Selects the elements of this `NumberSource` that have the specified `double` value.
      Parameters:
      `value` - The `double` value of the elements that you want the returned `NumberSource` to have.

      Returns:
      A `NumberSource` that has only those elements of this `NumberSource` that have the specified `double` value.

    <!-- -->

    - #### selectValue

          public final NumberSource selectValue(float value)

      Selects the elements of this `NumberSource` that have the specified `float` value.
      Parameters:
      `value` - The `float` value of the elements that you want the returned `NumberSource` to have.

      Returns:
      A `NumberSource` that has only those elements of this `NumberSource` that have the specified `float` value.

    <!-- -->

    - #### selectValue

          public final NumberSource selectValue(int value)

      Selects the elements of this `NumberSource` that have the specified `int` value.
      Parameters:
      `value` - The `int` value of the elements that you want the returned `NumberSource` to have.

      Returns:
      A `NumberSource` that has only those elements of this `NumberSource` that have the specified `int` value.

    <!-- -->

    - #### selectValue

          public final NumberSource selectValue(short value)

      Selects the elements of this `NumberSource` that have the specified `short` value.
      Parameters:
      `value` - The `short` value of the elements that you want the returned `NumberSource` to have.

      Returns:
      A `NumberSource` that has only those elements of this `NumberSource` that have the specified `short` value.

    <!-- -->

    - #### selectValues

          public final NumberSource selectValues(double[] values)

      Selects the elements of this `NumberSource` that have the specified `double` values.
      Parameters:
      `values` - An array of the `double` values that you want the returned `NumberSource` to have.

      Returns:
      A `NumberSource` that has only those elements of this `NumberSource` that have the specified `double` values.

    <!-- -->

    - #### selectValues

          public final NumberSource selectValues(float[] values)

      Selects the elements of this `NumberSource` that have the specified `float` values.
      Parameters:
      `values` - An array of the `float` values that you want the returned `NumberSource` to have.

      Returns:
      A `NumberSource` that has only those elements of this `NumberSource` that have the specified `float` values.

    <!-- -->

    - #### selectValues

          public final NumberSource selectValues(int[] values)

      Selects the elements of this `NumberSource` that have the specified `int` values.
      Parameters:
      `values` - An array of the `int` values that you want the returned `NumberSource` to have.

      Returns:
      A `NumberSource` that has only those elements of this `NumberSource` that have the specified `int` values.

    <!-- -->

    - #### selectValues

          public final NumberSource selectValues(short[] values)

      Selects the elements of this `NumberSource` that have the specified `short` values.
      Parameters:
      `values` - An array of the `short` values that you want the returned `NumberSource` to have.

      Returns:
      A `NumberSource` that has only those elements of this `NumberSource` that have the specified `short` values.

    <!-- -->

    - #### sin

          public final NumberSource sin()

      Calculates the sine of the value (interpreted as an angle) of each element of this `NumberSource`.
      Returns:
      A `NumberSource` whose elements have `double` values that are the sines of the values of the elements of this `NumberSource`.

    <!-- -->

    - #### sinh

          public final NumberSource sinh()

      Calculates the hyperbolic of the value (interpreted as an angle) of each element of this `NumberSource`.
      Returns:
      A `NumberSource` whose elements have `double` values that are the hyperbolic sines of the values of the elements of this `NumberSource`.

    <!-- -->

    - #### sqrt

          public final NumberSource sqrt()

      Calculates the square root of the value of each element of this `NumberSource`.
      Returns:
      A `NumberSource` whose elements have `double` values that are the square roots of the values of the elements of this `NumberSource`.

    <!-- -->

    - #### stdev

          public final NumberSource stdev()

      Calculates the standard deviation of the values of this `NumberSource`. This method ignores elements with null values.
      Returns:
      A `NumberSource` whose elements have values that are the standard deviations of the values of the elements of this `NumberSource`.

    <!-- -->

    - #### tan

          public final NumberSource tan()

      Calculates the tangent of the value (interpreted as an angle) of each element of this `NumberSource`.
      Returns:
      A `NumberSource` whose elements have `double` values that are the tangents of the values of the elements of this `NumberSource`.

    <!-- -->

    - #### tanh

          public final NumberSource tanh()

      Calculates the hyperbolic tangent of the value (interpreted as an angle) of each element of this `NumberSource`.
      Returns:
      A `NumberSource` whose elements have `double` values that are the interpreted tangents of the values of the elements of this `NumberSource`.

    <!-- -->

    - #### times

          public final NumberSource times(double rhs)

      Multiplies the value of each element of this `NumberSource` by the specified `double` value.
      Parameters:
      `rhs` - The `double` value by which you want to multiply the values of the elements of this `NumberSource`.

      Returns:
      A `NumberSource` whose elements have the `double` values that result from multiplying the values of the elements of this `NumberSource` by the specified value.

    <!-- -->

    - #### times

          public final NumberSource times(float rhs)

      Multiplies the value of each element of this `NumberSource` by the specified `float` value.
      Parameters:
      `rhs` - The `float` value by which you want to multiply the values of the elements of this `NumberSource`.

      Returns:
      A `NumberSource` whose elements have the `float` values that result from multiplying the values of the elements of this `NumberSource` by the specified value.

    <!-- -->

    - #### times

          public final NumberSource times(int rhs)

      Multiplies the value of each element of this `NumberSource` by the specified `int` value.
      Parameters:
      `rhs` - The `int` value by which you want to multiply the values of the elements of this `NumberSource`.

      Returns:
      A `NumberSource` whose elements have the `int` values that result from multiplying the values of the elements of this `NumberSource` by the specified value.

    <!-- -->

    - #### times

          public final NumberSource times(NumberSource rhs)

      Multiplies the value of each element of this `NumberSource` by the values of the elements of the specified `NumberSource`.
      Parameters:
      `rhs` - A `NumberSource` that has elements that have the values by which you want to multiply the values of the elements of this `NumberSource`.

      Returns:
      A `NumberSource` whose elements have the values that result from multiplying the values of the elements of this `NumberSource` by the values of the elements of the specified `NumberSource`.

    <!-- -->

    - #### times

          public final NumberSource times(short rhs)

      Multiplies the value of each element of this `NumberSource` by the specified `short` value.
      Parameters:
      `rhs` - The `short` value by which you want to multiply the values of the elements of this `NumberSource`.

      Returns:
      A `NumberSource` whose elements have the `short` values that result from multiplying the values of the elements of this `NumberSource` by the specified value.

    <!-- -->

    - #### total

          public final NumberSource total()

      Calculates the sum of the values of the elements of this `NumberSource`.
      Returns:
      A `NumberSource` that has an element whose value is sum of the values of the elements of this `NumberSource`.

    <!-- -->

    - #### lead

          public final NumberSource lead(MdmLevelHierarchy dimension,
                                         int offset)

      Selects the elements of this `NumberSource` that are specified by the values of the elements of `dimension` that are the `offset` number of values away from each value of the `dimension` hierarchy that is at the same level of the hierarchy. If this `NumberSource` does not have an element at the specified `offset`, then the value of the corresponding element of the `NumberSource` returned by this method is `null`. Call this method only on a `NumberSource` for an `MdmMeasure`.
      When this `NumberSource` is the `Source` for an `MdmMeasure` that has an `MdmTimeDimension` as an input dimension, and when `dimension` is an `MdmLevelHierarchy` component of the `MdmTimeDimension`, then this method uses the end date and the time span of the value of each element of the hierarchy of time periods to calculate the start of each value. This method then finds the element of the time hierarchy that has the value that is the `offset` number of time periods at the same level of the hierarchy away from the start date of the value.

      In the following example, `units` is the `NumberSource` for an `MdmBaseMeasure` of numbers of product units sold. The `mdmCalHier` object is the `MdmLevelHierarchy` for the CALENDAR_YEAR hierarchy of the TIME_AWJ dimension.

      The inputs of the `units` measure are the `Source` objects for the PRODUCT_AWJ, TIME_AWJ, CHANNEL_AWJ, and CUSTOMER_AWJdimensions. The `timeSel` object is a `Source` that specifies the first nine months of the year 2002, and `prodSel` is a `Source` that specifies the Desktop PCs family of the PRODUCT_PRIMARY hierarchy of the PRODUCT_AWJ dimension. The `chanSel` object is a `Source` that specifies the highest member of the CHANNEL_PRIMARY hierarchy of the CHANNEL_AWJ dimension. The `custSel` object is a `Source` that specifies the highest member of the SHIPMENTS hierarchy of the CUSTOMER_AWJ dimension. The `joinHidden` method causes the elements of the joined `Source` to not appear as an output of `leadResult`.

           NumberSource unitsLead3 = units.lead(mdmCalHier, 3);
           Source measuresDim =
             dp.createListSource(new Source[] { units, unitsLead3 });

           Source leadResult = measuresDim.extract()
                                          .join(measuresDim)
                                          .join(timeSel)
                                          .joinHidden(prodSel)
                                          .joinHidden(chanSel)
                                          .joinHidden(custSel);

      A `Cursor` for `leadResult` has the following values, which are displayed with headings for the customer, channel, and product values, and the months, units sold, and units sold three months later values. The `Source` identifications (IDs) that are the values of the output of `leadResult` that come from joining `measuresDim` to the object returned by the `measureDim.extract()` method, do not appear in the display.
           Total Customers
           Total Channels
           Product Family: Desktop PCs
           ---------------------------
                     Month                   Units Sold  Units Sold Three Months Later
           -----------------------------     ----------  -----------------------------

           CALENDAR_YEAR::MONTH::2002.01     1601        1732
           CALENDAR_YEAR::MONTH::2002.02     1651        1780
           CALENDAR_YEAR::MONTH::2002.03     1690        1840
           CALENDAR_YEAR::MONTH::2002.04     1732        1894
           CALENDAR_YEAR::MONTH::2002.05     1780        1934
           CALENDAR_YEAR::MONTH::2002.06     1840        1967
           CALENDAR_YEAR::MONTH::2002.07     1894        2001
           CALENDAR_YEAR::MONTH::2002.08     1934        2125
           CALENDAR_YEAR::MONTH::2002.09     1967        2205

      The display of the values of `leadResult` shows that, for each element of the `units` measure, the corresponding element of the `unitsLead3` measure has the value of the `units` element that is three time periods after the current element. For example, the `unitsLead3` value for `CALENDAR_YEAR::MONTH::2002.01` (January, 2002) is the `units` value for `CALENDAR_YEAR::MONTH::2002.04` (April, 2002), and so on.
      Parameters:
      `dimension` - An `MdmLevelHierarchy` that is a component of an `MdmPrimaryDimension` that is an input dimension of the `MdmMeasure` that this `NumberSource` represents. Typically, this parameter is a hierarchy of an `MdmTimeDimension`.

      `offset` - The number of values at the same level of the hierarchy to add to or subtract from the value of an element of the `dimension` hierarchy.

      Returns:
      A `NumberSource` that has, for each element of this `NumberSource` that is specified by a value of `dimension`, the element of this `NumberSource` that is specified by the value of `dimension` that is the `offset` number of values at the same level of the hierarchy away from the value of the `dimension`.

    <!-- -->

    - #### lag

          public final NumberSource lag(MdmLevelHierarchy dimension,
                                        int offset)

      Selects the elements of this `NumberSource` that are specified by the values of the elements of `dimension` that are the `offset` number of values away from each value of the `dimension` hierarchy that is at the same level of the hierarchy. If this `NumberSource` does not have an element at the specified `offset`, then the value of the corresponding element of the `NumberSource` returned by this method is `null`. Call this method only on a `NumberSource` for an `MdmMeasure`.
      This method operates in a way similar to the `lead` method, and when the `offset` value is negative, the method produces the same result as the `lead` method with a positive `offset`. The following example uses the same objects as the example in the description of the `lead` method except for the `unitsLag3` object that is returned by calling the `lag` method of the `units` object.

           NumberSource unitsLag3 = units.lag(mdmCalHier, 3);
           measuresDim =
             dp.createListSource(new Source[] { units, unitsLag3 });

           Source lagResult = measuresDim.extract()
                                         .join(measuresDim)
                                         .join(timeSel)
                                         .joinHidden(prodSel)
                                         .joinHidden(chanSel)
                                         .joinHidden(custSel);

      A `Cursor` for `lagResult` has the following values, which are displayed with headings for the customer, channel, and product values, and the months, units sold, and units sold three months before values. The `Source` identifications (IDs) that are the values of the output of `lagResult` that come from joining `measuresDim` to the object returned by the `measureDim.extract()` method, do not appear in the display.
           Total Customers
           Total Channels
           Product Family: Desktop PCs
           ---------------------------
                     Month                   Units Sold  Units Sold Three Months Earlier
           -----------------------------     ----------  -------------------------------

           CALENDAR_YEAR::MONTH::2002.01     1601        2115
           CALENDAR_YEAR::MONTH::2002.02     1651        2368
           CALENDAR_YEAR::MONTH::2002.03     1690        2391
           CALENDAR_YEAR::MONTH::2002.04     1732        1601
           CALENDAR_YEAR::MONTH::2002.05     1780        1651
           CALENDAR_YEAR::MONTH::2002.06     1840        1690
           CALENDAR_YEAR::MONTH::2002.07     1894        1732
           CALENDAR_YEAR::MONTH::2002.08     1934        1780
           CALENDAR_YEAR::MONTH::2002.09     1967        1840

      The display of the values of `lagResult` shows that, for each element of the `units` measure, the corresponding element of the `unitsLag3` measure has the value of the `units` element that is three time periods before the current element. For example, the `unitsLag3` value for `CALENDAR_YEAR::MONTH::2002.04` (April, 2002) is the `units` value for `CALENDAR_YEAR::MONTH::2002.01` (January, 2002), and so on.
      Parameters:
      `dimension` - An `MdmLevelHierarchy` that is a component of an `MdmPrimaryDimension` that is an input dimension of the `MdmMeasure` that this `NumberSource` represents. Typically, this dimension is a hierarchy of an `MdmTimeDimension`.

      `offset` - The number of values at the same level of the hierarchy to add to or subtract from the value of an element of the `dimension` hierarchy.

      Returns:
      A `NumberSource` that has, for each element of this `NumberSource` that is specified by a value of `dimension`, the element of this `NumberSource` that is specified by the value of `dimension` that is the `offset` number of values at the same level of the hierarchy away from the value of the `dimension`.

    <!-- -->

    - #### lagMonths

          public final NumberSource lagMonths(MdmLevelHierarchy timeDim,
                                              int offset)

      Selects the elements of this `NumberSource` that are specified by the month values of `timeDim` that are the `offset` number of months away from each month value of `timeDim`. If `timeDim` does not have an element at the specified `offset`, then the value of the corresponding element of the `NumberSource` returned by this method is `null`. Call this method only on a `NumberSource` for an `MdmMeasure` that has an `MdmTimeDimension` as an input dimension.
      Parameters:
      `timeDim` - An `MdmLevelHierarchy` that is a component of an `MdmTimeDimension` that is an input dimension of the `MdmMeasure` that this `NumberSource` represents.

      `offset` - The number of months to add to or subtract from the month values of the elements of the `timeDim` hierarchy.

      Returns:
      A `NumberSource` that has, for each element of this `NumberSource` that is specified by a month value of `timeDim`, the element of this `NumberSource` that is specified by the month value that is the `offset` number of months away from the value.

    <!-- -->

    - #### lagQuarters

          public final NumberSource lagQuarters(MdmLevelHierarchy timeDim,
                                                int offset)

      Selects the elements of this `NumberSource` that are specified by the quarter values of `timeDim` that are the `offset` number of quarters away from each quarter value of `timeDim`. If `timeDim` does not have an element at the specified `offset`, then the value of the corresponding element of the `NumberSource` returned by this method is `null`. Call this method only on a `NumberSource` for an `MdmMeasure` that has an `MdmTimeDimension` as an input dimension.
      Parameters:
      `timeDim` - An `MdmLevelHierarchy` that is a component of an `MdmTimeDimension` that is an input dimension of the `MdmMeasure` that this `NumberSource` represents.

      `offset` - The number of quarters to add to or subtract from the quarter values of the elements of the `timeDim` hierarchy.

      Returns:
      A `NumberSource` that has, for each element of this `NumberSource` that is specified by a quarter value of `timeDim`, the element of this `NumberSource` that is specified by the quarter value that is the `offset` number of quarters away from the value.

    <!-- -->

    - #### lagYears

          public final NumberSource lagYears(MdmLevelHierarchy timeDim,
                                             int offset)

      Selects the elements of this `NumberSource` that are specified by the year values of `timeDim` that are the `offset` number of years away from each year value of `timeDim`. If `timeDim` does not have an element at the specified `offset`, then the value of the corresponding element of the `NumberSource` returned by this method is `null`. Call this method only on a `NumberSource` for an `MdmMeasure` that has an `MdmTimeDimension` as an input dimension.
      Parameters:
      `timeDim` - An `MdmLevelHierarchy` that is a component of an `MdmTimeDimension` that is an input dimension of the `MdmMeasure` that this `NumberSource` represents.

      `offset` - The number of years to add to or subtract from the year values of the elements of the `timeDim` hierarchy.

      Returns:
      A `NumberSource` that has, for each element of this `NumberSource` that is specified by a year value of `timeDim`, the element of this `NumberSource` that is specified by the year value that is the `offset` number of years away from the value.

    <!-- -->

    - #### lagDays

          public final NumberSource lagDays(MdmLevelHierarchy timeDim,
                                            int offset)

      Selects the elements of this `NumberSource` that are specified by the day values of `timeDim` that are the `offset` number of days away from each day value of `timeDim`. If `timeDim` does not have an element at the specified `offset`, then the value of the corresponding element of the `NumberSource` returned by this method is `null`. Call this method only on a `NumberSource` for an `MdmMeasure` that has an `MdmTimeDimension` as an input dimension.
      Parameters:
      `timeDim` - An `MdmLevelHierarchy` that is a component of an `MdmTimeDimension` that is an input dimension of the `MdmMeasure` that this `NumberSource` represents.

      `offset` - The number of days to add to or subtract from the day values of the elements of the `timeDim` hierarchy.

      Returns:
      A `NumberSource` that has, for each element of this `NumberSource` that is specified by a day value of `timeDim`, the element of this `NumberSource` that is specified by the day value that is the `offset` number of days away from the value.

    <!-- -->

    - #### lagWeeks

          public final NumberSource lagWeeks(MdmLevelHierarchy timeDim,
                                             int offset)

      Selects the elements of this `NumberSource` that are specified by the week values of `timeDim` that are the `offset` number of weeks away from each week value of `timeDim`. If `timeDim` does not have an element at the specified `offset`, then the value of the corresponding element of the `NumberSource` returned by this method is `null`. Call this method only on a `NumberSource` for an `MdmMeasure` that has an `MdmTimeDimension` as an input dimension.
      Parameters:
      `timeDim` - An `MdmLevelHierarchy` that is a component of an `MdmTimeDimension` that is an input dimension of the `MdmMeasure` that this `NumberSource` represents.

      `offset` - The number of weeks to add to or subtract from the week values of the elements of the `timeDim` hierarchy.

      Returns:
      A `NumberSource` that has, for each element of this `NumberSource` that is specified by a week value of `timeDim`, the element of this `NumberSource` that is specified by the week value that is the `offset` number of weeks away from the value.

    <!-- -->

    - #### cumulativeTotal

          public final NumberSource cumulativeTotal(MdmLevelHierarchy dimension,
                                                    int offset)

      For each element of this `NumberSource`, calculates the total of the values of the elements of this `NumberSource` that are specified by the values of the elements of `dimension` that are at the same level of the hierarchy from the first element of `dimension` to the current element of `dimension` plus the number of elements specified by `offset`. Call this method only on a `NumberSource` for an `MdmMeasure`.
      In the following example, `units` is the `NumberSource` for an `MdmBaseMeasure` of the number of product units sold. The `mdmCalHier` object is the `MdmLevelHierarchy` for the CALENDAR_YEAR hierarchy of the TIME_AWJ dimension

      The input dimensions of the `units` measure are PRODUCT_AWJ, TIME_AWJ, CUSTOMER_AWJ, and CHANNEL_AWJ. The `timeSel` object is a `Source` that specifies the first three months of 2001, the quarters of the years 2001 and 2002, and the years 2001 and 2002. The `prodSel` object is a `Source` that specifies the Desktop PCs family of products from the PRODUCT_PRIMARY hierarchy of the PRODUCT_AWJ dimension. The `chanSel` object is a `Source` that specifies the highest member of the CHANNEL_PRIMARY hierarchy of the CHANNEL_AWJ dimension. The `custSel` object is a `Source` that specifies the highest member of the SHIPMENTS hierarchy of the CUSTOMER_AWJ dimension.

           Source unitsCumTotal = units.cumulativeTotal(mdmCalHier, 0);
           Source measuresDim =
             dp.createListSource(new Source[] { units, unitsCumTotal });

           Source result = measuresDim.extract()
                                      .join(measuresDim)
                                      .join(timeSel)
                                      .joinHidden(prodSel)
                                      .joinHidden(chanSel)
                                      .joinHidden(custSel);

      A `Cursor` for `result` has the following values, which are displayed with headings for the total customers, total channels, products value `DTPC`, (Desktop PCs), the time periods, the numbers of units sold, and the cumulative totals for the unit sold. The `Source` identifications (IDs) that are the values of the output of `result` for `measureDim`, which derive from joining `measuresDim` to the object returned by the `measureDim.extract()` method, do not appear in the display.
           Total Customers
           Total Channels
           Product Family: Desktop PCs
           ---------------------------

                Time Period                     Units Sold  Cumulative Total
           --------------------------------     ----------  ----------------
           CALENDAR_YEAR::YEAR::CY2001          24652        91815
           CALENDAR_YEAR::QUARTER::CY2001.Q1     5725        72888
           CALENDAR_YEAR::MONTH::2001.01         1975        69138
           CALENDAR_YEAR::MONTH::2001.02         1874        71012
           CALENDAR_YEAR::MONTH::2001.03         1876        72888
           CALENDAR_YEAR::QUARTER::CY2001.Q2     5845        78733
           CALENDAR_YEAR::QUARTER::CY2001.Q3     6208        84941
           CALENDAR_YEAR::QUARTER::CY2001.Q4     6874        91815
           CALENDAR_YEAR::YEAR::CY2002          22420       114235
           CALENDAR_YEAR::QUARTER::CY2002.Q1     4942        96757
           CALENDAR_YEAR::QUARTER::CY2002.Q2     5352       102109
           CALENDAR_YEAR::QUARTER::CY2002.Q3     5795       107904
           CALENDAR_YEAR::QUARTER::CY2002.Q4     6331       114235

      The display of the values of `result` shows that, for each element of the `units` measure, the corresponding element of the `unitsCumTotal` measure has the total of the values of the `units` elements at the same level from the first element at that level to the current element.

      Parameters:
      `dimension` - An `MdmLevelHierarchy` that is a component of an `MdmPrimaryDimension` that is an input dimension of the `MdmMeasure` that this `NumberSource` represents.

      `offset` - The number of elements of `dimension` relative to the current element of `dimension` to include in specifying the elements of this `NumberSource` for which values you want the cumulative total. An `offset` value of `0` (zero) includes the current value. An `offset` value of `-1` includes all of the values that precede the current value but does not include the current value.

      Returns:
      A `NumberSource` that has, for each element of this `NumberSource`, the total of the values of this `NumberSource` that are specified by the values of the elements of `dimension` that are at the same level from the first element of dimension up to the element that is the `offset` number of elements away from the current element.

    <!-- -->

    - #### cumulativeTotal

          public final NumberSource cumulativeTotal(MdmLevelHierarchy dimension,
                                                    int offset,
                                                    MdmLevel resetLevel)

      For each element of this `NumberSource`, calculates the total of the values of the elements of this `NumberSource` that are specified by the values of the elements of `dimension` that are at the same level of the hierarchy from the first element of `dimension` to the current element of `dimension` plus the number of elements specified by `offset`, with the cumulative total calculation reset at the level specified by `resetLevel`. Call this method only on a `NumberSource` for an `MdmMeasure`.
      Parameters:
      `dimension` - An `MdmLevelHierarchy` that is a component of an `MdmPrimaryDimension` that is an input dimension of the `MdmMeasure` that this `NumberSource` represents.

      `offset` - The number of elements of `dimension` relative to the current element of `dimension` to include in specifying the elements of this `NumberSource` for which values you want the cumulative total. An `offset` value of `0` (zero) includes the current value. An `offset` value of `-1` includes all of the values that precede the current value but does not include the current value.

      `resetLevel` - The `MdmLevel` for the level of the `dimension` hierarchy at which you want the calculation of the cumulative totals to begin anew.

      Returns:
      A `NumberSource` that has, for each element of this `NumberSource`, the total of the values of this `NumberSource` that are specified by the values of the elements of `dimension` that are at the same level from the first element of dimension up to the element that is the `offset` number of elements away from the current element, and that has the cumulative total calculation reset at the specified level of the hierarchy.

    <!-- -->

    - #### cumulativeAverage

          public final NumberSource cumulativeAverage(MdmLevelHierarchy dimension,
                                                      int offset)

      For each element of this `NumberSource`, calculates the average of the values of the elements of this `NumberSource` that are specified by the values of the elements of `dimension` that are at the same level of the hierarchy from the first element of `dimension` to the current element of `dimension` plus the number of elements specified by `offset`. Call this method only on a `NumberSource` for an `MdmMeasure`.
      Parameters:
      `dimension` - An `MdmLevelHierarchy` that is a component of an `MdmPrimaryDimension` that is an input dimension of the `MdmMeasure` that this `NumberSource` represents.

      `offset` - The number of elements of `dimension` relative to the current element of `dimension` to include in specifying the elements of this `NumberSource` for which values you want the cumulative average. An `offset` value of `0` (zero) includes the current value. An `offset` value of `-1` includes all of the values that precede the current value but does not include the current value.

      Returns:
      A `NumberSource` that has, for each element of this `NumberSource`, the average of the values of this `NumberSource` that are specified by the values of the elements of `dimension` that are at the same level from the first element of dimension up to the element that is the `offset` number of elements away from the current element.

    <!-- -->

    - #### cumulativeAverage

          public final NumberSource cumulativeAverage(MdmLevelHierarchy dimension,
                                                      int offset,
                                                      MdmLevel resetLevel)

      For each element of this `NumberSource`, calculates the average of the values of the elements of this `NumberSource` that are specified by the values of the elements of `dimension` that are at the same level of the hierarchy from the first element of `dimension` to the current element of `dimension` plus the number of elements specified by `offset`, with the cumulative average calculation reset at the level specified by `resetLevel`. Call this method only on a `NumberSource` for an `MdmMeasure`.
      Parameters:
      `dimension` - An `MdmLevelHierarchy` that is a component of an `MdmPrimaryDimension` that is an input dimension of the `MdmMeasure` that this `NumberSource` represents.

      `offset` - The number of elements of `dimension` relative to the current element of `dimension` to include in specifying the elements of this `NumberSource` for which values you want the cumulative average. An `offset` value of `0` (zero) includes the current value. An `offset` value of `-1` includes all of the values that precede the current value but does not include the current value.

      `resetLevel` - The `MdmLevel` for the level of the `dimension` hierarchy at which you want the calculation of the cumulative average to begin anew.

      Returns:
      A `NumberSource` that has, for each element of this `NumberSource`, the average of the values of this `NumberSource` that are specified by the values of the elements of `dimension` that are at the same level from the first element of dimension up to the element that is the `offset` number of elements away from the current element, and that has the cumulative average calculation reset at the specified level of the hierarchy.

    <!-- -->

    - #### cumulativeMaximum

          public final NumberSource cumulativeMaximum(MdmLevelHierarchy dimension,
                                                      int offset)

      For each element of this `NumberSource`, calculates the maximum value of the elements of this `NumberSource` that are specified by the values of the elements of `dimension` that are at the same level of the hierarchy from the first element of `dimension` to the current element of `dimension` plus the number of elements specified by `offset`. Call this method only on a `NumberSource` for an `MdmMeasure`.
      Parameters:
      `dimension` - An `MdmLevelHierarchy` that is a component of an `MdmPrimaryDimension` that is an input dimension of the `MdmMeasure` that this `NumberSource` represents.

      `offset` - The number of elements of `dimension` relative to the current element of `dimension` to include in specifying the elements of this `NumberSource` for which values you want the cumulative maximum. An `offset` value of `0` (zero) includes the current value. An `offset` value of `-1` includes all of the values that precede the current value but does not include the current value.

      Returns:
      A `NumberSource` that has, for each element of this `NumberSource`, the maximum value of this `NumberSource` of the values that are specified by the values of the elements of `dimension` that are at the same level from the first element of dimension up to the element that is the `offset` number of elements away from the current element.

    <!-- -->

    - #### cumulativeMaximum

          public final NumberSource cumulativeMaximum(MdmLevelHierarchy dimension,
                                                      int offset,
                                                      MdmLevel resetLevel)

      For each element of this `NumberSource`, calculates the maximum value of the elements of this `NumberSource` that are specified by the values of the elements of `dimension` that are at the same level of the hierarchy from the first element of `dimension` to the current element of `dimension` plus the number of elements specified by `offset`, with the cumulative maximum calculation reset at the level specified by `resetLevel`. Call this method only on a `NumberSource` for an `MdmMeasure`.
      Parameters:
      `dimension` - An `MdmLevelHierarchy` that is a component of an `MdmPrimaryDimension` that is an input dimension of the `MdmMeasure` that this `NumberSource` represents.

      `offset` - The number of elements of `dimension` relative to the current element of `dimension` to include in specifying the elements of this `NumberSource` for which values you want the cumulative maximum. An `offset` value of `0` (zero) includes the current value. An `offset` value of `-1` includes all of the values that precede the current value but does not include the current value.

      `resetLevel` - The `MdmLevel` for the level of the `dimension` hierarchy at which you want the calculation of the cumulative maximum to begin anew.

      Returns:
      A `NumberSource` that has, for each element of this `NumberSource`, the maximum value of this `NumberSource` of the values that are specified by the values of the elements of `dimension` that are at the same level from the first element of dimension up to the element that is the `offset` number of elements away from the current element, and that has the cumulative maximum calculation reset at the specified level of the hierarchy.

    <!-- -->

    - #### cumulativeMinimum

          public final NumberSource cumulativeMinimum(MdmLevelHierarchy dimension,
                                                      int offset)

      For each element of this `NumberSource`, calculates the minimum value of the elements of this `NumberSource` that are specified by the values of the elements of `dimension` that are at the same level of the hierarchy from the first element of `dimension` to the current element of `dimension` plus the number of elements specified by `offset`. Call this method only on a `NumberSource` for an `MdmMeasure`.
      Parameters:
      `dimension` - An `MdmLevelHierarchy` that is a component of an `MdmPrimaryDimension` that is an input dimension of the `MdmMeasure` that this `NumberSource` represents.

      `offset` - The number of elements of `dimension` relative to the current element of `dimension` to include in specifying the elements of this `NumberSource` for which values you want the cumulative minimum. An `offset` value of `0` (zero) includes the current value. An `offset` value of `-1` includes all of the values that precede the current value but does not include the current value.

      Returns:
      A `NumberSource` that has, for each element of this `NumberSource`, the minimum value of this `NumberSource` of the values that are specified by the values of the elements of `dimension` that are at the same level from the first element of dimension up to the element that is the `offset` number of elements away from the current element.

    <!-- -->

    - #### cumulativeMinimum

          public final NumberSource cumulativeMinimum(MdmLevelHierarchy dimension,
                                                      int offset,
                                                      MdmLevel resetLevel)

      For each element of this `NumberSource`, calculates the minimum value of the elements of this `NumberSource` that are specified by the values of the elements of `dimension` that are at the same level of the hierarchy from the first element of `dimension` to the current element of `dimension` plus the number of elements specified by `offset`, with the cumulative minimum calculation reset at the level specified by `resetLevel`. Call this method only on a `NumberSource` for an `MdmMeasure`.
      Parameters:
      `dimension` - An `MdmLevelHierarchy` that is a component of an `MdmPrimaryDimension` that is an input dimension of the `MdmMeasure` that this `NumberSource` represents.

      `offset` - The number of elements of `dimension` relative to the current element of `dimension` to include in specifying the elements of this `NumberSource` for which values you want the cumulative minimum. An `offset` value of `0` (zero) includes the current value. An `offset` value of `-1` includes all of the values that precede the current value but does not include the current value.

      `resetLevel` - The `MdmLevel` for the level of the `dimension` hierarchy at which you want the calculation of the cumulative minimum to begin anew.

      Returns:
      A `NumberSource` that has, for each element of this `NumberSource`, the minimum value of this `NumberSource` of the values that are specified by the values of the elements of `dimension` that are at the same level from the first element of dimension up to the element that is the `offset` number of elements away from the current element, and that has the cumulative minimum calculation reset at the specified level of the hierarchy.

    <!-- -->

    - #### movingTotal

          public final NumberSource movingTotal(MdmLevelHierarchy dimension,
                                                int startOffset,
                                                int endOffset)

      For each element of this `NumberSource`, calculates the total of the values of the elements of this `NumberSource` that are specified by the values of the elements of `dimension` that are at the same level of the hierarchy from the element of `dimension` specified by `startOffset` to the element specified by `endOffset`. A negative offset value specifies a value before the current value, a `0` (zero) value specifies the current value, and a positive value specifies a value after the current value. Call this method only on a `NumberSource` for an `MdmMeasure`.
      Parameters:
      `dimension` - An `MdmLevelHierarchy` that is a component of an `MdmPrimaryDimension` that is an input dimension of the `MdmMeasure` that this `NumberSource` represents.

      `startOffset` - The number of elements of `dimension` relative to the current element of `dimension` that marks the beginning of the elements to include in the specification of the elements of this `NumberSource` the values of which you want to total.

      `endOffset` - The number of elements of `dimension` relative to the current element of `dimension` that marks the end of the elements to include in the specification of the elements of this `NumberSource` the values of which you want to total.

      Returns:
      A `NumberSource` that has, for each element of this `NumberSource`, the total of the values of this `NumberSource` that are specified by the values of the elements of `dimension` that are at the same level from the `startOffset` element of dimension up to the `endOffset` element.

    <!-- -->

    - #### movingAverage

          public final NumberSource movingAverage(MdmLevelHierarchy dimension,
                                                  int startOffset,
                                                  int endOffset)

      For each element of this `NumberSource`, calculates the average of the values of the elements of this `NumberSource` that are specified by the values of the elements of `dimension` that are at the same level of the hierarchy from the element of `dimension` specified by `startOffset` to the element specified by `endOffset`. A negative offset value specifies a value before the current value, a `0` (zero) value specifies the current value, and a positive value specifies a value after the current value. Call this method only on a `NumberSource` for an `MdmMeasure`.
      Parameters:
      `dimension` - An `MdmLevelHierarchy` that is a component of an `MdmPrimaryDimension` that is an input dimension of the `MdmMeasure` that this `NumberSource` represents.

      `startOffset` - The number of elements of `dimension` relative to the current element of `dimension` that marks the beginning of the elements to include in the specification of the elements of this `NumberSource` the values of which you want to average.

      `endOffset` - The number of elements of `dimension` relative to the current element of `dimension` that marks the end of the elements to include in the specification of the elements of this `NumberSource` the values of which you want to average.

      Returns:
      A `NumberSource` that has, for each element of this `NumberSource`, the average of the values of this `NumberSource` that are specified by the values of the elements of `dimension` that are at the same level from the `startOffset` element of dimension up to the `endOffset` element.

    <!-- -->

    - #### movingMaximum

          public final NumberSource movingMaximum(MdmLevelHierarchy dimension,
                                                  int startOffset,
                                                  int endOffset)

      For each element of this `NumberSource`, determines the maximum value of the elements of this `NumberSource` that are specified by the values of the elements of `dimension` that are at the same level of the hierarchy from the element of `dimension` specified by `startOffset` to the element specified by `endOffset`. A negative offset value specifies a value before the current value, a `0` (zero) value specifies the current value, and a positive value specifies a value after the current value. Call this method only on a `NumberSource` for an `MdmMeasure`.
      Parameters:
      `dimension` - An `MdmLevelHierarchy` that is a component of an `MdmPrimaryDimension` that is an input dimension of the `MdmMeasure` that this `NumberSource` represents.

      `startOffset` - The number of elements of `dimension` relative to the current element of `dimension` that marks the beginning of the elements of this `NumberSource` to search for the maximum value.

      `endOffset` - The number of elements of `dimension` relative to the current element of `dimension` that marks the end of the elements of this `NumberSource` to search for the maximum value.

      Returns:
      A `NumberSource` that has, for each element of this `NumberSource`, the maximum value of the elements of this `NumberSource` that are specified by the values of the elements of `dimension` that are at the same level from the `startOffset` element of dimension up to the `endOffset` element.

    <!-- -->

    - #### movingMinimum

          public final NumberSource movingMinimum(MdmLevelHierarchy dimension,
                                                  int startOffset,
                                                  int endOffset)

      For each element of this `NumberSource`, determines the minimum value of the elements of this `NumberSource` that are specified by the values of the elements of `dimension` that are at the same level of the hierarchy from the element of `dimension` specified by `startOffset` to the element specified by `endOffset`. A negative offset value specifies a value before the current value, a `0` (zero) value specifies the current value, and a positive value specifies a value after the current value. Call this method only on a `NumberSource` for an `MdmMeasure`.
      Parameters:
      `dimension` - An `MdmLevelHierarchy` that is a component of an `MdmPrimaryDimension` that is an input dimension of the `MdmMeasure` that this `NumberSource` represents.

      `startOffset` - The number of elements of `dimension` relative to the current element of `dimension` that marks the beginning of the elements of this `NumberSource` to search for the minimum value.

      `endOffset` - The number of elements of `dimension` relative to the current element of `dimension` that marks the end of the elements of this `NumberSource` to search for the minimum value.

      Returns:
      A `NumberSource` that has, for each element of this `NumberSource`, the minimum value of the elements of this `NumberSource` that are specified by the values of the elements of `dimension` that are at the same level from the `startOffset` element of dimension up to the `endOffset` element.

    <!-- -->

    - #### median

          public final NumberSource median()

      Calculates the median values of the elements of this `NumberSource`.
      Returns:
      A `NumberSource` that has an element whose value is sum of the values of the elements of this `NumberSource`.

    <!-- -->

    - #### variance

          public final NumberSource variance()

      Calculates the variance of the elements of this `NumberSource`.
      Returns:
      A `NumberSource` whose element values are the variance of the values of the elements of this `NumberSource`.

    <!-- -->

    - #### variancePop

          public final NumberSource variancePop()

      Calculates the population variance of the elements of this `NumberSource`. This method ignores elements with null values.
      Returns:
      A `NumberSource` whose element values are the population variance of the values of the elements of this `NumberSource`.

    <!-- -->

    - #### varianceSamp

          public final NumberSource varianceSamp()

      Calculates the sample variance of the elements of this `NumberSource`.
      Returns:
      A `NumberSource` whose element values are the sample variance of the values of the elements of this `NumberSource`.

    <!-- -->

    - #### stdevPop

          public final NumberSource stdevPop()

      Calculates the population standard deviation of the values of this `NumberSource`.
      Returns:
      A `NumberSource` whose elements have values that are the square roots of the population variances of the values of the elements of this `NumberSource`.

    <!-- -->

    - #### stdevSamp

          public final NumberSource stdevSamp()

      Calculates the cumulative sample standard deviation of the values of this `NumberSource`.
      Returns:
      A `NumberSource` whose elements have values that are the square roots of the sample variances of the values of the elements of this `NumberSource`.

    <!-- -->

    - #### positionalPeriodsAgo

          public final NumberSource positionalPeriodsAgo(MdmLevelHierarchy hierarchy,
                                                         MdmLevel offsetLevel,
                                                         int offset)

      Selects the elements of this `NumberSource` that are specified by the members of `offsetLevel` that are the `offset` number of positions away from each member of the `offsetLevel` level of the hierarchy. This method assumes that the hierarchy is a component of a time dimension and that the members of the level are in consecutive sequence.
      The `positionalPeriodsAgo` method is similar to the `lead` or `lag` methods, except that it does not expect that the time hierarchy is based on a Gregorian calendar.

      If the value of the `offset` parameter is positive, then this method functions like the `lag` method. If the `offset` value is negative, then this method functions like the `lead` method.

      Call this method only on a `NumberSource` for an `MdmMeasure`. If the `NumberSource` does not have an element for the level member at the specified `offset`, then the value of the corresponding element of the `NumberSource` returned by this method is `null`.

      Parameters:
      `hierarchy` - An `MdmLevelHierarchy` that is a component of an `MdmTimeDimension` that is an input dimension of the `MdmMeasure` that this `NumberSource` represents.

      `offsetLevel` - An `MdmLevel` that is a component of the hierarchy.

      `offset` - The number of positions to add to or subtract from the position of each of the elements of the level.

      Returns:
      A `NumberSource` that has the elements of this `NumberSource` that are specified by the members of the level that are at the specified positions.

      See Also:
      `lead(oracle.olapi.metadata.mdm.MdmLevelHierarchy, int)`, `lag(oracle.olapi.metadata.mdm.MdmLevelHierarchy, int)`

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](NumberParameter.md)
- [Next Class](Parameter.md)

<!-- -->

- [Frames](../../../../index.md)
- No Frames

<!-- -->

- [All Classes](../../../../allclasses-noframe.md)

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
