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

- [Prev Class](QueueReceiver.md)
- [Next Class](QueueSender.md)

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

## Class QueueRequestor

- java.lang.Object

- - javax.jms.QueueRequestor

<!-- -->

-

  ------------------------------------------------------------------------



      public class QueueRequestor
      extends java.lang.Object

  The `QueueRequestor` helper class simplifies making service requests.
  The `QueueRequestor` constructor is given a non-transacted `QueueSession` and a destination `Queue`. It creates a `TemporaryQueue` for the responses and provides a `request` method that sends the request message and waits for its reply.

  This is a basic request/reply abstraction that should be sufficient for most uses. JMS providers and clients are free to create more sophisticated versions.

  See Also:
  [`TopicRequestor`](TopicRequestor.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                 |
    |---------------------------------------------------------------------------------------------------------------------------------------------|
    | `QueueRequestor``(`[`QueueSession`](QueueSession.md)` session, `[`Queue`](Queue.md)` queue)`<br>Constructor for the `QueueRequestor` class. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type       | Method and Description                                                                   |
    |-------------------------|------------------------------------------------------------------------------------------|
    | `void`                  | `close``()`<br>Closes the `QueueRequestor` and its session.                              |
    | [`Message`](Message.md) | `request``(`[`Message`](Message.md)` message)`<br>Sends a request and waits for a reply. |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### QueueRequestor

          public QueueRequestor(QueueSession session,
                                Queue queue)
                         throws JMSException

      Constructor for the `QueueRequestor` class.
      This implementation assumes the session parameter to be non-transacted, with a delivery mode of either `AUTO_ACKNOWLEDGE` or `DUPS_OK_ACKNOWLEDGE`.

      Parameters:
      `session` - the `QueueSession` the queue belongs to

      `queue` - the queue to perform the request/reply call on

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to create the `QueueRequestor` due to some internal error.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if an invalid queue is specified.

  <!-- -->

  - ### Method Detail

    - #### request

          public Message request(Message message)
                          throws JMSException

      Sends a request and waits for a reply. The temporary queue is used for the `JMSReplyTo` destination, and only one reply per request is expected.
      Parameters:
      `message` - the message to send

      Returns:
      the reply message

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to complete the request due to some internal error.

    <!-- -->

    - #### close

          public void close()
                     throws JMSException

      Closes the `QueueRequestor` and its session.
      Since a provider may allocate some resources on behalf of a `QueueRequestor` outside the Java virtual machine, clients should close them when they are not needed. Relying on garbage collection to eventually reclaim these resources may not be timely enough.

      Note that this method closes the `QueueSession` object passed to the `QueueRequestor` constructor.

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to close the `QueueRequestor` due to some internal error.

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

- [Prev Class](QueueReceiver.md)
- [Next Class](QueueSender.md)

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
