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

- [Prev Class](Queue.md)
- [Next Class](QueueConnection.md)

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

## Interface QueueBrowser

- All Known Implementing Classes:
  [AQjmsQueueBrowser](../../oracle/jms/AQjmsQueueBrowser.md)

  ------------------------------------------------------------------------



      public interface QueueBrowser

  A client uses a `QueueBrowser` object to look at messages on a queue without removing them.
  The `getEnumeration` method returns a `java.util.Enumeration` that is used to scan the queue's messages. It may be an enumeration of the entire content of a queue, or it may contain only the messages matching a message selector.

  Messages may be arriving and expiring while the scan is done. The JMS API does not require the content of an enumeration to be a static snapshot of queue content. Whether these changes are visible or not depends on the JMS provider.

  A `QueueBrowser` can be created from either a `Session` or a `QueueSession`.

  See Also:
  [`Session.createBrowser(javax.jms.Queue)`](Session.md), [`QueueSession.createBrowser(javax.jms.Queue)`](QueueSession.md), [`QueueReceiver`](QueueReceiver.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type       | Method and Description                                                                                                   |
    |-------------------------|--------------------------------------------------------------------------------------------------------------------------|
    | `void`                  | `close``()`<br>Closes the `QueueBrowser`.                                                                                |
    | `java.util.Enumeration` | `getEnumeration``()`<br>Gets an enumeration for browsing the current queue messages in the order they would be received. |
    | `java.lang.String`      | `getMessageSelector``()`<br>Gets this queue browser's message selector expression.                                       |
    | [`Queue`](Queue.md)     | `getQueue``()`<br>Gets the queue associated with this queue browser.                                                     |

<!-- -->

- - ### Method Detail

    - #### getQueue

          Queue getQueue()
                  throws JMSException

      Gets the queue associated with this queue browser.
      Returns:
      the queue

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the queue associated with this browser due to some internal error.

    <!-- -->

    - #### getMessageSelector

          java.lang.String getMessageSelector()
                                       throws JMSException

      Gets this queue browser's message selector expression.
      Returns:
      this queue browser's message selector, or null if no message selector exists for the message consumer (that is, if the message selector was not set or was set to null or the empty string)

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the message selector for this browser due to some internal error.

    <!-- -->

    - #### getEnumeration

          java.util.Enumeration getEnumeration()
                                        throws JMSException

      Gets an enumeration for browsing the current queue messages in the order they would be received.
      Returns:
      an enumeration for browsing the messages

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the enumeration for this browser due to some internal error.

    <!-- -->

    - #### close

          void close()
              throws JMSException

      Closes the `QueueBrowser`.
      Since a provider may allocate some resources on behalf of a QueueBrowser outside the Java virtual machine, clients should close them when they are not needed. Relying on garbage collection to eventually reclaim these resources may not be timely enough.

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to close this browser due to some internal error.

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

- [Prev Class](Queue.md)
- [Next Class](QueueConnection.md)

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
