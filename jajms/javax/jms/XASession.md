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

- [Prev Class](XAQueueSession.md)
- [Next Class](XATopicConnection.md)

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

## Interface XASession

- All Superinterfaces:
  java.lang.Runnable, [Session](Session.md)

  <!-- -->

  All Known Subinterfaces:
  [XAQueueSession](XAQueueSession.md), [XATopicSession](XATopicSession.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsXASession](../../oracle/jms/AQjmsXASession.md)

  ------------------------------------------------------------------------



      public interface XASession
      extends Session

  The `XASession` interface extends the capability of `Session` by adding access to a JMS provider's support for the Java Transaction API (JTA) (optional). This support takes the form of a `javax.transaction.xa.XAResource` object. The functionality of this object closely resembles that defined by the standard X/Open XA Resource interface.
  An application server controls the transactional assignment of an `XASession` by obtaining its `XAResource`. It uses the `XAResource` to assign the session to a transaction, prepare and commit work on the transaction, and so on.

  An `XAResource` provides some fairly sophisticated facilities for interleaving work on multiple transactions, recovering a list of transactions in progress, and so on. A JTA aware JMS provider must fully implement this functionality. This could be done by using the services of a database that supports XA, or a JMS provider may choose to implement this functionality from scratch.

  A client of the application server is given what it thinks is a regular JMS `Session`. Behind the scenes, the application server controls the transaction management of the underlying `XASession`.

  The `XASession` interface is optional. JMS providers are not required to support this interface. This interface is for use by JMS providers to support transactional environments. Client programs are strongly encouraged to use the transactional support available in their environment, rather than use these XA interfaces directly.

  See Also:
  [`Session`](Session.md)

<!-- -->

- - ### Field Summary

    - ### Fields inherited from interface javax.jms.[Session](Session.md)

      [`AUTO_ACKNOWLEDGE`](Session.md)`, `[`CLIENT_ACKNOWLEDGE`](Session.md)`, `[`DUPS_OK_ACKNOWLEDGE`](Session.md)`, `[`SESSION_TRANSACTED`](Session.md)

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                 | Method and Description                                                                                                |
    |-----------------------------------|-----------------------------------------------------------------------------------------------------------------------|
    | `void`                            | `commit``()`<br>Throws a `TransactionInProgressException`, since it should not be called for an `XASession` object.   |
    | [`Session`](Session.md)           | `getSession``()`<br>Gets the session associated with this `XASession`.                                                |
    | `boolean`                         | `getTransacted``()`<br>Indicates whether the session is in transacted mode.                                           |
    | `javax.transaction.xa.XAResource` | `getXAResource``()`<br>Returns an XA resource to the caller.                                                          |
    | `void`                            | `rollback``()`<br>Throws a `TransactionInProgressException`, since it should not be called for an `XASession` object. |

    - ### Methods inherited from interface javax.jms.[Session](Session.md)

      [`close`](Session.md)`, `[`createBrowser`](Session.md)`, `[`createBrowser`](Session.md)`, `[`createBytesMessage`](Session.md)`, `[`createConsumer`](Session.md)`, `[`createConsumer`](Session.md)`, `[`createConsumer`](Session.md)`, `[`createDurableSubscriber`](Session.md)`, `[`createDurableSubscriber`](Session.md)`, `[`createMapMessage`](Session.md)`, `[`createMessage`](Session.md)`, `[`createObjectMessage`](Session.md)`, `[`createObjectMessage`](Session.md)`, `[`createProducer`](Session.md)`, `[`createQueue`](Session.md)`, `[`createStreamMessage`](Session.md)`, `[`createTemporaryQueue`](Session.md)`, `[`createTemporaryTopic`](Session.md)`, `[`createTextMessage`](Session.md)`, `[`createTextMessage`](Session.md)`, `[`createTopic`](Session.md)`, `[`getAcknowledgeMode`](Session.md)`, `[`getMessageListener`](Session.md)`, `[`recover`](Session.md)`, `[`run`](Session.md)`, `[`setMessageListener`](Session.md)`, `[`unsubscribe`](Session.md)

<!-- -->

- - ### Method Detail

    - #### getSession

          Session getSession()
                      throws JMSException

      Gets the session associated with this `XASession`.
      Returns:
      the session object

      Throws:
      [`JMSException`](JMSException.md) - if an internal error occurs.

      Since:
      1.1

    <!-- -->

    - #### getXAResource

          javax.transaction.xa.XAResource getXAResource()

      Returns an XA resource to the caller.
      Returns:
      an XA resource to the caller

    <!-- -->

    - #### getTransacted

          boolean getTransacted()
                         throws JMSException

      Indicates whether the session is in transacted mode.
      Specified by:
      [`getTransacted`](Session.md) in interface [`Session`](Session.md)

      Returns:
      true

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to return the transaction mode due to some internal error.

    <!-- -->

    - #### commit

          void commit()
               throws JMSException

      Throws a `TransactionInProgressException`, since it should not be called for an `XASession` object.
      Specified by:
      [`commit`](Session.md) in interface [`Session`](Session.md)

      Throws:
      [`TransactionInProgressException`](TransactionInProgressException.md) - if the method is called on an `XASession`.

      [`JMSException`](JMSException.md) - if the JMS provider fails to commit the transaction due to some internal error.

      [`TransactionRolledBackException`](TransactionRolledBackException.md) - if the transaction is rolled back due to some internal error during commit.

      [`IllegalStateException`](IllegalStateException.md) - if the method is not called by a transacted session.

    <!-- -->

    - #### rollback

          void rollback()
                 throws JMSException

      Throws a `TransactionInProgressException`, since it should not be called for an `XASession` object.
      Specified by:
      [`rollback`](Session.md) in interface [`Session`](Session.md)

      Throws:
      [`TransactionInProgressException`](TransactionInProgressException.md) - if the method is called on an `XASession`.

      [`JMSException`](JMSException.md) - if the JMS provider fails to roll back the transaction due to some internal error.

      [`IllegalStateException`](IllegalStateException.md) - if the method is not called by a transacted session.

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

- [Prev Class](XAQueueSession.md)
- [Next Class](XATopicConnection.md)

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
