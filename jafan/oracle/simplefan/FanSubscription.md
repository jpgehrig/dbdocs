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

- [Prev Class](FanManager.md)
- [Next Class](FanUpEventListener.md)

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

## Interface FanSubscription

-

  ------------------------------------------------------------------------



      public interface FanSubscription

  Since:
  11.2

  Version:
  \$Header: dbjava/simplefan/src/java/oracle/simplefan/FanSubscription.java /main/2 2009/07/06 13:04:13 rhward Exp \$

  Author:
  dsurber

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                          |
    |-------------------|-------------------------------------------------------------------------------------------------|
    | `void`            | `addListener``(`[`FanEventListener`](FanEventListener.md)` listener)`<br>Adds a listener.       |
    | `void`            | `close``()`<br>Closes this subscription.                                                        |
    | `void`            | `removeListener``(`[`FanEventListener`](FanEventListener.md)` listener)`<br>Removes a listener. |

<!-- -->

- - ### Method Detail

    - #### addListener

          void addListener(FanEventListener listener)

      Adds a listener. Listeners are called in the order added. The argument is captured.
      Parameters:
      `listener` - the object to be added and notified of FAN events.

      Throws:
      `java.lang.IllegalStateException` - if the recevier is closed.

    <!-- -->

    - #### removeListener

          void removeListener(FanEventListener listener)

      Removes a listener. The argument is not captured.
      Parameters:
      `listener` - the object to be removed from the list of listeners.

      Throws:
      `java.lang.IllegalArgumentException` - if the param is not present in the list of listeners.

    <!-- -->

    - #### close

          void close()

      Closes this subscription. This method may return before all activity completes. In particular, some listeners may receive additional events even after the method returns. Closing an already closed object does nothing.

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

- [Prev Class](FanManager.md)
- [Next Class](FanUpEventListener.md)

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
