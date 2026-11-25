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

- [Prev Class](QueueConnectionFactory.md)
- [Next Class](QueueRequestor.md)

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

## Interface QueueReceiver

- All Superinterfaces:
  [MessageConsumer](MessageConsumer.md)

  <!-- -->

  All Known Subinterfaces:
  [AQjmsQueueReceiver](../../oracle/jms/AQjmsQueueReceiver.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsConsumer](../../oracle/jms/AQjmsConsumer.md)

  ------------------------------------------------------------------------



      public interface QueueReceiver
      extends MessageConsumer

  A client uses a `QueueReceiver` object to receive messages that have been delivered to a queue.
  Although it is possible to have multiple `QueueReceiver`s for the same queue, the JMS API does not define how messages are distributed between the `QueueReceiver`s.

  If a `QueueReceiver` specifies a message selector, the messages that are not selected remain on the queue. By definition, a message selector allows a `QueueReceiver` to skip messages. This means that when the skipped messages are eventually read, the total ordering of the reads does not retain the partial order defined by each message producer. Only `QueueReceiver`s without a message selector will read messages in message producer order.

  Creating a `MessageConsumer` provides the same features as creating a `QueueReceiver`. A `MessageConsumer` object is recommended for creating new code. The `QueueReceiver` is provided to support existing code.

  See Also:
  [`Session.createConsumer(Destination, String)`](Session.md), [`Session.createConsumer(Destination)`](Session.md), [`QueueSession.createReceiver(Queue, String)`](QueueSession.md), [`QueueSession.createReceiver(Queue)`](QueueSession.md), [`MessageConsumer`](MessageConsumer.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type   | Method and Description                                                  |
    |---------------------|-------------------------------------------------------------------------|
    | [`Queue`](Queue.md) | `getQueue``()`<br>Gets the `Queue` associated with this queue receiver. |

    - ### Methods inherited from interface javax.jms.[MessageConsumer](MessageConsumer.md)

      [`close`](MessageConsumer.md)`, `[`getMessageListener`](MessageConsumer.md)`, `[`getMessageSelector`](MessageConsumer.md)`, `[`receive`](MessageConsumer.md)`, `[`receive`](MessageConsumer.md)`, `[`receiveNoWait`](MessageConsumer.md)`, `[`setMessageListener`](MessageConsumer.md)

<!-- -->

- - ### Method Detail

    - #### getQueue

          Queue getQueue()
                  throws JMSException

      Gets the `Queue` associated with this queue receiver.
      Returns:
      this receiver's `Queue`

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the queue for this queue receiver due to some internal error.

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

- [Prev Class](QueueConnectionFactory.md)
- [Next Class](QueueRequestor.md)

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
