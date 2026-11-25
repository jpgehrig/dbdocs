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

- [Prev Class](StringParameter.md)
- [Next Class](Template.md)

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

## Class StringSource

- java.lang.Object

- - [oracle.olapi.data.source.Source](Source.md)

  - - oracle.olapi.data.source.StringSource

<!-- -->

- All Implemented Interfaces:
  [SourceIdentifier](../cursor/SourceIdentifier.md)

  ------------------------------------------------------------------------



      public final class StringSource
      extends Source

  A `Source` that has elements that have `String` objects as values. A `StringSource` has an OLAP Java API data type of String. This class implements some `Source` methods so that they use `String` values, such as `appendValue`, and implements other methods that perform String operations, such as `toUppercase`, `substring`, and `trim`.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from class oracle.olapi.data.source.[Source](Source.md)

      [`COMPARISON_RULE_ASCENDING`](Source.md)`, `[`COMPARISON_RULE_ASCENDING_NULLS_FIRST`](Source.md)`, `[`COMPARISON_RULE_ASCENDING_NULLS_LAST`](Source.md)`, `[`COMPARISON_RULE_DESCENDING`](Source.md)`, `[`COMPARISON_RULE_DESCENDING_NULLS_FIRST`](Source.md)`, `[`COMPARISON_RULE_DESCENDING_NULLS_LAST`](Source.md)`, `[`COMPARISON_RULE_REMOVE`](Source.md)`, `[`COMPARISON_RULE_SELECT`](Source.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                   | Method and Description                                                                                                                                                                                                                                                |
    |-------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `StringSource`                      | `appendValue``(java.lang.String appendValue)`<br>Appends an element with the specified `String` value to the elements of this `StringSource`.                                                                                                                         |
    | `StringSource`                      | `appendValues``(java.lang.String[] appendValues)`<br>Appends elements with the specified `String` values to the elements of this `StringSource`.                                                                                                                      |
    | [`BooleanSource`](BooleanSource.md) | `eq``(java.lang.String rhs)`<br>Compares the value of each element of this `StringSource` to the value of the specified `String` and determines if the values are equal.                                                                                              |
    | [`BooleanSource`](BooleanSource.md) | `ge``(java.lang.String rhs)`<br>Compares the value of each element of this `StringSource` to the specified `String` value, and determines whether it has a greater or equal value.                                                                                    |
    | [`Source`](Source.md)               | `getDataType``()`<br>Gets the fundamental `Source` that represents the OLAP Java API data type of this `StringSource`, which is String.                                                                                                                               |
    | [`BooleanSource`](BooleanSource.md) | `gt``(java.lang.String rhs)`<br>Compares the value of each element of this `StringSource` to the specified `String` value, and determines whether it has a greater value.                                                                                             |
    | [`NumberSource`](NumberSource.md)   | `indexOf``(java.lang.String substring, int fromIndex)`<br>Starting at the `fromIndex` position in the value of each element of this `StringSource`, identifies the starting position of the first occurrence of `substring` in the value.                             |
    | [`NumberSource`](NumberSource.md)   | `indexOf``(StringSource substring, `[`NumberSource`](NumberSource.md)` fromIndex)`<br>Starting at the `fromIndex` position in the value of each element of this `StringSource`, identifies the starting position of the first occurrence of `substring` in the value. |
    | [`BooleanSource`](BooleanSource.md) | `le``(java.lang.String rhs)`<br>Compares the value of each element of this `StringSource` to the specified `String` value, and determines whether it has a lesser or equal value.                                                                                     |
    | [`NumberSource`](NumberSource.md)   | `length``()`<br>Determines the length of the value of each element of this `StringSource`.                                                                                                                                                                            |
    | [`BooleanSource`](BooleanSource.md) | `like``(java.lang.String rhs)`<br>Compares the values of the elements of this `StringSource` to the specified `String`.                                                                                                                                               |
    | [`BooleanSource`](BooleanSource.md) | `like``(StringSource rhs)`<br>Compares the values of the elements of this `StringSource` to the values of the elements of the specified `StringSource`.                                                                                                               |
    | [`BooleanSource`](BooleanSource.md) | `lt``(java.lang.String rhs)`<br>Compares the value of each element of this `StringSource` to the specified `String` value, and determines whether it has a lesser value.                                                                                              |
    | [`BooleanSource`](BooleanSource.md) | `ne``(java.lang.String rhs)`<br>Compares the value of each element of this `StringSource` to the specified `String` value, and determines whether it is not equal to the value.                                                                                       |
    | `StringSource`                      | `plus``(StringSource rhs)`<br>Appends the values of the elements of `rhs` to the values of the elements of this `StringSource`.                                                                                                                                       |
    | [`NumberSource`](NumberSource.md)   | `positionOfValue``(java.lang.String value)`<br>Identifies the positions of the elements of this `StringSource` that have the specified `String` value.                                                                                                                |
    | [`NumberSource`](NumberSource.md)   | `positionOfValues``(java.lang.String[] values)`<br>Identifies the positions of the elements of this `StringSource` that have the specified `String` values.                                                                                                           |
    | `StringSource`                      | `remove``(int index, int length)`<br>Removes `length` number of characters starting at position `index` from the values of the elements of this `StringSource`.                                                                                                       |
    | `StringSource`                      | `remove``(`[`NumberSource`](NumberSource.md)` index, `[`NumberSource`](NumberSource.md)` length)`<br>Removes `length` number of characters starting at position `index` from the values of the elements of this `StringSource`.                                       |
    | `StringSource`                      | `removeValue``(java.lang.String value)`<br>Removes the elements of this `StringSource` that have the specified `String` as a value.                                                                                                                                   |
    | `StringSource`                      | `removeValues``(java.lang.String[] values)`<br>Removes the elements of this `StringSource` that have a value specified by one of the `String` objects in the `values` array.                                                                                          |
    | `StringSource`                      | `replace``(StringSource oldString, StringSource newString)`<br>Replaces each occurrence of `oldString` with `newString` in the value of each element of this `StringSource`.                                                                                          |
    | `StringSource`                      | `replace``(java.lang.String oldString, java.lang.String newString)`<br>Replaces each occurrence of `oldString` with `newString` in the value of each element of this `StringSource`.                                                                                  |
    | `StringSource`                      | `selectDescendants``(java.lang.String[] comparison, `[`Source`](Source.md)` parent)`<br>Selects the elements of this `StringSource` that are specified by `comparison` and the descendants of those elements in the hierarchy that this `StringSource` represents.    |
    | `StringSource`                      | `selectDescendants``(java.lang.String comparison, `[`Source`](Source.md)` parent)`<br>Selects the elements of this `StringSource` that are specified by `comparison` and the descendants of those elements in the hierarchy that this `StringSource` represents.      |
    | `StringSource`                      | `selectValue``(java.lang.String value)`<br>Selects the elements of this `StringSource` that have the specified value.                                                                                                                                                 |
    | `StringSource`                      | `selectValues``(java.lang.String[] values)`<br>Selects the elements of this `StringSource` that have the specified values.                                                                                                                                            |
    | `StringSource`                      | `substring``(int index, int length)`<br>Selects the `length` number of characters, beginning at the position specified by `index`, from the values of the elements of this `StringSource`.                                                                            |
    | `StringSource`                      | `substring``(`[`NumberSource`](NumberSource.md)` index, `[`NumberSource`](NumberSource.md)` length)`<br>Selects the `length` number of characters, beginning at the position specified by `index`, from the values of the elements of this `StringSource`.            |
    | `StringSource`                      | `textFill``(int width)`<br>Resizes the values of the elements of this `StringSource` to the specified width.                                                                                                                                                          |
    | `StringSource`                      | `textFill``(`[`NumberSource`](NumberSource.md)` width)`<br>Resizes the values of the elements of this `StringSource` to the specified width or widths.                                                                                                                |
    | `StringSource`                      | `toLowercase``()`<br>Converts the alphabetic characters in the values of the elements of this `StringSource` to lowercase.                                                                                                                                            |
    | `StringSource`                      | `toUppercase``()`<br>Converts the alphabetic characters in the values of the elements of this `StringSource` to uppercase.                                                                                                                                            |
    | `StringSource`                      | `trim``()`<br>Removes the leading and the trailing blank spaces from the values of the elements of this `StringSource`.                                                                                                                                               |
    | `StringSource`                      | `trimLeading``()`<br>Removes the leading blank spaces from the values of the elements of this `StringSource`.                                                                                                                                                         |
    | `StringSource`                      | `trimTrailing``()`<br>Removes the trailing blank spaces from the values of the elements of this `StringSource`.                                                                                                                                                       |

    - ### Methods inherited from class oracle.olapi.data.source.[Source](Source.md)

      [`alias`](Source.md)`, `[`appendValue`](Source.md)`, `[`appendValues`](Source.md)`, `[`appendValues`](Source.md)`, `[`at`](Source.md)`, `[`at`](Source.md)`, `[`count`](Source.md)`, `[`count`](Source.md)`, `[`cumulativeInterval`](Source.md)`, `[`cumulativeInterval`](Source.md)`, `[`cumulativeInterval`](Source.md)`, `[`distinct`](Source.md)`, `[`eq`](Source.md)`, `[`extract`](Source.md)`, `[`findMatchFor`](Source.md)`, `[`first`](Source.md)`, `[`ge`](Source.md)`, `[`getDataProvider`](Source.md)`, `[`getDefinition`](Source.md)`, `[`getExtractionInputs`](Source.md)`, `[`getID`](Source.md)`, `[`getInputs`](Source.md)`, `[`getMetadataProvider`](Source.md)`, `[`getMetadataProviderID`](Source.md)`, `[`getModel`](Source.md)`, `[`getOutputs`](Source.md)`, `[`getRegularInputs`](Source.md)`, `[`getType`](Source.md)`, `[`gt`](Source.md)`, `[`hasValue`](Source.md)`, `[`in`](Source.md)`, `[`interval`](Source.md)`, `[`interval`](Source.md)`, `[`isSubtypeOf`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`join`](Source.md)`, `[`joinHidden`](Source.md)`, `[`last`](Source.md)`, `[`le`](Source.md)`, `[`lt`](Source.md)`, `[`movingInterval`](Source.md)`, `[`movingInterval`](Source.md)`, `[`ne`](Source.md)`, `[`nullSource`](Source.md)`, `[`offset`](Source.md)`, `[`offset`](Source.md)`, `[`position`](Source.md)`, `[`position`](Source.md)`, `[`positionOfValue`](Source.md)`, `[`positionOfValues`](Source.md)`, `[`positionOfValues`](Source.md)`, `[`recursiveJoin`](Source.md)`, `[`recursiveJoin`](Source.md)`, `[`recursiveJoin`](Source.md)`, `[`recursiveJoin`](Source.md)`, `[`recursiveJoin`](Source.md)`, `[`recursiveJoin`](Source.md)`, `[`recursiveJoin`](Source.md)`, `[`remove`](Source.md)`, `[`removeValue`](Source.md)`, `[`removeValues`](Source.md)`, `[`removeValues`](Source.md)`, `[`select`](Source.md)`, `[`selectDescendants`](Source.md)`, `[`selectValue`](Source.md)`, `[`selectValues`](Source.md)`, `[`selectValues`](Source.md)`, `[`sortAscending`](Source.md)`, `[`sortAscending`](Source.md)`, `[`sortAscending`](Source.md)`, `[`sortAscendingHierarchically`](Source.md)`, `[`sortAscendingHierarchically`](Source.md)`, `[`sortAscendingHierarchically`](Source.md)`, `[`sortAscendingHierarchically`](Source.md)`, `[`sortDescending`](Source.md)`, `[`sortDescending`](Source.md)`, `[`sortDescending`](Source.md)`, `[`sortDescendingHierarchically`](Source.md)`, `[`sortDescendingHierarchically`](Source.md)`, `[`sortDescendingHierarchically`](Source.md)`, `[`sortDescendingHierarchically`](Source.md)`, `[`toDoubleSource`](Source.md)`, `[`toFloatSource`](Source.md)`, `[`toIntegerSource`](Source.md)`, `[`toShortSource`](Source.md)`, `[`toStringSource`](Source.md)`, `[`value`](Source.md)`, `[`value`](Source.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### appendValue

          public final StringSource appendValue(java.lang.String appendValue)

      Appends an element with the specified `String` value to the elements of this `StringSource`.
      Parameters:
      `appendValue` - The `String` value that you want to append to this `StringSource`.

      Returns:
      A `StringSource` that has the same elements as this `StringSource` and that has an additional appended element that has the specified `String` value.

    <!-- -->

    - #### appendValues

          public final StringSource appendValues(java.lang.String[] appendValues)

      Appends elements with the specified `String` values to the elements of this `StringSource`.
      Parameters:
      `appendValues` - An array of `String`StringSource.

      Returns:
      A `StringSource` that has the same elements as this `StringSource` and that has additional appended elements that have the specified `String` values.

    <!-- -->

    - #### eq

          public final BooleanSource eq(java.lang.String rhs)

      Compares the value of each element of this `StringSource` to the value of the specified `String` and determines if the values are equal.
      Parameters:
      `rhs` - The `String` value that you want to compare to the values of the elements of this `StringSource`.

      Returns:
      A `BooleanSource` that has an element that has a value of `true` when the value of an element of this `StringSource` equals the specified `String` value, or `false` when it does not.

    <!-- -->

    - #### ge

          public final BooleanSource ge(java.lang.String rhs)

      Compares the value of each element of this `StringSource` to the specified `String` value, and determines whether it has a greater or equal value.
      Parameters:
      `rhs` - The `String` value that you want to compare to the values of the elements of this `StringSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of an element of this `StringSource` is greater than or equal to the specified `String` value, or `false` when it is not.

    <!-- -->

    - #### getDataType

          public Source getDataType()

      Gets the fundamental `Source` that represents the OLAP Java API data type of this `StringSource`, which is String.
      Overrides:
      [`getDataType`](Source.md) in class [`Source`](Source.md)

      Returns:
      The fundamental `Source` that represents the OLAP Java API String data type.

    <!-- -->

    - #### gt

          public final BooleanSource gt(java.lang.String rhs)

      Compares the value of each element of this `StringSource` to the specified `String` value, and determines whether it has a greater value.
      Parameters:
      `rhs` - The `String` value that you want to compare to the values of the elements of this `StringSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of an element of this `StringSource` is greater than the specified `String` value, or `false` when it is not.

    <!-- -->

    - #### indexOf

          public final NumberSource indexOf(java.lang.String substring,
                                            int fromIndex)

      Starting at the `fromIndex` position in the value of each element of this `StringSource`, identifies the starting position of the first occurrence of `substring` in the value.
      Parameters:
      `substring` - A `String` the beginning position of which you want to locate in the value of each element of this `StringSource`.

      `fromIndex` - An `int` that is the one-based position in the value of each element of this `StringSource` at which this method begins searching for `substring`.

      Returns:
      A `NumberSource` that has the beginning position of the first occurrence of `substring` in the values of the elements of this `StringSource` or zero if `substring` is not in the value.

    <!-- -->

    - #### indexOf

          public final NumberSource indexOf(StringSource substring,
                                            NumberSource fromIndex)

      Starting at the `fromIndex` position in the value of each element of this `StringSource`, identifies the starting position of the first occurrence of `substring` in the value.
      Parameters:
      `substring` - A `String` the beginning position of which you want to locate in each element of this `StringSource`.

      `fromIndex` - An `NumberSource` that has the one-based position in the value of each element of this `StringSource` at which this method begins searching for `substring`.

      Returns:
      A `NumberSource` that has the beginning position of the first occurrence of `substring` in the values of the elements of this `StringSource` or zero if `substring` is not in the value.

    <!-- -->

    - #### le

          public final BooleanSource le(java.lang.String rhs)

      Compares the value of each element of this `StringSource` to the specified `String` value, and determines whether it has a lesser or equal value.
      Parameters:
      `rhs` - The `String` value that you want to compare to the values of the elements of this `StringSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of an element of this `StringSource` is less than or equal to the specified `String` value, or `false` when it is not.

    <!-- -->

    - #### length

          public final NumberSource length()

      Determines the length of the value of each element of this `StringSource`.
      Returns:
      A `NumberSource`, the value of each element of which is the length of the value of the corresponding element of this `StringSource`.

    <!-- -->

    - #### like

          public final BooleanSource like(java.lang.String rhs)

      Compares the values of the elements of this `StringSource` to the specified `String`.
      This method supports the percent sign wildcard and the underline position marker. For example, the following code uses the percent sign wildcard in producing `prodSel`, which is a `Source` that specifies the elements of `shortDescrByProd` that contain the `String` `External`. The `shortDescrByProd` object is the result of joining `prodDim`, which is the `Source` for the Product dimension, to `prodShortDescr`, which is the `Source` for the short value description attribute of the Product dimension.

           Source shortDescrByProd = prodShortDescr.join(prodDim);
           Source prodSel = shortDescrByProd.select(
                                       ((StringSource) shortDescrByProd.value())
                                        .like("%External%");

      The following code uses the underline position marker and the percent sign wildcard in producing `prodSel2`, which is a `Source` that specifies the elements of `shortDescrByProd` that have the `String` `tern` at element positions three through six. The first two characters of the `String` passed to the `like` method are underline characters.
           Source prodSel2 = shortDescrByProd.select(
                                       ((StringSource) shortDescrByProd.value())
                                        .like("__tern%");

      A `Cursor` for `prodSel` has the following values.
           PRODUCT_PRIMARY::ITEM::EXT CD ROM, External 48X CD-ROM
           PRODUCT_PRIMARY::ITEM::EXT DVD, External - DVD-RW - 8X
           PRODUCT_PRIMARY::ITEM::144MB DISK, 1.44MB External 3.5" Diskette
           PRODUCT_PRIMARY::ITEM::ENVY EXT KBD, Envoy External Keyboard
           PRODUCT_PRIMARY::ITEM::EXT KBD, External 101-key keyboard

      A `Cursor` for `prodSel2` has the following values.
           PRODUCT_PRIMARY::ITEM::EXT CD ROM, External 48X CD-ROM
           PRODUCT_PRIMARY::ITEM::EXT DVD, External - DVD-RW - 8X
           PRODUCT_PRIMARY::ITEM::INT 8X DVD, Internal - DVD-RW - 8X
           PRODUCT_PRIMARY::ITEM::INT CD ROM, Internal 48X CD-ROM
           PRODUCT_PRIMARY::ITEM::INT CD USB, Internal 48X CD-ROM USB
           PRODUCT_PRIMARY::ITEM::INT RW DVD, Internal - DVD-RW - 6X
           PRODUCT_PRIMARY::ITEM::EXT KBD, External 101-key keyboard

      Parameters:
      `rhs` - The `String` value that you want to compare to the values of the elements of this `StringSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of the corresponding element of this `StringSource` matches the value of the specified `String`, or `false` when it is does not.

    <!-- -->

    - #### like

          public final BooleanSource like(StringSource rhs)

      Compares the values of the elements of this `StringSource` to the values of the elements of the specified `StringSource`.
      This method supports the percent sign wildcard and the underline position marker.

      Parameters:
      `rhs` - A `StringSource`, the values of the elements of which you want to compare to the values of the elements of this `StringSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when a value of an element of this `StringSource` matches the value of an element of the specified `StringSource`, or `false` when it is does not.

    <!-- -->

    - #### lt

          public final BooleanSource lt(java.lang.String rhs)

      Compares the value of each element of this `StringSource` to the specified `String` value, and determines whether it has a lesser value.
      Parameters:
      `rhs` - The `String` value that you want to compare to the values of the elements of this `StringSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of an element of this `StringSource` is less than the specified `String` value, or `false` when it is not.

    <!-- -->

    - #### ne

          public final BooleanSource ne(java.lang.String rhs)

      Compares the value of each element of this `StringSource` to the specified `String` value, and determines whether it is not equal to the value.
      Parameters:
      `rhs` - The `String` value that you want to compare to the values of the elements of this `StringSource`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of an element of this `StringSource` is not equal to the specified `String` value, or `false` when it is equal to the specified value.

    <!-- -->

    - #### positionOfValue

          public final NumberSource positionOfValue(java.lang.String value)

      Identifies the positions of the elements of this `StringSource` that have the specified `String` value.
      Parameters:
      `value` - The `String` value that you want to compare to the values of the elements of this `StringSource`.

      Returns:
      A `NumberSource` whose elements have `int` values that identify the positions of the elements of this `StringSource` that have the specified `String` value. If this `StringSource` does not have any elements that have the specified value, then this method returns an empty `NumberSource`, which has no elements.

    <!-- -->

    - #### positionOfValues

          public final NumberSource positionOfValues(java.lang.String[] values)

      Identifies the positions of the elements of this `StringSource` that have the specified `String` values.
      Parameters:
      `values` - An array of`String` values that you want to compare to the values of the elements of this `StringSource`.

      Returns:
      A `NumberSource` whose elements have `int` values that identify the positions of the elements of this `StringSource` that have the specified `String` values. If this `StringSource` does not have any elements that have a specified value, then this method returns an empty `NumberSource`, which has no elements.

    <!-- -->

    - #### remove

          public final StringSource remove(int index,
                                           int length)

      Removes `length` number of characters starting at position `index` from the values of the elements of this `StringSource`. This method returns a `StringSource` that has the values of the elements of this `StringSource` with the specified characters removed.
      Parameters:
      `index` - An `int` value that is the one-based position within the value of each element of this `StringSource` that is the first of the characters that you want to remove.

      `length` - An `int` value that is the number of characters that you want to remove.

      Returns:
      A `StringSource` that has elements that have the values of the elements of this `StringSource` with the specified number of characters removed.

    <!-- -->

    - #### remove

          public final StringSource remove(NumberSource index,
                                           NumberSource length)

      Removes `length` number of characters starting at position `index` from the values of the elements of this `StringSource`.
      Parameters:
      `index` - A `NumberSource` that has elements that have the integer values that are the one-based character positions within the value of each element of this `StringSource` that is the first of the characters that you want to remove.

      `length` - A `NumberSource` that has elements that have the integer values that are the number of characters that you want to remove.

      Returns:
      A `StringSource` that has elements that have the values of the elements of this `StringSource` with the specified number of characters removed.

    <!-- -->

    - #### removeValue

          public final StringSource removeValue(java.lang.String value)

      Removes the elements of this `StringSource` that have the specified `String` as a value.
      Parameters:
      `value` - A `String` that has the value of the element or elements you do not want to have in the returned `StringSource`.

      Returns:
      A `StringSource` that has the elements of this `StringSource` except for those that have values that match the specified value.

    <!-- -->

    - #### removeValues

          public final StringSource removeValues(java.lang.String[] values)

      Removes the elements of this `StringSource` that have a value specified by one of the `String` objects in the `values` array. This method returns a `StringSource` that has the elements of this `StringSource` except for any elements that have a value that matches one of the specified `String` objects values.
      Parameters:
      `values` - An array of `String` objects that have the values that you do not want to have in the returned `StringSource`.

      Returns:
      A `StringSource` that has the elements of this `StringSource` except for those that have values that match the specified values.

    <!-- -->

    - #### replace

          public final StringSource replace(java.lang.String oldString,
                                            java.lang.String newString)

      Replaces each occurrence of `oldString` with `newString` in the value of each element of this `StringSource`.
      Parameters:
      `oldString` - A `String` that has the value that you want to replace with `newString`.

      `newString` - A `String` that has the value with which you want to replace `oldString`.

      Returns:
      A `StringSource` that has the elements of this `StringSource` but that has `oldString` replaced by `newString` in value of each element.

    <!-- -->

    - #### replace

          public final StringSource replace(StringSource oldString,
                                            StringSource newString)

      Replaces each occurrence of `oldString` with `newString` in the value of each element of this `StringSource`.
      Parameters:
      `oldString` - A `StringSource` that has elements that have the values that you want to replace with the values of the elements of `newString`.

      `newString` - A `StringSource` that has elements that have the values with which you want to replace the values of the elements of `oldString`.

      Returns:
      A `StringSource` that has the elements of this `StringSource` but that has the values of the elements of `oldString` replaced by the values of the elements of `newString`.

    <!-- -->

    - #### selectDescendants

          public final StringSource selectDescendants(java.lang.String comparison,
                                                      Source parent)

      Selects the elements of this `StringSource` that are specified by `comparison` and the descendants of those elements in the hierarchy that this `StringSource` represents. Call this method only on a `StringSource` that is the `Source` for an `MdmHierarchy` or on a subtype of such a `Source`.
      Parameters:
      `comparison` - A `String` that has the value of the element or elements that you want to select from this `StringSource`.

      `parent` - The `Source`, or a subtype of the `Source`, for the `MdmAttribute` returned by the `getParentAttribute` method of the `MdmHierarchy` for the hierarchy that this `StringSource` represents.

      Returns:
      A `StringSource` that has the elements of this `StringSource` that are specified by `comparison` and the descendants of those elements in the hierarchy that this `StringSource` represents.

    <!-- -->

    - #### selectDescendants

          public final StringSource selectDescendants(java.lang.String[] comparison,
                                                      Source parent)

      Selects the elements of this `StringSource` that are specified by `comparison` and the descendants of those elements in the hierarchy that this `StringSource` represents. Call this method only on a `StringSource` that is the `Source` for an `MdmHierarchy` or on a subtype of such a `Source`.
      Parameters:
      `comparison` - An array of `String` objects that have the values of the elements that you want to select from this `StringSource`.

      `parent` - The `Source`, or a subtype of the `Source`, for the `MdmAttribute` returned by the `getParentAttribute` method of the `MdmHierarchy` for the hierarchy that this `StringSource` represents.

      Returns:
      A `StringSource` that has the elements of this `StringSource` that are specified by `comparison` and the descendants of those elements in the hierarchy that this `StringSource` represents.

    <!-- -->

    - #### selectValue

          public final StringSource selectValue(java.lang.String value)

      Selects the elements of this `StringSource` that have the specified value.
      Parameters:
      `value` - A `String` that has the value of the elements of this `StringSource` that you want to have in the returned `StringSource`.

      Returns:
      A `StringSource` that has the elements of this `StringSource` that have the specified `String` value.

    <!-- -->

    - #### selectValues

          public final StringSource selectValues(java.lang.String[] values)

      Selects the elements of this `StringSource` that have the specified values.
      Parameters:
      `values` - An array of `String` objects that have the values of the elements of this `StringSource` that you want to have in the returned `StringSource`.

      Returns:
      A `StringSource` that has the elements of this `StringSource` that have the values specified by `values`.

    <!-- -->

    - #### substring

          public final StringSource substring(int index,
                                              int length)

      Selects the `length` number of characters, beginning at the position specified by `index`, from the values of the elements of this `StringSource`.
      Parameters:
      `index` - An `int` value that is the one-based position within the value of each element of this `StringSource` of the first character of the substring to select.

      `length` - An `int` value that is the number of characters in the substring.

      Returns:
      A `StringSource` that has the specified characters selected from the values of the elements of this `StringSource`.

    <!-- -->

    - #### substring

          public final StringSource substring(NumberSource index,
                                              NumberSource length)

      Selects the `length` number of characters, beginning at the position specified by `index`, from the values of the elements of this `StringSource`.
      Parameters:
      `index` - A `NumberSource` that has the one-based positions within the values of the elements of this `StringSource` of the first character of the substring or substrings to select.

      `length` - A `NumberSource` that has the number of characters in the substring or substrings.

      Returns:
      A `StringSource` that has the specified characters selected from the values of the elements of this `StringSource`.

    <!-- -->

    - #### textFill

          public final StringSource textFill(int width)

      Resizes the values of the elements of this `StringSource` to the specified width.
      Parameters:
      `width` - An `int` value that specifies the length that you want the values of the returned `StringSource` to be.

      Returns:
      A `StringSource` that has elements that have the values of the elements of this `StringSource` with the values truncated or lengthened by blank spaces to the number of characters specified by `width`.

    <!-- -->

    - #### textFill

          public final StringSource textFill(NumberSource width)

      Resizes the values of the elements of this `StringSource` to the specified width or widths.
      Parameters:
      `width` - A `NumberSource` that has elements that have the value or values that specify the length that you want the values of the returned `StringSource` to be.

      Returns:
      A `StringSource` that has elements that have the values of the elements of this `StringSource` with the values truncated or lengthened by blank spaces to the number of characters specified by `width`.

    <!-- -->

    - #### toLowercase

          public final StringSource toLowercase()

      Converts the alphabetic characters in the values of the elements of this `StringSource` to lowercase.
      Returns:
      A `StringSource` that has the elements of this `StringSource` with the alphabetic characters in the values of those elements converted to lowercase.

    <!-- -->

    - #### toUppercase

          public final StringSource toUppercase()

      Converts the alphabetic characters in the values of the elements of this `StringSource` to uppercase.
      Returns:
      A `StringSource` that has the elements of this `StringSource` with the alphabetic characters in the values of those elements converted to uppercase.

    <!-- -->

    - #### trim

          public final StringSource trim()

      Removes the leading and the trailing blank spaces from the values of the elements of this `StringSource`.
      Returns:
      A `StringSource` with the same elements as this `StringSource` but with all of the leading and trailing blank spaces removed from the values of the elements.

    <!-- -->

    - #### trimLeading

          public final StringSource trimLeading()

      Removes the leading blank spaces from the values of the elements of this `StringSource`.
      Returns:
      A `StringSource` with the same elements as this `StringSource` but with all of the leading blank spaces removed from the values of the elements.

    <!-- -->

    - #### trimTrailing

          public final StringSource trimTrailing()

      Removes the trailing blank spaces from the values of the elements of this `StringSource`.
      Returns:
      A `StringSource` with the same elements as this `StringSource` but with all of the trailing blank spaces removed from the values of the elements.

    <!-- -->

    - #### plus

          public final StringSource plus(StringSource rhs)

      Appends the values of the elements of `rhs` to the values of the elements of this `StringSource`.
      Parameters:
      `rhs` - A `StringSource` whose elements have the values that you want to append to the values of the elements of this `StringSource`.

      Returns:
      A `StringSource` that has the elements of this `StringSource` with the values of `rhs` appended to them.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](StringParameter.md)
- [Next Class](Template.md)

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
