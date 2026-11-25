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

- [Prev Class](AQjmsQueueReceiver.md)
- [Next Class](AQjmsSession.md)

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

## Interface AQjmsQueueSender

- All Superinterfaces:
  [MessageProducer](../../javax/jms/MessageProducer.md), [QueueSender](../../javax/jms/QueueSender.md)

  ------------------------------------------------------------------------



      public interface AQjmsQueueSender
      extends QueueSender

  Adds Oracle® Database Advanced Queuing extensions to `javax.jms.QueueSender`
  Allows use of transformations

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type  | Method and Description                                                                        |
    |--------------------|-----------------------------------------------------------------------------------------------|
    | `java.lang.String` | `getTransformation``()`<br>Get the name of the transformation function of the `QueueSender`.  |
    | `void`             | `setTransformation``(java.lang.String transformation)`<br>Set transformation for this sender. |

    - ### Methods inherited from interface javax.jms.[QueueSender](../../javax/jms/QueueSender.md)

      [`getQueue`](../../javax/jms/QueueSender.md)`, `[`send`](../../javax/jms/QueueSender.md)`, `[`send`](../../javax/jms/QueueSender.md)`, `[`send`](../../javax/jms/QueueSender.md)`, `[`send`](../../javax/jms/QueueSender.md)

    <!-- -->

    - ### Methods inherited from interface javax.jms.[MessageProducer](../../javax/jms/MessageProducer.md)

      [`close`](../../javax/jms/MessageProducer.md)`, `[`getDeliveryMode`](../../javax/jms/MessageProducer.md)`, `[`getDestination`](../../javax/jms/MessageProducer.md)`, `[`getDisableMessageID`](../../javax/jms/MessageProducer.md)`, `[`getDisableMessageTimestamp`](../../javax/jms/MessageProducer.md)`, `[`getPriority`](../../javax/jms/MessageProducer.md)`, `[`getTimeToLive`](../../javax/jms/MessageProducer.md)`, `[`send`](../../javax/jms/MessageProducer.md)`, `[`send`](../../javax/jms/MessageProducer.md)`, `[`setDeliveryMode`](../../javax/jms/MessageProducer.md)`, `[`setDisableMessageID`](../../javax/jms/MessageProducer.md)`, `[`setDisableMessageTimestamp`](../../javax/jms/MessageProducer.md)`, `[`setPriority`](../../javax/jms/MessageProducer.md)`, `[`setTimeToLive`](../../javax/jms/MessageProducer.md)

<!-- -->

- - ### Method Detail

    - #### setTransformation

          void setTransformation(java.lang.String transformation)

      Set transformation for this sender. This transformation will be applied before the message is inserted in the queue.
      Parameters:
      `transformation` - transformation name.

    <!-- -->

    - #### getTransformation

          java.lang.String getTransformation()

      Get the name of the transformation function of the `QueueSender`.
      Returns:
      the name of the transformation function of the `QueueSender`.

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

- [Prev Class](AQjmsQueueReceiver.md)
- [Next Class](AQjmsSession.md)

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
