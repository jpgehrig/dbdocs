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

- **[Prev Class](EventListener.md)**
- **[Next Class](MutationEvent.md)**

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

## **Interface EventTarget**

- **All Known Implementing Classes:**
  **[AttrDecl](../../../../oracle/xml/parser/v2/AttrDecl.md), [DTD](../../../../oracle/xml/parser/v2/DTD.md), [ElementDecl](../../../../oracle/xml/parser/v2/ElementDecl.md), [XMLAttr](../../../../oracle/xml/parser/v2/XMLAttr.md), [XMLCDATA](../../../../oracle/xml/parser/v2/XMLCDATA.md), [XMLComment](../../../../oracle/xml/parser/v2/XMLComment.md), [XMLDeclPI](../../../../oracle/xml/parser/v2/XMLDeclPI.md), [XMLDocument](../../../../oracle/xml/parser/v2/XMLDocument.md), [XMLDocumentFragment](../../../../oracle/xml/parser/v2/XMLDocumentFragment.md), [XMLElement](../../../../oracle/xml/parser/v2/XMLElement.md), [XMLEntity](../../../../oracle/xml/parser/v2/XMLEntity.md), [XMLEntityReference](../../../../oracle/xml/parser/v2/XMLEntityReference.md), [XMLNode](../../../../oracle/xml/parser/v2/XMLNode.md), [XMLNotation](../../../../oracle/xml/parser/v2/XMLNotation.md), [XMLNSNode](../../../../oracle/xml/parser/v2/XMLNSNode.md), [XMLPI](../../../../oracle/xml/parser/v2/XMLPI.md), [XMLText](../../../../oracle/xml/parser/v2/XMLText.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface EventTarget

  **The `EventTarget` interface is implemented by all `Nodes` in an implementation which supports the DOM Event Model. Therefore, this interface can be obtained by using binding-specific casting methods on an instance of the `Node` interface. The interface allows registration and removal of `EventListeners` on an `EventTarget` and dispatch of events to that `EventTarget`.**
  **See also the [Document Object Model (DOM) Level 2 Events Specification](http://www.w3.org/TR/2000/REC-DOM-Level-2-Events-20001113).**

  **Since:**
  **DOM Level 2**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                                                                                         |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `addEventListener``(java.lang.String type, `[`EventListener`](EventListener.md)` listener, boolean useCapture)`<br>This method allows the registration of event listeners on the event target. |
    | `boolean`         | `dispatchEvent``(`[`Event`](Event.md)` evt)`<br>This method allows the dispatch of events into the implementations event model.                                                                |
    | `void`            | `removeEventListener``(java.lang.String type, `[`EventListener`](EventListener.md)` listener, boolean useCapture)`<br>This method allows the removal of event listeners from the event target. |

<!-- -->

- - ### Method Detail

    - #### addEventListener

          void addEventListener(java.lang.String type,
                                EventListener listener,
                                boolean useCapture)

      This method allows the registration of event listeners on the event target. If an `EventListener` is added to an `EventTarget` while it is processing an event, it will not be triggered by the current actions but may be triggered during a later stage of event flow, such as the bubbling phase.
      If multiple identical `EventListener`s are registered on the same `EventTarget` with the same parameters the duplicate instances are discarded. They do not cause the `EventListener` to be called twice and since they are discarded they do not need to be removed with the `removeEventListener` method.
      Parameters:
      `type` - The event type for which the user is registering

      `listener` - The `listener` parameter takes an interface implemented by the user which contains the methods to be called when the event occurs.

      `useCapture` - If true, `useCapture` indicates that the user wishes to initiate capture. After initiating capture, all events of the specified type will be dispatched to the registered `EventListener` before being dispatched to any `EventTargets` beneath them in the tree. Events which are bubbling upward through the tree will not trigger an `EventListener` designated to use capture.

    <!-- -->

    - #### removeEventListener

          void removeEventListener(java.lang.String type,
                                   EventListener listener,
                                   boolean useCapture)

      This method allows the removal of event listeners from the event target. If an `EventListener` is removed from an `EventTarget` while it is processing an event, it will not be triggered by the current actions. `EventListener`s can never be invoked after being removed.
      Calling `removeEventListener` with arguments which do not identify any currently registered `EventListener` on the `EventTarget` has no effect.
      Parameters:
      `type` - Specifies the event type of the `EventListener` being removed.

      `listener` - The `EventListener` parameter indicates the `EventListener` to be removed.

      `useCapture` - Specifies whether the `EventListener` being removed was registered as a capturing listener or not. If a listener was registered twice, one with capture and one without, each must be removed separately. Removal of a capturing listener does not affect a non-capturing version of the same listener, and vice versa.

    <!-- -->

    - #### dispatchEvent

          boolean dispatchEvent(Event evt)
                         throws EventException

      This method allows the dispatch of events into the implementations event model. Events dispatched in this manner will have the same capturing and bubbling behavior as events dispatched directly by the implementation. The target of the event is the `EventTarget` on which `dispatchEvent` is called.
      Parameters:
      `evt` - Specifies the event type, behavior, and contextual information to be used in processing the event.

      Returns:
      The return value of `dispatchEvent` indicates whether any of the listeners which handled the event called `preventDefault`. If `preventDefault` was called the value is false, else the value is true.

      Throws:
      [`EventException`](EventException.md) - UNSPECIFIED_EVENT_TYPE_ERR: Raised if the `Event`'s type was not specified by initializing the event before `dispatchEvent` was called. Specification of the `Event`'s type as `null` or an empty string will also trigger this exception.

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

- **[Prev Class](EventListener.md)**
- **[Next Class](MutationEvent.md)**

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
