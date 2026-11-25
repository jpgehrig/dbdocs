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

- [Prev Class](StreamMessage.md)
- [Next Class](TemporaryTopic.md)

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

## Interface TemporaryQueue

- All Superinterfaces:
  [Destination](Destination.md), [Queue](Queue.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsDestination](../../oracle/jms/AQjmsDestination.md)

  ------------------------------------------------------------------------



      public interface TemporaryQueue
      extends Queue

  A `TemporaryQueue` object is a unique `Queue` object created for the duration of a `Connection`. It is a system-defined queue that can be consumed only by the `Connection` that created it.
  A `TemporaryQueue` object can be created at either the `Session` or `QueueSession` level. Creating it at the `Session` level allows to the `TemporaryQueue` to participate in transactions with objects from the Pub/Sub domain. If it is created at the `QueueSession`, it will only be able participate in transactions with objects from the PTP domain.

  See Also:
  [`Session.createTemporaryQueue()`](Session.md), [`QueueSession.createTemporaryQueue()`](QueueSession.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                        |
    |-------------------|-----------------------------------------------|
    | `void`            | `delete``()`<br>Deletes this temporary queue. |

    - ### Methods inherited from interface javax.jms.[Queue](Queue.md)

      [`getQueueName`](Queue.md)`, `[`toString`](Queue.md)

<!-- -->

- - ### Method Detail

    - #### delete

          void delete()
               throws JMSException

      Deletes this temporary queue. If there are existing receivers still using it, a `JMSException` will be thrown.
      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to delete the temporary queue due to some internal error.

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

- [Prev Class](StreamMessage.md)
- [Next Class](TemporaryTopic.md)

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
