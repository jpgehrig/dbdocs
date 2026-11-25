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

- [Prev Class](AQjmsTopicConnectionFactory.md)
- [Next Class](AQjmsTopicReceiver.md)

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

## Interface AQjmsTopicPublisher

- All Superinterfaces:
  [MessageProducer](../../javax/jms/MessageProducer.md), [TopicPublisher](../../javax/jms/TopicPublisher.md)

  ------------------------------------------------------------------------



      public interface AQjmsTopicPublisher
      extends TopicPublisher

  Adds Oracle® Database Advanced Queuing specific extensions to `javax.jms.TopicPublisher`
  Allows point to point publishing and use of transformations.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                                                                                                                                                                                                                                             |
    |--------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `java.lang.String` | `getTransformation``()`<br>Get the name of the transformation function of the `TopicPublisher`.                                                                                                                                                                                                                    |
    | `void`             | `publish``(`[`Message`](../../javax/jms/Message.md)` message, oracle.jms.AQjmsAgent[] recipient_list)`<br>Publish a Message to a specific list of recipients.                                                                                                                                                      |
    | `void`             | `publish``(`[`Message`](../../javax/jms/Message.md)` message, oracle.jms.AQjmsAgent[] recipient_list, int deliveryMode, int priority, long timeToLive)`<br>Publish a Message to a topic by specifying a list of recipients, delivery mode, priority and time to live.                                              |
    | `void`             | `publish``(`[`Topic`](../../javax/jms/Topic.md)` topic, `[`Message`](../../javax/jms/Message.md)` message, oracle.jms.AQjmsAgent[] recipient_list)`<br>Publish a Message to a topic by specifying a list of recipients.                                                                                            |
    | `void`             | `publish``(`[`Topic`](../../javax/jms/Topic.md)` topic, `[`Message`](../../javax/jms/Message.md)` message, oracle.jms.AQjmsAgent[] recipient_list, int deliveryMode, int priority, long timeToLive)`<br>Publish a Message to a topic by specifying a list of recipients, delivery mode, priority and time to live. |
    | `void`             | `setTransformation``(java.lang.String transformation)`<br>Set transformation for this sender.                                                                                                                                                                                                                      |

    - ### Methods inherited from interface javax.jms.[TopicPublisher](../../javax/jms/TopicPublisher.md)

      [`getTopic`](../../javax/jms/TopicPublisher.md)`, `[`publish`](../../javax/jms/TopicPublisher.md)`, `[`publish`](../../javax/jms/TopicPublisher.md)`, `[`publish`](../../javax/jms/TopicPublisher.md)`, `[`publish`](../../javax/jms/TopicPublisher.md)

    <!-- -->

    - ### Methods inherited from interface javax.jms.[MessageProducer](../../javax/jms/MessageProducer.md)

      [`close`](../../javax/jms/MessageProducer.md)`, `[`getDeliveryMode`](../../javax/jms/MessageProducer.md)`, `[`getDestination`](../../javax/jms/MessageProducer.md)`, `[`getDisableMessageID`](../../javax/jms/MessageProducer.md)`, `[`getDisableMessageTimestamp`](../../javax/jms/MessageProducer.md)`, `[`getPriority`](../../javax/jms/MessageProducer.md)`, `[`getTimeToLive`](../../javax/jms/MessageProducer.md)`, `[`send`](../../javax/jms/MessageProducer.md)`, `[`send`](../../javax/jms/MessageProducer.md)`, `[`send`](../../javax/jms/MessageProducer.md)`, `[`send`](../../javax/jms/MessageProducer.md)`, `[`setDeliveryMode`](../../javax/jms/MessageProducer.md)`, `[`setDisableMessageID`](../../javax/jms/MessageProducer.md)`, `[`setDisableMessageTimestamp`](../../javax/jms/MessageProducer.md)`, `[`setPriority`](../../javax/jms/MessageProducer.md)`, `[`setTimeToLive`](../../javax/jms/MessageProducer.md)

<!-- -->

- - ### Method Detail

    - #### publish

          void publish(Message message,
                       oracle.jms.AQjmsAgent[] recipient_list)
                throws JMSException

      Publish a Message to a specific list of recipients.
      Parameters:
      `message` - The message to be published

      `recipient_list` - The list of recipients to which the message is published. The recipients are of type `AQjmsAgent`.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to publish the mesasge due to some internal error.

    <!-- -->

    - #### publish

          void publish(Topic topic,
                       Message message,
                       oracle.jms.AQjmsAgent[] recipient_list)
                throws JMSException

      Publish a Message to a topic by specifying a list of recipients.
      Parameters:
      `topic` - The topic to which to publish the message. This overrides the default topic of the Message Producer.

      `message` - The message to be published.

      `recipient_list` - The list of recipients to which the message is published. The recipients are of type `AQjmsAgent`.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to publish the messgae due to some internal error.

    <!-- -->

    - #### publish

          void publish(Message message,
                       oracle.jms.AQjmsAgent[] recipient_list,
                       int deliveryMode,
                       int priority,
                       long timeToLive)
                throws JMSException

      Publish a Message to a topic by specifying a list of recipients, delivery mode, priority and time to live.
      Parameters:
      `message` - The message to be published.

      `recipient_list` - The list of recipients to which the message is published. The recipients are of type `AQjmsAgent`.

      `deliveryMode` - The delivery mode - `jjavax.jms.DeliveryMode.PERSISTENT` or `javax.jms.DeliveryMode.NON_PERSISTENT`.

      `priority` - The priority of the message.

      `timeToLive` - the message time to live in milliseconds. Zero is unlimited.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to publish the messgae due to some internal error.

    <!-- -->

    - #### publish

          void publish(Topic topic,
                       Message message,
                       oracle.jms.AQjmsAgent[] recipient_list,
                       int deliveryMode,
                       int priority,
                       long timeToLive)
                throws JMSException

      Publish a Message to a topic by specifying a list of recipients, delivery mode, priority and time to live.
      Parameters:
      `topic` - The topic to which to publish the message. This overrides the default topic of the Message Producer.

      `message` - The message to be published.

      `recipient_list` - The list of recipients to which the message is published. The recipients are of type `AQjmsAgent`.

      `deliveryMode` - The delivery mode - `javax.jms.DeliveryMode.PERSISTENT` or `javax.jms.DeliveryMode.NON_PERSISTENT`.

      `priority` - The priority of the message.

      `timeToLive` - the message time to live in milliseconds. Zero is unlimited.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to publish the messgae due to some internal error.

    <!-- -->

    - #### setTransformation

          void setTransformation(java.lang.String transformation)

      Set transformation for this sender. This transformation will be applied before the message is inserted in the topic.
      Parameters:
      `transformation` - transformation name.

    <!-- -->

    - #### getTransformation

          java.lang.String getTransformation()

      Get the name of the transformation function of the `TopicPublisher`.
      Returns:
      the name of the transformation function of the `TopicPublisher`.

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

- [Prev Class](AQjmsTopicConnectionFactory.md)
- [Next Class](AQjmsTopicReceiver.md)

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
