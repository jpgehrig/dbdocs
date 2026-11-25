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

- [Prev Class](FanUpEventListener.md)
- [Next Class](LoadAdvisoryEvent.LoadStatus.md)

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

## Class LoadAdvisoryEvent

- java.lang.Object

- - java.util.EventObject

  - - [oracle.simplefan.FanEvent](FanEvent.md)

    - - oracle.simplefan.LoadAdvisoryEvent

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, java.lang.Cloneable

  ------------------------------------------------------------------------



      public abstract class LoadAdvisoryEvent
      extends FanEvent
      implements java.lang.Cloneable, java.io.Serializable

  This FAN event provides advice that directs load balancing for subscribers.
  Since:
  11.2

  Version:
  \$Header: dbjava/simplefan/src/java/oracle/simplefan/LoadAdvisoryEvent.java /main/3 2015/09/09 23:06:27 vidnayak Exp \$

  Author:
  dsurber

  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Nested Class Summary

    **Nested Classes**

    | Modifier and Type | Class and Description                                              |
    |-------------------|--------------------------------------------------------------------|
    | `static class `   | [`LoadAdvisoryEvent.LoadStatus`](LoadAdvisoryEvent.LoadStatus.md)  |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                                                            | Method and Description       |
    |------------------------------------------------------------------------------|------------------------------|
    | `abstract java.lang.String`                                                  | `getDatabaseUniqueName``()`  |
    | `abstract java.lang.String`                                                  | `getInstanceName``()`        |
    | `abstract `[`LoadAdvisoryEvent.LoadStatus`](LoadAdvisoryEvent.LoadStatus.md) | `getLoadStatus``()`          |
    | `abstract int`                                                               | `getPercent``()`             |
    | `abstract java.lang.String`                                                  | `getServiceName``()`         |
    | `abstract int`                                                               | `getServiceQuality``()`      |

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

    - #### getServiceName

          public abstract java.lang.String getServiceName()

      Returns:
      service name

    <!-- -->

    - #### getDatabaseUniqueName

          public abstract java.lang.String getDatabaseUniqueName()

      Returns:
      database unique name

    <!-- -->

    - #### getInstanceName

          public abstract java.lang.String getInstanceName()

      Returns:
      Instance name

    <!-- -->

    - #### getPercent

          public abstract int getPercent()

      Returns:
      percent

    <!-- -->

    - #### getServiceQuality

          public abstract int getServiceQuality()

      Returns:
      service quality

    <!-- -->

    - #### getLoadStatus

          public abstract LoadAdvisoryEvent.LoadStatus getLoadStatus()

      Returns:
      load status

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

- [Prev Class](FanUpEventListener.md)
- [Next Class](LoadAdvisoryEvent.LoadStatus.md)

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
