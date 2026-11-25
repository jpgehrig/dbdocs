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

- [Prev Class](TopicBrowser.md)
- Next Class

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

## Interface TopicReceiver

- All Superinterfaces:
  [MessageConsumer](../../javax/jms/MessageConsumer.md)

  <!-- -->

  All Known Subinterfaces:
  [AQjmsTopicReceiver](AQjmsTopicReceiver.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsConsumer](AQjmsConsumer.md)

  ------------------------------------------------------------------------



      public interface TopicReceiver
      extends MessageConsumer

  Extends `javax.jms.MessageConsumer` to allow point to multipoint communication, which is an Oracle® Database Advanced Queuing specific variation of publish subscribe
  See Also:
  [`AQjmsTopicReceiver`](AQjmsTopicReceiver.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                   | Method and Description                                         |
    |-------------------------------------|----------------------------------------------------------------|
    | [`Topic`](../../javax/jms/Topic.md) | `getTopic``()`<br>Get the topic associated with this receiver. |

    - ### Methods inherited from interface javax.jms.[MessageConsumer](../../javax/jms/MessageConsumer.md)

      [`close`](../../javax/jms/MessageConsumer.md)`, `[`getMessageListener`](../../javax/jms/MessageConsumer.md)`, `[`getMessageSelector`](../../javax/jms/MessageConsumer.md)`, `[`receive`](../../javax/jms/MessageConsumer.md)`, `[`receive`](../../javax/jms/MessageConsumer.md)`, `[`receiveNoWait`](../../javax/jms/MessageConsumer.md)`, `[`setMessageListener`](../../javax/jms/MessageConsumer.md)

<!-- -->

- - ### Method Detail

    - #### getTopic

          Topic getTopic()
                  throws JMSException

      Get the topic associated with this receiver.
      Returns:
      this subscriber's topic

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to get topic for this topic receiver due to some internal error.

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

- [Prev Class](TopicBrowser.md)
- Next Class

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
