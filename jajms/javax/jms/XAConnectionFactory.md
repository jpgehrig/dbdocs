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

- [Prev Class](XAConnection.md)
- [Next Class](XAQueueConnection.md)

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

## Interface XAConnectionFactory

- All Known Subinterfaces:
  [XAQueueConnectionFactory](XAQueueConnectionFactory.md), [XATopicConnectionFactory](XATopicConnectionFactory.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsXAConnectionFactory](../../oracle/jms/AQjmsXAConnectionFactory.md), [AQjmsXAQueueConnectionFactory](../../oracle/jms/AQjmsXAQueueConnectionFactory.md), [AQjmsXATopicConnectionFactory](../../oracle/jms/AQjmsXATopicConnectionFactory.md)

  ------------------------------------------------------------------------



      public interface XAConnectionFactory

  The `XAConnectionFactory` interface is a base interface for the `XAQueueConnectionFactory` and `XATopicConnectionFactory` interfaces.
  Some application servers provide support for grouping JTS capable resource use into a distributed transaction (optional). To include JMS API transactions in a JTS transaction, an application server requires a JTS aware JMS provider. A JMS provider exposes its JTS support using an `XAConnectionFactory` object, which an application server uses to create `XAConnection` objects.

  `XAConnectionFactory` objects are JMS administered objects, just like `ConnectionFactory` objects. It is expected that application servers will find them using the Java Naming and Directory Interface (JNDI) API.

  The `XAConnectionFactory` interface is optional. JMS providers are not required to support this interface. This interface is for use by JMS providers to support transactional environments. Client programs are strongly encouraged to use the transactional support available in their environment, rather than use these XA interfaces directly.

  See Also:
  [`XAQueueConnectionFactory`](XAQueueConnectionFactory.md), [`XATopicConnectionFactory`](XATopicConnectionFactory.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                 | Method and Description                                                                                                                     |
    |-----------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------|
    | [`XAConnection`](XAConnection.md) | `createXAConnection``()`<br>Creates an `XAConnection` with the default user identity.                                                      |
    | [`XAConnection`](XAConnection.md) | `createXAConnection``(java.lang.String userName, java.lang.String password)`<br>Creates an XA connection with the specified user identity. |

<!-- -->

- - ### Method Detail

    - #### createXAConnection

          XAConnection createXAConnection()
                                   throws JMSException

      Creates an `XAConnection` with the default user identity. The connection is created in stopped mode. No messages will be delivered until the `Connection.start` method is explicitly called.
      Returns:
      a newly created `XAConnection`

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to create an XA connection due to some internal error.

      [`JMSSecurityException`](JMSSecurityException.md) - if client authentication fails due to an invalid user name or password.

      Since:
      1.1

    <!-- -->

    - #### createXAConnection

          XAConnection createXAConnection(java.lang.String userName,
                                          java.lang.String password)
                                   throws JMSException

      Creates an XA connection with the specified user identity. The connection is created in stopped mode. No messages will be delivered until the `Connection.start` method is explicitly called.
      Parameters:
      `userName` - the caller's user name

      `password` - the caller's password

      Returns:
      a newly created XA connection

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to create an XA connection due to some internal error.

      [`JMSSecurityException`](JMSSecurityException.md) - if client authentication fails due to an invalid user name or password.

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

- [Prev Class](XAConnection.md)
- [Next Class](XAQueueConnection.md)

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
