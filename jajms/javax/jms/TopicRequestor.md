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

- [Prev Class](TopicPublisher.md)
- [Next Class](TopicSession.md)

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

## Class TopicRequestor

- java.lang.Object

- - javax.jms.TopicRequestor

<!-- -->

-

  ------------------------------------------------------------------------



      public class TopicRequestor
      extends java.lang.Object

  The `TopicRequestor` helper class simplifies making service requests.
  The `TopicRequestor` constructor is given a non-transacted `TopicSession` and a destination `Topic`. It creates a `TemporaryTopic` for the responses and provides a `request` method that sends the request message and waits for its reply.

  This is a basic request/reply abstraction that should be sufficient for most uses. JMS providers and clients are free to create more sophisticated versions.

  See Also:
  [`QueueRequestor`](QueueRequestor.md)

<!-- -->

- - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                                                                                                 |
    |---------------------------------------------------------------------------------------------------------------------------------------------|
    | `TopicRequestor``(`[`TopicSession`](TopicSession.md)` session, `[`Topic`](Topic.md)` topic)`<br>Constructor for the `TopicRequestor` class. |

  <!-- -->

  - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type       | Method and Description                                                                   |
    |-------------------------|------------------------------------------------------------------------------------------|
    | `void`                  | `close``()`<br>Closes the `TopicRequestor` and its session.                              |
    | [`Message`](Message.md) | `request``(`[`Message`](Message.md)` message)`<br>Sends a request and waits for a reply. |

    - ### Methods inherited from class java.lang.Object

      `clone, equals, finalize, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Constructor Detail

    - #### TopicRequestor

          public TopicRequestor(TopicSession session,
                                Topic topic)
                         throws JMSException

      Constructor for the `TopicRequestor` class.
      This implementation assumes the session parameter to be non-transacted, with a delivery mode of either `AUTO_ACKNOWLEDGE` or `DUPS_OK_ACKNOWLEDGE`.

      Parameters:
      `session` - the `TopicSession` the topic belongs to

      `topic` - the topic to perform the request/reply call on

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to create the `TopicRequestor` due to some internal error.

      [`InvalidDestinationException`](InvalidDestinationException.md) - if an invalid topic is specified.

  <!-- -->

  - ### Method Detail

    - #### request

          public Message request(Message message)
                          throws JMSException

      Sends a request and waits for a reply. The temporary topic is used for the `JMSReplyTo` destination; the first reply is returned, and any following replies are discarded.
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

      Closes the `TopicRequestor` and its session.
      Since a provider may allocate some resources on behalf of a `TopicRequestor` outside the Java virtual machine, clients should close them when they are not needed. Relying on garbage collection to eventually reclaim these resources may not be timely enough.

      Note that this method closes the `TopicSession` object passed to the `TopicRequestor` constructor.

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to close the `TopicRequestor` due to some internal error.

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

- [Prev Class](TopicPublisher.md)
- [Next Class](TopicSession.md)

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
