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

- [Prev Class](XASession.md)
- [Next Class](XATopicConnectionFactory.md)

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

## Interface XATopicConnection

- All Superinterfaces:
  [Connection](Connection.md), [TopicConnection](TopicConnection.md), [XAConnection](XAConnection.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsXAConnection](../../oracle/jms/AQjmsXAConnection.md)

  ------------------------------------------------------------------------



      public interface XATopicConnection
      extends XAConnection, TopicConnection

  An `XATopicConnection` provides the same create options as `TopicConnection` (optional). The Topic connections created are transactional.
  The `XATopicConnection` interface is optional. JMS providers are not required to support this interface. This interface is for use by JMS providers to support transactional environments. Client programs are strongly encouraged to use the transactional support available in their environment, rather than use these XA interfaces directly.

  See Also:
  [`XAConnection`](XAConnection.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                     | Method and Description                                                                                 |
    |---------------------------------------|--------------------------------------------------------------------------------------------------------|
    | [`TopicSession`](TopicSession.md)     | `createTopicSession``(boolean transacted, int acknowledgeMode)`<br>Creates an `XATopicSession` object. |
    | [`XATopicSession`](XATopicSession.md) | `createXATopicSession``()`<br>Creates an `XATopicSession` object.                                      |

    - ### Methods inherited from interface javax.jms.[XAConnection](XAConnection.md)

      [`createSession`](XAConnection.md)`, `[`createXASession`](XAConnection.md)

    <!-- -->

    - ### Methods inherited from interface javax.jms.[TopicConnection](TopicConnection.md)

      [`createConnectionConsumer`](TopicConnection.md)`, `[`createDurableConnectionConsumer`](TopicConnection.md)

    <!-- -->

    - ### Methods inherited from interface javax.jms.[Connection](Connection.md)

      [`close`](Connection.md)`, `[`createConnectionConsumer`](Connection.md)`, `[`getClientID`](Connection.md)`, `[`getExceptionListener`](Connection.md)`, `[`getMetaData`](Connection.md)`, `[`setClientID`](Connection.md)`, `[`setExceptionListener`](Connection.md)`, `[`start`](Connection.md)`, `[`stop`](Connection.md)

<!-- -->

- - ### Method Detail

    - #### createXATopicSession

          XATopicSession createXATopicSession()
                                       throws JMSException

      Creates an `XATopicSession` object.
      Returns:
      a newly created XA topic session

      Throws:
      [`JMSException`](JMSException.md) - if the `XATopicConnection` object fails to create an XA topic session due to some internal error.

    <!-- -->

    - #### createTopicSession

          TopicSession createTopicSession(boolean transacted,
                                          int acknowledgeMode)
                                   throws JMSException

      Creates an `XATopicSession` object.
      Specified by:
      [`createTopicSession`](TopicConnection.md) in interface [`TopicConnection`](TopicConnection.md)

      Parameters:
      `transacted` - usage undefined

      `acknowledgeMode` - usage undefined

      Returns:
      a newly created XA topic session

      Throws:
      [`JMSException`](JMSException.md) - if the `XATopicConnection` object fails to create an XA topic session due to some internal error.

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

- [Prev Class](XASession.md)
- [Next Class](XATopicConnectionFactory.md)

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
