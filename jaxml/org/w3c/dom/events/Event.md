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

- **[Prev Class](DocumentEvent.md)**
- **[Next Class](EventException.md)**

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

## **Interface Event**

- **All Known Subinterfaces:**
  **[LSLoadEvent](../ls/LSLoadEvent.md), [LSProgressEvent](../ls/LSProgressEvent.md), [MutationEvent](MutationEvent.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface Event

  **The `Event` interface is used to provide contextual information about an event to the handler processing the event. An object which implements the `Event` interface is generally passed as the first parameter to an event handler. More specific context information is passed to event handlers by deriving additional interfaces from `Event` which contain information directly relating to the type of event they accompany. These derived interfaces are also implemented by the object passed to the event listener.**
  **See also the [Document Object Model (DOM) Level 2 Events Specification](http://www.w3.org/TR/2000/REC-DOM-Level-2-Events-20001113).**

  **Since:**
  **DOM Level 2**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description                                                              |
    |-------------------|------------------------------------------------------------------------------------|
    | `static short`    | `AT_TARGET`<br>The event is currently being evaluated at the target `EventTarget`. |
    | `static short`    | `BUBBLING_PHASE`<br>The current event phase is the bubbling phase.                 |
    | `static short`    | `CAPTURING_PHASE`<br>The current event phase is the capturing phase.               |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type               | Method and Description                                                                                                                                                                                                                       |
    |---------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `boolean`                       | `getBubbles``()`<br>Used to indicate whether or not an event is a bubbling event.                                                                                                                                                            |
    | `boolean`                       | `getCancelable``()`<br>Used to indicate whether or not an event can have its default action prevented.                                                                                                                                       |
    | [`EventTarget`](EventTarget.md) | `getCurrentTarget``()`<br>Used to indicate the `EventTarget` whose `EventListeners` are currently being processed.                                                                                                                           |
    | `short`                         | `getEventPhase``()`<br>Used to indicate which phase of event flow is currently being evaluated.                                                                                                                                              |
    | [`EventTarget`](EventTarget.md) | `getTarget``()`<br>Used to indicate the `EventTarget` to which the event was originally dispatched.                                                                                                                                          |
    | `long`                          | `getTimeStamp``()`<br>Used to specify the time (in milliseconds relative to the epoch) at which the event was created.                                                                                                                       |
    | `java.lang.String`              | `getType``()`<br>The name of the event (case-insensitive).                                                                                                                                                                                   |
    | `void`                          | `initEvent``(java.lang.String eventTypeArg, boolean canBubbleArg, boolean cancelableArg)`<br>The `initEvent` method is used to initialize the value of an `Event` created through the `DocumentEvent` interface.                             |
    | `void`                          | `preventDefault``()`<br>If an event is cancelable, the `preventDefault` method is used to signify that the event is to be canceled, meaning any default action normally taken by the implementation as a result of the event will not occur. |
    | `void`                          | `stopPropagation``()`<br>The `stopPropagation` method is used prevent further propagation of an event during event flow.                                                                                                                     |

<!-- -->

- - ### Field Detail

    - #### CAPTURING_PHASE

          static final short CAPTURING_PHASE

      The current event phase is the capturing phase.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### AT_TARGET

          static final short AT_TARGET

      The event is currently being evaluated at the target `EventTarget`.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

    <!-- -->

    - #### BUBBLING_PHASE

          static final short BUBBLING_PHASE

      The current event phase is the bubbling phase.
      See Also:
      [Constant Field Values](../../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getType

          java.lang.String getType()

      The name of the event (case-insensitive). The name must be an XML name.

    <!-- -->

    - #### getTarget

          EventTarget getTarget()

      Used to indicate the `EventTarget` to which the event was originally dispatched.

    <!-- -->

    - #### getCurrentTarget

          EventTarget getCurrentTarget()

      Used to indicate the `EventTarget` whose `EventListeners` are currently being processed. This is particularly useful during capturing and bubbling.

    <!-- -->

    - #### getEventPhase

          short getEventPhase()

      Used to indicate which phase of event flow is currently being evaluated.

    <!-- -->

    - #### getBubbles

          boolean getBubbles()

      Used to indicate whether or not an event is a bubbling event. If the event can bubble the value is true, else the value is false.

    <!-- -->

    - #### getCancelable

          boolean getCancelable()

      Used to indicate whether or not an event can have its default action prevented. If the default action can be prevented the value is true, else the value is false.

    <!-- -->

    - #### getTimeStamp

          long getTimeStamp()

      Used to specify the time (in milliseconds relative to the epoch) at which the event was created. Due to the fact that some systems may not provide this information the value of `timeStamp` may be not available for all events. When not available, a value of 0 will be returned. Examples of epoch time are the time of the system start or 0:0:0 UTC 1st January 1970.

    <!-- -->

    - #### stopPropagation

          void stopPropagation()

      The `stopPropagation` method is used prevent further propagation of an event during event flow. If this method is called by any `EventListener` the event will cease propagating through the tree. The event will complete dispatch to all listeners on the current `EventTarget` before event flow stops. This method may be used during any stage of event flow.

    <!-- -->

    - #### preventDefault

          void preventDefault()

      If an event is cancelable, the `preventDefault` method is used to signify that the event is to be canceled, meaning any default action normally taken by the implementation as a result of the event will not occur. If, during any stage of event flow, the `preventDefault` method is called the event is canceled. Any default action associated with the event will not occur. Calling this method for a non-cancelable event has no effect. Once `preventDefault` has been called it will remain in effect throughout the remainder of the event's propagation. This method may be used during any stage of event flow.

    <!-- -->

    - #### initEvent

          void initEvent(java.lang.String eventTypeArg,
                         boolean canBubbleArg,
                         boolean cancelableArg)

      The `initEvent` method is used to initialize the value of an `Event` created through the `DocumentEvent` interface. This method may only be called before the `Event` has been dispatched via the `dispatchEvent` method, though it may be called multiple times during that phase if necessary. If called multiple times the final invocation takes precedence. If called from a subclass of `Event` interface only the values specified in the `initEvent` method are modified, all other attributes are left unchanged.
      Parameters:
      `eventTypeArg` - Specifies the event type. This type may be any event type currently defined in this specification or a new event type.. The string must be an XML name. Any new event type must not begin with any upper, lower, or mixed case version of the string "DOM". This prefix is reserved for future DOM event sets. It is also strongly recommended that third parties adding their own events use their own prefix to avoid confusion and lessen the probability of conflicts with other new events.

      `canBubbleArg` - Specifies whether or not the event can bubble.

      `cancelableArg` - Specifies whether or not the event's default action can be prevented.

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

- **[Prev Class](DocumentEvent.md)**
- **[Next Class](EventException.md)**

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
