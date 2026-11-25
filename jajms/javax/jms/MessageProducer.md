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

- [Prev Class](MessageNotWriteableException.md)
- [Next Class](ObjectMessage.md)

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

## Interface MessageProducer

- All Known Subinterfaces:
  [AQjmsQueueSender](../../oracle/jms/AQjmsQueueSender.md), [AQjmsTopicPublisher](../../oracle/jms/AQjmsTopicPublisher.md), [QueueSender](QueueSender.md), [TopicPublisher](TopicPublisher.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsProducer](../../oracle/jms/AQjmsProducer.md)

  ------------------------------------------------------------------------



      public interface MessageProducer

  A client uses a `MessageProducer` object to send messages to a destination. A `MessageProducer` object is created by passing a `Destination` object to a message-producer creation method supplied by a session.
  `MessageProducer` is the parent interface for all message producers.

  A client also has the option of creating a message producer without supplying a destination. In this case, a destination must be provided with every send operation. A typical use for this kind of message producer is to send replies to requests using the request's `JMSReplyTo` destination.

  A client can specify a default delivery mode, priority, and time to live for messages sent by a message producer. It can also specify the delivery mode, priority, and time to live for an individual message.

  A client can specify a time-to-live value in milliseconds for each message it sends. This value defines a message expiration time that is the sum of the message's time-to-live and the GMT when it is sent (for transacted sends, this is the time the client sends the message, not the time the transaction is committed).

  A JMS provider should do its best to expire messages accurately; however, the JMS API does not define the accuracy provided.

  See Also:
  [`TopicPublisher`](TopicPublisher.md), [`QueueSender`](QueueSender.md), [`Session.createProducer(javax.jms.Destination)`](Session.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type               | Method and Description                                                                                                                                                                                                                                                     |
    |---------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                          | `close``()`<br>Closes the message producer.                                                                                                                                                                                                                                |
    | `int`                           | `getDeliveryMode``()`<br>Gets the producer's default delivery mode.                                                                                                                                                                                                        |
    | [`Destination`](Destination.md) | `getDestination``()`<br>Gets the destination associated with this `MessageProducer`.                                                                                                                                                                                       |
    | `boolean`                       | `getDisableMessageID``()`<br>Gets an indication of whether message IDs are disabled.                                                                                                                                                                                       |
    | `boolean`                       | `getDisableMessageTimestamp``()`<br>Gets an indication of whether message timestamps are disabled.                                                                                                                                                                         |
    | `int`                           | `getPriority``()`<br>Gets the producer's default priority.                                                                                                                                                                                                                 |
    | `long`                          | `getTimeToLive``()`<br>Gets the default length of time in milliseconds from its dispatch time that a produced message should be retained by the message system.                                                                                                            |
    | `void`                          | `send``(`[`Destination`](Destination.md)` destination, `[`Message`](Message.md)` message)`<br>Sends a message to a destination for an unidentified message producer.                                                                                                       |
    | `void`                          | `send``(`[`Destination`](Destination.md)` destination, `[`Message`](Message.md)` message, int deliveryMode, int priority, long timeToLive)`<br>Sends a message to a destination for an unidentified message producer, specifying delivery mode, priority and time to live. |
    | `void`                          | `send``(`[`Message`](Message.md)` message)`<br>Sends a message using the `MessageProducer`'s default delivery mode, priority, and time to live.                                                                                                                            |
    | `void`                          | `send``(`[`Message`](Message.md)` message, int deliveryMode, int priority, long timeToLive)`<br>Sends a message to the destination, specifying delivery mode, priority, and time to live.                                                                                  |
    | `void`                          | `setDeliveryMode``(int deliveryMode)`<br>Sets the producer's default delivery mode.                                                                                                                                                                                        |
    | `void`                          | `setDisableMessageID``(boolean value)`<br>Sets whether message IDs are disabled.                                                                                                                                                                                           |
    | `void`                          | `setDisableMessageTimestamp``(boolean value)`<br>Sets whether message timestamps are disabled.                                                                                                                                                                             |
    | `void`                          | `setPriority``(int defaultPriority)`<br>Sets the producer's default priority.                                                                                                                                                                                              |
    | `void`                          | `setTimeToLive``(long timeToLive)`<br>Sets the default length of time in milliseconds from its dispatch time that a produced message should be retained by the message system.                                                                                             |

<!-- -->

- - ### Method Detail

    - #### setDisableMessageID

          void setDisableMessageID(boolean value)
                            throws JMSException

      Sets whether message IDs are disabled.
      Since message IDs take some effort to create and increase a message's size, some JMS providers may be able to optimize message overhead if they are given a hint that the message ID is not used by an application. By calling the `setDisableMessageID` method on this message producer, a JMS client enables this potential optimization for all messages sent by this message producer. If the JMS provider accepts this hint, these messages must have the message ID set to null; if the provider ignores the hint, the message ID must be set to its normal unique value.

      Message IDs are enabled by default.

      Parameters:
      `value` - indicates if message IDs are disabled

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to set message ID to disabled due to some internal error.

    <!-- -->

    - #### getDisableMessageID

          boolean getDisableMessageID()
                               throws JMSException

      Gets an indication of whether message IDs are disabled.
      Returns:
      an indication of whether message IDs are disabled

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to determine if message IDs are disabled due to some internal error.

    <!-- -->

    - #### setDisableMessageTimestamp

          void setDisableMessageTimestamp(boolean value)
                                   throws JMSException

      Sets whether message timestamps are disabled.
      Since timestamps take some effort to create and increase a message's size, some JMS providers may be able to optimize message overhead if they are given a hint that the timestamp is not used by an application. By calling the `setDisableMessageTimestamp` method on this message producer, a JMS client enables this potential optimization for all messages sent by this message producer. If the JMS provider accepts this hint, these messages must have the timestamp set to zero; if the provider ignores the hint, the timestamp must be set to its normal value.

      Message timestamps are enabled by default.

      Parameters:
      `value` - indicates if message timestamps are disabled

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to set timestamps to disabled due to some internal error.

    <!-- -->

    - #### getDisableMessageTimestamp

          boolean getDisableMessageTimestamp()
                                      throws JMSException

      Gets an indication of whether message timestamps are disabled.
      Returns:
      an indication of whether message timestamps are disabled

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to determine if timestamps are disabled due to some internal error.

    <!-- -->

    - #### setDeliveryMode

          void setDeliveryMode(int deliveryMode)
                        throws JMSException

      Sets the producer's default delivery mode.
      Delivery mode is set to `PERSISTENT` by default.

      Parameters:
      `deliveryMode` - the message delivery mode for this message producer; legal values are `DeliveryMode.NON_PERSISTENT` and `DeliveryMode.PERSISTENT`

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to set the delivery mode due to some internal error.

      See Also:
      `MessageProducer.getDeliveryMode()`, [`DeliveryMode.NON_PERSISTENT`](DeliveryMode.md), [`DeliveryMode.PERSISTENT`](DeliveryMode.md), [`Message.DEFAULT_DELIVERY_MODE`](Message.md)

    <!-- -->

    - #### getDeliveryMode

          int getDeliveryMode()
                       throws JMSException

      Gets the producer's default delivery mode.
      Returns:
      the message delivery mode for this message producer

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the delivery mode due to some internal error.

      See Also:
      `MessageProducer.setDeliveryMode(int)`

    <!-- -->

    - #### setPriority

          void setPriority(int defaultPriority)
                    throws JMSException

      Sets the producer's default priority.
      The JMS API defines ten levels of priority value, with 0 as the lowest priority and 9 as the highest. Clients should consider priorities 0-4 as gradations of normal priority and priorities 5-9 as gradations of expedited priority. Priority is set to 4 by default.

      Parameters:
      `defaultPriority` - the message priority for this message producer; must be a value between 0 and 9

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to set the priority due to some internal error.

      See Also:
      `MessageProducer.getPriority()`, [`Message.DEFAULT_PRIORITY`](Message.md)

    <!-- -->

    - #### getPriority

          int getPriority()
                   throws JMSException

      Gets the producer's default priority.
      Returns:
      the message priority for this message producer

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the priority due to some internal error.

      See Also:
      `MessageProducer.setPriority(int)`

    <!-- -->

    - #### setTimeToLive

          void setTimeToLive(long timeToLive)
                      throws JMSException

      Sets the default length of time in milliseconds from its dispatch time that a produced message should be retained by the message system.
      Time to live is set to zero by default.

      Parameters:
      `timeToLive` - the message time to live in milliseconds; zero is unlimited

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to set the time to live due to some internal error.

      See Also:
      `MessageProducer.getTimeToLive()`, [`Message.DEFAULT_TIME_TO_LIVE`](Message.md)

    <!-- -->

    - #### getTimeToLive

          long getTimeToLive()
                      throws JMSException

      Gets the default length of time in milliseconds from its dispatch time that a produced message should be retained by the message system.
      Returns:
      the message time to live in milliseconds; zero is unlimited

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the time to live due to some internal error.

      See Also:
      `MessageProducer.setTimeToLive(long)`

    <!-- -->

    - #### getDestination

          Destination getDestination()
                              throws JMSException

      Gets the destination associated with this `MessageProducer`.
      Returns:
      this producer's `Destination/`

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the destination for this `MessageProducer` due to some internal error.

      Since:
      1.1

    <!-- -->

    - #### close

          void close()
              throws JMSException

      Closes the message producer.
      Since a provider may allocate some resources on behalf of a `MessageProducer` outside the Java virtual machine, clients should close them when they are not needed. Relying on garbage collection to eventually reclaim these resources may not be timely enough.

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to close the producer due to some internal error.

    <!-- -->

    - #### send

          void send(Message message)
             throws JMSException

      Sends a message using the `MessageProducer`'s default delivery mode, priority, and time to live.
      Parameters:
      `message` - the message to send

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to send the message due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if an invalid message is specified.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if a client uses this method with a `MessageProducer` with an invalid destination.

      `java.lang.UnsupportedOperationException` - if a client uses this method with a `MessageProducer` that did not specify a destination at creation time.

      Since:
      1.1

      See Also:
      [`Session.createProducer(javax.jms.Destination)`](Session.md), `MessageProducer`

    <!-- -->

    - #### send

          void send(Message message,
                    int deliveryMode,
                    int priority,
                    long timeToLive)
             throws JMSException

      Sends a message to the destination, specifying delivery mode, priority, and time to live.
      Parameters:
      `message` - the message to send

      `deliveryMode` - the delivery mode to use

      `priority` - the priority for this message

      `timeToLive` - the message's lifetime (in milliseconds)

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to send the message due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if an invalid message is specified.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if a client uses this method with a `MessageProducer` with an invalid destination.

      `java.lang.UnsupportedOperationException` - if a client uses this method with a `MessageProducer` that did not specify a destination at creation time.

      Since:
      1.1

      See Also:
      [`Session.createProducer(javax.jms.Destination)`](Session.md)

    <!-- -->

    - #### send

          void send(Destination destination,
                    Message message)
             throws JMSException

      Sends a message to a destination for an unidentified message producer. Uses the `MessageProducer`'s default delivery mode, priority, and time to live.
      Typically, a message producer is assigned a destination at creation time; however, the JMS API also supports unidentified message producers, which require that the destination be supplied every time a message is sent.

      Parameters:
      `destination` - the destination to send this message to

      `message` - the message to send

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to send the message due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if an invalid message is specified.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if a client uses this method with an invalid destination.

      `java.lang.UnsupportedOperationException` - if a client uses this method with a `MessageProducer` that specified a destination at creation time.

      Since:
      1.1

      See Also:
      [`Session.createProducer(javax.jms.Destination)`](Session.md), `MessageProducer`

    <!-- -->

    - #### send

          void send(Destination destination,
                    Message message,
                    int deliveryMode,
                    int priority,
                    long timeToLive)
             throws JMSException

      Sends a message to a destination for an unidentified message producer, specifying delivery mode, priority and time to live.
      Typically, a message producer is assigned a destination at creation time; however, the JMS API also supports unidentified message producers, which require that the destination be supplied every time a message is sent.

      Parameters:
      `destination` - the destination to send this message to

      `message` - the message to send

      `deliveryMode` - the delivery mode to use

      `priority` - the priority for this message

      `timeToLive` - the message's lifetime (in milliseconds)

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to send the message due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if an invalid message is specified.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if a client uses this method with an invalid destination.

      Since:
      1.1

      See Also:
      [`Session.createProducer(javax.jms.Destination)`](Session.md)

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

- [Prev Class](MessageNotWriteableException.md)
- [Next Class](ObjectMessage.md)

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
