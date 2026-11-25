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

- [Prev Class](TemporaryQueue.md)
- [Next Class](TextMessage.md)

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

## Interface TemporaryTopic

- All Superinterfaces:
  [Destination](Destination.md), [Topic](Topic.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsDestination](../../oracle/jms/AQjmsDestination.md)

  ------------------------------------------------------------------------



      public interface TemporaryTopic
      extends Topic

  A `TemporaryTopic` object is a unique `Topic` object created for the duration of a `Connection`. It is a system-defined topic that can be consumed only by the `Connection` that created it.
  A `TemporaryTopic` object can be created either at the `Session` or `TopicSession` level. Creating it at the `Session` level allows the `TemporaryTopic` to participate in the same transaction with objects from the PTP domain. If a `TemporaryTopic` is created at the `TopicSession`, it will only be able participate in transactions with objects from the Pub/Sub domain.

  See Also:
  [`Session.createTemporaryTopic()`](Session.md), [`TopicSession.createTemporaryTopic()`](TopicSession.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type | Method and Description                        |
    |-------------------|-----------------------------------------------|
    | `void`            | `delete``()`<br>Deletes this temporary topic. |

    - ### Methods inherited from interface javax.jms.[Topic](Topic.md)

      [`getTopicName`](Topic.md)`, `[`toString`](Topic.md)

<!-- -->

- - ### Method Detail

    - #### delete

          void delete()
               throws JMSException

      Deletes this temporary topic. If there are existing subscribers still using it, a `JMSException` will be thrown.
      Throws:
      [`JMSException`](JMSException.md) - if the JMS provider fails to delete the temporary topic due to some internal error.

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

- [Prev Class](TemporaryQueue.md)
- [Next Class](TextMessage.md)

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
