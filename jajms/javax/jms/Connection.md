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

- [Prev Class](BytesMessage.md)
- [Next Class](ConnectionConsumer.md)

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

## Interface Connection

- All Known Subinterfaces:
  [QueueConnection](QueueConnection.md), [TopicConnection](TopicConnection.md), [XAConnection](XAConnection.md), [XAQueueConnection](XAQueueConnection.md), [XATopicConnection](XATopicConnection.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsConnection](../../oracle/jms/AQjmsConnection.md), [AQjmsXAConnection](../../oracle/jms/AQjmsXAConnection.md)

  ------------------------------------------------------------------------



      public interface Connection

  A `Connection` object is a client's active connection to its JMS provider. It typically allocates provider resources outside the Java virtual machine (JVM).
  Connections support concurrent use.

  A connection serves several purposes:

  - It encapsulates an open connection with a JMS provider. It typically represents an open TCP/IP socket between a client and the service provider software.
  - Its creation is where client authentication takes place.
  - It can specify a unique client identifier.
  - It provides a `ConnectionMetaData` object.
  - It supports an optional `ExceptionListener` object.

  Because the creation of a connection involves setting up authentication and communication, a connection is a relatively heavyweight object. Most clients will do all their messaging with a single connection. Other more advanced applications may use several connections. The JMS API does not architect a reason for using multiple connections; however, there may be operational reasons for doing so.

  A JMS client typically creates a connection, one or more sessions, and a number of message producers and consumers. When a connection is created, it is in stopped mode. That means that no messages are being delivered.

  It is typical to leave the connection in stopped mode until setup is complete (that is, until all message consumers have been created). At that point, the client calls the connection's `start` method, and messages begin arriving at the connection's consumers. This setup convention minimizes any client confusion that may result from asynchronous message delivery while the client is still in the process of setting itself up.

  A connection can be started immediately, and the setup can be done afterwards. Clients that do this must be prepared to handle asynchronous message delivery while they are still in the process of setting up.

  A message producer can send messages while a connection is stopped.

  See Also:
  [`ConnectionFactory`](ConnectionFactory.md), [`QueueConnection`](QueueConnection.md), [`TopicConnection`](TopicConnection.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                             | Method and Description                                                                                                                                                                                                                                                                              |
    |-----------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                                        | `close``()`<br>Closes the connection.                                                                                                                                                                                                                                                               |
    | [`ConnectionConsumer`](ConnectionConsumer.md) | `createConnectionConsumer``(`[`Destination`](Destination.md)` destination, java.lang.String messageSelector, `[`ServerSessionPool`](ServerSessionPool.md)` sessionPool, int maxMessages)`<br>Creates a connection consumer for this connection (optional operation).                                |
    | [`ConnectionConsumer`](ConnectionConsumer.md) | `createDurableConnectionConsumer``(`[`Topic`](Topic.md)` topic, java.lang.String subscriptionName, java.lang.String messageSelector, `[`ServerSessionPool`](ServerSessionPool.md)` sessionPool, int maxMessages)`<br>Create a durable connection consumer for this connection (optional operation). |
    | [`Session`](Session.md)                       | `createSession``(boolean transacted, int acknowledgeMode)`<br>Creates a `Session` object.                                                                                                                                                                                                           |
    | `java.lang.String`                            | `getClientID``()`<br>Gets the client identifier for this connection.                                                                                                                                                                                                                                |
    | [`ExceptionListener`](ExceptionListener.md)   | `getExceptionListener``()`<br>Gets the `ExceptionListener` object for this connection.                                                                                                                                                                                                              |
    | [`ConnectionMetaData`](ConnectionMetaData.md) | `getMetaData``()`<br>Gets the metadata for this connection.                                                                                                                                                                                                                                         |
    | `void`                                        | `setClientID``(java.lang.String clientID)`<br>Sets the client identifier for this connection.                                                                                                                                                                                                       |
    | `void`                                        | `setExceptionListener``(`[`ExceptionListener`](ExceptionListener.md)` listener)`<br>Sets an exception listener for this connection.                                                                                                                                                                 |
    | `void`                                        | `start``()`<br>Starts (or restarts) a connection's delivery of incoming messages.                                                                                                                                                                                                                   |
    | `void`                                        | `stop``()`<br>Temporarily stops a connection's delivery of incoming messages.                                                                                                                                                                                                                       |

<!-- -->

- - ### Method Detail

    - #### createSession

          Session createSession(boolean transacted,
                                int acknowledgeMode)
                         throws JMSException

      Creates a `Session` object.
      Parameters:
      `transacted` - indicates whether the session is transacted

      `acknowledgeMode` - indicates whether the consumer or the client will acknowledge any messages it receives; ignored if the session is transacted. Legal values are `Session.AUTO_ACKNOWLEDGE`, `Session.CLIENT_ACKNOWLEDGE`, and `Session.DUPS_OK_ACKNOWLEDGE`.

      Returns:
      a newly created session

      Throws:
      [`JMSException`](JMSException.md) - if the `Connection` object fails to create a session due to some internal error or lack of support for the specific transaction and acknowledgement mode.

      Since:
      1.1

      See Also:
      [`Session.AUTO_ACKNOWLEDGE`](Session.md), [`Session.CLIENT_ACKNOWLEDGE`](Session.md), [`Session.DUPS_OK_ACKNOWLEDGE`](Session.md)

    <!-- -->

    - #### getClientID

          java.lang.String getClientID()
                                throws JMSException

      Gets the client identifier for this connection.
      This value is specific to the JMS provider. It is either preconfigured by an administrator in a `ConnectionFactory` object or assigned dynamically by the application by calling the `setClientID` method.

      Returns:
      the unique client identifier

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to return the client ID for this connection due to some internal error.

    <!-- -->

    - #### setClientID

          void setClientID(java.lang.String clientID)
                    throws JMSException

      Sets the client identifier for this connection.
      The preferred way to assign a JMS client's client identifier is for it to be configured in a client-specific `ConnectionFactory` object and transparently assigned to the `Connection` object it creates.

      Alternatively, a client can set a connection's client identifier using a provider-specific value. The facility to set a connection's client identifier explicitly is not a mechanism for overriding the identifier that has been administratively configured. It is provided for the case where no administratively specified identifier exists. If one does exist, an attempt to change it by setting it must throw an `IllegalStateException`. If a client sets the client identifier explicitly, it must do so immediately after it creates the connection and before any other action on the connection is taken. After this point, setting the client identifier is a programming error that should throw an `IllegalStateException`.

      The purpose of the client identifier is to associate a connection and its objects with a state maintained on behalf of the client by a provider. The only such state identified by the JMS API is that required to support durable subscriptions.

      If another connection with the same `clientID` is already running when this method is called, the JMS provider should detect the duplicate ID and throw an `InvalidClientIDException`.

      Parameters:
      `clientID` - the unique client identifier

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to set the client ID for this connection due to some internal error.

      [`InvalidClientIDException`](InvalidClientIDException.md) - if the JMS client specifies an invalid or duplicate client ID.

      [`IllegalStateException`](IllegalStateException.md) - if the JMS client attempts to set a connection's client ID at the wrong time or when it has been administratively configured.

    <!-- -->

    - #### getMetaData

          ConnectionMetaData getMetaData()
                                  throws JMSException

      Gets the metadata for this connection.
      Returns:
      the connection metadata

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the connection metadata for this connection.

      See Also:
      [`ConnectionMetaData`](ConnectionMetaData.md)

    <!-- -->

    - #### getExceptionListener

          ExceptionListener getExceptionListener()
                                          throws JMSException

      Gets the `ExceptionListener` object for this connection. Not every `Connection` has an `ExceptionListener` associated with it.
      Returns:
      the `ExceptionListener` for this connection, or null. if no `ExceptionListener` is associated with this connection.

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the `ExceptionListener` for this connection.

      See Also:
      `Connection.setExceptionListener(javax.jms.ExceptionListener)`

    <!-- -->

    - #### setExceptionListener

          void setExceptionListener(ExceptionListener listener)
                             throws JMSException

      Sets an exception listener for this connection.
      If a JMS provider detects a serious problem with a connection, it informs the connection's `ExceptionListener`, if one has been registered. It does this by calling the listener's `onException` method, passing it a `JMSException` object describing the problem.

      An exception listener allows a client to be notified of a problem asynchronously. Some connections only consume messages, so they would have no other way to learn their connection has failed.

      A connection serializes execution of its `ExceptionListener`.

      A JMS provider should attempt to resolve connection problems itself before it notifies the client of them.

      Parameters:
      `listener` - the exception listener

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to set the exception listener for this connection.

    <!-- -->

    - #### start

          void start()
              throws JMSException

      Starts (or restarts) a connection's delivery of incoming messages. A call to `start` on a connection that has already been started is ignored.
      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to start message delivery due to some internal error.

      See Also:
      `Connection.stop()`

    <!-- -->

    - #### stop

          void stop()
             throws JMSException

      Temporarily stops a connection's delivery of incoming messages. Delivery can be restarted using the connection's `start` method. When the connection is stopped, delivery to all the connection's message consumers is inhibited: synchronous receives block, and messages are not delivered to message listeners.
      This call blocks until receives and/or message listeners in progress have completed.

      Stopping a connection has no effect on its ability to send messages. A call to `stop` on a connection that has already been stopped is ignored.

      A call to `stop` must not return until delivery of messages has paused. This means that a client can rely on the fact that none of its message listeners will be called and that all threads of control waiting for `receive` calls to return will not return with a message until the connection is restarted. The receive timers for a stopped connection continue to advance, so receives may time out while the connection is stopped.

      If message listeners are running when `stop` is invoked, the `stop` call must wait until all of them have returned before it may return. While these message listeners are completing, they must have the full services of the connection available to them.

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to stop message delivery due to some internal error.

      See Also:
      `Connection.start()`

    <!-- -->

    - #### close

          void close()
              throws JMSException

      Closes the connection.
      Since a provider typically allocates significant resources outside the JVM on behalf of a connection, clients should close these resources when they are not needed. Relying on garbage collection to eventually reclaim these resources may not be timely enough.

      There is no need to close the sessions, producers, and consumers of a closed connection.

      Closing a connection causes all temporary destinations to be deleted.

      When this method is invoked, it should not return until message processing has been shut down in an orderly fashion. This means that all message listeners that may have been running have returned, and that all pending receives have returned. A close terminates all pending message receives on the connection's sessions' consumers. The receives may return with a message or with null, depending on whether there was a message available at the time of the close. If one or more of the connection's sessions' message listeners is processing a message at the time when connection `close` is invoked, all the facilities of the connection and its sessions must remain available to those listeners until they return control to the JMS provider.

      Closing a connection causes any of its sessions' transactions in progress to be rolled back. In the case where a session's work is coordinated by an external transaction manager, a session's `commit` and `rollback` methods are not used and the result of a closed session's work is determined later by the transaction manager. Closing a connection does NOT force an acknowledgment of client-acknowledged sessions.

      Invoking the `acknowledge` method of a received message from a closed connection's session must throw an `IllegalStateException`. Closing a closed connection must NOT throw an exception.

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to close the connection due to some internal error. For example, a failure to release resources or to close a socket connection can cause this exception to be thrown.

    <!-- -->

    - #### createConnectionConsumer

          ConnectionConsumer createConnectionConsumer(Destination destination,
                                                      java.lang.String messageSelector,
                                                      ServerSessionPool sessionPool,
                                                      int maxMessages)
                                               throws JMSException

      Creates a connection consumer for this connection (optional operation). This is an expert facility not used by regular JMS clients.
      Parameters:
      `destination` - the destination to access

      `messageSelector` - only messages with properties matching the message selector expression are delivered. A value of null or an empty string indicates that there is no message selector for the message consumer.

      `sessionPool` - the server session pool to associate with this connection consumer

      `maxMessages` - the maximum number of messages that can be assigned to a server session at one time

      Returns:
      the connection consumer

      Throws:
      [`JMSException`](JMSException.md) - if the `Connection` object fails to create a connection consumer due to some internal error or invalid arguments for `sessionPool` and `messageSelector`.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if an invalid destination is specified.

      [`InvalidSelectorException`](InvalidSelectorException.md) - if the message selector is invalid.

      Since:
      1.1

      See Also:
      [`ConnectionConsumer`](ConnectionConsumer.md)

    <!-- -->

    - #### createDurableConnectionConsumer

          ConnectionConsumer createDurableConnectionConsumer(Topic topic,
                                                             java.lang.String subscriptionName,
                                                             java.lang.String messageSelector,
                                                             ServerSessionPool sessionPool,
                                                             int maxMessages)
                                                      throws JMSException

      Create a durable connection consumer for this connection (optional operation). This is an expert facility not used by regular JMS clients.
      Parameters:
      `topic` - topic to access

      `subscriptionName` - durable subscription name

      `messageSelector` - only messages with properties matching the message selector expression are delivered. A value of null or an empty string indicates that there is no message selector for the message consumer.

      `sessionPool` - the server session pool to associate with this durable connection consumer

      `maxMessages` - the maximum number of messages that can be assigned to a server session at one time

      Returns:
      the durable connection consumer

      Throws:
      [`JMSException`](JMSException.md) - if the `Connection` object fails to create a connection consumer due to some internal error or invalid arguments for `sessionPool` and `messageSelector`.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if an invalid destination is specified.

      [`InvalidSelectorException`](InvalidSelectorException.md) - if the message selector is invalid.

      Since:
      1.1

      See Also:
      [`ConnectionConsumer`](ConnectionConsumer.md)

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

- [Prev Class](BytesMessage.md)
- [Next Class](ConnectionConsumer.md)

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
