Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database Advanced Queuing Java API Reference
19c**
E96513-01

- [Prev Class](MessageFormatException.md)
- [Next Class](MessageNotReadableException.md)

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

javax.jms

## Interface MessageListener

-

  ------------------------------------------------------------------------



      public interface MessageListener

  A `MessageListener` object is used to receive asynchronously delivered messages.
  Each session must insure that it passes messages serially to the listener. This means that a listener assigned to one or more consumers of the same session can assume that the `onMessage` method is not called with the next message until the session has completed the last call.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                                                                |
    |-------------------|---------------------------------------------------------------------------------------|
    | `void`            | `onMessage``(`[`Message`](Message.md)` message)`<br>Passes a message to the listener. |

<!-- -->

- - ### Method Detail

    - #### onMessage

          void onMessage(Message message)

      Passes a message to the listener.
      Parameters:
      `message` - the message passed to the listener

Skip navigation links

- [Overview](../../overview-summary.md)
- [Package](package-summary.md)
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database Advanced Queuing Java API Reference
19c**
E96513-01

- [Prev Class](MessageFormatException.md)
- [Next Class](MessageNotReadableException.md)

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

Copyright © 2001, 2019, Oracle and/or its affiliates. All rights reserved.
