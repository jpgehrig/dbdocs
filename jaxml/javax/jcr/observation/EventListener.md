Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](EventIterator.md)**
- **[Next Class](EventListenerIterator.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**javax.jcr.observation**

## **Interface EventListener**

-

  ------------------------------------------------------------------------

  **
  **

      public interface EventListener

  **An event listener.**
  **An `EventListener` can be registered via the [`ObservationManager`](ObservationManager.md) object. Event listeners are notified asynchronously, and see events after they occur and the transaction is committed. An event listener only sees events for which the session that registered it has sufficient access rights.**

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                         |
    |-------------------|------------------------------------------------------------------------------------------------|
    | `void`            | `onEvent``(`[`EventIterator`](EventIterator.md)` events)`<br>Gets called when an event occurs. |

<!-- -->

- - ### Method Detail

    - #### onEvent

          void onEvent(EventIterator events)

      Gets called when an event occurs.
      Parameters:
      `events` - The event set recieved.

Skip navigation links

- [Overview](../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../deprecated-list.md)
- [Index](../../../index-all.md)
- [Help](../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](EventIterator.md)**
- **[Next Class](EventListenerIterator.md)**

<!-- -->

- **[Frames](../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../allclasses-noframe.md)**

<!-- -->

- **Summary: **
- **Nested \| **
- **Field \| **
- **Constr \| **
- **Method**

<!-- -->

- **Detail: **
- **Field \| **
- **Constr \| **
- **Method**

**Copyright © 2004-2005 Day Software Management AG. All Rights Reserved.**
