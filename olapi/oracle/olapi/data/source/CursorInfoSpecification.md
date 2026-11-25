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

- [Prev Class](CompoundCursorSpecification.md)
- [Next Class](CursorLockException.md)

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

## Interface CursorInfoSpecification

- All Known Subinterfaces:
  [CompoundCursorInfoSpecification](CompoundCursorInfoSpecification.md), [ValueCursorInfoSpecification](ValueCursorInfoSpecification.md)

  <!-- -->

  All Known Implementing Classes:
  [CompoundCursorSpecification](CompoundCursorSpecification.md), [CursorSpecification](CursorSpecification.md), [ValueCursorSpecification](ValueCursorSpecification.md)

  ------------------------------------------------------------------------



      public interface CursorInfoSpecification

  An interface that specifies characteristics of a `Cursor`. You can create an instance of an implementation of `CursorInfoSpecification` by calling the `createCursorInfoSpecification` method of a `DataProvider`. You can pass the `CursorInfoSpecification` to one of the `createCursorManager` methods of the `DataProvider`, and then call the `createCursor` method of the `CursorManager`.
  See Also:
  [`DataProvider`](DataProvider.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type     | Method and Description                                                                                                                                                       |
    |-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Source`](Source.md) | `getSource``()`<br>Gets the `Source` for this `CursorInfoSpecification`.                                                                                                     |
    | `boolean`             | `isParentEndCalculationSpecified``()`<br>Indicates whether the `CursorInfoSpecification` is set to calculate the ending position of the `Cursor` in the parent `Cursor`.     |
    | `boolean`             | `isParentStartCalculationSpecified``()`<br>Indicates whether the `CursorInfoSpecification` is set to calculate the starting position of the `Cursor` in the parent `Cursor`. |
    | `void`                | `setParentEndCalculationSpecified``(boolean b)`<br>Specifies whether to calculate the ending position of the `Cursor` in the parent `Cursor`.                                |
    | `void`                | `setParentStartCalculationSpecified``(boolean b)`<br>Specifies whether to calculate the starting position of the `Cursor` in the parent `Cursor`.                            |

<!-- -->

- - ### Method Detail

    - #### getSource

          Source getSource()

      Gets the `Source` for this `CursorInfoSpecification`.
      Returns:
      The `Source` for this `CursorInfoSpecification`.

    <!-- -->

    - #### isParentEndCalculationSpecified

          boolean isParentEndCalculationSpecified()

      Indicates whether the `CursorInfoSpecification` is set to calculate the ending position of the `Cursor` in the parent `Cursor`.
      Returns:
      `true` if the `CursorInfoSpecification` is set to calculate the ending position of the `Cursor` in the parent `Cursor` and false otherwise.

    <!-- -->

    - #### isParentStartCalculationSpecified

          boolean isParentStartCalculationSpecified()

      Indicates whether the `CursorInfoSpecification` is set to calculate the starting position of the `Cursor` in the parent `Cursor`.
      Returns:
      `true` if the `CursorInfoSpecification` is set to calculate the starting position of the `Cursor` in the parent `Cursor` and false otherwise.

    <!-- -->

    - #### setParentEndCalculationSpecified

          void setParentEndCalculationSpecified(boolean b)

      Specifies whether to calculate the ending position of the `Cursor` in the parent `Cursor`.
      Parameters:
      `b` - `true` to calculate the ending position of the `Cursor` in the parent and `false` otherwise.

    <!-- -->

    - #### setParentStartCalculationSpecified

          void setParentStartCalculationSpecified(boolean b)

      Specifies whether to calculate the starting position of the `Cursor` in the parent `Cursor`.
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

- [Prev Class](CompoundCursorSpecification.md)
- [Next Class](CursorLockException.md)

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
