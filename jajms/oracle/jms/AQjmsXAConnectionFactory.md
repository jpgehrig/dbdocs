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

- [Prev Class](AQjmsXAConnection.md)
- [Next Class](AQjmsXAQueueConnectionFactory.md)

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

## Class AQjmsXAConnectionFactory

- java.lang.Object

- - [oracle.jms.AQjmsConnectionFactory](AQjmsConnectionFactory.md)

  - - oracle.jms.AQjmsXAConnectionFactory

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, [ConnectionFactory](../../javax/jms/ConnectionFactory.md), [XAConnectionFactory](../../javax/jms/XAConnectionFactory.md), javax.naming.spi.ObjectFactory

  ------------------------------------------------------------------------



      public class AQjmsXAConnectionFactory
      extends AQjmsConnectionFactory
      implements XAConnectionFactory

  Oracle class implementing javax.jms.XAConnectionFactory
  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                |
    |----------------------------------------------------------------------------|
    | `AQjmsXAConnectionFactory``()`<br>Constructs a XAConnectionFactory object. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                 | Method and Description                                                                                                                     |
    |---------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------|
    | [`XAConnection`](../../javax/jms/XAConnection.md) | `createXAConnection``()`<br>Creates a `XAConnection` with the default user identity.                                                       |
    | [`XAConnection`](../../javax/jms/XAConnection.md) | `createXAConnection``(java.lang.String userName, java.lang.String password)`<br>Creates a `XAConnection` with the specified user identity. |

    - ### Methods inherited from class oracle.jms.[AQjmsConnectionFactory](AQjmsConnectionFactory.md)

      [`createConnection`](AQjmsConnectionFactory.md)`, `[`createConnection`](AQjmsConnectionFactory.md)`, `[`getDataSource`](AQjmsConnectionFactory.md)`, `[`getJdbcURL`](AQjmsConnectionFactory.md)`, `[`getObjectInstance`](AQjmsConnectionFactory.md)`, `[`getUsername`](AQjmsConnectionFactory.md)`, `[`setDatasource`](AQjmsConnectionFactory.md)`, `[`setJdbcURL`](AQjmsConnectionFactory.md)`, `[`setPassword`](AQjmsConnectionFactory.md)`, `[`setUsername`](AQjmsConnectionFactory.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### AQjmsXAConnectionFactory

          public AQjmsXAConnectionFactory()

      Constructs a XAConnectionFactory object. Before using the new factory object to create connections, initializes it by setting its properties.

  <!-- -->

  - ### Method Detail

    - #### createXAConnection

          public XAConnection createXAConnection()
                                          throws JMSException

      Creates a `XAConnection` with the default user identity. The `XAConnection` is created in stopped mode. No messages will be delivered until the `XAConnection.start` method is explicitly called.
      Specified by:
      [`createXAConnection`](../../javax/jms/XAConnectionFactory.md) in interface [`XAConnectionFactory`](../../javax/jms/XAConnectionFactory.md)

      Returns:
      a newly created `XAConnection`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to create the connection due to some internal error.

      [`JMSSecurityException`](../../javax/jms/JMSSecurityException.md) - if client authentication fails due to an invalid user name or password.

      Since:
      1.1

    <!-- -->

    - #### createXAConnection

          public XAConnection createXAConnection(java.lang.String userName,
                                                 java.lang.String password)
                                          throws JMSException

      Creates a `XAConnection` with the specified user identity. The `XAConnection` is created in stopped mode. No messages will be delivered until the `XAConnection.start` method is explicitly called.
      Specified by:
      [`createXAConnection`](../../javax/jms/XAConnectionFactory.md) in interface [`XAConnectionFactory`](../../javax/jms/XAConnectionFactory.md)

      Parameters:
      `userName` - the caller's user name

      `password` - the caller's password

      Returns:
      a newly created `XAConnection`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the JMS provider fails to create the XAConnection due to some internal error.

      [`JMSSecurityException`](../../javax/jms/JMSSecurityException.md) - if client authentication fails due to an invalid user name or password.

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

- [Prev Class](AQjmsXAConnection.md)
- [Next Class](AQjmsXAQueueConnectionFactory.md)

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
