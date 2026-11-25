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

- [Prev Class](XAConnectionFactory.md)
- [Next Class](XAQueueConnectionFactory.md)

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

## Interface XAQueueConnection

- All Superinterfaces:
  [Connection](Connection.md), [QueueConnection](QueueConnection.md), [XAConnection](XAConnection.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsXAConnection](../../oracle/jms/AQjmsXAConnection.md)

  ------------------------------------------------------------------------



      public interface XAQueueConnection
      extends XAConnection, QueueConnection

  An `XAQueueConnection` provides the same create options as `QueueConnection` (optional). The only difference is that an `XAConnection` is by definition transacted.
  The `XAQueueConnection` interface is optional. JMS providers are not required to support this interface. This interface is for use by JMS providers to support transactional environments. Client programs are strongly encouraged to use the transactional support available in their environment, rather than use these XA interfaces directly.

  See Also:
  [`XAConnection`](XAConnection.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                     | Method and Description                                                                                 |
    |---------------------------------------|--------------------------------------------------------------------------------------------------------|
    | [`QueueSession`](QueueSession.md)     | `createQueueSession``(boolean transacted, int acknowledgeMode)`<br>Creates an `XAQueueSession` object. |
    | [`XAQueueSession`](XAQueueSession.md) | `createXAQueueSession``()`<br>Creates an `XAQueueSession` object.                                      |

    - ### Methods inherited from interface javax.jms.[XAConnection](XAConnection.md)

      [`createSession`](XAConnection.md)`, `[`createXASession`](XAConnection.md)

    <!-- -->

    - ### Methods inherited from interface javax.jms.[QueueConnection](QueueConnection.md)

      [`createConnectionConsumer`](QueueConnection.md)

    <!-- -->

    - ### Methods inherited from interface javax.jms.[Connection](Connection.md)

      [`close`](Connection.md)`, `[`createConnectionConsumer`](Connection.md)`, `[`createDurableConnectionConsumer`](Connection.md)`, `[`getClientID`](Connection.md)`, `[`getExceptionListener`](Connection.md)`, `[`getMetaData`](Connection.md)`, `[`setClientID`](Connection.md)`, `[`setExceptionListener`](Connection.md)`, `[`start`](Connection.md)`, `[`stop`](Connection.md)

<!-- -->

- - ### Method Detail

    - #### createXAQueueSession

          XAQueueSession createXAQueueSession()
                                       throws JMSException

      Creates an `XAQueueSession` object.
      Returns:
      a newly created `XAQueueSession`

      Throws:
      [`JMSException`](JMSException.md) - if the `XAQueueConnection` object fails to create an XA queue session due to some internal error.

    <!-- -->

    - #### createQueueSession

          QueueSession createQueueSession(boolean transacted,
                                          int acknowledgeMode)
                                   throws JMSException

      Creates an `XAQueueSession` object.
      Specified by:
      [`createQueueSession`](QueueConnection.md) in interface [`QueueConnection`](QueueConnection.md)

      Parameters:
      `transacted` - usage undefined

      `acknowledgeMode` - usage undefined

      Returns:
      a newly created `XAQueueSession`

      Throws:
      [`JMSException`](JMSException.md) - if the `XAQueueConnection` object fails to create an XA queue session due to some internal error.

      See Also:
      [`Session.AUTO_ACKNOWLEDGE`](Session.md), [`Session.CLIENT_ACKNOWLEDGE`](Session.md), [`Session.DUPS_OK_ACKNOWLEDGE`](Session.md)

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

- [Prev Class](XAConnectionFactory.md)
- [Next Class](XAQueueConnectionFactory.md)

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
