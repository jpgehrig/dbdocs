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

- [Prev Class](AQjmsParseException.md)
- [Next Class](AQjmsQueueBrowser.md)

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

## Class AQjmsProducer

- java.lang.Object

- - oracle.jms.AQjmsObject

  - - oracle.jms.AQjmsProducer

<!-- -->

- All Implemented Interfaces:
  [MessageProducer](../../javax/jms/MessageProducer.md)

  ------------------------------------------------------------------------



      public class AQjmsProducer
      extends oracle.jms.AQjmsObject
      implements MessageProducer

  This is an Oracle class which implements `javax.jms.MessageProducer`.
  See Also:
  [`AQjmsQueueSender`](AQjmsQueueSender.md), [`AQjmsTopicPublisher`](AQjmsTopicPublisher.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                               | Method and Description                                                                                                                                                                                                                                                                                                   |
    |-------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                          | `bufferPublish``(`[`Topic`](../../javax/jms/Topic.md)` topic, `[`Message`](../../javax/jms/Message.md)` message, int priority, long timeToLive)`<br>Publishes a non-persistent message to an in-memory portion of the topic for an unidentified message producer, specifying delivery mode, priority and time-to-live.   |
    | `void`                                          | `bufferSend``(`[`Destination`](../../javax/jms/Destination.md)` destination, `[`Message`](../../javax/jms/Message.md)` message, int priority, long timeToLive)`<br>Sends a non-persistent message to an in-memory portion of the destination for an unidentified message producer, specifying priority and time-to-live. |
    | `void`                                          | `bufferSend``(`[`Queue`](../../javax/jms/Queue.md)` queue, `[`Message`](../../javax/jms/Message.md)` message, int priority, long timeToLive)`<br>Sends a non-persistent message to an in-memory portion of the queue for an unidentified message producer, specifying delivery mode, priority and time-to-live.          |
    | `void`                                          | `close``()`<br>Public for test harness purposes                                                                                                                                                                                                                                                                          |
    | `int`                                           | `getDeliveryMode``()`<br>Gets this producer's default delivery mode.                                                                                                                                                                                                                                                     |
    | [`Destination`](../../javax/jms/Destination.md) | `getDestination``()`<br>Gets the destination associated with this `MessageProducer`.                                                                                                                                                                                                                                     |
    | `boolean`                                       | `getDisableMessageID``()`<br>Gets an indication of whether message IDs are disabled.                                                                                                                                                                                                                                     |
    | `boolean`                                       | `getDisableMessageTimestamp``()`<br>Gets an indication of whether message timestamps are disabled.                                                                                                                                                                                                                       |
    | `int`                                           | `getPriority``()`<br>Gets this producer's default priority.                                                                                                                                                                                                                                                              |
    | [`Queue`](../../javax/jms/Queue.md)             | `getQueue``()`<br>Gets the queue associated with this queue sender.                                                                                                                                                                                                                                                      |
    | `long`                                          | `getTimeToLive``()`<br>Gets the default length of time in milliseconds from its dispatch time that a produced message should be retained by the message system.                                                                                                                                                          |
    | [`Topic`](../../javax/jms/Topic.md)             | `getTopic``()`<br>Gets the topic associated with this publisher.                                                                                                                                                                                                                                                         |
    | `java.lang.String`                              | `getTransformation``()`<br>Gets this producer's transformation.                                                                                                                                                                                                                                                          |
    | `void`                                          | `publish``(`[`Message`](../../javax/jms/Message.md)` message)`<br>Publishes a message.                                                                                                                                                                                                                                   |
    | `void`                                          | `publish``(`[`Message`](../../javax/jms/Message.md)` message, oracle.jms.AQjmsAgent[] recipientList)`<br>Publishes a message to a specific list of recipients                                                                                                                                                            |
    | `void`                                          | `publish``(`[`Message`](../../javax/jms/Message.md)` message, oracle.jms.AQjmsAgent[] recipientList, int deliveryMode, int priority, long timeToLive)`<br>Publishes a message to a topic by specifying a list of recipients, delivery mode, priority and time-to-live                                                    |
    | `void`                                          | `publish``(`[`Message`](../../javax/jms/Message.md)` message, int deliveryMode, int priority, long timeToLive)`<br>Publishes a message to the topic specifying delivery mode, priority and time-to-live.                                                                                                                 |
    | `void`                                          | `publish``(`[`Topic`](../../javax/jms/Topic.md)` topic, `[`Message`](../../javax/jms/Message.md)` message)`<br>Publishes a message to a topic for an unidentified message producer.                                                                                                                                      |
    | `void`                                          | `publish``(`[`Topic`](../../javax/jms/Topic.md)` topic, `[`Message`](../../javax/jms/Message.md)` message, oracle.jms.AQjmsAgent[] recipientList)`<br>Publishes a message to a topic by specifying a list of recipients.                                                                                                 |
    | `void`                                          | `publish``(`[`Topic`](../../javax/jms/Topic.md)` topic, `[`Message`](../../javax/jms/Message.md)` message, oracle.jms.AQjmsAgent[] recipientList, int deliveryMode, int priority, long timeToLive)`<br>Publishes a message to a topic by specifying a list of recipients, delivery mode, priority and time-to-live       |
    | `void`                                          | `publish``(`[`Topic`](../../javax/jms/Topic.md)` topic, `[`Message`](../../javax/jms/Message.md)` message, int deliveryMode, int priority, long timeToLive)`<br>Publishes a message to a topic for an unidentified message producer, specifying delivery mode, priority and time-to-live.                                |
    | `void`                                          | `send``(`[`Destination`](../../javax/jms/Destination.md)` destination, `[`Message`](../../javax/jms/Message.md)` message)`<br>Sends a message to a destination for an unidentified message producer.                                                                                                                     |
    | `void`                                          | `send``(`[`Destination`](../../javax/jms/Destination.md)` destination, `[`Message`](../../javax/jms/Message.md)` message, int deliveryMode, int priority, long timeToLive)`<br>Sends a message to a destination for an unidentified message producer, specifying delivery mode, priority and time-to-live.               |
    | `void`                                          | `send``(`[`Message`](../../javax/jms/Message.md)` message)`<br>Sends a message.                                                                                                                                                                                                                                          |
    | `void`                                          | `send``(`[`Message`](../../javax/jms/Message.md)` message, int deliveryMode, int priority, long timeToLive)`<br>Sends a message.                                                                                                                                                                                         |
    | `void`                                          | `send``(`[`Queue`](../../javax/jms/Queue.md)` queue, `[`Message`](../../javax/jms/Message.md)` message)`<br>Sends a message.                                                                                                                                                                                             |
    | `void`                                          | `send``(`[`Queue`](../../javax/jms/Queue.md)` queue, `[`Message`](../../javax/jms/Message.md)` message, int deliveryMode, int priority, long timeToLive)`<br>Sends a message.                                                                                                                                            |
    | `void`                                          | `setDeliveryMode``(int deliveryMode)`<br>Sets this producer's default delivery mode.                                                                                                                                                                                                                                     |
    | `void`                                          | `setDisableMessageID``(boolean value)`<br>Sets whether message IDs can be disabled.                                                                                                                                                                                                                                      |
    | `void`                                          | `setDisableMessageTimestamp``(boolean value)`<br>Sets whether message timestamps can be disabled.                                                                                                                                                                                                                        |
    | `void`                                          | `setPriority``(int priority)`<br>Sets this producer's default priority.                                                                                                                                                                                                                                                  |
    | `void`                                          | `setTimeToLive``(long timeToLive)`<br>Sets the default length of time in milliseconds from its dispatch time that a produced message should be retained by the message system.                                                                                                                                           |
    | `void`                                          | `setTransformation``(java.lang.String transformation)`<br>Sets this producer's transformation.                                                                                                                                                                                                                           |

    - ### Methods inherited from class oracle.jms.AQjmsObject

      `checkClosed, children, finalize, getID, getParent, isOpen, localClose, preClose`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### setDisableMessageID

          public void setDisableMessageID(boolean value)
                                   throws JMSException

      Sets whether message IDs can be disabled.
      Since message ID's take some effort to create and increase a message's size, some JMS providers may be able to reduce message overhead if they are given a hint that message IDs are not used by an application. When a client sets a Producer to disable message IDs, it is saying that no one depends on the message IDs of the messages it produces. Produced messages must then either have message ID set to `null` or, if the hint is ignored, have message ID set to its normal unique value.

      Message IDs are enabled by default.

      Specified by:
      [`setDisableMessageID`](../../javax/jms/MessageProducer.md) in interface [`MessageProducer`](../../javax/jms/MessageProducer.md)

      Parameters:
      `value` - hint that message IDs can be disabled

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the disable message IDs hint is not set due to some error.

    <!-- -->

    - #### getDisableMessageID

          public boolean getDisableMessageID()
                                      throws JMSException

      Gets an indication of whether message IDs are disabled.
      Note that the returned value reflects the client-provided hint and can therefore only be used to determine whether or not message IDs *might* be set to null, not if they *are* being set to null.

      Specified by:
      [`getDisableMessageID`](../../javax/jms/MessageProducer.md) in interface [`MessageProducer`](../../javax/jms/MessageProducer.md)

      Returns:
      an indication of whether message IDs are disabled

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the disable message IDs hint is not retrieved due to some error.

    <!-- -->

    - #### setDisableMessageTimestamp

          public void setDisableMessageTimestamp(boolean value)
                                          throws JMSException

      Sets whether message timestamps can be disabled.
      Message timestamps are enabled by default.

      Specified by:
      [`setDisableMessageTimestamp`](../../javax/jms/MessageProducer.md) in interface [`MessageProducer`](../../javax/jms/MessageProducer.md)

      Parameters:
      `value` - hint that message timestamps can be disabled

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the disable message timestamp hint is not set due to some error.

    <!-- -->

    - #### getDisableMessageTimestamp

          public boolean getDisableMessageTimestamp()
                                             throws JMSException

      Gets an indication of whether message timestamps are disabled.
      Note that the returned value reflects the client-provided hint and can therefore only be used to determine whether or not message timestamps *might* be set to zero, not if they *are* being set to zero.

      Specified by:
      [`getDisableMessageTimestamp`](../../javax/jms/MessageProducer.md) in interface [`MessageProducer`](../../javax/jms/MessageProducer.md)

      Returns:
      an indication of whether message IDs are disabled

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the disable message timestamp hint is not retrieved due to some error.

    <!-- -->

    - #### setDeliveryMode

          public void setDeliveryMode(int deliveryMode)
                               throws JMSException

      Sets this producer's default delivery mode.
      Delivery mode is set to `PERSISTENT` by default.

      Specified by:
      [`setDeliveryMode`](../../javax/jms/MessageProducer.md) in interface [`MessageProducer`](../../javax/jms/MessageProducer.md)

      Parameters:
      `deliveryMode` - the message delivery mode for this message producer (`PERSISTENT` or `NON_PERSISTENT`)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the delivery mode is not set due to some error.

      See Also:
      [`MessageProducer.getDeliveryMode()`](../../javax/jms/MessageProducer.md), [`DeliveryMode.NON_PERSISTENT`](../../javax/jms/DeliveryMode.md), [`DeliveryMode.PERSISTENT`](../../javax/jms/DeliveryMode.md), [`Message.DEFAULT_DELIVERY_MODE`](../../javax/jms/Message.md)

    <!-- -->

    - #### getDeliveryMode

          public int getDeliveryMode()
                              throws JMSException

      Gets this producer's default delivery mode.
      Specified by:
      [`getDeliveryMode`](../../javax/jms/MessageProducer.md) in interface [`MessageProducer`](../../javax/jms/MessageProducer.md)

      Returns:
      the message delivery mode

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the delivery mode is not retrieved due to some error.

      See Also:
      [`MessageProducer.setDeliveryMode(int)`](../../javax/jms/MessageProducer.md)

    <!-- -->

    - #### setPriority

          public void setPriority(int priority)
                           throws JMSException

      Sets this producer's default priority. JMS defines a ten level priority value with 0 as the lowest priority and 9 as the highest. Priority is set to 4 by default.
      Specified by:
      [`setPriority`](../../javax/jms/MessageProducer.md) in interface [`MessageProducer`](../../javax/jms/MessageProducer.md)

      Parameters:
      `priority` - the message priority for this message producer

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the priority is not set due to some error.

      See Also:
      [`MessageProducer.getPriority()`](../../javax/jms/MessageProducer.md), [`Message.DEFAULT_PRIORITY`](../../javax/jms/Message.md)

    <!-- -->

    - #### getPriority

          public int getPriority()
                          throws JMSException

      Gets this producer's default priority. JMS defines a ten level priority value with 0 as the lowest priority and 9 as the highest.
      Specified by:
      [`getPriority`](../../javax/jms/MessageProducer.md) in interface [`MessageProducer`](../../javax/jms/MessageProducer.md)

      Returns:
      the message priority

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the priority is not retrieved due to some error.

      See Also:
      [`MessageProducer.setPriority(int)`](../../javax/jms/MessageProducer.md)

    <!-- -->

    - #### setTimeToLive

          public void setTimeToLive(long timeToLive)
                             throws JMSException

      Sets the default length of time in milliseconds from its dispatch time that a produced message should be retained by the message system.
      Time-to-live is set to zero by default.

      Specified by:
      [`setTimeToLive`](../../javax/jms/MessageProducer.md) in interface [`MessageProducer`](../../javax/jms/MessageProducer.md)

      Parameters:
      `timeToLive` - the message time-to-live in milliseconds; zero is unlimited

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if time-to-live is not set due to some error.

      See Also:
      [`MessageProducer.getTimeToLive()`](../../javax/jms/MessageProducer.md), [`Message.DEFAULT_TIME_TO_LIVE`](../../javax/jms/Message.md)

    <!-- -->

    - #### getTimeToLive

          public long getTimeToLive()
                             throws JMSException

      Gets the default length of time in milliseconds from its dispatch time that a produced message should be retained by the message system.
      Specified by:
      [`getTimeToLive`](../../javax/jms/MessageProducer.md) in interface [`MessageProducer`](../../javax/jms/MessageProducer.md)

      Returns:
      the message time-to-live in milliseconds; zero is unlimited

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if time-to-live is not retrieved due to some error.

      See Also:
      [`MessageProducer.setTimeToLive(long)`](../../javax/jms/MessageProducer.md)

    <!-- -->

    - #### getQueue

          public Queue getQueue()
                         throws JMSException

      Gets the queue associated with this queue sender.
      Returns:
      the queue

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the queue is not retrieved due to some error.

    <!-- -->

    - #### setTransformation

          public void setTransformation(java.lang.String transformation)

      Sets this producer's transformation.
      Parameters:
      `transformation` - the transformation to use when sending messages

    <!-- -->

    - #### getTransformation

          public java.lang.String getTransformation()

      Gets this producer's transformation.
      Returns:
      the transformation used when sending messages

    <!-- -->

    - #### send

          public void send(Message message)
                    throws JMSException

      Sends a message.
      Specified by:
      [`send`](../../javax/jms/MessageProducer.md) in interface [`MessageProducer`](../../javax/jms/MessageProducer.md)

      Parameters:
      `message` - the message to send

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message is not sent due to some error.

      See Also:
      [`Session.createProducer(javax.jms.Destination)`](../../javax/jms/Session.md), [`MessageProducer`](../../javax/jms/MessageProducer.md)

    <!-- -->

    - #### send

          public void send(Message message,
                           int deliveryMode,
                           int priority,
                           long timeToLive)
                    throws JMSException

      Sends a message.
      Specified by:
      [`send`](../../javax/jms/MessageProducer.md) in interface [`MessageProducer`](../../javax/jms/MessageProducer.md)

      Parameters:
      `message` - the message to send

      `deliveryMode` - the delivery mode for `message` ([`DeliveryMode.PERSISTENT`](../../javax/jms/DeliveryMode.md) or [`DeliveryMode.NON_PERSISTENT`](../../javax/jms/DeliveryMode.md))

      `priority` - the priority for `message` (JMS defines 0 as lowest and 9 as highest)

      `timeToLive` - the time-to-live for `message` (milliseconds; 0 means no limit)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message is not sent due to some error.

      See Also:
      [`Session.createProducer(javax.jms.Destination)`](../../javax/jms/Session.md)

    <!-- -->

    - #### send

          public void send(Queue queue,
                           Message message)
                    throws JMSException

      Sends a message.
      Parameters:
      `queue` - The destination queue where the message has to be sent. This overrides the default queue of the Message Producer.

      `message` - the message to send

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message is not sent due to some error.

    <!-- -->

    - #### send

          public void send(Queue queue,
                           Message message,
                           int deliveryMode,
                           int priority,
                           long timeToLive)
                    throws JMSException

      Sends a message.
      Parameters:
      `queue` - The destination queue where the message has to be sent. This overrides the default queue of the Message Producer.

      `message` - the message to send

      `deliveryMode` - the delivery mode for `message` ([`DeliveryMode.PERSISTENT`](../../javax/jms/DeliveryMode.md) or [`DeliveryMode.NON_PERSISTENT`](../../javax/jms/DeliveryMode.md))

      `priority` - the priority for `message` (JMS defines 0 as lowest and 9 as highest)

      `timeToLive` - the time-to-live for `message` (milliseconds; 0 means no limit)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message is not sent due to some error.

    <!-- -->

    - #### bufferSend

          public void bufferSend(Queue queue,
                                 Message message,
                                 int priority,
                                 long timeToLive)
                          throws JMSException

      Sends a non-persistent message to an in-memory portion of the queue for an unidentified message producer, specifying delivery mode, priority and time-to-live. When the in-memory queue is used, the enqueue operation is required to be in immediate visibility mode. (This requirement might be removed in a later release.) When a sharded queue is used, this method throws an exception. Use the JMS standard APIs to send non-persistent messages to sharded queues.
      Parameters:
      `queue` - The destination queue where the message has to be sent. This overrides the default queue of the Message Producer.

      `message` - the message to send

      `priority` - the priority for `message` (JMS defines 0 as lowest and 9 as highest)

      `timeToLive` - the time-to-live for `message` (milliseconds; 0 means no limit)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message is not sent due to some error.

    <!-- -->

    - #### getTopic

          public Topic getTopic()
                         throws JMSException

      Gets the topic associated with this publisher.
      Returns:
      this publisher's topic

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the topic is not retrieved due to some error.

    <!-- -->

    - #### publish

          public void publish(Message message)
                       throws JMSException

      Publishes a message.
      Parameters:
      `message` - the message to publish

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message is not published due to some error.

    <!-- -->

    - #### publish

          public void publish(Message message,
                              int deliveryMode,
                              int priority,
                              long timeToLive)
                       throws JMSException

      Publishes a message to the topic specifying delivery mode, priority and time-to-live.
      Parameters:
      `message` - the message to publish

      `deliveryMode` - the delivery mode for `message` ([`DeliveryMode.PERSISTENT`](../../javax/jms/DeliveryMode.md) or [`DeliveryMode.NON_PERSISTENT`](../../javax/jms/DeliveryMode.md))

      `priority` - the priority for `message` (JMS defines 0 as lowest and 9 as highest)

      `timeToLive` - the time-to-live for `message` (milliseconds; 0 means no limit)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message is not published due to some error.

    <!-- -->

    - #### publish

          public void publish(Topic topic,
                              Message message)
                       throws JMSException

      Publishes a message to a topic for an unidentified message producer. Uses the producer's default delivery mode, time-to-live and priority.
      Parameters:
      `topic` - The topic to which to publish the message. This overrides the default topic of the Message Producer.

      `message` - the message to publish

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if message is not published due to some error.

    <!-- -->

    - #### publish

          public void publish(Topic topic,
                              Message message,
                              int deliveryMode,
                              int priority,
                              long timeToLive)
                       throws JMSException

      Publishes a message to a topic for an unidentified message producer, specifying delivery mode, priority and time-to-live.
      Parameters:
      `topic` - The topic to which to publish the message. This overrides the default topic of the Message Producer.

      `message` - the message to publish

      `deliveryMode` - the delivery mode for `message` ([`DeliveryMode.PERSISTENT`](../../javax/jms/DeliveryMode.md) or [`DeliveryMode.NON_PERSISTENT`](../../javax/jms/DeliveryMode.md))

      `priority` - the priority for `message` (JMS defines 0 as lowest and 9 as highest)

      `timeToLive` - the time-to-live for `message` (milliseconds; 0 means no limit)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message is not published due to some error.

    <!-- -->

    - #### bufferPublish

          public void bufferPublish(Topic topic,
                                    Message message,
                                    int priority,
                                    long timeToLive)
                             throws JMSException

      Publishes a non-persistent message to an in-memory portion of the topic for an unidentified message producer, specifying delivery mode, priority and time-to-live. When the in-memory queue is used, the enqueue operation is required to be in immediate visibility mode. (This requirement might be removed in a later release.) When a sharded queue is used, this method throws an exception. Use the JMS standard APIs to send non-persistent messages to sharded queues.
      Parameters:
      `topic` - The topic to which to publish the message. This overrides the default topic of the Message Producer.

      `message` - the message to publish

      `priority` - the priority for `message` (JMS defines 0 as lowest and 9 as highest)

      `timeToLive` - the time-to-live for `message` (milliseconds; 0 means no limit)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message is not published due to some error.

    <!-- -->

    - #### publish

          public void publish(Message message,
                              oracle.jms.AQjmsAgent[] recipientList)
                       throws JMSException

      Publishes a message to a specific list of recipients
      Parameters:
      `message` - the message to publish

      `recipientList` - the list of recipients to which the message is to be published

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message is not published due to some error.

    <!-- -->

    - #### publish

          public void publish(Topic topic,
                              Message message,
                              oracle.jms.AQjmsAgent[] recipientList)
                       throws JMSException

      Publishes a message to a topic by specifying a list of recipients.
      Parameters:
      `topic` - The topic to which to publish the message. This overrides the default topic of the Message Producer.

      `message` - the message to publish

      `recipientList` - the list of recipients to which the message is to be published

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message is not published due to some error.

    <!-- -->

    - #### publish

          public void publish(Message message,
                              oracle.jms.AQjmsAgent[] recipientList,
                              int deliveryMode,
                              int priority,
                              long timeToLive)
                       throws JMSException

      Publishes a message to a topic by specifying a list of recipients, delivery mode, priority and time-to-live
      Parameters:
      `message` - the message to publish

      `recipientList` - the list of recipients to which the message is to be published

      `deliveryMode` - the delivery mode for `message` ([`DeliveryMode.PERSISTENT`](../../javax/jms/DeliveryMode.md) or [`DeliveryMode.NON_PERSISTENT`](../../javax/jms/DeliveryMode.md))

      `priority` - the priority for `message` (JMS defines 0 as lowest and 9 as highest)

      `timeToLive` - the time-to-live for `message` (milliseconds; 0 means no limit)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message is not published due to some error.

    <!-- -->

    - #### publish

          public void publish(Topic topic,
                              Message message,
                              oracle.jms.AQjmsAgent[] recipientList,
                              int deliveryMode,
                              int priority,
                              long timeToLive)
                       throws JMSException

      Publishes a message to a topic by specifying a list of recipients, delivery mode, priority and time-to-live
      Parameters:
      `topic` - The topic to which to publish the message. This overrides the default topic of the Message Producer.

      `message` - the message to publish

      `recipientList` - the list of recipients to which the message is to be published

      `deliveryMode` - the delivery mode for `message` ([`DeliveryMode.PERSISTENT`](../../javax/jms/DeliveryMode.md) or [`DeliveryMode.NON_PERSISTENT`](../../javax/jms/DeliveryMode.md))

      `priority` - the priority for `message` (JMS defines 0 as lowest and 9 as highest)

      `timeToLive` - the time-to-live for `message` (milliseconds; 0 means no limit)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message is not published due to some error.

    <!-- -->

    - #### close

          public void close()
                     throws JMSException

      Description copied from class: `oracle.jms.AQjmsObject`
      Public for test harness purposes
      Specified by:
      [`close`](../../javax/jms/MessageProducer.md) in interface [`MessageProducer`](../../javax/jms/MessageProducer.md)

      Overrides:
      `close` in class `oracle.jms.AQjmsObject`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to close the producer due to some internal error.

    <!-- -->

    - #### getDestination

          public Destination getDestination()
                                     throws JMSException

      Gets the destination associated with this `MessageProducer`.
      Specified by:
      [`getDestination`](../../javax/jms/MessageProducer.md) in interface [`MessageProducer`](../../javax/jms/MessageProducer.md)

      Returns:
      this producer's `Destination/`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the destination is not retrieved due to some error.

      Since:
      1.1

    <!-- -->

    - #### send

          public void send(Destination destination,
                           Message message)
                    throws JMSException

      Sends a message to a destination for an unidentified message producer. Uses this `MessageProducer`'s default delivery mode, priority, and time to live.
      Typically, a message producer is assigned a destination at creation time; however, the JMS API also supports unidentified message producers, which require that the destination be supplied every time a message is sent.

      Specified by:
      [`send`](../../javax/jms/MessageProducer.md) in interface [`MessageProducer`](../../javax/jms/MessageProducer.md)

      Parameters:
      `destination` - the destination to send this message to

      `message` - the message to send

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message is not sent due to some error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if an invalid message is specified.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if a client uses this method with an invalid destination.

      `java.lang.UnsupportedOperationException` - if a client uses this method with a `MessageProducer` that specified a destination at creation time.

      Since:
      1.1

      See Also:
      [`Session.createProducer(javax.jms.Destination)`](../../javax/jms/Session.md), [`MessageProducer`](../../javax/jms/MessageProducer.md)

    <!-- -->

    - #### send

          public void send(Destination destination,
                           Message message,
                           int deliveryMode,
                           int priority,
                           long timeToLive)
                    throws JMSException

      Sends a message to a destination for an unidentified message producer, specifying delivery mode, priority and time-to-live.
      Typically, a message producer is assigned a destination at creation time; however, the JMS API also supports unidentified message producers, which require that the destination be supplied every time a message is sent.

      Specified by:
      [`send`](../../javax/jms/MessageProducer.md) in interface [`MessageProducer`](../../javax/jms/MessageProducer.md)

      Parameters:
      `destination` - the destination to send this message to

      `message` - the message to send

      `deliveryMode` - the delivery mode for `message` ([`DeliveryMode.PERSISTENT`](../../javax/jms/DeliveryMode.md) or [`DeliveryMode.NON_PERSISTENT`](../../javax/jms/DeliveryMode.md))

      `priority` - the priority for `message` (JMS defines 0 as lowest and 9 as highest)

      `timeToLive` - the time-to-live for `message` (milliseconds; 0 means no limit)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message is not sent due to some error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if an invalid message is specified.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if a client uses this method with an invalid destination.

      Since:
      1.1

      See Also:
      [`Session.createProducer(javax.jms.Destination)`](../../javax/jms/Session.md)

    <!-- -->

    - #### bufferSend

          public void bufferSend(Destination destination,
                                 Message message,
                                 int priority,
                                 long timeToLive)
                          throws JMSException

      Sends a non-persistent message to an in-memory portion of the destination for an unidentified message producer, specifying priority and time-to-live. When the in-memory queue is used, the enqueue operation is required to be in immediate visibility mode. (This requirement might be removed in a later release.) When a sharded queue is used, this method throws an exception. Use the JMS standard APIs to send non-persistent messages to sharded queues.
      Parameters:
      `destination` - the destination to send this message to

      `message` - the message to send

      `priority` - the priority for `message` (JMS defines 0 as lowest and 9 as highest)

      `timeToLive` - the time-to-live for `message` (milliseconds; 0 means no limit)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message is not sent due to some error.

      [`MessageFormatException`](../../javax/jms/MessageFormatException.md) - if an invalid message is specified.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if a client uses this method with an invalid destination.

      See Also:
      [`Session.createProducer(javax.jms.Destination)`](../../javax/jms/Session.md)

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

- [Prev Class](AQjmsParseException.md)
- [Next Class](AQjmsQueueBrowser.md)

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
