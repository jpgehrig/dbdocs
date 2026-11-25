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

- Prev Class
- [Next Class](FanEventListener.md)

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

## Class FanEvent

- java.lang.Object

- - java.util.EventObject

  - - oracle.simplefan.FanEvent

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  <!-- -->

  Direct Known Subclasses:
  [LoadAdvisoryEvent](LoadAdvisoryEvent.md), [NodeDownEvent](NodeDownEvent.md), [NodeUpEvent](NodeUpEvent.md), [ServiceDownEvent](ServiceDownEvent.md), [ServiceUpEvent](ServiceUpEvent.md)

  ------------------------------------------------------------------------



      public abstract class FanEvent
      extends java.util.EventObject

  This abstract class supports three types of FAN events: service events, node down events, and load advisory (RLB) events.
  Since:
  11.2

  Version:
  \$Header: dbjava/simplefan/src/java/oracle/simplefan/FanEvent.java /main/2 2009/07/06 13:04:13 rhward Exp \$

  Author:
  dsurber

  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type | Method and Description                                     |
    |-------------------|------------------------------------------------------------|
    | `java.util.Date`  | `getTimestamp``()`<br>Returns the time the event occurred. |

    - ### Methods inherited from class java.util.EventObject

      `getSource, toString`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getTimestamp

          public java.util.Date getTimestamp()

      Returns the time the event occurred.
      Returns:
      the time the event occurred.

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

- Prev Class
- [Next Class](FanEventListener.md)

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
