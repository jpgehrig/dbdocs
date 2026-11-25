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

- [Prev Class](TopicSession.md)
- [Next Class](TransactionInProgressException.md)

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

## Interface TopicSubscriber

- All Superinterfaces:
  [MessageConsumer](MessageConsumer.md)

  <!-- -->

  All Known Subinterfaces:
  [AQjmsTopicSubscriber](../../oracle/jms/AQjmsTopicSubscriber.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsConsumer](../../oracle/jms/AQjmsConsumer.md)

  ------------------------------------------------------------------------



      public interface TopicSubscriber
      extends MessageConsumer

  A client uses a `TopicSubscriber` object to receive messages that have been published to a topic. A `TopicSubscriber` object is the publish/subscribe form of a message consumer. A `MessageConsumer` can be created by using `Session.createConsumer`.
  A `TopicSession` allows the creation of multiple `TopicSubscriber` objects per topic. It will deliver each message for a topic to each subscriber eligible to receive it. Each copy of the message is treated as a completely separate message. Work done on one copy has no effect on the others; acknowledging one does not acknowledge the others; one message may be delivered immediately, while another waits for its subscriber to process messages ahead of it.

  Regular `TopicSubscriber` objects are not durable. They receive only messages that are published while they are active.

  Messages filtered out by a subscriber's message selector will never be delivered to the subscriber. From the subscriber's perspective, they do not exist.

  In some cases, a connection may both publish and subscribe to a topic. The subscriber `NoLocal` attribute allows a subscriber to inhibit the delivery of messages published by its own connection.

  If a client needs to receive all the messages published on a topic, including the ones published while the subscriber is inactive, it uses a durable `TopicSubscriber`. The JMS provider retains a record of this durable subscription and insures that all messages from the topic's publishers are retained until they are acknowledged by this durable subscriber or they have expired.

  Sessions with durable subscribers must always provide the same client identifier. In addition, each client must specify a name that uniquely identifies (within client identifier) each durable subscription it creates. Only one session at a time can have a `TopicSubscriber` for a particular durable subscription.

  A client can change an existing durable subscription by creating a durable `TopicSubscriber` with the same name and a new topic and/or message selector. Changing a durable subscription is equivalent to unsubscribing (deleting) the old one and creating a new one.

  The `unsubscribe` method is used to delete a durable subscription. The `unsubscribe` method can be used at the `Session` or `TopicSession` level. This method deletes the state being maintained on behalf of the subscriber by its provider.

  Creating a `MessageConsumer` provides the same features as creating a `TopicSubscriber`. To create a durable subscriber, use of `Session.CreateDurableSubscriber` is recommended. The `TopicSubscriber` is provided to support existing code.

  See Also:
  [`Session.createConsumer(javax.jms.Destination)`](Session.md), [`Session.createDurableSubscriber(javax.jms.Topic, java.lang.String)`](Session.md), [`TopicSession`](TopicSession.md), [`TopicSession.createSubscriber(javax.jms.Topic)`](TopicSession.md), [`MessageConsumer`](MessageConsumer.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type   | Method and Description                                                |
    |---------------------|-----------------------------------------------------------------------|
    | `boolean`           | `getNoLocal``()`<br>Gets the `NoLocal` attribute for this subscriber. |
    | [`Topic`](Topic.md) | `getTopic``()`<br>Gets the `Topic` associated with this subscriber.   |

    - ### Methods inherited from interface javax.jms.[MessageConsumer](MessageConsumer.md)

      [`close`](MessageConsumer.md)`, `[`getMessageListener`](MessageConsumer.md)`, `[`getMessageSelector`](MessageConsumer.md)`, `[`receive`](MessageConsumer.md)`, `[`receive`](MessageConsumer.md)`, `[`receiveNoWait`](MessageConsumer.md)`, `[`setMessageListener`](MessageConsumer.md)

<!-- -->

- - ### Method Detail

    - #### getTopic

          Topic getTopic()
                  throws JMSException

      Gets the `Topic` associated with this subscriber.
      Returns:
      this subscriber's `Topic`

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the topic for this topic subscriber due to some internal error.

    <!-- -->

    - #### getNoLocal

          boolean getNoLocal()
                      throws JMSException

      Gets the `NoLocal` attribute for this subscriber. The default value for this attribute is false.
      Returns:
      true if locally published messages are being inhibited

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the `NoLocal` attribute for this topic subscriber due to some internal error.

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

- [Prev Class](TopicSession.md)
- [Next Class](TransactionInProgressException.md)

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
