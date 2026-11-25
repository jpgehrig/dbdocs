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

- Prev Class
- [Next Class](Cursor.md)

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

## Interface CompoundCursor

- All Superinterfaces:
  [Cursor](Cursor.md)

  ------------------------------------------------------------------------



      public interface CompoundCursor
      extends Cursor

  A `Cursor` for a `Source` that has outputs. A `CompoundCursor` has a child base `ValueCursor`, the elements of which have the values specified by the `Source`. A `CompoundCursor` also has one or more outputs, one for each output of the `Source`. The outputs of the `CompoundCursor` are child `CompoundCursor` or `ValueCursor` objects.
  The order of the outputs of a `CompoundCursor` is determined by the order of the outputs of the `Source`. The value of the base `ValueCursor` at any position in a `CompoundCursor` is determined by the set of the values of the elements of the outputs specified by that position.

  For example, in the following code `unitPrice` is the `Source` for an `MdmBaseMeasure`, and `prodHier` and `timeHier` are `StringSource` objects for the default `MdmLevelHierarchy` objects for the Product and Time dimensions, which are the dimensions of the measure.

       Source prodSel = prodHier.selectValues(new String[]
                                         {"PRODUCT_PRIMARY::ITEM::INT CD ROM",
                                          "PRODUCT_PRIMARY::ITEM::INT CD USB",
                                          "PRODUCT_PRIMARY::ITEM::INT RW DVD",
                                          "PRODUCT_PRIMARY::ITEM::INT 8X DVD"});
       Source timeSel = timeHier.selectValues(new String[]
                                             {"CALENDAR_YEAR::MONTH::2003.06",
                                              "CALENDAR_YEAR::MONTH::2004.06"});
       Source productsPriceForMonth = unitPrice.join(prodSel).join(timeSel);

  The `productsPriceForMonth` `Source` specifies the price of the selected products for the selected months. It has the `unitPrice` values as element values, and it has `prodSel` and `timeSel` as outputs. The following code creates a `CursorManager` and a `Cursor` for `productsPriceForMonth`. The `dp` object is the `DataProvider`.
       CursorManager cursorManager = dp.createCursorManager(productsPriceForMonth);
       Cursor result = cursorManager.createCursor

  Because the `productsPriceForDay` has outputs, `result` is a `CompoundCursor`. The base `ValueCursor` has the values from `unitPrice` that are specified by the set of the values of the outputs. The outputs of the `CompoundCursor` are two `ValueCursor` objects. The first output has the element values of `timesSel` and the second output has the element values of `productsSel`.
  The following table is a display of the values of `result`, formatted into columns. The table shows the current value of each `ValueCursor` at each position of the `CompoundCursor`. The left column has the values of the `ValueCursor` for the first output, the middle column has values of the `ValueCursor` for the second output, and right column has the values of the base `ValueCursor`. The display contains only the local values of the dimensions, not the three-part unique values.

          2003.06   INT 8X DVD       NA
          2003.06   INT CD ROM   121.84
          2003.06   INT CD USB    58.37
          2003.06   INT RW DVD   161.00
          2004.06   INT 8X DVD       NA
          2004.06   INT CD ROM   123.68
          2004.06   INT CD USB    46.76
          2004.06   INT RW DVD   167.72

  The following table shows the positions of the `CompoundCursor` and the child `Cursor` objects and the value at each `ValueCursor` position. The left column has the positions of the parent `CompoundCursor`. The second column from the left has the positions of the `ValueCursor` for `timesSel` and the values at those positions. The third column from the left has the positions of the `ValueCursor` for `productsSel` and the values at those positions. The right column has the positions of the base `ValueCursor` and the values at those positions.
       CompoundCursor      Output 1               Output 2         Base ValueCursor
       --------------  ------------------   ---------------------  -----------------
          Position     Position    Value    Position   Value       Position  Value
          --------     --------   -------   --------   ----------  --------  ------
             1            1       2003.06       1      INT 8X DVD       1        NA
             2            1       2003.06       2      INT CD ROM       1    121.84
             3            1       2003.06       3      INT CD USB       1     58.37
             4            1       2003.06       4      INT RW DVD       1    161.00
             5            2       2004.06       1      INT 8X DVD       1        NA
             6            2       2004.06       2      INT CD ROM       1    123.68
             7            2       2004.06       3      INT CD USB       1     46.76
             8            2       2004.06       4      INT RW DVD       1    167.72

  In the example, each set of output values specifies only one unit price value. The base `ValueCursor` therefore has only one position for each set of output values.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface oracle.olapi.data.cursor.[Cursor](Cursor.md)

      [`FETCH_SIZE_NOT_SPECIFIED`](Cursor.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type               | Method and Description                                                       |
    |---------------------------------|------------------------------------------------------------------------------|
    | `java.util.List`                | `getOutputs``()`<br>Gets the outputs of the `CompoundCursor`.                |
    | [`ValueCursor`](ValueCursor.md) | `getValueCursor``()`<br>Gets the base `ValueCursor` of the `CompoundCursor`. |

    - ### Methods inherited from interface oracle.olapi.data.cursor.[Cursor](Cursor.md)

      [`getExtent`](Cursor.md)`, `[`getFetchSize`](Cursor.md)`, `[`getParentEnd`](Cursor.md)`, `[`getParentStart`](Cursor.md)`, `[`getPosition`](Cursor.md)`, `[`getSource`](Cursor.md)`, , `[`setFetchSize`](Cursor.md)`, `[`setPosition`](Cursor.md)

<!-- -->

- - ### Method Detail

    - #### getValueCursor

          ValueCursor getValueCursor()

      Gets the base `ValueCursor` of the `CompoundCursor`. The base `ValueCursor` has the values of the `Source` for the `CompoundCursor`.
      Returns:
      The base `ValueCursor` of the `CompoundCursor`.

    <!-- -->

    - #### getOutputs

          java.util.List getOutputs()

      Gets the outputs of the `CompoundCursor`. An output is a `ValueCursor` or a `CompoundCursor`. A `CompoundCursor` has one output for each output of the associated `Source`.
      Returns:
      A `List` that contains the outputs of this `CompoundCursor`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- Prev Class
- [Next Class](Cursor.md)

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
