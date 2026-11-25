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

- [Prev Class](Model.md)
- [Next Class](NumberSource.md)

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

## Class NumberParameter

- java.lang.Object

- - [oracle.olapi.data.source.Parameter](Parameter.md)

  - - oracle.olapi.data.source.NumberParameter

<!-- -->

-

  ------------------------------------------------------------------------



      public class NumberParameter
      extends Parameter

  A `Parameter` that specifies a number value that you use in creating a query. After creating the query, you can change the value of the `NumberParameter` and thereby change the selection of dimension or measure elements that the query represents.
  The `createSource` method creates a parameterized `NumberSource`. You use the parameterized `NumberSource` as a parameter to a method that selects one or more elements of another `Source` and produces a derived `Source`. You can then create a `Cursor` for the `Source` to retrieve the results of the query.

  You can change the selection of elements that the derived `Source` represents by changing the value of the `NumberParameter` with the appropriate `setValue` method. The `Cursor` for the query `Source` then has the values of the new selection. You do not need to create a new `Cursor`. You can instead just set the position of the existing `Cursor` to its first position and get the values for the new selection from the `Cursor`.

  The following example creates a `NumberParameter` with the value `1000` and uses it to create a parameterized `NumberSource`. The `dp` object is the `DataProvider`. The example joins `Source` objects for a measure of product units sold, and for single selections from the default hierarchies of three of the four dimensions of the measure. The example then produces a selection of product values, `paramProdSel`, for which the number of units sold is greater than the value of the `NumberParameter`. It joins `paramProdSel` to the `Source` for the short description attribute for the product dimension, which produces the `results` `Source`. Finally, the example creates a `Cursor` for `results`.

       NumberParameter numParam = new NumberParameter(dp, 1000);
       NumberSource numParamSrc = (NumberSource) numParam.createSource();
       NumberSource qualifiedUnits =
                (NumberSource) units.join(timeHier, "CALENDAR_YEAR::YEAR::CY2001")
                                    .join(custHier, "SHIPMENTS::REGION::EMEA")
                                    .join(chanHier,"CHANNEL_PRIMARY::CHANNEL::INT");
       Source paramProdSel = prodHier.select(qualifiedUnits.gt(numParamSrc));
       Source results = prodShortDescr.join(paramProdSel);

       dp.getTransactionProvider().commitCurrentTransaction();

       CursorManager  cursorManager = dp.createCursorManager(results);
       Cursor resultsCursor = cursorManager.createCursor();

  The following table displays the values of `resultsCursor` and adds column heading.

       Product                                Short Description
       ------------------------------------   -----------------
       PRODUCT_PRIMARY::TOTAL_PRODUCT::TOTAL  Total Product
       PRODUCT_PRIMARY::CLASS::HRD            Hardware
       PRODUCT_PRIMARY::FAMILY::DISK          CD/DVD
       PRODUCT_PRIMARY::FAMILY::MOD           Modems/Fax
       PRODUCT_PRIMARY::CLASS::SFT            Software/Other
       PRODUCT_PRIMARY::FAMILY::ACC           Accessories
       PRODUCT_PRIMARY::FAMILY::OS            Operating Systems

  The following continuation of the example sets the value of the `NumberParameter` to `1500`. It then sets the position of `resultsCursor` back to the first position of the `Cursor`.

       numParam.setValue(1500);
       // Reset the Cursor position to 1
       resultsCursor.setPosition(1);

  The following table displays the values that `resultsCursor` now contains and adds column headings.

       Product                                Short Description
       ------------------------------------   -----------------
       PRODUCT_PRIMARY::TOTAL_PRODUCT::TOTAL  Total Product
       PRODUCT_PRIMARY::CLASS::HRD            Hardware
       PRODUCT_PRIMARY::CLASS::SFT            Software/Other
       PRODUCT_PRIMARY::FAMILY::ACC           Accessories

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                                  |
    |------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `NumberParameter``(`[`DataProvider`](DataProvider.md)` dataProvider, double initialValue)`<br>Creates a `NumberParameter` that has the specified `double` value.             |
    | `NumberParameter``(`[`DataProvider`](DataProvider.md)` dataProvider, java.lang.Double initialValue)`<br>Creates a `NumberParameter` that has the specified `Double` value.   |
    | `NumberParameter``(`[`DataProvider`](DataProvider.md)` dataProvider, float initialValue)`<br>Creates a `NumberParameter` that has the specified `float` value.               |
    | `NumberParameter``(`[`DataProvider`](DataProvider.md)` dataProvider, java.lang.Float initialValue)`<br>Creates a `NumberParameter` that has the specified `Float` value.     |
    | `NumberParameter``(`[`DataProvider`](DataProvider.md)` dataProvider, int initialValue)`<br>Creates a `NumberParameter` that has the specified integer value.                 |
    | `NumberParameter``(`[`DataProvider`](DataProvider.md)` dataProvider, java.lang.Integer initialValue)`<br>Creates a `NumberParameter` that has the specified `Integer` value. |
    | `NumberParameter``(`[`DataProvider`](DataProvider.md)` dataProvider, long initialValue)`<br>Creates a `NumberParameter` that has the specified `long` value.                 |
    | `NumberParameter``(`[`DataProvider`](DataProvider.md)` dataProvider, java.lang.Long initialValue)`<br>Creates a `NumberParameter` that has the specified `Long` value.       |
    | `NumberParameter``(`[`DataProvider`](DataProvider.md)` dataProvider, short initialValue)`<br>Creates a `NumberParameter` that has the specified `short` value.               |
    | `NumberParameter``(`[`DataProvider`](DataProvider.md)` dataProvider, java.lang.Short initialValue)`<br>Creates a `NumberParameter` that has the specified `Short` value.     |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                                                                                            |
    |--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object` | `acceptVisitor``(`[`ParameterVisitor`](ParameterVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitNumberParameter` method of the specified `ParameterVisitor` and passes that method this `NumberParameter` and the specified context `Object`. |
    | `double`           | `getDoubleValue``()`<br>Gets the value of this `NumberParameter` as a `double`.                                                                                                                                                                                   |
    | `float`            | `getFloatValue``()`<br>Gets the value of this `NumberParameter` as a `float`.                                                                                                                                                                                     |
    | `int`              | `getIntValue``()`<br>Gets the value of this `NumberParameter` as an integer.                                                                                                                                                                                      |
    | `long`             | `getLongValue``()`<br>Gets the value of this `NumberParameter` as a `long`.                                                                                                                                                                                       |
    | `short`            | `getShortValue``()`<br>Gets the value of this `NumberParameter` as a `short`.                                                                                                                                                                                     |
    | `java.lang.Number` | `getValue``()`<br>Gets the value of this `NumberParameter` as an OLAP API Number.                                                                                                                                                                                 |
    | `java.lang.Object` | `getValueObject``()`<br>Gets the value of this `NumberParameter` as an `Object`.                                                                                                                                                                                  |
    | `void`             | `setValue``(double value)`<br>Sets the value of this `NumberParameter` to the specified `double`.                                                                                                                                                                 |
    | `void`             | `setValue``(java.lang.Double value)`<br>Sets the value of this `NumberParameter` to the specified `Double`.                                                                                                                                                       |
    | `void`             | `setValue``(float value)`<br>Sets the value of this `NumberParameter` to the specified `float`.                                                                                                                                                                   |
    | `void`             | `setValue``(java.lang.Float value)`<br>Sets the value of this `NumberParameter` to the specified `Float`.                                                                                                                                                         |
    | `void`             | `setValue``(int value)`<br>Sets the value of this `NumberParameter` to the specified integer.                                                                                                                                                                     |
    | `void`             | `setValue``(java.lang.Integer value)`<br>Sets the value of this `NumberParameter` to the specified `Integer`.                                                                                                                                                     |
    | `void`             | `setValue``(long value)`<br>Sets the value of this `NumberParameter` to the specified `long`.                                                                                                                                                                     |
    | `void`             | `setValue``(java.lang.Long value)`<br>Sets the value of this `NumberParameter` to the specified `Long`.                                                                                                                                                           |
    | `void`             | `setValue``(short value)`<br>Sets the value of this `NumberParameter` to the specified `short`.                                                                                                                                                                   |
    | `void`             | `setValue``(java.lang.Short value)`<br>Sets the value of this `NumberParameter` to the specified `Short`.                                                                                                                                                         |

    - ### Methods inherited from class oracle.olapi.data.source.[Parameter](Parameter.md)

      [`createSource`](Parameter.md)`, `[`getDataProvider`](Parameter.md)`, `[`getID`](Parameter.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### NumberParameter

          public NumberParameter(DataProvider dataProvider,
                                 java.lang.Short initialValue)

      Creates a `NumberParameter` that has the specified `Short` value.
      Parameters:
      `dataProvider` - The `DataProvider` that you are using.

      `initialValue` - The `Short` that you want this `NumberParameter` to have.

    <!-- -->

    - #### NumberParameter

          public NumberParameter(DataProvider dataProvider,
                                 short initialValue)

      Creates a `NumberParameter` that has the specified `short` value.
      Parameters:
      `dataProvider` - The `DataProvider` that you are using.

      `initialValue` - The `short` that you want this `NumberParameter` to have.

    <!-- -->

    - #### NumberParameter

          public NumberParameter(DataProvider dataProvider,
                                 java.lang.Integer initialValue)

      Creates a `NumberParameter` that has the specified `Integer` value.
      Parameters:
      `dataProvider` - The `DataProvider` that you are using.

      `initialValue` - The `Integer` that you want this `NumberParameter` to have.

    <!-- -->

    - #### NumberParameter

          public NumberParameter(DataProvider dataProvider,
                                 int initialValue)

      Creates a `NumberParameter` that has the specified integer value.
      Parameters:
      `dataProvider` - The `DataProvider` that you are using.

      `initialValue` - The `int` that you want this `NumberParameter` to have.

    <!-- -->

    - #### NumberParameter

          public NumberParameter(DataProvider dataProvider,
                                 java.lang.Long initialValue)

      Creates a `NumberParameter` that has the specified `Long` value.
      Parameters:
      `dataProvider` - The `DataProvider` that you are using.

      `initialValue` - The `Long` that you want this `NumberParameter` to have.

    <!-- -->

    - #### NumberParameter

          public NumberParameter(DataProvider dataProvider,
                                 long initialValue)

      Creates a `NumberParameter` that has the specified `long` value.
      Parameters:
      `dataProvider` - The `DataProvider` that you are using.

      `initialValue` - The `long` that you want this `NumberParameter` to have.

    <!-- -->

    - #### NumberParameter

          public NumberParameter(DataProvider dataProvider,
                                 java.lang.Float initialValue)

      Creates a `NumberParameter` that has the specified `Float` value.
      Parameters:
      `dataProvider` - The `DataProvider` that you are using.

      `initialValue` - The `Float` that you want this `NumberParameter` to have.

    <!-- -->

    - #### NumberParameter

          public NumberParameter(DataProvider dataProvider,
                                 float initialValue)

      Creates a `NumberParameter` that has the specified `float` value.
      Parameters:
      `dataProvider` - The `DataProvider` that you are using.

      `initialValue` - The `float` that you want this `NumberParameter` to have.

    <!-- -->

    - #### NumberParameter

          public NumberParameter(DataProvider dataProvider,
                                 java.lang.Double initialValue)

      Creates a `NumberParameter` that has the specified `Double` value.
      Parameters:
      `dataProvider` - The `DataProvider` that you are using.

      `initialValue` - The `Double` that you want this `NumberParameter` to have.

    <!-- -->

    - #### NumberParameter

          public NumberParameter(DataProvider dataProvider,
                                 double initialValue)

      Creates a `NumberParameter` that has the specified `double` value.
      Parameters:
      `dataProvider` - The `DataProvider` that you are using.

      `initialValue` - The `double` that you want this `NumberParameter` to have.

  <!-- -->

  - ### Method Detail

    - #### acceptVisitor

          public final java.lang.Object acceptVisitor(ParameterVisitor visitor,
                                                      java.lang.Object context)

      Calls the `visitNumberParameter` method of the specified `ParameterVisitor` and passes that method this `NumberParameter` and the specified context `Object`.
      Specified by:
      [`acceptVisitor`](Parameter.md) in class [`Parameter`](Parameter.md)

      Parameters:
      `visitor` - An instance a class derived from the `ParameterVisitor` class.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitNumberParameter` method of the specified `ParameterVisitor`.

    <!-- -->

    - #### getShortValue

          public final short getShortValue()

      Gets the value of this `NumberParameter` as a `short`.
      Returns:
      The value of this `NumberParameter` as a `short`.

    <!-- -->

    - #### getIntValue

          public final int getIntValue()

      Gets the value of this `NumberParameter` as an integer.
      Returns:
      The value of this `NumberParameter` as a `int`.

    <!-- -->

    - #### getLongValue

          public final long getLongValue()

      Gets the value of this `NumberParameter` as a `long`.
      Returns:
      The value of this `NumberParameter` as a `long`.

    <!-- -->

    - #### getFloatValue

          public final float getFloatValue()

      Gets the value of this `NumberParameter` as a `float`.
      Returns:
      The value of this `NumberParameter` as a `float`.

    <!-- -->

    - #### getDoubleValue

          public final double getDoubleValue()

      Gets the value of this `NumberParameter` as a `double`.
      Returns:
      The value of this `NumberParameter` as a `double`.

    <!-- -->

    - #### getValue

          public final java.lang.Number getValue()

      Gets the value of this `NumberParameter` as an OLAP API Number.
      Returns:
      The value of this `NumberParameter` as an OLAP API Number.

    <!-- -->

    - #### getValueObject

          public final java.lang.Object getValueObject()

      Gets the value of this `NumberParameter` as an `Object`.
      Specified by:
      [`getValueObject`](Parameter.md) in class [`Parameter`](Parameter.md)

      Returns:
      The value of this `NumberParameter` as an `Object`.

    <!-- -->

    - #### setValue

          public final void setValue(java.lang.Short value)

      Sets the value of this `NumberParameter` to the specified `Short`.
      Parameters:
      `value` - The `Short` that you want this `NumberParameter` to have.

    <!-- -->

    - #### setValue

          public final void setValue(short value)

      Sets the value of this `NumberParameter` to the specified `short`.
      Parameters:
      `value` - The `short` that you want this `NumberParameter` to have.

    <!-- -->

    - #### setValue

          public final void setValue(java.lang.Integer value)

      Sets the value of this `NumberParameter` to the specified `Integer`.
      Parameters:
      `value` - The `Integer` that you want this `NumberParameter` to have.

    <!-- -->

    - #### setValue

          public final void setValue(int value)

      Sets the value of this `NumberParameter` to the specified integer.
      Parameters:
      `value` - The `int` that you want this `NumberParameter` to have.

    <!-- -->

    - #### setValue

          public final void setValue(java.lang.Long value)

      Sets the value of this `NumberParameter` to the specified `Long`.
      Parameters:
      `value` - The `Long` that you want this `NumberParameter` to have.

    <!-- -->

    - #### setValue

          public final void setValue(long value)

      Sets the value of this `NumberParameter` to the specified `long`.
      Parameters:
      `value` - The `long` that you want this `NumberParameter` to have.

    <!-- -->

    - #### setValue

          public final void setValue(java.lang.Float value)

      Sets the value of this `NumberParameter` to the specified `Float`.
      Parameters:
      `value` - The `Float` that you want this `NumberParameter` to have.

    <!-- -->

    - #### setValue

          public final void setValue(float value)

      Sets the value of this `NumberParameter` to the specified `float`.
      Parameters:
      `value` - The `float` that you want this `NumberParameter` to have.

    <!-- -->

    - #### setValue

          public final void setValue(java.lang.Double value)

      Sets the value of this `NumberParameter` to the specified `Double`.
      Parameters:
      `value` - The `Double` that you want this `NumberParameter` to have.

    <!-- -->

    - #### setValue

          public final void setValue(double value)

      Sets the value of this `NumberParameter` to the specified `double`.
      Parameters:
      `value` - The `double` that you want this `NumberParameter` to have.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](Model.md)
- [Next Class](NumberSource.md)

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
