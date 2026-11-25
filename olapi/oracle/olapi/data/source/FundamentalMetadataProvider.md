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

- [Prev Class](FundamentalMetadataObject.md)
- [Next Class](IncorrectDataValueException.md)

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

## Class FundamentalMetadataProvider

- java.lang.Object

- - oracle.olapi.data.source.FundamentalMetadataProvider

<!-- -->

- All Implemented Interfaces:
  [MetadataProvider](../../metadata/MetadataProvider.md)

  ------------------------------------------------------------------------



      public final class FundamentalMetadataProvider
      extends java.lang.Object
      implements MetadataProvider

  Provides `FundamentalMetadataObject` objects that represent OLAP Java API data types. In this documentation, the OLAP Java API data types appear in regular type face instead of in monospace type face to distinguish them from `java.lang` data type wrapper classes such as `Boolean` and `Float`. You get a `FundamentalMetadataProvider` with the `getFundamentalMetadataProvider` method of a `DataProvider`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                           | Method and Description                                                                                                                                                 |
    |-------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`FundamentalMetadataObject`](FundamentalMetadataObject.md) | `getBooleanDataType``()`<br>Gets the `FundamentalMetadataObject` that represents the OLAP Java API Boolean data type.                                                  |
    | [`FundamentalMetadataObject`](FundamentalMetadataObject.md) | `getDateDataType``()`<br>Gets the `FundamentalMetadataObject` that represents the OLAP Java API Date data type.                                                        |
    | [`FundamentalMetadataObject`](FundamentalMetadataObject.md) | `getDoubleDataType``()`<br>Gets the `FundamentalMetadataObject` that represents the OLAP Java API Double data type.                                                    |
    | [`FundamentalMetadataObject`](FundamentalMetadataObject.md) | `getEmptyDataType``()`<br>Gets the `FundamentalMetadataObject` that represents the OLAP Java API Empty data type.                                                      |
    | [`FundamentalMetadataObject`](FundamentalMetadataObject.md) | `getFloatDataType``()`<br>Gets the `FundamentalMetadataObject` that represents the OLAP Java API Float data type.                                                      |
    | `java.lang.String`                                          | `getID``()`<br>Gets the unique identifier for this `FundamentalMetadataProvider`.                                                                                      |
    | [`FundamentalMetadataObject`](FundamentalMetadataObject.md) | `getIntegerDataType``()`<br>Gets the `FundamentalMetadataObject` that represents the OLAP Java API Integer data type.                                                  |
    | [`FundamentalMetadataObject`](FundamentalMetadataObject.md) | `getMetadataObject``(java.lang.String id)`<br>Gets the `FundamentalMetadataObject` that has the specified identifier.                                                  |
    | `java.util.List`                                            | `getMetadataObjects``(java.lang.String[] ids)`<br>Retrieves a `List` in which each element is a `FundamentalMetadataObject` that has one of the specified identifiers. |
    | [`FundamentalMetadataObject`](FundamentalMetadataObject.md) | `getNumberDataType``()`<br>Gets the `FundamentalMetadataObject` that represents the OLAP Java API Number data type.                                                    |
    | [`FundamentalMetadataObject`](FundamentalMetadataObject.md) | `getShortDataType``()`<br>Gets the `FundamentalMetadataObject` that represents the OLAP Java API Short data type.                                                      |
    | [`FundamentalMetadataObject`](FundamentalMetadataObject.md) | `getStringDataType``()`<br>Gets the `FundamentalMetadataObject` that represents the OLAP Java API String data type.                                                    |
    | [`FundamentalMetadataObject`](FundamentalMetadataObject.md) | `getValueDataType``()`<br>Gets the `FundamentalMetadataObject` that represents the OLAP Java API Value data type.                                                      |
    | [`FundamentalMetadataObject`](FundamentalMetadataObject.md) | `getVoidDataType``()`<br>Gets the `FundamentalMetadataObject` that represents the OLAP Java API Void data type.                                                        |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getID

          public final java.lang.String getID()

      Gets the unique identifier for this `FundamentalMetadataProvider`.
      Specified by:
      [`getID`](../../metadata/MetadataProvider.md) in interface [`MetadataProvider`](../../metadata/MetadataProvider.md)

      Returns:
      The unique identifier for this `FundamentalMetadataProvider`.

    <!-- -->

    - #### getMetadataObject

          public final FundamentalMetadataObject getMetadataObject(java.lang.String id)

      Gets the `FundamentalMetadataObject` that has the specified identifier.
      Parameters:
      `id` - A `String` that uniquely identifies the `FundamentalMetadataObject` to be retrieved.

      Returns:
      The requested `FundamentalMetadataObject`.

    <!-- -->

    - #### getMetadataObjects

          public final java.util.List getMetadataObjects(java.lang.String[] ids)

      Retrieves a `List` in which each element is a `FundamentalMetadataObject` that has one of the specified identifiers.
      Parameters:
      `ids` - An array of `String` objects, each of which uniquely identifies a `FundamentalMetadataObject` to be retrieved.

      Returns:
      A `List` that contains a `FundamentalMetadataObject` for each of the specified identifiers.

    <!-- -->

    - #### getValueDataType

          public final FundamentalMetadataObject getValueDataType()

      Gets the `FundamentalMetadataObject` that represents the OLAP Java API Value data type. When the values of the elements of a `Source` object are any combination of the OLAP Java API Number, String, or Empty data types, the `Source` object has the OLAP Java API Value data type.
      Returns:
      A `FundamentalMetadataObject` that represents the OLAP Java API Value data type.

    <!-- -->

    - #### getEmptyDataType

          public final FundamentalMetadataObject getEmptyDataType()

      Gets the `FundamentalMetadataObject` that represents the OLAP Java API Empty data type. When a `Source` object has the OLAP Java API data type of Empty, it does not have any elements.
      Returns:
      A `FundamentalMetadataObject` that represents the OLAP Java API Empty data type.

    <!-- -->

    - #### getVoidDataType

          public final FundamentalMetadataObject getVoidDataType()

      Gets the `FundamentalMetadataObject` that represents the OLAP Java API Void data type. When a `Source` object has the OLAP Java API data type of Void, it one element, which has a `null` value.
      Returns:
      A `FundamentalMetadataObject` that represents the OLAP Java API Void data type.

    <!-- -->

    - #### getBooleanDataType

          public final FundamentalMetadataObject getBooleanDataType()

      Gets the `FundamentalMetadataObject` that represents the OLAP Java API Boolean data type. When a `Source` object has the OLAP Java API data type of Boolean, all of the values of its elements have the Java `boolean` data type.
      Returns:
      A `FundamentalMetadataObject` that represents the OLAP Java API Boolean data type.

    <!-- -->

    - #### getStringDataType

          public final FundamentalMetadataObject getStringDataType()

      Gets the `FundamentalMetadataObject` that represents the OLAP Java API String data type. When a `Source` object has the OLAP Java API data type of String, all of the values of its elements are Java `String` objects.
      Returns:
      A `FundamentalMetadataObject` that represents the OLAP Java API String data type.

    <!-- -->

    - #### getNumberDataType

          public final FundamentalMetadataObject getNumberDataType()

      Gets the `FundamentalMetadataObject` that represents the OLAP Java API Number data type. When the values of the elements of a `Source` object are any combination of the OLAP Java API numerical data types (that is, Double, Float, Integer, or Short), the `Source` object has the OLAP Java API Number data type.
      Returns:
      A `FundamentalMetadataObject` that represents the OLAP Java API Number data type.

    <!-- -->

    - #### getShortDataType

          public final FundamentalMetadataObject getShortDataType()

      Gets the `FundamentalMetadataObject` that represents the OLAP Java API Short data type. When a `Source` object has the OLAP Java API data type of Short, all of the values of its elements have the Java `short` data type.
      Returns:
      A `FundamentalMetadataObject` that represents the OLAP Java API Short data type.

    <!-- -->

    - #### getIntegerDataType

          public final FundamentalMetadataObject getIntegerDataType()

      Gets the `FundamentalMetadataObject` that represents the OLAP Java API Integer data type. When a `Source` object has the OLAP Java API data type of Integer, all of the values of its elements have the Java `int` data type.
      Returns:
      A `FundamentalMetadataObject` that represents the OLAP Java API Integer data type.

    <!-- -->

    - #### getFloatDataType

          public final FundamentalMetadataObject getFloatDataType()

      Gets the `FundamentalMetadataObject` that represents the OLAP Java API Float data type. When a `Source` object has the OLAP Java API data type of Float, all of the values of its elements have the Java `float` data type.
      Returns:
      A `FundamentalMetadataObject` that represents the OLAP Java API Float data type.

    <!-- -->

    - #### getDoubleDataType

          public final FundamentalMetadataObject getDoubleDataType()

      Gets the `FundamentalMetadataObject` that represents the OLAP Java API Double data type. When a `Source` object has the OLAP Java API data type of Double, all of the values of its elements have the Java `double` data type.
      Returns:
      A `FundamentalMetadataObject` that represents the OLAP Java API Double data type.

    <!-- -->

    - #### getDateDataType

          public final FundamentalMetadataObject getDateDataType()

      Gets the `FundamentalMetadataObject` that represents the OLAP Java API Date data type. When a `Source` object has the OLAP Java API data type of Date, all of the values of its elements are Java `Date` objects.
      Returns:
      A `FundamentalMetadataObject` that represents the OLAP Java API Date data type.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](FundamentalMetadataObject.md)
- [Next Class](IncorrectDataValueException.md)

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
