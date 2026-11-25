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

- [Prev Class](QueueConnection.md)
- [Next Class](QueueReceiver.md)

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

## Interface QueueConnectionFactory

- All Superinterfaces:
  [ConnectionFactory](ConnectionFactory.md)

  <!-- -->

  All Known Subinterfaces:
  [XAQueueConnectionFactory](XAQueueConnectionFactory.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsQueueConnectionFactory](../../oracle/jms/AQjmsQueueConnectionFactory.md), [AQjmsXAQueueConnectionFactory](../../oracle/jms/AQjmsXAQueueConnectionFactory.md)

  ------------------------------------------------------------------------



      public interface QueueConnectionFactory
      extends ConnectionFactory

  A client uses a `QueueConnectionFactory` object to create `QueueConnection` objects with a point-to-point JMS provider.
  `QueueConnectionFactory` can be used to create a `QueueConnection`, from which specialized queue-related objects can be created. A more general, and recommended, approach is to use the `ConnectionFactory` object.

  The `QueueConnectionFactory` object can be used to support existing code that already uses it.

  See Also:
  [`ConnectionFactory`](ConnectionFactory.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                       | Method and Description                                                                                                                          |
    |-----------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`QueueConnection`](QueueConnection.md) | `createQueueConnection``()`<br>Creates a queue connection with the default user identity.                                                       |
    | [`QueueConnection`](QueueConnection.md) | `createQueueConnection``(java.lang.String userName, java.lang.String password)`<br>Creates a queue connection with the specified user identity. |

    - ### Methods inherited from interface javax.jms.[ConnectionFactory](ConnectionFactory.md)

      [`createConnection`](ConnectionFactory.md)`, `[`createConnection`](ConnectionFactory.md)

<!-- -->

- - ### Method Detail

    - #### createQueueConnection

          QueueConnection createQueueConnection()
                                         throws JMSException

      Creates a queue connection with the default user identity. The connection is created in stopped mode. No messages will be delivered until the `Connection.start` method is explicitly called. .
      Returns:
      a newly created queue connection

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to create the queue connection due to some internal error.

      [`JMSSecurityException`](JMSSecurityException.md) - if client authentication fails due to an invalid user name or password.

    <!-- -->

    - #### createQueueConnection

          QueueConnection createQueueConnection(java.lang.String userName,
                                                java.lang.String password)
                                         throws JMSException

      Creates a queue connection with the specified user identity. The connection is created in stopped mode. No messages will be delivered until the `Connection.start` method is explicitly called.
      Parameters:
      `userName` - the caller's user name

      `password` - the caller's password

      Returns:
      a newly created queue connection

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to create the queue connection due to some internal error.

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

- [Prev Class](QueueConnection.md)
- [Next Class](QueueReceiver.md)

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
