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

- [Prev Class](BooleanParameter.md)
- [Next Class](BuildProperties.md)

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

## Class BooleanSource

- java.lang.Object

- - [oracle.olapi.data.source.Source](Source.md)

  - - oracle.olapi.data.source.BooleanSource

<!-- -->

- All Implemented Interfaces:
  [SourceIdentifier](../cursor/SourceIdentifier.md)

  ------------------------------------------------------------------------



      public final class BooleanSource
      extends Source

  A `Source` whose elements have `boolean` values. A `BooleanSource` object has an OLAP Java API data type of Boolean. This class implements some `Source` methods so that they use `boolean` values, such as `appendValue` and `eq`, and implements other boolean operations such as the `and`, `or`, and `forAny` methods.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from class oracle.olapi.data.source.[Source](Source.md)

      [`COMPARISON_RULE_ASCENDING`](Source.md)`, `[`COMPARISON_RULE_ASCENDING_NULLS_FIRST`](Source.md)`, `[`COMPARISON_RULE_ASCENDING_NULLS_LAST`](Source.md)`, `[`COMPARISON_RULE_DESCENDING`](Source.md)`, `[`COMPARISON_RULE_DESCENDING_NULLS_FIRST`](Source.md)`, `[`COMPARISON_RULE_DESCENDING_NULLS_LAST`](Source.md)`, `[`COMPARISON_RULE_REMOVE`](Source.md)`, `[`COMPARISON_RULE_SELECT`](Source.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                 | Method and Description                                                                                                                                                                                                                                                                                                                                                |
    |-----------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `BooleanSource`                   | `and``(boolean rhs)`<br>Performs a logical AND operation between the values of the elements of this `BooleanSource` and the specified `boolean` value.                                                                                                                                                                                                                |
    | `BooleanSource`                   | `and``(BooleanSource rhs)`<br>Performs a logical AND operation between the values of the elements of this `BooleanSource` and the values of the corresponding elements of the specified `BooleanSource`.                                                                                                                                                              |
    | `BooleanSource`                   | `appendValue``(boolean appendValue)`<br>Appends an element with the specified `boolean` value to this `BooleanSource`.                                                                                                                                                                                                                                                |
    | `BooleanSource`                   | `appendValues``(boolean[] appendValues)`<br>Appends elements with the specified `boolean` values to this `BooleanSource`.                                                                                                                                                                                                                                             |
    | `BooleanSource`                   | `eq``(boolean rhs)`<br>Compares the value of each element of this `BooleanSource` to the specified `boolean` value and determines if the values are equal.                                                                                                                                                                                                            |
    | `BooleanSource`                   | `forAll``()`<br>Indicates whether the values of all of the elements of this `BooleanSource` are `true`.                                                                                                                                                                                                                                                               |
    | `BooleanSource`                   | `forAll``(boolean noValueAsFalse)`<br>Indicates whether the values of all of the elements of this `BooleanSource` are `true`.                                                                                                                                                                                                                                         |
    | `BooleanSource`                   | `forAny``()`<br>Indicates whether the value of any of the elements of this `BooleanSource` is `true`.                                                                                                                                                                                                                                                                 |
    | `BooleanSource`                   | `forAny``(boolean noValueAsFalse)`<br>Indicates whether the value of any of the elements of this `BooleanSource` is `true`.                                                                                                                                                                                                                                           |
    | `BooleanSource`                   | `forNone``()`<br>Indicates whether the value of none of the elements of this `BooleanSource` is `true`.                                                                                                                                                                                                                                                               |
    | `BooleanSource`                   | `forNone``(boolean noValueAsFalse)`<br>Indicates whether the value of none of the elements of this `BooleanSource` is `true`.                                                                                                                                                                                                                                         |
    | `BooleanSource`                   | `ge``(boolean rhs)`<br>Compares the value of each element of this `BooleanSource` to the specified `boolean` value, and determines whether it is a greater or equal value.                                                                                                                                                                                            |
    | [`Source`](Source.md)             | `getDataType``()`<br>Gets the fundamental `Source` that represents the OLAP Java API data type of this `BooleanSource`, which is Boolean.                                                                                                                                                                                                                             |
    | `BooleanSource`                   | `gt``(boolean rhs)`<br>Compares the value of each element of this `BooleanSource` to the specified `boolean` value, and determines whether it is a greater value.                                                                                                                                                                                                     |
    | [`DateSource`](DateSource.md)     | `implies``(java.util.Date ifTrue, java.util.Date ifFalse)`<br>Produces a `DateSource` that has an element with the value of `ifTrue` for each element of this `BooleanSource` that has a value of `true` and an element with the value of `ifFalse` for each element of this `BooleanSource` that has a value of `false`.                                             |
    | [`DateSource`](DateSource.md)     | `implies``(`[`DateSource`](DateSource.md)` ifTrue, `[`DateSource`](DateSource.md)` ifFalse)`<br>Produces a `DateSource` that has an element with the value of `ifTrue` for each element of this `BooleanSource` that has a value of `true` and an element with the value of `ifFalse` for each element of this `BooleanSource` that has a value of `false`.           |
    | [`NumberSource`](NumberSource.md) | `implies``(double ifTrue, double ifFalse)`<br>Produces a `NumberSource` that has an element with the value of `ifTrue` for each element of this `BooleanSource` that has a value of `true` and an element with the value of `ifFalse` for each element of this `BooleanSource` that has a value of `false`.                                                           |
    | [`NumberSource`](NumberSource.md) | `implies``(int ifTrue, int ifFalse)`<br>Produces a `NumberSource` that has an element with the value of `ifTrue` for each element of this `BooleanSource` that has a value of `true` and an element with the value of `ifFalse` for each element of this `BooleanSource` that has a value of `false`.                                                                 |
    | [`NumberSource`](NumberSource.md) | `implies``(`[`NumberSource`](NumberSource.md)` ifTrue, `[`NumberSource`](NumberSource.md)` ifFalse)`<br>Produces a `NumberSource` that has an element with the value of `ifTrue` for each element of this `BooleanSource` that has a value of `true` and an element with the value of `ifFalse` for each element of this `BooleanSource` that has a value of `false`. |
    | [`StringSource`](StringSource.md) | `implies``(`[`StringSource`](StringSource.md)` ifTrue, `[`StringSource`](StringSource.md)` ifFalse)`<br>Produces a `StringSource` that has an element with the value of `ifTrue` for each element of this `BooleanSource` that has a value of `true` and an element with the value of `ifFalse` for each element of this `BooleanSource` that has a value of `false`. |
    | [`StringSource`](StringSource.md) | `implies``(java.lang.String ifTrue, java.lang.String ifFalse)`<br>Produces a `StringSource` that has an element with the value of `ifTrue` for each element of this `BooleanSource` that has a value of `true` and an element with the value of `ifFalse` for each element of this `BooleanSource` that has a value of `false`.                                       |
    | `BooleanSource`                   | `le``(boolean rhs)`<br>Compares the value of each element of this `BooleanSource` to the specified `boolean` value, and determines whether it is a lesser or equal value.                                                                                                                                                                                             |
    | `BooleanSource`                   | `lt``(boolean rhs)`<br>Compares the value of each element of this `BooleanSource` to the specified `boolean` value, and determines whether it is a lesser value.                                                                                                                                                                                                      |
    | `BooleanSource`                   | `ne``(boolean rhs)`<br>Compares the value of each element of this `BooleanSource` to the specified `boolean` value, and determines whether it is not equal to the value.                                                                                                                                                                                              |
    | `BooleanSource`                   | `not``()`<br>Performs a logical NOT operation on the values of the elements of this `BooleanSource`, which negates the values so that if an element of this `BooleanSource` has a value of `true`, then the corresponding element of the resulting `BooleanSource` has a value of `false`.                                                                            |
    | `BooleanSource`                   | `or``(boolean rhs)`<br>Performs a logical OR operation between the values of the elements of this `BooleanSource` and the specified `boolean` value.                                                                                                                                                                                                                  |
    | `BooleanSource`                   | `or``(BooleanSource rhs)`<br>Performs a logical OR operation between the values of the elements of this `BooleanSource` and the values of the corresponding elements of the specified `BooleanSource`.                                                                                                                                                                |
    | [`NumberSource`](NumberSource.md) | `positionOfValue``(boolean value)`<br>Identifies the positions of elements in this `BooleanSource` that have the specified `boolean` value.                                                                                                                                                                                                                           |
    | [`NumberSource`](NumberSource.md) | `positionOfValues``(boolean[] values)`<br>Identifies the positions of elements in this `BooleanSource` that have the specified `boolean` values.                                                                                                                                                                                                                      |
    | `BooleanSource`                   | `removeValue``(boolean value)`<br>Removes the elements of this `BooleanSource` that have the specified `boolean` value.                                                                                                                                                                                                                                               |
    | `BooleanSource`                   | `removeValues``(boolean[] values)`<br>Removes the elements of this `BooleanSource` that have the specified `boolean` values.                                                                                                                                                                                                                                          |
    | `BooleanSource`                   | `selectValue``(boolean value)`<br>Selects the elements of this `BooleanSource` that have the specified `boolean` value.                                                                                                                                                                                                                                               |
    | `BooleanSource`                   | `selectValues``(boolean[] values)`<br>Selects the elements of this `BooleanSource` that have the specified `boolean` values.                                                                                                                                                                                                                                          |

    - ### Methods inherited from class oracle.olapi.data.source.[Source](Source.md)

      [`alias`](Source.md)`, `[`appendValue`](Source.md)`, `[`appendValues`](Source.md)`, `[`appendValues`](Source.md)`, `[`at`](Source.md)`, `[`at`](Source.md)`, `[`count`](Source.md)`, `[`count`](Source.md)`, `[`cumulativeInterval`](Source.md)`, `[`cumulativeInterval`](Source.md)`, `[`cumulativeInterval`](Source.md)`, `[`distinct`](Source.md)`, `[`eq`](Source.md)`, `[`extract`](Source.md)`, `[`findMatchFor`](Source.md)`, `[`first`](Source.md)`, `[`ge`](Source.md)`, `[`getDataProvider`](Source.md)`, `[`getDefinition`](Source.md)`, `[`getExtractionInputs`](Source.md)`, `[`getID`](Source.md)`, `[`getInputs`](Source.md)`, `[`getMetadataProvider`](Source.md)`, `[`getMetadataProviderID`](Source.md)`, `[`getModel`](Source.md)`, `[`getOutputs`](Source.md)`, `[`getRegularInputs`](Source.md)`, `[`getType`](Source.md)`, `[`gt`](Source.md)`, `[`hasValue`](Source.md)`, `[`in`](Source.md)`, `[`interval`](Source.md)`, `[`interval`](Source.md)`, `[`isSubtypeOf`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`joinHidden`](Source.md)`, `[`last`](Source.md)`, `[`le`](Source.md)`, `[`lt`](Source.md)`, `[`movingInterval`](Source.md)`, `[`movingInterval`](Source.md)`, `[`ne`](Source.md)`, `[`nullSource`](Source.md)`, `[`offset`](Source.md)`, `[`offset`](Source.md)`, `[`position`](Source.md)`, `[`position`](Source.md)`, `[`positionOfValue`](Source.md)`, `[`positionOfValues`](Source.md)`, `[`positionOfValues`](Source.md)`, `[`recursiveJoin`](Source.md)`, `[`recursiveJoin`](Source.md)`, `[`recursiveJoin`](Source.md)`, `[`recursiveJoin`](Source.md)`, `[`recursiveJoin`](Source.md)`, `[`recursiveJoin`](Source.md)`, `[`recursiveJoin`](Source.md)`, `[`remove`](Source.md)`, `[`removeValue`](Source.md)`, `[`removeValues`](Source.md)`, `[`removeValues`](Source.md)`, `[`select`](Source.md)`, `[`selectDescendants`](Source.md)`, `[`selectValue`](Source.md)`, `[`selectValues`](Source.md)`, `[`selectValues`](Source.md)`, `[`sortAscending`](Source.md)`, `[`sortAscending`](Source.md)`, `[`sortAscending`](Source.md)`, `[`sortAscendingHierarchically`](Source.md)`, `[`sortAscendingHierarchically`](Source.md)`, `[`sortAscendingHierarchically`](Source.md)`, `[`sortAscendingHierarchically`](Source.md)`, `[`sortDescending`](Source.md)`, `[`sortDescending`](Source.md)`, `[`sortDescending`](Source.md)`, `[`sortDescendingHierarchically`](Source.md)`, `[`sortDescendingHierarchically`](Source.md)`, `[`sortDescendingHierarchically`](Source.md)`, `[`sortDescendingHierarchically`](Source.md)`, `[`toDoubleSource`](Source.md)`, `[`toFloatSource`](Source.md)`, `[`toIntegerSource`](Source.md)`, `[`toShortSource`](Source.md)`, `[`toStringSource`](Source.md)`, `[`value`](Source.md)`, `[`value`](Source.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### and

          public final BooleanSource and(BooleanSource rhs)

      Performs a logical AND operation between the values of the elements of this `BooleanSource` and the values of the corresponding elements of the specified `BooleanSource`.
      Parameters:
      `rhs` - The `BooleanSource` whose elements you want to logically AND with the elements of this `BooleanSource`.

      Returns:
      A `BooleanSource` that has the results of the logical AND operations between the values of the elements of this `BooleanSource` and the values of the corresponding elements of the specified `BooleanSource`.

    <!-- -->

    - #### and

          public final BooleanSource and(boolean rhs)

      Performs a logical AND operation between the values of the elements of this `BooleanSource` and the specified `boolean` value.
      Parameters:
      `rhs` - The `boolean` value that you want to logically AND with the values of the elements of this `BooleanSource`.

      Returns:
      A `BooleanSource` that has the results of the logical AND operations between the values of the element of this `BooleanSource` and the specified `boolean` value.

    <!-- -->

    - #### appendValue

          public final BooleanSource appendValue(boolean appendValue)

      Appends an element with the specified `boolean` value to this `BooleanSource`. The outputs of this `BooleanSource`, if any, do not appear in the resulting `BooleanSource`.
      Parameters:
      `appendValue` - The `boolean` value that you want to append to this `BooleanSource`.

      Returns:
      A `BooleanSource` that has the same elements as this `BooleanSource` and that has an additional appended element that has the specified `boolean` value.

    <!-- -->

    - #### appendValues

          public final BooleanSource appendValues(boolean[] appendValues)

      Appends elements with the specified `boolean` values to this `BooleanSource`. The outputs of this `BooleanSource`, if any, do not appear in the resulting `BooleanSource`.
      Parameters:
      `appendValues` - An array of `boolean` values that you want to append to this `BooleanSource`.

      Returns:
      A `BooleanSource` that has the same elements as this `BooleanSource` and that has additional appended elements that have the specified `boolean` values.

    <!-- -->

    - #### eq

          public final BooleanSource eq(boolean rhs)

      Compares the value of each element of this `BooleanSource` to the specified `boolean` value and determines if the values are equal.
      Parameters:
      `rhs` - The `boolean` value that you want to compare to the values of the elements of this `BooleanSource`.

      Returns:
      A `BooleanSource` that has an element that has a value of `true` when the value of the corresponding element of this `BooleanSource` equals the specified `boolean` value or `false` when it does not.

    <!-- -->

    - #### forAll

          public final BooleanSource forAll()

      Indicates whether the values of all of the elements of this `BooleanSource` are `true`. This method ignores elements that do not have a value.
      For a `BooleanSource` with no outputs, this method returns a `BooleanSource` that has an element whose value is `true` when all of the elements of this `BooleanSource` have a value of `true`, or `false` when they do not. For a `BooleanSource` with outputs, this method returns a `BooleanSource` that has an element whose value is `true` when the value of an element and the values of all of its corresponding output elements are `true`, or `false` when they are not.

      Returns:
      A `BooleanSource` that has an element whose value is `true` when the values of all of the elements, or an element and all of the corresponding elements of its outputs, is `true`, or `false` when they are not.

      See Also:
      `forAll(boolean noValueAsFalse)`

    <!-- -->

    - #### forAll

          public final BooleanSource forAll(boolean noValueAsFalse)

      Indicates whether the values of all of the elements of this `BooleanSource` are `true`. If `noValueAsFalse` is `true`, this method uses a value of `false` for elements that do not have a value. If `noValueAsFalse` is `false`, this method ignores elements that do not have a value.
      For a `BooleanSource` with no outputs, this method returns a `BooleanSource` that has an element whose value is `true` when all of the elements of this `BooleanSource` have a value of `true`, or `false` when they do not. For a `BooleanSource` with outputs, this method returns a `BooleanSource` that has an element whose value is `true` when the value of an element and the values of all of its corresponding output elements are `true`, or `false` when they are not.

      Parameters:
      `noValueAsFalse` - Specify `true` when you want this method to use a value of `false` for elements that do not have a value.

      Returns:
      A `BooleanSource` that has an element whose value is `true` when the values of all of the elements, or an element and all of the corresponding elements of its outputs, is `true`, or `false` when they are not.

      See Also:
      `forAll()`

    <!-- -->

    - #### forAny

          public final BooleanSource forAny()

      Indicates whether the value of any of the elements of this `BooleanSource` is `true`. This method ignores elements that do not have a value.
      For a `BooleanSource` with no outputs, this method returns a `BooleanSource` that has an element whose value is `true` when any of the elements of this `BooleanSource` have a value of `true`, or `false` when none does. For a `BooleanSource` with outputs, this method returns a `BooleanSource` that has an element whose value is `true` when the value of an element or the value of any of its corresponding output elements is `true`, or `false` when none is.

      Returns:
      A `BooleanSource` that has an element whose value is `true` when the value of any of the elements, or any of the corresponding elements of its outputs, is `true`, or `false` when none is.

      See Also:
      `forAny(boolean noValueAsFalse)`

    <!-- -->

    - #### forAny

          public final BooleanSource forAny(boolean noValueAsFalse)

      Indicates whether the value of any of the elements of this `BooleanSource` is `true`. If `noValueAsFalse` is `true`, this method uses a value of `false` for elements that do not have a value. If `noValueAsFalse` is `false`, this method ignores elements that do not have a value.
      For a `BooleanSource` with no outputs, this method returns a `BooleanSource` that has an element whose value is `true` when any of the elements of this `BooleanSource` have a value of `true`, or `false` when none does. For a `BooleanSource` with outputs, this method returns a `BooleanSource` that has an element whose value is `true` when the value of any element or the value of any of its corresponding output elements is `true`, or `false` when none is.

      Parameters:
      `noValueAsFalse` - Specify `true` when you want this method to use a value of `false` for elements that do not have a value.

      Returns:
      A `BooleanSource` that has an element whose value is `true` when the value of any of the elements of this `BooleanSource`, or any of the corresponding elements of its outputs, is `true`, or `false` when none is.

      See Also:
      `forAny()`

    <!-- -->

    - #### forNone

          public final BooleanSource forNone()

      Indicates whether the value of none of the elements of this `BooleanSource` is `true`. This method ignores elements that do not have any values.
      For a `BooleanSource` with no outputs, this method returns a `BooleanSource` that has an element whose value is `true` when none of the elements of this `BooleanSource` have a value of `true`, or `false` when any does. For a `BooleanSource` with outputs, this method returns a `BooleanSource` that has an element whose value is `true` when no value of an element or any of its corresponding output elements is `true`, or `false` when any is.

      Returns:
      A `BooleanSource` that has an element whose value is `true` when no value of any of the elements of this `BooleanSource`, or any of the corresponding elements of its outputs, is `true`, or `false` when any is.

      See Also:
      `forNone(boolean noValueAsFalse)`

    <!-- -->

    - #### forNone

          public final BooleanSource forNone(boolean noValueAsFalse)

      Indicates whether the value of none of the elements of this `BooleanSource` is `true`. If `noValueAsFalse` is `true`, this method uses a value of `false` for elements that do not have a value. If `noValueAsFalse` is `false`, this method ignores elements that do not have a value.
      For a `BooleanSource` with no outputs, this method returns a `BooleanSource` that has an element whose value is `true` when none of the elements of this `BooleanSource` have a value of `true`, or `false` when any does. For a `BooleanSource` with outputs, this method returns a `BooleanSource` that has an element whose value is `true` when no value of an element or any of its corresponding output elements is `true`, or `false` when any is.

      Parameters:
      `noValueAsFalse` - Specify `true` when you want this method to use a value of `false` for elements that do not have a value.

      Returns:
      A `BooleanSource` that has an element whose value is `true` when no value of any of the elements of this `BooleanSource`, or any of the corresponding elements of its outputs, is `true`, or `false` when any is.

      See Also:
      `forNone()`

    <!-- -->

    - #### ge

          public final BooleanSource ge(boolean rhs)

      Compares the value of each element of this `BooleanSource` to the specified `boolean` value, and determines whether it is a greater or equal value.
      Parameters:
      `rhs` - The `boolean` value that you want to compare to the values of the elements of this `BooleanSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of the corresponding element of this `BooleanSource` is greater than or equal to the specified `boolean` value, or `false` when it is not.

    <!-- -->

    - #### getDataType

          public Source getDataType()

      Gets the fundamental `Source` that represents the OLAP Java API data type of this `BooleanSource`, which is Boolean.
      Overrides:
      [`getDataType`](Source.md) in class [`Source`](Source.md)

      Returns:
      The fundamental `Source` that represents the OLAP Java API Boolean data type.

    <!-- -->

    - #### gt

          public final BooleanSource gt(boolean rhs)

      Compares the value of each element of this `BooleanSource` to the specified `boolean` value, and determines whether it is a greater value.
      Parameters:
      `rhs` - The `boolean` value that you want to compare to the values of the elements of this `BooleanSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of the corresponding element of this `BooleanSource` is greater than the specified `boolean` value, or `false` when it is not.

    <!-- -->

    - #### implies

          public final NumberSource implies(double ifTrue,
                                            double ifFalse)

      Produces a `NumberSource` that has an element with the value of `ifTrue` for each element of this `BooleanSource` that has a value of `true` and an element with the value of `ifFalse` for each element of this `BooleanSource` that has a value of `false`.
      Parameters:
      `ifTrue` - The `double` value that you want the elements of the resulting `NumberSource` to have for the elements of this `BooleanSource` that have a value of `true`.

      `ifFalse` - The `double` value that you want the elements of the resulting `NumberSource` to have for the elements of this `BooleanSource` that have a value of `false`.

      Returns:
      A `NumberSource` that has the value of `ifTrue` when the corresponding value of this `BooleanSource` is `true`, or the value of `ifFalse` when the corresponding value of this `BooleanSource` is `false`.

    <!-- -->

    - #### implies

          public final NumberSource implies(int ifTrue,
                                            int ifFalse)

      Produces a `NumberSource` that has an element with the value of `ifTrue` for each element of this `BooleanSource` that has a value of `true` and an element with the value of `ifFalse` for each element of this `BooleanSource` that has a value of `false`.
      Parameters:
      `ifTrue` - The `int` value that you want the elements of the resulting `NumberSource` to have for the elements of this `BooleanSource` that have a value of `true`.

      `ifFalse` - The `int` value that you want the elements of `int` value that you want the elements of the resulting `NumberSource` to have for the elements of this `BooleanSource` that have a value of `false`.

      Returns:
      A `NumberSource` that has the value of `ifTrue` when the corresponding value of this `BooleanSource` is `true`, or the value of `ifFalse` when the corresponding value of this `BooleanSource` is `false`.

    <!-- -->

    - #### implies

          public final StringSource implies(java.lang.String ifTrue,
                                            java.lang.String ifFalse)

      Produces a `StringSource` that has an element with the value of `ifTrue` for each element of this `BooleanSource` that has a value of `true` and an element with the value of `ifFalse` for each element of this `BooleanSource` that has a value of `false`.
      Parameters:
      `ifTrue` - The `String` value that you want the elements of the resulting `StringSource` to have for the elements of this `BooleanSource` that have a value of `true`.

      `ifFalse` - The `String` value that you want the elements of the resulting `StringSource` to have for the elements of this `BooleanSource` that have a value of `false`.

      Returns:
      A `StringSource` that has the value of `ifTrue` when the corresponding value of this `BooleanSource` is `true`, or the value of `ifFalse` when the corresponding value of this `BooleanSource` is `false`.

    <!-- -->

    - #### implies

          public final DateSource implies(java.util.Date ifTrue,
                                          java.util.Date ifFalse)

      Produces a `DateSource` that has an element with the value of `ifTrue` for each element of this `BooleanSource` that has a value of `true` and an element with the value of `ifFalse` for each element of this `BooleanSource` that has a value of `false`.
      Parameters:
      `ifTrue` - The `Date` value that you want the elements of the resulting `DateSource` to have for the elements of this `BooleanSource` that have a value of `true`.

      `ifFalse` - The `Date` value that you want the elements of the resulting `DateSource` to have for the elements of this `BooleanSource` that have a value of `false`.

      Returns:
      A `DateSource` that has the value of `ifTrue` when the corresponding value of this `BooleanSource` is `true`, or the value of `ifFalse` when the corresponding value of this `BooleanSource` is `false`.

    <!-- -->

    - #### implies

          public final DateSource implies(DateSource ifTrue,
                                          DateSource ifFalse)

      Produces a `DateSource` that has an element with the value of `ifTrue` for each element of this `BooleanSource` that has a value of `true` and an element with the value of `ifFalse` for each element of this `BooleanSource` that has a value of `false`.
      Parameters:
      `ifTrue` - A `DateSource` that has the `Date` value that you want the elements of the resulting `DateSource` to have for the elements of this `BooleanSource` that have a value of `true`.

      `ifFalse` - A `DateSource` that has the `Date` value that you want the elements of the resulting `DateSource` to have for the elements of this `BooleanSource` that have a value of `false`.

      Returns:
      A `DateSource` that has the value of the element of `ifTrue` when the corresponding value of this `BooleanSource` is `true`, or the value of the element of `ifFalse` when the corresponding value of this `BooleanSource` is `false`.

    <!-- -->

    - #### implies

          public final NumberSource implies(NumberSource ifTrue,
                                            NumberSource ifFalse)

      Produces a `NumberSource` that has an element with the value of `ifTrue` for each element of this `BooleanSource` that has a value of `true` and an element with the value of `ifFalse` for each element of this `BooleanSource` that has a value of `false`.
      Parameters:
      `ifTrue` - A `NumberSource` that has the value that you want the elements of the resulting `NumberSource` to have for the elements of this `BooleanSource` that have a value of `true`.

      `ifFalse` - A `NumberSource` that has the value that you want the elements of the resulting `NumberSource` to have for the elements of this `BooleanSource` that have a value of `false`.

      Returns:
      A `NumberSource` that has the value of the element of `ifTrue` when the corresponding value of this `BooleanSource` is `true`, or the value of the element of `ifFalse` when the corresponding value of this `BooleanSource` is `false`.

    <!-- -->

    - #### implies

          public final StringSource implies(StringSource ifTrue,
                                            StringSource ifFalse)

      Produces a `StringSource` that has an element with the value of `ifTrue` for each element of this `BooleanSource` that has a value of `true` and an element with the value of `ifFalse` for each element of this `BooleanSource` that has a value of `false`.
      Parameters:
      `ifTrue` - A `StringSource` that has the value that you want the elements of the resulting `StringSource` to have for the elements of this `BooleanSource` that have a value of `true`.

      `ifFalse` - A `StringSource` that has the value that you want the elements of the resulting `StringSource` to have for the elements of this `BooleanSource` that have a value of `false`.

      Returns:
      A `StringSource` that has the value of the element of `ifTrue` when the corresponding value of this `BooleanSource` is `true`, or the value of the element of `ifFalse` when the corresponding value of this `BooleanSource` is `false`.

    <!-- -->

    - #### le

          public final BooleanSource le(boolean rhs)

      Compares the value of each element of this `BooleanSource` to the specified `boolean` value, and determines whether it is a lesser or equal value.
      Parameters:
      `rhs` - The `boolean` value that you want to compare to the values of the elements of this `BooleanSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of a given element of this `BooleanSource` is less than or equal to the specified `boolean` value, or `false` when it is not.

    <!-- -->

    - #### lt

          public final BooleanSource lt(boolean rhs)

      Compares the value of each element of this `BooleanSource` to the specified `boolean` value, and determines whether it is a lesser value.
      Parameters:
      `rhs` - The `boolean` value that you want to compare to the values of the elements of this `BooleanSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of the corresponding element of this `BooleanSource` is less than the specified `boolean` value, or `false` when it is not.

    <!-- -->

    - #### ne

          public final BooleanSource ne(boolean rhs)

      Compares the value of each element of this `BooleanSource` to the specified `boolean` value, and determines whether it is not equal to the value.
      Parameters:
      `rhs` - The `boolean` value that you want to compare to the values of the elements of this `BooleanSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of the corresponding element of this `BooleanSource` is not equal to the specified `boolean` value, or `false` when it is equal to the specified value.

    <!-- -->

    - #### not

          public final BooleanSource not()

      Performs a logical NOT operation on the values of the elements of this `BooleanSource`, which negates the values so that if an element of this `BooleanSource` has a value of `true`, then the corresponding element of the resulting `BooleanSource` has a value of `false`. If an element of this `BooleanSource` has a value of `false`, then the corresponding element of the resulting `BooleanSource` has a value of `true`.
      Returns:
      A `BooleanSource` that has the results of the logical NOT operations on the values of the elements of this `BooleanSource`.

    <!-- -->

    - #### or

          public final BooleanSource or(BooleanSource rhs)

      Performs a logical OR operation between the values of the elements of this `BooleanSource` and the values of the corresponding elements of the specified `BooleanSource`.
      Parameters:
      `rhs` - The `BooleanSource` whose elements you want to logically OR with the elements of this `BooleanSource`.

      Returns:
      A `BooleanSource` that has the results of the logical OR operations between the values of the elements of this `BooleanSource` and the values of the corresponding elements of the specified `BooleanSource`.

    <!-- -->

    - #### or

          public final BooleanSource or(boolean rhs)

      Performs a logical OR operation between the values of the elements of this `BooleanSource` and the specified `boolean` value.
      Parameters:
      `rhs` - The `boolan` value that you want to logically OR with the elements of this `BooleanSource`.

      Returns:
      A `BooleanSource` that has the results of the logical OR operations between the values of the elements of this `BooleanSource` and the specified value.

    <!-- -->

    - #### positionOfValue

          public final NumberSource positionOfValue(boolean value)

      Identifies the positions of elements in this `BooleanSource` that have the specified `boolean` value.
      Parameters:
      `value` - The `boolean` value that you want to compare to the values of the elements of this `BooleanSource`.

      Returns:
      A `NumberSource` whose elements have `int` values that identify the positions of the elements in this `BooleanSource` that have the specified `boolean` value. If this `BooleanSource` does not have any elements that have the specified value, then this method returns an empty `NumberSource`, which has no elements.

    <!-- -->

    - #### positionOfValues

          public final NumberSource positionOfValues(boolean[] values)

      Identifies the positions of elements in this `BooleanSource` that have the specified `boolean` values.
      Parameters:
      `values` - An array of `boolean` values that you want to compare to the values of the elements of this `BooleanSource`.

      Returns:
      A `NumberSource` whose elements have `int` values that identify the positions of the elements in this `BooleanSource` that have the specified `boolean` values. If this `BooleanSource` does not have any elements that have the specified values, then this method returns an empty `NumberSource`, which has no elements.

    <!-- -->

    - #### removeValue

          public final BooleanSource removeValue(boolean value)

      Removes the elements of this `BooleanSource` that have the specified `boolean` value.
      Parameters:
      `value` - The `boolean` value you do not want to have in the returned `BooleanSource`.

      Returns:
      A `BooleanSource` that has the elements of this `BooleanSource` that do not have the specified `boolean` value.

    <!-- -->

    - #### removeValues

          public final BooleanSource removeValues(boolean[] values)

      Removes the elements of this `BooleanSource` that have the specified `boolean` values.
      Parameters:
      `values` - An array of `boolean` values that you do not want to have in the returned `BooleanSource`.

      Returns:
      A `BooleanSource` that has the elements of this `BooleanSource` that do not have the specified values.

    <!-- -->

    - #### selectValue

          public final BooleanSource selectValue(boolean value)

      Selects the elements of this `BooleanSource` that have the specified `boolean` value.
      Parameters:
      `value` - The value to compare to the values of the elements of this `BooleanSource`.

      Returns:
      A `BooleanSource` that has the elements of this `BooleanSource` that have the specified `boolean` value.

    <!-- -->

    - #### selectValues

          public final BooleanSource selectValues(boolean[] values)

      Selects the elements of this `BooleanSource` that have the specified `boolean` values.
      Parameters:
      `values` - An array of `boolean` values to compare to the values of the elements of this `BooleanSource`.

      Returns:
      A `BooleanSource` that has the elements of this `BooleanSource` that have the specified values.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](BooleanParameter.md)
- [Next Class](BuildProperties.md)

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
