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

- [Prev Class](AQjmsXAQueueConnectionFactory.md)
- [Next Class](AQjmsXATopicConnectionFactory.md)

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

## Class AQjmsXASession

- java.lang.Object

- - oracle.jms.AQjmsObject

  - - [oracle.jms.AQjmsSession](AQjmsSession.md)

    - - oracle.jms.AQjmsXASession

<!-- -->

- All Implemented Interfaces:
  java.lang.Runnable, [QueueSession](../../javax/jms/QueueSession.md), [Session](../../javax/jms/Session.md), [TopicSession](../../javax/jms/TopicSession.md), [XAQueueSession](../../javax/jms/XAQueueSession.md), [XASession](../../javax/jms/XASession.md), [XATopicSession](../../javax/jms/XATopicSession.md)

  ------------------------------------------------------------------------



      public class AQjmsXASession
      extends AQjmsSession
      implements XASession, XAQueueSession, XATopicSession

  This is an Oracle class which implements `javax.jms.XASession`, `javax.jms.XAQueueSession` and `javax.jms.XATopicSession`.

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface javax.jms.[Session](../../javax/jms/Session.md)

      [`AUTO_ACKNOWLEDGE`](../../javax/jms/Session.md)`, `[`CLIENT_ACKNOWLEDGE`](../../javax/jms/Session.md)`, `[`DUPS_OK_ACKNOWLEDGE`](../../javax/jms/Session.md)`, `[`SESSION_TRANSACTED`](../../javax/jms/Session.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                                 | Method and Description                                                                                                |
    |---------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------|
    | `void`                                            | `commit``()`<br>Throws a `TransactionInProgressException`, since it should not be called for an `XASession` object.   |
    | [`QueueSession`](../../javax/jms/QueueSession.md) | `getQueueSession``()`<br>Gets the queue session associated with this `XAQueueSession`.                                |
    | [`Session`](../../javax/jms/Session.md)           | `getSession``()`<br>Gets the session associated with this `XASession`.                                                |
    | [`TopicSession`](../../javax/jms/TopicSession.md) | `getTopicSession``()`<br>Gets the topic session associated with this `XATopicSession`.                                |
    | `javax.transaction.xa.XAResource`                 | `getXAResource``()`<br>Returns an XA resource to the caller.                                                          |
    | `void`                                            | `rollback``()`<br>Throws a `TransactionInProgressException`, since it should not be called for an `XASession` object. |

    - ### Methods inherited from class oracle.jms.[AQjmsSession](AQjmsSession.md)

      [`alterAQAgent`](AQjmsSession.md)`, `[`bindAgent`](AQjmsSession.md)`, `[`close`](AQjmsSession.md)`, `[`createAdtMessage`](AQjmsSession.md)`, `[`createAdtMessage`](AQjmsSession.md)`, `[`createAQAgent`](AQjmsSession.md)`, `[`createAQAgent`](AQjmsSession.md)`, `[`createBrowser`](AQjmsSession.md)`, `[`createBrowser`](AQjmsSession.md)`, `[`createBrowser`](AQjmsSession.md)`, `[`createBrowser`](AQjmsSession.md)`, `[`createBrowser`](AQjmsSession.md)`, `[`createBrowser`](AQjmsSession.md)`, `[`createBrowser`](AQjmsSession.md)`, `[`createBrowser`](AQjmsSession.md)`, `[`createBrowser`](AQjmsSession.md)`, `[`createBrowser`](AQjmsSession.md)`, `[`createBrowser`](AQjmsSession.md)`, `[`createBrowser`](AQjmsSession.md)`, `[`createBrowser`](AQjmsSession.md)`, `[`createBrowser`](AQjmsSession.md)`, `[`createBytesMessage`](AQjmsSession.md)`, `[`createConsumer`](AQjmsSession.md)`, `[`createConsumer`](AQjmsSession.md)`, `[`createConsumer`](AQjmsSession.md)`, `[`createConsumer`](AQjmsSession.md)`, `[`createDurableSubscriber`](AQjmsSession.md)`, `[`createDurableSubscriber`](AQjmsSession.md)`, `[`createDurableSubscriber`](AQjmsSession.md)`, `[`createDurableSubscriber`](AQjmsSession.md)`, `[`createDurableSubscriber`](AQjmsSession.md)`, `[`createJMSShardedQueue`](AQjmsSession.md)`, `[`createJMSShardedQueue`](AQjmsSession.md)`, `[`createMapMessage`](AQjmsSession.md)`, `[`createMessage`](AQjmsSession.md)`, `[`createObjectMessage`](AQjmsSession.md)`, `[`createObjectMessage`](AQjmsSession.md)`, `[`createORAMessage`](AQjmsSession.md)`, `[`createORAMessage`](AQjmsSession.md)`, `[`createORAMessage`](AQjmsSession.md)`, `[`createProducer`](AQjmsSession.md)`, `[`createPublisher`](AQjmsSession.md)`, `[`createQueue`](AQjmsSession.md)`, `[`createQueue`](AQjmsSession.md)`, `[`createQueue`](AQjmsSession.md)`, `[`createQueueTable`](AQjmsSession.md)`, `[`createQueueTable`](AQjmsSession.md)`, `[`createReceiver`](AQjmsSession.md)`, `[`createReceiver`](AQjmsSession.md)`, `[`createReceiver`](AQjmsSession.md)`, `[`createReceiver`](AQjmsSession.md)`, `[`createRemoteSubscriber`](AQjmsSession.md)`, `[`createRemoteSubscriber`](AQjmsSession.md)`, `[`createRemoteSubscriber`](AQjmsSession.md)`, `[`createRemoteSubscriber`](AQjmsSession.md)`, `[`createSender`](AQjmsSession.md)`, `[`createStreamMessage`](AQjmsSession.md)`, `[`createSubscriber`](AQjmsSession.md)`, `[`createSubscriber`](AQjmsSession.md)`, `[`createTemporaryQueue`](AQjmsSession.md)`, `[`createTemporaryTopic`](AQjmsSession.md)`, `[`createTextMessage`](AQjmsSession.md)`, `[`createTextMessage`](AQjmsSession.md)`, `[`createTextMessage`](AQjmsSession.md)`, `[`createTopic`](AQjmsSession.md)`, `[`createTopic`](AQjmsSession.md)`, `[`createTopic`](AQjmsSession.md)`, `[`createTopicReceiver`](AQjmsSession.md)`, `[`createTopicReceiver`](AQjmsSession.md)`, `[`disableDBAccess`](AQjmsSession.md)`, `[`dropAQAgent`](AQjmsSession.md)`, `[`enableDBAccess`](AQjmsSession.md)`, `[`getAckMode`](AQjmsSession.md)`, `[`getAcknowledgeMode`](AQjmsSession.md)`, `[`getDBConnection`](AQjmsSession.md)`, `[`getExceptionListener`](AQjmsSession.md)`, `[`getJmsConnection`](AQjmsSession.md)`, `[`getMessageListener`](AQjmsSession.md)`, `[`getQueue`](AQjmsSession.md)`, `[`getQueueTable`](AQjmsSession.md)`, `[`getTopic`](AQjmsSession.md)`, `[`getTransacted`](AQjmsSession.md)`, `[`getTypeMap`](AQjmsSession.md)`, `[`grantSystemPrivilege`](AQjmsSession.md)`, `[`recover`](AQjmsSession.md)`, `[`restartConsumers`](AQjmsSession.md)`, `[`revokeSystemPrivilege`](AQjmsSession.md)`, `[`run`](AQjmsSession.md)`, `[`setExceptionListener`](AQjmsSession.md)`, `[`setMessageListener`](AQjmsSession.md)`, `[`unbindAgent`](AQjmsSession.md)`, `[`unsubscribe`](AQjmsSession.md)`, `[`unsubscribe`](AQjmsSession.md)`, `[`unsubscribe`](AQjmsSession.md)

    <!-- -->

    - ### Methods inherited from class oracle.jms.AQjmsObject

      `checkClosed, children, finalize, getID, getParent, isOpen, localClose, preClose`

    <!-- -->

    - ### Methods inherited from class java.lang.Object

      `clone, equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

    <!-- -->

    - ### Methods inherited from interface javax.jms.[XASession](../../javax/jms/XASession.md)

      [`getTransacted`](../../javax/jms/XASession.md)

    <!-- -->

    - ### Methods inherited from interface javax.jms.[Session](../../javax/jms/Session.md)

      [`close`](../../javax/jms/Session.md)`, `[`createBrowser`](../../javax/jms/Session.md)`, `[`createBrowser`](../../javax/jms/Session.md)`, `[`createBytesMessage`](../../javax/jms/Session.md)`, `[`createConsumer`](../../javax/jms/Session.md)`, `[`createConsumer`](../../javax/jms/Session.md)`, `[`createConsumer`](../../javax/jms/Session.md)`, `[`createDurableSubscriber`](../../javax/jms/Session.md)`, `[`createDurableSubscriber`](../../javax/jms/Session.md)`, `[`createMapMessage`](../../javax/jms/Session.md)`, `[`createMessage`](../../javax/jms/Session.md)`, `[`createObjectMessage`](../../javax/jms/Session.md)`, `[`createObjectMessage`](../../javax/jms/Session.md)`, `[`createProducer`](../../javax/jms/Session.md)`, `[`createQueue`](../../javax/jms/Session.md)`, `[`createStreamMessage`](../../javax/jms/Session.md)`, `[`createTemporaryQueue`](../../javax/jms/Session.md)`, `[`createTemporaryTopic`](../../javax/jms/Session.md)`, `[`createTextMessage`](../../javax/jms/Session.md)`, `[`createTextMessage`](../../javax/jms/Session.md)`, `[`createTopic`](../../javax/jms/Session.md)`, `[`getAcknowledgeMode`](../../javax/jms/Session.md)`, `[`getMessageListener`](../../javax/jms/Session.md)`, `[`recover`](../../javax/jms/Session.md)`, `[`run`](../../javax/jms/Session.md)`, `[`setMessageListener`](../../javax/jms/Session.md)`, `[`unsubscribe`](../../javax/jms/Session.md)

    <!-- -->

    - ### Methods inherited from interface javax.jms.[QueueSession](../../javax/jms/QueueSession.md)

      [`createTemporaryQueue`](../../javax/jms/QueueSession.md)

    <!-- -->

    - ### Methods inherited from interface javax.jms.[TopicSession](../../javax/jms/TopicSession.md)

      [`createDurableSubscriber`](../../javax/jms/TopicSession.md)`, `[`createTemporaryTopic`](../../javax/jms/TopicSession.md)

<!-- -->

- - ### Method Detail

    - #### getSession

          public Session getSession()
                             throws JMSException

      Gets the session associated with this `XASession`.
      Specified by:
      [`getSession`](../../javax/jms/XASession.md) in interface [`XASession`](../../javax/jms/XASession.md)

      Returns:
      the session object

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if an internal error occurs.

    <!-- -->

    - #### getQueueSession

          public QueueSession getQueueSession()
                                       throws JMSException

      Gets the queue session associated with this `XAQueueSession`.
      Specified by:
      [`getQueueSession`](../../javax/jms/XAQueueSession.md) in interface [`XAQueueSession`](../../javax/jms/XAQueueSession.md)

      Returns:
      the queue session object

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if an internal error occurs.

    <!-- -->

    - #### getTopicSession

          public TopicSession getTopicSession()
                                       throws JMSException

      Gets the topic session associated with this `XATopicSession`.
      Specified by:
      [`getTopicSession`](../../javax/jms/XATopicSession.md) in interface [`XATopicSession`](../../javax/jms/XATopicSession.md)

      Returns:
      the topic session object

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if an internal error occurs.

    <!-- -->

    - #### commit

          public void commit()
                      throws JMSException

      Throws a `TransactionInProgressException`, since it should not be called for an `XASession` object.
      Specified by:
      [`commit`](../../javax/jms/Session.md) in interface [`Session`](../../javax/jms/Session.md)

      Specified by:
      [`commit`](../../javax/jms/XASession.md) in interface [`XASession`](../../javax/jms/XASession.md)

      Overrides:
      [`commit`](AQjmsSession.md) in class [`AQjmsSession`](AQjmsSession.md)

      Throws:
      [`TransactionInProgressException`](../../javax/jms/TransactionInProgressException.md) - if the method is called on an `XASession`.

      [`JMSException`](../../javax/jms/JMSException.md) - if the transaction is not committed due to some error.

    <!-- -->

    - #### rollback

          public void rollback()
                        throws JMSException

      Throws a `TransactionInProgressException`, since it should not be called for an `XASession` object.
      Specified by:
      [`rollback`](../../javax/jms/Session.md) in interface [`Session`](../../javax/jms/Session.md)

      Specified by:
      [`rollback`](../../javax/jms/XASession.md) in interface [`XASession`](../../javax/jms/XASession.md)

      Overrides:
      [`rollback`](AQjmsSession.md) in class [`AQjmsSession`](AQjmsSession.md)

      Throws:
      [`TransactionInProgressException`](../../javax/jms/TransactionInProgressException.md) - if the method is called on an `XASession`.

      [`JMSException`](../../javax/jms/JMSException.md) - if the transaction is not rolled back due to some error.

    <!-- -->

    - #### getXAResource

          public javax.transaction.xa.XAResource getXAResource()

      Returns an XA resource to the caller.
      Specified by:
      [`getXAResource`](../../javax/jms/XASession.md) in interface [`XASession`](../../javax/jms/XASession.md)

      Returns:
      an XA resource to the caller

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

- [Prev Class](AQjmsXAQueueConnectionFactory.md)
- [Next Class](AQjmsXATopicConnectionFactory.md)

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
