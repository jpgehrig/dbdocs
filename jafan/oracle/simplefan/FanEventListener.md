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

- [Prev Class](FanEvent.md)
- [Next Class](FanManager.md)

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

## Interface FanEventListener

- All Superinterfaces:
  java.util.EventListener

  <!-- -->

  All Known Subinterfaces:
  [FanUpEventListener](FanUpEventListener.md)

  ------------------------------------------------------------------------



      public interface FanEventListener
      extends java.util.EventListener

  Since:
  11.2

  Version:
  \$Header: dbjava/simplefan/src/java/oracle/simplefan/FanEventListener.java /main/2 2009/07/06 13:04:13 rhward Exp \$

  Author:
  dsurber

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                    |
    |-------------------|-------------------------------------------------------------------------------------------|
    | `void`            | `handleEvent``(`[`LoadAdvisoryEvent`](LoadAdvisoryEvent.md)` event)`<br>Handle the event. |
    | `void`            | `handleEvent``(`[`NodeDownEvent`](NodeDownEvent.md)` event)`<br>Handle the event.         |
    | `void`            | `handleEvent``(`[`ServiceDownEvent`](ServiceDownEvent.md)` event)`<br>Handle the event.   |

<!-- -->

- - ### Method Detail

    - #### handleEvent

          void handleEvent(ServiceDownEvent event)

      Handle the event. This method should return quickly. If it cannot do so, then it should start its work in another thread. If this method does not return quickly, it will delay processing of this and subsequent FAN events. The argument can be captured.
      Parameters:
      `event` - the attributes of the FAN event.

    <!-- -->

    - #### handleEvent

          void handleEvent(NodeDownEvent event)

      Handle the event. This method should return quickly. If it cannot do so, then it should start its work in another thread. If this method does not return quickly, it will delay processing of this and subsequent FAN events. The argument can be captured.
      Parameters:
      `event` - the attributes of the FAN event.

    <!-- -->

    - #### handleEvent

          void handleEvent(LoadAdvisoryEvent event)

      Handle the event. This method should return quickly. If it cannot do so, then it should start its work in another thread. If this method does not return quickly, it will delay processing of this and subsequent FAN events. The argument can be captured.
      Parameters:
      `event` - the attributes of the FAN event.

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

- [Prev Class](FanEvent.md)
- [Next Class](FanManager.md)

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
