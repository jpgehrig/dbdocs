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

- [Prev Class](ServerSessionPool.md)
- [Next Class](StreamMessage.md)

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

## Interface Session

- All Superinterfaces:
  java.lang.Runnable

  <!-- -->

  All Known Subinterfaces:
  [QueueSession](QueueSession.md), [TopicSession](TopicSession.md), [XAQueueSession](XAQueueSession.md), [XASession](XASession.md), [XATopicSession](XATopicSession.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsSession](../../oracle/jms/AQjmsSession.md), [AQjmsXASession](../../oracle/jms/AQjmsXASession.md)

  ------------------------------------------------------------------------



      public interface Session
      extends java.lang.Runnable

  A `Session` object is a single-threaded context for producing and consuming messages. Although it may allocate provider resources outside the Java virtual machine (JVM), it is considered a lightweight JMS object.

  A session serves several purposes:

  - It is a factory for its message producers and consumers.
  - It supplies provider-optimized message factories.
  - It is a factory for `TemporaryTopics` and `TemporaryQueues`.
  - It provides a way to create `Queue` or `Topic` objects for those clients that need to dynamically manipulate provider-specific destination names.
  - It supports a single series of transactions that combine work spanning its producers and consumers into atomic units.
  - It defines a serial order for the messages it consumes and the messages it produces.
  - It retains messages it consumes until they have been acknowledged.
  - It serializes execution of message listeners registered with its message consumers.
  - It is a factory for `QueueBrowsers`.

  A session can create and service multiple message producers and consumers.

  One typical use is to have a thread block on a synchronous `MessageConsumer` until a message arrives. The thread may then use one or more of the `Session`'s `MessageProducer`s.

  If a client desires to have one thread produce messages while others consume them, the client should use a separate session for its producing thread.

  Once a connection has been started, any session with one or more registered message listeners is dedicated to the thread of control that delivers messages to it. It is erroneous for client code to use this session or any of its constituent objects from another thread of control. The only exception to this rule is the use of the session or connection `close` method.

  It should be easy for most clients to partition their work naturally into sessions. This model allows clients to start simply and incrementally add message processing complexity as their need for concurrency grows.

  The `close` method is the only session method that can be called while some other session method is being executed in another thread.

  A session may be specified as transacted. Each transacted session supports a single series of transactions. Each transaction groups a set of message sends and a set of message receives into an atomic unit of work. In effect, transactions organize a session's input message stream and output message stream into series of atomic units. When a transaction commits, its atomic unit of input is acknowledged and its associated atomic unit of output is sent. If a transaction rollback is done, the transaction's sent messages are destroyed and the session's input is automatically recovered.

  The content of a transaction's input and output units is simply those messages that have been produced and consumed within the session's current transaction.

  A transaction is completed using either its session's `commit` method or its session's `rollback` method. The completion of a session's current transaction automatically begins the next. The result is that a transacted session always has a current transaction within which its work is done.

  The Java Transaction Service (JTS) or some other transaction monitor may be used to combine a session's transaction with transactions on other resources (databases, other JMS sessions, etc.). Since Java distributed transactions are controlled via the Java Transaction API (JTA), use of the session's `commit` and `rollback` methods in this context is prohibited.

  The JMS API does not require support for JTA; however, it does define how a provider supplies this support.

  Although it is also possible for a JMS client to handle distributed transactions directly, it is unlikely that many JMS clients will do this. Support for JTA in the JMS API is targeted at systems vendors who will be integrating the JMS API into their application server products.

  See Also:
  [`QueueSession`](QueueSession.md), [`TopicSession`](TopicSession.md), [`XASession`](XASession.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type | Field and Description                                                                                                                                                                                                                                                                                   |
    |-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static int`      | `AUTO_ACKNOWLEDGE`<br>With this acknowledgment mode, the session automatically acknowledges a client's receipt of a message either when the session has successfully returned from a call to `receive` or when the message listener the session has called to process the message successfully returns. |
    | `static int`      | `CLIENT_ACKNOWLEDGE`<br>With this acknowledgment mode, the client acknowledges a consumed message by calling the message's `acknowledge` method.                                                                                                                                                        |
    | `static int`      | `DUPS_OK_ACKNOWLEDGE`<br>This acknowledgment mode instructs the session to lazily acknowledge the delivery of messages.                                                                                                                                                                                 |
    | `static int`      | `SESSION_TRANSACTED`<br>This value is returned from the method `getAcknowledgeMode` if the session is transacted.                                                                                                                                                                                       |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                       | Method and Description                                                                                                                                                                                                                                                                                         |
    |-----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                  | `close``()`<br>Closes the session.                                                                                                                                                                                                                                                                             |
    | `void`                                  | `commit``()`<br>Commits all messages done in this transaction and releases any locks currently held.                                                                                                                                                                                                           |
    | [`QueueBrowser`](QueueBrowser.md)       | `createBrowser``(`[`Queue`](Queue.md)` queue)`<br>Creates a `QueueBrowser` object to peek at the messages on the specified queue.                                                                                                                                                                              |
    | [`QueueBrowser`](QueueBrowser.md)       | `createBrowser``(`[`Queue`](Queue.md)` queue, java.lang.String messageSelector)`<br>Creates a `QueueBrowser` object to peek at the messages on the specified queue using a message selector.                                                                                                                   |
    | [`BytesMessage`](BytesMessage.md)       | `createBytesMessage``()`<br>Creates a `BytesMessage` object.                                                                                                                                                                                                                                                   |
    | [`MessageConsumer`](MessageConsumer.md) | `createConsumer``(`[`Destination`](Destination.md)` destination)`<br>Creates a `MessageConsumer` for the specified destination.                                                                                                                                                                                |
    | [`MessageConsumer`](MessageConsumer.md) | `createConsumer``(`[`Destination`](Destination.md)` destination, java.lang.String messageSelector)`<br>Creates a `MessageConsumer` for the specified destination, using a message selector.                                                                                                                    |
    | [`MessageConsumer`](MessageConsumer.md) | `createConsumer``(`[`Destination`](Destination.md)` destination, java.lang.String messageSelector, boolean NoLocal)`<br>Creates `MessageConsumer` for the specified destination, using a message selector.                                                                                                     |
    | [`TopicSubscriber`](TopicSubscriber.md) | `createDurableSubscriber``(`[`Topic`](Topic.md)` topic, java.lang.String name)`<br>Creates a durable subscriber to the specified topic.                                                                                                                                                                        |
    | [`TopicSubscriber`](TopicSubscriber.md) | `createDurableSubscriber``(`[`Topic`](Topic.md)` topic, java.lang.String name, java.lang.String messageSelector, boolean noLocal)`<br>Creates a durable subscriber to the specified topic, using a message selector and specifying whether messages published by its own connection should be delivered to it. |
    | [`MapMessage`](MapMessage.md)           | `createMapMessage``()`<br>Creates a `MapMessage` object.                                                                                                                                                                                                                                                       |
    | [`Message`](Message.md)                 | `createMessage``()`<br>Creates a `Message` object.                                                                                                                                                                                                                                                             |
    | [`ObjectMessage`](ObjectMessage.md)     | `createObjectMessage``()`<br>Creates an `ObjectMessage` object.                                                                                                                                                                                                                                                |
    | [`ObjectMessage`](ObjectMessage.md)     | `createObjectMessage``(java.io.Serializable object)`<br>Creates an initialized `ObjectMessage` object.                                                                                                                                                                                                         |
    | [`MessageProducer`](MessageProducer.md) | `createProducer``(`[`Destination`](Destination.md)` destination)`<br>Creates a `MessageProducer` to send messages to the specified destination.                                                                                                                                                                |
    | [`Queue`](Queue.md)                     | `createQueue``(java.lang.String queueName)`<br>Creates a queue identity given a `Queue` name.                                                                                                                                                                                                                  |
    | [`StreamMessage`](StreamMessage.md)     | `createStreamMessage``()`<br>Creates a `StreamMessage` object.                                                                                                                                                                                                                                                 |
    | [`TemporaryQueue`](TemporaryQueue.md)   | `createTemporaryQueue``()`<br>Creates a `TemporaryQueue` object.                                                                                                                                                                                                                                               |
    | [`TemporaryTopic`](TemporaryTopic.md)   | `createTemporaryTopic``()`<br>Creates a `TemporaryTopic` object.                                                                                                                                                                                                                                               |
    | [`TextMessage`](TextMessage.md)         | `createTextMessage``()`<br>Creates a `TextMessage` object.                                                                                                                                                                                                                                                     |
    | [`TextMessage`](TextMessage.md)         | `createTextMessage``(java.lang.String text)`<br>Creates an initialized `TextMessage` object.                                                                                                                                                                                                                   |
    | [`Topic`](Topic.md)                     | `createTopic``(java.lang.String topicName)`<br>Creates a topic identity given a `Topic` name.                                                                                                                                                                                                                  |
    | `int`                                   | `getAcknowledgeMode``()`<br>Returns the acknowledgement mode of the session.                                                                                                                                                                                                                                   |
    | [`MessageListener`](MessageListener.md) | `getMessageListener``()`<br>Returns the session's distinguished message listener (optional).                                                                                                                                                                                                                   |
    | `boolean`                               | `getTransacted``()`<br>Indicates whether the session is in transacted mode.                                                                                                                                                                                                                                    |
    | `void`                                  | `recover``()`<br>Stops message delivery in this session, and restarts message delivery with the oldest unacknowledged message.                                                                                                                                                                                 |
    | `void`                                  | `rollback``()`<br>Rolls back any messages done in this transaction and releases any locks currently held.                                                                                                                                                                                                      |
    | `void`                                  | `run``()`<br>Optional operation, intended to be used only by Application Servers, not by ordinary JMS clients.                                                                                                                                                                                                 |
    | `void`                                  | `setMessageListener``(`[`MessageListener`](MessageListener.md)` listener)`<br>Sets the session's distinguished message listener (optional).                                                                                                                                                                    |
    | `void`                                  | `unsubscribe``(java.lang.String name)`<br>Unsubscribes a durable subscription that has been created by a client.                                                                                                                                                                                               |

<!-- -->

- - ### Field Detail

    - #### AUTO_ACKNOWLEDGE

          static final int AUTO_ACKNOWLEDGE

      With this acknowledgment mode, the session automatically acknowledges a client's receipt of a message either when the session has successfully returned from a call to `receive` or when the message listener the session has called to process the message successfully returns.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### CLIENT_ACKNOWLEDGE

          static final int CLIENT_ACKNOWLEDGE

      With this acknowledgment mode, the client acknowledges a consumed message by calling the message's `acknowledge` method. Acknowledging a consumed message acknowledges all messages that the session has consumed.
      When client acknowledgment mode is used, a client may build up a large number of unacknowledged messages while attempting to process them. A JMS provider should provide administrators with a way to limit client overrun so that clients are not driven to resource exhaustion and ensuing failure when some resource they are using is temporarily blocked.

      See Also:
      [`Message.acknowledge()`](Message.md), [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### DUPS_OK_ACKNOWLEDGE

          static final int DUPS_OK_ACKNOWLEDGE

      This acknowledgment mode instructs the session to lazily acknowledge the delivery of messages. This is likely to result in the delivery of some duplicate messages if the JMS provider fails, so it should only be used by consumers that can tolerate duplicate messages. Use of this mode can reduce session overhead by minimizing the work the session does to prevent duplicates.
      See Also:
      [Constant Field Values](../../constant-values.md)

    <!-- -->

    - #### SESSION_TRANSACTED

          static final int SESSION_TRANSACTED

      This value is returned from the method `getAcknowledgeMode` if the session is transacted. If a `Session` is transacted, the acknowledgement mode is ignored.
      See Also:
      [Constant Field Values](../../constant-values.md)

  <!-- -->

  - ### Method Detail

    - #### createBytesMessage

          BytesMessage createBytesMessage()
                                   throws JMSException

      Creates a `BytesMessage` object. A `BytesMessage` object is used to send a message containing a stream of uninterpreted bytes.
      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to create this message due to some internal error.

    <!-- -->

    - #### createMapMessage

          MapMessage createMapMessage()
                               throws JMSException

      Creates a `MapMessage` object. A `MapMessage` object is used to send a self-defining set of name-value pairs, where names are `String` objects and values are primitive values in the Java programming language.
      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to create this message due to some internal error.

    <!-- -->

    - #### createMessage

          Message createMessage()
                         throws JMSException

      Creates a `Message` object. The `Message` interface is the root interface of all JMS messages. A `Message` object holds all the standard message header information. It can be sent when a message containing only header information is sufficient.
      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to create this message due to some internal error.

    <!-- -->

    - #### createObjectMessage

          ObjectMessage createObjectMessage()
                                     throws JMSException

      Creates an `ObjectMessage` object. An `ObjectMessage` object is used to send a message that contains a serializable Java object.
      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to create this message due to some internal error.

    <!-- -->

    - #### createObjectMessage

          ObjectMessage createObjectMessage(java.io.Serializable object)
                                     throws JMSException

      Creates an initialized `ObjectMessage` object. An `ObjectMessage` object is used to send a message that contains a serializable Java object.
      Parameters:
      `object` - the object to use to initialize this message

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to create this message due to some internal error.

    <!-- -->

    - #### createStreamMessage

          StreamMessage createStreamMessage()
                                     throws JMSException

      Creates a `StreamMessage` object. A `StreamMessage` object is used to send a self-defining stream of primitive values in the Java programming language.
      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to create this message due to some internal error.

    <!-- -->

    - #### createTextMessage

          TextMessage createTextMessage()
                                 throws JMSException

      Creates a `TextMessage` object. A `TextMessage` object is used to send a message containing a `String` object.
      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to create this message due to some internal error.

    <!-- -->

    - #### createTextMessage

          TextMessage createTextMessage(java.lang.String text)
                                 throws JMSException

      Creates an initialized `TextMessage` object. A `TextMessage` object is used to send a message containing a `String`.
      Parameters:
      `text` - the string used to initialize this message

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to create this message due to some internal error.

    <!-- -->

    - #### getTransacted

          boolean getTransacted()
                         throws JMSException

      Indicates whether the session is in transacted mode.
      Returns:
      true if the session is in transacted mode

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to return the transaction mode due to some internal error.

    <!-- -->

    - #### getAcknowledgeMode

          int getAcknowledgeMode()
                          throws JMSException

      Returns the acknowledgement mode of the session. The acknowledgement mode is set at the time that the session is created. If the session is transacted, the acknowledgement mode is ignored.
      Returns:
      If the session is not transacted, returns the current acknowledgement mode for the session. If the session is transacted, returns SESSION_TRANSACTED.

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to return the acknowledgment mode due to some internal error.

      Since:
      1.1

      See Also:
      [`Connection.createSession(boolean, int)`](Connection.md)

    <!-- -->

    - #### commit

          void commit()
               throws JMSException

      Commits all messages done in this transaction and releases any locks currently held.
      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to commit the transaction due to some internal error.

      [`TransactionRolledBackException`](TransactionRolledBackException.md) - if the transaction is rolled back due to some internal error during commit.

      [`IllegalStateException`](IllegalStateException.md) - if the method is not called by a transacted session.

    <!-- -->

    - #### rollback

          void rollback()
                 throws JMSException

      Rolls back any messages done in this transaction and releases any locks currently held.
      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to roll back the transaction due to some internal error.

      [`IllegalStateException`](IllegalStateException.md) - if the method is not called by a transacted session.

    <!-- -->

    - #### close

          void close()
              throws JMSException

      Closes the session.
      Since a provider may allocate some resources on behalf of a session outside the JVM, clients should close the resources when they are not needed. Relying on garbage collection to eventually reclaim these resources may not be timely enough.

      There is no need to close the producers and consumers of a closed session.

      This call will block until a `receive` call or message listener in progress has completed. A blocked message consumer `receive` call returns `null` when this session is closed.

      Closing a transacted session must roll back the transaction in progress.

      This method is the only `Session` method that can be called concurrently.

      Invoking any other `Session` method on a closed session must throw a `JMSException.IllegalStateException`. Closing a closed session must *not* throw an exception.

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to close the session due to some internal error.

    <!-- -->

    - #### recover

          void recover()
                throws JMSException

      Stops message delivery in this session, and restarts message delivery with the oldest unacknowledged message.
      All consumers deliver messages in a serial order. Acknowledging a received message automatically acknowledges all messages that have been delivered to the client.

      Restarting a session causes it to take the following actions:

      - Stop message delivery
      - Mark all messages that might have been delivered but not acknowledged as "redelivered"
      - Restart the delivery sequence including all unacknowledged messages that had been previously delivered. Redelivered messages do not have to be delivered in exactly their original delivery order.

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to stop and restart message delivery due to some internal error.

      [`IllegalStateException`](IllegalStateException.md) - if the method is called by a transacted session.

    <!-- -->

    - #### getMessageListener

          MessageListener getMessageListener()
                                      throws JMSException

      Returns the session's distinguished message listener (optional).
      Returns:
      the message listener associated with this session

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the message listener due to an internal error.

      See Also:
      `Session.setMessageListener(javax.jms.MessageListener)`, [`ServerSessionPool`](ServerSessionPool.md), [`ServerSession`](ServerSession.md)

    <!-- -->

    - #### setMessageListener

          void setMessageListener(MessageListener listener)
                           throws JMSException

      Sets the session's distinguished message listener (optional).
      When the distinguished message listener is set, no other form of message receipt in the session can be used; however, all forms of sending messages are still supported.

      This is an expert facility not used by regular JMS clients.

      Parameters:
      `listener` - the message listener to associate with this session

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to set the message listener due to an internal error.

      See Also:
      `Session.getMessageListener()`, [`ServerSessionPool`](ServerSessionPool.md), [`ServerSession`](ServerSession.md)

    <!-- -->

    - #### run

          void run()

      Optional operation, intended to be used only by Application Servers, not by ordinary JMS clients.
      Specified by:
      `run` in interface `java.lang.Runnable`

      See Also:
      [`ServerSession`](ServerSession.md)

    <!-- -->

    - #### createProducer

          MessageProducer createProducer(Destination destination)
                                  throws JMSException

      Creates a `MessageProducer` to send messages to the specified destination.
      A client uses a `MessageProducer` object to send messages to a destination. Since `Queue` and `Topic` both inherit from `Destination`, they can be used in the destination parameter to create a `MessageProducer` object.

      Parameters:
      `destination` - the `Destination` to send to, or null if this is a producer which does not have a specified destination.

      Throws:
      [`JMSException`](JMSException.md) - if the session fails to create a MessageProducer due to some internal error.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if an invalid destination is specified.

      Since:
      1.1

    <!-- -->

    - #### createConsumer

          MessageConsumer createConsumer(Destination destination)
                                  throws JMSException

      Creates a `MessageConsumer` for the specified destination. Since `Queue` and `Topic` both inherit from `Destination`, they can be used in the destination parameter to create a `MessageConsumer`.
      Parameters:
      `destination` - the `Destination` to access.

      Throws:
      [`JMSException`](JMSException.md) - if the session fails to create a consumer due to some internal error.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if an invalid destination is specified.

      Since:
      1.1

    <!-- -->

    - #### createConsumer

          MessageConsumer createConsumer(Destination destination,
                                         java.lang.String messageSelector)
                                  throws JMSException

      Creates a `MessageConsumer` for the specified destination, using a message selector. Since `Queue` and `Topic` both inherit from `Destination`, they can be used in the destination parameter to create a `MessageConsumer`.
      A client uses a `MessageConsumer` object to receive messages that have been sent to a destination.

      Parameters:
      `destination` - the `Destination` to access

      `messageSelector` - only messages with properties matching the message selector expression are delivered. A value of null or an empty string indicates that there is no message selector for the message consumer.

      Throws:
      [`JMSException`](JMSException.md) - if the session fails to create a MessageConsumer due to some internal error.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if an invalid destination is specified.

      [`InvalidSelectorException`](InvalidSelectorException.md) - if the message selector is invalid.

      Since:
      1.1

    <!-- -->

    - #### createConsumer

          MessageConsumer createConsumer(Destination destination,
                                         java.lang.String messageSelector,
                                         boolean NoLocal)
                                  throws JMSException

      Creates `MessageConsumer` for the specified destination, using a message selector. This method can specify whether messages published by its own connection should be delivered to it, if the destination is a topic.
      Since `Queue` and `Topic` both inherit from `Destination`, they can be used in the destination parameter to create a `MessageConsumer`.

      A client uses a `MessageConsumer` object to receive messages that have been published to a destination.

      In some cases, a connection may both publish and subscribe to a topic. The consumer `NoLocal` attribute allows a consumer to inhibit the delivery of messages published by its own connection. The default value for this attribute is False. The `noLocal` value must be supported by destinations that are topics.

      Parameters:
      `destination` - the `Destination` to access

      `messageSelector` - only messages with properties matching the message selector expression are delivered. A value of null or an empty string indicates that there is no message selector for the message consumer.

      `NoLocal` - - if true, and the destination is a topic, inhibits the delivery of messages published by its own connection. The behavior for `NoLocal` is not specified if the destination is a queue.

      Throws:
      [`JMSException`](JMSException.md) - if the session fails to create a MessageConsumer due to some internal error.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if an invalid destination is specified.

      [`InvalidSelectorException`](InvalidSelectorException.md) - if the message selector is invalid.

      Since:
      1.1

    <!-- -->

    - #### createQueue

          Queue createQueue(java.lang.String queueName)
                     throws JMSException

      Creates a queue identity given a `Queue` name.
      This facility is provided for the rare cases where clients need to dynamically manipulate queue identity. It allows the creation of a queue identity with a provider-specific name. Clients that depend on this ability are not portable.

      Note that this method is not for creating the physical queue. The physical creation of queues is an administrative task and is not to be initiated by the JMS API. The one exception is the creation of temporary queues, which is accomplished with the `createTemporaryQueue` method.

      Parameters:
      `queueName` - the name of this `Queue`

      Returns:
      a `Queue` with the given name

      Throws:
      [`JMSException`](JMSException.md) - if the session fails to create a queue due to some internal error.

      Since:
      1.1

    <!-- -->

    - #### createTopic

          Topic createTopic(java.lang.String topicName)
                     throws JMSException

      Creates a topic identity given a `Topic` name.
      This facility is provided for the rare cases where clients need to dynamically manipulate topic identity. This allows the creation of a topic identity with a provider-specific name. Clients that depend on this ability are not portable.

      Note that this method is not for creating the physical topic. The physical creation of topics is an administrative task and is not to be initiated by the JMS API. The one exception is the creation of temporary topics, which is accomplished with the `createTemporaryTopic` method.

      Parameters:
      `topicName` - the name of this `Topic`

      Returns:
      a `Topic` with the given name

      Throws:
      [`JMSException`](JMSException.md) - if the session fails to create a topic due to some internal error.

      Since:
      1.1

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

      Parameters:
      `topic` - the non-temporary `Topic` to subscribe to

      `name` - the name used to identify this subscription

      Throws:
      [`JMSException`](JMSException.md) - if the session fails to create a subscriber due to some internal error.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if an invalid topic is specified.

      Since:
      1.1

    <!-- -->

    - #### createDurableSubscriber

          TopicSubscriber createDurableSubscriber(Topic topic,
                                                  java.lang.String name,
                                                  java.lang.String messageSelector,
                                                  boolean noLocal)
                                           throws JMSException

      Creates a durable subscriber to the specified topic, using a message selector and specifying whether messages published by its own connection should be delivered to it.
      If a client needs to receive all the messages published on a topic, including the ones published while the subscriber is inactive, it uses a durable `TopicSubscriber`. The JMS provider retains a record of this durable subscription and insures that all messages from the topic's publishers are retained until they are acknowledged by this durable subscriber or they have expired.

      Sessions with durable subscribers must always provide the same client identifier. In addition, each client must specify a name which uniquely identifies (within client identifier) each durable subscription it creates. Only one session at a time can have a `TopicSubscriber` for a particular durable subscription. An inactive durable subscriber is one that exists but does not currently have a message consumer associated with it.

      A client can change an existing durable subscription by creating a durable `TopicSubscriber` with the same name and a new topic and/or message selector. Changing a durable subscriber is equivalent to unsubscribing (deleting) the old one and creating a new one.

      Parameters:
      `topic` - the non-temporary `Topic` to subscribe to

      `name` - the name used to identify this subscription

      `messageSelector` - only messages with properties matching the message selector expression are delivered. A value of null or an empty string indicates that there is no message selector for the message consumer.

      `noLocal` - if set, inhibits the delivery of messages published by its own connection

      Throws:
      [`JMSException`](JMSException.md) - if the session fails to create a subscriber due to some internal error.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if an invalid topic is specified.

      [`InvalidSelectorException`](InvalidSelectorException.md) - if the message selector is invalid.

      Since:
      1.1

    <!-- -->

    - #### createBrowser

          QueueBrowser createBrowser(Queue queue)
                              throws JMSException

      Creates a `QueueBrowser` object to peek at the messages on the specified queue.
      Parameters:
      `queue` - the `queue` to access

      Throws:
      [`JMSException`](JMSException.md) - if the session fails to create a browser due to some internal error.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if an invalid destination is specified

      Since:
      1.1

    <!-- -->

    - #### createBrowser

          QueueBrowser createBrowser(Queue queue,
                                     java.lang.String messageSelector)
                              throws JMSException

      Creates a `QueueBrowser` object to peek at the messages on the specified queue using a message selector.
      Parameters:
      `queue` - the `queue` to access

      `messageSelector` - only messages with properties matching the message selector expression are delivered. A value of null or an empty string indicates that there is no message selector for the message consumer.

      Throws:
      [`JMSException`](JMSException.md) - if the session fails to create a browser due to some internal error.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if an invalid destination is specified

      [`InvalidSelectorException`](InvalidSelectorException.md) - if the message selector is invalid.

      Since:
      1.1

    <!-- -->

    - #### createTemporaryQueue

          TemporaryQueue createTemporaryQueue()
                                       throws JMSException

      Creates a `TemporaryQueue` object. Its lifetime will be that of the `Connection` unless it is deleted earlier.
      Returns:
      a temporary queue identity

      Throws:
      [`JMSException`](JMSException.md) - if the session fails to create a temporary queue due to some internal error.

      Since:
      1.1

    <!-- -->

    - #### createTemporaryTopic

          TemporaryTopic createTemporaryTopic()
                                       throws JMSException

      Creates a `TemporaryTopic` object. Its lifetime will be that of the `Connection` unless it is deleted earlier.
      Returns:
      a temporary topic identity

      Throws:
      [`JMSException`](JMSException.md) - if the session fails to create a temporary topic due to some internal error.

      Since:
      1.1

    <!-- -->

    - #### unsubscribe

          void unsubscribe(java.lang.String name)
                    throws JMSException

      Unsubscribes a durable subscription that has been created by a client.
      This method deletes the state being maintained on behalf of the subscriber by its provider.

      It is erroneous for a client to delete a durable subscription while there is an active `MessageConsumer` or `TopicSubscriber` for the subscription, or while a consumed message is part of a pending transaction or has not been acknowledged in the session.

      Parameters:
      `name` - the name used to identify this subscription

      Throws:
      [`JMSException`](JMSException.md) - if the session fails to unsubscribe to the durable subscription due to some internal error.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if an invalid subscription name is specified.

      Since:
      1.1

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

- [Prev Class](ServerSessionPool.md)
- [Next Class](StreamMessage.md)

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
