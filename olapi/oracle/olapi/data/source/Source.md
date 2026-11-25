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

- [Prev Class](ServerVersionException.md)
- [Next Class](SourceDefinition.md)

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

## Class Source

- java.lang.Object

- - oracle.olapi.data.source.Source

<!-- -->

- All Implemented Interfaces:
  [SourceIdentifier](../cursor/SourceIdentifier.md)

  <!-- -->

  Direct Known Subclasses:
  [BooleanSource](BooleanSource.md), [DateSource](DateSource.md), [NumberSource](NumberSource.md), [StringSource](StringSource.md)

  ------------------------------------------------------------------------



      public class Source
      extends java.lang.Object
      implements SourceIdentifier

  The base class of the Oracle OLAP query model. You use `Source` objects to specify the data that you want to retrieve from the data store and to specify any analytical or other operations that you want to perform on the data.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                                                                                                                                                                                                                                                                                                                                       |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static int`      | `COMPARISON_RULE_ASCENDING`<br>A constant that specifies that the `join` method selects only the elements of the `joined` `Source` that are in the `comparison` `Source` and that the positions of those elements in the resulting `Source` are in the same order as they are in the `comparison` `Source`.                                                                 |
    | `static int`      | `COMPARISON_RULE_ASCENDING_NULLS_FIRST`<br>A constant that specifies that the `join` method selects only the elements of the `joined` `Source` that are in the `comparison` `Source` and that the positions of those elements are in the same order in the resulting `Source` as they are in the `comparison` `Source` except that any `null` elements appear last.         |
    | `static int`      | `COMPARISON_RULE_ASCENDING_NULLS_LAST`<br>A constant that specifies that the `join` method selects only the elements of the `joined` `Source` that are in the `comparison` `Source` and that the positions of those elements in the resulting `Source` are in the same order as they are in the `comparison` `Source` with any `null` elements appearing last.              |
    | `static int`      | `COMPARISON_RULE_DESCENDING`<br>A constant that specifies that the `join` method selects only the elements of the `joined` `Source` that are in the `comparison` `Source` and that the positions of those elements in the resulting `Source` are in the reverse order of what they are in the `comparison` `Source`.                                                        |
    | `static int`      | `COMPARISON_RULE_DESCENDING_NULLS_FIRST`<br>A constant that specifies that the `join` method selects only the elements of the `joined` `Source` that are in the `comparison` `Source` and that the positions of those elements in the resulting `Source` are in the reverse order of what they are in the `comparison` `Source` with any `null` elements appearing first.   |
    | `static int`      | `COMPARISON_RULE_DESCENDING_NULLS_LAST`<br>A constant that specifies that the `join` method selects only the elements of the `joined` `Source` that are in the `comparison` `Source` and that the positions of those elements in the resulting `Source` are in the reverse order of what they are in the `comparison` `Source` except that any `null` elements appear last. |
    | `static int`      | `COMPARISON_RULE_REMOVE`<br>A constant that specifies that the `join` method selects only the elements of the joined `Source` that are not in the comparison `Source`.                                                                                                                                                                                                      |
    | `static int`      | `COMPARISON_RULE_SELECT`<br>A constant that specifies that the `join` method selects only the elements of the `joined` `Source` that are in the `comparison` `Source`.                                                                                                                                                                                                      |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                        | Method and Description                                                                                                                                                                                                                                                                                                                                                                      |
    |----------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `Source`                                                 | `alias``()`<br>Returns a `Source` that has the same elements as this `Source`, but that has this `Source` as its type.                                                                                                                                                                                                                                                                      |
    | `Source`                                                 | `appendValue``(Source appendValue)`<br>Appends the element of the specified `Source` to the elements of this `Source`.                                                                                                                                                                                                                                                                      |
    | `Source`                                                 | `appendValues``(Source appendValues)`<br>Appends the elements of the specified `Source` to the elements of this `Source`.                                                                                                                                                                                                                                                                   |
    | `Source`                                                 | `appendValues``(Source[] appendValues)`<br>Appends the elements of the specified `Source` array to the elements of this `Source`.                                                                                                                                                                                                                                                           |
    | `Source`                                                 | `at``(int position)`<br>Selects the element of this `Source` at the specified position.                                                                                                                                                                                                                                                                                                     |
    | `Source`                                                 | `at``(`[`NumberSource`](NumberSource.md)` position)`<br>Selects the elements of this `Source` at the positions specified by the `position` `NumberSource`.                                                                                                                                                                                                                                  |
    | [`NumberSource`](NumberSource.md)                        | `count``()`<br>Counts the elements in this `Source` that have values.                                                                                                                                                                                                                                                                                                                       |
    | [`NumberSource`](NumberSource.md)                        | `count``(boolean includeNoValue)`<br>Counts the elements in this `Source` including elements that have a `null` value, if the value of `includeNoValue` is `true`, or excluding elements that have a `null` value, if the value of `includeNoValue` is `false`.                                                                                                                             |
    | `Source`                                                 | `cumulativeInterval``()`<br>For each element of this `Source`, specifies the elements of this `Source` from position 1 to the position of the current element.                                                                                                                                                                                                                              |
    | `Source`                                                 | `cumulativeInterval``(int offset)`<br>For each element of this `Source`, specifies the elements of this `Source` from position 1 to the position of the current element plus the value specified by `offset`.                                                                                                                                                                               |
    | `Source`                                                 | `cumulativeInterval``(`[`NumberSource`](NumberSource.md)` offset)`<br>For each element of this `Source`, specifies the elements of this `Source` from position 1 to the position of the current element plus the value specified by `offset`.                                                                                                                                               |
    | `Source`                                                 | `distinct``()`<br>Selects all of the elements of this `Source` but removes any duplicated elements.                                                                                                                                                                                                                                                                                         |
    | [`BooleanSource`](BooleanSource.md)                      | `eq``(Source rhs)`<br>Compares the values of the elements of this `Source` to the values of the elements of the specified `Source`, and determines if they are equal.                                                                                                                                                                                                                       |
    | `Source`                                                 | `extract``()`<br>Produces a `Source` that has the elements of this `Source` and that has this `Source` as an extraction input.                                                                                                                                                                                                                                                              |
    | `Source`                                                 | `findMatchFor``(Source input)`<br>Determines if this `Source` or any of its outputs matches the specified `Source` and returns the matching `Source` when there is a match, or `null` when there is not.                                                                                                                                                                                    |
    | `Source`                                                 | `first``()`<br>Specifies the element at position 1 of this `Source`.                                                                                                                                                                                                                                                                                                                        |
    | [`BooleanSource`](BooleanSource.md)                      | `ge``(Source rhs)`<br>Compares each element of this `Source` to the corresponding element of another `Source` and determines if it has a greater or equal value.                                                                                                                                                                                                                            |
    | [`DataProvider`](DataProvider.md)                        | `getDataProvider``()`<br>Gets the `DataProvider` that is associated with this `Source`.                                                                                                                                                                                                                                                                                                     |
    | `Source`                                                 | `getDataType``()`<br>Gets the `Source` that represents the OLAP Java API data type of this `Source`.                                                                                                                                                                                                                                                                                        |
    | [`SourceDefinition`](SourceDefinition.md)                | `getDefinition``()`<br>Gets the `SourceDefinition` for this `Source`.                                                                                                                                                                                                                                                                                                                       |
    | `java.util.Set`                                          | `getExtractionInputs``()`<br>Gets the extraction inputs of this `Source` object.                                                                                                                                                                                                                                                                                                            |
    | `java.lang.String`                                       | `getID``()`<br>Gets a `String` that uniquely identifies this `Source` during this connection.                                                                                                                                                                                                                                                                                               |
    | `java.util.Set`                                          | `getInputs``()`<br>Gets all of the inputs of this `Source`, both the regular inputs and the extraction inputs, if any.                                                                                                                                                                                                                                                                      |
    | [`MetadataProvider`](../../metadata/MetadataProvider.md) | `getMetadataProvider``()`<br>Gets the `MetadataProvider` that provides the metadata objects for this primary `Source` object.                                                                                                                                                                                                                                                               |
    | `java.lang.String`                                       | `getMetadataProviderID``()`<br>Gets a `String` that uniquely identifies the `MetadataProvider` for this `Source`.                                                                                                                                                                                                                                                                           |
    | [`Model`](Model.md)                                      | `getModel``()`<br>Gets the `Model` associated with this `Source`.                                                                                                                                                                                                                                                                                                                           |
    | `java.util.List`                                         | `getOutputs``()`<br>Gets the outputs of this `Source`.                                                                                                                                                                                                                                                                                                                                      |
    | `java.util.Set`                                          | `getRegularInputs``()`<br>Gets the regular inputs of this `Source`.                                                                                                                                                                                                                                                                                                                         |
    | `Source`                                                 | `getType``()`<br>Gets the `Source` that is the type of this `Source`.                                                                                                                                                                                                                                                                                                                       |
    | [`BooleanSource`](BooleanSource.md)                      | `gt``(Source rhs)`<br>Compares each element of this `Source` to the corresponding element of another `Source` and determines if the value of the element of this `Source` is greater than the value of the element of the other `Source`.                                                                                                                                                   |
    | [`BooleanSource`](BooleanSource.md)                      | `hasValue``()`<br>Identifies whether each element of this `Source` has a value and produces a `BooleanSource` that has an element with the value of `true` when the value of the corresponding element of this `Source` is not `null` or `false` when the value is `null`.                                                                                                                  |
    | [`BooleanSource`](BooleanSource.md)                      | `in``(Source list)`<br>Determines if any element in this `Source` is also an element in the specified `Source`.                                                                                                                                                                                                                                                                             |
    | `Source`                                                 | `interval``(int bottom, int top)`<br>Selects the elements of this `Source` from position `bottom` to position `top`.                                                                                                                                                                                                                                                                        |
    | `Source`                                                 | `interval``(`[`NumberSource`](NumberSource.md)` bottom, `[`NumberSource`](NumberSource.md)` top)`<br>Selects the elements of this `Source` from position `bottom` to position `top`.                                                                                                                                                                                                        |
    | `boolean`                                                | `isSubtypeOf``(Source input)`<br>Indicates whether the specified `Source` is a subtype of this `Source`.                                                                                                                                                                                                                                                                                    |
    | `Source`                                                 | `join``(Source joined)`<br>Selects the elements of this `Source` that are specified by the elements of `joined` and adds `joined` as an output of the resulting `Source`.                                                                                                                                                                                                                   |
    | `Source`                                                 | `join``(Source joined, boolean comparison)`<br>Selects the elements of this `Source` that are determined by the elements of `joined` that are `true` or `false` as specified by the value of the `comparison` `boolean` and does not add `joined` as an output of the resulting `Source`.                                                                                                   |
    | `Source`                                                 | `join``(Source joined, boolean[] comparison)`<br>Selects the elements of this `Source` that are specified by the elements of `joined` that have a value equal to a value in the `comparison` `boolean` array and does not add `joined` as an output to the resulting `Source`.                                                                                                              |
    | `Source`                                                 | `join``(Source joined, java.util.Date comparison)`<br>Selects the elements of this `Source` that are specified by the elements of `joined` that have a value equal to the `comparison` `Date` and does not add `joined` as an output of the resulting `Source`.                                                                                                                             |
    | `Source`                                                 | `join``(Source joined, java.util.Date[] comparison)`<br>Selects the elements of this `Source` that are specified by the elements of `joined` that have a value equal to a value in the `comparison` `Date` array and does not add `joined` as an output of the resulting `Source`.                                                                                                          |
    | `Source`                                                 | `join``(Source joined, double comparison)`<br>Selects the elements of this `Source` that are specified by the elements of `joined` that have a value equal to the `comparison` `double` and does not add `joined` as an output of the resulting `Source`.                                                                                                                                   |
    | `Source`                                                 | `join``(Source joined, double[] comparison)`<br>Selects the elements of this `Source` that are specified by the elements of `joined` that have a value equal to a value in the `comparison` `double` array and does not add `joined` as an output of the resulting `Source`.                                                                                                                |
    | `Source`                                                 | `join``(Source joined, float comparison)`<br>Selects the elements of this `Source` that are specified by the elements of `joined` that have a value equal to the `comparison` `float` and does not add `joined` as an output of the resulting `Source`.                                                                                                                                     |
    | `Source`                                                 | `join``(Source joined, float[] comparison)`<br>Selects the elements of this `Source` that are specified by the elements of `joined` that have a value equal to a value in the `comparison` `float` array and does not add `joined` as an output of the resulting `Source`.                                                                                                                  |
    | `Source`                                                 | `join``(Source joined, int comparison)`<br>Selects the elements of this `Source` that are specified by the elements of `joined` that have a value equal to the `comparison` `int` and does not add `joined` as an output of the resulting `Source`.                                                                                                                                         |
    | `Source`                                                 | `join``(Source joined, int[] comparison)`<br>Selects the elements of this `Source` that are specified by the elements of `joined` that have a value equal to a value in the `comparison` `int` array and does not add `joined` as an output of the resulting `Source`.                                                                                                                      |
    | `Source`                                                 | `join``(Source joined, short comparison)`<br>Selects the elements of this `Source` that are specified by the elements of `joined` that have a value equal to the `comparison` `short` and does not add `joined` as an output of the resulting `Source`.                                                                                                                                     |
    | `Source`                                                 | `join``(Source joined, short[] comparison)`<br>Selects the elements of this `Source` that are specified by the elements of `joined` that have a value equal to a value in the `comparison` `short` array and does not add `joined` as an output of the resulting `Source`.                                                                                                                  |
    | `Source`                                                 | `join``(Source joined, Source comparison)`<br>Selects the elements of this `Source` that are specified by the elements of `joined` that appear in the `comparison` `Source` and does not add `joined` as an output of the resulting `Source`.                                                                                                                                               |
    | `Source`                                                 | `join``(Source joined, Source comparison, boolean visible)`<br>Selects the elements of this `Source` that are specified by the elements of `joined` that appear in `comparison` and that has or does not have `joined` as an output, depending on the value of `visible`.                                                                                                                   |
    | `Source`                                                 | `join``(Source joined, Source comparison, int comparisonRule)`<br>Selects the elements of this `Source` that are specified by the elements of `joined` that appear in `comparison` and does not add `joined` as an output of the resulting `Source`.                                                                                                                                        |
    | `Source`                                                 | `join``(Source joined, Source comparison, int comparisonRule, boolean visible)`<br>Selects the elements of this `Source` that are specified by the elements of `joined` that are selected from `joined` by comparison to the elements of `comparison` as determined by `comparisonRule`, and returns a `Source` that has or does not have `joined` as an output as determined by `visible`. |
    | `Source`                                                 | `join``(Source joined, java.lang.String comparison)`<br>Selects the elements of this `Source` that are specified by the elements of `joined` that have a value equal to the `comparison` `String` and does not add `joined` as an output of the resulting `Source`.                                                                                                                         |
    | `Source`                                                 | `join``(Source joined, java.lang.String[] comparison)`<br>Selects the elements of this `Source` that are specified by the elements of `joined` that have a value equal to a value in the `comparison` `String` array and does not add `joined` as an output of the resulting `Source`.                                                                                                      |
    | `Source`                                                 | `joinHidden``(Source joined)`<br>Selects the elements of this `Source` that are specified by the elements of `joined` and does not add `joined` as an output of the resulting `Source`.                                                                                                                                                                                                     |
    | `Source`                                                 | `last``()`<br>Specifies the element at last position of this `Source`.                                                                                                                                                                                                                                                                                                                      |
    | [`BooleanSource`](BooleanSource.md)                      | `le``(Source rhs)`<br>Compares each element of this `Source` to the corresponding element of another `Source` and determines if it has a lesser or equal value.                                                                                                                                                                                                                             |
    | [`BooleanSource`](BooleanSource.md)                      | `lt``(Source rhs)`<br>Compares each element of this `Source` to the corresponding element of another `Source` and determines if it has a lesser value.                                                                                                                                                                                                                                      |
    | `Source`                                                 | `movingInterval``(int bottom, int top)`<br>For each element of this `Source`, selects the elements of this `Source` in the range of positions from the position of the current element plus the `bottom` value to the position of the current element plus the `top` value.                                                                                                                 |
    | `Source`                                                 | `movingInterval``(`[`NumberSource`](NumberSource.md)` bottom, `[`NumberSource`](NumberSource.md)` top)`<br>For each element of this `Source`, selects the elements of this `Source` in the range of positions from the position of the current element plus the `bottom` value to the position of the current element plus the `top` value.                                                 |
    | [`BooleanSource`](BooleanSource.md)                      | `ne``(Source rhs)`<br>Compares the values of the elements of this `Source` to the values of the elements of the specified `Source`, and determines if they are not equal.                                                                                                                                                                                                                   |
    | `Source`                                                 | `nullSource``()`<br>Produces a `Source` that has a single element with the value of `null` and that has the base `Source` as its type.                                                                                                                                                                                                                                                      |
    | `Source`                                                 | `offset``(int offset)`<br>For each element of this `Source`, selects the element of this `Source` that is the specified number of positions away from it.                                                                                                                                                                                                                                   |
    | `Source`                                                 | `offset``(`[`NumberSource`](NumberSource.md)` offset)`<br>For each element of this `Source`, selects the element of this `Source` that is the specified number of positions away from it.                                                                                                                                                                                                   |
    | [`NumberSource`](NumberSource.md)                        | `position``()`<br>Produces a `NumberSource` that has an ordinal integer value for the position of each element of this `Source` and that has this `Source` as a regular input.                                                                                                                                                                                                              |
    | [`NumberSource`](NumberSource.md)                        | `position``(boolean zeroBased)`<br>Produces a `NumberSource` that has an ordinal integer value for the position of each element of this `Source` and that has this `Source` as a regular input.                                                                                                                                                                                             |
    | [`NumberSource`](NumberSource.md)                        | `positionOfValue``(Source value)`<br>Produces a `NumberSource` that has the position of the element of this `Source` that has the value that is specified by `value`.                                                                                                                                                                                                                       |
    | [`NumberSource`](NumberSource.md)                        | `positionOfValues``(Source values)`<br>Produces a `NumberSource` that has the positions of the elements of this `Source` that have the values that are specified by `values`.                                                                                                                                                                                                               |
    | [`NumberSource`](NumberSource.md)                        | `positionOfValues``(Source[] values)`<br>Produces a `NumberSource` that has the positions of the elements of this `Source` that have the `Source` objects that are specified by `values`.                                                                                                                                                                                                   |
    | `Source`                                                 | `recursiveJoin``(Source joined, Source comparison, Source parent, int comparisonRule)`<br>Selects the specified elements of this `Source` and orders them hierarchically by the parents and their children in the hierarchy that this `Source` represents.                                                                                                                                  |
    | `Source`                                                 | `recursiveJoin``(Source joined, Source comparison, Source parent, int comparisonRule, boolean parentsFirst, boolean parentsRestrictedToBase)`<br>Selects the specified elements of this `Source` and orders them hierarchically by the parents and their children in the hierarchy that this `Source` represents.                                                                           |
    | `Source`                                                 | `recursiveJoin``(Source joined, Source comparison, Source parent, int comparisonRule, boolean parentsFirst, boolean parentsRestrictedToBase, int maxIterations, boolean visible)`<br>Selects the parent and child elements of this `Source` that are determined by the `joined`, `comparison`, and `comparisonRule` parameters and orders the elements hierarchically.                      |
    | `Source`                                                 | `recursiveJoin``(Source joined, java.lang.String[] comparison, Source parent, int comparisonRule)`<br>Selects the specified elements of this `Source` and orders them hierarchically by the parents and their children in the hierarchy that this `Source` represents.                                                                                                                      |
    | `Source`                                                 | `recursiveJoin``(Source joined, java.lang.String[] comparison, Source parent, int comparisonRule, boolean parentsFirst, boolean parentsRestrictedToBase)`<br>Selects the specified elements of this `Source` and orders them hierarchically by the parents and their children in the hierarchy that this `Source` represents.                                                               |
    | `Source`                                                 | `recursiveJoin``(Source joined, java.lang.String comparison, Source parent, int comparisonRule)`<br>Selects the specified elements of this `Source` and orders them hierarchically by the parents and their children in the hierarchy that this `Source` represents.                                                                                                                        |
    | `Source`                                                 | `recursiveJoin``(Source joined, java.lang.String comparison, Source parent, int comparisonRule, boolean parentsFirst, boolean parentsRestrictedToBase)`<br>Selects the specified elements of this `Source` and orders them hierarchically by the parents and their children in the hierarchy that this `Source` represents.                                                                 |
    | `Source`                                                 | `remove``(`[`BooleanSource`](BooleanSource.md)` filter)`<br>Removes the elements of this `Source` for which the corresponding element of the specified `BooleanSource` has a value of `true`.                                                                                                                                                                                               |
    | `Source`                                                 | `removeValue``(Source value)`<br>Removes the elements of this `Source` that have the specified value.                                                                                                                                                                                                                                                                                       |
    | `Source`                                                 | `removeValues``(Source values)`<br>Removes the elements of this `Source` that have the specified values.                                                                                                                                                                                                                                                                                    |
    | `Source`                                                 | `removeValues``(Source[] values)`<br>Removes the elements of this `Source` that have the specified `Source` objects.                                                                                                                                                                                                                                                                        |
    | `Source`                                                 | `select``(`[`BooleanSource`](BooleanSource.md)` filter)`<br>Selects the elements of this `Source` for which the corresponding element of the specified `BooleanSource` has a value of `true`.                                                                                                                                                                                               |
    | `Source`                                                 | `selectDescendants``(Source comparison, Source parent)`<br>Selects the elements of this `Source` that are specified by `comparison` and the descendants of those elements in the hierarchy that this `Source` represents.                                                                                                                                                                   |
    | `Source`                                                 | `selectValue``(Source value)`<br>Selects the element of this `Source` that has the specified `Source` as its value.                                                                                                                                                                                                                                                                         |
    | `Source`                                                 | `selectValues``(Source values)`<br>Selects the elements of this `Source` that have the specified values.                                                                                                                                                                                                                                                                                    |
    | `Source`                                                 | `selectValues``(Source[] values)`<br>Selects the elements of this `Source` that have the specified values.                                                                                                                                                                                                                                                                                  |
    | `Source`                                                 | `sortAscending``()`<br>Sorts the elements of this `Source` in the ascending order of their data type.                                                                                                                                                                                                                                                                                       |
    | `Source`                                                 | `sortAscending``(Source sortValue)`<br>Selects the elements of this `Source` that are specified by the elements of `sortValue`, and orders them in the ascending order of the `sortValue` data type.                                                                                                                                                                                        |
    | `Source`                                                 | `sortAscending``(Source sortValue, boolean nullsFirst)`<br>Selects the elements of this `Source` that are specified by the elements of `sortValue`, and orders them in the ascending order of the `sortValue` data type.                                                                                                                                                                    |
    | `Source`                                                 | `sortAscendingHierarchically``(Source parent)`<br>Selects the elements of this `Source` and the descendants of those elements in the hierarchy that this `Source` represents and sorts the children of the parents in ascending order with the parents appearing before the children in the result.                                                                                         |
    | `Source`                                                 | `sortAscendingHierarchically``(Source parent, boolean parentsFirst)`<br>Selects the elements of this `Source` and the descendants of those elements in the hierarchy that this `Source` represents and sorts the children of the parents in ascending order.                                                                                                                                |
    | `Source`                                                 | `sortAscendingHierarchically``(Source joined, Source parent)`<br>Selects the elements of this `Source` that are specified by `joined` and the descendants of those elements in the hierarchy that this `Source` represents and sorts the children of the parents in ascending order with the parents appearing before their children.                                                       |
    | `Source`                                                 | `sortAscendingHierarchically``(Source joined, Source parent, boolean parentsFirst, boolean parentsRestrictedToBase)`<br>Selects the elements of this `Source` that are specified by `joined` and the descendants of those elements in the hierarchy that this `Source` represents and sorts the children of the parents in ascending order.                                                 |
    | `Source`                                                 | `sortDescending``()`<br>Sorts the elements of this `Source` in the descending order of their values.                                                                                                                                                                                                                                                                                        |
    | `Source`                                                 | `sortDescending``(Source sortValue)`<br>Selects the elements of this `Source` that are specified by the elements of `sortValue`, and orders them in the descending order of the `sortValue` data type.                                                                                                                                                                                      |
    | `Source`                                                 | `sortDescending``(Source sortValue, boolean nullsFirst)`<br>Selects the elements of this `Source` that are specified by the elements of `sortValue`, and orders them in the descending order of the `sortValue` data type.                                                                                                                                                                  |
    | `Source`                                                 | `sortDescendingHierarchically``(Source parent)`<br>Selects the elements of this `Source` and the descendants of those elements in the hierarchy that this `Source` represents and sorts the children of the parents in descending order with the parents appearing before the children in the result.                                                                                       |
    | `Source`                                                 | `sortDescendingHierarchically``(Source parent, boolean parentsFirst)`<br>Selects the elements of this `Source` and the descendants of those elements in the hierarchy that this `Source` represents and sorts the children of the parents in descending order.                                                                                                                              |
    | `Source`                                                 | `sortDescendingHierarchically``(Source joined, Source parent)`<br>Selects the elements of this `Source` that are specified by `joined` and the descendants of those elements in the hierarchy that this `Source` represents and sorts the children of the parents in descending order with the parents appearing before their children.                                                     |
    | `Source`                                                 | `sortDescendingHierarchically``(Source joined, Source parent, boolean parentsFirst, boolean parentsRestrictedToBase)`<br>Selects the elements of this `Source` that are specified by `joined` and the descendants of those elements in the hierarchy that this `Source` represents and sorts the children of the parents in descending order.                                               |
    | [`NumberSource`](NumberSource.md)                        | `toDoubleSource``()`<br>Converts the values of the elements of this `Source` to the Java `double` data type.                                                                                                                                                                                                                                                                                |
    | [`NumberSource`](NumberSource.md)                        | `toFloatSource``()`<br>Converts the values of the elements of this `Source` to the Java `float` data type.                                                                                                                                                                                                                                                                                  |
    | [`NumberSource`](NumberSource.md)                        | `toIntegerSource``()`<br>Converts the values of the elements of this `Source` to the Java `int` data type.                                                                                                                                                                                                                                                                                  |
    | [`NumberSource`](NumberSource.md)                        | `toShortSource``()`<br>Converts the values of the elements of this `Source` to the Java `short` data type.                                                                                                                                                                                                                                                                                  |
    | [`StringSource`](StringSource.md)                        | `toStringSource``()`<br>Converts the values of the elements of this `Source` to Java `String` objects.                                                                                                                                                                                                                                                                                      |
    | `Source`                                                 | `value``()`<br>Produces a `Source` that has the elements of this `Source` and that has this `Source` as an input.                                                                                                                                                                                                                                                                           |
    | `Source`                                                 | `value``(Source input)`<br>Produces a `Source` that has the same elements as this `Source` and that has the specified `Source` as an input.                                                                                                                                                                                                                                                 |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### COMPARISON_RULE_ASCENDING

          public static final int COMPARISON_RULE_ASCENDING

      A constant that specifies that the `join` method selects only the elements of the `joined` `Source` that are in the `comparison` `Source` and that the positions of those elements in the resulting `Source` are in the same order as they are in the `comparison` `Source`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### COMPARISON_RULE_ASCENDING_NULLS_FIRST

          public static final int COMPARISON_RULE_ASCENDING_NULLS_FIRST

      A constant that specifies that the `join` method selects only the elements of the `joined` `Source` that are in the `comparison` `Source` and that the positions of those elements are in the same order in the resulting `Source` as they are in the `comparison` `Source` except that any `null` elements appear last.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### COMPARISON_RULE_ASCENDING_NULLS_LAST

          public static final int COMPARISON_RULE_ASCENDING_NULLS_LAST

      A constant that specifies that the `join` method selects only the elements of the `joined` `Source` that are in the `comparison` `Source` and that the positions of those elements in the resulting `Source` are in the same order as they are in the `comparison` `Source` with any `null` elements appearing last. This rule is the same as `COMPARISON_RULE_ASCENDING`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### COMPARISON_RULE_DESCENDING

          public static final int COMPARISON_RULE_DESCENDING

      A constant that specifies that the `join` method selects only the elements of the `joined` `Source` that are in the `comparison` `Source` and that the positions of those elements in the resulting `Source` are in the reverse order of what they are in the `comparison` `Source`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### COMPARISON_RULE_DESCENDING_NULLS_FIRST

          public static final int COMPARISON_RULE_DESCENDING_NULLS_FIRST

      A constant that specifies that the `join` method selects only the elements of the `joined` `Source` that are in the `comparison` `Source` and that the positions of those elements in the resulting `Source` are in the reverse order of what they are in the `comparison` `Source` with any `null` elements appearing first. This rule is the same as `COMPARISON_RULE_DESCENDING`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### COMPARISON_RULE_DESCENDING_NULLS_LAST

          public static final int COMPARISON_RULE_DESCENDING_NULLS_LAST

      A constant that specifies that the `join` method selects only the elements of the `joined` `Source` that are in the `comparison` `Source` and that the positions of those elements in the resulting `Source` are in the reverse order of what they are in the `comparison` `Source` except that any `null` elements appear last.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### COMPARISON_RULE_REMOVE

          public static final int COMPARISON_RULE_REMOVE

      A constant that specifies that the `join` method selects only the elements of the joined `Source` that are not in the comparison `Source`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### COMPARISON_RULE_SELECT

          public static final int COMPARISON_RULE_SELECT

      A constant that specifies that the `join` method selects only the elements of the `joined` `Source` that are in the `comparison` `Source`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### alias

          public final Source alias()

      Returns a `Source` that has the same elements as this `Source`, but that has this `Source` as its type. Use this method when you want to control the match of a `Source` to an input or to create a parameter to use as the input of a function.
      Returns:
      A `Source` that has the same elements, inputs, and outputs as this `Source` object, but that has this `Source` as its type.

    <!-- -->

    - #### appendValue

          public final Source appendValue(Source appendValue)

      Appends the element of the specified `Source` to the elements of this `Source`.
      This method is equivalent to the following code where `base` is this `Source`, `appendSource` is the `Source` whose elements you want to append to this `Source`, and `dp` is the `DataProvider`.

           Source discriminator = dp.createListSource(new Source[]
                                                      {base, appendSource});
           Source result = discriminator.extract()
                                        .join(discriminator, dp.getEmptySource(),
                                              Source.COMPARISON_RULE_REMOVE, false);

      Parameters:
      `appendValue` - A `Source` whose element you want to append to this `Source`.

      Returns:
      A `Source` that has the same elements as this `Source` with the element of the specified `Source` appended.

    <!-- -->

    - #### appendValues

          public final Source appendValues(Source[] appendValues)

      Appends the elements of the specified `Source` array to the elements of this `Source`.
      This method is equivalent to the following code where `base` is this `Source`, `appendSource` is the `Source` array whose elements you want to append to this `Source`, and `dp` is the `DataProvider`.

           Source discriminator = dp.createListSource(new Source[]
                                                      {base, appendSource});
           Source result = discriminator.extract()
                                        .join(discriminator, dp.getEmptySource(),
                                              Source.COMPARISON_RULE_REMOVE, false);

      Parameters:
      `appendValues` - An array of `Source` objects whose elements you want to append to this `Source`.

      Returns:
      A `Source` that has the same elements as this `Source` with the elements of the specified `Source` array appended.

    <!-- -->

    - #### appendValues

          public final Source appendValues(Source appendValues)

      Appends the elements of the specified `Source` to the elements of this `Source`.
      This method is equivalent to the following code where `base` is this `Source`, `appendSource` is the `Source` whose elements you want to append to this `Source`, and `dp` is the `DataProvider`.

           Source discriminator = dp.createListSource(new Source[]
                                                      {base, appendSource});
           Source result = discriminator.extract()
                                        .join(discriminator, dp.getEmptySource(),
                                              Source.COMPARISON_RULE_REMOVE, false);

      Parameters:
      `appendValues` - A `Source` whose elements you want to append to this `Source`.

      Returns:
      A `Source` that has the same elements as this `Source` with the elements of the specified `Source` appended.

    <!-- -->

    - #### at

          public final Source at(int position)

      Selects the element of this `Source` at the specified position.
      This method is equivalent to the following code where `base` is this `Source` and `pos` specifies the position of the element that you want in the returned `Source`.

           Source result = base.join(base.position(), pos,
                                     Source.COMPARISON_RULE_SELECT, false);

      Parameters:
      `position` - The one-based position of the element of this `Source` that you want to have in the returned `Source`.

      Returns:
      A `Source` that has the element of this `Source` specified by `position`.

    <!-- -->

    - #### at

          public final Source at(NumberSource position)

      Selects the elements of this `Source` at the positions specified by the `position` `NumberSource`.
      This method is equivalent to the following code where `base` is this `Source` and `pos` is the `NumberSource` that specifies the positions of the elements that you want the returned `Source` to have.

           Source result = base.join(base.position(), pos,
                                     Source.COMPARISON_RULE_SELECT, false);

      In the following example, `dp` is the `DataProvider`, and `prodHier` is the `Source` for the default hierarchy of a dimension of product values.
           NumberSource positions = dp.createListSource(new int[] {3, 6, 9});
           Source result = prodHier.at(positions);

      A `Cursor` for the `result` `Source` has the following unique values.
           PRODUCT_PRIMARY::FAMILY::DISK
           PRODUCT_PRIMARY::ITEM::INT 8X DVD
           PRODUCT_PRIMARY::ITEM::INT RW DVD

      Parameters:
      `position` - A `NumberSource` that has the one-based positions of the elements of this `Source` that you want to have in the resulting `Source`.

      Returns:
      A `Source` that has the elements of this `Source` that are specified by `position`.

    <!-- -->

    - #### count

          public final NumberSource count()

      Counts the elements in this `Source` that have values.
      Returns:
      A `NumberSource` that has an element whose value is the number of elements in this `Source` that have a value that is not `null`.

    <!-- -->

    - #### count

          public final NumberSource count(boolean includeNoValue)

      Counts the elements in this `Source` including elements that have a `null` value, if the value of `includeNoValue` is `true`, or excluding elements that have a `null` value, if the value of `includeNoValue` is `false`.
      Parameters:
      `includeNoValue` - Specifies whether this method counts elements with a `null` value. Specify `true` if you want the method to count elements with a `null` value or `false` if you do not.

      Returns:
      A `NumberSource` that has an element whose value is the number of elements in this `Source`.

    <!-- -->

    - #### cumulativeInterval

          public final Source cumulativeInterval()

      For each element of this `Source`, specifies the elements of this `Source` from position 1 to the position of the current element. This method is equivalent to the following code where `base` is this `Source` and `dp` is the `DataProvider`.
           Source range = dp.createRangeSource(1, base.position());
           Source cumInterval = base.join(base.position(), range,
                                          Source.COMPARISON_RULE_SELECT, false);

      Because `range`, the `comparison` parameter of the join operation, has an input of `base`, the resulting `cumInterval` `Source` also has `base` as an input.
      In the following example, `shortDescMonths2002` is a `Source` that specifies the short descriptions for the months for the year 2002. The `Source` does not have any inputs or outputs. The first line produces the `cumIntMonths` `Source`, which has a type of `shortDescMonths2002` and has `shortDescMonths2002` as an input. The second line joins `cumIntMonths` to `shortDescMonths2002`. The input of `cumIntMonths` is matched by the `joined` parameter, `shortDescMonths2002`.

           Source cumIntMonths = shortDescMonths2002.cumulativeInterval();
           Source result = cumIntMonths.join(shortDescMonths2002);

      A `Cursor` for `result` has the following values, which are displayed with the positions of the elements of `result` in the left column, the values of the `shortDescMonths2002` output in the middle column, and the values of `result` in the right column. The `Cursor` has the 78 elements specified by the `result` `Source` but the values from element 7 to element 66 are not shown.
                           Cumulative Interval
               Months 2002   for Months 2002
               ----------- -------------------
           1:   JAN-02        JAN-02
           2:   FEB-02        JAN-02
           3:   FEB-02        FEB-02
           4:   MAR-02        JAN-02
           5:   MAR-02        FEB-02
           6:   MAR-02        MAR-02
           . . .
           67:  DEC-02        JAN-02
           68:  DEC-02        FEB-02
           69:  DEC-02        MAR-02
           70:  DEC-02        APR-02
           71:  DEC-02        MAY-02
           72:  DEC-02        JUN-02
           73:  DEC-02        JUL-02
           74:  DEC-02        AUG-02
           75:  DEC-02        SEP-02
           76:  DEC-02        OCT-02
           77:  DEC-02        NOV-02
           78:  DEC-02        DEC-02

      Returns:
      A `Source` that, for each element of this `Source`, specifies the positions of this `Source` that are less than or equal to the position of that element.

    <!-- -->

    - #### cumulativeInterval

          public final Source cumulativeInterval(int offset)

      For each element of this `Source`, specifies the elements of this `Source` from position 1 to the position of the current element plus the value specified by `offset`. This method is equivalent to the following code where `base` is this `Source`, `dp` is the `DataProvider`, and `offset` is an integer.
           Source range = dp.createRangeSource(1, base.position().plus(offset));
           Source cumInterval = base.join(base.position(), range,
                                          Source.COMPARISON_RULE_SELECT, false);

      Because `range`, the `comparison` parameter of the join operation, has an input of `base`, the resulting `cumInterval` `Source` also has `base` as an input.
      In the following example, `shortDescMonths2002` is a `Source` that specifies the short descriptions of the months for the year 2002. The `Source` does not have any inputs or outputs. The first line produces the `cumIntMonths3` `Source`, which has a type of `shortDescMonths2002` and has `shortDescMonths2002` as an input. The second line joins `cumIntMonths3` to `shortDescMonths2002`. The input of `cumIntMonths3` is matched by the `joined` parameter, `shortDescMonths2002`.

           Source cumIntMonths3 = shortDescMonths2002.cumulativeInterval(3);
           Source result3 = cumIntMonths3.join(shortDescMonths2002);

      A `Cursor` for `result3` has the following values, which are displayed with the positions of the elements of `result3` in the left column, the values of the `shortDescMonths2002` output in the middle column, and the values of `result3` in the right column. The `Cursor` has the 108 elements specified by the `result3` `Source` but the values from element 10 to element 96 are not shown.
                             Cumulative Interval
                 Months 2002   for Months 2002
                 ----------- -------------------
             1:    JAN-02       JAN-02
             2:    JAN-02       FEB-02
             3:    JAN-02       MAR-02
             4:    JAN-02       APR-02
             5:    FEB-02       JAN-02
             6:    FEB-02       FEB-02
             7:    FEB-02       MAR-02
             8:    FEB-02       APR-02
             9:    FEB-02       MAY-02
           . . .
            97:    DEC-02       JAN-02
            98:    DEC-02       FEB-02
            99:    DEC-02       MAR-02
           100:    DEC-02       APR-02
           101:    DEC-02       MAY-02
           102:    DEC-02       JUN-02
           103:    DEC-02       JUL-02
           104:    DEC-02       AUG-02
           105:    DEC-02       SEP-02
           106:    DEC-02       OCT-02
           107:    DEC-02       NOV-02
           108:    DEC-02       DEC-02

      Parameters:
      `offset` - The number of positions to add to the position of each element of this `Source`.

      Returns:
      A `Source` that, for each element of this `Source`, specifies the positions of this `Source` that are less than or equal to the position of that element plus the offset.

    <!-- -->

    - #### cumulativeInterval

          public final Source cumulativeInterval(NumberSource offset)

      For each element of this `Source`, specifies the elements of this `Source` from position 1 to the position of the current element plus the value specified by `offset`. This method is equivalent to the following code where `base` is this `Source`, `dp` is the `DataProvider`, and `offset` is a `NumberSource` specifying a single value.
           Source range = dp.createRangeSource(1, base.position().plus(offset));
           Source cumInterval = base.join(base.position(), range,
                                          Source.COMPARISON_RULE_SELECT, false);

      Because `range`, the `comparison` parameter of the join operation, has an input of `base`, the resulting `cumInterval` `Source` also has `base` as an input.
      For an example, see the `cumulativeInterval(int offset)` method, and substitute a `NumberSource` specifying the number 3 for the `offset` in the example of that method.

      Parameters:
      `offset` - The number of positions to add to the position of each element of this `Source`.

      Returns:
      A `Source` that, for each element of this `Source`, specifies the positions of this `Source` that are less than or equal to the position of that element plus the offset.

    <!-- -->

    - #### distinct

          public final Source distinct()

      Selects all of the elements of this `Source` but removes any duplicated elements. This method returns a `Source` that has the same type as this `Source`, but that has no duplicate elements.
      Each `Source` returned by this method has an associated `DistinctDefinition` object that contains its definition.

      Returns:
      A `Source` that has only the elements of this `Source` that are distinct.

    <!-- -->

    - #### eq

          public final BooleanSource eq(Source rhs)

      Compares the values of the elements of this `Source` to the values of the elements of the specified `Source`, and determines if they are equal. This method produces a `BooleanSource` that has an element whose value is `true` when the value of a given element of this `Source` equals the value of the corresponding element in the specified `Source` or `false` when it does not.
      Parameters:
      `rhs` - The `Source` whose elements you want to compare to the elements of this `Source`.

      Returns:
      A `BooleanSource` that has an element with the value of `true` when the value of a given element of this `Source` equals the value of the corresponding element of the specified `Source`, or `false` when it does not.

    <!-- -->

    - #### extract

          public final Source extract()

      Produces a `Source` that has the elements of this `Source` and that has this `Source` as an extraction input. Use this method when this `Source` has `Source` objects as its element values and you want to have access to the values of those `Source` objects.
      For example, the following code creates a list `Source`, `measures`, that has as the values of the elements `unitCost` and `unitPrice`, which are `Source` objects for measures of product unit costs and prices. Both measures are dimensioned by dimensions for times and products. The `timeSel` object represents the time value `CALENDAR_YEAR::MONTH::2000.06` and `prodSel` represents the product values `PRODUCT_PRIMARY::ITEM::ENVY STD` and `PRODUCT_PRIMARY::ITEM::ENVY EXE`. The `dp` object is the `DataProvider`.

      In the example, the `extract` method produces an unnamed `Source` that has the `measures` `Source` as an extraction input. The first `join` method produces a `Source` that has `prodSel` as an output and has `measures` as an extraction input. The second `join` method produces a `Source` that has `timeSel` as its first output, `prodSel` as its second output, and `measures` as an extraction input. The `joinHidden` method matches the `measures` `Source`, which is its `joined` parameter, to the extraction input. That `Source`-to-input match provides access to the values of the `Source` objects that are the values of `measures`. The `joinHidden` method also matches the regular inputs of the measures to the `timeSel` and `prodSel` outputs, which specify dimension values.

           Source measures = dp.createListSource(new Source[] {unitCost, unitPrice});
           Source cube = measures.extract().join(prodSel)
                                           .join(timeSel)
                                           .joinHidden(measures);

      The result of the `joinHidden` method is `cube`, which has as the values of its elements the values from the unit cost and unit price measures that are specified by its outputs, which are `timeSel` and `prodSel`. The `measures` `Source` is not an output of `cube` because the `joinedHidden` method does not make its `joined` parameter an output of the result.
      A `Cursor` for `cube` has as its values the unit prices and unit costs that are specified by its outputs, which are `ValueCursor` objects for `timeSel` and `prodSel`. The following table adds column headings and formatting to the values of the `Cursor` and includes only the local values of the dimensions. The left column lists the month, the next column to the right lists the products, the next column lists the unit costs, and the right column lists the unit prices.

            Month   Product    Cost    Price
           -------  --------  -------  -------
           2000.06  ENVY EXE  2893.68  3412.86
           2000.06  ENVY STD  2734.93  3235.71

      Returns:
      A `Source` that has the elements of this `Source` and that has this `Source` as an extraction input.

    <!-- -->

    - #### findMatchFor

          public final Source findMatchFor(Source input)

      Determines if this `Source` or any of its outputs matches the specified `Source` and returns the matching `Source` when there is a match, or `null` when there is not. A match occurs when this `Source` or any of its outputs is the same type as, or is a supertype of, the specified `Source`.
      Parameters:
      `input` - The `Source` that you want to match to this `Source` or to any of its outputs.

      Returns:
      The matching `Source` when there is a match, or `null` when there is not.

    <!-- -->

    - #### first

          public final Source first()

      Specifies the element at position 1 of this `Source`. This method is equivalent to the following code where `base` is this `Source` and `dp` is the `DataProvider`.
           Source firstBaseElement = base.join(base.position(),
                                               dp.createConstantSource(1),
                                               Source.COMPARISON_RULE_SELECT,
                                               false);

      Returns:
      A `Source` that has the first element of this `Source`.

    <!-- -->

    - #### ge

          public final BooleanSource ge(Source rhs)

      Compares each element of this `Source` to the corresponding element of another `Source` and determines if it has a greater or equal value. This method produces a `BooleanSource` that has an element with the value of `true` for each element of this `Source` that has a value that is greater than or equal to the value of the corresponding element in the specified `Source`, and an element with the value of `false` for each element of this `Source` that does not.
      Parameters:
      `rhs` - The `Source` whose elements you want to compare to the elements of this `Source`.

      Returns:
      A `BooleanSource` that has an element with the value of `true` for each element of this `Source` that has a value that is greater than or equal to the value of the corresponding element in the specified `Source`, and an element with the value of `false` for each element of this `Source` that does not.

    <!-- -->

    - #### getDataProvider

          public final DataProvider getDataProvider()

      Gets the `DataProvider` that is associated with this `Source`.
      Returns:
      The `DataProvider` that is associated with this `Source`.

    <!-- -->

    - #### getDataType

          public Source getDataType()

      Gets the `Source` that represents the OLAP Java API data type of this `Source`. A `Source` can have one of the following OLAP Java API data types:
      - Boolean
      - Date
      - Double
      - Float
      - Integer
      - Number, which represents any numerical data type
      - Short
      - String
      - Value, which represents any OLAP Java API data type

      You can also get the `Source` for an OLAP Java API data type by using the `getSource` method of the `FundamentalMetadataObject` for that data type. You get the `FundamentalMetadataObject` by using a method of a `FundamentalMetadataProvider`, such as the `getBooleanDataType` method.

      You use the `getDataType` method when you want a `Source` that represents a data type. One use of such a `Source` is as the comparison `Source` in a join operation, as in the following join from the `MakingQueriesExamples.java` example program.

           Source result =
             prodSelWithShortDescr.join(salesMeasure,
                                        salesMeasure.getDataType(),
                                        Source.COMPARISON_RULE_DESCENDING,
                                        true)
                                   .join(timeSelWithShortDescr)
                                   .join(custSelWithShortDescr)
                                   .join(chanSelWithShortDescr);

      Returns:
      The `Source` that represents the OLAP Java API data type of this `Source`.

    <!-- -->

    - #### getDefinition

          public final SourceDefinition getDefinition()

      Gets the `SourceDefinition` for this `Source`. The `SourceDefinition` has information about the `Source`.
      Returns:
      The `SourceDefinition` for this `Source`.

    <!-- -->

    - #### getExtractionInputs

          public final java.util.Set getExtractionInputs()

      Gets the extraction inputs of this `Source` object.
      Returns:
      A `Set` that contains the `Source` objects that are the extraction inputs of this `Source`.

    <!-- -->

    - #### getID

          public final java.lang.String getID()

      Gets a `String` that uniquely identifies this `Source` during this connection.
      Specified by:
      [`getID`](../cursor/SourceIdentifier.md) in interface [`SourceIdentifier`](../cursor/SourceIdentifier.md)

      Returns:
      A `String` that uniquely identifies this `Source` during this connection.

    <!-- -->

    - #### getInputs

          public final java.util.Set getInputs()

      Gets all of the inputs of this `Source`, both the regular inputs and the extraction inputs, if any.
      Returns:
      A `Set` that contains the `Source` objects that are the inputs of this `Source`.

    <!-- -->

    - #### getMetadataProvider

          public final MetadataProvider getMetadataProvider()

      Gets the `MetadataProvider` that provides the metadata objects for this primary `Source` object. Returns `null` for a `Source` that is not a primary `Source`.
      Returns:
      The `MetadataProvider` that provides the metadata objects for this `Source` object.

    <!-- -->

    - #### getMetadataProviderID

          public final java.lang.String getMetadataProviderID()

      Gets a `String` that uniquely identifies the `MetadataProvider` for this `Source`.
      Specified by:
      [`getMetadataProviderID`](../cursor/SourceIdentifier.md) in interface [`SourceIdentifier`](../cursor/SourceIdentifier.md)

      Returns:
      A `String` that uniquely identifies the `MetadataProvider` for this `Source`.

    <!-- -->

    - #### getModel

          public Model getModel()

      Gets the `Model` associated with this `Source`. If this `Source` does not have an associated `Model`, then this method returns `null`.
      Returns:
      The `Model` associated with this `Source`, or `null`.

    <!-- -->

    - #### getOutputs

          public final java.util.List getOutputs()

      Gets the outputs of this `Source`.
      Returns:
      A `List` that contains the `Source` objects that are the outputs of this `Source`.

    <!-- -->

    - #### getRegularInputs

          public final java.util.Set getRegularInputs()

      Gets the regular inputs of this `Source`.
      Returns:
      A `Set` that contains the `Source` objects that are the regular inputs of this `Source`.

    <!-- -->

    - #### getType

          public final Source getType()

      Gets the `Source` that is the type of this `Source`. To retrieve the OLAP Java API data type of this `Source`, use the `getDataType` method.
      Returns:
      The type of this `Source`.

    <!-- -->

    - #### gt

          public final BooleanSource gt(Source rhs)

      Compares each element of this `Source` to the corresponding element of another `Source` and determines if the value of the element of this `Source` is greater than the value of the element of the other `Source`. This method produces a `BooleanSource` that has an element with the value of `true` for each element of this `Source` that has a value that is greater than the value of the corresponding element in the specified `Source`, and an element with the value of `false` for each element of this `Source` that does not.
      Parameters:
      `rhs` - The `Source` whose elements you want to compare to the elements of this `Source`.

      Returns:
      A `BooleanSource` that has an element with the value of `true` for each element of this `Source` that has a value that is greater than the value of the corresponding element in the specified `Source`, and an element with the value of `false` for each element of this `Source` that does not.

    <!-- -->

    - #### hasValue

          public final BooleanSource hasValue()

      Identifies whether each element of this `Source` has a value and produces a `BooleanSource` that has an element with the value of `true` when the value of the corresponding element of this `Source` is not `null` or `false` when the value is `null`.
      Returns:
      A `BooleanSource` that has an element with the value of `true` when the value of the corresponding element of this `Source` is not `null` or `false` when it is.

    <!-- -->

    - #### in

          public final BooleanSource in(Source list)

      Determines if any element in this `Source` is also an element in the specified `Source`. This method returns a `BooleanSource` that has an element with a value of `true` when the value of any element of this `Source` equals a value of an element in the specified `Source`.
      This method is equivalent to the following code where `base` is this `Source`.

           BooleanSource result = base.eq(list).forAny();

      Parameters:
      `list` - The `Source` that you want to compare to this `Source`.

      Returns:
      A `BooleanSource` that has an element with a value of `true` when the value of any element in this `Source` is equal to the value of an element in the specified `Source` or `false` when none of the values of the elements of this `Source` equals the value of an element of the specified `Source`.

    <!-- -->

    - #### interval

          public final Source interval(int bottom,
                                       int top)

      Selects the elements of this `Source` from position `bottom` to position `top`. The positions of a `Source` are one-based. This method is equivalent to the following code where `base` is this `Source` and `dp` is the `DataProvider`.
           Source range = dataProvider.createRangeSource(bottom, top);
           Source result = base.join(base.position(), range,
                                     Source.COMPARISON_RULE_SELECT, false);

      Parameters:
      `bottom` - The position of the first element in this `Source` that you want to have in the result.

      `top` - The position of the last element in this `Source` that you want to have in the result.

      Returns:
      A `Source` that specifies the elements of this `Source` from position `bottom` to position `top`.

    <!-- -->

    - #### interval

          public final Source interval(NumberSource bottom,
                                       NumberSource top)

      Selects the elements of this `Source` from position `bottom` to position `top`. The positions of a `Source` are one-based. This method is equivalent to the following code where `base` is this `Source` and `dp` is the `DataProvider`.
           Source range = dataProvider.createRangeSource(bottom, top);
           Source result = base.join(base.position(), range,
                                     Source.COMPARISON_RULE_SELECT, false);

      Parameters:
      `bottom` - The position of the first element in this `Source` that you want to have in the result.

      `top` - The position of the last element in this `Source` that you want to have in the result.

      Returns:
      A `Source` that specifies the elements of this `Source` from position `bottom` to position `top`.

    <!-- -->

    - #### isSubtypeOf

          public final boolean isSubtypeOf(Source input)

      Indicates whether the specified `Source` is a subtype of this `Source`.
      Parameters:
      `input` - The `Source` that you want to determine whether it is a subtype of this `Source`.

      Returns:
      `true` when the specified `Source` is a subtype of this `Source` or `false` when it is not.

    <!-- -->

    - #### join

          public final Source join(Source joined)

      Selects the elements of this `Source` that are specified by the elements of `joined` and adds `joined` as an output of the resulting `Source`. This method is equivalent to the following code where `base` is this `Source` and `dp` is the `DataProvider`.
           Source result = base.join(joined,
                                     dp.getEmptySource(),
                                     Source.COMPARISON_RULE_REMOVE,
                                     true);

      Parameters:
      `joined` - The `Source` whose elements specify the elements of this `Source` that appear in the resulting `Source`.

      Returns:
      A `Source` that has the elements of this `Source` that are specified by the elements of `joined` and that has `joined` as an output.

      See Also:
      `join(Source joined, Source comparison, int comparisonRule, boolean visible)`

    <!-- -->

    - #### join

          public final Source join(Source joined,
                                   double[] comparison)

      Selects the elements of this `Source` that are specified by the elements of `joined` that have a value equal to a value in the `comparison` `double` array and does not add `joined` as an output of the resulting `Source`. This method is equivalent to the following code where `base` is this `Source`, `dp` is the `DataProvider`, and `doubleArray` is the `double` array that you want to use to select elements of `joined`.
           Source result = base.join(joined,
                                     dp.createListSource(doubleArray),
                                     Source.COMPARISON_RULE_SELECT,
                                     false);

      Parameters:
      `joined` - The `Source` whose elements specify the elements of this `Source` that appear in the resulting `Source`.

      `comparison` - An array of `double` values that you want to use to select the elements of `joined`.

      Returns:
      A `Source` that has the elements of this `Source` that are specified by the elements of `joined` that have a value equal to a value in `comparison` and that does not have `joined` as an output.

      See Also:
      `join(Source joined, Source comparison, int comparisonRule, boolean visible)`

    <!-- -->

    - #### join

          public final Source join(Source joined,
                                   float[] comparison)

      Selects the elements of this `Source` that are specified by the elements of `joined` that have a value equal to a value in the `comparison` `float` array and does not add `joined` as an output of the resulting `Source`. This method is equivalent to the following code where `base` is this `Source`, `dp` is the `DataProvider`, and `floatArray` is the `float` array that you want to use to select elements of `joined`.
           Source result = base.join(joined,
                                     dp.createListSource(floatArray),
                                     Source.COMPARISON_RULE_SELECT,
                                     false);

      Parameters:
      `joined` - The `Source` whose elements specify the elements of this `Source` that appear in the resulting `Source`.

      `comparison` - An array of `float` values that you want to use to select the elements of `joined`.

      Returns:
      A `Source` that has the elements of this `Source` that are specified by the elements of `joined` that have a value equal to a value in `comparison` and that does not have `joined` as an output.

      See Also:
      `join(Source joined, Source comparison, int comparisonRule, boolean visible)`

    <!-- -->

    - #### join

          public final Source join(Source joined,
                                   int[] comparison)

      Selects the elements of this `Source` that are specified by the elements of `joined` that have a value equal to a value in the `comparison` `int` array and does not add `joined` as an output of the resulting `Source`. This method is equivalent to the following code where `base` is this `Source`, `dp` is the `DataProvider`, and `intArray` is the `int` array that you want to use to select elements of `joined`.
           Source result = base.join(joined,
                                     dp.createListSource(intArray),
                                     Source.COMPARISON_RULE_SELECT,
                                     false);

      Parameters:
      `joined` - The `Source` whose elements specify the elements of this `Source` that appear in the resulting `Source`.

      `comparison` - An array of `int` values that you want to use to select the elements of `joined`.

      Returns:
      A `Source` that has the elements of this `Source` that are specified by the elements of `joined` that have a value equal to a value in `comparison` and that does not have `joined` as an output.

      See Also:
      `join(Source joined, Source comparison, int comparisonRule, boolean visible)`

    <!-- -->

    - #### join

          public final Source join(Source joined,
                                   java.lang.String[] comparison)

      Selects the elements of this `Source` that are specified by the elements of `joined` that have a value equal to a value in the `comparison` `String` array and does not add `joined` as an output of the resulting `Source`. This method is equivalent to the following code where `base` is this `Source`, `dp` is the `DataProvider`, and `stringArray` is the `String` array that you want to use to select elements of `joined`.
           Source result = base.join(joined,
                                     dp.createListSource(stringArray),
                                     Source.COMPARISON_RULE_SELECT,
                                     false);

      Parameters:
      `joined` - The `Source` whose elements specify the elements of this `Source` that appear in the resulting `Source`.

      `comparison` - An array of `String` values that you want to use to select the elements of `joined`.

      Returns:
      A `Source` that has the elements of this `Source` that are specified by the elements of `joined` that have a value equal to a value in `comparison` and that does not have `joined` as an output.

      See Also:
      `join(Source joined, Source comparison, int comparisonRule, boolean visible)`

    <!-- -->

    - #### join

          public final Source join(Source joined,
                                   java.util.Date[] comparison)

      Selects the elements of this `Source` that are specified by the elements of `joined` that have a value equal to a value in the `comparison` `Date` array and does not add `joined` as an output of the resulting `Source`. This method is equivalent to the following code where `base` is this `Source`, `dp` is the `DataProvider`, and `dateArray` is the `Date` array that you want to use to select elements of `joined`.
           Source result = base.join(joined,
                                     dp.createListSource(dateArray),
                                     Source.COMPARISON_RULE_SELECT,
                                     false);

      Parameters:
      `joined` - The `Source` whose elements specify the elements of this `Source` that appear in the resulting `Source`.

      `comparison` - An array of `Date` values that you want to use to select the elements of `joined`.

      Returns:
      A `Source` that has the elements of this `Source` that are specified by the elements of `joined` that have a value equal to a value in `comparison` and that does not have `joined` as an output.

      See Also:
      `join(Source joined, Source comparison, int comparisonRule, boolean visible)`

    <!-- -->

    - #### join

          public final Source join(Source joined,
                                   short[] comparison)

      Selects the elements of this `Source` that are specified by the elements of `joined` that have a value equal to a value in the `comparison` `short` array and does not add `joined` as an output of the resulting `Source`. This method is equivalent to the following code where `base` is this `Source`, `dp` is the `DataProvider`, and `shortArray` is the `short` array that you want to use to select elements of `joined`.
           Source result = base.join(joined,
                                     dp.createListSource(shortArray),
                                     Source.COMPARISON_RULE_SELECT,
                                     false);

      Parameters:
      `joined` - The `Source` whose elements specify the elements of this `Source` that appear in the resulting `Source`.

      `comparison` - An array of `short` values that you want to use to select the elements of `joined`.

      Returns:
      A `Source` that has the elements of this `Source` that are specified by the elements of `joined` that have a value equal to a value in `comparison` and that does not have `joined` as an output.

      See Also:
      `join(Source joined, Source comparison, int comparisonRule, boolean visible)`

    <!-- -->

    - #### join

          public final Source join(Source joined,
                                   boolean[] comparison)

      Selects the elements of this `Source` that are specified by the elements of `joined` that have a value equal to a value in the `comparison` `boolean` array and does not add `joined` as an output to the resulting `Source`. This method is equivalent to the following code where `base` is this `Source`, `dp` is the `DataProvider`, and `booleanArray` is the `boolean` array that you want to use to select elements of `joined`.
           Source result = base.join(joined,
                                     dp.createListSource(booleanArray),
                                     Source.COMPARISON_RULE_SELECT,
                                     false);

      Parameters:
      `joined` - The `Source` whose elements specify the elements of this `Source` that appear in the resulting `Source`.

      `comparison` - An array of `boolean` values that you want to use to select the elements of `joined`.

      Returns:
      A `Source` that has the elements of this `Source` that are specified by the elements of `joined` that have a value equal to a value in `comparison` and that does not have `joined` as an output.

      See Also:
      `join(Source joined, Source comparison, int comparisonRule, boolean visible)`

    <!-- -->

    - #### join

          public final Source join(Source joined,
                                   double comparison)

      Selects the elements of this `Source` that are specified by the elements of `joined` that have a value equal to the `comparison` `double` and does not add `joined` as an output of the resulting `Source`. This method is equivalent to the following code where `base` is this `Source`, `dp` is the `DataProvider`, and `doubleValue` is the `double` that you want to use to select elements of `joined`.
           Source result = base.join(joined,
                                     dp.createConstantSource(doubleValue),
                                     Source.COMPARISON_RULE_SELECT,
                                     false);

      Parameters:
      `joined` - The `Source` whose elements specify the elements of this `Source` that appear in the resulting `Source`.

      `comparison` - A `double` value that you want to use to select the elements of `joined`.

      Returns:
      A `Source` that has the elements of this `Source` that are specified by the elements of `joined` that have a value equal to `comparison` and that does not have `joined` as an output.

      See Also:
      `join(Source joined, Source comparison, int comparisonRule, boolean visible)`

    <!-- -->

    - #### join

          public final Source join(Source joined,
                                   float comparison)

      Selects the elements of this `Source` that are specified by the elements of `joined` that have a value equal to the `comparison` `float` and does not add `joined` as an output of the resulting `Source`. This method is equivalent to the following code where `base` is this `Source`, `dp` is the `DataProvider`, and `floatValue` is the `float` that you want to use to select elements of `joined`.
           Source result = base.join(joined,
                                     dp.createConstantSource(floatValue),
                                     Source.COMPARISON_RULE_SELECT,
                                     false);

      Parameters:
      `joined` - The `Source` whose elements specify the elements of this `Source` that appear in the resulting `Source`.

      `comparison` - A `float` value that you want to use to select the elements of `joined`.

      Returns:
      A `Source` that has the elements of this `Source` that are specified by the elements of `joined` that have a value equal to `comparison` and that does not have `joined` as an output.

      See Also:
      `join(Source joined, Source comparison, int comparisonRule, boolean visible)`

    <!-- -->

    - #### join

          public final Source join(Source joined,
                                   int comparison)

      Selects the elements of this `Source` that are specified by the elements of `joined` that have a value equal to the `comparison` `int` and does not add `joined` as an output of the resulting `Source`. This method is equivalent to the following code where `base` is this `Source`, `dp` is the `DataProvider`, and `intValue` is the `int` that you want to use to select elements of `joined`.
           Source result = base.join(joined,
                                     dp.createConstantSource(intValue),
                                     Source.COMPARISON_RULE_SELECT,
                                     false);

      Parameters:
      `joined` - The `Source` whose elements specify the elements of this `Source` that appear in the resulting `Source`.

      `comparison` - An `int` value that you want to use to select the elements of `joined`.

      Returns:
      A `Source` that has the elements of this `Source` that are specified by the elements of `joined` that have a value equal to `comparison` and that does not have `joined` as an output.

      See Also:
      `join(Source joined, Source comparison, int comparisonRule, boolean visible)`

    <!-- -->

    - #### join

          public final Source join(Source joined,
                                   java.lang.String comparison)

      Selects the elements of this `Source` that are specified by the elements of `joined` that have a value equal to the `comparison` `String` and does not add `joined` as an output of the resulting `Source`. This method is equivalent to the following code where `base` is this `Source`, `dp` is the `DataProvider`, and `stringValue` is the `String` that you want to use to select elements of `joined`.
           Source result = base.join(joined,
                                     dp.createConstantSource(stringValue),
                                     Source.COMPARISON_RULE_SELECT,
                                     false);

      Parameters:
      `joined` - The `Source` whose elements specify the elements of this `Source` that appear in the resulting `Source`.

      `comparison` - A `String` value that you want to use to select the elements of `joined`.

      Returns:
      A `Source` that has the elements of this `Source` that are specified by the elements of `joined` that have a value equal to `comparison` and that does not have `joined` as an output.

      See Also:
      `join(Source joined, Source comparison, int comparisonRule, boolean visible)`

    <!-- -->

    - #### join

          public final Source join(Source joined,
                                   java.util.Date comparison)

      Selects the elements of this `Source` that are specified by the elements of `joined` that have a value equal to the `comparison` `Date` and does not add `joined` as an output of the resulting `Source`. This method is equivalent to the following code where `base` is this `Source`, `dp` is the `DataProvider`, and `dateValue` is the `Date` that you want to use to select elements of `joined`.
           Source result = base.join(joined,
                                     dp.createConstantSource(dateValue),
                                     Source.COMPARISON_RULE_SELECT,
                                     false);

      Parameters:
      `joined` - The `Source` whose elements specify the elements of this `Source` that appear in the resulting `Source`.

      `comparison` - A `Date` value that you want to use to select the elements of `joined`.

      Returns:
      A `Source` that has the elements of this `Source` that are specified by the elements of `joined` that have a value equal to `comparison` and that does not have `joined` as an output.

      See Also:
      `join(Source joined, Source comparison, int comparisonRule, boolean visible)`

    <!-- -->

    - #### join

          public final Source join(Source joined,
                                   Source comparison)

      Selects the elements of this `Source` that are specified by the elements of `joined` that appear in the `comparison` `Source` and does not add `joined` as an output of the resulting `Source`. This method is equivalent to the following code where `base` is this `Source`.
           Source result = base.join(joined, comparison,
                                     Source.COMPARISON_RULE_SELECT,
                                     false);

      Parameters:
      `joined` - The `Source` whose elements specify the elements of this `Source` that appear in the resulting `Source`.

      `comparison` - The `Source` that has the element or elements that you want to select from `joined`.

      Returns:
      A `Source` that specifies the elements of `base` as determined by the elements of `joined` that appear in `comparison` and that does not have `joined` as an output.

      See Also:
      `join(Source joined, Source comparison, int comparisonRule, boolean visible)`

    <!-- -->

    - #### join

          public final Source join(Source joined,
                                   Source comparison,
                                   int comparisonRule)

      Selects the elements of this `Source` that are specified by the elements of `joined` that appear in `comparison` and does not add `joined` as an output of the resulting `Source`.
      This method is equivalent to the following code where `base` is this `Source`.

           Source result = base.join(joined, comparison, comparisonRule, false);

      Parameters:
      `joined` - The `Source` whose elements specify the elements of this `Source` that appear in the resulting `Source`.

      `comparison` - The `Source` that has the element or elements that you want to select or remove from `joined`.

      `comparisonRule` - The rule that specifies whether this method selects from `joined` only the elements of `joined` that are in `comparison` or selects only the elements of `joined` that are not in `comparison`, and whether this method sorts the selected elements in the same order of positions as in `comparison` or in the reverse order of those positions. Specify a value for this parameter using one of the `Source.COMPARISON_RULE` fields.

      Returns:
      A `Source` that specifies the elements of `base` as determined by the elements of `joined` that appear in `comparison` and are selected and ordered as specified by `comparisonRule`, and that does not have `joined` as an output.

      See Also:
      `join(Source joined, Source comparison, int comparisonRule, boolean visible)`

    <!-- -->

    - #### join

          public final Source join(Source joined,
                                   Source comparison,
                                   int comparisonRule,
                                   boolean visible)

      Selects the elements of this `Source` that are specified by the elements of `joined` that are selected from `joined` by comparison to the elements of `comparison` as determined by `comparisonRule`, and returns a `Source` that has or does not have `joined` as an output as determined by `visible`. With this method and its shortcuts, you incrementally join `Source` objects to produce a query that specifies the data that you want to retrieve from the data store.
      Because a `Source` with an input does not fully specify the data to retrieve from the data store, you cannot create a `Cursor` for a `Source` with an input. To produce a `Source` for which you can create a `Cursor`, you must match to the input a `Source` that has the elements that you want to specify.

      You use this `join` method, or one of its shortcuts, to match a `Source` to an input. For a description of the concepts of type, data type, inputs, and outputs of a `Source`, and for detailed information about matching a `Source` to an input, see *Oracle OLAP Java API Developer's Guide*.

      Parameters:
      `joined` - The `Source` whose elements specify the elements of this `Source` that appear in the resulting `Source`.

      `comparison` - The `Source` that has the element or elements that you want to select or remove from `joined` or by which you want the elements of the `joined` `Source` ordered.

      `comparisonRule` - The rule that specifies whether this method selects from `joined` only the elements of `joined` that are in `comparison` or selects only the elements of `joined` that are not in `comparison`, and whether this method sorts the selected elements in the same order of positions as in `comparison` or in the reverse order of those positions. Specify a value for this parameter using one of the `Source.COMPARISON_RULE` fields.

      `visible` - A flag that specifies whether you want `joined` to be an output of the returned `Source`. Specify `true` when you want `joined` to be an output of the returned `Source` or `false` when you do not.

      Returns:
      A `Source` that specifies the elements of `base` as determined by the elements of `joined` as compared to the elements of `comparison` and selected and ordered as specified by `comparisonRule`, and that has or does not have `joined` as an output as determined by the value of `visible`.

    <!-- -->

    - #### join

          public final Source join(Source joined,
                                   Source comparison,
                                   boolean visible)

      Selects the elements of this `Source` that are specified by the elements of `joined` that appear in `comparison` and that has or does not have `joined` as an output, depending on the value of `visible`. This method is equivalent to the following code where `base` is this `Source`.
           Source result = base.join(joined,
                                     comparison,
                                     Source.COMPARISON_RULE_SELECT,
                                     visible);

      Parameters:
      `joined` - The `Source` whose elements specify the elements of this `Source` that appear in the resulting `Source`.

      `comparison` - The `Source` that has the element or elements that you want to select from `joined`.

      `visible` - A flag that specifies whether you want `joined` to be an output of the returned `Source`. Specify `true` when you want `joined` to be an output of the returned `Source`, or `false` when you do not.

      Returns:
      A `Source` that has the elements of this `Source` as specified by the elements of `joined` that appear in `comparison` and that has or does not have `joined` as an output as determined by the value of `visible`.

      See Also:
      `join(Source joined, Source comparison, int comparisonRule, boolean visible)`

    <!-- -->

    - #### join

          public final Source join(Source joined,
                                   short comparison)

      Selects the elements of this `Source` that are specified by the elements of `joined` that have a value equal to the `comparison` `short` and does not add `joined` as an output of the resulting `Source`. This method is equivalent to the following code where `base` is this `Source`, `dp` is the `DataProvider`, and `shortValue` is the `short` that you want to use to select elements of `joined`.
           Source result = base.join(joined,
                                     dp.createConstantSource(shortValue),
                                     Source.COMPARISON_RULE_SELECT,
                                     false);

      Parameters:
      `joined` - The `Source` whose elements specify the elements of this `Source` that appear in the resulting `Source`.

      `comparison` - A `short` value that you want to use to select the elements of `joined`.

      Returns:
      A `Source` that has the elements of this `Source` that are specified by the elements of `joined` that have a value equal to `comparison` and that does not have `joined` as an output.

      See Also:
      `join(Source joined, Source comparison, int comparisonRule, boolean visible)`

    <!-- -->

    - #### join

          public final Source join(Source joined,
                                   boolean comparison)

      Selects the elements of this `Source` that are determined by the elements of `joined` that are `true` or `false` as specified by the value of the `comparison` `boolean` and does not add `joined` as an output of the resulting `Source`.
      This method is equivalent to the following code where `base` is this `Source`, `dp` is the `DataProvider`, and `booleanValue` is the `boolean` that you want to use to select elements of `joined`.

           Source result = base.join(joined,
                                     dp.createConstantSource(booleanValue),
                                     dp.Source.COMPARISON_RULE_SELECT,
                                     false);

      Parameters:
      `joined` - The `Source` whose elements specify the elements of this `Source` that appear in the resulting `Source`.

      `comparison` - The `boolean` value that you want to use to select the elements of `joined`.

      Returns:
      A `Source` that specifies the elements of this `Source` as determined by the elements of `joined` that are specified by the value of `comparison` and that does not have `joined` as an output.

      See Also:
      `join(Source joined, Source comparison, int comparisonRule, boolean visible)`

    <!-- -->

    - #### joinHidden

          public final Source joinHidden(Source joined)

      Selects the elements of this `Source` that are specified by the elements of `joined` and does not add `joined` as an output of the resulting `Source`. This method is equivalent to the following code where `base` is this `Source` and `dp` is the `DataProvider`.
           Source result = base.join(joined,
                                     dp.getEmptySource(),
                                     Source.COMPARISON_RULE_REMOVE,
                                     false);

      Parameters:
      `joined` - The `Source` whose elements specify the elements of this `Source` that appear in the resulting `Source`.

      Returns:
      A `Source` that has the elements of this `Source` that are specified by the elements of `joined` and that has `joined` as an output.

      See Also:
      `join(Source joined, Source comparison, int comparisonRule, boolean visible)`

    <!-- -->

    - #### last

          public final Source last()

      Specifies the element at last position of this `Source`. This method is equivalent to the following code where `base` is this `Source`.
           Source lastBaseElement = base.join(base.position(), base.count(),
                                              Source.COMPARISON_RULE_SELECT, false);

      Returns:
      A `Source` that has the last element of this `Source`.

    <!-- -->

    - #### le

          public final BooleanSource le(Source rhs)

      Compares each element of this `Source` to the corresponding element of another `Source` and determines if it has a lesser or equal value. This method produces a `BooleanSource` that has an element with the value of `true` for each element of this `Source` that has a value that is less than or equal to the value of the corresponding element in the specified `Source`, and an element with the value of `false` for each element of this `Source` that does not.
      Parameters:
      `rhs` - The `Source` whose elements you want to compare to the elements of this `Source`.

      Returns:
      A `BooleanSource` that has an element with the value of `true` for each element of this `Source` that has a value that is less than or equal to the value of the corresponding element in the specified `Source`, and an element with the value of `false` for each element of this `Source` that does not.

    <!-- -->

    - #### lt

          public final BooleanSource lt(Source rhs)

      Compares each element of this `Source` to the corresponding element of another `Source` and determines if it has a lesser value. This method produces a `BooleanSource` that has an element with the value of `true` for each element of this `Source` that has a value that is less than the value of the corresponding element in the specified `Source`, and an element with the value of `false` for each element of this `Source` that does not.
      Parameters:
      `rhs` - The `Source` whose elements you want to compare to the elements of this `Source`.

      Returns:
      A `BooleanSource` that has an element with the value of `true` for each element of this `Source` that has a value that is less than the value of the corresponding element in the specified `Source`, and an element with the value of `false` for each element of this `Source` that does not.

    <!-- -->

    - #### movingInterval

          public final Source movingInterval(int bottom,
                                             int top)

      For each element of this `Source`, selects the elements of this `Source` in the range of positions from the position of the current element plus the `bottom` value to the position of the current element plus the `top` value. This method is equivalent to the following code where `base` is this `Source`.
           Source result = base.interval(base.position().plus(bottom),
                                         base.position().plus(top));

      Parameters:
      `bottom` - The offset from the position of the element of this `Source` of the position of the first element in the range of elements that you want to select.

      `top` - The offset from the position of the element of this `Source` of the position of the last element in the range of elements that you want to select.

      Returns:
      A `Source` that has, for each element of this `Source`, the elements of this `Source` that are in the range of positions from the current position plus `bottom` to the current position plus `top`.

      See Also:
      `interval(int bottom, int top)`

    <!-- -->

    - #### movingInterval

          public final Source movingInterval(NumberSource bottom,
                                             NumberSource top)

      For each element of this `Source`, selects the elements of this `Source` in the range of positions from the position of the current element plus the `bottom` value to the position of the current element plus the `top` value. This method is equivalent to the following code where `base` is this `Source`.
           Source result = base.interval(base.position().plus(bottom),
                                         base.position().plus(top));

      Parameters:
      `bottom` - The offset from the position of the element of this `Source` of the position of the first element in the range of elements that you want to select.

      `top` - The offset from the position of the element of this `Source` of the position of the last element in the range of elements that you want to select.

      Returns:
      A `Source` that has, for each element of this `Source`, the elements of this `Source` that are in the range of positions from the current position plus `bottom` to the current position plus `top`.

      See Also:
      `interval(oracle.olapi.data.source.NumberSource bottom, oracle.olapi.data.source.NumberSource top)`

    <!-- -->

    - #### ne

          public final BooleanSource ne(Source rhs)

      Compares the values of the elements of this `Source` to the values of the elements of the specified `Source`, and determines if they are not equal. This method produces a `BooleanSource` that has an element whose value is `true` when the value of a given element of this `Source` is not equal to the value of the corresponding element in the specified `Source`, or `false` when it is equal
      Parameters:
      `rhs` - The `Source` whose elements you want to compare to the elements of this `Source`.

      Returns:
      A `BooleanSource` that has an element with the value of `true` when the value of a given element of this `Source` is not equal to the value of the corresponding element of the specified `Source` or `false` when it is equal.

    <!-- -->

    - #### nullSource

          public final Source nullSource()

      Produces a `Source` that has a single element with the value of `null` and that has the base `Source` as its type. You can call this method on the `Source` for an `MdmStandardDimension`, `MdmTimeDimension`, or `MdmSubDimension`, or the `Source` for the OLAP Java API data type of a `CustomModel` object.
      Returns:
      A `Source` that has an element with the value of `null` and the base `Source` as its type.

    <!-- -->

    - #### offset

          public final Source offset(int offset)

      For each element of this `Source`, selects the element of this `Source` that is the specified number of positions away from it. This method is equivalent to the following code where `base` is this `Source`.
           Source result = base.join(base.position(),
                                     base.position().plus(offset),
                                     Source.COMPARISON_RULE_SELECT, false);

      For example, assume that this `Source` is named `month` and that its element values are the months for the year 2000 with 2000-01 as the value of the first element. When you call this method of the `month` object with an offset of 4, the value of first element of the resulting `Source` is 2000-05 and the resulting `Source` has a type of `month` and an input of `month`.
      Parameters:
      `offset` - The number of positions away (plus or minus) from an element of this `Source` that is the position of the element of this `Source` that you want to select.

      Returns:
      A `Source` whose elements are selected from the elements of this `Source` by identifying the position of each element in this `Source` and selecting the element whose position is the specified number of places (the offset) away.

    <!-- -->

    - #### offset

          public final Source offset(NumberSource offset)

      For each element of this `Source`, selects the element of this `Source` that is the specified number of positions away from it. This method is equivalent to the following code where `base` is this `Source`.
           Source result = base.join(base.position(),
                                     base.position().plus(offset),
                                     Source.COMPARISON_RULE_SELECT, false);

      For example, assume that this `Source` is named `month` and that its element values are the months for the year 2000 with 2000-01 as the value of the first element. When you call this method of the `month` object with an offset of 4, the value of first element of the resulting `Source` is 2000-05 and the resulting `Source` has a type of `month` and an input of `month`.
      Parameters:
      `offset` - The number of positions away (plus or minus) from an element of this `Source` that is the position of the element of this `Source` that you want to select.

      Returns:
      A `Source` whose elements are selected from the elements of this `Source` by identifying the position of each element in this `Source` and selecting the element whose position is the specified number of places (the offset) away.

    <!-- -->

    - #### position

          public final NumberSource position()

      Produces a `NumberSource` that has an ordinal integer value for the position of each element of this `Source` and that has this `Source` as a regular input.
      Returns:
      A `NumberSource` that has the positions of the elements of this `Source`.

    <!-- -->

    - #### position

          public final NumberSource position(boolean zeroBased)

      Produces a `NumberSource` that has an ordinal integer value for the position of each element of this `Source` and that has this `Source` as a regular input. The position values are zero-based if `zeroBased` is `true` or one-based if `zeroBased` is `false`.
      Parameters:
      `zeroBased` - A `boolean` that specifies whether you want the position values to be zero-based or one-based.

      Returns:
      A `NumberSource` that has the positions of the elements of this `Source`.

    <!-- -->

    - #### positionOfValue

          public final NumberSource positionOfValue(Source value)

      Produces a `NumberSource` that has the position of the element of this `Source` that has the value that is specified by `value`. Use this method for a `Source` that has `Source` objects as its element values.
      This method is equivalent to the following code where `base` is this `Source` and `value` is the `Source` whose position you want to determine.

           NumberSource result = base.position()
                                     .join(base, value,
                                           COMPARISON_RULE_SELECT, false);

      Parameters:
      `value` - A `Source` that is the value of the element of this `Source` whose position you want to know.

      Returns:
      A `NumberSource` that has the integer value of the position of the element of this `Source` that is specified by `value`. When this `Source` does not have an element that has the specified value, this method returns an empty `NumberSource`.

    <!-- -->

    - #### positionOfValues

          public final NumberSource positionOfValues(Source[] values)

      Produces a `NumberSource` that has the positions of the elements of this `Source` that have the `Source` objects that are specified by `values`. This method is equivalent to the following code where `base` is this `Source` and `values` is an array of `Source` objects.
           NumberSource result = base.position()
                                     .join(base, values,
                                           COMPARISON_RULE_SELECT, false);

      Parameters:
      `values` - A `Source` that has the values of the elements of this `Source` whose positions you want to know.

      Returns:
      A `NumberSource` that has the positions of the elements of this `Source` that have the values specified by `values`. When this `Source` does not have any elements that have the specified values, this method returns an empty `NumberSource`.

    <!-- -->

    - #### positionOfValues

          public final NumberSource positionOfValues(Source values)

      Produces a `NumberSource` that has the positions of the elements of this `Source` that have the values that are specified by `values`. This method is equivalent to the following code where `base` is this `Source` and `values` is a `Source` that has the values to select.
           NumberSource result = base.position()
                                     .join(base, values,
                                           COMPARISON_RULE_SELECT, false);

      Parameters:
      `values` - A `Source` that has the values of the elements of this `Source` whose positions you want to know.

      Returns:
      A `NumberSource` that has the positions of the elements of this `Source` that have the values specified by `values`. When this `Source` does not have any elements that have the specified values, this method returns an empty `NumberSource`.

    <!-- -->

    - #### recursiveJoin

          public final Source recursiveJoin(Source joined,
                                            Source comparison,
                                            Source parent,
                                            int comparisonRule,
                                            boolean parentsFirst,
                                            boolean parentsRestrictedToBase,
                                            int maxIterations,
                                            boolean visible)

      Selects the parent and child elements of this `Source` that are determined by the `joined`, `comparison`, and `comparisonRule` parameters and orders the elements hierarchically. The order of the elements is specified by `comparisonRule` and `parentsFirst`.
      This `Source` must be the `Source` for an `MdmHierarchy` or a subtype of that `Source`. The `joined` `Source` must have as an input the `Source` for the dimension of which the hierarchy is a component. For example, `SHIPMENTS` is a hierarchy of the `CUSTOMER_AWJ` dimension. If this `Source` is a selection of elements derived from the hierarchy, then the `joined` `Source` must have as an input the `Source` for the `CUSTOMER_AWJ` dimension. The `joined` `Source` could be the `Source` for a `MdmMeasure` or an `MdmAttribute` that has the dimension as an input, or the `Source` returned by the `value` method of the `Source` for the dimension.

      The parents of the elements of this `Source` are identified by the `parent` parameter. The `comparisonRule` value specifies the order of the elements within a level. The `parentsFirst` value specifies whether a parent appears before or after its children.

      For a `Source` that is a subtype of the hierarchy, the `parentsRestrictedToBase` parameter specifies how this method handles the hierarchical ordering of an element of this `Source` when the parent of that element is not an element of this `Source`. If an element of this `Source` is selected by this method and the parent of that element is not in this `Source` and if `parentsRestrictedToBase` is `true`, then this method puts the child element under the element of this `Source` that is the closest ancestor of the child element. If `parentsRestrictedToBase` is `false`, then this method uses the missing parent in ordering the elements of the hierarchy even though the missing parent does not appear in the result.

      This method does not add the `joined` `Source` as an output, so the value of the `visible` parameter is always `false`.

      The following example creates a `Source` that specifies a parent element and the children of the parent, and includes the descriptions of the values of the elements from the value description attribute. The example uses the following `Source` objects:

      - `parentValue`, which represents an element of the `SHIPMENTS` hierarchy of the `CUSTOMER_AWJ` dimension that has children.
      - `shipments`, which represents the hierarchy.
      - `custDim`, which represents the dimension.
      - `shipmentsParentAttr`, which represents the parent attribute for the hierarchy.
      - `custValDescAttr`, which represents the value description attribute for the dimension.

      The `comparisonRule` value specifies that the elements of the resulting `Source` are selected from elements of `shipments` that are in `custDim` and have `parentValue` as their parent. The `parentsFirst` and `parentsRestrictedToBase` values are both `true`. The `maxIterations` value is `5`, although this method currently ignores this parameter. The `visible` value is `false`, which is currently always the value that this method uses for this parameter.

           Source parentValue =
             shipments.selectValue("SHIPMENTS::WAREHOUSE::JPN");

           Source parentAndChildren =
             shipments.recursiveJoin(custDim.value(),
                                     parentValue,
                                     shipmentsParentAttr,
                                     Source.COMPARISON_RULE_SELECT,
                                     true,
                                     true,
                                     5,
                                     false);
           Source parentAndChildrenWithDescr =
             custValDescAttr.join(parentAndChildren);

      A `Cursor` for `parentAndChildrenWithDescr` has the following values.

           SHIPMENTS::WAREHOUSE::JPN, Japan
           SHIPMENTS::SHIP_TO::COMP SERV TOK, Computer Services Tokyo
           SHIPMENTS::SHIP_TO::KOSH ENT TOK, KOSH Entrpr Tokyo
           SHIPMENTS::SHIP_TO::MSTR TRD JPN NGA, Ministry of Intl. Trad Nagano
           SHIPMENTS::SHIP_TO::MSTR TRD JPN NGO, Ministry of Intl. Trad Nagoya

      To see the complete code for the example, and for examples of other signatures of `recursiveJoin` and of some of the related methods such as `selectDescendants` and `sortDescendingHierarchically`, see the `RecursiveJoinAndShortcutsExamples.java` example program. For examples from *Oracle OLAP Java API Developer's Guide* that use `recursiveJoin`, see the `SortingHierarchicallyByAttribute.java` program and the Hierarchical Sorting by Measure Value example in the `MakingQueriesExamples.java` program. For information on the example programs, see [Example Oracle OLAP Java API Programs](../../../../doc-files/ExamplePrograms.md).

      Parameters:
      `joined` - A `Source` that has as an input the dimension of which the hierarchy that this `Source` represents is a component.

      `comparison` - A `Source` that has the parent or parents that you want to select, along with their children, from this `Source`.

      `parent` - The `Source`, or a subtype of the `Source`, for the `MdmAttribute` returned by the `getParentAttribute` method of the `MdmHierarchy` for the hierarchy that this `Source` represents, or of which it is a subtype.

      `comparisonRule` - A constant that specifies whether this method selects the elements of this `Source` that are in `comparison`, or that have a parent or ancestor that is in `comparison`, and orders them as specified, or whether it selects the elements of this `Source` that are not in `comparison`, or that have a parent or ancestor that is not in `comparison`. Specify a value for this parameter using one of the `COMPARISON_RULE` fields.

      `parentsFirst` - A `boolean` that specifies whether parents appear before or after their children in the result. Specify `true` when you want parents to appear before their children or `false` when you want parents to appear after their children.

      `parentsRestrictedToBase` - A `boolean` that specifies whether to associate with the closest parent value the children in the result that do not have a parent in this `Source`.

      `maxIterations` - The maximum number of levels of the hierarchy that this method traverses. This method does not currently use this parameter.

      `visible` - Always `false`. A recursive join does not add `joined` as an output of the result.

      Returns:
      A `Source` that has the specified elements of this `Source` ordered hierarchically by the parents and their children in the hierarchy.

    <!-- -->

    - #### recursiveJoin

          public final Source recursiveJoin(Source joined,
                                            Source comparison,
                                            Source parent,
                                            int comparisonRule,
                                            boolean parentsFirst,
                                            boolean parentsRestrictedToBase)

      Selects the specified elements of this `Source` and orders them hierarchically by the parents and their children in the hierarchy that this `Source` represents. Use this method only with the `Source` for an `MdmHierarchy` or on a subtype of such a `Source`.
      This method is currently the same as `recursiveJoin(Source joined, Source comparison, Source parent, int comparisonRule, boolean parentsFirst, boolean parentsRestrictedToBase, int maxIterations, boolean visible)`.

      Parameters:
      `joined` - A `Source` whose elements specify the elements of this `Source` that appear in the resulting `Source`.

      `comparison` - A `Source` that has the elements that you want to select or remove from `joined`, or that has elements with values that specify parents or ancestors of elements that you want to select or remove from `joined`.

      `parent` - The `Source`, or a subtype of the `Source`, for the `MdmAttribute` returned by the `getParentAttribute` method of the `MdmHierarchy` for the hierarchy that this `Source` represents, or of which it is a subtype.

      `comparisonRule` - A constant that specifies whether this method selects from `joined` only the elements of `joined` that are in `comparison`, or that have a parent or ancestor that is in `comparison`, or selects only the elements of `joined` that are not in, or whose parent or ancestor is not in, `comparison`, and whether this method sorts the children of a parent in ascending or descending order. Specify a value for this parameter using one of the `COMPARISON_RULE` fields.

      `parentsFirst` - A flag that specifies whether parents appear before or after their children in the result when `comparisonRule` specifies sorting in ascending or descending order. Specify `true` when you want parents to appear before their children or `false` when you want parents to appear after their children.

      `parentsRestrictedToBase` - A flag that specifies whether to restrict the parents in the hierarchy to those that are in this `Source`. Specify `true` when you want to restrict the parents to the elements of this `Source` or `false` when you do not.

      Returns:
      A `Source` that has the specified elements of this `Source` ordered hierarchically by the parents and their children in the hierarchy that this `Source` represents.

      See Also:
      `recursiveJoin(Source joined, Source comparison, Source parent, int comparisonRule, boolean parentsFirst, boolean parentsRestrictedToBase, int maxIterations, boolean visible)`

    <!-- -->

    - #### recursiveJoin

          public final Source recursiveJoin(Source joined,
                                            java.lang.String comparison,
                                            Source parent,
                                            int comparisonRule,
                                            boolean parentsFirst,
                                            boolean parentsRestrictedToBase)

      Selects the specified elements of this `Source` and orders them hierarchically by the parents and their children in the hierarchy that this `Source` represents. Use this method only with the `Source` for an `MdmHierarchy` or on a subtype of such a `Source`.
      This method is the same as `recursiveJoin(Source joined, Source comparison, Source parent, int comparisonRule, boolean parentsFirst, boolean parentsRestrictedToBase)` except that the value of `comparison` is a `String` instead of a `Source`.

      Parameters:
      `joined` - A `Source` whose elements specify the elements of this `Source` that appear in the resulting `Source`.

      `comparison` - A `String` that specifies the value of the element that you want to select or remove from `joined` or that specifies the parent or ancestor of elements that you want to select or remove from `joined`.

      `parent` - The `Source`, or a subtype of the `Source`, for the `MdmAttribute` returned by the `getParentAttribute` method of the `MdmHierarchy` for the hierarchy that this `Source` represents, or of which it is a subtype.

      `comparisonRule` - A constant that specifies whether this method selects from `joined` only the elements of `joined` that are in `comparison`, or that have a parent or ancestor that is in `comparison`, or selects only the elements of `joined` that are not in, or whose parent or ancestor is not in, `comparison`, and whether this method sorts the children of a parent in ascending or descending order. Specify a value for this parameter using one of the `COMPARISON_RULE` fields.

      `parentsFirst` - A flag that specifies whether parents appear before or after their children in the result when `comparisonRule` specifies sorting in ascending or descending order. Specify `true` when you want parents to appear before their children or `false` when you want parents to appear after their children.

      `parentsRestrictedToBase` - A flag that specifies whether to restrict the parents in the hierarchy to those that are in this `Source`. Specify `true` when you want to restrict the parents to the elements of this `Source` or `false` when you do not.

      Returns:
      A `Source` that has the specified elements of this `Source` ordered hierarchically by the parents and their children in the hierarchy that this `Source` represents.

      See Also:
      `recursiveJoin(Source joined, Source comparison, Source parent, int comparisonRule, boolean parentsFirst, boolean parentsRestrictedToBase)`

    <!-- -->

    - #### recursiveJoin

          public final Source recursiveJoin(Source joined,
                                            java.lang.String[] comparison,
                                            Source parent,
                                            int comparisonRule,
                                            boolean parentsFirst,
                                            boolean parentsRestrictedToBase)

      Selects the specified elements of this `Source` and orders them hierarchically by the parents and their children in the hierarchy that this `Source` represents. Use this method only with the `Source` for an `MdmHierarchy` or on a subtype of such a `Source`.
      This method is the same as `recursiveJoin(Source joined, Source comparison, Source parent, int comparisonRule, boolean parentsFirst, boolean parentsRestrictedToBase)` except that the value of `comparison` is a `String` array instead of a `Source`.

      Parameters:
      `joined` - A `Source` whose elements specify the elements of this `Source` that appear in the resulting `Source`.

      `comparison` - A `String` array that specifies the values of the elements that you want to select or remove from `joined` or that specifies the parents or ancestors of elements that you want to select or remove from `joined`.

      `parent` - The `Source`, or a subtype of the `Source`, for the `MdmAttribute` returned by the `getParentAttribute` method of the `MdmHierarchy` for the hierarchy that this `Source` represents, or of which it is a subtype.

      `comparisonRule` - A constant that specifies whether this method selects from `joined` only the elements of `joined` that are in `comparison`, or that have a parent or ancestor that is in `comparison`, or selects only the elements of `joined` that are not in, or whose parent or ancestor is not in, `comparison`, and whether this method sorts the children of a parent in ascending or descending order. Specify a value for this parameter using one of the `COMPARISON_RULE` fields.

      `parentsFirst` - A flag that specifies whether parents appear before or after their children in the result when `comparisonRule` specifies sorting in ascending or descending order. Specify `true` when you want parents to appear before their children or `false` when you want parents to appear after their children.

      `parentsRestrictedToBase` - A flag that specifies whether to restrict the parents in the hierarchy to those that are in this `Source`. Specify `true` when you want to restrict the parents to the elements of this `Source` or `false` when you do not.

      Returns:
      A `Source` that has the specified elements of this `Source` ordered hierarchically by the parents and their children in the hierarchy that this `Source` represents.

      See Also:
      `recursiveJoin(Source joined, Source comparison, Source parent, int comparisonRule, boolean parentsFirst, boolean parentsRestrictedToBase)`

    <!-- -->

    - #### recursiveJoin

          public final Source recursiveJoin(Source joined,
                                            Source comparison,
                                            Source parent,
                                            int comparisonRule)

      Selects the specified elements of this `Source` and orders them hierarchically by the parents and their children in the hierarchy that this `Source` represents. Use this method only with the `Source` for an `MdmHierarchy` or on a subtype of such a `Source`.
      This method is the same as the `recursiveJoin(Source joined, Source comparison, Source parent, int comparisonRule, boolean parentsFirst, boolean parentsRestrictedToBase)` method except that the `parentsFirst`, and `parentsRestrictedToBase` parameters are set to default values. You can discover the default values by calling methods on the `RecursiveJoinDefinition` returned by the `getDefinition` method of the `Source` returned by this method.

      Parameters:
      `joined` - A `Source` whose elements specify the elements of this `Source` that appear in the resulting `Source`.

      `comparison` - A `Source` that has the elements that you want to select or remove from `joined`, or that has elements with values that specify parents or ancestors of elements that you want to select or remove from `joined`.

      `parent` - The `Source`, or a subtype of the `Source`, for the `MdmAttribute` returned by the `getParentAttribute` method of the `MdmHierarchy` for the hierarchy that this `Source` represents, or of which it is a subtype.

      `comparisonRule` - A constant that specifies whether this method selects from `joined` only the elements of `joined` that are in `comparison`, or that have a parent or ancestor that is in `comparison`, or selects only the elements of `joined` that are not in, or whose parent or ancestor is not in, `comparison`, and whether this method sorts the children of a parent in ascending or descending order. Specify a value for this parameter using one of the `COMPARISON_RULE` fields.

      Returns:
      A `Source` that has the specified elements of this `Source` ordered hierarchically by the parents and their children in the hierarchy that this `Source` represents.

      See Also:
      `recursiveJoin(Source joined, Source comparison, Source parent, int comparisonRule, boolean parentsFirst, boolean parentsRestrictedToBase)`

    <!-- -->

    - #### recursiveJoin

          public final Source recursiveJoin(Source joined,
                                            java.lang.String comparison,
                                            Source parent,
                                            int comparisonRule)

      Selects the specified elements of this `Source` and orders them hierarchically by the parents and their children in the hierarchy that this `Source` represents. Use this method only with the `Source` for an `MdmHierarchy` or on a subtype of such a `Source`.
      This method is the same as the `recursiveJoin(Source joined, Source comparison, Source parent, int comparisonRule)` method except that `comparison` is a `String` instead of a `Source`.

      Parameters:
      `joined` - A `Source` whose elements specify the elements of this `Source` that appear in the resulting `Source`.

      `comparison` - A `String` that specifies the value of the element that you want to select or remove from `joined`, or that specifies the parent or ancestor of elements that you want to select or remove from `joined`.

      `parent` - The `Source`, or a subtype of the `Source`, for the `MdmAttribute` returned by the `getParentAttribute` method of the `MdmHierarchy` for the hierarchy that this `Source` represents, or of which it is a subtype.

      `comparisonRule` - A constant that specifies whether this method selects from `joined` only the elements of `joined` that are in `comparison`, or that have a parent or ancestor that is in `comparison`, or selects only the elements of `joined` that are not in, or whose parent or ancestor is not in, `comparison`, and whether this method sorts the children of a parent in ascending or descending order. Specify a value for this parameter using one of the `COMPARISON_RULE` fields.

      Returns:
      A `Source` that has the specified elements of this `Source` ordered hierarchically by the parents and their children in the hierarchy that this `Source` represents.

      See Also:
      `recursiveJoin(Source joined, Source comparison, Source parent, int comparisonRule)`

    <!-- -->

    - #### recursiveJoin

          public final Source recursiveJoin(Source joined,
                                            java.lang.String[] comparison,
                                            Source parent,
                                            int comparisonRule)

      Selects the specified elements of this `Source` and orders them hierarchically by the parents and their children in the hierarchy that this `Source` represents. Use this method only with the `Source` for an `MdmHierarchy` or on a subtype of such a `Source`.
      This method is the same as the `recursiveJoin(Source joined, Source comparison, Source parent, int comparisonRule)` method except that the value of `comparison` is a `String` array instead of a `Source`.

      Parameters:
      `joined` - A `Source` whose elements specify the elements of this `Source` that appear in the resulting `Source`.

      `comparison` - A `String` array that specifies the values of the elements that you want to select or remove from `joined`, or that specifies the parents or ancestors of elements that you want to select or remove from `joined`.

      `parent` - The `Source`, or a subtype of the `Source`, for the `MdmAttribute` returned by the `getParentAttribute` method of the `MdmHierarchy` for the hierarchy that this `Source` represents, or of which it is a subtype.

      `comparisonRule` - A constant that specifies whether this method selects from `joined` only the elements of `joined` that are in `comparison`, or that have a parent or ancestor that is in `comparison`, or selects only the elements of `joined` that are not in, or whose parent or ancestor is not in, `comparison`, and whether this method sorts the children of a parent in ascending or descending order. Specify a value for this parameter using one of the `COMPARISON_RULE` fields.

      Returns:
      A `Source` that has the specified elements of this `Source` ordered hierarchically by the parents and their children in the hierarchy that this `Source` represents.

      See Also:
      `recursiveJoin(Source joined, Source comparison, Source parent, int comparisonRule)`

    <!-- -->

    - #### remove

          public final Source remove(BooleanSource filter)

      Removes the elements of this `Source` for which the corresponding element of the specified `BooleanSource` has a value of `true`. For a base `Source` that has `String` values, this method is equivalent to the following code where `base` is this `Source`, `dp` is the `DataProvider`, and `someString` is a `String` that is present in `base`.
           Source filter = ((StringSource) base.value()).like(someString);
           Source result = base.join(filter,
                                     dp.createConstantSource(true),
                                     Source.COMPARISON_RULE_REMOVE,
                                     false);

      Parameters:
      `filter` - A `BooleanSource` whose values are `true` for the elements of this `Source` that you do not want to have in the returned `Source`.

      Returns:
      A `Source` that has all of the elements of this `Source` for which the value of the elements of `filter` is `false`.

    <!-- -->

    - #### removeValue

          public final Source removeValue(Source value)

      Removes the elements of this `Source` that have the specified value. This method is equivalent to the following code where `base` is this `Source` and `dp` is the `DataProvider`.
           Source result = base.join(base.value(),
                                     dp.createConstantSource(value),
                                     Source.COMPARISON_RULE_REMOVE,
                                     false);

      Parameters:
      `value` - A `Source` whose elements have the values that you do not want the resulting `Source` to have.

      Returns:
      A `Source` that has all of the elements of this `Source` except for the elements specified by `value`.

    <!-- -->

    - #### removeValues

          public final Source removeValues(Source[] values)

      Removes the elements of this `Source` that have the specified `Source` objects. This method is equivalent to the following code where `base` is this `Source` and `values` is an array of `Source` objects.
           Source result = base.join(base.value(),
                                     values,
                                     Source.COMPARISON_RULE_REMOVE,
                                     false);

      Parameters:
      `values` - An array of `Source` objects that you do not want to have in the resulting `Source`.

      Returns:
      A `Source` that has all of the elements of this `Source` except for the elements specified by `values`.

    <!-- -->

    - #### removeValues

          public final Source removeValues(Source values)

      Removes the elements of this `Source` that have the specified values. This method is equivalent to the following code where `base` is this `Source`.
           Source result = base.join(base.value(),
                                     values,
                                     Source.COMPARISON_RULE_REMOVE,
                                     false);

      Parameters:
      `values` - A `Source` whose elements have the values that you do not want to have in the resulting `Source`.

      Returns:
      A `Source` that has all of the elements of this `Source` except for the elements specified by `values`.

    <!-- -->

    - #### select

          public final Source select(BooleanSource filter)

      Selects the elements of this `Source` for which the corresponding element of the specified `BooleanSource` has a value of `true`. For a base `Source` that has `String` values, this method is equivalent to the following code where `base` is this `Source`, `dp` is the `DataProvider`, and `someString` is a `String` that is present in `base`.
           Source filter = ((StringSource) base.value()).like(someString);
           Source result = base.join(filter,
                                     dp.createConstantSource(true),
                                     Source.COMPARISON_RULE_SELECT,
                                     false);

      Parameters:
      `filter` - A `BooleanSource` whose values are `true` for the elements of this `Source` that you want to have in the returned `Source`.

      Returns:
      A `Source` that has all of the elements of this `Source` for which the value of the elements of `filter` is `true`.

    <!-- -->

    - #### selectDescendants

          public final Source selectDescendants(Source comparison,
                                                Source parent)

      Selects the elements of this `Source` that are specified by `comparison` and the descendants of those elements in the hierarchy that this `Source` represents. Use this method only with the `Source` for an `MdmHierarchy` or on a subtype of such a `Source`.
      The `Source` returned by this method has an associated `RecursiveJoinDefinition` that contains information about the `Source`.

      Parameters:
      `comparison` - A `Source` that has the element or elements that you want to select from this `Source`.

      `parent` - The `Source`, or a subtype of the `Source`, for the `MdmAttribute` returned by the `getParentAttribute` method of the `MdmHierarchy` for the hierarchy that this `Source` represents, or of which it is a subtype.

      Returns:
      A `Source` that has the specified elements of this `Source` ordered hierarchically by the parents and their children in the hierarchy that this `Source` represents.

    <!-- -->

    - #### selectValue

          public final Source selectValue(Source value)

      Selects the element of this `Source` that has the specified `Source` as its value. Use this method only with a `Source` that has `Source` objects as its element values.
      This method is equivalent to the following code where `base` is this `Source` and `dp` is the `DataProvider`.

           Source result = base.join(base.value(),
                                     dp.createConstantSource(value),
                                     Source.COMPARISON_RULE_SELECT,
                                     false);

      Parameters:
      `value` - The `Source` that you want to select from this `Source</CODE.`

      `Returns:`
      `The ``Source`` that is the value of an element of this ``Source`` and that is specified by ``value`` .`

    <!-- -->

    - #### selectValues

          public final Source selectValues(Source[] values)

      Selects the elements of this `Source` that have the specified values. This method is equivalent to the following code where `base` is this `Source`.
           Source result = base.join(base.value(),
                                     values,
                                     Source.COMPARISON_RULE_SELECT,
                                     false);

      Parameters:
      `values` - An array of `Source` objects that you want to have as the values of the elements of the returned `Source`.

      Returns:
      A `Source` that has all of the elements of this `Source` that have the specified values.

    <!-- -->

    - #### selectValues

          public final Source selectValues(Source values)

      Selects the elements of this `Source` that have the specified values. This method is equivalent to the following code where `base` is this `Source`.
           Source result = base.join(base.value(),
                                     values,
                                     Source.COMPARISON_RULE_SELECT,
                                     false);

      Parameters:
      `values` - A `Source` that has elements of this `Source` that you want to have in the returned `Source`.

      Returns:
      A `Source` that has the elements of this `Source` that have the specified values.

    <!-- -->

    - #### sortAscending

          public final Source sortAscending()

      Sorts the elements of this `Source` in the ascending order of their data type. This method is equivalent to the following code where `base` is this `Source`.
           Source result = base.join(base.value(),
                                     base.getDataType(),
                                     Source.COMPARISON_RULE_ASCENDING,
                                     false);

      Returns:
      A `Source` that has the elements of this `Source` sorted in ascending order by value.

    <!-- -->

    - #### sortAscending

          public final Source sortAscending(Source sortValue)

      Selects the elements of this `Source` that are specified by the elements of `sortValue`, and orders them in the ascending order of the `sortValue` data type. This method is equivalent to the following code where `base` is this `Source`.
           Source result = base.join(sortValue,
                                     sortValue.getDataType(),
                                     Source.COMPARISON_RULE_ASCENDING,
                                     false);

      Parameters:
      `sortValue` - A `Source` whose elements, sorted in ascending order by value, you want to use to select the elements of this `Source`.

      Returns:
      A `Source` that has the elements of this `Source` that are selected by the sorted elements of the specified `Source`.

    <!-- -->

    - #### sortAscending

          public final Source sortAscending(Source sortValue,
                                            boolean nullsFirst)

      Selects the elements of this `Source` that are specified by the elements of `sortValue`, and orders them in the ascending order of the `sortValue` data type. If the value of the specified `boolean` is `true`, then elements that have a `null` value appear first. If the value of the `boolean` is `false`, then elements that have a `null` value appear last. This method is equivalent to one of the following, where `base` is this `Source`.
           Source result = base.join(sortValue,
                                     sortValue.getDataType(),
                                     Source.COMPARISON_RULE_ASCENDING_NULLS_FIRST,
                                     false);

           Source result = base.join(sortValue,
                                     sortValue.getDataType(),
                                     Source.COMPARISON_RULE_ASCENDING_NULLS_LAST,
                                     false);

      Parameters:
      `sortValue` - A `Source` whose elements, sorted in ascending order by value, you want to use to select the elements of this `Source`.

      `nullsFirst` - A `boolean` that specifies whether elements with a `null` value appear first or last.

      Returns:
      A `Source` that has the elements of this `Source` that are selected by the sorted elements of the specified `Source` with the position of `null` values as specified by nullsFirst.

    <!-- -->

    - #### sortAscendingHierarchically

          public final Source sortAscendingHierarchically(Source joined,
                                                          Source parent,
                                                          boolean parentsFirst,
                                                          boolean parentsRestrictedToBase)

      Selects the elements of this `Source` that are specified by `joined` and the descendants of those elements in the hierarchy that this `Source` represents and sorts the children of the parents in ascending order. Use this method only with the `Source` for an `MdmHierarchy` or on a subtype of such a `Source`.
      The `Source` returned by this method has an associated `RecursiveJoinDefinition` that contains information about the `Source`.

      Parameters:
      `joined` - A `Source` whose elements specify the elements of this `Source` that appear in the resulting `Source`.

      `parent` - The `Source`, or a subtype of the `Source`, for the `MdmAttribute` returned by the `getParentAttribute` method of the `MdmHierarchy` for the hierarchy that this `Source` represents, or of which it is a subtype.

      `parentsFirst` - A flag that specifies whether parents appear before or after their children in the result. Specify `true` when you want parents to appear before their children or `false` when you want parents to appear after their children.

      `parentsRestrictedToBase` - A flag that specifies whether to restrict the parents in the hierarchy to those that are in this `Source`. Specify `true` when you want to restrict the parents to the elements of this `Source` or `false` when you do not.

      Returns:
      A `Source` that has the specified elements of this `Source` ordered hierarchically by the parents and their children in the hierarchy that this `Source` represents and with the children in ascending order.

    <!-- -->

    - #### sortAscendingHierarchically

          public final Source sortAscendingHierarchically(Source joined,
                                                          Source parent)

      Selects the elements of this `Source` that are specified by `joined` and the descendants of those elements in the hierarchy that this `Source` represents and sorts the children of the parents in ascending order with the parents appearing before their children. The parents are restricted to the elements of this `Source`. Use this method only with the `Source` for an `MdmHierarchy` or on a subtype of such a `Source`.
      The `Source` returned by this method has an associated `RecursiveJoinDefinition` that contains information about the `Source`.

      Parameters:
      `joined` - A `Source` whose elements specify the elements of this `Source` that appear in the resulting `Source`.

      `parent` - The `Source`, or a subtype of the `Source`, for the `MdmAttribute` returned by the `getParentAttribute` method of the `MdmHierarchy` for the hierarchy that this `Source` represents, or of which it is a subtype.

      Returns:
      A `Source` that has the specified elements of this `Source` ordered hierarchically by the parents and their children in the hierarchy that this `Source` represents and with the children in ascending order.

      See Also:
      `sortAscendingHierarchically(Source joined, Source parent, boolean parentsFirst, boolean parentsRestrictedToBase)`

    <!-- -->

    - #### sortAscendingHierarchically

          public final Source sortAscendingHierarchically(Source parent,
                                                          boolean parentsFirst)

      Selects the elements of this `Source` and the descendants of those elements in the hierarchy that this `Source` represents and sorts the children of the parents in ascending order. The parents are restricted to the elements of this `Source`. Use this method only with the `Source` for an `MdmHierarchy` or on a subtype of such a `Source`.
      The `Source` returned by this method has an associated `RecursiveJoinDefinition` that contains information about the `Source`.

      Parameters:
      `parent` - The `Source`, or a subtype of the `Source`, for the `MdmAttribute` returned by the `getParentAttribute` method of the `MdmHierarchy` for the hierarchy that this `Source` represents, or of which it is a subtype.

      `parentsFirst` - A flag that specifies whether parents appear before or after their children in the result. Specify `true` when you want parents to appear before their children or `false` when you want parents to appear after their children.

      Returns:
      A `Source` that has the specified elements of this `Source` ordered hierarchically by the parents and their children in the hierarchy that this `Source` represents and with the children in ascending order.

      See Also:
      `sortAscendingHierarchically(Source joined, Source parent, boolean parentsFirst, boolean parentsRestrictedToBase)`

    <!-- -->

    - #### sortAscendingHierarchically

          public final Source sortAscendingHierarchically(Source parent)

      Selects the elements of this `Source` and the descendants of those elements in the hierarchy that this `Source` represents and sorts the children of the parents in ascending order with the parents appearing before the children in the result. The parents are restricted to the elements of this `Source`. Use this method only with the `Source` for an `MdmHierarchy` or on a subtype of such a `Source`.
      The `Source` returned by this method has an associated `RecursiveJoinDefinition` that contains information about the `Source`.

      Parameters:
      `parent` - The `Source`, or a subtype of the `Source`, for the `MdmAttribute` returned by the `getParentAttribute` method of the `MdmHierarchy` for the hierarchy that this `Source` represents, or of which it is a subtype.

      Returns:
      A `Source` that has the specified elements of this `Source` ordered hierarchically by the parents and their children in the hierarchy that this `Source` represents and with the children in ascending order.

      See Also:
      `sortAscendingHierarchically(Source joined, Source parent, boolean parentsFirst, boolean parentsRestrictedToBase)`

    <!-- -->

    - #### sortDescending

          public final Source sortDescending()

      Sorts the elements of this `Source` in the descending order of their values. This method is equivalent to the following code where `base` is this `Source`.
           Source result = base.join(base.value(),
                                     base.getDataType(),
                                     Source.COMPARISON_RULE_DESCENDING,
                                     false);

      Returns:
      A `Source` that has the elements of this `Source` sorted in descending order by value.

    <!-- -->

    - #### sortDescending

          public final Source sortDescending(Source sortValue)

      Selects the elements of this `Source` that are specified by the elements of `sortValue`, and orders them in the descending order of the `sortValue` data type. This method is equivalent to the following code where `base` is this `Source`.
           Source result = base.join(sortValue,
                                     sortValue.getDataType(),
                                     Source.COMPARISON_RULE_DESCENDING,
                                     false);

      Parameters:
      `sortValue` - A `Source` whose elements, sorted in descending order by value, you want to use to select the elements of this `Source`.

      Returns:
      A `Source` that has the elements of this `Source` that are selected by the sorted elements of the specified `Source`.

    <!-- -->

    - #### sortDescending

          public final Source sortDescending(Source sortValue,
                                             boolean nullsFirst)

      Selects the elements of this `Source` that are specified by the elements of `sortValue`, and orders them in the descending order of the `sortValue` data type. If the value of the specified `boolean` is `true`, then elements that have a `null` value appear first. If the value of the `boolean` is `false`, then elements that have a `null` value appear last. This method is equivalent to one of the following, where `base` is this `Source`.
           Source result = base.join(sortValue,
                                     sortValue.getDataType(),
                                     Source.COMPARISON_RULE_DESCENDING_NULLS_FIRST,
                                     false);

           Source result = base.join(sortValue,
                                     sortValue.getDataType(),
                                     Source.COMPARISON_RULE_DESCENDING_NULLS_LAST,
                                     false);

      Parameters:
      `sortValue` - A `Source` whose elements, sorted in ascending order by value, you want to use to select the elements of this `Source`.

      `nullsFirst` - A `boolean` that specifies whether elements with a `null` value appear first or last.

      Returns:
      A `Source` that has the elements of this `Source` that are selected by the sorted elements of the specified `Source` with the position of `null` values as specified by nullsFirst.

    <!-- -->

    - #### sortDescendingHierarchically

          public final Source sortDescendingHierarchically(Source joined,
                                                           Source parent,
                                                           boolean parentsFirst,
                                                           boolean parentsRestrictedToBase)

      Selects the elements of this `Source` that are specified by `joined` and the descendants of those elements in the hierarchy that this `Source` represents and sorts the children of the parents in descending order. Use this method only with the `Source` for an `MdmHierarchy` or on a subtype of such a `Source`.
      The `Source` returned by this method has an associated `RecursiveJoinDefinition` that contains information about the `Source`.

      Parameters:
      `joined` - A `Source` whose elements specify the elements of this `Source` that appear in the resulting `Source`.

      `parent` - The `Source`, or a subtype of the `Source`, for the `MdmAttribute` returned by the `getParentAttribute` method of the `MdmHierarchy` for the hierarchy that this `Source` represents, or of which it is a subtype.

      `parentsFirst` - A flag that specifies whether parents appear before or after their children in the result. Specify `true` when you want parents to appear before their children or `false` when you want parents to appear after their children.

      `parentsRestrictedToBase` - A flag that specifies whether to restrict the parents in the hierarchy to those that are in this `Source`. Specify `true` when you want to restrict the parents to the elements of this `Source` or `false` when you do not.

      Returns:
      A `Source` that has the specified elements of this `Source` ordered hierarchically by the parents and their children in the hierarchy that this `Source` represents and with the children in descending order.

      See Also:
      `recursiveJoin(Source joined, Source comparison, Source parent, int comparisonRule, boolean parentsFirst, boolean parentsRestrictedToBase)`

    <!-- -->

    - #### sortDescendingHierarchically

          public final Source sortDescendingHierarchically(Source joined,
                                                           Source parent)

      Selects the elements of this `Source` that are specified by `joined` and the descendants of those elements in the hierarchy that this `Source` represents and sorts the children of the parents in descending order with the parents appearing before their children. The parents are restricted to the elements of this `Source`. Use this method only with the `Source` for an `MdmHierarchy` or on a subtype of such a `Source`.
      The `Source` returned by this method has an associated `RecursiveJoinDefinition` that contains information about the `Source`.

      Parameters:
      `joined` - A `Source` whose elements specify the elements of this `Source` that appear in the resulting `Source`.

      `parent` - The `Source`, or a subtype of the `Source`, for the `MdmAttribute` returned by the `getParentAttribute` method of the `MdmHierarchy` for the hierarchy that this `Source` represents, or of which it is a subtype.

      Returns:
      A `Source` that has the specified elements of this `Source` ordered hierarchically by the parents and their children in the hierarchy that this `Source` represents and with the children in descending order.

      See Also:
      `sortDescendingHierarchically(Source joined, Source parent, boolean parentsFirst, boolean parentsRestrictedToBase)`

    <!-- -->

    - #### sortDescendingHierarchically

          public final Source sortDescendingHierarchically(Source parent,
                                                           boolean parentsFirst)

      Selects the elements of this `Source` and the descendants of those elements in the hierarchy that this `Source` represents and sorts the children of the parents in descending order. The parents are restricted to the elements of this `Source`. Use this method only with the `Source` for an `MdmHierarchy` or on a subtype of such a `Source`.
      The `Source` returned by this method has an associated `RecursiveJoinDefinition` that contains information about the `Source`.

      Parameters:
      `parent` - The `Source`, or a subtype of the `Source`, for the `MdmAttribute` returned by the `getParentAttribute` method of the `MdmHierarchy` for the hierarchy that this `Source` represents, or of which it is a subtype.

      `parentsFirst` - A flag that specifies whether parents appear before or after their children in the result. Specify `true` when you want parents to appear before their children or `false` when you want parents to appear after their children.

      Returns:
      A `Source` that has the specified elements of this `Source` ordered hierarchically by the parents and their children in the hierarchy that this `Source` represents and with the children in descending order.

      See Also:
      `sortDescendingHierarchically(Source joined, Source parent, boolean parentsFirst, boolean parentsRestrictedToBase)`

    <!-- -->

    - #### sortDescendingHierarchically

          public final Source sortDescendingHierarchically(Source parent)

      Selects the elements of this `Source` and the descendants of those elements in the hierarchy that this `Source` represents and sorts the children of the parents in descending order with the parents appearing before the children in the result. The parents are restricted to the elements of this `Source`. Use this method only with the `Source` for an `MdmHierarchy` or on a subtype of such a `Source`.
      The `Source` returned by this method has an associated `RecursiveJoinDefinition` that contains information about the `Source`.

      Parameters:
      `parent` - The `Source`, or a subtype of the `Source`, for the `MdmAttribute` returned by the `getParentAttribute` method of the `MdmHierarchy` for the hierarchy that this `Source` represents, or of which it is a subtype.

      Returns:
      A `Source` that has the specified elements of this `Source` ordered hierarchically by the parents and their children in the hierarchy that this `Source` represents and with the children in descending order.

      See Also:
      `sortDescendingHierarchically(Source joined, Source parent, boolean parentsFirst, boolean parentsRestrictedToBase)`

    <!-- -->

    - #### toDoubleSource

          public final NumberSource toDoubleSource()

      Converts the values of the elements of this `Source` to the Java `double` data type.
      Returns:
      A `Source` that has the same elements as this `Source`, but whose type is the fundamental Double `Source`.

    <!-- -->

    - #### toFloatSource

          public final NumberSource toFloatSource()

      Converts the values of the elements of this `Source` to the Java `float` data type.
      Returns:
      A `Source` that has the same elements as this `Source`, but whose type Float `Source`.

    <!-- -->

    - #### toIntegerSource

          public final NumberSource toIntegerSource()

      Converts the values of the elements of this `Source` to the Java `int` data type.
      Returns:
      A `Source` that has the same elements as this `Source`, but whose type is the fundamental Integer `Source`.

    <!-- -->

    - #### toShortSource

          public final NumberSource toShortSource()

      Converts the values of the elements of this `Source` to the Java `short` data type.
      Returns:
      A `Source` that has the same elements as this `Source`, but whose type is the fundamental Short `Source`.

    <!-- -->

    - #### toStringSource

          public StringSource toStringSource()

      Converts the values of the elements of this `Source` to Java `String` objects.
      Returns:
      A `Source` that has the same elements as this `Source`, but whose type is the fundamental String `Source`.

    <!-- -->

    - #### value

          public final Source value()

      Produces a `Source` that has the elements of this `Source` and that has this `Source` as an input. Use this method when you want to produce a `Source` that has a subset of the elements of the `Source` on which you call it. For examples, see the `selectValues` and `removeValues` methods.
      Returns:
      A `Source` that has the elements of this `Source` and that has this `Source` as an input.

    <!-- -->

    - #### value

          public final Source value(Source input)

      Produces a `Source` that has the same elements as this `Source` and that has the specified `Source` as an input.
      Parameters:
      `input` - The `Source` that you want as an input to the returned `Source`.

      Returns:
      A `Source` that has the same elements as this `Source` and that has the specified `Source` as an input.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](ServerVersionException.md)
- [Next Class](SourceDefinition.md)

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
