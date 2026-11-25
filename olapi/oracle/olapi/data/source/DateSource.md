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

- [Prev Class](DateParameter.md)
- [Next Class](DynamicDefinition.md)

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

## Class DateSource

- java.lang.Object

- - [oracle.olapi.data.source.Source](Source.md)

  - - oracle.olapi.data.source.DateSource

<!-- -->

- All Implemented Interfaces:
  [SourceIdentifier](../cursor/SourceIdentifier.md)

  ------------------------------------------------------------------------



      public final class DateSource
      extends Source

  A `Source` whose elements have `Date` objects as values. A `DateSource` has an OLAP Java API data type of Date. This class implements some `Source` methods so that they use `Date` values, such as `appendValue`, and implements other methods that perform Date operations, such as `plusDays`.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from class oracle.olapi.data.source.[Source](Source.md)

      [`COMPARISON_RULE_ASCENDING`](Source.md)`, `[`COMPARISON_RULE_ASCENDING_NULLS_FIRST`](Source.md)`, `[`COMPARISON_RULE_ASCENDING_NULLS_LAST`](Source.md)`, `[`COMPARISON_RULE_DESCENDING`](Source.md)`, `[`COMPARISON_RULE_DESCENDING_NULLS_FIRST`](Source.md)`, `[`COMPARISON_RULE_DESCENDING_NULLS_LAST`](Source.md)`, `[`COMPARISON_RULE_REMOVE`](Source.md)`, `[`COMPARISON_RULE_SELECT`](Source.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                   | Method and Description                                                                                                                                                       |
    |-------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `DateSource`                        | `appendValue``(java.util.Date appendValue)`<br>Appends the specified `Date` object to this `DateSource`.                                                                     |
    | `DateSource`                        | `appendValues``(java.util.Date[] appendValues)`<br>Appends the specified `Date` objects to this `DateSource`.                                                                |
    | [`BooleanSource`](BooleanSource.md) | `eq``(java.util.Date rhs)`<br>Compares the value of each element of this `DateSource` to the specified `Date` value and determines they are equal.                           |
    | [`BooleanSource`](BooleanSource.md) | `ge``(java.util.Date rhs)`<br>Compares the value of each element of this `DateSource` to the specified `Date` value, and determines whether it has a greater or equal value. |
    | [`Source`](Source.md)               | `getDataType``()`<br>Gets the fundamental `Source` that represents the OLAP Java API data type of this `DateSource`, which is Date.                                          |
    | [`BooleanSource`](BooleanSource.md) | `gt``(java.util.Date rhs)`<br>Compares the value of each element of this `DateSource` to the specified `Date` value, and determines whether it has a greater value.          |
    | [`BooleanSource`](BooleanSource.md) | `le``(java.util.Date rhs)`<br>Compares the value of each element of this `DateSource` to the specified `Date` value, and determines whether it has a lesser or equal value.  |
    | [`BooleanSource`](BooleanSource.md) | `lt``(java.util.Date rhs)`<br>Compares the value of each element of this `DateSource` to the specified `Date` value, and determines whether it has a lesser value.           |
    | [`BooleanSource`](BooleanSource.md) | `ne``(java.util.Date rhs)`<br>Compares the value of each element of this `DateSource` to the specified `Date` value, and determines whether it is not equal to the value.    |
    | `DateSource`                        | `plusDays``(int rhs)`<br>Adds the specified number of days to the value of each element of this `DateSource`.                                                                |
    | `DateSource`                        | `plusDays``(`[`NumberSource`](NumberSource.md)` rhs)`<br>Adds the specified number of days to the value of each element of this `DateSource`.                                |
    | `DateSource`                        | `plusMonths``(int rhs)`<br>Adds the specified number of months to the value of each element of this `DateSource`.                                                            |
    | `DateSource`                        | `plusMonths``(`[`NumberSource`](NumberSource.md)` rhs)`<br>Adds the specified number of months to the value of each element of this `DateSource`.                            |
    | [`NumberSource`](NumberSource.md)   | `positionOfValue``(java.util.Date value)`<br>Identifies the positions of elements in this `DateSource` that have the specified `Date` values.                                |
    | [`NumberSource`](NumberSource.md)   | `positionOfValues``(java.util.Date[] values)`<br>Identifies the positions of elements in this `DateSource` that have the specified `Date` values.                            |
    | `DateSource`                        | `removeValue``(java.util.Date value)`<br>Removes the elements of this `DateSource` that have the specified `Date` value.                                                     |
    | `DateSource`                        | `removeValues``(java.util.Date[] values)`<br>Removes the elements of this `DateSource` that have the specified `Date` values.                                                |
    | `DateSource`                        | `selectValue``(java.util.Date value)`<br>Selects the elements of this `DateSource` that have the specified `Date` value.                                                     |
    | `DateSource`                        | `selectValues``(java.util.Date[] values)`<br>Selects the elements of this `DateSource` that have the specified `Date` values.                                                |

    - ### Methods inherited from class oracle.olapi.data.source.[Source](Source.md)

      [`alias`](Source.md)`, `[`appendValue`](Source.md)`, `[`appendValues`](Source.md)`, `[`appendValues`](Source.md)`, `[`at`](Source.md)`, `[`at`](Source.md)`, `[`count`](Source.md)`, `[`count`](Source.md)`, `[`cumulativeInterval`](Source.md)`, `[`cumulativeInterval`](Source.md)`, `[`cumulativeInterval`](Source.md)`, `[`distinct`](Source.md)`, `[`eq`](Source.md)`, `[`extract`](Source.md)`, `[`findMatchFor`](Source.md)`, `[`first`](Source.md)`, `[`ge`](Source.md)`, `[`getDataProvider`](Source.md)`, `[`getDefinition`](Source.md)`, `[`getExtractionInputs`](Source.md)`, `[`getID`](Source.md)`, `[`getInputs`](Source.md)`, `[`getMetadataProvider`](Source.md)`, `[`getMetadataProviderID`](Source.md)`, `[`getModel`](Source.md)`, `[`getOutputs`](Source.md)`, `[`getRegularInputs`](Source.md)`, `[`getType`](Source.md)`, `[`gt`](Source.md)`, `[`hasValue`](Source.md)`, `[`in`](Source.md)`, `[`interval`](Source.md)`, `[`interval`](Source.md)`, `[`isSubtypeOf`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`joinHidden`](Source.md)`, `[`last`](Source.md)`, `[`le`](Source.md)`, `[`lt`](Source.md)`, `[`movingInterval`](Source.md)`, `[`movingInterval`](Source.md)`, `[`ne`](Source.md)`, `[`nullSource`](Source.md)`, `[`offset`](Source.md)`, `[`offset`](Source.md)`, `[`position`](Source.md)`, `[`position`](Source.md)`, `[`positionOfValue`](Source.md)`, `[`positionOfValues`](Source.md)`, `[`positionOfValues`](Source.md)`, `[`recursiveJoin`](Source.md)`, `[`recursiveJoin`](Source.md)`, `[`recursiveJoin`](Source.md)`, `[`recursiveJoin`](Source.md)`, `[`recursiveJoin`](Source.md)`, `[`recursiveJoin`](Source.md)`, `[`recursiveJoin`](Source.md)`, `[`remove`](Source.md)`, `[`removeValue`](Source.md)`, `[`removeValues`](Source.md)`, `[`removeValues`](Source.md)`, `[`select`](Source.md)`, `[`selectDescendants`](Source.md)`, `[`selectValue`](Source.md)`, `[`selectValues`](Source.md)`, `[`selectValues`](Source.md)`, `[`sortAscending`](Source.md)`, `[`sortAscending`](Source.md)`, `[`sortAscending`](Source.md)`, `[`sortAscendingHierarchically`](Source.md)`, `[`sortAscendingHierarchically`](Source.md)`, `[`sortAscendingHierarchically`](Source.md)`, `[`sortAscendingHierarchically`](Source.md)`, `[`sortDescending`](Source.md)`, `[`sortDescending`](Source.md)`, `[`sortDescending`](Source.md)`, `[`sortDescendingHierarchically`](Source.md)`, `[`sortDescendingHierarchically`](Source.md)`, `[`sortDescendingHierarchically`](Source.md)`, `[`sortDescendingHierarchically`](Source.md)`, `[`toDoubleSource`](Source.md)`, `[`toFloatSource`](Source.md)`, `[`toIntegerSource`](Source.md)`, `[`toShortSource`](Source.md)`, `[`toStringSource`](Source.md)`, `[`value`](Source.md)`, `[`value`](Source.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### appendValue

          public final DateSource appendValue(java.util.Date appendValue)

      Appends the specified `Date` object to this `DateSource`.
      Parameters:
      `appendValue` - The `Date` to append to this `DateSource`.

      Returns:
      A `DateSource` that has the same elements as this `DateSource` with an appended element that has the specified `Date` as its value.

    <!-- -->

    - #### appendValues

          public final DateSource appendValues(java.util.Date[] appendValues)

      Appends the specified `Date` objects to this `DateSource`.
      Parameters:
      `appendValues` - An array of `Date` objects to append to this `DateSource`.

      Returns:
      A `DateSource` that has the same elements as this `DateSource` with appended elements that have the specified `Date` objects as values.

    <!-- -->

    - #### eq

          public final BooleanSource eq(java.util.Date rhs)

      Compares the value of each element of this `DateSource` to the specified `Date` value and determines they are equal.
      Parameters:
      `rhs` - The `Date` value that you want to compare to the values of the elements of this `DateSource`.

      Returns:
      A `BooleanSource` that has an element that has a value of `true` when the value of the corresponding element of this `DateSource` equals the specified `Date` value, or `false` when it does not.

    <!-- -->

    - #### ge

          public final BooleanSource ge(java.util.Date rhs)

      Compares the value of each element of this `DateSource` to the specified `Date` value, and determines whether it has a greater or equal value. The `BooleanSource` returned by this method has an element that is `true` when the value of a given element of this `DateSource` is greater than or equal to the specified `Date` value, or a value of `false` when it is not.
      Parameters:
      `rhs` - The `Date` value that you want to compare to the values of the elements of this `DateSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of a given element of this `DateSource` is greater than or equal to the specified `Date` value, or `false` when it is not.

    <!-- -->

    - #### getDataType

          public Source getDataType()

      Gets the fundamental `Source` that represents the OLAP Java API data type of this `DateSource`, which is Date.
      Overrides:
      [`getDataType`](Source.md) in class [`Source`](Source.md)

      Returns:
      The fundamental `Source` that represents the OLAP Java API Date data type.

    <!-- -->

    - #### gt

          public final BooleanSource gt(java.util.Date rhs)

      Compares the value of each element of this `DateSource` to the specified `Date` value, and determines whether it has a greater value.
      Parameters:
      `rhs` - The `Date` value that you want to compare to the values of the elements of this `DateSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of the corresponding element of this `DateSource` is greater than the specified `Date` value, or `false` when it is not.

    <!-- -->

    - #### le

          public final BooleanSource le(java.util.Date rhs)

      Compares the value of each element of this `DateSource` to the specified `Date` value, and determines whether it has a lesser or equal value.
      Parameters:
      `rhs` - The `boolean` value that you want to compare to the values of the elements of this `DateSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of the corresponding element of this `DateSource` is less than or equal to the specified `Date` value, or `false` when it is not.

    <!-- -->

    - #### lt

          public final BooleanSource lt(java.util.Date rhs)

      Compares the value of each element of this `DateSource` to the specified `Date` value, and determines whether it has a lesser value.
      Parameters:
      `rhs` - The `Date` value that you want to compare to the values of the elements of this `DateSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of a given element of this `DateSource` is less than the specified `Date` value, or `false` when it is not.

    <!-- -->

    - #### ne

          public final BooleanSource ne(java.util.Date rhs)

      Compares the value of each element of this `DateSource` to the specified `Date` value, and determines whether it is not equal to the value.
      Parameters:
      `rhs` - The `Date` value that you want to compare to the values of the elements of this `DateSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of a given element of this `DateSource` is not equal to the specified `Date` value, or `false` when it is equal to the specified value.

    <!-- -->

    - #### plusDays

          public final DateSource plusDays(int rhs)

      Adds the specified number of days to the value of each element of this `DateSource`. For example, the following code creates a `DateSource`, `aDate`, and then adds five days to the value of `aDate`. The `dp` object is the `DataProvider`.
           // Get an instance of a java.util.Calendar object.
           Calendar calendar =  Calendar.getInstance();
           // Set the date and time for the Calendar object.
           calendar.set(2009, 6, 17, 14, 24, 23);
           // Get a java.util.Date object from the Calendar object.
           Date date = calendar.getTime();
           // Create a DateSource using the Date object.
           DateSource aDate = dp.createConstantSource(date);
           DateSource aDatePlus5 = aDate.plusDays(5);

      If the value of `aDate` is `Fri Jul 17 19:24:23 GMT-05:00 2009`, then the value of `aDatePlus5` is `Wed Jul 22 19:24:23 GMT-05:00 2009`.
      Parameters:
      `rhs` - The `int` value that specifies the number of days that you want to add to the values of the elements of this `DateSource`.

      Returns:
      A `DateSource` that has the elements of this `DateSource` with the `Date` value of each element increased by the specified number of days.

    <!-- -->

    - #### plusDays

          public final DateSource plusDays(NumberSource rhs)

      Adds the specified number of days to the value of each element of this `DateSource`.
      Parameters:
      `rhs` - A `NumberSource` whose element values specify the number of days that you want to add to the values of the elements of this `DateSource`.

      Returns:
      A `DateSource` that has elements whose values are the `Date` values of this `DateSource` increased by the number of days specified by `rhs`.

    <!-- -->

    - #### plusMonths

          public final DateSource plusMonths(int rhs)

      Adds the specified number of months to the value of each element of this `DateSource`.
      Parameters:
      `rhs` - The `int` value that specifies the number of months that you want to add to the values of the elements of this `DateSource`.

      Returns:
      A `DateSource` that has the elements of this `DateSource` with the `Date` value of each element increased by the specified number of months.

    <!-- -->

    - #### plusMonths

          public final DateSource plusMonths(NumberSource rhs)

      Adds the specified number of months to the value of each element of this `DateSource`.
      Parameters:
      `rhs` - A `NumberSource` whose element values specify the number of months that you want to add to the values of the elements of this `DateSource`.

      Returns:
      A `DateSource` that has elements whose values are the `Date` values of this `DateSource` increased by the number of months specified by `rhs`.

    <!-- -->

    - #### positionOfValue

          public final NumberSource positionOfValue(java.util.Date value)

      Identifies the positions of elements in this `DateSource` that have the specified `Date` values.
      Parameters:
      `value` - A `DateSource` that has the values that you want to compare to the values of the elements of this `DateSource`.

      Returns:
      A `NumberSource` whose elements have `int` values that identify the positions of the elements in this `DateSource` that have the specified `Date` values. If this `DateSource` does not have any elements that have the specified values, then this method returns an empty `NumberSource`, which has no elements.

    <!-- -->

    - #### positionOfValues

          public final NumberSource positionOfValues(java.util.Date[] values)

      Identifies the positions of elements in this `DateSource` that have the specified `Date` values.
      Parameters:
      `values` - An array of `Date` values that you want to compare to the values of the elements of this `DateSource`.

      Returns:
      A `NumberSource` whose elements have `int` values that identify the positions of the elements in this `DateSource` that have the specified `Date` values. If this `DateSource` does not have any elements that have the specified values, then this method returns an empty `NumberSource`, which has no elements.

    <!-- -->

    - #### removeValue

          public final DateSource removeValue(java.util.Date value)

      Removes the elements of this `DateSource` that have the specified `Date` value.
      Parameters:
      `value` - The `Date` value you do not want to have in the returned `DateSource`.

      Returns:
      A `DateSource` that has the elements of this `DateSource` that do not have the specified `Date` value.

    <!-- -->

    - #### removeValues

          public final DateSource removeValues(java.util.Date[] values)

      Removes the elements of this `DateSource` that have the specified `Date` values.
      Parameters:
      `values` - A `DateSource` that has the `Date` values you do not want to have in the returned `DateSource`.

      Returns:
      A `DateSource` that has the elements of this `DateSource` that do not have the specified `Date` values.

    <!-- -->

    - #### selectValue

          public final DateSource selectValue(java.util.Date value)

      Selects the elements of this `DateSource` that have the specified `Date` value.
      Parameters:
      `value` - The `Date` value to compare to the values of the elements of this `DateSource`.

      Returns:
      A `DateSource` that has the elements of this `DateSource` that have the specified `Date` value.

    <!-- -->

    - #### selectValues

          public final DateSource selectValues(java.util.Date[] values)

      Selects the elements of this `DateSource` that have the specified `Date` values.
      Parameters:
      `values` - A `DateSource` that has the values to compare to the values of the elements of this `DateSource`.

      Returns:
      A `DateSource` that has the elements of this `DateSource` that have the specified `Date` values.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](DateParameter.md)
- [Next Class](DynamicDefinition.md)

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
