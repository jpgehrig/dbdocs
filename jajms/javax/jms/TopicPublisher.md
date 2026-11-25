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

- [Prev Class](TopicConnectionFactory.md)
- [Next Class](TopicRequestor.md)

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

## Interface TopicPublisher

- All Superinterfaces:
  [MessageProducer](MessageProducer.md)

  <!-- -->

  All Known Subinterfaces:
  [AQjmsTopicPublisher](../../oracle/jms/AQjmsTopicPublisher.md)

  ------------------------------------------------------------------------



      public interface TopicPublisher
      extends MessageProducer

  A client uses a `TopicPublisher` object to publish messages on a topic. A `TopicPublisher` object is the publish-subscribe form of a message producer.
  Normally, the `Topic` is specified when a `TopicPublisher` is created. In this case, an attempt to use the `publish` methods for an unidentified `TopicPublisher` will throw a `java.lang.UnsupportedOperationException`.

  If the `TopicPublisher` is created with an unidentified `Topic`, an attempt to use the `publish` methods that assume that the `Topic` has been identified will throw a `java.lang.UnsupportedOperationException`.

  During the execution of its `publish` method, a message must not be changed by other threads within the client. If the message is modified, the result of the `publish` is undefined.

  After publishing a message, a client may retain and modify it without affecting the message that has been published. The same message object may be published multiple times.

  The following message headers are set as part of publishing a message: `JMSDestination`, `JMSDeliveryMode`, `JMSExpiration`, `JMSPriority`, `JMSMessageID` and `JMSTimeStamp`. When the message is published, the values of these headers are ignored. After completion of the `publish`, the headers hold the values specified by the method publishing the message. It is possible for the `publish` method not to set `JMSMessageID` and `JMSTimeStamp` if the setting of these headers is explicitly disabled by the `MessageProducer.setDisableMessageID` or `MessageProducer.setDisableMessageTimestamp` method.

  Creating a `MessageProducer` provides the same features as creating a `TopicPublisher`. A `MessageProducer` object is recommended when creating new code. The `TopicPublisher` is provided to support existing code.

  Because `TopicPublisher` inherits from `MessageProducer`, it inherits the `send` methods that are a part of the `MessageProducer` interface. Using the `send` methods will have the same effect as using the `publish` methods: they are functionally the same.

  See Also:
  [`Session.createProducer(Destination)`](Session.md), [`TopicSession.createPublisher(Topic)`](TopicSession.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type   | Method and Description                                                                                                                                                                                                                                    |
    |---------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`Topic`](Topic.md) | `getTopic``()`<br>Gets the topic associated with this `TopicPublisher`.                                                                                                                                                                                   |
    | `void`              | `publish``(`[`Message`](Message.md)` message)`<br>Publishes a message to the topic.                                                                                                                                                                       |
    | `void`              | `publish``(`[`Message`](Message.md)` message, int deliveryMode, int priority, long timeToLive)`<br>Publishes a message to the topic, specifying delivery mode, priority, and time to live.                                                                |
    | `void`              | `publish``(`[`Topic`](Topic.md)` topic, `[`Message`](Message.md)` message)`<br>Publishes a message to a topic for an unidentified message producer.                                                                                                       |
    | `void`              | `publish``(`[`Topic`](Topic.md)` topic, `[`Message`](Message.md)` message, int deliveryMode, int priority, long timeToLive)`<br>Publishes a message to a topic for an unidentified message producer, specifying delivery mode, priority and time to live. |

    - ### Methods inherited from interface javax.jms.[MessageProducer](MessageProducer.md)

      [`close`](MessageProducer.md)`, `[`getDeliveryMode`](MessageProducer.md)`, `[`getDestination`](MessageProducer.md)`, `[`getDisableMessageID`](MessageProducer.md)`, `[`getDisableMessageTimestamp`](MessageProducer.md)`, `[`getPriority`](MessageProducer.md)`, `[`getTimeToLive`](MessageProducer.md)`, `[`send`](MessageProducer.md)`, `[`send`](MessageProducer.md)`, `[`send`](MessageProducer.md)`, `[`send`](MessageProducer.md)`, `[`setDeliveryMode`](MessageProducer.md)`, `[`setDisableMessageID`](MessageProducer.md)`, `[`setDisableMessageTimestamp`](MessageProducer.md)`, `[`setPriority`](MessageProducer.md)`, `[`setTimeToLive`](MessageProducer.md)

<!-- -->

- - ### Method Detail

    - #### getTopic

          Topic getTopic()
                  throws JMSException

      Gets the topic associated with this `TopicPublisher`.
      Returns:
      this publisher's topic

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the topic for this `TopicPublisher` due to some internal error.

    <!-- -->

    - #### publish

          void publish(Message message)
                throws JMSException

      Publishes a message to the topic. Uses the `TopicPublisher`'s default delivery mode, priority, and time to live.
      Parameters:
      `message` - the message to publish

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to publish the message due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if an invalid message is specified.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if a client uses this method with a `TopicPublisher` with an invalid topic.

      `java.lang.UnsupportedOperationException` - if a client uses this method with a `TopicPublisher` that did not specify a topic at creation time.

      See Also:
      [`MessageProducer.getDeliveryMode()`](MessageProducer.md), [`MessageProducer.getTimeToLive()`](MessageProducer.md), [`MessageProducer.getPriority()`](MessageProducer.md)

    <!-- -->

    - #### publish

          void publish(Message message,
                       int deliveryMode,
                       int priority,
                       long timeToLive)
                throws JMSException

      Publishes a message to the topic, specifying delivery mode, priority, and time to live.
      Parameters:
      `message` - the message to publish

      `deliveryMode` - the delivery mode to use

      `priority` - the priority for this message

      `timeToLive` - the message's lifetime (in milliseconds)

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to publish the message due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if an invalid message is specified.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if a client uses this method with a `TopicPublisher` with an invalid topic.

      `java.lang.UnsupportedOperationException` - if a client uses this method with a `TopicPublisher` that did not specify a topic at creation time.

    <!-- -->

    - #### publish

          void publish(Topic topic,
                       Message message)
                throws JMSException

      Publishes a message to a topic for an unidentified message producer. Uses the `TopicPublisher`'s default delivery mode, priority, and time to live.
      Typically, a message producer is assigned a topic at creation time; however, the JMS API also supports unidentified message producers, which require that the topic be supplied every time a message is published.

      Parameters:
      `topic` - the topic to publish this message to

      `message` - the message to publish

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to publish the message due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if an invalid message is specified.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if a client uses this method with an invalid topic.

      See Also:
      [`MessageProducer.getDeliveryMode()`](MessageProducer.md), [`MessageProducer.getTimeToLive()`](MessageProducer.md), [`MessageProducer.getPriority()`](MessageProducer.md)

    <!-- -->

    - #### publish

          void publish(Topic topic,
                       Message message,
                       int deliveryMode,
                       int priority,
                       long timeToLive)
                throws JMSException

      Publishes a message to a topic for an unidentified message producer, specifying delivery mode, priority and time to live.
      Typically, a message producer is assigned a topic at creation time; however, the JMS API also supports unidentified message producers, which require that the topic be supplied every time a message is published.

      Parameters:
      `topic` - the topic to publish this message to

      `message` - the message to publish

      `deliveryMode` - the delivery mode to use

      `priority` - the priority for this message

      `timeToLive` - the message's lifetime (in milliseconds)

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to publish the message due to some internal error.

      [`MessageFormatException`](MessageFormatException.md) - if an invalid message is specified.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if a client uses this method with an invalid topic.

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

- [Prev Class](TopicConnectionFactory.md)
- [Next Class](TopicRequestor.md)

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
