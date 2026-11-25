Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](EventException.md)**
- **[Next Class](EventTarget.md)**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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

**org.w3c.dom.events**

## **Interface EventListener**

-

  ------------------------------------------------------------------------

  **
  **

      public interface EventListener

  **The `EventListener` interface is the primary method for handling events. Users implement the `EventListener` interface and register their listener on an `EventTarget` using the `AddEventListener` method. The users should also remove their `EventListener` from its `EventTarget` after they have completed using the listener.**
  **When a `Node` is copied using the `cloneNode` method the `EventListener`s attached to the source `Node` are not attached to the copied `Node`. If the user wishes the same `EventListener`s to be added to the newly created copy the user must add them manually.**

  **See also the [Document Object Model (DOM) Level 2 Events Specification](http://www.w3.org/TR/2000/REC-DOM-Level-2-Events-20001113).**

  **Since:**
  **DOM Level 2**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                                           |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `handleEvent``(`[`Event`](Event.md)` evt)`<br>This method is called whenever an event occurs of the type for which the `EventListener` interface was registered. |

<!-- -->

- - ### Method Detail

    - #### handleEvent

          void handleEvent(Event evt)

      This method is called whenever an event occurs of the type for which the `EventListener` interface was registered.
      Parameters:
      `evt` - The `Event` contains contextual information about the event. It also contains the `stopPropagation` and `preventDefault` methods which are used in determining the event's flow and default action.

Skip navigation links

- [Overview](../../../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../../../deprecated-list.md)
- [Index](../../../../index-all.md)
- [Help](../../../../help-doc.md)

**Oracle® Database XML Java API Reference
Release 19*c*
E96475-03
**

- **[Prev Class](EventException.md)**
- **[Next Class](EventTarget.md)**

<!-- -->

- **[Frames](../../../../index.md)**
- **No Frames**

<!-- -->

- **[All Classes](../../../../allclasses-noframe.md)**

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

**Copyright © 2000 [W3C](http://www.w3.org/)<sup>®</sup> ([MIT](http://www.csail.mit.edu/), [INRIA](http://www.inria.fr/), [Keio](http://www.keio.ac.jp/)), All Rights Reserved. W3C [liability](http://www.w3.org/Consortium/Legal/2002/ipr-notice-20021231), [trademark](http://www.w3.org/Consortium/Legal/2002/ipr-notice-20021231), [document use](http://www.w3.org/Consortium/Legal/copyright-documents-19990405) and [software licensing](http://www.w3.org/Consortium/Legal/copyright-software-19980720) rules apply. This document has been reviewed by W3C Members and other interested parties and has been endorsed by the Director as a [W3C Recommendation](http://www.w3.org/Consortium/Process/Process-19991111/tr.html#RecsW3C).**
