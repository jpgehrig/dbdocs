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

- [Prev Class](AQjmsConnectionMetaData.md)
- [Next Class](AQjmsDestination.md)

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

oracle.jms

## Class AQjmsConsumer

- java.lang.Object

- - oracle.jms.AQjmsObject

  - - oracle.jms.AQjmsConsumer

<!-- -->

- All Implemented Interfaces:
  [MessageConsumer](../../javax/jms/MessageConsumer.md), [QueueReceiver](../../javax/jms/QueueReceiver.md), [TopicSubscriber](../../javax/jms/TopicSubscriber.md), [AQjmsQueueReceiver](AQjmsQueueReceiver.md), [AQjmsTopicReceiver](AQjmsTopicReceiver.md), [AQjmsTopicSubscriber](AQjmsTopicSubscriber.md), [TopicReceiver](TopicReceiver.md)

  ------------------------------------------------------------------------



      public class AQjmsConsumer
      extends oracle.jms.AQjmsObject
      implements AQjmsQueueReceiver, AQjmsTopicSubscriber, AQjmsTopicReceiver

  This is an Oracle class which implements `oracle.jms.AQjmsQueueReceiver`, `oracle.jms.AQjmsTopicSubscriber` and `oracle.jms.AQjmsTopicReceiver`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                       | Method and Description                                                                                                                                                               |
    |---------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Message`](../../javax/jms/Message.md)                 | `bufferReceive``()`<br>Receives the next message from both the in-memory and persistent portion of the queue.                                                                        |
    | [`Message`](../../javax/jms/Message.md)                 | `bufferReceive``(long timeout)`<br>Receives the next message from both the in-memory and persistent portion of the queue if one is available within the specified timeout.           |
    | [`Message`](../../javax/jms/Message.md)                 | `bufferReceiveNoWait``()`<br>Receives the next message from both the in-memory and persistent portion of the queue if one is immediately available.                                  |
    | `void`                                                  | `close``()`<br>Public for test harness purposes                                                                                                                                      |
    | [`MessageListener`](../../javax/jms/MessageListener.md) | `getMessageListener``()`<br>Gets this message consumer's [`MessageListener`](../../javax/jms/MessageListener.md).                                                                    |
    | `java.lang.String`                                      | `getMessageSelector``()`<br>Gets this message consumer's message selector expression.                                                                                                |
    | `int`                                                   | `getNavigationMode``()`<br>Gets the navigation mode used for receiving messages.                                                                                                     |
    | `boolean`                                               | `getNoLocal``()`<br>Gets the `NoLocal` attribute for this `TopicSubscriber`.                                                                                                         |
    | [`Queue`](../../javax/jms/Queue.md)                     | `getQueue``()`<br>Gets the queue associated with this queue receiver.                                                                                                                |
    | [`Topic`](../../javax/jms/Topic.md)                     | `getTopic``()`<br>Gets the topic associated with this topic subscriber.                                                                                                              |
    | `java.lang.String`                                      | `getTransformation``()`<br>Gets this consumer's transformation.                                                                                                                      |
    | [`Message`](../../javax/jms/Message.md)                 | `receive``()`<br>Receives the next message.                                                                                                                                          |
    | [`Message`](../../javax/jms/Message.md)                 | `receive``(long timeout)`<br>Receives the next message if one is available within the specified timeout.                                                                             |
    | `void`                                                  | `receiveNoData``()`<br>Consumes the message without returning it to the user.                                                                                                        |
    | `void`                                                  | `receiveNoData``(long timeout)`<br>Consumes the message without returning it to the user.                                                                                            |
    | [`Message`](../../javax/jms/Message.md)                 | `receiveNoWait``()`<br>Receives the next message if one is immediately available.                                                                                                    |
    | `void`                                                  | `setMessageListener``(`[`MessageListener`](../../javax/jms/MessageListener.md)` myListener)`<br>Set this message consumer's [`MessageListener`](../../javax/jms/MessageListener.md). |
    | `void`                                                  | `setNavigationMode``(int mode)`<br>Sets the navigation mode used for receiving messages.                                                                                             |
    | `void`                                                  | `setTransformation``(java.lang.String transformation)`<br>Sets this consumer's transformation.                                                                                       |

    - ### Methods inherited from class oracle.jms.AQjmsObject

      `checkClosed, children, finalize, getID, getParent, isOpen, localClose, preClose`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface oracle.jms.[AQjmsTopicSubscriber](AQjmsTopicSubscriber.md)

      [`receive`](AQjmsTopicSubscriber.md)

    <!-- -->

    - ### Methods inherited from interface oracle.jms.[AQjmsTopicReceiver](AQjmsTopicReceiver.md)

      [`receive`](AQjmsTopicReceiver.md)`, `[`receive`](AQjmsTopicReceiver.md)`, `[`receiveSignature`](AQjmsTopicReceiver.md)`, `[`receiveSignature`](AQjmsTopicReceiver.md)

<!-- -->

- - ### Method Detail

    - #### getMessageSelector

          public java.lang.String getMessageSelector()
                                              throws JMSException

      Gets this message consumer's message selector expression.
      Specified by:
      [`getMessageSelector`](../../javax/jms/MessageConsumer.md) in interface [`MessageConsumer`](../../javax/jms/MessageConsumer.md)

      Returns:
      this message consumer's message selector

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if this consumer has already been closed.

      See Also:
      `AQjmsConsumer.close()`

    <!-- -->

    - #### getMessageListener

          public MessageListener getMessageListener()
                                             throws JMSException

      Gets this message consumer's [`MessageListener`](../../javax/jms/MessageListener.md).
      Specified by:
      [`getMessageListener`](../../javax/jms/MessageConsumer.md) in interface [`MessageConsumer`](../../javax/jms/MessageConsumer.md)

      Returns:
      the listener for this message consumer, or `null` if no listener is set

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if:

      - this consumer has already been closed, or
      - a distinguished listener has been set for this consumer's session.

      See Also:
      `AQjmsConsumer.close()`, [`AQjmsSession.setMessageListener(javax.jms.MessageListener)`](AQjmsSession.md)

    <!-- -->

    - #### setMessageListener

          public void setMessageListener(MessageListener myListener)
                                  throws JMSException

      Set this message consumer's [`MessageListener`](../../javax/jms/MessageListener.md). Once set, `myListener`'s [`MessageListener.onMessage(javax.jms.Message)`](../../javax/jms/MessageListener.md) method is called when there are messages for this consumer.
      Specified by:
      [`setMessageListener`](../../javax/jms/MessageConsumer.md) in interface [`MessageConsumer`](../../javax/jms/MessageConsumer.md)

      Parameters:
      `myListener` - the listener to which incoming messages are to be sent

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if:

      - this consumer has already been closed,
      - a distinguished listener has been set for this consumer's session, or
      - a thread to process the listener can not be created/started.

      See Also:
      `AQjmsConsumer.close()`, [`AQjmsSession.setMessageListener(javax.jms.MessageListener)`](AQjmsSession.md)

    <!-- -->

    - #### receive

          public Message receive()
                          throws JMSException

      Receives the next message.
      Blocks indefinitely until a message is received or this consumer is closed.

      Specified by:
      [`receive`](../../javax/jms/MessageConsumer.md) in interface [`MessageConsumer`](../../javax/jms/MessageConsumer.md)

      Returns:
      the next message, or `null` if the receive was pending and was then terminated due to this consumer being closed

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the next message is not received due to some error.

    <!-- -->

    - #### receiveNoWait

          public Message receiveNoWait()
                                throws JMSException

      Receives the next message if one is immediately available.
      Specified by:
      [`receiveNoWait`](../../javax/jms/MessageConsumer.md) in interface [`MessageConsumer`](../../javax/jms/MessageConsumer.md)

      Returns:
      the next message, or `null` if none are immediately available

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the next message is not received due to some error.

    <!-- -->

    - #### receive

          public Message receive(long timeout)
                          throws JMSException

      Receives the next message if one is available within the specified timeout.
      Blocks until a message is received, the timeout expires, or this consumer is closed. A `timeout` of zero never expires.

      Specified by:
      [`receive`](../../javax/jms/MessageConsumer.md) in interface [`MessageConsumer`](../../javax/jms/MessageConsumer.md)

      Parameters:
      `timeout` - the timeout value (in milliseconds)

      Returns:
      the next message, or `null` if none are available in time

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the next message is not received due to some error.

    <!-- -->

    - #### bufferReceive

          public Message bufferReceive()
                                throws JMSException

      Receives the next message from both the in-memory and persistent portion of the queue. When the in-memory queue is used, the enqueue operation is required to be in immediate visibility mode. (This requirement might be removed in a later release.) When a sharded queue is used, this method throws an exception. Use the JMS standard APIs to receive messages from sharded queues.
      Blocks indefinitely until a message is received or this consumer is closed.

      Returns:
      the next message, or `null` if the receive was pending and was then terminated due to this consumer being closed

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the next message is not received due to some error.

    <!-- -->

    - #### bufferReceiveNoWait

          public Message bufferReceiveNoWait()
                                      throws JMSException

      Receives the next message from both the in-memory and persistent portion of the queue if one is immediately available. When the in-memory queue is used, the enqueue operation is required to be in immediate visibility mode. (This requirement might be removed in a later release.) When a sharded queue is used, this method throws an exception. Use the JMS standard APIs to receive messages from sharded queues.
      Returns:
      the next message, or `null` if none are immediately available

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the next message is not received due to some error.

    <!-- -->

    - #### bufferReceive

          public Message bufferReceive(long timeout)
                                throws JMSException

      Receives the next message from both the in-memory and persistent portion of the queue if one is available within the specified timeout. When the in-memory queue is used, the enqueue operation is required to be in immediate visibility mode. (This requirement might be removed in a later release.) When a sharded queue is used, this method throws an exception. Use the JMS standard APIs to receive messages from sharded queues.
      Blocks until a message is received, the timeout expires, or this consumer is closed. A `timeout` of zero never expires.

      Parameters:
      `timeout` - the timeout value (in milliseconds)

      Returns:
      the next message, or `null` if none are available in time

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the next message is not received due to some error.

    <!-- -->

    - #### close

          public void close()
                     throws JMSException

      Description copied from class: `oracle.jms.AQjmsObject`
      Public for test harness purposes
      Specified by:
      [`close`](../../javax/jms/MessageConsumer.md) in interface [`MessageConsumer`](../../javax/jms/MessageConsumer.md)

      Overrides:
      `close` in class `oracle.jms.AQjmsObject`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to close the consumer due to some internal error.

    <!-- -->

    - #### getQueue

          public Queue getQueue()
                         throws JMSException

      Gets the queue associated with this queue receiver.
      Specified by:
      [`getQueue`](../../javax/jms/QueueReceiver.md) in interface [`QueueReceiver`](../../javax/jms/QueueReceiver.md)

      Returns:
      the queue

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if called on a topic subscriber.

    <!-- -->

    - #### getTopic

          public Topic getTopic()
                         throws JMSException

      Gets the topic associated with this topic subscriber.
      Specified by:
      [`getTopic`](../../javax/jms/TopicSubscriber.md) in interface [`TopicSubscriber`](../../javax/jms/TopicSubscriber.md)

      Specified by:
      [`getTopic`](TopicReceiver.md) in interface [`TopicReceiver`](TopicReceiver.md)

      Returns:
      the topic

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if called on a queue receiver.

    <!-- -->

    - #### getNoLocal

          public boolean getNoLocal()
                             throws JMSException

      Gets the `NoLocal` attribute for this `TopicSubscriber`. The default value for this attribute is `false`.
      Specified by:
      [`getNoLocal`](../../javax/jms/TopicSubscriber.md) in interface [`TopicSubscriber`](../../javax/jms/TopicSubscriber.md)

      Returns:
      `true` if locally published messages are being inhibited.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if this method is called on a queue receiver.

    <!-- -->

    - #### getNavigationMode

          public int getNavigationMode()
                                throws JMSException

      Gets the navigation mode used for receiving messages. The navigation modes are:
      - `AQjmsConstants.NAVIGATION_FIRST_MESSAGE`
      - `AQjmsConstants.NAVIGATION_NEXT_MESSAGE`
      - `AQjmsConstants.NAVIGATION_NEXT_TRANSACTION`

      See the "Oracle® Database Advanced Queuing User's Guide and Reference" for an explanation of navigation modes.
      Specified by:
      [`getNavigationMode`](AQjmsQueueReceiver.md) in interface [`AQjmsQueueReceiver`](AQjmsQueueReceiver.md)

      Specified by:
      [`getNavigationMode`](AQjmsTopicReceiver.md) in interface [`AQjmsTopicReceiver`](AQjmsTopicReceiver.md)

      Specified by:
      [`getNavigationMode`](AQjmsTopicSubscriber.md) in interface [`AQjmsTopicSubscriber`](AQjmsTopicSubscriber.md)

      Returns:
      this consumer's navigation mode

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if this consumer has already been closed.

    <!-- -->

    - #### setNavigationMode

          public void setNavigationMode(int mode)
                                 throws JMSException

      Sets the navigation mode used for receiving messages. The navigation modes are:
      - `AQjmsConstants.NAVIGATION_FIRST_MESSAGE`
      - `AQjmsConstants.NAVIGATION_NEXT_MESSAGE`
      - `AQjmsConstants.NAVIGATION_NEXT_TRANSACTION`

      See the "Oracle® Database Advanced Queuing User's Guide and Reference" for an explanation of navigation modes.
      Specified by:
      [`setNavigationMode`](AQjmsQueueReceiver.md) in interface [`AQjmsQueueReceiver`](AQjmsQueueReceiver.md)

      Specified by:
      [`setNavigationMode`](AQjmsTopicReceiver.md) in interface [`AQjmsTopicReceiver`](AQjmsTopicReceiver.md)

      Specified by:
      [`setNavigationMode`](AQjmsTopicSubscriber.md) in interface [`AQjmsTopicSubscriber`](AQjmsTopicSubscriber.md)

      Parameters:
      `mode` - the new navigation mode for this consumer

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if:

      - this consumer has already been closed, or
      - the supplied `mode` does not match any of the above listed navigation modes.

    <!-- -->

    - #### setTransformation

          public void setTransformation(java.lang.String transformation)

      Sets this consumer's transformation.
      Specified by:
      [`setTransformation`](AQjmsQueueReceiver.md) in interface [`AQjmsQueueReceiver`](AQjmsQueueReceiver.md)

      Specified by:
      [`setTransformation`](AQjmsTopicReceiver.md) in interface [`AQjmsTopicReceiver`](AQjmsTopicReceiver.md)

      Parameters:
      `transformation` - the transformation to use when getting messages

    <!-- -->

    - #### getTransformation

          public java.lang.String getTransformation()

      Gets this consumer's transformation.
      Specified by:
      [`getTransformation`](AQjmsQueueReceiver.md) in interface [`AQjmsQueueReceiver`](AQjmsQueueReceiver.md)

      Specified by:
      [`getTransformation`](AQjmsTopicReceiver.md) in interface [`AQjmsTopicReceiver`](AQjmsTopicReceiver.md)

      Returns:
      the transformation used when getting messages

    <!-- -->

    - #### receiveNoData

          public void receiveNoData()
                             throws JMSException

      Consumes the message without returning it to the user. This call will avoid the overhead of fetching the message from the database. It can be used as an optimization by jms clients who have already read the message, for example using a queue browser.
      Blocks indefinitely until a message is received or this consumer is closed.

      Specified by:
      [`receiveNoData`](AQjmsQueueReceiver.md) in interface [`AQjmsQueueReceiver`](AQjmsQueueReceiver.md)

      Specified by:
      [`receiveNoData`](AQjmsTopicReceiver.md) in interface [`AQjmsTopicReceiver`](AQjmsTopicReceiver.md)

      Specified by:
      [`receiveNoData`](AQjmsTopicSubscriber.md) in interface [`AQjmsTopicSubscriber`](AQjmsTopicSubscriber.md)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message could not be received due to some error.

    <!-- -->

    - #### receiveNoData

          public void receiveNoData(long timeout)
                             throws JMSException

      Consumes the message without returning it to the user. This call will avoid the overhead of fetching the message from the database. It can be used as an optimization by jms clients who have already read the message, for example using a queue browser.
      Blocks until a message is received, the timeout expires, or this consumer is closed. A `timeout` of zero never expires.

      Specified by:
      [`receiveNoData`](AQjmsQueueReceiver.md) in interface [`AQjmsQueueReceiver`](AQjmsQueueReceiver.md)

      Specified by:
      [`receiveNoData`](AQjmsTopicReceiver.md) in interface [`AQjmsTopicReceiver`](AQjmsTopicReceiver.md)

      Specified by:
      [`receiveNoData`](AQjmsTopicSubscriber.md) in interface [`AQjmsTopicSubscriber`](AQjmsTopicSubscriber.md)

      Parameters:
      `timeout` - the timeout value in milliseconds

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message could not be received due to some error.

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

- [Prev Class](AQjmsConnectionMetaData.md)
- [Next Class](AQjmsDestination.md)

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
