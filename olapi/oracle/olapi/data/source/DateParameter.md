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

- [Prev Class](DataProviderMismatchException.md)
- [Next Class](DateSource.md)

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

## Class DateParameter

- java.lang.Object

- - [oracle.olapi.data.source.Parameter](Parameter.md)

  - - oracle.olapi.data.source.DateParameter

<!-- -->

-

  ------------------------------------------------------------------------



      public class DateParameter
      extends Parameter

  A `Parameter` that specifies a `Date` value that you use in creating a query. After creating the query, you can change the value of the `DateParameter` and thereby change the selection of dimension or measure elements that the query represents.
  The `createSource` method creates a parameterized `DateSource`. You use the parameterized `DateSource` as a parameter to a method that selects one or more elements of another `Source` and produces a derived `Source`. You can then create a `Cursor` for the `Source` to retrieve the results of the query.

  You can change the selection of elements that the derived `Source` represents by changing the value of the `DateParameter` with one of its `setValue` methods. The `Cursor` for the query `Source` then has the values of the new selection. You do not need to create a new `Cursor`. You can instead just set the position of the existing `Cursor` to its first position and get the values for the new selection from the `Cursor`.

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                                        |
    |--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `DateParameter``(`[`DataProvider`](DataProvider.md)` dataProvider, java.util.Date initialValue)`<br>Creates a `DateParameter` that has the specified `Date` value. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                                                                                        |
    |--------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Object` | `acceptVisitor``(`[`ParameterVisitor`](ParameterVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitDateParameter` method of the specified `ParameterVisitor` and passes that method this `DateParameter` and the specified context `Object`. |
    | `java.util.Date`   | `getValue``()`<br>Gets the value of this `DateParameter`.                                                                                                                                                                                                     |
    | `java.lang.Object` | `getValueObject``()`<br>Gets the value of this `DateParameter` as an `Object`.                                                                                                                                                                                |
    | `void`             | `setValue``(java.util.Date value)`<br>Sets the value of this `DateParameter` to the specified `Date`.                                                                                                                                                         |

    - ### Methods inherited from class oracle.olapi.data.source.[Parameter](Parameter.md)

      [`createSource`](Parameter.md)`, `[`getDataProvider`](Parameter.md)`, `[`getID`](Parameter.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### DateParameter

          public DateParameter(DataProvider dataProvider,
                               java.util.Date initialValue)

      Creates a `DateParameter` that has the specified `Date` value.
      Parameters:
      `dataProvider` - The `DataProvider` that you are using.

      `initialValue` - The `Date` value that you want this `StringParameter` to have.

  <!-- -->

  - ### Method Detail

    - #### acceptVisitor

          public final java.lang.Object acceptVisitor(ParameterVisitor visitor,
                                                      java.lang.Object context)

      Calls the `visitDateParameter` method of the specified `ParameterVisitor` and passes that method this `DateParameter` and the specified context `Object`.
      Specified by:
      [`acceptVisitor`](Parameter.md) in class [`Parameter`](Parameter.md)

      Parameters:
      `visitor` - An instance a class derived from the `ParameterVisitor` class.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitDateParameter` method of the specified `ParameterVisitor`.

    <!-- -->

    - #### getValue

          public final java.util.Date getValue()

      Gets the value of this `DateParameter`.
      Returns:
      The value of this `DateParameter`.

    <!-- -->

    - #### getValueObject

          public final java.lang.Object getValueObject()

      Gets the value of this `DateParameter` as an `Object`.
      Specified by:
      [`getValueObject`](Parameter.md) in class [`Parameter`](Parameter.md)

      Returns:
      The value of this `DateParameter` as an `Object`.

    <!-- -->

    - #### setValue

          public final void setValue(java.util.Date value)

      Sets the value of this `DateParameter` to the specified `Date`.
      Parameters:
      `value` - A `Date` that you want this `DateParameter` to have as its value.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](DataProviderMismatchException.md)
- [Next Class](DateSource.md)

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
