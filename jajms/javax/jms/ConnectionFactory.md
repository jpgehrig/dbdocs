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

- [Prev Class](ConnectionConsumer.md)
- [Next Class](ConnectionMetaData.md)

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

## Interface ConnectionFactory

- All Known Subinterfaces:
  [QueueConnectionFactory](QueueConnectionFactory.md), [TopicConnectionFactory](TopicConnectionFactory.md), [XAQueueConnectionFactory](XAQueueConnectionFactory.md), [XATopicConnectionFactory](XATopicConnectionFactory.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsConnectionFactory](../../oracle/jms/AQjmsConnectionFactory.md), [AQjmsQueueConnectionFactory](../../oracle/jms/AQjmsQueueConnectionFactory.md), [AQjmsTopicConnectionFactory](../../oracle/jms/AQjmsTopicConnectionFactory.md), [AQjmsXAConnectionFactory](../../oracle/jms/AQjmsXAConnectionFactory.md), [AQjmsXAQueueConnectionFactory](../../oracle/jms/AQjmsXAQueueConnectionFactory.md), [AQjmsXATopicConnectionFactory](../../oracle/jms/AQjmsXATopicConnectionFactory.md)

  ------------------------------------------------------------------------



      public interface ConnectionFactory

  A `ConnectionFactory` object encapsulates a set of connection configuration parameters that has been defined by an administrator. A client uses it to create a connection with a JMS provider.
  A `ConnectionFactory` object is a JMS administered object and supports concurrent use.

  JMS administered objects are objects containing configuration information that are created by an administrator and later used by JMS clients. They make it practical to administer the JMS API in the enterprise.

  Although the interfaces for administered objects do not explicitly depend on the Java Naming and Directory Interface (JNDI) API, the JMS API establishes the convention that JMS clients find administered objects by looking them up in a JNDI namespace.

  An administrator can place an administered object anywhere in a namespace. The JMS API does not define a naming policy.

  It is expected that JMS providers will provide the tools an administrator needs to create and configure administered objects in a JNDI namespace. JMS provider implementations of administered objects should be both `javax.jndi.Referenceable` and `java.io.Serializable` so that they can be stored in all JNDI naming contexts. In addition, it is recommended that these implementations follow the JavaBeans<sup>TM</sup> design patterns.

  This strategy provides several benefits:

  - It hides provider-specific details from JMS clients.
  - It abstracts administrative information into objects in the Java programming language ("Java objects") that are easily organized and administered from a common management console.
  - Since there will be JNDI providers for all popular naming services, this means that JMS providers can deliver one implementation of administered objects that will run everywhere.

  An administered object should not hold on to any remote resources. Its lookup should not use remote resources other than those used by the JNDI API itself.

  Clients should think of administered objects as local Java objects. Looking them up should not have any hidden side effects or use surprising amounts of local resources.

  See Also:
  [`Connection`](Connection.md), [`QueueConnectionFactory`](QueueConnectionFactory.md), [`TopicConnectionFactory`](TopicConnectionFactory.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type             | Method and Description                                                                                                               |
    |-------------------------------|--------------------------------------------------------------------------------------------------------------------------------------|
    | [`Connection`](Connection.md) | `createConnection``()`<br>Creates a connection with the default user identity.                                                       |
    | [`Connection`](Connection.md) | `createConnection``(java.lang.String userName, java.lang.String password)`<br>Creates a connection with the specified user identity. |

<!-- -->

- - ### Method Detail

    - #### createConnection

          Connection createConnection()
                               throws JMSException

      Creates a connection with the default user identity. The connection is created in stopped mode. No messages will be delivered until the `Connection.start` method is explicitly called.
      Returns:
      a newly created connection

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to create the connection due to some internal error.

      [`JMSSecurityException`](JMSSecurityException.md) - if client authentication fails due to an invalid user name or password.

      Since:
      1.1

    <!-- -->

    - #### createConnection

          Connection createConnection(java.lang.String userName,
                                      java.lang.String password)
                               throws JMSException

      Creates a connection with the specified user identity. The connection is created in stopped mode. No messages will be delivered until the `Connection.start` method is explicitly called.
      Parameters:
      `userName` - the caller's user name

      `password` - the caller's password

      Returns:
      a newly created connection

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to create the connection due to some internal error.

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

- [Prev Class](ConnectionConsumer.md)
- [Next Class](ConnectionMetaData.md)

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
