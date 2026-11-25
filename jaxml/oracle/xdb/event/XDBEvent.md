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

- **[Prev Class](XDBBasicEventListener.md)**
- **[Next Class](XDBHandler.md)**

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

## **Class XDBEvent**

- **java.lang.Object**

- - **oracle.xdb.event.XDBEvent**

<!-- -->

- **Direct Known Subclasses:**
  **[XDBRepositoryEvent](XDBRepositoryEvent.md)**

  ------------------------------------------------------------------------

  **
  **

      public class XDBEvent
      extends java.lang.Object

  **This class stores the information about the event that is fired.**
  **Since:**
  **11.1.0.0.0**

<!-- -->

-
  -

    ### **Field Summary**

    **Fields**

    | Modifier and Type | Field and Description                                                                                                        |
    |-------------------|------------------------------------------------------------------------------------------------------------------------------|
    | `static int`      | `POST_CHECKIN_EVENT`<br>Event fired after the checkin of a resource.                                                         |
    | `static int`      | `POST_CHECKOUT_EVENT`<br>Event fired after the checkeout of a resource.                                                      |
    | `static int`      | `POST_CREATE_EVENT`<br>Event fired after a resource is created.                                                              |
    | `static int`      | `POST_DELETE_EVENT`<br>Event fired after a resource is deleted.                                                              |
    | `static int`      | `POST_INCONUPDATE_EVENT`<br>Event fired after an incosistent update using NFS.                                               |
    | `static int`      | `POST_LINKIN_EVENT`<br>Event fired for the folder resource in which a new link is created, after the creation of the link.   |
    | `static int`      | `POST_LINKTO_EVENT`<br>Event fired for the target resource to which a new link is created, after the creation of the link.   |
    | `static int`      | `POST_LOCK_EVENT`<br>Event fired after a resource is locked.                                                                 |
    | `static int`      | `POST_OPEN_EVENT`<br>Event fired after an open using NFS.                                                                    |
    | `static int`      | `POST_UNCHECKOUT_EVENT`<br>Event fired after an uncheckout of a resource.                                                    |
    | `static int`      | `POST_UNLINKFROM_EVENT`<br>Event fired for the target resource when one of its links is deleted, after the unlink operation. |
    | `static int`      | `POST_UNLINKIN_EVENT`<br>Event fired for the folder resource from which a link is removed, after the unlink operation.       |
    | `static int`      | `POST_UNLOCK_EVENT`<br>Event fired after a resource is unlocked.                                                             |
    | `static int`      | `POST_UPDATE_EVENT`<br>Event fired after an update of a resource.                                                            |
    | `static int`      | `POST_VERSIONCONTROL_EVENT`<br>Event fired after version control operation on a resource.                                    |
    | `static int`      | `PRE_CHECKIN_EVENT`<br>Event fired before the checkin of a resource.                                                         |
    | `static int`      | `PRE_CHECKOUT_EVENT`<br>Event fired before the checkout of a resource.                                                       |
    | `static int`      | `PRE_CREATE_EVENT`<br>Event fired before a resource is created.                                                              |
    | `static int`      | `PRE_DELETE_EVENT`<br>Event fired before a resource is deleted.                                                              |
    | `static int`      | `PRE_INCONUPDATE_EVENT`<br>Event fired before an inconsistent update using NFS.                                              |
    | `static int`      | `PRE_LINKIN_EVENT`<br>Event fired for the folder resource in which a new link is created, before the creation of the link.   |
    | `static int`      | `PRE_LINKTO_EVENT`<br>Event fired for the target resource to which a new link is created, before the creation of the link.   |
    | `static int`      | `PRE_LOCK_EVENT`<br>Event fired before a resource is locked.                                                                 |
    | `static int`      | `PRE_OPEN_EVENT`<br>Event fired before an open using NFS.                                                                    |
    | `static int`      | `PRE_UNCHECKOUT_EVENT`<br>Event fired before an uncheckout of a resource.                                                    |
    | `static int`      | `PRE_UNLINKFROM_EVENT`<br>Event fired for the target resource when one of its links is deleted, before the unlink operation. |
    | `static int`      | `PRE_UNLINKIN_EVENT`<br>Event fired for the folder resource from which a link is removed, before the unlink operation.       |
    | `static int`      | `PRE_UNLOCK_EVENT`<br>Event fired before a resource is unlocked.                                                             |
    | `static int`      | `PRE_UPDATE_EVENT`<br>Event fired before an update of a resource.                                                            |
    | `static int`      | `PRE_VERSIONCONTROL_EVENT`<br>Event fired before version control operation on a resource.                                    |
    | `static int`      | `RENDER_EVENT`<br>Event fired when a resource is rendered.                                                                   |

  <!-- -->

  -

    ### **Method Summary**

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type  | Method and Description                                                                                 |
    |--------------------|--------------------------------------------------------------------------------------------------------|
    | `java.lang.String` | `getCurrentUser``()`<br>Returns the name of the user executing the operation that triggered the event. |
    | `int`              | `getEvent``()`<br>Returns event type of the triggering event                                           |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### RENDER_EVENT

          public static final int RENDER_EVENT

      Event fired when a resource is rendered. This event is used by event handlers.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PRE_CREATE_EVENT

          public static final int PRE_CREATE_EVENT

      Event fired before a resource is created. This event is used by event handlers.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### POST_CREATE_EVENT

          public static final int POST_CREATE_EVENT

      Event fired after a resource is created. This event is used by event handlers.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PRE_DELETE_EVENT

          public static final int PRE_DELETE_EVENT

      Event fired before a resource is deleted. This event is used by event handlers.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### POST_DELETE_EVENT

          public static final int POST_DELETE_EVENT

      Event fired after a resource is deleted. This event is used by event handlers.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PRE_UPDATE_EVENT

          public static final int PRE_UPDATE_EVENT

      Event fired before an update of a resource. This event is used by event handlers.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### POST_UPDATE_EVENT

          public static final int POST_UPDATE_EVENT

      Event fired after an update of a resource. This event is used by event handlers.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PRE_LOCK_EVENT

          public static final int PRE_LOCK_EVENT

      Event fired before a resource is locked. This event is used by event handlers.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### POST_LOCK_EVENT

          public static final int POST_LOCK_EVENT

      Event fired after a resource is locked. This event is used by event handlers.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PRE_UNLOCK_EVENT

          public static final int PRE_UNLOCK_EVENT

      Event fired before a resource is unlocked. This event is used by event handlers.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### POST_UNLOCK_EVENT

          public static final int POST_UNLOCK_EVENT

      Event fired after a resource is unlocked. This event is used by event handlers.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PRE_LINKIN_EVENT

          public static final int PRE_LINKIN_EVENT

      Event fired for the folder resource in which a new link is created, before the creation of the link. This event is used by event handlers.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### POST_LINKIN_EVENT

          public static final int POST_LINKIN_EVENT

      Event fired for the folder resource in which a new link is created, after the creation of the link. This event is used by event handlers.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PRE_LINKTO_EVENT

          public static final int PRE_LINKTO_EVENT

      Event fired for the target resource to which a new link is created, before the creation of the link. This event is used by event handlers.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### POST_LINKTO_EVENT

          public static final int POST_LINKTO_EVENT

      Event fired for the target resource to which a new link is created, after the creation of the link. This event is used by event handlers.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PRE_UNLINKIN_EVENT

          public static final int PRE_UNLINKIN_EVENT

      Event fired for the folder resource from which a link is removed, before the unlink operation. This event is used by event handlers.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### POST_UNLINKIN_EVENT

          public static final int POST_UNLINKIN_EVENT

      Event fired for the folder resource from which a link is removed, after the unlink operation. This event is used by event handlers.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PRE_UNLINKFROM_EVENT

          public static final int PRE_UNLINKFROM_EVENT

      Event fired for the target resource when one of its links is deleted, before the unlink operation. This event is used by event handlers.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### POST_UNLINKFROM_EVENT

          public static final int POST_UNLINKFROM_EVENT

      Event fired for the target resource when one of its links is deleted, after the unlink operation. This event is used by event handlers.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PRE_CHECKIN_EVENT

          public static final int PRE_CHECKIN_EVENT

      Event fired before the checkin of a resource. This event is used by event handlers.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### POST_CHECKIN_EVENT

          public static final int POST_CHECKIN_EVENT

      Event fired after the checkin of a resource. This event is used by event handlers.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PRE_CHECKOUT_EVENT

          public static final int PRE_CHECKOUT_EVENT

      Event fired before the checkout of a resource. This event is used by event handlers.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### POST_CHECKOUT_EVENT

          public static final int POST_CHECKOUT_EVENT

      Event fired after the checkeout of a resource. This event is used by event handlers.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PRE_UNCHECKOUT_EVENT

          public static final int PRE_UNCHECKOUT_EVENT

      Event fired before an uncheckout of a resource. This event is used by event handlers.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### POST_UNCHECKOUT_EVENT

          public static final int POST_UNCHECKOUT_EVENT

      Event fired after an uncheckout of a resource. This event is used by event handlers.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PRE_VERSIONCONTROL_EVENT

          public static final int PRE_VERSIONCONTROL_EVENT

      Event fired before version control operation on a resource. This event is used by event handlers.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### POST_VERSIONCONTROL_EVENT

          public static final int POST_VERSIONCONTROL_EVENT

      Event fired after version control operation on a resource. This event is used by event handlers.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PRE_OPEN_EVENT

          public static final int PRE_OPEN_EVENT

      Event fired before an open using NFS. This event is used by event handlers.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### POST_OPEN_EVENT

          public static final int POST_OPEN_EVENT

      Event fired after an open using NFS. This event is used by event handlers.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### PRE_INCONUPDATE_EVENT

          public static final int PRE_INCONUPDATE_EVENT

      Event fired before an inconsistent update using NFS. This event is used by event handlers.
      See Also:
      [Constant Field Values](../../../constant-values.md)

    <!-- -->

    - #### POST_INCONUPDATE_EVENT

          public static final int POST_INCONUPDATE_EVENT

      Event fired after an incosistent update using NFS. This event is used by event handlers.
      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### getCurrentUser

          public java.lang.String getCurrentUser()

      Returns the name of the user executing the operation that triggered the event.
      Returns:
      name of the user

    <!-- -->

    - #### getEvent

          public int getEvent()

      Returns event type of the triggering event
      Returns:
      event ID

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

- **[Prev Class](XDBBasicEventListener.md)**
- **[Next Class](XDBHandler.md)**

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
