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

- [Prev Class](CursorManager.md)
- [Next Class](CursorManagerUpdateListener.md)

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

## Class CursorManagerUpdateEvent

- java.lang.Object

- - java.util.EventObject

  - - oracle.olapi.data.cursor.CursorManagerUpdateEvent

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  ------------------------------------------------------------------------



      public class CursorManagerUpdateEvent
      extends java.util.EventObject

  An event passed by a `CursorManager` to the `CursorManageUpdateListener` objects associated with it. When a `CursorManager` becomes aware that a change has occurred to the `Source` associated with it, it calls the appropriate method on a `CursorManageUpdateListener` and passes that method a `CursorManagerUpdateEvent`.
  See Also:
  [`CursorManagerUpdateListener`](CursorManagerUpdateListener.md), [Serialized Form](../../../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                                                                                                                                                                                             |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static int`      | `CURSOR_MANAGER_DATA_UPDATED`<br>A constant that indicates that the `Source` associated with a `CursorManager` has changed so that the data specified by `Source` is different but the structure of the `Source` has not changed. |
    | `static int`      | `CURSOR_MANAGER_SPECIFICATION_UPDATED`<br>A constant that indicates that the `CursorInfoSpecification` associated with the `CursorManager` has been updated.                                                                      |
    | `static int`      | `CURSOR_MANAGER_STRUCTURE_UPDATED`<br>A constant that indicates that the `Source` associated with a `CursorManager` has changed and the structure of the `Source` is now different.                                               |

    - ### Fields inherited from class java.util.EventObject

      `source`

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                 |
    |-----------------------------------------------------------------------------------------------------------------------------|
    | `CursorManagerUpdateEvent``(`[`CursorManager`](CursorManager.md)` source, int id)`<br>Creates a `CursorManagerUpdateEvent`. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                   | Method and Description                                                                                                                  |
    |-------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
    | [`CursorManager`](CursorManager.md) | `getCursorManager``()`<br>Gets the `CursorManager` that originated the event.                                                           |
    | `int`                               | `getID``()`<br>Gets the constant that identifies the type of event that occurred, such as the `CURSOR_MANAGER_STRUCTURE_UPDATED` event. |

    - ### Methods inherited from class java.util.EventObject

      `getSource, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### CURSOR_MANAGER_DATA_UPDATED

          public static final int CURSOR_MANAGER_DATA_UPDATED

      A constant that indicates that the `Source` associated with a `CursorManager` has changed so that the data specified by `Source` is different but the structure of the `Source` has not changed.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### CURSOR_MANAGER_STRUCTURE_UPDATED

          public static final int CURSOR_MANAGER_STRUCTURE_UPDATED

      A constant that indicates that the `Source` associated with a `CursorManager` has changed and the structure of the `Source` is now different.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### CURSOR_MANAGER_SPECIFICATION_UPDATED

          public static final int CURSOR_MANAGER_SPECIFICATION_UPDATED

      A constant that indicates that the `CursorInfoSpecification` associated with the `CursorManager` has been updated.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### CursorManagerUpdateEvent

          public CursorManagerUpdateEvent(CursorManager source,
                                          int id)

      Creates a `CursorManagerUpdateEvent`.
      Parameters:
      `source` - The `CursorManager` that originated the event.

      `id` - The constant that indicates the type of the event that occurred.

  <!-- -->

  - ### Method Detail

    - #### getCursorManager

          public CursorManager getCursorManager()

      Gets the `CursorManager` that originated the event.
      Returns:
      The `CursorManager` that originated the event.

    <!-- -->

    - #### getID

          public int getID()

      Gets the constant that identifies the type of event that occurred, such as the `CURSOR_MANAGER_STRUCTURE_UPDATED` event.
      Returns:
      The constant that indicates the type of the event that occurred.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

Copyright © 2002, 2018, Oracle. All rights reserved.

- [Prev Class](CursorManager.md)
- [Next Class](CursorManagerUpdateListener.md)

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
