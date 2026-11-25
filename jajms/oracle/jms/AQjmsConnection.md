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

- [Prev Class](AQjmsBytesMessage.md)
- [Next Class](AQjmsConnectionFactory.md)

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

## Class AQjmsConnection

- java.lang.Object

- - oracle.jms.AQjmsObject

  - - oracle.jms.AQjmsConnection

<!-- -->

- All Implemented Interfaces:
  [Connection](../../javax/jms/Connection.md), [QueueConnection](../../javax/jms/QueueConnection.md), [TopicConnection](../../javax/jms/TopicConnection.md)

  <!-- -->

  Direct Known Subclasses:
  [AQjmsXAConnection](AQjmsXAConnection.md)

  ------------------------------------------------------------------------



      public class AQjmsConnection
      extends oracle.jms.AQjmsObject
      implements QueueConnection, TopicConnection

  This is an Oracle class which implements `javax.jms.QueueConnection` and `javax.jms.TopicConnection`.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                             | Method and Description                                                                                                                                                                                                                                                                                          |
    |---------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                                        | `close``()`<br>Public for test harness purposes                                                                                                                                                                                                                                                                 |
    | [`ConnectionConsumer`](../../javax/jms/ConnectionConsumer.md) | `createConnectionConsumer``(`[`Destination`](../../javax/jms/Destination.md)` destination, java.lang.String messageSelector, `[`ServerSessionPool`](../../javax/jms/ServerSessionPool.md)` sessionPool, int maxMessages)`<br>Creates a connection consumer for this connection (optional operation).            |
    | [`ConnectionConsumer`](../../javax/jms/ConnectionConsumer.md) | `createConnectionConsumer``(`[`Queue`](../../javax/jms/Queue.md)` queue, java.lang.String messageSelector, `[`ServerSessionPool`](../../javax/jms/ServerSessionPool.md)` sessionPool, int maxMessages)`<br>This method is not supported in the current release.                                                 |
    | [`ConnectionConsumer`](../../javax/jms/ConnectionConsumer.md) | `createConnectionConsumer``(`[`Topic`](../../javax/jms/Topic.md)` topic, java.lang.String messageSelector, `[`ServerSessionPool`](../../javax/jms/ServerSessionPool.md)` sessionPool, int maxMessages)`<br>Creates a connection consumer for this connection.                                                   |
    | [`ConnectionConsumer`](../../javax/jms/ConnectionConsumer.md) | `createDurableConnectionConsumer``(`[`Topic`](../../javax/jms/Topic.md)` topic, java.lang.String subscriptionName, java.lang.String messageSelector, `[`ServerSessionPool`](../../javax/jms/ServerSessionPool.md)` sessionPool, int maxMessages)`<br>Creates a durable connection consumer for this connection. |
    | [`QueueSession`](../../javax/jms/QueueSession.md)             | `createQueueSession``(boolean transacted, int acknowledgeMode)`<br>Creates a queue session.                                                                                                                                                                                                                     |
    | [`Session`](../../javax/jms/Session.md)                       | `createSession``(boolean transacted, int acknowledgeMode)`<br>Creates a `Session` object.                                                                                                                                                                                                                       |
    | [`TopicSession`](../../javax/jms/TopicSession.md)             | `createTopicSession``(boolean transacted, int acknowledgeMode)`<br>Creates a `TopicSession`.                                                                                                                                                                                                                    |
    | `java.lang.String`                                            | `getClientID``()`<br>Gets this connection's client identifier.                                                                                                                                                                                                                                                  |
    | [`Session`](../../javax/jms/Session.md)                       | `getCurrentJmsSession``()`<br>Returns the current open JMS session for this connection.                                                                                                                                                                                                                         |
    | [`ExceptionListener`](../../javax/jms/ExceptionListener.md)   | `getExceptionListener``()`<br>Gets this connection's `ExceptionListener`.                                                                                                                                                                                                                                       |
    | [`ConnectionMetaData`](../../javax/jms/ConnectionMetaData.md) | `getMetaData``()`<br>Gets this connection's meta data.                                                                                                                                                                                                                                                          |
    | `oracle.jdbc.pool.OracleOCIConnectionPool`                    | `getOCIConnectionPool``()`<br>Gets the underlying connection pool for this connection.                                                                                                                                                                                                                          |
    | `void`                                                        | `setClientID``(java.lang.String clientID)`<br>Sets this connection's client identifier.                                                                                                                                                                                                                         |
    | `void`                                                        | `setExceptionListener``(`[`ExceptionListener`](../../javax/jms/ExceptionListener.md)` listener)`<br>Sets this connection's `ExceptionListener`.                                                                                                                                                                 |
    | `void`                                                        | `start``()`<br>Starts (or restarts) a connection's delivery of incoming messages.                                                                                                                                                                                                                               |
    | `void`                                                        | `stop``()`<br>Temporarily stops a connection's delivery of incoming messages.                                                                                                                                                                                                                                   |

    - ### Methods inherited from class oracle.jms.AQjmsObject

      `checkClosed, children, finalize, getID, getParent, isOpen, localClose, preClose`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getClientID

          public java.lang.String getClientID()
                                       throws JMSException

      Gets this connection's client identifier.
      Specified by:
      [`getClientID`](../../javax/jms/Connection.md) in interface [`Connection`](../../javax/jms/Connection.md)

      Returns:
      the unique client identifier

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the client ID for this connection is not returned due to some error.

    <!-- -->

    - #### setClientID

          public void setClientID(java.lang.String clientID)
                           throws JMSException

      Sets this connection's client identifier.
      Specified by:
      [`setClientID`](../../javax/jms/Connection.md) in interface [`Connection`](../../javax/jms/Connection.md)

      Parameters:
      `clientID` - the unique client identifier

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the client ID for this connection is not set due to some error.

      [`IllegalStateException`](../../javax/jms/IllegalStateException.md) - if the JMS client attempts to set a connection's client ID at the wrong time or when it has been administratively configured.

    <!-- -->

    - #### getMetaData

          public ConnectionMetaData getMetaData()
                                         throws JMSException

      Gets this connection's meta data.
      Specified by:
      [`getMetaData`](../../javax/jms/Connection.md) in interface [`Connection`](../../javax/jms/Connection.md)

      Returns:
      the connection meta data

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the connection meta-data is not retrieved due to some error.

      See Also:
      [`ConnectionMetaData`](../../javax/jms/ConnectionMetaData.md)

    <!-- -->

    - #### setExceptionListener

          public void setExceptionListener(ExceptionListener listener)
                                    throws JMSException

      Sets this connection's `ExceptionListener`.
      Specified by:
      [`setExceptionListener`](../../javax/jms/Connection.md) in interface [`Connection`](../../javax/jms/Connection.md)

      Parameters:
      `listener` - the exception listener

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the exception listener is not set due to some error.

    <!-- -->

    - #### getExceptionListener

          public ExceptionListener getExceptionListener()
                                                 throws JMSException

      Gets this connection's `ExceptionListener`.
      Specified by:
      [`getExceptionListener`](../../javax/jms/Connection.md) in interface [`Connection`](../../javax/jms/Connection.md)

      Returns:
      the `ExceptionListener` for this connection, or null. if no `ExceptionListener` is associated with this connection.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the exception listener is not retrieved due to some error.

      See Also:
      [`Connection.setExceptionListener(javax.jms.ExceptionListener)`](../../javax/jms/Connection.md)

    <!-- -->

    - #### start

          public void start()
                     throws JMSException

      Starts (or restarts) a connection's delivery of incoming messages. Restarting begins with the oldest unacknowledged message. Starting a started connection is ignored.
      Specified by:
      [`start`](../../javax/jms/Connection.md) in interface [`Connection`](../../javax/jms/Connection.md)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if message delivery is not started due to some error.

      See Also:
      [`Connection.start()`](../../javax/jms/Connection.md)

    <!-- -->

    - #### stop

          public void stop()
                    throws JMSException

      Temporarily stops a connection's delivery of incoming messages. The connection can be restarted using the `AQjmsConnection.start()` method. When stopped, delivery to all of the connection's message consumers is inhibited: synchronous receives block and messages are not delivered to message listeners. A default timeout of 60 minutes is set to disable the MessageListener(s) set on the message consumer(s), which can by configured by setting the system property oracle.jms.notificationTimeOut in milli seconds, to an appropriate value. If there is a time out while disabling the MessageLister(s), the Connection will be started to keep the system in a good condition. After stop is called there may still be some messages delivered. Stopping a connection has no affect on its ability to send messages. Stopping a stopped connection is ignored.
      Specified by:
      [`stop`](../../javax/jms/Connection.md) in interface [`Connection`](../../javax/jms/Connection.md)

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if message delivery is not stopped due to some error.

      See Also:
      [`Connection.stop()`](../../javax/jms/Connection.md)

    <!-- -->

    - #### close

          public void close()
                     throws JMSException

      Description copied from class: `oracle.jms.AQjmsObject`
      Public for test harness purposes
      Specified by:
      [`close`](../../javax/jms/Connection.md) in interface [`Connection`](../../javax/jms/Connection.md)

      Overrides:
      `close` in class `oracle.jms.AQjmsObject`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to close the connection due to some internal error. For example, a failure to release resources or to close a socket connection can cause this exception to be thrown.

    <!-- -->

    - #### createQueueSession

          public QueueSession createQueueSession(boolean transacted,
                                                 int acknowledgeMode)
                                          throws JMSException

      Creates a queue session.
      Specified by:
      [`createQueueSession`](../../javax/jms/QueueConnection.md) in interface [`QueueConnection`](../../javax/jms/QueueConnection.md)

      Parameters:
      `transacted` - is session transacted?

      `acknowledgeMode` - acknowledgement mode

      Returns:
      a newly created queue session

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if queue session creation fails.

      See Also:
      [`Session.AUTO_ACKNOWLEDGE`](../../javax/jms/Session.md), [`Session.CLIENT_ACKNOWLEDGE`](../../javax/jms/Session.md), [`Session.DUPS_OK_ACKNOWLEDGE`](../../javax/jms/Session.md)

    <!-- -->

    - #### createConnectionConsumer

          public ConnectionConsumer createConnectionConsumer(Queue queue,
                                                             java.lang.String messageSelector,
                                                             ServerSessionPool sessionPool,
                                                             int maxMessages)
                                                      throws JMSException

      This method is not supported in the current release.
      Specified by:
      [`createConnectionConsumer`](../../javax/jms/QueueConnection.md) in interface [`QueueConnection`](../../javax/jms/QueueConnection.md)

      Parameters:
      `queue` - the queue to access

      `messageSelector` - only messages with properties matching the message selector expression are delivered. A value of null or an empty string indicates that there is no message selector for the message consumer.

      `sessionPool` - the server session pool to associate with this connection consumer

      `maxMessages` - the maximum number of messages that can be assigned to a server session at one time

      Returns:
      the connection consumer

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - `NOT_SUPPORTED`

      See Also:
      [`ConnectionConsumer`](../../javax/jms/ConnectionConsumer.md)

    <!-- -->

    - #### createTopicSession

          public TopicSession createTopicSession(boolean transacted,
                                                 int acknowledgeMode)
                                          throws JMSException

      Creates a `TopicSession`.
      Specified by:
      [`createTopicSession`](../../javax/jms/TopicConnection.md) in interface [`TopicConnection`](../../javax/jms/TopicConnection.md)

      Parameters:
      `transacted` - if `true`, the session is transacted.

      `acknowledgeMode` - indicates whether the consumer or the client will acknowledge any messages it receives. This parameter is ignored if the session is transacted.

      Returns:
      a newly created topic session

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if session creation fails due to some error or lack of support for the specific transaction and acknowledgement mode.

      See Also:
      [`Session.AUTO_ACKNOWLEDGE`](../../javax/jms/Session.md), [`Session.CLIENT_ACKNOWLEDGE`](../../javax/jms/Session.md), [`Session.DUPS_OK_ACKNOWLEDGE`](../../javax/jms/Session.md)

    <!-- -->

    - #### createConnectionConsumer

          public ConnectionConsumer createConnectionConsumer(Topic topic,
                                                             java.lang.String messageSelector,
                                                             ServerSessionPool sessionPool,
                                                             int maxMessages)
                                                      throws JMSException

      Creates a connection consumer for this connection. This is an expert facility not used by regular JMS clients. This method is not supported in the current release.
      Specified by:
      [`createConnectionConsumer`](../../javax/jms/TopicConnection.md) in interface [`TopicConnection`](../../javax/jms/TopicConnection.md)

      Parameters:
      `topic` - the topic to access

      `messageSelector` - only messages with properties matching the message selector expression are delivered. A value of null or an empty string indicates that there is no message selector for the message consumer.

      `sessionPool` - the server session pool to associate with this connection consumer

      `maxMessages` - the maximum number of messages that can be assigned to a server session at one time

      Returns:
      the connection consumer

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - `NOT_SUPPORTED`

      See Also:
      [`ConnectionConsumer`](../../javax/jms/ConnectionConsumer.md)

    <!-- -->

    - #### createDurableConnectionConsumer

          public ConnectionConsumer createDurableConnectionConsumer(Topic topic,
                                                                    java.lang.String subscriptionName,
                                                                    java.lang.String messageSelector,
                                                                    ServerSessionPool sessionPool,
                                                                    int maxMessages)
                                                             throws JMSException

      Creates a durable connection consumer for this connection. This is an expert facility not used by regular JMS clients. This method is not supported in the current release.
      Specified by:
      [`createDurableConnectionConsumer`](../../javax/jms/Connection.md) in interface [`Connection`](../../javax/jms/Connection.md)

      Specified by:
      [`createDurableConnectionConsumer`](../../javax/jms/TopicConnection.md) in interface [`TopicConnection`](../../javax/jms/TopicConnection.md)

      Parameters:
      `topic` - topic to access

      `subscriptionName` - durable subscription name

      `messageSelector` - only messages with properties matching the message selector expression are delivered. A value of null or an empty string indicates that there is no message selector for the message consumer.

      `sessionPool` - the server session pool to associate with this durable connection consumer

      `maxMessages` - the maximum number of messages that can be assigned to a server session at one time

      Returns:
      the durable connection consumer

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - `NOT_SUPPORTED`

      See Also:
      [`ConnectionConsumer`](../../javax/jms/ConnectionConsumer.md)

    <!-- -->

    - #### getCurrentJmsSession

          public Session getCurrentJmsSession()

      Returns the current open JMS session for this connection.
      **Important:** This method will be deprecated in a future release

      Returns:
      the current open JMS session, or `null` if no JMS session is currently available

    <!-- -->

    - #### getOCIConnectionPool

          public oracle.jdbc.pool.OracleOCIConnectionPool getOCIConnectionPool()

      Gets the underlying connection pool for this connection.
      Returns:
      the `oracle.jdbc.pool.OracleOCIConnectionPool` pool used to create this connection or `null`

    <!-- -->

    - #### createSession

          public Session createSession(boolean transacted,
                                       int acknowledgeMode)
                                throws JMSException

      Creates a `Session` object.
      Specified by:
      [`createSession`](../../javax/jms/Connection.md) in interface [`Connection`](../../javax/jms/Connection.md)

      Parameters:
      `transacted` - indicates whether the session is transacted

      `acknowledgeMode` - indicates whether the consumer or the client will acknowledge any messages it receives; ignored if the session is transacted. Legal values are `Session.AUTO_ACKNOWLEDGE`, `Session.CLIENT_ACKNOWLEDGE`, and `Session.DUPS_OK_ACKNOWLEDGE`.

      Returns:
      a newly created session

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if session creation fails due to some error or lack of support for the specific transaction and acknowledgement mode.

      Since:
      1.1

      See Also:
      [`Session.AUTO_ACKNOWLEDGE`](../../javax/jms/Session.md), [`Session.CLIENT_ACKNOWLEDGE`](../../javax/jms/Session.md), [`Session.DUPS_OK_ACKNOWLEDGE`](../../javax/jms/Session.md)

    <!-- -->

    - #### createConnectionConsumer

          public ConnectionConsumer createConnectionConsumer(Destination destination,
                                                             java.lang.String messageSelector,
                                                             ServerSessionPool sessionPool,
                                                             int maxMessages)
                                                      throws JMSException

      Creates a connection consumer for this connection (optional operation). This is an expert facility not used by regular JMS clients. This method is not supported in the current release.
      Specified by:
      [`createConnectionConsumer`](../../javax/jms/Connection.md) in interface [`Connection`](../../javax/jms/Connection.md)

      Parameters:
      `destination` - the destination to access

      `messageSelector` - only messages with properties matching the message selector expression are delivered. A value of null or an empty string indicates that there is no message selector for the message consumer.

      `sessionPool` - the server session pool to associate with this connection consumer

      `maxMessages` - the maximum number of messages that can be assigned to a server session at one time

      Returns:
      the connection consumer

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - `NOT_SUPPORTED`

      See Also:
      [`ConnectionConsumer`](../../javax/jms/ConnectionConsumer.md)

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

- [Prev Class](AQjmsBytesMessage.md)
- [Next Class](AQjmsConnectionFactory.md)

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
