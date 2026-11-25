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

- **[Prev Class](XDBRepositoryEvent.md)**
- **Next Class**

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

**oracle.xdb.event**

## **Interface XDBRepositoryEventListener**

- **All Known Implementing Classes:**
  **[XDBBasicEventListener](XDBBasicEventListener.md)**

  ------------------------------------------------------------------------

  **
  **

      public interface XDBRepositoryEventListener

  **Interface for Java handlers. Oracle XML Database event handlers written in Java must implement this interface, and the implementation class must provide a public zero-argument constructor.**
  **Since:**
  **11.1.0.0.0**

<!-- -->

-
  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                                     |
    |-------------------|----------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `handlePostCheckIn``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handler for Post-checkin event       |
    | `void`            | `handlePostCheckOut``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handler for Post-checkout event     |
    | `void`            | `handlePostCreate``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handler for Post-create event         |
    | `void`            | `handlePostDelete``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handler for Post-delete event         |
    | `void`            | `handlePostLinkIn``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handler for Post-linkin event         |
    | `void`            | `handlePostLinkTo``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handler for Post-linkto event         |
    | `void`            | `handlePostLock``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handler for Post-lock event             |
    | `void`            | `handlePostUnlinkFrom``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handler for Post-unlinkfrom event |
    | `void`            | `handlePostUnlinkIn``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handler for Post-unlinkin event     |
    | `void`            | `handlePostUnlock``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handler for Post-unlock event         |
    | `void`            | `handlePostUpdate``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handler for Post-update event         |
    | `void`            | `handlePreCheckIn``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handler for Pre-checkin event         |
    | `void`            | `handlePreCheckOut``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handler for Pre-checkout event       |
    | `void`            | `handlePreCreate``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handler for Pre-create event           |
    | `void`            | `handlePreDelete``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handler for Pre-delete event           |
    | `void`            | `handlePreLinkIn``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handler for Pre-linkin event           |
    | `void`            | `handlePreLinkTo``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handler for Pre-linto event            |
    | `void`            | `handlePreLock``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handler for Pre-lock event               |
    | `void`            | `handlePreUnlinkFrom``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handler for Pre-unlinkfrom event   |
    | `void`            | `handlePreUnlinkIn``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handler for Pre-unlinkin event       |
    | `void`            | `handlePreUnlock``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handler for Pre-unlock event           |
    | `void`            | `handlePreUpdate``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handler for Pre-update event           |
    | `void`            | `handleRender``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handler for Render event                  |

<!-- -->

- - ### Method Detail

    - #### handleRender

          void handleRender(XDBRepositoryEvent eventObject)

      Handler for Render event
      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePreCreate

          void handlePreCreate(XDBRepositoryEvent eventObject)

      Handler for Pre-create event
      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePostCreate

          void handlePostCreate(XDBRepositoryEvent eventObject)

      Handler for Post-create event
      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePreDelete

          void handlePreDelete(XDBRepositoryEvent eventObject)

      Handler for Pre-delete event
      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePostDelete

          void handlePostDelete(XDBRepositoryEvent eventObject)

      Handler for Post-delete event
      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePreUpdate

          void handlePreUpdate(XDBRepositoryEvent eventObject)

      Handler for Pre-update event
      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePostUpdate

          void handlePostUpdate(XDBRepositoryEvent eventObject)

      Handler for Post-update event
      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePreLock

          void handlePreLock(XDBRepositoryEvent eventObject)

      Handler for Pre-lock event
      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePostLock

          void handlePostLock(XDBRepositoryEvent eventObject)

      Handler for Post-lock event
      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePreUnlock

          void handlePreUnlock(XDBRepositoryEvent eventObject)

      Handler for Pre-unlock event
      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePostUnlock

          void handlePostUnlock(XDBRepositoryEvent eventObject)

      Handler for Post-unlock event
      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePreLinkIn

          void handlePreLinkIn(XDBRepositoryEvent eventObject)

      Handler for Pre-linkin event
      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePostLinkIn

          void handlePostLinkIn(XDBRepositoryEvent eventObject)

      Handler for Post-linkin event
      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePreLinkTo

          void handlePreLinkTo(XDBRepositoryEvent eventObject)

      Handler for Pre-linto event
      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePostLinkTo

          void handlePostLinkTo(XDBRepositoryEvent eventObject)

      Handler for Post-linkto event
      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePreUnlinkIn

          void handlePreUnlinkIn(XDBRepositoryEvent eventObject)

      Handler for Pre-unlinkin event
      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePostUnlinkIn

          void handlePostUnlinkIn(XDBRepositoryEvent eventObject)

      Handler for Post-unlinkin event
      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePreUnlinkFrom

          void handlePreUnlinkFrom(XDBRepositoryEvent eventObject)

      Handler for Pre-unlinkfrom event
      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePostUnlinkFrom

          void handlePostUnlinkFrom(XDBRepositoryEvent eventObject)

      Handler for Post-unlinkfrom event
      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePreCheckIn

          void handlePreCheckIn(XDBRepositoryEvent eventObject)

      Handler for Pre-checkin event
      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePostCheckIn

          void handlePostCheckIn(XDBRepositoryEvent eventObject)

      Handler for Post-checkin event
      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePreCheckOut

          void handlePreCheckOut(XDBRepositoryEvent eventObject)

      Handler for Pre-checkout event
      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePostCheckOut

          void handlePostCheckOut(XDBRepositoryEvent eventObject)

      Handler for Post-checkout event
      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

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

- **[Prev Class](XDBRepositoryEvent.md)**
- **Next Class**

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

**Copyright © 2003, 2019, Oracle and/or its affiliates. All rights reserved.
Use is subject to license terms. Also see the documentation redistribution policy.
ORACLE CONFIDENTIAL
For authorized use only.
Do not distribute to third parties.**
