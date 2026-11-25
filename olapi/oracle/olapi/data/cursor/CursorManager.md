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

- [Prev Class](Cursor.md)
- [Next Class](CursorManagerUpdateEvent.md)

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

## Interface CursorManager

- All Known Subinterfaces:
  [SpecifiedCursorManager](../source/SpecifiedCursorManager.md)

  ------------------------------------------------------------------------



      public interface CursorManager

  An interface for an object that creates and manages `Cursor` objects. An implementation of `CursorManager` has methods that create a `Cursor`, get or set the fetch size for the `Cursor` objects created by it, and get the `Source` associated with it.
  To create a `CursorManager`, call the `createCursorManager` method of a `DataProvider`. An application can create more than one `Cursor` from the same `CursorManager`. Those `Cursor` objects share the same data cache. An application might want to create two different `Cursor` objects if, for example, it wants to display different views of the same data, such as a table view and a graph view.

  See Also:
  [`CursorInfoSpecification`](../source/CursorInfoSpecification.md), [`DataProvider`](../source/DataProvider.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type               | Method and Description                                                                                                                                                                                                       |
    |---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                          | `addCursorManagerUpdateListener``(`[`CursorManagerUpdateListener`](CursorManagerUpdateListener.md)` l)`<br>Adds a `CursorManagerUpdateListener` to the `CursorManager`.                                                      |
    | `void`                          | `close``()`<br>Closes the `CursorManager` and releases the resources associated with it.                                                                                                                                     |
    | [`Cursor`](Cursor.md)           | `createCursor``()`<br>Creates a `Cursor` for the `Source` associated with the `CursorManager`.                                                                                                                               |
    | `int`                           | `getFetchSize``()`<br>Gets the fetch size for a `Cursor` created by this `CursorManager`.                                                                                                                                    |
    | [`Source`](../source/Source.md) | `getSource``()`<br>Gets the `Source` associated with this `CursorManager`.                                                                                                                                                   |
    | `boolean`                       | `isSpecificationUpdateNeeded``()`<br>Indicates whether the structure has changed of the `Source` associated with the `CursorManager`.                                                                                        |
    | `void`                          | `removeCursorManagerUpdateListener``(`[`CursorManagerUpdateListener`](CursorManagerUpdateListener.md)` l)`<br>Removes a `CursorManagerUpdateListener` from the list of listeners for the `CursorManager`.                    |
    | `void`                          | `setFetchSize``(int fetchSize)`<br>Specifies the fetch size for `Cursor` objects created by this `CursorManager`.                                                                                                            |
    | `void`                          | `updateSpecification``(`[`CursorInfoSpecification`](../source/CursorInfoSpecification.md)` cursorInfoSpec)`<br>Replaces the `CursorInfoSpecification` for this `CursorManager` with the specified `CursorInfoSpecification`. |

<!-- -->

- - ### Method Detail

    - #### close

          void close()

      Closes the `CursorManager` and releases the resources associated with it. Any `Cursor` objects created by the `CursorManager` become unusable.

    <!-- -->

    - #### createCursor

          Cursor createCursor()

      Creates a `Cursor` for the `Source` associated with the `CursorManager`.
      Returns:
      A `Cursor`.

    <!-- -->

    - #### isSpecificationUpdateNeeded

          boolean isSpecificationUpdateNeeded()

      Indicates whether the structure has changed of the `Source` associated with the `CursorManager`. If the structure of the `Source` has changed, then you need to create a new `CursoInfoSpecification` for the changed `Source`. You can use the new `CursorInfoSpecification` to update the specification for the existing `CursorManager` or use it to create a new `CursorManager`.
      Returns:
      A `boolean` that is `true` if the structure of the `Source` associated with the `CursorManager` has changed or `false` otherwise.

    <!-- -->

    - #### addCursorManagerUpdateListener

          void addCursorManagerUpdateListener(CursorManagerUpdateListener l)

      Adds a `CursorManagerUpdateListener` to the `CursorManager`.
      Parameters:
      `l` - The `CursorManagerUpdateListener` to add to this `CursorManager`.

    <!-- -->

    - #### removeCursorManagerUpdateListener

          void removeCursorManagerUpdateListener(CursorManagerUpdateListener l)

      Removes a `CursorManagerUpdateListener` from the list of listeners for the `CursorManager`.
      Parameters:
      `l` - The `CursorManagerUpdateListener` to remove from the list of listeners.

    <!-- -->

    - #### getSource

          Source getSource()

      Gets the `Source` associated with this `CursorManager`.
      Returns:
      The `Source` for this `CursorManager`.

    <!-- -->

    - #### updateSpecification

          void updateSpecification(CursorInfoSpecification cursorInfoSpec)

      Replaces the `CursorInfoSpecification` for this `CursorManager` with the specified `CursorInfoSpecification`. When you change the structure of the `Source` for a `CursorManager`, the `CursorInfoSpecification` becomes outdated.
      To continue to use this `CursorManager`, you must create a new `CursorInfoSpecification`, and call this method and pass in the new `CursorInfoSpecification`. You can then create new `Cursor` objects the `CursorManager`.

      Parameters:
      `cursorInfoSpec` - The `CursorInfoSpecification` with which to replace the current `CursorInfoSpecification` for this `CursorManager`.

    <!-- -->

    - #### getFetchSize

          int getFetchSize()

      Gets the fetch size for a `Cursor` created by this `CursorManager`.
      Returns:
      An integer that is the fetch size for Cursor objects created by this `CursorManager`.

    <!-- -->

    - #### setFetchSize

          void setFetchSize(int fetchSize)

      Specifies the fetch size for `Cursor` objects created by this `CursorManager`.
      Parameters:
      `fetchSize` - An integer that is the fetch size you want to specify for `Cursor` objects created by this `CursorManager`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](Cursor.md)
- [Next Class](CursorManagerUpdateEvent.md)

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
