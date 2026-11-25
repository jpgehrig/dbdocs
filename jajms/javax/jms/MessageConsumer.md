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

- [Prev Class](Message.md)
- [Next Class](MessageEOFException.md)

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

## Interface MessageConsumer

- All Known Subinterfaces:
  [AQjmsQueueReceiver](../../oracle/jms/AQjmsQueueReceiver.md), [AQjmsTopicReceiver](../../oracle/jms/AQjmsTopicReceiver.md), [AQjmsTopicSubscriber](../../oracle/jms/AQjmsTopicSubscriber.md), [QueueReceiver](QueueReceiver.md), [TopicReceiver](../../oracle/jms/TopicReceiver.md), [TopicSubscriber](TopicSubscriber.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsConsumer](../../oracle/jms/AQjmsConsumer.md)

  ------------------------------------------------------------------------



      public interface MessageConsumer

  A client uses a `MessageConsumer` object to receive messages from a destination. A `MessageConsumer` object is created by passing a `Destination` object to a message-consumer creation method supplied by a session.
  `MessageConsumer` is the parent interface for all message consumers.

  A message consumer can be created with a message selector. A message selector allows the client to restrict the messages delivered to the message consumer to those that match the selector.

  A client may either synchronously receive a message consumer's messages or have the consumer asynchronously deliver them as they arrive.

  For synchronous receipt, a client can request the next message from a message consumer using one of its `receive` methods. There are several variations of `receive` that allow a client to poll or wait for the next message.

  For asynchronous delivery, a client can register a `MessageListener` object with a message consumer. As messages arrive at the message consumer, it delivers them by calling the `MessageListener`'s `onMessage` method.

  It is a client programming error for a `MessageListener` to throw an exception.

  See Also:
  [`QueueReceiver`](QueueReceiver.md), [`TopicSubscriber`](TopicSubscriber.md), [`Session`](Session.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                       | Method and Description                                                                                                       |
    |-----------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                  | `close``()`<br>Closes the message consumer.                                                                                  |
    | [`MessageListener`](MessageListener.md) | `getMessageListener``()`<br>Gets the message consumer's `MessageListener`.                                                   |
    | `java.lang.String`                      | `getMessageSelector``()`<br>Gets this message consumer's message selector expression.                                        |
    | [`Message`](Message.md)                 | `receive``()`<br>Receives the next message produced for this message consumer.                                               |
    | [`Message`](Message.md)                 | `receive``(long timeout)`<br>Receives the next message that arrives within the specified timeout interval.                   |
    | [`Message`](Message.md)                 | `receiveNoWait``()`<br>Receives the next message if one is immediately available.                                            |
    | `void`                                  | `setMessageListener``(`[`MessageListener`](MessageListener.md)` listener)`<br>Sets the message consumer's `MessageListener`. |

<!-- -->

- - ### Method Detail

    - #### getMessageSelector

          java.lang.String getMessageSelector()
                                       throws JMSException

      Gets this message consumer's message selector expression.
      Returns:
      this message consumer's message selector, or null if no message selector exists for the message consumer (that is, if the message selector was not set or was set to null or the empty string)

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the message selector due to some internal error.

    <!-- -->

    - #### getMessageListener

          MessageListener getMessageListener()
                                      throws JMSException

      Gets the message consumer's `MessageListener`.
      Returns:
      the listener for the message consumer, or null if no listener is set

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the message listener due to some internal error.

      See Also:
      `MessageConsumer.setMessageListener(javax.jms.MessageListener)`

    <!-- -->

    - #### setMessageListener

          void setMessageListener(MessageListener listener)
                           throws JMSException

      Sets the message consumer's `MessageListener`.
      Setting the message listener to null is the equivalent of unsetting the message listener for the message consumer.

      The effect of calling `MessageConsumer.setMessageListener` while messages are being consumed by an existing listener or the consumer is being used to consume messages synchronously is undefined.

      Parameters:
      `listener` - the listener to which the messages are to be delivered

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to set the message listener due to some internal error.

      See Also:
      `MessageConsumer.getMessageListener()`

    <!-- -->

    - #### receive

          Message receive()
                   throws JMSException

      Receives the next message produced for this message consumer.
      This call blocks indefinitely until a message is produced or until this message consumer is closed.

      If this `receive` is done within a transaction, the consumer retains the message until the transaction commits.

      Returns:
      the next message produced for this message consumer, or null if this message consumer is concurrently closed

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to receive the next message due to some internal error.

    <!-- -->

    - #### receive

          Message receive(long timeout)
                   throws JMSException

      Receives the next message that arrives within the specified timeout interval.
      This call blocks until a message arrives, the timeout expires, or this message consumer is closed. A `timeout` of zero never expires, and the call blocks indefinitely.

      Parameters:
      `timeout` - the timeout value (in milliseconds)

      Returns:
      the next message produced for this message consumer, or null if the timeout expires or this message consumer is concurrently closed

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to receive the next message due to some internal error.

    <!-- -->

    - #### receiveNoWait

          Message receiveNoWait()
                         throws JMSException

      Receives the next message if one is immediately available.
      Returns:
      the next message produced for this message consumer, or null if one is not available

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to receive the next message due to some internal error.

    <!-- -->

    - #### close

          void close()
              throws JMSException

      Closes the message consumer.
      Since a provider may allocate some resources on behalf of a `MessageConsumer` outside the Java virtual machine, clients should close them when they are not needed. Relying on garbage collection to eventually reclaim these resources may not be timely enough.

      This call blocks until a `receive` or message listener in progress has completed. A blocked message consumer `receive` call returns null when this message consumer is closed.

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to close the consumer due to some internal error.

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

- [Prev Class](Message.md)
- [Next Class](MessageEOFException.md)

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
