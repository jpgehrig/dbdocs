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

- [Prev Class](XATopicConnection.md)
- [Next Class](XATopicSession.md)

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

## Interface XATopicConnectionFactory

- All Superinterfaces:
  [ConnectionFactory](ConnectionFactory.md), [TopicConnectionFactory](TopicConnectionFactory.md), [XAConnectionFactory](XAConnectionFactory.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsXATopicConnectionFactory](../../oracle/jms/AQjmsXATopicConnectionFactory.md)

  ------------------------------------------------------------------------



      public interface XATopicConnectionFactory
      extends XAConnectionFactory, TopicConnectionFactory

  An `XATopicConnectionFactory` provides the same create options as a `TopicConnectionFactory` (optional).
  The `XATopicConnectionFactory` interface is optional. JMS providers are not required to support this interface. This interface is for use by JMS providers to support transactional environments. Client programs are strongly encouraged to use the transactional support available in their environment, rather than use these XA interfaces directly.

  See Also:
  [`TopicConnectionFactory`](TopicConnectionFactory.md), [`XAConnectionFactory`](XAConnectionFactory.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                           | Method and Description                                                                                                                                |
    |---------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`XATopicConnection`](XATopicConnection.md) | `createXATopicConnection``()`<br>Creates an XA topic connection with the default user identity.                                                       |
    | [`XATopicConnection`](XATopicConnection.md) | `createXATopicConnection``(java.lang.String userName, java.lang.String password)`<br>Creates an XA topic connection with the specified user identity. |

    - ### Methods inherited from interface javax.jms.[XAConnectionFactory](XAConnectionFactory.md)

      [`createXAConnection`](XAConnectionFactory.md)`, `[`createXAConnection`](XAConnectionFactory.md)

    <!-- -->

    - ### Methods inherited from interface javax.jms.[TopicConnectionFactory](TopicConnectionFactory.md)

      [`createTopicConnection`](TopicConnectionFactory.md)`, `[`createTopicConnection`](TopicConnectionFactory.md)

    <!-- -->

    - ### Methods inherited from interface javax.jms.[ConnectionFactory](ConnectionFactory.md)

      [`createConnection`](ConnectionFactory.md)`, `[`createConnection`](ConnectionFactory.md)

<!-- -->

- - ### Method Detail

    - #### createXATopicConnection

          XATopicConnection createXATopicConnection()
                                             throws JMSException

      Creates an XA topic connection with the default user identity. The connection is created in stopped mode. No messages will be delivered until the `Connection.start` method is explicitly called.
      Returns:
      a newly created XA topic connection

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to create an XA topic connection due to some internal error.

      [`JMSSecurityException`](JMSSecurityException.md) - if client authentication fails due to an invalid user name or password.

    <!-- -->

    - #### createXATopicConnection

          XATopicConnection createXATopicConnection(java.lang.String userName,
                                                    java.lang.String password)
                                             throws JMSException

      Creates an XA topic connection with the specified user identity. The connection is created in stopped mode. No messages will be delivered until the `Connection.start` method is explicitly called.
      Parameters:
      `userName` - the caller's user name

      `password` - the caller's password

      Returns:
      a newly created XA topic connection

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to create an XA topic connection due to some internal error.

      [`JMSSecurityException`](JMSSecurityException.md) - if client authentication fails due to an invalid user name or password.

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

- [Prev Class](XATopicConnection.md)
- [Next Class](XATopicSession.md)

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
