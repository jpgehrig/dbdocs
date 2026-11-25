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

- [Prev Class](Connection.md)
- [Next Class](ConnectionFactory.md)

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

## Interface ConnectionConsumer

-

  ------------------------------------------------------------------------



      public interface ConnectionConsumer

  For application servers, `Connection` objects provide a special facility for creating a `ConnectionConsumer` (optional). The messages it is to consume are specified by a `Destination` and a message selector. In addition, a `ConnectionConsumer` must be given a `ServerSessionPool` to use for processing its messages.
  Normally, when traffic is light, a `ConnectionConsumer` gets a `ServerSession` from its pool, loads it with a single message, and starts it. As traffic picks up, messages can back up. If this happens, a `ConnectionConsumer` can load each `ServerSession` with more than one message. This reduces the thread context switches and minimizes resource use at the expense of some serialization of message processing.

  See Also:
  [`Connection.createConnectionConsumer(javax.jms.Destination, java.lang.String, javax.jms.ServerSessionPool, int)`](Connection.md), [`Connection.createDurableConnectionConsumer(javax.jms.Topic, java.lang.String, java.lang.String, javax.jms.ServerSessionPool, int)`](Connection.md), [`QueueConnection.createConnectionConsumer(javax.jms.Queue, java.lang.String, javax.jms.ServerSessionPool, int)`](QueueConnection.md), [`TopicConnection.createConnectionConsumer(javax.jms.Topic, java.lang.String, javax.jms.ServerSessionPool, int)`](TopicConnection.md), [`TopicConnection.createDurableConnectionConsumer(javax.jms.Topic, java.lang.String, java.lang.String, javax.jms.ServerSessionPool, int)`](TopicConnection.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                           | Method and Description                                                                               |
    |---------------------------------------------|------------------------------------------------------------------------------------------------------|
    | `void`                                      | `close``()`<br>Closes the connection consumer.                                                       |
    | [`ServerSessionPool`](ServerSessionPool.md) | `getServerSessionPool``()`<br>Gets the server session pool associated with this connection consumer. |

<!-- -->

- - ### Method Detail

    - #### getServerSessionPool

          ServerSessionPool getServerSessionPool()
                                          throws JMSException

      Gets the server session pool associated with this connection consumer.
      Returns:
      the server session pool used by this connection consumer

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to get the server session pool associated with this consumer due to some internal error.

    <!-- -->

    - #### close

          void close()
              throws JMSException

      Closes the connection consumer.
      Since a provider may allocate some resources on behalf of a connection consumer outside the Java virtual machine, clients should close these resources when they are not needed. Relying on garbage collection to eventually reclaim these resources may not be timely enough.

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to release resources on behalf of the connection consumer or fails to close the connection consumer.

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

- [Prev Class](Connection.md)
- [Next Class](ConnectionFactory.md)

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
