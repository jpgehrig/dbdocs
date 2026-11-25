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

- [Prev Class](AQjmsXAConnectionFactory.md)
- [Next Class](AQjmsXASession.md)

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

oracle.jms

## Class AQjmsXAQueueConnectionFactory

- java.lang.Object

- - [oracle.jms.AQjmsConnectionFactory](AQjmsConnectionFactory.md)

  - - [oracle.jms.AQjmsQueueConnectionFactory](AQjmsQueueConnectionFactory.md)

    - - oracle.jms.AQjmsXAQueueConnectionFactory

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, [ConnectionFactory](../../javax/jms/ConnectionFactory.md), [QueueConnectionFactory](../../javax/jms/QueueConnectionFactory.md), [XAConnectionFactory](../../javax/jms/XAConnectionFactory.md), [XAQueueConnectionFactory](../../javax/jms/XAQueueConnectionFactory.md), javax.naming.spi.ObjectFactory

  ------------------------------------------------------------------------



      public class AQjmsXAQueueConnectionFactory
      extends AQjmsQueueConnectionFactory
      implements XAQueueConnectionFactory

  Oracle class implementing `javax.jms.XAQueueConnectionFactory`
  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                          |
    |--------------------------------------------------------------------------------------|
    | `AQjmsXAQueueConnectionFactory``()`<br>Constructs a XAQueueConnectionFactory object. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                           | Method and Description                                                                                                                                                                                             |
    |-------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`XAConnection`](../../javax/jms/XAConnection.md)           | `createXAConnection``()`<br>create a XAConnection to the JMS Server hosting this XAQueueConnectionFactory.                                                                                                         |
    | [`XAConnection`](../../javax/jms/XAConnection.md)           | `createXAConnection``(java.lang.String username, java.lang.String password)`<br>create a XAConnection using the given username and password for authentication during creation of the XAConnection.                |
    | [`XAQueueConnection`](../../javax/jms/XAQueueConnection.md) | `createXAQueueConnection``()`<br>create a XAQueueConnection to the JMS Server hosting this XAQueueConnectionFactory                                                                                                |
    | [`XAQueueConnection`](../../javax/jms/XAQueueConnection.md) | `createXAQueueConnection``(java.lang.String username, java.lang.String password)`<br>create a XAQueueConnection using the given username and password for authentication during creation of the XAQueueConnection. |

    - ### Methods inherited from class oracle.jms.[AQjmsQueueConnectionFactory](AQjmsQueueConnectionFactory.md)

      [`createQueueConnection`](AQjmsQueueConnectionFactory.md)`, `[`createQueueConnection`](AQjmsQueueConnectionFactory.md)`, `[`createQueueConnection`](AQjmsQueueConnectionFactory.md)`, `[`createQueueConnection`](AQjmsQueueConnectionFactory.md)

    <!-- -->

    - ### Methods inherited from class oracle.jms.[AQjmsConnectionFactory](AQjmsConnectionFactory.md)

      [`createConnection`](AQjmsConnectionFactory.md)`, `[`createConnection`](AQjmsConnectionFactory.md)`, `[`getDataSource`](AQjmsConnectionFactory.md)`, `[`getJdbcURL`](AQjmsConnectionFactory.md)`, `[`getObjectInstance`](AQjmsConnectionFactory.md)`, `[`getUsername`](AQjmsConnectionFactory.md)`, `[`setDatasource`](AQjmsConnectionFactory.md)`, `[`setJdbcURL`](AQjmsConnectionFactory.md)`, `[`setPassword`](AQjmsConnectionFactory.md)`, `[`setUsername`](AQjmsConnectionFactory.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface javax.jms.[QueueConnectionFactory](../../javax/jms/QueueConnectionFactory.md)

      [`createQueueConnection`](../../javax/jms/QueueConnectionFactory.md)`, `[`createQueueConnection`](../../javax/jms/QueueConnectionFactory.md)

    <!-- -->

    - ### Methods inherited from interface javax.jms.[ConnectionFactory](../../javax/jms/ConnectionFactory.md)

      [`createConnection`](../../javax/jms/ConnectionFactory.md)`, `[`createConnection`](../../javax/jms/ConnectionFactory.md)

<!-- -->

- - ### Constructor Detail

    - #### AQjmsXAQueueConnectionFactory

          public AQjmsXAQueueConnectionFactory()

      Constructs a XAQueueConnectionFactory object. Before using the new factory object to create connections, initializes it by setting its properties.

  <!-- -->

  - ### Method Detail

    - #### createXAQueueConnection

          public XAQueueConnection createXAQueueConnection()
                                                    throws JMSException

      create a XAQueueConnection to the JMS Server hosting this XAQueueConnectionFactory
      Specified by:
      [`createXAQueueConnection`](../../javax/jms/XAQueueConnectionFactory.md) in interface [`XAQueueConnectionFactory`](../../javax/jms/XAQueueConnectionFactory.md)

      Returns:
      a XAQueueConnection

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to get a XAQueueConnection due to some JMS error

    <!-- -->

    - #### createXAQueueConnection

          public XAQueueConnection createXAQueueConnection(java.lang.String username,
                                                           java.lang.String password)
                                                    throws JMSException

      create a XAQueueConnection using the given username and password for authentication during creation of the XAQueueConnection.
      Specified by:
      [`createXAQueueConnection`](../../javax/jms/XAQueueConnectionFactory.md) in interface [`XAQueueConnectionFactory`](../../javax/jms/XAQueueConnectionFactory.md)

      Parameters:
      `username` - name of the user connecting to the DB for Queueing. password password for the creating the connection to server.

      `password` - the caller's password

      Returns:
      a XAQueueConnection

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to get a XAQueueConnection due to some JMS error

    <!-- -->

    - #### createXAConnection

          public XAConnection createXAConnection()
                                          throws JMSException

      create a XAConnection to the JMS Server hosting this XAQueueConnectionFactory.
      Specified by:
      [`createXAConnection`](../../javax/jms/XAConnectionFactory.md) in interface [`XAConnectionFactory`](../../javax/jms/XAConnectionFactory.md)

      Returns:
      a XAConnection

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to get a XAConnection due to some JMS error

    <!-- -->

    - #### createXAConnection

          public XAConnection createXAConnection(java.lang.String username,
                                                 java.lang.String password)
                                          throws JMSException

      create a XAConnection using the given username and password for authentication during creation of the XAConnection.
      Specified by:
      [`createXAConnection`](../../javax/jms/XAConnectionFactory.md) in interface [`XAConnectionFactory`](../../javax/jms/XAConnectionFactory.md)

      Parameters:
      `username` - name of the user connecting to the DB for Queueing. password password for the creating the connection to server.

      `password` - the caller's password

      Returns:
      a XAConnection

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to get a XAConnection due to some JMS error

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

- [Prev Class](AQjmsXAConnectionFactory.md)
- [Next Class](AQjmsXASession.md)

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
