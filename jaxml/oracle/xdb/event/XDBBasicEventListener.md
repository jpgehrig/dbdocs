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

- **Prev Class**
- **[Next Class](XDBEvent.md)**

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

## **Class XDBBasicEventListener**

- **java.lang.Object**

- - **oracle.xdb.event.XDBBasicEventListener**

<!-- -->

- **All Implemented Interfaces:**
  **[XDBRepositoryEventListener](XDBRepositoryEventListener.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XDBBasicEventListener
      extends java.lang.Object
      implements XDBRepositoryEventListener

  **An example class to show how application writers can create there own event listeners.**
  **Since:**
  **11.1.0.0.0**

<!-- -->

-
  -

    ### **Constructor Summary**

    **Constructors**

    | Constructor and Description  |
    |------------------------------|
    | `XDBBasicEventListener``()`  |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                                                                                 |
    |-------------------|------------------------------------------------------------------------------------------------------------------------|
    | `void`            | `handlePostCheckIn``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handle post-checkin event        |
    | `void`            | `handlePostCheckOut``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handle post-checkout event      |
    | `void`            | `handlePostCreate``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handle post-create event          |
    | `void`            | `handlePostDelete``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handle post-delete event          |
    | `void`            | `handlePostLinkIn``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handle post-link-in event         |
    | `void`            | `handlePostLinkTo``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handle post-link-to event         |
    | `void`            | `handlePostLock``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handle post-lock event              |
    | `void`            | `handlePostUnlinkFrom``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handle post-unlink-from event |
    | `void`            | `handlePostUnlinkIn``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handle post-unlink-in event     |
    | `void`            | `handlePostUnlock``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handle post-unlock event          |
    | `void`            | `handlePostUpdate``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handle post-update event          |
    | `void`            | `handlePreCheckIn``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handle pre-checkin event          |
    | `void`            | `handlePreCheckOut``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handle pre-checkout event        |
    | `void`            | `handlePreCreate``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handle pre-create event            |
    | `void`            | `handlePreDelete``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handle pre-delete event            |
    | `void`            | `handlePreLinkIn``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handle pre-link-in event           |
    | `void`            | `handlePreLinkTo``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handle pre-link-to event           |
    | `void`            | `handlePreLock``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handle pre-lock event                |
    | `void`            | `handlePreUnlinkFrom``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handle pre-unlink-from event   |
    | `void`            | `handlePreUnlinkIn``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handle pre-unlink-in event       |
    | `void`            | `handlePreUnlock``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handle pre-unlock event            |
    | `void`            | `handlePreUpdate``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handle pre-update event            |
    | `void`            | `handleRender``(`[`XDBRepositoryEvent`](XDBRepositoryEvent.md)` eventObject)`<br>Handle render event                   |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### XDBBasicEventListener

          public XDBBasicEventListener()

  <!-- -->

  - ### Method Detail

    - #### handleRender

          public void handleRender(XDBRepositoryEvent eventObject)

      Handle render event
      Specified by:
      [`handleRender`](XDBRepositoryEventListener.md) in interface [`XDBRepositoryEventListener`](XDBRepositoryEventListener.md)

      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePreCreate

          public void handlePreCreate(XDBRepositoryEvent eventObject)

      Handle pre-create event
      Specified by:
      [`handlePreCreate`](XDBRepositoryEventListener.md) in interface [`XDBRepositoryEventListener`](XDBRepositoryEventListener.md)

      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePostCreate

          public void handlePostCreate(XDBRepositoryEvent eventObject)

      Handle post-create event
      Specified by:
      [`handlePostCreate`](XDBRepositoryEventListener.md) in interface [`XDBRepositoryEventListener`](XDBRepositoryEventListener.md)

      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePreDelete

          public void handlePreDelete(XDBRepositoryEvent eventObject)

      Handle pre-delete event
      Specified by:
      [`handlePreDelete`](XDBRepositoryEventListener.md) in interface [`XDBRepositoryEventListener`](XDBRepositoryEventListener.md)

      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePostDelete

          public void handlePostDelete(XDBRepositoryEvent eventObject)

      Handle post-delete event
      Specified by:
      [`handlePostDelete`](XDBRepositoryEventListener.md) in interface [`XDBRepositoryEventListener`](XDBRepositoryEventListener.md)

      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePreUpdate

          public void handlePreUpdate(XDBRepositoryEvent eventObject)

      Handle pre-update event
      Specified by:
      [`handlePreUpdate`](XDBRepositoryEventListener.md) in interface [`XDBRepositoryEventListener`](XDBRepositoryEventListener.md)

      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePostUpdate

          public void handlePostUpdate(XDBRepositoryEvent eventObject)

      Handle post-update event
      Specified by:
      [`handlePostUpdate`](XDBRepositoryEventListener.md) in interface [`XDBRepositoryEventListener`](XDBRepositoryEventListener.md)

      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePreLock

          public void handlePreLock(XDBRepositoryEvent eventObject)

      Handle pre-lock event
      Specified by:
      [`handlePreLock`](XDBRepositoryEventListener.md) in interface [`XDBRepositoryEventListener`](XDBRepositoryEventListener.md)

      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePostLock

          public void handlePostLock(XDBRepositoryEvent eventObject)

      Handle post-lock event
      Specified by:
      [`handlePostLock`](XDBRepositoryEventListener.md) in interface [`XDBRepositoryEventListener`](XDBRepositoryEventListener.md)

      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePreUnlock

          public void handlePreUnlock(XDBRepositoryEvent eventObject)

      Handle pre-unlock event
      Specified by:
      [`handlePreUnlock`](XDBRepositoryEventListener.md) in interface [`XDBRepositoryEventListener`](XDBRepositoryEventListener.md)

      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePostUnlock

          public void handlePostUnlock(XDBRepositoryEvent eventObject)

      Handle post-unlock event
      Specified by:
      [`handlePostUnlock`](XDBRepositoryEventListener.md) in interface [`XDBRepositoryEventListener`](XDBRepositoryEventListener.md)

      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePreLinkIn

          public void handlePreLinkIn(XDBRepositoryEvent eventObject)

      Handle pre-link-in event
      Specified by:
      [`handlePreLinkIn`](XDBRepositoryEventListener.md) in interface [`XDBRepositoryEventListener`](XDBRepositoryEventListener.md)

      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePostLinkIn

          public void handlePostLinkIn(XDBRepositoryEvent eventObject)

      Handle post-link-in event
      Specified by:
      [`handlePostLinkIn`](XDBRepositoryEventListener.md) in interface [`XDBRepositoryEventListener`](XDBRepositoryEventListener.md)

      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePreLinkTo

          public void handlePreLinkTo(XDBRepositoryEvent eventObject)

      Handle pre-link-to event
      Specified by:
      [`handlePreLinkTo`](XDBRepositoryEventListener.md) in interface [`XDBRepositoryEventListener`](XDBRepositoryEventListener.md)

      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePostLinkTo

          public void handlePostLinkTo(XDBRepositoryEvent eventObject)

      Handle post-link-to event
      Specified by:
      [`handlePostLinkTo`](XDBRepositoryEventListener.md) in interface [`XDBRepositoryEventListener`](XDBRepositoryEventListener.md)

      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePreUnlinkIn

          public void handlePreUnlinkIn(XDBRepositoryEvent eventObject)

      Handle pre-unlink-in event
      Specified by:
      [`handlePreUnlinkIn`](XDBRepositoryEventListener.md) in interface [`XDBRepositoryEventListener`](XDBRepositoryEventListener.md)

      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePostUnlinkIn

          public void handlePostUnlinkIn(XDBRepositoryEvent eventObject)

      Handle post-unlink-in event
      Specified by:
      [`handlePostUnlinkIn`](XDBRepositoryEventListener.md) in interface [`XDBRepositoryEventListener`](XDBRepositoryEventListener.md)

      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePreUnlinkFrom

          public void handlePreUnlinkFrom(XDBRepositoryEvent eventObject)

      Handle pre-unlink-from event
      Specified by:
      [`handlePreUnlinkFrom`](XDBRepositoryEventListener.md) in interface [`XDBRepositoryEventListener`](XDBRepositoryEventListener.md)

      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePostUnlinkFrom

          public void handlePostUnlinkFrom(XDBRepositoryEvent eventObject)

      Handle post-unlink-from event
      Specified by:
      [`handlePostUnlinkFrom`](XDBRepositoryEventListener.md) in interface [`XDBRepositoryEventListener`](XDBRepositoryEventListener.md)

      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePreCheckIn

          public void handlePreCheckIn(XDBRepositoryEvent eventObject)

      Handle pre-checkin event
      Specified by:
      [`handlePreCheckIn`](XDBRepositoryEventListener.md) in interface [`XDBRepositoryEventListener`](XDBRepositoryEventListener.md)

      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePostCheckIn

          public void handlePostCheckIn(XDBRepositoryEvent eventObject)

      Handle post-checkin event
      Specified by:
      [`handlePostCheckIn`](XDBRepositoryEventListener.md) in interface [`XDBRepositoryEventListener`](XDBRepositoryEventListener.md)

      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePreCheckOut

          public void handlePreCheckOut(XDBRepositoryEvent eventObject)

      Handle pre-checkout event
      Specified by:
      [`handlePreCheckOut`](XDBRepositoryEventListener.md) in interface [`XDBRepositoryEventListener`](XDBRepositoryEventListener.md)

      Parameters:
      `eventObject` - The `XDBRepositoryEvent` passed from the Oracle XML Database events framework to the handler when an event is fired.

    <!-- -->

    - #### handlePostCheckOut

          public void handlePostCheckOut(XDBRepositoryEvent eventObject)

      Handle post-checkout event
      Specified by:
      [`handlePostCheckOut`](XDBRepositoryEventListener.md) in interface [`XDBRepositoryEventListener`](XDBRepositoryEventListener.md)

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

- **Prev Class**
- **[Next Class](XDBEvent.md)**

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
