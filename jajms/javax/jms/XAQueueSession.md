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

- [Prev Class](XAQueueConnectionFactory.md)
- [Next Class](XASession.md)

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

## Interface XAQueueSession

- All Superinterfaces:
  java.lang.Runnable, [Session](Session.md), [XASession](XASession.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsXASession](../../oracle/jms/AQjmsXASession.md)

  ------------------------------------------------------------------------



      public interface XAQueueSession
      extends XASession

  An `XAQueueSession` provides a regular `QueueSession`, which can be used to create `QueueReceiver`, `QueueSender`, and `QueueBrowser` objects (optional).
  The `XAQueueSession` interface is optional. JMS providers are not required to support this interface. This interface is for use by JMS providers to support transactional environments. Client programs are strongly encouraged to use the transactional support available in their environment, rather than use these XA interfaces directly.

  See Also:
  [`XASession`](XASession.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface javax.jms.[Session](Session.md)

      [`AUTO_ACKNOWLEDGE`](Session.md)`, `[`CLIENT_ACKNOWLEDGE`](Session.md)`, `[`DUPS_OK_ACKNOWLEDGE`](Session.md)`, `[`SESSION_TRANSACTED`](Session.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                 | Method and Description                                                                 |
    |-----------------------------------|----------------------------------------------------------------------------------------|
    | [`QueueSession`](QueueSession.md) | `getQueueSession``()`<br>Gets the queue session associated with this `XAQueueSession`. |

    - ### Methods inherited from interface javax.jms.[XASession](XASession.md)

      [`commit`](XASession.md)`, `[`getSession`](XASession.md)`, `[`getTransacted`](XASession.md)`, `[`getXAResource`](XASession.md)`, `[`rollback`](XASession.md)

    <!-- -->

    - ### Methods inherited from interface javax.jms.[Session](Session.md)

      [`close`](Session.md)`, `[`createBrowser`](Session.md)`, `[`createBrowser`](Session.md)`, `[`createBytesMessage`](Session.md)`, `[`createConsumer`](Session.md)`, `[`createConsumer`](Session.md)`, `[`createConsumer`](Session.md)`, `[`createDurableSubscriber`](Session.md)`, `[`createDurableSubscriber`](Session.md)`, `[`createMapMessage`](Session.md)`, `[`createMessage`](Session.md)`, `[`createObjectMessage`](Session.md)`, `[`createObjectMessage`](Session.md)`, `[`createProducer`](Session.md)`, `[`createQueue`](Session.md)`, `[`createStreamMessage`](Session.md)`, `[`createTemporaryQueue`](Session.md)`, `[`createTemporaryTopic`](Session.md)`, `[`createTextMessage`](Session.md)`, `[`createTextMessage`](Session.md)`, `[`createTopic`](Session.md)`, `[`getAcknowledgeMode`](Session.md)`, `[`getMessageListener`](Session.md)`, `[`recover`](Session.md)`, `[`run`](Session.md)`, `[`setMessageListener`](Session.md)`, `[`unsubscribe`](Session.md)

<!-- -->

- - ### Method Detail

    - #### getQueueSession

          QueueSession getQueueSession()
                                throws JMSException

      Gets the queue session associated with this `XAQueueSession`.
      Returns:
      the queue session object

      Throws:
      [`JMSException`](JMSException.md) - if an internal error occurs.

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

- [Prev Class](XAQueueConnectionFactory.md)
- [Next Class](XASession.md)

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
