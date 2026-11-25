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

- [Prev Class](AQjmsXATopicConnectionFactory.md)
- [Next Class](TopicReceiver.md)

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

## Interface TopicBrowser

- All Known Implementing Classes:
  [AQjmsTopicBrowser](AQjmsTopicBrowser.md)

  ------------------------------------------------------------------------



      public interface TopicBrowser

  Allows browsing of messages on a Topic.
  A client uses a TopicBrowser to look at messages on a topic without removing them. This interface is an Oracle-specific extension to JMS.

  The browse methods return a `java.util.Enumeration` that is used to scan the topic's messages. It may be an enumeration of the entire content of a topic or it may only contain the messages matching a message selector.

  Messages may be arriving and expiring while the scan is done. JMS does not require the content of an enumeration to be a static snapshot of topic content. Whether these changes are visible or not depends on the JMS provider.

  Since unexpired messages on topics are never deleted unless explicitly received by subscribers (durable subscribers in the case of OJMS), topic browsers provide a way for clients to indicate that all messages that have been seen in the current browse should be received and discarded. This allows clients to manage (if needed) the content of the topic without consuming increasing amounts of resources.

  In order to guarantee properly message deletion during cleanup, it may be necessary for the implementation of topic browsers to *lock* messages being browsed. This will affect the visibility of messages by other message consumers with the same durable consumer name.

  See Also:
  [`TopicReceiver`](TopicReceiver.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                   | Method and Description                                                                                                                                       |
    |-------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `void`                              | `close``()`<br>Since a provider may allocate some resources on behalf of a TopicBrowser outside the JVM, clients should close them when they are not needed. |
    | `java.util.Enumeration`             | `getEnumeration``()`<br>Get an enumeration for browsing the current topic messages in the order they would be received.                                      |
    | `java.lang.String`                  | `getMessageSelector``()`<br>Get this topic browser's message selector expression.                                                                            |
    | [`Topic`](../../javax/jms/Topic.md) | `getTopic``()`<br>Get the topic associated with this topic browser.                                                                                          |
    | `void`                              | `purgeSeen``()`<br>Purge the topic of all messages that were *seen* in the current browse.                                                                   |

<!-- -->

- - ### Method Detail

    - #### getTopic

          Topic getTopic()
                  throws JMSException

      Get the topic associated with this topic browser.

      Returns:
      the topic

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to get the topic associated with this Browser due to some JMS error.

    <!-- -->

    - #### getMessageSelector

          java.lang.String getMessageSelector()
                                       throws JMSException

      Get this topic browser's message selector expression.

      Returns:
      this topic browser's message selector

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to get the message selector for this browser due to some JMS error.

    <!-- -->

    - #### getEnumeration

          java.util.Enumeration getEnumeration()
                                        throws JMSException

      Get an enumeration for browsing the current topic messages in the order they would be received.

      Returns:
      an enumeration for browsing the messages

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to get the enumeration for this browser due to some JMS error.

    <!-- -->

    - #### purgeSeen

          void purgeSeen()
                  throws JMSException

      Purge the topic of all messages that were *seen* in the current browse. A message is considered *seen* if it was returned to the client via a call to `nextElement()` during the browse.

      It is possible for a client to create a topic browser, call purge immediately, and not change the state of the topic (since no messages were *seen* by the above definition).

      Purging a topic also does not affect the state of messages yet to be seen by the client during a browse.

      Purging is supported only on topic browsers that were created in the `LOCKED` mode. Attempting to purge topics that were not created in the `LOCKED` mode will result in an exception.

      The purge operation will take effect only if the session for this topic browser is `commit`ed. If the session is rolled back, the purge operation will be undone and the messages will become visible again.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a JMS fails to close this Browser due to some JMS error.

    <!-- -->

    - #### close

          void close()
              throws JMSException

      Since a provider may allocate some resources on behalf of a TopicBrowser outside the JVM, clients should close them when they are not needed. Relying on garbage collection to eventually reclaim these resources may not be timely enough.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if a JMS fails to close this Browser due to some JMS error.

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

- [Prev Class](AQjmsXATopicConnectionFactory.md)
- [Next Class](TopicReceiver.md)

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
