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

- [Prev Class](QueueBrowser.md)
- [Next Class](QueueConnectionFactory.md)

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

## Interface QueueConnection

- All Superinterfaces:
  [Connection](Connection.md)

  <!-- -->

  All Known Subinterfaces:
  [XAQueueConnection](XAQueueConnection.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsConnection](../../oracle/jms/AQjmsConnection.md), [AQjmsXAConnection](../../oracle/jms/AQjmsXAConnection.md)

  ------------------------------------------------------------------------



      public interface QueueConnection
      extends Connection

  A `QueueConnection` object is an active connection to a point-to-point JMS provider. A client uses a `QueueConnection` object to create one or more `QueueSession` objects for producing and consuming messages.
  A `QueueConnection` can be used to create a `QueueSession`, from which specialized queue-related objects can be created. A more general, and recommended, approach is to use the `Connection` object.

  The `QueueConnection` object should be used to support existing code that has already used it.

  A `QueueConnection` cannot be used to create objects specific to the publish/subscribe domain. The `createDurableConnectionConsumer` method inherits from `Connection`, but must throw an `IllegalStateException` if used from `QueueConnection`.

  See Also:
  [`Connection`](Connection.md), [`ConnectionFactory`](ConnectionFactory.md), [`QueueConnectionFactory`](QueueConnectionFactory.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                             | Method and Description                                                                                                                                                                                                                             |
    |-----------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`ConnectionConsumer`](ConnectionConsumer.md) | `createConnectionConsumer``(`[`Queue`](Queue.md)` queue, java.lang.String messageSelector, `[`ServerSessionPool`](ServerSessionPool.md)` sessionPool, int maxMessages)`<br>Creates a connection consumer for this connection (optional operation). |
    | [`QueueSession`](QueueSession.md)             | `createQueueSession``(boolean transacted, int acknowledgeMode)`<br>Creates a `QueueSession` object.                                                                                                                                                |

    - ### Methods inherited from interface javax.jms.[Connection](Connection.md)

      [`close`](Connection.md)`, `[`createConnectionConsumer`](Connection.md)`, `[`createDurableConnectionConsumer`](Connection.md)`, `[`createSession`](Connection.md)`, `[`getClientID`](Connection.md)`, `[`getExceptionListener`](Connection.md)`, `[`getMetaData`](Connection.md)`, `[`setClientID`](Connection.md)`, `[`setExceptionListener`](Connection.md)`, `[`start`](Connection.md)`, `[`stop`](Connection.md)

<!-- -->

- - ### Method Detail

    - #### createQueueSession

          QueueSession createQueueSession(boolean transacted,
                                          int acknowledgeMode)
                                   throws JMSException

      Creates a `QueueSession` object.
      Parameters:
      `transacted` - indicates whether the session is transacted

      `acknowledgeMode` - indicates whether the consumer or the client will acknowledge any messages it receives; ignored if the session is transacted. Legal values are `Session.AUTO_ACKNOWLEDGE`, `Session.CLIENT_ACKNOWLEDGE`, and `Session.DUPS_OK_ACKNOWLEDGE`.

      Returns:
      a newly created queue session

      Throws:
      [`JMSException`](JMSException.md) - if the `QueueConnection` object fails to create a session due to some internal error or lack of support for the specific transaction and acknowledgement mode.

      See Also:
      [`Session.AUTO_ACKNOWLEDGE`](Session.md), [`Session.CLIENT_ACKNOWLEDGE`](Session.md), [`Session.DUPS_OK_ACKNOWLEDGE`](Session.md)

    <!-- -->

    - #### createConnectionConsumer

          ConnectionConsumer createConnectionConsumer(Queue queue,
                                                      java.lang.String messageSelector,
                                                      ServerSessionPool sessionPool,
                                                      int maxMessages)
                                               throws JMSException

      Creates a connection consumer for this connection (optional operation). This is an expert facility not used by regular JMS clients.
      Parameters:
      `queue` - the queue to access

      `messageSelector` - only messages with properties matching the message selector expression are delivered. A value of null or an empty string indicates that there is no message selector for the message consumer.

      `sessionPool` - the server session pool to associate with this connection consumer

      `maxMessages` - the maximum number of messages that can be assigned to a server session at one time

      Returns:
      the connection consumer

      Throws:
      [`JMSException`](JMSException.md) - if the `QueueConnection` object fails to create a connection consumer due to some internal error or invalid arguments for `sessionPool` and `messageSelector`.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if an invalid queue is specified.

      [`InvalidSelectorException`](InvalidSelectorException.md) - if the message selector is invalid.

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

- [Prev Class](QueueBrowser.md)
- [Next Class](QueueConnectionFactory.md)

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
