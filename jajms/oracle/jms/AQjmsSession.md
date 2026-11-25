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

- [Prev Class](AQjmsQueueSender.md)
- [Next Class](AQjmsStreamMessage.md)

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

## Class AQjmsSession

- java.lang.Object

- - oracle.jms.AQjmsObject

  - - oracle.jms.AQjmsSession

<!-- -->

- All Implemented Interfaces:
  java.lang.Runnable, [QueueSession](../../javax/jms/QueueSession.md), [Session](../../javax/jms/Session.md), [TopicSession](../../javax/jms/TopicSession.md)

  <!-- -->

  Direct Known Subclasses:
  [AQjmsXASession](AQjmsXASession.md)

  ------------------------------------------------------------------------



      public class AQjmsSession
      extends oracle.jms.AQjmsObject
      implements QueueSession, TopicSession

  This is an Oracle class which implements `javax.jms.Session`, `javax.jms.QueueSession` and `javax.jms.TopicSession`.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface javax.jms.[Session](../../javax/jms/Session.md)

      [`AUTO_ACKNOWLEDGE`](../../javax/jms/Session.md)`, `[`CLIENT_ACKNOWLEDGE`](../../javax/jms/Session.md)`, `[`DUPS_OK_ACKNOWLEDGE`](../../javax/jms/Session.md)`, `[`SESSION_TRANSACTED`](../../javax/jms/Session.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                           | Method and Description                                                                                                                                                                                                                                                                                           |
    |-------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                      | `alterAQAgent``(java.lang.String agentName, boolean enableHTTP, boolean enableSMTP, java.lang.String certLocation)`<br>Alter an AQ agent.                                                                                                                                                                        |
    | `void`                                                      | `bindAgent``(oracle.jms.AQjmsAgent agent, java.lang.String certificate)`<br>Add an agent into LDAP server (bind)                                                                                                                                                                                                 |
    | `void`                                                      | `close``()`<br>Public for test harness purposes                                                                                                                                                                                                                                                                  |
    | `void`                                                      | `commit``()`<br>Commits all messages done in this transaction and releases any locks currently held.                                                                                                                                                                                                             |
    | [`AdtMessage`](AdtMessage.md)                               | `createAdtMessage``()`<br>Creates an `AdtMessage`.                                                                                                                                                                                                                                                               |
    | [`AQjmsAdtMessage`](AQjmsAdtMessage.md)                     | `createAdtMessage``(oracle.sql.CustomDatum payload)`<br>Creates an initialized `AdtMessage`.                                                                                                                                                                                                                     |
    | `void`                                                      | `createAQAgent``(java.lang.String agentName)`<br>Create an AQ agent.                                                                                                                                                                                                                                             |
    | `void`                                                      | `createAQAgent``(java.lang.String agentName, boolean enableHTTP, boolean enableSMTP, java.lang.String certLocation)`<br>Create an AQ agent.                                                                                                                                                                      |
    | [`QueueBrowser`](../../javax/jms/QueueBrowser.md)           | `createBrowser``(`[`Queue`](../../javax/jms/Queue.md)` queue)`<br>Creates a `QueueBrowser` to peek at the messages in the specified queue.                                                                                                                                                                       |
    | [`QueueBrowser`](../../javax/jms/QueueBrowser.md)           | `createBrowser``(`[`Queue`](../../javax/jms/Queue.md)` queue, java.lang.Object payloadFactory)`<br>Creates a `QueueBrowser` to peek at the messages in the specified queue containing ADT messages.                                                                                                              |
    | [`QueueBrowser`](../../javax/jms/QueueBrowser.md)           | `createBrowser``(`[`Queue`](../../javax/jms/Queue.md)` queue, java.lang.String messageSelector)`<br>Creates a `QueueBrowser` to peek at the messages in the specified queue.                                                                                                                                     |
    | [`QueueBrowser`](../../javax/jms/QueueBrowser.md)           | `createBrowser``(`[`Queue`](../../javax/jms/Queue.md)` queue, java.lang.String messageSelector, boolean locked)`<br>Creates a `QueueBrowser` to peek at the messages in the specified queue.                                                                                                                     |
    | [`QueueBrowser`](../../javax/jms/QueueBrowser.md)           | `createBrowser``(`[`Queue`](../../javax/jms/Queue.md)` queue, java.lang.String messageSelector, java.lang.Object payloadFactory)`<br>Creates a `QueueBrowser` to peek at the messages on the specified queue containing ADT messages.                                                                            |
    | [`QueueBrowser`](../../javax/jms/QueueBrowser.md)           | `createBrowser``(`[`Queue`](../../javax/jms/Queue.md)` queue, java.lang.String messageSelector, java.lang.Object payloadFactory, boolean locked)`<br>Creates a `QueueBrowser` to peek at the messages on the specified queue containing ADT messages.                                                            |
    | [`TopicBrowser`](TopicBrowser.md)                           | `createBrowser``(`[`Topic`](../../javax/jms/Topic.md)` topic, java.lang.String consumerName)`<br>Creates a `TopicBrowser` to peek at the messages on the specified topic.                                                                                                                                        |
    | [`TopicBrowser`](TopicBrowser.md)                           | `createBrowser``(`[`Topic`](../../javax/jms/Topic.md)` topic, java.lang.String consumerName, boolean locked)`<br>Creates a `TopicBrowser` to peek at the messages on the specified topic.                                                                                                                        |
    | [`TopicBrowser`](TopicBrowser.md)                           | `createBrowser``(`[`Topic`](../../javax/jms/Topic.md)` topic, java.lang.String consumerName, java.lang.Object payloadFactory)`<br>Creates a `TopicBrowser` to peek at the messages on the specified topic containing ADT messages.                                                                               |
    | [`TopicBrowser`](TopicBrowser.md)                           | `createBrowser``(`[`Topic`](../../javax/jms/Topic.md)` topic, java.lang.String consumerName, java.lang.Object payloadFactory, boolean locked)`<br>Creates a `TopicBrowser` to peek at the messages on the specified topic containing ADT messages.                                                               |
    | [`TopicBrowser`](TopicBrowser.md)                           | `createBrowser``(`[`Topic`](../../javax/jms/Topic.md)` topic, java.lang.String consumerName, java.lang.String messageSelector)`<br>Creates a `TopicBrowser` to peek at the messages on the specified topic.                                                                                                      |
    | [`TopicBrowser`](TopicBrowser.md)                           | `createBrowser``(`[`Topic`](../../javax/jms/Topic.md)` topic, java.lang.String consumerName, java.lang.String messageSelector, boolean locked)`<br>Creates a `TopicBrowser` to peek at the messages on the specified topic.                                                                                      |
    | [`TopicBrowser`](TopicBrowser.md)                           | `createBrowser``(`[`Topic`](../../javax/jms/Topic.md)` topic, java.lang.String consumerName, java.lang.String messageSelector, java.lang.Object payloadFactory)`<br>Creates a `TopicBrowser` to peek at the messages on the specified topic containing ADT messages.                                             |
    | [`TopicBrowser`](TopicBrowser.md)                           | `createBrowser``(`[`Topic`](../../javax/jms/Topic.md)` topic, java.lang.String consumerName, java.lang.String messageSelector, java.lang.Object payloadFactory, boolean locked)`<br>Creates a `TopicBrowser` to peek at the messages on the specified topic containing ADT messages.                             |
    | [`BytesMessage`](../../javax/jms/BytesMessage.md)           | `createBytesMessage``()`<br>Creates a `BytesMessage` object.                                                                                                                                                                                                                                                     |
    | [`MessageConsumer`](../../javax/jms/MessageConsumer.md)     | `createConsumer``(`[`Destination`](../../javax/jms/Destination.md)` destination)`<br>Creates a `MessageConsumer` for the specified destination.                                                                                                                                                                  |
    | [`MessageConsumer`](../../javax/jms/MessageConsumer.md)     | `createConsumer``(`[`Destination`](../../javax/jms/Destination.md)` destination, java.lang.String messageSelector)`<br>Creates a `MessageConsumer` for the specified destination, using a message selector.                                                                                                      |
    | [`MessageConsumer`](../../javax/jms/MessageConsumer.md)     | `createConsumer``(`[`Destination`](../../javax/jms/Destination.md)` destination, java.lang.String messageSelector, boolean NoLocal)`<br>Creates `MessageConsumer` for the specified destination, using a message selector.                                                                                       |
    | [`MessageConsumer`](../../javax/jms/MessageConsumer.md)     | `createConsumer``(`[`Destination`](../../javax/jms/Destination.md)` destination, java.lang.String messageSelector, java.lang.Object payloadFactory, java.lang.String transformation, boolean noLocal)`<br>A generic routine to create a MessageConsumer used to receive messages from the specified destination. |
    | [`TopicSubscriber`](../../javax/jms/TopicSubscriber.md)     | `createDurableSubscriber``(`[`Topic`](../../javax/jms/Topic.md)` topic, java.lang.String subscriberName)`<br>Creates a durable subscriber to the specified topic.                                                                                                                                                |
    | [`TopicSubscriber`](../../javax/jms/TopicSubscriber.md)     | `createDurableSubscriber``(`[`Topic`](../../javax/jms/Topic.md)` topic, java.lang.String subscriberName, java.lang.Object payloadFactory)`<br>Creates a durable subscriber to the specified topic.                                                                                                               |
    | [`TopicSubscriber`](../../javax/jms/TopicSubscriber.md)     | `createDurableSubscriber``(`[`Topic`](../../javax/jms/Topic.md)` topic, java.lang.String subscriberName, java.lang.String messageSelector, boolean noLocal)`<br>Creates a durable subscriber to the specified topic.                                                                                             |
    | [`TopicSubscriber`](../../javax/jms/TopicSubscriber.md)     | `createDurableSubscriber``(`[`Topic`](../../javax/jms/Topic.md)` topic, java.lang.String subscriberName, java.lang.String messageSelector, boolean noLocal, java.lang.Object payloadFactory)`<br>Creates a durable subscriber to the specified topic.                                                            |
    | [`TopicSubscriber`](../../javax/jms/TopicSubscriber.md)     | `createDurableSubscriber``(`[`Topic`](../../javax/jms/Topic.md)` topic, java.lang.String subscriberName, java.lang.String messageSelector, boolean noLocal, java.lang.Object payloadFactory, java.lang.String transformation)`<br>Create a durable Subscriber to the specified topic.                            |
    | [`Destination`](../../javax/jms/Destination.md)             | `createJMSShardedQueue``(java.lang.String queueName, boolean isMultipleConsumer)`<br>Create a JMS sharded queue.                                                                                                                                                                                                 |
    | [`Destination`](../../javax/jms/Destination.md)             | `createJMSShardedQueue``(java.lang.String queueName, boolean isMultipleConsumer, java.lang.String storageClause, int maxRetries, java.lang.String comment)`<br>Create a JMS sharded queue.                                                                                                                       |
    | [`MapMessage`](../../javax/jms/MapMessage.md)               | `createMapMessage``()`<br>Creates a `MapMessage`.                                                                                                                                                                                                                                                                |
    | [`Message`](../../javax/jms/Message.md)                     | `createMessage``()`<br>Creates a `Message` object.                                                                                                                                                                                                                                                               |
    | [`ObjectMessage`](../../javax/jms/ObjectMessage.md)         | `createObjectMessage``()`<br>Creates an `ObjectMessage`.                                                                                                                                                                                                                                                         |
    | [`ObjectMessage`](../../javax/jms/ObjectMessage.md)         | `createObjectMessage``(java.io.Serializable object)`<br>Creates an initialized `ObjectMessage`.                                                                                                                                                                                                                  |
    | [`AdtMessage`](AdtMessage.md)                               | `createORAMessage``()`<br>Creates an `AdtMessage`.                                                                                                                                                                                                                                                               |
    | [`AQjmsAdtMessage`](AQjmsAdtMessage.md)                     | `createORAMessage``(oracle.jdbc.OracleData payload)`<br>Creates an initialized `AdtMessage`.                                                                                                                                                                                                                     |
    | [`AQjmsAdtMessage`](AQjmsAdtMessage.md)                     | `createORAMessage``(oracle.sql.ORAData payload)`<br>Creates an initialized `AdtMessage`.                                                                                                                                                                                                                         |
    | [`MessageProducer`](../../javax/jms/MessageProducer.md)     | `createProducer``(`[`Destination`](../../javax/jms/Destination.md)` destination)`<br>Creates a `MessageProducer` to send messages to the specified destination.                                                                                                                                                  |
    | [`TopicPublisher`](../../javax/jms/TopicPublisher.md)       | `createPublisher``(`[`Topic`](../../javax/jms/Topic.md)` topic)`<br>Create a Publisher for the specified topic.                                                                                                                                                                                                  |
    | [`Queue`](../../javax/jms/Queue.md)                         | `createQueue``(oracle.AQ.AQQueueTable queueTable, java.lang.String queueName, `[`AQjmsDestinationProperty`](AQjmsDestinationProperty.md)` destinationProperty)`<br>Create a queue.                                                                                                                               |
    | [`Queue`](../../javax/jms/Queue.md)                         | `createQueue``(oracle.AQ.AQQueueTable queueTable, java.lang.String queueName, `[`AQjmsDestinationProperty`](AQjmsDestinationProperty.md)` destinationProperty, boolean autonomous)`                                                                                                                              |
    | [`Queue`](../../javax/jms/Queue.md)                         | `createQueue``(java.lang.String queueName)`<br>Creates a queue identity given a `Queue` name.                                                                                                                                                                                                                    |
    | `oracle.AQ.AQQueueTable`                                    | `createQueueTable``(java.lang.String owner, java.lang.String name, oracle.AQ.AQQueueTableProperty property)`<br>Create a Queue Table.                                                                                                                                                                            |
    | `oracle.AQ.AQQueueTable`                                    | `createQueueTable``(java.lang.String owner, java.lang.String name, oracle.AQ.AQQueueTableProperty property, boolean autonomous)`                                                                                                                                                                                 |
    | [`QueueReceiver`](../../javax/jms/QueueReceiver.md)         | `createReceiver``(`[`Queue`](../../javax/jms/Queue.md)` queue)`<br>Creates a `QueueReceiver` to receive messages from a queue containing JMS payloads.                                                                                                                                                           |
    | [`QueueReceiver`](../../javax/jms/QueueReceiver.md)         | `createReceiver``(`[`Queue`](../../javax/jms/Queue.md)` queue, java.lang.Object payloadFactory)`<br>Creates a `QueueReceiver` to receive messages from a queue containing ADT messages.                                                                                                                          |
    | [`QueueReceiver`](../../javax/jms/QueueReceiver.md)         | `createReceiver``(`[`Queue`](../../javax/jms/Queue.md)` queue, java.lang.String messageSelector)`<br>Creates a `QueueReceiver` to receive messages from a queue containing JMS payloads.                                                                                                                         |
    | [`QueueReceiver`](../../javax/jms/QueueReceiver.md)         | `createReceiver``(`[`Queue`](../../javax/jms/Queue.md)` queue, java.lang.String messageSelector, java.lang.Object payloadFactory)`<br>Creates a `QueueReceiver` to receive messages from a queue containing ADT messages.                                                                                        |
    | `void`                                                      | `createRemoteSubscriber``(`[`Topic`](../../javax/jms/Topic.md)` topic, oracle.jms.AQjmsAgent remoteSubscriber, java.lang.String messageSelector)`<br>Creates a remote topic subscriber.                                                                                                                          |
    | `void`                                                      | `createRemoteSubscriber``(`[`Topic`](../../javax/jms/Topic.md)` topic, oracle.jms.AQjmsAgent remoteSubscriber, java.lang.String messageSelector, java.lang.Object payloadFactory)`<br>Creates a remote topic subscriber.                                                                                         |
    | `void`                                                      | `createRemoteSubscriber``(`[`Topic`](../../javax/jms/Topic.md)` topic, oracle.jms.AQjmsAgent remoteSubscriber, java.lang.String messageSelector, java.lang.Object payloadFactory, java.lang.String transformation)`<br>Creates a remote topic subscriber.                                                        |
    | `void`                                                      | `createRemoteSubscriber``(`[`Topic`](../../javax/jms/Topic.md)` topic, oracle.jms.AQjmsAgent remoteSubscriber, java.lang.String messageSelector, java.lang.Object payloadFactory, java.lang.String transformation, boolean queueToQueue)`<br>Create a remote subscriber for a topic.                             |
    | [`QueueSender`](../../javax/jms/QueueSender.md)             | `createSender``(`[`Queue`](../../javax/jms/Queue.md)` queue)`<br>Creates a `QueueSender` to send messages to a queue.                                                                                                                                                                                            |
    | [`StreamMessage`](../../javax/jms/StreamMessage.md)         | `createStreamMessage``()`<br>Creates a `StreamMessage`.                                                                                                                                                                                                                                                          |
    | [`TopicSubscriber`](../../javax/jms/TopicSubscriber.md)     | `createSubscriber``(`[`Topic`](../../javax/jms/Topic.md)` topic)`<br>Creates a nondurable subscriber to the specified topic.                                                                                                                                                                                     |
    | [`TopicSubscriber`](../../javax/jms/TopicSubscriber.md)     | `createSubscriber``(`[`Topic`](../../javax/jms/Topic.md)` topic, java.lang.String messageSelector, boolean noLocal)`<br>Creates a nondurable subscriber to the specified topic, using a message selector or specifying whether messages published by its own connection should be delivered to it.               |
    | [`TemporaryQueue`](../../javax/jms/TemporaryQueue.md)       | `createTemporaryQueue``()`<br>Creates a `TemporaryQueue` object.                                                                                                                                                                                                                                                 |
    | [`TemporaryTopic`](../../javax/jms/TemporaryTopic.md)       | `createTemporaryTopic``()`<br>Create a temporary topic.                                                                                                                                                                                                                                                          |
    | [`TextMessage`](../../javax/jms/TextMessage.md)             | `createTextMessage``()`<br>Creates a `TextMessage`.                                                                                                                                                                                                                                                              |
    | [`TextMessage`](../../javax/jms/TextMessage.md)             | `createTextMessage``(java.lang.String text)`<br>Creates an initialized `TextMessage`.                                                                                                                                                                                                                            |
    | [`TextMessage`](../../javax/jms/TextMessage.md)             | `createTextMessage``(java.lang.StringBuffer stringBuffer)`<br>Creates an initialized `TextMessage`.                                                                                                                                                                                                              |
    | [`Topic`](../../javax/jms/Topic.md)                         | `createTopic``(oracle.AQ.AQQueueTable queueTable, java.lang.String topicName, `[`AQjmsDestinationProperty`](AQjmsDestinationProperty.md)` destinationProperty)`<br>Create a topic                                                                                                                                |
    | [`Topic`](../../javax/jms/Topic.md)                         | `createTopic``(oracle.AQ.AQQueueTable queueTable, java.lang.String topicName, `[`AQjmsDestinationProperty`](AQjmsDestinationProperty.md)` destinationProperty, boolean autonomous)`                                                                                                                              |
    | [`Topic`](../../javax/jms/Topic.md)                         | `createTopic``(java.lang.String topicName)`<br>Creates a topic identity given a `Topic` name.                                                                                                                                                                                                                    |
    | [`AQjmsTopicReceiver`](AQjmsTopicReceiver.md)               | `createTopicReceiver``(`[`Topic`](../../javax/jms/Topic.md)` topic, java.lang.String receiverName, java.lang.String messageSelector)`<br>Creates a `TopicReceiver` to receive messages from the specified topic.                                                                                                 |
    | [`AQjmsTopicReceiver`](AQjmsTopicReceiver.md)               | `createTopicReceiver``(`[`Topic`](../../javax/jms/Topic.md)` topic, java.lang.String receiverName, java.lang.String messageSelector, java.lang.Object payloadFactory)`<br>Creates a `TopicReceiver` to receive messages from the specified topic.                                                                |
    | `void`                                                      | `disableDBAccess``(java.lang.String agentName, java.lang.String dbUserName)`<br>Disable Agent Database Access This method revokes the privileges of the specified database user.                                                                                                                                 |
    | `void`                                                      | `dropAQAgent``(java.lang.String agentName)`<br>Drop AQ agent.                                                                                                                                                                                                                                                    |
    | `void`                                                      | `enableDBAccess``(java.lang.String agentName, java.lang.String dbUserName)`<br>Enable Agent Database Access This method enables the given agent name to have the privileges of the specified database user.                                                                                                      |
    | `int`                                                       | `getAckMode``()`<br>Returns the acknowledgement mode with which this session was created.                                                                                                                                                                                                                        |
    | `int`                                                       | `getAcknowledgeMode``()`<br>Returns the acknowledgement mode of the session.                                                                                                                                                                                                                                     |
    | `java.sql.Connection`                                       | `getDBConnection``()`<br>Return the JDBC connection used to connect to the database.                                                                                                                                                                                                                             |
    | [`ExceptionListener`](../../javax/jms/ExceptionListener.md) | `getExceptionListener``()`                                                                                                                                                                                                                                                                                       |
    | [`AQjmsConnection`](AQjmsConnection.md)                     | `getJmsConnection``()`<br>This method returns the JMS connection in which this session was created.                                                                                                                                                                                                              |
    | [`MessageListener`](../../javax/jms/MessageListener.md)     | `getMessageListener``()`<br>Returns this session's distinguished message listener.                                                                                                                                                                                                                               |
    | [`Queue`](../../javax/jms/Queue.md)                         | `getQueue``(java.lang.String owner, java.lang.String name)`<br>Get an existing queue.                                                                                                                                                                                                                            |
    | `oracle.AQ.AQQueueTable`                                    | `getQueueTable``(java.lang.String owner, java.lang.String name)`<br>Get a handle to an existing queue-table If owner of queue-table is not the same as the user which opened the connection, the caller must have AQ enqueue/dequeue priveleges on queues/topics in the queue table.                             |
    | [`Topic`](../../javax/jms/Topic.md)                         | `getTopic``(java.lang.String owner, java.lang.String name)`<br>Get an existing topic.                                                                                                                                                                                                                            |
    | `boolean`                                                   | `getTransacted``()`<br>Checks if this session is in transacted mode.                                                                                                                                                                                                                                             |
    | `java.util.Map`                                             | `getTypeMap``()`<br>Get the JDBC type map                                                                                                                                                                                                                                                                        |
    | `void`                                                      | `grantSystemPrivilege``(java.lang.String privilege, java.lang.String grantee, boolean adminOption)`<br>Grants AQ system privileges to users/roles.                                                                                                                                                               |
    | `void`                                                      | `recover``()`<br>Rolls back the current transaction in the [`Session.CLIENT_ACKNOWLEDGE`](../../javax/jms/Session.md) mode if this session is a non-transacted session.                                                                                                                                          |
    | `void`                                                      | `restartConsumers``()`<br>Restarts receive on all consumers in cons_list Called when a commit or rollback is detected                                                                                                                                                                                            |
    | `void`                                                      | `revokeSystemPrivilege``(java.lang.String privilege, java.lang.String grantee)`<br>Revokes AQ system privilege from user/roles.                                                                                                                                                                                  |
    | `void`                                                      | `rollback``()`<br>Rolls back any messages done in this transaction and releases any locks currently held.                                                                                                                                                                                                        |
    | `void`                                                      | `run``()`<br>Optional operation, intended to be used only by Application Servers, not by ordinary JMS clients.                                                                                                                                                                                                   |
    | `void`                                                      | `setExceptionListener``(`[`ExceptionListener`](../../javax/jms/ExceptionListener.md)` eListener)`<br>Set Exception Listener for JMS Session                                                                                                                                                                      |
    | `void`                                                      | `setMessageListener``(`[`MessageListener`](../../javax/jms/MessageListener.md)` listener)`<br>Sets this session's distinguished message listener.                                                                                                                                                                |
    | `void`                                                      | `unbindAgent``(oracle.jms.AQjmsAgent agent)`<br>remove an agent from LDAP server (unbind)                                                                                                                                                                                                                        |
    | `void`                                                      | `unsubscribe``(java.lang.String subscriberName)`<br>Unsubscribe a durable subscription that has been created by a client.                                                                                                                                                                                        |
    | `void`                                                      | `unsubscribe``(`[`Topic`](../../javax/jms/Topic.md)` topic, oracle.jms.AQjmsAgent remoteSubscriber)`<br>Unsubscribe a remote durable subscription that has been created by a client on the specified topic                                                                                                       |
    | `void`                                                      | `unsubscribe``(`[`Topic`](../../javax/jms/Topic.md)` topic, java.lang.String subscriberName)`<br>Unsubscribe a durable subscription that has been created by a client on the specified topic                                                                                                                     |

    - ### Methods inherited from class oracle.jms.AQjmsObject

      `checkClosed, children, finalize, getID, getParent, isOpen, localClose, preClose`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### createBytesMessage

          public BytesMessage createBytesMessage()
                                          throws JMSException

      Creates a `BytesMessage` object. A `BytesMessage` object is used to send a message containing a stream of uninterpreted bytes.
      Specified by:
      [`createBytesMessage`](../../javax/jms/Session.md) in interface [`Session`](../../javax/jms/Session.md)

      Returns:
      the message

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message is not created due to some error.

    <!-- -->

    - #### createMapMessage

          public MapMessage createMapMessage()
                                      throws JMSException

      Creates a `MapMessage`. A `MapMessage` is used to send a set of name-value pairs where names are `String`s and values are instances of Java primitive types.
      Specified by:
      [`createMapMessage`](../../javax/jms/Session.md) in interface [`Session`](../../javax/jms/Session.md)

      Returns:
      the message

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message is not created due to some error.

    <!-- -->

    - #### createMessage

          public Message createMessage()
                                throws JMSException

      Creates a `Message` object. The `Message` interface is the root interface of all JMS messages. A `Message` object holds all the standard message header information. It can be sent when a message containing only header information is sufficient.
      Specified by:
      [`createMessage`](../../javax/jms/Session.md) in interface [`Session`](../../javax/jms/Session.md)

      Returns:
      the message

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message is not created due to some error.

    <!-- -->

    - #### createObjectMessage

          public ObjectMessage createObjectMessage()
                                            throws JMSException

      Creates an `ObjectMessage`. An `ObjectMessage` is used to send a message that contains a serializable Java object.
      Specified by:
      [`createObjectMessage`](../../javax/jms/Session.md) in interface [`Session`](../../javax/jms/Session.md)

      Returns:
      the message

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message is not created due to some error.

    <!-- -->

    - #### createObjectMessage

          public ObjectMessage createObjectMessage(java.io.Serializable object)
                                            throws JMSException

      Creates an initialized `ObjectMessage`. An `ObjectMessage` is used to send a message that contains a serializable Java object.
      Specified by:
      [`createObjectMessage`](../../javax/jms/Session.md) in interface [`Session`](../../javax/jms/Session.md)

      Parameters:
      `object` - the object to use to initialize this message

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message is not created due to some error.

    <!-- -->

    - #### createAdtMessage

          public AdtMessage createAdtMessage()
                                      throws JMSException

      Creates an `AdtMessage`. An `AdtMessage` is used to send a message that contains a Java object that maps to an Oracle SQL ADT and implements the Oracle `CustomDatum` interface.
      Returns:
      the message

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message is not created due to some error.

    <!-- -->

    - #### createAdtMessage

          public AQjmsAdtMessage createAdtMessage(oracle.sql.CustomDatum payload)
                                           throws JMSException

      Creates an initialized `AdtMessage`. An `AQjmsAdtMessage` is used to send a message that contains a Java object that maps to an Oracle SQL ADT and implements the Oracle `CustomDatum` interface.
      **Important:** `CustomDatum` support (and hence this method) will be deprecated in a future release.

      Parameters:
      `payload` - the object to use to initialize this message

      Returns:
      the message

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message is not created due to some error.

      See Also:
      `AQjmsSession.createORAMessage(OracleData)`

    <!-- -->

    - #### createORAMessage

          public AdtMessage createORAMessage()
                                      throws JMSException

      Creates an `AdtMessage`. An `AdtMessage` is used to send a message that contains a Java object that maps to an Oracle SQL ADT and implements the `ORAData` interface.
      Returns:
      the message

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message is not created due to some error.

    <!-- -->

    - #### createORAMessage

          public AQjmsAdtMessage createORAMessage(oracle.jdbc.OracleData payload)
                                           throws JMSException

      Creates an initialized `AdtMessage`. An `AQjmsAdtMessage` is used to send a message that contains a Java object that maps to an Oracle SQL ADT and implements the `OracleData` interface.
      Parameters:
      `payload` - the object to use to initialize this message

      Returns:
      the message

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message is not created due to some error.

    <!-- -->

    - #### createORAMessage

          public AQjmsAdtMessage createORAMessage(oracle.sql.ORAData payload)
                                           throws JMSException

      Creates an initialized `AdtMessage`. An `AQjmsAdtMessage` is used to send a message that contains a Java object that maps to an Oracle SQL ADT and implements the `ORAData` interface.
      Parameters:
      `payload` - the object to use to initialize this message

      Returns:
      the message

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message is not created due to some error.

    <!-- -->

    - #### createStreamMessage

          public StreamMessage createStreamMessage()
                                            throws JMSException

      Creates a `StreamMessage`. A `StreamMessage` is used to send a stream of Java primitives.
      Specified by:
      [`createStreamMessage`](../../javax/jms/Session.md) in interface [`Session`](../../javax/jms/Session.md)

      Returns:
      the message

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message is not created due to some error.

    <!-- -->

    - #### createTextMessage

          public TextMessage createTextMessage()
                                        throws JMSException

      Creates a `TextMessage`. A `TextMessage` is used to send a message containing a text payload.
      Specified by:
      [`createTextMessage`](../../javax/jms/Session.md) in interface [`Session`](../../javax/jms/Session.md)

      Returns:
      the message

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message is not created due to some error.

    <!-- -->

    - #### createTextMessage

          public TextMessage createTextMessage(java.lang.StringBuffer stringBuffer)
                                        throws JMSException

      Creates an initialized `TextMessage`. A `TextMessage` is used to send a message containing a text payload.
      Parameters:
      `stringBuffer` - the string buffer used to initialize this message

      Returns:
      the message

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message is not created due to some error.

    <!-- -->

    - #### createTextMessage

          public TextMessage createTextMessage(java.lang.String text)
                                        throws JMSException

      Creates an initialized `TextMessage`. A `TextMessage` is used to send a message containing a text payload.
      Specified by:
      [`createTextMessage`](../../javax/jms/Session.md) in interface [`Session`](../../javax/jms/Session.md)

      Parameters:
      `text` - the text payload used to initialize this message

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message is not created due to some error.

    <!-- -->

    - #### getTransacted

          public boolean getTransacted()
                                throws JMSException

      Checks if this session is in transacted mode.
      Specified by:
      [`getTransacted`](../../javax/jms/Session.md) in interface [`Session`](../../javax/jms/Session.md)

      Returns:
      `true` iff in transacted mode

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if this session is closed.

    <!-- -->

    - #### getAckMode

          public int getAckMode()
                         throws JMSException

      Returns the acknowledgement mode with which this session was created.
      **Important:** This method will be deprecated in a future release.Use `getAcknowledgeMode()` instead.

      Returns:
      acknowlegement mode as an int

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if this session is closed.

      See Also:
      `AQjmsSession.getAcknowledgeMode()`

    <!-- -->

    - #### commit

          public void commit()
                      throws JMSException

      Commits all messages done in this transaction and releases any locks currently held.
      Specified by:
      [`commit`](../../javax/jms/Session.md) in interface [`Session`](../../javax/jms/Session.md)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the transaction is not committed due to some error.

    <!-- -->

    - #### rollback

          public void rollback()
                        throws JMSException

      Rolls back any messages done in this transaction and releases any locks currently held.
      Specified by:
      [`rollback`](../../javax/jms/Session.md) in interface [`Session`](../../javax/jms/Session.md)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the transaction is not rolled back due to some error.

    <!-- -->

    - #### close

          public void close()
                     throws JMSException

      Description copied from class: `oracle.jms.AQjmsObject`
      Public for test harness purposes
      Specified by:
      [`close`](../../javax/jms/Session.md) in interface [`Session`](../../javax/jms/Session.md)

      Overrides:
      `close` in class `oracle.jms.AQjmsObject`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the session is not closed due to some error.

    <!-- -->

    - #### recover

          public void recover()
                       throws JMSException

      Rolls back the current transaction in the [`Session.CLIENT_ACKNOWLEDGE`](../../javax/jms/Session.md) mode if this session is a non-transacted session. Otherwise, this call could come from a message listener's `onMessage()` method, in which case the transaction should be rolled back for all acknowledgement modes (since the listener did not successfully process the message). In all other cases the call is ignored
      Specified by:
      [`recover`](../../javax/jms/Session.md) in interface [`Session`](../../javax/jms/Session.md)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to stop and restart message delivery due to some internal error.

      [`IllegalStateException`](../../javax/jms/IllegalStateException.md) - if the method is called by a transacted session.

      See Also:
      [`Session.recover()`](../../javax/jms/Session.md)

    <!-- -->

    - #### getMessageListener

          public MessageListener getMessageListener()
                                             throws JMSException

      Returns this session's distinguished message listener.
      Specified by:
      [`getMessageListener`](../../javax/jms/Session.md) in interface [`Session`](../../javax/jms/Session.md)

      Returns:
      the message listener associated with this session

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message listener is not retrieved due to some error.

      See Also:
      [`Session.setMessageListener(javax.jms.MessageListener)`](../../javax/jms/Session.md), [`ServerSessionPool`](../../javax/jms/ServerSessionPool.md), [`ServerSession`](../../javax/jms/ServerSession.md)

    <!-- -->

    - #### setMessageListener

          public void setMessageListener(MessageListener listener)
                                  throws JMSException

      Sets this session's distinguished message listener. When it is set, no other form of message receipt in the session can be used; however, all forms of sending messages are still supported.
      Specified by:
      [`setMessageListener`](../../javax/jms/Session.md) in interface [`Session`](../../javax/jms/Session.md)

      Parameters:
      `listener` - the message listener to associate with this session

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message listener is not set due to some error.

      See Also:
      [`Session.getMessageListener()`](../../javax/jms/Session.md), [`ServerSessionPool`](../../javax/jms/ServerSessionPool.md), [`ServerSession`](../../javax/jms/ServerSession.md)

    <!-- -->

    - #### setExceptionListener

          public void setExceptionListener(ExceptionListener eListener)

      Set Exception Listener for JMS Session
      Parameters:
      `eListener` - the exception listener to associate with this session

    <!-- -->

    - #### getExceptionListener

          public ExceptionListener getExceptionListener()

      Returns:
      Exception Listener assosicated with this session

    <!-- -->

    - #### createQueue

          public Queue createQueue(java.lang.String queueName)
                            throws JMSException

      Description copied from interface: [`QueueSession`](../../javax/jms/QueueSession.md)
      Creates a queue identity given a `Queue` name.
      This facility is provided for the rare cases where clients need to dynamically manipulate queue identity. It allows the creation of a queue identity with a provider-specific name. Clients that depend on this ability are not portable.

      Note that this method is not for creating the physical queue. The physical creation of queues is an administrative task and is not to be initiated by the JMS API. The one exception is the creation of temporary queues, which is accomplished with the `createTemporaryQueue` method.

      Specified by:
      [`createQueue`](../../javax/jms/QueueSession.md) in interface [`QueueSession`](../../javax/jms/QueueSession.md)

      Specified by:
      [`createQueue`](../../javax/jms/Session.md) in interface [`Session`](../../javax/jms/Session.md)

      Parameters:
      `queueName` - name of queue, format is *schema*.*queueName* (where the *schema*. is optional)

      Returns:
      the queue

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the queue is not created due to some error.

    <!-- -->

    - #### createReceiver

          public QueueReceiver createReceiver(Queue queue)
                                       throws JMSException

      Creates a `QueueReceiver` to receive messages from a queue containing JMS payloads.
      This method is used to create receivers for queues that contain JMS payloads (payloads of type `aq$_jms_*`) or payloads of type `Sys.AnyData`.

      For `Sys.AnyData` queues, the typemap must be populated with `ORADataFactory` objects for any user-defined SQL types.

      Specified by:
      [`createReceiver`](../../javax/jms/QueueSession.md) in interface [`QueueSession`](../../javax/jms/QueueSession.md)

      Parameters:
      `queue` - the queue to access

      Returns:
      the queue receiver

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a receiver is not created due to some error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if an invalid `Queue` is specified.

    <!-- -->

    - #### createReceiver

          public QueueReceiver createReceiver(Queue queue,
                                              java.lang.Object payloadFactory)
                                       throws JMSException

      Creates a `QueueReceiver` to receive messages from a queue containing ADT messages.
      This method is used to create receivers for queues that contain Oracle ADT payloads.

      Parameters:
      `queue` - the queue to access

      `payloadFactory` - `CustomDatumFactory`/`ORADataFactory` for the java class that maps to the Oracle ADT

      Returns:
      the queue receiver

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a receiver is not created due to some error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if an invalid `Queue` is specified.

    <!-- -->

    - #### createReceiver

          public QueueReceiver createReceiver(Queue queue,
                                              java.lang.String messageSelector)
                                       throws JMSException

      Creates a `QueueReceiver` to receive messages from a queue containing JMS payloads.
      This method is used to create receivers for queues that contain JMS payloads (payloads of type `aq$_jms_*`) or payloads of type `Sys.AnyData`.

      For `Sys.AnyData` queues, the typemap must be populated with `ORADataFactory` objects for any user-defined SQL types.

      Specified by:
      [`createReceiver`](../../javax/jms/QueueSession.md) in interface [`QueueSession`](../../javax/jms/QueueSession.md)

      Parameters:
      `queue` - the queue to access

      `messageSelector` - only messages with properties matching the message selector expression are delivered
      When used with an 8.2 or later database, standard JMS selector syntax is fully supported.
      When used with a pre-8.2 database, the message selector is limited to one of the following:

      - `JMSMessageID` to retrieve messages that have the specified message ID. All message IDs must be prefixed with "ID:". For example, `JMSMessageID = 'ID:2345234523452345'`.
      - `JMSCorrelationID` to retrieve messages that have a certain correlationID. For example, `JMSCorrelationID = 'RUSH'`.

      Returns:
      the queue receiver

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a receiver is not created due to some error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if an invalid `Queue` is specified.

      [`InvalidSelectorException`](../../javax/jms/InvalidSelectorException.md) - if the message selector is invalid.

    <!-- -->

    - #### createReceiver

          public QueueReceiver createReceiver(Queue queue,
                                              java.lang.String messageSelector,
                                              java.lang.Object payloadFactory)
                                       throws JMSException

      Creates a `QueueReceiver` to receive messages from a queue containing ADT messages.
      This method is used to create receivers for queues that contain Oracle ADT payloads.

      Parameters:
      `queue` - the queue to access

      `messageSelector` - only messages with properties matching the message selector expression are delivered

      `payloadFactory` - `CustomDatumFactory`/`ORADataFactory` for the java class that maps to the Oracle ADT

      Returns:
      the queue receiver

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a receiver is not created due to some error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if an invalid `Queue` is specified.

      [`InvalidSelectorException`](../../javax/jms/InvalidSelectorException.md) - if the message selector is invalid.

    <!-- -->

    - #### createSender

          public QueueSender createSender(Queue queue)
                                   throws JMSException

      Creates a `QueueSender` to send messages to a queue.
      Specified by:
      [`createSender`](../../javax/jms/QueueSession.md) in interface [`QueueSession`](../../javax/jms/QueueSession.md)

      Parameters:
      `queue` - the queue to access, or `null` to create an unidentifed producer

      Returns:
      the queue sender

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a sender is not created due to some error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if an invalid `Queue` is specified.

    <!-- -->

    - #### createBrowser

          public QueueBrowser createBrowser(Queue queue)
                                     throws JMSException

      Creates a `QueueBrowser` to peek at the messages in the specified queue.
      This method is used to create browsers for queues that contain JMS payloads (payloads of type `aq$_jms_*`) or payloads of type `Sys.AnyData`.

      Specified by:
      [`createBrowser`](../../javax/jms/QueueSession.md) in interface [`QueueSession`](../../javax/jms/QueueSession.md)

      Specified by:
      [`createBrowser`](../../javax/jms/Session.md) in interface [`Session`](../../javax/jms/Session.md)

      Parameters:
      `queue` - the queue to access

      Returns:
      the browser

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a browser is not created due to some error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if an invalid `Queue` is specified.

    <!-- -->

    - #### createBrowser

          public QueueBrowser createBrowser(Queue queue,
                                            java.lang.Object payloadFactory)
                                     throws JMSException

      Creates a `QueueBrowser` to peek at the messages in the specified queue containing ADT messages.
      This method is used to create receivers for queues that contain Oracle ADT payloads.

      Parameters:
      `queue` - the queue to access

      `payloadFactory` - `CustomDatumFactory`/`ORADataFactory` for the java class that maps to the Oracle ADT.

      **Important:** `CustomDatum` support will be deprecated in a future release. Use `ORAData` instead.

      Returns:
      the browser

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a browser is not created due to some error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if an invalid `Queue` is specified.

    <!-- -->

    - #### createBrowser

          public QueueBrowser createBrowser(Queue queue,
                                            java.lang.String messageSelector)
                                     throws JMSException

      Creates a `QueueBrowser` to peek at the messages in the specified queue.
      This method is used to create browsers for queues that contain JMS payloads (payloads of type `aq$_jms_*`) or payloads of type `Sys.AnyData`.

      For `Sys.AnyData` queues, the typemap must be populated with `ORADataFactory` objects for any user-defined SQL types.

      Specified by:
      [`createBrowser`](../../javax/jms/QueueSession.md) in interface [`QueueSession`](../../javax/jms/QueueSession.md)

      Specified by:
      [`createBrowser`](../../javax/jms/Session.md) in interface [`Session`](../../javax/jms/Session.md)

      Parameters:
      `queue` - the queue to access

      `messageSelector` - only messages with properties matching the message selector expression are delivered

      Returns:
      the browser

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a browser is not created due to some error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if an invalid `Queue` is specified.

      [`InvalidSelectorException`](../../javax/jms/InvalidSelectorException.md) - if the message selector is invalid.

    <!-- -->

    - #### createBrowser

          public QueueBrowser createBrowser(Queue queue,
                                            java.lang.String messageSelector,
                                            boolean locked)
                                     throws JMSException

      Creates a `QueueBrowser` to peek at the messages in the specified queue.
      This method is used to create browsers for queues that contain JMS payloads (payloads of type `aq$_jms_*`) or payloads of type `Sys.AnyData`.

      For `Sys.AnyData` queues, the typemap must be populated with `ORADataFactory` objects for any user-defined SQL types.

      Parameters:
      `queue` - the queue to access

      `messageSelector` - only messages with properties matching the message selector expression are delivered

      `locked` - if `true` then messages are locked as they are browsed (similar to a `SELECT` for `UPDATE`)

      Returns:
      the browser

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a browser is not created due to some error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if an invalid `Queue` is specified.

      [`InvalidSelectorException`](../../javax/jms/InvalidSelectorException.md) - if the message selector is invalid.

    <!-- -->

    - #### createBrowser

          public QueueBrowser createBrowser(Queue queue,
                                            java.lang.String messageSelector,
                                            java.lang.Object payloadFactory)
                                     throws JMSException

      Creates a `QueueBrowser` to peek at the messages on the specified queue containing ADT messages.
      This method is used to create browsers for queues that contain Oracle ADT payloads.

      Parameters:
      `queue` - the queue to access

      `messageSelector` - only messages with properties matching the message selector expression are delivered

      `payloadFactory` - `CustomDatumFactory`/`ORADataFactory` for the java class that maps to the Oracle ADT

      **Important:** `CustomDatum` support will be deprecated in a future release. Use `ORAData` instead.

      Returns:
      the browser

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a browser is not created due to some error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if an invalid `Queue` is specified.

    <!-- -->

    - #### createBrowser

          public QueueBrowser createBrowser(Queue queue,
                                            java.lang.String messageSelector,
                                            java.lang.Object payloadFactory,
                                            boolean locked)
                                     throws JMSException

      Creates a `QueueBrowser` to peek at the messages on the specified queue containing ADT messages.
      This method is used to create browsers for queues that contain Oracle ADT payloads.

      Parameters:
      `queue` - the queue to access

      `messageSelector` - only messages with properties matching the message selector expression are delivered

      `payloadFactory` - `CustomDatumFactory`/`ORADataFactory` for the java class that maps to the Oracle ADT

      `locked` - if `true` then messages are locked as they are browsed (similar to a `SELECT` for `UPDATE`)

      **Important:** `CustomDatum` support will be deprecated in a future release. Use `ORAData` instead.

      Returns:
      the browser

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a browser is not created due to some error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if an invalid `Queue` is specified.

    <!-- -->

    - #### createBrowser

          public TopicBrowser createBrowser(Topic topic,
                                            java.lang.String consumerName)
                                     throws JMSException

      Creates a `TopicBrowser` to peek at the messages on the specified topic. Subscribers are durable.
      This method is used to create browsers for topics that contain JMS payloads (payloads of type `aq$_jms_*`) or payloads of type `Sys.AnyData`.

      Parameters:
      `topic` - the topic to access

      `consumerName` - the name of the durable subscriber/consumer

      Returns:
      the browser

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a browser is not created due to some error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if an invalid `Topic` is specified.

    <!-- -->

    - #### createBrowser

          public TopicBrowser createBrowser(Topic topic,
                                            java.lang.String consumerName,
                                            boolean locked)
                                     throws JMSException

      Creates a `TopicBrowser` to peek at the messages on the specified topic. Subscribers are durable.
      This method is used to create browsers for topics that contain JMS payloads (payloads of type `aq$_jms_*`) or payloads of type `Sys.AnyData`.

      Parameters:
      `topic` - the topic to access

      `consumerName` - the name of the durable subscriber/consumer

      `locked` - if `true` then messages are locked as they are browsed (similar to a `SELECT` for `UPDATE`)

      Returns:
      the browser

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a browser is not created due to some error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if an invalid `Topic` is specified.

    <!-- -->

    - #### createBrowser

          public TopicBrowser createBrowser(Topic topic,
                                            java.lang.String consumerName,
                                            java.lang.Object payloadFactory)
                                     throws JMSException

      Creates a `TopicBrowser` to peek at the messages on the specified topic containing ADT messages. Subscribers are durable.
      This method is used to create receivers for topics that contain Oracle ADT payloads.

      Parameters:
      `topic` - the topic to access

      `consumerName` - the name of the durable subscriber/consumer

      `payloadFactory` - `CustomDatumFactory`/`ORADataFactory` for the java class that maps to the Oracle ADT

      **Important:** `CustomDatum` support will be deprecated in a future release. Use `ORAData` instead.

      Returns:
      the browser

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a browser is not created due to some error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if an invalid `Topic` is specified.

    <!-- -->

    - #### createBrowser

          public TopicBrowser createBrowser(Topic topic,
                                            java.lang.String consumerName,
                                            java.lang.Object payloadFactory,
                                            boolean locked)
                                     throws JMSException

      Creates a `TopicBrowser` to peek at the messages on the specified topic containing ADT messages. Subscribers are durable.
      This method is used to create receivers for topics that contain Oracle ADT payloads.

      Parameters:
      `topic` - the topic to access

      `consumerName` - the name of the durable subscriber/consumer

      `payloadFactory` - `CustomDatumFactory`/`ORADataFactory` for the java class that maps to the Oracle ADT

      **Important:** `CustomDatum` support will be deprecated in a future release. Use `ORAData` instead.

      `locked` - if `true` then messages are locked as they are browsed (similar to a `SELECT` for `UPDATE`)

      Returns:
      the browser

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a browser is not created due to some error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if an invalid `Topic` is specified.

    <!-- -->

    - #### createBrowser

          public TopicBrowser createBrowser(Topic topic,
                                            java.lang.String consumerName,
                                            java.lang.String messageSelector)
                                     throws JMSException

      Creates a `TopicBrowser` to peek at the messages on the specified topic. Subscribers are durable.
      This method is used to create browsers for topics that contain JMS payloads (payloads of type `aq$_jms_*`) or payloads of type `Sys.AnyData`.

      Parameters:
      `topic` - the topic to access

      `consumerName` - the name of the durable subscriber/consumer

      `messageSelector` - only messages with properties matching the message selector expression are delivered

      Returns:
      the browser

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a browser is not created due to some error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if an invalid `Topic` is specified.

      [`InvalidSelectorException`](../../javax/jms/InvalidSelectorException.md) - if the message selector is invalid.

    <!-- -->

    - #### createBrowser

          public TopicBrowser createBrowser(Topic topic,
                                            java.lang.String consumerName,
                                            java.lang.String messageSelector,
                                            boolean locked)
                                     throws JMSException

      Creates a `TopicBrowser` to peek at the messages on the specified topic. Subscribers are durable.
      This method is used to create browsers for topics that contain JMS payloads (payloads of type `aq$_jms_*`) or payloads of type `Sys.AnyData`.

      Parameters:
      `topic` - the topic to access

      `consumerName` - the name of the durable subscriber/consumer

      `messageSelector` - only messages with properties matching the message selector expression are delivered

      `locked` - if `true` then messages are locked as they are browsed (similar to a `SELECT` for `UPDATE`)

      Returns:
      the browser

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a browser is not created due to some error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if an invalid `Topic` is specified.

      [`InvalidSelectorException`](../../javax/jms/InvalidSelectorException.md) - if the message selector is invalid.

    <!-- -->

    - #### createBrowser

          public TopicBrowser createBrowser(Topic topic,
                                            java.lang.String consumerName,
                                            java.lang.String messageSelector,
                                            java.lang.Object payloadFactory)
                                     throws JMSException

      Creates a `TopicBrowser` to peek at the messages on the specified topic containing ADT messages. Subscriber names are durable.
      This method is used to create browsers for topics that contain Oracle ADT payloads.

      Parameters:
      `topic` - the topic to access

      `consumerName` - the name of the durable subscriber/consumer to use

      `messageSelector` - only messages with properties matching the message selector expression are delivered

      `payloadFactory` - `CustomDatumFactory`/`ORADataFactory` for the java class that maps to the Oracle ADT

      **Important:** `CustomDatum` support will be deprecated in a future release. Use `ORAData` instead.

      Returns:
      the browser

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a browser is not created due to some error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if an invalid `Topic` is specified.

    <!-- -->

    - #### createBrowser

          public TopicBrowser createBrowser(Topic topic,
                                            java.lang.String consumerName,
                                            java.lang.String messageSelector,
                                            java.lang.Object payloadFactory,
                                            boolean locked)
                                     throws JMSException

      Creates a `TopicBrowser` to peek at the messages on the specified topic containing ADT messages. Subscriber names are durable.
      This method is used to create browsers for topics that contain Oracle ADT payloads.

      Parameters:
      `topic` - the topic to access

      `consumerName` - the name of the durable subscriber/consumer to use

      `messageSelector` - only messages with properties matching the message selector expression are delivered

      `payloadFactory` - `CustomDatumFactory`/`ORADataFactory` for the java class that maps to the Oracle ADT

      **Important:** `CustomDatum` support will be deprecated in a future release. Use `ORAData` instead.

      `locked` - if `true` then messages are locked as they are browsed (similar to a `SELECT` for `UPDATE`)

      Returns:
      the browser

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a browser is not created due to some error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if an invalid `Topic` is specified.

    <!-- -->

    - #### createTemporaryQueue

          public TemporaryQueue createTemporaryQueue()
                                              throws JMSException

      Description copied from interface: [`QueueSession`](../../javax/jms/QueueSession.md)
      Creates a `TemporaryQueue` object. Its lifetime will be that of the `QueueConnection` unless it is deleted earlier.
      Specified by:
      [`createTemporaryQueue`](../../javax/jms/QueueSession.md) in interface [`QueueSession`](../../javax/jms/QueueSession.md)

      Specified by:
      [`createTemporaryQueue`](../../javax/jms/Session.md) in interface [`Session`](../../javax/jms/Session.md)

      Returns:
      a temporary queue identity

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the session fails to create a temporary queue due to some internal error.

    <!-- -->

    - #### createJMSShardedQueue

          public Destination createJMSShardedQueue(java.lang.String queueName,
                                                   boolean isMultipleConsumer)
                                            throws JMSException

      Create a JMS sharded queue. It also internally creates the related queue objects (table, indexes) based on this name.
      Parameters:
      `queueName` - name of the queue to be created, format is *schema*.*queueName* (where the *schema*. is optional

      `isMultipleConsumer` - flag to indicate whether the queue is a multi-consumer or single-consumer queue

      Returns:
      javax.jms.Destination

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the queue could not be created

    <!-- -->

    - #### createJMSShardedQueue

          public Destination createJMSShardedQueue(java.lang.String queueName,
                                                   boolean isMultipleConsumer,
                                                   java.lang.String storageClause,
                                                   int maxRetries,
                                                   java.lang.String comment)
                                            throws JMSException

      Create a JMS sharded queue. It also internally creates the related queue objects (table, indexes) based on this name.
      Parameters:
      `queueName` - name of the queue to be created, format is *schema*.*queueName* (where the *schema*. is optional

      `isMultipleConsumer` - flag to indicate whether the queue is a multi-consumer or single-consumer queue

      `storageClause` - additional storage clause

      `maxRetries` - retry count before skip the message while dequeue

      `comment` - comment for the queue

      Returns:
      javax.jms.Destination

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the queue could not be created

    <!-- -->

    - #### createTopic

          public Topic createTopic(java.lang.String topicName)
                            throws JMSException

      Description copied from interface: [`Session`](../../javax/jms/Session.md)
      Creates a topic identity given a `Topic` name.
      This facility is provided for the rare cases where clients need to dynamically manipulate topic identity. This allows the creation of a topic identity with a provider-specific name. Clients that depend on this ability are not portable.

      Note that this method is not for creating the physical topic. The physical creation of topics is an administrative task and is not to be initiated by the JMS API. The one exception is the creation of temporary topics, which is accomplished with the `createTemporaryTopic` method.

      Specified by:
      [`createTopic`](../../javax/jms/Session.md) in interface [`Session`](../../javax/jms/Session.md)

      Specified by:
      [`createTopic`](../../javax/jms/TopicSession.md) in interface [`TopicSession`](../../javax/jms/TopicSession.md)

      Parameters:
      `topicName` - the name of this `Topic`

      Returns:
      a `Topic` with the given name

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the session fails to create a topic due to some internal error.

    <!-- -->

    - #### createSubscriber

          public TopicSubscriber createSubscriber(Topic topic)
                                           throws JMSException

      Description copied from interface: [`TopicSession`](../../javax/jms/TopicSession.md)
      Creates a nondurable subscriber to the specified topic.
      A client uses a `TopicSubscriber` object to receive messages that have been published to a topic.

      Regular `TopicSubscriber` objects are not durable. They receive only messages that are published while they are active.

      In some cases, a connection may both publish and subscribe to a topic. The subscriber `NoLocal` attribute allows a subscriber to inhibit the delivery of messages published by its own connection. The default value for this attribute is false.

      Specified by:
      [`createSubscriber`](../../javax/jms/TopicSession.md) in interface [`TopicSession`](../../javax/jms/TopicSession.md)

      Parameters:
      `topic` - the `Topic` to subscribe to

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the session fails to create a subscriber due to some internal error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if an invalid topic is specified.

    <!-- -->

    - #### createSubscriber

          public TopicSubscriber createSubscriber(Topic topic,
                                                  java.lang.String messageSelector,
                                                  boolean noLocal)
                                           throws JMSException

      Description copied from interface: [`TopicSession`](../../javax/jms/TopicSession.md)
      Creates a nondurable subscriber to the specified topic, using a message selector or specifying whether messages published by its own connection should be delivered to it.
      A client uses a `TopicSubscriber` object to receive messages that have been published to a topic.

      Regular `TopicSubscriber` objects are not durable. They receive only messages that are published while they are active.

      Messages filtered out by a subscriber's message selector will never be delivered to the subscriber. From the subscriber's perspective, they do not exist.

      In some cases, a connection may both publish and subscribe to a topic. The subscriber `NoLocal` attribute allows a subscriber to inhibit the delivery of messages published by its own connection. The default value for this attribute is false.

      Specified by:
      [`createSubscriber`](../../javax/jms/TopicSession.md) in interface [`TopicSession`](../../javax/jms/TopicSession.md)

      Parameters:
      `topic` - the `Topic` to subscribe to

      `messageSelector` - only messages with properties matching the message selector expression are delivered. A value of null or an empty string indicates that there is no message selector for the message consumer.

      `noLocal` - if set, inhibits the delivery of messages published by its own connection

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the session fails to create a subscriber due to some internal error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if an invalid topic is specified.

      [`InvalidSelectorException`](../../javax/jms/InvalidSelectorException.md) - if the message selector is invalid.

    <!-- -->

    - #### createDurableSubscriber

          public TopicSubscriber createDurableSubscriber(Topic topic,
                                                         java.lang.String subscriberName)
                                                  throws JMSException

      Creates a durable subscriber to the specified topic.
      This method is used to create browsers for topics that contain JMS payloads (payloads of type `aq$_jms_*`). A client can change an existing durable subscription by creating a durable `TopicSubscriber` with the same name and message selector.

      Specified by:
      [`createDurableSubscriber`](../../javax/jms/Session.md) in interface [`Session`](../../javax/jms/Session.md)

      Specified by:
      [`createDurableSubscriber`](../../javax/jms/TopicSession.md) in interface [`TopicSession`](../../javax/jms/TopicSession.md)

      Parameters:
      `topic` - the topic to subscribe to

      `subscriberName` - the name used to identify this subscription

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a subscriber is not created due to some error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if an invalid `Topic` is specified.

    <!-- -->

    - #### createDurableSubscriber

          public TopicSubscriber createDurableSubscriber(Topic topic,
                                                         java.lang.String subscriberName,
                                                         java.lang.Object payloadFactory)
                                                  throws JMSException

      Creates a durable subscriber to the specified topic.
      This method is used to create subscribers for topics that contain Oracle ADT payloads (instead of the standard JMS defined payloads). A client can change an existing durable subscription by creating a durable `TopicSubscriber` with the same name and message selector.

      Parameters:
      `topic` - the topic to subscribe to

      `subscriberName` - the name used to identify this subscription

      `payloadFactory` - `CustomDatumFactory`/`ORADataFactory` for the java class that maps to the Oracle ADT

      **Important:** `CustomDatum` support will be deprecated in a future release. Use `ORAData` instead.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a subscriber is not created due to some error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if an invalid `Topic` is specified.

    <!-- -->

    - #### createDurableSubscriber

          public TopicSubscriber createDurableSubscriber(Topic topic,
                                                         java.lang.String subscriberName,
                                                         java.lang.String messageSelector,
                                                         boolean noLocal)
                                                  throws JMSException

      Creates a durable subscriber to the specified topic.
      This method is used to create subscribers for topics that contain standard JMS payloads (payloads of type `aq$_jms_*`).

      Specified by:
      [`createDurableSubscriber`](../../javax/jms/Session.md) in interface [`Session`](../../javax/jms/Session.md)

      Specified by:
      [`createDurableSubscriber`](../../javax/jms/TopicSession.md) in interface [`TopicSession`](../../javax/jms/TopicSession.md)

      Parameters:
      `topic` - the non-temporary `Topic` to subscribe to

      `subscriberName` - the name used to identify this subscription

      `messageSelector` - only messages with properties matching the message selector expression are delivered. A value of null or an empty string indicates that there is no message selector for the message consumer.

      `noLocal` - if set, inhibits the delivery of messages published by its own connection

      Returns:
      TopicSubscriber newly created durable subscriber for this topic

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the session fails to create a subscriber due to some internal error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if an invalid topic is specified.

      [`InvalidSelectorException`](../../javax/jms/InvalidSelectorException.md) - if the message selector is invalid.

      See Also:
      [`Session.createDurableSubscriber(Topic,String,String,boolean)`](../../javax/jms/Session.md)

    <!-- -->

    - #### createDurableSubscriber

          public TopicSubscriber createDurableSubscriber(Topic topic,
                                                         java.lang.String subscriberName,
                                                         java.lang.String messageSelector,
                                                         boolean noLocal,
                                                         java.lang.Object payloadFactory)
                                                  throws JMSException

      Creates a durable subscriber to the specified topic.
      This method is used to create browsers for topics that contain Oracle ADT payloads (instead of the standard JMS defined payloads). A client can change an existing durable subscription by creating a durable TopicSubscriber with the same name and message selector. ADT messages do not contain any user defined properties. However, the selector can be used to select messages based on priority or correlation id or attribute values of the message payload The syntax for the selector for queues containing ADT messages is different from the syntax for selectors on queues containing standard JMS payloads (text, stream, object, bytes, map).

      Parameters:
      `topic` - the topic to subscribe to

      `subscriberName` - the name used to identify this subscription

      `messageSelector` - only messages with attributes matching the message selector expression are delivered. This value may be `null`.
      The selector syntax is similar to the AQ rules syntax:

      - Selection based on priority or correlation is specified as in the following example:
        `priority < 3 AND corr_id = 'Fiction'`
      - Selection based on message payload is specified as in the following example:
        `tab.user_data.color = 'GREEN' AND tab.user_data.price < 30000`
        Note that the attribute name must be prefixed with `tab.user_data`.

      `noLocal` - if set, inhibits the delivery of messages published by its own connection

      `payloadFactory` - `CustomDatumFactory`/`ORADataFactory` for the java class that maps to the Oracle ADT

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a session fails to create a subscriber due to some JMS error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if invalid Topic specified.

    <!-- -->

    - #### createDurableSubscriber

          public TopicSubscriber createDurableSubscriber(Topic topic,
                                                         java.lang.String subscriberName,
                                                         java.lang.String messageSelector,
                                                         boolean noLocal,
                                                         java.lang.Object payloadFactory,
                                                         java.lang.String transformation)
                                                  throws JMSException

      Create a durable Subscriber to the specified topic.
      This method is used to create browsers only for topics that contain Oracle ADT payloads (instead of the standard JMS defined payloads) A client can change an existing durable subscription by creating a durable TopicSubscriber with the same name and message selector. ADT messages do not contain any user defined properties. However, the selector can be used to select messages based on priority or correlation id or attribute values of the message payload The syntax for the selector for queues containing ADT messages is different from the syntax for selectors on queues containing standard JMS payloads (text, stream, object, bytes, map).

      Parameters:
      `topic` - the topic to subscribe to

      `subscriberName` - the name used to identify this subscription

      `messageSelector` - only messages with attributes matching the message selector expression are delivered. This value may be `null`.
      The selector syntax is similar to the AQ rules syntax:

      - Selection based on priority or correlation is specified as in the following example:
        `priority < 3 AND corr_id = 'Fiction'`
      - Selection based on message payload is specified as in the following example:
        `tab.user_data.color = 'GREEN' AND tab.user_data.price < 30000`
        Note that the attribute name must be prefixed with `tab.user_data`.

      `noLocal` - if set, inhibits the delivery of messages published by its own connection

      `payloadFactory` - `CustomDatumFactory`/`ORADataFactory` for the java class that maps to the Oracle ADT

      `transformation` - transformation for this subscriber

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a session fails to create a subscriber due to some JMS error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if invalid Topic specified.

    <!-- -->

    - #### createRemoteSubscriber

          public void createRemoteSubscriber(Topic topic,
                                             oracle.jms.AQjmsAgent remoteSubscriber,
                                             java.lang.String messageSelector)
                                      throws JMSException

      Creates a remote topic subscriber. This method is used to create remote subscribers for queues that contain JMS payloads (payloads of type `aq$_jms_*`).
      AQ allows topics to have remote subscribers, i.e. subscribers at other topics in the same or different database. In order to use remote subscribers you must set up propagation from the local topic to the remote subscriber/topic using one of the `createRemoteSubscriber` methods and schedule propagation using the [`AQjmsDestination.schedulePropagation(javax.jms.Session, java.lang.String, java.util.Date, java.lang.Double, java.lang.String, java.lang.Double)`](AQjmsDestination.md) method. Remote subscribers may be a specific consumer at the remote topic or all subscribers at the remote topic
      A remote subscriber is defined using the AQjmsAgent structure. An AQjmsAgent consists of a name and address. The name refers to the consumer_name at the remote topic.
      The address refers to the remote topic - the syntax is (schema).(topic_name)\[@dblink\]

      1. To publish messages to a particular consumer at the remote topic, the subscription_name of the recipient
      at the remote topic must be specified in the name field of AQjmsAgent. The remote topic must be specified in the address field of AQjmsAgent
      2. To publish messages to all subscribers of the remote topic, the name field of AQjmsAgent must be set to null. The remote topic must be specified in the address field of AQjmsAgent

      Parameters:
      `topic` - the local topic to propagate

      `remoteSubscriber` - the remote subscriber/topic
      The following attributes of `remoteSubscriber` define the remote subscriber/topic:

      - `name` - subscription name of the subscriber of the remote topic to which messages published to the local topic should be propagated, or `null` if messages published to the local topic should be propagated to all subscribers of the remote topic
      - `address` - address of the remote topic. The syntax is *schema*.*topicName*@*dblink* (where the *schema*. and @*dblink* portions are optional).

      `messageSelector` - only messages with properties matching the message selector expression are delivered. This value may be `null`. The selector syntax is the same as that for `createDurableSubscriber`.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the remote subscriber is not created due to some error.

    <!-- -->

    - #### createRemoteSubscriber

          public void createRemoteSubscriber(Topic topic,
                                             oracle.jms.AQjmsAgent remoteSubscriber,
                                             java.lang.String messageSelector,
                                             java.lang.Object payloadFactory)
                                      throws JMSException

      Creates a remote topic subscriber. This method is used to create remote subscribers for queues that contain Oracle ADT payloads (instead of the standard JMS defined payloads)
      AQ allows topics to have remote subscribers, i.e. subscribers at other topics in the same or different database. In order to use remote subscribers you must set up propagation from the local topic to the remote subscriber/topic using one of the `createRemoteSubscriber` methods and schedule propagation using the [`AQjmsDestination.schedulePropagation(javax.jms.Session, java.lang.String, java.util.Date, java.lang.Double, java.lang.String, java.lang.Double)`](AQjmsDestination.md) method. Remote subscribers may be a specific consumer at the remote topic or all subscribers at the remote topic
      A remote subscriber is defined using the AQjmsAgent structure. An AQjmsAgent consists of a name and address. The name refers to the consumer_name at the remote topic.
      The address refers to the remote topic - the syntax is (schema).(topic_name)\[@dblink\]

      1. To publish messages to a particular consumer at the remote topic, the subscription_name of the recipient
      at the remote topic must be specified in the name field of AQjmsAgent. The remote topic must be specified in the address field of AQjmsAgent
      2. To publish messages to all subscribers of the remote topic, the name field of AQjmsAgent must be set to null. The remote topic must be specified in the address field of AQjmsAgent

      Parameters:
      `topic` - the local topic to propagate

      `remoteSubscriber` - the remote subscriber/topic
      The following attributes of `remoteSubscriber` define the remote subscriber/topic:

      - `name` - subscription name of the subscriber of the remote topic to which messages published to the local topic should be propagated, or `null` if messages published to the local topic should be propagated to all subscribers of the remote topic
      - `address` - address of the remote topic. The syntax is *schema*.*topicName*@*dblink* (where the *schema*. and @*dblink* portions are optional).

      `messageSelector` - only messages with properties matching the message selector expression are delivered. This value may be `null`. The selector syntax is the same as that for `createDurableSubscriber` for topics with ADT messages.

      `payloadFactory` - `CustomDatumFactory`/`ORADataFactory` for the java class that maps to the Oracle ADT

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the remote subscriber is not created due to some error.

    <!-- -->

    - #### createRemoteSubscriber

          public void createRemoteSubscriber(Topic topic,
                                             oracle.jms.AQjmsAgent remoteSubscriber,
                                             java.lang.String messageSelector,
                                             java.lang.Object payloadFactory,
                                             java.lang.String transformation)
                                      throws JMSException

      Creates a remote topic subscriber. This method is used to create remote subscribers for queues that contain Oracle ADT payloads (instead of the standard JMS defined payloads)
      AQ allows topics to have remote subscribers, i.e. subscribers at other topics in the same or different database. In order to use remote subscribers you must set up propagation from the local topic to the remote subscriber/topic using one of the `createRemoteSubscriber` methods and schedule propagation using the [`AQjmsDestination.schedulePropagation(javax.jms.Session, java.lang.String, java.util.Date, java.lang.Double, java.lang.String, java.lang.Double)`](AQjmsDestination.md) method. Remote subscribers may be a specific consumer at the remote topic or all subscribers at the remote topic
      A remote subscriber is defined using the AQjmsAgent structure. An AQjmsAgent consists of a name and address. The name refers to the consumer_name at the remote topic.
      The address refers to the remote topic - the syntax is (schema).(topic_name)\[@dblink\]

      1. To publish messages to a particular consumer at the remote topic, the subscription_name of the recipient
      at the remote topic must be specified in the name field of AQjmsAgent. The remote topic must be specified in the address field of AQjmsAgent
      2. To publish messages to all subscribers of the remote topic, the name field of AQjmsAgent must be set to null. The remote topic must be specified in the address field of AQjmsAgent

      Parameters:
      `topic` - the local topic to propagate

      `remoteSubscriber` - the remote subscriber/topic
      The following attributes of `remoteSubscriber` define the remote subscriber/topic:

      - `name` - subscription name of the subscriber of the remote topic to which messages published to the local topic should be propagated, or `null` if messages published to the local topic should be propagated to all subscribers of the remote topic
      - `address` - address of the remote topic. The syntax is *schema*.*topicName*@*dblink* (where the *schema*. and @*dblink* portions are optional).

      `payloadFactory` - `CustomDatumFactory`/`ORADataFactory` for the java class that maps to the Oracle ADT

      `transformation` - transformation to be applied

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the remote subscriber is not created due to some error.

    <!-- -->

    - #### createRemoteSubscriber

          public void createRemoteSubscriber(Topic topic,
                                             oracle.jms.AQjmsAgent remoteSubscriber,
                                             java.lang.String messageSelector,
                                             java.lang.Object payloadFactory,
                                             java.lang.String transformation,
                                             boolean queueToQueue)
                                      throws JMSException

      Create a remote subscriber for a topic. This method is used to create browsers for queues that contain Oracle ADT payloads (instead of the standard JMS defined payloads)
      AQ allows topics to have remote subscribers, ie subscribers at other topics in the same or different database. In order to use remote subscribers, you must set up propagation between the two local and remote topic
      Remote subscribers may be a specific consumer at the remote topic or all subscribers at the remote topic
      A remote subscriber is defined using the AQjmsAgent structure. An AQjmsAgent consists of a name and address. The name refers to the consumer_name at the remote topic.
      The address refers to the remote topic - the syntax is (schema).(topic_name)\[@dblink\]

      1. To publish messages to a particular consumer at the remote topic, the subscription_name of the recipient
      at the remote topic must be specified in the name field of AQjmsAgent. The remote topic must be specified in the address field of AQjmsAgent
      2. To publish messages to all subscribers of the remote topic, the name field of AQjmsAgent must be set to null. The remote topic must be specified in the address field of AQjmsAgent

      Parameters:
      `topic` - the local topic to propagate

      `remoteSubscriber` - the remote subscriber/topic
      The following attributes of `remoteSubscriber` define the remote subscriber/topic:

      - `name` - subscription name of the subscriber of the remote topic to which messages published to the local topic should be propagated, or `null` if messages published to the local topic should be propagated to all subscribers of the remote topic
      - `address` - address of the remote topic. The syntax is *schema*.*topicName*@*dblink* (where the *schema*. and @*dblink* portions are optional).

      `payloadFactory` - `CustomDatumFactory`/`ORADataFactory` for the java class that maps to the Oracle ADT

      `transformation` - transformation to be applied

      `queueToQueue` - If `true`, propagation is from queue to queue

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the remote subscriber is not created due to some

    <!-- -->

    - #### createTopicReceiver

          public AQjmsTopicReceiver createTopicReceiver(Topic topic,
                                                        java.lang.String receiverName,
                                                        java.lang.String messageSelector)
                                                 throws JMSException

      Creates a `TopicReceiver` to receive messages from the specified topic. This method is used to create topic receivers for topics that contain JMS payloads (payloads of type `aq$_jms_*`) or payloads of type `Sys.AnyData`
      AQ allows messages to be sent to all subscribers of a topic or to specified recipients. The specified recipients may or may not be subscribers of the topic. If a specified recipient is not a subscriber of the topic, then one of the `createTopicReceiver` methods must be used to create a `TopicReceiver` which can receive the recipient's messages. `TopicReceiver`s only receive messages that are enqueued using a recipient list where recipient `receiverName` is included in the list.

      Parameters:
      `topic` - the topic from which messages are to be received

      `receiverName` - the name of the recipient

      `messageSelector` - only messages with properties matching the message selector expression are delivered
      See `createReceiver` for `messageSelector` limitations.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a topic receiver is not created due to some error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if an invalid `Topic` is specified.

      [`InvalidSelectorException`](../../javax/jms/InvalidSelectorException.md) - if the message selector is invalid.

      See Also:
      `AQjmsSession.createReceiver(javax.jms.Queue,String)`

    <!-- -->

    - #### createTopicReceiver

          public AQjmsTopicReceiver createTopicReceiver(Topic topic,
                                                        java.lang.String receiverName,
                                                        java.lang.String messageSelector,
                                                        java.lang.Object payloadFactory)
                                                 throws JMSException

      Creates a `TopicReceiver` to receive messages from the specified topic. This method is used to create topic receivers for topics that contain Oracle ADT payloads.
      AQ allows messages to be sent to all subscribers of a topic or to specified recipients. The specified recipients may or may not be subscribers of the topic. If a specified recipient is not a subscriber of the topic, then one of the `createTopicReceiver` methods must be used to create a `TopicReceiver` which can receive the recipient's messages. `TopicReceiver`s only receive messages that are enqueued using a recipient list where recipient `receiverName` is included in the list.

      Parameters:
      `topic` - the topic from which messages are to be received

      `receiverName` - the name of the recipient

      `messageSelector` - only messages with properties matching the message selector expression are delivered

      `payloadFactory` - `CustomDatumFactory`/`ORADataFactory` for the java class that maps to the Oracle ADT

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a topic receiver is not created due to some error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if an invalid `Topic` is specified.

      [`InvalidSelectorException`](../../javax/jms/InvalidSelectorException.md) - if the message selector is invalid.

    <!-- -->

    - #### createPublisher

          public TopicPublisher createPublisher(Topic topic)
                                         throws JMSException

      Create a Publisher for the specified topic. A client uses a TopicPublisher for publishing messages on a topic.
      Specified by:
      [`createPublisher`](../../javax/jms/TopicSession.md) in interface [`TopicSession`](../../javax/jms/TopicSession.md)

      Parameters:
      `topic` - the topic to publish to, or `null` if this is an unidentifed producer.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a session fails to create a publisher due to some JMS error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if invalid Topic specified.

    <!-- -->

    - #### createTemporaryTopic

          public TemporaryTopic createTemporaryTopic()
                                              throws JMSException

      Create a temporary topic. It's lifetime will be that of the TopicConnection unless deleted earlier.
      Specified by:
      [`createTemporaryTopic`](../../javax/jms/Session.md) in interface [`Session`](../../javax/jms/Session.md)

      Specified by:
      [`createTemporaryTopic`](../../javax/jms/TopicSession.md) in interface [`TopicSession`](../../javax/jms/TopicSession.md)

      Returns:
      a temporary topic identity

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md)

    <!-- -->

    - #### unsubscribe

          public void unsubscribe(java.lang.String subscriberName)
                           throws JMSException

      Unsubscribe a durable subscription that has been created by a client. This method works only if the subscriber name is a key in the in-memory subscriber-topic map, else the InvalidDestinationException is thrown and clients must use AQjmsSession.unsubscribe(Topic, subscriberName) instead
      Specified by:
      [`unsubscribe`](../../javax/jms/Session.md) in interface [`Session`](../../javax/jms/Session.md)

      Specified by:
      [`unsubscribe`](../../javax/jms/TopicSession.md) in interface [`TopicSession`](../../javax/jms/TopicSession.md)

      Parameters:
      `subscriberName` - the name used to identify this subscription

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - NOT_SUPPORTED

    <!-- -->

    - #### unsubscribe

          public void unsubscribe(Topic topic,
                                  java.lang.String subscriberName)
                           throws JMSException

      Unsubscribe a durable subscription that has been created by a client on the specified topic
      Parameters:
      `topic` - the topic subscribed to

      `subscriberName` - the name used to identify this subscription.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to unsubscribe to durable subscription due to some JMS error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if invalid Topic specified.

    <!-- -->

    - #### unsubscribe

          public void unsubscribe(Topic topic,
                                  oracle.jms.AQjmsAgent remoteSubscriber)
                           throws JMSException

      Unsubscribe a remote durable subscription that has been created by a client on the specified topic
      Parameters:
      `topic` - the topic subscribed to

      `remoteSubscriber` - AQjmsAgent that refers to the remote subcriber. the address field of the AQjmsAgent cannot be `null`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to unsubscribe to durable subscription due to some JMS error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if invalid Topic specified.

    <!-- -->

    - #### run

          public void run()

      Description copied from interface: [`Session`](../../javax/jms/Session.md)
      Optional operation, intended to be used only by Application Servers, not by ordinary JMS clients.
      Specified by:
      `run` in interface `java.lang.Runnable`

      Specified by:
      [`run`](../../javax/jms/Session.md) in interface [`Session`](../../javax/jms/Session.md)

      See Also:
      [`ServerSession`](../../javax/jms/ServerSession.md)

    <!-- -->

    - #### getDBConnection

          public java.sql.Connection getDBConnection()
                                              throws JMSException

      Return the JDBC connection used to connect to the database. This method get the underlying JDBC connection. This connection can be used to perform other SQL operations as part of the same JMS transaction
      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to get the JDBC connection

    <!-- -->

    - #### getTypeMap

          public java.util.Map getTypeMap()
                                   throws JMSException

      Get the JDBC type map
      Returns:
      java.util.Map TypeMap (jdk 1.1)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if type map not found or if the connection is closed

    <!-- -->

    - #### getJmsConnection

          public AQjmsConnection getJmsConnection()
                                           throws JMSException

      This method returns the JMS connection in which this session was created.
      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to get the connection

    <!-- -->

    - #### createQueueTable

          public oracle.AQ.AQQueueTable createQueueTable(java.lang.String owner,
                                                         java.lang.String name,
                                                         oracle.AQ.AQQueueTableProperty property)
                                                  throws JMSException

      Create a Queue Table. A QueueTable holds both queues or topics
      Parameters:
      `owner` - the queue table owner (schema)

      `name` - queue table name

      `property` - queue table properties. If the queuetable will be used to hold queues, then the queuetable must not be multiconsumer enabled (default). If the queue table will be used to hold topics the queuetable must be multiconsumer enabled

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the QueueTable cannot be created

      See Also:
      `AQQueueTableProperty`, `AQQueueTableProperty.setMultiConsumer(boolean)`

    <!-- -->

    - #### createQueueTable

          public oracle.AQ.AQQueueTable createQueueTable(java.lang.String owner,
                                                         java.lang.String name,
                                                         oracle.AQ.AQQueueTableProperty property,
                                                         boolean autonomous)
                                                  throws JMSException

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md)

    <!-- -->

    - #### getQueueTable

          public oracle.AQ.AQQueueTable getQueueTable(java.lang.String owner,
                                                      java.lang.String name)
                                               throws JMSException

      Get a handle to an existing queue-table If owner of queue-table is not the same as the user which opened the connection, the caller must have AQ enqueue/dequeue priveleges on queues/topics in the queue table. Otherwise the queue-table will not be returned
      Parameters:
      `owner` - the owner (schema) of the queue-table

      `name` - queue-table name

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the queue table does not exist or if the user does not have privileges on any queue/topic in the queue-table

    <!-- -->

    - #### createQueue

          public Queue createQueue(oracle.AQ.AQQueueTable queueTable,
                                   java.lang.String queueName,
                                   AQjmsDestinationProperty destinationProperty)
                            throws JMSException

      Create a queue.
      Parameters:
      `queueTable` - Queue-Table in which the queue is to be created. The queue-table must not be multiconsumer enabled

      `queueName` - name of the queue to be created

      `destinationProperty` - Queue properties.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the queue could not be created

      See Also:
      [`AQjmsDestinationProperty`](AQjmsDestinationProperty.md)

    <!-- -->

    - #### createQueue

          public Queue createQueue(oracle.AQ.AQQueueTable queueTable,
                                   java.lang.String queueName,
                                   AQjmsDestinationProperty destinationProperty,
                                   boolean autonomous)
                            throws JMSException

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md)

    <!-- -->

    - #### createTopic

          public Topic createTopic(oracle.AQ.AQQueueTable queueTable,
                                   java.lang.String topicName,
                                   AQjmsDestinationProperty destinationProperty)
                            throws JMSException

      Create a topic
      Parameters:
      `queueTable` - Queue-Table in which the topic is to be created. The queue-table must be multiconsumer enabled

      `topicName` - name of the topic to be created

      `destinationProperty` - Topic properties.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the topic could not be created

      See Also:
      [`AQjmsDestinationProperty`](AQjmsDestinationProperty.md)

    <!-- -->

    - #### createTopic

          public Topic createTopic(oracle.AQ.AQQueueTable queueTable,
                                   java.lang.String topicName,
                                   AQjmsDestinationProperty destinationProperty,
                                   boolean autonomous)
                            throws JMSException

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md)

    <!-- -->

    - #### getQueue

          public Queue getQueue(java.lang.String owner,
                                java.lang.String name)
                         throws JMSException

      Get an existing queue. The Queue is returned only if the user has created the queue or as enqueue/dequeue privileges on the specified queue
      Parameters:
      `owner` - queue owner (schema)

      `name` - queue name

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the queue could not be returned due to some error

    <!-- -->

    - #### getTopic

          public Topic getTopic(java.lang.String owner,
                                java.lang.String name)
                         throws JMSException

      Get an existing topic. The Topic is returned only if the user has created the topic or as enqueue/dequeue privileges on the specified topic
      Parameters:
      `owner` - topic owner (schema)

      `name` - topic name

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the topic could not be returned due to some error

    <!-- -->

    - #### grantSystemPrivilege

          public void grantSystemPrivilege(java.lang.String privilege,
                                           java.lang.String grantee,
                                           boolean adminOption)
                                    throws JMSException

      Grants AQ system privileges to users/roles. Initially only `SYS` and `SYSTEM` can use this procedure successfully. Starting from Oracle Database 12*c* Release 2, `MANAGE_ANY`, `ENQUEUE_ANY`, and `DEQUEUE_ANY` privileges will not allow access to `SYS` owned queues by users other than `SYS`.
      Parameters:
      `privilege` - options are:

      - `"ENQUEUE_ANY"` - users with this privilege are allowed to enqueue messages to any queue/topic in the database
      - `"DEQUEUE_ANY"` - users with this privilege are allowed to dequeue messages from any queue/topic in the database
      - `"MANAGE_ANY"` - users with this privilege are allowed to access and make admin calls on any queue/topic in the database

      `grantee` - specifies the grantee. The grantee can be a user, role or the `"PUBLIC"` role.

      `adminOption` - if this is set to `true`, the grantee is allowed to use this procedure to grant the system privilege to other users or roles

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the system privilege could not be granted.

    <!-- -->

    - #### revokeSystemPrivilege

          public void revokeSystemPrivilege(java.lang.String privilege,
                                            java.lang.String grantee)
                                     throws JMSException

      Revokes AQ system privilege from user/roles. Starting from Oracle Database 12*c* Release 2, `MANAGE_ANY`, `ENQUEUE_ANY`, and `DEQUEUE_ANY` privileges will not allow access to `SYS` owned queues by users other than `SYS`.
      Parameters:
      `privilege` - options are `"ENQUEUE_ANY"`, `"DEQUEUE_ANY"` and `"MANAGE_ANY"`

      `grantee` - specifies the grantee. The grantee can be a user, role or the `"PUBLIC"` role.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the system privilege could not be revoked.

    <!-- -->

    - #### createAQAgent

          public void createAQAgent(java.lang.String agentName)
                             throws JMSException

      Create an AQ agent. This agent can be used to access secure queues. In addition, the agent can be allowed access via protocols - HTTP/SMTP.
      Parameters:
      `agentName` - name of the AQ agent

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - is the agent could not be created. Check linked SQL exception for details

    <!-- -->

    - #### createAQAgent

          public void createAQAgent(java.lang.String agentName,
                                    boolean enableHTTP,
                                    boolean enableSMTP,
                                    java.lang.String certLocation)
                             throws JMSException

      Create an AQ agent. This agent can be used to access secure queues. In addition, the agent can be allowed access via protocols - HTTP/SMTP.
      Parameters:
      `agentName` - name of the AQ agent

      `enableHTTP` - allow this agent to access AQ via HTTP

      `enableSMTP` - allow this agent to access AQ via SMTP

      `certLocation` - certificate location - used authentication when accessing queues via SMTP. Not required for other protocols

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - is the agent could not be created. Check linked SQL exception for details

    <!-- -->

    - #### alterAQAgent

          public void alterAQAgent(java.lang.String agentName,
                                   boolean enableHTTP,
                                   boolean enableSMTP,
                                   java.lang.String certLocation)
                            throws JMSException

      Alter an AQ agent. This agent must have previously been created using createAQAgent This agent can be used to access secure queues. In addition, the agent can be allowed access via protocols - HTTP/SMTP.
      Parameters:
      `agentName` - name of the AQ agent

      `enableHTTP` - allow this agent to access AQ via HTTP

      `enableSMTP` - allow this agent to access AQ via SMTP

      `certLocation` - certificate location - used authentication when accessing queues via SMTP. Not required for other protocols

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - is the agent could not be altered. Check linked SQL exception for details

    <!-- -->

    - #### dropAQAgent

          public void dropAQAgent(java.lang.String agentName)
                           throws JMSException

      Drop AQ agent. This agent must have previously been created using createAQAgent
      Parameters:
      `agentName` - name of the AQ agent

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - is the agent could not be dropped. Check linked SQL exception for details

    <!-- -->

    - #### enableDBAccess

          public void enableDBAccess(java.lang.String agentName,
                                     java.lang.String dbUserName)
                              throws JMSException

      Enable Agent Database Access This method enables the given agent name to have the privileges of the specified database user.
      Parameters:
      `agentName` - name of the AQ agent

      `dbUserName` - name of the database user

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - is the agent/user mapping falied. Check linked SQL exception for details

    <!-- -->

    - #### disableDBAccess

          public void disableDBAccess(java.lang.String agentName,
                                      java.lang.String dbUserName)
                               throws JMSException

      Disable Agent Database Access This method revokes the privileges of the specified database user. from the given agent.
      Parameters:
      `agentName` - name of the AQ agent

      `dbUserName` - name of the database user

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - is the agent/user mapping falied. Check linked SQL exception for details

    <!-- -->

    - #### bindAgent

          public void bindAgent(oracle.jms.AQjmsAgent agent,
                                java.lang.String certificate)
                         throws JMSException

      Add an agent into LDAP server (bind)
      Parameters:
      `agent` - the agent to be binded

      `certificate` - the digital certificate of the agent

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the bind call failed

    <!-- -->

    - #### unbindAgent

          public void unbindAgent(oracle.jms.AQjmsAgent agent)
                           throws JMSException

      remove an agent from LDAP server (unbind)
      Parameters:
      `agent` - -- the agent to be unbinded

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the bind call failed

    <!-- -->

    - #### restartConsumers

          public void restartConsumers()

      Restarts receive on all consumers in cons_list Called when a commit or rollback is detected

    <!-- -->

    - #### getAcknowledgeMode

          public int getAcknowledgeMode()
                                 throws JMSException

      Returns the acknowledgement mode of the session. The acknowledgement mode is set at the time that the session is created. If the session is transacted, the acknowledgement mode is ignored.
      Specified by:
      [`getAcknowledgeMode`](../../javax/jms/Session.md) in interface [`Session`](../../javax/jms/Session.md)

      Returns:
      If the session is not transacted, returns the current acknowledgement mode for the session. If the session is transacted, returns SESSION_TRANSACTED.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to return the acknowledgment mode due to some internal error.

      Since:
      1.1

      See Also:
      [`AQjmsConnection.createSession(boolean, int)`](AQjmsConnection.md)

    <!-- -->

    - #### createProducer

          public MessageProducer createProducer(Destination destination)
                                         throws JMSException

      Creates a `MessageProducer` to send messages to the specified destination.
      A client uses a `MessageProducer` object to send messages to a destination. Since `Queue` and `Topic` both inherit from `Destination`, they can be used in the destination parameter to create a `MessageProducer` object.

      Specified by:
      [`createProducer`](../../javax/jms/Session.md) in interface [`Session`](../../javax/jms/Session.md)

      Parameters:
      `destination` - the `Destination` to send to, or `null` if this is a producer which does not have a specified destination.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the session fails to create a MessageProducer due to some internal error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if an invalid destination is specified.

      Since:
      1.1

    <!-- -->

    - #### createConsumer

          public MessageConsumer createConsumer(Destination destination)
                                         throws JMSException

      Description copied from interface: [`Session`](../../javax/jms/Session.md)
      Creates a `MessageConsumer` for the specified destination. Since `Queue` and `Topic` both inherit from `Destination`, they can be used in the destination parameter to create a `MessageConsumer`.
      Specified by:
      [`createConsumer`](../../javax/jms/Session.md) in interface [`Session`](../../javax/jms/Session.md)

      Parameters:
      `destination` - the `Destination` to access.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the session fails to create a consumer due to some internal error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if an invalid destination is specified.

    <!-- -->

    - #### createConsumer

          public MessageConsumer createConsumer(Destination destination,
                                                java.lang.String messageSelector)
                                         throws JMSException

      Description copied from interface: [`Session`](../../javax/jms/Session.md)
      Creates a `MessageConsumer` for the specified destination, using a message selector. Since `Queue` and `Topic` both inherit from `Destination`, they can be used in the destination parameter to create a `MessageConsumer`.
      A client uses a `MessageConsumer` object to receive messages that have been sent to a destination.

      Specified by:
      [`createConsumer`](../../javax/jms/Session.md) in interface [`Session`](../../javax/jms/Session.md)

      Parameters:
      `destination` - the `Destination` to access

      `messageSelector` - only messages with properties matching the message selector expression are delivered. A value of null or an empty string indicates that there is no message selector for the message consumer.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the session fails to create a MessageConsumer due to some internal error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if an invalid destination is specified.

      [`InvalidSelectorException`](../../javax/jms/InvalidSelectorException.md) - if the message selector is invalid.

    <!-- -->

    - #### createConsumer

          public MessageConsumer createConsumer(Destination destination,
                                                java.lang.String messageSelector,
                                                boolean NoLocal)
                                         throws JMSException

      Description copied from interface: [`Session`](../../javax/jms/Session.md)
      Creates `MessageConsumer` for the specified destination, using a message selector. This method can specify whether messages published by its own connection should be delivered to it, if the destination is a topic.
      Since `Queue` and `Topic` both inherit from `Destination`, they can be used in the destination parameter to create a `MessageConsumer`.

      A client uses a `MessageConsumer` object to receive messages that have been published to a destination.

      In some cases, a connection may both publish and subscribe to a topic. The consumer `NoLocal` attribute allows a consumer to inhibit the delivery of messages published by its own connection. The default value for this attribute is False. The `noLocal` value must be supported by destinations that are topics.

      Specified by:
      [`createConsumer`](../../javax/jms/Session.md) in interface [`Session`](../../javax/jms/Session.md)

      Parameters:
      `destination` - the `Destination` to access

      `messageSelector` - only messages with properties matching the message selector expression are delivered. A value of null or an empty string indicates that there is no message selector for the message consumer.

      `NoLocal` - - if true, and the destination is a topic, inhibits the delivery of messages published by its own connection. The behavior for `NoLocal` is not specified if the destination is a queue.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the session fails to create a MessageConsumer due to some internal error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if an invalid destination is specified.

      [`InvalidSelectorException`](../../javax/jms/InvalidSelectorException.md) - if the message selector is invalid.

    <!-- -->

    - #### createConsumer

          public MessageConsumer createConsumer(Destination destination,
                                                java.lang.String messageSelector,
                                                java.lang.Object payloadFactory,
                                                java.lang.String transformation,
                                                boolean noLocal)
                                         throws JMSException

      A generic routine to create a MessageConsumer used to receive messages from the specified destination. This method is used to create consumers for destinations that contain standard JMS as well as Oracle ADT payloads.
      Parameters:
      `destination` - the destination to access

      `messageSelector` - only messages with properties matching the message selector expression are delivered

      `payloadFactory` - `CustomDatumFactory`/`ORADataFactory` for the java class that maps to the Oracle ADT
      **Important:** `CustomDatum` support will be deprecated in a future release. Use `ORAData` instead.

      `transformation` - transformation if any involved

      `noLocal` - - if `true`, and the destination is a topic, inhibits the delivery of messages published by its own connection. The behavior for `NoLocal` is not specified if the destination is a queue.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a session fails to create a consumer due to some JMS error.

      [`InvalidDestinationException`](../../javax/jms/InvalidDestinationException.md) - if invalid Destination specified.

      [`InvalidSelectorException`](../../javax/jms/InvalidSelectorException.md) - if the message selector is invalid.

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

- [Prev Class](AQjmsQueueSender.md)
- [Next Class](AQjmsStreamMessage.md)

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
