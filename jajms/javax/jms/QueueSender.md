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

- [Prev Class](QueueRequestor.md)
- [Next Class](QueueSession.md)

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

## Interface QueueSender

- All Superinterfaces:
  [MessageProducer](MessageProducer.md)

  <!-- -->

  All Known Subinterfaces:
  [AQjmsQueueSender](../../oracle/jms/AQjmsQueueSender.md)

  ------------------------------------------------------------------------



      public interface QueueSender
      extends MessageProducer

  A client uses a `QueueSender` object to send messages to a queue.
  Normally, the `Queue` is specified when a `QueueSender` is created. In this case, an attempt to use the `send` methods for an unidentified `QueueSender` will throw a `java.lang.UnsupportedOperationException`.

  If the `QueueSender` is created with an unidentified `Queue`, an attempt to use the `send` methods that assume that the `Queue` has been identified will throw a `java.lang.UnsupportedOperationException`.

  During the execution of its `send` method, a message must not be changed by other threads within the client. If the message is modified, the result of the `send` is undefined.

  After sending a message, a client may retain and modify it without affecting the message that has been sent. The same message object may be sent multiple times.

  The following message headers are set as part of sending a message: `JMSDestination`, `JMSDeliveryMode`, `JMSExpiration`, `JMSPriority`, `JMSMessageID` and `JMSTimeStamp`. When the message is sent, the values of these headers are ignored. After the completion of the `send`, the headers hold the values specified by the method sending the message. It is possible for the `send` method not to set `JMSMessageID` and `JMSTimeStamp` if the setting of these headers is explicitly disabled by the `MessageProducer.setDisableMessageID` or `MessageProducer.setDisableMessageTimestamp` method.

  Creating a `MessageProducer` provides the same features as creating a `QueueSender`. A `MessageProducer` object is recommended when creating new code. The `QueueSender` is provided to support existing code.

  See Also:
  [`MessageProducer`](MessageProducer.md), [`Session.createProducer(Destination)`](Session.md), [`QueueSession.createSender(Queue)`](QueueSession.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type   | Method and Description                                                                                                                                                                                                                             |
    |---------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Queue`](Queue.md) | `getQueue``()`<br>Gets the queue associated with this `QueueSender`.                                                                                                                                                                               |
    | `void`              | `send``(`[`Message`](Message.md)` message)`<br>Sends a message to the queue.                                                                                                                                                                       |
    | `void`              | `send``(`[`Message`](Message.md)` message, int deliveryMode, int priority, long timeToLive)`<br>Sends a message to the queue, specifying delivery mode, priority, and time to live.                                                                |
    | `void`              | `send``(`[`Queue`](Queue.md)` queue, `[`Message`](Message.md)` message)`<br>Sends a message to a queue for an unidentified message producer.                                                                                                       |
    | `void`              | `send``(`[`Queue`](Queue.md)` queue, `[`Message`](Message.md)` message, int deliveryMode, int priority, long timeToLive)`<br>Sends a message to a queue for an unidentified message producer, specifying delivery mode, priority and time to live. |

    - ### Methods inherited from interface javax.jms.[MessageProducer](MessageProducer.md)

      [`close`](MessageProducer.md)`, `[`getDeliveryMode`](MessageProducer.md)`, `[`getDestination`](MessageProducer.md)`, `[`getDisableMessageID`](MessageProducer.md)`, `[`getDisableMessageTimestamp`](MessageProducer.md)`, `[`getPriority`](MessageProducer.md)`, `[`getTimeToLive`](MessageProducer.md)`, `[`send`](MessageProducer.md)`, `[`send`](MessageProducer.md)`, `[`setDeliveryMode`](MessageProducer.md)`, `[`setDisableMessageID`](MessageProducer.md)`, `[`setDisableMessageTimestamp`](MessageProducer.md)`, `[`setPriority`](MessageProducer.md)`, `[`setTimeToLive`](MessageProducer.md)

<!-- -->

- - ### Method Detail

    - #### getQueue

          Queue getQueue()
                  throws JMSException

      Gets the queue associated with this `QueueSender`.
      Returns:
      this sender's queue

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the queue for this `QueueSender` due to some internal error.

    <!-- -->

    - #### send

          void send(Message message)
             throws JMSException

      Sends a message to the queue. Uses the `QueueSender`'s default delivery mode, priority, and time to live.
      Specified by:
      [`send`](MessageProducer.md) in interface [`MessageProducer`](MessageProducer.md)

      Parameters:
      `message` - the message to send

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to send the message due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if an invalid message is specified.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if a client uses this method with a `QueueSender` with an invalid queue.

      `java.lang.UnsupportedOperationException` - if a client uses this method with a `QueueSender` that did not specify a queue at creation time.

      See Also:
      [`MessageProducer.getDeliveryMode()`](MessageProducer.md), [`MessageProducer.getTimeToLive()`](MessageProducer.md), [`MessageProducer.getPriority()`](MessageProducer.md)

    <!-- -->

    - #### send

          void send(Message message,
                    int deliveryMode,
                    int priority,
                    long timeToLive)
             throws JMSException

      Sends a message to the queue, specifying delivery mode, priority, and time to live.
      Specified by:
      [`send`](MessageProducer.md) in interface [`MessageProducer`](MessageProducer.md)

      Parameters:
      `message` - the message to send

      `deliveryMode` - the delivery mode to use

      `priority` - the priority for this message

      `timeToLive` - the message's lifetime (in milliseconds)

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to send the message due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if an invalid message is specified.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if a client uses this method with a `QueueSender` with an invalid queue.

      `java.lang.UnsupportedOperationException` - if a client uses this method with a `QueueSender` that did not specify a queue at creation time.

      See Also:
      [`Session.createProducer(javax.jms.Destination)`](Session.md)

    <!-- -->

    - #### send

          void send(Queue queue,
                    Message message)
             throws JMSException

      Sends a message to a queue for an unidentified message producer. Uses the `QueueSender`'s default delivery mode, priority, and time to live.
      Typically, a message producer is assigned a queue at creation time; however, the JMS API also supports unidentified message producers, which require that the queue be supplied every time a message is sent.

      Parameters:
      `queue` - the queue to send this message to

      `message` - the message to send

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to send the message due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if an invalid message is specified.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if a client uses this method with an invalid queue.

      See Also:
      [`MessageProducer.getDeliveryMode()`](MessageProducer.md), [`MessageProducer.getTimeToLive()`](MessageProducer.md), [`MessageProducer.getPriority()`](MessageProducer.md)

    <!-- -->

    - #### send

          void send(Queue queue,
                    Message message,
                    int deliveryMode,
                    int priority,
                    long timeToLive)
             throws JMSException

      Sends a message to a queue for an unidentified message producer, specifying delivery mode, priority and time to live.
      Typically, a message producer is assigned a queue at creation time; however, the JMS API also supports unidentified message producers, which require that the queue be supplied every time a message is sent.

      Parameters:
      `queue` - the queue to send this message to

      `message` - the message to send

      `deliveryMode` - the delivery mode to use

      `priority` - the priority for this message

      `timeToLive` - the message's lifetime (in milliseconds)

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to send the message due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if an invalid message is specified.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if a client uses this method with an invalid queue.

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

- [Prev Class](QueueRequestor.md)
- [Next Class](QueueSession.md)

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
