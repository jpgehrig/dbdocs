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

- [Prev Class](CursorLockException.md)
- [Next Class](CursorSpecificationVisitor.md)

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

## Class CursorSpecification

- java.lang.Object

- - oracle.olapi.data.source.CursorSpecification

<!-- -->

- All Implemented Interfaces:
  [CursorInfoSpecification](CursorInfoSpecification.md)

  <!-- -->

  Direct Known Subclasses:
  [CompoundCursorSpecification](CompoundCursorSpecification.md), [ValueCursorSpecification](ValueCursorSpecification.md)

  ------------------------------------------------------------------------



      public abstract class CursorSpecification
      extends java.lang.Object
      implements CursorInfoSpecification

  The base class for an object that specifies characteristics of a `Cursor` for a `Source`. A `CursorSpecification` implements the `CursorInfoSpecification` interface. An application creates a `CursorSpecification` with the `createCursorInfoSpecification(Source rootSource)` method of a `DataProvider`. That method returns a `CompoundCursorSpecification` or a `ValueCursorSpecification`.
  After creating a `CursorInfoSpecification`, an application can create a `CursorManager` by passing the `CursorInfoSpecification` to a `createCursorManager` method of the `DataProvider`. The application can then create a `Cursor` by calling the `createCursor` method of the `CursorManager`.

  With the methods of a `CursorSpecification`, an application can specify that it wants information such as the extent of the `Cursor`, which is the total number of elements the `Cursor` contains, or the position in a parent `Cursor` at which a child `Cursor` starts or ends. Calculating the extent or the starting or ending positions can take a lot of time and computing resources, so an application should only set the `CursorSpecification` to do so when it needs the information.

  An application can also set the default fetch size for a `Cursor` by calling the `setDefaultFetchSize` method of the `CursorSpecification` for that `Cursor`. The fetch size is the number of elements that a `Cursor` retrieves during a single fetch from the data store. If the application sets the default fetch size on a `CursorSpecification`, then it can then change the fetch size for the `Cursor` by calling the `setFetchSize` method of the `Cursor` itself.

  With other methods of a `CursorSpecification`, an application can accept a `CursorSpecificationVisitor` or retrieve the `Source` for the `CursorSpecification`. The `Source` for a `CursorSpecification` is the `Source` that defines the data that the `Cursor` retrieves from the data store.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                 | Method and Description                                                                                                                                                                                                                                                                                 |
    |---------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `abstract java.lang.Object`                       | `acceptVisitor``(`[`CursorSpecificationVisitor`](CursorSpecificationVisitor.md)` visitor, java.lang.Object context)`<br>Calls the `visitCursorSpecification` method of the specified `CursorSpecificationVisitor` and passes that method the `CursorSpecification` and the specified `context` object. |
    | `int`                                             | `getDefaultFetchSize``()`<br>Gets the fetch size set as the default for this `CursorSpecification`.                                                                                                                                                                                                    |
    | [`Source`](Source.md)                             | `getSource``()`<br>Gets the `Source` associated with the `CursorSpecification`.                                                                                                                                                                                                                        |
    | [`Transaction`](../../transaction/Transaction.md) | `getTransaction``()`<br>Gets the `Transaction` object for this `CursorSpecification`.                                                                                                                                                                                                                  |
    | `boolean`                                         | `isExtentCalculationSpecified``()`<br>Indicates whether the `CursorSpecification` is set to calculate the extent for the `Cursor`.                                                                                                                                                                     |
    | `boolean`                                         | `isParentEndCalculationSpecified``()`<br>Indicates whether the `CursorSpecification` is set to calculate the ending position of the `Cursor` in the parent `Cursor`.                                                                                                                                   |
    | `boolean`                                         | `isParentStartCalculationSpecified``()`<br>Indicates whether the `CursorSpecification` is set to calculate the starting position of the `Cursor` in the parent `Cursor`.                                                                                                                               |
    | `void`                                            | `setDefaultFetchSize``(int defaultFetchSize)`<br>Specifies a default fetch size for the `Cursor`.                                                                                                                                                                                                      |
    | `void`                                            | `setExtentCalculationSpecified``(boolean b)`<br>Specifies whether to calculate the extent of the `Cursor`.                                                                                                                                                                                             |
    | `void`                                            | `setParentEndCalculationSpecified``(boolean b)`<br>Specifies whether to calculate the ending position of the `Cursor` in the parent `Cursor`.                                                                                                                                                          |
    | `void`                                            | `setParentStartCalculationSpecified``(boolean b)`<br>Specifies whether to calculate the starting position of the `Cursor` in the parent `Cursor`.                                                                                                                                                      |
    | `void`                                            | `setTransaction``(`[`Transaction`](../../transaction/Transaction.md)` transaction)`<br>Specifies the `Transaction` object for this `CursorSpecification`.                                                                                                                                              |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getTransaction

          public final Transaction getTransaction()

      Gets the `Transaction` object for this `CursorSpecification`.
      Returns:
      The `Transaction` object for this `CursorSpecification`.

    <!-- -->

    - #### setTransaction

          public final void setTransaction(Transaction transaction)

      Specifies the `Transaction` object for this `CursorSpecification`.
      Parameters:
      `transaction` - The `Transaction` object for this `CursorSpecification`.

    <!-- -->

    - #### acceptVisitor

          public abstract java.lang.Object acceptVisitor(CursorSpecificationVisitor visitor,
                                                         java.lang.Object context)

      Calls the `visitCursorSpecification` method of the specified `CursorSpecificationVisitor` and passes that method the `CursorSpecification` and the specified `context` object.
      Parameters:
      `visitor` - A `CursorSpecificationVisitor`.

      `context` - An `Object`.

      Returns:
      The `Object` returned by the `visitCursorSpecification` method.

    <!-- -->

    - #### getDefaultFetchSize

          public final int getDefaultFetchSize()

      Gets the fetch size set as the default for this `CursorSpecification`.
      Returns:
      The default fetch size for the `CursorSpecification` or `Cursor.FETCH_SIZE_NOT_SPECIFIED` if setting the default fetch size is not specified for this `CursorSpecification`.

    <!-- -->

    - #### getSource

          public final Source getSource()

      Gets the `Source` associated with the `CursorSpecification`.
      Specified by:
      [`getSource`](CursorInfoSpecification.md) in interface [`CursorInfoSpecification`](CursorInfoSpecification.md)

      Returns:
      The `Source` associated with the `CursorSpecification`.

    <!-- -->

    - #### isExtentCalculationSpecified

          public final boolean isExtentCalculationSpecified()

      Indicates whether the `CursorSpecification` is set to calculate the extent for the `Cursor`.
      Returns:
      `true` if the `CursorSpecification` is set to calculate the extent for the `Cursor` and false otherwise.

    <!-- -->

    - #### isParentEndCalculationSpecified

          public final boolean isParentEndCalculationSpecified()

      Indicates whether the `CursorSpecification` is set to calculate the ending position of the `Cursor` in the parent `Cursor`.
      Specified by:
      [`isParentEndCalculationSpecified`](CursorInfoSpecification.md) in interface [`CursorInfoSpecification`](CursorInfoSpecification.md)

      Returns:
      `true` if the `CursorSpecification` is set to calculate the ending position of the `Cursor` in the parent `Cursor` and false otherwise.

    <!-- -->

    - #### isParentStartCalculationSpecified

          public final boolean isParentStartCalculationSpecified()

      Indicates whether the `CursorSpecification` is set to calculate the starting position of the `Cursor` in the parent `Cursor`.
      Specified by:
      [`isParentStartCalculationSpecified`](CursorInfoSpecification.md) in interface [`CursorInfoSpecification`](CursorInfoSpecification.md)

      Returns:
      `true` if the `CursorSpecification` is set to calculate the starting position of the `Cursor` in the parent `Cursor` and false otherwise.

    <!-- -->

    - #### setDefaultFetchSize

          public final void setDefaultFetchSize(int defaultFetchSize)
                                         throws java.lang.IllegalArgumentException

      Specifies a default fetch size for the `Cursor`. The default fetch size must be greater than zero. The fetch size can only be set at one level in the hierarchy of a parent `Cursor` and the children of that parent.
      Parameters:
      `defaultFetchSize` - The value to specify as the default fetch size.

      Throws:
      `java.lang.IllegalArgumentException` - Indicates that the values specified for the fetch size is zero or less than zero.

    <!-- -->

    - #### setExtentCalculationSpecified

          public final void setExtentCalculationSpecified(boolean b)

      Specifies whether to calculate the extent of the `Cursor`. For a `CompoundCursorSpecification`, calling this method causes Oracle OLAP to calculate the extents of all of the descendents of the `CompoundCursorSpecification`.
      Parameters:
      `b` - `true` to calculate the extent and `false` otherwise.

    <!-- -->

    - #### setParentEndCalculationSpecified

          public final void setParentEndCalculationSpecified(boolean b)

      Specifies whether to calculate the ending position of the `Cursor` in the parent `Cursor`.
      Specified by:
      [`setParentEndCalculationSpecified`](CursorInfoSpecification.md) in interface [`CursorInfoSpecification`](CursorInfoSpecification.md)

      Parameters:
      `b` - `true` to calculate the ending position of the `Cursor` in the parent and `false` otherwise.

    <!-- -->

    - #### setParentStartCalculationSpecified

          public final void setParentStartCalculationSpecified(boolean b)

      Specifies whether to calculate the starting position of the `Cursor` in the parent `Cursor`.
      Specified by:
      [`setParentStartCalculationSpecified`](CursorInfoSpecification.md) in interface [`CursorInfoSpecification`](CursorInfoSpecification.md)

      Parameters:
      `b` - `true` to calculate the starting position of the `Cursor` in the parent and `false` otherwise.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](CursorLockException.md)
- [Next Class](CursorSpecificationVisitor.md)

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
