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

- [Prev Class](SourceGenerator.md)
- [Next Class](SQLCursorManager.md)

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

## Interface SpecifiedCursorManager

- All Superinterfaces:
  [CursorManager](../cursor/CursorManager.md)

  ------------------------------------------------------------------------



      public interface SpecifiedCursorManager
      extends CursorManager

  A `CursorManager` that specifies methods for determining whether the `SpecifiedCursorManager` is open and for getting and setting the input `Source` objects associated with this `SpecifiedCursorManager`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type         | Method and Description                                                                                                                                         |
    |---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Source`](Source.md)`[]` | `getInputSources``()`<br>Returns an array that has the input `Source` objects associated with this `SpecifiedCursorManager`.                                   |
    | `boolean`                 | `isOpen``()`<br>Indicates whether this `SpecifiedCursorManager` is still open.                                                                                 |
    | `void`                    | `setInputSources``(`[`Source`](Source.md)`[] newInputSources)`<br>Replaces the existing input `Source`Source objects specified by the `newInputSources` array. |

    - ### Methods inherited from interface oracle.olapi.data.cursor.[CursorManager](../cursor/CursorManager.md)

      [`addCursorManagerUpdateListener`](../cursor/CursorManager.md)`, `[`close`](../cursor/CursorManager.md)`, `[`createCursor`](../cursor/CursorManager.md)`, `[`getFetchSize`](../cursor/CursorManager.md)`, `[`getSource`](../cursor/CursorManager.md)`, `[`isSpecificationUpdateNeeded`](../cursor/CursorManager.md)`, `[`removeCursorManagerUpdateListener`](../cursor/CursorManager.md)`, `[`setFetchSize`](../cursor/CursorManager.md)`, `[`updateSpecification`](../cursor/CursorManager.md)

<!-- -->

- - ### Method Detail

    - #### isOpen

          boolean isOpen()

      Indicates whether this `SpecifiedCursorManager` is still open.
      Returns:
      `true` if the `SpecifiedCursorManager` is open and `false` if it is closed.

    <!-- -->

    - #### getInputSources

          Source[] getInputSources()

      Returns an array that has the input `Source` objects associated with this `SpecifiedCursorManager`.
      Returns:
      An array of `Source` objects that are the input `Source` objects of this `SpecifiedCursorManager`.

    <!-- -->

    - #### setInputSources

          void setInputSources(Source[] newInputSources)

      Replaces the existing input `Source`Source objects specified by the `newInputSources` array.
      Parameters:
      `newInputSources` - An array of `Source`Source objects of the `SpecifiedCursorManager`.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](SourceGenerator.md)
- [Next Class](SQLCursorManager.md)

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
