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

- [Prev Class](QueueSender.md)
- [Next Class](ResourceAllocationException.md)

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

## Interface QueueSession

- All Superinterfaces:
  java.lang.Runnable, [Session](Session.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsSession](../../oracle/jms/AQjmsSession.md), [AQjmsXASession](../../oracle/jms/AQjmsXASession.md)

  ------------------------------------------------------------------------



      public interface QueueSession
      extends Session

  A `QueueSession` object provides methods for creating `QueueReceiver`, `QueueSender`, `QueueBrowser`, and `TemporaryQueue` objects.
  If there are messages that have been received but not acknowledged when a `QueueSession` terminates, these messages will be retained and redelivered when a consumer next accesses the queue.

  A `QueueSession` is used for creating Point-to-Point specific objects. In general, use the `Session` object. The `QueueSession` is used to support existing code. Using the `Session` object simplifies the programming model, and allows transactions to be used across the two messaging domains.

  A `QueueSession` cannot be used to create objects specific to the publish/subscribe domain. The following methods inherit from `Session`, but must throw an `IllegalStateException` if they are used from `QueueSession`:

  - `createDurableSubscriber`
  - `createTemporaryTopic`
  - `createTopic`
  - `unsubscribe`

  See Also:
  [`Session`](Session.md), [`QueueConnection.createQueueSession(boolean, int)`](QueueConnection.md), [`XAQueueSession.getQueueSession()`](XAQueueSession.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface javax.jms.[Session](Session.md)

      [`AUTO_ACKNOWLEDGE`](Session.md)`, `[`CLIENT_ACKNOWLEDGE`](Session.md)`, `[`DUPS_OK_ACKNOWLEDGE`](Session.md)`, `[`SESSION_TRANSACTED`](Session.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                     | Method and Description                                                                                                                                                                       |
    |---------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`QueueBrowser`](QueueBrowser.md)     | `createBrowser``(`[`Queue`](Queue.md)` queue)`<br>Creates a `QueueBrowser` object to peek at the messages on the specified queue.                                                            |
    | [`QueueBrowser`](QueueBrowser.md)     | `createBrowser``(`[`Queue`](Queue.md)` queue, java.lang.String messageSelector)`<br>Creates a `QueueBrowser` object to peek at the messages on the specified queue using a message selector. |
    | [`Queue`](Queue.md)                   | `createQueue``(java.lang.String queueName)`<br>Creates a queue identity given a `Queue` name.                                                                                                |
    | [`QueueReceiver`](QueueReceiver.md)   | `createReceiver``(`[`Queue`](Queue.md)` queue)`<br>Creates a `QueueReceiver` object to receive messages from the specified queue.                                                            |
    | [`QueueReceiver`](QueueReceiver.md)   | `createReceiver``(`[`Queue`](Queue.md)` queue, java.lang.String messageSelector)`<br>Creates a `QueueReceiver` object to receive messages from the specified queue using a message selector. |
    | [`QueueSender`](QueueSender.md)       | `createSender``(`[`Queue`](Queue.md)` queue)`<br>Creates a `QueueSender` object to send messages to the specified queue.                                                                     |
    | [`TemporaryQueue`](TemporaryQueue.md) | `createTemporaryQueue``()`<br>Creates a `TemporaryQueue` object.                                                                                                                             |

    - ### Methods inherited from interface javax.jms.[Session](Session.md)

      [`close`](Session.md)`, `[`commit`](Session.md)`, `[`createBytesMessage`](Session.md)`, `[`createConsumer`](Session.md)`, `[`createConsumer`](Session.md)`, `[`createConsumer`](Session.md)`, `[`createDurableSubscriber`](Session.md)`, `[`createDurableSubscriber`](Session.md)`, `[`createMapMessage`](Session.md)`, `[`createMessage`](Session.md)`, `[`createObjectMessage`](Session.md)`, `[`createObjectMessage`](Session.md)`, `[`createProducer`](Session.md)`, `[`createStreamMessage`](Session.md)`, `[`createTemporaryTopic`](Session.md)`, `[`createTextMessage`](Session.md)`, `[`createTextMessage`](Session.md)`, `[`createTopic`](Session.md)`, `[`getAcknowledgeMode`](Session.md)`, `[`getMessageListener`](Session.md)`, `[`getTransacted`](Session.md)`, `[`recover`](Session.md)`, `[`rollback`](Session.md)`, `[`run`](Session.md)`, `[`setMessageListener`](Session.md)`, `[`unsubscribe`](Session.md)

<!-- -->

- - ### Method Detail

    - #### createQueue

          Queue createQueue(java.lang.String queueName)
                     throws JMSException

      Creates a queue identity given a `Queue` name.
      This facility is provided for the rare cases where clients need to dynamically manipulate queue identity. It allows the creation of a queue identity with a provider-specific name. Clients that depend on this ability are not portable.

      Note that this method is not for creating the physical queue. The physical creation of queues is an administrative task and is not to be initiated by the JMS API. The one exception is the creation of temporary queues, which is accomplished with the `createTemporaryQueue` method.

      Specified by:
      [`createQueue`](Session.md) in interface [`Session`](Session.md)

      Parameters:
      `queueName` - the name of this `Queue`

      Returns:
      a `Queue` with the given name

      Throws:
      [`JMSException`](JMSException.md) - if the session fails to create a queue due to some internal error.

    <!-- -->

    - #### createReceiver

          QueueReceiver createReceiver(Queue queue)
                                throws JMSException

      Creates a `QueueReceiver` object to receive messages from the specified queue.
      Parameters:
      `queue` - the `Queue` to access

      Throws:
      [`JMSException`](JMSException.md) - if the session fails to create a receiver due to some internal error.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if an invalid queue is specified.

    <!-- -->

    - #### createReceiver

          QueueReceiver createReceiver(Queue queue,
                                       java.lang.String messageSelector)
                                throws JMSException

      Creates a `QueueReceiver` object to receive messages from the specified queue using a message selector.
      Parameters:
      `queue` - the `Queue` to access

      `messageSelector` - only messages with properties matching the message selector expression are delivered. A value of null or an empty string indicates that there is no message selector for the message consumer.

      Throws:
      [`JMSException`](JMSException.md) - if the session fails to create a receiver due to some internal error.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if an invalid queue is specified.

      [`InvalidSelectorException`](InvalidSelectorException.md) - if the message selector is invalid.

    <!-- -->

    - #### createSender

          QueueSender createSender(Queue queue)
                            throws JMSException

      Creates a `QueueSender` object to send messages to the specified queue.
      Parameters:
      `queue` - the `Queue` to access, or null if this is an unidentified producer

      Throws:
      [`JMSException`](JMSException.md) - if the session fails to create a sender due to some internal error.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if an invalid queue is specified.

    <!-- -->

    - #### createBrowser

          QueueBrowser createBrowser(Queue queue)
                              throws JMSException

      Creates a `QueueBrowser` object to peek at the messages on the specified queue.
      Specified by:
      [`createBrowser`](Session.md) in interface [`Session`](Session.md)

      Parameters:
      `queue` - the `Queue` to access

      Throws:
      [`JMSException`](JMSException.md) - if the session fails to create a browser due to some internal error.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if an invalid queue is specified.

    <!-- -->

    - #### createBrowser

          QueueBrowser createBrowser(Queue queue,
                                     java.lang.String messageSelector)
                              throws JMSException

      Creates a `QueueBrowser` object to peek at the messages on the specified queue using a message selector.
      Specified by:
      [`createBrowser`](Session.md) in interface [`Session`](Session.md)

      Parameters:
      `queue` - the `Queue` to access

      `messageSelector` - only messages with properties matching the message selector expression are delivered. A value of null or an empty string indicates that there is no message selector for the message consumer.

      Throws:
      [`JMSException`](JMSException.md) - if the session fails to create a browser due to some internal error.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if an invalid queue is specified.

      [`InvalidSelectorException`](InvalidSelectorException.md) - if the message selector is invalid.

    <!-- -->

    - #### createTemporaryQueue

          TemporaryQueue createTemporaryQueue()
                                       throws JMSException

      Creates a `TemporaryQueue` object. Its lifetime will be that of the `QueueConnection` unless it is deleted earlier.
      Specified by:
      [`createTemporaryQueue`](Session.md) in interface [`Session`](Session.md)

      Returns:
      a temporary queue identity

      Throws:
      [`JMSException`](JMSException.md) - if the session fails to create a temporary queue due to some internal error.

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

- [Prev Class](QueueSender.md)
- [Next Class](ResourceAllocationException.md)

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
