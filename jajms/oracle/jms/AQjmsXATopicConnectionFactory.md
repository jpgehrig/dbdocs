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

- [Prev Class](AQjmsXASession.md)
- [Next Class](TopicBrowser.md)

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

## Class AQjmsXATopicConnectionFactory

- java.lang.Object

- - [oracle.jms.AQjmsConnectionFactory](AQjmsConnectionFactory.md)

  - - [oracle.jms.AQjmsTopicConnectionFactory](AQjmsTopicConnectionFactory.md)

    - - oracle.jms.AQjmsXATopicConnectionFactory

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable, [ConnectionFactory](../../javax/jms/ConnectionFactory.md), [TopicConnectionFactory](../../javax/jms/TopicConnectionFactory.md), [XAConnectionFactory](../../javax/jms/XAConnectionFactory.md), [XATopicConnectionFactory](../../javax/jms/XATopicConnectionFactory.md), javax.naming.spi.ObjectFactory

  ------------------------------------------------------------------------



      public class AQjmsXATopicConnectionFactory
      extends AQjmsTopicConnectionFactory
      implements XATopicConnectionFactory

  Oracle class implementing `javax.jms.XATopicConnectionFactory`
  See Also:
  [Serialized Form](../../serialized-form.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                          |
    |--------------------------------------------------------------------------------------|
    | `AQjmsXATopicConnectionFactory``()`<br>Constructs a XATopicConnectionFactory object. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                           | Method and Description                                                                                                                                                                                             |
    |-------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | [`XAConnection`](../../javax/jms/XAConnection.md)           | `createXAConnection``()`<br>create a XAConnection to the JMS Server hosting this XATopicConnectionFactory.                                                                                                         |
    | [`XAConnection`](../../javax/jms/XAConnection.md)           | `createXAConnection``(java.lang.String username, java.lang.String password)`<br>create a XAConnection using the given username and password for authentication during creation of the XAConnection.                |
    | [`XATopicConnection`](../../javax/jms/XATopicConnection.md) | `createXATopicConnection``()`<br>create a XATopicConnection to the JMS Server hosting this XATopicConnectionFactory                                                                                                |
    | [`XATopicConnection`](../../javax/jms/XATopicConnection.md) | `createXATopicConnection``(java.lang.String username, java.lang.String password)`<br>create a XATopicConnection using the given username and password for authentication during creation of the XATopicConnection. |

    - ### Methods inherited from class oracle.jms.[AQjmsTopicConnectionFactory](AQjmsTopicConnectionFactory.md)

      [`createTopicConnection`](AQjmsTopicConnectionFactory.md)`, `[`createTopicConnection`](AQjmsTopicConnectionFactory.md)`, `[`createTopicConnection`](AQjmsTopicConnectionFactory.md)`, `[`createTopicConnection`](AQjmsTopicConnectionFactory.md)

    <!-- -->

    - ### Methods inherited from class oracle.jms.[AQjmsConnectionFactory](AQjmsConnectionFactory.md)

      [`createConnection`](AQjmsConnectionFactory.md)`, `[`createConnection`](AQjmsConnectionFactory.md)`, `[`getDataSource`](AQjmsConnectionFactory.md)`, `[`getJdbcURL`](AQjmsConnectionFactory.md)`, `[`getObjectInstance`](AQjmsConnectionFactory.md)`, `[`getUsername`](AQjmsConnectionFactory.md)`, `[`setDatasource`](AQjmsConnectionFactory.md)`, `[`setJdbcURL`](AQjmsConnectionFactory.md)`, `[`setPassword`](AQjmsConnectionFactory.md)`, `[`setUsername`](AQjmsConnectionFactory.md)

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface javax.jms.[TopicConnectionFactory](../../javax/jms/TopicConnectionFactory.md)

      [`createTopicConnection`](../../javax/jms/TopicConnectionFactory.md)`, `[`createTopicConnection`](../../javax/jms/TopicConnectionFactory.md)

    <!-- -->

    - ### Methods inherited from interface javax.jms.[ConnectionFactory](../../javax/jms/ConnectionFactory.md)

      [`createConnection`](../../javax/jms/ConnectionFactory.md)`, `[`createConnection`](../../javax/jms/ConnectionFactory.md)

<!-- -->

- - ### Constructor Detail

    - #### AQjmsXATopicConnectionFactory

          public AQjmsXATopicConnectionFactory()

      Constructs a XATopicConnectionFactory object. Before using the new factory object to create connections, initializes it by setting its properties.

  <!-- -->

  - ### Method Detail

    - #### createXATopicConnection

          public XATopicConnection createXATopicConnection()
                                                    throws JMSException

      create a XATopicConnection to the JMS Server hosting this XATopicConnectionFactory
      Specified by:
      [`createXATopicConnection`](../../javax/jms/XATopicConnectionFactory.md) in interface [`XATopicConnectionFactory`](../../javax/jms/XATopicConnectionFactory.md)

      Returns:
      a XATopicConnection

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to get a XATopicConnection due to some JMS error

    <!-- -->

    - #### createXATopicConnection

          public XATopicConnection createXATopicConnection(java.lang.String username,
                                                           java.lang.String password)
                                                    throws JMSException

      create a XATopicConnection using the given username and password for authentication during creation of the XATopicConnection.
      Specified by:
      [`createXATopicConnection`](../../javax/jms/XATopicConnectionFactory.md) in interface [`XATopicConnectionFactory`](../../javax/jms/XATopicConnectionFactory.md)

      Parameters:
      `username` - name of the user connecting to the DB for Queueing. password password for the user creating the connection.

      `password` - the caller's password

      Returns:
      a XATopicConnection

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to get a XATopicConnection due to some JMS error

    <!-- -->

    - #### createXAConnection

          public XAConnection createXAConnection()
                                          throws JMSException

      create a XAConnection to the JMS Server hosting this XATopicConnectionFactory.
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

- [Prev Class](AQjmsXASession.md)
- [Next Class](TopicBrowser.md)

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
