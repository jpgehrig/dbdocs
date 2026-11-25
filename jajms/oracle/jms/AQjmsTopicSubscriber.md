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

- [Prev Class](AQjmsTopicReceiver.md)
- [Next Class](AQjmsXAConnection.md)

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

## Interface AQjmsTopicSubscriber

- All Superinterfaces:
  [MessageConsumer](../../javax/jms/MessageConsumer.md), [TopicSubscriber](../../javax/jms/TopicSubscriber.md)

  <!-- -->

  All Known Implementing Classes:
  [AQjmsConsumer](AQjmsConsumer.md)

  ------------------------------------------------------------------------



      public interface AQjmsTopicSubscriber
      extends TopicSubscriber

  Adds Oracle® Database Advanced Queuing extensions to javax.jms.TopicSubscriber
  Allows use of navigation mode and methods to consume message without returning it to user.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Abstract Methods](javascript:show(4);)**

    | Modifier and Type                       | Method and Description                                                                                                                |
    |-----------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
    | `int`                                   | `getNavigationMode``()`<br>Get the navigation mode for receiving messages.                                                            |
    | [`Message`](../../javax/jms/Message.md) | `receive``(long timeout, oracle.jms.AQjmsSignature signature)`<br>Receive the next message if available within the specified timeout. |
    | `void`                                  | `receiveNoData``()`<br>Consume the message without returning it to the user.                                                          |
    | `void`                                  | `receiveNoData``(long timeout)`<br>Consume the message without returning it to the user.                                              |
    | `void`                                  | `setNavigationMode``(int mode)`<br>Set the navigation mode used for receiving messagess.                                              |

    - ### Methods inherited from interface javax.jms.[TopicSubscriber](../../javax/jms/TopicSubscriber.md)

      [`getNoLocal`](../../javax/jms/TopicSubscriber.md)`, `[`getTopic`](../../javax/jms/TopicSubscriber.md)

    <!-- -->

    - ### Methods inherited from interface javax.jms.[MessageConsumer](../../javax/jms/MessageConsumer.md)

      [`close`](../../javax/jms/MessageConsumer.md)`, `[`getMessageListener`](../../javax/jms/MessageConsumer.md)`, `[`getMessageSelector`](../../javax/jms/MessageConsumer.md)`, `[`receive`](../../javax/jms/MessageConsumer.md)`, `[`receive`](../../javax/jms/MessageConsumer.md)`, `[`receiveNoWait`](../../javax/jms/MessageConsumer.md)`, `[`setMessageListener`](../../javax/jms/MessageConsumer.md)

<!-- -->

- - ### Method Detail

    - #### getNavigationMode

          int getNavigationMode()
                         throws JMSException

      Get the navigation mode for receiving messages.
      Returns:
      the navigation mode. See the "Oracle® Database Advanced Queuing User's Guide and Reference" for the explanation of the navigation mode.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the navigation mode could not be set

    <!-- -->

    - #### setNavigationMode

          void setNavigationMode(int mode)
                          throws JMSException

      Set the navigation mode used for receiving messagess.
      Parameters:
      `mode` - the new value of the navigation mode. See the "Oracle® Database Advanced Queuing User's Guide and Reference" for explanation of the navigation mode. The valid values of this parameter are oracle.jms.AQjmsConstants.NAVIGATION_FIRST_MESSAGE oracle.jms.AQjmsConstants.NAVIGATION_NEXT_MESSAGE oracle.jms.AQjmsConstants.NAVIGATION_NEXT_TRANSACTION

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if there was an error in getting the navigation mode.

    <!-- -->

    - #### receiveNoData

          void receiveNoData()
                      throws JMSException

      Consume the message without returning it to the user. This call will avoid the ovehead of fetching the message from the database and hence can be used as an optimization by jms clients who have already got the message for example using a topic browser. This call will block until a message arrives.
      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message could not be received due to an error.

    <!-- -->

    - #### receiveNoData

          void receiveNoData(long timeout)
                      throws JMSException

      Consume the message without returning it to the user. This call will avoid the ovehead of fetching the message from the database and hence can be used as an optimization by jms clients who have already got the message for example using a topic browser. This call will block until a message arrives or the timeout expires.
      Parameters:
      `timeout` - the timeout value in milliseconds.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if the message could not be received due to an error.

    <!-- -->

    - #### receive

          Message receive(long timeout,
                          oracle.jms.AQjmsSignature signature)
                   throws JMSException

      Receive the next message if available within the specified timeout.
      Parameters:
      `timeout` - the timeout value (in milliseconds)

      `signature` - the signature value.

      Returns:
      the next message produced for this message consumer, or `null` if one is not available.

      Throws:
      [`JMSException`](../../javax/jms/JMSException.md) - if JMS fails to receive the next message due to some error.

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

- [Prev Class](AQjmsTopicReceiver.md)
- [Next Class](AQjmsXAConnection.md)

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
