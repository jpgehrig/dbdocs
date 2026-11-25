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

- [Prev Class](ObjectMessage.md)
- [Next Class](QueueBrowser.md)

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

## Interface Queue

- All Superinterfaces:
  [Destination](Destination.md)

  <!-- -->

  All Known Subinterfaces:
  [TemporaryQueue](TemporaryQueue.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsDestination](../../oracle/jms/AQjmsDestination.md)

  ------------------------------------------------------------------------



      public interface Queue
      extends Destination

  A `Queue` object encapsulates a provider-specific queue name. It is the way a client specifies the identity of a queue to JMS API methods. For those methods that use a `Destination` as a parameter, a `Queue` object used as an argument. For example, a queue can be used to create a `MessageConsumer` and a `MessageProducer` by calling:
  - `Session.CreateConsumer(Destination destination)`
  - `Session.CreateProducer(Destination destination)`

  The actual length of time messages are held by a queue and the consequences of resource overflow are not defined by the JMS API.

  See Also:
  [`Session.createConsumer(Destination)`](Session.md), [`Session.createProducer(Destination)`](Session.md), [`Session.createQueue(String)`](Session.md), [`QueueSession.createQueue(String)`](QueueSession.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                            |
    |--------------------|-------------------------------------------------------------------|
    | `java.lang.String` | `getQueueName``()`<br>Gets the name of this queue.                |
    | `java.lang.String` | `toString``()`<br>Returns a string representation of this object. |

<!-- -->

- - ### Method Detail

    - #### getQueueName

          java.lang.String getQueueName()
                                 throws JMSException

      Gets the name of this queue.
      Clients that depend upon the name are not portable.

      Returns:
      the queue name

      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider implementation of `Queue` fails to return the queue name due to some internal error.

    <!-- -->

    - #### toString

          java.lang.String toString()

      Returns a string representation of this object.
      Overrides:
      `toString` in class `java.lang.Object`

      Returns:
      the provider-specific identity values for this queue

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

- [Prev Class](ObjectMessage.md)
- [Next Class](QueueBrowser.md)

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
