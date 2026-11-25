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

- [Prev Class](FanSubscription.md)
- [Next Class](LoadAdvisoryEvent.md)

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

## Interface FanUpEventListener

- All Superinterfaces:
  java.util.EventListener, [FanEventListener](FanEventListener.md)

  ------------------------------------------------------------------------



      public interface FanUpEventListener
      extends FanEventListener

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                                 |
    |-------------------|--------------------------------------------------------------------------------------------------------|
    | `void`            | `handleEvent``(`[`NodeUpEvent`](NodeUpEvent.md)` event)`<br>This method handles NodeUpEvents.          |
    | `void`            | `handleEvent``(`[`ServiceUpEvent`](ServiceUpEvent.md)` event)`<br>This method handles ServiceUpEvents. |

    - ### Methods inherited from interface oracle.simplefan.[FanEventListener](FanEventListener.md)

      [`handleEvent`](FanEventListener.md)`, `[`handleEvent`](FanEventListener.md)`, `[`handleEvent`](FanEventListener.md)

<!-- -->

- - ### Method Detail

    - #### handleEvent

          void handleEvent(ServiceUpEvent event)

      This method handles ServiceUpEvents. This method should return quickly. If it cannot do so, then it should start its work in another thread. If this method does not return quickly, it will delay processing of this and subsequent FAN events. The argument can be captured.
      ServiceUpEvent gets generated on any

          service

      getting up and running on any instance. By implementing this method, the client take advantage of this service.
      Parameters:
      `event` - the attributes of the FAN event.

    <!-- -->

    - #### handleEvent

          void handleEvent(NodeUpEvent event)

      This method handles NodeUpEvents. This method should return quickly. If it cannot do so, then it should start its work in another thread. If this method does not return quickly, it will delay processing of this and subsequent FAN events. The argument can be captured.
      NodeUpEvent gets generated on any

          Instance

      getting up and running. By implementing this method, the client can take advantage of this Instance.
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

- [Prev Class](FanSubscription.md)
- [Next Class](LoadAdvisoryEvent.md)

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
