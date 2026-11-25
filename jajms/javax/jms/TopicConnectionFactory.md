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

- [Prev Class](TopicConnection.md)
- [Next Class](TopicPublisher.md)

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

## Interface TopicConnectionFactory

- All Superinterfaces:
  [ConnectionFactory](ConnectionFactory.md)

  <!-- -->

  All Known Subinterfaces:
  [XATopicConnectionFactory](XATopicConnectionFactory.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsTopicConnectionFactory](../../oracle/jms/AQjmsTopicConnectionFactory.md), [AQjmsXATopicConnectionFactory](../../oracle/jms/AQjmsXATopicConnectionFactory.md)

  ------------------------------------------------------------------------



      public interface TopicConnectionFactory
      extends ConnectionFactory

  A client uses a `TopicConnectionFactory` object to create `TopicConnection` objects with a publish/subscribe JMS provider.
  A `TopicConnectionFactory` can be used to create a `TopicConnection`, from which specialized topic-related objects can be created. A more general, and recommended approach is to use the `ConnectionFactory` object.

  The `TopicConnectionFactory` object should be used to support existing code.

  See Also:
  [`ConnectionFactory`](ConnectionFactory.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                       | Method and Description                                                                                                                          |
    |-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`TopicConnection`](TopicConnection.md) | `createTopicConnection``()`<br>Creates a topic connection with the default user identity.                                                       |
    | [`TopicConnection`](TopicConnection.md) | `createTopicConnection``(java.lang.String userName, java.lang.String password)`<br>Creates a topic connection with the specified user identity. |

    - ### Methods inherited from interface javax.jms.[ConnectionFactory](ConnectionFactory.md)

      [`createConnection`](ConnectionFactory.md)`, `[`createConnection`](ConnectionFactory.md)

<!-- -->

- - ### Method Detail

    - #### createTopicConnection

          TopicConnection createTopicConnection()
                                         throws JMSException

      Creates a topic connection with the default user identity. The connection is created in stopped mode. No messages will be delivered until the `Connection.start` method is explicitly called.
      Returns:
      a newly created topic connection

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to create a topic connection due to some internal error.

      [`JMSSecurityException`](JMSSecurityException.md) - if client authentication fails due to an invalid user name or password.

    <!-- -->

    - #### createTopicConnection

          TopicConnection createTopicConnection(java.lang.String userName,
                                                java.lang.String password)
                                         throws JMSException

      Creates a topic connection with the specified user identity. The connection is created in stopped mode. No messages will be delivered until the `Connection.start` method is explicitly called.
      Parameters:
      `userName` - the caller's user name

      `password` - the caller's password

      Returns:
      a newly created topic connection

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to create a topic connection due to some internal error.

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

- [Prev Class](TopicConnection.md)
- [Next Class](TopicPublisher.md)

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
