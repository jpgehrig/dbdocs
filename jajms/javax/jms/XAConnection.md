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

- [Prev Class](TransactionRolledBackException.md)
- [Next Class](XAConnectionFactory.md)

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

## Interface XAConnection

- All Superinterfaces:
  [Connection](Connection.md)

  <!-- -->

  All Known Subinterfaces:
  [XAQueueConnection](XAQueueConnection.md), [XATopicConnection](XATopicConnection.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsXAConnection](../../oracle/jms/AQjmsXAConnection.md)

  ------------------------------------------------------------------------



      public interface XAConnection
      extends Connection

  The `XAConnection` interface extends the capability of `Connection` by providing an `XASession` (optional).
  The `XAConnection` interface is optional. JMS providers are not required to support this interface. This interface is for use by JMS providers to support transactional environments. Client programs are strongly encouraged to use the transactional support available in their environment, rather than use these XA interfaces directly.

  See Also:
  [`XAQueueConnection`](XAQueueConnection.md), [`XATopicConnection`](XATopicConnection.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type           | Method and Description                                                                     |
    |-----------------------------|--------------------------------------------------------------------------------------------|
    | [`Session`](Session.md)     | `createSession``(boolean transacted, int acknowledgeMode)`<br>Creates an `Session` object. |
    | [`XASession`](XASession.md) | `createXASession``()`<br>Creates an `XASession` object.                                    |

    - ### Methods inherited from interface javax.jms.[Connection](Connection.md)

      [`close`](Connection.md)`, `[`createConnectionConsumer`](Connection.md)`, `[`createDurableConnectionConsumer`](Connection.md)`, `[`getClientID`](Connection.md)`, `[`getExceptionListener`](Connection.md)`, `[`getMetaData`](Connection.md)`, `[`setClientID`](Connection.md)`, `[`setExceptionListener`](Connection.md)`, `[`start`](Connection.md)`, `[`stop`](Connection.md)

<!-- -->

- - ### Method Detail

    - #### createXASession

          XASession createXASession()
                             throws JMSException

      Creates an `XASession` object.
      Returns:
      a newly created `XASession`

      Throws:
      [`JMSException`](JMSException.md) - if the `XAConnection` object fails to create an `XASession` due to some internal error.

      Since:
      1.1

    <!-- -->

    - #### createSession

          Session createSession(boolean transacted,
                                int acknowledgeMode)
                         throws JMSException

      Creates an `Session` object.
      Specified by:
      [`createSession`](Connection.md) in interface [`Connection`](Connection.md)

      Parameters:
      `transacted` - usage undefined

      `acknowledgeMode` - usage undefined

      Returns:
      a `Session` object

      Throws:
      [`JMSException`](JMSException.md) - if the `XAConnection` object fails to create an `Session` due to some internal error.

      Since:
      1.1

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

- [Prev Class](TransactionRolledBackException.md)
- [Next Class](XAConnectionFactory.md)

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
