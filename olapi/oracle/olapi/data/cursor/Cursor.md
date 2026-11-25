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

- [Prev Class](CompoundCursor.md)
- [Next Class](CursorManager.md)

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

## Interface Cursor

- All Known Subinterfaces:
  [CompoundCursor](CompoundCursor.md), [ValueCursor](ValueCursor.md)

  ------------------------------------------------------------------------



      public interface Cursor

  An interface for objects that provide access to the result set of a query. A query is represented by a `Source`. A `Cursor` communicates the query to Oracle OLAP and fetches the resulting data.
  At any time, one element of a `Cursor` is in the current position of the `Cursor`. The `getPosition` method returns the current position and the `setPosition` and `next` methods change the current position. The extent of a `Cursor` is the total number of positions of the `Cursor`.

  An `Source` is associated with a `Transaction`. A `Source` is active in the `Transaction` with which it is associated or in a descendent of that `Transaction`. Before an application can create a `Cursor` for a `Source`, the current `Transaction` must be the one with which the `Source` is associated or it must be a descendent of that `Transaction`. For more information on transactions, see the [`TransactionProvider`](../../transaction/TransactionProvider.md) interface.

  An application creates a `Cursor` for a `Source` by calling the `createCursor` method of a `CursorManager`. The following example demonstrates creating a `Cursor` for a `Source` named `query`.

       CursorManager cursorManager = dataProvider.createCursorManager(query);
       Cursor cursor = cursorManager.createCursor();

  An application can create more than one `Cursor` from the same `CursorManager`. It would do this if, for example, it wanted to display different views of the same data.
  The `Cursor` interface has two subinterfaces: `CompoundCursor` and `ValueCursor`. The type of `Cursor` returned by the `createCursor` method is determined by the structure of the `Source` for the `Cursor`. If the `Source` for the `Cursor` has no outputs, then the `Cursor` has only one set of values and the `createCursor` method returns a `ValueCursor`, the elements of which have the values specified by the `Source`. If the `Source` has one or more outputs, then the `createCursor` method returns a `CompoundCursor`.

  A `CompoundCursor` has two or more child `Cursor` objects. The children are the base `ValueCursor` for the `CompoundCursor` and a `Cursor` object for each output of the `Source`. If the output of the `Source` is a `Source` that itself has one or more outputs, then the child `Cursor` for that output is another `CompoundCursor`. If the output is a `Source` that has no outputs, then the child `Cursor` is a `ValueCursor`. Each position of a `CompoundCursor` specifies a position for each of the `ValueCursor` objects in the tree of the descendents of the `CompoundCursor`.

  An application can affect the behavior of a `Cursor` by creating a `CursorSpecification`, which implements the `CursorInfoSpecification` interface. An application creates a `CursorInfoSpecification` with the `createCursorInfoSpecification` method of a `DataProvider`. With a `CursorSpecification`, an application can specify whether Oracle OLAP calculates the extent of a `Cursor` or the starting and ending positions of the current value of a child `Cursor` in the parent `Cursor`. If a `CursorSpecification` specifies those calculations, then the application can retrieve information with the `getExtent`, `getParentStart`, or `getParentEnd` methods. By subtracting the starting position of the current value of a child in the parent from the ending position of the value and adding one, you can calculate the range of positions, or span, of the value of the child `Cursor`.

  The extent of a child `ValueCursor` in a parent `CompoundCursor` is the number of positions the `ValueCursor` has for the set of values specified by the other `ValueCursor` descendents. For example, if a `Source` defines the result set for a measure, which has only one value for any set of values of the dimensions of the measure, then the `ValueCursor` that has the values of the measure has only one position for any one set of output values. The extent of that `ValueCursor` is, therefore, always 1.

  The fetch size of a `Cursor` specifies the number of elements of the `Cursor` that Oracle OLAP sends to the client application during a single fetch from the data store. If the `CursorSpecification` for the `Cursor` is set to specify the default fetch size, you can retrieve the fetch size by calling the `getFetchSize` method. You can change the fetch size by calling the `setFetchSize` method.

  Some `Source` objects cannot have a `Cursor`. You cannot retrieve results with a `Cursor` for a `Source` if one of the following is true:

  - The `Source` has an input.
  - The `Source` has no elements or the `Source` has an input that has no elements.
  - The query is not computationally possible; for example, the query involves an infinite recursion.
  - The result set is infinite; for example, the `Source` represents all integers.

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                                                                                                                                                                  |
    |-------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static int`      | `FETCH_SIZE_NOT_SPECIFIED`<br>A constant value returned by the `getDefaultFetchSize` method of a `CursorSpecification` object if the default fetch size is not specified by the `CursorSpecification`. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                         | Method and Description                                                                                                                                                                                               |
    |-------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `long`                                    | `getExtent``()`<br>Gets the total number of positions of the `Cursor` if the `CursorSpecification` associated with the `Cursor` is set to calculate the extent.                                                      |
    | `int`                                     | `getFetchSize``()`<br>Gets the fetch size for the `Cursor` if the `CursorSpecification` for the `Cursor` is set to specify the fetch size.                                                                           |
    | `long`                                    | `getParentEnd``()`<br>Gets the position in the parent `Cursor` at which the current element of the child `Cursor` ends if the `CursorSpecification` for the `Cursor` is set to calculate the ending position.        |
    | `long`                                    | `getParentStart``()`<br>Gets the position in the parent `Cursor` at which the current element of the child `Cursor` begins if the `CursorSpecification` for the `Cursor` is set to calculate the beginning position. |
    | `long`                                    | `getPosition``()`<br>Gets the current position of the `Cursor`.                                                                                                                                                      |
    | [`SourceIdentifier`](SourceIdentifier.md) | `getSource``()`<br>Gets the `SourceIdentifier` for the `Cursor`.                                                                                                                                                     |
    | `boolean`                                 | `()`<br>Advances the position of the `Cursor` to the next element if the current position is not the last position of the `Cursor`.                                                                                  |
    | `void`                                    | `setFetchSize``(int fetchSize)`<br>Specifies the fetch size for the `Cursor` if the `CursorSpecification` for the `Cursor` is set to specify the fetch size.                                                         |
    | `void`                                    | `setPosition``(long position)`<br>Specifies a position to set as the current position of the `Cursor`.                                                                                                               |

<!-- -->

- - ### Field Detail

    - #### FETCH_SIZE_NOT_SPECIFIED

          static final int FETCH_SIZE_NOT_SPECIFIED

      A constant value returned by the `getDefaultFetchSize` method of a `CursorSpecification` object if the default fetch size is not specified by the `CursorSpecification`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getSource

          SourceIdentifier getSource()

      Gets the `SourceIdentifier` for the `Cursor`.
      Returns:
      The `SourceIdentifier` for the `Cursor`.

    <!-- -->

    - #### getPosition

          long getPosition()

      Gets the current position of the `Cursor`.
      Returns:
      The current position of the `Cursor`.

    <!-- -->

    - #### setPosition

          void setPosition(long position)
                    throws PositionOutOfBoundsException

      Specifies a position to set as the current position of the `Cursor`.
      Parameters:
      `position` - The position to set as the current position of the `Cursor`.

      Throws:
      [`PositionOutOfBoundsException`](PositionOutOfBoundsException.md) - Indicates that the specified position is not valid.

    <!-- -->

    - #### next

          boolean next()

      Advances the position of the `Cursor` to the next element if the current position is not the last position of the `Cursor`.
      Returns:
      `true` when the method successfully advances the position of the `Cursor` and `false` when it does not.

    <!-- -->

    - #### getExtent

          long getExtent()
                  throws NotSpecifiedException

      Gets the total number of positions of the `Cursor` if the `CursorSpecification` associated with the `Cursor` is set to calculate the extent. The extent of a `ValueCursor` that is a descendent in a `CompoundCursor` is determined by the values of the other outputs.
      Returns:
      The total number of positions of the `Cursor`.

      Throws:
      [`NotSpecifiedException`](NotSpecifiedException.md) - Indicates that the `CursorSpecification` does not specify calculating the extent.

    <!-- -->

    - #### getParentStart

          long getParentStart()
                       throws NotSpecifiedException

      Gets the position in the parent `Cursor` at which the current element of the child `Cursor` begins if the `CursorSpecification` for the `Cursor` is set to calculate the beginning position.
      Returns:
      The position in the parent `Cursor` at which the current element of the child `Cursor` begins.

      Throws:
      [`NotSpecifiedException`](NotSpecifiedException.md) - Indicates that the `CursorSpecification` does not specify calculating the beginning position.

    <!-- -->

    - #### getParentEnd

          long getParentEnd()
                     throws NotSpecifiedException

      Gets the position in the parent `Cursor` at which the current element of the child `Cursor` ends if the `CursorSpecification` for the `Cursor` is set to calculate the ending position.
      Returns:
      The position in the parent `Cursor` at which the current element of the child `Cursor` ends.

      Throws:
      [`NotSpecifiedException`](NotSpecifiedException.md) - Indicates that the `CursorSpecification` does not specify calculating the ending position.

    <!-- -->

    - #### getFetchSize

          int getFetchSize()
                    throws NotSpecifiedException

      Gets the fetch size for the `Cursor` if the `CursorSpecification` for the `Cursor` is set to specify the fetch size.
      Returns:
      The fetch size specified for the `Cursor`.

      Throws:
      [`NotSpecifiedException`](NotSpecifiedException.md)

    <!-- -->

    - #### setFetchSize

          void setFetchSize(int fetchSize)
                     throws NotSpecifiedException

      Specifies the fetch size for the `Cursor` if the `CursorSpecification` for the `Cursor` is set to specify the fetch size.
      Parameters:
      `fetchSize` - The fetch size to specify for the `Cursor`.

      Throws:
      [`NotSpecifiedException`](NotSpecifiedException.md) - Indicates that the `CursorSpecification` does not specify setting a fetch size.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](CompoundCursor.md)
- [Next Class](CursorManager.md)

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
