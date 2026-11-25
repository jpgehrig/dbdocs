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

- [Prev Class](ServiceDownEvent.ServiceMemberEvent.md)
- [Next Class](ServiceUpEvent.EventKind.md)

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

## Class ServiceUpEvent

- java.lang.Object

- - java.util.EventObject

  - - [oracle.simplefan.FanEvent](FanEvent.md)

    - - oracle.simplefan.ServiceUpEvent

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.lang.Cloneable

  ------------------------------------------------------------------------



      public abstract class ServiceUpEvent
      extends FanEvent
      implements java.lang.Cloneable, java.io.Serializable

  A container that can hold both kinds of service events. The service member and service composite events can either arrive separately or combined in a single event.
  Since:
  12.2

  Version:
  \$Header: dbjava/simplefan/src/java/oracle/simplefan/ServiceUpEvent.java /main/1 2014/12/10 09:50:33 tzhou Exp \$

  Author:
  tzhou

  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Class and Description                                                                                                                                                                     |
    |-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static class `   | [`ServiceUpEvent.EventKind`](ServiceUpEvent.EventKind.md)                                                                                                                                 |
    | `static class `   | [`ServiceUpEvent.Reason`](ServiceUpEvent.Reason.md)                                                                                                                                       |
    | `static class `   | [`ServiceUpEvent.ServiceMemberEvent`](ServiceUpEvent.ServiceMemberEvent.md)<br>The service member event that reflects the status change of a service on a particular instance (and node). |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                                      | Method and Description                                                                                           |
    |----------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------|
    | `abstract int`                                                                         | `getCardinality``()`                                                                                             |
    | `abstract java.lang.String`                                                            | `getDatabaseUniqueName``()`                                                                                      |
    | `abstract `[`ServiceUpEvent.EventKind`](ServiceUpEvent.EventKind.md)                   | `getKind``()`<br>Service up events can be member up, composite up, or both.                                      |
    | `abstract `[`ServiceUpEvent.Reason`](ServiceUpEvent.Reason.md)                         | `getReason``()`                                                                                                  |
    | `abstract `[`ServiceUpEvent.ServiceMemberEvent`](ServiceUpEvent.ServiceMemberEvent.md) | `getServiceMemberEvent``()`<br>Return the service member subevent information if this is a service member event. |
    | `abstract java.lang.String`                                                            | `getServiceName``()`                                                                                             |

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

          public abstract ServiceUpEvent.EventKind getKind()

      Service up events can be member up, composite up, or both. This method reports which this is. A member up means just a single member instance of the service is up. A composite up means that all member instances of the service are up and so the service itself is up. A single event can report both the last member up and the composite up. These may also come as separate events.
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

          public abstract ServiceUpEvent.Reason getReason()

      Returns:
      the reason for the service going up.

    <!-- -->

    - #### getCardinality

          public abstract int getCardinality()

      Returns:
      the cardinality for the service going up.

    <!-- -->

    - #### getServiceMemberEvent

          public abstract ServiceUpEvent.ServiceMemberEvent getServiceMemberEvent()

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

- [Prev Class](ServiceDownEvent.ServiceMemberEvent.md)
- [Next Class](ServiceUpEvent.EventKind.md)

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
