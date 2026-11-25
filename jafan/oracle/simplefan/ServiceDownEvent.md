Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database RAC FAN Events Java API Reference
19c**
E96462-02

- [Prev Class](NodeUpEvent.md)
- [Next Class](ServiceDownEvent.EventKind.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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

oracle.simplefan

## Class ServiceDownEvent

- java.lang.Object

- - java.util.EventObject

  - - [oracle.simplefan.FanEvent](FanEvent.md)

    - - oracle.simplefan.ServiceDownEvent

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.lang.Cloneable

  ------------------------------------------------------------------------



      public abstract class ServiceDownEvent
      extends FanEvent
      implements java.lang.Cloneable, java.io.Serializable

  A container that can hold both kinds of service events. The service member and service composite events can either arrive separately or combined in a single event.
  Since:
  11.2

  Version:
  \$Header: dbjava/simplefan/src/java/oracle/simplefan/ServiceDownEvent.java /main/4 2016/02/26 12:44:18 tzhou Exp \$

  Author:
  dsurber

  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Class and Description                                                                                                                                                                         |
    |-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static class `   | [`ServiceDownEvent.EventKind`](ServiceDownEvent.EventKind.md)                                                                                                                                 |
    | `static class `   | [`ServiceDownEvent.Reason`](ServiceDownEvent.Reason.md)                                                                                                                                       |
    | `static class `   | [`ServiceDownEvent.ServiceMemberEvent`](ServiceDownEvent.ServiceMemberEvent.md)<br>The service member event that reflects the status change of a service on a particular instance (and node). |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                          | Method and Description                                                                                           |
    |--------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------|
    | `abstract java.lang.String`                                                                | `getDatabaseUniqueName``()`                                                                                      |
    | `abstract int`                                                                             | `getDrainTimeout``()`                                                                                            |
    | `abstract `[`ServiceDownEvent.EventKind`](ServiceDownEvent.EventKind.md)                   | `getKind``()`<br>Service down events can be member down, composite down, or both.                                |
    | `abstract `[`ServiceDownEvent.Reason`](ServiceDownEvent.Reason.md)                         | `getReason``()`                                                                                                  |
    | `abstract `[`ServiceDownEvent.ServiceMemberEvent`](ServiceDownEvent.ServiceMemberEvent.md) | `getServiceMemberEvent``()`<br>Return the service member subevent information if this is a service member event. |
    | `abstract java.lang.String`                                                                | `getServiceName``()`                                                                                             |

    - ### Methods inherited from class oracle.simplefan.[FanEvent](FanEvent.md)

      [`getTimestamp`](FanEvent.md)

    <!-- -->

    - ### Methods inherited from class java.util.EventObject

      `getSource, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getKind

          public abstract ServiceDownEvent.EventKind getKind()

      Service down events can be member down, composite down, or both. This method reports which this is. A member down means just a single member instance of the service is down. A composite down means that all member instances of the service are down and so the service itself is down. A single event can report both the last member down and the composite down. These may also come as separate events.
      Returns:
      the event kind.

    <!-- -->

    - #### getServiceName

          public abstract java.lang.String getServiceName()

      Returns:
      the service name.

    <!-- -->

    - #### getDatabaseUniqueName

          public abstract java.lang.String getDatabaseUniqueName()

      Returns:
      the database unique name.

    <!-- -->

    - #### getReason

          public abstract ServiceDownEvent.Reason getReason()

      Returns:
      the reason for the service going down.

    <!-- -->

    - #### getDrainTimeout

          public abstract int getDrainTimeout()

      Returns:
      The server drain-timeout for the service going down, in seconds.

    <!-- -->

    - #### getServiceMemberEvent

          public abstract ServiceDownEvent.ServiceMemberEvent getServiceMemberEvent()

      Return the service member subevent information if this is a service member event. Returns null if this kind is COMPOSITE. A service event can be either a member or composite event, or both.
      Returns:
      a ServiceMemberEvent or null.

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database RAC FAN Events Java API Reference
19c**
E96462-02

- [Prev Class](NodeUpEvent.md)
- [Next Class](ServiceDownEvent.EventKind.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

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

Oracle and Java are registered trademarks of Oracle and/or its affiliates. Other names may be trademarks of their respective owners.
Copyright © 2008, 2019, Oracle and/or its affiliates. All rights reserved.
