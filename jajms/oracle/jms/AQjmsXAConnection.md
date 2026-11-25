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

- [Prev Class](AQjmsTopicSubscriber.md)
- [Next Class](AQjmsXAConnectionFactory.md)

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

## Class AQjmsXAConnection

- java.lang.Object

- - oracle.jms.AQjmsObject

  - - [oracle.jms.AQjmsConnection](AQjmsConnection.md)

    - - oracle.jms.AQjmsXAConnection

<!-- -->

- All Implemented Interfaces:
  [Connection](../../javax/jms/Connection.md), [QueueConnection](../../javax/jms/QueueConnection.md), [TopicConnection](../../javax/jms/TopicConnection.md), [XAConnection](../../javax/jms/XAConnection.md), [XAQueueConnection](../../javax/jms/XAQueueConnection.md), [XATopicConnection](../../javax/jms/XATopicConnection.md)

  ------------------------------------------------------------------------



      public class AQjmsXAConnection
      extends AQjmsConnection
      implements XAConnection, XAQueueConnection, XATopicConnection

  Oracle class implementing javax.jms.XAConnection, javax.jms.XAQueueConnection, javax.jms.XATopicConnection

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                     | Method and Description                                           |
    |-------------------------------------------------------|------------------------------------------------------------------|
    | [`XAQueueSession`](../../javax/jms/XAQueueSession.md) | `createXAQueueSession``()`<br>Creates a `XAQueueSession` object. |
    | [`XASession`](../../javax/jms/XASession.md)           | `createXASession``()`<br>Creates a `XASession` object.           |
    | [`XATopicSession`](../../javax/jms/XATopicSession.md) | `createXATopicSession``()`<br>Creates a `XATopicSession` object. |

    - ### Methods inherited from class oracle.jms.[AQjmsConnection](AQjmsConnection.md)

      [`close`](AQjmsConnection.md)`, `[`createConnectionConsumer`](AQjmsConnection.md)`, `[`createConnectionConsumer`](AQjmsConnection.md)`, `[`createConnectionConsumer`](AQjmsConnection.md)`, `[`createDurableConnectionConsumer`](AQjmsConnection.md)`, `[`createQueueSession`](AQjmsConnection.md)`, `[`createSession`](AQjmsConnection.md)`, `[`createTopicSession`](AQjmsConnection.md)`, `[`getClientID`](AQjmsConnection.md)`, `[`getCurrentJmsSession`](AQjmsConnection.md)`, `[`getExceptionListener`](AQjmsConnection.md)`, `[`getMetaData`](AQjmsConnection.md)`, `[`getOCIConnectionPool`](AQjmsConnection.md)`, `[`setClientID`](AQjmsConnection.md)`, `[`setExceptionListener`](AQjmsConnection.md)`, `[`start`](AQjmsConnection.md)`, `[`stop`](AQjmsConnection.md)

    <!-- -->

    - ### Methods inherited from class oracle.jms.AQjmsObject

      `checkClosed, children, finalize, getID, getParent, isOpen, localClose, preClose`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface javax.jms.[XAQueueConnection](../../javax/jms/XAQueueConnection.md)

      [`createQueueSession`](../../javax/jms/XAQueueConnection.md)

    <!-- -->

    - ### Methods inherited from interface javax.jms.[QueueConnection](../../javax/jms/QueueConnection.md)

      [`createConnectionConsumer`](../../javax/jms/QueueConnection.md)

    <!-- -->

    - ### Methods inherited from interface javax.jms.[XATopicConnection](../../javax/jms/XATopicConnection.md)

      [`createTopicSession`](../../javax/jms/XATopicConnection.md)

    <!-- -->

    - ### Methods inherited from interface javax.jms.[XAConnection](../../javax/jms/XAConnection.md)

      [`createSession`](../../javax/jms/XAConnection.md)

    <!-- -->

    - ### Methods inherited from interface javax.jms.[TopicConnection](../../javax/jms/TopicConnection.md)

      [`createConnectionConsumer`](../../javax/jms/TopicConnection.md)`, `[`createDurableConnectionConsumer`](../../javax/jms/TopicConnection.md)

    <!-- -->

    - ### Methods inherited from interface javax.jms.[Connection](../../javax/jms/Connection.md)

      [`close`](../../javax/jms/Connection.md)`, `[`createConnectionConsumer`](../../javax/jms/Connection.md)`, `[`getClientID`](../../javax/jms/Connection.md)`, `[`getExceptionListener`](../../javax/jms/Connection.md)`, `[`getMetaData`](../../javax/jms/Connection.md)`, `[`setClientID`](../../javax/jms/Connection.md)`, `[`setExceptionListener`](../../javax/jms/Connection.md)`, `[`start`](../../javax/jms/Connection.md)`, `[`stop`](../../javax/jms/Connection.md)

<!-- -->

- - ### Method Detail

    - #### createXASession

          public XASession createXASession()
                                    throws JMSException

      Creates a `XASession` object.
      Specified by:
      [`createXASession`](../../javax/jms/XAConnection.md) in interface [`XAConnection`](../../javax/jms/XAConnection.md)

      Returns:
      a newly created `XASession`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the `XAConnection` object fails to create a `XASession` due to some internal error

      Since:
      1.1

    <!-- -->

    - #### createXAQueueSession

          public XAQueueSession createXAQueueSession()
                                              throws JMSException

      Creates a `XAQueueSession` object.
      Specified by:
      [`createXAQueueSession`](../../javax/jms/XAQueueConnection.md) in interface [`XAQueueConnection`](../../javax/jms/XAQueueConnection.md)

      Returns:
      a newly created `XAQueueSession`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the `XAQueueConnection` object fails to create a `XAQueueSession` due to some internal error

    <!-- -->

    - #### createXATopicSession

          public XATopicSession createXATopicSession()
                                              throws JMSException

      Creates a `XATopicSession` object.
      Specified by:
      [`createXATopicSession`](../../javax/jms/XATopicConnection.md) in interface [`XATopicConnection`](../../javax/jms/XATopicConnection.md)

      Returns:
      a newly created `XATopicSession`

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the `XATopicConnection` object fails to create a `XATopicSession` due to some internal error

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

- [Prev Class](AQjmsTopicSubscriber.md)
- [Next Class](AQjmsXAConnectionFactory.md)

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
