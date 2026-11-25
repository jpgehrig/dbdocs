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

- [Prev Class](StructureUpdatedException.md)
- Next Class

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

oracle.olapi.data.cursor

## Interface ValueCursor

- All Superinterfaces:
  [Cursor](Cursor.md)

  ------------------------------------------------------------------------



      public interface ValueCursor
      extends Cursor

  A `Cursor` that has a value at its current position. A value can be any of the OLAP API data types or a `Source`.
  The value at the current position of a `ValueCursor` can also be `null`, in which case the `hasCurrentValue` method returns `false`. An example of a `ValueCursor` with an element whose value is `null` is the `Cursor` for a `Source` that was returned by the `getVoidSource` method of a `DataProvider`. Such a `Source` has one element whose value is `null`. In contrast, a `Source` returned by the `getEmptySource` method of a `DataProvider` has no elements, so it has no values, not even a `null` value. You cannot create a `ValueCursor` for an empty `Source` because the result set has no elements.

  A `ValueCursor` can have a single value or many values. For a `ValueCursor` that is a descendent of a `CompoundCursor`, the number of values it has, and therefore the number of positions, is specified by the set of values of the slower-varying outputs of the `CompoundCursor`. For example, a measure that has three dimensions might have a single value for any one set of its selected dimension values. If an application creates a query based on the measure and each dimension is an output in the query, then the base `ValueCursor` for the query has a single value (and only one position) for each set of values of the outputs.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.olapi.data.cursor.[Cursor](Cursor.md)

      [`FETCH_SIZE_NOT_SPECIFIED`](Cursor.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                         | Method and Description                                                                            |
    |-------------------------------------------|---------------------------------------------------------------------------------------------------|
    | `boolean`                                 | `getCurrentBoolean``()`<br>Gets the `boolean` value at the current position in the `ValueCursor`. |
    | `java.util.Date`                          | `getCurrentDate``()`<br>Gets the `Date` value at the current position in the `ValueCursor`.       |
    | `double`                                  | `getCurrentDouble``()`<br>Gets the `double` value at the current position in the `ValueCursor`.   |
    | `float`                                   | `getCurrentFloat``()`<br>Gets the `float` value at the current position in the `ValueCursor`.     |
    | `int`                                     | `getCurrentInteger``()`<br>Gets the `int` value at the current position in the `ValueCursor`.     |
    | `short`                                   | `getCurrentShort``()`<br>Gets the `short` value at the current position in the `ValueCursor`.     |
    | [`SourceIdentifier`](SourceIdentifier.md) | `getCurrentSource``()`<br>Gets the `SourceIdentifier` for the `ValueCursor`.                      |
    | `java.lang.String`                        | `getCurrentString``()`<br>Gets the `String` value at the current position in the `ValueCursor`.   |
    | `java.lang.Object`                        | `getCurrentValue``()`<br>Gets the value at the current position of the `ValueCursor`.             |
    | `boolean`                                 | `hasCurrentValue``()`<br>Indicates whether the `ValueCursor` has a value at its current position. |

    - ### Methods inherited from interface oracle.olapi.data.cursor.[Cursor](Cursor.md)

      [`getExtent`](Cursor.md)`, `[`getFetchSize`](Cursor.md)`, `[`getParentEnd`](Cursor.md)`, `[`getParentStart`](Cursor.md)`, `[`getPosition`](Cursor.md)`, `[`getSource`](Cursor.md)`, , `[`setFetchSize`](Cursor.md)`, `[`setPosition`](Cursor.md)

<!-- -->

- - ### Method Detail

    - #### hasCurrentValue

          boolean hasCurrentValue()

      Indicates whether the `ValueCursor` has a value at its current position.
      Returns:
      `true` if the `ValueCursor` has a value at its current position and `false` if it does not.

    <!-- -->

    - #### getCurrentValue

          java.lang.Object getCurrentValue()

      Gets the value at the current position of the `ValueCursor`. The value can be a `Source` or any of the specific data types such as `boolean`, `integer`, or `String`. This method is less efficient than the more specific methods, but `getCurrentValue` can return any value.
      Returns:
      The value at the current position.

    <!-- -->

    - #### getCurrentBoolean

          boolean getCurrentBoolean()

      Gets the `boolean` value at the current position in the `ValueCursor`.
      Returns:
      The `boolean` value at the current position.

    <!-- -->

    - #### getCurrentString

          java.lang.String getCurrentString()

      Gets the `String` value at the current position in the `ValueCursor`.
      Returns:
      The `String` value at the current position.

    <!-- -->

    - #### getCurrentShort

          short getCurrentShort()

      Gets the `short` value at the current position in the `ValueCursor`.
      Returns:
      The `short` value at the current position.

    <!-- -->

    - #### getCurrentInteger

          int getCurrentInteger()

      Gets the `int` value at the current position in the `ValueCursor`.
      Returns:
      The `int` value at the current position.

    <!-- -->

    - #### getCurrentFloat

          float getCurrentFloat()

      Gets the `float` value at the current position in the `ValueCursor`.
      Returns:
      The `float` value at the current position.

    <!-- -->

    - #### getCurrentDouble

          double getCurrentDouble()

      Gets the `double` value at the current position in the `ValueCursor`.
      Returns:
      The `double` value at the current position.

    <!-- -->

    - #### getCurrentDate

          java.util.Date getCurrentDate()

      Gets the `Date` value at the current position in the `ValueCursor`.
      Returns:
      The `Date` value at the current position.

    <!-- -->

    - #### getCurrentSource

          SourceIdentifier getCurrentSource()

      Gets the `SourceIdentifier` for the `ValueCursor`.
      Returns:
      The `SourceIdentifier` for the `ValueCursor`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](StructureUpdatedException.md)
- Next Class

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
