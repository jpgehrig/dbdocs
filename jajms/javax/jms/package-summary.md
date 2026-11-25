Skip navigation links

- [Overview](../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database Advanced Queuing Java API Reference
19c**
E96513-01

- Prev Package
- [Next Package](../../oracle/jms/package-summary.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

# Package javax.jms

- **Interface Summary**

  | Interface                                               | Description                                                                                                                                                                                   |
  |---------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [BytesMessage](BytesMessage.md)                         | A `BytesMessage` object is used to send a message containing a stream of uninterpreted bytes.                                                                                                 |
  | [Connection](Connection.md)                             | A `Connection` object is a client's active connection to its JMS provider.                                                                                                                    |
  | [ConnectionConsumer](ConnectionConsumer.md)             | For application servers, `Connection` objects provide a special facility for creating a `ConnectionConsumer` (optional).                                                                      |
  | [ConnectionFactory](ConnectionFactory.md)               | A `ConnectionFactory` object encapsulates a set of connection configuration parameters that has been defined by an administrator.                                                             |
  | [ConnectionMetaData](ConnectionMetaData.md)             | A `ConnectionMetaData` object provides information describing the `Connection` object.                                                                                                        |
  | [DeliveryMode](DeliveryMode.md)                         | The delivery modes supported by the JMS API are `PERSISTENT` and `NON_PERSISTENT`.                                                                                                            |
  | [Destination](Destination.md)                           | A `Destination` object encapsulates a provider-specific address.                                                                                                                              |
  | [ExceptionListener](ExceptionListener.md)               | If a JMS provider detects a serious problem with a `Connection` object, it informs the `Connection` object's `ExceptionListener`, if one has been registered.                                 |
  | [MapMessage](MapMessage.md)                             | A `MapMessage` object is used to send a set of name-value pairs.                                                                                                                              |
  | [Message](Message.md)                                   | The `Message` interface is the root interface of all JMS messages.                                                                                                                            |
  | [MessageConsumer](MessageConsumer.md)                   | A client uses a `MessageConsumer` object to receive messages from a destination.                                                                                                              |
  | [MessageListener](MessageListener.md)                   | A `MessageListener` object is used to receive asynchronously delivered messages.                                                                                                              |
  | [MessageProducer](MessageProducer.md)                   | A client uses a `MessageProducer` object to send messages to a destination.                                                                                                                   |
  | [ObjectMessage](ObjectMessage.md)                       | An `ObjectMessage` object is used to send a message that contains a serializable object in the Java programming language ("Java object").                                                     |
  | [Queue](Queue.md)                                       | A `Queue` object encapsulates a provider-specific queue name.                                                                                                                                 |
  | [QueueBrowser](QueueBrowser.md)                         | A client uses a `QueueBrowser` object to look at messages on a queue without removing them.                                                                                                   |
  | [QueueConnection](QueueConnection.md)                   | A `QueueConnection` object is an active connection to a point-to-point JMS provider.                                                                                                          |
  | [QueueConnectionFactory](QueueConnectionFactory.md)     | A client uses a `QueueConnectionFactory` object to create `QueueConnection` objects with a point-to-point JMS provider.                                                                       |
  | [QueueReceiver](QueueReceiver.md)                       | A client uses a `QueueReceiver` object to receive messages that have been delivered to a queue.                                                                                               |
  | [QueueSender](QueueSender.md)                           | A client uses a `QueueSender` object to send messages to a queue.                                                                                                                             |
  | [QueueSession](QueueSession.md)                         | A `QueueSession` object provides methods for creating `QueueReceiver`, `QueueSender`, `QueueBrowser`, and `TemporaryQueue` objects.                                                           |
  | [ServerSession](ServerSession.md)                       | A `ServerSession` object is an application server object that is used by a server to associate a thread with a JMS session (optional).                                                        |
  | [ServerSessionPool](ServerSessionPool.md)               | A `ServerSessionPool` object is an object implemented by an application server to provide a pool of `ServerSession` objects for processing the messages of a `ConnectionConsumer` (optional). |
  | [Session](Session.md)                                   | A `Session` object is a single-threaded context for producing and consuming messages.                                                                                                         |
  | [StreamMessage](StreamMessage.md)                       | A `StreamMessage` object is used to send a stream of primitive types in the Java programming language.                                                                                        |
  | [TemporaryQueue](TemporaryQueue.md)                     | A `TemporaryQueue` object is a unique `Queue` object created for the duration of a `Connection`.                                                                                              |
  | [TemporaryTopic](TemporaryTopic.md)                     | A `TemporaryTopic` object is a unique `Topic` object created for the duration of a `Connection`.                                                                                              |
  | [TextMessage](TextMessage.md)                           | A `TextMessage` object is used to send a message containing a `java.lang.String`.                                                                                                             |
  | [Topic](Topic.md)                                       | A `Topic` object encapsulates a provider-specific topic name.                                                                                                                                 |
  | [TopicConnection](TopicConnection.md)                   | A `TopicConnection` object is an active connection to a publish/subscribe JMS provider.                                                                                                       |
  | [TopicConnectionFactory](TopicConnectionFactory.md)     | A client uses a `TopicConnectionFactory` object to create `TopicConnection` objects with a publish/subscribe JMS provider.                                                                    |
  | [TopicPublisher](TopicPublisher.md)                     | A client uses a `TopicPublisher` object to publish messages on a topic.                                                                                                                       |
  | [TopicSession](TopicSession.md)                         | A `TopicSession` object provides methods for creating `TopicPublisher`, `TopicSubscriber`, and `TemporaryTopic` objects.                                                                      |
  | [TopicSubscriber](TopicSubscriber.md)                   | A client uses a `TopicSubscriber` object to receive messages that have been published to a topic.                                                                                             |
  | [XAConnection](XAConnection.md)                         | The `XAConnection` interface extends the capability of `Connection` by providing an `XASession` (optional).                                                                                   |
  | [XAConnectionFactory](XAConnectionFactory.md)           | The `XAConnectionFactory` interface is a base interface for the `XAQueueConnectionFactory` and `XATopicConnectionFactory` interfaces.                                                         |
  | [XAQueueConnection](XAQueueConnection.md)               | An `XAQueueConnection` provides the same create options as `QueueConnection` (optional).                                                                                                      |
  | [XAQueueConnectionFactory](XAQueueConnectionFactory.md) | An `XAQueueConnectionFactory` provides the same create options as a `QueueConnectionFactory` (optional).                                                                                      |
  | [XAQueueSession](XAQueueSession.md)                     | An `XAQueueSession` provides a regular `QueueSession`, which can be used to create `QueueReceiver`, `QueueSender`, and `QueueBrowser` objects (optional).                                     |
  | [XASession](XASession.md)                               | The `XASession` interface extends the capability of `Session` by adding access to a JMS provider's support for the Java Transaction API (JTA) (optional).                                     |
  | [XATopicConnection](XATopicConnection.md)               | An `XATopicConnection` provides the same create options as `TopicConnection` (optional).                                                                                                      |
  | [XATopicConnectionFactory](XATopicConnectionFactory.md) | An `XATopicConnectionFactory` provides the same create options as a `TopicConnectionFactory` (optional).                                                                                      |
  | [XATopicSession](XATopicSession.md)                     | An `XATopicSession` provides a regular `TopicSession`.                                                                                                                                        |

- **Class Summary**

  | Class                               | Description                                                           |
  |-------------------------------------|-----------------------------------------------------------------------|
  | [QueueRequestor](QueueRequestor.md) | The `QueueRequestor` helper class simplifies making service requests. |
  | [TopicRequestor](TopicRequestor.md) | The `TopicRequestor` helper class simplifies making service requests. |

- **Exception Summary**

  | Exception                                                           | Description                                                                                                                                                          |
  |---------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
  | [IllegalStateException](IllegalStateException.md)                   | This exception is thrown when a method is invoked at an illegal or inappropriate time or if the provider is not in an appropriate state for the requested operation. |
  | [InvalidClientIDException](InvalidClientIDException.md)             | This exception must be thrown when a client attempts to set a connection's client ID to a value that is rejected by a provider.                                      |
  | [InvalidDestinationException](InvalidDestinationException.md)       | This exception must be thrown when a destination either is not understood by a provider or is no longer valid.                                                       |
  | [InvalidSelectorException](InvalidSelectorException.md)             | This exception must be thrown when a JMS client attempts to give a provider a message selector with invalid syntax.                                                  |
  | [JMSException](JMSException.md)                                     | This is the root class of all JMS API exceptions.                                                                                                                    |
  | [JMSSecurityException](JMSSecurityException.md)                     | This exception must be thrown when a provider rejects a user name/password submitted by a client.                                                                    |
  | [MessageEOFException](MessageEOFException.md)                       | This exception must be thrown when an unexpected end of stream has been reached when a `StreamMessage` or `BytesMessage` is being read.                              |
  | [MessageFormatException](MessageFormatException.md)                 | This exception must be thrown when a JMS client attempts to use a data type not supported by a message or attempts to read data in a message as the wrong type.      |
  | [MessageNotReadableException](MessageNotReadableException.md)       | This exception must be thrown when a JMS client attempts to read a write-only message.                                                                               |
  | [MessageNotWriteableException](MessageNotWriteableException.md)     | This exception must be thrown when a JMS client attempts to write to a read-only message.                                                                            |
  | [ResourceAllocationException](ResourceAllocationException.md)       | This exception is thrown when a provider is unable to allocate the resources required by a method.                                                                   |
  | [TransactionInProgressException](TransactionInProgressException.md) | This exception is thrown when an operation is invalid because a transaction is in progress.                                                                          |
  | [TransactionRolledBackException](TransactionRolledBackException.md) | This exception must be thrown when a call to `Session.commit` results in a rollback of the current transaction.                                                      |

Skip navigation links

- [Overview](../../overview-summary.md)
- Package
- Class
- [Tree](package-tree.md)
- [Deprecated](../../deprecated-list.md)
- [Index](../../index-all.md)
- [Help](../../help-doc.md)

**Oracle® Database Advanced Queuing Java API Reference
19c**
E96513-01

- Prev Package
- [Next Package](../../oracle/jms/package-summary.md)

<!-- -->

- [Frames](../../index.md)
- No Frames

<!-- -->

- [All Classes](../../allclasses-noframe.md)

Copyright © 2001, 2019, Oracle and/or its affiliates. All rights reserved.
