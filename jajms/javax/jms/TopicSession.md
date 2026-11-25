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

- [Prev Class](TopicRequestor.md)
- [Next Class](TopicSubscriber.md)

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

## Interface TopicSession

- All Superinterfaces:
  java.lang.Runnable, [Session](Session.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsSession](../../oracle/jms/AQjmsSession.md), [AQjmsXASession](../../oracle/jms/AQjmsXASession.md)

  ------------------------------------------------------------------------



      public interface TopicSession
      extends Session

  A `TopicSession` object provides methods for creating `TopicPublisher`, `TopicSubscriber`, and `TemporaryTopic` objects. It also provides a method for deleting its client's durable subscribers.
  A `TopicSession` is used for creating Pub/Sub specific objects. In general, use the `Session` object, and use `TopicSession` only to support existing code. Using the `Session` object simplifies the programming model, and allows transactions to be used across the two messaging domains.

  A `TopicSession` cannot be used to create objects specific to the point-to-point domain. The following methods inherit from `Session`, but must throw an `IllegalStateException` if used from `TopicSession`:

  - `createBrowser`
  - `createQueue`
  - `createTemporaryQueue`

  See Also:
  [`Session`](Session.md), [`Connection.createSession(boolean, int)`](Connection.md), [`TopicConnection.createTopicSession(boolean, int)`](TopicConnection.md), [`XATopicSession.getTopicSession()`](XATopicSession.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface javax.jms.[Session](Session.md)

      [`AUTO_ACKNOWLEDGE`](Session.md)`, `[`CLIENT_ACKNOWLEDGE`](Session.md)`, `[`DUPS_OK_ACKNOWLEDGE`](Session.md)`, `[`SESSION_TRANSACTED`](Session.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                       | Method and Description                                                                                                                                                                                                                                                                                        |
    |-----------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`TopicSubscriber`](TopicSubscriber.md) | `createDurableSubscriber``(`[`Topic`](Topic.md)` topic, java.lang.String name)`<br>Creates a durable subscriber to the specified topic.                                                                                                                                                                       |
    | [`TopicSubscriber`](TopicSubscriber.md) | `createDurableSubscriber``(`[`Topic`](Topic.md)` topic, java.lang.String name, java.lang.String messageSelector, boolean noLocal)`<br>Creates a durable subscriber to the specified topic, using a message selector or specifying whether messages published by its own connection should be delivered to it. |
    | [`TopicPublisher`](TopicPublisher.md)   | `createPublisher``(`[`Topic`](Topic.md)` topic)`<br>Creates a publisher for the specified topic.                                                                                                                                                                                                              |
    | [`TopicSubscriber`](TopicSubscriber.md) | `createSubscriber``(`[`Topic`](Topic.md)` topic)`<br>Creates a nondurable subscriber to the specified topic.                                                                                                                                                                                                  |
    | [`TopicSubscriber`](TopicSubscriber.md) | `createSubscriber``(`[`Topic`](Topic.md)` topic, java.lang.String messageSelector, boolean noLocal)`<br>Creates a nondurable subscriber to the specified topic, using a message selector or specifying whether messages published by its own connection should be delivered to it.                            |
    | [`TemporaryTopic`](TemporaryTopic.md)   | `createTemporaryTopic``()`<br>Creates a `TemporaryTopic` object.                                                                                                                                                                                                                                              |
    | [`Topic`](Topic.md)                     | `createTopic``(java.lang.String topicName)`<br>Creates a topic identity given a `Topic` name.                                                                                                                                                                                                                 |
    | `void`                                  | `unsubscribe``(java.lang.String name)`<br>Unsubscribes a durable subscription that has been created by a client.                                                                                                                                                                                              |

    - ### Methods inherited from interface javax.jms.[Session](Session.md)

      [`close`](Session.md)`, `[`commit`](Session.md)`, `[`createBrowser`](Session.md)`, `[`createBrowser`](Session.md)`, `[`createBytesMessage`](Session.md)`, `[`createConsumer`](Session.md)`, `[`createConsumer`](Session.md)`, `[`createConsumer`](Session.md)`, `[`createMapMessage`](Session.md)`, `[`createMessage`](Session.md)`, `[`createObjectMessage`](Session.md)`, `[`createObjectMessage`](Session.md)`, `[`createProducer`](Session.md)`, `[`createQueue`](Session.md)`, `[`createStreamMessage`](Session.md)`, `[`createTemporaryQueue`](Session.md)`, `[`createTextMessage`](Session.md)`, `[`createTextMessage`](Session.md)`, `[`getAcknowledgeMode`](Session.md)`, `[`getMessageListener`](Session.md)`, `[`getTransacted`](Session.md)`, `[`recover`](Session.md)`, `[`rollback`](Session.md)`, `[`run`](Session.md)`, `[`setMessageListener`](Session.md)

<!-- -->

- - ### Method Detail

    - #### createTopic

          Topic createTopic(java.lang.String topicName)
                     throws JMSException

      Creates a topic identity given a `Topic` name.
      This facility is provided for the rare cases where clients need to dynamically manipulate topic identity. This allows the creation of a topic identity with a provider-specific name. Clients that depend on this ability are not portable.

      Note that this method is not for creating the physical topic. The physical creation of topics is an administrative task and is not to be initiated by the JMS API. The one exception is the creation of temporary topics, which is accomplished with the `createTemporaryTopic` method.

      Specified by:
      [`createTopic`](Session.md) in interface [`Session`](Session.md)

      Parameters:
      `topicName` - the name of this `Topic`

      Returns:
      a `Topic` with the given name

      Throws:
      [`JMSException`](JMSException.md) - if the session fails to create a topic due to some internal error.

    <!-- -->

    - #### createSubscriber

          TopicSubscriber createSubscriber(Topic topic)
                                    throws JMSException

      Creates a nondurable subscriber to the specified topic.
      A client uses a `TopicSubscriber` object to receive messages that have been published to a topic.

      Regular `TopicSubscriber` objects are not durable. They receive only messages that are published while they are active.

      In some cases, a connection may both publish and subscribe to a topic. The subscriber `NoLocal` attribute allows a subscriber to inhibit the delivery of messages published by its own connection. The default value for this attribute is false.

      Parameters:
      `topic` - the `Topic` to subscribe to

      Throws:
      [`JMSException`](JMSException.md) - if the session fails to create a subscriber due to some internal error.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if an invalid topic is specified.

    <!-- -->

    - #### createSubscriber

          TopicSubscriber createSubscriber(Topic topic,
                                           java.lang.String messageSelector,
                                           boolean noLocal)
                                    throws JMSException

      Creates a nondurable subscriber to the specified topic, using a message selector or specifying whether messages published by its own connection should be delivered to it.
      A client uses a `TopicSubscriber` object to receive messages that have been published to a topic.

      Regular `TopicSubscriber` objects are not durable. They receive only messages that are published while they are active.

      Messages filtered out by a subscriber's message selector will never be delivered to the subscriber. From the subscriber's perspective, they do not exist.

      In some cases, a connection may both publish and subscribe to a topic. The subscriber `NoLocal` attribute allows a subscriber to inhibit the delivery of messages published by its own connection. The default value for this attribute is false.

      Parameters:
      `topic` - the `Topic` to subscribe to

      `messageSelector` - only messages with properties matching the message selector expression are delivered. A value of null or an empty string indicates that there is no message selector for the message consumer.

      `noLocal` - if set, inhibits the delivery of messages published by its own connection

      Throws:
      [`JMSException`](JMSException.md) - if the session fails to create a subscriber due to some internal error.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if an invalid topic is specified.

      [`InvalidSelectorException`](InvalidSelectorException.md) - if the message selector is invalid.

    <!-- -->

    - #### createDurableSubscriber

          TopicSubscriber createDurableSubscriber(Topic topic,
                                                  java.lang.String name)
                                           throws JMSException

      Creates a durable subscriber to the specified topic.
      If a client needs to receive all the messages published on a topic, including the ones published while the subscriber is inactive, it uses a durable `TopicSubscriber`. The JMS provider retains a record of this durable subscription and insures that all messages from the topic's publishers are retained until they are acknowledged by this durable subscriber or they have expired.

      Sessions with durable subscribers must always provide the same client identifier. In addition, each client must specify a name that uniquely identifies (within client identifier) each durable subscription it creates. Only one session at a time can have a `TopicSubscriber` for a particular durable subscription.

      A client can change an existing durable subscription by creating a durable `TopicSubscriber` with the same name and a new topic and/or message selector. Changing a durable subscriber is equivalent to unsubscribing (deleting) the old one and creating a new one.

      In some cases, a connection may both publish and subscribe to a topic. The subscriber `NoLocal` attribute allows a subscriber to inhibit the delivery of messages published by its own connection. The default value for this attribute is false.

      Specified by:
      [`createDurableSubscriber`](Session.md) in interface [`Session`](Session.md)

      Parameters:
      `topic` - the non-temporary `Topic` to subscribe to

      `name` - the name used to identify this subscription

      Throws:
      [`JMSException`](JMSException.md) - if the session fails to create a subscriber due to some internal error.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if an invalid topic is specified.

    <!-- -->

    - #### createDurableSubscriber

          TopicSubscriber createDurableSubscriber(Topic topic,
                                                  java.lang.String name,
                                                  java.lang.String messageSelector,
                                                  boolean noLocal)
                                           throws JMSException

      Creates a durable subscriber to the specified topic, using a message selector or specifying whether messages published by its own connection should be delivered to it.
      If a client needs to receive all the messages published on a topic, including the ones published while the subscriber is inactive, it uses a durable `TopicSubscriber`. The JMS provider retains a record of this durable subscription and insures that all messages from the topic's publishers are retained until they are acknowledged by this durable subscriber or they have expired.

      Sessions with durable subscribers must always provide the same client identifier. In addition, each client must specify a name which uniquely identifies (within client identifier) each durable subscription it creates. Only one session at a time can have a `TopicSubscriber` for a particular durable subscription. An inactive durable subscriber is one that exists but does not currently have a message consumer associated with it.

      A client can change an existing durable subscription by creating a durable `TopicSubscriber` with the same name and a new topic and/or message selector. Changing a durable subscriber is equivalent to unsubscribing (deleting) the old one and creating a new one.

      Specified by:
      [`createDurableSubscriber`](Session.md) in interface [`Session`](Session.md)

      Parameters:
      `topic` - the non-temporary `Topic` to subscribe to

      `name` - the name used to identify this subscription

      `messageSelector` - only messages with properties matching the message selector expression are delivered. A value of null or an empty string indicates that there is no message selector for the message consumer.

      `noLocal` - if set, inhibits the delivery of messages published by its own connection

      Throws:
      [`JMSException`](JMSException.md) - if the session fails to create a subscriber due to some internal error.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if an invalid topic is specified.

      [`InvalidSelectorException`](InvalidSelectorException.md) - if the message selector is invalid.

    <!-- -->

    - #### createPublisher

          TopicPublisher createPublisher(Topic topic)
                                  throws JMSException

      Creates a publisher for the specified topic.
      A client uses a `TopicPublisher` object to publish messages on a topic. Each time a client creates a `TopicPublisher` on a topic, it defines a new sequence of messages that have no ordering relationship with the messages it has previously sent.

      Parameters:
      `topic` - the `Topic` to publish to, or null if this is an unidentified producer

      Throws:
      [`JMSException`](JMSException.md) - if the session fails to create a publisher due to some internal error.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if an invalid topic is specified.

    <!-- -->

    - #### createTemporaryTopic

          TemporaryTopic createTemporaryTopic()
                                       throws JMSException

      Creates a `TemporaryTopic` object. Its lifetime will be that of the `TopicConnection` unless it is deleted earlier.
      Specified by:
      [`createTemporaryTopic`](Session.md) in interface [`Session`](Session.md)

      Returns:
      a temporary topic identity

      Throws:
      [`JMSException`](JMSException.md) - if the session fails to create a temporary topic due to some internal error.

    <!-- -->

    - #### unsubscribe

          void unsubscribe(java.lang.String name)
                    throws JMSException

      Unsubscribes a durable subscription that has been created by a client.
      This method deletes the state being maintained on behalf of the subscriber by its provider.

      It is erroneous for a client to delete a durable subscription while there is an active `TopicSubscriber` for the subscription, or while a consumed message is part of a pending transaction or has not been acknowledged in the session.

      Specified by:
      [`unsubscribe`](Session.md) in interface [`Session`](Session.md)

      Parameters:
      `name` - the name used to identify this subscription

      Throws:
      [`JMSException`](JMSException.md) - if the session fails to unsubscribe to the durable subscription due to some internal error.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if an invalid subscription name is specified.

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

- [Prev Class](TopicRequestor.md)
- [Next Class](TopicSubscriber.md)

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
