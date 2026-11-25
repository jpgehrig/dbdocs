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

- [Prev Class](AQjmsQueueBrowser.md)
- [Next Class](AQjmsQueueReceiver.md)

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

## Class AQjmsQueueConnectionFactory

- java.lang.Object

- - [oracle.jms.AQjmsConnectionFactory](AQjmsConnectionFactory.md)

  - - oracle.jms.AQjmsQueueConnectionFactory

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, [ConnectionFactory](../../javax/jms/ConnectionFactory.md), [QueueConnectionFactory](../../javax/jms/QueueConnectionFactory.md), javax.naming.spi.ObjectFactory

  <!-- -->

  Direct Known Subclasses:
  [AQjmsXAQueueConnectionFactory](AQjmsXAQueueConnectionFactory.md)

  ------------------------------------------------------------------------



      public class AQjmsQueueConnectionFactory
      extends AQjmsConnectionFactory
      implements QueueConnectionFactory, java.io.Serializable

  This is an Oracle class which implements `javax.jms.QueueConnectionFactory`. A `QueueConnectionFactory` is an encapsulation of JMS servers to which `QueueConnection`s can be created to access message queuing facilities.
  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                      |
    |----------------------------------------------------------------------------------|
    | `AQjmsQueueConnectionFactory``()`<br>Constructs a QueueConnectionFactory object. |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                                | Method and Description                                                                                                                                      |
    |------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`QueueConnection`](../../javax/jms/QueueConnection.md)          | `createQueueConnection``()`<br>Creates a queue connection with the default user identity.                                                                   |
    | `static `[`QueueConnection`](../../javax/jms/QueueConnection.md) | `createQueueConnection``(java.sql.Connection jdbcConnection)`<br>Creates a queue connection using an already open JDBC connection.                          |
    | `static `[`QueueConnection`](../../javax/jms/QueueConnection.md) | `createQueueConnection``(oracle.jdbc.pool.OracleOCIConnectionPool connectionPool)`<br>Creates a queue connection using an already open OCI connection pool. |
    | [`QueueConnection`](../../javax/jms/QueueConnection.md)          | `createQueueConnection``(java.lang.String userName, java.lang.String password)`<br>Creates a queue connection using the specified user identity.            |

    - ### Methods inherited from class oracle.jms.[AQjmsConnectionFactory](AQjmsConnectionFactory.md)

      [`createConnection`](AQjmsConnectionFactory.md)`, `[`createConnection`](AQjmsConnectionFactory.md)`, `[`getDataSource`](AQjmsConnectionFactory.md)`, `[`getJdbcURL`](AQjmsConnectionFactory.md)`, `[`getObjectInstance`](AQjmsConnectionFactory.md)`, `[`getUsername`](AQjmsConnectionFactory.md)`, `[`setDatasource`](AQjmsConnectionFactory.md)`, `[`setJdbcURL`](AQjmsConnectionFactory.md)`, `[`setPassword`](AQjmsConnectionFactory.md)`, `[`setUsername`](AQjmsConnectionFactory.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface javax.jms.[ConnectionFactory](../../javax/jms/ConnectionFactory.md)

      [`createConnection`](../../javax/jms/ConnectionFactory.md)`, `[`createConnection`](../../javax/jms/ConnectionFactory.md)

<!-- -->

- - ### Constructor Detail

    - #### AQjmsQueueConnectionFactory

          public AQjmsQueueConnectionFactory()

      Constructs a QueueConnectionFactory object. Before using the new factory object to create connections, initializes it by setting its properties.

  <!-- -->

  - ### Method Detail

    - #### createQueueConnection

          public QueueConnection createQueueConnection()
                                                throws JMSException

      Creates a queue connection with the default user identity. The connection is created in stopped mode. No messages will be delivered until the `Connection.start` method is explicitly called.
      Specified by:
      [`createQueueConnection`](../../javax/jms/QueueConnectionFactory.md) in interface [`QueueConnectionFactory`](../../javax/jms/QueueConnectionFactory.md)

      Returns:
      a newly created connection

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the queue connection is not created due to some error.

      [`JMSSecurityException`](../../javax/jms/JMSSecurityException.md) - if client authentication fails due to an invalid user name or password.

    <!-- -->

    - #### createQueueConnection

          public QueueConnection createQueueConnection(java.lang.String userName,
                                                       java.lang.String password)
                                                throws JMSException

      Creates a queue connection using the specified user identity. The connection is created in stopped mode. No messages will be delivered until the `Connection.start` method is explicitly called.
      Specified by:
      [`createQueueConnection`](../../javax/jms/QueueConnectionFactory.md) in interface [`QueueConnectionFactory`](../../javax/jms/QueueConnectionFactory.md)

      Parameters:
      `userName` - the caller's user name

      `password` - the caller's password

      Returns:
      a newly created queue connection

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the queue connection is not created due to some error.

      [`JMSSecurityException`](../../javax/jms/JMSSecurityException.md) - if client authentication fails due to an invalid user name or password.

    <!-- -->

    - #### createQueueConnection

          public static QueueConnection createQueueConnection(java.sql.Connection jdbcConnection)
                                                       throws JMSException

      Creates a queue connection using an already open JDBC connection. This creation does NOT result in the creation of another connection to the database. Instead JMS binds the given connection to the database and provides an interface to the queuing mechanism defined by JMS.
      Parameters:
      `jdbcConnection` - a valid open connection to the database.

      Returns:
      a newly created queue connection

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the queue connection is not created due to some error.

    <!-- -->

    - #### createQueueConnection

          public static QueueConnection createQueueConnection(oracle.jdbc.pool.OracleOCIConnectionPool connectionPool)
                                                       throws JMSException

      Creates a queue connection using an already open OCI connection pool. This creation does NOT result in the creation of another connection pool to the database. Instead JMS binds the given OCI connection pool to the database and provides an interface to the queuing mechanism defined by JMS.
      Parameters:
      `connectionPool` - a valid open connection OCI connection pool to the database

      Returns:
      a newly created queue connection

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the queue connection is not created due to some error.

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

- [Prev Class](AQjmsQueueBrowser.md)
- [Next Class](AQjmsQueueReceiver.md)

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
