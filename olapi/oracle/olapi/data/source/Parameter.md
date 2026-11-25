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

- [Prev Class](NumberSource.md)
- [Next Class](ParameterVisitor.md)

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

## Class Parameter

- java.lang.Object

- - oracle.olapi.data.source.Parameter

<!-- -->

- Direct Known Subclasses:
  [BooleanParameter](BooleanParameter.md), [DateParameter](DateParameter.md), [NumberParameter](NumberParameter.md), [StringParameter](StringParameter.md)

  ------------------------------------------------------------------------



      public abstract class Parameter
      extends java.lang.Object

  An object that specifies a value that you use in creating a query. After creating the query, you can change the value of the `Parameter` and thereby change the selection of dimension or measure elements that the query represents.
  The `createSource` method of a `Parameter` creates a parameterized `Source`. You then use the parameterized `Source` as a parameter to a method that selects one or more elements of another `Source` and produces a derived `Source`. You can create a `Cursor` for the `Source` to retrieve the results of the query.

  You can change the selection of elements that the derived `Source` represents with the `setValue` method of a concrete subclass of `Parameter`. The `Cursor` for the query `Source` then has the values of the new selection. You do not need to create a new `Cursor`. You can instead just get the values for the new selection from the existing `Cursor`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                 | Method and Description                                                                                                                                                                                                                          |
    |-----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `abstract java.lang.Object`       | `acceptVisitor``(`[`ParameterVisitor`](ParameterVisitor.md)` visitor, java.lang.Object context)`<br>Calls the appropriate method of the specified `ParameterVisitor` and passes that method the `Parameter` and the specified context `Object`. |
    | [`Source`](Source.md)             | `createSource``()`<br>Creates a `Source` of the appropriate data type that contains the value specified for the `Parameter`.                                                                                                                    |
    | [`DataProvider`](DataProvider.md) | `getDataProvider``()`<br>Gets the `DataProvider` for this `Parameter`.                                                                                                                                                                          |
    | `java.lang.String`                | `getID``()`<br>Gets a `String` that uniquely identifies this `Parameter` during this connection.                                                                                                                                                |
    | `abstract java.lang.Object`       | `getValueObject``()`<br>Gets an `Object` that contains the value for this `Parameter`.                                                                                                                                                          |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### acceptVisitor

          public abstract java.lang.Object acceptVisitor(ParameterVisitor visitor,
                                                         java.lang.Object context)

      Calls the appropriate method of the specified `ParameterVisitor` and passes that method the `Parameter` and the specified context `Object`.
      Parameters:
      `visitor` - An instance a class derived from the `ParameterVisitor` class.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the appropriate method of the specified `ParameterVisitor`.

    <!-- -->

    - #### getDataProvider

          public final DataProvider getDataProvider()

      Gets the `DataProvider` for this `Parameter`.
      Returns:
      The `DataProvider` for this `Parameter`.

    <!-- -->

    - #### getID

          public final java.lang.String getID()

      Gets a `String` that uniquely identifies this `Parameter` during this connection.
      Returns:
      A `String` that uniquely identifies this `Parameter`.

    <!-- -->

    - #### getValueObject

          public abstract java.lang.Object getValueObject()

      Gets an `Object` that contains the value for this `Parameter`.
      Returns:
      An `Object` that contains the value for this `Parameter`.

    <!-- -->

    - #### createSource

          public Source createSource()

      Creates a `Source` of the appropriate data type that contains the value specified for the `Parameter`. The concrete subclasses of `Parameter` have constructors that take an initial value. An application can specify a different value by calling the `setValue` of the subclass.
      Returns:
      The `Source` associated with the `Parameter`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](NumberSource.md)
- [Next Class](ParameterVisitor.md)

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
