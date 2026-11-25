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

- [Prev Class](AQjmsTopicPublisher.md)
- [Next Class](AQjmsTopicSubscriber.md)

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

## Interface AQjmsTopicReceiver

- All Superinterfaces:
  [MessageConsumer](../../javax/jms/MessageConsumer.md), [TopicReceiver](TopicReceiver.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsConsumer](AQjmsConsumer.md)

  ------------------------------------------------------------------------



      public interface AQjmsTopicReceiver
      extends TopicReceiver

  Oracle Advanced Queueing allows messages to be sent to all subscribers of a topic (standard JMS behaviour) or to a set of specific recipients (These recipients may or may not be subscribers of the topic). Recipients that are not currently subscribing to a topic can create and use AQjmsTopicReceivers to receive messages explicitly sent to them.
  See Also:
  [`AQjmsSession.createTopicReceiver(Topic,String,String)`](AQjmsSession.md)

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                       | Method and Description                                                                                                                |
    |-----------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
    | `int`                                   | `getNavigationMode``()`<br>Get the navigation mode used for receiving messagess.                                                      |
    | `java.lang.String`                      | `getTransformation``()`<br>Get the transformation for the Consumer.                                                                   |
    | [`Message`](../../javax/jms/Message.md) | `receive``(oracle.jms.AQjmsSignature signature)`<br>Receive the next message                                                          |
    | [`Message`](../../javax/jms/Message.md) | `receive``(long timeout, oracle.jms.AQjmsSignature signature)`<br>Receive the next message if available within the specified timeout. |
    | `void`                                  | `receiveNoData``()`<br>Consume the message without returning it to the user.                                                          |
    | `void`                                  | `receiveNoData``(long timeout)`<br>Consume the message without returning it to the user.                                              |
    | [`Message`](../../javax/jms/Message.md) | `receiveSignature``()`<br>Only return the signature to the user.                                                                      |
    | [`Message`](../../javax/jms/Message.md) | `receiveSignature``(long timeout)`<br>Only return the signature to the user.                                                          |
    | `void`                                  | `setNavigationMode``(int mode)`<br>Set the navigation mode used for receiving messagess.                                              |
    | `void`                                  | `setTransformation``(java.lang.String transformation)`<br>Set transformation for this receiver.                                       |

    - ### Methods inherited from interface oracle.jms.[TopicReceiver](TopicReceiver.md)

      [`getTopic`](TopicReceiver.md)

    <!-- -->

    - ### Methods inherited from interface javax.jms.[MessageConsumer](../../javax/jms/MessageConsumer.md)

      [`close`](../../javax/jms/MessageConsumer.md)`, `[`getMessageListener`](../../javax/jms/MessageConsumer.md)`, `[`getMessageSelector`](../../javax/jms/MessageConsumer.md)`, `[`receive`](../../javax/jms/MessageConsumer.md)`, `[`receive`](../../javax/jms/MessageConsumer.md)`, `[`receiveNoWait`](../../javax/jms/MessageConsumer.md)`, `[`setMessageListener`](../../javax/jms/MessageConsumer.md)

<!-- -->

- - ### Method Detail

    - #### getNavigationMode

          int getNavigationMode()
                         throws JMSException

      Get the navigation mode used for receiving messagess.
      Returns:
      the navigation mode

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if there was an error in getting the navigation mode

    <!-- -->

    - #### setNavigationMode

          void setNavigationMode(int mode)
                          throws JMSException

      Set the navigation mode used for receiving messagess.
      Parameters:
      `mode` - the navigation mode

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if there was an error in setting the navigation mode

    <!-- -->

    - #### receiveNoData

          void receiveNoData()
                      throws JMSException

      Consume the message without returning it to the user. This call will avoid the ovehead of fetching the message from the database and hence can be used as an optimization by jms clients who have already got the message for example using a topic browser. This call will block until a message arrives.
      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message could not be received due to an error

    <!-- -->

    - #### receiveNoData

          void receiveNoData(long timeout)
                      throws JMSException

      Consume the message without returning it to the user. This call will avoid the ovehead of fetching the message from the database and hence can be used as an optimization by jms clients who have already got the message for example using a topic browser. This call will block until a message arrives or the timeout expires
      Parameters:
      `timeout` - the timeout value in milliseconds

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message could not be received due to an error

    <!-- -->

    - #### receive

          Message receive(oracle.jms.AQjmsSignature signature)
                   throws JMSException

      Receive the next message
      Parameters:
      `signature` - the signature value

      Returns:
      the next message produced for this message consumer, or `null` if one is not available.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to receive the next message due to some error.

    <!-- -->

    - #### receive

          Message receive(long timeout,
                          oracle.jms.AQjmsSignature signature)
                   throws JMSException

      Receive the next message if available within the specified timeout.
      Parameters:
      `timeout` - the timeout value (in milliseconds)

      `signature` - the signature value

      Returns:
      the next message produced for this message consumer, or `null` if one is not available.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to receive the next message due to some error.

    <!-- -->

    - #### receiveSignature

          Message receiveSignature()
                            throws JMSException

      Only return the signature to the user. The message is locked in this case. Only the signature and the message properties are returned. This is only possible for reciever non-repudiable queues.
      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message could not be received due to an error

    <!-- -->

    - #### receiveSignature

          Message receiveSignature(long timeout)
                            throws JMSException

      Only return the signature to the user. The message is locked in this case. Only the signature and the message properties are returned. This is only possible for reciever non-repudiable queues.
      Parameters:
      `timeout` - the timeout value in milliseconds

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message could not be received due to an error

    <!-- -->

    - #### setTransformation

          void setTransformation(java.lang.String transformation)

      Set transformation for this receiver. This transformation will be applied before the message is returned to the user.
      Parameters:
      `transformation` - transformation name

    <!-- -->

    - #### getTransformation

          java.lang.String getTransformation()

      Get the transformation for the Consumer.
      Returns:
      the transformation function name of this `TopicReceiver`.

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

- [Prev Class](AQjmsTopicPublisher.md)
- [Next Class](AQjmsTopicSubscriber.md)

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
